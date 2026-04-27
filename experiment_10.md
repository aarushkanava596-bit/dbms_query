# 2CSE18_2410030134:

### 1. Display employees from dept 10 earning more than ANY employee of other departments.
~~~sql
SELECT ENAME
FROM EMPLOYEE
WHERE DEPTNO=10
AND SAL > ANY (SELECT SAL FROM EMPLOYEE WHERE DEPTNO<>10);
~~~

### 2. Display employees from dept 10 earning more than ALL employees of other departments.
~~~sql
SELECT ENAME
FROM EMPLOYEE
WHERE DEPTNO=10
AND SAL > ALL (SELECT SAL FROM EMPLOYEE WHERE DEPTNO<>10);
~~~

### 3. Display details of employees working in SALES department
~~~sql
SELECT *
FROM EMPLOYEE
WHERE DEPTNO = (SELECT DEPTNO FROM DEPARTMENT WHERE DNAME='SALES');
~~~

### 4. Display employees who are not managers.
~~~sql
SELECT ENAME
FROM EMPLOYEE
WHERE JOB <> 'MANAGER';
~~~

### 5. Display employees whose manager is JONES.
~~~sql
SELECT E.ENAME
FROM EMPLOYEE E
JOIN EMPLOYEE M ON E.MGR=M.EMPNO
WHERE M.ENAME='JONES';
~~~

### 6. Display employees working in SALES department.
~~~sql
SELECT ENAME
FROM EMPLOYEE
WHERE DEPTNO = (SELECT DEPTNO FROM DEPARTMENT WHERE DNAME='SALES');
~~~

### 7. Display employee name, department, salary and commission where salary is between 2000 and 5000 and location is CHICAGO.
~~~sql
SELECT E.ENAME, D.DNAME, E.SAL, E.COMM
FROM EMPLOYEE E
JOIN DEPARTMENT D ON E.DEPTNO=D.DEPTNO
WHERE E.SAL BETWEEN 2000 AND 5000
AND D.LOC='CHICAGO';
~~~

### 8. Display employees whose salary is greater than their manager.
~~~sql
SELECT E.ENAME
FROM EMPLOYEE E
JOIN EMPLOYEE M ON E.MGR=M.EMPNO
WHERE E.SAL > M.SAL;
~~~

### 9. Display employees working in same department as their manager.
~~~sql
SELECT E.ENAME
FROM EMPLOYEE E
JOIN EMPLOYEE M ON E.MGR=M.EMPNO
WHERE E.DEPTNO = M.DEPTNO;
~~~

### 10. Display grade and employee name for dept 10 or 30, excluding grade 4 and joined before 31-Dec-82.
~~~sql
SELECT GRADE, ENAME
FROM EMPLOYEE
WHERE DEPTNO IN (10,30)
AND GRADE <> 4
AND HIREDATE < '31-DEC-82';
~~~
