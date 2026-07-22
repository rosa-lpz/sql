# List of columns and datatypes in SQL

To retrieve a list of columns and their data types in SQL, you can query the `INFORMATION_SCHEMA.COLUMNS` view or database-specific system tables.

## Standard SQL (MySQL, PostgreSQL, etc.)
The most portable method uses the `INFORMATION_SCHEMA` view:

```sql
SELECT COLUMN_NAME, DATA_TYPE
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME = 'YourTableName';
```

## SQL Server
For SQL Server, you can use `INFORMATION_SCHEMA` or system views for more detail (like precision and scale):

**Using INFORMATION_SCHEMA:**
```sql
SELECT COLUMN_NAME, DATA_TYPE
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME = 'YourTableName';
```

**Using System Views (Detailed):**
```sql
SELECT 
    c.name AS ColumnName,
    t.name AS DataType,
    c.max_length AS MaxLength,
    c.precision AS Precision,
    c.scale AS Scale,
    c.is_nullable AS IsNullable
FROM sys.columns c
JOIN sys.types t ON c.user_type_id = t.user_type_id
WHERE c.object_id = OBJECT_ID('YourTableName');
```

## Oracle
In Oracle, query the `ALL_TAB_COLUMNS` view:

```sql
SELECT COLUMN_NAME, DATA_TYPE
FROM ALL_TAB_COLUMNS
WHERE TABLE_NAME = 'YOUR_TABLE_NAME'; -- Note: Table names are often uppercase in Oracle
```

### Key Data Types
Common SQL data types include:
*   **Numeric**: `INT`, `DECIMAL`, `FLOAT`, `NUMERIC`
*   **String**: `VARCHAR`, `CHAR`, `NVARCHAR`, `TEXT`
*   **Date/Time**: `DATE`, `DATETIME`, `TIMESTAMP`
*   **Boolean**: `BOOLEAN`, `BIT` (varies by dialect)

Ensure you replace `'YourTableName'` with the actual name of the table you are inspecting.

## Databricks
```sql
DESCRIBE TABLE database.table;
```