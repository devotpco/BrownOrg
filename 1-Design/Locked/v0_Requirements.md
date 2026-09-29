# v0 Requirements and Test Plan (Draft)

**0.1** This draft turns the approved v0 design into a few numbered, testable requirements and a short test plan. The Steward is the human who holds the decision on the project. The Steward ruled for v0: keep it simple, with one expense form and one table, and keep testing light. This draft adds nothing beyond the six design drafts.

**0.2** Terms. A requirement is one statement that a test can pass or fail. "Objective §5" means the five success items in `Objective.md` §5.1, numbered 1 to 5: (1) the site loads at its Cloudflare address; (2) the login page refuses a wrong password and admits the right one; (3) after login, the user reaches the expense form through Finance, then Income & Expense; (4) submitting the form stores one record in the hosted D1 database, and the record can be seen there afterwards; (5) the code tested locally deploys with no code changes. D1 is Cloudflare's SQL database. A Worker is a program Cloudflare runs on request. A design block is a numbered paragraph such as **2.3** in a draft file.

**0.3** Test kinds. **Unit** means a pytest test of the business layer in ordinary Python, with a stand-in `ExpenseStore` (the interface the business logic saves through) that records calls. **End-to-end** means a check against the Worker running locally with `pywrangler dev` and its local D1. **Manual** means a person checks on the hosted site. The Steward's password value is never written in this file or in any test report.

## 1. Requirements

**1.1** Each requirement gives its Objective §5 item, its source (draft file and block), and its test kind.

**R-1** `sign_in` returns success when the password equals the one shared password. Objective §5: item 2. Source: `v0_Business.md` 3.3, 3.4. Test: unit.

**R-2** `sign_in` returns failure for any other password, including an empty one. Objective §5: item 2. Source: `v0_Business.md` 3.3, 3.4. Test: unit.

**R-3** `record_expense` with a valid date, a true-integer amount above zero and any optional fields calls `ExpenseStore.add` once with those values, and returns success. Objective §5: item 4. Source: `v0_Business.md` 4.4, 4.5. Test: unit.

**R-4** `record_expense` rejects an `amount_cents` that is missing, zero, negative or not a true integer, and reports a problem on `amount_cents`. The values `true`, `12.0` and `12.5` are problems. It does not call `ExpenseStore.add`. Objective §5: item 4. Source: `v0_Business.md` 4.4, 4.5. Test: unit.

**R-5** `record_expense` parses `expense_date` from text and rejects a missing date or text that is not a valid `YYYY-MM-DD` date, and reports a problem on `expense_date`. It does not call `ExpenseStore.add`. Objective §5: item 4. Source: `v0_Business.md` 4.4, 4.5; `v0_Boundary.md` 0.3, 2.3. Test: unit.

**R-6** When the `ExpenseStore` raises `StoreError`, `record_expense` does not catch it; the error passes up. Objective §5: item 4. Source: `v0_Data_Access.md` 3.1, 4.2. Test: unit, with a stand-in store that raises. Nothing deliberately breaks D1 in v0.

**R-7** `POST /api/finance/expenses` with a valid expense returns 201 and `{"ok": true}`, and one new row holding the submitted values then appears in `fin_expense`, read back with `npx wrangler d1 execute brownorg --local --command "SELECT … FROM fin_expense …"` run from the test. Objective §5: item 4. Source: `v0_Boundary.md` 2.3, 2.4; `v0_Data_Access.md` 2.1, 4.2. Test: end-to-end.

**R-8** On the hosted site, one walk-through shows: the login screen loads at the Cloudflare address; a wrong password is refused and the right one admits the user; Finance, then Income & Expense, then the expense form open in turn; a submitted expense shows the "Expense saved." toast; and `npx wrangler d1 execute brownorg --remote --command "SELECT * FROM fin_expense"` shows the new row. Objective §5: items 1, 2, 3 and 4. Source: `v0_UX.md` 1.3, 2.2, 3.2, 4.5; `v0_Deployment.md` 4.8. Test: manual.

**R-9** The commit deployed to Cloudflare is the commit that passed R-1 to R-7 locally, with no edit between. Objective §5: item 5. Source: `v0_Data_Access.md` 4.1; `v0_Deployment.md` 1.3, 4.6. Test: manual.

## 2. Build checks

**2.1** The design says two things are tested first in the build. If either fails, the design changes before more code is written.

**2.2** Build check A: Python imports across the sibling folders `Data`, `Boundary` and `Business` inside the Worker (`v0_Deployment.md` 2.2). Pass condition: the Worker started with `pywrangler dev` loads, and a request to any `/api/` path reaches Flask code that imports a name from `Business` and a name from `Data`, and returns a response with no import error. Fail condition: any `ImportError` or `ModuleNotFoundError`. If it fails, the layout changes.

**2.3** Build check B: inserting a row into D1 from Python (`v0_Data_Access.md` 2.2). Pass condition: with the migration applied to the local D1, the call `await self.env.DB.prepare(sql).bind(...).run()` inside the running Worker inserts one row into `fin_expense`, and a read of the table then shows that row with the values sent. Fail condition: the call raises an error, or no row appears.

## 3. Test plan

**3.1** Test runner: pytest, run from `2-APP/` with the project's virtual environment active, as `pytest tests`. All tests live in `2-APP/tests/`. There are no front-end tests.

**3.2** The unit suite covers R-1 to R-6. It has no network and no database.

**3.3** The end-to-end check (R-7) runs after `npx wrangler d1 migrations apply brownorg --local`, against the Worker started by `pywrangler dev`. It submits one valid expense through `POST /api/finance/expenses`, confirms 201, then reads the row back with the local `wrangler d1 execute` query and confirms the values.

**3.4** The manual checks (R-8, R-9) run once, after a deploy that the Steward approved (`v0_Deployment.md` 4.6).

**3.5** The run summary. Every `pytest tests` run ends with pytest's last line, which states how many tests ran and how many passed, for example `8 passed in 0.4s`. The last line must show that every test passed and none failed or errored. The team's rule is that no commit is made while a test fails. The QA report quotes this line and names the branch tested.

**3.6** Coverage by Objective §5 item: items 1 to 3 by R-8; item 4 by R-3 to R-8; item 5 by R-9.

## 4. Open questions

None.
