# SQL FUNCTIONS

SQL functions are built-in operations that perform  calculations, manipulate data, and return results in queries, making  data handling simpler without writing complex code.

- Simplify calculations, formatting, and analysis.
- Enable conditional logic and aggregation.

## Categories of SQL Functions

SQL functions are classified based on how they process data and the type of results they return. 

### 1. Single Row Function

Single-row functions return one result per row of a query. They are widely used in SELECT lists, WHERE clauses, and conditional expressions to manipulate  and format individual data items. 

**Types of Single-Row Functions:**

- **Numeric Functions:**  Perform arithmetic or numeric operations (e.g., ROUND(), ABS(), POWER()).
- **Character Functions:** Manipulate text values (e.g., UPPER(), LOWER(), INITCAP()).
- **Date and Time Functions:** Handle date, time, and interval calculations (e.g., SYSDATE, NOW()). 
- **Conversion Functions:** Convert data from one type to another (e.g., TO_CHAR(), CAST()). 
- **Data Mining Functions:** Used in predictive modeling queries (e.g., PREDICTION_PROBABILITY()).

**Example:** First, we will [create](https://www.geeksforgeeks.org/sql/sql-create-table/) a demo SQL database and table, on which we will use the  Single Row Function.

![Screenshot-2025-11-13-124752](https://media.geeksforgeeks.org/wp-content/uploads/20251113124837655226/Screenshot-2025-11-13-124752.png)Loan_applicant



## Window Functions

### PARTITION BY

Calculates the average `extension` length within each office. The `PARTITION BY` clause divides the data into partitions based on the `officeCode` column.

**Example**

```sql
SELECT employeeNumber, 
       officeCode, 
       extension, 
       AVG(LENGTH(extension)) OVER (
           PARTITION BY officeCode
       ) AS avg_extension_length
  FROM employees;
```



### ORDER BY

Calculates a running total of `extension` lengths ordered by length in descending order.

**Example**

```sql
SELECT employeeNumber, 
       officeCode, 
       extension, 
       SUM(LENGTH(extension)) OVER (
           ORDER BY LENGTH(extension) DESC
       ) AS running_total_length
  FROM employees;
```



### PARTITION BY AND ORDER BY

Calculates a running total of `extension` lengths within each office, ordered by len

**Example**

```sql
SELECT employeeNumber, 
       officeCode, 
       extension, 
       SUM(LENGTH(extension)) OVER (
           PARTITION BY officeCode
           ORDER BY LENGTH(extension) DESC
       ) AS running_total_length
  FROM employees;
```



# 

# REFERENCES

* https://www.geeksforgeeks.org/sql/sql-functions/
* https://www.w3schools.com/sql/sql_count_avg_sum.asp
* https://www.tutorialsteacher.com/sql/count-function
* https://www.tutorialsteacher.com/sql/avg-function
* https://www.tutorialsteacher.com/sql/sum-function
* Aggregate functions: https://youtu.be/jcoJuc5e3RE
* https://dev.mysql.com/doc/refman/8.0/en/string-functions.html
* https://dev.mysql.com/doc/refman/8.0/en/numeric-functions.html
* https://www.w3schools.com/sql/sql_min_max.asp
* User defined functions: https://youtu.be/cdr0TuKCvDU

**SQL cheatsheets**

* https://www.dataquest.io/cheat-sheet/sql-cheat-sheet/
