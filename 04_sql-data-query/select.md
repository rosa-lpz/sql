# SELECT

**SELECT**–  This command is used to retrieve table data from the database based on the condition described by the WHERE condition.

```sql
SELECT * FROM table_name;

SELECT * FROM table_name WHERE condition;  
```

```sql
SELECT <COLUMN_NAME>, <COLUMN_NAME> FROM <TABLE_NAME>;

-- Example
SELECT first_name, last_name FROM person;
```



## Select List Wildcard (*)

Now, sometimes when you look at a table, and you're going to write a SELECT statement, you might think, Wow, there're a lot of column names that I'm going to have to write down. And there is a way to not have to write down every column that you want to get. That's by using the asterisk or the star. 

**This (*) is the wildcard SELECT list character.**

**pulls all the columns from a table**

..BAD PRACTICE

 If I say SELECT star FROM table name, that's going to give me all of the columns, and that might seem like a really good thing. This is not a good thing. Using star or the asterisk in a SELECT statement is considered a very bad practice. The reason it's a bad practice is if the application that's getting back your data has to look at the different columns, what happens if the database updates those columns or adds a column? Well, now the database application could be caught in a weird situation. It's much better to be explicit about the names of the columns in your SELECT list. It will benefit you greatly, even if you maybe don't understand now completely why, if you're new to SQL. But just to warn you, if you submit SQL statements with star in it to any sort of code review or maybe you have to show it to the database administrator before the database administrator will let you run that query, nobody's going to like this. Everybody is going to say, Hey, could you use column names instead.



## SELECT DISTINCT 

The `SELECT DISTINCT` statement is used to return only distinct (different) values. In other words, SELECT DISTINCT constrains results to only unique values.

Inside a table, a column often contains many duplicate values; and sometimes you only want to list the different (distinct) values.

### **Syntax**

**One column**

```sql
SELECT DISTINCT column_name
FROM table_name;
```

**Multiple columns**

```sql
SELECT DISTINCT column_1, column_2, ...column_n  
FROM table_name;
```


**Counting Unique Values**

```
SELECT COUNT(DISTINCT column_name) AS unique_count
FROM table_name;
```

### Examples

For example, from an `elements` table:

```
SELECT DISTINCT name
FROM elements;
```

This returns each unique element name once, regardless of repetitions.





## References

*  https://www.geeksforgeeks.org/sql/sql-query-to-find-unique-column-values-from-table/
*  https://www.dbvis.com/thetable/sql-distinct-a-comprehensive-guide/
*  Common in analytical or reporting queries. [reddit](https://www.reddit.com/r/SQL/comments/18w218h/how_to_only_return_unique_values/)
*  https://www.geeksforgeeks.org/sql/sql-query-to-find-unique-column-values-from-table/
*  https://learn.microsoft.com/en-us/answers/questions/470464/how-i-get-distinct-values-in-column-wise-in-sql