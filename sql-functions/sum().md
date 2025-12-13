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







## REFERENCES

* https://www.geeksforgeeks.org/sql/sql-functions/

* https://www.w3schools.com/sql/sql_count_avg_sum.asp

* https://www.tutorialsteacher.com/sql/count-function

* https://www.tutorialsteacher.com/sql/avg-function

* https://www.tutorialsteacher.com/sql/sum-function

  
