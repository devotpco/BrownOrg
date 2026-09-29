# v0 Boundary Layer (Draft)

**0.1** This draft states the boundary layer of BrownOrg version v0. The boundary layer is the code that holds every connection crossing the app's edge, in or out. `Objective.md` says what v0 builds. The Steward ruled "keep it simple" for v0.

**0.2** A client is anything that starts a request to the app. In v0 the client is the Vue web page. An endpoint is the code that receives one kind of request. A payload is the data that travels with a request or a response. A use case is one thing a client asks the app to do.

**0.3** Rule for every endpoint (`Reference/Layer_Encapsulation.md` §4.5): it unpacks the request payload, calls the business logic, and packs the result into the response. It does nothing else. Endpoints live in `2-APP/Boundary/Boundary_in`.

## 1. Hosting

**1.1** v0 runs as one Cloudflare Python Worker that runs Flask. The Worker serves the built Vue front end as static files. It routes every path that starts with `/api/` to Flask.

**1.2** All payloads are JSON.

## 2. Endpoints

**2.1** `POST /api/sign-in` calls the use case `sign_in`. Request: `{"password": "<text>"}`.

**2.2** Responses:

- 200: `{"ok": true}`. The password is right.
- 401: `{"ok": false}`. The password is wrong or missing.

**2.3** `POST /api/finance/expenses` calls the use case `record_expense` in the module `finance`, section `income_expense`. Request fields:

- `expense_date`: text, format `YYYY-MM-DD`.
- `amount_cents`: integer, the amount in whole cents.
- `category`: text, optional.
- `payee`: text, optional.
- `note`: text, optional.

**2.6** The page address the user sees follows the navigation: `/finance/income-expense/expense` (see `v0_UX.md`). The API path names the thing stored, so it stays `POST /api/finance/expenses`. Income would later get `/api/finance/incomes`. Rearranging the screens then never changes the API.

**2.7** The form checks amounts for convenience. The business logic's validation is the one that decides, because any client may call the API directly.

**2.4** Responses:

- 201: `{"ok": true}`. The expense is stored. No id is returned.
- 400: `{"ok": false, "problems": [{"field": "amount_cents", "message": "..."}]}`. The business logic found the expense invalid. `problems` lists each one.

**2.5** The business logic decides what is valid. The endpoint only maps its result to the status code and payload above. An unexpected error returns 500.

## 3. Security in v0

**3.1** The login page is the only security. There are no sessions, no cookies, no signed-in checks and no sign-out. Neither endpoint is protected: anyone who can reach `/api/finance/expenses` can call it. The Steward accepts this for v0.

**3.2** The password is fixed in the code. Its value appears in no document.

## 4. Outbound connections

**4.1** v0 makes no outbound call. `Boundary_out` stays empty.

**4.2** The data layer reaches D1 (Cloudflare's SQLite-compatible database), not the boundary layer. Endpoints never touch the database.

## 5. Open questions

**5.1** None.
