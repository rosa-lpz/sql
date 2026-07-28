# SQL JOINS
## **INNER JOIN**

Returns records that have matching values in two or more tables.

```sql
SELECT table1.column_name(s), table2.column_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name = table2.column_name;
```



## LEFT JOIN

Returns all records from the left table, and the matched records from the right table.

It returns NULL for all non-matching records from the right table.

```sql
SELECT column_name(s)
FROM table1
LEFT JOIN table2
ON table1.column_name = table2.column_name;
```



## **RIGHT JOIN:**

Returns all records from the right table, and the matched records from the left table.

The RIGHT JOIN returns NULL for all non-matching records from the left table. In some databases, it is called RIGHT OUTER JOIN.

```sql
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name = table2.column_name;
```



## **FULL JOIN**

Returns all records when there is a match in either left or right table. It includes NULL for any non-matching records.

```SQL
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2
ON table1.column_name = table2.column_name;
```

**Note:** `FULL OUTER JOIN` can potentially return very large result-sets!



## **SELF JOIN**

```SQL
SELECT column_name(s)
FROM table1 T1, table1 T2
WHERE condition;
```



## CROSS JOIN

The `CROSS JOIN` keyword returns all records from both tables (table1 and table2).

```sql
SELECT column_name(s)
FROM table1
CROSS JOIN table2;
```

**Note:** The `CROSS JOIN` keyword returns all matching records from both tables whether the other table matches or not. So, if there are rows in "Customers" that do not have matches in "Orders", or if there are rows in "Orders" that do not have matches in "Customers", those rows will be listed as well.

If you add a `WHERE` clause (if table1 and table2 has a relationship), the `CROSS JOIN` will produce the same result as the `INNER JOIN` clause:








### References

* https://www.sqlshack.com/sql-multiple-joins-for-beginners-with-examples/
