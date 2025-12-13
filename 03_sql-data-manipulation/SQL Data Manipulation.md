# SQL Data Manipulation

Data Manipulation Language (DML): This sub-language is used to manipulate data within a database. It includes commands such as SELECT, INSERT, UPDATE, and DELETE to retrieve, add, modify, and delete data in tables.

Commands are not auto-committed which means it can’t save the data permanently in a database.

Here are the DML commands - _INSERT, UPDATE, DELETE_



**SELECT:** The `SELECT` statement is used to select data from a database.

```sql
SELECT column1, column2, ...
FROM table_name;
```



**UPDATE:** The `UPDATE` statement is used to modify the existing records in a table.

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```



**DELETE:** The `DELETE` statement is used to delete existing records in a table.

```sql
DELETE FROM table_name WHERE condition;
```



## SELECT

 **The SELECT command is a command that allows you to get data. It allows you to retrieve data, one or more rows, from one or more tables.**

```sql
SELECT first_name, last_name FROM contacts;
```

If we have a SELECT statement like this, where we say SELECT first_name, last_name FROM contacts, we know that SELECT is the command. It's a keyword. FROM is a keyword. First_name, last_name, and contacts are identifiers. So we take the statement to say, please give us the first name and last name column from the table name contacts. And this is what the results set would look like.







## INSERT

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

### References

* 



## UPDATE

The `UPDATE` statement is used to modify the existing records in a table.

* Modifies column(s) in a single table
* WHERE clause dictates which rows
* SET keyword follows table name  

**UPDATE modifies one or more rows in a table**. So let's imagine that I have this table where there is a row with the first name of John and the last name of Flanders. 

<img src="/media/rlz-98/Elements 1 TB/Archivos/2. Estudios/5. Computer Science/2.1 Programming/2. SQL/table-1.PNG" alt="table-1" style="zoom:67%;" />             

If I run this UPDATE statement, UPDATE contacts, so I'm telling the database I want to UPDATE the contacts table.

```sql
UPDATE contacts SET last_name='Ahern' WHERE id=1; 

// where statement need to be specified, or every row will be updated
```

<img src="/media/rlz-98/Elements 1 TB/Archivos/2. Estudios/5. Computer Science/2.1 Programming/2. SQL/table-3.PNG" alt="table-3" style="zoom:67%;" />

I want to set the value of the last_name column to be equal to Ahern. Then I have a **WHERE** clause. The WHERE clause tells the UPDATE statement, What is the restriction on this UPDATE? If I didn't specify any **WHERE** clause with this UPDATE statement, that means that every single row in my contacts table would have its lasting value set to Ahern. In this case, that would be a bad thing. It is not always the case, however, that an UPDATE statement without a WHERE clause is a bad thing. Sometimes it's a very useful thing if you need to UPDATE all of the data in one or more columns inside of a table. But it's not very usual. It's much more usual to have a WHERE clause where you're restricting that data. Once I execute that UPDATE statement, I'll have a row in that table where the first name is Jon, the last name is Ahern, and notice the ID stayed the same. We're updating that particular row. We're not creating a whole new row.



### Example 1 - record_company







## DELETE

And the last of the basic SQL commands is DELETE. **So DELETE is there to remove one or more rows from one table.** 

So let's imagine here is my table contacts again. I've got my first_name and last_name and the auto‑incrementing ID.



What I can do is say DELETE FROM contacts. So, again, the DELETE FROM is the full real DELETE command. Contacts is the table that I want to DELETE rows from. And WHERE id = 2 is my WHERE clause or my restriction. 



Again, just like UPDATE, if I say DELETE FROM contacts and don't specify any WHERE clause, that's going to DELETE all the rows in my table. And generally speaking, that's not what you want. So having a WHERE clause in this case, again, is almost always going to be the case. And so that's going to restrict the DELETE to just those rows that match the expression in the WHERE clause. And in this case, that's going to be WHERE the ID is 2, and that's going to get rid of the row with Fritz in it. I'm going to go into these commands in more detail in later modules. So, again, this is just a short introduction to the idea of what's in a SQL statement and what are the basic SQL statements and commands that we're going to cover in this course.



# References

* https://www.analyticsvidhya.com/blog/2022/05/an-introduction-to-sql-commands-for-beginners/#:~:text=SQL%20includes%205%20types%20of,DRL%2C%20DCL%2C%20and%20TCL
* https://www.tutorialsteacher.com/sql/sql-insert-statement
