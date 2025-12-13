# SQL FUNCTIONS

## COUNT()

The COUNT() function is an aggregate function that is used to find the number of values in the specified column **excluding NULL values.** It can be applied on numeric, character, or date values.

The `COUNT()` function returns the number of rows that matches a specified criterion.

### Syntax

```SQL
SELECT COUNT(column_name)
FROM table_name
WHERE condition;

--OR

SELECT COUNT([ALL | DISTINCT] expression | column_name)
FROM table_name
[WHERE condition]
[GROUP BY]    ;
```



### Example - Employee

| EmpId | FirstName | LastName | Email               | Salary | DeptId |
| ----- | --------- | -------- | ------------------- | ------ | ------ |
| 1     | John      | King     | 'john.king@abc.com' | 24000  | 10     |
| 2     | James     | Bond     |                     | 17000  | 20     |
| 3     | Neena     | Kochhar  | 'neena@test.com'    | 15000  | 20     |
| 4     | Lex       | King     | 'lex@test.com'      | 9000   | 30     |
| 5     | Amit      | Patel    |                     | 60000  | 30     |
| 6     | Abdul     | Kalam    | 'abdul@test.com'    | 4800   | 40     |





```SQL
														 				-- OUTPUT
-- Specify the column name to count the total values 
-- in that column excluding NULL values. 
-- counts the total records in the `FirstName` column.                                   
SELECT COUNT(FirstName) AS "Total" FROM Employee;  							-- 6

-- The COUNT() function excludes the NULL values.
SELECT COUNT(Email) AS "Total" FROM Employee;								-- 4

-- The COUNT() function can contain other functions 
-- such as Distinct, as shown below.
SELECT COUNT(Distinct(LastName)) AS "Total" FROM Employee;  				-- 5

-- Use the COUNT(*) to count the total records in the table. 
-- The following query count the total records of the Employee table.		
SELECT COUNT(*) AS "Total Records" FROM Employee;                			-- 6
```

  

The COUNT() is an aggregate function, so it can be used in [Group By](https://www.tutorialsteacher.com/sql/sql-groupby) queries. The following query counts the number of employees in each department.

```SQL
SELECT DeptId, COUNT(*) AS "Total Employees" 
FROM Employee
GROUP BY DeptId;
```

| DeptId | Total Employees |
| ------ | --------------- |
| 10     | 1               |
| 20     | 2               |
| 30     | 2               |
| 40     | 1               |



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





## References

* https://www.w3schools.com/sql/sql_count_avg_sum.asp

* https://www.tutorialsteacher.com/sql/count-function

* https://www.tutorialsteacher.com/sql/avg-function

* https://www.tutorialsteacher.com/sql/sum-function

* Aggregate functions: https://youtu.be/jcoJuc5e3RE

* https://dev.mysql.com/doc/refman/8.0/en/string-functions.html

* https://dev.mysql.com/doc/refman/8.0/en/numeric-functions.html

* https://www.w3schools.com/sql/sql_min_max.asp


User defined functions
https://youtu.be/cdr0TuKCvDU
