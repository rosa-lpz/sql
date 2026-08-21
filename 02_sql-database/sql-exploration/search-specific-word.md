
# Searching Across ALL Columns in a Table

## Databricks
```sql
SELECT * FROM my_table 
WHERE concat_ws(' ', *) ILIKE '%apple%';
```

## PosgreSQL
```sql
SELECT * FROM my_table 
WHERE my_table::text ILIKE '%apple%';
```

# Searching the Entire Database (Metadata Search)

## Databricks
```sql
-- Search for tables that have 'apple' in their name
SHOW TABLES IN my_schema LIKE '*apple*';

-- Search for columns across the information schema
SELECT table_name, column_name 
FROM my_catalog.information_schema.columns 
WHERE column_name ILIKE '%apple%';
```
## PosgreSQL
```sql
-- Search for columns across the entire database containing 'apple'
SELECT table_schema, table_name, column_name 
FROM information_schema.columns 
WHERE table_schema NOT IN ('pg_catalog', 'information_schema')
  AND column_name ILIKE '%apple%';
  ```