<!-- TOC START -->
**Table of Contents** — 19 subtopics · 253 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [SQL Queries](#sql-queries-76) | 76 |
| 2 | [Keys in DBMS](#keys-in-dbms-24) | 24 |
| 3 | [DBMS Architecture & Features](#dbms-architecture--features-22) | 22 |
| 4 | [ER Diagram & Database Design](#er-diagram--database-design-22) | 22 |
| 5 | [Normalization & Database Design](#normalization--database-design-20) | 20 |
| 6 | [SQL Commands (DDL, DML, DCL, TCL)](#sql-commands-ddl-dml-dcl-tcl-15) | 15 |
| 7 | [Relational Data Model & ER Relationships](#relational-data-model--er-relationships-13) | 13 |
| 8 | [Transaction Management & ACID Properties](#transaction-management--acid-properties-13) | 13 |
| 9 | [Database Backup & Disaster Recovery](#database-backup--disaster-recovery-8) | 8 |
| 10 | [Indexing & Query Optimization (B-Tree, B+ Tree)](#indexing--query-optimization-b-tree-b-tree-8) | 8 |
| 11 | [Data Warehousing, Data Mining & Business Intelligence](#data-warehousing-data-mining--business-intelligence-7) | 7 |
| 12 | [PL/SQL & Database Triggers](#plsql--database-triggers-6) | 6 |
| 13 | [Distributed & Parallel Databases](#distributed--parallel-databases-5) | 5 |
| 14 | [SQL Joins & Operations](#sql-joins--operations-5) | 5 |
| 15 | [Database Design & Data Types](#database-design--data-types-3) | 3 |
| 16 | [NoSQL, NewSQL & Modern Databases](#nosql-newsql--modern-databases-2) | 2 |
| 17 | [Database Connectivity (JDBC)](#database-connectivity-jdbc-2) | 2 |
| 18 | [Relational Keys (Candidate, Super, Primary, Foreign Key)](#relational-keys-candidate-super-primary-foreign-key-1) | 1 |
| 19 | [Indexing in DBMS](#indexing-in-dbms-1) | 1 |

<!-- TOC END -->

---

## SQL Queries (76)

1. Consider the following relation: **Employee(EmpID, Name, Department, Salary)**. Write an SQL query to retrieve the **Department**, the **total number of employees**, and the **average salary** for each department. The output should display one record for each department. [SO IT 25-07-2026]

2. Consider a STUDENTS table with the following attributes: StudentID, Name, Department, Marks (10 Marks)
   * **I.** Write an SQL query to display only StudentID, Name, and Marks for students scoring more than 80 marks.
   * **II.** Write an SQL query to count how many students scored more than 80 marks in each Department. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

3. **SQL Query: Find department name and Average salary form 2 table Department and Employee.......** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1334 (ET: BUET)]*
   Department table
   Department (dept_id, dept_name)
   Employee table
   Employee (emp_id, emp_name, salary, dept_id)

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

5. **Database Query related problem.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

6. **From an Employee table. Write SQL statement according to the following question:**
   **(a) Find out the employees who join the same date:** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1438 (ET: BUET)]*
   **(b) Find those employees whose salary greater than 8,000 and Less than 25,000** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*

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

8. **Consider the following relation:**

**Write an SQL query to display the region, average sale amount, and total number of sales for each region where: The average sale amount exceeds BDT 50,000 and the total number of sales in that region is at least 5.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1425 (ET: E-Zone)]*

9. **Given two tables:**

**a) Write an SQL query to retrieve all student names, their courses, and grades.**
**b) Write an SQL query to retrieve names of students who obtained grade 'A'.** *[BUET Assistant Programmer 21.06.2025 compact it 1434 (ET: BUET)]*

10. **Consider the following database schema-** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1350 (ET: N/A)]*
```sql
employee (employee_name, street, city)
works (employee_name, company_name, salary)
company (employee_name, city)
```
**Write the SQL commands to perform the following operations:**
 * **(i) Find the names of all employees who live in the city 'Dhaka'.**
 * **(ii) Find the names of all employees whose salary in greater than BDT 1,00,000.**

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

12. **Given a Patient table in a hospital database below.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1340 (ET: N/A)]*

| Patient_ID | Disease_Name |
|---|---|
| 1 | Covid-19 |
| 2 | Dialysis |
| 3 | Covid-19 |
| 4 | Dengue |

Write down an SQL query to display the total number of patients under each disease category.

13. **SQL OUTPUT Problem: Find Employee salary from a table where salary more than 5000.** *[BCIC Assistant Programmer 14.02.2025 compact it 1328 (ET: BUET)]*

14. **Write SQL code to get duplicate names from employee table.** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*

15. **Write an SQL query to find duplicate names in the employee table.** *[BBA Assistant Programmer 12.07.2025 compact it 1433 (ET: BUET)]*

16. **SUM, Avg, Max these function are subnet of __________ function.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*

17. **SQL Query.....** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 592 (ET: BUET)], [RAKUB Assistant Network System Engineer 03.11.2023 compact it 553 (ET: BIBM)], [BREB Assistant Programmer (AP) 21.02.2025 compact it 1335 (ET: N/A)], [Water Supply and Sewerage Authority (WASA); Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*

18. **Find sname who supplies pname=“wheel” with minimum price:** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 418 (ET: BUET)]*
    * **Catalog** (sid, pid, price)
    * **Supplier** (sid, sname, address)
    * **Product** (pid, pname, etc)

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

20. **Database query:**
   * **(i) Group by**
   * **(ii) Average Salary** *[Combined Bank Assistant Programmer 09.02.2024 compact it 299 (ET: BIBM)]*

21. **Consider that you are given a database of a 'Pet Society' with the following relations.**
   * **Animals(*ID*: integer, *Name*: string, *PrevOwner*: string, *DateAdmitted*: date, *Type*: string)**
   * **Adopter(*PSIN*: integer, *Name*: string, *Address*: string, *OtherAnimals*: integer)**
   * **Adoption(*AnimalID*: integer, *PSIN*: integer, *AdoptDate*: date, *chipNo*: integer)**
   **Give a sql query that list total number of adoptions on June 30, 2024 for each animal type.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 429 (ET: BIBM)]*

22. **How many row will return when we do i) Inner Join ii) Left Outer Join iii) Right Outer join and v) Full Outer join.** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 392 (ET: BUET)]*

23. **Write SQL Query For create, insert of a table Emp (id, name, designation, Dept_name, Salary). Write SQL Query that show department wise salary of Employee.** *[BKSP Assistant Programmer 13.07.2024 compact it 1459 (ET: N/A)]*

24. **Query's: Employee & department table given-**
   * **(i) Write the employee name who got same salary named Rahim but not same job of Rahim.**
   * **(ii) Write the employee's name who's average salary is more than company's average salary** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 380 (ET: BUET)]*

25. **EMPLOYEES (Emp_ID, Emp_Name, Manager_ID, Dept_ID);**
   **DEPARTMENTS (Dept ID, Salary, Dept Name, Emp_ID);**
   * **(a) Find out the names of the manager for each employee:**
   * **(b) Sort the employees total salary of each department based on salary in descending order.** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 431 (ET: BUET)]*

26. **Given Four table:**
   * **Employee (empno(PK), empname, monthlysalary, deptno, mqrnd(FK))**
   * **Department(deptno, deptname, deptlocation)**
   * **Course(erscode(pk) erd dese, ers category, ers duration)**
   * **Offering (of begingate, erscode fk, offeringlocation, empno fk)**
   **Write query for:**
   * **(a) Find Departments with Average Monthly Salary Greater than 1000.**
   * **(b) Find Courses with More Than 2 Offerings.** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1456 (ET: BUET)]*

27. **6.4 Consider the following relation: Employee(EmpID, Name, Department, Salary). Write an SQL query to retrieve the Department, the total number of employees, and the average salary for each department. The output should display one record for each department.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

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

29. **Employee Salary sql query a. Sum b. Avg. C. Employee_Name all 2nd letter 'a'......** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 508 (ET: N/A)]*

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

31. **Consider the employee tables: Create a SQL view that shows the details of Employee information who have the salary equivalent to the maximum, minimum and average salary of employee.** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 473 (ET: N/A)]*

32. **SQL query for employee table. (Approximate)** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 476 (ET: N/A)]*

33. **Suppose we have a relational database with five tables. table key Attributes S(sid, A) Sid T(tid, B) Tid U(uid, C) Uid R(sid, tid, D) sid, tid Q(tid, uid, E) tid, uid Here R implements a many-to-many relationship between the entities implemented with tables S and T, and Q implements a many-to-many relationship between the entities implemented with tables T and U.**
   **(A) Write an SQL query that returns all records of the form sid, uid where sid is the key of an S- record and uid is the key of a U-record and these two records are related through the relations R and Q. Use SELECT and not SELECT DISTINCT in your query.**
   **(B) Write an SQL query that returns records of the form A, C where the A-value is from an S- record and the C-value is from a U-record and these two records are related through the relations R and Q. Use SELECT and not SELECT DISTINCT in your query.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 496 (ET: N/A)]*

34. **Write following EMPLOYEE database table write an SQL query to find employee who work is a department where the average salary is lower then the average salary all the department......** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 452 (ET: BUET)]*

35. **Consider the two schema employees (id, first_name, last_name, designation, oining_date, salary, dept_id) and department (dept_id, dept_name). Where detp_id is forgeign key. Find the first_name and department name whose salary is maximum.** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 459 (ET: BUET)]*

36. **Suppose that we have a relational database with the following table. Underlined one represent primary key**
   **Movies (\underline{\text{mid}}, title, year)**
   **People (\underline{\text{pid}}, name)**
   **Genres (\underline{\text{gid}}, genre)**
   **HasRole (\underline{\text{pid}, \text{mid}}, role)**
   **Has Genre (\underline{\text{gid}, \text{mid}})**
   **Write a SQL query to return the number of movies that are romantic comedies.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 436 (ET: BIBM)]*

37. **(গ) ডাটাবেস সিস্টেমে view কী? এটি কী কী কাজে লাগে?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 627 (ET: N/A)]*

38. **অথবা, নিম্নোক্ত টেবিলগুলো হতে (ক), (খ) এবং (গ) এর উত্তর দিন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 627 (ET: N/A)]*
   Restaurant (rid, rname, rcity, phone, seat-capacity)
   Dishes (did, dname, dtype)
   Customer (cid, cname, ccity)
   Serves (rid, did)

   **(ক) যে যে রেস্টুরেন্টগুলো ‘Burger’ পরিবেশন করে সেগুলোর নাম খুঁজে বের করার জন্য SQL Query লিখুন। (খ) ‘Ziman’ নামক একজন Customer যে যে খাবারগুলো অ্যালার্জি সংক্রান্ত সমস্যা এড়িয়ে খেতে পারেন তার তালিকা তৈরি করুন। (গ) যে যে খাবারগুলো ঢাকার সকল রেস্টুরেন্টে পাওয়া যায় তার তালিকা তৈরি করুন।**

39. **SQL query from a given table.** *[BICIC Assistant Programmer 2022 compact it 634 (ET: BUET)]*

40. **Employee table হতে Employee_id, Employee কে খোঁজে বের করার SQL Command লিখ যাদের গড় salary 2000 উপরে।** *[BTCL Junior Assistant Manager 2022 compact it 641 (ET: BUET)]*

41. **Employee Table টেবিল হতে যে সকল কর্মচারীদের বেতন 30000 টাকার বেশি তাদের নাম পদবী আলাদা করার SQLCommand লিখুন।** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 699 (ET: DPI)]*

42. **There are two tables like Employees (Employee_ID, First_name, Last_name, Email, Phone_number, Hire_date, Job_Id) and Departments (Department_Id, Department_name, Manager_Id, Location_Id). Now, write a query to find the name (first_name, last_name), Department Id and name of all the employees.** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 718 (ET: N/A)]*

43. **For employee table: (a) Write a SQL query to find those employees who earn more than the average salary. Return employee ID, first name, last name. (b) Write a SQL query to find those employees who earn the highest salary in a department. Return department ID, employee name, and salary.** *[CAAB Programmer 2022 compact it 722 (ET: N/A)]*

44. **Write down the SQL command into the following two: (a) Find out the all information of employees from emp_info table. Where employee's salary is more than 20,000 and city is Dhaka. (b) Update employee name ‘Mr.X’ in emp_info, whose epm_id is 2.** *[NWPGCL Junior Assistant Manager (IT) 2022 compact it 730 (ET: N/A)]*

45. **Write down the equivalent SQL from following relational algebra. [full question not collected]** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 760 (ET: N/A)]*

46. **Write a SQL query to find same salary but job not same?** *[BIWTA; Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*

47. **This returns the names of the staff where timestampdiff is greater than 25 so it returns total 3 rows.** *[Water Supply and Sewerage Authority (WASA); Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*

48. **(c) In a SQL query, while performing string matching when do we use operator and when we use LIKE operator? Give examples.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 803 (ET: N/A)]*

49. **Consider the Electrical Powr company database which has the following tables: Powerplant(Powerplant_ID, location, type, capacity.unit_price) Customer(Customer_ID, name, address, DoB, monthly_demand) Customer_usage_profile(ID, month_name, Customer_ID, Powrplant_ID) The powerplant relation has attributes powerplan_ID, loation, Type{Thrmal power, hydro power, nuclear power, nuclear power, capacity, and unit_price of power generated by the powerplant. The customer relation has attributes Customer_ID, name, address, date of birth(DoB) and monthly_demand of electrical power. The customer_usesge_profile relation stores the user profile of a customer. A customer more usage hydropower during the rainy season and thermal or nuclear power during the dry season. Write the relational algebra expressions for the following queries: (i) List the customers with a yearly bill of more than taka 5,000. (ii) List the customers who uses nuclear power during December and has a monthly bill less then 500 in December.** *[BPDB Assistant Engineer (CSE) 2021 compact it 818 (ET: BUET)]*

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

51. **Write SQL command from the following tables. Employee (ename, street, city) Works (ename, cname, salary, joindate) Company (cname, city) Manages (ename, mname) (a) Find name, street, city who work for First Corporation Bank and earn more than 30000 (b) Find name of all employees, who live in the same city and company for which they work. (c) Give all employees of First Century Bank 10 percent salary raise (d) Find the company with payroll less than 100000.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 835-836 (ET: N/A)]*

52. **DB schema: book (book_id, book_title, book_type, publication_name) author (book_name, author_name) publicher (publication_name, publication_address, est_year) copies (book_id, branch_name, no_of-copies) [database query লিখতে আসছিল]** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)]*

53. **Given Table: Project (Project_id, Project_name, Manager_name) Location (location_id, Location_name, project_id) Employee (Employee_id, Employee_Name, Location_id, Joning date, Salary) Write a query to show project_name, Location_name, Total_salary of each projects employee who joined before ‘January 2021’.** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 868 (ET: BUET)]*

54. **(i) SQL Query for finding Dept names for departments Find out the employees whose salaries are greater than the salaries of their managers.** *[NESCO Assistant Manager (ICT) 2021 compact it 907 (ET: BUET)]*

55. **Two SQL query from given table (date and join related).** *[Sonali Bank Ltd. Officer IT 2021 compact it 910 (ET: N/A)]*

56. **emp [e_id, e_name, dept_id, salary, DOB], dept [dept_id, city, dept_name]; প্রত্যেকটি Department এর নাম এবং ঐ Department এর employee দের গড় Salary দেখার SQL Query লিখ।** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 911 (ET: BUET)]*

57. **Database table by name Loan Records is given below: What is the output of the following SQL query?** *[BAUST Assistant Programmer 2021 compact it 919-920 (ET: N/A)]*
```sql
SELECT count (*) FROM (
(SELECT Borrower, Bank_Manager, FROM Loan_Records) AS S NATURAL JOIN
(SELECT Bank_Manager, Loan_Amount FROM Loan_Records) AS T);
```

58. **Below tables are given, Employee (employee_id, name, salary, department) Leave (employee_id, date, reason, no_leaves) Holiday (Date, description) (i) Write mapping cardinality between 'Employee' and 'Holiday' table. (ii) Write query to show all employee's leave count. (iii) Write query to show employees who are in 'HR' department and have taken at least 5 leaves.** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 928 (ET: CTI)]*

59. **Find the Query for the Instructor table a. Find the average salary of instructors in each department. b. Find the names and average salaries of all departments whose average salary is greater than 42000. c. Find names of instructors with salary greater than that of some (at least one) instructor in the CSE department.** *[NRCC Assistant Programmer 2021 compact it 930 (ET: N/A)]*

60. **Consider the following relational database schema consisting of the four relation schemas: passenger (pid, ppname, pgender, pcity) agency (aid, aname, acity) flight (fid, fdate, time, src, dest) booking (pid, aid, fid, fdate) a) Get the complete details of all flights to New Delhi b) Get the details about all flights from Chennai to New Delhi.** *[SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)]*

61. **৫. সম্পূর্ণ টেবিলের ডেটা প্রদর্শন এর জন্য কোনটি ব্যবহার করা হয়?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

62. **Write a SQL query to find those employees who report that manager whose first name is ‘abc’. Return first name, last name, employee ID and salary.** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 947 (ET: BUET)]*

63. **Given a database schema and worker table with fully code: Now writes SQL Query from the following questions.** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 975 (ET: BUET)]*

64. **(b) SQL Query: commission greater than 10%** *[National University Assistant Programmer 2020 compact it 976 (ET: DU)]*

65. **(c) Remove duplicate data from table** *[National University Assistant Programmer 2020 compact it 976 (ET: DU)]*

66. **What is the full meaning of SQL? List of the aggregate function. Write SQL Query of a table and its output.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1002-1003 (ET: DU)]*

67. **Query to find out even number from given table.** *[RAKUB Assistant Database Administrator 2020 compact it 1014 (ET: E-Zone)]*

68. **How to copy from Parent table to Child Table with 1 column dividing into 3 different columns?** *[RAKUB Assistant Database Administrator 2020 compact it 1014-1015 (ET: E-Zone)]*

69. **Design and Queries from HR schema. (i) Display details of jobs where the minimum salary is greater than 10000. (ii) Display the first name and join date of the employees who joined between 2002 and 2005. (iii) Display first name and join date of the employees who is either IT Programmer or Sales Man. (iv) Display first name, salary, commission pct, and hire date for employees with salary less than 10000. (v) Display job Title, the difference between minimum and maximum salaries for jobs with max salary in the range 10000 to 20000. (vi) Display first name, salary, and round the salary to thousands. (vii) Display employees where the first name or last name starts with S. (viii) Display details of the employees where commission percentage is null and salary in the range 5000 to 10000 and department is 30. (ix) Display first name and date of first salary of the employees. (x) Display first name and last name after converting the first letter of each name to upper case and the rest to lower case.** *[RAKUB Assistant Database Administrator 2020 compact it 1016-1017 (ET: E-Zone)]*

70. **Query for retrieving UNCOMMON Name from Name column of two given tables.** *[RAKUB Assistant Database Administrator 2020 compact it 1017 (ET: E-Zone)]*

71. **Employee টেবিল থেকে যেসকল Employee এর Salary 25000 থেকে 50000 এর মধ্যে এবং Designation হচ্ছে officer এবং City হচ্ছে Dhaka তাদের দেখার জন্য SQL টেবিল দেখান।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1042 (ET: DPI)]*

72. **Design a database of student with the gpa of a university. Find the top 10% gpa holder from the different department of the university.** *[Combined 5 Banks Assistant Maintenance Engineer 2019 compact it 1055 (ET: AUST)]*

73. **(খ) SQL ব্যবহার করে Student নামে একটি টেবিল তৈরি করুন। টেবিলে Std-id, Std-name, Std-address এবং GPA নামে চারটি field থাকবে। Student টেবিল হতে যে সকল ছাত্রের ফলাফল GPA-5 তাদের সকল রেকর্ড দেখানোর জন্য SQL Query লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1097 (ET: N/A)]*

74. **There is a student table: Student (s_id, name, gender, age, phone, department, cgpa) find a query to get each department maximum CGPA of student. Which student gets highest cgpa in maximum of each department?** *[DESCO Assistant Engineer (CSE) 2019 compact it 1118 (ET: BUET)]*

75. **Given two tables are employee (id, name, salary, dept_id) and department (dept_id, dept_name), write SQL to find MAX salary and average salay of specific department.** *[DESCO Sub-Assistant Engineer (CSE) 2019 compact it 1121 (ET: BUET)]*

76. **একটি Branch Employee Table; Employee (ID, name, salary); এখন নতুন sub branch তৈরি করার যুক্তিক command লিখুন যার branch name একই হবে এবং Employee এর min ও avg salary বের করুন।** *[NPCBL Junior Technical Engineer 2019 compact it 1148 (ET: BUET)]*

## Keys in DBMS (24)

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

## ER Diagram & Database Design (22)

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

## Normalization & Database Design (20)

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

## SQL Commands (DDL, DML, DCL, TCL) (15)

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

## Relational Data Model & ER Relationships (13)

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

## Transaction Management & ACID Properties (13)

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

## Database Backup & Disaster Recovery (8)

1. **Difference between incremental backup and differential backup. Which is more suitable for the banking system?** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 319 (ET: N/A)]*

2. **Database Data Loss based case study type question......** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 321 (ET: N/A)]*

3. **What do you understand about the IT disaster recovery plan? Describe your approach to disaster recovery and business continuity planning for the data centre of your office.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 333 (ET: BIBM)]*

4. **একটি MySQL database এর ডাটা ব্যাক আপ ও ব্যাক আপ করা ডাটা রিস্টোর করার কমান্ড লিখ।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 382 (ET: BUET)]*

5. **In the context of data management, what are the primary differences between data recovery and data backup? Provide real-world examples of when each is employed effectively.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 539 (ET: MIST)]*

6. **To achieve a '0-bit data loss' for its 24 x 7 x 365 banking operation, what steps or technology should an online bank employ to safeguard its data against any potential threats of data loss?** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 518 (ET: MIST)]*

7. **MySQL database এর ক্ষেত্রে Backup and Restore করার কমান্ড লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 865 (ET: BUET)]*

8. **Describe what are the ways for no data loss?** *[RAKUB Assistant Database Administrator 2020 compact it 1015-1016 (ET: E-Zone)]*

## Indexing & Query Optimization (B-Tree, B+ Tree) (8)

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

## Data Warehousing, Data Mining & Business Intelligence (7)

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

## PL/SQL & Database Triggers (6)

1. **Explain Database Trigger with example.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

2. **Database program with base and high- level language (SQL) to find out the interest rate from the given database table.** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 321 (ET: N/A)]*

3. **(c) Define dynamic SQL and trigger with examples.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 693 (ET: N/A)]*

4. **(b) Describe the application of trigger in database.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 795 (ET: N/A)]*

5. **Suppose, ‘Employee’ table (emp_id, emp_name, dept_id, salary) and ‘Department’ table (dept_id, dept_name, increment_dept). Create a tigger to increment the salary of the employee by 10% whose salary is above 30000.** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 862 (ET: BUET)]*

6. **(a) What is the purpose of database trigger? Explain with an example.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 887 (ET: N/A)]*

## Distributed & Parallel Databases (5)

1. **(খ) Speedup এবং Scaleup চিত্রসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 613 (ET: N/A)]*

2. **(ক) Data Fragmentation কী? ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 613 (ET: N/A)]*

3. **What is distributed database?** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 660 (ET: N/A)]*

4. **Which of the following distributed database system over centralized database system? (a) Software cost (b) Software complexity (c) Slow response (d) Modular growth** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

5. **Explain the concept distributed DBMS. What are the features of DBMS?** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1054 (ET: BUET)]*

## SQL Joins & Operations (5)

1. **What are the different types of join in SQL?** *[DESCO Assistant Engineer 20.05.2023 compact it 580 (ET: DESCO)]*

2. **Left joning and inner joining of a table.** *[BTCL Assistant Manager (Technical) 2023 compact it 594 (ET: BUET)]*

3. **Which join is used for including not matching all records with output?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

4. **What is inner join? Explain with syntax and example.** *[Bangladesh Television Assistant Programmer 2019 compact it 1065 (ET: N/A)]*

5. **(b) Explain JOIN and INNER-JOIN procedure.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1143 (ET: N/A)]*

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
