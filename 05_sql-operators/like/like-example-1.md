# SQL - Like operator

## Example 1 - Customers

he table below shows the complete "Customers" table from the Northwind sample database:

| CustomerID | CustomerName                       | ContactName        | Address                       | City        | PostalCode | Country |
| :--------- | :--------------------------------- | :----------------- | :---------------------------- | :---------- | :--------- | :------ |
| 1          | Alfreds Futterkiste                | Maria Anders       | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo       | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno     | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy       | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |
| 5          | Berglunds snabbköp                 | Christina Berglund | Berguvsvägen 8                | Luleå       | S-958 22   | Sweden  |
| 6          | Blauer See Delikatessen            | Hanna Moos         | Forsterstr. 57                | Mannheim    | 68306      | Germany |
| 7          | Blondel père et fils               | Frédérique Citeaux | 24, place Kléber              | Strasbourg  | 67000      | France  |
| 8          | Bólido Comidas preparadas          | Martín Sommer      | C/ Araquil, 67                | Madrid      | 28023      | Spain   |
| 9          | Bon app'                           | Laurence Lebihans  | 12, rue des Bouchers          | Marseille   | 13008      | France  |
| 10         | Bottom-Dollar Marketse             | Elizabeth Lincoln  | 23 Tsawassen Blvd.            | Tsawassen   | T2F 8M4    | Canada  |



#### **Starting with "a"**

The following SQL statement selects all customers with a CustomerName starting with "a":

```
SELECT * FROM Customers
WHERE CustomerName LIKE 'a%';
```

Output

umber of Records: 4

| CustomerID | CustomerName                       | ContactName    | Address                       | City        | PostalCode | Country |
| :--------- | :--------------------------------- | :------------- | :---------------------------- | :---------- | :--------- | :------ |
| 1          | Alfreds Futterkiste                | Maria Anders   | Obere Str. 57                 | Berlin      | 12209      | Germany |
| 2          | Ana Trujillo Emparedados y helados | Ana Trujillo   | Avda. de la Constitución 2222 | México D.F. | 05021      | Mexico  |
| 3          | Antonio Moreno Taquería            | Antonio Moreno | Mataderos 2312                | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn                    | Thomas Hardy   | 120 Hanover Sq.               | London      | WA1 1DP    | UK      |



#### **Ending with "a"**

The following SQL statement selects all customers with a CustomerName starting with "a":

```
SELECT * FROM Customers
WHERE CustomerName LIKE '%a';
```

Output

Number of Records: 7

| CustomerID | CustomerName               | ContactName       | Address                   | City           | PostalCode | Country |
| :--------- | :------------------------- | :---------------- | :------------------------ | :------------- | :--------- | :------ |
| 3          | Antonio Moreno Taquería    | Antonio Moreno    | Mataderos 2312            | México D.F.    | 05023      | Mexico  |
| 13         | Centro comercial Moctezuma | Francisco Chang   | Sierras de Granada 9993   | México D.F.    | 05022      | Mexico  |
| 30         | Godos Cocina Típica        | José Pedro Freyre | C/ Romero, 33             | Sevilla        | 41101      | Spain   |
| 61         | Que Delícia                | Bernardo Batista  | Rua da Panificadora, 12   | Rio de Janeiro | 02389-673  | Brazil  |
| 62         | Queen Cozinha              | Lúcia Carvalho    | Alameda dos Canàrios, 891 | São Paulo      | 05487-020  | Brazil  |
| 88         | Wellington Importadora     | Paula Parente     | Rua do Mercado, 12        | Resende        | 08737-363  | Brazil  |
| 90         | Wilman Kala                | Matti Karttunen   | Keskuskatu 45             | Helsinki       | 21240      | Finland |



#### "or" in any position

The following SQL statement selects all customers with a CustomerName that have "or" in any position:

```SQL
SELECT * FROM Customers
WHERE CustomerName LIKE '%or%';
```

Output

Number of Records: 11

| CustomerID | CustomerName               | ContactName    | Address                        | City        | PostalCode | Country |
| :--------- | :------------------------- | :------------- | :----------------------------- | :---------- | :--------- | :------ |
| 3          | Antonio Moreno Taquería    | Antonio Moreno | Mataderos 2312                 | México D.F. | 05023      | Mexico  |
| 4          | Around the Horn            | Thomas Hardy   | 120 Hanover Sq.                | London      | WA1 1DP    | UK      |
| 36         | Hungry Coyote Import Store | Yoshi Latimer  | City Center Plaza 516 Main St. | Elgin       | 97827      | USA     |
| 40         | La corne d'abondance       | Daniel Tonini  | 67, avenue de l'Europe         | Versailles  | 78000      | France  |



#### "r" in the second position

The following SQL statement selects all customers with a CustomerName that have "r" in the second position:

```SQL
SELECT * FROM Customers
WHERE CustomerName LIKE '_r%';
```



