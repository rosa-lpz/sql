# SQL Operators

## Syntax

In order to filter certain results from being returned, we need to use a `WHERE` clause in the query. The clause is applied to each row of data by checking specific column values to determine whether it should be included in the results or not.

```SQL
SELECT column1 <OPERATOR> column2  
FROM table_name  
WHERE condition;  
------  
SELECT column1, column2, …  
FROM table_name  
WHERE condition  
    AND/OR another_condition  
    AND/OR …;
```


More complex clauses can be constructed by joining numerous `AND` or `OR` logical keywords (ie. num_wheels >= 4 AND doors <= 2). And below are some useful operators that you can use for numerical data (ie. integer or floating point):



When writing `WHERE` clauses with columns containing text data, SQL supports a number of useful operators to do things like case-insensitive string comparison and wildcard pattern matching. We show a few common text-data specific operators below

## Classification of SQL Operators

The following operators can be used in the `WHERE` clause:

* Arithmetic Operators
* Bitwise Operators
* Comparison Operators
* Compound Operators
* Logical Operators
* Complex Clauses

## **Arithmetic Operators**

| Operator | Description |
| -------- | ----------- |
| +        | Add         |
| -        | Subtract    |
| *        | Multiply    |
| /        | Divide      |
| %        | Modulo      |

## **Bitwise Operators**

| Operator | Description          |
| -------- | -------------------- |
| &        | Bitwise AND          |
| \|       | Bitwise OR           |
| ^        | Bitwise exclusive OR |

## **Comparison Operators**

| Operator | Description                                                  |
| -------- | ------------------------------------------------------------ |
| =        | Equal                                                        |
| >        | Greater than                                                 |
| <        | Less than                                                    |
| >=       | Greater than or equal                                        |
| <=       | Less than or equal                                           |
| <>       | Not equal. **Note:** In some versions of SQL this operator may be written as != |

## **Compound Operators**

| Operator | Description              |
| -------- | ------------------------ |
| +=       | Add equals               |
| -=       | Subtract equals          |
| *=       | Multiply equals          |
| / =      | Divide equals            |
| %=       | Modulo equals            |
| &=       | Bitwise AND equals       |
| ^-=      | Bitwise exclusive equals |
| \|*=     | Bitwise OR equals        |




## **Logical Operators**

| Operator | Description                                                  |
| -------- | ------------------------------------------------------------ |
| ALL      | TRUE if all of the subquery values meet the condition        |
| AND      | TRUE if all the conditions separated by AND is TRUE          |
| ANY      | TRUE if any of the subquery values meet the condition        |
| BETWEEN  | Between a certain range. TRUE if the operand is within the range of comparisons |
| EXISTS   | TRUE if the subquery returns one or more records             |
| IN       | To specify multiple possible values for a column. RUE if the operand is equal to one of a list of expressions |
| LIKE     | Search for a pattern. TRUE if the operand matches a pattern  |
| NOT      | Displays a record if the condition(s) is NOT TRUE            |
| OR       | TRUE if any of the conditions separated by OR is TRUE        |
| SOME     | TRUE if any of the subquery values meet the condition        |

## Complex Clauses

More complex clauses can be constructed by joining numerous `AND` or `OR` logical keywords (ie. num_wheels >= 4 AND doors <= 2). And below are some useful operators that you can use for numerical data (ie. integer or floating point):

| Operator            | Condition                                            | SQL Example                           |
| ------------------- | ---------------------------------------------------- | ------------------------------------- |
| =, !=, < <=, >, >=  | Standard numerical operators                         | col_name **!=** 4                     |
| BETWEEN … AND …     | Number is within range of two values (inclusive)     | col_name **BETWEEN** 1.5 **AND** 10.5 |
| NOT BETWEEN … AND … | Number is not within range of two values (inclusive) | col_name **NOT BETWEEN** 1 **AND** 10 |
| IN (…)              | Number exists in a list                              | col_name **IN** (2, 4, 6)             |
| NOT IN (…)          | Number does not exist in a list                      | col_name **NOT IN** (1, 3, 5)         |

When writing `WHERE` clauses with columns containing text data, SQL supports a number of useful operators to do things like case-insensitive string comparison and wildcard pattern matching. We show a few common text-data specific operators below

| Operator   | Condition                                                    | Example                                                      |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| =          | Case sensitive exact string comparison (_notice the single equals_) | col_name **=** "abc"                                         |
| != or <>   | Case sensitive exact string inequality comparison            | col_name **!=** "abcd"                                       |
| LIKE       | Case insensitive exact string comparison                     | col_name **LIKE** "ABC"                                      |
| NOT LIKE   | Case insensitive exact string inequality comparison          | col_name **NOT LIKE** "ABCD"                                 |
| %          | Used anywhere in a string to match a sequence of zero or more characters (only with LIKE or NOT LIKE) | col_name **LIKE** "%AT%" (matches "AT", "ATTIC", "CAT" or even "BATS") |
| _          | Used anywhere in a string to match a single character (only with LIKE or NOT LIKE) | col_name **LIKE** "AN_" (matches "AND", but not "AN")        |
| IN (…)     | String exists in a list                                      | col_name **IN** ("A", "B", "C")                              |
| NOT IN (…) | String does not exist in a list                              | col_name **NOT IN** ("D", "E", "F")                          |




# References

- [https://sqlbolt.com/lesson/select_queries_with_constraints](https://sqlbolt.com/lesson/select_queries_with_constraints)
- https://sqlbolt.com/lesson/select_queries_with_constraints_pt_2
- [https://www.w3schools.com/sql/sql_operators.asp](https://www.w3schools.com/sql/sql_operators.asp)