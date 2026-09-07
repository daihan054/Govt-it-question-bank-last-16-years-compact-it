<!-- TOC START -->
**Table of Contents** — 7 subtopics · 74 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Process Management & Scheduling](#process-management--scheduling-24) | 24 |
| 2 | [OS Concepts & Multiprogramming](#os-concepts--multiprogramming-16) | 16 |
| 3 | [Virtual Memory & Paging](#virtual-memory--paging-13) | 13 |
| 4 | [Linux Commands & Administration](#linux-commands--administration-9) | 9 |
| 5 | [Deadlock](#deadlock-6) | 6 |
| 6 | [File Systems & Disk Management](#file-systems--disk-management-4) | 4 |
| 7 | [Process Synchronization](#process-synchronization-2) | 2 |

<!-- TOC END -->

---

## Process Management & Scheduling (24)

1. **A process needs I/O operations, it switches to _____** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xix (ET: DU)]*
   (a) Ready
   (b) Running
   (c) Waiting (Blocked)
   (d) Terminated

2. **Which of the following scheduling algorithm is non preemptive?** *[NPCBL Executive Trainee (Software) 2023 compact it 37 (ET: N/A)]*
   (a) Shortest Job First
   (b) FCFS
   (c) Rounf Robin
   (d) Priority Scheduling

3. **Time during which a job is processed by the Computer is:** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 56 (ET: N/A)]*
   (ক) Delay time
   (খ) Real time
   (গ) Execution time
   (ঘ) Process time

4. **In Unix operating system, which system call is used for creating a new process?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 126 (ET: N/A)]*
   a) Exec()
   b) Create Process ()
   c) Fork ()
   d) None of them

5. **A job which is schedule to run periodically at fixed times or intervals is known as-** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 99 (ET: N/A)]*
   (a) Batch Job
   (b) Cron job
   (c) Shell Script
   (d) None of the above

6. **Which one of the following statements is true with respect to Printer Daemon process?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 103 (ET: N/A)]*
   (a) The printer daemon of Operating System runs in kernel mode.
   (b) Jobs in the printer daemon queue cannot be removed once inserted.
   (c) Printer daemon application runs only when it is printing.
   (d) Printer daemon runs as a service in Operating System

7. **Which of the following Process scheduling algorithm is highly improbable to be implemented?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 107 (ET: N/A)]*
   (a) FCFS Scheduling
   (b) Priority Scheduling
   (c) Shortest Job First Scheduling
   (d) None of the above

8. **A jet Aircraft employs a system for monitoring the rpm, pressure and temperature values of its engines using sensors that operate as follows:** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 179 (ET: N/A)]*
   RPM sensor (R) output = 0 only when \text{speed} < 4800\text{rpm}
   Pressure sensor (P) output = 0 only when \text{pressure} < 220\text{ psi}
   Temperature sensor (T) output = 0 only when \text{temperature} < 200^{\circ}\text{F}
   Following figure shows the logic circuit that controls a cockpit warning light for certain combinations of engine conditions. Assume that a HIGH at the output W activates the warning light. What engine condition will give a warning to the pilot?
   ```
   Temp    T
   sensor -----\
   \  +---\
   --|   \
   Pressure       |    )--- W  *
   sensor -- P     |   /       Warning
   |  +- | --/        light
   RPM    +-)| \
   sensor ---+-)|  )o--
   R   | /
   ```
   a) Temperature (T) is > 200^{\circ}\text{F} and pressure (P) > 220\text{ psi}
   b) Temperature (T) is > 200^{\circ}\text{F} and speed (R) < 4800\text{ rpm}
   c) Option (a) and (b)
   d) d) None of the above

9. **What is the disadvantage of multithreading?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 165 (ET: N/A)]*
   a) Share the same address space
   b) Simultaneous access to multiple application
   c) Low cost communication
   d) Difficulty in managing concurrency

10. **The time needs from the process arrival to the completion of that process is called** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 165 (ET: N/A)]*
   a) Waiting time
   b) Response time
   c) Turnaround time
   d) Throughput

11. **Which is not the state of a process in an Operating System?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 166 (ET: N/A)]*
   a) New
   b) Sleep
   c) Terminated
   d) Ready

12. **The maximum number of processes that can be in ready state in computer system with n CPU's is—** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 204 (ET: AUST)]*
   A) n
   B) \text{n}^2
   C) 2n
   D) independent of n

13. **In UNIX, processes that have finished execution but have not yet had their status collected are known as-** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 205 (ET: AUST)]*
   A) Sleeping processes
   B) Stopped processes
   C) Zombie processes
   D) Orphan processes

14. **Which of the following process scheduling algorithm may lead to starvation?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 206 (ET: AUST)]*
   A) FIFO
   B) Round Robin
   C) Shortest Job Next
   D) None of these

15. **A common representation of process scheduling is -** *[BPSC Assistant Maintenance Engineer 2019 compact it 192 (ET: N/A)]*
   (a) Static diagram
   (b) Scheduling queues
   (c) Queuing diagram
   (d) Process control block

16. **The scheduling queue is generally stored as-** *[BPSC Assistant Maintenance Engineer 2019 compact it 193 (ET: N/A)]*
   (a) A liner array
   (b) A stack
   (c) A linked list
   (d) A tree

17. **To execute a program, an OS creates a number of ________, each one for, running a different program.** *[BPSC Assistant Maintenance Engineer 2019 compact it 194 (ET: N/A)]*
   (a) Processors
   (b) Threads
   (c) Virtual processors
   (d) Kernel

18. **What is long term scheduling?** *[Combined 3 Bank Assistant Programmer 2018 compact it 230 (ET: N/A)]*
   A) It selects which process has to be brought into the ready queue
   B) It selects which process has to be executed next and allocates CPU
   C) It selects which process to remove from memory by swapping
   D) It selects which process needs to be killed next

19. **Multi-Threaded programs are-** *[Combined 3 Bank Assistant Programmer 2018 compact it 230 (ET: N/A)]*
   A) Lesser prone to deadlocks
   B) more prone to deadlocks
   C) not at all prone to deadlock
   D) always results in deadlocks

20. **When there is a large logical address space, the best way of paging would be ________.** *[Combined 3 Bank Assistant Programmer 2018 compact it 231 (ET: N/A)]*
   A) Not to page
   B) a two-level paging algorithm
   C) not all prone to deadlock
   D) all of the above

21. **What is the mounting of file system?** *[Combined 3 Bank Assistant Programmer 2018 compact it 231 (ET: N/A)]*
   A) creating of a file system
   B) deleting a file system
   C) attaching portion of the file system into a directory structure
   D) removing portion of the file system into a directory structure

22. **The main program in an operating system is called:** *[Combined 3 Bank Assistant Programmer 2018 compact it 232 (ET: N/A)]*
   A) kernel
   B) file manager
   C) Directory
   D) NOS

23. **The interval from the time of submission of a process to the time of completion is termed is ________.** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 259 (ET: N/A)]*
   A) Waiting time
   B) processing time
   C) turnaround time
   D) throughput

24. **Which of the following is not the state of a process in process Control Block (PCB)?** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 260 (ET: N/A)]*
   A) Old
   B) New
   C) waiting
   D) Running

## OS Concepts & Multiprogramming (16)

1. **The ______ system may manage a high degree of interaction between processes and is very useful for high speed and real-time processing.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 25 (ET: BIBM)]*
   (a) strongly coupled and loosely cohesive
   (b) loosely coupled and strongly cohesive
   (c) loosely coupled and loosely cohesive
   (d) strongly coupled and strongly cohesive

2. **Which one is an embedded operating system?** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 52 (ET: N/A)]*
   (ক) UNIX
   (খ) MS windows XP
   (গ) Windows CE
   (ঘ) Windows NET

3. **Which initial program is called at the starting of a computer?** *[Rupali Bank Ltd. Assistant Network Engineer (ANE) 2021 compact it 81 (ET: N/A)]*
   a. Computer Startup Loader
   b. Operating System Details
   c. Bootstrap Loader
   d. Hardware System Details

4. **What is the mean of the Booting in the system?** *[BREB Assistant General Manager (O&M/E&C) 2021 compact it 137 (ET: N/A)]*
   a. Restarting computer
   b. Install the program
   c. To scan
   d. To turn off

5. **What is LINUX?** *[BREB Assistant Enforcement Coordinator 2021 compact it 140 (ET: N/A)]*
   ক. Operating System
   খ. Application Program
   গ. Antivirus software
   ঘ. Firewall

6. **Where is the Boot strapping program stored?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 160 (ET: N/A)]*
   A) ROM
   B) Hard disk
   C) CD
   D) RAM

7. **Which one of the first 64-bit operating system?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 161 (ET: N/A)]*
   A) Windows Vista
   B) Mac
   C) Linux
   D) Windows XP

8. **In a computer, folder opening is denied by which of the following names?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 161 (ET: N/A)]*
   A) con
   B) com
   C) mak
   D) make

9. **Which of the following contains configuration information of a window?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 163 (ET: N/A)]*
   A) .exe
   B) .ini
   C) .dill
   D) .chm

10. **Who preside the interface between a process and the OS?** *[BPSC Assistant Maintenance Engineer 2019 compact it 193 (ET: N/A)]*
   (a) Kernel
   (b) System calls
   (c) Command
   (d) Graphical user

11. **Which O/S is recommended for real time system?** *[Combined Bank Maintenance Engineer 2018 compact it 227 (ET: N/A)]*
   A) Windows
   B) Unix
   C) Oracle
   D) None of this

12. **Which OS is recommended for real time systems?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 247 (ET: N/A)]*
   A) Windows
   B) Unix
   C) Oracle
   D) None of them

13. **Which one loads first when you boot up your Computer?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 247 (ET: N/A)]*
   A) BIOS
   B) Operating System
   C) Keyboard driver
   D) None of them

14. **Generally what type of server OS is chosen, where security concern is a great issue?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 248 (ET: N/A)]*
   A) Windows XP
   B) Windows Server 2000
   C) DOS V
   D) UNIX

15. **The command password issued without an argument with change the password of –** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 248 (ET: N/A)]*
   A) Root user
   B) Current user
   C) User with lowest user id
   D) User with lowest group id

16. **Multiprogramming systems ________** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 270 (ET: N/A)]*
   a. Are easier to develop than single programming system
   b. Execute each job faster
   c. Execute more jobs in the same time
   d. Are used only on large mainframe computers.

## Virtual Memory & Paging (13)

1. **Which of the following page replacement algorithms suffers from Belady’s anomaly?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 8 (ET: BIBM)]*
   a) FIFO
   b) LRU
   c) Optimal Page Replacement
   d) Both LRU and FIFO

2. **To keep track of how many frames have been allocated, how many are there, and how many are available, operating system maintain a—** *[Combined Bank Officer (IT) 04.10.2024 compact it 12 (ET: BIBM)]*
   (a) Memory table
   (b) Page table
   (c) mapping table
   (d) frame table

3. **Logical Memory is broken into blocks of the same size called-** *[NPCBL Executive Trainee (Software) 2023 compact it 38 (ET: N/A)]*
   a) Frames
   b) Pages
   c) raids
   d) Blocks

4. **A CPU generates 32-bit virtual addresses. The page size is 4 KB. The processor has a translation look-aside buffer (TLB) which can hold a total of 128 page table entries and is 4-way set associative. The minimum size of the TLB tag is:** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 24 (ET: BIBM)]*
   (a) 11 bits
   (b) 13 bits
   (c) 15 bits
   (d) 20 bits

5. **What is the relationship between Paging and Virtual memory?** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 45 (ET: N/A)]*
   (ক) Virtual memory came before Paging
   (খ) When pages are created in disks, it is called a virtual memory
   (গ) Virtual memory can never be implemented without paging
   (ঘ) Both have the same concepts

6. **Consider a virtual memory system with FIFO page replacement policy. For an arbitrary page access pattern, increasing the number of page frames in main memory will–** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*
   a) Always decrease the number of page faults
   b) Always increase the number of page faults
   c) Sometimes increase the number of page faults
   d) Never affect the number of page faults

7. **Applying the LRU page replacement to the reference string 1 2 4 5 2 1 2 4. The main memory can accommodate pages and it already has pages and 2. Pape I came in before page 2 How many page faults will court?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 128 (ET: N/A)]*
   a) 3
   b) 4
   c) 5
   d) 6

8. **Consider a virtual memory system where three pages are allocated for real memory. If the page replacement algorithm used is FIFO, how many page replacements take place for the access sequence: 1, 3, 2, 1, 4, 5, 2, 3, 4, 5?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 90 (ET: N/A)]*
   a. 2
   b. 3
   c. 4
   d. 6

9. **Virtual memory located on:** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 171 (ET: N/A)]*
   a) RAM
   b) CPU
   c) Flash drive
   d) Hard drive

10. **Virtually memory হিসেবে RAM এর পাশাপাশি কোনটি ব্যবহার হয়?** *[BPSC Assistant Network Engineer 2019 compact it 196 (ET: N/A)]*
   A) Cache
   B) CPU Register
   C) CD-ROM
   D) Hard disk

11. **Memory management scheme by which a computer stores and retrieves data from secondary storage for use in main memory is-** *[Combined Bank Senior Officer (IT) 2018 compact it 223 (ET: DU)]*
   A) Paging
   B) Scheduling
   C) Batch processing
   D) Virtual storage

12. **Swap space exists in ---** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 260 (ET: N/A)]*
   A) CPU
   B) random memory
   C) primary memory
   D) secondary memory

13. **A page fault occurs ________** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 270 (ET: N/A)]*
   a. When the page is not in the memory
   b. When the page is in the memory
   c. When the process inters into the blocked state
   d. When the process is in the ready state

## Linux Commands & Administration (9)

1. **User passwords in Linux are stored as-** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 100 (ET: N/A)]*
   (a) Direct text data
   (b) Encrypted using some sort of hashing function
   (c) Encrypted using mono-alphabetic cipher
   (d) Encrypted using homophonic substitution cipher

2. **Which of the following Linux command has incorrect syntax?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 106 (ET: N/A)]*
   (a) cat sample.txt | grep -v a | sort - r
   (b) chown:group3 File 1
   (c) chmoda+rx viewer.sh
   (d) None of the above

3. **What is the maximum size of a file allowed in Linux with the following data Block Size = 4KB, inode data pointer size = 4 byte?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 106 (ET: N/A)]*
   (a) 1 TB
   (b) Less than 4TB
   (c) 2TB+2GB+2MB+64KB
   (d) More than 4 TB

4. **Which UNIX/Linux command is used to make all files and sub-directories in the directory "progs" executable by all users?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 107 (ET: N/A)]*
   (a) chmod -R a+x progs
   (b) chmod -R 222 progs
   (c) chmod -X a+x progs
   (d) chmod -X 222 progs

5. **USER150, USER153 can do certain tasks and USER151, USER152 can also do certain tasks as depicted in the picture. For this reason, two ________ have been created.** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 179 (ET: N/A)]*
   ```
   CREATE                    SELECT                   INSERT
   TABLE                   ON Orders                 ON Orders
   |                         |                         |
   +------------+------------+------------+------------+
   |                         |
   Account MGR              Inventory MGR
   |                         |
   +---------+---------+     +---------+---------+
   |                   |     |                   |
   USER150             USER151 USER152             USER153
   ```
   a) Roles
   b) Privileges
   c) Functions
   d) Stord Procedures

6. **In UNIX, the login prompt can be changed by changing the content of the file-** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 205 (ET: AUST)]*
   A) gettydefs
   B) contrab
   C) inittab
   D) init

7. **Which of the following UNIX commands allows scheduling a program to be executed at specifies time?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 205 (ET: AUST)]*
   A) nice
   B) cron
   C) date and time
   D) schedule

8. **What command is used to remove files UNIX?** *[BREB Assistant Junior Engineer (IT) 2019 compact it 218 (ET: N/A)]*
   A) dm
   B) rm
   C) delete
   D) erase

9. **You need to determine whether IP information has been assigned to your Windows NT. Which utility should you use?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 250 (ET: N/A)]*
   A) NBTSTAT
   B) NETSTAT
   C) IPCONFIG
   D) WINTPCFG

## Deadlock (6)

1. **A system has 6 identical resources and N processes competing for them. Each process can request at most 2 resources. Which one of the following values of N could lead to a deadlock?** *[Combined Bank Officer (IT) 04.10.2024 compact it 12 (ET: BIBM)]*
   (a) 1
   (b) 2
   (c) 3
   (d) 4

2. **Which one of the following is the deadlock avoidance algorithm?** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*
   a) banker’s algorithm
   b) round-robin algorithm
   c) Elevator algorithm
   d) karn’s algorithm

3. **Which of the following is not a deadlock handling strategy?** *[NPCBL Executive Trainee (Software) 2023 compact it 41 (ET: N/A)]*
   a) Deadlock prevention
   b) Timeout
   c) Deadlock detection and recovery
   d) Deadlock annihilation

4. **A system has 12 magnetic tape drives and 3 processes: PO, PI, and P2. Process PO requires 10 tape drives, P1 requires 4 and P2 requires 9 tape drives. The current allocation tape drives of processes P0, PI and P2 is 5, 2, 2, respectively. Which of the following sequence is a safe sequence?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 126 (ET: N/A)]*
   a) P0, PI, P2
   b) P1, P2, P0
   c) P2, P0, P1
   d) P1, P0, P2

5. **A computer system has 6 type drives and each process may need 3 type drives. What is the maximum number of processes than is guaranteed to be deadlock free?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 164 (ET: N/A)]*
   a) 4
   b) 3
   c) 2
   d) None
   5. Consider the following table named “Course”-
   | Course Title | Content |
   |---|---|
   | Web Programming | Python, CSS, JS |
   What is the main problem/anomalies in the Course table? *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 164 (ET: N/A)]*
   a) Attribute name is not correct
   b) Table is larger
   c) Attribute has multiple value
   d) It has functional dependency

6. **The request and release of resources are-** *[BPSC Assistant Maintenance Engineer 2019 compact it 194 (ET: N/A)]*
   (a) Command line
   (b) Interrupts statements
   (c) System calls
   (d) Special program

## File Systems & Disk Management (4)

1. **A system has two IDE hard drives that are each divided into primary and extended partitions, which drive letter is assigned to the primary partition of the second drive?** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 42 (ET: N/A)]*
   (a) C
   (b) D
   (c) E
   (d) F

2. **Which of the following is not a true statement?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 131 (ET: N/A)]*
   a) Deleted files can be found in recycle bin
   b) Deleted files in recycle bin can be restored
   c) Disk space can be increased by sending files into recycle bin
   d) There may have multiple recycle bin

3. **Which of the following file name extension suggests that the file is backup of another file?** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 270 (ET: N/A)]*
   a. TXT
   b. COM
   c. BAS
   d. BAK

4. **"INI" extension refers usually what kind of file?** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 270 (ET: N/A)]*
   a. Image file
   b. System file
   c. Hypertext file
   d. Image Color Matching Profile file

## Process Synchronization (2)

1. **A counting semaphore was initialized to 10. Then 6 wait operations and 4 signal operations were completed on this semaphore. The resulting value of the semaphore is___** *[Combined Bank Officer (IT) 04.10.2024 compact it 13 (ET: BIBM)]*
   (a) 0
   (b) 10
   (c) 8
   (d) 12

2. **A critical section is a program segment-** *[Combined Bank Officer (IT) 04.10.2024 compact it 13 (ET: BIBM)]*
   (a) which should run in a certain specified amount of time
   (b) which avoids deadlocks
   (c) where shared resources are accessed
   (d) which must be enclosed by a pair of semaphore (wait and signal) operations
