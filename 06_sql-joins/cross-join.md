
## CROSS JOIN

The `CROSS JOIN` keyword returns all records from both tables (table1 and table2).

```sql
SELECT column_name(s)
FROM table1
CROSS JOIN table2;
```

**Note:** The `CROSS JOIN` keyword returns all matching records from both tables whether the other table matches or not. So, if there are rows in "Customers" that do not have matches in "Orders", or if there are rows in "Orders" that do not have matches in "Customers", those rows will be listed as well.

If you add a `WHERE` clause (if table1 and table2 has a relationship), the `CROSS JOIN` will produce the same result as the `INNER JOIN` clause:


