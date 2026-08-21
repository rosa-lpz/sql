# Concatenation Strings in SQL

String concatenation works a bit differently depending on the flavor of SQL we are using. While some databases support the standard `||` operator, others rely strictly on functions like `CONCAT()` or `CONCAT_WS()`.

Here is how to handle concatenation across Databricks, Spark SQL, PostgreSQL, and SQL Server.

---

## Databricks & Spark SQL

Databricks (which runs on Apache Spark) is highly flexible. It supports both the standard pipe operator and built-in functions.

* **The `||` Operator:** Standard and clean.
* **`CONCAT()`:** Joins strings together. If *any* argument is `NULL`, the entire result becomes `NULL`.
* **`CONCAT_WS()` (Concat With Separator):** The first argument is the separator. **Bonus:** It automatically skips `NULL` values instead of ruining the whole string.

```sql
-- Using the pipe operator
SELECT 'Spark' || ' ' || 'SQL'; -- Result: 'Spark SQL'

-- Using CONCAT
SELECT CONCAT('Databricks', ' ', 'Lakehouse'); -- Result: 'Databricks Lakehouse'

-- Using CONCAT_WS (Skips NULLs safely)
SELECT CONCAT_WS(', ', 'Apple', NULL, 'Banana'); -- Result: 'Apple, Banana'

```

---

## PostgreSQL

PostgreSQL strictly adheres to the ANSI SQL standard.

* **The `||` Operator:** The most common way to concatenate in Postgres. Note that `'Text' || NULL` will result in `NULL`.
* **`CONCAT()`:** Safer than `||` because it converts `NULL` values into empty strings (`''`) instead of turning the whole result into `NULL`.
* **`CONCAT_WS()`:** Works exactly like Spark's version, using a defined separator and ignoring `NULL`s.

```sql
-- Using the pipe operator
SELECT 'Postgre' || 'SQL'; -- Result: 'PostgreSQL'

-- Using CONCAT (NULL-safe)
SELECT CONCAT('User: ', NULL, 'John Doe'); -- Result: 'User: John Doe'

-- Using CONCAT_WS
SELECT CONCAT_WS('-', '2026', '07', '02'); -- Result: '2026-07-02'

```

---

## SQL Server (T-SQL)

SQL Server historically used the plus sign (`+`) for concatenation, but modern versions support standard functions too.

* **The `+` Operator:** The traditional T-SQL method. Be careful: if `SET CONCAT_NULL_YIELDS_NULL` is ON (the default), adding a `NULL` will make the whole string `NULL`.
* **`CONCAT()`:** Introduced in SQL Server 2012. It automatically converts `NULL` values to empty strings.
* **`CONCAT_WS()`:** Introduced in SQL Server 2017. Joins strings with a separator and ignores `NULL`s.

```sql
-- Using the + operator
SELECT 'SQL' + ' ' + 'Server'; -- Result: 'SQL Server'

-- Using CONCAT (NULL-safe)
SELECT CONCAT('Total: ', NULL, 100); -- Result: 'Total: 100'

-- Using CONCAT_WS
SELECT CONCAT_WS(' | ', 'Error', 'Code 500', NULL); -- Result: 'Error | Code 500'

```

---

## Quick Reference Summary

| Database / Engine | Operator | `CONCAT()` | `CONCAT_WS()` | `NULL` Handling in Basic Operator/Function |
| --- | --- | --- | --- | --- |
| **Databricks / Spark SQL** | ` |  | ` | Yes |
| **PostgreSQL** | ` |  | ` | Yes |
| **SQL Server** | `+` | Yes | Yes (2017+) | `+` returns `NULL`. `CONCAT()` ignores `NULL`. |

> 💡 **Pro-Tip:** If you are writing cross-platform SQL queries or want to avoid bugs caused by unexpected missing data, **`CONCAT()`** or **`CONCAT_WS()`** are generally the safest choices across all these systems because of how they gracefully handle `NULL` values.