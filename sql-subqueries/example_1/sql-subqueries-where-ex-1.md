# Example 1 - Employees

## Table Employees
| employee_id | first_name | last_name | email                                                                       | phone_number | hire_date  | job_id |   salary | manager_id | department_id |
| ----------: | ---------- | --------- | --------------------------------------------------------------------------- | ------------ | ---------- | -----: | -------: | ---------: | ------------: |
|         100 | Steven     | King      | [steven.king@sqltutorial.org](mailto:steven.king@sqltutorial.org)           | 515.123.4567 | 1987-06-17 |      4 | 24000.00 |       NULL |             9 |
|         101 | Neena      | Kochhar   | [neena.kochhar@sqltutorial.org](mailto:neena.kochhar@sqltutorial.org)       | 515.123.4568 | 1989-09-21 |      5 | 17000.00 |        100 |             9 |
|         102 | Lex        | De Haan   | [lex.dehaan@sqltutorial.org](mailto:lex.dehaan@sqltutorial.org)             | 515.123.4569 | 1993-01-13 |      5 | 17000.00 |        100 |             9 |
|         103 | Alexander  | Hunold    | [alexander.hunold@sqltutorial.org](mailto:alexander.hunold@sqltutorial.org) | 590.423.4567 | 1990-01-03 |      9 |  9000.00 |        102 |          NULL |


# SQL subquery in the WHERE clause
## Employees with higher salary
The following statement uses a subquery to find the employees who have the highest salary:
### Query
```SQL
SELECT first_name,salary
FROM employees
WHERE salary = (
    SELECT MAX(salary)
    FROM employees
  );
```
### Output
```bash
first_name |  salary
------------+----------
 Steven     | 24000.00
```
### How it works
* First, the subquery returns the max salary from the salary column of the employees table.
* Second, the outer query uses the value returned by the subquery and returns the employee with the highest salary.

## Employees with a salary higher than the average

## Query
```SQL
SELECT first_name,salary
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
  );
```
### Output
```bash
first_name |  salary
------------+----------
 John       |  8200.00
 Adam       |  8200.00
 William    |  8300.00
 Jack       |  8400.00
 Jonathon   |  8600.00
```
### How it works
* AVG(salary) = 8060
* First, the subquery returns the avg salary from the salary column of the employees table.
* Second, the outer query uses the value returned by the subquery and returns the employees with a salary higher than the average.

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

# Reference
* https://www.sqltutorial.org/sql-subquery/