# NULL Functions

If a field in a table is optional, it is possible to insert or update a record without adding any value to this field. This way, the field will be saved with a `NULL` value.

A `NULL` value represents an unknown,  missing, or inapplicable data in a database field. It is not a value  itself, but a placeholder to indicate the absence of data.

To fetch the NULL values from a table, we can use keywords, NULL or NOT NULL. You can not select NULL data of a table by using any comparison operators (e.g. =, !=, >, < ). The special clause IS NULL or IS NOT NULL is needed to check it.

**Note:** A `NULL` value is different from zero (0) or an empty string (''). A field with a `NULL` value is one that has been left blank upon record creation.

## Test for null values

It is not possible to test for NULL values with comparison operators, such as  =, <, or <>. We will have to use the `IS NULL` and ` IS NOT NULL` operators instead.

### IS NULL Syntax

```sql
SELECT column_names
FROM table_name
WHERE column_name IS NULL; 
```

### IS NOT NULL Syntax

```sql
SELECT column_names
FROM table_name
WHERE column_name IS NULL; 
```



## Example - Employee table

| mpId | FirstName | LastName  | Email                                           | PhoneNo        | Salary |
| ---- | --------- | --------- | ----------------------------------------------- | -------------- | ------ |
| 1    | 'John'    | 'King'    | '[john.king@abc.com](mailto:john.king@abc.com)' | '650.127.1834' | 33000  |
| 2    | 'James'   | 'Bond'    |                                                 | '123.456.4568' |        |
| 3    | 'Neena'   | 'Kochhar' | '[neena@test.com](mailto:neena@test.com)'       |                | 17000  |
| 4    | 'Lex'     | 'De Haan' | '[lex@test.com](mailto:lex@test.com)'           | '123.456.4569' | 15000  |



The following example will select employees with `PhoneNo` as NULL.

```sql
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







# References

* https://www.w3schools.com/sql/sql_null_values.asp

* https://www.w3schools.com/sql/sql_isnull.asp

  

### Videos

* Data with Baraa - [SQL NULL Functions | COALESCE, ISNULL, NULLIF, IS (NOT) NULL](https://youtu.be/X_cPXHV2NQ4?list=PLNcg_FV9n7qZY_2eAtUzEUulNjTJREhQe)
* 
