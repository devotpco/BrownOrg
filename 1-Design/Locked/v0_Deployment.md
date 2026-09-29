# v0 Deployment and Project Setup (Draft)

**0.1** This draft says how BrownOrg v0 is set up, run locally and deployed. It serves `Objective.md` §2.2 and §5.1. The Steward is the human who decides on the project. v0 is kept simple: one expense form and one table. Nothing here designs for after v0.

**0.2** Terms. **Cloudflare** is the hosting platform. A **Worker** is a program Cloudflare runs on request. A **Python Worker** is a Worker written in Python. **Wrangler** is Cloudflare's command-line tool. **pywrangler** is the command-line tool for Python Workers; it needs **uv** (a Python package manager) and **Node.js**. **D1** is Cloudflare's SQL database. A **binding** is a name through which a Worker reaches a resource such as D1.

## 1. Environments and resources

**1.1** There are two environments. **DEV** is any developer machine, of which the Steward has two. It runs the Worker locally with a local D1 database that keeps its data between runs. **PROD** is Cloudflare.

**1.2** There is one Worker and one D1 database. Both are named `brownorg`. One tracked file, `2-APP/wrangler.jsonc`, names the Worker, sets its entry file to `main.py`, points the static-assets directory at `html/dist`, sends `/api/*` requests to the Worker's Python code, where Flask handles each route (`v0_Boundary.md` §1.1), and binds D1 as `DB` with `migrations_dir` set to `Data/migrations`.

**1.3** v0 has no configuration step. It has no YAML file, no secrets and no `scripts/` folder. The login password is fixed in the code. The code reads only the `DB` binding.

## 2. Project layout

**2.1** The Worker project root is `2-APP/`. Inside it:

- `Data/` holds the D1 access code and `Data/migrations/`, which holds the one SQL migration file that creates the expense table.
- `main.py` is the Worker's entry file. It only wires together the Flask endpoints from `Boundary/Boundary_in/`. `Data/`, `Boundary/` and `Business/` sit beside it.
- `Boundary/Boundary_in/` holds the Flask endpoints. An endpoint only unpacks the request, calls `Business`, and packs the reply.
- `Business/` holds the business logic. It imports neither Flask nor Cloudflare.
- `html/` holds the Vue 3 + PrimeVue source. `html/dist/` is the build output.
- `tests/` holds the pytest suite.

**2.2** The Python code in `Data`, `Boundary` and `Business` imports across these sibling folders. The first build step tests this, and tests inserting a row into D1 from Python. If the imports fail, the layout changes then.

## 3. Setup, once per machine and once per Cloudflare account

**3.1** On each developer machine, from `2-APP/` with the project's Python virtual environment active: install the Python packages, then `npm --prefix html install`. Node.js and npm live inside the virtual environment.

**3.2** Sign in to Cloudflare: `npx wrangler login`. This opens a browser. There is no API key.

**3.3** Create the hosted database, once: `npx wrangler d1 create brownorg`. Copy the `database_id` it prints into `wrangler.jsonc`, which is tracked. The Worker itself is created by the first deploy.

## 4. Commands

**4.1** Commands run from `2-APP/` with the virtual environment active.

**4.2** Build the front end: `npm --prefix html run build`.

**4.3** Migrate the local database: `npx wrangler d1 migrations apply brownorg --local`.

**4.4** Run locally: `pywrangler dev`. The local data stays in `.wrangler/`.

**4.5** Migrate the hosted database: `npx wrangler d1 migrations apply brownorg --remote`.

**4.6** Deploy, by hand, from branch `dev_claude`, only on the Steward's go: `npm --prefix html run build`, then `npx wrangler d1 migrations apply brownorg --remote`, then `pywrangler deploy`.

**4.7** Retired 2026-09-29. Beyond v0.

**4.8** Show the saved rows in the hosted database, to see a record after submitting the form: `npx wrangler d1 execute brownorg --remote --command "SELECT * FROM fin_expense"`.

## 5. Tests

**5.1** A small pytest suite tests the two use cases, `sign_in` and `record_expense`, against the business layer, in the ordinary Python environment: `pytest tests`.

**5.2** One end-to-end check runs against the local Worker started by `pywrangler dev`. It submits an expense with `POST /api/finance/expenses` and confirms one row is stored. There are no front-end unit tests.

## 6. Git ignore

**6.1** Paths to add to `.gitignore`: `/2-APP/config/` (the folder holding the Steward's configuration file, which may contain secrets; the project's `.gitignore` already lists it), `node_modules/`, `.venv/`, `2-APP/html/dist/`, `.wrangler/`, `python_modules/` (pywrangler's vendored packages), `__pycache__/` and `.pytest_cache/`.

## 7. Open questions

**7.1** None. The Steward's rulings answer every earlier question.
