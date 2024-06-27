

# Subqueries

### Multiple WHERE clauses

```
SELECT *
FROM economics2019
WHERE code in
(SELECT code
FROM economics2015
WHERE gross_savings < 22.5)
```

### Semi join

1
```
-- Select country code for countries in the Middle East
SELECT code
FROM countries
WHERE region = 'Middle East';
```

2
```
-- Select unique language names
SELECT DISTINCT name
FROM languages
-- Order by the name of the language
ORDER BY name ASC;
```

3
```
SELECT DISTINCT name
FROM languages
-- Add syntax to use bracketed subquery below as a filter
WHERE code IN
    (SELECT code
    FROM countries
    WHERE region = 'Middle East')
ORDER BY name;
```

### Diagnosing problems using anti join

1
```
-- Select code and name of countries from Oceania
SELECT code, name
FROM countries
WHERE continent = 'Oceania';
```

2
```
SELECT code, name
FROM countries
WHERE continent = 'Oceania'
  AND code NOT IN
    (SELECT code
    FROM currencies);
```

### Subquery inside WHERE

1
```
-- Select average life_expectancy from the populations table
SELECT AVG(life_expectancy)
FROM populations
-- Filter for the year 2015
WHERE year = 2015;
```

2
```
SELECT *
FROM populations
-- Filter for only those populations where life expectancy is 1.15 times higher than average
WHERE life_expectancy > 1.15 *
  (SELECT AVG(life_expectancy)
   FROM populations
   WHERE year = 2015) 
    AND year = 2015;
```

### WHERE do people live?

```
-- Select relevant fields from cities table
SELECT name, country_code, urbanarea_pop
FROM cities
-- Filter using a subquery on the countries table
WHERE name IN
  (SELECT capital
   FROM countries)
ORDER BY urbanarea_pop DESC;
```

#### Subquery inside SELECT

1
```
-- Find top nine countries with the most cities
SELECT countries.name AS country, COUNT(*) AS cities_num
FROM countries
LEFT JOIN cities
ON countries.code = cities.country_code
GROUP BY country
-- Order by count of cities as cities_num
ORDER BY cities_num DESC, country
LIMIT 9;
```

2
```
SELECT countries.name AS country,
-- Subquery that provides the count of cities   
  (SELECT COUNT(*)
   FROM cities
   WHERE cities.country_code = countries.code) AS cities_num
FROM countries
ORDER BY cities_num DESC, country
LIMIT 9;
```

### Subquery inside FROM

1
```
-- Select code, and language count as lang_num
SELECT code,
       COUNT(*) AS lang_num
FROM languages
GROUP BY code;
```

2
```
-- Select local_name and lang_num from appropriate tables
SELECT local_name, lang_num
FROM countries,
  (SELECT code, COUNT(*) AS lang_num
  FROM languages
  GROUP BY code) AS sub
-- Where codes match
WHERE countries.code = sub.code
ORDER BY lang_num DESC;
```

### Subquery challenge

```
-- Select relevant fields
SELECT code, inflation_rate, unemployment_rate
FROM economies
WHERE year = 2015 
  AND code NOT IN
-- Subquery returning country codes filtered on gov_form
	(SELECT code
    FROM countries
    WHERE gov_form LIKE '%Republic%'
       OR gov_form LIKE '%Monarchy%')
ORDER BY inflation_rate;
```

### Final challenge

```
-- Select fields from cities
SELECT 
    name,
    country_code,
    city_proper_pop,
    metroarea_pop,
    city_proper_pop / metroarea_pop * 100 AS city_perc
FROM 
    cities
-- Use subquery to filter city name
WHERE 
    name IN (
        SELECT capital
        FROM countries
        WHERE continent = 'Europe'
           OR continent LIKE '%America'
    )
-- Add filter condition such that metroarea_pop does not have null values
    AND metroarea_pop IS NOT NULL
-- Sort and limit the result
ORDER BY 
    city_perc DESC
LIMIT 10;
```
