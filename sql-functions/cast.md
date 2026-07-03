# CAST()

The CAST() function converts a value (of any type) into a specified datatype.


## PostgreSQL
### Syntax
```sql
CAST(expression AS datatype)
```

|Parameter/Argument	|Description|
|---|---|
|expression	|Required. The value to convert|
|datatype	|Required. The datatype to convert expression to|

### Example

```sql
SELECT CAST(25.65 AS int);
```
Output
```sql
25
```
## SQL Server 
### Syntax
```sql
CAST(expression AS datatype(length))
```

|Parameter/Argument	|Description|
|---|---|
|expression	|Required. The value to convert|
|datatype	|Required. The datatype to convert expression to. Can be one of the following: bigint, int, smallint, tinyint, bit, decimal, numeric, money, smallmoney, float, real, datetime, smalldatetime, char, varchar, text, nchar, nvarchar, ntext, binary, varbinary, or image|
|(length)|	Optional. The length of the resulting data type (for char, varchar, nchar, nvarchar, binary and varbinary)|
### Example

```sql
SELECT CAST(25.65 AS int);
```
Output
```sql
25
```

## Databrics & Spark SQL
Casts the value expr to the target data type type. This operator is a synonym for :: (colon colon sign) operator
### Syntax
```sql
cast(sourceExpr AS targetType)
```
|Parameter/Argument	|Description|
|---|---|
|sourceExpr| Any castable expression.|
|targetType| The data type of the result.|

### Example

```sql
SELECT CAST(25.65 AS int);
```
Output
```sql
25
```




# References
* https://www.postgresql.org/docs/8.3/sql-expressions.html
* https://www.w3schools.com/sql/func_sqlserver_cast.asp
* https://docs.databricks.com/aws/en/sql/language-manual/functions/cast