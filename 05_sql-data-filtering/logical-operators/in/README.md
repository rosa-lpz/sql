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



# NOT IN

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

# References

- https://www.w3schools.com/sql/sql_in.asp
- https://www.tutorialsteacher.com/sql/sql-in-operator
- 

