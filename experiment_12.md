# 2CSE18_2410030134

### 1. Display employees whose salary is less than their manager but more than salary of any other managers.
~~~sql
SELECT E.ENAME
FROM EMPLOYEE E
JOIN EMPLOYEE M ON E.MGR = M.EMPNO
WHERE E.SAL < M.SAL
AND E.SAL > ANY (
    SELECT SAL FROM EMPLOYEE WHERE JOB = 'MANAGER'
);
~~~

### 2. Find number of employees whose salary is greater than their manager salary.
~~~sql
SELECT COUNT(*)
FROM EMPLOYEE E
JOIN EMPLOYEE M ON E.MGR = M.EMPNO
WHERE E.SAL > M.SAL;
~~~

### 3. Display managers who are not working under president but under another manager.
~~~sql
SELECT E.ENAME
FROM EMPLOYEE E
JOIN EMPLOYEE M ON E.MGR = M.EMPNO
WHERE E.JOB = 'MANAGER'
AND M.JOB <> 'PRESIDENT';
~~~

### 4. Delete departments where no employee is working.
~~~sql
DELETE FROM DEPARTMENT
WHERE DEPTNO NOT IN (
    SELECT DISTINCT DEPTNO FROM EMPLOYEE
);
~~~

### 5. Delete employees whose department does not exist in department table.
~~~sql
DELETE FROM EMPLOYEE
WHERE DEPTNO NOT IN (
    SELECT DEPTNO FROM DEPARTMENT
);
~~~

### 6. Display employees whose salary is not within any grade (from SALGRADE table)
~~~sql
SELECT ENAME
FROM EMPLOYEE
WHERE SAL NOT BETWEEN ANY (
    SELECT LOWSAL AND HIGHSAL FROM SALGRADE
);
~~~

### 7. Display employees whose net pay (SAL+COMM) is highest in company.
~~~sql
SELECT ENAME, SAL, COMM
FROM EMPLOYEE
WHERE (SAL + NVL(COMM,0)) = (
    SELECT MAX(SAL + NVL(COMM,0)) FROM EMPLOYEE
);
~~~

### 8. Display employees working in SALES or RESEARCH department.
~~~sql
SELECT E.ENAME
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO
WHERE D.DNAME IN ('SALES','RESEARCH');
~~~

### 9. Display grade of JONES.
~~~sql
SELECT GRADE
FROM SALGRADE
WHERE (
    SELECT SAL FROM EMPLOYEE WHERE ENAME='JONES'
) BETWEEN LOSAL AND HISAL;
~~~

### 10. Display department name whose number of characters equals number of employees in that department.
~~~sql
SELECT DNAME
FROM DEPARTMENT D
WHERE LENGTH(DNAME) = (
    SELECT COUNT(*)
    FROM EMPLOYEE E
    WHERE E.DEPTNO = D.DEPTNO
);
~~~
