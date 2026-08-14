# INSERT

**The INSERT command adds one or more rows into a table.** **INSERT only works against a single table, unlike SELECT, which can work against multiple tables.** 



**Syntax**

```sql
INSERT INTO table_name (col1, col2, col3, ..., col n)
VALUES (value1, value2, value3..., value n);

OR

INSERT INTO table_name (col1, col2, col3, ..., col n);
    
```





So let's assume that we have the table as we described it on the last slide. We've got the context table where there's an ID column, a first_name, and a last_name. 

```sql
INSERT INTO contacts (first_name, last_name) VALUES ('Fritz', 'Onion');
```



**INSERT INTO** is the actual command. We do refer to it as INSERT as shorthand. Then we specify the table name and the columns that we want to update. The columns go inside of the parentheses. And then we specify a **VALUES** clause. In the VALUES clause, we specify the values that we want to be put into the table. 



### Example 1 - record_company



```SQL
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

INSERT INTO bands (name)
VALUES ('Iron Maiden');

INSERT INTO bands (name)
VALUES ('Deuce'), ('Avenged Sevenfold'), ('Ankor');
```



### Example 2 - Employees

Insert multiple records in a single INSERT INTO statement by having mulitiple records in parenthesis after VALUES. The following will insert two records in the `Employee` table in SQL Server, MySQL, PostgreSQL, SQLite database.

For the demo purpose, the following `Employee` table will be used in all examples here.

| EmpId | FirstName | LastName | Email | PhoneNo | Salary |
| ----- | --------- | -------- | ----- | ------- | ------ |
|       |           |          |       |         |        |

#### Insert Values to All Columns

To insert values to all columns of a table, you don't need to specify column names with the table name. Specify the values for each column in a sequence as they appear in the table.

The following statement will insert a single row in all columns of the above `Employee` table in the SQL Server, Oracle, MySQL, SQLite, and PostgreSQL database.

```SQL
INSERT INTO Employee
VALUES(1,'John','King','john.king@abc.com','123.123.1834',33000);
```

Now, the `Select * from Employee;` query will display the following result.

| EmpId | FirstName | LastName | Email               | PhoneNo        | Salary |
| ----- | --------- | -------- | ------------------- | -------------- | ------ |
| 1     | 'John'    | 'King'   | 'john.king@abc.com' | '123.123.1834' | 33000  |

 Note: Any change in the sequence, the number of values, or its data type may result in an error or incorrect data.





#### Insert Values to Specific Columns

Mention the column names in the INSERT statement to insert data to some specific columns of a table.

The following INSERT statement will add a new record to the `Employee` table in `EmpId`, `FirstName`, and `LastName` columns. Note that the INSERT statement requires the column names in the parenthesis if you don't want to insert data in all the columns but to some specific columns only.

```SQL
INSERT INTO Employee(EmpId, FirstName, LastName)
VALUES(2,'James','Bond');
```





#### Insert Multiple records

```SQL
INSERT INTO Employee 
VALUES 
(3,'Neena','Kochhar','neena@test.com','123.456.4568',17000),
(4,'Lex','De Haan','lex@test.com','123.456.4569',15000);
```

Now, the `Select * from Employee` query will display the following result.

| EmpId | FirstName | LastName  | Email               | PhoneNo        | Salary |
| ----- | --------- | --------- | ------------------- | -------------- | ------ |
| 1     | 'John'    | 'King'    | 'john.king@abc.com' | '123.123.1834' | 33000  |
| 2     | 'James'   | 'Bond'    |                     |                |        |
| 3     | 'Neena'   | 'Kochhar' | 'neena@test.com'    | '123.456.4568' | 17000  |
| 4     | 'Lex'     | 'De Haan' | 'lex@test.com'      | '123.456.4569' | 15000  |


# References

* https://www.analyticsvidhya.com/blog/2022/05/an-introduction-to-sql-commands-for-beginners/#:~:text=SQL%20includes%205%20types%20of,DRL%2C%20DCL%2C%20and%20TCL
* https://www.tutorialsteacher.com/sql/sql-insert-statement