## AVG()

The `AVG()` function returns the average value of a numeric column. 

### Syntax

```sql
SELECT AVG(column_name)
FROM table_name
WHERE condition;
```



### Example - Employee

* Same table as used in COUNT() function

  

The following query calculates the average salary of all the employees.

```SQL
SELECT AVG(Salary) AS AVERAGE FROM Employee;  -- Average: 21633
```



You can also calculate the average salary of each department using the following command:

```SQL
SELECT DeptId, AVG(Salary) AS AVERAGE FROM Employees GROUP BY DeptId;
```

| DeptId | AVERAGE |
| ------ | ------- |
| 10     | 24000   |
| 20     | 16000   |
| 30     | 34500   |
| 40     | 4800    |



## SUM() 

The `SUM()` function returns the total sum of a numeric column. 

### Syntax

```sql
SELECT SUM(column_name)
FROM table_name
WHERE condition;
```



### Example - Employee

* Same table as used in COUNT() function

  

The following query calculates the total salary of all the employees.

```SQL
SELECT SUM(Salary) AS "Total Salary" FROM Employees;  -- Total salary: 129800
```



You can also calculate the total salary of each department using the following query:

```SQL
SELECT DeptId, SUM(Salary) AS "Department wise Total Salary" FROM Employee 
GROUP BY DeptId;
```

Employee Table

| DeptId | Department wise Total Salary |
| ------ | ---------------------------- |
| 10     | 24000                        |
| 20     | 32000                        |
| 30     | 69000                        |
| 40     | 4800                         |



## MIN() & MAX()

### Syntax

```SQL
-- MIN()
SELECT MIN(column_name)
FROM table_name
WHERE condition;

-- MAX()
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```



### Example - Products

Below is a selection from the "Products" table in the Northwind sample database:

| ProductID | ProductName                  | SupplierID | CategoryID | Unit                | Price |
| :-------- | :--------------------------- | :--------- | :--------- | :------------------ | :---- |
| 1         | Chais                        | 1          | 1          | 10 boxes x 20 bags  | 18    |
| 2         | Chang                        | 1          | 1          | 24 - 12 oz bottles  | 19    |
| 3         | Aniseed Syrup                | 1          | 2          | 12 - 550 ml bottles | 10    |
| 4         | Chef Anton's Cajun Seasoning | 2          | 2          | 48 - 6 oz jars      | 22    |
| 5         | Chef Anton's Gumbo Mix       | 2          | 2          | 36 boxes            | 21.35 |



#### MIN()  

The following SQL statement finds the price of the cheapest product:

```SQL
SELECT MIN(Price) AS SmallestPrice
FROM Products;

-- OUTPUT

SmallestPrice
2.5
```



#### MAX()  

```sql
SELECT MAX(Price) AS LargestPrice
FROM Products; 

-- OUTPUT
LargestPrice
263.5
```





## REFERENCES

* https://www.geeksforgeeks.org/sql/sql-functions/
* https://www.w3schools.com/sql/sql_count_avg_sum.asp
* https://www.tutorialsteacher.com/sql/avg-function
