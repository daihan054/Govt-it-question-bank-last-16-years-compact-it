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

10. **If you are told to remove the inconsistency from the course table which normalization technique you will use-** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 167]**
   a) 1NF
   b) 2NF
   c) 3NF
   d) BCNF

11. **If you are assigned to remove partial dependency from a database, which technique you will use?** **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 180]**
   a) 1NF
   b) 2NF
   c) 3NF
   d) BCNF

12. **The table in below violates the Normal Form(s). Which normal form it violates?** **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 150]**
   a) All of normal forms listed here
   b) 3NF
   c) 2NF
   d) 1NF

13. **Why do we need to normalize a database?** **(Sonali & Janata Bank Assistant Programmer Preliminary Exam: 2018) [compact it 240]**
   A) To remove redundancy
   B) To make data meaningful
   C) To make database secure
   D) To make database consistency

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

24. **Which is not the steps of SQL Query processing?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 163]** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   a) Parsing
   b) Translation
   c) Optimization
   d) None

25. **Which one is the Data Control Language (DCL) in SQL?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
   a) Insert
   b) Create
   c) Drop
   d) Grant

26. **We can create a “View” of a relation using the “create view_name” command in SQL analyze the following information about view and find which option is correct-** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
   a) View is not visible to user
   b) It is not a virtual table
   c) It is not a part of the logical model
   d) View cannot be updated

27. **Consider the following “staff” table** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 166]**
   | staff_name | staff_dep | city |
   |---|---|---|
   | Riaz | CSE | Dhaka |
   | Toha | EEE | Rajshahi |
   What should be the query to find the output like “Riaz(CSE)” from the staff table?
   a) select staff_name || ‘(‘|| staff_dep ||’)’ FROM staff where city= ‘Dhaka’
   b) select staff_name ‘(‘|| staff_dep ||’)’ FROM staff where city== ‘Dhaka’
   c) select staff_name || ‘(‘|| staff_dep ’)’|| FROM staff where city= ‘Dhaka’
   d) select staff_name || ‘(‘ staff_dep ||’)’ FROM staff where city= ‘Rajshahi’

28. **What is the maximum length of the “varchar” in the database?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 167]**
   a) 35000
   b) 100
   c) 65535
   d) 255

29. **Assume that in a table named “student” the cgpa is calculated using the all course’s gpa. What kind of attribute cgpa is?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   a) Multivalued
   b) Derived
   c) Simple
   d) Composite

30. **What is wrong statements for SQL?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   a) Non-procedural language
   b) Input can be several tables
   c) Output is always a single table
   d) Output can be multiple table

31. **The ________ operation, denoted by -, allows us to find tuples that are in one relation but are not in another.** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 168]**
   a) Union
   b) Set-difference
   c) Difference
   d) Intersection

32. **Consider the following Employee Table and the SQL query given:** **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 185]**
   | id | Date | Work_hour |
   |---|---|---|
   | 1 | 2020-10-18 | 8 |
   | 1 | 2020-10-17 | 8 |
   | 1 | 2020-10-16 | 9 |
   | 2 | 2020-10-18 | 7 |
   | 2 | 2020-10-16 | 8 |
   | 3 | 2020-10-16 | 6 |
   SELECT id, sum(work_hour) from Employee Where Work hour>6 Group BY ID;
   How many rows are returned by the SQL query?
   a) 3
   b) 4
   c) 2
   d) 0

33. **Following table shows the delivery record of an online shop. Which of the SQL statements results in the largest value?** **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 185]**
   | Product Id | Date | Quantity |
   |---|---|---|
   | F101 | 2020-10-17 | 3 |
   | H201 | 2020-10-17 | 2 |
   | F101 | 2020-10-16 | 1 |
   | H201 | 2020-10-16 | 2 |
   a) SELECT AVE(Quantity) FROM Delivery Record WHERE Product id='F101'
   b) SELECT COUNT (*) FROM Delivery Record
   c) SELECT SUM (Quantity) FROM Delivery Record WHERE Date = '2020-10-16'
   d) SELECT MAX (Quantity) FROM Delivery Record

34. **What is the advantage of using ‘case’ while doing the update operation?** **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 150]**
   a) No proper sequence is required to maintain.
   b) It is much easier to write code with ‘case’ keyword.
   c) Update with ‘case’ provides significant time improvement.
   d) None of these above.

35. **উল্লেখিত কোনটি Database aggregate এর function?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 187]** **(BPSC Assistant Network Engineer Exam: 2019) [compact it 197]**
   A) where
   B) sum
   C) select
   D) from

36. **নিচের কোনটি Database তুলনা করার কাজে ব্যবহার হয়?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 188]**
   A) BETWEEN
   B) ANY
   C) IN
   D) COMPARE

37. **কোনটি দিয়ে Database Table এ uniqueness নিশ্চিত করা হয়?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 188]** **(BPSC Assistant Network Engineer Exam: 2019) [compact it 195]**
   A) Primary Key
   B) Foreign Key
   C) Entity
   D) Relation

38. **In SQL, the ________ command is used to recompile a view.** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 206]** **(Probashi Kallyan Bank Assistant Programmer: 2019 Exam Taker: AUST) [compact it 216]**
   A) COMPILE VIEW
   B) DEFINE VIEW
   C) ALTER VIEW
   D) CREATE VIEW

39. **Which one is database language?** **(BREB Assistant Junior Engineer (IT) Exam: 2019) [compact it 219]**
   A) DDL
   B) DML
   C) Both A & B
   D) None

40. **The SQL statement that requires or reads data from the table is-** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 234]**
   A) Select
   B) Read
   C) Query
   D) None of the above

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

18. **The collection of information stored in the database at a particular moment is called-** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
   a) Schema
   b) Instance
   c) Relation
   d) Record

19. **Running the given task in less time by increasing the degree of parallelism in DBMS is called ________.** **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 174]**
   a) scale up
   b) roll up
   c) speedup
   d) Data Warehouse

20. **In user facilities, copying of all records onto a main store from permanent store is considered as-** **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 209]**
   A) delete file
   B) rename file
   C) save file
   D) load file

21. **If master and transaction file have keys in same order, then it takes____** **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 209]**
   A) less time
   B) more time
   C) many hours
   D) many days

22. **File used to update information in computer's master file is classified as** **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 210]**
   A) transaction file
   B) direct file
   C) order file
   D) sequence file

23. **Interleaving of records to form one file containing all records is classified as ____.** **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 212]**
   A) merging
   B) finding
   C) file learning
   D) searching

24. **Set of numbers used to check all groups record within limits of data is classified as-** **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 213]**
   A) variable check
   B) decimal check
   C) type check
   D) range check

25. **Process of converting data or information in the form of which is readily available for processing is called-** **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 214]**
   A) encoding
   B) decoding
   C) translating
   D) data organization

26. **Which of the following term refers to the degree to which data in a database system are accurate and correct?** **(Probashi Kallyan Bank Assistant Programmer: 2019 Exam Taker: AUST) [compact it 217]**
   A) Data integrity
   B) Data security
   C) Data Validity
   D) None of these

27. **Which one is an example of DBMS?** **(BTRC Sub-Assistant Director (Technical) Exam: 2019 (IBA)) [compact it 201]**
   A. MS word
   B. MS Excel
   C. C++
   D. MS Access

28. **In the hypermedia database, information bits are stored in the form of:** **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 193]**
   (a) Cubes
   (b) Nodes
   (c) Signals
   (d) Symbols

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

6. **Which one is not Database Transaction property?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]** **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 181]**
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

12. **After a transaction completes successfully, the changes it has made to the database persist, even if there are system failures. This property of transaction is known as-** **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 184]**
   a) Atomicity
   b) Consistency
   c) Isolation
   d) Durability

13. **It is a necessary requirement that the transaction is guaranteed to complete or the transaction is never started, so that an inconsistent state would not be visible except during the execution of the transaction. Such a property of transaction is known as-** **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 154]**
   a) Atomicity
   b) Consistency
   c) Isolation
   d) Durability

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

6. **Related records of the different relations can be stored on the same block using which file organization technique?** **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 177]**
   a) Heap file organization
   b) Sequential file organization
   c) Hashing file organization
   d) Clustering file organization

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

3. **In a table an attribute named interest is defined as follows,** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
   When which one is the correct format for the interest columns?
   a) 65.2
   b) 7.2
   c) 19.02
   d) 1.03

4. **Which one is not unary operator in relational algebra?** **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 157]**
   A) Select
   B) Project
   C) Union
   D) Renames

5. **Which one is an entity?** **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 157]**
   A) Roll No.
   B) Student
   C) Passport No.
   D) Department ID

6. **Which one is TRUE for FIRD?** **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 158]**
   A) Uses electromagnetic signal
   B) Uses laser beam
   C) Uses optical signal
   D) Uses infrared

7. **Flat file database is most useful for ________.** **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 163]**
   A) Large scale users
   B) Banking
   C) Small-group situation.
   D) Chain stores

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

6. **Which of the following is a group of one or more attributes that uniquely identifies a row?** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 234]**
   A) Key
   B) Determinant
   C) Tuple
   D) Relation

7. **For every relationship, how many possible sets of minimum cardinalities are there?** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 235]**
   A) Two
   B) Three
   C) Four
   D) Six

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

5. **A relationship is given below in an ER diagram How many tables can be created (preferred) from below diagram?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
   ```
   +------------+               +-----------+
   | instructor |               |  student  |
   +------------+               +-----------+
   | ID         |  /---------\  | ID        |
   | name       |--< advisor >--| name      |
   | salary     |  \---------/  | tot_cred  |
   +------------+               +-----------+
   ```
   a) No definite numbers
   b) Two
   c) Three
   d) Two or Three

6. **A relationship is given below in an ER diagram. How many tables can be created (preferred) from below diagram?** **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 184]**
   ```
   +------------+               +------------+
   | instructor |               |   student  |
   +------------+   +---------+ +------------+
   | ID         |<--| advisor | | ID         |
   | name       |   +---------+ | name       |
   | salary     |               | tot_cred   |
   +------------+               +------------+
   ```
   a) One
   b) Two
   c) Three
   d) No definite numbers

7. **Consider an Entity-relationship (ER) model where R is defined as a many-to-one relationship from entity set E1 to entity set E2. If E1 and E2 participate totally in R and cardinality of E1 is greater than the cardinality of E2, which of the following is true about R?** **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 184]**
   a) Every entity in E1 is associated with exactly one entity in E2
   b) Some entity in E1 is associated with more than one entity in E2
   c) Every entity in E2 is associated with exactly one entity in E1
   d) Every entity in E2 is associated with at most one entity on E1

8. **A relationship is given below in an ER diagram. How many tables can be created (preferred) from below diagram?** **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 149]**
   a) Two
   b) Three
   c) Two or Three
   d) No definite numbers

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

5. **Which of the following protocol is an SQL trigger support by oracle?** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 234]**
   A) Before
   B) Instead of
   C) After
   D) All of the above

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

3. **A major challenge in mixing SQL with a general-purpose language is mismatching in the** **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 209]**
   A) Definition of data
   B) Manipulation of data
   C) Execution of data
   D) Output of data

4. **Once connection is set up, program can send SQL commands to database by using** **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 210]**
   A) SQLExcelConn
   B) SQLDirect
   C) SQLExcelDirect
   D) SQLConnect

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
