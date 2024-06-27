

# Selecting Data

### Learning to COUNT()

```
Answer: The number of records containing a film_id.
```


### Practice with COUNT()

1
```
-- Count the number of records in the people table
SELECT COUNT(*) AS count_records
FROM people;
```

2
```
-- Count the number of birthdates in the people table
SELECT COUNT(birthdate) AS count_birthdate
FROM people;
```

3
```
-- Count the records for languages and countries represented in the films table
SELECT 
    COUNT(language) AS count_languages,
    COUNT(country) AS count_countries
FROM films;
```

### SELECT DISTINCT

1
```
-- Return the unique countries from the films table
SELECT DISTINCT country
FROM films;
```

2
```
-- Count the distinct countries from the films table
SELECT COUNT(DISTINCT country) AS count_distinct_countries
FROM films;
```

### Order of execution

```
FROM
SELECT
LIMIT
```

### Debugging errors
1
```
-- Debug this code
SELECT certification
FROM films
LIMIT 5;
```

2
```
-- Debug this code
SELECT film_Id , Imdb_score , num_votes
FROM reviews;
```

3
```
-- Debug this code
SELECT COUNT(birthdate) AS count_birthdays
FROM people;
```

### SQL best practices


|                    Best Practice                  |             Poor Practice               | 
| --------------------------------------------------| --------------------------------------- |
|Use underscores in field names rather than spaces  | Write the query on one line             | 
|End queries with a semicolon                       | Write lots of queries with no semicolon | 
| Capitalize keywords                               | Don't capitalize keywords               |

### Formatting

```
-- Rewrite this query
SELECT person_id, role 
FROM roles 
LIMIT 10;
```

### Non-standard fields
```
Answer:"facebook likes"
```


