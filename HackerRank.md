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

        SELECT CONCAT(name,"(",LEFT(occupation, 1),")") AS name
        FROM OCCUPATIONS ORDER BY name;
        SELECT CONCAT ("There are a total of ", COUNT(*)," ", LOWER(occupation),"s.") AS result
        FROM OCCUPATIONS
        GROUP BY occupation
        ORDER BY COUNT(*) ASC, occupation ASC;

23. Occupations

        SELECT
            MAX(CASE when Occupation = "Doctor" THEN NAME END) AS Doctor,
            MAX(CASE when Occupation = "Professor" THEN NAME END) AS Professor,
            MAX(CASE when Occupation = "Singer" THEN NAME END) AS Singer,
            MAX(CASE when Occupation = "Actor" THEN NAME END) AS Actor
            FROM (
            SELECT Name, Occupation,
                ROW_NUMBER() OVER(PARTITION BY Occupation ORDER BY Name)AS RowNum 
                FROM OCCUPATIONS
            ) AS SubQuery
            GROUP BY RowNum
            ORDER BY RowNum;

24. Binary Tree Nodes

        SELECT N, 
        CASE 
            WHEN P IS NULL THEN "Root" 
            WHEN N IN(SELECT P FROM BST) THEN "Inner" 
                ELSE "Leaf" 
        END AS TYPE_OF_NODE 
        FROM BST ORDER BY N;

25. New Companies

        SELECT company.company_code, company.founder, COUNT(DISTINCT employee.lead_manager_code), COUNT(DISTINCT employee.senior_manager_code), COUNT(DISTINCT employee.manager_code), COUNT(DISTINCT employee.employee_code) 
        FROM company 
        JOIN 
        employee
        ON company.company_code = employee.company_code
        GROUP BY company.company_code, company.founder 
        ORDER BY company.company_code;

26. Revising Aggregations - The Count Function

        SELECT COUNT(NAME)
        FROM CITY
        WHERE POPULATION > 100000;

27. Revising Aggregations - The Sum Function

        SELECT SUM(POPULATION)
        FROM CITY
        WHERE DISTRICT = 'California';

28. Revising Aggregations - Averages

        SELECT AVG(POPULATION)
        FROM CITY
        WHERE DISTRICT = 'California';

29. Average Population

        SELECT ROUND(AVG(POPULATION),0)
        FROM CITY;

30. Japan Population

        SELECT SUM(POPULATION)
        FROM CITY
        WHERE COUNTRYCODE = 'JPN';

31. Population Density Difference

        SELECT (MAX(POPULATION)- MIN(POPULATION)) 
        FROM CITY;

32. The Blunder

        SELECT CEIL(AVG(Salary) - AVG(CAST(REPLACE(CAST(Salary AS CHAR(10)),'0','') AS DECIMAL(10,2)))) AS SALARY_DIFF
        FROM EMPLOYEES;

33. Top Earners

        SELECT MAX(SALARY * MONTHS) AS MAX_TOTAL_EARNINGS, COUNT(EMPLOYEE_ID) AS NUM_EMP_WITH_MAX_EARNINGS
        FROM EMPLOYEE
        WHERE (SALARY*MONTHS) = (SELECT MAX(SALARY * MONTHS) FROM EMPLOYEE);

34. Population Census

        SELECT SUM(C.POPULATION)
        FROM CITY C
        JOIN
        COUNTRY T
        ON C.COUNTRYCODE = T.CODE
        WHERE T.CONTINENT = 'Asia';

35. African Cities

        SELECT C.NAME
        FROM CITY C
        JOIN
        COUNTRY T
        ON C.COUNTRYCODE = T.CODE
        WHERE T.CONTINENT = 'Africa';

36. Average Population of Each Continent

        SELECT T.CONTINENT, FLOOR(AVG(C.POPULATION))
        FROM CITY C 
        JOIN 
        COUNTRY  T
        ON C.COUNTRYCODE = T.CODE 
        GROUP BY T.CONTINENT;

37. Weather Observation Station 18

        SELECT CAST(ROUND((MAX(LAT_N) - MIN(LAT_N)) + (MAX(LONG_W) - MIN(LONG_W)), 4 ) AS DECIMAL(10,4)) AS ManhattanDistance 
        FROM STATION;

38. Weather Observation Station 19

        SELECT ROUND(SQRT(POWER(MAX(LAT_N) - MIN(LAT_N), 2) + POWER(MAX(LONG_W) - MIN(LONG_W), 2)), 4)
        FROM STATION;

39. Weather Observation Station 20

        SELECT ROUND(LAT_N,4)
        FROM (SELECT LAT_N, ROW_NUMBER() OVER(ORDER BY LAT_N ASC) AS RN, COUNT(*) OVER() AS Total_Rows FROM STATION) AS SUB_QUERY
        WHERE RN = CEIL(Total_Rows/2) OR RN = FLOOR(Total_Rows/2)+1;

40. Top Competitors

        SELECT h.hacker_id, h.name
        FROM (
            SELECT s.hacker_id, COUNT(DISTINCT s.challenge_id) AS count_ch
            FROM Submissions s
            LEFT JOIN Challenges c ON s.challenge_id = c.challenge_id
            LEFT JOIN Difficulty d ON c.difficulty_level = d.difficulty_level
            WHERE s.score = d.score
            GROUP BY s.hacker_id
            HAVING COUNT(DISTINCT s.challenge_id) >= 2
        ) AS a
        JOIN Hackers h ON a.hacker_id = h.hacker_id
        ORDER BY a.count_ch DESC, h.hacker_id;

41. Ollivander's Inventory

        SELECT w.id, p.age,w.coins_needed,w.power
        FROM Wands w 
        JOIN 
        Wands_Property p 
        ON w.code = p.code 
        WHERE p.is_evil= 0 AND (w.coins_needed,w.power,p.age) 
            IN (SELECT MIN(w1.coins_needed),w1.power,p1.age 
            FROM Wands w1 JOIN Wands_Property p1 ON w1.code=p1.code 
            WHERE p1.is_evil= 0 
            GROUP BY w1.power,p1.age) 
            ORDER BY w.power DESC ,p.age DESC;

42. Challenges

        SELECT A.hacker_id, A.name, COUNT(B.challenge_id) AS cc
        FROM hackers A 
        INNER JOIN 
        Challenges B 
        ON A.hacker_id = B.hacker_id
        GROUP BY hacker_id, name
        HAVING cc IN
        (SELECT NC.nc 
         FROM
            (SELECT hacker_id, COUNT(challenge_id) AS nc FROM Challenges GROUP BY hacker_id) NC
         GROUP BY Nc.nc
         HAVING NOT
         (COUNT(NC.hacker_id) >= 2 
          AND NC.nc < (SELECT COUNT(challenge_id) AS cc FROM Challenges GROUP BY hacker_id ORDER BY cc DESC LIMIT 1)))
        ORDER BY cc DESC, hacker_id;

43. Contest Leaderboard

        SELECT A.hacker_id, B.name, SUM(maxScore) as total_score
        FROM( SELECT hacker_id, challenge_id, MAX(score) as maxScore 
             FROM submissions GROUP BY hacker_id, challenge_id ) A JOIN 
             hackers B ON A.hacker_id = B.hacker_id 
             GROUP BY A.hacker_id, B.name HAVING SUM(maxScore) >0 
             ORDER BY total_score DESC,hacker_id ASC;

44. 15 Days of Learning SQL
45. The Report

        SELECT CASE WHEN g.grade < 8 THEN 'NULL'
                    ELSE s.name END AS name,
               g.grade,
               s.marks
        FROM students s
                    JOIN grades g ON s.marks BETWEEN g.min_mark AND g.max_mark
        ORDER BY g.grade DESC, s.name, s.marks;

46. Placements

        SELECT s.name 
        FROM students s 
        JOIN friends f ON s.id = f.id
        JOIN packages p ON p.id = s.id
        JOIN packages x ON x.id = f.friend_id
        WHERE x.salary > p.salary
        ORDER BY x.salary;

47. SQL Project Planning

        SELECT 
            s.Start_Date, 
            MIN(e.End_Date) AS End_Date
        FROM 
            (SELECT Start_Date 
             FROM Projects 
             WHERE Start_Date NOT IN (SELECT End_Date FROM Projects)) s
        JOIN 
            (SELECT End_Date 
             FROM Projects 
             WHERE End_Date NOT IN (SELECT Start_Date FROM Projects)) e
        ON 
            s.Start_Date < e.End_Date
        GROUP BY s.Start_Date
        ORDER BY DATEDIFF(MIN(e.End_Date), s.Start_Date), s.Start_Date;

48. Symmetric Pairs

        SELECT f1.X, f1.Y
        FROM Functions f1 
        JOIN Functions f2 
        ON f1.X = f2.Y AND f2.X = f1.Y 
        WHERE f1.X < f1.Y
        UNION
        SELECT X,Y 
        FROM Functions 
        GROUP BY X,Y 
        HAVING COUNT(*) > 1 
        ORDER BY X;

49. Print Prime Numbers
50. Draw The Triangle 1

        WITH RECURSIVE cnt (n) AS ( SELECT 20 UNION ALL SELECT n - 1 FROM cnt WHERE n > 1 )
        SELECT REPEAT("* ", n) FROM cnt;

51. Draw The Triangle 2

        WITH RECURSIVE cnt (n) AS ( SELECT 1 AS n UNION ALL SELECT n + 1 FROM cnt WHERE n < 20 )
        SELECT REPEAT("* ", n) FROM cnt;

52. Interviews Discussions
53. Weather Observation Station 2

        SELECT ROUND(SUM(LAT_N),2), ROUND(SUM(LONG_W),2)
        FROM STATION
    
54. Weather Observation Station 13

        SELECT ROUND(SUM(LAT_N),4)
        FROM STATION
        WHERE LAT_N BETWEEN 38.7880 AND 137.2345;

55. Weather Observation Station 14 

        SELECT ROUND(MAX(LAT_N),4)
        FROM STATION
        WHERE LAT_N < 137.2345;
        
56.Weather Observation Station 15

       SELECT ROUND(LONG_W,4)
        FROM STATION
        WHERE LAT_N = (SELECT MAX(LAT_N)
                      FROM STATION
                      WHERE LAT_N <137.2345); 

57. Weather Observation Station 16

        SELECT ROUND(MIN(LAT_N),4)
        FROM STATION
        WHERE LAT_N  > 38.7780);

58. Weather Observation Station 17 

        SELECT ROUND(LONG_W,4)
        FROM STATION
        WHERE LAT_N = (SELECT MIN(LAT_N)
                       FROM STATION
                       WHERE LAT_N > 38.7780);        
    
