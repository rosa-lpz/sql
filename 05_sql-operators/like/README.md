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





## **Common patterns**

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





## Example 1 - Customers

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


# Performance considerations wehen using the LIKE operator

The LIKE operator is great, but it can potentially impact query performance, especially when used on large datasets. Here are some considerations to optimize its use:

- Indexes: The LIKE operator performs best when the pattern starts with a constant string, such as Adam%, because the database can use indexes. However, patterns like %Adam or %Adam% require a full table scan, which can be slow for large tables.
- Avoid leading wildcards: Starting a pattern with %, such as %pattern, disables index usage, as the database has to examine every record.
- Collation and case-insensitive matching: Using functions like LOWER() or UPPER() on columns for case-insensitive searches can also prevent indexes from being used. Instead, make sure the database collation is set appropriately for case-insensitive comparisons.
- Alternative approaches: For large datasets, consider using full-text search or database-specific search features, such as GIN indexes in PostgreSQL or FULLTEXT indexes in MySQL, when performing complex or frequent string matching.
- Selective queries: Limit the scope of your queries using additional filters, such as date ranges or numerical columns, to reduce the data processed by the LIKE operator.

### Reference
* https://www.datacamp.com/tutorial/sql-like-pattern-matching-tutorial

# Why we should not use LIKE with wildcard (%) in SQL query
Consider this common search pattern:

```SQL
SELECT * FROM customers 
WHERE name LIKE '%Smith%';
```
This query looks simple, but it harbors several serious issues:

- Index Invalidation: When you use a leading wildcard (%Smith), the database engine cannot utilize the index effectively. It's forced to perform a full table scan, examining every single row in the table.
- Resource Intensive: Full table scans consume significant CPU resources and I/O operations, especially as your table grows larger.
- Poor Scalability: As your dataset expands, query performance degrades linearly with the table size.

## Better alternatives
### Trailing wildcards only
If you must use wildcards, restrict them to the end of the search term:
```SQL
SELECT * FROM customers 
WHERE name LIKE 'Smith%';
```
This allows the database to use the index for matching the prefix, significantly improving performance.

### Full-text Search
For more complex search requirements, leverage your database’s full-text search capabilities:
```SQL
-- MySQL Example
CREATE FULLTEXT INDEX idx_name ON customers(name);

SELECT * FROM customers 
WHERE MATCH(name) AGAINST('Smith' IN NATURAL LANGUAGE MODE);
```
Full-text search provides:
- Better performance through specialized indexing
- More relevant results
- Support for complex search operations

### Trigram indexes (PostgreSQL)
PostgreSQL offers powerful trigram matching with the pg_trgm extension:
```SQL
CREATE EXTENSION pg_trgm;
CREATE INDEX idx_trgm_name ON customers USING GIN (name gin_trgm_ops);

SELECT * FROM customers 
WHERE name % 'Smith';
```
This approach provides:
- Efficient fuzzy matching
- Good performance even with wildcards
- Support for similarity searching

### Elastic Search Integration
For applications requiring advanced search capabilities, consider integrating Elasticsearch:
- Superior full-text search capabilities
- Excellent performance at scale
- Rich feature set including fuzzy matching and relevance scoring

### Reference
* - https://medium.com/@huzaifaqureshi037/the-hidden-performance-costs-of-sql-wildcards-optimizing-search-query-5ff1c9c455f0
# References

- https://www.w3schools.com/sql/sql_like.asp
- https://www.tutorialsteacher.com/sql/sql-like-operator
- https://www.datacamp.com/tutorial/sql-like-pattern-matching-tutorial
- https://sqlbolt.com/lesson/select_queries_with_constraints_pt_2
- https://medium.com/@huzaifaqureshi037/the-hidden-performance-costs-of-sql-wildcards-optimizing-search-query-5ff1c9c455f0
- https://stackoverflow.com/questions/11478995/why-is-it-not-recomended-to-use-like-in-sql
