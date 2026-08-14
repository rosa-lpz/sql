# Common Table Expression (CTE) in SQL
A Common Table Expression (CTE) is a temporary result set in SQL that you can reference within a single query. CTEs simplify complex queries, make them easier to read and can be reused multiple times within the same query. It is used for:

* Performing recursive operations, such as traversing hierarchical data.
* Breaking down multi-step calculations into manageable parts.
* Replacing nested subqueries in complex data retrieval task

# SQL WITH Clause

The SQL WITH clause (Common Table Expression or CTE) defines a temporary result set that can be used within a query. It simplifies complex SQL statements, making them easier to read, manage and reuse.

+ `WITH` creates a **Common Table Expression (CTE)**.

## Syntax

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



## Key Categories / Functional Classification of CTEs

`WITH` clauses are generally classified into three structural patterns based on how they operate:

### Non-Recursive (Basic) CTE

A single temporary result set used to break down complex queries or avoid duplicate subqueries.

```sql
WITH HighValueOrders AS (
    SELECT customer_id, SUM(amount) AS total_spent
    FROM orders
    GROUP BY customer_id
)
SELECT * 
FROM HighValueOrders 
WHERE total_spent > 1000;
```
### Chained / Multiple CTEs
You can define multiple temporary tables inside a single WITH block separated by commas. Later CTEs can reference earlier CTEs in the sequence.

```sql
WITH RegionalSales AS (
    SELECT region, SUM(amount) AS total_sales
    FROM orders
    GROUP BY region
),
TopRegions AS (
    SELECT region 
    FROM RegionalSales 
    WHERE total_sales > 50000
)
SELECT * FROM TopRegions;
```
### Recursive CTE (WITH RECURSIVE)
A CTE that references itself. It is designed for processing hierarchical or graph-structured data (e.g., organizational charts, bill-of-materials, or tree structures).

```sql
WITH RECURSIVE OrgChart AS (
    -- Anchor member (base case)
    SELECT employee_id, manager_id, 1 AS level
    FROM employees
    WHERE manager_id IS NULL

    UNION ALL

    -- Recursive member (joins back to the CTE)
    SELECT e.employee_id, e.manager_id, o.level + 1
    FROM employees e
    JOIN OrgChart o ON e.manager_id = o.employee_id
)
SELECT * FROM OrgChart;
```



# References
* https://www.geeksforgeeks.org/sql/cte-in-sql/
* https://www.geeksforgeeks.org/sql/sql-with-clause/
* https://www.tutorialspoint.com/sql/sql-common-table-expression.htm
* https://www.datacamp.com/tutorial/cte-sql
* https://biwave.substack.com/p/common-table-expressions-in-sql