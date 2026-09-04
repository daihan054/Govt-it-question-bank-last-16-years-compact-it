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

   Answer:

   | Point | Primary Key | Foreign Key | Candidate Key |
   |---|---|---|---|
   | Definition | The candidate key chosen to identify each row | A column referring to the primary key of another table | A minimal set of attributes that uniquely identifies a row |
   | Uniqueness | Always unique | May repeat | Always unique |
   | NULL allowed | `Never` | Yes, unless declared NOT NULL | No |
   | Number per table | Exactly `one` | Many | One or many |
   | Purpose | Entity integrity — identify a row | Referential integrity — link two tables | The pool from which the primary key is chosen |
   | Belongs to | Its own table | Refers to another table | Its own table |
   | Index | Clustered index created automatically in most systems | Non-clustered, must usually be created manually | Only if chosen as primary or unique |
   | Relationship | Is one of the candidate keys | Points at a primary key elsewhere | Superset that includes the primary key |

   The relationship between them
   ```
   Super Key       -> any attribute set that identifies a row uniquely
      |
   Candidate Key   -> a MINIMAL super key (no attribute can be removed)
      |
   Primary Key     -> the ONE candidate key the designer selects
      |
   Alternate Key   -> the candidate keys not selected
   ```

   Example
   ```
   Student (student_id, national_id, email, name, dept_id)

   Super keys      : {student_id}, {student_id, name}, {national_id, email}, ...
   Candidate keys  : {student_id}, {national_id}, {email}     -- each minimal
   Primary key     : student_id                                -- chosen
   Alternate keys  : national_id, email
   Foreign key     : dept_id  -> Department(dept_id)
   ```

   ```sql
   CREATE TABLE Department (
       dept_id   INT PRIMARY KEY,
       dept_name VARCHAR(50)
   );

   CREATE TABLE Student (
       student_id  INT PRIMARY KEY,              -- primary key
       national_id VARCHAR(20) UNIQUE,           -- alternate (candidate) key
       email       VARCHAR(100) UNIQUE,          -- alternate (candidate) key
       name        VARCHAR(100) NOT NULL,
       dept_id     INT,
       FOREIGN KEY (dept_id) REFERENCES Department(dept_id)   -- foreign key
   );
   ```

   What each one enforces
   - `Primary key` — entity integrity: no two rows are identical and no row is unidentifiable, so it can never be NULL.
   - `Foreign key` — referential integrity: a value must already exist in the referenced table, so an order cannot point at a customer who does not exist.
   - `Candidate key` — every attribute set capable of being the primary key; the designer picks one, usually the smallest and most stable.

2. **(a) Define RDBMS. Explain the different key and primary key, candidate key, super key, and foreign key DBMS.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1445 (ET: N/A)]*

   Answer:

   RDBMS
   - A `Relational Database Management System` is software that stores data in `tables` (relations) made of rows (tuples) and columns (attributes), and manages the relationships between those tables using keys.
   - It is based on E. F. Codd's relational model (1970) and is accessed with `SQL`.
   - Characteristics: data in two-dimensional tables; every row uniquely identified by a primary key; tables linked by foreign keys; support for constraints; and `ACID` transaction guarantees.
   - Examples: Oracle, MySQL, PostgreSQL, SQL Server, IBM Db2, SQLite.
   - Difference from a plain DBMS: a DBMS may store data as files or in a hierarchy with no enforced relationships, whereas an RDBMS enforces the relational model, normalisation and referential integrity.

   The keys

   `Super key`
   - Any set of one or more attributes that `uniquely identifies` a row. It may contain redundant attributes.
   - Example, for Student(student_id, national_id, email, name):
   ```
   {student_id}, {national_id}, {student_id, name}, {student_id, national_id, email, name}
   ```
   - All of these identify a row uniquely, so all are super keys. Note that adding extra attributes to a super key still gives a super key.

   `Candidate key`
   - A `minimal` super key — remove any attribute and it stops being unique.
   ```
   Candidate keys: {student_id}, {national_id}, {email}
   ```
   - `{student_id, name}` is a super key but not a candidate key, because `name` is unnecessary.
   - Every candidate key is a super key; not every super key is a candidate key.

   `Primary key`
   - The `one` candidate key the designer selects to identify rows. It can never be NULL and never repeat, and a table has exactly one.
   ```
   Primary key: student_id
   ```
   - The candidate keys not chosen become `alternate keys` and are usually declared UNIQUE.

   `Foreign key`
   - An attribute in one table whose values must exist as the primary key of another table. It enforces `referential integrity`.
   - It may be NULL (meaning "no related row yet") and may repeat, since many students can be in one department.
   ```
   Student.dept_id -> Department.dept_id
   ```

   Complete example
   ```sql
   CREATE TABLE Department (
       dept_id   INT PRIMARY KEY,
       dept_name VARCHAR(50) NOT NULL UNIQUE
   );

   CREATE TABLE Student (
       student_id  INT PRIMARY KEY,            -- primary key
       national_id VARCHAR(20) UNIQUE,         -- alternate key
       email       VARCHAR(100) UNIQUE,        -- alternate key
       name        VARCHAR(100) NOT NULL,
       dept_id     INT,
       FOREIGN KEY (dept_id) REFERENCES Department(dept_id)
   );
   ```

   Two other keys often asked alongside
   - `Composite key` — a primary key made of more than one attribute, for example `(order_id, product_id)` in an order-line table.
   - `Alternate key` — a candidate key not chosen as the primary key.

3. **Difference between primary key, foreign key? What is trigger?** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 502 (ET: N/A)]*

   Answer:

   Primary key vs foreign key

   | Point | Primary Key | Foreign Key |
   |---|---|---|
   | Purpose | Uniquely identifies each row of its own table | Links a row to a row in another table |
   | Integrity enforced | `Entity integrity` | `Referential integrity` |
   | Uniqueness | Must be unique | May repeat |
   | NULL | `Not allowed` | Allowed, unless declared NOT NULL |
   | Number per table | Exactly one | Many |
   | Refers to | Nothing; it is the reference | The primary key of another table |
   | Index | Clustered index created automatically | Must usually be indexed manually |
   | Deleting a referenced row | Restricted if child rows exist | The child row is the dependent one |

   Example
   ```sql
   CREATE TABLE Department (
       dept_id   INT PRIMARY KEY,          -- primary key
       dept_name VARCHAR(50)
   );

   CREATE TABLE Employee (
       emp_id   INT PRIMARY KEY,           -- primary key of this table
       emp_name VARCHAR(100),
       dept_id  INT,
       FOREIGN KEY (dept_id) REFERENCES Department(dept_id)   -- foreign key
   );
   ```
   - `Employee.dept_id` may repeat, because many employees work in one department, and it may be NULL for an unassigned employee. `Department.dept_id` may do neither.

   What is a trigger
   - A `trigger` is a block of code stored in the database that runs `automatically` in response to an event on a table — an INSERT, UPDATE or DELETE. It is never called explicitly.

   ```sql
   CREATE TRIGGER audit_salary_change
   AFTER UPDATE ON Employee
   FOR EACH ROW
   BEGIN
       INSERT INTO Salary_Audit (emp_id, old_salary, new_salary, changed_on)
       VALUES (OLD.emp_id, OLD.salary, NEW.salary, NOW());
   END;
   ```
   - `OLD` refers to the row before the change and `NEW` to the row after it.

   Classification
   - By timing: `BEFORE` (validate or modify the data before it is written) and `AFTER` (react once the change is committed to the table).
   - By event: `INSERT`, `UPDATE`, `DELETE`.
   - By granularity: `ROW-level` (once per affected row) and `STATEMENT-level` (once per statement).

   Uses
   - Maintaining an `audit trail` of who changed what and when.
   - Enforcing complex business rules that a CHECK constraint cannot express.
   - Keeping `derived data` consistent, such as a running total or a stock level.
   - Cascading changes to related tables, and preventing invalid operations.

   Drawbacks
   - They are `invisible` — an application developer may not realise a trigger is firing, which makes debugging hard.
   - They add overhead to every write, and a trigger that fires another trigger can cascade unexpectedly.
   - Business logic hidden in the database is harder to test and version-control than logic in the application.

4. **Define primary key, super key, and Candidate key.** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*

   Answer:

   `Super key`
   - Any set of one or more attributes whose values `uniquely identify` a row in a relation. It is allowed to contain redundant attributes.
   - Adding any attribute to a super key produces another super key, so a table usually has many of them.

   `Candidate key`
   - A `minimal` super key: no attribute can be removed from it without destroying uniqueness.
   - Every candidate key is a super key, but not every super key is a candidate key.

   `Primary key`
   - The `one` candidate key that the designer chooses to identify rows in the table.
   - It can never be NULL and never repeat, and there is exactly one per table. The candidate keys not chosen become `alternate keys`.

   Worked example
   ```
   Student (student_id, national_id, email, name, phone)

   Assume student_id, national_id and email are each unique on their own.
   ```

   Super keys — many
   ```
   {student_id}
   {national_id}
   {email}
   {student_id, name}
   {national_id, phone}
   {student_id, national_id, email, name, phone}
   ```
   - All identify a row uniquely, so all are super keys. Most contain unnecessary attributes.

   Candidate keys — the minimal ones
   ```
   {student_id}
   {national_id}
   {email}
   ```
   - `{student_id, name}` is `not` a candidate key: removing `name` still gives uniqueness, so it is not minimal.

   Primary key — the one chosen
   ```
   student_id
   ```
   - Chosen because it is short, numeric, never changes and is generated by the system. `national_id` and `email` become alternate keys and are declared UNIQUE.

   The hierarchy
   ```
   +-------------------------------------------+
   |              SUPER KEYS                   |
   |   +-----------------------------------+   |
   |   |        CANDIDATE KEYS             |   |
   |   |   +-------------------------+     |   |
   |   |   |      PRIMARY KEY        |     |   |
   |   |   +-------------------------+     |   |
   |   +-----------------------------------+   |
   +-------------------------------------------+
   ```

   In SQL
   ```sql
   CREATE TABLE Student (
       student_id  INT PRIMARY KEY,          -- primary key
       national_id VARCHAR(20) UNIQUE,       -- alternate (candidate) key
       email       VARCHAR(100) UNIQUE,      -- alternate (candidate) key
       name        VARCHAR(100) NOT NULL,
       phone       VARCHAR(15)
   );
   ```

   Choosing a primary key in practice
   - Prefer one that is `short`, `numeric`, `never changes` and is `never NULL`. That is why a surrogate `id` is usually preferred to a natural key such as an email address, which a person may change.

5. **What is primary key and foreign key with example?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 499 (ET: N/A)]*

   Answer:

   Primary key
   - The column, or set of columns, that `uniquely identifies` each row of a table.
   - Rules: values must be `unique`, can `never be NULL`, and there is exactly `one` primary key per table.
   - It enforces `entity integrity` — the guarantee that every row is distinct and identifiable.
   - Most database systems create a clustered index on it automatically, which is why lookups by primary key are fast.

   Foreign key
   - A column in one table whose values must match the `primary key` of another table.
   - It enforces `referential integrity` — the guarantee that a reference points at something that actually exists.
   - Values may `repeat` and may be `NULL` (meaning "not related to anything yet"). A table may have many foreign keys.

   Example
   ```sql
   CREATE TABLE Department (
       dept_id   INT PRIMARY KEY,               -- PRIMARY KEY
       dept_name VARCHAR(50) NOT NULL
   );

   CREATE TABLE Employee (
       emp_id   INT PRIMARY KEY,                -- PRIMARY KEY of Employee
       emp_name VARCHAR(100) NOT NULL,
       salary   DECIMAL(10,2),
       dept_id  INT,
       FOREIGN KEY (dept_id) REFERENCES Department(dept_id)   -- FOREIGN KEY
   );
   ```

   The data
   ```
   Department (parent)                Employee (child)
   +---------+-----------+            +--------+----------+---------+
   | dept_id | dept_name |            | emp_id | emp_name | dept_id |
   +---------+-----------+            +--------+----------+---------+
   |   10    | IT        |  <-------- |  101   | Karim    |   10    |
   |   20    | HR        |  <-------- |  102   | Rahim    |   10    |  repeats
   +---------+-----------+  <-------- |  103   | Sumi     |   20    |
                                      |  104   | Nabil    |  NULL   |  allowed
                                      +--------+----------+---------+
   ```

   What the constraints prevent
   ```sql
   -- rejected: dept 99 does not exist in Department
   INSERT INTO Employee VALUES (105, 'Jamil', 40000, 99);
      -> ERROR: foreign key constraint fails

   -- rejected: emp_id 101 already exists
   INSERT INTO Employee VALUES (101, 'Farida', 50000, 10);
      -> ERROR: duplicate primary key

   -- rejected: employees still reference department 10
   DELETE FROM Department WHERE dept_id = 10;
      -> ERROR: cannot delete a parent row
   ```

   Comparison

   | Point | Primary key | Foreign key |
   |---|---|---|
   | Uniqueness | Required | Not required |
   | NULL | Never | Allowed |
   | Count per table | One | Many |
   | Integrity enforced | Entity | Referential |
   | Points at | Nothing | The parent table's primary key |

6. **Explain Primary key, Candidate key, and Foreign key.** *[Teletalk Assistant Manager (IT) 2023 compact it 468 (ET: N/A)]*

   Answer:

   `Primary key`
   - The candidate key chosen to uniquely identify each row of a table.
   - It must be `unique`, can `never be NULL`, and there is exactly one per table.
   - It enforces `entity integrity`, and it is normally indexed automatically.
   ```sql
   student_id INT PRIMARY KEY
   ```

   `Candidate key`
   - Any `minimal` set of attributes that uniquely identifies a row — remove one attribute and uniqueness is lost.
   - A table may have several. The designer selects one as the primary key, and the rest become `alternate keys`, usually declared UNIQUE.
   ```
   Student(student_id, national_id, email, name)
   Candidate keys: {student_id}, {national_id}, {email}
   ```

   `Foreign key`
   - An attribute in one table whose values must already exist as the primary key of another table.
   - It enforces `referential integrity`, may `repeat`, and may be `NULL`.
   ```sql
   dept_id INT REFERENCES Department(dept_id)
   ```

   Complete worked example
   ```sql
   CREATE TABLE Department (
       dept_id   INT PRIMARY KEY,
       dept_name VARCHAR(50) NOT NULL UNIQUE
   );

   CREATE TABLE Student (
       student_id  INT PRIMARY KEY,           -- PRIMARY KEY (chosen candidate)
       national_id VARCHAR(20) UNIQUE,        -- CANDIDATE KEY (alternate)
       email       VARCHAR(100) UNIQUE,       -- CANDIDATE KEY (alternate)
       name        VARCHAR(100) NOT NULL,
       dept_id     INT,
       FOREIGN KEY (dept_id) REFERENCES Department(dept_id)   -- FOREIGN KEY
   );
   ```

   Comparison

   | Point | Primary key | Candidate key | Foreign key |
   |---|---|---|---|
   | Uniqueness | Yes | Yes | No |
   | NULL allowed | No | No | Yes |
   | Number per table | One | One or many | Many |
   | Minimal | Yes | Yes | Not applicable |
   | Refers to another table | No | No | Yes |
   | Integrity enforced | Entity | — | Referential |
   | Chosen by | The designer, from the candidates | Determined by the data | The designer |

   The relationship in one line
   - Every `primary key` is a `candidate key`, and every candidate key is a `super key`. A `foreign key` is different in kind — it is not about identifying rows in its own table but about pointing at rows in another.

7. **(খ) Primary key এবং Super key এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 625 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   | Point | Primary Key | Super Key |
   |---|---|---|
   | Definition | The candidate key chosen to identify rows | Any attribute set that identifies rows uniquely |
   | Minimality | `Must be minimal` — no attribute can be removed | `May contain redundant attributes` |
   | Number per table | Exactly `one` | Usually `many` |
   | NULL allowed | Never | Its attributes could be NULL unless constrained |
   | Chosen by | The designer | Determined by the data; not chosen |
   | Declared in SQL | Yes, with `PRIMARY KEY` | No SQL keyword exists for it |
   | Index created | Yes, automatically | No |
   | Relationship | Every primary key is a super key | Not every super key is a primary key |

   Worked example
   ```
   Student (student_id, national_id, email, name, phone)
   ```

   Super keys — many of them
   ```
   {student_id}
   {national_id}
   {email}
   {student_id, name}
   {student_id, national_id}
   {national_id, phone, name}
   {student_id, national_id, email, name, phone}
   ```
   - Any set containing a unique attribute is a super key, and adding more attributes keeps it a super key. A table with n attributes can have a very large number of them.

   Primary key — exactly one
   ```
   student_id
   ```
   - Chosen from the minimal super keys (the candidate keys) because it is short, numeric and never changes.

   Why `{student_id, name}` is a super key but not a primary key
   - It does identify a row uniquely, so it qualifies as a super key.
   - But `name` is redundant — `student_id` alone is already sufficient. A primary key must be `minimal`, so this set is disqualified.

   The containment relationship
   ```
   +----------------------------------------------+
   |                 SUPER KEYS                   |
   |   (any set that uniquely identifies a row)   |
   |   +--------------------------------------+   |
   |   |          CANDIDATE KEYS              |   |
   |   |     (minimal super keys)             |   |
   |   |   +------------------------------+   |   |
   |   |   |        PRIMARY KEY           |   |   |
   |   |   |   (the one that is chosen)   |   |   |
   |   |   +------------------------------+   |   |
   |   +--------------------------------------+   |
   +----------------------------------------------+
   ```
   - In one sentence: `every primary key is a super key, but a super key becomes a primary key only if it is minimal and is the one selected`.

8. **Super key and Candidate key finding from table.** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 648 (ET: BUET)]*

   Answer: Super keys and candidate keys are found from the data by testing which attribute sets are unique, and then removing the ones that are not minimal.

   The method
   - Step 1 — identify which single attributes are unique across all rows.
   - Step 2 — every set containing such an attribute is a `super key`.
   - Step 3 — a super key is a `candidate key` only if it is `minimal`: no attribute can be dropped without losing uniqueness.
   - Step 4 — the designer picks one candidate key as the `primary key`.

   Worked example
   ```
   Student
   +------------+-------------+---------------------+-------+-------+
   | student_id | national_id | email               | name  | dept  |
   +------------+-------------+---------------------+-------+-------+
   |    101     | 1234567890  | karim@mail.com      | Karim | CSE   |
   |    102     | 2345678901  | rahim@mail.com      | Rahim | EEE   |
   |    103     | 3456789012  | sumi@mail.com       | Sumi  | CSE   |
   |    104     | 4567890123  | nabil@mail.com      | Karim | BBA   |
   +------------+-------------+---------------------+-------+-------+
   ```

   Step 1 — test each attribute for uniqueness
   ```
   student_id  : 101, 102, 103, 104   -> all different  -> UNIQUE
   national_id : all different                          -> UNIQUE
   email       : all different                          -> UNIQUE
   name        : Karim appears twice                    -> NOT unique
   dept        : CSE appears twice                      -> NOT unique
   ```

   Step 2 — super keys
   ```
   {student_id}
   {national_id}
   {email}
   {student_id, name}
   {student_id, dept}
   {national_id, email}
   {email, name, dept}
   {student_id, national_id, email, name, dept}
   ... and every other set containing at least one unique attribute
   ```

   Step 3 — candidate keys (minimal super keys)
   ```
   {student_id}
   {national_id}
   {email}
   ```
   - `{student_id, name}` is rejected because dropping `name` still gives uniqueness — it is not minimal.
   - `{name, dept}` is not even a super key: Karim/CSE would not distinguish rows if a second Karim joined CSE.

   Step 4 — primary key
   ```
   student_id       (chosen; short, numeric, stable, system-generated)
   Alternate keys: national_id, email
   ```

   A composite example, where no single attribute is unique
   ```
   Enrollment
   +------------+-----------+-------+
   | student_id | course_id | grade |
   +------------+-----------+-------+
   |    101     |   CS101   |   A   |
   |    101     |   CS102   |   B   |
   |    102     |   CS101   |   A   |
   +------------+-----------+-------+

   student_id alone : repeats -> not unique
   course_id  alone : repeats -> not unique
   {student_id, course_id} : unique -> candidate key (composite)
   ```
   - Here the candidate key is `composite`, and it is also the primary key. This is the normal shape of a junction table implementing a many-to-many relationship.

   The counting rule often asked
   - If a relation has one candidate key of size 1 and `n` attributes in total, the number of super keys is `2^(n−1)` — every subset of the remaining n−1 attributes combined with that key.

9. **From Functional Dependency for determine candidate key.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 661 (ET: N/A)]*

   Answer: A candidate key is found from a set of functional dependencies by computing `attribute closures`. The rule is that a set X is a candidate key when `X⁺` contains every attribute of the relation and no proper subset of X has that property.

   The method
   - Step 1 — classify the attributes:
     - appearing `only on the left` of the FDs — must be in every candidate key.
     - appearing `only on the right` — can never be in a candidate key.
     - appearing on `both sides` or in `neither` — may or may not be.
   - Step 2 — start with the attributes that appear only on the left. Compute their closure.
   - Step 3 — if that closure already contains all attributes, it is the only candidate key.
   - Step 4 — otherwise add the "both sides" attributes one at a time and recompute, keeping only the minimal sets.

   Worked example 1
   ```
   R(A, B, C, D)
   FDs: A -> B,  B -> C,  C -> D
   ```
   - `A` appears only on the left, so it must be in every candidate key.
   ```
   A+ = {A}
      A -> B  gives {A, B}
      B -> C  gives {A, B, C}
      C -> D  gives {A, B, C, D}   = all attributes
   ```
   - `Candidate key: {A}`. It is the only one, since no other attribute or set has a closure covering R.

   Worked example 2
   ```
   R(A, B, C, D, E)
   FDs: AB -> C,  C -> D,  D -> A,  E -> B
   ```
   - Attribute `E` appears only on the left of `E -> B` and never on the right, so `E must be in every candidate key`.
   ```
   E+ = {E, B}                      -- not all attributes, so E alone is not a key

   Try {A, E}: A+ ... AE+ = {A,E,B} then AB -> C gives {A,B,C,E}, C -> D gives {A,B,C,D,E}  ✓
   Try {C, E}: CE+ = {C,E,B}, C -> D gives {C,D,E,B}, D -> A gives {A,B,C,D,E}              ✓
   Try {D, E}: DE+ = {D,E,B}, D -> A gives {A,B,D,E}, AB -> C gives {A,B,C,D,E}             ✓
   ```
   - `Candidate keys: {A,E}, {C,E}, {D,E}` — all minimal, all covering R.

   Worked example 3 — the classic exam form
   ```
   R(A, B, C, D, E, F)
   FDs: A -> BC,  CD -> E,  B -> D,  E -> A
   ```
   - `F` appears in no FD at all, so it must be in every candidate key.
   ```
   AF+ = {A,F} -> BC gives {A,B,C,F} -> B->D gives {A,B,C,D,F} -> CD->E gives all  ✓
   BF+ = {B,F} -> D gives {B,D,F}                                -- not all, so not a key
   EF+ = {E,F} -> A gives {A,E,F} -> BC, D ... gives all          ✓
   CDF+ = {C,D,F} -> E gives {C,D,E,F} -> A gives all             ✓
   ```
   - `Candidate keys: {A,F}, {E,F}, {C,D,F}`.

   The closure algorithm itself
   ```
   X+ = X
   repeat:
       for each FD  Y -> Z :
           if Y is a subset of X+ then X+ = X+ ∪ Z
   until X+ stops changing
   ```

   Practical shortcuts
   - An attribute appearing `only on the right` of every FD can never be part of any candidate key.
   - An attribute appearing on `neither` side must be part of `every` candidate key.
   - Always verify `minimality`: after finding a set whose closure is R, check that no proper subset also works.

10. **Relation to find primary key, candidate key, super key.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 663 (ET: N/A)]*

    Answer: All three are found from the same table by testing which attribute sets are unique.

    The definitions
    - `Super key` — any attribute set that uniquely identifies a row; redundant attributes are allowed.
    - `Candidate key` — a `minimal` super key; removing any attribute destroys uniqueness.
    - `Primary key` — the `one` candidate key the designer selects.

    Worked example
    ```
    Employee
    +--------+-------------+-------------------+-------+---------+
    | emp_id | national_id | email             | name  | dept_id |
    +--------+-------------+-------------------+-------+---------+
    |  101   | 1234567890  | karim@mail.com    | Karim |   10    |
    |  102   | 2345678901  | rahim@mail.com    | Rahim |   10    |
    |  103   | 3456789012  | sumi@mail.com     | Sumi  |   20    |
    |  104   | 4567890123  | nabil@mail.com    | Karim |   20    |
    +--------+-------------+-------------------+-------+---------+
    ```

    Step 1 — which single attributes are unique?
    ```
    emp_id      -> all different   -> UNIQUE
    national_id -> all different   -> UNIQUE
    email       -> all different   -> UNIQUE
    name        -> Karim twice     -> not unique
    dept_id     -> 10, 20 repeat   -> not unique
    ```

    Step 2 — super keys
    ```
    {emp_id}, {national_id}, {email}
    {emp_id, name}, {emp_id, dept_id}, {national_id, email}
    {email, name, dept_id}
    {emp_id, national_id, email, name, dept_id}
    ...
    ```
    - Any set containing at least one of the three unique attributes is a super key.

    Step 3 — candidate keys (the minimal super keys)
    ```
    {emp_id}
    {national_id}
    {email}
    ```
    - `{emp_id, name}` fails minimality: `name` can be dropped and uniqueness survives.

    Step 4 — primary key
    ```
    emp_id
    ```
    - Chosen because it is short, numeric, system-generated and never changes. A person can change their email, so `email` is a poor primary key even though it is a valid candidate key.
    - `national_id` and `email` become `alternate keys`, declared UNIQUE.

    In SQL
    ```sql
    CREATE TABLE Employee (
        emp_id      INT PRIMARY KEY,          -- primary key
        national_id VARCHAR(20) UNIQUE,       -- alternate key
        email       VARCHAR(100) UNIQUE,      -- alternate key
        name        VARCHAR(100) NOT NULL,
        dept_id     INT REFERENCES Department(dept_id)   -- foreign key
    );
    ```

    The counting rule
    - If a relation has `n` attributes and a single-attribute candidate key K, the number of super keys is `2^(n−1)`: K combined with any subset of the remaining n−1 attributes. Here n = 5 and there are three such keys, so the count is larger and must be worked out by inclusion-exclusion.

11. **(a) Differentiate among foreign key, candidate key, and primary key.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 694 (ET: N/A)]*

    Answer:

    | Point | Foreign Key | Candidate Key | Primary Key |
    |---|---|---|---|
    | Definition | An attribute referring to another table's primary key | A minimal set of attributes that uniquely identifies a row | The candidate key chosen to identify rows |
    | Uniqueness | Not required | Required | Required |
    | NULL allowed | `Yes` | `No` | `No` |
    | Number per table | Many | One or many | Exactly one |
    | Minimal | Not applicable | `Yes` | Yes |
    | Refers to another table | `Yes` | No | No |
    | Integrity enforced | `Referential` | — | `Entity` |
    | Chosen by | The designer | Determined by the data | The designer, from the candidates |
    | Index created automatically | No, usually manual | Only if declared UNIQUE | Yes, clustered |
    | Purpose | Link two tables | Show which sets could identify rows | Identify each row |

    The relationship between them
    ```
    Super keys  ⊃  Candidate keys  ⊃  Primary key   (all about identifying rows in THIS table)

    Foreign key —  a different concept: it points at another table's primary key
    ```

    Worked example
    ```sql
    CREATE TABLE Department (
        dept_id   INT PRIMARY KEY,
        dept_name VARCHAR(50) NOT NULL UNIQUE
    );

    CREATE TABLE Employee (
        emp_id      INT PRIMARY KEY,          -- PRIMARY KEY (a chosen candidate key)
        national_id VARCHAR(20) UNIQUE,       -- CANDIDATE KEY (alternate)
        email       VARCHAR(100) UNIQUE,      -- CANDIDATE KEY (alternate)
        emp_name    VARCHAR(100) NOT NULL,
        dept_id     INT,
        FOREIGN KEY (dept_id) REFERENCES Department(dept_id)   -- FOREIGN KEY
    );
    ```

    The data, showing the difference in behaviour
    ```
    Department                        Employee
    +---------+-----------+           +--------+----------+---------+
    | dept_id | dept_name |           | emp_id | emp_name | dept_id |
    +---------+-----------+           +--------+----------+---------+
    |   10    | IT        | <-------- |  101   | Karim    |   10    |
    |   20    | HR        | <-------- |  102   | Rahim    |   10    |  repeats — allowed
    +---------+-----------+ <-------- |  103   | Sumi     |   20    |
                                      |  104   | Nabil    |  NULL   |  NULL — allowed
                                      +--------+----------+---------+
    ```
    - `emp_id` (primary key) can neither repeat nor be NULL.
    - `dept_id` (foreign key) can do both, because many employees share a department and a new employee may not yet be assigned one.

    What each prevents
    ```sql
    INSERT INTO Employee VALUES (101, ...);           -- rejected: duplicate primary key
    INSERT INTO Employee VALUES (105, ..., 99);       -- rejected: dept 99 does not exist
    DELETE FROM Department WHERE dept_id = 10;        -- rejected: child rows still refer to it
    ```

12. **Explain the primary key and composite key with respect to database.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 745 (ET: N/A)]*

    Answer:

    Primary key
    - The column or set of columns that `uniquely identifies` each row of a table.
    - Rules: values must be `unique`, may `never be NULL`, and a table has exactly `one`.
    - It enforces `entity integrity` — every row is distinct and identifiable — and is normally given a clustered index automatically.
    ```sql
    CREATE TABLE Student (
        student_id INT PRIMARY KEY,
        name       VARCHAR(100)
    );
    ```

    Composite key
    - A `primary key made of two or more attributes`, used when no single attribute is unique on its own but a combination is.
    - Also called a `compound key`. It follows the same rules as any primary key: the `combination` must be unique, and `none` of its columns may be NULL.
    ```sql
    CREATE TABLE Enrollment (
        student_id INT,
        course_id  INT,
        grade      CHAR(2),
        PRIMARY KEY (student_id, course_id),          -- COMPOSITE KEY
        FOREIGN KEY (student_id) REFERENCES Student(student_id),
        FOREIGN KEY (course_id)  REFERENCES Course(course_id)
    );
    ```

    Why the composite key is needed here
    ```
    Enrollment
    +------------+-----------+-------+
    | student_id | course_id | grade |
    +------------+-----------+-------+
    |    101     |   CS101   |   A   |
    |    101     |   CS102   |   B   |   <- same student, different course
    |    102     |   CS101   |   A   |   <- same course, different student
    +------------+-----------+-------+

    student_id alone : 101 repeats  -> not unique
    course_id  alone : CS101 repeats -> not unique
    {student_id, course_id} : every pair distinct -> unique  ✓
    ```
    - This shape — a junction table implementing a many-to-many relationship — is where composite keys are most often found.

    Comparison

    | Point | Primary key (single column) | Composite key |
    |---|---|---|
    | Number of columns | One | Two or more |
    | Uniqueness | Of that one column | Of the `combination` |
    | NULL | Not allowed | Not allowed in any of the columns |
    | Typical use | Ordinary entity table | Junction table for many-to-many |
    | Foreign keys referring to it | One column | Must repeat all the columns |
    | Index size | Small | Larger, so joins are more costly |

    Practical trade-off
    - A composite key is logically correct but makes every referencing foreign key wider and every join more expensive. Many designers therefore add a `surrogate key` — a single auto-increment `enrollment_id` — as the primary key, and keep `UNIQUE(student_id, course_id)` to preserve the business rule:
    ```sql
    CREATE TABLE Enrollment (
        enrollment_id INT PRIMARY KEY AUTO_INCREMENT,   -- surrogate key
        student_id    INT NOT NULL,
        course_id     INT NOT NULL,
        grade         CHAR(2),
        UNIQUE (student_id, course_id)                  -- the real business rule
    );
    ```

13. **(খ) Relational Database Design এ Primary Key ও Foreign Key বলতে কি বুঝায়? উদাহরণসহ লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 769 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    Primary key
    - The attribute, or set of attributes, that `uniquely identifies` each row of a table.
    - It must be `unique`, can `never be NULL`, and there is exactly `one` per table.
    - It enforces `entity integrity` — the rule that no two rows are identical and every row can be located.
    - In relational database design it is what makes a row addressable, and it is what foreign keys elsewhere point at.

    Foreign key
    - An attribute in one table whose values must match a value of the `primary key` in another table.
    - It enforces `referential integrity` — the rule that a reference must point at something that exists.
    - It `may repeat` and `may be NULL`, and a table may have many foreign keys.
    - It is what actually implements a relationship between two tables in the relational model.

    Example
    ```sql
    CREATE TABLE Department (
        dept_id   INT PRIMARY KEY,                  -- PRIMARY KEY
        dept_name VARCHAR(50) NOT NULL
    );

    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,                   -- PRIMARY KEY of Employee
        emp_name VARCHAR(100) NOT NULL,
        salary   DECIMAL(10,2),
        dept_id  INT,
        FOREIGN KEY (dept_id) REFERENCES Department(dept_id)   -- FOREIGN KEY
    );
    ```

    The data
    ```
    Department (parent)                 Employee (child)
    +---------+-----------+             +--------+----------+---------+
    | dept_id | dept_name |             | emp_id | emp_name | dept_id |
    +---------+-----------+             +--------+----------+---------+
    |   10    | IT        |  <--------  |  101   | Karim    |   10    |
    |   20    | HR        |  <--------  |  102   | Rahim    |   10    |
    +---------+-----------+  <--------  |  103   | Sumi     |   20    |
                                        |  104   | Nabil    |  NULL   |
                                        +--------+----------+---------+
    ```

    What the two constraints prevent
    ```sql
    INSERT INTO Employee VALUES (101, 'Farida', 50000, 10);
       -> rejected: emp_id 101 already exists (primary key violation)

    INSERT INTO Employee VALUES (105, 'Jamil', 40000, 99);
       -> rejected: department 99 does not exist (foreign key violation)

    DELETE FROM Department WHERE dept_id = 10;
       -> rejected: employees still reference it
    ```

    Comparison

    | Point | Primary key | Foreign key |
    |---|---|---|
    | Uniqueness | Required | Not required |
    | NULL | Never | Allowed |
    | Count per table | One | Many |
    | Integrity | Entity | Referential |
    | Points at | Nothing | Another table's primary key |
    | Index | Automatic | Usually manual |

14. **(b) What are purpose of using foreign key in a database? Give suitable example.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 802 (ET: N/A)]*

    Answer:

    Purposes of a foreign key

    1. `Enforcing referential integrity` — the primary purpose
    - It guarantees that a value in the child table actually exists in the parent table. An order cannot refer to a customer who was never created, and an employee cannot belong to a department that does not exist.

    2. `Establishing relationships between tables`
    - The foreign key is what physically implements a one-to-many or many-to-many relationship in the relational model. Without it, the tables are merely separate lists with no connection.

    3. `Preventing orphan records`
    - A parent row cannot be deleted while child rows still refer to it, unless a cascading action is defined. This stops rows being left pointing at nothing.

    4. `Enabling joins`
    - The foreign key is the natural join column, which is how data spread across normalised tables is reassembled.

    5. `Supporting normalisation`
    - Splitting data into separate tables to remove redundancy only works because foreign keys can put it back together. They are what makes 2NF and 3NF practical.

    6. `Documenting the data model`
    - The constraint records the intended relationship in the schema itself, so it is visible to every developer and to design tools, not merely implied by naming.

    7. `Allowing controlled cascading actions`
    - `ON DELETE CASCADE`, `SET NULL` and `RESTRICT` let the designer state what should happen automatically when a parent disappears.

    Example
    ```sql
    CREATE TABLE Department (
        dept_id   INT PRIMARY KEY,
        dept_name VARCHAR(50) NOT NULL
    );

    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,
        emp_name VARCHAR(100) NOT NULL,
        dept_id  INT,
        CONSTRAINT fk_dept FOREIGN KEY (dept_id)
            REFERENCES Department(dept_id)
            ON DELETE SET NULL
            ON UPDATE CASCADE
    );
    ```

    What it prevents in practice
    ```sql
    -- 1. an invalid reference is rejected
    INSERT INTO Employee VALUES (105, 'Jamil', 99);
       -> ERROR: department 99 does not exist

    -- 2. deleting a referenced parent is controlled
    DELETE FROM Department WHERE dept_id = 10;
       -> with the default RESTRICT: rejected
       -> with ON DELETE CASCADE : the employees are deleted too
       -> with ON DELETE SET NULL: the employees' dept_id becomes NULL
    ```

    The referential actions

    | Action | Effect when the parent row is deleted or updated |
    |---|---|
    | `RESTRICT` / `NO ACTION` | The operation is rejected. This is the default |
    | `CASCADE` | The child rows are deleted or updated to match |
    | `SET NULL` | The child's foreign key becomes NULL (the column must allow NULL) |
    | `SET DEFAULT` | The child's foreign key takes its default value |

    - Choosing between them is a design decision: `CASCADE` suits an order and its order-lines, where the lines are meaningless without the order; `SET NULL` suits an employee and a department, where the employee still exists after the department is dissolved.

15. **What is primary key?** *[BCC CA Monitoring System Project 2021 compact it 829 (ET: N/A)]*

    Answer: A `primary key` is the column, or set of columns, that uniquely identifies each row of a table.

    Rules it must satisfy
    - `Unique` — no two rows may hold the same value.
    - `Not NULL` — the value can never be missing, since a row must always be identifiable.
    - `One per table` — a table may have many candidate keys, but only one of them is designated the primary key.
    - `Immutable in practice` — it should never change, because other tables refer to it.

    What it enforces
    - `Entity integrity`: the guarantee that every row in the table is distinct and can be located.

    Example
    ```sql
    CREATE TABLE Student (
        student_id INT PRIMARY KEY,           -- primary key
        name       VARCHAR(100) NOT NULL,
        email      VARCHAR(100) UNIQUE,
        dept_id    INT
    );
    ```
    ```
    Student
    +------------+-------+------------------+
    | student_id | name  | email            |
    +------------+-------+------------------+
    |    101     | Karim | karim@mail.com   |
    |    102     | Rahim | rahim@mail.com   |
    |    103     | Karim | karim2@mail.com  |   <- same name is fine
    +------------+-------+------------------+
    ```
    - Two students may share a name; they may not share a `student_id`.

    Composite primary key
    - When no single column is unique, several are combined:
    ```sql
    CREATE TABLE Enrollment (
        student_id INT,
        course_id  INT,
        grade      CHAR(2),
        PRIMARY KEY (student_id, course_id)
    );
    ```
    - The `combination` must be unique, and none of the columns may be NULL.

    How to choose one
    - Prefer a value that is `short`, `numeric`, `never changes` and is `never NULL`.
    - A `surrogate key` — an auto-increment id generated by the system — is usually better than a `natural key` such as an email address or national ID, because natural values can change, can be entered wrongly, and may carry privacy concerns.

    Primary key vs unique key

    | Point | Primary key | Unique key |
    |---|---|---|
    | NULL allowed | No | Yes, usually one NULL |
    | Number per table | One | Many |
    | Index type | Clustered, by default | Non-clustered |
    | Purpose | Identify the row | Prevent duplicate values in a column |

    - Related terms: a `super key` is any set that identifies a row; a `candidate key` is a minimal super key; the primary key is the candidate key chosen; the remaining candidates are `alternate keys`.

16. **What is Primary key, Unique key and Forgein key.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*

    Answer:

    `Primary key`
    - The column or set of columns that uniquely identifies each row.
    - Must be `unique`, can `never be NULL`, and there is exactly `one` per table.
    - Enforces `entity integrity`, and normally receives a clustered index automatically.

    `Unique key`
    - A constraint that prevents duplicate values in a column, but `allows NULL` (usually one NULL, though SQL Server permits only one and Oracle permits several).
    - A table may have `many` unique keys. They are the candidate keys not chosen as the primary key, also called `alternate keys`.
    - Receives a non-clustered index.

    `Foreign key`
    - A column whose values must exist as the primary key of another table.
    - Enforces `referential integrity`. Values `may repeat` and `may be NULL`, and a table may have many.

    Example
    ```sql
    CREATE TABLE Department (
        dept_id   INT PRIMARY KEY,
        dept_name VARCHAR(50) NOT NULL UNIQUE
    );

    CREATE TABLE Employee (
        emp_id      INT PRIMARY KEY,               -- PRIMARY KEY
        national_id VARCHAR(20) UNIQUE,            -- UNIQUE KEY
        email       VARCHAR(100) UNIQUE,           -- UNIQUE KEY
        emp_name    VARCHAR(100) NOT NULL,
        dept_id     INT,
        FOREIGN KEY (dept_id) REFERENCES Department(dept_id)   -- FOREIGN KEY
    );
    ```

    Comparison

    | Point | Primary key | Unique key | Foreign key |
    |---|---|---|---|
    | Uniqueness | Required | Required | Not required |
    | NULL allowed | `Never` | `Yes` | `Yes` |
    | Number per table | One | Many | Many |
    | Index | Clustered | Non-clustered | Manual |
    | Integrity enforced | Entity | Uniqueness of a column | Referential |
    | Refers to another table | No | No | Yes |
    | Can be a composite | Yes | Yes | Yes |

    The behaviour that distinguishes them
    ```sql
    -- primary key: neither duplicate nor NULL
    INSERT INTO Employee VALUES (101, ...);   -- second time -> rejected, duplicate
    INSERT INTO Employee VALUES (NULL, ...);  -- rejected, NULL not allowed

    -- unique key: duplicates rejected, but NULL accepted
    INSERT INTO Employee (emp_id, national_id) VALUES (105, NULL);   -- accepted
    INSERT INTO Employee (emp_id, national_id) VALUES (106, NULL);   -- accepted in MySQL

    -- foreign key: must exist in the parent
    INSERT INTO Employee (emp_id, dept_id) VALUES (107, 99);   -- rejected if dept 99 absent
    INSERT INTO Employee (emp_id, dept_id) VALUES (108, NULL); -- accepted
    ```

    - The single most examined point: `a primary key is a unique key that additionally forbids NULL and is limited to one per table`.

17. **Database Management System (DBMS) বলতে কী বোঝেন? Relational database -এ Primary key এবং Foreign key -এর ভূমিকা উদাহরণসহ সংক্ষেপে বর্ণনা করুন?** *[41th BCS 2021 compact it 882 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    What is a DBMS
    - A `Database Management System` is software that lets users define, create, store, retrieve, update and manage data in a database, while controlling access to it.
    - It sits between the user or application and the physical data files, so the user never deals with storage directly.

    What a DBMS provides
    - `Data definition` — creating tables, columns, data types and constraints (DDL).
    - `Data manipulation` — inserting, querying, updating and deleting rows (DML).
    - `Data security` — users, roles, privileges and views that restrict what each person can see.
    - `Data integrity` — constraints that keep the data correct and consistent.
    - `Concurrency control` — many users working at once without corrupting each other's work.
    - `Backup and recovery` — restoring the database after a failure.
    - `Transaction management` with the `ACID` properties: Atomicity, Consistency, Isolation, Durability.
    - `Reduced redundancy` and `data independence`, so applications survive changes in storage structure.
    - Examples: MySQL, PostgreSQL, Oracle, SQL Server, MongoDB (NoSQL).

    Role of the primary key in a relational database
    - It `uniquely identifies` each row, so no two rows are indistinguishable and any row can be located.
    - It enforces `entity integrity`: the value can never be NULL and never repeat.
    - It is the target that foreign keys elsewhere point at, so it is what makes relationships possible.
    - It normally carries a clustered index, so lookups and joins on it are fast.

    Role of the foreign key
    - It links a row in one table to a row in another, `implementing the relationship` between them.
    - It enforces `referential integrity`: a value must already exist in the parent table, which prevents orphan records.
    - It permits controlled cascading — `ON DELETE CASCADE` or `SET NULL` — when a parent row is removed.

    Example
    ```sql
    CREATE TABLE Department (
        dept_id   INT PRIMARY KEY,                 -- PRIMARY KEY
        dept_name VARCHAR(50) NOT NULL
    );

    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,                  -- PRIMARY KEY
        emp_name VARCHAR(100) NOT NULL,
        dept_id  INT,
        FOREIGN KEY (dept_id) REFERENCES Department(dept_id)   -- FOREIGN KEY
    );
    ```
    ```
    Department                         Employee
    +---------+-----------+            +--------+----------+---------+
    | dept_id | dept_name |            | emp_id | emp_name | dept_id |
    +---------+-----------+  <-------- |  101   | Karim    |   10    |
    |   10    | IT        |  <-------- |  102   | Rahim    |   10    |
    |   20    | HR        |  <-------- |  103   | Sumi     |   20    |
    +---------+-----------+            +--------+----------+---------+
    ```
    - `emp_id` and `dept_id` (in Department) can neither repeat nor be NULL.
    - `dept_id` in Employee may repeat, because many employees share a department, and may be NULL for someone unassigned.
    - The database will reject an employee whose `dept_id` does not exist, and will refuse to delete a department that still has employees.

18. **(b) Explain the different type of database keys with examples.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)]*

    Answer: A relational database defines several kinds of key, each with a distinct job.

    Example table used throughout
    ```
    Student (student_id, national_id, email, name, dept_id, roll, session)
    ```

    1. `Super key`
    - Any attribute set that uniquely identifies a row. Redundant attributes are allowed.
    ```
    {student_id}, {national_id}, {student_id, name}, {email, dept_id, session}, ...
    ```

    2. `Candidate key`
    - A `minimal` super key — remove any attribute and uniqueness is lost.
    ```
    {student_id}, {national_id}, {email}, {roll, session}
    ```
    - `{student_id, name}` is a super key but not a candidate key, because `name` is unnecessary.

    3. `Primary key`
    - The `one` candidate key chosen to identify rows. Never NULL, never duplicated, one per table.
    ```sql
    student_id INT PRIMARY KEY
    ```

    4. `Alternate key`
    - The candidate keys not chosen as primary. Usually declared UNIQUE.
    ```sql
    national_id VARCHAR(20) UNIQUE,
    email       VARCHAR(100) UNIQUE
    ```

    5. `Composite (compound) key`
    - A key made of two or more attributes, used when no single attribute is unique.
    ```sql
    PRIMARY KEY (roll, session)          -- roll repeats across sessions
    PRIMARY KEY (student_id, course_id)  -- in an Enrollment table
    ```

    6. `Foreign key`
    - An attribute whose values must exist as the primary key of another table. Enforces referential integrity; may repeat and may be NULL.
    ```sql
    dept_id INT REFERENCES Department(dept_id)
    ```

    7. `Surrogate key`
    - A meaningless, system-generated value — usually an auto-increment integer — used as the primary key instead of real-world data.
    ```sql
    student_id INT PRIMARY KEY AUTO_INCREMENT
    ```
    - Preferred because it never changes, is short, and carries no privacy risk.

    8. `Natural key`
    - A key taken from real-world data, such as a national ID or an email address. Meaningful but fragile, because such values can change.

    9. `Unique key`
    - A constraint forbidding duplicates but `allowing NULL`. Several per table.

    10. `Partial (discriminator) key`
    - Used in a `weak entity` to distinguish rows within one parent. It is unique only among the children of the same owner, so the full primary key is the parent's key plus this one.
    ```sql
    CREATE TABLE Dependent (
        emp_id    INT,
        dep_name  VARCHAR(50),           -- partial key
        PRIMARY KEY (emp_id, dep_name),
        FOREIGN KEY (emp_id) REFERENCES Employee(emp_id)
    );
    ```

    The hierarchy
    ```
    Super keys  ⊃  Candidate keys  ⊃  Primary key
                          |
                          +--> the rest become Alternate keys

    Foreign key — separate concept: points at another table's primary key
    ```

    Complete example
    ```sql
    CREATE TABLE Student (
        student_id  INT PRIMARY KEY AUTO_INCREMENT,   -- primary + surrogate
        national_id VARCHAR(20) UNIQUE,               -- alternate + natural
        email       VARCHAR(100) UNIQUE,              -- alternate
        name        VARCHAR(100) NOT NULL,
        roll        INT,
        session     VARCHAR(10),
        dept_id     INT,
        UNIQUE (roll, session),                       -- composite candidate key
        FOREIGN KEY (dept_id) REFERENCES Department(dept_id)   -- foreign key
    );
    ```

19. **What is the Primary key, Candidate key and Super key?** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 921 (ET: N/A)]*

    Answer:

    `Super key`
    - Any set of one or more attributes whose values `uniquely identify` a row. Redundant attributes are permitted, so a table typically has many super keys.

    `Candidate key`
    - A `minimal` super key: removing any attribute from it destroys uniqueness. Every candidate key is a super key, but not conversely.

    `Primary key`
    - The `one` candidate key chosen by the designer to identify rows. It can never be NULL, never repeat, and there is exactly one per table.

    Worked example
    ```
    Employee (emp_id, national_id, email, name, dept_id)
    where emp_id, national_id and email are each unique on their own.
    ```

    Super keys
    ```
    {emp_id}
    {national_id}
    {email}
    {emp_id, name}
    {national_id, dept_id}
    {emp_id, national_id, email, name, dept_id}
    ```

    Candidate keys — the minimal ones
    ```
    {emp_id}
    {national_id}
    {email}
    ```
    - `{emp_id, name}` is rejected: `name` can be dropped and uniqueness survives, so it is not minimal.

    Primary key
    ```
    emp_id
    ```
    - Chosen because it is short, numeric, system-generated and never changes. `national_id` and `email` become `alternate keys`.

    The containment relationship
    ```
    +---------------------------------------------+
    |                SUPER KEYS                   |
    |  +--------------------------------------+   |
    |  |          CANDIDATE KEYS              |   |
    |  |   (minimal super keys)               |   |
    |  |    +----------------------------+    |   |
    |  |    |      PRIMARY KEY           |    |   |
    |  |    |   (the one selected)       |    |   |
    |  |    +----------------------------+    |   |
    |  +--------------------------------------+   |
    +---------------------------------------------+
    ```

    Comparison

    | Point | Super key | Candidate key | Primary key |
    |---|---|---|---|
    | Uniqueness | Yes | Yes | Yes |
    | Minimal | Not necessarily | `Yes` | Yes |
    | Number per table | Many | One or many | Exactly one |
    | NULL allowed | Depends on the columns | No | `Never` |
    | Declared in SQL | No keyword | `UNIQUE` for the alternates | `PRIMARY KEY` |
    | Chosen by | Not chosen — implied by the data | Implied by the data | The designer |

    In SQL
    ```sql
    CREATE TABLE Employee (
        emp_id      INT PRIMARY KEY,        -- primary key
        national_id VARCHAR(20) UNIQUE,     -- alternate (candidate) key
        email       VARCHAR(100) UNIQUE,    -- alternate (candidate) key
        name        VARCHAR(100) NOT NULL,
        dept_id     INT
    );
    ```
    - Note that SQL has no keyword for a super key; only candidate keys (as UNIQUE) and the primary key are declared.

20. **Difference between Primary key and Unique Key, Drop and Purge, Delete and Truncate.** *[RAKUB Assistant Database Administrator 2020 compact it 1013-1014 (ET: E-Zone)]*

    Answer:

    (a) Primary key vs Unique key

    | Point | Primary key | Unique key |
    |---|---|---|
    | NULL allowed | `Never` | `Yes` (one NULL in SQL Server, several in Oracle and MySQL) |
    | Number per table | Exactly one | Many |
    | Index created | `Clustered` by default | `Non-clustered` |
    | Purpose | Identify each row — entity integrity | Prevent duplicate values in a column |
    | Implicit constraints | NOT NULL + UNIQUE | UNIQUE only |
    | Referenced by foreign keys | Normally yes | Possible, but unusual |
    | Relationship | It is a chosen candidate key | The candidate keys not chosen (alternate keys) |

    ```sql
    CREATE TABLE Employee (
        emp_id      INT PRIMARY KEY,          -- unique + not null, one per table
        national_id VARCHAR(20) UNIQUE,       -- unique, but may be NULL
        email       VARCHAR(100) UNIQUE       -- another unique key
    );
    ```

    (b) DROP vs PURGE

    | Point | DROP | PURGE |
    |---|---|---|
    | Effect | Removes the table from the database | Permanently removes it from the recycle bin |
    | Recoverable | Yes in Oracle — it goes to the recycle bin and can be restored with `FLASHBACK TABLE` | `No` — the space is released and the object is gone |
    | Space released | Not immediately in Oracle | Immediately |
    | Syntax | `DROP TABLE Employee;` | `PURGE TABLE Employee;` or `DROP TABLE Employee PURGE;` |

    ```sql
    DROP TABLE Employee;                     -- goes to the recycle bin (Oracle)
    FLASHBACK TABLE Employee TO BEFORE DROP; -- recoverable
    PURGE RECYCLEBIN;                        -- now permanently gone
    DROP TABLE Employee PURGE;               -- drop and purge in one step
    ```
    - This distinction is specific to `Oracle`. MySQL and SQL Server have no recycle bin, so DROP is immediate and irreversible there.

    (c) DELETE vs TRUNCATE

    | Point | DELETE | TRUNCATE |
    |---|---|---|
    | Command type | `DML` | `DDL` |
    | WHERE clause | Supported | Not supported — removes all rows |
    | Rollback | Yes, it is transactional | Normally no (auto-commits in MySQL and Oracle; rollback is possible in SQL Server and PostgreSQL) |
    | Speed | Slow — row by row, each logged | `Fast` — deallocates whole data pages |
    | Triggers fired | `Yes` | `No` |
    | Identity / AUTO_INCREMENT | Not reset | `Reset to the starting value` |
    | Transaction log | One entry per row | Only the page deallocations |
    | Space reclaimed | Not immediately | Immediately |
    | Foreign key references | Allowed | Rejected if the table is referenced by a foreign key |

    ```sql
    DELETE FROM Employee WHERE dept_id = 10;   -- selective, undoable, slow
    DELETE FROM Employee;                       -- all rows, still undoable
    TRUNCATE TABLE Employee;                    -- all rows, fast, resets identity
    DROP TABLE Employee;                        -- rows AND structure gone
    ```

    The three compared in one line each
    - `DELETE` — removes chosen rows; the table and its structure remain.
    - `TRUNCATE` — removes every row quickly; the table and its structure remain.
    - `DROP` — removes the rows, the structure, the indexes and the constraints together.

21. **Example Foreign key in RDBMS.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1035 (ET: BUET)]*

    Answer: A `foreign key` is an attribute in one table whose values must exist as the primary key of another table. It is what implements a relationship in an RDBMS and what enforces `referential integrity`.

    Example — Department and Employee
    ```sql
    CREATE TABLE Department (
        dept_id   INT PRIMARY KEY,
        dept_name VARCHAR(50) NOT NULL
    );

    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,
        emp_name VARCHAR(100) NOT NULL,
        salary   DECIMAL(10,2),
        dept_id  INT,
        CONSTRAINT fk_employee_dept
            FOREIGN KEY (dept_id) REFERENCES Department(dept_id)
    );
    ```

    The data
    ```
    Department (parent / referenced)      Employee (child / referencing)
    +---------+-----------+               +--------+----------+---------+
    | dept_id | dept_name |               | emp_id | emp_name | dept_id |
    +---------+-----------+   <---------- |  101   | Karim    |   10    |
    |   10    | IT        |   <---------- |  102   | Rahim    |   10    |
    |   20    | HR        |   <---------- |  103   | Sumi     |   20    |
    +---------+-----------+               |  104   | Nabil    |  NULL   |
                                          +--------+----------+---------+
    ```
    - `dept_id` in Employee `repeats` (two employees in IT) and may be `NULL` (Nabil is unassigned). Both are allowed for a foreign key, and neither would be allowed for a primary key.

    What the constraint enforces
    ```sql
    -- rejected: department 99 does not exist
    INSERT INTO Employee VALUES (105, 'Jamil', 40000, 99);
       ERROR: Cannot add or update a child row: a foreign key constraint fails

    -- rejected: employees still reference department 10
    DELETE FROM Department WHERE dept_id = 10;
       ERROR: Cannot delete or update a parent row
    ```

    Another example — a many-to-many relationship
    ```sql
    CREATE TABLE Enrollment (
        student_id INT,
        course_id  INT,
        grade      CHAR(2),
        PRIMARY KEY (student_id, course_id),                      -- composite key
        FOREIGN KEY (student_id) REFERENCES Student(student_id),  -- FK 1
        FOREIGN KEY (course_id)  REFERENCES Course(course_id)     -- FK 2
    );
    ```
    - Two foreign keys in one table, which is how a many-to-many relationship is implemented.

    Referential actions
    ```sql
    FOREIGN KEY (dept_id) REFERENCES Department(dept_id)
        ON DELETE CASCADE      -- delete the employees too
        ON UPDATE CASCADE;     -- follow a change of dept_id
    ```

    | Action | Effect on the child when the parent is deleted |
    |---|---|
    | `RESTRICT` / `NO ACTION` | The delete is rejected (default) |
    | `CASCADE` | The child rows are deleted as well |
    | `SET NULL` | The child's foreign key becomes NULL |
    | `SET DEFAULT` | The child's foreign key takes its default |

    - A self-referencing foreign key is also possible and common: `Employee.manager_id REFERENCES Employee(emp_id)` builds a reporting hierarchy inside one table.

22. **What is the difference between primary key and candidate key? Explain the foreign key with an example.** *[Bangladesh Competition Commission Programmer 2019 compact it 1061-1062 (ET: DU)]*

    Answer:

    Primary key vs candidate key

    | Point | Primary key | Candidate key |
    |---|---|---|
    | Definition | The candidate key chosen to identify rows | Any minimal set of attributes that identifies rows uniquely |
    | Number per table | Exactly `one` | `One or many` |
    | NULL allowed | Never | No |
    | Minimal | Yes | Yes |
    | Selected by | The designer | Determined by the data, not chosen |
    | Declared in SQL | `PRIMARY KEY` | `UNIQUE` for the ones not chosen |
    | Index | Clustered, automatically | Non-clustered, if declared UNIQUE |
    | Relationship | It `is` one of the candidate keys | The pool the primary key is drawn from |

    Example
    ```
    Student (student_id, national_id, email, name)

    Candidate keys : {student_id}, {national_id}, {email}
    Primary key    : student_id            <- the designer's choice
    Alternate keys : national_id, email    <- the candidates not chosen
    ```
    ```sql
    CREATE TABLE Student (
        student_id  INT PRIMARY KEY,        -- primary key
        national_id VARCHAR(20) UNIQUE,     -- alternate (candidate) key
        email       VARCHAR(100) UNIQUE,    -- alternate (candidate) key
        name        VARCHAR(100) NOT NULL
    );
    ```
    - In one sentence: `every primary key is a candidate key, but only one candidate key can be the primary key`.

    Foreign key, with an example
    - A `foreign key` is a column in one table whose values must exist as the primary key of another. It enforces `referential integrity` and is what implements a relationship between tables.

    ```sql
    CREATE TABLE Department (
        dept_id   INT PRIMARY KEY,
        dept_name VARCHAR(50) NOT NULL
    );

    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,
        emp_name VARCHAR(100) NOT NULL,
        dept_id  INT,
        FOREIGN KEY (dept_id) REFERENCES Department(dept_id)
    );
    ```
    ```
    Department                        Employee
    +---------+-----------+           +--------+----------+---------+
    | dept_id | dept_name |  <------- | emp_id | emp_name | dept_id |
    +---------+-----------+  <------- +--------+----------+---------+
    |   10    | IT        |           |  101   | Karim    |   10    |
    |   20    | HR        |           |  102   | Rahim    |   10    |   repeats
    +---------+-----------+           |  103   | Nabil    |  NULL   |   NULL allowed
                                      +--------+----------+---------+
    ```

    What it enforces
    ```sql
    INSERT INTO Employee VALUES (104, 'Jamil', 99);
       -> rejected: department 99 does not exist

    DELETE FROM Department WHERE dept_id = 10;
       -> rejected: employees still reference it
    ```
    - Unlike a primary key, a foreign key `may repeat` and `may be NULL`, and a table may have several of them.

23. **(খ) Candidate key and Composite key কাকে বলে?** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1069 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    `Candidate key`
    - Any `minimal` set of attributes that uniquely identifies a row in a relation. Minimal means no attribute can be removed without losing uniqueness.
    - A table may have several candidate keys; the designer selects one as the `primary key`, and the rest become `alternate keys`.
    - Every candidate key is a super key; not every super key is a candidate key.

    Example
    ```
    Student (student_id, national_id, email, name)

    Candidate keys : {student_id}, {national_id}, {email}
    Not a candidate key: {student_id, name}   -- 'name' is redundant, so not minimal
    ```

    `Composite key`
    - A key made of `two or more attributes` combined, used when no single attribute is unique on its own but the combination is. Also called a compound key.
    - It follows the same rules as any primary key: the combination must be unique and none of its columns may be NULL.

    Example
    ```
    Enrollment
    +------------+-----------+-------+
    | student_id | course_id | grade |
    +------------+-----------+-------+
    |    101     |   CS101   |   A   |
    |    101     |   CS102   |   B   |    same student, different course
    |    102     |   CS101   |   A   |    same course, different student
    +------------+-----------+-------+

    student_id alone : repeats -> not unique
    course_id  alone : repeats -> not unique
    {student_id, course_id}    -> unique  ✓  composite key
    ```

    ```sql
    CREATE TABLE Enrollment (
        student_id INT,
        course_id  INT,
        grade      CHAR(2),
        PRIMARY KEY (student_id, course_id),      -- composite key
        FOREIGN KEY (student_id) REFERENCES Student(student_id),
        FOREIGN KEY (course_id)  REFERENCES Course(course_id)
    );
    ```

    Relationship between the two
    - A composite key `can also be` a candidate key — in the Enrollment table, `{student_id, course_id}` is both.
    - The two terms answer different questions: `candidate key` is about `minimality and uniqueness`; `composite key` is about `how many columns` it contains.

    | Point | Candidate key | Composite key |
    |---|---|---|
    | Defined by | Minimality and uniqueness | Having more than one column |
    | Columns | One or more | Always two or more |
    | Number per table | One or many | Depends |
    | Can be the primary key | Yes | Yes |
    | Example | {student_id} | {student_id, course_id} |

    - Where composite keys appear: junction tables for many-to-many relationships, weak entities (owner key plus partial key), and any natural key that needs several attributes such as `{roll, session, department}`.

24. **(b) What happens when someone tries to delete an entry of a table that has referential integrity constraint? Explain with example.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1136-1138 (ET: N/A)]*

    Answer: What happens depends on the `referential action` declared on the foreign key. By default the delete is `rejected`.

    The situation
    ```sql
    CREATE TABLE Department (
        dept_id   INT PRIMARY KEY,
        dept_name VARCHAR(50)
    );

    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,
        emp_name VARCHAR(100),
        dept_id  INT,
        FOREIGN KEY (dept_id) REFERENCES Department(dept_id)
    );
    ```
    ```
    Department                    Employee
    +---------+-----------+       +--------+----------+---------+
    | dept_id | dept_name |       | emp_id | emp_name | dept_id |
    +---------+-----------+       +--------+----------+---------+
    |   10    | IT        |  <--- |  101   | Karim    |   10    |
    |   20    | HR        |  <--- |  102   | Rahim    |   10    |
    +---------+-----------+  <--- |  103   | Sumi     |   20    |
                                  +--------+----------+---------+
    ```

    Attempting the delete
    ```sql
    DELETE FROM Department WHERE dept_id = 10;
    ```

    1. `RESTRICT` / `NO ACTION` — the default
    ```
    ERROR 1451 (23000): Cannot delete or update a parent row:
    a foreign key constraint fails (`Employee`, CONSTRAINT `fk_dept`
    FOREIGN KEY (`dept_id`) REFERENCES `Department` (`dept_id`))
    ```
    - The delete is refused, and nothing changes. This protects the data from becoming inconsistent, since Karim and Rahim would otherwise point at a department that no longer exists — an `orphan record`.

    2. `ON DELETE CASCADE`
    ```sql
    FOREIGN KEY (dept_id) REFERENCES Department(dept_id) ON DELETE CASCADE
    ```
    - The department is deleted `and so are Karim and Rahim`.
    ```
    Employee after
    +--------+----------+---------+
    | emp_id | emp_name | dept_id |
    +--------+----------+---------+
    |  103   | Sumi     |   20    |
    +--------+----------+---------+
    ```
    - Powerful but dangerous: it can delete far more than intended, and cascades can chain through several tables.

    3. `ON DELETE SET NULL`
    ```sql
    FOREIGN KEY (dept_id) REFERENCES Department(dept_id) ON DELETE SET NULL
    ```
    - The department is deleted and the children survive with `dept_id` set to NULL.
    ```
    +--------+----------+---------+
    | emp_id | emp_name | dept_id |
    +--------+----------+---------+
    |  101   | Karim    |  NULL   |
    |  102   | Rahim    |  NULL   |
    |  103   | Sumi     |   20    |
    +--------+----------+---------+
    ```
    - The column must allow NULL for this to be legal.

    4. `ON DELETE SET DEFAULT`
    - The child's foreign key takes its declared default value. Supported by PostgreSQL and SQL Server, not by MySQL's InnoDB.

    Summary

    | Action | Parent row | Child rows |
    |---|---|---|
    | RESTRICT / NO ACTION | Not deleted | Unchanged — the operation fails |
    | CASCADE | Deleted | Deleted too |
    | SET NULL | Deleted | Kept, foreign key becomes NULL |
    | SET DEFAULT | Deleted | Kept, foreign key takes its default |

    Choosing between them
    - `CASCADE` fits a genuine ownership relationship — an order and its order-lines, where a line has no meaning without its order.
    - `SET NULL` fits an association — an employee still exists after their department is dissolved.
    - `RESTRICT` is the safe default, forcing the application to deal with the children deliberately.

    Working around a RESTRICT manually
    ```sql
    UPDATE Employee SET dept_id = NULL WHERE dept_id = 10;   -- or reassign them
    DELETE FROM Department WHERE dept_id = 10;                -- now succeeds
    ```
    - The same rules apply to `ON UPDATE` when the parent's primary key value changes.

25. **What is foreign key? When foreign key used?** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1152 (ET: KUET)]*

    Answer:

    What is a foreign key
    - A `foreign key` is a column, or set of columns, in one table whose values must match a `primary key` value in another table (or be NULL).
    - The table containing it is the `child` or referencing table; the table it points at is the `parent` or referenced table.
    - It enforces `referential integrity` — the guarantee that a reference points at a row that actually exists.

    Properties
    - Values `may repeat`, since many children can share one parent.
    - Values `may be NULL`, meaning "not related to anything yet", unless declared NOT NULL.
    - A table may have `many` foreign keys.
    - It must reference a primary key or a unique key in the parent table.

    ```sql
    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,
        emp_name VARCHAR(100),
        dept_id  INT,
        FOREIGN KEY (dept_id) REFERENCES Department(dept_id)
    );
    ```

    When a foreign key is used

    1. `To implement a one-to-many relationship` — the commonest case. The foreign key goes in the `many` side.
    ```
    Department (1) ----< Employee (many)      Employee.dept_id -> Department.dept_id
    Customer   (1) ----< Order    (many)      Order.cust_id    -> Customer.cust_id
    ```

    2. `To implement a many-to-many relationship`, through a junction table holding two foreign keys.
    ```sql
    CREATE TABLE Enrollment (
        student_id INT,
        course_id  INT,
        PRIMARY KEY (student_id, course_id),
        FOREIGN KEY (student_id) REFERENCES Student(student_id),
        FOREIGN KEY (course_id)  REFERENCES Course(course_id)
    );
    ```

    3. `To implement a self-referencing hierarchy` — a manager is also an employee.
    ```sql
    manager_id INT REFERENCES Employee(emp_id)
    ```

    4. `To support normalisation` — splitting a table to remove redundancy only works if foreign keys can rejoin the pieces.

    5. `To prevent orphan records` — the parent cannot be deleted while children still refer to it, unless a cascading action is defined.

    6. `To document the data model` — the constraint records the intended relationship in the schema itself.

    7. `To enable reliable joins` — the foreign key is the natural join column.

    What it enforces in practice
    ```sql
    INSERT INTO Employee VALUES (105, 'Jamil', 99);
       -> rejected: department 99 does not exist

    DELETE FROM Department WHERE dept_id = 10;
       -> rejected by default; or cascades / sets NULL if so declared
    ```

    When `not` to use one
    - In a data warehouse or a bulk-load staging table, foreign keys are sometimes omitted because the integrity check slows every insert, and the data is validated in the ETL process instead. Some very-high-volume OLTP systems do the same and enforce integrity in the application — a deliberate trade of safety for speed.

26. **Difference between primary key, foreign key and candidate key.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1162 (ET: N/A)]*

    Answer:

    | Point | Primary Key | Foreign Key | Candidate Key |
    |---|---|---|---|
    | Definition | The candidate key chosen to identify each row | A column referencing another table's primary key | A minimal set of attributes that uniquely identifies a row |
    | Uniqueness | Required | Not required | Required |
    | NULL allowed | `Never` | `Yes` | `No` |
    | Number per table | Exactly one | Many | One or many |
    | Minimal | Yes | Not applicable | Yes |
    | Refers to another table | No | `Yes` | No |
    | Integrity enforced | `Entity integrity` | `Referential integrity` | — |
    | SQL declaration | `PRIMARY KEY` | `FOREIGN KEY ... REFERENCES` | `UNIQUE` for the alternates |
    | Index | Clustered, automatic | Usually manual | Non-clustered if UNIQUE |
    | Chosen by | The designer | The designer | Determined by the data |
    | Can be composite | Yes | Yes | Yes |

    The relationship
    ```
    Super keys ⊃ Candidate keys ⊃ Primary key      (identify rows in THIS table)
                        |
                        +--> the unchosen ones become Alternate keys

    Foreign key — points OUT, at another table's primary key
    ```

    Worked example
    ```sql
    CREATE TABLE Department (
        dept_id   INT PRIMARY KEY,
        dept_name VARCHAR(50) NOT NULL UNIQUE
    );

    CREATE TABLE Employee (
        emp_id      INT PRIMARY KEY,        -- PRIMARY KEY (a chosen candidate key)
        national_id VARCHAR(20) UNIQUE,     -- CANDIDATE KEY (alternate)
        email       VARCHAR(100) UNIQUE,    -- CANDIDATE KEY (alternate)
        emp_name    VARCHAR(100) NOT NULL,
        dept_id     INT,
        FOREIGN KEY (dept_id) REFERENCES Department(dept_id)   -- FOREIGN KEY
    );
    ```
    ```
    Department                       Employee
    +---------+-----------+          +--------+-------------+----------+---------+
    | dept_id | dept_name |  <-----  | emp_id | national_id | emp_name | dept_id |
    +---------+-----------+  <-----  +--------+-------------+----------+---------+
    |   10    | IT        |          |  101   | 1234567890  | Karim    |   10    |
    |   20    | HR        |          |  102   | 2345678901  | Rahim    |   10    |
    +---------+-----------+          |  103   | 3456789012  | Nabil    |  NULL   |
                                     +--------+-------------+----------+---------+
    ```
    - `emp_id` never repeats and is never NULL. `dept_id` does both, which is exactly what distinguishes a foreign key from a primary key.
    - `national_id` and `email` are candidate keys that were not chosen, so they are declared UNIQUE rather than PRIMARY KEY.

    Three sentences to remember
    - A `candidate key` is any minimal way of identifying a row.
    - The `primary key` is the one candidate key the designer picks.
    - A `foreign key` does not identify rows at all — it links this table to another.

27. **Define weak Entity? What are the difference between primary key and super key?** *[Palli Sanchay Bank Programmer 2018 compact it 1171 (ET: N/A)]*

    Answer:

    Weak entity
    - A `weak entity` is an entity that `cannot be uniquely identified by its own attributes alone`. It depends on another entity, called the `owner` or `identifying entity`, for its identity.
    - It has a `partial key` (also called a discriminator) that distinguishes it only `among the children of the same owner`. Its full primary key is the owner's primary key plus that partial key.
    - It participates in an `identifying relationship` with its owner, and that participation is `total` — a weak entity cannot exist without its owner.
    - If the owner is deleted, its weak entities must be deleted too.

    ER notation
    ```
    +-----------+        /------------\        +==========+
    | Employee  |=======<  Has         >=======| Dependent|
    +-----------+        \------------/        +==========+
      (strong)          identifying relationship  (weak — double rectangle)
                         (double diamond)
    ```
    - Double rectangle for the weak entity, double diamond for the identifying relationship, and a dashed underline for the partial key.

    Example
    ```sql
    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,                 -- strong entity
        emp_name VARCHAR(100)
    );

    CREATE TABLE Dependent (
        emp_id       INT,                         -- owner's key
        dep_name     VARCHAR(50),                 -- PARTIAL KEY
        relationship VARCHAR(20),
        PRIMARY KEY (emp_id, dep_name),           -- composite primary key
        FOREIGN KEY (emp_id) REFERENCES Employee(emp_id) ON DELETE CASCADE
    );
    ```
    ```
    Dependent
    +--------+----------+--------------+
    | emp_id | dep_name | relationship |
    +--------+----------+--------------+
    |  101   | Rina     | Daughter     |
    |  101   | Sabbir   | Son          |
    |  102   | Rina     | Daughter     |   <- same name, different employee: allowed
    +--------+----------+--------------+
    ```
    - `dep_name` alone is not unique — two employees may both have a daughter named Rina. Only `{emp_id, dep_name}` identifies a row.
    - Other typical weak entities: order-lines belonging to an order, room numbers within a hotel, and chapter numbers within a book.

    Primary key vs super key

    | Point | Primary key | Super key |
    |---|---|---|
    | Minimality | `Must be minimal` | May contain redundant attributes |
    | Number per table | Exactly one | Usually many |
    | NULL allowed | Never | Depends on the columns |
    | Chosen by | The designer | Not chosen; implied by the data |
    | SQL keyword | `PRIMARY KEY` | None exists |
    | Index | Created automatically | None |
    | Relationship | Every primary key is a super key | Not every super key is a primary key |

    Example
    ```
    Student (student_id, national_id, email, name)

    Super keys   : {student_id}, {student_id, name}, {national_id, email, name}, ...
    Candidate keys (minimal super keys): {student_id}, {national_id}, {email}
    Primary key  : student_id
    ```
    - `{student_id, name}` is a super key but cannot be the primary key, because dropping `name` still gives uniqueness — it fails the minimality test.

28. **Difference between Super Key and UNIQUE key?** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1174 (ET: N/A)]*

    Answer:

    | Point | Super Key | Unique Key |
    |---|---|---|
    | Nature | A `theoretical` concept from the relational model | A `practical` SQL constraint |
    | Definition | Any attribute set that uniquely identifies a row | A constraint forbidding duplicate values in a column or set of columns |
    | Minimality | Not required — redundant attributes allowed | Not required either, but usually minimal in practice |
    | NULL allowed | Depends on the columns involved | `Yes` — one NULL in SQL Server, several in MySQL and Oracle |
    | Declared in SQL | `No keyword exists` | `UNIQUE` |
    | Number per table | Many, often very many | Many |
    | Index created | None — it is not a physical object | `Non-clustered index` created automatically |
    | Enforced by the DBMS | No | `Yes` |
    | Purpose | To reason about identification during design | To prevent duplicate data at run time |
    | Can be referenced by a foreign key | Not as such | Yes |

    Example
    ```
    Student (student_id, national_id, email, name, phone)
    ```

    Super keys — a design-time concept
    ```
    {student_id}
    {national_id}
    {email}
    {student_id, name}
    {national_id, phone}
    {student_id, national_id, email, name, phone}
    ```
    - All of these identify a row uniquely. None of them is declared anywhere in SQL; they exist only as a property of the data.

    Unique keys — what is actually written
    ```sql
    CREATE TABLE Student (
        student_id  INT PRIMARY KEY,          -- primary key
        national_id VARCHAR(20) UNIQUE,       -- UNIQUE KEY
        email       VARCHAR(100) UNIQUE,      -- UNIQUE KEY
        name        VARCHAR(100),
        phone       VARCHAR(15),
        UNIQUE (name, phone)                  -- composite UNIQUE KEY
    );
    ```

    The behaviour that distinguishes them
    ```sql
    -- unique key rejects duplicates
    INSERT INTO Student (student_id, email) VALUES (101, 'a@mail.com');
    INSERT INTO Student (student_id, email) VALUES (102, 'a@mail.com');
       -> ERROR: Duplicate entry for key 'email'

    -- but accepts NULL
    INSERT INTO Student (student_id, email) VALUES (103, NULL);
    INSERT INTO Student (student_id, email) VALUES (104, NULL);
       -> both accepted in MySQL, because NULL is not equal to NULL
    ```

    The key relationship
    - A `unique key` is the SQL mechanism used to `enforce` a candidate key, and every candidate key is a minimal super key. So a unique key is the practical implementation of the theoretical idea, restricted to the minimal cases that are worth enforcing.
    - One important difference remains: a super key by definition cannot have NULLs in a way that breaks identification, whereas a unique key in SQL tolerates NULLs precisely because SQL treats NULL as "unknown" rather than as a value.

29. **Define Super key and Primary key.** *[Jiban Bima Corporation Assistant Programmer 2018 compact it 1211 (ET: N/A)]*

    Answer:

    `Super key`
    - Any set of one or more attributes whose values `uniquely identify` a row in a relation.
    - It may contain `redundant` attributes — adding any attribute to a super key produces another super key — so a table typically has many of them.
    - It is a design-time concept from the relational model, with no SQL keyword of its own.

    `Primary key`
    - The `one` candidate key chosen by the designer to identify rows in a table.
    - It must be `unique`, can `never be NULL`, and there is exactly one per table.
    - It must be `minimal` — no attribute can be removed from it.
    - It enforces `entity integrity`, is declared with `PRIMARY KEY`, and normally receives a clustered index.

    Worked example
    ```
    Student (student_id, national_id, email, name, phone)
    where student_id, national_id and email are each unique on their own.
    ```

    Super keys
    ```
    {student_id}
    {national_id}
    {email}
    {student_id, name}
    {student_id, national_id}
    {email, phone, name}
    {student_id, national_id, email, name, phone}
    ```

    Primary key
    ```
    student_id
    ```

    Why `{student_id, name}` is a super key but not a primary key
    - It identifies a row uniquely, so it satisfies the super key definition.
    - But `name` is unnecessary — `student_id` alone suffices — so it is not minimal, and a primary key must be minimal.

    The containment relationship
    ```
    +---------------------------------------------+
    |                SUPER KEYS                   |
    |  +--------------------------------------+   |
    |  |         CANDIDATE KEYS               |   |
    |  |     (the minimal super keys)         |   |
    |  |    +----------------------------+    |   |
    |  |    |       PRIMARY KEY          |    |   |
    |  |    |    (the one selected)      |    |   |
    |  |    +----------------------------+    |   |
    |  +--------------------------------------+   |
    +---------------------------------------------+
    ```

    Comparison

    | Point | Super key | Primary key |
    |---|---|---|
    | Minimal | Not necessarily | `Required` |
    | Number per table | Many | Exactly one |
    | NULL | Depends on the columns | Never |
    | SQL keyword | None | `PRIMARY KEY` |
    | Index | None | Automatic |
    | Chosen | No — implied by the data | Yes — by the designer |

    - In one line: `every primary key is a super key, but a super key becomes a primary key only if it is minimal and is the one the designer selects`.

30. **What are the difference among Candidate key, Primary key and Foreign key?** *[Investment Corporation Bangladesh Assistant Programmer 2017 compact it 1216 (ET: N/A)]*

    Answer:

    | Point | Candidate Key | Primary Key | Foreign Key |
    |---|---|---|---|
    | Definition | A minimal set of attributes uniquely identifying a row | The candidate key chosen for identification | A column referencing another table's primary key |
    | Uniqueness | Required | Required | Not required |
    | NULL allowed | `No` | `Never` | `Yes` |
    | Number per table | One or many | Exactly one | Many |
    | Minimal | Yes | Yes | Not applicable |
    | Refers to another table | No | No | `Yes` |
    | Integrity enforced | — | `Entity` | `Referential` |
    | SQL declaration | `UNIQUE` (for alternates) | `PRIMARY KEY` | `FOREIGN KEY ... REFERENCES` |
    | Index | Non-clustered if declared | Clustered, automatic | Usually manual |
    | Selected by | Determined by the data | The designer | The designer |

    Worked example
    ```sql
    CREATE TABLE Department (
        dept_id   INT PRIMARY KEY,
        dept_name VARCHAR(50) NOT NULL UNIQUE
    );

    CREATE TABLE Student (
        student_id  INT PRIMARY KEY,          -- PRIMARY KEY  (chosen candidate)
        national_id VARCHAR(20) UNIQUE,       -- CANDIDATE KEY (alternate)
        email       VARCHAR(100) UNIQUE,      -- CANDIDATE KEY (alternate)
        name        VARCHAR(100) NOT NULL,
        dept_id     INT,
        FOREIGN KEY (dept_id) REFERENCES Department(dept_id)   -- FOREIGN KEY
    );
    ```

    The data
    ```
    Department                       Student
    +---------+-----------+          +------------+-------------+-------+---------+
    | dept_id | dept_name |  <-----  | student_id | national_id | name  | dept_id |
    +---------+-----------+  <-----  +------------+-------------+-------+---------+
    |   10    | CSE       |          |    101     | 1234567890  | Karim |   10    |
    |   20    | EEE       |          |    102     | 2345678901  | Rahim |   10    |
    +---------+-----------+          |    103     | 3456789012  | Sumi  |  NULL   |
                                     +------------+-------------+-------+---------+
    ```

    Behaviour that separates them
    ```sql
    INSERT INTO Student VALUES (101, ...);        -- rejected: duplicate primary key
    INSERT INTO Student VALUES (104, NULL, ...);  -- accepted: national_id UNIQUE allows NULL
    INSERT INTO Student (student_id, dept_id) VALUES (105, 99);
                                                  -- rejected: department 99 does not exist
    ```

    The relationship in three lines
    - `Candidate keys` are all the minimal ways of identifying a row — determined by the data, not chosen.
    - The `primary key` is the single candidate key the designer selects; the rest become alternate keys, declared UNIQUE.
    - The `foreign key` is a different kind of thing altogether: it does not identify rows in its own table, but links them to rows in another.

31. **Explain with examples: Candidate key, foreign key and horizontal scaling.** *[Agrani Bank Ltd. Senior Officer (IT) 2017 compact it 1223 (ET: N/A)]*

    Answer:

    Candidate key
    - A `minimal` set of attributes that uniquely identifies a row in a relation. Minimal means no attribute can be dropped without losing uniqueness.
    - A table may have several; the designer picks one as the primary key and declares the rest `UNIQUE`.
    ```
    Student (student_id, national_id, email, name)

    Candidate keys : {student_id}, {national_id}, {email}
    Not a candidate key: {student_id, name}   -- 'name' is redundant
    ```
    ```sql
    CREATE TABLE Student (
        student_id  INT PRIMARY KEY,        -- chosen candidate key
        national_id VARCHAR(20) UNIQUE,     -- alternate candidate key
        email       VARCHAR(100) UNIQUE,    -- alternate candidate key
        name        VARCHAR(100) NOT NULL
    );
    ```

    Foreign key
    - A column in one table whose values must exist as the `primary key` of another table. It enforces `referential integrity` and is what implements a relationship between tables.
    - Values `may repeat` and `may be NULL`, and a table may have many.
    ```sql
    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,
        emp_name VARCHAR(100),
        dept_id  INT,
        FOREIGN KEY (dept_id) REFERENCES Department(dept_id)
    );
    ```
    ```
    Department                   Employee
    +---------+-----------+      +--------+----------+---------+
    | dept_id | dept_name | <--- | emp_id | emp_name | dept_id |
    +---------+-----------+ <--- +--------+----------+---------+
    |   10    | IT        |      |  101   | Karim    |   10    |
    |   20    | HR        |      |  102   | Rahim    |   10    |  repeats
    +---------+-----------+      |  103   | Sumi     |  NULL   |  NULL allowed
                                 +--------+----------+---------+
    ```
    - Inserting an employee with `dept_id = 99` is rejected, because no such department exists.

    Horizontal scaling
    - `Horizontal scaling` (scaling `out`) means adding `more machines` to share the load, rather than making one machine bigger.
    - The contrast is `vertical scaling` (scaling `up`): adding more CPU, RAM or disk to a single server.

    ```
    VERTICAL SCALING (scale up)          HORIZONTAL SCALING (scale out)

         +-----------+                    +------+  +------+  +------+
         |  Server   |                    |Server|  |Server|  |Server|
         |  8 CPU    |  ->  16 CPU        |  1   |  |  2   |  |  3   |
         |  32 GB    |      128 GB        +------+  +------+  +------+
         +-----------+                         \      |      /
                                                [Load balancer]
    ```

    | Point | Vertical scaling | Horizontal scaling |
    |---|---|---|
    | Method | Bigger machine | More machines |
    | Limit | Hardware ceiling | Practically unlimited |
    | Cost | Rises steeply at the high end | Commodity hardware, linear |
    | Downtime to scale | Usually required | None — add a node |
    | Fault tolerance | Single point of failure | Redundant by design |
    | Complexity | Simple | Needs load balancing, replication, sharding |
    | Data consistency | Easy | Hard — this is the real cost |

    - In databases, horizontal scaling is achieved by `sharding` (splitting rows across servers) and `replication` (copies for read scaling). NoSQL systems such as MongoDB and Cassandra were designed for it, while traditional relational databases scale vertically more naturally, which is one of the main reasons NoSQL emerged.

32. **Write down the differences between super key and candidate key with example.** *[Agrani Bank Ltd. Officer (ICT) 2017 compact it 1225 (ET: N/A)]*

    Answer:

    | Point | Super Key | Candidate Key |
    |---|---|---|
    | Definition | Any attribute set that uniquely identifies a row | A `minimal` super key |
    | Minimality | `Not required` — redundant attributes allowed | `Required` — no attribute can be removed |
    | Number per table | Many, often very many | Fewer; one or a handful |
    | Relationship | The superset | A subset of the super keys |
    | Contains extra attributes | Possibly | Never |
    | Chosen as primary key | Only if it is also a candidate key | One of them is chosen |
    | SQL declaration | No keyword exists | `PRIMARY KEY` or `UNIQUE` |
    | Nature | Theoretical, used in design | Practical, enforced by the DBMS |

    Worked example
    ```
    Employee (emp_id, national_id, email, name, dept_id)

    Assume emp_id, national_id and email are each unique on their own.
    ```

    Super keys
    ```
    {emp_id}
    {national_id}
    {email}
    {emp_id, name}
    {emp_id, national_id}
    {national_id, dept_id, name}
    {emp_id, national_id, email, name, dept_id}
    ```
    - Every one of these identifies a row uniquely. Most carry attributes that are not needed for that purpose.

    Candidate keys — only the minimal ones survive
    ```
    {emp_id}
    {national_id}
    {email}
    ```

    Why the others are excluded
    ```
    {emp_id, name}           -> drop 'name'  -> still unique -> NOT minimal -> not a candidate key
    {national_id, dept_id}   -> drop 'dept_id' -> still unique -> NOT minimal
    {name, dept_id}          -> not unique at all -> not even a super key
    ```

    The containment picture
    ```
    +-----------------------------------------------+
    |                 SUPER KEYS                    |
    |   (any set that identifies a row uniquely)    |
    |                                               |
    |   +---------------------------------------+   |
    |   |          CANDIDATE KEYS               |   |
    |   |     (the minimal super keys)          |   |
    |   |   {emp_id}, {national_id}, {email}    |   |
    |   +---------------------------------------+   |
    +-----------------------------------------------+
    ```

    The counting rule
    - If a relation has `n` attributes and exactly one single-attribute candidate key K, the number of super keys is `2^(n−1)` — K combined with any subset of the other n−1 attributes.
    - Example: `R(A, B, C, D)` with candidate key `{A}` has 2³ = `8` super keys: {A}, {A,B}, {A,C}, {A,D}, {A,B,C}, {A,B,D}, {A,C,D}, {A,B,C,D}.

    - In one sentence: `every candidate key is a super key, but a super key is a candidate key only when nothing can be removed from it`.

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

    Answer:

    Primary key
    - The column, or set of columns, that `uniquely identifies` each row of a table.
    - Rules: values must be `unique`, may `never be NULL`, and there is exactly `one` per table.
    - It enforces `entity integrity` — the guarantee that every row is distinct and can be located — and normally carries a clustered index.
    - It is the value that foreign keys in other tables point at.

    Foreign key
    - A column in one table whose values must match a `primary key` value in another table.
    - It enforces `referential integrity` — the guarantee that a reference points at a row that exists.
    - Values `may repeat` and `may be NULL`, and a table may have several foreign keys.
    - It is what physically implements a relationship between two tables.

    Example
    ```sql
    CREATE TABLE Department (
        dept_id   INT PRIMARY KEY,               -- PRIMARY KEY
        dept_name VARCHAR(50) NOT NULL
    );

    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,                -- PRIMARY KEY of this table
        emp_name VARCHAR(100) NOT NULL,
        dept_id  INT,
        FOREIGN KEY (dept_id) REFERENCES Department(dept_id)   -- FOREIGN KEY
    );
    ```
    ```
    Department (parent)             Employee (child)
    +---------+-----------+         +--------+----------+---------+
    | dept_id | dept_name |  <----- | emp_id | emp_name | dept_id |
    +---------+-----------+  <----- +--------+----------+---------+
    |   10    | IT        |         |  101   | Karim    |   10    |
    |   20    | HR        |         |  102   | Rahim    |   10    |   repeats
    +---------+-----------+         |  103   | Sumi     |  NULL   |   NULL allowed
                                    +--------+----------+---------+
    ```

    What each prevents
    ```sql
    INSERT INTO Employee VALUES (101, 'Farida', 10);
       -> rejected: emp_id 101 already exists (primary key violation)

    INSERT INTO Employee VALUES (104, 'Jamil', 99);
       -> rejected: department 99 does not exist (foreign key violation)

    DELETE FROM Department WHERE dept_id = 10;
       -> rejected by default: employees still reference it
    ```

    Comparison

    | Point | Primary key | Foreign key |
    |---|---|---|
    | Uniqueness | Required | Not required |
    | NULL | Never | Allowed |
    | Number per table | One | Many |
    | Integrity | Entity | Referential |
    | Points at | Nothing | Another table's primary key |
    | Index | Automatic and clustered | Usually created manually |

    - A foreign key may also point back into its own table — `Employee.manager_id REFERENCES Employee(emp_id)` — which is how a reporting hierarchy is stored in a single table.

34. **Define ‘integrity rules’ of database systems. Write a SQL query to get the second highest salary from Employee table.** *[Bangladesh Bank Assistant Programmer 2016 compact it 1265 (ET: N/A)]*

    Answer:

    Integrity rules of a database system

    Integrity rules are the constraints that keep the data `accurate, consistent and valid` at all times. There are three fundamental categories.

    1. `Entity integrity`
    - Every table must have a `primary key`, and no part of that primary key may be `NULL`.
    - Reason: a row that cannot be identified cannot be referenced, updated or deleted reliably.
    ```sql
    student_id INT PRIMARY KEY        -- implies UNIQUE + NOT NULL
    ```

    2. `Referential integrity`
    - A `foreign key` value must either match an existing primary key value in the referenced table, or be entirely NULL.
    - Reason: it prevents `orphan records` — a row pointing at something that does not exist.
    ```sql
    FOREIGN KEY (dept_id) REFERENCES Department(dept_id)
    ```
    - It also governs what happens when the parent is deleted: `RESTRICT`, `CASCADE`, `SET NULL` or `SET DEFAULT`.

    3. `Domain integrity`
    - Every value in a column must belong to the column's defined `domain` — its data type, length, format and permitted range.
    ```sql
    salary DECIMAL(10,2) CHECK (salary > 0),
    gender CHAR(1) CHECK (gender IN ('M','F')),
    email  VARCHAR(100) NOT NULL
    ```

    Other constraints usually grouped with them
    - `Key (uniqueness) integrity` — `UNIQUE` prevents duplicate values in a candidate key.
    - `User-defined or business integrity` — rules specific to the organisation, enforced by CHECK constraints, triggers or stored procedures. For example, a loan may not exceed ten times the applicant's salary.
    - `Null integrity` — `NOT NULL` where a value is mandatory.

    Summary

    | Rule | Enforced by | Prevents |
    |---|---|---|
    | Entity integrity | `PRIMARY KEY` | Duplicate or unidentifiable rows |
    | Referential integrity | `FOREIGN KEY` | Orphan records |
    | Domain integrity | Data type, `CHECK`, `NOT NULL`, `DEFAULT` | Invalid values |
    | Key integrity | `UNIQUE` | Duplicate candidate-key values |
    | Business integrity | `CHECK`, triggers, procedures | Violations of organisation-specific rules |

    Second highest salary from the Employee table
    ```sql
    SELECT MAX(salary) AS second_highest_salary
    FROM   Employee
    WHERE  salary < (SELECT MAX(salary) FROM Employee);
    ```
    - The subquery finds the highest salary; the outer query finds the highest value strictly below it.
    - Duplicates cause no problem: if several employees share the top salary, `<` excludes them all and the genuine second distinct value is returned.

    Alternative forms
    ```sql
    -- LIMIT with OFFSET; DISTINCT is essential
    SELECT DISTINCT salary FROM Employee
    ORDER  BY salary DESC LIMIT 1 OFFSET 1;

    -- DENSE_RANK, which generalises to the Nth highest
    SELECT DISTINCT salary FROM (
        SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
        FROM   Employee
    ) t
    WHERE rnk = 2;
    ```
    - `DENSE_RANK` rather than `RANK`: with salaries 90000, 90000, 75000, RANK gives 1, 1, 3 so no row has rank 2 at all, whereas DENSE_RANK gives 1, 1, 2 and correctly returns 75000.

## DBMS Architecture & Features (26)

1. (a) DBMS এর মূল বৈশিষ্ট্য লিখুন।
   (b) HTTP ও HTTPS প্রোটোকলের মধ্যে সুরক্ষার দিক থেকে পার্থক্য ব্যাখ্যা করুন। *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) The main features of a DBMS.

   1. `Data storage, retrieval and update`
   - The core function: adding, reading, modifying and deleting data through SQL, without the user knowing anything about how the data is physically stored.

   2. `Reduced data redundancy and inconsistency`
   - Data is stored once in a normalised structure and shared by every application. In a file-based system the same customer address is duplicated in several files, and updating one but not the others produces inconsistency.

   3. `Data integrity`
   - Constraints keep the data valid: `PRIMARY KEY` (entity integrity), `FOREIGN KEY` (referential integrity), `CHECK`, `NOT NULL`, `UNIQUE` and `DEFAULT`.

   4. `Data security and access control`
   - Users, roles and privileges (`GRANT`, `REVOKE`) restrict who can see or change what. Views hide sensitive columns, and data can be encrypted at rest and in transit.

   5. `Concurrency control`
   - Many users can work simultaneously without corrupting each other's data, through locking, timestamps or multi-version concurrency control (MVCC).

   6. `Transaction management with ACID properties`
   - `Atomicity` — all or nothing; `Consistency` — the database moves from one valid state to another; `Isolation` — concurrent transactions do not interfere; `Durability` — committed changes survive a crash.

   7. `Backup and recovery`
   - Automatic logging, checkpointing and recovery restore the database after a failure, using the transaction log to roll forward or roll back.

   8. `Data independence`
   - `Physical` independence — storage structures can change without altering the logical schema. `Logical` independence — the logical schema can change without rewriting applications. This is what the three-level architecture exists to provide.

   9. `Data sharing and multi-user support`
   - One database serves many applications and many users at once, with a consistent view of the data.

   10. `Query language and query optimisation`
   - A declarative language (SQL) lets the user state `what` is wanted; the optimiser decides `how` to fetch it, choosing indexes and join orders automatically.

   11. `Metadata management — the data dictionary`
   - The DBMS stores a description of the database itself: tables, columns, types, constraints, indexes and privileges.

   12. `Views and abstraction`
   - Virtual tables present the data differently to different users without duplicating it.

   13. `Scalability, indexing and performance tuning`
   - Indexes, partitioning, caching and replication support large data volumes.

   - Taken together, these features are what distinguish a DBMS from a collection of files: the data becomes shared, controlled, consistent and recoverable rather than scattered and fragile.

2. **ODBC এর পূর্ণ রূপ কি?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: ODBC stands for `Open Database Connectivity`.

   What it is
   - A `standard API` developed by Microsoft in 1992 that lets an application access data in `any` database management system, provided a driver for that system exists.
   - Its purpose is to make the application independent of the particular database: the same program can talk to Oracle, MySQL, SQL Server or PostgreSQL simply by changing the driver, with no change to the code.

   How it works
   ```
   +-------------+     +--------------+     +------------+     +----------+
   | Application |---->| ODBC Driver  |---->| ODBC       |---->| Database |
   |             |     | Manager      |     | Driver     |     |          |
   +-------------+     +--------------+     +------------+     +----------+
      standard API      selects the driver   translates to      MySQL,
      calls             for the target DB    the DB's own       Oracle,
                                             protocol           SQL Server
   ```
   - The application issues standard ODBC calls; the driver manager routes them to the correct driver; the driver translates them into the database's native calls and returns the results in a standard form.

   Components
   - `Application` — the program making the calls.
   - `Driver Manager` — loads and manages the drivers.
   - `Driver` — database-specific translation layer.
   - `Data Source (DSN)` — a named configuration holding the server address, database name and credentials.

   Advantages
   - One API for every database; the application is portable; the driver can be swapped without recompiling; and it is supported on Windows, Linux and macOS.

   Disadvantage
   - The extra layer costs some performance compared with a native driver, and vendor-specific features may be unreachable through the generic API.

   Related abbreviations often asked with it

   | Abbreviation | Full form |
   |---|---|
   | `ODBC` | Open Database Connectivity |
   | `JDBC` | Java Database Connectivity |
   | `OLE DB` | Object Linking and Embedding, Database |
   | `ADO.NET` | ActiveX Data Objects for .NET |
   | `DSN` | Data Source Name |

3. **Data about data is Called __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: Data about data is called `metadata`.

   What it is
   - Metadata is data that `describes other data` — its structure, meaning, origin, format and constraints — rather than being the data itself.

   In a database
   - The DBMS stores its metadata in the `data dictionary` (also called the system catalogue). It records:
     - table names, column names and data types
     - primary keys, foreign keys and other constraints
     - indexes and views
     - user accounts and privileges
     - storage locations and statistics used by the query optimiser

   ```sql
   -- querying the metadata itself
   SELECT table_name, column_name, data_type
   FROM   information_schema.columns
   WHERE  table_schema = 'company';

   DESCRIBE Employee;      -- the structure, not the data
   SHOW TABLES;
   ```

   Example of the distinction
   ```
   DATA                                METADATA
   +--------+----------+--------+      Table name : Employee
   | emp_id | emp_name | salary |      Columns    : emp_id INT, emp_name VARCHAR(100),
   +--------+----------+--------+                   salary DECIMAL(10,2)
   |  101   | Karim    | 50000  |      Primary key: emp_id
   |  102   | Rahim    | 60000  |      Rows       : 2
   +--------+----------+--------+      Created on : 2025-01-15
   ```

   Types of metadata
   - `Descriptive` — title, author, keywords; used for discovery.
   - `Structural` — how the parts fit together: tables, columns, relationships, page order in a document.
   - `Administrative` — creation date, owner, permissions, retention rules.
   - `Technical` — file format, size, encoding, compression.

   Everyday examples outside databases
   - A photograph's EXIF data: camera model, date, exposure, GPS location.
   - A music file's tags: artist, album, track number, duration.
   - An email's headers: sender, recipient, timestamp, routing path.
   - A file's properties: size, type, created and modified dates, permissions.

   Why it matters
   - The query optimiser relies on statistics held as metadata to choose an execution plan; without accurate statistics, queries run badly.
   - Data governance, lineage tracking and compliance auditing are all metadata problems.
   - Metadata is also a privacy concern: call metadata — who called whom, when, and for how long — can be as revealing as the conversation itself.

4. **Difference between MSAccess and MS FoxPro in SQL.** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 317 (ET: N/A)]*

   Answer: Both are Microsoft desktop database products, but they belong to different generations and different models.

   | Point | MS Access | MS FoxPro (Visual FoxPro) |
   |---|---|---|
   | Type | Relational DBMS with a graphical front end | Procedural DBMS with an integrated programming language (xBase) |
   | Data engine | Jet / ACE database engine | Native FoxPro / Rushmore engine |
   | File format | Single `.accdb` (or `.mdb`) file holding everything | Separate files: `.dbf` for tables, `.cdx` for indexes, `.fpt` for memos |
   | SQL support | Full support, close to ANSI SQL | Supported, but blended with xBase commands such as `USE`, `SEEK`, `SKIP` |
   | Programming | VBA (Visual Basic for Applications) | FoxPro's own procedural and object-oriented language |
   | Data access style | `Set-based` — write a query, get a result set | `Record-based` — move a pointer through the table with SKIP and SEEK |
   | Interface | Strong visual designers for forms and reports | Also has designers, but code-centred |
   | Performance | Slower on very large tables | Faster, thanks to the Rushmore query optimisation technology |
   | Concurrent users | Practical limit around 10–20 | Handled more users, but still file-based |
   | Ease of use | `Very easy` — designed for non-programmers | Steeper learning curve; aimed at developers |
   | Status | Still shipped as part of Microsoft Office | `Discontinued` — Visual FoxPro 9 was the last version, support ended in 2015 |
   | Typical use | Small office databases, prototypes, front end to SQL Server | Legacy business applications from the 1990s |

   The SQL difference in practice
   ```sql
   -- MS Access: set-based, SQL-first
   SELECT emp_name, salary FROM Employee WHERE salary > 50000;

   -- FoxPro: SQL is available ...
   SELECT emp_name, salary FROM Employee WHERE salary > 50000 INTO CURSOR result

   -- ... but the traditional xBase style is record-by-record
   USE Employee
   SET FILTER TO salary > 50000
   GO TOP
   DO WHILE NOT EOF()
       ? emp_name, salary
       SKIP
   ENDDO
   ```
   - That contrast is the essential one: `Access thinks in result sets, FoxPro thinks in record pointers`.

   Common limitations of both
   - Both are `file-based` rather than client-server, so the whole file travels across the network and concurrency is limited. Neither is suitable for a large multi-user system, where SQL Server, MySQL or PostgreSQL should be used instead. In practice Access is now most often used as a front end to a proper server database rather than as the database itself.

5. **(খ) DBMS কী? দুটি সুবিধা লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer: (Answered in English, as required for IT topics.)

   What is a DBMS
   - A `Database Management System` is software that lets users create, store, retrieve, update and manage data in a database while controlling access to it.
   - It sits between the user or application and the physical data files, so users work with tables and queries rather than with storage.
   - Examples: MySQL, PostgreSQL, Oracle, SQL Server, SQLite, MongoDB.

   Two advantages (with a fuller list for completeness)

   1. `Reduced data redundancy and inconsistency`
   - Data is stored once in a normalised structure and shared by every application, instead of being duplicated in separate files. In a file-based system the same customer address appears in the sales file, the billing file and the delivery file; updating one and forgetting the others makes the data inconsistent. A DBMS removes that risk.

   2. `Data security and controlled access`
   - Users, roles and privileges determine exactly who may read or change which data. `GRANT` and `REVOKE` control access at table and column level, views hide sensitive columns, and the database can be encrypted. A collection of files offers only the operating system's file permissions, which are far coarser.

   Other advantages worth naming
   - `Data integrity` — constraints such as PRIMARY KEY, FOREIGN KEY, CHECK and NOT NULL keep the data valid automatically.
   - `Concurrency control` — many users work at once without corrupting each other's data.
   - `Transaction support with ACID properties` — Atomicity, Consistency, Isolation, Durability.
   - `Backup and recovery` — the transaction log allows the database to be restored to a consistent state after a crash.
   - `Data independence` — storage structures can change without rewriting applications.
   - `Efficient querying` — a declarative language plus an optimiser that chooses indexes and join orders.
   - `Data sharing` — one database serves many applications simultaneously.

   Disadvantages, for balance
   - Higher cost of software, hardware and skilled staff; greater complexity; and a single point of failure if the server is not made redundant.

6. **What is Database?** *[EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)]*

   Answer: A `database` is an organised collection of related data, stored electronically so that it can be efficiently accessed, managed and updated.

   Key characteristics
   - The data is `structured` — usually into tables of rows and columns in a relational database.
   - The data is `related` — it describes some part of the real world, such as a bank's customers and their accounts.
   - It is `persistent` — it survives program termination and power loss.
   - It is `shared` — many users and applications use the same data simultaneously.
   - It is managed by a `DBMS`, which controls access, enforces integrity and provides recovery.

   Example
   ```
   Database: University

   Table: Student                        Table: Course
   +------------+-------+------+         +-----------+------------------+
   | student_id | name  | dept |         | course_id | course_name      |
   +------------+-------+------+         +-----------+------------------+
   |    101     | Karim | CSE  |         |   CS101   | Database Systems |
   |    102     | Rahim | EEE  |         |   CS102   | Networking       |
   +------------+-------+------+         +-----------+------------------+
   ```

   Terminology
   - `Table (relation)` — a two-dimensional structure holding data about one kind of thing.
   - `Row (tuple / record)` — one instance, such as one student.
   - `Column (attribute / field)` — one property, such as the name.
   - `Field` — the smallest unit of data: the value of one column in one row.
   - `Schema` — the structural definition of the database.

   Types of database
   - `Relational` — tables linked by keys, queried with SQL: MySQL, PostgreSQL, Oracle.
   - `NoSQL` — document (MongoDB), key-value (Redis), column-family (Cassandra), graph (Neo4j).
   - By location: centralised, distributed, cloud.
   - By use: OLTP for day-to-day transactions, OLAP data warehouses for analysis.

   Why a database rather than files
   - Less redundancy and inconsistency, enforced integrity, controlled security, concurrent multi-user access, transactions with ACID guarantees, backup and recovery, and a query language with an optimiser.

   - Note the distinction examiners look for: the `database` is the data itself, while the `DBMS` is the software that manages it. Oracle is a DBMS; the payroll data stored in it is the database.

7. **What is data about data?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

   Answer: Data about data is called `metadata`.

   Definition
   - Metadata `describes` other data — its structure, meaning, origin, format, ownership and constraints — rather than being the subject data itself.

   In a database
   - The DBMS keeps its metadata in the `data dictionary`, also called the system catalogue. It holds:
     - table and column names with their data types and sizes
     - primary keys, foreign keys, and CHECK, NOT NULL and UNIQUE constraints
     - indexes, views, triggers and stored procedures
     - user accounts, roles and privileges
     - storage locations, row counts and the statistics the query optimiser depends on

   ```sql
   DESCRIBE Employee;                        -- the structure, not the rows

   SELECT table_name, column_name, data_type
   FROM   information_schema.columns
   WHERE  table_schema = 'company';          -- querying the metadata directly
   ```

   The distinction, illustrated
   ```
   DATA                                  METADATA
   +--------+----------+--------+        Table name  : Employee
   | emp_id | emp_name | salary |        Column      : emp_id, type INT, primary key
   +--------+----------+--------+        Column      : emp_name, VARCHAR(100), not null
   |  101   | Karim    | 50000  |        Column      : salary, DECIMAL(10,2)
   |  102   | Rahim    | 60000  |        Row count   : 2
   +--------+----------+--------+        Last modified: 2025-01-15
   ```

   Types
   - `Descriptive` — title, author, keywords; supports discovery and search.
   - `Structural` — how components relate: tables, relationships, page order.
   - `Administrative` — creation date, owner, permissions, retention policy.
   - `Technical` — format, size, encoding, compression.

   Everyday examples
   - A photograph's EXIF data: camera, date, shutter speed, GPS coordinates.
   - A music file's ID3 tags: artist, album, duration.
   - An email's headers: sender, recipient, timestamp, routing.
   - A file's properties: size, type, created and modified dates.

   Why it matters
   - The query `optimiser` chooses its execution plan from statistical metadata; stale statistics cause slow queries.
   - Data governance, lineage and compliance auditing are all metadata questions.
   - Metadata carries real privacy weight: knowing who called whom, when and for how long can reveal as much as the conversation itself.

8. **(খ) Centralized System ও Client Server System সম্পর্কে সচিত্র বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 612 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   Centralised system
   - All the data and all the processing reside on `one central computer`, usually a mainframe. Users connect through terminals that do no processing of their own — "dumb terminals".

   ```
                       +---------------------+
                       |   CENTRAL COMPUTER  |
                       |   (mainframe)       |
                       |  - Database         |
                       |  - Application      |
                       |  - Processing       |
                       +----------+----------+
                                  |
             +--------------------+--------------------+
             |                    |                    |
         [Terminal]          [Terminal]           [Terminal]
         (no processing)     (no processing)      (no processing)
   ```

   - Advantages: a single point of control and administration; strong security, since everything is in one place; no data inconsistency; simple backup; and low cost per terminal.
   - Disadvantages: a `single point of failure` — if the central machine fails, everything stops; a performance bottleneck as users increase; expensive central hardware; and terminals cannot work offline.

   Client-server system
   - Processing is `divided`. The client handles the user interface and some logic; the server holds the database and executes queries. The two communicate over a network.

   ```
      [Client 1]        [Client 2]        [Client 3]
      - UI              - UI              - UI
      - some logic      - some logic      - some logic
           \                |                /
            \               |               /
             \______________|______________/
                            |
                      (network requests)
                            |
                 +----------+----------+
                 |      SERVER         |
                 |  - Database         |
                 |  - Business logic   |
                 |  - Query processing |
                 +---------------------+
   ```

   - Advantages: the load is shared, so the server does less work per user; clients can be ordinary PCs; the system scales by adding clients or servers; the network carries only requests and results rather than whole files; and servers can be replicated for availability.
   - Disadvantages: more complex to build and administer; the server is still a bottleneck and a failure point unless clustered; and network latency affects every operation.

   Comparison

   | Point | Centralised | Client-server |
   |---|---|---|
   | Processing | Entirely on the central machine | Divided between client and server |
   | Client hardware | Dumb terminal | Full computer |
   | Scalability | Poor | Good |
   | Cost of central machine | Very high | Moderate |
   | Single point of failure | Yes | The server, unless clustered |
   | Network traffic | Screen output only | Requests and result sets |
   | Maintenance | One machine | Server plus every client |
   | Example | Mainframe banking systems of the 1970s and 1980s | MySQL or Oracle serving desktop and web applications |

   - The modern extension is the `three-tier` architecture: presentation (browser), application (web or app server) and data (database server). Separating the middle tier lets business logic be changed without touching either the client or the database, and it is the standard shape of web applications today.

9. **(ক) একজন ডাটাবেস এডমিন এর কাজ কী? কিছু ডাটাবেস সিস্টেম অ্যাপ্লিকেশনের নাম লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 625 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   Work of a Database Administrator (DBA)

   1. `Database design and implementation`
   - Designing the schema, choosing data types, defining primary and foreign keys, and normalising the tables. Creating databases, tables, views and indexes.

   2. `Installation, configuration and upgrades`
   - Installing the DBMS, tuning its configuration parameters, applying patches and planning version upgrades.

   3. `Security administration`
   - Creating users and roles, granting and revoking privileges, enforcing password policy, configuring encryption, and auditing who accessed what.

   4. `Backup and recovery`
   - Designing the backup strategy (full, incremental, differential), scheduling and verifying backups, and — critically — `testing the restore`. A backup that has never been restored is not a backup.

   5. `Performance monitoring and tuning`
   - Finding slow queries, examining execution plans, creating and removing indexes, tuning memory and buffer settings, and partitioning large tables.

   6. `Capacity planning and storage management`
   - Forecasting growth, allocating tablespaces, archiving old data.

   7. `Data integrity`
   - Defining and maintaining constraints, and running consistency checks.

   8. `Availability and disaster recovery`
   - Configuring replication, clustering, failover and standby servers; defining and testing the DR plan.

   9. `Troubleshooting and user support`
   - Diagnosing deadlocks, blocked sessions, corruption and connection failures; helping developers write efficient SQL.

   10. `Documentation and compliance`
   - Maintaining the data dictionary and schema documentation, and meeting regulatory requirements for retention and audit.

   Database system applications
   - `Banking` — accounts, transactions, loans, ATM networks.
   - `Airlines and railways` — reservations, schedules, seat allocation.
   - `Universities` — student registration, courses, results.
   - `Telecommunications` — call records, billing, prepaid balances.
   - `Sales and e-commerce` — customers, products, orders, inventory.
   - `Human resources and payroll` — employees, salaries, leave, taxation.
   - `Healthcare` — patient records, prescriptions, laboratory results.
   - `Manufacturing` — production planning, supply chain, stock control.
   - `Government` — national ID, land records, tax administration.
   - `Libraries` — catalogues, members, loans.
   - `Social media and search` — user profiles, posts, relationships, indexes.

   - Related roles worth distinguishing: a `Data Administrator` decides policy and standards for data as a corporate asset, while the `Database Administrator` implements and operates the databases themselves.

10. **(খ) ডাটাবেস ব্যবস্থাপনা সিস্টেমের তিন স্তরবিশিষ্ট আর্কিটেকচার ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 626 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The `three-level (three-schema) architecture` was proposed by ANSI/SPARC to separate a user's view of the data from how it is actually stored.

    The diagram
    ```
    +-------------------------------------------------------------+
    |  EXTERNAL LEVEL  (view level)                               |
    |                                                             |
    |   [User View 1]      [User View 2]      [User View 3]       |
    |   Clerk sees name    HR sees salary     Manager sees        |
    |   and phone only     and leave          department totals   |
    +-------------------------------------------------------------+
                              |  external / conceptual mapping
    +-------------------------------------------------------------+
    |  CONCEPTUAL LEVEL  (logical level)                          |
    |                                                             |
    |   The whole database as one logical structure:              |
    |   Employee(emp_id, name, salary, dept_id)                   |
    |   Department(dept_id, dept_name)                            |
    |   plus all constraints and relationships                    |
    +-------------------------------------------------------------+
                              |  conceptual / internal mapping
    +-------------------------------------------------------------+
    |  INTERNAL LEVEL  (physical level)                           |
    |                                                             |
    |   How the data is actually stored:                          |
    |   file organisation, B-tree indexes, pages, compression,    |
    |   record placement on disk                                  |
    +-------------------------------------------------------------+
                              |
                        [ Physical database ]
    ```

    1. External level (view level)
    - The `highest` level, closest to the user. Each user or group sees only the part of the database that concerns them, in the form that suits them.
    - There are `many` external schemas, one per user group.
    - It provides `security` (sensitive columns are simply absent from the view) and `simplicity` (a complex join is presented as one virtual table).
    - Implemented in SQL with `views`.

    2. Conceptual level (logical level)
    - The `middle` level, describing the `whole` database logically: all the entities, attributes, relationships and constraints, but nothing about how they are stored.
    - There is exactly `one` conceptual schema, and it is the DBA's central design.

    3. Internal level (physical level)
    - The `lowest` level, describing `how` the data is stored: file organisation, record layout, index structures, compression, page size and placement on disk.
    - There is exactly `one` internal schema. Users and application programmers never see it.

    Data independence — the reason for the architecture

    | Type | Meaning | Example |
    |---|---|---|
    | `Logical data independence` | The conceptual schema can change without altering the external schemas or the applications | Adding a column to Employee does not break existing views |
    | `Physical data independence` | The internal schema can change without altering the conceptual schema | Adding an index or moving the data to a new disk does not affect any query's meaning |

    - `Physical` independence is easier to achieve and is well supported by every DBMS; `logical` independence is harder, because a change to the logical structure often does affect what the applications expect.

    Advantages of the architecture
    - Users are shielded from storage details; several customised views can exist over the same data; security is enforced by restricting views; storage can be reorganised for performance without touching applications; and the DBA can tune the system independently of the developers.

11. **(ক) সাধারণ ফাইলভিত্তিক সিস্টেমের চেয়ে DBMS এর সুবিধা কী কী?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 627 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Advantages of a DBMS over an ordinary file-based system.

    1. `Reduced data redundancy`
    - In a file system the same data is duplicated across files — the customer address appears in the sales file, the billing file and the delivery file. A DBMS stores it once in a normalised structure and shares it.

    2. `Elimination of data inconsistency`
    - Because the data exists once, updating it updates it everywhere. In a file system, changing the address in one file and forgetting the others leaves the organisation with two contradictory answers to the same question.

    3. `Data integrity`
    - Constraints — PRIMARY KEY, FOREIGN KEY, CHECK, NOT NULL, UNIQUE — are enforced by the DBMS itself. A file system enforces nothing; every application must re-implement the rules, and any one of them can get it wrong.

    4. `Data security and access control`
    - Users, roles and privileges control access at table and even column level; views hide sensitive data. A file system offers only coarse file permissions.

    5. `Concurrent multi-user access`
    - Locking or MVCC lets many users read and write simultaneously without corrupting each other's work. In a file system two programs writing the same file at once will corrupt it.

    6. `Transaction support — the ACID properties`
    - A transfer that debits one account and credits another either completes entirely or not at all. A file system has no notion of a transaction, so a crash midway leaves the money missing.

    7. `Backup and recovery`
    - The transaction log allows automatic recovery to a consistent state after a crash. File-based recovery means restoring yesterday's copy and losing a day's work.

    8. `Data independence`
    - Storage structures and even the logical schema can change without rewriting the applications. In a file system, changing a record layout means changing every program that reads the file.

    9. `Efficient querying`
    - SQL states `what` is wanted and the optimiser decides `how` to get it, using indexes and join strategies. In a file system every query must be written as a program.

    10. `Data sharing`
    - One database serves many applications and departments with a single consistent version of the truth, rather than each department keeping its own files.

    11. `Enforcement of standards`
    - Naming conventions, data formats and documentation are centralised in the data dictionary.

    Summary

    | Point | File system | DBMS |
    |---|---|---|
    | Redundancy | High | Controlled |
    | Consistency | Hard to maintain | Enforced |
    | Integrity rules | In each application | In the database |
    | Security | File-level only | User, role, table and column level |
    | Concurrency | Unsafe | Managed |
    | Transactions | None | ACID |
    | Recovery | Manual | Automatic, log-based |
    | Querying | Program per query | Declarative SQL |
    | Data independence | None | Physical and logical |

    Disadvantages of a DBMS, for balance
    - Higher cost of software, hardware and skilled staff; greater complexity; and a single point of failure unless replicated. For a very small, single-user, read-only dataset, a file may genuinely be the better choice.

12. **What is Database administrator role?** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 662 (ET: N/A)]*

    Answer: The `Database Administrator (DBA)` is the person responsible for the design, implementation, security, performance and availability of an organisation's databases.

    Main roles

    1. `Schema design and implementation`
    - Designing tables, choosing data types, defining keys, normalising the structure, and creating databases, views and indexes.

    2. `Installation, configuration and upgrades`
    - Installing the DBMS, tuning configuration parameters, applying security patches, and planning version migrations.

    3. `Security administration`
    - Creating users and roles; granting and revoking privileges with `GRANT` and `REVOKE`; enforcing password policy; configuring encryption at rest and in transit; and auditing access.

    4. `Backup and recovery`
    - Choosing a backup strategy — full, incremental, differential — scheduling it, monitoring it, and `regularly testing the restore`. An untested backup is not a backup.

    5. `Performance monitoring and tuning`
    - Identifying slow queries, reading execution plans, adding or removing indexes, tuning buffer and memory settings, partitioning large tables, and updating optimiser statistics.

    6. `Capacity planning and storage management`
    - Forecasting growth, allocating storage, archiving and purging old data.

    7. `Availability and disaster recovery`
    - Configuring replication, clustering and failover; maintaining a standby site; defining and rehearsing the DR plan against agreed RPO and RTO targets.

    8. `Data integrity`
    - Defining and maintaining constraints, and running consistency checks.

    9. `Troubleshooting`
    - Diagnosing deadlocks, blocking, connection exhaustion, corruption and failed jobs.

    10. `Supporting developers and users`
    - Reviewing SQL for efficiency and safety, advising on schema changes, and managing the migration of changes from development to production.

    11. `Documentation and compliance`
    - Maintaining the data dictionary and schema documentation; meeting regulatory obligations for retention, privacy and audit.

    Types of DBA
    - `System DBA` — installation, patching, configuration, storage.
    - `Application DBA` — schema and SQL for one particular application.
    - `Development DBA` — design and code review during development.
    - `Cloud DBA` — managed services such as RDS, Azure SQL and Cloud SQL.

    Skills required
    - SQL and the internals of at least one DBMS; performance tuning; backup and recovery; operating systems and storage; scripting for automation; and security practice.

    - A useful distinction: a `Data Administrator` sets policy and standards for data as a corporate asset — what data is held, what it means, who owns it — while the `Database Administrator` builds and operates the systems that store it.

13. **Explain difference between Data Administrator and Database Administrator.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 681 (ET: N/A)]*

    Answer:

    | Point | Data Administrator (DA) | Database Administrator (DBA) |
    |---|---|---|
    | Focus | `Data as a corporate asset` — policy and meaning | `The database systems` — implementation and operation |
    | Orientation | Managerial and strategic | Technical and operational |
    | Main concern | What data the organisation holds, what it means, who owns it | How that data is stored, secured and made to perform |
    | Level | Conceptual and logical | Logical and physical |
    | Typical tasks | Data policy, standards, naming conventions, the enterprise data model, data ownership and stewardship, data quality rules, regulatory compliance | Installation, schema creation, indexing, tuning, backup and recovery, security administration, replication, troubleshooting |
    | Deliverables | Data dictionary, data governance policy, enterprise data model | A running, secure, fast, recoverable database |
    | Tools | Modelling and governance tools, documentation | The DBMS itself, monitoring and backup tools, SQL |
    | Technical depth | Moderate | High |
    | Reports to | Usually senior management or the CIO | Usually IT operations |
    | Number in an organisation | Few — often one | Several, sometimes per system |
    | Time horizon | Long term | Day to day |

    The relationship between them
    ```
    DATA ADMINISTRATOR
      decides: "Customer address must be stored once, in a standard format,
                owned by the Sales department, retained for 7 years."
                                  |
                                  v
    DATABASE ADMINISTRATOR
      implements: CREATE TABLE Customer (... address VARCHAR(200) ...);
                  adds constraints, indexes, permissions, backups,
                  and an archival job that purges after 7 years.
    ```

    In one line each
    - The `Data Administrator` decides `what` data the organisation keeps and what the rules are.
    - The `Database Administrator` decides `how` it is stored and makes it work.

    Practical note
    - In a small organisation one person performs both roles. The separation matters in large enterprises and in government, where data governance, ownership and regulatory compliance are substantial responsibilities in their own right, quite separate from keeping a server running.
    - A third related role, the `Data Architect`, sits between them, designing the overall data landscape and integration between systems.

14. **Describe the advantages and disadvantages of DBMS-provided and application provided security.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 684 (ET: N/A)]*

    Answer: Security can be enforced by the DBMS itself, or written into the application, and each approach has real strengths and weaknesses.

    DBMS-provided security
    - The database enforces access control directly: users, roles, privileges, views, row-level security and encryption.
    ```sql
    CREATE USER clerk IDENTIFIED BY 'password';
    GRANT SELECT ON Employee(emp_name, designation) TO clerk;   -- no salary column
    REVOKE DELETE ON Employee FROM clerk;
    ```

    `Advantages`
    - `Centralised and consistent` — one set of rules applies no matter which application, report tool or command-line client connects. This is the decisive advantage.
    - `Cannot be bypassed` — a user connecting with SQL directly is still subject to the same privileges.
    - `Reliable and well tested` — the vendor's implementation is mature and audited, rather than home-written.
    - `Granular` — control at database, table, column and even row level, plus views that hide data entirely.
    - `Built-in auditing` of who accessed what and when.
    - `Less code to write and maintain`, and the rules survive when applications are rewritten.

    `Disadvantages`
    - `Limited expressiveness` — it enforces "who may see which rows and columns", but not complex business rules such as "a manager may approve a loan only up to their sanction limit, and only during office hours".
    - `Administrative overhead` — every user needs a database account, which is impractical for a public web application with a million users.
    - `Vendor-specific` — the syntax and capabilities differ between Oracle, SQL Server and PostgreSQL, so migration is harder.
    - `Connection pooling conflicts` — modern applications share one pooled database login, which defeats per-user database privileges.

    Application-provided security
    - The application authenticates users and decides what each may do, connecting to the database with a single privileged account.

    `Advantages`
    - `Flexible and expressive` — arbitrary business logic, workflow states, time-of-day rules and approval limits can all be encoded.
    - `Scales to many users` without creating a database account for each one.
    - `Portable` — independent of the DBMS, so the database can be changed without rewriting the security model.
    - `Better user experience` — friendly error messages, single sign-on, multi-factor authentication.
    - `Works with connection pooling`, which is essential for web performance.

    `Disadvantages`
    - `Bypassable` — this is the fundamental weakness. Anyone who obtains the application's database credentials, or connects with a SQL client, has full access. The database itself is defenceless.
    - `Duplicated effort` — every application touching the database must re-implement the same rules, and any one of them may implement them wrongly.
    - `Bug-prone` — a single missing authorisation check exposes data. This is the commonest cause of real breaches.
    - `Weaker auditing`, since the database sees only the shared account.

    Comparison

    | Point | DBMS-provided | Application-provided |
    |---|---|---|
    | Enforcement point | The database | The application |
    | Can be bypassed | No | `Yes` |
    | Business-rule complexity | Limited | Unlimited |
    | Scales to many users | Poorly | Well |
    | Consistency across applications | Guaranteed | Must be re-implemented |
    | Portability | Vendor-specific | Portable |
    | Auditing | Built in | Must be written |

    The practical answer — `defence in depth`
    - Real systems use `both`. The application enforces the rich business rules and the user experience, while the database still restricts the application's own account to the minimum privileges it needs, uses views to hide sensitive columns, encrypts data at rest, and audits access. Neither layer alone is sufficient: the application layer is bypassable, and the database layer cannot express the business rules.

15. **(a) What is database schema? What are dangling tuple and descriptive attribute?** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 693 (ET: N/A)]*

    Answer:

    Database schema
    - A `schema` is the `logical structure` of a database — its design or blueprint. It defines the tables, the columns and their data types, the keys, the relationships and the constraints, but not the data itself.
    - It is defined with DDL statements and is stored in the data dictionary.
    - The `schema` is the definition; the `instance` is the data actually held at a given moment. The schema changes rarely; the instance changes constantly.

    ```sql
    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,
        emp_name VARCHAR(100) NOT NULL,
        salary   DECIMAL(10,2) CHECK (salary > 0),
        dept_id  INT REFERENCES Department(dept_id)
    );
    ```
    - Three levels of schema exist in the ANSI/SPARC architecture: `external` (individual user views), `conceptual` (the whole database logically) and `internal` (physical storage).

    Dangling tuple
    - A `dangling tuple` is a row that is lost, or fails to combine, when relations are joined — a row in one relation with `no matching row` in the other.
    - It arises in two important contexts:

    1. `In a natural or inner join`
    ```
    Employee                       Department
    +--------+---------+           +---------+-----------+
    | emp_id | dept_id |           | dept_id | dept_name |
    +--------+---------+           +---------+-----------+
    |  101   |   10    |           |   10    | IT        |
    |  102   |  NULL   | <- dangling|   20   | HR        |
    |  103   |   99    | <- dangling+---------+-----------+
    +--------+---------+
    ```
    - Employees 102 and 103 disappear from an inner join. An `outer join` preserves them, padding the missing side with NULLs — which is exactly what outer joins exist for.

    2. `In a lossy decomposition`
    - When a relation is split into two and the common attribute is not a superkey of either, rejoining them produces `spurious tuples` and may lose genuine ones. Dangling tuples are the symptom that the decomposition was not lossless.

    - Practical significance: a dangling tuple usually signals a `referential integrity` problem — a foreign key pointing at a row that no longer exists, which a properly declared FOREIGN KEY constraint would have prevented.

    Descriptive attribute
    - A `descriptive attribute` is an attribute that belongs to a `relationship` rather than to either of the entities it connects.
    - It describes the relationship itself, and it cannot sensibly be stored in either entity alone.

    ```
       Student  -------< Enrolls >-------  Course
                            |
                         [grade]           <- descriptive attribute
                         [date]
    ```
    - `grade` belongs neither to the student (a student has many grades) nor to the course (a course gives many grades). It exists only for the `pairing` of one student with one course.

    ```sql
    CREATE TABLE Enrollment (
        student_id INT,
        course_id  INT,
        grade      CHAR(2),        -- descriptive attribute
        enrol_date DATE,           -- descriptive attribute
        PRIMARY KEY (student_id, course_id),
        FOREIGN KEY (student_id) REFERENCES Student(student_id),
        FOREIGN KEY (course_id)  REFERENCES Course(course_id)
    );
    ```
    - Other examples: `quantity` on the relationship between an order and a product; `salary` on the relationship between an employee and a project they are assigned to; `borrow_date` between a member and a book.
    - In the ER diagram, a descriptive attribute is drawn as an oval attached to the `diamond`, not to either rectangle.

16. **What is data Independence? How many types of data independence?** *[BDCCL Assistant Engineer (Network) 2022 compact it 742 (ET: N/A)]*

    Answer:

    What is data independence
    - `Data independence` is the ability to change the schema at one level of a database system `without` having to change the schema at the level above, and therefore without rewriting the applications.
    - It is the main reason the ANSI/SPARC three-level architecture exists: external, conceptual and internal levels are separated by `mappings`, and a change is absorbed by adjusting a mapping rather than by changing everything above it.

    ```
    +-------------------------------------------+
    |  EXTERNAL LEVEL  (user views)             |
    +-------------------------------------------+
            ^  LOGICAL data independence
    +-------------------------------------------+
    |  CONCEPTUAL LEVEL  (whole logical schema) |
    +-------------------------------------------+
            ^  PHYSICAL data independence
    +-------------------------------------------+
    |  INTERNAL LEVEL  (physical storage)       |
    +-------------------------------------------+
    ```

    There are `two` types.

    1. Physical data independence
    - The ability to change the `internal (physical) schema` without changing the conceptual schema.
    - Examples of such changes: creating or dropping an index, moving the database to a different disk or file system, changing the file organisation from heap to clustered, altering the page size, enabling compression, or partitioning a table.
    - Effect on applications: `none`. A query means exactly the same thing before and after; only its execution plan changes.
    ```sql
    CREATE INDEX idx_salary ON Employee(salary);
    -- every existing query still works, unchanged; some simply run faster
    ```
    - This form is `easier to achieve` and every modern DBMS provides it fully.

    2. Logical data independence
    - The ability to change the `conceptual schema` without changing the external schemas or the application programs.
    - Examples: adding a new column or table, splitting one table into two, merging two tables, renaming an attribute, or changing a relationship.
    - Applications are protected by `views`: if the underlying tables change, the view definition is rewritten and the applications querying the view continue to work.
    ```sql
    -- the conceptual schema changes: Employee is split into two tables
    -- but the old view is redefined, so applications see no difference
    CREATE VIEW Employee AS
    SELECT p.emp_id, p.emp_name, j.salary, j.dept_id
    FROM   Employee_Personal p JOIN Employee_Job j ON p.emp_id = j.emp_id;
    ```
    - This form is `harder to achieve`, because a change to the logical structure often genuinely changes what the application needs to know — for example, removing a column that an application displays cannot be hidden by any view.

    Comparison

    | Point | Physical data independence | Logical data independence |
    |---|---|---|
    | Levels separated | Internal and conceptual | Conceptual and external |
    | Changes absorbed | Storage, indexes, files | Tables, columns, relationships |
    | Difficulty | Easier | Harder |
    | Mechanism | The DBMS storage layer | Views |
    | Support in practice | Complete | Partial |

    Why it matters
    - Without it, adding an index or reorganising storage would require every application to be recompiled. Data independence is what allows a DBA to tune a production system for performance while the applications above it carry on unchanged.

17. **(ii) Database এর Table and View এর মধ্যে পার্থক্য লিখুন। E-R diagram এর প্রয়োজনীয়তা লিখুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 785 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    Table vs View

    | Point | Table | View |
    |---|---|---|
    | Nature | A `real` object that physically stores data | A `virtual` table defined by a stored SELECT statement |
    | Storage | Occupies disk space | Stores no data; only the query definition is saved |
    | Data source | Its own rows | Derived from one or more base tables each time it is used |
    | Created with | `CREATE TABLE` | `CREATE VIEW` |
    | Updatable | Always | Only under restrictions — no aggregates, GROUP BY, DISTINCT or (usually) joins |
    | Indexes | Can be indexed | Cannot be indexed directly (except SQL Server indexed views and materialised views) |
    | Performance | Direct access | The underlying query runs each time, so it can be slower |
    | Purpose | Store data | Simplify complex queries, restrict access, present data differently |
    | Effect of dropping | The data is lost | Only the definition is lost; the base data is untouched |
    | Security use | Coarse — table-level permissions | `Fine` — expose only chosen columns and rows |

    ```sql
    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,
        emp_name VARCHAR(100),
        salary   DECIMAL(10,2),
        dept_id  INT
    );

    CREATE VIEW PublicStaff AS
    SELECT emp_id, emp_name, dept_id       -- salary deliberately excluded
    FROM   Employee;

    GRANT SELECT ON PublicStaff TO clerk;  -- the clerk cannot reach Employee at all
    ```

    Why views are used
    - `Security` — expose only permitted columns and rows.
    - `Simplicity` — a five-table join is presented as one virtual table.
    - `Logical data independence` — the base tables can be restructured and the view redefined, so applications continue to work.
    - `Consistency` — one definition of a business figure, used by everyone.

    Necessity of an E-R diagram
    - An `Entity-Relationship diagram` is a graphical model of the data: entities (rectangles), attributes (ovals) and relationships (diamonds), with cardinality marked on each relationship.

    Why it is needed
    - `Communication` — it lets designers, developers and non-technical stakeholders discuss the data model in one picture, before any code exists. Errors caught here cost nothing; the same errors caught after implementation are expensive.
    - `Blueprint for the database` — entities become tables, attributes become columns, and relationships become foreign keys or junction tables. The conversion is mechanical once the diagram is right.
    - `Reveals the relationships and their cardinality` — one-to-one, one-to-many and many-to-many, which decides where each foreign key goes and whether a junction table is required.
    - `Supports normalisation` — a clear model exposes redundancy and update anomalies early.
    - `Documentation` — it remains the reference for anyone maintaining or extending the system.
    - `Completeness check` — it makes missing entities and forgotten relationships visible in a way that a list of tables does not.

    ```
       +----------+       /-----------\       +----------+
       | Student  |------<  Enrolls    >------| Course   |
       +----------+  M    \-----------/   N   +----------+
            |                    |                  |
        [student_id]          [grade]           [course_id]
        [name]                                  [title]
    ```
    - The M:N relationship shown here tells the designer immediately that a third table, `Enrollment(student_id, course_id, grade)`, is required — which is exactly the kind of decision the diagram exists to make obvious.

18. **(a) Distinguish between table and view in database management system.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 802 (ET: N/A)]*

    Answer:

    | Point | Table | View |
    |---|---|---|
    | Definition | A database object that `physically stores` rows and columns | A `virtual table` defined by a stored SELECT statement |
    | Physical storage | Occupies disk space | Stores no data — only the query text |
    | Data | Its own | Derived from one or more base tables at the moment of use |
    | Created by | `CREATE TABLE` | `CREATE VIEW` |
    | Contains | Actual records | A saved query |
    | Updatable | Always | Only when the mapping to one base table is unambiguous |
    | Indexes | Yes | Not directly, except SQL Server indexed views and Oracle materialised views |
    | Constraints | Can carry PRIMARY KEY, FOREIGN KEY, CHECK | Cannot; the base tables carry them |
    | Performance | Direct read | The underlying query executes each time |
    | Effect of DROP | Data is destroyed | Only the definition is removed |
    | Security role | Table-level grants only | Column-level and row-level restriction |
    | Maintenance | Data must be maintained | Automatically reflects the current base data |

    Example
    ```sql
    -- base table
    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,
        emp_name VARCHAR(100),
        salary   DECIMAL(10,2),
        dept_id  INT
    );

    -- view: hides salary and shows only one department
    CREATE VIEW IT_Staff AS
    SELECT emp_id, emp_name, dept_id
    FROM   Employee
    WHERE  dept_id = 10;

    SELECT * FROM IT_Staff;      -- used exactly like a table
    ```
    - If a new employee is inserted into `Employee` with `dept_id = 10`, they appear in `IT_Staff` immediately, because the view is recomputed on every use.

    When a view can be updated
    - Generally only if it selects from a `single` base table and contains no `DISTINCT`, `GROUP BY`, aggregate function, `UNION` or set operator, and includes every NOT NULL column of the base table without a default.
    ```sql
    UPDATE IT_Staff SET emp_name = 'Karim Ahmed' WHERE emp_id = 101;   -- allowed
    ```
    - A view containing `AVG(salary) GROUP BY dept_id` cannot be updated, because there is no single row to change.

    Materialised view — the middle case
    - A `materialised view` actually `stores` the result, and is refreshed on a schedule or on commit. It behaves like a table for reading (fast, indexable) but like a view for definition (derived from base tables). The trade-off is freshness against speed. Oracle and PostgreSQL support them; MySQL does not.

    Why views are used
    - Security (hide columns and rows), simplicity (encapsulate a complex join), logical data independence (redefine the view when base tables change), and consistency (one agreed definition of a derived figure).

19. **Database এর সর্বনিম্ন Unit কোনটি?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 944 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The smallest unit of a database is a `field` — also called a `data item` or `attribute value`.

    The hierarchy, smallest to largest
    ```
    Bit  ->  Character  ->  Field  ->  Record  ->  File (Table)  ->  Database
    ```

    | Level | Meaning | Example |
    |---|---|---|
    | `Bit` | A single 0 or 1 — the smallest unit of storage | 1 |
    | `Character (byte)` | A single letter, digit or symbol | 'K' |
    | `Field` | `The smallest meaningful unit of data` — one attribute value | "Karim" |
    | `Record (tuple / row)` | A collection of related fields describing one entity | 101, Karim, 50000 |
    | `Table (file / relation)` | A collection of related records | The whole Employee table |
    | `Database` | A collection of related tables | The company database |

    Illustration
    ```
    Employee table
    +--------+----------+--------+
    | emp_id | emp_name | salary |     <- column names (attributes)
    +--------+----------+--------+
    |  101   | Karim    | 50000  |     <- one RECORD (row)
    |  102   | Rahim    | 60000  |
    +--------+----------+--------+
        ^        ^
        |        +--- one FIELD: the value "Karim"
        +--- one FIELD: the value 101
    ```

    Two readings of the question, both worth stating
    - If the question means the smallest unit that carries `meaning`, the answer is the `field` — a single attribute value, which is the smallest thing a user can address in SQL.
    - If it means the smallest unit of `storage`, the answer is the `bit`, or the `character` for text.
    - Examination papers on database concepts normally intend the `field`, because the hierarchy field → record → file → database is the standard one taught.

    Related point — atomicity
    - `First normal form` requires that every field hold an `atomic` (indivisible) value. Storing "Dhaka, Bangladesh, 1207" in one address field breaks 1NF, because the field is then not the smallest unit — it should be split into city, country and postcode.

20. **DBMS বলতে কী বোঝানো হয়? DBMS শ্রেণিভিন্যাস বর্ণনা করুন।** *[40th BCS 2020 compact it 971-972 (ET: BPSC)]*

    Answer: (Answered in English, as required for IT topics.)

    What is a DBMS
    - A `Database Management System` is software that allows users to create, store, retrieve, update and manage data in a database, while controlling access to it.
    - It sits between the user or application and the physical data files, so users work with tables and queries instead of storage.
    - Functions: data definition, data manipulation, security, integrity, concurrency control, transaction management with ACID guarantees, backup and recovery, and metadata management.
    - Examples: MySQL, PostgreSQL, Oracle, SQL Server, MongoDB.

    Classification of DBMS

    1. `By data model` — the most important classification
    - `Hierarchical` — data in a tree, each child having exactly one parent. Fast for one-to-many but rigid, and many-to-many is impossible. Example: IBM IMS.
    - `Network` — a graph in which a record can have several parents, so many-to-many is supported. More flexible but complex. Example: IDMS, CODASYL.
    - `Relational (RDBMS)` — data in tables linked by keys, queried with SQL. Simple, mathematically grounded, and dominant today. Examples: Oracle, MySQL, PostgreSQL, SQL Server.
    - `Object-oriented` — data stored as objects with attributes and methods, matching object-oriented programming. Example: ObjectDB, db4o.
    - `Object-relational` — relational plus user-defined types and inheritance. Example: PostgreSQL, Oracle.
    - `NoSQL` — non-relational, designed for scale and flexible schemas:
      - Document: MongoDB, CouchDB
      - Key-value: Redis, DynamoDB
      - Column-family: Cassandra, HBase
      - Graph: Neo4j

    2. `By number of users`
    - `Single-user` — one user at a time (MS Access, SQLite).
    - `Multi-user` — many concurrent users (Oracle, MySQL).

    3. `By location of the data`
    - `Centralised` — the whole database on one machine.
    - `Distributed` — spread across several machines. `Homogeneous` if all sites run the same DBMS, `heterogeneous` if they differ.
    - `Cloud` — hosted as a managed service (Amazon RDS, Azure SQL).

    4. `By purpose`
    - `OLTP` — online transaction processing, optimised for many small fast writes: banking, ticketing.
    - `OLAP` — online analytical processing, optimised for large read-only analytical queries: data warehouses.

    5. `By licensing`
    - `Open source` — MySQL, PostgreSQL, MariaDB, SQLite.
    - `Commercial` — Oracle, SQL Server, IBM Db2.

    Comparison of the three classical models

    | Point | Hierarchical | Network | Relational |
    |---|---|---|---|
    | Structure | Tree | Graph | Tables |
    | Parent per child | One | Many | Not applicable |
    | Many-to-many | Not supported | Supported | Supported via a junction table |
    | Navigation | Pointer-based, procedural | Pointer-based | Declarative, using SQL |
    | Flexibility | Low | Medium | High |
    | Status | Legacy | Legacy | Dominant |

21. **Define View, Materialized View. Difference between View and Materialized View and Usage of two.** *[RAKUB Assistant Database Administrator 2020 compact it 1012-1013 (ET: E-Zone)]*

    Answer:

    View
    - A `view` is a virtual table defined by a stored SELECT statement. It holds `no data of its own`; the underlying query runs every time the view is used, so it always reflects the current state of the base tables.
    ```sql
    CREATE VIEW DeptSummary AS
    SELECT dept_id, COUNT(*) AS staff, AVG(salary) AS avg_salary
    FROM   Employee
    GROUP  BY dept_id;

    SELECT * FROM DeptSummary;      -- the SELECT above executes now
    ```

    Materialised view
    - A `materialised view` stores the `result` of the query physically on disk, like a table. It is not recomputed on each access; instead it is `refreshed` — on a schedule, on demand, or on commit.
    ```sql
    -- Oracle / PostgreSQL
    CREATE MATERIALIZED VIEW DeptSummary_MV AS
    SELECT dept_id, COUNT(*) AS staff, AVG(salary) AS avg_salary
    FROM   Employee
    GROUP  BY dept_id;

    REFRESH MATERIALIZED VIEW DeptSummary_MV;      -- update it
    ```

    Comparison

    | Point | View | Materialised view |
    |---|---|---|
    | Data stored | `No` — definition only | `Yes` — the result is stored |
    | Disk space | Negligible | Same as a table |
    | Freshness | `Always current` | Stale until refreshed |
    | Query speed | Slower — recomputed each time | `Much faster` — a simple read |
    | Indexes | Not possible directly | `Possible` |
    | Refresh needed | Never | Yes, manually or on a schedule |
    | Effect of base-table changes | Seen immediately | Not seen until refresh |
    | Overhead on writes | None | Refresh cost |
    | Supported by | Every DBMS | Oracle, PostgreSQL, SQL Server (indexed views); `not MySQL` |

    When to use each

    Use a `view` when
    - The data must always be `current` — account balances, order status, anything transactional.
    - The purpose is `security`, hiding columns or rows from certain users.
    - The purpose is `simplification`, giving a complex join a friendly name.
    - The base tables change frequently, so any stored copy would be stale immediately.
    - Storage is a concern.

    Use a `materialised view` when
    - The query is `expensive` — large aggregations, joins across many tables, or a data-warehouse summary.
    - The same expensive result is `read many times` between updates.
    - Slightly stale data is `acceptable` — a daily sales summary, a monthly report, a dashboard refreshed hourly.
    - The result must be `indexed` for fast filtering.
    - The underlying tables are in a remote or distributed database, so recomputing is costly.

    Refresh strategies
    - `COMPLETE` — rebuild the whole thing; simple but expensive.
    - `FAST / INCREMENTAL` — apply only the changes, using a materialised view log.
    - `ON COMMIT` — refresh as soon as a base table changes; always current but slows every write.
    - `ON DEMAND` — refresh when asked, typically overnight.

    - The trade-off in one line: a view trades `speed` for `freshness`; a materialised view trades `freshness` for `speed`.

22. **What are the roles of Database Engineer?** *[RAKUB Assistant Database Administrator 2020 compact it 1014 (ET: E-Zone)]*

    Answer: A `Database Engineer` designs, builds and maintains the data systems on which applications and analytics depend. The role sits between a DBA and a software engineer.

    Main roles

    1. `Database design and data modelling`
    - Designing schemas, choosing data types, normalising tables, and deciding when to denormalise deliberately for performance. Producing ER diagrams and documenting the model.

    2. `Building and maintaining data pipelines`
    - Writing ETL or ELT processes that extract data from source systems, transform it and load it into the database or warehouse. Scheduling and monitoring those jobs.

    3. `Writing and optimising SQL`
    - Producing stored procedures, functions, triggers and complex queries; reading execution plans and rewriting queries that perform badly.

    4. `Performance tuning`
    - Designing indexes, partitioning large tables, tuning configuration, managing statistics, and diagnosing slow or blocking queries.

    5. `Automation and scripting`
    - Automating deployments, backups, monitoring and routine maintenance with shell, Python or the DBMS's own scripting.

    6. `Schema migration and version control`
    - Managing schema changes through migration tools such as Flyway or Liquibase, so that changes move safely from development to production and can be rolled back.

    7. `Data integrity and quality`
    - Defining constraints, validation rules and reconciliation checks; investigating and correcting data quality problems.

    8. `Security implementation`
    - Applying least-privilege access, encryption, masking of sensitive columns and audit logging.

    9. `Backup, recovery and high availability`
    - Implementing backup strategies, replication, clustering and failover, and testing recovery.

    10. `Capacity planning and scaling`
    - Forecasting growth; implementing sharding, partitioning, read replicas and caching layers.

    11. `Supporting developers`
    - Reviewing SQL and schema changes proposed by application teams, and advising on efficient access patterns.

    12. `Working with modern data platforms`
    - Cloud databases (RDS, Aurora, Cloud SQL), NoSQL stores, data warehouses (Snowflake, BigQuery, Redshift), and streaming systems (Kafka).

    Skills required
    - Strong SQL and knowledge of at least one DBMS internally; data modelling; a programming language, usually Python; Linux; cloud platforms; and version control.

    How the related roles differ

    | Role | Primary concern |
    |---|---|
    | `Database Administrator` | Keeping databases running: backup, security, tuning, availability |
    | `Database Engineer` | Building and evolving the database and its pipelines |
    | `Data Engineer` | Large-scale data movement and processing, warehouses and streaming |
    | `Data Architect` | The overall data strategy and how systems fit together |
    | `Data Analyst / Scientist` | Extracting meaning from the data |

    - In many organisations, especially smaller ones, one person performs several of these roles.

23. **A company needs key person for DBMS. What is his/her duty as key person?** *[Bangladesh Bank Assistant Programmer 2019 compact it 1155 (ET: DU)]*

    Answer: The key person for a company's DBMS is the `Database Administrator (DBA)`. Their duties are as follows.

    1. `Database design and implementation`
    - Designing the schema, choosing data types, defining primary and foreign keys, normalising the tables, and creating databases, views and indexes.

    2. `Installation, configuration and upgrades`
    - Installing the DBMS, tuning its configuration, applying security patches, and planning version migrations with minimal downtime.

    3. `Security administration`
    - Creating users and roles; granting the `minimum necessary` privileges; enforcing password policy; configuring encryption at rest and in transit; and auditing access to sensitive data.

    4. `Backup and recovery` — the most critical duty
    - Designing the backup strategy, scheduling and monitoring it, and `regularly testing the restore`. An untested backup is not a backup. Defining recovery point and recovery time objectives with the business.

    5. `Performance monitoring and tuning`
    - Identifying slow queries, reading execution plans, adding or removing indexes, tuning memory and buffer settings, partitioning large tables, and keeping optimiser statistics current.

    6. `Ensuring availability`
    - Configuring replication, clustering and failover so that a hardware failure does not stop the business; maintaining a disaster recovery site and rehearsing the switch-over.

    7. `Capacity planning`
    - Forecasting data growth, allocating storage, archiving and purging old data before space becomes a crisis.

    8. `Maintaining data integrity`
    - Defining and enforcing constraints, running consistency checks, and investigating anomalies.

    9. `Troubleshooting`
    - Diagnosing deadlocks, blocking, connection exhaustion, corruption and failed jobs, usually under time pressure.

    10. `Supporting developers and users`
    - Reviewing SQL and schema changes for efficiency and safety; advising on access patterns; managing the promotion of changes from development to production.

    11. `Documentation and compliance`
    - Maintaining the data dictionary and schema documentation; meeting regulatory obligations for data retention, privacy and audit.

    12. `Change management`
    - Controlling how schema changes reach production, with a tested rollback for every change.

    The three duties that matter most
    - If the role had to be reduced to three things: `keep the data safe` (backup, recovery, security), `keep it correct` (integrity constraints), and `keep it available and fast` (high availability and tuning). Everything else supports those.

    Skills the person needs
    - SQL and DBMS internals, performance tuning, backup and recovery, operating systems and storage, scripting for automation, security practice, and the judgement to say no to a risky change.

24. **What is RDBMS? Why data are stored in database system instead of file?** *[ICT Ministry Assistant Programmer 2017 compact it 1236 (ET: N/A)]*

    Answer:

    What is an RDBMS
    - A `Relational Database Management System` is software that stores data in `tables` (relations) of rows and columns, and manages the relationships between those tables using `keys`.
    - It is based on E. F. Codd's relational model of 1970 and is accessed through `SQL`.

    Characteristics
    - Data held in two-dimensional tables; every row uniquely identified by a `primary key`; tables linked by `foreign keys`; constraints enforcing integrity; support for `normalisation`; and `ACID` transaction guarantees.
    - Examples: Oracle, MySQL, PostgreSQL, SQL Server, IBM Db2, SQLite.
    - A plain `DBMS` may store data as files or in a hierarchy with no enforced relationships; an `RDBMS` enforces the relational model, keys and referential integrity.

    Why data is stored in a database rather than in files

    1. `Reduced redundancy`
    - In a file system the same customer address is duplicated across the sales, billing and delivery files. A database stores it once, normalised, and shares it.

    2. `No inconsistency`
    - Because the data exists once, an update is seen everywhere. In a file system, updating one copy and forgetting the others leaves two contradictory answers.

    3. `Integrity is enforced by the system`
    - PRIMARY KEY, FOREIGN KEY, CHECK, NOT NULL and UNIQUE are enforced by the database itself. A file system enforces nothing; every program must implement the rules, and any one of them can get it wrong.

    4. `Security and access control`
    - Users, roles and privileges control access at table and column level, and views hide sensitive data. Files offer only coarse operating-system permissions.

    5. `Concurrent multi-user access`
    - Locking or MVCC lets many users read and write simultaneously. Two programs writing the same file at once will corrupt it.

    6. `Transactions with ACID guarantees`
    - A bank transfer either debits and credits both accounts or does neither. A file system has no concept of a transaction, so a crash midway loses money.

    7. `Backup and recovery`
    - The transaction log allows automatic recovery to a consistent state after a crash. File-based recovery means restoring yesterday's copy and losing a day's work.

    8. `Efficient querying`
    - SQL states what is wanted; the optimiser chooses indexes and join strategies. In a file system every query must be programmed by hand and every search is a full scan.

    9. `Data independence`
    - Storage structures can change without rewriting applications. In a file system, changing a record layout means changing every program that reads it.

    10. `Data sharing`
    - One database serves many applications with a single consistent version of the truth.

    Summary

    | Point | File system | RDBMS |
    |---|---|---|
    | Redundancy | High | Controlled |
    | Consistency | Fragile | Enforced |
    | Integrity | In each program | In the database |
    | Security | File-level | User, role, table, column |
    | Concurrency | Unsafe | Managed |
    | Transactions | None | ACID |
    | Recovery | Manual | Automatic |
    | Querying | Program per query | Declarative SQL |

    - When a file is still the better choice: a small, single-user, read-only dataset, or a configuration file. The overhead of a database is only worth paying when the data is shared, changing and important.

25. **a) What is a database? Discuss the importance of database.** *[Ministry of Finance Programmer 2013 compact it 1272 (ET: N/A)]*

    Answer:

    What is a database
    - A `database` is an organised collection of related data, stored electronically so that it can be efficiently accessed, managed and updated.
    - It is `structured` (usually into tables), `related` (it describes some part of the real world), `persistent` (it survives program termination), `shared` (many users and applications use it at once) and `managed` by a DBMS.

    ```
    Database: Bank

    Table: Customer                     Table: Account
    +---------+--------+-------+        +---------+---------+---------+
    | cust_id | name   | city  |        | acc_no  | cust_id | balance |
    +---------+--------+-------+        +---------+---------+---------+
    |  101    | Karim  | Dhaka |        | A1001   |  101    | 50000   |
    |  102    | Rahim  | Sylhet|        | A1002   |  101    | 25000   |
    +---------+--------+-------+        +---------+---------+---------+
    ```

    Importance of a database

    1. `Single source of truth`
    - Data is stored once and shared, so every department works from the same figures. Without it, sales, finance and delivery each keep their own version and they disagree.

    2. `Accuracy and consistency`
    - Constraints prevent invalid data from ever being stored, and an update is seen immediately by every application.

    3. `Efficient retrieval`
    - Indexes and query optimisation find one record among millions in milliseconds. A file-based search would scan everything.

    4. `Security and controlled access`
    - Users, roles and privileges determine exactly who may see or change what, and every access can be audited. This is essential for financial and personal data.

    5. `Concurrent multi-user working`
    - Hundreds of tellers, ATMs and web users can transact simultaneously without corrupting each other's work.

    6. `Transaction reliability`
    - ACID guarantees mean a transfer either completes fully or not at all — no money is created or destroyed by a crash.

    7. `Backup and recovery`
    - Logging and replication allow the organisation to survive hardware failure, and to meet regulatory obligations for retention.

    8. `Supports decision-making`
    - Reporting, analytics and data warehousing turn stored transactions into information for management.

    9. `Scalability and growth`
    - Volume can grow from thousands to billions of rows through indexing, partitioning, replication and sharding.

    10. `Reduced cost and duplicated effort`
    - One well-designed store replaces many overlapping files and the staff time spent reconciling them.

    11. `Enables modern applications`
    - Every banking system, e-commerce site, airline reservation system, hospital record system, mobile application and government register rests on a database. Almost no significant software exists without one.

    - In one sentence: a database turns raw data into a `shared, reliable, secure and queryable organisational asset`, which is why it is the foundation of essentially every information system in use today.

26. **b) Specify the functions of the database administration.** *[Ministry of Finance Programmer 2013 compact it 1272 (ET: N/A)]*

    Answer: `Database administration` is the function responsible for the design, security, performance, availability and integrity of an organisation's databases. Its specific functions are as follows.

    1. `Database design and implementation`
    - Defining the schema, choosing data types, establishing primary and foreign keys, normalising the structure, and creating the databases, tables, views and indexes.

    2. `Installation and configuration`
    - Installing the DBMS, setting configuration parameters, applying patches and planning upgrades.

    3. `Security administration`
    - Creating users and roles; granting and revoking privileges on the principle of least privilege; enforcing password policy; configuring encryption; and auditing access to sensitive data.

    4. `Backup and recovery`
    - Designing the backup strategy — full, incremental, differential — scheduling and monitoring it, and testing the restore procedure regularly. Defining recovery point and recovery time objectives with the business.

    5. `Performance monitoring and tuning`
    - Identifying slow queries and reading their execution plans; creating and removing indexes; tuning memory, buffers and connection limits; partitioning large tables; and refreshing optimiser statistics.

    6. `Capacity planning and storage management`
    - Forecasting growth, allocating tablespaces and file groups, archiving and purging historical data.

    7. `Ensuring data integrity`
    - Defining and maintaining constraints, and running consistency and reconciliation checks.

    8. `High availability and disaster recovery`
    - Configuring replication, clustering, log shipping and failover; maintaining and rehearsing a disaster recovery plan.

    9. `Concurrency and transaction management`
    - Choosing isolation levels, monitoring locks and deadlocks, and resolving blocking.

    10. `Change and version control`
    - Managing how schema changes move from development through testing to production, with a tested rollback for each.

    11. `Documentation and metadata management`
    - Maintaining the data dictionary, schema documentation and operational runbooks.

    12. `User support and training`
    - Helping developers write efficient and safe SQL, and advising on access patterns and schema design.

    13. `Regulatory compliance`
    - Meeting obligations for data retention, privacy, audit trails and reporting.

    14. `Monitoring and alerting`
    - Watching space, performance, replication lag, failed jobs and error logs, with alerts before problems become outages.

    The functions ranked by importance
    - If reduced to three: `protect the data` (backup, recovery, security), `keep it correct` (integrity), and `keep it available and responsive` (high availability, tuning). Every other function supports one of these three.

    - Related distinction: `data administration` is the policy-level function — deciding what data the organisation holds, what it means and who owns it — while `database administration` is the technical function of building and running the systems that store it.

## ER Diagram & Database Design (25)

1. BSCPL regularly publishes multiple job vacancies, where each Job is identified by a unique Job ID and contains information such as Job Title, Starting Salary, Job Description, and other relevant attributes. An Applicant is identified by a unique Applicant ID and has attributes such as Name, Date of Birth, Starting/Joining Date, Contact Information, and other details. An applicant can apply for only one job, while a particular job can receive applications from many applicants. Design the ER diagram for this system, showing the entities, attributes, primary keys, relationship, cardinalities, and participation constraints. [BSCCPL AME 21-08-2026 (BUET)]

   Answer: An applicant applies for `only one` job, while a job receives `many` applications, so the relationship is `1:N` from Job to Applicant.

   ER diagram
   ```mermaid
   erDiagram
       JOB ||--o{ APPLICANT : "receives application from"
       JOB {
           int Job_ID PK
           string Job_Title
           decimal Starting_Salary
           string Job_Description
           date Posting_Date
           int Vacancies
       }
       APPLICANT {
           int Applicant_ID PK
           string Name
           date Date_of_Birth
           date Joining_Date
           string Contact_Info
           string Qualification
           int Job_ID FK
       }
   ```

   Chen notation, as drawn in the examination
   ```
       +-------------+                                 +---------------+
       |    JOB      |                                 |   APPLICANT   |
       +-------------+                                 +---------------+
             |                                                 |
             |            /---------------\                    |
             +===========<   Applies_For   >-------------------+
                1        \---------------/           N
           (double line =                        (single line =
            total participation)                  partial participation)

     JOB attributes:                     APPLICANT attributes:
      (Job_ID)  <- underlined, PK         (Applicant_ID) <- underlined, PK
      (Job_Title)                         (Name)
      (Starting_Salary)                   (Date_of_Birth)
      (Job_Description)                   (Joining_Date)
      (Posting_Date)                      (Contact_Info)
   ```

   The four things the question asks for

   `Entities and primary keys`
   - `JOB` — primary key `Job_ID`
   - `APPLICANT` — primary key `Applicant_ID`

   `Attributes`
   - Job: Job_ID, Job_Title, Starting_Salary, Job_Description, Posting_Date, Vacancies.
   - Applicant: Applicant_ID, Name, Date_of_Birth, Joining_Date, Contact_Info, Qualification.
   - `Contact_Info` is a `composite` attribute (phone, email, address) and could be decomposed; `Age` would be a `derived` attribute, computed from Date_of_Birth.

   `Cardinality — 1 : N`
   - One Job → many Applicants.
   - One Applicant → exactly one Job.

   `Participation constraints`
   - `APPLICANT: total participation` (drawn as a double line). Every applicant must apply for some job — an applicant who has applied for nothing does not exist in this system.
   - `JOB: partial participation` (single line). A newly posted job may have no applicants yet.

   Converting to tables
   - For a 1:N relationship, the primary key of the `1` side becomes a `foreign key` on the `N` side. No separate relationship table is needed.
   ```sql
   CREATE TABLE Job (
       Job_ID          INT PRIMARY KEY,
       Job_Title       VARCHAR(100) NOT NULL,
       Starting_Salary DECIMAL(10,2),
       Job_Description TEXT,
       Posting_Date    DATE
   );

   CREATE TABLE Applicant (
       Applicant_ID  INT PRIMARY KEY,
       Name          VARCHAR(100) NOT NULL,
       Date_of_Birth DATE,
       Joining_Date  DATE,
       Contact_Info  VARCHAR(200),
       Job_ID        INT NOT NULL,          -- NOT NULL enforces total participation
       FOREIGN KEY (Job_ID) REFERENCES Job(Job_ID)
   );
   ```
   - Note how `NOT NULL` on the foreign key is what implements the total participation constraint in SQL.

   Design note
   - If the requirement changed so that an applicant `could apply for several jobs`, the relationship would become `M:N` and a third table would be required:
   ```sql
   CREATE TABLE Application (
       Job_ID       INT,
       Applicant_ID INT,
       Applied_Date DATE,
       Status       VARCHAR(20),
       PRIMARY KEY (Job_ID, Applicant_ID),
       FOREIGN KEY (Job_ID)       REFERENCES Job(Job_ID),
       FOREIGN KEY (Applicant_ID) REFERENCES Applicant(Applicant_ID)
   );
   ```

2. **(a) Design an ER diagram for a library management systems where-** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1349 (ET: N/A)]*
   * **(i) A library has multiple books.**
   * **(ii) Each book can have multiple copies.**

   Answer: The important design point is the distinction between a `Book` (the title, with its ISBN and author) and a `Copy` (a physical volume on the shelf). A library holds many books, and each book has many copies.

   ER diagram
   ```mermaid
   erDiagram
       LIBRARY  ||--o{ BOOK     : "holds"
       BOOK     ||--o{ COPY     : "has physical"
       MEMBER   ||--o{ LOAN     : "borrows"
       COPY     ||--o{ LOAN     : "is issued in"
       AUTHOR   ||--o{ BOOK     : "writes"

       LIBRARY {
           int Library_ID PK
           string Name
           string Address
       }
       BOOK {
           string ISBN PK
           string Title
           string Publisher
           int Year
           string Category
           int Library_ID FK
       }
       COPY {
           int Copy_ID PK
           string ISBN FK
           string Shelf_Location
           string Status
       }
       MEMBER {
           int Member_ID PK
           string Name
           string Address
           string Phone
           date Membership_Date
       }
       LOAN {
           int Loan_ID PK
           int Copy_ID FK
           int Member_ID FK
           date Issue_Date
           date Due_Date
           date Return_Date
       }
   ```

   Chen notation for the two relationships the question names
   ```
     +----------+          /--------\          +--------+          /------\        +========+
     | LIBRARY  |=========<  Holds   >=========|  BOOK  |=========<  Has   >=======|  COPY  |
     +----------+   1      \--------/     N    +--------+    1     \------/    N   +========+
                                                                                 (weak entity)

     LIBRARY attributes           BOOK attributes            COPY attributes
      (Library_ID) PK              (ISBN) PK                  (Copy_ID) partial key
      (Name)                       (Title)                    (Shelf_Location)
      (Address)                    (Publisher)                (Status)
                                   (Year)
   ```

   Cardinalities
   - `Library : Book` = `1 : N` — one library holds many books; each book belongs to one library.
   - `Book : Copy` = `1 : N` — one title has many physical copies; each copy is of one title.
   - `Member : Loan` = `1 : N`, and `Copy : Loan` = `1 : N`. Together these implement the M:N relationship between members and copies, with `Loan` as the associative entity carrying the dates.

   Participation
   - `Copy` has `total` participation in "Has" — a copy cannot exist without a book. It is arguably a `weak entity`, identified by ISBN plus a copy number.
   - `Book` has partial participation in "Holds" from the library's side, since a library may briefly hold no books.

   Converting to tables
   ```sql
   CREATE TABLE Library (
       Library_ID INT PRIMARY KEY,
       Name       VARCHAR(100) NOT NULL,
       Address    VARCHAR(200)
   );

   CREATE TABLE Book (
       ISBN       VARCHAR(20) PRIMARY KEY,
       Title      VARCHAR(200) NOT NULL,
       Publisher  VARCHAR(100),
       Year       INT,
       Library_ID INT,
       FOREIGN KEY (Library_ID) REFERENCES Library(Library_ID)
   );

   CREATE TABLE Copy (
       Copy_ID        INT PRIMARY KEY,
       ISBN           VARCHAR(20) NOT NULL,
       Shelf_Location VARCHAR(50),
       Status         VARCHAR(20) DEFAULT 'Available',
       FOREIGN KEY (ISBN) REFERENCES Book(ISBN)
   );

   CREATE TABLE Loan (
       Loan_ID     INT PRIMARY KEY,
       Copy_ID     INT NOT NULL,
       Member_ID   INT NOT NULL,
       Issue_Date  DATE NOT NULL,
       Due_Date    DATE NOT NULL,
       Return_Date DATE,
       FOREIGN KEY (Copy_ID)   REFERENCES Copy(Copy_ID),
       FOREIGN KEY (Member_ID) REFERENCES Member(Member_ID)
   );
   ```
   - Why the separation matters: a loan must record `which physical copy` went out, not merely which title, so that the library knows exactly which volume is missing. Modelling `Book` and `Copy` as one entity would make that impossible.

3. **(খ) নিচের ডেটাবেস অনুযায়ী ER ডায়াগ্রাম তৈরি করুন :** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 415 (ET: N/A)]*
   * **Worker** (Worker ID, Worker Name, Hour Rate, Skill Type)
   * **Assignment** (Worker ID, Building ID, Start Date, Num Days)
   * **Building** (Building ID, Address, Building Type)

   Answer: (Answered in English, as required for IT topics.) The `Assignment` relation contains only foreign keys plus descriptive attributes, which is the signature of an `M:N relationship` between Worker and Building.

   ER diagram
   ```mermaid
   erDiagram
       WORKER   ||--o{ ASSIGNMENT : "is assigned"
       BUILDING ||--o{ ASSIGNMENT : "receives"

       WORKER {
           int Worker_ID PK
           string Worker_Name
           decimal Hour_Rate
           string Skill_Type
       }
       BUILDING {
           int Building_ID PK
           string Address
           string Building_Type
       }
       ASSIGNMENT {
           int Worker_ID PK-FK
           int Building_ID PK-FK
           date Start_Date
           int Num_Days
       }
   ```

   Chen notation, as drawn in the examination
   ```
      +-----------+                                    +------------+
      |  WORKER   |                                    |  BUILDING  |
      +-----------+                                    +------------+
           |                                                  |
           |             /----------------\                   |
           +------------<   ASSIGNED_TO    >------------------+
                M        \----------------/          N
                                 |
                       +---------+---------+
                       |                   |
                 (Start_Date)         (Num_Days)     <- descriptive attributes

     WORKER attributes:                  BUILDING attributes:
      (Worker_ID)  <- underlined, PK      (Building_ID) <- underlined, PK
      (Worker_Name)                       (Address)
      (Hour_Rate)                         (Building_Type)
   ```

   Reading the design
   - `WORKER` — primary key `Worker_ID`; attributes Worker_Name, Hour_Rate, Skill_Type.
   - `BUILDING` — primary key `Building_ID`; attributes Address, Building_Type.
   - `ASSIGNMENT` is not an entity in the conceptual model but the `M:N relationship` between them. `Start_Date` and `Num_Days` are `descriptive attributes` of the relationship — they belong to the pairing of a worker with a building, not to either alone.

   Cardinality
   - One worker can be assigned to `many` buildings.
   - One building can have `many` workers assigned.
   - Therefore `M : N`, which is exactly why a third table is needed.

   Converting to tables
   - The rule for an M:N relationship: create a `separate table` whose primary key is the combination of both foreign keys, and place any descriptive attributes there.
   ```sql
   CREATE TABLE Worker (
       Worker_ID   INT PRIMARY KEY,
       Worker_Name VARCHAR(100) NOT NULL,
       Hour_Rate   DECIMAL(8,2),
       Skill_Type  VARCHAR(50)
   );

   CREATE TABLE Building (
       Building_ID   INT PRIMARY KEY,
       Address       VARCHAR(200),
       Building_Type VARCHAR(50)
   );

   CREATE TABLE Assignment (
       Worker_ID   INT,
       Building_ID INT,
       Start_Date  DATE,
       Num_Days    INT,
       PRIMARY KEY (Worker_ID, Building_ID),          -- composite key
       FOREIGN KEY (Worker_ID)   REFERENCES Worker(Worker_ID),
       FOREIGN KEY (Building_ID) REFERENCES Building(Building_ID)
   );
   ```

   A refinement worth mentioning
   - The composite key `(Worker_ID, Building_ID)` allows a worker to be assigned to a building only `once`. If the same worker could return to the same building on a later date, `Start_Date` must join the key:
   ```sql
   PRIMARY KEY (Worker_ID, Building_ID, Start_Date)
   ```
   - This is the kind of question the cardinality alone does not answer, and it is worth stating explicitly in a design answer.

4. **Consider the Schema employee(id, name, salary), equipment(id, name, price), hire(employee_id, equipment_id)**
   **(i) Draw the ERD digram for the relation**
   **(ii) Write the SQL query to show the name of employee who borrow the maximum equipment?** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 462 (ET: BUET)]*

   Answer:

   Schema
   ```
   employee (id, name, salary)
   equipment (id, name, price)
   hire (employee_id, equipment_id)
   ```
   - `hire` contains nothing but two foreign keys, which is the signature of an `M:N` relationship between employee and equipment.

   (i) ER diagram
   ```mermaid
   erDiagram
       EMPLOYEE  ||--o{ HIRE : "borrows"
       EQUIPMENT ||--o{ HIRE : "is borrowed in"

       EMPLOYEE {
           int id PK
           string name
           decimal salary
       }
       EQUIPMENT {
           int id PK
           string name
           decimal price
       }
       HIRE {
           int employee_id PK-FK
           int equipment_id PK-FK
       }
   ```

   Chen notation
   ```
      +------------+                                  +-------------+
      |  EMPLOYEE  |                                  |  EQUIPMENT  |
      +------------+                                  +-------------+
           |                                                 |
           |              /----------\                       |
           +-------------<   HIRE     >----------------------+
                M         \----------/            N

     EMPLOYEE attributes:               EQUIPMENT attributes:
      (id)  <- underlined, PK            (id)  <- underlined, PK
      (name)                             (name)
      (salary)                           (price)
   ```
   - Cardinality: one employee may borrow many pieces of equipment, and one piece of equipment may be borrowed by many employees — `M : N`.
   - The relationship becomes the `hire` table, whose primary key is the pair `(employee_id, equipment_id)`.

   (ii) The employee who borrowed the most equipment
   ```sql
   SELECT   e.name,
            COUNT(*) AS items_borrowed
   FROM     employee e
   JOIN     hire     h ON e.id = h.employee_id
   GROUP BY e.id, e.name
   ORDER BY items_borrowed DESC
   LIMIT    1;
   ```

   Version that correctly handles a tie
   ```sql
   SELECT   e.name, COUNT(*) AS items_borrowed
   FROM     employee e
   JOIN     hire     h ON e.id = h.employee_id
   GROUP BY e.id, e.name
   HAVING   COUNT(*) = (
               SELECT MAX(cnt) FROM (
                   SELECT COUNT(*) AS cnt FROM hire GROUP BY employee_id
               ) t
            );
   ```
   - `ORDER BY ... LIMIT 1` returns only one employee even when several are tied at the top; the `HAVING = MAX` form returns them all. Which is correct depends on the question, and stating the difference is worth marks.

   Sample output
   ```
   hire
   +-------------+--------------+
   | employee_id | equipment_id |
   +-------------+--------------+
   |     101     |      1       |
   |     101     |      2       |
   |     101     |      3       |
   |     102     |      1       |
   +-------------+--------------+

   Result
   +-------+-----------------+
   | name  | items_borrowed  |
   +-------+-----------------+
   | Karim |        3        |
   +-------+-----------------+
   ```

   Related queries on this schema
   ```sql
   -- total value of equipment each employee has borrowed
   SELECT   e.name, SUM(q.price) AS total_value
   FROM     employee e JOIN hire h ON e.id = h.employee_id
   JOIN     equipment q ON h.equipment_id = q.id
   GROUP BY e.id, e.name;

   -- equipment never borrowed by anyone
   SELECT q.name FROM equipment q
   LEFT JOIN hire h ON q.id = h.equipment_id
   WHERE  h.equipment_id IS NULL;
   ```

5. **Develop an entity relationship diagram that describes data objects, relationships and attributes of the following system: -A web based order processing system for a computer store.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 639 (ET: N/A)]*

   Answer: An order-processing system for a computer store centres on Customers placing Orders for Products, with each order containing several line items.

   ER diagram
   ```mermaid
   erDiagram
       CUSTOMER ||--o{ ORDER      : places
       ORDER    ||--|{ ORDER_ITEM : contains
       PRODUCT  ||--o{ ORDER_ITEM : "appears in"
       CATEGORY ||--o{ PRODUCT    : classifies
       ORDER    ||--|| PAYMENT    : "is paid by"
       ORDER    ||--o| SHIPMENT   : "is shipped as"
       SUPPLIER ||--o{ PRODUCT    : supplies

       CUSTOMER {
           int Customer_ID PK
           string Name
           string Email
           string Phone
           string Address
           string Password_Hash
       }
       ORDER {
           int Order_ID PK
           int Customer_ID FK
           datetime Order_Date
           decimal Total_Amount
           string Status
       }
       ORDER_ITEM {
           int Order_ID PK-FK
           int Product_ID PK-FK
           int Quantity
           decimal Unit_Price
       }
       PRODUCT {
           int Product_ID PK
           string Name
           string Description
           decimal Price
           int Stock_Quantity
           int Category_ID FK
           int Supplier_ID FK
       }
       CATEGORY {
           int Category_ID PK
           string Category_Name
       }
       PAYMENT {
           int Payment_ID PK
           int Order_ID FK
           decimal Amount
           string Method
           datetime Payment_Date
           string Status
       }
       SHIPMENT {
           int Shipment_ID PK
           int Order_ID FK
           string Courier
           string Tracking_No
           date Dispatch_Date
           date Delivery_Date
       }
       SUPPLIER {
           int Supplier_ID PK
           string Supplier_Name
           string Contact
       }
   ```

   The relationships and their cardinality

   | Relationship | Cardinality | Explanation |
   |---|---|---|
   | Customer places Order | `1 : N` | One customer may place many orders; each order belongs to one customer |
   | Order contains Order_Item | `1 : N` | An order has at least one line item |
   | Product appears in Order_Item | `1 : N` | A product may appear in many orders |
   | Customer buys Product | `M : N` | Resolved through Order and Order_Item |
   | Category classifies Product | `1 : N` | One category has many products |
   | Supplier supplies Product | `1 : N` | One supplier supplies many products |
   | Order has Payment | `1 : 1` | Each order is paid once |
   | Order has Shipment | `1 : 0..1` | An order is shipped once, or not yet at all |

   The three design points worth stating
   - `ORDER_ITEM is the associative entity` that resolves the M:N relationship between Order and Product. Its descriptive attributes are `Quantity` and `Unit_Price`.
   - `Unit_Price is stored on the order line, not read from Product`. This is essential: the price at the time of purchase must be preserved, because the product's price will change later and old invoices must not change with it.
   - `Order has total participation` in "contains" — an order with no items is meaningless.

   Core tables
   ```sql
   CREATE TABLE Customer (
       Customer_ID INT PRIMARY KEY,
       Name        VARCHAR(100) NOT NULL,
       Email       VARCHAR(100) UNIQUE,
       Address     VARCHAR(200)
   );

   CREATE TABLE Orders (
       Order_ID     INT PRIMARY KEY,
       Customer_ID  INT NOT NULL,
       Order_Date   DATETIME NOT NULL,
       Total_Amount DECIMAL(12,2),
       Status       VARCHAR(20) DEFAULT 'Pending',
       FOREIGN KEY (Customer_ID) REFERENCES Customer(Customer_ID)
   );

   CREATE TABLE Order_Item (
       Order_ID   INT,
       Product_ID INT,
       Quantity   INT NOT NULL CHECK (Quantity > 0),
       Unit_Price DECIMAL(10,2) NOT NULL,
       PRIMARY KEY (Order_ID, Product_ID),
       FOREIGN KEY (Order_ID)   REFERENCES Orders(Order_ID) ON DELETE CASCADE,
       FOREIGN KEY (Product_ID) REFERENCES Product(Product_ID)
   );
   ```
   - `ON DELETE CASCADE` on Order_Item is correct here: a line item has no meaning once its order is deleted. That is a genuine ownership relationship.

6. **Draw a ER diagram for BPL.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 662 (ET: N/A)]*

   Answer: A cricket league such as the BPL is modelled around Teams, Players, Matches and Venues, with a player belonging to a team and a match played between two teams.

   ER diagram
   ```mermaid
   erDiagram
       TEAM     ||--o{ PLAYER       : "has"
       TEAM     ||--o{ MATCH_TEAM   : "plays in"
       MATCH    ||--|{ MATCH_TEAM   : "involves"
       VENUE    ||--o{ MATCH        : hosts
       MATCH    ||--o{ PERFORMANCE  : records
       PLAYER   ||--o{ PERFORMANCE  : achieves
       COACH    ||--|| TEAM         : coaches
       UMPIRE   ||--o{ MATCH        : officiates

       TEAM {
           int Team_ID PK
           string Team_Name
           string City
           string Owner
           int Coach_ID FK
       }
       PLAYER {
           int Player_ID PK
           string Name
           date DOB
           string Role
           string Country
           int Team_ID FK
       }
       MATCH {
           int Match_ID PK
           date Match_Date
           time Start_Time
           int Venue_ID FK
           int Winner_Team_ID FK
           string Result
       }
       MATCH_TEAM {
           int Match_ID PK-FK
           int Team_ID PK-FK
           int Score
           int Wickets
           decimal Overs
       }
       VENUE {
           int Venue_ID PK
           string Stadium_Name
           string City
           int Capacity
       }
       PERFORMANCE {
           int Match_ID PK-FK
           int Player_ID PK-FK
           int Runs_Scored
           int Balls_Faced
           int Wickets_Taken
           decimal Overs_Bowled
       }
       COACH {
           int Coach_ID PK
           string Coach_Name
           string Nationality
       }
       UMPIRE {
           int Umpire_ID PK
           string Umpire_Name
           string Country
       }
   ```

   Relationships and cardinality

   | Relationship | Cardinality | Note |
   |---|---|---|
   | Team has Player | `1 : N` | A player belongs to one team in a season |
   | Team plays Match | `M : N` | Resolved by MATCH_TEAM; each match involves exactly 2 teams |
   | Venue hosts Match | `1 : N` | One stadium hosts many matches |
   | Player performs in Match | `M : N` | Resolved by PERFORMANCE, holding the scorecard |
   | Coach coaches Team | `1 : 1` | One coach per team |
   | Umpire officiates Match | `M : N` | Several umpires per match; simplify to 1:N if required |

   The design decisions worth explaining
   - `MATCH_TEAM` is the associative entity resolving the M:N between Match and Team. It also carries the descriptive attributes `Score`, `Wickets` and `Overs`, which belong to the pairing of a team with a match, not to either alone.
   - `PERFORMANCE` does the same for Player and Match, holding the individual scorecard — runs, balls faced, wickets taken. This is the table every statistic in the tournament is computed from.
   - `Winner_Team_ID` in MATCH is a `derived` attribute — it could be computed from the scores, but storing it makes standings queries far simpler. Storing it is a deliberate denormalisation.
   - A `player transferring between teams across seasons` would break the simple 1:N from Team to Player; the correct model would then add a `Team_Player(Team_ID, Player_ID, Season)` table.

   Key tables
   ```sql
   CREATE TABLE Team (
       Team_ID   INT PRIMARY KEY,
       Team_Name VARCHAR(100) NOT NULL UNIQUE,
       City      VARCHAR(50),
       Owner     VARCHAR(100)
   );

   CREATE TABLE Player (
       Player_ID INT PRIMARY KEY,
       Name      VARCHAR(100) NOT NULL,
       Role      VARCHAR(30),
       Team_ID   INT,
       FOREIGN KEY (Team_ID) REFERENCES Team(Team_ID)
   );

   CREATE TABLE Match_Team (
       Match_ID INT,
       Team_ID  INT,
       Score    INT,
       Wickets  INT,
       PRIMARY KEY (Match_ID, Team_ID),
       FOREIGN KEY (Match_ID) REFERENCES Matches(Match_ID),
       FOREIGN KEY (Team_ID)  REFERENCES Team(Team_ID)
   );
   ```

   Typical query the design supports
   ```sql
   -- leading run scorer of the tournament
   SELECT   p.Name, SUM(pf.Runs_Scored) AS total_runs
   FROM     Player p JOIN Performance pf ON p.Player_ID = pf.Player_ID
   GROUP BY p.Player_ID, p.Name
   ORDER BY total_runs DESC
   LIMIT    1;
   ```

7. **How can you define the ER model in DBMS?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*

   Answer:

   What the ER model is
   - The `Entity-Relationship model`, introduced by Peter Chen in 1976, is a `conceptual` data model that describes the data of a system as `entities`, their `attributes`, and the `relationships` between them.
   - It is drawn as a diagram, independent of any particular DBMS, and is the standard first step in database design: the ER diagram is produced, agreed with the stakeholders, and only then converted into tables.

   The components

   `Entity`
   - A real-world object or concept about which data is stored — Student, Employee, Course.
   - An `entity set` is the collection of all such entities. Drawn as a `rectangle`.
   - A `strong entity` has its own primary key; a `weak entity` does not and depends on an owner — drawn as a `double rectangle`.

   `Attribute`
   - A property of an entity. Drawn as an `oval` connected to its entity.
   - Types:
     - `Key` attribute — underlined; uniquely identifies the entity (Student_ID).
     - `Composite` — divisible into parts (Name → First, Last; Address → City, Road).
     - `Multivalued` — may hold several values, drawn as a double oval (Phone_Numbers).
     - `Derived` — computed from others, drawn as a dashed oval (Age from Date_of_Birth).
     - `Simple` — atomic and indivisible.

   `Relationship`
   - An association between entities, drawn as a `diamond`.
   - A relationship may have its own `descriptive attributes` — for example `grade` on the Enrolls relationship between Student and Course.
   - `Degree`: unary (an employee manages an employee), binary (the usual case), ternary (three entities).

   `Cardinality`
   - `1 : 1` — one person has one passport.
   - `1 : N` — one department has many employees.
   - `M : N` — many students take many courses.

   `Participation`
   - `Total` (double line) — every entity must participate; an employee must belong to a department.
   - `Partial` (single line) — participation is optional; a department may exist with no employees.

   Example
   ```mermaid
   erDiagram
       DEPARTMENT ||--o{ EMPLOYEE : employs
       STUDENT    }o--o{ COURSE   : enrolls

       DEPARTMENT {
           int Dept_ID PK
           string Dept_Name
       }
       EMPLOYEE {
           int Emp_ID PK
           string Name
           date DOB
           int Dept_ID FK
       }
       STUDENT {
           int Student_ID PK
           string Name
       }
       COURSE {
           string Course_ID PK
           string Title
       }
   ```

   Chen notation for the same
   ```
      +------------+        /---------\        +-----------+
      | DEPARTMENT |=======<  Employs   >------| EMPLOYEE  |
      +------------+   1    \---------/    N   +-----------+
           |                                        |
      (Dept_ID) PK                             (Emp_ID) PK
      (Dept_Name)                              (Name)
   ```

   Converting an ER diagram to tables
   - Each `strong entity` becomes a table, with the key attribute as the primary key.
   - Each `weak entity` becomes a table whose primary key is the owner's key plus its own partial key.
   - A `1 : N` relationship puts the primary key of the `1` side as a foreign key on the `N` side.
   - A `1 : 1` relationship puts the foreign key on either side, preferably the one with total participation.
   - An `M : N` relationship becomes a `separate table` holding both foreign keys as a composite primary key, plus any descriptive attributes.
   - A `multivalued attribute` becomes its own table.

   Extended ER (EER) concepts
   - `Generalisation` — combining similar entities into a superclass (Car and Truck → Vehicle).
   - `Specialisation` — the reverse, splitting a superclass into subclasses.
   - `Aggregation` — treating a whole relationship as an entity so that another relationship can attach to it.

8. **Draw an entity diagram Student database management systemfrom following statement: Student (data); Course (data); Report (data); Registration; Staff (data)** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 759 (ET: N/A)]*

   Answer: The system covers Students registering for Courses, Staff teaching them, and Reports (results) produced from that registration.

   ER diagram
   ```mermaid
   erDiagram
       STUDENT ||--o{ REGISTRATION : makes
       COURSE  ||--o{ REGISTRATION : "is registered in"
       STAFF   ||--o{ COURSE       : teaches
       REGISTRATION ||--|| REPORT  : produces
       DEPARTMENT   ||--o{ STUDENT : enrolls
       DEPARTMENT   ||--o{ STAFF   : employs

       STUDENT {
           int Student_ID PK
           string Name
           date DOB
           string Address
           string Phone
           int Dept_ID FK
       }
       COURSE {
           string Course_ID PK
           string Course_Name
           int Credit_Hours
           string Semester
           int Staff_ID FK
       }
       REGISTRATION {
           int Reg_ID PK
           int Student_ID FK
           string Course_ID FK
           date Reg_Date
           string Session
       }
       REPORT {
           int Report_ID PK
           int Reg_ID FK
           decimal Marks
           char Grade
           decimal GPA
           date Publish_Date
       }
       STAFF {
           int Staff_ID PK
           string Name
           string Designation
           string Specialization
           int Dept_ID FK
       }
       DEPARTMENT {
           int Dept_ID PK
           string Dept_Name
       }
   ```

   Chen notation for the central part
   ```
      +----------+        /---------------\        +----------+
      | STUDENT  |-------<  REGISTRATION   >-------|  COURSE  |
      +----------+   M    \---------------/    N   +----------+
                                 |                       |
                           (Reg_Date)                    |
                                 |                 /----------\
                           +-----------+          <   Teaches  >
                           |  REPORT   |           \----------/
                           +-----------+                 |
                           (Marks)                  +---------+
                           (Grade)                  |  STAFF  |
                                                    +---------+
   ```

   Relationships and cardinality

   | Relationship | Cardinality | Explanation |
   |---|---|---|
   | Student registers for Course | `M : N` | A student takes many courses; a course has many students. Resolved by REGISTRATION |
   | Registration produces Report | `1 : 1` | Each registration yields one result record |
   | Staff teaches Course | `1 : N` | One teacher takes several courses; each course has one primary teacher |
   | Department enrolls Student | `1 : N` | |
   | Department employs Staff | `1 : N` | |

   Design points
   - `REGISTRATION` is the associative entity resolving the M:N between Student and Course. Its descriptive attributes — registration date, session — belong to the pairing, not to either entity.
   - `REPORT` depends on a registration, not directly on a student or a course. Attaching marks to a student alone would lose which subject they belong to; attaching them to a course alone would lose which student. This is the design point the question is really testing.
   - If a course can be taught by `several` staff members, `Teaches` becomes M:N and needs its own table.

   Tables
   ```sql
   CREATE TABLE Student (
       Student_ID INT PRIMARY KEY,
       Name       VARCHAR(100) NOT NULL,
       DOB        DATE,
       Dept_ID    INT REFERENCES Department(Dept_ID)
   );

   CREATE TABLE Course (
       Course_ID    VARCHAR(10) PRIMARY KEY,
       Course_Name  VARCHAR(100) NOT NULL,
       Credit_Hours INT,
       Staff_ID     INT REFERENCES Staff(Staff_ID)
   );

   CREATE TABLE Registration (
       Reg_ID     INT PRIMARY KEY,
       Student_ID INT NOT NULL,
       Course_ID  VARCHAR(10) NOT NULL,
       Reg_Date   DATE,
       Session    VARCHAR(10),
       UNIQUE (Student_ID, Course_ID, Session),
       FOREIGN KEY (Student_ID) REFERENCES Student(Student_ID),
       FOREIGN KEY (Course_ID)  REFERENCES Course(Course_ID)
   );

   CREATE TABLE Report (
       Report_ID INT PRIMARY KEY,
       Reg_ID    INT NOT NULL UNIQUE,          -- UNIQUE enforces the 1:1
       Marks     DECIMAL(5,2),
       Grade     CHAR(2),
       FOREIGN KEY (Reg_ID) REFERENCES Registration(Reg_ID)
   );
   ```
   - Note the `UNIQUE` on `Reg_ID` in Report: that is how a `1:1` relationship is enforced in SQL, since a plain foreign key would allow many reports per registration.

9. **(ক) Entity-Relationship (ER) Diagram কেন ব্যবহার করা হয়? একটি উদাহরণের মাধ্যমে ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 768 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   Why an ER diagram is used

   1. `Conceptual design before implementation`
   - It models the data at a level everyone can discuss, independent of any DBMS. Design errors caught in a diagram cost nothing; the same errors found after the database is built and populated are expensive to fix.

   2. `Communication between technical and non-technical people`
   - A librarian, a bank manager or a hospital administrator can look at an ER diagram and say "no, a patient can see several doctors" — which they could never do from a set of CREATE TABLE statements.

   3. `Blueprint for the tables`
   - The conversion is mechanical once the diagram is right: entities become tables, attributes become columns, and relationships become foreign keys or junction tables.

   4. `Reveals cardinality and participation`
   - Whether a relationship is 1:1, 1:N or M:N decides where each foreign key goes and whether an extra table is needed. This is the single most important thing the diagram settles.

   5. `Supports normalisation`
   - A clear model exposes redundancy and update anomalies before any data exists.

   6. `Documentation`
   - It remains the reference for everyone who later maintains or extends the system.

   7. `Completeness check`
   - Missing entities and forgotten relationships are visible in a picture in a way that they are not in a list of tables.

   Worked example — a university

   ```mermaid
   erDiagram
       DEPARTMENT ||--o{ STUDENT      : enrolls
       DEPARTMENT ||--o{ TEACHER      : employs
       STUDENT    ||--o{ ENROLLMENT   : registers
       COURSE     ||--o{ ENROLLMENT   : "has"
       TEACHER    ||--o{ COURSE       : teaches

       DEPARTMENT {
           int Dept_ID PK
           string Dept_Name
       }
       STUDENT {
           int Student_ID PK
           string Name
           date DOB
           int Dept_ID FK
       }
       COURSE {
           string Course_ID PK
           string Title
           int Credits
           int Teacher_ID FK
       }
       ENROLLMENT {
           int Student_ID PK-FK
           string Course_ID PK-FK
           char Grade
           string Semester
       }
       TEACHER {
           int Teacher_ID PK
           string Name
           int Dept_ID FK
       }
   ```

   Chen notation for the central relationship
   ```
      +----------+          /-------------\          +----------+
      | STUDENT  |---------<   ENROLLS     >---------|  COURSE  |
      +----------+   M      \-------------/     N    +----------+
           |                       |                       |
     (Student_ID) PK           (Grade)                (Course_ID) PK
     (Name)                    (Semester)             (Title)
     (DOB)                                            (Credits)
   ```

   What this diagram immediately tells the designer
   - Student and Course are `M:N`, so a third table `Enrollment` is unavoidable. Without the diagram this is easy to miss, and a designer might wrongly put `Course_ID` in the Student table, which would allow only one course per student.
   - `Grade` is a `descriptive attribute` of the relationship — it belongs neither to the student nor to the course, but to the pairing.
   - `Department to Student` is `1:N`, so `Dept_ID` becomes a foreign key in Student. No extra table is needed.

   The resulting tables
   ```sql
   CREATE TABLE Student (
       Student_ID INT PRIMARY KEY,
       Name       VARCHAR(100) NOT NULL,
       Dept_ID    INT REFERENCES Department(Dept_ID)
   );

   CREATE TABLE Enrollment (
       Student_ID INT,
       Course_ID  VARCHAR(10),
       Grade      CHAR(2),
       Semester   VARCHAR(10),
       PRIMARY KEY (Student_ID, Course_ID),
       FOREIGN KEY (Student_ID) REFERENCES Student(Student_ID),
       FOREIGN KEY (Course_ID)  REFERENCES Course(Course_ID)
   );
   ```
   - The diagram to the schema is a direct translation, which is exactly why the diagram is drawn first.

10. **(a) While converting E-R diagram into Tables, how is a Many-to-many relationship set between entities A and B is converted into database tables?** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 804 (ET: N/A)]*

    Answer: An `M:N` relationship cannot be represented by a foreign key in either table. It requires a `third table`.

    Why a foreign key will not work
    - Suppose A is Student and B is Course, and the relationship is "enrolls".
    - Putting `Course_ID` in Student would allow each student `one` course only.
    - Putting `Student_ID` in Course would allow each course `one` student only.
    - Neither captures many-to-many, so a separate relation is unavoidable.

    The rule
    > For an `M:N` relationship between A and B, create a `new table` whose attributes are the primary key of A plus the primary key of B, both as foreign keys, with their combination as the composite primary key. Any descriptive attributes of the relationship go into this table as well.

    Structure
    ```
    Entity A                Relationship table            Entity B
    +--------+           +--------------------+        +--------+
    | A_ID PK|<----------| A_ID  PK, FK       |        | B_ID PK|
    | attr1  |           | B_ID  PK, FK       |------->| attr1  |
    +--------+           | descriptive attrs  |        +--------+
                         +--------------------+
    ```

    Worked example
    ```mermaid
    erDiagram
        STUDENT ||--o{ ENROLLMENT : has
        COURSE  ||--o{ ENROLLMENT : has
        STUDENT {
            int Student_ID PK
            string Name
        }
        COURSE {
            string Course_ID PK
            string Title
        }
        ENROLLMENT {
            int Student_ID PK-FK
            string Course_ID PK-FK
            char Grade
            date Enrol_Date
        }
    ```

    ```sql
    CREATE TABLE Student (
        Student_ID INT PRIMARY KEY,
        Name       VARCHAR(100) NOT NULL
    );

    CREATE TABLE Course (
        Course_ID VARCHAR(10) PRIMARY KEY,
        Title     VARCHAR(100) NOT NULL
    );

    CREATE TABLE Enrollment (              -- the relationship table
        Student_ID INT,
        Course_ID  VARCHAR(10),
        Grade      CHAR(2),                -- descriptive attribute
        Enrol_Date DATE,                   -- descriptive attribute
        PRIMARY KEY (Student_ID, Course_ID),
        FOREIGN KEY (Student_ID) REFERENCES Student(Student_ID),
        FOREIGN KEY (Course_ID)  REFERENCES Course(Course_ID)
    );
    ```

    The data
    ```
    Student              Course                Enrollment
    +-----+-------+      +-------+-------+     +-----+-------+-------+
    | ID  | Name  |      | ID    | Title |     | SID | CID   | Grade |
    +-----+-------+      +-------+-------+     +-----+-------+-------+
    | 101 | Karim |      | CS101 | DB    |     | 101 | CS101 |   A   |
    | 102 | Rahim |      | CS102 | Net   |     | 101 | CS102 |   B   |  one student, two courses
    +-----+-------+      +-------+-------+     | 102 | CS101 |   A   |  one course, two students
                                               +-----+-------+-------+
    ```

    Three points that earn marks
    - The `composite primary key (A_ID, B_ID)` is what prevents the same pairing from being recorded twice.
    - `Descriptive attributes` of the relationship belong in this table and nowhere else — Grade belongs neither to the student nor to the course.
    - The M:N relationship is thereby `decomposed into two 1:N relationships`, which is what the relational model can actually express.

    Comparison with the other cardinalities

    | Relationship | How it is converted |
    |---|---|
    | `1 : 1` | Foreign key in either table, preferably the one with total participation; declare it UNIQUE |
    | `1 : N` | Foreign key on the `N` side, referring to the `1` side. No extra table |
    | `M : N` | `A separate table` with both keys as a composite primary key |

    - A variant sometimes preferred in practice adds a `surrogate key` — `Enrollment_ID INT PRIMARY KEY` — and keeps `UNIQUE(Student_ID, Course_ID)` to preserve the rule, which simplifies any table that needs to refer to a particular enrolment.

11. **Draw ER diagram for Titas Gas Transmission and Distribution Company limited. Relation between customer and meter. (full question টা পাওয়া যায়নি।)** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 824 (ET: BUET)]*

    Answer: The core of a gas distribution company's data model is the relationship between a `Customer` and the `Meter` installed at their premises, with `Bills` generated from meter readings.

    ER diagram
    ```mermaid
    erDiagram
        CUSTOMER ||--|| METER    : "is installed with"
        METER    ||--o{ READING  : records
        CUSTOMER ||--o{ BILL     : receives
        BILL     ||--o{ PAYMENT  : "is settled by"
        ZONE     ||--o{ CUSTOMER : serves
        METER    }o--|| METER_TYPE : "is of"

        CUSTOMER {
            int Customer_ID PK
            string Name
            string Address
            string Phone
            string Customer_Type
            date Connection_Date
            int Zone_ID FK
        }
        METER {
            int Meter_No PK
            int Customer_ID FK
            string Model
            string Producer_Name
            date Install_Date
            string Status
        }
        READING {
            int Reading_ID PK
            int Meter_No FK
            date Reading_Date
            decimal Previous_Reading
            decimal Current_Reading
            decimal Consumption
        }
        BILL {
            int Bill_ID PK
            int Customer_ID FK
            int Reading_ID FK
            string Billing_Month
            decimal Amount
            date Due_Date
            string Status
        }
        PAYMENT {
            int Payment_ID PK
            int Bill_ID FK
            decimal Amount_Paid
            date Payment_Date
            string Method
        }
        ZONE {
            int Zone_ID PK
            string Zone_Name
            string Region
        }
    ```

    Chen notation for the relationship the question asks about
    ```
       +------------+                                +----------+
       |  CUSTOMER  |================================|  METER   |
       +------------+   1     /-------------\   1    +----------+
            |               =<   Installed   >=           |
       (Customer_ID) PK      \-------------/         (Meter_No) PK
       (Name)                                        (Model)
       (Address)             double lines =          (Producer_Name)
       (Customer_Type)       TOTAL participation     (Install_Date)
                             on both sides
    ```

    Customer to Meter — the cardinality
    - `1 : 1`. Every customer has exactly one meter, and every meter serves exactly one customer.
    - `Participation is total on both sides`: a customer without a meter has no gas supply, and a meter not assigned to a customer is not in service.
    - Because participation is total on both sides, the two could in principle be merged into one table — but they are kept separate because a meter has its own life cycle: it is manufactured, installed, replaced and scrapped, and a customer may receive a replacement meter.

    Converting the 1:1 relationship to tables
    - Place the foreign key on `either` side and declare it `UNIQUE`, which is what enforces the 1:1.
    ```sql
    CREATE TABLE Customer (
        Customer_ID     INT PRIMARY KEY,
        Name            VARCHAR(100) NOT NULL,
        Address         VARCHAR(200),
        Customer_Type   VARCHAR(20),
        Connection_Date DATE
    );

    CREATE TABLE Meter (
        Meter_No      INT PRIMARY KEY,
        Customer_ID   INT NOT NULL UNIQUE,       -- UNIQUE enforces 1:1
        Model         VARCHAR(50),
        Producer_Name VARCHAR(100),
        Install_Date  DATE,
        FOREIGN KEY (Customer_ID) REFERENCES Customer(Customer_ID)
    );
    ```
    - Without `UNIQUE`, the constraint would be 1:N and one customer could hold several meters.

    Other relationships
    - `Meter records Reading` — 1:N. Each monthly reading belongs to one meter.
    - `Customer receives Bill` — 1:N. One bill per month.
    - `Bill is settled by Payment` — 1:N, since a bill may be paid in instalments.
    - `Zone serves Customer` — 1:N, for meter-reading routes and regional reporting.

    A typical query the design supports
    ```sql
    -- current month's unpaid bills in one zone
    SELECT c.Name, c.Address, b.Amount, b.Due_Date
    FROM   Customer c JOIN Bill b ON c.Customer_ID = b.Customer_ID
    WHERE  b.Status = 'Unpaid' AND c.Zone_ID = 3;
    ```

12. **Draw ER diagram from a story.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 837 (ET: N/A)]*

    Answer: The specific story was not printed, so the `method` for converting a narrative into an ER diagram is given, with a worked example.

    The method — how to read a story

    | In the story | In the ER diagram |
    |---|---|
    | A `noun` that the system stores data about | An `entity` |
    | A noun describing a property of another noun | An `attribute` |
    | A `verb` connecting two nouns | A `relationship` |
    | "each", "only one", "exactly one" | Cardinality `1` |
    | "many", "several", "one or more" | Cardinality `N` |
    | "must", "always" | `Total` participation (double line) |
    | "may", "optionally", "sometimes" | `Partial` participation (single line) |
    | A noun that cannot exist alone | A `weak entity` |
    | A property of the connection itself | A `descriptive attribute` on the relationship |
    | "is a kind of" | Generalisation / specialisation |

    Worked example — a typical bank story
    > "A bank has several branches, each identified by a branch code and having a name and an address. A customer, identified by a customer ID, may open one or more accounts. Each account belongs to exactly one branch. A customer may also take loans. Every account has an account number, a type and a balance. Each transaction on an account records a date, a type and an amount."

    Step 1 — extract the entities (the nouns the system stores data about)
    ```
    BRANCH, CUSTOMER, ACCOUNT, LOAN, TRANSACTION
    ```

    Step 2 — extract the attributes and mark the keys
    ```
    BRANCH      : Branch_Code (PK), Name, Address
    CUSTOMER    : Customer_ID (PK), Name, Address, Phone
    ACCOUNT     : Account_No (PK), Type, Balance, Open_Date
    LOAN        : Loan_ID (PK), Amount, Interest_Rate, Term
    TRANSACTION : Txn_ID (PK), Date, Type, Amount
    ```

    Step 3 — extract the relationships and their cardinality from the verbs
    ```
    BRANCH  has        ACCOUNT      1 : N    ("each account belongs to exactly one branch")
    CUSTOMER opens     ACCOUNT      M : N    ("one or more"; joint accounts make it M:N)
    CUSTOMER takes     LOAN         1 : N
    ACCOUNT  records   TRANSACTION  1 : N    (TRANSACTION is weak — it cannot exist alone)
    ```

    Step 4 — draw it
    ```mermaid
    erDiagram
        BRANCH   ||--o{ ACCOUNT     : maintains
        CUSTOMER ||--o{ ACC_HOLDER  : holds
        ACCOUNT  ||--o{ ACC_HOLDER  : "is held by"
        CUSTOMER ||--o{ LOAN        : takes
        ACCOUNT  ||--o{ TRANSACTION : records

        BRANCH {
            string Branch_Code PK
            string Name
            string Address
        }
        CUSTOMER {
            int Customer_ID PK
            string Name
            string Address
            string Phone
        }
        ACCOUNT {
            string Account_No PK
            string Type
            decimal Balance
            string Branch_Code FK
        }
        ACC_HOLDER {
            int Customer_ID PK-FK
            string Account_No PK-FK
            date Since
        }
        LOAN {
            int Loan_ID PK
            int Customer_ID FK
            decimal Amount
            decimal Interest_Rate
        }
        TRANSACTION {
            int Txn_ID PK
            string Account_No FK
            datetime Txn_Date
            string Txn_Type
            decimal Amount
        }
    ```

    Step 5 — convert to tables
    - `1:N` → foreign key on the N side. `M:N` → a separate table. Weak entity → owner's key plus its own partial key.
    ```sql
    CREATE TABLE Account (
        Account_No  VARCHAR(20) PRIMARY KEY,
        Type        VARCHAR(20),
        Balance     DECIMAL(15,2) DEFAULT 0,
        Branch_Code VARCHAR(10) NOT NULL REFERENCES Branch(Branch_Code)
    );

    CREATE TABLE Acc_Holder (
        Customer_ID INT,
        Account_No  VARCHAR(20),
        Since       DATE,
        PRIMARY KEY (Customer_ID, Account_No),
        FOREIGN KEY (Customer_ID) REFERENCES Customer(Customer_ID),
        FOREIGN KEY (Account_No)  REFERENCES Account(Account_No)
    );
    ```

    The two mistakes to avoid
    - Treating an attribute as an entity, or vice versa. A rule of thumb: if the noun has properties of its own and can be listed, it is an entity; if it is just a value, it is an attribute.
    - Missing an `M:N` relationship and trying to represent it with a foreign key. Any relationship where both sides can be "many" needs its own table. <!-- verify -->

13. **Draw E-R diagram of hospital management system. Hospital name “SKY Hospital Ltd.”.** *[RAKUB Programmer (PO) 12.10.2021 compact it 853 (ET: N/A)]*

    Answer: A hospital system centres on Patients, Doctors, Appointments and Treatments, with departments, wards and billing around them.

    ER diagram
    ```mermaid
    erDiagram
        DEPARTMENT  ||--o{ DOCTOR       : employs
        DOCTOR      ||--o{ APPOINTMENT  : attends
        PATIENT     ||--o{ APPOINTMENT  : books
        APPOINTMENT ||--o{ PRESCRIPTION : produces
        PRESCRIPTION||--o{ MEDICINE_ITEM: contains
        MEDICINE    ||--o{ MEDICINE_ITEM: "is prescribed as"
        PATIENT     ||--o{ ADMISSION    : "is admitted by"
        WARD        ||--o{ ADMISSION    : accommodates
        PATIENT     ||--o{ BILL         : receives
        NURSE       }o--|| WARD         : "works in"
        PATIENT     ||--o{ TEST_REPORT  : undergoes

        PATIENT {
            int Patient_ID PK
            string Name
            int Age
            string Gender
            string Blood_Group
            string Phone
            string Address
        }
        DOCTOR {
            int Doctor_ID PK
            string Name
            string Specialization
            string Phone
            decimal Consultation_Fee
            int Dept_ID FK
        }
        DEPARTMENT {
            int Dept_ID PK
            string Dept_Name
            string Location
        }
        APPOINTMENT {
            int Appt_ID PK
            int Patient_ID FK
            int Doctor_ID FK
            datetime Appt_DateTime
            string Status
        }
        PRESCRIPTION {
            int Presc_ID PK
            int Appt_ID FK
            string Diagnosis
            string Advice
            date Presc_Date
        }
        MEDICINE {
            int Medicine_ID PK
            string Name
            string Type
            decimal Price
        }
        MEDICINE_ITEM {
            int Presc_ID PK-FK
            int Medicine_ID PK-FK
            string Dosage
            int Duration_Days
        }
        WARD {
            int Ward_ID PK
            string Ward_Name
            string Ward_Type
            int Total_Beds
        }
        ADMISSION {
            int Admission_ID PK
            int Patient_ID FK
            int Ward_ID FK
            int Bed_No
            date Admit_Date
            date Discharge_Date
        }
        NURSE {
            int Nurse_ID PK
            string Name
            string Shift
            int Ward_ID FK
        }
        TEST_REPORT {
            int Report_ID PK
            int Patient_ID FK
            string Test_Name
            date Test_Date
            string Result
        }
        BILL {
            int Bill_ID PK
            int Patient_ID FK
            decimal Total_Amount
            date Bill_Date
            string Payment_Status
        }
    ```

    Relationships and cardinality

    | Relationship | Cardinality | Note |
    |---|---|---|
    | Department employs Doctor | `1 : N` | A doctor belongs to one department |
    | Patient books Appointment | `1 : N` | |
    | Doctor attends Appointment | `1 : N` | |
    | Patient consults Doctor | `M : N` | Resolved by APPOINTMENT |
    | Appointment produces Prescription | `1 : N` | |
    | Prescription contains Medicine | `M : N` | Resolved by MEDICINE_ITEM, with dosage as a descriptive attribute |
    | Ward accommodates Admission | `1 : N` | |
    | Nurse works in Ward | `N : 1` | |
    | Patient receives Bill | `1 : N` | |

    Design points worth stating
    - `APPOINTMENT` is the associative entity that resolves the M:N between Patient and Doctor, with `date and time` as its descriptive attributes.
    - `MEDICINE_ITEM` does the same for Prescription and Medicine, holding `dosage` and `duration` — which belong to the pairing of a particular medicine with a particular prescription, not to either alone.
    - `ADMISSION` records the stay rather than putting `Ward_ID` on Patient, because a patient may be admitted several times and to different wards.
    - A `Bed` could be modelled as a `weak entity` of Ward, identified by Ward_ID plus bed number.

    Core tables
    ```sql
    CREATE TABLE Patient (
        Patient_ID INT PRIMARY KEY,
        Name       VARCHAR(100) NOT NULL,
        Age        INT,
        Gender     CHAR(1),
        Phone      VARCHAR(15)
    );

    CREATE TABLE Appointment (
        Appt_ID       INT PRIMARY KEY,
        Patient_ID    INT NOT NULL,
        Doctor_ID     INT NOT NULL,
        Appt_DateTime DATETIME NOT NULL,
        Status        VARCHAR(20) DEFAULT 'Scheduled',
        UNIQUE (Doctor_ID, Appt_DateTime),        -- no double-booking a doctor
        FOREIGN KEY (Patient_ID) REFERENCES Patient(Patient_ID),
        FOREIGN KEY (Doctor_ID)  REFERENCES Doctor(Doctor_ID)
    );
    ```
    - The `UNIQUE (Doctor_ID, Appt_DateTime)` constraint is worth highlighting: it enforces a real business rule — one doctor cannot have two appointments at the same instant — directly in the database rather than in application code.

14. **Draw E-R diagram of Banking Management system. Bank name “SKY Bank Ltd.”.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)]*

    Answer: A banking system centres on Customers holding Accounts at Branches, with Transactions, Loans and Employees around them.

    ER diagram
    ```mermaid
    erDiagram
        BRANCH      ||--o{ ACCOUNT     : maintains
        BRANCH      ||--o{ EMPLOYEE    : employs
        BRANCH      ||--o{ LOAN        : sanctions
        CUSTOMER    ||--o{ ACC_HOLDER  : holds
        ACCOUNT     ||--o{ ACC_HOLDER  : "is held by"
        ACCOUNT     ||--o{ TRANSACTION : records
        CUSTOMER    ||--o{ LOAN        : takes
        LOAN        ||--o{ INSTALLMENT : "is repaid by"
        EMPLOYEE    ||--o{ CUSTOMER    : manages

        BRANCH {
            string Branch_Code PK
            string Branch_Name
            string Address
            string City
            decimal Assets
        }
        CUSTOMER {
            int Customer_ID PK
            string Name
            string Address
            string Phone
            string NID
            date DOB
        }
        ACCOUNT {
            string Account_No PK
            string Account_Type
            decimal Balance
            date Open_Date
            string Status
            string Branch_Code FK
        }
        ACC_HOLDER {
            int Customer_ID PK-FK
            string Account_No PK-FK
            date Since
        }
        TRANSACTION {
            int Txn_ID PK
            string Account_No FK
            datetime Txn_DateTime
            string Txn_Type
            decimal Amount
            decimal Balance_After
        }
        LOAN {
            int Loan_ID PK
            int Customer_ID FK
            string Branch_Code FK
            decimal Amount
            decimal Interest_Rate
            int Term_Months
            date Sanction_Date
        }
        INSTALLMENT {
            int Inst_ID PK
            int Loan_ID FK
            date Due_Date
            decimal Amount
            date Paid_Date
            string Status
        }
        EMPLOYEE {
            int Emp_ID PK
            string Name
            string Designation
            decimal Salary
            string Branch_Code FK
        }
    ```

    Chen notation for the central relationships
    ```
       +----------+       /----------\       +----------+       /-----------\      +-------------+
       | CUSTOMER |------<  HOLDS     >------| ACCOUNT  |======<  RECORDS    >=====| TRANSACTION |
       +----------+  M   \----------/   N    +----------+  1   \-----------/   N   +=============+
            |                                      |                                (weak entity)
            |            /----------\              |
            +-----------<   TAKES    >             | maintained by
                 1       \----------/              |
                              | N            +----------+
                         +--------+          |  BRANCH  |
                         |  LOAN  |          +----------+
                         +--------+
    ```

    Relationships and cardinality

    | Relationship | Cardinality | Explanation |
    |---|---|---|
    | Branch maintains Account | `1 : N` | Each account belongs to one branch |
    | Customer holds Account | `M : N` | A customer may have several accounts; a joint account has several customers. Resolved by ACC_HOLDER |
    | Account records Transaction | `1 : N` | TRANSACTION is a weak entity — it cannot exist without its account |
    | Customer takes Loan | `1 : N` | |
    | Loan is repaid by Installment | `1 : N` | |
    | Branch employs Employee | `1 : N` | |

    Design points worth explaining
    - `ACC_HOLDER` is essential rather than optional: without it, a `joint account` could not be represented, and neither could a customer with both a savings and a current account. Putting `Customer_ID` directly in Account would force 1:N and lose joint accounts.
    - `TRANSACTION` is a `weak entity`: a transaction has no meaning apart from the account it belongs to, and its participation is total.
    - `Balance` in Account is a `derived` attribute — it can be computed by summing transactions. It is stored anyway, because recomputing it on every enquiry would be far too slow. This is a deliberate, justified denormalisation.
    - A `self-referencing` relationship could be added: `Employee manages Employee`.

    Core tables
    ```sql
    CREATE TABLE Account (
        Account_No   VARCHAR(20) PRIMARY KEY,
        Account_Type VARCHAR(20) CHECK (Account_Type IN ('Savings','Current','Fixed')),
        Balance      DECIMAL(15,2) NOT NULL DEFAULT 0 CHECK (Balance >= 0),
        Branch_Code  VARCHAR(10) NOT NULL REFERENCES Branch(Branch_Code)
    );

    CREATE TABLE Acc_Holder (
        Customer_ID INT,
        Account_No  VARCHAR(20),
        Since       DATE,
        PRIMARY KEY (Customer_ID, Account_No),
        FOREIGN KEY (Customer_ID) REFERENCES Customer(Customer_ID),
        FOREIGN KEY (Account_No)  REFERENCES Account(Account_No)
    );

    CREATE TABLE Transaction (
        Txn_ID        INT PRIMARY KEY,
        Account_No    VARCHAR(20) NOT NULL,
        Txn_DateTime  DATETIME NOT NULL,
        Txn_Type      VARCHAR(10) CHECK (Txn_Type IN ('Deposit','Withdrawal','Transfer')),
        Amount        DECIMAL(15,2) NOT NULL CHECK (Amount > 0),
        FOREIGN KEY (Account_No) REFERENCES Account(Account_No)
    );
    ```
    - `CHECK (Balance >= 0)` and `CHECK (Amount > 0)` push real banking rules into the database, where no application bug can bypass them.

15. **Draw ER diagram for details of gas company data described. Bakharbad gas distribution Compeny has two types of customers i.e General and Industrial. General customer has customer ID, name, DOB, age (calculated from DOB). Industrial customer has all attributes of general customer with TAX number additionally. Meter has model and producer name. Every customer has one meter.** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 877 (ET: BUET)]*

    Answer: The distinguishing feature of this problem is that an `Industrial customer has every attribute of a General customer plus a TAX number` — which is the textbook signal for `generalisation and specialisation`.

    ER diagram
    ```mermaid
    erDiagram
        CUSTOMER ||--|| METER : "is installed with"
        CUSTOMER ||--o| GENERAL_CUSTOMER    : "is a"
        CUSTOMER ||--o| INDUSTRIAL_CUSTOMER : "is a"

        CUSTOMER {
            int Customer_ID PK
            string Name
            date DOB
            string Address
            string Customer_Type
        }
        GENERAL_CUSTOMER {
            int Customer_ID PK-FK
        }
        INDUSTRIAL_CUSTOMER {
            int Customer_ID PK-FK
            string TAX_Number
        }
        METER {
            int Meter_No PK
            int Customer_ID FK
            string Model
            string Producer_Name
            date Install_Date
        }
    ```

    Chen notation with the specialisation triangle
    ```
                        +--------------+
                        |   CUSTOMER   |
                        +--------------+
                        (Customer_ID) PK
                        (Name)
                        (DOB)
                        (Age)  <- dashed oval: DERIVED from DOB
                               |
                               |
                             /   \
                            /  d  \      <- specialisation triangle
                           /_______\        (d = disjoint)
                            |     |
                  +---------+     +----------+
                  |                          |
        +-------------------+     +----------------------+
        | GENERAL_CUSTOMER  |     | INDUSTRIAL_CUSTOMER  |
        +-------------------+     +----------------------+
                                    (TAX_Number)  <- extra attribute


        +--------------+                          +-----------+
        |   CUSTOMER   |==========================|   METER   |
        +--------------+   1   /---------\   1    +-----------+
                              =<  HAS     >=       (Meter_No) PK
                               \---------/         (Model)
                            total participation    (Producer_Name)
                            on both sides
    ```

    The three modelling decisions the question is testing

    1. `Generalisation / specialisation`
    - `CUSTOMER` is the superclass holding the common attributes (Customer_ID, Name, DOB, Address).
    - `GENERAL_CUSTOMER` and `INDUSTRIAL_CUSTOMER` are subclasses. Only the industrial subclass adds `TAX_Number`.
    - The specialisation is `disjoint` (a customer is one type or the other, never both) and `total` (every customer is one of the two).

    2. `Derived attribute`
    - `Age` is computed from `DOB` and is `not stored`. In a diagram it is drawn as a `dashed oval`; in SQL it is a computed column or a view:
    ```sql
    SELECT Customer_ID, Name, TIMESTAMPDIFF(YEAR, DOB, CURDATE()) AS Age FROM Customer;
    ```
    - Storing age would be a design error, because it becomes wrong the day after it is written.

    3. `1 : 1 relationship with total participation`
    - "Every customer has one meter" gives `1:1`, with double lines on both sides.

    Converting to tables — three possible strategies for the specialisation

    `Strategy A — one table per subclass plus the superclass` (the normalised choice, shown above)
    ```sql
    CREATE TABLE Customer (
        Customer_ID   INT PRIMARY KEY,
        Name          VARCHAR(100) NOT NULL,
        DOB           DATE,
        Customer_Type VARCHAR(20) CHECK (Customer_Type IN ('General','Industrial'))
    );

    CREATE TABLE Industrial_Customer (
        Customer_ID INT PRIMARY KEY,
        TAX_Number  VARCHAR(30) NOT NULL UNIQUE,
        FOREIGN KEY (Customer_ID) REFERENCES Customer(Customer_ID)
    );

    CREATE TABLE Meter (
        Meter_No      INT PRIMARY KEY,
        Customer_ID   INT NOT NULL UNIQUE,        -- UNIQUE enforces the 1:1
        Model         VARCHAR(50),
        Producer_Name VARCHAR(100),
        FOREIGN KEY (Customer_ID) REFERENCES Customer(Customer_ID)
    );
    ```
    - `General_Customer` needs no table of its own, since it adds no attributes.

    `Strategy B — a single table with a type discriminator`
    ```sql
    CREATE TABLE Customer (
        Customer_ID   INT PRIMARY KEY,
        Name          VARCHAR(100),
        DOB           DATE,
        Customer_Type VARCHAR(20),
        TAX_Number    VARCHAR(30) NULL          -- NULL for general customers
    );
    ```
    - Simpler and faster to query, but it permits a general customer to be given a TAX number, so the constraint has to be enforced by a CHECK:
    ```sql
    CHECK ((Customer_Type = 'Industrial' AND TAX_Number IS NOT NULL)
        OR (Customer_Type = 'General'    AND TAX_Number IS NULL))
    ```
    - `Strategy A` is preferred when the subclasses differ substantially; `Strategy B` when they differ by only one or two columns, as here.

16. **Draw the ER diagram where their relation named TEAM, PLAYER, MATCH** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 880 (ET: BUET)]*

    Answer: The relationships are a Team having Players, and a Match being played between two Teams — which is an `M:N` relationship that Players contribute performances to.

    ER diagram
    ```mermaid
    erDiagram
        TEAM   ||--o{ PLAYER      : "has"
        TEAM   ||--o{ MATCH_TEAM  : "plays in"
        MATCH  ||--|{ MATCH_TEAM  : involves
        PLAYER ||--o{ PERFORMANCE : achieves
        MATCH  ||--o{ PERFORMANCE : records

        TEAM {
            int Team_ID PK
            string Team_Name
            string City
            string Coach_Name
            date Founded
        }
        PLAYER {
            int Player_ID PK
            string Player_Name
            date DOB
            string Position
            int Jersey_No
            int Team_ID FK
        }
        MATCH {
            int Match_ID PK
            date Match_Date
            time Start_Time
            string Venue
            int Winner_Team_ID FK
            string Result
        }
        MATCH_TEAM {
            int Match_ID PK-FK
            int Team_ID PK-FK
            int Score
            string Home_Away
        }
        PERFORMANCE {
            int Match_ID PK-FK
            int Player_ID PK-FK
            int Goals
            int Assists
            int Minutes_Played
        }
    ```

    Chen notation
    ```
       +--------+       /--------\       +----------+
       |  TEAM  |------<   HAS    >------|  PLAYER  |
       +--------+  1    \--------/    N  +----------+
           |                                   |
           | M                                 | M
       /--------\                          /-------------\
      <  PLAYS   >                        <  PERFORMS_IN  >
       \--------/                          \-------------/
           | N                                 | N
       +---------+                             |
       |  MATCH  |-----------------------------+
       +---------+
       (Match_ID) PK
       (Match_Date)
       (Venue)
    ```

    Relationships and cardinality

    | Relationship | Cardinality | Explanation |
    |---|---|---|
    | Team has Player | `1 : N` | One team has many players; a player belongs to one team |
    | Team plays Match | `M : N` | One team plays many matches; each match involves exactly two teams |
    | Player performs in Match | `M : N` | One player features in many matches; each match involves many players |

    Design points worth stating
    - `MATCH_TEAM` is the associative entity resolving the M:N between Match and Team. It also holds the descriptive attributes `Score` and `Home_Away`, which belong to the pairing of one team with one match.
    - A constraint that a match must have `exactly two` teams cannot be expressed by cardinality alone; it needs a trigger or an application rule.
    - `PERFORMANCE` resolves the M:N between Player and Match, holding the individual statistics. This is the table every player statistic is computed from.
    - `Winner_Team_ID` is a `derived` attribute — computable from the scores — stored deliberately because it makes league-table queries far simpler.

    Tables
    ```sql
    CREATE TABLE Team (
        Team_ID   INT PRIMARY KEY,
        Team_Name VARCHAR(100) NOT NULL UNIQUE,
        City      VARCHAR(50)
    );

    CREATE TABLE Player (
        Player_ID   INT PRIMARY KEY,
        Player_Name VARCHAR(100) NOT NULL,
        Position    VARCHAR(30),
        Jersey_No   INT,
        Team_ID     INT REFERENCES Team(Team_ID),
        UNIQUE (Team_ID, Jersey_No)               -- no two players share a shirt number
    );

    CREATE TABLE Match_Team (
        Match_ID  INT,
        Team_ID   INT,
        Score     INT DEFAULT 0,
        Home_Away CHAR(1) CHECK (Home_Away IN ('H','A')),
        PRIMARY KEY (Match_ID, Team_ID),
        FOREIGN KEY (Match_ID) REFERENCES Matches(Match_ID),
        FOREIGN KEY (Team_ID)  REFERENCES Team(Team_ID)
    );
    ```

    Typical query the design supports
    ```sql
    -- league table
    SELECT   t.Team_Name,
             COUNT(*) AS played,
             SUM(CASE WHEN m.Winner_Team_ID = t.Team_ID THEN 3 ELSE 0 END) AS points
    FROM     Team t
    JOIN     Match_Team mt ON t.Team_ID = mt.Team_ID
    JOIN     Matches    m  ON mt.Match_ID = m.Match_ID
    GROUP BY t.Team_ID, t.Team_Name
    ORDER BY points DESC;
    ```

17. **Railway Service system ER diagram.** *[Sonali Bank Ltd. Officer IT 2021 compact it 910 (ET: N/A)]*

    Answer: A railway reservation system centres on Trains running on Routes, Passengers making Bookings on a particular journey date.

    ER diagram
    ```mermaid
    erDiagram
        TRAIN     ||--o{ SCHEDULE    : "runs on"
        STATION   ||--o{ SCHEDULE    : "is stop in"
        TRAIN     ||--o{ COACH       : "has"
        COACH     ||--o{ SEAT        : contains
        PASSENGER ||--o{ BOOKING     : makes
        TRAIN     ||--o{ BOOKING     : "is booked on"
        BOOKING   ||--|{ TICKET      : issues
        SEAT      ||--o{ TICKET      : "is allocated to"
        BOOKING   ||--|| PAYMENT     : "is paid by"

        TRAIN {
            int Train_No PK
            string Train_Name
            string Train_Type
            string Source_Station
            string Dest_Station
            string Running_Days
        }
        STATION {
            string Station_Code PK
            string Station_Name
            string City
            string Zone
        }
        SCHEDULE {
            int Schedule_ID PK
            int Train_No FK
            string Station_Code FK
            int Stop_No
            time Arrival_Time
            time Departure_Time
            int Distance_KM
        }
        COACH {
            int Coach_ID PK
            int Train_No FK
            string Coach_No
            string Class_Type
            int Total_Seats
        }
        SEAT {
            int Seat_ID PK
            int Coach_ID FK
            string Seat_No
            string Berth_Type
        }
        PASSENGER {
            int Passenger_ID PK
            string Name
            int Age
            string Gender
            string Phone
            string NID
        }
        BOOKING {
            int PNR PK
            int Passenger_ID FK
            int Train_No FK
            date Journey_Date
            string From_Station
            string To_Station
            decimal Total_Fare
            string Status
        }
        TICKET {
            int Ticket_ID PK
            int PNR FK
            int Seat_ID FK
            string Passenger_Name
            int Age
            string Status
        }
        PAYMENT {
            int Payment_ID PK
            int PNR FK
            decimal Amount
            string Method
            datetime Paid_On
        }
    ```

    Relationships and cardinality

    | Relationship | Cardinality | Explanation |
    |---|---|---|
    | Train runs on Schedule | `1 : N` | A train stops at many stations in order |
    | Station is stop in Schedule | `1 : N` | A station serves many trains |
    | Train stops at Station | `M : N` | Resolved by SCHEDULE, carrying arrival and departure times |
    | Train has Coach | `1 : N` | |
    | Coach contains Seat | `1 : N` | SEAT is a weak entity of Coach |
    | Passenger makes Booking | `1 : N` | |
    | Booking issues Ticket | `1 : N` | One PNR may cover several travellers |
    | Seat is allocated to Ticket | `1 : N` | The same seat on different dates |
    | Booking has Payment | `1 : 1` | |

    Design points worth stating
    - `SCHEDULE` is the associative entity resolving the M:N between Train and Station. Its descriptive attributes — stop number, arrival and departure times, distance — belong to the pairing of a train with a station, not to either alone.
    - A single `PNR` covering several passengers is why `BOOKING` and `TICKET` are separate. Merging them would make a family booking impossible to represent.
    - `Journey_Date` must be part of any seat-availability constraint: the same seat is bookable again on a different date, so uniqueness is over `(Seat_ID, Journey_Date)`, not `Seat_ID` alone. This is the subtlest point in the design.

    Key constraint
    ```sql
    CREATE TABLE Ticket (
        Ticket_ID INT PRIMARY KEY,
        PNR       INT NOT NULL REFERENCES Booking(PNR),
        Seat_ID   INT NOT NULL REFERENCES Seat(Seat_ID),
        Journey_Date DATE NOT NULL,
        Status    VARCHAR(20) DEFAULT 'Confirmed',
        UNIQUE (Seat_ID, Journey_Date)      -- one seat cannot be double-booked on a date
    );
    ```

    Typical query
    ```sql
    -- seats still free on a train for a given date and class
    SELECT s.Seat_No, c.Coach_No
    FROM   Seat s JOIN Coach c ON s.Coach_ID = c.Coach_ID
    WHERE  c.Train_No = 705 AND c.Class_Type = 'AC'
      AND  s.Seat_ID NOT IN (SELECT Seat_ID FROM Ticket
                             WHERE Journey_Date = '2025-08-15' AND Status = 'Confirmed');
    ```

18. **(i) Draw ER diagram: Given a scenario about football Game (Game_no, game_time, game_name), Team (team-id, coach_id, team-name), Referee (Referee-id, Referee-name) Player (player-id, palyername, player-position), Stadium information (stadium-id, stadium-name, stadium-loc) Match (match_id, match_date, match_result).** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 928-929 (ET: CTI)], [Janata Bank Assistant System Administrator 2021 compact it 939 (ET: N/A)]*
   **(ii) Convert the ER diagram to relations (Table)** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 929-930 (ET: CTI)]*

    Answer:

    Entities and attributes as given
    ```
    Game    (Game_no, game_time, game_name)
    Team    (Team_ID, Coach_ID, Team_Name)
    Referee (Referee_ID, Referee_Name)
    Player  (Player_ID, Player_Name, Player_Position)
    Stadium (Stadium_ID, Stadium_Name, Stadium_Loc)
    Match   (Match_ID, Match_Date, Match_Result)
    ```

    ER diagram
    ```mermaid
    erDiagram
        TEAM    ||--o{ PLAYER      : "has"
        COACH   ||--|| TEAM        : coaches
        TEAM    ||--o{ MATCH_TEAM  : "plays in"
        MATCH   ||--|{ MATCH_TEAM  : involves
        STADIUM ||--o{ MATCH       : hosts
        REFEREE ||--o{ MATCH_REF   : officiates
        MATCH   ||--o{ MATCH_REF   : "is officiated by"
        GAME    ||--o{ MATCH       : "is played as"
        PLAYER  ||--o{ PERFORMANCE : achieves
        MATCH   ||--o{ PERFORMANCE : records

        GAME {
            int Game_no PK
            string Game_Name
            time Game_Time
        }
        TEAM {
            int Team_ID PK
            string Team_Name
            int Coach_ID FK
        }
        COACH {
            int Coach_ID PK
            string Coach_Name
        }
        PLAYER {
            int Player_ID PK
            string Player_Name
            string Player_Position
            int Team_ID FK
        }
        REFEREE {
            int Referee_ID PK
            string Referee_Name
        }
        STADIUM {
            int Stadium_ID PK
            string Stadium_Name
            string Stadium_Loc
        }
        MATCH {
            int Match_ID PK
            date Match_Date
            string Match_Result
            int Stadium_ID FK
            int Game_no FK
        }
        MATCH_TEAM {
            int Match_ID PK-FK
            int Team_ID PK-FK
            int Goals_Scored
            string Home_Away
        }
        MATCH_REF {
            int Match_ID PK-FK
            int Referee_ID PK-FK
            string Role
        }
        PERFORMANCE {
            int Match_ID PK-FK
            int Player_ID PK-FK
            int Goals
            int Cards
        }
    ```

    Chen notation for the central structure
    ```
       +---------+       /---------\       +----------+
       |  TEAM   |------<    HAS    >------|  PLAYER  |
       +---------+  1    \---------/    N  +----------+
           | M
       /---------\
      <   PLAYS   >   (with Goals_Scored as a descriptive attribute)
       \---------/
           | N
       +---------+       /----------\       +-----------+
       |  MATCH  |------<  HOSTED_AT >------|  STADIUM  |
       +---------+  N    \----------/   1   +-----------+
           | M
       /-------------\
      <  OFFICIATES   >
       \-------------/
           | N
       +-----------+
       |  REFEREE  |
       +-----------+
    ```

    Relationships and cardinality

    | Relationship | Cardinality | Note |
    |---|---|---|
    | Team has Player | `1 : N` | A player belongs to one team |
    | Coach coaches Team | `1 : 1` | Coach_ID appears in Team, so one coach per team |
    | Team plays Match | `M : N` | Resolved by MATCH_TEAM; exactly two teams per match |
    | Stadium hosts Match | `1 : N` | One stadium, many matches |
    | Referee officiates Match | `M : N` | Several referees per match, and a referee works many matches |
    | Player performs in Match | `M : N` | Resolved by PERFORMANCE |
    | Game is played as Match | `1 : N` | A game type has many match instances |

    Design points
    - Both `Team–Match` and `Referee–Match` are `M:N`, so each needs its own table. This is the main thing the question tests.
    - `MATCH_TEAM` carries `Goals_Scored` and `Home_Away`, which belong to the pairing rather than to either entity.
    - `Coach_ID` is listed as an attribute of Team, which implies 1:1. If a coach could manage several teams over time, a separate `Coach_Team(Coach_ID, Team_ID, Season)` table would be needed.
    - `Match_Result` is `derived` from the goals in MATCH_TEAM, but is stored for query convenience.

    Tables
    ```sql
    CREATE TABLE Match_Team (
        Match_ID     INT,
        Team_ID      INT,
        Goals_Scored INT DEFAULT 0,
        Home_Away    CHAR(1) CHECK (Home_Away IN ('H','A')),
        PRIMARY KEY (Match_ID, Team_ID),
        FOREIGN KEY (Match_ID) REFERENCES Matches(Match_ID),
        FOREIGN KEY (Team_ID)  REFERENCES Team(Team_ID)
    );

    CREATE TABLE Match_Ref (
        Match_ID   INT,
        Referee_ID INT,
        Role       VARCHAR(20),          -- Main, Assistant, Fourth official
        PRIMARY KEY (Match_ID, Referee_ID),
        FOREIGN KEY (Match_ID)   REFERENCES Matches(Match_ID),
        FOREIGN KEY (Referee_ID) REFERENCES Referee(Referee_ID)
    );
    ```

19. **Draw ER diagram (Self test)** *[Combined 4 Banks Assistant Programmer 2020 compact it 1009 (ET: DU)]*

    Answer: The scenario was not printed, so the general method for drawing an ER diagram is given with a complete worked example, so it can be applied to any question of this type.

    The five steps

    - Step 1 — `Identify the entities`. Look for nouns the system stores data about. Each becomes a rectangle.
    - Step 2 — `Identify the attributes` of each entity, and underline the key attribute.
    - Step 3 — `Identify the relationships` from the verbs joining the nouns. Each becomes a diamond.
    - Step 4 — `Determine the cardinality` of every relationship: 1:1, 1:N or M:N.
    - Step 5 — `Determine participation`: total (double line) if every entity must participate, partial (single line) otherwise.

    Worked example — an employee and project system
    > "A company has several departments. Each department has many employees, and each employee works in exactly one department. Employees may be assigned to several projects, and a project may have several employees working on it, with the number of hours recorded. Each department is managed by one employee."

    ```mermaid
    erDiagram
        DEPARTMENT ||--o{ EMPLOYEE   : employs
        EMPLOYEE   ||--o| DEPARTMENT : manages
        EMPLOYEE   ||--o{ WORKS_ON   : "is assigned"
        PROJECT    ||--o{ WORKS_ON   : "has"
        EMPLOYEE   ||--o{ DEPENDENT  : supports

        DEPARTMENT {
            int Dept_ID PK
            string Dept_Name
            string Location
            int Manager_ID FK
        }
        EMPLOYEE {
            int Emp_ID PK
            string Name
            date DOB
            decimal Salary
            int Dept_ID FK
        }
        PROJECT {
            int Project_ID PK
            string Project_Name
            decimal Budget
        }
        WORKS_ON {
            int Emp_ID PK-FK
            int Project_ID PK-FK
            decimal Hours
        }
        DEPENDENT {
            int Emp_ID PK-FK
            string Dep_Name PK
            string Relationship
        }
    ```

    Chen notation
    ```
       +-------------+       /----------\       +------------+
       | DEPARTMENT  |======<   EMPLOYS   >-----|  EMPLOYEE  |
       +-------------+   1   \----------/    N  +------------+
       (Dept_ID) PK                                    | M
       (Dept_Name)                                /----------\
                                                 <  WORKS_ON  >---(Hours)
                                                  \----------/
                                                        | N
                                                 +------------+
                                                 |  PROJECT   |
                                                 +------------+

                                                 +============+
                                                 | DEPENDENT  |  <- weak entity
                                                 +============+
    ```

    Reading the four kinds of construct in this one diagram
    - `1 : N` — Department employs Employee. The department's key becomes a foreign key on Employee.
    - `M : N` — Employee works on Project, with `Hours` as a descriptive attribute. This needs its own table.
    - `1 : 1` — Employee manages Department. The foreign key goes on Department, declared UNIQUE.
    - `Weak entity` — Dependent has no key of its own; it is identified by `Emp_ID` plus the partial key `Dep_Name`.

    Converting to tables
    ```sql
    CREATE TABLE Department (
        Dept_ID    INT PRIMARY KEY,
        Dept_Name  VARCHAR(50) NOT NULL,
        Manager_ID INT UNIQUE REFERENCES Employee(Emp_ID)   -- UNIQUE gives the 1:1
    );

    CREATE TABLE Employee (
        Emp_ID  INT PRIMARY KEY,
        Name    VARCHAR(100) NOT NULL,
        Salary  DECIMAL(10,2),
        Dept_ID INT NOT NULL REFERENCES Department(Dept_ID) -- NOT NULL = total participation
    );

    CREATE TABLE Works_On (
        Emp_ID     INT,
        Project_ID INT,
        Hours      DECIMAL(6,2),
        PRIMARY KEY (Emp_ID, Project_ID),                   -- M:N resolved
        FOREIGN KEY (Emp_ID)     REFERENCES Employee(Emp_ID),
        FOREIGN KEY (Project_ID) REFERENCES Project(Project_ID)
    );

    CREATE TABLE Dependent (
        Emp_ID       INT,
        Dep_Name     VARCHAR(50),
        Relationship VARCHAR(20),
        PRIMARY KEY (Emp_ID, Dep_Name),                     -- weak entity key
        FOREIGN KEY (Emp_ID) REFERENCES Employee(Emp_ID) ON DELETE CASCADE
    );
    ```
    - The conversion rules in one line each: `1:N` puts the foreign key on the many side; `1:1` puts it on either side with UNIQUE; `M:N` needs a new table; a weak entity's key is the owner's key plus its partial key.

20. **E-R Diagram কী? উদাহরণসহ লিখুন?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019-1020 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    What an E-R diagram is
    - An `Entity-Relationship diagram` is a graphical, conceptual model of the data in a system. It shows the `entities` (things data is kept about), their `attributes` (properties) and the `relationships` between them.
    - Introduced by Peter Chen in 1976. It is independent of any DBMS, and it is the standard first step in database design: draw the diagram, agree it with the stakeholders, then convert it into tables.

    The notation

    | Symbol | Meaning |
    |---|---|
    | `Rectangle` | Entity |
    | `Double rectangle` | Weak entity |
    | `Oval` | Attribute |
    | `Underlined oval` | Key attribute (primary key) |
    | `Double oval` | Multivalued attribute |
    | `Dashed oval` | Derived attribute |
    | `Diamond` | Relationship |
    | `Double diamond` | Identifying relationship (to a weak entity) |
    | `Line` | Connects entity to attribute or relationship |
    | `Double line` | Total participation |
    | `1, N, M` on a line | Cardinality |

    Example — a university
    ```mermaid
    erDiagram
        DEPARTMENT ||--o{ STUDENT    : enrolls
        STUDENT    ||--o{ ENROLLMENT : registers
        COURSE     ||--o{ ENROLLMENT : "has"
        TEACHER    ||--o{ COURSE     : teaches

        DEPARTMENT {
            int Dept_ID PK
            string Dept_Name
        }
        STUDENT {
            int Student_ID PK
            string Name
            date DOB
            int Dept_ID FK
        }
        COURSE {
            string Course_ID PK
            string Title
            int Credits
        }
        ENROLLMENT {
            int Student_ID PK-FK
            string Course_ID PK-FK
            char Grade
        }
        TEACHER {
            int Teacher_ID PK
            string Name
        }
    ```

    Chen notation for the central relationship
    ```
                    (Student_ID)  (Name)   (Age)
                         |          |     .'
                         |          |    ' (dashed = derived from DOB)
                    +----------+          
                    | STUDENT  |
                    +----------+
                         | M
                    /----------\
                   <  ENROLLS   >----(Grade)   <- descriptive attribute
                    \----------/
                         | N
                    +----------+
                    |  COURSE  |
                    +----------+
                         |
                 (Course_ID)  (Title)  (Credits)
    ```

    Reading the example
    - `Entities`: Student, Course, Teacher, Department.
    - `Key attributes`: Student_ID, Course_ID, Teacher_ID, Dept_ID — each underlined.
    - `Derived attribute`: Age, computed from DOB, drawn with a dashed outline.
    - `Relationship`: Enrolls, between Student and Course.
    - `Cardinality`: M:N — a student takes many courses and a course has many students.
    - `Descriptive attribute`: Grade, belonging to the relationship rather than to either entity.

    Why the diagram matters
    - It settles, before any code is written, whether a relationship is 1:1, 1:N or M:N — which decides where every foreign key goes and whether an extra table is needed. Here the M:N immediately requires an `Enrollment` table.
    - It can be discussed with non-technical stakeholders, who can spot a wrong assumption that would be invisible in SQL.
    - The conversion to tables is then mechanical: entities become tables, attributes become columns, 1:N becomes a foreign key, and M:N becomes a junction table.

21. **Draw an ER diagram of a Library Management System.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036-1037 (ET: BUET)]*

    Answer: A library system centres on Members borrowing physical Copies of Books, with the important distinction between a `Book` (a title) and a `Copy` (a physical volume).

    ER diagram
    ```mermaid
    erDiagram
        AUTHOR   ||--o{ BOOK_AUTHOR : writes
        BOOK     ||--o{ BOOK_AUTHOR : "is written by"
        PUBLISHER||--o{ BOOK        : publishes
        CATEGORY ||--o{ BOOK        : classifies
        BOOK     ||--o{ COPY        : "has physical"
        MEMBER   ||--o{ LOAN        : borrows
        COPY     ||--o{ LOAN        : "is issued in"
        LOAN     ||--o| FINE        : incurs
        MEMBER   ||--o{ RESERVATION : makes
        BOOK     ||--o{ RESERVATION : "is reserved"
        STAFF    ||--o{ LOAN        : issues

        BOOK {
            string ISBN PK
            string Title
            int Publication_Year
            int Publisher_ID FK
            int Category_ID FK
        }
        AUTHOR {
            int Author_ID PK
            string Author_Name
            string Nationality
        }
        BOOK_AUTHOR {
            string ISBN PK-FK
            int Author_ID PK-FK
        }
        COPY {
            int Copy_ID PK
            string ISBN FK
            string Shelf_Location
            string Status
            date Acquired_Date
        }
        MEMBER {
            int Member_ID PK
            string Name
            string Address
            string Phone
            date Membership_Date
            string Member_Type
        }
        LOAN {
            int Loan_ID PK
            int Copy_ID FK
            int Member_ID FK
            int Staff_ID FK
            date Issue_Date
            date Due_Date
            date Return_Date
        }
        FINE {
            int Fine_ID PK
            int Loan_ID FK
            decimal Amount
            string Status
        }
        RESERVATION {
            int Res_ID PK
            int Member_ID FK
            string ISBN FK
            date Res_Date
            string Status
        }
        PUBLISHER {
            int Publisher_ID PK
            string Publisher_Name
            string Address
        }
        CATEGORY {
            int Category_ID PK
            string Category_Name
        }
        STAFF {
            int Staff_ID PK
            string Name
            string Designation
        }
    ```

    Chen notation for the core
    ```
       +----------+       /---------\       +========+
       |   BOOK   |======<    HAS    >======|  COPY  |
       +----------+   1   \---------/    N  +========+
       (ISBN) PK                                 | N
       (Title)                              /---------\
                                           <   LOAN    >----(Issue_Date)
                                            \---------/     (Due_Date)
                                                 | N        (Return_Date)
                                           +----------+
                                           |  MEMBER  |
                                           +----------+
    ```

    Relationships and cardinality

    | Relationship | Cardinality | Note |
    |---|---|---|
    | Book has Copy | `1 : N` | One title, many physical volumes |
    | Author writes Book | `M : N` | Resolved by BOOK_AUTHOR |
    | Publisher publishes Book | `1 : N` | |
    | Member borrows Copy | `M : N` | Resolved by LOAN, holding the dates |
    | Loan incurs Fine | `1 : 0..1` | Only overdue loans generate a fine |
    | Member reserves Book | `M : N` | Reservation is against the title, not a copy |
    | Staff issues Loan | `1 : N` | |

    The three design decisions worth explaining
    - `BOOK versus COPY` is the central one. A loan must record `which physical volume` left the building, so that the library knows exactly which one is missing. Merging them would make that impossible.
    - `RESERVATION is against the ISBN, not the Copy_ID`, because a member wants `any` copy of the title, not one particular volume.
    - `LOAN` is the associative entity resolving the M:N between Member and Copy, and its dates are descriptive attributes of that pairing.

    Core tables
    ```sql
    CREATE TABLE Copy (
        Copy_ID        INT PRIMARY KEY,
        ISBN           VARCHAR(20) NOT NULL REFERENCES Book(ISBN),
        Shelf_Location VARCHAR(50),
        Status         VARCHAR(20) DEFAULT 'Available'
                       CHECK (Status IN ('Available','Issued','Lost','Damaged'))
    );

    CREATE TABLE Loan (
        Loan_ID     INT PRIMARY KEY,
        Copy_ID     INT NOT NULL REFERENCES Copy(Copy_ID),
        Member_ID   INT NOT NULL REFERENCES Member(Member_ID),
        Issue_Date  DATE NOT NULL,
        Due_Date    DATE NOT NULL,
        Return_Date DATE,
        CHECK (Due_Date > Issue_Date)
    );
    ```

    Typical query
    ```sql
    -- overdue loans with the member's contact details
    SELECT m.Name, m.Phone, b.Title, l.Due_Date,
           DATEDIFF(CURDATE(), l.Due_Date) AS days_overdue
    FROM   Loan l
    JOIN   Member m ON l.Member_ID = m.Member_ID
    JOIN   Copy   c ON l.Copy_ID   = c.Copy_ID
    JOIN   Book   b ON c.ISBN      = b.ISBN
    WHERE  l.Return_Date IS NULL AND l.Due_Date < CURDATE();
    ```

22. **(ক) Database এর ক্ষেত্রে E-R Diagram বলতে কী বোঝায়? একটি উদাহরণের মাধ্যমে ব্যাখ্যা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1094 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    What an E-R diagram means in a database context
    - An `Entity-Relationship diagram` is a graphical, conceptual model of the data a system must store. It shows `entities` (the things data is kept about), their `attributes` (properties) and the `relationships` between them, together with the cardinality of each relationship.
    - It is drawn before any table is created, is independent of any DBMS, and forms the blueprint from which the tables are derived.
    - Introduced by Peter Chen in 1976.

    The symbols

    | Symbol | Meaning |
    |---|---|
    | Rectangle | Entity |
    | Double rectangle | Weak entity |
    | Oval | Attribute |
    | Underlined oval | Key attribute |
    | Double oval | Multivalued attribute |
    | Dashed oval | Derived attribute |
    | Diamond | Relationship |
    | Double line | Total participation |
    | 1, N, M | Cardinality |

    Worked example — a hospital
    ```mermaid
    erDiagram
        DEPARTMENT  ||--o{ DOCTOR      : employs
        DOCTOR      ||--o{ APPOINTMENT : attends
        PATIENT     ||--o{ APPOINTMENT : books

        DEPARTMENT {
            int Dept_ID PK
            string Dept_Name
        }
        DOCTOR {
            int Doctor_ID PK
            string Name
            string Specialization
            int Dept_ID FK
        }
        PATIENT {
            int Patient_ID PK
            string Name
            date DOB
            string Phone
        }
        APPOINTMENT {
            int Appt_ID PK
            int Patient_ID FK
            int Doctor_ID FK
            datetime Appt_DateTime
            string Diagnosis
        }
    ```

    Chen notation for the same
    ```
                  (Patient_ID)   (Name)   (Age)
                        |          |      .'  (dashed = derived from DOB)
                   +-----------+
                   |  PATIENT  |
                   +-----------+
                         | M
                    /-------------\
                   <  APPOINTMENT  >----(Appt_DateTime)
                    \-------------/     (Diagnosis)
                         | N
                   +-----------+          /----------\        +--------------+
                   |  DOCTOR   |=========<  BELONGS   >=======| DEPARTMENT   |
                   +-----------+    N     \----------/    1   +--------------+
                         |
              (Doctor_ID)  (Name)  (Specialization)
    ```

    Reading it
    - `Entities`: Patient, Doctor, Department.
    - `Key attributes`: Patient_ID, Doctor_ID, Dept_ID — underlined.
    - `Derived attribute`: Age, computed from DOB, drawn dashed.
    - `Relationship`: Appointment, between Patient and Doctor.
    - `Cardinality`: `M : N` — a patient sees many doctors over time, and a doctor sees many patients.
    - `Descriptive attributes`: Appt_DateTime and Diagnosis, belonging to the appointment itself.
    - `Participation`: Doctor's participation in "belongs to a department" is `total` (double line) — every doctor must be in a department.

    Converting it to tables
    ```sql
    CREATE TABLE Doctor (
        Doctor_ID      INT PRIMARY KEY,
        Name           VARCHAR(100) NOT NULL,
        Specialization VARCHAR(50),
        Dept_ID        INT NOT NULL REFERENCES Department(Dept_ID)   -- 1:N -> FK
    );

    CREATE TABLE Appointment (                                       -- M:N -> new table
        Appt_ID       INT PRIMARY KEY,
        Patient_ID    INT NOT NULL REFERENCES Patient(Patient_ID),
        Doctor_ID     INT NOT NULL REFERENCES Doctor(Doctor_ID),
        Appt_DateTime DATETIME NOT NULL,
        Diagnosis     TEXT,
        UNIQUE (Doctor_ID, Appt_DateTime)
    );
    ```
    - The conversion rules: an entity becomes a table; a `1:N` relationship becomes a foreign key on the many side; an `M:N` relationship becomes its own table with a composite key; and a descriptive attribute goes into that table.

23. **Explain E-R diagram with example?** *[BINA Assistant Programmer 2019 compact it 1155 (ET: IBA)]*

    Answer:

    What an E-R diagram is
    - An `Entity-Relationship diagram` is a conceptual, graphical model of the data in a system, showing `entities`, their `attributes` and the `relationships` between them, with cardinality and participation marked.
    - It is drawn before implementation, is independent of any DBMS, and is the blueprint from which tables are derived. Introduced by Peter Chen in 1976.

    Components

    `Entity` — a thing data is stored about. Drawn as a rectangle. A `weak entity`, which has no key of its own, is drawn as a double rectangle.

    `Attribute` — a property of an entity. Drawn as an oval.
    - `Key` (underlined), `composite` (divisible into parts), `multivalued` (double oval), `derived` (dashed oval), `simple` (atomic).

    `Relationship` — an association between entities. Drawn as a diamond. It may have its own `descriptive attributes`.

    `Cardinality` — 1:1, 1:N or M:N.

    `Participation` — total (double line) if every entity must take part, partial (single line) otherwise.

    Worked example — an online bookshop
    ```mermaid
    erDiagram
        CUSTOMER ||--o{ ORDER      : places
        ORDER    ||--|{ ORDER_ITEM : contains
        BOOK     ||--o{ ORDER_ITEM : "appears in"
        AUTHOR   ||--o{ BOOK       : writes

        CUSTOMER {
            int Customer_ID PK
            string Name
            string Email
            string Address
        }
        ORDER {
            int Order_ID PK
            int Customer_ID FK
            date Order_Date
            decimal Total
        }
        ORDER_ITEM {
            int Order_ID PK-FK
            string ISBN PK-FK
            int Quantity
            decimal Unit_Price
        }
        BOOK {
            string ISBN PK
            string Title
            decimal Price
            int Author_ID FK
        }
        AUTHOR {
            int Author_ID PK
            string Author_Name
        }
    ```

    Chen notation
    ```
         (Customer_ID)  (Name)  (Email)
                |         |       |
            +------------+
            |  CUSTOMER  |
            +------------+
                 | 1
            /---------\
           <  PLACES   >
            \---------/
                 | N
            +---------+       /------------\       +--------+
            |  ORDER  |======<   CONTAINS   >------|  BOOK  |
            +---------+   M   \------------/    N  +--------+
                                     |
                              +------+------+
                              |             |
                         (Quantity)   (Unit_Price)   <- descriptive attributes
    ```

    Reading it
    - `Customer places Order` is `1:N` — one customer, many orders. The customer's key becomes a foreign key on Order.
    - `Order contains Book` is `M:N` — an order holds several books and a book appears in many orders. This needs the `ORDER_ITEM` table.
    - `Quantity` and `Unit_Price` are `descriptive attributes` of that relationship. Storing `Unit_Price` here rather than reading it from Book is deliberate: the price on an old invoice must not change when the book's price changes.
    - `Order has total participation` in "contains" — an order with no items is meaningless.

    Converting to tables
    ```sql
    CREATE TABLE Orders (
        Order_ID    INT PRIMARY KEY,
        Customer_ID INT NOT NULL REFERENCES Customer(Customer_ID),   -- 1:N
        Order_Date  DATE NOT NULL,
        Total       DECIMAL(12,2)
    );

    CREATE TABLE Order_Item (                                        -- M:N
        Order_ID   INT,
        ISBN       VARCHAR(20),
        Quantity   INT NOT NULL CHECK (Quantity > 0),
        Unit_Price DECIMAL(10,2) NOT NULL,
        PRIMARY KEY (Order_ID, ISBN),
        FOREIGN KEY (Order_ID) REFERENCES Orders(Order_ID) ON DELETE CASCADE,
        FOREIGN KEY (ISBN)     REFERENCES Book(ISBN)
    );
    ```
    - The rules in summary: entity → table; `1:N` → foreign key on the many side; `1:1` → foreign key with UNIQUE; `M:N` → a new table with a composite key; multivalued attribute → its own table; weak entity → owner's key plus partial key.

24. **Daraz is proud of having up-to-date information on the processing and current location of each shipped item. Daraz relies on a company-wide information system. Shipped items are the heart of the Daraz product tracking information system. Shipped items can be characterized by item number, weight, dimensions, insurance amount, destination and final delivery date. Shipped items are received into the Daraz system at a single retail center. Retail center are characterized by their type, ID and address. Shipped items make their way to their destination via one or more standard Daraz transportation events (flights, truck deliveries). These transportation events are characterized by a schedule number, a type (e.g. flight, truck), and a delivery route. Please create an entity relationship diagram that captures this information about the Daraz system. Be certain to indicate identifiers and cardinality constraints.** *[Sonali & Janata Bank Senior Officer (IT/ICT) 2018 compact it 1166 (ET: N/A)]*

    Answer: The system tracks `Shipped Items` that enter at a `Retail Center` and travel to their destination through one or more `Transportation Events`.

    ER diagram
    ```mermaid
    erDiagram
        RETAIL_CENTER ||--o{ SHIPPED_ITEM      : receives
        SHIPPED_ITEM  ||--|{ ITEM_TRANSPORT    : "travels via"
        TRANSPORT_EVENT ||--o{ ITEM_TRANSPORT  : carries
        SHIPPED_ITEM  ||--o{ TRACKING_LOG      : "is tracked in"

        SHIPPED_ITEM {
            int Item_Number PK
            decimal Weight
            string Dimensions
            decimal Insurance_Amount
            string Destination
            date Final_Delivery_Date
            int Center_ID FK
        }
        RETAIL_CENTER {
            int Center_ID PK
            string Center_Type
            string Address
        }
        TRANSPORT_EVENT {
            int Schedule_Number PK
            string Event_Type
            string Delivery_Route
            datetime Departure_Time
            datetime Arrival_Time
        }
        ITEM_TRANSPORT {
            int Item_Number PK-FK
            int Schedule_Number PK-FK
            int Leg_Sequence
            datetime Loaded_At
        }
        TRACKING_LOG {
            int Log_ID PK
            int Item_Number FK
            string Current_Location
            datetime Scan_Time
            string Status
        }
    ```

    Chen notation
    ```
       +==================+        /-----------\        +-----------------+
       |  RETAIL_CENTER   |=======<  RECEIVES   >======>|  SHIPPED_ITEM   |
       +==================+   1    \-----------/    N   +-----------------+
       (Center_ID) PK                                   (Item_Number) PK
       (Center_Type)                                    (Weight)
       (Address)                                        (Dimensions)
                                                        (Insurance_Amount)
                                                        (Destination)
                                                        (Final_Delivery_Date)
                                                                | M
                                                         /-------------\
                                                        <  TRAVELS_VIA  >---(Leg_Sequence)
                                                         \-------------/
                                                                | N
                                                      +---------------------+
                                                      |  TRANSPORT_EVENT    |
                                                      +---------------------+
                                                      (Schedule_Number) PK
                                                      (Event_Type)
                                                      (Delivery_Route)
    ```

    Identifiers, as the question requires
    - `SHIPPED_ITEM` — `Item_Number`
    - `RETAIL_CENTER` — `Center_ID`
    - `TRANSPORT_EVENT` — `Schedule_Number`
    - `ITEM_TRANSPORT` — the composite key `(Item_Number, Schedule_Number)`

    Cardinality constraints, as the question requires

    | Relationship | Cardinality | Reason from the text |
    |---|---|---|
    | Retail Center receives Shipped Item | `1 : N` | "received into the system at a `single` retail center" |
    | Shipped Item travels via Transport Event | `M : N` | "via `one or more` standard transportation events"; a flight or truck also carries many items |
    | Shipped Item has Tracking Log | `1 : N` | Each scan along the route produces one entry |

    Participation constraints
    - `SHIPPED_ITEM has total participation` in "receives" — every item enters at exactly one centre, so the double line and a `NOT NULL` foreign key.
    - `SHIPPED_ITEM has total participation` in "travels via" — an item must make at least one transportation event to reach its destination. This is why the mermaid diagram uses `||--|{`.
    - `RETAIL_CENTER` and `TRANSPORT_EVENT` have `partial` participation: a newly opened centre may hold no items, and a scheduled flight may be carrying none.

    The key design decision
    - `ITEM_TRANSPORT` is the associative entity resolving the `M:N` between item and transport event. Its descriptive attribute `Leg_Sequence` records the `order` of the legs, which is essential — an item flying Dhaka → Dubai → London must know which leg came first. Without this attribute the route could not be reconstructed.

    Tables
    ```sql
    CREATE TABLE Shipped_Item (
        Item_Number         INT PRIMARY KEY,
        Weight              DECIMAL(10,2),
        Dimensions          VARCHAR(50),
        Insurance_Amount    DECIMAL(12,2),
        Destination         VARCHAR(200) NOT NULL,
        Final_Delivery_Date DATE,
        Center_ID           INT NOT NULL REFERENCES Retail_Center(Center_ID)
    );

    CREATE TABLE Item_Transport (
        Item_Number     INT,
        Schedule_Number INT,
        Leg_Sequence    INT NOT NULL,
        Loaded_At       DATETIME,
        PRIMARY KEY (Item_Number, Schedule_Number),
        UNIQUE (Item_Number, Leg_Sequence),           -- no two legs share a position
        FOREIGN KEY (Item_Number)     REFERENCES Shipped_Item(Item_Number),
        FOREIGN KEY (Schedule_Number) REFERENCES Transport_Event(Schedule_Number)
    );
    ```

    Query the design supports
    ```sql
    -- full route of one parcel, in order
    SELECT te.Event_Type, te.Delivery_Route, it.Leg_Sequence, it.Loaded_At
    FROM   Item_Transport it JOIN Transport_Event te
           ON it.Schedule_Number = te.Schedule_Number
    WHERE  it.Item_Number = 100234
    ORDER  BY it.Leg_Sequence;
    ```

25. **Design ER diagram for Online MCQ examination portal. Your design must contain separate entities for student, examination, question, solution and submission. Ensure that normalization is ful-fill in your design and identify the primary and foreign key.** *[Combined 3 Banks Assistant Programmer 2018 compact it 1196-1197 (ET: N/A)]*

    Answer: The design must contain separate entities for Student, Examination, Question, Solution and Submission, and must be normalised with keys identified.

    ER diagram
    ```mermaid
    erDiagram
        STUDENT     ||--o{ SUBMISSION  : makes
        EXAMINATION ||--o{ SUBMISSION  : receives
        EXAMINATION ||--o{ EXAM_QUESTION : contains
        QUESTION    ||--o{ EXAM_QUESTION : "appears in"
        QUESTION    ||--|{ OPTION      : "has"
        QUESTION    ||--|| SOLUTION    : "has correct"
        SUBMISSION  ||--o{ ANSWER      : contains
        QUESTION    ||--o{ ANSWER      : "is answered in"
        SUBJECT     ||--o{ QUESTION    : classifies

        STUDENT {
            int Student_ID PK
            string Name
            string Email
            string Password_Hash
            date Registration_Date
        }
        EXAMINATION {
            int Exam_ID PK
            string Exam_Title
            datetime Start_Time
            int Duration_Minutes
            int Total_Marks
            decimal Negative_Marking
        }
        QUESTION {
            int Question_ID PK
            text Question_Text
            int Subject_ID FK
            string Difficulty
            decimal Marks
        }
        OPTION {
            int Option_ID PK
            int Question_ID FK
            char Option_Label
            text Option_Text
        }
        SOLUTION {
            int Solution_ID PK
            int Question_ID FK
            int Correct_Option_ID FK
            text Explanation
        }
        EXAM_QUESTION {
            int Exam_ID PK-FK
            int Question_ID PK-FK
            int Question_Order
        }
        SUBMISSION {
            int Submission_ID PK
            int Student_ID FK
            int Exam_ID FK
            datetime Started_At
            datetime Submitted_At
            decimal Total_Score
        }
        ANSWER {
            int Submission_ID PK-FK
            int Question_ID PK-FK
            int Chosen_Option_ID FK
            boolean Is_Correct
            decimal Marks_Awarded
        }
        SUBJECT {
            int Subject_ID PK
            string Subject_Name
        }
    ```

    Primary and foreign keys

    | Entity | Primary key | Foreign keys |
    |---|---|---|
    | STUDENT | Student_ID | — |
    | EXAMINATION | Exam_ID | — |
    | SUBJECT | Subject_ID | — |
    | QUESTION | Question_ID | Subject_ID → Subject |
    | OPTION | Option_ID | Question_ID → Question |
    | SOLUTION | Solution_ID | Question_ID → Question, Correct_Option_ID → Option |
    | EXAM_QUESTION | (Exam_ID, Question_ID) | both, to Examination and Question |
    | SUBMISSION | Submission_ID | Student_ID → Student, Exam_ID → Examination |
    | ANSWER | (Submission_ID, Question_ID) | both, plus Chosen_Option_ID → Option |

    Cardinality

    | Relationship | Cardinality |
    |---|---|
    | Student makes Submission | 1 : N |
    | Examination receives Submission | 1 : N |
    | Examination contains Question | `M : N` — resolved by EXAM_QUESTION |
    | Question has Option | 1 : N (typically 4) |
    | Question has Solution | `1 : 1` |
    | Submission contains Answer | 1 : N |

    How normalisation is satisfied
    - `1NF` — every attribute is atomic. The four options are `not` stored as four columns in Question; they are rows in a separate `OPTION` table. Storing option_a, option_b, option_c, option_d would be a repeating group and would also make five-option questions impossible.
    - `2NF` — in the composite-key tables `EXAM_QUESTION` and `ANSWER`, every non-key attribute depends on the `whole` key. `Question_Order` depends on both the exam and the question; `Is_Correct` depends on both the submission and the question.
    - `3NF` — no transitive dependency. `Subject_Name` lives in SUBJECT, not repeated in QUESTION; the student's name lives in STUDENT, not copied into SUBMISSION.
    - The `SOLUTION` entity is separated from QUESTION so that the correct answer and explanation can be `hidden` from the student's session — a security benefit as well as a normalisation one.

    Key tables
    ```sql
    CREATE TABLE Question (
        Question_ID   INT PRIMARY KEY,
        Question_Text TEXT NOT NULL,
        Subject_ID    INT NOT NULL REFERENCES Subject(Subject_ID),
        Marks         DECIMAL(4,2) DEFAULT 1
    );

    CREATE TABLE Option (
        Option_ID    INT PRIMARY KEY,
        Question_ID  INT NOT NULL REFERENCES Question(Question_ID) ON DELETE CASCADE,
        Option_Label CHAR(1) NOT NULL,
        Option_Text  TEXT NOT NULL,
        UNIQUE (Question_ID, Option_Label)
    );

    CREATE TABLE Solution (
        Solution_ID       INT PRIMARY KEY,
        Question_ID       INT NOT NULL UNIQUE REFERENCES Question(Question_ID),
        Correct_Option_ID INT NOT NULL REFERENCES Option(Option_ID),
        Explanation       TEXT
    );

    CREATE TABLE Submission (
        Submission_ID INT PRIMARY KEY,
        Student_ID    INT NOT NULL REFERENCES Student(Student_ID),
        Exam_ID       INT NOT NULL REFERENCES Examination(Exam_ID),
        Started_At    DATETIME NOT NULL,
        Submitted_At  DATETIME,
        Total_Score   DECIMAL(6,2),
        UNIQUE (Student_ID, Exam_ID)          -- one attempt per student per exam
    );

    CREATE TABLE Answer (
        Submission_ID    INT,
        Question_ID      INT,
        Chosen_Option_ID INT REFERENCES Option(Option_ID),
        Is_Correct       BOOLEAN,
        Marks_Awarded    DECIMAL(4,2),
        PRIMARY KEY (Submission_ID, Question_ID),
        FOREIGN KEY (Submission_ID) REFERENCES Submission(Submission_ID) ON DELETE CASCADE,
        FOREIGN KEY (Question_ID)   REFERENCES Question(Question_ID)
    );
    ```
    - `UNIQUE (Question_ID)` on Solution is what enforces the `1:1` relationship. `UNIQUE (Student_ID, Exam_ID)` on Submission enforces one attempt per exam — a genuine business rule pushed into the database rather than left to application code.

## Normalization & Database Design (21)

1. **What is Normalization? How do 1NF and 2NF work in a database? Give examples.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

   Answer:

   What is normalisation
   - `Normalisation` is the process of organising the columns and tables of a relational database to `reduce redundancy` and eliminate `update anomalies`, by decomposing a large table into smaller related tables joined by keys.
   - Proposed by E. F. Codd. It proceeds through a series of `normal forms`, each stricter than the last: 1NF, 2NF, 3NF, BCNF, 4NF, 5NF.

   The three anomalies it removes
   - `Insertion anomaly` — a new course cannot be recorded until some student enrols in it.
   - `Update anomaly` — a teacher's name stored in twenty rows must be changed in all twenty, and missing one leaves the data inconsistent.
   - `Deletion anomaly` — deleting the last student on a course also destroys the record of the course itself.

   First Normal Form (1NF)
   - Rule: every column must hold an `atomic` (indivisible) value; there must be no repeating groups; each row must be unique; and each column must have a unique name.

   `Violating 1NF`
   ```
   Student
   +------------+-------+---------------------+
   | Student_ID | Name  | Phone               |
   +------------+-------+---------------------+
   |    101     | Karim | 01711111, 01822222  |   <- two values in one cell
   |    102     | Rahim | 01933333            |
   +------------+-------+---------------------+
   ```

   `In 1NF` — one value per cell
   ```
   Student                          Student_Phone
   +------------+-------+           +------------+----------+
   | Student_ID | Name  |           | Student_ID | Phone    |
   +------------+-------+           +------------+----------+
   |    101     | Karim |           |    101     | 01711111 |
   |    102     | Rahim |           |    101     | 01822222 |
   +------------+-------+           |    102     | 01933333 |
                                    +------------+----------+
   ```
   - Putting the numbers in `Phone1` and `Phone2` columns instead would also break 1NF, because it is a repeating group and it fixes an arbitrary maximum.

   Second Normal Form (2NF)
   - Rule: the table must be in 1NF, and every `non-key attribute` must depend on the `whole` primary key, not on part of it. This only becomes an issue when the primary key is `composite`.
   - The problem it removes is `partial dependency`.

   `Violating 2NF`
   ```
   Enrollment  — primary key (Student_ID, Course_ID)
   +------------+-----------+--------------+-------------+-------+
   | Student_ID | Course_ID | Student_Name | Course_Name | Grade |
   +------------+-----------+--------------+-------------+-------+
   |    101     |   CS101   | Karim        | Database    |   A   |
   |    101     |   CS102   | Karim        | Networking  |   B   |
   |    102     |   CS101   | Rahim        | Database    |   A   |
   +------------+-----------+--------------+-------------+-------+

   Student_Name depends only on Student_ID  -> partial dependency
   Course_Name  depends only on Course_ID   -> partial dependency
   Grade        depends on BOTH             -> full dependency, correct
   ```
   - Note the redundancy: "Karim" and "Database" are each repeated, and changing a course name means changing many rows.

   `In 2NF` — split so that each attribute sits with the key it actually depends on
   ```
   Student                     Course                       Enrollment
   +------------+-------+      +-----------+------------+   +------------+-----------+-------+
   | Student_ID | Name  |      | Course_ID | Course_Name|   | Student_ID | Course_ID | Grade |
   +------------+-------+      +-----------+------------+   +------------+-----------+-------+
   |    101     | Karim |      |   CS101   | Database   |   |    101     |   CS101   |   A   |
   |    102     | Rahim |      |   CS102   | Networking |   |    101     |   CS102   |   B   |
   +------------+-------+      +-----------+------------+   |    102     |   CS101   |   A   |
                                                            +------------+-----------+-------+
   ```
   - Each fact is now stored `once`. A course name is changed in one place, a new course can be created before anyone enrols, and deleting the last enrolment does not destroy the course.

   The next step
   - `3NF` removes `transitive dependency` — a non-key attribute depending on another non-key attribute rather than directly on the key.

2. **Why normalization is required in Database? Write shortly about 3NF?** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1350 (ET: N/A)]*

   Answer:

   Why normalisation is required

   1. `To eliminate data redundancy`
   - Without it, the same fact is stored many times. A department name repeated in every employee row wastes space and, worse, allows the copies to disagree.

   2. `To prevent the three anomalies`
   - `Insertion anomaly` — a new department cannot be recorded until an employee is hired into it.
   - `Update anomaly` — changing a department name requires updating every row that mentions it; missing one leaves the database inconsistent.
   - `Deletion anomaly` — deleting the last employee of a department destroys the department's record as well.

   3. `To ensure data consistency and integrity`
   - Each fact is stored exactly once, so it cannot contradict itself.

   4. `To make the design flexible`
   - Adding a new attribute or entity does not require restructuring everything.

   5. `To save storage` and reduce the volume of data written on every update.

   6. `To produce a clear, logical structure` that reflects the real relationships in the data.

   Third Normal Form (3NF)

   - Rule: the table must be in `2NF`, and there must be `no transitive dependency` — that is, no non-key attribute may depend on another non-key attribute.
   - Formally: for every functional dependency `X → Y`, either X is a superkey, or Y is a prime attribute (part of some candidate key).
   - The phrase to remember: `every non-key attribute must depend on the key, the whole key, and nothing but the key`.

   `Violating 3NF`
   ```
   Employee  — primary key Emp_ID
   +--------+----------+---------+-------------+
   | Emp_ID | Emp_Name | Dept_ID | Dept_Name   |
   +--------+----------+---------+-------------+
   |  101   | Karim    |   10    | IT          |
   |  102   | Rahim    |   10    | IT          |
   |  103   | Sumi     |   20    | HR          |
   +--------+----------+---------+-------------+

   Emp_ID -> Dept_ID -> Dept_Name

   Dept_Name depends on Dept_ID, which is not a key. It therefore depends on
   Emp_ID only INDIRECTLY — a transitive dependency.
   ```
   - Consequences: "IT" is repeated; renaming the department means updating many rows; a new department cannot be created without an employee; and deleting employee 103 loses the HR department entirely.

   `In 3NF`
   ```
   Employee                              Department
   +--------+----------+---------+       +---------+-------------+
   | Emp_ID | Emp_Name | Dept_ID |       | Dept_ID | Dept_Name   |
   +--------+----------+---------+       +---------+-------------+
   |  101   | Karim    |   10    |       |   10    | IT          |
   |  102   | Rahim    |   10    |       |   20    | HR          |
   |  103   | Sumi     |   20    |       +---------+-------------+
   +--------+----------+---------+
   ```
   - The department name is now stored once. All three anomalies disappear, and the two tables are rejoined by a foreign key whenever the combined view is needed.

   ```sql
   SELECT e.Emp_Name, d.Dept_Name
   FROM   Employee e JOIN Department d ON e.Dept_ID = d.Dept_ID;
   ```

   The trade-off worth stating
   - Normalisation reduces redundancy but increases the number of `joins`. In a read-heavy reporting system or a data warehouse, deliberate `denormalisation` is sometimes chosen to avoid those joins — accepting controlled redundancy in exchange for speed. That is a considered decision, not an excuse for a badly designed transactional schema.

3. **Explain the differences between Second Normal Form (2NF) and Third Normal Form (3NF) with examples.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1340 (ET: N/A)]*

| 2NF(Second Normal Form) | 3NF(Third Normal Form) |
|---|---|
| It is already in 1NF. | It is already in 1NF as well as in 2NF also. |
| In 2NF, non-prime attributes (attributes that are not part of any candidate key) must depend on the entire candidate key. | In 3NF non-prime attributes are only allowed to be functionally dependent on Super key of relation. |
| No partial functional dependency of non-prime attributes on any proper subset of a candidate key is allowed. | No transitive functional dependency of non-prime attributes on any super key is allowed. |
| Stronger normal form than 1NF but lesser than 3NF. | Stronger normal form than 1NF and 2NF. |
| It eliminates repeating groups in relation. | It virtually eliminates all the redundancies. |
| The goal of the second normal form is to eliminate redundant data. | The goal of the third normal form is to ensure referential integrity. |

   Answer:

   The two definitions
   - `2NF` — the table is in 1NF and there is `no partial dependency`: every non-key attribute depends on the `whole` primary key.
   - `3NF` — the table is in 2NF and there is `no transitive dependency`: no non-key attribute depends on another non-key attribute.

   Comparison

   | Point | 2NF | 3NF |
   |---|---|---|
   | Prerequisite | Must be in 1NF | Must be in 2NF |
   | Removes | `Partial` dependency | `Transitive` dependency |
   | The dependency concerned | Non-key attribute → part of a composite key | Non-key attribute → another non-key attribute |
   | Only arises when | The primary key is `composite` | Any key, even a single-column one |
   | Rule of thumb | Depends on the `whole` key | Depends on `nothing but` the key |
   | Strictness | Less strict | Stricter |

   2NF example — partial dependency

   `Violating 2NF`, primary key (Student_ID, Course_ID)
   ```
   +------------+-----------+--------------+-------------+-------+
   | Student_ID | Course_ID | Student_Name | Course_Name | Grade |
   +------------+-----------+--------------+-------------+-------+
   |    101     |   CS101   | Karim        | Database    |   A   |
   |    101     |   CS102   | Karim        | Networking  |   B   |
   |    102     |   CS101   | Rahim        | Database    |   A   |
   +------------+-----------+--------------+-------------+-------+

   Student_ID -> Student_Name    (part of the key only) -> PARTIAL
   Course_ID  -> Course_Name     (part of the key only) -> PARTIAL
   (Student_ID, Course_ID) -> Grade                     -> full, correct
   ```

   `In 2NF`
   ```
   Student(Student_ID, Student_Name)
   Course(Course_ID, Course_Name)
   Enrollment(Student_ID, Course_ID, Grade)
   ```

   3NF example — transitive dependency

   `Violating 3NF`, primary key Emp_ID — note the key is a single column, so 2NF is not the issue
   ```
   +--------+----------+---------+-------------+
   | Emp_ID | Emp_Name | Dept_ID | Dept_Name   |
   +--------+----------+---------+-------------+
   |  101   | Karim    |   10    | IT          |
   |  102   | Rahim    |   10    | IT          |
   |  103   | Sumi     |   20    | HR          |
   +--------+----------+---------+-------------+

   Emp_ID -> Dept_ID -> Dept_Name

   Dept_Name depends on Dept_ID, and Dept_ID is not a key,
   so Dept_Name depends on Emp_ID only TRANSITIVELY.
   ```

   `In 3NF`
   ```
   Employee(Emp_ID, Emp_Name, Dept_ID)
   Department(Dept_ID, Dept_Name)
   ```

   The essential distinction
   - `2NF` is about an attribute depending on `only part of a composite key`. It cannot occur at all when the primary key is a single column.
   - `3NF` is about an attribute depending on a `non-key attribute`. It can occur with any key, composite or not.
   - Both remove the same three anomalies — insertion, update and deletion — but they remove different `causes` of them.

   The mnemonic
   > Every non-key attribute must depend on `the key` (1NF), `the whole key` (2NF), and `nothing but the key` (3NF).

4. **What is Logical design database is called?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: The logical design of a database is called the `schema` — more precisely, the `logical schema` or `conceptual schema`.

   The three levels of design

   | Stage | Name | What it produces |
   |---|---|---|
   | Conceptual design | `Conceptual schema` | The ER diagram — entities, attributes, relationships, independent of any DBMS |
   | `Logical design` | `Logical schema` | The relational schema — tables, columns, keys, constraints, normalised |
   | Physical design | `Physical / internal schema` | Storage structures, file organisation, indexes, partitions |

   What logical design produces
   - Converting the ER model into `tables`; choosing data types; defining primary, foreign and unique keys; applying `normalisation`; and specifying integrity constraints.
   - It is `DBMS-independent` in principle, though it is expressed in relational terms.

   ```sql
   -- the logical schema, written as DDL
   CREATE TABLE Employee (
       emp_id   INT PRIMARY KEY,
       emp_name VARCHAR(100) NOT NULL,
       salary   DECIMAL(10,2) CHECK (salary > 0),
       dept_id  INT REFERENCES Department(dept_id)
   );
   ```

   Related answers the question might be seeking
   - If the expected answer is a single word, it is `schema` (or `logical schema`).
   - Some textbooks call the whole activity `logical database design`, whose output is the `relational schema`.
   - The `data model` is the notation used to express it; the `data dictionary` is where the DBMS stores it.

   Distinguishing schema from instance
   - The `schema` is the structure — it changes rarely.
   - The `instance` is the data held at a particular moment — it changes constantly with every insert, update and delete.
   ```
   Schema  : Employee(emp_id, emp_name, salary, dept_id)     -- the definition
   Instance: (101, 'Karim', 50000, 10), (102, 'Rahim', ...)  -- today's rows
   ```

5. **A Bank schema is given below:** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1322 (ET: DU)]*
   $$\text{Bank}(\text{Br\_Name}, \text{Br\_City}, \text{Assets}, \text{Acc\_name}, \text{Acc\_Num}, \text{Balance})$$
   * (a) Provided and Normalize and point out Primary and Foreign Key?
   * (b) Show that is the schema and state that why your schema is in good form.

   Answer: The bank schema was not printed, so the standard bank schema used in these questions is normalised step by step, which is what the question invariably asks.

   The unnormalised table
   ```
   Bank_Record
   +---------+----------+-------------+-------------+------------+---------+-----------+
   | Acc_No  | Cust_ID  | Cust_Name   | Cust_Phone  | Branch_Code| Branch  | Balance   |
   +---------+----------+-------------+-------------+------------+---------+-----------+
   | A101    |  C01     | Karim       | 0171,0182   |   BR10     | Dhanmondi| 50000    |
   | A102    |  C01     | Karim       | 0171,0182   |   BR10     | Dhanmondi| 25000    |
   | A103    |  C02     | Rahim       | 0193        |   BR20     | Uttara   | 70000    |
   +---------+----------+-------------+-------------+------------+---------+-----------+
   ```

   Step 1 — First Normal Form (1NF)
   - `Problem`: `Cust_Phone` holds two values in one cell — not atomic.
   - `Fix`: move the phone numbers into their own table.
   ```
   Customer_Phone
   +----------+-------+
   | Cust_ID  | Phone |
   +----------+-------+
   |   C01    | 0171  |
   |   C01    | 0182  |
   |   C02    | 0193  |
   +----------+-------+
   ```

   Step 2 — Second Normal Form (2NF)
   - 2NF matters only when the primary key is `composite`. If the key here is `Acc_No` alone, the table is already in 2NF.
   - If the key were `(Acc_No, Cust_ID)`, then `Cust_Name` depending on `Cust_ID` alone would be a `partial dependency` and would have to be removed.

   Step 3 — Third Normal Form (3NF)
   - `Problem`: two transitive dependencies.
   ```
   Acc_No -> Cust_ID   -> Cust_Name        (Cust_Name depends on a non-key attribute)
   Acc_No -> Branch_Code -> Branch_Name    (Branch_Name likewise)
   ```
   - `Fix`: separate the customer and the branch into their own tables.

   The normalised schema
   ```sql
   CREATE TABLE Customer (
       Cust_ID   VARCHAR(10) PRIMARY KEY,
       Cust_Name VARCHAR(100) NOT NULL,
       Address   VARCHAR(200)
   );

   CREATE TABLE Customer_Phone (
       Cust_ID VARCHAR(10),
       Phone   VARCHAR(15),
       PRIMARY KEY (Cust_ID, Phone),
       FOREIGN KEY (Cust_ID) REFERENCES Customer(Cust_ID)
   );

   CREATE TABLE Branch (
       Branch_Code VARCHAR(10) PRIMARY KEY,
       Branch_Name VARCHAR(100) NOT NULL,
       City        VARCHAR(50)
   );

   CREATE TABLE Account (
       Acc_No      VARCHAR(20) PRIMARY KEY,
       Acc_Type    VARCHAR(20),
       Balance     DECIMAL(15,2) DEFAULT 0 CHECK (Balance >= 0),
       Branch_Code VARCHAR(10) NOT NULL REFERENCES Branch(Branch_Code)
   );

   CREATE TABLE Acc_Holder (              -- M:N, so joint accounts are possible
       Cust_ID VARCHAR(10),
       Acc_No  VARCHAR(20),
       Since   DATE,
       PRIMARY KEY (Cust_ID, Acc_No),
       FOREIGN KEY (Cust_ID) REFERENCES Customer(Cust_ID),
       FOREIGN KEY (Acc_No)  REFERENCES Account(Acc_No)
   );

   CREATE TABLE Transaction (
       Txn_ID     INT PRIMARY KEY,
       Acc_No     VARCHAR(20) NOT NULL REFERENCES Account(Acc_No),
       Txn_Date   DATETIME NOT NULL,
       Txn_Type   VARCHAR(10) CHECK (Txn_Type IN ('Deposit','Withdrawal')),
       Amount     DECIMAL(15,2) CHECK (Amount > 0)
   );
   ```

   What the normalisation achieved
   - `Karim` and `Dhanmondi` are now each stored `once`, not repeated in every account row.
   - A branch can be created before it has any accounts (insertion anomaly gone).
   - Renaming a branch is one update (update anomaly gone).
   - Closing the last account of a branch does not delete the branch (deletion anomaly gone).
   - `Acc_Holder` as an M:N table additionally makes joint accounts representable, which the original flat table could not do.

   Rejoining when needed
   ```sql
   SELECT c.Cust_Name, a.Acc_No, a.Balance, b.Branch_Name
   FROM   Customer c
   JOIN   Acc_Holder ah ON c.Cust_ID = ah.Cust_ID
   JOIN   Account    a  ON ah.Acc_No = a.Acc_No
   JOIN   Branch     b  ON a.Branch_Code = b.Branch_Code;
   ```
   - The information is not lost by normalisation; it is simply reassembled by a join when it is wanted. <!-- verify -->

6. **What is Normalize a database? Used containers if needed, draw an ER Diagram.** **[See WZPGCL, Assistant Engineer (CSE), Exam: 27.05.2023]** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 315 (ET: N/A)]*

   Answer:

   What normalising a database means
   - `Normalisation` is the process of restructuring tables so that each fact is stored exactly `once`, by decomposing a large table into smaller related tables joined by keys.
   - Its purpose is to remove `redundancy` and the three `anomalies` — insertion, update and deletion.

   Worked example — a container shipping system

   `Unnormalised`
   ```
   Shipment_Record
   +-------------+--------------+-------------+------------+-----------+------------+
   | Shipment_ID | Container_No | Cont_Type   | Cust_ID    | Cust_Name | Port_Name  |
   +-------------+--------------+-------------+------------+-----------+------------+
   |    S001     | C101, C102   | 20ft        |   CU01     | Karim     | Chattogram |
   |    S002     | C103         | 40ft        |   CU01     | Karim     | Mongla     |
   |    S003     | C104, C105   | 20ft        |   CU02     | Rahim     | Chattogram |
   +-------------+--------------+-------------+------------+-----------+------------+
   ```

   `1NF` — Container_No holds several values in one cell, which is not atomic. Split it out.
   ```
   Shipment(Shipment_ID, Cust_ID, Cust_Name, Port_Name)
   Shipment_Container(Shipment_ID, Container_No, Cont_Type)
   ```

   `2NF` — in Shipment_Container the key is (Shipment_ID, Container_No), and `Cont_Type` depends only on Container_No — a partial dependency. Move it to a Container table.
   ```
   Container(Container_No, Cont_Type, Capacity)
   Shipment_Container(Shipment_ID, Container_No)
   ```

   `3NF` — in Shipment, `Cust_Name` depends on Cust_ID, which is not the key. That is a transitive dependency. Separate the customer.
   ```
   Customer(Cust_ID, Cust_Name, Address)
   Port(Port_ID, Port_Name, City)
   Shipment(Shipment_ID, Cust_ID, Port_ID, Ship_Date)
   ```

   Final normalised schema
   ```sql
   CREATE TABLE Customer (
       Cust_ID   VARCHAR(10) PRIMARY KEY,
       Cust_Name VARCHAR(100) NOT NULL,
       Address   VARCHAR(200)
   );

   CREATE TABLE Port (
       Port_ID   INT PRIMARY KEY,
       Port_Name VARCHAR(100) NOT NULL,
       City      VARCHAR(50)
   );

   CREATE TABLE Container (
       Container_No VARCHAR(20) PRIMARY KEY,
       Cont_Type    VARCHAR(20),
       Capacity     DECIMAL(10,2)
   );

   CREATE TABLE Shipment (
       Shipment_ID VARCHAR(20) PRIMARY KEY,
       Cust_ID     VARCHAR(10) NOT NULL REFERENCES Customer(Cust_ID),
       Port_ID     INT NOT NULL REFERENCES Port(Port_ID),
       Ship_Date   DATE
   );

   CREATE TABLE Shipment_Container (
       Shipment_ID  VARCHAR(20),
       Container_No VARCHAR(20),
       PRIMARY KEY (Shipment_ID, Container_No),
       FOREIGN KEY (Shipment_ID)  REFERENCES Shipment(Shipment_ID),
       FOREIGN KEY (Container_No) REFERENCES Container(Container_No)
   );
   ```

   ER diagram for the normalised design
   ```mermaid
   erDiagram
       CUSTOMER  ||--o{ SHIPMENT           : places
       PORT      ||--o{ SHIPMENT           : "is destination of"
       SHIPMENT  ||--o{ SHIPMENT_CONTAINER : carries
       CONTAINER ||--o{ SHIPMENT_CONTAINER : "is carried in"

       CUSTOMER {
           string Cust_ID PK
           string Cust_Name
           string Address
       }
       PORT {
           int Port_ID PK
           string Port_Name
           string City
       }
       SHIPMENT {
           string Shipment_ID PK
           string Cust_ID FK
           int Port_ID FK
           date Ship_Date
       }
       CONTAINER {
           string Container_No PK
           string Cont_Type
           decimal Capacity
       }
       SHIPMENT_CONTAINER {
           string Shipment_ID PK-FK
           string Container_No PK-FK
       }
   ```

   What was achieved
   - Each customer name and container type is stored once.
   - A customer or a container can be registered before any shipment exists.
   - A container type is changed in one place.
   - Deleting a shipment does not destroy the customer or the container record.
   - `Shipment_Container` resolves the M:N relationship — one shipment carries many containers, and a container is reused on many shipments over time.

7. **(ক) Normalization কী? কত প্রকার ও কী কী? ব্যাখ্যা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 415 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   What normalisation is
   - `Normalisation` is the process of organising the tables and columns of a relational database to `minimise redundancy` and eliminate `update anomalies`, by decomposing a large table into smaller related tables connected by keys.
   - Proposed by E. F. Codd. It removes three problems: the `insertion`, `update` and `deletion` anomalies.

   The normal forms

   `1NF — First Normal Form`
   - Rule: every attribute must hold an `atomic` value; no repeating groups; every row unique.
   ```
   Violates 1NF:  Phone = "0171111, 0182222"     <- two values in one cell
   In 1NF      :  a separate Student_Phone(Student_ID, Phone) table
   ```

   `2NF — Second Normal Form`
   - Rule: in 1NF, and `no partial dependency` — every non-key attribute depends on the `whole` primary key. Only relevant when the key is composite.
   ```
   Enrollment(Student_ID, Course_ID, Student_Name, Grade)
      Student_Name depends only on Student_ID   -> partial dependency
   In 2NF: Student(Student_ID, Student_Name) + Enrollment(Student_ID, Course_ID, Grade)
   ```

   `3NF — Third Normal Form`
   - Rule: in 2NF, and `no transitive dependency` — no non-key attribute depends on another non-key attribute.
   ```
   Employee(Emp_ID, Emp_Name, Dept_ID, Dept_Name)
      Emp_ID -> Dept_ID -> Dept_Name             -> transitive dependency
   In 3NF: Employee(Emp_ID, Emp_Name, Dept_ID) + Department(Dept_ID, Dept_Name)
   ```

   `BCNF — Boyce-Codd Normal Form`
   - Rule: for `every` non-trivial functional dependency `X → Y`, X must be a `superkey`. Stricter than 3NF, because 3NF permits a determinant that is not a superkey when the dependent attribute is prime.

   `4NF — Fourth Normal Form`
   - Rule: in BCNF, and no `multivalued dependency`. It removes the redundancy caused by two independent multivalued facts in one table.
   ```
   Student(Student_ID, Language, Hobby)  -- languages and hobbies are independent
   In 4NF: Student_Language(Student_ID, Language) + Student_Hobby(Student_ID, Hobby)
   ```

   `5NF — Fifth Normal Form (Project-Join Normal Form)`
   - Rule: in 4NF, and no `join dependency` that is not implied by the candidate keys. It handles cases that can only be decomposed into three or more tables.

   `6NF` and `DKNF` exist but are of theoretical interest only.

   Summary

   | Normal form | Removes | Concerned with |
   |---|---|---|
   | 1NF | Non-atomic values, repeating groups | Attribute values |
   | 2NF | `Partial` dependency | Composite keys |
   | 3NF | `Transitive` dependency | Non-key attributes |
   | BCNF | Determinants that are not superkeys | Every dependency |
   | 4NF | Multivalued dependency | Independent multivalued facts |
   | 5NF | Join dependency | Decomposition into three or more tables |

   The mnemonic
   > Every non-key attribute must depend on `the key` (1NF), `the whole key` (2NF), and `nothing but the key` (3NF).

   - In practice, `3NF` or `BCNF` is the normal target. Going beyond that is rarely worth the extra joins, and reporting systems often deliberately `denormalise` back towards fewer tables for speed.

8. **What is database Normalization? Write down the types of database Normalization.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 504 (ET: N/A)]*

   Answer:

   What database normalisation is
   - `Normalisation` is the process of organising the tables and columns of a relational database to `reduce redundancy` and eliminate `anomalies`, by decomposing a large table into smaller related tables joined by keys.
   - Introduced by E. F. Codd. Each `normal form` is a stricter condition than the last, and a relation in a higher form automatically satisfies all the lower ones.

   The three anomalies it removes
   - `Insertion anomaly` — a fact cannot be recorded because some unrelated fact is missing. A new department cannot be created until an employee is hired into it.
   - `Update anomaly` — a fact stored in many rows must be changed in all of them; missing one leaves the data inconsistent.
   - `Deletion anomaly` — removing one fact destroys another. Deleting the last employee also deletes the department.

   Types of normalisation

   `1NF` — every value atomic, no repeating groups, every row unique.
   ```
   Bad : Phone = "0171111, 0182222"
   Good: a separate table with one phone number per row
   ```

   `2NF` — in 1NF, plus no `partial dependency` on a composite key.
   ```
   Bad : Enrollment(Student_ID, Course_ID, Student_Name, Grade)
         Student_Name depends on Student_ID alone
   Good: Student(Student_ID, Student_Name) + Enrollment(Student_ID, Course_ID, Grade)
   ```

   `3NF` — in 2NF, plus no `transitive dependency`.
   ```
   Bad : Employee(Emp_ID, Emp_Name, Dept_ID, Dept_Name)
         Emp_ID -> Dept_ID -> Dept_Name
   Good: Employee(Emp_ID, Emp_Name, Dept_ID) + Department(Dept_ID, Dept_Name)
   ```

   `BCNF` — every determinant must be a `superkey`. Stricter than 3NF.

   `4NF` — in BCNF, plus no `multivalued dependency`.

   `5NF (PJNF)` — in 4NF, plus no `join dependency` not implied by the candidate keys.

   Summary table

   | Form | Condition added | Anomaly removed |
   |---|---|---|
   | 1NF | Atomic values | Repeating groups |
   | 2NF | No partial dependency | Redundancy from composite keys |
   | 3NF | No transitive dependency | Redundancy from derived facts |
   | BCNF | Every determinant is a superkey | The remaining 3NF anomalies |
   | 4NF | No multivalued dependency | Independent multivalued facts |
   | 5NF | No join dependency | Redundancy needing 3-way decomposition |

   The cost, and denormalisation
   - Normalisation reduces redundancy but increases the number of `joins` needed to reassemble the data. In read-heavy reporting systems and data warehouses, designers deliberately `denormalise` — reintroducing controlled redundancy — to avoid expensive joins.
   - The rule of thumb: normalise to `3NF or BCNF` for a transactional system, then denormalise selectively and deliberately where measurement shows it is needed.

9. **Which normalization is related to functional dependency?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

   Answer: The normal forms `directly based on functional dependency` are `2NF`, `3NF` and `BCNF`.

   Why
   - A `functional dependency` `X → Y` means that the value of X determines the value of Y: any two rows agreeing on X must agree on Y.
   - Each of these three normal forms is defined by restricting what kinds of functional dependency are allowed to exist.

   | Normal form | The functional dependency it forbids |
   |---|---|
   | `1NF` | None — it concerns atomic values, not dependencies |
   | `2NF` | `Partial` dependency: a non-key attribute determined by `part` of a composite key |
   | `3NF` | `Transitive` dependency: a non-key attribute determined by another non-key attribute |
   | `BCNF` | Any dependency `X → Y` where X is `not a superkey` |
   | `4NF` | Based on `multivalued` dependency, a generalisation of FD |
   | `5NF` | Based on `join` dependency |

   The definitions in terms of FDs
   - `2NF` — no non-prime attribute is partially dependent on any candidate key.
   - `3NF` — for every non-trivial FD `X → Y`, either X is a superkey `or` Y is a prime attribute.
   - `BCNF` — for every non-trivial FD `X → Y`, X `must` be a superkey. The 3NF escape clause is removed, which is exactly why BCNF is stricter.

   Examples
   ```
   Partial dependency (violates 2NF)
      Enrollment(Student_ID, Course_ID, Student_Name)
      Student_ID -> Student_Name      -- part of the key determines a non-key attribute

   Transitive dependency (violates 3NF)
      Employee(Emp_ID, Dept_ID, Dept_Name)
      Emp_ID -> Dept_ID -> Dept_Name  -- a non-key attribute determines another

   Non-superkey determinant (violates BCNF but satisfies 3NF)
      Student_Course_Teacher(Student, Course, Teacher)
      (Student, Course) -> Teacher    -- fine
      Teacher -> Course               -- Teacher is not a superkey, so BCNF fails,
                                         but Course is prime, so 3NF is satisfied
   ```

   The answer in one line
   - If the question expects a single normal form, the usual intended answer is `3NF`, since it is the form most often described as "based on functional dependency". Strictly, `2NF, 3NF and BCNF` are all defined by functional dependencies, while `1NF` is not, and `4NF` and `5NF` rest on the generalisations of the idea.

10. **Functional dependency use in which normalizations?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

    Answer: Functional dependency is used in `2NF`, `3NF` and `BCNF`.

    What a functional dependency is
    - `X → Y` means the value of X `determines` the value of Y: any two rows that agree on X must agree on Y.
    - X is the `determinant`, Y is the `dependent`.
    ```
    Student_ID -> Student_Name        one ID gives exactly one name
    (Student_ID, Course_ID) -> Grade  the pair gives exactly one grade
    ```

    Types of functional dependency

    | Type | Definition | Example |
    |---|---|---|
    | `Trivial` | Y is a subset of X | (A, B) → A |
    | `Non-trivial` | Y is not a subset of X | Student_ID → Name |
    | `Fully functional` | Y depends on the whole of X, not part | (Student_ID, Course_ID) → Grade |
    | `Partial` | Y depends on part of a composite X | (Student_ID, Course_ID) → Student_Name |
    | `Transitive` | X → Y and Y → Z, so X → Z indirectly | Emp_ID → Dept_ID → Dept_Name |
    | `Multivalued` | X determines a `set` of Y values | Student ↠ Language |

    Where each normal form uses them

    `2NF` — forbids `partial` dependency
    ```
    Enrollment(Student_ID, Course_ID, Student_Name, Grade)
       Student_ID -> Student_Name      PARTIAL, so 2NF is violated
    Fix: Student(Student_ID, Student_Name) + Enrollment(Student_ID, Course_ID, Grade)
    ```

    `3NF` — forbids `transitive` dependency
    ```
    Employee(Emp_ID, Emp_Name, Dept_ID, Dept_Name)
       Emp_ID -> Dept_ID -> Dept_Name  TRANSITIVE, so 3NF is violated
    Fix: Employee(Emp_ID, Emp_Name, Dept_ID) + Department(Dept_ID, Dept_Name)
    ```

    `BCNF` — requires every determinant to be a `superkey`
    ```
    For every non-trivial FD  X -> Y,  X must be a superkey.
    ```

    `4NF` and `5NF` use the generalisations — multivalued dependency and join dependency.

    Armstrong's axioms, used to reason about FDs
    - `Reflexivity` — if Y ⊆ X then X → Y.
    - `Augmentation` — if X → Y then XZ → YZ.
    - `Transitivity` — if X → Y and Y → Z then X → Z.
    - Derived rules: union, decomposition and pseudo-transitivity.

    Why FDs matter in practice
    - They are how `candidate keys` are found: X is a candidate key when its closure `X⁺` contains every attribute and no proper subset of X does.
    - They are how a designer decides `where to split` a table. Every normalisation step is really the statement "this dependency does not belong here", followed by moving it to a table where its determinant `is` the key.

11. **What in First and Second Normal form is DBMS?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*

    Answer:

    First Normal Form (1NF)
    - Rule: every attribute must contain an `atomic` (indivisible) value; there must be `no repeating groups`; each row must be unique; and each column must have a unique name and hold values of a single type.

    `Violating 1NF`
    ```
    Student
    +------------+-------+---------------------+---------------+
    | Student_ID | Name  | Phone               | Courses       |
    +------------+-------+---------------------+---------------+
    |    101     | Karim | 01711111, 01822222  | CS101, CS102  |   <- multiple values
    |    102     | Rahim | 01933333            | CS101         |
    +------------+-------+---------------------+---------------+
    ```

    `In 1NF`
    ```
    Student                    Student_Phone                Student_Course
    +------------+-------+     +------------+----------+    +------------+-----------+
    | Student_ID | Name  |     | Student_ID | Phone    |    | Student_ID | Course_ID |
    +------------+-------+     +------------+----------+    +------------+-----------+
    |    101     | Karim |     |    101     | 01711111 |    |    101     |  CS101    |
    |    102     | Rahim |     |    101     | 01822222 |    |    101     |  CS102    |
    +------------+-------+     |    102     | 01933333 |    |    102     |  CS101    |
                               +------------+----------+    +------------+-----------+
    ```
    - Note that adding `Phone1` and `Phone2` columns instead would `also` violate 1NF: it is a repeating group, it fixes an arbitrary maximum of two, and querying "who has number X" becomes awkward.

    Second Normal Form (2NF)
    - Rule: the table must be in 1NF, and every `non-key attribute` must be `fully functionally dependent` on the whole primary key — no `partial dependency`.
    - This can only be violated when the primary key is `composite`. A table whose key is a single column is automatically in 2NF once it is in 1NF.

    `Violating 2NF` — primary key (Student_ID, Course_ID)
    ```
    +------------+-----------+--------------+-------------+-------+
    | Student_ID | Course_ID | Student_Name | Course_Name | Grade |
    +------------+-----------+--------------+-------------+-------+
    |    101     |   CS101   | Karim        | Database    |   A   |
    |    101     |   CS102   | Karim        | Networking  |   B   |
    |    102     |   CS101   | Rahim        | Database    |   A   |
    +------------+-----------+--------------+-------------+-------+

    Functional dependencies:
       Student_ID              -> Student_Name    PARTIAL
       Course_ID               -> Course_Name     PARTIAL
       (Student_ID, Course_ID) -> Grade           FULL, correct
    ```
    - The redundancy is visible: "Karim" appears twice and "Database" appears twice. Renaming a course means updating several rows.

    `In 2NF`
    ```
    Student(Student_ID, Student_Name)
    Course(Course_ID, Course_Name)
    Enrollment(Student_ID, Course_ID, Grade)
    ```
    ```sql
    CREATE TABLE Enrollment (
        Student_ID INT,
        Course_ID  VARCHAR(10),
        Grade      CHAR(2),
        PRIMARY KEY (Student_ID, Course_ID),
        FOREIGN KEY (Student_ID) REFERENCES Student(Student_ID),
        FOREIGN KEY (Course_ID)  REFERENCES Course(Course_ID)
    );
    ```

    Comparison

    | Point | 1NF | 2NF |
    |---|---|---|
    | Concerns | The `values` in a column | The `dependencies` on the key |
    | Removes | Non-atomic values, repeating groups | Partial dependencies |
    | Prerequisite | None | Must already be in 1NF |
    | Arises when | Any table | The primary key is composite |

    - The next step, `3NF`, removes `transitive dependency` — a non-key attribute depending on another non-key attribute.

12. **অথবা, (ক) “BCNF is stricter than 3NF” এই উক্তিটি উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 626 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The statement is correct: `every relation in BCNF is in 3NF, but not every relation in 3NF is in BCNF`.

    The two definitions, side by side
    - `3NF` — for every non-trivial functional dependency `X → Y`, either
      - X is a `superkey`, `OR`
      - Y is a `prime attribute` (part of some candidate key).
    - `BCNF` — for every non-trivial functional dependency `X → Y`,
      - X `must` be a `superkey`. Full stop.

    BCNF simply removes the second escape clause, which is exactly why it is stricter.

    The counter-example — a relation in 3NF but not in BCNF
    ```
    Student_Course_Teacher (Student, Course, Teacher)

    Business rules:
       1. A student takes a course from exactly one teacher.
       2. Each teacher teaches exactly one course.

    Functional dependencies:
       (Student, Course) -> Teacher
       Teacher           -> Course
    ```
    ```
    +---------+---------+----------+
    | Student | Course  | Teacher  |
    +---------+---------+----------+
    | Karim   | DBMS    | Dr. Ali  |
    | Karim   | Network | Dr. Bilal|
    | Rahim   | DBMS    | Dr. Ali  |
    | Sumi    | DBMS    | Dr. Chan |
    +---------+---------+----------+
    ```

    Is it in 3NF? — `Yes`
    - Candidate keys: `(Student, Course)` and `(Student, Teacher)`.
    - Prime attributes are therefore Student, Course and Teacher — all of them.
    - Check `Teacher → Course`: Teacher is not a superkey, so the first condition fails. But `Course` is a `prime attribute`, so the second condition is satisfied. `3NF holds`.

    Is it in BCNF? — `No`
    - Check `Teacher → Course`: Teacher is `not` a superkey, and BCNF offers no escape clause. `BCNF is violated`.

    The anomaly this permits
    - The fact "Dr. Ali teaches DBMS" is stored in `every row` in which Dr. Ali appears — redundancy that 3NF failed to eliminate.
    - `Insertion anomaly`: a new teacher's subject cannot be recorded until some student is assigned to them.
    - `Deletion anomaly`: if Sumi withdraws, the fact that Dr. Chan teaches DBMS is lost entirely.

    Decomposing into BCNF
    ```
    Teacher_Course(Teacher, Course)          -- key: Teacher
    Student_Teacher(Student, Teacher)        -- key: (Student, Teacher)
    ```
    ```
    Teacher_Course              Student_Teacher
    +----------+---------+      +---------+----------+
    | Teacher  | Course  |      | Student | Teacher  |
    +----------+---------+      +---------+----------+
    | Dr. Ali  | DBMS    |      | Karim   | Dr. Ali  |
    | Dr. Bilal| Network |      | Karim   | Dr. Bilal|
    | Dr. Chan | DBMS    |      | Rahim   | Dr. Ali  |
    +----------+---------+      | Sumi    | Dr. Chan |
                                +---------+----------+
    ```
    - Each teacher's subject is now stored once, and both anomalies disappear.

    The price of BCNF — this is the important second half of the answer
    - The decomposition is `lossless`, but it is `not dependency-preserving`. The original dependency `(Student, Course) → Teacher` spans both new tables, so it can no longer be enforced by a constraint within either one; checking it would require a join.
    - This is a general result: `every relation can be decomposed into 3NF with both lossless join and dependency preservation, but a BCNF decomposition cannot always preserve all dependencies`.

    Comparison

    | Point | 3NF | BCNF |
    |---|---|---|
    | Condition | X is a superkey `or` Y is prime | X `must` be a superkey |
    | Strictness | Less strict | `Stricter` |
    | Redundancy remaining | Some, involving prime attributes | None from functional dependencies |
    | Lossless decomposition | Always achievable | Always achievable |
    | Dependency preservation | `Always` achievable | `Not always` achievable |
    | Practical choice | The usual target | Used when the residual anomaly matters |

    - The practical conclusion: designers normally aim for `3NF`, and go to `BCNF` only when the leftover redundancy causes real problems — accepting that some constraint will then have to be enforced by the application rather than by the schema.

13. **Why Normalization is used in database? Explain 1^{\text{st}} Normal form using an example.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 665 (ET: N/A)]*

    Answer:

    Why normalisation is used

    1. `To eliminate redundancy` — each fact stored once instead of repeated in many rows.
    2. `To prevent the insertion anomaly` — a new department should be recordable before anyone is hired into it.
    3. `To prevent the update anomaly` — a name changed in one place rather than in fifty rows, so the copies cannot disagree.
    4. `To prevent the deletion anomaly` — deleting the last employee should not destroy the department.
    5. `To maintain data consistency and integrity`.
    6. `To save storage` and reduce the volume written on every update.
    7. `To make the schema flexible`, so new attributes and entities can be added without restructuring.
    8. `To produce a clear logical design` that mirrors the real relationships in the data.

    First Normal Form, with an example

    - Rule: every attribute must hold an `atomic` (indivisible) value; there must be no `repeating groups`; every row must be unique; and each column must have a unique name and hold a single type of value.

    `Violating 1NF`
    ```
    Employee
    +--------+----------+---------------------------+--------------------+
    | Emp_ID | Emp_Name | Phone                     | Skills             |
    +--------+----------+---------------------------+--------------------+
    |  101   | Karim    | 01711111, 01822222        | Java, SQL, Python  |
    |  102   | Rahim    | 01933333                  | C++, SQL           |
    |  103   | Sumi     | 01944444, 01955555        | Java               |
    +--------+----------+---------------------------+--------------------+
    ```
    Why this is a problem
    - "Which employees know SQL?" cannot be answered by a simple equality test; it needs unreliable string searching.
    - Adding a third phone number means editing a text field, and there is no way to stop rubbish being entered.
    - Sorting, indexing and joining on these columns is impossible.

    `Converting to 1NF` — give each value its own row in its own table
    ```
    Employee                      Employee_Phone                Employee_Skill
    +--------+----------+         +--------+----------+         +--------+--------+
    | Emp_ID | Emp_Name |         | Emp_ID | Phone    |         | Emp_ID | Skill  |
    +--------+----------+         +--------+----------+         +--------+--------+
    |  101   | Karim    |         |  101   | 01711111 |         |  101   | Java   |
    |  102   | Rahim    |         |  101   | 01822222 |         |  101   | SQL    |
    |  103   | Sumi     |         |  102   | 01933333 |         |  101   | Python |
    +--------+----------+         |  103   | 01944444 |         |  102   | C++    |
                                  |  103   | 01955555 |         |  102   | SQL    |
                                  +--------+----------+         |  103   | Java   |
                                                                +--------+--------+
    ```

    ```sql
    CREATE TABLE Employee_Skill (
        Emp_ID INT,
        Skill  VARCHAR(50),
        PRIMARY KEY (Emp_ID, Skill),
        FOREIGN KEY (Emp_ID) REFERENCES Employee(Emp_ID)
    );
    ```

    Now the query is trivial
    ```sql
    SELECT e.Emp_Name FROM Employee e
    JOIN   Employee_Skill s ON e.Emp_ID = s.Emp_ID
    WHERE  s.Skill = 'SQL';
    ```

    The wrong "fix" to avoid
    ```
    +--------+----------+---------+---------+---------+
    | Emp_ID | Emp_Name | Skill_1 | Skill_2 | Skill_3 |
    +--------+----------+---------+---------+---------+
    ```
    - This also violates 1NF. It is a `repeating group`, it caps the number of skills at three, most cells are NULL, and searching for a skill means testing three columns with OR.

    - The next step is `2NF`, which removes partial dependency on a composite key.

14. **Why do you need database Normalization?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*

    Answer: Normalisation is needed because an unnormalised table stores the same fact many times, and that redundancy causes three specific failures.

    1. `To eliminate data redundancy`
    - Without it, the same value is repeated in every row that mentions it. A department name stored beside each employee is written once per employee — wasted space, and worse, the copies can drift apart.

    2. `To prevent the insertion anomaly`
    ```
    Employee(Emp_ID, Emp_Name, Dept_ID, Dept_Name)
    ```
    - A newly created department cannot be recorded until somebody is hired into it, because there is no row to put it in.

    3. `To prevent the update anomaly`
    - If a department is renamed, `every` employee row must be updated. Missing one leaves two contradictory department names in the same table, and no way to tell which is correct.

    4. `To prevent the deletion anomaly`
    - Deleting the last employee of a department deletes the department itself. Information that should have survived is lost as a side effect.

    5. `To maintain consistency and integrity`
    - When a fact exists in exactly one place, it cannot contradict itself.

    6. `To save storage and reduce write volume`
    - Repeating a long text value in a million rows costs space and makes every update larger.

    7. `To make the design flexible`
    - New attributes and entities can be added without restructuring existing tables.

    8. `To produce a logical structure that reflects reality`
    - Each table describes one kind of thing, which makes the schema easier to understand and to query correctly.

    Illustration of all three anomalies in one table
    ```
    Employee
    +--------+----------+---------+-------------+
    | Emp_ID | Emp_Name | Dept_ID | Dept_Name   |
    +--------+----------+---------+-------------+
    |  101   | Karim    |   10    | IT          |
    |  102   | Rahim    |   10    | IT          |
    |  103   | Sumi     |   20    | HR          |
    +--------+----------+---------+-------------+

    INSERT : a new Finance department cannot be added — no employee yet
    UPDATE : renaming "IT" requires changing rows 101 and 102 together
    DELETE : removing Sumi destroys all record of the HR department
    ```

    After normalising to 3NF
    ```
    Employee                          Department
    +--------+----------+---------+   +---------+-------------+
    | Emp_ID | Emp_Name | Dept_ID |   | Dept_ID | Dept_Name   |
    +--------+----------+---------+   +---------+-------------+
    |  101   | Karim    |   10    |   |   10    | IT          |
    |  102   | Rahim    |   10    |   |   20    | HR          |
    |  103   | Sumi     |   20    |   |   30    | Finance     |  <- can now exist alone
    +--------+----------+---------+   +---------+-------------+
    ```
    - All three anomalies are gone: Finance exists with no employees, renaming IT is one update, and deleting Sumi leaves HR intact.

    The cost, stated honestly
    - Normalisation increases the number of `joins` needed to reassemble the data, which costs query time. For read-heavy reporting and data warehouses, designers deliberately `denormalise` to avoid those joins. The usual rule is: normalise to 3NF or BCNF for a transactional system, then denormalise selectively where measurement proves it is needed.

15. **Let a relational function is R(A, B, C, D, E), Write Yes or No based on those are the follow n functional dependency.** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 822 (ET: BUET)]*
   AB \to C
   B \to B
   DE \to A

    Answer: The list of dependencies was not printed, so the `method` for deciding whether a functional dependency holds is given, applied to `R(A, B, C, D, E)`.

    What a functional dependency means
    - `X → Y` holds if, in every legal instance of the relation, any two tuples that agree on X `must` agree on Y.
    - To test a claimed dependency, compute the `closure` of X under the given FD set. `X → Y` holds if and only if `Y ⊆ X⁺`.

    The closure algorithm
    ```
    X+ = X
    repeat:
        for each FD  P -> Q  in F:
            if P is a subset of X+ then X+ = X+ ∪ Q
    until X+ stops changing
    ```

    Worked example
    ```
    R(A, B, C, D, E)
    F = { A -> B,  BC -> D,  D -> E,  AC -> E }
    ```

    Test each claimed dependency

    `1. A → B ?`
    ```
    A+ = {A}
       A -> B  gives {A, B}
       no other FD applies
    A+ = {A, B}     B ⊆ A+   ->  YES
    ```

    `2. A → D ?`
    ```
    A+ = {A, B}
       BC -> D needs both B and C; C is not in A+, so it does not apply
    A+ = {A, B}     D ∉ A+   ->  NO
    ```

    `3. AC → D ?`
    ```
    AC+ = {A, C}
       A -> B   gives {A, B, C}
       BC -> D  gives {A, B, C, D}
       D -> E   gives {A, B, C, D, E}
    AC+ = {A,B,C,D,E}     D ⊆ AC+   ->  YES
    ```

    `4. AC → E ?`
    ```
    AC+ = {A,B,C,D,E}     E ⊆ AC+   ->  YES
    ```

    `5. BC → E ?`
    ```
    BC+ = {B, C}
       BC -> D  gives {B, C, D}
       D  -> E  gives {B, C, D, E}
    BC+ = {B,C,D,E}       E ⊆ BC+   ->  YES
    ```

    `6. D → A ?`
    ```
    D+ = {D}
       D -> E gives {D, E}
       no FD has D or DE on its left producing A
    D+ = {D, E}           A ∉ D+   ->  NO
    ```

    `7. AB → C ?`
    ```
    AB+ = {A, B}
       A -> B adds nothing new
    AB+ = {A, B}          C ∉ AB+  ->  NO
    ```

    Summary

    | Claimed FD | Closure | Holds? |
    |---|---|---|
    | A → B | A⁺ = {A,B} | `Yes` |
    | A → D | A⁺ = {A,B} | `No` |
    | AC → D | AC⁺ = {A,B,C,D,E} | `Yes` |
    | AC → E | AC⁺ = {A,B,C,D,E} | `Yes` |
    | BC → E | BC⁺ = {B,C,D,E} | `Yes` |
    | D → A | D⁺ = {D,E} | `No` |
    | AB → C | AB⁺ = {A,B} | `No` |

    Finding the candidate key with the same tool
    ```
    AC+ = {A,B,C,D,E} = R, and neither A+ nor C+ covers R
       -> {A, C} is a candidate key
    ```

    Armstrong's axioms, useful as shortcuts
    - `Reflexivity` — if Y ⊆ X then X → Y (a trivial dependency, always true).
    - `Augmentation` — if X → Y then XZ → YZ.
    - `Transitivity` — if X → Y and Y → Z then X → Z.
    - Derived: union, decomposition, pseudo-transitivity.
    - Attributes appearing only on the `right` of every FD can never be part of a candidate key; attributes appearing on `neither` side must be in `every` candidate key. <!-- verify -->

16. **What is DBMS? Write down the purpose of normalization in DBMS.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*

    Answer:

    What is a DBMS
    - A `Database Management System` is software that lets users create, store, retrieve, update and manage data in a database while controlling access to it.
    - It sits between the user or application and the physical data files, so users work with tables and queries rather than with storage.
    - Its functions: data definition, data manipulation, security, integrity, concurrency control, transaction management with ACID guarantees, backup and recovery, and metadata management.
    - Examples: MySQL, PostgreSQL, Oracle, SQL Server, SQLite.

    Purpose of normalisation in a DBMS

    1. `Eliminate data redundancy`
    - Each fact is stored exactly once instead of being repeated in every row that mentions it.

    2. `Remove the insertion anomaly`
    - A new department, course or product can be recorded before any dependent record exists.

    3. `Remove the update anomaly`
    - A value changed in one place cannot leave stale copies elsewhere to contradict it.

    4. `Remove the deletion anomaly`
    - Deleting one fact does not accidentally destroy another that happened to share the row.

    5. `Ensure data consistency and integrity`
    - A single stored copy cannot disagree with itself.

    6. `Save storage space` and reduce the volume written on every update.

    7. `Make the schema flexible and extensible`
    - New attributes and entities can be added without restructuring existing tables.

    8. `Produce a clear logical design`
    - Each table describes one kind of thing, which makes the schema easier to understand and to query correctly.

    9. `Support efficient indexing`
    - Smaller, focused tables index better and their indexes are more selective.

    Illustration
    ```
    BEFORE (unnormalised)
    Employee(Emp_ID, Emp_Name, Dept_ID, Dept_Name)
       "IT" repeated for every IT employee
       INSERT : cannot create a department with no employees
       UPDATE : renaming IT means changing many rows
       DELETE : removing the last employee erases the department

    AFTER (3NF)
    Employee(Emp_ID, Emp_Name, Dept_ID)
    Department(Dept_ID, Dept_Name)
       each department name stored once; all three anomalies gone
    ```

    The trade-off, stated honestly
    - Normalisation increases the number of `joins` required to reassemble the data. For a transactional system the correctness is worth it; for a read-heavy reporting system or data warehouse, deliberate `denormalisation` is often chosen instead, accepting controlled redundancy for speed.
    - The usual rule: normalise to `3NF or BCNF`, then denormalise selectively where measurement shows a real need.

17. **(b) What is normalization? Why is it needed?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 895 (ET: N/A)]*

    Answer:

    What normalisation is
    - `Normalisation` is the process of organising the tables and columns of a relational database so that each fact is stored exactly `once`, by decomposing a large table into smaller related tables joined by keys.
    - Proposed by E. F. Codd. It proceeds through a series of `normal forms` — 1NF, 2NF, 3NF, BCNF, 4NF, 5NF — each stricter than the last.

    The normal forms in brief

    | Form | Condition | Removes |
    |---|---|---|
    | `1NF` | Every value atomic; no repeating groups | Multi-valued cells |
    | `2NF` | 1NF + no partial dependency | Dependence on part of a composite key |
    | `3NF` | 2NF + no transitive dependency | Dependence on a non-key attribute |
    | `BCNF` | Every determinant is a superkey | Residual 3NF anomalies |
    | `4NF` | BCNF + no multivalued dependency | Independent multivalued facts |
    | `5NF` | 4NF + no join dependency | Redundancy needing 3-way decomposition |

    Why it is needed

    1. `To eliminate redundancy` — the same value is not repeated in every row that mentions it.

    2. `To remove the insertion anomaly`
    ```
    Employee(Emp_ID, Emp_Name, Dept_ID, Dept_Name)
    ```
    - A new Finance department cannot be recorded until somebody is hired into it.

    3. `To remove the update anomaly`
    - Renaming a department means updating every row that names it. Missing one leaves two contradictory values in the same column.

    4. `To remove the deletion anomaly`
    - Deleting the last employee of a department destroys the record of the department.

    5. `To maintain integrity and consistency` — a fact stored once cannot disagree with itself.

    6. `To save storage` and reduce the volume written on each update.

    7. `To make the design flexible` — attributes and entities can be added without restructuring.

    Worked illustration
    ```
    BEFORE
    +--------+----------+---------+-------------+
    | Emp_ID | Emp_Name | Dept_ID | Dept_Name   |
    +--------+----------+---------+-------------+
    |  101   | Karim    |   10    | IT          |
    |  102   | Rahim    |   10    | IT          |     <- "IT" stored twice
    |  103   | Sumi     |   20    | HR          |
    +--------+----------+---------+-------------+
       Emp_ID -> Dept_ID -> Dept_Name    (transitive dependency)

    AFTER (3NF)
    Employee                         Department
    +--------+----------+---------+  +---------+-------------+
    | Emp_ID | Emp_Name | Dept_ID |  | Dept_ID | Dept_Name   |
    +--------+----------+---------+  +---------+-------------+
    |  101   | Karim    |   10    |  |   10    | IT          |
    |  102   | Rahim    |   10    |  |   20    | HR          |
    |  103   | Sumi     |   20    |  |   30    | Finance     |
    +--------+----------+---------+  +---------+-------------+
    ```

    The cost
    - More tables means more `joins`. Normalisation trades query speed for correctness, which is the right trade for a transactional system. Reporting systems and data warehouses often `denormalise` deliberately, and that is a considered decision rather than a design failure.

18. **(i) DBMS কী? একটি Database কে normalize করার পদ্ধতিগুলো বর্ণনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 953-954 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    What is a DBMS
    - A `Database Management System` is software that lets users define, create, store, retrieve, update and manage data in a database while controlling access to it.
    - Functions: data definition, data manipulation, security, integrity, concurrency control, transactions with ACID guarantees, backup and recovery, and metadata management.
    - Examples: MySQL, PostgreSQL, Oracle, SQL Server, MongoDB.

    The procedure for normalising a database

    `Step 0 — start from the unnormalised relation`
    ```
    Student_Record
    +------------+-------+---------------+-----------+-------------+---------+--------------+
    | Student_ID | Name  | Phone         | Course_ID | Course_Name | Dept_ID | Dept_Name    |
    +------------+-------+---------------+-----------+-------------+---------+--------------+
    |    101     | Karim | 0171, 0182    | CS101     | Database    |   10    | CSE          |
    |    101     | Karim | 0171, 0182    | CS102     | Networking  |   10    | CSE          |
    |    102     | Rahim | 0193          | CS101     | Database    |   20    | EEE          |
    +------------+-------+---------------+-----------+-------------+---------+--------------+
    ```

    `Step 1 — First Normal Form: make every value atomic`
    - Problem: `Phone` holds two values in one cell.
    - Fix: move phone numbers to their own table, one per row.
    ```
    Student_Phone(Student_ID, Phone)
    ```

    `Step 2 — Second Normal Form: remove partial dependencies`
    - The key of the main table is `(Student_ID, Course_ID)`.
    ```
    Student_ID -> Name, Dept_ID, Dept_Name    depends on PART of the key -> partial
    Course_ID  -> Course_Name                 depends on PART of the key -> partial
    ```
    - Fix: split so each attribute sits with the key it truly depends on.
    ```
    Student(Student_ID, Name, Dept_ID, Dept_Name)
    Course(Course_ID, Course_Name)
    Enrollment(Student_ID, Course_ID, Grade)
    ```

    `Step 3 — Third Normal Form: remove transitive dependencies`
    - In Student, `Student_ID → Dept_ID → Dept_Name`; Dept_Name depends on a non-key attribute.
    - Fix: separate the department.
    ```
    Student(Student_ID, Name, Dept_ID)
    Department(Dept_ID, Dept_Name)
    ```

    `Step 4 — BCNF: check that every determinant is a superkey`
    - For each remaining functional dependency `X → Y`, verify that X is a superkey. If not, decompose further.

    `Step 5 — 4NF and 5NF, if required`
    - Remove any `multivalued dependency` (two independent multivalued facts in one table), then any `join dependency`. These are rarely needed in practice.

    `Step 6 — verify the decomposition`
    - Check it is `lossless` — rejoining the pieces must reproduce the original rows exactly, which is guaranteed when the common attribute is a superkey of at least one fragment.
    - Check `dependency preservation` where possible, so constraints can still be enforced without a join.

    The final schema
    ```sql
    CREATE TABLE Department (
        Dept_ID   INT PRIMARY KEY,
        Dept_Name VARCHAR(50) NOT NULL
    );

    CREATE TABLE Student (
        Student_ID INT PRIMARY KEY,
        Name       VARCHAR(100) NOT NULL,
        Dept_ID    INT REFERENCES Department(Dept_ID)
    );

    CREATE TABLE Student_Phone (
        Student_ID INT,
        Phone      VARCHAR(15),
        PRIMARY KEY (Student_ID, Phone),
        FOREIGN KEY (Student_ID) REFERENCES Student(Student_ID)
    );

    CREATE TABLE Course (
        Course_ID   VARCHAR(10) PRIMARY KEY,
        Course_Name VARCHAR(100) NOT NULL
    );

    CREATE TABLE Enrollment (
        Student_ID INT,
        Course_ID  VARCHAR(10),
        Grade      CHAR(2),
        PRIMARY KEY (Student_ID, Course_ID),
        FOREIGN KEY (Student_ID) REFERENCES Student(Student_ID),
        FOREIGN KEY (Course_ID)  REFERENCES Course(Course_ID)
    );
    ```
    - The mnemonic that summarises steps 1 to 3: every non-key attribute must depend on `the key, the whole key, and nothing but the key`.

19. **What is normalization? Explain composite key with example.** *[Bangladesh Television Assistant Programmer 2019 compact it 1063 (ET: N/A)]*

    Answer:

    What normalisation is
    - `Normalisation` is the process of organising the tables and columns of a relational database to `reduce redundancy` and eliminate the `insertion, update and deletion anomalies`, by decomposing a large table into smaller related tables joined by keys.
    - Proposed by E. F. Codd. The normal forms are 1NF, 2NF, 3NF, BCNF, 4NF and 5NF, each stricter than the last.
    - The mnemonic: every non-key attribute must depend on `the key` (1NF), `the whole key` (2NF), and `nothing but the key` (3NF).

    Composite key, with an example
    - A `composite key` is a primary key made of `two or more attributes`, used when no single attribute is unique on its own but a combination is. Also called a compound key.
    - The rules are those of any primary key: the `combination` must be unique, and `none` of its columns may be NULL.

    Example
    ```
    Enrollment
    +------------+-----------+-------+
    | Student_ID | Course_ID | Grade |
    +------------+-----------+-------+
    |    101     |   CS101   |   A   |
    |    101     |   CS102   |   B   |   <- same student, different course
    |    102     |   CS101   |   A   |   <- same course, different student
    |    102     |   CS102   |   C   |
    +------------+-----------+-------+

    Student_ID alone : 101 repeats   -> not unique
    Course_ID  alone : CS101 repeats -> not unique
    {Student_ID, Course_ID}          -> every pair distinct -> COMPOSITE KEY
    ```

    ```sql
    CREATE TABLE Enrollment (
        Student_ID INT,
        Course_ID  VARCHAR(10),
        Grade      CHAR(2),
        PRIMARY KEY (Student_ID, Course_ID),        -- composite key
        FOREIGN KEY (Student_ID) REFERENCES Student(Student_ID),
        FOREIGN KEY (Course_ID)  REFERENCES Course(Course_ID)
    );
    ```

    Where composite keys occur
    - `Junction tables` implementing an M:N relationship — the commonest case, as above.
    - `Weak entities` — the owner's key plus a partial key, for example `Dependent(Emp_ID, Dep_Name)`.
    - Natural keys needing several attributes, such as `(Roll_No, Session, Department)`.

    The connection with normalisation
    - Composite keys are precisely where `2NF` becomes relevant. A table with a single-column key is automatically in 2NF; only a composite key can suffer a `partial dependency`.
    ```
    Bad (violates 2NF):
       Enrollment(Student_ID, Course_ID, Student_Name, Grade)
       Student_Name depends on Student_ID alone -> partial dependency

    Good (2NF):
       Student(Student_ID, Student_Name)
       Enrollment(Student_ID, Course_ID, Grade)
    ```

    The practical trade-off
    - A composite key makes every referencing foreign key wider and every join more expensive. Many designers therefore add a `surrogate key` and keep the composite as a UNIQUE constraint:
    ```sql
    CREATE TABLE Enrollment (
        Enrollment_ID INT PRIMARY KEY AUTO_INCREMENT,   -- surrogate key
        Student_ID    INT NOT NULL,
        Course_ID     VARCHAR(10) NOT NULL,
        Grade         CHAR(2),
        UNIQUE (Student_ID, Course_ID)                  -- the real business rule
    );
    ```
    - Both designs are correct; the surrogate version simply makes referencing this table from elsewhere simpler.

20. **(a) What do you mean by Normalization in RDBMS? Explain with an example.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1143 (ET: N/A)]*

    Answer:

    What normalisation means in an RDBMS
    - `Normalisation` is the process of organising the tables and columns of a relational database so that each fact is stored exactly `once`, by decomposing a large table into smaller related tables joined by keys.
    - Its object is to remove `redundancy` and the three `anomalies`: insertion, update and deletion.
    - Proposed by E. F. Codd. It proceeds through a sequence of `normal forms`, each stricter than the last.

    Worked example, step by step

    `Step 0 — the unnormalised table`
    ```
    Student_Record
    +------------+-------+---------------+-----------+-------------+---------+-----------+
    | Student_ID | Name  | Phone         | Course_ID | Course_Name | Dept_ID | Dept_Name |
    +------------+-------+---------------+-----------+-------------+---------+-----------+
    |    101     | Karim | 0171, 0182    | CS101     | Database    |   10    | CSE       |
    |    101     | Karim | 0171, 0182    | CS102     | Networking  |   10    | CSE       |
    |    102     | Rahim | 0193          | CS101     | Database    |   20    | EEE       |
    +------------+-------+---------------+-----------+-------------+---------+-----------+
    ```
    The problems visible in this one table
    - `Phone` holds two values in one cell.
    - "Karim", "Database" and "CSE" are each repeated.
    - A new course cannot be created until a student enrols (`insertion anomaly`).
    - Renaming "Database" means editing several rows (`update anomaly`).
    - Deleting Rahim's only enrolment loses the EEE department (`deletion anomaly`).

    `Step 1 — 1NF: atomic values`
    ```
    Student(Student_ID, Name, Dept_ID, Dept_Name)
    Student_Phone(Student_ID, Phone)
    Enrollment(Student_ID, Course_ID, Course_Name)
    ```

    `Step 2 — 2NF: remove partial dependency`
    - In Enrollment the key is `(Student_ID, Course_ID)`, and `Course_Name` depends on `Course_ID` alone.
    ```
    Course(Course_ID, Course_Name)
    Enrollment(Student_ID, Course_ID, Grade)
    ```

    `Step 3 — 3NF: remove transitive dependency`
    - In Student, `Student_ID → Dept_ID → Dept_Name`.
    ```
    Student(Student_ID, Name, Dept_ID)
    Department(Dept_ID, Dept_Name)
    ```

    The final normalised schema
    ```sql
    CREATE TABLE Department (
        Dept_ID   INT PRIMARY KEY,
        Dept_Name VARCHAR(50) NOT NULL
    );

    CREATE TABLE Student (
        Student_ID INT PRIMARY KEY,
        Name       VARCHAR(100) NOT NULL,
        Dept_ID    INT REFERENCES Department(Dept_ID)
    );

    CREATE TABLE Student_Phone (
        Student_ID INT,
        Phone      VARCHAR(15),
        PRIMARY KEY (Student_ID, Phone),
        FOREIGN KEY (Student_ID) REFERENCES Student(Student_ID)
    );

    CREATE TABLE Course (
        Course_ID   VARCHAR(10) PRIMARY KEY,
        Course_Name VARCHAR(100) NOT NULL
    );

    CREATE TABLE Enrollment (
        Student_ID INT,
        Course_ID  VARCHAR(10),
        Grade      CHAR(2),
        PRIMARY KEY (Student_ID, Course_ID),
        FOREIGN KEY (Student_ID) REFERENCES Student(Student_ID),
        FOREIGN KEY (Course_ID)  REFERENCES Course(Course_ID)
    );
    ```

    What was gained
    - Every fact is stored once. A course exists without students; a department name is changed in one place; deleting an enrolment destroys nothing else.

    Recovering the original view when it is needed
    ```sql
    SELECT s.Name, c.Course_Name, d.Dept_Name, e.Grade
    FROM   Student s
    JOIN   Enrollment e ON s.Student_ID = e.Student_ID
    JOIN   Course     c ON e.Course_ID  = c.Course_ID
    JOIN   Department d ON s.Dept_ID    = d.Dept_ID;
    ```
    - Nothing is lost by normalising; the combined picture is simply reassembled by a join. The cost is that join, which is why reporting systems sometimes `denormalise` deliberately.

21. **What do you mean by Database properties using Normalization?** *[Pubali Bank Ltd. Senior Officer (SD) 2018 compact it 1174 (ET: N/A)]*

    Answer: The properties a database gains from normalisation are the guarantees that its decomposition is correct and its data consistent.

    The two essential properties of a good decomposition

    1. `Lossless join (non-additive join) property`
    - When the decomposed tables are joined back together, the result must be `exactly` the original relation — no rows lost and no `spurious` rows created.
    - The condition: for a decomposition of R into R1 and R2, the join is lossless if `R1 ∩ R2` is a `superkey` of R1 or of R2.
    ```
    Lossy example:
       Student_Course(Student, Course, Teacher) decomposed on 'Course'
       into (Student, Course) and (Course, Teacher)
       -> if a course has two teachers, rejoining invents student-teacher pairs
          that never existed. These are SPURIOUS TUPLES.
    ```
    - This property is `mandatory`. A lossy decomposition is simply wrong.

    2. `Dependency preservation property`
    - Every functional dependency of the original relation should still be enforceable within `one` of the decomposed tables, without needing a join.
    - If a dependency spans two tables, the constraint cannot be checked by any single-table constraint, so the application must enforce it — which is fragile.
    - `Every relation can be decomposed into 3NF with both properties. BCNF guarantees lossless join but not always dependency preservation` — this is the classic trade-off and the usual reason designers stop at 3NF.

    The other properties normalisation delivers

    3. `Minimal redundancy` — each fact stored exactly once.

    4. `Freedom from anomalies` — insertion, update and deletion anomalies are eliminated.

    5. `Data integrity and consistency` — one stored copy cannot contradict itself.

    6. `Atomicity of attribute values` (from 1NF) — every cell holds one indivisible value, so it can be compared, indexed and joined.

    7. `Full functional dependency on the key` (from 2NF and 3NF) — every non-key attribute depends on the key, the whole key, and nothing but the key.

    8. `Flexibility and extensibility` — new attributes and entities can be added without restructuring existing tables.

    Illustration of the two decomposition properties
    ```
    R(A, B, C) with FDs  A -> B,  B -> C

    Decomposition 1: R1(A,B), R2(B,C)
       R1 ∩ R2 = {B}, and B is a key of R2   -> LOSSLESS  ✓
       A -> B held in R1, B -> C held in R2  -> DEPENDENCY PRESERVING  ✓

    Decomposition 2: R1(A,B), R2(A,C)
       R1 ∩ R2 = {A}, and A is a key of both -> LOSSLESS  ✓
       but B -> C is now split across the two tables
                                              -> NOT dependency preserving  ✗
    ```

    Summary

    | Property | Meaning | Always achievable? |
    |---|---|---|
    | `Lossless join` | Rejoining reproduces the original exactly | Yes, and mandatory |
    | `Dependency preservation` | Every FD enforceable in one table | Yes for 3NF, `not always` for BCNF |
    | `Minimal redundancy` | Each fact stored once | The goal of normalisation |
    | `No anomalies` | Insert, update, delete all safe | Achieved by 3NF/BCNF |

    - The practical conclusion: aim for a decomposition that is `lossless` above all, `dependency-preserving` where possible, and normalised to `3NF or BCNF`.

## SQL Commands (DDL, DML, DCL, TCL) (18)

1. Example Query of DDL, DML, DCL. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

   Answer:

   DDL — Data Definition Language
   - Defines and modifies the `structure` of the database. All DDL commands are `auto-committed` and cannot be rolled back in most systems.
   ```sql
   -- CREATE: build a new object
   CREATE TABLE Employee (
       emp_id   INT PRIMARY KEY,
       emp_name VARCHAR(100) NOT NULL,
       salary   DECIMAL(10,2) CHECK (salary > 0),
       dept_id  INT REFERENCES Department(dept_id)
   );

   -- ALTER: change an existing object
   ALTER TABLE Employee ADD COLUMN email VARCHAR(100);
   ALTER TABLE Employee MODIFY salary DECIMAL(12,2);
   ALTER TABLE Employee DROP COLUMN email;

   -- TRUNCATE: remove all rows, keep the structure
   TRUNCATE TABLE Employee;

   -- DROP: remove the object entirely
   DROP TABLE Employee;

   -- RENAME
   RENAME TABLE Employee TO Staff;
   ```

   DML — Data Manipulation Language
   - Works on the `data inside` the tables. DML is `not` auto-committed, so it can be rolled back.
   ```sql
   -- INSERT
   INSERT INTO Employee (emp_id, emp_name, salary, dept_id)
   VALUES (101, 'Karim', 50000, 10);

   INSERT INTO Employee VALUES
     (102, 'Rahim', 60000, 10),
     (103, 'Sumi',  45000, 20);

   -- UPDATE
   UPDATE Employee SET salary = salary * 1.10 WHERE dept_id = 10;

   -- DELETE
   DELETE FROM Employee WHERE emp_id = 103;

   -- SELECT (classified as DQL by many texts)
   SELECT emp_name, salary FROM Employee WHERE salary > 40000;
   ```

   DCL — Data Control Language
   - Controls `access` to the database objects.
   ```sql
   -- create a user
   CREATE USER clerk IDENTIFIED BY 'StrongPass123';

   -- GRANT: give privileges
   GRANT SELECT ON Employee TO clerk;
   GRANT SELECT, INSERT, UPDATE ON Employee TO manager;
   GRANT SELECT (emp_name, dept_id) ON Employee TO clerk;   -- column level
   GRANT ALL PRIVILEGES ON company.* TO admin_user;
   GRANT SELECT ON Employee TO analyst WITH GRANT OPTION;

   -- REVOKE: take them away
   REVOKE INSERT, UPDATE ON Employee FROM manager;
   REVOKE ALL PRIVILEGES ON company.* FROM admin_user;
   ```

   TCL — Transaction Control Language, usually asked alongside
   ```sql
   BEGIN;                                  -- or START TRANSACTION
   UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';
   SAVEPOINT after_debit;
   UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';
   ROLLBACK TO after_debit;                -- undo part of it
   COMMIT;                                 -- make it permanent
   ```

   Summary

   | Category | Commands | Acts on | Auto-commit | Rollback possible |
   |---|---|---|---|---|
   | `DDL` | CREATE, ALTER, DROP, TRUNCATE, RENAME | Structure | Yes | No |
   | `DML` | INSERT, UPDATE, DELETE | Data | No | Yes |
   | `DQL` | SELECT | Data (read only) | — | — |
   | `DCL` | GRANT, REVOKE | Permissions | Yes | No |
   | `TCL` | COMMIT, ROLLBACK, SAVEPOINT | Transactions | — | — |

2. **What is SQL?** *[BBA Assistant Programmer 12.07.2025 compact it 1433 (ET: BUET)]*

   Answer: `SQL` stands for `Structured Query Language`. It is the standard language for defining, manipulating and querying data in a relational database.

   Key facts
   - Developed at IBM in the 1970s, originally called SEQUEL. Standardised by ANSI in 1986 and ISO in 1987.
   - It is a `declarative` language: the user states `what` is wanted, and the DBMS decides `how` to get it. That is the essential difference from a procedural language.
   - It is used by every relational DBMS — MySQL, PostgreSQL, Oracle, SQL Server, SQLite — with small dialect differences.

   The five categories of SQL command

   | Category | Full form | Commands | Purpose |
   |---|---|---|---|
   | `DDL` | Data Definition Language | CREATE, ALTER, DROP, TRUNCATE, RENAME | Define the structure |
   | `DML` | Data Manipulation Language | INSERT, UPDATE, DELETE | Change the data |
   | `DQL` | Data Query Language | SELECT | Retrieve the data |
   | `DCL` | Data Control Language | GRANT, REVOKE | Control access |
   | `TCL` | Transaction Control Language | COMMIT, ROLLBACK, SAVEPOINT | Manage transactions |

   Examples of each
   ```sql
   -- DDL
   CREATE TABLE Student (
       id   INT PRIMARY KEY,
       name VARCHAR(100) NOT NULL,
       gpa  DECIMAL(3,2)
   );

   -- DML
   INSERT INTO Student VALUES (101, 'Karim', 3.75);
   UPDATE Student SET gpa = 3.90 WHERE id = 101;
   DELETE FROM Student WHERE id = 101;

   -- DQL
   SELECT name, gpa FROM Student WHERE gpa > 3.50 ORDER BY gpa DESC;

   -- DCL
   GRANT SELECT ON Student TO clerk;
   REVOKE SELECT ON Student FROM clerk;

   -- TCL
   BEGIN; UPDATE Student SET gpa = 4.00 WHERE id = 101; COMMIT;
   ```

   What SQL can do
   - Create and modify databases, tables, views and indexes; insert, update and delete data; run queries with filtering, sorting, grouping and joining; enforce constraints; control user permissions; and manage transactions.

   Features worth naming
   - `Declarative` rather than procedural; `case-insensitive` for keywords; `set-based`, operating on whole result sets rather than row by row; and supported by an `optimiser` that chooses indexes and join strategies automatically.

   Order of evaluation, which explains most SQL rules
   ```
   FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY -> LIMIT
   ```
   - This is why an aggregate cannot appear in `WHERE` (the groups do not yet exist) but can appear in `HAVING`, and why a column alias defined in SELECT can be used in ORDER BY but not in WHERE.

3. **ডাটাবেজ এ টেবিলের শুধু গঠন ডিলিট করার SQL কমান্ড কি?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) To delete only the `structure` of a table — the table itself and everything in it — the command is `DROP TABLE`.

   ```sql
   DROP TABLE table_name;
   ```
   - This removes the table definition, all its rows, its indexes, its constraints and any privileges granted on it. Nothing remains.

   The three commands compared, which is what the question is really testing

   | Command | What it removes | Structure survives? | Type | Rollback |
   |---|---|---|---|---|
   | `DELETE` | Chosen rows (or all rows) | `Yes` | DML | Yes |
   | `TRUNCATE` | All rows | `Yes` | DDL | Normally no |
   | `DROP` | Rows `and` structure | `No` | DDL | Normally no |

   ```sql
   DELETE FROM Student WHERE gpa < 2.0;   -- some rows go, table stays
   DELETE FROM Student;                    -- all rows go, table stays
   TRUNCATE TABLE Student;                 -- all rows go quickly, table stays
   DROP TABLE Student;                     -- table and rows both gone
   ```

   Other DROP forms
   ```sql
   DROP DATABASE company;
   DROP VIEW HighEarners;
   DROP INDEX idx_salary ON Employee;
   ALTER TABLE Employee DROP COLUMN email;      -- removes one column only
   ```

   Points worth remembering
   - `DROP TABLE IF EXISTS Student;` avoids an error when the table may not exist — useful in scripts.
   - A table referenced by a `foreign key` cannot be dropped until the referencing constraint is removed, or `CASCADE` is used:
   ```sql
   DROP TABLE Department CASCADE;      -- PostgreSQL, Oracle
   ```
   - `TRUNCATE` is far faster than `DELETE` on a large table, because it deallocates whole data pages instead of logging each row. It also resets the AUTO_INCREMENT counter, which `DELETE` does not.
   - In Oracle, a dropped table goes to the `recycle bin` and can be recovered with `FLASHBACK TABLE`; adding `PURGE` removes it permanently. MySQL and SQL Server have no such safety net.

4. **(খ) SQL এ DDL এবং DML এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 627 (ET: N/A)], [17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 611 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   | Point | DDL — Data Definition Language | DML — Data Manipulation Language |
   |---|---|---|
   | Full form | Data Definition Language | Data Manipulation Language |
   | Acts on | The `structure` (schema) of the database | The `data` inside the tables |
   | Commands | CREATE, ALTER, DROP, TRUNCATE, RENAME | INSERT, UPDATE, DELETE (and SELECT, classified as DQL) |
   | Auto-commit | `Yes` — changes are permanent immediately | `No` — must be committed |
   | Rollback possible | `No` (in most systems) | `Yes` |
   | Affects | Table definitions, columns, indexes, views | Rows and their values |
   | WHERE clause | Not applicable | Used to select which rows |
   | Speed | Fast — metadata only | Depends on the number of rows |
   | Typical user | Database administrator, designer | Application, end user |
   | Stored in | The data dictionary | The table's data pages |

   Examples

   `DDL`
   ```sql
   CREATE TABLE Student (
       id   INT PRIMARY KEY,
       name VARCHAR(100) NOT NULL,
       gpa  DECIMAL(3,2)
   );

   ALTER TABLE Student ADD COLUMN email VARCHAR(100);
   ALTER TABLE Student MODIFY gpa DECIMAL(4,2);
   ALTER TABLE Student DROP COLUMN email;

   TRUNCATE TABLE Student;        -- all rows removed, structure kept
   DROP TABLE Student;            -- structure removed as well
   ```

   `DML`
   ```sql
   INSERT INTO Student VALUES (101, 'Karim', 3.75);

   UPDATE Student SET gpa = 3.90 WHERE id = 101;

   DELETE FROM Student WHERE gpa < 2.00;

   SELECT name, gpa FROM Student WHERE gpa > 3.50;
   ```

   The difference in one illustration
   ```
   DDL creates the container:
       CREATE TABLE Student (id, name, gpa)
       +----+------+-----+
       | id | name | gpa |        <- the structure exists, no rows yet
       +----+------+-----+

   DML fills and changes it:
       INSERT INTO Student VALUES (101, 'Karim', 3.75)
       +-----+-------+------+
       | 101 | Karim | 3.75 |     <- a row now exists
       +-----+-------+------+
   ```

   The most examined point
   - `DDL is auto-committed and DML is not`. A mistaken `DELETE` inside a transaction can be undone with `ROLLBACK`; a mistaken `DROP TABLE` generally cannot. This is why a DROP should always be preceded by a backup.
   ```sql
   BEGIN;
   DELETE FROM Student;      -- oops
   ROLLBACK;                 -- recovered

   DROP TABLE Student;       -- committed immediately; no rollback
   ```

5. **SQL query to insert data into table. (A table was given with 3 row)** *[NSDA Assistant Programmer Date: 04-03-2022 compact it 657 (ET: N/A)]*

   Answer: The table was not printed, so a three-row insert is shown in every form.

   Basic INSERT — one row, naming the columns
   ```sql
   INSERT INTO Student (student_id, name, department, gpa)
   VALUES (101, 'Karim', 'CSE', 3.75);
   ```
   - Naming the columns explicitly is good practice: the statement keeps working if a column is added later, and the mapping is obvious to a reader.

   Multiple rows in one statement — the answer the question wants
   ```sql
   INSERT INTO Student (student_id, name, department, gpa) VALUES
       (101, 'Karim', 'CSE', 3.75),
       (102, 'Rahim', 'EEE', 3.50),
       (103, 'Sumi',  'CSE', 3.90);
   ```
   - One statement is faster than three: a single round trip and a single transaction.

   Without naming the columns
   ```sql
   INSERT INTO Student VALUES (101, 'Karim', 'CSE', 3.75);
   ```
   - Legal, but fragile — the values must match the column order exactly, and adding a column breaks it.

   Inserting into some columns only
   ```sql
   INSERT INTO Student (student_id, name) VALUES (104, 'Nabil');
   ```
   - The remaining columns take their `DEFAULT`, or NULL if none is defined. This fails if a NOT NULL column with no default is omitted.

   Inserting from another table
   ```sql
   INSERT INTO Student_Backup (student_id, name, department, gpa)
   SELECT student_id, name, department, gpa
   FROM   Student
   WHERE  department = 'CSE';
   ```
   - `INSERT ... SELECT` copies rows without any VALUES clause. This is how data is migrated between tables.

   Handling a duplicate key
   ```sql
   -- MySQL: update instead of failing
   INSERT INTO Student (student_id, name, gpa) VALUES (101, 'Karim', 3.85)
   ON DUPLICATE KEY UPDATE gpa = VALUES(gpa);

   -- PostgreSQL
   INSERT INTO Student (student_id, name, gpa) VALUES (101, 'Karim', 3.85)
   ON CONFLICT (student_id) DO UPDATE SET gpa = EXCLUDED.gpa;

   -- MySQL: silently skip a duplicate
   INSERT IGNORE INTO Student VALUES (101, 'Karim', 'CSE', 3.75);
   ```

   The result
   ```
   Student
   +------------+-------+------------+------+
   | student_id | name  | department | gpa  |
   +------------+-------+------------+------+
   |    101     | Karim | CSE        | 3.75 |
   |    102     | Rahim | EEE        | 3.50 |
   |    103     | Sumi  | CSE        | 3.90 |
   +------------+-------+------------+------+
   ```

   Points worth remembering
   - Text and dates go in `single quotes`; numbers do not.
   - The insert is rejected if it violates a `PRIMARY KEY`, `NOT NULL`, `CHECK`, `UNIQUE` or `FOREIGN KEY` constraint — which is exactly what those constraints are for.
   - Wrap a large or important insert in a transaction so it can be undone:
   ```sql
   BEGIN;
   INSERT INTO Student VALUES (...);
   SELECT * FROM Student;      -- verify
   COMMIT;                      -- or ROLLBACK
   ```

6. **How can you Revoke permissions from a database table? Give SQL command for it.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 666 (ET: N/A)]*

   Answer: Permissions are removed with the `REVOKE` command, which belongs to `DCL` (Data Control Language).

   Basic syntax
   ```sql
   REVOKE privilege_list ON object FROM user_or_role;
   ```

   Examples
   ```sql
   -- take away one privilege
   REVOKE INSERT ON Employee FROM clerk;

   -- take away several at once
   REVOKE INSERT, UPDATE, DELETE ON Employee FROM manager;

   -- take away everything on one table
   REVOKE ALL PRIVILEGES ON Employee FROM clerk;

   -- take away everything on every table in a database
   REVOKE ALL PRIVILEGES ON company.* FROM analyst;

   -- column-level revoke
   REVOKE UPDATE (salary) ON Employee FROM clerk;

   -- revoke from several users in one statement
   REVOKE SELECT ON Employee FROM clerk, intern, temp_user;

   -- revoke a role
   REVOKE role_reporting FROM analyst;
   ```

   The counterpart, GRANT
   ```sql
   GRANT SELECT ON Employee TO clerk;
   GRANT SELECT, INSERT, UPDATE ON Employee TO manager;
   GRANT ALL PRIVILEGES ON company.* TO admin_user;
   GRANT SELECT ON Employee TO analyst WITH GRANT OPTION;
   ```

   The privileges that can be granted or revoked

   | Privilege | Allows |
   |---|---|
   | SELECT | Reading rows |
   | INSERT | Adding rows |
   | UPDATE | Changing rows |
   | DELETE | Removing rows |
   | REFERENCES | Creating a foreign key pointing at the table |
   | ALTER | Changing the structure |
   | INDEX | Creating and dropping indexes |
   | EXECUTE | Running a procedure or function |
   | ALL PRIVILEGES | Everything above |

   The cascade problem, which is the subtle point
   - If a privilege was granted `WITH GRANT OPTION`, the recipient may have passed it on. Revoking it from them leaves those onward grants dangling.
   ```sql
   REVOKE SELECT ON Employee FROM analyst CASCADE;   -- also revokes what analyst granted
   REVOKE SELECT ON Employee FROM analyst RESTRICT;  -- refuses if analyst granted it onward
   ```
   - Oracle and PostgreSQL support `CASCADE`; MySQL revokes only the direct grant and leaves onward grants in place, which is a real administrative trap.

   Practical notes
   ```sql
   -- in MySQL the privilege cache must be refreshed after some changes
   FLUSH PRIVILEGES;

   -- check what a user currently holds
   SHOW GRANTS FOR 'clerk'@'localhost';       -- MySQL
   \du                                         -- PostgreSQL
   ```
   - Best practice is `least privilege`: grant only what the role genuinely needs, prefer granting to `roles` rather than to individual users, and use `views` to expose a subset of columns rather than granting access to the whole table.

7. **What is DDL and DML?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

   Answer:

   DDL — Data Definition Language
   - Commands that define and modify the `structure` of the database, not its contents.
   - All DDL statements are `auto-committed`: the change is permanent as soon as it runs and cannot normally be rolled back.

   | Command | Purpose |
   |---|---|
   | `CREATE` | Create a database, table, view or index |
   | `ALTER` | Modify an existing object's structure |
   | `DROP` | Delete an object entirely |
   | `TRUNCATE` | Remove all rows, keeping the structure |
   | `RENAME` | Rename an object |

   ```sql
   CREATE TABLE Employee (
       emp_id   INT PRIMARY KEY,
       emp_name VARCHAR(100) NOT NULL,
       salary   DECIMAL(10,2)
   );

   ALTER TABLE Employee ADD COLUMN email VARCHAR(100);
   ALTER TABLE Employee MODIFY salary DECIMAL(12,2);
   TRUNCATE TABLE Employee;
   DROP TABLE Employee;
   ```

   DML — Data Manipulation Language
   - Commands that work on the `data` stored in the tables.
   - DML is `not` auto-committed, so it can be rolled back within a transaction.

   | Command | Purpose |
   |---|---|
   | `INSERT` | Add new rows |
   | `UPDATE` | Modify existing rows |
   | `DELETE` | Remove rows |
   | `SELECT` | Retrieve rows (classified as DQL by many texts) |

   ```sql
   INSERT INTO Employee VALUES (101, 'Karim', 50000);
   UPDATE Employee SET salary = salary * 1.10 WHERE emp_id = 101;
   DELETE FROM Employee WHERE emp_id = 101;
   SELECT emp_name, salary FROM Employee WHERE salary > 40000;
   ```

   Comparison

   | Point | DDL | DML |
   |---|---|---|
   | Acts on | Structure | Data |
   | Auto-commit | Yes | No |
   | Rollback | Not possible | Possible |
   | WHERE clause | Not used | Used |
   | Speed | Fast, metadata only | Depends on row count |
   | Typical user | DBA, designer | Application, end user |

   The illustration that makes it clear
   ```
   DDL builds the container:
      CREATE TABLE Employee (emp_id, emp_name, salary)
      +--------+----------+--------+
      | emp_id | emp_name | salary |     <- structure exists, no data
      +--------+----------+--------+

   DML puts things in it:
      INSERT INTO Employee VALUES (101, 'Karim', 50000)
      +-----+-------+-------+
      | 101 | Karim | 50000 |            <- data now exists
      +-----+-------+-------+
   ```

   The point examiners test most
   - A wrong `DELETE` inside a transaction can be undone with `ROLLBACK`; a wrong `DROP TABLE` generally cannot, because DDL commits itself. That single difference is why every DROP should be preceded by a backup.

8. **(i) নিচের Table টি তৈরি করার SQL কমান্ড লিখুন। student_info (std_id, name, department, phone_number) (a) Table তে ২টি record (insert) প্রবেশ করার SQL কমান্ড লিখুন। (b) Table টি থেকে CSE বিভাগের ছাত্র/ছাত্রীদের নামের তালিকা বের করার SQL command লিখুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 785 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   Creating the table
   ```sql
   CREATE TABLE student_info (
       std_id       INT PRIMARY KEY,
       name         VARCHAR(100) NOT NULL,
       department   VARCHAR(50),
       phone_number VARCHAR(15)
   );
   ```
   - `PRIMARY KEY` on std_id makes it unique and not null.
   - `NOT NULL` on name forbids a nameless record.
   - `phone_number` is `VARCHAR`, not a numeric type — a phone number is a string of digits, not a quantity. Storing it as INT would lose a leading zero and would allow meaningless arithmetic on it. This is a point examiners look for.

   (a) Inserting two records
   ```sql
   INSERT INTO student_info (std_id, name, department, phone_number) VALUES
       (101, 'Karim Ahmed', 'CSE', '01711111111'),
       (102, 'Rahim Uddin', 'EEE', '01822222222');
   ```

   As two separate statements, which is equally acceptable
   ```sql
   INSERT INTO student_info VALUES (101, 'Karim Ahmed', 'CSE', '01711111111');
   INSERT INTO student_info VALUES (102, 'Rahim Uddin', 'EEE', '01822222222');
   ```

   (b) Listing the names of CSE students
   ```sql
   SELECT name
   FROM   student_info
   WHERE  department = 'CSE';
   ```

   Sample data and output
   ```
   student_info
   +--------+--------------+------------+--------------+
   | std_id | name         | department | phone_number |
   +--------+--------------+------------+--------------+
   |  101   | Karim Ahmed  | CSE        | 01711111111  |
   |  102   | Rahim Uddin  | EEE        | 01822222222  |
   |  103   | Sumi Akter   | CSE        | 01933333333  |
   +--------+--------------+------------+--------------+

   Result of (b)
   +--------------+
   | name         |
   +--------------+
   | Karim Ahmed  |
   | Sumi Akter   |
   +--------------+
   ```

   Useful refinements
   ```sql
   -- sorted alphabetically
   SELECT name FROM student_info WHERE department = 'CSE' ORDER BY name;

   -- with the id as well
   SELECT std_id, name FROM student_info WHERE department = 'CSE';

   -- how many students in each department
   SELECT department, COUNT(*) FROM student_info GROUP BY department;

   -- case-insensitive match, portable
   SELECT name FROM student_info WHERE UPPER(department) = 'CSE';
   ```
   - Note that string comparison is case-sensitive in PostgreSQL and Oracle but case-insensitive under MySQL's default collation, so `'cse'` may or may not match `'CSE'` depending on the system.

9. **Write the create table command for the ‘Employee’ table with the following column: Emp_ID, Emp_Name, Date_of_Birth.** *[BCC CA Monitoring System Project 2021 compact it 829 (ET: N/A)]*

   Answer:

   The command
   ```sql
   CREATE TABLE Employee (
       Emp_ID        INT PRIMARY KEY,
       Emp_Name      VARCHAR(100) NOT NULL,
       Date_of_Birth DATE
   );
   ```

   Explanation of each part
   - `Emp_ID INT PRIMARY KEY` — a whole number that uniquely identifies each employee. `PRIMARY KEY` implies both `UNIQUE` and `NOT NULL`, and creates a clustered index automatically.
   - `Emp_Name VARCHAR(100) NOT NULL` — variable-length text up to 100 characters. `VARCHAR` is preferred to `CHAR` for a name, because names differ in length and CHAR would pad every one to the full width. `NOT NULL` forbids a nameless record.
   - `Date_of_Birth DATE` — the `DATE` type stores a real date, so date arithmetic, comparison and sorting all work correctly. Storing a date as `VARCHAR` is a common and serious error: '01/02/2000' cannot be compared or sorted reliably, and the format is ambiguous.

   A fuller version, as it would be written in practice
   ```sql
   CREATE TABLE Employee (
       Emp_ID        INT PRIMARY KEY AUTO_INCREMENT,
       Emp_Name      VARCHAR(100) NOT NULL,
       Date_of_Birth DATE CHECK (Date_of_Birth < CURRENT_DATE),
       Email         VARCHAR(100) UNIQUE,
       Salary        DECIMAL(10,2) CHECK (Salary > 0),
       Dept_ID       INT,
       Created_At    TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
       FOREIGN KEY (Dept_ID) REFERENCES Department(Dept_ID)
   );
   ```
   - `AUTO_INCREMENT` (MySQL), `SERIAL` (PostgreSQL) or `IDENTITY` (SQL Server) generates the id automatically.
   - `CHECK (Date_of_Birth < CURRENT_DATE)` prevents a date in the future.
   - `DECIMAL` rather than `FLOAT` for money, because binary floating point cannot represent decimal amounts exactly.

   Inserting a row
   ```sql
   INSERT INTO Employee (Emp_ID, Emp_Name, Date_of_Birth)
   VALUES (101, 'Karim Ahmed', '1995-06-15');
   ```

   Verifying the structure
   ```sql
   DESCRIBE Employee;          -- MySQL
   \d Employee                 -- PostgreSQL
   ```

   Modifying it afterwards
   ```sql
   ALTER TABLE Employee ADD COLUMN Phone VARCHAR(15);
   ALTER TABLE Employee MODIFY Emp_Name VARCHAR(150);
   ALTER TABLE Employee DROP COLUMN Phone;
   ```

   Computing age from the stored date
   ```sql
   SELECT Emp_Name, TIMESTAMPDIFF(YEAR, Date_of_Birth, CURDATE()) AS Age
   FROM   Employee;
   ```
   - `Age` is deliberately `not` stored as a column: it is a `derived` value and would be wrong the day after it was written. Storing the date of birth and computing the age is the correct design.

10. **৪. ডাটাবেইজে টেবিল ডিলেট করার কমান্ড লিখ?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) To delete a table from a database, the command is:

    ```sql
    DROP TABLE table_name;
    ```

    Example
    ```sql
    DROP TABLE Student;
    ```
    - This removes the table completely — its structure, all its rows, its indexes, its constraints and any privileges granted on it.

    Safer form for use in scripts
    ```sql
    DROP TABLE IF EXISTS Student;
    ```
    - Avoids an error when the table may not exist.

    The three related commands, which the question is really testing

    | Command | Removes | Structure remains? | Type | Rollback |
    |---|---|---|---|---|
    | `DELETE` | Selected rows | Yes | DML | Yes |
    | `TRUNCATE` | All rows | Yes | DDL | Normally no |
    | `DROP` | Rows and structure | `No` | DDL | Normally no |

    ```sql
    DELETE FROM Student WHERE gpa < 2.0;   -- some rows
    DELETE FROM Student;                    -- all rows, table stays
    TRUNCATE TABLE Student;                 -- all rows quickly, table stays
    DROP TABLE Student;                     -- table gone entirely
    ```

    Other DROP commands
    ```sql
    DROP DATABASE company;
    DROP VIEW HighEarners;
    DROP INDEX idx_salary ON Employee;
    DROP PROCEDURE calculate_bonus;
    ALTER TABLE Employee DROP COLUMN email;    -- removes one column only
    ```

    Points to be careful about
    - A table referenced by a `foreign key` cannot be dropped until the constraint is removed, or `CASCADE` is used:
    ```sql
    DROP TABLE Department CASCADE;      -- PostgreSQL, Oracle
    ```
    - `DROP` is `auto-committed` — it cannot be undone with `ROLLBACK`. Always take a backup first.
    - In Oracle a dropped table goes to the `recycle bin` and can be restored with `FLASHBACK TABLE ... TO BEFORE DROP`. Adding `PURGE` removes it permanently. MySQL and SQL Server have no such safety net, so a DROP there is immediate and final.

11. **ডাটাবেইজ ম্যানেজমেন্ট সিস্টেমের মধ্যে CRUD এর কাজ কি?** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 947 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) `CRUD` stands for `Create, Read, Update, Delete` — the four basic operations that any persistent-storage system must support.

    The four operations and their SQL commands

    | CRUD | SQL command | HTTP method | Purpose |
    |---|---|---|---|
    | `Create` | `INSERT` | POST | Add new data |
    | `Read` | `SELECT` | GET | Retrieve existing data |
    | `Update` | `UPDATE` | PUT / PATCH | Modify existing data |
    | `Delete` | `DELETE` | DELETE | Remove data |

    Examples
    ```sql
    -- CREATE
    INSERT INTO Student (student_id, name, department, gpa)
    VALUES (101, 'Karim', 'CSE', 3.75);

    -- READ
    SELECT * FROM Student WHERE department = 'CSE';
    SELECT name, gpa FROM Student WHERE gpa > 3.5 ORDER BY gpa DESC;

    -- UPDATE
    UPDATE Student SET gpa = 3.90 WHERE student_id = 101;

    -- DELETE
    DELETE FROM Student WHERE student_id = 101;
    ```

    Why CRUD matters
    - It is the `minimum complete set` of operations. Any data-management system that supports all four can maintain data through its whole life cycle; one missing any of them is incomplete.
    - It is the standard vocabulary for describing an application's data layer, and it maps directly onto `REST API` design, which is why the HTTP column above lines up so neatly.
    - Application frameworks generate `CRUD scaffolding` — forms and endpoints for the four operations — because almost every screen in a business application is one of them.

    The relationship with SQL command categories
    ```
    CREATE, UPDATE, DELETE  -> DML (Data Manipulation Language)
    READ (SELECT)           -> DQL (Data Query Language)
    ```

    Practical cautions
    - `UPDATE` and `DELETE` without a `WHERE` clause affect `every row`. Always run the equivalent `SELECT` first to confirm the target rows, and wrap the change in a transaction:
    ```sql
    BEGIN;
    DELETE FROM Student WHERE department = 'CSE';
    SELECT COUNT(*) FROM Student;     -- verify
    COMMIT;                            -- or ROLLBACK
    ```
    - Many systems prefer a `soft delete` — setting an `is_deleted` flag instead of removing the row — so that history and audit trails survive:
    ```sql
    UPDATE Student SET is_deleted = 1, deleted_at = NOW() WHERE student_id = 101;
    ```
    - Each operation should also be subject to permission control, so that a user who may `read` is not automatically allowed to `delete`.

12. **Main components of SQL are DDL (Data definition Language), DML (Data Manipulation Language) and DCL (Data Control Language). Give some examples of DDL, DML and DCL commands.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 988-989 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

    Answer:

    DDL — Data Definition Language
    - Defines and modifies the `structure` of the database. All DDL commands are `auto-committed`.

    | Command | Purpose |
    |---|---|
    | `CREATE` | Create a database, table, view or index |
    | `ALTER` | Modify an existing structure |
    | `DROP` | Delete an object completely |
    | `TRUNCATE` | Remove all rows, keep the structure |
    | `RENAME` | Rename an object |

    ```sql
    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,
        emp_name VARCHAR(100) NOT NULL,
        salary   DECIMAL(10,2)
    );
    ALTER TABLE Employee ADD COLUMN email VARCHAR(100);
    TRUNCATE TABLE Employee;
    DROP TABLE Employee;
    ```

    DML — Data Manipulation Language
    - Works on the `data` inside the tables. Not auto-committed, so it can be rolled back.

    | Command | Purpose |
    |---|---|
    | `INSERT` | Add rows |
    | `UPDATE` | Modify rows |
    | `DELETE` | Remove rows |
    | `SELECT` | Retrieve rows (classified as DQL by many texts) |

    ```sql
    INSERT INTO Employee VALUES (101, 'Karim', 50000);
    UPDATE Employee SET salary = salary * 1.10 WHERE emp_id = 101;
    DELETE FROM Employee WHERE emp_id = 101;
    SELECT emp_name, salary FROM Employee WHERE salary > 40000;
    ```

    DCL — Data Control Language
    - Controls `access` to the database objects.

    | Command | Purpose |
    |---|---|
    | `GRANT` | Give privileges to a user or role |
    | `REVOKE` | Take privileges away |

    ```sql
    CREATE USER clerk IDENTIFIED BY 'StrongPass123';

    GRANT SELECT ON Employee TO clerk;
    GRANT SELECT, INSERT, UPDATE ON Employee TO manager;
    GRANT SELECT (emp_name, dept_id) ON Employee TO clerk;   -- column level
    GRANT ALL PRIVILEGES ON company.* TO admin_user;

    REVOKE INSERT, UPDATE ON Employee FROM manager;
    REVOKE ALL PRIVILEGES ON company.* FROM admin_user;
    ```

    TCL — Transaction Control Language, usually asked with them
    ```sql
    BEGIN;
    UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';
    SAVEPOINT after_debit;
    UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';
    COMMIT;                       -- or ROLLBACK, or ROLLBACK TO after_debit
    ```

    Summary

    | Category | Commands | Acts on | Auto-commit | Rollback |
    |---|---|---|---|---|
    | `DDL` | CREATE, ALTER, DROP, TRUNCATE, RENAME | Structure | Yes | No |
    | `DML` | INSERT, UPDATE, DELETE | Data | No | Yes |
    | `DCL` | GRANT, REVOKE | Permissions | Yes | No |
    | `TCL` | COMMIT, ROLLBACK, SAVEPOINT | Transactions | — | — |

    - The distinction worth remembering: `DDL builds the container, DML fills it, DCL decides who may touch it, and TCL decides when the changes become permanent`.

13. **How to find duplicate data in database? Explain DDL and DML.** *[RAKUB Assistant Database Administrator 2020 compact it 1017-1018 (ET: E-Zone)]*

    Answer:

    Part 1 — finding duplicate data
    - A duplicate is a value that appears more than once, so the rows are grouped and the groups with a count above one are kept.

    ```sql
    -- duplicates on a single column
    SELECT   emp_name, COUNT(*) AS occurrences
    FROM     Employee
    GROUP BY emp_name
    HAVING   COUNT(*) > 1;

    -- duplicates on several columns together
    SELECT   emp_name, dept_id, COUNT(*) AS occurrences
    FROM     Employee
    GROUP BY emp_name, dept_id
    HAVING   COUNT(*) > 1;

    -- the full rows of every duplicated employee
    SELECT *
    FROM   Employee
    WHERE  emp_name IN (SELECT emp_name FROM Employee
                        GROUP BY emp_name HAVING COUNT(*) > 1)
    ORDER  BY emp_name;

    -- window-function form, which also marks the extra copies
    SELECT * FROM (
        SELECT e.*, ROW_NUMBER() OVER (PARTITION BY emp_name ORDER BY emp_id) AS rn
        FROM   Employee e
    ) t
    WHERE rn > 1;                    -- these are the rows to delete
    ```

    Removing them, keeping the lowest id
    ```sql
    DELETE FROM Employee
    WHERE  emp_id NOT IN (SELECT keep FROM
            (SELECT MIN(emp_id) AS keep FROM Employee GROUP BY emp_name) AS t);
    ```
    - Preventing the problem is better than curing it:
    ```sql
    ALTER TABLE Employee ADD CONSTRAINT uq_emp UNIQUE (emp_name, dept_id);
    ```

    Part 2 — DDL and DML

    `DDL — Data Definition Language`
    - Defines and modifies the `structure` of the database. `Auto-committed`, so it cannot be rolled back.
    ```sql
    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,
        emp_name VARCHAR(100) NOT NULL,
        salary   DECIMAL(10,2)
    );
    ALTER TABLE Employee ADD COLUMN email VARCHAR(100);
    TRUNCATE TABLE Employee;
    DROP TABLE Employee;
    ```

    `DML — Data Manipulation Language`
    - Works on the `data` inside the tables. Not auto-committed, so it can be rolled back.
    ```sql
    INSERT INTO Employee VALUES (101, 'Karim', 50000);
    UPDATE Employee SET salary = salary * 1.10 WHERE emp_id = 101;
    DELETE FROM Employee WHERE emp_id = 101;
    SELECT emp_name, salary FROM Employee;
    ```

    Comparison

    | Point | DDL | DML |
    |---|---|---|
    | Acts on | Structure | Data |
    | Commands | CREATE, ALTER, DROP, TRUNCATE, RENAME | INSERT, UPDATE, DELETE, SELECT |
    | Auto-commit | Yes | No |
    | Rollback | Not possible | Possible |
    | WHERE clause | Not used | Used |
    | Typical user | DBA, designer | Application, end user |

    - The connection between the two halves of this question: `DELETE` (DML) removing duplicates can be rolled back if it goes wrong, whereas a `TRUNCATE` or `DROP` (DDL) cannot. That is why duplicate cleanup should always be done with DELETE inside a transaction.

14. **(a) How can you revoke permissions from a database table? Give SQL command for it.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1136-1138 (ET: N/A)]*

    Answer: Permissions are removed with the `REVOKE` command, which belongs to `DCL` (Data Control Language).

    Syntax
    ```sql
    REVOKE privilege_list ON object FROM user_or_role;
    ```

    Examples
    ```sql
    -- a single privilege
    REVOKE INSERT ON Employee FROM clerk;

    -- several at once
    REVOKE INSERT, UPDATE, DELETE ON Employee FROM manager;

    -- everything on one table
    REVOKE ALL PRIVILEGES ON Employee FROM clerk;

    -- everything on every table in a database
    REVOKE ALL PRIVILEGES ON company.* FROM analyst;

    -- column-level
    REVOKE UPDATE (salary) ON Employee FROM clerk;

    -- from several users
    REVOKE SELECT ON Employee FROM clerk, intern;

    -- a whole role
    REVOKE role_reporting FROM analyst;
    ```

    The counterpart
    ```sql
    GRANT SELECT ON Employee TO clerk;
    GRANT SELECT, INSERT, UPDATE ON Employee TO manager;
    GRANT ALL PRIVILEGES ON company.* TO admin_user;
    GRANT SELECT ON Employee TO analyst WITH GRANT OPTION;
    ```

    Privileges that can be granted or revoked

    | Privilege | Allows |
    |---|---|
    | SELECT | Reading rows |
    | INSERT | Adding rows |
    | UPDATE | Changing rows |
    | DELETE | Removing rows |
    | REFERENCES | Creating a foreign key to the table |
    | ALTER | Changing the structure |
    | INDEX | Creating and dropping indexes |
    | EXECUTE | Running a procedure |
    | ALL PRIVILEGES | All of the above |

    The cascade issue
    - If the privilege was granted `WITH GRANT OPTION`, the recipient may have passed it on. Revoking from them leaves those onward grants in place unless CASCADE is used.
    ```sql
    REVOKE SELECT ON Employee FROM analyst CASCADE;    -- also revokes onward grants
    REVOKE SELECT ON Employee FROM analyst RESTRICT;   -- refuses if any exist
    ```
    - Oracle and PostgreSQL support this; MySQL revokes only the direct grant, which is an administrative trap worth knowing.

    Verifying the result
    ```sql
    SHOW GRANTS FOR 'clerk'@'localhost';     -- MySQL
    \du                                       -- PostgreSQL
    SELECT * FROM information_schema.table_privileges WHERE grantee = 'clerk';
    FLUSH PRIVILEGES;                         -- MySQL, after some manual changes
    ```

    Best practice
    - Apply `least privilege` — grant only what the role genuinely needs.
    - Grant to `roles` rather than to individual users, so that staff changes need no privilege changes.
    - Use `views` to expose a subset of columns instead of granting access to a whole table:
    ```sql
    CREATE VIEW PublicStaff AS SELECT emp_name, designation FROM Employee;
    GRANT SELECT ON PublicStaff TO clerk;    -- no access to salary at all
    ```

15. **(c) Differentiate between “delete from” and “drop table” SQL statement.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1136-1138 (ET: N/A)]*

    Answer:

    | Point | DELETE FROM | DROP TABLE |
    |---|---|---|
    | Command type | `DML` — Data Manipulation Language | `DDL` — Data Definition Language |
    | Removes | `Rows` only | The `entire table` — rows and structure |
    | Table survives | `Yes` — the empty structure remains | `No` — the table ceases to exist |
    | WHERE clause | Supported, so specific rows can be chosen | Not applicable |
    | Rollback | `Possible` inside a transaction | `Not possible` — auto-committed |
    | Speed | Slower — row by row, each logged | Fast |
    | Triggers fired | `Yes` | No |
    | Indexes and constraints | Retained | Removed with the table |
    | Privileges on the object | Retained | Removed |
    | Space reclaimed | Not immediately | Immediately |
    | AUTO_INCREMENT counter | Not reset | Irrelevant — the table is gone |

    Examples
    ```sql
    -- DELETE: chosen rows, table stays
    DELETE FROM Student WHERE gpa < 2.0;

    -- DELETE: every row, table still stays
    DELETE FROM Student;

    -- DROP: the table itself disappears
    DROP TABLE Student;
    ```

    Illustration
    ```
    Before
    +--------+-------+------+
    | std_id | name  | gpa  |
    +--------+-------+------+
    |  101   | Karim | 3.75 |
    |  102   | Rahim | 1.80 |
    +--------+-------+------+

    After  DELETE FROM Student;
    +--------+-------+------+
    | std_id | name  | gpa  |      <- structure intact, no rows
    +--------+-------+------+

    After  DROP TABLE Student;
    ERROR 1146: Table 'Student' doesn't exist
    ```

    TRUNCATE, the third command in the family
    ```sql
    TRUNCATE TABLE Student;
    ```
    - Removes all rows like `DELETE FROM Student` but is far faster, because it deallocates whole data pages rather than logging each row. It is DDL, so it normally cannot be rolled back; it does not fire triggers; and it `resets` the AUTO_INCREMENT counter.

    | Command | Rows | Structure | Type | Rollback | Speed |
    |---|---|---|---|---|---|
    | `DELETE` | Selected or all | Kept | DML | Yes | Slow |
    | `TRUNCATE` | All | Kept | DDL | Normally no | Fast |
    | `DROP` | All | `Removed` | DDL | No | Fast |

    The practical consequence
    ```sql
    BEGIN;
    DELETE FROM Student;      -- a mistake
    ROLLBACK;                 -- recovered, no harm done

    DROP TABLE Student;       -- a mistake
    ROLLBACK;                 -- too late; DDL committed itself
    ```
    - This is why a `DROP` should always be preceded by a backup, while a `DELETE` inside a transaction is comparatively safe.

16. **Write an SQL query to insert a tuple in the table: Employee (ID, Name, Designation, and Salary).** *[NESCO Assistant Manager (MIS & ICT) 2018 compact it 1177 (ET: N/A)]*

    Answer:

    The command
    ```sql
    INSERT INTO Employee (ID, Name, Designation, Salary)
    VALUES (101, 'Karim Ahmed', 'Manager', 75000);
    ```

    Without naming the columns
    ```sql
    INSERT INTO Employee VALUES (101, 'Karim Ahmed', 'Manager', 75000);
    ```
    - Legal, but the values must match the column order exactly. Naming the columns is better practice: the statement survives a later column addition and its intent is obvious to a reader.

    Inserting several tuples at once
    ```sql
    INSERT INTO Employee (ID, Name, Designation, Salary) VALUES
        (101, 'Karim Ahmed', 'Manager',   75000),
        (102, 'Rahim Uddin', 'Developer', 55000),
        (103, 'Sumi Akter',  'Analyst',   48000);
    ```
    - One statement rather than three: a single round trip and a single transaction, so it is considerably faster.

    Inserting into some columns only
    ```sql
    INSERT INTO Employee (ID, Name) VALUES (104, 'Nabil Hasan');
    ```
    - The remaining columns take their `DEFAULT` value, or NULL where none is defined. This fails if a NOT NULL column without a default is omitted.

    Inserting from a query
    ```sql
    INSERT INTO Employee_Archive (ID, Name, Designation, Salary)
    SELECT ID, Name, Designation, Salary
    FROM   Employee
    WHERE  Salary > 100000;
    ```

    Sample result
    ```
    Employee
    +-----+-------------+-------------+--------+
    | ID  | Name        | Designation | Salary |
    +-----+-------------+-------------+--------+
    | 101 | Karim Ahmed | Manager     | 75000  |
    +-----+-------------+-------------+--------+
    ```

    Points worth remembering
    - Text values go in `single quotes`; numeric values do not.
    - Dates are written as `'YYYY-MM-DD'`, the unambiguous ISO form.
    - The insert is rejected if it violates a `PRIMARY KEY`, `NOT NULL`, `CHECK`, `UNIQUE` or `FOREIGN KEY` constraint — which is exactly what those constraints exist for.
    - Handling a duplicate key without failing:
    ```sql
    -- MySQL
    INSERT INTO Employee VALUES (101, 'Karim', 'Manager', 80000)
    ON DUPLICATE KEY UPDATE Salary = VALUES(Salary);

    -- PostgreSQL
    INSERT INTO Employee VALUES (101, 'Karim', 'Manager', 80000)
    ON CONFLICT (ID) DO UPDATE SET Salary = EXCLUDED.Salary;
    ```
    - For an important insert, use a transaction so it can be undone:
    ```sql
    BEGIN;
    INSERT INTO Employee VALUES (101, 'Karim Ahmed', 'Manager', 75000);
    SELECT * FROM Employee WHERE ID = 101;    -- verify
    COMMIT;                                    -- or ROLLBACK
    ```

17. **Construct a database table “Customer”, Where CustomerID is primary key of the table.** *[Jiban Bima Corporation Assistant Programmer 2018 compact it 1211 (ET: N/A)]*

| CustomerID | CustomerName | Address | PostCode |
|---|---|---|---|
| 1 | Sakib | Khulna | 1212 |
| 2 | Tamim | Barisal | 2100 |
| 3 | Musfiq | Dhaka | 1205 |

    Answer:

    The command
    ```sql
    CREATE TABLE Customer (
        CustomerID   INT PRIMARY KEY,
        CustomerName VARCHAR(100) NOT NULL,
        Address      VARCHAR(200),
        Phone        VARCHAR(15),
        Email        VARCHAR(100) UNIQUE,
        City         VARCHAR(50),
        Join_Date    DATE DEFAULT (CURRENT_DATE)
    );
    ```

    Explanation of each element
    - `CustomerID INT PRIMARY KEY` — the primary key. It implies both `UNIQUE` and `NOT NULL`, so no two customers can share an id and none can be left blank. Most systems create a clustered index on it automatically.
    - `CustomerName VARCHAR(100) NOT NULL` — variable-length text; `NOT NULL` forbids a nameless record.
    - `Phone VARCHAR(15)` — a phone number is a string of digits, not a quantity. Storing it as an integer would drop a leading zero and permit meaningless arithmetic.
    - `Email VARCHAR(100) UNIQUE` — an alternate key: no two customers may share an email, but it `may` be NULL, unlike the primary key.
    - `Join_Date DATE DEFAULT (CURRENT_DATE)` — the correct type for a date, so comparison and sorting work.

    Alternative ways of declaring the primary key
    ```sql
    -- named constraint, which produces clearer error messages
    CREATE TABLE Customer (
        CustomerID   INT,
        CustomerName VARCHAR(100) NOT NULL,
        CONSTRAINT pk_customer PRIMARY KEY (CustomerID)
    );

    -- auto-generated key
    CREATE TABLE Customer (
        CustomerID   INT PRIMARY KEY AUTO_INCREMENT,     -- MySQL
        CustomerName VARCHAR(100) NOT NULL
    );
    -- PostgreSQL: CustomerID SERIAL PRIMARY KEY
    -- SQL Server: CustomerID INT IDENTITY(1,1) PRIMARY KEY

    -- adding it later
    ALTER TABLE Customer ADD PRIMARY KEY (CustomerID);
    ```

    What the primary key prevents
    ```sql
    INSERT INTO Customer VALUES (101, 'Karim', ...);
    INSERT INTO Customer VALUES (101, 'Rahim', ...);
       -> ERROR 1062: Duplicate entry '101' for key 'PRIMARY'

    INSERT INTO Customer (CustomerID, CustomerName) VALUES (NULL, 'Sumi');
       -> ERROR 1048: Column 'CustomerID' cannot be null
    ```

    Inserting valid data
    ```sql
    INSERT INTO Customer (CustomerID, CustomerName, Address, Phone, Email, City) VALUES
      (101, 'Karim Ahmed', 'Dhanmondi, Dhaka', '01711111111', 'karim@mail.com', 'Dhaka'),
      (102, 'Rahim Uddin', 'Agrabad, Chattogram', '01822222222', 'rahim@mail.com', 'Chattogram');
    ```

    Verifying the structure
    ```sql
    DESCRIBE Customer;        -- MySQL
    \d Customer               -- PostgreSQL
    ```
    - Choosing the key: prefer one that is `short`, `numeric`, `never changes` and is `never NULL`. That is why a surrogate `CustomerID` is better than a natural key such as an email address or a national ID, both of which a person can change.

18. **What are the difference among DDL, DML and DCL?** *[NWPGCL Assistant Engineer (CSE) 2018 compact it 1213 (ET: N/A)]*

    Answer:

    | Point | DDL | DML | DCL |
    |---|---|---|---|
    | Full form | Data Definition Language | Data Manipulation Language | Data Control Language |
    | Acts on | The `structure` of the database | The `data` inside the tables | `Permissions` on the objects |
    | Commands | CREATE, ALTER, DROP, TRUNCATE, RENAME | INSERT, UPDATE, DELETE, SELECT | GRANT, REVOKE |
    | Auto-commit | `Yes` | `No` | `Yes` |
    | Rollback possible | No | `Yes` | No |
    | WHERE clause | Not used | Used | Not used |
    | Typical user | Database administrator, designer | Application, end user | Database administrator |
    | Affects | Table and column definitions | Rows and values | User and role privileges |
    | Stored in | The data dictionary | The table's data pages | The system privilege tables |
    | Purpose | Build the container | Fill and change it | Decide who may touch it |

    Examples of each

    `DDL`
    ```sql
    CREATE TABLE Employee (
        emp_id   INT PRIMARY KEY,
        emp_name VARCHAR(100) NOT NULL,
        salary   DECIMAL(10,2)
    );
    ALTER TABLE Employee ADD COLUMN email VARCHAR(100);
    TRUNCATE TABLE Employee;
    DROP TABLE Employee;
    ```

    `DML`
    ```sql
    INSERT INTO Employee VALUES (101, 'Karim', 50000);
    UPDATE Employee SET salary = salary * 1.10 WHERE emp_id = 101;
    DELETE FROM Employee WHERE emp_id = 101;
    SELECT emp_name, salary FROM Employee WHERE salary > 40000;
    ```

    `DCL`
    ```sql
    GRANT SELECT ON Employee TO clerk;
    GRANT SELECT, INSERT, UPDATE ON Employee TO manager;
    REVOKE INSERT, UPDATE ON Employee FROM manager;
    REVOKE ALL PRIVILEGES ON company.* FROM analyst;
    ```

    The fourth category usually asked with them — `TCL`
    ```sql
    BEGIN;
    UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';
    SAVEPOINT after_debit;
    UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';
    COMMIT;                     -- or ROLLBACK / ROLLBACK TO after_debit
    ```

    The distinction in one line each
    - `DDL` builds and reshapes the container.
    - `DML` puts things into it, changes them and takes them out.
    - `DCL` decides who is allowed to do either.
    - `TCL` decides when a set of DML changes becomes permanent.

    The point examiners test most
    - DDL and DCL are `auto-committed`; DML is not. A mistaken `DELETE` inside a transaction can be undone with `ROLLBACK`, but a mistaken `DROP TABLE` or `REVOKE` cannot.

## Transaction Management & ACID Properties (14)

1. **Explain the concept of ACID properties in a database transaction. Describe how each property—Atomicity, Consistency, Isolation, and Durability—ensures the reliability and integrity of a database system.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1425 (ET: E-Zone)]*

   Answer: A `transaction` is a single logical unit of work made up of one or more SQL statements, which must either complete entirely or have no effect at all. The `ACID` properties are the four guarantees a DBMS gives about every transaction.

   The standard example used throughout
   ```sql
   BEGIN;
   UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';   -- debit
   UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';   -- credit
   COMMIT;
   ```

   `A — Atomicity` (all or nothing)
   - A transaction is `indivisible`. Either every statement takes effect, or none does.
   - If the system crashes after the debit but before the credit, the debit is `undone` during recovery. Money is never destroyed by a failure.
   - Implemented by the `transaction log` and the `undo` mechanism: `COMMIT` makes the whole unit permanent, `ROLLBACK` reverses all of it.
   - Without atomicity, a crash mid-transfer would leave 5,000 taka missing from the bank.

   `C — Consistency` (valid state to valid state)
   - A transaction moves the database from one `consistent` state to another. Every integrity constraint — primary key, foreign key, CHECK, NOT NULL — and every business rule holds before it starts and after it finishes.
   - In the transfer, the total money in the two accounts must be the same afterwards as before. If a `CHECK (balance >= 0)` would be violated, the whole transaction is rejected.
   - Enforced jointly by the DBMS's constraints and by the application writing correct transactions.

   `I — Isolation` (concurrent transactions do not interfere)
   - Transactions running at the same time must produce the same result as if they had run `one after another` — a property called `serializability`.
   - Without it, three classic problems occur:
     - `Dirty read` — reading data another transaction wrote but has not committed.
     - `Non-repeatable read` — reading the same row twice and getting different values.
     - `Phantom read` — re-running a query and finding new rows that were not there before.
   - Implemented by `locking` (two-phase locking) or by `MVCC` (multi-version concurrency control).

   The four SQL isolation levels

   | Level | Dirty read | Non-repeatable read | Phantom read |
   |---|---|---|---|
   | Read Uncommitted | Possible | Possible | Possible |
   | Read Committed | Prevented | Possible | Possible |
   | Repeatable Read | Prevented | Prevented | Possible |
   | `Serializable` | Prevented | Prevented | Prevented |

   - Higher isolation gives more correctness and less concurrency. Most systems default to `Read Committed`; MySQL InnoDB defaults to `Repeatable Read`.

   `D — Durability` (committed means permanent)
   - Once a transaction has committed, its changes `survive` any subsequent failure — power loss, crash, or disk error.
   - Implemented by `write-ahead logging`: the log record is forced to stable storage `before` the data page is written, so recovery can `redo` any committed change that had not yet reached the data files.
   - Supported further by checkpoints, backups and replication.

   How the four fit together
   ```
   Atomicity   : all or nothing            -> protects against FAILURE mid-transaction
   Consistency : valid state to valid state -> protects the RULES of the data
   Isolation   : as if run one at a time    -> protects against CONCURRENCY
   Durability  : committed is permanent     -> protects against CRASH after commit
   ```

   Why they matter together
   - A bank transfer needs all four simultaneously. Atomicity stops the money vanishing, consistency stops the balances becoming invalid, isolation stops another transaction reading a half-completed transfer, and durability stops a power failure losing a committed deposit. Any one of them missing makes the system untrustworthy for financial data.
   - The trade-off is performance: strict isolation in particular reduces concurrency, which is why NoSQL systems often relax these guarantees to `BASE` — Basically Available, Soft state, Eventual consistency — accepting temporary inconsistency in exchange for scale.

2. **How many process of Transaction complete?** *[BREB Assistant Programmer (AP) 21.02.2025 compact it 1336 (ET: N/A)]*

   Answer: A transaction passes through `five` states, from the moment it begins to the moment it ends.

   The state diagram
   ```mermaid
   stateDiagram-v2
       [*] --> Active
       Active --> PartiallyCommitted : final statement executed
       Active --> Failed : error occurs
       PartiallyCommitted --> Committed : changes written to disk
       PartiallyCommitted --> Failed : failure during write
       Failed --> Aborted : rollback complete
       Committed --> [*]
       Aborted --> [*]
   ```

   ASCII form, as drawn in an examination
   ```
                       +-----------+
         BEGIN ------->|  ACTIVE   |
                       +-----+-----+
                       /           \
          last statement            error
                     /                 \
          +----------v--------+     +---v------+
          | PARTIALLY         |     |  FAILED  |
          | COMMITTED         |     +----+-----+
          +----------+--------+          |
                     |                   | rollback
          written to disk                |
                     |             +-----v-----+
          +----------v--------+    |  ABORTED  |
          |    COMMITTED      |    +-----------+
          +-------------------+
   ```

   The five states

   1. `Active`
   - The transaction is executing. This is the initial state, and it remains active while its statements run. All changes so far are held in buffers and are not yet permanent.

   2. `Partially Committed`
   - The `final statement` has executed, but the changes are still in memory and have not been written to disk. The transaction is not yet safe: a crash at this moment still loses it.

   3. `Committed`
   - The changes have been written permanently to stable storage. The transaction is complete and `cannot be rolled back`. This is where `durability` takes effect.

   4. `Failed`
   - An error has made normal execution impossible — a constraint violation, a deadlock, a system crash, or an explicit abort.

   5. `Aborted (Terminated)`
   - The rollback has finished and the database has been restored to the state it was in before the transaction started. The transaction may then be `restarted` (if the failure was transient, such as a deadlock) or `killed` (if it was a logic error).

   The SQL statements that move between the states
   ```sql
   BEGIN;                    -- enters the Active state
   UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';
   UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';
   SAVEPOINT after_transfer;  -- an intermediate marker
   COMMIT;                    -- Partially Committed -> Committed
   -- or
   ROLLBACK;                  -- Failed -> Aborted
   ROLLBACK TO after_transfer;-- undo part of the work, stay Active
   ```

   The point worth stating
   - The distinction between `Partially Committed` and `Committed` is where the whole recovery mechanism lives. Until the log record reaches stable storage, the transaction can still be lost; after it does, the DBMS is obliged to reproduce it even after a crash. That transition is what `write-ahead logging` exists to make safe.
   - Note that a transaction can `only` reach Committed from Partially Committed, and once Committed it can never move again — which is precisely what durability means.

3. **ACID এর প্রোপার্টি কি?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1450 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) `ACID` stands for `Atomicity, Consistency, Isolation, Durability` — the four properties that every database transaction must guarantee.

   Example used throughout — a bank transfer
   ```sql
   BEGIN;
   UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';
   UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';
   COMMIT;
   ```

   `A — Atomicity`
   - All or nothing. Either every statement in the transaction takes effect, or none does.
   - If the system fails after the debit but before the credit, the debit is `undone`. Money is never lost to a crash.
   - Implemented by the transaction log's `undo` records, with `COMMIT` and `ROLLBACK` as the controls.

   `C — Consistency`
   - The database moves from one `valid` state to another. Every constraint — primary key, foreign key, CHECK, NOT NULL — and every business rule holds before and after.
   - Here, the total money across the two accounts must be unchanged. A `CHECK (balance >= 0)` violation causes the whole transaction to be rejected.

   `I — Isolation`
   - Concurrent transactions must produce the same result as if they had run `one after another`.
   - Without it: `dirty read` (reading uncommitted data), `non-repeatable read` (the same row changing between two reads) and `phantom read` (new rows appearing).
   - Implemented by locking or MVCC, and controlled by the four isolation levels: Read Uncommitted, Read Committed, Repeatable Read and Serializable.

   `D — Durability`
   - Once committed, the changes `survive` any later failure — power loss, crash or disk error.
   - Implemented by `write-ahead logging`: the log record reaches stable storage before the data page does, so recovery can redo any committed change.

   Summary

   | Property | Guarantee | Protects against | Implemented by |
   |---|---|---|---|
   | `Atomicity` | All or nothing | Failure mid-transaction | Log, undo, ROLLBACK |
   | `Consistency` | Valid state to valid state | Invalid data | Constraints and correct application logic |
   | `Isolation` | As if run one at a time | Concurrency problems | Locking, MVCC |
   | `Durability` | Committed is permanent | Crash after commit | Write-ahead log, checkpoints |

   - The four are needed `together`. A bank transfer without atomicity loses money, without consistency produces invalid balances, without isolation lets another transaction read a half-finished transfer, and without durability loses a committed deposit in a power cut.

4. **(খ) Transaction কী? Transaction Management এর ACID properties সমূহ বর্ণনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 415 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   What a transaction is
   - A `transaction` is a single logical unit of work consisting of one or more SQL statements, which must either complete `entirely` or have `no effect at all`.
   - It is the unit at which the database guarantees correctness. The classic example is a bank transfer, in which a debit and a credit must succeed or fail together.
   ```sql
   BEGIN;
   UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';
   UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';
   COMMIT;
   ```
   - A transaction passes through five states: `Active` → `Partially Committed` → `Committed`, or `Active` → `Failed` → `Aborted`.

   The ACID properties

   `Atomicity`
   - The transaction is `indivisible` — all of it happens or none of it does.
   - If the system crashes between the debit and the credit, the debit is undone during recovery, so money is never destroyed.
   - Implemented by the transaction log's undo records; controlled by `COMMIT` and `ROLLBACK`.

   `Consistency`
   - The database moves from one `valid` state to another. Every integrity constraint and business rule holds before and after the transaction.
   - In the transfer, the total across both accounts must be unchanged. A violation of `CHECK (balance >= 0)` aborts the whole transaction.
   - Enforced jointly by the DBMS constraints and by correctly written application logic.

   `Isolation`
   - Concurrent transactions must behave as though they ran `one after another` — the property called `serializability`.
   - Without it, three problems appear: `dirty read`, `non-repeatable read` and `phantom read`.
   - Implemented by two-phase locking or by MVCC. The SQL standard defines four isolation levels:

   | Level | Dirty read | Non-repeatable read | Phantom |
   |---|---|---|---|
   | Read Uncommitted | Possible | Possible | Possible |
   | Read Committed | No | Possible | Possible |
   | Repeatable Read | No | No | Possible |
   | Serializable | No | No | No |

   `Durability`
   - Once `COMMIT` returns, the changes are permanent and survive any later crash.
   - Implemented by `write-ahead logging` — the log record reaches stable storage before the data page — together with checkpoints, backups and replication.

   How they work together
   ```
   Atomicity   -> protects against a failure in the middle
   Consistency -> protects the rules of the data
   Isolation   -> protects against interference from other transactions
   Durability  -> protects against a crash after commit
   ```

   The trade-off worth stating
   - Strict isolation in particular costs concurrency, because locks make transactions wait. This is why many distributed and NoSQL systems relax ACID to `BASE` — Basically Available, Soft state, Eventual consistency — accepting temporary inconsistency in exchange for scale and availability. For financial data, that trade is not acceptable, which is why banks stay with ACID.

5. **Case Study type Database-related problem (Solve: ACID)** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 321 (ET: N/A)]*

   Answer: The case study was not printed, so the standard ACID case study — a bank transfer — is worked through in full, which is what these questions invariably present.

   The scenario
   > Karim transfers 5,000 taka from account A101 to account A102. A101 holds 20,000 and A102 holds 8,000. Explain how the DBMS guarantees correctness.

   The transaction
   ```sql
   BEGIN;
   UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';   -- step 1
   UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';   -- step 2
   COMMIT;
   ```

   `Problem 1 — the system crashes after step 1`
   ```
   A101 = 15000   (debited)
   A102 =  8000   (not yet credited)
   Total = 23000, but it was 28000 -> 5000 taka has vanished
   ```
   - `Atomicity` solves it. The transaction never committed, so during recovery the DBMS reads the undo log and reverses step 1. A101 returns to 20,000 and the customer simply retries.

   `Problem 2 — the account would go negative`
   ```
   Karim tries to transfer 25000 from an account holding 20000
   ```
   - `Consistency` solves it. The constraint `CHECK (balance >= 0)` is violated by step 1, so the DBMS aborts the entire transaction. The database is never left in an invalid state.
   ```sql
   ALTER TABLE Account ADD CONSTRAINT chk_bal CHECK (balance >= 0);
   ```

   `Problem 3 — another transaction reads the half-finished transfer`
   ```
   T1: debit A101 (15000)  ...
   T2: reads A101 = 15000 and A102 = 8000, reports a total of 23000
   T1: credit A102, COMMIT
   ```
   - T2 saw money that momentarily existed nowhere. This is a `dirty read` if T1 had not committed.
   - `Isolation` solves it. At `Read Committed` or above, T2 cannot see T1's uncommitted changes; at `Serializable`, the two behave exactly as though they had run one after the other.

   `Problem 4 — power failure immediately after COMMIT`
   ```
   COMMIT returns to the user, then the server loses power
   ```
   - `Durability` solves it. `Write-ahead logging` forced the log record to disk `before` COMMIT returned, so on restart the DBMS `redoes` the change from the log. The customer's receipt is honoured.

   The complete solution
   ```sql
   BEGIN;

   UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';
   -- constraint CHECK (balance >= 0) fires here if funds are insufficient

   UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';

   INSERT INTO Transaction_Log (acc_no, txn_type, amount, txn_time)
   VALUES ('A101', 'Transfer Out', 5000, NOW()),
          ('A102', 'Transfer In',  5000, NOW());

   COMMIT;
   ```

   Which property answers which failure

   | What goes wrong | Property that prevents it | Mechanism |
   |---|---|---|
   | Crash between the two updates | `Atomicity` | Undo log, ROLLBACK |
   | Balance would go negative | `Consistency` | CHECK constraint |
   | Another user reads a half-done transfer | `Isolation` | Locking or MVCC |
   | Power cut just after COMMIT | `Durability` | Write-ahead log, redo |

   - The lesson the case study is designed to teach: all four are needed `simultaneously`. Removing any one of them makes the system unusable for money.

6. **What are the ACID properties of transaction to ensure data reliability and integrity?** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 472 (ET: N/A)]*

   Answer: The `ACID` properties are the four guarantees a DBMS gives about every transaction, and together they are what make a database trustworthy for data such as money and medical records.

   `Atomicity` — all or nothing
   - A transaction is `indivisible`: either every one of its statements takes effect, or none does.
   - Reliability role: a failure in the middle can never leave the data half-changed.
   ```sql
   BEGIN;
   UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';
   -- crash here
   UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';
   COMMIT;
   ```
   - Recovery reads the undo log and reverses the debit, so the 5,000 taka is not lost.

   `Consistency` — valid state to valid state
   - Every integrity constraint and business rule holds before the transaction starts and after it finishes.
   - Reliability role: the data can never become invalid, whatever the application does.
   ```sql
   CHECK (balance >= 0)          -- an overdraft is rejected, aborting the transaction
   FOREIGN KEY (dept_id) ...     -- an order cannot reference a customer who does not exist
   ```

   `Isolation` — as if run one at a time
   - Concurrent transactions produce the same result as some serial order of them.
   - Reliability role: one user's half-finished work is never visible to another.
   - The three problems it prevents:
   ```
   Dirty read          : T2 reads data T1 wrote but has not committed
   Non-repeatable read : T2 reads the same row twice and gets different values
   Phantom read        : T2 repeats a query and finds new rows
   ```
   - Implemented by two-phase locking or MVCC, and tuned through the four isolation levels.

   `Durability` — committed means permanent
   - Once `COMMIT` returns, the changes survive any subsequent crash, power failure or disk error.
   - Reliability role: a customer holding a receipt can rely on the transaction having happened.
   - Implemented by `write-ahead logging`: the log record is forced to stable storage before COMMIT returns, so recovery can `redo` the change.

   Summary

   | Property | Guarantee | Failure it prevents | Mechanism |
   |---|---|---|---|
   | Atomicity | All or nothing | Partial update after a crash | Undo log, ROLLBACK |
   | Consistency | Valid to valid | Invalid or corrupt data | Constraints, triggers |
   | Isolation | As if serial | Interference between users | Locking, MVCC |
   | Durability | Permanent once committed | Losing committed work | Write-ahead log, redo |

   Why all four are needed together
   - Take away `atomicity` and money disappears in a crash. Take away `consistency` and balances become negative. Take away `isolation` and two ATMs withdraw the same funds twice. Take away `durability` and a committed deposit is lost in a power cut. No three of them are sufficient.
   - The cost is performance, particularly from isolation, which is why some distributed systems adopt `BASE` instead — accepting eventual rather than immediate consistency in exchange for availability and scale.

7. **(a) What is ACID mean in database system?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 492 (ET: N/A)]*

   Answer: `ACID` is the set of four properties that a database transaction must satisfy: `Atomicity, Consistency, Isolation and Durability`.

   A `transaction` is a single logical unit of work made of one or more SQL statements, which must either complete entirely or have no effect at all.

   `A — Atomicity`
   - All or nothing. The transaction is indivisible.
   - If a bank transfer debits one account and the system crashes before crediting the other, the debit is undone during recovery.
   - Implemented by the transaction log's `undo` records; controlled by `COMMIT` and `ROLLBACK`.

   `C — Consistency`
   - The database moves from one `valid` state to another. All integrity constraints and business rules hold both before and after.
   - In a transfer, the total money must be unchanged; a `CHECK (balance >= 0)` violation aborts the whole transaction.

   `I — Isolation`
   - Concurrent transactions behave as though they had run `one after another`.
   - Prevents `dirty reads`, `non-repeatable reads` and `phantom reads`.
   - Implemented by locking or MVCC; tuned by the four isolation levels — Read Uncommitted, Read Committed, Repeatable Read, Serializable.

   `D — Durability`
   - Once committed, the changes survive any later crash or power failure.
   - Implemented by `write-ahead logging`, where the log record reaches stable storage before COMMIT returns.

   Illustration
   ```sql
   BEGIN;
   UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';
   UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';
   COMMIT;
   ```
   ```
   Atomicity   : both updates happen, or neither does
   Consistency : total money before = total money after
   Isolation   : no other transaction sees the intermediate state
   Durability  : after COMMIT, a power cut cannot undo it
   ```

   Summary

   | Letter | Property | Guarantee |
   |---|---|---|
   | A | Atomicity | All or nothing |
   | C | Consistency | Valid state to valid state |
   | I | Isolation | As if executed serially |
   | D | Durability | Permanent once committed |

   - The term was coined by Theo Härder and Andreas Reuter in 1983, building on Jim Gray's earlier work on transactions.
   - The contrast worth knowing: many NoSQL systems adopt `BASE` — Basically Available, Soft state, Eventual consistency — trading strict ACID guarantees for availability and horizontal scale. That trade is acceptable for a social media feed and unacceptable for a bank ledger.

8. **(গ) ডাটাবেস ট্রানজেকশনের ACID Properties সম্পর্কে লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 626 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) A `transaction` is a single logical unit of work that must complete entirely or have no effect at all. The `ACID` properties are the four guarantees the DBMS makes about it.

   `Atomicity` — all or nothing
   - The transaction is indivisible. Either all its statements take effect or none do.
   ```sql
   BEGIN;
   UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';
   -- crash here
   UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';
   COMMIT;
   ```
   - Recovery reads the `undo log` and reverses the debit, so no money is lost.

   `Consistency` — valid state to valid state
   - Every integrity constraint and business rule holds before and after the transaction.
   - The total money in the two accounts must be unchanged. A `CHECK (balance >= 0)` violation aborts the whole transaction.

   `Isolation` — as if executed one at a time
   - Concurrent transactions must yield the same result as some serial order of them.
   - Prevents three problems:
   ```
   Dirty read          : reading data another transaction has not committed
   Non-repeatable read : the same row gives different values when read twice
   Phantom read        : a repeated query returns rows that were not there before
   ```
   - Implemented by `two-phase locking` or `MVCC`, and controlled by four isolation levels:

   | Level | Dirty | Non-repeatable | Phantom |
   |---|---|---|---|
   | Read Uncommitted | Yes | Yes | Yes |
   | Read Committed | No | Yes | Yes |
   | Repeatable Read | No | No | Yes |
   | Serializable | No | No | No |

   `Durability` — permanent once committed
   - After `COMMIT` returns, the changes survive any crash or power failure.
   - Implemented by `write-ahead logging`: the log record is forced to disk before COMMIT returns, so recovery can `redo` the change.

   Summary

   | Property | Guarantee | Prevents | Mechanism |
   |---|---|---|---|
   | Atomicity | All or nothing | Half-completed work | Undo log, ROLLBACK |
   | Consistency | Valid to valid | Invalid data | Constraints |
   | Isolation | As if serial | Interference | Locks, MVCC |
   | Durability | Permanent | Losing committed work | Write-ahead log, redo |

   - All four are required together. Removing any one makes the database unusable for financial data, which is why relational systems retain ACID while many NoSQL systems relax it to `BASE` for scale.

9. **What do you mean by Rollback and Roll forward?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 682 (ET: N/A)]*

   Answer: `Rollback` and `roll forward` are the two recovery operations a DBMS performs after a failure, using the `transaction log`.

   Rollback (UNDO)
   - Reversing the changes made by a transaction, restoring the database to the state it was in before the transaction began.
   - Applied to transactions that were `active but not committed` when the failure occurred, and to any transaction the user explicitly aborts.
   - Uses the `undo` (before-image) records in the log: for each change, the old value is written back.

   ```sql
   BEGIN;
   UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';
   -- an error occurs, or the user changes their mind
   ROLLBACK;                     -- the debit is reversed
   ```

   - Partial rollback with a savepoint
   ```sql
   BEGIN;
   UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';
   SAVEPOINT after_debit;
   UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A999';   -- wrong account
   ROLLBACK TO after_debit;      -- undo only the second statement
   UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';   -- correct it
   COMMIT;
   ```

   Roll forward (REDO)
   - Reapplying the changes of transactions that `had committed` before the failure but whose data pages had not yet reached disk.
   - Uses the `redo` (after-image) records in the log: for each change, the new value is written again.
   - This is what makes `durability` real: `COMMIT` only guarantees that the log record is safe, not that the data page was written.

   ```
   Recovery after a crash:
      1. Read the log from the last checkpoint
      2. REDO   every committed transaction   -> roll forward
      3. UNDO   every uncommitted transaction -> rollback
      4. The database is now consistent
   ```

   Comparison

   | Point | Rollback (UNDO) | Roll forward (REDO) |
   |---|---|---|
   | Direction | Backward in time | Forward in time |
   | Applied to | Uncommitted transactions | Committed transactions |
   | Log record used | Before-image (old value) | After-image (new value) |
   | Purpose | Preserve `atomicity` | Preserve `durability` |
   | Triggered by | Error, user abort, deadlock, crash recovery | Crash recovery, restoring from backup |
   | Result | The change never happened | The change is reapplied |

   Roll forward in backup and recovery
   - The other common use: restore last night's full backup, then `roll forward` through the archived logs to bring the database up to the moment just before the failure. This is `point-in-time recovery`.
   ```
   Full backup (Sunday) ---> apply logs Mon, Tue, Wed ---> state at Wednesday 14:32
   ```

   The illustration that ties them together
   ```
   Log:  T1 begin ... T1 commit ... T2 begin ... [CRASH]

   Recovery:
      T1 committed but its pages may not be on disk  -> ROLL FORWARD (redo T1)
      T2 was still active                             -> ROLL BACK (undo T2)
   ```
   - In short: `roll forward makes committed work permanent, rollback makes uncommitted work disappear`. Together they restore the database to a state that satisfies both atomicity and durability.

10. **Describe ACID properties of DBMS.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 860 (ET: N/A)]*

    Answer: The `ACID` properties are the four guarantees a DBMS makes about every transaction — a transaction being a single logical unit of work that must complete entirely or not at all.

    `Atomicity`
    - All or nothing. Either every statement of the transaction takes effect or none does.
    - If a bank transfer debits one account and the system crashes before crediting the other, recovery reads the `undo log` and reverses the debit. Money is never destroyed by a failure.
    - Controlled by `COMMIT` and `ROLLBACK`.

    `Consistency`
    - The database moves from one `valid` state to another. Every constraint — primary key, foreign key, CHECK, NOT NULL — and every business rule holds before and after.
    - In a transfer, the total across both accounts must be unchanged. A `CHECK (balance >= 0)` violation aborts the entire transaction.
    - Enforced jointly by the DBMS's constraints and by correctly written application logic.

    `Isolation`
    - Concurrent transactions behave as though they had run `one after another` — the property called `serializability`.
    - Without it three problems arise:
    ```
    Dirty read          : T2 reads what T1 wrote but has not committed
    Non-repeatable read : T2 reads a row twice and gets different values
    Phantom read        : T2 repeats a query and new rows have appeared
    ```
    - Implemented by `two-phase locking` (a growing phase acquiring locks, a shrinking phase releasing them) or by `MVCC`, which gives each transaction a consistent snapshot instead of blocking readers.

    `Durability`
    - Once `COMMIT` returns, the changes are permanent and survive any subsequent crash, power failure or disk error.
    - Implemented by `write-ahead logging`: the log record is forced to stable storage `before` the data page is written and before COMMIT returns, so recovery can `redo` the change.
    - Supported further by checkpoints, backups and replication.

    Worked illustration
    ```sql
    BEGIN;
    UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';
    UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';
    COMMIT;
    ```
    ```
    Atomicity   : both updates, or neither
    Consistency : 28000 total before, 28000 total after
    Isolation   : no other session sees the intermediate 23000
    Durability  : a power cut after COMMIT cannot undo it
    ```

    Summary

    | Property | Guarantee | Mechanism |
    |---|---|---|
    | Atomicity | All or nothing | Undo log, ROLLBACK |
    | Consistency | Valid state to valid state | Constraints, triggers |
    | Isolation | As if serial | 2PL or MVCC |
    | Durability | Permanent once committed | Write-ahead log, redo, checkpoints |

    - The cost is concurrency: strict isolation makes transactions wait for locks. That is why many distributed systems relax ACID to `BASE` — Basically Available, Soft state, Eventual consistency — which is acceptable for a social feed but not for a bank ledger.

11. **A transaction consists of a sequence of query and/or update statements. SQL statement must be required to end the transaction. List the SQL statements, required to end the transaction and also write their functions.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 984-985 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

    Answer: The SQL statements that end a transaction are `COMMIT` and `ROLLBACK`. `SAVEPOINT` and `SET TRANSACTION` are used within one.

    `COMMIT`
    ```sql
    COMMIT;
    COMMIT WORK;        -- the full standard form
    ```
    - Function: makes all the changes of the current transaction `permanent` and visible to other users.
    - It ends the transaction successfully. Once it returns, the changes are `durable` — they survive any subsequent crash, because the log record was forced to stable storage first.
    - All locks held by the transaction are released, and the changes can no longer be rolled back.

    `ROLLBACK`
    ```sql
    ROLLBACK;
    ROLLBACK WORK;
    ```
    - Function: `undoes` every change made by the current transaction, restoring the database to the state it was in when the transaction began.
    - It ends the transaction unsuccessfully, releases all its locks, and preserves `atomicity` by ensuring the partial work leaves no trace.
    - The DBMS also issues an implicit rollback automatically on a deadlock, a constraint violation, or a system crash.

    `SAVEPOINT` — a partial marker within a transaction
    ```sql
    SAVEPOINT savepoint_name;
    ROLLBACK TO savepoint_name;
    RELEASE SAVEPOINT savepoint_name;
    ```
    - Function: marks an intermediate point so that part of a transaction can be undone without abandoning all of it. `ROLLBACK TO` does not end the transaction — it remains active.

    `SET TRANSACTION` — sets the properties of the transaction
    ```sql
    SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
    SET TRANSACTION READ ONLY;
    ```

    A worked example using all of them
    ```sql
    BEGIN;                                       -- or START TRANSACTION

    UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';

    SAVEPOINT after_debit;                        -- intermediate marker

    UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A999';   -- wrong account

    ROLLBACK TO after_debit;                      -- undo only the second update
                                                  -- the transaction is still ACTIVE

    UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';   -- correct it

    COMMIT;                                       -- ENDS the transaction, permanently
    ```

    Summary

    | Statement | Function | Ends the transaction? |
    |---|---|---|
    | `COMMIT` | Makes all changes permanent | `Yes`, successfully |
    | `ROLLBACK` | Undoes all changes | `Yes`, unsuccessfully |
    | `ROLLBACK TO savepoint` | Undoes changes made after the savepoint | No — still active |
    | `SAVEPOINT` | Marks a point to return to | No |
    | `SET TRANSACTION` | Sets isolation level or read-only mode | No |

    Points worth remembering
    - `DDL statements auto-commit`. Running `CREATE TABLE` in the middle of a transaction silently commits everything before it, which is a frequent and painful surprise.
    - Many client tools run in `autocommit` mode, where every statement is its own transaction. Explicit `BEGIN` turns that off for the duration.
    - After `COMMIT` there is no way back, which is why an important change should be verified with a `SELECT` while the transaction is still open.

12. **Describe Database ACID properties.** *[RAKUB Assistant Database Administrator 2020 compact it 1012 (ET: E-Zone)]*

    Answer: A `transaction` is one logical unit of work — a group of SQL statements that must succeed or fail together. `ACID` is the set of four properties the DBMS guarantees for every transaction.

    `A — Atomicity`
    - All or nothing. Either every statement of the transaction takes effect, or none of them does.
    - A transfer debits one account and credits another. If the system crashes between the two, recovery reads the `undo log` and reverses the debit, so money is never lost or created.
    - Statements: `COMMIT` makes the work permanent, `ROLLBACK` erases it.

    `C — Consistency`
    - The database moves from one `valid` state to another. Every constraint — primary key, foreign key, `CHECK`, `NOT NULL` — and every business rule holds before and after.
    - In a transfer the sum of the two balances must be unchanged. A `CHECK (balance >= 0)` violation aborts the whole transaction.

    `I — Isolation`
    - Concurrent transactions must produce the same result as if they had run `one after another`. This is called `serializability`.
    - Without it three anomalies occur:
    ```
    Dirty read          : reading data another transaction has not committed
    Non-repeatable read : the same row gives a different value when read again
    Phantom read        : a repeated query returns rows that were not there before
    ```
    - Enforced by `two-phase locking` — a growing phase that only acquires locks and a shrinking phase that only releases them — or by `MVCC`, which gives each transaction a snapshot so readers never block writers.
    - Four standard levels trade safety for speed:

    | Level | Dirty | Non-repeatable | Phantom |
    |---|---|---|---|
    | Read Uncommitted | Yes | Yes | Yes |
    | Read Committed | No | Yes | Yes |
    | Repeatable Read | No | No | Yes |
    | Serializable | No | No | No |

    `D — Durability`
    - Once `COMMIT` returns, the changes are permanent and survive a crash, a power cut or a disk failure.
    - Implemented by `write-ahead logging`: the log record reaches stable storage before the data page is written and before COMMIT returns, so recovery can `redo` the change.

    Worked example
    ```sql
    BEGIN;
    UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';
    UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';
    COMMIT;
    ```
    ```
    Atomicity   : both updates or neither
    Consistency : total across the two accounts stays the same
    Isolation   : no other session sees the money "in the air"
    Durability  : a power failure after COMMIT cannot undo it
    ```
    - The price of ACID is concurrency, since strict isolation makes transactions wait for locks. That is why many distributed NoSQL systems relax it to `BASE` — Basically Available, Soft state, Eventual consistency — acceptable for a news feed but not for a bank ledger.

13. **Describe the ACID properties in a database. When does a deadlock occur and how do you prevent it, in a database?** *[Combined Bank Senior Officer (IT/ICT) 2019 compact it 1116 (ET: DU)]*

    Answer: Part 1 — the ACID properties

    `Atomicity` — all or nothing. Either every statement of the transaction takes effect or none does. If a transfer debits one account and the system crashes before the credit, recovery uses the `undo log` to reverse the debit.

    `Consistency` — the database goes from one valid state to another. All constraints and business rules hold before and after, so the total money across the two accounts never changes.

    `Isolation` — concurrent transactions behave as if run one at a time (`serializability`). It prevents dirty reads, non-repeatable reads and phantom reads, and is enforced by `two-phase locking` or `MVCC`.

    `Durability` — once `COMMIT` returns, the changes survive any crash. Implemented by `write-ahead logging`: the log record is forced to disk before COMMIT returns.

    Part 2 — when a deadlock occurs

    A `deadlock` is when two or more transactions each hold a lock the other one needs, so all of them wait forever and none can finish.

    ```
    T1                                T2
    LOCK Account   (granted)          LOCK Loan      (granted)
    request LOCK Loan  ---- waits for T2
                                      request LOCK Account ---- waits for T1
            both wait forever = DEADLOCK
    ```

    ```mermaid
    flowchart LR
        T1[Transaction T1] -->|waits for lock on Loan| T2[Transaction T2]
        T2 -->|waits for lock on Account| T1
    ```

    Four conditions must all hold at once (Coffman conditions):
    - `Mutual exclusion` — a lock is held by only one transaction at a time.
    - `Hold and wait` — a transaction keeps its locks while asking for more.
    - `No preemption` — a lock cannot be taken away by force.
    - `Circular wait` — a closed chain of transactions, each waiting on the next.

    Part 3 — how to prevent it

    Timestamp-based prevention — every transaction gets a timestamp, and older means higher priority. Breaking the circular wait is what makes deadlock impossible.

    | Scheme | T1 (older) needs a lock held by T2 (younger) | T2 (younger) needs a lock held by T1 (older) |
    |---|---|---|
    | `Wait-Die` (non-preemptive) | T1 waits | T2 dies — aborts and restarts with its old timestamp |
    | `Wound-Wait` (preemptive) | T1 wounds T2 — T2 is aborted | T2 waits |

    Other practical methods:
    - `Lock ordering` — every transaction acquires locks in the same fixed order, for example always Account then Loan. A cycle then cannot form. This is the simplest and most effective fix in application code.
    - `Acquire all locks at once` at the start, which removes the hold-and-wait condition.
    - `Lock timeout` — a transaction that waits longer than a set time is rolled back automatically. Simple, but it can abort transactions that were not deadlocked.
    - `Keep transactions short` and touch the fewest rows possible, so the window for a conflict is small.

    Detection instead of prevention
    - Most real systems (Oracle, SQL Server, PostgreSQL, MySQL InnoDB) let deadlocks happen and then detect them. The DBMS builds a `wait-for graph` with one node per transaction and an edge Ti → Tj when Ti waits for a lock held by Tj. A `cycle` in the graph means a deadlock.
    - The system then picks a `victim` — usually the transaction with the least work done or the fewest locks — rolls it back, releases its locks and lets the others proceed. The application should catch the deadlock error and simply retry.

14. **Describe the ACID properties of database.** *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1219 (ET: N/A)]*

    Answer: A `transaction` is one logical unit of work whose statements must all succeed or all fail. `ACID` is the four guarantees a DBMS gives every transaction, proposed by Härder and Reuter in 1983.

    `Atomicity` — all or nothing
    - Either every statement of the transaction takes effect or none of them does. There is no half-done transaction.
    - A crash in the middle of a bank transfer is undone from the `undo log`, so the debit without the matching credit never survives.
    - Under the control of `COMMIT` and `ROLLBACK`.

    `Consistency` — valid state to valid state
    - Every integrity constraint and business rule holds both before and after the transaction: primary key, foreign key, `CHECK`, `NOT NULL`, triggers.
    - The total of the two account balances must be the same after the transfer as before it.

    `Isolation` — as if run one at a time
    - Transactions running at the same time give the same result as some serial order of them, a property called `serializability`.
    - It stops three anomalies:
    ```
    Dirty read          : T2 reads a value T1 wrote but never committed
    Non-repeatable read : T2 reads a row twice and gets two different values
    Phantom read        : T2 repeats a query and finds new rows have appeared
    ```
    - Enforced by `two-phase locking` (locks are only acquired in a growing phase, only released in a shrinking phase) or by `MVCC`, which shows each transaction a consistent snapshot.

    `Durability` — permanent once committed
    - After `COMMIT` returns, the changes survive a crash, a power failure or a restart.
    - Implemented by `write-ahead logging`: the log record is forced to stable storage before COMMIT returns, so recovery can `redo` the change even if the data page never reached disk. Checkpoints and backups support this.

    Example
    ```sql
    BEGIN;
    UPDATE Account SET balance = balance - 5000 WHERE acc_no = 'A101';
    UPDATE Account SET balance = balance + 5000 WHERE acc_no = 'A102';
    COMMIT;
    ```

    | Property | What it guarantees here | Mechanism |
    |---|---|---|
    | Atomicity | Both updates or neither | Undo log, ROLLBACK |
    | Consistency | Total balance unchanged | Constraints |
    | Isolation | Nobody sees the money mid-flight | 2PL or MVCC |
    | Durability | A power cut after COMMIT cannot undo it | Write-ahead log, redo |

    - ACID is what makes a relational database trustworthy for banking, ticketing and accounting. Systems that need extreme scale often relax it to `BASE` — Basically Available, Soft state, Eventual consistency.

## Relational Data Model & ER Relationships (14)

1. What are the different types of relationships in a relational database? Explain each with examples. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer: A `relationship` is a link between two tables, created by a foreign key. There are three types, decided by how many rows on one side can match how many rows on the other.

   (a) One-to-One (1:1)
   - One row in table A matches at most one row in table B, and the reverse is also true.
   - Example: `Employee` and `EmployeePassport`. One employee has one passport, one passport belongs to one employee.
   - Implementation: put the foreign key in either table and mark it `UNIQUE`.
   ```sql
   CREATE TABLE Passport (
     passport_no VARCHAR(15) PRIMARY KEY,
     emp_id      INT UNIQUE REFERENCES Employee(emp_id)
   );
   ```
   - Used to split rarely used or sensitive columns into a separate table.

   (b) One-to-Many (1:N)
   - One row in table A matches many rows in table B, but each row in B matches only one row in A.
   - Example: one `Department` has many `Employee` rows; each employee works in one department.
   - Implementation: put the foreign key on the `many` side. This is the most common relationship.
   ```sql
   CREATE TABLE Employee (
     emp_id  INT PRIMARY KEY,
     dept_id INT REFERENCES Department(dept_id)
   );
   ```

   (c) Many-to-Many (M:N)
   - Many rows in A match many rows in B.
   - Example: a `Student` takes many `Course` rows, and a course has many students.
   - Implementation: a relational table cannot store this directly, so a third table — a `junction` or `bridge` table — is created. Its primary key is the pair of foreign keys.
   ```sql
   CREATE TABLE Enrollment (
     student_id INT REFERENCES Student(student_id),
     course_id  INT REFERENCES Course(course_id),
     grade      CHAR(2),
     PRIMARY KEY (student_id, course_id)
   );
   ```

   ```mermaid
   erDiagram
       DEPARTMENT ||--o{ EMPLOYEE : "has"
       EMPLOYEE ||--|| PASSPORT : "holds"
       STUDENT ||--o{ ENROLLMENT : "takes"
       COURSE ||--o{ ENROLLMENT : "has"
   ```

   Summary

   | Type | Rule | Example | How it is stored |
   |---|---|---|---|
   | 1:1 | One matches one | Employee — Passport | Foreign key with `UNIQUE` |
   | 1:N | One matches many | Department — Employee | Foreign key on the many side |
   | M:N | Many match many | Student — Course | Junction table with two foreign keys |

   - A fourth case is the `self-relationship` (unary), where a table refers to itself — for example `Employee.manager_id` pointing to `Employee.emp_id`.

2. **Discuss about different types of relations in DBMS.** *[Combined Bank Assistant Programmer 09.02.2024 compact it 297 (ET: BIBM)]*

   Answer: The word `relation` has two meanings in DBMS, and both are asked in exams.

   Part 1 — a relation as a table
   - In the relational model a `relation` is a table: a set of rows (tuples) over a fixed set of columns (attributes).
   - Its `degree` is the number of columns and its `cardinality` is the number of rows.

   Types of relations
   - `Base relation` — a real table stored on disk, created by `CREATE TABLE`.
   - `View` (virtual relation) — not stored; it is a saved `SELECT` computed when used.
   - `Derived relation` — the result of a query such as a join or a projection.
   - `Snapshot` / materialised view — the result of a query that `is` stored, refreshed periodically.
   - `Temporary relation` — exists only for the current session or query.

   Part 2 — relations between tables
   - More often the question means the `relationship` between two tables, created by a foreign key. There are three.

   `One-to-One (1:1)`
   - One row on each side. Example: `Employee` and `Passport`.
   - Stored as a foreign key marked `UNIQUE`.

   `One-to-Many (1:N)`
   - One row on the left matches many on the right. Example: one `Department` has many `Employee` rows.
   - Stored as a foreign key on the `many` side. This is the most common type.

   `Many-to-Many (M:N)`
   - Many rows on both sides. Example: a `Student` takes many `Course` rows and a course has many students.
   - Cannot be stored directly. A third `junction table` is created whose primary key is the pair of foreign keys.

   ```sql
   CREATE TABLE Enrollment (
     student_id INT REFERENCES Student(student_id),
     course_id  INT REFERENCES Course(course_id),
     PRIMARY KEY (student_id, course_id)
   );
   ```

   ```mermaid
   erDiagram
       DEPARTMENT ||--o{ EMPLOYEE : has
       STUDENT ||--o{ ENROLLMENT : takes
       COURSE ||--o{ ENROLLMENT : has
   ```

   By degree — the number of entity types taking part
   - `Unary` (recursive) — an entity related to itself, such as `Employee.manager_id` pointing back to `Employee`.
   - `Binary` — two entity types. Almost all real relationships are binary.
   - `Ternary` — three entity types, such as Supplier–Part–Project.
   - `N-ary` — n entity types; rare, and usually broken into binary ones.

3. **What is the degree of relation in dbms?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

   Answer: The word `degree` is used in two different senses, so the answer depends on which one the question means. Both are given below.

   (a) Degree of a relation (a table)
   - The `degree` of a relation is the `number of attributes (columns)` in it. It is also called the `arity` of the relation.
   - The number of rows is the `cardinality`, not the degree.

   ```
   Student(student_id, name, dept, cgpa)

      degree      = 4       (four columns)
      cardinality = 3       (three rows, in this example)

      student_id | name   | dept | cgpa
      -----------+--------+------+------
      101        | Rahim  | CSE  | 3.75
      102        | Karim  | EEE  | 3.40
      103        | Jamal  | CSE  | 3.90
   ```
   - A relation with degree 1 is `unary`, degree 2 is `binary`, degree 3 is `ternary`, degree n is `n-ary`.
   - The degree changes only when a column is added or dropped, so it is a property of the schema. The cardinality changes with every `INSERT` or `DELETE`, so it is a property of the data.

   (b) Degree of a relationship
   - The `degree of a relationship` is the `number of entity types taking part` in it.

   | Degree | Name | Meaning | Example |
   |---|---|---|---|
   | 1 | Unary (recursive) | An entity related to itself | An `Employee` manages another `Employee` |
   | 2 | Binary | Two entity types | `Student` enrolls in `Course` |
   | 3 | Ternary | Three entity types | `Supplier` supplies `Part` for `Project` |
   | n | N-ary | n entity types | Rare; usually broken into binary ones |

   ```mermaid
   erDiagram
       STUDENT ||--o{ ENROLLMENT : "binary"
       COURSE ||--o{ ENROLLMENT : "binary"
       EMPLOYEE ||--o{ EMPLOYEE : "unary - manages"
   ```

   - Do not confuse degree with cardinality. Degree counts `how many entity types` take part; cardinality (1:1, 1:N, M:N) says `how many instances` of one may relate to the other.

4. **(খ) One-to-one এবং One-to-many রিলেশন উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 614 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) `Cardinality` decides how many rows on one side of a relationship may match rows on the other side. One-to-one and one-to-many are two of its three forms.

   One-to-One (1:1)
   - One row in table A matches at most one row in table B, and one row in B matches at most one row in A.
   - Example: an `Employee` has exactly one `Passport`, and a passport belongs to exactly one employee.
   ```
   Employee                  Passport
   +--------+-------+        +-------------+--------+
   | emp_id | name  |        | passport_no | emp_id |
   +--------+-------+        +-------------+--------+
   | 101    | Rahim | -----> | BD1234567   | 101    |
   | 102    | Karim | -----> | BD7654321   | 102    |
   +--------+-------+        +-------------+--------+
   ```
   - Implementation: the foreign key is placed in either table and marked `UNIQUE`, which is what limits the match to one row.
   ```sql
   CREATE TABLE Passport (
     passport_no VARCHAR(15) PRIMARY KEY,
     emp_id      INT UNIQUE REFERENCES Employee(emp_id)
   );
   ```
   - Other examples: Person — NID, Country — Capital city, User — User profile.
   - Used mainly to move rarely read or sensitive columns into a separate table.

   One-to-Many (1:N)
   - One row in table A matches many rows in table B, but each row in B matches only one row in A.
   - Example: one `Department` has many `Employee` rows, while each employee works in one department.
   ```
   Department                Employee
   +---------+--------+      +--------+-------+---------+
   | dept_id | name   |      | emp_id | name  | dept_id |
   +---------+--------+      +--------+-------+---------+
   | 10      | CSE    | ---> | 101    | Rahim | 10      |
   |         |        | ---> | 102    | Karim | 10      |
   | 20      | EEE    | ---> | 103    | Jamal | 20      |
   +---------+--------+      +--------+-------+---------+
   ```
   - Implementation: the foreign key goes on the `many` side, with no `UNIQUE` on it.
   ```sql
   CREATE TABLE Employee (
     emp_id  INT PRIMARY KEY,
     name    VARCHAR(50),
     dept_id INT REFERENCES Department(dept_id)
   );
   ```
   - Other examples: Customer — Order, Author — Book, Teacher — Class.
   - This is the most common relationship in real databases.

   ```mermaid
   erDiagram
       EMPLOYEE ||--|| PASSPORT : "1:1 holds"
       DEPARTMENT ||--o{ EMPLOYEE : "1:N has"
   ```

   | Point | One-to-One | One-to-Many |
   |---|---|---|
   | Matching | One row to one row | One row to many rows |
   | Foreign key | In either table, `UNIQUE` | On the many side, not unique |
   | Example | Employee — Passport | Department — Employee |
   | How common | Rare | Very common |

5. **Weak Entity and strong entity difference with relation.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 660 (ET: N/A)]*

   Answer: An `entity` is a real-world object stored as a table. Entities are of two kinds, decided by whether the entity can identify itself.

   Strong entity
   - An entity that has its `own primary key`, so each of its rows can be identified without help from any other table.
   - Example: `Student(student_id, name)` — `student_id` alone identifies a student.
   - Drawn as a single rectangle in an ER diagram.

   Weak entity
   - An entity that has `no primary key of its own`. It depends on a strong entity — called its `owner` or identifying entity — for identification.
   - It has a `partial key` (discriminator), which is unique only within one owner.
   - Example: `Dependent(name, relation)` of an employee. Two employees may both have a son named "Rahim", so `name` alone is not unique. The key becomes `emp_id + name`.
   - Drawn as a double rectangle, and its partial key is underlined with a dashed line.

   The relation between them — the identifying relationship
   - The link joining a weak entity to its owner is the `identifying relationship`, drawn as a `double diamond`.
   - The weak entity has `total participation` — no dependent can exist without an employee — shown by a double line.
   - Its primary key = `owner's primary key + its own partial key`, so the foreign key is part of the primary key.
   - Deleting the owner row deletes all its weak rows, so `ON DELETE CASCADE` is the natural rule.

   ```
      +-----------+       /\/\        +==========+
      | EMPLOYEE  |------< HAS >======|| DEPENDENT ||
      +-----------+       \/\/        +==========+
       emp_id (PK)      identifying     name (partial key)
                        relationship
   ```

   ```sql
   CREATE TABLE Dependent (
     emp_id INT,
     name   VARCHAR(50),
     relation VARCHAR(20),
     PRIMARY KEY (emp_id, name),                 -- owner key + partial key
     FOREIGN KEY (emp_id) REFERENCES Employee(emp_id) ON DELETE CASCADE
   );
   ```

   | Point | Strong entity | Weak entity |
   |---|---|---|
   | Primary key | Has its own | Has none; only a partial key |
   | Identified by | Itself | Owner's key + partial key |
   | Existence | Independent | Depends on the owner |
   | ER symbol | Single rectangle | Double rectangle |
   | Relationship symbol | Single diamond | Double diamond (identifying) |
   | Participation | May be partial | Always total |
   | Example | Employee, Student | Dependent, Order line, Room in a building |

6. **(b) Give example of week and strong entity sets.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 694 (ET: N/A)]*

   Answer: A `strong entity set` has its own primary key and can be identified on its own. A `weak entity set` has no primary key of its own and depends on an owner entity for identification.

   Example 1 — Employee and Dependent
   - `Employee(emp_id, name, salary)` is strong: `emp_id` alone identifies a row.
   - `Dependent(name, age, relation)` is weak: two different employees may each have a son named "Rahim", so `name` is not unique on its own. Its key becomes `emp_id + name`.
   ```
      +-----------+      /\/\       +===============+
      | EMPLOYEE  |-----< HAS >=====||  DEPENDENT   ||
      +-----------+      \/\/       +===============+
       emp_id (PK)    identifying     name (partial key)
   ```

   Example 2 — Order and Order_Item
   - `Order(order_id, order_date)` is strong.
   - `Order_Item(line_no, qty, price)` is weak: line number 1 exists in every order, so it is unique only inside one order. Key = `order_id + line_no`.

   Example 3 — Building and Room
   - `Building(building_id, name)` is strong.
   - `Room(room_no, capacity)` is weak: room 101 exists in many buildings. Key = `building_id + room_no`.

   Example 4 — Bank Loan and Payment
   - `Loan(loan_no, amount)` is strong.
   - `Payment(payment_no, date, amount)` is weak: payment number 1 exists for every loan. Key = `loan_no + payment_no`.

   ```sql
   CREATE TABLE Order_Item (
     order_id INT,
     line_no  INT,
     qty      INT,
     PRIMARY KEY (order_id, line_no),            -- owner key + partial key
     FOREIGN KEY (order_id) REFERENCES Orders(order_id) ON DELETE CASCADE
   );
   ```

   Points to note
   - The weak entity is drawn as a `double rectangle` and its link to the owner as a `double diamond` (the identifying relationship).
   - The weak entity always has `total participation` — no dependent without an employee, no room without a building.
   - Deleting the owner must delete its weak rows, so `ON DELETE CASCADE` is used.

7. **(a) What is referential integrity? How do you impose in your database design?** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 795 (ET: N/A)]*

   Answer: `Referential integrity` is the rule that a foreign key value must either match an existing primary key value in the parent table or be `NULL`. It stops rows that point at something that does not exist.

   - Example: an `Employee` row with `dept_id = 50` is invalid if no department 50 exists in `Department`. Such a row is called an `orphan row`.
   - The child table is called the `referencing` table, the parent the `referenced` table.

   How it is imposed in a database design
   - Declare the foreign key when creating the table. The DBMS then enforces it automatically on every insert, update and delete.
   ```sql
   CREATE TABLE Department (
     dept_id   INT PRIMARY KEY,
     dept_name VARCHAR(50) NOT NULL
   );

   CREATE TABLE Employee (
     emp_id  INT PRIMARY KEY,
     name    VARCHAR(50),
     dept_id INT,
     CONSTRAINT fk_dept FOREIGN KEY (dept_id)
         REFERENCES Department(dept_id)
         ON DELETE SET NULL
         ON UPDATE CASCADE
   );
   ```
   - Add it to an existing table:
   ```sql
   ALTER TABLE Employee
   ADD CONSTRAINT fk_dept FOREIGN KEY (dept_id) REFERENCES Department(dept_id);
   ```

   What the DBMS then blocks
   ```
   INSERT INTO Employee VALUES (105, 'Rahim', 50);   -- rejected, dept 50 does not exist
   DELETE FROM Department WHERE dept_id = 10;        -- action depends on the rule below
   ```

   Referential actions — what happens when the parent row changes

   | Action | On delete or update of the parent |
   |---|---|
   | `NO ACTION` / `RESTRICT` | The operation is rejected while children exist (the default) |
   | `CASCADE` | The children are deleted, or their foreign key is updated too |
   | `SET NULL` | The child foreign key becomes `NULL` (the column must allow NULL) |
   | `SET DEFAULT` | The child foreign key takes its default value |

   Design rules to follow
   - The foreign key column and the referenced column must have the `same data type`.
   - The referenced column must be a `primary key` or have a `UNIQUE` constraint.
   - Index the foreign key column, otherwise every parent delete scans the whole child table.
   - Choose the action from the business rule: an order line has no meaning without its order, so `CASCADE`; an employee still exists after a department closes, so `SET NULL`.
   - Do the checking in the database, not only in the application. Application checks are bypassed by direct SQL, bulk loads and other programs.

8. **What is a weak entity for data modeling using the entity relationship model find out any weak entity and its identify relationship for the school database? Which of the following table? Student(student_id, student_name, admission_year) Teacher(teacher_id, teacher_name, teacher_joindate) Course(course_id, subject_name, credit)** *[BCC Assistant Programmer 12.02.2021 compact it 814 (ET: BUET)]*

   Answer: A `weak entity` is an entity that has no primary key of its own. It cannot be identified on its own, so it depends on a `strong` (owner) entity. It has only a `partial key` (discriminator), which is unique inside one owner, and its real primary key is `owner's primary key + partial key`. The relationship joining it to its owner is the `identifying relationship`, drawn as a double diamond, and the weak entity always has total participation.

   Answer to the question asked
   - None of the three tables given is a weak entity:
   ```
   Student(student_id, student_name, admission_year)   -> strong, key student_id
   Teacher(teacher_id, teacher_name, teacher_joindate) -> strong, key teacher_id
   Course(course_id, subject_name, credit)             -> strong, key course_id
   ```
   - Each has its own primary key, so each is a `strong entity`.

   The weak entity in a school database
   - The missing piece is `Enrollment` (the mark or grade a student gets in a course). A row like "the result of student 101 in course CSE101" has no identity of its own — remove the student or the course and it means nothing.
   - Its partial key is the `semester` or `exam_no`, unique only within one student–course pair.

   ```
      +-----------+     /\/\      +=================+     /\/\     +----------+
      |  STUDENT  |----< TAKES >==||   ENROLLMENT   ||===< FOR >---|  COURSE  |
      +-----------+     \/\/      +=================+     \/\/     +----------+
       student_id(PK)  identifying   semester              identifying course_id(PK)
                       relationship  (partial key)         relationship
   ```

   ```mermaid
   erDiagram
       STUDENT ||--o{ ENROLLMENT : takes
       COURSE  ||--o{ ENROLLMENT : "is taken as"
       TEACHER ||--o{ COURSE : teaches
   ```

   ```sql
   CREATE TABLE Enrollment (
     student_id  INT,
     course_id   INT,
     semester    VARCHAR(10),                  -- partial key
     grade       CHAR(2),
     PRIMARY KEY (student_id, course_id, semester),
     FOREIGN KEY (student_id) REFERENCES Student(student_id) ON DELETE CASCADE,
     FOREIGN KEY (course_id)  REFERENCES Course(course_id)  ON DELETE CASCADE
   );
   ```

   Other weak entities that fit a school database
   - `Class_Section` — section A exists in every class, so its key is `course_id + section_name`.
   - `Attendance` — identified by `student_id + class_date`.
   - `Dependent` of a teacher — identified by `teacher_id + name`.
   - In every case the pattern is the same: the child borrows the parent's key, and deleting the parent deletes the child, so `ON DELETE CASCADE` is used.

9. **(c) What is a weak entity set? How the primary key is generated for weak entity set?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 896 (ET: N/A)]*

   Answer: A `weak entity set` is a set of entities that has `no primary key of its own`. Its rows cannot be identified without the help of another entity, called the `owner` or identifying entity set.

   - Example: `Dependent(name, age, relation)` of an employee. Two employees may each have a son named "Rahim", so `name` alone cannot identify a row.
   - It is drawn as a `double rectangle`. The link to its owner is the `identifying relationship`, drawn as a `double diamond`.
   - It always has `total participation` in that relationship — no dependent can exist without an employee — shown by a double line.

   How the primary key is generated
   - The weak entity has a `partial key`, also called a `discriminator`: an attribute that is unique only `within one owner`. In an ER diagram it is underlined with a `dashed` line.
   - The primary key is then formed as:
   ```
      Primary key of weak entity =
           Primary key of the owner entity  +  Partial key (discriminator)
   ```
   - So `Dependent` gets `(emp_id, name)`. Employee 101's son Rahim and employee 102's son Rahim are now two different rows.

   ```
      +-----------+       /\/\        +================+
      | EMPLOYEE  |------< HAS >======||   DEPENDENT   ||
      +-----------+       \/\/        +================+
       emp_id (PK)     identifying      name (partial key, dashed underline)
                       relationship     PK = (emp_id, name)
   ```

   ```sql
   CREATE TABLE Dependent (
     emp_id   INT,                                   -- borrowed from the owner
     name     VARCHAR(50),                           -- partial key
     age      INT,
     relation VARCHAR(20),
     PRIMARY KEY (emp_id, name),                     -- owner key + partial key
     FOREIGN KEY (emp_id) REFERENCES Employee(emp_id) ON DELETE CASCADE
   );
   ```

   Points worth noting
   - The foreign key here is `part of the primary key`, which is what makes the entity weak. If the foreign key were an ordinary column, the entity would be strong.
   - The owner's key column must be `NOT NULL` in the weak table, since a primary key cannot contain NULL.
   - Deleting the owner must delete its weak rows, so `ON DELETE CASCADE` is the correct rule.
   - More examples: `Room` in a `Building` → `(building_id, room_no)`; `Order_Item` in an `Order` → `(order_id, line_no)`; `Payment` on a `Loan` → `(loan_no, payment_no)`.

10. **(a) Write down Integrity rules in database.** *[National University Assistant Programmer 2020 compact it 976 (ET: DU)]*

    Answer: `Integrity rules` are the conditions that keep the data in a database correct and meaningful. The relational model defines two rules that every DBMS must enforce, plus user-defined rules.

    1. Entity integrity
    - The `primary key of a table can never be NULL`, and it must be unique.
    - Reason: the primary key is what identifies a row. A NULL means "unknown", so a NULL key would leave a row that cannot be found or referenced.
    - If the key has several columns, `no column` in it may be NULL.
    ```sql
    CREATE TABLE Student (
      student_id INT PRIMARY KEY,            -- implicitly NOT NULL and UNIQUE
      name       VARCHAR(50) NOT NULL
    );
    INSERT INTO Student VALUES (NULL, 'Rahim');   -- rejected
    ```

    2. Referential integrity
    - A `foreign key value must match an existing primary key value in the parent table, or be NULL`.
    - Reason: it stops `orphan rows` that point at something that does not exist.
    ```sql
    CREATE TABLE Employee (
      emp_id  INT PRIMARY KEY,
      dept_id INT REFERENCES Department(dept_id) ON DELETE SET NULL
    );
    INSERT INTO Employee VALUES (101, 50);    -- rejected if department 50 does not exist
    ```
    - Referential actions decide what happens to the child when the parent is deleted or updated: `RESTRICT`, `CASCADE`, `SET NULL`, `SET DEFAULT`.

    3. Domain integrity
    - Every value in a column must belong to the column's `domain` — the right data type, range and format.
    - Enforced by the data type plus `CHECK`, `NOT NULL` and `DEFAULT`.
    ```sql
    age    INT CHECK (age BETWEEN 18 AND 60),
    gender CHAR(1) CHECK (gender IN ('M','F')),
    status VARCHAR(10) DEFAULT 'ACTIVE'
    ```

    4. Key integrity (uniqueness)
    - Any candidate key must stay unique. Enforced by `UNIQUE`.
    ```sql
    email VARCHAR(80) UNIQUE
    ```

    5. User-defined (business) integrity
    - Rules that come from the business and cannot be expressed by the four above. Enforced by `CHECK`, `triggers` or stored procedures.
    - Example: an account balance must not fall below the minimum, or a loan cannot be approved by the same officer who applied for it.

    Summary

    | Rule | What it protects | Enforced by |
    |---|---|---|
    | Entity integrity | Primary key is unique and never NULL | `PRIMARY KEY` |
    | Referential integrity | Foreign key matches a real parent row | `FOREIGN KEY` |
    | Domain integrity | Values fit the column's type and range | Data type, `CHECK`, `NOT NULL` |
    | Key integrity | Candidate keys stay unique | `UNIQUE` |
    | Business integrity | Company-specific rules | `CHECK`, triggers |

    - These rules must live `in the database`, not only in the application. Application checks are bypassed by direct SQL, bulk loads and other programs.

11. **What is constraints? Why use constraint? Difference between table level Cosntraint and column level Cosntraint.** *[RAKUB Assistant Database Administrator 2020 compact it 1015 (ET: E-Zone)]*

    Answer: A `constraint` is a rule attached to a table column that the DBMS enforces on every insert, update and delete. If a statement breaks the rule, the DBMS rejects it.

    Why constraints are used
    - They keep the data `accurate and valid` — no negative salary, no invalid grade.
    - They enforce `entity integrity` — the primary key is unique and never NULL.
    - They enforce `referential integrity` — no employee in a department that does not exist.
    - They stop `duplicate` values where duplicates are wrong, such as two accounts with the same email.
    - They put the rule in `one place`. Every application, script and direct SQL session obeys it, so it cannot be bypassed the way application-level checking can.
    - They help the `optimiser`, which uses `PRIMARY KEY`, `UNIQUE` and `NOT NULL` information to pick better plans.

    Main constraints
    ```
    NOT NULL      the column must have a value
    UNIQUE        no two rows may share the value
    PRIMARY KEY   UNIQUE + NOT NULL, one per table
    FOREIGN KEY   the value must exist in the parent table
    CHECK         the value must satisfy a condition
    DEFAULT       a value used when none is supplied
    ```

    Column-level constraint
    - Written `on the same line as the column`, right after its data type.
    - Applies to that `one column only`.
    ```sql
    CREATE TABLE Employee (
      emp_id INT PRIMARY KEY,                       -- column level
      name   VARCHAR(50) NOT NULL,                  -- column level
      salary DECIMAL(10,2) CHECK (salary > 0)       -- column level
    );
    ```

    Table-level constraint
    - Written `after all the columns`, as a separate item in the list.
    - Can use `more than one column`, which is the reason it exists.
    ```sql
    CREATE TABLE Enrollment (
      student_id INT,
      course_id  INT,
      marks      INT,
      final      INT,
      PRIMARY KEY (student_id, course_id),                    -- composite key
      CHECK (final <= marks),                                 -- two columns
      FOREIGN KEY (student_id) REFERENCES Student(student_id) -- table level
    );
    ```

    Difference

    | Point | Column level | Table level |
    |---|---|---|
    | Where written | With the column definition | After all columns |
    | Columns covered | Exactly one | One or more |
    | Composite key possible | No | Yes |
    | Multi-column `CHECK` | No | Yes |
    | `NOT NULL` allowed | Yes | No — only column level |
    | Naming | Usually unnamed, so the system names it | Usually named with `CONSTRAINT` |
    | Readability | Shorter, easier to read | Needed for composite rules |

    - `NOT NULL` is the one constraint that `cannot` be written at table level. Everything else can be written either way; the choice matters only when more than one column is involved.
    - Naming a constraint (`CONSTRAINT chk_salary CHECK (salary > 0)`) is good practice, because the error message then says which rule failed and the constraint can be dropped by name.

12. **(ক) Relationship degree কাকে বলে? উহা কত প্রকার ও কি কি? সংক্ষেপে লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1068 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The `degree of a relationship` is the number of entity types that take part in it. If two entity types are joined, the degree is 2; if three, the degree is 3.

    - Do not confuse it with cardinality. Degree counts `how many entity types` join a relationship. Cardinality (1:1, 1:N, M:N) says `how many instances` of one may relate to the other.

    Types — there are four

    (a) Unary (degree 1), also called recursive
    - One entity type is related to `itself`.
    - Example: an `Employee` manages another `Employee`. A `Course` is a prerequisite for another `Course`.
    - Implemented by a foreign key inside the same table.
    ```sql
    CREATE TABLE Employee (
      emp_id     INT PRIMARY KEY,
      name       VARCHAR(50),
      manager_id INT REFERENCES Employee(emp_id)     -- points to the same table
    );
    ```

    (b) Binary (degree 2)
    - `Two` entity types take part. This is by far the most common type and maps directly to tables.
    - Example: `Student` enrolls in `Course`; `Department` has `Employee`.

    (c) Ternary (degree 3)
    - `Three` entity types take part in one relationship at the same time.
    - Example: a `Supplier` supplies a `Part` for a `Project`. A `Doctor` prescribes a `Medicine` to a `Patient`.
    - Stored as a table holding all three foreign keys.
    ```sql
    CREATE TABLE Supply (
      supplier_id INT, part_id INT, project_id INT, qty INT,
      PRIMARY KEY (supplier_id, part_id, project_id)
    );
    ```

    (d) N-ary (degree n)
    - `n` entity types take part. Rare in practice, and usually broken into several binary relationships because it is hard to read and to maintain.

    ```mermaid
    erDiagram
        EMPLOYEE  ||--o{ EMPLOYEE : "unary - manages"
        STUDENT   ||--o{ ENROLLMENT : "binary"
        COURSE    ||--o{ ENROLLMENT : "binary"
        SUPPLIER  ||--o{ SUPPLY : "ternary"
        PART      ||--o{ SUPPLY : "ternary"
        PROJECT   ||--o{ SUPPLY : "ternary"
    ```

    | Degree | Name | Entity types | Example |
    |---|---|---|---|
    | 1 | Unary / recursive | 1 (itself) | Employee manages Employee |
    | 2 | Binary | 2 | Student enrolls in Course |
    | 3 | Ternary | 3 | Supplier supplies Part for Project |
    | n | N-ary | n | Rare; usually split into binary |

13. **(খ) Relational Database Model কী? অন্যান্য মডেলের তুলনায় এর সুবিধা ও অসুবিধা গুলো লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1094-1095 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The `Relational Database Model`, given by E. F. Codd in 1970, stores all data in `tables` (relations). A table has rows called `tuples` and columns called `attributes`. Tables are linked not by pointers but by `common values` — a foreign key in one table matching a primary key in another.

    Its main features
    - Every row is identified by a `primary key`, which is unique and never NULL.
    - Relationships are made by `foreign keys`, so the structure is value-based, not pointer-based.
    - Data is read and changed by `SQL`, a declarative language: the user says `what` is wanted, not `how` to get it.
    - The design is refined by `normalization` to remove redundancy and update anomalies.
    - The DBMS guarantees the `ACID` properties for every transaction.

    ```
    Department                   Employee
    +---------+--------+         +--------+-------+---------+
    | dept_id | name   |         | emp_id | name  | dept_id |
    +---------+--------+         +--------+-------+---------+
    | 10      | CSE    | <------ | 101    | Rahim | 10      |
    | 20      | EEE    | <------ | 102    | Karim | 20      |
    +---------+--------+         +--------+-------+---------+
       primary key                          foreign key
    ```

    Advantages over the older models (hierarchical, network) and over newer ones
    - `Simple` — everything is a table of rows and columns, easy for a non-programmer to picture. Hierarchical and network models needed the user to follow pointer chains.
    - `Structural independence` — adding a column or a table does not break existing programs. In the network model the access path was part of the program.
    - `Flexible querying` — any table can be joined with any other on the spot. The hierarchical model allowed only the paths built in at design time.
    - `Data integrity` — entity, referential and domain integrity are enforced by the DBMS itself.
    - `Less redundancy` after normalization, so update anomalies disappear.
    - `Standard language` — SQL works, with small differences, across Oracle, MySQL, SQL Server and PostgreSQL, so skills and code are portable.
    - `Strong security` — access can be granted per table, per column or through views.

    Disadvantages
    - `Slower for deep hierarchies`. Following a parent–child chain needs repeated joins, while the hierarchical model followed a pointer directly.
    - `Cost` — a commercial RDBMS needs powerful hardware, licences and trained staff.
    - `Scaling out is hard`. It scales up on one big machine well, but spreading one database across many machines is difficult because joins and ACID must hold across the network. NoSQL systems win here.
    - `Poor fit for complex data` — images, documents, graphs, geographic and hierarchical data do not fit rows and columns naturally. Object-oriented and document databases handle these better.
    - `Impedance mismatch` — program objects have to be converted into flat rows and back, which is why ORM tools are needed.
    - `Rigid schema` — the structure must be fixed in advance, and changing a large live table is expensive. Document databases allow a flexible schema.
    - `Over-normalization` can produce so many small tables that queries need many joins and become slow, which is why data warehouses deliberately denormalize.

14. **What is cardinality and modality?** *[Bangladesh Bank Assistant Programmer 2016 compact it 1265-1266 (ET: N/A)]*

    Answer: `Cardinality` and `modality` are the two numbers written on a relationship line in an ER diagram. Cardinality gives the `maximum` number of related rows; modality gives the `minimum`.

    Cardinality — how many
    - The maximum number of instances of one entity that may relate to one instance of another.
    - Three forms:
    ```
    One-to-One  (1:1)   one Employee has one Passport
    One-to-Many (1:N)   one Department has many Employees
    Many-to-Many(M:N)   a Student takes many Courses, a Course has many Students
    ```
    - Written as the maximum in the pair `(min, max)`.

    Modality — is it required
    - Whether an instance `must` take part in the relationship at all. It has only two values:
    ```
    Modality 0  -> optional  (partial participation, the foreign key may be NULL)
    Modality 1  -> mandatory (total participation, the foreign key is NOT NULL)
    ```
    - Example: an `Employee` may or may not have a `Company Car` → modality 0. Every `Employee` must belong to a `Department` → modality 1.

    Reading them together
    ```
            modality (min)          cardinality (max)
                  |                        |
                  v                        v
       EMPLOYEE ---(1,1)--- works in ---(0,N)--- DEPARTMENT

       (1,1) on Employee  : every employee must work in exactly one department
       (0,N) on Department: a department may have zero or many employees
    ```

    In crow's foot notation the inner symbol is the modality and the outer symbol is the cardinality:
    ```
       ---o<     zero or many   (optional, many)
       ---|<     one or many    (mandatory, many)
       ---o|     zero or one    (optional, one)
       ---||     exactly one    (mandatory, one)
    ```

    ```mermaid
    erDiagram
        DEPARTMENT ||--o{ EMPLOYEE : "employs"
        EMPLOYEE ||--o| CAR : "may be given"
    ```

    | Point | Cardinality | Modality |
    |---|---|---|
    | Answers | How many? | Is it required? |
    | Value given | Maximum | Minimum |
    | Possible values | 1 or N (many) | 0 or 1 |
    | Types | 1:1, 1:N, M:N | Optional, mandatory |
    | In SQL | Foreign key with or without `UNIQUE` | `NULL` allowed or `NOT NULL` |
    | Example | One department, many employees | An employee must have a department |

    - A second, unrelated meaning of cardinality appears in query tuning: the number of `distinct values` in a column. A `national_id` column has high cardinality, a `gender` column has low cardinality, and the optimiser uses this to decide whether an index is worth using.

## Indexing & Query Optimization (B-Tree, B+ Tree) (10)

1. **How indexing improve query performance?** *[Bangladesh Satellite Company Limited Assistant Engineer (CSE) 23.08.2025 compact it 1431 (ET: BUET)]*

   Answer: An `index` is a separate, sorted structure that stores the values of one or more columns together with a pointer to the row that holds them. It works like the index at the back of a book — instead of reading every page, you look up the word and jump straight to the page number.

   How it speeds up a query
   - `It removes the full table scan.` Without an index the DBMS reads every row (a `full table scan`, cost O(n)). With a B+ tree index it walks 3 or 4 levels down the tree, cost O(log n).
   ```
   Employee table with 1,000,000 rows
      without index : ~1,000,000 row reads
      with B+ tree  : ~3-4 node reads  ->  thousands of times faster
   ```
   - `Fewer disk I/Os.` The B+ tree is wide and shallow, and its upper levels usually stay in memory, so only one or two real disk reads are needed.
   - `Range queries become cheap.` The leaves of a B+ tree are linked in sorted order, so `WHERE salary BETWEEN 30000 AND 50000` finds the first match and then walks the leaf chain.
   - `Sorting is avoided.` An index on the `ORDER BY` column already holds the data in order, so the expensive sort step disappears.
   - `Joins get faster.` An index on the foreign key turns a nested-loop join from "scan the inner table once per outer row" into an index lookup per outer row.
   - `GROUP BY, MIN and MAX` are answered from the index directly — the smallest value is the leftmost leaf entry.
   - `Covering index.` If the index contains every column the query asks for, the DBMS answers from the index alone and never touches the table. This is an `index-only scan`.
   - `UNIQUE indexes` make duplicate checking a single lookup instead of a scan.

   ```sql
   CREATE INDEX idx_emp_dept ON Employee(dept_id);
   CREATE INDEX idx_emp_name_sal ON Employee(dept_id, salary);   -- composite
   ```

   The cost side
   - Every `INSERT`, `UPDATE` and `DELETE` must update the index too, so writes get slower.
   - Indexes take extra disk space.
   - An index is not used if the query hides the column in a function, such as `WHERE UPPER(name) = 'RAHIM'`, or if the column has very few distinct values.
   - A composite index is used only if the query filters on its `leftmost` columns. An index on `(dept_id, salary)` helps `WHERE dept_id = 10` but not `WHERE salary = 50000`.

   - Rule of thumb: index the primary key, the foreign keys, and the columns that appear in `WHERE`, `JOIN` and `ORDER BY`. Do not index every column.

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

   Answer: Primary key
   - A column, or a set of columns, that `uniquely identifies` each row of a table. It is always `UNIQUE` and `NOT NULL`, and a table can have only one.
   - Example: `student_id` in `Student`. It enforces `entity integrity`.

   Foreign key
   - A column in one table whose value must match a `primary key` value in another table, or be `NULL`.
   - Example: `Employee.dept_id` referring to `Department.dept_id`. It enforces `referential integrity` and stops orphan rows.

   Indexing
   - A separate sorted structure (usually a `B+ tree`) holding column values plus a pointer to the matching row. It lets the DBMS jump to a row instead of scanning the whole table.

   The relationship between the three
   - A `PRIMARY KEY` constraint automatically creates a `unique index` in every major DBMS. That index is how the uniqueness is checked at all — without it, each insert would need a full scan.
   - A `FOREIGN KEY` does `not` create an index automatically in most systems (MySQL InnoDB is the exception). It only uses the parent's index for checking.
   - So the practical rule is: index every foreign key yourself. Otherwise each parent `DELETE` or `UPDATE` scans the whole child table, and joins on that key stay slow.
   ```sql
   CREATE INDEX idx_emp_dept ON Employee(dept_id);
   ```

   | Item | Purpose | Index created? |
   |---|---|---|
   | Primary key | Identify a row uniquely | Yes, a unique index, automatically |
   | Unique key | Prevent duplicates | Yes, automatically |
   | Foreign key | Link to the parent table | No — you must create it |

   Does indexing always make an application faster? No.

   Reasons it can make things slower
   - `Writes slow down.` Every `INSERT`, `UPDATE` and `DELETE` must also update every index on the table. Ten indexes mean ten extra structures to maintain per write. On a write-heavy table this can dominate.
   - `Storage cost.` Indexes may take as much space as the table itself, and they compete for memory with the data pages.
   - `Low-selectivity columns.` An index on `gender` or a `status` flag returns half the table. Reading index plus table is `slower` than a plain sequential scan, so the optimiser ignores it and the index becomes dead weight.
   - `The index may not be usable.` `WHERE UPPER(name) = 'RAHIM'`, `WHERE salary * 12 > 600000` or a leading wildcard `LIKE '%man'` all prevent index use, because the stored value no longer matches what is searched.
   - `Wrong column order` in a composite index. An index on `(dept_id, salary)` does not help `WHERE salary = 50000`, because only the leftmost columns can be used.
   - `Small tables.` For a few hundred rows the whole table fits in one or two pages, so a scan is already fastest.
   - `Fragmentation.` After many updates the index becomes bloated and must be rebuilt.
   - `Stale statistics` can make the optimiser choose the wrong index entirely.

   - Conclusion: an index is a `trade — faster reads for slower writes and more space`. It helps when the query is selective (returns a small fraction of the rows) and the column is used in `WHERE`, `JOIN` or `ORDER BY`. Adding indexes blindly to every column makes an application slower, not faster.

3. **অথবা, (ক) Indexing এবং Hashing এর পদ্ধতিগুলো বর্ণনা করুন** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 612 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) `Indexing` and `hashing` are the two ways a DBMS finds a row without reading the whole table.

   Part 1 — Indexing methods

   An index stores `search key + pointer to the row`, kept in sorted order.

   (a) Primary (clustering) index
   - Built on the column the file is `physically sorted` by, usually the primary key. Only one per table, because the data can be sorted only one way.

   (b) Secondary (non-clustering) index
   - Built on a column the file is not sorted by. A table can have many. It must be `dense`, because the rows are scattered.

   (c) Dense index
   - One index entry for `every` row. Fast, but large.

   (d) Sparse index
   - One entry per `block` of rows. Smaller, but the block must then be scanned. Possible only on a sorted file.
   ```
   Sparse index          Data file (sorted)
   +-----+-----+         +----+----+----+
   | 10  | ----+-------> | 10 | 20 | 30 |
   | 40  | ----+-------> | 40 | 50 | 60 |
   +-----+-----+         +----+----+----+
   ```

   (e) Multi-level index
   - The index itself grows too big to search, so an index is built on the index. Repeating this gives the `B+ tree`.

   (f) B+ tree index
   - The structure used by nearly every real DBMS. All the actual keys live in the `leaf` nodes, which are linked in sorted order; the internal nodes are only a directory. Height stays 3-4 even for millions of rows, so a lookup is O(log n), and `range queries` are answered by walking the leaf chain.

   Part 2 — Hashing methods

   Hashing computes the address directly with a `hash function` h(key) → bucket number. No searching, no tree walking: one lookup is O(1).

   (a) Static hashing
   - A `fixed` number of buckets is fixed in advance.
   ```
   h(emp_id) = emp_id mod 5

      emp_id 101 -> bucket 1
      emp_id 205 -> bucket 0
   ```
   - Problem: when a bucket fills, an `overflow chain` is added, and searching that chain destroys the O(1) benefit. If the file grows, the whole thing must be rehashed.

   (b) Dynamic hashing
   - The number of buckets `grows and shrinks` with the data.
   - `Extendible hashing` — a directory of 2^d entries, where d is the global depth. When a bucket overflows, only that bucket is split, and the directory doubles only when needed. No full rehash.
   - `Linear hashing` — buckets are split one at a time in a fixed order, so no directory is needed at all.

   Comparison

   | Point | Indexing (B+ tree) | Hashing |
   |---|---|---|
   | Structure | Sorted tree | Hash function and buckets |
   | Exact-match lookup | O(log n) | O(1), the fastest |
   | Range query `BETWEEN` | Very good — walk the leaf chain | Not possible; must scan all buckets |
   | `ORDER BY` | Free, data is already sorted | No help |
   | Space | Extra tree storage | Buckets, plus overflow chains |
   | Weakness | Slightly slower point lookup | Collisions and overflow; growth is costly |
   | Used for | General purpose, ranges, sorting | Point lookups, hash joins, in-memory tables |

4. **How does index tuning help in improving query performance?** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 747 (ET: N/A)]*

   Answer: `Index tuning` is the work of choosing which indexes a database should have — adding the missing ones, dropping the useless ones, and fixing the shape of the ones that exist — so that queries run faster without making writes too slow.

   How it improves performance
   - `Removes full table scans.` Adding an index on a filtered column turns a scan of a million rows into a 3-4 level tree walk.
   - `Fixes the column order in composite indexes.` Only the `leftmost` columns of a composite index can be used. An index on `(salary, dept_id)` is useless for `WHERE dept_id = 10`, while `(dept_id, salary)` serves both. Reordering the columns costs nothing and can change everything.
   - `Creates covering indexes.` If the index holds every column the query needs, the DBMS never touches the table — an `index-only scan`.
   ```sql
   -- query: SELECT emp_id, salary FROM Employee WHERE dept_id = 10;
   CREATE INDEX idx_cover ON Employee(dept_id, salary, emp_id);
   ```
   - `Indexes the foreign keys.` Most systems do not index a foreign key automatically, so joins and parent deletes stay slow until you add it.
   - `Removes the sort step.` An index on the `ORDER BY` or `GROUP BY` column supplies rows already in order.
   - `Drops unused and duplicate indexes.` Every extra index slows down every `INSERT`, `UPDATE` and `DELETE` and wastes space. An index on `(dept_id)` is redundant when `(dept_id, salary)` exists.
   - `Rebuilds fragmented indexes` and `updates statistics`, so the optimiser's row estimates are right and it picks the correct plan.

   How it is done in practice
   ```sql
   EXPLAIN ANALYZE SELECT * FROM Employee WHERE dept_id = 10;
   ```
   ```
   1. Find the slow queries from the slow-query log or the DBMS's own views
   2. Read the execution plan; look for "Seq Scan", "Full Table Scan", "Sort"
   3. Add or reshape the index on the WHERE / JOIN / ORDER BY columns
   4. Re-run EXPLAIN and compare the cost and the actual time
   5. Check that writes have not become too slow
   6. Drop indexes the plans never use
   ```

   Points to keep in mind
   - An index helps only when the query is `selective` — it returns a small fraction of the rows. An index on `gender` will not be used.
   - An index is ignored when the column is wrapped in a function (`WHERE UPPER(name) = ...`) or when `LIKE` starts with a wildcard. Rewrite the query, or build a function-based index.
   - Index tuning is always a `trade`: faster reads for slower writes and more disk space. On a table that is written far more often than it is read, fewer indexes is the right answer.

5. **Construct a B+ tree index structure on emp_id for the given relation employee as shown below with n=4.** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 824 (ET: BUET)]*

   Answer: The employee rows are not printed with the question, so the standard set of `emp_id` values below is used. The method is the same for any data.
   ```
   emp_id values inserted in order:  10, 20, 30, 40, 50, 60, 70, 80
   ```

   Rules for n = 4
   ```
   n = 4  means each node holds at most 4 pointers.

   Internal node : max 3 keys, 4 pointers   min ceil(4/2) = 2 pointers
   Leaf node     : max n-1 = 3 keys          min ceil(3/2) = 2 keys
   ```
   - All the real keys live in the `leaves`. Internal nodes only guide the search.
   - The leaves are linked left to right, so a range query walks the chain.

   Step-by-step construction

   Insert 10, 20, 30 — one leaf, still within 3 keys.
   ```
      [10 | 20 | 30]
   ```

   Insert 40 — the leaf now needs 4 keys, so it `splits`. The first ceil(n/2) = 2 keys stay left, the rest go right, and the first key of the right leaf (30) is `copied up`.
   ```
               [ 30 ]
              /      \
      [10|20] -----> [30|40]
   ```

   Insert 50 — fits in the right leaf.
   ```
               [ 30 ]
              /      \
      [10|20] -----> [30|40|50]
   ```

   Insert 60 — that leaf overflows {30,40,50,60}, splits into [30|40] and [50|60], and 50 is copied up.
   ```
                 [ 30 | 50 ]
                /     |     \
      [10|20] -> [30|40] -> [50|60]
   ```

   Insert 70 — fits.
   ```
                 [ 30 | 50 ]
                /     |     \
      [10|20] -> [30|40] -> [50|60|70]
   ```

   Insert 80 — that leaf overflows {50,60,70,80}, splits into [50|60] and [70|80], and 70 is copied up. The root now has 3 keys and 4 pointers, which is exactly its limit.

   Final B+ tree
   ```
                       +----+----+----+
                       | 30 | 50 | 70 |          <- root (internal)
                       +----+----+----+
                      /     |     |     \
                     /      |     |      \
           +-------+   +-------+   +-------+   +-------+
           | 10 20 |-->| 30 40 |-->| 50 60 |-->| 70 80 |    <- leaves, linked
           +-------+   +-------+   +-------+   +-------+
               |           |           |           |
             record      record      record      record
            pointers    pointers    pointers    pointers
   ```

   How a search works
   - To find `emp_id = 60`: at the root, 60 lies between 50 and 70, so follow the third pointer; the leaf [50|60] holds 60, and its pointer gives the employee record. Two node reads for eight records, and still only 3-4 reads for millions.
   - To find `emp_id BETWEEN 30 AND 60`: reach leaf [30|40], then follow the leaf chain right until the key passes 60.

   Points to state in the exam
   - A key `copied up` on a leaf split stays in the leaf as well. On an `internal` node split the middle key is `moved up`, not copied.
   - Every leaf is at the `same depth`, so the tree stays balanced and every search costs the same.

6. **What is Indexing? Write down the usages of Indexing.** *[RAKUB Assistant Database Administrator 2020 compact it 1015 (ET: E-Zone)]*

   Answer: `Indexing` is a technique that creates a small, sorted structure holding the values of one or more columns together with a pointer to the row that contains them. The DBMS searches this structure instead of reading the whole table — the same idea as the index at the back of a book.

   - The structure used in practice is a `B+ tree`. All the keys sit in the leaves, the leaves are linked in sorted order, and the tree stays 3-4 levels deep even for millions of rows.
   ```
   Index                      Table
   +-------+--------+         +--------+-------+---------+
   | key   | rowid  |         | emp_id | name  | dept_id |
   +-------+--------+         +--------+-------+---------+
   | 101   | ---------------> | 101    | Rahim | 10      |
   | 102   | ---------------> | 102    | Karim | 20      |
   +-------+--------+         +--------+-------+---------+
   ```

   ```sql
   CREATE INDEX idx_emp_dept ON Employee(dept_id);
   CREATE UNIQUE INDEX idx_emp_email ON Employee(email);
   DROP INDEX idx_emp_dept;
   ```

   Usages of indexing
   - `Fast lookup` — turns a full table scan of O(n) into a tree walk of O(log n), which is the main reason it exists.
   - `Range queries` — `WHERE salary BETWEEN 30000 AND 50000` finds the first match and walks the linked leaves.
   - `Enforcing uniqueness` — a `PRIMARY KEY` or `UNIQUE` constraint is implemented by a unique index; that is how duplicates are caught without a scan.
   - `Faster joins` — an index on the foreign key turns the inner side of a join into a lookup instead of a scan.
   - `Avoiding sorts` — an index on the `ORDER BY` or `GROUP BY` column already holds the rows in order.
   - `MIN and MAX` — read from the first or last leaf entry directly.
   - `Covering index` — if the index holds every column the query needs, the table is never touched (an `index-only scan`).
   - `Referential integrity checks` — the parent's index is what makes a foreign-key check cheap.

   Types
   ```
   Primary / clustered  : on the column the table is physically sorted by; one per table
   Secondary            : on any other column; many allowed
   Unique               : no duplicate values
   Composite            : on several columns, e.g. (dept_id, salary)
   Dense / sparse       : one entry per row / one entry per block
   Bitmap               : for columns with few distinct values, used in data warehouses
   ```

   - The cost: every write must update every index, and indexes take disk space. So index the primary key, the foreign keys, and the columns used in `WHERE`, `JOIN` and `ORDER BY` — not every column.

7. **(খ) Database এর ক্ষেত্রে Indexing এর কার্যকারিতা বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1096 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) An `index` is a small sorted structure that holds column values plus a pointer to the row that contains them. The DBMS searches the index instead of the table, exactly as a reader uses the index at the back of a book.

   Effectiveness of indexing
   - `It removes the full table scan.` A table of one million rows costs about one million reads without an index. With a B+ tree index the search walks 3-4 levels, so it costs 3-4 node reads.
   ```
      without index : O(n)      ~1,000,000 row reads
      with B+ tree  : O(log n)  ~3-4 node reads
   ```
   - `Fewer disk I/Os`, which is the real cost in a database. The upper levels of the tree usually stay in memory, so only one or two true disk reads are needed.
   - `Range queries become cheap.` The leaves of a B+ tree are linked in sorted order, so `WHERE salary BETWEEN 30000 AND 50000` finds the first matching entry and then walks the chain.
   - `Sorting is avoided.` An index on the `ORDER BY` column supplies the rows already in order, so the sort step disappears.
   - `Joins get faster.` An index on the foreign key turns the inner table of a join from a repeated scan into a repeated lookup.
   - `Uniqueness is enforced cheaply.` `PRIMARY KEY` and `UNIQUE` are implemented by a unique index; without it every insert would scan the table to check for duplicates.
   - `MIN, MAX and COUNT` can be answered from the index alone.
   - `Covering index` — when the index holds every column the query asks for, the table is never read at all.

   ```sql
   CREATE INDEX idx_emp_dept ON Employee(dept_id);
   CREATE INDEX idx_dept_sal  ON Employee(dept_id, salary);   -- composite
   ```

   Where it does not help
   - Every `INSERT`, `UPDATE` and `DELETE` must update every index, so writes become slower.
   - Indexes take extra disk space, sometimes as much as the table.
   - On a column with few distinct values, such as `gender`, the index returns half the table and the optimiser ignores it.
   - Wrapping the column in a function — `WHERE UPPER(name) = 'RAHIM'` — or a leading wildcard `LIKE '%man'` prevents the index from being used.
   - On a very small table a plain scan is already the fastest choice.

   - So indexing trades `faster reads for slower writes and more space`. Index the primary key, the foreign keys and the columns used in `WHERE`, `JOIN` and `ORDER BY` — not every column.

8. **(ক) Sorting and Indexing-এর মধ্যে পার্থক্য লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1096 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) `Sorting` arranges the data records themselves in order. `Indexing` leaves the data where it is and builds a separate sorted structure that points to it.

   Sorting
   - The rows are physically rearranged in the file so that the values of one column appear in ascending or descending order.
   - Only `one` order is possible, because a file can be laid out only one way.
   - Every insert in the middle needs the following records to shift, which is expensive.
   - In SQL, `ORDER BY` sorts the result of one query; it does not change the stored table.

   Indexing
   - A separate structure — normally a `B+ tree` — stores `search key + pointer to the row`. The table itself stays untouched.
   - `Many` indexes on many different columns can exist on the same table at the same time.
   - An insert only adds one entry to each index; nothing in the table is shifted.

   ```
   Index (sorted)                Table (unsorted)
   +------+---------+            +--------+-------+
   | key  | pointer |            | emp_id | name  |
   +------+---------+            +--------+-------+
   | 10   |  -----------------> | 30     | Jamal |
   | 20   |  ----------------->  | 10     | Rahim |
   | 30   |  ----------------->  | 20     | Karim |
   +------+---------+            +--------+-------+
   ```

   Difference

   | Point | Sorting | Indexing |
   |---|---|---|
   | What is arranged | The data records themselves | A separate key-and-pointer structure |
   | Data movement | Records are physically moved | Records stay where they are |
   | How many possible | Only one order per table | Many indexes on many columns |
   | Extra space | None | Extra space for each index |
   | Insert / delete cost | High — records must shift | Low — only the index entry changes |
   | Search speed | Binary search, O(log n), but only on the sorted column | O(log n) on every indexed column |
   | Structure | The data file itself | B+ tree, hash table, bitmap |
   | SQL | `ORDER BY` (result only), clustered table | `CREATE INDEX` |

   - The two meet in the `clustered index`, where the table is physically kept in the order of the index key. It gives the fastest range scans, which is why only one clustered index per table is allowed.
   - Practical point: sorting helps only the one column it was done on, while indexing can speed up searches on many columns at once — at the cost of extra space and slower writes.

9. **What is the purpose of index in database?** *[DESCO Assistant Engineer (CSE) 2016 compact it 1267 (ET: N/A)]*

   Answer: An `index` is a small sorted structure that stores the values of one or more columns together with a pointer to the row holding them. Its purpose is to let the DBMS find rows `without reading the whole table`.

   Purposes of an index
   - `Speed up searching.` Without an index the DBMS performs a full table scan, cost O(n). With a B+ tree index it walks 3-4 levels, cost O(log n). On a million-row table that is the difference between a million reads and four.
   - `Reduce disk I/O`, which is the real cost in any database. The upper levels of the B+ tree usually stay cached in memory.
   - `Answer range queries.` The leaves of a B+ tree are linked in sorted order, so `WHERE salary BETWEEN 30000 AND 50000` finds the first match and walks the chain.
   - `Enforce uniqueness.` `PRIMARY KEY` and `UNIQUE` are implemented internally by a unique index — that is how a duplicate is caught in one lookup instead of a scan.
   - `Avoid sorting.` An index on the `ORDER BY` or `GROUP BY` column already holds the rows in order.
   - `Speed up joins.` An index on the foreign key turns the inner side of a join into a lookup rather than a repeated scan.
   - `Support referential integrity.` Checking a foreign key uses the parent's index.
   - `Serve a query from the index alone.` If the index holds every column the query needs, the table is never touched — an `index-only scan`.

   ```sql
   CREATE INDEX idx_emp_dept ON Employee(dept_id);
   CREATE UNIQUE INDEX idx_emp_email ON Employee(email);
   ```

   ```
   Index                        Table
   +-------+---------+          +--------+-------+---------+
   | key   | pointer |          | emp_id | name  | dept_id |
   +-------+---------+          +--------+-------+---------+
   | 101   | -----------------> | 101    | Rahim | 10      |
   | 102   | -----------------> | 102    | Karim | 20      |
   +-------+---------+          +--------+-------+---------+
   ```

   The cost
   - Every `INSERT`, `UPDATE` and `DELETE` must also update every index, so writes get slower.
   - Indexes consume extra disk space.
   - On a column with few distinct values, or when the column is wrapped in a function, the index is not used at all.

   - So the purpose of an index is to trade `write speed and disk space for read speed`. Index the primary key, the foreign keys and the columns used in `WHERE`, `JOIN` and `ORDER BY`.

10. **How hashtable is used in database?** *[DESCO Assistant Engineer (CSE) 2016 compact it 1267 (ET: N/A)]*

    Answer: A `hash table` maps a key to a storage address directly, using a `hash function`: h(key) → bucket number. There is no searching and no tree to walk, so an exact-match lookup costs O(1). A database uses this idea in several places.

    1. Hash file organisation (hash index)
    - The rows themselves are stored in `buckets` chosen by the hash of the key column.
    ```
    h(emp_id) = emp_id mod 5

       emp_id 101 -> bucket 1
       emp_id 205 -> bucket 0
       emp_id 307 -> bucket 2

       +----------+----------+----------+----------+----------+
       | bucket 0 | bucket 1 | bucket 2 | bucket 3 | bucket 4 |
       +----------+----------+----------+----------+----------+
            205        101        307
    ```
    - To find employee 101 the DBMS computes 101 mod 5 = 1 and reads bucket 1. One disk read, no matter how big the table is.
    - `Static hashing` fixes the bucket count in advance, so a full bucket needs an `overflow chain`, which slows lookups. `Dynamic hashing` — extendible or linear hashing — splits buckets as the file grows, so no full rehash is needed.

    2. Hash index
    ```sql
    CREATE INDEX idx_emp_hash ON Employee USING HASH (emp_id);
    ```
    - Faster than a B+ tree for `=` lookups, but useless for `<`, `>`, `BETWEEN` and `ORDER BY`, because hashing destroys the order. That is why B+ trees remain the default.

    3. Hash join
    - The most important use in query processing. To join two tables, the DBMS builds a hash table in memory on the join key of the smaller table (`build` phase), then scans the bigger table and probes it (`probe` phase).
    ```
    Build : hash Department on dept_id, keep it in memory
    Probe : for each Employee row, hash its dept_id and look it up
    ```
    - This makes an equi-join O(m + n) instead of the O(m × n) of a nested loop.

    4. Other uses inside the DBMS
    - `Hash aggregation` for `GROUP BY` — each group key hashes to a slot that keeps its running total.
    - `DISTINCT` and set operations — duplicates are detected by hashing.
    - `Partitioning` — `PARTITION BY HASH (customer_id)` spreads rows evenly across partitions or across nodes in a distributed database.
    - `Buffer pool and lock manager` — the DBMS finds a cached page or a lock entry by hashing its page id.
    - `Password and checksum storage` — a one-way hash such as SHA-256, a different purpose from lookup.

    Limitations
    - `Collisions` — two keys hashing to the same bucket — need chaining or open addressing.
    - `No range or sorted access`, so a hash index cannot serve `BETWEEN` or `ORDER BY`.
    - A `poor hash function` makes buckets uneven and degrades lookups to a scan.

## Data Warehousing, Data Mining & Business Intelligence (9)

1. **Differentiate among Database, Data Warehouse and Data Mining with real world example.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 517 (ET: MIST)]*

   Answer: The three are different stages of the same journey: a `database` records what happens, a `data warehouse` stores the history of what happened, and `data mining` finds the hidden pattern inside that history.

   Database
   - A store of `current, operational` data used to run day-to-day work. Optimised for many small reads and writes (`OLTP`), and kept `normalized` so nothing is duplicated.
   - Real example: the core banking system of Sonali Bank. When a customer withdraws Tk 5,000 from an ATM, the balance row is updated in a second.

   Data warehouse
   - A large store of `historical, integrated` data brought together from many source databases through `ETL` (Extract, Transform, Load). Optimised for reading and aggregating huge volumes (`OLAP`), and deliberately `denormalized` into a star schema.
   - It is subject-oriented, integrated, time-variant and non-volatile — data is loaded and then never updated.
   - Real example: ten years of every branch's deposits, loans and card transactions in one place, so management can compare branch performance by quarter.

   Data mining
   - The `process` of digging through that stored data to find patterns, rules and predictions that nobody asked for in advance. It uses statistics and machine learning: classification, clustering, association rules, regression.
   - Real example: mining the warehouse shows that customers who take a car loan and hold a credit card are 3 times more likely to default in the first year, or that a card used in two cities within one hour is probably fraud.

   ```mermaid
   flowchart LR
       A[Operational databases<br/>ATM, branch, cards] -->|ETL| B[Data warehouse<br/>10 years of history]
       B --> C[Data mining<br/>patterns and prediction]
       C --> D[Business decision]
   ```

   | Point | Database | Data warehouse | Data mining |
   |---|---|---|---|
   | What it is | A storage system | A storage system | A process / technique |
   | Data | Current, detailed | Historical, summarised | Uses the warehouse's data |
   | Purpose | Run the business (OLTP) | Analyse the business (OLAP) | Discover unknown patterns |
   | Operations | INSERT, UPDATE, DELETE | Mostly SELECT and aggregate | Classification, clustering, association |
   | Design | Normalized | Denormalized, star schema | No storage of its own |
   | Size | GB | TB to PB | — |
   | Users | Clerks, applications | Analysts, management | Data scientists |
   | Bank example | Today's ATM withdrawal | 10 years of all transactions | Fraud detection, churn prediction |

   - The order is fixed: databases feed the warehouse, and the warehouse feeds the mining. Mining directly on the live operational database is avoided, because heavy analytical queries would slow down customer service.

2. **Discuss different tools and techniques to develop a Business Intelligence Dashboard for a bank. How can data be captured and aggregated from various sources within the bank to monitor the business performance?** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 519 (ET: MIST)]*

   Answer: A `Business Intelligence (BI) dashboard` is a single screen that shows a bank's key numbers — deposits, loans, NPL, income, branch performance — as charts and indicators, refreshed automatically from the bank's own systems.

   Part 1 — Tools

   Data integration (ETL / ELT)
   - `Informatica PowerCenter`, `Talend`, `SSIS`, `Apache NiFi`, `Pentaho` for scheduled extraction and transformation.
   - `Apache Kafka` with `Debezium` for change-data-capture, when the dashboard must be near real time.

   Storage
   - Data warehouse: `Oracle Exadata`, `Teradata`, `SQL Server`, `Snowflake`, `Amazon Redshift`, `Google BigQuery`.
   - Data lake for raw and unstructured data: `Hadoop HDFS`, `Amazon S3`.
   - `Data marts` per department — retail, credit, treasury — built on top of the warehouse.

   OLAP and modelling
   - `Star` or `snowflake` schema, OLAP cubes in `SSAS` or `Oracle OLAP`, with roll-up, drill-down, slice and dice.

   Visualisation
   - `Power BI`, `Tableau`, `Qlik Sense`, `Oracle OBIEE`, `SAP BusinessObjects`, or open source `Apache Superset` and `Metabase`.

   Part 2 — Techniques for capturing and aggregating data

   ```mermaid
   flowchart LR
       A[Core banking] --> E[Staging area]
       B[ATM / POS switch] --> E
       C[Cards, loans, treasury] --> E
       D[CRM, HR, complaints] --> E
       E -->|clean, standardise| F[Data warehouse<br/>star schema]
       F --> G[Data marts / OLAP cube]
       G --> H[BI dashboard]
   ```

   - `Identify the sources` — core banking, card switch, ATM/POS, loan origination, treasury, CRM, call centre, HR, and external feeds such as Bangladesh Bank rates.
   - `Extract` — nightly batch for the core system, and `change-data-capture` from the redo log for tables that must be current. CDC is preferred because it does not load the production database.
   - `Stage and clean` — remove duplicate customer records, standardise date, currency and branch codes, handle nulls, and run a `single customer view` match on NID and mobile number.
   - `Transform and conform` — build shared dimensions (Customer, Branch, Product, Time, Employee) so that "branch" means the same thing in every report. This step is what makes cross-source comparison possible.
   - `Load into fact tables` — one row per transaction or per daily balance, with foreign keys to the dimensions.
   - `Aggregate` — pre-compute daily, monthly and quarterly totals per branch and per product into summary tables, so the dashboard does not aggregate millions of rows at query time.
   - `Define the KPIs` — total deposit, advance-deposit ratio, NPL percentage, cost of fund, net interest margin, CASA ratio, new accounts per day, ATM uptime, transactions per channel.
   - `Publish` — role-based dashboards: a branch manager sees only that branch, the MD sees the whole bank. Drill-down goes from bank to zone to branch to account.
   - `Refresh` — most figures nightly, a few (cash position, ATM status, fraud alerts) in near real time.

   Points to note
   - `Data quality` is the main risk. A dashboard built on unmatched customer records gives confident but wrong numbers.
   - `Security` — mask account numbers and NID, encrypt at rest and in transit, and keep an audit log of who viewed what, as required by the bank's regulator.
   - Keep the dashboard to `5-8 KPIs` per screen. A crowded dashboard is not read.

3. **Software scenario question- Business Intelligence Model** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 521 (ET: MIST)]*

4. **(খ) Big data বলতে কি বুঝায়? Big data এর বৈশিষ্ট্যগুলো লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 766 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) `Big data` means datasets so large, so fast-arriving or so varied that ordinary databases and tools cannot store or process them in a reasonable time. It needs distributed systems such as `Hadoop` and `Spark` that spread the data and the computation across many machines.

   - Example: the transaction logs of all mobile financial services in Bangladesh, or every post and click on a social network.

   Characteristics — the 5 V's

   `Volume` — the size
   - Data measured in terabytes and petabytes rather than gigabytes. A single bank's card and ATM logs alone run to billions of rows a year.
   - Handled by storing across many nodes (`HDFS`, object storage) instead of one big server.

   `Velocity` — the speed
   - Data arrives continuously and must often be processed as it arrives: card swipes, sensor readings, clickstreams, mobile money transfers.
   - Handled by streaming tools such as `Kafka`, `Spark Streaming` and `Flink`.

   `Variety` — the different forms
   ```
   Structured    : tables, rows and columns  (core banking)
   Semi-structured: JSON, XML, CSV, log files
   Unstructured  : text, e-mail, image, audio, video, CCTV
   ```
   - Traditional relational databases handle only the first kind well, which is the main reason big data tools exist.

   `Veracity` — the trustworthiness
   - Large data is dirty: duplicates, missing fields, wrong entries, biased samples. Cleaning and validating it is a major part of the work, because a wrong conclusion is worse than no conclusion.

   `Value` — the usefulness
   - Data has no worth until analysis turns it into a decision. This is the V that justifies the cost of the other four.
   - Example: fraud detection, credit scoring, customer churn prediction, targeted offers.

   Two more V's often added
   - `Variability` — the meaning and the arrival rate change over time (festival season traffic differs from an ordinary week).
   - `Visualization` — the result must be shown as a chart or dashboard, because nobody can read a billion rows.

   Technologies used
   ```
   Storage     : HDFS, Amazon S3, NoSQL (Cassandra, MongoDB, HBase)
   Processing  : MapReduce, Apache Spark
   Streaming   : Kafka, Flink
   Query       : Hive, Presto, BigQuery
   ```
   - The common design idea is `move the computation to the data`, not the data to the computation, because moving petabytes across a network is impossible.

5. **Write down different stage of data mining?** *[Combined 5 Banks Assistant Maintenance Engineer 2019 compact it 1055 (ET: AUST)]*
   a) Data Purification
   b) Data Integration
   c) Data Selection
   d) Data Transformation
   e) Data Mining (The Final Stage)
   f) Pattern Evaluation
   g) Knowledge Representation

   Answer: `Data mining` is the process of finding useful, previously unknown patterns in large amounts of data. It is one step inside the larger process called `KDD` — Knowledge Discovery in Databases — and the stages below are usually asked as "the stages of data mining".

   ```mermaid
   flowchart LR
       A[Data cleaning] --> B[Data integration]
       B --> C[Data selection]
       C --> D[Data transformation]
       D --> E[Data mining]
       E --> F[Pattern evaluation]
       F --> G[Knowledge presentation]
   ```

   1. Data cleaning
   - Remove noise, duplicate rows and clearly wrong values, and decide what to do with missing fields — drop them, or fill them with the mean or a predicted value.
   - Usually the longest stage. Dirty data gives a confident but wrong answer.

   2. Data integration
   - Combine data from several sources — the core banking system, the card switch, the CRM — into one store, resolving conflicts where the same thing is named differently in each source.

   3. Data selection
   - Pick only the rows and columns relevant to the question being asked. Mining the whole warehouse is slow and adds noise.
   - Example: to predict loan default, select loan history and repayment behaviour, not marketing e-mails.

   4. Data transformation
   - Convert the selected data into the form the mining algorithm needs: `normalization` to a common scale, `aggregation` to monthly totals, `discretization` of age into bands, and encoding of categorical values into numbers.

   5. Data mining
   - The core step. Apply the algorithm that fits the goal:
   ```
   Classification    : decision tree, Naive Bayes  -> will this customer default?
   Clustering        : k-means                     -> which customer groups exist?
   Association rules : Apriori, FP-Growth          -> what is bought together?
   Regression        : linear, logistic            -> how much will sales be?
   Anomaly detection : outlier analysis            -> is this transaction fraud?
   ```

   6. Pattern evaluation
   - Judge which of the discovered patterns are actually `interesting` — valid, new, useful and understandable. Accuracy, precision, recall, support and confidence are used here, and the model is tested on data it has never seen.
   - Most patterns found are trivial or already known; this stage filters them out.

   7. Knowledge presentation
   - Show the surviving results as charts, rules, reports or a dashboard so that a manager who is not a data scientist can act on them.

   - Points to note: the process is `iterative`, not a straight line — a poor result sends the work back to selection or transformation. Roughly 60-70 per cent of the total effort goes into stages 1 to 4, not into the mining algorithm itself.

6. **Database tuning and database mining বলতে কী বোঝেন?** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1077 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) The two terms sound similar but belong to different areas: tuning is about `speed`, mining is about `knowledge`.

   Database tuning
   - The work of adjusting a database so that it runs faster and uses hardware efficiently, without changing what it stores.
   - It works at several levels:
   ```
   Query tuning    : rewrite slow SQL, avoid SELECT *, replace a correlated
                     subquery with a join, read the EXPLAIN plan
   Index tuning    : add missing indexes, fix composite column order,
                     drop unused indexes, rebuild fragmented ones
   Schema tuning   : normalize to remove redundancy, or denormalize a
                     reporting table to remove joins; partition huge tables
   Memory tuning   : size the buffer cache, sort area and shared pool
   Disk tuning     : spread files over disks, separate data from log,
                     use faster storage for hot tables
   Concurrency     : shorter transactions, right isolation level, fewer locks
   Statistics      : keep optimiser statistics fresh so plans stay correct
   ```
   - Measured by `response time`, `throughput` and the number of disk I/Os. The method is always: measure, change one thing, measure again.

   Database mining (data mining)
   - The process of searching large stored data for patterns and relationships that nobody knew were there, using statistics and machine learning.
   - Main techniques:
   ```
   Classification    : predict a class    -> will this customer default?
   Clustering        : find natural groups -> which customer segments exist?
   Association rules : find items that occur together -> market basket analysis
   Regression        : predict a number   -> next month's sales
   Anomaly detection : find the odd one   -> fraudulent card use
   ```
   - It normally runs on a `data warehouse`, not on the live operational database, because heavy analytical queries would slow down day-to-day work.

   | Point | Database tuning | Database mining |
   |---|---|---|
   | Goal | Make the system faster | Find hidden knowledge |
   | Concerned with | Performance, resources | Patterns, prediction |
   | Changes the data? | No — only how it is stored and accessed | No — only reads it |
   | Done by | DBA | Data analyst, data scientist |
   | Tools | EXPLAIN, index advisor, AWR reports | Weka, R, Python, SQL Server Analysis Services |
   | Output | Lower response time | Rules, models, predictions |
   | Runs on | The live production database | Usually the data warehouse |

   - They meet at one point: mining queries are heavy, so a well-tuned warehouse — partitioned tables, summary tables, the right indexes — is what makes mining practical at all.

7. **(ক) Data Mining and Data Warehousing বলতে কী বোঝায়? এদের মধ্যে সম্পর্ক কী? এদের উপকারিতা কী?** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1095-1096 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Data warehousing
   - A `data warehouse` is a large central store of historical data collected from many different source systems, built for analysis and reporting rather than for daily transactions.
   - Bill Inmon's four properties: it is `subject-oriented` (organised around sales or customers, not around an application), `integrated` (codes and formats made uniform across sources), `time-variant` (it keeps years of history) and `non-volatile` (data is loaded, then read, never updated by users).
   - Data reaches it through `ETL` — Extract from the sources, Transform and clean, Load into the warehouse — and is stored denormalized as a `star schema` of one fact table surrounded by dimension tables.

   Data mining
   - `Data mining` is the process of searching that stored data for patterns, rules and predictions that were not known in advance.
   - Main techniques: `classification` (will this customer default?), `clustering` (which customer groups exist?), `association rules` (what is bought together?), `regression` (how much will we sell?) and `anomaly detection` (is this transaction fraud?).

   The relationship between them
   - The warehouse `stores`, the mining `analyses`. One is a place, the other is a process.
   - Mining needs clean, integrated, historical data covering years and many sources — which is exactly what a warehouse provides. Mining directly on operational databases fails, because the data is scattered, inconsistent and holds only current values.
   - The warehouse is also what protects the live system: heavy mining queries run on the warehouse, so customer service is never slowed down.

   ```mermaid
   flowchart LR
       A[Operational databases] -->|ETL| B[Data warehouse]
       B --> C[Data mining]
       C --> D[Knowledge and decisions]
   ```

   Benefits of data warehousing
   - One `single version of the truth` — every department reports the same number.
   - Fast analytical and historical queries, because the design is built for reading and aggregating.
   - Keeps years of history that operational systems overwrite.
   - Removes the analysis load from the production database.
   - Provides the clean base for BI dashboards, OLAP and mining.

   Benefits of data mining
   - Finds relationships nobody thought to look for.
   - Predicts future behaviour: default risk, churn, demand.
   - Detects fraud by spotting transactions that do not fit the usual pattern.
   - Supports targeted marketing and cross-selling, so campaigns cost less and work better.
   - Turns stored data, which is a cost, into decisions, which are a return.

   - In short: `the warehouse gives clean historical data, mining turns it into knowledge`. Neither is much use without the other.

8. **What is Data warehouse? Why We Need Data Warehouse? Advantages of Data warehousing.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1162 (ET: N/A)]*

   Answer: A `data warehouse` is a large central store of historical data brought together from many different source systems, built for analysis and reporting rather than for running daily transactions.

   - W. H. Inmon's definition gives its four properties:
   ```
   Subject-oriented : organised around a subject (sales, customer, loan),
                      not around an application
   Integrated       : codes, units and formats are made uniform across sources
   Time-variant     : it holds years of history, every record stamped with time
   Non-volatile     : data is loaded and then read; users never update or delete it
   ```
   - Data enters through `ETL` — Extract from the sources, Transform and clean, Load — and is stored denormalized as a `star schema`: one central fact table holding the measures, surrounded by dimension tables holding the descriptions.

   ```mermaid
   flowchart LR
       A[Core banking] -->|ETL| D[Data warehouse]
       B[Card / ATM switch] -->|ETL| D
       C[CRM, HR] -->|ETL| D
       D --> E[Data marts]
       E --> F[OLAP / BI reports]
   ```

   Why we need a data warehouse
   - `Data is scattered.` A bank keeps customer data in the core system, card data in the switch and complaints in the CRM. No single query can cross them until they are brought together.
   - `Operational databases keep only current data.` They overwrite the old balance. Trend analysis needs years of history.
   - `Analytical queries would kill the live system.` A report that scans ten years of transactions would slow down the ATM network if it ran on production.
   - `Normalized OLTP design is wrong for analysis.` A report joining fifteen normalized tables is slow; a star schema needs two or three joins.
   - `Different systems disagree.` Each department reports a different figure until the definitions are conformed in one place — the `single version of the truth`.
   - `BI, OLAP and data mining need a clean, integrated base` to work on at all.

   Advantages
   - One consistent set of numbers for the whole organisation.
   - Fast historical and aggregated queries; a summary that took hours takes seconds.
   - Keeps long-term history that source systems delete or overwrite.
   - Removes the reporting load from production databases.
   - Improves data quality, because errors are found and fixed during ETL.
   - Supports OLAP operations — roll-up, drill-down, slice and dice — and data mining.
   - Gives management fast, evidence-based decisions instead of guesswork.

   Limitations to mention
   - Expensive to build and to maintain, and the ETL work is far larger than people expect.
   - Data is usually one day old, so it does not replace real-time systems.
   - It needs continuous care: source systems change, and the ETL must change with them.

9. **Explain data warehouse with figure. Describe fact table and dimension table with example.** *[ICT Ministry Assistant Programmer 2017 compact it 1243-1244 (ET: N/A)]*

   Answer: A `data warehouse` is a central store of historical data collected from many source systems, built for analysis rather than for daily transactions. It is subject-oriented, integrated, time-variant and non-volatile.

   Architecture

   ```mermaid
   flowchart LR
       A[Core banking DB] -->|Extract| S[Staging area]
       B[ATM / card switch] -->|Extract| S
       C[CRM, Excel, external feeds] -->|Extract| S
       S -->|Transform: clean, standardise| W[(Data warehouse<br/>star schema)]
       W --> M1[Sales data mart]
       W --> M2[Finance data mart]
       M1 --> R[OLAP / BI dashboard]
       M2 --> R
   ```

   ```
   +-------------+     +---------+     +-------------+     +----------+
   |   Source    | ETL | Staging | ETL |    Data     |     | OLAP /   |
   |  systems    |---->|  area   |---->|  warehouse  |---->| reports  |
   | OLTP, files |     | (clean) |     | (star schema)|    | dashboard|
   +-------------+     +---------+     +-------------+     +----------+
                                             |
                                       +-----------+
                                       | Data marts|
                                       +-----------+
   ```
   - `Source layer` — the operational databases and files where the data is created.
   - `Staging area` — a working space where data is cleaned, de-duplicated and standardised. Nothing is reported from here.
   - `Warehouse layer` — the permanent store, held as a star schema.
   - `Data marts` — department-sized subsets (sales, finance) for faster access.
   - `Presentation layer` — OLAP cubes, reports and dashboards.

   Fact table
   - The central table. It holds the `measures` — the numbers being analysed — plus foreign keys to the dimension tables.
   - Its primary key is the combination of those foreign keys.
   - It is `long and thin`: few columns but millions or billions of rows, and it grows every day.
   - The measures should be `additive`, so they can be summed across any dimension.

   Dimension table
   - Describes the `context` of a fact: who, what, when, where.
   - It is `short and wide`: many descriptive columns, relatively few rows, and it changes slowly.
   - It is deliberately `denormalized` — the whole hierarchy sits in one table — so that a report needs only one join.
   - The key is a `surrogate key`, a meaningless integer, so that a changed business code does not break history.

   Example — a bank's sales star schema
   ```
           Dim_Time                 Dim_Branch
      +--------------+          +----------------+
      | time_key PK  |          | branch_key PK  |
      | date, month  |          | branch_name    |
      | quarter,year |          | city, zone     |
      +------+-------+          +--------+-------+
             |                           |
             |    +------------------+   |
             +----|   Fact_Sales     |---+
                  +------------------+
                  | time_key    FK   |
                  | branch_key  FK   |    <- keys
                  | product_key FK   |
                  | customer_key FK  |
                  +------------------+
                  | quantity_sold    |
                  | amount           |    <- measures (facts)
                  | discount         |
                  +--------+---------+
             |                           |
      +------+-------+          +--------+-------+
      | product_key PK|         | customer_key PK|
      | product_name  |         | customer_name  |
      | category      |         | occupation     |
      +--------------+          +----------------+
          Dim_Product               Dim_Customer
   ```
   - A query such as "total sales of the Savings product in Dhaka zone during Q1 2025" joins the fact table to three dimensions and sums one column.

   | Point | Fact table | Dimension table |
   |---|---|---|
   | Holds | Numeric measures | Descriptive attributes |
   | Size | Millions of rows, few columns | Few rows, many columns |
   | Key | Composite of foreign keys | Single surrogate key |
   | Growth | Grows constantly | Changes slowly |
   | Example columns | amount, quantity, discount | product_name, city, month |

## Database Backup & Disaster Recovery (8)

1. **Difference between incremental backup and differential backup. Which is more suitable for the banking system?** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 319 (ET: N/A)]*

   Answer: Both are partial backups taken between two full backups. The difference is what they measure the change against.

   Incremental backup
   - Copies only the data changed `since the last backup of any kind` — full or incremental.
   - Each incremental therefore covers a small slice of time, so it is the fastest to take and uses the least space.
   - Restoring needs the `full backup plus every incremental in the chain`, applied in order. If one incremental in the middle is lost or corrupt, everything after it is useless.

   Differential backup
   - Copies all the data changed `since the last full backup`.
   - It grows a little bigger every day, because it repeats what the earlier differentials already had.
   - Restoring needs only `the full backup plus the latest differential` — two files.

   Example — full backup on Sunday
   ```
           Incremental                     Differential
   Mon  changes of Mon        (small)   changes since Sun        (small)
   Tue  changes of Tue        (small)   changes of Mon+Tue       (bigger)
   Wed  changes of Wed        (small)   changes of Mon+Tue+Wed   (bigger still)

   Restore on Thursday:
     Incremental  : Full + Mon + Tue + Wed   (4 files, slow, fragile)
     Differential : Full + Wed               (2 files, fast, safe)
   ```

   | Point | Incremental | Differential |
   |---|---|---|
   | Baseline | The last backup of any type | The last full backup |
   | Backup time | Fastest | Slower, grows daily |
   | Storage used | Least | More |
   | Restore time | Slowest — apply the whole chain | Faster — only two sets |
   | Files needed to restore | Full + all incrementals | Full + latest differential |
   | Risk | One broken file breaks the chain | Only two files must be good |
   | Best for | Huge data, narrow backup window | Fast recovery, moderate data |

   Which suits a banking system
   - `Differential` is the safer choice for a bank, because in banking `restore time and reliability matter far more than backup storage cost`. An RTO measured in minutes cannot afford to replay a seven-day incremental chain, and the chain has a single point of failure that incremental backups cannot escape.
   - In practice a bank uses all three together:
   ```
   Weekly   : full backup
   Daily    : differential backup
   Every 15 min : transaction log (archive log) backup
   Continuous   : synchronous replication to the DR site
   ```
   - The log backups give a very small `RPO` — point-in-time recovery to within minutes — while the differential keeps the `RTO` short. Storage is cheap; a bank that cannot reopen on Monday morning is not.

2. **Database Data Loss based case study type question......** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 321 (ET: N/A)]*

3. **What do you understand about the IT disaster recovery plan? Describe your approach to disaster recovery and business continuity planning for the data centre of your office.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 333 (ET: BIBM)]*

   Answer: An `IT disaster recovery (DR) plan` is a written, tested procedure that says how IT systems and data will be brought back after a disaster — fire, flood, power failure, hardware failure, cyber attack or human error. `Business continuity planning (BCP)` is wider: it covers how the whole organisation keeps working while IT is being restored.

   Two numbers drive every DR plan
   ```
   RPO (Recovery Point Objective) : how much data may be lost   -> "at most 15 minutes"
   RTO (Recovery Time Objective)  : how long the outage may last -> "back within 1 hour"
   ```
   - Every technology choice below is decided by these two numbers, so they are agreed with the business first, not with IT.

   Approach for the data centre

   1. Business impact analysis and risk assessment
   - List every system, rank it as critical, important or deferrable, and set an RPO and RTO for each. The core banking system may need RPO 0; the HR portal may tolerate one day.

   2. Backup strategy — the 3-2-1 rule
   ```
   3 copies of the data
   2 different media types
   1 copy off-site (and ideally 1 immutable / offline copy against ransomware)

   Weekly full  +  daily differential  +  15-minute log backup
   ```
   - Backups must be `encrypted`, catalogued, and `test-restored` regularly. An untested backup is not a backup.

   3. Redundancy inside the primary site
   - Dual power feeds, UPS and generator; redundant cooling; RAID storage; clustered servers; dual network paths and dual ISPs; no single point of failure.

   4. A DR site
   ```
   Hot site   : fully equipped, data replicated live, ready in minutes     (high cost)
   Warm site  : hardware ready, data restored from backup, hours to start  (medium)
   Cold site  : space and power only, days to start                        (low cost)
   ```
   - A bank's core system needs a `hot` DR site far enough away that the same flood or earthquake cannot hit both.

   5. Replication
   - `Synchronous` replication to the DR site gives RPO = 0, because a transaction commits only after the standby confirms the write. It needs low latency, so the distance is limited.
   - `Asynchronous` replication works over any distance but loses the last few seconds.
   - Oracle Data Guard, SQL Server Always On availability groups and storage-level mirroring all implement this.

   6. Failover and failback procedure
   - Write, step by step, who declares a disaster, who switches DNS or the load balancer, how the application is pointed at the DR database, and how the systems are brought back to the primary site afterwards.

   7. People and communication
   - A named DR team with deputies, an out-of-hours contact list, an escalation path, and a plan to inform customers and the regulator.

   8. Testing
   - A `tabletop` walkthrough every quarter and a real `failover drill` at least once a year. Record how long it actually took and fix what failed.

   9. Documentation and review
   - Keep runbooks, network diagrams and passwords in a sealed off-site copy — a plan stored only on the failed server is worthless. Review after every major change.

   - Points to note for a Bangladeshi bank: Bangladesh Bank's ICT Security Guideline requires a DR site, periodic DR drills and documented BCP. Cyber recovery now needs `immutable` or air-gapped backups, because ransomware deliberately encrypts the online backups first.

4. **একটি MySQL database এর ডাটা ব্যাক আপ ও ব্যাক আপ করা ডাটা রিস্টোর করার কমান্ড লিখ।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 382 (ET: BUET)]*

   Answer: (Answered in English, as required for IT topics.) MySQL uses the `mysqldump` utility to take a logical backup and the `mysql` client to restore it. These are run from the operating system shell, not from inside the MySQL prompt.

   Backup — mysqldump

   One database
   ```bash
   mysqldump -u root -p bank_db > bank_db_backup.sql
   ```

   One or more specific tables
   ```bash
   mysqldump -u root -p bank_db customer account > tables_backup.sql
   ```

   Several databases
   ```bash
   mysqldump -u root -p --databases bank_db hr_db > multi_backup.sql
   ```

   All databases on the server
   ```bash
   mysqldump -u root -p --all-databases > full_backup.sql
   ```

   A consistent backup of a live InnoDB database, with the binary log position recorded
   ```bash
   mysqldump -u root -p --single-transaction --routines --triggers --events \
             --master-data=2 bank_db > bank_db_backup.sql
   ```

   Compressed backup, to save space
   ```bash
   mysqldump -u root -p bank_db | gzip > bank_db_backup.sql.gz
   ```

   Restore

   Into an existing database
   ```bash
   mysql -u root -p bank_db < bank_db_backup.sql
   ```

   The database must exist first, so create it if needed
   ```bash
   mysql -u root -p -e "CREATE DATABASE bank_db;"
   mysql -u root -p bank_db < bank_db_backup.sql
   ```

   From inside the MySQL prompt
   ```sql
   CREATE DATABASE bank_db;
   USE bank_db;
   SOURCE /home/admin/bank_db_backup.sql;
   ```

   Restoring a compressed backup
   ```bash
   gunzip < bank_db_backup.sql.gz | mysql -u root -p bank_db
   ```

   A backup taken with `--all-databases` already contains the CREATE statements
   ```bash
   mysql -u root -p < full_backup.sql
   ```

   Points to note
   - `mysqldump` produces a `logical` backup — a text file of `CREATE` and `INSERT` statements. It is portable across versions and platforms, but slow to restore for very large databases.
   - `--single-transaction` gives a consistent snapshot of InnoDB tables `without locking them`, so the application keeps running. Do not use `--lock-all-tables` on a production server unless the outage is planned.
   - Add `--routines --triggers --events`, otherwise stored procedures, triggers and scheduled events are silently left out.
   - For very large databases use a `physical` backup tool such as `Percona XtraBackup` or `mysqlbackup`, which copies the data files directly and restores far faster.
   - For point-in-time recovery, restore the dump and then replay the binary log:
   ```bash
   mysqlbinlog --start-datetime="2026-09-04 09:00:00" mysql-bin.000012 | mysql -u root -p
   ```

5. **In the context of data management, what are the primary differences between data recovery and data backup? Provide real-world examples of when each is employed effectively.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 539 (ET: MIST)]*

   Answer: `Data backup` is the act of making an extra copy of data before anything goes wrong. `Data recovery` is the act of bringing data back after something has gone wrong. Backup is preventive and planned; recovery is corrective and reactive.

   Data backup
   - A copy of the data kept on separate storage — disk, tape, or cloud — so that the original can be replaced if lost.
   - Done on a schedule, automatically, whether or not there is a problem.
   - Types: `full`, `differential`, `incremental`, plus transaction log backups for point-in-time recovery.
   - The standard rule is `3-2-1`: three copies, two media types, one copy off-site.
   - Real-world use: a bank runs a full backup every Sunday, a differential every night, and a transaction log backup every 15 minutes. A company laptop syncs to cloud storage continuously. None of this depends on anything failing.

   Data recovery
   - The process of restoring data after loss caused by hardware failure, accidental deletion, corruption, ransomware or a disaster.
   - Two very different situations:
   ```
   Recovery FROM a backup : restore the copy, then roll forward the logs
                            -> planned, fast, reliable
   Recovery WITHOUT a backup : forensic tools, file carving, clean-room
                            work on a failed disk
                            -> expensive, slow, partial success at best
   ```
   - Measured by `RTO` (how long the restore may take) and `RPO` (how much data may be lost).
   - Real-world use: a DBA drops the wrong table at 11 a.m.; the team restores last night's backup and replays the transaction log up to 10:59 a.m. Or a ransomware attack encrypts the file server, and the systems are rebuilt from the immutable off-site copy.

   | Point | Data backup | Data recovery |
   |---|---|---|
   | Nature | Preventive | Corrective |
   | When done | Before loss, on a schedule | After loss, on demand |
   | Frequency | Regular and routine | Rare, only when needed |
   | Cost | Predictable storage cost | Can be very high if no backup exists |
   | Depends on | Policy and automation | The quality of the backup |
   | Success | Almost always | Not guaranteed |
   | Example | Nightly `mysqldump` to off-site storage | Restoring that dump after a disk failure |

   - The link between them: `recovery is only as good as the backup`. A backup that has never been test-restored is not a backup — it is a hope. Banks therefore run periodic restore drills and measure the actual RTO achieved, not the planned one.

6. **To achieve a '0-bit data loss' for its 24 x 7 x 365 banking operation, what steps or technology should an online bank employ to safeguard its data against any potential threats of data loss?** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 518 (ET: MIST)]*

   Answer: `Zero data loss` means `RPO = 0` — not a single committed transaction is lost, even if the primary site is destroyed. For a 24×7 bank this needs several layers working together; no single product gives it.

   1. Synchronous replication to a DR site
   - The single most important step. A transaction commits `only after` the standby site has confirmed that the redo/log record is written on its own disk.
   - Oracle `Data Guard` in Maximum Protection or Maximum Availability mode, SQL Server `Always On` synchronous-commit availability groups, or `MySQL Group Replication`.
   - Cost: extra commit latency, so the DR site must be within a distance where the round trip stays small (typically under 100-150 km). For a longer distance, Oracle's `Far Sync` instance keeps RPO 0 while placing the standby far away.

   2. Write-ahead logging and archive log shipping
   - Every change is written to the log `before` the data page, and the log is forced to disk at commit. This is what makes `durability` real.
   - Archive logs are shipped continuously, giving point-in-time recovery to the second.

   3. Storage-level redundancy
   ```
   RAID 1 / RAID 10   : mirrored disks, survives a disk failure
   Redundant controllers, dual HBAs, dual SAN fabrics
   Storage array mirroring (EMC SRDF, IBM Metro Mirror) between sites
   ```

   4. High-availability clustering at the primary site
   - `Oracle RAC` or SQL Server failover clusters keep the database up when a server dies, so a node failure never becomes a data-loss event.
   - Redundant power (dual feed, UPS, generator), redundant cooling, redundant network paths and dual ISPs.

   5. Multi-layer backup with the 3-2-1 rule
   ```
   3 copies, 2 media types, 1 off-site
   Weekly full + daily differential + 15-minute log backup
   At least one immutable or air-gapped copy against ransomware
   ```
   - Backups encrypted, catalogued and `test-restored` on a schedule.

   6. Geographically separated DR site
   - Far enough that one flood, fire or earthquake cannot take both. Ideally a third, distant site holds an asynchronous copy, so a regional disaster is also survivable.

   7. Transaction-level protection
   - Strict ACID with `Serializable` or `Repeatable Read` where correctness demands it, and two-phase commit for distributed transactions so partial updates cannot survive.

   8. Protection against the non-hardware causes
   - Most real data loss is human or malicious, not physical:
   ```
   Least-privilege access and separation of duties
   No shared DBA accounts; every action logged and audited
   Change control on production; no ad-hoc DELETE without a WHERE review
   Flashback / point-in-time recovery to undo a wrong DELETE quickly
   Anti-ransomware: immutable backups, offline copy, EDR, network segmentation
   ```

   9. Monitoring and drills
   - Alert on replication lag, log-shipping delay, failed backup jobs and full disks — a silent replication break is how "zero data loss" quietly becomes "one week of loss".
   - Run a real failover drill at least once a year and record the actual RTO and RPO achieved.

   - Summary of the architecture:
   ```
   Primary site (RAC cluster, RAID, UPS)
           | synchronous replication  -> RPO 0
   Near DR site (hot standby, same city region)
           | asynchronous replication -> regional disaster
   Far DR site + immutable off-site backup copies
   ```

7. **MySQL database এর ক্ষেত্রে Backup and Restore করার কমান্ড লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 865 (ET: BUET)]*

   Answer: (Answered in English, as required for IT topics.) MySQL is backed up with the `mysqldump` utility and restored with the `mysql` client. Both are run from the operating system shell.

   Backup commands
   ```bash
   # one database
   mysqldump -u root -p bank_db > bank_db.sql

   # specific tables only
   mysqldump -u root -p bank_db customer account > tables.sql

   # several databases
   mysqldump -u root -p --databases bank_db hr_db > multi.sql

   # every database on the server
   mysqldump -u root -p --all-databases > full_backup.sql

   # consistent backup of a live InnoDB database, without locking it
   mysqldump -u root -p --single-transaction --routines --triggers --events \
             bank_db > bank_db.sql

   # compressed
   mysqldump -u root -p bank_db | gzip > bank_db.sql.gz
   ```

   Restore commands
   ```bash
   # the target database must exist first
   mysql -u root -p -e "CREATE DATABASE bank_db;"

   # restore into it
   mysql -u root -p bank_db < bank_db.sql

   # a --all-databases dump already contains CREATE DATABASE
   mysql -u root -p < full_backup.sql

   # from a compressed file
   gunzip < bank_db.sql.gz | mysql -u root -p bank_db
   ```

   From inside the MySQL prompt
   ```sql
   CREATE DATABASE bank_db;
   USE bank_db;
   SOURCE /home/admin/bank_db.sql;
   ```

   Point-in-time recovery
   ```bash
   # restore the dump, then replay the binary log up to the moment before the error
   mysqlbinlog --stop-datetime="2026-09-04 10:59:00" mysql-bin.000012 | mysql -u root -p
   ```

   Points to note
   - `mysqldump` gives a `logical` backup — a text file of `CREATE` and `INSERT` statements. Portable, but slow to restore for a very large database.
   - `--single-transaction` takes a consistent snapshot of InnoDB tables `without locking` them, so the application stays online. Use it on production.
   - Always add `--routines --triggers --events`; without them stored procedures, triggers and scheduled events are silently missing from the dump.
   - For large databases use a `physical` backup tool such as `Percona XtraBackup`, which copies the data files and restores far faster.
   - Restoring overwrites existing data, so verify the target database name before running the command.

8. **Describe what are the ways for no data loss?** *[RAKUB Assistant Database Administrator 2020 compact it 1015-1016 (ET: E-Zone)]*

   Answer: No single technique prevents data loss. Protection is built in layers, so that when one layer fails another still holds. The target is `RPO = 0` — not one committed transaction lost.

   1. Regular, tested backups
   ```
   3-2-1 rule : 3 copies, 2 media types, 1 off-site
   Weekly full + daily differential + 15-minute transaction log backup
   At least one immutable / air-gapped copy against ransomware
   ```
   - Backups must be encrypted and `test-restored` on a schedule. An untested backup is only a hope.

   2. Transaction logging and point-in-time recovery
   - `Write-ahead logging` forces the log record to disk before commit returns, so a crash can be repaired by `redo` and `undo`.
   - Archived logs allow recovery to any second, which is how a wrong `DELETE` at 11:00 is undone by restoring to 10:59.

   3. Replication
   - `Synchronous` replication to a standby — the transaction commits only after the standby has written the log — gives RPO 0. Oracle Data Guard Maximum Protection, SQL Server Always On synchronous commit.
   - `Asynchronous` replication to a distant site protects against a regional disaster, at the cost of a few seconds.

   4. Storage and server redundancy
   ```
   RAID 1 / RAID 10   : mirrored disks survive a disk failure
   Clustered servers  : a node failure does not stop the database
   Dual power, UPS and generator; redundant cooling; dual network paths
   ```

   5. A disaster recovery site
   - A `hot` DR site far enough away that one flood or fire cannot take both, with a documented failover procedure and a yearly live drill.

   6. ACID transactions
   - Atomicity and durability are what stop a half-finished transaction from surviving a crash. Distributed work uses `two-phase commit` so partial updates cannot happen.

   7. Access control and change discipline
   - Most real data loss is human, not physical:
   ```
   Least privilege; no shared DBA accounts
   Separation of duties, and every action audited
   Change control on production; review any DELETE or UPDATE without a WHERE
   Test on a staging copy before running on production
   ```

   8. Security against attack
   - Ransomware targets the online backups first, so keep an offline or immutable copy. Add encryption at rest and in transit, patching, network segmentation and endpoint protection.

   9. Physical and environmental protection
   - Controlled data-centre access, fire suppression, temperature and humidity control, and surge protection.

   10. Monitoring and validation
   - Alert on replication lag, failed backup jobs, disk space and database corruption checks (`DBCC CHECKDB`, `RMAN VALIDATE`). A silently broken replication link is how zero data loss quietly becomes a week of loss.

   - Summary: `backups protect against everything slowly, replication protects against disaster instantly, and access control protects against the most common cause of all — people`. All three are needed.

## PL/SQL & Database Triggers (7)

1. **Explain Database Trigger with example.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

   Answer: A `database trigger` is a block of code stored in the database that runs `automatically` when a defined event happens on a table — an `INSERT`, `UPDATE` or `DELETE`. Nobody calls it; the DBMS fires it.

   - Unlike a stored procedure, a trigger cannot be executed by name and cannot take parameters.

   Syntax
   ```sql
   CREATE OR REPLACE TRIGGER trigger_name
   { BEFORE | AFTER } { INSERT | UPDATE | DELETE } ON table_name
   [ FOR EACH ROW ]
   [ WHEN (condition) ]
   BEGIN
       -- statements
   END;
   ```

   Classification
   ```
   By timing : BEFORE  -> runs before the change; :NEW values can be modified
               AFTER   -> runs after the change; used for auditing
               INSTEAD OF -> used on views, which cannot be updated directly
   By level  : Row-level (FOR EACH ROW) -> once per affected row
               Statement-level          -> once per statement, whatever the row count
   ```
   - Inside a row-level trigger, `:NEW` holds the incoming value and `:OLD` the previous one. On an `INSERT` `:OLD` is null; on a `DELETE` `:NEW` is null.

   Example 1 — validate and default a value before insert
   ```sql
   CREATE OR REPLACE TRIGGER trg_check_salary
   BEFORE INSERT OR UPDATE ON Employee
   FOR EACH ROW
   BEGIN
       IF :NEW.salary < 0 THEN
           RAISE_APPLICATION_ERROR(-20001, 'Salary cannot be negative');
       END IF;
       :NEW.emp_name := UPPER(:NEW.emp_name);
   END;
   ```

   Example 2 — audit trail after an update
   ```sql
   CREATE TABLE Salary_Audit (
       emp_id NUMBER, old_salary NUMBER, new_salary NUMBER,
       changed_by VARCHAR2(30), changed_on DATE
   );

   CREATE OR REPLACE TRIGGER trg_salary_audit
   AFTER UPDATE OF salary ON Employee
   FOR EACH ROW
   BEGIN
       INSERT INTO Salary_Audit
       VALUES (:OLD.emp_id, :OLD.salary, :NEW.salary, USER, SYSDATE);
   END;
   ```
   ```sql
   UPDATE Employee SET salary = 55000 WHERE emp_id = 101;
   -- the trigger fires by itself and writes one row into Salary_Audit
   ```

   Uses
   - Enforcing business rules that a `CHECK` constraint cannot express.
   - Keeping an `audit trail` of who changed what and when.
   - Maintaining derived or summary columns automatically.
   - Preventing invalid operations, such as changing a salary outside office hours.

   Drawbacks
   - Hidden logic — a developer reading only the application code cannot see why the data changed.
   - Hard to debug, and a slow trigger slows down every DML statement on that table.
   - A trigger that updates another table can fire further triggers, which is easy to write and hard to trace.

2. **Database program with base and high- level language (SQL) to find out the interest rate from the given database table.** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 321 (ET: N/A)]*

   Answer: The table is not printed with the question, so the usual `Loan` table is assumed. The method is the same for any table.
   ```sql
   CREATE TABLE Loan (
       loan_id      NUMBER PRIMARY KEY,
       customer_id  NUMBER,
       loan_type    VARCHAR2(20),      -- HOME, CAR, PERSONAL
       principal    NUMBER(12,2),
       interest_rate NUMBER(5,2),      -- percent per year
       tenure_years NUMBER
   );
   ```

   Part 1 — using plain SQL (the high-level, declarative way)

   Read the rate directly
   ```sql
   SELECT loan_id, loan_type, interest_rate
   FROM   Loan
   WHERE  customer_id = 1001;
   ```

   Average, highest and lowest rate per loan type
   ```sql
   SELECT loan_type,
          ROUND(AVG(interest_rate), 2) AS avg_rate,
          MAX(interest_rate) AS max_rate,
          MIN(interest_rate) AS min_rate
   FROM   Loan
   GROUP  BY loan_type;
   ```

   Compute the rate when only the interest amount is known
   ```sql
   SELECT loan_id,
          ROUND((interest_amount * 100) / (principal * tenure_years), 2) AS rate
   FROM   Loan;
   ```
   - Formula used: simple interest `I = P × R × T / 100`, so `R = (I × 100) / (P × T)`.

   Part 2 — using PL/SQL (the procedural, base-language way)

   ```sql
   CREATE OR REPLACE PROCEDURE get_interest_rate (p_loan_id IN NUMBER)
   IS
       v_type      Loan.loan_type%TYPE;
       v_principal Loan.principal%TYPE;
       v_rate      Loan.interest_rate%TYPE;
       v_years     Loan.tenure_years%TYPE;
       v_interest  NUMBER(12,2);
   BEGIN
       SELECT loan_type, principal, interest_rate, tenure_years
       INTO   v_type, v_principal, v_rate, v_years
       FROM   Loan
       WHERE  loan_id = p_loan_id;

       v_interest := (v_principal * v_rate * v_years) / 100;

       DBMS_OUTPUT.PUT_LINE('Loan type      : ' || v_type);
       DBMS_OUTPUT.PUT_LINE('Interest rate  : ' || v_rate || ' %');
       DBMS_OUTPUT.PUT_LINE('Interest amount: ' || v_interest);

   EXCEPTION
       WHEN NO_DATA_FOUND THEN
           DBMS_OUTPUT.PUT_LINE('No loan found with id ' || p_loan_id);
       WHEN OTHERS THEN
           DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
   END;
   /

   EXEC get_interest_rate(101);
   ```

   Using a cursor when many rows must be processed
   ```sql
   DECLARE
       CURSOR c_loan IS SELECT loan_id, loan_type, interest_rate FROM Loan;
   BEGIN
       FOR r IN c_loan LOOP
           DBMS_OUTPUT.PUT_LINE(r.loan_id || ' - ' || r.loan_type
                                || ' - ' || r.interest_rate || '%');
       END LOOP;
   END;
   /
   ```

   Points to note
   - Plain `SQL` says `what` is wanted and is the right tool whenever the answer is a single set of rows.
   - `PL/SQL` adds variables, `IF`, loops, cursors and exception handling, so it is used when the logic needs step-by-step decisions or must handle errors.
   - `%TYPE` ties a variable to the column's data type, so the code does not break if the column definition changes.
   - `SELECT ... INTO` must return exactly one row, otherwise it raises `NO_DATA_FOUND` or `TOO_MANY_ROWS` — which is why the exception block is required.

3. **(c) Define dynamic SQL and trigger with examples.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 693 (ET: N/A)]*

   Answer: Dynamic SQL
   - `Dynamic SQL` is SQL that is `built as a text string while the program is running` and executed at that moment, instead of being written and compiled in advance.
   - It is needed when the table name, column name or the whole `WHERE` clause is not known until run time, and for `DDL` statements, which cannot be written directly inside a PL/SQL block.
   - In Oracle it is run with `EXECUTE IMMEDIATE`.

   ```sql
   DECLARE
       v_table  VARCHAR2(30) := 'Employee';
       v_count  NUMBER;
       v_sql    VARCHAR2(200);
   BEGIN
       -- 1. DDL, which static PL/SQL cannot do
       EXECUTE IMMEDIATE 'CREATE TABLE Temp_Emp (id NUMBER, name VARCHAR2(50))';

       -- 2. table name decided at run time
       v_sql := 'SELECT COUNT(*) FROM ' || v_table || ' WHERE dept_id = :d';
       EXECUTE IMMEDIATE v_sql INTO v_count USING 10;
       DBMS_OUTPUT.PUT_LINE('Rows: ' || v_count);
   END;
   /
   ```
   - The `USING` clause supplies a `bind variable` (`:d`). Bind variables must always be used instead of joining the value into the string, because string concatenation opens the door to `SQL injection` and forces the database to re-parse every statement.

   | Point | Static SQL | Dynamic SQL |
   |---|---|---|
   | Written | At compile time | At run time, as a string |
   | Checked | At compile time | Only when executed |
   | Speed | Faster, plan is reused | Slower, needs parsing |
   | DDL allowed | No | Yes |
   | Risk | Safe | SQL injection if not bound |

   Trigger
   - A `trigger` is a stored block of code that the DBMS runs `automatically` when an `INSERT`, `UPDATE` or `DELETE` happens on a table. It cannot be called by name and takes no parameters.
   - Timing is `BEFORE`, `AFTER` or `INSTEAD OF`; level is row (`FOR EACH ROW`) or statement. Inside a row trigger, `:NEW` is the incoming value and `:OLD` the previous one.

   ```sql
   -- validate before the change
   CREATE OR REPLACE TRIGGER trg_check_salary
   BEFORE INSERT OR UPDATE ON Employee
   FOR EACH ROW
   BEGIN
       IF :NEW.salary < 0 THEN
           RAISE_APPLICATION_ERROR(-20001, 'Salary cannot be negative');
       END IF;
   END;
   /

   -- audit after the change
   CREATE OR REPLACE TRIGGER trg_salary_audit
   AFTER UPDATE OF salary ON Employee
   FOR EACH ROW
   BEGIN
       INSERT INTO Salary_Audit
       VALUES (:OLD.emp_id, :OLD.salary, :NEW.salary, USER, SYSDATE);
   END;
   /
   ```
   ```sql
   UPDATE Employee SET salary = 55000 WHERE emp_id = 101;
   -- both triggers fire on their own; no call is written anywhere
   ```
   - Used for business rules a `CHECK` cannot express, audit trails, and maintaining derived columns. The drawback is hidden logic that is hard to debug.

4. **(b) Describe the application of trigger in database.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 795 (ET: N/A)]*

   Answer: A `trigger` is a stored block of code that the DBMS runs automatically when an `INSERT`, `UPDATE` or `DELETE` happens on a table. Its applications are the jobs that must happen every time, regardless of which program made the change.

   1. Auditing — who changed what and when
   - The most common use. Banks and government systems are required to keep this trail.
   ```sql
   CREATE OR REPLACE TRIGGER trg_salary_audit
   AFTER UPDATE OF salary ON Employee
   FOR EACH ROW
   BEGIN
       INSERT INTO Salary_Audit
       VALUES (:OLD.emp_id, :OLD.salary, :NEW.salary, USER, SYSDATE);
   END;
   /
   ```

   2. Enforcing complex business rules
   - Rules a `CHECK` constraint cannot express, because they involve other tables or other rows.
   - Example: a withdrawal must not take the balance below the minimum; a loan cannot be approved by the officer who applied for it.

   3. Maintaining derived and summary columns
   - Keeping a running total in sync automatically.
   ```sql
   CREATE OR REPLACE TRIGGER trg_update_total
   AFTER INSERT ON Order_Item
   FOR EACH ROW
   BEGIN
       UPDATE Orders
       SET    total_amount = total_amount + (:NEW.qty * :NEW.price)
       WHERE  order_id = :NEW.order_id;
   END;
   /
   ```

   4. Referential integrity that a foreign key cannot handle
   - Cross-table rules, cascading actions on views, or checks that depend on a condition.

   5. Data validation and standardisation
   - Converting a name to upper case, trimming spaces, or generating a code before the row is stored. This must be a `BEFORE` trigger, because only there can `:NEW` be modified.

   6. Automatic value generation
   - Setting `created_on := SYSDATE` and `created_by := USER` on every insert, or filling a sequence number.

   7. Security and access control
   - Blocking a change made outside office hours, or from an unexpected user.
   ```sql
   IF TO_CHAR(SYSDATE,'HH24') NOT BETWEEN '09' AND '17' THEN
       RAISE_APPLICATION_ERROR(-20002, 'Changes allowed only in office hours');
   END IF;
   ```

   8. Replication and synchronisation
   - Writing every change into a queue table that another system reads, when the DBMS's own replication is not used.

   9. Preventing invalid operations
   - Stopping a `DELETE` on a master table, or rejecting an update to a closed accounting period.

   10. Making a view updatable
   - An `INSTEAD OF` trigger redirects an insert on a join view to the correct base tables.

   Points to note
   - Triggers are `hidden logic`. A developer reading the application code cannot see why the data changed, so they must be documented.
   - A slow trigger slows down every DML statement on that table.
   - Triggers can `cascade` — one trigger fires another — which is easy to write and painful to trace. Where a constraint can do the job, prefer the constraint.

5. **Suppose, ‘Employee’ table (emp_id, emp_name, dept_id, salary) and ‘Department’ table (dept_id, dept_name, increment_dept). Create a tigger to increment the salary of the employee by 10% whose salary is above 30000.** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 862 (ET: BUET)]*

   Answer: The question as written cannot be done exactly as stated, and the exam answer should say why and then give the working version.

   - A trigger on `Employee` cannot `UPDATE Employee` itself in a row-level trigger. Oracle raises the `mutating table` error `ORA-04091`, because the table is in the middle of being changed.
   - The correct way is a `BEFORE` trigger that changes `:NEW.salary` directly. In a `BEFORE` trigger the row has not been written yet, so assigning to `:NEW` is allowed and costs no extra statement.

   The trigger
   ```sql
   CREATE OR REPLACE TRIGGER trg_increment_salary
   BEFORE INSERT OR UPDATE OF salary ON Employee
   FOR EACH ROW
   WHEN (NEW.salary > 30000)
   BEGIN
       :NEW.salary := :NEW.salary * 1.10;      -- 10% increment
   END;
   /
   ```
   - `WHEN (NEW.salary > 30000)` filters the rows before the body runs. Note that inside `WHEN` the colon is not written.
   - Equivalent form without `WHEN`:
   ```sql
   CREATE OR REPLACE TRIGGER trg_increment_salary
   BEFORE INSERT OR UPDATE OF salary ON Employee
   FOR EACH ROW
   BEGIN
       IF :NEW.salary > 30000 THEN
           :NEW.salary := :NEW.salary * 1.10;
       END IF;
   END;
   /
   ```

   Testing it
   ```sql
   INSERT INTO Employee VALUES (101, 'Rahim', 10, 40000);
   SELECT salary FROM Employee WHERE emp_id = 101;    -- 44000

   INSERT INTO Employee VALUES (102, 'Karim', 10, 25000);
   SELECT salary FROM Employee WHERE emp_id = 102;    -- 25000, unchanged
   ```

   Using the Department table's own increment rate
   - The `Department` table has an `increment_dept` column, so a more realistic trigger reads the rate from there.
   ```sql
   CREATE OR REPLACE TRIGGER trg_dept_increment
   BEFORE INSERT OR UPDATE OF salary ON Employee
   FOR EACH ROW
   DECLARE
       v_rate Department.increment_dept%TYPE;
   BEGIN
       IF :NEW.salary > 30000 THEN
           SELECT increment_dept INTO v_rate
           FROM   Department
           WHERE  dept_id = :NEW.dept_id;

           :NEW.salary := :NEW.salary * (1 + v_rate / 100);
       END IF;
   EXCEPTION
       WHEN NO_DATA_FOUND THEN
           NULL;                                -- no rate set, leave salary as is
   END;
   /
   ```

   If a one-time raise is wanted rather than a trigger
   ```sql
   UPDATE Employee SET salary = salary * 1.10 WHERE salary > 30000;
   ```

   Points to state
   - `BEFORE` trigger, because `:NEW` can be assigned only there. An `AFTER` trigger cannot change the row.
   - `FOR EACH ROW`, because the rule applies per employee, not per statement.
   - Reading `Employee` inside a row trigger on `Employee` causes ORA-04091; reading another table such as `Department` is fine.

6. **(a) What is the purpose of database trigger? Explain with an example.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)]*

   Answer: Purpose of a database trigger
   - A `trigger` is a block of code stored in the database that runs `automatically` when a defined event — `INSERT`, `UPDATE` or `DELETE` — happens on a table. It cannot be called by name and takes no parameters.
   - Its purpose is to make a rule apply `every time, to every program`. Logic written in one application can be bypassed by a second application, a script or a direct SQL session; logic in a trigger cannot.

   What it is used for
   - Enforcing business rules that a `CHECK` constraint cannot express, because they involve other tables or other rows.
   - Keeping an `audit trail` of who changed what and when — required in banking and government systems.
   - Maintaining derived or summary columns automatically, such as an order total.
   - Validating and standardising data before it is stored.
   - Filling automatic values: `created_on`, `created_by`, a sequence number.
   - Blocking invalid operations, such as a change to a closed accounting period.
   - Making a view updatable, through an `INSTEAD OF` trigger.

   Types
   ```
   Timing : BEFORE     -> runs before the change; :NEW can be modified here
            AFTER      -> runs after the change; used for auditing
            INSTEAD OF -> on views
   Level  : Row-level (FOR EACH ROW) -> once per affected row
            Statement-level          -> once per statement
   ```
   - `:NEW` is the incoming value, `:OLD` the previous one. On `INSERT`, `:OLD` is null; on `DELETE`, `:NEW` is null.

   Example — audit every salary change
   ```sql
   CREATE TABLE Salary_Audit (
       emp_id NUMBER, old_salary NUMBER, new_salary NUMBER,
       changed_by VARCHAR2(30), changed_on DATE
   );

   CREATE OR REPLACE TRIGGER trg_salary_audit
   AFTER UPDATE OF salary ON Employee
   FOR EACH ROW
   BEGIN
       INSERT INTO Salary_Audit
       VALUES (:OLD.emp_id, :OLD.salary, :NEW.salary, USER, SYSDATE);
   END;
   /
   ```
   ```sql
   UPDATE Employee SET salary = 55000 WHERE emp_id = 101;

   SELECT * FROM Salary_Audit;
   -- 101 | 50000 | 55000 | SCOTT | 04-SEP-26
   ```
   - Nobody wrote a call to the trigger. The `UPDATE` alone caused the audit row to appear, and it would appear equally if the update came from a web application, a batch job or SQL*Plus.

   Example — validate before the change
   ```sql
   CREATE OR REPLACE TRIGGER trg_check_salary
   BEFORE INSERT OR UPDATE ON Employee
   FOR EACH ROW
   BEGIN
       IF :NEW.salary < 0 THEN
           RAISE_APPLICATION_ERROR(-20001, 'Salary cannot be negative');
       END IF;
   END;
   /
   ```

   - Drawbacks to mention: triggers are hidden logic that is hard to debug, they slow down every DML statement on the table, and one trigger can fire another and cascade. Where an ordinary constraint can do the job, use the constraint.

7. **Write a program in pl/SQL to find the heighest paid employees from employee table and store the data in HighestPaidEmp table.** *[Dutch Bangla Bank Ltd. Probationary Officer (Software) 2018 compact it 1199 (ET: N/A)]*

   Answer: Tables assumed
   ```sql
   CREATE TABLE Employee (
       emp_id   NUMBER PRIMARY KEY,
       emp_name VARCHAR2(50),
       dept_id  NUMBER,
       salary   NUMBER(12,2)
   );

   CREATE TABLE HighestPaidEmp (
       emp_id     NUMBER,
       emp_name   VARCHAR2(50),
       dept_id    NUMBER,
       salary     NUMBER(12,2),
       copied_on  DATE
   );
   ```

   Program 1 — the simple case, one highest-paid employee
   ```sql
   DECLARE
       v_emp_id   Employee.emp_id%TYPE;
       v_name     Employee.emp_name%TYPE;
       v_dept     Employee.dept_id%TYPE;
       v_salary   Employee.salary%TYPE;
   BEGIN
       SELECT emp_id, emp_name, dept_id, salary
       INTO   v_emp_id, v_name, v_dept, v_salary
       FROM   Employee
       WHERE  salary = (SELECT MAX(salary) FROM Employee)
       AND    ROWNUM = 1;

       INSERT INTO HighestPaidEmp
       VALUES (v_emp_id, v_name, v_dept, v_salary, SYSDATE);

       COMMIT;
       DBMS_OUTPUT.PUT_LINE('Inserted: ' || v_name || ' - ' || v_salary);

   EXCEPTION
       WHEN NO_DATA_FOUND THEN
           DBMS_OUTPUT.PUT_LINE('Employee table is empty');
       WHEN OTHERS THEN
           ROLLBACK;
           DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
   END;
   /
   ```

   Program 2 — with a cursor, so that ties are all stored
   ```sql
   DECLARE
       CURSOR c_top IS
           SELECT emp_id, emp_name, dept_id, salary
           FROM   Employee
           WHERE  salary = (SELECT MAX(salary) FROM Employee);

       v_count NUMBER := 0;
   BEGIN
       FOR r IN c_top LOOP
           INSERT INTO HighestPaidEmp
           VALUES (r.emp_id, r.emp_name, r.dept_id, r.salary, SYSDATE);
           v_count := v_count + 1;
       END LOOP;

       COMMIT;
       DBMS_OUTPUT.PUT_LINE(v_count || ' row(s) inserted');

   EXCEPTION
       WHEN OTHERS THEN
           ROLLBACK;
           DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
   END;
   /
   ```

   Program 3 — highest paid employee of each department
   ```sql
   BEGIN
       INSERT INTO HighestPaidEmp
       SELECT emp_id, emp_name, dept_id, salary, SYSDATE
       FROM   Employee e
       WHERE  salary = (SELECT MAX(salary) FROM Employee
                        WHERE dept_id = e.dept_id);
       COMMIT;
   END;
   /
   ```

   The same job as a single SQL statement
   ```sql
   INSERT INTO HighestPaidEmp
   SELECT emp_id, emp_name, dept_id, salary, SYSDATE
   FROM   Employee
   WHERE  salary = (SELECT MAX(salary) FROM Employee);
   ```

   Points to note
   - Use `= (SELECT MAX(salary) ...)`, not `ORDER BY salary DESC` with `ROWNUM = 1` alone. `ROWNUM` is assigned before the sort, so `WHERE ROWNUM = 1 ORDER BY salary DESC` returns a random row, which is a common exam trap.
   - `SELECT ... INTO` fails with `TOO_MANY_ROWS` if two employees share the top salary, which is exactly why the cursor version exists.
   - `%TYPE` ties each variable to its column's data type, so a change to the table does not break the code.
   - Always `COMMIT` on success and `ROLLBACK` in the exception block, otherwise a partial insert can be left behind.

## SQL Joins & Operations (7)

1. **What are the different types of join in SQL?** *[DESCO Assistant Engineer 20.05.2023 compact it 580 (ET: DESCO)]*

   Answer: A `JOIN` combines rows from two or more tables based on a related column between them, usually a foreign key.

   Sample tables
   ```
   Employee                       Department
   +--------+-------+---------+   +---------+--------+
   | emp_id | name  | dept_id |   | dept_id | name   |
   +--------+-------+---------+   +---------+--------+
   | 101    | Rahim | 10      |   | 10      | CSE    |
   | 102    | Karim | 20      |   | 20      | EEE    |
   | 103    | Jamal | NULL    |   | 30      | ME     |  <- no employee
   +--------+-------+---------+   +---------+--------+
   ```

   1. INNER JOIN
   - Returns only the rows that `match on both sides`. Unmatched rows from either table are dropped.
   ```sql
   SELECT e.name, d.name
   FROM Employee e INNER JOIN Department d ON e.dept_id = d.dept_id;
   ```
   ```
   Rahim | CSE
   Karim | EEE          -- Jamal and ME are excluded
   ```

   2. LEFT OUTER JOIN
   - All rows from the `left` table, plus the matching rows from the right. Where there is no match, the right columns come back `NULL`.
   ```
   Rahim | CSE
   Karim | EEE
   Jamal | NULL         -- kept, though he has no department
   ```

   3. RIGHT OUTER JOIN
   - All rows from the `right` table, plus matches from the left; unmatched left columns are `NULL`.
   ```
   Rahim | CSE
   Karim | EEE
   NULL  | ME           -- kept, though nobody works in ME
   ```

   4. FULL OUTER JOIN
   - All rows from `both` tables. Unmatched rows on either side get NULLs.
   ```
   Rahim | CSE
   Karim | EEE
   Jamal | NULL
   NULL  | ME
   ```

   5. CROSS JOIN
   - Every row of the first table paired with every row of the second — the `Cartesian product`. 3 rows × 3 rows = 9 rows. No `ON` clause. Written by accident when the join condition is forgotten.

   6. SELF JOIN
   - A table joined to itself, using two aliases. Used for hierarchies.
   ```sql
   SELECT e.name AS employee, m.name AS manager
   FROM Employee e JOIN Employee m ON e.manager_id = m.emp_id;
   ```

   7. NATURAL JOIN
   - Joins automatically on `all columns with the same name`. Short to write but risky, because adding a column later can silently change the result.

   ```
      INNER          LEFT           RIGHT          FULL
      +---+---+     +===+---+     +---+===+     +===+===+
      | A |*B*|     |*A*|*B*|     | A |*B*|     |*A*|*B*|
      +---+---+     +===+---+     +---+===+     +===+===+
      only matches  all of A      all of B      all of both
   ```

   | Join | Returns |
   |---|---|
   | INNER | Only matching rows |
   | LEFT OUTER | All left rows + matches |
   | RIGHT OUTER | All right rows + matches |
   | FULL OUTER | All rows from both sides |
   | CROSS | Every combination |
   | SELF | A table joined to itself |

   - MySQL has no `FULL OUTER JOIN`; it is written as a `LEFT JOIN UNION RIGHT JOIN`.

2. **Left joning and inner joining of a table.** *[BTCL Assistant Manager (Technical) 2023 compact it 594 (ET: BUET)]*

   Answer: Both combine rows from two tables using a matching column. The difference is what happens to rows that have `no match`.

   Sample tables
   ```
   Employee                       Department
   +--------+-------+---------+   +---------+-----------+
   | emp_id | name  | dept_id |   | dept_id | dept_name |
   +--------+-------+---------+   +---------+-----------+
   | 101    | Rahim | 10      |   | 10      | CSE       |
   | 102    | Karim | 20      |   | 20      | EEE       |
   | 103    | Jamal | NULL    |   | 30      | ME        |
   +--------+-------+---------+   +---------+-----------+
   ```

   INNER JOIN
   - Returns only the rows where the condition matches on `both` sides. Any row without a partner is dropped.
   ```sql
   SELECT e.name, d.dept_name
   FROM   Employee e
   INNER  JOIN Department d ON e.dept_id = d.dept_id;
   ```
   ```
   name  | dept_name
   ------+----------
   Rahim | CSE
   Karim | EEE

   Jamal is dropped (no department), ME is dropped (no employee)
   ```

   LEFT JOIN (LEFT OUTER JOIN)
   - Returns `every row of the left table`, and the matching data from the right table where it exists. Where there is no match, the right-hand columns come back as `NULL`.
   ```sql
   SELECT e.name, d.dept_name
   FROM   Employee e
   LEFT   JOIN Department d ON e.dept_id = d.dept_id;
   ```
   ```
   name  | dept_name
   ------+----------
   Rahim | CSE
   Karim | EEE
   Jamal | NULL        <- kept, with NULL

   ME is still dropped, because it is on the right side
   ```

   ```
      INNER JOIN                LEFT JOIN
      +-----+-----+            +=====+-----+
      |  A  |**B**|            |**A**|**B**|
      +-----+-----+            +=====+-----+
      only the overlap         all of A, plus the overlap
   ```

   The most useful pattern — finding what is missing
   ```sql
   -- employees who belong to no department
   SELECT e.name
   FROM   Employee e
   LEFT   JOIN Department d ON e.dept_id = d.dept_id
   WHERE  d.dept_id IS NULL;
   ```

   | Point | INNER JOIN | LEFT JOIN |
   |---|---|---|
   | Rows returned | Only matching rows | All left rows + matches |
   | Unmatched left rows | Dropped | Kept, right columns NULL |
   | Unmatched right rows | Dropped | Dropped |
   | Row count | ≤ smaller side | ≥ number of left rows |
   | NULLs in the result | None from the join | Yes, where no match |
   | Used for | Rows that exist in both | Full list plus optional detail |

   - A common mistake: putting a condition on the right table in the `WHERE` clause of a LEFT JOIN. `WHERE d.dept_name = 'CSE'` removes the NULL rows and silently turns the LEFT JOIN back into an INNER JOIN. Put such a condition in the `ON` clause instead.

3. **Which join is used for including not matching all records with output?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

   Answer: The `FULL OUTER JOIN` includes all records from both tables, matching or not.

   - It returns every row from the left table and every row from the right table. Where a row on one side has no partner on the other, the missing columns come back as `NULL`.

   ```sql
   SELECT e.name, d.dept_name
   FROM   Employee e
   FULL   OUTER JOIN Department d ON e.dept_id = d.dept_id;
   ```

   ```
   Employee                     Department
   101 Rahim  dept 10           10  CSE
   102 Karim  dept 20           20  EEE
   103 Jamal  dept NULL         30  ME

   Result:
   name  | dept_name
   ------+----------
   Rahim | CSE          <- matched
   Karim | EEE          <- matched
   Jamal | NULL         <- unmatched left row, kept
   NULL  | ME           <- unmatched right row, kept
   ```

   Related answers, depending on how the question is meant
   - Non-matching rows from `one` side only: `LEFT OUTER JOIN` keeps all left rows, `RIGHT OUTER JOIN` keeps all right rows.
   - `Only` the non-matching rows on both sides:
   ```sql
   SELECT e.name, d.dept_name
   FROM   Employee e
   FULL   OUTER JOIN Department d ON e.dept_id = d.dept_id
   WHERE  e.dept_id IS NULL OR d.dept_id IS NULL;
   ```

   ```
      FULL OUTER JOIN
      +=======+=======+
      |***A***|***B***|
      +=======+=======+
      everything from both sides
   ```

   Points to note
   - Oracle, SQL Server and PostgreSQL support `FULL OUTER JOIN` directly. `OUTER` is optional in the keyword.
   - MySQL does `not` have it, so it is written as the union of a left and a right join:
   ```sql
   SELECT e.name, d.dept_name FROM Employee e
   LEFT JOIN Department d ON e.dept_id = d.dept_id
   UNION
   SELECT e.name, d.dept_name FROM Employee e
   RIGHT JOIN Department d ON e.dept_id = d.dept_id;
   ```
   - It is used mainly for `reconciliation` — comparing two lists to find what exists in one but not the other, such as matching a bank's own transaction list against the card switch's list.

4. **What is inner join? Explain with syntax and example.** *[Bangladesh Television Assistant Programmer 2019 compact it 1065 (ET: N/A)]*

   Answer: An `INNER JOIN` combines rows from two tables and returns only the rows where the join condition is `true on both sides`. Any row without a partner in the other table is left out.

   Syntax
   ```sql
   SELECT column_list
   FROM   table1
   INNER  JOIN table2
   ON     table1.column = table2.column
   [WHERE condition];
   ```
   - `INNER` is optional — writing `JOIN` alone means an inner join in every major DBMS.
   - The older form puts the condition in the `WHERE` clause. It works, but the `ON` form is preferred because the join condition and the filter stay separate.
   ```sql
   SELECT e.name, d.dept_name
   FROM   Employee e, Department d
   WHERE  e.dept_id = d.dept_id;         -- old style, same result
   ```

   Example
   ```
   Employee                       Department
   +--------+-------+---------+   +---------+-----------+
   | emp_id | name  | dept_id |   | dept_id | dept_name |
   +--------+-------+---------+   +---------+-----------+
   | 101    | Rahim | 10      |   | 10      | CSE       |
   | 102    | Karim | 20      |   | 20      | EEE       |
   | 103    | Jamal | NULL    |   | 30      | ME        |
   +--------+-------+---------+   +---------+-----------+
   ```
   ```sql
   SELECT e.emp_id, e.name, d.dept_name
   FROM   Employee e
   INNER  JOIN Department d ON e.dept_id = d.dept_id;
   ```
   ```
   emp_id | name  | dept_name
   -------+-------+----------
   101    | Rahim | CSE
   102    | Karim | EEE

   Jamal is excluded : his dept_id is NULL, so it matches nothing
   ME is excluded    : no employee has dept_id 30
   ```

   With a filter and three tables
   ```sql
   SELECT e.name, d.dept_name, p.project_name
   FROM   Employee e
   JOIN   Department d ON e.dept_id = d.dept_id
   JOIN   Project p    ON p.emp_id  = e.emp_id
   WHERE  d.dept_name = 'CSE';
   ```

   ```
      INNER JOIN
      +-----+-----+
      |  A  |**B**|      only the overlapping part is returned
      +-----+-----+
   ```

   Points to note
   - `NULL` never matches anything, not even another `NULL`, so a row with a NULL in the join column is always dropped by an inner join.
   - The result has at most as many rows as the smaller side — unless the join column has duplicates, in which case the rows multiply.
   - Forgetting the `ON` clause turns the query into a `CROSS JOIN` and returns every combination of rows.
   - Use an inner join when only rows that exist in both tables are wanted; use a `LEFT JOIN` when the unmatched rows must be kept.

5. **(b) Explain JOIN and INNER-JOIN procedure.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1143 (ET: N/A)]*

   Answer: JOIN
   - A `JOIN` is the SQL operation that combines rows from two or more tables using a related column, normally a foreign key matching a primary key. It is what makes a normalized design usable: data is split across tables to avoid redundancy, and joins put it back together for a report.
   - General form:
   ```sql
   SELECT column_list
   FROM   table1
   JOIN   table2 ON table1.column = table2.column;
   ```
   - Types: `INNER`, `LEFT OUTER`, `RIGHT OUTER`, `FULL OUTER`, `CROSS`, `SELF` and `NATURAL`.

   INNER JOIN
   - Returns only the rows where the condition is `true on both sides`. Unmatched rows on either side are dropped. Writing `JOIN` alone means `INNER JOIN`.

   Procedure — how the DBMS actually performs it
   ```
   1. Read the join condition from the ON clause
   2. Take a row from the outer (usually smaller) table
   3. Find the rows in the inner table whose join column matches
   4. Combine the matched pair into one output row
   5. Discard rows with no match
   6. Repeat for every row of the outer table
   7. Apply the WHERE filter and the SELECT list to the result
   ```
   - The optimiser picks one of three physical methods:
   ```
   Nested loop join : for each outer row, look up the inner table
                      -> good when the inner side has an index
   Hash join        : build a hash table on the smaller side, probe with the
                      larger -> best for large equi-joins
   Sort-merge join  : sort both sides on the join key, then merge
                      -> good when the data is already sorted
   ```

   Example
   ```
   Employee                       Department
   +--------+-------+---------+   +---------+-----------+
   | emp_id | name  | dept_id |   | dept_id | dept_name |
   +--------+-------+---------+   +---------+-----------+
   | 101    | Rahim | 10      |   | 10      | CSE       |
   | 102    | Karim | 20      |   | 20      | EEE       |
   | 103    | Jamal | NULL    |   | 30      | ME        |
   +--------+-------+---------+   +---------+-----------+
   ```
   ```sql
   SELECT e.name, d.dept_name
   FROM   Employee e
   INNER  JOIN Department d ON e.dept_id = d.dept_id;
   ```
   ```
   Rahim | CSE
   Karim | EEE          -- Jamal and ME are dropped
   ```

   Points to note
   - `NULL` matches nothing, so a NULL in the join column always removes the row from an inner join.
   - Index the join column — usually the foreign key — or the join falls back to scanning the inner table for every outer row.
   - Forgetting the `ON` clause produces a `CROSS JOIN` and every combination of rows, which is the classic cause of a query that never finishes.

6. **Define: (i) Left outer join (ii) Right outer join (iii) Full outer join (iv) One to many and (v) Many to many** *[Dutch Bangla Bank Ltd. Probationary Officer (Software) 2018 compact it 1199 (ET: N/A)]*

   Answer: (i) Left outer join
   - Returns `all rows from the left table`, plus the matching rows from the right table. Where the right table has no match, its columns come back as `NULL`.
   ```sql
   SELECT e.name, d.dept_name
   FROM   Employee e LEFT OUTER JOIN Department d ON e.dept_id = d.dept_id;
   ```
   ```
   Rahim | CSE
   Karim | EEE
   Jamal | NULL      <- employee with no department, still shown
   ```
   - Used to list everything on one side with optional detail from the other, and to find missing rows with `WHERE d.dept_id IS NULL`.

   (ii) Right outer join
   - Returns `all rows from the right table`, plus the matching rows from the left. Unmatched left columns become `NULL`.
   ```sql
   SELECT e.name, d.dept_name
   FROM   Employee e RIGHT OUTER JOIN Department d ON e.dept_id = d.dept_id;
   ```
   ```
   Rahim | CSE
   Karim | EEE
   NULL  | ME        <- department with no employee, still shown
   ```
   - Any right join can be rewritten as a left join by swapping the tables, which is why it is used far less often.

   (iii) Full outer join
   - Returns `all rows from both tables`. Unmatched rows on either side get NULLs in the missing columns.
   ```
   Rahim | CSE
   Karim | EEE
   Jamal | NULL
   NULL  | ME
   ```
   - Used for reconciliation — finding what exists in one list but not the other. MySQL has no `FULL OUTER JOIN`; it is written as `LEFT JOIN UNION RIGHT JOIN`.

   ```
      LEFT           RIGHT          FULL
      +===+---+     +---+===+     +===+===+
      |*A*|*B*|     | A |*B*|     |*A*|*B*|
      +===+---+     +---+===+     +===+===+
      all of A      all of B      all of both
   ```

   (iv) One to many (1:N)
   - A `relationship` in which one row of table A can be linked to many rows of table B, while each row of B links to only one row of A.
   - Example: one `Department` has many `Employee` rows; each employee works in one department.
   - Implementation: put the `foreign key on the many side`.
   ```sql
   CREATE TABLE Employee (
     emp_id  INT PRIMARY KEY,
     dept_id INT REFERENCES Department(dept_id)
   );
   ```
   - This is the most common relationship in real databases.

   (v) Many to many (M:N)
   - Many rows of A relate to many rows of B.
   - Example: a `Student` takes many `Course` rows, and each course has many students.
   - A relational table cannot store this directly, so a third `junction table` is created whose primary key is the pair of foreign keys.
   ```sql
   CREATE TABLE Enrollment (
     student_id INT REFERENCES Student(student_id),
     course_id  INT REFERENCES Course(course_id),
     grade      CHAR(2),
     PRIMARY KEY (student_id, course_id)
   );
   ```
   - The junction table is also the natural place for attributes of the relationship itself, such as the grade or the enrollment date.

7. **What join should use when there is no match between two tables?** *[DESCO Assistant Engineer (CSE) 2016 compact it 1266 (ET: N/A)]*

   Answer: When rows that have `no match` in the other table must still appear, an `OUTER JOIN` is used. Which one depends on which side's unmatched rows are needed.

   ```
   FULL OUTER JOIN  -> keeps unmatched rows from BOTH tables
   LEFT OUTER JOIN  -> keeps unmatched rows from the LEFT table only
   RIGHT OUTER JOIN -> keeps unmatched rows from the RIGHT table only
   ```
   - An `INNER JOIN` cannot be used, because it drops every row without a partner.

   Sample data
   ```
   Employee                       Department
   101 Rahim  dept 10             10  CSE
   102 Karim  dept 20             20  EEE
   103 Jamal  dept NULL           30  ME
   ```

   FULL OUTER JOIN — nothing is lost from either side
   ```sql
   SELECT e.name, d.dept_name
   FROM   Employee e
   FULL   OUTER JOIN Department d ON e.dept_id = d.dept_id;
   ```
   ```
   Rahim | CSE
   Karim | EEE
   Jamal | NULL      <- employee with no department
   NULL  | ME        <- department with no employee
   ```

   LEFT OUTER JOIN — every employee, matched or not
   ```sql
   SELECT e.name, d.dept_name
   FROM   Employee e
   LEFT   JOIN Department d ON e.dept_id = d.dept_id;
   ```

   Listing `only` the non-matching rows
   ```sql
   -- employees who belong to no department
   SELECT e.name
   FROM   Employee e
   LEFT   JOIN Department d ON e.dept_id = d.dept_id
   WHERE  d.dept_id IS NULL;

   -- unmatched rows on both sides at once
   SELECT e.name, d.dept_name
   FROM   Employee e
   FULL   OUTER JOIN Department d ON e.dept_id = d.dept_id
   WHERE  e.emp_id IS NULL OR d.dept_id IS NULL;
   ```

   Points to note
   - MySQL has no `FULL OUTER JOIN`. Use `LEFT JOIN ... UNION ... RIGHT JOIN`.
   - Test the unmatched side with `IS NULL`, never with `= NULL`, which is always unknown.
   - In a LEFT JOIN, a condition on the right table belongs in the `ON` clause. Putting it in `WHERE` removes the NULL rows and quietly turns the query back into an inner join.

## Distributed & Parallel Databases (5)

1. **(খ) Speedup এবং Scaleup চিত্রসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 613 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) `Speedup` and `scaleup` are the two measures used to judge how well a parallel or distributed database uses extra hardware.

   Speedup — same work, more machines
   - `Speedup` means running the `same fixed task` faster by adding more resources. The problem size stays constant; only the hardware grows.
   ```
   Speedup = (time taken on the small system) / (time taken on the large system)
   ```
   - Example: a query takes 100 seconds on 1 node. On 10 nodes it takes 10 seconds → speedup = 10.
   - `Linear speedup` is the ideal: n times the hardware gives n times the speed. Real systems fall short (`sublinear`) because of start-up cost, interference for shared resources, and skew, where one node gets more data than the others.

   ```
      Speedup
         |            ideal (linear)
      10 |          /
         |        /
       5 |      /  . . . . actual (sublinear)
         |    / . '
       1 |__/_'________________________
         1    5    10   -> number of nodes
         (problem size FIXED)
   ```

   Scaleup — more work and more machines together
   - `Scaleup` means handling a `larger task` in the `same time` by adding proportionally more resources. Both the problem and the hardware grow together.
   ```
   Scaleup = (small problem on small system time) / (big problem on big system time)
   ```
   - Example: 1 node processes 1 GB in 60 seconds. If 10 nodes process 10 GB also in 60 seconds → scaleup = 1, which is linear.

   ```
      Time
         |
      60 |. . . . . . . . . .  ideal (linear scaleup, flat line)
         |            . '
         |      . '            actual (sublinear, time creeps up)
         |__________________________
         1GB/1node  5GB/5nodes  10GB/10nodes
         (problem size GROWS with the hardware)
   ```

   Two forms of each
   ```
   Batch scaleup       : the database size grows (bigger tables, same query)
   Transaction scaleup : the number of transactions grows (more users)
   ```

   | Point | Speedup | Scaleup |
   |---|---|---|
   | Problem size | Fixed | Grows with the hardware |
   | Hardware | Increased | Increased |
   | Goal | Finish the same job faster | Finish a bigger job in the same time |
   | Ideal value | n (linear) | 1 (flat) |
   | Measures | Response time | Capacity |
   | Example | 100 s on 1 node → 10 s on 10 nodes | 1 GB/1 node and 10 GB/10 nodes both 60 s |

   - Why the ideal is never reached: `start-up cost` of launching many processes, `interference` on shared disks and network, and `skew` — an uneven split of data means the slowest node decides the finish time. Good partitioning of the data is what keeps skew low.

2. **(ক) Data Fragmentation কী? ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 613 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) `Data fragmentation` is the process of dividing one logical table into smaller pieces, called `fragments`, and storing those pieces at different sites of a distributed database.

   - The purpose is to keep data `close to the users who use it`, so most queries are answered locally instead of over the network.
   - Three rules must hold for the fragmentation to be correct:
   ```
   Completeness : every row and column of the original table is in some fragment
   Reconstruction : the original table can be rebuilt exactly from the fragments
   Disjointness : a data item is not stored twice (except the key in vertical
                  fragmentation, and except where replication is deliberate)
   ```

   Types

   (a) Horizontal fragmentation — split by `rows`
   - The table is divided by a condition on the rows, using the `selection` operation.
   ```sql
   Employee_Dhaka     = SELECT * FROM Employee WHERE branch = 'Dhaka';
   Employee_Chattogram= SELECT * FROM Employee WHERE branch = 'Chattogram';
   ```
   ```
             Employee (whole table)
      +--------+-------+-------------+
      | emp_id | name  | branch      |
      +--------+-------+-------------+
      | 101    | Rahim | Dhaka       |  --> fragment 1, stored in Dhaka
      | 102    | Karim | Dhaka       |  --> fragment 1
      | 103    | Jamal | Chattogram  |  --> fragment 2, stored in Chattogram
      +--------+-------+-------------+
   ```
   - Rebuilt with `UNION`. Best when different sites use different sets of rows — the normal case for a bank's branches.
   - `Derived horizontal fragmentation` splits a child table the same way as its parent, so that a join stays local.

   (b) Vertical fragmentation — split by `columns`
   - The table is divided by columns, using the `projection` operation. The `primary key is repeated in every fragment`, otherwise the table cannot be rebuilt.
   ```sql
   Emp_Personal = SELECT emp_id, name, address FROM Employee;   -- HR site
   Emp_Payroll  = SELECT emp_id, salary, tax   FROM Employee;   -- Accounts site
   ```
   - Rebuilt with a `natural join` on the key. Best when different departments use different columns, and it also helps security — payroll columns are simply not stored at the HR site.

   (c) Mixed (hybrid) fragmentation
   - Both applied together: first split by rows, then split those pieces by columns, or the reverse.
   - Example: split `Employee` by branch, then split each branch's fragment into personal and payroll columns.

   ```mermaid
   flowchart TD
       A[Employee table] --> B[Horizontal: by branch]
       B --> C[Dhaka rows]
       B --> D[Chattogram rows]
       C --> E[Personal columns]
       C --> F[Payroll columns]
   ```

   Advantages
   - Faster local queries, because most data needed at a site is stored there.
   - Less network traffic and lower cost.
   - Better security — a site holds only what it needs.
   - Parallel processing, since fragments can be scanned at the same time.

   Disadvantages
   - A query that needs several fragments must join across the network, which is slow.
   - Harder to keep consistent, and recursive fragmentation makes the design complex.

3. **What is distributed database?** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 660 (ET: N/A)]*

   Answer: A `distributed database` is a single logical database whose data is physically stored across several computers, at different locations, connected by a network. To the user it looks and behaves like one ordinary database — the fact that the data is spread out is hidden.

   - The software that manages it is a `DDBMS` (Distributed Database Management System). It handles where the data lives, how a query is split, and how the sites are kept consistent.

   ```mermaid
   flowchart LR
       U[User / application] --> D[DDBMS]
       D --> A[(Site 1 - Dhaka)]
       D --> B[(Site 2 - Chattogram)]
       D --> C[(Site 3 - Khulna)]
   ```

   Key ideas
   - `Fragmentation` — one table is split into pieces: `horizontal` by rows (Dhaka branch rows in Dhaka), `vertical` by columns, or `mixed`.
   - `Replication` — the same data is kept at more than one site, which improves availability and read speed but makes updates harder.
   - `Transparency` — the user does not need to know any of this:
   ```
   Location transparency   : no need to know which site holds the data
   Fragmentation transparency : the table looks whole
   Replication transparency : the user does not know how many copies exist
   ```

   Types
   - `Homogeneous` — every site runs the same DBMS product and schema. Easier to manage.
   - `Heterogeneous` — sites run different products (Oracle at one, MySQL at another). Needs a translation layer.

   Advantages
   - `Reliability and availability` — one site failing does not stop the whole system.
   - `Faster local access`, because data sits near the users who use it.
   - `Modular growth` — a new branch is added by adding a site, without replacing the central machine.
   - `Lower communication cost`, since most queries are answered locally.
   - Matches how an organisation is actually organised, branch by branch.

   Disadvantages
   - `Complex` design, query optimisation and administration.
   - Keeping copies consistent needs `two-phase commit`, which is slow and blocks if a site fails.
   - Higher software cost and a larger `security surface`, because data travels over the network.
   - A query that needs several sites can be very slow.

   - Real example: a bank keeping each branch's accounts on that branch's server, while head office can still query all branches as one table. A centralized database, by contrast, keeps everything on one machine — simpler, but a single point of failure.

4. **Which of the following distributed database system over centralized database system? (a) Software cost (b) Software complexity (c) Slow response (d) Modular growth** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

   Answer: (d) Modular growth

   - `Modular growth` is the clear advantage of a distributed database over a centralized one. A new branch or region is added simply by adding another site to the network — the existing sites keep running and nothing has to be replaced. In a centralized system, growth means buying a bigger machine and taking downtime to migrate to it.

   Why the other options are wrong — they are `disadvantages`, not advantages
   - `(a) Software cost` — a DDBMS costs `more`, not less. Extra licences, extra hardware and extra staff are needed at each site.
   - `(b) Software complexity` — a distributed system is far `more` complex: distributed query optimisation, two-phase commit, replication control and distributed deadlock detection all have to be handled.
   - `(c) Slow response` — response is generally `faster`, because data is stored near the users who use it and most queries are answered locally.

   Other genuine advantages of a distributed database
   - `Reliability and availability` — one site failing does not bring down the whole system, whereas a centralized database is a single point of failure.
   - `Local autonomy` — each site controls and manages its own data.
   - `Lower communication cost`, since most access is local.
   - `Parallel processing` — a query can be answered by several sites at once.
   - It matches the way an organisation is actually structured, branch by branch.

   The real disadvantages, for completeness
   ```
   Higher software and hardware cost
   Much greater complexity in design and administration
   Harder to keep data consistent (needs two-phase commit)
   Larger security surface, because data crosses the network
   Slow cross-site queries when several sites must be joined
   ```

5. **Explain the concept distributed DBMS. What are the features of DBMS?** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1054 (ET: BUET)]*

   Answer: Concept of a distributed DBMS
   - A `distributed DBMS (DDBMS)` is the software that manages a single logical database whose data is physically stored on several computers at different locations, connected by a network. The user sees one ordinary database; the distribution is hidden.

   ```mermaid
   flowchart LR
       U[User / application] --> D[DDBMS]
       D --> A[(Site 1 - Dhaka)]
       D --> B[(Site 2 - Chattogram)]
       D --> C[(Site 3 - Khulna)]
   ```

   - `Fragmentation` splits a table into pieces: `horizontal` by rows, `vertical` by columns, or `mixed`.
   - `Replication` keeps the same data at more than one site, improving availability and read speed at the cost of harder updates.
   - `Transparency` hides the details — location, fragmentation and replication transparency all mean the user writes an ordinary SQL query.
   - `Homogeneous` DDBMS runs the same product everywhere; `heterogeneous` mixes different products and needs a translation layer.
   - A transaction spanning several sites is committed with `two-phase commit`, so either all sites commit or none does.
   - Advantages: reliability, local speed, modular growth. Disadvantages: complexity, cost, and slow cross-site joins.

   Features of a DBMS
   - `Data storage and retrieval` — the DBMS manages files, pages and buffers, so the user never handles files directly.
   - `Data independence` — `logical` independence means the application survives a schema change; `physical` independence means it survives a change in storage or indexing.
   - `Reduced redundancy and consistency` — data is stored once and shared, so the same fact does not disagree between two files.
   - `Data integrity` — primary key, foreign key, `CHECK` and `NOT NULL` constraints are enforced by the DBMS itself.
   - `Transaction management with ACID` — atomicity, consistency, isolation and durability for every unit of work.
   - `Concurrency control` — locking or MVCC lets many users work at once without seeing each other's half-finished changes.
   - `Recovery` — write-ahead logging, checkpoints, undo and redo bring the database back after a crash.
   - `Security` — user accounts, `GRANT` and `REVOKE` privileges, views that expose only certain columns, and encryption.
   - `Query language` — SQL, a declarative language, plus a query optimiser that decides how to run the query.
   - `Multiple views` — each user group sees only the part of the schema it needs.
   - `Backup and restore utilities`, an active `data dictionary`, and import/export tools.
   - `Multi-user access` with authentication and an audit trail.

## Database Design & Data Types (3)

1. An institute wants to create a database table named STUDENT to store student information. The table should include the columns Roll Number, Name, Department, Email, and Admission Date. Specify the most appropriate SQL data type for each column and identify which column should be defined as the Primary Key, giving a brief justification for your choice. *[Officer (IT) 31 Jul 2026 bscs 03 (ET: N/A)]*

   Answer: Table design
   ```sql
   CREATE TABLE Student (
       roll_number    INT           PRIMARY KEY,
       name           VARCHAR(100)  NOT NULL,
       department     VARCHAR(50)   NOT NULL,
       email          VARCHAR(100)  UNIQUE NOT NULL,
       admission_date DATE          NOT NULL DEFAULT CURRENT_DATE
   );
   ```

   Data type for each column

   | Column | Data type | Why |
   |---|---|---|
   | Roll Number | `INT` | A whole number, fixed and small. Integer comparison and indexing are the fastest. Use `VARCHAR(15)` only if the roll carries letters or leading zeros, as in "CSE-2021-005" |
   | Name | `VARCHAR(100)` | Names vary in length, so a variable-length type wastes no space. `CHAR` would pad every short name with blanks |
   | Department | `VARCHAR(50)` | Same reason. If the list of departments is fixed and short, a `dept_id INT` foreign key to a `Department` table is better still |
   | Email | `VARCHAR(100)` | Variable length; 100 covers practical addresses. Mark it `UNIQUE`, since no two students share an e-mail |
   | Admission Date | `DATE` | Stores year, month and day and allows date arithmetic and `BETWEEN`. Never store a date as `VARCHAR` — sorting and comparison then break |

   Primary key — `roll_number`
   - It is `unique`, since the institute issues one roll number to one student and never repeats it.
   - It is `never NULL`; every admitted student is given a roll number at admission.
   - It is `stable` — a student's roll number does not change, while a name, department or e-mail can.
   - It is `small and numeric`, so the index is compact and joins from other tables (`Result`, `Attendance`, `Fees`) are fast.

   Why not the other columns
   - `Name` — not unique. Two students can both be "Rahim Uddin", and a name can also be corrected later.
   - `Department` — clearly not unique; hundreds of students share one.
   - `Email` — it `is` unique, so it is a valid `candidate key` and should carry a `UNIQUE` constraint. It is not chosen as the primary key because it can change, it may be missing for a new student, and it is a long string that makes every foreign key in every child table large.

   - If the institute has no reliable natural key, a `surrogate key` — `student_id INT AUTO_INCREMENT PRIMARY KEY` — is used instead, with `roll_number` kept as a `UNIQUE` column.

2. **(c) Describe the difference between CHAR and VARCHAR data type.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 795 (ET: N/A)]*

   Answer: Both store character strings. The difference is whether the length is `fixed` or `variable`.

   CHAR(n)
   - A `fixed-length` type. Every value takes exactly n characters. A shorter value is padded with trailing spaces.
   - `CHAR(10)` storing 'BD' occupies 10 characters — 'BD' plus 8 spaces.
   - Because every row's value is the same size, the DBMS knows exactly where each value starts, so access is slightly faster.
   - Trailing spaces are usually stripped when the value is read back, which can surprise a comparison.

   VARCHAR(n)
   - A `variable-length` type. Only the actual characters are stored, plus 1 or 2 bytes recording the length. n is only the maximum allowed.
   - `VARCHAR(50)` storing 'Rahim' occupies about 6 bytes, not 50.
   - Saves a large amount of space when values differ in length, which is the usual case.

   ```
   CHAR(10) storing 'BD'         VARCHAR(10) storing 'BD'
   +---+---+---+---+---+...      +---+---+---+
   | B | D |   |   |   |         | 2 | B | D |
   +---+---+---+---+---+...      +---+---+---+
      10 characters always        length byte + 2 characters
   ```

   | Point | CHAR | VARCHAR |
   |---|---|---|
   | Length | Fixed at n | Variable, up to n |
   | Padding | Padded with spaces | No padding |
   | Storage | Always n characters | Actual length + 1-2 length bytes |
   | Space use | Wasteful for varying data | Efficient |
   | Speed | Slightly faster, fixed offset | Slightly slower, length must be read |
   | Fragmentation on update | None — size never changes | Possible, if the new value is longer |
   | Max length | 255 in MySQL | 65,535 in MySQL (row limit applies) |
   | Best for | Values of one known length | Values of differing length |

   When to use which
   - `CHAR` — country code `CHAR(2)`, gender `CHAR(1)`, PIN `CHAR(4)`, blood group `CHAR(3)`, a fixed-format account number. Anything where every value genuinely has the same length.
   - `VARCHAR` — name, address, e-mail, designation, remarks. Anything where length varies.

   - A practical warning: comparison of `CHAR` values ignores trailing spaces in most systems, so `'BD'` and `'BD  '` compare equal, while in `VARCHAR` they may not. This causes hard-to-find bugs when the same value is stored in a `CHAR` column in one table and a `VARCHAR` column in another.

3. **What is the domain in a relational database? Explain with an example. Show how you would use Alter table SQL command to add a domain on a database table.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 916 (ET: N/A)]*

   Answer: A `domain` is the set of all `permitted values` that an attribute (column) may take. It defines the data type, the length, the format and the range that a value must satisfy to be valid.

   - Example domains:
   ```
   Age            : integer, 18 to 60
   Gender         : 'M' or 'F'
   Email          : a string containing '@'
   Salary         : decimal, greater than 0
   Blood group    : 'A+', 'A-', 'B+', 'B-', 'O+', 'O-', 'AB+', 'AB-'
   ```
   - Every value in a column must belong to that column's domain. Enforcing this is called `domain integrity`, one of the integrity rules of the relational model.
   - Domains are `atomic`: one cell holds one indivisible value, not a list. That is the requirement of `1NF`.

   Example
   ```sql
   CREATE TABLE Employee (
       emp_id  INT PRIMARY KEY,
       name    VARCHAR(50) NOT NULL,
       age     INT,
       gender  CHAR(1),
       salary  DECIMAL(10,2)
   );
   ```
   - The declared data types already set part of the domain — `age` can only hold integers. But nothing yet stops an age of 200 or a gender of 'X', so a `CHECK` constraint is added.

   Adding a domain constraint with ALTER TABLE
   ```sql
   -- restrict age to a valid working range
   ALTER TABLE Employee
   ADD CONSTRAINT chk_age CHECK (age BETWEEN 18 AND 60);

   -- restrict gender to two values
   ALTER TABLE Employee
   ADD CONSTRAINT chk_gender CHECK (gender IN ('M', 'F'));

   -- salary must be positive
   ALTER TABLE Employee
   ADD CONSTRAINT chk_salary CHECK (salary > 0);

   -- the column must always have a value
   ALTER TABLE Employee
   MODIFY name VARCHAR(50) NOT NULL;
   ```

   Testing it
   ```sql
   INSERT INTO Employee VALUES (101, 'Rahim', 30, 'M', 45000);   -- accepted
   INSERT INTO Employee VALUES (102, 'Karim', 70, 'M', 45000);   -- rejected, age
   INSERT INTO Employee VALUES (103, 'Jamal', 30, 'X', 45000);   -- rejected, gender
   ```

   Removing a domain constraint
   ```sql
   ALTER TABLE Employee DROP CONSTRAINT chk_age;     -- Oracle, PostgreSQL, SQL Server
   ALTER TABLE Employee DROP CHECK chk_age;          -- MySQL
   ```

   A named domain object
   - The SQL standard also allows a reusable domain, supported by PostgreSQL and Oracle 23c:
   ```sql
   CREATE DOMAIN age_domain AS INT CHECK (VALUE BETWEEN 18 AND 60);

   ALTER TABLE Employee
   ALTER COLUMN age TYPE age_domain;
   ```
   - The advantage is that the rule is written once and reused by every table that needs it, so a change is made in one place.

   - Points to note: always `name` the constraint, so the error message identifies the rule and the constraint can be dropped by name. Adding a constraint to a table that already holds bad rows fails, so the existing data must be cleaned first.

## NoSQL, NewSQL & Modern Databases (2)

1. **What are the limitations of DBMS and how to related newsql with SQL and No-SQL.** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1332 (ET: BUET)]*

   Answer: Limitations of a traditional DBMS (relational, SQL)
   - `Hard to scale out.` It scales up on one bigger machine well, but spreading one database across many machines is difficult, because joins and ACID must then hold across a network.
   - `Rigid schema.` The structure must be fixed before data is loaded, and altering a large live table is slow and risky.
   - `Poor fit for unstructured data` — documents, images, logs, social graphs and sensor streams do not fit rows and columns.
   - `Joins get expensive` as tables grow; a heavily normalized design can need a dozen joins for one report.
   - `Cost` — commercial licences, powerful hardware and trained DBAs.
   - `Impedance mismatch` — program objects must be flattened into rows and rebuilt, which is why ORM tools exist.
   - `Single point of failure` in a centralized deployment, and limited write throughput because one node owns the writes.

   NoSQL — the answer to scale, at a price
   - Drops the fixed schema and, usually, joins. Data is stored as documents, key-value pairs, wide columns or graphs.
   - Scales `horizontally` across cheap machines by sharding, and handles very large, fast, varied data.
   - Relaxes ACID to `BASE` — Basically Available, Soft state, Eventual consistency. By the CAP theorem, when the network partitions, it usually keeps availability and gives up strict consistency.
   - The price: `no strong transactional guarantee`, limited query power, no standard language, and application code must handle the data that used to be handled by joins and constraints. That is unacceptable for a bank ledger.

   NewSQL — the bridge between the two
   - `NewSQL` is a class of modern relational systems that keep the `relational model, SQL and full ACID`, but obtain NoSQL-style `horizontal scalability` for OLTP workloads.
   - How it does this:
   ```
   Sharding / partitioning the data across many nodes automatically
   Distributed consensus (Raft, Paxos) instead of a single master
   In-memory or log-structured storage, so no disk seek per transaction
   Lock-free concurrency control (MVCC, optimistic, or deterministic scheduling)
   ```
   - Examples: `Google Spanner`, `CockroachDB`, `VoltDB`, `TiDB`, `YugabyteDB`, `MemSQL/SingleStore`, `NuoDB`, and MySQL Cluster.

   How the three relate

   | Point | SQL (RDBMS) | NoSQL | NewSQL |
   |---|---|---|---|
   | Data model | Tables, fixed schema | Document, key-value, column, graph | Tables, fixed schema |
   | Query language | SQL | Product-specific API | SQL |
   | Transactions | Full ACID | BASE, eventual consistency | Full ACID |
   | Scaling | Vertical (scale up) | Horizontal (scale out) | Horizontal (scale out) |
   | Joins | Yes | Usually not | Yes |
   | Best for | Banking, ERP, accounting | Big data, feeds, IoT, catalogues | High-volume OLTP that still needs ACID |
   | Maturity | Very mature | Mature | Newest, fewest tools |

   - The relationship in one line: `NewSQL = the correctness and SQL of a relational database + the horizontal scalability of NoSQL`. It exists because SQL could not scale out and NoSQL could not guarantee correctness.
   - NewSQL's own limitations: fewer features and tools than a mature RDBMS, a smaller pool of skilled people, and the extra latency that distributed consensus adds to every commit. It is chosen only when the workload genuinely outgrows a single relational server.

2. **Write difference between relational database and NoSQL database.** *[Sonali Bank Ltd. Officer IT 2021 compact it 909 (ET: N/A)]*

   Answer: A `relational database` stores data in tables with a fixed schema and links them by keys. A `NoSQL database` stores data in flexible formats — documents, key-value pairs, wide columns or graphs — and is built to spread across many machines.

   Relational database
   - Data is held in `tables` of rows and columns; the structure must be defined before data is loaded.
   - Tables are linked by `foreign keys` and combined with `joins`.
   - Queried with `SQL`, a standard declarative language.
   - Guarantees `ACID` for every transaction.
   - Designed by `normalization`, so a fact is stored once.
   - Scales `vertically` — a bigger server.
   - Examples: Oracle, MySQL, PostgreSQL, SQL Server.

   NoSQL database
   - `Schema-free`: two documents in the same collection may have different fields, so the structure can change without an `ALTER TABLE`.
   - Four families:
   ```
   Document    : MongoDB, CouchDB          -> JSON-like documents
   Key-value   : Redis, DynamoDB           -> a value fetched by its key
   Column-family: Cassandra, HBase         -> wide rows, huge write volume
   Graph       : Neo4j                     -> nodes and edges, relationship queries
   ```
   - Usually no joins; related data is `embedded` in the same document instead.
   - Follows `BASE` — Basically Available, Soft state, Eventual consistency — rather than strict ACID.
   - Scales `horizontally` by sharding across cheap servers.

   ```
   Relational                     NoSQL (document)
   +--------+-------+---------+   {
   | emp_id | name  | dept_id |     "emp_id": 101,
   +--------+-------+---------+     "name": "Rahim",
   | 101    | Rahim | 10      |     "dept": { "id": 10, "name": "CSE" },
   +--------+-------+---------+     "skills": ["SQL", "Java"]
      plus a Department table     }
   ```

   | Point | Relational database | NoSQL database |
   |---|---|---|
   | Data model | Tables, rows, columns | Document, key-value, column, graph |
   | Schema | Fixed, defined in advance | Flexible, can differ per record |
   | Query language | SQL, standard | Product-specific API or query language |
   | Transactions | Full ACID | BASE, usually eventual consistency |
   | Joins | Yes | Usually none; data is embedded |
   | Scaling | Vertical — a bigger machine | Horizontal — more machines |
   | Data type suited | Structured | Semi-structured and unstructured |
   | Consistency | Strong | Eventual, mostly |
   | Best for | Banking, ERP, accounting, reporting | Big data, real-time feeds, IoT, catalogues |
   | Examples | Oracle, MySQL, PostgreSQL | MongoDB, Cassandra, Redis, Neo4j |

   - How to choose: if the data is structured and every transaction must be exactly right, use `relational`. If the volume is huge, the shape varies and losing a second of consistency is acceptable, use `NoSQL`. Large systems often use both — the ledger in an RDBMS, the activity log and search index in NoSQL.

## Database Connectivity (JDBC) (2)

1. What is JDBC? Explain the steps required to connect a Java application to a MySQL database. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

   Answer: `JDBC` (Java Database Connectivity) is the standard Java API that lets a Java program connect to a database, send SQL statements and read the results. It sits in the `java.sql` package and hides the differences between database products — the same Java code works with MySQL, Oracle or PostgreSQL by changing only the driver and the URL.

   ```mermaid
   flowchart LR
       A[Java application] --> B[JDBC API]
       B --> C[JDBC driver<br/>Connector/J]
       C --> D[(MySQL database)]
   ```

   Main interfaces
   ```
   DriverManager     : finds the driver and opens the connection
   Connection        : one session with the database
   Statement         : sends a plain SQL statement
   PreparedStatement : sends a pre-compiled SQL statement with parameters
   ResultSet         : the rows returned by a query
   ```

   Steps to connect a Java application to MySQL

   1. Add the driver
   - Put `mysql-connector-j-8.x.x.jar` on the classpath, or add the Maven dependency. Without it the program fails with `No suitable driver`.

   2. Load and register the driver
   ```java
   Class.forName("com.mysql.cj.jdbc.Driver");
   ```
   - Since JDBC 4.0 this line is optional, because the driver registers itself automatically, but it is still written in exams.

   3. Establish the connection
   ```java
   String url  = "jdbc:mysql://localhost:3306/bank_db";
   String user = "root";
   String pass = "secret";
   Connection con = DriverManager.getConnection(url, user, pass);
   ```
   - URL format: `jdbc:mysql://<host>:<port>/<database>`. Port 3306 is MySQL's default.

   4. Create a statement
   ```java
   PreparedStatement ps =
       con.prepareStatement("SELECT emp_id, name FROM Employee WHERE dept_id = ?");
   ps.setInt(1, 10);
   ```

   5. Execute it
   ```java
   ResultSet rs = ps.executeQuery();          // for SELECT
   // int n = ps.executeUpdate();             // for INSERT, UPDATE, DELETE
   ```

   6. Process the result
   ```java
   while (rs.next()) {
       System.out.println(rs.getInt("emp_id") + " - " + rs.getString("name"));
   }
   ```

   7. Close the resources
   ```java
   rs.close(); ps.close(); con.close();
   ```

   Complete program
   ```java
   import java.sql.*;

   public class DbDemo {
       public static void main(String[] args) {
           String url = "jdbc:mysql://localhost:3306/bank_db";
           String sql = "SELECT emp_id, name FROM Employee WHERE dept_id = ?";

           try (Connection con = DriverManager.getConnection(url, "root", "secret");
                PreparedStatement ps = con.prepareStatement(sql)) {

               ps.setInt(1, 10);
               try (ResultSet rs = ps.executeQuery()) {
                   while (rs.next()) {
                       System.out.println(rs.getInt("emp_id") + " - "
                                        + rs.getString("name"));
                   }
               }
           } catch (SQLException e) {
               e.printStackTrace();
           }
       }
   }
   ```

   Points to note
   - Use `try-with-resources`, as above. It closes the connection even when an exception is thrown; a leaked connection eventually exhausts the pool.
   - Always prefer `PreparedStatement` over `Statement`. It blocks `SQL injection`, because a parameter is never treated as SQL, and it is faster since the plan is reused.
   - In production, connections come from a `connection pool` (HikariCP, Tomcat JDBC), not from `DriverManager` on every request — opening a connection is expensive.
   - For a transaction, call `con.setAutoCommit(false)`, then `con.commit()` or `con.rollback()`.

2. **(b) Explain embedded SQL with an appropriate example.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 693 (ET: N/A)]*

   Answer: `Embedded SQL` means SQL statements written directly inside the source code of a `host language` such as C, C++, COBOL or Java. The program gets the computing power of the host language and the data-handling power of SQL in one place.

   - The SQL is `static` — written and known at compile time — so it can be checked and optimised in advance. This is the opposite of `dynamic SQL`, which is built as a string at run time.

   How it is compiled
   ```
      source.pc  --->  Precompiler  --->  source.c  --->  C compiler  --->  program
      (C + SQL)        (Pro*C)            (pure C with        |
                                           library calls)     v
                                                          database
   ```
   - A `precompiler` reads the mixed file, replaces every SQL statement with a call to the DBMS runtime library, and produces ordinary host-language source.

   Rules
   - Every SQL statement begins with `EXEC SQL` and ends with the host language's terminator (`;` in C).
   - `Host variables` — ordinary program variables used inside SQL — are declared in a declare section and prefixed with a colon inside SQL statements.
   - `SQLCA` (SQL Communications Area) carries the status back; `SQLCODE` is 0 on success, 100 when no row was found, and negative on error.
   - A query returning many rows must use a `cursor`, because a C variable can hold only one value.

   Example in C (Oracle Pro*C)
   ```c
   #include <stdio.h>
   EXEC SQL INCLUDE SQLCA;

   int main() {
       EXEC SQL BEGIN DECLARE SECTION;
           int     emp_id;
           char    emp_name[50];
           float   salary;
           char    user[30] = "scott/tiger";
       EXEC SQL END DECLARE SECTION;

       EXEC SQL CONNECT :user;

       /* single row : SELECT ... INTO */
       emp_id = 101;
       EXEC SQL SELECT emp_name, salary
                INTO   :emp_name, :salary
                FROM   Employee
                WHERE  emp_id = :emp_id;

       printf("Name: %s  Salary: %.2f\n", emp_name, salary);

       /* update and commit */
       EXEC SQL UPDATE Employee SET salary = salary * 1.10
                WHERE emp_id = :emp_id;
       EXEC SQL COMMIT WORK;

       return 0;
   }
   ```

   Reading many rows with a cursor
   ```c
   EXEC SQL DECLARE c_emp CURSOR FOR
            SELECT emp_id, emp_name FROM Employee WHERE dept_id = :dept;

   EXEC SQL OPEN c_emp;

   while (1) {
       EXEC SQL FETCH c_emp INTO :emp_id, :emp_name;
       if (sqlca.sqlcode == 100) break;          /* no more rows */
       printf("%d %s\n", emp_id, emp_name);
   }

   EXEC SQL CLOSE c_emp;
   ```

   | Point | Embedded (static) SQL | Dynamic SQL |
   |---|---|---|
   | Written | At compile time | Built as a string at run time |
   | Syntax checked | By the precompiler | Only when executed |
   | Speed | Faster, plan prepared once | Slower, must be parsed |
   | Flexibility | Fixed statement | Table and columns can vary |
   | Risk | Safe | SQL injection if values are concatenated |

   - Advantages: compile-time checking, better performance, and the host language supplies the logic SQL lacks. Drawbacks: it needs a precompiler, the code is tied to that DBMS, and modern applications mostly use `JDBC` or `ODBC` call-level interfaces instead.

## Relational Keys (Candidate, Super, Primary, Foreign Key) (1)

1. **Employee table( NID, Company_ID, Name, Mobile Number). Assume every record has a unique Mobile number. Find the number of super key, candidate key. And give example of two candidate key.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 399 (ET: BUET)]*

## Indexing in DBMS (1)

1. **সূচকের ধরন কি? এখানে প্রশ্নের উত্তর বিষয়ভিত্তিক প্রকার লেখ।** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*
