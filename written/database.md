## DBMS Architecture & Features

1. (a) DBMS এর মূল বৈশিষ্ট্য লিখুন।
   (b) HTTP ও HTTPS প্রোটোকলের মধ্যে সুরক্ষার দিক থেকে পার্থক্য ব্যাখ্যা করুন। **(Assistant Programmer - Department of Immigration & Passports Exam: 15.07.2026) [compact it 1464]**

## NoSQL, NewSQL & Modern Databases

1. **What are the limitations of DBMS and how to related newsql with SQL and No-SQL.** **(Islami Bank PLC Quality Assurance (QA) Engineer Exam: 14.03.2025 (BUET)) [compact it 1332]**

## SQL Commands (DDL, DML, DCL, TCL)

1. Example Query of DDL, DML, DCL. (BEPRC Assistant Programmer Exam: 08.08.2026)

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

## PL/SQL & Database Triggers

1. **Explain Database Trigger with example.** **(DPDC - Assistant Engineer (CSE) Exam: 17.10.2025) [compact it 1453]**

## Relational Data Model & ER Relationships

1. What are the different types of relationships in a relational database? Explain each with examples. (Combined Bank Officer (IT) Exam: 09.05.2026) [debug it]

## Keys in DBMS

1. Difference Between Primary Key, Foreign Key, Candidate Key. (BEPRC Assistant Programmer Exam: 08.08.2026)

## Indexing in DBMS

1. **সূচকের ধরন কি? এখানে প্রশ্নের উত্তর বিষয়ভিত্তিক প্রকার লেখ।** **(Assistant Programmer - Department of Immigration & Passports Exam: 15.07.2026) [compact it 1464]**

## ER Diagram & Database Design

1. BSCPL regularly publishes multiple job vacancies, where each Job is identified by a unique Job ID and contains information such as Job Title, Starting Salary, Job Description, and other relevant attributes. An Applicant is identified by a unique Applicant ID and has attributes such as Name, Date of Birth, Starting/Joining Date, Contact Information, and other details. An applicant can apply for only one job, while a particular job can receive applications from many applicants. Design the ER diagram for this system, showing the entities, attributes, primary keys, relationship, cardinalities, and participation constraints. [BSCCPL AME 21-08-2026 (BUET)]

## Database Connectivity (JDBC)

1. What is JDBC? Explain the steps required to connect a Java application to a MySQL database. (Officer (IT) Exam: 31 Jul 2026) [bscs 02]

## Database Design & Data Types

1. An institute wants to create a database table named STUDENT to store student information. The table should include the columns Roll Number, Name, Department, Email, and Admission Date. Specify the most appropriate SQL data type for each column and identify which column should be defined as the Primary Key, giving a brief justification for your choice. (Officer (IT) Exam: 31 Jul 2026) [bscs 03]
