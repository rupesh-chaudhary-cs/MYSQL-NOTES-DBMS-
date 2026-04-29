# Experiment 7: Advanced Queries and Aggregations

## Aim
To perform advanced queries, aggregations, and calculations.

---

## Queries

```sql
-- 1. Compute number of days remaining in this year.
SELECT DATEDIFF(CONCAT(YEAR(CURDATE()),'-12-31'), CURDATE()) AS DAYS_LEFT;

-- 2. Find highest, lowest salaries and difference.
SELECT MAX(SAL) AS MAX_SAL, MIN(SAL) AS MIN_SAL,
(MAX(SAL)-MIN(SAL)) AS DIFFERENCE
FROM EMPLOYEE;

-- 3. Employees whose commission > 25% of salary.
SELECT * FROM EMPLOYEE
WHERE COMM > 0.25 * SAL;

-- 4. Display salary in dollar format.
SELECT ENAME, CONCAT('$',SAL) AS SALARY FROM EMPLOYEE;

-- 5. Matrix query: job-wise salary by department.
SELECT JOB,
SUM(CASE WHEN DEPTNO=10 THEN SAL ELSE 0 END) AS DEPT10,
SUM(CASE WHEN DEPTNO=20 THEN SAL ELSE 0 END) AS DEPT20,
SUM(CASE WHEN DEPTNO=30 THEN SAL ELSE 0 END) AS DEPT30,
SUM(SAL) AS TOTAL
FROM EMPLOYEE
GROUP BY JOB;

-- 6. Employees hired in specific years.
SELECT COUNT(*) AS TOTAL,
SUM(YEAR(HIREDATE)=1980) AS Y1980,
SUM(YEAR(HIREDATE)=1981) AS Y1981,
SUM(YEAR(HIREDATE)=1982) AS Y1982,
SUM(YEAR(HIREDATE)=1983) AS Y1983
FROM EMPLOYEE;

-- 7. Last Sunday of current month.
SELECT DATE_SUB(LAST_DAY(CURDATE()),
INTERVAL (DAYOFWEEK(LAST_DAY(CURDATE()))-1) DAY);

-- 8. Department-wise employee count.
SELECT DEPTNO, COUNT(*) FROM EMPLOYEE GROUP BY DEPTNO;

-- 9. Job-wise employee count.
SELECT JOB, COUNT(*) FROM EMPLOYEE GROUP BY JOB;

-- 10. Department-wise total salary.
SELECT DEPTNO, SUM(SAL) FROM EMPLOYEE GROUP BY DEPTNO;
