## OS Concepts & System Software

1. Difference Between Firmware and OS. (BEPRC Assistant Programmer Exam: 08.08.2026)

2. **Define: Socket, Kernel, Process, Program, Multiprogramming, Context Switching; Explain Preemptive Priority Scheduling algorithm with illustration; Explain LRU and NRU Page Replacement algorithm.** **(Combined Bank - Assistant Maintenance Engineer/ Assistant Engineer (IT) Exam: 24.02.2024 (BIBM)) [compact it 302]**

3. **Explain how can multiprogramming be achieved on a uniprocessor system?** **(BGDCL - Assistant Manager (CSE) Exam: 15.03.2024 (BUET)) [compact it 379]**

4. **Write the difference between shell and kernel?** **(Bangladesh Oil Gas Mineral Corporation (PetroBangla) - Assistant Manager (CSE/IT) Exam: 31.06.2024 (BUET)) [compact it 1454]**

5. **DOS কী? অপারেটিং সিস্টেমের কাজ ও প্রকারভেদ ব্যাখ্যা করুন।** **(18th NTRCA - Assistant Teacher (ICT) Exam: 12.07.2024) [compact it 407]**

6. **Write down the difference between Multitasking and Multiprocessing.** **(DESCO Sub-Assistant Engineer Exam: 20.05.2023 (DESCO)) [compact it 581]**

7. **(b) What is the difference between micro kernel and macro kernel in the context of OS?** **(BPSC (Multiple Ministry) Assistant Programmer (ICT) Exam: 19.07.2023) [compact it 490]**

8. **অথবা, (ক) Blocking এবং Buffering OS এর পার্থক্য লিখুন।** **(17th NTRCA Lecturer (ICT) Written Exam (CSE): 2023) [compact it 610]**

9. **(গ) Real Time System বলতে কী বোঝায় ব্যাখ্যা করুন।** **(17th NTRCA Lecturer (ICT) Written Exam (ICT): 2023) [compact it 625]**

10. **Explain context switching in Operating System.** **(MGMCL Assistant Manager (ICT) Exam: 20.05.2022 (BUET)) [compact it 649]**

11. **Which Operating system is considered as an Open source?** **(BARI Assistant Maintenance Engineer Exam: 26.08.2022) [compact it 702]**

12. **What is kernel? Write down the objectives of kernel.** **(SPCB Sub-Assistant Programmer Exam: 2022) [compact it 740]**

13. **IBM প্রতিষ্ঠান কর্তৃক কোন Operating System প্রস্তুত করা হয়?** **(BPSC Computer Operator Exam: 2021) [compact it 781]**

## Concurrency, Threads & Synchronization

1. Multi-threaded processing and distributed computing have become essential. (Combined Bank Officer (IT) Exam: 03.01.2026) [debug it]

2. **What is Multithreading programming? Why Multithreading used in programming?** **(Combined Bank - Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 296]**

3. **What is Multithreading System?** **(BARI - Assistant Maintenance Engineer Exam: 10.05.2024) [compact it 1460]**

4. **What is the output of the following code?** **(BAERA Assistant Engineer (CSE) Exam: 2023 (BUET)) [compact it 574]**
```c
#include <stdlib.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
int main(int argc, char *argv[]){
    int i;
    for(i=0;i<4;i++){
        int pid = fork();
        if(pid==0){
            printf("%d\n",i);
            exit(0);
        }
    }
    for(i=0;i<4;i++){
        wait(NULL);
    }
    return 0;
}
```

5. **অথবা, (ক) Thread এর সংজ্ঞা দিন।** **(17th NTRCA Lecturer (ICT) Written Exam (ICT): 2023) [compact it 619]**

6. **Write down the thread life cycle.** **(BDCCL Assistant Manager (Cyber Security) Exam: 14.10.2022) [compact it 755]**

7. **What is Multi-threading and multi-tasking? Difference between Multi-threading and Multi-tasking?** **(RAKUB Maintenance Engineer (PO) Exam: 05.10.2021) [compact it 854]**

## Linux / Unix Commands & Administration

1. **Write Linux command:** **(Islami Bank PLC Senior Officer (Network/System) Exam: 14.03.2025 (BUET)) [compact it 1331]**
   (a) Give a file Read Write and Execute permission.
   (b) IP address show.
   (c) Delete all files in a folder.
   (d) Show partition.

2. **Write a Linux command to count the total number of characters and words from the first 10 lines of a file named "wasacustomers.txt".** **(Dhaka WASA - Assistant Maintenance Engineer (Network) Exam: 04.07.2025 (BUET)) [compact it 1437]**

3. **Linux command:** **(DESCO Sub-Assistant Engineer Exam: 20.06.2025 (BUET)) [compact it 1361]** **(GTCL Assistant Engineer (CSE) Exam: 2022 (BUET)) [compact it 685]**

4. **Write Linux command:** **(BCIC Assistant Programmer Exam: 14.02.2025 (BUET)) [compact it 1324]**
   * **(a) Displays real-time system statistics, including CPU usage, memory usage, running processes, and system load.**
   * **(b) Searches for a specified pattern in a file or output.**
   * **(c) Shows disk usage for all mounted file systems.**
   * **(d) Displays information about system memory (RAM and swap).** **(BCIC Assistant Programmer Exam: 14.02.2025 (BUET)) [compact it 1325]**

5. **ফাইল Rename করার Linux কমান্ড কি?** **(BARI - Assistant Maintenance Engineer Exam: 15.11.2025) [compact it 1451]**

6. **Which file is need by init to get the default run level?** **(BARI - Assistant Maintenance Engineer Exam: 15.11.2025) [compact it 1452]**

7. **Show last 10 lines of log file which is continuously updating in Linux command?** **(Titas Gas - Assistant Engineer (CSE) Exam: 24.05.2024 (BUET)) [compact it 417]**

8. **Linux Command in ownership and group permission.** **(Pubali Bank Limited Hardware Engineer Exam: 18.03.2023) [compact it 567]**

9. **UNIX command with example: File move, Change Directory and search from a specific line.** **(NPCBL Executive Trainee (Software) Exam: 26.05.2023 (IBA)) [compact it 500]**

10. **Write appropriate linux command:**
| Questions |
|---|
| Show hidden files and directories |
| Delete a directory and its file |
| Prints last five lines of a text file |
| Download a file from an URL |
**(Milk Vita Assistant Manager (CSE/MIS) Exam: 2023) [compact it 474]**

11. **Write Linux command to find out the following question:** **(BTCL Assistant Manager (Technical) Exam: 2023 (BUET)) [compact it 592]**
   (a) To show current file directory.
   (b) To show 11^{\text{th}} to 15^{\text{th}} line from file name myfile.
   (c) To show permission for read, write and execution file name myfile.

12. **Write down the names of the three users who can access a file on directory on Linux.** **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 447]**

13. **You need to find the total number of linux of the .c and .h file in the current directory formulas the linux commands to display this......... (Approximate)** **(BPDB Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 448]**

14. **Find the possible path to know how data on the internet treavels from your mechine to the site www.bicic.gov.bd. Write down the necessary command to accomplish this.** **(BICIC Assistant Programmer Exam: 2022 (BUET)) [compact it 633]**

15. **You want to run some specific commands at some price schedules time. Which command will have to be used for this.** **(BICIC Assistant Programmer Exam: 2022 (BUET)) [compact it 633]**

16. **Linux Command লিখ:** **(BTCL Junior Assistant Manager Exam: 2022 (BUET)) [compact it 640]**
   a) একটি ফোল্ডারের সকল ফাইল দেখানোর কমান্ড।
   b) নতুন ডিরেক্টরি তৈরির কমান্ড।
   c) ফাইল এ্যাকসেস পারমিশন দেখানোর কমান্ড।

17. **Write down the linux command: All hidden flies, remove a file, permission of a file, search for a string.** **(MGMCL Assistant Manager (ICT) Exam: 20.05.2022 (BUET)) [compact it 651]**

18. **UNIX command (directory listing with hidden files).** **(Sonali & Janata Bank Ltd. Assistant Database Administrator Exam: 2022) [compact it 662]**

19. **Difference between below 3 linux command: cd, cd usr/desk/home, cd/user/desk/home** **(EGCB Assistant Engineer (CSE) Exam: 2022 (BUET)) [compact it 717]**

20. **Linux Command: Write down the linux command: All hidden flies, remove a file, permission of a file, search for a string.** **(Water Supply and Sewerage Authority (WASA); Assistant Programmer Exam: 25.11.2022) [compact it 763]**

21. **(b) Write Linux commands to: (i) Make a directory named PSC (ii) Copy a directory with all its Contents into a directory name/home/admin.** **(BPSC Sub-Assistant Engineer (Ministry of Agriculture) Exam: 2021) [compact it 799]**

22. **In Linux, History is a very useful command to show you all of the last commands that have been recently used. Grep is a Linux command-line tool used to search for a string of characters in a specified file. Write grep and history command to find previous commands in Linux.** **(BCC Assistant Programmer Exam: 12.02.2021 (BUET)) [compact it 813]**

23. **Write down a shell script program that would add the line “This is my file” at the top of each file having the extention ‘txt’ in the current directory. Note that all the other contents of the .txt file(s) would remain unchanged and start from the second line.** **(BPDB Assistant Engineer (CSE) Exam: 2021 (BUET)) [compact it 818]**

24. **Write the following UNIX command with example: (a) ls (b) grep (c) ssh** **(BITAC Assistant Maintenance Engineer (ICT) Exam: 2021 (BUET)) [compact it 820]**

25. **(a) Check if the website of ‘TGTDCL’. (b) How to create folder in sub-directory?** **(Titas Gas Assistant Engineer (CSE) Exam: 2021 (BUET)) [compact it 823]**

26. **Write a Linux command to revoke permission from no user but owner from a file “jdcl.txt”.** **(JGTDSL Assistant Engineer (CSE) Exam: 08.10.2021) [compact it 859]**

## Windows & System Administration

1. **How to check the IP address in the Windows Command Prompt?** **(BARI - Assistant Maintenance Engineer Exam: 15.11.2025) [compact it 1451]**

2. **Assume that an office has three departments and each department has 50 to 70 employees who are using computers with Windows operating systems. The office space is designed in such a way that an employee can use any computer within a department. Once an employee logs in from a computer, he/she will get access to his files from the server. Let you are planning for network and server setup for this company.**
   * **(a) What is Active Directory? Do you need an Active Directory for such an office? If yes, briefly explain its use under this circumstance.** **(Combined Bank - Senior Officer (IT) Exam: 17.05.2024 (BIBM)) [compact it 323]**

3. **Describe the booting process in windows system.** **(Pubali Bank Limited Hardware Engineer Exam: 18.03.2023) [compact it 565]**

## CPU Scheduling

1. A system has three processes with the following arrival times and CPU burst times:

| Process | Arrival Time (ms) | Burst Time (ms) |
|---|---|---|
| P1 | 0 | 5 |
| P2 | 1 | 3 |
| P3 | 2 | 2 |

Using the First-Come, First-Served (FCFS) CPU scheduling algorithm calculate the average waiting time and the average turnaround time. (Officer (IT) Exam: 31 Jul 2026) [bscs 02]

2. (a) নিচের গুলোর Distributed-GPT control and computing এর কার্যকারিতা লিখুন:
   (b) Clock cycle কী? একটি প্রসেসরের clock speed 3.5 GHz বলতে কী বোঝায়?
   (c) নিচের সারণীটি দেখুুন:

| Process | Burst Time (milli second) | Priority |
|---|---|---|
| P_1 | 15 | 1 |
| P_2 | 2 | 1 |
| P_3 | 4 | 3 |
| P_4 | 2 | 4 |
| P_5 | 8 | 2 |

(a) অ্যালগরিদম প্রতিটি সংক্ষেপ ও সারণির উত্তর লেখুন।
(b) FCFS এবং SJF Scheduling algorithm গুলোর মধ্যে Gantt Chart এবং অপেক্ষাকৃত সুষম এবং গড়ের (average waiting time) ও টার্ন অ্যারাউন্ড (turnaround time) এর হিসাব নির্ণয় কর। **(Assistant Programmer - Department of Immigration & Passports Exam: 15.07.2026) [compact it 1464]**

3. **Consider the set of 3 processes whose arrival time and burst time are given below-**

| Process | AT | BT |
|---|---|---|
| P1 | 0 | 5 |
| P2 | 1 | 4 |
| P3 | 2 | 2 |

**If the CPU scheduling policy is round robin with time quantum=2, finds out the completion time, turnaround time, waiting time, and response time** **(Cadet College (Combined) - Lecturer ICT Exam: 11.05.2025) [compact it 1447]**

4. **There are 3 tasks P1, P2, and P3. The arrival time and duration of each task is given below. Apply the round-robin scheduling algorithm with quantum size-20 to schedule the tasks in a single core machine. Calculate the turnaround time for each task. (All tasks have the same priority)** **(BPSC (Ministry of Food) Network/Website Manager Exam: 21.05.2025 (CSE)) [compact it 1338]**

| Task | Arrival time (ms) | Duration (ms) |
|---|---|---|
| P1 | 0 | 40 |
| P2 | 5 | 40 |
| P3 | 10 | 20 |

5. **Calculate the average waiting time.** **(BCIC Assistant Programmer Exam: 14.02.2025 (BUET)) [compact it 1328]**

| Process | Burst Time |
|---|---|
| P1 | 21 |
| P2 | 3 |
| P3 | 6 |

6. **(খ) CPU Scheduling কী? যে যে কারণে CPU Scheduling করতে হয় সেগুলো লিখুন।** **(17th NTRCA Lecturer (ICT) Written Exam (ICT): 2023) [compact it 624]**
## CPU Scheduling Algorithms

1. A CPU scheduling algorithm must choose a process from the ready queue to execute. (Combined Bank Officer (IT) Exam: 09.05.2026) [debug it]

2. **Five jobs A, B, C, D, and E arrive at a compute center at approximately the same time. Their estimated running times are 10, 6, 2, 4, and 8 minutes, respectively. Their (externally defined) priorities are 3, 5, 2, 1, and 4, respectively, with 5 being the highest priority. For each of the following scheduling algorithms, determine the mean process turnaround time. (Ignore process switching overhead.) (a) Round-robin (quantum = 2 minutes), (b) Priority scheduling, (c) First-come, first-served (run in order 10, 6, 2, 4, 8), (d) Shortest job first.** **(Combined Bank Senior Officer (IT) Exam: 17.10.2025 (E-Zone)) [compact it 1421]**

3. **Process CPU burst and Priority given. Calculate Average Waiting time using (i) Preemptive Priority (ii) Non Preemptive priority.** **(DPDC - Assistant Engineer (CSE) Exam: 17.10.2025) [compact it 1453]**

4. **Calculate Average Waiting time using (i) FCFS (ii) SJF and (iii) RR (Quantum = 2) for the following:** **(BCC - Assistant Programmer Exam: 18.10.2025 (BCC)) [compact it 1443]**

5. **(a) Consider the following set of process with the length of CPU burst given in milliseconds-** **(BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) Exam: 29.05.2025 (CS/CSE)) [compact it 1351]**

| Process | Burst time | Priority |
|---|---|---|
| P1 | 10 | 3 |
| P2 | 1 | 1 |
| P3 | 2 | 3 |
| P4 | 1 | 4 |
| P5 | 5 | 2 |

All process arrived at time 0. Lower number has higher priority.
 * (i) Draw the Gantt chart using FCFS, Non-preemptive priority, SJF and RR (Quantum = 1).
 * (ii) What is the turnaround time of each process for each of the scheduling algorithms in (i)?
 * (iii) What is waiting time of each process for each of the scheduling algorithms in (i)?
 * (iv) Which algorithm resulting minimum average waiting time?

6. **a) Define CPU Scheduling. Draw Gantt charts and find average waiting time for: i) FCFS, ii) SJF (Non-preemptive), iii) Preemptive Priority.** **(BPSC (Ministry of Food) Network/Website Manager Exam: 21.05.2025 (ICT)) [compact it 1344]**

7. **Process burst time and priority given. Draw Gantt chart and find average waiting time for preemptive priority scheduling.** **(BPSC (Ministry of Food) Network/Website Manager Exam: 21.05.2025 (CSE)) [compact it 1339]**

8. **Shortest job scheduling (SJF) is a __________.** **(BARI - Assistant Maintenance Engineer Exam: 15.11.2025) [compact it 1451]**

9. **Round-robin scheduling (RR) is a __________.** **(BARI - Assistant Maintenance Engineer Exam: 15.11.2025) [compact it 1451]**

10. **(a) FCFS and SJF Scheduling. (b) Find AWT and ATAT.** **(Sonali Bank PLC - Assistant Database Administrator Written Exam: 23.02.2024) [compact it 316]**

11. **Advantages of CPU Scheduling Algorithm.** **(BARI - Assistant Maintenance Engineer Exam: 10.05.2024) [compact it 1460]**

12. **What type of RR Scheduling Algorithm: Preemtive/ Non-Preemtive?** **(BARI - Assistant Maintenance Engineer Exam: 10.05.2024) [compact it 1461]**

13. **Consider the following six processes each having its own unique processing time and arrival time.**
| Processes | Arrival time | Processing time |
|---|---|---|
| P1 | 0 | 8 |
| P2 | 0 | 4 |
| P3 | 0 | 5 |
| P4 | 1 | 9 |
| P5 | 1 | 7 |
| P6 | 0 | 1 |
**Find average turnaround time using shortest job first scheduling algorithm.**
**(BIWTA Assistant Engineer (CSE) Exam: 24.02.2023 (BUET)) [compact it 461]**

14. **Find average turnaround time and average waiting time using round robin and FCFS algorithm?**
| Process | Arrival Time | Execute Time |
|---|---|---|
| P0 | 0 | 5 |
| P1 | 1 | 3 |
| P2 | 2 | 8 |
| P3 | 3 | 6 |
**(Teletalk Assistant Manager (IT) Exam: 2023) [compact it 467]**

15. **Starvation in SJF, Starvation free scheduling algorithm name. (Question not clear)** **(RPGCL Assistant Manager (ICT) Exam: 2022 (BUET)) [compact it 654]**

16. **Consider the processes P1, P2, P3, P4 given in the below table, arrives for execution in the same order, with Arrival Time 0, and given Burst Time, let's find the average waiting time using the FCFS scheduling algorithm.** **(RAKUB Maintenance Engineer (PO) Exam: 05.10.2021) [compact it 856]**

## Memory Management & Paging

1. **A system uses 16 bit logical address and a page size of 1 KB.**
   **(i) How many pages are in logical address space?**
   **(ii) How many bits are used for the page number and offset?** **(Dhaka WASA - Assistant Maintenance Engineer (Network) Exam: 04.07.2025 (BUET)) [compact it 1437]**

2. **Consider a logical address space of 512 pages, each of 2-KB page size, mapped onto a physical memory containing 128 frames.**
   **a. How many bits are required in the logical address?**
   **b. How many bits are required in the physical address?** **(Combined Bank Senior Officer (IT) Exam: 17.10.2025 (E-Zone)) [compact it 1420]**

3. **(a) Consider a computer system with the following specifications:** **(BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) Exam: 29.05.2025 (CS/CSE)) [compact it 1351]**
 * Physical memory (RAM): 4\text{ GB}
 * Page size: 4\text{ KB}
 * Virtual address space: 32\text{ bits}
 * Page table entry size: 8\text{ bytes}
**Answer the following:**
 * **(i) How many pages are there in the virtual address space? Explain your answer.**
 * **(ii) What is the size of the page table? Explain your answer.**

4. **Compare “Paging” and “Segmentation” memory management technique?** **(BPSC (Ministry of Food) Network/Website Manager Exam: 21.05.2025 (CSE)) [compact it 1340]**

5. **The __________ swaps process in and out of the memory.** **(BARI - Assistant Maintenance Engineer Exam: 15.11.2025) [compact it 1451]**

6. **Difference between Paging and Segmentation.** **(BTCL - JAM (Technical) Exam: 05.04.2024 (BUET)) [compact it 383]**

7. **(ক) Swapping কী? Internal এবং External Fragmentation এর মধ্যে পার্থক্য লিখুন।** **(18th NTRCA - College Lecturer (ICT) Exam: 13.07.2024) [compact it 414]**

8. **Find out total number of pages, when page size 4KB and address space 32 bit.** **(Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) Exam: 2023 (BUET)) [compact it 588]**

9. **(ক) Paging এবং Segmentation এর পার্থক্য লিখুন।** **(17th NTRCA Lecturer (ICT) Written Exam (CSE): 2023) [compact it 609]**

10. **(খ) Operating System-এর Memory hierarchy সচিত্র বর্ণনা করুন।** **(17th NTRCA Lecturer (ICT) Written Exam (CSE): 2023) [compact it 611]**

11. **(খ) Internal এবং External fragmentation এর মধ্যে পার্থক্য লিখুন।** **(17th NTRCA Lecturer (ICT) Written Exam (ICT): 2023) [compact it 623]**

12. **(a) What is demand paging?** **(BITAC Assistant Maintenance Engineer (ICT) Exam: 2021 (BUET)) [compact it 821]**

## Virtual Memory & Page Replacement (Thrashing)

1. **Explain the concept of thrashing in an operating system, describing how it occurs in a demand-paged virtual memory system and how it impacts CPU utilization and overall system performance.** **(Combined Bank Senior Officer (IT) Exam: 17.10.2025 (E-Zone)) [compact it 1422]**

2. **a) Write about notes on i) Virtual memory, and ii) Cache memory.** **(BPSC (Ministry of Food) Network/Website Manager Exam: 21.05.2025 (ICT)) [compact it 1343]**

3. Consider the following page reference string: 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2, 1, 2, 0, 1, 7, 0, 1. Assuming a system with 3 page frames initially empty, calculate the number of page faults using the following page replacement algorithms: (i) FIFO (First-In, First-Out), (ii) LRU (Least Recently Used), and (iii) Optimal Page Replacement. [BSCCPL AME 21-08-2026 (BUET)]

4. **Consider a reference string 4,7,6,1,2,7,2 the number of frames in the memory is 3. Using page Replacement Algorithm (LRU), find the number of page fault.** **(BPDB - Assistant Engineer (CSE) Exam: 10.05.2024 (BUET)) [compact it 391]**

5. **Why virtual memory needed?** **(Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) Exam: 27.01.2023) [compact it 477]**

6. **Consider page reference string 1, 3, 0, 3, 5, 6, 3 with 3 page frames. Find the number of page faults.** **(Combined Bank Assistant Programmer Exam: 09.06.2023) [compact it 493]**

7. **Difference between physical memory and virtual memory, also describe the advantages and disadvantages of virtual memory.** **(Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer Exam: 23.11.2023 (BIBM)) [compact it 553]**

8. **(c) Define paging and trashing in the context of OS.** **(BPSC (Multiple Ministry) Assistant Programmer (ICT) Exam: 19.07.2023) [compact it 490]**

9. **What is page fault in computing systems? What does it occur?** **(BICIC Assistant Programmer Exam: 2022 (BUET)) [compact it 632]**

10. **Write short note on Virtual Memory and Cache memory.** **(SPCB Sub-Assistant Programmer Exam: 2022) [compact it 738]**

11. **(ii) Virtual Memory এর প্রয়োজনীয়তা কি ব্যাখ্যা করুন।** **(BPSC Assistant Programmer (Ministry of Commerce) Exam: 2021) [compact it 786]**

12. **A system uses 3 page frames for storing process pages in main memory. It uses the Least Recently Used (LRU) page replacement policy. Assume that all the page frames are initially empty. What is the total number of page faults that will occur while processing the page reference string given below? 4, 7, 6, 1, 7, 6, 1, 2, 7, 2.** **(BPDB Assistant Engineer (CSE) Exam: 2021 (BUET)) [compact it 817]**

13. **Briefly explain the concept of ‘Thrashing’ in terms of OS.** **(Titas Gas Assistant Engineer (CSE) Exam: 2021 (BUET)) [compact it 822]**

## Process Management & Process States

1. **(b) What is process? Describe different states of a process.** **(BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) Exam: 29.05.2025 (CS/CSE)) [compact it 1352]**

2. **(c) Define context switch with proper example.** **(BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) Exam: 29.05.2025 (CS/CSE)) [compact it 1352]**

3. **(খ) Process কী? বিভিন্ন ধরনের Process state এর কাজ বর্ণনা করুন।** **(18th NTRCA - College Lecturer (ICT) Exam: 13.07.2024) [compact it 414]**

4. **Explain the process state.** **(EGCB Sub-Divisional Engineer (ICT) Exam: 28.01.2023 (BUET)) [compact it 563]**

5. **(ক) Process কী? একটি Process এর বিভিন্ন ধাপগুলো লিখুন।** **(17th NTRCA Lecturer (ICT) Written Exam (ICT): 2023) [compact it 623]**

6. **অথবা, (ক) Process Control Block (PCB) কী? এটি একটি Process সংক্রান্ত যে যে তথ্য রাখে সেগুলো লিখুন।** **(17th NTRCA Lecturer (ICT) Written Exam (ICT): 2023) [compact it 624]**

7. **Write down the name of four information stored in PCB (Process Control Block).** **(RPGCL Assistant Manager (ICT) Exam: 2022 (BUET)) [compact it 653]**

8. **Operating System এর Process state diagram অঙ্কন করুন?** **(DESCO Sub-Assistant Engineer (CSE) Exam: 16.09.2022 (DPI)) [compact it 698]**

9. **(i) Operating System এর Process State Transition Diagram আঁকুন ও ব্যাখ্যা করুন।** **(BPSC Assistant Programmer (Ministry of Commerce) Exam: 2021) [compact it 786]**

## Process Synchronization & Concurrency

1. Two independent applications running concurrently attempt to update the same file located at a same file location. Both applications may read and modify the file at nearly the same time, creating a possibility of race conditions, lost updates, or inconsistent data. What type of consistency problem can occur in this situation, and which synchronization technique(s) should be used to ensure that only one application can safely update the file at a time? Explain the mechanism and justify the most appropriate solution. [BSCCPL AME 21-08-2026 (BUET)]

2. **What is Semaphore? How would you improve performance when using semaphores?** **(WZPGCL Assistant Engineer (CSE) Exam: 27.05.2023) [compact it 504]**

3. **(গ) Process Synchronization এর ক্ষেত্রে Race condition ব্যাখ্যা করুন।** **(17th NTRCA Lecturer (ICT) Written Exam (ICT): 2023) [compact it 624]**

4. **(ক) Critical Section Problem কী? ইহা কীভাবে সমাধান করা যায়?** **(Software Assistant Programmer Exam: 13.10.2022) [compact it 710]**

## Deadlock & Resource Allocation

1. **What is Deadlock? Given a scenery and find out the process is face deadlock sitiation?** **(IFIC Bank - Officer IT Exam: 2025 (IFIC)) [compact it 1448]**

2. **The four conditions that are necessary for a resource deadlock to occur are mutual exclusion, hold and wait, no preemption and circular wait. Give an example to show that these conditions are not sufficient for a resource deadlock to occur.** **(DPDC Assistant Manager (ICT) Exam: 27.06.2025 (BUET)) [compact it 1364]**

3. **(a) Define operating system. Why resource allocation graph used for deadlock detection?** **(Cadet College (Combined) - Lecturer ICT Exam: 11.05.2025) [compact it 1446]**

4. **What is Deadlock? Write Conditions for Deadlock and also write Deadlock.** **(BUET - Assistant Programmer Exam: 21.06.2025 (BUET)) [compact it 1434]**

5. **Banker's Algorithm: 5 processes P_0 through P_4; 3 resource types A (10 instances), B (5 instances), and C (7 instances).** **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it 1321]**
   * (a) Need matrix
   * (b) Safe state or Unsafe
   Snapshot at time T_0:
The content of the matrix. Need is defined to be Max – Allocation.

6. **(a) Explain Circular wait deadlock.** **(Titas Gas - Assistant Engineer (CSE) Exam: 24.05.2024 (BUET)) [compact it 415]**

7. **Give the necessary conditions for deadlock to occur. Is it possible to have deadlock involving only a single process? Explain your answer.** **(Combined 2 Bank (Sonali & Janata) - Officer IT Exam: 04.10.2024 (BIBM)) [compact it 422]**

8. **Deadlock এর চারটি শর্ত লিখ।** **(BTCL - JAM (Technical) Exam: 05.04.2024 (BUET)) [compact it 381]**

9. **What is deadlock? Draw its diagram.** **(BKSP - Assistant Programmer Exam: 13.07.2024) [compact it 1457]**

10. **(ক) Deadlock কী? Deadlock Handling করার বিভিন্ন উপায়সমূহ আলোচনা করুন।** **(18th NTRCA - College Lecturer (ICT) Exam: 13.07.2024) [compact it 413]**

11. **What are the four necessary condition of deadlock in an operating system?** **(Milk Vita Assistant Manager (CSE/MIS) Exam: 2023) [compact it 472]**

12. **(a) What is deadlock in operating system (OS)? What are the four necessary and sufficient conditions behind deadlock?** **(BPSC (Multiple Ministry) Assistant Programmer (ICT) Exam: 19.07.2023) [compact it 490]**

13. **(b) A system has P processes each needing a maximum of m resources and a total of r resources available. Which conditions must hold to make the system deadlock free?** **(BPSC (Multiple Ministry) Assistant Programmer (ICT) Exam: 19.07.2023) [compact it 492]**

14. **Name and define characteristics properties of the Deadlock situation in a computer system.** **(BPSC (Ministry of Agriculture) Assistant Programmer Exam: 15.02.2022) [compact it 677]**

15. **(b) What are the conditions for deadlock situations? Explain briefly.** **(BPSC (Ministry of Home Affairs) Senior Computer Operator Exam: 13.09.2022 (CSE)) [compact it 688]**

16. **Banker's Algorithm: 5 processes P_0 through P_4; 3 resource types A (10 instances), B (5 instances), and C (7 instances). Snapshot at time T_0. The content of the matrix. Need is defined to be \text{Max} - \text{Allocation}. Check that \text{Request} \le \text{Available}. Executing safety algorithm shows that sequence \langle P_1, P_3, P_4, P_0, P_2 \rangle satisfies safety requirement.** **(RAKUB Maintenance Engineer (PO) Exam: 05.10.2021) [compact it 855]**

## File Systems & Disk Management

1. **NTFS stands for __________?** **(BARI - Assistant Maintenance Engineer Exam: 10.05.2024) [compact it 1462]**

2. **(খ) Unix file system এর প্রকারভেদ বর্ণনা করুন।** **(17th NTRCA Lecturer (ICT) Written Exam (CSE): 2023) [compact it 610]**

3. **কোন ড্রাইভে ‘My Document’ রাখা হয় এবং NTFS কী?** **(BPSC Computer Operator Exam: 2021) [compact it 780]**
