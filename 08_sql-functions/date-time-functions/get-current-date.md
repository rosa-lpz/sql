# Get Current Date

## Comparison


Here are the common SQL functions for retrieving the **current date and time** in each database:

 | Database | Current date | Current date & time |
| --- | --- | --- |
| **PostgreSQL** | `CURRENT_DATE` | `CURRENT_TIMESTAMP` / `NOW()` |
| **MySQL** | `CURDATE()` | `NOW()` / `CURRENT_TIMESTAMP()` |
| **SQL Server** | `CAST(GETDATE() AS DATE)` | `GETDATE()` |
| **Databricks SQL** | `CURRENT_DATE()` | `CURRENT_TIMESTAMP()` |



## **PostgreSQL**

```
SELECT CURRENT_DATE;
SELECT CURRENT_TIMESTAMP;
-- or
SELECT NOW();
```

## **MySQL**
The NOW() function retrieves the current date and time in YYYY-MM-DD HH:MI:SS format.
```
SELECT CURDATE();
SELECT NOW();
-- or
SELECT CURRENT_TIMESTAMP();
```

## **SQL Server**

```
SELECT CAST(GETDATE() AS DATE);
SELECT GETDATE();

-- Higher precision:
SELECT SYSDATETIME();
```

##  **Databricks SQL**

```
SELECT CURRENT_DATE();
SELECT CURRENT_TIMESTAMP();
```

## Quick comparison

 If you specifically need the **current date and time**, the simplest equivalents are:

```
PostgreSQL   → CURRENT_TIMESTAMP
MySQL        → NOW()
SQL Server   → GETDATE()
Databricks   → CURRENT_TIMESTAMP()
```

 If you need **only the current date**:

```
PostgreSQL   → CURRENT_DATE
MySQL        → CURDATE()
SQL Server   → CAST(GETDATE() AS DATE)
Databricks   → CURRENT_DATE()
```

 One important difference: **SQL Server's `GETDATE()` returns a `datetime` value**, while `SYSDATETIME()` provides greater fractional-second precision.
 
 
 # References
 * https://www.w3schools.com/sql/func_mysql_now.asp
 * https://learn.microsoft.com/en-us/sql/t-sql/functions/getdate-transact-sql?view=sql-server-ver17
