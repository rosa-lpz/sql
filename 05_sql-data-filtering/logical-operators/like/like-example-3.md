

# SQL - Like operator

## Example 3 - Movies

| Id   | Title           | Director       | Year | Length_minutes |
| ---- | --------------- | -------------- | ---- | -------------- |
| 1    | Toy Story       | John Lasseter  | 1995 | 81             |
| 2    | A Bug's Life    | John Lasseter  | 1998 | 95             |
| 3    | Toy Story 2     | John Lasseter  | 1999 | 93             |
| 4    | Monsters, Inc.  | Pete Docter    | 2001 | 92             |
| 5    | Finding Nemo    | Andrew Stanton | 2003 | 107            |
| 6    | The Incredibles | Brad Bird      | 2004 | 116            |
| 7    | Cars            | John Lasseter  | 2006 | 117            |
| 8    | Ratatouille     | Brad Bird      | 2007 | 115            |
| 9    | WALL-E          | Andrew Stanton | 2008 | 104            |
| 10   | Up              | Pete Docter    | 2009 | 101            |
| 11   | Toy Story 3     | Lee Unkrich    | 2010 | 103            |
| 12   | Cars 2          | John Lasseter  | 2011 | 120            |



### Find all the Toy Story movies

```SQL
SELECT * FROM movies
WHERE Title LIKE '%Toy Story%';
```

| Id   | Title       | Director      | Year | Length_minutes |
| ---- | ----------- | ------------- | ---- | -------------- |
| 1    | Toy Story   | John Lasseter | 1995 | 81             |
| 3    | Toy Story 2 | John Lasseter | 1999 | 93             |
| 11   | Toy Story 3 | Lee Unkrich   | 2010 | 103            |



### Find all the movies directed by John Lasseter

```SQL
SELECT * FROM movies
WHERE Director = 'John Lasseter';
```

| Id   | Title        | Director      | Year | Length_minutes |
| ---- | ------------ | ------------- | ---- | -------------- |
| 1    | Toy Story    | John Lasseter | 1995 | 81             |
| 2    | A Bug's Life | John Lasseter | 1998 | 95             |
| 3    | Toy Story 2  | John Lasseter | 1999 | 93             |
| 7    | Cars         | John Lasseter | 2006 | 117            |
| 12   | Cars 2       | John Lasseter | 2011 | 120            |





### Find all the movies (and director) not directed by John Lasseter

```SQL
SELECT * FROM movies
WHERE Director != 'John Lasseter';
```

| Id   | Title               | Director       | Year | Length_minutes |
| ---- | ------------------- | -------------- | ---- | -------------- |
| 4    | Monsters, Inc.      | Pete Docter    | 2001 | 92             |
| 5    | Finding Nemo        | Andrew Stanton | 2003 | 107            |
| 6    | The Incredibles     | Brad Bird      | 2004 | 116            |
| 8    | Ratatouille         | Brad Bird      | 2007 | 115            |
| 9    | WALL-E              | Andrew Stanton | 2008 | 104            |
| 10   | Up                  | Pete Docter    | 2009 | 101            |
| 11   | Toy Story 3         | Lee Unkrich    | 2010 | 103            |
| 13   | Brave               | Brenda Chapman | 2012 | 102            |
| 14   | Monsters University | Dan Scanlon    | 2013 | 110            |
| 87   | WALL-G              | Brenda Chapman | 2042 | 97             |



### Find all the WALL-* movies

```SQL
SELECT * FROM Movies
WHERE Title LIKE 'WALL-%';
```



| Id   | Title  | Director       | Year | Length_minutes |
| ---- | ------ | -------------- | ---- | -------------- |
| 9    | WALL-E | Andrew Stanton | 2008 | 104            |
| 87   | WALL-G | Brenda Chapman | 2042 | 97             |


# 