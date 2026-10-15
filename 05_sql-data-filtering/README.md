# SQL Data Filtering

To filter data in SQL we use operators.

## Content
* **[SQL Operators](01_sql-operators/README.md)**
    * [Syntax](01_sql-operators/README.md#syntax)
    * [Classification of SQL Operators](01_sql-operators/README.md#classification-of-sql-operators)
        * Arithmetic Operators
        * Bitwise Operators
        * Comparison Operators
        * Compound Operators
        * Logical Operators
        * Complex Clauses
* **[Comparison Operators](comparison-operators/)**
* **[Logical Operators](logical-operators/)**
    * [AND, OR and NOT](#and-or-and-not)
    * [BETWEEN](logical-operators/between/README.md#between)
    * [NOT BETWEEN](logical-operators/between/README.md#not-between)
    * [BETWEEN dates](logical-operators/between/README.md#between-dates)
    * [IN](logical-operators/README.md#in)
    * [NOT IN](logical-operators/README.md#not-in)
    * [LIKE](logical-operators/like/README.md#like)
* [IS NULL & IS NOT NULL](#is-null--is-not-null)







# CASE

The `CASE` expression goes through conditions and returns a value when the first condition is met (like an if-then-else statement). So, once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the `ELSE` clause.

If there is no `ELSE` part and no conditions are true, it returns NULL.

## Syntax

```
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    WHEN conditionN THEN resultN
    ELSE result
END;
```



## Example - Players

```
SELECT player_name,
       year,
       CASE WHEN year = 'SR' THEN 'yes'
            ELSE NULL END AS is_a_senior
  FROM benn.college_football_players
```



### Adding multiple conditions to a CASE statement

You can also define a number of outcomes in a `CASE` statement by including as many `WHEN`/`THEN` statements as you'd like:

```sql
SELECT player_name,
       weight,
       CASE WHEN weight > 250 THEN 'over 250'
            WHEN weight > 200 THEN '201-250'
            WHEN weight > 175 THEN '176-200'
            ELSE '175 or under' END AS weight_group
  FROM benn.college_football_players
```

 

### Using CASE with aggregate functions

`CASE`'s slightly more complicated and substantially more useful functionality comes from pairing it with [aggregate functions](https://mode.com/sql-tutorial/sql-aggregate-functions). For example, let's say you want to only count rows that fulfill a certain condition. Since [`COUNT`](https://mode.com/sql-tutorial/sql-count) ignores nulls, you could use a `CASE` statement to evaluate the condition and produce null or non-null values depending on the outcome:

```sql
SELECT CASE WHEN year = 'FR' THEN 'FR'
            ELSE 'Not FR' END AS year_group,
            COUNT(1) AS count
  FROM benn.college_football_players
 GROUP BY CASE WHEN year = 'FR' THEN 'FR'
               ELSE 'Not FR' END
```





https://mode.com/sql-tutorial/sql-case/

## Example - Orders

| OrderDetailID | OrderID | ProductID | Quantity |
| :------------ | :------ | :-------- | :------- |
| 1             | 10248   | 11        | 12       |
| 2             | 10248   | 42        | 10       |
| 3             | 10248   | 72        | 5        |
| 4             | 10249   | 14        | 9        |
| 5             | 10249   | 51        | 40       |

### Case

The following SQL goes through conditions and returns a value when the first condition is met:

```SQL
SELECT OrderID, Quantity,
CASE
    WHEN Quantity > 30 THEN 'The quantity is greater than 30'
    WHEN Quantity = 30 THEN 'The quantity is 30'
    ELSE 'The quantity is under 30'
END AS QuantityText
FROM OrderDetails;
```

**Output**

Number of Records: 2155

| OrderID | Quantity | QuantityText                    |
| :------ | :------- | :------------------------------ |
| 10248   | 12       | The quantity is under 30        |
| 10248   | 10       | The quantity is under 30        |
| 10248   | 5        | The quantity is under 30        |
| 10249   | 9        | The quantity is under 30        |
| 10249   | 40       | The quantity is greater than 30 |
| 10250   | 10       | The quantity is under 30        |
| 10250   | 35       | The quantity is greater than 30 |
| 10250   | 15       | The quantity is under 30        |

### Case - ORDER BY

The following SQL will order the customers by City. However, if City is NULL, then order by Country:

```
SELECT CustomerName, City, Country
FROM Customers
ORDER BY
(CASE
    WHEN City IS NULL THEN Country
    ELSE City
END);
```

**Output**

Number of Records: 91

| CustomerName                 | City         | Country   |
| :--------------------------- | :----------- | :-------- |
| Drachenblut Delikatessend    | Aachen       | Germany   |
| Rattlesnake Canyon Grocery   | Albuquerque  | USA       |
| Old World Delicatessen       | Anchorage    | USA       |
| Vaffeljernet                 | Århus        | Denmark   |
| Galería del gastrónomo       | Barcelona    | Spain     |
| LILA-Supermercado            | Barquisimeto | Venezuela |
| Magazzini Alimentari Riuniti | Bergamo      | Italy     |

## References

- https://www.w3schools.com/sql/sql_case.asphttps://www.w3schools.com/sql/sql_case.asp
