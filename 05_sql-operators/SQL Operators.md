# SQL Operators

## Syntax

In order to filter certain results from being returned, we need to use a `WHERE` clause in the query. The clause is applied to each row of data by checking specific column values to determine whether it should be included in the results or not.

```
SELECT column1 <OPERATOR> column2
FROM table_name
WHERE condition;

------

SELECT column1, column2, …
FROM table_name
WHERE condition
    AND/OR another_condition
    AND/OR …;
```



More complex clauses can be constructed by joining numerous `AND` or `OR` logical keywords (ie. num_wheels >= 4 AND doors <= 2). And below are some useful operators that you can use for numerical data (ie. integer or floating point):

| Operator            | Condition                                            | SQL Example                           |
| ------------------- | ---------------------------------------------------- | ------------------------------------- |
| =, !=, < <=, >, >=  | Standard numerical operators                         | col_name **!=** 4                     |
| BETWEEN … AND …     | Number is within range of two values (inclusive)     | col_name **BETWEEN** 1.5 **AND** 10.5 |
| NOT BETWEEN … AND … | Number is not within range of two values (inclusive) | col_name **NOT BETWEEN** 1 **AND** 10 |
| IN (…)              | Number exists in a list                              | col_name **IN** (2, 4, 6)             |
| NOT IN (…)          | Number does not exist in a list                      | col_name **NOT IN** (1, 3, 5)         |



When writing `WHERE` clauses with columns containing text data, SQL supports a number of useful operators to do things like case-insensitive string comparison and wildcard pattern matching. We show a few common text-data specific operators below

| Operator   | Condition                                                    | Example                                                      |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| =          | Case sensitive exact string comparison (*notice the single equals*) | col_name **=** "abc"                                         |
| != or <>   | Case sensitive exact string inequality comparison            | col_name **!=** "abcd"                                       |
| LIKE       | Case insensitive exact string comparison                     | col_name **LIKE** "ABC"                                      |
| NOT LIKE   | Case insensitive exact string inequality comparison          | col_name **NOT LIKE** "ABCD"                                 |
| %          | Used anywhere in a string to match a sequence of zero or more characters (only with LIKE or NOT LIKE) | col_name **LIKE** "%AT%" (matches "AT", "ATTIC", "CAT" or even "BATS") |
| _          | Used anywhere in a string to match a single character (only with LIKE or NOT LIKE) | col_name **LIKE** "AN_" (matches "AND", but not "AN")        |
| IN (…)     | String exists in a list                                      | col_name **IN** ("A", "B", "C")                              |
| NOT IN (…) | String does not exist in a list                              | col_name **NOT IN** ("D", "E", "F")                          |



## Operators clasification

The following operators can be used in the `WHERE` clause:

**Arithmetic Operators**

| Operator | Description |
| :------- | :---------- |
| +        | Add         |
| -        | Subtract    |
| *        | Multiply    |
| /        | Divide      |
| %        | Modulo      |



**Bitwise Operators**

| Operator | Description          |
| :------- | :------------------- |
| &        | Bitwise AND          |
| \|       | Bitwise OR           |
| ^        | Bitwise exclusive OR |



**Comparison Operators**

| Operator | Description                                                  |
| :------- | :----------------------------------------------------------- |
| =        | Equal                                                        |
| >        | Greater than                                                 |
| <        | Less than                                                    |
| >=       | Greater than or equal                                        |
| <=       | Less than or equal                                           |
| <>       | Not equal. **Note:** In some versions of SQL this operator may be written as != |



**Compound Operators**

| Operator | Description              |
| :------- | :----------------------- |
| +=       | Add equals               |
| -=       | Subtract equals          |
| *=       | Multiply equals          |
| /=       | Divide equals            |
| %=       | Modulo equals            |
| &=       | Bitwise AND equals       |
| ^-=      | Bitwise exclusive equals |
| \|*=     | Bitwise OR equals        |



**Logical Operators**

| Operator | Description                                                  |
| :------- | :----------------------------------------------------------- |
| ALL      | TRUE if all of the subquery values meet the condition        |
| AND      | TRUE if all the conditions separated by AND is TRUE          |
| ANY      | TRUE if any of the subquery values meet the condition        |
| BETWEEN  | Between a certain range. TRUE if the operand is within the range of comparisons |
| EXISTS   | TRUE if the subquery returns one or more records             |
| IN       | To specify multiple possible values for a column. RUE if the operand is equal to one of a list of expressions |
| LIKE     | Search for a pattern. TRUE if the operand matches a pattern  |
| NOT      | Displays a record if the condition(s) is NOT TRUE            |
| OR       | TRUE if any of the conditions separated by OR is TRUE        |
| SOME     | TRUE if any of the subquery values meet the condition        |





## Examples

### Countries, population and gdp

**Database**

| name        | continent | area    | population | gdp          |
| :---------- | :-------- | :------ | :--------- | :----------- |
| Afghanistan | Asia      | 652230  | 25500100   | 20343000000  |
| Albania     | Europe    | 28748   | 2831741    | 12960000000  |
| Algeria     | Africa    | 2381741 | 37100000   | 188681000000 |
| Andorra     | Europe    | 468     | 78115      | 3712000000   |
| Angola      | Africa    | 1246700 | 20609294   | 100990000000 |



**Large Countries**

How to use WHERE to filter records. Show the name for the countries that have a population of at least 200 million. 200 million is 200000000, there are eight zeros.

```SQL
SELECT name FROM world
WHERE population >=200000000;
```

Output

| name          |
| ------------- |
| Brazil        |
| China         |
| India         |
| Indonesia     |
| United States |



**Per capita GDP**

Give the `name` and the **per capita GDP** for those countries with a `population` of at least 200 million.

```SQL
SELECT name, gdp/population AS 'per capita GDP' FROM world
WHERE population >=200000000;
```

Output

| name          | per capita GDP     |
| ------------- | ------------------ |
| Brazil        | 11115.264751422625 |
| China         | 6121.710598592322  |
| India         | 1504.793124478397  |
| Indonesia     | 3482.020488188676  |
| United States | 51032.29454636844  |



**South America In millions**

```SQL
SELECT name, population/1000000 FROM world
WHERE continent='South America';
```

Output

| name                             |           |
| -------------------------------- | --------- |
| Argentina                        | 42.6695   |
| Bolivia                          | 10.027254 |
| Brazil                           | 202.794   |
| Chile                            | 17.773    |
| Colombia                         | 47.662    |
| Ecuador                          | 15.7742   |
| Guyana                           | 0.784894  |
| Paraguay                         | 6.783374  |
| Peru                             | 30.475144 |
| Saint Vincent and the Grenadines | 0.109     |
| Suriname                         | 0.534189  |
| Uruguay                          | 3.286314  |
| Venezuela                        | 28.946101 |



**France, Germany, Italy**

Show the `name` and `population` for France, Germany, Italy

```SQL
SELECT name, population FROM world
WHERE name='France' OR name='Germany'OR name='Italy';
```

Output

| name    | population |
| ------- | ---------- |
| France  | 65906000   |
| Germany | 80716000   |
| Italy   | 60782668   |



## References

- https://sqlbolt.com/lesson/select_queries_with_constraints

- https://sqlbolt.com/lesson/select_queries_with_constraints_pt_2

- https://www.w3schools.com/sql/sql_operators.asp

  



# AND, OR and NOT

The `WHERE` clause can be combined with `AND`, `OR`, and `NOT` operators.

The `AND` and `OR` operators are used to filter records based on more than one condition:

- The `AND` operator displays a record if all the conditions separated by `AND` are TRUE.
- The `OR` operator displays a record if any of the conditions separated by `OR` is TRUE.

The `NOT` operator displays a record if the condition(s) is NOT TRUE.



## **Syntax**

**AND**

```
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```



**OR**

```
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```



**NOT**

```SQL
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
```



## Examples  

### Customers

The table below shows the complete "Customers" table from the Northwind sample database:

- Complete DEMO database: https://www.w3schools.com/sql/sql_and_or.asp

| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| :--------- | :--------------------------------- | :----------------- | :---------------------------- | :---------- | :--------- | :------ |
| 1          | Alfreds Futterkiste                | Maria Anders       | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |
| 6          | Blauer See Delikatessen            | Hanna Moos         | Forsterstr. 57                | Mannheim    | 68306      | Germany |
| 7          | Blondel père et fils               | Frédérique Citeaux | 24, place Kléber              | Strasbourg  | 67000      | France  |
| 8          | Bólido Comidas preparadas          | Martín Sommer      | C/ Araquil, 67                | Madrid      | 28023      | Spain   |
| 9          | Bon app'                           | Laurence Lebihans  | 12, rue des Bouchers          | Marseille   | 13008      | France  |
| 10         | Bottom-Dollar Marketse             | Elizabeth Lincoln  | 23 Tsawassen Blvd.            | Tsawassen   | T2F 8M4    | Canada  |
| 11         | B's Beverages                      | Victoria Ashworth  | Fauntleroy Circus             | London      | EC2 5NT    | UK      |



##### **AND**

The following SQL statement selects all fields from "Customers" where country is "Germany" AND city is "Berlin":

```SQL
SELECT * FROM Customers
WHERE Country='Germany' AND City='Berlin';
```



Output

Number of Records: 1

| CustomerID | CustomerName        | ContactName  | Address       | City   | PostalCode | Country |
| :--------- | :------------------ | :----------- | :------------ | :----- | :--------- | :------ |
| 1          | Alfreds Futterkiste | Maria Anders | Obere Str. 57 | Berlin | 12209      | Germany |



##### OR

The following SQL statement selects all fields from "Customers" where country is "Germany" AND city is "Berlin":

```SQL
SELECT * FROM Customers
WHERE Country='Germany' AND City='Berlin';
```

Output

Number of Records: 2

| CustomerID | CustomerName        | ContactName   | Address           | City    | PostalCode | Country |
| :--------- | :------------------ | :------------ | :---------------- | :------ | :--------- | :------ |
| 1          | Alfreds Futterkiste | Maria Anders  | Obere Str. 57     | Berlin  | 12209      | Germany |
| 25         | Frankenversand      | Peter Franken | Berliner Platz 43 | München | 80805      | Germany |





The following SQL statement selects all fields from "Customers" where country is "Germany" OR "Spain":

```SQL
SELECT * FROM Customers
WHERE Country='Germany' OR Country='Spain';
```

Output

Number of Records: 16

| CustomerID | CustomerName              | ContactName   | Address        | City     | PostalCode | Country |
| :--------- | :------------------------ | :------------ | :------------- | :------- | :--------- | :------ |
| 1          | Alfreds Futterkiste       | Maria Anders  | Obere Str. 57  | Berlin   | 12209      | Germany |
| 6          | Blauer See Delikatessen   | Hanna Moos    | Forsterstr. 57 | Mannheim | 68306      | Germany |
| 8          | Bólido Comidas preparadas | Martín Sommer | C/ Araquil, 67 | Madrid   | 28023      | Spain   |
| 17         | Drachenblut Delikatessend | Sven Ottlieb  | Walserweg 21   | Aachen   | 52066      | Germany |



##### NOT

The following SQL statement selects all fields from "Customers" where country is NOT "Germany":

```SQL
SELECT * FROM Customers
WHERE NOT Country='Germany';
```

Output

Number of Records: 80

| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| :--------- | :--------------------------------- | :----------------- | :---------------------------- | :---------- | :--------- | :------ |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |
| 7          | Blondel père et fils               | Frédérique Citeaux | 24, place Kléber              | Strasbourg  | 67000      | France  |



##### Combining AND, OR and NOT

You can also combine the `AND`, `OR` and `NOT` operators.

1. The following SQL statement selects all fields from "Customers" where country is "Germany" AND city must be "Berlin" OR "München" (use parenthesis to form complex expressions):

```SQL
SELECT * FROM Customers
WHERE Country='Germany' AND (City='Berlin' OR City='München');
```

Output

Number of Records: 2

| CustomerID | CustomerName        | ContactName   | Address           | City    | PostalCode | Country |
| :--------- | :------------------ | :------------ | :---------------- | :------ | :--------- | :------ |
| 1          | Alfreds Futterkiste | Maria Anders  | Obere Str. 57     | Berlin  | 12209      | Germany |
| 25         | Frankenversand      | Peter Franken | Berliner Platz 43 | München | 80805      | Germany |



1. The following SQL statement selects all fields from "Customers" where country is NOT "Germany" and NOT "USA":

```SQL
SELECT * FROM Customers
WHERE NOT Country='Germany' AND NOT Country='USA';
```

Output

Number of Records: 67

| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| :--------- | :--------------------------------- | :----------------- | :---------------------------- | :---------- | :--------- | :------ |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |
| 7          | Blondel père et fils               | Frédérique Citeaux | 24, place Kléber              | Strasbourg  | 67000      | France  |
| 8          | Bólido Comidas preparadas          | Martín Sommer      | C/ Araquil, 67                | Madrid      | 28023      | Spain   |



## Reference

- https://www.w3schools.com/sql/sql_and_or.asp

  

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



# IN

The `IN` operator allows you to specify multiple values in a `WHERE` clause.

The `IN` operator is a shorthand for multiple `OR` conditions.

## Syntax

**IN**

```
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);
```

**NOT IN**

```
SELECT column_name(s)
FROM table_name
WHERE column_name NOT IN (value1, value2, ...);
```



**IN (FOR SUBQUERY)**

```
SELECT column_name(s)
FROM table_name
WHERE column_name IN (SELECT STATEMENT / QUERY);
```





## Example 1 - Customers

The table below shows the complete "Customers" table from the Northwind sample database:

- Number of Records: 91

| CustomerID | CustomerName                         | ContactName        | Address                       | City         | PostalCode | Country     |
| :--------- | :----------------------------------- | :----------------- | :---------------------------- | :----------- | :--------- | :---------- |
| 1          | Alfreds Futterkiste                  | Maria Anders       | Obere Str. 57                 | Berlin       | 12209      | Germany     |
| 2          | Ana Trujillo Emparedados y helados   | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F.  | 05021      | Mexico      |
| 3          | Antonio Moreno Taquería              | Antonio Moreno     | Mataderos 2312                | México D.F.  | 05023      | Mexico      |
| 4          | Around the Horn                      | Thomas Hardy       | 120 Hanover Sq.               | London       | WA1 1DP    | UK          |
| 5          | Berglunds snabbköp                   | Christina Berglund | Berguvsvägen 8                | Luleå        | S-958 22   | Sweden      |
| 6          | Blauer See Delikatessen              | Hanna Moos         | Forsterstr. 57                | Mannheim     | 68306      | Germany     |
| 7          | Blondel père et fils                 | Frédérique Citeaux | 24, place Kléber              | Strasbourg   | 67000      | France      |
| 8          | Bólido Comidas preparadas            | Martín Sommer      | C/ Araquil, 67                | Madrid       | 28023      | Spain       |
| 9          | Bon app'                             | Laurence Lebihans  | 12, rue des Bouchers          | Marseille    | 13008      | France      |
| 10         | Bottom-Dollar Marketse               | Elizabeth Lincoln  | 23 Tsawassen Blvd.            | Tsawassen    | T2F 8M4    | Canada      |
| 11         | B's Beverages                        | Victoria Ashworth  | Fauntleroy Circus             | London       | EC2 5NT    | UK          |
| 12         | Cactus Comidas para llevar           | Patricio Simpson   | Cerrito 333                   | Buenos Aires | 1010       | Argentina   |
| 13         | Centro comercial Moctezuma           | Francisco Chang    | Sierras de Granada 9993       | México D.F.  | 05022      | Mexico      |
| 14         | Chop-suey Chinese                    | Yang Wang          | Hauptstr. 29                  | Bern         | 3012       | Switzerland |
| 15         | Comércio Mineiro                     | Pedro Afonso       | Av. dos Lusíadas, 23          | São Paulo    | 05432-043  | Brazil      |
| 16         | Consolidated Holdings                | Elizabeth Brown    | Berkeley Gardens 12 Brewery   | London       | WX1 6LT    | UK          |
| 17         | Drachenblut Delikatessend            | Sven Ottlieb       | Walserweg 21                  | Aachen       | 52066      | Germany     |
| 18         | Du monde entier                      | Janine Labrune     | 67, rue des Cinquante Otages  | Nantes       | 44000      | France      |
| 19         | Eastern Connection                   | Ann Devon          | 35 King George                | London       | WX3 6FW    | UK          |
| 20         | Ernst Handel                         | Roland Mendel      | Kirchgasse 6                  | Graz         | 8010       | Austria     |
| 21         | Familia Arquibaldo                   | Aria Cruz          | Rua Orós, 92                  | São Paulo    | 05442-030  | Brazil      |
| 22         | FISSA Fabrica Inter. Salchichas S.A. | Diego Roel         | C/ Moralzarzal, 86            | Madrid       | 28034      | Spain       |
| 23         | Folies gourmandes                    | Martine Rancé      | 184, chaussée de Tournai      | Lille        | 59000      | France      |
| 24         | Folk och fä HB                       | Maria Larsson      | Åkergatan 24                  | Bräcke       | S-844 67   | Sweden      |
| 25         | Frankenversand                       | Peter Franken      | Berliner Platz 43             | München      | 80805      | Germany     |
| 26         | France restauration                  | Carine Schmitt     | 54, rue Royale                | Nantes       | 44000      | France      |
| 27         | Franchi S.p.A.                       | Paolo Accorti      | Via Monte Bianco 34           | Torino       | 10100      | Italy       |
| 28         | Furia Bacalhau e Frutos do Mar       | Lino Rodriguez     | Jardim das rosas n. 32        | Lisboa       | 1675       | Portugal    |
| 29         | Galería del gastrónomo               | Eduardo Saavedra   | Rambla de Cataluña, 23        | Barcelona    | 08022      | Spain       |
| 30         | Godos Cocina Típica                  | José Pedro Freyre  | C/ Romero, 33                 | Sevilla      | 41101      | Spain       |



### Patterns

| SQL query pattern                                            | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| SELECT * FROM Customers WHERE Country IN ('Germany', 'France', 'UK'); | selects all customers that are located in "Germany", "France" or "UK" |
| SELECT * FROM Customers WHERE Country NOT IN ('Germany', 'France', 'UK'); | selects all customers that are NOT located in "Germany", "France" or "UK" |
| SELECT * FROM Customers WHERE Country IN (SELECT Country FROM Suppliers); | selects all customers that are from the same countries as the suppliers |
|                                                              |                                                              |



### **Subquery**

The following SQL statement selects all customers that are from the same countries as the suppliers:

```
SELECT * FROM Customers
WHERE Country IN (SELECT Country FROM Suppliers);
```

**Output**

Number of Records: 69

| CustomerID | CustomerName              | ContactName        | Address              | City       | PostalCode | Country |
| :--------- | :------------------------ | :----------------- | :------------------- | :--------- | :--------- | :------ |
| 1          | Alfreds Futterkiste       | Maria Anders       | Obere Str. 57        | Berlin     | 12209      | Germany |
| 4          | Around the Horn           | Thomas Hardy       | 120 Hanover Sq.      | London     | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp        | Christina Berglund | Berguvsvägen 8       | Luleå      | S-958 22   | Sweden  |
| 6          | Blauer See Delikatessen   | Hanna Moos         | Forsterstr. 57       | Mannheim   | 68306      | Germany |
| 7          | Blondel père et fils      | Frédérique Citeaux | 24, place Kléber     | Strasbourg | 67000      | France  |
| 8          | Bólido Comidas preparadas | Martín Sommer      | C/ Araquil, 67       | Madrid     | 28023      | Spain   |
| 9          | Bon app'                  | Laurence Lebihans  | 12, rue des Bouchers | Marseille  | 13008      | France  |



## Example 2 - Employee & Department 

**Employee table**

| EmpId | FirstName | LastName  | Email                                           | Salary | DeptId |
| ----- | --------- | --------- | ----------------------------------------------- | ------ | ------ |
| 1     | 'John'    | 'King'    | '[john.king@abc.com](mailto:john.king@abc.com)' | 33000  | 1      |
| 2     | 'James'   | 'Bond'    |                                                 |        | 1      |
| 3     | 'Neena'   | 'Kochhar' | '[neena@test.com](mailto:neena@test.com)'       | 17000  | 2      |
| 4     | 'Lex'     | 'De Haan' | '[lex@test.com](mailto:lex@test.com)'           | 15000  | 1      |
| 5     | 'Amit'    | 'Patel'   |                                                 | 18000  | 3      |
| 6     | 'Abdul'   | 'Kalam'   | '[abdul@test.com](mailto:abdul@test.com)'       | 25000  | 4      |

**Department Table**

| DeptId | Name      |
| ------ | --------- |
| 1      | 'Finance' |
| 2      | 'HR'      |
| 3      | 'Sales'   |
| 4      | 'Admin'   |



### Patterns

| SQL query pattern                                            | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| SELECT EmpId, FirstName, LastName, Salary<br/>FROM Employee<br/>WHERE EmpId IN (1, 3, 5, 6) | selects records with EmpId 1, 3, 5 or 6                      |
| SELECT EmpId, FirstName, LastName, Salary<br/>FROM Employee<br/>WHERE FirstName IN ('james','john','abdul'); | selects records where the FirstName is 'james', 'john', or 'abdul' |
| SELECT EmpId, FirstName, LastName, DeptId<br/>FROM Employee<br/>WHERE DeptId IN (SELECT DeptId from Department WHERE DeptId > 2); | Seects records where                                         |
| SELECT EmpId, FirstName, LastName, Salary<br/>FROM Employee<br/>WHERE EmpId NOT IN (1, 3, 5); | Filter records that do not fall in the specified values.     |



### **IN - Number values**

Return records where `EmpId` is 1 or 3 or 5 or 6.

```SQL
SELECT EmpId, FirstName, LastName, Salary
FROM Employee
WHERE EmpId IN (1, 3, 5, 6)
```

**Output**

| EmpId | FirstName | LastName  | Salary |
| ----- | --------- | --------- | ------ |
| 1     | 'John'    | 'King'    | 33000  |
| 3     | 'Neena'   | 'Kochhar' | 17000  |
| 5     | 'Amit'    | 'Patel'   | 18000  |
| 6     | 'Abdul'   | 'Kalam'   | 25000  |



### **IN - String values**

```SQL
SELECT EmpId, FirstName, LastName, Salary
FROM Employee
WHERE FirstName IN ('james','john','abdul');
```

**Output**

| EmpId | FirstName | LastName | Salary |
| ----- | --------- | -------- | ------ |
| 1     | 'John'    | 'King'   | 33000  |
| 2     | 'James'   | 'Bond'   |        |
| 6     | 'Abdul'   | 'Kalam'  | 25000  |

Note that wildcard characters '%', '_', etc. cannot be used with the string values.



### Sub-query with IN Operator

```SQL
SELECT EmpId, FirstName, LastName, DeptId
FROM Employee
WHERE DeptId IN (SELECT DeptId from Department WHERE DeptId > 2);
```

In the above query, the sub-query `SELECT DeptId from Department WHERE DeptId > 2` returns two `DeptId`, 3 and 4. So, now the query would be like `SELECT EmpId, FirstName, LastName, Salary FROM Employee WHERE DeptId in (3, 4);`. The following is the result.

**Output**

| EmpId | FirstName | LastName | DeptId |
| ----- | --------- | -------- | ------ |
| 5     | 'Amit'    | 'Patel'  | 3      |
| 6     | 'Abdul'   | 'Kalam'  | 4      |



### NOT IN

Use the NOT operator with the IN operator to filter records that do not fall in the specified values.

```SQL
SELECT EmpId, FirstName, LastName, Salary
FROM Employee
WHERE EmpId NOT IN (1, 3, 5);
```

**Output**

| EmpId | FirstName | LastName  | Salary |
| ----- | --------- | --------- | ------ |
| 2     | 'James'   | 'Bond'    |        |
| 4     | 'Lex'     | 'De Haan' | 15000  |
| 6     | 'Abdul'   | 'Kalam'   | 25000  |

## References

- https://www.w3schools.com/sql/sql_in.asp
- https://www.tutorialsteacher.com/sql/sql-in-operator
- 

# LIKE

The `LIKE` operator is used in a `WHERE` clause to search for a specified pattern in a column. It can be used with numbers, string, or date values. However, it is recommended to use the string values.

The LIKE operator in MS SQL Server, SQLite, MySQL database are not case-sensitive, whereas it is case-sensitive in Oracle, and PostgreSQL database.

There are two wildcards often used in conjunction with the `LIKE` operator:

- The percent sign (%) represents zero, one, or multiple characters
- The underscore sign (*) represents one, single character*
- ***Note:** MS Access uses an asterisk (\*) instead of the percent sign (%), and a question mark (?) instead of the underscore (*).

## Syntax

```SQL
SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern;
```

**Tip:** You can also combine any number of conditions using `AND` or `OR` operators.



## Wildcard characters 

The LIKE operator uses the following wildcard characters to specify a pattern:

| Pattern | Description                                                  |
| ------- | ------------------------------------------------------------ |
| %       | The **%** matches zero, one, or multiple characters (capital or small) or numbers. E.g. 'A%' will matche all string starting with 'A' and followed by any number of characters or numbers. |
| _       | The underscore **_** sign matches any single character or number. E.g. 'A_' will match all strings with two chars where the first character must be 'A' and second character can be anything. |
| []      | The **[]** matches any single character within the specified range in the []. E.g. 'A[e,l,p]' will match 'Apple', 'Aelp', 'Alep', 'Aple', etc. |
| [^]     | The **[^]** matches any single character except the specified range in the [^]. E.g. 'A[^e,l,p]' will match anything that starts with 'A', but not 'Apple', 'Aelp', 'Alep', 'Aple', etc. |





## **Common patters**

Here are some examples showing different `LIKE` operators with '%' and '_' wildcards:

| LIKE Operator                    | Description                                                  |
| :------------------------------- | :----------------------------------------------------------- |
| WHERE CustomerName LIKE 'a%'     | Finds any values that start with "a"                         |
| WHERE CustomerName LIKE '%a'     | Finds any values that end with "a"                           |
| WHERE CustomerName LIKE '%or%'   | Finds any values that have "or" in any position              |
| WHERE CustomerName LIKE '_r%'    | Finds any values that have "r" in the second position        |
| WHERE CustomerName LIKE 'a_%'    | Finds any values that start with "a" and are at least 2 characters in length |
| WHERE CustomerName LIKE 'a__%'   | Finds any values that start with "a" and are at least 3 characters in length |
| WHERE ContactName LIKE 'a%o'     | Finds any values that start with "a" and ends with "o"       |
| WHERE CustomerName NOT LIKE 'a%' | Finds any values that does NOT start with "a"                |





## Example 1- Customers

he table below shows the complete "Customers" table from the Northwind sample database:

| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| :--------- | :--------------------------------- | :----------------- | :---------------------------- | :---------- | :--------- | :------ |
| 1          | Alfreds Futterkiste                | Maria Anders       | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |
| 6          | Blauer See Delikatessen            | Hanna Moos         | Forsterstr. 57                | Mannheim    | 68306      | Germany |
| 7          | Blondel père et fils               | Frédérique Citeaux | 24, place Kléber              | Strasbourg  | 67000      | France  |
| 8          | Bólido Comidas preparadas          | Martín Sommer      | C/ Araquil, 67                | Madrid      | 28023      | Spain   |
| 9          | Bon app'                           | Laurence Lebihans  | 12, rue des Bouchers          | Marseille   | 13008      | France  |
| 10         | Bottom-Dollar Marketse             | Elizabeth Lincoln  | 23 Tsawassen Blvd.            | Tsawassen   | T2F 8M4    | Canada  |



#### **Starting with "a"**

The following SQL statement selects all customers with a CustomerName starting with "a":

```
SELECT * FROM Customers
WHERE CustomerName LIKE 'a%';
```

Output

umber of Records: 4

| CustomerID | CustomerName                       | ContactName    | Address                       | City        | PostalCode | Country |
| :--------- | :--------------------------------- | :------------- | :---------------------------- | :---------- | :--------- | :------ |
| 1          | Alfreds Futterkiste                | Maria Anders   | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo   | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy   | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |



#### **Ending with "a"**

The following SQL statement selects all customers with a CustomerName starting with "a":

```
SELECT * FROM Customers
WHERE CustomerName LIKE '%a';
```

Output

Number of Records: 7

| CustomerID | CustomerName               | ContactName       | Address                   | City           | PostalCode | Country |
| :--------- | :------------------------- | :---------------- | :------------------------ | :------------- | :--------- | :------ |
| 3          | Antonio Moreno Taquería    | Antonio Moreno    | Mataderos 2312            | México D.F.    | 05023      | Mexico  |
| 13         | Centro comercial Moctezuma | Francisco Chang   | Sierras de Granada 9993   | México D.F.    | 05022      | Mexico  |
| 30         | Godos Cocina Típica        | José Pedro Freyre | C/ Romero, 33             | Sevilla        | 41101      | Spain   |
| 61         | Que Delícia                | Bernardo Batista  | Rua da Panificadora, 12   | Rio de Janeiro | 02389-673  | Brazil  |
| 62         | Queen Cozinha              | Lúcia Carvalho    | Alameda dos Canàrios, 891 | São Paulo      | 05487-020  | Brazil  |
| 88         | Wellington Importadora     | Paula Parente     | Rua do Mercado, 12        | Resende        | 08737-363  | Brazil  |
| 90         | Wilman Kala                | Matti Karttunen   | Keskuskatu 45             | Helsinki       | 21240      | Finland |



#### "or" in any position

The following SQL statement selects all customers with a CustomerName that have "or" in any position:

```SQL
SELECT * FROM Customers
WHERE CustomerName LIKE '%or%';
```

Output

Number of Records: 11

| CustomerID | CustomerName               | ContactName    | Address                        | City        | PostalCode | Country |
| :--------- | :------------------------- | :------------- | :----------------------------- | :---------- | :--------- | :------ |
| 3          | Antonio Moreno Taquería    | Antonio Moreno | Mataderos 2312                 | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn            | Thomas Hardy   | 120 Hanover Sq.                | London      | WA1 1DP    | UK      |
| 36         | Hungry Coyote Import Store | Yoshi Latimer  | City Center Plaza 516 Main St. | Elgin       | 97827      | USA     |
| 40         | La corne d'abondance       | Daniel Tonini  | 67, avenue de l'Europe         | Versailles  | 78000      | France  |



#### "r" in the second position

The following SQL statement selects all customers with a CustomerName that have "r" in the second position:

```SQL
SELECT * FROM Customers
WHERE CustomerName LIKE '_r%';
```





## Example 2 - Employee

| EmpId | FirstName | LastName  | Email                                           | Salary | HireDate   |
| ----- | --------- | --------- | ----------------------------------------------- | ------ | ---------- |
| 1     | 'John'    | 'King'    | '[john.king@abc.com](mailto:john.king@abc.com)' | 33000  | 2018-07-25 |
| 2     | 'James'   | 'Bond'    |                                                 |        | 2018-07-29 |
| 3     | 'Neena'   | 'Kochhar' | '[neena@test.com](mailto:neena@test.com)'       | 17000  | 2018-08-22 |
| 4     | 'Lex'     | 'De Haan' | '[lex@test.com](mailto:lex@test.com)'           | 15000  | 2018-09-8  |
| 5     | 'Amit'    | 'Patel'   |                                                 | 18000  | 2019-01-25 |
| 6     | 'Abdul'   | 'Kalam'   | '[abdul@test.com](mailto:abdul@test.com)'       | 25000  | 2020-07-14 |



#### **Three characters word - Second position**

The bellow query will return records whose `FirstName` value contains three letters and 'e' at the second position. The '_' indicates any one character.

```SQL
SELECT *
FROM Employee
WHERE FirstName LIKE '_e_';
```

**Output**

| EmpId | FirstName | LastName  | Email                                 | Salary | HireDate  |
| ----- | --------- | --------- | ------------------------------------- | ------ | --------- |
| 4     | 'Lex'     | 'De Haan' | '[lex@test.com](mailto:lex@test.com)' | 15000  | 2018-09-8 |



#### [] pattern

The bellow query uses the [] wildcard pattern.

```SQL
SELECT *
FROM Employee
WHERE FirstName LIKE 'A[i,m,t,y,s]';
```

**Output**

| EmpId | FirstName | LastName | Email | Salary | HireDate   |
| ----- | --------- | -------- | ----- | ------ | ---------- |
| 5     | 'Amit'    | 'Patel'  |       | 18000  | 2019-01-25 |

Note: The **[]** matches any single character within the specified range in the [].

- E.g. 'A[e,l,p]' will match 'Apple', 'Aelp', 'Alep', 'Aple', etc.



## Example 3 - Movies

| Id   | Title           | Director       | Year | Length_minutes |
| ---- | --------------- | -------------- | ---- | -------------- |
| 1    | Toy Story       | John Lasseter  | 1995 | 81             |
| 2    | A Bug's Life    | John Lasseter  | 1998 | 95             |
| 3    | Toy Story 2     | John Lasseter  | 1999 | 93             |
| 4    | Monsters, Inc.  | Pete Docter    | 2001 | 92             |
| 5    | Finding Nemo    | Andrew Stanton | 2003 | 107            |
| 6    | The Incredibles | Brad Bird      | 2004 | 116            |
| 7    | Cars            | John Lasseter  | 2006 | 117            |
| 8    | Ratatouille     | Brad Bird      | 2007 | 115            |
| 9    | WALL-E          | Andrew Stanton | 2008 | 104            |
| 10   | Up              | Pete Docter    | 2009 | 101            |
| 11   | Toy Story 3     | Lee Unkrich    | 2010 | 103            |
| 12   | Cars 2          | John Lasseter  | 2011 | 120            |



### Find all the Toy Story movies

```SQL
SELECT * FROM movies
WHERE Title LIKE '%Toy Story%';
```

| Id   | Title       | Director      | Year | Length_minutes |
| ---- | ----------- | ------------- | ---- | -------------- |
| 1    | Toy Story   | John Lasseter | 1995 | 81             |
| 3    | Toy Story 2 | John Lasseter | 1999 | 93             |
| 11   | Toy Story 3 | Lee Unkrich   | 2010 | 103            |



### Find all the movies directed by John Lasseter

```SQL
SELECT * FROM movies
WHERE Director = 'John Lasseter';
```

| Id   | Title        | Director      | Year | Length_minutes |
| ---- | ------------ | ------------- | ---- | -------------- |
| 1    | Toy Story    | John Lasseter | 1995 | 81             |
| 2    | A Bug's Life | John Lasseter | 1998 | 95             |
| 3    | Toy Story 2  | John Lasseter | 1999 | 93             |
| 7    | Cars         | John Lasseter | 2006 | 117            |
| 12   | Cars 2       | John Lasseter | 2011 | 120            |





### Find all the movies (and director) not directed by John Lasseter

```SQL
SELECT * FROM movies
WHERE Director != 'John Lasseter';
```

| Id   | Title               | Director       | Year | Length_minutes |
| ---- | ------------------- | -------------- | ---- | -------------- |
| 4    | Monsters, Inc.      | Pete Docter    | 2001 | 92             |
| 5    | Finding Nemo        | Andrew Stanton | 2003 | 107            |
| 6    | The Incredibles     | Brad Bird      | 2004 | 116            |
| 8    | Ratatouille         | Brad Bird      | 2007 | 115            |
| 9    | WALL-E              | Andrew Stanton | 2008 | 104            |
| 10   | Up                  | Pete Docter    | 2009 | 101            |
| 11   | Toy Story 3         | Lee Unkrich    | 2010 | 103            |
| 13   | Brave               | Brenda Chapman | 2012 | 102            |
| 14   | Monsters University | Dan Scanlon    | 2013 | 110            |
| 87   | WALL-G              | Brenda Chapman | 2042 | 97             |



### Find all the WALL-* movies

```SQL
SELECT * FROM Movies
WHERE Title LIKE 'WALL-%';
```



| Id   | Title  | Director       | Year | Length_minutes |
| ---- | ------ | -------------- | ---- | -------------- |
| 9    | WALL-E | Andrew Stanton | 2008 | 104            |
| 87   | WALL-G | Brenda Chapman | 2042 | 97             |



## Reference

- https://www.w3schools.com/sql/sql_like.asp
- https://www.tutorialsteacher.com/sql/sql-like-operator
- https://sqlbolt.com/lesson/select_queries_with_constraints_pt_2



# IS NULL & IS NOT NULL

You may not insert data to all the columns of a table in the database. If a column defined as NULL column, that means the value of that column can be empty. You are free to insert or update data anytime you want.

To fetch the NULL values from a table, we can use keywords, NULL or NOT NULL. You can not select NULL data of a table by using any comparison operators (e.g. =, !=, >, < ). The special clause IS NULL or IS NOT NULL is needed to check it.

IS only works against NULL. So it's like an equals operator but just specially for NULL. Database column values can be null. 

The `IS NOT NULL` operator is used to test for non-empty values (NOT NULL values).

The following SQL lists all customers with a value in the "Address" field:

```
SELECT CustomerName, ContactName, Address
FROM Customers
WHERE Address IS NOT NULL;
```



## NULL functions

- https://www.w3schools.com/sql/sql_isnull.asp
- https://www.tutorialsteacher.com/sql/sql-null-value



## Example - Employee table

| mpId | FirstName | LastName  | Email                                           | PhoneNo        | Salary |
| ---- | --------- | --------- | ----------------------------------------------- | -------------- | ------ |
| 1    | 'John'    | 'King'    | '[john.king@abc.com](mailto:john.king@abc.com)' | '650.127.1834' | 33000  |
| 2    | 'James'   | 'Bond'    |                                                 | '123.456.4568' |        |
| 3    | 'Neena'   | 'Kochhar' | '[neena@test.com](mailto:neena@test.com)'       |                | 17000  |
| 4    | 'Lex'     | 'De Haan' | '[lex@test.com](mailto:lex@test.com)'           | '123.456.4569' | 15000  |



The following example will select employees with `PhoneNo` as NULL.

```
SELECT * FROM Employee WHERE PhoneNo IS NULL;
```

| EmpId | FirstName | LastName  | Email                                     | PhoneNo | Salary |
| ----- | --------- | --------- | ----------------------------------------- | ------- | ------ |
| 3     | 'Neena'   | 'Kochhar' | '[neena@test.com](mailto:neena@test.com)' |         | 17000  |



The following query uses IS NOT NULL to return data whose `Email` value is not NULL.

```SQL
SELECT * FROM Employee WHERE Email IS NOT NULL;
```

| EmpId | FirstName | LastName  | Email                                           | PhoneNo        | Salary |
| ----- | --------- | --------- | ----------------------------------------------- | -------------- | ------ |
| 1     | 'John'    | 'King'    | '[john.king@abc.com](mailto:john.king@abc.com)' | '650.127.1834' | 33000  |
| 3     | 'Neena'   | 'Kochhar' | '[neena@test.com](mailto:neena@test.com)'       |                | 17000  |
| 4     | 'Lex'     | 'De Haan' | '[lex@test.com](mailto:lex@test.com)'           | '123.456.4569' | 15000  |



Update the NULL value using the UPDATE statement, as shown below.

```SQL
UPDATE Employee SET Salary = NULL WHERE EmpId = 1;
```

| EmpId | FirstName | LastName  | Email                                           | PhoneNo        | Salary |
| ----- | --------- | --------- | ----------------------------------------------- | -------------- | ------ |
| 1     | 'John'    | 'King'    | '[john.king@abc.com](mailto:john.king@abc.com)' | '650.127.1834' |        |
| 2     | 'James'   | 'Bond'    |                                                 | '123.456.4568' |        |
| 3     | 'Neena'   | 'Kochhar' | '[neena@test.com](mailto:neena@test.com)'       |                | 17000  |
| 4     | 'Lex'     | 'De Haan' | '[lex@test.com](mailto:lex@test.com)'           | '123.456.4569' | 15000  |







# CASE

The `CASE` expression goes through conditions and returns a value when the first condition is met (like an if-then-else statement). So, once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the `ELSE` clause.

If there is no `ELSE` part and no conditions are true, it returns NULL.

## Syntax

```
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    WHEN conditionN THEN resultN
    ELSE result
END;
```



## Example - Players

```
SELECT player_name,
       year,
       CASE WHEN year = 'SR' THEN 'yes'
            ELSE NULL END AS is_a_senior
  FROM benn.college_football_players
```



### Adding multiple conditions to a CASE statement

You can also define a number of outcomes in a `CASE` statement by including as many `WHEN`/`THEN` statements as you'd like:

```sql
SELECT player_name,
       weight,
       CASE WHEN weight > 250 THEN 'over 250'
            WHEN weight > 200 THEN '201-250'
            WHEN weight > 175 THEN '176-200'
            ELSE '175 or under' END AS weight_group
  FROM benn.college_football_players
```

 

### Using CASE with aggregate functions

`CASE`'s slightly more complicated and substantially more useful functionality comes from pairing it with [aggregate functions](https://mode.com/sql-tutorial/sql-aggregate-functions). For example, let's say you want to only count rows that fulfill a certain condition. Since [`COUNT`](https://mode.com/sql-tutorial/sql-count) ignores nulls, you could use a `CASE` statement to evaluate the condition and produce null or non-null values depending on the outcome:

```sql
SELECT CASE WHEN year = 'FR' THEN 'FR'
            ELSE 'Not FR' END AS year_group,
            COUNT(1) AS count
  FROM benn.college_football_players
 GROUP BY CASE WHEN year = 'FR' THEN 'FR'
               ELSE 'Not FR' END
```





https://mode.com/sql-tutorial/sql-case/

## Example - Orders

| OrderDetailID | OrderID | ProductID | Quantity |
| :------------ | :------ | :-------- | :------- |
| 1             | 10248   | 11        | 12       |
| 2             | 10248   | 42        | 10       |
| 3             | 10248   | 72        | 5        |
| 4             | 10249   | 14        | 9        |
| 5             | 10249   | 51        | 40       |

### Case

The following SQL goes through conditions and returns a value when the first condition is met:

```SQL
SELECT OrderID, Quantity,
CASE
    WHEN Quantity > 30 THEN 'The quantity is greater than 30'
    WHEN Quantity = 30 THEN 'The quantity is 30'
    ELSE 'The quantity is under 30'
END AS QuantityText
FROM OrderDetails;
```

**Output**

Number of Records: 2155

| OrderID | Quantity | QuantityText                    |
| :------ | :------- | :------------------------------ |
| 10248   | 12       | The quantity is under 30        |
| 10248   | 10       | The quantity is under 30        |
| 10248   | 5        | The quantity is under 30        |
| 10249   | 9        | The quantity is under 30        |
| 10249   | 40       | The quantity is greater than 30 |
| 10250   | 10       | The quantity is under 30        |
| 10250   | 35       | The quantity is greater than 30 |
| 10250   | 15       | The quantity is under 30        |

### Case - ORDER BY

The following SQL will order the customers by City. However, if City is NULL, then order by Country:

```
SELECT CustomerName, City, Country
FROM Customers
ORDER BY
(CASE
    WHEN City IS NULL THEN Country
    ELSE City
END);
```

**Output**

Number of Records: 91

| CustomerName                 | City         | Country   |
| :--------------------------- | :----------- | :-------- |
| Drachenblut Delikatessend    | Aachen       | Germany   |
| Rattlesnake Canyon Grocery   | Albuquerque  | USA       |
| Old World Delicatessen       | Anchorage    | USA       |
| Vaffeljernet                 | Århus        | Denmark   |
| Galería del gastrónomo       | Barcelona    | Spain     |
| LILA-Supermercado            | Barquisimeto | Venezuela |
| Magazzini Alimentari Riuniti | Bergamo      | Italy     |

## References

- https://www.w3schools.com/sql/sql_case.asphttps://www.w3schools.com/sql/sql_case.asp
