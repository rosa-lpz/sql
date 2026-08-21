# SQL Subqueries in the SELECT clause


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

## Example 3
| employee_id | first_name | last_name | email                                                                       | phone_number | hire_date  | job_id |   salary | manager_id | department_id |
| ----------: | ---------- | --------- | --------------------------------------------------------------------------- | ------------ | ---------- | -----: | -------: | ---------: | ------------: |
|         100 | Steven     | King      | [steven.king@sqltutorial.org](mailto:steven.king@sqltutorial.org)           | 515.123.4567 | 1987-06-17 |      4 | 24000.00 |       NULL |             9 |
|         101 | Neena      | Kochhar   | [neena.kochhar@sqltutorial.org](mailto:neena.kochhar@sqltutorial.org)       | 515.123.4568 | 1989-09-21 |      5 | 17000.00 |        100 |             9 |
|         102 | Lex        | De Haan   | [lex.dehaan@sqltutorial.org](mailto:lex.dehaan@sqltutorial.org)             | 515.123.4569 | 1993-01-13 |      5 | 17000.00 |        100 |             9 |
|         103 | Alexander  | Hunold    | [alexander.hunold@sqltutorial.org](mailto:alexander.hunold@sqltutorial.org) | 590.423.4567 | 1990-01-03 |      9 |  9000.00 |        102 |          NULL |


```SQL
SELECT first_name, salary,
  (
    SELECT
      ROUND(AVG(salary),2) average_salary
    FROM
      employees
  )
FROM
  employees
ORDER BY
  salary;
```

# References
* https://w3schools.tech/tutorial/sql/sql-sub-queries
* https://www.sqltutorial.org/sql-subquery/