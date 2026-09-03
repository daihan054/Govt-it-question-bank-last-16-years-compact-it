# বাংলাদেশ ব্যাংক সহকারী পরিচালক (ICT) ২০২৬ — লিখিত সাজেশন

> এই সাজেশন **শুধুমাত্র** [`all-questions/`](../../all-questions/) ফোল্ডারের ঐতিহাসিক প্রশ্নভাণ্ডার থেকে তৈরি।
> নিচের প্রতিটি "কোথায় এসেছে" লাইন ঐ ফাইলগুলোর ভেতরে থাকা আসল exam tag থেকে হুবহু নেওয়া।
> প্র্যাকটিসের জন্য বানানো নতুন প্রশ্নগুলো আলাদাভাবে **🔮 সম্ভাব্য (Predicted)** লেখা আছে।
>
> **একটি নোট:** ঐতিহাসিক প্রশ্নগুলো যে ভাষায় প্রশ্নপত্রে ছিল, সেই ভাষাতেই হুবহু উদ্ধৃত করা হয়েছে — কারণ ঐতিহাসিক প্রশ্নের শব্দ বদলানো যাবে না। বিশ্লেষণ, ব্যাখ্যা ও পরামর্শ সব বাংলায়।

---

## বিশ্লেষণের সারসংক্ষেপ

### কী কী প্রসেস করা হয়েছে

| বিষয় | পরিমাণ |
|---|---|
| সোর্স ফোল্ডার | `all-questions/` |
| মোট `.md` ফাইল পাওয়া গেছে | **৫০টি** — `written/`-এ ২৪টি টপিক ফাইল + `written/suggestion/written-question-count.md`, `mcq/`-এ ২৪টি টপিক ফাইল + `mcq/suggestion/mcq-question-count.md` |
| সম্পূর্ণ পড়া হয়েছে | **৫০ / ৫০** (কোনো ফাইল বাদ দেওয়া হয়নি, স্যাম্পলিং করা হয়নি) |
| মোট প্রশ্ন এক্সট্র্যাক্ট হয়েছে | **৫,৯১০** |
| Written অংশ (`all-questions/written/`) | **৩,১৬৮** প্রশ্ন — IT ২,৬২৩ · General ৫৪৫ |
| MCQ অংশ (`all-questions/mcq/`) | **২,৭৪২** প্রশ্ন |
| ট্যাগ থেকে পাওয়া আলাদা পরীক্ষার সংখ্যা | **৩৫০** |
| ট্যাগে থাকা সালের পরিসর | **২০১১ – ২০২৬** |

এই ফাইলটা **শুধু লিখিত পরীক্ষার জন্য**, তাই এটা `all-questions/written/` দিয়ে চালিত। MCQ পরীক্ষার সাজেশন আছে [`mcq-bb-ad-ict-suggestion.md`](mcq-bb-ad-ict-suggestion.md) ফাইলে।

### বাংলাদেশ ব্যাংকের লিখিত পদচিহ্ন

বাংলাদেশ ব্যাংক আগে **সহকারী প্রোগ্রামার (AP)** আর **সহকারী মেইনটেন্যান্স ইঞ্জিনিয়ার (AME)** — এই দুই পদে আলাদা সার্কুলার দিত; এখন এই দুইটা মিলিয়ে হয়েছে **সহকারী পরিচালক (ICT)**। ডেটাসেটে **১৫টি পরীক্ষার মোট ৩৫৯টি বাংলাদেশ ব্যাংক প্রশ্ন রেকর্ড** আছে — তার মধ্যে **১৩৪টি লিখিত অংশে, ১১টি আলাদা পরীক্ষায় ছড়ানো**:

| বাংলাদেশ ব্যাংক পরীক্ষা (লিখিত অবদান) | লিখিত রেকর্ড | ET |
|---|---|---|
| Senior Officer (IT), Grade-9 (Job ID-25104) 2024 | ২৪ | N/A |
| Recruitment Test 2020 | ১৯ | N/A |
| Assistant Programmer 03.02.2023 | ১৭ | BIBM |
| Assistant Maintenance Engineer 04.02.2023 | ১৪ | BIBM |
| **Assistant Director (ICT) 07.02.2025** | **১১** | **DU** |
| Assistant Programmer 2016 | ৯ | N/A |
| Assistant Programmer 2019 | ৯ | DU |
| Assistant Maintenance Engineer 2019 | ৯ | BUET |
| Assistant Maintenance Engineer 2011 | ৮ | N/A |
| Assistant Maintenance Engineer 2017 | ৮ | N/A |
| Assistant Maintenance Engineer 2016 | ৬ | N/A |

*(১১টি পরীক্ষা · ১৩৪টি লিখিত রেকর্ড · `all-questions/written/`-এর ভেতরের exam tag গুনে যাচাই করা।)*

### যে পাঁচটি আবিষ্কার এই সাজেশনটা গড়ে দিয়েছে

**১। AD(ICT) 07.02.2025-এর ১১টা লিখিত প্রশ্নের সবগুলোই উদ্ধার করা গেছে, আর সবই পাঠ্যবইয়ের মানসম্পন্ন সমস্যা।** ডেটাসেটে মার্জ হওয়া পদের এটাই একমাত্র পরীক্ষা। হুবহু:

| # | প্রশ্ন | ফাইল / সাবটপিক |
|---|---|---|
| ১ | **Banker's Algorithm:** 5 processes P₀–P₄; 3 resource types A (10), B (5), C (7). (a) Need matrix (b) Safe state or Unsafe | `operating-system.md` → Deadlock & Resource Allocation |
| ২ | **Construction of Min Heap:** Given Value 12, 29, 33, 56, 66, 99, 100, and 344 | `algorithm.md` → Heap & Priority Queue |
| ৩ | **A Bank schema is given below: Bank(Br_Name, Br_City, Assets, Acc_name, Acc_Num, Balance).** (a) Normalize and point out Primary and Foreign Key (b) Show the schema and state why your schema is in good form | `database.md` → Normalization & Database Design |
| ৪ | **Bangladesh Bank have client server and the communication with Mail Server, DNS server, Web server. Bangladesh Bank want to ensure the security using firewall on those server. Draw a diagram with the scenario.** | `computer-network-security.md` → Firewalls & Network Defense |
| ৫ | **Sinthia wants to send an email to her friend (Afsana).** (a) Mention the protocol of application layer and transport layer (b) Write down the steps of Mail transfer from Afsana to Sinthia | `computer-networks.md` → Email Architecture & Protocols |
| ৬ | **What is Total Latency for a 3-kbyte message (an e-mail) if the bandwidth of the network is 1 Gbps?** Distance 300 km, light travels at 2×10⁸ m/s, RTT 50 ms, Queuing Time 5 ms | `computer-networks.md` → Error Detection & Data Communication |
| ৭ | **Ā·B̄·(A+B)‾·C ; Write Truth Table.** | `dld.md` → Logic Gates & Universal Gates |
| ৮ | **∫₀² (2x² + 3x) dx** | `math.md` → Calculus & Integration |
| ৯ | **In Bangladesh Bank, there are 6 Assistant Directors (ADs) and 4 Deputy Directors (DDs). Each AD brings a bag, while only half of the DDs bring a bag. If a bag is selected at random from all the bags, what is the probability that the chosen bag belongs to a Deputy Director (DD)?** | `math.md` → Probability & Statistics |
| ১০ | **Write short note on: "The role of AI and machine language mitigate challenges of cyber attack on banking system" (100–150 words)** | `english.md` → Focus Writing |
| ১১ | **Bengali to English:** (a) শনিবার হতে সে অফিসে আসছে না। (b) আপনার ব্যাংক একাউন্ট এর স্থিতি জানার জন্য মোবাইল ব্যাংকিং এপ্লিকেশন এ লগইন করুন | `english.md` → Translation |

এখানে দুটো কাঠামোগত বিষয় স্পষ্ট: **প্রতিটা IT প্রশ্নই একটা প্রমিত পাঠ্যবইয়ের সমস্যা, শুধু ব্যাংকিং মোড়কে বসানো** (Silberschatz-এর Banker's Algorithm; Silberschatz-এর `Bank(branch_name, branch_city, assets, customer_name, account_number, balance)` normalization অনুশীলন; Forouzan-এর total-latency সূত্র), আর **ব্যাংকের নিজের নামটাই প্রশ্নের ভেতরে লিখে দেওয়া হয়েছে** — firewall diagram, probability সমস্যা আর focus-writing টপিক তিনটাই বাংলাদেশ ব্যাংকের দৃশ্যপট।

**২। বাংলাদেশ ব্যাংকের একটা লিখিত প্রশ্নপত্র ইতোমধ্যেই প্রায় পুরোটা পুনর্ব্যবহার হয়ে গেছে।** `SO IT 25-07-2026` ট্যাগের ২২টা প্রশ্নের মধ্যে **২০টাই `Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024`-এর হুবহু পুনরাবৃত্তি** — এর মধ্যে আছে K-map simplification, subnetting, SQL aggregation, Java recursion tracing, cache miss-এর ধরন, pipelining, circular queue, hashing vs encryption, unit vs integration testing, HTTP status code, multiplexing guard-band, tree-এর পরিভাষা, PaaS বাছাই, grammar ambiguity, দশ লক্ষ সংখ্যায় binary search, আর পাঁচটা GK one-liner। ২০২৬ প্রশ্নপত্রে মাত্র দুইটা আইটেম নতুন (একটা e-commerce class diagram আর একটা AI-in-banking রচনা)। এটাই ডেটাসেটের সবচেয়ে বড় প্রমাণ যে **বাংলাদেশ ব্যাংকের লিখিত প্রশ্ন পুনর্ব্যবহার হয়**, আর এ কারণেই AD(ICT) ২০২৫-এর পরেই দ্বিতীয় সবচেয়ে মূল্যবান ডকুমেন্ট হলো BB SO(IT) ২০২৪-এর প্রশ্নপত্র।

**৩। পুরো ভাণ্ডারে সবচেয়ে ঘন টপিক হলো subnetting।** `written/computer-networks.md` → *Subnetting & IP Addressing*-এ **১০৯টি প্রশ্ন** — ৫,৯১০ রেকর্ডের মধ্যে অন্য যেকোনো সাবটপিকের চেয়ে বেশি। একটা প্রশ্ন — *"Given IP address 192.168.1.50, Subnet Mask: 255.255.255.240. Find the valid IP range, Network address and Broadcast address"* — একাই **চারটা** আলাদা exam tag বহন করছে।

**৪। লিখিত প্রশ্নপত্রের অর্ধেকটাই গণিত।** শুধু AD(ICT) ২০২৫-এই: Banker's Algorithm (matrix-এর কাজ), min-heap নির্মাণ, total-latency হিসাব, একটা definite integral আর একটা probability সমস্যা — ১১টার মধ্যে ৫টাই ক্যালকুলেশন। বৃহত্তর ভাণ্ডারেও একই চিত্র: `written/computer-networks.md`-এ ১৬টা Nyquist/Shannon প্রশ্ন, ১৮টা multiplexing প্রশ্ন আর ১৩টা optical-fibre power-budget প্রশ্ন; `written/operating-system.md`-এ ২৫টা CPU-scheduling প্রশ্ন।

**৫। যে মার্ক ডিস্ট্রিবিউশন ধরে এগোনো হচ্ছে।** লিখিত পরীক্ষা **২ ঘণ্টায় ২০০ নম্বর**, ভাগ **IT ১৫০ · Math ২০ · English ৩০**। MCQ পাশ না করলে লিখিত খাতাই দেখা হয় না, আর চূড়ান্ত নির্বাচনে লিখিত + ভাইভার নম্বরই কাজে লাগে। তাই MCQ-র তুলনায় এখানে গভীরতা অনেক বেশি জরুরি।

---

## 🔥 Tier 1 — অবশ্যই পড়তে হবে

প্রতিটাই হয় AD(ICT) ২০২৫-এর হুবহু লিখিত প্রশ্ন, নাহয় একাধিক বাংলাদেশ ব্যাংক পরীক্ষায় ফিরে আসা প্রশ্ন।

---

### T1.1 — Banker's Algorithm: Need matrix আর safe sequence

**প্রশ্ন (ঐতিহাসিক, হুবহু):**
> **Banker's Algorithm: 5 processes P₀ through P₄; 3 resource types A (10 instances), B (5 instances), and C (7 instances).**
> (a) Need matrix (b) Safe state or Unsafe
> Snapshot at time T₀. The content of the matrix. Need is defined to be Max – Allocation.

* **প্রাধান্য:** সর্বোচ্চ
* **ধরন:** Historical Repeat (**২ পরীক্ষায়, একই instance**)
* **ঐতিহাসিক প্রমাণ:**
  * **Bangladesh Bank Assistant Director (ICT) 07.02.2025** — `written/operating-system.md` → *Deadlock & Resource Allocation (23)*
  * RAKUB Maintenance Engineer (PO) 05.10.2021 — একই instance, সাথে যোগ করা *"Executing safety algorithm shows that sequence ⟨P1, P3, P4, P0, P2⟩ satisfies safety requirement"*
* **প্রশ্নের ভ্যারিয়েশন:** *"The four conditions … are mutual exclusion, hold and wait, no preemption and circular wait. Give an example to show that these conditions are not sufficient"* (DPDC Assistant Manager (ICT) 27.06.2025); *"A system has P processes each needing a maximum of m resources and a total of r resources available. Which conditions must hold to make the system deadlock free?"* (BPSC Multiple Ministry AP (ICT) 19.07.2023); *"Why resource allocation graph used for deadlock detection?"* (Cadet College Lecturer ICT 11.05.2025)।
* **সংশ্লিষ্ট কনসেপ্ট:** deadlock-এর চারটি আবশ্যক শর্ত · resource-allocation graph · prevention vs avoidance vs detection vs recovery · safe vs unsafe state। *Deadlock* সাবটপিকে **২৩টি লিখিত প্রশ্ন** — OS ফাইলের চতুর্থ বৃহত্তম।

---

### T1.2 — ব্যাংক schema normalize করে PK / FK বের করা

**প্রশ্ন (ঐতিহাসিক, হুবহু):**
> **A Bank schema is given below: Bank(Br_Name, Br_City, Assets, Acc_name, Acc_Num, Balance)**
> (a) Provided and Normalize and point out Primary and Foreign Key?
> (b) Show that is the schema and state that why your schema is in good form.

* **প্রাধান্য:** সর্বোচ্চ
* **ধরন:** Historical Repeat (AD(ICT) ২০২৫) + Question Family
* **ঐতিহাসিক প্রমাণ:** `written/database.md` → *Normalization & Database Design (21)*। এটা Silberschatz-এর ক্লাসিক branch/account decomposition, শুধু বাংলাদেশ ব্যাংকের দৃশ্যপটে বসানো। Normalization লিখিত ফোল্ডারে **২১** জায়গায় এসেছে, যার মধ্যে *"Why normalization is required in Database? Write shortly about 3NF"* (BPSC Ministry of Power, Energy & Mineral Resources AD(ICT) (CS/CSE) 29.05.2025 — একই ধরনের AD(ICT) পদ), *"Explain the differences between 2NF and 3NF with examples"* (BPSC Network/Website Manager (CSE) 21.05.2025), *"BCNF is stricter than 3NF"* (17th NTRCA Lecturer (ICT) 2023), *"Why Normalization is used in database? Explain 1st Normal form using an example"* (BPSC Home Affairs Assistant DBA (CSE) 2022)।
* **যে ধাঁচে উত্তর মুখস্থ রাখবেন:** `Branch(Br_Name, Br_City, Assets)`, `Account(Acc_Num, Br_Name, Balance)` আর `Depositor(Acc_name, Acc_Num)` — এই তিনটায় ভাগ করুন; প্রত্যেকটার PK দেখান; `Account`-এ `Br_Name` কে FK হিসেবে দেখান; তারপর যুক্তি দিন — "partial dependency নেই (2NF), transitive dependency নেই (3NF), প্রতিটা determinant candidate key (BCNF)"।
* **সংশ্লিষ্ট কনসেপ্ট:** `written/database.md` → *Keys in DBMS (**34**)* — ডেটাবেজের দ্বিতীয় বৃহত্তম সাবটপিক। Primary vs candidate vs super vs foreign key-এর সংজ্ঞা ৩০+ পরীক্ষায় ফিরে এসেছে, যার মধ্যে **Bangladesh Bank AP 03.02.2023** আর **Bangladesh Bank AP 2016** (*"Define 'integrity rules' of database systems"*)।

---

### T1.3 — ব্যাংক সার্ভারের জন্য firewall placement diagram (DMZ)

**প্রশ্ন (ঐতিহাসিক, হুবহু):**
> **Bangladesh Bank have client server and the communication with Mail Server, DNS server, Web server. Bangladesh Bank want to ensure the security using firewall on those server. Draw a diagram with the scenario.**

* **প্রাধান্য:** সর্বোচ্চ
* **ধরন:** Historical Repeat (**বাংলাদেশ ব্যাংক এটা ৬ বছরের ব্যবধানে দুইবার জিজ্ঞেস করেছে**)
* **ঐতিহাসিক প্রমাণ:**
  * **Bangladesh Bank Assistant Director (ICT) 07.02.2025** — `written/computer-network-security.md` → *Firewalls & Network Defense (20)*
  * **Bangladesh Bank Assistant Programmer 2019 (ET: DU)** — *"What is firewall? explain its work. Draw a LAN network and a firewall where firewall will be situated."*
* **প্রশ্নের ভ্যারিয়েশন:** *"What is DMZ in data center? Describe using diagram? Write the network devices in this system?"* (BDCCL Assistant Manager (Cyber Security) 14.10.2022); *"DMZ and firewall placement in a diagram"* (MGMCL Assistant Manager (ICT) 20.05.2022); *"What is Demilitarized Zone (DMZ) and sandbox for security test?"* (PGCB AE (CSE) 17.05.2024); *"What is firewall? Draw a LAN network to showing firewall"* (BREB Junior Assistant Manager (ICT) 2021); *"Draw a diagram of LAN including network Firewall … List 5 major types of network firewalls. Differentiate between Traditional Firewall and Next Generation Firewall"* (Rupali Bank ANE 04.11.2023)।
* **সংশ্লিষ্ট কনসেপ্ট:** packet-filter vs stateful vs proxy vs NGFW vs WAF (Islami Bank PLC SO (Network/System) 14.03.2025-এ পুরো NGFW-vs-WAF তুলনার টেবিল আছে); firewall vs antivirus (BREB AGM (IT) 2021); firewall vs gateway (DMTCL AE (ICT) 27.01.2023); stateful vs stateless firewall (Dutch Bangla Bank 2019)। **তিন-জোনের ডায়াগ্রামটা — Internet → NGFW → DMZ (Mail/DNS/Web) → internal firewall → LAN/core banking — মুখস্থ করে আঁকার প্র্যাকটিস করুন।**

---

### T1.4 — ইমেইল ট্রান্সফার: application/transport প্রোটোকল আর ধাপে ধাপে পথ

**প্রশ্ন (ঐতিহাসিক, হুবহু):**
> **Sinthia wants to send an email to her friend (Afsana). He sends the email through application and transport layer.**
> (a) Mention the protocol of application layer and transport layer.
> (b) Write down the steps of Mail transfer from Afsana to Sinthia.

* **প্রাধান্য:** সর্বোচ্চ
* **ধরন:** Historical Repeat (AD(ICT) ২০২৫) + Recurring Concept
* **ঐতিহাসিক প্রমাণ:** `written/computer-networks.md` → *Email Architecture & Protocols (SMTP, POP3, IMAP) (10)*। কনসেপ্টটা ফিরে এসেছে: *"SMTP, DNS, DHCP, NAT এর কাজ কি লিখ?"* (BTCL JAM 2022); *"Distinguish the purpose of SMTP and IMAP in email communication"* (BPSC Home Affairs Senior Computer Operator (CSE) 13.09.2022); *"What is SMTP? How SMTP works?"* (BPSC AP (ICT) 2019); *"Difference between SMTP and SNMP"* (RAKUB Assistant Network System Engineer 03.11.2023); **Bangladesh Bank AME 2017** (*"Write short notes on DHCP and SMTP"*)।
* **যে ধাঁচে উত্তর লিখবেন:** Application layer = SMTP (পাঠানো, MTA→MTA), POP3/IMAP (সংগ্রহ), সাথে DNS MX lookup। Transport layer = TCP (SMTP 25/587, POP3 110, IMAP 143)। ধাপ: compose → UA → প্রেরকের mail server-এ SMTP → প্রাপকের domain-এর জন্য DNS MX query → প্রাপকের mail server-এ SMTP relay → mailbox-এ জমা → প্রাপকের UA POP3 বা IMAP দিয়ে টেনে নেয়।
* **সংশ্লিষ্ট কনসেপ্ট:** MIME/Content-type (Sonali Bank and BDBL SO(IT) 25.09.2021); DNS কেন UDP ব্যবহার করে কিন্তু zone transfer-এ TCP (Combined Bank SO(IT) 17.10.2025); URL টাইপ করলে DNS resolution-এর ধারাক্রম (একই পরীক্ষা, আর BPSC Sub-AE Ministry of Agriculture 2021)।

---

### T1.5 — একটি message-এর total latency (Forouzan-এর সূত্র)

**প্রশ্ন (ঐতিহাসিক, হুবহু):**
> **What is Total Latency for a 3-kbyte message (an e-mail) if the bandwidth of the network is 1 Gbps? Assume that the distance between the sender and the receiver is 300 km and that light travels at 2 × 10⁸ m/s. Round Trip Time 50 ms Queuing Time 5 ms**

* **প্রাধান্য:** সর্বোচ্চ
* **ধরন:** Historical Repeat (AD(ICT) ২০২৫) + পাঠ্যবইয়ের পরিবার
* **ঐতিহাসিক প্রমাণ:** `written/computer-networks.md` → *Error Detection & Data Communication (CRC, Throughput) (14)*। একই Forouzan পরিবার MCQ অংশেও আছে: *"What is the propagation time for a 2.5-kbyte message (an e-mail) if the bandwidth of the network is 1 Gbps? … distance 12,000 km … 2.4 × 10⁸ m/s"* (Sonali Bank and BDBL SO(IT) 25.09.2021)।
* **যে ধাঁচে উত্তর লিখবেন:** `Latency = Propagation time + Transmission time + Queuing time (+ processing)`; Propagation = দূরত্ব / propagation speed = ৩,০০,০০০ মি ÷ ২×১০⁸ = ১.৫ ms; Transmission = message size / bandwidth = ৩,০০০×৮ bit ÷ ১০⁹ = ২৪ µs। প্রতিটা term ইউনিটসহ দেখান।
* **সংশ্লিষ্ট কনসেপ্ট:** ব্যাংকের প্রশ্নকর্তারা যে পুরো Forouzan ক্যালকুলেশন ব্লক ঘুরিয়ে ফিরিয়ে দেন — প্রতি সেকেন্ডে ১০০ পৃষ্ঠার bit rate (Sonali/Janata/Rupali 25.10.2021, Rupali ANE 2021, Janata Bank ANE (SO) 2020 — **৩ পরীক্ষা**); Nyquist `C = 2B log₂ L`; Shannon `C = B log₂(1+SNR)`, যার ৩০০০ Hz / SNR ৩১৬২-র টেলিফোন-লাইন instance আছে RPGCL 2022 **এবং** Combined Bank AP 09.06.2023-এ; guard-band multiplexing (**BB SO(IT) 2024** + SO IT 2026)।

---

### T1.6 — Boolean expression থেকে truth table

**প্রশ্ন (ঐতিহাসিক, হুবহু):**
> **Ā·B̄·(A+B)‾·C ; Write Truth Table.**

* **প্রাধান্য:** সর্বোচ্চ
* **ধরন:** Historical Repeat (AD(ICT) ২০২৫) + Question Family
* **ঐতিহাসিক প্রমাণ:** `written/dld.md` → *Logic Gates & Universal Gates (33)*, লিখিত অংশে DLD-র বৃহত্তম সাবটপিক। "expression দেওয়া হলো, truth table বানাও / নির্দিষ্ট input-এ মান বের করো" — এই একই ধাঁচ এসেছে: *"Logic Circuit of Boolean algebra: Q = C̄ + ĀB + BC(B+C)‾; Where output Q and input (A,B,C)=(0,0,1)?"* (Sonali Bank PLC Assistant DBA 23.02.2024); *"Draw the logic circuit of the Boolean Expression, Q = ĀB̄ + BC(B+C)‾; find Q where (A,B,C)=(1,0,1)"* (Combined Bank AME/AE(IT) 24.02.2024); *"Construct a truth table for (r ∨ (q ∧ ¬p)) ∧ ¬(r ∧ (q ∧ ¬p))"* (Combined 3 Banks AP 2018); *"Truth table construction for f(A,B,C,D) = (A+B) ⊕ (CD)"* (DESCO AE(CSE) 2016)।
* **সংশ্লিষ্ট কনসেপ্ট:** De Morgan-এর উপপাদ্য — *Boolean Algebra & De Morgan's Theorem (19)*, জিজ্ঞেস করেছে **BB AME 2019** (*"How will realize an AND gate and OR gate using CMOS NAND and NOR gate?"*) আর **BB AME 2011** (*"What do you understand by universality of logic gate? Prove universality of NOR logic gate."*)।

---

### T1.7 — মানের তালিকা থেকে min-heap / max-heap নির্মাণ

**প্রশ্ন (ঐতিহাসিক, হুবহু):**
> **Construction of Min Heap: Given Value 12, 29, 33, 56, 66, 99, 100, and 344**

* **প্রাধান্য:** সর্বোচ্চ
* **ধরন:** Historical Repeat (AD(ICT) ২০২৫) + Recurring Concept
* **ঐতিহাসিক প্রমাণ:** `written/algorithm.md` → *Heap & Priority Queue (2)*; `written/data-structure.md` → *Priority Queues & Heaps (Min/Max Heap) (8)*। একই পরিবার: *"Given item- 40, 45, 80, 90, 50, 70. Draw Heap and Binary search tree (BST)"* (SGFL AE (IT) 2023); *"Given an array of 6 elements: {15, 19, 10, 7, 17, 16}. Draw heap tree and again draw the tree after deletion of element 7"* (PGCB AE (CSE) 30.09.2021); *"Binary tree টিকে heapify করুন যেন maximum heap-এ রূপান্তরিত হয়"* (NACTAR 2020); *"Heapify the MAX heap tree"* (PGCB Sub-AE (CSE) 2020); *"Draw (max/min) heap binary tree using 11 nodes"* (DESCO Sub-AE (CSE) 2019); *"Max Heap Operation [a-j] show heap"* (Combined Bank AP 09.06.2023); *"Describe, and estimate the costs of, a procedure to insert a new item into an existing binary max-heap"* (Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024)।
* **সংশ্লিষ্ট কনসেপ্ট:** heapsort অ্যালগরিদম আর max-heap-এর property (BPSC Home Affairs Senior Computer Operator (CSE) 13.09.2022); priority queue-র implementation হিসেবে heap (এটাই AD(ICT) ২০২৫-এর MCQ, দেখুন MCQ ফাইলের T1.3)।

---

### T1.8 — Subnetting: ব্লক ভাগ করে network / broadcast / mask / usable range

**প্রশ্ন (ঐতিহাসিক, হুবহু — BB Senior Officer (IT) ২০২৪-এর রূপ):**
> **An organization is granted the IPv4 network block 14.24.74.0/24 and needs to segment it into two subnets: Subnet A (requires 120 addresses) and Subnet B (requires 60 addresses). Allocating sequentially from the requirement first to maximize remaining address space, state only the Network Address (with its CIDR mask) and the Broadcast Address for both subnets.**

* **প্রাধান্য:** সর্বোচ্চ
* **ধরন:** Historical Repeat (**বাংলাদেশ ব্যাংক SO(IT) ২০২৪ → SO IT 25-07-2026-এ হুবহু পুনর্ব্যবহার**) + ডেটাসেটের সবচেয়ে ঘন টপিক
* **ঐতিহাসিক প্রমাণ:** `written/computer-networks.md` → *Subnetting & IP Addressing (**109**)* — পুরো ৫,৯১০ প্রশ্নের মধ্যে বৃহত্তম সাবটপিক। বাংলাদেশ ব্যাংকের instance: **SO(IT) Grade-9 2024** (ওপরের প্রশ্নটা, আইটেম 6.10) আর **AME 2017** (*"How many subnets and hosts per subnet can you get from the network 172.20.0.0/27?"*)। একটা প্রশ্ন — *"Given IP address 192.168.1.50, Subnet Mask: 255.255.255.240. Find the valid IP range. Also find Network address and Broadcast address"* — **৪টা ট্যাগ** বহন করছে (NWPGCL Assistant Manager (ICT) 12.01.2024, BTCL Assistant Manager (Technical) 2023, BPDB AE (CSE) 10.05.2024, BIWTA AE (CSE) 24.02.2023)।
* **প্রশ্নের ভ্যারিয়েশন:** অসম সাইজের ডিপার্টমেন্ট নিয়ে VLSM (Rupali Bank ANE 2021: 192.168.0.0/20 থেকে ২০০০/১০০০/৬০০০/৮০০০ host; Dhaka WASA AME (Network) 04.07.2025: 245.248.128.0/20-র অর্ধেক / এক-চতুর্থাংশ / এক-চতুর্থাংশ; Cadet College Lecturer ICT 11.05.2025: 192.168.0.0/24 থেকে ১১০/৫০/২০/৮ host); "৪টা সমান subnet-এ ভাগ করো" (Senior Officer IT 22-05-2026, Officer (IT) 31 Jul 2026, Combined Bank Officer (IT) 09.05.2026 — তিনটাই ব্যাংক-শাখার দৃশ্যপট হিসেবে সাজানো)।
* **সংশ্লিষ্ট কনসেপ্ট:** classful vs classless; শ্রেণিভিত্তিক private range; wildcard mask; CIDR aggregation; **NAT (১৩টি লিখিত প্রশ্ন)** এবং **VLAN vs subnetting** (BSCCPL AME 21-08-2026)।

---

### T1.9 — গ্রুপভিত্তিক aggregate SQL query (COUNT + AVG + GROUP BY)

**প্রশ্ন (ঐতিহাসিক, হুবহু — BB Senior Officer (IT) ২০২৪-এর রূপ):**
> **Consider the following relation: Employee(EmpID, Name, Department, Salary). Write an SQL query to retrieve the Department, the total number of employees, and the average salary for each department. The output should display one record for each department.**

* **প্রাধান্য:** সর্বোচ্চ
* **ধরন:** Historical Repeat (**BB SO(IT) ২০২৪ → SO IT 25-07-2026-এ হুবহু পুনর্ব্যবহার**) + subnetting-এর পরেই বৃহত্তম লিখিত সাবটপিক
* **ঐতিহাসিক প্রমাণ:** `written/database.md` → *SQL Queries (**87**)*। বাংলাদেশ ব্যাংকের SQL instance: **SO(IT) Grade-9 2024** (ওপরের), **AP 03.02.2023** (পাঁচ-টেবিলের Movies/People/Genres schema-য় *"Write a SQL query to return the number of movies that are romantic comedies"*), **AP 2016** (*"Write a SQL query to get the second highest salary from Employee table"*), **Recruitment Test 2020** (*"Give some examples of DDL, DML and DCL commands"*)।
* **যেসব ভ্যারিয়েশন অবিরাম ফিরে আসে:** ডিপার্টমেন্টভিত্তিক average salary (Islami Bank QA 14.03.2025, NESCO JAM (ICT) 2021, BTCL JAM 2022, Combined Bank AP 09.02.2024); কোম্পানি/ডিপার্টমেন্টের গড়ের চেয়ে বেশি বেতন পাওয়া employee (BGDCL 15.03.2024, BPDB 24.02.2023, CAAB 2022, Dutch Bangla Bank 2019, আর Sonali & Janata Bank Officer (IT) 14.10.2023 ও Rupali Bank ANE 04.11.2023 — দুটোতেই *এই query-টা বিশ্লেষণ করো* রূপে); দ্বিতীয় সর্বোচ্চ বেতন (BCC AP 2017, WZPDCL 2019, **BB AP 2016**); duplicate row (BCC AP 18.10.2025, BBA AP 12.07.2025, Agrani Bank 2017); চার ধরনের JOIN-এর ফলাফলসহ (Combined Bank SO(IT) 17.05.2024, BPDB 10.05.2024)।
* **সংশ্লিষ্ট কনসেপ্ট:** `WHERE` vs `HAVING`; correlated subquery; একাধিক aggregate নিয়ে `GROUP BY`; JOIN-এ কত row আসবে সেই যুক্তি; view আর trigger (*PL/SQL & Database Triggers (7)*)।

---

### T1.10 — K-map দিয়ে minimal SOP-এ সরলীকরণ

**প্রশ্ন (ঐতিহাসিক, হুবহু — BB Senior Officer (IT) ২০২৪-এর রূপ):**
> **Simplify the following boolean expression using 4 variable K-map: F(A,B,C,D) = Σm(0,3,5,7,8,10,11,12,13,14,15). Draw the K-map grid, clearly show your groupings (loops), and write the final simplified Sum-of-Products (SOP) expression.**

* **প্রাধান্য:** সর্বোচ্চ
* **ধরন:** Historical Repeat (**BB SO(IT) ২০২৪ → SO IT 25-07-2026-এ হুবহু পুনর্ব্যবহার**)
* **ঐতিহাসিক প্রমাণ:** `written/dld.md` → *Karnaugh Map (K-Map) (19)*। একই instance অন্যত্রও বসানো হয়েছে: *"Show minimal function using K-Map: F(A,B,C,D) = Σ(2,8,9,11,13,15)"* আছে **দুইটা** ট্যাগে (BPDB AE (CSE) 10.05.2024 আর BICIC AP 2022)। আবার *"Simplify F(A,B,C,D) = ACD + AB + D̄ + AC̄D using K-map and draw the logic circuits"*-ও **দুইটা** ট্যাগে (BPSC Home Affairs Assistant DBA (CSE) 2022 আর BPSC AP (CSE) 2019)।
* **সংশ্লিষ্ট কনসেপ্ট:** SOP vs POS; don't-care condition; সরলীকৃত function শুধু NAND বা শুধু NOR দিয়ে বাস্তবায়ন (*"X = ĀBC + AB̄C + ABC̄ + ABC সমীকরণটির সরলীকৃত মান NAND এবং NOR গেইট দ্বারা বাস্তবায়ন করুন"* — 18th NTRCA Assistant Teacher (ICT) 12.07.2024); K-map + decoder মিলিয়ে comparator/7-segment (Rupali Bank ANE 2021, BPSC Sub-AE Ministry of Agriculture 2021)।

---

## ⭐ Tier 2 — উচ্চ প্রাধান্য

| # | প্রশ্ন / কনসেপ্ট | ধরন | ঐতিহাসিক প্রমাণ |
|---|---|---|---|
| T2.1 | **CPU scheduling: FCFS, SJF, Priority আর RR-এর Gantt chart + average waiting time + average turnaround time** | Recurring Concept (২৫টি লিখিত প্রশ্ন) | `written/operating-system.md` → *CPU Scheduling Algorithms (25)* + *CPU Scheduling (6)*। burst time ১০/১/২/১/৫ আর priority ৩/১/৩/৪/২ — এই পাঁচ-process টেবিলটা এসেছে BPSC Ministry of Power, Energy & Mineral Resources **AD(ICT) (CS/CSE) 29.05.2025**-এ (সরাসরি তুলনীয় AD(ICT) পদ), আর আবার Passport Office AP 2024-এর প্রশ্নপত্রে burst time ১৫/২/৪/২/৮ দিয়ে। আরও Combined Bank SO(IT) 17.10.2025 (পাঁচ job, চার অ্যালগরিদম), BCC AP 18.10.2025, DPDC AE (CSE) 17.10.2025, Sonali Bank PLC Assistant DBA 23.02.2024, BCIC AP 14.02.2025, Teletalk 2023, BIWTA 2023, Rupali Bank ANE 2021, National University AP 2020, Sundharban Gas 2020, **Bangladesh Bank AME 2011** (*"What is turnaround time of a process?"*)। |
| T2.2 | **Page replacement: FIFO / LRU / Optimal-এ page-fault সংখ্যা** | Recurring Concept | `written/operating-system.md` → *Virtual Memory & Page Replacement (Thrashing) (16)*। প্রমিত reference string 7,0,1,2,0,3,0,4,2,3,0,3,2,1,2,0,1,7,0,1 আর ৩টা frame এসেছে BSCCPL AME 21-08-2026-এ; 4,7,6,1,7,6,1,2,7,2 আর ৩ frame BPDB AE (CSE) 2021-এ; 4,7,6,1,2,7,2 BPDB 10.05.2024-এ; 1,3,0,3,5,6,3 Combined Bank AP 09.06.2023-এ। Thrashing ব্যাখ্যা Combined Bank SO(IT) 17.10.2025 আর Titas Gas 2021-এ। |
| T2.3 | **Linux command (file permission, listing, search, disk, network)** | Recurring Concept (**OS-র বৃহত্তম সাবটপিক**) | `written/operating-system.md` → *Linux / Unix Commands & Administration (**47**)*। যেগুলো বারবার আসে: chmod/permission (Islami Bank PLC SO 14.03.2025, APSCL 2021, JGTDSL 2021, BTCL JAM 2022, DESCO 2019, BPDB 2018); hidden file (`ls -a`) NESCO 2021, MGMCL 2022, WASA 2022-এ; N লাইনের head/tail (BTCL 2023, Titas Gas 2024, Milk Vita 2023, APSCL 2021); grep (BCC AP 12.02.2021, BITAC 2021, BCIC 14.02.2025); ip/ifconfig (PGCL 2021, DESCO 2025, BARI 2025); df/free/top (BCIC 14.02.2025)। |
| T2.4 | **Hashing vs encryption; symmetric vs asymmetric; RSA; Caesar cipher** | **৩ পরীক্ষার repeat** + BB-তে এসেছে | `written/computer-network-security.md` → *Cryptography (**31**)*। *"Explain the operational difference between Hashing and Encryption"* ট্যাগ করা আছে **Bangladesh Bank Senior Officer (IT), Grade-9 2024** (আইটেম 6.2), SO IT 25-07-2026, DESCO AE (CSE) 10.09.2022 আর BKSP AP 03.12.2022-এ। উদাহরণসহ symmetric vs asymmetric ৮+ পরীক্ষায় ফিরে এসেছে। **BB AP 03.02.2023** Diffie-Hellman key exchange-এ MITM আক্রমণ জিজ্ঞেস করেছিল। |
| T2.5 | **CIA triad আর তিন নীতি কীভাবে আক্রমণের সাথে মেলে** | BB-তে এসেছে + recurring | `written/computer-network-security.md` → *Security Principles (CIA Triad) (8)*। **Bangladesh Bank AP 03.02.2023**: *"Preserving confidentiality integrity and availability of data is a restatement of the concern over falsification, interception, masquerade and denial of service. Explain how the first three concepts relate to the last four."* আরও Combined Bank SO(IT) 17.10.2025, NPCBL Cyber Security Analyst 11 July 2026, Combined Bank Officer (IT) 09.05.2026 ও 03.01.2026, EGCB 28.01.2023, Teletalk 2023। |
| T2.6 | **SQL injection ও XSS: কীভাবে কাজ করে আর কীভাবে প্রতিরোধ** | **৩ পরীক্ষার repeat** | `written/computer-network-security.md` → *Web Security Vulnerabilities (19)*। *"What is SQL Injection? How to Prevent against SQL Injection Attacks?"*-এ তিনটা ট্যাগ (RAKUB Programmer (PO) 12.10.2021, RAKUB ME (PO) 05.10.2021, Dhaka WASA AME (Network) 04.07.2025)। XSS/CSRF এসেছে Islami Bank QA 14.03.2025, DESCO 20.06.2025, Titas Gas 24.05.2024, BICIC 2022, SPCB 2022, 16th NTRCA 2019-এ। **BB AME 2017** জিজ্ঞেস করেছিল *"What are the important steps to secure a web server?"* |
| T2.7 | **OSI / TCP-IP layer, প্রতি layer-এর function, protocol আর device** | Recurring Concept (৫২টি লিখিত প্রশ্ন) | `written/computer-networks.md` → *OSI & TCP/IP Reference Model (**52**)*। **Bangladesh Bank AP 03.02.2023** এটাকে ডিজাইন-সিদ্ধান্ত হিসেবে সাজিয়েছিল: *"the company decided to add end-to-end encryption techniques — which layer of the OSI model is suitable considering development time, software maintainability and development cost?"* **BB AP 2019** জিজ্ঞেস করেছিল *"Two OSI layers which known as 'flow Control' — which are those?"* "layer / function / protocol / device" টেবিল রূপে এসেছে Combined Bank AME/AE(IT) 24.02.2024, Rupali Bank ANE 04.11.2023, BPSC AD(ICT) (CS/CSE) 29.05.2025-এ। |
| T2.8 | **TCP vs UDP আর three-way handshake-এর ডায়াগ্রাম** | **৩ পরীক্ষার repeat** | `written/computer-networks.md` → *Transport Layer (TCP & UDP) (17)*। *"Distinguish between TCP and UDP protocols"*-এ তিনটা ট্যাগ (BPSC Security Services Division AP 13.12.2021, BPSC Home Affairs Senior Computer Operator (ICT) 13.09.2022, Combined Bank Officer (IT) 03.01.2026)। 3-way handshake ডায়াগ্রাম BRiCM 24.02.2024 **ও** BGDCL 19.11.2021-এ (২ ট্যাগ), সাথে BPSC Network/Website Manager (CSE) 21.05.2025, BICIC 2022, Sonali Bank Ltd. Officer IT 2021। **Bangladesh Bank Recruitment Test 2020** জিজ্ঞেস করেছিল *"the primary function of TCP is to turn an unreliable network into a reliable network … What are the functions performed by TCP?"* |
| T2.9 | **Cache memory: hit/miss, compulsory vs capacity miss, direct-mapped tag/index/offset, average access time** | **বাংলাদেশ ব্যাংক ৩টি আলাদা পরীক্ষায় জিজ্ঞেস করেছে** | `written/microprocessor-and-computer-architecture.md` → *Cache Memory (14)*। **BB SO(IT) Grade-9 2024** (6.3: compulsory vs capacity miss — SO IT 25-07-2026-এ পুনর্ব্যবহৃত); **BB AME 04.02.2023** (*"16 KB of data in a direct mapped cache with 4 word blocks … size of the tag, index and offset fields, 32-bit architecture"*); **BB AME 2017** (*"If main memory access time is 100 ns, cache access time is 50 ns, cache hit rate is 90% then what is the average time to read from memory?"*)। |
| T2.10 | **Instruction pipelining আর hazard** | **বাংলাদেশ ব্যাংক ৩টি আলাদা পরীক্ষায় জিজ্ঞেস করেছে** | `written/microprocessor-and-computer-architecture.md` → *Instruction Pipelining & Hazards (9)*। **BB SO(IT) 2024** (6.1: single-cycle-এর বদলে multi-stage pipelining কেন — SO IT 25-07-2026-এ পুনর্ব্যবহৃত); **BB AME 2019** (*"How is computer Architecture characterized. What are the 5 stages of the DLX pipeline?"*); **BB AME 2011** (*"What is pipelining? What is opcode and operand in machine code? Explain snooping cache."*)। |
| T2.11 | **OOP: inheritance, polymorphism, overloading vs overriding, encapsulation — কোড উদাহরণসহ** | **বাংলাদেশ ব্যাংক ৪টি আলাদা পরীক্ষায় জিজ্ঞেস করেছে** + বৃহত্তম OOP সাবটপিক | `written/oop.md` → *OOP Concepts (Inheritance & Polymorphism) (**54**)*। **BB AP 03.02.2023** (একজোড়া Java class দিয়ে কোন method overload / override / hide করছে); **BB Recruitment Test 2020** (*"The main advantage of Inheritance is the ability to reuse the code. Explain in brief different types of Inheritance"*); **BB AP 2016** (*"What is polymorphism? What is the difference between method overriding and method overloading?"*); **BB AP 2019** (Java-তে multi-threaded Overdraft Account class)। |
| T2.12 | **static variable আর recursion নিয়ে Java output tracing** | Historical Repeat (**BB SO(IT) ২০২৪ → SO IT 2026**) | `written/oop.md` → *Output Tracing & Recursion (10)*। ঠিক ঐ প্রোগ্রামটা (`static int x = 5; fun(n) { if (n<=1) return 1; x = x + 2; return fun(n-1) + x; }` — `fun(3)` প্রিন্ট) ট্যাগ করা আছে **BB SO(IT) Grade-9 2024** আর SO IT 25-07-2026-এ। C অংশে output tracing হলো `written/c-programming.md`-এর **৫৭ প্রশ্নের** *Output Tracing & Control Flow* সাবটপিক। |
| T2.13 | **Sorting অ্যালগরিদম: ধাপে ধাপে trace + best/average/worst complexity টেবিল** | Recurring Concept (**বৃহত্তম algorithm সাবটপিক**) | `written/algorithm.md` → *Sorting Algorithms & Complexity (**36**)*। **Bangladesh Bank Recruitment Test 2020** (*"Insertion sort is a simple sorting algorithm. Write a program to sort some given numbers using insertion sort"*)। complexity টেবিল পূরণ করার রূপে DPDC Assistant Manager (ICT) 27.06.2025-এ; quicksort-এর worst case Combined Bank SO(IT) 17.10.2025, Combined 2 Bank Officer IT 04.10.2024, BKSP 2024, PetroBangla 2024-এ; merge-sort recurrence T(n)=2T(n/2)+n BPSC Multiple Ministry AP (CSE) 19.07.2023-এ। |
| T2.14 | **BFS / DFS traversal ও পার্থক্য; Kruskal দিয়ে MST; Dijkstra দিয়ে shortest path** | AD(ICT)-সংলগ্ন + recurring | `written/algorithm.md` → *Graph Traversal (17)*, *Shortest Path & MST (15)*। Kruskal-এর MST এসেছে BPSC **AD(ICT) (CS/CSE) 29.05.2025**, RAKUB Programmer (PO) 2021, BAUST 2021, Sonali Bank Ltd. Officer IT 2021, DESCO 2022-এ। BFS-vs-DFS পার্থক্য BPSC Security Services AP 13.12.2021, 17th NTRCA 2023, BPSC Ministry of Agriculture 2022, DPDC 17.10.2025-এ। |
| T2.15 | **Software testing: unit vs integration; black-box vs white-box; verification vs validation** | **BB-তে এসেছে + ৫ পরীক্ষার repeat** | `written/software-engineering.md` → *Software Testing & Evaluation (**40**)*। *"What is the main difference between black box and white box testing?"*-এ **পাঁচটা** ট্যাগ (BARC Programmer 04.08.2023, BPSC AME (CSE) 2020, MRA AME 2022, Teletalk 2023, SGFL 2021)। **BB SO(IT) 2024** 6.5-এ unit vs integration (SO IT 2026-এ পুনর্ব্যবহৃত); **BB AME 04.02.2023** CMMI level 3-এ verification/validation; **BB AME 2019** *"How would you test an ATM in a banking system?"*; **BB Recruitment Test 2020** implementation পর্যায়ে কোন কোন test হয়। |
| T2.16 | **SDLC মডেল: waterfall vs agile, আর কোন পরিস্থিতিতে কোনটা বাছবেন** | Recurring Concept (**বৃহত্তম SE সাবটপিক**) | `written/software-engineering.md` → *SDLC Phases & Models (**45**)*। দৃশ্যপট-ভিত্তিক প্রশ্নই বেশি: *"You are asked to lead a team … deploy as fast as possible. Between Waterfall and Incremental, which approach will you take?"* (Combined Bank SO(IT) 17.05.2024); *"the librarian wants the system delivered in phases so that feedback can be incorporated"* (Officer (IT) 31 Jul 2026); *"Critically analyze the limitations of the Waterfall model and explain how Agile methodologies address those"* (Combined Bank Officer (IT) 03.01.2026)। |
| T2.17 | **UML: দৃশ্যপট থেকে class diagram আর use-case diagram** | BB-তে এসেছে + recurring | `written/software-engineering.md` → *UML Diagrams (14)*। **Bangladesh Bank AP 03.02.2023**: *"Draw a class diagram. A token-ring based local area network (LAN) … Workstations are originators of messages; servers and printers are network nodes that can receive messages …"* ব্যাংক-দৃশ্যপটের রূপ: ATM use case (Combined Bank HBFC/BKB AP 2018, Agrani Bank 2017), online banking use case (Combined Bank Officer (IT) 09.05.2026), e-commerce class diagram (SO IT 25-07-2026, PGCB 17.05.2024, Combined 2 Bank Officer IT 04.10.2024)। |
| T2.18 | **RAID level আর ব্যাংকের জন্য কোনটা বাছবেন** | Recurring Concept | `written/microprocessor-and-computer-architecture.md` → *RAID Architecture & Storage (15)*। *"Which RAID level is best and why?"*-এ দুইটা ট্যাগ (Sonali Bank PLC Assistant DBA 23.02.2024 আর BEPRC AP 08.08.2026)। RAID 1 vs RAID 5 তুলনা BPSC Home Affairs Senior Computer Operator (CSE) 13.09.2022 আর BDCCL Cyber Security 14.10.2022-এ; ডেটাবেজে RAID-এর প্রাসঙ্গিকতা Sonali Bank PLC Assistant DBA 23.02.2024-এ। |

---

## 📌 Tier 3 — মধ্যম প্রাধান্য

| # | কনসেপ্ট | ঐতিহাসিক প্রমাণ (`all-questions/written/`) |
|---|---|---|
| T3.1 | **Interpreter vs compiler; compiler-এর phase** | *Compiler vs Interpreter (7)* — পার্থক্যের প্রশ্নটায় **ছয়টা** ট্যাগ: MRA AME 2020, BPSC Home Affairs Assistant DBA (ICT) 2022, CAAB AP 2022, PGCB Sub-AE (CSE) 30.09.2021, Combined Bank Officer (IT) 03.01.2026, BPSC Ministry of Agriculture AP 15.02.2022। আরও 41তম BCS 2021। |
| T3.2 | **DFA/NFA ডিজাইন আর regular expression; CFG ambiguity** | *Regular Expressions & Finite Automata (7)*, *Grammar & Ambiguity (5)*। **Bangladesh Bank SO(IT) Grade-9 2024** জিজ্ঞেস করেছিল `E → E+E | E*E | id` grammar-টা `id + id * id` string-এর জন্য ambiguous কি না — এটাও SO IT 25-07-2026-এ ট্যাগ করা। |
| T3.3 | **Data structure-এর মূল কথা: array vs linked list; stack vs queue; circular queue** | `written/data-structure.md` → *Linked List (15)*, *Stack (20)*, *Queue (6)*। **BB SO(IT) 2024**: 6.6-এ circular vs linear queue আর 6.12-এ tree-র পরিভাষা (দুটোই SO IT 2026-এ পুনর্ব্যবহৃত); **BB Recruitment Test 2020**: enqueue-র ধাপ; **BB AP 2016**: `((A+B)*C-(D-E)^F)`-র prefix ও postfix। |
| T3.4 | **Tree: দুইটা traversal থেকে গাছ বানানো; BST-তে insert/delete; B/B+ tree** | *Tree (27)* — data-structure-এর বৃহত্তম সাবটপিক। preorder+inorder থেকে পুনর্নির্মাণ BSCCPL AME 21-08-2026, BAUST 2021, Rupali Bank ANE 2021, APSCL 2021-এ; pre+post BPDB 10.05.2024-এ; B-tree 17th NTRCA 2023-এ; B+ tree index Titas Gas 2021-এ। |
| T3.5 | **Linear probing দিয়ে hash table** | *Hashing & Hash Tables (6)*। **Bangladesh Bank AP 03.02.2023**: *"Consider a hash table of size 13 … h(k) = k mod 13. Insert keys 10, 3, 6, 16, 17, 19 using linear probing to resolve collisions. Show all the work."* আরও JGTDSL 2021 (h(x)=x%11) আর Sonali & Janata Bank Assistant DBA 2022। |
| T3.6 | **C প্রোগ্রামিং: প্রোগ্রাম লেখা (prime, factorial, Fibonacci, series-এর যোগফল, pattern, array-র max)** | *Basic Programs & Control Statements (**111**)* — subnetting আর SQL-এর পরে একক বৃহত্তম লিখিত সাবটপিক। **BB AP 03.02.2023** (A ও B-র LCM); **BB AP 2016** (১০০ পর্যন্ত Fibonacci); **BB AP 2019** (২০টা আইটেমের সর্বোচ্চ দাম); **BB Recruitment Test 2020** (overtime সহ সাপ্তাহিক বেতন; recursive factorial)। |
| T3.7 | **Recursion: লেখা, trace করা, আর recurrence বের করা** | *Recursion & Functions (38)*। **BB Recruitment Test 2020** (recursive factorial অ্যালগরিদম); call-by-value vs call-by-reference ফিরে এসেছে BPSC Home Affairs Assistant DBA (CSE) 2022 + BPSC Ministry of Agriculture AP 2022-এ (২ ট্যাগ) আর আরও ৬টা পরীক্ষায়। |
| T3.8 | **Memory management: paging vs segmentation; page-table-এর আকার; internal vs external fragmentation** | *Memory Management & Paging (16)*। page-table-এর আকারের হিসাব BPSC **AD(ICT) (CS/CSE) 29.05.2025** (৪ GB RAM, ৪ KB page, ৩২-bit VA, ৮-byte PTE), Dhaka WASA 04.07.2025, Combined Bank SO(IT) 17.10.2025, SGFL 2023-এ। |
| T3.9 | **Cloud: IaaS/PaaS/SaaS বাছাই; VM vs container; multi-tenancy** | `written/cloud-computing.md` → *Cloud Service Models (13)*, *Virtualization & Containers (8)*। **BB SO(IT) 2024** (6.11 PaaS দৃশ্যপট — SO IT 2026-এ পুনর্ব্যবহৃত); **BB AME 04.02.2023** দুইবার (*"Explain IaaS, PaaS, and SaaS"*; *"Define a virtual machine with a neat diagram"*)। |
| T3.10 | **লিখিত দৃশ্যপট থেকে ER diagram, তারপর টেবিলে রূপান্তর** | `written/database.md` → *ER Diagram & Database Design (25)*। ব্যাংক-ঘেঁষা instance: Banking Management system-এর E-R (RAKUB ME (PO) 05.10.2021), Railway service (Sonali Bank Ltd. Officer IT 2021), library (BPSC AD(ICT) 29.05.2025, MRA 2020), job-application (BSCCPL AME 21-08-2026), football league (Rupali Bank ANE 2021 + Janata Bank Assistant System Administrator 2021, ২ ট্যাগ)। |
| T3.11 | **ব্যাংকের জন্য data centre, server, UPS, DR/BCP** | `written/computer-fundamental.md` → *Data Center Infrastructure & Power Management (10)*, *Server Hardware (5)*। **Bangladesh Bank AME 04.02.2023**: *"What are the challenges in optimizing energy efficiency of data centers?"* আরও Combined Bank AME/AE(IT) 24.02.2024, Combined Bank AME/Hardware 23.11.2023, Combined Bank SO(IT) 17.05.2024 (IT disaster recovery plan), BDCCL Cloud 14.10.2022 (data-centre TIER standard)। |
| T3.12 | **Blockchain, ব্যাংকিংয়ে AI/ML, digital vs traditional banking** | `written/computer-fundamental.md` → *Blockchain & Emerging Technologies (8)*, *Digital Banking & Financial Inclusion (2)*; `written/ai-and-ml.md` (৪৩টি প্রশ্ন)। সরাসরি প্রাসঙ্গিক, কারণ AD(ICT) ২০২৫-এর ইংরেজি focus-writing ছিল *"The role of AI and machine language mitigate challenges of cyber attack on banking system"*। |
| T3.13 | **Two-factor authentication আর digital certificate** | *Authentication & Access Control (16)*। 2FA-র সংজ্ঞায় দুইটা ট্যাগ (BPSC AD(ICT) (CS/CSE) 29.05.2025 + BPSC Workshop Maintenance Engineer (CSE) 2021); OTP-ভিত্তিক অনলাইন-ব্যাংকিং সুরক্ষা Combined Bank AME/AE(IT) 24.02.2024-এ; digital signature vs digital certificate Sonali & Janata Bank Officer (IT) 14.10.2023-এ। |
| T3.14 | **ইলেকট্রিক্যাল ও ইলেকট্রনিক্সের লিখিত সমস্যা (AME অংশ)** | `written/electrical-and-electronics.md` (৩৯টি প্রশ্ন)। **BB AME 04.02.2023**: *"Describe cut off, saturation and active region of operation of a transistor with diagram. Explain the working principle of an n-channel JFET…"*; **BB AME 2019**: ৩% slip-সহ ৩-ফেজ ১২-পোল alternator দিয়ে ৮-পোল induction motor; **BB AME 2017**: *"What is the difference between battery and capacitor?"* |
| T3.15 | **গণিত (২০ নম্বর): probability, definite integral, set theory, algebra, লাভ-ক্ষতি** | `written/math.md` (৯৬)। **AD(ICT) ২০২৫** দিয়েছিল একটা probability আর একটা definite integral। **BB AP 03.02.2023**: `x + 1/x = 17/4 → x − 1/x`, সারিতে দাঁড়ানো ছাত্র, সমকোণী ত্রিভুজের ক্ষেত্রফল। **BB AME 04.02.2023**: করণী সরলীকরণ, ২৫,০০০ টাকার compound-vs-simple ভাগ, লাভ%=ক্ষতি% থেকে দাম নির্ণয়, দীর্ঘতম বাহুর জ্যামিতি। **BB AP 2016**: truth table দিয়ে tautology প্রমাণ। **BB AP 2019**: এলোমেলো সংখ্যার ১০টা bit-ই ১ হওয়ার probability। |
| T3.16 | **ইংরেজি (৩০ নম্বর): focus writing + বাংলা→ইংরেজি অনুবাদ** | `written/english.md` → *Focus Writing (37)*, *Translation (18)*। **AD(ICT) ২০২৫** = একটা ১০০–১৫০ শব্দের নোট + দুইটা বাংলা বাক্য। **BB SO(IT) 2024** = *"The Importance of Digital Literacy in Expanding Cashless Transactions in Bangladesh"* + একটা বাংলা প্যাসেজ (সময়ের এক ফোঁড় …) + একটা ইংরেজি প্যাসেজ। **BB AP 03.02.2023** = *"Growing use of technology in the Financial Service Industry"*। **BB Recruitment Test 2020** = *"Post-corona Green Recovery Plans and Progress in Bangladesh"* + কোভিড-টিকার তহবিল নিয়ে প্যাসেজ + নোবেল-চিকিৎসা নিয়ে প্যাসেজ। **এই ডেটাসেটে বাংলাদেশ ব্যাংকের প্রতিটা ইংরেজি টপিকই ব্যাংকিং, প্রযুক্তি বা জাতীয় উন্নয়ন-ঘেঁষা।** |

---

## 🔁 পুনরাবৃত্ত লিখিত প্রশ্ন

`all-questions/written/`-এ সবচেয়ে শক্তিশালী হুবহু / প্রায়-হুবহু repeat, আসল শব্দে।

### প্রধান repeat: বাংলাদেশ ব্যাংকের একটা পুরো প্রশ্নপত্র পুনর্ব্যবহৃত

**`SO IT 25-07-2026` ট্যাগের ২২টা প্রশ্নের মধ্যে ২০টাই `Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024`-এর হুবহু প্রশ্ন।** যে সেটটা মিলে গেছে:

| BB SO(IT) ২০২৪ আইটেম | প্রশ্ন |
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
| 6.13 | Consider the following Java program and determine the integer value printed by main() — `static int x = 5; fun(n) { … x = x + 2; return fun(n-1) + x; }` — `fun(3)` প্রিন্ট। |
| 6.14 | An array contains one million sorted integers. Which searching algorithm would you choose? Justify. |
| 6.15 | Consider the grammar: E → E+E \| E*E \| id. Show that the grammar is ambiguous for the string id + id * id. |
| 5.1 | What is the full form of NPSB in the banking sector of Bangladesh? |
| 5.2 | Who is the architect of the National Martyrs' Memorial in Savar? |
| 5.3 | What is the name of the central bank of the United Kingdom? |
| 5.4 | Which international organization publishes the "World Economic Outlook" report? |
| 5.5 | What is the name of the first submarine communications cable system that Bangladesh is connected to? |

২০২৬-এর পরীক্ষায় মাত্র দুইটা প্রশ্ন নতুন: একটা e-commerce class diagram (`written/software-engineering.md`) আর *"Discuss the impact of Artificial Intelligence and Automation on the banking sector of Bangladesh"* (`written/computer-fundamental.md`)।

**অর্থ:** BB SO(IT) Grade-9 ২০২৪-এর প্রশ্নপত্রটা প্রথম থেকে শেষ পর্যন্ত সমাধান করুন। এটা বাংলাদেশ ব্যাংকের একটা IT লিখিত প্রশ্নপত্র, যার **২২-এর মধ্যে ২০টা** পরবর্তী একটা পরীক্ষায় ইতোমধ্যেই পুনর্ব্যবহৃত হয়েছে।

### অন্যান্য বেশি-বার আসা repeat

| কতবার | প্রশ্ন (হুবহু) | কোন কোন পরীক্ষা |
|---|---|---|
| **৬** | *"Write down the difference between Interpreter and Compiler?"* | MRA AME 2020 · BPSC Home Affairs Assistant DBA (ICT) 2022 · CAAB AP 2022 · PGCB Sub-AE (CSE) 30.09.2021 · Combined Bank Officer (IT) 03.01.2026 · BPSC Ministry of Agriculture AP 15.02.2022 |
| **৫** | *"What is the main difference between black box and white box testing?"* | BARC Programmer 04.08.2023 · BPSC AME (CSE) 2020 · MRA AME 2022 · Teletalk 2023 · SGFL 2021 |
| **৪** | *"Given IP address 192.168.1.50, Subnet Mask: 255.255.255.240. Find the valid IP range. Also find Network address and Broadcast address."* | NWPGCL Assistant Manager (ICT) 12.01.2024 · BTCL Assistant Manager (Technical) 2023 · BPDB AE (CSE) 10.05.2024 · BIWTA AE (CSE) 24.02.2023 |
| **৪** | *"Differentiate between IPv4 and IPv6."* | BMA Signal AE (Computer) 2021 · BPSC Security Services AME 15.12.2021 · BREB AGM (IT) 2021 · WZPGCL AE (CSE) 27.05.2023 |
| **৩** | *"Write the Difference among Network Switch, Hub and Router."* | BMA Signal AE (Computer) 2021 · BPSC AME (ICT) 2020 · DESCO Sub-AE 20.05.2023 |
| **৩** | *"What is SQL Injection? How to Prevent against SQL Injection Attacks?"* | RAKUB Programmer (PO) 12.10.2021 · RAKUB ME (PO) 05.10.2021 · Dhaka WASA AME (Network) 04.07.2025 |
| **৩** | *"Distinguish between TCP and UDP protocols."* | BPSC Security Services AP 13.12.2021 · BPSC Home Affairs Senior Computer Operator (ICT) 13.09.2022 · Combined Bank Officer (IT) 03.01.2026 |
| **৩** | *"What is the difference between supervised and unsupervised learning? Explain with examples."* | BPSC Security Services AP 13.12.2021 · SGFL 2021 · DPDC JAM 27.06.2025 |
| **৩** | *"Assume a TDMA based communication system having 8 transmission receiver pairs. Each source is sampled at 8 kHz … calculate the data rate of TDMA line."* | BDCCL AE (Network) 2022 · BTCL Assistant Manager (Technical) 2021 · WASA AP 25.11.2022 |
| **৩** | *"What is the port number used by DNS?"* | BARI AME 15.11.2025 · BBA AP 12.07.2025 · BCC AP 18.10.2025 |
| **২** | **Banker's Algorithm — ৫টি process, A(10) B(5) C(7)** | **Bangladesh Bank AD(ICT) 07.02.2025** · RAKUB ME (PO) 05.10.2021 |
| **২** | **LAN / ব্যাংক সার্ভারের জন্য firewall placement ডায়াগ্রাম** | **Bangladesh Bank AD(ICT) 07.02.2025** · **Bangladesh Bank AP 2019** |
| **২** | *"Show minimal function using K-Map: F(A,B,C,D) = Σ(2,8,9,11,13,15)"* | BPDB AE (CSE) 10.05.2024 · BICIC AP 2022 |
| **২** | *"Simplify F(A,B,C,D) = ACD + AB + D̄ + AC̄D using K-map and draw the logic circuits"* | BPSC Home Affairs Assistant DBA (CSE) 2022 · BPSC AP (CSE) 2019 |
| **২** | *"What is the difference between latch and flip-flop?"* | **Bangladesh Bank AME 2017** · SPCBL AME 20.11.2021 |
| **২** | *"What is MVC? Write down the MVC design pattern."* | Pubali Bank Ltd. SO (SD) 2018 · WZPGCL AE (CSE) 27.05.2023 |
| **২** | *"What are the differences between call by value and call by Reference?"* | BPSC Home Affairs Assistant DBA (CSE) 2022 · BPSC Ministry of Agriculture AP 15.02.2022 |
| **২** | *"Explain the message flow / How does DHCP work?"* | Pubali Bank Hardware Engineer 18.03.2023 · BREB AP (AP) 21.02.2025 |

আরও লক্ষ্য করুন **Bangladesh Bank Recruitment Test 2020**-এর প্রশ্নপত্রটা: **এর ১৯টা রেকর্ডের ১৫টাই `Sonali & Janata Bank Officer (IT) 2020 (ET: DU)`-তেও ট্যাগ করা** — অর্থাৎ এর পুরো IT অংশটাই একই পরীক্ষা গ্রহণকারী (DU) নেওয়া একটা Sonali & Janata পরীক্ষার সাথে অভিন্ন। শুধু চারটা সাধারণ-অংশের আইটেম (ইংরেজি প্যারাগ্রাফ + ইংরেজি অনুবাদ, বাংলা রচনা + বাংলা অনুবাদ) বাংলাদেশ ব্যাংকের একক। এটা দ্বিতীয় স্বাধীন প্রমাণ যে বাংলাদেশ ব্যাংকের লিখিত IT প্রশ্ন অন্য রাষ্ট্রায়ত্ত ব্যাংকগুলোর মতো একই DU-নির্মিত পুল থেকেই আসে।

---

## 🧩 বারবার ফিরে আসা কনসেপ্ট

**C1 — "schema দেওয়া হলো, normalization + key চাওয়া হলো।"** ২১টা normalization প্রশ্ন আর ৩৪টা key প্রশ্ন। AD(ICT) ২০২৫-এর রূপটা এটাকে ব্যাংক schema-র ভেতরে ঢুকিয়ে দিয়েছে। প্রত্যাশা করুন: 3NF/BCNF-এ ভাগ করা, প্রতিটা relation-এর PK বলা, FK বলা, আর যুক্তি দেওয়া।

**C2 — "network block দেওয়া হলো, চারটা সংখ্যা চাওয়া হলো।"** ১০৯টা subnetting প্রশ্নের সবই দাঁড়ায়: network address · subnet mask (CIDR + dotted decimal) · broadcast address · প্রথম/শেষ usable host · usable host সংখ্যা। VLSM (অসম ডিপার্টমেন্ট সাইজ) হলো কঠিন রূপ, যেটা BB ২০২৪-এ ব্যবহার করেছে।

**C3 — "process টেবিল দেওয়া হলো, Gantt chart আঁকো।"** দুইটা সাবটপিক মিলিয়ে ৩১টা CPU-scheduling প্রশ্ন। সবসময় FCFS + SJF (preemptive ও non-preemptive) + Priority + Round Robin, তারপর average waiting time আর average turnaround time।

**C4 — "সিকিউরিটি ডায়াগ্রাম আঁকো।"** Firewall/DMZ placement (**AD(ICT) ২০২৫ ও BB AP 2019**), firewall-সহ LAN, NAT topology (১৩টা প্রশ্ন), VPN site-to-site vs remote-access, timing diagram-সহ DHCP message flow। ব্যাংকের প্রশ্নকর্তারা *ছবি* চান, অনুচ্ছেদ নয়।

**C5 — "ডেটা-কমিউনিকেশনের হিসাব।"** Total latency (AD(ICT) ২০২৫), propagation vs transmission delay, Nyquist আর Shannon capacity (১৬টা প্রশ্ন), multiplexing guard band (**BB SO(IT) 2024**), TDMA/TDM frame-এর হিসাব (৩ পরীক্ষার repeat), optical-fibre power budget (১৩টা প্রশ্ন), throughput আর sliding-window efficiency।

**C6 — "X আর Y-এর তুলনা করো।"** লিখিত অংশে সবচেয়ে বেশি ব্যবহৃত ক্রিয়া: interpreter/compiler (৬ পরীক্ষা), black-box/white-box (৫), IPv4/IPv6 (৪), hub/switch/router (৩), TCP/UDP (৩), supervised/unsupervised (৩), latch/flip-flop (২, এর মধ্যে **BB AME 2017**), SRAM/DRAM, RAM/ROM, paging/segmentation, HDD/SSD, symmetric/asymmetric, overloading/overriding, process/thread, RISC/CISC, primary/foreign key, hashing/encryption (**BB SO(IT) 2024**), waterfall/agile। **এগুলো ৪–৬ সারির রেডিমেড টেবিল হিসেবে তৈরি রাখুন।**

**C7 — "প্রোগ্রামটা লেখো।"** `written/c-programming.md`-এ ১১১টা basic-program + ৩৮টা recursion + ৫৭টা output-tracing প্রশ্ন, সাথে `written/oop.md`-এ ১৮টা Java প্রশ্ন। বাংলাদেশ ব্যাংকের নিজের প্রশ্ন ছিল LCM (২০২৩), Fibonacci (২০১৬), array-র max (২০১৯), overtime বেতন ও recursive factorial (২০২০), আর একটা multi-threaded Overdraft Account class (২০১৯)।

**C8 — "ব্যাংক-দৃশ্যপটের মোড়ক।"** পুরো ডেটাসেটে যেসব ব্যাংক-নির্দিষ্ট মোড়ক ফিরে আসে: ATM testing (**BB AME 2019**), payment-gateway ঝুঁকি নিরীক্ষা (**BB AME 2023**), core-banking DB vs archive স্টোরেজ বাছাই (Combined Bank Officer (IT) 09.05.2026), ব্যাংকিং সফটওয়্যারের ফিচার তালিকা (**BB Recruitment Test 2020**), বহু-ডিপার্টমেন্ট অফিসের জন্য Active Directory (Combined Bank SO(IT) 17.05.2024), অনলাইন ব্যাংকিংয়ে MFA (Combined Bank Officer (IT) 09.05.2026), digital vs traditional banking (Combined Bank AME/Hardware 23.11.2023), ২৪×৭×৩৬৫ কার্যক্রমে 0-bit data loss (Combined Bank SO(IT) 13.10.2023)। **২০২৬-এর প্রশ্নপত্রেও প্রমিত theory বাংলাদেশ ব্যাংকের দৃশ্যপটে মোড়া থাকবে বলে ধরে নিন — AD(ICT) ২০২৫ তার ১১টা লিখিত প্রশ্নের ৪টাতেই ঠিক এটাই করেছে।**

---

## 🔮 সম্ভাব্য (Predicted) লিখিত প্রশ্ন

প্র্যাকটিসের জন্য নতুন লেখা প্রশ্ন। **এগুলোর কোনোটাই কোনো ঐতিহাসিক প্রশ্নপত্রে আসেনি।** প্রতিটাই ওপরে নথিবদ্ধ একটা প্যাটার্ন থেকে তৈরি।

**🔮 সম্ভাব্য W1 — Deadlock**
> *ভিত্তি:* AD(ICT) ২০২৫ প্রমিত ৫-process / A(10) B(5) C(7) snapshot-এ Banker's Algorithm দিয়েছিল, যেটা আগে RAKUB ME (PO) ২০২১-এও এসেছিল।
>
> একটি সিস্টেমে ৪টি process আর ৩টি resource type A(9), B(6), C(6)। Allocation = P0(2,1,1), P1(3,2,1), P2(1,1,2), P3(1,1,1); Max = P0(5,3,2), P1(6,3,3), P2(4,2,4), P3(3,2,2)।
> (ক) Need matrix তৈরি করুন। (খ) সিস্টেমটি safe state-এ আছে কি না নির্ণয় করে একটি safe sequence দিন। (গ) এখন P1 যদি (1,0,1) চায়, অনুরোধটি তাৎক্ষণিকভাবে মঞ্জুর করা যাবে কি? যুক্তি দিন।

**🔮 সম্ভাব্য W2 — ব্যাংকিং schema-র normalization**
> *ভিত্তি:* AD(ICT) ২০২৫ `Bank(Br_Name, Br_City, Assets, Acc_name, Acc_Num, Balance)` দিয়ে normalization + PK/FK চেয়েছিল।
>
> বিবেচনা করুন `Loan(Loan_No, Br_Name, Br_City, Assets, Cust_ID, Cust_Name, Cust_Address, Amount)`।
> (ক) functional dependency-গুলো চিহ্নিত করুন। (খ) 3NF-এ ভাগ করুন। (গ) প্রতিটি ফলাফল relation-এর primary key ও foreign key দেখান। (ঘ) কেন এই decomposition lossless, লিখুন।

**🔮 সম্ভাব্য W3 — Firewall / DMZ ডায়াগ্রাম**
> *ভিত্তি:* ঠিক এই আঁকার কাজটাই BB AP ২০১৯-এ আর আবার AD(ICT) ২০২৫-এ দেওয়া হয়েছিল।
>
> একটি ব্যাংক একটি ইন্টারনেট-ব্যাংকিং web server, একটি public DNS server, একটি mail server আর একটি অন্তর্বর্তী core-banking database চালায়। একটি external firewall, একটি DMZ আর একটি internal firewall নিয়ে নেটওয়ার্কটি আঁকুন। কোন সার্ভারগুলো DMZ-তে বসবে, প্রতিটি firewall কোন ট্রাফিক অনুমোদন করবে, এবং core-banking database কেন কখনো DMZ-তে রাখা যাবে না — ব্যাখ্যা করুন।

**🔮 সম্ভাব্য W4 — ডেটা-কমিউনিকেশন latency**
> *ভিত্তি:* AD(ICT) ২০২৫ ৩০০ কিমি দূরত্বে ১ Gbps-এ ৩-kbyte message-এর total latency, RTT ও queuing time সহ চেয়েছিল।
>
> ৬০০ কিমি দূরের দুই শাখার মধ্যে ১০০-Mbps লিংকে একটি ৫-Mbyte ফাইল স্থানান্তর হচ্ছে। Propagation speed ২×১০⁸ মি/সে, queuing delay ১০ ms, processing delay নগণ্য। transmission delay, propagation delay আর total latency নির্ণয় করুন, এবং কোন term প্রধান ভূমিকা রাখছে ও কেন তা লিখুন।

**🔮 সম্ভাব্য W5 — ইমেইল আর্কিটেকচার**
> *ভিত্তি:* AD(ICT) ২০২৫ প্রোটোকল আর ধাপে ধাপে mail-এর পথ (Sinthia → Afsana) চেয়েছিল।
>
> `branch.bank.gov.bd`-এর একজন কর্মী `customer@example.com`-এ একটি mail পাঠাচ্ছেন। (ক) compose থেকে retrieval পর্যন্ত জড়িত প্রতিটি প্রোটোকল, তার layer আর port সহ তালিকা করুন। (খ) MUA/MTA/MDA পথ আর যে DNS query এটাকে সম্ভব করে, তা আঁকুন। (গ) প্রাপক POP3-র বদলে IMAP ব্যবহার করলে কী বদলাবে, ব্যাখ্যা করুন।

**🔮 সম্ভাব্য W6 — Subnetting / VLSM**
> *ভিত্তি:* BB SO(IT) ২০২৪ একটা /24 থেকে দুই-subnet-এর ক্রমিক বরাদ্দ চেয়েছিল; টপিকটায় ১০৯টা লিখিত প্রশ্ন আছে।
>
> একটি ব্যাংক শাখা `172.20.16.0/22` পেয়েছে। এটাকে সেবা দিতে হবে Core Banking (৫০০ host), ATM network (১২০ host), CCTV (৬০ host) আর Staff Wi-Fi (২৫ host)। VLSM ব্যবহার করে বড় থেকে ছোট ক্রমে বরাদ্দ দিয়ে প্রতিটির জন্য দিন: CIDR mask-সহ network address, dotted decimal-এ subnet mask, প্রথম ও শেষ usable host, এবং broadcast address।

**🔮 সম্ভাব্য W7 — CPU scheduling**
> *ভিত্তি:* ৩১টা লিখিত CPU-scheduling প্রশ্ন; পাঁচ-process priority টেবিলটা সমগোত্রীয় BPSC AD(ICT) ২০২৫ পদে এসেছে।
>
> P1–P5 process সময় ০-তে আসে, burst time ৮, ২, ৭, ৩, ৫ আর priority ৩, ১, ৪, ২, ৫ (ছোট সংখ্যা = বেশি priority)।
> (ক) FCFS, SJF (non-preemptive), Priority (non-preemptive) আর Round Robin (quantum = ৩) — প্রত্যেকটির Gantt chart আঁকুন।
> (খ) প্রত্যেকটির average waiting time আর average turnaround time নির্ণয় করুন। (গ) কোন অ্যালগরিদমে starvation-এর ঝুঁকি আছে এবং কেন?

**🔮 সম্ভাব্য W8 — Cache**
> *ভিত্তি:* বাংলাদেশ ব্যাংক ২০২৩-এ direct-mapped cache-এর field size, ২০১৭-তে average access time আর ২০২৪-এ miss-এর শ্রেণিবিভাগ চেয়েছে।
>
> একটি processor ৩২-bit address আর ৮-word (৩২-byte) block-সহ ৩২ KB-র direct-mapped cache ব্যবহার করে। (ক) block সংখ্যা এবং offset, index ও tag field-এর প্রস্থ নির্ণয় করুন। (খ) hit time ২ ns, miss penalty ৮০ ns আর hit rate ৯৫% হলে average memory access time বের করুন। (গ) কোনো block-এ একেবারে প্রথম reference-এর miss আর working set cache-এর ধারণক্ষমতা ছাড়িয়ে যাওয়ায় হওয়া miss — দুটোকে শ্রেণিবদ্ধ করুন।

**🔮 সম্ভাব্য W9 — SQL**
> *ভিত্তি:* BB SO(IT) ২০২৪-এর aggregation query ২০২৬-এ হুবহু পুনর্ব্যবহৃত হয়েছে; ডিপার্টমেন্টভিত্তিক aggregation পুরো ভাণ্ডারে সবচেয়ে বেশি পুনরাবৃত্ত SQL আকার।
>
> `Account(Acc_No, Br_Name, Balance)` আর `Branch(Br_Name, Br_City, Assets)` দেওয়া আছে:
> (ক) প্রতিটি শাখা-শহরের মোট আমানত আর অ্যাকাউন্ট সংখ্যা দেখান। (খ) যেসব শাখার average balance সব শাখার সামগ্রিক average balance-এর চেয়ে বেশি, তাদের তালিকা দিন। (গ) `LIMIT`/`TOP` ব্যবহার না করে দ্বিতীয় সর্বোচ্চ balance বের করার query লিখুন।

**🔮 সম্ভাব্য W10 — সিকিউরিটি কনসেপ্ট**
> *ভিত্তি:* BB SO(IT) ২০২৪ hashing vs encryption চেয়েছিল; BB AP ২০২৩ CIA-থেকে-আক্রমণের ম্যাপিং চেয়েছিল; AD(ICT) ২০২৫-এর ইংরেজি টপিক ছিল ব্যাংকিং সাইবার-আক্রমণে AI।
>
> (ক) hashing, symmetric encryption আর asymmetric encryption-এর কার্যকরী পার্থক্য ব্যাখ্যা করুন, প্রত্যেকটির জন্য একটি ব্যাংকিং ব্যবহার-ক্ষেত্র দিয়ে। (খ) একজন গ্রাহক নিজে অনুমোদন করা একটি লেনদেন অস্বীকার করছেন। কোন security service এটা প্রতিরোধ করে, আর কোন cryptographic mechanism সেটা দেয়? (গ) Confidentiality, Integrity আর Availability — প্রত্যেকটি প্রধানত ভঙ্গ করে এমন একটি করে আক্রমণের নাম দিন।

---

## 🏆 চূড়ান্ত লিখিত র‍্যাঙ্কিং

| ক্রম | টপিক | কেন এই অবস্থানে |
|---|---|---|
| ১ | **Banker's Algorithm + deadlock-এর শর্ত** | AD(ICT) ২০২৫-এর ১ম প্রশ্ন; একই instance ইতোমধ্যেই একবার repeat হয়েছে (RAKUB ২০২১); ২৩টা লিখিত প্রশ্ন |
| ২ | **ব্যাংক schema-র normalization + PK/FK নির্ণয়** | AD(ICT) ২০২৫-এর প্রশ্ন; ২১টা normalization + ৩৪টা key প্রশ্ন |
| ৩ | **ব্যাংক সার্ভারের জন্য firewall / DMZ ডায়াগ্রাম** | বাংলাদেশ ব্যাংক দুইবার জিজ্ঞেস করেছে (AP ২০১৯, AD(ICT) ২০২৫); ২০টা firewall প্রশ্ন |
| ৪ | **Subnetting ও VLSM** | ১০৯টা প্রশ্ন — ভাণ্ডারের সবচেয়ে ঘন টপিক; BB SO(IT) ২০২৪-এর রূপটা ২০২৬-এ হুবহু পুনর্ব্যবহৃত |
| ৫ | **SQL: GROUP BY aggregation, join, গড়ের বেশি, n-তম সর্বোচ্চ** | ৮৭টা প্রশ্ন; বাংলাদেশ ব্যাংক ৪টি আলাদা পরীক্ষায় SQL জিজ্ঞেস করেছে; BB SO(IT) ২০২৪-এর query হুবহু পুনর্ব্যবহৃত |
| ৬ | **CPU scheduling-এর Gantt chart (FCFS/SJF/Priority/RR)** | ৩১টা লিখিত প্রশ্ন; সমগোত্রীয় BPSC AD(ICT) পদে এসেছে |
| ৭ | **ডেটা-কমিউনিকেশনের হিসাব (latency, Nyquist, Shannon, multiplexing)** | AD(ICT) ২০২৫-এর প্রশ্ন; BB SO(IT) ২০২৪-এর guard-band প্রশ্ন; তিনটা সাবটপিকে ১৬ + ১৮ + ১৪টা প্রশ্ন |
| ৮ | **ইমেইল আর্কিটেকচার: SMTP/POP3/IMAP-এর পথ ও প্রোটোকল** | AD(ICT) ২০২৫-এর প্রশ্ন; BB AME ২০১৭; ১০টা প্রশ্ন |
| ৯ | **K-map সরলীকরণ + Boolean expression থেকে truth table** | AD(ICT) ২০২৫-এর truth table; BB SO(IT) ২০২৪-এর K-map (২০২৬-এ পুনর্ব্যবহৃত); ১৯ + ৩৩টা প্রশ্ন |
| ১০ | **Cache memory (miss-এর ধরন, direct-mapped field, average access time)** | বাংলাদেশ ব্যাংক তিনটি আলাদা পরীক্ষায় (২০১৭, ২০২৩, ২০২৪) cache জিজ্ঞেস করেছে |
| ১১ | **Heap নির্মাণ / heapify / heapsort** | AD(ICT) ২০২৫-এর min-heap প্রশ্ন; দুইটা ফাইলে মোট ১০টা প্রশ্ন |
| ১২ | **OOP: polymorphism, overloading vs overriding, কোডসহ inheritance** | বাংলাদেশ ব্যাংক চারটি আলাদা পরীক্ষায় OOP জিজ্ঞেস করেছে; ৫৪ প্রশ্নের সাবটপিক |
| ১৩ | **Software testing (unit vs integration, black-box vs white-box, V&V)** | BB SO(IT) ২০২৪ + BB AME ২০২৩ + BB AME ২০১৯ + BB ২০২০; ৪০ প্রশ্নের সাবটপিক; ৫ পরীক্ষার repeat |
| ১৪ | **Cryptography: hashing vs encryption, symmetric vs asymmetric, digital signature, CIA** | BB SO(IT) ২০২৪ + BB AP ২০২৩; ৩১ + ৮টা প্রশ্ন |
| ১৫ | **Pipelining আর hazard** | বাংলাদেশ ব্যাংক তিনটি আলাদা পরীক্ষায় (২০১১, ২০১৯, ২০২৪) জিজ্ঞেস করেছে |
| ১৬ | **Linux command** | ৪৭টা প্রশ্ন — OS-র বৃহত্তম সাবটপিক; ব্যাংকের লিখিত পরীক্ষায় প্রমিত অংশ, পুরোটাই নিশ্চিত নম্বর |
| ১৭ | **প্রোটোকল ও device-সহ OSI/TCP-IP layer** | ৫২টা প্রশ্ন; BB AP ২০২৩ আর BB AP ২০১৯ দুটোতেই ব্যবহৃত |
| ১৮ | **Sorting: trace + complexity টেবিল; BFS/DFS; Kruskal MST** | ৩৬ + ১৭ + ১৫টা প্রশ্ন; BB Recruitment Test ২০২০ insertion sort চেয়েছিল |
| ১৯ | **SDLC / Agile vs Waterfall + UML class ও use-case diagram** | ৪৫ + ১৪টা প্রশ্ন; BB AP ২০২৩ একটা class diagram চেয়েছিল |
| ২০ | **গণিত (probability, integration, set theory) আর ইংরেজি (ব্যাংকিং focus writing + বাংলা→ইংরেজি)** | লিখিত ২০০ নম্বরের ৫০ নম্বর; AD(ICT) ২০২৫ ২টা গণিত + ২টা ইংরেজি প্রশ্ন দিয়েছিল |

---

## 🚨 শেষ মুহূর্তের লিখিত সাজেশন

প্রস্তুতির সময় প্রায় শেষ হয়ে এলে এই ২০টাই সময়প্রতি সবচেয়ে বেশি নম্বর দেবে। প্রতিটাই একটা আসল ঐতিহাসিক প্রশ্নের সাথে বাঁধা।

১. **Banker's Algorithm** — Need matrix বানান, safety algorithm চালান, safe sequence লিখুন। প্রমিত ৫-process / A(10) B(5) C(7) snapshot প্র্যাকটিস করুন। *(AD(ICT) ২০২৫ + RAKUB ২০২১)*
২. **Deadlock-এর চারটি শর্ত** — mutual exclusion, hold-and-wait, no preemption, circular wait; সাথে prevention vs avoidance vs detection। *(২৩টা প্রশ্ন)*
৩. **ব্যাংক schema 3NF-এ normalize** করে প্রতিটা relation-এ PK/FK দেখান, তারপর যুক্তি দিন। *(AD(ICT) ২০২৫)*
৪. **1NF → 2NF → 3NF → BCNF ম্যাপিং**: repeating group → partial dependency → transitive dependency → প্রতিটা determinant candidate key। *(২১টা প্রশ্ন)*
৫. **Firewall/DMZ ডায়াগ্রাম** — ব্যাংকের Mail + DNS + Web server, আর দ্বিতীয় firewall-এর পেছনে internal LAN। *(AD(ICT) ২০২৫ + BB AP ২০১৯)*
৬. **Subnetting ড্রিল**: ব্লক আর host-এর চাহিদা দেওয়া হলে network address, mask (CIDR + dotted), প্রথম/শেষ usable host, broadcast আর host সংখ্যা বের করুন। তারপর VLSM রূপটা বড় থেকে ছোট ক্রমে করুন। *(১০৯টা প্রশ্ন)*
৭. **SQL aggregation সেট**: `COUNT`+`AVG` নিয়ে `GROUP BY`; সামগ্রিক গড়ের ওপরে `HAVING`; চার ধরনের JOIN; দ্বিতীয় সর্বোচ্চ বেতন। *(৮৭টা প্রশ্ন; BB SO(IT) ২০২৪-এর প্রশ্নটা ২০২৬-এ হুবহু পুনর্ব্যবহৃত)*
৮. **CPU scheduling**: একটা process টেবিল থেকে FCFS, SJF, Priority আর RR-এর Gantt chart + AWT + ATAT। *(৩১টা প্রশ্ন)*
৯. **Total latency সূত্র**: propagation (d/s) + transmission (L/B) + queuing + processing; তারপর Nyquist `C = 2B log₂L` আর Shannon `C = B log₂(1+SNR)`। *(AD(ICT) ২০২৫ + ১৬টা capacity প্রশ্ন)*
১০. **Multiplexing guard band**: n × channel bandwidth + (n−1) × guard band। *(BB SO(IT) ২০২৪, ২০২৬-এ পুনর্ব্যবহৃত)*
১১. **ইমেইলের পথ**: SMTP (25/587) পাঠানো, POP3 (110) / IMAP (143) সংগ্রহ, DNS MX lookup, transport-এ TCP — সাথে MUA→MTA→MDA ডায়াগ্রাম। *(AD(ICT) ২০২৫)*
১২. **Boolean expression থেকে truth table** আর **৪-variable K-map থেকে minimal SOP**, loop এঁকে দেখানো। *(AD(ICT) ২০২৫ + BB SO(IT) ২০২৪)*
১৩. **NAND/NOR-এর universality** — শুধু NAND দিয়ে AND, OR, NOT, XOR বানান; আর দুইটা half adder দিয়ে full adder। *(৩৩ + ২৩টা প্রশ্ন; BB AME ২০১১ ও ২০১৯)*
১৪. **Min-heap / max-heap নির্মাণ** মানের তালিকা থেকে, সাথে delete-এর পর heapify। *(AD(ICT) ২০২৫)*
১৫. **Cache**: compulsory vs capacity vs conflict miss; direct-mapped-এ tag/index/offset ভাগ; average access time = hit-time + miss-rate × miss-penalty। *(BB ২০১৭, ২০২৩, ২০২৪)*
১৬. **যে তুলনা টেবিলগুলো মুখস্থ লিখতে পারতে হবে**: interpreter/compiler · black-box/white-box · TCP/UDP · IPv4/IPv6 · hub/switch/router · SRAM/DRAM · paging/segmentation · overloading/overriding · process/thread · hashing/encryption · symmetric/asymmetric · RAID 1/RAID 5 · VM/container। *(প্রত্যেকটি ২–৬ পরীক্ষায়)*
১৭. **Polymorphism + overloading vs overriding**, ছোট একটা Java/C++ উদাহরণসহ। *(বাংলাদেশ ব্যাংক ৪ পরীক্ষায় OOP জিজ্ঞেস করেছে)*
১৮. **Linux one-liner**: `ls -la`, `chmod 755` / `chmod -R a+x`, `grep`, `head -n` / `tail -f`, `df -h`, `free -m`, `top`, `rm -r`, `cp -r`, `ifconfig`/`ip a`, `ping`, `traceroute`, `crontab`। *(৪৭টা প্রশ্ন)*
১৯. **সিকিউরিটির সংক্ষিপ্ত উত্তর**: CIA triad-কে আক্রমণের সাথে মেলানো · digital signature = প্রেরকের private key দিয়ে sign, প্রেরকের public key দিয়ে verify · SQL injection প্রতিরোধ (parameterised query + input validation) · 2FA · DoS vs DDoS vs MITM vs phishing। *(৩১ + ৩২ + ১৯ + ১৬টা প্রশ্ন)*
২০. **ইংরেজি + গণিত**: একটা ১৫০ শব্দের ব্যাংকিং/প্রযুক্তি focus write-up (ব্যাংকিংয়ে AI, cashless economy, ব্যাংকে সাইবার সিকিউরিটি — তিনটাই বাংলাদেশ ব্যাংকের ঐতিহাসিক টপিক) · দুইটা ব্যাংকিং বাক্যের বাংলা→ইংরেজি · একটা probability সমস্যা · একটা definite integral। *(AD(ICT) ২০২৫ ঠিক এই মিশ্রণটাই দিয়েছিল; ২০০-র মধ্যে ৫০ নম্বর)*

---

### যাচাইকরণ নোট

ওপরে উদ্ধৃত সবকিছু `all-questions/written/` অথবা `all-questions/mcq/`-এর ভেতরের কোনো ট্যাগ পর্যন্ত ট্রেস করা যায়। এই ডকুমেন্টের কোনো পরীক্ষার নাম, সাল, পদ, সংখ্যা বা পুনরাবৃত্তির হিসাব অনুমান করে লেখা হয়নি। সম্ভাব্য প্রশ্নগুলো শুধুমাত্র **🔮 সম্ভাব্য (Predicted) লিখিত প্রশ্ন** সেকশনে সীমাবদ্ধ এবং আলাদাভাবে চিহ্নিত।
