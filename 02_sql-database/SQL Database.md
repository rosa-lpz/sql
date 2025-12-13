# SQL Database

Data Definition Language (DDL): This sub-language is used to define and manage the structure of a database. It includes commands such as CREATE, ALTER, and DROP to create and modify tables, indexes, views, and other database objects.

## Create database

Now the first thing we want to do is create a database. Oddly enough, the CREATE DATABASE command is not part of the SQL standard. It is, however, supported by almost all implementations. So this'll be the first command that we will use to specify we want to create this container, and the container's going to contain some number of tables. We want to organize our tables in a logical way, related tables together inside of a database. There's lots of other reasons for partitioning databases in particular ways. Some have to do with querying, some have to do with performance, some have to do with reliability and availability, all things beyond the scope of this course. Now once you have a database, if you want to execute a query inside of that database, there are two ways to do that. One is to use the USE DATABASE statement. All queries that happen after the USE DATABASE statement will happen in the context of that database. Or you can fully qualify the table name to the database instead. This is actually generally a best practice to fully qualify the table name. In some databases it's known that fully qualifying the table name can actually lead to an increase in performance in your queries. So here's our CREATE DATABASE statement. This is going to create a database called Contact. Now if we want to query a table inside of the Contact database, we can either use the USE DATABASE Contact. Once we execute that command, all the other queries that we execute after that in the same session will be scoped to the Contact database until we say USE DATABASE, some other database name. Again, another way to do this is to write your queries in such a way that no matter where they're executed from, they are qualified to the name of the database and table. And again, this is probably a slightly better way of doing it than the USE DATABASE command.




```sql
CREATE DATABASE contacts_V2;
USE contacts_V2;

CREATE TABLE person (
	person_id INTEGER,
    person_first_name VARCHAR(256),
    person_last_name VARCHAR(256)
    
);
```

## Create table

```sql
CREATE TABLE person (
	person_id INTEGER,
    person_first_name VARCHAR(256),
    person_last_name VARCHAR(256)
    
);
```



## DB & Table - Examples

### **Example 1 - record company**

```sql
CREATE DATABASE record_company;
USE record_company;
CREATE TABLE bands (
	id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    PRIMARY KEY (id)
);

CREATE TABLE albums (
	id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    release_year INT,
    band_id INT NOT NULL,
    PRIMARY KEY (id),
    FOREIGN KEY(band_id) REFERENCES band(id)
);

```



## SQL Constraints

Constraints can be specified when the table is created with the `CREATE TABLE` statement, or after the table is created with the `ALTER TABLE` statement.

Syntax

```sql
CREATE TABLE _table_name _(  
  _    column1 datatype_ _constraint_,  
  _    column2 datatype_ _constraint_,  
  _    column3 datatype_ _constraint_,  
     ....  
 );
```

**SQL constraints** are used to specify rules for the data in a table.

Constraints are used to limit the type of data that can go into a table. This ensures the accuracy and reliability of the data in the table. If there is any violation between the constraint and the data action, the action is aborted.

Constraints can be column level or table level. Column level constraints apply to a column, and table level constraints apply to the whole table.

The following constraints are commonly used in SQL:

* `NOT NULL` \- Ensures that a column cannot have a NULL value
* `UNIQUE` \- Ensures that all values in a column are different
* `PRIMARY KEY` \- A combination of a `NOT NULL` and `UNIQUE`. Uniquely identifies each row in a table
* `FOREIGN KEY` \- Prevents actions that would destroy links between tables
* `CHECK` \- Ensures that the values in a column satisfies a specific condition
* `DEFAULT` \- Sets a default value for a column if no value is specified
* `CREATE INDEX` \- Used to create and retrieve data from the database very quickly

## SQL Index

The `CREATE INDEX` statement is used to create indexes in tables.

Indexes are used to retrieve data from the database more quickly than otherwise. The users cannot see the indexes, they are just used to speed up searches/queries.

* When we create an index, the database will generate a method to rapidly find data based one or more columns.

**Note:** Updating a table with indexes takes more time than updating a table without (because the indexes also need an update). So, only create indexes on columns that will be frequently searched against.



### Syntax

```SQL
CREATE INDEX index_name
ON table_name (column1, column2, ...);
```



Example

````SQL
CREATE INDEX idx_pname
ON Persons (LastName, FirstName);
````





### Reference

* SQL Index |¦| Indexes in SQL |¦| Database Index
  * https://youtu.be/fsG1XaZEa78



## ALTER Table Statements

* Rename columns
* Modify column type
* Rename tables
* Drop tables



### Add columns in the table

**Syntax**

```SQL
ALTER TABLE table_name 
ADD column_name1 data_type,
    column_name2 data_type,
    ...  
```

**Example**

```SQL
ALTER TABLE Employee 
ADD Address VARCHAR(100),
    City VARCHAR(25),
    PinCode integer;
```



https://www.tutorialsteacher.com/sql/sql-alter-table



### Rename columns

**Syntax**

```SQL
ALTER TABLE table_name 
RENAME COLUMN old_column_name TO new_column_name;
```

https://www.tutorialsteacher.com/sql/sql-rename-columns



### Modify column type

**Syntax**

```SQL
ALTER TABLE table_name ALTER COLUMN column_name newDATATYPE;

-- Example - SQL Server
ALTER TABLE Employee ALTER COLUMN FirstName VARCHAR(50);

-- Example - PostgreeSQL
ALTER TABLE Employee 
ALTER COLUMN FirstName TYPE VARCHAR(50);
```

https://www.tutorialsteacher.com/sql/sql-modify-column-datatype-size

### Rename tables

Different databases support the different syntax to rename a table.

Use the following ALTER TABLE RENAME script to rename table names in the MySQL, PostgreSQL, and SQLite database.



```SQL
--  Rename Table in MySQL, PostgreSQL, and SQLite
ALTER TABLE Employee RENAME TO Emp;
```



https://www.tutorialsteacher.com/sql/sql-rename-table



### Drop tables

The ALTER command is a DDL command to modify the structure of existing tables in the database by adding, modifying, renaming, or dropping columns and constraints.

Use the DROP keyword to delete one or more columns from a table.

```SQL
ALTER TABLE table_name DROP column_name1, column_name2...;
```



https://www.tutorialsteacher.com/sql/sql-delete-columns



## SQL Truncate table

The TRUNCATE statement is used to delete all rows from a table in the database. It works the same as the `DELETE` statement, but you cannot use the [WHERE clause](https://www.tutorialsteacher.com/sql/sql-where-clause) with the TRUNCATE statement. The deleted rows using the TRUNCATE statement cannot be recovered. It deletes the rows permanently.

**Syntax**

```SQL
TRUNCATE TABLE table_name;
```





**References**

* https://www.tutorialsteacher.com/sql/sql-truncate-table



## SQL Merge 

The MERGE statement selects the rows from one or more tables (called Source table), and based on conditions specified, INSERT or UPDATE data to another table (called Target table).

**Syntax**

```SQL
MERGE INTO target_table_name or target_table_query
USING source_table_name or source_table_query
ON (list_of_conditions)
WHEN MATCHED THEN
    UPDATE target_table_name SET target_table_name.column_1 = source_table_name.expr_1, target_table_name.column_2 = source_table_name.expr_2,...target_table_name.column_n = source_table_name.expr_n
WHEN NOT MATCHED THEN
    INSERT (column_1,column_2...column_n)
    VALUES(source_table_name.expr_1, source_table_name.expr_2,...source_table_name.expr_n);
```



**Reference**

* https://www.tutorialsteacher.com/sql/sql-merge-statement



## SQL VIEW

In SQL, a view is a virtual table based on the result-set of an SQL statement.

A view contains rows and columns, just like a real table. The fields in a view are fields from one or more real tables in the database.

You can add SQL statements and functions to a view and present the data as if the data were coming from one single table.

A view is created with the `CREATE VIEW` statement. 

```SQL
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**Note:** A view always shows up-to-date data! The database engine recreates the view, every time a user queries it.



### References

* https://www.w3schools.com/sql/sql_view.asp



## References

* https://www.w3schools.com/sql/sql_constraints.asp 
* Youtube - Web Dev Simplified - Learn SQL In 60 Minutes
  * https://www.youtube.com/watch?v=p3qvj9hO_Bo
* https://www.w3schools.com/sql/sql_create_index.asp
* https://www.tutorialsteacher.com/sql/sql-alter-table
