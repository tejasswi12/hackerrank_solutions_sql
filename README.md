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

15. Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.
Solution:
SELECT DISTINCT(CITY)
FROM STATION
WHERE 
CITY NOT LIKE '%A' AND
CITY NOT LIKE '%E' AND
CITY NOT LIKE '%I' AND
CITY NOT LIKE '%O' AND
CITY NOT LIKE '%U'
ORDER BY CITY ASC;

16. Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.
Solution:
SELECT DISTINCT(CITY)
FROM STATION
WHERE
(CITY NOT LIKE 'A%' AND CITY NOT LIKE 'E%' AND CITY NOT LIKE 'I%' AND CITY NOT LIKE 'O%' AND CITY NOT LIKE 'U%')
 OR 
(CITY NOT LIKE '%A' AND CITY NOT LIKE '%E' AND CITY NOT LIKE '%I' AND CITY NOT LIKE '%O' AND CITY NOT LIKE '%U')
ORDER BY CITY ASC;

17. Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.
Solution:
SELECT DISTINCT(CITY)
FROM STATION
WHERE
(CITY NOT LIKE 'A%' AND CITY NOT LIKE 'E%' AND CITY NOT LIKE 'I%' AND CITY NOT LIKE 'O%' AND CITY NOT LIKE 'U%')
AND 
(CITY NOT LIKE '%A' AND CITY NOT LIKE '%E' AND CITY NOT LIKE '%I' AND CITY NOT LIKE '%O' AND CITY NOT LIKE '%U')
ORDER BY CITY ASC;

18. Query the Name of any student in STUDENTS who scored higher than  Marks.
    Order your output by the last three characters of each name.
    If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.
Solution:
SELECT NAME 
FROM STUDENTS 
WHERE 
MARKS > 75 
ORDER BY SUBSTR(NAME, -3), ID ASC;

19. Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.
Solution:  
SELECT NAME 
FROM EMPLOYEE
ORDER BY NAME ASC; 

20. Write a query that prints a list of employee names for employees in Employee having a salary greater than 2000 per month who have been employees for less than 10 months.
    Sort your result by ascending order of employee_id.
Solution:
SELECT NAME 
FROM EMPLOYEE
WHERE
SALARY > 2000 AND MONTHS < 10 
ORDER BY EMPLOYEE_ID ASC;

21. Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.
    Note: CITY.CountryCode and COUNTRY.Code are matching key columns.
Solution:
SELECT Country.Continent, FLOOR(AVG(City.Population))
FROM Country, City 
WHERE Country.Code = City.CountryCode 
GROUP BY Country.Continent ;

22. You are given two tables: Students and Grades. Students contains three columns ID, Name and Marks.
    Ketty gives Eve a task to generate a report containing three columns: Name, Grade and Mark.
    Ketty doesn't want the NAMES of those students who received a grade lower than 8. The report must be in descending order by grade -- i.e. higher grades are entered first.
    If there is more than one student with the same grade (8-10) assigned to them, order those particular students by their name alphabetically.
    Finally, if the grade is lower than 8, use "NULL" as their name and list them by their grades in descending order.
    If there is more than one student with the same grade (1-7) assigned to them, order those particular students by their marks in ascending order.
    Write a query to help Eve.
Solution:
   
23. Query a count of the number of cities in CITY having a Population larger than 100000
Solution:
SELECT COUNT(*) 
FROM CITY 
WHERE POPULATION > 100000;
 
24. Query the total population of all cities in CITY where District is California.
Solution:
SELECT SUM(POPULATION) 
FROM CITY
WHERE DISTRICT = 'CALIFORNIA' ;

25. Query the average population of all cities in CITY where District is California.
Solution:
SELECT AVG(POPULATION) 
FROM CITY
WHERE DISTRICT = 'CALIFORNIA' ; 

26.Query the average population for all cities in CITY, rounded down to the nearest integer.
Solution:
SELECT ROUND(AVG(POPULATION),0)
FROM CITY;

27. Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.
Solution:
SELECT SUM(POPULATION)
FROM CITY
WHERE COUNTRYCODE ='JPN';

28. Query the difference between the maximum and minimum populations in CITY. 
Solution:
SELECT MAX(POPULATION) - MIN(POPULATION)
FROM CITY;

29. Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's  key was broken until after completing the calculation. 
    She wants your help finding the difference between her miscalculation (using salaries with any zeros removed), and the actual average salary.
    Write a query calculating the amount of error (i.e.:  average monthly salaries), and round it up to the next integer.
Solution:
SELECT CEIL(AVG(SALARY) - AVG(REPLACE(SALARY, '0', '')))
FROM EMPLOYEES;

30. We define an employee’s total earnings to be their monthly salary* months worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. 
    Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. 
    Then print these values as space-separated integers.
Solution:
SELECT MONTHS*SALARY, COUNT(*) 
FROM EMPLOYEE
GROUP BY MONTHS*SALARY
ORDER BY MONTHS*SALARY DESC
LIMIT 1;

31. Query the following two values from the STATION table:
    The sum of all values in LAT_N rounded to a scale of  decimal places.
    The sum of all values in LONG_W rounded to a scale of  decimal places.
Solution:
SELECT ROUND(SUM(LAT_N),2), ROUND(SUM(LONG_W),2) FROM STATION; 

32. Query the sum of Northern Latitudes (LAT_N) from STATION having values greater than 38.7880 and less than 137.2345 . Truncate your answer to 4 decimal places.
Solution:
SELECT ROUND(SUM(LAT_N),4) 
FROM STATION 
WHERE
LAT_N BETWEEN 38.7880 AND 137.2345 ; 

33. Query the greatest value of the Northern Latitudes (LAT_N) from STATION that is less than 137.2345. Truncate your answer to 4 decimal places.
Solution:
SELECT ROUND(MAX(LAT_N),4) 
FROM STATION
WHERE
LAT_N < 137.2345 ;

34. Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than 137.2345. Round your answer to 4 decimal places.
Solution:
SELECT ROUND(LONG_W,4)
FROM STATION
WHERE
LAT_N = (SELECT MAX(LAT_N) FROM STATION WHERE LAT_N < 137.2345);

35. Query the smallest Northern Latitude (LAT_N) from STATION that is greater than 38.7780. Round your answer to 4 decimal places.
Solution:
SELECT ROUND(MIN(LAT_N),4)
FROM STATION
WHERE
LAT_N > 38.7780 ;

36. Query the Western Longitude (LONG_W) where the smallest Northern Latitude (LAT_N) in STATION is greater than 38.7780 . Round your answer to 4 decimal places. 
Solution:
SELECT ROUND(LONG_W, 4)
FROM STATION
WHERE 
LAT_N = (SELECT MIN(LAT_N) FROM STATION WHERE LAT_N > 38.7780);

37. Consider p1(a,b) and p2(c,d) to be two points on a 2D plane.
    a happens to equal the minimum value in Northern Latitude (LAT_N in STATION).
    b happens to equal the minimum value in Western Longitude (LONG_W in STATION).
    c happens to equal the maximum value in Northern Latitude (LAT_N in STATION).
    d happens to equal the maximum value in Western Longitude (LONG_W in STATION).
    Query the Manhattan Distance between points p1 and p2 and round it to a scale of 4 decimal places.
Solution: 
SELECT ROUND((MAX(LAT_N) - MIN(LAT_N) + MAX(LONG_W) - MIN(LONG_W)), 4) AS D
FROM STATION; 

38. Consider p1(a,b) and p2(c,d) to be two points on a 2D plane where (a,b) are the respective minimum and maximum values of Northern Latitude (LAT_N) and (c,d) are the 
    respective minimum and maximum values of Western Longitude (LONG_W) in STATION.
    Query the Euclidean Distance between points p1(a,b) and p2(c,d) and format your answer to display 4 decimal digits.
Solution:
SELECT 
ROUND(SQRT(POWER(MAX(LAT_N) - MIN(LAT_N), 2) + POWER(MAX(LONG_W) - MIN(LONG_W), 2)),4)
FROM STATION; 

39. A median is defined as a number separating the higher half of a data set from the lower half. Query the median of the Northern Latitudes (LAT_N) from STATION and round 
    your answer to 4 decimal places.
Solution:
SELECT ROUND(LAT_N,4) AS MEDIAN 
FROM STATION AS S
WHERE
(SELECT COUNT(LAT_N) FROM STATION WHERE LAT_N < S.LAT_N) = (SELECT COUNT(LAT_N) FROM STATION WHERE LAT_N > S.LAT_N);

40. Julia conducted a 15 days of learning SQL contest. The start date of the contest was March 01, 2016 and the end date was March 15, 2016.
    Write a query to print total number of unique hackers who made at least 1 submission each day (starting on the first day of the contest), and find the hacker_id and 
    name of the hacker who made maximum number of submissions each day. If more than one such hacker has a maximum number of submissions, print the lowest hacker_id. The 
    query should print this information for each day of the contest, sorted by the date.
Solution:

41. Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.
    Note: CITY.CountryCode and COUNTRY.Code are matching key columns.
Solution:
SELECT SUM(C.POPULATION)
FROM CITY AS C
JOIN COUNTRY AS C1
ON 
C.COUNTRYCODE = C1.CODE
WHERE
C1.CONTINENT = 'ASIA';

42. 

























