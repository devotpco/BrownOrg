# v0 Business Logic Design (Draft)

**0.1** This draft designs the business logic of BrownOrg version v0. Business logic is the code that does the work the app exists to do. The Steward is the human who holds the decision on the project. The Steward ruled for v0: keep it simple, with one expense form and one table that saves the entries. Nothing here plans for after v0.

**0.2** The code lives in `2-APP/Business`. It is plain Python. It imports no Cloudflare code and no Flask code, so a test can run it in an ordinary Python environment.

## 1. Layer rules that bind this code
**1.1** The business logic stores information only through an interface. An interface is a named call that the business logic declares and the data layer fulfils. The business logic does not know how the data layer works inside.

**1.2** The business logic does not know which client started a request. A use case is one thing a client can ask the app to do. Endpoints (the code that receives each kind of request; `v0_Boundary.md` §0.2) unpack the payload (the data that travels with a request), call a use case, and pack the result.

## 2. The expense object
**2.1** `Expense` is a plain Python object, a frozen dataclass. It carries one expense between the layers and holds no logic.

**2.2** Its fields are:

1. `expense_date`: a `datetime.date`, the day the money was spent. Required.
2. `amount_cents`: an `int`, whole cents, greater than zero. Required.
3. `category`: a `str` or `None`. Optional.
4. `payee`: a `str` or `None`. Optional.
5. `note`: a `str` or `None`. Optional.

## 3. Use case sign_in
**3.1** Purpose: decide whether a person may enter. v0 has one shared password and no accounts.

**3.2** Input: `password`, a `str`.

**3.3** Rule: the business logic compares `password` with the one shared password, a constant fixed in the code. It calls no interface.

**3.4** Results: success when the password matches, failure when it does not.

**3.5** `sign_in` creates no session. No use case checks whether a person has signed in.

## 4. Use case record_expense
**4.1** Purpose: save one new expense, in the `income_expense` section of the `finance` module.

**4.2** Inputs: `expense_date`, `amount_cents`, `category`, `payee`, `note`.

**4.3** Interface called: `ExpenseStore`, a data-layer interface with the method `add(expense)`. It returns nothing.

**4.4** Rules:

1. `expense_date` is required and must be a date.
2. `amount_cents` is required and must be a whole number greater than zero.
3. `category`, `payee` and `note` are optional plain text. There is no category list and no length limit.
4. The business logic collects every problem, not only the first.

**4.5** Results:

1. Success: every rule passed, and `ExpenseStore.add` was called once with the new `Expense`. No id goes back.
2. Validation failure: carries the list of problems, each a field name and a reason. `ExpenseStore.add` is not called.

## 5. Open questions
None.
