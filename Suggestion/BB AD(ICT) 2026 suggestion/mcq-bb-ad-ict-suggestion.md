# Bangladesh Bank Assistant Director (ICT) 2026 — MCQ Suggestion

> Built **only** from the historical question bank in [`all-questions/`](../../all-questions/).
> Every "Appeared in" line below is copied from a real exam tag inside those files.
> Anything invented for practice is explicitly marked **🔮 Predicted**.

---

## Analysis Summary

### What was processed

| Item | Value |
|---|---|
| Source folder | `all-questions/` |
| `.md` files discovered | **50** — `mcq/` 24 topic files + `mcq/suggestion/mcq-question-count.md`, `written/` 24 topic files + `written/suggestion/written-question-count.md` |
| Files read end-to-end | **50 / 50** (no sampling, no skipping) |
| Total questions extracted | **5,910** |
| MCQ side (`all-questions/mcq/`) | **2,742** questions — IT 1,617 · General 1,125 |
| Written side (`all-questions/written/`) | **3,168** questions |
| Distinct exam sittings identified from tags | **350** |
| Year range covered by tags | **2011 – 2026** |

Year spread of tagged questions (whole bank): 2011:73 · 2012:53 · 2013:24 · 2015:28 · 2016:166 · 2017:87 · 2018:269 · 2019:504 · 2020:507 · 2021:1,393 · 2022:1,118 · 2023:730 · 2024:583 · 2025:427 · 2026:161.

This file covers the **MCQ paper only**, and is therefore driven by `all-questions/mcq/`. The written paper is handled in [`written-bb-ad-ict-suggestion.md`](written-bb-ad-ict-suggestion.md).

### Why AD(ICT) is the right target and what feeds it

Bangladesh Bank used to recruit **Assistant Programmer (AP)** and **Assistant Maintenance Engineer (AME)** through separate circulars. Those two posts are now merged into **Assistant Director (ICT)**. The historical dataset reflects exactly that lineage — it holds **359 Bangladesh Bank question records across 15 distinct BB sittings** (225 on the MCQ side, 134 on the written side):

| Bangladesh Bank sitting | Question records | Exam taker (ET) |
|---|---|---|
| **Assistant Director (ICT) 07.02.2025** | **56** (45 MCQ + 11 written) | **DU** |
| Assistant Programmer 03.02.2023 | 42 | BIBM |
| Assistant Maintenance Engineer 04.02.2023 | 40 | BIBM |
| Assistant Programmer 2011 | 38 | N/A |
| Assistant Maintenance Engineer 2011 | 35 | N/A |
| Assistant Programmer 2016 | 25 | N/A |
| Assistant Director (IT) 2016 | 25 | N/A |
| Senior Officer (IT), Grade-9 (Job ID-25104) 2024 | 24 | N/A |
| Recruitment Test 2020 | 19 | N/A |
| Assistant Maintenance Engineer 2013 | 13 | N/A |
| Data Entry Operator (IT) 2020 | 11 | N/A |
| Assistant Programmer 2019 | 9 | DU |
| Assistant Maintenance Engineer 2019 | 9 | BUET |
| Assistant Maintenance Engineer 2017 | 8 | N/A |
| Assistant Maintenance Engineer 2016 | 6 | N/A |

**The single most important paper in this whole bank is `Bangladesh Bank Assistant Director (ICT) 07.02.2025 (ET: DU)`** — the only sitting of the merged post that exists in the data, set by Dhaka University. Its 45 MCQ records break down as:

| Subject file | AD(ICT) 2025 MCQs |
|---|---|
| `database.md` | 6 |
| `electrical-and-electronics.md` | 6 |
| `gk.md` | 5 |
| `math.md` | 5 |
| `computer-network-security.md` | 4 |
| `data-structure.md` | 4 |
| `software-engineering.md` | 3 |
| `c-programming.md` | 2 |
| `dld.md` | 2 |
| `oop.md` | 2 |
| `web-technology.md` | 2 |
| `algorithm.md`, `cloud-computing.md`, `computer-networks.md`, `operating-system.md` | 1 each |

### The three findings that shaped this suggestion

**1. The DU setter repeats the same concept twice inside one paper.** In the AD(ICT) 07.02.2025 MCQ paper these pairs are both present:

* *"Digital Signature uses which algorithm?"* **and** *"Digital signature uses which algorithm for encryption?"*
* *"Which algorithm is used in email security?"* **and** *"What kind of encryption is used for securing emails in transit?"*
* *"Which data structure is preferred for Priority Queue?"* **and** *"What is the best way to implement priority queue?"*
* *"What is the Work of a Rectifier?"* **and** *"Which device is need to converts AC to DC?"*
* *"Zener diode is a _____ conducting device."* **and** *"What should be true for a Zener Diode?"*
* *"Which of the following is a DML command?"* **and** *"Which of the following is a command of Data Definition Language (DDL)?"*

Where the setter doubles up, the topic is being *emphasised*, not sampled. Those six pairs are the spine of Tier 1.

**2. Bank-sector MCQs are recycled verbatim across sittings.** A worked example that already reached AD(ICT): *"Which one is a Universal logic gate?"* carries four separate exam tags in `mcq/dld.md` — **Bangladesh Bank Assistant Director (ICT) 07.02.2025**, Probashi Kallyan Bank Assistant Programmer 2018, Combined Bank Maintenance Engineer 2018, Sonali Bank Limited Assistant Programmer 2016.

**3. Electrical/electronics is not optional.** 6 of 45 AD(ICT) 2025 MCQs came from `electrical-and-electronics.md` — the joint-highest share with database. That is the AME half of the merged post showing up. Any CSE-only preparation loses those marks outright.

### Mark distribution being targeted

MCQ paper is **100 marks in 1 hour**, split **IT 75 · Math 15 · GK 10**, and it is a **gate** — the written script is not evaluated if the MCQ is not passed. Tiering below is weighted accordingly.

---

## 🔥 Tier 1 — Must Study

Highest-confidence items. Every one of these is either a verbatim AD(ICT) 2025 question, or a concept the AD(ICT) 2025 paper asked twice.

---

### T1.1 — Digital signature: which algorithm, and which key class

**Question (historical, verbatim):**
> **Digital Signature uses which algorithm?** — (a) AES (b) RSA (c) DES (d) Diffie-Hellman
>
> **Digital signature uses which algorithm for encryption?** — (a) Symmetric Key Algorithm (b) Asymmetric Key Algorithm (c) Hashing Algorithm only (d) Stream Ciphe

* **Priority:** Highest
* **Type:** Historical Repeat (same paper, asked twice)
* **Historical evidence:** Both in `mcq/computer-network-security.md` → *Cryptography (17)*, both tagged **Bangladesh Bank Assistant Director (ICT) 07.02.2025**. Across the whole MCQ folder only **4** questions mention digital signature at all — **2 of those 4 are this one paper.**
* **Related variations to study:** *"In an asymmetric key encryption process, the key used to encrypt the data is known as a—"* (Sonali & Janata Bank Assistant DBA 25-09-2021); *"Laili digitally signs a message and sends it to Mojnu. Verification of the signature by Mojnu requires—"* (Rupali Bank Ltd. ANE 2021); *"Digital signature is a cryptographic method that ensures—"* (Combined 4 Bank AP 2020); *"Which of the following is the role of Certification Authority (CA)…"* (Sonali, Janata and RAKUB AE (IT)/AHME/AME 2020).

---

### T1.2 — Email security: algorithm and transit encryption

**Question (historical, verbatim):**
> **Which algorithm is used in email security?** — (a) AES (b) RSA (c) SHA (d) All of the above
>
> **What kind of encryption is used for securing emails in transit?** — (a) Symmetric Encryption (b) Asymmetric Encryption (c) TLS (Transport Layer Security) (d) Hashing

* **Priority:** Highest
* **Type:** Historical Repeat (same paper, asked twice)
* **Historical evidence:** `mcq/computer-network-security.md` → *Cryptography (17)* and *Email Security & Spam (2)*. The Email Security subtopic has only **2** questions in the entire MCQ folder and **one of them is AD(ICT) 2025**.
* **Related variations to study:** SSL → TLS evolution (*"Which of the following statements is false with respect to SSL?"*, Sonali Bank and BDBL SO(IT) 25.09.2021); Diffie-Hellman shared key `K = G^xy mod N` (same sitting); *"What is/are the main operation of SSL/TLS?"* (Sonali, Janata and RAKUB 2020).

---

### T1.3 — Priority queue is implemented with a heap

**Question (historical, verbatim):**
> **Which data structure is preferred for Priority Queue?** — (a) Heap Tree (b) Graph (c) Stack (d) Table
>
> **What is the best way to implement priority queue?** — (a) Array (b) Linked List (c) Heap (d) Stack

* **Priority:** Highest
* **Type:** Historical Repeat (same paper, asked twice)
* **Historical evidence:** `mcq/data-structure.md` → *Priority Queue & Heap (3)*. That subtopic contains exactly **3** questions bank-wide and **2 of the 3 are AD(ICT) 2025**. The third is *"In the priority queue, insertion and deletion take place at –"* (Sonali, Janata & Rupali Bank SO (AHE)/AE(IT)/AME 25.10.2021).
* **Related variations to study:** max-heap root position (*"Max-Heap data structure এর সবচেয়ে বড় নম্বরটি কোথায় থাকে?"* — BPSC AP (Dept. of ICT) 2020 **and** BPSC Assistant Network Engineer 2019, i.e. already a 2-sitting repeat); array representation of a heap (children of node n = 2n, 2n+1 — Sonali Bank Ltd. Assistant DBA 2020).

---

### T1.4 — Rectifier converts AC to DC

**Question (historical, verbatim):**
> **What is the Work of a Rectifier?** — (a) Converts DC to AC (b) Converts AC to DC (c) Stores Electrical Energy (d) Increases Voltage
>
> **Which device is need to converts AC to DC?** — (a) Transformer (b) Rectifier (c) Inverter (d) Amplifier

* **Priority:** Highest
* **Type:** Historical Repeat (same paper, asked twice — mirror-image framing)
* **Historical evidence:** `mcq/electrical-and-electronics.md` → *Diodes & Rectifiers (4)*. **All 4 questions in that subtopic are from Bangladesh Bank AD(ICT) 07.02.2025.** No other sitting in the entire MCQ folder contributes to it.
* **Related variations to study:** full-wave rectifier efficiency 81.2% (BDCCL Assistant Manager (Transmission) 2022, tagged twice); *"নিচের কোন ইলেকট্রনিক্স যন্ত্র AC থেকে DC তৈরি করতে পারে?"* (BTRC Sub-Assistant Director (Tech.) 2021).

---

### T1.5 — Zener diode: direction and operating region

**Question (historical, verbatim):**
> **Zener diode is a _____ conducting device.** — (a) Unidirectional (b) Bidirectional (c) Multidirectional (d) Tri-directional
>
> **What should be true for a Zener Diode?** — (a) Reverse bias for amplifying (b) Operates in forward bias only (c) Works in reverse breakdown region (d) Used for rectification

* **Priority:** Highest
* **Type:** Historical Repeat (same paper, asked twice)
* **Historical evidence:** Same *Diodes & Rectifiers (4)* subtopic as T1.4 — all four AD(ICT) 2025.
* **Related variations to study:** *"ব্রেকডাউন ঘটলে জিনার ডায়োডের ক্ষেত্রে কোনটি প্রায় অপরিবর্তিত থাকে?"* (BDCCL Assistant Manager (Transmission) 2022, appears under two tags); depletion-layer formation timing (same sitting).

---

### T1.6 — DDL vs DML vs DCL classification of SQL commands

**Question (historical, verbatim):**
> **Which of the following is a DML (Data Manipulation Language) command?** — (a) CREATE (b) DELETE (c) DROP (d) ALTER
>
> **Which of the following is a command of Data Definition Language (DDL)?** — (a) SELECT (b) INSERT (c) UPDATE (d) CREATE

* **Priority:** Highest
* **Type:** Historical Repeat (same paper, asked twice) + Recurring Concept
* **Historical evidence:** `mcq/database.md` → *SQL Commands & Queries (52)*, the largest database subtopic in the MCQ folder. Beyond AD(ICT) 2025 the same classification is asked by: Combined Bank Officer (IT) 04.10.2024 (twice — *"Which statements are used to create the database structure?"*, *"Which of the following is not a DDL statement?"*), NPCBL Executive Trainee (Software) 2023 **and** Combined 3 Bank AP 2018 (same `CREATE TABLE employee(...)` stem, 2 sittings), BPSC (Ministry) AP 21.09.2022, Sonali, Janata & Rupali Bank SO 25.10.2021, Sonali and Janata Bank Assistant DBA 25.09.2021, Sonali Bank Ltd. Assistant DBA 2020 (`GRANT` = DCL), BREB Assistant Junior Engineer (IT) 2019.
* **Related variations to study:** `GRANT`/`REVOKE` = DCL; `COMMIT`/`ROLLBACK`/`SAVEPOINT` = TCL; `TRUNCATE` is DDL not DML; **clause execution order** — *"Which clause is executed first in an SQL query?"* is also an AD(ICT) 2025 question (answer: FROM).

---

### T1.7 — Universal logic gate

**Question (historical, verbatim):**
> **Which one is a Universal logic gate?** — (a) NAND (b) AND (c) OR (d) NOT

* **Priority:** Highest
* **Type:** Historical Repeat (**4 sittings, verbatim**)
* **Historical evidence:** In `mcq/dld.md` → *Logic Gates & Universal Gates (16)* this single question carries four tags:
  * Bangladesh Bank Assistant Director (ICT) 07.02.2025
  * Probashi Kallyan Bank Assistant Programmer 2018
  * Combined Bank Maintenance Engineer 2018
  * Sonali Bank Limited Assistant Programmer 2016
* **Related variations to study:** *"Universal logic gate is: (d) NAND, NOR"* (BREB AP 2023); *"Which is the universal gate?"* (BREB AGM (IT) 2016); *"NAND gates are preferred over other because these ______"* (**Bangladesh Bank AME 2011**); *"What is the lowest number of NAND gates required to make an inverter?"* (Combined Bank Officer (IT) 04.10.2024).

---

### T1.8 — 2's complement of a hex/binary number

**Question (historical, verbatim):**
> **What is the 2's complement of (65)₁₆ number?** — (a) 10011011 (b) 10011010 (c) 00011011 (d) 10011100

* **Priority:** Highest
* **Type:** Recurring Concept + Historical Repeat
* **Historical evidence:** `mcq/dld.md` → *Number Systems & Binary Arithmetic (**45**)*, the single largest MCQ subtopic in the DLD file. The 2's-complement family alone: **Bangladesh Bank AD(ICT) 07.02.2025** (this one), **Bangladesh Bank AME 04.02.2023** (*"The greatest negative number … 8-bits … 2's complement …"*), BREB AP 2023 (*"Find out 2's complement value of 11100101"*), BPSC (Ministry) AME 2022 (*"(11111111)₂ in 2's complement form"*), BPSC AP (Dept. of ICT) 2020 (*"10000000 এর … 2's complement ফরম্যাটের মান কত (৮ বিট)?"*).
* **Related variations to study:** all base conversions (dec↔bin↔oct↔hex), nibble = 4 bits, ASCII-8 = 256 symbols, Unicode = 16 bits, largest value in n bits, BCD = 4 bits. These are the highest-density, lowest-effort marks on the whole paper.

---

### T1.9 — Stack: applications and LIFO

**Question (historical, verbatim):**
> **Which one of the following is an application of Stack Data Structure?** — (a) Managing function calls (b) The stock span problem (c) Arithmetic expression evaluation (d) All of the above

* **Priority:** Highest
* **Type:** Recurring Concept (bank-wide) + AD(ICT) 2025 hit
* **Historical evidence:** `mcq/data-structure.md` → *Stack & Queue (**23**)*. Stack-family MCQs recur across Bangladesh Bank itself: **AD(ICT) 07.02.2025** (this), **BB AP 2016** three times (*"Which is correct for stack?"*, *"Find the correct arranged data after stack operation push(1), push(2), pop, …"*, *"Stack operations are—"*), **BB AP 03.02.2023** (*"Which data structure allows insertion and deletion of elements from both ends?"* → Deque). Outside BB: *"The term push and pop related to –"* recurs across Combined Bank ME 2018, Sonali Bank Ltd. AE(IT) 2016 and Probashi Kallyan Bank Programmer 2019.
* **Related variations to study:** infix → postfix/prefix conversion (`a+(b-c)*d` appears in Sonali, Janata & Rupali Bank SO 25.10.2021 **and** Sonali Bank Ltd. Assistant DBA 2020); balanced-parenthesis checking; minimum 2 stacks to implement a queue (Combined Bank Officer (IT) 04.10.2024); stack overflow/underflow.

---

### T1.10 — CIDR value + subnet mask for a required host count

**Question (historical, verbatim):**
> **An IP address is given 192.168.3.0, need to 254 useable host. What is the CIDR value and subnet mask?** — (a) 255.255.255.0 (b) 255.255.255.128 (c) 255.255.255.192 (d) 255.255.254.0

* **Priority:** Highest
* **Type:** Recurring Concept (the densest topic in the whole networks file)
* **Historical evidence:** `mcq/computer-networks.md` → *Subnetting & IP Addressing (33)*; on the written side `written/computer-networks.md` → *Subnetting & IP Addressing (**109**)* — the largest single subtopic in the entire 5,910-question bank. Bangladesh Bank alone has asked subnetting at **AD(ICT) 07.02.2025**, **AP 03.02.2023** twice (*"How many address is there 200.10.10.10/20"*, *"Which is suitable subnet mask for 200 host?"*), **AME 04.02.2023** (*"Which of the following cannot be used as a public IP address?"*, itself repeated at Rupali Bank ANE 2021), **AP 2016**, and **AME 2017** on the written side.
* **Related variations to study:** *"To divide a class C network into a maximum of 14 subnets – each capable of having up to 14 hosts"* — a **3-sitting verbatim repeat** (Combined Bank ME 2018, Probashi Kallyan Bank Programmer 2019, Sonali Bank Ltd. AE(IT) 2016); private ranges 10/8, 172.16/12, 192.168/16; loopback 127.0.0.1 (repeated across Probashi Kallyan Bank AP 2018, Sonali Bank Ltd. AP 2016, Sonali & Janata Bank Officer (IT/ICT) 2019, Sonali/Janata/Rupali 25.10.2021, Janata Bank ANE (SO) 2020).

---

## ⭐ Tier 2 — High Priority

Strong candidates: single AD(ICT) 2025 hits backed by wide cross-exam recurrence, or heavy multi-sitting recurrence without an AD(ICT) hit yet.

| # | Question / concept | Type | Historical evidence |
|---|---|---|---|
| T2.1 | **ACID — which property is violated when A debits but B never credits?** (*A to B transfer balance but not sent to B? Which property in ACID is responsible?* → Atomicity) | AD(ICT) 2025 + recurring | `mcq/database.md` → *Transaction Management & ACID (14)*. Also: Combined Bank Officer (IT) 04.10.2024, NPCBL ET (Software) 2023, BCC AP 11.11.2023, Sonali/Janata/Rupali SO 25.10.2021 **and** Janata Bank ANE (SO) 2020 (same *"Which one is not Database Transaction property?"* stem, 2 sittings), Janata Bank ANE (SO) 2020 (Durability), Combined 4 Bank AP 2020 (Atomicity). Banking scenario framing is the AD(ICT) signature. |
| T2.2 | **Indexing makes database reads faster** (*Which one make data access from a database faster?*) | AD(ICT) 2025 + recurring | `mcq/database.md` → *Indexing & Query Optimization (6)*; written side *Indexing & Query Optimization (B-Tree, B+ Tree) (10)*. Also Sonali & Janata Bank Assistant DBA 25-09-2021 (three separate index questions), Combined Bank ME 2018 (*"Which data structure is used for indexing?"* → B+ tree). |
| T2.3 | **SQL clause execution order** (*Which clause is executed first in an SQL query?* → FROM) | AD(ICT) 2025 | `mcq/database.md` → *SQL Commands & Queries (52)*. Study the full logical order FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY, plus `WHERE` vs `HAVING` (Combined 3 Bank AP 2018). |
| T2.4 | **Process state on I/O request** (*A process needs I/O operations, it switches to _____* → Waiting/Blocked) | AD(ICT) 2025 + recurring | `mcq/operating-system.md` → *Process Management & Scheduling (24)*. Also Sonali Bank Ltd. Assistant DBA 2020 (*"Which is not the state of a process…"*), Janata Bank Ltd. AE (IT) 2015 (*"…not the state of a process in PCB?"*), turnaround-time definition asked by Sonali Bank Ltd. Assistant DBA 2020 **and** Janata Bank AE (IT) 2015. |
| T2.5 | **Integration testing tests the interface between modules** | AD(ICT) 2025 (**tag appears twice on the one question**) + recurring | `mcq/software-engineering.md` → *Software Testing (20)*, the largest SE subtopic. Also Combined Bank Officer (IT) 04.10.2024 (*"Objective of integration testing is to find _____"* → interface error). Alpha/Beta/Regression/Usability/Smoke definitions recur across Pubali Bank SQA 18.03.2023 (5 questions), Combined 4 Bank AP 2020, Janata Bank ANE (SO) 2020, Sonali/Janata/RAKUB 2020, Probashi Kallyan Bank 2019 ×4. |
| T2.6 | **Waterfall model's major drawback** (inflexible to changing requirements) | AD(ICT) 2025 + recurring | `mcq/software-engineering.md` → *SDLC Models (14)*. Also **Bangladesh Bank AME 04.02.2023** (*"How many steps in waterfall model?"*), Probashi Kallyan Bank Programmer 2019 (waterfall phase naming), Sonali Bank Ltd. AE(IT) 2016 (prototype model). |
| T2.7 | **Encapsulation — what breaks it** (*Which of the following does NOT achieve encapsulation?* → global variables) | AD(ICT) 2025 + recurring | `mcq/oop.md` → *Encapsulation & Access Modifiers (7)*. The exact same idea is asked as *"Encapsulation এর মাধ্যমে OOP এর কোন বৈশিষ্ট্যটি নিশ্চিত হয়?"* by BPSC AP (Dept. of ICT) 2020 **and Bangladesh Bank Data Entry Operator (IT) 2020**; and *"Which variable violates the principle of encapsulation?"* → global variable (BCC AP 11.11.2023). |
| T2.8 | **Operator overloading — which operator prefers a global (friend) function** (`<<` insertion operator) | AD(ICT) 2025 + recurring | `mcq/oop.md` → *Polymorphism & Overloading (16)*. Also **Bangladesh Bank AP 03.02.2023** (*"Which of the following operators cannot be overloaded in C/C++?"*), Sonali & Janata Bank Officer (IT/ICT) 2019 ×3, Probashi Kallyan Bank AP 2018, **Bangladesh Bank AP 2011** (*"Overloaded functions are ______"*). |
| T2.9 | **HTTP status code 500 = Internal Server Error** | AD(ICT) 2025 | `mcq/web-technology.md` → *HTTP & Status Codes (5)*. On the written side the same family is a **cross-organisation repeat**: *"What do the following specific HTTP status codes mean … (a) 200 (b) 403 (c) 503"* appears under **Bangladesh Bank Senior Officer (IT), Grade-9 2024** *and* SO IT 25-07-2026. Memorise 200/201/301/302/400/401/403/404/500/502/503. |
| T2.10 | **Which is not a web server** (Apache Tomcat / Jetty / Tornado are; PHP is not) | AD(ICT) 2025 | `mcq/web-technology.md` → *Full Stack & Web Servers (5)*. Supporting: WAF blocks SQLi between client and web server (Sonali Bank and BDBL SO(IT) 25.09.2021); Java servlet invoked over HTTP (Sonali & Janata Bank Assistant DBA 25-09-2021). |
| T2.11 | **Docker vs Docker Hub** (container platform vs cloud image repository) | AD(ICT) 2025 | `mcq/cloud-computing.md` → *Containers & Virtualization (2)* — only 2 questions exist and one is AD(ICT) 2025. The other is *"Which software is mostly used for virtualization?"* → VMware, itself a **2-sitting repeat** (Combined Bank ME 2018 + Sonali Bank Ltd. AE(IT) 2016). |
| T2.12 | **Linear search vs binary search — the real advantage** (works whether or not the array is sorted) | AD(ICT) 2025 + recurring | `mcq/algorithm.md` → *Searching Algorithms (18)*. Also **Bangladesh Bank AP 03.02.2023** (*"…not the required condition for a binary search algorithm?"*), **Bangladesh Bank AME 2013** (*"For a sorted linear array, which is the fastest algorithm to find the location?"*), plus *"The complexity of Binary search algorithm is-"* as a 2-sitting repeat (Combined Bank SO(IT) 2018 + Probashi Kallyan Bank AP 2018). |
| T2.13 | **Sorted insertion into a linked list is Θ(n²)** | AD(ICT) 2025 + **3-sitting repeat** | `mcq/data-structure.md` → *Linked List (10)*. The identical problem is tagged **Bangladesh Bank AD(ICT) 07.02.2025**, 6 Banks & FI AP 18.03.2021, and Janata Bank ANE (SO) 2020. |
| T2.14 | **Inductance depends on turns, permeability and cross-section** | AD(ICT) 2025 + recurring | `mcq/electrical-and-electronics.md` → *Circuits & Components (83)*, the largest EEE subtopic. Mirror question *"ইন্ডাক্টরের ইন্ডাক্টেন্স নিম্নের কোনটির উপর নির্ভর করে না?"* is tagged twice under BDCCL Assistant Manager (Transmission) 2022. |
| T2.15 | **Parallel resistors + total current** (10Ω ∥ 20Ω ∥ 30Ω across 60 V → 11 A) | AD(ICT) 2025 + recurring | `mcq/electrical-and-electronics.md` → *Circuits & Components (83)*. Also **Bangladesh Bank AME 04.02.2023** (*"Two resistors R1 and R2 connected in parallel with R1 < R2…"*), BTRC Sub-AD (Tech.) 2021 (bulb resistance from W and V), BTRC Sub-AD (Tech.) 2019 (12 Ω wire cut and paralleled), BPSC Senior Instructor (MEW) 2021. |

---

## 📌 Tier 3 — Medium Priority

Well-supported by the data but one step below in target relevance.

| # | Concept | Historical evidence (from `all-questions/mcq/`) |
|---|---|---|
| T3.1 | **Memory hierarchy speed order** (Register > Cache > RAM > SSD > HDD) | *Memory Hierarchy (28)* in `microprocessor-and-computer-architecture.md`. **Bangladesh Bank Assistant Director (IT) 2016 contributed 5 memory questions** to this file; also Combined Bank Officer (IT) 04.10.2024, Pubali Bank Hardware Engineer 18.03.2023, and *"Which is the faster memory?"* as a 2-sitting repeat (DESCO AE(CSE) 2016 + BREB AGM(IT) 2016). |
| T3.2 | **SRAM vs DRAM (flip-flop vs refresh)** | Rupali Bank ANE 2021, **Bangladesh Bank Assistant Director (IT) 2016** (*"Which of the following memories needs refreshing?"*). |
| T3.3 | **CPU registers: PC, IR, MAR, Accumulator, ALU** | *CPU & Registers (35)*. **Bangladesh Bank Assistant Director (IT) 2016** ×3 (word length in bits, CPU = ALU + CU, control-unit function); Pubali Bank Hardware Engineer 18.03.2023; BPSC AP (Dept. of ICT) 2020. |
| T3.4 | **RISC vs CISC at the same clock** | 2-sitting repeat (Combined Bank ME 2018 + Sonali Bank Ltd. AE(IT) 2016) and **Bangladesh Bank AME 2013**. |
| T3.5 | **OSI has 7 layers / TCP-IP layer count & PDUs** | *OSI & TCP-IP Model (16)*. **Bangladesh Bank AP 2016** (*"Which is not work of Data link layer?"*), **BB AME 2013** (end-to-end delivery = transport). *"How many layers Internet protocol suite?"* is a 2-sitting repeat (Combined Bank ME 2018 + Sonali Bank Ltd. AE(IT) 2016). |
| T3.6 | **Email protocols SMTP / POP3 / IMAP** | *Application Layer Protocols (58)* — the biggest networks subtopic. **BB AME 2011** (*"What is SMTP?"*). *"POP3 is a protocol for-"* recurs (Sonali & Janata Bank Officer (IT/ICT) 2019 + Sonali Bank Ltd. AE(IT) 2016); *"Email is a protocol of the following layer?"* likewise (Combined Bank ME 2018 + Sonali Bank Ltd. AE(IT) 2016). |
| T3.7 | **Port numbers** (HTTP 80, HTTPS 443, FTP 21, SSH 22, Telnet 23, SMTP 25, DNS 53, Oracle 1521) | Combined Bank Officer (IT) 04.10.2024 (443), BREB AP 2023 (1521, 21), BPSC (Ministry) AP 21.09.2022 (53), Janata Bank ANE (SO) 2020 (80), Pubali Bank Officer (IT) 2012 (21). |
| T3.8 | **DHCP full form + dynamic IP assignment** | *"DHCP means?"* / *"Which protocol dynamically assigns IP addresses?"* across Sonali/Janata/Rupali SO 25.10.2021, Janata Bank ANE (SO) 2020, 6 Banks & FI AP 18.03.2021 + Sonali/Janata/RAKUB 2020 (2-sitting repeat), BPSC (Ministry) AME 2022, Sonali & Janata Bank Officer (IT/ICT) 2019. |
| T3.9 | **IPv6 = 128 bits** | 3-sitting verbatim repeat (BPSC (Ministry) AME 2022, BPSC AME 2019, Combined Bank SO(IT) 17.05.2024) plus **Bangladesh Bank AP 03.02.2023** (IPv4-in-IPv6 = tunneling) and 8 more sittings across `computer-networks.md`. |
| T3.10 | **Network devices: hub / switch / bridge / router / repeater, collision vs broadcast domain** | *Network Devices & Configuration (38)*. **Bangladesh Bank AME 04.02.2023** (Cisco IOS `copy tftp flash`), **BB AP 2016** (*"Server machine is connected to—"*), Sonali Bank and BDBL SO(IT) 25.09.2021 (switch port = separate collision domain), Rupali Bank ANE 2021 ×3. |
| T3.11 | **CIA triad = Confidentiality, Integrity, Availability** | *Security Principles (CIA Triad) (5)*: Combined 4 Bank AP 2020 (*"Cyber security Triad means-"*), Combined Bank Officer (IT) 04.10.2024. |
| T3.12 | **Attack families: DoS, MITM, phishing, SQL injection, rootkit, steganography** | *Cyber Attacks & Threats (20)*. Note the bank-specific item: *"The Bangladesh Bank robbery … February 2016 … engaged ______ to lead the security incident response"* → World Informatix Cyber Security (Sonali, Janata and RAKUB 2020). *"How can we prevent SQL Injection Attack?"* is a 2-sitting repeat (Janata Bank ANE (SO) 2020 + Sonali/Janata/Rupali SO 25.10.2021). |
| T3.13 | **Cloud service models IaaS / PaaS / SaaS + virtualization = resource pooling** | *Cloud Computing Fundamentals (14)* + *Cloud Service Models (4)*. **Bangladesh Bank AME 04.02.2023 contributed 5 of these questions** — the strongest single-sitting concentration in the cloud file. *"Which one is not a layer of cloud computing?"* is a 2-sitting repeat (Sonali/Janata/Rupali 25.10.2021 + Sonali/Janata/RAKUB 2020). |
| T3.14 | **Java: `new` creates the object; source compiles to bytecode; JVM/JDK/JRE** | *Java Programming (48)*, the largest OOP subtopic. *"In Java, which operator is used to create an object?"* is a **5-sitting verbatim repeat** (Combined Bank ME 2018, Probashi Kallyan Bank AP 2018, Probashi Kallyan Bank AP 2019, Sonali Bank Ltd. AE(IT) 2016, Sonali Bank Ltd. AP 2016). **Bangladesh Bank AP 2011** asked Java keywords and `java.lang.Runnable`. |
| T3.15 | **C output tracing: `++`/`--`, integer division, `%c` vs `%d`, `sizeof`** | *Output Tracing (36)*, the largest C subtopic. **Bangladesh Bank AD(ICT) 07.02.2025** has 2 such questions; **BB AP 03.02.2023** has 3 (`i=i++`, `malloc` struct, `sizeof(i++)`); **BB AP 2011** has 1 (`const int i; i++`). |
| T3.16 | **Complexity table** (bubble/selection/insertion O(n²); merge/heap O(n log n); quick worst O(n²); binary search O(log n)) | *Sorting Algorithms (20)* + *Searching Algorithms (18)*. **Bangladesh Bank AP 03.02.2023** (merge sort O(n log n)), **BB AP 2016** (*"Which is the slowest algorithm?"*). *"The complexity of Bubble sort algorithm is-"* is a 2-sitting repeat (Combined Bank ME 2018 + Probashi Kallyan Bank AP 2019). |
| T3.17 | **Math — the exact five AD(ICT) 2025 types** | `mcq/math.md`: percentage-of-salary remainder (→ 30,000); two pipes 4 h + 6 h → 2.4 h; father 36 / son 16 → 6 years ago; 5 m N + 3 m E + 2 m S → 4.24 m; 8 balls one heavier → 2 weighings. These are ordinary bank-math types, and 15 of 100 MCQ marks ride on them. |
| T3.18 | **GK — the AD(ICT) 2025 mix** | 5 questions, all "one recent + one classic": highest peak of Bangladesh (Saka Haphong); Nobel Peace Prize 2024 (Nihon Hidankyo); Strasbourg → France; Suez Canal joins Mediterranean & Red Sea; first ICC ODI World Cup winning captain (Clive Lloyd). `mcq/gk.md` → *Bangladesh Affairs (171)* + *International Affairs (103)*. |

---

## 🔁 Repeated MCQs

Strongest exact / near-exact repeats in `all-questions/mcq/`, quoted in their original wording.

| Repeats | Question (verbatim) | Sittings |
|---|---|---|
| **5** | *"In Java, which operator is used to create an object?"* | Combined Bank ME 2018 · Probashi Kallyan Bank AP 2018 · Probashi Kallyan Bank AP 2019 · Sonali Bank Ltd. AE(IT) 2016 · Sonali Bank Ltd. AP 2016 |
| **4** | *"Which one is a Universal logic gate?"* | **Bangladesh Bank AD(ICT) 07.02.2025** · Probashi Kallyan Bank AP 2018 · Combined Bank ME 2018 · Sonali Bank Ltd. AP 2016 |
| **4** | *"What is the output of this Java program?"* (`class Test{int i;} … System.out.println(t.i);`) | Combined Bank AP 09.02.2024 · Combined 4 Bank AP 2020 · 6 Banks & FI AP 18.03.2021 · Sonali Bank Ltd. Assistant DBA 2020 |
| **3** | *"Suppose you have an 8-bit binary number N. Which of the following operations does not change its lower 4 bits?"* | Sonali/Janata/Rupali SO 25.10.2021 · 6 Banks & FI AP 18.03.2021 · Janata Bank ANE (SO) 2020 |
| **3** | *"How long is an IPv6 address?"* | Combined Bank SO(IT) 17.05.2024 · BPSC (Ministry) AME 2022 · BPSC AME 2019 |
| **3** | *"A relationship is given below in an ER diagram. How many tables can be created (preferred) from below diagram?"* | Combined 4 Bank AP 2020 · Janata Bank ANE (SO) 2020 · Sonali Bank Ltd. Assistant DBA 2020 |
| **3** | *"In SQL, the ______ command is used to recompile a view."* | Sonali & Janata Bank Officer (IT/ICT) 2019 · Probashi Kallyan Bank AP 2019 · Sonali Bank Ltd. AE(IT) 2016 |
| **3** | *"To divide a class C network into a maximum of 14 subnets – each capable of having up to 14 hosts, the subnet mask used should be:"* | Combined Bank ME 2018 · Probashi Kallyan Bank Programmer 2019 · Sonali Bank Ltd. AE(IT) 2016 |
| **3** | *"Which of the standard protocol for network management features?"* (→ SNMP) | Sonali & Janata Bank Officer (IT/ICT) 2019 · Probashi Kallyan Bank AP 2019 · Sonali Bank Ltd. AE(IT) 2016 |
| **3** | *"A path for carrying signals between a source and a destination is known as—"* (→ Channel) | Sonali & Janata Bank Officer (IT/ICT) 2019 · Probashi Kallyan Bank AP 2019 · Sonali Bank Ltd. AE(IT) 2016 |
| **3** | *"What is the correct output of the following C program statements?"* (`int array[]={6,7,8,…}, *p=array+5; printf("%d\n",p[1]);`) | Rupali Bank ANE 2021 · 6 Banks & FI AP 18.03.2021 · Janata Bank ANE (SO) 2020 |
| **3** | *"What is the worst case time complexity of inserting n elements into an empty linked list, if the linked list needs to be maintained in sorted order?"* | **Bangladesh Bank AD(ICT) 07.02.2025** · 6 Banks & FI AP 18.03.2021 · Janata Bank ANE (SO) 2020 |
| **2** | *"Table Employee has 10 records. It has a non-NULL SALARY column which is also UNIQUE. The SQL statement SELECT COUNT(\*) …"* (ALL vs ANY variant) | **Bangladesh Bank AP 03.02.2023** · 6 Banks & FI AP 18.03.2021 |
| **2** | *"Which of the following pairs is an example of intra-domain routing protocols?"* (→ OSPF, RIP) | **Bangladesh Bank AME 04.02.2023** · BPSC (Ministry) AME 2022 |
| **2** | *"The complexity of Bubble sort algorithm is-"* | Combined Bank ME 2018 · Probashi Kallyan Bank AP 2019 |
| **2** | *"According to Boolean algebra the value of: (A + AB)·(B + AB) is-"* | Sonali Bank Ltd. AE(IT) 2016 · Combined Bank ME 2018 |
| **2** | *"What is postfix expression of the string, a+(b-c)\*d?"* | Sonali/Janata/Rupali SO 25.10.2021 · Sonali Bank Ltd. Assistant DBA 2020 |

**Reading of this table:** BB reuses items from the wider bank-sector pool (`Combined Bank`, `Sonali`, `Janata`, `Rupali`, `Probashi Kallyan`, `6 Banks & FI`), and AD(ICT) 2025 already pulled three of these repeats. Solving the bank-sector MCQ pool is not a substitute for BB papers — it is a direct feeder to them.

---

## 🧩 Recurring MCQ Concepts

Concepts asked repeatedly through *different* questions.

**C1 — Cryptography key-type family.** Only 13 MCQs in the folder touch symmetric/asymmetric/RSA/AES/public-private keys — and **4 of the 13 are Bangladesh Bank AD(ICT) 07.02.2025**. Variations seen: RSA is asymmetric (BPSC (Ministry) AP 21.09.2022); a symmetric system uses only the private key (Sonali Bank and BDBL SO(IT) 25.09.2021); the encryption key in asymmetric is the public key (Sonali & Janata Bank Assistant DBA 25-09-2021); verifying Laili's signature needs Laili's public key (Rupali Bank ANE 2021); MD5 is not an encryption algorithm (Combined 4 Bank AP 2020); Vigenère cipher (Combined 4 Bank AP 2020); Diffie-Hellman `K = G^xy mod N` (Sonali Bank and BDBL SO(IT) 25.09.2021). **Prepare to be asked all of: which is symmetric, which is asymmetric, which is hashing, which key signs, which key verifies.**

**C2 — Normal form ↔ dependency mapping.** *Normalization (16)*. 2NF removes partial dependency — asked as *"To remove partial dependency from a database, which technique you will use?"* (Sonali/Janata/Rupali SO 25.10.2021) **and** *"If you are assigned to remove partial dependency…"* (Janata Bank ANE (SO) 2020) **and** *"There must not be any partial dependency – Which Normal Form holds this condition?"* (BPSC (Ministry) AME 2022). 3NF is based on transitive dependency (Sonali & Janata Bank Assistant DBA 25-09-2021). BCNF = all determinants are candidate keys (Combined Bank Officer (IT) 04.10.2024). Redundancy exists in unnormalized form (**Bangladesh Bank AP 2016**). **Learn the mapping table, not the definitions.**

**C3 — Key taxonomy.** *Keys in DBMS (11)*. Primary key is chosen from candidate keys (**Bangladesh Bank AP 2011**); the key selected from candidate keys is the primary key (BPSC (Ministry) AP 21.09.2022); unique keys prevent duplicate rows (same sitting); a primary key must also be unique (Combined Bank SO(IT) 2018); referential integrity = foreign key constraint (Sonali & Janata Bank Assistant DBA 25.09.2021); max super keys of R(E,F,G,H) with E as key = 8 (same sitting).

**C4 — Which sort/search for which constraint.** Bank setters like the *constrained-choice* framing, not the definition: sort 1 GB with 100 MB RAM → merge sort (Sonali & Janata Bank Officer (IT/ICT) 2019); very little extra memory + many items → heap sort (BPSC (Ministry) AME 2022); random linked list, minimum time → merge sort, a **2-sitting repeat** (Combined Bank Officer (IT) 04.10.2024 + Combined Bank AP 09.02.2024); least dependent on initial ordering → merge sort (BREB AP 2023); not in-place → merge sort (6 Banks & FI AP 18.03.2021).

**C5 — Which testing type for which situation.** Alpha = in-house simulated environment; Beta = real users/live site; Regression = existing features after change; Usability = ease of use; Smoke = pacing/build-check integration. Every one of those framings appears verbatim: Pubali Bank SQA 18.03.2023 (5 questions), Combined 4 Bank AP 2020, Janata Bank ANE (SO) 2020, Sonali/Janata/RAKUB 2020, Probashi Kallyan Bank 2019 ×4, Sonali Bank Ltd. AE(IT) 2016. Plus **AD(ICT) 2025** on integration testing.

**C6 — OOP four pillars + "which is NOT a feature".** *"Which is not a feature of object-oriented programming?"* → recursion, asked at Combined Bank ME 2018 and Sonali Bank Ltd. AE(IT) 2016; *"Which of the following is not property of the OOP Concept?"* → exception (NPCBL ET 2023); *"Object Oriented programming এর বৈশিষ্ট্য কোনটি?"* at BPSC AP (Dept. of ICT) 2020 **and** BPSC ANE 2019. Overloading vs overriding recurs at Combined 3 Bank AP 2018, Combined Bank SO(IT) 2018, **Bangladesh Bank AP 2011**.

**C7 — Basic electronics one-liners (the AME half of AD(ICT)).** Rectifier AC→DC · Zener in reverse breakdown · inductance dependencies · series vs parallel resistance · transformer turns ratio · BJT configurations (common-collector = voltage follower / emitter follower) · op-amp characteristics · flip-flop stores 1 bit. Sources: **AD(ICT) 07.02.2025** (6), **BB AME 04.02.2023**, **BB AME 2013** (4), **BB AME 2011**, BDCCL Assistant Manager (Transmission) 2022, BTRC Sub-AD (Tech.) 2021, BREB AGM (O&M/E&C) 2021, BPSC (Ministry) AP 21.09.2022.

---

## 🔮 Predicted MCQs

New questions written for practice. **None of these appeared in any historical paper.** Each is derived from a pattern that is documented above.

**🔮 Predicted 1**
> *Historical pattern:* AD(ICT) 2025 asked both *"Which of the following is a DML command?"* and *"Which of the following is a command of DDL?"*, and eight other sittings ask the same taxonomy.
>
> **Which of the following is a Data Control Language (DCL) command?**
> (a) TRUNCATE (b) GRANT (c) COMMIT (d) UPDATE

**🔮 Predicted 2**
> *Historical pattern:* Digital signature was asked twice in AD(ICT) 2025, always as "which algorithm / which key class".
>
> **In a digital signature scheme, the sender signs the message digest using —**
> (a) the receiver's public key (b) the receiver's private key (c) the sender's private key (d) a shared symmetric key

**🔮 Predicted 3**
> *Historical pattern:* the *Diodes & Rectifiers (4)* subtopic is 100% AD(ICT) 2025, covering rectifier direction and Zener region.
>
> **A Zener diode is normally used in a circuit as a —**
> (a) rectifier (b) amplifier (c) voltage regulator (d) oscillator

**🔮 Predicted 4**
> *Historical pattern:* AD(ICT) 2025 asked *"An IP address is given 192.168.3.0, need to 254 useable host…"*; subnetting is the largest subtopic in the bank.
>
> **A department needs 60 usable host addresses from the block 192.168.20.0/24. Which subnet mask is the most efficient?**
> (a) 255.255.255.128 (b) 255.255.255.192 (c) 255.255.255.224 (d) 255.255.255.240

**🔮 Predicted 5**
> *Historical pattern:* ACID was asked at AD(ICT) 2025 through a bank-transfer scenario; Durability/Isolation are the untouched two.
>
> **A completed fund transfer survives an immediate power failure of the database server. Which ACID property guarantees this?**
> (a) Atomicity (b) Consistency (c) Isolation (d) Durability

**🔮 Predicted 6**
> *Historical pattern:* AD(ICT) 2025 asked the priority-queue implementation twice; max-heap root position is a documented 2-sitting repeat.
>
> **In a max-heap of n elements stored in an array, the smallest element is guaranteed to be —**
> (a) at the root (b) at index n/2 (c) in a leaf node (d) at index 1

**🔮 Predicted 7**
> *Historical pattern:* HTTP status 500 was asked at AD(ICT) 2025; 200/403/503 recur on the BB written side.
>
> **A user reaches a page but the server refuses to serve it because of insufficient permission. Which status code is returned?**
> (a) 401 (b) 403 (c) 404 (d) 500

**🔮 Predicted 8**
> *Historical pattern:* AD(ICT) 2025 asked *"A process needs I/O operations, it switches to _____"*; process-state naming recurs at three other bank sittings.
>
> **A process that has finished execution but whose exit status has not yet been read by its parent is called —**
> (a) an orphan process (b) a zombie process (c) a daemon process (d) a suspended process

**🔮 Predicted 9**
> *Historical pattern:* the universal-gate question is a 4-sitting verbatim repeat that already hit AD(ICT) 2025.
>
> **What is the minimum number of 2-input NAND gates required to implement a 2-input XOR gate?**
> (a) 3 (b) 4 (c) 5 (d) 6

**🔮 Predicted 10**
> *Historical pattern:* Docker/Docker Hub was asked at AD(ICT) 2025 and virtualization = resource pooling recurs at BB AME 04.02.2023 and BPSC AME 2019.
>
> **Compared with a virtual machine, a container primarily saves resources because it —**
> (a) runs without any operating system (b) shares the host OS kernel (c) needs no CPU scheduling (d) stores no persistent data

---

## 🏆 Final MCQ Ranking

Ranked by (target relevance to AD(ICT)) × (historical recurrence) × (recency) — highest value first.

| Rank | Topic | Why it ranks here |
|---|---|---|
| 1 | **Digital signature + email-security encryption (RSA / asymmetric / TLS)** | 4 of AD(ICT) 2025's 45 MCQs; two concepts each asked twice in one paper |
| 2 | **Rectifier & Zener diode (AC→DC, reverse breakdown)** | 4 of AD(ICT) 2025's MCQs; the entire *Diodes & Rectifiers* subtopic is this one paper |
| 3 | **DDL / DML / DCL classification + SQL clause execution order** | 3 AD(ICT) 2025 MCQs from the largest database subtopic (52 questions) |
| 4 | **Priority queue → heap; stack applications; sorted linked-list insertion** | 4 AD(ICT) 2025 MCQs; one is a 3-sitting verbatim repeat |
| 5 | **Number systems: 2's complement, base conversions, nibble/ASCII/Unicode** | Largest DLD subtopic (45); AD(ICT) 2025, BB AME 04.02.2023 and 3 more sittings |
| 6 | **Universal gates (NAND/NOR)** | 4-sitting verbatim repeat that already hit AD(ICT) 2025 |
| 7 | **Subnetting / CIDR / private & loopback IPs** | AD(ICT) 2025 hit; largest subtopic in the whole bank (109 written + 33 MCQ) |
| 8 | **ACID (bank-transfer framing) + indexing speeds reads** | 2 AD(ICT) 2025 MCQs; ACID recurs across 8 bank sittings |
| 9 | **Software testing types + waterfall drawback** | 3 AD(ICT) 2025 MCQs; *Software Testing (20)* is the largest SE subtopic |
| 10 | **Encapsulation, operator overloading, OOP pillars** | 2 AD(ICT) 2025 MCQs; *Java (48)* + *Polymorphism (16)* are heavily recycled |
| 11 | **Basic EEE circuits: inductance, series/parallel, transformer, BJT** | 2 more AD(ICT) 2025 MCQs; *Circuits & Components (83)* is the largest EEE subtopic |
| 12 | **Bank math types: percentage, pipes/tanks, ages, direction, weighing puzzle** | 5 of AD(ICT) 2025's MCQs = 15 marks of the paper |
| 13 | **Process states, turnaround time, scheduling names** | AD(ICT) 2025 hit; *Process Management & Scheduling (24)* |
| 14 | **Memory hierarchy, SRAM/DRAM, registers, RISC vs CISC** | **BB Assistant Director (IT) 2016 contributed 14 MCQs to this file alone** |
| 15 | **OSI/TCP-IP layers, port numbers, DHCP/DNS/SMTP** | 58-question application-layer subtopic; multiple 2–3 sitting repeats |
| 16 | **HTTP status codes + "which is not a web server"** | 2 AD(ICT) 2025 MCQs; status codes also recur on the BB written side |
| 17 | **Cloud IaaS/PaaS/SaaS, virtualization, Docker/Docker Hub** | AD(ICT) 2025 hit; **BB AME 04.02.2023 contributed 5 cloud MCQs** |
| 18 | **Searching & sorting complexity, constrained-choice framing** | AD(ICT) 2025 + BB AP 03.02.2023 + BB AP 2016 + BB AME 2013 |
| 19 | **CIA triad, attack families, malware taxonomy** | 20-question attack subtopic; includes the BB 2016 heist question |
| 20 | **GK: recent Nobel/sports + Bangladesh geography & superlatives** | 5 of AD(ICT) 2025's MCQs = 10 marks |

---

## 🚨 Last-Minute MCQ Suggestion

If only a few hours remain, revise exactly these 25. Every entry is anchored to a real historical question; nothing here is filler.

1. **Digital signature → RSA, asymmetric key; signing uses the sender's private key.** (AD(ICT) 2025 ×2)
2. **Email in transit → TLS; email security algorithms → AES + RSA + SHA all used.** (AD(ICT) 2025 ×2)
3. **Rectifier converts AC → DC; inverter does the reverse.** (AD(ICT) 2025 ×2)
4. **Zener diode = unidirectional, operates in the reverse breakdown region.** (AD(ICT) 2025 ×2)
5. **Priority queue → heap.** (AD(ICT) 2025 ×2)
6. **DDL = CREATE/ALTER/DROP/TRUNCATE · DML = SELECT/INSERT/UPDATE/DELETE · DCL = GRANT/REVOKE · TCL = COMMIT/ROLLBACK/SAVEPOINT.** (AD(ICT) 2025 ×2)
7. **SQL clause execution order: FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY.** (AD(ICT) 2025)
8. **ACID: money debited but never credited = Atomicity failure.** (AD(ICT) 2025)
9. **Indexing speeds up reads (SELECT/WHERE), slows writes.** (AD(ICT) 2025)
10. **NAND and NOR are the universal gates.** (AD(ICT) 2025 + 3 more sittings, verbatim)
11. **2's complement: invert + 1; 8-bit range −128 … +127; largest negative = −128.** (AD(ICT) 2025 + BB AME 04.02.2023)
12. **Base conversion drill: dec↔bin↔oct↔hex; nibble = 4 bits; ASCII-8 = 256; Unicode = 16 bits.** (45-question subtopic)
13. **Stack: LIFO, push/pop, function calls, expression evaluation, balanced parentheses, infix→postfix.** (AD(ICT) 2025 + BB AP 2016 ×3)
14. **Sorted insertion into a linked list = Θ(n²).** (AD(ICT) 2025 + 2 more sittings, verbatim)
15. **Linear search works on unsorted data; binary search needs a sorted array, O(log n).** (AD(ICT) 2025 + BB AP 03.02.2023 + BB AME 2013)
16. **Subnetting: /24 = 254 usable; /25 = 126; /26 = 62; /27 = 30; /28 = 14; /30 = 2. Private = 10/8, 172.16/12, 192.168/16. Loopback = 127.0.0.1.** (AD(ICT) 2025 + 3-sitting repeat)
17. **IPv6 = 128 bits; no broadcast (unicast/multicast/anycast only); IPv4-in-IPv6 = tunneling.** (3-sitting repeat + BB AP 03.02.2023)
18. **Integration testing checks the *interface* between modules; unit testing checks the smallest unit.** (AD(ICT) 2025, tagged twice)
19. **Alpha = in-house/simulated; Beta = real users/live; Regression = after change; Usability = ease of use.** (7+ sittings)
20. **Waterfall's drawback = inflexible to changing requirements; 6 phases.** (AD(ICT) 2025 + BB AME 04.02.2023)
21. **Global variables break encapsulation; `<<` overloads best as a global/friend function.** (AD(ICT) 2025 ×2)
22. **Process on I/O request → Waiting (Blocked); turnaround = arrival → completion.** (AD(ICT) 2025 + 3 sittings)
23. **Memory speed order: Register > Cache > RAM > SSD > HDD; SRAM = flip-flop, DRAM needs refresh.** (BB AD(IT) 2016 ×5)
24. **HTTP 500 = Internal Server Error; 403 = Forbidden; 200 = OK; 503 = Service Unavailable. PHP is not a web server (Apache Tomcat/Jetty/Tornado are).** (AD(ICT) 2025 ×2)
25. **Docker = container platform, Docker Hub = cloud image repository; virtualization = resource pooling/sharing; IaaS = hardware, PaaS = runtime, SaaS = application.** (AD(ICT) 2025 + BB AME 04.02.2023 ×5)

---

### Verification note

Everything cited above is traceable to a tag inside `all-questions/mcq/` or `all-questions/written/`. No exam name, year, post, count or repetition figure in this document was estimated. Predicted questions are confined to the **🔮 Predicted MCQs** section and are labelled individually.
