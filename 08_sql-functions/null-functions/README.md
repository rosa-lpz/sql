# Null function

If a field in a table is optional, it is possible to insert or update a record without adding any value to this field. This way, the field will be saved with a `NULL` value.

A `NULL` value represents an unknown,  missing, or inapplicable data in a database field. It is not a value  itself, but a placeholder to indicate the absence of data.

**Note:** A `NULL` value is different from zero (0) or an empty string (''). A field with a `NULL` value is one that has been left blank upon record creation.

## Test for null values

It is not possible to test for NULL values with comparison operators, such as  =, <, or <>. We will have to use the `IS NULL` and ` IS NOT NULL` operators instead.

### IS NULL Syntax

```sql
SELECT column_names
FROM table_name
WHERE column_name IS NULL; 
```

### IS NOT NULL Syntax

```sql
SELECT column_names
FROM table_name
WHERE column_name IS NULL; 
```

### 

# References

* https://www.w3schools.com/sql/sql_null_values.asp
