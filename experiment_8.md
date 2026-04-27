# 2CSE18_24110030134;


### 1. Display all employees with their department name.
~~~sql
SELECT E.ENAME, D.DNAME
FROM EMPLOYEE E
JOIN DEPARTMENT D
ON E.DEPTNO = D.DEPTNO;
~~~

### 2. Display employees whose manager is ‘JONES’, along with manager name.
~~~sql
SELECT E.ENAME AS EMPLOYEE, M.ENAME AS MANAGER
FROM EMPLOYEE E
JOIN EMPLOYEE M
ON E.MGR = M.EMPNO
WHERE M.ENAME = 'JONES';
~~~

### 3. Display employee name, job, department name, manager name.
~~~sql
SELECT E.ENAME, E.JOB, D.DNAME, M.ENAME AS MANAGER
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO
LEFT JOIN EMPLOYEE M ON E.MGR = M.EMPNO;
~~~

### 4. List employees except clerks with salary sorted highest first.
~~~sql
SELECT E.ENAME, E.JOB, E.SAL, D.DNAME
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO
WHERE E.JOB <> 'CLERK'
ORDER BY E.SAL DESC;
~~~

### 5. Display employee name, job, and manager (include employees without manager).
~~~sql
SELECT E.ENAME, E.JOB, M.ENAME AS MANAGER
FROM EMPLOYEE E
LEFT JOIN EMPLOYEE M
ON E.MGR = M.EMPNO;
~~~

### 6. List employee name, job, annual salary, dept no and dept name who earn 36000 annually or are not clerks.
~~~sql
SELECT E.ENAME, E.JOB, (E.SAL*12) AS ANNUAL_SAL,
       E.DEPTNO, D.DNAME
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO
WHERE (E.SAL*12) = 36000 OR E.JOB <> 'CLERK';
~~~
### 7. List employee name, job, annual salary, dept no and dept name who earn 30000 annually and are not clerks.
~~~sql
SELECT E.ENAME, E.JOB, (E.SAL*12) AS ANNUAL_SAL,
       E.DEPTNO, D.DNAME
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO
WHERE (E.SAL*12) = 30000 AND E.JOB <> 'CLERK';
~~~

### 8. List employee name and number along with their manager’s name and display 'NO MANAGER' if none.
~~~sql
SELECT E.EMPNO, E.ENAME,
       NVL(M.ENAME, 'NO MANAGER') AS MANAGER_NAME
FROM EMPLOYEE E
LEFT JOIN EMPLOYEE M ON E.MGR = M.EMPNO;
~~~

### 9. Display department name, department number and total salary for each department.
~~~sql
SELECT D.DNAME, D.DEPTNO, SUM(E.SAL) AS TOTAL_SAL
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO
GROUP BY D.DNAME, D.DEPTNO;
~~~

### 10. Display employee number, name and location of the department in which they are working.
~~~sql
SELECT E.EMPNO, E.ENAME, D.LOC
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO = D.DEPTNO;
~~~
