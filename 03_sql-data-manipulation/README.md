# SQL Data Manipulation

Data Manipulation Language (DML): This sub-language is used to manipulate data within a database. It includes commands such as SELECT, INSERT, UPDATE, and DELETE to retrieve, add, modify, and delete data in tables.

Commands are not auto-committed which means it can’t save the data permanently in a database.

Here are the DML commands - _INSERT, UPDATE, DELETE_



**SELECT:** The `SELECT` statement is used to select data from a database.

```sql
SELECT column1, column2, ...
FROM table_name;
```
For more details go to 

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

# Content (with more details)
* [SELECT](select.md)
* [UPDATE](update.md)
* [INSERT](insert.md)
* [DELETE](delete.md)





# References

* https://www.analyticsvidhya.com/blog/2022/05/an-introduction-to-sql-commands-for-beginners/#:~:text=SQL%20includes%205%20types%20of,DRL%2C%20DCL%2C%20and%20TCL
* https://www.tutorialsteacher.com/sql/sql-insert-statement
