
---

# 📄 **Experiment 5.md**

```md id="exp5md"
# Experiment 5: Aggregate and String Functions

## Aim
To use aggregate and string functions.

---

## Queries

```sql
-- 1. Total number of employees.
SELECT COUNT(*) FROM EMPLOYEE;

-- 2. Total salary of all employees.
SELECT SUM(SAL) FROM EMPLOYEE;

-- 3. Maximum salary.
SELECT MAX(SAL) FROM EMPLOYEE;

-- 4. Minimum salary.
SELECT MIN(SAL) FROM EMPLOYEE;

-- 5. Average salary.
SELECT AVG(SAL) FROM EMPLOYEE;

-- 6. Maximum salary of clerk.
SELECT MAX(SAL) FROM EMPLOYEE WHERE JOB='CLERK';

-- 7. Maximum salary in dept 20.
SELECT MAX(SAL) FROM EMPLOYEE WHERE DEPTNO=20;

-- 8. Minimum salary of salesman.
SELECT MIN(SAL) FROM EMPLOYEE WHERE JOB='SALESMAN';

-- 9. Average salary of managers.
SELECT AVG(SAL) FROM EMPLOYEE WHERE JOB='MANAGER';

-- 10. Total salary of analyst in dept 40.
SELECT SUM(SAL) FROM EMPLOYEE WHERE JOB='ANALYST' AND DEPTNO=40;

-- 11. Names in uppercase.
SELECT UPPER(ENAME) FROM EMPLOYEE;

-- 12. Names in lowercase.
SELECT LOWER(ENAME) FROM EMPLOYEE;

-- 13. Names in proper case.
SELECT CONCAT(UCASE(LEFT(ENAME,1)), LCASE(SUBSTRING(ENAME,2))) FROM EMPLOYEE;

-- 14. Length of your name.
SELECT LENGTH('RUPESH');

-- 15. Length of all employee names.
SELECT ENAME, LENGTH(ENAME) FROM EMPLOYEE;
