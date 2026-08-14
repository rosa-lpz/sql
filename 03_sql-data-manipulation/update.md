
# UPDATE

The `UPDATE` statement is used to modify the existing records in a table.

* Modifies column(s) in a single table
* WHERE clause dictates which rows
* SET keyword follows table name  

**UPDATE modifies one or more rows in a table**. So let's imagine that I have this table where there is a row with the first name of John and the last name of Flanders. 

       

If I run this UPDATE statement, UPDATE contacts, so I'm telling the database I want to UPDATE the contacts table.

```sql
UPDATE contacts SET last_name='Ahern' WHERE id=1; 

// where statement need to be specified, or every row will be updated

I want to set the value of the last_name column to be equal to Ahern. Then I have a **WHERE** clause. The WHERE clause tells the UPDATE statement, What is the restriction on this UPDATE? If I didn't specify any **WHERE** clause with this UPDATE statement, that means that every single row in my contacts table would have its lasting value set to Ahern. In this case, that would be a bad thing. It is not always the case, however, that an UPDATE statement without a WHERE clause is a bad thing. Sometimes it's a very useful thing if you need to UPDATE all of the data in one or more columns inside of a table. But it's not very usual. It's much more usual to have a WHERE clause where you're restricting that data. Once I execute that UPDATE statement, I'll have a row in that table where the first name is Jon, the last name is Ahern, and notice the ID stayed the same. We're updating that particular row. We're not creating a whole new row.

```

### Example 1 - record_company


