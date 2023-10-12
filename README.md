# hackerrank_solutions_sql
solutions for all hackerrank queries are incorporated here :) 

BASIC SELECT > Revising the Select Query I >

1. Query all columns for all American cities in the CITY table with populations larger than 100000. The CountryCode for America is USA.
Solution: 
SELECT * 
FROM CITY 
WHERE 
POPULATION > 100000 AND COUNTRYCODE = 'USA' ; 

2. Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.
Solution:
SELECT NAME 
FROM CITY 
WHERE 
POPULATION > 120000 AND COUNTRYCODE = 'USA' ;
 
3. Query all columns (attributes) for every row in the CITY table.
Solution:
SELECT * FROM CITY;

4. Query all columns for a city in CITY with the ID 1661.
Solution:
SELECT * 
FROM CITY 
WHERE 
ID = 1661 ;

5.Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN.
Solution:
SELECT * 
FROM CITY 
WHERE 
COUNTRYCODE='JPN';

6.Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN. 
Solution:
SELECT NAME 
FROM CITY 
WHERE 
COUNTRYCODE='JPN';

7. Query a list of CITY and STATE from the STATION table.
Solution:
SELECT CITY,STATE 
FROM 
STATION;

8. Query a list of CITY names from STATION for cities that have an even ID number.
   Print the results in any order, but exclude duplicates from the answer.
Solution:
SELECT DISTINCT(CITY)
FROM STATION 
WHERE ID%2=0
ORDER BY CITY ASC;

Solution:
SELECT DISTINCT(CITY)
FROM STATION 
WHERE MOD(ID,2)=0 
ORDER BY CITY ASC; 

9. Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table.
Solution:
SELECT (COUNT(CITY) - COUNT(DISTINCT(CITY))) AS DIFF
FROM STATION ;

10. Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name).
    If there is more than one smallest or largest city, 
    choose the one that comes first when ordered alphabetically.
Solution:
SELECT CITY, LENGTH(CITY) FROM STATION ORDER BY LENGTH(CITY) ASC, CITY ASC LIMIT 1;
SELECT CITY, LENGTH(CITY) FROM STATION ORDER BY LENGTH(CITY) DESC , CITY DESC LIMIT 1;

11. Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.
Solution:
SELECT DISTINCT(CITY)
FROM STATION 
WHERE 
CITY LIKE 'A%' OR 
CITY LIKE 'E%' OR 
CITY LIKE 'I%' OR 
CITY LIKE 'O%' OR 
CITY LIKE 'U%' 
ORDER BY CITY ASC;


12. Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.
Solution:
SELECT DISTINCT(CITY)
FROM STATION 
WHERE 
TRIM(UPPER(CITY)) LIKE '%A' OR 
TRIM(UPPER(CITY)) LIKE '%E' OR 
TRIM(UPPER(CITY)) LIKE '%I' OR 
TRIM(UPPER(CITY)) LIKE '%O' OR 
TRIM(UPPER(CITY)) LIKE '%U' ;

13. Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters.
    Your result cannot contain duplicates.
Solution:
SELECT CITY
FROM STATION
WHERE 
(CITY LIKE 'A%' OR CITY LIKE 'E%' OR CITY LIKE 'I%' OR CITY LIKE 'O%' OR CITY LIKE 'U%') 
AND 
(CITY LIKE '%A' OR CITY LIKE '%E' OR CITY LIKE '%I' OR CITY LIKE '%O' OR CITY LIKE '%U')
ORDER BY CITY ASC;
    
14. Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.
    
Solution: 

SELECT DISTINCT(CITY)
FROM STATION 
WHERE 
CITY NOT LIKE 'A%' AND CITY NOT LIKE 'E%' AND CITY NOT LIKE 'I%' AND CITY NOT LIKE 'O%' AND
CITY NOT LIKE 'U%'
ORDER BY CITY ASC;














