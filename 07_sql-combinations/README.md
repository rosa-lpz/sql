#  SQL COMBINATIONS

* [UNION ALL](union-all.md)



| Clause | How to use| Explained   | 
|------------|-------------|------------|
| Union | SELECT productName FROM products WHERE productLine = 'Classic Cars' **UNION** SELECT productName FROM products WHERE productLine = 'Vintage Cars';|Combines the product names from Classic Cars and Vintage Cars product lines, removing duplicates.|
| Union All | SELECT productName FROM products WHERE productLine = 'Classic Cars' **UNION ALL** SELECT productName FROM products WHERE productLine = 'Vintage Cars';|Combines the product names from Classic Cars and Vintage Cars product lines, removing duplicates.|
| Except | SELECT productCode, productName FROM products **EXCEPT** SELECT productCode, productName FROM products WHERE productLine = 'Classic Cars';|Returns products EXCEPT the Classic Cars product line, demonstrating how EXCEPT removes rows from the first result that appear in the second result.|
|Intersect|SELECT customerNumber, customerName FROM customers WHERE country = 'USA' **INTERSECT** SELECT customerNumber, customerName FROM customers WHERE creditLimit > 100000;|Returns customers who are both located in the USA AND have a credit limit over 100,000. This query demonstrates how INTERSECT finds common rows between two result sets.|


# REFERENCES
 * DataQuest - SQL Cheat Sheet | [PDF](cheatsheets/dataquest_sql-cheat-sheet.pdf)  | [Website](https://www.dataquest.io/cheat-sheet/sql-cheat-sheet/) 