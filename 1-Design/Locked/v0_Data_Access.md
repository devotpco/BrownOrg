# v0 Data Access (draft)

**0.1** This draft says how the data layer saves one expense in D1 for version v0. The Steward ruled v0 stays simple: one expense form, one table. Layer rules are in the Library note `Reference/Layer_Encapsulation.md` §4.

**0.2** Terms. **D1** is Cloudflare's SQLite-compatible database. A **binding** is a named handle Cloudflare gives the Worker so it can reach D1; here it is named `DB`. A **parameterized query** is SQL with `?` placeholders, where the values travel apart from the SQL text. A **migration file** is a script that creates or changes tables.

## 1. Interface and table

**1.1** The business logic sees one interface, `ExpenseStore`, with one call: `async def add(expense) -> None`. It returns nothing. There is no read call.

**1.2** `expense` is a plain Python object with five fields: `expense_date`, `amount_cents`, `category`, `payee`, `note`.

**1.3** The table is `fin_expense`. Its columns are an integer `id` that the database assigns, `expense_date` as text `YYYY-MM-DD`, `amount_cents` as an integer, and `category`, `payee` and `note` as optional text.

**1.4** The migration file `0001_create_fin_expense.sql` (`v0_Data_Model.md` §3) creates the table. Wrangler applies it to the local D1 (DEV) and to the hosted D1 (PROD).

## 2. The D1 implementation

**2.1** The class `D1ExpenseStore` implements `ExpenseStore`. It is the only code that holds SQL. It runs one parameterized INSERT and never builds SQL from strings.

```
INSERT INTO fin_expense (expense_date, amount_cents, category, payee, note)
VALUES (?, ?, ?, ?, ?)
```

**2.2** The class runs it with `await self.env.DB.prepare(sql).bind(...).run()`, as Cloudflare documents for Python (developers.cloudflare.com/d1/examples/query-d1-from-python-workers/). The build tests first that this call works from Python.

**2.3** The Worker's start-up code hands the `DB` binding to `D1ExpenseStore` through its constructor, then passes the store to the business logic as an `ExpenseStore`. The business logic never sees the binding.

**2.4** D1 calls are awaitable, so `add` is `async` and every D1 call uses `await`.

## 3. Errors

**3.1** The data layer defines one error type, `StoreError`. `D1ExpenseStore` catches every D1 exception, logs it in full, and raises `StoreError` with a plain message that holds no SQL and no values. The business logic does not catch `StoreError`. The error passes up to the endpoint, which returns a 500 response (v0_Boundary.md §2.5).

## 4. Environments and tests

**4.1** The local D1 and the hosted D1 attach to the same binding name, `DB`. The code is identical in both.

**4.2** Data-layer tests run locally against the local D1, after the migration is applied. A test calls `add`, then checks the row with its own test-only query, and a second test checks that a failure raises `StoreError`.

## Open questions

None. The Steward's rulings answer every earlier question.
