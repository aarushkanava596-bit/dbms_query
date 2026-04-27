# 2CSE18_2410030134;

### 1. Delete employees who joined before 31-Dec-82 and belong to departments located in ‘New York’ or ‘Chicago’.
~~~sql
DELETE FROM EMPLOYEE
WHERE HIREDATE < '31-DEC-82'
AND DEPTNO IN (
    SELECT DEPTNO 
    FROM DEPARTMENT 
    WHERE LOC IN ('NEW YORK','CHICAGO')
);
~~~

### 2. Display employee name, job, department name and location for all managers.
~~~sql
SELECT E.ENAME, E.JOB, D.DNAME, D.LOC
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO
WHERE E.JOB = 'MANAGER';
~~~

### 3. Display name and salary of FORD if his salary is equal to highest salary.
~~~sql
SELECT ENAME, SAL
FROM EMPLOYEE
WHERE ENAME = 'FORD'
AND SAL = (SELECT MAX(SAL) FROM EMPLOYEE);
~~~

### 4. Find top 5 earners of the company.
~~~sql
SELECT *
FROM EMPLOYEE
ORDER BY SAL DESC
FETCH FIRST 5 ROWS ONLY;
~~~

### 5. Display employees getting highest salary.
~~~sql
SELECT ENAME
FROM EMPLOYEE
WHERE SAL = (SELECT MAX(SAL) FROM EMPLOYEE);
~~~

### 6. Display employees whose salary is equal to average of maximum and minimum salary.
~~~sql
SELECT ENAME
FROM EMPLOYEE
WHERE SAL = (
    SELECT (MAX(SAL) + MIN(SAL)) / 2 
    FROM EMPLOYEE
);
~~~

### 7. Display department names where at least 3 employees are working.
~~~sql
SELECT D.DNAME
FROM DEPARTMENT D
WHERE (
    SELECT COUNT(*) 
    FROM EMPLOYEE E 
    WHERE E.DEPTNO = D.DEPTNO
) >= 3;
~~~

### 8. Display managers whose salary is greater than average salary of company.
~~~sql
SELECT ENAME
FROM EMPLOYEE
WHERE JOB = 'MANAGER'
AND SAL > (SELECT AVG(SAL) FROM EMPLOYEE);
~~~

### 9. Display managers whose salary is greater than average salary of their employees.
~~~sql
SELECT M.ENAME
FROM EMPLOYEE M
WHERE M.JOB = 'MANAGER'
AND M.SAL > (
    SELECT AVG(E.SAL)
    FROM EMPLOYEE E
    WHERE E.MGR = M.EMPNO
);
~~~

### 10. Display employee name, salary, commission and net pay (SAL+COMM) where net pay is greater than or equal to any employee salary.
~~~sql
SELECT ENAME, SAL, COMM, (SAL + NVL(COMM,0)) AS NET_PAY
FROM EMPLOYEE
WHERE (SAL + NVL(COMM,0)) >= ANY (
    SELECT SAL FROM EMPLOYEE
);
~~~
