﻿

# Filtering Records

### Filtering Records

```
Answer: Films released after the year 2000.
```

### Using WHERE with numbers

1
```
-- Select film_ids and imdb_score with an imdb_score over 7.0
SELECT film_id, imdb_score
FROM reviews
WHERE imdb_score > 7.0;
```

2
```
-- Select film_ids and facebook_likes for ten records with less than 1000 likes 
SELECT film_id, facebook_likes
FROM reviews
WHERE facebook_likes < 1000
LIMIT 10;
```

3
```
-- Count the records with at least 100,000 votes
SELECT COUNT(*) AS films_over_100K_votes
FROM reviews
WHERE num_votes >= 100000;
```

### Using WHERE with text

```
SELECT COUNT(*) AS count_spanish
FROM films
WHERE language = 'Spanish';
```

### Using AND

1
```
-- Select the title and release_year for all German-language films released before 2000
SELECT title, release_year
FROM films
WHERE language = 'German' 
  AND release_year < 2000;
```

2
```
-- Update the query to see all German-language films released after 2000
SELECT title, release_year
FROM films
WHERE release_year > 2000
	AND language = 'German';
```

3
```
-- Select all records for German-language films released after 2000 and before 2010
SELECT *
FROM films
WHERE language = 'German'
  AND release_year > 2000
  AND release_year < 2010;
```

### Using OR

1
```
-- Find the title and year of films from the 1990 or 1999
SELECT title, release_year
FROM films
WHERE release_year = 1990 OR release_year = 1999;
```

2
```
SELECT title, release_year
FROM films
WHERE (release_year = 1990 OR release_year = 1999)
-- Add a filter to see only English or Spanish-language films
	AND language IN ('English', 'Spanish');
```

3
```
SELECT title, release_year
FROM films
WHERE (release_year = 1990 OR release_year = 1999)
	AND (language = 'English' OR language = 'Spanish')
-- Filter films with more than $2,000,000 gross
	AND gross > 2000000;
```

### Using BETWEEN

1
```
-- Select the title and release_year for films released between 1990 and 2000
SELECT title, release_year
FROM films
WHERE release_year BETWEEN 1990 AND 2000;
```


2
```
SELECT title, release_year
FROM films
WHERE release_year BETWEEN 1990 AND 2000
-- Narrow down your query to films with budgets > $100 million
	AND budget > 100000000;
```

3
```
SELECT title, release_year
FROM films
WHERE release_year BETWEEN 1990 AND 2000
	AND budget > 100000000
-- Restrict the query to only Spanish-language films
	AND language = 'Spanish';
```

4
```
SELECT title, release_year
FROM films
WHERE release_year BETWEEN 1990 AND 2000
	AND budget > 100000000
-- Amend the query to include Spanish or French-language films
	AND (language = 'Spanish' OR language = 'French');
```

### LIKE and NOT LIKE

1
```
-- Select the names that start with B
SELECT name
FROM people
WHERE name LIKE 'B%';
```

2
```
SELECT name
FROM people
-- Select the names that have r as the second letter
WHERE name LIKE '_r%';
```

3
```
SELECT name
FROM people
-- Select names that don't start with A
WHERE name NOT LIKE 'A%';
```

### WHERE IN

1
```
-- Find the title and release_year for all films over two hours in length released in 1990 and 2000
SELECT title, release_year
FROM films
WHERE (release_year = 1990 OR release_year = 2000)
  AND duration > 120;
```

2
```
-- Find the title and language of all films in English, Spanish, and French
SELECT title, language
FROM films
WHERE language IN ('English', 'Spanish', 'French');
```

3
```
-- Find the title, certification, and language all films certified NC-17 or R that are in English, Italian, or Greek
SELECT title, certification, language
FROM films
WHERE certification IN ('NC-17', 'R')
  AND language IN ('English', 'Italian', 'Greek');
```

### Combining filtering and selecting

```
-- Count the unique titles
SELECT COUNT(DISTINCT title) AS nineties_english_films_for_teens
FROM films
-- Filter to release_years to between 1990 and 1999
WHERE release_year BETWEEN 1990 AND 1999
-- Filter to English-language films
	AND language = 'English'
-- Narrow it down to G, PG, and PG-13 certifications
	AND certification IN ('G', 'PG', 'PG-13');
```

### What does NULL mean?

```
Answer: A missing Value.
```

### Practice with NULLs

1
```
-- List all film titles with missing budgets
SELECT title AS no_budget_info
FROM films
WHERE budget IS NULL;
```

2
```
-- Count the number of films we have language data for
SELECT COUNT(*) AS count_language_known
FROM films
WHERE language IS NOT NULL;
```
