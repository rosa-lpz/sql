# Subquery in the SELECT clause


Subqueries are most commonly used with the SELECT statement. They can be incredibly powerful for retrieving data based on dynamic conditions. Let's look at a more complex example:

```sql
SELECT product_name, price
FROM products
WHERE price > (SELECT AVG(price) FROM products);
```