<!-- TOC START -->
**Table of Contents** — 19 subtopics · 294 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [SQL Queries](#sql-queries-87) | 87 |
| 2 | [Keys in DBMS](#keys-in-dbms-34) | 34 |
| 3 | [DBMS Architecture & Features](#dbms-architecture--features-26) | 26 |
| 4 | [ER Diagram & Database Design](#er-diagram--database-design-25) | 25 |
| 5 | [Normalization & Database Design](#normalization--database-design-21) | 21 |
| 6 | [SQL Commands (DDL, DML, DCL, TCL)](#sql-commands-ddl-dml-dcl-tcl-18) | 18 |
| 7 | [Transaction Management & ACID Properties](#transaction-management--acid-properties-14) | 14 |
| 8 | [Relational Data Model & ER Relationships](#relational-data-model--er-relationships-14) | 14 |
| 9 | [Indexing & Query Optimization (B-Tree, B+ Tree)](#indexing--query-optimization-b-tree-b-tree-10) | 10 |
| 10 | [Data Warehousing, Data Mining & Business Intelligence](#data-warehousing-data-mining--business-intelligence-9) | 9 |
| 11 | [Database Backup & Disaster Recovery](#database-backup--disaster-recovery-8) | 8 |
| 12 | [PL/SQL & Database Triggers](#plsql--database-triggers-7) | 7 |
| 13 | [SQL Joins & Operations](#sql-joins--operations-7) | 7 |
| 14 | [Distributed & Parallel Databases](#distributed--parallel-databases-5) | 5 |
| 15 | [Database Design & Data Types](#database-design--data-types-3) | 3 |
| 16 | [NoSQL, NewSQL & Modern Databases](#nosql-newsql--modern-databases-2) | 2 |
| 17 | [Database Connectivity (JDBC)](#database-connectivity-jdbc-2) | 2 |
| 18 | [Relational Keys (Candidate, Super, Primary, Foreign Key)](#relational-keys-candidate-super-primary-foreign-key-1) | 1 |
| 19 | [Indexing in DBMS](#indexing-in-dbms-1) | 1 |

<!-- TOC END -->

---

## SQL Queries (87)

1. Consider the following relation: **Employee(EmpID, Name, Department, Salary)**. Write an SQL query to retrieve the **Department**, the **total number of employees**, and the **average salary** for each department. The output should display one record for each department. [SO IT 25-07-2026]

   Answer: The requirement is one row per department, so `GROUP BY Department` with the aggregate functions `COUNT` and `AVG`.

   Query
   ```sql
   SELECT  Department,
           COUNT(*)     AS Total_Employees,
           AVG(Salary)  AS Average_Salary
   FROM    Employee
   GROUP BY Department;
   ```

   Explanation
   - `GROUP BY Department` collapses all rows of one department into a single group, which is what produces "one record for each department".
   - `COUNT(*)` counts the rows in each group, giving the number of employees.
   - `AVG(Salary)` averages the salary within each group.
   - Every column in the SELECT list must either be in the GROUP BY clause or be inside an aggregate function — Department satisfies the first rule, and the other two satisfy the second.

   Sample data and output
   ```
   Employee
   +-------+--------+------------+--------+
   | EmpID | Name   | Department | Salary |
   +-------+--------+------------+--------+
   |  1    | Karim  | IT         |  50000 |
   |  2    | Rahim  | IT         |  60000 |
   |  3    | Sumi   | HR         |  40000 |
   |  4    | Nabil  | HR         |  45000 |
   |  5    | Jamil  | Accounts   |  55000 |
   +-------+--------+------------+--------+

   Result
   +------------+-----------------+----------------+
   | Department | Total_Employees | Average_Salary |
   +------------+-----------------+----------------+
   | IT         |        2        |     55000      |
   | HR         |        2        |     42500      |
   | Accounts   |        1        |     55000      |
   +------------+-----------------+----------------+
   ```

   Useful variations
   ```sql
   -- rounded average and sorted by department
   SELECT Department,
          COUNT(*)              AS Total_Employees,
          ROUND(AVG(Salary), 2) AS Average_Salary
   FROM   Employee
   GROUP  BY Department
   ORDER  BY Department;

   -- only departments with more than 2 employees
   SELECT Department, COUNT(*), AVG(Salary)
   FROM   Employee
   GROUP  BY Department
   HAVING COUNT(*) > 2;
   ```
   - Note the distinction: `WHERE` filters individual rows `before` grouping; `HAVING` filters groups `after` aggregation.
   - `COUNT(*)` counts every row, while `COUNT(Salary)` would ignore rows where Salary is NULL. AVG also ignores NULLs, so a department where every salary is NULL would return NULL rather than 0.

2. Consider a STUDENTS table with the following attributes: StudentID, Name, Department, Marks (10 Marks)
   * **I.** Write an SQL query to display only StudentID, Name, and Marks for students scoring more than 80 marks.
   * **II.** Write an SQL query to count how many students scored more than 80 marks in each Department. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer:

   Table: `STUDENTS(StudentID, Name, Department, Marks)`

   (I) Display StudentID, Name and Marks for students scoring more than 80
   ```sql
   SELECT  StudentID,
           Name,
           Marks
   FROM    STUDENTS
   WHERE   Marks > 80;
   ```
   - `WHERE` filters individual rows before anything else happens.
   - Only the three requested columns are listed, so `SELECT *` would be wrong here.

   Sample output
   ```
   +-----------+--------+-------+
   | StudentID | Name   | Marks |
   +-----------+--------+-------+
   |     2     | Rahim  |  92   |
   |     5     | Sumi   |  85   |
   |     7     | Nabil  |  88   |
   +-----------+--------+-------+
   ```

   (II) Count how many students scored more than 80 in each Department
   ```sql
   SELECT  Department,
           COUNT(*) AS Students_Above_80
   FROM    STUDENTS
   WHERE   Marks > 80
   GROUP BY Department;
   ```
   - `WHERE Marks > 80` removes the low-scoring rows `first`.
   - `GROUP BY Department` then collapses what remains into one row per department.
   - `COUNT(*)` counts the rows in each group.

   Sample output
   ```
   +------------+-------------------+
   | Department | Students_Above_80 |
   +------------+-------------------+
   | CSE        |         3         |
   | EEE        |         1         |
   | BBA        |         2         |
   +------------+-------------------+
   ```

   The key point in part II
   - The filter must be in `WHERE`, not `HAVING`, because it applies to individual students before grouping.
   - `HAVING` would be used only to filter the groups themselves, for example:
   ```sql
   -- departments where MORE THAN 5 students scored above 80
   SELECT Department, COUNT(*) AS Students_Above_80
   FROM   STUDENTS
   WHERE  Marks > 80          -- filters rows
   GROUP  BY Department
   HAVING COUNT(*) > 5;       -- filters groups
   ```
   - Order of execution in SQL: `FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY`. Remembering this order settles almost every WHERE-versus-HAVING question.

3. **SQL Query: Find department name and Average salary form 2 table Department and Employee.......** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1334 (ET: BUET)]*
   Department table
   Department (dept_id, dept_name)
   Employee table
   Employee (emp_id, emp_name, salary, dept_id)

   Answer: Two tables are involved, so a `JOIN` is needed, then `GROUP BY` to produce one row per department.

   Schema
   ```
   Department (dept_id, dept_name)
   Employee   (emp_id, emp_name, salary, dept_id)
   ```

   Query
   ```sql
   SELECT  d.dept_name,
           AVG(e.salary) AS average_salary
   FROM    Department d
   JOIN    Employee   e ON d.dept_id = e.dept_id
   GROUP BY d.dept_id, d.dept_name;
   ```

   Explanation
   - `JOIN ... ON d.dept_id = e.dept_id` matches each employee to their department through the foreign key.
   - `GROUP BY d.dept_name` produces one row per department; grouping by `d.dept_id` as well is safer, in case two departments share a name.
   - `AVG(e.salary)` averages the salaries within each group.

   Sample data and result
   ```
   Department                    Employee
   +---------+-----------+       +--------+----------+--------+---------+
   | dept_id | dept_name |       | emp_id | emp_name | salary | dept_id |
   +---------+-----------+       +--------+----------+--------+---------+
   |   10    | IT        |       |   1    | Karim    | 50000  |   10    |
   |   20    | HR        |       |   2    | Rahim    | 60000  |   10    |
   |   30    | Accounts  |       |   3    | Sumi     | 40000  |   20    |
   +---------+-----------+       |   4    | Nabil    | 44000  |   20    |
                                 +--------+----------+--------+---------+

   Result
   +-----------+----------------+
   | dept_name | average_salary |
   +-----------+----------------+
   | IT        |     55000      |
   | HR        |     42000      |
   +-----------+----------------+
   ```
   - Note that `Accounts` does not appear, because an inner join drops departments with no employees.

   To include departments that have no employees
   ```sql
   SELECT  d.dept_name,
           AVG(e.salary) AS average_salary
   FROM    Department d
   LEFT JOIN Employee e ON d.dept_id = e.dept_id
   GROUP BY d.dept_id, d.dept_name;
   ```
   - `Accounts` now appears with `NULL` as its average.

   Refinements often asked for
   ```sql
   -- rounded, sorted, and only departments averaging above 45000
   SELECT d.dept_name, ROUND(AVG(e.salary), 2) AS average_salary
   FROM   Department d
   JOIN   Employee e ON d.dept_id = e.dept_id
   GROUP  BY d.dept_id, d.dept_name
   HAVING AVG(e.salary) > 45000
   ORDER  BY average_salary DESC;
   ```

4. **Consider the following database schema, find out the employees whose manager's region is same as the employee working under him.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1363 (ET: BUET)]*
```sql
REGIONS (REGION_ID, REGION_NAME)
COUNTRIES (COUNTRY_ID, COUNTRY_NAME, REGION_ID)
LOCATIONS (LOCATION_ID, STREET_ADDRESS, POSTAL_CODE, CITY, STATE_PROVINCE, COUNTRY_ID)
DEPARTMENTS (DEPARTMENT_ID, DEPARTMENT_NAME, MANAGER_ID, LOCATION_ID)
EMPLOYEES (EMPLOYEE_ID, FIRST_NAME, LAST_NAME, EMAIL, PHONE_NUMBER, HIRE_DATE, JOB_ID, SALARY, COMMISSION_PCT, MANAGER_ID, DEPARTMENT_ID)
JOB_HISTORY (EMPLOYEE_ID, START_DATE, END_DATE, JOB_ID, DEPARTMENT_ID)
JOBS (JOB_ID, JOB_TITLE, MIN_SALARY, MAX_SALARY)
```

   Answer: An employee's region and their manager's region must be compared, so the EMPLOYEES table has to be joined to `itself` (a self join), and each side then traced through DEPARTMENTS, LOCATIONS and COUNTRIES to reach REGIONS.

   The chain of joins needed
   ```
   EMPLOYEES -> DEPARTMENTS -> LOCATIONS -> COUNTRIES -> REGIONS
   ```
   - Each employee reaches a region through this chain, and the manager reaches their own region through the same chain a second time.

   Query
   ```sql
   SELECT  e.EMPLOYEE_ID,
           e.FIRST_NAME || ' ' || e.LAST_NAME AS Employee_Name,
           m.EMPLOYEE_ID                      AS Manager_ID,
           m.FIRST_NAME || ' ' || m.LAST_NAME AS Manager_Name,
           r1.REGION_NAME                     AS Region
   FROM    EMPLOYEES   e
   JOIN    DEPARTMENTS d1 ON e.DEPARTMENT_ID = d1.DEPARTMENT_ID
   JOIN    LOCATIONS   l1 ON d1.LOCATION_ID  = l1.LOCATION_ID
   JOIN    COUNTRIES   c1 ON l1.COUNTRY_ID   = c1.COUNTRY_ID
   JOIN    REGIONS     r1 ON c1.REGION_ID    = r1.REGION_ID

   JOIN    EMPLOYEES   m  ON e.MANAGER_ID    = m.EMPLOYEE_ID     -- self join
   JOIN    DEPARTMENTS d2 ON m.DEPARTMENT_ID = d2.DEPARTMENT_ID
   JOIN    LOCATIONS   l2 ON d2.LOCATION_ID  = l2.LOCATION_ID
   JOIN    COUNTRIES   c2 ON l2.COUNTRY_ID   = c2.COUNTRY_ID
   JOIN    REGIONS     r2 ON c2.REGION_ID    = r2.REGION_ID

   WHERE   r1.REGION_ID = r2.REGION_ID;
   ```

   How it works
   - Alias `e` is the employee and alias `m` is the manager. `e.MANAGER_ID = m.EMPLOYEE_ID` is the `self join` that links them — the same table appearing twice with two different aliases.
   - The first chain (d1, l1, c1, r1) finds the employee's region; the second chain (d2, l2, c2, r2) finds the manager's region.
   - `WHERE r1.REGION_ID = r2.REGION_ID` keeps only the pairs whose regions match. Comparing the IDs rather than the names is safer.

   Shorter equivalent, comparing region IDs only
   ```sql
   SELECT e.EMPLOYEE_ID, e.FIRST_NAME, e.LAST_NAME
   FROM   EMPLOYEES e
   JOIN   DEPARTMENTS d1 ON e.DEPARTMENT_ID = d1.DEPARTMENT_ID
   JOIN   LOCATIONS   l1 ON d1.LOCATION_ID  = l1.LOCATION_ID
   JOIN   COUNTRIES   c1 ON l1.COUNTRY_ID   = c1.COUNTRY_ID
   WHERE  c1.REGION_ID = (
            SELECT c2.REGION_ID
            FROM   EMPLOYEES   m
            JOIN   DEPARTMENTS d2 ON m.DEPARTMENT_ID = d2.DEPARTMENT_ID
            JOIN   LOCATIONS   l2 ON d2.LOCATION_ID  = l2.LOCATION_ID
            JOIN   COUNTRIES   c2 ON l2.COUNTRY_ID   = c2.COUNTRY_ID
            WHERE  m.EMPLOYEE_ID = e.MANAGER_ID
          );
   ```
   - This uses a `correlated subquery` instead of the second join chain. It is easier to read but usually slower.

   Points to note
   - `MANAGER_ID` is a foreign key pointing back into EMPLOYEES, which is what makes the self join necessary.
   - Employees with a `NULL MANAGER_ID` (the top of the hierarchy) are excluded by the inner join; a LEFT JOIN would keep them.
   - The concatenation operator `||` is Oracle and PostgreSQL syntax; MySQL uses `CONCAT(first, ' ', last)` and SQL Server uses `+`.

5. **Database Query related problem.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

   Answer: The specific problem was not printed, so the standard database-query patterns that appear in these examinations are worked through, with the schema used throughout being:
   ```
   Employee   (emp_id, emp_name, salary, dept_id, hire_date, manager_id)
   Department (dept_id, dept_name, location)
   ```

   1. Aggregation with GROUP BY
   ```sql
   -- number of employees and average salary per department
   SELECT d.dept_name, COUNT(*) AS total, AVG(e.salary) AS avg_salary
   FROM   Employee e JOIN Department d ON e.dept_id = d.dept_id
   GROUP  BY d.dept_id, d.dept_name;
   ```

   2. Filtering groups with HAVING
   ```sql
   -- departments whose average salary exceeds 50000
   SELECT d.dept_name, AVG(e.salary) AS avg_salary
   FROM   Employee e JOIN Department d ON e.dept_id = d.dept_id
   GROUP  BY d.dept_id, d.dept_name
   HAVING AVG(e.salary) > 50000;
   ```
   - `WHERE` filters rows before grouping; `HAVING` filters groups afterwards.

   3. Subquery comparing against an aggregate
   ```sql
   -- employees earning more than the overall average
   SELECT emp_name, salary
   FROM   Employee
   WHERE  salary > (SELECT AVG(salary) FROM Employee);
   ```

   4. Correlated subquery
   ```sql
   -- employees earning more than their own department's average
   SELECT e.emp_name, e.salary
   FROM   Employee e
   WHERE  e.salary > (SELECT AVG(e2.salary)
                      FROM   Employee e2
                      WHERE  e2.dept_id = e.dept_id);
   ```

   5. Nth highest value
   ```sql
   -- second highest salary
   SELECT MAX(salary) FROM Employee
   WHERE  salary < (SELECT MAX(salary) FROM Employee);

   -- general Nth highest, using a window function
   SELECT DISTINCT salary FROM (
      SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
      FROM Employee) t
   WHERE rnk = 2;
   ```

   6. Finding duplicates
   ```sql
   SELECT emp_name, COUNT(*) FROM Employee
   GROUP  BY emp_name HAVING COUNT(*) > 1;
   ```

   7. Self join
   ```sql
   -- employees earning more than their manager
   SELECT e.emp_name, m.emp_name AS manager
   FROM   Employee e JOIN Employee m ON e.manager_id = m.emp_id
   WHERE  e.salary > m.salary;
   ```

   8. Outer join to find non-matching rows
   ```sql
   -- departments with no employees
   SELECT d.dept_name
   FROM   Department d LEFT JOIN Employee e ON d.dept_id = e.dept_id
   WHERE  e.emp_id IS NULL;
   ```

   9. Update and delete
   ```sql
   UPDATE Employee SET salary = salary * 1.10 WHERE dept_id = 10;
   DELETE FROM Employee WHERE hire_date < '2010-01-01';
   ```

   10. Ranking within groups
   ```sql
   -- highest-paid employee in each department
   SELECT dept_id, emp_name, salary FROM (
      SELECT dept_id, emp_name, salary,
             RANK() OVER (PARTITION BY dept_id ORDER BY salary DESC) AS r
      FROM Employee) t
   WHERE r = 1;
   ```
   - Order of evaluation to remember: `FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY`. Almost every SQL question is settled by knowing this sequence. <!-- verify -->

6. **From an Employee table. Write SQL statement according to the following question:**
   **(a) Find out the employees who join the same date:** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1438 (ET: BUET)]*
   **(b) Find those employees whose salary greater than 8,000 and Less than 25,000** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*

   Answer:

   (a) Employees who joined on the same date
   - The requirement is to find join dates that occur more than once, then list the employees holding them.

   ```sql
   SELECT  e.emp_id, e.emp_name, e.join_date
   FROM    Employee e
   WHERE   e.join_date IN (
               SELECT join_date
               FROM   Employee
               GROUP  BY join_date
               HAVING COUNT(*) > 1
           )
   ORDER BY e.join_date, e.emp_name;
   ```
   - The inner query finds every date shared by two or more employees; the outer query then returns the employees on those dates.

   Alternative using a self join
   ```sql
   SELECT DISTINCT e1.emp_id, e1.emp_name, e1.join_date
   FROM   Employee e1
   JOIN   Employee e2
          ON e1.join_date = e2.join_date
         AND e1.emp_id   <> e2.emp_id;
   ```
   - `e1.emp_id <> e2.emp_id` prevents a row from matching itself; `DISTINCT` removes the duplicates the join creates.

   Just the dates and how many joined
   ```sql
   SELECT join_date, COUNT(*) AS how_many
   FROM   Employee
   GROUP  BY join_date
   HAVING COUNT(*) > 1;
   ```

   (b) Employees whose salary is greater than 8,000 and less than 25,000
   ```sql
   SELECT  emp_id, emp_name, salary
   FROM    Employee
   WHERE   salary > 8000
     AND   salary < 25000;
   ```

   - If the boundaries are to be `included`, use BETWEEN, which is inclusive at both ends:
   ```sql
   SELECT emp_id, emp_name, salary
   FROM   Employee
   WHERE  salary BETWEEN 8000 AND 25000;
   ```
   - The question says "greater than 8,000 and less than 25,000", so the strict `>` and `<` form above is the exact answer. `BETWEEN 8000 AND 25000` is equivalent to `>= 8000 AND <= 25000`, which is subtly different — a common trap.

   Sample output
   ```
   +--------+----------+--------+
   | emp_id | emp_name | salary |
   +--------+----------+--------+
   |   3    | Sumi     | 12000  |
   |   5    | Nabil    | 18500  |
   |   8    | Jamil    | 24000  |
   +--------+----------+--------+
   ```

7. **Write down the Query for the following table?** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1361 (ET: BUET)]*

| StudentID | StudentName | Age | Department |
|---|---|---|---|
| 1 | Alice | 20 | CSE |
| 2 | Bob | 22 | EEE |
| 3 | Charlie | 21 | CSE |
| 4 | David | 23 | BBA |

* **(i) Shows only students in the CSE department.**
* **(ii) Shows all students sorted by age (highest first).**
* **(iii) Shows how many students are in each department.**

   Answer:

   Table used
   ```
   +-----------+-------------+-----+------------+
   | StudentID | StudentName | Age | Department |
   +-----------+-------------+-----+------------+
   |     1     | Alice       | 20  | CSE        |
   |     2     | Bob         | 22  | EEE        |
   |     3     | Charlie     | 21  | CSE        |
   |     4     | David       | 23  | BBA        |
   +-----------+-------------+-----+------------+
   ```

   (i) Show only students in the CSE department
   ```sql
   SELECT *
   FROM   Student
   WHERE  Department = 'CSE';
   ```
   Output
   ```
   +-----------+-------------+-----+------------+
   | StudentID | StudentName | Age | Department |
   +-----------+-------------+-----+------------+
   |     1     | Alice       | 20  | CSE        |
   |     3     | Charlie     | 21  | CSE        |
   +-----------+-------------+-----+------------+
   ```

   (ii) Show all students sorted by age, highest first
   ```sql
   SELECT *
   FROM   Student
   ORDER BY Age DESC;
   ```
   Output
   ```
   +-----------+-------------+-----+------------+
   | StudentID | StudentName | Age | Department |
   +-----------+-------------+-----+------------+
   |     4     | David       | 23  | BBA        |
   |     2     | Bob         | 22  | EEE        |
   |     3     | Charlie     | 21  | CSE        |
   |     1     | Alice       | 20  | CSE        |
   +-----------+-------------+-----+------------+
   ```
   - `DESC` gives descending order. The default is `ASC`, so omitting DESC would sort lowest first.

   (iii) Show how many students are in each department
   ```sql
   SELECT   Department,
            COUNT(*) AS Total_Students
   FROM     Student
   GROUP BY Department;
   ```
   Output
   ```
   +------------+----------------+
   | Department | Total_Students |
   +------------+----------------+
   | CSE        |       2        |
   | EEE        |       1        |
   | BBA        |       1        |
   +------------+----------------+
   ```
   - `GROUP BY Department` creates one group per distinct department, and `COUNT(*)` counts the rows in each.

   Useful additions
   ```sql
   -- sorted by the count, largest department first
   SELECT Department, COUNT(*) AS Total_Students
   FROM   Student
   GROUP  BY Department
   ORDER  BY Total_Students DESC;

   -- only departments with more than one student
   SELECT Department, COUNT(*) AS Total_Students
   FROM   Student
   GROUP  BY Department
   HAVING COUNT(*) > 1;
   ```

8. **Consider the following relation:**

**Write an SQL query to display the region, average sale amount, and total number of sales for each region where: The average sale amount exceeds BDT 50,000 and the total number of sales in that region is at least 5.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1425 (ET: E-Zone)]*

   Answer: Two conditions must be applied to the `groups`, not to individual rows, so both belong in the `HAVING` clause.

   Assumed relation
   ```
   Sales (SaleID, Region, SaleAmount, SaleDate)
   ```

   Query
   ```sql
   SELECT   Region,
            AVG(SaleAmount) AS Average_Sale_Amount,
            COUNT(*)        AS Total_Sales
   FROM     Sales
   GROUP BY Region
   HAVING   AVG(SaleAmount) > 50000
      AND   COUNT(*) >= 5;
   ```

   Explanation
   - `GROUP BY Region` produces one row per region.
   - `AVG(SaleAmount)` and `COUNT(*)` compute the two required figures for each region.
   - `HAVING` filters the resulting groups. Both conditions test aggregate values, so neither can go in `WHERE` — `WHERE` runs before grouping and aggregates do not yet exist at that point. Writing `WHERE AVG(SaleAmount) > 50000` is a syntax error, and it is the classic mistake this question is testing.
   - The two conditions are combined with `AND`, so a region must satisfy both.

   Sample data and output
   ```
   Sales
   +--------+-----------+------------+
   | SaleID | Region    | SaleAmount |
   +--------+-----------+------------+
   | ...    | Dhaka     | (7 sales, avg 62000)  |
   | ...    | Chattogram| (6 sales, avg 48000)  |
   | ...    | Khulna    | (3 sales, avg 71000)  |
   | ...    | Sylhet    | (9 sales, avg 55000)  |
   +--------+-----------+------------+

   Result
   +-----------+---------------------+-------------+
   | Region    | Average_Sale_Amount | Total_Sales |
   +-----------+---------------------+-------------+
   | Dhaka     |        62000        |      7      |
   | Sylhet    |        55000        |      9      |
   +-----------+---------------------+-------------+
   ```
   - `Chattogram` fails the average test (48000 is not above 50000).
   - `Khulna` passes the average test but fails the count test (only 3 sales, not at least 5).

   Refinements
   ```sql
   -- restrict to one year first, then apply the group conditions
   SELECT   Region, ROUND(AVG(SaleAmount), 2) AS Average_Sale_Amount, COUNT(*) AS Total_Sales
   FROM     Sales
   WHERE    SaleDate >= '2025-01-01' AND SaleDate < '2026-01-01'   -- filters ROWS
   GROUP BY Region
   HAVING   AVG(SaleAmount) > 50000 AND COUNT(*) >= 5              -- filters GROUPS
   ORDER BY Average_Sale_Amount DESC;
   ```
   - This shows the division of labour clearly: `WHERE` narrows the rows that enter the grouping, `HAVING` discards whole groups afterwards.

9. **Given two tables:**

**a) Write an SQL query to retrieve all student names, their courses, and grades.**
**b) Write an SQL query to retrieve names of students who obtained grade 'A'.** *[BUET Assistant Programmer 21.06.2025 compact it 1434 (ET: BUET)]*

   Answer:

   Assumed schema
   ```
   Students (StudentID, StudentName, ...)
   Courses  (CourseID, CourseName, StudentID, Grade)
   ```
   - Or, in the more usual three-table form, `Enrollment(StudentID, CourseID, Grade)` linking `Students` and `Courses`. Both versions are given.

   (a) All student names, their courses and grades
   ```sql
   SELECT  s.StudentName,
           c.CourseName,
           e.Grade
   FROM    Students   s
   JOIN    Enrollment e ON s.StudentID = e.StudentID
   JOIN    Courses    c ON e.CourseID  = c.CourseID;
   ```
   - Two joins are needed because the enrolment table sits between students and courses.

   Two-table version, if Grade is stored directly with the course
   ```sql
   SELECT s.StudentName, c.CourseName, c.Grade
   FROM   Students s
   JOIN   Courses  c ON s.StudentID = c.StudentID;
   ```

   To include students who are not enrolled in anything
   ```sql
   SELECT s.StudentName, c.CourseName, e.Grade
   FROM   Students s
   LEFT JOIN Enrollment e ON s.StudentID = e.StudentID
   LEFT JOIN Courses    c ON e.CourseID  = c.CourseID;
   ```
   - Those students appear with NULL in the course and grade columns.

   (b) Names of students who obtained grade 'A'
   ```sql
   SELECT DISTINCT s.StudentName
   FROM   Students   s
   JOIN   Enrollment e ON s.StudentID = e.StudentID
   WHERE  e.Grade = 'A';
   ```
   - `DISTINCT` is important: a student with an A in three subjects would otherwise appear three times.

   Sample output
   ```
   (a)
   +-------------+--------------+-------+
   | StudentName | CourseName   | Grade |
   +-------------+--------------+-------+
   | Alice       | Database     |   A   |
   | Alice       | Networking   |   B   |
   | Bob         | Database     |   A   |
   | Charlie     | Programming  |   C   |
   +-------------+--------------+-------+

   (b)
   +-------------+
   | StudentName |
   +-------------+
   | Alice       |
   | Bob         |
   +-------------+
   ```

   Useful variations
   ```sql
   -- students with an A, and how many A grades each has
   SELECT s.StudentName, COUNT(*) AS A_count
   FROM   Students s JOIN Enrollment e ON s.StudentID = e.StudentID
   WHERE  e.Grade = 'A'
   GROUP  BY s.StudentID, s.StudentName;

   -- students whose grades are ALL A
   SELECT s.StudentName
   FROM   Students s JOIN Enrollment e ON s.StudentID = e.StudentID
   GROUP  BY s.StudentID, s.StudentName
   HAVING MIN(e.Grade) = 'A' AND MAX(e.Grade) = 'A';
   ```

10. **Consider the following database schema-** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1350 (ET: N/A)]*
```sql
employee (employee_name, street, city)
works (employee_name, company_name, salary)
company (employee_name, city)
```
**Write the SQL commands to perform the following operations:**
 * **(i) Find the names of all employees who live in the city 'Dhaka'.**
 * **(ii) Find the names of all employees whose salary in greater than BDT 1,00,000.**

    Answer:

    Schema
    ```
    employee (employee_name, street, city)
    works    (employee_name, company_name, salary)
    company  (company_name, city)
    ```
    - Note: the question prints `company (employee_name, city)`, which is clearly a typographical error — the company relation must be keyed on `company_name`, since that is what `works` refers to.

    (i) Names of all employees who live in the city 'Dhaka'
    ```sql
    SELECT  employee_name
    FROM    employee
    WHERE   city = 'Dhaka';
    ```
    - Only the `employee` relation is needed, because both the name and the city live there. No join is required.

    (ii) Names of all employees whose salary is greater than BDT 1,00,000
    ```sql
    SELECT  employee_name
    FROM    works
    WHERE   salary > 100000;
    ```
    - Salary is stored in `works`, so that is the only table needed.
    - If the requirement is names without duplicates (an employee could work for more than one company):
    ```sql
    SELECT DISTINCT employee_name
    FROM   works
    WHERE  salary > 100000;
    ```

    Both conditions together, which is the usual follow-up
    ```sql
    SELECT  e.employee_name, e.city, w.salary
    FROM    employee e
    JOIN    works    w ON e.employee_name = w.employee_name
    WHERE   e.city = 'Dhaka'
      AND   w.salary > 100000;
    ```

    Other standard queries on this classic schema
    ```sql
    -- employees who live in the same city as the company they work for
    SELECT e.employee_name
    FROM   employee e
    JOIN   works   w ON e.employee_name = w.employee_name
    JOIN   company c ON w.company_name  = c.company_name
    WHERE  e.city = c.city;

    -- give every employee of 'First Bank' a 10 percent raise
    UPDATE works
    SET    salary = salary * 1.10
    WHERE  company_name = 'First Bank';

    -- the company with the largest payroll
    SELECT company_name, SUM(salary) AS payroll
    FROM   works
    GROUP  BY company_name
    ORDER  BY payroll DESC
    LIMIT  1;

    -- employees who do NOT work for 'First Bank'
    SELECT employee_name FROM employee
    WHERE  employee_name NOT IN (SELECT employee_name FROM works
                                 WHERE company_name = 'First Bank');
    ```

11. **Given the following two tables (Students and Marks) in a database, write down the output of the given SQL queries and write down the SQL queries for the outputs:** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1344 (ET: N/A)]*

| Students |  |
|---|---|
| StudentId | StudentName |
| 1 | Mr. A |
| 2 | Mr. B |
| 3 | Mr. C |
| 4 | Mr. D |

| Marks |  |  |
|---|---|---|
| StudentId | Subject | Mark |
| 1 | Math | 70 |
| 2 | Math | 90 |
| 3 | Math | 30 |
| 1 | Bangali | 50 |
| 2 | Bangali | 60 |
| 3 | Bangali | 70 |
| 1 | Physics | 80 |
| 2 | Physics | 70 |
| 3 | Physics | 60 |

 * **(i) SELECT Count (*) FROM Students S LEFT JOIN Marks M;**
 * **(ii) SELECT StudentName From Students S JOIN Marks M**
**ON S.StudentId=M.StudentId GROUP BY S.StudentId, S.StudentName HAVING SUM (Mark)>=200;**
 * **(iii) List all the students name and number of subjects they have completed.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1345 (ET: N/A)]*
 * **(iv) List all the students who have not completed any subject.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1345 (ET: N/A)]*
 * **(v) List all the subject names.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1345 (ET: N/A)]*

    Answer:

    The data
    ```
    Students                    Marks
    +-----------+-------------+ +-----------+---------+------+
    | StudentId | StudentName | | StudentId | Subject | Mark |
    +-----------+-------------+ +-----------+---------+------+
    |     1     | Mr. A       | |     1     | Math    |  70  |
    |     2     | Mr. B       | |     2     | Math    |  90  |
    |     3     | Mr. C       | |     3     | Math    |  30  |
    |     4     | Mr. D       | |     1     | Bangali |  50  |
    +-----------+-------------+ |     2     | Bangali |  60  |
                                |     3     | Bangali |  70  |
       4 rows                   |     1     | Physics |  80  |
                                |     2     | Physics |  70  |
                                |     3     | Physics |  60  |
                                +-----------+---------+------+
                                      9 rows
    ```

    (i) `SELECT Count(*) FROM Students S LEFT JOIN Marks M;`

    - Strictly, this statement is `invalid` in most database systems: a `LEFT JOIN` requires an `ON` or `USING` clause. MySQL, PostgreSQL, Oracle and SQL Server all raise a syntax error.
    - If it is read as the intended `cross join` (every row of one table paired with every row of the other), the count is:
    ```
    4 × 9 = 36
    ```
    - `Answer: 36` (as a cross join), and a syntax error if executed literally as written.

    (ii)
    ```sql
    SELECT StudentName FROM Students S JOIN Marks M
    ON S.StudentId = M.StudentId
    GROUP BY S.StudentId, S.StudentName
    HAVING SUM(Mark) >= 200;
    ```
    Working out each student's total
    ```
    Mr. A : 70 + 50 + 80 = 200   -> 200 >= 200  ✓
    Mr. B : 90 + 60 + 70 = 220   -> 220 >= 200  ✓
    Mr. C : 30 + 70 + 60 = 160   -> 160 >= 200  ✗
    Mr. D : no rows in Marks, so an inner join drops him entirely
    ```
    Output
    ```
    +-------------+
    | StudentName |
    +-------------+
    | Mr. A       |
    | Mr. B       |
    +-------------+
    ```

    (iii) All student names and the number of subjects completed
    ```sql
    SELECT   S.StudentName,
             COUNT(M.Subject) AS Subjects_Completed
    FROM     Students S
    LEFT JOIN Marks  M ON S.StudentId = M.StudentId
    GROUP BY S.StudentId, S.StudentName;
    ```
    - A `LEFT JOIN` is essential so that Mr. D still appears. `COUNT(M.Subject)` counts non-NULL values, so it correctly returns 0 for him — whereas `COUNT(*)` would wrongly return 1.
    ```
    +-------------+--------------------+
    | StudentName | Subjects_Completed |
    +-------------+--------------------+
    | Mr. A       |         3          |
    | Mr. B       |         3          |
    | Mr. C       |         3          |
    | Mr. D       |         0          |
    +-------------+--------------------+
    ```

    (iv) Students who have not completed any subject
    ```sql
    SELECT   S.StudentName
    FROM     Students S
    LEFT JOIN Marks  M ON S.StudentId = M.StudentId
    WHERE    M.StudentId IS NULL;
    ```
    - The `LEFT JOIN ... WHERE ... IS NULL` pattern is the standard way to find rows in one table with no match in another.
    ```
    +-------------+
    | StudentName |
    +-------------+
    | Mr. D       |
    +-------------+
    ```
    Equivalent forms
    ```sql
    SELECT StudentName FROM Students
    WHERE  StudentId NOT IN (SELECT StudentId FROM Marks);

    SELECT StudentName FROM Students S
    WHERE  NOT EXISTS (SELECT 1 FROM Marks M WHERE M.StudentId = S.StudentId);
    ```

    (v) All the subject names
    ```sql
    SELECT DISTINCT Subject FROM Marks;
    ```
    ```
    +---------+
    | Subject |
    +---------+
    | Math    |
    | Bangali |
    | Physics |
    +---------+
    ```
    - `DISTINCT` is necessary, since each subject appears three times in the Marks table.

12. **Given a Patient table in a hospital database below.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1340 (ET: N/A)]*

| Patient_ID | Disease_Name |
|---|---|
| 1 | Covid-19 |
| 2 | Dialysis |
| 3 | Covid-19 |
| 4 | Dengue |

Write down an SQL query to display the total number of patients under each disease category.

    Answer: The requirement is a count per disease category, which is a `GROUP BY` with `COUNT`.

    The data
    ```
    Patient
    +------------+--------------+
    | Patient_ID | Disease_Name |
    +------------+--------------+
    |     1      | Covid-19     |
    |     2      | Dialysis     |
    |     3      | Covid-19     |
    |     4      | Dengue       |
    +------------+--------------+
    ```

    Query
    ```sql
    SELECT   Disease_Name,
             COUNT(*) AS Total_Patients
    FROM     Patient
    GROUP BY Disease_Name;
    ```

    Output
    ```
    +--------------+----------------+
    | Disease_Name | Total_Patients |
    +--------------+----------------+
    | Covid-19     |       2        |
    | Dialysis     |       1        |
    | Dengue       |       1        |
    +--------------+----------------+
    ```

    Explanation
    - `GROUP BY Disease_Name` gathers all rows with the same disease into one group — here Covid-19 has two rows, the others one each.
    - `COUNT(*)` counts the rows within each group.
    - `Disease_Name` may appear in the SELECT list because it is the grouping column; any other plain column would be an error.

    Useful variations
    ```sql
    -- sorted with the most common disease first
    SELECT Disease_Name, COUNT(*) AS Total_Patients
    FROM   Patient
    GROUP  BY Disease_Name
    ORDER  BY Total_Patients DESC;

    -- only diseases with more than one patient
    SELECT Disease_Name, COUNT(*) AS Total_Patients
    FROM   Patient
    GROUP  BY Disease_Name
    HAVING COUNT(*) > 1;

    -- the single most common disease
    SELECT Disease_Name, COUNT(*) AS Total_Patients
    FROM   Patient
    GROUP  BY Disease_Name
    ORDER  BY Total_Patients DESC
    LIMIT  1;
    ```
    - `COUNT(*)` counts every row including those with NULLs elsewhere; `COUNT(Disease_Name)` would skip rows where the disease is NULL. Here the two give the same result, but the distinction matters when NULLs are present.

13. **SQL OUTPUT Problem: Find Employee salary from a table where salary more than 5000.** *[BCIC Assistant Programmer 14.02.2025 compact it 1328 (ET: BUET)]*

    Answer:

    Query
    ```sql
    SELECT  emp_id, emp_name, salary
    FROM    Employee
    WHERE   salary > 5000;
    ```
    - `WHERE salary > 5000` keeps only the rows whose salary exceeds 5000. The comparison is strict, so a salary of exactly 5000 is excluded.

    Sample input and output
    ```
    Employee
    +--------+----------+--------+
    | emp_id | emp_name | salary |
    +--------+----------+--------+
    |   1    | Karim    |  4500  |
    |   2    | Rahim    |  8000  |
    |   3    | Sumi     |  5000  |
    |   4    | Nabil    | 12000  |
    |   5    | Jamil    |  6500  |
    +--------+----------+--------+

    Result
    +--------+----------+--------+
    | emp_id | emp_name | salary |
    +--------+----------+--------+
    |   2    | Rahim    |  8000  |
    |   4    | Nabil    | 12000  |
    |   5    | Jamil    |  6500  |
    +--------+----------+--------+
    ```
    - Karim (4500) is excluded because his salary is below the limit, and Sumi (5000) because the operator is `>` rather than `>=`.

    Related variations
    ```sql
    -- all columns
    SELECT * FROM Employee WHERE salary > 5000;

    -- 5000 included
    SELECT * FROM Employee WHERE salary >= 5000;

    -- a range (BETWEEN is inclusive at both ends)
    SELECT * FROM Employee WHERE salary BETWEEN 5000 AND 20000;

    -- sorted, highest first
    SELECT * FROM Employee WHERE salary > 5000 ORDER BY salary DESC;

    -- with a second condition
    SELECT * FROM Employee WHERE salary > 5000 AND dept_id = 10;

    -- how many, and what they cost
    SELECT COUNT(*) AS how_many, SUM(salary) AS total
    FROM   Employee WHERE salary > 5000;
    ```
    - A point worth remembering: a row where `salary` is `NULL` is `not` returned by `salary > 5000`, because any comparison with NULL yields UNKNOWN rather than TRUE. To include such rows the condition must be written `salary > 5000 OR salary IS NULL`.

14. **Write SQL code to get duplicate names from employee table.** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*

    Answer: A name is a duplicate when it appears more than once, so the rows are grouped by name and the groups with a count above one are kept.

    Query — list the duplicate names and how often each occurs
    ```sql
    SELECT   emp_name,
             COUNT(*) AS occurrences
    FROM     Employee
    GROUP BY emp_name
    HAVING   COUNT(*) > 1;
    ```

    Explanation
    - `GROUP BY emp_name` puts all rows sharing a name into one group.
    - `COUNT(*)` counts the rows in each group.
    - `HAVING COUNT(*) > 1` keeps only the groups containing more than one row — that is, the duplicated names. `WHERE` cannot be used here, because it runs before grouping and the count does not yet exist.

    Sample data and output
    ```
    Employee
    +--------+----------+--------+
    | emp_id | emp_name | salary |
    +--------+----------+--------+
    |   1    | Karim    | 40000  |
    |   2    | Rahim    | 50000  |
    |   3    | Karim    | 45000  |
    |   4    | Sumi     | 38000  |
    |   5    | Rahim    | 52000  |
    |   6    | Karim    | 41000  |
    +--------+----------+--------+

    Result
    +----------+-------------+
    | emp_name | occurrences |
    +----------+-------------+
    | Karim    |      3      |
    | Rahim    |      2      |
    +----------+-------------+
    ```

    To see the full rows of the duplicated employees
    ```sql
    SELECT *
    FROM   Employee
    WHERE  emp_name IN (SELECT emp_name FROM Employee
                        GROUP BY emp_name HAVING COUNT(*) > 1)
    ORDER  BY emp_name;
    ```

    Duplicates on more than one column
    ```sql
    SELECT emp_name, dept_id, COUNT(*)
    FROM   Employee
    GROUP  BY emp_name, dept_id
    HAVING COUNT(*) > 1;
    ```

    Deleting the duplicates, keeping the lowest emp_id
    ```sql
    DELETE FROM Employee
    WHERE  emp_id NOT IN (SELECT MIN(emp_id) FROM Employee GROUP BY emp_name);
    ```
    - MySQL requires this to be wrapped in a derived table, because it will not read from the same table it is deleting from:
    ```sql
    DELETE FROM Employee
    WHERE  emp_id NOT IN (SELECT keep FROM
            (SELECT MIN(emp_id) AS keep FROM Employee GROUP BY emp_name) AS t);
    ```

    Window-function alternative
    ```sql
    SELECT * FROM (
       SELECT e.*, COUNT(*) OVER (PARTITION BY emp_name) AS cnt
       FROM Employee e) t
    WHERE cnt > 1;
    ```

15. **Write an SQL query to find duplicate names in the employee table.** *[BBA Assistant Programmer 12.07.2025 compact it 1433 (ET: BUET)]*

    Answer: A duplicate name is one that appears in more than one row, so the table is grouped by name and only groups with a count above one are kept.

    Query
    ```sql
    SELECT   emp_name,
             COUNT(*) AS occurrences
    FROM     Employee
    GROUP BY emp_name
    HAVING   COUNT(*) > 1;
    ```

    Why HAVING and not WHERE
    - SQL executes in the order `FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY`. At the time `WHERE` runs, the rows have not yet been grouped, so `COUNT(*)` does not exist. Conditions on an aggregate must therefore go in `HAVING`.

    Sample data and output
    ```
    Employee
    +--------+----------+
    | emp_id | emp_name |
    +--------+----------+
    |   1    | Karim    |
    |   2    | Rahim    |
    |   3    | Karim    |
    |   4    | Sumi     |
    |   5    | Rahim    |
    |   6    | Karim    |
    +--------+----------+

    Result
    +----------+-------------+
    | emp_name | occurrences |
    +----------+-------------+
    | Karim    |      3      |
    | Rahim    |      2      |
    +----------+-------------+
    ```

    Just the names, without the count
    ```sql
    SELECT emp_name
    FROM   Employee
    GROUP  BY emp_name
    HAVING COUNT(*) > 1;
    ```

    Full details of every duplicated employee
    ```sql
    SELECT e.*
    FROM   Employee e
    JOIN  (SELECT emp_name FROM Employee
           GROUP BY emp_name HAVING COUNT(*) > 1) d
       ON e.emp_name = d.emp_name
    ORDER BY e.emp_name;
    ```

    Self-join alternative
    ```sql
    SELECT DISTINCT e1.emp_name
    FROM   Employee e1
    JOIN   Employee e2 ON e1.emp_name = e2.emp_name
                      AND e1.emp_id  <> e2.emp_id;
    ```

    Window-function alternative
    ```sql
    SELECT emp_id, emp_name FROM (
       SELECT emp_id, emp_name,
              ROW_NUMBER() OVER (PARTITION BY emp_name ORDER BY emp_id) AS rn
       FROM Employee) t
    WHERE rn > 1;
    ```
    - This form returns only the `extra` copies, keeping the first of each name — which is exactly what is wanted before deleting duplicates.

16. **SUM, Avg, Max these function are subnet of __________ function.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*

    Answer: SUM, AVG and MAX are a subset of `AGGREGATE` functions.

    - An aggregate function takes many rows as input and returns a `single` summary value. That is what distinguishes them from scalar functions, which return one value per row.

    The five standard aggregate functions

    | Function | Purpose | NULL handling |
    |---|---|---|
    | `COUNT()` | Number of rows or non-null values | COUNT(*) counts all rows; COUNT(col) skips NULLs |
    | `SUM()` | Total of a numeric column | NULLs ignored |
    | `AVG()` | Arithmetic mean | NULLs ignored — so the divisor is the count of non-null values |
    | `MAX()` | Largest value | NULLs ignored |
    | `MIN()` | Smallest value | NULLs ignored |

    Example
    ```sql
    SELECT COUNT(*)    AS total_employees,
           SUM(salary) AS total_salary,
           AVG(salary) AS average_salary,
           MAX(salary) AS highest_salary,
           MIN(salary) AS lowest_salary
    FROM   Employee;
    ```

    Used with GROUP BY, they summarise each group instead of the whole table
    ```sql
    SELECT   dept_id,
             COUNT(*)    AS employees,
             AVG(salary) AS avg_salary
    FROM     Employee
    GROUP BY dept_id
    HAVING   AVG(salary) > 50000;
    ```

    Rules to remember
    - Aggregate functions cannot appear in a `WHERE` clause, because WHERE runs before grouping. Conditions on aggregates go in `HAVING`.
    - Every non-aggregated column in the SELECT list must appear in the `GROUP BY` clause.
    - `AVG` ignoring NULLs is a frequent source of error: with values 10, 20 and NULL, `AVG` returns 15, not 10. Use `AVG(COALESCE(col, 0))` if NULLs should count as zero.
    - Other functions in the family: `STDDEV`, `VARIANCE`, `GROUP_CONCAT` (MySQL) or `STRING_AGG` (PostgreSQL, SQL Server).

17. **SQL Query.....** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 592 (ET: BUET)], [RAKUB Assistant Network System Engineer 03.11.2023 compact it 553 (ET: BIBM)], [BREB Assistant Programmer (AP) 21.02.2025 compact it 1335 (ET: N/A)], [Water Supply and Sewerage Authority (WASA); Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*

    Answer: The specific query was not printed, so the SQL query patterns that these examinations set repeatedly are given, with a common schema:
    ```
    Employee   (emp_id, emp_name, salary, dept_id, hire_date, manager_id, job)
    Department (dept_id, dept_name, location)
    ```

    1. Filtering
    ```sql
    SELECT * FROM Employee WHERE salary > 30000 AND dept_id = 10;
    SELECT * FROM Employee WHERE salary BETWEEN 20000 AND 50000;
    SELECT * FROM Employee WHERE emp_name LIKE 'A%';        -- starts with A
    SELECT * FROM Employee WHERE dept_id IN (10, 20, 30);
    SELECT * FROM Employee WHERE manager_id IS NULL;
    ```

    2. Aggregation per group
    ```sql
    SELECT d.dept_name, COUNT(*) AS staff, AVG(e.salary) AS avg_salary
    FROM   Employee e JOIN Department d ON e.dept_id = d.dept_id
    GROUP  BY d.dept_id, d.dept_name
    HAVING COUNT(*) > 3
    ORDER  BY avg_salary DESC;
    ```

    3. Subqueries
    ```sql
    -- above the overall average
    SELECT emp_name FROM Employee
    WHERE  salary > (SELECT AVG(salary) FROM Employee);

    -- above their OWN department's average (correlated)
    SELECT e.emp_name FROM Employee e
    WHERE  e.salary > (SELECT AVG(x.salary) FROM Employee x WHERE x.dept_id = e.dept_id);
    ```

    4. Second highest salary
    ```sql
    SELECT MAX(salary) FROM Employee
    WHERE  salary < (SELECT MAX(salary) FROM Employee);
    ```

    5. Duplicates
    ```sql
    SELECT emp_name, COUNT(*) FROM Employee
    GROUP  BY emp_name HAVING COUNT(*) > 1;
    ```

    6. Joins
    ```sql
    SELECT e.emp_name, d.dept_name FROM Employee e
    JOIN   Department d ON e.dept_id = d.dept_id;          -- matching rows only

    SELECT d.dept_name FROM Department d
    LEFT JOIN Employee e ON d.dept_id = e.dept_id
    WHERE  e.emp_id IS NULL;                                -- departments with no staff
    ```

    7. Self join
    ```sql
    SELECT e.emp_name AS employee, m.emp_name AS manager
    FROM   Employee e JOIN Employee m ON e.manager_id = m.emp_id
    WHERE  e.salary > m.salary;
    ```

    8. Modifying data
    ```sql
    INSERT INTO Employee VALUES (101, 'Karim', 45000, 10, '2024-01-15', 5, 'Analyst');
    UPDATE Employee SET salary = salary * 1.10 WHERE dept_id = 10;
    DELETE FROM Employee WHERE hire_date < '2010-01-01';
    ```

    9. Creating a table and a view
    ```sql
    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,
        emp_name VARCHAR(50) NOT NULL,
        salary   DECIMAL(10,2) CHECK (salary > 0),
        dept_id  INT REFERENCES Department(dept_id)
    );

    CREATE VIEW HighEarners AS
    SELECT emp_name, salary FROM Employee WHERE salary > 50000;
    ```

    10. Ranking with a window function
    ```sql
    SELECT dept_id, emp_name, salary FROM (
       SELECT dept_id, emp_name, salary,
              RANK() OVER (PARTITION BY dept_id ORDER BY salary DESC) AS r
       FROM Employee) t
    WHERE r = 1;
    ```
    - The one rule that resolves most exam questions: SQL evaluates `FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY`. `WHERE` filters rows, `HAVING` filters groups. <!-- verify -->

18. **Find sname who supplies pname=“wheel” with minimum price:** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 418 (ET: BUET)]*
    * **Catalog** (sid, pid, price)
    * **Supplier** (sid, sname, address)
    * **Product** (pid, pname, etc)

    Answer:

    Schema
    ```
    Catalog  (sid, pid, price)
    Supplier (sid, sname, address)
    Product  (pid, pname, ...)
    ```

    Query
    ```sql
    SELECT  s.sname
    FROM    Supplier s
    JOIN    Catalog  c ON s.sid = c.sid
    JOIN    Product  p ON c.pid = p.pid
    WHERE   p.pname = 'wheel'
      AND   c.price = (
                SELECT MIN(c2.price)
                FROM   Catalog c2
                JOIN   Product p2 ON c2.pid = p2.pid
                WHERE  p2.pname = 'wheel'
            );
    ```

    How it works
    - The three tables are joined so that a supplier can be connected to a product name through the catalogue.
    - `WHERE p.pname = 'wheel'` restricts attention to wheels.
    - The subquery computes the `minimum price at which any supplier offers a wheel`, and the outer query keeps only the supplier or suppliers charging exactly that price.
    - Using `= MIN(...)` rather than `ORDER BY price LIMIT 1` correctly returns `all` suppliers if several tie at the lowest price.

    Sample data and result
    ```
    Catalog                     Supplier                 Product
    +-----+-----+-------+       +-----+---------+        +-----+-------+
    | sid | pid | price |       | sid | sname   |        | pid | pname |
    +-----+-----+-------+       +-----+---------+        +-----+-------+
    |  1  | 10  |  500  |       |  1  | Alpha   |        | 10  | wheel |
    |  2  | 10  |  350  |       |  2  | Beta    |        | 11  | tyre  |
    |  3  | 10  |  350  |       |  3  | Gamma   |        +-----+-------+
    |  1  | 11  |  200  |       |  4  | Delta   |
    +-----+-----+-------+       +-----+---------+

    Minimum wheel price = 350

    Result
    +-------+
    | sname |
    +-------+
    | Beta  |
    | Gamma |
    +-------+
    ```

    Alternative using ORDER BY and LIMIT
    ```sql
    SELECT s.sname, c.price
    FROM   Supplier s
    JOIN   Catalog  c ON s.sid = c.sid
    JOIN   Product  p ON c.pid = p.pid
    WHERE  p.pname = 'wheel'
    ORDER  BY c.price ASC
    LIMIT  1;
    ```
    - Simpler, but it returns only `one` supplier even when several share the lowest price. The subquery version is the correct answer to the question as asked.

    If `pid` for the wheel is known directly
    ```sql
    SELECT s.sname
    FROM   Supplier s JOIN Catalog c ON s.sid = c.sid
    WHERE  c.pid = 10
      AND  c.price = (SELECT MIN(price) FROM Catalog WHERE pid = 10);
    ```

19. **Let a database has two tables, Customers and Orders. The following figure shows the partial data of these two tables. Based on this partial data, explain Inner, Left, Right and Full join. Show the result set of each join operation.**

**Table: Customers**
| ID | First name |
|---|---|
| 1 | Rahim |
| 2 | Karim |
| 3 | Belal |
| 4 | Rony |
| 5 | Helal |

**Table: Orders**
| Order id | Amount | Customer id |
|---|---|---|
| 1 | 200 | 10 |
| 2 | 500 | 3 |
| 3 | 300 | 6 |
| 4 | 800 | 5 |
| 5 | 150 | 8 |

*[Combined Bank Senior Officer (IT) 17.05.2024 compact it 335 (ET: BIBM)]*

    Answer: The two tables share almost nothing, which makes the differences between the four joins very clear.

    The data
    ```
    Customers                        Orders
    +----+------------+              +----------+--------+-------------+
    | ID | First name |              | Order id | Amount | Customer id |
    +----+------------+              +----------+--------+-------------+
    | 1  | Rahim      |              |    1     |  200   |     10      |
    | 2  | Karim      |              |    2     |  500   |      3      |
    | 3  | Belal      |              |    3     |  300   |      6      |
    | 4  | Rony       |              |    4     |  800   |      5      |
    | 5  | Helal      |              |    5     |  150   |      8      |
    +----+------------+              +----------+--------+-------------+
    ```
    - Matching pairs: `Customer 3 (Belal) with Order 2`, and `Customer 5 (Helal) with Order 4`. Nothing else matches.

    1. INNER JOIN — only the matching rows
    ```sql
    SELECT c.ID, c.First_name, o.Order_id, o.Amount
    FROM   Customers c
    INNER JOIN Orders o ON c.ID = o.Customer_id;
    ```
    ```
    +----+------------+----------+--------+
    | ID | First name | Order id | Amount |
    +----+------------+----------+--------+
    | 3  | Belal      |    2     |  500   |
    | 5  | Helal      |    4     |  800   |
    +----+------------+----------+--------+
    2 rows
    ```

    2. LEFT (OUTER) JOIN — all customers, matched orders where they exist
    ```sql
    SELECT c.ID, c.First_name, o.Order_id, o.Amount
    FROM   Customers c
    LEFT JOIN Orders o ON c.ID = o.Customer_id;
    ```
    ```
    +----+------------+----------+--------+
    | ID | First name | Order id | Amount |
    +----+------------+----------+--------+
    | 1  | Rahim      |   NULL   |  NULL  |
    | 2  | Karim      |   NULL   |  NULL  |
    | 3  | Belal      |    2     |  500   |
    | 4  | Rony       |   NULL   |  NULL  |
    | 5  | Helal      |    4     |  800   |
    +----+------------+----------+--------+
    5 rows
    ```

    3. RIGHT (OUTER) JOIN — all orders, matched customers where they exist
    ```sql
    SELECT c.ID, c.First_name, o.Order_id, o.Amount
    FROM   Customers c
    RIGHT JOIN Orders o ON c.ID = o.Customer_id;
    ```
    ```
    +------+------------+----------+--------+
    | ID   | First name | Order id | Amount |
    +------+------------+----------+--------+
    | NULL | NULL       |    1     |  200   |
    |  3   | Belal      |    2     |  500   |
    | NULL | NULL       |    3     |  300   |
    |  5   | Helal      |    4     |  800   |
    | NULL | NULL       |    5     |  150   |
    +------+------------+----------+--------+
    5 rows
    ```

    4. FULL OUTER JOIN — everything from both sides
    ```sql
    SELECT c.ID, c.First_name, o.Order_id, o.Amount
    FROM   Customers c
    FULL OUTER JOIN Orders o ON c.ID = o.Customer_id;
    ```
    ```
    +------+------------+----------+--------+
    | ID   | First name | Order id | Amount |
    +------+------------+----------+--------+
    |  1   | Rahim      |   NULL   |  NULL  |
    |  2   | Karim      |   NULL   |  NULL  |
    |  3   | Belal      |    2     |  500   |
    |  4   | Rony       |   NULL   |  NULL  |
    |  5   | Helal      |    4     |  800   |
    | NULL | NULL       |    1     |  200   |
    | NULL | NULL       |    3     |  300   |
    | NULL | NULL       |    5     |  150   |
    +------+------------+----------+--------+
    8 rows
    ```
    - Count check: 2 matched + 3 unmatched customers + 3 unmatched orders = `8`.

    Summary

    | Join | Rows returned | Which rows are kept |
    |---|---|---|
    | INNER | 2 | Only where the condition matches |
    | LEFT | 5 | All customers, plus matches |
    | RIGHT | 5 | All orders, plus matches |
    | FULL OUTER | 8 | Everything from both tables |

    - Note for MySQL: it has no `FULL OUTER JOIN`. The usual workaround is
    ```sql
    SELECT ... FROM Customers c LEFT JOIN Orders o ON c.ID = o.Customer_id
    UNION
    SELECT ... FROM Customers c RIGHT JOIN Orders o ON c.ID = o.Customer_id;
    ```

20. **Database query:**
   * **(i) Group by**
   * **(ii) Average Salary** *[Combined Bank Assistant Programmer 09.02.2024 compact it 299 (ET: BIBM)]*

    Answer:

    (i) GROUP BY
    - `GROUP BY` collapses rows that share the same value in one or more columns into a single summary row, so that an aggregate function can be applied to each group instead of to the whole table.

    ```sql
    SELECT   dept_id,
             COUNT(*)    AS employees,
             SUM(salary) AS total_salary
    FROM     Employee
    GROUP BY dept_id;
    ```
    ```
    Employee                              Result
    +--------+---------+--------+         +---------+-----------+--------------+
    | emp_id | dept_id | salary |         | dept_id | employees | total_salary |
    +--------+---------+--------+         +---------+-----------+--------------+
    |   1    |   10    | 50000  |   ->    |   10    |     2     |   110000     |
    |   2    |   10    | 60000  |         |   20    |     2     |    85000     |
    |   3    |   20    | 40000  |         +---------+-----------+--------------+
    |   4    |   20    | 45000  |
    +--------+---------+--------+
    ```

    Rules
    - Every column in the SELECT list must either appear in the `GROUP BY` clause or be inside an aggregate function.
    - `WHERE` filters individual rows `before` grouping; `HAVING` filters whole groups `after` aggregation. Aggregate functions can never appear in a WHERE clause.
    - Grouping by several columns creates one group per distinct combination.
    ```sql
    SELECT dept_id, job, COUNT(*)
    FROM   Employee
    GROUP  BY dept_id, job;
    ```
    - SQL's order of evaluation is `FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY`, which explains all of these rules.

    (ii) Average salary
    ```sql
    -- overall average
    SELECT AVG(salary) AS average_salary FROM Employee;

    -- average per department
    SELECT   dept_id, AVG(salary) AS average_salary
    FROM     Employee
    GROUP BY dept_id;

    -- with the department name, rounded and sorted
    SELECT   d.dept_name, ROUND(AVG(e.salary), 2) AS average_salary
    FROM     Employee e
    JOIN     Department d ON e.dept_id = d.dept_id
    GROUP BY d.dept_id, d.dept_name
    ORDER BY average_salary DESC;

    -- only departments averaging above 50000
    SELECT   dept_id, AVG(salary) AS average_salary
    FROM     Employee
    GROUP BY dept_id
    HAVING   AVG(salary) > 50000;

    -- employees earning more than the overall average
    SELECT emp_name, salary FROM Employee
    WHERE  salary > (SELECT AVG(salary) FROM Employee);
    ```

    Caution with NULLs
    - `AVG(salary)` ignores rows where salary is NULL, so the divisor is the count of `non-null` salaries, not the row count. With values 10, 20 and NULL, AVG returns 15, not 10.
    - To treat NULL as zero: `AVG(COALESCE(salary, 0))`.

21. **Consider that you are given a database of a 'Pet Society' with the following relations.**
   * **Animals(*ID*: integer, *Name*: string, *PrevOwner*: string, *DateAdmitted*: date, *Type*: string)**
   * **Adopter(*PSIN*: integer, *Name*: string, *Address*: string, *OtherAnimals*: integer)**
   * **Adoption(*AnimalID*: integer, *PSIN*: integer, *AdoptDate*: date, *chipNo*: integer)**
   **Give a sql query that list total number of adoptions on June 30, 2024 for each animal type.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 429 (ET: BIBM)]*

    Answer:

    Schema
    ```
    Animals  (ID, Name, PrevOwner, DateAdmitted, Type)
    Adopter  (PSIN, Name, Address, OtherAnimals)
    Adoption (AnimalID, PSIN, AdoptDate, chipNo)
    ```

    Query — total adoptions on 30 June 2024 for each animal type
    ```sql
    SELECT   a.Type,
             COUNT(*) AS Total_Adoptions
    FROM     Adoption ad
    JOIN     Animals  a ON ad.AnimalID = a.ID
    WHERE    ad.AdoptDate = '2024-06-30'
    GROUP BY a.Type;
    ```

    Explanation
    - `Adoption` records the event but stores only the animal's ID, so it must be joined to `Animals` to obtain the `Type`.
    - `WHERE ad.AdoptDate = '2024-06-30'` filters the rows to that single day, before grouping.
    - `GROUP BY a.Type` produces one row per animal type, and `COUNT(*)` counts the adoptions in each.

    Sample output
    ```
    +--------+-----------------+
    | Type   | Total_Adoptions |
    +--------+-----------------+
    | Cat    |        5        |
    | Dog    |        3        |
    | Rabbit |        1        |
    +--------+-----------------+
    ```

    If AdoptDate stores a date and time
    - A plain equality would then match only midnight exactly. The reliable form is a half-open range, which also allows an index on AdoptDate to be used:
    ```sql
    WHERE ad.AdoptDate >= '2024-06-30'
      AND ad.AdoptDate <  '2024-07-01'
    ```
    - Avoid `WHERE DATE(ad.AdoptDate) = '2024-06-30'`, because wrapping the column in a function prevents the index from being used.

    To show types with zero adoptions as well
    ```sql
    SELECT   a.Type, COUNT(ad.AnimalID) AS Total_Adoptions
    FROM     Animals a
    LEFT JOIN Adoption ad ON a.ID = ad.AnimalID
                         AND ad.AdoptDate = '2024-06-30'
    GROUP BY a.Type;
    ```
    - The date condition must be in the `ON` clause, not in `WHERE`. Placing it in WHERE would discard the NULL rows and turn the outer join back into an inner join — a very common mistake.

    Related queries on this schema
    ```sql
    -- adopters who have adopted more than one animal
    SELECT ad2.Name, COUNT(*) FROM Adoption a JOIN Adopter ad2 ON a.PSIN = ad2.PSIN
    GROUP BY ad2.PSIN, ad2.Name HAVING COUNT(*) > 1;

    -- animals still waiting for adoption
    SELECT a.Name, a.Type FROM Animals a
    LEFT JOIN Adoption ad ON a.ID = ad.AnimalID
    WHERE ad.AnimalID IS NULL;
    ```

22. **How many row will return when we do i) Inner Join ii) Left Outer Join iii) Right Outer join and v) Full Outer join.** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 392 (ET: BUET)]*

    Answer: The number of rows each join returns depends entirely on how many rows match. Using the two tables from the accompanying question:

    The data
    ```
    Customers (5 rows)              Orders (5 rows)
    +----+------------+             +----------+--------+-------------+
    | ID | First name |             | Order id | Amount | Customer id |
    +----+------------+             +----------+--------+-------------+
    | 1  | Rahim      |             |    1     |  200   |     10      |
    | 2  | Karim      |             |    2     |  500   |      3      |
    | 3  | Belal      |             |    3     |  300   |      6      |
    | 4  | Rony       |             |    4     |  800   |      5      |
    | 5  | Helal      |             |    5     |  150   |      8      |
    +----+------------+             +----------+--------+-------------+

    Matching pairs: customer 3 with order 2, and customer 5 with order 4  -> 2 matches
    Unmatched customers: 1, 2, 4                                          -> 3 rows
    Unmatched orders   : 1, 3, 5 (customer ids 10, 6, 8)                   -> 3 rows
    ```

    Results

    | # | Join type | Rows | Reason |
    |---|---|---|---|
    | i | `INNER JOIN` | `2` | Only the matching pairs |
    | ii | `LEFT OUTER JOIN` | `5` | 2 matched + 3 unmatched customers |
    | iii | `RIGHT OUTER JOIN` | `5` | 2 matched + 3 unmatched orders |
    | iv | `FULL OUTER JOIN` | `8` | 2 matched + 3 unmatched customers + 3 unmatched orders |

    The general rules

    ```
    INNER JOIN  = M                         (M = number of matching pairs)
    LEFT JOIN   = M + (unmatched left rows)
    RIGHT JOIN  = M + (unmatched right rows)
    FULL JOIN   = M + (unmatched left) + (unmatched right)
    CROSS JOIN  = rows(left) × rows(right)   -- here 5 × 5 = 25
    ```

    - A useful check: `LEFT JOIN` always returns at least as many rows as the left table has, and `INNER JOIN` returns at most as many as a `CROSS JOIN`.

    The one-to-many complication
    - If a single customer had `three` orders, the inner join would return three rows for that customer, not one. So the count is the number of `matching pairs`, not the number of matching customers.
    ```
    Customer 3 with 3 orders -> INNER JOIN returns 3 rows for customer 3
    ```

    Diagrams
    ```
    INNER            LEFT             RIGHT            FULL
      (A∩B)          (A + A∩B)        (A∩B + B)        (A + A∩B + B)
       ###             ####             ####            #######
      #   #           #    #           #    #          #       #
    ```
    - Note for MySQL: `FULL OUTER JOIN` is not supported; the standard workaround is `LEFT JOIN ... UNION ... RIGHT JOIN`.

23. **Write SQL Query For create, insert of a table Emp (id, name, designation, Dept_name, Salary). Write SQL Query that show department wise salary of Employee.** *[BKSP Assistant Programmer 13.07.2024 compact it 1459 (ET: N/A)]*

    Answer:

    Part 1 — create the table
    ```sql
    CREATE TABLE Emp (
        id          INT PRIMARY KEY,
        name        VARCHAR(50)   NOT NULL,
        designation VARCHAR(50),
        Dept_name   VARCHAR(50),
        Salary      DECIMAL(10,2) CHECK (Salary > 0)
    );
    ```
    - `PRIMARY KEY` on id makes it unique and not null.
    - `NOT NULL` on name forbids a nameless record.
    - `CHECK (Salary > 0)` rejects a negative or zero salary.
    - `DECIMAL(10,2)` is the correct type for money — `FLOAT` should be avoided, because binary floating point cannot represent decimal amounts exactly.

    Part 2 — insert rows
    ```sql
    INSERT INTO Emp (id, name, designation, Dept_name, Salary) VALUES
      (1, 'Karim',  'Manager',   'IT',       75000),
      (2, 'Rahim',  'Developer', 'IT',       55000),
      (3, 'Sumi',   'Analyst',   'HR',       48000),
      (4, 'Nabil',  'Officer',   'HR',       42000),
      (5, 'Jamil',  'Accountant','Accounts', 50000),
      (6, 'Farida', 'Developer', 'IT',       60000);
    ```
    - A single INSERT with several value lists is faster than six separate statements, because it is one transaction and one round trip.

    Part 3 — department-wise salary
    ```sql
    SELECT   Dept_name,
             COUNT(*)    AS Total_Employees,
             SUM(Salary) AS Total_Salary,
             AVG(Salary) AS Average_Salary
    FROM     Emp
    GROUP BY Dept_name;
    ```

    Output
    ```
    +-----------+-----------------+--------------+----------------+
    | Dept_name | Total_Employees | Total_Salary | Average_Salary |
    +-----------+-----------------+--------------+----------------+
    | IT        |        3        |    190000    |    63333.33    |
    | HR        |        2        |     90000    |    45000.00    |
    | Accounts  |        1        |     50000    |    50000.00    |
    +-----------+-----------------+--------------+----------------+
    ```

    If only the total per department is wanted
    ```sql
    SELECT   Dept_name, SUM(Salary) AS Total_Salary
    FROM     Emp
    GROUP BY Dept_name
    ORDER BY Total_Salary DESC;
    ```

    Useful extensions
    ```sql
    -- only departments spending more than 100000
    SELECT Dept_name, SUM(Salary) FROM Emp
    GROUP  BY Dept_name HAVING SUM(Salary) > 100000;

    -- department-wise breakdown by designation as well
    SELECT Dept_name, designation, COUNT(*), SUM(Salary)
    FROM   Emp GROUP BY Dept_name, designation;
    ```
    - Design note: storing `Dept_name` as text in the Emp table repeats the department name in every row, which is a normalisation problem. A properly designed schema would hold `dept_id` here and a separate `Department(dept_id, dept_name)` table.

24. **Query's: Employee & department table given-**
   * **(i) Write the employee name who got same salary named Rahim but not same job of Rahim.**
   * **(ii) Write the employee's name who's average salary is more than company's average salary** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 380 (ET: BUET)]*

    Answer:

    (i) Employees on the same salary as Rahim, but with a different job
    ```sql
    SELECT  e.emp_name, e.job, e.salary
    FROM    Employee e
    WHERE   e.salary = (SELECT salary FROM Employee WHERE emp_name = 'Rahim')
      AND   e.job   <> (SELECT job    FROM Employee WHERE emp_name = 'Rahim')
      AND   e.emp_name <> 'Rahim';
    ```
    - The first subquery fetches Rahim's salary and the second his job.
    - `<>` on the job excludes anyone doing the same work.
    - The last condition removes Rahim himself, who would otherwise fail only the job test and not appear anyway — but it is included for clarity and safety if names are duplicated.

    Self-join alternative, usually faster
    ```sql
    SELECT  e.emp_name, e.job, e.salary
    FROM    Employee e
    JOIN    Employee r ON r.emp_name = 'Rahim'
    WHERE   e.salary = r.salary
      AND   e.job   <> r.job;
    ```

    Sample output
    ```
    Employee
    +----------+-----------+--------+
    | emp_name | job       | salary |
    +----------+-----------+--------+
    | Rahim    | Developer | 50000  |
    | Karim    | Analyst   | 50000  |   <- same salary, different job  ✓
    | Sumi     | Developer | 50000  |   <- same salary, SAME job       ✗
    | Nabil    | Analyst   | 60000  |   <- different salary            ✗
    +----------+-----------+--------+

    Result
    +----------+---------+--------+
    | emp_name | job     | salary |
    +----------+---------+--------+
    | Karim    | Analyst | 50000  |
    +----------+---------+--------+
    ```

    (ii) Employees whose department's average salary exceeds the company average

    - Reading the question as "employees working in a department whose average salary is above the company-wide average":
    ```sql
    SELECT  e.emp_name, e.salary, d.dept_name
    FROM    Employee e
    JOIN    Department d ON e.dept_id = d.dept_id
    WHERE   e.dept_id IN (
                SELECT dept_id
                FROM   Employee
                GROUP  BY dept_id
                HAVING AVG(salary) > (SELECT AVG(salary) FROM Employee)
            );
    ```
    - The innermost query gives the company average; the middle query lists the departments beating it; the outer query lists the employees in those departments.

    - Reading it instead as "employees whose own salary exceeds the company average":
    ```sql
    SELECT emp_name, salary
    FROM   Employee
    WHERE  salary > (SELECT AVG(salary) FROM Employee);
    ```

    To list the qualifying departments themselves
    ```sql
    SELECT   d.dept_name, AVG(e.salary) AS dept_avg
    FROM     Employee e JOIN Department d ON e.dept_id = d.dept_id
    GROUP BY d.dept_id, d.dept_name
    HAVING   AVG(e.salary) > (SELECT AVG(salary) FROM Employee);
    ```

25. **EMPLOYEES (Emp_ID, Emp_Name, Manager_ID, Dept_ID);**
   **DEPARTMENTS (Dept ID, Salary, Dept Name, Emp_ID);**
   * **(a) Find out the names of the manager for each employee:**
   * **(b) Sort the employees total salary of each department based on salary in descending order.** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 431 (ET: BUET)]*

    Answer:

    Schema
    ```
    EMPLOYEES   (Emp_ID, Emp_Name, Manager_ID, Dept_ID)
    DEPARTMENTS (Dept_ID, Salary, Dept_Name, Emp_ID)
    ```

    (a) The name of the manager for each employee

    - `Manager_ID` points back into EMPLOYEES, so the table must be joined to `itself` — a self join.
    ```sql
    SELECT  e.Emp_ID,
            e.Emp_Name             AS Employee_Name,
            m.Emp_Name             AS Manager_Name
    FROM    EMPLOYEES e
    LEFT JOIN EMPLOYEES m ON e.Manager_ID = m.Emp_ID
    ORDER BY e.Emp_ID;
    ```
    - `LEFT JOIN` rather than `JOIN`, so that the topmost employee — whose `Manager_ID` is NULL — is still listed, with NULL as the manager. An inner join would silently drop them.

    Sample output
    ```
    EMPLOYEES
    +--------+----------+------------+
    | Emp_ID | Emp_Name | Manager_ID |
    +--------+----------+------------+
    |  101   | Karim    |    NULL    |     <- the CEO
    |  102   | Rahim    |    101     |
    |  103   | Sumi     |    101     |
    |  104   | Nabil    |    102     |
    +--------+----------+------------+

    Result
    +--------+---------------+--------------+
    | Emp_ID | Employee_Name | Manager_Name |
    +--------+---------------+--------------+
    |  101   | Karim         |     NULL     |
    |  102   | Rahim         |    Karim     |
    |  103   | Sumi          |    Karim     |
    |  104   | Nabil         |    Rahim     |
    +--------+---------------+--------------+
    ```
    - To show a label instead of NULL:
    ```sql
    SELECT e.Emp_Name, COALESCE(m.Emp_Name, 'No Manager') AS Manager_Name
    FROM   EMPLOYEES e LEFT JOIN EMPLOYEES m ON e.Manager_ID = m.Emp_ID;
    ```

    (b) Total salary of each department, sorted in descending order

    - Taking the salary from the DEPARTMENTS relation as the schema states:
    ```sql
    SELECT   Dept_Name,
             SUM(Salary) AS Total_Salary
    FROM     DEPARTMENTS
    GROUP BY Dept_ID, Dept_Name
    ORDER BY Total_Salary DESC;
    ```

    - If salary is in fact an employee attribute, which is the normal design, the join form is:
    ```sql
    SELECT   d.Dept_Name,
             SUM(e.Salary) AS Total_Salary
    FROM     EMPLOYEES   e
    JOIN     DEPARTMENTS d ON e.Dept_ID = d.Dept_ID
    GROUP BY d.Dept_ID, d.Dept_Name
    ORDER BY Total_Salary DESC;
    ```

    Sample output
    ```
    +-----------+--------------+
    | Dept_Name | Total_Salary |
    +-----------+--------------+
    | IT        |    250000    |
    | Sales     |    180000    |
    | HR        |     95000    |
    +-----------+--------------+
    ```
    - Note a design flaw worth mentioning: the schema places `Salary` in DEPARTMENTS and `Emp_ID` in DEPARTMENTS as well, which duplicates the relationship already expressed by `EMPLOYEES.Dept_ID`. A normalised design would keep salary with the employee and keep only `Manager_Emp_ID` in the department table.

26. **Given Four table:**
   * **Employee (empno(PK), empname, monthlysalary, deptno, mqrnd(FK))**
   * **Department(deptno, deptname, deptlocation)**
   * **Course(erscode(pk) erd dese, ers category, ers duration)**
   * **Offering (of begingate, erscode fk, offeringlocation, empno fk)**
   **Write query for:**
   * **(a) Find Departments with Average Monthly Salary Greater than 1000.**
   * **(b) Find Courses with More Than 2 Offerings.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1456 (ET: BUET)]*

    Answer:

    Schema (as given, with the obvious typographical errors corrected)
    ```
    Employee   (empno PK, empname, monthlysalary, deptno, mgrno FK)
    Department (deptno PK, deptname, deptlocation)
    Course     (crscode PK, crsdesc, crscategory, crsduration)
    Offering   (ofbegindate, crscode FK, offeringlocation, empno FK)
    ```

    (a) Departments with an average monthly salary greater than 1000
    ```sql
    SELECT   d.deptno,
             d.deptname,
             AVG(e.monthlysalary) AS avg_salary
    FROM     Employee   e
    JOIN     Department d ON e.deptno = d.deptno
    GROUP BY d.deptno, d.deptname
    HAVING   AVG(e.monthlysalary) > 1000;
    ```
    - `GROUP BY` produces one row per department.
    - The condition tests an `aggregate`, so it must be in `HAVING`, not `WHERE`. Writing `WHERE AVG(...) > 1000` is a syntax error, because WHERE is evaluated before the rows are grouped.

    Sample output
    ```
    +--------+-----------+------------+
    | deptno | deptname  | avg_salary |
    +--------+-----------+------------+
    |   10   | IT        |   1450.00  |
    |   20   | Sales     |   1200.00  |
    +--------+-----------+------------+
    ```
    - A department averaging 950 would be excluded.

    Without the department name, if only Employee is available
    ```sql
    SELECT   deptno, AVG(monthlysalary) AS avg_salary
    FROM     Employee
    GROUP BY deptno
    HAVING   AVG(monthlysalary) > 1000;
    ```

    (b) Courses with more than 2 offerings
    ```sql
    SELECT   c.crscode,
             c.crsdesc,
             COUNT(*) AS number_of_offerings
    FROM     Course   c
    JOIN     Offering o ON c.crscode = o.crscode
    GROUP BY c.crscode, c.crsdesc
    HAVING   COUNT(*) > 2;
    ```
    - Each row of `Offering` is one occasion on which the course was run, so counting the rows per course gives the number of offerings.

    Sample output
    ```
    +---------+------------------+---------------------+
    | crscode | crsdesc          | number_of_offerings |
    +---------+------------------+---------------------+
    | DB101   | Database Systems |          4          |
    | NW202   | Networking       |          3          |
    +---------+------------------+---------------------+
    ```

    Including courses that have never been offered
    ```sql
    SELECT   c.crscode, c.crsdesc, COUNT(o.crscode) AS number_of_offerings
    FROM     Course c
    LEFT JOIN Offering o ON c.crscode = o.crscode
    GROUP BY c.crscode, c.crsdesc;
    ```
    - `COUNT(o.crscode)` rather than `COUNT(*)` is essential here: it counts non-null values and therefore correctly reports 0 for a course with no offerings, whereas `COUNT(*)` would report 1.

27. **6.4 Consider the following relation: Employee(EmpID, Name, Department, Salary). Write an SQL query to retrieve the Department, the total number of employees, and the average salary for each department. The output should display one record for each department.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

    Answer: One row per department is required, which means `GROUP BY Department` together with the aggregates `COUNT` and `AVG`.

    Query
    ```sql
    SELECT   Department,
             COUNT(*)    AS Total_Employees,
             AVG(Salary) AS Average_Salary
    FROM     Employee
    GROUP BY Department;
    ```

    Explanation
    - `GROUP BY Department` gathers all employees of a department into one group, which produces exactly one output row per department.
    - `COUNT(*)` counts the rows in each group — the number of employees.
    - `AVG(Salary)` averages the salaries within the group.
    - Every column in the SELECT list is either the grouping column or inside an aggregate, which is the rule SQL enforces.

    Sample data and result
    ```
    Employee
    +-------+--------+------------+--------+
    | EmpID | Name   | Department | Salary |
    +-------+--------+------------+--------+
    |   1   | Karim  | IT         | 50000  |
    |   2   | Rahim  | IT         | 60000  |
    |   3   | Sumi   | HR         | 40000  |
    |   4   | Nabil  | HR         | 45000  |
    |   5   | Jamil  | Accounts   | 55000  |
    +-------+--------+------------+--------+

    Result
    +------------+-----------------+----------------+
    | Department | Total_Employees | Average_Salary |
    +------------+-----------------+----------------+
    | IT         |        2        |     55000      |
    | HR         |        2        |     42500      |
    | Accounts   |        1        |     55000      |
    +------------+-----------------+----------------+
    ```

    Polished version
    ```sql
    SELECT   Department,
             COUNT(*)              AS Total_Employees,
             ROUND(AVG(Salary), 2) AS Average_Salary
    FROM     Employee
    GROUP BY Department
    ORDER BY Average_Salary DESC;
    ```

    Points examiners look for
    - `COUNT(*)` counts all rows; `COUNT(Salary)` would skip rows where Salary is NULL.
    - `AVG` also ignores NULLs, so its divisor is the number of non-null salaries.
    - To filter the departments themselves, use `HAVING`, never `WHERE`:
    ```sql
    HAVING COUNT(*) > 2 AND AVG(Salary) > 45000
    ```

28. **Analize the following code:**
```sql
SELECT department_name, AVG(salary) as average_salary
FROM employees
JOIN department d ON e.department_id = d.department_id
WHERE salary > (SELECT AVG(salary) FROM employees )
GROUP BY department_name
HAVING COUNT(*) > 2
ORDER BY average_salary desc
```
*[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 521 (ET: MIST)]*

    Answer: The query is intended to list departments whose average salary is high, but as written it `will not run`, and its logic is also questionable.

    The code
    ```sql
    SELECT department_name, AVG(salary) as average_salary
    FROM employees
    JOIN department d ON e.department_id = d.department_id
    WHERE salary > (SELECT AVG(salary) FROM employees )
    GROUP BY department_name
    HAVING COUNT(*) > 2
    ORDER BY average_salary desc
    ```

    Errors

    1. `Missing table alias` — the fatal one
    - `FROM employees` declares no alias, yet the ON clause refers to `e.department_id`. The identifier `e` is undefined, so the statement fails with "unknown alias e".
    - Fix: `FROM employees e`.

    2. `Inconsistent table name`
    - The table is called `department` (singular) here but is usually `departments`. Whichever is correct, it must match the schema.

    3. `Ambiguous column references`
    - `salary` and `department_name` are unqualified. If both tables happened to contain a column of that name the query would be ambiguous. Qualifying every column (`e.salary`, `d.department_name`) is good practice.

    Corrected version
    ```sql
    SELECT   d.department_name,
             AVG(e.salary) AS average_salary
    FROM     employees   e
    JOIN     departments d ON e.department_id = d.department_id
    WHERE    e.salary > (SELECT AVG(salary) FROM employees)
    GROUP BY d.department_name
    HAVING   COUNT(*) > 2
    ORDER BY average_salary DESC;
    ```

    What the corrected query actually does, clause by clause
    - `FROM ... JOIN` — pairs each employee with their department.
    - `WHERE e.salary > (SELECT AVG(salary) FROM employees)` — keeps only employees earning more than the `company-wide` average. This subquery is `not correlated`: it is computed once, and returns a single number for the whole query.
    - `GROUP BY d.department_name` — groups the surviving rows by department.
    - `HAVING COUNT(*) > 2` — keeps only departments in which `more than two` of those above-average earners remain.
    - `AVG(e.salary)` — note carefully that this is the average `of the filtered rows only`, not of the whole department. It is the average salary of the department's above-average earners.
    - `ORDER BY average_salary DESC` — highest first.

    The logical subtlety worth stating
    - Because `WHERE` runs before `GROUP BY`, the average reported is `not` the department's true average. A department where three people earn well above the company average and twenty earn below it would report a very high figure.
    - If the department's genuine average is wanted, the filter must be moved into `HAVING`:
    ```sql
    SELECT   d.department_name, AVG(e.salary) AS average_salary
    FROM     employees e JOIN departments d ON e.department_id = d.department_id
    GROUP BY d.department_name
    HAVING   COUNT(*) > 2
         AND AVG(e.salary) > (SELECT AVG(salary) FROM employees)
    ORDER BY average_salary DESC;
    ```
    - Summary: the query has one fatal syntax error (the missing alias) and one conceptual trap (WHERE filtering rows before the average is computed).

29. **Employee Salary sql query a. Sum b. Avg. C. Employee_Name all 2nd letter 'a'......** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 508 (ET: N/A)]*

    Answer: Assuming the table `Employee(emp_id, Employee_Name, Salary, dept_id)`.

    (a) Sum of salaries
    ```sql
    -- total salary of the whole organisation
    SELECT SUM(Salary) AS Total_Salary FROM Employee;

    -- total salary per department
    SELECT   dept_id, SUM(Salary) AS Total_Salary
    FROM     Employee
    GROUP BY dept_id;
    ```

    (b) Average salary
    ```sql
    -- overall average
    SELECT AVG(Salary) AS Average_Salary FROM Employee;

    -- average per department, rounded
    SELECT   dept_id, ROUND(AVG(Salary), 2) AS Average_Salary
    FROM     Employee
    GROUP BY dept_id;

    -- employees earning above the overall average
    SELECT Employee_Name, Salary FROM Employee
    WHERE  Salary > (SELECT AVG(Salary) FROM Employee);
    ```

    (c) Employees whose name has 'a' as the second letter
    ```sql
    SELECT  Employee_Name
    FROM    Employee
    WHERE   Employee_Name LIKE '_a%';
    ```
    - The pattern `_a%` reads as: `_` matches exactly one character, `a` is the literal second character, `%` matches any number of remaining characters.

    Sample data and output
    ```
    Employee_Name
    +---------------+
    | Karim         |   ->  K a rim   -> 2nd letter is 'a'  ✓
    | Rahim         |   ->  R a him   ->                    ✓
    | Sumi          |   ->  S u mi    ->                    ✗
    | Nabil         |   ->  N a bil   ->                    ✓
    | Jamil         |   ->  J a mil   ->                    ✓
    +---------------+

    Result: Karim, Rahim, Nabil, Jamil
    ```

    The LIKE wildcards
    ```
    %  any sequence of characters, including none
    _  exactly one character
    ```

    | Pattern | Matches |
    |---|---|
    | `'a%'` | Starts with a |
    | `'%a'` | Ends with a |
    | `'%a%'` | Contains a anywhere |
    | `'_a%'` | Second letter is a |
    | `'__a%'` | Third letter is a |
    | `'a_%_%'` | Starts with a and is at least 3 characters long |

    - Case sensitivity depends on the collation. MySQL's default collation is case-insensitive, so `'_a%'` would also match `KArim`. To force a case-sensitive match use `LIKE BINARY '_a%'` in MySQL, or `WHERE SUBSTRING(Employee_Name, 2, 1) = 'a'` portably.
    - Equivalent without LIKE:
    ```sql
    SELECT Employee_Name FROM Employee
    WHERE  SUBSTRING(Employee_Name, 2, 1) = 'a';
    ```

30. **Analyze the output of the following SQL :** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 543 (ET: MIST)]*
```sql
SELECT department_name, AVG(salary) AS average_salary
FROM employees e
JOIN departments d ON e.department_id=d.department_id
WHERE salary> (SELECT AVG(salary) FROM employees WHERE department_id=d.department_id)
GROUP BY department_name
HAVING COUNT(*)>2
ORDER BY average_salary DESC;
```

    Answer: This version is `syntactically correct`, unlike the similar query with the missing alias, but it contains a subtle logical point that is the whole purpose of the question.

    The query
    ```sql
    SELECT department_name, AVG(salary) AS average_salary
    FROM employees e
    JOIN departments d ON e.department_id = d.department_id
    WHERE salary > (SELECT AVG(salary) FROM employees WHERE department_id = d.department_id)
    GROUP BY department_name
    HAVING COUNT(*) > 2
    ORDER BY average_salary DESC;
    ```

    Clause-by-clause analysis

    - `FROM employees e JOIN departments d ON e.department_id = d.department_id`
      - Pairs each employee with their department. Employees with a NULL department_id are dropped, as are departments with no employees.

    - `WHERE salary > (SELECT AVG(salary) FROM employees WHERE department_id = d.department_id)`
      - This is a `correlated subquery`: it refers to `d.department_id` from the outer query, so it is re-evaluated `for every row`.
      - For each employee it computes the average salary of `that employee's own department`, and keeps the employee only if they earn more than it.
      - This is the crucial difference from the non-correlated version `(SELECT AVG(salary) FROM employees)`, which compares against the `company-wide` average instead.

    - `GROUP BY department_name`
      - Groups the surviving rows — the above-department-average earners — by department.

    - `HAVING COUNT(*) > 2`
      - Keeps only departments in which `more than two` employees beat their own department's average.

    - `AVG(salary)`
      - Averages `only the filtered rows`. So the figure reported is the average salary of the department's above-average earners, `not` the department's true average. It will always be higher than the department average.

    - `ORDER BY average_salary DESC`
      - Highest first.

    What the query returns, in one sentence
    > For every department in which more than two employees earn more than that department's own average salary, the department name and the average salary of just those high earners, listed highest first.

    Worked example
    ```
    employees
    +------+---------------+--------+
    | name | department_id | salary |
    +------+---------------+--------+
    | A    |      10       | 90000  |
    | B    |      10       | 85000  |
    | C    |      10       | 80000  |
    | D    |      10       | 40000  |
    | E    |      10       | 35000  |
    | F    |      20       | 70000  |
    | G    |      20       | 30000  |
    +------+---------------+--------+

    Dept 10 average = (90+85+80+40+35)/5 = 66000
      Above it: A, B, C  -> 3 employees, COUNT(*) = 3 > 2  ✓
      AVG of those three = (90000+85000+80000)/3 = 85000

    Dept 20 average = (70000+30000)/2 = 50000
      Above it: F only   -> COUNT(*) = 1, not > 2          ✗

    Result
    +-----------------+----------------+
    | department_name | average_salary |
    +-----------------+----------------+
    | IT (dept 10)    |     85000      |
    +-----------------+----------------+
    ```

    Performance note
    - A correlated subquery is re-executed once per row, so on a large table this is slow. A window function does the same work in a single pass:
    ```sql
    SELECT department_name, AVG(salary) AS average_salary
    FROM (
        SELECT d.department_name, e.salary,
               AVG(e.salary) OVER (PARTITION BY e.department_id) AS dept_avg
        FROM   employees e JOIN departments d ON e.department_id = d.department_id
    ) t
    WHERE  salary > dept_avg
    GROUP  BY department_name
    HAVING COUNT(*) > 2
    ORDER  BY average_salary DESC;
    ```

31. **Consider the employee tables: Create a SQL view that shows the details of Employee information who have the salary equivalent to the maximum, minimum and average salary of employee.** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 473 (ET: N/A)]*

    Answer:

    Query
    ```sql
    CREATE VIEW Salary_Extremes AS
    SELECT  e.emp_id,
            e.emp_name,
            e.salary,
            e.dept_id,
            CASE
                WHEN e.salary = (SELECT MAX(salary) FROM Employee) THEN 'Maximum'
                WHEN e.salary = (SELECT MIN(salary) FROM Employee) THEN 'Minimum'
                ELSE 'Average'
            END AS Salary_Category
    FROM    Employee e
    WHERE   e.salary IN (
                SELECT MAX(salary) FROM Employee
                UNION
                SELECT MIN(salary) FROM Employee
                UNION
                SELECT AVG(salary) FROM Employee
            );
    ```

    How it works
    - The three subqueries produce the maximum, the minimum and the average salary; `UNION` combines them into one list of three values.
    - `WHERE e.salary IN (...)` keeps only employees whose salary equals one of those three figures.
    - The `CASE` expression labels each row, so the output shows which of the three it matched.

    Simpler version without the label
    ```sql
    CREATE VIEW Salary_Extremes AS
    SELECT *
    FROM   Employee
    WHERE  salary = (SELECT MAX(salary) FROM Employee)
       OR  salary = (SELECT MIN(salary) FROM Employee)
       OR  salary = (SELECT AVG(salary) FROM Employee);
    ```

    Using the view
    ```sql
    SELECT * FROM Salary_Extremes;
    SELECT * FROM Salary_Extremes WHERE Salary_Category = 'Maximum';
    DROP VIEW Salary_Extremes;
    ```

    Sample output
    ```
    Employee salaries: 30000, 45000, 50000, 60000, 90000
    MAX = 90000 ; MIN = 30000 ; AVG = 55000

    +--------+----------+--------+-----------------+
    | emp_id | emp_name | salary | Salary_Category |
    +--------+----------+--------+-----------------+
    |   1    | Karim    | 90000  | Maximum         |
    |   5    | Jamil    | 30000  | Minimum         |
    +--------+----------+--------+-----------------+
    ```
    - No employee earns exactly 55000, so no row matches the average. That is normal, and it is worth stating: an exact match on `AVG` is rare because the average is usually a fractional value that no individual salary equals.

    A more useful variant — the employee nearest to the average
    ```sql
    CREATE VIEW Salary_Summary AS
    SELECT emp_id, emp_name, salary, 'Maximum' AS category FROM Employee
    WHERE  salary = (SELECT MAX(salary) FROM Employee)
    UNION ALL
    SELECT emp_id, emp_name, salary, 'Minimum' FROM Employee
    WHERE  salary = (SELECT MIN(salary) FROM Employee)
    UNION ALL
    SELECT emp_id, emp_name, salary, 'Closest to Average' FROM Employee
    ORDER  BY ABS(salary - (SELECT AVG(salary) FROM Employee))
    LIMIT  1;
    ```

    What a view is, and why it is used here
    - A `view` is a stored query that behaves like a virtual table. It holds no data of its own; the underlying SELECT runs each time the view is queried.
    - Benefits: it hides complexity behind a simple name, restricts which columns and rows a user can see (a security mechanism), presents the data in a consistent form, and lets the underlying tables change without breaking applications.

32. **SQL query for employee table. (Approximate)** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 476 (ET: N/A)]*

    Answer: The exact query was not printed, so the employee-table queries that appear repeatedly in these examinations are worked through, using
    ```
    Employee (emp_id, emp_name, salary, dept_id, job, hire_date, manager_id, city)
    ```

    Basic retrieval
    ```sql
    SELECT * FROM Employee;
    SELECT emp_name, salary FROM Employee WHERE salary > 30000;
    SELECT * FROM Employee WHERE salary BETWEEN 20000 AND 50000;
    SELECT * FROM Employee WHERE city = 'Dhaka' AND job = 'Officer';
    SELECT * FROM Employee WHERE emp_name LIKE 'A%';
    SELECT * FROM Employee WHERE dept_id IN (10, 20);
    SELECT * FROM Employee WHERE manager_id IS NULL;
    SELECT * FROM Employee ORDER BY salary DESC;
    SELECT DISTINCT job FROM Employee;
    ```

    Aggregates
    ```sql
    SELECT COUNT(*), SUM(salary), AVG(salary), MAX(salary), MIN(salary) FROM Employee;

    SELECT   dept_id, COUNT(*) AS staff, AVG(salary) AS avg_salary
    FROM     Employee
    GROUP BY dept_id
    HAVING   COUNT(*) > 2
    ORDER BY avg_salary DESC;
    ```

    Subqueries
    ```sql
    -- above the overall average
    SELECT emp_name, salary FROM Employee
    WHERE  salary > (SELECT AVG(salary) FROM Employee);

    -- above their own department's average
    SELECT e.emp_name FROM Employee e
    WHERE  e.salary > (SELECT AVG(x.salary) FROM Employee x WHERE x.dept_id = e.dept_id);

    -- second highest salary
    SELECT MAX(salary) FROM Employee
    WHERE  salary < (SELECT MAX(salary) FROM Employee);

    -- highest paid in each department
    SELECT dept_id, emp_name, salary FROM Employee e
    WHERE  salary = (SELECT MAX(salary) FROM Employee WHERE dept_id = e.dept_id);
    ```

    Self join
    ```sql
    SELECT e.emp_name AS employee, m.emp_name AS manager
    FROM   Employee e LEFT JOIN Employee m ON e.manager_id = m.emp_id;

    SELECT e.emp_name FROM Employee e JOIN Employee m ON e.manager_id = m.emp_id
    WHERE  e.salary > m.salary;              -- earning more than their manager
    ```

    Duplicates
    ```sql
    SELECT emp_name, COUNT(*) FROM Employee
    GROUP  BY emp_name HAVING COUNT(*) > 1;
    ```

    Date queries
    ```sql
    SELECT * FROM Employee WHERE hire_date >= '2020-01-01';
    SELECT * FROM Employee WHERE YEAR(hire_date) = 2023;
    SELECT emp_name, DATEDIFF(CURDATE(), hire_date)/365 AS years_of_service FROM Employee;
    ```

    Modification
    ```sql
    INSERT INTO Employee VALUES (101,'Karim',45000,10,'Analyst','2024-01-15',5,'Dhaka');
    UPDATE Employee SET salary = salary * 1.10 WHERE dept_id = 10;
    DELETE FROM Employee WHERE hire_date < '2010-01-01';
    ```

    String functions
    ```sql
    SELECT UPPER(emp_name), LENGTH(emp_name), SUBSTRING(emp_name, 1, 3) FROM Employee;
    SELECT CONCAT(emp_name, ' - ', job) AS label FROM Employee;
    ```
    - The single rule that resolves most of these: SQL evaluates `FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY`, so `WHERE` filters rows and `HAVING` filters groups. <!-- verify -->

33. **Suppose we have a relational database with five tables. table key Attributes S(sid, A) Sid T(tid, B) Tid U(uid, C) Uid R(sid, tid, D) sid, tid Q(tid, uid, E) tid, uid Here R implements a many-to-many relationship between the entities implemented with tables S and T, and Q implements a many-to-many relationship between the entities implemented with tables T and U.**
   **(A) Write an SQL query that returns all records of the form sid, uid where sid is the key of an S- record and uid is the key of a U-record and these two records are related through the relations R and Q. Use SELECT and not SELECT DISTINCT in your query.**
   **(B) Write an SQL query that returns records of the form A, C where the A-value is from an S- record and the C-value is from a U-record and these two records are related through the relations R and Q. Use SELECT and not SELECT DISTINCT in your query.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 496 (ET: N/A)]*

    Answer:

    Schema
    ```
    S(sid, A)          key: sid
    T(tid, B)          key: tid
    U(uid, C)          key: uid
    R(sid, tid, D)     key: (sid, tid)   -- many-to-many between S and T
    Q(tid, uid, E)     key: (tid, uid)   -- many-to-many between T and U
    ```
    - An S-record and a U-record are related when there is a `tid` that appears both in an R row with that sid and in a Q row with that uid. R and Q therefore have to be joined through `T`.

    (A) All sid, uid pairs related through R and Q
    ```sql
    SELECT  R.sid, Q.uid
    FROM    R, Q
    WHERE   R.tid = Q.tid;
    ```
    Equivalent explicit-join form
    ```sql
    SELECT  R.sid, Q.uid
    FROM    R
    JOIN    Q ON R.tid = Q.tid;
    ```
    - Tables S, T and U are not needed at all: `sid` is already in R, `uid` is already in Q, and the join is over `tid`, which both contain. Adding the other tables would only slow the query down.
    - `SELECT` rather than `SELECT DISTINCT` is used as the question requires, so a pair appears once for every distinct `tid` connecting them. If S1 and U1 are linked through two different T-records, the pair (S1, U1) appears twice.

    (B) All A, C pairs related through R and Q
    ```sql
    SELECT  S.A, U.C
    FROM    S, R, Q, U
    WHERE   S.sid = R.sid
      AND   R.tid = Q.tid
      AND   Q.uid = U.uid;
    ```
    Equivalent explicit-join form
    ```sql
    SELECT  S.A, U.C
    FROM    S
    JOIN    R ON S.sid = R.sid
    JOIN    Q ON R.tid = Q.tid
    JOIN    U ON Q.uid = U.uid;
    ```
    - Here S and U `are` required, because the attributes A and C live in them, not in R or Q. The full four-table chain is therefore necessary.
    - Again `SELECT` rather than `SELECT DISTINCT`, so duplicates arising from multiple connecting tids are retained.

    The join path, drawn
    ```
       S ---(sid)--- R ---(tid)--- Q ---(uid)--- U
       A                                          C
    ```

    Why DISTINCT would change the answer
    - Suppose S1 relates to both T1 and T2, and both T1 and T2 relate to U1. Then:
    ```
    R: (S1, T1), (S1, T2)
    Q: (T1, U1), (T2, U1)

    Join on tid gives:  (S1, U1) twice
    ```
    - With `SELECT` the pair appears twice; with `SELECT DISTINCT` it would appear once. The question deliberately asks for the former, so the multiplicity is preserved.

34. **Write following EMPLOYEE database table write an SQL query to find employee who work is a department where the average salary is lower then the average salary all the department......** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 452 (ET: BUET)]*

    Answer: The requirement is to find employees working in a department whose `average salary is lower than the overall average of all departments`. Two subqueries are needed, one nested inside the other.

    Query
    ```sql
    SELECT  e.emp_id,
            e.emp_name,
            e.salary,
            e.dept_id
    FROM    Employee e
    WHERE   e.dept_id IN (
                SELECT   dept_id
                FROM     Employee
                GROUP BY dept_id
                HAVING   AVG(salary) < (
                           SELECT AVG(dept_avg)
                           FROM ( SELECT AVG(salary) AS dept_avg
                                  FROM   Employee
                                  GROUP  BY dept_id ) AS t
                         )
            );
    ```

    How it works, from the inside out
    - The innermost derived table computes `each department's average salary`.
    - `AVG(dept_avg)` over those values gives the `average of the department averages`.
    - The middle query lists the departments whose own average falls below that figure.
    - The outer query returns the employees working in those departments.

    The important distinction
    - "The average salary of all the departments" can mean two different things, and they are not the same number:
      - `AVG(salary) over all employees` — every employee counts equally.
      - `AVG of the department averages` — every department counts equally, regardless of size.
    - The wording "lower than the average salary of all the departments" points at the second reading, which is what the query above implements.

    The simpler reading — compared with the company-wide employee average
    ```sql
    SELECT e.emp_id, e.emp_name, e.salary, e.dept_id
    FROM   Employee e
    WHERE  e.dept_id IN (
              SELECT   dept_id
              FROM     Employee
              GROUP BY dept_id
              HAVING   AVG(salary) < (SELECT AVG(salary) FROM Employee)
           );
    ```

    Worked example
    ```
    Employee
    +--------+----------+--------+---------+
    | emp_id | emp_name | salary | dept_id |
    +--------+----------+--------+---------+
    |   1    | Karim    | 80000  |   10    |
    |   2    | Rahim    | 70000  |   10    |
    |   3    | Sumi     | 40000  |   20    |
    |   4    | Nabil    | 30000  |   20    |
    |   5    | Jamil    | 50000  |   30    |
    +--------+----------+--------+---------+

    Department averages: 10 -> 75000 ; 20 -> 35000 ; 30 -> 50000
    Average of those averages = (75000 + 35000 + 50000) / 3 = 53333
    Company-wide employee average = 270000 / 5 = 54000

    Departments below the average of averages: 20 (35000), 30 (50000)

    Result
    +--------+----------+--------+---------+
    | emp_id | emp_name | salary | dept_id |
    +--------+----------+--------+---------+
    |   3    | Sumi     | 40000  |   20    |
    |   4    | Nabil    | 30000  |   20    |
    |   5    | Jamil    | 50000  |   30    |
    +--------+----------+--------+---------+
    ```

    Just the departments, without the employees
    ```sql
    SELECT   dept_id, AVG(salary) AS dept_avg
    FROM     Employee
    GROUP BY dept_id
    HAVING   AVG(salary) < (SELECT AVG(salary) FROM Employee);
    ```

35. **Consider the two schema employees (id, first_name, last_name, designation, oining_date, salary, dept_id) and department (dept_id, dept_name). Where detp_id is forgeign key. Find the first_name and department name whose salary is maximum.** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 459 (ET: BUET)]*

    Answer:

    Schema
    ```
    employees  (id, first_name, last_name, designation, joining_date, salary, dept_id)
    department (dept_id, dept_name)
    ```

    Query
    ```sql
    SELECT  e.first_name,
            d.dept_name,
            e.salary
    FROM    employees  e
    JOIN    department d ON e.dept_id = d.dept_id
    WHERE   e.salary = (SELECT MAX(salary) FROM employees);
    ```

    How it works
    - The subquery `(SELECT MAX(salary) FROM employees)` returns the single highest salary in the whole company.
    - The outer query joins each employee to their department and keeps only those earning exactly that amount.
    - Using `= MAX(...)` rather than `ORDER BY salary DESC LIMIT 1` correctly returns `all` employees if several share the top salary — which is the point examiners usually check.

    Sample data and result
    ```
    employees                                 department
    +----+------------+--------+---------+    +---------+-----------+
    | id | first_name | salary | dept_id |    | dept_id | dept_name |
    +----+------------+--------+---------+    +---------+-----------+
    | 1  | Karim      | 90000  |   10    |    |   10    | IT        |
    | 2  | Rahim      | 75000  |   10    |    |   20    | HR        |
    | 3  | Sumi       | 60000  |   20    |    +---------+-----------+
    | 4  | Nabil      | 90000  |   20    |
    +----+------------+--------+---------+

    Highest salary = 90000

    Result
    +------------+-----------+--------+
    | first_name | dept_name | salary |
    +------------+-----------+--------+
    | Karim      | IT        | 90000  |
    | Nabil      | HR        | 90000  |
    +------------+-----------+--------+
    ```

    Alternative with ORDER BY and LIMIT
    ```sql
    SELECT e.first_name, d.dept_name, e.salary
    FROM   employees e JOIN department d ON e.dept_id = d.dept_id
    ORDER  BY e.salary DESC
    LIMIT  1;
    ```
    - Shorter, but returns only `one` row even when there is a tie, so it is not equivalent.

    Related variation — highest paid `in each` department
    ```sql
    SELECT  e.first_name, d.dept_name, e.salary
    FROM    employees e
    JOIN    department d ON e.dept_id = d.dept_id
    WHERE   e.salary = (SELECT MAX(x.salary) FROM employees x WHERE x.dept_id = e.dept_id);
    ```
    - The subquery is now `correlated` — it recomputes the maximum for each employee's own department.

    Window-function version, which reads more clearly and runs in one pass
    ```sql
    SELECT first_name, dept_name, salary FROM (
        SELECT e.first_name, d.dept_name, e.salary,
               RANK() OVER (PARTITION BY e.dept_id ORDER BY e.salary DESC) AS rnk
        FROM   employees e JOIN department d ON e.dept_id = d.dept_id
    ) t
    WHERE rnk = 1;
    ```

36. **Suppose that we have a relational database with the following table. Underlined one represent primary key**
   **Movies (\underline{\text{mid}}, title, year)**
   **People (\underline{\text{pid}}, name)**
   **Genres (\underline{\text{gid}}, genre)**
   **HasRole (\underline{\text{pid}, \text{mid}}, role)**
   **Has Genre (\underline{\text{gid}, \text{mid}})**
   **Write a SQL query to return the number of movies that are romantic comedies.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 436 (ET: BIBM)]*

    Answer:

    Schema
    ```
    Movies   (mid, title, year)
    People   (pid, name)
    Genres   (gid, genre)
    HasRole  (pid, mid, role)
    HasGenre (gid, mid)
    ```
    - A "romantic comedy" is a film that has `both` the genre `Romance` and the genre `Comedy`. This is the crucial point: it is not one genre but two, and a film qualifies only when both are present.

    Query — count movies having both genres
    ```sql
    SELECT COUNT(*) AS romantic_comedies
    FROM (
        SELECT   hg.mid
        FROM     HasGenre hg
        JOIN     Genres   g ON hg.gid = g.gid
        WHERE    g.genre IN ('Romance', 'Comedy')
        GROUP BY hg.mid
        HAVING   COUNT(DISTINCT g.genre) = 2
    ) AS t;
    ```

    How it works
    - `WHERE g.genre IN ('Romance', 'Comedy')` keeps only the genre rows of interest.
    - `GROUP BY hg.mid` gathers those rows per movie.
    - `HAVING COUNT(DISTINCT g.genre) = 2` keeps only the movies for which `both` genres are present. `DISTINCT` guards against a duplicate row listing the same genre twice.
    - The outer `COUNT(*)` then counts the qualifying movies.

    Alternative using INTERSECT
    ```sql
    SELECT COUNT(*) FROM (
        SELECT hg.mid FROM HasGenre hg JOIN Genres g ON hg.gid = g.gid
        WHERE  g.genre = 'Romance'
        INTERSECT
        SELECT hg.mid FROM HasGenre hg JOIN Genres g ON hg.gid = g.gid
        WHERE  g.genre = 'Comedy'
    ) AS t;
    ```
    - Reads very directly: movies in the Romance set `and` in the Comedy set. Not supported by MySQL, which lacks INTERSECT.

    Alternative by joining HasGenre to itself
    ```sql
    SELECT COUNT(DISTINCT h1.mid) AS romantic_comedies
    FROM   HasGenre h1
    JOIN   Genres   g1 ON h1.gid = g1.gid AND g1.genre = 'Romance'
    JOIN   HasGenre h2 ON h1.mid = h2.mid
    JOIN   Genres   g2 ON h2.gid = g2.gid AND g2.genre = 'Comedy';
    ```
    - Each movie is matched once through its Romance row and once through its Comedy row; `COUNT(DISTINCT h1.mid)` prevents double counting.

    The wrong answer to avoid
    ```sql
    -- WRONG: this counts movies that are Romance OR Comedy, not both
    SELECT COUNT(DISTINCT hg.mid)
    FROM   HasGenre hg JOIN Genres g ON hg.gid = g.gid
    WHERE  g.genre IN ('Romance', 'Comedy');
    ```
    - A single row cannot have `genre = 'Romance' AND genre = 'Comedy'` at the same time, so writing `AND` in the WHERE clause returns zero rows. The condition has to apply across `several rows` of the same movie, which is exactly what `GROUP BY ... HAVING` is for.

    Listing the titles instead of counting them
    ```sql
    SELECT   m.title, m.year
    FROM     Movies m
    JOIN     HasGenre hg ON m.mid = hg.mid
    JOIN     Genres   g  ON hg.gid = g.gid
    WHERE    g.genre IN ('Romance', 'Comedy')
    GROUP BY m.mid, m.title, m.year
    HAVING   COUNT(DISTINCT g.genre) = 2;
    ```

37. **(গ) ডাটাবেস সিস্টেমে view কী? এটি কী কী কাজে লাগে?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 627 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    What is a view
    - A `view` is a virtual table defined by a stored `SELECT` statement. It has a name and columns like a real table, but it holds `no data of its own` — the underlying query is executed each time the view is used.
    - The tables the view is built on are called the `base tables`.

    ```sql
    CREATE VIEW HighEarners AS
    SELECT emp_id, emp_name, salary, dept_id
    FROM   Employee
    WHERE  salary > 50000;

    -- used exactly like a table
    SELECT * FROM HighEarners WHERE dept_id = 10;

    DROP VIEW HighEarners;
    ```

    What views are used for

    - `Simplifying complex queries.` A join across five tables can be written once and then queried by name. Users work with a simple virtual table instead of repeating the join.
    ```sql
    CREATE VIEW EmployeeDetails AS
    SELECT e.emp_name, d.dept_name, l.city
    FROM   Employee e
    JOIN   Department d ON e.dept_id = d.dept_id
    JOIN   Location   l ON d.loc_id  = l.loc_id;
    ```

    - `Security and access control.` This is the most important use. A view can expose only some columns and only some rows, and permission can be granted on the view while the base table stays inaccessible. Salary and national ID can be hidden from ordinary staff, and a branch manager can be restricted to their own branch's rows.
    ```sql
    CREATE VIEW PublicStaff AS SELECT emp_name, designation FROM Employee;
    GRANT SELECT ON PublicStaff TO clerk;      -- no access to Employee itself
    ```

    - `Logical data independence.` If a base table is restructured, the view can be redefined to present the same columns, so existing applications and reports continue to work unchanged.

    - `Presenting derived and summarised data.` Computed columns and aggregates can be stored as a view, so every user gets the same definition of a business figure.
    ```sql
    CREATE VIEW DeptSummary AS
    SELECT dept_id, COUNT(*) AS staff, AVG(salary) AS avg_salary
    FROM   Employee GROUP BY dept_id;
    ```

    - `Consistency and reuse.` A calculation written once in a view cannot be got wrong differently by different developers.

    - `Restricting rows for different users` — the same base table can support many views, one per role or region.

    Limitations
    - A view is `not always updatable`. INSERT, UPDATE and DELETE through a view are only allowed when the view maps unambiguously to one base table — no aggregates, no GROUP BY, no DISTINCT, no joins in most systems.
    - Performance can suffer, since the underlying query runs every time. A `materialised view` (Oracle, PostgreSQL) actually stores the result and is refreshed periodically, trading freshness for speed.
    - Views cannot be indexed directly in most systems, though SQL Server's indexed views and Oracle's materialised views are exceptions.

38. **অথবা, নিম্নোক্ত টেবিলগুলো হতে (ক), (খ) এবং (গ) এর উত্তর দিন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 627 (ET: N/A)]*
   Restaurant (rid, rname, rcity, phone, seat-capacity)
   Dishes (did, dname, dtype)
   Customer (cid, cname, ccity)
   Serves (rid, did)

   **(ক) যে যে রেস্টুরেন্টগুলো ‘Burger’ পরিবেশন করে সেগুলোর নাম খুঁজে বের করার জন্য SQL Query লিখুন। (খ) ‘Ziman’ নামক একজন Customer যে যে খাবারগুলো অ্যালার্জি সংক্রান্ত সমস্যা এড়িয়ে খেতে পারেন তার তালিকা তৈরি করুন। (গ) যে যে খাবারগুলো ঢাকার সকল রেস্টুরেন্টে পাওয়া যায় তার তালিকা তৈরি করুন।**

    Answer: (Answered in English, as required for IT topics.)

    Schema
    ```
    Restaurant (rid, rname, rcity, phone, seat-capacity)
    Dishes     (did, dname, dtype)
    Customer   (cid, cname, ccity)
    Serves     (rid, did)
    ```

    (ক) Names of the restaurants that serve 'Burger'
    ```sql
    SELECT DISTINCT r.rname
    FROM   Restaurant r
    JOIN   Serves     s ON r.rid = s.rid
    JOIN   Dishes     d ON s.did = d.did
    WHERE  d.dname = 'Burger';
    ```
    - `Serves` is the many-to-many bridge between restaurants and dishes, so both joins are required.
    - `DISTINCT` guards against a restaurant appearing twice if it somehow lists the dish more than once.

    (খ) Dishes a customer named 'Ziman' can eat, avoiding allergy problems
    - The schema as given has `no allergy relation`, so this part cannot be answered exactly as printed. Assuming an additional table `Allergy(cid, dtype)` recording which dish types a customer is allergic to:
    ```sql
    SELECT d.dname, d.dtype
    FROM   Dishes d
    WHERE  d.dtype NOT IN (
              SELECT a.dtype
              FROM   Allergy  a
              JOIN   Customer c ON a.cid = c.cid
              WHERE  c.cname = 'Ziman'
           );
    ```
    - The subquery lists the dish types Ziman is allergic to; `NOT IN` keeps every dish that is not of one of those types.
    - `NOT EXISTS` is safer if the subquery could return NULL, because `NOT IN` returns no rows at all when a NULL is present:
    ```sql
    SELECT d.dname FROM Dishes d
    WHERE  NOT EXISTS (SELECT 1 FROM Allergy a JOIN Customer c ON a.cid = c.cid
                       WHERE c.cname = 'Ziman' AND a.dtype = d.dtype);
    ```

    (গ) Dishes available in `every` restaurant in Dhaka
    - This is a `relational division` problem: find dishes for which no Dhaka restaurant fails to serve them.

    Using NOT EXISTS — the standard division idiom
    ```sql
    SELECT d.dname
    FROM   Dishes d
    WHERE  NOT EXISTS (
              SELECT 1
              FROM   Restaurant r
              WHERE  r.rcity = 'Dhaka'
                AND  NOT EXISTS (
                        SELECT 1 FROM Serves s
                        WHERE  s.rid = r.rid AND s.did = d.did
                     )
           );
    ```
    - Read it as: "there is no Dhaka restaurant that does not serve this dish."

    Using GROUP BY and COUNT — often easier to follow
    ```sql
    SELECT   d.dname
    FROM     Dishes     d
    JOIN     Serves     s ON d.did = s.did
    JOIN     Restaurant r ON s.rid = r.rid
    WHERE    r.rcity = 'Dhaka'
    GROUP BY d.did, d.dname
    HAVING   COUNT(DISTINCT r.rid) = (SELECT COUNT(*) FROM Restaurant WHERE rcity = 'Dhaka');
    ```
    - A dish qualifies when the number of distinct Dhaka restaurants serving it equals the total number of Dhaka restaurants.
    - `COUNT(DISTINCT r.rid)` rather than `COUNT(*)` is important, in case Serves contains duplicate rows.

39. **SQL query from a given table.** *[BICIC Assistant Programmer 2022 compact it 634 (ET: BUET)]*

    Answer: The table was not printed, so the query forms these examinations set on a single table are worked through, using
    ```
    Employee (emp_id, emp_name, salary, dept_id, job, city, hire_date)
    ```

    Selection and filtering
    ```sql
    SELECT * FROM Employee;                                     -- everything
    SELECT emp_name, salary FROM Employee;                      -- chosen columns
    SELECT * FROM Employee WHERE salary > 30000;
    SELECT * FROM Employee WHERE city = 'Dhaka' AND job = 'Officer';
    SELECT * FROM Employee WHERE salary BETWEEN 20000 AND 50000;
    SELECT * FROM Employee WHERE dept_id IN (10, 20, 30);
    SELECT * FROM Employee WHERE emp_name LIKE 'S%';            -- starts with S
    SELECT * FROM Employee WHERE emp_name LIKE '_a%';           -- second letter a
    SELECT * FROM Employee WHERE manager_id IS NULL;
    SELECT DISTINCT job FROM Employee;
    ```

    Sorting and limiting
    ```sql
    SELECT * FROM Employee ORDER BY salary DESC;
    SELECT * FROM Employee ORDER BY dept_id ASC, salary DESC;
    SELECT * FROM Employee ORDER BY salary DESC LIMIT 5;        -- top 5 earners
    ```

    Aggregation
    ```sql
    SELECT COUNT(*), SUM(salary), AVG(salary), MAX(salary), MIN(salary) FROM Employee;

    SELECT   dept_id, COUNT(*) AS staff, AVG(salary) AS avg_salary
    FROM     Employee
    GROUP BY dept_id
    HAVING   COUNT(*) > 2
    ORDER BY avg_salary DESC;
    ```

    Subqueries
    ```sql
    SELECT emp_name FROM Employee WHERE salary > (SELECT AVG(salary) FROM Employee);

    SELECT MAX(salary) FROM Employee                            -- second highest
    WHERE  salary < (SELECT MAX(salary) FROM Employee);

    SELECT emp_name, COUNT(*) FROM Employee                     -- duplicates
    GROUP  BY emp_name HAVING COUNT(*) > 1;
    ```

    Data modification
    ```sql
    INSERT INTO Employee VALUES (101,'Karim',45000,10,'Analyst','Dhaka','2024-01-15');
    UPDATE Employee SET salary = salary * 1.10 WHERE dept_id = 10;
    DELETE FROM Employee WHERE hire_date < '2010-01-01';
    ```

    Table definition
    ```sql
    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,
        emp_name VARCHAR(50) NOT NULL,
        salary   DECIMAL(10,2) CHECK (salary > 0),
        dept_id  INT REFERENCES Department(dept_id)
    );
    ALTER TABLE Employee ADD COLUMN email VARCHAR(100);
    ```
    - The rule that answers most of these: SQL evaluates `FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY`. That is why `WHERE` cannot contain an aggregate and `HAVING` can. <!-- verify -->

40. **Employee table হতে Employee_id, Employee কে খোঁজে বের করার SQL Command লিখ যাদের গড় salary 2000 উপরে।** *[BTCL Junior Assistant Manager 2022 compact it 641 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) The requirement is employees whose average salary is above 2000. Since an individual has one salary, "average salary above 2000" is read at the `department` level — the standard interpretation of this question.

    Reading 1 — departments whose average salary exceeds 2000, with their employees
    ```sql
    SELECT  e.employee_id, e.employee_name, e.salary, e.dept_id
    FROM    Employee e
    WHERE   e.dept_id IN (
                SELECT   dept_id
                FROM     Employee
                GROUP BY dept_id
                HAVING   AVG(salary) > 2000
            );
    ```

    Reading 2 — the groups themselves, with their averages
    ```sql
    SELECT   dept_id,
             COUNT(*)    AS employees,
             AVG(salary) AS average_salary
    FROM     Employee
    GROUP BY dept_id
    HAVING   AVG(salary) > 2000;
    ```
    - The condition tests an aggregate, so it must go in `HAVING`. `WHERE AVG(salary) > 2000` is a syntax error, because WHERE runs before the rows are grouped.

    Reading 3 — the simplest reading, individual salary above 2000
    ```sql
    SELECT employee_id, employee_name, salary
    FROM   Employee
    WHERE  salary > 2000;
    ```
    - Here `WHERE` is correct, because the test applies to each row separately.

    Sample data and results
    ```
    Employee
    +-------------+---------------+--------+---------+
    | employee_id | employee_name | salary | dept_id |
    +-------------+---------------+--------+---------+
    |     1       | Karim         |  3000  |   10    |
    |     2       | Rahim         |  2500  |   10    |
    |     3       | Sumi          |  1500  |   20    |
    |     4       | Nabil         |  1800  |   20    |
    +-------------+---------------+--------+---------+

    Department averages: 10 -> 2750 ; 20 -> 1650

    Reading 1 result: Karim and Rahim (both in dept 10)
    Reading 2 result: dept 10, average 2750
    Reading 3 result: Karim, Rahim, and nobody from dept 20
    ```

    The point being tested
    - `WHERE` filters `rows` before grouping; `HAVING` filters `groups` after aggregation. Any condition containing SUM, AVG, COUNT, MAX or MIN belongs in HAVING.
    - SQL's order of evaluation, `FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY`, is the reason.

41. **Employee Table টেবিল হতে যে সকল কর্মচারীদের বেতন 30000 টাকার বেশি তাদের নাম পদবী আলাদা করার SQLCommand লিখুন।** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 699 (ET: DPI)]*

    Answer: (Answered in English, as required for IT topics.) The requirement is the name and designation of employees earning more than 30,000, with the two columns shown separately.

    Query
    ```sql
    SELECT  emp_name,
            designation
    FROM    Employee
    WHERE   salary > 30000;
    ```
    - Only the two requested columns are listed, so `SELECT *` would be wrong.
    - `WHERE salary > 30000` is a strict comparison, so a salary of exactly 30,000 is excluded.

    Sample data and output
    ```
    Employee
    +--------+----------+-------------+--------+
    | emp_id | emp_name | designation | salary |
    +--------+----------+-------------+--------+
    |   1    | Karim    | Manager     | 45000  |
    |   2    | Rahim    | Officer     | 28000  |
    |   3    | Sumi     | Analyst     | 30000  |
    |   4    | Nabil    | Developer   | 52000  |
    |   5    | Jamil    | Officer     | 35000  |
    +--------+----------+-------------+--------+

    Result
    +----------+-------------+
    | emp_name | designation |
    +----------+-------------+
    | Karim    | Manager     |
    | Nabil    | Developer   |
    | Jamil    | Officer     |
    +----------+-------------+
    ```
    - Rahim is excluded (28,000 is below the limit) and Sumi too (exactly 30,000 fails a strict `>`).

    Variations
    ```sql
    -- include 30000 itself
    SELECT emp_name, designation FROM Employee WHERE salary >= 30000;

    -- sorted, highest paid first
    SELECT emp_name, designation, salary FROM Employee
    WHERE  salary > 30000 ORDER BY salary DESC;

    -- unique designations only
    SELECT DISTINCT designation FROM Employee WHERE salary > 30000;

    -- how many such employees per designation
    SELECT designation, COUNT(*) FROM Employee
    WHERE  salary > 30000 GROUP BY designation;

    -- name and designation joined into one column
    SELECT CONCAT(emp_name, ' - ', designation) AS staff FROM Employee
    WHERE  salary > 30000;
    ```
    - A point worth remembering: if `salary` can be NULL, those rows are `not` returned, because any comparison with NULL evaluates to UNKNOWN rather than TRUE.

42. **There are two tables like Employees (Employee_ID, First_name, Last_name, Email, Phone_number, Hire_date, Job_Id) and Departments (Department_Id, Department_name, Manager_Id, Location_Id). Now, write a query to find the name (first_name, last_name), Department Id and name of all the employees.** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 718 (ET: N/A)]*

    Answer:

    Schema
    ```
    Employees   (Employee_ID, First_name, Last_name, Email, Phone_number, Hire_date, Job_Id)
    Departments (Department_Id, Department_name, Manager_Id, Location_Id)
    ```
    - Note that the `Employees` table as printed has `no Department_Id column`, so a direct join is not possible. In the standard HR schema, `Employees` does contain `Department_Id`, and that is assumed below.

    Query
    ```sql
    SELECT  e.First_name,
            e.Last_name,
            d.Department_Id,
            d.Department_name
    FROM    Employees   e
    JOIN    Departments d ON e.Department_Id = d.Department_Id;
    ```

    To include employees who are not yet assigned to a department
    ```sql
    SELECT  e.First_name,
            e.Last_name,
            d.Department_Id,
            d.Department_name
    FROM    Employees   e
    LEFT JOIN Departments d ON e.Department_Id = d.Department_Id;
    ```
    - Those employees appear with NULL in the two department columns. An inner join would drop them silently, which is a common oversight.

    Sample output
    ```
    +------------+-----------+---------------+-----------------+
    | First_name | Last_name | Department_Id | Department_name |
    +------------+-----------+---------------+-----------------+
    | Karim      | Ahmed     |      10       | IT              |
    | Rahim      | Uddin     |      10       | IT              |
    | Sumi       | Akter     |      20       | HR              |
    | Nabil      | Hasan     |     NULL      | NULL            |
    +------------+-----------+---------------+-----------------+
    ```

    If the relationship really is only through the manager
    - If `Employees` genuinely has no Department_Id, the only link in the given schema is `Departments.Manager_Id`, which points at an employee. That relates each department to its `manager`, not to all its staff:
    ```sql
    SELECT e.First_name, e.Last_name, d.Department_Id, d.Department_name
    FROM   Departments d
    JOIN   Employees   e ON d.Manager_Id = e.Employee_ID;
    ```
    - This returns one row per department — the manager of that department — which is a different question and worth pointing out.

    Useful related queries
    ```sql
    -- full name in a single column
    SELECT CONCAT(e.First_name, ' ', e.Last_name) AS Employee_Name,
           d.Department_name
    FROM   Employees e JOIN Departments d ON e.Department_Id = d.Department_Id;

    -- number of employees in each department
    SELECT d.Department_name, COUNT(e.Employee_ID) AS staff
    FROM   Departments d LEFT JOIN Employees e ON d.Department_Id = e.Department_Id
    GROUP  BY d.Department_Id, d.Department_name;

    -- departments with no employees
    SELECT d.Department_name FROM Departments d
    LEFT JOIN Employees e ON d.Department_Id = e.Department_Id
    WHERE  e.Employee_ID IS NULL;
    ```

43. **For employee table: (a) Write a SQL query to find those employees who earn more than the average salary. Return employee ID, first name, last name. (b) Write a SQL query to find those employees who earn the highest salary in a department. Return department ID, employee name, and salary.** *[CAAB Programmer 2022 compact it 722 (ET: N/A)]*

    Answer:

    (a) Employees earning more than the average salary
    ```sql
    SELECT  employee_id,
            first_name,
            last_name
    FROM    employees
    WHERE   salary > (SELECT AVG(salary) FROM employees);
    ```
    - The subquery returns a single number, the company-wide average, and every employee is compared against it.
    - It is `not correlated` — it is evaluated once, not per row, so it is efficient.
    - Note that the subquery must be written as a subquery: `WHERE salary > AVG(salary)` is a syntax error, because an aggregate cannot appear in a WHERE clause.

    Sample output
    ```
    salaries: 30000, 45000, 50000, 60000, 90000 -> average = 55000

    +-------------+------------+-----------+
    | employee_id | first_name | last_name |
    +-------------+------------+-----------+
    |      4      | Nabil      | Hasan     |
    |      5      | Karim      | Ahmed     |
    +-------------+------------+-----------+
    ```

    (b) Employees earning the highest salary in their department
    ```sql
    SELECT  e.department_id,
            e.first_name,
            e.last_name,
            e.salary
    FROM    employees e
    WHERE   e.salary = (SELECT MAX(x.salary)
                        FROM   employees x
                        WHERE  x.department_id = e.department_id);
    ```
    - This subquery `is` correlated: it refers to `e.department_id` from the outer query, so it is recomputed for each employee, returning that employee's own department's maximum.
    - Using `= MAX(...)` returns `all` employees who tie for the top salary in a department, which `ORDER BY ... LIMIT 1` would not.

    Equivalent using a derived table
    ```sql
    SELECT e.department_id, e.first_name, e.last_name, e.salary
    FROM   employees e
    JOIN  (SELECT department_id, MAX(salary) AS max_sal
           FROM   employees GROUP BY department_id) m
      ON   e.department_id = m.department_id AND e.salary = m.max_sal;
    ```
    - Usually faster than the correlated form, because the maximums are computed once rather than per row.

    Window-function version
    ```sql
    SELECT department_id, first_name, last_name, salary FROM (
        SELECT department_id, first_name, last_name, salary,
               RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rnk
        FROM   employees
    ) t
    WHERE rnk = 1;
    ```
    - `RANK()` gives ties the same rank, so all top earners are returned. `ROW_NUMBER()` would arbitrarily pick just one, and `DENSE_RANK()` behaves like RANK here.

    Sample output for (b)
    ```
    +---------------+------------+-----------+--------+
    | department_id | first_name | last_name | salary |
    +---------------+------------+-----------+--------+
    |      10       | Karim      | Ahmed     | 90000  |
    |      20       | Sumi       | Akter     | 65000  |
    |      30       | Jamil      | Khan      | 55000  |
    +---------------+------------+-----------+--------+
    ```

44. **Write down the SQL command into the following two: (a) Find out the all information of employees from emp_info table. Where employee's salary is more than 20,000 and city is Dhaka. (b) Update employee name ‘Mr.X’ in emp_info, whose epm_id is 2.** *[NWPGCL Junior Assistant Manager (IT) 2022 compact it 730 (ET: N/A)]*

    Answer:

    (a) All information about employees earning more than 20,000 in Dhaka
    ```sql
    SELECT  *
    FROM    emp_info
    WHERE   salary > 20000
      AND   city = 'Dhaka';
    ```
    - `SELECT *` is correct here, because the question asks for "all information".
    - `AND` requires both conditions to be true. Using `OR` instead would be wrong — it would return every high earner anywhere plus everyone in Dhaka.

    Sample output
    ```
    emp_info
    +--------+----------+--------+------------+
    | emp_id | emp_name | salary | city       |
    +--------+----------+--------+------------+
    |   1    | Karim    | 25000  | Dhaka      |
    |   2    | Rahim    | 18000  | Dhaka      |
    |   3    | Sumi     | 30000  | Chattogram |
    |   4    | Nabil    | 45000  | Dhaka      |
    +--------+----------+--------+------------+

    Result
    +--------+----------+--------+-------+
    | emp_id | emp_name | salary | city  |
    +--------+----------+--------+-------+
    |   1    | Karim    | 25000  | Dhaka |
    |   4    | Nabil    | 45000  | Dhaka |
    +--------+----------+--------+-------+
    ```

    (b) Update the employee name to 'Mr. X' where emp_id is 2
    ```sql
    UPDATE  emp_info
    SET     emp_name = 'Mr.X'
    WHERE   emp_id = 2;
    ```

    - The `WHERE` clause is critical. Omitting it would rename `every employee in the table`:
    ```sql
    UPDATE emp_info SET emp_name = 'Mr.X';     -- DANGEROUS: updates all rows
    ```
    - Safe practice is to run the equivalent SELECT first, confirm it returns exactly the intended rows, and only then run the UPDATE:
    ```sql
    SELECT * FROM emp_info WHERE emp_id = 2;   -- check first
    UPDATE emp_info SET emp_name = 'Mr.X' WHERE emp_id = 2;
    ```
    - Inside a transaction, the change can be undone if something is wrong:
    ```sql
    BEGIN;
    UPDATE emp_info SET emp_name = 'Mr.X' WHERE emp_id = 2;
    SELECT * FROM emp_info WHERE emp_id = 2;   -- verify
    COMMIT;                                     -- or ROLLBACK
    ```

    Updating several columns at once
    ```sql
    UPDATE emp_info
    SET    emp_name = 'Mr.X', salary = 35000, city = 'Dhaka'
    WHERE  emp_id = 2;
    ```
    - All assignments go in one `SET` clause separated by commas; repeating the keyword SET is a syntax error.

45. **Write down the equivalent SQL from following relational algebra. [full question not collected]** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 760 (ET: N/A)]*

    Answer: The relational algebra expression was not printed, so the systematic translation from relational algebra to SQL is given, with a worked example for each operator.

    The correspondence

    | Relational algebra | Meaning | SQL equivalent |
    |---|---|---|
    | σ (sigma) — selection | Choose rows | `WHERE` |
    | π (pi) — projection | Choose columns | `SELECT` (with DISTINCT) |
    | ⋈ — natural join | Join on common attributes | `NATURAL JOIN`, or `JOIN ... ON` |
    | ⋈θ — theta join | Join on a condition | `JOIN ... ON <condition>` |
    | × — Cartesian product | All combinations | `CROSS JOIN`, or `FROM A, B` |
    | ∪ — union | Rows in either | `UNION` |
    | ∩ — intersection | Rows in both | `INTERSECT` |
    | − — set difference | Rows in A but not B | `EXCEPT` / `MINUS` |
    | ρ — rename | Rename a relation | `AS` |
    | ÷ — division | "for all" queries | `NOT EXISTS` twice, or GROUP BY with COUNT |
    | G — aggregation | Grouped summary | `GROUP BY` with aggregate functions |

    Worked translations, using `Employee(eid, ename, salary, dept)` and `Department(dept, location)`

    `Selection`
    ```
    σ salary > 50000 (Employee)
    ```
    ```sql
    SELECT * FROM Employee WHERE salary > 50000;
    ```

    `Projection`
    ```
    π ename, salary (Employee)
    ```
    ```sql
    SELECT DISTINCT ename, salary FROM Employee;
    ```
    - `DISTINCT` matters: relational algebra works on sets and removes duplicates automatically, whereas SQL keeps them by default. This is the single most common mistake in this translation.

    `Selection combined with projection`
    ```
    π ename (σ salary > 50000 (Employee))
    ```
    ```sql
    SELECT DISTINCT ename FROM Employee WHERE salary > 50000;
    ```

    `Natural join`
    ```
    Employee ⋈ Department
    ```
    ```sql
    SELECT * FROM Employee NATURAL JOIN Department;
    -- or, safer and explicit:
    SELECT * FROM Employee e JOIN Department d ON e.dept = d.dept;
    ```

    `Theta join`
    ```
    Employee ⋈ (Employee.salary > 50000) Department
    ```
    ```sql
    SELECT * FROM Employee e JOIN Department d ON e.dept = d.dept AND e.salary > 50000;
    ```

    `Cartesian product`
    ```
    Employee × Department
    ```
    ```sql
    SELECT * FROM Employee CROSS JOIN Department;
    ```

    `Set operations`
    ```
    π ename (σ dept='IT' (Employee))  ∪  π ename (σ dept='HR' (Employee))
    ```
    ```sql
    SELECT ename FROM Employee WHERE dept = 'IT'
    UNION
    SELECT ename FROM Employee WHERE dept = 'HR';
    ```
    - `UNION` removes duplicates, matching relational algebra; `UNION ALL` keeps them.

    `Difference`
    ```
    π ename (Employee)  −  π ename (σ dept='IT' (Employee))
    ```
    ```sql
    SELECT ename FROM Employee
    EXCEPT
    SELECT ename FROM Employee WHERE dept = 'IT';
    ```
    - MySQL has no `EXCEPT` or `INTERSECT`; `NOT IN` or `LEFT JOIN ... IS NULL` is used instead.

    `Aggregation`
    ```
    dept G AVG(salary) (Employee)
    ```
    ```sql
    SELECT dept, AVG(salary) FROM Employee GROUP BY dept;
    ```
    - General method: read the expression from the innermost operator outwards. Selections become WHERE conditions, projections become the SELECT list, joins become JOIN clauses, and aggregation becomes GROUP BY. <!-- verify -->

46. **Write a SQL query to find same salary but job not same?** *[BIWTA; Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*

    Answer: The requirement is pairs of employees who earn the `same salary` but hold `different jobs`. A self join is the natural tool.

    Query — list the matching pairs
    ```sql
    SELECT  e1.emp_name AS employee_1, e1.job AS job_1,
            e2.emp_name AS employee_2, e2.job AS job_2,
            e1.salary
    FROM    Employee e1
    JOIN    Employee e2
            ON  e1.salary = e2.salary       -- same salary
            AND e1.job   <> e2.job          -- different job
            AND e1.emp_id <  e2.emp_id;     -- each pair listed once
    ```
    - `e1.emp_id < e2.emp_id` is the important detail. Without it the join would return each pair twice, once in each order, and would also let a row match itself.

    Sample data and output
    ```
    Employee
    +--------+----------+-----------+--------+
    | emp_id | emp_name | job       | salary |
    +--------+----------+-----------+--------+
    |   1    | Karim    | Developer | 50000  |
    |   2    | Rahim    | Analyst   | 50000  |
    |   3    | Sumi     | Developer | 50000  |
    |   4    | Nabil    | Manager   | 70000  |
    |   5    | Jamil    | Analyst   | 70000  |
    +--------+----------+-----------+--------+

    Result
    +------------+-----------+------------+-----------+--------+
    | employee_1 | job_1     | employee_2 | job_2     | salary |
    +------------+-----------+------------+-----------+--------+
    | Karim      | Developer | Rahim      | Analyst   | 50000  |
    | Rahim      | Analyst   | Sumi       | Developer | 50000  |
    | Nabil      | Manager   | Jamil      | Analyst   | 70000  |
    +------------+-----------+------------+-----------+--------+
    ```
    - Karim and Sumi do not appear together, because they share both the salary and the job.

    Just the employees, not the pairs
    ```sql
    SELECT DISTINCT e1.emp_name, e1.job, e1.salary
    FROM   Employee e1
    JOIN   Employee e2 ON e1.salary = e2.salary AND e1.job <> e2.job;
    ```

    Relative to one named person, say Rahim
    ```sql
    SELECT e.emp_name, e.job, e.salary
    FROM   Employee e
    WHERE  e.salary = (SELECT salary FROM Employee WHERE emp_name = 'Rahim')
      AND  e.job   <> (SELECT job    FROM Employee WHERE emp_name = 'Rahim');
    ```

    Salaries that are shared across different jobs
    ```sql
    SELECT   salary, COUNT(DISTINCT job) AS different_jobs
    FROM     Employee
    GROUP BY salary
    HAVING   COUNT(DISTINCT job) > 1;
    ```
    - A neat alternative: it finds the salary levels at which more than one distinct job exists, without listing the individual pairs.

47. **This returns the names of the staff where timestampdiff is greater than 25 so it returns total 3 rows.** *[Water Supply and Sewerage Authority (WASA); Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*

    Answer: The statement describes the `result` of a query rather than asking for one, so the query it refers to is reconstructed and explained.

    What `TIMESTAMPDIFF` does
    - It is a MySQL function that returns the difference between two dates or times, expressed in a stated unit.
    ```sql
    TIMESTAMPDIFF(unit, start_datetime, end_datetime)
    ```
    - Units: `YEAR`, `QUARTER`, `MONTH`, `WEEK`, `DAY`, `HOUR`, `MINUTE`, `SECOND`.

    The query being described — staff whose service exceeds 25 years
    ```sql
    SELECT  staff_name,
            joining_date,
            TIMESTAMPDIFF(YEAR, joining_date, CURDATE()) AS years_of_service
    FROM    Staff
    WHERE   TIMESTAMPDIFF(YEAR, joining_date, CURDATE()) > 25;
    ```

    Sample data and result
    ```
    Staff
    +----+------------+--------------+
    | id | staff_name | joining_date |
    +----+------------+--------------+
    | 1  | Karim      | 1995-03-10   |   -> 30 years  ✓
    | 2  | Rahim      | 2005-07-22   |   -> 20 years  ✗
    | 3  | Sumi       | 1998-01-05   |   -> 27 years  ✓
    | 4  | Nabil      | 2015-11-30   |   -> 9 years   ✗
    | 5  | Jamil      | 1990-06-18   |   -> 34 years  ✓
    +----+------------+--------------+

    Result: Karim, Sumi, Jamil  -> 3 rows, as the statement says
    ```

    Equivalents in other systems
    ```sql
    -- MySQL
    WHERE TIMESTAMPDIFF(YEAR, joining_date, CURDATE()) > 25

    -- Oracle
    WHERE MONTHS_BETWEEN(SYSDATE, joining_date) / 12 > 25

    -- SQL Server
    WHERE DATEDIFF(YEAR, joining_date, GETDATE()) > 25

    -- PostgreSQL
    WHERE AGE(CURRENT_DATE, joining_date) > INTERVAL '25 years'

    -- Portable and index-friendly
    WHERE joining_date < CURRENT_DATE - INTERVAL '25' YEAR
    ```

    An important performance point
    - Wrapping the column in a function, as in `TIMESTAMPDIFF(YEAR, joining_date, CURDATE()) > 25`, prevents the database from using an index on `joining_date`, so the whole table must be scanned.
    - Rewriting the condition so the column stands alone allows the index to be used:
    ```sql
    WHERE joining_date < DATE_SUB(CURDATE(), INTERVAL 25 YEAR);
    ```
    - This is the general rule: keep the column on one side of the comparison, unmodified.

    A subtlety with TIMESTAMPDIFF(YEAR, ...)
    - It counts `complete` years. Someone who joined on 1 January 2000 reaches 25 years only on 1 January 2025, not at any point during 2024. `DATEDIFF(YEAR, ...)` in SQL Server behaves differently — it counts year boundaries crossed — so the two are not interchangeable.

48. **(c) In a SQL query, while performing string matching when do we use operator and when we use LIKE operator? Give examples.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 803 (ET: N/A)]*

    Answer:

    The `=` operator
    - Used for an `exact` match of the whole value. The comparison succeeds only if the two strings are identical.
    ```sql
    SELECT * FROM Employee WHERE emp_name = 'Karim';
    ```
    - Matches `Karim` only. It does not match `Karim Ahmed`, `karim` in a case-sensitive collation, or `Karima`.
    - It is faster than LIKE, and it can use an index directly.

    The `LIKE` operator
    - Used for `pattern` matching, when only part of the value is known, with two wildcards:
    ```
    %   any sequence of characters, including none
    _   exactly one character
    ```
    ```sql
    SELECT * FROM Employee WHERE emp_name LIKE 'Kar%';
    ```
    - Matches `Karim`, `Karima`, `Karman` — anything beginning with Kar.

    When to use which

    | Situation | Operator | Example |
    |---|---|---|
    | The exact value is known | `=` | `WHERE city = 'Dhaka'` |
    | Only a prefix is known | `LIKE` | `WHERE name LIKE 'A%'` |
    | Only a suffix is known | `LIKE` | `WHERE email LIKE '%.gov.bd'` |
    | A substring anywhere | `LIKE` | `WHERE address LIKE '%Road%'` |
    | A specific character position | `LIKE` | `WHERE name LIKE '_a%'` (second letter a) |
    | A fixed length | `LIKE` | `WHERE code LIKE '____'` (exactly 4 characters) |
    | Comparing numbers or dates | `=` | `WHERE salary = 50000` |

    Worked examples
    ```sql
    -- exact
    SELECT * FROM Employee WHERE designation = 'Manager';

    -- names starting with S
    SELECT * FROM Employee WHERE emp_name LIKE 'S%';

    -- names ending with 'im'
    SELECT * FROM Employee WHERE emp_name LIKE '%im';

    -- names containing 'ah' anywhere
    SELECT * FROM Employee WHERE emp_name LIKE '%ah%';

    -- second letter is 'a'
    SELECT * FROM Employee WHERE emp_name LIKE '_a%';

    -- exactly five characters long
    SELECT * FROM Employee WHERE emp_name LIKE '_____';

    -- does NOT match the pattern
    SELECT * FROM Employee WHERE emp_name NOT LIKE 'A%';
    ```

    Points worth remembering
    - `LIKE 'Karim'` with no wildcard behaves exactly like `= 'Karim'`, so the wildcards are what give LIKE its purpose.
    - `Performance`: a leading wildcard, as in `LIKE '%im'`, prevents the use of an index and forces a full table scan. `LIKE 'Kar%'` can still use an index, because the prefix is fixed. For frequent substring searches a full-text index is the right tool.
    - To search for a literal `%` or `_`, escape it: `WHERE code LIKE '50\%%' ESCAPE '\'`.
    - Case sensitivity depends on the column's collation, not on the operator. MySQL's default collation is case-insensitive for both `=` and `LIKE`; PostgreSQL is case-sensitive and offers `ILIKE` for a case-insensitive match.

49. **Consider the Electrical Powr company database which has the following tables: Powerplant(Powerplant_ID, location, type, capacity.unit_price) Customer(Customer_ID, name, address, DoB, monthly_demand) Customer_usage_profile(ID, month_name, Customer_ID, Powrplant_ID) The powerplant relation has attributes powerplan_ID, loation, Type{Thrmal power, hydro power, nuclear power, nuclear power, capacity, and unit_price of power generated by the powerplant. The customer relation has attributes Customer_ID, name, address, date of birth(DoB) and monthly_demand of electrical power. The customer_usesge_profile relation stores the user profile of a customer. A customer more usage hydropower during the rainy season and thermal or nuclear power during the dry season. Write the relational algebra expressions for the following queries: (i) List the customers with a yearly bill of more than taka 5,000. (ii) List the customers who uses nuclear power during December and has a monthly bill less then 500 in December.** *[BPDB Assistant Engineer (CSE) 2021 compact it 818 (ET: BUET)]*

    Answer:

    Schema
    ```
    Powerplant             (Powerplant_ID, location, type, capacity, unit_price)
    Customer               (Customer_ID, name, address, DoB, monthly_demand)
    Customer_usage_profile (ID, month_name, Customer_ID, Powerplant_ID)
    ```
    - A customer's bill for a month is `monthly_demand × unit_price` of the plant used in that month, so the three relations must be joined.

    (i) Customers with a yearly bill of more than 5,000 taka

    Relational algebra
    ```
    π name (
        σ yearly_bill > 5000 (
            Customer_ID G SUM(monthly_demand × unit_price) AS yearly_bill (
                Customer ⋈ Customer_usage_profile ⋈ Powerplant
            )
        )
    )
    ```
    - Step by step:
      - Join the three relations on `Customer_ID` and `Powerplant_ID`.
      - Group by `Customer_ID` and sum `monthly_demand × unit_price` over the twelve months.
      - Select the groups whose total exceeds 5000.
      - Project the customer name.

    Equivalent SQL
    ```sql
    SELECT   c.name, SUM(c.monthly_demand * p.unit_price) AS yearly_bill
    FROM     Customer c
    JOIN     Customer_usage_profile u ON c.Customer_ID   = u.Customer_ID
    JOIN     Powerplant             p ON u.Powerplant_ID = p.Powerplant_ID
    GROUP BY c.Customer_ID, c.name
    HAVING   SUM(c.monthly_demand * p.unit_price) > 5000;
    ```

    (ii) Customers who use nuclear power in December with a monthly bill under 500

    Relational algebra
    ```
    π name (
        σ (type = 'nuclear power')
          ∧ (month_name = 'December')
          ∧ (monthly_demand × unit_price < 500)
          ( Customer ⋈ Customer_usage_profile ⋈ Powerplant )
    )
    ```
    - Here no aggregation is needed, because the condition applies to a single month's row. All three conditions are ordinary selections on the joined relation.

    Equivalent SQL
    ```sql
    SELECT DISTINCT c.name
    FROM   Customer               c
    JOIN   Customer_usage_profile u ON c.Customer_ID   = u.Customer_ID
    JOIN   Powerplant             p ON u.Powerplant_ID = p.Powerplant_ID
    WHERE  p.type       = 'nuclear power'
      AND  u.month_name = 'December'
      AND  c.monthly_demand * p.unit_price < 500;
    ```

    The algebra operators used, for reference

    | Symbol | Name | Purpose |
    |---|---|---|
    | σ | Selection | Choose rows meeting a condition |
    | π | Projection | Choose columns |
    | ⋈ | Natural join | Combine relations on common attributes |
    | G | Aggregation | Group and summarise |
    | ρ | Rename | Give a relation or attribute a new name |

    - The general translation rule: `σ` becomes `WHERE`, `π` becomes the `SELECT` list, `⋈` becomes `JOIN`, and `G` becomes `GROUP BY` with an aggregate. Aggregate conditions become `HAVING`, as in part (i). <!-- verify -->

50. **What will be the output after running all the following queries?** *[BCC Assistant Programmer 12.02.2021 compact it 813 (ET: BUET)]*
```sql
CREATE Table t(
val INT
);
INSERT INTO t(val)
values (1), (2), (3), (null), (null), (4), (5);
SELECT count (*) val_count
From t;
SELECT count(Distinct val) val_count
From t;
```

    Answer:

    The statements
    ```sql
    CREATE TABLE t (val INT);
    INSERT INTO t(val) VALUES (1), (2), (3), (null), (null), (4), (5);

    SELECT COUNT(*)            AS val_count FROM t;
    SELECT COUNT(DISTINCT val) AS val_count FROM t;
    ```

    The table after the INSERT
    ```
    t
    +------+
    | val  |
    +------+
    |  1   |
    |  2   |
    |  3   |
    | NULL |
    | NULL |
    |  4   |
    |  5   |
    +------+
    7 rows
    ```

    First query — `SELECT COUNT(*) FROM t`
    ```
    val_count = 7
    ```
    - `COUNT(*)` counts `rows`, not values. It does not look at the contents at all, so the two NULL rows are counted like any others.

    Second query — `SELECT COUNT(DISTINCT val) FROM t`
    ```
    val_count = 5
    ```
    - Two rules combine here:
      - `COUNT(column)` ignores NULLs — so the two NULL rows are excluded, leaving 1, 2, 3, 4, 5.
      - `DISTINCT` removes duplicates — here there are none among the non-null values.
    - The distinct non-null values are 1, 2, 3, 4 and 5, giving `5`.

    Summary

    | Query | Result | Reason |
    |---|---|---|
    | `COUNT(*)` | `7` | Counts every row, including NULLs |
    | `COUNT(val)` | `5` | Counts non-null values only |
    | `COUNT(DISTINCT val)` | `5` | Non-null values, duplicates removed |

    The rule to remember
    - `COUNT(*)` counts rows. `COUNT(expression)` counts rows where the expression is `not NULL`. Every other aggregate — SUM, AVG, MAX, MIN — also ignores NULLs.
    - This matters most for `AVG`: over the values 10, 20 and NULL, `AVG` returns 15, not 10, because the divisor is 2 rather than 3.

    A further illustration
    ```sql
    INSERT INTO t(val) VALUES (3), (3);       -- two more 3s, now 9 rows

    SELECT COUNT(*)            FROM t;   -- 9
    SELECT COUNT(val)          FROM t;   -- 7   (NULLs excluded)
    SELECT COUNT(DISTINCT val) FROM t;   -- 5   (1,2,3,4,5)
    SELECT SUM(val)            FROM t;   -- 21  (1+2+3+4+5+3+3)
    SELECT AVG(val)            FROM t;   -- 3.0 (21 / 7, not 21 / 9)
    ```

51. **Write SQL command from the following tables. Employee (ename, street, city) Works (ename, cname, salary, joindate) Company (cname, city) Manages (ename, mname) (a) Find name, street, city who work for First Corporation Bank and earn more than 30000 (b) Find name of all employees, who live in the same city and company for which they work. (c) Give all employees of First Century Bank 10 percent salary raise (d) Find the company with payroll less than 100000.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 835-836 (ET: N/A)]*

    Answer:

    Schema
    ```
    Employee (ename, street, city)
    Works    (ename, cname, salary, joindate)
    Company  (cname, city)
    Manages  (ename, mname)
    ```

    (a) Name, street and city of those who work for First Corporation Bank and earn more than 30000
    ```sql
    SELECT  e.ename, e.street, e.city
    FROM    Employee e
    JOIN    Works    w ON e.ename = w.ename
    WHERE   w.cname  = 'First Corporation Bank'
      AND   w.salary > 30000;
    ```
    - `Employee` holds the address, `Works` holds the company and the salary, so both are needed.

    (b) Employees who live in the same city as the company they work for
    ```sql
    SELECT  e.ename
    FROM    Employee e
    JOIN    Works    w ON e.ename = w.ename
    JOIN    Company  c ON w.cname = c.cname
    WHERE   e.city = c.city;
    ```
    - Three tables are required: the employee's city comes from `Employee`, the company's city from `Company`, and `Works` is the link between them.
    - The classic textbook version of this question also requires the street to match; here only the city is asked for.

    (c) Give all employees of First Century Bank a 10 percent salary raise
    ```sql
    UPDATE  Works
    SET     salary = salary * 1.10
    WHERE   cname = 'First Century Bank';
    ```
    - The salary lives in `Works`, so that is the table updated.
    - The `WHERE` clause is essential — without it every employee of every company would receive the raise.
    - `salary * 1.10` adds 10 percent; `salary + salary * 0.10` is equivalent but longer.

    (d) Companies with a payroll of less than 100000
    ```sql
    SELECT   cname, SUM(salary) AS payroll
    FROM     Works
    GROUP BY cname
    HAVING   SUM(salary) < 100000;
    ```
    - Payroll is the total of all salaries paid by a company, so the rows are grouped by company and summed.
    - The condition tests an aggregate and must therefore be in `HAVING`, not `WHERE`.

    Other standard queries on this well-known schema
    ```sql
    -- the company with the largest payroll
    SELECT cname, SUM(salary) AS payroll FROM Works
    GROUP  BY cname ORDER BY payroll DESC LIMIT 1;

    -- employees who earn more than every employee of Small Bank
    SELECT ename FROM Works
    WHERE  salary > ALL (SELECT salary FROM Works WHERE cname = 'Small Bank');

    -- employees who do NOT work for First Bank
    SELECT ename FROM Employee
    WHERE  ename NOT IN (SELECT ename FROM Works WHERE cname = 'First Bank');

    -- each manager and how many people report to them
    SELECT mname, COUNT(*) AS reports FROM Manages GROUP BY mname;

    -- employees earning more than their manager
    SELECT w1.ename FROM Manages m
    JOIN   Works w1 ON m.ename = w1.ename
    JOIN   Works w2 ON m.mname = w2.ename
    WHERE  w1.salary > w2.salary;
    ```

52. **DB schema: book (book_id, book_title, book_type, publication_name) author (book_name, author_name) publicher (publication_name, publication_address, est_year) copies (book_id, branch_name, no_of-copies) [database query লিখতে আসছিল]** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)]*

    Answer: The specific query was not printed, so the standard queries on this library schema are given.

    Schema (with the obvious typographical corrections)
    ```
    book      (book_id, book_title, book_type, publication_name)
    author    (book_id, author_name)              -- book_name in the question is clearly book_id
    publisher (publication_name, publication_address, est_year)
    copies    (book_id, branch_name, no_of_copies)
    ```

    Basic retrieval
    ```sql
    -- all books of a given type
    SELECT book_title FROM book WHERE book_type = 'Science';

    -- books with their authors
    SELECT b.book_title, a.author_name
    FROM   book b JOIN author a ON b.book_id = a.book_id;

    -- books with their publisher's address
    SELECT b.book_title, p.publication_name, p.publication_address
    FROM   book b JOIN publisher p ON b.publication_name = p.publication_name;
    ```

    Aggregation
    ```sql
    -- total copies of each book across all branches
    SELECT   b.book_title, SUM(c.no_of_copies) AS total_copies
    FROM     book b JOIN copies c ON b.book_id = c.book_id
    GROUP BY b.book_id, b.book_title;

    -- number of books each publisher has published
    SELECT   publication_name, COUNT(*) AS titles
    FROM     book
    GROUP BY publication_name
    ORDER BY titles DESC;

    -- branches holding more than 100 books in total
    SELECT   branch_name, SUM(no_of_copies) AS total
    FROM     copies
    GROUP BY branch_name
    HAVING   SUM(no_of_copies) > 100;
    ```

    Multi-table joins
    ```sql
    -- full detail of every book
    SELECT b.book_title, b.book_type, a.author_name,
           p.publication_name, p.publication_address, c.branch_name, c.no_of_copies
    FROM   book b
    JOIN   author    a ON b.book_id = a.book_id
    JOIN   publisher p ON b.publication_name = p.publication_name
    JOIN   copies    c ON b.book_id = c.book_id;

    -- books available at the 'Dhaka' branch
    SELECT b.book_title, c.no_of_copies
    FROM   book b JOIN copies c ON b.book_id = c.book_id
    WHERE  c.branch_name = 'Dhaka' AND c.no_of_copies > 0;
    ```

    Subqueries and outer joins
    ```sql
    -- books written by more than one author
    SELECT b.book_title FROM book b
    WHERE  (SELECT COUNT(*) FROM author a WHERE a.book_id = b.book_id) > 1;

    -- books published by houses established before 1990
    SELECT b.book_title FROM book b
    WHERE  b.publication_name IN (SELECT publication_name FROM publisher WHERE est_year < 1990);

    -- books not held at any branch
    SELECT b.book_title FROM book b
    LEFT JOIN copies c ON b.book_id = c.book_id
    WHERE  c.book_id IS NULL;

    -- the book with the most copies overall
    SELECT b.book_title, SUM(c.no_of_copies) AS total
    FROM   book b JOIN copies c ON b.book_id = c.book_id
    GROUP  BY b.book_id, b.book_title
    ORDER  BY total DESC LIMIT 1;
    ```

    Modification
    ```sql
    INSERT INTO book VALUES (101, 'Database Systems', 'Computer', 'Pearson');
    UPDATE copies SET no_of_copies = no_of_copies + 5
    WHERE  book_id = 101 AND branch_name = 'Dhaka';
    DELETE FROM copies WHERE no_of_copies = 0;
    ```
    - Design note: storing `publication_name` as the foreign key in `book` works but is fragile — a surrogate `publisher_id` would be better, since a publisher's name can change. <!-- verify -->

53. **Given Table: Project (Project_id, Project_name, Manager_name) Location (location_id, Location_name, project_id) Employee (Employee_id, Employee_Name, Location_id, Joning date, Salary) Write a query to show project_name, Location_name, Total_salary of each projects employee who joined before ‘January 2021’.** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 868 (ET: BUET)]*

    Answer:

    Schema
    ```
    Project  (Project_id, Project_name, Manager_name)
    Location (location_id, Location_name, project_id)
    Employee (Employee_id, Employee_Name, Location_id, Joining_date, Salary)
    ```
    - The chain of relationships is `Project -> Location -> Employee`, so both joins are needed to link an employee to a project.

    Query
    ```sql
    SELECT   p.Project_name,
             l.Location_name,
             SUM(e.Salary) AS Total_Salary
    FROM     Project  p
    JOIN     Location l ON p.Project_id  = l.project_id
    JOIN     Employee e ON l.location_id = e.Location_id
    WHERE    e.Joining_date < '2021-01-01'
    GROUP BY p.Project_id, p.Project_name, l.location_id, l.Location_name;
    ```

    How it works
    - The two joins connect each employee to their location and each location to its project.
    - `WHERE e.Joining_date < '2021-01-01'` keeps only employees who joined `before` January 2021. This filter must be in `WHERE`, because it applies to individual employees before any grouping.
    - `GROUP BY` on the project and location produces one total per project–location pair, and `SUM(e.Salary)` adds up the salaries within each.
    - Grouping by the id columns as well as the names is safer, in case two projects or locations share a name.

    Sample output
    ```
    +--------------+---------------+--------------+
    | Project_name | Location_name | Total_Salary |
    +--------------+---------------+--------------+
    | Metro Rail   | Dhaka         |    450000    |
    | Metro Rail   | Gazipur       |    280000    |
    | Power Grid   | Chattogram    |    320000    |
    +--------------+---------------+--------------+
    ```

    If the total is wanted per `project` only, not per location
    ```sql
    SELECT   p.Project_name, SUM(e.Salary) AS Total_Salary
    FROM     Project  p
    JOIN     Location l ON p.Project_id  = l.project_id
    JOIN     Employee e ON l.location_id = e.Location_id
    WHERE    e.Joining_date < '2021-01-01'
    GROUP BY p.Project_id, p.Project_name;
    ```

    To include projects and locations with no qualifying employees
    ```sql
    SELECT   p.Project_name, l.Location_name,
             COALESCE(SUM(e.Salary), 0) AS Total_Salary
    FROM     Project  p
    JOIN     Location l ON p.Project_id  = l.project_id
    LEFT JOIN Employee e ON l.location_id = e.Location_id
                        AND e.Joining_date < '2021-01-01'
    GROUP BY p.Project_id, p.Project_name, l.location_id, l.Location_name;
    ```
    - Note that the date condition moves into the `ON` clause. Leaving it in `WHERE` would eliminate the NULL rows produced by the outer join and turn it back into an inner join — the single most common mistake with outer joins.

54. **(i) SQL Query for finding Dept names for departments Find out the employees whose salaries are greater than the salaries of their managers.** *[NESCO Assistant Manager (ICT) 2021 compact it 907 (ET: BUET)]*

    Answer: Employees and their managers are both rows of the same table, linked by `manager_id`, so a `self join` is required.

    Query — employees earning more than their manager
    ```sql
    SELECT  e.emp_id,
            e.emp_name       AS employee,
            e.salary         AS employee_salary,
            m.emp_name       AS manager,
            m.salary         AS manager_salary,
            d.dept_name
    FROM    Employee   e
    JOIN    Employee   m ON e.manager_id = m.emp_id
    JOIN    Department d ON e.dept_id    = d.dept_id
    WHERE   e.salary > m.salary;
    ```

    How the self join works
    - The same table appears twice with two different aliases: `e` for the employee and `m` for the manager.
    - `e.manager_id = m.emp_id` is the join condition that pairs each employee with their own manager.
    - `WHERE e.salary > m.salary` then keeps only the pairs where the subordinate earns more.
    - Employees with a NULL `manager_id` — the top of the hierarchy — are excluded automatically by the inner join, which is correct here since they have no manager to compare against.

    Sample data and result
    ```
    Employee
    +--------+----------+--------+------------+---------+
    | emp_id | emp_name | salary | manager_id | dept_id |
    +--------+----------+--------+------------+---------+
    |  101   | Karim    | 90000  |    NULL    |   10    |
    |  102   | Rahim    | 95000  |    101     |   10    |   <- earns more than Karim  ✓
    |  103   | Sumi     | 60000  |    101     |   20    |
    |  104   | Nabil    | 70000  |    102     |   10    |
    +--------+----------+--------+------------+---------+

    Result
    +--------+----------+-----------------+---------+----------------+
    | emp_id | employee | employee_salary | manager | manager_salary |
    +--------+----------+-----------------+---------+----------------+
    |  102   | Rahim    |     95000       | Karim   |     90000      |
    +--------+----------+-----------------+---------+----------------+
    ```

    Just the department names, as the first part of the question asks
    ```sql
    SELECT DISTINCT d.dept_name
    FROM   Employee   e
    JOIN   Employee   m ON e.manager_id = m.emp_id
    JOIN   Department d ON e.dept_id    = d.dept_id
    WHERE  e.salary > m.salary;
    ```

    Correlated-subquery alternative
    ```sql
    SELECT e.emp_name, e.salary
    FROM   Employee e
    WHERE  e.salary > (SELECT m.salary FROM Employee m WHERE m.emp_id = e.manager_id);
    ```
    - Equivalent in result but usually slower, since the subquery is evaluated once per row.

    Related self-join queries
    ```sql
    -- every employee with their manager's name, including those with no manager
    SELECT e.emp_name, COALESCE(m.emp_name, 'No Manager') AS manager
    FROM   Employee e LEFT JOIN Employee m ON e.manager_id = m.emp_id;

    -- how many people report to each manager
    SELECT m.emp_name, COUNT(*) AS reports
    FROM   Employee e JOIN Employee m ON e.manager_id = m.emp_id
    GROUP  BY m.emp_id, m.emp_name;

    -- employees who manage nobody
    SELECT e.emp_name FROM Employee e
    WHERE  e.emp_id NOT IN (SELECT manager_id FROM Employee WHERE manager_id IS NOT NULL);
    ```

55. **Two SQL query from given table (date and join related).** *[Sonali Bank Ltd. Officer IT 2021 compact it 910 (ET: N/A)]*

    Answer: The tables were not printed, so the two categories the question names — `date-related` and `join-related` queries — are covered with worked examples, using
    ```
    Employee   (emp_id, emp_name, salary, dept_id, hire_date, manager_id)
    Department (dept_id, dept_name)
    ```

    Date-related queries
    ```sql
    -- employees hired in a given year
    SELECT emp_name, hire_date FROM Employee
    WHERE  hire_date >= '2023-01-01' AND hire_date < '2024-01-01';

    -- employees hired between two dates (BETWEEN is inclusive)
    SELECT * FROM Employee WHERE hire_date BETWEEN '2020-01-01' AND '2022-12-31';

    -- years of service
    SELECT emp_name,
           TIMESTAMPDIFF(YEAR, hire_date, CURDATE()) AS years_of_service
    FROM   Employee;

    -- employees with more than 10 years of service
    SELECT emp_name FROM Employee
    WHERE  hire_date < DATE_SUB(CURDATE(), INTERVAL 10 YEAR);

    -- hires per year
    SELECT   YEAR(hire_date) AS yr, COUNT(*) AS hires
    FROM     Employee
    GROUP BY YEAR(hire_date)
    ORDER BY yr;

    -- employees whose work anniversary falls this month
    SELECT emp_name FROM Employee WHERE MONTH(hire_date) = MONTH(CURDATE());

    -- formatting a date for display
    SELECT emp_name, DATE_FORMAT(hire_date, '%d-%m-%Y') AS joined FROM Employee;
    ```

    An important performance point
    - `WHERE YEAR(hire_date) = 2023` works, but wrapping the column in a function prevents an index on `hire_date` from being used, forcing a full table scan.
    - The range form `hire_date >= '2023-01-01' AND hire_date < '2024-01-01'` returns the same rows and `can` use the index. This is the preferred style.

    Join-related queries
    ```sql
    -- inner join: employees with their department
    SELECT e.emp_name, d.dept_name
    FROM   Employee e JOIN Department d ON e.dept_id = d.dept_id;

    -- left join: keep employees with no department
    SELECT e.emp_name, COALESCE(d.dept_name, 'Unassigned') AS dept
    FROM   Employee e LEFT JOIN Department d ON e.dept_id = d.dept_id;

    -- departments with no employees
    SELECT d.dept_name FROM Department d
    LEFT JOIN Employee e ON d.dept_id = e.dept_id
    WHERE  e.emp_id IS NULL;

    -- self join: employee and manager
    SELECT e.emp_name AS employee, m.emp_name AS manager
    FROM   Employee e LEFT JOIN Employee m ON e.manager_id = m.emp_id;

    -- join with aggregation
    SELECT   d.dept_name, COUNT(*) AS staff, AVG(e.salary) AS avg_salary
    FROM     Employee e JOIN Department d ON e.dept_id = d.dept_id
    GROUP BY d.dept_id, d.dept_name;

    -- join combined with a date filter
    SELECT   d.dept_name, COUNT(*) AS recent_hires
    FROM     Employee e JOIN Department d ON e.dept_id = d.dept_id
    WHERE    e.hire_date >= '2023-01-01'
    GROUP BY d.dept_id, d.dept_name;
    ```

    Date function equivalents across systems

    | Task | MySQL | Oracle | SQL Server | PostgreSQL |
    |---|---|---|---|---|
    | Today | `CURDATE()` | `SYSDATE` | `GETDATE()` | `CURRENT_DATE` |
    | Extract year | `YEAR(d)` | `EXTRACT(YEAR FROM d)` | `YEAR(d)` | `EXTRACT(YEAR FROM d)` |
    | Difference | `DATEDIFF(a,b)` | `a - b` | `DATEDIFF(day,b,a)` | `a - b` |
    | Add an interval | `DATE_ADD(d, INTERVAL 1 YEAR)` | `ADD_MONTHS(d,12)` | `DATEADD(year,1,d)` | `d + INTERVAL '1 year'` | <!-- verify -->

56. **emp [e_id, e_name, dept_id, salary, DOB], dept [dept_id, city, dept_name]; প্রত্যেকটি Department এর নাম এবং ঐ Department এর employee দের গড় Salary দেখার SQL Query লিখ।** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 911 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.)

    Schema
    ```
    emp  (e_id, e_name, dept_id, salary, DOB)
    dept (dept_id, city, dept_name)
    ```

    Query
    ```sql
    SELECT   d.dept_name,
             AVG(e.salary) AS average_salary
    FROM     dept d
    JOIN     emp  e ON d.dept_id = e.dept_id
    GROUP BY d.dept_id, d.dept_name;
    ```

    Explanation
    - The two tables are joined on `dept_id`, the foreign key that links an employee to a department.
    - `GROUP BY` on the department produces exactly one output row per department.
    - `AVG(e.salary)` averages the salaries within each group.
    - Grouping by `d.dept_id` as well as the name protects against two departments sharing a name.

    Sample data and output
    ```
    dept                          emp
    +---------+-----------+       +------+--------+---------+--------+
    | dept_id | dept_name |       | e_id | e_name | dept_id | salary |
    +---------+-----------+       +------+--------+---------+--------+
    |   10    | IT        |       |  1   | Karim  |   10    | 50000  |
    |   20    | HR        |       |  2   | Rahim  |   10    | 60000  |
    |   30    | Accounts  |       |  3   | Sumi   |   20    | 40000  |
    +---------+-----------+       |  4   | Nabil  |   20    | 44000  |
                                  +------+--------+---------+--------+

    Result
    +-----------+----------------+
    | dept_name | average_salary |
    +-----------+----------------+
    | IT        |     55000      |
    | HR        |     42000      |
    +-----------+----------------+
    ```
    - `Accounts` does not appear, because an inner join drops departments that have no employees.

    To show every department, including empty ones
    ```sql
    SELECT   d.dept_name,
             COALESCE(AVG(e.salary), 0) AS average_salary
    FROM     dept d
    LEFT JOIN emp e ON d.dept_id = e.dept_id
    GROUP BY d.dept_id, d.dept_name;
    ```
    - `Accounts` now appears with 0 (or with NULL if `COALESCE` is omitted).

    Refinements
    ```sql
    -- rounded and sorted, highest average first
    SELECT   d.dept_name, ROUND(AVG(e.salary), 2) AS average_salary
    FROM     dept d JOIN emp e ON d.dept_id = e.dept_id
    GROUP BY d.dept_id, d.dept_name
    ORDER BY average_salary DESC;

    -- with the staff count and the city as well
    SELECT   d.dept_name, d.city, COUNT(*) AS staff, AVG(e.salary) AS average_salary
    FROM     dept d JOIN emp e ON d.dept_id = e.dept_id
    GROUP BY d.dept_id, d.dept_name, d.city;

    -- only departments averaging above 45000
    SELECT   d.dept_name, AVG(e.salary) AS average_salary
    FROM     dept d JOIN emp e ON d.dept_id = e.dept_id
    GROUP BY d.dept_id, d.dept_name
    HAVING   AVG(e.salary) > 45000;
    ```

57. **Database table by name Loan Records is given below: What is the output of the following SQL query?** *[BAUST Assistant Programmer 2021 compact it 919-920 (ET: N/A)]*
```sql
SELECT count (*) FROM (
(SELECT Borrower, Bank_Manager, FROM Loan_Records) AS S NATURAL JOIN
(SELECT Bank_Manager, Loan_Amount FROM Loan_Records) AS T);
```

    Answer: This is the well-known GATE question on `NATURAL JOIN`, and the point it tests is that the join produces more rows than either input.

    The query
    ```sql
    SELECT count(*) FROM (
       (SELECT Borrower, Bank_Manager FROM Loan_Records) AS S
       NATURAL JOIN
       (SELECT Bank_Manager, Loan_Amount FROM Loan_Records) AS T
    );
    ```

    The standard table
    ```
    Loan_Records
    +----------+--------------+-------------+
    | Borrower | Bank_Manager | Loan_Amount |
    +----------+--------------+-------------+
    | Ramesh   | Sunderajan   |    10000    |
    | Suresh   | Ramgopal     |     5000    |
    | Mahesh   | Sunderajan   |     7000    |
    +----------+--------------+-------------+
    ```

    Step 1 — the two derived tables
    ```
    S (Borrower, Bank_Manager)          T (Bank_Manager, Loan_Amount)
    +----------+--------------+         +--------------+-------------+
    | Ramesh   | Sunderajan   |         | Sunderajan   |    10000    |
    | Suresh   | Ramgopal     |         | Ramgopal     |     5000    |
    | Mahesh   | Sunderajan   |         | Sunderajan   |     7000    |
    +----------+--------------+         +--------------+-------------+
         3 rows                                3 rows
    ```

    Step 2 — the NATURAL JOIN
    - A natural join matches on `all columns the two relations share`. Here the only common column is `Bank_Manager`, so the join condition is `S.Bank_Manager = T.Bank_Manager`.

    ```
    Ramesh / Sunderajan  matches Sunderajan/10000 and Sunderajan/7000  -> 2 rows
    Suresh / Ramgopal    matches Ramgopal/5000                          -> 1 row
    Mahesh / Sunderajan  matches Sunderajan/10000 and Sunderajan/7000  -> 2 rows
    ```

    Result of the join
    ```
    +----------+--------------+-------------+
    | Borrower | Bank_Manager | Loan_Amount |
    +----------+--------------+-------------+
    | Ramesh   | Sunderajan   |    10000    |
    | Ramesh   | Sunderajan   |     7000    |
    | Suresh   | Ramgopal     |     5000    |
    | Mahesh   | Sunderajan   |    10000    |
    | Mahesh   | Sunderajan   |     7000    |
    +----------+--------------+-------------+
    ```

    Step 3 — the count
    ```
    Output = 5
    ```

    Why the answer is not 3
    - The intuitive but wrong answer is 3, on the assumption that splitting a table and rejoining it must restore the original.
    - It does not, because `Bank_Manager` is `not a key` of Loan_Records — Sunderajan appears twice. Joining on a non-key column multiplies the matching rows, producing `spurious tuples`.
    - The general count is the sum, over each distinct value of the join column, of (rows in S) × (rows in T):
    ```
    Sunderajan : 2 × 2 = 4
    Ramgopal   : 1 × 1 = 1
    Total      = 5
    ```

    The database-theory lesson
    - A decomposition is `lossless` only when the common attribute of the two fragments is a `superkey` of at least one of them. Here it is not, so the decomposition is `lossy` — rejoining produces extra, incorrect rows.
    - Note also the syntax error in the printed query: `SELECT Borrower, Bank_Manager, FROM` has a stray comma before FROM. Removing it gives the working statement.

58. **Below tables are given, Employee (employee_id, name, salary, department) Leave (employee_id, date, reason, no_leaves) Holiday (Date, description) (i) Write mapping cardinality between 'Employee' and 'Holiday' table. (ii) Write query to show all employee's leave count. (iii) Write query to show employees who are in 'HR' department and have taken at least 5 leaves.** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 928 (ET: CTI)]*

    Answer:

    Schema
    ```
    Employee (employee_id, name, salary, department)
    Leave    (employee_id, date, reason, no_leaves)
    Holiday  (Date, description)
    ```

    (i) Mapping cardinality between Employee and Holiday
    - The cardinality is `many-to-many (M:N)` — but only in a conceptual sense, and in the schema as given there is in fact `no relationship at all`.
    - Reasoning: a holiday applies to every employee, and every employee observes every holiday, which conceptually is M:N. However, the two tables share no attribute — `Holiday` has only `Date` and `description`, and `Employee` has no date column — so no join is possible and no foreign key exists between them.
    - The only indirect connection is through `Leave.date`, which could coincide with `Holiday.Date`. If that is the intended link, the relationship is:
    ```
    Employee (1) ----< Leave >---- (M) Holiday
    ```
    - That is, `Leave` is the associative entity implementing an M:N relationship between employees and dates.

    (ii) Leave count for every employee
    ```sql
    SELECT   e.employee_id,
             e.name,
             COALESCE(SUM(l.no_leaves), 0) AS total_leaves
    FROM     Employee e
    LEFT JOIN Leave  l ON e.employee_id = l.employee_id
    GROUP BY e.employee_id, e.name;
    ```
    - `LEFT JOIN` is important so that employees who have taken no leave still appear, and `COALESCE(..., 0)` shows 0 rather than NULL for them.
    - `SUM(l.no_leaves)` totals the days; if the question means the number of leave `applications` rather than days, use `COUNT(l.employee_id)` instead.

    Sample output
    ```
    +-------------+-------+--------------+
    | employee_id | name  | total_leaves |
    +-------------+-------+--------------+
    |     101     | Karim |      12      |
    |     102     | Rahim |       5      |
    |     103     | Sumi  |       0      |
    +-------------+-------+--------------+
    ```

    (iii) HR employees who have taken at least 5 leaves
    ```sql
    SELECT   e.employee_id,
             e.name,
             SUM(l.no_leaves) AS total_leaves
    FROM     Employee e
    JOIN     Leave    l ON e.employee_id = l.employee_id
    WHERE    e.department = 'HR'
    GROUP BY e.employee_id, e.name
    HAVING   SUM(l.no_leaves) >= 5;
    ```
    - `WHERE e.department = 'HR'` filters `rows` before grouping — it applies to each employee individually.
    - `HAVING SUM(l.no_leaves) >= 5` filters `groups` after aggregation — it applies to the total. The two clauses do different jobs, and this query shows both in the same statement, which is exactly what examiners look for.

    Sample output
    ```
    +-------------+-------+--------------+
    | employee_id | name  | total_leaves |
    +-------------+-------+--------------+
    |     101     | Karim |      12      |
    |     105     | Nabil |       7      |
    +-------------+-------+--------------+
    ```

59. **Find the Query for the Instructor table a. Find the average salary of instructors in each department. b. Find the names and average salaries of all departments whose average salary is greater than 42000. c. Find names of instructors with salary greater than that of some (at least one) instructor in the CSE department.** *[NRCC Assistant Programmer 2021 compact it 930 (ET: N/A)]*

    Answer:

    Assumed schema
    ```
    Instructor (id, name, dept_name, salary)
    ```

    (a) Average salary of instructors in each department
    ```sql
    SELECT   dept_name,
             AVG(salary) AS average_salary
    FROM     Instructor
    GROUP BY dept_name;
    ```
    - `GROUP BY dept_name` produces one row per department, and `AVG(salary)` averages within each group.

    (b) Departments whose average salary is greater than 42000
    ```sql
    SELECT   dept_name,
             AVG(salary) AS average_salary
    FROM     Instructor
    GROUP BY dept_name
    HAVING   AVG(salary) > 42000;
    ```
    - The condition tests an aggregate, so it belongs in `HAVING`, not `WHERE`. Writing `WHERE AVG(salary) > 42000` is a syntax error, because WHERE is evaluated before grouping takes place.

    Sample output
    ```
    Department averages: Physics 91000, CSE 77333, History 61000, Finance 85000, Biology 72000

    +-----------+----------------+
    | dept_name | average_salary |
    +-----------+----------------+
    | Physics   |     91000      |
    | CSE       |     77333      |
    | History   |     61000      |
    | Finance   |     85000      |
    | Biology   |     72000      |
    +-----------+----------------+
    ```

    (c) Instructors earning more than `some` (at least one) instructor in the CSE department
    ```sql
    SELECT  name, salary
    FROM    Instructor
    WHERE   salary > SOME (SELECT salary FROM Instructor WHERE dept_name = 'CSE');
    ```
    - `> SOME` (equivalently `> ANY`) is true when the value exceeds `at least one` member of the set. It is therefore equivalent to being greater than the `minimum` of that set.

    Equivalent forms
    ```sql
    SELECT name, salary FROM Instructor
    WHERE  salary > ANY (SELECT salary FROM Instructor WHERE dept_name = 'CSE');

    SELECT name, salary FROM Instructor
    WHERE  salary > (SELECT MIN(salary) FROM Instructor WHERE dept_name = 'CSE');
    ```

    The contrast with ALL — the distinction being examined
    ```sql
    -- more than SOME/ANY  =  more than the MINIMUM (at least one)
    WHERE salary > SOME (SELECT salary FROM Instructor WHERE dept_name = 'CSE')

    -- more than ALL       =  more than the MAXIMUM (every one)
    WHERE salary > ALL  (SELECT salary FROM Instructor WHERE dept_name = 'CSE')
    ```

    | Operator | Meaning | Equivalent |
    |---|---|---|
    | `> SOME` / `> ANY` | Greater than at least one | `> MIN(...)` |
    | `> ALL` | Greater than every one | `> MAX(...)` |
    | `< SOME` / `< ANY` | Less than at least one | `< MAX(...)` |
    | `< ALL` | Less than every one | `< MIN(...)` |
    | `= ANY` | Equal to at least one | `IN (...)` |
    | `<> ALL` | Not equal to any | `NOT IN (...)` |

60. **Consider the following relational database schema consisting of the four relation schemas: passenger (pid, ppname, pgender, pcity) agency (aid, aname, acity) flight (fid, fdate, time, src, dest) booking (pid, aid, fid, fdate) a) Get the complete details of all flights to New Delhi b) Get the details about all flights from Chennai to New Delhi.** *[SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)]*

    Answer:

    Schema
    ```
    passenger (pid, ppname, pgender, pcity)
    agency    (aid, aname, acity)
    flight    (fid, fdate, time, src, dest)
    booking   (pid, aid, fid, fdate)
    ```

    (a) Complete details of all flights to New Delhi
    ```sql
    SELECT  *
    FROM    flight
    WHERE   dest = 'New Delhi';
    ```
    - Only the `flight` relation is needed — the destination is an attribute of the flight itself, so no join is required.
    - `SELECT *` is correct because the question asks for "complete details".

    Sample output
    ```
    +-----+------------+-------+-----------+-----------+
    | fid | fdate      | time  | src       | dest      |
    +-----+------------+-------+-----------+-----------+
    | F01 | 2025-06-10 | 09:30 | Chennai   | New Delhi |
    | F05 | 2025-06-10 | 14:00 | Mumbai    | New Delhi |
    | F09 | 2025-06-11 | 18:45 | Chennai   | New Delhi |
    +-----+------------+-------+-----------+-----------+
    ```

    (b) Details of all flights from Chennai to New Delhi
    ```sql
    SELECT  *
    FROM    flight
    WHERE   src  = 'Chennai'
      AND   dest = 'New Delhi';
    ```
    - Both conditions must hold, so they are joined with `AND`. Using `OR` would return every flight leaving Chennai plus every flight arriving in New Delhi — a common slip.

    Sample output
    ```
    +-----+------------+-------+---------+-----------+
    | fid | fdate      | time  | src     | dest      |
    +-----+------------+-------+---------+-----------+
    | F01 | 2025-06-10 | 09:30 | Chennai | New Delhi |
    | F09 | 2025-06-11 | 18:45 | Chennai | New Delhi |
    +-----+------------+-------+---------+-----------+
    ```

    Other standard queries on this well-known schema
    ```sql
    -- passengers who booked a flight to New Delhi
    SELECT DISTINCT p.ppname
    FROM   passenger p
    JOIN   booking   b ON p.pid = b.pid
    JOIN   flight    f ON b.fid = f.fid
    WHERE  f.dest = 'New Delhi';

    -- number of bookings handled by each agency
    SELECT   a.aname, COUNT(*) AS bookings
    FROM     agency  a JOIN booking b ON a.aid = b.aid
    GROUP BY a.aid, a.aname;

    -- agencies located in the same city as the passenger they booked for
    SELECT DISTINCT a.aname
    FROM   agency a JOIN booking b ON a.aid = b.aid
    JOIN   passenger p ON b.pid = p.pid
    WHERE  a.acity = p.pcity;

    -- passengers who have never made a booking
    SELECT p.ppname FROM passenger p
    LEFT JOIN booking b ON p.pid = b.pid
    WHERE  b.pid IS NULL;

    -- the busiest route
    SELECT   src, dest, COUNT(*) AS flights
    FROM     flight
    GROUP BY src, dest
    ORDER BY flights DESC LIMIT 1;
    ```

61. **৫. সম্পূর্ণ টেবিলের ডেটা প্রদর্শন এর জন্য কোনটি ব্যবহার করা হয়?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) To display all the data of a complete table, the statement used is:

    ```sql
    SELECT * FROM table_name;
    ```

    - The `asterisk (*)` is the wildcard meaning "all columns", and omitting the `WHERE` clause means "all rows". Together they return the entire table.

    Example
    ```sql
    SELECT * FROM Student;
    ```
    ```
    +-----------+-------------+-----+------------+
    | StudentID | StudentName | Age | Department |
    +-----------+-------------+-----+------------+
    |     1     | Alice       | 20  | CSE        |
    |     2     | Bob         | 22  | EEE        |
    |     3     | Charlie     | 21  | CSE        |
    +-----------+-------------+-----+------------+
    ```

    Related statements often confused with it

    | Statement | What it shows |
    |---|---|
    | `SELECT * FROM table_name;` | `All the data` in the table |
    | `DESCRIBE table_name;` or `DESC table_name;` | The `structure` — column names, data types, keys — not the data |
    | `SHOW TABLES;` | The list of tables in the current database |
    | `SHOW DATABASES;` | The list of databases |
    | `SELECT COUNT(*) FROM table_name;` | How many rows the table holds |

    Useful refinements
    ```sql
    -- chosen columns only
    SELECT StudentName, Age FROM Student;

    -- sorted
    SELECT * FROM Student ORDER BY Age DESC;

    -- first 10 rows only
    SELECT * FROM Student LIMIT 10;

    -- distinct values of one column
    SELECT DISTINCT Department FROM Student;
    ```

    A practical caution
    - `SELECT *` is convenient in an exam but is discouraged in production code. It returns columns the application may not need, breaks if the table's column order changes, and prevents the database from using a covering index. Naming the required columns explicitly is the better habit.

62. **Write a SQL query to find those employees who report that manager whose first name is ‘abc’. Return first name, last name, employee ID and salary.** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 947 (ET: BUET)]*

    Answer: The employee and the manager are both rows of the same table, so a `self join` is required.

    Query
    ```sql
    SELECT  e.first_name,
            e.last_name,
            e.employee_id,
            e.salary
    FROM    employees e
    JOIN    employees m ON e.manager_id = m.employee_id
    WHERE   m.first_name = 'abc';
    ```

    How it works
    - The table appears twice: alias `e` is the reporting employee and alias `m` is the manager.
    - `e.manager_id = m.employee_id` is the join condition linking each employee to their own manager.
    - `WHERE m.first_name = 'abc'` restricts the result to the subordinates of that particular manager.

    Sample data and result
    ```
    employees
    +-------------+------------+-----------+--------+------------+
    | employee_id | first_name | last_name | salary | manager_id |
    +-------------+------------+-----------+--------+------------+
    |     100     | abc        | Rahman    | 90000  |    NULL    |
    |     101     | Karim      | Ahmed     | 60000  |    100     |
    |     102     | Rahim      | Uddin     | 55000  |    100     |
    |     103     | Sumi       | Akter     | 50000  |    102     |
    +-------------+------------+-----------+--------+------------+

    Result
    +------------+-----------+-------------+--------+
    | first_name | last_name | employee_id | salary |
    +------------+-----------+-------------+--------+
    | Karim      | Ahmed     |     101     | 60000  |
    | Rahim      | Uddin     |     102     | 55000  |
    +------------+-----------+-------------+--------+
    ```
    - Sumi reports to Rahim, not to abc, so she is excluded. This is a direct-reports query, not a whole-hierarchy query.

    Subquery alternative
    ```sql
    SELECT first_name, last_name, employee_id, salary
    FROM   employees
    WHERE  manager_id = (SELECT employee_id FROM employees WHERE first_name = 'abc');
    ```
    - Simpler to read, but it fails with an error if more than one manager is named 'abc'. Using `IN` instead of `=` handles that:
    ```sql
    WHERE manager_id IN (SELECT employee_id FROM employees WHERE first_name = 'abc');
    ```

    If the whole reporting chain is wanted, not just direct reports
    ```sql
    WITH RECURSIVE subordinates AS (
        SELECT employee_id, first_name, last_name, salary, manager_id
        FROM   employees WHERE first_name = 'abc'
        UNION ALL
        SELECT e.employee_id, e.first_name, e.last_name, e.salary, e.manager_id
        FROM   employees e JOIN subordinates s ON e.manager_id = s.employee_id
    )
    SELECT first_name, last_name, employee_id, salary FROM subordinates
    WHERE  first_name <> 'abc';
    ```
    - A `recursive CTE` walks down the hierarchy level by level, so Sumi would also appear. This is the standard technique for organisation charts and bill-of-materials queries.

63. **Given a database schema and worker table with fully code: Now writes SQL Query from the following questions.** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 975 (ET: BUET)]*

    Answer: The specific schema was not printed, so a `Worker` table in the standard form used by this question is assumed, together with the queries usually set on it.

    Schema
    ```sql
    CREATE TABLE Worker (
        WORKER_ID    INT PRIMARY KEY AUTO_INCREMENT,
        FIRST_NAME   VARCHAR(25),
        LAST_NAME    VARCHAR(25),
        SALARY       INT,
        JOINING_DATE DATETIME,
        DEPARTMENT   VARCHAR(25)
    );

    INSERT INTO Worker VALUES
     (001,'Monika','Arora',100000,'2014-02-20 09:00:00','HR'),
     (002,'Niharika','Verma',80000,'2014-06-11 09:00:00','Admin'),
     (003,'Vishal','Singhal',300000,'2014-02-20 09:00:00','HR'),
     (004,'Amitabh','Singh',500000,'2014-02-20 09:00:00','Admin'),
     (005,'Vivek','Bhati',500000,'2014-06-11 09:00:00','Admin'),
     (006,'Vipul','Diwan',200000,'2014-06-11 09:00:00','Account'),
     (007,'Satish','Kumar',75000,'2014-01-20 09:00:00','Account'),
     (008,'Geetika','Chauhan',90000,'2014-04-11 09:00:00','Admin');
    ```

    Standard queries

    ```sql
    -- 1. all workers
    SELECT * FROM Worker;

    -- 2. first names in upper case
    SELECT UPPER(FIRST_NAME) AS FIRST_NAME FROM Worker;

    -- 3. distinct departments
    SELECT DISTINCT DEPARTMENT FROM Worker;

    -- 4. first three characters of each first name
    SELECT SUBSTRING(FIRST_NAME, 1, 3) FROM Worker;

    -- 5. full name in one column
    SELECT CONCAT(FIRST_NAME, ' ', LAST_NAME) AS FULL_NAME FROM Worker;

    -- 6. sorted by first name ascending, department descending
    SELECT * FROM Worker ORDER BY FIRST_NAME ASC, DEPARTMENT DESC;

    -- 7. workers in Admin
    SELECT * FROM Worker WHERE DEPARTMENT = 'Admin';

    -- 8. names containing 'a'
    SELECT * FROM Worker WHERE FIRST_NAME LIKE '%a%';

    -- 9. names ending with 'h' and exactly six characters long
    SELECT * FROM Worker WHERE FIRST_NAME LIKE '_____h';

    -- 10. salary between 100000 and 500000
    SELECT * FROM Worker WHERE SALARY BETWEEN 100000 AND 500000;

    -- 11. joined in February 2014
    SELECT * FROM Worker
    WHERE  JOINING_DATE >= '2014-02-01' AND JOINING_DATE < '2014-03-01';

    -- 12. number of workers in Admin
    SELECT COUNT(*) FROM Worker WHERE DEPARTMENT = 'Admin';

    -- 13. workers earning more than 50000, name and salary, highest first
    SELECT CONCAT(FIRST_NAME,' ',LAST_NAME) AS NAME, SALARY
    FROM   Worker WHERE SALARY > 50000 ORDER BY SALARY DESC;

    -- 14. department-wise count, largest first
    SELECT   DEPARTMENT, COUNT(*) AS WORKERS
    FROM     Worker GROUP BY DEPARTMENT ORDER BY WORKERS DESC;

    -- 15. departments with fewer than four workers
    SELECT   DEPARTMENT, COUNT(*) FROM Worker
    GROUP BY DEPARTMENT HAVING COUNT(*) < 4;

    -- 16. highest salary
    SELECT MAX(SALARY) FROM Worker;

    -- 17. second highest salary
    SELECT MAX(SALARY) FROM Worker WHERE SALARY < (SELECT MAX(SALARY) FROM Worker);

    -- 18. workers with the same salary as another worker
    SELECT * FROM Worker
    WHERE  SALARY IN (SELECT SALARY FROM Worker GROUP BY SALARY HAVING COUNT(*) > 1);

    -- 19. department with the highest total salary
    SELECT   DEPARTMENT, SUM(SALARY) AS TOTAL FROM Worker
    GROUP BY DEPARTMENT ORDER BY TOTAL DESC LIMIT 1;

    -- 20. top 5 earners
    SELECT * FROM Worker ORDER BY SALARY DESC LIMIT 5;

    -- 21. the 5th highest salary
    SELECT DISTINCT SALARY FROM Worker ORDER BY SALARY DESC LIMIT 1 OFFSET 4;

    -- 22. duplicate first names
    SELECT FIRST_NAME, COUNT(*) FROM Worker
    GROUP  BY FIRST_NAME HAVING COUNT(*) > 1;

    -- 23. give everyone in HR a 10 percent raise
    UPDATE Worker SET SALARY = SALARY * 1.10 WHERE DEPARTMENT = 'HR';
    ```
    - The rule that answers most of these: SQL evaluates `FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY -> LIMIT`. <!-- verify -->

64. **(b) SQL Query: commission greater than 10%** *[National University Assistant Programmer 2020 compact it 976 (ET: DU)]*

    Answer: "Commission greater than 10 percent" depends on how the commission is stored, and both forms appear in real schemas.

    If commission is stored as a `fraction` (0.10 means 10 percent)
    ```sql
    SELECT  employee_id,
            first_name,
            last_name,
            salary,
            commission_pct
    FROM    employees
    WHERE   commission_pct > 0.10;
    ```
    - This is the Oracle HR schema convention, where `commission_pct` holds values such as 0.15 and 0.25.

    If commission is stored as a `percentage number` (10 means 10 percent)
    ```sql
    SELECT employee_id, first_name, last_name, salary, commission
    FROM   employees
    WHERE  commission > 10;
    ```

    If the commission is an `amount` and the 10 percent is of salary
    ```sql
    SELECT employee_id, first_name, last_name, salary, commission
    FROM   employees
    WHERE  commission > salary * 0.10;
    ```

    Sample output for the first form
    ```
    employees
    +-------------+------------+--------+----------------+
    | employee_id | first_name | salary | commission_pct |
    +-------------+------------+--------+----------------+
    |    101      | Karim      | 60000  |     0.05       |
    |    102      | Rahim      | 55000  |     0.15       |
    |    103      | Sumi       | 70000  |     0.25       |
    |    104      | Nabil      | 45000  |     NULL       |
    +-------------+------------+--------+----------------+

    Result
    +-------------+------------+--------+----------------+
    | employee_id | first_name | salary | commission_pct |
    +-------------+------------+--------+----------------+
    |    102      | Rahim      | 55000  |     0.15       |
    |    103      | Sumi       | 70000  |     0.25       |
    +-------------+------------+--------+----------------+
    ```

    The NULL trap worth noting
    - Nabil has `NULL` commission and is `not` returned, because any comparison with NULL yields UNKNOWN, never TRUE. This is correct here — a NULL commission is not greater than 10 percent — but it must be understood, not stumbled upon.
    - To treat NULL as zero explicitly:
    ```sql
    WHERE COALESCE(commission_pct, 0) > 0.10
    ```
    - To find those with no commission at all:
    ```sql
    SELECT * FROM employees WHERE commission_pct IS NULL;
    ```
    - Note that `WHERE commission_pct = NULL` never matches anything; `IS NULL` is the only correct test.

    Related useful queries
    ```sql
    -- total earnings including commission, NULLs treated as zero
    SELECT first_name, salary,
           salary + (salary * COALESCE(commission_pct, 0)) AS total_earning
    FROM   employees;

    -- highest commission percentage in each department
    SELECT   department_id, MAX(commission_pct) FROM employees
    GROUP BY department_id;
    ```

65. **(c) Remove duplicate data from table** *[National University Assistant Programmer 2020 compact it 976 (ET: DU)]*

    Answer: Duplicates are removed by keeping one row of each group — usually the one with the lowest primary key — and deleting the rest.

    Method 1 — DELETE using a subquery on the minimum id
    ```sql
    DELETE FROM Employee
    WHERE  emp_id NOT IN (
              SELECT MIN(emp_id)
              FROM   Employee
              GROUP  BY emp_name, salary, dept_id      -- the columns that define a duplicate
           );
    ```
    - The subquery lists one surviving id per distinct combination; everything else is deleted.
    - `MySQL` refuses to read from the same table it is deleting from, so the subquery must be wrapped in a derived table:
    ```sql
    DELETE FROM Employee
    WHERE  emp_id NOT IN (
              SELECT keep FROM (
                  SELECT MIN(emp_id) AS keep FROM Employee
                  GROUP BY emp_name, salary, dept_id
              ) AS t
           );
    ```

    Method 2 — a self join, which is the fastest form in MySQL
    ```sql
    DELETE e1 FROM Employee e1
    JOIN   Employee e2
      ON   e1.emp_name = e2.emp_name
     AND   e1.salary   = e2.salary
     AND   e1.emp_id   > e2.emp_id;
    ```
    - Every row that has an identical twin with a smaller id is deleted, so exactly one copy survives.

    Method 3 — a window function, the modern approach
    ```sql
    DELETE FROM Employee
    WHERE  emp_id IN (
        SELECT emp_id FROM (
            SELECT emp_id,
                   ROW_NUMBER() OVER (PARTITION BY emp_name, salary, dept_id
                                      ORDER BY emp_id) AS rn
            FROM   Employee
        ) t
        WHERE rn > 1
    );
    ```
    - `ROW_NUMBER()` numbers the copies within each duplicate group; everything numbered above 1 is removed.

    Method 4 — rebuild the table, safest for very large tables
    ```sql
    CREATE TABLE Employee_clean AS SELECT DISTINCT * FROM Employee;
    DROP  TABLE Employee;
    RENAME TABLE Employee_clean TO Employee;
    ```
    - Faster than a large DELETE, but indexes, constraints and permissions must be recreated afterwards.

    Before deleting anything — always check first
    ```sql
    -- see which rows are duplicated, and how many copies exist
    SELECT emp_name, salary, dept_id, COUNT(*) AS copies
    FROM   Employee
    GROUP  BY emp_name, salary, dept_id
    HAVING COUNT(*) > 1;
    ```

    Preventing the problem in the first place
    ```sql
    ALTER TABLE Employee ADD CONSTRAINT uq_emp UNIQUE (emp_name, dept_id);
    ```
    - A `UNIQUE` constraint makes duplicates impossible, which is far better than cleaning them up repeatedly. Deletion is a cure; the constraint is the prevention.
    - Run any of the deletes inside a transaction, so it can be rolled back if the result is not what was expected.

66. **What is the full meaning of SQL? List of the aggregate function. Write SQL Query of a table and its output.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1002-1003 (ET: DU)]*

    Answer:

    Full form of SQL
    - `SQL` stands for `Structured Query Language`. It is the standard language for defining, manipulating and querying data in a relational database, standardised by ANSI in 1986 and ISO in 1987.
    - Pronounced either "S-Q-L" or "sequel"; its predecessor at IBM was called SEQUEL.

    The aggregate functions

    | Function | Purpose | NULL handling |
    |---|---|---|
    | `COUNT()` | Number of rows or of non-null values | `COUNT(*)` counts all rows; `COUNT(col)` skips NULLs |
    | `SUM()` | Total of a numeric column | Ignores NULLs |
    | `AVG()` | Arithmetic mean | Ignores NULLs, so the divisor is the non-null count |
    | `MAX()` | Largest value | Ignores NULLs |
    | `MIN()` | Smallest value | Ignores NULLs |

    - Others available in most systems: `STDDEV`, `VARIANCE`, and `GROUP_CONCAT` (MySQL) or `STRING_AGG` (PostgreSQL, SQL Server).
    - Key rule: an aggregate function may not appear in a `WHERE` clause, because WHERE is evaluated before grouping. Conditions on aggregates belong in `HAVING`.

    A worked query with its output
    ```sql
    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,
        emp_name VARCHAR(50),
        dept     VARCHAR(30),
        salary   DECIMAL(10,2)
    );

    INSERT INTO Employee VALUES
     (1,'Karim','IT',50000), (2,'Rahim','IT',60000),
     (3,'Sumi','HR',40000),  (4,'Nabil','HR',45000),
     (5,'Jamil','IT',70000);
    ```

    Query
    ```sql
    SELECT   dept,
             COUNT(*)    AS employees,
             SUM(salary) AS total_salary,
             AVG(salary) AS average_salary,
             MAX(salary) AS highest,
             MIN(salary) AS lowest
    FROM     Employee
    GROUP BY dept
    HAVING   COUNT(*) > 1
    ORDER BY average_salary DESC;
    ```

    Output
    ```
    +------+-----------+--------------+----------------+---------+--------+
    | dept | employees | total_salary | average_salary | highest | lowest |
    +------+-----------+--------------+----------------+---------+--------+
    | IT   |     3     |    180000    |    60000.00    |  70000  | 50000  |
    | HR   |     2     |     85000    |    42500.00    |  45000  | 40000  |
    +------+-----------+--------------+----------------+---------+--------+
    ```

    Whole-table aggregates, with no GROUP BY
    ```sql
    SELECT COUNT(*), SUM(salary), AVG(salary), MAX(salary), MIN(salary) FROM Employee;
    ```
    ```
    +----------+--------+----------+--------+--------+
    | COUNT(*) | SUM    | AVG      | MAX    | MIN    |
    +----------+--------+----------+--------+--------+
    |    5     | 265000 | 53000.00 | 70000  | 40000  |
    +----------+--------+----------+--------+--------+
    ```
    - Without `GROUP BY`, the whole table is treated as a single group and exactly one row is returned.

67. **Query to find out even number from given table.** *[RAKUB Assistant Database Administrator 2020 compact it 1014 (ET: E-Zone)]*

    Answer: A number is even when it leaves no remainder on division by 2, so the `modulo` operator is used.

    Query
    ```sql
    SELECT  *
    FROM    Numbers
    WHERE   num % 2 = 0;
    ```

    Sample data and output
    ```
    Numbers
    +----+-----+
    | id | num |
    +----+-----+
    | 1  | 10  |
    | 2  |  7  |
    | 3  | 24  |
    | 4  |  3  |
    | 5  | 18  |
    +----+-----+

    Result
    +----+-----+
    | id | num |
    +----+-----+
    | 1  | 10  |
    | 3  | 24  |
    | 5  | 18  |
    +----+-----+
    ```

    Odd numbers, for contrast
    ```sql
    SELECT * FROM Numbers WHERE num % 2 <> 0;
    -- or
    SELECT * FROM Numbers WHERE num % 2 = 1;
    ```
    - The `<> 0` form is safer for negative numbers: in some systems `-3 % 2` yields `-1`, not `1`, so `= 1` would miss it.

    Equivalents in different database systems
    ```sql
    -- MySQL, PostgreSQL, SQL Server
    WHERE num % 2 = 0

    -- Oracle and standard SQL
    WHERE MOD(num, 2) = 0

    -- bitwise test, works in MySQL and SQL Server
    WHERE num & 1 = 0
    ```

    Selecting rows at even `positions` rather than even values
    - If the intent is every second row, a window function is needed:
    ```sql
    SELECT * FROM (
        SELECT t.*, ROW_NUMBER() OVER (ORDER BY id) AS rn
        FROM   Numbers t
    ) x
    WHERE rn % 2 = 0;
    ```
    - In MySQL 5.x, which has no window functions, a user variable is used instead:
    ```sql
    SET @row = 0;
    SELECT * FROM (SELECT *, (@row := @row + 1) AS rn FROM Numbers ORDER BY id) x
    WHERE  rn % 2 = 0;
    ```

    Related examples
    ```sql
    -- even ids
    SELECT * FROM Employee WHERE emp_id % 2 = 0;

    -- count how many are even and how many odd
    SELECT SUM(CASE WHEN num % 2 = 0 THEN 1 ELSE 0 END) AS evens,
           SUM(CASE WHEN num % 2 <> 0 THEN 1 ELSE 0 END) AS odds
    FROM   Numbers;

    -- label each row
    SELECT num, CASE WHEN num % 2 = 0 THEN 'Even' ELSE 'Odd' END AS parity
    FROM   Numbers;
    ```
    - Performance note: `WHERE num % 2 = 0` applies a function to the column, so an index on `num` cannot be used and the whole table is scanned. For a large table where this query is frequent, a computed column or a filtered index would be the remedy.

68. **How to copy from Parent table to Child Table with 1 column dividing into 3 different columns?** *[RAKUB Assistant Database Administrator 2020 compact it 1014-1015 (ET: E-Zone)]*

    Answer: The requirement is to copy rows from a parent table into a child table while `splitting one column into three`. The tool for this is `INSERT ... SELECT` with string functions.

    The situation
    ```
    Parent                                  Child (target)
    +----+---------------------+            +----+-------+--------+------+
    | id | full_address        |            | id | house | road   | city |
    +----+---------------------+            +----+-------+--------+------+
    | 1  | 12,Green Road,Dhaka |    ->      | 1  | 12    | Green  | Dhaka|
    | 2  | 45,Blue Lane,Khulna |            | 2  | 45    | Blue   |Khulna|
    +----+---------------------+            +----+-------+--------+------+
    ```

    MySQL — splitting on a delimiter with SUBSTRING_INDEX
    ```sql
    INSERT INTO Child (id, house, road, city)
    SELECT  id,
            SUBSTRING_INDEX(full_address, ',', 1)                       AS house,
            SUBSTRING_INDEX(SUBSTRING_INDEX(full_address, ',', 2), ',', -1) AS road,
            SUBSTRING_INDEX(full_address, ',', -1)                      AS city
    FROM    Parent;
    ```
    - `SUBSTRING_INDEX(str, ',', 1)` takes everything before the first comma.
    - `SUBSTRING_INDEX(str, ',', -1)` takes everything after the last comma.
    - The nested form extracts the middle piece: take the first two fields, then the last of those.

    PostgreSQL — SPLIT_PART, which is the clearest
    ```sql
    INSERT INTO Child (id, house, road, city)
    SELECT id,
           SPLIT_PART(full_address, ',', 1),
           SPLIT_PART(full_address, ',', 2),
           SPLIT_PART(full_address, ',', 3)
    FROM   Parent;
    ```

    SQL Server — using CHARINDEX and SUBSTRING
    ```sql
    INSERT INTO Child (id, house, road, city)
    SELECT id,
           LEFT(full_address, CHARINDEX(',', full_address) - 1),
           SUBSTRING(full_address,
                     CHARINDEX(',', full_address) + 1,
                     CHARINDEX(',', full_address, CHARINDEX(',', full_address) + 1)
                     - CHARINDEX(',', full_address) - 1),
           RIGHT(full_address,
                 LEN(full_address) - CHARINDEX(',', full_address,
                                     CHARINDEX(',', full_address) + 1))
    FROM   Parent;
    ```

    Splitting by `fixed width` instead of a delimiter
    ```sql
    -- e.g. a 12-character code: 4 for branch, 4 for account type, 4 for serial
    INSERT INTO Child (id, branch, acc_type, serial)
    SELECT id,
           SUBSTRING(code, 1, 4),
           SUBSTRING(code, 5, 4),
           SUBSTRING(code, 9, 4)
    FROM   Parent;
    ```

    Splitting a full name into first, middle and last
    ```sql
    INSERT INTO Child (id, first_name, middle_name, last_name)
    SELECT id,
           SUBSTRING_INDEX(full_name, ' ', 1),
           SUBSTRING_INDEX(SUBSTRING_INDEX(full_name, ' ', 2), ' ', -1),
           SUBSTRING_INDEX(full_name, ' ', -1)
    FROM   Parent;
    ```

    Practical cautions
    - Always run the `SELECT` part on its own first and inspect the output before wrapping it in an INSERT.
    - Rows with a different number of delimiters will split wrongly; filter or handle them separately.
    - `TRIM()` the results, since a space usually follows each comma.
    - Wrap the whole operation in a transaction so it can be rolled back:
    ```sql
    BEGIN;
    INSERT INTO Child (...) SELECT ... FROM Parent;
    SELECT * FROM Child LIMIT 20;      -- verify
    COMMIT;                             -- or ROLLBACK
    ```
    - Design note: storing three separate values in one column violates `first normal form`. Splitting them, as this question does, is exactly the normalisation step that fixes it.

69. **Design and Queries from HR schema. (i) Display details of jobs where the minimum salary is greater than 10000. (ii) Display the first name and join date of the employees who joined between 2002 and 2005. (iii) Display first name and join date of the employees who is either IT Programmer or Sales Man. (iv) Display first name, salary, commission pct, and hire date for employees with salary less than 10000. (v) Display job Title, the difference between minimum and maximum salaries for jobs with max salary in the range 10000 to 20000. (vi) Display first name, salary, and round the salary to thousands. (vii) Display employees where the first name or last name starts with S. (viii) Display details of the employees where commission percentage is null and salary in the range 5000 to 10000 and department is 30. (ix) Display first name and date of first salary of the employees. (x) Display first name and last name after converting the first letter of each name to upper case and the rest to lower case.** *[RAKUB Assistant Database Administrator 2020 compact it 1016-1017 (ET: E-Zone)]*

    Answer: The Oracle `HR` schema is assumed: `employees(employee_id, first_name, last_name, salary, commission_pct, hire_date, job_id, department_id)` and `jobs(job_id, job_title, min_salary, max_salary)`.

    (i) Jobs where the minimum salary is greater than 10000
    ```sql
    SELECT * FROM jobs WHERE min_salary > 10000;
    ```

    (ii) First name and join date of employees who joined between 2002 and 2005
    ```sql
    SELECT first_name, hire_date
    FROM   employees
    WHERE  hire_date >= '2002-01-01' AND hire_date < '2006-01-01';
    ```
    - The range form is preferred over `YEAR(hire_date) BETWEEN 2002 AND 2005`, because wrapping the column in a function prevents an index from being used.

    (iii) First name and join date of IT Programmers or Sales Men
    ```sql
    SELECT first_name, hire_date
    FROM   employees
    WHERE  job_id IN ('IT_PROG', 'SA_MAN');
    ```

    (iv) First name, salary, commission_pct and hire date for employees earning less than 10000
    ```sql
    SELECT first_name, salary, commission_pct, hire_date
    FROM   employees
    WHERE  salary < 10000;
    ```

    (v) Job title and the salary spread, for jobs with a maximum salary between 10000 and 20000
    ```sql
    SELECT job_title,
           (max_salary - min_salary) AS salary_difference
    FROM   jobs
    WHERE  max_salary BETWEEN 10000 AND 20000;
    ```

    (vi) First name, salary, and the salary rounded to thousands
    ```sql
    SELECT first_name, salary, ROUND(salary, -3) AS rounded_salary
    FROM   employees;
    ```
    - A `negative` second argument to ROUND rounds to the left of the decimal point: −3 rounds to the nearest thousand, so 17,499 becomes 17,000 and 17,500 becomes 18,000.

    (vii) Employees whose first name or last name starts with S
    ```sql
    SELECT first_name, last_name
    FROM   employees
    WHERE  first_name LIKE 'S%' OR last_name LIKE 'S%';
    ```

    (viii) Commission percentage NULL, salary between 5000 and 10000, department 30
    ```sql
    SELECT *
    FROM   employees
    WHERE  commission_pct IS NULL
      AND  salary BETWEEN 5000 AND 10000
      AND  department_id = 30;
    ```
    - `IS NULL` is essential; `= NULL` never matches anything, because a comparison with NULL yields UNKNOWN.

    (ix) First name and the date of the first salary
    ```sql
    SELECT first_name,
           LAST_DAY(hire_date) + 1 AS first_salary_date
    FROM   employees;
    ```
    - Interpreting "date of first salary" as the first day of the month following the hire date, which is the usual convention. `LAST_DAY` returns the last day of the hire month, and adding one day gives the first of the next.

    (x) First and last name with the first letter capitalised and the rest lower case
    ```sql
    SELECT INITCAP(first_name) AS first_name,
           INITCAP(last_name)  AS last_name
    FROM   employees;
    ```
    - `INITCAP` is Oracle and PostgreSQL. In MySQL there is no such function, so it is built manually:
    ```sql
    SELECT CONCAT(UPPER(SUBSTRING(first_name,1,1)), LOWER(SUBSTRING(first_name,2))) AS first_name,
           CONCAT(UPPER(SUBSTRING(last_name ,1,1)), LOWER(SUBSTRING(last_name ,2))) AS last_name
    FROM   employees;
    ```

70. **Query for retrieving UNCOMMON Name from Name column of two given tables.** *[RAKUB Assistant Database Administrator 2020 compact it 1017 (ET: E-Zone)]*

    Answer: "Uncommon" names are those appearing in one table but not the other — the `symmetric difference` of the two sets.

    The two tables
    ```
    TableA              TableB
    +-------+           +-------+
    | Name  |           | Name  |
    +-------+           +-------+
    | Karim |           | Rahim |
    | Rahim |           | Sumi  |
    | Nabil |           | Karim |
    +-------+           +-------+

    Common      : Karim, Rahim
    Uncommon    : Nabil (only in A), Sumi (only in B)
    ```

    Method 1 — using EXCEPT twice with UNION
    ```sql
    SELECT Name FROM TableA
    EXCEPT
    SELECT Name FROM TableB

    UNION

    SELECT Name FROM TableB
    EXCEPT
    SELECT Name FROM TableA;
    ```
    - Clear and direct, but `EXCEPT` is not available in MySQL. Oracle calls it `MINUS`.

    Method 2 — FULL OUTER JOIN, the standard portable approach
    ```sql
    SELECT COALESCE(a.Name, b.Name) AS uncommon_name
    FROM   TableA a
    FULL OUTER JOIN TableB b ON a.Name = b.Name
    WHERE  a.Name IS NULL OR b.Name IS NULL;
    ```
    - The full outer join keeps every row from both sides; the WHERE clause keeps only the rows where one side failed to match.

    Method 3 — NOT IN, which works everywhere including MySQL
    ```sql
    SELECT Name FROM TableA
    WHERE  Name NOT IN (SELECT Name FROM TableB)

    UNION

    SELECT Name FROM TableB
    WHERE  Name NOT IN (SELECT Name FROM TableA);
    ```
    - Caution: `NOT IN` returns `no rows at all` if the subquery contains a NULL, because the comparison becomes UNKNOWN. Guard against it:
    ```sql
    WHERE Name NOT IN (SELECT Name FROM TableB WHERE Name IS NOT NULL)
    ```

    Method 4 — NOT EXISTS, which is NULL-safe and usually the fastest
    ```sql
    SELECT a.Name FROM TableA a
    WHERE  NOT EXISTS (SELECT 1 FROM TableB b WHERE b.Name = a.Name)

    UNION

    SELECT b.Name FROM TableB b
    WHERE  NOT EXISTS (SELECT 1 FROM TableA a WHERE a.Name = b.Name);
    ```

    Method 5 — UNION ALL with a count, a neat trick
    ```sql
    SELECT Name FROM (
        SELECT Name FROM TableA
        UNION ALL
        SELECT Name FROM TableB
    ) t
    GROUP BY Name
    HAVING COUNT(*) = 1;
    ```
    - A name appearing in both tables occurs twice in the combined list; an uncommon name occurs once. This assumes no duplicates within either table.

    Result in every case
    ```
    +---------------+
    | uncommon_name |
    +---------------+
    | Nabil         |
    | Sumi          |
    +---------------+
    ```

    For contrast — the `common` names
    ```sql
    SELECT Name FROM TableA INTERSECT SELECT Name FROM TableB;
    -- or, portably:
    SELECT a.Name FROM TableA a JOIN TableB b ON a.Name = b.Name;
    ```

71. **Employee টেবিল থেকে যেসকল Employee এর Salary 25000 থেকে 50000 এর মধ্যে এবং Designation হচ্ছে officer এবং City হচ্ছে Dhaka তাদের দেখার জন্য SQL টেবিল দেখান।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1042 (ET: DPI)]*

    Answer: (Answered in English, as required for IT topics.) Three conditions must all hold, so they are combined with `AND`.

    Query
    ```sql
    SELECT  *
    FROM    Employee
    WHERE   Salary BETWEEN 25000 AND 50000
      AND   Designation = 'Officer'
      AND   City = 'Dhaka';
    ```

    - `BETWEEN 25000 AND 50000` is inclusive at both ends, so 25000 and 50000 themselves qualify. It is equivalent to `Salary >= 25000 AND Salary <= 50000`.
    - All three conditions are joined with `AND`, so an employee must satisfy every one. Using `OR` would return anyone in the salary range, plus every Officer anywhere, plus everyone in Dhaka — a very different and much larger result.

    Sample data and output
    ```
    Employee
    +--------+----------+--------+-------------+------------+
    | emp_id | emp_name | Salary | Designation | City       |
    +--------+----------+--------+-------------+------------+
    |   1    | Karim    | 30000  | Officer     | Dhaka      |   ✓
    |   2    | Rahim    | 60000  | Officer     | Dhaka      |   ✗ salary too high
    |   3    | Sumi     | 35000  | Manager     | Dhaka      |   ✗ wrong designation
    |   4    | Nabil    | 40000  | Officer     | Chattogram |   ✗ wrong city
    |   5    | Jamil    | 25000  | Officer     | Dhaka      |   ✓ boundary included
    +--------+----------+--------+-------------+------------+

    Result
    +--------+----------+--------+-------------+-------+
    | emp_id | emp_name | Salary | Designation | City  |
    +--------+----------+--------+-------------+-------+
    |   1    | Karim    | 30000  | Officer     | Dhaka |
    |   5    | Jamil    | 25000  | Officer     | Dhaka |
    +--------+----------+--------+-------------+-------+
    ```

    If the boundaries should be `excluded`
    ```sql
    SELECT * FROM Employee
    WHERE  Salary > 25000 AND Salary < 50000
      AND  Designation = 'Officer' AND City = 'Dhaka';
    ```
    - This is the distinction the question hinges on: "between 25000 and 50000" is normally read as inclusive, which `BETWEEN` gives.

    Useful refinements
    ```sql
    -- selected columns, sorted by salary
    SELECT emp_name, Designation, Salary FROM Employee
    WHERE  Salary BETWEEN 25000 AND 50000 AND Designation = 'Officer' AND City = 'Dhaka'
    ORDER  BY Salary DESC;

    -- how many such employees there are
    SELECT COUNT(*) FROM Employee
    WHERE  Salary BETWEEN 25000 AND 50000 AND Designation = 'Officer' AND City = 'Dhaka';

    -- several designations accepted
    SELECT * FROM Employee
    WHERE  Salary BETWEEN 25000 AND 50000
      AND  Designation IN ('Officer', 'Senior Officer')
      AND  City = 'Dhaka';
    ```

72. **Design a database of student with the gpa of a university. Find the top 10% gpa holder from the different department of the university.** *[Combined 5 Banks Assistant Maintenance Engineer 2019 compact it 1055 (ET: AUST)]*

    Answer:

    Part 1 — designing the database
    ```sql
    CREATE TABLE Department (
        dept_id   INT PRIMARY KEY,
        dept_name VARCHAR(50) NOT NULL UNIQUE
    );

    CREATE TABLE Student (
        student_id INT PRIMARY KEY,
        name       VARCHAR(100) NOT NULL,
        dept_id    INT NOT NULL,
        gpa        DECIMAL(3,2) CHECK (gpa BETWEEN 0.00 AND 4.00),
        session    VARCHAR(20),
        FOREIGN KEY (dept_id) REFERENCES Department(dept_id)
    );
    ```
    - `dept_id` is a foreign key, which enforces referential integrity — a student cannot belong to a department that does not exist.
    - `CHECK (gpa BETWEEN 0 AND 4)` prevents an impossible GPA from ever being stored.
    - `DECIMAL(3,2)` is right for a GPA; `FLOAT` should be avoided because binary floating point cannot represent decimal values exactly.

    Part 2 — the top 10 percent GPA holders in each department

    Modern SQL, using a window function — the clean solution
    ```sql
    SELECT   dept_name, name, gpa
    FROM (
        SELECT   d.dept_name,
                 s.name,
                 s.gpa,
                 PERCENT_RANK() OVER (PARTITION BY s.dept_id ORDER BY s.gpa DESC) AS pr
        FROM     Student s
        JOIN     Department d ON s.dept_id = d.dept_id
    ) t
    WHERE    pr <= 0.10
    ORDER BY dept_name, gpa DESC;
    ```
    - `PARTITION BY s.dept_id` restarts the ranking for each department, which is what "from the different departments" requires.
    - `PERCENT_RANK()` returns a value from 0 to 1 giving each student's relative position, so `<= 0.10` selects the top tenth.

    Alternative using NTILE, which divides each department into ten equal bands
    ```sql
    SELECT dept_name, name, gpa FROM (
        SELECT d.dept_name, s.name, s.gpa,
               NTILE(10) OVER (PARTITION BY s.dept_id ORDER BY s.gpa DESC) AS band
        FROM   Student s JOIN Department d ON s.dept_id = d.dept_id
    ) t
    WHERE band = 1;
    ```

    Without window functions — a correlated subquery counting how many are better
    ```sql
    SELECT d.dept_name, s.name, s.gpa
    FROM   Student s
    JOIN   Department d ON s.dept_id = d.dept_id
    WHERE  (SELECT COUNT(*) FROM Student x
            WHERE  x.dept_id = s.dept_id AND x.gpa > s.gpa)
           < (SELECT COUNT(*) * 0.10 FROM Student y WHERE y.dept_id = s.dept_id)
    ORDER  BY d.dept_name, s.gpa DESC;
    ```
    - Reads as: a student is in the top 10 percent when fewer than 10 percent of their department's students have a higher GPA.

    The whole university, ignoring departments
    ```sql
    SELECT name, gpa FROM Student
    ORDER  BY gpa DESC
    LIMIT (SELECT CEIL(COUNT(*) * 0.10) FROM Student);
    ```

    Points worth stating
    - `LIMIT 10` is `not` the same as "top 10 percent" — the number of students differs from department to department, so a percentage must be computed per department.
    - Ties matter: `PERCENT_RANK()` gives tied GPAs the same value, so a tie at the boundary correctly includes all of them. `ROW_NUMBER()` would arbitrarily cut between equal students.

73. **(খ) SQL ব্যবহার করে Student নামে একটি টেবিল তৈরি করুন। টেবিলে Std-id, Std-name, Std-address এবং GPA নামে চারটি field থাকবে। Student টেবিল হতে যে সকল ছাত্রের ফলাফল GPA-5 তাদের সকল রেকর্ড দেখানোর জন্য SQL Query লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1097 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    Part 1 — creating the Student table
    ```sql
    CREATE TABLE Student (
        Std_id      INT PRIMARY KEY,
        Std_name    VARCHAR(100) NOT NULL,
        Std_address VARCHAR(200),
        GPA         DECIMAL(3,2) CHECK (GPA BETWEEN 0.00 AND 5.00)
    );
    ```
    - `PRIMARY KEY` on `Std_id` makes it unique and not null, so no two students can share an id.
    - `NOT NULL` on the name forbids a nameless record.
    - `DECIMAL(3,2)` holds values such as 5.00 and 4.75 exactly; `FLOAT` should be avoided for grades because binary floating point is inexact.
    - `CHECK` restricts the GPA to the valid Bangladeshi range of 0.00 to 5.00.

    Inserting some data
    ```sql
    INSERT INTO Student (Std_id, Std_name, Std_address, GPA) VALUES
     (1, 'Karim Ahmed',  'Dhanmondi, Dhaka',   5.00),
     (2, 'Rahim Uddin',  'Uttara, Dhaka',      4.50),
     (3, 'Sumi Akter',   'Agrabad, Chattogram',5.00),
     (4, 'Nabil Hasan',  'Zindabazar, Sylhet', 4.25);
    ```

    Part 2 — students who achieved GPA 5
    ```sql
    SELECT  *
    FROM    Student
    WHERE   GPA = 5.00;
    ```

    Output
    ```
    +--------+-------------+---------------------+------+
    | Std_id | Std_name    | Std_address         | GPA  |
    +--------+-------------+---------------------+------+
    |   1    | Karim Ahmed | Dhanmondi, Dhaka    | 5.00 |
    |   3    | Sumi Akter  | Agrabad, Chattogram | 5.00 |
    +--------+-------------+---------------------+------+
    ```

    Related variations
    ```sql
    -- names only
    SELECT Std_name FROM Student WHERE GPA = 5.00;

    -- GPA of 4.5 or above, best first
    SELECT * FROM Student WHERE GPA >= 4.50 ORDER BY GPA DESC;

    -- how many students achieved GPA 5
    SELECT COUNT(*) AS gpa5_holders FROM Student WHERE GPA = 5.00;

    -- average GPA of all students
    SELECT AVG(GPA) AS average_gpa FROM Student;

    -- the highest GPA in the table
    SELECT MAX(GPA) FROM Student;

    -- students with the highest GPA, whatever it happens to be
    SELECT * FROM Student WHERE GPA = (SELECT MAX(GPA) FROM Student);
    ```

    A note on comparing decimals
    - `WHERE GPA = 5.00` is safe here because the column is `DECIMAL`, which stores the value exactly. Had the column been `FLOAT`, an exact equality test could fail because 5.00 might be stored as 4.999999. This is the practical reason for choosing DECIMAL for grades and money.

74. **There is a student table: Student (s_id, name, gender, age, phone, department, cgpa) find a query to get each department maximum CGPA of student. Which student gets highest cgpa in maximum of each department?** *[DESCO Assistant Engineer (CSE) 2019 compact it 1118 (ET: BUET)]*

    Answer:

    Schema
    ```
    Student (s_id, name, gender, age, phone, department, cgpa)
    ```

    Part 1 — the maximum CGPA in each department
    ```sql
    SELECT   department,
             MAX(cgpa) AS highest_cgpa
    FROM     Student
    GROUP BY department;
    ```
    ```
    +------------+--------------+
    | department | highest_cgpa |
    +------------+--------------+
    | CSE        |     3.95     |
    | EEE        |     3.88     |
    | BBA        |     3.75     |
    +------------+--------------+
    ```
    - This gives the value but not the student's name, because a plain column cannot be mixed with an aggregate.

    Part 2 — which student holds the highest CGPA in each department
    ```sql
    SELECT  s.department,
            s.name,
            s.cgpa
    FROM    Student s
    WHERE   s.cgpa = (SELECT MAX(x.cgpa)
                      FROM   Student x
                      WHERE  x.department = s.department)
    ORDER BY s.department;
    ```
    - The subquery is `correlated`: for each student it computes the maximum CGPA of that student's own department, and the row is kept only if it matches.
    - Using `= MAX(...)` returns `all` students who tie for the top place in a department, which is the correct behaviour.

    ```
    +------------+-------+------+
    | department | name  | cgpa |
    +------------+-------+------+
    | CSE        | Karim | 3.95 |
    | EEE        | Sumi  | 3.88 |
    | BBA        | Nabil | 3.75 |
    +------------+-------+------+
    ```

    Derived-table alternative, usually faster
    ```sql
    SELECT s.department, s.name, s.cgpa
    FROM   Student s
    JOIN  (SELECT department, MAX(cgpa) AS max_cgpa
           FROM   Student GROUP BY department) m
      ON   s.department = m.department AND s.cgpa = m.max_cgpa;
    ```
    - The maximums are computed once rather than once per row.

    Window-function version
    ```sql
    SELECT department, name, cgpa FROM (
        SELECT department, name, cgpa,
               RANK() OVER (PARTITION BY department ORDER BY cgpa DESC) AS rnk
        FROM   Student
    ) t
    WHERE rnk = 1;
    ```
    - `RANK()` gives ties the same rank, so every joint topper is returned. `ROW_NUMBER()` would arbitrarily pick one of them, which would be wrong here.

    The mistake to avoid
    ```sql
    -- WRONG: name is not in GROUP BY and is not aggregated
    SELECT department, name, MAX(cgpa) FROM Student GROUP BY department;
    ```
    - Strict SQL rejects this. MySQL in its default mode may accept it and return an `arbitrary` name that need not belong to the top student — which is worse than an error, because the answer looks plausible but is wrong.

75. **Given two tables are employee (id, name, salary, dept_id) and department (dept_id, dept_name), write SQL to find MAX salary and average salay of specific department.** *[DESCO Sub-Assistant Engineer (CSE) 2019 compact it 1121 (ET: BUET)]*

    Answer:

    Schema
    ```
    employee   (id, name, salary, dept_id)
    department (dept_id, dept_name)
    ```

    Maximum and average salary of one specific department
    ```sql
    SELECT  d.dept_name,
            MAX(e.salary) AS max_salary,
            AVG(e.salary) AS avg_salary
    FROM    employee   e
    JOIN    department d ON e.dept_id = d.dept_id
    WHERE   d.dept_name = 'IT'
    GROUP BY d.dept_id, d.dept_name;
    ```
    ```
    +-----------+------------+------------+
    | dept_name | max_salary | avg_salary |
    +-----------+------------+------------+
    | IT        |   90000    |  62500.00  |
    +-----------+------------+------------+
    ```
    - `WHERE` restricts the rows to that department `before` the aggregates are computed, which is exactly right here.

    For every department at once
    ```sql
    SELECT   d.dept_name,
             MAX(e.salary)         AS max_salary,
             ROUND(AVG(e.salary),2) AS avg_salary,
             COUNT(*)              AS employees
    FROM     employee   e
    JOIN     department d ON e.dept_id = d.dept_id
    GROUP BY d.dept_id, d.dept_name
    ORDER BY avg_salary DESC;
    ```
    ```
    +-----------+------------+------------+-----------+
    | dept_name | max_salary | avg_salary | employees |
    +-----------+------------+------------+-----------+
    | IT        |   90000    |  62500.00  |     4     |
    | Accounts  |   70000    |  55000.00  |     2     |
    | HR        |   50000    |  44000.00  |     3     |
    +-----------+------------+------------+-----------+
    ```

    Without the department name, using the id directly
    ```sql
    SELECT MAX(salary) AS max_salary, AVG(salary) AS avg_salary
    FROM   employee
    WHERE  dept_id = 10;
    ```

    Including departments that have no employees
    ```sql
    SELECT   d.dept_name,
             COALESCE(MAX(e.salary), 0) AS max_salary,
             COALESCE(AVG(e.salary), 0) AS avg_salary
    FROM     department d
    LEFT JOIN employee e ON d.dept_id = e.dept_id
    GROUP BY d.dept_id, d.dept_name;
    ```

    Related queries
    ```sql
    -- who actually earns the maximum in the IT department
    SELECT e.name, e.salary
    FROM   employee e JOIN department d ON e.dept_id = d.dept_id
    WHERE  d.dept_name = 'IT'
      AND  e.salary = (SELECT MAX(x.salary) FROM employee x WHERE x.dept_id = e.dept_id);

    -- departments whose average exceeds the company average
    SELECT   d.dept_name, AVG(e.salary) AS avg_salary
    FROM     employee e JOIN department d ON e.dept_id = d.dept_id
    GROUP BY d.dept_id, d.dept_name
    HAVING   AVG(e.salary) > (SELECT AVG(salary) FROM employee);
    ```
    - Note that `AVG` ignores NULL salaries, so the divisor is the count of non-null values rather than the number of employees.

76. **একটি Branch Employee Table; Employee (ID, name, salary); এখন নতুন sub branch তৈরি করার যুক্তিক command লিখুন যার branch name একই হবে এবং Employee এর min ও avg salary বের করুন।** *[NPCBL Junior Technical Engineer 2019 compact it 1148 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.)

    Part 1 — creating the new sub-branch table with the same structure

    The cleanest way — copy the structure only, without the data
    ```sql
    CREATE TABLE Sub_Branch_Employee LIKE Employee;
    ```
    - MySQL syntax. It copies the columns, data types, indexes and constraints, but no rows.

    Copying structure and data together
    ```sql
    CREATE TABLE Sub_Branch_Employee AS
    SELECT * FROM Employee;
    ```
    - Works in MySQL, PostgreSQL and Oracle. It copies the rows as well, but `not` the primary key, indexes or constraints — those must be added afterwards.

    Standard SQL, portable everywhere
    ```sql
    CREATE TABLE Sub_Branch_Employee (
        ID     INT PRIMARY KEY,
        name   VARCHAR(100) NOT NULL,
        salary DECIMAL(10,2) CHECK (salary > 0)
    );
    ```

    Copying only some rows into the new branch
    ```sql
    INSERT INTO Sub_Branch_Employee (ID, name, salary)
    SELECT ID, name, salary FROM Employee WHERE salary < 50000;
    ```

    Part 2 — minimum and average salary
    ```sql
    SELECT  MIN(salary)          AS minimum_salary,
            ROUND(AVG(salary),2) AS average_salary
    FROM    Employee;
    ```

    Output
    ```
    Employee
    +----+-------+--------+
    | ID | name  | salary |
    +----+-------+--------+
    | 1  | Karim | 45000  |
    | 2  | Rahim | 60000  |
    | 3  | Sumi  | 38000  |
    | 4  | Nabil | 52000  |
    +----+-------+--------+

    +----------------+----------------+
    | minimum_salary | average_salary |
    +----------------+----------------+
    |     38000      |    48750.00    |
    +----------------+----------------+
    ```

    For both branches together
    ```sql
    SELECT 'Main Branch' AS branch, MIN(salary), AVG(salary) FROM Employee
    UNION ALL
    SELECT 'Sub Branch',            MIN(salary), AVG(salary) FROM Sub_Branch_Employee;
    ```

    A better design than two separate tables
    - Creating a second table with the same columns duplicates the schema and forces every query to be written twice with `UNION`. The normalised alternative is one table with a `branch` column:
    ```sql
    ALTER TABLE Employee ADD COLUMN branch VARCHAR(50) DEFAULT 'Main';

    SELECT   branch, MIN(salary) AS minimum, AVG(salary) AS average, COUNT(*) AS staff
    FROM     Employee
    GROUP BY branch;
    ```
    - One table, one query, and adding a third branch requires no schema change at all. This is the answer an examiner is looking for when the question mentions "same branch name".

    Related aggregates
    ```sql
    SELECT MIN(salary), MAX(salary), AVG(salary), SUM(salary), COUNT(*) FROM Employee;

    -- the employee who actually earns the minimum
    SELECT * FROM Employee WHERE salary = (SELECT MIN(salary) FROM Employee);
    ```

77. **Write an SQL Query for 2nd highest score for the table T.** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1152 (ET: KUET)]*

    Answer: The second highest value is the maximum of everything below the maximum.

    Method 1 — nested MAX, the classic answer
    ```sql
    SELECT MAX(score) AS second_highest
    FROM   T
    WHERE  score < (SELECT MAX(score) FROM T);
    ```
    - The subquery finds the highest score; the outer query then finds the highest score strictly below it.
    - Duplicates cause no problem: if three students share the top score, they are all excluded by `<`, and the genuine second distinct value is returned.
    - If there is no second value, it returns `NULL` rather than an error, which is usually the desired behaviour.

    Method 2 — LIMIT with OFFSET
    ```sql
    SELECT DISTINCT score
    FROM   T
    ORDER  BY score DESC
    LIMIT  1 OFFSET 1;
    ```
    - `DISTINCT` is essential. Without it, a tie for first place would make the second row still be the top score.
    - `LIMIT 1 OFFSET 1` skips the first row and takes the next. Oracle uses `OFFSET 1 ROWS FETCH NEXT 1 ROWS ONLY`; SQL Server uses `OFFSET 1 ROWS FETCH NEXT 1 ROWS ONLY` as well.

    Method 3 — DENSE_RANK, the general solution for the Nth highest
    ```sql
    SELECT DISTINCT score FROM (
        SELECT score, DENSE_RANK() OVER (ORDER BY score DESC) AS rnk
        FROM   T
    ) t
    WHERE rnk = 2;
    ```
    - Changing `rnk = 2` to `rnk = N` gives the Nth highest, which is why this is the version worth remembering.
    - `DENSE_RANK` is correct here rather than `RANK`: with scores 95, 95, 90, RANK assigns 1, 1, 3 and no row has rank 2 at all, whereas DENSE_RANK assigns 1, 1, 2 and correctly returns 90.

    Method 4 — correlated subquery counting how many are higher
    ```sql
    SELECT score FROM T t1
    WHERE  1 = (SELECT COUNT(DISTINCT t2.score) FROM T t2 WHERE t2.score > t1.score);
    ```
    - Reads as: exactly one distinct score is higher than this one.

    Worked example
    ```
    T
    +----+-------+
    | id | score |
    +----+-------+
    | 1  |  95   |
    | 2  |  95   |
    | 3  |  88   |
    | 4  |  76   |
    +----+-------+

    Highest        = 95
    Second highest = 88     (not 95, because the duplicate must not count)
    ```

    Comparison

    | Method | Handles ties | Portable | Extends to Nth |
    |---|---|---|---|
    | Nested MAX | Yes | Everywhere | Awkward |
    | LIMIT / OFFSET with DISTINCT | Yes | Syntax differs by system | Easily, change the OFFSET |
    | DENSE_RANK | Yes | Modern systems only | `Best` — change one number |
    | Correlated COUNT | Yes | Everywhere | Change the count |

78. **Write the SQL from employee table where average salary of all employee is greater than the salary of each department. Employee (emp_Id, emp_name, salary, city, dept_name).** *[Dutch Bangla Bank Assistant Network/Hardware Engineer 2019 compact it 1161 (ET: BUET)]*

    Answer: The wording is ambiguous, so both readings are given. The natural database reading is: find the departments whose average salary is `below` the overall average of all employees.

    Reading 1 — departments below the company average, with their employees
    ```sql
    SELECT  e.emp_Id, e.emp_name, e.salary, e.dept_name
    FROM    Employee e
    WHERE   e.dept_name IN (
                SELECT   dept_name
                FROM     Employee
                GROUP BY dept_name
                HAVING   AVG(salary) < (SELECT AVG(salary) FROM Employee)
            );
    ```

    Reading 2 — just the departments and their averages
    ```sql
    SELECT   dept_name,
             AVG(salary) AS dept_average
    FROM     Employee
    GROUP BY dept_name
    HAVING   AVG(salary) < (SELECT AVG(salary) FROM Employee);
    ```

    Worked example
    ```
    Employee
    +--------+----------+--------+-----------+
    | emp_Id | emp_name | salary | dept_name |
    +--------+----------+--------+-----------+
    |   1    | Karim    | 80000  | IT        |
    |   2    | Rahim    | 70000  | IT        |
    |   3    | Sumi     | 40000  | HR        |
    |   4    | Nabil    | 30000  | HR        |
    |   5    | Jamil    | 50000  | Accounts  |
    +--------+----------+--------+-----------+

    Company average = 270000 / 5 = 54000
    Department averages: IT 75000 ; HR 35000 ; Accounts 50000

    Departments below 54000: HR (35000), Accounts (50000)

    Result (reading 1)
    +--------+----------+--------+-----------+
    | emp_Id | emp_name | salary | dept_name |
    +--------+----------+--------+-----------+
    |   3    | Sumi     | 40000  | HR        |
    |   4    | Nabil    | 30000  | HR        |
    |   5    | Jamil    | 50000  | Accounts  |
    +--------+----------+--------+-----------+
    ```

    Reading 3 — individual employees earning less than the company average
    ```sql
    SELECT emp_Id, emp_name, salary, dept_name
    FROM   Employee
    WHERE  salary < (SELECT AVG(salary) FROM Employee);
    ```

    Reading 4 — comparing against the average of the department averages
    - If "the average salary of all employees" is meant as the mean of the departmental means, every department counts equally regardless of size:
    ```sql
    SELECT   dept_name, AVG(salary) AS dept_average
    FROM     Employee
    GROUP BY dept_name
    HAVING   AVG(salary) < (
                SELECT AVG(d_avg) FROM (
                    SELECT AVG(salary) AS d_avg FROM Employee GROUP BY dept_name
                ) t
             );
    ```
    - The two figures differ whenever departments are of different sizes: here the employee average is 54000 but the average of the three department averages is (75000 + 35000 + 50000)/3 = 53333.

    The technical point being tested
    - A condition on an aggregate must go in `HAVING`, never in `WHERE`, because SQL evaluates `FROM -> WHERE -> GROUP BY -> HAVING -> SELECT`. At the time WHERE runs, the groups and their averages do not yet exist.

79. **Write a query to select top 10% row from grade table.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1162 (ET: N/A)]*

    Answer: "Top 10 percent" means a fraction of the row count, which varies with the size of the table, so the number cannot simply be hard-coded.

    Method 1 — LIMIT with a computed count (MySQL 8, PostgreSQL)
    ```sql
    SELECT *
    FROM   grade
    ORDER  BY marks DESC
    LIMIT  (SELECT CEIL(COUNT(*) * 0.10) FROM grade);
    ```
    - `CEIL` rounds up, so a table of 45 rows yields 5 rows rather than 4.

    Method 2 — PERCENT_RANK, the cleanest modern form
    ```sql
    SELECT * FROM (
        SELECT g.*, PERCENT_RANK() OVER (ORDER BY marks DESC) AS pr
        FROM   grade g
    ) t
    WHERE pr <= 0.10;
    ```
    - `PERCENT_RANK()` returns a value between 0 and 1 giving each row's relative position, so `<= 0.10` is exactly the top tenth. Ties are handled correctly, because equal marks receive the same value.

    Method 3 — NTILE, dividing the table into ten equal bands
    ```sql
    SELECT * FROM (
        SELECT g.*, NTILE(10) OVER (ORDER BY marks DESC) AS band
        FROM   grade g
    ) t
    WHERE band = 1;
    ```

    Method 4 — SQL Server's built-in syntax
    ```sql
    SELECT TOP 10 PERCENT *
    FROM   grade
    ORDER  BY marks DESC;
    ```
    - Add `WITH TIES` to include every row that ties with the last one.

    Method 5 — Oracle
    ```sql
    SELECT * FROM (
        SELECT g.*, ROW_NUMBER() OVER (ORDER BY marks DESC) AS rn,
                    COUNT(*) OVER () AS total
        FROM   grade g
    )
    WHERE rn <= CEIL(total * 0.10);
    ```

    Method 6 — portable, without window functions
    ```sql
    SELECT g.*
    FROM   grade g
    WHERE  (SELECT COUNT(*) FROM grade x WHERE x.marks > g.marks)
           < (SELECT COUNT(*) * 0.10 FROM grade);
    ```
    - Reads as: a row is in the top 10 percent when fewer than 10 percent of all rows score higher.

    Top 10 percent `within each department`
    ```sql
    SELECT * FROM (
        SELECT g.*,
               PERCENT_RANK() OVER (PARTITION BY department ORDER BY marks DESC) AS pr
        FROM   grade g
    ) t
    WHERE pr <= 0.10
    ORDER BY department, marks DESC;
    ```

    Points to be careful about
    - `LIMIT 10` is not the same as "top 10 percent" — the first is a fixed count, the second a proportion.
    - Ties at the cut-off must be decided deliberately. `PERCENT_RANK` and `RANK` keep all tied rows; `ROW_NUMBER` cuts arbitrarily between equal scores.
    - Rounding matters: `CEIL` includes the partial row, `FLOOR` excludes it. `CEIL` is the usual choice so that a small table still returns at least one row.

80. **Three table are given: Customer (cust_id, Name, Address, Sales_id), Order (Order_id, cust_id, Date, sales_id), Salesman (Sales_id, commission)** *[Palli Sanchay Bank Assistant Database Administrator 2018 compact it 1170 (ET: N/A)]*
   (i) Find the customer details for those salesman get commission greater than 12% commission.
   (ii) Count the salesman by their order_id and date.

    Answer:

    Schema
    ```
    Customer (cust_id, Name, Address, Sales_id)
    Order    (Order_id, cust_id, Date, sales_id)
    Salesman (Sales_id, commission)
    ```
    - Note that `Order` is a reserved word in SQL, so it must be quoted — backticks in MySQL, double quotes in standard SQL — or the table renamed to `Orders`.

    (i) Customer details where the salesman's commission exceeds 12 percent
    ```sql
    SELECT  c.cust_id,
            c.Name,
            c.Address,
            s.Sales_id,
            s.commission
    FROM    Customer c
    JOIN    Salesman s ON c.Sales_id = s.Sales_id
    WHERE   s.commission > 0.12;
    ```
    - The threshold depends on how commission is stored. If it is a fraction, `> 0.12` is correct; if it is a whole-number percentage, use `> 12`:
    ```sql
    WHERE s.commission > 12;
    ```
    - This ambiguity is worth stating explicitly, since both conventions occur.

    Sample output
    ```
    +---------+-------+----------+----------+------------+
    | cust_id | Name  | Address  | Sales_id | commission |
    +---------+-------+----------+----------+------------+
    |  1001   | Karim | Dhaka    |   S01    |    0.15    |
    |  1003   | Sumi  | Khulna   |   S03    |    0.20    |
    +---------+-------+----------+----------+------------+
    ```

    (ii) Count the salesmen by their order id and date
    ```sql
    SELECT   o.sales_id,
             o.Date,
             COUNT(o.Order_id) AS total_orders
    FROM     `Order` o
    GROUP BY o.sales_id, o.Date
    ORDER BY o.sales_id, o.Date;
    ```
    - Grouping by both columns produces one row per salesman per day, with the number of orders taken.

    Sample output
    ```
    +----------+------------+--------------+
    | sales_id | Date       | total_orders |
    +----------+------------+--------------+
    |   S01    | 2018-03-01 |      3       |
    |   S01    | 2018-03-02 |      1       |
    |   S02    | 2018-03-01 |      2       |
    +----------+------------+--------------+
    ```

    If the intent is the number of `distinct salesmen` per date
    ```sql
    SELECT   o.Date, COUNT(DISTINCT o.sales_id) AS salesmen
    FROM     `Order` o
    GROUP BY o.Date;
    ```

    Related useful queries
    ```sql
    -- orders per salesman, with the commission rate
    SELECT   s.Sales_id, s.commission, COUNT(o.Order_id) AS orders
    FROM     Salesman s
    LEFT JOIN `Order` o ON s.Sales_id = o.sales_id
    GROUP BY s.Sales_id, s.commission;

    -- customers who have never placed an order
    SELECT c.Name FROM Customer c
    LEFT JOIN `Order` o ON c.cust_id = o.cust_id
    WHERE  o.Order_id IS NULL;

    -- the salesman handling the most customers
    SELECT   Sales_id, COUNT(*) AS customers FROM Customer
    GROUP BY Sales_id ORDER BY customers DESC LIMIT 1;
    ```
    - Design note: `sales_id` appears in both `Customer` and `Order`, which duplicates the relationship and risks the two disagreeing. A normalised design would keep it in only one place.

81. **Suppose you've two table (Employee, Department) in a Database and Employee table three cell (emp_name, dept_id, salary) also Department table two cell (dept_id, dept_name), now update the salary 10% increase value from Department table. Give the appropriate example.** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1175 (ET: N/A)]*

    Answer: The salary lives in `Employee`, but the department must be identified through `Department`, so a join is needed inside the UPDATE.

    MySQL — UPDATE with a JOIN
    ```sql
    UPDATE  Employee e
    JOIN    Department d ON e.dept_id = d.dept_id
    SET     e.salary = e.salary * 1.10
    WHERE   d.dept_name = 'IT';
    ```

    Standard SQL — UPDATE with a subquery, portable to Oracle and others
    ```sql
    UPDATE  Employee
    SET     salary = salary * 1.10
    WHERE   dept_id IN (
                SELECT dept_id FROM Department WHERE dept_name = 'IT'
            );
    ```

    PostgreSQL — UPDATE ... FROM
    ```sql
    UPDATE Employee e
    SET    salary = e.salary * 1.10
    FROM   Department d
    WHERE  e.dept_id = d.dept_id
      AND  d.dept_name = 'IT';
    ```

    SQL Server
    ```sql
    UPDATE e
    SET    e.salary = e.salary * 1.10
    FROM   Employee e
    JOIN   Department d ON e.dept_id = d.dept_id
    WHERE  d.dept_name = 'IT';
    ```

    Worked example
    ```
    Before
    +----------+---------+--------+          Department
    | emp_name | dept_id | salary |          +---------+-----------+
    +----------+---------+--------+          | dept_id | dept_name |
    | Karim    |   10    | 50000  |          +---------+-----------+
    | Rahim    |   10    | 60000  |          |   10    | IT        |
    | Sumi     |   20    | 40000  |          |   20    | HR        |
    +----------+---------+--------+          +---------+-----------+

    After the 10 percent raise for IT
    +----------+---------+--------+
    | emp_name | dept_id | salary |
    +----------+---------+--------+
    | Karim    |   10    | 55000  |    <- 50000 × 1.10
    | Rahim    |   10    | 66000  |    <- 60000 × 1.10
    | Sumi     |   20    | 40000  |    <- unchanged
    +----------+---------+--------+
    ```

    Raising every department by 10 percent
    ```sql
    UPDATE Employee SET salary = salary * 1.10;
    ```

    Different raises for different departments, using CASE
    ```sql
    UPDATE Employee e
    JOIN   Department d ON e.dept_id = d.dept_id
    SET    e.salary = e.salary * CASE d.dept_name
                                    WHEN 'IT' THEN 1.10
                                    WHEN 'HR' THEN 1.05
                                    ELSE 1.00
                                 END;
    ```

    Safe practice
    ```sql
    -- 1. check which rows will be affected
    SELECT e.emp_name, e.salary, e.salary * 1.10 AS new_salary
    FROM   Employee e JOIN Department d ON e.dept_id = d.dept_id
    WHERE  d.dept_name = 'IT';

    -- 2. run inside a transaction so it can be undone
    BEGIN;
    UPDATE Employee e JOIN Department d ON e.dept_id = d.dept_id
    SET    e.salary = e.salary * 1.10 WHERE d.dept_name = 'IT';
    SELECT * FROM Employee;          -- verify
    COMMIT;                          -- or ROLLBACK
    ```
    - The `WHERE` clause is the critical part. Omitting it would give every employee in the company the raise, and without a transaction there would be no way back.
    - `salary * 1.10` is preferred to `salary + salary * 0.10` — shorter and less error-prone, though both are correct.

82. **What is the SQL query for showing only the duplicate lists in student (id, name, gpa) table?** *[Agrani Bank Ltd. Officer (ICT) 2017 compact it 1223 (ET: N/A)]*

    Answer: Duplicate rows are found by grouping on the columns that define a duplicate and keeping only the groups with a count above one.

    Duplicates by name
    ```sql
    SELECT   name,
             COUNT(*) AS occurrences
    FROM     student
    GROUP BY name
    HAVING   COUNT(*) > 1;
    ```

    Duplicates on both name and GPA
    ```sql
    SELECT   name, gpa, COUNT(*) AS occurrences
    FROM     student
    GROUP BY name, gpa
    HAVING   COUNT(*) > 1;
    ```
    - The columns in `GROUP BY` define what counts as a duplicate. `id` must be excluded, since it is unique by definition and would make every group size 1.

    Showing the full rows of every duplicated student
    ```sql
    SELECT *
    FROM   student
    WHERE  name IN (SELECT name FROM student GROUP BY name HAVING COUNT(*) > 1)
    ORDER  BY name, id;
    ```

    Sample data and output
    ```
    student
    +----+-------+------+
    | id | name  | gpa  |
    +----+-------+------+
    | 1  | Karim | 3.50 |
    | 2  | Rahim | 3.75 |
    | 3  | Karim | 3.50 |
    | 4  | Sumi  | 3.20 |
    | 5  | Rahim | 3.90 |
    | 6  | Karim | 3.50 |
    +----+-------+------+

    Grouped by name
    +-------+-------------+
    | name  | occurrences |
    +-------+-------------+
    | Karim |      3      |
    | Rahim |      2      |
    +-------+-------------+

    Grouped by name and gpa
    +-------+------+-------------+
    | name  | gpa  | occurrences |
    +-------+------+-------------+
    | Karim | 3.50 |      3      |
    +-------+------+-------------+
    ```
    - Rahim appears in the first result but not the second, because his two rows have different GPAs. This shows why the choice of grouping columns matters.

    Self-join alternative
    ```sql
    SELECT DISTINCT s1.*
    FROM   student s1
    JOIN   student s2 ON s1.name = s2.name AND s1.id <> s2.id;
    ```

    Window-function alternative, which also identifies the extra copies
    ```sql
    SELECT * FROM (
        SELECT s.*, COUNT(*) OVER (PARTITION BY name, gpa) AS cnt,
                    ROW_NUMBER() OVER (PARTITION BY name, gpa ORDER BY id) AS rn
        FROM   student s
    ) t
    WHERE cnt > 1;
    ```
    - Rows with `rn > 1` are precisely the ones to delete if the duplicates are to be cleaned up.

    Deleting the duplicates, keeping the lowest id
    ```sql
    DELETE FROM student
    WHERE  id NOT IN (SELECT keep FROM
            (SELECT MIN(id) AS keep FROM student GROUP BY name, gpa) AS t);
    ```
    - Preventing the problem is better than curing it:
    ```sql
    ALTER TABLE student ADD CONSTRAINT uq_student UNIQUE (name, gpa);
    ```

83. **Given a database table with some column** *[BTCL Assistant Manager (Technical) 2017 compact it 1256 (ET: N/A)]*
   a. find out the min salary from table
   b. find out a matched string

    Answer: The table was not printed, so a standard `Employee(emp_id, emp_name, salary, city, designation)` is assumed.

    (a) Minimum salary from the table
    ```sql
    SELECT MIN(salary) AS minimum_salary
    FROM   Employee;
    ```
    - `MIN()` is an aggregate function that returns the smallest value of a column. It ignores NULLs, and without a `GROUP BY` it treats the whole table as one group, so exactly one row is returned.

    To see `who` earns that minimum, the value must be found first and then matched
    ```sql
    SELECT *
    FROM   Employee
    WHERE  salary = (SELECT MIN(salary) FROM Employee);
    ```
    - Using `= (SELECT MIN(...))` returns `all` employees who tie at the lowest salary, which `ORDER BY salary LIMIT 1` would not.

    Minimum per department
    ```sql
    SELECT   dept_name, MIN(salary) AS minimum_salary
    FROM     Employee
    GROUP BY dept_name;
    ```

    The mistake to avoid
    ```sql
    -- WRONG: emp_name is neither grouped nor aggregated
    SELECT emp_name, MIN(salary) FROM Employee;
    ```
    - Strict SQL rejects this. MySQL in its default mode may accept it and return an `arbitrary` name that need not belong to the lowest-paid employee — worse than an error, because the result looks plausible.

    (b) Finding a matched string
    - Exact match, when the whole value is known:
    ```sql
    SELECT * FROM Employee WHERE emp_name = 'Karim';
    ```
    - Pattern match, when only part is known, using `LIKE` with its two wildcards (`%` any sequence, `_` exactly one character):
    ```sql
    SELECT * FROM Employee WHERE emp_name LIKE 'Kar%';   -- starts with Kar
    SELECT * FROM Employee WHERE emp_name LIKE '%im';    -- ends with im
    SELECT * FROM Employee WHERE emp_name LIKE '%ah%';   -- contains ah
    SELECT * FROM Employee WHERE emp_name LIKE '_a%';    -- second letter is a
    SELECT * FROM Employee WHERE emp_name LIKE '_____';  -- exactly 5 characters
    SELECT * FROM Employee WHERE emp_name NOT LIKE 'A%'; -- does not start with A
    ```

    | Pattern | Matches |
    |---|---|
    | `'a%'` | Starts with a |
    | `'%a'` | Ends with a |
    | `'%a%'` | Contains a anywhere |
    | `'_a%'` | Second character is a |
    | `'a_c'` | Three characters, a then anything then c |

    Points worth remembering
    - A `leading` wildcard, as in `LIKE '%im'`, prevents an index on the column from being used and forces a full table scan. `LIKE 'Kar%'` can still use an index because the prefix is fixed.
    - Case sensitivity depends on the column's collation, not on the operator. MySQL's default collation is case-insensitive; PostgreSQL is case-sensitive and provides `ILIKE`.
    - To search for a literal `%` or `_`, escape it: `WHERE code LIKE '50\%%' ESCAPE '\'`.

84. **Probably a SQL query** *[BTCL Assistant Manager (Technical) 2017 compact it 1256 (ET: N/A)]*
   (a) Show the branch name with the minimum balance
   (b) Select all dept_name, roll from Student

    Answer:

    (a) Branch name with the minimum balance
    ```sql
    SELECT  branch_name, balance
    FROM    Account
    WHERE   balance = (SELECT MIN(balance) FROM Account);
    ```
    - The subquery finds the smallest balance in the table; the outer query returns the branch or branches holding it.
    - Using `= (SELECT MIN(...))` correctly returns `all` branches if several tie at the lowest balance.

    Shorter alternative
    ```sql
    SELECT branch_name, balance
    FROM   Account
    ORDER  BY balance ASC
    LIMIT  1;
    ```
    - Simpler, but returns only `one` row even when there is a tie, so it is not strictly equivalent.

    If the balance is a total held per branch
    ```sql
    SELECT   branch_name, SUM(balance) AS total_balance
    FROM     Account
    GROUP BY branch_name
    ORDER BY total_balance ASC
    LIMIT 1;
    ```
    - Here the branch with the smallest total deposits is wanted, so the balances must be summed per branch first.

    Sample output
    ```
    Account
    +---------+-------------+---------+
    | acc_no  | branch_name | balance |
    +---------+-------------+---------+
    |  A101   | Dhanmondi   |  50000  |
    |  A102   | Uttara      |  12000  |
    |  A103   | Gulshan     |  75000  |
    |  A104   | Uttara      |  30000  |
    +---------+-------------+---------+

    (a) minimum single balance -> Uttara, 12000
    per-branch totals: Dhanmondi 50000, Uttara 42000, Gulshan 75000
        -> smallest total is Uttara, 42000
    ```

    (b) All dept_name and roll from Student
    ```sql
    SELECT  dept_name, roll
    FROM    Student;
    ```
    - Only the two requested columns are listed, so `SELECT *` would be wrong.

    Common refinements
    ```sql
    -- unique department and roll combinations
    SELECT DISTINCT dept_name, roll FROM Student;

    -- just the list of departments
    SELECT DISTINCT dept_name FROM Student;

    -- sorted by department, then by roll
    SELECT dept_name, roll FROM Student ORDER BY dept_name, roll;

    -- one department only
    SELECT dept_name, roll FROM Student WHERE dept_name = 'CSE';

    -- how many students in each department
    SELECT   dept_name, COUNT(roll) AS students
    FROM     Student
    GROUP BY dept_name;
    ```
    - Note that `DISTINCT` applies to the whole selected row, not to a single column: `SELECT DISTINCT dept_name, roll` removes duplicate `pairs`, which for a unique roll number removes nothing at all.

85. **Write a SQL query to get second highest salary from Employee table.** *[BCC Assistant Programmer 2017 compact it 1257 (ET: N/A)]*

    Answer: The second highest salary is the maximum of everything strictly below the maximum.

    Method 1 — nested MAX, the classic answer
    ```sql
    SELECT MAX(salary) AS second_highest_salary
    FROM   Employee
    WHERE  salary < (SELECT MAX(salary) FROM Employee);
    ```
    - The subquery finds the highest salary; the outer query finds the highest value below it.
    - Duplicates cause no problem: if three employees share the top salary, `<` excludes all of them and the genuine second distinct salary is returned.
    - If no second salary exists, it returns `NULL` rather than raising an error.

    Method 2 — LIMIT with OFFSET
    ```sql
    SELECT DISTINCT salary
    FROM   Employee
    ORDER  BY salary DESC
    LIMIT  1 OFFSET 1;
    ```
    - `DISTINCT` is essential. Without it, a tie for first place would leave the second row still holding the top salary.
    - Oracle and SQL Server use `OFFSET 1 ROWS FETCH NEXT 1 ROWS ONLY`.

    Method 3 — DENSE_RANK, the general Nth-highest solution
    ```sql
    SELECT DISTINCT salary FROM (
        SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
        FROM   Employee
    ) t
    WHERE rnk = 2;
    ```
    - Changing `rnk = 2` to `rnk = N` gives the Nth highest, which is why this version is worth memorising.
    - `DENSE_RANK` rather than `RANK`: with salaries 95000, 95000, 90000, RANK assigns 1, 1, 3 and no row has rank 2 at all, whereas DENSE_RANK assigns 1, 1, 2 and correctly returns 90000.

    Method 4 — correlated subquery
    ```sql
    SELECT salary FROM Employee e1
    WHERE  1 = (SELECT COUNT(DISTINCT e2.salary) FROM Employee e2 WHERE e2.salary > e1.salary);
    ```
    - Reads as: exactly one distinct salary is higher than this one.

    To return the employee as well as the amount
    ```sql
    SELECT emp_name, salary
    FROM   Employee
    WHERE  salary = (SELECT MAX(salary) FROM Employee
                     WHERE salary < (SELECT MAX(salary) FROM Employee));
    ```

    Worked example
    ```
    Employee salaries: 90000, 90000, 75000, 60000

    Highest        = 90000
    Second highest = 75000   (not 90000 — the duplicate must not count)
    ```

    Comparison

    | Method | Handles ties | Portable | Extends to Nth |
    |---|---|---|---|
    | Nested MAX | Yes | Everywhere | Awkward |
    | DISTINCT with LIMIT/OFFSET | Yes | Syntax varies | Easily |
    | `DENSE_RANK` | Yes | Modern systems | `Best` |
    | Correlated COUNT | Yes | Everywhere | Change the count |

86. **Which modifier should be used to remove duplicate rows in SQL query?** *[DESCO Assistant Engineer (CSE) 2016 compact it 1266 (ET: N/A)]*

    Answer: The modifier used to remove duplicate rows is `DISTINCT`.

    - It is placed immediately after `SELECT` and eliminates duplicate rows from the result set, returning only unique combinations of the selected columns.

    ```sql
    SELECT DISTINCT department FROM Employee;
    ```

    Example
    ```
    Employee
    +--------+----------+------------+
    | emp_id | emp_name | department |
    +--------+----------+------------+
    |   1    | Karim    | IT         |
    |   2    | Rahim    | HR         |
    |   3    | Sumi     | IT         |
    |   4    | Nabil    | Accounts   |
    |   5    | Jamil    | HR         |
    +--------+----------+------------+

    SELECT department FROM Employee;            SELECT DISTINCT department FROM Employee;
    +------------+                              +------------+
    | IT         |                              | IT         |
    | HR         |                              | HR         |
    | IT         |                              | Accounts   |
    | Accounts   |                              +------------+
    | HR         |                                  3 rows
    +------------+
        5 rows
    ```

    The important rule about several columns
    ```sql
    SELECT DISTINCT department, designation FROM Employee;
    ```
    - `DISTINCT` applies to the `entire selected row`, not to one column. This returns unique `combinations` of department and designation, so IT/Manager and IT/Developer are both kept.
    - Writing `SELECT DISTINCT(department), designation` does not change this — the parentheses are cosmetic and the DISTINCT still covers both columns. That is a frequent misunderstanding.

    Related uses
    ```sql
    -- count the distinct values
    SELECT COUNT(DISTINCT department) FROM Employee;

    -- distinct values inside an aggregate
    SELECT SUM(DISTINCT salary) FROM Employee;

    -- UNION removes duplicates automatically; UNION ALL keeps them
    SELECT name FROM TableA UNION     SELECT name FROM TableB;   -- de-duplicated
    SELECT name FROM TableA UNION ALL SELECT name FROM TableB;   -- duplicates kept
    ```

    Points worth knowing
    - The opposite of `DISTINCT` is `ALL`, which is the default and need not be written: `SELECT ALL department` is identical to `SELECT department`.
    - `DISTINCT` treats all NULLs as equal to one another, so a column containing several NULLs yields a single NULL row.
    - It has a performance cost, because the database must sort or hash the result to detect duplicates. If duplicates arise from a badly written join, fixing the join is better than masking the problem with DISTINCT.
    - `GROUP BY department` produces the same rows as `SELECT DISTINCT department`, but GROUP BY is intended for aggregation and DISTINCT for de-duplication.

87. **What dose following query do?** *[DESCO Assistant Engineer (CSE) 2016 compact it 1267 (ET: N/A)]*
```sql
SELECT *FROM students ORDER BY ID, NAME DESC
```

    Answer:

    The query
    ```sql
    SELECT * FROM students ORDER BY ID, NAME DESC;
    ```

    What it does
    - It retrieves `every column and every row` from the `students` table, and sorts the result by `ID ascending` first, and then by `NAME descending` within each equal ID.

    The critical detail
    - `DESC` applies only to the column immediately before it. Since no keyword follows `ID`, that column uses the default, which is `ASC`.
    ```sql
    ORDER BY ID, NAME DESC        is identical to        ORDER BY ID ASC, NAME DESC
    ```
    - To sort both columns descending, `DESC` must be repeated:
    ```sql
    ORDER BY ID DESC, NAME DESC
    ```
    - This is the single point the question is testing, and the most common mistake is to assume `DESC` applies to the whole list.

    How multi-column sorting works
    - The rows are ordered by the first column. Only where two rows share the same value in that column does the second column decide the order between them.

    Worked example
    ```
    students
    +----+---------+-------+
    | ID | NAME    | Marks |
    +----+---------+-------+
    | 2  | Zara    |  80   |
    | 1  | Karim   |  75   |
    | 2  | Amina   |  90   |
    | 1  | Sumi    |  85   |
    | 3  | Nabil   |  70   |
    +----+---------+-------+

    Result of  ORDER BY ID, NAME DESC
    +----+---------+-------+
    | ID | NAME    | Marks |
    +----+---------+-------+
    | 1  | Sumi    |  85   |    <- ID 1 group, NAME descending: Sumi before Karim
    | 1  | Karim   |  75   |
    | 2  | Zara    |  80   |    <- ID 2 group, NAME descending: Zara before Amina
    | 2  | Amina   |  90   |
    | 3  | Nabil   |  70   |
    +----+---------+-------+
    ```
    - The IDs run 1, 2, 3 in ascending order, while the names inside each ID group run in reverse alphabetical order.

    Related points
    - Since `ID` is normally a primary key, it is unique, so in a real table the `NAME DESC` part would never actually take effect — a detail worth noting when the question uses an id column.
    - `ORDER BY` is the `last` clause evaluated, after `SELECT`, which is why a column alias defined in the SELECT list may be used in it.
    - Sorting by column position is also legal but discouraged: `ORDER BY 1, 2 DESC` means the first and second selected columns.
    - NULL ordering differs by system: MySQL and PostgreSQL place NULLs first in ascending order by default, Oracle places them last. `NULLS FIRST` or `NULLS LAST` makes it explicit where supported.

## Keys in DBMS (34)

1. Difference Between Primary Key, Foreign Key, Candidate Key. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

2. **(a) Define RDBMS. Explain the different key and primary key, candidate key, super key, and foreign key DBMS.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1445 (ET: N/A)]*

3. **Difference between primary key, foreign key? What is trigger?** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 502 (ET: N/A)]*

4. **Define primary key, super key, and Candidate key.** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*

5. **What is primary key and foreign key with example?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 499 (ET: N/A)]*

6. **Explain Primary key, Candidate key, and Foreign key.** *[Teletalk Assistant Manager (IT) 2023 compact it 468 (ET: N/A)]*

7. **(খ) Primary key এবং Super key এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 625 (ET: N/A)]*

8. **Super key and Candidate key finding from table.** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 648 (ET: BUET)]*

9. **From Functional Dependency for determine candidate key.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 661 (ET: N/A)]*

10. **Relation to find primary key, candidate key, super key.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 663 (ET: N/A)]*

11. **(a) Differentiate among foreign key, candidate key, and primary key.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 694 (ET: N/A)]*

12. **Explain the primary key and composite key with respect to database.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 745 (ET: N/A)]*

13. **(খ) Relational Database Design এ Primary Key ও Foreign Key বলতে কি বুঝায়? উদাহরণসহ লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 769 (ET: N/A)]*

14. **(b) What are purpose of using foreign key in a database? Give suitable example.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 802 (ET: N/A)]*

15. **What is primary key?** *[BCC CA Monitoring System Project 2021 compact it 829 (ET: N/A)]*

16. **What is Primary key, Unique key and Forgein key.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*

17. **Database Management System (DBMS) বলতে কী বোঝেন? Relational database -এ Primary key এবং Foreign key -এর ভূমিকা উদাহরণসহ সংক্ষেপে বর্ণনা করুন?** *[41th BCS 2021 compact it 882 (ET: N/A)]*

18. **(b) Explain the different type of database keys with examples.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)]*

19. **What is the Primary key, Candidate key and Super key?** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 921 (ET: N/A)]*

20. **Difference between Primary key and Unique Key, Drop and Purge, Delete and Truncate.** *[RAKUB Assistant Database Administrator 2020 compact it 1013-1014 (ET: E-Zone)]*

21. **Example Foreign key in RDBMS.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1035 (ET: BUET)]*

22. **What is the difference between primary key and candidate key? Explain the foreign key with an example.** *[Bangladesh Competition Commission Programmer 2019 compact it 1061-1062 (ET: DU)]*

23. **(খ) Candidate key and Composite key কাকে বলে?** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1069 (ET: N/A)]*

24. **(b) What happens when someone tries to delete an entry of a table that has referential integrity constraint? Explain with example.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1136-1138 (ET: N/A)]*

25. **What is foreign key? When foreign key used?** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1152 (ET: KUET)]*

26. **Difference between primary key, foreign key and candidate key.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1162 (ET: N/A)]*

27. **Define weak Entity? What are the difference between primary key and super key?** *[Palli Sanchay Bank Programmer 2018 compact it 1171 (ET: N/A)]*

28. **Difference between Super Key and UNIQUE key?** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1174 (ET: N/A)]*

29. **Define Super key and Primary key.** *[Jiban Bima Corporation Assistant Programmer 2018 compact it 1211 (ET: N/A)]*

30. **What are the difference among Candidate key, Primary key and Foreign key?** *[Investment Corporation Bangladesh Assistant Programmer 2017 compact it 1216 (ET: N/A)]*

31. **Explain with examples: Candidate key, foreign key and horizontal scaling.** *[Agrani Bank Ltd. Senior Officer (IT) 2017 compact it 1223 (ET: N/A)]*

32. **Write down the differences between super key and candidate key with example.** *[Agrani Bank Ltd. Officer (ICT) 2017 compact it 1225 (ET: N/A)]*

33. **What do you mean by primary key and foreign key?** *[Multiple Ministry Assistant Programmer 2017 compact it 1230 (ET: N/A)]*

**Table Name: STUDENT**

| Stu_Id | Stu_Name | Stu_Age |
|---|---|---|
| 101 | Steve | 23 |
| 102 | John | 24 |
| 103 | Robert | 28 |
| 104 | Steve | 29 |

**Course_enrollment table:**

| Course_Id | Stu_Id |
|---|---|
| C01 | 101 |
| C02 | 102 |
| C03 | 101 |
| C05 | 102 |
| C06 | 103 |
| C07 | 102 |

34. **Define ‘integrity rules’ of database systems. Write a SQL query to get the second highest salary from Employee table.** *[Bangladesh Bank Assistant Programmer 2016 compact it 1265 (ET: N/A)]*

## DBMS Architecture & Features (26)

1. (a) DBMS এর মূল বৈশিষ্ট্য লিখুন।
   (b) HTTP ও HTTPS প্রোটোকলের মধ্যে সুরক্ষার দিক থেকে পার্থক্য ব্যাখ্যা করুন। *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

2. **ODBC এর পূর্ণ রূপ কি?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

3. **Data about data is Called __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

4. **Difference between MSAccess and MS FoxPro in SQL.** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 317 (ET: N/A)]*

5. **(খ) DBMS কী? দুটি সুবিধা লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

6. **What is Database?** *[EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)]*

7. **What is data about data?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

8. **(খ) Centralized System ও Client Server System সম্পর্কে সচিত্র বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 612 (ET: N/A)]*

9. **(ক) একজন ডাটাবেস এডমিন এর কাজ কী? কিছু ডাটাবেস সিস্টেম অ্যাপ্লিকেশনের নাম লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 625 (ET: N/A)]*

10. **(খ) ডাটাবেস ব্যবস্থাপনা সিস্টেমের তিন স্তরবিশিষ্ট আর্কিটেকচার ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 626 (ET: N/A)]*

11. **(ক) সাধারণ ফাইলভিত্তিক সিস্টেমের চেয়ে DBMS এর সুবিধা কী কী?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 627 (ET: N/A)]*

12. **What is Database administrator role?** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 662 (ET: N/A)]*

13. **Explain difference between Data Administrator and Database Administrator.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 681 (ET: N/A)]*

14. **Describe the advantages and disadvantages of DBMS-provided and application provided security.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 684 (ET: N/A)]*

15. **(a) What is database schema? What are dangling tuple and descriptive attribute?** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 693 (ET: N/A)]*

16. **What is data Independence? How many types of data independence?** *[BDCCL Assistant Engineer (Network) 2022 compact it 742 (ET: N/A)]*

17. **(ii) Database এর Table and View এর মধ্যে পার্থক্য লিখুন। E-R diagram এর প্রয়োজনীয়তা লিখুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 785 (ET: N/A)]*

18. **(a) Distinguish between table and view in database management system.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 802 (ET: N/A)]*

19. **Database এর সর্বনিম্ন Unit কোনটি?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 944 (ET: N/A)]*

20. **DBMS বলতে কী বোঝানো হয়? DBMS শ্রেণিভিন্যাস বর্ণনা করুন।** *[40th BCS 2020 compact it 971-972 (ET: BPSC)]*

21. **Define View, Materialized View. Difference between View and Materialized View and Usage of two.** *[RAKUB Assistant Database Administrator 2020 compact it 1012-1013 (ET: E-Zone)]*

22. **What are the roles of Database Engineer?** *[RAKUB Assistant Database Administrator 2020 compact it 1014 (ET: E-Zone)]*

23. **A company needs key person for DBMS. What is his/her duty as key person?** *[Bangladesh Bank Assistant Programmer 2019 compact it 1155 (ET: DU)]*

24. **What is RDBMS? Why data are stored in database system instead of file?** *[ICT Ministry Assistant Programmer 2017 compact it 1236 (ET: N/A)]*

25. **a) What is a database? Discuss the importance of database.** *[Ministry of Finance Programmer 2013 compact it 1272 (ET: N/A)]*

26. **b) Specify the functions of the database administration.** *[Ministry of Finance Programmer 2013 compact it 1272 (ET: N/A)]*

## ER Diagram & Database Design (25)

1. BSCPL regularly publishes multiple job vacancies, where each Job is identified by a unique Job ID and contains information such as Job Title, Starting Salary, Job Description, and other relevant attributes. An Applicant is identified by a unique Applicant ID and has attributes such as Name, Date of Birth, Starting/Joining Date, Contact Information, and other details. An applicant can apply for only one job, while a particular job can receive applications from many applicants. Design the ER diagram for this system, showing the entities, attributes, primary keys, relationship, cardinalities, and participation constraints. [BSCCPL AME 21-08-2026 (BUET)]

2. **(a) Design an ER diagram for a library management systems where-** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1349 (ET: N/A)]*
   * **(i) A library has multiple books.**
   * **(ii) Each book can have multiple copies.**

3. **(খ) নিচের ডেটাবেস অনুযায়ী ER ডায়াগ্রাম তৈরি করুন :** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 415 (ET: N/A)]*
   * **Worker** (Worker ID, Worker Name, Hour Rate, Skill Type)
   * **Assignment** (Worker ID, Building ID, Start Date, Num Days)
   * **Building** (Building ID, Address, Building Type)

4. **Consider the Schema employee(id, name, salary), equipment(id, name, price), hire(employee_id, equipment_id)**
   **(i) Draw the ERD digram for the relation**
   **(ii) Write the SQL query to show the name of employee who borrow the maximum equipment?** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 462 (ET: BUET)]*

5. **Develop an entity relationship diagram that describes data objects, relationships and attributes of the following system: -A web based order processing system for a computer store.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 639 (ET: N/A)]*

6. **Draw a ER diagram for BPL.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 662 (ET: N/A)]*

7. **How can you define the ER model in DBMS?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*

8. **Draw an entity diagram Student database management systemfrom following statement: Student (data); Course (data); Report (data); Registration; Staff (data)** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 759 (ET: N/A)]*

9. **(ক) Entity-Relationship (ER) Diagram কেন ব্যবহার করা হয়? একটি উদাহরণের মাধ্যমে ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 768 (ET: N/A)]*

10. **(a) While converting E-R diagram into Tables, how is a Many-to-many relationship set between entities A and B is converted into database tables?** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 804 (ET: N/A)]*

11. **Draw ER diagram for Titas Gas Transmission and Distribution Company limited. Relation between customer and meter. (full question টা পাওয়া যায়নি।)** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 824 (ET: BUET)]*

12. **Draw ER diagram from a story.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 837 (ET: N/A)]*

13. **Draw E-R diagram of hospital management system. Hospital name “SKY Hospital Ltd.”.** *[RAKUB Programmer (PO) 12.10.2021 compact it 853 (ET: N/A)]*

14. **Draw E-R diagram of Banking Management system. Bank name “SKY Bank Ltd.”.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)]*

15. **Draw ER diagram for details of gas company data described. Bakharbad gas distribution Compeny has two types of customers i.e General and Industrial. General customer has customer ID, name, DOB, age (calculated from DOB). Industrial customer has all attributes of general customer with TAX number additionally. Meter has model and producer name. Every customer has one meter.** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 877 (ET: BUET)]*

16. **Draw the ER diagram where their relation named TEAM, PLAYER, MATCH** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 880 (ET: BUET)]*

17. **Railway Service system ER diagram.** *[Sonali Bank Ltd. Officer IT 2021 compact it 910 (ET: N/A)]*

18. **(i) Draw ER diagram: Given a scenario about football Game (Game_no, game_time, game_name), Team (team-id, coach_id, team-name), Referee (Referee-id, Referee-name) Player (player-id, palyername, player-position), Stadium information (stadium-id, stadium-name, stadium-loc) Match (match_id, match_date, match_result).** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 928-929 (ET: CTI)], [Janata Bank Assistant System Administrator 2021 compact it 939 (ET: N/A)]*
   **(ii) Convert the ER diagram to relations (Table)** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 929-930 (ET: CTI)]*

19. **Draw ER diagram (Self test)** *[Combined 4 Banks Assistant Programmer 2020 compact it 1009 (ET: DU)]*

20. **E-R Diagram কী? উদাহরণসহ লিখুন?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019-1020 (ET: N/A)]*

21. **Draw an ER diagram of a Library Management System.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036-1037 (ET: BUET)]*

22. **(ক) Database এর ক্ষেত্রে E-R Diagram বলতে কী বোঝায়? একটি উদাহরণের মাধ্যমে ব্যাখ্যা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1094 (ET: N/A)]*

23. **Explain E-R diagram with example?** *[BINA Assistant Programmer 2019 compact it 1155 (ET: IBA)]*

24. **Daraz is proud of having up-to-date information on the processing and current location of each shipped item. Daraz relies on a company-wide information system. Shipped items are the heart of the Daraz product tracking information system. Shipped items can be characterized by item number, weight, dimensions, insurance amount, destination and final delivery date. Shipped items are received into the Daraz system at a single retail center. Retail center are characterized by their type, ID and address. Shipped items make their way to their destination via one or more standard Daraz transportation events (flights, truck deliveries). These transportation events are characterized by a schedule number, a type (e.g. flight, truck), and a delivery route. Please create an entity relationship diagram that captures this information about the Daraz system. Be certain to indicate identifiers and cardinality constraints.** *[Sonali & Janata Bank Senior Officer (IT/ICT) 2018 compact it 1166 (ET: N/A)]*

25. **Design ER diagram for Online MCQ examination portal. Your design must contain separate entities for student, examination, question, solution and submission. Ensure that normalization is ful-fill in your design and identify the primary and foreign key.** *[Combined 3 Banks Assistant Programmer 2018 compact it 1196-1197 (ET: N/A)]*

## Normalization & Database Design (21)

1. **What is Normalization? How do 1NF and 2NF work in a database? Give examples.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

2. **Why normalization is required in Database? Write shortly about 3NF?** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1350 (ET: N/A)]*

3. **Explain the differences between Second Normal Form (2NF) and Third Normal Form (3NF) with examples.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1340 (ET: N/A)]*

| 2NF(Second Normal Form) | 3NF(Third Normal Form) |
|---|---|
| It is already in 1NF. | It is already in 1NF as well as in 2NF also. |
| In 2NF, non-prime attributes (attributes that are not part of any candidate key) must depend on the entire candidate key. | In 3NF non-prime attributes are only allowed to be functionally dependent on Super key of relation. |
| No partial functional dependency of non-prime attributes on any proper subset of a candidate key is allowed. | No transitive functional dependency of non-prime attributes on any super key is allowed. |
| Stronger normal form than 1NF but lesser than 3NF. | Stronger normal form than 1NF and 2NF. |
| It eliminates repeating groups in relation. | It virtually eliminates all the redundancies. |
| The goal of the second normal form is to eliminate redundant data. | The goal of the third normal form is to ensure referential integrity. |

4. **What is Logical design database is called?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

5. **A Bank schema is given below:** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1322 (ET: DU)]*
   $$\text{Bank}(\text{Br\_Name}, \text{Br\_City}, \text{Assets}, \text{Acc\_name}, \text{Acc\_Num}, \text{Balance})$$
   * (a) Provided and Normalize and point out Primary and Foreign Key?
   * (b) Show that is the schema and state that why your schema is in good form.

6. **What is Normalize a database? Used containers if needed, draw an ER Diagram.** **[See WZPGCL, Assistant Engineer (CSE), Exam: 27.05.2023]** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 315 (ET: N/A)]*

7. **(ক) Normalization কী? কত প্রকার ও কী কী? ব্যাখ্যা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 415 (ET: N/A)]*

8. **What is database Normalization? Write down the types of database Normalization.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 504 (ET: N/A)]*

9. **Which normalization is related to functional dependency?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

10. **Functional dependency use in which normalizations?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

11. **What in First and Second Normal form is DBMS?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*

12. **অথবা, (ক) “BCNF is stricter than 3NF” এই উক্তিটি উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 626 (ET: N/A)]*

13. **Why Normalization is used in database? Explain 1^{\text{st}} Normal form using an example.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 665 (ET: N/A)]*

14. **Why do you need database Normalization?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*

15. **Let a relational function is R(A, B, C, D, E), Write Yes or No based on those are the follow n functional dependency.** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 822 (ET: BUET)]*
   AB \to C
   B \to B
   DE \to A

16. **What is DBMS? Write down the purpose of normalization in DBMS.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*

17. **(b) What is normalization? Why is it needed?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 895 (ET: N/A)]*

18. **(i) DBMS কী? একটি Database কে normalize করার পদ্ধতিগুলো বর্ণনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 953-954 (ET: N/A)]*

19. **What is normalization? Explain composite key with example.** *[Bangladesh Television Assistant Programmer 2019 compact it 1063 (ET: N/A)]*

20. **(a) What do you mean by Normalization in RDBMS? Explain with an example.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1143 (ET: N/A)]*

21. **What do you mean by Database properties using Normalization?** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1174 (ET: N/A)]*

## SQL Commands (DDL, DML, DCL, TCL) (18)

1. Example Query of DDL, DML, DCL. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

2. **What is SQL?** *[BBA Assistant Programmer 12.07.2025 compact it 1433 (ET: BUET)]*

3. **ডাটাবেজ এ টেবিলের শুধু গঠন ডিলিট করার SQL কমান্ড কি?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

4. **(খ) SQL এ DDL এবং DML এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 627 (ET: N/A)], [17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 611 (ET: N/A)]*

5. **SQL query to insert data into table. (A table was given with 3 row)** *[NSDA Assistant Programmer Date: 04-03-2022 compact it 657 (ET: N/A)]*

6. **How can you Revoke permissions from a database table? Give SQL command for it.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 666 (ET: N/A)]*

7. **What is DDL and DML?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

8. **(i) নিচের Table টি তৈরি করার SQL কমান্ড লিখুন। student_info (std_id, name, department, phone_number) (a) Table তে ২টি record (insert) প্রবেশ করার SQL কমান্ড লিখুন। (b) Table টি থেকে CSE বিভাগের ছাত্র/ছাত্রীদের নামের তালিকা বের করার SQL command লিখুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 785 (ET: N/A)]*

9. **Write the create table command for the ‘Employee’ table with the following column: Emp_ID, Emp_Name, Date_of_Birth.** *[BCC CA Monitoring System Project 2021 compact it 829 (ET: N/A)]*

10. **৪. ডাটাবেইজে টেবিল ডিলেট করার কমান্ড লিখ?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

11. **ডাটাবেইজ ম্যানেজমেন্ট সিস্টেমের মধ্যে CRUD এর কাজ কি?** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 947 (ET: BUET)]*

12. **Main components of SQL are DDL (Data definition Language), DML (Data Manipulation Language) and DCL (Data Control Language). Give some examples of DDL, DML and DCL commands.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 988-989 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

13. **How to find duplicate data in database? Explain DDL and DML.** *[RAKUB Assistant Database Administrator 2020 compact it 1017-1018 (ET: E-Zone)]*

14. **(a) How can you revoke permissions from a database table? Give SQL command for it.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1136-1138 (ET: N/A)]*

15. **(c) Differentiate between “delete from” and “drop table” SQL statement.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1136-1138 (ET: N/A)]*

16. **Write an SQL query to insert a tuple in the table: Employee (ID, Name, Designation, and Salary).** *[NESCO Assistant Manager (MIS & ICT) 2018 compact it 1177 (ET: N/A)]*

17. **Construct a database table “Customer”, Where CustomerID is primary key of the table.** *[Jiban Bima Corporation Assistant Programmer 2018 compact it 1211 (ET: N/A)]*

| CustomerID | CustomerName | Address | PostCode |
|---|---|---|---|
| 1 | Sakib | Khulna | 1212 |
| 2 | Tamim | Barisal | 2100 |
| 3 | Musfiq | Dhaka | 1205 |

18. **What are the difference among DDL, DML and DCL?** *[NWPGCL Assistant Engineer (CSE) 2018 compact it 1213 (ET: N/A)]*

## Transaction Management & ACID Properties (14)

1. **Explain the concept of ACID properties in a database transaction. Describe how each property—Atomicity, Consistency, Isolation, and Durability—ensures the reliability and integrity of a database system.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1425 (ET: E-Zone)]*

2. **How many process of Transaction complete?** *[BREB Assistant Programmer (AP) 21.02.2025 compact it 1336 (ET: N/A)]*

3. **ACID এর প্রোপার্টি কি?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1450 (ET: N/A)]*

4. **(খ) Transaction কী? Transaction Management এর ACID properties সমূহ বর্ণনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 415 (ET: N/A)]*

5. **Case Study type Database-related problem (Solve: ACID)** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 321 (ET: N/A)]*

6. **What are the ACID properties of transaction to ensure data reliability and integrity?** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 472 (ET: N/A)]*

7. **(a) What is ACID mean in database system?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 492 (ET: N/A)]*

8. **(গ) ডাটাবেস ট্রানজেকশনের ACID Properties সম্পর্কে লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 626 (ET: N/A)]*

9. **What do you mean by Rollback and Roll forward?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 682 (ET: N/A)]*

10. **Describe ACID properties of DBMS.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 860 (ET: N/A)]*

11. **A transaction consists of a sequence of query and/or update statements. SQL statement must be required to end the transaction. List the SQL statements, required to end the transaction and also write their functions.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 984-985 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

12. **Describe Database ACID properties.** *[RAKUB Assistant Database Administrator 2020 compact it 1012 (ET: E-Zone)]*

13. **Describe the ACID properties in a database. When does a deadlock occur and how do you prevent it, in a database?** *[Combined Bank Senior Officer (IT/ICT) 2019 compact it 1116 (ET: DU)]*

14. **Describe the ACID properties of database.** *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1219 (ET: N/A)]*

## Relational Data Model & ER Relationships (14)

1. What are the different types of relationships in a relational database? Explain each with examples. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

2. **Discuss about different types of relations in DBMS.** *[Combined Bank Assistant Programmer 09.02.2024 compact it 297 (ET: BIBM)]*

3. **What is the degree of relation in dbms?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

4. **(খ) One-to-one এবং One-to-many রিলেশন উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 614 (ET: N/A)]*

5. **Weak Entity and strong entity difference with relation.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 660 (ET: N/A)]*

6. **(b) Give example of week and strong entity sets.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 694 (ET: N/A)]*

7. **(a) What is referential integrity? How do you impose in your database design?** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 795 (ET: N/A)]*

8. **What is a weak entity for data modeling using the entity relationship model find out any weak entity and its identify relationship for the school database? Which of the following table? Student(student_id, student_name, admission_year) Teacher(teacher_id, teacher_name, teacher_joindate) Course(course_id, subject_name, credit)** *[BCC Assistant Programmer 12.02.2021 compact it 814 (ET: BUET)]*

9. **(c) What is a weak entity set? How the primary key is generated for weak entity set?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 896 (ET: N/A)]*

10. **(a) Write down Integrity rules in database.** *[National University Assistant Programmer 2020 compact it 976 (ET: DU)]*

11. **What is constraints? Why use constraint? Difference between table level Cosntraint and column level Cosntraint.** *[RAKUB Assistant Database Administrator 2020 compact it 1015 (ET: E-Zone)]*

12. **(ক) Relationship degree কাকে বলে? উহা কত প্রকার ও কি কি? সংক্ষেপে লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1068 (ET: N/A)]*

13. **(খ) Relational Database Model কী? অন্যান্য মডেলের তুলনায় এর সুবিধা ও অসুবিধা গুলো লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1094-1095 (ET: N/A)]*

14. **What is cardinality and modality?** *[Bangladesh Bank Assistant Programmer 2016 compact it 1265-1266 (ET: N/A)]*

## Indexing & Query Optimization (B-Tree, B+ Tree) (10)

1. **How indexing improve query performance?** *[Bangladesh Satellite Company Limited Assistant Engineer (CSE) 23.08.2025 compact it 1431 (ET: BUET)]*

2. **Briefly describe primary key, foreign key and indexing in relational database and their relationship. Do you think database indexing always makes applications faster? Explain your answer.**

**Table Name: STUDENT**
| Stu_Id | Stu_Name | Stu_Age |
|---|---|---|
| 101 | Steve | 23 |
| 102 | John | 24 |
| 103 | Robert | 28 |
| 104 | Steve | 29 |

**Course_enrollment table:**
| Course_Id | Stu_Id |
|---|---|
| C01 | 101 |
| C02 | 102 |
| C03 | 101 |
| C05 | 102 |
| C06 | 103 |
| C07 | 102 |

*[Combined Bank Senior Officer (IT) 17.05.2024 compact it 337 (ET: BIBM)]*

3. **অথবা, (ক) Indexing এবং Hashing এর পদ্ধতিগুলো বর্ণনা করুন** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 612 (ET: N/A)]*

4. **How does index tuning help in improving query performance?** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 747 (ET: N/A)]*

5. **Construct a B+ tree index structure on emp_id for the given relation employee as shown below with n=4.** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 824 (ET: BUET)]*

6. **What is Indexing? Write down the usages of Indexing.** *[RAKUB Assistant Database Administrator 2020 compact it 1015 (ET: E-Zone)]*

7. **(খ) Database এর ক্ষেত্রে Indexing এর কার্যকারিতা বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1096 (ET: N/A)]*

8. **(ক) Sorting and Indexing-এর মধ্যে পার্থক্য লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1096 (ET: N/A)]*

9. **What is the purpose of index in database?** *[DESCO Assistant Engineer (CSE) 2016 compact it 1267 (ET: N/A)]*

10. **How hashtable is used in database?** *[DESCO Assistant Engineer (CSE) 2016 compact it 1267 (ET: N/A)]*

## Data Warehousing, Data Mining & Business Intelligence (9)

1. **Differentiate among Database, Data Warehouse and Data Mining with real world example.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 517 (ET: MIST)]*

2. **Discuss different tools and techniques to develop a Business Intelligence Dashboard for a bank. How can data be captured and aggregated from various sources within the bank to monitor the business performance?** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 519 (ET: MIST)]*

3. **Software scenario question- Business Intelligence Model** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 521 (ET: MIST)]*

4. **(খ) Big data বলতে কি বুঝায়? Big data এর বৈশিষ্ট্যগুলো লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 766 (ET: N/A)]*

5. **Write down different stage of data mining?** *[Combined 5 Banks Assistant Maintenance Engineer 2019 compact it 1055 (ET: AUST)]*
   a) Data Purification
   b) Data Integration
   c) Data Selection
   d) Data Transformation
   e) Data Mining (The Final Stage)
   f) Pattern Evaluation
   g) Knowledge Representation

6. **Database tuning and database mining বলতে কী বোঝেন?** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1077 (ET: N/A)]*

7. **(ক) Data Mining and Data Warehousing বলতে কী বোঝায়? এদের মধ্যে সম্পর্ক কী? এদের উপকারিতা কী?** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1095-1096 (ET: N/A)]*

8. **What is Data warehouse? Why We Need Data Warehouse? Advantages of Data warehousing.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1162 (ET: N/A)]*

9. **Explain data warehouse with figure. Describe fact table and dimension table with example.** *[ICT Ministry Assistant Programmer 2017 compact it 1243-1244 (ET: N/A)]*

## Database Backup & Disaster Recovery (8)

1. **Difference between incremental backup and differential backup. Which is more suitable for the banking system?** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 319 (ET: N/A)]*

2. **Database Data Loss based case study type question......** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 321 (ET: N/A)]*

3. **What do you understand about the IT disaster recovery plan? Describe your approach to disaster recovery and business continuity planning for the data centre of your office.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 333 (ET: BIBM)]*

4. **একটি MySQL database এর ডাটা ব্যাক আপ ও ব্যাক আপ করা ডাটা রিস্টোর করার কমান্ড লিখ।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 382 (ET: BUET)]*

5. **In the context of data management, what are the primary differences between data recovery and data backup? Provide real-world examples of when each is employed effectively.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 539 (ET: MIST)]*

6. **To achieve a '0-bit data loss' for its 24 x 7 x 365 banking operation, what steps or technology should an online bank employ to safeguard its data against any potential threats of data loss?** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 518 (ET: MIST)]*

7. **MySQL database এর ক্ষেত্রে Backup and Restore করার কমান্ড লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 865 (ET: BUET)]*

8. **Describe what are the ways for no data loss?** *[RAKUB Assistant Database Administrator 2020 compact it 1015-1016 (ET: E-Zone)]*

## PL/SQL & Database Triggers (7)

1. **Explain Database Trigger with example.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

2. **Database program with base and high- level language (SQL) to find out the interest rate from the given database table.** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 321 (ET: N/A)]*

3. **(c) Define dynamic SQL and trigger with examples.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 693 (ET: N/A)]*

4. **(b) Describe the application of trigger in database.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 795 (ET: N/A)]*

5. **Suppose, ‘Employee’ table (emp_id, emp_name, dept_id, salary) and ‘Department’ table (dept_id, dept_name, increment_dept). Create a tigger to increment the salary of the employee by 10% whose salary is above 30000.** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 862 (ET: BUET)]*

6. **(a) What is the purpose of database trigger? Explain with an example.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)]*

7. **Write a program in pl/SQL to find the heighest paid employees from employee table and store the data in HighestPaidEmp table.** *[Dutch Bangla Bank Ltd. Probationary Officer (Software) 2018 compact it 1199 (ET: N/A)]*

## SQL Joins & Operations (7)

1. **What are the different types of join in SQL?** *[DESCO Assistant Engineer 20.05.2023 compact it 580 (ET: DESCO)]*

2. **Left joning and inner joining of a table.** *[BTCL Assistant Manager (Technical) 2023 compact it 594 (ET: BUET)]*

3. **Which join is used for including not matching all records with output?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

4. **What is inner join? Explain with syntax and example.** *[Bangladesh Television Assistant Programmer 2019 compact it 1065 (ET: N/A)]*

5. **(b) Explain JOIN and INNER-JOIN procedure.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1143 (ET: N/A)]*

6. **Define: (i) Left outer join (ii) Right outer join (iii) Full outer join (iv) One to many and (v) Many to many** *[Dutch Bangla Bank Ltd. Probationary Officer (Software) 2018 compact it 1199 (ET: N/A)]*

7. **What join should use when there is no match between two tables?** *[DESCO Assistant Engineer (CSE) 2016 compact it 1266 (ET: N/A)]*

## Distributed & Parallel Databases (5)

1. **(খ) Speedup এবং Scaleup চিত্রসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 613 (ET: N/A)]*

2. **(ক) Data Fragmentation কী? ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 613 (ET: N/A)]*

3. **What is distributed database?** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 660 (ET: N/A)]*

4. **Which of the following distributed database system over centralized database system? (a) Software cost (b) Software complexity (c) Slow response (d) Modular growth** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

5. **Explain the concept distributed DBMS. What are the features of DBMS?** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1054 (ET: BUET)]*

## Database Design & Data Types (3)

1. An institute wants to create a database table named STUDENT to store student information. The table should include the columns Roll Number, Name, Department, Email, and Admission Date. Specify the most appropriate SQL data type for each column and identify which column should be defined as the Primary Key, giving a brief justification for your choice. *[Officer (IT) 31 Jul 2026 bscs 03 (ET: N/A)]*

2. **(c) Describe the difference between CHAR and VARCHAR data type.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 795 (ET: N/A)]*

3. **What is the domain in a relational database? Explain with an example. Show how you would use Alter table SQL command to add a domain on a database table.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 916 (ET: N/A)]*

## NoSQL, NewSQL & Modern Databases (2)

1. **What are the limitations of DBMS and how to related newsql with SQL and No-SQL.** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1332 (ET: BUET)]*

2. **Write difference between relational database and NoSQL database.** *[Sonali Bank Ltd. Officer IT 2021 compact it 909 (ET: N/A)]*

## Database Connectivity (JDBC) (2)

1. What is JDBC? Explain the steps required to connect a Java application to a MySQL database. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

2. **(b) Explain embedded SQL with an appropriate example.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 693 (ET: N/A)]*

## Relational Keys (Candidate, Super, Primary, Foreign Key) (1)

1. **Employee table( NID, Company_ID, Name, Mobile Number). Assume every record has a unique Mobile number. Find the number of super key, candidate key. And give example of two candidate key.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 399 (ET: BUET)]*

## Indexing in DBMS (1)

1. **সূচকের ধরন কি? এখানে প্রশ্নের উত্তর বিষয়ভিত্তিক প্রকার লেখ।** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*
