# FROM

**Defines the table that you want to query**. **It is possible to query multiple tables**. A good practice is, instead of saying:

```sql
SELECT first_name, last_name FROM person;
```

 it's a good idea to qualify every column name in your select list with the table name. 

```sql
SELECT person.first_name, person.last_name FROM person; -- Good practice
```

Simplify using an alias "p" -- Best practice

```sql
SELECT p.first_name, p.last_name FROM person p; // Simplify using an alias "p" -- Best practice
```



# Queries with Constraints

Now all of the queries that we've done so far have returned all of the columns from the table. Although you will sometimes run such a query, it is fairly unusual. Most of the time what you want is some subset of the data. You want to constrain the rows that get returned to your dataset from the SQL statement. And so there are really two ways to constrain the number of results. One way is to add a WHERE clause to your SELECT statement. The WHERE clause we're going to cover in detail in the next module. So I'm going to cover the other way that we can constrain the number of results, and that's by using the DISTINCT qualifier.

* WHERE CLAUSE

* DISTINCT Qualifier

  

