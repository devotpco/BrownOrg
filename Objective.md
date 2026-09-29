# Objective

**0.1** This file is the objective statement of the project BrownOrg. An objective statement says what a project builds, why it builds it, and what success is for each version of what it builds. Success is stated as facts a person can observe. Every decision about what goes into a version is checked against this file.

**0.2** The Steward is the human who holds the decision on the project. The project manager keeps this file on the Steward's behalf. The project manager asks the Steward when the objective is unclear. The Library note `Method/Cross_Functional_Team.md` defines both roles. The Library is the folder `/Users/jerry/DEV/DEVLibrary/`, which holds rules and formats that any project may reuse.

## 1. What is built, and why

**1.1** BrownOrg is an application for managing the life of the Steward's family, which the Steward calls the Brown Organization. It is meant to hold goals, finance, a bucket list, getting-things-done lists and more. The Steward stated this on 2026-09-28:

> This app is for the management for the Brown Organization. By Brown Org, I mean my life, my family's life. Goals, finance, bucket list, GTDs, etc, etc. So, it will have a number of modules with synchronization points between them.

**1.2** A module is one area of the application, such as Finance. A synchronization point is a place where two modules share or exchange data. The application will have several modules and several synchronization points.

**1.3** The database and the design are planned for more than one module from the start. A user must pick a module, then a section of it, to reach a form. The Steward stated this on 2026-09-28:

> Plan the DB and design for more than one module; So, the user should need to pick the Finance module, Income section, etc to access the intake form. Create only for now, edit and delete later

## 2. Version v0

**2.1** Version v0 has two purposes. The first is to deploy the site on Cloudflare, a hosting platform. The second is to test one use case from start to finish. The Steward stated this on 2026-09-28:

> That's the plan v0 gets us deployed in CF and a use case test. Then, I pay the $5 and we build on our preferred stack.

**2.2** In v0, the website is live on the Steward's Cloudflare account. It is deployed from the git branch `dev_claude` and tested live there.

**2.3** In v0, a login page admits a user with a single shared password. The password is fixed in the code. There are no accounts. This is insecure on purpose. User accounts, roles, permissions and sign-in through another service (OAuth) come later.

**2.4** In v0, after login, the user picks the Finance module. The user then picks its Income & Expense section. The user then reaches the expense intake form.

**2.5** Income & Expense is the section of Finance that follows the income statement, as against the balance sheet. The Steward stated this on 2026-09-28:

> Income and Expense section of Finance, as in the Income Expense statement (vs for example, our balance sheet)

**2.6** v0 records expenses only. Income comes later, possibly as a second form. The Steward stated this on 2026-09-28:

> Could be 2. v0 expenses only

**2.7** v0 creates records only. Editing and deleting come later.

**2.8** Each expense record is stored in D1, Cloudflare's database.

**2.9** v0 runs as a Python Worker, which is Cloudflare's way of running Python, on Cloudflare's free plan. Flask runs on the server. Vue with PrimeVue runs in the browser.

## 3. After v0

**3.1** After v0, the Steward moves to Cloudflare's paid plan. The team then builds on the Steward's preferred stack.

## 4. Constraints

**4.1** The layer rules in the Library note `Reference/Layer_Encapsulation.md`, section 4, apply to every version. Among them, what is built and tested locally runs on Cloudflare with no changes.

## 5. Success for v0

**5.1** v0 succeeds when a person can observe all of these facts:

1. The site loads at its Cloudflare address.
2. The login page refuses a wrong password and admits the right one.
3. After login, the user can pick Finance, then Income & Expense, and reach the expense form.
4. Submitting the form stores one expense record in the hosted D1 database, and the record can be seen there afterwards.
5. The code tested locally deploys to Cloudflare with no code changes.

**5.2** Open questions for the Steward are kept in the parking lot, `9-Backlog/Parking_Lot/Parking_Lot.md`.
