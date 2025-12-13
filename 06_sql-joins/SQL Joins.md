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



## MULTIPLE JOINS

* **Inner join** returns the rows that match in both tables
* **Left join** returns all rows from the left table
* **Right join** returns all rows from the right table
* **Full join** returns whole rows from both tables



### What are SQL multiple joins?

Multiple joins can be described as follows; multiple join is a query that contains the same or different join types, which are used more than once**.** Thus, we gain the ability to combine multiple tables of data in order to overcome relational database issues.



## Example 1

Green-Tree company launched a new campaign for the New Year and made different offers to its online customers. As a result of their campaign, they succeeded in converting some offers to sales. In the following examples, we will uncover the new year campaign data details of the Green-Tree company.

The company stores these campaign data details in the following tables. Now, we will create these tables through the following query and populate them with some dummy data:



```SQL
DROP TABLE IF EXISTS sales
GO
DROP TABLE IF EXISTS orders
GO
DROP TABLE IF EXISTS onlinecustomers
GO
CREATE TABLE onlinecustomers (customerid INT PRIMARY KEY IDENTITY(1,1) ,CustomerName VARCHAR(100) 
,CustomerCity VARCHAR(100) ,Customermail VARCHAR(100))
GO
CREATE TABLE orders (orderId INT PRIMARY KEY IDENTITY(1,1) , customerid INT  ,
ordertotal float ,discountrate float ,orderdate DATETIME)
GO
CREATE TABLE sales (salesId INT PRIMARY KEY IDENTITY(1,1) , 
orderId INT  ,
salestotal FLOAT)
GO
 
 
INSERT INTO [dbo].[onlinecustomers]([CustomerName],[CustomerCity],[Customermail]) VALUES (N'Salvador',N'Philadelphia',N'tyiptqo.wethls@chttw.org')
INSERT INTO [dbo].[onlinecustomers]([CustomerName],[CustomerCity],[Customermail]) VALUES (N'Gilbert',N'San Diego',N'rrvyy.wdumos@lklkj.org')
INSERT INTO [dbo].[onlinecustomers]([CustomerName],[CustomerCity],[Customermail]) VALUES (N'Ernest',N'New York',N'ymuea.pnxkukf@dwv.org')
INSERT INTO [dbo].[onlinecustomers]([CustomerName],[CustomerCity],[Customermail]) VALUES (N'Stella',N'Phoenix',N'xvsfzp.rjhtni@rdn.com')
INSERT INTO [dbo].[onlinecustomers]([CustomerName],[CustomerCity],[Customermail]) VALUES (N'Jorge',N'Los Angeles',N'oykbo.vlxopp@nmwhv.org')
INSERT INTO [dbo].[onlinecustomers]([CustomerName],[CustomerCity],[Customermail]) VALUES (N'Jerome',N'San Antonio',N'wkabc.ofmhetq@gtmh.co')
INSERT INTO [dbo].[onlinecustomers]([CustomerName],[CustomerCity],[Customermail]) VALUES (N'Edward',N'Chicago',N'wguexiymy.nnbdgpc@juc.co')
 
GO
 
INSERT INTO [dbo].[orders]([customerid],[ordertotal],[discountrate],[orderdate]) VALUES (3,1910.64,5.49,CAST('03-Dec-2019' AS DATETIME))
INSERT INTO [dbo].[orders]([customerid],[ordertotal],[discountrate],[orderdate]) VALUES (4,150.89,15.33,CAST('11-Jun-2019' AS DATETIME))
INSERT INTO [dbo].[orders]([customerid],[ordertotal],[discountrate],[orderdate]) VALUES (5,912.55,13.74,CAST('15-Sep-2019' AS DATETIME))
INSERT INTO [dbo].[orders]([customerid],[ordertotal],[discountrate],[orderdate]) VALUES (7,418.24,14.53,CAST('28-May-2019' AS DATETIME))
INSERT INTO [dbo].[orders]([customerid],[ordertotal],[discountrate],[orderdate]) VALUES (55,512.55,13.74,CAST('15-Jun-2019' AS DATETIME))
INSERT INTO [dbo].[orders]([customerid],[ordertotal],[discountrate],[orderdate]) VALUES (57,118.24,14.53,CAST('28-Dec-2019' AS DATETIME))
GO
 
INSERT INTO [dbo].[sales]([orderId],[salestotal]) VALUES (3,370.95)
INSERT INTO [dbo].[sales]([orderId],[salestotal]) VALUES (4,882.13)
INSERT INTO [dbo].[sales]([orderId],[salestotal]) VALUES (12,370.95)
INSERT INTO [dbo].[sales]([orderId],[salestotal]) VALUES (13,882.13)
INSERT INTO [dbo].[sales]([orderId],[salestotal]) VALUES (55,170.95)
INSERT INTO [dbo].[sales]([orderId],[salestotal]) VALUES (57,382.13)
```



## How SQL multiple joins work?

**Business problem**: Which customers were interested in this New Year campaign?

In order to answer this question, we need to find out the matched rows for all the tables because some customers did not receive an email offer, and some offers could not be converted into a sale. The following Venn diagram will help us to figure out the matched rows which we need. In short, the result of this query should be the intersecting rows of all tables in the query. The grey-colored area specifies these rows in the Venn diagram:





The SQL multiple joins approach will help us to join **onlinecustomers**, **orders,** and **sales** tables. As shown in the Venn diagram, we need to matched rows of all tables. For this reason, we will combine all tables with an **inner join** clause. The following query will return a result set that is desired from us and will answer the question:

```SQL
SELECT customerName, customercity, customermail, salestotal
FROM onlinecustomers AS oc
   INNER JOIN
   orders AS o
   ON oc.customerid = o.customerid
   INNER JOIN
   sales AS s
   ON o.orderId = s.orderId
```

At first, we will analyze the query. An inner join clause that is between **onlinecustomers** and **orders** tables derived the matched rows between these two tables. The second inner join clause that combines the **sales** table derived the matched rows from the previous result set. The following colored tables illustration will help us to understand the joined tables data matching in the query. The yellow-colored rows specify matched data between **onlinecustomers** and **orders.** On the other hand, only the blue colored rows exist in the **sales** tables so the query result will be blue colored rows:







### References

* https://www.sqlshack.com/sql-multiple-joins-for-beginners-with-examples/
