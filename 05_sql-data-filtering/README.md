# SQL Data Filtering

To filter data in SQL we use operators.

## Content
* [SQL Operators](01_sql-operators/README.md)
    * [Syntax](01_sql-operators/README.md#syntax)
    * [Classification of SQL Operators](01_sql-operators/README.md#classification-of-sql-operators)
        * Arithmetic Operators
        * Bitwise Operators
        * Comparison Operators
        * Compound Operators
        * Logical Operators
        * Complex Clauses
* Comparison Operators
* **Logical Operators**
    * [AND, OR and NOT](#and-or-and-not)
    * [BETWEEN](logical-operators/between/README.md#between)
    * [NOT BETWEEN](logical-operators/between/README.md#not-between)
    * [BETWEEN dates](logical-operators/between/README.md#between-dates)
    * [IN](#in)
    * [NOT IN](#not-in)
    * [LIKE](like/README.md#like)
* [IS NULL & IS NOT NULL](#is-null--is-not-null)






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
