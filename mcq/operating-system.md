## Virtual Memory & Paging

1. **Which of the following page replacement algorithms suffers from Belady’s anomaly?** **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM)) [compact it 8]**
   a) FIFO
   b) LRU
   c) Optimal Page Replacement
   d) Both LRU and FIFO

2. **To keep track of how many frames have been allocated, how many are there, and how many are available, operating system maintain a—** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 12]**
   (a) Memory table
   (b) Page table
   (c) mapping table
   (d) frame table

3. **Logical Memory is broken into blocks of the same size called-** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 38]**
   a) Frames
   b) Pages
   c) raids
   d) Blocks

4. **A CPU generates 32-bit virtual addresses. The page size is 4 KB. The processor has a translation look-aside buffer (TLB) which can hold a total of 128 page table entries and is 4-way set associative. The minimum size of the TLB tag is:** **(Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)) [compact it 24]**
   (a) 11 bits
   (b) 13 bits
   (c) 15 bits
   (d) 20 bits

5. **What is the relationship between Paging and Virtual memory?** **(BPSC (Ministry) Assistant Maintenance Engineer Exam: 2022) [compact it 45]**
   (ক) Virtual memory came before Paging
   (খ) When pages are created in disks, it is called a virtual memory
   (গ) Virtual memory can never be implemented without paging
   (ঘ) Both have the same concepts

6. **Consider a virtual memory system with FIFO page replacement policy. For an arbitrary page access pattern, increasing the number of page frames in main memory will–** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 127]**
   a) Always decrease the number of page faults
   b) Always increase the number of page faults
   c) Sometimes increase the number of page faults
   d) Never affect the number of page faults

7. **Applying the LRU page replacement to the reference string 1 2 4 5 2 1 2 4. The main memory can accommodate pages and it already has pages and 2. Pape I came in before page 2 How many page faults will court?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 128]**
   a) 3
   b) 4
   c) 5
   d) 6

8. **Consider a virtual memory system where three pages are allocated for real memory. If the page replacement algorithm used is FIFO, how many page replacements take place for the access sequence: 1, 3, 2, 1, 4, 5, 2, 3, 4, 5?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 90]**
   a. 2
   b. 3
   c. 4
   d. 6

9. **Virtual memory located on:** **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 171]**
   a) RAM
   b) CPU
   c) Flash drive
   d) Hard drive

10. **Virtually memory হিসেবে RAM এর পাশাপাশি কোনটি ব্যবহার হয়?** **(BPSC Assistant Network Engineer Exam: 2019) [compact it 196]**
   A) Cache
   B) CPU Register
   C) CD-ROM
   D) Hard disk

11. **Memory management scheme by which a computer stores and retrieves data from secondary storage for use in main memory is-** **(Combined Bank Senior Officer (IT) Exam: 2018 Exam Taker: DU) [compact it 223]**
   A) Paging
   B) Scheduling
   C) Batch processing
   D) Virtual storage

## Deadlock

1. **A system has 6 identical resources and N processes competing for them. Each process can request at most 2 resources. Which one of the following values of N could lead to a deadlock?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 12]**
   (a) 1
   (b) 2
   (c) 3
   (d) 4

2. **Which one of the following is the deadlock avoidance algorithm?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) banker’s algorithm
   b) round-robin algorithm
   c) Elevator algorithm
   d) karn’s algorithm

3. **Which of the following is not a deadlock handling strategy?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 41]**
   a) Deadlock prevention
   b) Timeout
   c) Deadlock detection and recovery
   d) Deadlock annihilation

4. **A system has 12 magnetic tape drives and 3 processes: PO, PI, and P2. Process PO requires 10 tape drives, P1 requires 4 and P2 requires 9 tape drives. The current allocation tape drives of processes P0, PI and P2 is 5, 2, 2, respectively. Which of the following sequence is a safe sequence?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 126]**
   a) P0, PI, P2
   b) P1, P2, P0
   c) P2, P0, P1
   d) P1, P0, P2

5. **A computer system has 6 type drives and each process may need 3 type drives. What is the maximum number of processes than is guaranteed to be deadlock free?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 164]**
   a) 4
   b) 3
   c) 2
   d) None
   5. Consider the following table named “Course”-
   | Course Title | Content |
   |---|---|
   | Web Programming | Python, CSS, JS |
   What is the main problem/anomalies in the Course table? **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 164]**
   a) Attribute name is not correct
   b) Table is larger
   c) Attribute has multiple value
   d) It has functional dependency

6. **The request and release of resources are-** **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 194]**
   (a) Command line
   (b) Interrupts statements
   (c) System calls
   (d) Special program

## Process Synchronization

1. **A counting semaphore was initialized to 10. Then 6 wait operations and 4 signal operations were completed on this semaphore. The resulting value of the semaphore is___** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 13]**
   (a) 0
   (b) 10
   (c) 8
   (d) 12

2. **A critical section is a program segment-** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 13]**
   (a) which should run in a certain specified amount of time
   (b) which avoids deadlocks
   (c) where shared resources are accessed
   (d) which must be enclosed by a pair of semaphore (wait and signal) operations

## Process Management & Scheduling

1. **A process needs I/O operations, it switches to _____** **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xix]**
   (a) Ready
   (b) Running
   (c) Waiting (Blocked)
   (d) Terminated

2. **Which of the following scheduling algorithm is non preemptive?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 37]**
   (a) Shortest Job First
   (b) FCFS
   (c) Rounf Robin
   (d) Priority Scheduling

3. **Time during which a job is processed by the Computer is:** **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 56]**
   (ক) Delay time
   (খ) Real time
   (গ) Execution time
   (ঘ) Process time

4. **In Unix operating system, which system call is used for creating a new process?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 126]**
   a) Exec()
   b) Create Process ()
   c) Fork ()
   d) None of them

5. **A job which is schedule to run periodically at fixed times or intervals is known as-** **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 99]**
   (a) Batch Job
   (b) Cron job
   (c) Shell Script
   (d) None of the above

6. **Which one of the following statements is true with respect to Printer Daemon process?** **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 103]**
   (a) The printer daemon of Operating System runs in kernel mode.
   (b) Jobs in the printer daemon queue cannot be removed once inserted.
   (c) Printer daemon application runs only when it is printing.
   (d) Printer daemon runs as a service in Operating System

7. **Which of the following Process scheduling algorithm is highly improbable to be implemented?** **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 107]**
   (a) FCFS Scheduling
   (b) Priority Scheduling
   (c) Shortest Job First Scheduling
   (d) None of the above

8. **A jet Aircraft employs a system for monitoring the rpm, pressure and temperature values of its engines using sensors that operate as follows:** **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 179]**
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

9. **What is the disadvantage of multithreading?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
   a) Share the same address space
   b) Simultaneous access to multiple application
   c) Low cost communication
   d) Difficulty in managing concurrency

10. **The time needs from the process arrival to the completion of that process is called** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
   a) Waiting time
   b) Response time
   c) Turnaround time
   d) Throughput

11. **Which is not the state of a process in an Operating System?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 166]**
   a) New
   b) Sleep
   c) Terminated
   d) Ready

12. **The maximum number of processes that can be in ready state in computer system with n CPU's is—** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 204]**
   A) n
   B) \text{n}^2
   C) 2n
   D) independent of n

13. **In UNIX, processes that have finished execution but have not yet had their status collected are known as-** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 205]**
   A) Sleeping processes
   B) Stopped processes
   C) Zombie processes
   D) Orphan processes

14. **Which of the following process scheduling algorithm may lead to starvation?** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 206]**
   A) FIFO
   B) Round Robin
   C) Shortest Job Next
   D) None of these

15. **A common representation of process scheduling is -** **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 192]**
   (a) Static diagram
   (b) Scheduling queues
   (c) Queuing diagram
   (d) Process control block

16. **The scheduling queue is generally stored as-** **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 193]**
   (a) A liner array
   (b) A stack
   (c) A linked list
   (d) A tree

17. **To execute a program, an OS creates a number of ________, each one for, running a different program.** **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 194]**
   (a) Processors
   (b) Threads
   (c) Virtual processors
   (d) Kernel

18. **What is long term scheduling?** **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 230]**
   A) It selects which process has to be brought into the ready queue
   B) It selects which process has to be executed next and allocates CPU
   C) It selects which process to remove from memory by swapping
   D) It selects which process needs to be killed next

19. **Multi-Threaded programs are-** **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 230]**
   A) Lesser prone to deadlocks
   B) more prone to deadlocks
   C) not at all prone to deadlock
   D) always results in deadlocks

20. **When there is a large logical address space, the best way of paging would be ________.** **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 231]**
   A) Not to page
   B) a two-level paging algorithm
   C) not all prone to deadlock
   D) all of the above

21. **What is the mounting of file system?** **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 231]**
   A) creating of a file system
   B) deleting a file system
   C) attaching portion of the file system into a directory structure
   D) removing portion of the file system into a directory structure

22. **The main program in an operating system is called:** **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 232]**
   A) kernel
   B) file manager
   C) Directory
   D) NOS

## File Systems & Disk Management

1. **A system has two IDE hard drives that are each divided into primary and extended partitions, which drive letter is assigned to the primary partition of the second drive?** **(Pubali Bank Limited, Hardware Engineer Exam: 18.03.2023) [compact it 42]**
   (a) C
   (b) D
   (c) E
   (d) F

2. **Which of the following is not a true statement?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 131]**
   a) Deleted files can be found in recycle bin
   b) Deleted files in recycle bin can be restored
   c) Disk space can be increased by sending files into recycle bin
   d) There may have multiple recycle bin

## OS Concepts & Multiprogramming

1. **The ______ system may manage a high degree of interaction between processes and is very useful for high speed and real-time processing.** **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 25]**
   (a) strongly coupled and loosely cohesive
   (b) loosely coupled and strongly cohesive
   (c) loosely coupled and loosely cohesive
   (d) strongly coupled and strongly cohesive

2. **Which one is an embedded operating system?** **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 52]**
   (ক) UNIX
   (খ) MS windows XP
   (গ) Windows CE
   (ঘ) Windows NET

3. **Which initial program is called at the starting of a computer?** **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 81]**
   a. Computer Startup Loader
   b. Operating System Details
   c. Bootstrap Loader
   d. Hardware System Details

4. **What is the mean of the Booting in the system?** **(BREB Assistant General Manager (O&M/E&C) Exam: 2021) [compact it 137]**
   a. Restarting computer
   b. Install the program
   c. To scan
   d. To turn off

5. **What is LINUX?** **(BREB Assistant Enforcement Coordinator Exam: 2021) [compact it 140]**
   ক. Operating System
   খ. Application Program
   গ. Antivirus software
   ঘ. Firewall

6. **Where is the Boot strapping program stored?** **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 160]**
   A) ROM
   B) Hard disk
   C) CD
   D) RAM

7. **Which one of the first 64-bit operating system?** **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 161]**
   A) Windows Vista
   B) Mac
   C) Linux
   D) Windows XP

8. **In a computer, folder opening is denied by which of the following names?** **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 161]**
   A) con
   B) com
   C) mak
   D) make

9. **Which of the following contains configuration information of a window?** **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 163]**
   A) .exe
   B) .ini
   C) .dill
   D) .chm

10. **Who preside the interface between a process and the OS?** **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 193]**
   (a) Kernel
   (b) System calls
   (c) Command
   (d) Graphical user

11. **Which O/S is recommended for real time system?** **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 227]**
   A) Windows
   B) Unix
   C) Oracle
   D) None of this

12. **Which OS is recommended for real time systems?** **(Sonali Bank Limited Assistant Engineer (IT) Preliminary Exam: 2016) [compact it 247]**
   A) Windows
   B) Unix
   C) Oracle
   D) None of them

13. **Which one loads first when you boot up your Computer?** **(Sonali Bank Limited Assistant Engineer (IT) Preliminary Exam: 2016) [compact it 247]**
   A) BIOS
   B) Operating System
   C) Keyboard driver
   D) None of them

14. **Generally what type of server OS is chosen, where security concern is a great issue?** **(Sonali Bank Limited Assistant Engineer (IT) Preliminary Exam: 2016) [compact it 248]**
   A) Windows XP
   B) Windows Server 2000
   C) DOS V
   D) UNIX

15. **The command password issued without an argument with change the password of –** **(Sonali Bank Limited Assistant Engineer (IT) Preliminary Exam: 2016) [compact it 248]**
   A) Root user
   B) Current user
   C) User with lowest user id
   D) User with lowest group id

## Linux Commands & Administration

1. **User passwords in Linux are stored as-** **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 100]**
   (a) Direct text data
   (b) Encrypted using some sort of hashing function
   (c) Encrypted using mono-alphabetic cipher
   (d) Encrypted using homophonic substitution cipher

2. **Which of the following Linux command has incorrect syntax?** **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 106]**
   (a) cat sample.txt | grep -v a | sort - r
   (b) chown:group3 File 1
   (c) chmoda+rx viewer.sh
   (d) None of the above

3. **What is the maximum size of a file allowed in Linux with the following data Block Size = 4KB, inode data pointer size = 4 byte?** **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 106]**
   (a) 1 TB
   (b) Less than 4TB
   (c) 2TB+2GB+2MB+64KB
   (d) More than 4 TB

4. **Which UNIX/Linux command is used to make all files and sub-directories in the directory "progs" executable by all users?** **(Sonali Bank and BDBL Senior Officer (IT) Exam: 25.09.2021) [compact it 107]**
   (a) chmod -R a+x progs
   (b) chmod -R 222 progs
   (c) chmod -X a+x progs
   (d) chmod -X 222 progs

5. **USER150, USER153 can do certain tasks and USER151, USER152 can also do certain tasks as depicted in the picture. For this reason, two ________ have been created.** **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 179]**
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

6. **In UNIX, the login prompt can be changed by changing the content of the file-** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 205]**
   A) gettydefs
   B) contrab
   C) inittab
   D) init

7. **Which of the following UNIX commands allows scheduling a program to be executed at specifies time?** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 205]**
   A) nice
   B) cron
   C) date and time
   D) schedule

8. **What command is used to remove files UNIX?** **(BREB Assistant Junior Engineer (IT) Exam: 2019) [compact it 218]**
   A) dm
   B) rm
   C) delete
   D) erase

9. **You need to determine whether IP information has been assigned to your Windows NT. Which utility should you use?** **(Sonali Bank Limited Assistant Engineer (IT) Preliminary Exam: 2016) [compact it 250]**
   A) NBTSTAT
   B) NETSTAT
   C) IPCONFIG
   D) WINTPCFG
