## DBMS Architecture & Features

1. (a) DBMS এর মূল বৈশিষ্ট্য লিখুন।
   (b) HTTP ও HTTPS প্রোটোকলের মধ্যে সুরক্ষার দিক থেকে পার্থক্য ব্যাখ্যা করুন। **(Assistant Programmer - Department of Immigration & Passports Exam: 15.07.2026) [compact it 1464]**

2. **ODBC এর পূর্ণ রূপ কি?** **(BARI - Assistant Maintenance Engineer Exam: 15.11.2025) [compact it 1451]**

3. **Data about data is Called __________.** **(BARI - Assistant Maintenance Engineer Exam: 15.11.2025) [compact it 1451]**

## NoSQL, NewSQL & Modern Databases

1. **What are the limitations of DBMS and how to related newsql with SQL and No-SQL.** **(Islami Bank PLC Quality Assurance (QA) Engineer Exam: 14.03.2025 (BUET)) [compact it 1332]**

## SQL Commands (DDL, DML, DCL, TCL)

1. Example Query of DDL, DML, DCL. (BEPRC Assistant Programmer Exam: 08.08.2026)

2. **What is SQL?** **(BBA - Assistant Programmer Exam: 12.07.2025 (BUET)) [compact it 1433]**

3. **ডাটাবেজ এ টেবিলের শুধু গঠন ডিলিট করার SQL কমান্ড কি?** **(BARI - Assistant Maintenance Engineer Exam: 15.11.2025) [compact it 1451]**

## SQL Queries

1. Consider the following relation: **Employee(EmpID, Name, Department, Salary)**. Write an SQL query to retrieve the **Department**, the **total number of employees**, and the **average salary** for each department. The output should display one record for each department. [SO IT 25-07-2026]

2. Consider a STUDENTS table with the following attributes: StudentID, Name, Department, Marks (10 Marks)
   * **I.** Write an SQL query to display only StudentID, Name, and Marks for students scoring more than 80 marks.
   * **II.** Write an SQL query to count how many students scored more than 80 marks in each Department. (Combined Bank Officer (IT) Exam: 09.05.2026) [debug it]

3. **SQL Query: Find department name and Average salary form 2 table Department and Employee.......** **(Islami Bank PLC Quality Assurance (QA) Engineer Exam: 14.03.2025 (BUET)) [compact it 1334]**
   Department table
   Department (dept_id, dept_name)
   Employee table
   Employee (emp_id, emp_name, salary, dept_id)

4. **Consider the following database schema, find out the employees whose manager's region is same as the employee working under him.** **(DPDC Assistant Manager (ICT) Exam: 27.06.2025 (BUET)) [compact it 1363]**
```sql
REGIONS (REGION_ID, REGION_NAME)
COUNTRIES (COUNTRY_ID, COUNTRY_NAME, REGION_ID)
LOCATIONS (LOCATION_ID, STREET_ADDRESS, POSTAL_CODE, CITY, STATE_PROVINCE, COUNTRY_ID)
DEPARTMENTS (DEPARTMENT_ID, DEPARTMENT_NAME, MANAGER_ID, LOCATION_ID)
EMPLOYEES (EMPLOYEE_ID, FIRST_NAME, LAST_NAME, EMAIL, PHONE_NUMBER, HIRE_DATE, JOB_ID, SALARY, COMMISSION_PCT, MANAGER_ID, DEPARTMENT_ID)
JOB_HISTORY (EMPLOYEE_ID, START_DATE, END_DATE, JOB_ID, DEPARTMENT_ID)
JOBS (JOB_ID, JOB_TITLE, MIN_SALARY, MAX_SALARY)
```

5. **Database Query related problem.** **(DPDC - Assistant Engineer (CSE) Exam: 17.10.2025) [compact it 1453]**

6. **From an Employee table. Write SQL statement according to the following question:**
   **(a) Find out the employees who join the same date:** **(Dhaka WASA - Assistant Maintenance Engineer (Network) Exam: 04.07.2025 (BUET)) [compact it 1438]**
   **(b) Find those employees whose salary greater than 8,000 and Less than 25,000** **(Dhaka WASA - Assistant Maintenance Engineer (Network) Exam: 04.07.2025 (BUET)) [compact it 1439]**

7. **Write down the Query for the following table?** **(DESCO Sub-Assistant Engineer Exam: 20.06.2025 (BUET)) [compact it 1361]**

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

**Write an SQL query to display the region, average sale amount, and total number of sales for each region where: The average sale amount exceeds BDT 50,000 and the total number of sales in that region is at least 5.** **(Combined Bank Senior Officer (IT) Exam: 17.10.2025 (E-Zone)) [compact it 1425]**

9. **Given two tables:**

**a) Write an SQL query to retrieve all student names, their courses, and grades.**
**b) Write an SQL query to retrieve names of students who obtained grade 'A'.** **(BUET - Assistant Programmer Exam: 21.06.2025 (BUET)) [compact it 1434]**

10. **SQL Query:** **(BREB Assistant Programmer (AP) Exam: 21.02.2025) [compact it 1335]**

11. **Consider the following database schema-** **(BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) Exam: 29.05.2025 (CS/CSE)) [compact it 1350]**
```sql
employee (employee_name, street, city)
works (employee_name, company_name, salary)
company (employee_name, city)
```
**Write the SQL commands to perform the following operations:**
 * **(i) Find the names of all employees who live in the city 'Dhaka'.**
 * **(ii) Find the names of all employees whose salary in greater than BDT 1,00,000.**

12. **Given the following two tables (Students and Marks) in a database, write down the output of the given SQL queries and write down the SQL queries for the outputs:** **(BPSC (Ministry of Food) Network/Website Manager Exam: 21.05.2025 (ICT)) [compact it 1344]**

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
 * **(iii) List all the students name and number of subjects they have completed.** **(BPSC (Ministry of Food) Network/Website Manager Exam: 21.05.2025 (ICT)) [compact it 1345]**
 * **(iv) List all the students who have not completed any subject.** **(BPSC (Ministry of Food) Network/Website Manager Exam: 21.05.2025 (ICT)) [compact it 1345]**
 * **(v) List all the subject names.** **(BPSC (Ministry of Food) Network/Website Manager Exam: 21.05.2025 (ICT)) [compact it 1345]**

13. **Given a Patient table in a hospital database below.** **(BPSC (Ministry of Food) Network/Website Manager Exam: 21.05.2025 (CSE)) [compact it 1340]**

| Patient_ID | Disease_Name |
|---|---|
| 1 | Covid-19 |
| 2 | Dialysis |
| 3 | Covid-19 |
| 4 | Dengue |

Write down an SQL query to display the total number of patients under each disease category.

14. **SQL OUTPUT Problem: Find Employee salary from a table where salary more than 5000.** **(BCIC Assistant Programmer Exam: 14.02.2025 (BUET)) [compact it 1328]**

15. **Write SQL code to get duplicate names from employee table.** **(BCC - Assistant Programmer Exam: 18.10.2025 (BCC)) [compact it 1442]**

16. **Write an SQL query to find duplicate names in the employee table.** **(BBA - Assistant Programmer Exam: 12.07.2025 (BUET)) [compact it 1433]**

17. **SUM, Avg, Max these function are subnet of __________ function.** **(BARI - Assistant Maintenance Engineer Exam: 15.11.2025) [compact it 1452]**

## Transaction Management & ACID Properties

1. **Explain the concept of ACID properties in a database transaction. Describe how each property—Atomicity, Consistency, Isolation, and Durability—ensures the reliability and integrity of a database system.** **(Combined Bank Senior Officer (IT) Exam: 17.10.2025 (E-Zone)) [compact it 1425]**

2. **How many process of Transaction complete?** **(BREB Assistant Programmer (AP) Exam: 21.02.2025) [compact it 1336]**

3. **ACID এর প্রোপার্টি কি?** **(BARI - Assistant Maintenance Engineer Exam: 15.11.2025) [compact it 1450]**

## Normalization & Database Design

1. **Why normalization is required in Database? Write shortly about 3NF?** **(BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) Exam: 29.05.2025 (CS/CSE)) [compact it 1350]**

2. **Explain the differences between Second Normal Form (2NF) and Third Normal Form (3NF) with examples.** **(BPSC (Ministry of Food) Network/Website Manager Exam: 21.05.2025 (CSE)) [compact it 1340]**

| 2NF(Second Normal Form) | 3NF(Third Normal Form) |
|---|---|
| It is already in 1NF. | It is already in 1NF as well as in 2NF also. |
| In 2NF, non-prime attributes (attributes that are not part of any candidate key) must depend on the entire candidate key. | In 3NF non-prime attributes are only allowed to be functionally dependent on Super key of relation. |
| No partial functional dependency of non-prime attributes on any proper subset of a candidate key is allowed. | No transitive functional dependency of non-prime attributes on any super key is allowed. |
| Stronger normal form than 1NF but lesser than 3NF. | Stronger normal form than 1NF and 2NF. |
| It eliminates repeating groups in relation. | It virtually eliminates all the redundancies. |
| The goal of the second normal form is to eliminate redundant data. | The goal of the third normal form is to ensure referential integrity. |

3. **What is Logical design database is called?** **(BARI - Assistant Maintenance Engineer Exam: 15.11.2025) [compact it 1451]**

## PL/SQL & Database Triggers

1. **Explain Database Trigger with example.** **(DPDC - Assistant Engineer (CSE) Exam: 17.10.2025) [compact it 1453]**

## Indexing & Query Optimization (B-Tree, B+ Tree)

1. **How indexing improve query performance?** **(Bangladesh Satellite Company Limited - Assistant Engineer (CSE) Exam: 23.08.2025 (BUET)) [compact it 1431]**

## Relational Data Model & ER Relationships

1. What are the different types of relationships in a relational database? Explain each with examples. (Combined Bank Officer (IT) Exam: 09.05.2026) [debug it]

## Keys in DBMS

1. Difference Between Primary Key, Foreign Key, Candidate Key. (BEPRC Assistant Programmer Exam: 08.08.2026)

2. **(a) Define RDBMS. Explain the different key and primary key, candidate key, super key, and foreign key DBMS.** **(Cadet College (Combined) - Lecturer ICT Exam: 11.05.2025) [compact it 1445]**

## Indexing in DBMS

1. **সূচকের ধরন কি? এখানে প্রশ্নের উত্তর বিষয়ভিত্তিক প্রকার লেখ।** **(Assistant Programmer - Department of Immigration & Passports Exam: 15.07.2026) [compact it 1464]**

## ER Diagram & Database Design

1. BSCPL regularly publishes multiple job vacancies, where each Job is identified by a unique Job ID and contains information such as Job Title, Starting Salary, Job Description, and other relevant attributes. An Applicant is identified by a unique Applicant ID and has attributes such as Name, Date of Birth, Starting/Joining Date, Contact Information, and other details. An applicant can apply for only one job, while a particular job can receive applications from many applicants. Design the ER diagram for this system, showing the entities, attributes, primary keys, relationship, cardinalities, and participation constraints. [BSCCPL AME 21-08-2026 (BUET)]

2. **(a) Design an ER diagram for a library management systems where-** **(BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) Exam: 29.05.2025 (CS/CSE)) [compact it 1349]**
   * **(i) A library has multiple books.**
   * **(ii) Each book can have multiple copies.**

## Database Connectivity (JDBC)

1. What is JDBC? Explain the steps required to connect a Java application to a MySQL database. (Officer (IT) Exam: 31 Jul 2026) [bscs 02]

## Database Design & Data Types

1. An institute wants to create a database table named STUDENT to store student information. The table should include the columns Roll Number, Name, Department, Email, and Admission Date. Specify the most appropriate SQL data type for each column and identify which column should be defined as the Primary Key, giving a brief justification for your choice. (Officer (IT) Exam: 31 Jul 2026) [bscs 03]
