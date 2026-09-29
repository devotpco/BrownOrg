# v0 Data Model (draft)

**0.1** This draft defines how BrownOrg v0 stores data. The Steward ruled "keep it simple" for v0: one expense form and one table. A migration is a numbered SQL file that changes the database's structure. A table is a named set of rows. A row is one record.

## 1. Setting

**1.1** The database is Cloudflare D1, which is SQLite-compatible. Only the data layer reaches it, through a Worker binding (Cloudflare's link from code to a resource). The data layer uses plain SQL with bound parameters.

**1.2** D1 runs on Cloudflare's free plan. DEV is the local D1, which keeps its data between runs. PROD is the hosted D1.

## 2. The table

**2.1** v0 has one table, `fin_expense`. The prefix `fin_` marks the Finance module. One row is one expense. v0 has no other table.

**2.2** Columns:

| Column | Type | Rule |
|---|---|---|
| `id` | INTEGER | assigned by the database |
| `expense_date` | TEXT | required; the day the money was spent, as `YYYY-MM-DD` |
| `amount_cents` | INTEGER | required; whole cents, greater than zero |
| `category` | TEXT | optional |
| `payee` | TEXT | optional |
| `note` | TEXT | optional |

## 3. The migration

**3.1** One migration file creates the table: `2-APP/Data/migrations/0001_create_fin_expense.sql`. Wrangler, Cloudflare's command-line tool, applies it to DEV and then to PROD.

**3.2** The file holds this statement:

```sql
CREATE TABLE fin_expense (
  id            INTEGER PRIMARY KEY AUTOINCREMENT,
  expense_date  TEXT    NOT NULL,
  amount_cents  INTEGER NOT NULL CHECK (amount_cents > 0),
  category      TEXT,
  payee         TEXT,
  note          TEXT
);
```

## 4. Open questions

None.
