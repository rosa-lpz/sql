# SQL Subquery
A SQL subquery is a query nested within another SQL query, used to perform operations that require multiple steps or complex logic. Subqueries can simplify queries, improve readability, and allow for dynamic data retrieval based on the results of another query.

It allows complex filtering, aggregation and data manipulation by using the result of one query inside another. They are an essential tool when we need to perform operations like:

* Apply aggregate functions like SUM, COUNT or AVG dynamically.
* Update data using values from other tables.
* Delete rows based on conditions returned by another query.

**Syntax**

```SQL
SELECT column_name
FROM table_name
WHERE column_name operator
      (SELECT column_name 
       FROM table_name 
       WHERE condition);

```



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





# REFERENCES

* https://www.sqltutorial.org/sql-subquery/
* https://w3schools.tech/tutorial/sql/sql-sub-queries
* https://www.geeksforgeeks.org/sql/sql-subquery/
