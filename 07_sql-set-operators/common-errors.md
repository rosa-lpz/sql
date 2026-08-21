# Common errors with UNION

## UNION two tables with different column counts 

When you try to UNION two tables with different column counts (179 vs 180), SQL will throw an error because **UNION requires the same number of columns in both queries**.

Here are your options:

## Fix the Column Mismatch

**Option 1: Add a NULL placeholder to the smaller table**
```sql
SELECT col1, col2, ..., col179, NULL AS missing_col  -- add NULL as the 180th column
FROM table_179_cols

UNION ALL

SELECT col1, col2, ..., col180
FROM table_180_cols;
```

**Option 2: Drop the extra column from the larger table**
```sql
SELECT col1, col2, ..., col179  -- exclude the extra column
FROM table_180_cols

UNION ALL

SELECT col1, col2, ..., col179
FROM table_179_cols;
```

---

## Practical Tips for 180 Columns

With that many columns, writing them manually is painful. You can **generate the column list dynamically**:

**In PostgreSQL / SQL Server / MySQL** — query the information schema to find which column is missing:
```sql
-- Find columns in table_180 but NOT in table_179
SELECT column_name
FROM information_schema.columns
WHERE table_name = 'table_180'

EXCEPT

SELECT column_name
FROM information_schema.columns
WHERE table_name = 'table_179';
```

This tells you exactly which column to NULL-pad or exclude.

---

## Which approach to choose?

| Situation | Recommendation |
|---|---|
| The extra column has meaningful data | Add `NULL AS col_name` to the smaller table |
| The extra column is irrelevant | Exclude it from the larger table |
| You want all data preserved | Consider a `JOIN` instead of `UNION` |
| Column names differ but data is compatible | Alias columns to match names |

---

**Most common fix** is the NULL placeholder — just identify the missing column and pad it on the side that lacks it. Would you like help generating the full query dynamically for your specific database (PostgreSQL, MySQL, SQL Server, etc.)?