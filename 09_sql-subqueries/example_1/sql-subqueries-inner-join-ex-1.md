
# Example 1 - Employees

## Table Employees
| employee_id | first_name | last_name | email                                                                       | phone_number | hire_date  | job_id |   salary | manager_id | department_id |
| ----------: | ---------- | --------- | --------------------------------------------------------------------------- | ------------ | ---------- | -----: | -------: | ---------: | ------------: |
|         100 | Steven     | King      | [steven.king@sqltutorial.org](mailto:steven.king@sqltutorial.org)           | 515.123.4567 | 1987-06-17 |      4 | 24000.00 |       NULL |             9 |
|         101 | Neena      | Kochhar   | [neena.kochhar@sqltutorial.org](mailto:neena.kochhar@sqltutorial.org)       | 515.123.4568 | 1989-09-21 |      5 | 17000.00 |        100 |             9 |
|         102 | Lex        | De Haan   | [lex.dehaan@sqltutorial.org](mailto:lex.dehaan@sqltutorial.org)             | 515.123.4569 | 1993-01-13 |      5 | 17000.00 |        100 |             9 |
|         103 | Alexander  | Hunold    | [alexander.hunold@sqltutorial.org](mailto:alexander.hunold@sqltutorial.org) | 590.423.4567 | 1990-01-03 |      9 |  9000.00 |        102 |          NULL |

# Subquery in the INNER JOIN clause

## Employees who earn above the company’s average salary:
The following example uses a subquery in the INNER JOIN clause of the outer query to retrieve employees who earn above the company’s average salary:

### Query
```SQL
SELECT first_name, last_name, salary, s.avg_salary
FROM employees e
INNER JOIN (
  SELECT
    ROUND(AVG(salary), 0) AS avg_salary
  FROM employees) s 
ON e.salary > s.avg_salary
ORDER BY salary;
```
### Output
```bash
first_name | last_name  |  salary  | avg_salary
------------+------------+----------+------------
 John       | Chen       |  8200.00 |       8060
 Adam       | Fripp      |  8200.00 |       8060
 William    | Gietz      |  8300.00 |       8060
 Jack       | Livingston |  8400.00 |       8060
 Jonathon   | Taylor     |  8600.00 |       8060
```

### How it works?
* First, the subquery calculates the company’s average salary.
* Second, the outer query retrieves employees earning above that average salary.

#### Output of the subquery
```SQL
SELECT
  ROUND(AVG(salary), 0) AS avg_salary
FROM employees
```
Output
```
avg_salary
8060
```

# Reference
* https://www.sqltutorial.org/sql-subquery/