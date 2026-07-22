# SQL to extract values from a column json



The exact SQL depends on your database. Here are common examples for extracting values from a JSON column.

### PostgreSQL

Assume a table:

```sql
CREATE TABLE users (
    id INT,
    profile JSONB
);
```

JSON example:

```json
{
  "name": "John",
  "age": 30,
  "address": {
    "city": "New York"
  }
}
```

Extract a string value:

```sql
SELECT profile->>'name' AS name
FROM users;
```

Extract a numeric value:

```sql
SELECT (profile->>'age')::INT AS age
FROM users;
```

Extract a nested value:

```sql
SELECT profile->'address'->>'city' AS city
FROM users;
```

------

### MySQL

Assume a JSON column named `profile`.

Extract a value:

```sql
SELECT JSON_EXTRACT(profile, '$.name') AS name
FROM users;
```

Return it as plain text:

```sql
SELECT JSON_UNQUOTE(JSON_EXTRACT(profile, '$.name')) AS name
FROM users;
```

Nested value:

```sql
SELECT JSON_UNQUOTE(JSON_EXTRACT(profile, '$.address.city')) AS city
FROM users;
```

Or using the shorthand operator:

```sql
SELECT profile->>'$.name' AS name
FROM users;
```

------

### SQL Server

```sql
SELECT JSON_VALUE(profile, '$.name') AS name
FROM users;
```

Nested value:

```sql
SELECT JSON_VALUE(profile, '$.address.city') AS city
FROM users;
```

------

### Snowflake

```sql
SELECT profile:name::STRING AS name
FROM users;
```

Nested value:

```sql
SELECT profile:address.city::STRING AS city
FROM users;
```

------

### BigQuery

```sql
SELECT JSON_VALUE(profile, '$.name') AS name
FROM users;
```

Nested value:

```sql
SELECT JSON_VALUE(profile, '$.address.city') AS city
FROM users;
```

If you tell me:

1. Which database you're using (PostgreSQL, MySQL, SQL Server, Snowflake, BigQuery, etc.), and
2. A sample JSON document,

I can provide the exact query.
