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



## REFERENCES

* https://www.geeksforgeeks.org/sql/sql-functions/

* https://www.tutorialsteacher.com/sql/count-function

  
