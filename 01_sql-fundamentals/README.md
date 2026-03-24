# SQL Fundamentals

Structured Query Language, or SQL, as it’s better known as or SQL is a special‑purpose programming language. That differentiates it from other languages, like C, C++, JavaScript, or Java, which are all general‑purpose programming languages. This means that SQL has a very particular purpose, and that purpose is to manipulate sets of data.

Now typically, we manipulate those sets of data from what we call a relational database. Typically, because there are other kinds of databases or other kinds of data sources that we can use SQL against, and even if we can’t use SQL directly against these other data sources, most query languages today have some relationship to SQL.

Now SQL has a number of standards. It’s both an ANSI and an ISO standard, and this is only really important. because that means that each relational database vendor has to implement at least the standard so that you can know that if you learn the SQL standard, you can apply that to many different databases.

## SQL sublanguages

SQL (Structured Query Language) is a domain-specific language used for managing and querying relational databases. There are several sub-languages within SQL that are used for different purposes. Here are some of the most common sub-languages of SQL:

1. **Data Definition Language (DDL):** This sub-language is used to define and manage the structure of a database. It includes commands such as CREATE, ALTER, and DROP to create and modify tables, indexes, views, and other database objects.
2. **Data Manipulation Language (DML):** This sub-language is used to manipulate data within a database. It includes commands such as SELECT, INSERT, UPDATE, and DELETE to retrieve, add, modify, and delete data in tables.
3. **Data Control Language (DCL):** This sub-language is used to manage access to a database. It includes commands such as GRANT and REVOKE to grant and revoke privileges and permissions to users and roles.
4. **Transaction Control Language (TCL):** This sub-language is used to manage transactions in a database. It includes commands such as COMMIT, ROLLBACK, and SAVEPOINT to control the state and consistency of a transaction.
5. **Data Query Language (DQL):** This sub-language is used to query data from a database. It includes commands such as SELECT to retrieve data from one or more tables based on certain conditions.
6. **Data Definition Extension Language (DDEL):** This sub-language is used to extend the functionality of SQL by adding new data types, operators, and functions to the language.

These sub-languages are essential for working with relational databases and managing data effectively.


## Basic SQL Syntax

### Introduction

The basic syntax for executing commands against a database is known as a SQL statement. And a SQL statement, again, is just an expression that tells the database what you want it to do. It's going to take that expression, it's going to parse it into its component parts, and then it's going to execute that expression, assuming, of course, that your expression is a valid SQL expression. So let's see a SQL expression being built. First, here's SELECT first_name FROM person. And what's really important is to have a semicolon at the end of your command. Every valid SQL expression has a semicolon at the end.

SELECT first_name FROM person;

Now let's look at these different pieces of this expression and sort of parse it the way that a database would. So SELECT. SELECT is what's known as a keyword. In fact, it's a particular kind of a keyword called a command. In this course, and I think as a good practice, I'm going to have all the SQL keywords in uppercase and all of the identifiers like first_name in lowercase. FROM is also a keyword and person is also an identifier. Alright, so SELECT and FROM are the keywords, first_name and person are the identifiers. SELECT and FROM are part of the SQL specification. First_name and person refer to things inside of my database.

```SQL
SELECT first_name FROM person;
```





## SQL Keywords

| Keyword                                                      | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ADD](https://www.w3schools.com/sql/sql_ref_add.asp)         | Adds a column in an existing table                           |
| [ADD CONSTRAINT](https://www.w3schools.com/sql/sql_ref_add_constraint.asp) | Adds a constraint after a table is already created           |
| [ALL](https://www.w3schools.com/sql/sql_ref_all.asp)         | Returns true if all of the subquery values meet the condition |
| [ALTER](https://www.w3schools.com/sql/sql_ref_alter.asp)     | Adds, deletes, or modifies columns in a table, or changes the data type of a column in a table |
| [ALTER COLUMN](https://www.w3schools.com/sql/sql_ref_alter_column.asp) | Changes the data type of a column in a table                 |
| [ALTER TABLE](https://www.w3schools.com/sql/sql_ref_alter_table.asp) | Adds, deletes, or modifies columns in a table                |
| [AND](https://www.w3schools.com/sql/sql_ref_and.asp)         | Only includes rows where both conditions is true             |
| [ANY](https://www.w3schools.com/sql/sql_ref_any.asp)         | Returns true if any of the subquery values meet the condition |
| [AS](https://www.w3schools.com/sql/sql_ref_as.asp)           | Renames a column or table with an alias                      |
| [ASC](https://www.w3schools.com/sql/sql_ref_asc.asp)         | Sorts the result set in ascending order                      |
| [BACKUP DATABASE](https://www.w3schools.com/sql/sql_ref_backup_database.asp) | Creates a back up of an existing database                    |
| [BETWEEN](https://www.w3schools.com/sql/sql_ref_between.asp) | Selects values within a given range                          |
| [CASE](https://www.w3schools.com/sql/sql_ref_case.asp)       | Creates different outputs based on conditions                |
| [CHECK](https://www.w3schools.com/sql/sql_ref_check.asp)     | A constraint that limits the value that can be placed in a column |
| [COLUMN](https://www.w3schools.com/sql/sql_ref_column.asp)   | Changes the data type of a column or deletes a column in a table |
| [CONSTRAINT](https://www.w3schools.com/sql/sql_ref_constraint.asp) | Adds or deletes a constraint                                 |
| [CREATE](https://www.w3schools.com/sql/sql_ref_create.asp)   | Creates a database, index, view, table, or procedure         |
| [CREATE DATABASE](https://www.w3schools.com/sql/sql_ref_create_database.asp) | Creates a new SQL database                                   |
| [CREATE INDEX](https://www.w3schools.com/sql/sql_ref_create_index.asp) | Creates an index on a table (allows duplicate values)        |
| [CREATE OR REPLACE VIEW](https://www.w3schools.com/sql/sql_ref_create_or_replace_view.asp) | Updates a view                                               |
| [CREATE TABLE](https://www.w3schools.com/sql/sql_ref_create_table.asp) | Creates a new table in the database                          |
| [CREATE PROCEDURE](https://www.w3schools.com/sql/sql_ref_create_procedure.asp) | Creates a stored procedure                                   |
| [CREATE UNIQUE INDEX](https://www.w3schools.com/sql/sql_ref_create_unique_index.asp) | Creates a unique index on a table (no duplicate values)      |
| [CREATE VIEW](https://www.w3schools.com/sql/sql_ref_create_view.asp) | Creates a view based on the result set of a SELECT statement |
| [DATABASE](https://www.w3schools.com/sql/sql_ref_database.asp) | Creates or deletes an SQL database                           |
| [DEFAULT](https://www.w3schools.com/sql/sql_ref_default.asp) | A constraint that provides a default value for a column      |
| [DELETE](https://www.w3schools.com/sql/sql_ref_delete.asp)   | Deletes rows from a table                                    |
| [DESC](https://www.w3schools.com/sql/sql_ref_desc.asp)       | Sorts the result set in descending order                     |
| [DISTINCT](https://www.w3schools.com/sql/sql_ref_distinct.asp) | Selects only distinct (different) values                     |
| [DROP](https://www.w3schools.com/sql/sql_ref_drop.asp)       | Deletes a column, constraint, database, index, table, or view |
| [DROP COLUMN](https://www.w3schools.com/sql/sql_ref_drop_column.asp) | Deletes a column in a table                                  |
| [DROP CONSTRAINT](https://www.w3schools.com/sql/sql_ref_drop_constraint.asp) | Deletes a UNIQUE, PRIMARY KEY, FOREIGN KEY, or CHECK constraint |
| [DROP DATABASE](https://www.w3schools.com/sql/sql_ref_drop_database.asp) | Deletes an existing SQL database                             |
| [DROP DEFAULT](https://www.w3schools.com/sql/sql_ref_drop_default.asp) | Deletes a DEFAULT constraint                                 |
| [DROP INDEX](https://www.w3schools.com/sql/sql_ref_drop_index.asp) | Deletes an index in a table                                  |
| [DROP TABLE](https://www.w3schools.com/sql/sql_ref_drop_table.asp) | Deletes an existing table in the database                    |
| [DROP VIEW](https://www.w3schools.com/sql/sql_ref_drop_view.asp) | Deletes a view                                               |
| [EXEC](https://www.w3schools.com/sql/sql_ref_exec.asp)       | Executes a stored procedure                                  |
| [EXISTS](https://www.w3schools.com/sql/sql_ref_exists.asp)   | Tests for the existence of any record in a subquery          |
| [FOREIGN KEY](https://www.w3schools.com/sql/sql_ref_foreign_key.asp) | A constraint that is a key used to link two tables together  |
| [FROM](https://www.w3schools.com/sql/sql_ref_from.asp)       | Specifies which table to select or delete data from          |
| [FULL OUTER JOIN](https://www.w3schools.com/sql/sql_ref_full_outer_join.asp) | Returns all rows when there is a match in either left table or right table |
| [GROUP BY](https://www.w3schools.com/sql/sql_ref_group_by.asp) | Groups the result set (used with aggregate functions: COUNT, MAX, MIN, SUM, AVG) |
| [HAVING](https://www.w3schools.com/sql/sql_ref_having.asp)   | Used instead of WHERE with aggregate functions               |
| [IN](https://www.w3schools.com/sql/sql_ref_in.asp)           | Allows you to specify multiple values in a WHERE clause      |
| [INDEX](https://www.w3schools.com/sql/sql_ref_index.asp)     | Creates or deletes an index in a table                       |
| [INNER JOIN](https://www.w3schools.com/sql/sql_ref_inner_join.asp) | Returns rows that have matching values in both tables        |
| [INSERT INTO](https://www.w3schools.com/sql/sql_ref_insert_into.asp) | Inserts new rows in a table                                  |
| [INSERT INTO SELECT](https://www.w3schools.com/sql/sql_ref_insert_into_select.asp) | Copies data from one table into another table                |
| [IS NULL](https://www.w3schools.com/sql/sql_ref_is_null.asp) | Tests for empty values                                       |
| [IS NOT NULL](https://www.w3schools.com/sql/sql_ref_is_not_null.asp) | Tests for non-empty values                                   |
| [JOIN](https://www.w3schools.com/sql/sql_ref_join.asp)       | Joins tables                                                 |
| [LEFT JOIN](https://www.w3schools.com/sql/sql_ref_left_join.asp) | Returns all rows from the left table, and the matching rows from the right table |
| [LIKE](https://www.w3schools.com/sql/sql_ref_like.asp)       | Searches for a specified pattern in a column                 |
| [LIMIT](https://www.w3schools.com/sql/sql_ref_limit.asp)     | Specifies the number of records to return in the result set  |
| [NOT](https://www.w3schools.com/sql/sql_ref_not.asp)         | Only includes rows where a condition is not true             |
| [NOT NULL](https://www.w3schools.com/sql/sql_ref_not_null.asp) | A constraint that enforces a column to not accept NULL values |
| [OR](https://www.w3schools.com/sql/sql_ref_or.asp)           | Includes rows where either condition is true                 |
| [ORDER BY](https://www.w3schools.com/sql/sql_ref_order_by.asp) | Sorts the result set in ascending or descending order        |
| [OUTER JOIN](https://www.w3schools.com/sql/sql_ref_outer_join.asp) | Returns all rows when there is a match in either left table or right table |
| [PRIMARY KEY](https://www.w3schools.com/sql/sql_ref_primary_key.asp) | A constraint that uniquely identifies each record in a database table |
| [PROCEDURE](https://www.w3schools.com/sql/sql_ref_procedure.asp) | A stored procedure                                           |
| [RIGHT JOIN](https://www.w3schools.com/sql/sql_ref_right_join.asp) | Returns all rows from the right table, and the matching rows from the left table |
| [ROWNUM](https://www.w3schools.com/sql/sql_ref_rownum.asp)   | Specifies the number of records to return in the result set  |
| [SELECT](https://www.w3schools.com/sql/sql_ref_select.asp)   | Selects data from a database                                 |
| [SELECT DISTINCT](https://www.w3schools.com/sql/sql_ref_select_distinct.asp) | Selects only distinct (different) values                     |
| [SELECT INTO](https://www.w3schools.com/sql/sql_ref_select_into.asp) | Copies data from one table into a new table                  |
| [SELECT TOP](https://www.w3schools.com/sql/sql_ref_select_top.asp) | Specifies the number of records to return in the result set  |
| [SET](https://www.w3schools.com/sql/sql_ref_set.asp)         | Specifies which columns and values that should be updated in a table |
| [TABLE](https://www.w3schools.com/sql/sql_ref_table.asp)     | Creates a table, or adds, deletes, or modifies columns in a table, or deletes a table or data inside a table |
| [TOP](https://www.w3schools.com/sql/sql_ref_top.asp)         | Specifies the number of records to return in the result set  |
| [TRUNCATE TABLE](https://www.w3schools.com/sql/sql_ref_truncate_table.asp) | Deletes the data inside a table, but not the table itself    |
| [UNION](https://www.w3schools.com/sql/sql_ref_union.asp)     | Combines the result set of two or more SELECT statements (only distinct values) |
| [UNION ALL](https://www.w3schools.com/sql/sql_ref_union_all.asp) | Combines the result set of two or more SELECT statements (allows duplicate values) |
| [UNIQUE](https://www.w3schools.com/sql/sql_ref_unique.asp)   | A constraint that ensures that all values in a column are unique |
| [UPDATE](https://www.w3schools.com/sql/sql_ref_update.asp)   | Updates existing rows in a table                             |
| [VALUES](https://www.w3schools.com/sql/sql_ref_values.asp)   | Specifies the values of an INSERT INTO statement             |
| [VIEW](https://www.w3schools.com/sql/sql_ref_view.asp)       | Creates, updates, or deletes a view                          |
| [WHERE](https://www.w3schools.com/sql/sql_ref_where.asp)     | Filters a result set to include only records that fulfill a specified condition |



## SQL DataTypes

The data type of a column defines what value the column can hold: integer character, money, date and time, binary, and so on. Each column in a database table is required to have a name and a data type.

An SQL developer must decide what type of data that will be stored inside each column when creating a table. The data type is a guideline for SQL to understand what type of data is expected inside of each column, and it also identifies how SQL will interact with the stored data.

## MySQL Data Types (Version 8.0)

### String Data Types

| Data type                   | Description                                                  |
| --------------------------- | ------------------------------------------------------------ |
| CHAR(size)                  | A FIXED length string (can contain letters, numbers, and special characters). The _size_ parameter specifies the column length in characters - can be from 0 to 255. Default is 1 |
| VARCHAR(size)               | A VARIABLE length string (can contain letters, numbers, and special characters). The _size_ parameter specifies the maximum string length in characters - can be from 0 to 65535 |
| BINARY(size)                | Equal to CHAR(), but stores binary byte strings. The _size_ parameter specifies the column length in bytes. Default is 1 |
| VARBINARY(size)             | Equal to VARCHAR(), but stores binary byte strings. The _size_ parameter specifies the maximum column length in bytes. |
| TINYBLOB                    | For BLOBs (Binary Large Objects). Max length: 255 bytes      |
| TINYTEXT                    | Holds a string with a maximum length of 255 characters       |
| TEXT(size)                  | Holds a string with a maximum length of 65,535 bytes         |
| BLOB(size)                  | For BLOBs (Binary Large Objects). Holds up to 65,535 bytes of data |
| MEDIUMTEXT                  | Holds a string with a maximum length of 16,777,215 characters |
| MEDIUMBLOB                  | For BLOBs (Binary Large Objects). Holds up to 16,777,215 bytes of data |
| LONGTEXT                    | Holds a string with a maximum length of 4,294,967,295 characters |
| LONGBLOB                    | For BLOBs (Binary Large Objects). Holds up to 4,294,967,295 bytes of data |
| ENUM(val1, val2, val3, ...) | A string object that can have only one value, chosen from a list of possible values. You can list up to 65535 values in an ENUM list. If a value is inserted that is not in the list, a blank value will be inserted. The values are sorted in the order you enter them |
| SET(val1, val2, val3, ...)  | A string object that can have 0 or more values, chosen from a list of possible values. You can list up to 64 values in a SET list |

### Numeric Data Types

| Data type                     | Description                                                  |
| ----------------------------- | ------------------------------------------------------------ |
| BIT(_size_)                   | A bit-value type. The number of bits per value is specified in _size_. The _size_ parameter can hold a value from 1 to 64. The default value for _size_ is 1. |
| TINYINT(_size_)               | A very small integer. Signed range is from -128 to 127. Unsigned range is from 0 to 255. The _size_ parameter specifies the maximum display width (which is 255) |
| BOOL                          | Zero is considered as false, nonzero values are considered as true. |
| BOOLEAN                       | Equal to BOOL                                                |
| SMALLINT(_size_)              | A small integer. Signed range is from -32768 to 32767. Unsigned range is from 0 to 65535. The _size_ parameter specifies the maximum display width (which is 255) |
| MEDIUMINT(_size_)             | A medium integer. Signed range is from -8388608 to 8388607. Unsigned range is from 0 to 16777215. The _size_ parameter specifies the maximum display width (which is 255) |
| INT(_size_)                   | A medium integer. Signed range is from -2147483648 to 2147483647. Unsigned range is from 0 to 4294967295. The _size_ parameter specifies the maximum display width (which is 255) |
| INTEGER(_size_)               | Equal to INT(size)                                           |
| BIGINT(_size_)                | A large integer. Signed range is from -9223372036854775808 to 9223372036854775807. Unsigned range is from 0 to 18446744073709551615. The _size_ parameter specifies the maximum display width (which is 255) |
| FLOAT(_size_, _d_)            | A floating point number. The total number of digits is specified in _size_. The number of digits after the decimal point is specified in the _d_ parameter. This syntax is deprecated in MySQL 8.0.17, and it will be removed in future MySQL versions |
| FLOAT(_p_)                    | A floating point number. MySQL uses the _p_ value to determine whether to use FLOAT or DOUBLE for the resulting data type. If _p_ is from 0 to 24, the data type becomes FLOAT(). If _p_ is from 25 to 53, the data type becomes DOUBLE() |
| DOUBLE(_size_, _d_)           | A normal-size floating point number. The total number of digits is specified in _size_. The number of digits after the decimal point is specified in the _d_ parameter |
| DOUBLE PRECISION(_size_, _d_) |                                                              |
| DECIMAL(_size_, _d_)          | An exact fixed-point number. The total number of digits is specified in _size_. The number of digits after the decimal point is specified in the _d_ parameter. The maximum number for _size_ is 65. The maximum number for _d_ is 30. The default value for _size_ is 10. The default value for _d_ is 0. |
| DEC(_size_, _d_)              | Equal to DECIMAL(size,d)                                     |

**Note:** All the numeric data types may have an extra option: UNSIGNED or ZEROFILL. If you add the UNSIGNED option, MySQL disallows negative values for the column. If you add the ZEROFILL option, MySQL automatically also adds the UNSIGNED attribute to the column.

### Date and Time Data Types

| Data type        | Description                                                  |
| ---------------- | ------------------------------------------------------------ |
| DATE             | A date. Format: YYYY-MM-DD. The supported range is from '1000-01-01' to '9999-12-31' |
| DATETIME(_fsp_)  | A date and time combination. Format: YYYY-MM-DD hh:mm:ss. The supported range is from '1000-01-01 00:00:00' to '9999-12-31 23:59:59'. Adding DEFAULT and ON UPDATE in the column definition to get automatic initialization and updating to the current date and time |
| TIMESTAMP(_fsp_) | A timestamp. TIMESTAMP values are stored as the number of seconds since the Unix epoch ('1970-01-01 00:00:00' UTC). Format: YYYY-MM-DD hh:mm:ss. The supported range is from '1970-01-01 00:00:01' UTC to '2038-01-09 03:14:07' UTC. Automatic initialization and updating to the current date and time can be specified using DEFAULT CURRENT_TIMESTAMP and ON UPDATE CURRENT_TIMESTAMP in the column definition |
| TIME(_fsp_)      | A time. Format: hh:mm:ss. The supported range is from '-838:59:59' to '838:59:59' |
| YEAR             | A year in four-digit format. Values allowed in four-digit format: 1901 to 2155, and 0000. MySQL 8.0 does not support year in two-digit format. |

### SQL Date Data Types

**MySQL** comes with the following data types for storing a date or a date/time value in the database:

- `DATE` - format YYYY-MM-DD
- `DATETIME` - format: YYYY-MM-DD HH:MI:SS
- `TIMESTAMP` - format: YYYY-MM-DD HH:MI:SS
- `YEAR` - format YYYY or YY
  

**SQL Server** comes with the following data types for storing a date or a date/time value in the database:

- `DATE` - format YYYY-MM-DD
- `DATETIME` - format: YYYY-MM-DD HH:MI:SS
- `SMALLDATETIME` - format: YYYY-MM-DD HH:MI:SS
- `TIMESTAMP` - format: a unique number
  

**Note:** The date types are chosen for a column when you create a new table in your database!

**Tip:** To keep your queries simple and easy to maintain, do not use time-components in your dates, unless you have to!

## References

- [https://www.w3schools.com/sql/sql_datatypes.asp](https://www.w3schools.com/sql/sql_datatypes.asp)
- [https://www.w3schools.com/sql/sql_dates.asp](https://www.w3schools.com/sql/sql_dates.asp)
