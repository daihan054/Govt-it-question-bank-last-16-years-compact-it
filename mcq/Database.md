# Database

**Total Questions: 68** (from last 16 years government job exams)

## Table of Contents

- [Transaction & ACID (8)](#transaction-acid-8)
- [SQL Query (21)](#sql-query-21)
- [Normalization (8)](#normalization-8)
- [ER Model & Schema (6)](#er-model-schema-6)
- [DML & DDL (3)](#dml-ddl-3)
- [Keys & Constraints (6)](#keys-constraints-6)
- [General (16)](#general-16)

---

## Transaction & ACID (8)

6. A to B transfer balance but not sent to B? Which property in ACID is responsible? **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xviii]**
   (a) Atomicity
   (b) Consistency
   (c) Isolation
   (d) Durability

88. Which one of these is not included in acid property of database? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) Atomicity
   (b) Consistency
   (c) Durability
   (d) Display

9. Which one is not Database Transaction property? **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 181]**
   a) Atomicity
   b) Consistency
   c) Durability
   d) Quality

31. After a transaction completes successfully, the changes it has made to the database persist, even if there are system failures. This property of transaction is known as- **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 184]**
   a) Atomicity
   b) Consistency
   c) Isolation
   d) Durability

7. If master and transaction file have keys in same order, then it takes____ **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 209]**
   A) less time
   B) more time
   C) many hours
   D) many days

11. Why do we need to normalize a database? **(Sonali & Janata Bank Assistant Programmer Preliminary Exam: 2018) [compact it 240]**
   A) To remove redundancy
   B) To make data meaningful
   C) To make database secure
   D) To make database consistency

27. A transaction for which all committed changes are permanent is called ________ **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 273]**
   a. Atomic
   b. Consistent
   c. Isolated
   d. Durable

28. Which of the following locks the item from access of any type? **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 273]**
   a. Implicit lock
   b. Explicit lock
   c. Exclusive lock
   d. Shared lock

---

## SQL Query (21)

15. Which clause is executed first in an SQL query? **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xix]**
   (a) WHERE
   (b) SELECT
   (c) FROM
   (d) ORDER BY

17. Which of the following is a DML (Data Manipulation Language) command? **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xix]**
   (a) CREATE
   (b) DELETE
   (c) DROP
   (d) ALTER

27. Which of the following is a command of Data Definition Language (DDL)? **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xxi]**
   (a) SELECT
   (b) INSERT
   (c) UPDATE
   (d) CREATE

84. Which of the following is not a DDL statement? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) Create
   (b) Alter
   (c) Drop
   (d) Select

89. Which clause is required in an SQL query for getting information from a database? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) Update
   (b) Select
   (c) Create
   (d) Isolation

32. Consider the following Employee Table and the SQL query given: **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 185]**
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

34. Following table shows the delivery record of an online shop. Which of the SQL statements results in the largest value? **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 185]**
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

22. In SQL, the ________ command is used to recompile a view. **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 206]**
   A) COMPILE VIEW
   B) DEFINE VIEW
   C) ALTER VIEW
   D) CREATE VIEW

15. In SQL, the ________ command is used to recompile a view. **(Probashi Kallyan Bank Assistant Programmer: 2019 Exam Taker: AUST) [compact it 216]**
   A) Compile View
   B) Define View
   C) Alter View
   D) Create View

40. A shared lock allows which of the following type of transaction to occur? **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 224]**
   A) Delete
   B) Insert
   C) Read
   D) Update

7. The result of a SQL SELECT statement is a ---- **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 225]**
   A) Report
   B) form
   C) file
   D) table

12. To remove the duplicate rows from the result of an SQL Select statement, the---- qualifier specified include. **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 226]**
   A) only
   B) distinct
   C) unique
   D) single

14. The ________ clause is used to list the attributes desired in the result of a query. **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 230]**
   A) Where
   B) Select
   C) From
   D) Distinct

22. CREATE TABLE employee (name VARCHAR, id INTEGER) , What type of statement is this? **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 231]**
   A) DML
   B) DDL
   C) View
   D) Integrity constraint

24. In SQL, aggregate functions can be used in the select list or the ________ clause of a select statement or subquery. They cannot be used in a ________ clause. **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 232]**
   A) Where, having
   B) Having, where
   C) Group by, Having
   D) Group by, Where

4. The SQL statement that requires or reads data from the table is- **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 234]**
   A) Select
   B) Read
   C) Query
   D) None of the above

35. In SQL, the ________ command is used to recompile a view. **(Sonali Bank Limited Assistant Engineer (IT) Preliminary Exam: 2016) [compact it 250]**
   A) COMPLTE VIEW
   B) DEFINE VIEW
   C) ALTER VIEW
   D) CREATE VIEW

48. From where the data is captured in the SQL Server Database? **(Pubali Bank Limited Officer (IT) Preliminary Exam: 2012) [compact it 268]**
   a. Automatic call decider
   b. Automation call distributor
   c. Automatic call distributor
   d. Automatic historical data

24. With SQL how can you insert "Olsen" as the "LastName" in the "Persons" table? **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 273]**
   a. INSERT INTO Persons(LastName) VALUES('Olsen')
   b. INSERT INTO Persons (Olsen) VALUES('LastName')
   c. INSERT INTO Person ('Olsen') INTO LastName
   d. INSERT INTO Persons (LastName= 'Olsen')

26. Which SQL keyword is used to short the result set? **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 273]**
   a. ORDER
   b. SORT
   c. ORDER BY
   d. SORT BY

30. You run a SELECT statement and multiple duplicate values are retrieved. What keyword can you use to retrieve only the non-duplicate data? **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 273]**
   a. DUPLICATE
   b. SEPARATE
   c. DISTINCT
   d. INDEX

---

## Normalization (8)

24. Which one make data access from a database faster? **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xx]**
   (a) Indexing
   (b) Normalization
   (c) Denormalization
   (d) All of the above

17. Which normal form is considered adequate for normal relational database design? **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM)) [compact it 8]**
   a) 2NF
   b) 5NF
   c) 4NF
   d) 3NF

80. Which one is correct in case of normalization- **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 15]**
   (a) Normalization maximizes duplicates
   (b) Normalization reduces duplicates
   (c) Normalization eliminates duplicates
   (d) Normalization increases

82. If a table is normalized so that all its determinants are candidate keys then, the tableis in- **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) 1NF
   (b) 2NF
   (c) 3NF
   (d) BCNF

3. If you are assigned to remove partial dependency from a database, which technique you will use? **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 180]**
   a) 1NF
   b) 2NF
   c) 3NF
   d) BCNF

30. In the ________ normal form, a composite attribute is converted to individual attributes. **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 232]**
   A) First
   B) Second
   C) Third
   D) Fourth

14. Repeated data exist at— **(Bangladesh Bank Assistant Programmer Preliminary Exam: 2016) [compact it 246]**
   A) unnormalized
   B) 1NF
   C) 2NF
   D) 3NF

12. What is normalization? **(Janata Bank Limited Assistant Engineer (IT) Preliminary Exam: 2015) [compact it 258]**
   A) To Remove Redundancy
   B) To make Database
   C) To make data meaningful
   D) To make database Consistency

---

## ER Model & Schema (6)

81. If attribute A determines both attributes B and C then, it is also true that— **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 15]**
   (a) A \rightarrow B
   (b) B \rightarrow A
   (c) C \rightarrow A
   (d) (BC) \rightarrow A

40. Which of these is not a core data type? **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 208]**
   A) Lists
   B) Dictionary
   C) Class
   D) Tuples+95

38. What represents a row in a relational database? **(Combined Bank Senior Officer (IT) Exam: 2018 Exam Taker: DU) [compact it 224]**
   A) variable
   B) tuple
   C) entity
   D) field

3. Which of the following is a group of one or more attributes that uniquely identifies a row? **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 234]**
   A) Key
   B) Determinant
   C) Tuple
   D) Relation

44. Which of the following is an example of a client server model? **(Sonali Bank Limited Assistant Engineer (IT) Preliminary Exam: 2016) [compact it 250]**
   A) TELNET
   B) FTP
   C) DNS
   D) All

23. What is a tuple? **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 273]**
   a. Another name for a table in an RDBMS
   b. A row or record in a database table
   c. An attribute attached to a record
   d. Another name for the key linking different table in a database

---

## DML & DDL (3)

83. Which statements are used to create the database structure? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) DML
   (b) DDL
   (c) BNF
   (d) None of these

29. Variable which use same name in whole program and in its all routines thus best classified as- **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 213]**
   A) middle variable
   B) default variable
   C) local variable
   D) global variable

18. Which one is database language? **(BREB Assistant Junior Engineer (IT) Exam: 2019) [compact it 219]**
   A) DDL
   B) DML
   C) Both A & B
   D) None

---

## Keys & Constraints (6)

37. কোনটি দিয়ে Database Table এ uniqueness নিশ্চিত করা হয়? **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 188]**
   A) Primary Key
   B) Foreign Key
   C) Entity
   D) Relation

8. কোনটি দিয়ে Database Table এ uniqueness নিশ্চিত করা হয়? **(BPSC Assistant Network Engineer Exam: 2019) [compact it 195]**
   A) Primary Key
   B) Foreign Key
   C) Entity
   D) Relation

30. A primary key must also be- **(Combined Bank Senior Officer (IT) Exam: 2018 Exam Taker: DU) [compact it 223]**
   A) Foreign key
   B) Unique
   C) Identical
   D) Case sensitive

19. The subset of super key is a candidate key under what condition? **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 231]**
   A) No proper subset is a super key
   B) All subsets are super keys
   C) Subset is a super key
   D) Each subset is a super key

14. In an Entity-Relationship diagram many-to-many relationship corresponds to a -- in actual database. **(Janata Bank Limited Assistant Engineer (IT) Preliminary Exam: 2015) [compact it 258]**
   A) Table
   B) field
   C) row
   D) primary key

25. The primary key is selected from the ________ **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 273]**
   a. Candidate keys
   b. Composite keys
   c. Determinants
   d. Foreign keys

---

## General (16)

85. Which for loop has range of similar indexes of 'i' used in for (i = 0; i < n; i++)? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) for (i= n; i>0; i--)
   (b) for (i=n-1; i>0; i--)
   (c) for (i = 0; i = 0; i--)
   (d) for (i=n-1; i>-1; i--)

86. Data about data is called- **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) Data dictionary
   (b) Data bank
   (c) Meta Data
   (d) Warehouse

8. A filter having a single continuous transmission band with neither the upper nor the lower cutoff frequencies is zero or infinite is called- **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 190]**
   (a) Band pass filter
   (b) Low pass filter
   (c) High pass filter
   (d) Band stop filter

16. Which of the following programming language helps you to learn Android programming? **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 205]**
   A) C
   B) SQL
   C) Java
   D) Python

10. Once connection is set up, program can send SQL commands to database by using **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 210]**
   A) SQLExcelConn
   B) SQLDirect
   C) SQLExcelDirect
   D) SQLConnect

36. Which of the following logical connectives is not included in SQL? **(Combined Bank Senior Officer (IT) Exam: 2018 Exam Taker: DU) [compact it 224]**
   A) AND
   B) OR
   C) NOR
   D) NOT

34. A graph having an edge from each vertex to every other vertex is called: **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 233]**
   A) Tightly connected
   B) Strongly connected
   C) Weakly connected
   D) Loosely connected

35. Pushing an element into stack already having five elements and stack size of 5 then stack becomes- **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 233]**
   A) Overflow
   B) Crash
   C) Underflow
   D) User flow

7. Which of the following protocol is an SQL trigger support by oracle? **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 234]**
   A) Before
   B) Instead of
   C) After
   D) All of the above

15. The smallest element of array index is called it- **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 235]**
   A) Lower Bound
   B) Upper Bound
   C) Range
   D) Extraction

20. Which of the following programming helps you to learn android programming? **(Sonali Bank Limited Assistant Engineer (IT) Preliminary Exam: 2016) [compact it 246]**
   A) C
   B) SQL
   C) Java
   D) Python

1. What is the full meaning of SQL? **(BREB Assistant General Manager (IT) Preliminary Exam: 2016) [compact it 253]**
   A) Search and Query Language
   B) Simulation of Query Language
   C) Standard Query Language
   D) Structured Query Language

36. How the router makes decisions for SQL server database logs? **(Pubali Bank Limited Officer (IT) Preliminary Exam: 2012) [compact it 267]**
   a. Call router
   b. Response Router
   c. Automatic Router
   d. Static Router

29. In your program you want to use the JDBC-ODBC bridge drive. What code do you use? **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 273]**
   a. Class.callName("sun.jdbc.odbc.jdbcOdbcDriver")
   b. Class.forName("sun.jdbc.odbc.jdbcOdbcDriver")
   c. Class.callFunc("JdbcOdbcDriver")
   d. Class.Name.init("sun.jdbc.odbc.JdbcOdbcDriver")

31. Microsoft Access is a ________ **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 273]**
   a. RDBMS
   b. OODBMS
   c. ORDBMS
   d. All of these

36. Which of the following is not a type of Microsoft Access Database object? **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 274]**
   a. Table
   b. Form
   c. Worksheets
   d. Modules

---
