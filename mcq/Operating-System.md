# Operating System

**Total Questions: 33** (from last 16 years government job exams)

## Table of Contents

- [Process Management (10)](#process-management-10)
- [CPU Scheduling (5)](#cpu-scheduling-5)
- [Memory Management (4)](#memory-management-4)
- [Synchronization (4)](#synchronization-4)
- [Deadlock (1)](#deadlock-1)
- [General (9)](#general-9)

---

## Process Management (10)

13. A process needs I/O operations, it switches to _____ **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xix]**
   (a) Ready
   (b) Running
   (c) Waiting (Blocked)
   (d) Terminated

46. A system has 6 identical resources and N processes competing for them. Each process can request at most 2 resources. Which one of the following values of N could lead to a deadlock? **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 12]**
   (a) 1
   (b) 2
   (c) 3
   (d) 4

7. Which one is wrong statement for BIOS of a computer? **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 181]**
   a) Connect microprocessor and I/O
   b) Manages data flow
   c) Loads the operating system
   d) Provide storage

27. A common representation of process scheduling is - **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 192]**
   (a) Static diagram
   (b) Scheduling queues
   (c) Queuing diagram
   (d) Process control block

35. Who preside the interface between a process and the OS? **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 193]**
   (a) Kernel
   (b) System calls
   (c) Command
   (d) Graphical user

36. To execute a program, an OS creates a number of ________, each one for, running a different program. **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 194]**
   (a) Processors
   (b) Threads
   (c) Virtual processors
   (d) Kernel

8. What is long term scheduling? **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 230]**
   A) It selects which process has to be brought into the ready queue
   B) It selects which process has to be executed next and allocates CPU
   C) It selects which process to remove from memory by swapping
   D) It selects which process needs to be killed next

13. Multi-Threaded programs are- **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 230]**
   A) Lesser prone to deadlocks
   B) more prone to deadlocks
   C) not at all prone to deadlock
   D) always results in deadlocks

25. Which one of these interfaces is implemented by thread class? **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 237]**
   A) Set
   B) Connections
   C) Runnable
   D) None of above

36. The main thread of cloud-based provisioning is-? **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 238]**
   A) Cost
   B) Security
   C) Visualization
   D) All of above

---

## CPU Scheduling (5)

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

13. Which of the following is major part of time taken when accessing data on the disk? **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 205]**
   A) Settle time
   B) Rotational delay
   C) Waiting time
   D) Seek time

23. Which of the following process scheduling algorithm may lead to starvation? **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 206]**
   A) FIFO
   B) Round Robin
   C) Shortest Job Next
   D) None of these

9. The interval from the time of submission of a process to the time of completion is termed is ________. **(Janata Bank Limited Assistant Engineer (IT) Preliminary Exam: 2015) [compact it 259]**
   A) Waiting time
   B) processing time
   C) turnaround time
   D) throughput

28. Which approach is used in the client server model of the cluster? **(Janata Bank Limited Assistant Engineer (IT) Preliminary Exam: 2015) [compact it 261]**
   A) Load configuration
   B) FIFO
   C) LIFO
   D) Round robin

---

## Memory Management (4)

21. Which of the following page replacement algorithms suffers from Belady’s anomaly? **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM)) [compact it 8]**
   a) FIFO
   b) LRU
   c) Optimal Page Replacement
   d) Both LRU and FIFO

45. To keep track of how many frames have been allocated, how many are there, and how many are available, operating system maintain a— **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 12]**
   (a) Memory table
   (b) Page table
   (c) mapping table
   (d) frame table

48. An increase in a computer's RAM leads to a typical improvement in performance because: **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 13]**
   (a) Virtual memory increases
   (b) Fewer segmentation faults occur
   (c) A larger RAM is faster
   (d) Fewer page faults occur

10. A page fault occurs ________ **(Bangladesh Bank Assistant Maintenance Engineer Exam: 2011) [compact it 270]**
   a. When the page is not in the memory
   b. When the page is in the memory
   c. When the process inters into the blocked state
   d. When the process is in the ready state

---

## Synchronization (4)

47. A counting semaphore was initialized to 10. Then 6 wait operations and 4 signal operations were completed on this semaphore. The resulting value of the semaphore is___ **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 13]**
   (a) 0
   (b) 10
   (c) 8
   (d) 12

50. A critical section is a program segment- **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 13]**
   (a) which should run in a certain specified amount of time
   (b) which avoids deadlocks
   (c) where shared resources are accessed
   (d) which must be enclosed by a pair of semaphore (wait and signal) operations

8. CRT monitor produce image by ________ **(Bangladesh Bank Assistant Maintenance Engineer Exam: 2011) [compact it 270]**
   a. Laser beam
   b. Electron beam
   c. Light beam
   d. ink jet

9. Monitor image is refreshed at least ________ **(Bangladesh Bank Assistant Maintenance Engineer Exam: 2011) [compact it 270]**
   a. 1 times/sec
   b. 50 times/sec
   c. 60 time/sec
   d. 100 times/sec

---

## Deadlock (1)

16. When there is a large logical address space, the best way of paging would be ________. **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 231]**
   A) Not to page
   B) a two-level paging algorithm
   C) not all prone to deadlock
   D) all of the above

---

## General (9)

38. The request and release of resources are- **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 194]**
   (a) Command line
   (b) Interrupts statements
   (c) System calls
   (d) Special program

19. সর্বাধিক ব্যবহৃত Operating system কোনটি? **(BTRC Sub-Assistant Director (Technical) Exam: 2019 (IBA)) [compact it 200]**
   A. Linux
   B. Windows
   C. MAC OS
   D. Unix

4. Which of these data types is used by operating system to manage the Recursion in Java? **(Combined Bank Senior Officer (IT) Exam: 2018 Exam Taker: DU) [compact it 220]**
   A) Array
   B) Stack
   C) Queue
   D) Tree

5. Which of the following is an incorrect statement about packages? **(Combined Bank Senior Officer (IT) Exam: 2018 Exam Taker: DU) [compact it 220]**
   A) Package defines a namespace in which classes are stored
   B) A package can contain other packages within
   C) A package can be renamed without renaming the directory, in which the classes are stored
   D) Java uses file system directories to store packages

18. What is the mounting of file system? **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 231]**
   A) creating of a file system
   B) deleting a file system
   C) attaching portion of the file system into a directory structure
   D) removing portion of the file system into a directory structure

29. The main program in an operating system is called: **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 232]**
   A) kernel
   B) file manager
   C) Directory
   D) NOS

26. Which is correct for stack? **(Bangladesh Bank Assistant Programmer Preliminary Exam: 2016) [compact it 243]**
   A) FIFO
   B) LIFO
   C) Both A, B
   D) None

15. Which one loads first when you boot up your Computer? **(Sonali Bank Limited Assistant Engineer (IT) Preliminary Exam: 2016) [compact it 247]**
   A) BIOS
   B) Operating System
   C) Keyboard driver
   D) None of them

10. Which one is not operating system software? **(BREB Assistant General Manager (IT) Preliminary Exam: 2016) [compact it 254]**
   A) DOS
   B) LINUX
   C) Windows
   D) Oracle

---
