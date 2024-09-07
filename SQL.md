# Multi-table queries with JOINs



<table>
  <tr>
    <td>

<h2 style="text-align: center;">Table: Movies</h2>

| Id | Title                | Director       | Year | Length_minutes |
|----|----------------------|----------------|------|----------------|
| 1  | Toy Story            | John Lasseter  | 1995 | 81             |
| 2  | A Bug's Life         | John Lasseter  | 1998 | 95             |
| 3  | Toy Story 2          | John Lasseter  | 1999 | 93             |
| 4  | Monsters, Inc.       | Pete Docter    | 2001 | 92             |
| 5  | Finding Nemo         | Andrew Stanton | 2003 | 107            |
| 6  | The Incredibles      | Brad Bird      | 2004 | 116            |
| 7  | Cars                 | John Lasseter  | 2006 | 117            |
| 8  | Ratatouille          | Brad Bird      | 2007 | 115            |
| 9  | WALL-E               | Andrew Stanton | 2008 | 104            |
| 10 | Up                   | Pete Docter    | 2009 | 101            |
| 11 | Toy Story 3          | Lee Unkrich    | 2010 | 103            |
| 12 | Cars 2               | John Lasseter  | 2011 | 120            |
| 13 | Brave                | Brenda Chapman | 2012 | 102            |
| 14 | Monsters University  | Dan Scanlon    | 2013 | 110            |

  </td>
    <td style="width: 50px;"></td>
    <td>

<h2 style="text-align: center;">Table: Boxoffice</h2>

| Movie_id | Rating | Domestic_sales | International_sales |
|----------|--------|----------------|----------------------|
| 5        | 8.2    | 380,843,261    | 555,900,000          |
| 14       | 7.4    | 268,492,764    | 475,066,843          |
| 8        | 8.0    | 206,445,654    | 417,277,164          |
| 12       | 6.4    | 191,452,396    | 368,400,000          |
| 3        | 7.9    | 245,852,179    | 239,163,000          |
| 6        | 8.0    | 261,441,092    | 370,001,000          |
| 9        | 8.5    | 223,808,164    | 297,503,696          |
| 11       | 8.4    | 415,004,880    | 648,167,031          |
| 1        | 8.3    | 191,796,233    | 170,162,503          |
| 7        | 7.2    | 244,082,982    | 217,900,167          |
| 10       | 8.3    | 293,004,164    | 438,338,580          |
| 4        | 8.1    | 289,916,256    | 272,900,000          |
| 2        | 7.2    | 162,798,565    | 200,600,000          |
| 13       | 7.2    | 237,283,207    | 301,700,000          |

  </td>
  </tr>
</table>

## 1.Find the domestic and international sales for each movie
```
SELECT title, domestic_sales, international_sales 
FROM movies
  JOIN boxoffice
    ON movies.id = boxoffice.movie_id;
```
## 2.Show the sales numbers for each movie that did better internationally rather than domestically
```
SELECT title, domestic_sales, international_sales
FROM movies
  JOIN boxoffice
    ON movies.id = boxoffice.movie_id
WHERE international_sales > domestic_sales;
```
## 3.List all the movies by their ratings in descending order
```
SELECT title, rating
FROM movies
  JOIN boxoffice
    ON movies.id = boxoffice.movie_id
ORDER BY rating DESC;
```
## 4.List all movies and their combined sales in millions of dollars
```
SELECT title, (domestic_sales + international_sales) AS gross_sales_millions
FROM movies
  JOIN boxoffice
    ON movies.id = boxoffice.movie_id;
```
## 5.List all movies and their ratings in percent
```
SELECT title, rating * 10 AS rating_percent
FROM movies
  JOIN boxoffice
    ON movies.id = boxoffice.movie_id;
```
## 6.List all movies that were released on even number years
```
SELECT title, year
FROM movies
WHERE year % 2 = 0;
```
## 7.Find the number of movies each director has directed 
```
SELECT director, COUNT(id) as Num_movies_directed
FROM movies
GROUP BY director;
```
## 8.Find the total domestic and international sales that can be attributed to each director
```
SELECT director, SUM(domestic_sales + international_sales) as Cumulative_sales_from_all_movies
FROM movies
    INNER JOIN boxoffice
        ON movies.id = boxoffice.movie_id
GROUP BY director;
```

# Outer Joins
<table>
  <tr>
    <td>

<h2 style="text-align: center;">Table: Buildings (Read-Only)</h2>

| Building_name | Capacity |
|---------------|----------|
| 1e            | 24       |
| 1w            | 32       |
| 2e            | 16       |
| 2w            | 20       |

  </td>
    <td style="width: 50px;"></td>
    <td>

<h2 style="text-align: center;">Table: Employees</h2>

| Role    | Name         | Building | Years_employed |
|---------|--------------|----------|----------------|
| Engineer| Becky A.     | 1e       | 4              |
| Engineer| Dan B.       | 1e       | 2              |
| Engineer| Sharon F.    | 1e       | 6              |
| Engineer| Dan M.       | 1e       | 4              |
| Engineer| Malcom S.    | 1e       | 1              |
| Artist  | Tylar S.     | 2w       | 2              |
| Artist  | Sherman D.   | 2w       | 8              |
| Artist  | Jakob J.     | 2w       | 6              |
| Artist  | Lillia A.    | 2w       | 7              |
| Artist  | Brandon J.   | 2w       | 7              |
| Manager | Scott K.     | 1e       | 9              |
| Manager | Shirlee M.   | 1e       | 3              |
| Manager | Daria O.     | 2w       | 6              |

  </td>
  </tr>
</table>

## 1.Find the list of all buildings that have employees
```
SELECT DISTINCT building FROM employees;
```
## 2.Find the list of all buildings and their capacity
```
SELECT * FROM buildings;
```
## 3.List all buildings and the distinct employee roles in each building (including empty buildings)
```
SELECT DISTINCT building_name, role 
FROM buildings 
  LEFT JOIN employees
    ON building_name = building;
```
## 4.Find the name and role of all employees who have not been assigned to a building
```
SELECT name, role FROM employees
WHERE building IS NULL;
```
## 5.Find the names of the buildings that hold no employees
```
SELECT DISTINCT building_name
FROM buildings 
  LEFT JOIN employees
    ON building_name = building
WHERE role IS NULL;
```
# Table: Employees

| Role    | Name         | Building | Years_employed |
|---------|--------------|----------|----------------|
| Engineer| Becky A.     | 1e       | 4              |
| Engineer| Dan B.       | 1e       | 2              |
| Engineer| Sharon F.    | 1e       | 6              |
| Engineer| Dan M.       | 1e       | 4              |
| Engineer| Malcom S.    | 1e       | 1              |
| Artist  | Tylar S.     | 2w       | 2              |
| Artist  | Sherman D.   | 2w       | 8              |
| Artist  | Jakob J.     | 2w       | 6              |
| Artist  | Lillia A.    | 2w       | 7              |
| Artist  | Brandon J.   | 2w       | 7              |
| Manager | Scott K.     | 1e       | 9              |
| Manager | Shirlee M.   | 1e       | 3              |
| Manager | Daria O.     | 2w       | 6              |


## 1.Find the longest time that an employee has been at the studio
```
SELECT MAX(years_employed) as Max_years_employed
FROM employees;
```
## 2.For each role, find the average number of years employed by employees in that role
```
SELECT role, AVG(years_employed) as Average_years_employed
FROM employees
GROUP BY role;
```
## 3.Find the total number of employee years worked in each building
```
SELECT building, SUM(years_employed) as Total_years_employed
FROM employees
GROUP BY building;
```
## 4.Find the number of Artists in the studio (without a HAVING clause)
```
SELECT role, COUNT(*) as Number_of_artists
FROM employees
WHERE role = "Artist";
```
## 5.Find the number of Employees of each role in the studio
```
SELECT role, COUNT(*)
FROM employees
GROUP BY role;
```
## 6.Find the total number of years employed by all Engineers
```
SELECT role, SUM(years_employed)
FROM employees
GROUP BY role
HAVING role = "Engineer";
```



