# Substring 

## PostgreSQL
### Syntax
```sql
substr(<string>,<position_from > [,<number_of_characters>]
```

|Name	|Description	Return Type|
|---|---|
|string	|A string, in which the search will occur.|	text|
|position_from	|The starting position of search from the string.	|integer|
|number_of_characters	|A substring which may be one or more characters will be extracted from the string.	|text|

### Example

```sql
SELECT substr('w3resource',2,3) AS "Extracting characters";
```
Output
```sql
3re
```




## SQL Server 
### Syntax
```sql
SUBSTRING(string, start, length)
```
### Example

```sql
SELECT SUBSTRING(CustomerName, 1, 5) AS ExtractString, CustomerName
FROM Customers;
```
Output
|ExtractString	|CustomerName|
|---|---|
|Alfre	|Alfreds Futterkiste|
|Ana T	|Ana Trujillo Emparedados y helados|
|Anton	|Antonio Moreno Taquería|

## MySQL

### Syntax
```sql
SUBSTRING(string, start, length)
```
### Example

```sql
SELECT SUBSTRING("SQL Tutorial", 1, 3) AS ExtractString;
```

## Databrics & Spark SQL
### Syntax
```sql
substring(expr, pos [, len])
substring(expr FROM pos [FOR len] ] )
```

|Name	|Description	Return Type|
|---|---|
|expr	|An BINARY or STRING expression.|	text|
|pos 	|An integral numeric expression specifying the starting position.	|integer|
|len|An optional integral numeric expression.|integer|
 

### Example

```sql
> SELECT substring('Spark SQL', 5);
 k SQL
> SELECT substring('Spark SQL', -3);
 SQL
> SELECT substring('Spark SQL', 5, 1);
 k
> SELECT substring('Spark SQL' FROM 5);
 k SQL
> SELECT substring('Spark SQL' FROM -3);
 SQL
> SELECT substring('Spark SQL' FROM 5 FOR 1);
 k
> SELECT substring('Spark SQL' FROM -10 FOR 5);
 Spar
```



# References
* https://www.w3resource.com/PostgreSQL/substr-function.php
* https://www.w3schools.com/sql/func_mysql_substring.asp
* https://www.w3schools.com/sql/func_sqlserver_substring.asp
* https://docs.databricks.com/aws/en/sql/language-manual/functions/substring