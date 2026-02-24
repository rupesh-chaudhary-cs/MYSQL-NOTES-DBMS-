# Experiment No. 0  
## Database Setup and Table Creation

---

### Student Details

Name: Rupesh Kumar Chaudhary  
Roll Number: __________  
Section: 2CSE23  
Subject: Database Management System (DBMS)  
Trainer: SATYAM YADAV (MySQL)  
Course / Semester: B.Tech CSE – 4th Semester  
Submission Date: __________  

---

## Aim

To create tables EMPLOYEE and DEPARTMENT as per given constraints, insert records into them, and perform required DDL and DML operations.

---

## Procedure

1. Create database as per naming rule.
2. Create DEPARTMENT table with primary key.
3. Create EMPLOYEE table with primary key and foreign key constraint.
4. Insert given values into both tables.
5. Perform required queries on Employee_master table.

---

## Step 1: Create Database

```sql
CREATE DATABASE 2cse23_1086;
USE 2cse23_1086;
```

---

## Step 2: Create DEPARTMENT Table

```sql
CREATE TABLE DEPARTMENT (
    DEPTNO INT(2) PRIMARY KEY,
    DNAME VARCHAR(15) NOT NULL
);
```

---

## Step 3: Create EMPLOYEE Table

```sql
CREATE TABLE EMPLOYEE (
    EMPNO INT(4) PRIMARY KEY,
    ENAME VARCHAR(20) NOT NULL,
    JOB VARCHAR(20),
    MGR INT(4),
    HIREDATE DATE,
    SAL INT(10),
    COMM INT(7),
    DEPTNO INT(2),
    FOREIGN KEY (DEPTNO) REFERENCES DEPARTMENT(DEPTNO)
);
```

---

## Step 4: Insert Values into DEPARTMENT

```sql
INSERT INTO DEPARTMENT VALUES (10, 'RESEARCH');
INSERT INTO DEPARTMENT VALUES (20, 'ACCOUNTING');
INSERT INTO DEPARTMENT VALUES (30, 'SALES');
INSERT INTO DEPARTMENT VALUES (40, 'OPERATIONS');
```

---

## Step 5: Insert Values into EMPLOYEE

```sql
INSERT INTO EMPLOYEE VALUES (7369,'SMITH','CLERK',7902,'1980-12-17',800,NULL,20);
INSERT INTO EMPLOYEE VALUES (7499,'ALLEN','SALESMAN',7698,'1981-02-20',1600,300,30);
INSERT INTO EMPLOYEE VALUES (7521,'WARD','SALESMAN',7698,'1981-02-22',1250,300,30);
INSERT INTO EMPLOYEE VALUES (7566,'JONES','MANAGER',7839,'1981-04-02',2975,NULL,20);
INSERT INTO EMPLOYEE VALUES (7654,'MARTIN','SALESMAN',7698,'1981-09-28',1250,1400,30);
INSERT INTO EMPLOYEE VALUES (7698,'BLAKE','MANAGER',7839,'1981-05-01',2850,NULL,30);
INSERT INTO EMPLOYEE VALUES (7782,'CLARK','MANAGER',7839,'1981-06-09',2450,NULL,20);
INSERT INTO EMPLOYEE VALUES (7788,'SCOTT','ANALYST',7566,'1982-12-09',3000,NULL,40);
INSERT INTO EMPLOYEE VALUES (7839,'KING','PRESIDENT',NULL,'1981-11-17',5000,NULL,20);
INSERT INTO EMPLOYEE VALUES (7844,'TURNER','SALESMAN',7698,'1981-09-08',1500,0,30);
INSERT INTO EMPLOYEE VALUES (7876,'ADAMS','CLERK',7788,'1983-01-12',1100,NULL,20);
INSERT INTO EMPLOYEE VALUES (7900,'JAMES','CLERK',7698,'1981-12-03',950,NULL,30);
INSERT INTO EMPLOYEE VALUES (7902,'FORD','ANALYST',7566,'1981-12-03',3000,NULL,20);
INSERT INTO EMPLOYEE VALUES (7934,'MILLER','CLERK',7782,'1982-01-23',1300,NULL,10);
```

---

# Required Queries

---

## 1. Create Employee_master table with data using Employee table

```sql
CREATE TABLE Employee_master AS
SELECT * FROM EMPLOYEE;
```

---

## 2. Delete all records from Employee_master whose DEPTNO is 10

```sql
DELETE FROM Employee_master
WHERE DEPTNO = 10;
```

---

## 3. Update 10% increase in salary of DEPTNO 20 in Employee_master

```sql
UPDATE Employee_master
SET SAL = SAL + (SAL * 0.10)
WHERE DEPTNO = 20;
```

---

## 4. Alter SAL column size to 10,2 in Employee_master

```sql
ALTER TABLE Employee_master
MODIFY SAL DECIMAL(10,2);
```

---

## 5. Drop Employee_master Table

```sql
DROP TABLE Employee_master;
```

---

## Conclusion

The EMPLOYEE and DEPARTMENT tables were created successfully with given constraints.  
Data was inserted properly and required DDL and DML operations were performed successfully.
