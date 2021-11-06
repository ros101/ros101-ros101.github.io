---
layout: notes
---
# Assignment

## To Begin...
In the new terminal window, type mysql into the command line and a new MariaDB> client for MySQL will start (the MariaDB client is much faster than MySQL).

### Running mysql statements
The MariaDB client is enabled with all the sql databases and table editing and reading privileges to enable you carry out this assessment.

### For this Assessment
There are two tables available in the database COMPANY1 which should be used for this assessment activity. Type the command

```
USE COMPANY1;
```
to ensure you are in the right database before carrying out the assessment instructions on page 3.

## The Tables

### The EMP Table
The employees table, called EMP, contains the attributes described below:

- EMPNO is a unique employee number, it is the primary key of the employee table.
- ENAME stores the employee’s name.
- The JOB attribute stores the name of the job of the employee.
- The MGR attribute contains the employee number of the employee who manages that employee, if the employee has no manager, then the MGR column for that employee is left set to null.
- The HIREDATE column stores the date on which the employee joined the Company.
- The SAL column contains the details of employee salaries.
- The COMM attribute stores values of commission paid to employees, not all employees receive commission, in which case the COMM field is set to null.
- The DEPTNO column stores the department number of the department in which each employee is based. This data item acts as a foreign key, linking the employee details stored in the EMP table with the details of departments in which employees work, which are stored in the DEPT table.

The data in the EMP table contains the following 14 rows:

|EMPNO	|ENAME	|JOB	    |MGR	|HIREDATE	|SAL	|COMM	|DEPTNO
| ---   | ---   | ---       | ---   | ---       | ---   | ---   | ---  
|7369	|SMITH	|CLERK	    |7902	|1980-12-17	|800	|       |20
|7499	|ALLEN	|SALESMAN	|7698	|1981-02-20	|1600	|300	|30
|7521	|WARD	|SALESMAN	|7698	|1981-02-22	|1250	|500	|30
|7566	|JONES	|MANAGER	|7839	|1981-04-02	|2975	|       |20
|7654	|MARTIN	|SALESMAN	|7698	|1981-09-28	|1250	|1400	|30
|7698	|BLAKE	|MANAGER	|7839	|1981-05-01	|2850	|	    |30
|7782	|CLARK	|MANAGER	|7839	|1981-06-09	|2450	|	    |10
|7788	|SCOTT	|ANALYST	|7566	|1987-04-19	|3000	|	    |20
|7839	|KING	|PRESIDENT	|	    |1981-11-17	|5000	|       |10
|7844	|TURNER	|SALESMAN	|7698	|1981-09-08	|1500	|0	    |30
|7876	|ADAMS	|CLERK	    |7788	|1987-05-23	|1100	|	    |20
|7900	|JAMES	|CLERK	    |7698	|1981-12-03	|950	|   	|30
|7902	|FORD	|ANALYST	|7566	|1981-12-03	|3000	|	    |20
|7934	|MILLER	|CLERK	    |7782	|1982-01-23	|1300	|	    |10

### The DEPT Table
The DEPT table contains just 3 columns as follows:

- DEPTNO: which is the primary key containing the department numbers used to identify each department.
- DNAME: the name of each department
- LOC: the location where each department is based.

The DEPT table contains the following 4 rows of data:

|DEPTNO	|DNAME	    |LOC
| ---   | ---       | ---
|10	    |ACCOUNTING	|NEW YORK
|20	    |RESEARCH	|DALLAS
|30	    |SALES	    |CHICAGO
|40	    |OPERATIONS	|BOSTON

---

# Solution

## start
```
USE COMPANY1;
```
It opens the correct database.

---

## List all Employees whose salary is between 1,000 AND 2,000. Show the Employee Name, Department and Salary.

### simple solution

```
SELECT ENAME, DNAME, SAL FROM EMP E, DEPT D WHERE E.DEPTNO=D.DEPTNO AND SAL>=1000 AND SAL<=2000;
+--------+------------+---------+
| ENAME  | DNAME      | SAL     |
+--------+------------+---------+
| ALLEN  | SALES      | 1600.00 |
| WARD   | SALES      | 1250.00 |
| MARTIN | SALES      | 1250.00 |
| TURNER | SALES      | 1500.00 |
| ADAMS  | RESEARCH   | 1100.00 |
| MILLER | ACCOUNTING | 1300.00 |
+--------+------------+---------+
6 rows in set (0.001 sec)
```
This is the most obvious solution. When integrated in a software, it is simpler to keep the original column names to avoid inconsistencies.

### alternative with better formatting

```
SELECT ENAME AS 'Employee Name', DNAME AS 'Department Name', SAL AS 'Salary' FROM EMP E, DEPT D WHERE E.DEPTNO=D.DEPTNO AND SAL>=1000 AND SAL<=2000;
+---------------+-----------------+---------+
| Employee Name | Department Name | Salary  |
+---------------+-----------------+---------+
| ALLEN         | SALES           | 1600.00 |
| WARD          | SALES           | 1250.00 |
| MARTIN        | SALES           | 1250.00 |
| TURNER        | SALES           | 1500.00 |
| ADAMS         | RESEARCH        | 1100.00 |
| MILLER        | ACCOUNTING      | 1300.00 |
+---------------+-----------------+---------+
```
Uncommon, but sometimes desirable, columns can be formatted with a more expressive name.

### alternative with BETWEEN

```
SELECT ENAME AS 'Employee Name', DNAME AS 'Department Name', SAL AS 'Salary' FROM EMP E, DEPT D WHERE E.DEPTNO=D.DEPTNO AND SAL BETWEEN 1000 AND 2000;
```
*Between* is an alternative and more expressive way to replace "*a <= field <= b*"

## alternative with sorting by Employee Name then Department Name then Salary

```
SELECT ENAME, DNAME, SAL FROM EMP E, DEPT D WHERE E.DEPTNO=D.DEPTNO AND SAL BETWEEN 1000 AND 2000 ORDER BY ENAME,DNAME,SAL;
+--------+------------+---------+
| ENAME  | DNAME      | SAL     |
+--------+------------+---------+
| ADAMS  | RESEARCH   | 1100.00 |
| ALLEN  | SALES      | 1600.00 |
| MARTIN | SALES      | 1250.00 |
| MILLER | ACCOUNTING | 1300.00 |
| TURNER | SALES      | 1500.00 |
| WARD   | SALES      | 1250.00 |
+--------+------------+---------+
6 rows in set (0.001 sec)
```
Sorting so few records is probably a responsibility of a GUI, but it may be useful to do it on the database for larger sets of data.

---

## Count the number of people in department 30 who receive a salary and the number of people who receive a commission.

This specification suffers of ambiguity: does the user expect that a salary/commission = 0 is the same as a salary/commission = NULL?

I will analyze both cases:

* NULL = 0: only positive values count as receiving salary/commission
* 0 = receiving: only NULL values mean that the employee does not receive salary/commission

### simple "lazy" solution (NULL = 0)

```
SELECT COUNT(*) AS TOTAL FROM EMP WHERE DEPTNO=30 AND SAL>0;
+-------+
| TOTAL |
+-------+
|     6 |
+-------+
1 row in set (0.000 sec)

SELECT COUNT(*) AS TOTAL FROM EMP WHERE DEPTNO=30 AND COMM>0;
+-------+
| TOTAL |
+-------+
|     3 |
+-------+
1 row in set (0.000 sec)
```
This would be my preferred implementation if I had to implement a software reporting the two numbers separately.

### alternative "lazy" solution (0 = receiving)
```
SELECT COUNT(*) AS TOTAL FROM EMP WHERE DEPTNO=30 AND SAL IS NOT NULL;
+-------+
| TOTAL |
+-------+
|     6 |
+-------+
1 row in set (0.000 sec)

SELECT COUNT(*) AS TOTAL FROM EMP WHERE DEPTNO=30 AND COMM IS NOT NULL;
+-------+
| TOTAL |
+-------+
|     4 |
+-------+
1 row in set (0.000 sec)
```
If having a salary/commission = 0 is different from having NULL, the above queries are the ones that should be used.

### improved overview (NULL = 0)

```
SELECT 'with salary' AS PAYMENT,COUNT(*) AS TOTAL FROM EMP WHERE DEPTNO=30 AND SAL>0
UNION
SELECT 'with commission' AS PAYMENT,COUNT(*) AS TOTAL FROM EMP WHERE DEPTNO=30 AND COMM>0
UNION
SELECT 'with salary, no commission' AS PAYMENT,COUNT(*) AS TOTAL FROM EMP WHERE DEPTNO=30 AND SAL>0  AND COMM=0
UNION
SELECT 'with commission, no salary' AS PAYMENT,COUNT(*) AS TOTAL FROM EMP WHERE DEPTNO=30 AND SAL=0  AND COMM>0;
+----------------------------+-------+
| PAYMENT                    | TOTAL |
+----------------------------+-------+
| with salary                |     6 |
| with commission            |     3 |
| with salary, no commission |     1 |
| with commission, no salary |     0 |
+----------------------------+-------+
4 rows in set (0.001 sec)
```
This query is better suited if the requirement is to provide a complete overview with a single query.

### improved overview (0 = receiving)
```
SELECT 'with salary' AS PAYMENT,COUNT(*) AS TOTAL FROM EMP WHERE DEPTNO=30 AND SAL IS NOT NULL
UNION
SELECT 'with commission' AS PAYMENT,COUNT(*) AS TOTAL FROM EMP WHERE DEPTNO=30 AND COMM IS NOT NULL
UNION
SELECT 'with salary, no commission' AS PAYMENT,COUNT(*) AS TOTAL FROM EMP WHERE DEPTNO=30 AND SAL IS NOT NULL AND COMM IS NULL
UNION
SELECT 'with commission, no salary' AS PAYMENT,COUNT(*) AS TOTAL FROM EMP WHERE DEPTNO=30 AND SAL IS NULL  AND COMM IS NOT NULL;
+----------------------------+-------+
| PAYMENT                    | TOTAL |
+----------------------------+-------+
| with salary                |     6 |
| with commission            |     4 |
| with salary, no commission |     2 |
| with commission, no salary |     0 |
+----------------------------+-------+
4 rows in set (0.000 sec)
```
If having a salary/commission = 0 is different from having NULL, the above queries are the ones that should be used.

This is the execution plan:

```
+------+--------------+----------------+------+---------------+------+---------+------+------+--------+----------+------------+-------------+
| id   | select_type  | table          | type | possible_keys | key  | key_len | ref  | rows | r_rows | filtered | r_filtered | Extra       |
+------+--------------+----------------+------+---------------+------+---------+------+------+--------+----------+------------+-------------+
|    1 | PRIMARY      | EMP            | ALL  | NULL          | NULL | NULL    | NULL | 14   | 14.00  |   100.00 |      42.86 | Using where |
|    2 | UNION        | EMP            | ALL  | NULL          | NULL | NULL    | NULL | 14   | 14.00  |   100.00 |      21.43 | Using where |
|    3 | UNION        | EMP            | ALL  | NULL          | NULL | NULL    | NULL | 14   | 14.00  |   100.00 |       7.14 | Using where |
|    4 | UNION        | EMP            | ALL  | NULL          | NULL | NULL    | NULL | 14   | 14.00  |   100.00 |       0.00 | Using where |
| NULL | UNION RESULT | <union1,2,3,4> | ALL  | NULL          | NULL | NULL    | NULL | NULL | 4.00   |     NULL |       NULL |             |
+------+--------------+----------------+------+---------------+------+---------+------+------+--------+----------+------------+-------------+
```

### alternative with virtual table (NULL = 0)
```
WITH DEP30 AS (SELECT SAL,COMM,DEPTNO FROM EMP WHERE DEPTNO=30)
SELECT 'with salary' AS PAYMENT,COUNT(*) AS TOTAL FROM DEP30 WHERE SAL>0
UNION
SELECT 'with commission' AS PAYMENT,COUNT(*) AS TOTAL FROM DEP30 WHERE COMM>0
UNION
SELECT 'with salary, no commission' AS PAYMENT,COUNT(*) AS TOTAL FROM DEP30 WHERE SAL>0 AND COMM=0
UNION
SELECT 'with commission, no salary' AS PAYMENT,COUNT(*) AS TOTAL FROM DEP30 WHERE SAL=0 AND COMM>0
```
this creates a virtual table DEP30 used by the other unions.

### alternative with virtual table (0 = receiving)
```
WITH DEP30 AS (SELECT SAL,COMM,DEPTNO FROM EMP WHERE DEPTNO=30)
SELECT 'with salary' AS PAYMENT,COUNT(*) AS TOTAL FROM DEP30 WHERE SAL IS NOT NULL
UNION
SELECT 'with commission' AS PAYMENT,COUNT(*) AS TOTAL FROM DEP30 WHERE COMM IS NOT NULL
UNION
SELECT 'with salary, no commission' AS PAYMENT,COUNT(*) AS TOTAL FROM DEP30 WHERE SAL IS NOT NULL AND COMM IS NULL
UNION
SELECT 'with commission, no salary' AS PAYMENT,COUNT(*) AS TOTAL FROM DEP30 WHERE SAL IS NULL  AND COMM IS NOT NULL;
```
this creates a virtual table DEP30 used by the other unions.

The execution plan is almost identical to the alternative without virtual table. This approach can be convenient if the virtual table has complex conditions that must be repeated.

```
+------+--------------+----------------+------+---------------+------+---------+------+------+--------+----------+------------+-------------+
| id   | select_type  | table          | type | possible_keys | key  | key_len | ref  | rows | r_rows | filtered | r_filtered | Extra       |
+------+--------------+----------------+------+---------------+------+---------+------+------+--------+----------+------------+-------------+
|    1 | PRIMARY      | EMP            | ALL  | NULL          | NULL | NULL    | NULL | 14   | 14.00  |   100.00 |      42.86 | Using where |
|    3 | UNION        | EMP            | ALL  | NULL          | NULL | NULL    | NULL | 14   | 14.00  |   100.00 |      28.57 | Using where |
|    4 | UNION        | EMP            | ALL  | NULL          | NULL | NULL    | NULL | 14   | 14.00  |   100.00 |      14.29 | Using where |
|    5 | UNION        | EMP            | ALL  | NULL          | NULL | NULL    | NULL | 14   | 14.00  |   100.00 |       0.00 | Using where |
| NULL | UNION RESULT | <union1,3,4,5> | ALL  | NULL          | NULL | NULL    | NULL | NULL | 4.00   |     NULL |       NULL |             |
+------+--------------+----------------+------+---------------+------+---------+------+------+--------+----------+------------+-------------+
```

---

## Find the name and salary of employees in Dallas.

```
SELECT ENAME, SAL FROM EMP E, DEPT D WHERE E.DEPTNO=D.DEPTNO AND D.LOC='DALLAS';
+-------+---------+
| ENAME | SAL     |
+-------+---------+
| SMITH |  800.00 |
| JONES | 2975.00 |
| SCOTT | 3000.00 |
| ADAMS | 1100.00 |
| FORD  | 3000.00 |
+-------+---------+
5 rows in set (0.001 sec)
```
This is a simple solution. Alternatives can have aliases in the column names.

---

## List all departments that do not have any employees.

### simple solution with nested query

```
SELECT * FROM DEPT WHERE DEPTNO NOT IN (SELECT DEPTNO FROM EMP GROUP BY DEPTNO);
+--------+------------+--------+
| DEPTNO | DNAME      | LOC    |
+--------+------------+--------+
|     40 | OPERATIONS | BOSTON |
+--------+------------+--------+
1 row in set (0.001 sec)
```
This query is easy to read. Unfortunately the IN operator and the nested query have a negative impact on performances (with large datasets).

### alternative

```
SELECT * FROM DEPT WHERE DEPTNO NOT IN (SELECT DISTINCT(DEPTNO) FROM EMP);
```
This is equivalent to the previous solution as shown by the execution plan.

```
ANALYZE SELECT * FROM DEPT WHERE DEPTNO NOT IN (SELECT DEPTNO FROM EMP GROUP BY DEPTNO);
+------+--------------+-------+------+---------------+------+---------+------+------+--------+----------+------------+-------------+
| id   | select_type  | table | type | possible_keys | key  | key_len | ref  | rows | r_rows | filtered | r_filtered | Extra       |
+------+--------------+-------+------+---------------+------+---------+------+------+--------+----------+------------+-------------+
|    1 | PRIMARY      | DEPT  | ALL  | NULL          | NULL | NULL    | NULL | 4    | 4.00   |   100.00 |      25.00 | Using where |
|    2 | MATERIALIZED | EMP   | ALL  | NULL          | NULL | NULL    | NULL | 14   | 14.00  |   100.00 |     100.00 |             |
+------+--------------+-------+------+---------------+------+---------+------+------+--------+----------+------------+-------------+
2 rows in set (0.001 sec)

MariaDB [COMPANY1]> ANALYZE SELECT * FROM DEPT WHERE DEPTNO NOT IN (SELECT DISTINCT(DEPTNO) FROM EMP);
+------+--------------+-------+------+---------------+------+---------+------+------+--------+----------+------------+-------------+
| id   | select_type  | table | type | possible_keys | key  | key_len | ref  | rows | r_rows | filtered | r_filtered | Extra       |
+------+--------------+-------+------+---------------+------+---------+------+------+--------+----------+------------+-------------+
|    1 | PRIMARY      | DEPT  | ALL  | NULL          | NULL | NULL    | NULL | 4    | 4.00   |   100.00 |      25.00 | Using where |
|    2 | MATERIALIZED | EMP   | ALL  | NULL          | NULL | NULL    | NULL | 14   | 14.00  |   100.00 |     100.00 |             |
+------+--------------+-------+------+---------------+------+---------+------+------+--------+----------+------------+-------------+
2 rows in set (0.000 sec)
```
The execution plan also shows that the nested query creates a temporary table (MATERIALIZED) that is used to get the final result.

### alternative without nested query

```
SELECT D.* FROM DEPT D LEFT JOIN EMP E ON E.DEPTNO=D.DEPTNO WHERE E.DEPTNO IS NULL;
+--------+------------+--------+
| DEPTNO | DNAME      | LOC    |
+--------+------------+--------+
|     40 | OPERATIONS | BOSTON |
+--------+------------+--------+
1 row in set (0.000 sec)
```
This query may be more efficient with large datasets because it avoid the nested query.

```
+------+-------------+-------+-------+---------------+---------+---------+------+------+--------+----------+------------+-------------------------------------------------+
| id   | select_type | table | type  | possible_keys | key     | key_len | ref  | rows | r_rows | filtered | r_filtered | Extra                                           |
+------+-------------+-------+-------+---------------+---------+---------+------+------+--------+----------+------------+-------------------------------------------------+
|    1 | SIMPLE      | D     | index | NULL          | PRIMARY | 1       | NULL | 4    | 4.00   |   100.00 |     100.00 | Using index                                     |
|    1 | SIMPLE      | E     | ALL   | NULL          | NULL    | NULL    | NULL | 14   | 14.00  |   100.00 |       7.14 | Using where; Using join buffer (flat, BNL join) |
+------+-------------+-------+-------+---------------+---------+---------+------+------+--------+----------+------------+-------------------------------------------------+
```
The execution plan is improved: DB uses an index on DEPT, only EMP has a full scan now, and there is no more a temporary table.

---

## List the department number and average salary of each department.

### complete overview with all departments

```
SELECT D.DEPTNO, IFNULL(AVG(SAL),0) FROM DEPT D LEFT JOIN EMP E ON E.DEPTNO=D.DEPTNO GROUP BY D.DEPTNO;
+--------+--------------------+
| DEPTNO | IFNULL(AVG(SAL),0) |
+--------+--------------------+
|     10 |        2916.666667 |
|     20 |        2175.000000 |
|     30 |        1566.666667 |
|     40 |           0.000000 |
+--------+--------------------+
4 rows in set (0.000 sec)
```
It is necessary to perform a LEFT JOIN to include all departments that have no corresponding entry between employees.
Since empty departments would have a NULL in the salary, it is useful to set a default in the SELECT.

### complete overview with a better presentation

```
SELECT D.DEPTNO AS 'Department Number', ROUND(IFNULL(AVG(SAL),0),2) AS 'Average Salary' FROM DEPT D LEFT JOIN EMP E ON E.DEPTNO=D.DEPTNO GROUP BY D.DEPTNO;
+-------------------+----------------+
| Department Number | Average Salary |
+-------------------+----------------+
|                10 |        2916.67 |
|                20 |        2175.00 |
|                30 |        1566.67 |
|                40 |           0.00 |
+-------------------+----------------+
4 rows in set (0.007 sec)
```
It may be useful to round the values for a better presentation. This practice, however, should be avoided if the result is used to perform financial calculations.
