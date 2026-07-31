# SQL WITH Clause

The SQL WITH clause (Common Table Expression or CTE) defines a temporary result set that can be used within a query. It simplifies complex SQL statements, making them easier to read, manage and reuse.

```sql
WITH cte_name (column1, column2, ...)
AS (
    -- subquery
    SELECT column1, column2, ...
    FROM table_name
    WHERE condition
)
SELECT *
FROM cte_name;
```
* cte_name is the name of the Common Table Expression.
* The query inside parentheses defines the temporary result set.
* The main query uses this CTE as if it were a table.


# References
* https://www.geeksforgeeks.org/sql/sql-with-clause/