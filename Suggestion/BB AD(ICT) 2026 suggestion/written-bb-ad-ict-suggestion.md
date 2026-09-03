# Bangladesh Bank Assistant Director (ICT) 2026 — Written Suggestion

> Built **only** from the historical question bank in [`all-questions/`](../../all-questions/).
> Every "Appeared in" line below is copied from a real exam tag inside those files.
> Anything invented for practice is explicitly marked **🔮 Predicted**.

---

## Analysis Summary

### What was processed

| Item | Value |
|---|---|
| Source folder | `all-questions/` |
| `.md` files discovered | **50** — `written/` 24 topic files + `written/suggestion/written-question-count.md`, `mcq/` 24 topic files + `mcq/suggestion/mcq-question-count.md` |
| Files read end-to-end | **50 / 50** (no sampling, no skipping) |
| Total questions extracted | **5,910** |
| Written side (`all-questions/written/`) | **3,168** questions — IT 2,623 · General 545 |
| MCQ side (`all-questions/mcq/`) | **2,742** questions |
| Distinct exam sittings identified from tags | **350** |
| Year range covered by tags | **2011 – 2026** |

This file covers the **written paper only**, and is therefore driven by `all-questions/written/`. The MCQ paper is handled in [`mcq-bb-ad-ict-suggestion.md`](mcq-bb-ad-ict-suggestion.md).

### The Bangladesh Bank written footprint

Bangladesh Bank previously ran **Assistant Programmer (AP)** and **Assistant Maintenance Engineer (AME)** as separate circulars; those two posts are now merged into **Assistant Director (ICT)**. The dataset holds **359 Bangladesh Bank question records across 15 sittings — 134 of them on the written side, spread over 11 distinct BB sittings**:

| Bangladesh Bank sitting (written contribution) | Written records | ET |
|---|---|---|
| **Assistant Director (ICT) 07.02.2025** | **11** | **DU** |
| Senior Officer (IT), Grade-9 (Job ID-25104) 2024 | 24 | N/A |
| Recruitment Test 2020 | 19 | N/A |
| Assistant Programmer 03.02.2023 | 17 | BIBM |
| Assistant Maintenance Engineer 04.02.2023 | 14 | BIBM |
| Assistant Programmer 2016 | 9 | N/A |
| Assistant Programmer 2019 | 9 | DU |
| Assistant Maintenance Engineer 2019 | 9 | BUET |
| Assistant Maintenance Engineer 2011 | 8 | N/A |
| Assistant Maintenance Engineer 2017 | 8 | N/A |
| Assistant Maintenance Engineer 2016 | 6 | N/A |

*(11 sittings · 134 written records · verified by counting exam tags inside `all-questions/written/`.)*

### The five findings that shaped this suggestion

**1. All 11 AD(ICT) 07.02.2025 written questions are recoverable, and they are textbook-standard problems.** This is the only sitting of the merged post in the dataset. Verbatim:

| # | Question | File / subtopic |
|---|---|---|
| 1 | **Banker's Algorithm:** 5 processes P₀–P₄; 3 resource types A (10), B (5), C (7). (a) Need matrix (b) Safe state or Unsafe | `operating-system.md` → Deadlock & Resource Allocation |
| 2 | **Construction of Min Heap:** Given Value 12, 29, 33, 56, 66, 99, 100, and 344 | `algorithm.md` → Heap & Priority Queue |
| 3 | **A Bank schema is given below: Bank(Br_Name, Br_City, Assets, Acc_name, Acc_Num, Balance).** (a) Normalize and point out Primary and Foreign Key (b) Show the schema and state why your schema is in good form | `database.md` → Normalization & Database Design |
| 4 | **Bangladesh Bank have client server and the communication with Mail Server, DNS server, Web server. Bangladesh Bank want to ensure the security using firewall on those server. Draw a diagram with the scenario.** | `computer-network-security.md` → Firewalls & Network Defense |
| 5 | **Sinthia wants to send an email to her friend (Afsana).** (a) Mention the protocol of application layer and transport layer (b) Write down the steps of Mail transfer from Afsana to Sinthia | `computer-networks.md` → Email Architecture & Protocols |
| 6 | **What is Total Latency for a 3-kbyte message (an e-mail) if the bandwidth of the network is 1 Gbps?** Distance 300 km, light travels at 2×10⁸ m/s, RTT 50 ms, Queuing Time 5 ms | `computer-networks.md` → Error Detection & Data Communication |
| 7 | **Ā·B̄·(A+B)‾·C ; Write Truth Table.** | `dld.md` → Logic Gates & Universal Gates |
| 8 | **∫₀² (2x² + 3x) dx** | `math.md` → Calculus & Integration |
| 9 | **In Bangladesh Bank, there are 6 Assistant Directors (ADs) and 4 Deputy Directors (DDs). Each AD brings a bag, while only half of the DDs bring a bag. If a bag is selected at random from all the bags, what is the probability that the chosen bag belongs to a Deputy Director (DD)?** | `math.md` → Probability & Statistics |
| 10 | **Write short note on: "The role of AI and machine language mitigate challenges of cyber attack on banking system" (100–150 words)** | `english.md` → Focus Writing |
| 11 | **Bengali to English:** (a) শনিবার হতে সে অফিসে আসছে না। (b) আপনার ব্যাংক একাউন্ট এর স্থিতি জানার জন্য মোবাইল ব্যাংকিং এপ্লিকেশন এ লগইন করুন | `english.md` → Translation |

Two structural facts leap out: **every IT question is a standard textbook problem set in a banking wrapper** (Silberschatz's Banker's Algorithm; Silberschatz's `Bank(branch_name, branch_city, assets, customer_name, account_number, balance)` normalization exercise; Forouzan's total-latency formula), and **the bank's own name is written into the questions** — the firewall diagram, the probability problem and the focus-writing topic are all Bangladesh Bank scenarios.

**2. A Bangladesh Bank written paper has already been recycled almost wholesale.** Of the 22 questions tagged `SO IT 25-07-2026`, **20 are verbatim repeats of `Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024`** — including K-map simplification, subnetting, SQL aggregation, Java recursion tracing, cache miss types, pipelining, circular queue, hashing vs encryption, unit vs integration testing, HTTP status codes, multiplexing guard-band, tree terminology, PaaS selection, grammar ambiguity, binary search on a million records, and five GK one-liners. Only two items in the 2026 paper are new (an e-commerce class diagram and an AI-in-banking essay). This is the strongest single proof in the dataset that **BB written items get reused**, and it makes the BB SO(IT) 2024 paper the second-most valuable document after AD(ICT) 2025 itself.

**3. Subnetting is the single densest topic in the entire bank.** `written/computer-networks.md` → *Subnetting & IP Addressing* holds **109 questions**, more than any other subtopic in all 5,910 records. One stem — *"Given IP address 192.168.1.50, Subnet Mask: 255.255.255.240. Find the valid IP range, Network address and Broadcast address"* — carries **four** separate exam tags.

**4. The written paper is half maths.** Across AD(ICT) 2025 alone: Banker's Algorithm (matrix work), min-heap construction, total-latency computation, a definite integral and a probability problem — 5 of 11 questions are calculations. This matches the wider bank: `written/computer-networks.md` has 16 Nyquist/Shannon questions, 18 multiplexing questions and 13 optical-fibre power-budget questions; `written/operating-system.md` has 25 CPU-scheduling questions.

**5. Mark distribution being targeted.** Written is **200 marks in 2 hours**, split **IT 150 · Math 20 · English 30**. The written script is only evaluated if the MCQ is passed, and the written + viva marks are what actually determine selection. Depth matters here in a way it does not in the MCQ.

---

## 🔥 Tier 1 — Must Study

Every item here is either a verbatim AD(ICT) 2025 written question or a cross-sitting Bangladesh Bank repeat.

---

### T1.1 — Banker's Algorithm: Need matrix and safe sequence

**Question (historical, verbatim):**
> **Banker's Algorithm: 5 processes P₀ through P₄; 3 resource types A (10 instances), B (5 instances), and C (7 instances).**
> (a) Need matrix (b) Safe state or Unsafe
> Snapshot at time T₀. The content of the matrix. Need is defined to be Max – Allocation.

* **Priority:** Highest
* **Type:** Historical Repeat (**2 sittings, identical instance**)
* **Historical evidence:**
  * **Bangladesh Bank Assistant Director (ICT) 07.02.2025** — `written/operating-system.md` → *Deadlock & Resource Allocation (23)*
  * RAKUB Maintenance Engineer (PO) 05.10.2021 — same instance, extended with *"Executing safety algorithm shows that sequence ⟨P1, P3, P4, P0, P2⟩ satisfies safety requirement"*
* **Question variations:** *"The four conditions … are mutual exclusion, hold and wait, no preemption and circular wait. Give an example to show that these conditions are not sufficient"* (DPDC Assistant Manager (ICT) 27.06.2025); *"A system has P processes each needing a maximum of m resources and a total of r resources available. Which conditions must hold to make the system deadlock free?"* (BPSC Multiple Ministry AP (ICT) 19.07.2023); *"Why resource allocation graph used for deadlock detection?"* (Cadet College Lecturer ICT 11.05.2025).
* **Related concepts:** four necessary conditions · resource-allocation graph · deadlock prevention vs avoidance vs detection vs recovery · safe vs unsafe state. The *Deadlock* subtopic holds **23 written questions** — the fourth largest in the OS file.

---

### T1.2 — Normalize the bank schema and identify PK / FK

**Question (historical, verbatim):**
> **A Bank schema is given below: Bank(Br_Name, Br_City, Assets, Acc_name, Acc_Num, Balance)**
> (a) Provided and Normalize and point out Primary and Foreign Key?
> (b) Show that is the schema and state that why your schema is in good form.

* **Priority:** Highest
* **Type:** Historical Repeat (AD(ICT) 2025) + Question Family
* **Historical evidence:** `written/database.md` → *Normalization & Database Design (21)*. This is the classic Silberschatz branch/account decomposition, set as a Bangladesh Bank scenario. Normalization is asked at **21** places in the written folder including *"Why normalization is required in Database? Write shortly about 3NF"* (BPSC Ministry of Power, Energy & Mineral Resources AD(ICT) (CS/CSE) 29.05.2025 — a sibling AD(ICT) post), *"Explain the differences between 2NF and 3NF with examples"* (BPSC Network/Website Manager (CSE) 21.05.2025), *"BCNF is stricter than 3NF"* (17th NTRCA Lecturer (ICT) 2023), *"Why Normalization is used in database? Explain 1st Normal form using an example"* (BPSC Home Affairs Assistant DBA (CSE) 2022).
* **Model answer shape to rehearse:** decompose into `Branch(Br_Name, Br_City, Assets)` and `Account(Acc_Num, Br_Name, Balance)` and `Depositor(Acc_name, Acc_Num)`; PK of each; `Br_Name` as FK in `Account`; then justify with "no partial dependency (2NF), no transitive dependency (3NF), every determinant is a candidate key (BCNF)".
* **Related concepts:** `written/database.md` → *Keys in DBMS (**34**)* — the second-largest database subtopic. Primary vs candidate vs super vs foreign key definitions recur at 30+ sittings including **Bangladesh Bank AP 03.02.2023** and **Bangladesh Bank AP 2016** (*"Define 'integrity rules' of database systems"*).

---

### T1.3 — Firewall placement diagram for bank servers (DMZ)

**Question (historical, verbatim):**
> **Bangladesh Bank have client server and the communication with Mail Server, DNS server, Web server. Bangladesh Bank want to ensure the security using firewall on those server. Draw a diagram with the scenario.**

* **Priority:** Highest
* **Type:** Historical Repeat (**Bangladesh Bank asked this twice, 6 years apart**)
* **Historical evidence:**
  * **Bangladesh Bank Assistant Director (ICT) 07.02.2025** — `written/computer-network-security.md` → *Firewalls & Network Defense (20)*
  * **Bangladesh Bank Assistant Programmer 2019 (ET: DU)** — *"What is firewall? explain its work. Draw a LAN network and a firewall where firewall will be situated."*
* **Question variations:** *"What is DMZ in data center? Describe using diagram? Write the network devices in this system?"* (BDCCL Assistant Manager (Cyber Security) 14.10.2022); *"DMZ and firewall placement in a diagram"* (MGMCL Assistant Manager (ICT) 20.05.2022); *"What is Demilitarized Zone (DMZ) and sandbox for security test?"* (PGCB AE (CSE) 17.05.2024); *"What is firewall? Draw a LAN network to showing firewall"* (BREB Junior Assistant Manager (ICT) 2021); *"Draw a diagram of LAN including network Firewall … List 5 major types of network firewalls. Differentiate between Traditional Firewall and Next Generation Firewall"* (Rupali Bank ANE 04.11.2023).
* **Related concepts:** packet-filter vs stateful vs proxy vs NGFW vs WAF (Islami Bank PLC SO (Network/System) 14.03.2025 gives a full NGFW-vs-WAF comparison table); firewall vs antivirus (BREB AGM (IT) 2021); firewall vs gateway (DMTCL AE (ICT) 27.01.2023); stateful vs stateless firewall (Dutch Bangla Bank 2019). **Practise drawing the three-zone diagram — Internet → NGFW → DMZ (Mail/DNS/Web) → internal firewall → LAN/core banking — from memory.**

---

### T1.4 — Email transfer: application/transport protocols and the step-by-step path

**Question (historical, verbatim):**
> **Sinthia wants to send an email to her friend (Afsana). He sends the email through application and transport layer.**
> (a) Mention the protocol of application layer and transport layer.
> (b) Write down the steps of Mail transfer from Afsana to Sinthia.

* **Priority:** Highest
* **Type:** Historical Repeat (AD(ICT) 2025) + Recurring Concept
* **Historical evidence:** `written/computer-networks.md` → *Email Architecture & Protocols (SMTP, POP3, IMAP) (10)*. The concept recurs at: *"SMTP, DNS, DHCP, NAT এর কাজ কি লিখ?"* (BTCL JAM 2022); *"Distinguish the purpose of SMTP and IMAP in email communication"* (BPSC Home Affairs Senior Computer Operator (CSE) 13.09.2022); *"What is SMTP? How SMTP works?"* (BPSC AP (ICT) 2019); *"Difference between SMTP and SNMP"* (RAKUB Assistant Network System Engineer 03.11.2023); **Bangladesh Bank AME 2017** (*"Write short notes on DHCP and SMTP"*).
* **Model answer shape:** Application layer = SMTP (sending, MTA→MTA), POP3/IMAP (retrieval), plus DNS MX lookup. Transport layer = TCP (SMTP 25/587, POP3 110, IMAP 143). Steps: compose → UA → SMTP to sender's mail server → DNS MX query for the recipient domain → SMTP relay to recipient's mail server → stored in mailbox → recipient's UA pulls it with POP3 or IMAP.
* **Related concepts:** MIME/Content-type (Sonali Bank and BDBL SO(IT) 25.09.2021); why DNS uses UDP but zone transfer uses TCP (Combined Bank SO(IT) 17.10.2025); the DNS resolution sequence when a URL is typed (same sitting, and BPSC Sub-AE Ministry of Agriculture 2021).

---

### T1.5 — Total latency of a message (Forouzan formula)

**Question (historical, verbatim):**
> **What is Total Latency for a 3-kbyte message (an e-mail) if the bandwidth of the network is 1 Gbps? Assume that the distance between the sender and the receiver is 300 km and that light travels at 2 × 10⁸ m/s. Round Trip Time 50 ms Queuing Time 5 ms**

* **Priority:** Highest
* **Type:** Historical Repeat (AD(ICT) 2025) + textbook family
* **Historical evidence:** `written/computer-networks.md` → *Error Detection & Data Communication (CRC, Throughput) (14)*. The identical Forouzan family appears on the MCQ side too: *"What is the propagation time for a 2.5-kbyte message (an e-mail) if the bandwidth of the network is 1 Gbps? … distance 12,000 km … 2.4 × 10⁸ m/s"* (Sonali Bank and BDBL SO(IT) 25.09.2021).
* **Model answer shape:** `Latency = Propagation time + Transmission time + Queuing time (+ processing)`; Propagation = distance / propagation speed = 300,000 m ÷ 2×10⁸ = 1.5 ms; Transmission = message size / bandwidth = 3,000×8 bits ÷ 10⁹ = 24 µs. Show every term with units.
* **Related concepts:** the whole Forouzan calculation block that bank setters reuse — bit rate for 100 pages/second (Sonali/Janata/Rupali 25.10.2021, Rupali ANE 2021, Janata Bank ANE (SO) 2020 — **3 sittings**); Nyquist `C = 2B log₂ L`; Shannon `C = B log₂(1+SNR)` with the 3000 Hz / SNR 3162 telephone-line instance appearing at RPGCL 2022 **and** Combined Bank AP 09.06.2023; guard-band multiplexing (**BB SO(IT) 2024** + SO IT 2026).

---

### T1.6 — Truth table from a Boolean expression

**Question (historical, verbatim):**
> **Ā·B̄·(A+B)‾·C ; Write Truth Table.**

* **Priority:** Highest
* **Type:** Historical Repeat (AD(ICT) 2025) + Question Family
* **Historical evidence:** `written/dld.md` → *Logic Gates & Universal Gates (33)*, the largest DLD subtopic on the written side. The same "given an expression, produce the truth table / evaluate at a given input" pattern appears at: *"Logic Circuit of Boolean algebra: Q = C̄ + ĀB + BC(B+C)‾; Where output Q and input (A,B,C)=(0,0,1)?"* (Sonali Bank PLC Assistant DBA 23.02.2024); *"Draw the logic circuit of the Boolean Expression, Q = ĀB̄ + BC(B+C)‾; find Q where (A,B,C)=(1,0,1)"* (Combined Bank AME/AE(IT) 24.02.2024); *"Construct a truth table for (r ∨ (q ∧ ¬p)) ∧ ¬(r ∧ (q ∧ ¬p))"* (Combined 3 Banks AP 2018); *"Truth table construction for f(A,B,C,D) = (A+B) ⊕ (CD)"* (DESCO AE(CSE) 2016).
* **Related concepts:** De Morgan's theorems — *Boolean Algebra & De Morgan's Theorem (19)*, asked at **BB AME 2019** (*"How will realize an AND gate and OR gate using CMOS NAND and NOR gate?"*) and **BB AME 2011** (*"What do you understand by universality of logic gate? Prove universality of NOR logic gate."*).

---

### T1.7 — Min-heap / max-heap construction from a value list

**Question (historical, verbatim):**
> **Construction of Min Heap: Given Value 12, 29, 33, 56, 66, 99, 100, and 344**

* **Priority:** Highest
* **Type:** Historical Repeat (AD(ICT) 2025) + Recurring Concept
* **Historical evidence:** `written/algorithm.md` → *Heap & Priority Queue (2)*; `written/data-structure.md` → *Priority Queues & Heaps (Min/Max Heap) (8)*. Same family: *"Given item- 40, 45, 80, 90, 50, 70. Draw Heap and Binary search tree (BST)"* (SGFL AE (IT) 2023); *"Given an array of 6 elements: {15, 19, 10, 7, 17, 16}. Draw heap tree and again draw the tree after deletion of element 7"* (PGCB AE (CSE) 30.09.2021); *"Binary tree টিকে heapify করুন যেন maximum heap-এ রূপান্তরিত হয়"* (NACTAR 2020); *"Heapify the MAX heap tree"* (PGCB Sub-AE (CSE) 2020); *"Draw (max/min) heap binary tree using 11 nodes"* (DESCO Sub-AE (CSE) 2019); *"Max Heap Operation [a-j] show heap"* (Combined Bank AP 09.06.2023); *"Describe, and estimate the costs of, a procedure to insert a new item into an existing binary max-heap"* (Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024).
* **Related concepts:** heapsort algorithm and max-heap properties (BPSC Home Affairs Senior Computer Operator (CSE) 13.09.2022); heap as the priority-queue implementation (which is the AD(ICT) 2025 MCQ, see the MCQ file T1.3).

---

### T1.8 — Subnetting: divide a block, give network / broadcast / mask / usable range

**Question (historical, verbatim — the BB Senior Officer (IT) 2024 form):**
> **An organization is granted the IPv4 network block 14.24.74.0/24 and needs to segment it into two subnets: Subnet A (requires 120 addresses) and Subnet B (requires 60 addresses). Allocating sequentially from the requirement first to maximize remaining address space, state only the Network Address (with its CIDR mask) and the Broadcast Address for both subnets.**

* **Priority:** Highest
* **Type:** Historical Repeat (**Bangladesh Bank SO(IT) 2024 → reused verbatim at SO IT 25-07-2026**) + the densest topic in the dataset
* **Historical evidence:** `written/computer-networks.md` → *Subnetting & IP Addressing (**109**)* — the largest subtopic in all 5,910 questions. Bangladesh Bank instances: **SO(IT) Grade-9 2024** (above, item 6.10) and **AME 2017** (*"How many subnets and hosts per subnet can you get from the network 172.20.0.0/27?"*). One stem — *"Given IP address 192.168.1.50, Subnet Mask: 255.255.255.240. Find the valid IP range. Also find Network address and Broadcast address"* — carries **4 tags** (NWPGCL Assistant Manager (ICT) 12.01.2024, BTCL Assistant Manager (Technical) 2023, BPDB AE (CSE) 10.05.2024, BIWTA AE (CSE) 24.02.2023).
* **Question variations:** VLSM with unequal department sizes (Rupali Bank ANE 2021: 2000/1000/6000/8000 hosts from 192.168.0.0/20; Dhaka WASA AME (Network) 04.07.2025: half / quarter / quarter of 245.248.128.0/20; Cadet College Lecturer ICT 11.05.2025: 110/50/20/8 hosts from 192.168.0.0/24); "divide into 4 equal subnets" (Senior Officer IT 22-05-2026, Officer (IT) 31 Jul 2026, Combined Bank Officer (IT) 09.05.2026 — all three phrase it as a bank-branch scenario).
* **Related concepts:** classful vs classless; private ranges per class; wildcard mask; CIDR aggregation; **NAT (13 written questions)** and **VLAN vs subnetting** (BSCCPL AME 21-08-2026).

---

### T1.9 — Aggregate SQL query per group (COUNT + AVG + GROUP BY)

**Question (historical, verbatim — the BB Senior Officer (IT) 2024 form):**
> **Consider the following relation: Employee(EmpID, Name, Department, Salary). Write an SQL query to retrieve the Department, the total number of employees, and the average salary for each department. The output should display one record for each department.**

* **Priority:** Highest
* **Type:** Historical Repeat (**BB SO(IT) 2024 → reused verbatim at SO IT 25-07-2026**) + the largest written subtopic after subnetting
* **Historical evidence:** `written/database.md` → *SQL Queries (**87**)*. Bangladesh Bank SQL instances: **SO(IT) Grade-9 2024** (above), **AP 03.02.2023** (*"Write a SQL query to return the number of movies that are romantic comedies"* over a five-table Movies/People/Genres schema), **AP 2016** (*"Write a SQL query to get the second highest salary from Employee table"*), **Recruitment Test 2020** (*"Give some examples of DDL, DML and DCL commands"*).
* **Question variations that recur constantly:** department-wise average salary (Islami Bank QA 14.03.2025, NESCO JAM (ICT) 2021, BTCL JAM 2022, Combined Bank AP 09.02.2024); employees earning above the company/department average (BGDCL 15.03.2024, BPDB 24.02.2023, CAAB 2022, Dutch Bangla Bank 2019, Sonali & Janata Bank Officer (IT) 14.10.2023 and Rupali Bank ANE 04.11.2023 both as *analyse this query* problems); second-highest salary (BCC AP 2017, WZPDCL 2019, **BB AP 2016**); duplicate rows (BCC AP 18.10.2025, BBA AP 12.07.2025, Agrani Bank 2017); the four JOIN types with a worked result set (Combined Bank SO(IT) 17.05.2024, BPDB 10.05.2024).
* **Related concepts:** `WHERE` vs `HAVING`; correlated subqueries; `GROUP BY` with multiple aggregates; JOIN row-count reasoning; views and triggers (*PL/SQL & Database Triggers (7)*).

---

### T1.10 — K-map simplification to minimal SOP

**Question (historical, verbatim — the BB Senior Officer (IT) 2024 form):**
> **Simplify the following boolean expression using 4 variable K-map: F(A,B,C,D) = Σm(0,3,5,7,8,10,11,12,13,14,15). Draw the K-map grid, clearly show your groupings (loops), and write the final simplified Sum-of-Products (SOP) expression.**

* **Priority:** Highest
* **Type:** Historical Repeat (**BB SO(IT) 2024 → reused verbatim at SO IT 25-07-2026**)
* **Historical evidence:** `written/dld.md` → *Karnaugh Map (K-Map) (19)*. Same instance re-set elsewhere: *"Show minimal function using K-Map: F(A,B,C,D) = Σ(2,8,9,11,13,15)"* appears under **two** tags (BPDB AE (CSE) 10.05.2024 and BICIC AP 2022). Also *"Simplify F(A,B,C,D) = ACD + AB + D̄ + AC̄D using K-map and draw the logic circuits"* under **two** tags (BPSC Home Affairs Assistant DBA (CSE) 2022 and BPSC AP (CSE) 2019).
* **Related concepts:** SOP vs POS; don't-care conditions; implementing the minimised function with NAND-only or NOR-only gates (*"X = ĀBC + AB̄C + ABC̄ + ABC সমীকরণটির সরলীকৃত মান NAND এবং NOR গেইট দ্বারা বাস্তবায়ন করুন"* — 18th NTRCA Assistant Teacher (ICT) 12.07.2024); comparator/7-segment as K-map + decoder combinations (Rupali Bank ANE 2021, BPSC Sub-AE Ministry of Agriculture 2021).

---

## ⭐ Tier 2 — High Priority

| # | Question / concept | Type | Historical evidence |
|---|---|---|---|
| T2.1 | **CPU scheduling: Gantt chart + average waiting time + average turnaround time for FCFS, SJF, Priority and RR** | Recurring Concept (25 written questions) | `written/operating-system.md` → *CPU Scheduling Algorithms (25)* + *CPU Scheduling (6)*. The five-process table with burst times 10/1/2/1/5 and priorities 3/1/3/4/2 appears at BPSC Ministry of Power, Energy & Mineral Resources **AD(ICT) (CS/CSE) 29.05.2025** — a directly comparable AD(ICT) post — and again in the Passport Office AP 2024 paper with burst times 15/2/4/2/8. Also Combined Bank SO(IT) 17.10.2025 (five jobs, four algorithms), BCC AP 18.10.2025, DPDC AE (CSE) 17.10.2025, Sonali Bank PLC Assistant DBA 23.02.2024, BCIC AP 14.02.2025, Teletalk 2023, BIWTA 2023, Rupali Bank ANE 2021, National University AP 2020, Sundharban Gas 2020, **Bangladesh Bank AME 2011** (*"What is turnaround time of a process?"*). |
| T2.2 | **Page replacement: FIFO / LRU / Optimal page-fault count** | Recurring Concept | `written/operating-system.md` → *Virtual Memory & Page Replacement (Thrashing) (16)*. The canonical reference string 7,0,1,2,0,3,0,4,2,3,0,3,2,1,2,0,1,7,0,1 with 3 frames appears at BSCCPL AME 21-08-2026; 4,7,6,1,7,6,1,2,7,2 with 3 frames at BPDB AE (CSE) 2021; 4,7,6,1,2,7,2 at BPDB 10.05.2024; 1,3,0,3,5,6,3 at Combined Bank AP 09.06.2023. Thrashing explained at Combined Bank SO(IT) 17.10.2025 and Titas Gas 2021. |
| T2.3 | **Linux commands (file permission, listing, search, disk, network)** | Recurring Concept (**largest OS subtopic**) | `written/operating-system.md` → *Linux / Unix Commands & Administration (**47**)*. Recurring asks: chmod/permission (Islami Bank PLC SO 14.03.2025, APSCL 2021, JGTDSL 2021, BTCL JAM 2022, DESCO 2019, BPDB 2018); hidden files (`ls -a`) at NESCO 2021, MGMCL 2022, WASA 2022; head/tail of N lines (BTCL 2023, Titas Gas 2024, Milk Vita 2023, APSCL 2021); grep (BCC AP 12.02.2021, BITAC 2021, BCIC 14.02.2025); ip/ifconfig (PGCL 2021, DESCO 2025, BARI 2025); df/free/top (BCIC 14.02.2025). |
| T2.4 | **Hashing vs encryption; symmetric vs asymmetric; RSA; Caesar cipher** | **3-sitting repeat** + BB hit | `written/computer-network-security.md` → *Cryptography (**31**)*. *"Explain the operational difference between Hashing and Encryption"* is tagged **Bangladesh Bank Senior Officer (IT), Grade-9 2024** (as 6.2), SO IT 25-07-2026, DESCO AE (CSE) 10.09.2022 and BKSP AP 03.12.2022. Symmetric vs asymmetric with examples recurs at 8+ sittings. **BB AP 03.02.2023** asked the MITM attack on Diffie-Hellman key exchange. |
| T2.5 | **CIA triad and how the three principles map to attacks** | BB hit + recurring | `written/computer-network-security.md` → *Security Principles (CIA Triad) (8)*. **Bangladesh Bank AP 03.02.2023**: *"Preserving confidentiality integrity and availability of data is a restatement of the concern over falsification, interception, masquerade and denial of service. Explain how the first three concepts relate to the last four."* Also Combined Bank SO(IT) 17.10.2025, NPCBL Cyber Security Analyst 11 July 2026, Combined Bank Officer (IT) 09.05.2026 and 03.01.2026, EGCB 28.01.2023, Teletalk 2023. |
| T2.6 | **SQL injection & XSS: how they work and how to prevent** | **3-sitting repeat** | `written/computer-network-security.md` → *Web Security Vulnerabilities (19)*. *"What is SQL Injection? How to Prevent against SQL Injection Attacks?"* carries three tags (RAKUB Programmer (PO) 12.10.2021, RAKUB ME (PO) 05.10.2021, Dhaka WASA AME (Network) 04.07.2025). XSS/CSRF at Islami Bank QA 14.03.2025, DESCO 20.06.2025, Titas Gas 24.05.2024, BICIC 2022, SPCB 2022, 16th NTRCA 2019. **BB AME 2017** asked *"What are the important steps to secure a web server?"* |
| T2.7 | **OSI / TCP-IP layers with functions, protocols and devices per layer** | Recurring Concept (52 written questions) | `written/computer-networks.md` → *OSI & TCP/IP Reference Model (**52**)*. **Bangladesh Bank AP 03.02.2023** framed it as a design decision: *"the company decided to add end-to-end encryption techniques — which layer of the OSI model is suitable considering development time, software maintainability and development cost?"* **BB AP 2019** asked *"Two OSI layers which known as 'flow Control' — which are those?"* The tabular "layer / function / protocol / device" form is asked at Combined Bank AME/AE(IT) 24.02.2024, Rupali Bank ANE 04.11.2023, BPSC AD(ICT) (CS/CSE) 29.05.2025. |
| T2.8 | **TCP vs UDP and the three-way handshake diagram** | **3-sitting repeat** | `written/computer-networks.md` → *Transport Layer (TCP & UDP) (17)*. *"Distinguish between TCP and UDP protocols"* carries three tags (BPSC Security Services Division AP 13.12.2021, BPSC Home Affairs Senior Computer Operator (ICT) 13.09.2022, Combined Bank Officer (IT) 03.01.2026). 3-way handshake diagram at BRiCM 24.02.2024 **and** BGDCL 19.11.2021 (2 tags), plus BPSC Network/Website Manager (CSE) 21.05.2025, BICIC 2022, Sonali Bank Ltd. Officer IT 2021. **Bangladesh Bank Recruitment Test 2020** asked *"the primary function of TCP is to turn an unreliable network into a reliable network … What are the functions performed by TCP?"* |
| T2.9 | **Cache memory: hit/miss, compulsory vs capacity miss, direct-mapped tag/index/offset, average access time** | **BB asked it in 3 different sittings** | `written/microprocessor-and-computer-architecture.md` → *Cache Memory (14)*. **BB SO(IT) Grade-9 2024** (6.3: compulsory vs capacity miss — reused at SO IT 25-07-2026); **BB AME 04.02.2023** (*"16 KB of data in a direct mapped cache with 4 word blocks … size of the tag, index and offset fields, 32-bit architecture"*); **BB AME 2017** (*"If main memory access time is 100 ns, cache access time is 50 ns, cache hit rate is 90% then what is the average time to read from memory?"*). |
| T2.10 | **Instruction pipelining and hazards** | **BB asked it in 3 different sittings** | `written/microprocessor-and-computer-architecture.md` → *Instruction Pipelining & Hazards (9)*. **BB SO(IT) 2024** (6.1: why multi-stage pipelining over single-cycle — reused at SO IT 25-07-2026); **BB AME 2019** (*"How is computer Architecture characterized. What are the 5 stages of the DLX pipeline?"*); **BB AME 2011** (*"What is pipelining? What is opcode and operand in machine code? Explain snooping cache."*). |
| T2.11 | **OOP: inheritance, polymorphism, overloading vs overriding, encapsulation — with a code example** | **BB asked it in 4 different sittings** + largest OOP subtopic | `written/oop.md` → *OOP Concepts (Inheritance & Polymorphism) (**54**)*. **BB AP 03.02.2023** (a Java class-pair asking which methods overload / override / hide); **BB Recruitment Test 2020** (*"The main advantage of Inheritance is the ability to reuse the code. Explain in brief different types of Inheritance"*); **BB AP 2016** (*"What is polymorphism? What is the difference between method overriding and method overloading?"*); **BB AP 2019** (a multi-threaded Overdraft Account class in Java). |
| T2.12 | **Java output tracing with static variables and recursion** | Historical Repeat (**BB SO(IT) 2024 → SO IT 2026**) | `written/oop.md` → *Output Tracing & Recursion (10)*. The exact program (`static int x = 5; fun(n) { if (n<=1) return 1; x = x + 2; return fun(n-1) + x; }` printing `fun(3)`) is tagged **BB SO(IT) Grade-9 2024** and SO IT 25-07-2026. C-side output tracing is the **57-question** *Output Tracing & Control Flow* subtopic in `written/c-programming.md`. |
| T2.13 | **Sorting algorithms: step-by-step trace + best/average/worst complexity table** | Recurring Concept (**largest algorithm subtopic**) | `written/algorithm.md` → *Sorting Algorithms & Complexity (**36**)*. **Bangladesh Bank Recruitment Test 2020** (*"Insertion sort is a simple sorting algorithm. Write a program to sort some given numbers using insertion sort"*). Fill-the-complexity-table form at DPDC Assistant Manager (ICT) 27.06.2025; quicksort worst case at Combined Bank SO(IT) 17.10.2025, Combined 2 Bank Officer IT 04.10.2024, BKSP 2024, PetroBangla 2024; merge-sort recurrence T(n)=2T(n/2)+n at BPSC Multiple Ministry AP (CSE) 19.07.2023. |
| T2.14 | **BFS / DFS traversal and difference; MST by Kruskal; shortest path by Dijkstra** | AD(ICT)-adjacent + recurring | `written/algorithm.md` → *Graph Traversal (17)*, *Shortest Path & MST (15)*. Kruskal's MST is set at BPSC **AD(ICT) (CS/CSE) 29.05.2025**, RAKUB Programmer (PO) 2021, BAUST 2021, Sonali Bank Ltd. Officer IT 2021, DESCO 2022. BFS-vs-DFS difference at BPSC Security Services AP 13.12.2021, 17th NTRCA 2023, BPSC Ministry of Agriculture 2022, DPDC 17.10.2025. |
| T2.15 | **Software testing: unit vs integration; black-box vs white-box; verification vs validation** | **BB hit + 5-sitting repeat** | `written/software-engineering.md` → *Software Testing & Evaluation (**40**)*. *"What is the main difference between black box and white box testing?"* carries **five** tags (BARC Programmer 04.08.2023, BPSC AME (CSE) 2020, MRA AME 2022, Teletalk 2023, SGFL 2021). **BB SO(IT) 2024** asked 6.5 unit vs integration (reused at SO IT 2026); **BB AME 04.02.2023** asked verification/validation at CMMI level 3; **BB AME 2019** asked *"How would you test an ATM in a banking system?"*; **BB Recruitment Test 2020** asked the tests conducted at the implementation stage. |
| T2.16 | **SDLC models: waterfall vs agile, and which to pick for a given scenario** | Recurring Concept (**largest SE subtopic**) | `written/software-engineering.md` → *SDLC Phases & Models (**45**)*. Scenario framing dominates: *"You are asked to lead a team … deploy as fast as possible. Between Waterfall and Incremental, which approach will you take?"* (Combined Bank SO(IT) 17.05.2024); *"the librarian wants the system delivered in phases so that feedback can be incorporated"* (Officer (IT) 31 Jul 2026); *"Critically analyze the limitations of the Waterfall model and explain how Agile methodologies address those"* (Combined Bank Officer (IT) 03.01.2026). |
| T2.17 | **UML: class diagram and use-case diagram from a scenario** | BB hit + recurring | `written/software-engineering.md` → *UML Diagrams (14)*. **Bangladesh Bank AP 03.02.2023**: *"Draw a class diagram. A token-ring based local area network (LAN) … Workstations are originators of messages; servers and printers are network nodes that can receive messages …"* Bank-scenario variants: ATM use case (Combined Bank HBFC/BKB AP 2018, Agrani Bank 2017), online banking use case (Combined Bank Officer (IT) 09.05.2026), e-commerce class diagram (SO IT 25-07-2026, PGCB 17.05.2024, Combined 2 Bank Officer IT 04.10.2024). |
| T2.18 | **RAID levels and which to choose for a bank** | Recurring Concept | `written/microprocessor-and-computer-architecture.md` → *RAID Architecture & Storage (15)*. *"Which RAID level is best and why?"* carries two tags (Sonali Bank PLC Assistant DBA 23.02.2024 and BEPRC AP 08.08.2026). RAID 1 vs RAID 5 comparison at BPSC Home Affairs Senior Computer Operator (CSE) 13.09.2022 and BDCCL Cyber Security 14.10.2022; RAID relevance to a database at Sonali Bank PLC Assistant DBA 23.02.2024. |

---

## 📌 Tier 3 — Medium Priority

| # | Concept | Historical evidence (`all-questions/written/`) |
|---|---|---|
| T3.1 | **Interpreter vs compiler; phases of a compiler** | *Compiler vs Interpreter (7)* — the difference question carries **six** tags: MRA AME 2020, BPSC Home Affairs Assistant DBA (ICT) 2022, CAAB AP 2022, PGCB Sub-AE (CSE) 30.09.2021, Combined Bank Officer (IT) 03.01.2026, BPSC Ministry of Agriculture AP 15.02.2022. Also 41st BCS 2021. |
| T3.2 | **DFA/NFA design and regular expressions; CFG ambiguity** | *Regular Expressions & Finite Automata (7)*, *Grammar & Ambiguity (5)*. **Bangladesh Bank SO(IT) Grade-9 2024** asked the ambiguity of `E → E+E | E*E | id` for `id + id * id` — also tagged SO IT 25-07-2026. |
| T3.3 | **Data structure basics: array vs linked list; stack vs queue; circular queue** | `written/data-structure.md` → *Linked List (15)*, *Stack (20)*, *Queue (6)*. **BB SO(IT) 2024**: 6.6 circular vs linear queue and 6.12 tree terminology (both reused at SO IT 2026); **BB Recruitment Test 2020**: enqueue steps; **BB AP 2016**: prefix/postfix of `((A+B)*C-(D-E)^F)`. |
| T3.4 | **Tree: construct from two traversals; BST insert/delete; B/B+ tree** | *Tree (27)* — the largest data-structure subtopic. Preorder+inorder reconstruction at BSCCPL AME 21-08-2026, BAUST 2021, Rupali Bank ANE 2021, APSCL 2021; pre+post at BPDB 10.05.2024; B-tree at 17th NTRCA 2023; B+ tree index at Titas Gas 2021. |
| T3.5 | **Hash table with linear probing** | *Hashing & Hash Tables (6)*. **Bangladesh Bank AP 03.02.2023**: *"Consider a hash table of size 13 … h(k) = k mod 13. Insert keys 10, 3, 6, 16, 17, 19 using linear probing to resolve collisions. Show all the work."* Also JGTDSL 2021 (h(x)=x%11) and Sonali & Janata Bank Assistant DBA 2022. |
| T3.6 | **C programming: write a program (prime, factorial, Fibonacci, series sum, pattern, array max)** | *Basic Programs & Control Statements (**111**)* — the largest single written subtopic after subnetting and SQL. **BB AP 03.02.2023** (LCM of A and B); **BB AP 2016** (Fibonacci up to 100); **BB AP 2019** (max price from 20 items); **BB Recruitment Test 2020** (weekly pay with overtime; recursive factorial). |
| T3.7 | **Recursion: write it, trace it, and give the recurrence** | *Recursion & Functions (38)*. **BB Recruitment Test 2020** (recursive factorial algorithm); call-by-value vs call-by-reference recurs at BPSC Home Affairs Assistant DBA (CSE) 2022 + BPSC Ministry of Agriculture AP 2022 (2 tags) and 6 more sittings. |
| T3.8 | **Memory management: paging vs segmentation; page-table size; internal vs external fragmentation** | *Memory Management & Paging (16)*. Page-table-size calculations at BPSC **AD(ICT) (CS/CSE) 29.05.2025** (4 GB RAM, 4 KB pages, 32-bit VA, 8-byte PTE), Dhaka WASA 04.07.2025, Combined Bank SO(IT) 17.10.2025, SGFL 2023. |
| T3.9 | **Cloud: IaaS/PaaS/SaaS selection; VM vs container; multi-tenancy** | `written/cloud-computing.md` → *Cloud Service Models (13)*, *Virtualization & Containers (8)*. **BB SO(IT) 2024** (6.11 PaaS scenario — reused at SO IT 2026); **BB AME 04.02.2023** twice (*"Explain IaaS, PaaS, and SaaS"*; *"Define a virtual machine with a neat diagram"*). |
| T3.10 | **ER diagram from a written scenario, then convert to tables** | `written/database.md` → *ER Diagram & Database Design (25)*. Bank-flavoured instances: E-R of a Banking Management system (RAKUB ME (PO) 05.10.2021), Railway service (Sonali Bank Ltd. Officer IT 2021), library (BPSC AD(ICT) 29.05.2025, MRA 2020), job-application (BSCCPL AME 21-08-2026), football league (Rupali Bank ANE 2021 + Janata Bank Assistant System Administrator 2021, 2 tags). |
| T3.11 | **Data centre, server, UPS, DR/BCP for a bank** | `written/computer-fundamental.md` → *Data Center Infrastructure & Power Management (10)*, *Server Hardware (5)*. **Bangladesh Bank AME 04.02.2023**: *"What are the challenges in optimizing energy efficiency of data centers?"* Also Combined Bank AME/AE(IT) 24.02.2024, Combined Bank AME/Hardware 23.11.2023, Combined Bank SO(IT) 17.05.2024 (IT disaster recovery plan), BDCCL Cloud 14.10.2022 (data-centre TIER standards). |
| T3.12 | **Blockchain, AI/ML in banking, digital vs traditional banking** | `written/computer-fundamental.md` → *Blockchain & Emerging Technologies (8)*, *Digital Banking & Financial Inclusion (2)*; `written/ai-and-ml.md` (43 questions). Directly relevant because AD(ICT) 2025's English focus-writing was *"The role of AI and machine language mitigate challenges of cyber attack on banking system"*. |
| T3.13 | **Two-factor authentication and digital certificates** | *Authentication & Access Control (16)*. 2FA definition carries two tags (BPSC AD(ICT) (CS/CSE) 29.05.2025 + BPSC Workshop Maintenance Engineer (CSE) 2021); OTP-based online-banking security at Combined Bank AME/AE(IT) 24.02.2024; digital signature vs digital certificate at Sonali & Janata Bank Officer (IT) 14.10.2023. |
| T3.14 | **Electrical & electronics written problems (the AME half)** | `written/electrical-and-electronics.md` (39 questions). **BB AME 04.02.2023**: *"Describe cut off, saturation and active region of operation of a transistor with diagram. Explain the working principle of an n-channel JFET…"*; **BB AME 2019**: 3-phase 12-pole alternator driving an 8-pole induction motor with 3% slip; **BB AME 2017**: *"What is the difference between battery and capacitor?"* |
| T3.15 | **Math (20 marks): probability, definite integrals, set theory, algebra, profit & loss** | `written/math.md` (96). **AD(ICT) 2025** gave one probability and one definite integral. **BB AP 03.02.2023**: `x + 1/x = 17/4 → x − 1/x`, students-in-rows, right-triangle area. **BB AME 04.02.2023**: surd simplification, compound-vs-simple profit split of Tk 25,000, profit%=loss% pricing, longest-side geometry. **BB AP 2016**: tautology proof by truth table. **BB AP 2019**: probability that all 10 bits of a random number are 1. |
| T3.16 | **English (30 marks): focus writing + Bangla→English translation** | `written/english.md` → *Focus Writing (37)*, *Translation (18)*. **AD(ICT) 2025** = one 100–150-word note + two Bengali sentences. **BB SO(IT) 2024** = *"The Importance of Digital Literacy in Expanding Cashless Transactions in Bangladesh"* + a Bangla passage (সময়ের এক ফোঁড় …) + an English passage. **BB AP 03.02.2023** = *"Growing use of technology in the Financial Service Industry"*. **BB Recruitment Test 2020** = *"Post-corona Green Recovery Plans and Progress in Bangladesh"* + a COVID-vaccine-funding passage + a Nobel-Medicine passage. **Every Bangladesh Bank English topic in this dataset is banking, technology or national-development themed.** |

---

## 🔁 Repeated Written Questions

Strongest exact / near-exact repeats in `all-questions/written/`, in original wording.

### The headline repeat: an entire Bangladesh Bank paper reused

**20 of the 22 questions tagged `SO IT 25-07-2026` are verbatim `Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024` questions.** The shared set:

| BB SO(IT) 2024 item | Question |
|---|---|
| 6.1 | Why do modern processor designs favor a multi-stage pipelined approach over a single-cycle implementation? |
| 6.2 | Explain the operational difference between Hashing and Encryption. |
| 6.3 | Explain the difference between a "Compulsory Miss" (Cold Miss) and a "Capacity Miss" in cache memory. |
| 6.4 | Consider the following relation: Employee(EmpID, Name, Department, Salary). Write an SQL query to retrieve the Department, the total number of employees, and the average salary for each department. |
| 6.5 | Explain the difference between Unit Testing and Integration Testing. |
| 6.6 | Why is a Circular Queue preferred over a Linear Queue in many operating systems? Explain with one example. |
| 6.7 | What do the following specific HTTP status codes mean? Write the exact standard text phrase for each: (a) 200 (b) 403 (c) 503 |
| 6.8 | Simplify the following boolean expression using 4 variable K-map: F(A,B,C,D) = Σm(0,3,5,7,8,10,11,12,13,14,15). |
| 6.9 | Five channels, each with a 100-kHz bandwidth, are to be multiplexed together. What is the minimum bandwidth of the link if there is a need for a guard band of 10 kHz between the channels? |
| 6.10 | An organization is granted the IPv4 network block 14.24.74.0/24 … Subnet A (120 addresses), Subnet B (60 addresses) … Network Address and Broadcast Address for both. |
| 6.11 | A startup … does not want to manage hardware, OS or runtime … which Cloud Service Model (IaaS, PaaS, SaaS)? Give two real-world examples. |
| 6.12 | Define the following terms used in tree data structures: (i) Tree, (ii) Leaf Node, (iii) Internal Node, (iv) Height of a Tree. |
| 6.13 | Consider the following Java program and determine the integer value printed by main() — `static int x = 5; fun(n) { … x = x + 2; return fun(n-1) + x; }` printing `fun(3)`. |
| 6.14 | An array contains one million sorted integers. Which searching algorithm would you choose? Justify. |
| 6.15 | Consider the grammar: E → E+E | E*E | id. Show that the grammar is ambiguous for the string id + id * id. |
| 5.1 | What is the full form of NPSB in the banking sector of Bangladesh? |
| 5.2 | Who is the architect of the National Martyrs' Memorial in Savar? |
| 5.3 | What is the name of the central bank of the United Kingdom? |
| 5.4 | Which international organization publishes the "World Economic Outlook" report? |
| 5.5 | What is the name of the first submarine communications cable system that Bangladesh is connected to? |

Only two questions in the 2026 sitting are new: an e-commerce class diagram (`written/software-engineering.md`) and *"Discuss the impact of Artificial Intelligence and Automation on the banking sector of Bangladesh"* (`written/computer-fundamental.md`).

**Implication:** work the BB SO(IT) Grade-9 2024 paper end to end. It is a Bangladesh Bank IT written paper that has already demonstrated **20-of-22 reuse** in a later sitting.

### Other high-count repeats

| Repeats | Question (verbatim) | Sittings |
|---|---|---|
| **6** | *"Write down the difference between Interpreter and Compiler?"* | MRA AME 2020 · BPSC Home Affairs Assistant DBA (ICT) 2022 · CAAB AP 2022 · PGCB Sub-AE (CSE) 30.09.2021 · Combined Bank Officer (IT) 03.01.2026 · BPSC Ministry of Agriculture AP 15.02.2022 |
| **5** | *"What is the main difference between black box and white box testing?"* | BARC Programmer 04.08.2023 · BPSC AME (CSE) 2020 · MRA AME 2022 · Teletalk 2023 · SGFL 2021 |
| **4** | *"Given IP address 192.168.1.50, Subnet Mask: 255.255.255.240. Find the valid IP range. Also find Network address and Broadcast address."* | NWPGCL Assistant Manager (ICT) 12.01.2024 · BTCL Assistant Manager (Technical) 2023 · BPDB AE (CSE) 10.05.2024 · BIWTA AE (CSE) 24.02.2023 |
| **4** | *"Differentiate between IPv4 and IPv6."* | BMA Signal AE (Computer) 2021 · BPSC Security Services AME 15.12.2021 · BREB AGM (IT) 2021 · WZPGCL AE (CSE) 27.05.2023 |
| **3** | *"Write the Difference among Network Switch, Hub and Router."* | BMA Signal AE (Computer) 2021 · BPSC AME (ICT) 2020 · DESCO Sub-AE 20.05.2023 |
| **3** | *"What is SQL Injection? How to Prevent against SQL Injection Attacks?"* | RAKUB Programmer (PO) 12.10.2021 · RAKUB ME (PO) 05.10.2021 · Dhaka WASA AME (Network) 04.07.2025 |
| **3** | *"Distinguish between TCP and UDP protocols."* | BPSC Security Services AP 13.12.2021 · BPSC Home Affairs Senior Computer Operator (ICT) 13.09.2022 · Combined Bank Officer (IT) 03.01.2026 |
| **3** | *"What is the difference between supervised and unsupervised learning? Explain with examples."* | BPSC Security Services AP 13.12.2021 · SGFL 2021 · DPDC JAM 27.06.2025 |
| **3** | *"Assume a TDMA based communication system having 8 transmission receiver pairs. Each source is sampled at 8 kHz … calculate the data rate of TDMA line."* | BDCCL AE (Network) 2022 · BTCL Assistant Manager (Technical) 2021 · WASA AP 25.11.2022 |
| **3** | *"What is the port number used by DNS?"* | BARI AME 15.11.2025 · BBA AP 12.07.2025 · BCC AP 18.10.2025 |
| **2** | **Banker's Algorithm — 5 processes, A(10) B(5) C(7)** | **Bangladesh Bank AD(ICT) 07.02.2025** · RAKUB ME (PO) 05.10.2021 |
| **2** | **Firewall placement diagram for LAN / bank servers** | **Bangladesh Bank AD(ICT) 07.02.2025** · **Bangladesh Bank AP 2019** |
| **2** | *"Show minimal function using K-Map: F(A,B,C,D) = Σ(2,8,9,11,13,15)"* | BPDB AE (CSE) 10.05.2024 · BICIC AP 2022 |
| **2** | *"Simplify F(A,B,C,D) = ACD + AB + D̄ + AC̄D using K-map and draw the logic circuits"* | BPSC Home Affairs Assistant DBA (CSE) 2022 · BPSC AP (CSE) 2019 |
| **2** | *"What is the difference between latch and flip-flop?"* | **Bangladesh Bank AME 2017** · SPCBL AME 20.11.2021 |
| **2** | *"What is MVC? Write down the MVC design pattern."* | Pubali Bank Ltd. SO (SD) 2018 · WZPGCL AE (CSE) 27.05.2023 |
| **2** | *"What are the differences between call by value and call by Reference?"* | BPSC Home Affairs Assistant DBA (CSE) 2022 · BPSC Ministry of Agriculture AP 15.02.2022 |
| **2** | *"Explain the message flow / How does DHCP work?"* | Pubali Bank Hardware Engineer 18.03.2023 · BREB AP (AP) 21.02.2025 |

Note also the **Bangladesh Bank Recruitment Test 2020** paper: **15 of its 19 records are also tagged `Sonali & Janata Bank Officer (IT) 2020 (ET: DU)`** — i.e. its entire IT section is shared with a Sonali & Janata sitting set by the same exam taker (DU). Only the four general-section items (English paragraph + English translation, Bangla essay + Bangla translation) are Bangladesh-Bank-only. That is a second, independent proof that BB written IT questions are drawn from the same DU-set pool as the other state-owned banks.

---

## 🧩 Recurring Concepts

**C1 — "Give the schema, ask for normalization + keys."** 21 written normalization questions plus 34 key questions. The AD(ICT) 2025 form embeds it in a bank schema. Anticipate: decompose to 3NF/BCNF, name each relation's PK, name the FK, and justify.

**C2 — "Give the network block, ask for four numbers."** 109 subnetting questions, all reducible to: network address · subnet mask (CIDR + dotted decimal) · broadcast address · first/last usable host · usable host count. VLSM (unequal department sizes) is the harder variant that BB used in 2024.

**C3 — "Give the process table, draw the Gantt chart."** 31 CPU-scheduling questions across two subtopics. Always FCFS + SJF (preemptive and non-preemptive) + Priority + Round Robin, then average waiting time and average turnaround time.

**C4 — "Draw the security diagram."** Firewall/DMZ placement (**AD(ICT) 2025 and BB AP 2019**), LAN with firewall, NAT topology (13 questions), VPN site-to-site vs remote-access, DHCP message flow with a timing diagram. Bank setters want a *drawing*, not a paragraph.

**C5 — "Data-communication arithmetic."** Total latency (AD(ICT) 2025), propagation vs transmission delay, Nyquist and Shannon capacity (16 questions), multiplexing guard band (**BB SO(IT) 2024**), TDMA/TDM frame arithmetic (3-sitting repeat), optical-fibre power budget (13 questions), throughput and sliding-window efficiency.

**C6 — "Compare X and Y."** The single most common written verb in the bank: interpreter/compiler (6 sittings), black-box/white-box (5), IPv4/IPv6 (4), hub/switch/router (3), TCP/UDP (3), supervised/unsupervised (3), latch/flip-flop (2, incl. **BB AME 2017**), SRAM/DRAM, RAM/ROM, paging/segmentation, HDD/SSD, symmetric/asymmetric, overloading/overriding, process/thread, RISC/CISC, primary/foreign key, hashing/encryption (**BB SO(IT) 2024**), waterfall/agile. **Prepare these as ready-made 4–6 row tables.**

**C7 — "Write the program."** 111 basic-program questions + 38 recursion questions + 57 output-tracing questions in `written/c-programming.md`, plus 18 Java questions in `written/oop.md`. Bangladesh Bank's own asks were LCM (2023), Fibonacci (2016), array max (2019), overtime pay and recursive factorial (2020), and a multi-threaded Overdraft Account class (2019).

**C8 — "Bank-scenario wrapper."** Recurring bank-specific framings across the dataset: ATM testing (**BB AME 2019**), payment-gateway risk audit (**BB AME 2023**), core-banking DB vs archive storage choice (Combined Bank Officer (IT) 09.05.2026), banking software feature list (**BB Recruitment Test 2020**), Active Directory for a multi-department office (Combined Bank SO(IT) 17.05.2024), MFA for online banking (Combined Bank Officer (IT) 09.05.2026), digital vs traditional banking (Combined Bank AME/Hardware 23.11.2023), 0-bit data loss for 24×7×365 operation (Combined Bank SO(IT) 13.10.2023). **Expect the 2026 paper to wrap standard theory in a Bangladesh Bank scenario — that is exactly what AD(ICT) 2025 did in 4 of its 11 written questions.**

---

## 🔮 Predicted Written Questions

New questions written for practice. **None appeared in any historical paper.** Each is derived from a documented pattern above.

**🔮 Predicted W1 — Deadlock**
> *Basis:* AD(ICT) 2025 set the Banker's Algorithm on the standard 5-process / A(10) B(5) C(7) snapshot, which had already been set at RAKUB ME (PO) 2021.
>
> A system has 4 processes and 3 resource types A(9), B(6), C(6). Allocation = P0(2,1,1), P1(3,2,1), P2(1,1,2), P3(1,1,1); Max = P0(5,3,2), P1(6,3,3), P2(4,2,4), P3(3,2,2).
> (a) Build the Need matrix. (b) Determine whether the system is in a safe state and give a safe sequence. (c) If P1 now requests (1,0,1), can the request be granted immediately? Justify.

**🔮 Predicted W2 — Normalization on a banking schema**
> *Basis:* AD(ICT) 2025 gave `Bank(Br_Name, Br_City, Assets, Acc_name, Acc_Num, Balance)` and asked for normalization + PK/FK.
>
> Consider `Loan(Loan_No, Br_Name, Br_City, Assets, Cust_ID, Cust_Name, Cust_Address, Amount)`.
> (a) Identify the functional dependencies. (b) Decompose to 3NF. (c) Mark the primary key and foreign key of each resulting relation. (d) State why the decomposition is lossless.

**🔮 Predicted W3 — Firewall / DMZ diagram**
> *Basis:* the identical drawing task was set at BB AP 2019 and again at AD(ICT) 2025.
>
> A bank runs an internet-banking web server, a public DNS server, a mail server and an internal core-banking database. Draw the network with an external firewall, a DMZ and an internal firewall. Mark which servers sit in the DMZ, which traffic each firewall permits, and explain why the core-banking database must never be placed in the DMZ.

**🔮 Predicted W4 — Data-communication latency**
> *Basis:* AD(ICT) 2025 asked total latency for a 3-kbyte message over 1 Gbps at 300 km with RTT and queuing time.
>
> A 5-Mbyte file is transferred over a 100-Mbps link between two branches 600 km apart. Propagation speed is 2×10⁸ m/s, queuing delay is 10 ms and processing delay is negligible. Compute the transmission delay, propagation delay and total latency, and state which term dominates and why.

**🔮 Predicted W5 — Email architecture**
> *Basis:* AD(ICT) 2025 asked the protocols and the step-by-step mail path (Sinthia → Afsana).
>
> An employee at `branch.bank.gov.bd` sends a mail to `customer@example.com`. (a) List every protocol involved from composition to retrieval, with its layer and port. (b) Draw the MUA/MTA/MDA path and the DNS query that makes it work. (c) Explain what changes if the recipient uses IMAP instead of POP3.

**🔮 Predicted W6 — Subnetting / VLSM**
> *Basis:* BB SO(IT) 2024 asked a two-subnet sequential allocation from a /24; the topic holds 109 written questions.
>
> A bank branch is granted `172.20.16.0/22`. It must serve Core Banking (500 hosts), ATM network (120 hosts), CCTV (60 hosts) and Staff Wi-Fi (25 hosts). Using VLSM and allocating largest-first, give for each: network address with CIDR mask, subnet mask in dotted decimal, first and last usable host, and broadcast address.

**🔮 Predicted W7 — CPU scheduling**
> *Basis:* 31 written CPU-scheduling questions; the five-process priority table is set at the sibling BPSC AD(ICT) 2025 post.
>
> Processes P1–P5 arrive at time 0 with burst times 8, 2, 7, 3, 5 and priorities 3, 1, 4, 2, 5 (lower number = higher priority).
> (a) Draw the Gantt chart for FCFS, SJF (non-preemptive), Priority (non-preemptive) and Round Robin (quantum = 3).
> (b) Compute average waiting time and average turnaround time for each. (c) Which algorithm risks starvation and why?

**🔮 Predicted W8 — Cache**
> *Basis:* BB set direct-mapped cache field sizes in 2023, average access time in 2017, and miss classification in 2024.
>
> A processor uses a 32-bit address and a direct-mapped cache of 32 KB with 8-word (32-byte) blocks. (a) Compute the number of blocks, and the width of the offset, index and tag fields. (b) If the hit time is 2 ns, the miss penalty 80 ns and the hit rate 95%, compute the average memory access time. (c) Classify a miss on the very first reference to a block and a miss caused by the working set exceeding cache capacity.

**🔮 Predicted W9 — SQL**
> *Basis:* BB SO(IT) 2024's aggregation query was reused verbatim in 2026; department-wise aggregation is the single most repeated SQL shape in the bank.
>
> Given `Account(Acc_No, Br_Name, Balance)` and `Branch(Br_Name, Br_City, Assets)`:
> (a) List each branch city with its total deposit and its number of accounts. (b) List branches whose average balance exceeds the overall average balance across all branches. (c) Write the query that returns the second-highest balance without using `LIMIT`/`TOP`.

**🔮 Predicted W10 — Security concepts**
> *Basis:* BB SO(IT) 2024 asked hashing vs encryption; BB AP 2023 asked the CIA-to-attack mapping; AD(ICT) 2025's English topic was AI against banking cyber-attacks.
>
> (a) Explain the operational difference between hashing, symmetric encryption and asymmetric encryption, with one banking use case for each. (b) A customer disputes a transaction they actually authorised. Which security service prevents this, and which cryptographic mechanism provides it? (c) Give one attack that primarily violates each of Confidentiality, Integrity and Availability.

---

## 🏆 Final Written Ranking

| Rank | Topic | Why it ranks here |
|---|---|---|
| 1 | **Banker's Algorithm + deadlock conditions** | AD(ICT) 2025 question 1; the same instance already repeated once (RAKUB 2021); 23 written questions |
| 2 | **Normalization of a bank schema + PK/FK identification** | AD(ICT) 2025 question; 21 normalization + 34 key questions |
| 3 | **Firewall / DMZ diagram for bank servers** | Bangladesh Bank asked it twice (AP 2019, AD(ICT) 2025); 20 firewall questions |
| 4 | **Subnetting & VLSM** | 109 questions — the densest topic in the bank; BB SO(IT) 2024's version was reused verbatim in 2026 |
| 5 | **SQL: GROUP BY aggregation, joins, above-average, nth-highest** | 87 questions; BB asked SQL in 4 separate sittings; BB SO(IT) 2024's query was reused verbatim |
| 6 | **CPU scheduling Gantt charts (FCFS/SJF/Priority/RR)** | 31 written questions; set at the sibling BPSC AD(ICT) post |
| 7 | **Data-communication arithmetic (latency, Nyquist, Shannon, multiplexing)** | AD(ICT) 2025 question; BB SO(IT) 2024 guard-band question; 16 + 18 + 14 questions across three subtopics |
| 8 | **Email architecture: SMTP/POP3/IMAP path and protocols** | AD(ICT) 2025 question; BB AME 2017; 10 questions |
| 9 | **K-map simplification + truth table from a Boolean expression** | AD(ICT) 2025 truth table; BB SO(IT) 2024 K-map (reused 2026); 19 + 33 questions |
| 10 | **Cache memory (miss types, direct-mapped fields, average access time)** | Bangladesh Bank asked cache in three separate sittings (2017, 2023, 2024) |
| 11 | **Heap construction / heapify / heapsort** | AD(ICT) 2025 min-heap question; 10 questions across two files |
| 12 | **OOP: polymorphism, overloading vs overriding, inheritance with code** | Bangladesh Bank asked OOP in four separate sittings; 54-question subtopic |
| 13 | **Software testing (unit vs integration, black-box vs white-box, V&V)** | BB SO(IT) 2024 + BB AME 2023 + BB AME 2019 + BB 2020; 40-question subtopic; 5-sitting repeat |
| 14 | **Cryptography: hashing vs encryption, symmetric vs asymmetric, digital signature, CIA** | BB SO(IT) 2024 + BB AP 2023; 31 + 8 questions |
| 15 | **Pipelining and hazards** | Bangladesh Bank asked it in three separate sittings (2011, 2019, 2024) |
| 16 | **Linux commands** | 47 questions — the largest OS subtopic; standard bank-written filler that is pure marks |
| 17 | **OSI/TCP-IP layers with protocols and devices** | 52 questions; BB AP 2023 and BB AP 2019 both used it |
| 18 | **Sorting: trace + complexity table; BFS/DFS; Kruskal MST** | 36 + 17 + 15 questions; BB Recruitment Test 2020 asked insertion sort |
| 19 | **SDLC / Agile vs Waterfall + UML class & use-case diagrams** | 45 + 14 questions; BB AP 2023 asked a class diagram |
| 20 | **Math (probability, integration, set theory) and English (banking focus writing + Bangla→English)** | 50 of the 200 written marks; AD(ICT) 2025 gave 2 math + 2 English questions |

---

## 🚨 Last-Minute Written Suggestion

If preparation time is nearly gone, these 20 carry the most marks per minute. Every one is anchored to a real historical question.

1. **Banker's Algorithm** — build the Need matrix, run the safety algorithm, write the safe sequence. Practise the standard 5-process / A(10) B(5) C(7) snapshot. *(AD(ICT) 2025 + RAKUB 2021)*
2. **Four deadlock conditions** — mutual exclusion, hold-and-wait, no preemption, circular wait; plus prevention vs avoidance vs detection. *(23 questions)*
3. **Normalize a bank schema to 3NF** and mark PK/FK on each relation, then justify. *(AD(ICT) 2025)*
4. **1NF → 2NF → 3NF → BCNF mapping**: repeating groups → partial dependency → transitive dependency → every determinant is a candidate key. *(21 questions)*
5. **Firewall/DMZ diagram** for bank Mail + DNS + Web servers, with the internal LAN behind a second firewall. *(AD(ICT) 2025 + BB AP 2019)*
6. **Subnetting drill**: given a block and host requirements, produce network address, mask (CIDR + dotted), first/last usable host, broadcast, and host count. Then do the VLSM version largest-first. *(109 questions)*
7. **SQL aggregation set**: `GROUP BY` with `COUNT`+`AVG`; `HAVING` above the overall average; the four JOIN types; second-highest salary. *(87 questions; BB SO(IT) 2024 reused verbatim in 2026)*
8. **CPU scheduling**: Gantt chart + AWT + ATAT for FCFS, SJF, Priority and RR from one process table. *(31 questions)*
9. **Total latency formula**: propagation (d/s) + transmission (L/B) + queuing + processing; then Nyquist `C = 2B log₂L` and Shannon `C = B log₂(1+SNR)`. *(AD(ICT) 2025 + 16 capacity questions)*
10. **Multiplexing guard band**: n channels × bandwidth + (n−1) × guard band. *(BB SO(IT) 2024, reused 2026)*
11. **Email path**: SMTP (25/587) sending, POP3 (110) / IMAP (143) retrieval, DNS MX lookup, TCP at transport — plus the MUA→MTA→MDA diagram. *(AD(ICT) 2025)*
12. **Truth table from a Boolean expression** and **4-variable K-map to minimal SOP** with loops drawn. *(AD(ICT) 2025 + BB SO(IT) 2024)*
13. **NAND/NOR universality** — build AND, OR, NOT, XOR from NAND only; and a full adder from two half adders. *(33 + 23 questions; BB AME 2011 and 2019)*
14. **Min-heap / max-heap construction** from a value list, plus heapify after deletion. *(AD(ICT) 2025)*
15. **Cache**: compulsory vs capacity vs conflict miss; direct-mapped tag/index/offset split; average access time = hit-time + miss-rate × miss-penalty. *(BB 2017, 2023, 2024)*
16. **Comparison tables ready to write cold**: interpreter/compiler · black-box/white-box · TCP/UDP · IPv4/IPv6 · hub/switch/router · SRAM/DRAM · paging/segmentation · overloading/overriding · process/thread · hashing/encryption · symmetric/asymmetric · RAID 1/RAID 5 · VM/container. *(each 2–6 sittings)*
17. **Polymorphism + overloading vs overriding with a short Java/C++ example.** *(BB asked OOP in 4 sittings)*
18. **Linux one-liners**: `ls -la`, `chmod 755` / `chmod -R a+x`, `grep`, `head -n` / `tail -f`, `df -h`, `free -m`, `top`, `rm -r`, `cp -r`, `ifconfig`/`ip a`, `ping`, `traceroute`, `crontab`. *(47 questions)*
19. **Security short answers**: CIA triad mapped to attacks · digital signature = sign with sender's private key, verify with sender's public key · SQL injection prevention (parameterised queries + input validation) · 2FA · DoS vs DDoS vs MITM vs phishing. *(31 + 32 + 19 + 16 questions)*
20. **English + Math**: one 150-word banking/technology focus write-up (AI in banking, cashless economy, cyber security in banks — all three are historical BB topics) · Bangla→English of two banking sentences · one probability problem · one definite integral. *(AD(ICT) 2025 gave exactly this mix; 50 of 200 marks)*

---

### Verification note

Everything cited above is traceable to a tag inside `all-questions/written/` or `all-questions/mcq/`. No exam name, year, post, count or repetition figure in this document was estimated. Predicted questions are confined to the **🔮 Predicted Written Questions** section and are labelled individually.
