# Theory Clustering Progress

Tracks the subtopic → theory grouping decisions for the RULE 1b task in CLAUDE.md, so the
identical grouping can be replayed across `all-questions/written/`, `written-answers/`,
`all-questions/mcq/` and `mcq-answers/` without re-deriving it each time.

Order of work (per user instruction): 1) all-questions/written  2) written-answers
3) all-questions/mcq  4) mcq-answers  5) all-theories-with-previous-questions-attached
(step 5 is a content-sync check only, NOT a clustering task).

Workflow per subtopic: extract question blocks by exact byte slice from source (never retype
Bengali/long text), reassemble under `###` groups via `cluster_lib.py` (`extract_blocks` +
`build_section`), verify content-multiset match against `git show HEAD:<path>`, rebuild TOC via
`rebuild_toc.py` (check then build), verify TOC anchors resolve, commit+push.

Reusable scripts live in the scratchpad dir: `cluster_lib.py`, `rebuild_toc.py`,
`find_dup_ranges2.py` (from an earlier task, may still be useful).

Status legend: DONE = subtopic reorganized + TOC rebuilt + verified + committed (in
all-questions/written/ so far). NO SPLIT = subtopic is already single-theme, left flat.
PENDING = split decided (by analysis agent) but not yet applied to any file.

## Folder 1: all-questions/written/ — ALL 24 FILES DONE ✓

Every file in `all-questions/written/` has been reorganized (or confirmed to need no change),
TOC rebuilt to nested bullet format, content-multiset verified against git HEAD before each
change, anchors verified, and committed+pushed individually:
ai-and-ml.md, algorithm.md, bangla.md, c-programming.md (no split needed), cloud-computing.md
(no split needed), compiler-and-toc.md (no split needed), computer-fundamental.md,
computer-network-security.md, computer-networks.md, data-structure.md, database.md, dld.md,
electrical-and-electronics.md, english.md (no split needed), gk.md, image-processing.md (no
split needed), math.md, microprocessor-and-computer-architecture.md, ms-office.md (no split
needed), oop.md, operating-system.md, programming-languages.md, software-engineering.md,
web-technology.md.

## Folder 2: written-answers/ — ALL 24 FILES DONE ✓

Replayed the identical Folder-1 groupings onto every written-answers/*.md file (18 files
actually needed the split applied; the other 6 — c-programming.md, cloud-computing.md,
compiler-and-toc.md, english.md, image-processing.md, ms-office.md — needed zero changes since
every one of their subtopics was NO SPLIT in Folder 1 too).

IMPORTANT BUG FOUND & FIXED while doing this folder: `extract_blocks` originally discarded any
non-blank "preamble" text sitting between a `##` heading and its first numbered question (e.g.
computer-networks.md's OSI section had `> Best Tutorial: [GeeksforGeeks ...]` right after the
heading, before Q1). This was caught by the mandatory content-multiset check (git HEAD vs new
file) after processing computer-networks.md — do NOT skip that check on any future file.
`cluster_lib.py`'s `extract_blocks` now takes `allow_preamble=True` and returns `(blocks,
preamble)`; `build_section` takes an optional `preamble=` list and re-inserts it right after the
`##` heading, before any `###` theme heading. ALWAYS call `extract_blocks(..., allow_preamble=True)`
and thread the returned preamble into `build_section(..., preamble=preamble)` going forward — the
default (allow_preamble=False) now raises loudly instead of silently dropping content, which is a
useful safety net but should not be relied on in place of the content-multiset check.

NEXT STEP: Folder 3 (all-questions/mcq/) — this needs a FRESH clustering analysis (different
file, different subtopic structure from written/). Same method: per-file, per-subtopic, decide
NO SPLIT vs SPLIT with theme names + original question numbers, then apply with
extract_blocks/build_section + rebuild_toc.py, verifying content-multiset match every time.
After mcq/ is fully done, replay its exact grouping onto mcq-answers/ (Folder 4), the same way
Folder 1's plan was replayed onto Folder 2.

---

## DETAILED PLANS (theme name — original 1-indexed question numbers within that subtopic)

### ai-and-ml.md — DONE
- Artificial Intelligence & Machine Learning (23) — SPLIT (applied):
  - Cybersecurity & Information Security (6): 4,5,10,15,16,17
  - Machine Learning Concepts (4): 1,2,3,6
  - Mathematics & Aptitude (3): 8,19,23
  - Writing & Composition (3): 9,13,20
  - Software Engineering & Programming Concepts (2): 7,18
  - Algorithms & Problem Solving (2): 12,22
  - Database Concepts (1): 11
  - General Knowledge & Trivia (1): 14
  - Digital Communication & Modulation (1): 21
- All other 11 subtopics — NO SPLIT

### algorithm.md — DONE
- Searching & Graph Algorithms (6) — SPLIT (applied):
  - Graph Algorithms (MST) (1): 1
  - Searching Algorithms (1): 2
  - Number Theory Programs (Prime Numbers) (2): 3,5
  - General Knowledge (1): 4
  - Binary Search Tree Construction (1): 6
- All other 14 subtopics — NO SPLIT

### oop.md — DONE
- Java Programming & Methods (18) — SPLIT (applied):
  - Java/C# Coding Exercises (11): 1,2,5,6,7,9,10,11,14,16,17
  - Java Platform Concepts (JVM/JDK/JRE/GC) (7): 3,4,8,12,13,15,18
- OOP Concepts (Inheritance, Polymorphism, Encapsulation) (11) — SPLIT (applied):
  - OOP Concepts (Polymorphism, Inheritance, Friend Function) (5): 1,4,6,9,10
  - Basic Programming (Loops & Series) (3): 2,5,8
  - Math & Aptitude Problems (2): 7,11
  - General English Essay (1): 3
- All other 7 subtopics — NO SPLIT

### operating-system.md — DONE
- OS Concepts & Process Management (7) — SPLIT (applied):
  - Process States & Multithreading (3): 1,3,6
  - Hardware & Microprocessor Comparisons (3): 2,5,7
  - Software Engineering Challenges (1): 4
- All other 13 subtopics — NO SPLIT

### programming-languages.md — DONE
- Core Programming Languages (7) — SPLIT (applied):
  - Programming Exercise (Leap Year) (1): 1
  - AI Search Algorithms (1): 2
  - Sustainable Development Goals (SDG) (2): 3,6
  - RSA Algorithm & Cryptography (1): 4
  - English Grammar Correction (1): 5
  - OS Page Replacement (LRU) (1): 7
- Visual Basic & .NET (6) — NO SPLIT

### software-engineering.md — DONE
- Software Project Management & Organization (9) — SPLIT (applied):
  - Project Management & Team Leadership (7): 1,2,3,4,5,8,9
  - Version Control & Software Maintenance (2): 6,7
- Software Design Principles (Coupling & Cohesion) (5) — SPLIT (applied):
  - Software Design Principles (4): 1,2,3,4
  - UI Design Mistakes (1): 5
- All other 12 subtopics — NO SPLIT

### web-technology.md — DONE
- HTML & Web Fundamentals (32) — SPLIT (applied):
  - HTML & Web Fundamentals (30): 1-30
  - Web Services (SOAP vs REST) (1): 31
  - General English Translation (1): 32
- All other 6 subtopics — NO SPLIT

---

### bangla.md — PLAN READY, NOT APPLIED
- বাংলা ব্যাকরণ ও সাহিত্য (61) — SPLIT:
  - বাংলা ব্যাকরণ (Bangla Grammar) (49): 1,2,3,4,5,6,7,9,10,11,12,13,14,17,18,19,20,22,23,24,25,26,28,29,30,31,32,33,34,35,37,38,39,41,42,43,44,45,49,50,51,52,53,54,55,56,57,58,60
  - বাংলা সাহিত্য (Bangla Literature) (12): 8,15,16,21,27,36,40,46,47,48,59,61
- Focus Writing (41) — SPLIT:
  - Essay & Composition Writing (29): 1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,28,29,39
  - General Knowledge (Bangladesh Facts) (8): 32,33,34,35,36,37,38,40
  - Reading Comprehension (Bangla Passage) (2): 30,31
  - Translation (2): 27,41
- Translation (19), পত্র লিখন (7), সারমর্ম / সারাংশ (6), এক কথায় প্রকাশ (One Word Substitution) (5) — NO SPLIT
NOTE: theme names with Bengali text must be copied byte-exact from the source file when applying
(extract via script, do not retype) to avoid Unicode-normalization drift.

### computer-fundamental.md — PLAN READY, NOT APPLIED
- Computer Fundamentals & Acronyms (114) — SPLIT:
  - Computer Fundamentals & Acronyms (80): 1-60,66,67,81,84,85,90,91,92,93,95,96,97,98,99,100,101,102,103,104,113
  - Bangla Language (Grammar & Vocabulary) (8): 61,62,69,70,86,106,107,114
  - English Language (Grammar & Usage) (11): 63,64,65,71,72,73,74,75,108,109,110
  - Mathematics & Aptitude (7): 82,83,87,88,94,111,112
  - General Knowledge (Bangladesh & World) (8): 68,76,77,78,79,80,89,105
  (80+8+11+7+8 = 114 ✓ — VERIFY the "80" list count sums correctly before applying: listed
  numbers 1-60 (60) + 66,67 (2) + 81 (1) + 84,85 (2) + 90-93 (4) + 95 (1) + 96-104 (9) + 113 (1)
  = 60+2+1+2+4+1+9+1 = 80 ✓)
- All other 9 subtopics — NO SPLIT

### computer-network-security.md — PLAN READY, NOT APPLIED (15 subtopics total)
- Social Engineering & Cyber Attacks (32) — SPLIT:
  - Network & Infrastructure Attacks (MITM, Spoofing, DoS/DDoS, MAC/DNS/DHCP attacks) (19): 2,3,4,5,7,13,14,15,16,17,19,20,22,24,25,28,29,31,32
  - Social Engineering Attacks (Phishing & Pharming) (4): 1,6,21,23
  - Cyber Attack Overview & Classification (9): 8,9,10,11,12,18,26,27,30
- Authentication & Access Control (16) — SPLIT:
  - Two-Factor / Multi-Factor Authentication (8): 1,2,4,6,8,9,13,16
  - Digital Signatures & Certificates (6): 3,7,10,11,12,14
  - Other (LDAP, Password Protection) (2): 5,15
- Cryptography & Network Security (14) — SPLIT:
  - Cryptography & Network Security Core (5): 1,3,6,8,13
  - Operating System Questions (Misplaced) (2): 4,7
  - Software Release Security Practices (1): 11
  - GK / English Essay Questions (Off-topic) (6): 2,5,9,10,12,14
- Cryptography (31), Firewalls & Network Defense (20), Malware & Security Threats (20),
  Web Security Vulnerabilities (19), Security Protocols (SSL/TLS, HTTPS) (12), Cyber Crime &
  Security (10), Security Principles (CIA Triad) (8), VPN & Tunneling Protocols (IPsec, SSL VPN)
  (6), Critical Information Infrastructure (CII) & Cyber Governance (3), Cryptography & Network
  Security Scenarios (3), Email & Messaging Security (Spam, Phishing) (3), Buffer Overflow &
  Software Vulnerabilities (1) — NO SPLIT

### computer-networks.md — PLAN READY, NOT APPLIED (33 subtopics total, LARGE)
- Subnetting & IP Addressing (119) — SPLIT:
  - Subnetting & CIDR Calculations (80): 1,2,3,4,6,7,8,9,10,11,12,13,15,16,17,18,20,22,25,26,30,31,35,36,39,41,42,44,48,50,51,52,54,56,57,58,60,63,64,66,67,68,69,70,71,73,74,75,76,77,78,79,80,81,82,83,86,87,88,91,92,93,94,95,98,101,102,103,104,105,106,107,109,110,111,113,115,116,118,119
  - IP Address Classes & Public/Private Ranges (28): 5,14,19,21,23,24,29,32,33,37,40,43,45,46,47,49,53,55,59,62,65,89,96,97,100,108,114,117
  - IP Addressing Fundamentals & Special Addresses (11): 27,28,34,38,61,72,84,85,90,99,112
- OSI & TCP/IP Reference Model (57) — SPLIT (the user's own example case):
  - OSI Model (29): 1,2,3,4,5,9,10,11,12,15,18,20,22,23,24,25,27,29,32,33,34,36,40,41,44,46,47,50,51
  - TCP/IP Model (12): 6,7,8,13,14,16,26,28,38,39,43,45
  - OSI vs TCP/IP Comparison (7): 17,19,30,37,42,48,52
  - Networking Protocols & PDU Concepts (4): 21,31,35,49
  - Off-topic / Misplaced Content (5): 53,54,55,56,57
- Networking Devices (24) — SPLIT:
  - Networking Devices (Hub, Switch, Router, Bridge, Gateway) (19): 1-19
  - Network Topology (1): 24
  - Off-topic / Misplaced (4): 20,21,22,23
- Physical Layer & Transmission Media (Cables & Wiring) (21) — SPLIT:
  - Physical Layer & Transmission Media (15): 1-15
  - Off-topic / Misplaced (6): 16,17,18,19,20,21
- Multiplexing & Bandwidth (19) — SPLIT:
  - Multiplexing & Bandwidth Calculations (18): 1-18
  - Off-topic Math Problem (1): 19
- Routing Protocols & Route Configuration (19) — SPLIT:
  - Routing Protocols & Route Configuration (18): 1-18
  - Off-topic Math Problem (1): 19
- Network Address Translation (NAT) (17) — SPLIT:
  - NAT & PAT (13): 1-13
  - Off-topic (English/GK/math) (4): 14,15,16,17
- Networking Fundamentals & Terminology (32), Application Layer Protocols & Troubleshooting
  (DNS, DHCP, HTTPS) (23), Transport Layer (TCP & UDP) (22), Wireless Networks & IoT (mmWave)
  (19), Communication System & Transmission Modes (17), Data Rate & Channel Capacity (Nyquist,
  Shannon) (16), Error Detection & Data Communication (CRC, Throughput) (14), Network Topologies
  (14), IPv6 Addressing (13), Physical Layer & Optical Fiber (Attenuation & Power Budget) (13),
  Flow Control & Data Link Layer (Stop-and-Wait) (12), Network Services (DHCP, NAT) (11), Digital
  Modulation & Signal Processing (BPSK, QPSK) (10), Email Architecture & Protocols (SMTP, POP3,
  IMAP) (10), Application Layer & Well-Known Port Numbers (6), Pulse Code Modulation (PCM) &
  Signal Processing (6), Switching Techniques (Circuit vs Packet Switching) (5), WAN Technologies
  (SONET/SDH, ATM, WDM) (5), Network Layer (Packet Fragmentation & Tunneling) (4), Satellite
  Communication (4), Analog Modulation & Radio Receivers (3), Spread Spectrum & Multiple Access
  (CDMA, FHSS, DSSS) (3), Line Coding & Digital Encoding (2), Address Resolution (ARP & RARP)
  (2), VLANs & Subnetting Comparison (2), High Availability & Redundancy Protocols (VRRP, HSRP)
  (1) — NO SPLIT

### data-structure.md — PLAN READY, NOT APPLIED
- Stack (20) — SPLIT:
  - Stack Operations & Expression Conversion (15): 1,2,3,5,8,9,10,13,14,15,16,17,18,19,20
  - Stack vs Queue / LIFO vs FIFO Comparison (5): 4,6,7,11,12
- Linked List (15) — SPLIT:
  - Linked List Fundamentals & Operations (9): 1,2,3,5,7,10,13,14,15
  - Array vs Linked List Comparison (6): 4,6,8,9,11,12
- Tree (27), Binary Search Tree (BST) (9), Priority Queues & Heaps (Min/Max Heap) (8), Hashing &
  Hash Tables (7), Queue (6), Data Structure Fundamentals (6), Tree Data Structures (BST, AVL,
  B-Tree, Heaps) (2), Linear Data Structures (Arrays, Stacks, Queues, Linked Lists) (2) — NO SPLIT

### database.md — PLAN READY, NOT APPLIED (20 subtopics total)
- SQL Queries (95) — SPLIT:
  - SQL Query Writing Practice (82): 1,2,3,4,5,6,7,8,9,10,12,13,14,15,16,17,18,19,20,21,24,25,26,27,29,32,33,34,35,36,38,39,40,41,42,43,44,45,46,48,51,52,53,54,55,56,58,59,60,61,62,63,64,65,66,67,68,69,70,71,72,73,74,75,76,77,78,79,80,81,82,83,84,85,86,88,89,90,91,92,93,94
  - SQL Output Analysis & Query Tracing (8): 11,22,28,30,47,50,57,87
  - Views, DDL & Relational Algebra Concepts (5): 23,31,37,49,95
- DBMS Architecture & Features (26) — SPLIT:
  - DBMS Fundamentals & Advantages (13): 1,2,3,4,5,6,7,11,14,19,20,24,25
  - Database Administrator Roles & Responsibilities (6): 9,12,13,22,23,26
  - DBMS Architecture (3-Tier, Client-Server, Data Independence, Schema) (4): 8,10,15,16
  - Table vs View & Materialized View (3): 17,18,21
- Normalization & Database Design (23) — SPLIT:
  - Normalization Concepts (1NF/2NF/3NF/BCNF, Functional Dependency) (22): 1-21,23
  - Off-topic / Misplaced (duplicate ER-diagram question) (1): 22
- Keys in DBMS (34), ER Diagram & Database Design (25), SQL Commands (DDL, DML, DCL, TCL) (18),
  Transaction Management & ACID Properties (15), Relational Data Model & ER Relationships (14),
  Indexing & Query Optimization (B-Tree, B+ Tree) (10), Data Warehousing, Data Mining & Business
  Intelligence (9), Database Backup & Disaster Recovery (8), PL/SQL & Database Triggers (7), SQL
  Joins & Operations (7), Distributed & Parallel Databases (5), Database Design & Data Types (3),
  NoSQL, NewSQL & Modern Databases (2), Database Connectivity (JDBC) (2), Relational Keys
  (Candidate, Super, Primary, Foreign Key) (1), Indexing in DBMS (1), Keys, Constraints &
  Database Objects (0) — NO SPLIT

### dld.md — PLAN READY, NOT APPLIED
- Logic Gates & Universal Gates (34) — SPLIT:
  - Universal Gates (NAND & NOR) Proofs & Implementation (22): 1,2,4,8,10,11,12,14,16,17,18,19,20,21,22,23,24,25,27,28,29,33
  - Basic Logic Gates, Boolean Circuits & Digital Fundamentals (12): 3,5,6,7,9,13,15,26,30,31,32,34
- Karnaugh Map (K-Map) (24) — SPLIT:
  - Karnaugh Map Simplification (21): 1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,22,24
  - Miscellaneous Off-Topic Content (3): 20,21,23
- Combinational Circuits (Adders, Encoders, MUX) (23) — SPLIT:
  - Adders & Custom Combinational Logic Design (11): 2,3,4,5,7,10,11,13,15,19,21
  - Multiplexers, Decoders & Displays (12): 1,6,8,9,12,14,16,17,18,20,22,23
- Sequential Circuits (Latches & Flip-Flops) (17) — SPLIT:
  - Latch vs Flip-Flop Fundamentals (7): 1,6,8,10,13,16,17
  - Counters & Clock Circuits (7): 3,5,7,9,11,12,15
  - Combinational vs Sequential Circuits Comparison (3): 2,4,14
- Number Systems & Base Conversions (26), Boolean Algebra & De Morgan's Theorem (19), Logic
  Families (TTL vs CMOS) (6), 2's Complement & Binary Arithmetic (4), Number Systems & Codes (3),
  Finite State Machines (FSM) (1) — NO SPLIT

### electrical-and-electronics.md — PLAN READY, NOT APPLIED
- Electrical Circuits & Protection Devices (13) — SPLIT:
  - Circuit Analysis & Theorems (R, I, Norton calculations) (4): 2,6,9,12
  - Protection Devices (Fuse, MCB, Relay, Breaker) (2): 1,8
  - AC-DC Conversion & Transformers (3): 3,4,5
  - Power Systems & Frequency (3): 7,10,11
  - Component Comparison (Battery vs Capacitor) (1): 13
- Transistors (BJT & FET) (9), Semiconductor Devices & Diodes (4), Digital-to-Analog &
  Analog-to-Digital Converters (DAC/ADC) (4), AC Circuits & Power Analysis (2), Operational
  Amplifiers (Op-Amp) (2), Sensor Circuits & Automated Control Systems (2), Circuit Theorems
  (Thevenin, Norton, Superposition) (2), Electrical Machines (Motors & Alternators) (1) — NO SPLIT

### gk.md — PLAN READY, NOT APPLIED
- Bangladesh Affairs (114) — SPLIT:
  - Liberation War & Bangabandhu History (39): 1,10,16,21,22,32,42,53,56,58,59,60,65,66,68,70,71,72,77,81,82,83,84,85,87,88,94,95,97,98,100,101,104,105,106,107,110,113,114
  - Geography & Natural Resources (15): 3,4,7,8,23,35,36,48,52,75,76,78,79,80,112
  - Constitution, Politics & Governance (12): 11,13,14,17,19,25,50,64,69,74,96,111
  - Economy, Banking & Institutions (12): 9,24,28,29,30,31,41,46,49,51,73,102
  - Energy & Power Sector (6): 33,34,37,38,39,43
  - ICT & Digital Bangladesh (9): 2,5,27,47,54,62,86,92,99
  - Sports (2): 63,109
  - Culture, Literature & Awards (10): 20,26,40,44,45,55,57,61,67,103
  - Current Affairs & Miscellaneous (9): 6,12,15,18,89,90,91,93,108
- International Affairs (70) — SPLIT:
  - International Organizations & Abbreviations (20): 1,2,3,4,25,28,29,30,31,36,37,45,46,52,53,59,60,65,66,69
  - World Geography (11): 5,13,32,42,55,56,61,62,67,68,70
  - Global Economy & Development (13): 6,9,10,12,17,33,34,35,39,40,50,51,57
  - Current Conflicts & Geopolitics (8): 7,8,11,14,15,16,54,58
  - Sports (7): 20,21,22,27,38,43,47
  - History, Civilization & Personalities (11): 18,19,23,24,26,41,44,48,49,63,64
- Everyday Science & Environment (22), Banking & ICT Abbreviations (8) — NO SPLIT

### math.md — PLAN READY, NOT APPLIED (15 subtopics total)
- Arithmetic & Algebra Problems (17) — SPLIT:
  - Word Problems (Linear Equations, Ages, Population, Loans) (7): 2,3,5,7,10,11,17
  - Algebraic Identities (x + 1/x family) (4): 6,13,14,15
  - Surds & Logarithms (3): 8,12,16
  - Number Series & Sequences (2): 4,9
  - Magic Square (1): 1
- Set Theory & Discrete Math (13) — SPLIT:
  - Set Theory (7): 1,2,3,4,8,9,10
  - Propositional & Predicate Logic (6): 5,6,7,11,12,13
- Basic Arithmetic & Average (11) — SPLIT:
  - Averages (4): 1,4,10,11
  - Number Theory (GCD, LCM, Primes, Divisibility) (6): 2,3,6,7,8,9
  - Number Series (1): 5
- Ratio, Proportion & Mixtures (4) — SPLIT:
  - Ratio, Proportion & Mixtures (3): 1,2,3
  - Time & Work (1): 4
- Probability & Statistics (4) — SPLIT:
  - Probability (3): 1,2,4
  - Statistics (Mean, Median, Mode) (1): 3
- Discrete Mathematics & Recurrence Relations (3) — SPLIT:
  - Recurrence Relations (1): 1
  - Mathematical Induction (2): 2,3
- Percentage, Profit & Loss, Simple & Compound Interest (12), Geometry & Coordinate Geometry
  (10), Permutations & Combinations (6), Speed, Time, Distance & Boats (4), Propositional Logic &
  Logical Equivalence (4), Analytical Ability & Logical Reasoning (3), Calculus & Integration
  (2), Comprehensive Math Problems (2), Numerical Methods & Root Finding (2) — NO SPLIT

### microprocessor-and-computer-architecture.md — PLAN READY, NOT APPLIED
- Microprocessor Architecture & Functions (36) — SPLIT:
  - Microprocessor Definition & Functions (4): 1,14,18,20
  - Microprocessor vs Microcontroller (5): 3,7,21,27,31
  - CPU, ALU & Control Unit (5): 6,17,22,30,33
  - Registers & Flag Register (6): 13,15,23,24,25,29
  - Bus Architecture (System/Data/USB) (4): 5,16,28,32
  - GPU (3): 2,4,12
  - Bit-Width & Speed Comparisons (3): 8,9,19
  - 8086/8088 Architecture (2): 10,34
  - I/O & Peripheral Interfacing (DMA, PPI, SPI) (3): 11,26,35
  - Cache Memory (1): 36
- All other 10 subtopics — NO SPLIT

### english.md, image-processing.md, ms-office.md — NO CHANGES NEEDED (every subtopic NO SPLIT)

---

## Folder 2: written-answers/ — NOT STARTED (replay Folder 1's exact grouping per file once that file is done in Folder 1)

## Folder 3: all-questions/mcq/ — IN PROGRESS

### Files done in mcq/ (group D applied):
- ms-office.md — DONE: MS Office & Shortcuts (4) SPLIT: General Computer & OS Knowledge (2): 1,2;
  English Language & Literature (2): 3,4. All other subtopics NO SPLIT.
- oop.md — DONE: Polymorphism & Overloading (16) SPLIT: Polymorphism & Overloading (13):
  1,2,3,4,5,6,8,9,10,12,14,15,16; Destructors (2): 7,11; Abstract Classes (1): 13. All other
  subtopics (Java Programming 48, OOP Concepts & Principles 11, Encapsulation & Access Modifiers
  7, Inheritance 6, Constructors & Destructors 6, Exception Handling 6) NO SPLIT.
- operating-system.md — DONE: Process Management & Scheduling (24) SPLIT: Process States &
  Scheduling (20): 1,2,3,4,5,6,7,9,10,11,12,13,14,15,16,17,18,19,23,24; Digital Logic Circuits
  (1): 8; Virtual Memory & Paging (1): 20; File System Mounting (1): 21; OS Kernel Concept (1):
  22. Linux Commands & Administration (9) SPLIT: Linux/UNIX Commands & Administration (7):
  1,2,3,4,6,7,8; Database Roles & Privileges (1): 5; Windows Networking Utilities (1): 9. All
  other subtopics (OS Concepts & Multiprogramming 16, Virtual Memory & Paging 13, Deadlock 6,
  File Systems & Disk Management 4, Process Synchronization 2) NO SPLIT.
- programming-languages.md — DONE, no changes needed (Python 10, Mobile & Android Development 7,
  Visual Basic & .NET 7 — all NO SPLIT).
- software-engineering.md — DONE, no changes needed (Software Testing 20, SDLC Models 14,
  Software Design & Metrics 8, Design Patterns 3, Software Requirements Engineering 1 — all NO
  SPLIT).
- web-technology.md — DONE: Web Services & APIs (6) SPLIT: REST APIs & Message Formats (5):
  2,3,4,5,6; Web Application Security (1): 1. Full Stack & Web Servers (5) SPLIT: Web Servers &
  CMS (3): 1,2,3; Cisco Telephony/Server Platforms (2): 4,5. All other subtopics (HTML XML & Web
  Fundamentals 15, PHP & Server-Side 9, Scripting & JavaScript 8, HTTP & Status Codes 5, CSS &
  Styling 1) NO SPLIT.

### Files with a plan ready but NOT YET applied to mcq/: (waiting on groups A, B, C analysis
agents to report back — will be filled in here once they land) covering: ai-and-ml.md,
algorithm.md, bangla.md, c-programming.md, cloud-computing.md, compiler-and-toc.md,
computer-fundamental.md, computer-network-security.md, computer-networks.md, data-structure.md,
database.md, dld.md, electrical-and-electronics.md, english.md, gk.md, math.md,
mechanical-engineering.md, microprocessor-and-computer-architecture.md

## Folder 4: mcq-answers/ — NOT STARTED (replay Folder 3's grouping once Folder 3 is fully done)

## Folder 5: all-theories-with-previous-questions-attached/ — check only if written-answers/mcq-answers content changed (NOT a clustering task)
