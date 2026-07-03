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

