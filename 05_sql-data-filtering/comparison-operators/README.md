# Comparison Operators



| Operator | Description                                                  |
| -------- | ------------------------------------------------------------ |
| =        | Equal                                                        |
| >        | Greater than                                                 |
| <        | Less than                                                    |
| >=       | Greater than or equal                                        |
| <=       | Less than or equal                                           |
| <>       | Not equal. **Note:** In some versions of SQL this operator may be written as != |

## 

## Examples

### Countries, population and gdp

**Database**

| name        | continent | area    | population | gdp          |
| :---------- | :-------- | :------ | :--------- | :----------- |
| Afghanistan | Asia      | 652230  | 25500100   | 20343000000  |
| Albania     | Europe    | 28748   | 2831741    | 12960000000  |
| Algeria     | Africa    | 2381741 | 37100000   | 188681000000 |
| Andorra     | Europe    | 468     | 78115      | 3712000000   |
| Angola      | Africa    | 1246700 | 20609294   | 100990000000 |



**Large Countries**

How to use WHERE to filter records. Show the name for the countries that have a population of at least 200 million. 200 million is 200000000, there are eight zeros.

```SQL
SELECT name FROM world
WHERE population >=200000000;
```

Output

| name          |
| ------------- |
| Brazil        |
| China         |
| India         |
| Indonesia     |
| United States |



**Per capita GDP**

Give the `name` and the **per capita GDP** for those countries with a `population` of at least 200 million.

```SQL
SELECT name, gdp/population AS 'per capita GDP' FROM world
WHERE population >=200000000;
```

Output

| name          | per capita GDP     |
| ------------- | ------------------ |
| Brazil        | 11115.264751422625 |
| China         | 6121.710598592322  |
| India         | 1504.793124478397  |
| Indonesia     | 3482.020488188676  |
| United States | 51032.29454636844  |



**South America In millions**

```SQL
SELECT name, population/1000000 FROM world
WHERE continent='South America';
```

Output

| name                             |           |
| -------------------------------- | --------- |
| Argentina                        | 42.6695   |
| Bolivia                          | 10.027254 |
| Brazil                           | 202.794   |
| Chile                            | 17.773    |
| Colombia                         | 47.662    |
| Ecuador                          | 15.7742   |
| Guyana                           | 0.784894  |
| Paraguay                         | 6.783374  |
| Peru                             | 30.475144 |
| Saint Vincent and the Grenadines | 0.109     |
| Suriname                         | 0.534189  |
| Uruguay                          | 3.286314  |
| Venezuela                        | 28.946101 |



**France, Germany, Italy**

Show the `name` and `population` for France, Germany, Italy

```SQL
SELECT name, population FROM world
WHERE name='France' OR name='Germany'OR name='Italy';
```

Output

| name    | population |
| ------- | ---------- |
| France  | 65906000   |
| Germany | 80716000   |
| Italy   | 60782668   |



# References

- https://sqlbolt.com/lesson/select_queries_with_constraints

- https://sqlbolt.com/lesson/select_queries_with_constraints_pt_2

- https://www.w3schools.com/sql/sql_operators.asp

  

