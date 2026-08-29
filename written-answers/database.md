<!-- TOC START -->
**Table of Contents** — 19 subtopics · 229 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [SQL Queries](#sql-queries-71) | 71 |
| 2 | [DBMS Architecture & Features](#dbms-architecture--features-22) | 22 |
| 3 | [ER Diagram & Database Design](#er-diagram--database-design-21) | 21 |
| 4 | [Keys in DBMS](#keys-in-dbms-21) | 21 |
| 5 | [Normalization & Database Design](#normalization--database-design-18) | 18 |
| 6 | [SQL Commands (DDL, DML, DCL, TCL)](#sql-commands-ddl-dml-dcl-tcl-13) | 13 |
| 7 | [Transaction Management & ACID Properties](#transaction-management--acid-properties-12) | 12 |
| 8 | [Relational Data Model & ER Relationships](#relational-data-model--er-relationships-11) | 11 |
| 9 | [Database Backup & Disaster Recovery](#database-backup--disaster-recovery-8) | 8 |
| 10 | [PL/SQL & Database Triggers](#plsql--database-triggers-6) | 6 |
| 11 | [Indexing & Query Optimization (B-Tree, B+ Tree)](#indexing--query-optimization-b-tree-b-tree-6) | 6 |
| 12 | [Distributed & Parallel Databases](#distributed--parallel-databases-4) | 4 |
| 13 | [Data Warehousing, Data Mining & Business Intelligence](#data-warehousing-data-mining--business-intelligence-4) | 4 |
| 14 | [Database Design & Data Types](#database-design--data-types-3) | 3 |
| 15 | [SQL Joins & Operations](#sql-joins--operations-3) | 3 |
| 16 | [NoSQL, NewSQL & Modern Databases](#nosql-newsql--modern-databases-2) | 2 |
| 17 | [Database Connectivity (JDBC)](#database-connectivity-jdbc-2) | 2 |
| 18 | [Relational Keys (Candidate, Super, Primary, Foreign Key)](#relational-keys-candidate-super-primary-foreign-key-1) | 1 |
| 19 | [Indexing in DBMS](#indexing-in-dbms-1) | 1 |

<!-- TOC END -->

---

## SQL Queries (71)

1. Consider the following relation: **Employee(EmpID, Name, Department, Salary)**. Write an SQL query to retrieve the **Department**, the **total number of employees**, and the **average salary** for each department. The output should display one record for each department. [SO IT 25-07-2026]


   Answer:

   ```sql
   SELECT Department,
          COUNT(*)      AS TotalEmployees,
          AVG(Salary)   AS AverageSalary
   FROM   Employee
   GROUP  BY Department;
   ```

   Explanation:
   - `GROUP BY Department` collapses all the rows of each department into a single group, which is what produces one record per department.
   - `COUNT(*)` counts the rows in each group, that is the number of employees in that department.
   - `AVG(Salary)` computes the mean salary within each group.
   - Every column in the SELECT list must either appear in the GROUP BY clause or be an aggregate function; `Department` satisfies the first condition and the other two the second.

   Refinements worth adding:
   - To round the average: `ROUND(AVG(Salary), 2) AS AverageSalary`.
   - To order the output: add `ORDER BY AverageSalary DESC`.
   - To exclude employees with no department: add `WHERE Department IS NOT NULL`.
   - To restrict the output to departments meeting a condition, use HAVING rather than WHERE, since WHERE is applied before grouping and HAVING after: `HAVING COUNT(*) > 5`.
2. Consider a STUDENTS table with the following attributes: StudentID, Name, Department, Marks (10 Marks)
   * **I.** Write an SQL query to display only StudentID, Name, and Marks for students scoring more than 80 marks.
   * **II.** Write an SQL query to count how many students scored more than 80 marks in each Department. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*


   Answer:

   (I) Students scoring more than 80 marks:

   ```sql
   SELECT StudentID, Name, Marks
   FROM   STUDENTS
   WHERE  Marks > 80;
   ```

   - `WHERE` filters individual rows before any grouping, so only the qualifying students are returned. Only the three requested columns are listed, rather than using `SELECT *`.

   (II) Count of students scoring more than 80 marks in each department:

   ```sql
   SELECT Department, COUNT(*) AS StudentsAbove80
   FROM   STUDENTS
   WHERE  Marks > 80
   GROUP  BY Department;
   ```

   - The order of evaluation matters here: `WHERE Marks > 80` removes the unqualified rows first, and `GROUP BY Department` then counts what remains within each department.
   - Using `HAVING Marks > 80` instead would be wrong, because HAVING is applied after grouping and operates on aggregates, not on individual rows.
   - To list only departments having at least one such student, the query above already does so, since a department with none forms no group. To include departments with a zero count, a LEFT JOIN against a Department table would be required.
   - To order the result: add `ORDER BY StudentsAbove80 DESC`.
3. **SQL Query: Find department name and Average salary form 2 table Department and Employee.......** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1334 (ET: BUET)]*
   Department table
   Department (dept_id, dept_name)
   Employee table
   Employee (emp_id, emp_name, salary, dept_id)


   Answer:

   ```sql
   SELECT d.dept_name,
          AVG(e.salary) AS average_salary
   FROM   Department d
   JOIN   Employee e ON d.dept_id = e.dept_id
   GROUP  BY d.dept_id, d.dept_name;
   ```

   Explanation:
   - The two tables are joined on `dept_id`, which is the primary key of Department and the foreign key in Employee.
   - `GROUP BY` collapses the joined rows by department, and `AVG(e.salary)` computes the mean salary within each group.
   - Grouping by `d.dept_id` as well as `d.dept_name` is safer, because two departments could share a name; the identifier guarantees correct grouping.

   Variation, to include departments that have no employees:

   ```sql
   SELECT d.dept_name,
          COALESCE(AVG(e.salary), 0) AS average_salary
   FROM   Department d
   LEFT JOIN Employee e ON d.dept_id = e.dept_id
   GROUP  BY d.dept_id, d.dept_name;
   ```

   - An inner join silently omits an empty department. The LEFT JOIN keeps it, and `COALESCE` replaces the resulting NULL average with 0.
   - To show only departments whose average exceeds a value, add `HAVING AVG(e.salary) > 50000`.
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


   Answer: The requirement is to find employees whose own department's region is the same as their manager's department's region. The chain is EMPLOYEES to DEPARTMENTS to LOCATIONS to COUNTRIES to REGIONS, traversed once for the employee and once for the manager.

   ```sql
   SELECT e.employee_id,
          e.first_name,
          e.last_name,
          m.first_name AS manager_first_name,
          m.last_name  AS manager_last_name,
          r_emp.region_name
   FROM   employees e
   JOIN   departments d_emp ON e.department_id = d_emp.department_id
   JOIN   locations  l_emp  ON d_emp.location_id = l_emp.location_id
   JOIN   countries  c_emp  ON l_emp.country_id  = c_emp.country_id
   JOIN   regions    r_emp  ON c_emp.region_id   = r_emp.region_id
   JOIN   employees  m      ON e.manager_id      = m.employee_id
   JOIN   departments d_mgr ON m.department_id   = d_mgr.department_id
   JOIN   locations  l_mgr  ON d_mgr.location_id = l_mgr.location_id
   JOIN   countries  c_mgr  ON l_mgr.country_id  = c_mgr.country_id
   JOIN   regions    r_mgr  ON c_mgr.region_id   = r_mgr.region_id
   WHERE  r_emp.region_id = r_mgr.region_id;
   ```

   Explanation:
   - The EMPLOYEES table is joined to itself, once as `e` for the employee and once as `m` for the manager, using `e.manager_id = m.employee_id`. This self join is the essential step, and the aliases are what make it possible.
   - Each of the two employees is then followed through the same four table chain to reach its region, using distinct aliases for each path so that the two chains do not interfere.
   - The WHERE clause keeps only the rows where the two region identifiers coincide.
   - Comparing `region_id` rather than `region_name` is correct, since the identifier is the key.

   Simpler equivalent using a derived table, which avoids repeating the chain:

   ```sql
   WITH emp_region AS (
       SELECT e.employee_id, e.manager_id, e.first_name, e.last_name, r.region_id
       FROM   employees e
       JOIN   departments d ON e.department_id = d.department_id
       JOIN   locations   l ON d.location_id   = l.location_id
       JOIN   countries   c ON l.country_id    = c.country_id
       JOIN   regions     r ON c.region_id     = r.region_id
   )
   SELECT er.employee_id, er.first_name, er.last_name
   FROM   emp_region er
   JOIN   emp_region mr ON er.manager_id = mr.employee_id
   WHERE  er.region_id = mr.region_id;
   ```

   - The common table expression computes the region of every employee once, and the query then joins that result to itself. This is clearer and easier to check, and most optimisers execute it at least as efficiently.
   - Employees with no manager, that is with a NULL `manager_id`, are excluded by the inner join, which is the correct behaviour here since the question concerns those working under a manager.
5. **Database Query related problem.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*


   Answer: The question gives no data, so the standard method of answering a database query problem is set out, with the patterns an examination requires.

   Method to follow:
   - Read the schema and identify the primary and foreign keys, which determine the join conditions.
   - Decide which tables are needed. Do not join a table that contributes nothing.
   - Decide the filter: WHERE for conditions on individual rows, HAVING for conditions on aggregates.
   - Decide whether grouping is required, which is indicated by phrases such as "for each", "per department" or "total number of".
   - Write the clauses in the order SELECT, FROM, JOIN, WHERE, GROUP BY, HAVING, ORDER BY, remembering that they are evaluated in the order FROM, WHERE, GROUP BY, HAVING, SELECT, ORDER BY.

   Common patterns:

   ```sql
   -- Filtering rows
   SELECT name, salary FROM employee WHERE salary > 50000;

   -- Aggregate per group
   SELECT department, COUNT(*) AS total, AVG(salary) AS avg_salary
   FROM   employee
   GROUP  BY department;

   -- Condition on an aggregate
   SELECT department, AVG(salary) AS avg_salary
   FROM   employee
   GROUP  BY department
   HAVING AVG(salary) > 60000;

   -- Joining two tables
   SELECT e.name, d.dept_name
   FROM   employee e
   JOIN   department d ON e.dept_id = d.dept_id;

   -- Rows in one table with no match in another
   SELECT d.dept_name
   FROM   department d
   LEFT JOIN employee e ON d.dept_id = e.dept_id
   WHERE  e.emp_id IS NULL;

   -- Second highest value
   SELECT MAX(salary) FROM employee
   WHERE salary < (SELECT MAX(salary) FROM employee);

   -- Duplicates
   SELECT name, COUNT(*) FROM employee GROUP BY name HAVING COUNT(*) > 1;
   ```

   Points that earn marks:
   - Use explicit `JOIN ... ON` rather than commas in the FROM clause.
   - Use table aliases and qualify every column when more than one table is involved.
   - Never place an aggregate in a WHERE clause; use HAVING.
   - Every non-aggregated column in SELECT must appear in GROUP BY.
   - Use `COUNT(column)` when NULLs are to be ignored and `COUNT(*)` when they are not. <!-- verify -->
6. **From an Employee table. Write SQL statement according to the following question:**
   **(a) Find out the employees who join the same date:** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1438 (ET: BUET)]*
   **(b) Find those employees whose salary greater than 8,000 and Less than 25,000** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*


   Answer:

   (a) Employees who joined on the same date:

   ```sql
   SELECT e.emp_id, e.emp_name, e.join_date
   FROM   Employee e
   WHERE  e.join_date IN (
              SELECT join_date
              FROM   Employee
              GROUP  BY join_date
              HAVING COUNT(*) > 1
          )
   ORDER  BY e.join_date, e.emp_id;
   ```

   - The subquery finds every date on which more than one employee joined, and the outer query then returns all the employees having those dates.
   - `HAVING COUNT(*) > 1` is the standard way of detecting duplication; `WHERE` cannot be used, because the condition applies to a group rather than to a row.

   Alternative using a self join, which pairs the employees directly:

   ```sql
   SELECT DISTINCT e1.emp_id, e1.emp_name, e1.join_date
   FROM   Employee e1
   JOIN   Employee e2 ON e1.join_date = e2.join_date
                     AND e1.emp_id   <> e2.emp_id;
   ```

   - The condition `e1.emp_id <> e2.emp_id` prevents a row from matching itself, and `DISTINCT` removes the duplicates the join produces.

   To list only the dates with a count:

   ```sql
   SELECT join_date, COUNT(*) AS number_of_employees
   FROM   Employee
   GROUP  BY join_date
   HAVING COUNT(*) > 1;
   ```

   (b) Employees whose salary is greater than 8,000 and less than 25,000:

   ```sql
   SELECT emp_id, emp_name, salary
   FROM   Employee
   WHERE  salary > 8000 AND salary < 25000;
   ```

   - The bounds here are strict, as the wording requires, so an employee earning exactly 8,000 or exactly 25,000 is excluded.
   - If the bounds were meant to be inclusive, `BETWEEN` would be used: `WHERE salary BETWEEN 8000 AND 25000`, which is equivalent to `salary >= 8000 AND salary <= 25000`. The distinction should be stated explicitly, since BETWEEN is inclusive at both ends and is a common source of error.
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

   (i) Students in the CSE department:

   ```sql
   SELECT *
   FROM   Student
   WHERE  Department = 'CSE';
   ```

   Output:

   | StudentID | StudentName | Age | Department |
   |---|---|---|---|
   | 1 | Alice | 20 | CSE |
   | 3 | Charlie | 21 | CSE |

   (ii) All students sorted by age, highest first:

   ```sql
   SELECT *
   FROM   Student
   ORDER  BY Age DESC;
   ```

   Output:

   | StudentID | StudentName | Age | Department |
   |---|---|---|---|
   | 4 | David | 23 | BBA |
   | 2 | Bob | 22 | EEE |
   | 3 | Charlie | 21 | CSE |
   | 1 | Alice | 20 | CSE |

   - `DESC` gives descending order; `ASC`, which is the default, would give ascending.

   (iii) Number of students in each department:

   ```sql
   SELECT Department, COUNT(*) AS TotalStudents
   FROM   Student
   GROUP  BY Department;
   ```

   Output:

   | Department | TotalStudents |
   |---|---|
   | CSE | 2 |
   | EEE | 1 |
   | BBA | 1 |

   - `GROUP BY Department` creates one group per distinct department value, and `COUNT(*)` counts the rows in each group.
   - Adding `ORDER BY TotalStudents DESC` would list the largest department first.
8. **Consider the following relation:**

**Write an SQL query to display the region, average sale amount, and total number of sales for each region where: The average sale amount exceeds BDT 50,000 and the total number of sales in that region is at least 5.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1425 (ET: E-Zone)]*


   Answer:

   ```sql
   SELECT region,
          AVG(sale_amount) AS average_sale,
          COUNT(*)         AS total_sales
   FROM   Sales
   GROUP  BY region
   HAVING AVG(sale_amount) > 50000
      AND COUNT(*) >= 5;
   ```

   Explanation:
   - `GROUP BY region` produces one row per region.
   - `AVG(sale_amount)` and `COUNT(*)` compute the two required aggregates within each group.
   - Both conditions concern aggregates rather than individual rows, so they must be placed in `HAVING` and not in `WHERE`. A WHERE clause is evaluated before grouping and therefore cannot refer to AVG or COUNT.
   - The two conditions are combined with `AND`, so a region qualifies only if it satisfies both.

   Order of evaluation, which is what makes HAVING necessary:
   - FROM, then WHERE, then GROUP BY, then HAVING, then SELECT, then ORDER BY.

   Refinements:
   - To order the output by the strongest region: add `ORDER BY average_sale DESC`.
   - To round the average: `ROUND(AVG(sale_amount), 2) AS average_sale`.
   - If the question also restricted the period, that condition would go in a WHERE clause, since it applies to individual rows: `WHERE sale_date >= '2025-01-01'` placed before GROUP BY.
9. **Given two tables:**

**a) Write an SQL query to retrieve all student names, their courses, and grades.**
**b) Write an SQL query to retrieve names of students who obtained grade 'A'.** *[BUET Assistant Programmer 21.06.2025 compact it 1434 (ET: BUET)]*


   Answer: Two tables are assumed, `Student(student_id, student_name)` and `Enrollment(student_id, course, grade)`, joined on `student_id`.

   (a) All student names with their courses and grades:

   ```sql
   SELECT s.student_name, e.course, e.grade
   FROM   Student s
   JOIN   Enrollment e ON s.student_id = e.student_id;
   ```

   - An inner join returns only students who are enrolled in at least one course. If students with no enrolment must also appear, with NULLs in the course and grade columns, use `LEFT JOIN` instead.

   (b) Names of students who obtained grade 'A':

   ```sql
   SELECT DISTINCT s.student_name
   FROM   Student s
   JOIN   Enrollment e ON s.student_id = e.student_id
   WHERE  e.grade = 'A';
   ```

   - `DISTINCT` is necessary because a student who scored an A in more than one course would otherwise be listed several times.

   Equivalent using a subquery, which some examiners prefer:

   ```sql
   SELECT student_name
   FROM   Student
   WHERE  student_id IN (SELECT student_id FROM Enrollment WHERE grade = 'A');
   ```

   - This form needs no DISTINCT, because `IN` tests membership once per student regardless of how many matching rows exist.
   - If grades are stored with case variation, `WHERE UPPER(e.grade) = 'A'` should be used, though that prevents the use of an index on the column.
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

   (i) Names of all employees who live in the city 'Dhaka':

   ```sql
   SELECT employee_name
   FROM   employee
   WHERE  city = 'Dhaka';
   ```

   - The `employee` relation already holds the city, so no join is required.

   (ii) Names of all employees whose salary is greater than 1,00,000:

   ```sql
   SELECT employee_name
   FROM   works
   WHERE  salary > 100000;
   ```

   - The salary is held in the `works` relation, so that is the table to query.

   If the two conditions were to be combined, a join would be needed:

   ```sql
   SELECT e.employee_name
   FROM   employee e
   JOIN   works w ON e.employee_name = w.employee_name
   WHERE  e.city = 'Dhaka'
     AND  w.salary > 100000;
   ```

   - Note on the schema as printed: the `company` relation is given as `company(employee_name, city)`, which is almost certainly a misprint for `company(company_name, city)`, since a company relation would hold the company's name and the city in which it is located. The queries above do not depend on it.
   - Points worth stating: string literals are enclosed in single quotes; numeric literals are not; and the comparison is strict, so an employee earning exactly 100000 is excluded.
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

   (i) `SELECT Count(*) FROM Students S LEFT JOIN Marks M;`

   - Output: 36
   - Reason: the join has no `ON` condition, so it is not a genuine left join at all; every row of Students is paired with every row of Marks, which is a Cartesian product. Students has 4 rows and Marks has 9, so 4 × 9 = 36.
   - In strict SQL a `JOIN` without `ON` is a syntax error, and MySQL treats it as a cross join. This is exactly the trap the question is setting.

   (ii) The query with `HAVING SUM(Mark) >= 200`:

   - Totals per student: Mr. A gives 70 + 50 + 80 = 200; Mr. B gives 90 + 60 + 70 = 220; Mr. C gives 30 + 70 + 60 = 160; Mr. D has no marks at all and forms no group, since the inner join excludes him.
   - Output:

   | StudentName |
   |---|
   | Mr. A |
   | Mr. B |

   - Mr. A qualifies because the condition is `>= 200` and his total is exactly 200.

   (iii) All student names and the number of subjects they have completed:

   ```sql
   SELECT S.StudentName,
          COUNT(M.Subject) AS SubjectsCompleted
   FROM   Students S
   LEFT JOIN Marks M ON S.StudentId = M.StudentId
   GROUP  BY S.StudentId, S.StudentName;
   ```

   - A `LEFT JOIN` is essential so that Mr. D appears with a count of zero. `COUNT(M.Subject)` rather than `COUNT(*)` is also essential, because `COUNT(*)` would count the single NULL row produced by the left join and wrongly report 1 for Mr. D.
   - Output:

   | StudentName | SubjectsCompleted |
   |---|---|
   | Mr. A | 3 |
   | Mr. B | 3 |
   | Mr. C | 3 |
   | Mr. D | 0 |

   (iv) All students who have not completed any subject:

   ```sql
   SELECT S.StudentName
   FROM   Students S
   LEFT JOIN Marks M ON S.StudentId = M.StudentId
   WHERE  M.StudentId IS NULL;
   ```

   - This is the standard anti-join pattern: perform a left join and keep the rows where the right hand side is NULL, which means no match was found.
   - Equivalent with a subquery: `SELECT StudentName FROM Students WHERE StudentId NOT IN (SELECT StudentId FROM Marks);`
   - Output: Mr. D

   (v) All the subject names:

   ```sql
   SELECT DISTINCT Subject
   FROM   Marks;
   ```

   - `DISTINCT` is required, since each subject appears once per student.
   - Output: Math, Bangali, Physics
12. **Given a Patient table in a hospital database below.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1340 (ET: N/A)]*

| Patient_ID | Disease_Name |
|---|---|
| 1 | Covid-19 |
| 2 | Dialysis |
| 3 | Covid-19 |
| 4 | Dengue |

Write down an SQL query to display the total number of patients under each disease category.


   Answer:

   ```sql
   SELECT Disease_Name,
          COUNT(*) AS Total_Patients
   FROM   Patient
   GROUP  BY Disease_Name;
   ```

   Output for the given data:

   | Disease_Name | Total_Patients |
   |---|---|
   | Covid-19 | 2 |
   | Dialysis | 1 |
   | Dengue | 1 |

   Explanation:
   - `GROUP BY Disease_Name` collects together all the rows sharing the same disease, producing one group per distinct disease.
   - `COUNT(*)` counts the rows within each group, which is the number of patients suffering from that disease.
   - Covid-19 appears for patients 1 and 3, so its count is 2; Dialysis and Dengue appear once each.

   Refinements:
   - To list the commonest disease first: add `ORDER BY Total_Patients DESC`.
   - To show only diseases affecting more than one patient: add `HAVING COUNT(*) > 1`, which would leave only Covid-19.
   - `COUNT(Patient_ID)` would give the same result here, since the identifier is never NULL; the two differ only when the counted column contains NULLs.
13. **SQL OUTPUT Problem: Find Employee salary from a table where salary more than 5000.** *[BCIC Assistant Programmer 14.02.2025 compact it 1328 (ET: BUET)]*


   Answer:

   ```sql
   SELECT emp_id, emp_name, salary
   FROM   Employee
   WHERE  salary > 5000;
   ```

   Explanation:
   - `WHERE salary > 5000` filters the rows before anything is returned, so only employees earning strictly more than 5000 appear. An employee earning exactly 5000 is excluded; `>=` would include them.
   - Numeric literals are written without quotation marks.

   Sample output, for an Employee table containing 4000, 5000, 7500 and 12000:

   | emp_id | emp_name | salary |
   |---|---|---|
   | 3 | Karim | 7500 |
   | 4 | Rahim | 12000 |

   Related variations often asked with this question:

   ```sql
   -- Highest salary
   SELECT MAX(salary) FROM Employee;

   -- Second highest salary
   SELECT MAX(salary) FROM Employee
   WHERE salary < (SELECT MAX(salary) FROM Employee);

   -- Employees earning more than the average
   SELECT emp_name, salary FROM Employee
   WHERE salary > (SELECT AVG(salary) FROM Employee);

   -- Salary in a range, inclusive at both ends
   SELECT emp_name, salary FROM Employee
   WHERE salary BETWEEN 5000 AND 20000;
   ```
14. **Write SQL code to get duplicate names from employee table.** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*


   Answer:

   ```sql
   SELECT name, COUNT(*) AS occurrences
   FROM   Employee
   GROUP  BY name
   HAVING COUNT(*) > 1;
   ```

   Explanation:
   - `GROUP BY name` collects together all the rows sharing the same name.
   - `HAVING COUNT(*) > 1` keeps only those groups containing more than one row, which is precisely the definition of a duplicate.
   - `HAVING` must be used rather than `WHERE`, because the condition concerns an aggregate computed over a group, and `WHERE` is evaluated before grouping takes place.

   To list the full rows rather than just the duplicated names:

   ```sql
   SELECT *
   FROM   Employee
   WHERE  name IN (
              SELECT name FROM Employee GROUP BY name HAVING COUNT(*) > 1
          )
   ORDER  BY name;
   ```

   Detecting duplicates on a combination of columns:

   ```sql
   SELECT name, department, COUNT(*) AS occurrences
   FROM   Employee
   GROUP  BY name, department
   HAVING COUNT(*) > 1;
   ```

   Deleting the duplicates, keeping the row with the lowest identifier:

   ```sql
   DELETE FROM Employee
   WHERE  emp_id NOT IN (
              SELECT MIN(emp_id) FROM Employee GROUP BY name
          );
   ```

   - In MySQL this form must be wrapped in a derived table, because MySQL forbids selecting from the same table that is being deleted from within a subquery.
   - The correct long term remedy is a `UNIQUE` constraint on the column, so that duplicates cannot be inserted in the first place.
15. **Write an SQL query to find duplicate names in the employee table.** *[BBA Assistant Programmer 12.07.2025 compact it 1433 (ET: BUET)]*


   Answer:

   ```sql
   SELECT name, COUNT(*) AS occurrences
   FROM   Employee
   GROUP  BY name
   HAVING COUNT(*) > 1;
   ```

   Explanation:
   - Rows sharing a name are collected into one group by `GROUP BY name`.
   - `HAVING COUNT(*) > 1` retains only the groups that contain more than one row, which are exactly the duplicated names.
   - The condition applies to an aggregate, so it belongs in `HAVING`; `WHERE` is evaluated before grouping and cannot refer to `COUNT`.

   Sample output, for an Employee table in which Karim appears three times and Rahim twice:

   | name | occurrences |
   |---|---|
   | Karim | 3 |
   | Rahim | 2 |

   To return the complete duplicate rows:

   ```sql
   SELECT *
   FROM   Employee
   WHERE  name IN (SELECT name FROM Employee GROUP BY name HAVING COUNT(*) > 1)
   ORDER  BY name;
   ```

   Using a window function, which is the modern approach and returns the rows in a single pass:

   ```sql
   SELECT emp_id, name
   FROM   (SELECT emp_id, name,
                  COUNT(*) OVER (PARTITION BY name) AS cnt
           FROM   Employee) t
   WHERE  cnt > 1;
   ```

   - The permanent fix is a `UNIQUE` constraint on the column where duplication is not permitted.
16. **SUM, Avg, Max these function are subnet of __________ function.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*


   Answer: SUM, AVG and MAX are a subset of the aggregate functions in SQL.

   - An aggregate function operates on a set of rows and returns a single summary value, in contrast to a scalar function, which operates on one row and returns one value per row.
   - The five standard aggregate functions are:
   - `COUNT()`, which returns the number of rows.
   - `SUM()`, which returns the total of a numeric column.
   - `AVG()`, which returns the arithmetic mean.
   - `MIN()`, which returns the smallest value.
   - `MAX()`, which returns the largest value.
   - Aggregate functions are normally used with `GROUP BY`, which applies them to each group separately rather than to the whole table, and their results are filtered with `HAVING` rather than `WHERE`.
   - They ignore NULL values, with the single exception of `COUNT(*)`, which counts every row including those with NULLs. This is why `COUNT(column)` and `COUNT(*)` can give different answers.
   - Example: `SELECT department, COUNT(*), SUM(salary), AVG(salary), MIN(salary), MAX(salary) FROM Employee GROUP BY department;`
17. **SQL Query.....** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 592 (ET: BUET)], [RAKUB Assistant Network System Engineer 03.11.2023 compact it 553 (ET: BIBM)], [BREB Assistant Programmer (AP) 21.02.2025 compact it 1335 (ET: N/A)], [Water Supply and Sewerage Authority (WASA); Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*


   Answer: Skipped, as the question is content free.

   - The entry reads only "SQL Query....." with no schema, no data and no requirement stated, so there is nothing that can be answered. <!-- verify -->
18. **Find sname who supplies pname=“wheel” with minimum price:** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 418 (ET: BUET)]*
    * **Catalog** (sid, pid, price)
    * **Supplier** (sid, sname, address)
    * **Product** (pid, pname, etc)


   Answer:

   ```sql
   SELECT s.sname
   FROM   Supplier s
   JOIN   Catalog c ON s.sid = c.sid
   JOIN   Product p ON c.pid = p.pid
   WHERE  p.pname = 'wheel'
     AND  c.price = (
              SELECT MIN(c2.price)
              FROM   Catalog c2
              JOIN   Product p2 ON c2.pid = p2.pid
              WHERE  p2.pname = 'wheel'
          );
   ```

   Explanation:
   - The three tables are joined so that a supplier's name can be connected to the price at which that supplier offers a particular product: Supplier gives the name, Catalog gives the price, and Product gives the product name.
   - The subquery computes the minimum price at which the product named 'wheel' is offered by any supplier.
   - The outer query then returns the supplier or suppliers whose price equals that minimum. Using `=` with the subquery rather than `MIN` directly in the WHERE clause is essential, because an aggregate function cannot appear in a WHERE clause.
   - If more than one supplier offers the wheel at the same lowest price, all of them are returned, which is normally the desired behaviour.

   Alternative using ORDER BY and LIMIT, which is simpler but returns only one supplier even in the event of a tie:

   ```sql
   SELECT s.sname, c.price
   FROM   Supplier s
   JOIN   Catalog c ON s.sid = c.sid
   JOIN   Product p ON c.pid = p.pid
   WHERE  p.pname = 'wheel'
   ORDER  BY c.price ASC
   LIMIT  1;
   ```

   - `LIMIT 1` is MySQL and PostgreSQL syntax; Oracle uses `FETCH FIRST 1 ROW ONLY` and SQL Server uses `SELECT TOP 1`.
   - The first form should be preferred in an examination, since it handles ties correctly and uses only standard SQL.
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


   Answer: A join combines rows from two tables on a matching condition. Here the condition is `Customers.ID = Orders.Customer_id`.

   Examining the data first: the customer identifiers present are 1, 2, 3, 4 and 5, and the customer identifiers referenced by orders are 10, 3, 6, 5 and 8. Only 3 and 5 appear in both, so only two rows match.

   INNER JOIN — returns only the rows that match in both tables:

   ```sql
   SELECT c.ID, c.First_name, o.Order_id, o.Amount
   FROM   Customers c
   INNER JOIN Orders o ON c.ID = o.Customer_id;
   ```

   | ID | First name | Order id | Amount |
   |---|---|---|---|
   | 3 | Belal | 2 | 500 |
   | 5 | Helal | 4 | 800 |

   - 2 rows. Customers without orders and orders without a matching customer are both discarded.

   LEFT JOIN — returns every row of the left table, with NULLs where there is no match:

   ```sql
   SELECT c.ID, c.First_name, o.Order_id, o.Amount
   FROM   Customers c
   LEFT JOIN Orders o ON c.ID = o.Customer_id;
   ```

   | ID | First name | Order id | Amount |
   |---|---|---|---|
   | 1 | Rahim | NULL | NULL |
   | 2 | Karim | NULL | NULL |
   | 3 | Belal | 2 | 500 |
   | 4 | Rony | NULL | NULL |
   | 5 | Helal | 4 | 800 |

   - 5 rows, that is every customer. This is the join used to answer "which customers have placed no order", by adding `WHERE o.Order_id IS NULL`.

   RIGHT JOIN — returns every row of the right table, with NULLs where there is no match:

   ```sql
   SELECT c.ID, c.First_name, o.Order_id, o.Amount
   FROM   Customers c
   RIGHT JOIN Orders o ON c.ID = o.Customer_id;
   ```

   | ID | First name | Order id | Amount |
   |---|---|---|---|
   | NULL | NULL | 1 | 200 |
   | 3 | Belal | 2 | 500 |
   | NULL | NULL | 3 | 300 |
   | 5 | Helal | 4 | 800 |
   | NULL | NULL | 5 | 150 |

   - 5 rows, that is every order. The three orders referring to customers 10, 6 and 8 have no matching customer, which reveals a referential integrity problem in the data.

   FULL OUTER JOIN — returns every row of both tables, matched where possible:

   ```sql
   SELECT c.ID, c.First_name, o.Order_id, o.Amount
   FROM   Customers c
   FULL OUTER JOIN Orders o ON c.ID = o.Customer_id;
   ```

   | ID | First name | Order id | Amount |
   |---|---|---|---|
   | 1 | Rahim | NULL | NULL |
   | 2 | Karim | NULL | NULL |
   | 3 | Belal | 2 | 500 |
   | 4 | Rony | NULL | NULL |
   | 5 | Helal | 4 | 800 |
   | NULL | NULL | 1 | 200 |
   | NULL | NULL | 3 | 300 |
   | NULL | NULL | 5 | 150 |

   - 8 rows: the 2 matched rows, the 3 unmatched customers and the 3 unmatched orders.
   - MySQL does not support FULL OUTER JOIN directly; it is written as a `UNION` of the LEFT JOIN and the RIGHT JOIN.

   Summary: inner join gives 2 rows, left join 5, right join 5 and full outer join 8. The data also demonstrates why a foreign key constraint matters, since three orders reference customers that do not exist.
20. **Database query:**
   * **(i) Group by**
   * **(ii) Average Salary** *[Combined Bank Assistant Programmer 09.02.2024 compact it 299 (ET: BIBM)]*


   Answer:

   (i) GROUP BY:
   - `GROUP BY` collects the rows sharing the same value in one or more columns into a single group, so that an aggregate function returns one value per group rather than one for the whole table.
   - Rules: every column in the SELECT list must either appear in the GROUP BY clause or be inside an aggregate function; conditions on individual rows go in `WHERE`, which is evaluated before grouping; and conditions on aggregates go in `HAVING`, which is evaluated after.
   - Order of evaluation: FROM, WHERE, GROUP BY, HAVING, SELECT, ORDER BY.

   ```sql
   SELECT department, COUNT(*) AS total_employees
   FROM   Employee
   GROUP  BY department;
   ```

   - This returns one row per department with the number of employees in it. Grouping on more than one column is permitted, for example `GROUP BY department, designation`, which creates a group for each combination.

   (ii) Average salary:

   ```sql
   -- Average salary of the whole organisation
   SELECT AVG(salary) AS average_salary
   FROM   Employee;

   -- Average salary of each department
   SELECT department, AVG(salary) AS average_salary
   FROM   Employee
   GROUP  BY department;

   -- Departments whose average salary exceeds 50000
   SELECT department, AVG(salary) AS average_salary
   FROM   Employee
   GROUP  BY department
   HAVING AVG(salary) > 50000;

   -- Employees earning more than the overall average
   SELECT emp_name, salary
   FROM   Employee
   WHERE  salary > (SELECT AVG(salary) FROM Employee);
   ```

   Points worth stating:
   - `AVG` ignores NULL salaries; it does not treat them as zero. If they should count as zero, `AVG(COALESCE(salary, 0))` must be used, which gives a different answer.
   - `ROUND(AVG(salary), 2)` gives a readable result.
   - An aggregate can never appear in a WHERE clause, which is why the third query uses HAVING and the fourth uses a subquery.
21. **Consider that you are given a database of a 'Pet Society' with the following relations.**
   * **Animals(*ID*: integer, *Name*: string, *PrevOwner*: string, *DateAdmitted*: date, *Type*: string)**
   * **Adopter(*PSIN*: integer, *Name*: string, *Address*: string, *OtherAnimals*: integer)**
   * **Adoption(*AnimalID*: integer, *PSIN*: integer, *AdoptDate*: date, *chipNo*: integer)**
   **Give a sql query that list total number of adoptions on June 30, 2024 for each animal type.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 429 (ET: BIBM)]*


   Answer:

   ```sql
   SELECT a.Type,
          COUNT(*) AS total_adoptions
   FROM   Adoption ad
   JOIN   Animals  a ON ad.AnimalID = a.ID
   WHERE  ad.AdoptDate = DATE '2024-06-30'
   GROUP  BY a.Type;
   ```

   Explanation:
   - The animal type is held in the Animals relation, while the adoption date is in the Adoption relation, so the two must be joined on `Adoption.AnimalID = Animals.ID`.
   - `WHERE ad.AdoptDate = DATE '2024-06-30'` restricts the rows to that single day, before any grouping.
   - `GROUP BY a.Type` then produces one row per animal type, and `COUNT(*)` gives the number of adoptions of that type on that date.
   - The Adopter relation is not needed, since nothing about the adopter is asked for. Joining it would be a mark losing error.

   Points worth noting:
   - If `AdoptDate` is a timestamp rather than a date, an equality test would miss every row with a time component. In that case the condition must be written as a range: `WHERE ad.AdoptDate >= '2024-06-30' AND ad.AdoptDate < '2024-07-01'`.
   - Date literal syntax varies: `DATE '2024-06-30'` is the ANSI standard, MySQL accepts `'2024-06-30'` directly, and Oracle uses `TO_DATE('30-JUN-2024', 'DD-MON-YYYY')`.
   - Animal types with no adoption on that date do not appear at all. To show them with a count of zero, a LEFT JOIN from a distinct list of types would be needed.
22. **How many row will return when we do i) Inner Join ii) Left Outer Join iii) Right Outer join and v) Full Outer join.** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 392 (ET: BUET)]*


   Answer: The number of rows returned by each join depends on how many rows match, so the answer is expressed in terms of the matched and unmatched rows of each table.

   Notation: let the left table have L rows, the right table R rows, M matched pairs produced by the join condition, Lu the left rows with no match and Ru the right rows with no match.

   - Inner join: returns M rows, that is only the matching pairs. Unmatched rows on either side are discarded.
   - Left outer join: returns M + Lu rows, that is every row of the left table, with NULLs in the right hand columns where there was no match.
   - Right outer join: returns M + Ru rows, that is every row of the right table, with NULLs in the left hand columns where there was no match.
   - Full outer join: returns M + Lu + Ru rows, that is every row of both tables, matched where possible.

   Worked example. Customers has 5 rows with identifiers 1 to 5, and Orders has 5 rows referring to customers 10, 3, 6, 5 and 8. Only customers 3 and 5 have orders, so M = 2, Lu = 3 and Ru = 3.

   | Join | Rows returned | Working |
   |---|---|---|
   | Inner join | 2 | M |
   | Left outer join | 5 | M + Lu = 2 + 3 |
   | Right outer join | 5 | M + Ru = 2 + 3 |
   | Full outer join | 8 | M + Lu + Ru = 2 + 3 + 3 |

   Important points:
   - The count is not simply the size of a table when the relationship is one to many. If one customer has three orders, that single customer contributes three rows to the inner join, so M can exceed the number of rows in either table.
   - A join with no ON condition, or a `CROSS JOIN`, returns the Cartesian product L × R, which for these tables would be 25 rows.
   - A left outer join always returns at least L rows and an inner join at most as many as a left outer join, which is a useful check on any answer.
   - MySQL has no FULL OUTER JOIN; it is written as `LEFT JOIN ... UNION ... RIGHT JOIN`.
23. **Write SQL Query For create, insert of a table Emp (id, name, designation, Dept_name, Salary). Write SQL Query that show department wise salary of Employee.** *[BKSP Assistant Programmer 13.07.2024 compact it 1459 (ET: N/A)]*


   Answer:

   Creating the table:

   ```sql
   CREATE TABLE Emp (
       id           INT PRIMARY KEY,
       name         VARCHAR(50) NOT NULL,
       designation  VARCHAR(50),
       Dept_name    VARCHAR(50),
       Salary       DECIMAL(10, 2) CHECK (Salary > 0)
   );
   ```

   - `INT PRIMARY KEY` makes `id` unique and not null, and creates an index automatically.
   - `VARCHAR(50)` is used for variable length text; `NOT NULL` on the name enforces that every employee has one.
   - `DECIMAL(10,2)` is the correct type for money, since floating point types introduce rounding errors in financial calculations.
   - The `CHECK` constraint prevents a negative or zero salary from being stored.

   Inserting rows:

   ```sql
   INSERT INTO Emp (id, name, designation, Dept_name, Salary) VALUES
       (1, 'Rahim',  'Programmer',       'IT',      45000),
       (2, 'Karim',  'Senior Programmer','IT',      65000),
       (3, 'Salma',  'Accountant',       'Finance', 40000),
       (4, 'Nadia',  'Manager',          'Finance', 80000),
       (5, 'Jamal',  'Officer',          'HR',      35000);
   ```

   - Listing the column names explicitly is good practice, because it keeps the statement correct if the table structure changes later.

   Department wise salary:

   ```sql
   SELECT Dept_name,
          COUNT(*)     AS total_employees,
          SUM(Salary)  AS total_salary,
          AVG(Salary)  AS average_salary
   FROM   Emp
   GROUP  BY Dept_name
   ORDER  BY total_salary DESC;
   ```

   Output for the data inserted above:

   | Dept_name | total_employees | total_salary | average_salary |
   |---|---|---|---|
   | Finance | 2 | 120000 | 60000 |
   | IT | 2 | 110000 | 55000 |
   | HR | 1 | 35000 | 35000 |

   - `GROUP BY Dept_name` produces one row per department, and the aggregate functions summarise each group.
   - To show only departments whose total exceeds a value, add `HAVING SUM(Salary) > 100000`; the condition concerns an aggregate, so it cannot be placed in a WHERE clause.
24. **Query's: Employee & department table given-**
   * **(i) Write the employee name who got same salary named Rahim but not same job of Rahim.**
   * **(ii) Write the employee's name who's average salary is more than company's average salary** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 380 (ET: BUET)]*


   Answer:

   (i) Employees who have the same salary as Rahim but not the same job:

   ```sql
   SELECT e.emp_name, e.salary, e.job_id
   FROM   Employee e
   WHERE  e.salary = (SELECT salary FROM Employee WHERE emp_name = 'Rahim')
     AND  e.job_id <> (SELECT job_id FROM Employee WHERE emp_name = 'Rahim')
     AND  e.emp_name <> 'Rahim';
   ```

   - The first subquery supplies Rahim's salary and the second his job, so the outer query keeps employees matching on one and differing on the other.
   - The third condition excludes Rahim himself, who would otherwise fail only the job test and so be excluded anyway; it is included for clarity and for safety if two employees share the name.
   - A cleaner equivalent using a self join, which reads the Employee table once for Rahim:

   ```sql
   SELECT e.emp_name, e.salary, e.job_id
   FROM   Employee e
   JOIN   Employee r ON r.emp_name = 'Rahim'
   WHERE  e.salary = r.salary
     AND  e.job_id <> r.job_id;
   ```

   - Caution worth stating: if two employees are named Rahim, the scalar subquery form fails with a "more than one row returned" error, whereas the join form silently compares against both. The identifier should be used rather than the name where possible.

   (ii) Employees whose salary is more than the company's average salary:

   ```sql
   SELECT emp_name, salary
   FROM   Employee
   WHERE  salary > (SELECT AVG(salary) FROM Employee);
   ```

   - The subquery computes a single value, the average over the whole table, and the outer query compares each row against it.
   - An aggregate cannot be written directly in a WHERE clause, which is why the subquery is necessary.

   If the question means departments whose average salary exceeds the company average, the correct form is:

   ```sql
   SELECT d.dept_name, AVG(e.salary) AS dept_average
   FROM   Employee e
   JOIN   Department d ON e.dept_id = d.dept_id
   GROUP  BY d.dept_id, d.dept_name
   HAVING AVG(e.salary) > (SELECT AVG(salary) FROM Employee);
   ```

   - Here the condition is on a group aggregate, so it belongs in HAVING, while the subquery still computes the single overall average.
25. **EMPLOYEES (Emp_ID, Emp_Name, Manager_ID, Dept_ID);**
   **DEPARTMENTS (Dept ID, Salary, Dept Name, Emp_ID);**
   * **(a) Find out the names of the manager for each employee:**
   * **(b) Sort the employees total salary of each department based on salary in descending order.** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 431 (ET: BUET)]*


   Answer:

   (a) Names of the manager for each employee:

   ```sql
   SELECT e.Emp_Name AS employee_name,
          m.Emp_Name AS manager_name
   FROM   EMPLOYEES e
   LEFT JOIN EMPLOYEES m ON e.Manager_ID = m.Emp_ID;
   ```

   - This is a self join: the EMPLOYEES table is joined to itself, once as `e` for the employee and once as `m` for the manager, using `e.Manager_ID = m.Emp_ID`. The aliases are what make the self join possible.
   - A `LEFT JOIN` is used deliberately so that the topmost employee, whose `Manager_ID` is NULL, still appears with a NULL manager name. An inner join would silently drop that row.
   - To make the output clearer: `COALESCE(m.Emp_Name, 'No Manager') AS manager_name`.

   (b) Total salary of each department, sorted in descending order:

   ```sql
   SELECT d.Dept_Name,
          SUM(d.Salary) AS total_salary
   FROM   DEPARTMENTS d
   GROUP  BY d.Dept_ID, d.Dept_Name
   ORDER  BY total_salary DESC;
   ```

   - `GROUP BY` produces one row per department, `SUM` totals the salaries within it, and `ORDER BY ... DESC` sorts the highest total first.

   Note on the schema as printed:
   - The DEPARTMENTS relation is given as `(Dept_ID, Salary, Dept_Name, Emp_ID)`, which places the salary in the department table. That is a poor design, since salary is an attribute of an employee rather than of a department, and the presence of `Emp_ID` in DEPARTMENTS alongside `Dept_ID` in EMPLOYEES creates a redundant two way reference.
   - If the salary is in fact held in EMPLOYEES, the correct query is:

   ```sql
   SELECT d.Dept_Name,
          SUM(e.Salary) AS total_salary
   FROM   EMPLOYEES e
   JOIN   DEPARTMENTS d ON e.Dept_ID = d.Dept_ID
   GROUP  BY d.Dept_ID, d.Dept_Name
   ORDER  BY total_salary DESC;
   ```

   - Both forms should be shown, with the design flaw pointed out, since that is what an examiner is testing.
26. **Given Four table:**
   * **Employee (empno(PK), empname, monthlysalary, deptno, mqrnd(FK))**
   * **Department(deptno, deptname, deptlocation)**
   * **Course(erscode(pk) erd dese, ers category, ers duration)**
   * **Offering (of begingate, erscode fk, offeringlocation, empno fk)**
   **Write query for:**
   * **(a) Find Departments with Average Monthly Salary Greater than 1000.**
   * **(b) Find Courses with More Than 2 Offerings.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1456 (ET: BUET)]*


   Answer:

   (a) Departments with an average monthly salary greater than 1000:

   ```sql
   SELECT d.deptno,
          d.deptname,
          AVG(e.monthlysalary) AS average_salary
   FROM   Department d
   JOIN   Employee e ON d.deptno = e.deptno
   GROUP  BY d.deptno, d.deptname
   HAVING AVG(e.monthlysalary) > 1000;
   ```

   - The two tables are joined on `deptno`, grouped by department, and the aggregate condition is placed in `HAVING` because it applies to a group rather than to a row.
   - If only the department number is required, the join is unnecessary: `SELECT deptno, AVG(monthlysalary) FROM Employee GROUP BY deptno HAVING AVG(monthlysalary) > 1000;` The department name is what makes the join worthwhile.

   (b) Courses with more than 2 offerings:

   ```sql
   SELECT c.crscode,
          c.crsdesc,
          COUNT(*) AS number_of_offerings
   FROM   Course c
   JOIN   Offering o ON c.crscode = o.crscode
   GROUP  BY c.crscode, c.crsdesc
   HAVING COUNT(*) > 2;
   ```

   - Each row of Offering represents one offering of a course, so counting the rows per `crscode` gives the number of offerings.
   - `HAVING COUNT(*) > 2` keeps only the courses offered three or more times.

   Points worth stating:
   - Both queries follow the same pattern: join to obtain the descriptive column, group by the key together with that column, aggregate, and filter the aggregate with HAVING.
   - Grouping by the key as well as the name is safer, since two departments or courses could share a description.
   - The column names in the question are evidently mistranscribed, `erscode` for `crscode` and `mqrnd` for `mgrno`, so the corrected names are used and the assumption stated.
27. **6.4 Consider the following relation: Employee(EmpID, Name, Department, Salary). Write an SQL query to retrieve the Department, the total number of employees, and the average salary for each department. The output should display one record for each department.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*


   Answer:

   ```sql
   SELECT Department,
          COUNT(*)    AS TotalEmployees,
          AVG(Salary) AS AverageSalary
   FROM   Employee
   GROUP  BY Department;
   ```

   Explanation:
   - `GROUP BY Department` collapses the rows of each department into one group, which produces exactly one record per department as required.
   - `COUNT(*)` gives the number of employees in the group and `AVG(Salary)` the mean salary within it.
   - Every column in the SELECT list is either grouped or aggregated, which is the rule that must be satisfied.

   Sample output:

   | Department | TotalEmployees | AverageSalary |
   |---|---|---|
   | IT | 12 | 58000 |
   | Finance | 8 | 62000 |
   | HR | 5 | 41000 |

   Refinements: `ROUND(AVG(Salary), 2)` for a readable figure, `ORDER BY AverageSalary DESC` to rank the departments, and `HAVING COUNT(*) > 5` to restrict the output to larger departments, the condition being on an aggregate and therefore requiring HAVING rather than WHERE.
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


   Answer: The code contains one definite error and one point of ambiguity, and both must be identified.

   The code as given:

   ```sql
   SELECT department_name, AVG(salary) as average_salary
   FROM employees
   JOIN department d ON e.department_id = d.department_id
   WHERE salary > (SELECT AVG(salary) FROM employees )
   GROUP BY department_name
   HAVING COUNT(*) > 2
   ORDER BY average_salary desc
   ```

   Error 1, an undefined alias:
   - The `FROM` clause is written as `FROM employees` with no alias, yet the join condition refers to `e.department_id`. The alias `e` was never declared, so the statement fails to parse. The table name must be aliased: `FROM employees e`.

   Error 2, an inconsistent table name:
   - The table is called `employees` in the FROM clause but the joined table is `department`, singular, while the schema in such questions normally names it `departments`. The names must match the actual schema.

   Point of correctness, not an error but worth noting:
   - The subquery `(SELECT AVG(salary) FROM employees)` is uncorrelated, so it computes the average salary of the entire organisation once. Every employee is compared against that single figure. This is valid, but it is probably not what was intended; a comparison against the employee's own department average would require a correlated subquery.

   Corrected version:

   ```sql
   SELECT d.department_name,
          AVG(e.salary) AS average_salary
   FROM   employees e
   JOIN   departments d ON e.department_id = d.department_id
   WHERE  e.salary > (SELECT AVG(salary) FROM employees)
   GROUP  BY d.department_name
   HAVING COUNT(*) > 2
   ORDER  BY average_salary DESC;
   ```

   What the corrected query does, in order of evaluation:
   - FROM and JOIN combine each employee with the row of their department.
   - WHERE keeps only the employees whose salary exceeds the company wide average. This filter is applied to individual rows, before any grouping.
   - GROUP BY forms one group per department name, containing only those above average employees.
   - HAVING keeps only the departments that have more than two such employees.
   - SELECT computes the average salary of the surviving employees in each department. Note that this is the average of the above average earners only, not of the whole department.
   - ORDER BY sorts the departments by that average, highest first.

   In one sentence: it lists the departments having more than two employees who earn above the company average, together with the average salary of those employees, ranked from highest to lowest.

   Further improvements worth mentioning: qualify every column with its table alias for readability, add a semicolon to terminate the statement, and group by `d.department_id` as well as the name in case two departments share a name.
29. **Employee Salary sql query a. Sum b. Avg. C. Employee_Name all 2nd letter 'a'......** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 508 (ET: N/A)]*


   Answer:

   (a) Sum of employee salaries:

   ```sql
   -- Total salary of the whole organisation
   SELECT SUM(salary) AS total_salary FROM Employee;

   -- Total salary of each department
   SELECT department, SUM(salary) AS total_salary
   FROM   Employee
   GROUP  BY department;
   ```

   (b) Average of employee salaries:

   ```sql
   -- Average salary of the whole organisation
   SELECT AVG(salary) AS average_salary FROM Employee;

   -- Average salary of each department, rounded
   SELECT department, ROUND(AVG(salary), 2) AS average_salary
   FROM   Employee
   GROUP  BY department;
   ```

   - `AVG` ignores NULL salaries rather than treating them as zero. If they should count as zero, `AVG(COALESCE(salary, 0))` must be used, which gives a different answer.

   (c) Employee names whose second letter is 'a':

   ```sql
   SELECT Employee_Name
   FROM   Employee
   WHERE  Employee_Name LIKE '_a%';
   ```

   - In the `LIKE` pattern, the underscore matches exactly one character and the percent sign matches any sequence of characters including none. So `'_a%'` means: any single first character, then the letter 'a', then anything at all.
   - This matches Rahim, Karim, Jamal and Nadia, but not Salma, whose second letter is 'a'... in fact Salma does match, since its second character is 'a'. It does not match Belal, whose second character is 'e'.

   Related patterns worth stating:
   - Names beginning with 'a': `LIKE 'a%'`
   - Names ending with 'a': `LIKE '%a'`
   - Names containing 'a' anywhere: `LIKE '%a%'`
   - Names whose third letter is 'a': `LIKE '__a%'`, with two underscores.
   - Names of exactly five characters: `LIKE '_____'`, with five underscores.
   - Case sensitivity depends on the collation of the column; `WHERE UPPER(Employee_Name) LIKE '_A%'` forces a case insensitive match but prevents the use of an index.
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


   Answer: This query is well formed, unlike the similar one with the uncorrelated subquery, and its distinguishing feature is the correlated subquery in the WHERE clause.

   ```sql
   SELECT department_name, AVG(salary) AS average_salary
   FROM employees e
   JOIN departments d ON e.department_id = d.department_id
   WHERE salary > (SELECT AVG(salary) FROM employees WHERE department_id = d.department_id)
   GROUP BY department_name
   HAVING COUNT(*) > 2
   ORDER BY average_salary DESC;
   ```

   Order of evaluation and what each clause does:
   - FROM and JOIN: each employee row is joined to the row of their own department, so that the department name becomes available.
   - WHERE with a correlated subquery: this is the key clause. For each employee row being examined, the subquery recomputes the average salary of that employee's own department, because it refers to `d.department_id` from the outer query. Only employees earning more than their own department's average survive. This is quite different from comparing against the company wide average.
   - GROUP BY department_name: the surviving employees are grouped by department.
   - HAVING COUNT(*) > 2: only departments in which more than two employees are above their own department average are retained.
   - SELECT AVG(salary): the average is computed over the surviving employees only, that is over the above average earners of each department, not over the whole department.
   - ORDER BY average_salary DESC: the departments are listed with the highest such average first.

   What the output means, in one sentence:
   - It lists the departments that contain more than two employees earning above that department's own average salary, together with the average salary of those high earners, ranked from highest to lowest.

   Sample output:

   | department_name | average_salary |
   |---|---|
   | Engineering | 95000 |
   | Sales | 72000 |
   | Support | 54000 |

   Points an examiner looks for:
   - The subquery is correlated, since it references `d.department_id` from the outer query, so it is evaluated once for every candidate row rather than once for the whole query. This makes it correct but potentially slow on a large table, and an index on `department_id` matters.
   - The average reported is not the department's average salary. It is the average of the employees who already exceed that average, which is necessarily higher. Misreading this is the commonest error.
   - `HAVING` is used rather than `WHERE` for the count, because the condition concerns a group.
   - A department in which two or fewer employees exceed the average does not appear at all.
   - The same result can be obtained more efficiently with a window function: `AVG(salary) OVER (PARTITION BY department_id)` computes each department's average once, avoiding the repeated subquery.
31. **Consider the employee tables: Create a SQL view that shows the details of Employee information who have the salary equivalent to the maximum, minimum and average salary of employee.** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 473 (ET: N/A)]*


   Answer:

   ```sql
   CREATE VIEW Employee_Salary_Extremes AS
   SELECT e.emp_id,
          e.emp_name,
          e.designation,
          e.dept_id,
          e.salary,
          CASE
              WHEN e.salary = (SELECT MAX(salary) FROM Employee) THEN 'Maximum'
              WHEN e.salary = (SELECT MIN(salary) FROM Employee) THEN 'Minimum'
              ELSE 'Average'
          END AS salary_category
   FROM   Employee e
   WHERE  e.salary IN (
              SELECT MAX(salary) FROM Employee
              UNION
              SELECT MIN(salary) FROM Employee
              UNION
              SELECT AVG(salary) FROM Employee
          );
   ```

   Explanation:
   - The `WHERE ... IN` clause with three subqueries combined by `UNION` builds the set of the three values of interest, and keeps only the employees whose salary equals one of them.
   - The `CASE` expression labels each row so that the reader can see which of the three conditions it satisfies.
   - `UNION` rather than `UNION ALL` is used so that duplicates are removed if, for example, the maximum and the average happen to coincide.

   A simpler and clearer alternative:

   ```sql
   CREATE VIEW Employee_Salary_Extremes AS
   SELECT *
   FROM   Employee
   WHERE  salary = (SELECT MAX(salary) FROM Employee)
      OR  salary = (SELECT MIN(salary) FROM Employee)
      OR  salary = (SELECT AVG(salary) FROM Employee);
   ```

   Using the view:

   ```sql
   SELECT * FROM Employee_Salary_Extremes;
   ```

   Practical caution that should be stated:
   - Matching the average exactly will usually return nothing, because `AVG(salary)` is generally a fractional value that no stored salary equals precisely. A more useful formulation is to find the employee nearest to the average:

   ```sql
   SELECT * FROM Employee
   ORDER BY ABS(salary - (SELECT AVG(salary) FROM Employee))
   LIMIT 1;
   ```

   What a view is and why it is used here:
   - A view is a stored named query. It holds no data of its own; it is executed each time it is referenced, so it always reflects the current contents of the base tables.
   - Benefits: it simplifies a complex query into a single name, provides security by exposing only selected rows and columns, and gives logical data independence, since the underlying tables can change while the view's definition is adjusted to keep the interface stable.
32. **SQL query for employee table. (Approximate)** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 476 (ET: N/A)]*


   Answer: The question gives no table and no requirement, so the standard employee table queries are set out, since that is what such a question expects.

   ```sql
   -- Table assumed: Employee(emp_id, emp_name, designation, dept_id, salary, join_date)

   -- All employees
   SELECT * FROM Employee;

   -- Employees earning more than 50000
   SELECT emp_name, salary FROM Employee WHERE salary > 50000;

   -- Highest and lowest salary
   SELECT MAX(salary) AS highest, MIN(salary) AS lowest FROM Employee;

   -- Second highest salary
   SELECT MAX(salary) FROM Employee
   WHERE salary < (SELECT MAX(salary) FROM Employee);

   -- Employees earning above the company average
   SELECT emp_name, salary FROM Employee
   WHERE salary > (SELECT AVG(salary) FROM Employee);

   -- Number of employees and average salary per department
   SELECT dept_id, COUNT(*) AS total, AVG(salary) AS average
   FROM   Employee
   GROUP  BY dept_id;

   -- Departments whose average salary exceeds 60000
   SELECT dept_id, AVG(salary) AS average
   FROM   Employee
   GROUP  BY dept_id
   HAVING AVG(salary) > 60000;

   -- Duplicate names
   SELECT emp_name, COUNT(*) FROM Employee
   GROUP BY emp_name HAVING COUNT(*) > 1;

   -- Employees whose name begins with 'A'
   SELECT emp_name FROM Employee WHERE emp_name LIKE 'A%';

   -- Employees who joined in 2024
   SELECT emp_name, join_date FROM Employee
   WHERE join_date BETWEEN '2024-01-01' AND '2024-12-31';

   -- Top 5 earners
   SELECT emp_name, salary FROM Employee
   ORDER BY salary DESC LIMIT 5;

   -- Employees with no department assigned
   SELECT emp_name FROM Employee WHERE dept_id IS NULL;
   ```

   Points that earn marks in any such question:
   - Use `IS NULL` and not `= NULL`, since NULL is never equal to anything, including itself.
   - Place row conditions in WHERE and aggregate conditions in HAVING.
   - Every non-aggregated column in the SELECT list must appear in the GROUP BY clause.
   - Use explicit `JOIN ... ON` rather than commas in the FROM clause, and qualify columns with table aliases. <!-- verify -->
33. **Suppose we have a relational database with five tables. table key Attributes S(sid, A) Sid T(tid, B) Tid U(uid, C) Uid R(sid, tid, D) sid, tid Q(tid, uid, E) tid, uid Here R implements a many-to-many relationship between the entities implemented with tables S and T, and Q implements a many-to-many relationship between the entities implemented with tables T and U.**
   **(A) Write an SQL query that returns all records of the form sid, uid where sid is the key of an S- record and uid is the key of a U-record and these two records are related through the relations R and Q. Use SELECT and not SELECT DISTINCT in your query.**
   **(B) Write an SQL query that returns records of the form A, C where the A-value is from an S- record and the C-value is from a U-record and these two records are related through the relations R and Q. Use SELECT and not SELECT DISTINCT in your query.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 496 (ET: N/A)]*


   Answer:

   (A) All pairs sid, uid related through R and Q:

   ```sql
   SELECT R.sid, Q.uid
   FROM   R
   JOIN   Q ON R.tid = Q.tid;
   ```

   Explanation:
   - R links S to T through the pair (sid, tid), and Q links T to U through the pair (tid, uid). The common attribute is `tid`, so joining R and Q on `tid` connects an S record to a U record through the intermediate T record.
   - Tables S, T and U themselves need not appear at all, because the identifiers required are already present in R and Q. Joining them would be unnecessary work.
   - `SELECT` rather than `SELECT DISTINCT` is used as the question requires, so a pair appears once for each distinct `tid` that connects it. That is the intended behaviour here.

   (B) All pairs A, C related through R and Q:

   ```sql
   SELECT S.A, U.C
   FROM   S
   JOIN   R ON S.sid = R.sid
   JOIN   Q ON R.tid = Q.tid
   JOIN   U ON Q.uid = U.uid;
   ```

   Explanation:
   - This time the non-key attributes A and C are required, which are stored in S and U respectively, so those two tables must be joined in as well.
   - The chain of joins follows the relationship path: S to R on `sid`, R to Q on `tid`, and Q to U on `uid`. Table T is still not needed, since nothing about T is being selected and R and Q both already carry `tid`.
   - Again `SELECT` rather than `SELECT DISTINCT` is used as instructed, so a pair of values appears once per connecting path.

   Point worth stating:
   - The tables that must appear in a query are exactly those supplying a selected column or a join condition. Including T here would produce the same rows but would show a failure to reason about which tables are actually required, which is what the question is testing.
34. **Write following EMPLOYEE database table write an SQL query to find employee who work is a department where the average salary is lower then the average salary all the department......** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 452 (ET: BUET)]*


   Answer:

   ```sql
   SELECT e.emp_id, e.emp_name, e.dept_id, e.salary
   FROM   Employee e
   WHERE  e.dept_id IN (
              SELECT dept_id
              FROM   Employee
              GROUP  BY dept_id
              HAVING AVG(salary) < (
                         SELECT AVG(dept_avg)
                         FROM   (SELECT AVG(salary) AS dept_avg
                                 FROM   Employee
                                 GROUP  BY dept_id) AS d
                     )
          );
   ```

   Explanation, working from the inside outward:
   - The innermost derived table computes the average salary of each department, giving one figure per department.
   - `SELECT AVG(dept_avg) FROM (...)` then averages those departmental averages, which is the average across all the departments.
   - The middle subquery lists the departments whose own average is below that figure, using HAVING because the condition is on an aggregate.
   - The outer query returns every employee working in one of those departments.

   An important distinction that carries marks:
   - The average of all the departmental averages is not the same as the average salary of all employees. The first gives each department equal weight; the second gives each employee equal weight. A department of two people counts as much as a department of two hundred in the first calculation but not in the second.
   - If the intended comparison is against the overall employee average, the query is simpler:

   ```sql
   SELECT e.emp_id, e.emp_name, e.dept_id, e.salary
   FROM   Employee e
   WHERE  e.dept_id IN (
              SELECT dept_id FROM Employee
              GROUP  BY dept_id
              HAVING AVG(salary) < (SELECT AVG(salary) FROM Employee)
          );
   ```

   - Both readings should be shown with the difference explained, since the wording "the average salary of all the departments" is genuinely ambiguous.

   Clearer formulation using a common table expression:

   ```sql
   WITH dept_avg AS (
       SELECT dept_id, AVG(salary) AS avg_sal
       FROM   Employee
       GROUP  BY dept_id
   )
   SELECT e.*
   FROM   Employee e
   JOIN   dept_avg da ON e.dept_id = da.dept_id
   WHERE  da.avg_sal < (SELECT AVG(avg_sal) FROM dept_avg);
   ```
35. **Consider the two schema employees (id, first_name, last_name, designation, oining_date, salary, dept_id) and department (dept_id, dept_name). Where detp_id is forgeign key. Find the first_name and department name whose salary is maximum.** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 459 (ET: BUET)]*


   Answer:

   ```sql
   SELECT e.first_name, d.dept_name
   FROM   employees e
   JOIN   department d ON e.dept_id = d.dept_id
   WHERE  e.salary = (SELECT MAX(salary) FROM employees);
   ```

   Explanation:
   - The subquery finds the single highest salary in the whole table.
   - The outer query returns the employee or employees earning exactly that amount, joined to the department table to obtain the department name.
   - Using `=` with the subquery is essential, because an aggregate function such as `MAX` cannot appear directly in a WHERE clause.
   - If two employees share the highest salary, both are returned, which is normally the desired behaviour.

   Alternative using ORDER BY and LIMIT:

   ```sql
   SELECT e.first_name, d.dept_name, e.salary
   FROM   employees e
   JOIN   department d ON e.dept_id = d.dept_id
   ORDER  BY e.salary DESC
   LIMIT  1;
   ```

   - Simpler, but it returns only one row even when several employees are tied at the top, so the subquery form is safer.
   - `LIMIT` is MySQL and PostgreSQL syntax; Oracle uses `FETCH FIRST 1 ROW ONLY` and SQL Server uses `SELECT TOP 1`.

   Related variation, the highest paid employee within each department:

   ```sql
   SELECT e.first_name, d.dept_name, e.salary
   FROM   employees e
   JOIN   department d ON e.dept_id = d.dept_id
   WHERE  e.salary = (SELECT MAX(salary) FROM employees
                      WHERE dept_id = e.dept_id);
   ```

   - This uses a correlated subquery, evaluated once per row against that row's own department.
36. **Suppose that we have a relational database with the following table. Underlined one represent primary key**
   **Movies (\underline{\text{mid}}, title, year)**
   **People (\underline{\text{pid}}, name)**
   **Genres (\underline{\text{gid}}, genre)**
   **HasRole (\underline{\text{pid}, \text{mid}}, role)**
   **Has Genre (\underline{\text{gid}, \text{mid}})**
   **Write a SQL query to return the number of movies that are romantic comedies.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 436 (ET: BIBM)]*


   Answer: A romantic comedy is a film belonging to both the genre 'Romance' and the genre 'Comedy', so the film must appear twice in HasGenre with two different genre identifiers.

   ```sql
   SELECT COUNT(*) AS romantic_comedies
   FROM   Movies m
   WHERE  m.mid IN (SELECT hg.mid FROM HasGenre hg
                    JOIN Genres g ON hg.gid = g.gid
                    WHERE g.genre = 'Romance')
     AND  m.mid IN (SELECT hg.mid FROM HasGenre hg
                    JOIN Genres g ON hg.gid = g.gid
                    WHERE g.genre = 'Comedy');
   ```

   Explanation:
   - The first subquery lists every film with the Romance genre and the second every film with the Comedy genre. A film qualifies only if it appears in both lists, which the `AND` enforces.
   - The People and HasRole tables are irrelevant here and must not be joined in.

   Equivalent using grouping, which generalises to any number of required genres:

   ```sql
   SELECT COUNT(*) AS romantic_comedies
   FROM   (SELECT hg.mid
           FROM   HasGenre hg
           JOIN   Genres g ON hg.gid = g.gid
           WHERE  g.genre IN ('Romance', 'Comedy')
           GROUP  BY hg.mid
           HAVING COUNT(DISTINCT g.genre) = 2) AS t;
   ```

   - `HAVING COUNT(DISTINCT g.genre) = 2` requires that both genres are present, not merely two rows, which matters if a film could be recorded twice under the same genre.

   A common error to avoid:
   - Writing `WHERE g.genre = 'Romance' AND g.genre = 'Comedy'` in a single join. That condition is applied to one row at a time, and no single row can have both values, so the query would always return zero. The requirement is a condition across rows, which is why either two subqueries or a grouped count is needed.
   - `COUNT(*)` here counts films, not genre rows, because the outer query operates on the distinct film identifiers.
37. **(গ) ডাটাবেস সিস্টেমে view কী? এটি কী কী কাজে লাগে?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 627 (ET: N/A)]*


   Answer:

   What a view is:
   - A view is a virtual table defined by a stored SELECT statement. It contains no data of its own; the query is executed whenever the view is referenced, so the result always reflects the current contents of the underlying base tables.
   - It is created with `CREATE VIEW view_name AS SELECT ...` and is then queried exactly like a table.
   - A materialised view is different: it does store the result physically and must be refreshed, which trades storage and staleness for speed. It is used in data warehousing.

   ```sql
   CREATE VIEW HighPaidEmployees AS
   SELECT e.emp_id, e.emp_name, d.dept_name, e.salary
   FROM   Employee e
   JOIN   Department d ON e.dept_id = d.dept_id
   WHERE  e.salary > 50000;

   SELECT * FROM HighPaidEmployees WHERE dept_name = 'IT';
   ```

   What a view is used for:
   - Simplifying complex queries: a join across five tables is defined once and thereafter referenced by a single name, so application code and reports become far shorter and less error prone.
   - Security and access control: a user can be granted access to the view while being denied access to the base table, so that sensitive columns such as salary or national identity number, or rows belonging to other departments, are never exposed. This is the commonest reason for creating a view in a bank.
   - Logical data independence: if the underlying table structure changes, the view definition can be adjusted so that the applications reading the view continue to work unchanged.
   - Presenting data in a different form: renaming columns, computing derived values, aggregating, and combining several tables into one apparent table tailored to a particular user group.
   - Consistency: a business rule such as the definition of an "active customer" is written once in the view rather than being repeated, and possibly repeated inconsistently, in many queries.
   - Reducing duplication: several reports can share one view instead of each carrying its own copy of the logic.

   Limitations that should be stated:
   - A view carries a performance cost, since its query is executed on every reference, and a view built on views can become very slow.
   - Updating through a view is restricted. It is generally permitted only for a simple view over a single table with no aggregation, no DISTINCT, no GROUP BY and no join.
   - Indexes cannot be created on an ordinary view, only on a materialised or indexed view.
38. **অথবা, নিম্নোক্ত টেবিলগুলো হতে (ক), (খ) এবং (গ) এর উত্তর দিন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 627 (ET: N/A)]*
   Restaurant (rid, rname, rcity, phone, seat-capacity)
   Dishes (did, dname, dtype)
   Customer (cid, cname, ccity)
   Serves (rid, did)

   **(ক) যে যে রেস্টুরেন্টগুলো ‘Burger’ পরিবেশন করে সেগুলোর নাম খুঁজে বের করার জন্য SQL Query লিখুন। (খ) ‘Ziman’ নামক একজন Customer যে যে খাবারগুলো অ্যালার্জি সংক্রান্ত সমস্যা এড়িয়ে খেতে পারেন তার তালিকা তৈরি করুন। (গ) যে যে খাবারগুলো ঢাকার সকল রেস্টুরেন্টে পাওয়া যায় তার তালিকা তৈরি করুন।**


   Answer:

   (a) Restaurants that serve 'Burger':

   ```sql
   SELECT DISTINCT r.rname
   FROM   Restaurant r
   JOIN   Serves s ON r.rid = s.rid
   JOIN   Dishes d ON s.did = d.did
   WHERE  d.dname = 'Burger';
   ```

   - The Serves relation links restaurants to dishes, so the chain runs Restaurant to Serves to Dishes. `DISTINCT` guards against a restaurant appearing more than once if the dish were recorded twice.

   (b) Dishes a customer named 'Ziman' can eat while avoiding an allergy:

   - The schema as given contains no allergy information at all, so the question cannot be answered from it. An additional relation is required, for example `Allergy(cid, dtype)` recording the dish types to which each customer is allergic. Stating this gap is part of the answer.
   - With that relation added, the query is:

   ```sql
   SELECT d.dname
   FROM   Dishes d
   WHERE  d.dtype NOT IN (
              SELECT a.dtype
              FROM   Allergy a
              JOIN   Customer c ON a.cid = c.cid
              WHERE  c.cname = 'Ziman'
          );
   ```

   - This is the standard set difference pattern: all the dishes, minus those whose type appears in Ziman's allergy list.
   - `NOT IN` fails silently if the subquery can return NULL, so `NOT EXISTS` is the safer form in production code. <!-- verify -->

   (c) Dishes available in every restaurant in Dhaka:

   ```sql
   SELECT d.dname
   FROM   Dishes d
   WHERE  NOT EXISTS (
              SELECT 1
              FROM   Restaurant r
              WHERE  r.rcity = 'Dhaka'
                AND  NOT EXISTS (
                         SELECT 1
                         FROM   Serves s
                         WHERE  s.rid = r.rid
                           AND  s.did = d.did
                     )
          );
   ```

   - This is relational division, expressed as a double negation: return a dish for which there is no Dhaka restaurant that does not serve it. There is no direct SQL operator for "for all", so the pattern `NOT EXISTS ( ... NOT EXISTS ( ... ) )` is the standard construction and is exactly what such a question is testing.

   Equivalent using counting, which many find clearer:

   ```sql
   SELECT d.dname
   FROM   Dishes d
   JOIN   Serves s ON d.did = s.did
   JOIN   Restaurant r ON s.rid = r.rid
   WHERE  r.rcity = 'Dhaka'
   GROUP  BY d.did, d.dname
   HAVING COUNT(DISTINCT r.rid) = (SELECT COUNT(*) FROM Restaurant WHERE rcity = 'Dhaka');
   ```

   - A dish qualifies if the number of distinct Dhaka restaurants serving it equals the total number of Dhaka restaurants.
39. **SQL query from a given table.** *[BICIC Assistant Programmer 2022 compact it 634 (ET: BUET)]*


   Answer: The question gives no table, so the standard patterns are set out.

   ```sql
   -- Table assumed: Employee(emp_id, emp_name, dept_id, designation, salary, join_date)

   -- Simple selection with a condition
   SELECT emp_name, salary FROM Employee WHERE salary > 40000;

   -- Sorting
   SELECT emp_name, salary FROM Employee ORDER BY salary DESC;

   -- Aggregate per group
   SELECT dept_id, COUNT(*) AS total, AVG(salary) AS average
   FROM   Employee GROUP BY dept_id;

   -- Condition on an aggregate
   SELECT dept_id, AVG(salary) FROM Employee
   GROUP BY dept_id HAVING AVG(salary) > 50000;

   -- Join
   SELECT e.emp_name, d.dept_name
   FROM   Employee e JOIN Department d ON e.dept_id = d.dept_id;

   -- Rows with no match, the anti-join
   SELECT d.dept_name FROM Department d
   LEFT JOIN Employee e ON d.dept_id = e.dept_id
   WHERE e.emp_id IS NULL;

   -- Subquery
   SELECT emp_name FROM Employee
   WHERE salary > (SELECT AVG(salary) FROM Employee);

   -- Pattern matching
   SELECT emp_name FROM Employee WHERE emp_name LIKE 'A%';

   -- Second highest value
   SELECT MAX(salary) FROM Employee
   WHERE salary < (SELECT MAX(salary) FROM Employee);
   ```

   Method to follow for any such question:
   - Identify the tables and the keys, which determine the join conditions.
   - Decide whether grouping is needed; phrases such as "for each" or "per department" indicate that it is.
   - Put row conditions in WHERE and aggregate conditions in HAVING.
   - Write the clauses in the order SELECT, FROM, JOIN, WHERE, GROUP BY, HAVING, ORDER BY, remembering that they are evaluated FROM, WHERE, GROUP BY, HAVING, SELECT, ORDER BY. <!-- verify -->
40. **Employee table হতে Employee_id, Employee কে খোঁজে বের করার SQL Command লিখ যাদের গড় salary 2000 উপরে।** *[BTCL Junior Assistant Manager 2022 compact it 641 (ET: BUET)]*


   Answer: The wording "average salary above 2000" is ambiguous, and both readings should be given.

   Reading 1, employees whose own salary is above 2000, which is what such questions usually mean:

   ```sql
   SELECT Employee_id, Employee_name, Salary
   FROM   Employee
   WHERE  Salary > 2000;
   ```

   Reading 2, employees whose salary is above the average salary of the whole table:

   ```sql
   SELECT Employee_id, Employee_name, Salary
   FROM   Employee
   WHERE  Salary > (SELECT AVG(Salary) FROM Employee);
   ```

   - An aggregate function cannot appear directly in a WHERE clause, which is why the average must be computed in a subquery.

   Reading 3, departments whose average salary exceeds 2000:

   ```sql
   SELECT Dept_id, AVG(Salary) AS average_salary
   FROM   Employee
   GROUP  BY Dept_id
   HAVING AVG(Salary) > 2000;
   ```

   - Here the condition applies to a group, so it belongs in HAVING rather than WHERE.

   - The rule that decides which form is correct: WHERE filters individual rows before grouping; HAVING filters groups after aggregation. If the question concerns individual employees, use reading 1 or 2; if it concerns departments, use reading 3.
41. **Employee Table টেবিল হতে যে সকল কর্মচারীদের বেতন 30000 টাকার বেশি তাদের নাম পদবী আলাদা করার SQLCommand লিখুন।** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 699 (ET: DPI)]*


   Answer:

   ```sql
   SELECT emp_name, designation
   FROM   Employee
   WHERE  salary > 30000;
   ```

   Explanation:
   - `WHERE salary > 30000` filters the rows so that only employees earning strictly more than 30,000 are returned. An employee earning exactly 30,000 is excluded; `>=` would include them.
   - Only the two required columns are listed rather than using `SELECT *`, which is what the question asks for.
   - Numeric literals are written without quotation marks.

   Refinements:
   - To sort the result: add `ORDER BY salary DESC`.
   - To combine conditions: `WHERE salary > 30000 AND designation = 'Officer'`.
   - To include the salary in the output for verification: `SELECT emp_name, designation, salary`.
42. **There are two tables like Employees (Employee_ID, First_name, Last_name, Email, Phone_number, Hire_date, Job_Id) and Departments (Department_Id, Department_name, Manager_Id, Location_Id). Now, write a query to find the name (first_name, last_name), Department Id and name of all the employees.** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 718 (ET: N/A)]*


   Answer:

   ```sql
   SELECT e.first_name,
          e.last_name,
          d.department_id,
          d.department_name
   FROM   Employees e
   JOIN   Departments d ON e.department_id = d.department_id;
   ```

   Note on the schema as printed:
   - The Employees relation is listed as `(Employee_ID, First_name, Last_name, Email, Phone_number, Hire_date, Job_Id)` with no `Department_Id` column, so as written the two tables cannot be joined at all. In the standard HR schema on which this question is based, Employees does contain `department_id`, and that is assumed above. Pointing out the omission is part of a complete answer.

   If the join must instead go through the manager:

   ```sql
   SELECT e.first_name, e.last_name, d.department_id, d.department_name
   FROM   Employees e
   JOIN   Departments d ON e.employee_id = d.manager_id;
   ```

   - This would return only the managers, not all the employees, so it is not what the question asks for.

   To include employees not assigned to any department:

   ```sql
   SELECT e.first_name, e.last_name, d.department_id, d.department_name
   FROM   Employees e
   LEFT JOIN Departments d ON e.department_id = d.department_id;
   ```

   - The `LEFT JOIN` keeps every employee, showing NULL for the department where none is assigned. An inner join would silently drop those employees, which is a common and easily missed error.
43. **For employee table: (a) Write a SQL query to find those employees who earn more than the average salary. Return employee ID, first name, last name. (b) Write a SQL query to find those employees who earn the highest salary in a department. Return department ID, employee name, and salary.** *[CAAB Programmer 2022 compact it 722 (ET: N/A)]*


   Answer:

   (a) Employees who earn more than the average salary:

   ```sql
   SELECT employee_id, first_name, last_name
   FROM   Employees
   WHERE  salary > (SELECT AVG(salary) FROM Employees);
   ```

   - The subquery returns a single value, the average over the whole table, and each row is compared against it.
   - An aggregate function cannot appear directly in a WHERE clause, which is why the subquery is required.
   - The subquery is uncorrelated, so it is evaluated once rather than once per row, and the query is efficient.

   (b) Employees who earn the highest salary in their department:

   ```sql
   SELECT e.department_id, e.first_name, e.last_name, e.salary
   FROM   Employees e
   WHERE  e.salary = (SELECT MAX(salary)
                      FROM   Employees
                      WHERE  department_id = e.department_id);
   ```

   - This subquery is correlated: it refers to `e.department_id` from the outer query, so it is recomputed for each candidate row against that row's own department.
   - If two employees tie for the highest salary in a department, both are returned, which is normally the desired behaviour.

   Equivalent using a grouped subquery, which avoids evaluating the subquery repeatedly:

   ```sql
   SELECT e.department_id, e.first_name, e.last_name, e.salary
   FROM   Employees e
   JOIN   (SELECT department_id, MAX(salary) AS max_sal
           FROM   Employees
           GROUP  BY department_id) m
     ON   e.department_id = m.department_id
    AND   e.salary        = m.max_sal;
   ```

   Modern form using a window function:

   ```sql
   SELECT department_id, first_name, last_name, salary
   FROM   (SELECT department_id, first_name, last_name, salary,
                  RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS rnk
           FROM   Employees) t
   WHERE  rnk = 1;
   ```

   - `RANK` rather than `ROW_NUMBER` is used so that ties are all kept.
44. **Write down the SQL command into the following two: (a) Find out the all information of employees from emp_info table. Where employee's salary is more than 20,000 and city is Dhaka. (b) Update employee name ‘Mr.X’ in emp_info, whose epm_id is 2.** *[NWPGCL Junior Assistant Manager (IT) 2022 compact it 730 (ET: N/A)]*


   Answer:

   (a) All information about employees earning more than 20,000 and living in Dhaka:

   ```sql
   SELECT *
   FROM   emp_info
   WHERE  salary > 20000
     AND  city = 'Dhaka';
   ```

   - Both conditions must hold, so they are combined with `AND`. String literals are enclosed in single quotes and numeric literals are not.
   - `SELECT *` is acceptable here because the question asks for all information; in general, listing the required columns is better practice.

   (b) Updating the employee name to 'Mr.X' where emp_id is 2:

   ```sql
   UPDATE emp_info
   SET    emp_name = 'Mr.X'
   WHERE  emp_id = 2;
   ```

   Points that earn marks:
   - The `WHERE` clause is essential. An `UPDATE` without it changes every row in the table, which is one of the commonest and most damaging mistakes in practice.
   - Before running an update, the same condition should be tested with a SELECT to confirm which rows will be affected: `SELECT * FROM emp_info WHERE emp_id = 2;`
   - In an interactive session the change should be made inside a transaction, so that it can be reversed: `BEGIN TRANSACTION; UPDATE ...; COMMIT;` or `ROLLBACK;` if the result is wrong.
   - Several columns may be set at once, separated by commas: `SET emp_name = 'Mr.X', city = 'Dhaka'`.
45. **Write down the equivalent SQL from following relational algebra. [full question not collected]** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 760 (ET: N/A)]*


   Answer: The relational algebra expression itself is not reproduced in the question, so the translation rules are given, which is what such a question tests.

   Correspondence between relational algebra and SQL:

   | Relational algebra | SQL |
   |---|---|
   | σ_condition(R), selection | `SELECT * FROM R WHERE condition;` |
   | π_columns(R), projection | `SELECT DISTINCT columns FROM R;` |
   | R × S, Cartesian product | `SELECT * FROM R, S;` or `CROSS JOIN` |
   | R ⋈_condition S, theta join | `SELECT * FROM R JOIN S ON condition;` |
   | R ⋈ S, natural join | `SELECT * FROM R NATURAL JOIN S;` |
   | R ∪ S, union | `SELECT * FROM R UNION SELECT * FROM S;` |
   | R ∩ S, intersection | `SELECT * FROM R INTERSECT SELECT * FROM S;` |
   | R − S, difference | `SELECT * FROM R EXCEPT SELECT * FROM S;` |
   | ρ_alias(R), rename | `SELECT * FROM R AS alias;` |
   | R ÷ S, division | `NOT EXISTS ( ... NOT EXISTS ( ... ) )` |
   | γ grouping and aggregation | `SELECT ... GROUP BY ... HAVING ...` |

   Worked examples:
   - π_name(σ_salary>50000(Employee)) becomes `SELECT DISTINCT name FROM Employee WHERE salary > 50000;`
   - π_name, dept_name(Employee ⋈ Department) becomes `SELECT DISTINCT e.name, d.dept_name FROM Employee e NATURAL JOIN Department d;`
   - π_sid(R) − π_sid(σ_grade='F'(R)) becomes `SELECT sid FROM R EXCEPT SELECT sid FROM R WHERE grade = 'F';`

   Two points worth stating:
   - Projection in relational algebra removes duplicates automatically, because a relation is a set. SQL works on multisets, so `DISTINCT` must be written explicitly to reproduce the algebra exactly.
   - Relational algebra is procedural, describing how the result is obtained step by step, whereas SQL is declarative, describing what is required and leaving the method to the optimiser. <!-- verify -->
46. **Write a SQL query to find same salary but job not same?** *[BIWTA; Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*


   Answer:

   ```sql
   SELECT e1.emp_id, e1.emp_name, e1.salary, e1.job_id
   FROM   Employee e1
   JOIN   Employee e2 ON e1.salary = e2.salary
                     AND e1.job_id <> e2.job_id;
   ```

   Explanation:
   - This is a self join: the Employee table is joined to itself under two aliases, so that every employee can be compared with every other employee.
   - `e1.salary = e2.salary` requires the salaries to be equal, and `e1.job_id <> e2.job_id` requires the jobs to differ. Together they select employees who earn the same as somebody else but do a different job.
   - The second condition also prevents a row from matching itself, since an employee necessarily has the same job as themselves.
   - `DISTINCT` may be added if an employee could match several others and should appear only once.

   To display the matching pairs rather than the individual employees:

   ```sql
   SELECT e1.emp_name AS employee_1, e1.job_id AS job_1,
          e2.emp_name AS employee_2, e2.job_id AS job_2,
          e1.salary
   FROM   Employee e1
   JOIN   Employee e2 ON e1.salary = e2.salary
                     AND e1.job_id <> e2.job_id
                     AND e1.emp_id < e2.emp_id;
   ```

   - The extra condition `e1.emp_id < e2.emp_id` lists each pair once instead of twice, since without it the pair (A, B) and the pair (B, A) would both appear.

   If the comparison is against one named employee rather than against everybody:

   ```sql
   SELECT e.emp_name, e.salary, e.job_id
   FROM   Employee e
   JOIN   Employee r ON r.emp_name = 'Rahim'
   WHERE  e.salary  = r.salary
     AND  e.job_id <> r.job_id;
   ```
47. **This returns the names of the staff where timestampdiff is greater than 25 so it returns total 3 rows.** *[Water Supply and Sewerage Authority (WASA); Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*


   Answer: The statement describes the behaviour of a query using `TIMESTAMPDIFF`, which is MySQL's function for computing the difference between two dates or timestamps in a chosen unit.

   Syntax: `TIMESTAMPDIFF(unit, start, end)`, where the unit may be SECOND, MINUTE, HOUR, DAY, WEEK, MONTH, QUARTER or YEAR. It returns `end − start` in that unit, as an integer with the remainder discarded.

   The query being described:

   ```sql
   SELECT staff_name
   FROM   Staff
   WHERE  TIMESTAMPDIFF(YEAR, join_date, CURDATE()) > 25;
   ```

   - For each row, the function computes the number of complete years between the joining date and today, and the condition keeps only those exceeding 25. If three staff members have served more than 25 years, three rows are returned, which is what the statement asserts.
   - `CURDATE()` returns today's date in MySQL; `CURRENT_DATE` is the ANSI standard form.

   Related forms:

   ```sql
   -- Age of each staff member in years
   SELECT staff_name, TIMESTAMPDIFF(YEAR, dob, CURDATE()) AS age FROM Staff;

   -- Service in complete months
   SELECT staff_name, TIMESTAMPDIFF(MONTH, join_date, CURDATE()) AS months FROM Staff;

   -- Staff who joined in the last 90 days
   SELECT staff_name FROM Staff
   WHERE TIMESTAMPDIFF(DAY, join_date, CURDATE()) <= 90;
   ```

   Points worth stating:
   - The function is MySQL specific. The equivalents are `DATEDIFF(YEAR, start, end)` in SQL Server, `MONTHS_BETWEEN(end, start)/12` in Oracle, and `AGE(end, start)` in PostgreSQL.
   - Applying a function to a column in a WHERE clause prevents the use of an index on that column, so on a large table the condition should be rewritten as a range on the raw column: `WHERE join_date < DATE_SUB(CURDATE(), INTERVAL 25 YEAR)`. This is the same test but it can use an index.
   - The result is truncated rather than rounded, so a service of 25 years and 11 months returns 25 and is excluded by `> 25`. <!-- verify -->
48. **(c) In a SQL query, while performing string matching when do we use operator and when we use LIKE operator? Give examples.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 803 (ET: N/A)]*


   Answer: The two operators serve different purposes, and using the wrong one is a common error.

   The `=` operator:
   - It tests for exact equality of the entire string. Every character must match, and no wildcard is interpreted.
   - It is used when the complete value is known.
   - It is fast, because it can use an index on the column directly.

   ```sql
   SELECT * FROM Employee WHERE emp_name = 'Rahim';
   -- Matches only the exact string 'Rahim'. It does not match
   -- 'Rahim Uddin', 'Md. Rahim' or 'rahim' in a case sensitive collation.
   ```

   The `LIKE` operator:
   - It performs pattern matching, and it recognises two wildcards: `%` matches any sequence of characters including none, and `_` matches exactly one character.
   - It is used when only part of the value is known, or when a pattern rather than a fixed value is being sought.

   ```sql
   -- Names beginning with 'R'
   SELECT * FROM Employee WHERE emp_name LIKE 'R%';

   -- Names ending with 'm'
   SELECT * FROM Employee WHERE emp_name LIKE '%m';

   -- Names containing 'ahi' anywhere
   SELECT * FROM Employee WHERE emp_name LIKE '%ahi%';

   -- Names whose second letter is 'a'
   SELECT * FROM Employee WHERE emp_name LIKE '_a%';

   -- Names of exactly five characters
   SELECT * FROM Employee WHERE emp_name LIKE '_____';

   -- Email addresses at a particular domain
   SELECT * FROM Employee WHERE email LIKE '%@gmail.com';
   ```

   When to use which:
   - Use `=` when the full value is known and an exact match is required, which is almost always the case for keys, codes and identifiers.
   - Use `LIKE` only when a pattern is genuinely needed, for a search box or a partial match.

   Points that earn marks:
   - `LIKE 'Rahim'` without any wildcard is equivalent to `= 'Rahim'`, so the wildcards are what give LIKE its purpose.
   - `LIKE` with a leading wildcard, as in `'%ahi%'`, cannot use an index and forces a full table scan, so it is slow on a large table. A pattern anchored at the start, such as `'R%'`, can still use an index.
   - To search for a literal percent sign or underscore, an escape character must be declared: `WHERE code LIKE '50\%%' ESCAPE '\\'`.
   - Case sensitivity depends on the column's collation. `UPPER(emp_name) LIKE 'R%'` forces case insensitivity but again defeats the index.
   - For complex patterns, `REGEXP` in MySQL or `SIMILAR TO` in PostgreSQL offers full regular expressions, at a further cost in speed.
49. **Consider the Electrical Powr company database which has the following tables: Powerplant(Powerplant_ID, location, type, capacity.unit_price) Customer(Customer_ID, name, address, DoB, monthly_demand) Customer_usage_profile(ID, month_name, Customer_ID, Powrplant_ID) The powerplant relation has attributes powerplan_ID, loation, Type{Thrmal power, hydro power, nuclear power, nuclear power, capacity, and unit_price of power generated by the powerplant. The customer relation has attributes Customer_ID, name, address, date of birth(DoB) and monthly_demand of electrical power. The customer_usesge_profile relation stores the user profile of a customer. A customer more usage hydropower during the rainy season and thermal or nuclear power during the dry season. Write the relational algebra expressions for the following queries: (i) List the customers with a yearly bill of more than taka 5,000. (ii) List the customers who uses nuclear power during December and has a monthly bill less then 500 in December.** *[BPDB Assistant Engineer (CSE) 2021 compact it 818 (ET: BUET)]*


   Answer:

   (i) Customers with a yearly bill of more than 5,000 taka:

   - The bill for one month is the customer's monthly demand multiplied by the unit price of the power plant supplying them in that month. The yearly bill is the sum over the twelve months recorded in the usage profile.

   Relational algebra:
   - Step 1, join the three relations on the identifiers:
   - T1 ← Customer ⋈_(Customer.Customer_ID = Customer_usage_profile.Customer_ID) Customer_usage_profile
   - T2 ← T1 ⋈_(T1.Powerplant_ID = Powerplant.Powerplant_ID) Powerplant
   - Step 2, group by customer and sum the monthly charges:
   - T3 ← _(Customer_ID, name) γ _(SUM(monthly_demand × unit_price) → yearly_bill) (T2)
   - Step 3, select and project:
   - Result ← π_(Customer_ID, name) ( σ_(yearly_bill > 5000) (T3) )

   Equivalent SQL:

   ```sql
   SELECT c.Customer_ID, c.name,
          SUM(c.monthly_demand * p.unit_price) AS yearly_bill
   FROM   Customer c
   JOIN   Customer_usage_profile u ON c.Customer_ID = u.Customer_ID
   JOIN   Powerplant p ON u.Powerplant_ID = p.Powerplant_ID
   GROUP  BY c.Customer_ID, c.name
   HAVING SUM(c.monthly_demand * p.unit_price) > 5000;
   ```

   (ii) Customers who use nuclear power in December and whose December bill is less than 500:

   Relational algebra:
   - T1 ← σ_(type = 'nuclear power') (Powerplant)
   - T2 ← σ_(month_name = 'December') (Customer_usage_profile)
   - T3 ← Customer ⋈ T2 ⋈_(Powerplant_ID) T1
   - Result ← π_(Customer_ID, name) ( σ_(monthly_demand × unit_price < 500) (T3) )

   Equivalent SQL:

   ```sql
   SELECT c.Customer_ID, c.name,
          c.monthly_demand * p.unit_price AS december_bill
   FROM   Customer c
   JOIN   Customer_usage_profile u ON c.Customer_ID = u.Customer_ID
   JOIN   Powerplant p ON u.Powerplant_ID = p.Powerplant_ID
   WHERE  u.month_name = 'December'
     AND  p.type = 'nuclear power'
     AND  c.monthly_demand * p.unit_price < 500;
   ```

   Points worth stating:
   - Selection is pushed as early as possible, that is the restriction to December and to nuclear plants is applied before the join wherever the optimiser can do so, because that reduces the number of rows joined. This is the standard query optimisation heuristic and it is what the algebraic form makes visible.
   - The aggregation operator γ is an extension of the basic relational algebra; the basic operators alone cannot express SUM.
   - The schema is somewhat unrealistic, since `monthly_demand` is stored once per customer rather than once per month, so every month's demand is assumed equal. That assumption should be stated. <!-- verify -->
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

   The table after the INSERT contains 7 rows: 1, 2, 3, NULL, NULL, 4, 5.

   Query 1:

   ```sql
   SELECT count(*) AS val_count FROM t;
   ```

   - Output: 7
   - `COUNT(*)` counts rows, not values. It includes every row regardless of whether any column is NULL, so both NULL rows are counted.

   Query 2:

   ```sql
   SELECT count(DISTINCT val) AS val_count FROM t;
   ```

   - Output: 5
   - `COUNT(column)` ignores NULLs entirely, so the two NULL rows are excluded. `DISTINCT` then removes duplicates, and the remaining values 1, 2, 3, 4 and 5 are already distinct, giving 5.

   For completeness, the third form that such questions usually include:

   ```sql
   SELECT count(val) AS val_count FROM t;
   ```

   - Output: 5 as well, since `COUNT(val)` ignores the two NULLs but does not remove duplicates. Here the non-null values happen to be distinct, so the answer coincides; had the data contained a repeated value, `COUNT(val)` and `COUNT(DISTINCT val)` would differ.

   The rule to state:
   - `COUNT(*)` counts rows and includes NULLs.
   - `COUNT(column)` counts non-null values in that column.
   - `COUNT(DISTINCT column)` counts distinct non-null values.
   - The same principle applies to every aggregate function: SUM, AVG, MIN and MAX all ignore NULLs. In particular `AVG` divides by the number of non-null values, not by the number of rows, so `AVG(val)` here would be (1+2+3+4+5)/5 = 3 and not 15/7.
51. **Write SQL command from the following tables. Employee (ename, street, city) Works (ename, cname, salary, joindate) Company (cname, city) Manages (ename, mname) (a) Find name, street, city who work for First Corporation Bank and earn more than 30000 (b) Find name of all employees, who live in the same city and company for which they work. (c) Give all employees of First Century Bank 10 percent salary raise (d) Find the company with payroll less than 100000.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 835-836 (ET: N/A)]*


   Answer:

   (a) Name, street and city of employees who work for First Corporation Bank and earn more than 30000:

   ```sql
   SELECT e.ename, e.street, e.city
   FROM   Employee e
   JOIN   Works w ON e.ename = w.ename
   WHERE  w.cname = 'First Corporation Bank'
     AND  w.salary > 30000;
   ```

   - The address is in Employee and the company and salary are in Works, so the two must be joined on `ename`.

   (b) Employees who live in the same city as the company for which they work:

   ```sql
   SELECT e.ename
   FROM   Employee e
   JOIN   Works w   ON e.ename = w.ename
   JOIN   Company c ON w.cname = c.cname
   WHERE  e.city = c.city;
   ```

   - Three tables are needed: Employee for the residence, Works for the employment link, and Company for the company's city. The condition compares the two city columns.

   (c) Give all employees of First Century Bank a 10 percent salary raise:

   ```sql
   UPDATE Works
   SET    salary = salary * 1.10
   WHERE  cname = 'First Century Bank';
   ```

   - The `WHERE` clause is essential; without it every employee of every company would receive the raise. `salary = salary * 1.10` increases the value by 10 percent.

   (d) Companies with a payroll of less than 100000:

   ```sql
   SELECT cname, SUM(salary) AS total_payroll
   FROM   Works
   GROUP  BY cname
   HAVING SUM(salary) < 100000;
   ```

   - The payroll is the total of the salaries paid by a company, so the rows are grouped by company and summed. The condition applies to an aggregate, so it belongs in HAVING rather than WHERE.

   - Note on the schema: joining on `ename` implies that employee names are unique, which is unrealistic. In a properly designed schema an `eid` would be the key and the join would use it. The point is worth making, since the examiner is testing whether the candidate notices the design weakness.
52. **DB schema: book (book_id, book_title, book_type, publication_name) author (book_name, author_name) publicher (publication_name, publication_address, est_year) copies (book_id, branch_name, no_of-copies) [database query লিখতে আসছিল]** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)]*


   Answer: The question states only that a query was required, without giving it, so the standard queries on this library schema are set out.

   Schema, with the evident misprints corrected: `book(book_id, book_title, book_type, publication_name)`, `author(book_id, author_name)`, `publisher(publication_name, publication_address, est_year)`, `copies(book_id, branch_name, no_of_copies)`.

   ```sql
   -- All books of a particular type
   SELECT book_title FROM book WHERE book_type = 'Computer Science';

   -- Books with their authors
   SELECT b.book_title, a.author_name
   FROM   book b JOIN author a ON b.book_id = a.book_id;

   -- Books published by a particular publisher
   SELECT b.book_title, p.publication_address
   FROM   book b JOIN publisher p ON b.publication_name = p.publication_name
   WHERE  p.publication_name = 'Oxford University Press';

   -- Total number of copies of each book across all branches
   SELECT b.book_title, SUM(c.no_of_copies) AS total_copies
   FROM   book b JOIN copies c ON b.book_id = c.book_id
   GROUP  BY b.book_id, b.book_title;

   -- Branches holding more than 50 books in total
   SELECT branch_name, SUM(no_of_copies) AS total
   FROM   copies GROUP BY branch_name HAVING SUM(no_of_copies) > 50;

   -- Books written by more than one author
   SELECT b.book_title, COUNT(*) AS author_count
   FROM   book b JOIN author a ON b.book_id = a.book_id
   GROUP  BY b.book_id, b.book_title HAVING COUNT(*) > 1;

   -- Books of which no branch holds a copy
   SELECT b.book_title
   FROM   book b LEFT JOIN copies c ON b.book_id = c.book_id
   WHERE  c.book_id IS NULL;

   -- Publishers established before 1950
   SELECT publication_name FROM publisher WHERE est_year < 1950;

   -- The author with the largest number of books
   SELECT author_name, COUNT(*) AS books
   FROM   author GROUP BY author_name
   ORDER  BY books DESC LIMIT 1;
   ```

   Note on the schema as printed:
   - The `author` relation is given as `(book_name, author_name)`, which links to the book by its title rather than by its identifier. That is poor design, since titles are not unique and are liable to change, and it also makes the join slower. The corrected form uses `book_id`, and pointing this out is part of a full answer. <!-- verify -->
53. **Given Table: Project (Project_id, Project_name, Manager_name) Location (location_id, Location_name, project_id) Employee (Employee_id, Employee_Name, Location_id, Joning date, Salary) Write a query to show project_name, Location_name, Total_salary of each projects employee who joined before ‘January 2021’.** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 868 (ET: BUET)]*


   Answer:

   ```sql
   SELECT p.Project_name,
          l.Location_name,
          SUM(e.Salary) AS Total_salary
   FROM   Project p
   JOIN   Location l ON p.Project_id = l.project_id
   JOIN   Employee e ON l.location_id = e.Location_id
   WHERE  e.Joining_date < '2021-01-01'
   GROUP  BY p.Project_id, p.Project_name, l.location_id, l.Location_name;
   ```

   Explanation:
   - The chain of relationships is Project to Location on `project_id`, and Location to Employee on `location_id`. Employees are not linked to projects directly, so both joins are required.
   - `WHERE e.Joining_date < '2021-01-01'` keeps only employees who joined before January 2021. This filter is applied to individual rows, so it belongs in WHERE and is applied before grouping.
   - `GROUP BY` produces one row per project and location combination, and `SUM(e.Salary)` totals the salaries of the qualifying employees within it.
   - Grouping by the identifiers as well as the names is safer, since two projects or locations could share a name.

   Refinements:
   - To rank the projects by cost: add `ORDER BY Total_salary DESC`.
   - To include projects with no qualifying employee, showing zero, use LEFT JOINs and `COALESCE(SUM(e.Salary), 0)`; note also that with a LEFT JOIN the date condition must move into the ON clause, because placing it in WHERE would discard the unmatched rows and defeat the outer join.
   - Date literal syntax varies: `'2021-01-01'` works in MySQL and PostgreSQL, while Oracle requires `TO_DATE('01-JAN-2021', 'DD-MON-YYYY')`.
54. **(i) SQL Query for finding Dept names for departments Find out the employees whose salaries are greater than the salaries of their managers.** *[NESCO Assistant Manager (ICT) 2021 compact it 907 (ET: BUET)]*


   Answer:

   Employees whose salary is greater than their manager's salary:

   ```sql
   SELECT e.employee_id,
          e.emp_name  AS employee_name,
          e.salary    AS employee_salary,
          m.emp_name  AS manager_name,
          m.salary    AS manager_salary
   FROM   Employee e
   JOIN   Employee m ON e.manager_id = m.employee_id
   WHERE  e.salary > m.salary;
   ```

   Explanation:
   - This is a self join: the Employee table is joined to itself, once as `e` for the employee and once as `m` for the manager, using `e.manager_id = m.employee_id`. The aliases are what make the self join possible.
   - The WHERE clause then keeps only the pairs in which the subordinate earns more than the manager.
   - An inner join is correct here, because an employee with no manager has a NULL `manager_id` and cannot satisfy the comparison anyway.

   Department names, which the first part of the question also asks for:

   ```sql
   SELECT DISTINCT d.dept_name
   FROM   Employee e
   JOIN   Employee   m ON e.manager_id = m.employee_id
   JOIN   Department d ON e.dept_id    = d.dept_id
   WHERE  e.salary > m.salary;
   ```

   - `DISTINCT` prevents a department from being listed more than once if it contains several such employees.

   - The self join is the point being tested. It is the standard technique whenever a table must be compared against itself, as in manager and subordinate relationships, employees sharing a salary, or consecutive rows in a sequence.
55. **Two SQL query from given table (date and join related).** *[Sonali Bank Ltd. Officer IT 2021 compact it 910 (ET: N/A)]*


   Answer: The question gives no table, so the standard date and join queries are set out, which is what "date and join related" indicates.

   Date related queries:

   ```sql
   -- Employees who joined in 2023
   SELECT emp_name, join_date FROM Employee
   WHERE  join_date BETWEEN '2023-01-01' AND '2023-12-31';

   -- Employees who joined in the last 90 days
   SELECT emp_name FROM Employee
   WHERE  join_date >= DATE_SUB(CURDATE(), INTERVAL 90 DAY);

   -- Length of service in complete years
   SELECT emp_name, TIMESTAMPDIFF(YEAR, join_date, CURDATE()) AS years_of_service
   FROM   Employee;

   -- Employees who joined on the same date
   SELECT join_date, COUNT(*) AS number_joined
   FROM   Employee GROUP BY join_date HAVING COUNT(*) > 1;

   -- Number of employees recruited in each year
   SELECT YEAR(join_date) AS year, COUNT(*) AS recruits
   FROM   Employee GROUP BY YEAR(join_date) ORDER BY year;

   -- Employees whose birthday falls this month
   SELECT emp_name FROM Employee WHERE MONTH(dob) = MONTH(CURDATE());
   ```

   Join related queries:

   ```sql
   -- Inner join: employees with their department name
   SELECT e.emp_name, d.dept_name
   FROM   Employee e JOIN Department d ON e.dept_id = d.dept_id;

   -- Left join: every department, including those with no employee
   SELECT d.dept_name, COUNT(e.emp_id) AS employee_count
   FROM   Department d LEFT JOIN Employee e ON d.dept_id = e.dept_id
   GROUP  BY d.dept_id, d.dept_name;

   -- Anti-join: departments having no employee at all
   SELECT d.dept_name
   FROM   Department d LEFT JOIN Employee e ON d.dept_id = e.dept_id
   WHERE  e.emp_id IS NULL;

   -- Self join: each employee with their manager
   SELECT e.emp_name AS employee, m.emp_name AS manager
   FROM   Employee e LEFT JOIN Employee m ON e.manager_id = m.emp_id;
   ```

   Points that earn marks:
   - `COUNT(e.emp_id)` rather than `COUNT(*)` must be used with a LEFT JOIN, otherwise an empty department is wrongly reported as having one employee.
   - Applying a function to a column in a WHERE clause, as in `YEAR(join_date) = 2023`, prevents the use of an index; a range condition on the raw column is faster.
   - Date function names differ between systems: `CURDATE()` and `DATE_SUB` in MySQL, `SYSDATE` in Oracle, `GETDATE()` in SQL Server, and `CURRENT_DATE` in the ANSI standard. <!-- verify -->
56. **emp [e_id, e_name, dept_id, salary, DOB], dept [dept_id, city, dept_name]; প্রত্যেকটি Department এর নাম এবং ঐ Department এর employee দের গড় Salary দেখার SQL Query লিখ।** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 911 (ET: BUET)]*


   Answer:

   ```sql
   SELECT d.dept_name,
          AVG(e.salary) AS average_salary
   FROM   dept d
   JOIN   emp e ON d.dept_id = e.dept_id
   GROUP  BY d.dept_id, d.dept_name;
   ```

   Explanation:
   - The department name is in `dept` and the salary in `emp`, so the two tables are joined on `dept_id`, which is the primary key of one and the foreign key in the other.
   - `GROUP BY` collapses the joined rows by department, and `AVG(e.salary)` computes the mean salary within each group.
   - Grouping by `d.dept_id` as well as the name is safer, since two departments could share a name.

   To include departments that have no employees:

   ```sql
   SELECT d.dept_name,
          COALESCE(AVG(e.salary), 0) AS average_salary
   FROM   dept d
   LEFT JOIN emp e ON d.dept_id = e.dept_id
   GROUP  BY d.dept_id, d.dept_name;
   ```

   - An inner join silently omits an empty department. The LEFT JOIN keeps it, and `COALESCE` turns the resulting NULL average into 0.

   Refinements:
   - `ROUND(AVG(e.salary), 2)` gives a readable figure.
   - `ORDER BY average_salary DESC` ranks the departments.
   - Adding `HAVING AVG(e.salary) > 50000` restricts the output; the condition is on an aggregate and therefore cannot be placed in WHERE.
   - `AVG` ignores NULL salaries rather than treating them as zero, which changes the answer if any salary is missing.
57. **Database table by name Loan Records is given below: What is the output of the following SQL query?** *[BAUST Assistant Programmer 2021 compact it 919-920 (ET: N/A)]*
```sql
SELECT count (*) FROM (
(SELECT Borrower, Bank_Manager, FROM Loan_Records) AS S NATURAL JOIN
(SELECT Bank_Manager, Loan_Amount FROM Loan_Records) AS T);
```


   Answer:

   ```sql
   SELECT count(*) FROM (
       (SELECT Borrower, Bank_Manager FROM Loan_Records) AS S
       NATURAL JOIN
       (SELECT Bank_Manager, Loan_Amount FROM Loan_Records) AS T
   );
   ```

   Method:
   - S projects the pairs (Borrower, Bank_Manager) and T projects the pairs (Bank_Manager, Loan_Amount) from the same table.
   - The only attribute common to S and T is `Bank_Manager`, so the natural join matches on that column alone. Note that it does not match on the original row; a borrower is paired with every loan amount belonging to the same manager, including rows of other borrowers.
   - The number of resulting rows is therefore the sum, over each manager, of (number of rows in S with that manager) × (number of rows in T with that manager).

   Worked example, with the Loan_Records table usually given with this question:

   | Borrower | Bank_Manager | Loan_Amount |
   |---|---|---|
   | Ramesh | Sunderajan | 10000 |
   | Suresh | Ramgopal | 5000 |
   | Mahesh | Sunderajan | 7000 |

   - S contains (Ramesh, Sunderajan), (Suresh, Ramgopal), (Mahesh, Sunderajan).
   - T contains (Sunderajan, 10000), (Ramgopal, 5000), (Sunderajan, 7000).
   - Sunderajan appears in 2 rows of S and 2 rows of T, contributing 2 × 2 = 4 rows.
   - Ramgopal appears in 1 row of each, contributing 1 × 1 = 1 row.
   - Total: 4 + 1 = 5

   Output: 5

   The point being tested:
   - The natural join is performed on `Bank_Manager` only, because that is the sole common attribute after the projections. Candidates who assume the rows are rejoined on their original identity answer 3, which is the commonest error.
   - Whenever a manager handles more than one loan, the join multiplies the rows, which is why the count exceeds the number of rows in the base table.
   - Note also that the query as printed contains a stray comma after `Bank_Manager` in the first subquery, which would be a syntax error and should be removed.
58. **Below tables are given, Employee (employee_id, name, salary, department) Leave (employee_id, date, reason, no_leaves) Holiday (Date, description) (i) Write mapping cardinality between 'Employee' and 'Holiday' table. (ii) Write query to show all employee's leave count. (iii) Write query to show employees who are in 'HR' department and have taken at least 5 leaves.** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 928 (ET: CTI)]*


   Answer:

   (i) Mapping cardinality between Employee and Holiday:
   - There is no direct relationship between the two tables at all. Holiday is a standalone calendar of dates and descriptions; it has no employee identifier, and Employee has no reference to it. A public holiday applies to every employee automatically rather than being assigned to any of them.
   - If a relationship were to be modelled, for example to record which employees worked on a holiday, it would be many to many: one holiday can involve many employees and one employee can work on many holidays. Such a relationship requires a junction table, for example `Holiday_Duty(employee_id, date)`.
   - The indirect connection that does exist runs through Leave: `Leave.date` and `Holiday.Date` share a domain, so a leave taken on a holiday could be detected by joining on the date. That is a join of convenience, not a modelled relationship.

   (ii) Leave count of every employee:

   ```sql
   SELECT e.employee_id,
          e.name,
          COALESCE(SUM(l.no_leaves), 0) AS total_leaves
   FROM   Employee e
   LEFT JOIN Leave l ON e.employee_id = l.employee_id
   GROUP  BY e.employee_id, e.name;
   ```

   - A `LEFT JOIN` is essential so that an employee who has taken no leave appears with a total of zero rather than being omitted, and `COALESCE` converts the resulting NULL into 0.
   - `SUM(l.no_leaves)` is used rather than `COUNT(*)`, because the table records the number of days per leave record; counting rows would count applications rather than days.

   (iii) Employees in the HR department who have taken at least 5 leaves:

   ```sql
   SELECT e.employee_id,
          e.name,
          SUM(l.no_leaves) AS total_leaves
   FROM   Employee e
   JOIN   Leave l ON e.employee_id = l.employee_id
   WHERE  e.department = 'HR'
   GROUP  BY e.employee_id, e.name
   HAVING SUM(l.no_leaves) >= 5;
   ```

   - `WHERE e.department = 'HR'` is a condition on individual rows and so is applied before grouping.
   - `HAVING SUM(l.no_leaves) >= 5` is a condition on an aggregate and so is applied after grouping. Placing either in the wrong clause is the error the question is testing.
   - An inner join is appropriate here, since an employee who has taken no leave cannot satisfy the condition.
59. **Find the Query for the Instructor table a. Find the average salary of instructors in each department. b. Find the names and average salaries of all departments whose average salary is greater than 42000. c. Find names of instructors with salary greater than that of some (at least one) instructor in the CSE department.** *[NRCC Assistant Programmer 2021 compact it 930 (ET: N/A)]*


   Answer:

   (a) Average salary of instructors in each department:

   ```sql
   SELECT dept_name, AVG(salary) AS average_salary
   FROM   Instructor
   GROUP  BY dept_name;
   ```

   (b) Names and average salaries of departments whose average salary exceeds 42000:

   ```sql
   SELECT dept_name, AVG(salary) AS average_salary
   FROM   Instructor
   GROUP  BY dept_name
   HAVING AVG(salary) > 42000;
   ```

   - The condition applies to a group aggregate, so it must be placed in `HAVING`. A `WHERE` clause is evaluated before grouping and cannot refer to `AVG`.

   (c) Instructors whose salary is greater than that of at least one instructor in the CSE department:

   ```sql
   SELECT DISTINCT name
   FROM   Instructor
   WHERE  salary > SOME (SELECT salary FROM Instructor WHERE dept_name = 'CSE');
   ```

   - `SOME` and `ANY` are synonyms and mean "greater than at least one of these values", which is exactly what the question asks. It is equivalent to being greater than the minimum of the set.
   - The same query can be written without the quantifier:

   ```sql
   SELECT DISTINCT name
   FROM   Instructor
   WHERE  salary > (SELECT MIN(salary) FROM Instructor WHERE dept_name = 'CSE');
   ```

   The distinction that carries the marks:
   - `> SOME` or `> ANY` means greater than at least one, which is equivalent to greater than the minimum.
   - `> ALL` means greater than every one, which is equivalent to greater than the maximum.
   - Confusing the two is the commonest error in this question. If the requirement had been "greater than every instructor in CSE", the query would be `WHERE salary > ALL (SELECT salary FROM Instructor WHERE dept_name = 'CSE')`.
   - `DISTINCT` guards against duplicate names appearing in the output.
60. **Consider the following relational database schema consisting of the four relation schemas: passenger (pid, ppname, pgender, pcity) agency (aid, aname, acity) flight (fid, fdate, time, src, dest) booking (pid, aid, fid, fdate) a) Get the complete details of all flights to New Delhi b) Get the details about all flights from Chennai to New Delhi.** *[SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)]*


   Answer:

   (a) Complete details of all flights to New Delhi:

   ```sql
   SELECT *
   FROM   flight
   WHERE  dest = 'New Delhi';
   ```

   - The flight relation already holds the destination, so no join is required. `SELECT *` is appropriate because the question asks for complete details.

   (b) Details of all flights from Chennai to New Delhi:

   ```sql
   SELECT *
   FROM   flight
   WHERE  src  = 'Chennai'
     AND  dest = 'New Delhi';
   ```

   - Both conditions must hold, so they are combined with `AND`.

   Related queries on the same schema, which such a question usually continues with:

   ```sql
   -- Passengers who booked a flight to New Delhi
   SELECT DISTINCT p.pname
   FROM   passenger p
   JOIN   booking b ON p.pid = b.pid
   JOIN   flight  f ON b.fid = f.fid
   WHERE  f.dest = 'New Delhi';

   -- Agencies in Chennai that have made a booking
   SELECT DISTINCT a.aname
   FROM   agency a JOIN booking b ON a.aid = b.aid
   WHERE  a.acity = 'Chennai';

   -- Number of bookings per flight
   SELECT f.fid, f.src, f.dest, COUNT(*) AS bookings
   FROM   flight f JOIN booking b ON f.fid = b.fid
   GROUP  BY f.fid, f.src, f.dest;

   -- Flights with no booking at all
   SELECT f.fid, f.src, f.dest
   FROM   flight f LEFT JOIN booking b ON f.fid = b.fid
   WHERE  b.fid IS NULL;
   ```

   - Note that `booking` carries both `fid` and `fdate`, which duplicates the date already held in `flight`. That redundancy is a design weakness, since the two could disagree; it is worth pointing out.
61. **৫. সম্পূর্ণ টেবিলের ডেটা প্রদর্শন এর জন্য কোনটি ব্যবহার করা হয়?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*


   Answer: The `SELECT` statement with the asterisk is used to display all the data of a complete table.

   ```sql
   SELECT * FROM table_name;
   ```

   - The asterisk means "all columns", and the absence of a `WHERE` clause means all rows, so the whole table is returned.
   - Example: `SELECT * FROM Employee;` displays every column of every row of the Employee table.

   Related forms:
   - `SELECT column1, column2 FROM table_name;` displays only the named columns, which is better practice in application code because it is unaffected by later changes to the table structure and transfers less data.
   - `SELECT * FROM table_name WHERE condition;` displays only the rows satisfying the condition.
   - `SELECT DISTINCT column FROM table_name;` displays the distinct values of a column.
   - `SELECT * FROM table_name ORDER BY column;` displays the whole table in sorted order.
   - `DESCRIBE table_name;` or `DESC table_name;` displays the structure of the table, that is its columns and their data types, rather than its data. This is the answer if the question means the structure rather than the contents.
62. **Write a SQL query to find those employees who report that manager whose first name is ‘abc’. Return first name, last name, employee ID and salary.** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 947 (ET: BUET)]*


   Answer:

   ```sql
   SELECT e.first_name,
          e.last_name,
          e.employee_id,
          e.salary
   FROM   Employees e
   JOIN   Employees m ON e.manager_id = m.employee_id
   WHERE  m.first_name = 'abc';
   ```

   Explanation:
   - This is a self join: the Employees table is joined to itself, once as `e` for the subordinate and once as `m` for the manager, using `e.manager_id = m.employee_id`. The two aliases are what make the self join possible.
   - The condition `m.first_name = 'abc'` restricts the manager side, so the query returns the employees reporting to that manager.
   - An inner join is correct here, since an employee with no manager cannot report to anyone.

   Equivalent using a subquery:

   ```sql
   SELECT first_name, last_name, employee_id, salary
   FROM   Employees
   WHERE  manager_id IN (SELECT employee_id FROM Employees WHERE first_name = 'abc');
   ```

   - `IN` rather than `=` is used because more than one manager could share the first name; with `=` the query would fail with a "more than one row" error.

   Related variation, all employees under a manager at any depth, which requires recursion:

   ```sql
   WITH RECURSIVE subordinates AS (
       SELECT employee_id, first_name, last_name, manager_id
       FROM   Employees WHERE first_name = 'abc'
       UNION ALL
       SELECT e.employee_id, e.first_name, e.last_name, e.manager_id
       FROM   Employees e
       JOIN   subordinates s ON e.manager_id = s.employee_id
   )
   SELECT * FROM subordinates WHERE first_name <> 'abc';
   ```

   - The simple self join returns only the direct reports; a recursive common table expression is needed to walk the whole hierarchy.
63. **Given a database schema and worker table with fully code: Now writes SQL Query from the following questions.** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 975 (ET: BUET)]*


   Answer: The schema and the specific requirements are not reproduced in the question, so the standard queries on a worker table are set out, which is what such a question expects.

   ```sql
   -- Table assumed: Worker(worker_id, first_name, last_name, salary, joining_date, department)

   -- All records
   SELECT * FROM Worker;

   -- Specific columns with an alias
   SELECT first_name AS WORKER_NAME, salary FROM Worker;

   -- Names in upper case
   SELECT UPPER(first_name) FROM Worker;

   -- Distinct departments
   SELECT DISTINCT department FROM Worker;

   -- Workers whose name contains 'a'
   SELECT * FROM Worker WHERE first_name LIKE '%a%';

   -- Workers whose salary is between 50000 and 100000
   SELECT * FROM Worker WHERE salary BETWEEN 50000 AND 100000;

   -- Workers in the Admin or HR department
   SELECT * FROM Worker WHERE department IN ('Admin', 'HR');

   -- Number of workers in each department
   SELECT department, COUNT(*) AS total FROM Worker GROUP BY department;

   -- Departments having more than 5 workers
   SELECT department, COUNT(*) FROM Worker
   GROUP BY department HAVING COUNT(*) > 5;

   -- Highest paid worker
   SELECT * FROM Worker WHERE salary = (SELECT MAX(salary) FROM Worker);

   -- Second highest salary
   SELECT MAX(salary) FROM Worker
   WHERE salary < (SELECT MAX(salary) FROM Worker);

   -- Nth highest salary, here the third
   SELECT DISTINCT salary FROM Worker ORDER BY salary DESC LIMIT 1 OFFSET 2;

   -- Duplicate names
   SELECT first_name, COUNT(*) FROM Worker
   GROUP BY first_name HAVING COUNT(*) > 1;

   -- Workers who joined in February
   SELECT * FROM Worker WHERE MONTH(joining_date) = 2;

   -- Workers sorted by salary, highest first
   SELECT * FROM Worker ORDER BY salary DESC;
   ```

   Points that earn marks:
   - Use `IS NULL` and not `= NULL`.
   - Place row conditions in WHERE and aggregate conditions in HAVING.
   - Every non-aggregated column in SELECT must appear in GROUP BY.
   - `BETWEEN` is inclusive at both ends. <!-- verify -->
64. **(b) SQL Query: commission greater than 10%** *[National University Assistant Programmer 2020 compact it 976 (ET: DU)]*


   Answer:

   ```sql
   SELECT emp_id, emp_name, commission_pct
   FROM   Employee
   WHERE  commission_pct > 0.10;
   ```

   - This assumes the commission is stored as a fraction, so that 10 percent is 0.10, which is the convention in the standard HR schema.
   - If the column stores the percentage as a whole number, the condition becomes `WHERE commission_pct > 10`.

   Handling NULL commissions, which is the point such a question usually tests:

   ```sql
   SELECT emp_id, emp_name, COALESCE(commission_pct, 0) AS commission_pct
   FROM   Employee
   WHERE  COALESCE(commission_pct, 0) > 0.10;
   ```

   - Employees earning no commission commonly have NULL in that column rather than 0. A comparison with NULL yields UNKNOWN rather than TRUE, so such rows are excluded by the plain condition, which is usually the desired behaviour but should be stated explicitly.
   - `COALESCE(commission_pct, 0)` replaces NULL with zero where the rows must still be considered.

   Related forms:

   ```sql
   -- Employees earning no commission at all
   SELECT emp_name FROM Employee WHERE commission_pct IS NULL;

   -- Total pay including commission
   SELECT emp_name, salary, salary * COALESCE(commission_pct, 0) AS commission,
          salary * (1 + COALESCE(commission_pct, 0)) AS total_pay
   FROM   Employee;
   ```

   - `IS NULL` must be used rather than `= NULL`, since NULL is never equal to anything, including itself.
65. **(c) Remove duplicate data from table** *[National University Assistant Programmer 2020 compact it 976 (ET: DU)]*


   Answer: Duplicate rows are removed by keeping one representative of each group and deleting the rest, identified by the lowest primary key value.

   Method 1, using a subquery with MIN, which is the standard approach:

   ```sql
   DELETE FROM Employee
   WHERE  emp_id NOT IN (
              SELECT MIN(emp_id)
              FROM   Employee
              GROUP  BY emp_name, department, salary
          );
   ```

   - The subquery finds, for each distinct combination of values, the smallest identifier. Everything else is a duplicate and is deleted.
   - In MySQL this exact form is rejected, because MySQL forbids selecting from the table being deleted from within a subquery. The remedy is to wrap the subquery in a derived table:

   ```sql
   DELETE FROM Employee
   WHERE  emp_id NOT IN (
              SELECT id FROM (
                  SELECT MIN(emp_id) AS id FROM Employee
                  GROUP BY emp_name, department, salary
              ) AS t
          );
   ```

   Method 2, using a self join:

   ```sql
   DELETE e1
   FROM   Employee e1
   JOIN   Employee e2
     ON   e1.emp_name = e2.emp_name
    AND   e1.department = e2.department
    AND   e1.emp_id > e2.emp_id;
   ```

   - Every row that has an identical twin with a smaller identifier is deleted.

   Method 3, using a window function, which is the modern approach:

   ```sql
   WITH numbered AS (
       SELECT emp_id,
              ROW_NUMBER() OVER (PARTITION BY emp_name, department, salary
                                 ORDER BY emp_id) AS rn
       FROM   Employee
   )
   DELETE FROM Employee
   WHERE  emp_id IN (SELECT emp_id FROM numbered WHERE rn > 1);
   ```

   Method 4, rebuilding the table, which is often fastest for a very large table:

   ```sql
   CREATE TABLE Employee_clean AS SELECT DISTINCT * FROM Employee;
   DROP TABLE Employee;
   ALTER TABLE Employee_clean RENAME TO Employee;
   ```

   Practical points:
   - Always run the equivalent SELECT first to see exactly which rows would be deleted, and take a backup before running the DELETE.
   - Perform the operation inside a transaction so that it can be rolled back.
   - The permanent remedy is to prevent duplication in the first place with a `UNIQUE` constraint on the columns concerned.
   - If there is no primary key, `ROWID` in Oracle or `ctid` in PostgreSQL can be used in its place.
66. **What is the full meaning of SQL? List of the aggregate function. Write SQL Query of a table and its output.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1002-1003 (ET: DU)]*


   Answer:

   Full meaning of SQL:
   - SQL stands for Structured Query Language. It is the standard language for defining, manipulating and controlling data in a relational database. It was developed at IBM in the 1970s, originally as SEQUEL, and it was standardised by ANSI in 1986 and by ISO in 1987.
   - It is a declarative language: the query states what is required, and the database's optimiser decides how to obtain it.

   Aggregate functions in SQL:
   - `COUNT()` returns the number of rows. `COUNT(*)` counts all rows including those with NULLs, while `COUNT(column)` counts only the non-null values.
   - `SUM()` returns the total of a numeric column.
   - `AVG()` returns the arithmetic mean.
   - `MIN()` returns the smallest value.
   - `MAX()` returns the largest value.
   - All of them except `COUNT(*)` ignore NULL values, and all are normally used with `GROUP BY`, their results being filtered by `HAVING` rather than `WHERE`.

   Example query and its output:

   ```sql
   -- Table: Employee
   -- emp_id | emp_name | department | salary
   --   1    | Rahim    | IT         | 45000
   --   2    | Karim    | IT         | 65000
   --   3    | Salma    | Finance    | 40000
   --   4    | Nadia    | Finance    | 80000
   --   5    | Jamal    | HR         | 35000

   SELECT department,
          COUNT(*)    AS total_employees,
          SUM(salary) AS total_salary,
          AVG(salary) AS average_salary,
          MIN(salary) AS lowest_salary,
          MAX(salary) AS highest_salary
   FROM   Employee
   GROUP  BY department
   ORDER  BY total_salary DESC;
   ```

   Output:

   | department | total_employees | total_salary | average_salary | lowest_salary | highest_salary |
   |---|---|---|---|---|---|
   | Finance | 2 | 120000 | 60000 | 40000 | 80000 |
   | IT | 2 | 110000 | 55000 | 45000 | 65000 |
   | HR | 1 | 35000 | 35000 | 35000 | 35000 |

   - `GROUP BY department` creates one group per department, the five aggregate functions summarise each group, and `ORDER BY` ranks the departments by total salary.
67. **Query to find out even number from given table.** *[RAKUB Assistant Database Administrator 2020 compact it 1014 (ET: E-Zone)]*


   Answer:

   ```sql
   SELECT *
   FROM   Numbers
   WHERE  num % 2 = 0;
   ```

   - The modulo operator `%` returns the remainder of a division. A number is even exactly when its remainder on division by 2 is zero.
   - The operator is written `%` in MySQL, SQL Server and PostgreSQL. Oracle has no `%` operator and uses the function `MOD(num, 2) = 0`, which also works in MySQL and PostgreSQL and is therefore the more portable form.

   Portable version:

   ```sql
   SELECT * FROM Numbers WHERE MOD(num, 2) = 0;
   ```

   Related forms:

   ```sql
   -- Odd numbers
   SELECT * FROM Numbers WHERE MOD(num, 2) <> 0;

   -- Rows with an even identifier
   SELECT * FROM Employee WHERE MOD(emp_id, 2) = 0;

   -- Even numbers within a range, sorted
   SELECT * FROM Numbers WHERE MOD(num, 2) = 0 AND num BETWEEN 1 AND 100
   ORDER BY num;

   -- Count of even and odd values
   SELECT CASE WHEN MOD(num, 2) = 0 THEN 'Even' ELSE 'Odd' END AS parity,
          COUNT(*) AS total
   FROM   Numbers GROUP BY parity;

   -- Numbers divisible by 3
   SELECT * FROM Numbers WHERE MOD(num, 3) = 0;
   ```

   Points worth stating:
   - Applying a function to a column in a WHERE clause prevents the use of an index on that column, so on a very large table the query performs a full scan. A computed or functional index on `MOD(num, 2)` would restore index use where the system supports it.
   - For a negative value, `MOD(-4, 2)` is 0 in every system, so negative even numbers are matched correctly; but `MOD(-3, 2)` returns −1 in MySQL and Oracle, so the odd number test should be written as `<> 0` rather than `= 1`.
68. **How to copy from Parent table to Child Table with 1 column dividing into 3 different columns?** *[RAKUB Assistant Database Administrator 2020 compact it 1014-1015 (ET: E-Zone)]*


   Answer: Copying rows from a parent table while splitting one column into three is done with an `INSERT ... SELECT` statement that applies string functions to the source column.

   Suppose the parent table holds a single `full_name` column and the child table has `first_name`, `middle_name` and `last_name`.

   ```sql
   INSERT INTO Child (id, first_name, middle_name, last_name)
   SELECT id,
          SUBSTRING_INDEX(full_name, ' ', 1)                       AS first_name,
          CASE WHEN LENGTH(full_name) - LENGTH(REPLACE(full_name, ' ', '')) >= 2
               THEN SUBSTRING_INDEX(SUBSTRING_INDEX(full_name, ' ', 2), ' ', -1)
               ELSE NULL
          END                                                       AS middle_name,
          SUBSTRING_INDEX(full_name, ' ', -1)                       AS last_name
   FROM   Parent;
   ```

   How the functions work in MySQL:
   - `SUBSTRING_INDEX(str, ' ', 1)` returns everything before the first space, which is the first name.
   - `SUBSTRING_INDEX(str, ' ', -1)` returns everything after the last space, which is the last name.
   - The nested form `SUBSTRING_INDEX(SUBSTRING_INDEX(str, ' ', 2), ' ', -1)` takes the first two words and then the last of those, which is the middle name.
   - The `CASE` guards against names with only two parts, where there is no middle name, so NULL is stored instead of repeating the last name.

   Splitting a delimited column, for example an address of the form 'street,city,postcode':

   ```sql
   INSERT INTO Child (id, street, city, postcode)
   SELECT id,
          SUBSTRING_INDEX(address, ',', 1),
          SUBSTRING_INDEX(SUBSTRING_INDEX(address, ',', 2), ',', -1),
          SUBSTRING_INDEX(address, ',', -1)
   FROM   Parent;
   ```

   Portable version using position and substring, which works in most systems:

   ```sql
   INSERT INTO Child (id, first_name, last_name)
   SELECT id,
          SUBSTRING(full_name, 1, POSITION(' ' IN full_name) - 1),
          SUBSTRING(full_name, POSITION(' ' IN full_name) + 1)
   FROM   Parent;
   ```

   - SQL Server uses `CHARINDEX` and `LEFT`/`RIGHT`; Oracle uses `INSTR` and `SUBSTR`, and also offers `REGEXP_SUBSTR(full_name, '[^ ]+', 1, n)` to extract the nth word directly, which is far cleaner.

   Practical points:
   - Run the `SELECT` part alone first to inspect the results before inserting anything.
   - Trim the source values with `TRIM()`, since leading and trailing spaces are the commonest cause of wrong splits.
   - Decide explicitly what should happen when the name has one part, or four; the CASE expression above handles the two part case and should be extended for the others.
   - If a foreign key links the child to the parent, insert the parent rows first.
69. **Design and Queries from HR schema. (i) Display details of jobs where the minimum salary is greater than 10000. (ii) Display the first name and join date of the employees who joined between 2002 and 2005. (iii) Display first name and join date of the employees who is either IT Programmer or Sales Man. (iv) Display first name, salary, commission pct, and hire date for employees with salary less than 10000. (v) Display job Title, the difference between minimum and maximum salaries for jobs with max salary in the range 10000 to 20000. (vi) Display first name, salary, and round the salary to thousands. (vii) Display employees where the first name or last name starts with S. (viii) Display details of the employees where commission percentage is null and salary in the range 5000 to 10000 and department is 30. (ix) Display first name and date of first salary of the employees. (x) Display first name and last name after converting the first letter of each name to upper case and the rest to lower case.** *[RAKUB Assistant Database Administrator 2020 compact it 1016-1017 (ET: E-Zone)]*


   Answer: These are the standard HR schema queries, using `employees` and `jobs`.

   (i) Jobs where the minimum salary is greater than 10000:

   ```sql
   SELECT * FROM jobs WHERE min_salary > 10000;
   ```

   (ii) Employees who joined between 2002 and 2005:

   ```sql
   SELECT first_name, hire_date
   FROM   employees
   WHERE  hire_date BETWEEN '2002-01-01' AND '2005-12-31';
   ```

   - `BETWEEN` is inclusive at both ends. A range on the raw column is preferable to `YEAR(hire_date) BETWEEN 2002 AND 2005`, because the latter prevents the use of an index.

   (iii) Employees who are either an IT Programmer or a Sales Man:

   ```sql
   SELECT first_name, hire_date
   FROM   employees
   WHERE  job_id IN ('IT_PROG', 'SA_MAN');
   ```

   (iv) Employees with a salary less than 10000:

   ```sql
   SELECT first_name, salary, commission_pct, hire_date
   FROM   employees
   WHERE  salary < 10000;
   ```

   (v) Job title and the salary range, for jobs whose maximum salary is between 10000 and 20000:

   ```sql
   SELECT job_title,
          max_salary - min_salary AS salary_difference
   FROM   jobs
   WHERE  max_salary BETWEEN 10000 AND 20000;
   ```

   (vi) First name, salary, and the salary rounded to the nearest thousand:

   ```sql
   SELECT first_name, salary, ROUND(salary, -3) AS rounded_salary
   FROM   employees;
   ```

   - A negative second argument to `ROUND` rounds to the left of the decimal point, so −3 rounds to the nearest thousand.

   (vii) Employees whose first name or last name starts with S:

   ```sql
   SELECT first_name, last_name
   FROM   employees
   WHERE  first_name LIKE 'S%' OR last_name LIKE 'S%';
   ```

   (viii) Employees with a null commission, a salary between 5000 and 10000, and department 30:

   ```sql
   SELECT *
   FROM   employees
   WHERE  commission_pct IS NULL
     AND  salary BETWEEN 5000 AND 10000
     AND  department_id = 30;
   ```

   - `IS NULL` must be used and not `= NULL`, since a comparison with NULL yields UNKNOWN rather than TRUE.

   (ix) First name and the date of the first salary, taken as the end of the month of joining:

   ```sql
   SELECT first_name, LAST_DAY(hire_date) AS first_salary_date
   FROM   employees;
   ```

   - `LAST_DAY` returns the last day of the month containing the given date, which is when salary is normally paid. In MySQL, `LAST_DAY(hire_date)` works directly; in Oracle the same function exists.

   (x) First name and last name with the first letter capitalised and the rest in lower case:

   ```sql
   SELECT CONCAT(UPPER(SUBSTRING(first_name, 1, 1)), LOWER(SUBSTRING(first_name, 2))) AS first_name,
          CONCAT(UPPER(SUBSTRING(last_name, 1, 1)),  LOWER(SUBSTRING(last_name, 2)))  AS last_name
   FROM   employees;
   ```

   - Oracle provides `INITCAP(first_name)`, which does the whole operation in one function; MySQL has no equivalent, so the expression above is required.
70. **Query for retrieving UNCOMMON Name from Name column of two given tables.** *[RAKUB Assistant Database Administrator 2020 compact it 1017 (ET: E-Zone)]*


   Answer: "Uncommon" names are those appearing in one table but not in the other, in either direction. This is the symmetric difference of the two sets.

   Standard SQL, using EXCEPT in both directions:

   ```sql
   (SELECT name FROM Table1
    EXCEPT
    SELECT name FROM Table2)
   UNION
   (SELECT name FROM Table2
    EXCEPT
    SELECT name FROM Table1);
   ```

   - The first part gives the names present in Table1 but not Table2, the second gives those in Table2 but not Table1, and the union combines them.
   - `EXCEPT` is the ANSI operator; Oracle calls it `MINUS`. MySQL supports `EXCEPT` only from version 8.0.31.

   MySQL version using NOT IN, which works everywhere:

   ```sql
   SELECT name FROM Table1
   WHERE  name NOT IN (SELECT name FROM Table2)
   UNION
   SELECT name FROM Table2
   WHERE  name NOT IN (SELECT name FROM Table1);
   ```

   - `NOT IN` fails silently if the subquery can return NULL, since a comparison with NULL yields UNKNOWN. `NOT EXISTS` is the safer form:

   ```sql
   SELECT t1.name FROM Table1 t1
   WHERE  NOT EXISTS (SELECT 1 FROM Table2 t2 WHERE t2.name = t1.name)
   UNION
   SELECT t2.name FROM Table2 t2
   WHERE  NOT EXISTS (SELECT 1 FROM Table1 t1 WHERE t1.name = t2.name);
   ```

   Version using a full outer join, which also shows which table each name came from:

   ```sql
   SELECT COALESCE(t1.name, t2.name) AS name,
          CASE WHEN t1.name IS NULL THEN 'Only in Table2'
               ELSE 'Only in Table1' END AS source
   FROM   Table1 t1
   FULL OUTER JOIN Table2 t2 ON t1.name = t2.name
   WHERE  t1.name IS NULL OR t2.name IS NULL;
   ```

   For contrast, the common names, that is the intersection:

   ```sql
   SELECT name FROM Table1 INTERSECT SELECT name FROM Table2;
   -- or
   SELECT t1.name FROM Table1 t1 JOIN Table2 t2 ON t1.name = t2.name;
   ```

   - `UNION` removes duplicates; `UNION ALL` keeps them and is faster where duplicates cannot arise or do not matter.
71. **Employee টেবিল থেকে যেসকল Employee এর Salary 25000 থেকে 50000 এর মধ্যে এবং Designation হচ্ছে officer এবং City হচ্ছে Dhaka তাদের দেখার জন্য SQL টেবিল দেখান।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1042 (ET: DPI)]*


   Answer:

   ```sql
   SELECT *
   FROM   Employee
   WHERE  Salary BETWEEN 25000 AND 50000
     AND  Designation = 'Officer'
     AND  City = 'Dhaka';
   ```

   Explanation:
   - `BETWEEN 25000 AND 50000` is inclusive at both ends, so an employee earning exactly 25,000 or exactly 50,000 is included. It is equivalent to `Salary >= 25000 AND Salary <= 50000`. If the bounds were meant to be exclusive, the explicit comparison operators would be required.
   - All three conditions must hold simultaneously, so they are joined with `AND`.
   - String literals are enclosed in single quotes and numeric literals are not.

   Refinements:
   - To list only the required columns rather than all of them: `SELECT emp_id, emp_name, Designation, Salary, City`.
   - To sort the result: add `ORDER BY Salary DESC`.
   - To make the designation match case insensitively: `AND UPPER(Designation) = 'OFFICER'`, though this prevents the use of an index on the column.
   - To count the matching employees rather than list them: `SELECT COUNT(*)` in place of `SELECT *`.

## DBMS Architecture & Features (22)

1. (a) DBMS এর মূল বৈশিষ্ট্য লিখুন।
   (b) HTTP ও HTTPS প্রোটোকলের মধ্যে সুরক্ষার দিক থেকে পার্থক্য ব্যাখ্যা করুন। *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*


   Answer:

   (a) Main features of a DBMS:
   - Data storage and retrieval, with a declarative query language, SQL, so that the user states what is required rather than how to obtain it.
   - Control of redundancy, since data is stored once rather than repeated across many files.
   - Data integrity, enforced by constraints such as primary key, foreign key, NOT NULL, UNIQUE and CHECK, so that invalid data cannot be stored whatever the application does.
   - Concurrency control, allowing many users to read and write simultaneously while transactions and locking keep the result correct.
   - Transaction management with the ACID properties: atomicity, consistency, isolation and durability.
   - Security and authorisation: privileges granted per user on particular tables, columns and operations, with views used to hide sensitive data.
   - Backup and recovery, with transaction logging so that the database can be restored to a consistent state after a crash.
   - Data independence, both logical and physical, so that the storage or the structure can change without rewriting the applications.
   - A data dictionary, that is metadata describing every table, column, index, constraint and privilege.
   - Multiple user views of the same data, and efficient query processing through an optimiser and indexes.

   (b) Difference between HTTP and HTTPS from the security point of view:
   - HTTP transmits everything in plain text, so anyone who can capture the traffic can read the passwords, the card numbers and the whole page content. HTTPS carries the same HTTP inside a TLS encrypted channel, so an interceptor sees only ciphertext. This is confidentiality.
   - HTTPS attaches a message authentication code to every record, so any alteration in transit is detected and the connection is aborted. With HTTP an attacker can inject advertisements or malware into the page and neither side will know. This is integrity.
   - HTTPS requires the server to present an X.509 certificate issued by a trusted Certifying Authority, which the browser validates, proving that the site is genuine. HTTP provides no such assurance, so a counterfeit site is indistinguishable from the real one. This is authentication.
   - Ports: HTTP uses TCP 80 and HTTPS uses TCP 443.
   - Practical consequences: browsers mark HTTP sites as "Not Secure", search engines rank HTTPS higher, PCI DSS and data protection law effectively require HTTPS for any site handling personal or financial data, and HTTP/2 and HTTP/3 are in practice available only over HTTPS.
2. **ODBC এর পূর্ণ রূপ কি?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: ODBC stands for Open Database Connectivity.

   - It is a standard application programming interface, developed by Microsoft in 1992 and now a widely adopted standard, that allows an application to access data in any database management system through a common set of function calls.
   - The purpose is portability: an application written against ODBC can work with Oracle, MySQL, SQL Server or PostgreSQL simply by changing the driver, without any change to the application code.
   - Architecture: the application calls the ODBC API; the Driver Manager loads the appropriate driver; the driver translates the calls into the native protocol of the particular database; and the database returns the result along the same path.
   - A Data Source Name, DSN, holds the connection details, that is the driver, the server, the database and the credentials.
   - Related interfaces: JDBC, Java Database Connectivity, which performs the same role for Java; OLE DB, Microsoft's successor for a wider range of data sources; and ADO.NET on the .NET platform.
   - Advantage: database independence and a single programming interface. Disadvantage: some performance overhead from the translation layer, and driver specific behaviour can still leak through.
3. **Data about data is Called __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: Data about data is called metadata.

   - Metadata describes the structure, meaning, origin and constraints of the actual data, rather than the data itself.
   - In a database it is held in the data dictionary or system catalog, and it records every table, its columns and their data types and sizes, the primary and foreign keys, the indexes, the views, the users and their privileges, and the storage details. The DBMS itself consults the dictionary whenever a query is processed.
   - Examples: for a column holding the value 'Rahim', the metadata is that the column is named `emp_name`, is of type VARCHAR(50), belongs to the table Employee, cannot be NULL and is not a key.
   - Types: descriptive metadata, such as a title or an author; structural metadata, describing how the parts fit together; and administrative metadata, such as the creation date, the owner and the access rights.
   - Beyond databases: the EXIF data of a photograph, that is the camera, date and location; the header of a file; and the tags of an MP3 file are all metadata.
   - Why it matters: it enables the DBMS to validate queries, the optimiser to choose an execution plan, and administrators to understand and govern the data. In data warehousing it is the foundation of data lineage and governance.
4. **Difference between MSAccess and MS FoxPro in SQL.** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 317 (ET: N/A)]*


   Answer:

   | Point | MS Access | MS FoxPro |
   |---|---|---|
   | Type | A relational database management system with a graphical development environment | A procedural database programming language with an integrated database engine |
   | Data model | Relational, with the Jet or ACE engine | Originally flat file dBase style, later relational |
   | SQL support | Full SQL support, though with some dialect differences from ANSI SQL | Limited SQL support, added later on top of its own xBase commands |
   | Programming | VBA, Visual Basic for Applications | FoxPro's own procedural language, later Visual FoxPro with object orientation |
   | Interface | Strong graphical designers for forms, reports and queries | Primarily code driven, with weaker visual tools |
   | Ease of use | Designed for non-programmers; forms and reports are built by dragging | Requires programming knowledge |
   | Performance | Slower with large data volumes | Faster data processing, since it was optimised for that |
   | File format | `.mdb` and `.accdb` | `.dbf` for tables, `.dbc` for the container |
   | Multi-user capacity | Practical up to a few concurrent users | Somewhat better, but still limited |
   | Current status | Still shipped as part of Microsoft Office | Discontinued; support ended in 2015 |
   | Typical use | Small office applications, prototypes, personal databases | Legacy business applications, largely replaced by SQL Server and .NET |

   - In summary: Access is an application development environment with a database attached, aimed at users who are not programmers, while FoxPro was a programming language with a fast data engine, aimed at developers. Both are limited to small scale use, and both have been superseded for serious work by SQL Server, MySQL or PostgreSQL with a modern application framework. <!-- verify -->
5. **(খ) DBMS কী? দুটি সুবিধা লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*


   Answer:

   What a DBMS is:
   - A Database Management System is software that allows users to define, create, store, retrieve, update and manage data in a database, and that controls access to it. It sits between the physical data and the users and applications, so that no program has to know how the data is actually stored.
   - Examples: Oracle, MySQL, PostgreSQL, Microsoft SQL Server, MongoDB.

   Two advantages:
   - Control of data redundancy and consistency: in a file based system the same information is repeated across many files, so it wastes space and the copies inevitably come to disagree. A DBMS stores each item once, so an update is made in one place and every user sees the same value.
   - Data security and integrity: the DBMS enforces integrity constraints such as primary keys, foreign keys and CHECK conditions, so invalid data cannot be stored whatever any application does; and it grants privileges per user on particular tables and columns, so sensitive data is visible only to those authorised to see it.

   Further advantages worth naming if more are wanted:
   - Concurrent access by many users with correct results, through transactions and locking.
   - Automatic backup and recovery after a crash.
   - Data independence, so that storage or structure can change without rewriting applications.
   - A declarative query language, SQL, with an optimiser and indexes, which greatly reduces development effort.
6. **What is Database?** *[EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)]*


   Answer: A database is an organised collection of related data, stored electronically and structured so that it can be efficiently accessed, managed and updated.

   Characteristics:
   - The data is organised rather than arbitrary, normally into tables of rows and columns in a relational database.
   - The data items are related to one another and describe some part of the real world, called the miniworld or the universe of discourse.
   - It is designed and populated for a defined purpose and a defined group of users.
   - It is self describing: alongside the data itself it contains metadata in the data dictionary, describing the structure of the data.
   - It supports concurrent access by many users while remaining consistent.

   Components: the data itself; the schema, that is the structure; the metadata in the data dictionary; and the constraints that define what is valid.

   Types:
   - Relational, storing data in tables with keys and using SQL, such as Oracle, MySQL and PostgreSQL. This is the dominant model.
   - NoSQL, which is non-relational and includes document stores such as MongoDB, key-value stores such as Redis, column family stores such as Cassandra and graph databases such as Neo4j.
   - Others: hierarchical, network, object oriented, distributed, cloud, and data warehouses for analytical work.

   Related terms: a Database Management System is the software that manages the database, and a database system is the combination of the database, the DBMS, the applications and the users.

   Example: a bank's database holding customers, accounts, transactions and branches, in which the tables are related so that a customer's accounts and their transactions can be retrieved together.
7. **What is data about data?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*


   Answer: Data about data is called metadata.

   - It describes the structure, meaning and properties of the actual data rather than being the data itself.
   - In a database it is stored in the data dictionary or system catalog, which records every table, its columns and their data types, the keys, the indexes, the views, the users and their privileges. The DBMS consults it whenever a query is parsed and optimised.
   - Example: if a stored value is 'Rahim', the metadata is that the column is called `emp_name`, is of type VARCHAR(50), belongs to the Employee table and cannot be NULL.
   - Outside databases: the EXIF information of a photograph, giving the camera, date and GPS location; a file's creation date, size and owner; and the ID3 tags of an MP3 file.
   - Types: descriptive, structural and administrative metadata.
   - Its importance: it makes a database self describing, allows the optimiser to plan queries, and is the basis of data governance and lineage in a data warehouse.
8. **(খ) Centralized System ও Client Server System সম্পর্কে সচিত্র বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 612 (ET: N/A)]*


   Answer:

   Centralized system:
   - All the data, the processing and the control reside on a single central computer, and users connect to it through terminals that do little or no processing of their own.
   - Characteristics: one point of control and one copy of the data; simple administration, backup and security; but that single machine is a single point of failure and a bottleneck, and every user's response time depends on its load.
   - Examples: the classic mainframe with dumb terminals, and a single server holding an entire organisation's data.

   ```mermaid
   graph TD
       T1["Terminal 1"] --> S["Central Computer: data, processing and control"]
       T2["Terminal 2"] --> S
       T3["Terminal 3"] --> S
   ```

   Client server system:
   - The work is divided between two kinds of machine. The client provides the user interface and performs some processing, and the server holds the data and provides services on request. They communicate over a network using a defined protocol.
   - Characteristics: the processing load is shared, so the server is relieved; clients can be added without redesigning the system; the server can be made redundant for availability; but the network becomes a dependency and the design is more complex.
   - Architectures: two tier, in which the client talks directly to the database server; and three tier, in which a middle application server sits between them, which is the standard for web applications.
   - Examples: a bank's branch terminals connecting to a core banking server, a web browser connecting to a web server, and any application using a database server.

   ```mermaid
   graph TD
       C1["Client 1: user interface"] --> N["Network"]
       C2["Client 2: user interface"] --> N
       C3["Client 3: user interface"] --> N
       N --> A["Application Server: business logic"]
       A --> D["Database Server: data storage"]
   ```

   Comparison:

   | Point | Centralized | Client server |
   |---|---|---|
   | Processing | Entirely on the central machine | Shared between client and server |
   | Data location | One place | Usually on the server, sometimes distributed |
   | Scalability | Poor; only by buying a larger machine | Good; clients and servers can be added |
   | Failure | The central machine is a single point of failure | The server can be made redundant; a client failure affects one user |
   | Network dependence | Minimal | Complete |
   | Cost | High for one large machine | Lower, using ordinary machines |
   | Management | Simple, one place | More complex, many components |
9. **(ক) একজন ডাটাবেস এডমিন এর কাজ কী? কিছু ডাটাবেস সিস্টেম অ্যাপ্লিকেশনের নাম লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 625 (ET: N/A)]*


   Answer:

   Duties of a Database Administrator:
   - Installing, configuring and upgrading the database software, and applying patches.
   - Designing and creating the database: schemas, tables, indexes, views, constraints and storage structures, working with the designers.
   - Managing users and security: creating accounts, granting and revoking privileges, defining roles, and ensuring that each user sees only what they are entitled to see.
   - Backup and recovery: designing the backup strategy, verifying that backups actually restore, and recovering the database after a failure within the agreed recovery point and recovery time objectives.
   - Performance tuning and monitoring: analysing slow queries, creating and maintaining indexes, examining execution plans, managing memory and storage, and capacity planning.
   - Ensuring data integrity and consistency through constraints and regular checks.
   - Managing concurrency, that is transactions, locking and deadlock resolution.
   - Storage management: allocating space, archiving old data, and managing growth.
   - Maintaining the data dictionary and the documentation of the schema.
   - Migrating data between systems, and importing and exporting data.
   - Enforcing compliance and audit requirements, including the retention of audit trails.
   - Disaster recovery planning, replication and high availability configuration, and periodic drills.
   - Supporting developers with query optimisation and schema advice.

   Names of some database system applications:
   - Banking: core banking systems, ATM and card transaction processing, loan and deposit management.
   - Airline and railway reservation systems.
   - University systems: admission, registration, results and library management.
   - Hospital management: patient records, appointments, pharmacy and billing.
   - E-commerce: product catalogue, orders, payments and inventory.
   - Telecommunications: subscriber records, billing and call detail records.
   - Human resources and payroll systems.
   - Government: national identity, land records, taxation and passport systems.
   - Retail: point of sale, stock control and supply chain.
   - Social media, search engines and content management systems.
10. **(খ) ডাটাবেস ব্যবস্থাপনা সিস্টেমের তিন স্তরবিশিষ্ট আর্কিটেকচার ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 626 (ET: N/A)]*


   Answer:

   The ANSI/SPARC three level architecture separates the way data is stored from the way it is seen.

   - External level, also called the view level: what each user or application sees. Different users have different views of the same database, each showing only the tables, rows and columns relevant to them and hiding everything else. There are many external schemas.
   - Conceptual level, also called the logical level: the complete logical structure of the whole database, that is all the entities, attributes, relationships and constraints, without any reference to how it is stored. There is exactly one conceptual schema, and it is what the database designer produces.
   - Internal level, also called the physical level: how the data is actually stored on disk, that is the file organisation, the indexes, the compression and the placement of records. There is exactly one internal schema.

   ```mermaid
   graph TD
       A["External level: User view 1"] --> D["Conceptual level: logical structure of the whole database"]
       B["External level: User view 2"] --> D
       C["External level: User view 3"] --> D
       D --> E["Internal level: physical storage, files and indexes"]
   ```

   Why the separation matters, that is data independence:
   - Logical data independence: the conceptual schema can be changed, for example by adding a column or splitting a table, without altering the external views or the application programs. This is the harder of the two to achieve in practice.
   - Physical data independence: the internal schema can be changed, for example by adding an index, reorganising the files or moving to different storage, without altering the conceptual schema or any application. This is achieved routinely.
   - The DBMS maintains the mappings between the levels and translates every request downward and every result upward.
11. **(ক) সাধারণ ফাইলভিত্তিক সিস্টেমের চেয়ে DBMS এর সুবিধা কী কী?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 627 (ET: N/A)]*


   Answer: Advantages of a DBMS over a conventional file based system:

   - Control of redundancy: in a file system the same data is repeated in many files; a database stores it once, which saves space and removes the chance of the copies disagreeing.
   - Consistency and integrity: constraints such as primary keys, foreign keys, NOT NULL and CHECK are enforced by the DBMS itself, so invalid data cannot be stored whatever the application does.
   - Data sharing and concurrency: many users may read and write at the same time, and the DBMS uses locking and transactions to keep the result correct.
   - Security: users are given privileges on particular tables, columns and operations, and views can hide sensitive data entirely.
   - Backup and recovery: automatic backup, transaction logging and recovery after a crash, which a file system leaves entirely to the programmer.
   - Data independence: the physical storage can be changed without altering the applications, and the logical structure can be changed without altering the users' views.
   - Efficient query processing: a declarative language, SQL, together with an optimiser and indexes, so the programmer states what is required rather than how to obtain it.
   - Reduced application development time, since searching, sorting, joining and validation are provided rather than written by hand.

   The specific defects of a file based system that a DBMS removes:
   - Data redundancy and inconsistency, since each application keeps its own file and the same fact is stored many times.
   - Difficulty of access, because every new question requires a new program to be written.
   - Data isolation, since the data is scattered across files of different formats.
   - Integrity problems, because the rules are coded inside each application rather than enforced centrally, so one careless program can corrupt the data.
   - Atomicity problems, since a failure part way through an update leaves the files inconsistent with no means of recovery.
   - Concurrent access anomalies, because file systems provide no locking, so simultaneous updates overwrite one another.
   - Security problems, since file level permissions cannot express "this user may see these columns of these rows".

   Disadvantages, which a complete answer should mention:
   - High initial cost of the software, the hardware and the skilled staff.
   - Complexity, so that a database administrator is required.
   - Performance overhead for a very simple single user application, where a file would be faster.
   - Centralisation makes the database a single point of failure and a high value target, so backup and security become critical.
12. **What is Database administrator role?** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 662 (ET: N/A)]*


   Answer: A Database Administrator is the person responsible for the design, implementation, security, performance and continued availability of an organisation's databases.

   Roles and responsibilities:
   - Installation, configuration, upgrade and patching of the database software.
   - Database design and implementation: creating schemas, tables, indexes, views and constraints, in cooperation with the designers and developers.
   - Security administration: creating user accounts, granting and revoking privileges, defining roles, enforcing least privilege, and controlling access to sensitive columns through views.
   - Backup and recovery: designing the strategy, scheduling and verifying backups, testing restoration, and recovering the database after a failure within the agreed RPO and RTO.
   - Performance tuning: identifying slow queries, examining execution plans, creating and maintaining indexes, tuning memory and storage parameters, and updating statistics.
   - Monitoring: watching space usage, locks, deadlocks, long running queries, replication lag and error logs, with alerting.
   - Capacity planning and storage management, including archiving and purging old data.
   - Concurrency and transaction management, including deadlock detection and resolution.
   - Maintaining data integrity through constraints and periodic consistency checks.
   - High availability and disaster recovery: replication, clustering, standby databases and rehearsed failover.
   - Data migration, import and export, and supporting application releases.
   - Compliance and audit: retaining audit trails, meeting regulatory requirements such as the Bangladesh Bank ICT guidelines, and supporting internal and external audit.
   - Documentation of the schema, the procedures and the recovery plans.
   - Supporting developers with schema and query advice.

   Types of DBA: system DBA, concerned with the software and the infrastructure; application DBA, concerned with a particular application's schema and queries; and development DBA, working alongside the programmers.
13. **Explain difference between Data Administrator and Database Administrator.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 681 (ET: N/A)]*


   Answer:

   | Point | Data Administrator, DA | Database Administrator, DBA |
   |---|---|---|
   | Focus | The data itself as a corporate resource | The database system that holds it |
   | Level | Managerial and strategic | Technical and operational |
   | Main concern | What data the organisation needs, what it means and who owns it | How that data is stored, secured and made to perform |
   | Responsibilities | Data policy, data standards, naming conventions, the data dictionary at the conceptual level, data ownership and stewardship, data quality, and the conceptual and logical design | Physical design, installation and configuration, security implementation, backup and recovery, performance tuning, storage management, and day to day operation |
   | Design level | Conceptual and logical schema | Internal and physical schema |
   | Technical depth | Understands the business and the data model; less concerned with the particular product | Deep expertise in a specific DBMS product |
   | Tools | Data models, dictionaries, governance frameworks | The DBMS itself, monitoring and backup tools |
   | Reports to | Business or information management | IT operations |
   | Present in | Larger organisations only | Almost every organisation with a database |

   - In summary, the data administrator decides what data the organisation should hold, what it means and who is responsible for it, while the database administrator makes that decision work in a particular database product. In a small organisation the same person performs both roles, which is why the distinction is often blurred in practice.
   - The DA role is the ancestor of what is now generally called data governance and the office of the Chief Data Officer.
14. **Describe the advantages and disadvantages of DBMS-provided and application provided security.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 684 (ET: N/A)]*


   Answer: Security may be enforced by the DBMS itself or by the application, and each approach has a distinct set of advantages and weaknesses.

   DBMS provided security:
   - The DBMS authenticates users, grants privileges on tables, columns and operations, and restricts what may be seen through views.

   Advantages:
   - It cannot be bypassed. Whether the user connects through the application, a reporting tool or a command line client, the same rules apply. This is the decisive argument.
   - It is centralised, so a rule is written once and applies to every application that touches the database.
   - It is enforced by tested, mature code rather than by every developer's own implementation.
   - It provides an audit trail at the source of the data.
   - It supports fine grained control through views, row level security and column privileges.
   - Changing a policy requires no change to any application.

   Disadvantages:
   - Its granularity is limited to the database's own model. Rules that depend on the business context, such as "a clerk may approve a transaction only up to a limit that depends on the branch and the time of day", cannot be expressed naturally.
   - Every end user needs a database account, which does not scale to a web application with a million users and conflicts with connection pooling.
   - It is specific to the DBMS product, so migrating to another database means rewriting the security configuration.
   - Error messages returned by the database may be unhelpful or may leak schema information to the user.

   Application provided security:
   - The application authenticates its own users and decides what each may do, connecting to the database through a single privileged account.

   Advantages:
   - Rules of any complexity can be expressed, including those depending on business logic, workflow state, time or the value of the data.
   - It scales to very large numbers of users without a database account for each, and it works with connection pooling.
   - It is portable across database products.
   - It can give clear, user friendly error messages and can integrate with a corporate identity provider through single sign on.

   Disadvantages:
   - It can be bypassed entirely. Anyone who obtains the application's database credentials, or who reaches the database directly, has full access, because the database itself imposes no restriction. This is the fundamental weakness.
   - The application account must hold broad privileges, so a SQL injection flaw yields the whole database.
   - The rules must be implemented consistently in every application and every path, and a single omission creates a hole.
   - It is expensive to develop and to maintain, and it is where most real access control defects are found.

   Conclusion:
   - The two are complementary and should be used together in a defence in depth design. The DBMS enforces the coarse rules that must never be bypassed, such as which account may reach which table at all, and the application enforces the fine grained business rules above them. Relying on either alone is a mistake, and relying on the application alone is the more dangerous of the two.
15. **(a) What is database schema? What are dangling tuple and descriptive attribute?** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 693 (ET: N/A)]*


   Answer:

   Database schema:
   - A schema is the overall logical structure or design of a database: the tables, their columns and data types, the keys, the relationships and the constraints. It is the blueprint of the database and it is defined when the database is created.
   - It is distinguished from the instance, which is the actual data held at a particular moment. The schema changes rarely; the instance changes with every transaction.
   - Levels of schema, following the three level architecture: the external schema, that is each user's view; the conceptual schema, that is the complete logical structure; and the internal schema, that is the physical storage.
   - Example: `Student(student_id INT PRIMARY KEY, name VARCHAR(50) NOT NULL, dept_id INT REFERENCES Department(dept_id))` is a schema definition; the rows actually stored in the table are the instance.

   Dangling tuple:
   - A dangling tuple is a row in one relation that has no matching row in the relation with which it should be associated. In a join it is the row that is lost, and in a foreign key context it is a row referring to a parent that does not exist.
   - It arises when a natural or inner join is performed and one side has no partner. Such rows silently disappear from the result, which is why an outer join is used when they must be retained.
   - It also arises as a referential integrity violation: an Order row whose customer_id does not appear in the Customer table is a dangling tuple, and it should be prevented by a foreign key constraint.
   - Example: joining Employee and Department on `dept_id`, an employee whose `dept_id` is NULL or refers to a deleted department is dangling and vanishes from an inner join. A LEFT JOIN preserves it with NULLs on the department side.
   - Its significance in decomposition: a decomposition is lossless only if no dangling tuples are generated when the parts are rejoined; otherwise information is lost or spurious rows are created.

   Descriptive attribute:
   - A descriptive attribute is an attribute that belongs to a relationship rather than to either of the entities it connects. It describes the association itself.
   - Example: in the relationship `Student ENROLLS_IN Course`, the attributes `enrollment_date` and `grade` belong to neither Student nor Course; a grade is meaningless without both. They are descriptive attributes of the relationship.
   - Another example: in `Employee WORKS_ON Project`, the attribute `hours_worked` is descriptive of the relationship.
   - Conversion to tables: when a many to many relationship carrying descriptive attributes is converted into a relational schema, it becomes a separate table whose primary key is the combination of the two foreign keys, and the descriptive attributes become ordinary columns of that table. For example `Enrollment(student_id, course_id, enrollment_date, grade)`.
   - This is precisely why a many to many relationship cannot be represented without a junction table: there is nowhere else to put the descriptive attributes.
16. **What is data Independence? How many types of data independence?** *[BDCCL Assistant Engineer (Network) 2022 compact it 742 (ET: N/A)]*


   Answer:

   What data independence is:
   - Data independence is the capacity to change the schema at one level of the database system without having to change the schema at the next higher level, and therefore without altering the application programs.
   - It is achieved by the three level ANSI/SPARC architecture, in which the external, conceptual and internal levels are separated and the DBMS maintains the mappings between them. Changing one level only requires the mapping to be adjusted.

   Types of data independence, of which there are two:

   Logical data independence:
   - The ability to change the conceptual schema without changing the external schemas or the application programs.
   - Examples of such changes: adding a new column to a table, adding a new table, splitting one table into two, merging two tables, or changing a constraint.
   - How it works: the external views are redefined against the altered conceptual schema, so that each user continues to see exactly what they saw before.
   - It is the harder of the two to achieve, because the users' views are defined in terms of the conceptual schema, so some changes, such as removing a column that a view exposes, cannot be hidden at all.

   Physical data independence:
   - The ability to change the internal schema without changing the conceptual schema, and therefore without affecting any user or application.
   - Examples of such changes: creating or dropping an index, changing the file organisation from heap to clustered, moving the data to a different disk or storage device, changing the compression, or partitioning a table.
   - How it works: the mapping between the conceptual and the internal level is adjusted, and no query needs to be rewritten because SQL never refers to physical storage.
   - It is easily achieved and is the reason an administrator can add an index to speed up a query without any application change whatever.

   Why it matters:
   - It is the central practical benefit of the database approach over file based systems, in which the physical layout of a file is coded into every program that reads it, so that any change to the file forces every program to be rewritten and recompiled.
   - It allows the database to evolve, be tuned and be migrated over a working life of decades while the applications above it continue to run.
17. **(ii) Database এর Table and View এর মধ্যে পার্থক্য লিখুন। E-R diagram এর প্রয়োজনীয়তা লিখুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 785 (ET: N/A)]*


   Answer:

   Difference between a table and a view:

   | Point | Table | View |
   |---|---|---|
   | Nature | A real object that physically stores data | A virtual object defined by a stored query |
   | Storage | Occupies disk space | Occupies no space beyond its definition |
   | Data | Holds the data itself | Holds no data; the query runs on every reference |
   | Currency | Contains whatever was last written | Always reflects the current contents of the base tables |
   | Creation | `CREATE TABLE` | `CREATE VIEW ... AS SELECT ...` |
   | Update | Always updatable | Updatable only in restricted cases: a single base table, no aggregation, no DISTINCT, no GROUP BY, no join |
   | Indexes | Can be indexed | Cannot be indexed, except a materialised or indexed view |
   | Constraints | Primary key, foreign key, CHECK and so on may be defined | No constraints of its own; it inherits those of the base tables |
   | Purpose | To store data | To simplify queries, to restrict access, and to give logical data independence |
   | Dependency | Independent | Depends on the base tables; dropping a base table breaks the view |

   Necessity of an E-R diagram:
   - It provides a clear, graphical model of the data requirements before any table is created, so that the design can be discussed and corrected while changes are still cheap.
   - It is a communication tool between the designer, the developers and the users, who can understand a diagram of entities and relationships without knowing SQL.
   - It identifies the entities, their attributes and the relationships between them, together with the cardinality and participation constraints, which are precisely the facts needed to produce a correct relational schema.
   - It reveals design errors early, such as a missing entity, a many to many relationship that needs a junction table, or an attribute placed on the wrong entity.
   - It is the basis of normalisation, since a well drawn E-R model already avoids most redundancy.
   - It provides lasting documentation of the database, which is essential when the original designers have left.
   - It maps directly to tables by defined rules: each entity becomes a table, each many to many relationship becomes a junction table, and each one to many relationship becomes a foreign key.
18. **(a) Distinguish between table and view in database management system.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 802 (ET: N/A)]*


   Answer:

   | Point | Table | View |
   |---|---|---|
   | Nature | A real object that physically stores data | A virtual object defined by a stored query |
   | Storage | Occupies disk space | Occupies no space beyond its definition |
   | Data | Holds the data itself | Holds no data; the query runs on every reference |
   | Currency | Contains whatever was last written | Always reflects the current contents of the base tables |
   | Creation | `CREATE TABLE` | `CREATE VIEW ... AS SELECT ...` |
   | Update | Always updatable | Updatable only in restricted cases: a single base table, no aggregation, no DISTINCT, no GROUP BY, no join |
   | Indexes | Can be indexed | Cannot be indexed, except a materialised or indexed view |
   | Constraints | Primary key, foreign key, CHECK and so on may be defined | No constraints of its own; it inherits those of the base tables |
   | Purpose | To store data | To simplify queries, to restrict access, and to give logical data independence |
   | Dependency | Independent | Depends on the base tables; dropping a base table breaks the view |

   Example:

   ```sql
   -- A table stores data
   CREATE TABLE Employee (
       emp_id   INT PRIMARY KEY,
       emp_name VARCHAR(50),
       dept_id  INT,
       salary   DECIMAL(10,2)
   );

   -- A view stores only a query
   CREATE VIEW HighPaidEmployees AS
   SELECT emp_id, emp_name, dept_id
   FROM   Employee
   WHERE  salary > 50000;
   ```

   - The view holds no data. Every time `SELECT * FROM HighPaidEmployees` is executed, the underlying query runs against the Employee table, so the result always reflects the current data.
   - Note that the view above deliberately omits the salary column, which illustrates the principal use of views: a user may be granted access to the view and denied access to the table, so that they can see who the senior staff are without seeing what anyone earns.

   Uses of a view: simplifying a complex join into a single name; restricting access to particular rows and columns for security; providing logical data independence, so the base tables can change while the view's definition preserves the interface; and expressing a business rule once instead of repeating it in many queries.
19. **Database এর সর্বনিম্ন Unit কোনটি?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 944 (ET: N/A)]*


   Answer: The smallest unit of a database is a field, also called an attribute or a column value, and below that in pure storage terms the smallest unit is a bit or a character.

   The hierarchy, from smallest to largest:
   - Bit: a single binary digit, 0 or 1. This is the smallest unit of storage in absolute terms.
   - Byte or character: eight bits, holding one character such as 'A'.
   - Field, or attribute: a single item of data describing one property of one entity, for example the name 'Rahim' or the salary 45000. This is the smallest meaningful unit of data in a database, and it is normally the expected answer.
   - Record, or row, or tuple: a collection of related fields describing one entity, for example all the details of one employee.
   - Table, or relation, or file: a collection of related records of the same type.
   - Database: a collection of related tables.

   - So the answer depends on what is meant by "unit". If the question means the smallest unit of storage, it is the bit; if it means the smallest unit of meaningful data, which is what such a question normally intends, it is the field.
20. **DBMS বলতে কী বোঝানো হয়? DBMS শ্রেণিভিন্যাস বর্ণনা করুন।** *[40th BCS 2020 compact it 971-972 (ET: BPSC)]*


   Answer:

   What a DBMS is:
   - A Database Management System is software that enables users to define, create, store, retrieve, update and manage data in a database, and that controls access to it. It stands between the physical data and the users, so no application needs to know how the data is actually stored.
   - Its principal functions: data definition, data manipulation, transaction management, concurrency control, security and authorisation, backup and recovery, integrity enforcement, and maintenance of the data dictionary.
   - Examples: Oracle, MySQL, PostgreSQL, Microsoft SQL Server, MongoDB.

   Classification of DBMS:

   By data model:
   - Hierarchical DBMS: data organised as a tree, with each child having one parent. Fast for one to many relationships but rigid, and it cannot represent many to many. Example: IBM IMS.
   - Network DBMS: data organised as a graph, so a record may have several parents. More flexible than hierarchical but complex to navigate. Example: IDMS, following the CODASYL model.
   - Relational DBMS: data organised as tables of rows and columns, related by keys and queried with SQL. This is the dominant model. Examples: Oracle, MySQL, PostgreSQL, SQL Server.
   - Object oriented DBMS: data stored as objects with attributes and methods, matching object oriented programming languages directly. Example: ObjectDB, db4o.
   - Object relational DBMS: relational with object features added, such as user defined types and inheritance. Examples: PostgreSQL, Oracle.
   - NoSQL DBMS: non-relational, designed for very large volumes and flexible schemas. Four kinds: document stores such as MongoDB, key-value stores such as Redis, column family stores such as Cassandra, and graph databases such as Neo4j.

   By number of users:
   - Single user, such as MS Access on a personal machine, and multi-user, such as Oracle serving an organisation.

   By distribution:
   - Centralised, with the whole database on one machine; distributed, with the data spread across several sites; and cloud based, hosted by a provider.

   By purpose:
   - OLTP, Online Transaction Processing, optimised for many short read and write transactions, as in banking; and OLAP, Online Analytical Processing, that is data warehousing, optimised for complex analytical queries over large volumes.

   By licence: commercial, such as Oracle and SQL Server; and open source, such as MySQL, PostgreSQL and MongoDB.
21. **Define View, Materialized View. Difference between View and Materialized View and Usage of two.** *[RAKUB Assistant Database Administrator 2020 compact it 1012-1013 (ET: E-Zone)]*


   Answer:

   View:
   - A view is a virtual table defined by a stored SELECT statement. It holds no data of its own; the query is executed every time the view is referenced, so the result always reflects the current contents of the base tables.
   - `CREATE VIEW active_customers AS SELECT * FROM Customer WHERE status = 'Active';`

   Materialized view:
   - A materialized view is a view whose result is physically stored on disk, like a table. The query is executed when the view is created or refreshed, and thereafter the stored result is read directly rather than recomputed.
   - It must be refreshed to reflect changes in the base tables, either on demand, on a schedule, or on commit of the underlying transaction.
   - `CREATE MATERIALIZED VIEW monthly_sales AS SELECT region, SUM(amount) FROM Sales GROUP BY region;`

   Difference:

   | Point | View | Materialized View |
   |---|---|---|
   | Storage | Stores only the query definition | Stores the actual result set on disk |
   | Disk space | None | Consumes space proportional to the result |
   | Currency of data | Always current, since it is recomputed on every access | Stale between refreshes |
   | Query speed | Slower; the underlying query runs each time | Much faster; the stored result is simply read |
   | Refresh | Not applicable | Required, on demand, on a schedule or on commit |
   | Indexes | Cannot be indexed | Can be indexed, which makes it faster still |
   | Cost of maintenance | None | Refresh consumes time and resources |
   | Effect on write performance | None | On commit refresh slows down every write to the base tables |
   | Availability | Supported by every DBMS | Oracle, PostgreSQL and SQL Server, where it is called an indexed view; not supported by MySQL |

   Usage of each:
   - View: use it when the data must always be current and the underlying query is not expensive. Its purposes are to simplify a complex join into a single name, to restrict access to particular rows and columns for security, to give logical data independence, and to express a business rule once rather than repeating it.
   - Materialized view: use it when the query is expensive and the data need not be perfectly current. Its purposes are to pre-compute aggregations for reporting and data warehousing, to speed up dashboards, to replicate data to a remote site, and to reduce the load of repeated identical heavy queries. The trade-off is always storage and staleness against speed.
   - Typical decision: a bank's operational screen showing a customer's current balance must use a view, because a stale balance is unacceptable; the management report showing last month's regional totals should use a materialized view refreshed nightly, because recomputing it on every access would be wasteful.
22. **What are the roles of Database Engineer?** *[RAKUB Assistant Database Administrator 2020 compact it 1014 (ET: E-Zone)]*


   Answer: A Database Engineer designs, builds and maintains the data infrastructure of an organisation. The role overlaps with that of the Database Administrator but leans towards development and architecture rather than day to day operation.

   Roles and responsibilities:
   - Database design: producing the conceptual, logical and physical models, that is the entity relationship model, normalisation to an appropriate form, and the choice of tables, keys, data types and indexes.
   - Selecting the technology: deciding between relational and NoSQL, and between particular products, according to the workload, the volume, the consistency requirements and the cost.
   - Building the schema and the objects: tables, constraints, indexes, views, stored procedures, functions and triggers.
   - Writing and optimising queries: examining execution plans, rewriting inefficient SQL, and designing indexes to support the actual query patterns.
   - Performance engineering: partitioning large tables, denormalising deliberately where read performance demands it, caching, and capacity planning for growth.
   - Building data pipelines: ETL and ELT processes to move data between operational systems, warehouses and analytical platforms.
   - Ensuring data quality and integrity through constraints, validation rules and reconciliation processes.
   - Implementing security: encryption at rest and in transit, access control, masking of sensitive data in test environments, and audit logging.
   - Backup, recovery and high availability: designing replication, clustering and standby configurations, and testing the recovery procedures rather than assuming them.
   - Schema migration and version control: managing changes to the database structure alongside application releases, with scripts that can be applied and rolled back.
   - Automation: scripting routine maintenance, monitoring and deployment, and integrating the database into the continuous delivery pipeline.
   - Collaborating with application developers and data analysts, and advising them on data access patterns.
   - Documentation of the data model, the dictionary and the operational procedures.

   Distinction from related roles:
   - The Database Administrator concentrates on operating and protecting the running database; the Database Engineer concentrates on designing and building it. The Data Engineer, a further specialisation, concentrates on pipelines and large scale analytical platforms.
   - In smaller organisations one person performs all three roles.

## ER Diagram & Database Design (21)

1. BSCPL regularly publishes multiple job vacancies, where each Job is identified by a unique Job ID and contains information such as Job Title, Starting Salary, Job Description, and other relevant attributes. An Applicant is identified by a unique Applicant ID and has attributes such as Name, Date of Birth, Starting/Joining Date, Contact Information, and other details. An applicant can apply for only one job, while a particular job can receive applications from many applicants. Design the ER diagram for this system, showing the entities, attributes, primary keys, relationship, cardinalities, and participation constraints. [BSCCPL AME 21-08-2026 (BUET)]


   Answer:

   Entities and attributes:
   - Job: Job_ID as the primary key, Job_Title, Starting_Salary, Job_Description, Posting_Date, Closing_Date.
   - Applicant: Applicant_ID as the primary key, Name as a composite attribute of First_Name and Last_Name, Date_of_Birth, Age as a derived attribute computed from the date of birth, Joining_Date, Contact_Information as a composite attribute of Phone, Email and Address, and Qualification.

   Relationship and constraints:
   - The relationship is APPLIES_FOR between Applicant and Job.
   - Cardinality: an applicant may apply for only one job, and one job may receive applications from many applicants. This is therefore many to one from Applicant to Job, or equivalently one to many from Job to Applicant.
   - Participation: Applicant has total participation, shown by a double line, since an applicant exists only in order to apply for a job. Job has partial participation, since a job may be advertised and receive no application at all.
   - The relationship may carry a descriptive attribute, Application_Date.

   E-R diagram:

   ```
        Job_ID          Job_Title      Starting_Salary   Job_Description
           |                |                |                 |
           +----------------+-------+--------+-----------------+
                                    |
                              +-----------+
                              |    JOB    |
                              +-----------+
                                    |
                                    | 1
                              <APPLIES_FOR>-------- Application_Date
                                    |
                                    | M   (double line: total participation of Applicant)
                              +-------------+
                              |  APPLICANT  |
                              +-------------+
                                    |
        +---------------+-----------+-----------+----------------+
        |               |           |           |                |
   Applicant_ID       Name    Date_of_Birth  Joining_Date   Contact_Info
     (key)         (composite)                              (composite)
                   /      \                                  /   |   \
             First_Name  Last_Name                      Phone  Email  Address
   ```

   ```mermaid
   erDiagram
       JOB ||--o{ APPLICANT : "receives applications from"
       JOB {
           int Job_ID PK
           string Job_Title
           decimal Starting_Salary
           string Job_Description
       }
       APPLICANT {
           int Applicant_ID PK
           string First_Name
           string Last_Name
           date Date_of_Birth
           date Joining_Date
           string Contact_Info
           int Job_ID FK
       }
   ```

   Conversion to relational tables:
   - Since the relationship is one to many, no junction table is required. The foreign key is placed on the "many" side, that is in Applicant.

   ```sql
   CREATE TABLE Job (
       Job_ID          INT PRIMARY KEY,
       Job_Title       VARCHAR(100) NOT NULL,
       Starting_Salary DECIMAL(10,2),
       Job_Description TEXT
   );

   CREATE TABLE Applicant (
       Applicant_ID     INT PRIMARY KEY,
       First_Name       VARCHAR(50) NOT NULL,
       Last_Name        VARCHAR(50),
       Date_of_Birth    DATE,
       Joining_Date     DATE,
       Phone            VARCHAR(20),
       Email            VARCHAR(100),
       Address          VARCHAR(200),
       Application_Date DATE,
       Job_ID           INT NOT NULL,
       FOREIGN KEY (Job_ID) REFERENCES Job(Job_ID)
   );
   ```

   - `Job_ID NOT NULL` in Applicant enforces the total participation constraint: an applicant must be associated with a job.
   - Age is not stored, since it is a derived attribute; it is computed from Date_of_Birth when required.
   - Note that the constraint "an applicant can apply for only one job" is unusual in practice; if it were relaxed to many to many, a junction table `Application(Applicant_ID, Job_ID, Application_Date)` would be required instead.
2. **(a) Design an ER diagram for a library management systems where-** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1349 (ET: N/A)]*
   * **(i) A library has multiple books.**
   * **(ii) Each book can have multiple copies.**


   Answer:

   Entities and attributes for a library management system:
   - Library: Library_ID as primary key, Library_Name, Address, Phone.
   - Book: ISBN as primary key, Title, Author, Publisher, Edition, Subject, Price.
   - Book_Copy, a weak entity: Copy_ID as a partial key together with the ISBN of the owning book, Shelf_Location, Status which is Available, Issued or Damaged, Acquisition_Date.
   - Member: Member_ID as primary key, Name, Address, Phone, Membership_Type, Join_Date.
   - Issue, the relationship between Member and Book_Copy, carrying Issue_Date, Due_Date, Return_Date and Fine.

   Relationships and cardinalities:
   - Library HAS Book: one to many, since a library holds many books.
   - Book HAS Book_Copy: one to many, since each book may exist in several physical copies. Book_Copy is a weak entity, because a copy has no identity independent of the book it is a copy of, so it is drawn with a double rectangle and its identifying relationship with a double diamond.
   - Member BORROWS Book_Copy: many to many over time, since a member borrows many copies and a copy is borrowed by many members at different times. It carries the descriptive attributes of the loan.

   ```mermaid
   erDiagram
       LIBRARY ||--o{ BOOK : "holds"
       BOOK ||--o{ BOOK_COPY : "has copies"
       MEMBER ||--o{ ISSUE : "borrows"
       BOOK_COPY ||--o{ ISSUE : "is issued in"
       LIBRARY {
           int Library_ID PK
           string Library_Name
           string Address
       }
       BOOK {
           string ISBN PK
           string Title
           string Author
           string Publisher
           int Library_ID FK
       }
       BOOK_COPY {
           int Copy_ID PK
           string ISBN FK
           string Shelf_Location
           string Status
       }
       MEMBER {
           int Member_ID PK
           string Name
           string Phone
           string Membership_Type
       }
       ISSUE {
           int Issue_ID PK
           int Copy_ID FK
           int Member_ID FK
           date Issue_Date
           date Due_Date
           date Return_Date
           decimal Fine
       }
   ```

   Conversion to tables:

   ```sql
   CREATE TABLE Library (
       Library_ID   INT PRIMARY KEY,
       Library_Name VARCHAR(100),
       Address      VARCHAR(200)
   );

   CREATE TABLE Book (
       ISBN       VARCHAR(20) PRIMARY KEY,
       Title      VARCHAR(200) NOT NULL,
       Author     VARCHAR(100),
       Publisher  VARCHAR(100),
       Library_ID INT REFERENCES Library(Library_ID)
   );

   CREATE TABLE Book_Copy (
       Copy_ID        INT,
       ISBN           VARCHAR(20),
       Shelf_Location VARCHAR(50),
       Status         VARCHAR(20) DEFAULT 'Available',
       PRIMARY KEY (Copy_ID, ISBN),
       FOREIGN KEY (ISBN) REFERENCES Book(ISBN)
   );

   CREATE TABLE Member (
       Member_ID INT PRIMARY KEY,
       Name      VARCHAR(100) NOT NULL,
       Phone     VARCHAR(20)
   );

   CREATE TABLE Issue (
       Issue_ID    INT PRIMARY KEY,
       Copy_ID     INT,
       ISBN        VARCHAR(20),
       Member_ID   INT REFERENCES Member(Member_ID),
       Issue_Date  DATE NOT NULL,
       Due_Date    DATE,
       Return_Date DATE,
       Fine        DECIMAL(8,2) DEFAULT 0,
       FOREIGN KEY (Copy_ID, ISBN) REFERENCES Book_Copy(Copy_ID, ISBN)
   );
   ```

   - The essential design point is the separation of Book from Book_Copy. The Book table holds the bibliographic information once, and the Book_Copy table holds one row per physical volume. Without this separation, the title, author and publisher would be repeated for every copy, which is exactly the redundancy that normalisation exists to remove.
3. **(খ) নিচের ডেটাবেস অনুযায়ী ER ডায়াগ্রাম তৈরি করুন :** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 415 (ET: N/A)]*
   * **Worker** (Worker ID, Worker Name, Hour Rate, Skill Type)
   * **Assignment** (Worker ID, Building ID, Start Date, Num Days)
   * **Building** (Building ID, Address, Building Type)


   Answer:

   Entities and attributes, read from the given relations:
   - Worker: Worker_ID as primary key, Worker_Name, Hour_Rate, Skill_Type.
   - Building: Building_ID as primary key, Address, Building_Type.
   - Assignment: this is not an entity in its own right but the junction table implementing the many to many relationship between Worker and Building. Its key is the combination (Worker_ID, Building_ID), and it carries the descriptive attributes Start_Date and Num_Days.

   Relationship:
   - Worker IS_ASSIGNED_TO Building, many to many: one worker may be assigned to many buildings, and one building may have many workers assigned to it.
   - Start_Date and Num_Days are descriptive attributes of the relationship, not of either entity: a start date is meaningless without knowing both which worker and which building it refers to. This is exactly why the relationship must become its own table.

   E-R diagram:

   ```
    Worker_ID   Worker_Name   Hour_Rate   Skill_Type
        |            |            |           |
        +------------+-----+------+-----------+
                           |
                     +-----------+
                     |  WORKER   |
                     +-----------+
                           |
                           | M
                    <ASSIGNMENT>------- Start_Date
                           |      \---- Num_Days
                           | N
                     +-----------+
                     | BUILDING  |
                     +-----------+
                           |
              +------------+------------+
              |            |            |
        Building_ID     Address    Building_Type
   ```

   ```mermaid
   erDiagram
       WORKER ||--o{ ASSIGNMENT : "is assigned"
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
           int Worker_ID PK
           int Building_ID PK
           date Start_Date
           int Num_Days
       }
   ```

   Relational schema:

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
       PRIMARY KEY (Worker_ID, Building_ID),
       FOREIGN KEY (Worker_ID)   REFERENCES Worker(Worker_ID),
       FOREIGN KEY (Building_ID) REFERENCES Building(Building_ID)
   );
   ```

   - If a worker could be assigned to the same building more than once at different times, the composite key would have to include Start_Date as well, giving `PRIMARY KEY (Worker_ID, Building_ID, Start_Date)`.
4. **Consider the Schema employee(id, name, salary), equipment(id, name, price), hire(employee_id, equipment_id)**
   **(i) Draw the ERD digram for the relation**
   **(ii) Write the SQL query to show the name of employee who borrow the maximum equipment?** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 462 (ET: BUET)]*


   Answer:

   (i) E-R diagram for the schema `employee(id, name, salary)`, `equipment(id, name, price)`, `hire(employee_id, equipment_id)`:

   - Entities: Employee with id as primary key, name and salary; Equipment with id as primary key, name and price.
   - Relationship: HIRE, many to many, since one employee may hire many pieces of equipment and one piece of equipment may be hired by many employees at different times.
   - The `hire` relation is the junction table implementing that relationship, with the composite primary key (employee_id, equipment_id).

   ```
      id      name     salary                    id      name      price
       |        |         |                       |        |         |
       +--------+---------+                       +--------+---------+
                |                                          |
          +-----------+          M       N          +-------------+
          | EMPLOYEE  |------< HIRE >--------------| EQUIPMENT   |
          +-----------+                            +-------------+
   ```

   ```mermaid
   erDiagram
       EMPLOYEE ||--o{ HIRE : "hires"
       EQUIPMENT ||--o{ HIRE : "is hired in"
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
           int employee_id PK
           int equipment_id PK
       }
   ```

   - A many to many relationship cannot be represented by a foreign key in either entity table; it requires the separate junction table, which is what `hire` is.

   (ii) SQL query for the employee who borrowed the maximum amount of equipment:

   ```sql
   SELECT e.name, COUNT(*) AS equipment_count
   FROM   employee e
   JOIN   hire h ON e.id = h.employee_id
   GROUP  BY e.id, e.name
   HAVING COUNT(*) = (
              SELECT MAX(cnt)
              FROM   (SELECT COUNT(*) AS cnt
                      FROM   hire
                      GROUP  BY employee_id) AS t
          );
   ```

   - The inner derived table counts the equipment hired by each employee, and `MAX(cnt)` finds the largest of those counts. The outer query returns every employee whose count equals that maximum, so a tie returns all the tied employees.

   Simpler alternative, which returns only one employee even in the event of a tie:

   ```sql
   SELECT e.name, COUNT(*) AS equipment_count
   FROM   employee e
   JOIN   hire h ON e.id = h.employee_id
   GROUP  BY e.id, e.name
   ORDER  BY equipment_count DESC
   LIMIT  1;
   ```

   - The first form should be preferred in an examination, since it handles ties correctly and uses only standard SQL.
5. **Develop an entity relationship diagram that describes data objects, relationships and attributes of the following system: -A web based order processing system for a computer store.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 639 (ET: N/A)]*


   Answer: The system is a web based order processing system for a computer store.

   Entities and attributes:
   - Customer: Customer_ID as primary key, Name, Email, Phone, Address, Registration_Date.
   - Product: Product_ID as primary key, Product_Name, Category, Description, Unit_Price, Stock_Quantity.
   - Order: Order_ID as primary key, Order_Date, Order_Status, Total_Amount, Shipping_Address.
   - Order_Item: the junction entity between Order and Product, with the composite key (Order_ID, Product_ID) and the descriptive attributes Quantity, Unit_Price at the time of sale and Subtotal.
   - Payment: Payment_ID as primary key, Payment_Date, Amount, Payment_Method, Payment_Status, Transaction_Reference.
   - Shipment: Shipment_ID as primary key, Dispatch_Date, Delivery_Date, Courier, Tracking_Number, Status.
   - Category and Supplier may be added if the model is to be fuller.

   Relationships and cardinalities:
   - Customer PLACES Order: one to many. A customer may place many orders; each order belongs to exactly one customer, which is total participation on the Order side.
   - Order CONTAINS Product: many to many, resolved by the Order_Item junction entity. An order contains many products and a product appears in many orders.
   - Order HAS Payment: one to one in the simple case, or one to many if part payments are allowed.
   - Order GENERATES Shipment: one to one, or one to many if an order may be dispatched in several consignments.

   ```mermaid
   erDiagram
       CUSTOMER ||--o{ ORDERS : "places"
       ORDERS ||--|{ ORDER_ITEM : "contains"
       PRODUCT ||--o{ ORDER_ITEM : "appears in"
       ORDERS ||--|| PAYMENT : "is paid by"
       ORDERS ||--o| SHIPMENT : "is dispatched as"
       CUSTOMER {
           int Customer_ID PK
           string Name
           string Email
           string Phone
           string Address
       }
       PRODUCT {
           int Product_ID PK
           string Product_Name
           string Category
           decimal Unit_Price
           int Stock_Quantity
       }
       ORDERS {
           int Order_ID PK
           int Customer_ID FK
           date Order_Date
           string Order_Status
           decimal Total_Amount
       }
       ORDER_ITEM {
           int Order_ID PK
           int Product_ID PK
           int Quantity
           decimal Unit_Price
           decimal Subtotal
       }
       PAYMENT {
           int Payment_ID PK
           int Order_ID FK
           date Payment_Date
           decimal Amount
           string Payment_Method
       }
       SHIPMENT {
           int Shipment_ID PK
           int Order_ID FK
           date Dispatch_Date
           string Tracking_Number
       }
   ```

   Two design points worth stating:
   - `Unit_Price` appears both in Product and in Order_Item. This is not a normalisation error but a deliberate decision: the price in Product is the current price, whereas the price in Order_Item is the price at the moment of sale, which must not change when the catalogue price is later revised. Historical accuracy requires the duplication.
   - Order_Item exists because the relationship carries descriptive attributes, namely the quantity and the price, which belong to neither Order nor Product alone.
6. **Draw a ER diagram for BPL.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 662 (ET: N/A)]*


   Answer: BPL is taken here as the Bangladesh Premier League, a Twenty20 cricket competition.

   Entities and attributes:
   - Team: Team_ID as primary key, Team_Name, Owner, Home_Ground, Coach_Name, Year_Established.
   - Player: Player_ID as primary key, Player_Name, Date_of_Birth, Nationality, Playing_Role which is Batsman, Bowler, All-rounder or Wicketkeeper, Batting_Style, Bowling_Style, Base_Price.
   - Match: Match_ID as primary key, Match_Date, Venue, Result, Winning_Team_ID, Man_of_the_Match.
   - Stadium: Stadium_ID as primary key, Stadium_Name, City, Capacity.
   - Umpire: Umpire_ID as primary key, Umpire_Name, Nationality.
   - Performance: the junction entity between Player and Match, carrying Runs_Scored, Balls_Faced, Wickets_Taken, Overs_Bowled, Runs_Conceded and Catches.
   - Season: Season_ID as primary key, Year, Start_Date, End_Date.

   Relationships and cardinalities:
   - Team HAS Player: one to many in a given season, since a player belongs to one team at a time and a team has many players. Across seasons it becomes many to many and would require a Contract junction entity.
   - Team PLAYS Match: many to many, since each match involves two teams and each team plays many matches. In practice this is often modelled with two foreign keys in Match, Team1_ID and Team2_ID.
   - Match HELD_AT Stadium: many to one, since many matches are played at one stadium.
   - Player PERFORMS_IN Match: many to many, resolved by the Performance junction entity, which carries all the statistics of that player in that match.
   - Umpire OFFICIATES Match: many to many, since a match has several umpires and an umpire officiates many matches.

   ```mermaid
   erDiagram
       TEAM ||--o{ PLAYER : "has"
       TEAM ||--o{ MATCH : "plays in"
       STADIUM ||--o{ MATCH : "hosts"
       PLAYER ||--o{ PERFORMANCE : "records"
       MATCH ||--o{ PERFORMANCE : "contains"
       UMPIRE ||--o{ MATCH : "officiates"
       SEASON ||--o{ MATCH : "includes"
       TEAM {
           int Team_ID PK
           string Team_Name
           string Owner
           string Coach_Name
       }
       PLAYER {
           int Player_ID PK
           string Player_Name
           date Date_of_Birth
           string Nationality
           string Playing_Role
           int Team_ID FK
       }
       MATCH {
           int Match_ID PK
           date Match_Date
           int Stadium_ID FK
           int Season_ID FK
           string Result
       }
       STADIUM {
           int Stadium_ID PK
           string Stadium_Name
           string City
           int Capacity
       }
       PERFORMANCE {
           int Player_ID PK
           int Match_ID PK
           int Runs_Scored
           int Wickets_Taken
           int Catches
       }
       UMPIRE {
           int Umpire_ID PK
           string Umpire_Name
           string Nationality
       }
   ```

   - The Performance entity is the important design decision: runs scored and wickets taken belong to neither the player alone nor the match alone, but to the combination of the two, so they are descriptive attributes of a many to many relationship and must be held in their own table.
7. **How can you define the ER model in DBMS?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*


   Answer: The Entity Relationship model, proposed by Peter Chen in 1976, is a high level conceptual data model that describes the data requirements of a system in terms of entities, the attributes that describe them and the relationships between them, independently of any particular DBMS.

   Components of an E-R model:
   - Entity: a real world object or concept about which data is stored, drawn as a rectangle. A strong entity has its own key; a weak entity, drawn as a double rectangle, depends on another entity for its identity.
   - Attribute: a property of an entity, drawn as an ellipse. Types: simple and composite; single valued and multivalued, drawn as a double ellipse; derived, drawn as a dashed ellipse; and the key attribute, whose name is underlined.
   - Relationship: an association between entities, drawn as a diamond. A relationship may itself carry descriptive attributes.
   - Cardinality: one to one, one to many, many to one, or many to many, written on the connecting lines.
   - Participation: total participation, shown by a double line, meaning every instance of the entity must take part; and partial participation, shown by a single line.

   Example:

   ```
       Student_ID     Name        Course_ID     Course_Name
           |            |             |              |
           +-----+------+             +------+-------+
                 |                           |
           +-----------+   M         N  +----------+
           |  STUDENT  |-----< ENROLLS >-| COURSE  |
           +-----------+                 +----------+
                              |
                          Grade, Enrollment_Date
                       (descriptive attributes)
   ```

   Extended E-R features:
   - Specialisation and generalisation, that is the IS-A relationship, for example Employee generalising Manager and Engineer.
   - Aggregation, treating a whole relationship as a single entity so that another relationship can be defined on it.
   - Constraints on specialisation: disjoint or overlapping, and total or partial.

   Why the model is used:
   - It captures the data requirements before any table is created, so errors are found while they are still cheap to correct.
   - It is understandable by users and managers who do not know SQL, so it serves as a communication tool.
   - It maps mechanically to a relational schema by defined rules, which is why it is the standard first step of database design.
   - It documents the design permanently.

   Rules for converting an E-R diagram into tables:
   - Each strong entity becomes a table, with its key attribute as the primary key.
   - Each weak entity becomes a table whose primary key is the combination of its own partial key and the primary key of the owning entity, which is also a foreign key.
   - A one to one relationship becomes a foreign key placed in either table, preferably in the one with total participation.
   - A one to many relationship becomes a foreign key placed in the table on the "many" side, referring to the "one" side. No extra table is needed.
   - A many to many relationship becomes a separate junction table, whose primary key is the combination of the two foreign keys, and which also holds any descriptive attributes of the relationship.
   - A multivalued attribute becomes a separate table containing the entity's key and the attribute.
   - A composite attribute is flattened into its component columns.
   - A derived attribute is not stored; it is computed when required.
8. **Draw an entity diagram Student database management systemfrom following statement: Student (data); Course (data); Report (data); Registration; Staff (data)** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 759 (ET: N/A)]*


   Answer: A student database management system with the entities Student, Course, Report, Registration and Staff.

   Entities and attributes:
   - Student: Student_ID as primary key, Name, Date_of_Birth, Address, Phone, Email, Admission_Date, Programme.
   - Course: Course_ID as primary key, Course_Name, Credit_Hours, Semester, Department.
   - Staff: Staff_ID as primary key, Name, Designation, Department, Phone, Email.
   - Registration: the junction entity between Student and Course, with the composite key (Student_ID, Course_ID, Semester) and the descriptive attributes Registration_Date and Status.
   - Report: Report_ID as primary key, Marks, Grade, Grade_Point, Exam_Date, together with the Student_ID and Course_ID to which it refers.

   Relationships and cardinalities:
   - Student REGISTERS_FOR Course: many to many, since a student registers for many courses and a course is taken by many students. It is resolved by the Registration entity.
   - Staff TEACHES Course: one to many, since one member of staff teaches several courses; or many to many if a course may be shared between teachers.
   - Student RECEIVES Report: one to many, since a student receives one report per course per semester.
   - Course GENERATES Report: one to many.

   ```mermaid
   erDiagram
       STUDENT ||--o{ REGISTRATION : "registers"
       COURSE ||--o{ REGISTRATION : "is registered in"
       STAFF ||--o{ COURSE : "teaches"
       STUDENT ||--o{ REPORT : "receives"
       COURSE ||--o{ REPORT : "generates"
       STUDENT {
           int Student_ID PK
           string Name
           date Date_of_Birth
           string Programme
       }
       COURSE {
           int Course_ID PK
           string Course_Name
           int Credit_Hours
           int Staff_ID FK
       }
       STAFF {
           int Staff_ID PK
           string Name
           string Designation
           string Department
       }
       REGISTRATION {
           int Student_ID PK
           int Course_ID PK
           string Semester PK
           date Registration_Date
       }
       REPORT {
           int Report_ID PK
           int Student_ID FK
           int Course_ID FK
           decimal Marks
           string Grade
       }
   ```

   Relational schema:

   ```sql
   CREATE TABLE Student (
       Student_ID INT PRIMARY KEY,
       Name       VARCHAR(100) NOT NULL,
       Programme  VARCHAR(50)
   );

   CREATE TABLE Staff (
       Staff_ID    INT PRIMARY KEY,
       Name        VARCHAR(100) NOT NULL,
       Designation VARCHAR(50)
   );

   CREATE TABLE Course (
       Course_ID    INT PRIMARY KEY,
       Course_Name  VARCHAR(100) NOT NULL,
       Credit_Hours INT,
       Staff_ID     INT REFERENCES Staff(Staff_ID)
   );

   CREATE TABLE Registration (
       Student_ID        INT REFERENCES Student(Student_ID),
       Course_ID         INT REFERENCES Course(Course_ID),
       Semester          VARCHAR(20),
       Registration_Date DATE,
       PRIMARY KEY (Student_ID, Course_ID, Semester)
   );

   CREATE TABLE Report (
       Report_ID  INT PRIMARY KEY,
       Student_ID INT REFERENCES Student(Student_ID),
       Course_ID  INT REFERENCES Course(Course_ID),
       Marks      DECIMAL(5,2),
       Grade      CHAR(2)
   );
   ```

   - The Registration table exists because the relationship between Student and Course is many to many and carries its own attributes; a foreign key in either entity table could not represent it.
9. **(ক) Entity-Relationship (ER) Diagram কেন ব্যবহার করা হয়? একটি উদাহরণের মাধ্যমে ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 768 (ET: N/A)]*


   Answer:

   Why an E-R diagram is used:
   - To model the data requirements of a system before any table is created, so that design errors are found while correcting them is still cheap. Correcting a design after the database is built and populated is far more expensive.
   - As a communication tool between the designer, the developers and the users. A diagram of boxes and lines can be reviewed by people who do not know SQL, which is how requirements are actually confirmed.
   - To identify the entities, their attributes and the relationships between them, together with cardinality and participation constraints. These are precisely the facts needed to produce a correct relational schema.
   - To reveal design problems early: a missing entity, an attribute placed on the wrong entity, or a many to many relationship that will need a junction table.
   - As the basis of normalisation. A carefully drawn E-R model already avoids most of the redundancy that normalisation exists to remove.
   - As permanent documentation of the database, which is essential once the original designers have left.
   - Because it maps mechanically to tables by defined rules, so the conversion is systematic rather than a matter of judgement.

   Example, a university enrolment system:

   ```
       Student_ID    Name    Department            Course_ID    Course_Name   Credit
           |          |          |                     |             |          |
           +----+-----+----------+                     +------+------+----------+
                |                                             |
          +-----------+        M              N       +-------------+
          |  STUDENT  |-----------< ENROLLS >---------|   COURSE    |
          +-----------+                               +-------------+
                                    |
                            Enrollment_Date, Grade
                            (descriptive attributes)
   ```

   Reading the diagram:
   - Student and Course are entities, drawn as rectangles, with their attributes in ellipses and their key attributes underlined.
   - ENROLLS is a relationship, drawn as a diamond, and it is many to many: a student enrols in many courses and a course is taken by many students.
   - Enrollment_Date and Grade are descriptive attributes of the relationship. A grade belongs to neither the student nor the course alone; it is meaningful only for the pair, which is why it is attached to the relationship.

   Conversion to tables:

   ```sql
   Student(Student_ID, Name, Department)
   Course(Course_ID, Course_Name, Credit)
   Enrollment(Student_ID, Course_ID, Enrollment_Date, Grade)
   ```

   - The many to many relationship becomes its own table with a composite primary key of the two foreign keys. Without the diagram, a designer might attempt to put a course identifier in Student or a student identifier in Course, both of which are wrong and both of which the diagram makes obviously wrong.
10. **(a) While converting E-R diagram into Tables, how is a Many-to-many relationship set between entities A and B is converted into database tables?** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 804 (ET: N/A)]*


   Answer: A many to many relationship between entities A and B cannot be represented by placing a foreign key in either table, so it is converted into three tables.

   The rule:
   - Entity A becomes a table with its own primary key.
   - Entity B becomes a table with its own primary key.
   - The relationship itself becomes a third table, called a junction, bridge, associative or link table. Its primary key is the combination of the primary keys of A and B, and each of those columns is also a foreign key referring to the corresponding table. Any descriptive attributes of the relationship become ordinary columns of this third table.

   Why a foreign key alone will not work:
   - Suppose a student enrols in many courses and a course has many students. Placing `course_id` in the Student table would allow only one course per student. Placing `student_id` in the Course table would allow only one student per course. Placing a list of identifiers in a single column would violate first normal form. The only correct representation is a separate table with one row per pair.

   Example:

   ```
   E-R model:     STUDENT ----M----< ENROLLS >----N---- COURSE
                                      |
                            enrollment_date, grade
   ```

   ```sql
   CREATE TABLE Student (
       student_id INT PRIMARY KEY,
       name       VARCHAR(100)
   );

   CREATE TABLE Course (
       course_id   INT PRIMARY KEY,
       course_name VARCHAR(100)
   );

   CREATE TABLE Enrollment (
       student_id      INT,
       course_id       INT,
       enrollment_date DATE,
       grade           CHAR(2),
       PRIMARY KEY (student_id, course_id),
       FOREIGN KEY (student_id) REFERENCES Student(student_id),
       FOREIGN KEY (course_id)  REFERENCES Course(course_id)
   );
   ```

   - The composite primary key (student_id, course_id) enforces that a given student can be enrolled in a given course only once. If the same pair may recur, for example if a student may retake a course in a later semester, the semester must be added to the key.
   - `enrollment_date` and `grade` are descriptive attributes of the relationship and have no other place to live; this is the second reason the junction table is required.

   General statement of the rule:
   - For a relationship R between A and B with cardinality m:n, create a table R(A_key, B_key, descriptive attributes) with PRIMARY KEY (A_key, B_key) and a foreign key on each component.
   - For contrast, a 1:n relationship needs no extra table: the foreign key is simply placed on the "many" side. A 1:1 relationship places the foreign key in either table, preferably the one with total participation.
11. **Draw ER diagram for Titas Gas Transmission and Distribution Company limited. Relation between customer and meter. (full question টা পাওয়া যায়নি।)** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 824 (ET: BUET)]*


   Answer: A gas transmission and distribution company such as Titas, modelling in particular the relationship between customer and meter.

   Entities and attributes:
   - Customer: Customer_ID as primary key, Name, Address, Phone, NID, Customer_Type which is Domestic, Commercial or Industrial, Connection_Date, Zone_ID.
   - Meter: Meter_ID as primary key, Meter_Number, Model, Manufacturer, Installation_Date, Meter_Type which is prepaid or postpaid, Status.
   - Reading: Reading_ID as primary key, Meter_ID, Reading_Date, Previous_Reading, Current_Reading, Consumption.
   - Bill: Bill_ID as primary key, Customer_ID, Billing_Month, Units_Consumed, Amount, Due_Date, Status.
   - Payment: Payment_ID as primary key, Bill_ID, Payment_Date, Amount_Paid, Payment_Method.
   - Zone or Office: Zone_ID as primary key, Zone_Name, Area, Office_Address.
   - Complaint: Complaint_ID as primary key, Customer_ID, Complaint_Date, Type, Description, Status.

   Relationships and cardinalities:
   - Customer HAS Meter: one to one in the usual case, since each customer has exactly one meter and each meter serves exactly one customer. Both sides have total participation, since a connection cannot exist without a meter and a meter is not installed except for a customer. If a large industrial customer may have several meters, the relationship becomes one to many.
   - Meter RECORDS Reading: one to many, since a meter produces a reading every billing period.
   - Customer RECEIVES Bill: one to many, one bill per month.
   - Bill HAS Payment: one to many if part payment is allowed, otherwise one to one.
   - Zone SERVES Customer: one to many.

   ```mermaid
   erDiagram
       ZONE ||--o{ CUSTOMER : "serves"
       CUSTOMER ||--|| METER : "has"
       METER ||--o{ READING : "records"
       CUSTOMER ||--o{ BILL : "receives"
       BILL ||--o{ PAYMENT : "is settled by"
       CUSTOMER ||--o{ COMPLAINT : "lodges"
       CUSTOMER {
           int Customer_ID PK
           string Name
           string Address
           string Customer_Type
           int Zone_ID FK
       }
       METER {
           int Meter_ID PK
           string Meter_Number
           string Model
           string Manufacturer
           date Installation_Date
           int Customer_ID FK
       }
       READING {
           int Reading_ID PK
           int Meter_ID FK
           date Reading_Date
           decimal Current_Reading
           decimal Consumption
       }
       BILL {
           int Bill_ID PK
           int Customer_ID FK
           string Billing_Month
           decimal Amount
           date Due_Date
       }
       PAYMENT {
           int Payment_ID PK
           int Bill_ID FK
           date Payment_Date
           decimal Amount_Paid
       }
   ```

   - The one to one relationship between Customer and Meter is implemented by placing `Customer_ID` as a foreign key in Meter with a UNIQUE constraint on it, which enforces that no customer has two meters. Placing it on the Meter side is preferable because Meter has total participation.
   - Consumption in the Reading entity is a derived attribute, computed as the current reading minus the previous one; whether to store it is a deliberate denormalisation decision, usually taken because billing disputes require the figure as it was calculated at the time. <!-- verify -->
12. **Draw ER diagram from a story.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 837 (ET: N/A)]*


   Answer: Drawing an E-R diagram from a narrative description follows a systematic procedure, which is what such a question tests.

   Procedure:
   - Step 1: read the description and underline every noun. Nouns are candidate entities and attributes.
   - Step 2: decide which nouns are entities. A noun is an entity if it has attributes of its own and there will be many instances of it. A noun that merely describes another noun is an attribute.
   - Step 3: underline every verb. Verbs connecting two entities are candidate relationships.
   - Step 4: assign attributes to entities and identify the primary key of each.
   - Step 5: determine the cardinality of each relationship by asking two questions in both directions: "can one A be related to many B?" and "can one B be related to many A?"
   - Step 6: determine participation by asking "must every A take part in this relationship?" Total participation is drawn with a double line.
   - Step 7: identify any attributes belonging to the relationship rather than to either entity; these are descriptive attributes and they force the relationship into its own table.
   - Step 8: look for weak entities, which have no key of their own and depend on an owner.
   - Step 9: draw the diagram and then convert it to tables by the standard rules.

   Worked example, from the narrative "A hospital has several departments. Each department has many doctors, and each doctor belongs to one department. A patient may consult many doctors, and a doctor sees many patients. Each consultation has a date, a diagnosis and a prescription.":
   - Nouns: hospital, department, doctor, patient, consultation, date, diagnosis, prescription.
   - Entities: Department, Doctor, Patient. Consultation becomes a relationship.
   - Attributes: date, diagnosis and prescription describe the consultation, so they are descriptive attributes of the relationship.
   - Cardinalities: Department to Doctor is one to many; Doctor to Patient is many to many.

   ```mermaid
   erDiagram
       DEPARTMENT ||--o{ DOCTOR : "employs"
       DOCTOR ||--o{ CONSULTATION : "conducts"
       PATIENT ||--o{ CONSULTATION : "attends"
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
           int Age
       }
       CONSULTATION {
           int Doctor_ID PK
           int Patient_ID PK
           date Consult_Date PK
           string Diagnosis
           string Prescription
       }
   ```

   Rules for converting an E-R diagram into tables:
   - Each strong entity becomes a table, with its key attribute as the primary key.
   - Each weak entity becomes a table whose primary key is the combination of its own partial key and the primary key of the owning entity, which is also a foreign key.
   - A one to one relationship becomes a foreign key placed in either table, preferably in the one with total participation.
   - A one to many relationship becomes a foreign key placed in the table on the "many" side, referring to the "one" side. No extra table is needed.
   - A many to many relationship becomes a separate junction table, whose primary key is the combination of the two foreign keys, and which also holds any descriptive attributes of the relationship.
   - A multivalued attribute becomes a separate table containing the entity's key and the attribute.
   - A composite attribute is flattened into its component columns.
   - A derived attribute is not stored; it is computed when required.
13. **Draw E-R diagram of hospital management system. Hospital name “SKY Hospital Ltd.”.** *[RAKUB Programmer (PO) 12.10.2021 compact it 853 (ET: N/A)]*


   Answer: E-R diagram for a hospital management system, SKY Hospital Ltd.

   Entities and attributes:
   - Patient: Patient_ID as primary key, Name, Age, Gender, Date_of_Birth, Address, Phone, Blood_Group, Admission_Date.
   - Doctor: Doctor_ID as primary key, Name, Specialization, Qualification, Phone, Consultation_Fee, Department_ID.
   - Department: Department_ID as primary key, Department_Name, Location, Head_Doctor_ID.
   - Appointment: Appointment_ID as primary key, Patient_ID, Doctor_ID, Appointment_Date, Time_Slot, Status.
   - Treatment: the relationship between Doctor and Patient, carrying Treatment_Date, Diagnosis, Prescription and Notes.
   - Room: Room_No as primary key, Room_Type which is General, Cabin or ICU, Charge_Per_Day, Availability.
   - Admission: Admission_ID as primary key, Patient_ID, Room_No, Admit_Date, Discharge_Date.
   - Bill: Bill_ID as primary key, Patient_ID, Bill_Date, Room_Charge, Doctor_Fee, Medicine_Cost, Test_Charge, Total_Amount, Payment_Status.
   - Nurse: Nurse_ID as primary key, Name, Shift, Department_ID.
   - Test: Test_ID as primary key, Test_Name, Cost, Patient_ID, Result, Test_Date.

   Relationships and cardinalities:
   - Department EMPLOYS Doctor: one to many.
   - Patient BOOKS Appointment WITH Doctor: many to many, resolved by the Appointment entity.
   - Doctor TREATS Patient: many to many, carrying the diagnosis and prescription.
   - Patient OCCUPIES Room: one to one at any moment, but one to many over time, so the Admission entity records each stay.
   - Patient RECEIVES Bill: one to many.
   - Patient UNDERGOES Test: one to many.
   - Nurse ASSIGNED_TO Department: many to one.

   ```mermaid
   erDiagram
       DEPARTMENT ||--o{ DOCTOR : "employs"
       DEPARTMENT ||--o{ NURSE : "employs"
       PATIENT ||--o{ APPOINTMENT : "books"
       DOCTOR ||--o{ APPOINTMENT : "accepts"
       PATIENT ||--o{ ADMISSION : "is admitted by"
       ROOM ||--o{ ADMISSION : "accommodates"
       PATIENT ||--o{ BILL : "is billed"
       PATIENT ||--o{ TEST : "undergoes"
       PATIENT {
           int Patient_ID PK
           string Name
           int Age
           string Blood_Group
           string Phone
       }
       DOCTOR {
           int Doctor_ID PK
           string Name
           string Specialization
           decimal Consultation_Fee
           int Department_ID FK
       }
       DEPARTMENT {
           int Department_ID PK
           string Department_Name
           string Location
       }
       APPOINTMENT {
           int Appointment_ID PK
           int Patient_ID FK
           int Doctor_ID FK
           date Appointment_Date
           string Diagnosis
       }
       ROOM {
           int Room_No PK
           string Room_Type
           decimal Charge_Per_Day
       }
       ADMISSION {
           int Admission_ID PK
           int Patient_ID FK
           int Room_No FK
           date Admit_Date
           date Discharge_Date
       }
       BILL {
           int Bill_ID PK
           int Patient_ID FK
           decimal Total_Amount
           string Payment_Status
       }
       TEST {
           int Test_ID PK
           int Patient_ID FK
           string Test_Name
           decimal Cost
       }
       NURSE {
           int Nurse_ID PK
           string Name
           string Shift
           int Department_ID FK
       }
   ```

   - The design point worth stating: Admission is a separate entity rather than a simple foreign key in Patient, because a patient may be admitted several times and each stay has its own room, dates and charges. Recording only the current room would destroy the history.
14. **Draw E-R diagram of Banking Management system. Bank name “SKY Bank Ltd.”.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)]*


   Answer: E-R diagram for a banking management system, SKY Bank Ltd.

   Entities and attributes:
   - Customer: Customer_ID as primary key, Name, Date_of_Birth, Address, Phone, Email, NID, Occupation.
   - Account: Account_No as primary key, Account_Type which is Savings, Current or Fixed Deposit, Balance, Opening_Date, Status, Interest_Rate, Branch_ID.
   - Branch: Branch_ID as primary key, Branch_Name, Address, City, Phone, Manager_ID.
   - Transaction: Transaction_ID as primary key, Account_No, Transaction_Date, Transaction_Type which is deposit, withdrawal or transfer, Amount, Balance_After, Description.
   - Loan: Loan_ID as primary key, Customer_ID, Loan_Type, Principal_Amount, Interest_Rate, Tenure, Sanction_Date, Outstanding_Balance, Status.
   - Employee: Employee_ID as primary key, Name, Designation, Branch_ID, Salary, Joining_Date.
   - Card: Card_No as primary key, Account_No, Card_Type which is debit or credit, Issue_Date, Expiry_Date, Status.
   - Loan_Payment: Payment_ID as primary key, Loan_ID, Payment_Date, Amount, Principal_Component, Interest_Component.

   Relationships and cardinalities:
   - Customer HAS Account: many to many in the general case, since a customer may hold several accounts and a joint account has several holders. If joint accounts are excluded it is one to many.
   - Branch MAINTAINS Account: one to many.
   - Account RECORDS Transaction: one to many, with total participation on the Transaction side since a transaction cannot exist without an account.
   - Customer TAKES Loan: one to many.
   - Loan HAS Loan_Payment: one to many.
   - Branch EMPLOYS Employee: one to many.
   - Account HAS Card: one to many, since an account may have both a debit and a credit card.

   ```mermaid
   erDiagram
       BRANCH ||--o{ ACCOUNT : "maintains"
       BRANCH ||--o{ EMPLOYEE : "employs"
       CUSTOMER ||--o{ ACCOUNT : "holds"
       ACCOUNT ||--o{ TRANSACTION : "records"
       ACCOUNT ||--o{ CARD : "has"
       CUSTOMER ||--o{ LOAN : "takes"
       LOAN ||--o{ LOAN_PAYMENT : "is repaid by"
       CUSTOMER {
           int Customer_ID PK
           string Name
           string NID
           string Address
           string Phone
       }
       ACCOUNT {
           string Account_No PK
           string Account_Type
           decimal Balance
           date Opening_Date
           int Customer_ID FK
           int Branch_ID FK
       }
       BRANCH {
           int Branch_ID PK
           string Branch_Name
           string City
       }
       TRANSACTION {
           int Transaction_ID PK
           string Account_No FK
           date Transaction_Date
           string Transaction_Type
           decimal Amount
       }
       LOAN {
           int Loan_ID PK
           int Customer_ID FK
           decimal Principal_Amount
           decimal Interest_Rate
           string Status
       }
       LOAN_PAYMENT {
           int Payment_ID PK
           int Loan_ID FK
           date Payment_Date
           decimal Amount
       }
       CARD {
           string Card_No PK
           string Account_No FK
           string Card_Type
           date Expiry_Date
       }
       EMPLOYEE {
           int Employee_ID PK
           string Name
           string Designation
           int Branch_ID FK
       }
   ```

   Design points worth stating:
   - If joint accounts are permitted, the Customer to Account relationship is many to many and requires a junction table `Account_Holder(Customer_ID, Account_No, Holder_Type)`. This is the decision an examiner looks for.
   - `Balance` in Account is a derived value, being the sum of all transactions, but it is stored deliberately. Recomputing it from millions of transactions on every enquiry would be unacceptable, so this is a justified denormalisation, maintained by the application within a transaction.
   - A transfer is modelled as two transaction rows, a debit and a credit, linked by a common reference, so that double entry is preserved.
15. **Draw ER diagram for details of gas company data described. Bakharbad gas distribution Compeny has two types of customers i.e General and Industrial. General customer has customer ID, name, DOB, age (calculated from DOB). Industrial customer has all attributes of general customer with TAX number additionally. Meter has model and producer name. Every customer has one meter.** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 877 (ET: BUET)]*


   Answer: This is a specialisation and generalisation problem, since there are two kinds of customer sharing most attributes.

   Entities and attributes:
   - Customer, the superclass: Customer_ID as primary key, Name, Date_of_Birth, Age as a derived attribute computed from the date of birth, Address, Phone.
   - General_Customer, a subclass: it inherits everything from Customer and adds nothing of its own.
   - Industrial_Customer, a subclass: it inherits everything from Customer and adds Tax_Number.
   - Meter: Meter_ID as primary key, Model, Producer_Name, Installation_Date.

   Relationships and constraints:
   - Customer IS-A General_Customer or Industrial_Customer: this is a specialisation, drawn with a triangle. It is disjoint, since a customer is of one kind or the other but not both, and total, since every customer is one of the two.
   - Customer HAS Meter: one to one, since every customer has exactly one meter and every meter belongs to one customer. Both sides have total participation.
   - Age is a derived attribute, drawn with a dashed ellipse, and it is not stored; it is computed from the date of birth whenever required.

   ```
        Customer_ID   Name   DOB   (Age)   Address
             |          |     |      :        |
             +----------+--+--+......+--------+
                           |
                     +-----------+  1        1  +---------+
                     | CUSTOMER  |----< HAS >---|  METER  |
                     +-----------+              +---------+
                           |                         |
                          /_\  (disjoint, total)   +--+---+
                         /   \                     |      |
              +---------+     +----------+       Model  Producer
              | GENERAL |     | INDUSTRIAL|
              +---------+     +----------+
                                    |
                               Tax_Number
   ```

   ```mermaid
   erDiagram
       CUSTOMER ||--|| METER : "has"
       CUSTOMER ||--o| GENERAL_CUSTOMER : "is a"
       CUSTOMER ||--o| INDUSTRIAL_CUSTOMER : "is a"
       CUSTOMER {
           int Customer_ID PK
           string Name
           date DOB
           string Address
       }
       GENERAL_CUSTOMER {
           int Customer_ID PK
       }
       INDUSTRIAL_CUSTOMER {
           int Customer_ID PK
           string Tax_Number
       }
       METER {
           int Meter_ID PK
           string Model
           string Producer_Name
           int Customer_ID FK
       }
   ```

   Conversion to tables. Three strategies exist for a specialisation, and the choice should be justified:

   Strategy 1, a single table with a discriminator, which is the simplest and is appropriate here because the subclasses differ by only one attribute:

   ```sql
   CREATE TABLE Customer (
       Customer_ID   INT PRIMARY KEY,
       Name          VARCHAR(100) NOT NULL,
       DOB           DATE,
       Address       VARCHAR(200),
       Customer_Type VARCHAR(20) CHECK (Customer_Type IN ('General','Industrial')),
       Tax_Number    VARCHAR(30),
       CHECK ((Customer_Type = 'Industrial' AND Tax_Number IS NOT NULL)
           OR (Customer_Type = 'General'    AND Tax_Number IS NULL))
   );

   CREATE TABLE Meter (
       Meter_ID      INT PRIMARY KEY,
       Model         VARCHAR(50),
       Producer_Name VARCHAR(100),
       Customer_ID   INT UNIQUE NOT NULL REFERENCES Customer(Customer_ID)
   );
   ```

   Strategy 2, a table per subclass, keeping the superclass table and adding one table for the subclass with the extra attribute:

   ```sql
   CREATE TABLE Industrial_Customer (
       Customer_ID INT PRIMARY KEY REFERENCES Customer(Customer_ID),
       Tax_Number  VARCHAR(30) NOT NULL
   );
   ```

   Points worth stating:
   - `Age` is not a column, because it is derived. Storing it would require updating every row every year, which is exactly the kind of anomaly normalisation avoids.
   - The one to one relationship is implemented by putting `Customer_ID` in Meter with a `UNIQUE` and `NOT NULL` constraint, which enforces both the one to one cardinality and the total participation.
16. **Draw the ER diagram where their relation named TEAM, PLAYER, MATCH** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 880 (ET: BUET)]*


   Answer: E-R diagram for the entities TEAM, PLAYER and MATCH.

   Entities and attributes:
   - Team: Team_ID as primary key, Team_Name, Coach_Name, Home_Ground, Founded_Year, City.
   - Player: Player_ID as primary key, Player_Name, Date_of_Birth, Age as a derived attribute, Position, Jersey_Number, Nationality, Team_ID.
   - Match: Match_ID as primary key, Match_Date, Venue, Home_Team_ID, Away_Team_ID, Result, Home_Score, Away_Score.
   - Performance, the junction entity between Player and Match: Player_ID, Match_ID, Goals_Scored or Runs, Minutes_Played, Cards or Wickets, Rating.

   Relationships and cardinalities:
   - Team HAS Player: one to many. A team has many players and a player belongs to one team at a time. Player has total participation, since a player must belong to a team.
   - Team PLAYS Match: many to many, since each match involves two teams and each team plays many matches. In practice it is implemented by two foreign keys in Match, Home_Team_ID and Away_Team_ID, both referring to Team, which is a double relationship to the same entity.
   - Player PLAYS_IN Match: many to many, resolved by the Performance entity, which carries the statistics of that player in that match.

   ```mermaid
   erDiagram
       TEAM ||--o{ PLAYER : "has"
       TEAM ||--o{ MATCH : "plays as home team"
       PLAYER ||--o{ PERFORMANCE : "records"
       MATCH ||--o{ PERFORMANCE : "contains"
       TEAM {
           int Team_ID PK
           string Team_Name
           string Coach_Name
           string Home_Ground
       }
       PLAYER {
           int Player_ID PK
           string Player_Name
           date Date_of_Birth
           string Position
           int Jersey_Number
           int Team_ID FK
       }
       MATCH {
           int Match_ID PK
           date Match_Date
           string Venue
           int Home_Team_ID FK
           int Away_Team_ID FK
           string Result
       }
       PERFORMANCE {
           int Player_ID PK
           int Match_ID PK
           int Goals_Scored
           int Minutes_Played
       }
   ```

   Relational schema:

   ```sql
   CREATE TABLE Team (
       Team_ID     INT PRIMARY KEY,
       Team_Name   VARCHAR(100) NOT NULL,
       Coach_Name  VARCHAR(100),
       Home_Ground VARCHAR(100)
   );

   CREATE TABLE Player (
       Player_ID     INT PRIMARY KEY,
       Player_Name   VARCHAR(100) NOT NULL,
       Date_of_Birth DATE,
       Position      VARCHAR(30),
       Jersey_Number INT,
       Team_ID       INT NOT NULL REFERENCES Team(Team_ID),
       UNIQUE (Team_ID, Jersey_Number)
   );

   CREATE TABLE Match (
       Match_ID     INT PRIMARY KEY,
       Match_Date   DATE NOT NULL,
       Venue        VARCHAR(100),
       Home_Team_ID INT NOT NULL REFERENCES Team(Team_ID),
       Away_Team_ID INT NOT NULL REFERENCES Team(Team_ID),
       Result       VARCHAR(50),
       CHECK (Home_Team_ID <> Away_Team_ID)
   );

   CREATE TABLE Performance (
       Player_ID      INT REFERENCES Player(Player_ID),
       Match_ID       INT REFERENCES Match(Match_ID),
       Goals_Scored   INT DEFAULT 0,
       Minutes_Played INT,
       PRIMARY KEY (Player_ID, Match_ID)
   );
   ```

   - Two constraints worth pointing out: `UNIQUE (Team_ID, Jersey_Number)` prevents two players in the same team wearing the same number, and `CHECK (Home_Team_ID <> Away_Team_ID)` prevents a team from playing itself. Constraints of this kind are what turn a diagram into a correct schema.
17. **Railway Service system ER diagram.** *[Sonali Bank Ltd. Officer IT 2021 compact it 910 (ET: N/A)]*


   Answer: E-R diagram for a railway service system.

   Entities and attributes:
   - Passenger: Passenger_ID as primary key, Name, Age, Gender, Phone, Email, NID.
   - Train: Train_No as primary key, Train_Name, Source_Station, Destination_Station, Departure_Time, Arrival_Time, Total_Seats, Train_Type.
   - Station: Station_ID as primary key, Station_Name, City, Zone, Platform_Count.
   - Route: Route_ID as primary key, Train_No, Station_ID, Arrival_Time, Departure_Time, Stop_Number, Distance_From_Source.
   - Ticket: PNR_Number as primary key, Passenger_ID, Train_No, Journey_Date, Class, Seat_Number, Coach_Number, Fare, Booking_Date, Status.
   - Booking: Booking_ID as primary key, Passenger_ID, Booking_Date, Total_Amount, Payment_Status.
   - Class: Class_ID as primary key, Class_Name such as AC, First or Shovon, Fare_Per_Km.
   - Payment: Payment_ID as primary key, Booking_ID, Amount, Payment_Method, Payment_Date, Transaction_Reference.

   Relationships and cardinalities:
   - Passenger BOOKS Ticket: one to many, since one passenger books many tickets over time.
   - Train HAS Ticket: one to many.
   - Train PASSES_THROUGH Station: many to many, resolved by the Route entity, which carries the arrival and departure time at each stop and the stop number. These are descriptive attributes of the relationship, since an arrival time is meaningless without both the train and the station.
   - Ticket BELONGS_TO Class: many to one.
   - Booking HAS Payment: one to one, or one to many if part payment is allowed.

   ```mermaid
   erDiagram
       PASSENGER ||--o{ TICKET : "books"
       TRAIN ||--o{ TICKET : "carries"
       TRAIN ||--o{ ROUTE : "follows"
       STATION ||--o{ ROUTE : "is a stop on"
       PASSENGER ||--o{ BOOKING : "makes"
       BOOKING ||--o{ PAYMENT : "is settled by"
       CLASS ||--o{ TICKET : "categorises"
       PASSENGER {
           int Passenger_ID PK
           string Name
           int Age
           string Phone
           string NID
       }
       TRAIN {
           int Train_No PK
           string Train_Name
           string Source_Station
           string Destination_Station
           int Total_Seats
       }
       STATION {
           int Station_ID PK
           string Station_Name
           string City
       }
       ROUTE {
           int Train_No PK
           int Station_ID PK
           int Stop_Number
           time Arrival_Time
           time Departure_Time
       }
       TICKET {
           string PNR_Number PK
           int Passenger_ID FK
           int Train_No FK
           date Journey_Date
           string Seat_Number
           decimal Fare
       }
       BOOKING {
           int Booking_ID PK
           int Passenger_ID FK
           date Booking_Date
           decimal Total_Amount
       }
       PAYMENT {
           int Payment_ID PK
           int Booking_ID FK
           decimal Amount
           string Payment_Method
       }
       CLASS {
           int Class_ID PK
           string Class_Name
           decimal Fare_Per_Km
       }
   ```

   - The Route entity is the important design decision. A train stops at many stations and a station is served by many trains, so the relationship is many to many; and the arrival time, departure time and stop number belong to the pair rather than to either entity, so they force the relationship into its own table.
18. **(i) Draw ER diagram: Given a scenario about football Game (Game_no, game_time, game_name), Team (team-id, coach_id, team-name), Referee (Referee-id, Referee-name) Player (player-id, palyername, player-position), Stadium information (stadium-id, stadium-name, stadium-loc) Match (match_id, match_date, match_result).** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 928-929 (ET: CTI)], [Janata Bank Assistant System Administrator 2021 compact it 939 (ET: N/A)]*
   **(ii) Convert the ER diagram to relations (Table)** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 929-930 (ET: CTI)]*


   Answer:

   (i) E-R diagram for the football scenario:

   Entities and attributes:
   - Game: Game_no as primary key, Game_time, Game_name.
   - Team: Team_id as primary key, Coach_id, Team_name.
   - Referee: Referee_id as primary key, Referee_name.
   - Player: Player_id as primary key, Player_name, Player_position, Team_id.
   - Stadium: Stadium_id as primary key, Stadium_name, Stadium_loc.
   - Match: Match_id as primary key, Match_date, Match_result, Stadium_id, Referee_id.

   Relationships and cardinalities:
   - Team HAS Player: one to many. A team has many players; a player belongs to one team. Player has total participation.
   - Team PLAYS Match: many to many, since each match involves two teams and each team plays many matches. It is implemented by two foreign keys in Match.
   - Match HELD_AT Stadium: many to one.
   - Referee OFFICIATES Match: one to many, or many to many if several referees officiate one match.
   - Match BELONGS_TO Game: many to one, taking Game as the tournament or fixture category.
   - Player PLAYS_IN Match: many to many, which requires a Performance junction entity if individual statistics are to be recorded.

   ```mermaid
   erDiagram
       TEAM ||--o{ PLAYER : "has"
       TEAM ||--o{ MATCH : "plays in"
       STADIUM ||--o{ MATCH : "hosts"
       REFEREE ||--o{ MATCH : "officiates"
       GAME ||--o{ MATCH : "comprises"
       PLAYER ||--o{ PERFORMANCE : "records"
       MATCH ||--o{ PERFORMANCE : "contains"
       GAME {
           int Game_no PK
           time Game_time
           string Game_name
       }
       TEAM {
           int Team_id PK
           int Coach_id
           string Team_name
       }
       PLAYER {
           int Player_id PK
           string Player_name
           string Player_position
           int Team_id FK
       }
       REFEREE {
           int Referee_id PK
           string Referee_name
       }
       STADIUM {
           int Stadium_id PK
           string Stadium_name
           string Stadium_loc
       }
       MATCH {
           int Match_id PK
           date Match_date
           string Match_result
           int Stadium_id FK
           int Referee_id FK
           int Game_no FK
       }
       PERFORMANCE {
           int Player_id PK
           int Match_id PK
           int Goals
           int Minutes_Played
       }
   ```

   (ii) Conversion of the E-R diagram to relations:

   ```sql
   Game(Game_no, Game_time, Game_name)
       PRIMARY KEY (Game_no)

   Team(Team_id, Coach_id, Team_name)
       PRIMARY KEY (Team_id)

   Player(Player_id, Player_name, Player_position, Team_id)
       PRIMARY KEY (Player_id)
       FOREIGN KEY (Team_id) REFERENCES Team(Team_id)

   Referee(Referee_id, Referee_name)
       PRIMARY KEY (Referee_id)

   Stadium(Stadium_id, Stadium_name, Stadium_loc)
       PRIMARY KEY (Stadium_id)

   Match(Match_id, Match_date, Match_result, Home_Team_id, Away_Team_id,
         Stadium_id, Referee_id, Game_no)
       PRIMARY KEY (Match_id)
       FOREIGN KEY (Home_Team_id) REFERENCES Team(Team_id)
       FOREIGN KEY (Away_Team_id) REFERENCES Team(Team_id)
       FOREIGN KEY (Stadium_id)   REFERENCES Stadium(Stadium_id)
       FOREIGN KEY (Referee_id)   REFERENCES Referee(Referee_id)
       FOREIGN KEY (Game_no)      REFERENCES Game(Game_no)
       CHECK (Home_Team_id <> Away_Team_id)

   Performance(Player_id, Match_id, Goals, Minutes_Played)
       PRIMARY KEY (Player_id, Match_id)
       FOREIGN KEY (Player_id) REFERENCES Player(Player_id)
       FOREIGN KEY (Match_id)  REFERENCES Match(Match_id)
   ```

   Rules applied in the conversion:
   - Each entity became a table with its key attribute as the primary key.
   - The one to many relationship between Team and Player became a foreign key on the "many" side, that is `Team_id` in Player. No extra table was needed.
   - The many to many relationship between Team and Match was handled by two foreign keys in Match, since exactly two teams take part; had the number been unbounded, a junction table would have been required.
   - The many to many relationship between Player and Match became the Performance junction table with a composite primary key.
   - `CHECK (Home_Team_id <> Away_Team_id)` was added, because a team cannot play itself.
19. **Draw ER diagram (Self test)** *[Combined 4 Banks Assistant Programmer 2020 compact it 1009 (ET: DU)]*


   Answer: The scenario is not specified, so the general method and a complete worked example are given.

   Method for drawing an E-R diagram:
   - Identify the entities: the nouns in the description that have attributes of their own and of which there will be many instances.
   - Identify the attributes of each entity, and underline the primary key.
   - Identify the relationships: the verbs connecting two entities.
   - Determine the cardinality of each relationship, by asking in both directions whether one instance can relate to many.
   - Determine the participation, that is whether every instance must take part; total participation is drawn with a double line.
   - Identify any attributes belonging to a relationship rather than to an entity; these are descriptive attributes.
   - Look for weak entities, which have no key of their own.
   - Draw the diagram and convert it to tables.

   Worked example, an online shopping system:

   ```mermaid
   erDiagram
       CUSTOMER ||--o{ ORDERS : "places"
       ORDERS ||--|{ ORDER_ITEM : "contains"
       PRODUCT ||--o{ ORDER_ITEM : "appears in"
       CATEGORY ||--o{ PRODUCT : "classifies"
       ORDERS ||--|| PAYMENT : "is paid by"
       CUSTOMER {
           int Customer_ID PK
           string Name
           string Email
           string Phone
           string Address
       }
       CATEGORY {
           int Category_ID PK
           string Category_Name
       }
       PRODUCT {
           int Product_ID PK
           string Product_Name
           decimal Price
           int Stock
           int Category_ID FK
       }
       ORDERS {
           int Order_ID PK
           int Customer_ID FK
           date Order_Date
           decimal Total_Amount
           string Status
       }
       ORDER_ITEM {
           int Order_ID PK
           int Product_ID PK
           int Quantity
           decimal Unit_Price
       }
       PAYMENT {
           int Payment_ID PK
           int Order_ID FK
           decimal Amount
           string Method
           date Payment_Date
       }
   ```

   Rules for converting an E-R diagram into tables:
   - Each strong entity becomes a table, with its key attribute as the primary key.
   - Each weak entity becomes a table whose primary key is the combination of its own partial key and the primary key of the owning entity, which is also a foreign key.
   - A one to one relationship becomes a foreign key placed in either table, preferably in the one with total participation.
   - A one to many relationship becomes a foreign key placed in the table on the "many" side, referring to the "one" side. No extra table is needed.
   - A many to many relationship becomes a separate junction table, whose primary key is the combination of the two foreign keys, and which also holds any descriptive attributes of the relationship.
   - A multivalued attribute becomes a separate table containing the entity's key and the attribute.
   - A composite attribute is flattened into its component columns.
   - A derived attribute is not stored; it is computed when required.
20. **E-R Diagram কী? উদাহরণসহ লিখুন?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019-1020 (ET: N/A)]*


   Answer:

   What an E-R diagram is:
   - An Entity Relationship diagram is a graphical representation of the data requirements of a system, showing the entities about which data is to be stored, the attributes describing them, and the relationships between them. It was introduced by Peter Chen in 1976 and it is the standard first step of database design.
   - It is a conceptual model, independent of any particular database product, and it is converted to a relational schema by defined rules.

   Components of an E-R model:
   - Entity: a real world object or concept about which data is stored, drawn as a rectangle. A strong entity has its own key; a weak entity, drawn as a double rectangle, depends on another entity for its identity.
   - Attribute: a property of an entity, drawn as an ellipse. Types: simple and composite; single valued and multivalued, drawn as a double ellipse; derived, drawn as a dashed ellipse; and the key attribute, whose name is underlined.
   - Relationship: an association between entities, drawn as a diamond. A relationship may itself carry descriptive attributes.
   - Cardinality: one to one, one to many, many to one, or many to many, written on the connecting lines.
   - Participation: total participation, shown by a double line, meaning every instance of the entity must take part; and partial participation, shown by a single line.

   Example, a university system:

   ```
      Student_ID     Name      Dept            Course_ID   Course_Name   Credit
          |            |         |                 |            |          |
          +------+-----+---------+                 +-----+------+----------+
                 |                                       |
           +-----------+     M              N     +-------------+
           |  STUDENT  |--------< ENROLLS >-------|   COURSE    |
           +-----------+                          +-------------+
                                  |
                          Grade, Enrollment_Date
   ```

   Reading the diagram:
   - Student and Course are entities, drawn as rectangles. Their attributes are drawn as ellipses, with the key attributes underlined.
   - ENROLLS is a relationship, drawn as a diamond. It is many to many, since a student enrols in many courses and a course has many students.
   - Grade and Enrollment_Date are descriptive attributes of the relationship, because a grade is meaningless without knowing both the student and the course.

   Conversion to tables:

   ```sql
   Student(Student_ID, Name, Dept)
   Course(Course_ID, Course_Name, Credit)
   Enrollment(Student_ID, Course_ID, Enrollment_Date, Grade)
   ```

   - The many to many relationship becomes a junction table whose primary key is the pair of foreign keys, which is where the descriptive attributes are stored.
21. **Draw an ER diagram of a Library Management System.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036-1037 (ET: BUET)]*


   Answer: E-R diagram for a library management system.

   Entities and attributes:
   - Book: ISBN as primary key, Title, Author, Publisher, Edition, Subject, Publication_Year, Price.
   - Book_Copy, a weak entity: Copy_ID as a partial key together with ISBN, Shelf_Location, Status which is Available, Issued, Reserved or Damaged, Acquisition_Date.
   - Member: Member_ID as primary key, Name, Address, Phone, Email, Member_Type which is Student, Teacher or Staff, Join_Date, Expiry_Date.
   - Librarian: Staff_ID as primary key, Name, Designation, Phone, Shift.
   - Issue: Issue_ID as primary key, Copy_ID, ISBN, Member_ID, Staff_ID, Issue_Date, Due_Date, Return_Date, Fine.
   - Reservation: Reservation_ID as primary key, Member_ID, ISBN, Reservation_Date, Status.
   - Publisher: Publisher_ID as primary key, Publisher_Name, Address, Contact.

   Relationships and cardinalities:
   - Book HAS Book_Copy: one to many, and identifying, since a copy has no identity of its own without the book it is a copy of. Book_Copy is therefore a weak entity, drawn with a double rectangle and a double diamond.
   - Member BORROWS Book_Copy: many to many over time, resolved by the Issue entity, which carries the dates and the fine.
   - Librarian PROCESSES Issue: one to many.
   - Member RESERVES Book: many to many, resolved by the Reservation entity.
   - Publisher PUBLISHES Book: one to many.

   ```mermaid
   erDiagram
       PUBLISHER ||--o{ BOOK : "publishes"
       BOOK ||--|{ BOOK_COPY : "has copies"
       MEMBER ||--o{ ISSUE : "borrows"
       BOOK_COPY ||--o{ ISSUE : "is issued in"
       LIBRARIAN ||--o{ ISSUE : "processes"
       MEMBER ||--o{ RESERVATION : "reserves"
       BOOK ||--o{ RESERVATION : "is reserved as"
       BOOK {
           string ISBN PK
           string Title
           string Author
           string Subject
           int Publisher_ID FK
       }
       BOOK_COPY {
           int Copy_ID PK
           string ISBN PK
           string Shelf_Location
           string Status
       }
       MEMBER {
           int Member_ID PK
           string Name
           string Member_Type
           date Expiry_Date
       }
       LIBRARIAN {
           int Staff_ID PK
           string Name
           string Designation
       }
       ISSUE {
           int Issue_ID PK
           int Copy_ID FK
           int Member_ID FK
           int Staff_ID FK
           date Issue_Date
           date Due_Date
           date Return_Date
           decimal Fine
       }
       RESERVATION {
           int Reservation_ID PK
           int Member_ID FK
           string ISBN FK
           date Reservation_Date
       }
       PUBLISHER {
           int Publisher_ID PK
           string Publisher_Name
           string Address
       }
   ```

   Design points that earn marks:
   - The separation of Book from Book_Copy is the essential decision. Book holds the bibliographic information once, and Book_Copy holds one row per physical volume. Without it, the title, author and publisher would be repeated for every copy, which is precisely the redundancy that normalisation exists to remove.
   - Book_Copy is a weak entity: its Copy_ID alone does not identify it, so its primary key is the composite (ISBN, Copy_ID).
   - Fine is stored in Issue rather than computed on demand, because the rate may change over time and the amount actually charged must be preserved.

## Keys in DBMS (21)

1. Difference Between Primary Key, Foreign Key, Candidate Key. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*


   Answer:

   | Point | Primary Key | Foreign Key | Candidate Key |
   |---|---|---|---|
   | Definition | The candidate key chosen to identify rows of its own table | An attribute referring to the primary key of another table | Any minimal set of attributes that uniquely identifies a row |
   | Uniqueness | Must be unique | May repeat | Must be unique |
   | NULL | Not permitted | Permitted unless declared NOT NULL | Permitted in principle, but a candidate key chosen as primary must not be NULL |
   | Number per table | Exactly one | Any number | One or more |
   | Purpose | Entity integrity, that is unique identification | Referential integrity, that is linking tables | Provides the pool from which the primary key is chosen |
   | Index | Created automatically | Not created automatically; should be added | Created if declared UNIQUE |
   | Minimality | Minimal, since it is a candidate key | Not relevant | Minimal by definition |
   | Example | Student_ID in Student | Dept_ID in Employee referring to Department | Student_ID, Registration_No and NID in Student |

   Relationship between them:
   - Every candidate key is a minimal super key. The designer chooses one of them as the primary key; the remainder become alternate keys, normally enforced with a UNIQUE constraint.
   - A foreign key is not a key of its own table at all; it is a reference to a key of another table. Its values are drawn from the referenced column, so it is unique only by coincidence.

   Example:

   ```sql
   CREATE TABLE Department (
       Dept_ID   INT PRIMARY KEY,
       Dept_Name VARCHAR(50) NOT NULL UNIQUE
   );

   CREATE TABLE Student (
       Student_ID      INT PRIMARY KEY,          -- primary key
       Registration_No VARCHAR(20) UNIQUE,       -- candidate key, now an alternate key
       NID             VARCHAR(20) UNIQUE,       -- candidate key, now an alternate key
       Name            VARCHAR(100) NOT NULL,
       Dept_ID         INT REFERENCES Department(Dept_ID)   -- foreign key
   );
   ```
2. **(a) Define RDBMS. Explain the different key and primary key, candidate key, super key, and foreign key DBMS.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1445 (ET: N/A)]*


   Answer:

   Definition of RDBMS:
   - A Relational Database Management System is a database management system based on the relational model proposed by E. F. Codd in 1970, in which data is stored in tables, called relations, consisting of rows and columns.
   - Its characteristics: data is held in two dimensional tables; each row is a tuple and each column an attribute; the order of rows and columns is immaterial; every value is atomic; tables are related to one another by keys rather than by pointers; and the language used is SQL.
   - It enforces integrity: entity integrity through the primary key, referential integrity through the foreign key, and domain integrity through data types and CHECK constraints.
   - It supports transactions with the ACID properties.
   - Examples: Oracle, MySQL, PostgreSQL, Microsoft SQL Server, IBM Db2.

   The different kinds of key:

   - Super key: any attribute or set of attributes that uniquely identifies a row. It may contain extra attributes that are not needed for uniqueness. It is the widest category, and every other key is a super key.
   - Candidate key: a minimal super key, that is a super key from which no attribute can be removed without losing uniqueness. A relation may have several candidate keys.
   - Primary key: the one candidate key chosen by the designer to identify rows. It cannot be NULL and cannot contain duplicates, and a table has exactly one.
   - Alternate key: any candidate key not chosen as the primary key. It is normally enforced with a UNIQUE constraint.
   - Composite key: a key made up of two or more attributes together, because no single attribute is unique.
   - Foreign key: an attribute in one table whose values must match the primary key of another table, which is how a relationship between tables is expressed. It may be NULL and may contain duplicates.
   - Unique key: a constraint guaranteeing uniqueness that is not the primary key. Unlike the primary key it permits one NULL value.
   - Surrogate key: an artificial key with no business meaning, such as an auto-incremented number, used when no natural attribute is a satisfactory identifier.

   Example, a Student relation:

   ```
   Student(Student_ID, Registration_No, NID, Name, Department, Dept_ID)
   ```

   - Super keys: {Student_ID}, {Registration_No}, {NID}, {Student_ID, Name}, {Registration_No, Department} and so on, since adding attributes to a unique set keeps it unique.
   - Candidate keys: {Student_ID}, {Registration_No}, {NID}, each of which is unique and minimal.
   - Primary key: Student_ID, chosen by the designer.
   - Alternate keys: Registration_No and NID.
   - Foreign key: Dept_ID, referring to Department(Dept_ID).
   - Composite key example: in `Enrollment(Student_ID, Course_ID, Grade)` the primary key is the pair (Student_ID, Course_ID), since neither alone is unique.

   Relationship between them: every candidate key is a super key, and the primary key is one of the candidate keys. So primary key ⊆ candidate key ⊆ super key.
3. **Difference between primary key, foreign key? What is trigger?** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 502 (ET: N/A)]*


   Answer:

   Difference between primary key and foreign key:

   | Point | Primary Key | Foreign Key |
   |---|---|---|
   | Purpose | Uniquely identifies each row of its own table | Links a row to a row of another table |
   | Uniqueness | Must be unique | May repeat |
   | NULL values | Not permitted | Permitted, unless declared NOT NULL |
   | Number per table | Exactly one | Any number |
   | Index | Created automatically | Not created automatically in most systems; should be created manually |
   | References | Nothing; it is referenced | The primary key or a unique key of another table |
   | Deletion | A row cannot be deleted while a foreign key refers to it, unless CASCADE is specified | Deleting the child row affects nothing else |
   | What it enforces | Entity integrity | Referential integrity |
   | Constraint syntax | `PRIMARY KEY (col)` | `FOREIGN KEY (col) REFERENCES Parent(col)` |

   Example:

   ```sql
   CREATE TABLE Department (
       Dept_ID   INT PRIMARY KEY,
       Dept_Name VARCHAR(50) NOT NULL
   );

   CREATE TABLE Employee (
       Emp_ID   INT PRIMARY KEY,              -- primary key of Employee
       Emp_Name VARCHAR(100) NOT NULL,
       Dept_ID  INT,                          -- foreign key
       FOREIGN KEY (Dept_ID) REFERENCES Department(Dept_ID)
   );
   ```

   - `Emp_ID` uniquely identifies each employee, which is entity integrity.
   - `Dept_ID` in Employee must match some `Dept_ID` in Department, which is referential integrity. An employee cannot be placed in a department that does not exist, and a department cannot be deleted while employees still refer to it, unless `ON DELETE CASCADE` or `ON DELETE SET NULL` is specified.

   What a trigger is:
   - A trigger is a named block of procedural code stored in the database and executed automatically by the DBMS when a specified event occurs on a specified table. It is never called explicitly by an application.
   - Its components: the event, that is INSERT, UPDATE or DELETE; the timing, that is BEFORE, AFTER or INSTEAD OF; the level, that is FOR EACH ROW or FOR EACH STATEMENT; and the body, that is the code to be executed.

   ```sql
   CREATE TRIGGER audit_salary_change
   AFTER UPDATE ON Employee
   FOR EACH ROW
   BEGIN
       IF OLD.salary <> NEW.salary THEN
           INSERT INTO Salary_Audit(emp_id, old_salary, new_salary, changed_on, changed_by)
           VALUES (OLD.emp_id, OLD.salary, NEW.salary, NOW(), CURRENT_USER());
       END IF;
   END;
   ```

   Uses of triggers:
   - Maintaining an audit trail of who changed what and when, which is a regulatory requirement in banking.
   - Enforcing complex business rules that a CHECK constraint cannot express, for example that a withdrawal must not exceed the balance plus the overdraft limit.
   - Maintaining derived or summary columns automatically, such as updating an account balance when a transaction is inserted.
   - Enforcing referential actions beyond what CASCADE provides.
   - Preventing invalid operations, by raising an error inside a BEFORE trigger.

   Disadvantages worth stating: triggers execute invisibly, so they make behaviour hard to predict and to debug; they add overhead to every affected statement; a chain of triggers firing one another is difficult to trace; and they can make a bulk load extremely slow.
4. **Define primary key, super key, and Candidate key.** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*


   Answer:

   Super key:
   - A super key is any attribute or set of attributes whose values uniquely identify a row of a relation. It may contain redundant attributes that are not required for uniqueness.
   - It is the widest of the three categories: every candidate key and every primary key is also a super key.
   - Example, in `Student(Student_ID, Registration_No, Name, Department)`: {Student_ID}, {Registration_No}, {Student_ID, Name}, {Student_ID, Registration_No, Name, Department} are all super keys, because each identifies a row uniquely.

   Candidate key:
   - A candidate key is a minimal super key, that is a super key from which no attribute can be removed without destroying uniqueness.
   - A relation may have several candidate keys, and each is a genuine alternative for identifying rows.
   - Example: {Student_ID} and {Registration_No} are candidate keys, since each is unique and neither contains a redundant attribute. {Student_ID, Name} is not a candidate key, because Name can be dropped and uniqueness survives.

   Primary key:
   - The primary key is the one candidate key selected by the designer to be the principal means of identifying rows.
   - It must be unique, it cannot be NULL, and a table has exactly one. The DBMS creates an index on it automatically.
   - The candidate keys not chosen are called alternate keys and are normally enforced with a UNIQUE constraint.
   - Example: Student_ID is chosen as the primary key, and Registration_No becomes an alternate key.

   Relationship, which is the point being tested:
   - primary key ⊆ candidate key ⊆ super key.
   - Every primary key is a candidate key, and every candidate key is a super key, but not the reverse.

   Criteria for choosing the primary key from among the candidate keys: it should be stable and never change, short, simple, never NULL, and preferably numeric for indexing efficiency. Where no natural attribute satisfies these, a surrogate key such as an auto-incremented integer is created.
5. **What is primary key and foreign key with example?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 499 (ET: N/A)]*


   Answer:

   Primary key:
   - A primary key is the attribute or set of attributes chosen to identify each row of a table uniquely. It must be unique, it cannot contain NULL, and a table has exactly one. It enforces entity integrity, and the DBMS creates an index on it automatically.

   Foreign key:
   - A foreign key is an attribute in one table whose values must match the primary key of another table. It expresses the relationship between the two tables and enforces referential integrity. It may be NULL and may contain duplicate values, and a table may have several.

   Example:

   ```sql
   CREATE TABLE Department (
       Dept_ID   INT PRIMARY KEY,
       Dept_Name VARCHAR(50) NOT NULL
   );

   CREATE TABLE Employee (
       Emp_ID   INT PRIMARY KEY,
       Emp_Name VARCHAR(100) NOT NULL,
       Salary   DECIMAL(10,2),
       Dept_ID  INT,
       FOREIGN KEY (Dept_ID) REFERENCES Department(Dept_ID)
   );
   ```

   With data:

   | Department |  | | Employee | | | |
   |---|---|---|---|---|---|---|
   | Dept_ID | Dept_Name | | Emp_ID | Emp_Name | Salary | Dept_ID |
   | 10 | IT | | 1 | Rahim | 45000 | 10 |
   | 20 | Finance | | 2 | Karim | 65000 | 10 |
   | 30 | HR | | 3 | Salma | 40000 | 20 |

   - `Emp_ID` is the primary key of Employee: no two employees share it and it is never NULL.
   - `Dept_ID` in Employee is a foreign key referring to `Dept_ID` in Department. It repeats, since two employees are in department 10, and it could be NULL for an employee not yet assigned.
   - What the foreign key enforces: an employee cannot be given `Dept_ID = 50`, because no such department exists; and department 10 cannot be deleted while employees still refer to it, unless `ON DELETE CASCADE` is specified, which would delete those employees too, or `ON DELETE SET NULL`, which would set their `Dept_ID` to NULL.

   | Point | Primary Key | Foreign Key |
   |---|---|---|
   | Purpose | Uniquely identifies each row of its own table | Links a row to a row of another table |
   | Uniqueness | Must be unique | May repeat |
   | NULL values | Not permitted | Permitted, unless declared NOT NULL |
   | Number per table | Exactly one | Any number |
   | Index | Created automatically | Not created automatically in most systems; should be created manually |
   | References | Nothing; it is referenced | The primary key or a unique key of another table |
   | Deletion | A row cannot be deleted while a foreign key refers to it, unless CASCADE is specified | Deleting the child row affects nothing else |
   | What it enforces | Entity integrity | Referential integrity |
   | Constraint syntax | `PRIMARY KEY (col)` | `FOREIGN KEY (col) REFERENCES Parent(col)` |

   Example:

   ```sql
   CREATE TABLE Department (
       Dept_ID   INT PRIMARY KEY,
       Dept_Name VARCHAR(50) NOT NULL
   );

   CREATE TABLE Employee (
       Emp_ID   INT PRIMARY KEY,              -- primary key of Employee
       Emp_Name VARCHAR(100) NOT NULL,
       Dept_ID  INT,                          -- foreign key
       FOREIGN KEY (Dept_ID) REFERENCES Department(Dept_ID)
   );
   ```

   - `Emp_ID` uniquely identifies each employee, which is entity integrity.
   - `Dept_ID` in Employee must match some `Dept_ID` in Department, which is referential integrity. An employee cannot be placed in a department that does not exist, and a department cannot be deleted while employees still refer to it, unless `ON DELETE CASCADE` or `ON DELETE SET NULL` is specified.
6. **Explain Primary key, Candidate key, and Foreign key.** *[Teletalk Assistant Manager (IT) 2023 compact it 468 (ET: N/A)]*


   Answer:

   Primary key:
   - The candidate key chosen by the designer to identify each row of a table uniquely. It must be unique, cannot be NULL, and there is exactly one per table. It enforces entity integrity and is indexed automatically.
   - Example: `Student_ID` in `Student(Student_ID, Name, Registration_No, Dept_ID)`.

   Candidate key:
   - A minimal set of attributes that uniquely identifies a row, that is a super key from which no attribute can be removed without losing uniqueness. A relation may have several, and the designer chooses one of them as the primary key; the rest become alternate keys.
   - Example: `Student_ID` and `Registration_No` are both candidate keys of Student, since each is unique and minimal. If `Student_ID` is chosen as primary, `Registration_No` becomes an alternate key and is enforced with a UNIQUE constraint.

   Foreign key:
   - An attribute in one table whose values must match the primary key of another table. It is how a relationship between two tables is expressed, and it enforces referential integrity. It may be NULL and may repeat, and a table may have several.
   - Example: `Dept_ID` in Student, referring to `Dept_ID` in Department. A student cannot be placed in a department that does not exist, and a department cannot be deleted while students still refer to it.

   ```sql
   CREATE TABLE Department (
       Dept_ID   INT PRIMARY KEY,
       Dept_Name VARCHAR(50)
   );

   CREATE TABLE Student (
       Student_ID      INT PRIMARY KEY,        -- primary key
       Registration_No VARCHAR(20) UNIQUE,     -- alternate, that is another candidate key
       Name            VARCHAR(100) NOT NULL,
       Dept_ID         INT REFERENCES Department(Dept_ID)   -- foreign key
   );
   ```

   Relationship: primary key ⊆ candidate key ⊆ super key. The foreign key is not a key of its own table at all; it is a reference to a key of another table.
7. **(খ) Primary key এবং Super key এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 625 (ET: N/A)]*


   Answer:

   | Point | Primary Key | Super Key |
   |---|---|---|
   | Definition | The candidate key chosen to identify rows uniquely | Any attribute or set of attributes that identifies rows uniquely |
   | Minimality | Minimal; no attribute can be removed | Not necessarily minimal; it may contain redundant attributes |
   | Number per relation | Exactly one | Many; a relation with n attributes may have a very large number |
   | NULL values | Not permitted | Permitted in principle, since the concept is theoretical |
   | Selection | Chosen deliberately by the designer | Not chosen; it is any set satisfying the uniqueness property |
   | Implementation | Declared with `PRIMARY KEY` and indexed automatically | A theoretical concept, not declared in SQL |
   | Relationship | Every primary key is a super key | Not every super key is a primary key |
   | Purpose | Practical identification of rows and enforcement of entity integrity | Theoretical basis from which candidate keys and the primary key are derived |

   Example, `Student(Student_ID, Registration_No, Name, Department)`:
   - Super keys: {Student_ID}, {Registration_No}, {Student_ID, Name}, {Registration_No, Department}, {Student_ID, Registration_No, Name, Department}, and every other set containing a unique attribute.
   - Candidate keys, that is the minimal super keys: {Student_ID} and {Registration_No}.
   - Primary key: {Student_ID}, chosen from among the candidate keys.

   - The hierarchy to state: primary key ⊆ candidate key ⊆ super key. A super key becomes a candidate key when it is minimal, and a candidate key becomes the primary key when it is selected.
8. **Super key and Candidate key finding from table.** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 648 (ET: BUET)]*


   Answer: Super keys and candidate keys are found from a table by testing which sets of attributes are unique, or more reliably from the functional dependencies by computing attribute closures.

   Method:
   - Step 1: identify which single attributes are unique across all the rows. Each is a candidate key.
   - Step 2: for the remaining attributes, test pairs, then triples, until a unique combination is found. A combination is a candidate key only if no proper subset of it is already unique.
   - Step 3: every superset of a candidate key is a super key. The number of super keys is therefore large: if a relation has n attributes and {A} is a candidate key, then all 2^(n−1) subsets containing A are super keys.

   Worked example:

   | Roll | Reg_No | Name | Department |
   |---|---|---|---|
   | 101 | R-001 | Rahim | CSE |
   | 102 | R-002 | Karim | CSE |
   | 103 | R-003 | Rahim | EEE |
   | 104 | R-004 | Salma | CSE |

   - Roll: all four values are distinct, so {Roll} is unique. It is a candidate key.
   - Reg_No: all four values are distinct, so {Reg_No} is also a candidate key.
   - Name: 'Rahim' appears twice, so {Name} is not unique and cannot be a key.
   - Department: repeats, so it is not a key.
   - {Name, Department}: the pairs are (Rahim, CSE), (Karim, CSE), (Rahim, EEE), (Salma, CSE), all distinct in this instance. It is therefore unique here, but uniqueness must hold for every possible instance, not merely the one shown, so it can be treated as a candidate key only if the business rule guarantees that no two students of the same name are in the same department. This distinction is what such a question is testing.

   Candidate keys: {Roll}, {Reg_No}.

   Super keys: every set containing a candidate key, that is
   - {Roll}, {Reg_No}
   - {Roll, Reg_No}, {Roll, Name}, {Roll, Department}, {Reg_No, Name}, {Reg_No, Department}
   - {Roll, Reg_No, Name}, {Roll, Name, Department}, and so on
   - {Roll, Reg_No, Name, Department}
   - With 4 attributes and 2 single attribute candidate keys, the number of super keys is 2⁴ − number of subsets containing neither Roll nor Reg_No, that is 16 − 4 = 12.

   Finding candidate keys from functional dependencies, which is the more rigorous method:
   - Compute the closure X⁺ of each candidate set X. If X⁺ contains every attribute of the relation, X is a super key. If no proper subset of X has that property, X is a candidate key.
   - Attributes appearing only on the left of every dependency must be in every candidate key; attributes appearing only on the right can never be part of one.
9. **From Functional Dependency for determine candidate key.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 661 (ET: N/A)]*


   Answer: Candidate keys are found from a set of functional dependencies by computing attribute closures.

   Method:
   - Step 1: classify the attributes. An attribute that appears only on the left hand side of the dependencies, or in none of them, must belong to every candidate key. An attribute that appears only on the right hand side can never belong to a candidate key.
   - Step 2: compute the closure of the set of essential attributes found in step 1. If that closure already contains every attribute of the relation, it is the only candidate key and the work is finished.
   - Step 3: otherwise, add the remaining attributes one at a time, and to each resulting set, and compute the closure of each. Any set whose closure is the whole relation is a super key; it is a candidate key if no proper subset of it is already a super key.

   Closure algorithm: to compute X⁺, start with X, and repeatedly, for every dependency A → B in which A is already contained in the current set, add B. Stop when nothing more can be added.

   Worked example: R(A, B, C, D, E) with F = {A → BC, CD → E, B → D, E → A}.

   - Step 1: attribute A appears on both sides, B on both, C on both, D on both, E on both. No attribute is confined to one side, so no attribute is forced into or excluded from every key.
   - Step 2, test single attributes:
   - A⁺ = A, then A → BC gives {A, B, C}; B → D gives {A, B, C, D}; CD → E gives {A, B, C, D, E}. So A⁺ = ABCDE and {A} is a candidate key.
   - B⁺ = B, then B → D gives {B, D}. Nothing more applies, so B⁺ = BD. Not a key.
   - C⁺ = C. Not a key.
   - D⁺ = D. Not a key.
   - E⁺ = E, then E → A gives {E, A}; A → BC gives {E, A, B, C}; B → D gives everything. So E⁺ = ABCDE and {E} is a candidate key.
   - Step 3, test pairs that do not contain A or E:
   - BC⁺ = {B, C}, then B → D gives {B, C, D}; CD → E gives {B, C, D, E}; E → A gives everything. So {B, C} is a candidate key, and neither {B} nor {C} alone is, so it is minimal.
   - CD⁺ = {C, D}, then CD → E gives {C, D, E}; E → A gives {A, C, D, E}; A → BC gives everything. So {C, D} is a candidate key.
   - BD⁺ = {B, D}. Not a key.

   Candidate keys: {A}, {E}, {B, C}, {C, D}.

   - Prime attributes, that is those appearing in some candidate key: A, B, C, D, E. Here all five are prime.
   - Any superset of a candidate key is a super key.
   - The result is used directly in normalisation: 2NF requires that no non-prime attribute is partially dependent on a candidate key, and 3NF that none is transitively dependent.
10. **Relation to find primary key, candidate key, super key.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 663 (ET: N/A)]*


   Answer: The three kinds of key are found from a relation by testing which sets of attributes uniquely identify a row.

   Definitions:
   - Super key: any set of attributes that uniquely identifies a row; it may contain redundant attributes.
   - Candidate key: a minimal super key, from which no attribute can be removed without losing uniqueness.
   - Primary key: the candidate key chosen by the designer.

   Worked example, `Employee(Emp_ID, NID, Email, Name, Dept)`:

   | Emp_ID | NID | Email | Name | Dept |
   |---|---|---|---|---|
   | 101 | 1234567890 | rahim@x.com | Rahim | IT |
   | 102 | 2345678901 | karim@x.com | Karim | IT |
   | 103 | 3456789012 | salma@x.com | Salma | HR |

   Step 1, test single attributes for uniqueness:
   - Emp_ID: all distinct, so it is a candidate key.
   - NID: all distinct, and a national identity number is unique by definition, so it is a candidate key.
   - Email: all distinct, and an email address is unique in practice, so it is a candidate key.
   - Name and Dept: not unique, so neither can be a key.

   Step 2, candidate keys: {Emp_ID}, {NID}, {Email}. Each is unique and minimal.

   Step 3, primary key: {Emp_ID} is chosen, because it is short, numeric, stable and controlled by the organisation. NID and Email become alternate keys, enforced with UNIQUE constraints. Email in particular is a poor primary key, because a person may change it.

   Step 4, super keys: every set containing at least one candidate key.
   - {Emp_ID}, {NID}, {Email}
   - {Emp_ID, Name}, {NID, Dept}, {Email, Name}, {Emp_ID, NID}, and so on
   - {Emp_ID, NID, Email, Name, Dept}, the whole relation
   - Counting: with 5 attributes and 3 single attribute candidate keys, the super keys are all subsets except those containing none of Emp_ID, NID or Email. There are 2² = 4 such subsets, taken from {Name, Dept}, so the number of super keys is 32 − 4 = 28.

   ```sql
   CREATE TABLE Employee (
       Emp_ID INT PRIMARY KEY,
       NID    VARCHAR(20) UNIQUE NOT NULL,
       Email  VARCHAR(100) UNIQUE,
       Name   VARCHAR(100) NOT NULL,
       Dept   VARCHAR(50)
   );
   ```

   - Caution worth stating: uniqueness must hold for every possible instance of the relation, not merely for the rows that happen to be present. A column that looks unique in a sample may not be unique in general, so the business rules must be consulted rather than the data alone.
11. **(a) Differentiate among foreign key, candidate key, and primary key.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 694 (ET: N/A)]*


   Answer:

   | Point | Candidate Key | Primary Key | Foreign Key |
   |---|---|---|---|
   | Definition | A minimal set of attributes that uniquely identifies a row | The candidate key chosen to identify rows | An attribute referring to the primary key of another table |
   | Minimality | Minimal by definition | Minimal, being a candidate key | Not applicable |
   | Uniqueness | Unique | Unique | May repeat |
   | NULL | Permitted in theory | Never permitted | Permitted unless declared NOT NULL |
   | Number per table | One or more | Exactly one | Any number |
   | Chosen by | Determined by the data and the business rules | Selected by the designer from the candidate keys | Determined by the relationship being modelled |
   | Purpose | Identifies the possible identifiers | Entity integrity | Referential integrity |
   | Index | Created if declared UNIQUE | Created automatically | Not automatic; should be added manually |
   | Belongs to | Its own table | Its own table | Its own table, but refers to another |

   Relationship:
   - primary key ⊆ candidate key ⊆ super key. The candidate keys are all the minimal identifiers available; the primary key is the one selected; the remainder become alternate keys.
   - A foreign key is of a different character altogether. It is not an identifier of its own table but a pointer to another table's identifier, and it is what turns a set of independent tables into a related database.

   Example:

   ```sql
   CREATE TABLE Department (
       Dept_ID   INT PRIMARY KEY,
       Dept_Name VARCHAR(50) UNIQUE NOT NULL
   );

   CREATE TABLE Student (
       Student_ID      INT PRIMARY KEY,       -- primary key, chosen
       Registration_No VARCHAR(20) UNIQUE,    -- candidate key, now alternate
       NID             VARCHAR(20) UNIQUE,    -- candidate key, now alternate
       Name            VARCHAR(100) NOT NULL,
       Dept_ID         INT REFERENCES Department(Dept_ID)  -- foreign key
   );
   ```
12. **Explain the primary key and composite key with respect to database.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 745 (ET: N/A)]*


   Answer:

   Primary key:
   - The attribute or set of attributes chosen to identify each row of a table uniquely. It must be unique, it cannot be NULL, and a table has exactly one. It enforces entity integrity and is indexed automatically by the DBMS.
   - Example: `Student_ID` in `Student(Student_ID, Name, Department)`.

   Composite key:
   - A composite key, also called a compound key, is a primary key made up of two or more attributes taken together, used when no single attribute is unique on its own but the combination is.
   - Every attribute of a composite key must be NOT NULL, and the uniqueness applies to the combination rather than to any individual column.

   Example of a composite key:

   ```sql
   CREATE TABLE Enrollment (
       Student_ID INT,
       Course_ID  INT,
       Semester   VARCHAR(20),
       Grade      CHAR(2),
       PRIMARY KEY (Student_ID, Course_ID, Semester),
       FOREIGN KEY (Student_ID) REFERENCES Student(Student_ID),
       FOREIGN KEY (Course_ID)  REFERENCES Course(Course_ID)
   );
   ```

   - Neither `Student_ID` nor `Course_ID` alone is unique in this table: a student takes many courses and a course has many students. The combination of the two, together with the semester, is unique, because a given student takes a given course once in a given semester.
   - This arrangement arises naturally whenever a many to many relationship is converted into a table, which is why composite keys are common in junction tables.

   Relationship between the two:
   - A composite key is a kind of primary key, not an alternative to it. Every primary key is either simple, consisting of one attribute, or composite, consisting of several.

   Practical consideration:
   - A composite key can become cumbersome when it must be referenced by other tables, since every referencing table must carry all its columns. For this reason designers often add a surrogate key, such as an auto-incremented `Enrollment_ID`, as the primary key, and keep a UNIQUE constraint on the natural composite key to preserve the business rule. Both approaches are correct, and the trade-off should be stated.
13. **(খ) Relational Database Design এ Primary Key ও Foreign Key বলতে কি বুঝায়? উদাহরণসহ লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 769 (ET: N/A)]*


   Answer:

   Primary key:
   - A primary key is the attribute or set of attributes chosen to identify each row of a table uniquely. It must be unique, it cannot contain NULL, and each table has exactly one. The DBMS creates an index on it automatically, so lookups by the key are fast. It enforces entity integrity, that is the rule that every row must be identifiable.

   Foreign key:
   - A foreign key is an attribute in one table whose values must match the primary key of another table. It is the mechanism by which a relationship between two tables is represented, and it enforces referential integrity, that is the rule that a reference must point to something that exists.
   - It may be NULL, meaning that no relationship exists for that row, and it may repeat, since many rows may refer to the same parent. A table may have several foreign keys.

   Example:

   ```sql
   CREATE TABLE Department (
       Dept_ID   INT PRIMARY KEY,
       Dept_Name VARCHAR(50) NOT NULL
   );

   CREATE TABLE Employee (
       Emp_ID   INT PRIMARY KEY,               -- primary key
       Emp_Name VARCHAR(100) NOT NULL,
       Salary   DECIMAL(10,2),
       Dept_ID  INT,                           -- foreign key
       FOREIGN KEY (Dept_ID) REFERENCES Department(Dept_ID)
           ON DELETE SET NULL
           ON UPDATE CASCADE
   );
   ```

   What this achieves:
   - `Emp_ID` guarantees that every employee row is distinct and identifiable.
   - `Dept_ID` in Employee can only hold a value that exists in Department, so an employee cannot be assigned to a department that does not exist.
   - `ON DELETE SET NULL` means that if a department is deleted, its employees remain but their `Dept_ID` becomes NULL. The alternatives are `ON DELETE RESTRICT`, which is the default and refuses the deletion, and `ON DELETE CASCADE`, which deletes the employees too.
   - `ON UPDATE CASCADE` means that if a department's identifier is changed, the change propagates automatically to the employees.

   | Point | Primary Key | Foreign Key |
   |---|---|---|
   | Purpose | Uniquely identifies each row of its own table | Links a row to a row of another table |
   | Uniqueness | Must be unique | May repeat |
   | NULL values | Not permitted | Permitted, unless declared NOT NULL |
   | Number per table | Exactly one | Any number |
   | Index | Created automatically | Not created automatically in most systems; should be created manually |
   | References | Nothing; it is referenced | The primary key or a unique key of another table |
   | Deletion | A row cannot be deleted while a foreign key refers to it, unless CASCADE is specified | Deleting the child row affects nothing else |
   | What it enforces | Entity integrity | Referential integrity |
   | Constraint syntax | `PRIMARY KEY (col)` | `FOREIGN KEY (col) REFERENCES Parent(col)` |

   Example:

   ```sql
   CREATE TABLE Department (
       Dept_ID   INT PRIMARY KEY,
       Dept_Name VARCHAR(50) NOT NULL
   );

   CREATE TABLE Employee (
       Emp_ID   INT PRIMARY KEY,              -- primary key of Employee
       Emp_Name VARCHAR(100) NOT NULL,
       Dept_ID  INT,                          -- foreign key
       FOREIGN KEY (Dept_ID) REFERENCES Department(Dept_ID)
   );
   ```

   - `Emp_ID` uniquely identifies each employee, which is entity integrity.
   - `Dept_ID` in Employee must match some `Dept_ID` in Department, which is referential integrity. An employee cannot be placed in a department that does not exist, and a department cannot be deleted while employees still refer to it, unless `ON DELETE CASCADE` or `ON DELETE SET NULL` is specified.
14. **(b) What are purpose of using foreign key in a database? Give suitable example.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 802 (ET: N/A)]*


   Answer: The purpose of a foreign key is to represent a relationship between two tables and to enforce referential integrity, that is the rule that a reference must always point to a row that actually exists.

   Purposes:
   - Establishing relationships: a foreign key is how a one to many relationship is represented in a relational database. Without it the tables would be independent and the connection between them would exist only in the mind of the programmer.
   - Referential integrity: the DBMS refuses to insert or update a row whose foreign key value does not exist in the parent table, so orphan records cannot be created. This is enforced centrally, whatever any application does.
   - Controlled deletion and update: `ON DELETE RESTRICT` prevents a parent from being deleted while children refer to it; `ON DELETE CASCADE` deletes the children with it; `ON DELETE SET NULL` leaves the children but severs the link. `ON UPDATE CASCADE` propagates a change of key value automatically.
   - Documenting the design: the constraints make the structure of the database self describing, so a new developer can see how the tables relate without consulting a document.
   - Enabling the optimiser: the query planner uses the declared relationship to choose better join strategies.
   - Supporting joins naturally, since the foreign key names the column on which the tables should be joined.

   Example:

   ```sql
   CREATE TABLE Customer (
       Customer_ID INT PRIMARY KEY,
       Name        VARCHAR(100) NOT NULL,
       Phone       VARCHAR(20)
   );

   CREATE TABLE Orders (
       Order_ID    INT PRIMARY KEY,
       Order_Date  DATE NOT NULL,
       Amount      DECIMAL(10,2),
       Customer_ID INT NOT NULL,
       FOREIGN KEY (Customer_ID) REFERENCES Customer(Customer_ID)
           ON DELETE RESTRICT
   );
   ```

   What the constraint prevents:
   - `INSERT INTO Orders VALUES (5, '2025-01-10', 500, 99);` fails if customer 99 does not exist, so an order can never belong to a non-existent customer.
   - `DELETE FROM Customer WHERE Customer_ID = 1;` fails if that customer has orders, so the order history cannot be silently orphaned.
   - `NOT NULL` on `Customer_ID` additionally enforces total participation: every order must belong to a customer.

   Practical note: a foreign key is not indexed automatically in most database systems, although the primary key it refers to is. An index should be created on the foreign key column, otherwise every deletion from the parent table requires a full scan of the child table to check the constraint.
15. **What is primary key?** *[BCC CA Monitoring System Project 2021 compact it 829 (ET: N/A)]*


   Answer: A primary key is the attribute or set of attributes chosen to identify each row of a table uniquely.

   Properties:
   - Uniqueness: no two rows may have the same value. This is what makes every row identifiable.
   - Not NULL: it can never be empty, because a row that cannot be identified has no place in a relation.
   - Exactly one per table: a table may have several candidate keys, but only one of them is designated the primary key.
   - Minimal: it contains no attribute that is not needed for uniqueness, since it is a candidate key.
   - Immutable in practice: it should be chosen so that its value never needs to change, because changing it would require every referencing foreign key to be changed too.
   - Indexed automatically by the DBMS, so lookups by the key are fast.
   - It enforces entity integrity, which is one of the two fundamental integrity rules of the relational model.
   - It is the target of foreign keys in other tables, and therefore the basis of every relationship.

   Types: simple, consisting of one attribute; composite, consisting of several attributes together; natural, drawn from real data such as a national identity number; and surrogate, an artificial value such as an auto-incremented integer with no business meaning.

   ```sql
   CREATE TABLE Student (
       Student_ID INT PRIMARY KEY,
       Name       VARCHAR(100) NOT NULL,
       Department VARCHAR(50)
   );

   -- Composite primary key
   CREATE TABLE Enrollment (
       Student_ID INT,
       Course_ID  INT,
       Grade      CHAR(2),
       PRIMARY KEY (Student_ID, Course_ID)
   );
   ```

   Choosing a primary key: it should be stable, short, simple, never NULL and preferably numeric. Where no natural attribute satisfies these conditions, a surrogate key is created. An email address or a telephone number is a poor choice, because a person may change either.
16. **What is Primary key, Unique key and Forgein key.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*


   Answer:

   Primary key:
   - The attribute or set of attributes chosen to identify each row uniquely. It must be unique, cannot be NULL, and there is exactly one per table. It is indexed automatically and enforces entity integrity.

   Unique key:
   - A constraint that guarantees the values of a column or a combination of columns are distinct, but which is not the primary key. It is used for the alternate keys, that is the candidate keys not chosen as primary.
   - The essential difference from the primary key is that a unique key permits NULL, and in most systems permits one NULL value, because NULL is not equal to anything including another NULL.

   Foreign key:
   - An attribute whose values must match the primary key or a unique key of another table. It represents the relationship between the tables and enforces referential integrity. It may be NULL and may repeat.

   Comparison:

   | Point | Primary Key | Unique Key | Foreign Key |
   |---|---|---|---|
   | Uniqueness | Enforced | Enforced | Not enforced; values may repeat |
   | NULL permitted | No | Yes, generally one | Yes |
   | Number per table | Exactly one | Any number | Any number |
   | Index | Clustered index created automatically in most systems | Non-clustered unique index created | None automatically |
   | Purpose | Identifies rows, entity integrity | Prevents duplicates in a non-key column | Links tables, referential integrity |
   | Can be referenced by a foreign key | Yes | Yes | Not applicable |

   Example:

   ```sql
   CREATE TABLE Department (
       Dept_ID   INT PRIMARY KEY,
       Dept_Name VARCHAR(50) NOT NULL
   );

   CREATE TABLE Employee (
       Emp_ID  INT PRIMARY KEY,                  -- primary key
       Email   VARCHAR(100) UNIQUE,              -- unique key, may be NULL
       NID     VARCHAR(20) UNIQUE NOT NULL,      -- unique key, made compulsory
       Name    VARCHAR(100) NOT NULL,
       Dept_ID INT REFERENCES Department(Dept_ID) -- foreign key
   );
   ```

   - `Email` is unique but optional: two employees cannot share an address, but an employee may have none.
   - `NID` is unique and compulsory, which makes it effectively a second primary key, an alternate key.
   - `Dept_ID` may repeat, since many employees belong to one department, and may be NULL for an unassigned employee.
17. **Database Management System (DBMS) বলতে কী বোঝেন? Relational database -এ Primary key এবং Foreign key -এর ভূমিকা উদাহরণসহ সংক্ষেপে বর্ণনা করুন?** *[41th BCS 2021 compact it 882 (ET: N/A)]*


   Answer:

   What a DBMS is:
   - A Database Management System is software that allows users to define, create, store, retrieve, update and manage data in a database, and that controls access to it. It sits between the physical stored data and the users and applications, so that no program needs to know how the data is actually held.
   - Its main functions: data definition, data manipulation through SQL, transaction management with the ACID properties, concurrency control, security and authorisation, backup and recovery, enforcement of integrity constraints, and maintenance of the data dictionary.
   - Its benefits over file based storage: control of redundancy, enforced consistency and integrity, controlled sharing by many users, security, recovery after failure, and data independence.
   - Examples: Oracle, MySQL, PostgreSQL, Microsoft SQL Server, MongoDB.

   Role of the primary key in a relational database:
   - It uniquely identifies every row of a table, so that any particular record can be found, updated or deleted without ambiguity.
   - It enforces entity integrity: it cannot be NULL and cannot be duplicated, so no row is unidentifiable and no two rows are indistinguishable.
   - It is indexed automatically, so lookups by the key are fast.
   - It is the anchor for relationships: every foreign key in the database points at some table's primary key.

   Role of the foreign key:
   - It represents the relationship between two tables, which is what turns a set of independent tables into a database.
   - It enforces referential integrity: a value in the foreign key column must exist in the referenced table, so orphan rows cannot be created.
   - It controls what happens on deletion and update of the parent through CASCADE, RESTRICT or SET NULL.
   - It documents the design, so that the structure of the database is self describing.

   Example:

   ```sql
   CREATE TABLE Department (
       Dept_ID   INT PRIMARY KEY,
       Dept_Name VARCHAR(50) NOT NULL
   );

   CREATE TABLE Employee (
       Emp_ID   INT PRIMARY KEY,
       Emp_Name VARCHAR(100) NOT NULL,
       Dept_ID  INT REFERENCES Department(Dept_ID)
   );
   ```

   - `Emp_ID` identifies each employee uniquely; `Dept_ID` in Employee must match a department that exists. An employee cannot be assigned to department 50 if no such department has been created, and department 10 cannot be deleted while employees still belong to it.
18. **(b) Explain the different type of database keys with examples.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)]*


   Answer: The different types of database key, with examples:

   - Super key: any attribute or set of attributes that uniquely identifies a row. It may contain extra attributes that are not needed for uniqueness. It is the widest category, and every other key is a super key.
   - Candidate key: a minimal super key, that is a super key from which no attribute can be removed without losing uniqueness. A relation may have several candidate keys.
   - Primary key: the one candidate key chosen by the designer to identify rows. It cannot be NULL and cannot contain duplicates, and a table has exactly one.
   - Alternate key: any candidate key not chosen as the primary key. It is normally enforced with a UNIQUE constraint.
   - Composite key: a key made up of two or more attributes together, because no single attribute is unique.
   - Foreign key: an attribute in one table whose values must match the primary key of another table, which is how a relationship between tables is expressed. It may be NULL and may contain duplicates.
   - Unique key: a constraint guaranteeing uniqueness that is not the primary key. Unlike the primary key it permits one NULL value.
   - Surrogate key: an artificial key with no business meaning, such as an auto-incremented number, used when no natural attribute is a satisfactory identifier.

   Example, a Student relation:

   ```
   Student(Student_ID, Registration_No, NID, Name, Department, Dept_ID)
   ```

   - Super keys: {Student_ID}, {Registration_No}, {NID}, {Student_ID, Name}, {Registration_No, Department} and so on, since adding attributes to a unique set keeps it unique.
   - Candidate keys: {Student_ID}, {Registration_No}, {NID}, each of which is unique and minimal.
   - Primary key: Student_ID, chosen by the designer.
   - Alternate keys: Registration_No and NID.
   - Foreign key: Dept_ID, referring to Department(Dept_ID).
   - Composite key example: in `Enrollment(Student_ID, Course_ID, Grade)` the primary key is the pair (Student_ID, Course_ID), since neither alone is unique.

   Relationship between them: every candidate key is a super key, and the primary key is one of the candidate keys. So primary key ⊆ candidate key ⊆ super key.

   Declaration in SQL:

   ```sql
   CREATE TABLE Department (
       Dept_ID   INT PRIMARY KEY,
       Dept_Name VARCHAR(50) UNIQUE NOT NULL
   );

   CREATE TABLE Student (
       Student_ID      INT PRIMARY KEY,                    -- primary key
       Registration_No VARCHAR(20) UNIQUE,                 -- alternate key
       NID             VARCHAR(20) UNIQUE,                 -- alternate key
       Name            VARCHAR(100) NOT NULL,
       Dept_ID         INT REFERENCES Department(Dept_ID)  -- foreign key
   );

   CREATE TABLE Enrollment (
       Student_ID INT REFERENCES Student(Student_ID),
       Course_ID  INT,
       Grade      CHAR(2),
       PRIMARY KEY (Student_ID, Course_ID)                 -- composite key
   );
   ```
19. **What is the Primary key, Candidate key and Super key?** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 921 (ET: N/A)]*


   Answer:

   Super key:
   - Any attribute or set of attributes whose values uniquely identify a row of a relation. It may include attributes that are not needed for uniqueness, so it need not be minimal.
   - It is the broadest category: every candidate key and every primary key is also a super key.

   Candidate key:
   - A minimal super key, that is a super key from which no attribute can be removed without losing the uniqueness property.
   - A relation may have several candidate keys, and each is a genuine alternative identifier.

   Primary key:
   - The one candidate key selected by the designer to be the principal identifier of rows. It must be unique and not NULL, there is exactly one per table, and it is indexed automatically.
   - The candidate keys not selected are called alternate keys and are enforced with UNIQUE constraints.

   Example, `Student(Student_ID, Registration_No, NID, Name, Department)`:
   - Candidate keys: {Student_ID}, {Registration_No}, {NID}, since each is unique and minimal.
   - Primary key: {Student_ID}, chosen because it is short, numeric, stable and controlled by the institution.
   - Alternate keys: {Registration_No} and {NID}.
   - Super keys: all of the above, and every set containing one of them, such as {Student_ID, Name}, {NID, Department} and the whole relation. With 5 attributes and 3 single attribute candidate keys, there are 2⁵ − 2² = 28 super keys.

   Relationship, which is the point of the question:
   - primary key ⊆ candidate key ⊆ super key.
   - A super key becomes a candidate key when it is minimal, and a candidate key becomes the primary key when the designer selects it.
20. **Difference between Primary key and Unique Key, Drop and Purge, Delete and Truncate.** *[RAKUB Assistant Database Administrator 2020 compact it 1013-1014 (ET: E-Zone)]*


   Answer:

   Primary key vs Unique key:

   | Point | Primary Key | Unique Key |
   |---|---|---|
   | NULL values | Never permitted | Permitted, generally one NULL |
   | Number per table | Exactly one | Any number |
   | Index created | Clustered index in most systems | Non-clustered unique index |
   | Purpose | Identifies each row; entity integrity | Prevents duplicate values in a non-key column |
   | Role | The chosen identifier | Enforces an alternate key |
   | Referenced by a foreign key | Yes, normally | Yes, it may also be referenced |

   DROP vs PURGE:

   | Point | DROP | PURGE |
   |---|---|---|
   | Effect | Removes the table from the database | Permanently removes an object already in the recycle bin |
   | Recoverability | Recoverable, since the table goes to the recycle bin in Oracle and can be restored with FLASHBACK | Not recoverable at all |
   | Space | Space is not released immediately | Space is released immediately |
   | Syntax | `DROP TABLE employee;` | `PURGE TABLE employee;` or `DROP TABLE employee PURGE;` |
   | Availability | Every DBMS | Chiefly Oracle, which has the recycle bin concept |

   DELETE vs TRUNCATE:

   | Point | DELETE | TRUNCATE |
   |---|---|---|
   | Command type | DML, Data Manipulation Language | DDL, Data Definition Language |
   | Rows removed | Selected rows, or all if no WHERE clause | All rows, always |
   | WHERE clause | Permitted | Not permitted |
   | Transaction log | Each row is logged individually | Only the page deallocations are logged |
   | Speed | Slow on a large table | Very fast |
   | Rollback | Can be rolled back | Cannot be rolled back in most systems, since it is DDL and is auto-committed |
   | Triggers | DELETE triggers fire | Triggers do not fire |
   | Identity or auto-increment counter | Not reset | Reset to the initial value |
   | Space reclaimed | Not immediately | Immediately |
   | Foreign key references | Permitted | Refused if the table is referenced by a foreign key |

   - The practical rule: use DELETE when specific rows must be removed or when the operation must be reversible; use TRUNCATE to empty a large table quickly when nothing is to be preserved; and use DROP when the table itself is no longer required.
21. **Example Foreign key in RDBMS.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1035 (ET: BUET)]*


   Answer: A foreign key is an attribute in one table whose values must match the primary key of another table, which is how a relationship between the two is represented and how referential integrity is enforced.

   Example:

   ```sql
   -- Parent table
   CREATE TABLE Department (
       Dept_ID   INT PRIMARY KEY,
       Dept_Name VARCHAR(50) NOT NULL
   );

   -- Child table with a foreign key
   CREATE TABLE Employee (
       Emp_ID   INT PRIMARY KEY,
       Emp_Name VARCHAR(100) NOT NULL,
       Salary   DECIMAL(10,2),
       Dept_ID  INT,
       CONSTRAINT fk_employee_dept
           FOREIGN KEY (Dept_ID) REFERENCES Department(Dept_ID)
           ON DELETE SET NULL
           ON UPDATE CASCADE
   );
   ```

   Sample data:

   | Department | | | Employee | | |
   |---|---|---|---|---|---|
   | Dept_ID | Dept_Name | | Emp_ID | Emp_Name | Dept_ID |
   | 10 | IT | | 1 | Rahim | 10 |
   | 20 | Finance | | 2 | Karim | 10 |
   | 30 | HR | | 3 | Salma | 20 |
   | | | | 4 | Jamal | NULL |

   What the constraint enforces:
   - `INSERT INTO Employee VALUES (5, 'Nadia', 50000, 99);` is refused, because no department 99 exists. This is the prevention of an orphan row.
   - `DELETE FROM Department WHERE Dept_ID = 10;` sets the `Dept_ID` of Rahim and Karim to NULL, because of `ON DELETE SET NULL`. Without any action clause the default is RESTRICT, which would refuse the deletion; `ON DELETE CASCADE` would delete both employees.
   - `UPDATE Department SET Dept_ID = 15 WHERE Dept_ID = 10;` changes the employees' `Dept_ID` to 15 automatically, because of `ON UPDATE CASCADE`.
   - Employee 4 has a NULL `Dept_ID`, which is permitted, and means the employee is not yet assigned to any department. Adding `NOT NULL` would forbid this and enforce total participation.

   Practical note: create an index on the foreign key column. It is not created automatically, and without it every deletion from the parent table requires a full scan of the child table to verify the constraint.

## Normalization & Database Design (18)

1. **What is Normalization? How do 1NF and 2NF work in a database? Give examples.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*


   Answer:

   What normalisation is:
   - Normalisation is the process of organising the tables and columns of a relational database so as to reduce data redundancy and eliminate the update, insertion and deletion anomalies that redundancy causes. It was introduced by E. F. Codd.
   - It proceeds by decomposing a large table into smaller related tables, in such a way that no information is lost and the original can be reconstructed by joining them.

   Why it is needed, that is the anomalies it removes:
   - Update anomaly: the same fact stored in many rows must be changed in every one of them; if one is missed, the data becomes inconsistent.
   - Insertion anomaly: a fact cannot be recorded because other, unrelated, information is not yet available. For example a new department cannot be recorded until an employee is assigned to it.
   - Deletion anomaly: deleting one fact accidentally destroys another. For example deleting the last employee of a department destroys the record of the department itself.
   - It also saves storage, makes the design clearer, and makes constraints easier to enforce.

   The normal forms:

   First Normal Form, 1NF:
   - Every attribute must hold a single atomic value; no repeating groups, no multivalued attributes and no arrays.
   - Each row must be unique, that is the table must have a primary key.
   - Violation: `Student(Roll, Name, Subjects)` where Subjects holds 'Math, Physics, Chemistry'.
   - Remedy: place each value in its own row, or move the multivalued attribute to a separate table: `Student(Roll, Name)` and `Student_Subject(Roll, Subject)`.

   Second Normal Form, 2NF:
   - The relation must be in 1NF, and every non-prime attribute must be fully functionally dependent on the whole primary key, not on part of it. Partial dependency is not permitted.
   - It only arises when the primary key is composite; a table with a single attribute key is automatically in 2NF once it is in 1NF.
   - Violation: `Enrollment(Student_ID, Course_ID, Student_Name, Course_Name, Grade)` with the key (Student_ID, Course_ID). Here Student_Name depends only on Student_ID and Course_Name only on Course_ID, both of which are partial dependencies.
   - Remedy: decompose into `Student(Student_ID, Student_Name)`, `Course(Course_ID, Course_Name)` and `Enrollment(Student_ID, Course_ID, Grade)`.


   - Higher forms are 3NF, which removes transitive dependency; BCNF, which is a stricter version of 3NF; and 4NF and 5NF, which remove multivalued and join dependencies.

   Worked example of 1NF:

   Unnormalised, violating 1NF because Subjects holds several values in one field:

   | Roll | Name | Subjects |
   |---|---|---|
   | 101 | Rahim | Math, Physics |
   | 102 | Karim | Chemistry |

   In 1NF, each field holding a single atomic value:

   | Roll | Name | Subject |
   |---|---|---|
   | 101 | Rahim | Math |
   | 101 | Rahim | Physics |
   | 102 | Karim | Chemistry |

   Worked example of 2NF:

   In 1NF but violating 2NF, since the key is (Roll, Subject) and Name depends only on Roll, which is a partial dependency:

   | Roll | Subject | Name | Marks |
   |---|---|---|---|
   | 101 | Math | Rahim | 85 |
   | 101 | Physics | Rahim | 78 |
   | 102 | Chemistry | Karim | 90 |

   In 2NF, decomposed so that every non-key attribute depends on the whole key:

   ```
   Student(Roll, Name)
     101, Rahim
     102, Karim

   Result(Roll, Subject, Marks)
     101, Math, 85
     101, Physics, 78
     102, Chemistry, 90
   ```

   - The improvement: Rahim's name is now stored once rather than twice, so it cannot be updated inconsistently; a student can be recorded before any result exists; and deleting a result does not destroy the student's record.
2. **Why normalization is required in Database? Write shortly about 3NF?** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1350 (ET: N/A)]*


   Answer:

   Why normalisation is required:
   - To eliminate data redundancy, so that the same fact is not stored in many places.
   - To remove the update anomaly: if a fact is repeated in fifty rows, changing it requires fifty updates, and missing one leaves the database inconsistent.
   - To remove the insertion anomaly: a new department should be recordable before any employee is assigned to it, which an unnormalised design prevents.
   - To remove the deletion anomaly: deleting the last employee of a department should not destroy the record of the department.
   - To save storage space.
   - To make the design clearer and easier to extend, since each table then describes one kind of thing.
   - To make integrity constraints easier to define and enforce.

   Third Normal Form:
   - A relation is in 3NF if it is in 2NF and no non-prime attribute is transitively dependent on the primary key. Equivalently, for every non-trivial functional dependency X → Y, either X is a super key or Y is a prime attribute.
   - A transitive dependency exists when a non-key attribute determines another non-key attribute, so that the second depends on the key only through the first.

   Example of a violation:

   | Emp_ID | Emp_Name | Dept_ID | Dept_Name | Dept_Location |
   |---|---|---|---|---|
   | 1 | Rahim | 10 | IT | Dhaka |
   | 2 | Karim | 10 | IT | Dhaka |
   | 3 | Salma | 20 | Finance | Chattogram |

   - The dependencies are Emp_ID → Dept_ID and Dept_ID → Dept_Name, Dept_Location. So Emp_ID → Dept_Name transitively, through Dept_ID, which is not a key. This violates 3NF.
   - The consequences: the IT department's name and location are repeated for every employee, so renaming the department requires many updates; a new department cannot be recorded until it has an employee; and deleting the last employee of Finance destroys all record of that department.

   Decomposition into 3NF:

   ```
   Employee(Emp_ID, Emp_Name, Dept_ID)
     1, Rahim, 10
     2, Karim, 10
     3, Salma, 20

   Department(Dept_ID, Dept_Name, Dept_Location)
     10, IT, Dhaka
     20, Finance, Chattogram
   ```

   - Each department's details are now stored exactly once, all three anomalies disappear, and the original table can be recovered exactly by joining on Dept_ID, so the decomposition is lossless.
   - 3NF is the usual target for a transactional database, because it removes almost all redundancy while keeping the number of joins reasonable.
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

   Second Normal Form:
   - A relation is in 2NF if it is in 1NF and every non-prime attribute is fully functionally dependent on the whole of the primary key, that is there is no partial dependency on a proper subset of a composite key.
   - It arises only when the primary key is composite. A relation whose key is a single attribute is automatically in 2NF once it is in 1NF.

   Third Normal Form:
   - A relation is in 3NF if it is in 2NF and no non-prime attribute is transitively dependent on the primary key, that is no non-key attribute determines another non-key attribute.

   Difference:

   | Point | 2NF | 3NF |
   |---|---|---|
   | Prerequisite | Must be in 1NF | Must be in 2NF |
   | Dependency removed | Partial dependency on part of a composite key | Transitive dependency through a non-key attribute |
   | When it can be violated | Only when the primary key is composite | Even when the key is a single attribute |
   | Formal condition | Every non-prime attribute is fully dependent on every candidate key | For every X → Y, either X is a super key or Y is prime |
   | Strength | Stronger than 1NF, weaker than 3NF | Stronger than both |
   | Effect | Removes redundancy caused by part of the key | Removes redundancy caused by non-key attributes determining each other |

   Example of a 2NF violation:

   `Enrollment(Student_ID, Course_ID, Student_Name, Course_Name, Grade)` with the key (Student_ID, Course_ID).

   | Student_ID | Course_ID | Student_Name | Course_Name | Grade |
   |---|---|---|---|---|
   | 101 | C1 | Rahim | Database | A |
   | 101 | C2 | Rahim | Networks | B |
   | 102 | C1 | Karim | Database | A |

   - Student_Name depends only on Student_ID and Course_Name only on Course_ID; both are partial dependencies on part of the composite key.
   - Decomposition into 2NF: `Student(Student_ID, Student_Name)`, `Course(Course_ID, Course_Name)`, `Enrollment(Student_ID, Course_ID, Grade)`.

   Example of a 3NF violation:

   `Employee(Emp_ID, Emp_Name, Dept_ID, Dept_Name)` with the key Emp_ID.

   | Emp_ID | Emp_Name | Dept_ID | Dept_Name |
   |---|---|---|---|
   | 1 | Rahim | 10 | IT |
   | 2 | Karim | 10 | IT |
   | 3 | Salma | 20 | Finance |

   - The key is a single attribute, so the relation is already in 2NF. But Emp_ID → Dept_ID and Dept_ID → Dept_Name, so Dept_Name depends on the key only transitively.
   - Decomposition into 3NF: `Employee(Emp_ID, Emp_Name, Dept_ID)` and `Department(Dept_ID, Dept_Name)`.

   - The essential distinction: 2NF is concerned with dependency on part of the key, and therefore arises only with composite keys; 3NF is concerned with dependency through a non-key attribute, and can arise with any key.
4. **What is Logical design database is called?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: The logical design of a database is called the schema, and more precisely the conceptual schema or logical schema.

   - The logical design describes what data is stored and how it is structured — the tables, their columns and data types, the primary and foreign keys, the relationships and the constraints — without any reference to how it is physically stored.
   - It is the second of the three stages of database design:
   - Conceptual design produces the E-R model, which is independent of any DBMS.
   - Logical design converts that model into a relational schema of tables and keys, normalised to an appropriate form. This is where the schema is produced.
   - Physical design decides how it is actually stored: file organisation, indexes, partitioning and placement.
   - In the three level ANSI/SPARC architecture, the logical design corresponds to the conceptual level, which sits between the external views seen by users and the internal storage.
   - The term "schema" is also used for the whole definition written in the Data Definition Language, that is the set of CREATE TABLE statements.
   - Related term: the logical design is sometimes described as the logical data model, and the process of producing it as data modelling.
5. **A Bank schema is given below:** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1322 (ET: DU)]*
   $$\text{Bank}(\text{Br\_Name}, \text{Br\_City}, \text{Assets}, \text{Acc\_name}, \text{Acc\_Num}, \text{Balance})$$
   * (a) Provided and Normalize and point out Primary and Foreign Key?
   * (b) Show that is the schema and state that why your schema is in good form.


   Answer:

   Given schema: `Bank(Br_Name, Br_City, Assets, Acc_Name, Acc_Num, Balance)`

   (a) Normalisation, with the keys identified:

   Step 1, identify the functional dependencies:
   - Br_Name → Br_City, Assets, since a branch has one city and one asset figure.
   - Acc_Num → Balance, Br_Name, since an account has one balance and belongs to one branch.
   - Acc_Name and Acc_Num together identify a row if a customer may hold several accounts; taking Acc_Num as unique, it alone is the key of the account information.

   Step 2, identify the problems with the single table:
   - Redundancy: the city and the assets of a branch are repeated for every account held at that branch.
   - Update anomaly: if a branch's assets change, every row for that branch must be updated.
   - Insertion anomaly: a new branch cannot be recorded until an account is opened there.
   - Deletion anomaly: deleting the last account of a branch destroys the record of the branch, its city and its assets.

   Step 3, check 1NF: every attribute holds a single atomic value, so the relation is already in 1NF.

   Step 4, check 2NF and 3NF: taking Acc_Num as the key, Acc_Num → Br_Name and Br_Name → Br_City, Assets. So Br_City and Assets depend on the key only transitively, which violates 3NF.

   Step 5, decomposition into 3NF:

   ```
   Branch(Br_Name, Br_City, Assets)
       PRIMARY KEY (Br_Name)

   Account(Acc_Num, Acc_Name, Balance, Br_Name)
       PRIMARY KEY (Acc_Num)
       FOREIGN KEY (Br_Name) REFERENCES Branch(Br_Name)
   ```

   - Primary keys: `Br_Name` in Branch, and `Acc_Num` in Account.
   - Foreign key: `Br_Name` in Account, referring to Branch.
   - If a customer may hold accounts at several branches and the customer's own details are to be held separately, a third relation `Customer(Cust_ID, Acc_Name, Address)` with a link table would be added; the schema as given does not require it.

   ```sql
   CREATE TABLE Branch (
       Br_Name VARCHAR(50) PRIMARY KEY,
       Br_City VARCHAR(50) NOT NULL,
       Assets  DECIMAL(15,2)
   );

   CREATE TABLE Account (
       Acc_Num  INT PRIMARY KEY,
       Acc_Name VARCHAR(100) NOT NULL,
       Balance  DECIMAL(15,2) DEFAULT 0,
       Br_Name  VARCHAR(50) NOT NULL,
       FOREIGN KEY (Br_Name) REFERENCES Branch(Br_Name)
   );
   ```

   (b) Why this schema is in good form:
   - It is in 3NF, and in fact in BCNF, since in each relation the only determinant is the primary key. Br_Name determines everything else in Branch and is its key; Acc_Num determines everything else in Account and is its key.
   - The decomposition is lossless: joining Branch and Account on Br_Name reconstructs the original relation exactly, with no spurious rows, because Br_Name is a key of Branch.
   - It is dependency preserving: both original dependencies, Br_Name → Br_City, Assets and Acc_Num → Balance, Br_Name, are each enforceable within a single relation, so no dependency has to be checked by joining.
   - All three anomalies are removed: a branch's assets are stored once and can be updated in one place; a new branch can be created before any account exists; and closing the last account does not destroy the branch record.
   - Referential integrity is enforced by the foreign key, so an account cannot belong to a branch that does not exist.
   - Storage is reduced, since the branch details are no longer repeated per account.

   - One practical qualification: using Br_Name as a key is undesirable in a real system, because a branch may be renamed and the change would have to cascade. A surrogate `Br_ID` would be preferable, with a UNIQUE constraint on Br_Name.
6. **What is Normalize a database? Used containers if needed, draw an ER Diagram.** **[See WZPGCL, Assistant Engineer (CSE), Exam: 27.05.2023]** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 315 (ET: N/A)]*


   Answer:

   What normalising a database means:
   - Normalisation is the process of organising the tables and columns of a relational database so as to remove redundancy and eliminate the update, insertion and deletion anomalies that redundancy causes. A large table is decomposed into smaller related tables in a way that loses no information.

   Worked example, from an unnormalised table to 3NF:

   Unnormalised, a single Student table:

   | Roll | Name | Dept_ID | Dept_Name | Courses |
   |---|---|---|---|---|
   | 101 | Rahim | 10 | CSE | Database, Networks |
   | 102 | Karim | 10 | CSE | Database |
   | 103 | Salma | 20 | EEE | Circuits |

   Problems: Courses holds several values in one field, violating 1NF; the department name is repeated for every student of that department, causing an update anomaly; a new department cannot be recorded before a student joins it; and deleting the last student of EEE destroys the record of the department.

   1NF, by making every value atomic:

   | Roll | Name | Dept_ID | Dept_Name | Course |
   |---|---|---|---|---|
   | 101 | Rahim | 10 | CSE | Database |
   | 101 | Rahim | 10 | CSE | Networks |
   | 102 | Karim | 10 | CSE | Database |
   | 103 | Salma | 20 | EEE | Circuits |

   2NF, by removing partial dependency. The key is now (Roll, Course), and Name, Dept_ID and Dept_Name depend only on Roll:

   ```
   Student(Roll, Name, Dept_ID, Dept_Name)
   Enrollment(Roll, Course)
   ```

   3NF, by removing the transitive dependency Roll → Dept_ID → Dept_Name:

   ```
   Student(Roll, Name, Dept_ID)
   Department(Dept_ID, Dept_Name)
   Enrollment(Roll, Course)
   ```

   E-R diagram of the normalised design:

   ```mermaid
   erDiagram
       DEPARTMENT ||--o{ STUDENT : "has"
       STUDENT ||--o{ ENROLLMENT : "registers"
       COURSE ||--o{ ENROLLMENT : "is taken in"
       DEPARTMENT {
           int Dept_ID PK
           string Dept_Name
       }
       STUDENT {
           int Roll PK
           string Name
           int Dept_ID FK
       }
       COURSE {
           string Course_ID PK
           string Course_Name
       }
       ENROLLMENT {
           int Roll PK
           string Course_ID PK
           string Grade
       }
   ```

   - Each department's name is now stored once; a department can exist without students; deleting a student does not affect the department; and the original table can be reconstructed exactly by joining, so the decomposition is lossless.
7. **(ক) Normalization কী? কত প্রকার ও কী কী? ব্যাখ্যা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 415 (ET: N/A)]*


   Answer:

   What normalisation is:
   - Normalisation is the process of organising the tables and columns of a relational database so as to reduce data redundancy and eliminate the update, insertion and deletion anomalies that redundancy causes. It was introduced by E. F. Codd.
   - It proceeds by decomposing a large table into smaller related tables, in such a way that no information is lost and the original can be reconstructed by joining them.

   Why it is needed, that is the anomalies it removes:
   - Update anomaly: the same fact stored in many rows must be changed in every one of them; if one is missed, the data becomes inconsistent.
   - Insertion anomaly: a fact cannot be recorded because other, unrelated, information is not yet available. For example a new department cannot be recorded until an employee is assigned to it.
   - Deletion anomaly: deleting one fact accidentally destroys another. For example deleting the last employee of a department destroys the record of the department itself.
   - It also saves storage, makes the design clearer, and makes constraints easier to enforce.

   The normal forms:

   First Normal Form, 1NF:
   - Every attribute must hold a single atomic value; no repeating groups, no multivalued attributes and no arrays.
   - Each row must be unique, that is the table must have a primary key.
   - Violation: `Student(Roll, Name, Subjects)` where Subjects holds 'Math, Physics, Chemistry'.
   - Remedy: place each value in its own row, or move the multivalued attribute to a separate table: `Student(Roll, Name)` and `Student_Subject(Roll, Subject)`.

   Second Normal Form, 2NF:
   - The relation must be in 1NF, and every non-prime attribute must be fully functionally dependent on the whole primary key, not on part of it. Partial dependency is not permitted.
   - It only arises when the primary key is composite; a table with a single attribute key is automatically in 2NF once it is in 1NF.
   - Violation: `Enrollment(Student_ID, Course_ID, Student_Name, Course_Name, Grade)` with the key (Student_ID, Course_ID). Here Student_Name depends only on Student_ID and Course_Name only on Course_ID, both of which are partial dependencies.
   - Remedy: decompose into `Student(Student_ID, Student_Name)`, `Course(Course_ID, Course_Name)` and `Enrollment(Student_ID, Course_ID, Grade)`.

   Third Normal Form, 3NF:
   - The relation must be in 2NF, and no non-prime attribute may be transitively dependent on the primary key. In other words, a non-key attribute must not determine another non-key attribute.
   - Violation: `Employee(Emp_ID, Emp_Name, Dept_ID, Dept_Name)`. Here Emp_ID determines Dept_ID, and Dept_ID determines Dept_Name, so Dept_Name depends on the key only transitively.
   - Remedy: decompose into `Employee(Emp_ID, Emp_Name, Dept_ID)` and `Department(Dept_ID, Dept_Name)`.
   - Formal statement: for every functional dependency X → Y, either X is a super key or Y is a prime attribute.

   Boyce-Codd Normal Form, BCNF:
   - A stricter form of 3NF: for every non-trivial functional dependency X → Y, X must be a super key. 3NF allows the exception "or Y is a prime attribute"; BCNF removes it.
   - Every relation in BCNF is in 3NF, but not every 3NF relation is in BCNF. The difference arises only when a relation has overlapping candidate keys.
   - Example: `Class(Student, Subject, Teacher)` where a student takes one teacher per subject, and each teacher teaches only one subject. The dependencies are (Student, Subject) → Teacher and Teacher → Subject. The candidate keys are (Student, Subject) and (Student, Teacher). The relation is in 3NF, because Subject is a prime attribute; but Teacher → Subject has a determinant that is not a super key, so it is not in BCNF.
   - Remedy: decompose into `Teacher_Subject(Teacher, Subject)` and `Student_Teacher(Student, Teacher)`.

   Higher forms:
   - Fourth Normal Form, 4NF: removes multivalued dependencies, that is two independent multivalued facts stored in one table.
   - Fifth Normal Form, 5NF or project-join normal form: removes join dependencies, so that a relation cannot be losslessly decomposed further.

   How far to normalise:
   - 3NF or BCNF is the normal target for a transactional system. Beyond that the benefit is usually theoretical.
   - Deliberate denormalisation is used in reporting and data warehouse systems, where the cost of many joins outweighs the cost of the redundancy, and the redundancy is controlled by the load process rather than by ad hoc updates.
8. **What is database Normalization? Write down the types of database Normalization.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 504 (ET: N/A)]*


   Answer:

   What database normalisation is:
   - Normalisation is the process of organising the tables and columns of a relational database to reduce redundancy and eliminate the update, insertion and deletion anomalies that redundancy causes. It works by decomposing a large table into smaller related tables in a lossless way.
   - It was introduced by E. F. Codd, who defined the first three normal forms in 1970 and 1971.

   Types of normalisation, that is the normal forms:

   - First Normal Form, 1NF: every attribute holds a single atomic value, with no repeating groups, no multivalued attributes and no arrays; and every row is unique. Violation: a Subjects column holding 'Math, Physics'. Remedy: one value per row, or a separate table.

   - Second Normal Form, 2NF: in 1NF, and every non-prime attribute is fully dependent on the whole primary key, with no partial dependency on part of a composite key. It arises only when the key is composite. Violation: `Enrollment(Student_ID, Course_ID, Student_Name, Grade)` where Student_Name depends only on Student_ID. Remedy: separate Student from Enrollment.

   - Third Normal Form, 3NF: in 2NF, and no non-prime attribute is transitively dependent on the key, that is no non-key attribute determines another non-key attribute. Violation: `Employee(Emp_ID, Name, Dept_ID, Dept_Name)`. Remedy: separate Department from Employee.

   - Boyce-Codd Normal Form, BCNF: a stricter 3NF, requiring that for every non-trivial dependency X → Y, X is a super key. It differs from 3NF only when candidate keys overlap.

   - Fourth Normal Form, 4NF: in BCNF, and containing no multivalued dependency, that is no two independent multivalued facts in one table. Violation: a table holding a student's skills and languages together, which forces a spurious cross product.

   - Fifth Normal Form, 5NF, also called project-join normal form: containing no join dependency that is not implied by the candidate keys, so the relation cannot be decomposed further without loss.

   - Sixth Normal Form and Domain-Key Normal Form are further theoretical refinements, rarely used in practice.

   How far to go: 3NF or BCNF is the practical target for a transactional database. Beyond that the benefit is usually theoretical, and reporting systems are often deliberately denormalised to avoid excessive joins.
9. **Which normalization is related to functional dependency?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*


   Answer: Functional dependency is the basis of the second, third and Boyce-Codd normal forms.

   - A functional dependency X → Y means that the value of X determines the value of Y: if two rows agree on X they must agree on Y. It is the formal relationship between attributes on which normalisation rests.

   Which normal forms use it:
   - First Normal Form does not use functional dependencies at all. It concerns only atomicity, that is that every value must be single valued, so it is a structural rather than a dependency requirement.
   - Second Normal Form uses it: it forbids partial functional dependency, that is a non-prime attribute depending on only part of a composite key.
   - Third Normal Form uses it: it forbids transitive functional dependency, that is a non-prime attribute depending on the key only through another non-prime attribute.
   - Boyce-Codd Normal Form uses it most strictly: for every non-trivial functional dependency X → Y, X must be a super key.
   - Fourth Normal Form is based on multivalued dependency, which is a generalisation of functional dependency, and Fifth Normal Form on join dependency, a further generalisation.

   - So the direct answer is 2NF, 3NF and BCNF, with 4NF and 5NF resting on the generalisations of the concept.

   Example:
   - In `Employee(Emp_ID, Emp_Name, Dept_ID, Dept_Name)` the dependencies are Emp_ID → Emp_Name, Dept_ID and Dept_ID → Dept_Name. The second of these has a determinant that is not a key, which is precisely what 3NF forbids, and it is the reason the table must be decomposed.
10. **Functional dependency use in which normalizations?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*


   Answer: Functional dependency is used in the second, third and Boyce-Codd normal forms, and its generalisations are used in the fourth and fifth.

   - Functional dependency X → Y means that X determines Y: any two rows agreeing on X must agree on Y.

   Where it is used:
   - 1NF: not used. It requires only that every value be atomic, which is a structural condition.
   - 2NF: forbids partial functional dependency, in which a non-prime attribute depends on part of a composite key rather than on the whole of it.
   - 3NF: forbids transitive functional dependency, in which a non-prime attribute depends on the key only through another non-prime attribute. Formally, for every X → Y, either X is a super key or Y is prime.
   - BCNF: the strictest condition based purely on functional dependency, requiring that for every non-trivial X → Y, X is a super key.
   - 4NF: based on multivalued dependency, X →→ Y, which is a generalisation of functional dependency.
   - 5NF: based on join dependency, a further generalisation.

   Types of functional dependency worth naming:
   - Trivial: X → Y where Y is a subset of X, for example {Roll, Name} → Roll. Always holds.
   - Non-trivial: Y is not a subset of X.
   - Fully functional: Y depends on the whole of X and on no proper subset of it.
   - Partial: Y depends on only part of a composite X. This is what 2NF removes.
   - Transitive: X → Y and Y → Z, so X → Z indirectly. This is what 3NF removes.

   Armstrong's axioms, the rules by which dependencies are derived: reflexivity, augmentation and transitivity, with union, decomposition and pseudo-transitivity following from them. They are used to compute the closure of a set of attributes, which is how candidate keys are found and how a normal form is verified.
11. **What in First and Second Normal form is DBMS?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*


   Answer:

   First Normal Form:
   - A relation is in 1NF if every attribute holds a single atomic value, so there are no repeating groups, no multivalued attributes and no arrays or lists inside a column, and if every row is unique, that is the relation has a primary key.
   - It is the minimum requirement for a table to be relational at all.

   Example of a violation and its remedy:

   Not in 1NF, since Phone holds two values in one field:

   | Roll | Name | Phone |
   |---|---|---|
   | 101 | Rahim | 01711111111, 01822222222 |
   | 102 | Karim | 01933333333 |

   In 1NF, one value per field:

   | Roll | Name | Phone |
   |---|---|---|
   | 101 | Rahim | 01711111111 |
   | 101 | Rahim | 01822222222 |
   | 102 | Karim | 01933333333 |

   - The better remedy is to move the multivalued attribute to its own table: `Student(Roll, Name)` and `Student_Phone(Roll, Phone)`, which avoids repeating the name.

   Second Normal Form:
   - A relation is in 2NF if it is in 1NF and every non-prime attribute is fully functionally dependent on the whole primary key, that is no non-prime attribute depends on only part of a composite key.
   - It can only be violated when the primary key is composite; a relation whose key is a single attribute is automatically in 2NF once it is in 1NF.

   Example of a violation and its remedy:

   Not in 2NF. The key is (Roll, Course_ID), but Name depends only on Roll and Course_Name only on Course_ID:

   | Roll | Course_ID | Name | Course_Name | Marks |
   |---|---|---|---|---|
   | 101 | C1 | Rahim | Database | 85 |
   | 101 | C2 | Rahim | Networks | 78 |
   | 102 | C1 | Karim | Database | 90 |

   In 2NF, decomposed so that each non-key attribute depends on the whole key of its own table:

   ```
   Student(Roll, Name)
   Course(Course_ID, Course_Name)
   Result(Roll, Course_ID, Marks)
   ```

   - The improvement: the student's name and the course's name are each stored once, so they cannot become inconsistent; a course can be created before anyone enrols in it; and deleting a result does not destroy the record of either the student or the course.
12. **অথবা, (ক) “BCNF is stricter than 3NF” এই উক্তিটি উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 626 (ET: N/A)]*


   Answer: The statement is correct: every relation in BCNF is in 3NF, but a relation may be in 3NF without being in BCNF.

   The two definitions, which make the difference visible:
   - 3NF: for every non-trivial functional dependency X → Y, either X is a super key, or Y is a prime attribute, that is Y belongs to some candidate key.
   - BCNF: for every non-trivial functional dependency X → Y, X must be a super key. The escape clause "or Y is prime" is removed.
   - BCNF is therefore strictly stronger. The difference arises only when a relation has more than one candidate key and those keys overlap.

   Worked example:

   `Class(Student, Subject, Teacher)` with the business rules:
   - A student takes one teacher for a given subject: (Student, Subject) → Teacher.
   - Each teacher teaches only one subject: Teacher → Subject.

   | Student | Subject | Teacher |
   |---|---|---|
   | Rahim | Database | Dr. Alam |
   | Rahim | Networks | Dr. Haque |
   | Karim | Database | Dr. Alam |
   | Salma | Database | Dr. Rashid |

   - Candidate keys: (Student, Subject) and (Student, Teacher). They overlap in Student.
   - Prime attributes: Student, Subject and Teacher, since all three appear in some candidate key.

   Is it in 3NF?
   - The dependency (Student, Subject) → Teacher has a super key as its determinant, so it is fine.
   - The dependency Teacher → Subject has a determinant that is not a super key, but its right hand side, Subject, is a prime attribute, so the 3NF escape clause applies. The relation is therefore in 3NF.

   Is it in BCNF?
   - Teacher → Subject has a determinant, Teacher, that is not a super key. BCNF has no escape clause, so the relation is not in BCNF.

   Why this matters in practice, that is the redundancy 3NF leaves behind:
   - The fact that Dr. Alam teaches Database is repeated in every row involving him, so it can be updated inconsistently.
   - A teacher's subject cannot be recorded before any student is assigned to that teacher.
   - Deleting the last student of Dr. Rashid destroys the fact that he teaches Database.
   - These are exactly the anomalies normalisation exists to remove, and 3NF has failed to remove them.

   Decomposition into BCNF:

   ```
   Teaches(Teacher, Subject)
       PRIMARY KEY (Teacher)

   Studies(Student, Teacher)
       PRIMARY KEY (Student, Teacher)
   ```

   - Each teacher's subject is now stored once, and the anomalies disappear.

   The cost of BCNF, which should also be stated:
   - The decomposition is lossless, but it is not dependency preserving: the original dependency (Student, Subject) → Teacher can no longer be enforced within a single relation, so a join is required to check it.
   - Every relation can be decomposed into 3NF losslessly and with dependency preservation; not every relation can be decomposed into BCNF with dependency preservation. This is why designers sometimes stop at 3NF deliberately.
13. **Why Normalization is used in database? Explain 1^{\text{st}} Normal form using an example.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 665 (ET: N/A)]*


   Answer:

   Why normalisation is used:
   - To eliminate data redundancy, so that a fact is stored once rather than repeated.
   - To remove the update anomaly, in which a repeated fact must be changed in many rows and an omission leaves the data inconsistent.
   - To remove the insertion anomaly, in which a fact cannot be recorded because unrelated information is missing.
   - To remove the deletion anomaly, in which deleting one fact accidentally destroys another.
   - To save storage space.
   - To produce a clearer design in which each table describes one kind of thing, which makes the database easier to understand and to extend.
   - To make integrity constraints easier to state and enforce.

   First Normal Form:
   - A relation is in 1NF if every attribute contains only a single atomic value, so there are no repeating groups, no multivalued attributes and no lists inside a column, and if every row is unique.
   - It is the minimum requirement for a table to be relational at all, since the relational model is defined on atomic values.

   Example of a violation:

   | Student_ID | Name | Subjects |
   |---|---|---|
   | 101 | Rahim | Math, Physics, Chemistry |
   | 102 | Karim | Math |
   | 103 | Salma | Physics, Chemistry |

   - The Subjects column holds several values in one field. The consequences are severe: it is impossible to search for all students taking Physics with a simple equality test; sorting and aggregating on subject is impossible; the value must be parsed by the application; and adding or removing one subject requires rewriting the whole string.

   Conversion to 1NF, method 1, one row per value:

   | Student_ID | Name | Subject |
   |---|---|---|
   | 101 | Rahim | Math |
   | 101 | Rahim | Physics |
   | 101 | Rahim | Chemistry |
   | 102 | Karim | Math |
   | 103 | Salma | Physics |
   | 103 | Salma | Chemistry |

   - The primary key is now the composite (Student_ID, Subject). Every field holds one atomic value, so the table is in 1NF.

   Conversion to 1NF, method 2, which is better because it also avoids repeating the name:

   ```
   Student(Student_ID, Name)
       101, Rahim
       102, Karim
       103, Salma

   Student_Subject(Student_ID, Subject)
       101, Math
       101, Physics
       101, Chemistry
       102, Math
       103, Physics
       103, Chemistry
   ```

   - A common error to avoid: adding columns Subject1, Subject2 and Subject3 does not achieve 1NF in spirit. It creates a repeating group, imposes an arbitrary limit, wastes space when fewer subjects are taken, and makes querying just as awkward.
14. **Why do you need database Normalization?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*


   Answer: Normalisation is needed because an unnormalised design stores the same fact in many places, and that redundancy causes three specific kinds of failure.

   The anomalies it removes:

   - Update anomaly: a fact repeated across many rows must be changed in every one of them. If one row is missed, the database now holds two contradictory values and there is no way to tell which is correct. Example: in a table holding employee and department details together, changing a department's location requires updating every employee row of that department.

   - Insertion anomaly: a fact cannot be recorded because other, unrelated, information is not yet available. Example: a newly created department cannot be entered at all until at least one employee is assigned to it, because the row would have no key value.

   - Deletion anomaly: deleting one fact accidentally destroys another. Example: deleting the last employee of a department also destroys the only record of that department's name and location.

   Other reasons:
   - Reduced storage, since a fact occupies space once rather than many times.
   - Improved data integrity and consistency, because there is only one place where each fact can be wrong.
   - Clearer design: each table describes one kind of thing, so the schema is easier to understand, to document and to extend.
   - Easier enforcement of constraints, since a constraint on a fact stored once is simple, whereas a constraint on a fact stored many times requires the copies to be kept in agreement.
   - Better support for change: adding a new attribute of a department affects only the Department table.
   - More efficient indexing, since smaller tables with narrower rows fit more rows per page.

   Illustration:

   Unnormalised:

   | Emp_ID | Emp_Name | Dept_ID | Dept_Name | Dept_Location |
   |---|---|---|---|---|
   | 1 | Rahim | 10 | IT | Dhaka |
   | 2 | Karim | 10 | IT | Dhaka |
   | 3 | Salma | 20 | Finance | Chattogram |

   Normalised:

   ```
   Employee(Emp_ID, Emp_Name, Dept_ID)
   Department(Dept_ID, Dept_Name, Dept_Location)
   ```

   - All three anomalies disappear: the location is stored once, a department can exist without employees, and removing an employee does not remove the department.

   The cost, which a complete answer should state:
   - Normalisation increases the number of tables and therefore the number of joins, which costs query performance. For reporting and data warehouse systems, deliberate denormalisation is often the right choice, because the redundancy is controlled by the load process rather than by ad hoc updates. The rule of thumb is to normalise to 3NF and then denormalise selectively where measurement shows it is necessary.
15. **Let a relational function is R(A, B, C, D, E), Write Yes or No based on those are the follow n functional dependency.** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 822 (ET: BUET)]*
   AB \to C
   B \to B
   DE \to A


   Answer: The question asks whether each of the given dependencies can hold on the relation R(A, B, C, D, E). The three must be judged separately.

   AB → C
   - Answer: Yes.
   - This is a valid non-trivial functional dependency. It asserts that the combination of A and B determines C, that is any two rows agreeing on both A and B must agree on C. Whether it actually holds for a particular relation depends on the data and the business rules, but it is a well formed and permissible dependency.

   B → B
   - Answer: Yes, but it is trivial.
   - A functional dependency X → Y is trivial when Y is a subset of X. Here the right hand side is identical to the left, so B → B holds for every relation by definition, in every possible instance. It follows immediately from Armstrong's reflexivity axiom.
   - Because it always holds and asserts nothing, it is useless for design purposes. It is never listed in a set of functional dependencies, it plays no part in computing a closure, and it never causes a normal form violation.

   DE → A
   - Answer: Yes.
   - Like the first, this is a valid non-trivial functional dependency asserting that D and E together determine A. Its truth depends on the data and the business rules.

   Summary:

   | Dependency | Valid | Type |
   |---|---|---|
   | AB → C | Yes | Non-trivial |
   | B → B | Yes | Trivial, holds always |
   | DE → A | Yes | Non-trivial |

   The point being tested:
   - The distinction between trivial and non-trivial dependencies. A trivial dependency is always true and therefore carries no information; a non-trivial one is a genuine assertion about the data that may or may not hold and that must be enforced.
   - Armstrong's axioms formalise this: reflexivity states that if Y ⊆ X then X → Y, which is exactly why B → B needs no justification.
   - In normalisation, only non-trivial dependencies matter. The definitions of 3NF and BCNF explicitly exclude trivial dependencies, since otherwise no relation could ever satisfy them.
16. **What is DBMS? Write down the purpose of normalization in DBMS.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*


   Answer:

   What a DBMS is:
   - A Database Management System is software that enables users to define, create, store, retrieve, update and manage data in a database, and that controls access to it. It stands between the physical data and the users, so that no application needs to know how the data is stored.
   - Its principal functions: data definition, data manipulation through SQL, transaction management with the ACID properties, concurrency control, security and authorisation, backup and recovery, enforcement of integrity constraints, and maintenance of the data dictionary.
   - Examples: Oracle, MySQL, PostgreSQL, Microsoft SQL Server, MongoDB.

   Purpose of normalisation in a DBMS:
   - To eliminate data redundancy, so that each fact is stored in exactly one place.
   - To remove the update anomaly: a fact repeated in many rows must be changed in all of them, and missing one leaves contradictory data with no means of telling which value is correct.
   - To remove the insertion anomaly: a new fact should be recordable without waiting for unrelated information, for example a new department should be enterable before any employee joins it.
   - To remove the deletion anomaly: removing one fact should not destroy another, for example deleting the last employee of a department should not erase the department itself.
   - To ensure data integrity and consistency, since there is only one place where each fact can be wrong.
   - To save storage space.
   - To produce a clearer design in which each table represents one kind of thing, which makes the schema easier to understand, document and extend.
   - To simplify the enforcement of constraints, since a constraint on a fact stored once is straightforward.
   - To organise the data logically so that relationships are represented explicitly by keys.

   How it is achieved: by decomposing tables according to the normal forms — 1NF for atomicity, 2NF to remove partial dependency, 3NF to remove transitive dependency, and BCNF as a stricter form of 3NF — in such a way that the decomposition is lossless and, where possible, dependency preserving.

   The cost, which should be stated: more tables means more joins, so heavily normalised schemas can be slower to query. 3NF is the usual target, with selective denormalisation for reporting.
17. **(b) What is normalization? Why is it needed?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 895 (ET: N/A)]*


   Answer:

   What normalisation is:
   - Normalisation is the process of organising the tables and columns of a relational database so as to reduce redundancy and eliminate the anomalies it causes. A large table is decomposed into smaller related tables in a way that loses no information, so that the original can be reconstructed by joining them.
   - It proceeds through a series of normal forms, each imposing a stricter condition: 1NF requires atomic values; 2NF removes partial dependency on part of a composite key; 3NF removes transitive dependency through a non-key attribute; and BCNF requires every determinant to be a super key.
   - It was introduced by E. F. Codd.

   Why it is needed:
   - Update anomaly: a fact repeated across many rows must be changed in every one of them; missing one leaves the database holding contradictory values.
   - Insertion anomaly: a fact cannot be recorded because other information is not yet available. A new department cannot be entered until an employee is assigned to it.
   - Deletion anomaly: deleting one fact destroys another. Removing the last employee of a department erases the department itself.
   - Redundancy wastes storage.
   - Integrity is easier to enforce when each fact exists in exactly one place.
   - The design becomes clearer, since each table then describes one kind of entity, and it is easier to extend.

   Example:

   Before normalisation:

   | Emp_ID | Emp_Name | Dept_ID | Dept_Name | Dept_Location |
   |---|---|---|---|---|
   | 1 | Rahim | 10 | IT | Dhaka |
   | 2 | Karim | 10 | IT | Dhaka |
   | 3 | Salma | 20 | Finance | Chattogram |

   After normalisation to 3NF:

   ```
   Employee(Emp_ID, Emp_Name, Dept_ID)
   Department(Dept_ID, Dept_Name, Dept_Location)
   ```

   - The department's name and location are now stored once; they can be updated in one place; a department can exist with no employees; and removing an employee does not remove the department.

   The trade-off worth stating: normalisation increases the number of joins, which costs query performance. 3NF is the practical target for a transactional system, and reporting systems are deliberately denormalised where measurement shows the joins to be too expensive.
18. **(i) DBMS কী? একটি Database কে normalize করার পদ্ধতিগুলো বর্ণনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 953-954 (ET: N/A)]*


   Answer:

   What a DBMS is:
   - A Database Management System is software that allows users to define, create, store, retrieve, update and manage data in a database, and that controls access to it. It stands between the stored data and the applications, so no program needs to know how the data is physically held.
   - Its functions: data definition, data manipulation, transaction management with ACID guarantees, concurrency control, security, backup and recovery, integrity enforcement, and maintenance of the data dictionary.

   Procedure for normalising a database:

   Step 1, gather the relation and its functional dependencies:
   - List every attribute, and determine which attributes determine which others from the business rules. This is the essential preparatory step; normalisation cannot be performed without knowing the dependencies.

   Step 2, identify the candidate keys:
   - Compute attribute closures to find the minimal sets that determine every attribute. From these, identify the prime attributes, that is those appearing in some candidate key.

   Step 3, convert to First Normal Form:
   - Ensure every attribute holds a single atomic value. Remove repeating groups, multivalued attributes and lists inside columns by placing each value in its own row or in a separate table. Ensure the relation has a primary key.

   Step 4, convert to Second Normal Form:
   - Check whether any non-prime attribute depends on only part of a composite key. If so, that is a partial dependency: move the partially dependent attributes, together with the part of the key they depend on, into a new relation.
   - A relation whose key is a single attribute is already in 2NF.

   Step 5, convert to Third Normal Form:
   - Check whether any non-prime attribute is determined by another non-prime attribute. If so, that is a transitive dependency: move the determining attribute and the attributes it determines into a new relation, leaving the determining attribute in the original as a foreign key.

   Step 6, convert to Boyce-Codd Normal Form:
   - Check every non-trivial dependency X → Y. If X is not a super key, decompose so that it becomes one. This step matters only where candidate keys overlap.

   Step 7, consider 4NF and 5NF:
   - Remove multivalued dependencies, that is two independent multivalued facts held in one table, and then any remaining join dependencies. These are rarely required in practice.

   Step 8, verify the decomposition:
   - Lossless join: the original relation must be reconstructible exactly by joining the parts, with no spurious rows. This is guaranteed if the common attributes of the two parts form a key of at least one of them.
   - Dependency preservation: every original functional dependency should be enforceable within a single relation, so that no constraint requires a join to check. 3NF always allows this; BCNF sometimes does not.

   Step 9, consider deliberate denormalisation:
   - Measure the resulting query performance. Where the number of joins is unacceptable, as in reporting and data warehouse systems, reintroduce controlled redundancy knowingly, and manage it through the load process rather than through ad hoc updates.

## SQL Commands (DDL, DML, DCL, TCL) (13)

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

## Transaction Management & ACID Properties (12)

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

## Relational Data Model & ER Relationships (11)

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

## Database Backup & Disaster Recovery (8)

1. **Difference between incremental backup and differential backup. Which is more suitable for the banking system?** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 319 (ET: N/A)]*

2. **Database Data Loss based case study type question......** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 321 (ET: N/A)]*

3. **What do you understand about the IT disaster recovery plan? Describe your approach to disaster recovery and business continuity planning for the data centre of your office.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 333 (ET: BIBM)]*

4. **একটি MySQL database এর ডাটা ব্যাক আপ ও ব্যাক আপ করা ডাটা রিস্টোর করার কমান্ড লিখ।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 382 (ET: BUET)]*

5. **In the context of data management, what are the primary differences between data recovery and data backup? Provide real-world examples of when each is employed effectively.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 539 (ET: MIST)]*

6. **To achieve a '0-bit data loss' for its 24 x 7 x 365 banking operation, what steps or technology should an online bank employ to safeguard its data against any potential threats of data loss?** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 518 (ET: MIST)]*

7. **MySQL database এর ক্ষেত্রে Backup and Restore করার কমান্ড লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 865 (ET: BUET)]*

8. **Describe what are the ways for no data loss?** *[RAKUB Assistant Database Administrator 2020 compact it 1015-1016 (ET: E-Zone)]*

## PL/SQL & Database Triggers (6)

1. **Explain Database Trigger with example.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

2. **Database program with base and high- level language (SQL) to find out the interest rate from the given database table.** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 321 (ET: N/A)]*

3. **(c) Define dynamic SQL and trigger with examples.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 693 (ET: N/A)]*

4. **(b) Describe the application of trigger in database.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 795 (ET: N/A)]*

5. **Suppose, ‘Employee’ table (emp_id, emp_name, dept_id, salary) and ‘Department’ table (dept_id, dept_name, increment_dept). Create a tigger to increment the salary of the employee by 10% whose salary is above 30000.** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 862 (ET: BUET)]*

6. **(a) What is the purpose of database trigger? Explain with an example.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)]*

## Indexing & Query Optimization (B-Tree, B+ Tree) (6)

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

## Distributed & Parallel Databases (4)

1. **(খ) Speedup এবং Scaleup চিত্রসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 613 (ET: N/A)]*

2. **(ক) Data Fragmentation কী? ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 613 (ET: N/A)]*

3. **What is distributed database?** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 660 (ET: N/A)]*

4. **Which of the following distributed database system over centralized database system? (a) Software cost (b) Software complexity (c) Slow response (d) Modular growth** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

## Data Warehousing, Data Mining & Business Intelligence (4)

1. **Differentiate among Database, Data Warehouse and Data Mining with real world example.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 517 (ET: MIST)]*

2. **Discuss different tools and techniques to develop a Business Intelligence Dashboard for a bank. How can data be captured and aggregated from various sources within the bank to monitor the business performance?** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 519 (ET: MIST)]*

3. **Software scenario question- Business Intelligence Model** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 521 (ET: MIST)]*

4. **(খ) Big data বলতে কি বুঝায়? Big data এর বৈশিষ্ট্যগুলো লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 766 (ET: N/A)]*

## Database Design & Data Types (3)

1. An institute wants to create a database table named STUDENT to store student information. The table should include the columns Roll Number, Name, Department, Email, and Admission Date. Specify the most appropriate SQL data type for each column and identify which column should be defined as the Primary Key, giving a brief justification for your choice. *[Officer (IT) 31 Jul 2026 bscs 03 (ET: N/A)]*

2. **(c) Describe the difference between CHAR and VARCHAR data type.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 795 (ET: N/A)]*

3. **What is the domain in a relational database? Explain with an example. Show how you would use Alter table SQL command to add a domain on a database table.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 916 (ET: N/A)]*

## SQL Joins & Operations (3)

1. **What are the different types of join in SQL?** *[DESCO Assistant Engineer 20.05.2023 compact it 580 (ET: DESCO)]*

2. **Left joning and inner joining of a table.** *[BTCL Assistant Manager (Technical) 2023 compact it 594 (ET: BUET)]*

3. **Which join is used for including not matching all records with output?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

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
