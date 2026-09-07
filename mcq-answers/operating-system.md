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
answer: C
explanation: রানিং অবস্থায় থাকা কোনো প্রসেস যখন I/O অপারেশনের প্রয়োজন বোধ করে বা কোনো ইভেন্টের জন্য অপেক্ষা করে, তখন সিপিইউ তাকে 'Waiting' বা 'Blocked' স্টেটে স্থানান্তর করে।

2. **Which of the following scheduling algorithm is non preemptive?** *[NPCBL Executive Trainee (Software) 2023 compact it 37 (ET: N/A)]*
   (a) Shortest Job First
   (b) FCFS
   (c) Rounf Robin
   (d) Priority Scheduling
answer: B
explanation: FCFS (First-Come, First-Served) শিডিউলিং অ্যালগরিদমটি শতভাগ নন-প্রিম্পটিভ (Non-preemptive); অর্থাৎ কোনো প্রসেস একবার সিপিইউ বরাদ্দ পেলে তা শেষ না হওয়া পর্যন্ত বা I/O-তে না যাওয়া পর্যন্ত সিপিইউ ছাড়ে না।

3. **Time during which a job is processed by the Computer is:** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 56 (ET: N/A)]*
   (ক) Delay time
   (খ) Real time
   (গ) Execution time
   (ঘ) Process time
answer: C
explanation: কম্পিউটার বা সিপিইউ দ্বারা কোনো জব বা প্রোগ্রামের নির্দেশাবলী কার্যকর বা প্রসেস হওয়ার সময়কে 'এক্সেকিউশন টাইম' (Execution time) বলা হয়।

4. **In Unix operating system, which system call is used for creating a new process?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 126 (ET: N/A)]*
   a) Exec()
   b) Create Process ()
   c) Fork ()
   d) None of them
answer: C
explanation: ইউনিক্স বা লিনাক্স অপারেটিং সিস্টেমে বিদ্যমান প্রসেসের একটি ক্লোন হিসেবে নতুন চাইল্ড প্রসেস তৈরি করতে `fork()` সিস্টেম কল ব্যবহৃত হয়।

5. **A job which is schedule to run periodically at fixed times or intervals is known as-** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 99 (ET: N/A)]*
   (a) Batch Job
   (b) Cron job
   (c) Shell Script
   (d) None of the above
answer: B
explanation: নির্দিষ্ট সময়সূচি বা বিরতিতে স্বয়ংক্রিয়ভাবে ব্যাকগ্রাউন্ডে চলার জন্য শিডিউল করা জবকে 'ক্রন জব' (Cron job) বলা হয়।

6. **Which one of the following statements is true with respect to Printer Daemon process?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 103 (ET: N/A)]*
   (a) The printer daemon of Operating System runs in kernel mode.
   (b) Jobs in the printer daemon queue cannot be removed once inserted.
   (c) Printer daemon application runs only when it is printing.
   (d) Printer daemon runs as a service in Operating System
answer: D
explanation: ডেমোন (Daemon) হলো অপারেটিং সিস্টেমের ব্যাকগ্রাউন্ডে সার্বক্ষণিক সক্রিয় থাকা সার্ভিস প্রক্রিয়া; সুতরাং প্রিন্টার ডেমোন ওএস-এর একটি ব্যাকগ্রাউন্ড সার্ভিস (Service) হিসেবে কাজ করে।

7. **Which of the following Process scheduling algorithm is highly improbable to be implemented?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 107 (ET: N/A)]*
   (a) FCFS Scheduling
   (b) Priority Scheduling
   (c) Shortest Job First Scheduling
   (d) None of the above
answer: C
explanation: Shortest Job First (SJF) অ্যালগরিদম বাস্তবে কার্যকর করা প্রায় অসম্ভব, কারণ পরবর্তী সিপিইউ বার্স্ট টাইম ঠিক কতটুকু হবে তা কোনো প্রসেস চালনার আগে নিশ্চিতভাবে জানা সম্ভব নয়।

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
answer: C
explanation: লজিক সার্কিট অনুযায়ী আউটপুট ফাংশন $W = T \cdot P + T \cdot \overline{R}$; অর্থাৎ তাপমাত্রা > ২০০°F এবং চাপ > ২২০ psi হলে, অথবা তাপমাত্রা > ২০০°F এবং গতি < ৪৮০০ rpm হলে ওয়ার্নিং লাইট জ্বলে উঠবে। তাই (a) ও (b) উভয় শর্তেই এটি সত্য।

9. **What is the disadvantage of multithreading?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 165 (ET: N/A)]*
   a) Share the same address space
   b) Simultaneous access to multiple application
   c) Low cost communication
   d) Difficulty in managing concurrency
answer: D
explanation: একই অ্যাড্রেস স্পেস ও রিসোর্স একাধিক থ্রেড দ্বারা যুগপৎ শেয়ার করায় ডেডলক ও রেস কন্ডিশন প্রতিরোধ করে কনকারেন্সি নিয়ন্ত্রণ করা অত্যন্ত কঠিন (Difficulty in managing concurrency)।

10. **The time needs from the process arrival to the completion of that process is called** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 165 (ET: N/A)]*
   a) Waiting time
   b) Response time
   c) Turnaround time
   d) Throughput
answer: C
explanation: একটি প্রসেস সিস্টেমে পৌঁছানোর (Arrival) পর থেকে তা সম্পূর্ণ শেষ (Completion) হওয়া পর্যন্ত অতিবাহিত মোট সময়কে 'টার্নঅ্যারাউন্ড টাইম' (Turnaround time) বলে।

11. **Which is not the state of a process in an Operating System?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 166 (ET: N/A)]*
   a) New
   b) Sleep
   c) Terminated
   d) Ready
answer: B
explanation: অপারেটিং সিস্টেমের স্ট্যান্ডার্ড ৫-স্টেট লাইফসাইকেল মডেলে New, Ready, Running, Waiting এবং Terminated বিদ্যমান থাকে; 'Sleep' কোনো মৌলিক স্টেট নয়।

12. **The maximum number of processes that can be in ready state in computer system with n CPU's is—** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 204 (ET: AUST)]*
   A) n
   B) \text{n}^2
   C) 2n
   D) independent of n
answer: D
explanation: $n$ সংখ্যক সিপিইউ বিশিষ্ট সিস্টেমে একই সাথে সর্বোচ্চ $n$ টি প্রসেস Running অবস্থায় থাকতে পারে; কিন্তু Ready কিউতে কতগুলো প্রসেস থাকবে তা সিপিইউ সংখ্যার ওপর নির্ভর করে না (Independent of $n$)।

13. **In UNIX, processes that have finished execution but have not yet had their status collected are known as-** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 205 (ET: AUST)]*
   A) Sleeping processes
   B) Stopped processes
   C) Zombie processes
   D) Orphan processes
answer: C
explanation: ইউনিক্সে যেসব প্রসেস এক্সেকিউশন শেষ করেছে কিন্তু তাদের প্যারেন্ট প্রসেস এখনও তাদের এক্সিট স্ট্যাটাস সংগ্রহ করেনি, সেগুলোকে 'জম্বি প্রসেস' (Zombie processes) বলা হয়।

14. **Which of the following process scheduling algorithm may lead to starvation?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 206 (ET: AUST)]*
   A) FIFO
   B) Round Robin
   C) Shortest Job Next
   D) None of these
answer: C
explanation: Shortest Job Next (SJN/SJF) অ্যালগরিদমে অনবরত স্বল্প দৈর্ঘ্যের জব আসতে থাকলে অপেক্ষাকৃত বড় জবগুলো দীর্ঘক্ষণ বা অনির্দিষ্টকাল সিপিইউ না পেয়ে স্টারভেশন (Starvation)-এর শিকার হয়।

15. **A common representation of process scheduling is -** *[BPSC Assistant Maintenance Engineer 2019 compact it 192 (ET: N/A)]*
   (a) Static diagram
   (b) Scheduling queues
   (c) Queuing diagram
   (d) Process control block
answer: C
explanation: অপারেটিং সিস্টেম তত্ত্বে প্রসেস শিডিউলিংয়ের কিউগুলোর মধ্য দিয়ে প্রসেস সঞ্চালনের প্রবাহকে চিত্রিত করতে সাধারণভাবে 'কিউয়িং ডায়াগ্রাম' (Queuing diagram) ব্যবহৃত হয়।

16. **The scheduling queue is generally stored as-** *[BPSC Assistant Maintenance Engineer 2019 compact it 193 (ET: N/A)]*
   (a) A liner array
   (b) A stack
   (c) A linked list
   (d) A tree
answer: C
explanation: অপারেটিং সিস্টেমে শিডিউলিং কিউগুলো সাধারণত লিঙ্কড লিস্ট (Linked list) হিসেবে সংরক্ষিত থাকে, যাতে সহজে নতুন প্রসেস যুক্ত ও সম্পন্ন প্রসেস অপসারণ করা যায়।

17. **To execute a program, an OS creates a number of ________, each one for, running a different program.** *[BPSC Assistant Maintenance Engineer 2019 compact it 194 (ET: N/A)]*
   (a) Processors
   (b) Threads
   (c) Virtual processors
   (d) Kernel
answer: C
explanation: মাল্টিপ্রোগ্রামিং ধারণায় বিভিন্ন প্রোগ্রাম আলাদাভাবে এক্সেকিউট করার জন্য অপারেটিং সিস্টেম ভার্চুয়াল প্রসেসর (Virtual processors) বা লজিক্যাল প্রসেস এক্সিকিউশন স্টেট তৈরি করে।

18. **What is long term scheduling?** *[Combined 3 Bank Assistant Programmer 2018 compact it 230 (ET: N/A)]*
   A) It selects which process has to be brought into the ready queue
   B) It selects which process has to be executed next and allocates CPU
   C) It selects which process to remove from memory by swapping
   D) It selects which process needs to be killed next
answer: A
explanation: লং-টার্ম শিডিউলার সেকেন্ডারি স্টোরেজ বা জব পুল থেকে প্রসেস নির্বাচন করে মূল মেমোরির রেডি কিউতে (Ready queue) নিয়ে আসে।

19. **Multi-Threaded programs are-** *[Combined 3 Bank Assistant Programmer 2018 compact it 230 (ET: N/A)]*
   A) Lesser prone to deadlocks
   B) more prone to deadlocks
   C) not at all prone to deadlock
   D) always results in deadlocks
answer: B
explanation: মাল্টি-থ্রেডেড প্রোগ্রামগুলোতে থ্রেডসমূহ একই মেমোরি ও শেয়ার্ড রিসোর্স বিভিন্ন লকিং মেকানিজমের মাধ্যমে অ্যাক্সেস করে, যার ফলে তারা ডেডলক হওয়ার ক্ষেত্রে অধিক ঝুঁকিপূর্ণ (More prone to deadlocks)।

20. **When there is a large logical address space, the best way of paging would be ________.** *[Combined 3 Bank Assistant Programmer 2018 compact it 231 (ET: N/A)]*
   A) Not to page
   B) a two-level paging algorithm
   C) not all prone to deadlock
   D) all of the above
answer: B
explanation: বৃহৎ লজিক্যাল অ্যাড্রেস স্পেসের ক্ষেত্রে একক পেজ টেবিল মেমোরিতে অতিরিক্ত জায়গা দখল করে, তাই টু-লেভেল পেজিং (Two-level paging) বা হায়ারার্কিক্যাল পেজিং সবচেয়ে কার্যকর সমাধান।

21. **What is the mounting of file system?** *[Combined 3 Bank Assistant Programmer 2018 compact it 231 (ET: N/A)]*
   A) creating of a file system
   B) deleting a file system
   C) attaching portion of the file system into a directory structure
   D) removing portion of the file system into a directory structure
answer: C
explanation: মাউন্টিং (Mounting) হলো কোনো স্টোরেজ ডিভাইসের ফাইল সিস্টেমকে ওএস-এর মূল ডিরেক্টরি কাঠামোর নির্দিষ্ট মাউন্ট পয়েন্টে সংযুক্ত (Attaching) করার প্রক্রিয়া।

22. **The main program in an operating system is called:** *[Combined 3 Bank Assistant Programmer 2018 compact it 232 (ET: N/A)]*
   A) kernel
   B) file manager
   C) Directory
   D) NOS
answer: A
explanation: অপারেটিং সিস্টেমের কেন্দ্রীয় এবং সবচেয়ে গুরুত্বপূর্ণ কোর প্রোগ্রামটিকে 'কার্নেল' (Kernel) বলা হয়, যা হার্ডওয়্যার রিসোর্স ব্যবস্থাপনা করে।

23. **The interval from the time of submission of a process to the time of completion is termed is ________.** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 259 (ET: N/A)]*
   A) Waiting time
   B) processing time
   C) turnaround time
   D) throughput
answer: C
explanation: কোনো প্রসেস জমা (Submission) দেওয়ার সময় থেকে তার সফল সমাপ্তি (Completion) পর্যন্ত মোট সময়কে 'টার্নঅ্যারাউন্ড টাইম' (Turnaround time) বলা হয়।

24. **Which of the following is not the state of a process in process Control Block (PCB)?** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 260 (ET: N/A)]*
   A) Old
   B) New
   C) waiting
   D) Running
answer: A
explanation: প্রসেস কন্ট্রোল ব্লকে (PCB) প্রসেসের অবস্থা হিসেবে New, Ready, Running, Waiting, Terminated সংরক্ষিত থাকে; কিন্তু 'Old' নামে কোনো প্রসেস স্টেট নেই।

## OS Concepts & Multiprogramming (16)

1. **The ______ system may manage a high degree of interaction between processes and is very useful for high speed and real-time processing.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 25 (ET: BIBM)]*
   (a) strongly coupled and loosely cohesive
   (b) loosely coupled and strongly cohesive
   (c) loosely coupled and loosely cohesive
   (d) strongly coupled and strongly cohesive
answer: D
explanation: স্ট্রংলি কাপল্ড ও স্ট্রংলি কোহেসিভ সিস্টেমে শেয়ার্ড মেমোরির মাধ্যমে প্রসেসগুলোর মধ্যে দ্রুত যোগাযোগ ও উচ্চ মাত্রার মিথস্ক্রিয়া সম্ভব হয়, যা রিয়েল-টাইম প্রসেসিংয়ের জন্য অত্যন্ত কার্যকর।

2. **Which one is an embedded operating system?** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 52 (ET: N/A)]*
   (ক) UNIX
   (খ) MS windows XP
   (গ) Windows CE
   (ঘ) Windows NET
answer: C
explanation: Windows CE (Windows Embedded Compact) হলো মাইক্রোসফটের একটি বিশেষায়িত রিয়েল-টাইম এমবেডেড অপারেটিং সিস্টেম যা হ্যান্ডহেল্ড এবং সীমিত মেমরিসম্পন্ন ডিভাইসে ব্যবহৃত হয়।

3. **Which initial program is called at the starting of a computer?** *[Rupali Bank Ltd. Assistant Network Engineer (ANE) 2021 compact it 81 (ET: N/A)]*
   a. Computer Startup Loader
   b. Operating System Details
   c. Bootstrap Loader
   d. Hardware System Details
answer: C
explanation: কম্পিউটার চালু করার পর রোমে থাকা বুটস্ট্র্যাপ লোডার (Bootstrap Loader) প্রোগ্রামটি সর্বপ্রথম এক্সিকিউট হয় এবং সেকেন্ডারি স্টোরেজ থেকে ওএস-কে প্রধান মেমোরিতে (RAM) লোড করে।

4. **What is the mean of the Booting in the system?** *[BREB Assistant General Manager (O&M/E&C) 2021 compact it 137 (ET: N/A)]*
   a. Restarting computer
   b. Install the program
   c. To scan
   d. To turn off
answer: A
explanation: অপারেটিং সিস্টেমকে লোড করে কম্পিউটারকে চালু বা পুনরায় চালু (Restarting/starting computer) করার সামগ্রিক প্রক্রিয়াকে বুটিং (Booting) বলে।

5. **What is LINUX?** *[BREB Assistant Enforcement Coordinator 2021 compact it 140 (ET: N/A)]*
   ক. Operating System
   খ. Application Program
   গ. Antivirus software
   ঘ. Firewall
answer: A
explanation: লিনাক্স (Linux) হলো একটি বহুল ব্যবহৃত উন্মুক্ত বা ওপেন-সোর্স অপারেটিং সিস্টেম (Operating System)।

6. **Where is the Boot strapping program stored?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 160 (ET: N/A)]*
   A) ROM
   B) Hard disk
   C) CD
   D) RAM
answer: A
explanation: প্রাথমিক বুটস্ট্র্যাপ প্রোগ্রাম বা BIOS ফার্মওয়্যার মাদারবোর্ডের নন-ভোলাটাইল মেমোরি অর্থাৎ রোমে (ROM) সংরক্ষিত থাকে।

7. **Which one of the first 64-bit operating system?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 161 (ET: N/A)]*
   A) Windows Vista
   B) Mac
   C) Linux
   D) Windows XP
answer: C
explanation: বিকল্পগুলোর মধ্যে লিনাক্স (Linux) সর্বপ্রথম (১৯৯৫ সালে DEC Alpha আর্কিটেকচারে) পূর্ণাঙ্গ ৬৪-বিট সংস্করণ হিসেবে আত্মপ্রকাশ করে।

8. **In a computer, folder opening is denied by which of the following names?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 161 (ET: N/A)]*
   A) con
   B) com
   C) mak
   D) make
answer: A
explanation: ডস ও উইন্ডোজ অপারেটিং সিস্টেমে 'con' (কনসোল) হলো একটি সংরক্ষিত ডিভাইস নাম (Reserved device name), যার কারণে 'con' নামে কোনো ফোল্ডার বা ফাইল তৈরি করা যায় না।

9. **Which of the following contains configuration information of a window?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 163 (ET: N/A)]*
   A) .exe
   B) .ini
   C) .dill
   D) .chm
answer: B
explanation: উইন্ডোজে বিভিন্ন সফটওয়্যারের প্রাথমিক সেটিংস ও কনফিগারেশন তথ্য সংরক্ষণ করতে `.ini` (Initialization) এক্সটেনশনের ফাইল ব্যবহৃত হয়।

10. **Who preside the interface between a process and the OS?** *[BPSC Assistant Maintenance Engineer 2019 compact it 193 (ET: N/A)]*
    (a) Kernel
    (b) System calls
    (c) Command
    (d) Graphical user
answer: B
explanation: একটি চলমান প্রোগ্রাম বা প্রসেস এবং অপারেটিং সিস্টেমের কার্নেলের মধ্যে প্রধান যোগাযোগ মাধ্যম বা ইন্টারফেস হিসেবে 'সিস্টেম কল' (System calls) কাজ করে।

11. **Which O/S is recommended for real time system?** *[Combined Bank Maintenance Engineer 2018 compact it 227 (ET: N/A)]*
    A) Windows
    B) Unix
    C) Oracle
    D) None of this
answer: D
explanation: রিয়েল-টাইম সিস্টেমের জন্য বিশেষায়িত RTOS (যেমন VxWorks, QNX) প্রয়োজন; সাধারণ উইন্ডোজ বা সাধারণ ইউনিক্স ওএস রিয়েল-টাইম নিশ্চয়তা দিতে পারে না (সঠিক উত্তর: None of this)।

12. **Which OS is recommended for real time systems?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 247 (ET: N/A)]*
    A) Windows
    B) Unix
    C) Oracle
    D) None of them
answer: D
explanation: সাধারণ বাণিজ্যিক অপারেটিং সিস্টেম (Windows বা সাধারণ Unix) রিয়েল-টাইম প্রসেসিংয়ের কঠোর ডেডলাইন নিশ্চিত করতে পারে না বিধায় কোনোটিই সুপারিশকৃত নয় (সঠিক উত্তর: None of them)।

13. **Which one loads first when you boot up your Computer?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 247 (ET: N/A)]*
    A) BIOS
    B) Operating System
    C) Keyboard driver
    D) None of them
answer: A
explanation: কম্পিউটার অন করার পরপরই রোমে থাকা বেসিক ইনপুট/আউটপুট সিস্টেম বা BIOS (Basic Input/Output System) সর্বপ্রথম লোড হয়ে হার্ডওয়্যার চেক করে।

14. **Generally what type of server OS is chosen, where security concern is a great issue?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 248 (ET: N/A)]*
    A) Windows XP
    B) Windows Server 2000
    C) DOS V
    D) UNIX
answer: D
explanation: সার্ভারের সর্বোচ্চ নিরাপত্তা, স্থায়িত্ব ও পারমিশন ব্যবস্থাপনার ক্ষেত্রে ঐতিহ্যগতভাবেই ইউনিক্স (UNIX / Linux) অপারেটিং সিস্টেম অগ্রাধিকার পায়।

15. **The command password issued without an argument with change the password of –** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 248 (ET: N/A)]*
    A) Root user
    B) Current user
    C) User with lowest user id
    D) User with lowest group id
answer: B
explanation: ইউনিক্স ও লিনাক্সে কোনো প্যারামিটার ছাড়া শুধু `passwd` কমান্ড দিলে তা বর্তমান লগইন করা ব্যবহারকারীর (Current user) পাসওয়ার্ড পরিবর্তন করে।

16. **Multiprogramming systems ________** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 270 (ET: N/A)]*
    a. Are easier to develop than single programming system
    b. Execute each job faster
    c. Execute more jobs in the same time
    d. Are used only on large mainframe computers.
answer: C
explanation: মাল্টিপ্রোগ্রামিং সিস্টেমের মূল উদ্দেশ্য হলো সিপিইউ-কে ব্যস্ত রেখে একই নির্দিষ্ট সময়সীমার মধ্যে তুলনামূলকভাবে অধিক কাজ সম্পন্ন (Execute more jobs in the same time) করা।

## Virtual Memory & Paging (13)

1. **Which of the following page replacement algorithms suffers from Belady’s anomaly?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 8 (ET: BIBM)]*
   a) FIFO
   b) LRU
   c) Optimal Page Replacement
   d) Both LRU and FIFO
answer: A
explanation: বেলাডির অ্যানোমালি (Belady's Anomaly) হলো মেমোরিতে ফ্রেম সংখ্যা বৃদ্ধি করলেও পেজ ফল্টের সংখ্যা বেড়ে যাওয়ার ঘটনা; FIFO অ্যালগরিদম বেলাডির অ্যানোমালিতে আক্রান্ত হয় (LRU ও Optimal কখনো আক্রান্ত হয় না)।

2. **To keep track of how many frames have been allocated, how many are there, and how many are available, operating system maintain a—** *[Combined Bank Officer (IT) 04.10.2024 compact it 12 (ET: BIBM)]*
   (a) Memory table
   (b) Page table
   (c) mapping table
   (d) frame table
answer: D
explanation: অপারেটিং সিস্টেম ফিজিক্যাল মেমোরির ফ্রেমগুলোর বরাদ্দ ও লভ্যতা ট্র্যাক করার জন্য একটি ডেটা স্ট্রাকচার হিসেবে 'ফ্রেম টেবিল' (Frame table) সংরক্ষণ করে।

3. **Logical Memory is broken into blocks of the same size called-** *[NPCBL Executive Trainee (Software) 2023 compact it 38 (ET: N/A)]*
   a) Frames
   b) Pages
   c) raids
   d) Blocks
answer: B
explanation: অপারেটিং সিস্টেমে লজিক্যাল মেমোরিকে নির্দিষ্ট সমান আকারের ব্লকে বিভক্ত করা হলে সেগুলোকে 'পেজ' (Pages) বলা হয়, আর ফিজিক্যাল মেমোরির ব্লককে 'ফ্রেম' (Frames) বলে।

4. **A CPU generates 32-bit virtual addresses. The page size is 4 KB. The processor has a translation look-aside buffer (TLB) which can hold a total of 128 page table entries and is 4-way set associative. The minimum size of the TLB tag is:** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 24 (ET: BIBM)]*
   (a) 11 bits
   (b) 13 bits
   (c) 15 bits
   (d) 20 bits
answer: C
explanation: ভার্চুয়াল অ্যাড্রেস ৩২-বিট এবং পেজ সাইজ ৪ KB ($2^{12}$ B), তাই অফসেট ১২-বিট এবং ভার্চুয়াল পেজ নম্বর (VPN) = $32 - 12 = 20$ বিট। TLB-তে ১২৮টি এন্ট্রি ৪-ওয়ে সেট অ্যাসোসিয়েটিভ হওয়ায় সেট সংখ্যা = $128 / 4 = 32 = 2^5$, অর্থাৎ ইনডেক্স ৫-বিট। সুতরাং ট্যাগ সাইজ = $20 - 5 = 15$ বিট।

5. **What is the relationship between Paging and Virtual memory?** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 45 (ET: N/A)]*
   (ক) Virtual memory came before Paging
   (খ) When pages are created in disks, it is called a virtual memory
   (গ) Virtual memory can never be implemented without paging
   (ঘ) Both have the same concepts
answer: B
explanation: পেজিং হলো নন-কন্টিগুয়াস মেমোরি বরাদ্দের কৌশল; তবে যখন মেমোরির পেজগুলোকে সেকেন্ডারি স্টোরেজ বা ডিস্কে সংরক্ষণ করে সোয়াপিংয়ের মাধ্যমে মেমোরি সম্প্রসারণ করা হয়, তখন তাকে ভার্চুয়াল মেমোরি বলা হয়।

6. **Consider a virtual memory system with FIFO page replacement policy. For an arbitrary page access pattern, increasing the number of page frames in main memory will–** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*
   a) Always decrease the number of page faults
   b) Always increase the number of page faults
   c) Sometimes increase the number of page faults
   d) Never affect the number of page faults
answer: C
explanation: FIFO পেজ রিপ্লেসমেন্ট পলিসিতে বেলাডির অ্যানোমালির কারণে মেমোরিতে ফ্রেমের সংখ্যা বৃদ্ধি করলেও বিশেষ কিছু ক্ষেত্রে পেজ ফল্টের সংখ্যা কমে যাওয়ার পরিবর্তে বৃদ্ধি পেতে পারে (Sometimes increase the number of page faults)।

7. **Applying the LRU page replacement to the reference string 1 2 4 5 2 1 2 4. The main memory can accommodate pages and it already has pages and 2. Pape I came in before page 2 How many page faults will court?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 128 (ET: N/A)]*
   a) 3
   b) 4
   c) 5
   d) 6
answer: B
explanation: মেমোরিতে শুরুতে ১ ও ২ থাকার পর ৩ ফ্রেমের মেমোরিতে প্রদত্ত রেফারেন্স স্ট্রিং ১, ২, ৪, ৫, ২, ১, ২, ৪ এর জন্য ৪, ৫, ১ এবং ৪ অ্যাক্সেসকালে মোট ৪টি পেজ ফল্ট (Page faults) ঘটবে।

8. **Consider a virtual memory system where three pages are allocated for real memory. If the page replacement algorithm used is FIFO, how many page replacements take place for the access sequence: 1, 3, 2, 1, 4, 5, 2, 3, 4, 5?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 90 (ET: N/A)]*
   a. 2
   b. 3
   c. 4
   d. 6
answer: B
explanation: ৩টি ফ্রেমে প্রাথমিক লোডের পর মেমোরি পূর্ণ হয় (পেজ ১, ৩, ২)। এরপর পেজ ৪ (১ কে প্রতিস্থাপন করে), পেজ ৫ (৩ কে প্রতিস্থাপন করে) এবং পেজ ৩ (২ কে প্রতিস্থাপন করে)—এই ৩টি পেজ রিপ্লেসমেন্ট (Replacements) সংঘটিত হয় (মোট পেজ ফল্ট ৬টি)।

9. **Virtual memory located on:** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 171 (ET: N/A)]*
   a) RAM
   b) CPU
   c) Flash drive
   d) Hard drive
answer: D
explanation: ভার্চুয়াল মেমোরির সোয়াপ বা পেজিং স্পেস সেকেন্ডারি মেমোরি অর্থাৎ হার্ড ড্রাইভে (Hard drive) অবস্থান করে।

10. **Virtually memory হিসেবে RAM এর পাশাপাশি কোনটি ব্যবহার হয়?** *[BPSC Assistant Network Engineer 2019 compact it 196 (ET: N/A)]*
    A) Cache
    B) CPU Register
    C) CD-ROM
    D) Hard disk
answer: D
explanation: ভার্চুয়াল মেমোরি বাস্তবায়নের জন্য মূল মেমোরি বা RAM-এর সহযোগী স্টোরেজ হিসেবে হার্ডডিস্ক (Hard disk) ব্যবহৃত হয়।

11. **Memory management scheme by which a computer stores and retrieves data from secondary storage for use in main memory is-** *[Combined Bank Senior Officer (IT) 2018 compact it 223 (ET: DU)]*
    A) Paging
    B) Scheduling
    C) Batch processing
    D) Virtual storage
answer: A
explanation: পেজিং (Paging) হলো মেমোরি ম্যানেজমেন্টের একটি প্রমিত স্কিম যার মাধ্যমে কম্পিউটার সেকেন্ডারি স্টোরেজ থেকে নির্দিষ্ট আকারের ব্লকে (Pages) ডেটা এনে মূল মেমোরিতে লোড করে।

12. **Swap space exists in ---** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 260 (ET: N/A)]*
    A) CPU
    B) random memory
    C) primary memory
    D) secondary memory
answer: D
explanation: সোয়াপ স্পেস (Swap space) মূল মেমোরির অংশ নয়, বরং এটি সেকেন্ডারি মেমোরি বা হার্ডডিস্কে (Secondary memory) অবস্থিত।

13. **A page fault occurs ________** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 270 (ET: N/A)]*
    a. When the page is not in the memory
    b. When the page is in the memory
    c. When the process inters into the blocked state
    d. When the process is in the ready state
answer: A
explanation: কোনো প্রসেস এমন একটি মেমোরি পেজ অ্যাক্সেসের চেষ্টা করলে যা বর্তমানে মূল মেমোরিতে (RAM) উপস্থিত নেই, তখন পেজ ফল্ট (Page fault) ইন্টারাপ্ট ঘটে।

## Linux Commands & Administration (9)

1. **User passwords in Linux are stored as-** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 100 (ET: N/A)]*
   (a) Direct text data
   (b) Encrypted using some sort of hashing function
   (c) Encrypted using mono-alphabetic cipher
   (d) Encrypted using homophonic substitution cipher
answer: B
explanation: লিনাক্সে পাসওয়ার্ড সরাসরি প্লেইনটেক্সট আকারে রাখা হয় না, বরং ক্রিপ্টোগ্রাফিক সল্টেড হ্যাশিং অ্যালগরিদম (যেমন SHA-512) প্রয়োগ করে হ্যাশ ভ্যালু হিসেবে `/etc/shadow` ফাইলে সংরক্ষণ করা হয়।

2. **Which of the following Linux command has incorrect syntax?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 106 (ET: N/A)]*
   (a) cat sample.txt | grep -v a | sort - r
   (b) chown:group3 File 1
   (c) chmoda+rx viewer.sh
   (d) None of the above
answer: C
explanation: `chmoda+rx viewer.sh` কমান্ডটিতে কমান্ড নেম `chmod` এবং পারমিশন আর্গুমেন্ট `a+rx`-এর মাঝে কোনো স্পেস নেই, ফলে শেল এটিকে একটি কমান্ড হিসেবে খুঁজে না পেয়ে ত্রুটি দেখাবে।

3. **What is the maximum size of a file allowed in Linux with the following data Block Size = 4KB, inode data pointer size = 4 byte?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 106 (ET: N/A)]*
   (a) 1 TB
   (b) Less than 4TB
   (c) 2TB+2GB+2MB+64KB
   (d) More than 4 TB
answer: D
explanation: ইনোড স্ট্রাকচারে ট্রিপল ইনডাইরেক্ট পয়েন্টারের ধারণক্ষমতা $(4\text{KB}/4\text{B})^3 \times 4\text{KB} = 1024^3 \times 4\text{KB} = 4\text{ TB}$; এর সাথে ডাবল ও সিঙ্গেল ইনডাইরেক্ট ব্লকের মেমোরি যুক্ত করলে মোট সাইজ ৪ টেরাবাইটের কিছুটা বেশি (More than 4 TB) হয়।

4. **Which UNIX/Linux command is used to make all files and sub-directories in the directory "progs" executable by all users?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 107 (ET: N/A)]*
   (a) chmod -R a+x progs
   (b) chmod -R 222 progs
   (c) chmod -X a+x progs
   (d) chmod -X 222 progs
answer: A
explanation: `chmod -R a+x progs` কমান্ডে `-R` অপশন দিয়ে রিকার্সিভলি ফোল্ডারের অভ্যন্তরীণ সকল ফাইল ও ডিরেক্টরিতে এবং `a+x` দিয়ে সকল ব্যবহারকারীকে এক্সিকিউট পারমিশন প্রদান করা হয়।

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
answer: A
explanation: সিকিউরিটি ও প্রিভিলেজ ব্যবস্থাপনায় নির্দিষ্ট কিছু অধিকারের সমষ্টি তৈরি করে একাধিক ইউজারের উপর সমন্বিতভাবে প্রয়োগ করতে 'রোল' (Roles; যেমন Account MGR ও Inventory MGR) তৈরি করা হয়।

6. **In UNIX, the login prompt can be changed by changing the content of the file-** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 205 (ET: AUST)]*
   A) gettydefs
   B) contrab
   C) inittab
   D) init
answer: A
explanation: সনাতন ইউনিক্স অপারেটিং সিস্টেমে টার্মিনাল লাইন স্পিড এবং লগইন প্রম্পটের টেক্সট কনফিগার করার জন্য `/etc/gettydefs` ফাইলটির বিষয়বস্তু পরিবর্তন করতে হয়।

7. **Which of the following UNIX commands allows scheduling a program to be executed at specifies time?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 205 (ET: AUST)]*
   A) nice
   B) cron
   C) date and time
   D) schedule
answer: B
explanation: ইউনিক্সে নির্দিষ্ট সময়সূচিতে বা নির্ধারিত সময়ে স্বয়ংক্রিয়ভাবে কোনো স্ক্রিপ্ট বা জব চালনার শিডিউলিং সুবিধা দেয় `cron` (বা `crontab`)।

8. **What command is used to remove files UNIX?** *[BREB Assistant Junior Engineer (IT) 2019 compact it 218 (ET: N/A)]*
   A) dm
   B) rm
   C) delete
   D) erase
answer: B
explanation: ইউনিক্স এবং লিনাক্সে ফাইল মুছে ফেলতে (Remove) স্ট্যান্ডার্ড কমান্ড হিসেবে `rm` ব্যবহৃত হয়।

9. **You need to determine whether IP information has been assigned to your Windows NT. Which utility should you use?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 250 (ET: N/A)]*
   A) NBTSTAT
   B) NETSTAT
   C) IPCONFIG
   D) WINTPCFG
answer: C
explanation: উইন্ডোজ এনটি (Windows NT) অপারেটিং সিস্টেমে নেটওয়ার্ক ইন্টারফেসের আইপি অ্যাড্রেস এবং কনফিগারেশন পরীক্ষা করার মূল কমান্ড-লাইন ইউটিলিটি হলো `ipconfig`।

## Deadlock (6)

1. **A system has 6 identical resources and N processes competing for them. Each process can request at most 2 resources. Which one of the following values of N could lead to a deadlock?** *[Combined Bank Officer (IT) 04.10.2024 compact it 12 (ET: BIBM)]*
   (a) 1
   (b) 2
   (c) 3
   (d) 4
answer: D
explanation: সূত্রানুসারে ডেডলক এড়াতে $R \ge N(M-1)+1$ বা $6 \ge N(1)+1 \implies N \le 5$; অর্থাৎ ৫টি প্রসেস পর্যন্ত কোনো ডেডলক সম্ভব নয়। তবে পরীক্ষার প্রশ্নে টাইপো বা বিকল্পগুলোর মধ্য থেকে সম্ভাব্য সর্বোচ্চ চাপ হিসেবে (d) 4 চিহ্নিত করা হয়।

2. **Which one of the following is the deadlock avoidance algorithm?** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*
   a) banker’s algorithm
   b) round-robin algorithm
   c) Elevator algorithm
   d) karn’s algorithm
answer: A
explanation: ব্যাঙ্কার্স অ্যালগরিদম (Banker's Algorithm) হলো অপারেটিং সিস্টেমে ডেডলক পরিহার বা অ্যাভয়ডেন্স (Deadlock Avoidance)-এর একটি অত্যন্ত পরিচিত অ্যালগরিদম।

3. **Which of the following is not a deadlock handling strategy?** *[NPCBL Executive Trainee (Software) 2023 compact it 41 (ET: N/A)]*
   a) Deadlock prevention
   b) Timeout
   c) Deadlock detection and recovery
   d) Deadlock annihilation
answer: D
explanation: ডেডলক ব্যবস্থাপনায় Prevention, Avoidance, Detection & Recovery এবং Timeout স্বীকৃত কৌশল হলেও 'Deadlock annihilation' কোনো স্বীকৃত কৌশল নয়।

4. **A system has 12 magnetic tape drives and 3 processes: PO, PI, and P2. Process PO requires 10 tape drives, P1 requires 4 and P2 requires 9 tape drives. The current allocation tape drives of processes P0, PI and P2 is 5, 2, 2, respectively. Which of the following sequence is a safe sequence?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 126 (ET: N/A)]*
   a) P0, PI, P2
   b) P1, P2, P0
   c) P2, P0, P1
   d) P1, P0, P2
answer: D
explanation: মোট ১২টি ড্রাইভের মধ্যে বরাদ্দ ৯টি, অবশিষ্ট ৩টি। প্রসেসগুলোর বাকি চাহিদা: P0=৫, P1=২, P2=৭। শুরুতে কেবল P1 (চাহিদা ২ $\le$ ৩) সম্পন্ন হতে পারে। P1 শেষ হলে লভ্য হবে ৩ + ২ = ৫টি, যা দিয়ে P0 সম্পন্ন হবে; সবশেষে P2 সম্পন্ন হবে। সুতরাং নিরাপদ ক্রম P1, P0, P2।

5. **A computer system has 6 type drives and each process may need 3 type drives. What is the maximum number of processes than is guaranteed to be deadlock free?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 164 (ET: N/A)]*
   a) 4
   b) 3
   c) 2
   d) None
answer: C
explanation: ডেডলক মুক্ত থাকার নিশ্চয়তা সূত্র $N \le \frac{R - 1}{M - 1} = \frac{6 - 1}{3 - 1} = 2.5$; অর্থাৎ সিস্টেমে সর্বোচ্চ ২টি (2) প্রসেস থাকলে কখনোই ডেডলক হবে না (৩টি প্রসেস থাকলে প্রত্যেকে ২টি করে নিয়ে ডেডলক হতে পারে)।

   **Consider the following table named “Course”:**
   | Course Title | Content |
   |---|---|
   | Web Programming | Python, CSS, JS |
   What is the main problem/anomalies in the Course table? *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 164 (ET: N/A)]*
   a) Attribute name is not correct
   b) Table is larger
   c) Attribute has multiple value
   d) It has functional dependency
answer: C
explanation: ১ম নরমাল ফর্ম (1NF) অনুযায়ী প্রতিটি অ্যাট্রিবিউটে একটি একক পারমাণবিক মান থাকতে হয়; এখানে 'Content' ফিল্ডে একাধিক মান (Python, CSS, JS) সংরক্ষিত থাকায় এটি অ্যাট্রিবিউটের মাল্টিপল ভ্যালু সমস্যা।

6. **The request and release of resources are-** *[BPSC Assistant Maintenance Engineer 2019 compact it 194 (ET: N/A)]*
   (a) Command line
   (b) Interrupts statements
   (c) System calls
   (d) Special program
answer: C
explanation: অপারেটিং সিস্টেমে কোনো প্রসেস কর্তৃক রিসোর্সের আবেদন (Request) এবং ব্যবহারের পর তা অবমুক্ত (Release) করার কাজটি কার্নেল সিস্টেম কলের (System calls) মাধ্যমে পরিচালিত হয়।

## File Systems & Disk Management (4)

1. **A system has two IDE hard drives that are each divided into primary and extended partitions, which drive letter is assigned to the primary partition of the second drive?** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 42 (ET: N/A)]*
   (a) C
   (b) D
   (c) E
   (d) F
answer: B
explanation: ডস এবং উইন্ডোজের স্ট্যান্ডার্ড ড্রাইভ লেটার অ্যাসাইনমেন্ট নিয়ম অনুযায়ী, প্রথম ড্রাইভের প্রাইমারি পার্টিশন পায় 'C' এবং দ্বিতীয় ড্রাইভের প্রাইমারি পার্টিশন পায় 'D' (এরপর এক্সটেন্ডেড পার্টিশনের লজিক্যাল ড্রাইভগুলো E, F বরাদ্দ পায়)।

2. **Which of the following is not a true statement?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 131 (ET: N/A)]*
   a) Deleted files can be found in recycle bin
   b) Deleted files in recycle bin can be restored
   c) Disk space can be increased by sending files into recycle bin
   d) There may have multiple recycle bin
answer: C
explanation: কোনো ফাইলকে রিসাইকেল বিনে পাঠালে ডিস্কের খালি জায়গা বৃদ্ধি পায় না; রিসাইকেল বিন সম্পূর্ণরূপে খালি (Empty) না করা পর্যন্ত ফাইলগুলো ডিস্কের মেমরি দখল করে রাখে।

3. **Which of the following file name extension suggests that the file is backup of another file?** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 270 (ET: N/A)]*
   a. TXT
   b. COM
   c. BAS
   d. BAK
answer: D
explanation: `.BAK` এক্সটেনশন দ্বারা কোনো সফটওয়্যার বা সিস্টেমের মূল ফাইলের স্বয়ংক্রিয় সংরক্ষিত ব্যাকআপ ফাইল (Backup file) বোঝানো হয়।

4. **"INI" extension refers usually what kind of file?** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 270 (ET: N/A)]*
   a. Image file
   b. System file
   c. Hypertext file
   d. Image Color Matching Profile file
answer: B
explanation: `.INI` (Initialization) এক্সটেনশন বিশিষ্ট ফাইলগুলো মূলত সিস্টেম কনফিগারেশন বা সিস্টেম ফাইল (System file) হিসেবে অপারেটিং সিস্টেম ও সফটওয়্যারের প্যারামিটার ধারণ করে।

## Process Synchronization (2)

1. **A counting semaphore was initialized to 10. Then 6 wait operations and 4 signal operations were completed on this semaphore. The resulting value of the semaphore is___** *[Combined Bank Officer (IT) 04.10.2024 compact it 13 (ET: BIBM)]*
   (a) 0
   (b) 10
   (c) 8
   (d) 12
answer: C
explanation: কাউন্টিং সেমাফোরের প্রারম্ভিক মান ১০। প্রতিটি wait (P) অপারেশন মান ১ কমায় (১০ - ৬ = ৪) এবং প্রতিটি signal (V) অপারেশন মান ১ বাড়ায় (৪ + ৪ = ৮); অতএব সেমাফোরের চূড়ান্ত মান হবে ৮।

2. **A critical section is a program segment-** *[Combined Bank Officer (IT) 04.10.2024 compact it 13 (ET: BIBM)]*
   (a) which should run in a certain specified amount of time
   (b) which avoids deadlocks
   (c) where shared resources are accessed
   (d) which must be enclosed by a pair of semaphore (wait and signal) operations
answer: C
explanation: ক্রিটিক্যাল সেকশন (Critical section) হলো প্রোগ্রামের এমন একটি সংবেদনশীল অংশ যেখানে একাধিক প্রসেসের মধ্যে শেয়ার্ড মেমোরি বা শেয়ার্ড রিসোর্স অ্যাক্সেস (Where shared resources are accessed) করা হয়।
