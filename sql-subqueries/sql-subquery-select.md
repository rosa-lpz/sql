# Subquery in the SELECT clause


Subqueries are most commonly used with the SELECT statement. They can be incredibly powerful for retrieving data based on dynamic conditions. Let's look at a more complex example:

##  Example 1
```SQL
SELECT 
    employee_name,
    salary,
    (SELECT AVG(salary) FROM employees) as avg_salary
FROM employees;
```
This query not only retrieves each employee's name and salary but also includes the average salary across all employees in each row. It's like having a mini-report for each employee!

##  Example 2
```SQL
SELECT e.name,d.name AS dept_name, (SELECT AVG(salary) FROM employees) AS avg_salary
FROM employees e
JOIN (
    SELECT id, name FROM departments
    WHERE location = 'NY') d
ON e.dept_id = d.id;
```


# References
* https://w3schools.tech/tutorial/sql/sql-sub-queries