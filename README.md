# SQL
Structured Query Language (SQL) is a standard language for storing, manipulating and retrieving data in databases.
## Content

* [1. SQL Fundamentals](01_sql-fundamentals/)
* [2. SQL Database](02_sql-database/)
* [3. SQL Data Manipulation](03_sql-data-manipulation/)
* [4. SQL Data Query](04_sql-data-query/)
* [5. SQL Data Filtering](05_sql-data-filtering/)
* [6. SQL Joins](06_sql-joins/)
* [7. SQL Set Operators](07_sql-set-operators/)
* [8. SQL Functions](08_sql-functions/)
* [10. SQL Common Table Expression (CTE)](10_sql-common-table-expression/)









## General Overview



```mermaid
flowchart LR
SQL["SQL<br/>Structured Query Language"]
SQL --> Fundamentals["SQL<br/>Fundamentals"]
SQL --> Database["SQL<br/>Database"]
SQL --> DataManipulation["SQL<br/>Data Manipulation"]
SQL --> DataQuery["SQL<br/>Data Query"]
SQL --> DataFiltering["SQL<br/>Data Filtering"]
SQL --> Joins["SQL<br/>Joins"]
SQL --> SetOps["SQL<br/>Set Operators"]
SQL --> Functions["SQL<br/>Functions"]
SQL --> Subqueries["SQL<br/>Subqueries"]
SQL --> CTE["SQL<br/>Common Table Expressions (CTE)"]

DataQuery-->QueryElements["SELECT<br/>WHERE<br/>GROUP BY<br/>HAVING"]
Joins-->JoinsElements["INNER JOIN<br/>LEFT JOIN<br/>RIGHT JOIN<br/>FULL JOIN<br/>CROSS JOIN"]
SetOps-->SetOpsElements["UNION<br/>UNION ALL<br/>EXCEPT<br/>INTERSECT"]
Functions-->RowLevelFunctions["Row-Level Functions"]
Functions-->AggrAnalyticalFunctions["Aggregation & Analytical Functions"]
RowLevelFunctions-->RowLevFElm["String Functions<br/>Number Functions<br/>Date & Time Functions<br/>Null Functions<br/>Case Statement"]
AggrAnalyticalFunctions-->AggrAnalyticalFElm["Aggregate Funtions<br/>Window Basics<br/>Window Aggregate Functions<br/>Window Ranking Function<br/>Window Value Function"]


classDef sql fill:#2563eb,color:#fff,stroke:#1e40af,stroke-width:2px
classDef category fill:#7c3aed,color:#fff,stroke:#5b21b6,stroke-width:2px
classDef command fill:#f3f4f6,color:#111,stroke:#6b7280
classDef logic fill:#fef3c7,color:#92400e,stroke:#d97706,stroke-width:2px

class SQL sql
class Fundamentals,Database,DataManipulation,DataQuery,DataFiltering,Joins,SetOps,Functions,Subqueries,CTE category
class DataElements,QueryElements,JoinsElements,SetOpsElements,RowLevelFunctions,AggrAnalyticalFunctions command
class RowLevFElm,AggrAnalyticalFElm logic
```











## SQL Sublanguages

```mermaid
flowchart LR
    SQL["SQL<br/>Structured Query Language"]
SQL --> DDL["DDL<br/>Data Definition"]
SQL --> DML["DML<br/>Data Manipulation"]
SQL --> DQL["DQL<br/>Data Query"]
SQL --> DCL["DCL<br/>Data Control"]
SQL --> TCL["TCL<br/>Transaction Control"]

DDL --> DDL_C["CREATE<br/>ALTER<br/>DROP<br/>TRUNCATE<br/>RENAME"]

DML --> DML_C["INSERT<br/>UPDATE<br/>DELETE<br/>MERGE"]

DQL --> SELECT["SELECT"]

SELECT --> FROM["FROM"]
SELECT --> WHERE["WHERE"]
WHERE --> LOGIC["AND<br/>OR<br/>NOT"]

SELECT --> GROUP["GROUP BY"]
SELECT --> HAVING["HAVING"]
SELECT --> ORDER["ORDER BY"]
SELECT --> DISTINCT["DISTINCT"]
SELECT --> JOIN["JOIN"]

DCL --> DCL_C["GRANT<br/>REVOKE"]

TCL --> TCL_C["COMMIT<br/>ROLLBACK<br/>SAVEPOINT"]

classDef sql fill:#2563eb,color:#fff,stroke:#1e40af,stroke-width:3px
classDef category fill:#7c3aed,color:#fff,stroke:#5b21b6,stroke-width:2px
classDef command fill:#f3f4f6,color:#111,stroke:#6b7280
classDef logic fill:#fef3c7,color:#92400e,stroke:#d97706,stroke-width:2px

class SQL sql
class DDL,DML,DQL,DCL,TCL category
class DDL_C,DML_C,SELECT,FROM,WHERE,GROUP,HAVING,ORDER,DISTINCT,JOIN,DCL_C,TCL_C command
class LOGIC logic
```





# Resources

## Cheatsheets
 * DataQuest - SQL Cheat Sheet | [PDF](cheatsheets/dataquest_sql-cheat-sheet.pdf)  | [Website](https://www.dataquest.io/cheat-sheet/sql-cheat-sheet/) 



## Courses

* Data with Baara - SQL Full Course for Beginners (30 Hours) – From Zero to Hero: https://youtu.be/SSKVgrwhzus





