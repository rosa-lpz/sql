# SQL Subqueries in the FROM clause

Subqueries in the FROM clause, known as derived tables or inline views, act as temporary tables for queries. These allow flexible reshaping and summarizing of data on the fly. You can treat the results of that subquery like any other table. You can join to it, filter it, group it, and so on. 
- A subquery within the FROM clause is a full SELECT statement in parentheses, given an alias for reference in the main query.
- Use these subqueries to transform, aggregate, or filter data before joining with other tables, often making queries more efficient and readable.
- Subqueries help summarize data. For example, find each customer’s total spending in the orders table before joining to the customers table.
- Nesting subqueries allows step-by-step query building, like filtering orders by year, then aggregating, then ranking top customers.
- Each subquery works like a building block; testability improves query accuracy and debugging.
- This technique avoids unnecessary temporary tables, keeping queries organized and easier to manage.


## Syntax
```SQL
SELECT column_name
FROM (
    SELECT column_name 
    FROM table_name 
    WHERE condition
)AS subquery_alias;

```
## Example 1

```SQL
SELECT employee_name
FROM employees
WHERE department_id = (SELECT department_id FROM departments WHERE department_name = 'Marketing');
```

```sql
SELECT product_name, price
FROM products
WHERE price > (SELECT AVG(price) FROM products);
```

## References
* Udacity - SQL for data analysis