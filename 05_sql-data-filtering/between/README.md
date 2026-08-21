
# BETWEEN

The `BETWEEN` operator selects values within a given range. The values can be numbers, text, or dates. The range of values can be strings, numbers, or dates. The range of values must be specified with the AND operator.

The `BETWEEN` operator is inclusive: begin and end values are included. 

## Syntax

**BETTWEEN**

```
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN begin_value AND end_value;
```



**NOT BETWEEN**

To display the products outside the range of the selected values.

```
SELECT column_name(s)
FROM table_name
WHERE column_name NOT BETWEEN begin_value AND end_value;
```



## Example 1 - Products

- Reference: https://www.w3schools.com/sql/sql_between.asp

Below is a selection from the "Products" table in the Northwind sample database:

| ProductID | ProductName                  | SupplierID | CategoryID | Unit                | Price |
| :-------- | :--------------------------- | :--------- | :--------- | :------------------ | :---- |
| 1         | Chais                        | 1          | 1          | 10 boxes x 20 bags  | 18    |
| 2         | Chang                        | 1          | 1          | 24 - 12 oz bottles  | 19    |
| 3         | Aniseed Syrup                | 1          | 2          | 12 - 550 ml bottles | 10    |
| 4         | Chef Anton's Cajun Seasoning | 1          | 2          | 48 - 6 oz jars      | 22    |
| 5         | Chef Anton's Gumbo Mix       | 1          | 2          | 36 boxes            | 21.35 |

### BETWEEN

The following SQL statement selects all products with a price between 10 and 20:

```SQL
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20;
```

**Output**

Number of Records: 29

| ProductID | ProductName   | SupplierID | CategoryID | Unit                | Price |
| :-------- | :------------ | :--------- | :--------- | :------------------ | :---- |
| 1         | Chais         | 1          | 1          | 10 boxes x 20 bags  | 18    |
| 2         | Chang         | 1          | 1          | 24 - 12 oz bottles  | 19    |
| 3         | Aniseed Syrup | 1          | 2          | 12 - 550 ml bottles | 10    |
| 15        | Genen Shouyu  | 6          | 2          | 24 - 250 ml bottles | 15.5  |
| 16        | Pavlova       | 7          | 3          | 32 - 500 g boxes    | 17.45 |



### NOT BETWEEN

To display the products outside the range of the previous example, use `NOT BETWEEN`:

```SQL
SELECT * FROM Products
WHERE Price NOT BETWEEN 10 AND 20;
```

**Output**

Number of Records: 48

| ProductID | ProductName                     | SupplierID | CategoryID | Unit            | Price |
| :-------- | :------------------------------ | :--------- | :--------- | :-------------- | :---- |
| 4         | Chef Anton's Cajun Seasoning    | 2          | 2          | 48 - 6 oz jars  | 22    |
| 5         | Chef Anton's Gumbo Mix          | 2          | 2          | 36 boxes        | 21.35 |
| 6         | Grandma's Boysenberry Spread    | 3          | 2          | 12 - 8 oz jars  | 25    |
| 7         | Uncle Bob's Organic Dried Pears | 3          | 7          | 12 - 1 lb pkgs. | 30    |
| 8         | Northwoods Cranberry Sauce      | 3          | 2          | 12 - 12 oz jars | 40    |



### BETWEEN with IN Example

The following SQL statement selects all products with a price between 10 and 20. In addition; do not show products with a CategoryID of 1,2, or 3:

```sql
SELECT * FROM Products
WHERE Price BETWEEN 10 AND 20
AND CategoryID NOT IN (1,2,3);
```

**Output**

Number of Records: 9

| ProductID | ProductName                   | SupplierID | CategoryID | Unit            | Price |
| :-------- | :---------------------------- | :--------- | :--------- | :-------------- | :---- |
| 31        | Gorgonzola Telino             | 14         | 4          | 12 - 100 g pkgs | 12.5  |
| 36        | Inlagd Sill                   | 17         | 8          | 24 - 250 g jars | 19    |
| 40        | Boston Crab Meat              | 19         | 8          | 24 - 4 oz tins  | 18.4  |
| 42        | Singaporean Hokkien Fried Mee | 20         | 5          | 32 - 1 kg pkgs. | 14    |



### BETWEEN Text Values Example

The following SQL statement selects all products with a ProductName between Carnarvon Tigers and Mozzarella di Giovanni:

```SQL
SELECT * FROM Products
WHERE ProductName BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName;
```

- Reference: https://www.simplilearn.com/tutorials/sql-tutorial/sql-between

## Example 2 - Orders

Below is a selection from the "Orders" table in the Northwind sample database:

Number of records=196

| OrderID | CustomerID | EmployeeID | OrderDate | ShipperID |
| :------ | :--------- | :--------- | :-------- | :-------- |
| 10248   | 90         | 5          | 7/4/1996  | 3         |
| 10249   | 81         | 6          | 7/5/1996  | 1         |
| 10250   | 34         | 4          | 7/8/1996  | 2         |
| 10251   | 84         | 3          | 7/9/1996  | 1         |
| 10252   | 76         | 4          | 7/10/1996 | 2         |



### BETWEEN Dates

The following SQL statement selects all orders with an OrderDate between '01-July-1996' and '31-July-1996':

```SQL
SELECT * FROM Orders
WHERE OrderDate BETWEEN #07/01/1996# AND #07/31/1996#;

-- OR
SELECT * FROM Orders
WHERE OrderDate BETWEEN '1996-07-01' AND '1996-07-31';
```





**Output**

Number of Records: 22

| OrderID | CustomerID | EmployeeID | OrderDate | ShipperID |
| :------ | :--------- | :--------- | :-------- | :-------- |
| 10248   | 90         | 5          | 7/4/1996  | 3         |
| 10249   | 81         | 6          | 7/5/1996  | 1         |
| 10250   | 34         | 4          | 7/8/1996  | 2         |
| 10251   | 84         | 3          | 7/8/1996  | 1         |





## Example 3 - Employees

- Reference: https://www.tutorialsteacher.com/sql/sql-between-operator

For the demo purpose, we will use the following `Employee` tables in all examples.

| EmpId | FirstName | LastName  | Email                                           | Salary | HireDate   |
| ----- | --------- | --------- | ----------------------------------------------- | ------ | ---------- |
| 1     | 'John'    | 'King'    | '[john.king@abc.com](mailto:john.king@abc.com)' | 33000  | 2018-07-25 |
| 2     | 'James'   | 'Bond'    |                                                 |        | 2018-07-29 |
| 3     | 'Neena'   | 'Kochhar' | '[neena@test.com](mailto:neena@test.com)'       | 17000  | 2018-08-22 |
| 4     | 'Lex'     | 'De Haan' | '[lex@test.com](mailto:lex@test.com)'           | 15000  | 2018-09-8  |
| 5     | 'Amit'    | 'Patel'   |                                                 | 18000  | 2019-01-25 |
| 6     | 'Abdul'   | 'Kalam'   | '[abdul@test.com](mailto:abdul@test.com)'       | 25000  | 2020-07-14 |



### BETWEEN

The `Salary` column is used with the BETWEEN operator to filter records. The `Salary BETWEEN 10000 AND 20000;` specifies that the values in the `Salary` column should be between 10000 and 20000 (inclusive of both values).  

```SQL
SELECT EmpId, FirstName, LastName, Salary
FROM Employee
WHERE Salary BETWEEN 10000 AND 20000;
```

**Output**

| EmpId | FirstName | LastName  | Salary |
| ----- | --------- | --------- | ------ |
| 3     | 'Neena'   | 'Kochhar' | 17000  |
| 4     | 'Lex'     | 'De Haan' | 15000  |
| 5     | 'Amit'    | 'Patel'   | 18000  |

### BETWEEN Date Range

The following query uses the BETWEEN operator to specify the date range.

```sql
SELECT EmpId, FirstName, LastName, HireDate
FROM Employee
WHERE HireDate BETWEEN '2018-07-01' and '2018-8-31';
```

**Output**

| EmpId | FirstName | LastName  | HireDate   |
| ----- | --------- | --------- | ---------- |
| 1     | 'John'    | 'King'    | 2018-07-25 |
| 2     | 'James'   | 'Bond'    | 2018-07-29 |
| 3     | 'Neena'   | 'Kochhar' | 2018-08-22 |



### BETWEEN String Range

The following query uses the string range with the BETWEEN operator.

```SQL
SELECT * FROM Employee
WHERE FirstName BETWEEN 'a%' AND 'j%';
```

Above, string range `FirstName BETWEEN 'a%' AND 'j%'` fetches records where the `FirstName` value should start from either 'a%' or any character before 'j%' (but not 'j'). It will display the following result.

**Output**

| EmpId | FirstName | LastName | Email                                     | Salary | HireDate   |
| ----- | --------- | -------- | ----------------------------------------- | ------ | ---------- |
| 5     | 'Amit'    | 'Patel'  |                                           | 18000  | 2019-01-25 |
| 6     | 'Abdul'   | 'Kalam'  | '[abdul@test.com](mailto:abdul@test.com)' | 25000  | 2020-07-14 |



## References

- https://www.w3schools.com/sql/sql_between.asp
- https://www.tutorialsteacher.com/sql/sql-between-operator
- https://www.simplilearn.com/tutorials/sql-tutorial/sql-between

