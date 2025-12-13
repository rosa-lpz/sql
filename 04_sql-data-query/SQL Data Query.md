# SQL DATA QUERY



Stands for **Data Query Language**. DQL is used to fetch data from the database.

It uses only command i.e SELECT

# SELECT

**SELECT**–  This command is used to retrieve table data from the database based on the condition described by the WHERE condition.

```sql
SELECT * FROM table_name;

SELECT * FROM table_name WHERE condition;  
```

```sql
SELECT <COLUMN_NAME>, <COLUMN_NAME> FROM <TABLE_NAME>;

-- Example
SELECT first_name, last_name FROM person;
```



## Select List Wildcard (*)

Now, sometimes when you look at a table, and you're going to write a SELECT statement, you might think, Wow, there're a lot of column names that I'm going to have to write down. And there is a way to not have to write down every column that you want to get. That's by using the asterisk or the star. 

**This (*) is the wildcard SELECT list character.**

**pulls all the columns from a table**

..BAD PRACTICE

 If I say SELECT star FROM table name, that's going to give me all of the columns, and that might seem like a really good thing. This is not a good thing. Using star or the asterisk in a SELECT statement is considered a very bad practice. The reason it's a bad practice is if the application that's getting back your data has to look at the different columns, what happens if the database updates those columns or adds a column? Well, now the database application could be caught in a weird situation. It's much better to be explicit about the names of the columns in your SELECT list. It will benefit you greatly, even if you maybe don't understand now completely why, if you're new to SQL. But just to warn you, if you submit SQL statements with star in it to any sort of code review or maybe you have to show it to the database administrator before the database administrator will let you run that query, nobody's going to like this. Everybody is going to say, Hey, could you use column names instead.



## SELECT DISTINCT 

The `SELECT DISTINCT` statement is used to return only distinct (different) values. In other words, SELECT DISTINCT constrains results to only unique values.

Inside a table, a column often contains many duplicate values; and sometimes you only want to list the different (distinct) values.

### **Syntax**

```sql
SELECT DISTINCT column_1, column_2, ...column_n  
FROM table_name;
```





# FROM

**Defines the table that you want to query**. **It is possible to query multiple tables**. A good practice is, instead of saying:

```sql
SELECT first_name, last_name FROM person;
```

 it's a good idea to qualify every column name in your select list with the table name. 

```sql
SELECT person.first_name, person.last_name FROM person; -- Good practice
```

Simplify using an alias "p" -- Best practice

```sql
SELECT p.first_name, p.last_name FROM person p; // Simplify using an alias "p" -- Best practice
```



# Queries with Constraints

Now all of the queries that we've done so far have returned all of the columns from the table. Although you will sometimes run such a query, it is fairly unusual. Most of the time what you want is some subset of the data. You want to constrain the rows that get returned to your dataset from the SQL statement. And so there are really two ways to constrain the number of results. One way is to add a WHERE clause to your SELECT statement. The WHERE clause we're going to cover in detail in the next module. So I'm going to cover the other way that we can constrain the number of results, and that's by using the DISTINCT qualifier.

* WHERE CLAUSE

* DISTINCT Qualifier

  



# WHERE

The `WHERE` clause is used to filter records. It is used to extract only those records that fulfill a specified condition.

* Constrains the result set
* Comes after the FROM clause
* Contains boolean expressions
* Only matching rows are in the result set



## **Syntax**

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

