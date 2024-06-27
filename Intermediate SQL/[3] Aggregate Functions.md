

# Aggregate Functions

### Aggregate functions and data types


| Numerical data only | Various data types | 
| ------------------- | ------------------ |
|AVG()                | COUNT()            | 
|SUM()                | MAX()              | 
|                     | MIN()              |


### Practice with aggregate functions


1
```
-- Query the sum of film durations
SELECT SUM(duration) AS total_duration
FROM films;
```

2
```
-- Calculate the average duration of all films
SELECT AVG(duration) AS average_duration
FROM films;
```

3
```
-- Find the latest release_year
SELECT MAX(release_year) AS latest_year
FROM films;
```

4
```
-- Find the duration of the shortest film
SELECT MIN(duration) AS shortest_film
FROM films;
```

### Combining aggregate functions with WHERE

1
```
-- Calculate the sum of gross from the year 2000 or later
SELECT SUM(gross) AS total_gross
FROM films
WHERE release_year >= 2000;
```

2
```
-- Calculate the average gross of films that start with A
SELECT AVG(gross) AS avg_gross_A
FROM films
WHERE title LIKE 'A%';
```

3
```
-- Calculate the lowest gross film in 1994
SELECT MIN(gross) AS lowest_gross
FROM films
WHERE release_year = 1994;
```

4
```
-- Calculate the highest gross film released between 2000-2012
SELECT MAX(gross) AS highest_gross
FROM films
WHERE release_year BETWEEN 2000 AND 2012;
```

### Using ROUND()

```
-- Round the average number of facebook_likes to one decimal place
SELECT ROUND(AVG(facebook_likes), 1) AS avg_facebook_likes
FROM reviews;
```

### ROUND() with a negative parameter

```
-- Calculate the average budget rounded to the thousands
SELECT ROUND(AVG(budget) / 1000) * 1000 AS avg_budget_thousands
FROM films;
```

### Using arithmetic
 0

### Aliasing with functions

1
```
-- Calculate the title and duration_hours from films
SELECT title, duration / 60.0 AS duration_hours
FROM films;
```

2
```
-- Calculate the percentage of people who are no longer alive
SELECT COUNT(CASE WHEN deathdate IS NOT NULL THEN 1 END) * 100.0 / COUNT(*) AS percentage_dead
FROM people;
```

3
```
-- Find the number of decades in the films table
SELECT (MAX(release_year) - MIN(release_year)) / 10.0 AS number_of_decades
FROM films;
```

### Rounding results

```
-- Round duration_hours to two decimal places
SELECT title, ROUND(duration / 60.0, 2) AS duration_hours
FROM films;
```
