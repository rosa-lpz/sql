# coalescence()


The COALESCE function in SQL is used to handle NULL values by returning the first non-NULL value from a list of expressions. It is particularly useful for ensuring that query results contain meaningful data, even when some values are missing.

Syntax
The basic syntax for the COALESCE function is:

COALESCE(expression1, expression2, ..., expressionN)

* expression1, expression2, ..., expressionN: These are the values or columns you want to evaluate. COALESCE will return the first non-NULL value from this list.

## References
* https://www.w3schools.com/sql/sql_isnull.asp
* https://www.stratascratch.com/blog/sql-coalesce-function-a-guide-for-postgresql-users