# v0 User Experience Design (Draft)

**0.1** This draft describes the screens of BrownOrg version v0. `Objective.md` §2 defines v0. The Steward ruled that v0 is kept simple: one expense form and one table that saves the entries. A screen is one page the user sees in the browser. The path is: login, Finance, Income & Expense, expense form.

**0.2** The front end is a client. A client starts requests and shows results. It holds no business rules; the server decides every rule and the screen shows the server's answer (`Reference/Layer_Encapsulation.md` §4). The front end uses Vue 3 with PrimeVue, a set of ready-made screen parts called components. Each part is named where it is used.

**0.3** Each screen has an address, the text after the site name in the browser bar. The addresses mirror the navigation: `/` for the login screen (§1), `/modules` for the module screen (§2), `/finance` for Finance, `/finance/income-expense` for the Income & Expense screen (§3) and `/finance/income-expense/expense` for the expense form (§4).

## 1. Login screen

**1.1** Purpose: admit the user with one shared password, through the use case `sign_in`. This is the home page. The password is fixed in the code and is never written in this design.

**1.2** Elements: a `Password` component, a text box that hides what is typed; a `Button` "Sign in"; a `Message`, a small notice, for errors. Pressing Enter submits.

**1.3** On success: the module screen opens (§2). There are no sessions, no later sign-in checks and no sign-out. On error: a wrong password shows "That password is not correct." and the user stays here.

## 2. Module screen

**2.1** Purpose: let the user pick a module, one area of the app. Finance is the only module in v0. The screen shows one `Card`, a box with a title, reading "Finance". No other card appears.

**2.2** Navigation: clicking the Finance card opens the section screen (§3). The screen has no error state.

## 3. Income & Expense screen

**3.1** Purpose: let the user pick a section of Finance. The section `income_expense` is shown as "Income & Expense". In v0 the screen shows one `Card` for the use case `record_expense`, labelled "Record expense". It shows no Balance Sheet card and no income card.

**3.2** Navigation: a `Breadcrumb`, a trail of links reading "Home > Finance > Income & Expense", goes back one or two screens. Clicking the card opens the expense form (§4). The screen has no error state.

## 4. Expense form

**4.1** Purpose: create one expense record through `record_expense`. An expense is money that was spent.

**4.2** Required fields. `expense_date`, the day the money was spent: a `DatePicker`, a calendar pop-up. `amount_cents`: an `InputNumber`, a number box where the user types dollars and cents, such as 12.50. The screen converts it to whole cents (1250) before it sends the request. The `InputNumber` settings allow only an amount of at least 0.01 with at most two decimals, shown as dollars, and the date is required. These checks are a convenience only: the business logic enforces the same rules for every client, so they are settings on the components, not separate rule code.

**4.3** Optional fields, all plain text. `category`: an `InputText`, a one-line box. `payee`, who received the money: an `InputText`. `note`: a `Textarea`, a multi-line box. There is no currency, no category list, no date rule and no length limit.

**4.4** Buttons: a `Button` "Save expense", and a link "Cancel" back to §3.

**4.5** On success: a `Toast`, a short pop-up, reads "Expense saved." The form clears, so the user can enter the next expense.

**4.6** On error: if the server rejects the entry, the screen shows what to fix in red under each field named. The form keeps what the user typed.

## 5. Open questions

None.
