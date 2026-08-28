# Bangladesh Bank — Assistant Director (ICT) 2026 : MCQ Suggestion

> Prepared **28 August 2026**, roughly four weeks before the exam.
> Built from the full question bank in this repo: **2,781 MCQ** + **2,726 written** questions across 581 distinct exams,
> of which **1,361 MCQ came from bank-sector exams** and **45 MCQ from the last AD(ICT) paper (07.02.2025, conducted by DU)**.

---

## 1. Exam snapshot

| Paper | Marks | Time | Breakdown |
|---|---|---|---|
| **MCQ** | 100 | 10:00–11:00 am (1 hr) | **IT 75 · Math 15 · GK 10** |
| Written | 200 | 11:00 am–1:00 pm (2 hr) | IT 150 · Math 20 · English 30 |

Three things that change how you should prepare:

1. **MCQ is a gate.** If you don't pass MCQ, your written script is never marked. Everything below is therefore about *clearing the gate reliably*, not about scoring maximum.
2. **60 minutes ÷ 100 questions = 36 seconds per question.** This is a speed exam. Topics you "sort of know" cost you two questions each — the one you get wrong and the one you run out of time for.
3. Final selection weight comes from **Written + Viva**. So MCQ needs to be *passed efficiently*, not perfected.

---

## 2. The post merger — the single biggest edge in this suggestion

Bangladesh Bank previously ran **separate circulars** for *Assistant Programmer* (CSE-flavoured) and *Assistant Maintenance Engineer* (EEE / hardware-flavoured). These two posts are now **merged into Assistant Director (ICT)**.

The 2025 AD(ICT) paper shows exactly what that merger did to the question mix:

| | Share of pure **Electronics / EEE** questions |
|---|---|
| Average across all bank-sector MCQ in this bank (mostly old AP-only papers) | **1.2 %** |
| Actual AD(ICT) 2025 paper (DU) | **13 %** (6 of the 45 captured) |

The six were all *first-year electronics*, not deep EEE:

- What is the work of a **Rectifier**?
- **Zener diode** is a ______ conducting device
- What should be true for a **Zener Diode**? (reverse breakdown region)
- Which device converts **AC to DC**?
- What does **inductance** depend on?
- 10 Ω, 20 Ω, 30 Ω **in parallel** across 60 V — find total current

**Why this matters:** a CSE-background candidate typically skips this entirely. It is roughly **6–8 easy marks** that take about **six hours** to prepare. This is the highest return-per-hour item on the whole syllabus. Do not skip it.

The same logic applies, less dramatically, to **hardware / peripherals / memory-hierarchy** questions, which were the AME paper's bread and butter (BB AME 2011 alone had 8 hardware-component questions).

---

## 3. Recommended mark allocation for IT-75

Two data columns, then a recommendation. The 2025 column is a small sample (45 of 100 questions captured), so it is used to *tilt* the historical baseline, not to replace it.

| # | Topic | Historical bank-sector share | AD(ICT) 2025 (scaled) | **Target questions** |
|---|---|---|---|---|
| 1 | **Computer Networks** | 19.6 % | ~2 | **12** |
| 2 | **Database / SQL** | 14.1 % | ~11 | **10** |
| 3 | **Electronics (EEE basics)** | 1.2 % | ~13 | **6** |
| 4 | **Data Structure** | 5.3 % | ~9 | **5** |
| 5 | **Security & Cryptography** | 5.3 % | ~9 | **5** |
| 6 | **C / C++ output tracing** | 6.3 % | ~4 | **5** |
| 7 | **OOP (Java/C++)** | 6.9 % | ~4 | **4** |
| 8 | **Computer Fundamentals & Hardware** | 7.8 % | ~0 | **4** |
| 9 | **Microprocessor & Architecture** | 6.1 % | ~0 | **4** |
| 10 | **Operating System** | 5.2 % | ~4 | **4** |
| 11 | **Digital Logic Design** | 3.6 % | ~4 | **3** |
| 12 | **Algorithm** | 4.3 % | ~2 | **3** |
| 13 | **Software Engineering** | 3.9 % | ~4 | **3** |
| 14 | **Web Technology** | 3.9 % | ~4 | **2** |
| 15 | **Cloud & Virtualization** | 1.4 % | ~2 | **2** |
| 16 | AI/ML, MS Office, compiler, misc | 2.8 % | ~1 | **3** |
| | | | | **75** |

**Reliability check** — how many *distinct* bank exams have asked from each area (out of the bank-sector exams in this repo). This is a better signal than raw counts, because it measures *how dependably* a topic shows up:

| Distinct exams | Topic |
|---|---|
| **21** | Networking fundamentals & terminology |
| **20** | SQL commands & queries |
| **18** | Application layer protocols |
| **17** | Java programming |
| **16** | Subnetting & IP addressing |
| **14** | CPU & registers |
| **13** | Computer fundamentals / generations · Software types · Number systems |
| **12** | Network devices · DBMS concepts · C output tracing · Sorting |
| **11** | Searching · Normalization |
| **10** | International affairs · Software testing · Stack & Queue · IPv6 |

Anything in that table is a topic that has appeared in **more than half** of all bank IT exams. Those are non-negotiable.

---

## 4. Tiered study list

### Tier 1 — must be automatic (≈45 of 75 IT marks)

**Computer Networks (12)**
- Subnetting & CIDR: given a host requirement → find CIDR + subnet mask; given an IP → find class, network, broadcast. *2025 asked exactly this: "192.168.3.0, need 254 usable hosts — CIDR and subnet mask?"*
- OSI vs TCP/IP: layer order, what sits at each layer, one protocol per layer
- Port numbers: 20/21 FTP, 22 SSH, 23 Telnet, 25 SMTP, 53 DNS, 67/68 DHCP, 80 HTTP, 110 POP3, 143 IMAP, 443 HTTPS, 3389 RDP
- Devices: hub vs switch vs router vs bridge vs repeater vs gateway — and which OSI layer each works at
- DNS and DHCP working steps (DORA); ARP vs RARP; NAT vs PAT
- IPv4 vs IPv6 (header, address size, why IPv6)
- Topologies and their failure behaviour

**Database (10)**
- SQL clause **execution order**: FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY. *2025 asked "which clause executes first" — answer FROM, not SELECT.*
- DDL / DML / DCL / TCL classification — CREATE/ALTER/DROP/TRUNCATE vs INSERT/UPDATE/DELETE/SELECT vs GRANT/REVOKE vs COMMIT/ROLLBACK/SAVEPOINT
- ACID mapped to failure scenarios. *2025: "A transfers to B but B doesn't receive — which ACID property?" → **Atomicity**.*
- Normalization 1NF→2NF→3NF→BCNF, and which anomaly each removes
- Keys: super, candidate, primary, foreign, composite
- Indexing (what speeds up reads, and its write cost); clustered vs non-clustered
- DELETE vs TRUNCATE vs DROP — a perennial favourite
- JOIN types + basic GROUP BY/HAVING/aggregate output prediction

**Electronics — EEE basics (6)** ← *the merger topic*
- Diode, Zener diode (reverse breakdown, voltage regulation), LED
- Rectifier: half-wave vs full-wave vs bridge; AC↔DC direction; inverter vs rectifier vs transformer
- Ohm's law; series vs parallel resistance; current/voltage division
- Capacitance and inductance — what each depends on, energy stored, behaviour in DC vs AC
- Transistor basics: BJT vs FET, regions of operation, transistor as switch
- Logic families: TTL vs CMOS (power, speed, noise margin)
- Basic power: kVA vs kW, UPS, power factor (data-centre flavoured questions do appear)

**Data Structure (5)**
- Time complexity table for array / linked list / stack / queue / BST / heap / hash — insert, delete, search, worst vs average
- **Priority queue is implemented with a heap** — 2025 asked this *twice*
- Stack applications: function calls, expression evaluation, infix→postfix, undo, backtracking
- Tree traversals, and reconstructing a tree from (inorder + preorder) or (inorder + postorder)
- BST vs AVL vs B-tree vs B+ tree — where each is used (B+ tree → DB indexing)

**Security & Cryptography (5)**
- Symmetric vs asymmetric; AES/DES vs RSA/Diffie-Hellman; which is faster and why
- **Digital signature uses asymmetric (RSA): sign with private key, verify with public key** — 2025 asked this twice in different wording
- Hashing (MD5/SHA) vs encryption — hashing is one-way, no key
- TLS/SSL for data in transit; HTTPS; what TLS actually protects
- CIA triad mapped to scenarios
- Attack vocabulary: phishing/spear-phishing/whaling, ransomware, MITM, DoS vs DDoS, SQL injection, XSS, CSRF, ARP poisoning, zero-day

**C / C++ output tracing (5)**
- Pointer parameters and dereferencing (`*p = *p + 10`) — 2025 asked exactly this pattern
- `++i` vs `i++` inside expressions and printf argument lists
- Operator precedence and integer division / type promotion
- Static variables, scope, and recursion return values
- Array–pointer arithmetic, string functions, `sizeof`
- Missing braces / dangling else — 2025's second output question was a plain if-else trap

### Tier 2 — solid coverage (≈22 marks)

- **OOP (4):** encapsulation (2025: *global variables break encapsulation*), overloading vs overriding, static vs dynamic binding, abstract class vs interface, constructor/destructor order, which operators are better overloaded as global functions (2025 asked: insertion `<<`)
- **Computer Fundamentals & Hardware (4):** generations, RAM vs ROM types, cache levels, motherboard/BIOS/CMOS, printer & storage types, units and conversions, common acronyms
- **Microprocessor & Architecture (4):** 8085/8086 registers, EU/BIU, addressing modes, RISC vs CISC, pipelining basics, memory hierarchy speed/cost order, cache mapping types, Von Neumann vs Harvard
- **Operating System (4):** process states (2025: *I/O request → Waiting/Blocked*), scheduling algorithms and computing AWT/ATAT (2025 had a non-preemptive priority TAT calculation), deadlock's four conditions, paging vs segmentation, page replacement (FIFO/LRU/Optimal), multiprogramming vs multitasking vs multiprocessing, common Linux commands
- **DLD (3):** universal gates (NAND/NOR — the most repeated MCQ in this entire bank, 3 exams), number-system and 2's-complement conversion (2025: 2's complement of hex 65), K-map basics, adders, MUX/decoder, flip-flops
- **Algorithm (3):** complexity of the standard sorts and searches, when linear search beats binary (2025 asked this — answer: works on unsorted data), greedy vs DP vs divide-and-conquer, recurrence/Master theorem basics

### Tier 3 — light pass, do not over-invest (≈8 marks)

- **Software Engineering (3):** SDLC models and waterfall's drawback (2025), testing types — unit / **integration = interface between modules** (2025) / system / acceptance, black vs white box, verification vs validation
- **Web Technology (2):** HTTP status codes (2025: **500 = Internal Server Error**), GET vs POST, what is/isn't a web server (2025: PHP is not), HTML/CSS basics, REST vs SOAP
- **Cloud (2):** IaaS/PaaS/SaaS with examples, public/private/hybrid, VM vs container, **Docker vs Docker Hub** (2025)
- **AI/ML + misc (3):** supervised vs unsupervised vs reinforcement, ML vs DL, agent types, blockchain basics; plus stray MS Office / compiler-vs-interpreter items

---

## 5. Math — 15 marks

Straightforward bank math, no calculus in the MCQ. Historical bank-sector distribution:

| Topic | Weight | What to drill |
|---|---|---|
| Algebra | highest (18 of 62) | equations, indices, simplification |
| Percentage, profit & loss | 8 | salary/discount/interest chains — *2025: 30 %+20 %+10 % spent, 12,000 left, find salary* |
| Geometry | 6 | triangle, circle, area/perimeter |
| Arithmetic & number series | 6 | series completion, LCM/HCF |
| Time, work & distance | 6 | pipes & cisterns — *2025: 4 hr + 6 hr pipes together* |
| Set theory | 6 | two/three-set Venn |
| Ratio & proportion | 5 | partnership, mixture |
| Average & age | 3 | *2025: father 36, son 16, when was father 3× son* |
| Analytical reasoning | 2 | direction/distance and weighing puzzles — *2025 had both* |

Note that **five of the 2025 math questions map exactly onto five different rows above** — the coverage is broad but each type is standard. Drill one worked example of each type and you have the whole 15 marks.

## 6. GK — 10 marks

Split roughly evenly between **Bangladesh Affairs (30)** and **International Affairs (30)** historically, plus sports and geography.

- **Current affairs of the last 6–12 months** carry the most weight. 2025 asked the 2024 Nobel Peace Prize (Nihon Hidankyo).
- **Banking terminology** is the highest-yield GK sub-area for this specific post: NPSB, BEFTN, RTGS, BACH, MFS, CBDC, SWIFT, LC, CRR/SLR, repo/reverse repo, inflation, remittance figures, foreign-exchange reserve, Basel III.
- Bangladesh: constitution basics, rivers/geography (2025: highest peak = Saka Haphong), liberation war, budget and current economic indicators.
- International: UN bodies, IMF/World Bank reports, capitals/currencies, Suez/Hormuz-type geography (2025 asked Suez), major sporting firsts.

Bangla and English MCQ also appear inside the general portion — **বাংলা ব্যাকরণ (39)** dominates over সাহিত্য (23), and **English grammar (35)** dominates over vocabulary (13). For both, past-paper repetition is high, so revising previous years' questions is more efficient than reading a grammar book cover to cover.

---

## 7. Your single best mock — the AD(ICT) 2025 (DU) paper

This is the only paper written for *this exact post* by *the same style of examiner*. Sit it under timed conditions before you do anything else, so you can calibrate. All 45 captured questions are already in this repo, tagged `Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)`.

Pull them with:

```
grep -rn "Assistant Director (ICT) Exam: 07.02.2025" mcq/
```

Where they live:

| File | Questions |
|---|---|
| [electrical-and-electronics.md](../../mcq/electrical-and-electronics.md) | 6 |
| [database.md](../../mcq/database.md) | 6 |
| [gk.md](../../mcq/gk.md) | 5 |
| [math.md](../../mcq/math.md) | 5 |
| [computer-network-security.md](../../mcq/computer-network-security.md) | 4 |
| [data-structure.md](../../mcq/data-structure.md) | 4 |
| [c-programming.md](../../mcq/c-programming.md) | 2 |
| [dld.md](../../mcq/dld.md) | 2 |
| [oop.md](../../mcq/oop.md) | 2 |
| [software-engineering.md](../../mcq/software-engineering.md) | 2 |
| [web-technology.md](../../mcq/web-technology.md) | 2 |
| [operating-system.md](../../mcq/operating-system.md) | 2 |
| [computer-networks.md](../../mcq/computer-networks.md), [cloud-computing.md](../../mcq/cloud-computing.md), [algorithm.md](../../mcq/algorithm.md) | 1 each |

**Second and third priority papers**, in order:

1. `Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)` — 25 MCQ, the CSE half of the merged post
2. `Bangladesh Bank Assistant Maintenance Engineer Exam: 04.02.2023 (BIBM)` — 25 MCQ, the EEE/infrastructure half
3. `Bangladesh Bank Assistant Director (IT) Preliminary Exam: 2016` — 25 MCQ, heavy on memory hierarchy and storage
4. `Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)` — 100 questions, the largest single recent bank paper in the repo
5. `Bangladesh Bank Senior Officer (IT), Grade-9 Exam: 2024` — 24 questions

---

## 8. Four-week plan

**Week 1 — establish the floor**
- Day 1: sit AD(ICT) 2025 timed. Score it. Note which of the 16 topic rows you lost marks in.
- Days 2–4: Computer Networks Tier-1 list end to end. Do 40 subnetting problems until CIDR↔mask is instant.
- Days 5–6: Database Tier-1 list. Write out the clause-execution order and ACID-scenario mapping from memory.
- Day 7: **Electronics crash course** — the entire Tier-1 EEE list in one sitting. It is genuinely only a few hours.

**Week 2 — the middle block**
- Days 8–9: Data Structure complexity table + heap/priority-queue + traversals
- Days 10–11: Security & cryptography, with special attention to digital signature key direction
- Days 12–13: C/C++ output tracing — 60 snippets minimum, mostly pointers and `++`
- Day 14: BB AP 2023 + BB AME 2023 papers, timed

**Week 3 — Tier 2 and general**
- Days 15–16: OOP + Computer Fundamentals/Hardware
- Days 17–18: Microprocessor/Architecture + OS
- Day 19: DLD + Algorithm
- Days 20–21: Math (one worked example of each of the nine types) and GK/banking terminology

**Week 4 — consolidation only**
- Days 22–24: Tier 3 light pass (SE, Web, Cloud, AI) — one day total for all four, then re-drill weak Tier-1 areas
- Days 25–26: two full timed mocks from the priority paper list, 100 questions in 60 minutes
- Day 27: revise your own error log only
- Day 28: light revision of formulas, port numbers, complexity table, ACID, status codes. Sleep.

---

## 9. Exam-hall tactics

- **Three passes.** Pass 1: answer everything you know instantly (~40 questions, 15 min). Pass 2: the ones needing 20–40 seconds of work (~35 questions, 25 min). Pass 3: the calculation-heavy ones (~25 questions, 20 min).
- **Never compute subnetting or scheduling maths on the first pass.** They are worth the same one mark as "which is a universal gate", and they eat four times the time.
- Confirm the **negative-marking rule** on the question paper before you start guessing. Bank MCQs commonly carry 0.25–0.50 penalty; if there is none, leave nothing blank.
- Electronics and GK questions are almost always fast — sweep them early to bank easy marks.
- Keep an eye on the clock at question 50. You should be there by minute 28.

---

### Source and honest limits

Everything above is derived from the question bank in this repo — 2,781 MCQ across 581 exam tags, filtered to the 1,361 from bank-sector exams. Two caveats worth stating plainly:

- Only **45 of the 100** questions from the AD(ICT) 2025 paper are captured here. Its topic proportions happen to line up well with the official IT-75 / Math-15 / GK-10 split, which is reassuring, but a 45-question sample still carries real noise. That is exactly why the recommended allocation blends it with the historical baseline rather than following it directly.
- The exam-conducting body for 2026 is not yet confirmed. 2025 was **DU**. If it turns out to be **BUET**, expect noticeably more calculation — shift weight toward subnetting, scheduling, cache and pipelining maths, and C output tracing.
