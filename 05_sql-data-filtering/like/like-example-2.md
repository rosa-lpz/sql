# SQL - Like operator

## Example 2 - Employee

| EmpId | FirstName | LastName  | Email                                           | Salary | HireDate   |
| ----- | --------- | --------- | ----------------------------------------------- | ------ | ---------- |
| 1     | 'John'    | 'King'    | '[john.king@abc.com](mailto:john.king@abc.com)' | 33000  | 2018-07-25 |
| 2     | 'James'   | 'Bond'    |                                                 |        | 2018-07-29 |
| 3     | 'Neena'   | 'Kochhar' | '[neena@test.com](mailto:neena@test.com)'       | 17000  | 2018-08-22 |
| 4     | 'Lex'     | 'De Haan' | '[lex@test.com](mailto:lex@test.com)'           | 15000  | 2018-09-8  |
| 5     | 'Amit'    | 'Patel'   |                                                 | 18000  | 2019-01-25 |
| 6     | 'Abdul'   | 'Kalam'   | '[abdul@test.com](mailto:abdul@test.com)'       | 25000  | 2020-07-14 |



#### **Three characters word - Second position**

The bellow query will return records whose `FirstName` value contains three letters and 'e' at the second position. The '_' indicates any one character.

```SQL
SELECT *
FROM Employee
WHERE FirstName LIKE '_e_';
```

**Output**

| EmpId | FirstName | LastName  | Email                                 | Salary | HireDate  |
| ----- | --------- | --------- | ------------------------------------- | ------ | --------- |
| 4     | 'Lex'     | 'De Haan' | '[lex@test.com](mailto:lex@test.com)' | 15000  | 2018-09-8 |



#### [] pattern

The bellow query uses the [] wildcard pattern.

```SQL
SELECT *
FROM Employee
WHERE FirstName LIKE 'A[i,m,t,y,s]';
```

**Output**

| EmpId | FirstName | LastName | Email | Salary | HireDate   |
| ----- | --------- | -------- | ----- | ------ | ---------- |
| 5     | 'Amit'    | 'Patel'  |       | 18000  | 2019-01-25 |

Note: The **[]** matches any single character within the specified range in the [].

- E.g. 'A[e,l,p]' will match 'Apple', 'Aelp', 'Alep', 'Aple', etc.

