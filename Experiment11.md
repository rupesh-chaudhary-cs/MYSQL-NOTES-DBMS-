
---

# 📄 **Experiment 11.md**

```md
# Experiment 11: Advanced Subqueries and Operations

## Aim
To perform advanced queries with nested conditions.

---

## Queries

```sql
-- 1. Delete employees joined before 31-Dec-82 (location assumed).
DELETE FROM EMPLOYEE
WHERE HIREDATE < '1982-12-31';

-- 2. Employees working as managers.
SELECT E.ENAME, E.JOB, D.DNAME
FROM EMPLOYEE E JOIN DEPARTMENT D
ON E.DEPTNO=D.DEPTNO
WHERE E.JOB='MANAGER';

-- 3. Ford salary equals highest in grade.
SELECT ENAME, SAL FROM EMPLOYEE
WHERE ENAME='FORD'
AND SAL = (SELECT MAX(SAL) FROM EMPLOYEE);

-- 4. Top 5 earners.
SELECT ENAME, SAL FROM EMPLOYEE
ORDER BY SAL DESC
LIMIT 5;

-- 5. Employees with highest salary.
SELECT ENAME FROM EMPLOYEE
WHERE SAL=(SELECT MAX(SAL) FROM EMPLOYEE);

-- 6. Salary equal to avg(max,min).
SELECT * FROM EMPLOYEE
WHERE SAL = ((SELECT MAX(SAL)+MIN(SAL) FROM EMPLOYEE)/2);

-- 7. Dept with at least 3 employees.
SELECT DNAME FROM DEPARTMENT D
JOIN EMPLOYEE E ON D.DEPTNO=E.DEPTNO
GROUP BY D.DEPTNO
HAVING COUNT(*) >= 3;

-- 8. Managers earning > avg salary.
SELECT ENAME FROM EMPLOYEE
WHERE JOB='MANAGER'
AND SAL > (SELECT AVG(SAL) FROM EMPLOYEE);

-- 9. Managers earning > avg of their employees.
SELECT M.ENAME FROM EMPLOYEE M
WHERE JOB='MANAGER'
AND SAL > (SELECT AVG(SAL) FROM EMPLOYEE WHERE MGR=M.EMPNO);

-- 10. Employees whose net pay >= any salary.
SELECT ENAME, SAL, COMM,
(SAL + IFNULL(COMM,0)) AS NETPAY
FROM EMPLOYEE
WHERE (SAL + IFNULL(COMM,0)) >= ANY (SELECT SAL FROM EMPLOYEE);
