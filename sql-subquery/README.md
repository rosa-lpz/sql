# SQL Subquery

A subquery is an SQL query nested inside another [query](https://www.sqltutorial.org/sql-select/). The query that contains a subquery is known as an outer query.

**Syntax**

```SQL
SELECT
  select_list
FROM
  table1
  INNER JOIN table2 ON join_condition
WHERE
  filter_condition;
```

- The `SELECT` clause can accept a single value, which can be a column or an expression.
- The `FROM` and `INNER JOIN` clauses can accept a result set such as a table.
- The `WHERE` can accept a single value, which can be a column or an expression.

* Note: The join can be `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, or `FULL JOIN`.



## Example 1

```SQL
SELECT employee_name
FROM employees
WHERE department_id = (SELECT department_id FROM departments WHERE department_name = 'Marketing');
```



## Rules to be followed

Before we dive deeper, let's go over some important rules for using subqueries:

1. Subqueries must be enclosed in parentheses.
2. A subquery can have only one column in the SELECT clause, unless multiple columns are in the main query for comparison.
3. An ORDER BY command cannot be used in a subquery, although the main query can use an ORDER BY.
4. Subqueries that return more than one row can only be used with multiple value operators such as the IN operator.

Here's a handy table summarizing these rules:

| Rule          | Description                                                  |
| ------------- | ------------------------------------------------------------ |
| Parentheses   | Subqueries must be enclosed in parentheses                   |
| Single Column | Subquery SELECT usually returns only one column              |
| No ORDER BY   | ORDER BY can't be used in a subquery                         |
| Multiple Rows | Use multiple value operators for subqueries returning multiple rows |

## Subqueries with the SELECT Statement

Subqueries are most commonly used with the SELECT statement. They can be incredibly powerful for retrieving data based on dynamic conditions. Let's look at a more complex example:

```sql
SELECT product_name, price
FROM products
WHERE price > (SELECT AVG(price) FROM products);
```



# REFERENCES

* https://www.sqltutorial.org/sql-subquery/
* https://w3schools.tech/tutorial/sql/sql-sub-queries
