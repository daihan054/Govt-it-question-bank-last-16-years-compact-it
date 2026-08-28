## Normalization

1. **Which normal form is considered adequate for normal relational database design?** **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM)) [compact it 8]**
   a) 2NF
   b) 5NF
   c) 4NF
   d) 3NF

2. **Which one is correct in case of normalization-** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 15]**
   (a) Normalization maximizes duplicates
   (b) Normalization reduces duplicates
   (c) Normalization eliminates duplicates
   (d) Normalization increases

3. **If attribute A determines both attributes B and C then, it is also true that—** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 15]**
   (a) A \rightarrow B
   (b) B \rightarrow A
   (c) C \rightarrow A
   (d) (BC) \rightarrow A

4. **If a table is normalized so that all its determinants are candidate keys then, the tableis in-** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) 1NF
   (b) 2NF
   (c) 3NF
   (d) BCNF

5. **Functional dependency use in which normalizations?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Second Normal Form (2NF)

6. **"There must not be any partial dependency "Which of the following Normal Forms holds this condition?** **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 43]**
   (ক) 1NF
   (খ) 2NF
   (গ) 3NF
   (ঘ) BCNF

## SQL Commands & Queries

1. **Which statements are used to create the database structure?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) DML
   (b) DDL
   (c) BNF
   (d) None of these

2. **Which of the following is not a DDL statement?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) Create
   (b) Alter
   (c) Drop
   (d) Select

3. **Which clause is required in an SQL query for getting information from a database?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) Update
   (b) Select
   (c) Create
   (d) Isolation

4. **Which clause is executed first in an SQL query?** **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xix]**
   (a) WHERE
   (b) SELECT
   (c) FROM
   (d) ORDER BY

5. **Which of the following is a DML (Data Manipulation Language) command?** **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xix]**
   (a) CREATE
   (b) DELETE
   (c) DROP
   (d) ALTER

6. **Which of the following is a command of Data Definition Language (DDL)?** **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xxi]**
   (a) SELECT
   (b) INSERT
   (c) UPDATE
   (d) CREATE

7. **CREATE TABLE employee (name VARCHAR, id INTEGER). What type of statement is this?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 39]**
   a) DML
   b) DDL
   c) View
   d) Integrity constraint

8. **Which one of the followings sorts rows in SQL?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) SORT BY
   b) ALIGN BY
   c) ORDER BY
   d) GROUP BY

9. **Table employee has 10 records. It has a non-NULL SALARY column which is also UNIQUE. The SQL statement:** **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 27]**
   ```sql
   SELECT COUNT (*) FROM employee
   WHERE SALARY > ALL(SELECT SALARY FROM EMPLOYEE);
   ```
   Prints:
   (a) 10
   (b) 9
   (c) 5
   (d) 0

10. **Which of the following provides the ability to query information from the database and insert tuples into, delete tuples from, and modify tuples in the database?** **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 24]**
   (a) DML (Data Manipulation Language)
   (b) DDL (Data Definition Language)
   (c) Query
   (d) Relational Schema

11. **To remove a relational table from SQL database, we use ______.** **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) Delete
   (খ) Purge
   (গ) Remove
   (ঘ) Drop

## DBMS Concepts & Architecture

1. **Data about data is called-** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) Data dictionary
   (b) Data bank
   (c) Meta Data
   (d) Warehouse

2. **Which level of abstraction specifies the data and relationships between data?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Conceptual Level (Logical Level)

## Transaction Management & ACID

1. **Which one of these is not included in acid property of database?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) Atomicity
   (b) Consistency
   (c) Durability
   (d) Display

2. **A to B transfer balance but not sent to B? Which property in ACID is responsible?** **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xviii]**
   (a) Atomicity
   (b) Consistency
   (c) Isolation
   (d) Durability

3. **A transaction completes its execution is said to be-** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 41]**
   a) Committed
   b) Aborted
   c) Rolled back
   d) Successful

4. **What is the D in ACID property in database?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Durability

## Indexing & Query Optimization

1. **Which one make data access from a database faster?** **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xx]**
   (a) Indexing
   (b) Normalization
   (c) Denormalization
   (d) All of the above
   25. Priority Scheduling (Non-Preemptive) with No Arrival Time Consider the following set of processes with their burst times and priorities:
   | Process | Burst Time (BT) | Priority |
   |---|---|---|
   | P1 | 10 | 3 |
   | P2 | 1 | 1 |
   | P3 | 2 | 4 |
   | P4 | 1 | 5 |
   | P5 | 5 | 2 |
   Using Non-Preemptive Priority Scheduling (lower number = higher priority), what is the Average Turnaround Time (TAT)? **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xx]**
   (a) 10
   (b) 8.6
   (c) 12
   (d) 9.2

## SQL Joins

1. **What type of join in needed when you wish to include rows that do not have matching values?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) Equal join
   b) Natural join
   c) Outer join
   d) Inner join

## Data Warehousing & Data Mining

1. **Where is data warehousing used?** **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 22]**
   (a) Transaction System
   (b) Logical system
   (c) Decision support system
   (d) None

2. **What is the use of data cleaning?** **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 23]**
   (a) To remove the noisy data
   (b) Transformations to correct the wrong data
   (c) Correct the inconsistencies in data
   (d) All of the above

3. **Small logical units where data warehouse hold large amounts of data is known as ______.** **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 23]**
   (a) Access layers
   (b) Data marts
   (c) Data storage
   (d) Data miners

4. **Which of the following is an essential process in which the intelligent methods are applied to extract data patterns?** **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 23]**
   (a) Warehousing
   (b) Data Mining
   (c) Text Mining
   (d) Data Selection

5. **Hadoop written in which language?** **(BREB Assistant Programmer Exam: 2023) [compact it 32]**
   (a) Java
   (b) C++
   (c) Pascal
   (d) Kotlin

## Relational Model & Terminology

1. **What is the degree of relation?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** a degree of relationship represents the number of entity types that are associated with a relationship.

## Keys in DBMS

1. **The key selected from the sets of candidate keys by database design is called ______ key:** **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) Candidate
   (খ) Primary
   (গ) Super
   (ঘ) Foreign

2. **Which of the following types of table constraints prevents the entry of duplicate rows?** **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 58]**
   (ক) Foreign keys
   (খ) Primary keys
   (গ) Unique keys
   (ঘ) Candidate keys
