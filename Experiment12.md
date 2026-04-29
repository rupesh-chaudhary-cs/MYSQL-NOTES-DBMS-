
---

# 📄 **Experiment 12.md**

```md
# Experiment 12: Complex Queries and Deletions

## Aim
To perform complex queries and data deletion operations.

---

## Queries

```sql
-- 1. Salary < manager but > any manager salary.
SELECT E.ENAME FROM EMPLOYEE E
JOIN EMPLOYEE M ON E.MGR=M.EMPNO
WHERE E.SAL < M.SAL
AND E.SAL > ANY (SELECT SAL FROM EMPLOYEE WHERE JOB='MANAGER');

-- 2. Number of employees earning more than manager.
SELECT COUNT(*) FROM EMPLOYEE E
JOIN EMPLOYEE M ON E.MGR=M.EMPNO
WHERE E.SAL > M.SAL;

-- 3. Managers not under president.
SELECT ENAME FROM EMPLOYEE
WHERE JOB='MANAGER'
AND MGR <> (SELECT EMPNO FROM EMPLOYEE WHERE JOB='PRESIDENT');

-- 4. Delete departments with no employees.
DELETE FROM DEPARTMENT
WHERE DEPTNO NOT IN (SELECT DISTINCT DEPTNO FROM EMPLOYEE);

-- 5. Delete employees whose deptno not in department table.
DELETE FROM EMPLOYEE
WHERE DEPTNO NOT IN (SELECT DEPTNO FROM DEPARTMENT);

-- 6. Employees whose salary not in grade range.
SELECT * FROM EMPLOYEE E
WHERE NOT EXISTS (
SELECT * FROM SALGRADE S
WHERE E.SAL BETWEEN S.LOSAL AND S.HISAL);

-- 7. Employees whose net pay > any salary.
SELECT ENAME, SAL, COMM,
(SAL + IFNULL(COMM,0)) AS NETPAY
FROM EMPLOYEE
WHERE (SAL + IFNULL(COMM,0)) > ANY (SELECT SAL FROM EMPLOYEE);

-- 8. Employees in sales or research.
SELECT ENAME FROM EMPLOYEE
WHERE DEPTNO IN (
SELECT DEPTNO FROM DEPARTMENT
WHERE DNAME IN ('SALES','RESEARCH'));

-- 9. Grade of JONES.
SELECT GRADE FROM SALGRADE S, EMPLOYEE E
WHERE E.ENAME='JONES'
AND E.SAL BETWEEN S.LOSAL AND S.HISAL;

-- 10. Dept name where length equals employees count.
SELECT DNAME FROM DEPARTMENT D
WHERE LENGTH(DNAME) IN (
SELECT COUNT(*) FROM EMPLOYEE GROUP BY DEPTNO);
