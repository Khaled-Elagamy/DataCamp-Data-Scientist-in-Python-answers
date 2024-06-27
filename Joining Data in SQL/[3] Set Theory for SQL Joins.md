
# Set Theory for SQL Joins

### UNION vs. UNION ALL

1- A SQL error, because languages and currencies do not have the same number of fields

2- An unordered list of each country code in languages and currencies, including duplicates

3- A SQL error, because code and curr_id are not of the same data type

### Comparing global economies

```
-- Select all fields from economies2015
SELECT * 
FROM economies2015   
-- Set operation
UNION
-- Select all fields from economies2019
SELECT * 
FROM economies2019
ORDER BY code, year;
```

### Comparing two set operations

1
```
-- Query that determines all pairs of code and year from economies and populations, without duplicates
SELECT code, year
FROM economies
UNION
SELECT country_code, year
FROM populations
ORDER BY code, year;
```

2
```
SELECT code, year
FROM economies
-- Set theory clause
UNION ALL
SELECT country_code, year
FROM populations
ORDER BY code, year;
```

### INTERSECT

```
-- Return all cities with the same name as a country
SELECT name
FROM cities
INTERSECT
SELECT name
FROM countries;
```


### Review UNION and INTERSECT

INTERSECT: returns only records appearing in both tables



### You've got it, EXCEPT...

```
-- Return all cities that do not have the same name as a country
SELECT name 
FROM cities
EXCEPT
SELECT name
FROM countries
ORDER BY name;
```

### Calling all set operators


| UNION or UNION ALL | INTERSECT | EXCEPT |
| ------------------- | ------------------ |---|
|You are a school teacher teaching multiple classes. You would like to combine the grades of all students into one consolidated sheet.|A residence hall has asked students to rank their preferences to be assigned a room. They now want to pair students based on common preferences.| You run a music streaming service and have a list of songs a user has listened to. You want to show them new songs they haven't heard before.|

