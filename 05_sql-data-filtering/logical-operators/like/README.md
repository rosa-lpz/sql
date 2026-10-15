# SQL - Like operator

The `LIKE` operator is used in a `WHERE` clause to search for a specified pattern in a column. It can be used with numbers, string, or date values. However, it is recommended to use the string values.

The LIKE operator in MS SQL Server, SQLite, MySQL database are not case-sensitive, whereas it is case-sensitive in Oracle, and PostgreSQL database.

There are two wildcards often used in conjunction with the `LIKE` operator:

- The percent sign (%) represents zero, one, or multiple characters
- The underscore sign (*) represents one, single character*
- ***Note:** MS Access uses an asterisk (\*) instead of the percent sign (%), and a question mark (?) instead of the underscore (*).

## Syntax

```SQL
SELECT column1, column2, ...
FROM table_name
WHERE columnN LIKE pattern;
```

**Tip:** You can also combine any number of conditions using `AND` or `OR` operators.



## Wildcard characters 

The LIKE operator uses the following wildcard characters to specify a pattern:

| Pattern | Description                                                  |
| ------- | ------------------------------------------------------------ |
| %       | The **%** matches zero, one, or multiple characters (capital or small) or numbers. E.g. 'A%' will matche all string starting with 'A' and followed by any number of characters or numbers. |
| _       | The underscore **_** sign matches any single character or number. E.g. 'A_' will match all strings with two chars where the first character must be 'A' and second character can be anything. |
| []      | The **[]** matches any single character within the specified range in the []. E.g. 'A[e,l,p]' will match 'Apple', 'Aelp', 'Alep', 'Aple', etc. |
| [^]     | The **[^]** matches any single character except the specified range in the [^]. E.g. 'A[^e,l,p]' will match anything that starts with 'A', but not 'Apple', 'Aelp', 'Alep', 'Aple', etc. |





## **Common patterns**

Here are some examples showing different `LIKE` operators with '%' and '_' wildcards:

| LIKE Operator                    | Description                                                  |
| :------------------------------- | :----------------------------------------------------------- |
| WHERE CustomerName LIKE 'a%'     | Finds any values that start with "a"                         |
| WHERE CustomerName LIKE '%a'     | Finds any values that end with "a"                           |
| WHERE CustomerName LIKE '%or%'   | Finds any values that have "or" in any position              |
| WHERE CustomerName LIKE '_r%'    | Finds any values that have "r" in the second position        |
| WHERE CustomerName LIKE 'a_%'    | Finds any values that start with "a" and are at least 2 characters in length |
| WHERE CustomerName LIKE 'a__%'   | Finds any values that start with "a" and are at least 3 characters in length |
| WHERE ContactName LIKE 'a%o'     | Finds any values that start with "a" and ends with "o"       |
| WHERE CustomerName NOT LIKE 'a%' | Finds any values that does NOT start with "a"                |



# Examples

* [Example 1 - Customers](like-example-1.md)
* [Example 2 - Employee](like-example-2.md)
* [Example 3 - Movies](like-example-3.md)




# Performance considerations wehen using the LIKE operator

The LIKE operator is great, but it can potentially impact query performance, especially when used on large datasets. Here are some considerations to optimize its use:

- Indexes: The LIKE operator performs best when the pattern starts with a constant string, such as Adam%, because the database can use indexes. However, patterns like %Adam or %Adam% require a full table scan, which can be slow for large tables.
- Avoid leading wildcards: Starting a pattern with %, such as %pattern, disables index usage, as the database has to examine every record.
- Collation and case-insensitive matching: Using functions like LOWER() or UPPER() on columns for case-insensitive searches can also prevent indexes from being used. Instead, make sure the database collation is set appropriately for case-insensitive comparisons.
- Alternative approaches: For large datasets, consider using full-text search or database-specific search features, such as GIN indexes in PostgreSQL or FULLTEXT indexes in MySQL, when performing complex or frequent string matching.
- Selective queries: Limit the scope of your queries using additional filters, such as date ranges or numerical columns, to reduce the data processed by the LIKE operator.

### Reference
* https://www.datacamp.com/tutorial/sql-like-pattern-matching-tutorial

# Why we should not use LIKE with wildcard (%) in SQL query
Consider this common search pattern:

```SQL
SELECT * FROM customers 
WHERE name LIKE '%Smith%';
```
This query looks simple, but it harbors several serious issues:

- Index Invalidation: When you use a leading wildcard (%Smith), the database engine cannot utilize the index effectively. It's forced to perform a full table scan, examining every single row in the table.
- Resource Intensive: Full table scans consume significant CPU resources and I/O operations, especially as your table grows larger.
- Poor Scalability: As your dataset expands, query performance degrades linearly with the table size.

## Better alternatives
### Trailing wildcards only
If you must use wildcards, restrict them to the end of the search term:
```SQL
SELECT * FROM customers 
WHERE name LIKE 'Smith%';
```
This allows the database to use the index for matching the prefix, significantly improving performance.

### Full-text Search
For more complex search requirements, leverage your database’s full-text search capabilities:
```SQL
-- MySQL Example
CREATE FULLTEXT INDEX idx_name ON customers(name);

SELECT * FROM customers 
WHERE MATCH(name) AGAINST('Smith' IN NATURAL LANGUAGE MODE);
```
Full-text search provides:
- Better performance through specialized indexing
- More relevant results
- Support for complex search operations

### Trigram indexes (PostgreSQL)
PostgreSQL offers powerful trigram matching with the pg_trgm extension:
```SQL
CREATE EXTENSION pg_trgm;
CREATE INDEX idx_trgm_name ON customers USING GIN (name gin_trgm_ops);

SELECT * FROM customers 
WHERE name % 'Smith';
```
This approach provides:
- Efficient fuzzy matching
- Good performance even with wildcards
- Support for similarity searching

### Elastic Search Integration
For applications requiring advanced search capabilities, consider integrating Elasticsearch:
- Superior full-text search capabilities
- Excellent performance at scale
- Rich feature set including fuzzy matching and relevance scoring

### Reference
* - https://medium.com/@huzaifaqureshi037/the-hidden-performance-costs-of-sql-wildcards-optimizing-search-query-5ff1c9c455f0
# References

- https://www.w3schools.com/sql/sql_like.asp
- https://www.tutorialsteacher.com/sql/sql-like-operator
- https://www.datacamp.com/tutorial/sql-like-pattern-matching-tutorial
- https://sqlbolt.com/lesson/select_queries_with_constraints_pt_2
- https://medium.com/@huzaifaqureshi037/the-hidden-performance-costs-of-sql-wildcards-optimizing-search-query-5ff1c9c455f0
- https://stackoverflow.com/questions/11478995/why-is-it-not-recomended-to-use-like-in-sql
