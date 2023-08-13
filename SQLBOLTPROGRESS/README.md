## SQL Review: Simple SELECT Queries
In the exercise below i'll be working with a table  contains information about a few of the most populous cities of North America including their population and geo-spatial location in the world.
### Table: North_american_cities
| City        | Country           | Population  | Latitude        | Longitude           |
| ------------- |:-------------:| -----:| ------------- |:-------------:|
| Guadalajara     | Mexico |1500800 |20.659699 |-103.349609 |
| Toronto     | Canada      | 2795060 | 43.653226| -79.383184| |
| Houston | United States    |   2195914 | 29.760427|-95.369803 | |
| New York     | United States |8405837 |40.712784 |-74.005941 |
| Philadelphia     | United States |1553165 |39.952584 |-75.165222 |
| Havana     | Cuba |2106146 | 23.05407|-82.345189 |
| Mexico City    | Mexico |8555500 |19.432608 | -99.133208|
| Phoenix    | United States |1513367 |33.448377	 |-112.074037 |
| Los Angeles    | United States |3884307 |34.052234 |-118.243685 |
| Ecatepec de Morelos    | Mexico |1742000 |19.601841 |-99.050674 |
| Montreal    | Canada |1717767 | 45.501689|-73.567256 |
| Chicago    | United States | 2718782|41.878114 | -87.629798|
### Task
Try and write some queries to find the information requested in the tasks you know. You may have to use a different combination of clauses in your query for each task. Once you're done, continue onto the next lesson to learn about queries that span multiple tables.
Below are my answers.

##### 1. List all the Canadian cities and their populations
        
```SQL
SELECT
City,Population 
FROM north_american_cities
WHERE Country = "Canada"; .
```
| City        |  Population  | 
| ------------- |:-------------:| 
| Toronto     | 2795060 |
| Montreal     | 1717767      |

---

##### 2.Order all the cities in the United States by their latitude from north to south

```SQL
SELECT
City 
FROM north_american_cities
WHERE Country = "United States"
ORDER BY Latitude DESC .
```
| City        | 
| ------------- |
| Chicago     |
| New York    | 
| Philadelphia |
| Los Angeles   | 
| Phoenix |
| Houston     |

---
##### 3.List all the cities west of Chicago, ordered from west to east

```SQL
SELECT
city, longitude
FROM north_american_cities
WHERE longitude < -87.629798
ORDER BY longitude ASC
```

| City        |  Population  | 
| ------------- |:-------------:| 
| Los Angeles     | -118.243685 |
| Phoenix     | -112.074037      |
| Guadalajara     | 	-103.349609 |
| Mexico City	     | 	-99.133208      |
| Ecatepec de Morelos	     | -99.050674 |
| Houston     | -95.369803      |

---

##### 4. List the two largest cities in Mexico (by population)

```SQL
SELECT city, population
FROM north_american_cities
WHERE country LIKE "Mexico"
ORDER BY population DESC
LIMIT 2;
```

| City        |  Population  | 
| ------------- |:-------------:| 
| Mexico City     | 8555500 |
| Ecatepec de Morelos	     | 1742000     |

---

##### 5. List the third and fourth largest cities (by population) in the United States and their population

```SQL
SELECT city, population FROM north_american_cities
WHERE country LIKE "United States"
ORDER BY population DESC
LIMIT 2 OFFSET 2;
```
| City        |  Population  | 
| ------------- |:-------------:| 
| Chicago    | 2718782 |
| Houston	     | 2195914     |

