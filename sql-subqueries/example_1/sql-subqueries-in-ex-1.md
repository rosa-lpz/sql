
# Example 1 - Employees

## Table Employees
| employee_id | first_name | last_name | email                                                                       | phone_number | hire_date  | job_id |   salary | manager_id | department_id |
| ----------: | ---------- | --------- | --------------------------------------------------------------------------- | ------------ | ---------- | -----: | -------: | ---------: | ------------: |
|         100 | Steven     | King      | [steven.king@sqltutorial.org](mailto:steven.king@sqltutorial.org)           | 515.123.4567 | 1987-06-17 |      4 | 24000.00 |       NULL |             9 |
|         101 | Neena      | Kochhar   | [neena.kochhar@sqltutorial.org](mailto:neena.kochhar@sqltutorial.org)       | 515.123.4568 | 1989-09-21 |      5 | 17000.00 |        100 |             9 |
|         102 | Lex        | De Haan   | [lex.dehaan@sqltutorial.org](mailto:lex.dehaan@sqltutorial.org)             | 515.123.4569 | 1993-01-13 |      5 | 17000.00 |        100 |             9 |
|         103 | Alexander  | Hunold    | [alexander.hunold@sqltutorial.org](mailto:alexander.hunold@sqltutorial.org) | 590.423.4567 | 1990-01-03 |      9 |  9000.00 |        102 |          NULL |

# Table Jobs
| job_id | job_title                       | min_salary | max_salary |
| -----: | ------------------------------- | ---------: | ---------: |
|      1 | Public Accountant               |    4200.00 |    9000.00 |
|      2 | Accounting Manager              |    8200.00 |   16000.00 |
|      3 | Administration Assistant        |    3000.00 |    6000.00 |
|      4 | President                       |   20000.00 |   40000.00 |
|      5 | Administration Vice President   |   15000.00 |   30000.00 |
|      6 | Accountant                      |    4200.00 |    9000.00 |
|      7 | Finance Manager                 |    8200.00 |   16000.00 |
|      8 | Human Resources Representative  |    4000.00 |    9000.00 |
|      9 | Programmer                      |    4000.00 |   10000.00 |
|     10 | Marketing Manager               |    9000.00 |   15000.00 |
|     11 | Marketing Representative        |    4000.00 |    9000.00 |
|     12 | Public Relations Representative |    4500.00 |   10500.00 |
|     13 | Purchasing Clerk                |    2500.00 |    5500.00 |
|     14 | Purchasing Manager              |    8000.00 |   15000.00 |
|     15 | Sales Manager                   |   10000.00 |   20000.00 |
|     16 | Sales Representative            |    6000.00 |   12000.00 |
|     17 | Shipping Clerk                  |    2500.00 |    5500.00 |
|     18 | Stock Clerk                     |    2000.00 |    5000.00 |
|     19 | Stock Manager                   |    5500.00 |    8500.00 |


# SQL Subquery with the IN operator 

The IN operator returns true if a value equals any value in a list of values. You can use a subquery to return a list of values for the IN operator:
```bash
IN subquery
```
## Employees with jobs related to Sales
For example, the following query uses a subquery with the IN operator to find all employees with the job titles related to Sales:
### Query
```SQL
SELECT first_name, last_name
FROM employees
WHERE job_id IN (
    SELECT job_id
    FROM jobs
    WHERE job_title LIKE '%Sales%'
);
```

### Output
```bash
first_name | last_name
------------+------------
 John       | Russell
 Karen      | Partners
 Jonathon   | Taylor
 Jack       | Livingston
 Kimberely  | Grant
 Charles    | Johnson
```

### How it works

* First, the subquery returns a list of job IDs with the job titles have the word "Sales":
```SQL
SELECT job_id
FROM jobs
WHERE job_title LIKE '%Sales%';
```
Output
```bash
job_id
15
16
```
* Second, the outer query selects the employees with the job_id in the job id list (15, 16).