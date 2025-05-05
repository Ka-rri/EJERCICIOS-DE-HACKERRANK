# EJERCICIOS-DE-HACKERRANK
1. Revising the Select Query I

        SELECT *
        FROM CITY
        WHERE COUNTRYCODE = 'USA' AND POPULATION > 100000;
   
2. Revising the Select Query II

        SELECT NAME
        FROM CITY
        WHERE COUNTRYCODE = 'USA' AND POPULATION > 120000;
   
3. Select All

        SELECT *
        FROM CITY;

4. Select By ID

        SELECT *
        FROM CITY
        WHERE ID = 1661;

5. Japanese Cities' Attributes

        SELECT *
        FROM CITY
        WHERE COUNTRYCODE = 'JPN';

6. Japanese Cities' Names

        SELECT NAME
        FROM CITY
        WHERE COUNTRYCODE = 'JPN';

7. Weather Observation Station 1

        SELECT CITY, STATE
        FROM STATION;

8. Weather Observation Station 3

        SELECT DISTINCT(CITY)
        FROM STATION
        WHERE MOD(ID, 2) = 0;

9. Weather Observation Station 4

        SELECT COUNT(CITY)-COUNT(DISTINCT(CITY))
        FROM STATION;

10. Weather Observation Station 5

        (
          SELECT CITY, LENGTH(CITY) AS LEN
          FROM STATION
          ORDER BY LENGTH(CITY) ASC, CITY ASC
          LIMIT 1
        )
        UNION
        (
          SELECT CITY, LENGTH(CITY) AS LEN
          FROM STATION
          ORDER BY LENGTH(CITY) DESC, CITY ASC
          LIMIT 1
        );

11. Weather Observation Station 6

        SELECT CITY
        FROM STATION
        WHERE SUBSTR(CITY,1,1) IN ('A','E','I','O','U');

12. Weather Observation Station 7

        SELECT DISTINCT(CITY)
        FROM STATION
        WHERE SUBSTR(CITY,LENGTH(CITY),1) IN ('A','E','I','O','U');

13. Weather Observation Station 8

        SELECT DISTINCT(CITY)
        FROM STATION
        WHERE 
        SUBSTR(CITY,1,1) IN ('A','E','I','O','U') AND SUBSTR(CITY,LENGTH(CITY),1) IN ('A','E','I','O','U');

14. Weather Observation Station 9

        SELECT DISTINCT(CITY)
        FROM STATION
        WHERE SUBSTR(CITY,1,1) NOT IN ('A','E','I','O','U');

15. Weather Observation Station 10

        SELECT DISTINCT(CITY)
        FROM STATION
        WHERE SUBSTR(CITY,LENGTH(CITY),1) NOT IN ('A','E','I','O','U');

16. Weather Observation Station 11

        SELECT DISTINCT(CITY)
        FROM STATION
        WHERE SUBSTR(CITY,1,1) NOT IN ('A','E','I','O','U') OR SUBSTR(CITY,LENGTH(CITY),1) NOT IN ('A','E','I','O','U');

17. Weather Observation Station 12

        SELECT DISTINCT(CITY)
        FROM STATION
        WHERE SUBSTR(CITY,1,1) NOT IN ('A','E','I','O','U') AND SUBSTR(CITY,LENGTH(CITY),1) NOT IN ('A','E','I','O','U');

18. Higher Than 75 Marks

        SELECT NAME
        FROM STUDENTS
        WHERE MARKS > 75
        ORDER BY RIGHT(NAME, 3), ID ASC;

19. Employee Names

        SELECT NAME
        FROM EMPLOYEE
        ORDER BY NAME ASC;

20. Employee Salaries

        SELECT NAME
        FROM EMPLOYEE
        WHERE SALARY > 2000 AND MONTHS < 10
        ORDER BY EMPLOYEE_ID ASC;

21. Type of Triangle

        SELECT 
          CASE
            WHEN A + B <= C OR A + C <= B OR B + C <= A THEN 'Not A Triangle'
            WHEN A = B AND B = C THEN 'Equilateral'
            WHEN A = B OR B = C OR A = C THEN 'Isosceles'
            ELSE 'Scalene'
          END AS Triangle_Type
        FROM TRIANGLES;

22. The PADS



    
