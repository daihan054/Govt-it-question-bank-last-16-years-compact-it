# Bangladesh Bank — Assistant Director (ICT) 2026
# FINAL WRITTEN SUGGESTION

**Written 200 marks · 2 hours · IT 150 + Math 20 + English 30**
*200 marks in 120 minutes = 36 seconds per mark. A 20-mark question gets 12 minutes including the diagram.*

> **Basis of this sheet.** Compiled from 2,726 written + 2,781 MCQ questions across 581 exams in this bank — of which 477 written are from bank-sector papers and 11 from the last AD(ICT) paper (07.02.2025, DU). Star ratings come from *how many distinct exams* asked each subtopic, weighted by the 2025 paper. Every question in Section C is either an AD(ICT) 2025 original or a confirmed repeater in this bank.

### Star legend

| | Meaning |
|---|---|
| ★★★★★ | **Will come.** 6+ separate exams, or asked in AD(ICT) 2025. Must be answerable cold. |
| ★★★★ | Very high — 4–5 exams. |
| ★★★ | High — 2–3 exams. |
| ★★ | Read once. |
| ★ | Only if time remains. |

### Read the 2025 paper's shape before anything else

Eleven captured questions from AD(ICT) 2025 tell you the format precisely:

- **Seven IT questions ≈ 150 marks** → roughly **20 marks / 12 minutes each**
- **Every single IT question was either a calculation or a diagram.** Not one was "write an essay on X."
- **Banking context is deliberately woven in** — the schema is a bank schema, the firewall is Bangladesh Bank's, the probability question is about ADs and DDs.
- Math = **2 questions / 20 marks**, and unlike the MCQ it **includes calculus**.
- English = **2 questions / 30 marks** — one short note + one translation.
- **No Bangla in the written paper.** (IT 150 + Math 20 + English 30 = 200.) Prepare Bangla for the MCQ general portion only.

### ⚠ What the post merger changed here

AP (CSE) + AME (EEE/hardware) merged into AD(ICT). In the MCQ this surfaces as basic-electronics questions. In the **written** paper it surfaces as **infrastructure-flavoured IT** — firewall/server topology diagrams, RAID, data-centre and server hardware, HDD vs SSD selection, disk and cache maths. Do not read "merged post" as "learn circuit theory" — read it as **"be able to draw and justify a bank's IT infrastructure."**

---

# SECTION A — IT (150 marks): topic & subtopic star map

## A.1 Computer Networks — **16.4 % of all bank written questions, the largest single area** ★★★★★

| Subtopic | Stars | Evidence |
|---|---|---|
| **Subnetting & VLSM** | ★★★★★ | 10 exams, 12 questions — the most reliable written topic that exists |
| **Latency / throughput calculation** | ★★★★★ | AD(ICT) 2025 |
| **Email architecture & protocol steps** | ★★★★★ | AD(ICT) 2025 |
| OSI & TCP/IP model | ★★★★★ | 6 exams |
| Channel capacity — Nyquist & Shannon | ★★★★ | recurring, exact numbers repeat |
| Multiplexing — TDM/FDM/WDM + maths | ★★★★ | 7 exams |
| CRC & error detection | ★★★★ | |
| Well-known port numbers | ★★★★ | 3 exams |
| TCP vs UDP; 3-way handshake | ★★★★ | 3 exams |
| IPv4 vs IPv6, why no NAT in IPv6 | ★★★★ | 3 exams |
| Networking devices — hub/switch/router | ★★★★ | 2 exams, twice |
| MAC vs IP address | ★★★ | |
| NAT — need, advantages, topology diagram | ★★★ | |
| Routing — autonomous system, link-state vs distance-vector | ★★★ | |
| VLAN — static vs dynamic | ★★★ | |
| Synchronous vs asynchronous transmission | ★★★ | |
| Five components of a data communication system | ★★★ | |
| PCM, line coding, transmission media | ★★ | |

## A.2 Database — 10.9 % ★★★★★

| Subtopic | Stars | Evidence |
|---|---|---|
| **Normalization from a given schema + PK/FK + justification** | ★★★★★ | AD(ICT) 2025 — near-certain |
| **ER diagram from a described system** | ★★★★★ | 8 exams (bank, hospital, student, BPL, football) |
| SQL queries — GROUP BY, aggregate, join, nested | ★★★★★ | 9 exams, 12 questions |
| Keys — primary / candidate / super / foreign | ★★★★★ | 5 exams |
| Backup & disaster recovery | ★★★★ | 6 questions — very bank-relevant, easy marks |
| ACID & transaction management | ★★★★ | |
| DDL vs DML | ★★★★ | |
| Trigger, view, cursor | ★★★ | |
| Indexing & B+ tree | ★★★ | |
| DELETE vs TRUNCATE vs DROP | ★★★ | |

## A.3 Security — 6.7 % ★★★★★

| Subtopic | Stars | Evidence |
|---|---|---|
| **Firewall / DMZ topology diagram for a bank** | ★★★★★ | AD(ICT) 2025 — highest-probability diagram on the paper |
| **SQL injection & prevention** | ★★★★★ | 4 exams |
| **Hashing vs encryption** | ★★★★★ | 3 exams |
| **Two-factor authentication with example** | ★★★★★ | 3 exams |
| Attack types & countermeasures | ★★★★ | 7 exams |
| Digital signature — how it works via public key | ★★★★ | |
| HTTP vs HTTPS | ★★★★ | |
| Active vs passive attack | ★★★ | |
| CIA triad in a banking scenario | ★★★ | |
| Symmetric vs asymmetric, RSA, Caesar cipher | ★★★ | |
| IDS vs IPS, firewall types | ★★★ | |

## A.4 Operating System — 5.0 % ★★★★★

| Subtopic | Stars | Evidence |
|---|---|---|
| **Banker's algorithm — Need matrix + safe state** | ★★★★★ | AD(ICT) 2025; appears twice in this bank |
| **CPU scheduling + Gantt chart + AWT/ATAT** | ★★★★★ | 6 exams |
| Linux commands — permissions, hidden files, search | ★★★★★ | 3 exams |
| Deadlock — four conditions, prevention vs avoidance | ★★★★ | |
| Page replacement — FIFO/LRU/Optimal, page faults | ★★★★ | |
| Swapping; internal vs external fragmentation | ★★★★ | 2 exams |
| Thrashing; virtual vs physical memory | ★★★ | |
| Paging vs segmentation | ★★★ | |
| Semaphore, mutex, producer–consumer | ★★★ | |
| Multiprogramming vs multitasking vs multiprocessing | ★★★ | |

## A.5 C Programming — 4.2 %, **12 exams — most reliable non-network topic** ★★★★★

| Subtopic | Stars | Evidence |
|---|---|---|
| **Series-summation program** (eˣ, sin series, n/(n+1)(n+2)…) | ★★★★★ | 4 exams |
| Prime / Armstrong / even-odd / factorial programs | ★★★★★ | 4 exams |
| String reverse without library function | ★★★★ | 2 exams |
| Pattern printing | ★★★★ | |
| Call by value vs call by reference | ★★★★ | 2 exams |
| Array vs structure | ★★★ | |
| Recursion (factorial, Fibonacci) | ★★★ | |
| File handling | ★★★ | |
| Pointers & dynamic memory (malloc/calloc/realloc) | ★★★ | |

## A.6 Algorithm — 4.4 % ★★★★

| Subtopic | Stars | Evidence |
|---|---|---|
| **Min/Max Heap construction from given values** | ★★★★★ | AD(ICT) 2025 |
| **Kruskal's MST from a given graph** | ★★★★★ | 3 exams, asked repeatedly |
| Dijkstra / shortest path | ★★★★ | 2 exams |
| BFS & DFS traversal from a figure | ★★★★ | 2 exams |
| Time & space complexity analysis | ★★★★ | |
| Greedy vs DP vs divide-and-conquer | ★★★ | |
| Huffman coding | ★★★ | |
| Recurrence relations & Master theorem | ★★★ | |
| 0/1 vs fractional knapsack | ★★★ | |

## A.7 Microprocessor & Architecture — 4.4 % ★★★★

| Subtopic | Stars | Evidence |
|---|---|---|
| **RAID levels — which is best for a core banking DB, and why** | ★★★★★ | 5 questions, 4 exams |
| **Direct-mapped cache sizing** (tag/index/offset bits) | ★★★★ | asked twice with identical numbers |
| Cache memory vs main memory | ★★★★ | 2 exams |
| Disk-pack capacity calculation | ★★★★ | |
| HDD vs SSD for a banking workload | ★★★★ | |
| Microprocessor vs microcontroller | ★★★★ | 3 exams |
| Pipelining — why multi-stage over single-cycle | ★★★ | |
| 8086 architecture, EU/BIU, addressing modes | ★★★ | |
| RISC vs CISC | ★★★ | |
| Optical disk read/write | ★★ | |

## A.8 Software Engineering — 5.0 % ★★★★

| Subtopic | Stars | Evidence |
|---|---|---|
| **Black box vs white box testing** | ★★★★★ | **7 exams — the most repeated written IT question in this bank** |
| SDLC models & when to use each | ★★★★★ | 8 questions |
| UML — use case / class diagram from a scenario | ★★★★ | *usually described, not named — recognise it* |
| MVC framework & advantages | ★★★★ | 2 exams |
| Verification vs validation | ★★★ | |
| DFD | ★★★ | |
| Coupling & cohesion | ★★ | |

## A.9 Data Structure — 3.1 % ★★★★

| Subtopic | Stars | Evidence |
|---|---|---|
| Stack vs Queue difference | ★★★★ | 2 exams |
| Balanced parentheses program | ★★★★ | 2 exams |
| Tree traversal & reconstruction from two orders | ★★★★ | |
| Circular vs linear queue | ★★★ | |
| Tree terminology (leaf, internal node, height) | ★★★ | |
| Infix → postfix conversion | ★★★ | |
| Linked list operations | ★★★ | |

## A.10 DLD — 2.5 % ★★★★

| Subtopic | Stars | Evidence |
|---|---|---|
| **K-map simplification with grid, loops & SOP** | ★★★★★ | 2024 + 2025 |
| **Truth table from a Boolean expression** | ★★★★★ | AD(ICT) 2025 |
| Full adder design + truth table | ★★★★ | |
| Why NAND is a universal gate | ★★★★ | 2 exams |
| Logic circuit output for given inputs | ★★★★ | 2 exams |
| MUX / decoder / 7-segment display | ★★★ | |
| D latch vs D flip-flop | ★★★ | 2 exams |

## A.11 Others

| Topic | Stars | Key items |
|---|---|---|
| Compiler & TOC | ★★★★ | **Compiler vs interpreter + phases of a compiler — 5 exams**; regular expressions; CFG ambiguity |
| Cloud | ★★★★ | Service-model selection for a scenario with 2 examples; VM vs container; Docker; edge computing |
| Computer Fundamentals / Infrastructure | ★★★ | Server hardware, data-centre power & cooling, UPS, DR site design |
| OOP theory | ★★★ | Overloading vs overriding, inheritance, polymorphism, abstraction |
| AI/ML | ★★★ | **Supervised vs unsupervised — 3 exams**; ML vs DL; agent types |
| Web Technology | ★★ | HTML table code, cookies, HTTP methods, REST |

---

# SECTION B — General (50 marks)

## B.1 Math — 20 marks (2 questions)

| Subtopic | Stars | Evidence |
|---|---|---|
| **Integration / calculus** | ★★★★★ | AD(ICT) 2025 |
| **Probability** | ★★★★★ | AD(ICT) 2025 |
| Geometry & coordinate geometry | ★★★★ | 5 questions |
| Algebra (x + 1/x type) | ★★★★ | 2 exams, identical |
| Percentage, profit & loss, SI/CI | ★★★★ | 4 questions |
| Ratio, proportion & mixture | ★★★ | |
| Set theory / Venn | ★★★ | |
| Speed, time, distance, boats | ★★★ | |

**Prepare the 2025 pair first — one integration + one probability — then geometry, interest and Venn as backup.**

## B.2 English — 30 marks (2 questions)

| Subtopic | Stars |
|---|---|
| **Focus writing / short note, 100–200 words** | ★★★★★ (19 exams) |
| **Translation both directions** | ★★★★★ (15 exams each — the single most repeated written item in this bank) |
| Reading comprehension | ★★★ (4 exams) |
| Letter / application writing | ★★ |

---

# SECTION C — QUESTION LIST

✅ = AD(ICT) 2025 original · 🔁×n = confirmed repeater across n exams

## C.1 The AD(ICT) 2025 paper — sit this first

1. ✅ **Construction of Min Heap** from: 12, 29, 33, 56, 66, 99, 100, 344
2. ✅ **Banker's Algorithm** — 5 processes P₀–P₄; 3 resource types A(10), B(5), C(7); snapshot at T₀. (a) Need matrix (Need = Max − Allocation) (b) Is the system in a safe state?
3. ✅ **Total latency** for a 3-kbyte e-mail: bandwidth 1 Gbps, distance 300 km, light 2×10⁸ m/s, RTT 50 ms, queuing time 5 ms
4. ✅ Sinthia sends an e-mail to Afsana through the application and transport layers. (a) Name the application- and transport-layer protocols (b) Write the steps of mail transfer
5. ✅ **Bank schema normalization** — `Bank(Br_Name, Br_City, Assets, Acc_name, Acc_Num, Balance)`. (a) Normalize it and identify Primary and Foreign keys (b) Show the schema and justify why it is in good form
6. ✅ **Firewall diagram** — Bangladesh Bank has a client–server setup communicating with a Mail Server, DNS server and Web server. Draw a diagram securing those servers with a firewall
7. ✅ **Truth table** for `Ā·B̄·(A+B)‾·C`
8. ✅ Evaluate **∫₀² (2x² + 3x) dx**
9. ✅ **Probability** — 6 ADs each bring a bag; only half of the 4 DDs bring a bag. A bag is chosen at random. What is the probability it belongs to a DD?
10. ✅ **Short note (100–150 words):** "The role of AI and machine language to mitigate challenges of cyber attack on banking system"
11. ✅ **Bengali → English:** (a) শনিবার হতে সে অফিসে আসছে না। (b) আপনার ব্যাংক একাউন্ট এর স্থিতি জানার জন্য মোবাইল ব্যাংকিং এপ্লিকেশন এ লগইন করুন

## C.2 Networks — near-certain

12. 🔁×4 Given IP **192.168.1.50**, subnet mask **255.255.255.240** — find valid host IP range, network address and broadcast address
13. 🔁×3 Divide **192.168.10.0/24** into 4 equal subnets — bits borrowed, new subnet mask, and network / first-usable / broadcast for each
14. 🔁×2 **192.168.0.0/28** — network address, broadcast address, first and last usable IP
15. 🔁×2 **192.168.10.0/23** — (i) how many usable addresses (ii) subnet mask (iii) broadcast address
16. 🔁×2 **172.18.10.0/23** — divide into 4 subnets; give each subnet address, start address, subnet mask, broadcast
17. 🔁×2 **172.16.128.120/25** — network address, valid hosts, subnet mask, broadcast address
18. 🔁×2 `14.24.74.0/24` into Subnet A (120 addresses) and Subnet B (60 addresses), allocated largest-first — network address with CIDR and broadcast for both
19. 🔁×2 Write the **private IP ranges** for Class A, B and C
20. 🔁×2 What is a subnet and subnet mask? `172.16.0.0/19` gives how many subnets and hosts? What is the function of OSPF?
21. 🔁×2 A telephone line has bandwidth **3000 Hz (300–3300 Hz)**, SNR **3162** — find the channel capacity *(Shannon)*
22. 🔁×2 **Five channels** of 100 kHz each are multiplexed with a **10 kHz guard band** between them — minimum link bandwidth?
23. 🔁 TDM: rate 1.536 Mbps, message 960,000 bits, slot 32, circuit-switch setup 800 ms — total transfer time
24. 🔁 Two channels at 190 kbps and 180 kbps multiplexed with pulse-stuffing TDM, no sync bits — frame rate and output bit rate
25. 🔁 **CRC** — data **11100**, divisor **1001**: find the transmitted frame and verify at the receiver
26. 🔁×3 **What is the port number of DNS?** (and the well-known port table)
27. 🔁×3 What is the **TCP/IP model**? Explain it briefly. Compare with OSI
28. 🔁×2 Write down the **OSI model** and the function of each layer
29. 🔁×3 **Difference between IPv4 and IPv6.** How many bits in each? Why is NAT not required in IPv6?
30. 🔁×3 **3-way handshake** for TCP connection, with diagram
31. 🔁×2 **Distinguish between TCP and UDP**
32. 🔁×2 **Difference between MAC address and IP address**
33. 🔁×2 **Difference among Hub, Switch and Router** *(also asked as Hub vs Switch alone)*
34. 🔁×2 What is **VLAN**? Difference between static and dynamic VLAN
35. 🔁×2 Why do we need **NAT**? Its advantages, with a topology diagram
36. 🔁×2 What is an **Autonomous System**? Link-state vs distance-vector routing protocols
37. 🔁×2 **Synchronous vs asynchronous** transmission
38. 🔁×2 Name and define the **five components of a data communication system**, with diagram

## C.3 Database — near-certain

39. 🔁×3 Define **primary key, super key and candidate key** *(also asked as primary/candidate/foreign)*
40. 🔁×2 Draw an **ER diagram of a Banking Management System** ("SKY Bank Ltd.") — **prepare this one specifically**
41. 🔁×2 Draw an **ER diagram of a Hospital Management System** ("SKY Hospital Ltd.")
42. 🔁 Draw an ER diagram for a **Student database** (Student, Course, Report, Registration, Staff)
43. 🔁 Draw an ER diagram from a **football-game scenario** (Game, Team, Referee)
44. 🔁×2 **DDL vs DML** difference
45. 🔁×2 Write **SQL to find duplicate names** in an employee table
46. 🔁×2 `Employee(EmpID, Name, Department, Salary)` — SQL for department, employee count and average salary, one row per department
47. 🔁×2 Explain **database trigger** with an example
48. 🔁 What is **normalization**? Explain 1NF, 2NF, 3NF with examples
49. 🔁 **Backup types** (full / incremental / differential), RPO & RTO, hot vs cold site
50. 🔁 **DELETE vs TRUNCATE vs DROP**; advantages of a DBMS over a file system; view / cursor / trigger

## C.4 Security — near-certain

51. 🔁×4 What is **SQL injection**? How can you prevent SQL injection attacks?
52. 🔁×3 **Difference between hashing and encryption**
53. 🔁×3 What is **2-factor authentication**? Describe with an example
54. 🔁×2 **Difference between HTTP and HTTPS**
55. 🔁×2 **Active vs passive attack**
56. 🔁 Explain how a **digital signature** works using public-key encryption — draw the flow
57. 🔁 Types of **cyber attack** — phishing, ransomware, MITM, DoS vs DDoS — with countermeasures
58. 🔁 **CIA triad** applied to a banking scenario
59. 🔁 **Caesar cipher** / symmetric-key problem; RSA worked example
60. 🔁 Firewall types (packet filter, stateful, proxy, NGFW); **IDS vs IPS**

## C.5 Operating System — near-certain

61. 🔁×2 **Banker's algorithm** with 5 processes and 3 resource types — Need matrix and safety sequence
62. 🔁 Five jobs A–E arrive together with running times 10, 6, 2, 4, 8 min and given priorities — schedule and compute
63. 🔁 Processes P1–P4 arriving at time 0 with given burst times — **average waiting time and turnaround time** using FCFS and SJF, with Gantt chart
64. 🔁 Page reference string **1, 3, 0, 3, 5, 6, 3** with 3 frames — number of page faults (FIFO / LRU / Optimal)
65. 🔁×2 What is **swapping**? Difference between internal and external fragmentation
66. 🔁 Necessary conditions for **deadlock**. Can deadlock occur with a single process?
67. 🔁 Explain **thrashing** — how it arises in demand paging and its effect on CPU utilization
68. 🔁×2 **Linux commands:** list all hidden files, remove a file, change file permission, search for a string
69. 🔁 Write a shell command to create folder 'A' with read-only permission; copy all contents of 'A' into 'P'
70. 🔁 **Physical vs virtual memory**; advantages and disadvantages of virtual memory

## C.6 C Programming — near-certain

71. 🔁×4 Write a program for the series **eˣ = 1 + x/1 + x²/2! + x³/3! + …**
72. 🔁 Write a C program for **x − x³/3 + x⁵/5 − …**
73. 🔁 Write a C/C++ program for **1/(2×3) + 2/(3×4) + 3/(4×5) + …** up to n terms
74. 🔁×2 Write a program to check an **Armstrong number**
75. 🔁×2 Write a C program to find **prime numbers from 1 to n**
76. 🔁×2 Write a C program to check whether a number is **even or odd**
77. 🔁×2 Write a program to **reverse a string without using a library function**
78. 🔁×2 Write a C program to print the given **pattern**
79. 🔁×2 **Call by value vs call by reference**
80. 🔁×2 **Difference between array and structure**
81. 🔁×2 Write a C/C++ program to check **balanced parentheses** in an expression

## C.7 Algorithm & Data Structure

82. 🔁×3 Find the **Minimum Spanning Tree** of the given graph using **Kruskal's algorithm**
83. 🔁×2 **Dijkstra's shortest path** algorithm on a given graph
84. 🔁×2 Give the **BFS and DFS** sequences for the tree/graph in the figure
85. 🔁×2 **Stack vs Queue** difference
86. 🔁 Why is a **circular queue** preferred over a linear queue in operating systems? Give one example
87. 🔁 Define **tree, leaf node, internal node, height of a tree** with an example
88. 🔁 An array holds one million **sorted** integers — which search algorithm and why?
89. 🔁 Cost of inserting a new item into an existing **binary max-heap**
90. 🔁 **Time and space complexity** analysis; recurrence relations

## C.8 Architecture, DLD, SE, Compiler, Cloud, AI

91. 🔁×4 **RAID** — what is it, which level is best and why, its relevance in a database / data-centre server
92. 🔁×2 How many total bits for a **direct-mapped cache** with 16 KB data and 4-word blocks, 32-bit address? Find tag, index and offset field sizes
93. 🔁×2 **Cache memory** — what it is, and how it differs from main memory
94. 🔁 Disk pack: 16 surfaces, 128 tracks/surface, 256 sectors/track, 512 bytes/sector — capacity calculations
95. 🔁 Compare **HDD vs SSD** for Server A (core banking database) and Server B (10-year immutable archive)
96. 🔁×3 **Microprocessor vs microcontroller** (also asked as hardware-level differences)
97. 🔁 Why do modern processors favour a **multi-stage pipeline** over a single-cycle implementation?
98. 🔁×2 Simplify with a **4-variable K-map**: F(A,B,C,D) = Σm(0,3,5,7,8,10,11,12,13,14,15) — draw the grid, show the loops, write the SOP
99. 🔁 Simplify F = ĀB̄C̄ + AB̄C̄ + ĀB̄C + ĀBC + ABC using K-map, and draw the logic circuit
100. 🔁×2 **Why is NAND a universal gate?**
101. 🔁×2 Logic circuit Q = C̄ + ĀB + (BC(B+C))‾ — find output Q when (A,B,C) = (0,0,1)
102. 🔁 Design a **full adder** with basic gates — truth table, Sum and Carry expressions, complete circuit
103. 🔁×2 What is a **multiplexer**? Difference between D latch and D flip-flop
104. 🔁 **7-segment display** — draw the 2-to-4 line decoder / de-multiplexer logic circuit
105. 🔁×7 **What is software testing? Difference between black box and white box testing** ← *most repeated written IT question in this bank*
106. 🔁 **SDLC models** — describe and state when each is used
107. 🔁×2 What is the **MVC framework**? Write its advantages
108. 🔁 Draw a **use-case / class diagram** for the described banking scenario
109. 🔁×5 **Difference between compiler and interpreter.** Write the phases of a compiler
110. 🔁×2 Regular expression for the given binary-string language
111. 🔁×3 **Difference between supervised and unsupervised learning**, with examples
112. 🔁×2 Cloud service-model selection for a described startup — IaaS, PaaS or SaaS, with two real platform examples
113. 🔁×2 **Edge computing** — present the concept briefly; VM vs container

## C.9 Math

114. ✅ ∫₀² (2x² + 3x) dx
115. ✅ Probability — the AD/DD bag problem
116. 🔁×2 If **x + 1/x = 4**, find x² + 1/x²
117. 🔁 Simple and compound interest on a bank deposit
118. 🔁 Three-set **Venn diagram** problem
119. 🔁 Coordinate geometry — distance, straight line, triangle/circle area
120. 🔁 Boats and streams; time, work and distance

## C.10 English — 30 marks

**Focus writing / short note.** Across 35 past prompts the theme is consistently *technology × banking × Bangladesh development*. Actual recent prompts: "The role of AI and machine language mitigate challenges of cyber attack on banking system" (AD(ICT) 2025) · "The Importance of Digital Literacy in Expanding Cashless Transactions in Bangladesh" · "The Role of Sustainable Banking in Achieving the UN SDGs in Bangladesh" · "Growing use of technology in the Financial Service Industry" · "Digital Financial Literacy" · "Blockchain technology" · "Edge Computing".

**Prepare these seven skeletons — one will fit whatever comes:**

| ★ | Predicted 2026 topic |
|---|---|
| ★★★★★ | AI / GenAI in banking — opportunity and risk |
| ★★★★★ | Cybersecurity and fraud prevention in digital banking |
| ★★★★★ | Cashless Bangladesh, **Bangla QR** and interoperable digital payments |
| ★★★★ | Fourth Industrial Revolution and the banking workforce |
| ★★★★ | CBDC / digital currency, or open banking |
| ★★★ | Financial inclusion through MFS and agent banking |
| ★★★ | Climate finance / green banking and LDC graduation |

Use one reusable structure: **definition → Bangladesh context (name a real initiative) → three benefits → two risks → two recommendations → conclusion.**

**Translation** — 🔁×15 each direction, the most repeated written item in the bank. Sentences are short and banking-flavoured. Drill this vocabulary both ways: account balance, deposit, withdrawal, remittance, interest rate, loan disbursement, branch, transaction, mobile banking application, login, fund transfer, statement, foreign exchange reserve.

---

# SECTION D — Diagrams to rehearse (under 4 minutes each)

| ★ | Diagram |
|---|---|
| ★★★★★ | **Bank network with firewall + DMZ** (Mail, DNS, Web servers) |
| ★★★★★ | **ER diagram for a banking system** |
| ★★★★★ | **Gantt chart** + AWT/ATAT table |
| ★★★★★ | **Min/max heap** built step by step |
| ★★★★ | **E-mail flow** sender → MTA → MTA → receiver, with protocol labels |
| ★★★★ | **K-map grid** with loops drawn and SOP written |
| ★★★★ | **Full adder** circuit with truth table |
| ★★★ | **Process state diagram** |
| ★★★ | **Use-case diagram** for a banking scenario |
| ★★★ | **OSI seven layers** with one protocol each |
| ★★★ | **TCP 3-way handshake** |
| ★★★ | **NAT topology** |

---

# SECTION E — Time strategy (120 minutes)

| Phase | Min | What |
|---|---|---|
| Read the whole paper, pick your order | 4 | decide before writing a word |
| English (short note + translation) — 30 | 22 | do it early while your hand is fresh |
| Math — 20 | 12 | fast, self-contained, fully scoreable |
| Your 4 strongest IT questions — ~80 | 45 | diagram first, then explanation |
| Remaining 3 IT questions — ~70 | 32 | write the formula and setup even if unfinished |
| Review, label diagrams, number answers | 5 | |

**What actually earns marks on these papers:**

- **Draw the diagram first, write around it.** An unlabelled diagram scores little; a labelled diagram with three lines of explanation scores nearly full.
- **Write the formula before substituting numbers.** In latency and Shannon questions the formula itself carries marks.
- **Never leave a numeric question blank** — known values + formula + approach earns generous partial credit.
- **Answer in the banking context when offered.** If the schema is a bank schema, name real banking entities. Examiners visibly reward it.

---

### Coverage note

This sheet is built to cover the paper's topic surface, not to predict exact wording. Two honest limits: only **11 questions** from the 2025 written paper are captured here — enough to fix the *format* (computation-and-diagram driven, banking-contextualised, ~20 marks per IT question) but not enough to pin specific topics, which is why Section A's stars rest on 477 questions across many exams rather than on 2025 alone; and the **2026 conducting body is unconfirmed** — 2025 was DU, and if BUET conducts it, promote cache sizing, pipelining, disk maths and Linux commands into Tier ★★★★★.
