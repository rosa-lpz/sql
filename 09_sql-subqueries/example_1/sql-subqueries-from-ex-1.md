
# Example 1 - Employees

## Table Employees
| employee_id | first_name | last_name | email                                                                       | phone_number | hire_date  | job_id |   salary | manager_id | department_id |
| ----------: | ---------- | --------- | --------------------------------------------------------------------------- | ------------ | ---------- | -----: | -------: | ---------: | ------------: |
|         100 | Steven     | King      | [steven.king@sqltutorial.org](mailto:steven.king@sqltutorial.org)           | 515.123.4567 | 1987-06-17 |      4 | 24000.00 |       NULL |             9 |
|         101 | Neena      | Kochhar   | [neena.kochhar@sqltutorial.org](mailto:neena.kochhar@sqltutorial.org)       | 515.123.4568 | 1989-09-21 |      5 | 17000.00 |        100 |             9 |
|         102 | Lex        | De Haan   | [lex.dehaan@sqltutorial.org](mailto:lex.dehaan@sqltutorial.org)             | 515.123.4569 | 1993-01-13 |      5 | 17000.00 |        100 |             9 |
|         103 | Alexander  | Hunold    | [alexander.hunold@sqltutorial.org](mailto:alexander.hunold@sqltutorial.org) | 590.423.4567 | 1990-01-03 |      9 |  9000.00 |        102 |          NULL |

# Subquery in the FROM clause

## Average salary of all employees
The following example uses a subquery in the SELECT clause to retrieve the first name, salary, and average salary of all employees:

### Query
```SQL
SELECT
  ROUND(AVG(department_salary), 0) average_department_salary
FROM
  (
    SELECT
      department_id,
      SUM(salary) department_salary
    FROM
      employees
    GROUP BY
      department_id
  );
```
### Output
```bash
average_department_salary
---------------------------
                     29309
```

### How it works?
* First, the subquery returns a result set that includes department_id and total salary for each department
* Second, the outer query calculates the average total salary of all departments and rounds it off with zero decimal places.

#### Output of the subquery
```SQL
SELECT
      department_id,
      SUM(salary) department_salary
    FROM
      employees
    GROUP BY
      department_id
```

Output
```
|department_id	|department_salary|
|---|---|
|1|	4400.0000000000000000|
|2|	9500.0000000000000000|
|3|	4150.0000000000000000|
|4|	6500.0000000000000000|
|5|	5885.7142857142857143|
|6|	5760.0000000000000000|
|7|	10000.0000000000000000|
|8|	9616.6666666666666667|
|9	|19333.333333333333|
|10	|8600.0000000000000000|
|11|	10150.0000000000000000|
```
# Reference
* https://www.sqltutorial.org/sql-subquery/