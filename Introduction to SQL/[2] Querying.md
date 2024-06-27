# Querying

### SQL strengths

```
Answer: Large amounts of data about many different but related areas of a business are housed in a relational database.
```

### Developing SQL style

|                      Make suggestion                   |   Don't make suggestion             | 
| -------------------------------------------------------| ----------------------------------- |
|Captalize ``` From ```                                  | Captalize  ``` patrons ```          | 
|Add a ``` ; ``` at the end of the query                 | All code should be on just one line | 
| Make ``` CARD_NUM ``` and ``` TOTAL_FINE ``` lowercase | Make ``` SElECT ``` lowercase       |


### Querying the books table

1
```
-- Return all titles from the books table
SELECT title
FROM books;
```
2
```
-- Select title and author from the books table
SELECT title, author
FROM books;
```
3
```
-- Select all fields from the books table
SELECT *
FROM books;
```

### Making queries DISTINCT

1
```
-- Select unique authors from the books table
SELECT DISTINCT author
FROM books;
```

2
```
-- Select unique authors and genre combinations from the books table
SELECT DISTINCT author, genre
FROM books;
```

### Aliasing

```
-- Alias author so that it becomes unique_author
SELECT DISTINCT author AS unique_author
FROM books;
```

### VIEWing your query

1
```
-- Save the results of this query as a view called library_authors
CREATE VIEW library_authors AS
SELECT DISTINCT author AS unique_author
FROM books;
```
2
```
-- Your code to create the view:
CREATE VIEW library_authors AS
SELECT DISTINCT author AS unique_author
FROM books;

-- Select all columns from library_authors
SELECT *
FROM library_authors;
```

### Comparing flavors

|                      PostgreSQL                    |           SQL Server                  | 
| ---------------------------------------------------| ------------------------------------- |
| Free and open source                               | Has both free and enterprise versions | 
| Developed at the University of California, Berkeley| Queried using T-SQL                   | 
| Research funds provided by DARPA                   | Created by Microsoft                  |

### Limiting results

```
-- Select the first 10 genres from books using PostgreSQL
SELECT genre
FROM books
LIMIT 10;
```

### Translating between flavors

```
Answer: Remove LIMIT statement and add TOP(10) after SELECT.
```


