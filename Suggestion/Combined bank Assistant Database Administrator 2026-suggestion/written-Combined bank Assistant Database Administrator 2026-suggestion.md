# কম্বাইন্ড ব্যাংক অ্যাসিস্ট্যান্ট ডেটাবেজ অ্যাডমিনিস্ট্রেটর ২০২৬ — লিখিত সাজেশন

**ভিত্তি:** [`all-questions/`](../../all-questions/)-এর ৫০টি `.md` ফাইল সম্পূর্ণ পড়া হয়েছে — ৫,৯১০টি প্রশ্ন, ৩৫০টি আলাদা পরীক্ষা, ২০১১–২০২৬। লিখিত অংশে ৩,১৬৮টি প্রশ্ন। এই পদের **১৩২টি লিখিত রেকর্ড**।

**মূল রেফারেন্স প্রশ্নপত্র — সবগুলো সম্পূর্ণ পড়া:**

| পরীক্ষা | লিখিত প্রশ্ন |
|---|---|
| `BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022` | ৪৫ |
| `BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022` | ৩৩ |
| `Sonali Bank PLC Assistant Database Administrator 23.02.2024` — **সবচেয়ে সাম্প্রতিক ব্যাংক ADBA পত্র** | ২৬ |
| `RAKUB Assistant Database Administrator 2020` | ১২ |
| `Sonali & Janata Bank Ltd. Assistant Database Administrator 2022` | ১১ |
| `Palli Sanchay Bank Assistant Database Administrator 2018` | ৫ |

## এই পদের চরিত্র — সরাসরি গোনা

১৩২টি লিখিত হিটের বিন্যাস: **database ২৭ · gk ২৫ · computer-networks ২৩ · bangla ৯ · english ৭ · c-programming ৬ · dld ৬ · computer-fundamental ৫ · algorithm ৪ · microprocessor ৪**।

দুটো জিনিস খেয়াল করার মতো:

1. **ডেটাবেজ সবচেয়ে বড় (২৭), কিন্তু MCQ-র মতো একচেটিয়া নয়।** লিখিততে GK (২৫) আর নেটওয়ার্কিং (২৩) প্রায় সমান জায়গা নেয় — শুধু ডেটাবেজ পড়ে লিখিতে পাশ করা যাবে না।
2. **`RAKUB ADBA 2020`-এর ১২টি প্রশ্নের ১২টিই ডেটাবেজ থেকে।** অর্থাৎ কোনো কোনো পত্র পুরোপুরি ডেটাবেজকেন্দ্রিকও হতে পারে — দুই ধরনের পত্রের জন্যই প্রস্তুত থাকতে হবে।

### স্টারের অর্থ

| স্টার | মানে |
|---|---|
| ★★★★★ | ব্যাংক ADBA-র পত্রে সরাসরি এসেছে, বা একাধিক ADBA পত্রে repeat |
| ★★★★ | BPSC ADBA বা কাছাকাছি পদে এসেছে, অথবা সাবটপিকটা খুব বড় |
| ★★★ | ব্যাংক সেক্টরে নিয়মিত আসে |
| ★★ | আছে, কিন্তু ঘনত্ব কম |
| ★ | বিরল — সময় থাকলে দেখবেন |

`SB'24` = Sonali Bank PLC ADBA 23.02.2024 · `SJ'22` = Sonali & Janata Bank ADBA 2022 · `RAKUB'20` = RAKUB ADBA 2020 · `(৮৭)` = ঐ সাবটপিকে মোট প্রশ্ন

---

## Important topic

| Topic | ★ | Subtopic | ★ | প্রমাণ |
|---|---|---|---|---|
| **Database** | ★★★★★ | SQL Queries — **জোড় সংখ্যা বের করা; দুই টেবিলের UNCOMMON নাম; HR schema (minimum salary > 10000); parent থেকে child টেবিলে কপি; শীর্ষ n% বের করা** | ★★★★★ | **RAKUB'20-এ ৪টি আলাদা query** · ×৫ · **(৮৭) সর্ববৃহৎ** |
| | | DBMS Architecture & Features — **DBA/Database Engineer-এর দায়িত্ব; View বনাম Materialized View ও কখন কোনটা** | ★★★★★ | **RAKUB'20-এ ২টি** · **SJ'22** · **SB'24** · ×৪ · (২৬) |
| | | Keys in DBMS — **Primary key বনাম Unique key; Drop বনাম Purge; Delete বনাম Truncate; functional dependency থেকে candidate key; primary/candidate/super key** | ★★★★★ | **RAKUB'20** · **SJ'22-এ ২টি** · ×৩ · (৩৪) |
| | | Database Backup & Disaster Recovery — **incremental বনাম differential backup, ব্যাংকিং সিস্টেমে কোনটা; ডেটা না হারানোর উপায়** | ★★★★★ | **SB'24-এ ২টি** · **RAKUB'20** · ×৩ · (৮) |
| | | Transaction Management & ACID — **ACID properties; case study দিয়ে সমাধান** | ★★★★★ | **RAKUB'20** · **SB'24** · ×২ · (১৪) |
| | | Normalization & Database Design — **ডেটাবেজ normalize করে ER Diagram আঁকা** | ★★★★★ | **SB'24** · ×২ · (২১) |
| | | Relational Data Model & ER Relationships — **constraint কী, table-level বনাম column-level constraint; weak বনাম strong entity** | ★★★★★ | **RAKUB'20** · **SJ'22** · ×২ · (১৪) |
| | | ER Diagram & Database Design — **দৃশ্যপট থেকে ER ডায়াগ্রাম আঁকা (যেমন BPL)** | ★★★★★ | **SJ'22** · (২৫) |
| | | SQL Commands (DDL, DML, DCL, TCL) — **ডুপ্লিকেট ডেটা খুঁজে বের করা; DDL ও DML ব্যাখ্যা** | ★★★★★ | **RAKUB'20** · ×২ · (১৮) |
| | | Indexing & Query Optimization — **Indexing কী, কোথায় ব্যবহার হয়** | ★★★★★ | **RAKUB'20** · (১০) |
| | | PL/SQL & Database Triggers — **টেবিল থেকে সুদের হার বের করতে SQL প্রোগ্রাম** | ★★★★★ | **SB'24** · (৭) |
| | | Distributed & Parallel Databases — distributed database কী | ★★★★★ | **SJ'22** · (৫) |
| | | Data Warehousing, Data Mining & BI · SQL Joins · NoSQL · JDBC | ★★★ | (৯)+(৭)+(২)+(২) |
| **GK (সাধারণ অংশ)** | ★★★★★ | Bangladesh Affairs — **GI পণ্য কী; ECNEC-এর কাজ; সার্বিক অর্থনীতি ও মূল্যস্ফীতি** | ★★★★★ | **SB'24-এ ৩টি** · ×১০ · **(১১৪) সর্ববৃহৎ** |
| | | International Affairs — **Green Economy বনাম Blue Economy; Westminster সরকার ব্যবস্থা** | ★★★★★ | **SB'24-এ ২টি** · ×৯ · (৭০) |
| | | Everyday Science & Environment — **ECG বনাম ECHO; "ট্রানজিস্টরের আবিষ্কার পৃথিবী বদলে দিয়েছে" — ব্যাখ্যা** | ★★★★★ | **SB'24-এ ২টি** · ×৬ · (২২) |
| | | Banking & ICT Abbreviations — RTGS, NPSB, BEFTN | ★★★★ | (৮) |
| **Computer Networks** | ★★★★ | Multiplexing & Bandwidth — TDM/FDM/WDM | ★★★★★ | ×৩ · (১৮) |
| | | Digital Modulation & Signal Processing — BPSK/QPSK/QAM constellation | ★★★★★ | ×৩ · (১০) |
| | | Subnetting & IP Addressing — **classful থেকে classless ঠিকানায় যাওয়ার মূল কারণ** | ★★★★★ | **SB'24** · **(১০৯) ভাণ্ডারের সর্ববৃহৎ** |
| | | Pulse Code Modulation (PCM) · Network Layer (Fragmentation & Tunneling) | ★★★★ | ×২ · (৬)+(৪) |
| | | Spread Spectrum & Multiple Access (CDMA, FHSS, DSSS) | ★★★★ | ×২ · (৩) |
| | | OSI & TCP/IP · Transport Layer · Application Layer · Networking Devices | ★★★ | (৫২)+(১৭)+(২২)+(১৯) |
| | | Error Detection · Data Rate · Topologies · IPv6 · Routing · Optical Fiber | ★★★ | (১৪)+(১৬)+(১৪)+(১৩)+(১৮)+(১৩) |
| **DLD** | ★★★★ | Logic Gates & Universal Gates — **Boolean expression-এর লজিক সার্কিট এঁকে নির্দিষ্ট ইনপুটে আউটপুট** | ★★★★★ | **SB'24** (Q = C̄ + ĀB + BC(B+C)‾) · ×২ · **(৩৩) সর্ববৃহৎ** |
| | | Combinational Circuits — **সার্কিট থেকে truth table (2-bit full adder with carry)** | ★★★★★ | **SB'24** · (২৩) |
| | | Number Systems · Boolean Algebra · K-Map · Sequential Circuits | ★★★ | (২৬)+(১৯)+(১৯)+(১৭) |
| **Computer Fundamental** | ★★★★ | Server Hardware & Enterprise Systems — **সার্ভার কেনার আগে কী কী যাচাই করবেন** | ★★★★★ | **SB'24** · (৫) |
| | | Computer Fundamentals & Acronyms · Hardware Components & BIOS (CMOS ব্যাটারি) | ★★★★ | ×২ প্রত্যেকটি · (৫৯)+(২৪) |
| | | Data Center Infrastructure · ICT in Society · Blockchain | ★★★ | (১০)+(২৪)+(৮) |
| **C Programming / প্রোগ্রাম লেখা** | ★★★★ | Recursion & Functions | ★★★★★ | ×৩ · (৩৮) |
| | | Basic Programs & Control Statements — **`eˣ = 1 + x/1 + x²/2! + …` ধারার প্রোগ্রাম** | ★★★★★ | **SB'24** · **(১১১) ভাণ্ডারের সর্ববৃহৎ** |
| | | String Manipulation & Algorithms — **লাইব্রেরি ফাংশন ছাড়া string reverse** | ★★★★★ | **SJ'22** · (১৪) |
| | | Output Tracing & Control Flow · Flowcharts | ★★★ | (৫৭)+(১৬) |
| **Microprocessor & Architecture** | ★★★★ | RAID Architecture & Storage — **কোন RAID level সবচেয়ে ভালো ও কেন; ডেটাবেজে RAID-র প্রাসঙ্গিকতা ও ব্যবহার** | ★★★★★ | **SB'24-এ ২টি আলাদা প্রশ্ন** · ×২ · (১৫) |
| | | Memory Hierarchy & Storage · Cache Memory · Secondary Storage (HDD বনাম SSD) | ★★★ | (২৬)+(১৪)+(১০) |
| **Operating System** | ★★★★ | CPU Scheduling Algorithms — **FCFS ও SJF; AWT ও ATAT নির্ণয়** | ★★★★★ | **SB'24** · (২৫) |
| | | Linux / Unix Commands & Administration — **লুকানো ফাইলসহ ডিরেক্টরি তালিকা** | ★★★★★ | **SJ'22** · **(৪৭) OS-র সর্ববৃহৎ** |
| | | Deadlock · Virtual Memory · Memory Management · Concurrency | ★★★ | (২৩)+(১৬)+(১৬)+(১১) |
| **Algorithm** | ★★★ | Sorting Algorithms & Complexity · Dynamic Programming | ★★★★ | ×২ প্রত্যেকটি · (৩৬)+(৫) |
| | | Searching · Graph Traversal · Graph Algorithms · Complexity Analysis | ★★★ | (১৪)+(১৭)+(১৫)+(১৪) |
| **Computer / Network Security** | ★★★ | Security Protocols (SSL/TLS, HTTPS) — **ক্লায়েন্ট অ্যাপ ও ডেটাবেজ সার্ভারের মধ্যে নিরাপদ যোগাযোগ নিশ্চিত করা** | ★★★★★ | **SB'24** · (১২) |
| | | Web Security Vulnerabilities — **SQL Injection** | ★★★★ | (১৯) — DBA পদে সবচেয়ে প্রাসঙ্গিক নিরাপত্তা প্রশ্ন |
| | | Cryptography · Authentication & Access Control · Firewalls | ★★★ | (৩১)+(১৬)+(২০) |
| **Data Structure** | ★★★ | Hashing & Hash Tables — **separate chaining দিয়ে hash function-এর অঙ্ক** | ★★★★★ | **SJ'22** · (৬) |
| | | Tree · Stack · Linked List · BST · Priority Queue & Heap | ★★★ | (২৭)+(২০)+(১৫)+(৯)+(৮) |
| **Compiler & TOC** | ★★★ | Compiler vs Interpreter | ★★★★★ | ×২ · **৬ পরীক্ষায় হুবহু — লিখিতের সবচেয়ে পুনরাবৃত্ত প্রশ্ন** |
| **Web Technology** | ★★★ | Full Stack & Backend — **ক্লায়েন্ট, ডেটাবেজ ও লগইন পেজসহ প্রোগ্রাম** | ★★★★★ | **SB'24** · (৭) |
| | | HTML · JavaScript & jQuery · HTTP Protocol | ★★★ | (৩০)+(১৬)+(১০) |
| **Image Processing** | ★★★ | Vector বনাম Raster · Color Model · Edge Detection | ★★★ | ×৩ · (৭) — শুধু এই পদের ঘরানাতেই দেখা গেছে |
| **OOP** | ★★ | OOP Concepts (Inheritance & Polymorphism) · Java Programming | ★★★ | (৫৪)+(১৮) |
| **Software Engineering** | ★★ | SDLC · Software Testing · UML | ★★★ | (৪৫)+(৪০)+(১৪) |
| **গণিত** | ★★ | Arithmetic & Algebra · Percentage & সুদ · Set Theory | ★★ | (১৬)+(১২)+(১৩) |

### General section — বাংলা ও ইংরেজি

| Topic | ★ | Subtopic | ★ | প্রমাণ |
|---|---|---|---|---|
| **বাংলা** | ★★★★★ | Focus Writing — **প্রকাশনার মান, প্রযুক্তির অপকারিতা** ঘরানার রচনা | ★★★★★ | **SB'24** ("প্রকাশনার মান উন্নয়নে সু-সম্পাদিত পাণ্ডুলিপি") · **SJ'22** (প্রযুক্তির অপকারিতা) · ×৩ · (২৫) |
| | | Translation (ইংরেজি → বাংলা) | ★★★★★ | **SB'24** (বিদ্যালয়ের সৃজনশীলতা) · ×২ · (১৯) |
| | | ব্যাকরণ ও সাহিত্য · সারমর্ম · পত্র লিখন | ★★★ | ×২ · (৬১)+(৬)+(৭) |
| **ইংরেজি** | ★★★★★ | Focus Writing — **পরিবেশ, সামাজিক সমস্যা** ঘরানার রচনা | ★★★★★ | **SB'24** ("Roadside tree plantation in reducing noise pollution") · **SJ'22** ("Harm of drugs") · ×৩ · **(৩৭) সর্ববৃহৎ** |
| | | Translation (বাংলা → ইংরেজি) · English Grammar · Idioms | ★★★ | (১৮)+(২৯)+(৯) |

---

## Prediction

**কম্বাইন্ড ব্যাংক Assistant Database Administrator ২০২৬-এর লিখিতে যেগুলো আসার সবচেয়ে বেশি সম্ভাবনা।** *(ভবিষ্যতের প্রশ্ন কেউ নিশ্চিত বলতে পারে না; স্টার আমার আত্মবিশ্বাসের মাত্রা, যা পুরোপুরি ঐতিহাসিক ডেটার ওপর দাঁড়ানো।)*

### ক. প্রায় নিশ্চিত — ব্যাংক ADBA-র পত্রেই এসেছে

| # | যা আসবে | কেন | ★ |
|---|---|---|---|
| ১ | **SQL query লেখা — জোড় সংখ্যা; দুই টেবিলের অমিল নাম; HR schema-য় শর্তসাপেক্ষ SELECT; parent থেকে child টেবিলে কপি** | **RAKUB'20-এর ১২ প্রশ্নের ৪টিই SQL query**; **(৮৭) সর্ববৃহৎ** | ★★★★★ |
| ২ | **DBA / Database Engineer-এর দায়িত্ব** | **RAKUB'20** · **SJ'22** — দুই পত্রেই; পদের নামেই DBA | ★★★★★ |
| ৩ | **View বনাম Materialized View — পার্থক্য ও কখন কোনটা ব্যবহার করবেন** | **RAKUB'20**-এ হুবহু | ★★★★★ |
| ৪ | **Primary key বনাম Unique key; Drop বনাম Purge; Delete বনাম Truncate** | **RAKUB'20**-এ এক প্রশ্নে তিনটি জোড়াই | ★★★★★ |
| ৫ | **Functional dependency থেকে candidate key নির্ণয়; relation থেকে primary/candidate/super key** | **SJ'22-এ ২টি আলাদা প্রশ্ন** | ★★★★★ |
| ৬ | **Incremental বনাম differential backup — ব্যাংকিং সিস্টেমে কোনটা উপযুক্ত** | **SB'24**-এ হুবহু; **RAKUB'20**-এ "ডেটা না হারানোর উপায়"; SO'23-এও ০-bit data loss | ★★★★★ |
| ৭ | **ACID properties + case study দিয়ে সমাধান** | **RAKUB'20** · **SB'24** — দুই পত্রেই; SO'25-এও ACID | ★★★★★ |
| ৮ | **ডেটাবেজ normalize করা + ER Diagram আঁকা** | **SB'24**-এ হুবহু; **SJ'22**-এ BPL-এর ER diagram; SO'26-এও normalization | ★★★★★ |
| ৯ | **Constraint কী, কেন দরকার; table-level বনাম column-level constraint** | **RAKUB'20**-এ হুবহু | ★★★★★ |
| ১০ | **Weak entity বনাম strong entity — relation সহ** | **SJ'22**-এ হুবহু | ★★★★★ |
| ১১ | **ডুপ্লিকেট ডেটা খুঁজে বের করা + DDL ও DML ব্যাখ্যা** | **RAKUB'20**-এ হুবহু | ★★★★★ |
| ১২ | **Indexing কী, কোথায় ব্যবহার হয়** | **RAKUB'20**-এ হুবহু; SO'24-এও primary key–foreign key–indexing-এর সম্পর্ক | ★★★★★ |
| ১৩ | **RAID — কোন level সবচেয়ে ভালো ও কেন; ডেটাবেজে RAID-র প্রাসঙ্গিকতা** | **SB'24-এ ২টি আলাদা প্রশ্ন**; AME'23-এও RAID; ডেটাবেজ সার্ভারের সাথে সরাসরি জড়িত | ★★★★★ |
| ১৪ | **ক্লায়েন্ট অ্যাপ ও ডেটাবেজ সার্ভারের মধ্যে নিরাপদ যোগাযোগ নিশ্চিত করা (SSL/TLS)** | **SB'24**-এ হুবহু | ★★★★★ |
| ১৫ | **ডেটাবেজ টেবিল থেকে সুদের হার বের করার SQL/PL-SQL প্রোগ্রাম** | **SB'24**-এ হুবহু — ব্যাংকিং প্রেক্ষাপটে | ★★★★★ |
| ১৬ | **সার্ভার কেনার আগে কী কী যাচাই করবেন** | **SB'24**-এ হুবহু; Rupali ANE'23-এও সার্ভার হার্ডওয়্যার | ★★★★★ |
| ১৭ | **FCFS ও SJF scheduling — AWT ও ATAT নির্ণয়** | **SB'24**-এ হুবহু; SO'25 ও Officer(IT) '২৬-এও CPU scheduling | ★★★★★ |
| ১৮ | **Boolean expression-এর লজিক সার্কিট এঁকে নির্দিষ্ট ইনপুটে আউটপুট; সার্কিট থেকে truth table** | **SB'24-এ ২টি আলাদা প্রশ্ন** (Q = C̄ + ĀB + BC(B+C)‾ এবং 2-bit full adder) | ★★★★★ |
| ১৯ | **ধারার প্রোগ্রাম — `eˣ = 1 + x/1 + x²/2! + x³/3! + …`** | **SB'24**-এ হুবহু; **(১১১) ভাণ্ডারের সর্ববৃহৎ** | ★★★★★ |
| ২০ | **লাইব্রেরি ফাংশন ছাড়া string reverse** | **SJ'22**-এ হুবহু | ★★★★★ |
| ২১ | **Separate chaining দিয়ে hash function-এর অঙ্ক** | **SJ'22**-এ হুবহু; **BB AP'23**-এ linear probing | ★★★★★ |
| ২২ | **Distributed database কী** | **SJ'22**-এ হুবহু | ★★★★★ |
| ২৩ | **Linux command — লুকানো ফাইলসহ ডিরেক্টরি তালিকা** | **SJ'22**; **(৪৭) OS-র সর্ববৃহৎ** | ★★★★★ |
| ২৪ | **Classful থেকে classless IP ঠিকানায় যাওয়ার মূল কারণ** | **SB'24**-এ হুবহু; **(১০৯) ভাণ্ডারের সর্ববৃহৎ** | ★★★★★ |
| ২৫ | **ক্লায়েন্ট, ডেটাবেজ ও লগইন পেজসহ প্রোগ্রাম লেখা** | **SB'24**-এ হুবহু; SO'26-এও login ফ্লোচার্ট | ★★★★★ |
| ২৬ | **GK — GI পণ্য, ECNEC-এর কাজ, মূল্যস্ফীতি, Green বনাম Blue Economy, Westminster ব্যবস্থা** | **SB'24-এ ৫টি**; লিখিততে GK ২৫ হিট — ডেটাবেজের প্রায় সমান | ★★★★★ |
| ২৭ | **ব্যাখ্যামূলক বিজ্ঞান — ECG বনাম ECHO; "ট্রানজিস্টর পৃথিবী বদলে দিয়েছে"** | **SB'24-এ ২টি** — ADBA লিখিতে এই ঘরানার প্রশ্ন আসে | ★★★★★ |
| ২৮ | **বাংলা রচনা + ইংরেজি রচনা (পরিবেশ/সামাজিক/প্রযুক্তি)** | **SB'24-এ দুটোই** (পাণ্ডুলিপি সম্পাদনা; সড়কের পাশে বৃক্ষরোপণ) · **SJ'22-এ দুটোই** (প্রযুক্তির অপকারিতা; মাদকের ক্ষতি) | ★★★★★ |
| ২৯ | **ইংরেজি → বাংলা অনুবাদ** | **SB'24**; ×২ | ★★★★★ |

### খ. খুব বেশি সম্ভাবনা — কাছাকাছি পদে বা পুরো ভাণ্ডারে খুব ঘন

| # | যা আসবে | কেন | ★ |
|---|---|---|---|
| ৩০ | **Compiler বনাম Interpreter** | ×২; **৬ পরীক্ষায় হুবহু — লিখিত অংশের সবচেয়ে পুনরাবৃত্ত প্রশ্ন**; BPSC ADBA (ICT)'22-এও | ★★★★★ |
| ৩১ | **SQL Injection — কীভাবে হয়, কীভাবে ঠেকাবেন** | (১৯); **৩ পরীক্ষায় হুবহু**; DBA পদে সবচেয়ে প্রাসঙ্গিক নিরাপত্তা প্রশ্ন | ★★★★★ |
| ৩২ | **Multiplexing (TDM/FDM/WDM) ও PCM** | ×৩+×২; নেটওয়ার্ক লিখিতে ২৩ হিট | ★★★★ |
| ৩৩ | **Digital modulation — BPSK/QPSK/QAM constellation** | ×৩; (১০) | ★★★★ |
| ৩৪ | **CDMA/FHSS/DSSS; packet fragmentation ও tunneling** | ×২ প্রত্যেকটি | ★★★★ |
| ৩৫ | **Data warehouse বনাম data mining; OLTP বনাম OLAP** | (৯); SO'23-এ পরপর ৩টি BI প্রশ্ন | ★★★★ |
| ৩৬ | **Recursion দিয়ে প্রোগ্রাম ও আউটপুট** | ×৩; (৩৮) | ★★★★ |
| ৩৭ | **Sorting-এর trace ও complexity; dynamic programming** | ×২ প্রত্যেকটি | ★★★★ |
| ৩৮ | **CMOS ব্যাটারি ও BIOS; কম্পিউটার সংক্রান্ত পূর্ণরূপ** | ×২ প্রত্যেকটি; **(৫৯) সর্ববৃহৎ** | ★★★★ |
| ৩৯ | **Vector বনাম raster; color model; edge detection** | ×৩ — image-processing শুধু এই ঘরানাতেই দেখা গেছে | ★★★ |
| ৪০ | **OSI layer ও TCP বনাম UDP** | (৫২)+(১৭); প্রায় প্রতিটি ব্যাংক লিখিততেই | ★★★★ |

---

## যাচাইকরণ নোট

সব স্টার, সংখ্যা আর পরীক্ষার নাম `all-questions/`-এর ভেতরের আসল exam tag থেকে গোনা — কোনোটাই অনুমান করা নয়। Prediction অংশটা ঐতিহাসিক প্যাটার্ন থেকে করা পূর্বাভাস, নিশ্চয়তা নয়।
