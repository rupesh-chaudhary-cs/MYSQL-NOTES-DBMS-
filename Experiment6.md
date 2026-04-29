
---

# 📄 **Experiment 6.md**

```md id="exp6md"
# Experiment 6: Date and Miscellaneous Functions

## Aim
To perform operations using date and special functions.

---

## Queries

```sql
-- 1. Display empno, ename, dept name instead of deptno.
SELECT E.EMPNO, E.ENAME, D.DNAME
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO;

-- 2. Display your age in days.
SELECT DATEDIFF(CURDATE(),'2000-01-01') AS AGE_DAYS;

-- 3. Display your age in months.
SELECT PERIOD_DIFF(DATE_FORMAT(CURDATE(),'%Y%m'), DATE_FORMAT('2000-01-01','%Y%m')) AS AGE_MONTHS;

-- 4. Display current date in format.
SELECT DATE_FORMAT(CURDATE(),'%D %M %W %Y');

-- 5. Display formatted joining sentence.
SELECT CONCAT(ENAME,' has joined the company on ',
DATE_FORMAT(HIREDATE,'%W %D %M %Y')) FROM EMPLOYEE;

-- 6. Example output already covered above.

-- 7. Find nearest Saturday after current date.
SELECT NEXT_DAY(CURDATE(),'SATURDAY');

-- 8. Display current time.
SELECT CURTIME();

-- 9. Display date three months before current date.
SELECT DATE_SUB(CURDATE(), INTERVAL 3 MONTH);

-- 10. Employees joined in December.
SELECT * FROM EMPLOYEE
WHERE MONTH(HIREDATE)=12;

-- 11. First 2 characters of hiredate and last 2 of salary.
SELECT ENAME,
LEFT(HIREDATE,2),
RIGHT(SAL,2)
FROM EMPLOYEE;

-- 12. Employees where 10% salary equals joining year.
SELECT * FROM EMPLOYEE
WHERE (SAL*0.10)=YEAR(HIREDATE);

-- 13. Employees who joined before 15 months.
SELECT * FROM EMPLOYEE
WHERE HIREDATE < DATE_SUB(CURDATE(), INTERVAL 15 MONTH);

-- 14. Employees who joined before 15th of month.
SELECT * FROM EMPLOYEE
WHERE DAY(HIREDATE) < 15;

-- 15. Employees whose joining date matches deptno (logical condition).
SELECT * FROM EMPLOYEE
WHERE DAY(HIREDATE)=DEPTNO;
