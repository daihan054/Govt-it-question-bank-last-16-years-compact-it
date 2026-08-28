# Bangladesh Bank — Assistant Director (ICT) 2026 : Written Suggestion

> Prepared **28 August 2026**, roughly four weeks before the exam.
> Built from the full question bank in this repo: **2,726 written** + **2,781 MCQ** questions across 581 distinct exams,
> of which **477 written questions came from bank-sector exams** and **11 from the last AD(ICT) paper (07.02.2025, conducted by DU)**.

---

## 1. Exam snapshot

| Paper | Marks | Time | Breakdown |
|---|---|---|---|
| MCQ | 100 | 10:00–11:00 am | IT 75 · Math 15 · GK 10 |
| **Written** | **200** | **11:00 am–1:00 pm (2 hr)** | **IT 150 · Math 20 · English 30** |

Three consequences you should plan around:

1. **The written script is only marked if you pass MCQ.** Clear that gate first — see the companion [MCQ suggestion](mcq-bb-ad-ict-suggestion.md).
2. **200 marks in 120 minutes = 36 seconds per mark.** A 20-mark question gets 12 minutes, including the diagram. You cannot write essays. You write *structured, labelled, complete* answers, fast.
3. **Written + Viva decide the final job.** This is the paper that actually gets you selected, so depth matters here in a way it doesn't in the MCQ.

Note there is **no Bangla component in the written mark distribution** (IT 150 + Math 20 + English 30 = 200). Some other bank papers do carry Bangla focus writing; for this post the written language paper is English. Prepare Bangla for the MCQ general portion, not for the written.

---

## 2. The post merger, and what it means here

Bangladesh Bank used to issue separate circulars for **Assistant Programmer** (CSE) and **Assistant Maintenance Engineer** (EEE / hardware / infrastructure). These are now merged into **Assistant Director (ICT)**.

In the MCQ this shows up as a burst of basic-electronics questions. In the **written** paper the merger shows up differently — as **infrastructure-flavoured IT questions**:

- firewall / server-topology **diagrams** (2025 asked exactly this)
- RAID levels and their trade-offs — 5 bank-sector written questions, 4 distinct exams
- data-centre power, UPS, server hardware — 5 questions under *Server Hardware & Enterprise Systems*
- HDD vs SSD selection for a banking workload, disk-pack capacity maths
- cache/memory sizing maths

So for the written paper, do not read "merged post" as "learn circuit theory". Read it as **"be able to draw and justify a bank's IT infrastructure."**

---

## 3. The 2025 AD(ICT) written paper — your template

This is the single most valuable artifact available. Eleven questions are captured in this repo, tagged `Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)`:

| # | Question | Area | File |
|---|---|---|---|
| 1 | **Construction of Min Heap** from 12, 29, 33, 56, 66, 99, 100, 344 | Algorithm | [algorithm.md](../../written/algorithm.md) |
| 2 | **Banker's Algorithm** — 5 processes P₀–P₄, resources A(10) B(5) C(7); find Need matrix; safe or unsafe | OS | [operating-system.md](../../written/operating-system.md) |
| 3 | **Total latency** for a 3-kbyte e-mail at 1 Gbps, 300 km, light 2×10⁸ m/s, RTT 50 ms, queuing 5 ms | Networks | [computer-networks.md](../../written/computer-networks.md) |
| 4 | **E-mail transfer** — (a) application & transport layer protocols (b) steps of mail transfer | Networks | [computer-networks.md](../../written/computer-networks.md) |
| 5 | **Bank schema normalization** — `Bank(Br_Name, Br_City, Assets, Acc_name, Acc_Num, Balance)`; normalize, identify PK/FK, justify the schema | Database | [database.md](../../written/database.md) |
| 6 | **Firewall diagram** — BB client–server with Mail, DNS and Web servers; draw the secured topology | Security | [computer-network-security.md](../../written/computer-network-security.md) |
| 7 | **Truth table** for `Ā·B̄·(A+B)‾·C` | DLD | [dld.md](../../written/dld.md) |
| 8 | **∫₀² (2x² + 3x) dx** | Math | [math.md](../../written/math.md) |
| 9 | **Probability** — 6 ADs (all bring a bag), 4 DDs (half bring a bag); a bag is picked at random, P(belongs to a DD)? | Math | [math.md](../../written/math.md) |
| 10 | **Short note (100–150 words)** — "The role of AI and machine language to mitigate challenges of cyber attack on banking system" | English | [english.md](../../written/english.md) |
| 11 | **Bengali → English translation** — two banking sentences | English | [english.md](../../written/english.md) |

Read the pattern off that list, because it repeats:

- **Seven IT questions ≈ 150 marks**, so roughly **20 marks each**, roughly **12 minutes each**.
- Every single IT question is either a **computation** or a **diagram**. Not one is "write an essay on X".
- **Banking context is deliberately woven in** — the schema is a bank schema, the firewall is Bangladesh Bank's, the probability question is about ADs and DDs. Expect this again.
- Math is **2 questions / 20 marks**, and unlike the MCQ it *does* include calculus.
- English is **2 questions / 30 marks** — one short note plus one translation.

Pull the whole paper with:

```
grep -rn "Assistant Director (ICT) Exam: 07.02.2025" written/
```

---

## 4. IT-150 — topic priorities

Ranked by **how many distinct bank exams** have asked from each area (the reliability measure), cross-checked against the 2025 paper.

### Tier 1 — expect one question from each of these

**Computer Networks — 16.4 % of all bank-sector written questions, the single largest area**

- **Subnetting & VLSM** (10 distinct exams, 12 questions). Given `192.168.10.0/24` → divide into 4 equal subnets; state borrowed bits, new mask, network/first-usable/broadcast per subnet. Also `172.16.0.0/19` → how many subnets and hosts. Practise until you can do a full VLSM table in 6 minutes.
- **Latency / throughput maths** — total latency = propagation + transmission + queuing + RTT. The 2025 question is the canonical form; be fluent with unit conversion (km ÷ m/s, kbyte → bits, Gbps).
- **Channel capacity** — Nyquist `C = 2B log₂L` and Shannon `C = B log₂(1+SNR)`; SNR in dB vs ratio. A recurring form: telephone line 3000 Hz, SNR 3162.
- **Multiplexing** (7 exams) — TDM vs FDM vs WDM, pulse-stuffing TDM, frame rate and bit-rate calculations.
- **CRC** — original data 11100, divisor 1001 → find the transmitted frame and check at the receiver.
- **OSI / TCP-IP** (6 exams) — layer functions, protocol per layer, and the differences table.
- **E-mail architecture** — SMTP vs POP3 vs IMAP, MTA/MUA, and the end-to-end step sequence (2025).
- **PCM** — sampling rate, quantization levels, bit rate.
- Routing protocols, transmission media, flow control (stop-and-wait, Go-Back-N) with efficiency maths.

**Database — 10.9 %**

- **Normalization to 3NF/BCNF from a given schema, with PK and FK identified and the choice justified** — this is 2025's question and it is close to guaranteed. Practise on a bank schema specifically (branch, account, customer, loan, transaction).
- **ER diagram** (8 exams) — draw for a described system. Past papers used a bank, a hospital, a student system and BPL. **Draw one for a banking system before the exam** and memorise the entity set.
- **SQL queries** (9 exams, 12 questions) — GROUP BY with aggregate + HAVING, joins, nested queries, and "one row per department" style output.
- ACID with a failure scenario; transaction states.
- Backup & disaster recovery (6 questions) — full/incremental/differential, RPO/RTO, hot vs cold site. Very bank-relevant, easy marks.
- DELETE vs TRUNCATE vs DROP; view, cursor, trigger; indexing and B+ tree.

**Security — 6.7 %**

- **Draw a secured network topology** — DMZ with Mail/DNS/Web servers, internal LAN, firewall placement, and why each server sits where it does. This is 2025's question and it is the highest-probability diagram on the paper.
- Types of attack (7 exams) — phishing, ransomware, MITM, DoS vs DDoS, SQL injection, XSS, ARP poisoning; and the countermeasure for each.
- **Cryptography** — symmetric vs asymmetric, RSA worked example, Caesar cipher, and **how a digital signature actually works** (hash → encrypt with sender's private key → verify with public key). Be ready to draw that flow.
- CIA triad applied to a banking scenario.
- Firewall types (packet filter / stateful / proxy / NGFW), IDS vs IPS.

**Operating System — 5.0 %**

- **Banker's algorithm** (2025) — build the Need matrix, run the safety sequence, state safe/unsafe. Practise the exact 5-process / 3-resource layout; it appears twice in this bank.
- **CPU scheduling** (6 exams) — FCFS, SJF, priority, round robin; Gantt chart plus average waiting and turnaround time. Always draw the Gantt chart, always show the per-process table.
- Deadlock — four necessary conditions, prevention vs avoidance vs detection.
- Page replacement — FIFO, LRU, Optimal on a given reference string; count page faults; Belady's anomaly.
- Thrashing, virtual memory, paging vs segmentation.
- Semaphore / mutex, producer–consumer.
- Linux commands — file permissions (`chmod`, `chown`), directory listing with hidden files, copy/move, and writing a short shell command. A repeated favourite (3 exams).

### Tier 2 — expect one question across this whole group

- **Algorithm** — min/max **heap construction** (2025) and heap insert cost; **MST via Kruskal** (4 exams, asked repeatedly); Dijkstra; Huffman coding; complexity analysis and recurrence relations; greedy vs DP vs divide-and-conquer distinctions.
- **Microprocessor & Architecture** — **RAID levels** and which suits a core banking DB (5 questions, 4 exams); direct-mapped **cache sizing** (tag/index/offset bits for 16 KB, 4-word blocks, 32-bit address — appears twice); **disk-pack capacity** maths; HDD vs SSD selection for a banking workload; 8086 EU/BIU, addressing modes; pipelining and hazards; RISC vs CISC.
- **C Programming** (12 exams, 14 questions — the most reliable non-network written topic) — write a complete program. Recurring asks: recursion (factorial, Fibonacci), string manipulation, sorting, file handling, and pointer/dynamic-memory use. Write clean, compilable, commented code.
- **Data Structure** — stack applications and infix→postfix conversion; tree traversals and reconstruction; linked-list operations.
- **Software Engineering** — SDLC models and when to use each; **testing types** (unit/integration/system/acceptance, black vs white box); **UML use-case or class diagram from a described scenario** — note that the question usually *describes a system* rather than saying "draw a UML diagram", so recognise it; DFD.
- **DLD** — **K-map simplification** with the grid, loops and final SOP drawn (asked in 2024 and 2025); truth table from a Boolean expression (2025); full adder design; MUX/decoder; 7-segment display as K-map + decoder.
- **Cloud & Virtualization** — IaaS/PaaS/SaaS choice for a described scenario with two real examples; VM vs container; Docker.
- **Computer Fundamentals / Infrastructure** — server hardware, data-centre power and cooling, UPS sizing, disaster-recovery site design.

### Tier 3 — read once, don't drill

AI/ML (agent types, supervised vs unsupervised, ML vs DL), compiler vs interpreter, grammar ambiguity, OOP theory (overloading vs overriding, abstraction, MVC), web technology (HTTP methods, status codes, REST).

---

## 5. Math — 20 marks

Two questions, and unlike the MCQ this includes **calculus**. Historical bank-sector written distribution:

| Topic | Count | Note |
|---|---|---|
| Geometry & coordinate geometry | 5 | triangle/circle area, straight line, distance |
| Arithmetic & algebra | 4 | equations, simplification |
| Percentage, profit & loss, SI/CI | 4 | interest is very bank-typical |
| Ratio, proportion & mixtures | 3 | |
| Set theory & discrete math | 2 | Venn with three sets |
| Speed, time & distance | 2 | boats and streams |
| **Probability & statistics** | 2 | **2025 asked this** |
| **Calculus & integration** | 1 | **2025 asked this** |

Since 2025 used exactly *one integration + one probability*, prepare that pair first:

- Definite integration of polynomials; basic differentiation; area under a curve.
- Probability: conditional probability, total probability, and simple counting-based selection problems (the 2025 bag problem is a total-probability question in disguise).
- Then cover geometry, SI/CI and Venn as backup.

## 6. English — 30 marks

Two questions, both predictable in *form*:

**(a) Focus writing / short note — 100–200 words.** Across 35 past focus-writing prompts in this bank, the theme is consistently **technology × banking × Bangladesh development**. Recent actual prompts:

- "The role of AI and machine language mitigate challenges of cyber attack on banking system" (AD(ICT) 2025)
- "The Importance of Digital Literacy in Expanding Cashless Transactions in Bangladesh" (SO IT 2026)
- "The Role of Sustainable Banking in Achieving the UN SDGs in Bangladesh" (Officer IT 2026)
- "Growing use of technology in the Financial Service Industry"
- "Digital Financial Literacy", "Blockchain technology", "Edge Computing", "Digital Bangladesh"

**Likely 2026 prompts** — prepare a reusable 150-word skeleton for each:

1. AI / GenAI in banking — opportunity and risk
2. Cybersecurity and fraud prevention in digital banking
3. Cashless Bangladesh, **Bangla QR** and interoperable digital payments
4. Fourth Industrial Revolution and the banking workforce
5. CBDC / digital currency, or open banking
6. Financial inclusion through MFS and agent banking
7. Climate finance / green banking and LDC graduation

Build one flexible structure — *definition → current Bangladesh context (name a real initiative) → three benefits → two risks → two recommendations → conclusion* — and you can answer any of them.

**(b) Translation.** Bengali→English appeared in 2025; English→Bengali also recurs (each seen in 15 distinct bank exams — the most repeated written item in the entire bank). Sentences are short and **banking-flavoured**, e.g. *"আপনার ব্যাংক একাউন্ট এর স্থিতি জানার জন্য মোবাইল ব্যাংকিং এপ্লিকেশন এ লগইন করুন"*. Drill banking vocabulary in both directions: account balance, deposit, withdrawal, remittance, interest rate, loan disbursement, branch, transaction, mobile banking application, login.

---

## 7. Diagrams to have ready before you walk in

The written paper rewards diagrams heavily, and drawing under time pressure is a skill. Practise these until each takes under four minutes:

1. **Bank network with firewall + DMZ** (Mail, DNS, Web servers) ← highest probability
2. **ER diagram for a banking system**
3. **E-mail flow** sender → MTA → MTA → receiver, with protocol labels
4. **Gantt chart** for CPU scheduling with the AWT/ATAT table beneath
5. **Min/max heap** as a tree, showing each insertion step
6. **K-map grid** with loops drawn and the SOP written out
7. **Full adder** circuit with truth table
8. **Process state diagram**
9. **Use-case diagram** for a described banking scenario
10. **OSI seven layers** with one protocol per layer

---

## 8. Time strategy for the 2-hour paper

| Phase | Minutes | What |
|---|---|---|
| Read the whole paper, mark the ones you own | 4 | decide your order before writing anything |
| English (short note + translation), 30 marks | 22 | do it early while your hand is fresh and your mind is uncluttered |
| Math, 20 marks | 12 | fast, self-contained, fully scoreable |
| IT — your four strongest, ~80 marks | 45 | diagram first, then explanation |
| IT — remaining three, ~70 marks | 32 | partial credit is real: write the formula and the setup even if you can't finish |
| Review, label diagrams, number answers | 5 | |

Guidance that consistently earns marks on these papers:

- **Draw the diagram first, then write around it.** An unlabelled diagram scores little; a labelled diagram with three lines of explanation scores nearly full.
- **Show the formula before substituting numbers.** In the latency and Shannon questions the formula itself carries marks.
- **Never leave a numeric question blank.** Write the known values, the formula and the approach — partial credit on these is generous.
- **Answer in the banking context when it is offered.** If the schema is a bank schema, name real bank entities. Examiners visibly reward it.

---

## 9. Four-week plan

**Week 1 — the recurring maths**
- Day 1: attempt the AD(ICT) 2025 written paper cold, 2 hours, timed. This tells you where you actually stand.
- Days 2–3: Subnetting and VLSM until fluent; then latency, Nyquist/Shannon, CRC
- Days 4–5: Normalization + ER diagram; draw the banking ER diagram from scratch three times
- Days 6–7: Banker's algorithm, CPU scheduling with Gantt charts, page replacement

**Week 2 — diagrams and security**
- Days 8–9: Firewall/DMZ topology, attack types and countermeasures, digital signature flow
- Days 10–11: RAID, cache sizing, disk-pack maths, HDD vs SSD for banking
- Days 12–13: C programs — recursion, strings, file handling, pointers; write them by hand on paper
- Day 14: BB AP 2023 + BB AME 2023 written sections, timed

**Week 3 — breadth and language**
- Days 15–16: Algorithm (heap, Kruskal, Dijkstra, Huffman, complexity)
- Day 17: DLD (K-map, truth tables, adder, MUX)
- Day 18: SE (SDLC, testing, UML/DFD) + Cloud
- Days 19–20: Math — integration, probability, geometry, SI/CI
- Day 21: English — write three full focus-writing answers under 20-minute timing, plus ten translation sentences

**Week 4 — rehearsal**
- Days 22–23: two full 200-mark mocks under strict 2-hour timing. Score them honestly.
- Day 24: rebuild the diagrams you drew slowly or badly
- Days 25–26: prepare and memorise your seven focus-writing skeletons; drill banking translation vocabulary
- Day 27: one final timed mock, weak areas only
- Day 28: revise formulas, the diagram list, and your error log. Nothing new.

---

### Source and honest limits

Derived from the question bank in this repo — 2,726 written questions across 581 exam tags, filtered to the 477 from bank-sector exams, with the 2025 AD(ICT) paper weighted most heavily.

Two caveats stated plainly:

- Only **11 questions** from the AD(ICT) 2025 written paper are captured here. That is enough to read the paper's *shape* — computation-and-diagram driven, banking-contextualised, roughly 20 marks per IT question — but not enough to predict specific topics with confidence. Treat section 4's tiers, which rest on 477 questions across many exams, as the more reliable guide, and the 2025 paper as the format template.
- The 2026 conducting body is unconfirmed. 2025 was **DU**. If **BUET** conducts it instead, expect heavier calculation and more Linux/architecture content — in that case move cache sizing, pipelining, disk maths and Linux commands up into Tier 1.
