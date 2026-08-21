# SQL Window Functions
SQL window functions allow performing calculations across a set of rows that are related to the current row, without collapsing the result into a single value. They are commonly used for tasks like aggregates, rankings and running totals. The OVER clause defines the “window” of rows for the calculation. It can:

* PARTITION BY: It divides the data into groups using PARTITION BY.
* ORDER BY: It specifies the order of rows within each group using ORDER BY.
With this, functions such as SUM(), AVG(), ROW_NUMBER(), RANK() and DENSE_RANK() can be applied in a controlled way.
Syntax:

```sql
SELECT column_name1, 
       window_function(column_name2) 
       OVER ([PARTITION BY column_name3] [ORDER BY column_name4]) AS new_column
FROM table_name;
```

* window_function: Aggregate or ranking function (SUM(), AVG(), ROW_NUMBER(), etc.)
* column_name1: Column(s) to display
* column_name2: Column used by the window function
* column_name3: Column for grouping (PARTITION BY)
* column_name4: Column for ordering (ORDER BY)
* new_column: Alias for the window function result
* table_name: Table to select data from

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


# References
* https://www.geeksforgeeks.org/sql/window-functions-in-sql/
* https://www.dataquest.io/cheat-sheet/sql-cheat-sheet/#item-6