# Experiment 10: Subqueries and Conditions

## Aim
To perform complex queries using subqueries and conditions.

---

## Queries

```sql
-- 1. Employees from dept 10 with salary greater than ANY employee in other departments.
SELECT ENAME FROM EMPLOYEE
WHERE DEPTNO = 10
AND SAL > ANY (SELECT SAL FROM EMPLOYEE WHERE DEPTNO <> 10);

-- 2. Employees from dept 10 with salary greater than ALL employees in other departments.
SELECT ENAME FROM EMPLOYEE
WHERE DEPTNO = 10
AND SAL > ALL (SELECT SAL FROM EMPLOYEE WHERE DEPTNO <> 10);

-- 3. Employees in sales dept and grade = 3 (assuming SALGRADE table).
SELECT E.* FROM EMPLOYEE E, SALGRADE S
WHERE E.SAL BETWEEN S.LOSAL AND S.HISAL
AND S.GRADE = 3
AND E.DEPTNO = (SELECT DEPTNO FROM DEPARTMENT WHERE DNAME='SALES');

-- 4. Employees who are not managers.
SELECT * FROM EMPLOYEE
WHERE JOB <> 'MANAGER';

-- 5. Employees whose manager name is JONES.
SELECT E.ENAME FROM EMPLOYEE E
JOIN EMPLOYEE M ON E.MGR = M.EMPNO
WHERE M.ENAME='JONES';

-- 6. Employees working in sales dept.
SELECT ENAME FROM EMPLOYEE
WHERE DEPTNO = (SELECT DEPTNO FROM DEPARTMENT WHERE DNAME='SALES');

-- 7. Employee details with salary between 2000-5000 and location Chicago (assumed).
SELECT E.ENAME, D.DNAME, E.SAL, E.COMM
FROM EMPLOYEE E JOIN DEPARTMENT D
ON E.DEPTNO=D.DEPTNO
WHERE E.SAL BETWEEN 2000 AND 5000;

-- 8. Employees whose salary > manager salary.
SELECT E.ENAME FROM EMPLOYEE E
JOIN EMPLOYEE M ON E.MGR=M.EMPNO
WHERE E.SAL > M.SAL;

-- 9. Employees working in same dept as manager.
SELECT E.ENAME FROM EMPLOYEE E
JOIN EMPLOYEE M ON E.MGR=M.EMPNO
WHERE E.DEPTNO = M.DEPTNO;

-- 10. Grade and employees for dept 10 or 30, grade not 4, joined before 31-Dec-82.
SELECT E.ENAME, S.GRADE
FROM EMPLOYEE E, SALGRADE S
WHERE E.SAL BETWEEN S.LOSAL AND S.HISAL
AND E.DEPTNO IN (10,30)
AND S.GRADE <> 4
AND E.HIREDATE < '1982-12-31';
