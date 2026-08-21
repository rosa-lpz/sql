
# Example 1 - Employees

## Table Employees
| employee_id | first_name | last_name | email                                                                       | phone_number | hire_date  | job_id |   salary | manager_id | department_id |
| ----------: | ---------- | --------- | --------------------------------------------------------------------------- | ------------ | ---------- | -----: | -------: | ---------: | ------------: |
|         100 | Steven     | King      | [steven.king@sqltutorial.org](mailto:steven.king@sqltutorial.org)           | 515.123.4567 | 1987-06-17 |      4 | 24000.00 |       NULL |             9 |
|         101 | Neena      | Kochhar   | [neena.kochhar@sqltutorial.org](mailto:neena.kochhar@sqltutorial.org)       | 515.123.4568 | 1989-09-21 |      5 | 17000.00 |        100 |             9 |
|         102 | Lex        | De Haan   | [lex.dehaan@sqltutorial.org](mailto:lex.dehaan@sqltutorial.org)             | 515.123.4569 | 1993-01-13 |      5 | 17000.00 |        100 |             9 |
|         103 | Alexander  | Hunold    | [alexander.hunold@sqltutorial.org](mailto:alexander.hunold@sqltutorial.org) | 590.423.4567 | 1990-01-03 |      9 |  9000.00 |        102 |          NULL |

# Subquery in the SELECT clause

## Average salary of all employees
The following example uses a subquery in the SELECT clause to retrieve the first name, salary, and average salary of all employees:

### Query
```SQL
SELECT first_name,salary,
(
    SELECT
      ROUND(AVG(salary),2) average_salary
    FROM
      employees
  )
FROM employees
ORDER BY salary;
```
### Output
```bash
  first_name  |  salary  | average_salary
-------------+----------+----------------
 Karen       |  2500.00 |        8060.00
 Guy         |  2600.00 |        8060.00
 Irene       |  2700.00 |        8060.00
 Sigal       |  2800.00 |        8060.00
 Shelli      |  2900.00 |        8060.00
 
```


# Reference
* https://www.sqltutorial.org/sql-subquery/