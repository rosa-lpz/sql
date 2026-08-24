# SQL VIEWS
The CREATE VIEW statement in SQL is used to create a virtual table based on the result of a SELECT query. A view does not store data physically but acts like a table that can be queried like any regular table.
A view contains rows and columns, just like a real table. The fields in a view are fields from one or more real tables in the database.
You can add SQL statements and functions to a view and present the data as if the data were coming from one single table.

* A view is a named SQL query stored in the database.
* Views can include joins, filtering conditions, grouping, and aggregation.
* You can select data from a view just like a table using SELECT statement.
* Views do not store data, they display data from the underlying base tables.

## Create View

A view is created with the `CREATE VIEW` statement. 

```SQL
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**Note:** A view always shows up-to-date data! The database engine recreates the view, every time a user queries it.

### Example: Create a Simple View
#### Create table
Assume we have created a table named CUSTOMERS using the CREATE TABLE statement using the following query:
```SQL
CREATE TABLE CUSTOMERS (
   ID INT NOT NULL,
   NAME VARCHAR (20) NOT NULL,
   AGE INT NOT NULL,
   ADDRESS CHAR (25),
   SALARY DECIMAL (18, 2),
   PRIMARY KEY (ID)
);

```
Now, let us insert few records into this table using the INSERT statement as follows:

```SQL
INSERT INTO CUSTOMERS VALUES 
(1, 'Ramesh', 32, 'Ahmedabad', 2000.00 ),
(2, 'Khilan', 25, 'Delhi', 1500.00 ),
(3, 'Kaushik', 23, 'Kota', 2000.00 ),
(4, 'Chaitali', 25, 'Mumbai', 6500.00 ),
(5, 'Hardik', 27, 'Bhopal', 8500.00 ),
(6, 'Komal', 22, 'Hyderabad', 4500.00 ),
(7, 'Muffy', 24, 'Indore', 10000.00 );
```
The table will be created as follows:

|ID |	NAME 	|SALARY|
|---|---|---|
|1|	Ramesh|	2000.00|
|2|	Khilan|	1500.00|
|3|	Kaushik|	2000.00|
|4|	Chaitali|	6500.00|
|5|	Hardik	|8500.00|
|6|	Komal	|4500.00|
|7|	Muffy	|10000.00|

#### Create view
Now, we create a view that displays only the ID, NAME, and SALARY of customers from the CUSTOMERS table:
```SQL
CREATE VIEW CUSTOMER_SALARY_VIEW AS
SELECT ID, NAME, SALARY
FROM CUSTOMERS;
```
We get the following output:
```SQL
Query OK, 0 rows affected (0.05 sec)
```

#### Verification

You can retrieve data from the view using the following SELECT query:

```SQL
SELECT * FROM CUSTOMER_SALARY_VIEW;
```

Following is the table produced:

|ID |	NAME 	|SALARY|
|---|---|---|
|1|	Ramesh|	2000.00|
|2|	Khilan|	1500.00|
|3|	Kaushik|	2000.00|
|4|	Chaitali|	6500.00|
|5|	Hardik	|8500.00|
|6|	Komal	|4500.00|
|7|	Muffy	|10000.00|


# References

* https://www.w3schools.com/sql/sql_view.asp
* https://www.tutorialspoint.com/sql/sql-create-view.htm