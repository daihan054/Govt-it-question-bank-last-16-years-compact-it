# কম্বাইন্ড ব্যাংক অ্যাসিস্ট্যান্ট প্রোগ্রামার ২০২৬ — লিখিত সাজেশন

**ভিত্তি:** [`all-questions/`](../../all-questions/)-এর ৫০টি `.md` ফাইল সম্পূর্ণ পড়া হয়েছে — ৫,৯১০টি প্রশ্ন, ৩৫০টি আলাদা পরীক্ষা, ২০১১–২০২৬। লিখিত অংশে ৩,১৬৮টি প্রশ্ন। এই পদের **১২৬টি লিখিত রেকর্ড**।

**মূল রেফারেন্স প্রশ্নপত্র — সবগুলো সম্পূর্ণ পড়া:**

| পরীক্ষা | লিখিত প্রশ্ন |
|---|---|
| `Combined Bank Assistant Programmer 09.02.2024` | ১৮ |
| `Bangladesh Bank Assistant Programmer 03.02.2023` | ১৭ |
| `Combined Bank Assistant Programmer 09.06.2023` | ১৩ |
| `Combined Bank (HBFC and BKB) Assistant Programmer 2018` | ১৩ |
| `Combined 4 Banks Assistant Programmer 2020` | ১১ |
| `Bangladesh Bank Assistant Programmer 2016` · `2019` | ৯ + ৯ |
| `6 Banks & Financial Institutions Assistant Programmer 2021` | ৮ |
| `Combined 3 Banks Assistant Programmer 2018` | ৭ |

## এই পদের চরিত্র — সরাসরি গোনা

AP-র ১২৬টি লিখিত হিটের বিন্যাস: **c-programming ১৯ · database ১৮ · math ১০ · english ৯ · oop ৯ · web-technology ৯ · security ৮ · networks ৮ · algorithm ৭ · data-structure ৭ · software-engineering ৭ · bangla ৪ · dld ৩ · operating-system ৩**।

দুটো জিনিস এই পদকে আলাদা করে:

1. **প্রোগ্রাম লেখা বাধ্যতামূলক** — c-programming **(১১১)** সাবটপিকে ×১১ হিট, ভাণ্ডারের সর্ববৃহৎ।
2. **লিখিততেও গণিত আসে** — `Combined Bank AP 09.02.2024`-এ **৪টি আলাদা গাণিতিক প্রশ্ন** (জ্যামিতি, সুদ, সোনার বিশুদ্ধতার অনুপাত, সেট)। অন্য অনেক পদের লিখিতে গণিত নেই, এখানে আছে।

### স্টারের অর্থ

| স্টার | মানে |
|---|---|
| ★★★★★ | কম্বাইন্ড ব্যাংক AP-র লিখিত পত্রে সরাসরি এসেছে, বা একাধিক AP পত্রে repeat |
| ★★★★ | বাংলাদেশ ব্যাংক AP বা অন্য AP পত্রে এসেছে, অথবা সাবটপিকটা খুব বড় |
| ★★★ | ব্যাংক সেক্টরে নিয়মিত আসে |
| ★★ | আছে, কিন্তু ঘনত্ব কম |
| ★ | বিরল — সময় থাকলে দেখবেন |

`AP'24` = Combined Bank AP 09.02.2024 · `AP'23` = Combined Bank AP 09.06.2023 · `BB AP'23` = Bangladesh Bank AP 03.02.2023 · `(১১১)` = ঐ সাবটপিকে মোট প্রশ্ন

---

## Important topic

| Topic | ★ | Subtopic | ★ | প্রমাণ |
|---|---|---|---|---|
| **C Programming / প্রোগ্রাম লেখা** | ★★★★★ | Basic Programs & Control Statements — **prime 1..n · Floyd's triangle · ধারার যোগফল · অ্যারের ক্ষুদ্রতম উপাদান** | ★★★★★ | **AP'24-এ ৩টি** (prime; Floyd's triangle n=৫; `1+2+4+7+11+…+N`) · **AP'23** (smallest element) · **BB AP'23** (LCM) · ×১১ · **(১১১) ভাণ্ডারের সর্ববৃহৎ** |
| | | Output Tracing & Control Flow — কোড দেখে আউটপুট বলা | ★★★★★ | ×৫ · (৫৭) |
| | | Recursion & Functions — **recursion-এর আউটপুট**, iterative রূপে লেখা | ★★★★★ | **AP'24** · ×২ · (৩৮) |
| | | Flowcharts & Algorithms · String Manipulation · Pointers · File Handling | ★★★ | (১৬)+(১৪)+(৪)+(৪) |
| **Database** | ★★★★★ | SQL Queries — **GROUP BY + গড় বেতন**, বহু-টেবিল join | ★★★★★ | **AP'24** (Group by; Average Salary) · **AP'23** (৫ টেবিলের S/T/U/R স্কিমা) · ×৬ · **(৮৭) সর্ববৃহৎ** |
| | | Keys in DBMS — primary/candidate/super/foreign key নির্ণয় | ★★★★★ | ×৪ · (৩৪) |
| | | Relational Data Model & ER Relationships — **DBMS-এ সম্পর্কের প্রকার** | ★★★★★ | **AP'24** · ×২ · (১৪) |
| | | ER Diagram & Database Design — দৃশ্যপট → ERD → টেবিল | ★★★★★ | ×৩ · (২৫) |
| | | Normalization & Database Design · Transaction & ACID · Indexing | ★★★★ | (২১)+(১৪)+(১০) |
| | | SQL Commands (DDL/DML/DCL) · SQL Joins · Backup & DR · Data Warehousing | ★★★ | (১৮)+(৭)+(৮)+(৯) |
| **OOP** | ★★★★★ | OOP Concepts (Inheritance & Polymorphism) — **Polymorphism কী, প্রকারভেদ উদাহরণসহ** | ★★★★★ | **AP'24** · ×৪ · **(৫৪) সর্ববৃহৎ** |
| | | Output Tracing & Recursion — Java কোডের আউটপুট | ★★★★★ | ×২ · (১০) |
| | | Java Programming & Methods · Class Design & OO Modeling | ★★★★ | (১৮)+(১১) |
| | | Constructors & Destructors · Encapsulation · Exception Handling · Interface vs Abstract | ★★★ | (৮)+(৭)+(৪)+(২) |
| **Web Technology** | ★★★★★ | HTML & Web Fundamentals — টেবিল/লিস্ট/ফর্মের কোড, static বনাম dynamic | ★★★★★ | ×৪ · **(৩০) সর্ববৃহৎ** |
| | | JavaScript & jQuery — **form validation, DOM, `$.ajax()` বনাম `$.get()`** | ★★★★★ | ×৩ · (১৬) |
| | | Web Security & Same-Origin — **ভিন্ন origin-এর দুই frame কেন আলাদা রাখা যুক্তিসঙ্গত** | ★★★★★ | **AP'23** · (২) |
| | | HTTP Protocol · Web Services & APIs · Full Stack & Backend · CSS | ★★★ | (১০)+(৮)+(৭)+(৪) |
| **গণিত** | ★★★★★ | Percentage, Profit & Loss, সুদ | ★★★★★ | **AP'24** (সুদ) · ×২ · (১২) |
| | | Geometry & Coordinate Geometry | ★★★★★ | **AP'24** · ×২ · (১০) |
| | | Ratio, Proportion & Mixtures — **সোনার বিশুদ্ধতা** ঘরানা | ★★★★★ | **AP'24** · (৪) |
| | | Set Theory & Discrete Math — **৭২%, ৪০%, উভয় ৩০%** ধাঁচের ভেন সমস্যা | ★★★★★ | **AP'24** · (১৩) |
| | | Arithmetic & Algebra Problems | ★★★★★ | ×২ · (১৬) |
| | | Permutation & Combination · Probability · Propositional Logic · Recurrence | ★★★ | (৬)+(৪)+(৪)+(৩) |
| **Computer / Network Security** | ★★★★ | Social Engineering & Cyber Attacks — DoS/DDoS, phishing, MITM | ★★★★★ | ×৩ · **(৩২) সর্ববৃহৎ** |
| | | Security Protocols (SSL/TLS) — **TLS-এর private key চুরি হলে নিষ্ক্রিয় আক্রমণকারী কী পড়তে পারবে** | ★★★★★ | **AP'23** · (১২) |
| | | Malware & Security Threats — virus/worm/trojan/ransomware | ★★★★ | ×২ · (২০) |
| | | Cryptography · Web Security (SQLi, XSS) · Firewalls · Authentication · CIA Triad | ★★★★ | (৩১)+(১৯)+(২০)+(১৬)+(৮) |
| **Computer Networks** | ★★★★ | Subnetting & IP Addressing — network/broadcast/mask/usable range | ★★★★★ | ×৩ · **(১০৯) ভাণ্ডারের সর্ববৃহৎ** |
| | | Error Detection & Data Communication — **CRC কোডওয়ার্ড; ৩০০০ Hz টেলিফোন লাইনের ডেটা রেট** | ★★★★★ | **AP'23-এ দুটোই** · ×২ · (১৪) |
| | | OSI & TCP/IP Reference Model — layer, protocol, PDU | ★★★★★ | ×২ · (৫২) |
| | | Data Rate & Channel Capacity (Nyquist, Shannon) | ★★★★ | (১৬) |
| | | Transport Layer (TCP/UDP) · Networking Devices · Application Layer · Topologies | ★★★ | (১৭)+(১৯)+(২২)+(১৪) |
| **Algorithm** | ★★★★ | Graph Representation — **adjacency list-এ কোন সমস্যা matrix-এর চেয়ে বেশি দক্ষ** | ★★★★★ | **AP'23** · **BB AP'23** (৭ vertex complete binary tree) · ×২ · (৪) |
| | | Sorting Algorithms & Complexity — trace + complexity টেবিল | ★★★★★ | **(৩৬) সর্ববৃহৎ** |
| | | Algorithm Analysis & Asymptotic Complexity — Big-O, recurrence | ★★★★ | **BB AP'16** · (১৪) |
| | | Searching · Graph Traversal (BFS/DFS) · Graph Algorithms (MST/Dijkstra) · DP & Greedy | ★★★ | (১৪)+(১৭)+(১৫)+(৯) |
| **Data Structure** | ★★★★ | Stack — **Stack বনাম Queue-র পার্থক্য ও প্রত্যেকের ২টি প্রয়োগ**; infix→postfix | ★★★★★ | **AP'24** · **BB AP'16** · ×৩ · (২০) |
| | | Priority Queues & Heaps — **Max Heap-এর ধাপে ধাপে অপারেশন [a–j]** | ★★★★★ | **AP'23** · (৮) |
| | | Tree · Linked List · BST · Hashing & Hash Tables · Queue | ★★★★ | (২৭)+(১৫)+(৯)+(৬)+(৬) |
| **Software Engineering** | ★★★★ | Software Project Management — **আপনি কোন বাস্তব প্রজেক্ট বানিয়েছেন, কী সমস্যা হয়েছে, কীভাবে সমাধান করেছেন** | ★★★★★ | **AP'24** · (৯) |
| | | Software Cost Estimation — **Function Point গণনা (complexity adjustment factor)** | ★★★★★ | **AP'23** · (৪) |
| | | Software Testing & Evaluation · UML Diagrams | ★★★★ | ×২ প্রত্যেকটি · (৪০)+(১৪) |
| | | SDLC Phases & Models · Architecture & Design Patterns · Requirements Engineering | ★★★ | (৪৫)+(১৩)+(১০) |
| **Operating System** | ★★★★ | Virtual Memory & Page Replacement — **page reference string-এ page fault গোনা** | ★★★★★ | **AP'23** (1,3,0,3,5,6,3 · ৩ frame) · (১৬) |
| | | Concurrency, Threads & Synchronization — **Multithreading কী, কেন ব্যবহার হয়** | ★★★★★ | **AP'24** · (১১) |
| | | CPU Scheduling · Deadlock · Linux Commands · Memory Management | ★★★ | (২৫)+(২৩)+(৪৭)+(১৬) |
| **DLD** | ★★★ | Number Systems & Base Conversions · Logic Gates & Universal Gates | ★★★★ | (২৬)+(৩৩) |
| | | K-Map · Boolean Algebra · Combinational Circuits · Sequential Circuits | ★★★ | (১৯)+(১৯)+(২৩)+(১৭) |
| **Programming Languages** | ★★★ | .NET Framework — component, CLR | ★★★★ | ×২ · (৬) |
| **Cloud Computing** | ★★ | Cloud Service Models · Virtualization & Containers | ★★★ | (১৩)+(৮) |
| **Compiler & TOC** | ★★ | Compiler vs Interpreter | ★★★★ | **৬ পরীক্ষায় হুবহু** · (৭) |
| **Computer Fundamental** | ★★ | Acronyms · ICT in Society · Blockchain · Data Center | ★★ | (৫৯)+(২৪)+(৮)+(১০) |

### General section — বাংলা ও ইংরেজি

| Topic | ★ | Subtopic | ★ | প্রমাণ |
|---|---|---|---|---|
| **ইংরেজি** | ★★★★★ | Focus Writing — **শিক্ষা/প্রযুক্তি/আর্থিক সাক্ষরতা** ঘরানার রচনা | ★★★★★ | **AP'24** ("The Role of computer on education system in Bangladesh") · **AP'23** ("Digital Financial Literacy") · ×৫ · **(৩৭) সর্ববৃহৎ** |
| | | Translation (বাংলা → ইংরেজি) — ব্যাংক/অর্থনীতি অনুচ্ছেদ | ★★★★★ | **AP'24** · **AP'23** · ×৩ · (১৮) |
| | | Letter & Application Writing — **ছোট ভাইকে বৃত্তিমূলক প্রশিক্ষণের গুরুত্ব নিয়ে চিঠি** | ★★★★★ | **AP'24** · (৬) |
| | | English Grammar · Idioms & Phrases · Comprehension | ★★★ | (২৯)+(৯)+(৫) |
| **বাংলা** | ★★★★ | Translation (ইংরেজি → বাংলা) — ঝুঁকি ব্যবস্থাপনা/ব্যাংকিং অনুচ্ছেদ | ★★★★★ | **AP'24** · **AP'23** (Risk Management) · ×৩ · (১৯) |
| | | Focus Writing (বাংলা রচনা) | ★★★★ | (২৫) |
| | | ব্যাকরণ ও সাহিত্য · সারমর্ম · পত্র লিখন | ★★ | (৬১)+(৬)+(৭) |

---

## Prediction

**কম্বাইন্ড ব্যাংক Assistant Programmer ২০২৬-এর লিখিতে যেগুলো আসার সবচেয়ে বেশি সম্ভাবনা।** *(ভবিষ্যতের প্রশ্ন কেউ নিশ্চিত বলতে পারে না; স্টার আমার আত্মবিশ্বাসের মাত্রা, যা পুরোপুরি ঐতিহাসিক ডেটার ওপর দাঁড়ানো।)*

### ক. প্রায় নিশ্চিত — কম্বাইন্ড ব্যাংক AP-র পত্রেই এসেছে

| # | যা আসবে | কেন | ★ |
|---|---|---|---|
| ১ | **প্রোগ্রাম লেখা — prime 1..n** | **AP'24**-এ হুবহু; **SO'24**, **SO'23**-এও prime/matrix; **(১১১) ভাণ্ডারের সর্ববৃহৎ সাবটপিক** | ★★★★★ |
| ২ | **প্যাটার্ন প্রোগ্রাম — Floyd's triangle (n=৫)** | **AP'24**-এ হুবহু, আউটপুট সহ দেওয়া ছিল | ★★★★★ |
| ৩ | **ধারার যোগফল — `1+2+4+7+11+…+N`** | **AP'24**-এ হুবহু (পার্থক্য ১,২,৩,৪… ধাঁচের ধারা) | ★★★★★ |
| ৪ | **Recursion-এর আউটপুট বের করা** | **AP'24**-এ কোডসহ; Recursion **(৩৮)** | ★★★★★ |
| ৫ | **অ্যারে থেকে ক্ষুদ্রতম/বৃহত্তম উপাদান বের করার ফাংশন** | **AP'23**-এ হুবহু; **BB AP'19**-এ ২০ আইটেমের সর্বোচ্চ | ★★★★★ |
| ৬ | **SQL — GROUP BY দিয়ে গড় বেতন / বিভাগভিত্তিক সমষ্টি** | **AP'24**-এ হুবহু (Group by; Average Salary); **(৮৭) সর্ববৃহৎ** | ★★★★★ |
| ৭ | **বহু-টেবিলের স্কিমা থেকে SQL query** | **AP'23**-এ হুবহু (S, T, U, R — পাঁচ টেবিল) | ★★★★★ |
| ৮ | **DBMS-এ সম্পর্কের প্রকার (1:1, 1:M, M:N)** | **AP'24**-এ হুবহু; Officer(IT) '২৬ মে-তেও একই প্রশ্ন | ★★★★★ |
| ৯ | **Polymorphism কী, কত প্রকার, উদাহরণসহ** | **AP'24**-এ হুবহু; **(৫৪) oop-র সর্ববৃহৎ**; BB AP'23/'20/'16/'19 — **BB-র ৪ পত্রেই** | ★★★★★ |
| ১০ | **Stack বনাম Queue + প্রত্যেক দিয়ে সমাধান হওয়া ২টি সমস্যা** | **AP'24**-এ হুবহু; **BB AP'16**-এ infix→postfix | ★★★★★ |
| ১১ | **Max Heap-এর ধাপে ধাপে অপারেশন দেখানো** | **AP'23**-এ হুবহু ([a–j] ধাপ); BB AD(ICT)'25-এও min heap | ★★★★★ |
| ১২ | **Multithreading কী, কেন ব্যবহার করা হয়** | **AP'24**-এ হুবহু; Officer(IT) '২৬ জানু-তেও multi-threaded ও distributed computing | ★★★★★ |
| ১৩ | **Page reference string থেকে page fault গণনা** | **AP'23**-এ হুবহু (1,3,0,3,5,6,3 · ৩ frame) | ★★★★★ |
| ১৪ | **Adjacency list বনাম adjacency matrix — কোন সমস্যায় কোনটা দক্ষ** | **AP'23**; **BB AP'23**-এ ৭ vertex complete binary tree-র রূপান্তর | ★★★★★ |
| ১৫ | **CRC দিয়ে কোডওয়ার্ড/ত্রুটি নির্ণয়** | **AP'23**-এ হুবহু | ★★★★★ |
| ১৬ | **টেলিফোন লাইনের ব্যান্ডউইথ থেকে সর্বোচ্চ ডেটা রেট (Nyquist/Shannon)** | **AP'23**-এ হুবহু (৩০০০ Hz, ৩০০–৩৩০০ Hz) | ★★★★★ |
| ১৭ | **Function Point গণনা (complexity adjustment factor সহ)** | **AP'23**-এ হুবহু — লিখিত AP পত্রের সবচেয়ে অপ্রত্যাশিত কিন্তু বাস্তব প্রশ্ন | ★★★★★ |
| ১৮ | **TLS-এর private key চুরি হলে নিষ্ক্রিয় আক্রমণকারী পুরনো ট্রাফিক পড়তে পারবে কি না** | **AP'23**-এ হুবহু (forward secrecy-র ধারণা) | ★★★★★ |
| ১৯ | **ভিন্ন origin থেকে লোড হওয়া দুই frame কেন আলাদা রাখা যুক্তিসঙ্গত (same-origin policy)** | **AP'23**-এ হুবহু | ★★★★★ |
| ২০ | **লিখিততে গণিত — সুদ, জ্যামিতি, অনুপাত (সোনার বিশুদ্ধতা), সেট (৭২%–৪০%–৩০%)** | **AP'24-এ ৪টি আলাদা গাণিতিক প্রশ্ন** — AP-র লিখিতে গণিত বাদ দেওয়া যাবে না | ★★★★★ |
| ২১ | **ইংরেজি রচনা — শিক্ষায় কম্পিউটার / ডিজিটাল আর্থিক সাক্ষরতা** | **AP'24** ("The Role of computer on education system in Bangladesh") · **AP'23** ("Digital Financial Literacy") | ★★★★★ |
| ২২ | **ইংরেজি চিঠি লেখা — ছোট ভাইকে বৃত্তিমূলক প্রশিক্ষণ নিয়ে** | **AP'24**-এ হুবহু; Letter Writing (৬) | ★★★★★ |
| ২৩ | **দুই দিকের অনুবাদ — ব্যাংক ও ঝুঁকি ব্যবস্থাপনার অনুচ্ছেদ** | **AP'24** · **AP'23** — পরপর দুই পত্রেই দুই দিকের অনুবাদ | ★★★★★ |
| ২৪ | **বাস্তব প্রজেক্টের অভিজ্ঞতা — কী বানিয়েছেন, কী সমস্যা, কীভাবে সমাধান** | **AP'24**-এ হুবহু — এটা মুখস্থের নয়, আগে থেকে গুছিয়ে রাখার প্রশ্ন | ★★★★★ |

### খ. খুব বেশি সম্ভাবনা — বাংলাদেশ ব্যাংক AP বা অন্য AP পত্রে এসেছে

| # | যা আসবে | কেন | ★ |
|---|---|---|---|
| ২৫ | **Subnetting — network/broadcast/mask/usable range** | ×৩; **(১০৯) ভাণ্ডারের সর্ববৃহৎ**; প্রায় প্রতিটি ব্যাংক লিখিততেই | ★★★★★ |
| ২৬ | **OSI layer — কোন layer-এ কী; end-to-end encryption কোন layer-এ** | ×২; **BB AP'23** · **BB AP'19** (flow control কোন দুই layer) | ★★★★ |
| ২৭ | **ER diagram দৃশ্যপট থেকে → টেবিলে রূপান্তর** | ×৩; (২৫) | ★★★★ |
| ২৮ | **Primary/candidate/super/foreign key নির্ণয়** | ×৪; (৩৪); **BB AP'23**, **BB AP'16** | ★★★★ |
| ২৯ | **HTML — টেবিল/লিস্ট/ফর্মের কোড লেখা** | ×৪; **(৩০) সর্ববৃহৎ**; **BB AP'16** | ★★★★ |
| ৩০ | **JavaScript form validation / DOM / `$.ajax()` বনাম `$.get()`** | ×৩; (১৬) | ★★★★ |
| ৩১ | **SQL injection ও XSS — কীভাবে হয়, কীভাবে ঠেকাবেন** | **৩ পরীক্ষায় হুবহু**; (১৯) | ★★★★ |
| ৩২ | **Malware — virus/worm/trojan/ransomware-এর পার্থক্য** | ×২; (২০); **BB AP'19** | ★★★★ |
| ৩৩ | **Sorting — ধাপে ধাপে trace + complexity টেবিল** | **(৩৬) সর্ববৃহৎ**; **BB Recruitment Test'20**-এ insertion sort | ★★★★ |
| ৩৪ | **Big-O ও recurrence relation** | **BB AP'16**; (১৪) | ★★★★ |
| ৩৫ | **Hash table — linear probing দিয়ে collision resolution** | **BB AP'23** (size ১৩, h(k)=k mod ১৩); (৬) | ★★★★ |
| ৩৬ | **UML class/use case diagram দৃশ্যপট থেকে** | ×২; **BB AP'23** (token-ring LAN class diagram); (১৪) | ★★★★ |
| ৩৭ | **Software testing — unit বনাম integration, black-box বনাম white-box** | ×২; **৫ পরীক্ষায় হুবহু**; (৪০) | ★★★★ |
| ৩৮ | **Java কোডের আউটপুট (static variable + recursion সহ)** | ×২; (১০); **BB SO'24 → '২৬**-এ হুবহু | ★★★★ |
| ৩৯ | **Compiler বনাম Interpreter** | **৬ পরীক্ষায় হুবহু — লিখিত অংশের সবচেয়ে পুনরাবৃত্ত প্রশ্ন** | ★★★★ |
| ৪০ | **.NET Framework-এর component** | ×২; (৬) — AP পদে এটা এখনো আসে | ★★★ |

---

## যাচাইকরণ নোট

সব স্টার, সংখ্যা আর পরীক্ষার নাম `all-questions/`-এর ভেতরের আসল exam tag থেকে গোনা — কোনোটাই অনুমান করা নয়। Prediction অংশটা ঐতিহাসিক প্যাটার্ন থেকে করা পূর্বাভাস, নিশ্চয়তা নয়।
