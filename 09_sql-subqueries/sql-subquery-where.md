
## Example 1

```SQL
SELECT employee_name
FROM employees
WHERE department_id = (SELECT department_id FROM departments WHERE department_name = 'Marketing');
```
## Example 2
```sql
SELECT product_name, price
FROM products
WHERE price > (SELECT AVG(price) FROM products);
```