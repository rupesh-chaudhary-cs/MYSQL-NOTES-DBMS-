
---

# 📄 **Experiment 4.md**

```md id="exp4md"
# Experiment 4: Advanced Conditions and Updates

## Aim
To apply advanced conditions and perform updates.

---

## Queries

```sql
-- 1. Display the list of employees who have joined before 30th June 1980 or after 31st Dec 1981.
SELECT * FROM EMPLOYEE
WHERE HIREDATE < '1980-06-30'
OR HIREDATE > '1981-12-31';

-- 2. Display names of employees whose second alphabet is A.
SELECT ENAME FROM EMPLOYEE
WHERE ENAME LIKE '_A%';

-- 3. Display names of employees whose name is exactly five characters.
SELECT ENAME FROM EMPLOYEE
WHERE LENGTH(ENAME) = 5;

-- 4. Display names of employees whose second alphabet is A.
SELECT ENAME FROM EMPLOYEE
WHERE ENAME LIKE '_A%';

-- 5. Display names of employees who are not salesman, clerk or analyst.
SELECT ENAME FROM EMPLOYEE
WHERE JOB NOT IN ('SALESMAN','CLERK','ANALYST');

-- 6. Display employee name with annual salary in descending order.
SELECT ENAME, (SAL*12) AS ANNUAL_SALARY
FROM EMPLOYEE
ORDER BY SAL DESC;

-- 7. Display name, sal, hra, da, pf and total salary.
SELECT ENAME, SAL,
(SAL*0.15) AS HRA,
(SAL*0.10) AS DA,
(SAL*0.05) AS PF,
((SAL + (SAL*0.15) + (SAL*0.10)) - (SAL*0.05)) AS TOTALSAL
FROM EMPLOYEE;

-- 8. Update salary by 10% for employees not getting commission.
UPDATE EMPLOYEE
SET SAL = SAL * 1.10
WHERE COMM IS NULL;

-- 9. Display employees whose salary becomes more than 3000 after 20% increment.
SELECT * FROM EMPLOYEE
WHERE SAL * 1.20 > 3000;

-- 10. Display employees whose salary has at least 3 digits.
SELECT * FROM EMPLOYEE
WHERE SAL >= 100;
