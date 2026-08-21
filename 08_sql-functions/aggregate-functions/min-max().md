## MIN() & MAX()

### Syntax

```SQL
-- MIN()
SELECT MIN(column_name)
FROM table_name
WHERE condition;

-- MAX()
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```



### Example - Products

Below is a selection from the "Products" table in the Northwind sample database:

| ProductID | ProductName                  | SupplierID | CategoryID | Unit                | Price |
| :-------- | :--------------------------- | :--------- | :--------- | :------------------ | :---- |
| 1         | Chais                        | 1          | 1          | 10 boxes x 20 bags  | 18    |
| 2         | Chang                        | 1          | 1          | 24 - 12 oz bottles  | 19    |
| 3         | Aniseed Syrup                | 1          | 2          | 12 - 550 ml bottles | 10    |
| 4         | Chef Anton's Cajun Seasoning | 2          | 2          | 48 - 6 oz jars      | 22    |
| 5         | Chef Anton's Gumbo Mix       | 2          | 2          | 36 boxes            | 21.35 |



#### MIN()  

The following SQL statement finds the price of the cheapest product:

```SQL
SELECT MIN(Price) AS SmallestPrice
FROM Products;

-- OUTPUT

SmallestPrice
2.5
```



#### MAX()  

```sql
SELECT MAX(Price) AS LargestPrice
FROM Products; 

-- OUTPUT
LargestPrice
263.5
```



# REFERENCES

* https://www.geeksforgeeks.org/sql/sql-functions/

* https://www.w3schools.com/sql/sql_count_avg_sum.asp

* https://www.tutorialsteacher.com/sql/count-function

* https://www.tutorialsteacher.com/sql/avg-function

* https://www.tutorialsteacher.com/sql/sum-function

* Aggregate functions: https://youtu.be/jcoJuc5e3RE

* https://dev.mysql.com/doc/refman/8.0/en/string-functions.html

* https://dev.mysql.com/doc/refman/8.0/en/numeric-functions.html

* https://www.w3schools.com/sql/sql_min_max.asp