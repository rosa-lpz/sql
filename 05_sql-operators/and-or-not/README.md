# AND, OR and NOT

# SELECT clause

In a `SELECT`,  `AND`, `OR`, and `NOT` operators are used to create **logical/Boolean expressions**, rather than to choose columns in `WHERE` clause.

## Syntax

**AND** / **OR**

```sql
SELECT column1 AND/OR column2 , ...  
FROM table_name
---
SELECT column1 <operator> <number> AND/OR column2 =<number>, ...  -- operator: =, !=, < <=, >, >=
FROM table_name
```



**NOT**

```SQL
SELECT NOT (column1 <operator> <number> ), ... -- operator: =, !=, < <=, >, >=
FROM table_name
```



## Examples


| name | age  | salary |
| ---- | ---- | ------ |
| John | 25   | 50000  |
| Mary | 35   | 70000  |
| Bob  | 45   | 90000  |



### AND

```SQL
SELECT age > 30 AND salary > 60000
FROM employees;
```



**Output**

Conceptually, this evaluates the expression for each row:

```
John → FALSE AND FALSE → FALSE
Mary → TRUE  AND TRUE  → TRUE
Bob  → TRUE  AND TRUE  → TRUE
```



### OR

```SQL
SELECT age > 40 OR salary > 80000
FROM employees;
```



**Output**

Conceptually, this evaluates the expression for each row:

```
John → FALSE
Mary → FALSE
Bob  → TRUE
```





### NOT

```SQL
SELECT NOT (age > 30)
FROM employees;
```



**Output**

Conceptually, this evaluates the expression for each row:

```
John → TRUE
Mary → FALSE
Bob  → FALSE
```



# WHERE clause

The `WHERE` clause can be combined with `AND`, `OR`, and `NOT` operators.

The `AND` and `OR` operators are used to filter records based on more than one condition:

- The `AND` operator displays a record if all the conditions separated by `AND` are TRUE.
- The `OR` operator displays a record if any of the conditions separated by `OR` is TRUE.

The `NOT` operator displays a record if the condition(s) is NOT TRUE.



## **Syntax**

**AND**

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```



**OR**

```sql
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



# Reference

- https://www.w3schools.com/sql/sql_and_or.asp

  