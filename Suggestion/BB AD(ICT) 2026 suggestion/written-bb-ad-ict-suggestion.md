# বাংলাদেশ ব্যাংক — Assistant Director (ICT) ২০২৬ : Written সাজেশন

> তৈরি: **২৮ আগস্ট ২০২৬**, পরীক্ষার প্রায় চার সপ্তাহ আগে।
> এই repo-র পুরো question bank থেকে তৈরি: **২,৭২৬টি written** + **২,৭৮১টি MCQ** প্রশ্ন, ৫৮১টি আলাদা পরীক্ষা থেকে।
> এর মধ্যে **৪৭৭টি written প্রশ্ন এসেছে ব্যাংক খাতের পরীক্ষা থেকে**, আর **১১টি এসেছে গত AD(ICT) paper (০৭.০২.২০২৫, DU পরিচালিত) থেকে**।

---

## ১. পরীক্ষার কাঠামো

| Paper | মার্ক | সময় | বিভাজন |
|---|---|---|---|
| MCQ | ১০০ | সকাল ১০:০০–১১:০০ | IT ৭৫ · Math ১৫ · GK ১০ |
| **Written** | **২০০** | **১১:০০–১:০০ (২ ঘণ্টা)** | **IT ১৫০ · Math ২০ · English ৩০** |

যে তিনটা বিষয় মাথায় রেখে পরিকল্পনা করতে হবে:

১. **MCQ-তে পাশ করলে তবেই written-এর খাতা দেখা হয়।** আগে সেই gate পার হও — সঙ্গের [MCQ সাজেশন](mcq-bb-ad-ict-suggestion.md) দেখো।
২. **১২০ মিনিটে ২০০ মার্ক = প্রতি মার্কে ৩৬ সেকেন্ড।** ২০ মার্কের প্রশ্নে পাবে ১২ মিনিট, diagram-সহ। রচনা লেখার সুযোগ নেই। লিখতে হবে *গোছানো, লেবেলযুক্ত, সম্পূর্ণ* উত্তর — দ্রুত।
৩. **Written + Viva-ই চূড়ান্তভাবে চাকরি ঠিক করে।** তাই এই paper-এ গভীরতা যতটা দরকার, MCQ-তে ততটা নয়।

লক্ষণীয়, written-এর মার্ক বিভাজনে **বাংলা নেই** (IT ১৫০ + Math ২০ + English ৩০ = ২০০)। অন্য কিছু ব্যাংকের paper-এ বাংলা focus writing থাকে; এই পদের written ভাষা-অংশ ইংরেজি। বাংলা তৈরি করো MCQ-র সাধারণ অংশের জন্য, written-এর জন্য নয়।

---

## ২. পদ merge হওয়ার প্রভাব এখানে কী

বাংলাদেশ ব্যাংক আগে আলাদা সার্কুলার দিত **Assistant Programmer** (CSE) আর **Assistant Maintenance Engineer** (EEE / hardware / infrastructure) পদের জন্য। এখন এগুলো merge হয়ে **Assistant Director (ICT)**।

MCQ-তে এর প্রকাশ ঘটে মৌলিক electronics প্রশ্নের ঝাঁক হিসেবে। **Written**-এ প্রকাশটা আলাদা — **infrastructure-ঘেঁষা IT প্রশ্ন** হিসেবে:

- firewall / server-topology **diagram** (২০২৫-এ ঠিক এটাই এসেছে)
- RAID level ও তাদের সুবিধা-অসুবিধা — ব্যাংক খাতের ৫টি written প্রশ্ন, ৪টি আলাদা পরীক্ষায়
- data-centre power, UPS, server hardware — *Server Hardware & Enterprise Systems*-এ ৫টি প্রশ্ন
- ব্যাংকিং workload-এর জন্য HDD বনাম SSD বাছাই, disk-pack ধারণক্ষমতার অঙ্ক
- cache/memory sizing-এর অঙ্ক

তাই written-এর জন্য "merged পদ" মানে "circuit theory শেখো" নয়। এর মানে — **একটা ব্যাংকের IT infrastructure এঁকে দেখাতে ও ব্যাখ্যা করতে পারা।**

---

## ৩. AD(ICT) ২০২৫-এর written paper — তোমার টেমপ্লেট

হাতের কাছে এটাই সবচেয়ে মূল্যবান জিনিস। এগারোটা প্রশ্ন এই repo-তে আছে, tag: `Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)`:

| # | প্রশ্ন | এলাকা | File |
|---|---|---|---|
| ১ | ১২, ২৯, ৩৩, ৫৬, ৬৬, ৯৯, ১০০, ৩৪৪ থেকে **Min Heap গঠন** | Algorithm | [algorithm.md](../../written/algorithm.md) |
| ২ | **Banker's Algorithm** — ৫টি process P₀–P₄, resource A(10) B(5) C(7); Need matrix বের করো; safe না unsafe | OS | [operating-system.md](../../written/operating-system.md) |
| ৩ | ৩-kbyte ই-মেইলের **Total latency**: 1 Gbps, ৩০০ কিমি, আলোর গতি 2×10⁸ m/s, RTT ৫০ ms, queuing ৫ ms | Networks | [computer-networks.md](../../written/computer-networks.md) |
| ৪ | **ই-মেইল স্থানান্তর** — (ক) application ও transport layer-এর protocol (খ) mail transfer-এর ধাপ | Networks | [computer-networks.md](../../written/computer-networks.md) |
| ৫ | **ব্যাংক schema-র normalization** — `Bank(Br_Name, Br_City, Assets, Acc_name, Acc_Num, Balance)`; normalize করো, PK/FK চিহ্নিত করো, schema-র যৌক্তিকতা দাও | Database | [database.md](../../written/database.md) |
| ৬ | **Firewall diagram** — BB-র client–server, সাথে Mail, DNS ও Web server; নিরাপদ topology আঁকো | Security | [computer-network-security.md](../../written/computer-network-security.md) |
| ৭ | `Ā·B̄·(A+B)‾·C`-এর **Truth table** | DLD | [dld.md](../../written/dld.md) |
| ৮ | **∫₀² (2x² + 3x) dx** | Math | [math.md](../../written/math.md) |
| ৯ | **Probability** — ৬ জন AD (সবাই ব্যাগ আনে), ৪ জন DD (অর্ধেক ব্যাগ আনে); এলোমেলোভাবে একটা ব্যাগ নিলে সেটা DD-র হওয়ার সম্ভাবনা? | Math | [math.md](../../written/math.md) |
| ১০ | **সংক্ষিপ্ত রচনা (১০০–১৫০ শব্দ)** — "The role of AI and machine language to mitigate challenges of cyber attack on banking system" | English | [english.md](../../written/english.md) |
| ১১ | **বাংলা → ইংরেজি অনুবাদ** — ব্যাংকিং বিষয়ক দুইটি বাক্য | English | [english.md](../../written/english.md) |

এই তালিকা থেকে যে ধরনটা পড়ে নাও, সেটা বারবার ফিরে আসে:

- **সাতটা IT প্রশ্ন ≈ ১৫০ মার্ক**, অর্থাৎ প্রতিটা প্রায় **২০ মার্ক**, প্রায় **১২ মিনিট**।
- প্রতিটা IT প্রশ্নই হয় **হিসাব**, নয়তো **diagram**। একটাও "X নিয়ে রচনা লেখো" নয়।
- **ব্যাংকিং প্রেক্ষাপট ইচ্ছাকৃতভাবে মেশানো** — schema একটা ব্যাংকের, firewall বাংলাদেশ ব্যাংকের, probability-র প্রশ্ন AD আর DD নিয়ে। এবারও এটাই আশা করো।
- Math **২টা প্রশ্ন / ২০ মার্ক**, আর MCQ-র বিপরীতে এখানে calculus *থাকে*।
- English **২টা প্রশ্ন / ৩০ মার্ক** — একটা সংক্ষিপ্ত রচনা, একটা অনুবাদ।

পুরো paper বের করার কমান্ড:

```
grep -rn "Assistant Director (ICT) Exam: 07.02.2025" written/
```

---

## ৪. IT-১৫০ — বিষয় অগ্রাধিকার

ক্রম নির্ধারিত হয়েছে **কয়টা আলাদা ব্যাংক পরীক্ষা** কোন এলাকা থেকে প্রশ্ন করেছে তার ভিত্তিতে (নির্ভরযোগ্যতার মাপকাঠি), সাথে ২০২৫-এর paper মিলিয়ে দেখা হয়েছে।

### Tier 1 — প্রতিটা থেকে একটা করে প্রশ্ন আশা করো

**Computer Networks — ব্যাংক খাতের সব written প্রশ্নের ১৬.৪ %, একক বৃহত্তম এলাকা**

- **Subnetting ও VLSM** (১০টি আলাদা পরীক্ষা, ১২টি প্রশ্ন)। `192.168.10.0/24` → ৪টি সমান subnet-এ ভাগ করো; কয় bit ধার নিতে হবে, নতুন mask, প্রতিটি subnet-এর network/first-usable/broadcast। আরও: `172.16.0.0/19` → কয়টা subnet ও host। ৬ মিনিটে পুরো VLSM টেবিল করতে পারা পর্যন্ত অনুশীলন করো।
- **Latency / throughput-এর অঙ্ক** — total latency = propagation + transmission + queuing + RTT। ২০২৫-এর প্রশ্নটাই আদর্শ রূপ; unit রূপান্তরে (কিমি ÷ m/s, kbyte → bit, Gbps) সাবলীল হও।
- **Channel capacity** — Nyquist `C = 2B log₂L` ও Shannon `C = B log₂(1+SNR)`; SNR dB না অনুপাত সেটা খেয়াল রাখো। বারবার আসা রূপ: টেলিফোন লাইন ৩০০০ Hz, SNR ৩১৬২।
- **Multiplexing** (৭টি পরীক্ষা) — TDM বনাম FDM বনাম WDM, pulse-stuffing TDM, frame rate ও bit-rate-এর হিসাব।
- **CRC** — মূল ডেটা 11100, divisor 1001 → transmitted frame বের করো এবং receiver-এ যাচাই করো।
- **OSI / TCP-IP** (৬টি পরীক্ষা) — layer-এর কাজ, প্রতি layer-এর protocol, এবং পার্থক্যের টেবিল।
- **ই-মেইল architecture** — SMTP বনাম POP3 বনাম IMAP, MTA/MUA, এবং শুরু থেকে শেষ পর্যন্ত ধাপের ক্রম (২০২৫)।
- **PCM** — sampling rate, quantization level, bit rate।
- Routing protocol, transmission media, flow control (stop-and-wait, Go-Back-N) দক্ষতার হিসাবসহ।

**Database — ১০.৯ %**

- **দেওয়া schema থেকে 3NF/BCNF পর্যন্ত normalization, PK ও FK চিহ্নিত করে এবং সিদ্ধান্তের যুক্তি দিয়ে** — এটাই ২০২৫-এর প্রশ্ন এবং আসা প্রায় নিশ্চিত। বিশেষ করে ব্যাংক schema (branch, account, customer, loan, transaction) নিয়ে অনুশীলন করো।
- **ER diagram** (৮টি পরীক্ষা) — বর্ণিত সিস্টেমের জন্য আঁকো। আগের paper-এ এসেছে ব্যাংক, হাসপাতাল, student system ও BPL। **পরীক্ষার আগে ব্যাংকিং সিস্টেমের একটা ER diagram এঁকে entity set মুখস্থ করে যাও।**
- **SQL query** (৯টি পরীক্ষা, ১২টি প্রশ্ন) — aggregate সহ GROUP BY ও HAVING, join, nested query, এবং "প্রতি department-এ এক সারি" ধরনের output।
- ACID, failure scenario সহ; transaction state।
- Backup ও disaster recovery (৬টি প্রশ্ন) — full/incremental/differential, RPO/RTO, hot বনাম cold site। ব্যাংকের জন্য খুবই প্রাসঙ্গিক, সহজ মার্ক।
- DELETE বনাম TRUNCATE বনাম DROP; view, cursor, trigger; indexing ও B+ tree।

**Security — ৬.৭ %**

- **নিরাপদ network topology আঁকো** — DMZ-তে Mail/DNS/Web server, ভেতরের LAN, firewall কোথায় বসবে, এবং কোন server কেন কোথায়। এটাই ২০২৫-এর প্রশ্ন এবং paper-এর সবচেয়ে সম্ভাব্য diagram।
- আক্রমণের ধরন (৭টি পরীক্ষা) — phishing, ransomware, MITM, DoS বনাম DDoS, SQL injection, XSS, ARP poisoning; এবং প্রতিটার প্রতিকার।
- **Cryptography** — symmetric বনাম asymmetric, RSA-র উদাহরণসহ সমাধান, Caesar cipher, এবং **digital signature আসলে কীভাবে কাজ করে** (hash → প্রেরকের private key দিয়ে encrypt → public key দিয়ে verify)। এই প্রবাহটা আঁকতে পারতে হবে।
- ব্যাংকিং scenario-তে প্রয়োগ করা CIA triad।
- Firewall-এর ধরন (packet filter / stateful / proxy / NGFW), IDS বনাম IPS।

**Operating System — ৫.০ %**

- **Banker's algorithm** (২০২৫) — Need matrix তৈরি, safety sequence বের করা, safe/unsafe বলা। ঠিক ৫-process / ৩-resource বিন্যাসটা অনুশীলন করো; এই bank-এ এটা দুইবার আছে।
- **CPU scheduling** (৬টি পরীক্ষা) — FCFS, SJF, priority, round robin; Gantt chart সহ average waiting ও turnaround time। সবসময় Gantt chart আঁকো, সবসময় process-ভিত্তিক টেবিল দাও।
- Deadlock — চারটি প্রয়োজনীয় শর্ত, prevention বনাম avoidance বনাম detection।
- Page replacement — দেওয়া reference string-এ FIFO, LRU, Optimal; page fault গোনা; Belady's anomaly।
- Thrashing, virtual memory, paging বনাম segmentation।
- Semaphore / mutex, producer–consumer।
- Linux command — file permission (`chmod`, `chown`), লুকানো ফাইলসহ directory listing, copy/move, এবং ছোট shell command লেখা। বারবার আসা প্রিয় বিষয় (৩টি পরীক্ষা)।

### Tier 2 — এই পুরো দল থেকে একটা প্রশ্ন আশা করো

- **Algorithm** — min/max **heap গঠন** (২০২৫) ও heap insert-এর খরচ; **Kruskal দিয়ে MST** (৪টি পরীক্ষা, বারবার এসেছে); Dijkstra; Huffman coding; complexity বিশ্লেষণ ও recurrence relation; greedy বনাম DP বনাম divide-and-conquer-এর পার্থক্য।
- **Microprocessor ও Architecture** — **RAID level** এবং core banking DB-র জন্য কোনটা উপযুক্ত (৫টি প্রশ্ন, ৪টি পরীক্ষা); direct-mapped **cache sizing** (১৬ KB, ৪-word block, ৩২-bit address-এ tag/index/offset bit — দুইবার এসেছে); **disk-pack ধারণক্ষমতা**-র অঙ্ক; ব্যাংকিং workload-এ HDD বনাম SSD; 8086-এর EU/BIU, addressing mode; pipelining ও hazard; RISC বনাম CISC।
- **C Programming** (১২টি পরীক্ষা, ১৪টি প্রশ্ন — network-এর পরে সবচেয়ে নির্ভরযোগ্য written বিষয়) — সম্পূর্ণ program লিখতে বলা হয়। বারবার আসে: recursion (factorial, Fibonacci), string manipulation, sorting, file handling, এবং pointer/dynamic memory। পরিচ্ছন্ন, compile-যোগ্য, comment করা কোড লেখো।
- **Data Structure** — stack-এর প্রয়োগ ও infix→postfix রূপান্তর; tree traversal ও পুনর্গঠন; linked list-এর operation।
- **Software Engineering** — SDLC model ও কখন কোনটা; **testing-এর ধরন** (unit/integration/system/acceptance, black বনাম white box); **বর্ণিত scenario থেকে UML use-case বা class diagram** — মনে রাখো, প্রশ্নে সাধারণত *সিস্টেমের বর্ণনা* দেওয়া থাকে, সরাসরি "UML diagram আঁকো" বলা থাকে না, তাই চিনতে পারা জরুরি; DFD।
- **DLD** — **K-map simplification**, grid, loop ও চূড়ান্ত SOP এঁকে (২০২৪ ও ২০২৫ দুইবারই এসেছে); Boolean expression থেকে truth table (২০২৫); full adder ডিজাইন; MUX/decoder; ৭-segment display = K-map + decoder।
- **Cloud ও Virtualization** — বর্ণিত scenario-তে IaaS/PaaS/SaaS বাছাই, দুইটা বাস্তব উদাহরণসহ; VM বনাম container; Docker।
- **Computer Fundamentals / Infrastructure** — server hardware, data-centre power ও cooling, UPS sizing, disaster recovery site ডিজাইন।

### Tier 3 — একবার পড়ো, অনুশীলনে সময় দিও না

AI/ML (agent-এর ধরন, supervised বনাম unsupervised, ML বনাম DL), compiler বনাম interpreter, grammar ambiguity, OOP তত্ত্ব (overloading বনাম overriding, abstraction, MVC), web technology (HTTP method, status code, REST)।

---

## ৫. Math — ২০ মার্ক

দুইটা প্রশ্ন, এবং MCQ-র বিপরীতে এখানে **calculus** থাকে। ঐতিহাসিক ব্যাংক-খাত বণ্টন:

| বিষয় | সংখ্যা | মন্তব্য |
|---|---|---|
| Geometry ও coordinate geometry | ৫ | ত্রিভুজ/বৃত্তের ক্ষেত্রফল, সরলরেখা, দূরত্ব |
| Arithmetic ও algebra | ৪ | সমীকরণ, সরলীকরণ |
| Percentage, লাভ-ক্ষতি, সরল/চক্রবৃদ্ধি সুদ | ৪ | সুদ ব্যাংকের জন্য খুবই স্বাভাবিক |
| অনুপাত, সমানুপাত ও মিশ্রণ | ৩ | |
| Set theory ও discrete math | ২ | তিন সেটের Venn |
| গতি, সময় ও দূরত্ব | ২ | নৌকা ও স্রোত |
| **Probability ও statistics** | ২ | **২০২৫-এ এসেছে** |
| **Calculus ও integration** | ১ | **২০২৫-এ এসেছে** |

যেহেতু ২০২৫-এ ঠিক *একটা integration + একটা probability* এসেছিল, ওই জোড়াটা আগে তৈরি করো:

- বহুপদীর নির্দিষ্ট যোগজীকরণ; মৌলিক অন্তরীকরণ; বক্ররেখার নিচের ক্ষেত্রফল।
- Probability: শর্তাধীন সম্ভাবনা, মোট সম্ভাবনা, এবং গণনাভিত্তিক নির্বাচনের সমস্যা (২০২৫-এর ব্যাগের প্রশ্নটা আসলে ছদ্মবেশে total probability-র প্রশ্ন)।
- তারপর backup হিসেবে geometry, সরল/চক্রবৃদ্ধি সুদ এবং Venn।

## ৬. English — ৩০ মার্ক

দুইটা প্রশ্ন, দুইটারই *গঠন* অনুমানযোগ্য:

**(ক) Focus writing / সংক্ষিপ্ত রচনা — ১০০–২০০ শব্দ।** এই bank-এর ৩৫টি পুরনো focus-writing প্রশ্নে বিষয়বস্তু ধারাবাহিকভাবে **প্রযুক্তি × ব্যাংকিং × বাংলাদেশের উন্নয়ন**। সাম্প্রতিক প্রকৃত প্রশ্ন:

- "The role of AI and machine language mitigate challenges of cyber attack on banking system" (AD(ICT) ২০২৫)
- "The Importance of Digital Literacy in Expanding Cashless Transactions in Bangladesh" (SO IT ২০২৬)
- "The Role of Sustainable Banking in Achieving the UN SDGs in Bangladesh" (Officer IT ২০২৬)
- "Growing use of technology in the Financial Service Industry"
- "Digital Financial Literacy", "Blockchain technology", "Edge Computing", "Digital Bangladesh"

**২০২৬-এর জন্য সম্ভাব্য বিষয়** — প্রতিটার জন্য ১৫০ শব্দের একটা পুনর্ব্যবহারযোগ্য কাঠামো তৈরি রাখো:

১. ব্যাংকিংয়ে AI / GenAI — সম্ভাবনা ও ঝুঁকি
২. ডিজিটাল ব্যাংকিংয়ে সাইবার নিরাপত্তা ও জালিয়াতি প্রতিরোধ
৩. ক্যাশলেস বাংলাদেশ, **বাংলা QR** ও আন্তঃপরিচালনযোগ্য ডিজিটাল পেমেন্ট
৪. চতুর্থ শিল্পবিপ্লব ও ব্যাংকিং জনশক্তি
৫. CBDC / ডিজিটাল মুদ্রা, অথবা open banking
৬. MFS ও এজেন্ট ব্যাংকিংয়ের মাধ্যমে আর্থিক অন্তর্ভুক্তি
৭. জলবায়ু অর্থায়ন / সবুজ ব্যাংকিং এবং LDC উত্তরণ

একটাই নমনীয় কাঠামো বানাও — *সংজ্ঞা → বাংলাদেশের বর্তমান প্রেক্ষাপট (একটা বাস্তব উদ্যোগের নাম) → তিনটা সুবিধা → দুইটা ঝুঁকি → দুইটা সুপারিশ → উপসংহার* — এতেই যেকোনোটার উত্তর দেওয়া যাবে।

**(খ) অনুবাদ।** ২০২৫-এ বাংলা→ইংরেজি এসেছে; ইংরেজি→বাংলাও ঘুরেফিরে আসে (প্রতিটা ১৫টি আলাদা ব্যাংক পরীক্ষায় দেখা গেছে — পুরো bank-এর সবচেয়ে বেশিবার আসা written আইটেম)। বাক্য ছোট এবং **ব্যাংকিং ঘেঁষা**, যেমন *"আপনার ব্যাংক একাউন্ট এর স্থিতি জানার জন্য মোবাইল ব্যাংকিং এপ্লিকেশন এ লগইন করুন"*। দুই দিকেই ব্যাংকিং শব্দভাণ্ডার অনুশীলন করো: account balance, deposit, withdrawal, remittance, interest rate, loan disbursement, branch, transaction, mobile banking application, login।

---

## ৭. হলে ঢোকার আগে যে diagram গুলো তৈরি রাখবে

Written paper-এ diagram-এ ভালো মার্ক আসে, আর সময়ের চাপে আঁকাটা আলাদা দক্ষতা। প্রতিটা চার মিনিটের নিচে নামা পর্যন্ত অনুশীলন করো:

১. **Firewall + DMZ সহ ব্যাংক network** (Mail, DNS, Web server) ← সবচেয়ে সম্ভাব্য
২. **ব্যাংকিং সিস্টেমের ER diagram**
৩. **ই-মেইল প্রবাহ** প্রেরক → MTA → MTA → প্রাপক, protocol লেবেলসহ
৪. **CPU scheduling-এর Gantt chart**, নিচে AWT/ATAT টেবিলসহ
৫. **Min/max heap** গাছ হিসেবে, প্রতিটা insertion ধাপ দেখিয়ে
৬. **K-map grid**, loop আঁকা ও SOP লেখা
৭. **Full adder** circuit, truth table সহ
৮. **Process state diagram**
৯. বর্ণিত ব্যাংকিং scenario-র **Use-case diagram**
১০. **OSI-র সাতটি layer**, প্রতি layer-এ একটা করে protocol

---

## ৮. ২ ঘণ্টার paper-এর সময় কৌশল

| ধাপ | মিনিট | কী করবে |
|---|---|---|
| পুরো paper পড়ে যেগুলো ভালো পারো চিহ্নিত করা | ৪ | লেখা শুরুর আগেই ক্রম ঠিক করো |
| English (সংক্ষিপ্ত রচনা + অনুবাদ), ৩০ মার্ক | ২২ | হাত সতেজ ও মাথা পরিষ্কার থাকতে শুরুতেই সেরে ফেলো |
| Math, ২০ মার্ক | ১২ | দ্রুত, স্বয়ংসম্পূর্ণ, পুরো নম্বর তোলা সম্ভব |
| IT — তোমার সবচেয়ে শক্তিশালী চারটা, ~৮০ মার্ক | ৪৫ | আগে diagram, তারপর ব্যাখ্যা |
| IT — বাকি তিনটা, ~৭০ মার্ক | ৩২ | আংশিক নম্বর বাস্তব: শেষ করতে না পারলেও সূত্র ও setup লিখে দাও |
| রিভিউ, diagram-এ লেবেল, উত্তরের নম্বর মেলানো | ৫ | |

এই ধরনের paper-এ যা ধারাবাহিকভাবে নম্বর এনে দেয়:

- **আগে diagram আঁকো, তারপর তার চারপাশে লেখো।** লেবেলহীন diagram-এ নম্বর কম; লেবেলযুক্ত diagram-এর সাথে তিন লাইন ব্যাখ্যা থাকলে প্রায় পুরো নম্বর।
- **সংখ্যা বসানোর আগে সূত্র লেখো।** latency ও Shannon-এর প্রশ্নে সূত্রটাই আলাদা নম্বর বহন করে।
- **কোনো সংখ্যাভিত্তিক প্রশ্ন খালি রেখো না।** জানা মান, সূত্র ও পদ্ধতি লিখে দাও — এগুলোতে আংশিক নম্বর উদার হাতে দেওয়া হয়।
- **সুযোগ থাকলে ব্যাংকিং প্রেক্ষাপটেই উত্তর দাও।** schema যদি ব্যাংকের হয়, বাস্তব ব্যাংকিং entity-র নাম ব্যবহার করো। পরীক্ষক এটা স্পষ্টভাবে পছন্দ করেন।

---

## ৯. চার সপ্তাহের পরিকল্পনা

**সপ্তাহ ১ — বারবার আসা অঙ্ক**
- দিন ১: AD(ICT) ২০২৫-এর written paper কোনো প্রস্তুতি ছাড়াই, ২ ঘণ্টা সময় ধরে দাও। এতেই বুঝবে আসলে কোথায় দাঁড়িয়ে আছো।
- দিন ২–৩: Subnetting ও VLSM সাবলীল হওয়া পর্যন্ত; তারপর latency, Nyquist/Shannon, CRC
- দিন ৪–৫: Normalization + ER diagram; ব্যাংকিং ER diagram শূন্য থেকে তিনবার আঁকো
- দিন ৬–৭: Banker's algorithm, Gantt chart সহ CPU scheduling, page replacement

**সপ্তাহ ২ — diagram ও নিরাপত্তা**
- দিন ৮–৯: Firewall/DMZ topology, আক্রমণের ধরন ও প্রতিকার, digital signature-এর প্রবাহ
- দিন ১০–১১: RAID, cache sizing, disk-pack-এর অঙ্ক, ব্যাংকিংয়ে HDD বনাম SSD
- দিন ১২–১৩: C program — recursion, string, file handling, pointer; কাগজে হাতে লিখে অনুশীলন করো
- দিন ১৪: BB AP ২০২৩ + BB AME ২০২৩-এর written অংশ, সময় ধরে

**সপ্তাহ ৩ — বিস্তার ও ভাষা**
- দিন ১৫–১৬: Algorithm (heap, Kruskal, Dijkstra, Huffman, complexity)
- দিন ১৭: DLD (K-map, truth table, adder, MUX)
- দিন ১৮: SE (SDLC, testing, UML/DFD) + Cloud
- দিন ১৯–২০: Math — integration, probability, geometry, সরল/চক্রবৃদ্ধি সুদ
- দিন ২১: English — ২০ মিনিট সময় ধরে তিনটা পূর্ণ focus writing, সাথে দশটা অনুবাদ বাক্য

**সপ্তাহ ৪ — মহড়া**
- দিন ২২–২৩: কড়া ২ ঘণ্টা সময়ে দুইটা পূর্ণ ২০০ মার্কের mock। সৎভাবে নম্বর দাও।
- দিন ২৪: যে diagram গুলো ধীরে বা খারাপ এঁকেছো, সেগুলো আবার তৈরি করো
- দিন ২৫–২৬: সাতটা focus-writing কাঠামো তৈরি ও মুখস্থ করো; ব্যাংকিং অনুবাদের শব্দভাণ্ডার ঝালাই
- দিন ২৭: শুধু দুর্বল জায়গা নিয়ে শেষ একটা সময়বদ্ধ mock
- দিন ২৮: সূত্র, diagram-এর তালিকা ও নিজের ভুলের খাতা রিভিশন। নতুন কিছু নয়।

---

### উৎস ও সীমাবদ্ধতা

এই repo-র question bank থেকে বের করা — ৫৮১টি exam tag জুড়ে ২,৭২৬টি written প্রশ্ন, যার মধ্যে ব্যাংক খাতের ৪৭৭টি আলাদা করা হয়েছে, এবং ২০২৫-এর AD(ICT) paper-কে সবচেয়ে বেশি গুরুত্ব দেওয়া হয়েছে।

দুইটা কথা পরিষ্কার করে বলা দরকার:

- AD(ICT) ২০২৫-এর written paper-এর মাত্র **১১টা প্রশ্ন** এখানে আছে। paper-এর *ধরন* বোঝার জন্য এটুকুই যথেষ্ট — হিসাব ও diagram-নির্ভর, ব্যাংকিং প্রেক্ষাপটে বসানো, প্রতি IT প্রশ্নে প্রায় ২০ মার্ক — কিন্তু নির্দিষ্ট topic আত্মবিশ্বাসের সাথে অনুমান করার জন্য যথেষ্ট নয়। তাই ৪ নম্বর অনুচ্ছেদের স্তরগুলো (যেগুলো অনেক পরীক্ষার ৪৭৭টি প্রশ্নের উপর দাঁড়ানো) বেশি নির্ভরযোগ্য নির্দেশনা হিসেবে ধরো, আর ২০২৫-এর paper-কে ধরো format-এর টেমপ্লেট হিসেবে।
- ২০২৬-এ কে পরীক্ষা নেবে তা নিশ্চিত নয়। ২০২৫-এ ছিল **DU**। যদি **BUET** নেয়, তাহলে হিসাব ও Linux/architecture-এর অংশ বাড়বে — সেক্ষেত্রে cache sizing, pipelining, disk-এর অঙ্ক ও Linux command Tier 1-এ তুলে আনো।
