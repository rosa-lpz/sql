# WHERE

The `WHERE` clause is used to filter records. It is used to extract only those records that fulfill a specified condition.

* Constrains the result set
* Comes after the FROM clause
* Contains boolean expressions
* Only matching rows are in the result set



## Syntax

```SQL
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**Note:** The `WHERE` clause is not only used in `SELECT` statements, it is also used in `UPDATE`, `DELETE`, etc.!



## Examples



Below is a selection from the "Customers" table in the Northwind sample database:

| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| :--------- | :--------------------------------- | :----------------- | :---------------------------- | :---------- | :--------- | :------ |
| 1          | Alfreds Futterkiste                | Maria Anders       | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |



### WHERE clause - Text field

The following SQL statement selects all the customers from the country "Mexico", in the "Customers" table:

```SQL
SELECT * FROM Customers
WHERE Country='Mexico';
```



**Result**

Number of Records: 5

| CustomerID | CustomerName                       | ContactName          | Address                       | City        | PostalCode | Country |
| :--------- | :--------------------------------- | :------------------- | :---------------------------- | :---------- | :--------- | :------ |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo         | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno       | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 13         | Centro comercial Moctezuma         | Francisco Chang      | Sierras de Granada 9993       | México D.F. | 05022      | Mexico  |
| 58         | Pericles Comidas clásicas          | Guillermo Fernández  | Calle Dr. Jorge Cash 321      | México D.F. | 05033      | Mexico  |
| 80         | Tortuga Restaurante                | Miguel Angel Paolino | Avda. Azteca 123              | México D.F. | 05033      | Mexico  |



### WHERE clause - Numeric field

The following SQL statement selects all the customers from the country "Mexico", in the "Customers" table:

```SQL
SELECT * FROM Customers
WHERE CustomerID=1;
```



**Result**

Number of Records: 1

| CustomerID | CustomerName        | ContactName  | Address       | City   | PostalCode | Country |
| :--------- | :------------------ | :----------- | :------------ | :----- | :--------- | :------ |
| 1          | Alfreds Futterkiste | Maria Anders | Obere Str. 57 | Berlin | 12209      | Germany |



## References

* https://www.w3schools.com/sql/sql_where.asp

