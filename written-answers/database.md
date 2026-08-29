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

## ER Diagram & Database Design (21)

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

## Keys in DBMS (21)

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

## Normalization & Database Design (18)

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
