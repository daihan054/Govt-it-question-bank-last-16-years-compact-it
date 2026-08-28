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

7. **To remove partial dependency from a database, which technique you will use?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
   a) 1NF
   b) 2NF
   c) 3NF
   d) BCN

8. **In a schema with attributes A, B, C, D and F following set of functional dependencies are given A => B, A=>C, CD=> E, B=>D, E=>A. Which of the following functional dependencies is not implied by the above set?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 112]**
   a) CD=>AC
   b) BD=>CD
   c) BC=>CD
   d) AC=>BC

9. **Third normal form is based on the concept of ______.** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 116]**
   a) Normal Dependency
   b) Closure Dependency
   c) Functional Dependency
   d) Transitive Dependency

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

12. **Which of the following command is a type of Data Definition language command?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 128]**
   a) Create
   b) Update
   c) Deleted
   d) Select
   24. Let transaction T1 has obtained a shared mode lock S on data item Q and transaction T2 has obtained an exclusive mode lock X on data item R. Consider the following statement.
   I: T1 can read Q but cannot write Q.
   II: T2 can read R but cannot write R.
   Which of the above statements is / are valid? **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 128]**
   a) Only I
   b) Only II
   c) Both I and II
   d) Neither I nor II

13. **Which one is the correct SQL statement to find the second highest mark from STUDENT database contains the marks of all students?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
   a) Select MAX(marks) from *STUDENT* WHERE marks NOT IN (select MAX(marks) from *STUDENT*
   b) Select MAX(marks) from *STUDENT* WHERE marks IN (select MAX(marks) from *STUDENT*
   c) select MAX(marks) from *STUDENT*
   d) select MAX(marks) from *STUDENT* WHERE marks NOT IN (select MIN(marks) from *STUDENT*

14. **Which of the following is not a DDL command?** **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
   a) Create
   b) Drop
   c) Alter
   d) Update

15. **The SQL statement** **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
   ```sql
   SELECT ROUND (45.926, -1) FROM DUAL;
   ```
   a) is illegal
   b) prints garbage
   c) prints 045.926
   d) prints 50

16. **When three or more AND & OR conditions are combined, it is easier to use the SQL keyword(s):** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 113]**
   a) LIKE only
   b) IN only
   c) NOT IN only
   d) Both IN and NOT IN

17. **How to select all data from student table starting the name from letter 'r'?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 113]**
   a) SELECT * FROM student WHERE name LIKE 'r%';
   b) SELECT * FROM student WHERE name LIKE '%r%';
   c) SELECT * FROM student WHERE name LIKE '%r';
   d) SELECT * FROM student WHERE name LIKE '_r%';

18. **Which of the following are the five built-in functions provided by SQL?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 115]**
   a) COUNT, SUM, AVG, MAX, MIN
   b) SUM, AVG, MIN, MAX, MULT
   c) SUM, AVG, MULT, DIV, MIN
   d) SUM, AVG, MIN, MAX, NAME

19. **What does this query do?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 115]**
   ```sql
   SELECT employee_number, name FROM
   employees AS Parent WHERE salary> (SELECT AVG (salary)
   FROM employee WHWRE department= Parent department) ,
   ```
   a) Finds the name and ID of employees who get more than average
   b) Finds the employee's name and ID of those who gets more than average salaries of all the departments' salaries.
   c) Finds the name and ID of employees who get more than average salaries of his own department.
   d) None

20. **What will be the output of the following SQL "Select Round (232.420, -2) AS Round Value"?** **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 103]**
   (a) 240
   (b) 200
   (c) 233
   (d) Syntax error

21. **Consider the following relational data table, Employee. Now, find the output for the following SQL Statement?** **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 81]**
   ```sql
   SELECT COUNT (*) FROM Employee, Employee, Employee
   ```
   a. 4
   b. 27
   c. 32
   d. 64

22. **Table Employee has 10 records. It has a non-NULL SALARY column which is also UNIQUE. The SQL statement** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 88]**
   ```sql
   SELECT COUNT(*) FROM Employee WHERE SALARY > ANY (SELECT SALARY FROM EMPLOYEE);
   ```
   prints
   a. 0
   b. 5
   c. 9
   d. 10

23. **Following table shows the delivery record of an online shop. Which of the SQL statements results in the largest value?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 91]**
   | Product ID | Delivery Data | Quantity |
   |---|---|---|
   | F101 | 2021-03-17 | 3 |
   | H201 | 2021-03-17 | 2 |
   | F101 | 2021-03-16 | 1 |
   | H201 | 2021-03-16 | 2 |
   a. SELECT AVE(Quantity) FROM Delivery Record WHERE Product No. = 'F101'
   b. SELECT COUNT (*) FROM Delivery Record
   c. SELECT SUM (Quantity) FROM Delivery Record WHERE data = '2021-03-16'
   d. SELECT MAX (Quantity) FROM Delivery Record

## DBMS Concepts & Architecture

1. **Data about data is called-** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) Data dictionary
   (b) Data bank
   (c) Meta Data
   (d) Warehouse

2. **Which level of abstraction specifies the data and relationships between data?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** Conceptual Level (Logical Level)

3. **Which of the following is not a function of a database administrator?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 131]**
   a) Database the design
   b) Backing up the database
   c) Query processing
   d) User coordination

4. **Assume that you want to improve database performance and willing to see the amount of swap space. Which command you can use in LINUX OS environment?** **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
   a) Lsps -a
   b) Swapinfo -m
   c) Swapon -s
   d) Swap -l and Swap -s

5. **In oracle to change the DB_Block_size parameter, you need to-** **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
   a) Re-create the database
   b) Alter the database
   c) Move database to temporary
   d) Update the table types of the database

6. **Which of the following controls the execution of application program and UI in two tier client/server architecture?** **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
   a) Modulation side
   b) Server side
   c) Host side
   d) None of the above

7. **LGWR process writes information into-** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 112]**
   a) Database files
   b) Control Files
   c) Redo log Files
   d) All of the above

8. **Data integrity problems in a DBMS is caused due to-** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 114]**
   a) Missing Data
   b) Data inconsistency
   c) Data Redundancy
   d) Security constraints

9. **A collection of conceptual tools for describing data, data relationships, data semantics, and consistency constraints, is known as-** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 114]**
   a) Data organization
   b) Data Binding
   c) Data schemas
   d) Data models

10. **Which is the oracle component that contains the memory structures and background process?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) Instance
   b) Server
   c) SGA
   d) Database files

11. **The three different application logic components are which of the following?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) Presentation, Client, and Storage
   b) Presentation, Client, and Processing
   c) Presentation, Processing, and Storage
   d) Presentation, Processing, and Network

12. **Of the functions provided by a DBMS. Which of the following is a means for achieving protection for data confidentiality?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) Checking referential constraints when the data is updated
   b) Managing a transaction that combines a series of processes as a logical Unit.
   c) Managing the data access rights of users.
   d) Placing an exclusive lock on the data before it is updated

13. **Oracle materialized views or SNAPSHOTS is used-** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) Hiding data from users
   b) Dynamic data replication
   c) Table Space Reduction
   d) Data Abstraction

14. **A distributed database has which of the following advantages over a centralized database?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) Software cost
   b) Software complexity
   c) Slow Response
   d) Modular growth

15. **In Oracle DBMS, LGWR process is a-** **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 100]**
   (a) Foreground Process
   (b) Background Process
   (c) High Priority Process
   (d) Batch Process

16. **Which one of the following is a No-SQL Database?** **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 103]**
   (a) MongoDB
   (b) CasperDB
   (c) ZBase
   (d) All of the above

17. **Which one of the following statements is true with respect to a Database Management System?** **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 104]**
   (a) Super key and candidate keys are similar
   (b) Candidate keys and Unique Keys are similar
   (c) Unique Keys and Primary Keys are similar
   (d) Candidate keys and Primary keys are similar

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

5. **Which one of the following commands is used to restore the database to the last committed state?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
   a) Save point
   b) Rollback
   c) Commit
   d) None of the

6. **Which one is not Database Transaction property?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]**
   a) Atomicity
   b) Consistency
   c) Durability
   d) Quality

7. **Which one of the following is a failure to a system?** **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
   a) Boot crash
   b) Read failure
   c) Transaction failure
   d) All of the mentioned

8. **How can your rollback a committed transaction in any DBMS?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 112]**
   a) Using SQL rollback commands
   b) Restoring the data from backups
   c) Run the transaction again in Reverse order
   d) All of the Above

9. **The packaged procedure that makes data in form permanent in the Database is-** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 113]**
   a) Post
   b) Post form
   c) Commit form
   d) None of the above

10. **ROLLBACK command is used to undo the changes made by-** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 115]**
   a) DDL commands
   b) TCL commands
   c) DML Commands
   d) Commit command

11. **Why is set transaction used in an oracle DBMS?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) For placing a name on a transaction
   b) For committing a transaction
   c) For locking a transaction
   d) To setup transaction user parameters.

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

2. **Related records of the different relations can be stored on the same block using which file organization technique?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]**
   a) Heap file organization
   b) Sequential file organization
   c) Hashing file organization
   d) Multi-table Clustering file organization

3. **Which of the following is correct for the Create index command?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 116]**
   a) Insert index index_name on table_name
   b) Insert index index_name on database_name;
   c) Create index index_name on database_name;
   d) Create index index_name on table_name;

4. **Database index speeds up-** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) Select queries
   b) Where clauses
   c) Update query
   d) Both a and b

5. **Which of the following index is automatically created by the database server when an object is created?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) Implicit
   b) Single column
   c) Unique
   d) composite

## SQL Joins

1. **What type of join in needed when you wish to include rows that do not have matching values?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) Equal join
   b) Natural join
   c) Outer join
   d) Inner join

2. **Which type of JOIN operation in SQL command is used to returns that do not have matching values?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 126]**
   a) Natural Join
   b) EQUI Join
   c) Outer Join
   d) All of the above

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

6. **Business Intelligence (BI) reporting analyses can be performed using** **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
   a) standard SQL only
   b) extensions to SQL only
   c) OLAP only
   d) Both standard SQL and extensions to SQL

7. **A star schema has what type of relationship between a dimension and fact table?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 115]**
   a) Many-to-many
   b) One-to-one
   c) One-to-many
   d) All of the above

8. **Finding useful pattern from the data in a database is known as-** **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 101]**
   (a) Data Visualization
   (b) Data Mining
   (c) Data Analytics
   (d) All of the above

## Relational Model & Terminology

1. **What is the degree of relation?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** a degree of relationship represents the number of entity types that are associated with a relationship.

2. **Which one of the following is true for a tuple in a database?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 116]**
   a) A tuple in a database represents a column
   b) A tuple in a database represents database schema.
   c) A tuple in a database represents a Record
   d) A tuple in a database represents a Database topology

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

3. **Referential integrity in a DBMS is a form of-** **(Sonali and Janata Bank Assistant Database Administrator Exam: 25.09.2021) [compact it 111]**
   a) Foreign key
   b) Primary key
   c) Assertion
   d) Referential constraint

4. **Needing to assess the validity of assumed referential integrity constraints on foreign keys is a(n) _________ of normalization.** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 113]**
   a) advantage
   b) disadvantage
   c) either an advantage or disadvantage
   d) neither an advantage nor disadvantage

5. **The maximum number of super keys for the relation schema R (E, F, G, H) with E as the key is-** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) 5
   b) 6
   c) 7
   d) 8

## ER Diagram & Data Modeling

1. **Let E1 and E2 be two entities in an E/R diagram with simple single-valued attributes. R1 and R2 are two relationships between E1 and E2, where R1 is one-to-many and R2 is many-to-many. R1 and R2 do not have any attributes of their own. What is the minimum number of tables required to represent this situation in the relational model?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 112]**
   a) 2
   b) 3
   c) 4
   d) 5

2. **Which of the following is an appropriate description of the mapping between the relational model and relational database as its implementations?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 114]**
   a) A domain is mapped to a character type or a character string type.
   b) A relation is mapped to a table
   c) Attributes and columns are ordered from left to right
   d) Neither tuples nor rows have duplicates

3. **What is the min and max number of tables required to convert an ER diagram with 2 entities and 1 relationship between them with partial participation constraints of both entities?** **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 105]**
   (a) Min 1 and max 2
   (b) Min 1 and max 3
   (c) Min 2 and max 3
   (d) Min 2 and max 2

4. **Consider an Entity-relationship from entity set E1 to entity set E2. If E1 and E2 participate totally in R and cardinality of E1 is greater that the cardinality of E2. Which of the following is true about R?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 90]**
   a. Every entity in E1 is associated with exactly one entity in E2
   b. Some entity in E1 is associated with more than one entity in E2
   c. Every entity in E2 is associated with exactly one entity in E1
   d. Every entity in E2 is associated with at most one entity in E1

## PL/SQL & Triggers

1. **What are the different events in Triggers?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 113]**
   a) Define, Create
   b) Drop, Comment
   c) Insert, Update, Delete
   d) Select, Commit

2. **How can you generate debugging output from PL/SQL?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 114]**
   a) DBMS_SQL
   b) DBMS_OUTPUT
   c) DBMS_PIPE
   d) DBMS_LOB

3. **What is GET_BLOCK property?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 114]**
   a) Restricted procedure
   b) Unrestricted procedure
   c) Library function
   d) None of the above

4. **Which is not the UTL_FILE function-** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) FOPEN()
   b) File_Close()
   c) FCOPY
   d) FFLUSH()

## Database Connectivity (JDBC/ODBC)

1. **Embedded SQL is which of the following?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 115]**
   a) Hard-coded SQL statements in a program language such as Java.
   b) The process of making an application capable of generating specific SQL code on the fly
   c) Hard-coded SQL statements in a procedure.
   d) Hard-coded SQL statements in a trigger.

2. **The Application program interface in a two-tier architecture DBMS is provided by-** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) Close module connectivity
   b) Open module connectivity
   c) Open database connectivity
   d) Close database connectivity

## Concurrency Control & Locking

1. **Which of the following is not a factor in determining the concurrency control behavior of SQL Server?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) Lock level
   b) Transaction isolation level
   c) Cursor concurrency setting
   d) Locking hints

2. **In a DBMS, when multiple transaction programs update the same database simultaneously, which of the following is a technology that is used to prevent logical contradictions?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) Exclusive Control
   b) Integrity constraint
   c) Normalization
   d) Reorganization

3. **Which of the below is responsible for controlling the interaction among simultaneous transaction?** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 117]**
   a) Serializable controller
   b) Concurrency Control Manager
   c) Transportation management system
   d) Multiple Access Protocol

4. **In strict two phase locking protocol-** **(Sonali and Janata Bank Assistant Database Administrator 25-09-2021) [compact it 118]**
   a) All exclusive mode locks taken by transaction be held until transaction commit
   b) All exclusive mode locks taken by transaction can be released before transaction commits
   c) All locks can be released before transaction commits
   d) None of these
