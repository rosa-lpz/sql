# Concatenate columns in SQL

To concatenate **entire columns** in a table rather than static strings, you simply pass the column names into the operators or functions.

Here is how to concatenate columns across Databricks/Spark SQL, PostgreSQL, and SQL Server using a practical example.

### The Example Data

Imagine we have a `users` table with the following data:

| first_name | middle_name | last_name |
| --- | --- | --- |
| John | NULL | Doe |
| Jane | Marie | Smith |

---



## PostgreSQL

If you use the `||` operator on a column containing a `NULL` value, the entire row's result becomes `NULL`. Using `CONCAT` or `CONCAT_WS` prevents this.

```sql
-- Method 1: Standard CONCAT (Converts NULL to an empty string, but beware of extra spaces)
SELECT CONCAT(first_name, ' ', middle_name, ' ', last_name) AS full_name 
FROM users;

-- Method 2: CONCAT_WS (Cleanest output)
SELECT CONCAT_WS(' ', first_name, middle_name, last_name) AS full_name 
FROM users;

```

---

## SQL Server (T-SQL)

In SQL Server, using the `+` operator on columns requires you to manually wrap nullable columns in an `ISNULL` or `COALESCE` function to prevent the entire string from wiping out. Otherwise, use `CONCAT`.

```sql
-- Method 1: The + Operator (Requires ISNULL safety net)
SELECT first_name + ' ' + ISNULL(middle_name + ' ', '') + last_name AS full_name 
FROM users;

-- Method 2: CONCAT (Safe from NULLs, but might leave a double space for John)
SELECT CONCAT(first_name, ' ', middle_name, ' ', last_name) AS full_name 
FROM users;

-- Method 3: CONCAT_WS (SQL Server 2017+ | Cleanest approach)
SELECT CONCAT_WS(' ', first_name, middle_name, last_name) AS full_name 
FROM users;

```

---

## Databricks & Spark SQL

In Spark SQL, using `CONCAT_WS` is highly recommended for columns because it gracefully handles missing middle names without leaving ugly double spaces or resulting in `NULL`.

```sql
-- Method 1: The || Operator (Will return NULL for John due to the missing middle name)
SELECT first_name || ' ' || middle_name || ' ' || last_name AS full_name 
FROM users;

-- Method 2: CONCAT_WS (Best choice: Automatically skips NULLs and handles spacing)
SELECT CONCAT_WS(' ', first_name, middle_name, last_name) AS full_name 
FROM users;

```

* **John's Result (Method 2):** `John Doe`
* **Jane's Result (Method 2):** `Jane Marie Smith`

---

## Notes

When combining columns, **always assume some rows will contain `NULL` values**.

* If you want a specific separator (like a space or a comma) between your columns, use **`CONCAT_WS(' ', col1, col2, col3)`**. It is supported by all three platforms and eliminates formatting headaches caused by missing data.