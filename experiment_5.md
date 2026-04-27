# USE 2cse18_2410030134;
~~~sql
SELECT * FROM EMPLOYEE;
~~~

### 1. Display the total number of employee working in the company.
~~~sql
SELECT COUNT(*) AS TOTAL_COUNT FROM EMPLOYEE;
~~~

### 2. Display the total salary being paid to all employees.
~~~sql
SELECT SUM(SAL) AS TOTAL_SALARY FROM EMPLOYEE;
~~~

### 3. Display the maximum salary from employee table.
~~~sql
SELECT MAX(SAL) AS MAXIMUM_SALARY FROM EMPLOYEE;
~~~

### 4.Display the minimum salary from employee table.
~~~sql
SELECT MIN(SAL) AS MINIMUM_SALARY FROM EMPLOYEE;
~~~

### 5. Display the average salary from employee table
~~~sql
SELECT AVG(SAL) AS AVERAGE_SALARY FROM EMPLOYEE;
~~~

### 6. Display the maximum salary being paid to clerk.
~~~sql
SELECT MAX(SAL) AS CLERK_MAX_SALARY FROM EMPLOYEE 
WHERE JOB = 'CLERK';
~~~

### 7. Display the maximum salary being paid in dept no 20.
~~~sql
SELECT MAX(SAL) AS MAXIMUM_SALARY FROM EMPLOYEE 
WHERE DEPTNO = 20;
~~~

### 8. Display the minimum salary paid to any salesman.
~~~sql
SELECT MIN(SAL) AS MIN_SALARY FROM EMPLOYEE 
WHERE JOB = 'SALEMAN';
~~~

### 9. Display the average salary drawn by managers.
~~~sql
SELECT AVG(SAL) AS AVERAGE_SALARY FROM EMPLOYEE
WHERE JOB = 'MANAGER';
~~~

### 10. Display the total salary drawn by analyst working in dept no 40.
~~~sql
SELECT SUM(SAL) AS ANALYST_SALARY FROM EMPLOYEE
WHERE DEPTNO = 40
AND 
JOB = 'ANALYST'; 
~~~

### 11. Display the names of the employee in Uppercase.
~~~sql
SELECT UPPER(ENAME) AS UPPER_EMPLOYEE_NAME 
FROM EMPLOYEE;
~~~

### 12. Display the names of the employee in Lowercase.
~~~sql
SELECT LOWER(ENAME) AS LOWER_EMPLOYEE_NAME 
FROM EMPLOYEE;
~~~

### 13. Display the names of the employee in Proper case.
~~~sql
SELECT CONCAT(UPPER(LEFT(ENAME,1)), LOWER(SUBSTRING(ENAME,2))) AS PROPER_CASE
FROM EMPLOYEE;
~~~

### 14. Display the length of Your name using appropriate function.
~~~sql
SELECT LENGTH('AYUSH') AS TOTAL_LENGTH;
~~~

### 15. Display the length of all the employee names.
~~~sql
SELECT ENAME, LENGTH(ENAME) AS NAME_LENGTH FROM EMPLOYEE;
~~~
