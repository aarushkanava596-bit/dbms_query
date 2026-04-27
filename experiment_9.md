# 2CSE18_2410030134:

### 1. Display the name of employee who earns highest salary.
~~~sql
SELECT ENAME
FROM EMPLOYEE
WHERE SAL = (SELECT MAX(SAL) FROM EMPLOYEE);
~~~

### 2. Display employee number and name of clerk earning highest salary among clerks.
~~~sql
SELECT EMPNO, ENAME
FROM EMPLOYEE
WHERE JOB='CLERK'
AND SAL = (SELECT MAX(SAL) FROM EMPLOYEE WHERE JOB='CLERK');
~~~

### 3. Display salesman earning more than highest salary of any clerk.
~~~sql
SELECT ENAME
FROM EMPLOYEE
WHERE JOB='SALESMAN'
AND SAL > (SELECT MAX(SAL) FROM EMPLOYEE WHERE JOB='CLERK');
~~~

### 4. Display clerks earning more than JAMES but less than SCOTT.
~~~sql
SELECT ENAME
FROM EMPLOYEE
WHERE JOB='CLERK'
AND SAL > (SELECT SAL FROM EMPLOYEE WHERE ENAME='JAMES')
AND SAL < (SELECT SAL FROM EMPLOYEE WHERE ENAME='SCOTT');
~~~

### 5. Display employees earning more than JAMES or SCOTT.
~~~sql
SELECT ENAME
FROM EMPLOYEE
WHERE SAL > (SELECT SAL FROM EMPLOYEE WHERE ENAME='JAMES')
OR SAL > (SELECT SAL FROM EMPLOYEE WHERE ENAME='SCOTT');
~~~

### 6. Display employees earning highest salary in their respective departments.
~~~sql
SELECT ENAME, DEPTNO
FROM EMPLOYEE E
WHERE SAL = (SELECT MAX(SAL) FROM EMPLOYEE WHERE DEPTNO = E.DEPTNO);
~~~

### 7. Display employees earning highest salary in their job group.
~~~sql
SELECT ENAME, JOB
FROM EMPLOYEE E
WHERE SAL = (SELECT MAX(SAL) FROM EMPLOYEE WHERE JOB = E.JOB);
~~~

### 8. Display employees working in ACCOUNTING department.
~~~sql
SELECT ENAME
FROM EMPLOYEE
WHERE DEPTNO = (SELECT DEPTNO FROM DEPARTMENT WHERE DNAME='ACCOUNTING');
~~~

### 9. Display employees working in CHICAGO.
~~~sql
SELECT ENAME
FROM EMPLOYEE
WHERE DEPTNO = (SELECT DEPTNO FROM DEPARTMENT WHERE LOC='CHICAGO');
~~~

### 10. Display job groups having total salary greater than maximum salary of managers.
~~~sql
SELECT JOB
FROM EMPLOYEE
GROUP BY JOB
HAVING SUM(SAL) > (SELECT MAX(SAL) FROM EMPLOYEE WHERE JOB='MANAGER');
~~~
