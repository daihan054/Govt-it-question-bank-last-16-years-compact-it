# কম্বাইন্ড ব্যাংক অ্যাসিস্ট্যান্ট মেইনটেন্যান্স ইঞ্জিনিয়ার ২০২৬ — লিখিত সাজেশন

**ভিত্তি:** [`all-questions/`](../../all-questions/)-এর ৫০টি `.md` ফাইল সম্পূর্ণ পড়া হয়েছে — ৫,৯১০টি প্রশ্ন, ৩৫০টি আলাদা পরীক্ষা, ২০১১–২০২৬। লিখিত অংশে ৩,১৬৮টি প্রশ্ন। এই পদের ঘরানার **১১৯টি লিখিত রেকর্ড**।

**মূল রেফারেন্স প্রশ্নপত্র — সবগুলো সম্পূর্ণ পড়া:**

| পরীক্ষা | লিখিত প্রশ্ন |
|---|---|
| `Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024` | ১৮ |
| `RAKUB Maintenance Engineer (PO) 05.10.2021` | ১৮ |
| `SPCBL Assistant Maintenance Engineer 20.11.2021` | ১৫ |
| `Bangladesh Bank Assistant Maintenance Engineer 04.02.2023` | ১৪ |
| `Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023` | ১৪ |
| `Combined 5 Banks Assistant Maintenance Engineer 2019` | ৯ |
| `Bangladesh Bank AME 2016 / 2017 / 2019` | ৬ + ৬ + ৬ |
| `Bangladesh Bank Assistant Maintenance Engineer 2011` | ৪ |

## এই পদের চরিত্র — সরাসরি গোনা

১১৯টি লিখিত হিটের বিন্যাস: **computer-networks ১৭ · microprocessor ১৩ · computer-fundamental ১২ · math ১১ · security ১০ · dld ৯ · operating-system ৮ · database ৭ · english ৬ · software-engineering ৬**।

তিনটা জিনিস এই পদকে আলাদা করে:

1. **হার্ডওয়্যার ও ডেটা সেন্টার** — computer-fundamental ১২ হিট; ডেটা সেন্টারের কুলিং, জেনারেটর, TIER, সার্ভার — অন্য পদে এত নেই।
2. **লিখিততে গণিত ১১ হিট** — `AME/AE(IT) 24.02.2024`-এ **৪টি** আর `AME/Hardware Engineer 23.11.2023`-এ **৩টি** গাণিতিক প্রশ্ন। বাদ দেওয়া যাবে না।
3. **ডিজিটাল লজিক ও মাইক্রোপ্রসেসর** — dld ৯ + microprocessor ১৩ = ২২, অর্থাৎ প্রতি ৫টির ১টি।

### স্টারের অর্থ

| স্টার | মানে |
|---|---|
| ★★★★★ | কম্বাইন্ড ব্যাংক AME-র পত্রে সরাসরি এসেছে, বা বাংলাদেশ ব্যাংক AME-র একাধিক পত্রে |
| ★★★★ | এই ঘরানার কোনো পত্রে এসেছে, অথবা সাবটপিকটা খুব বড় |
| ★★★ | ব্যাংক সেক্টরে নিয়মিত আসে |
| ★★ | আছে, কিন্তু ঘনত্ব কম |
| ★ | বিরল — সময় থাকলে দেখবেন |

`AME'24` = Combined Bank AME/Assistant Engineer (IT) 24.02.2024 · `AHE'23` = Combined Bank AME/Assistant Hardware Engineer 23.11.2023 · `BB AME'23` = Bangladesh Bank AME 04.02.2023 · `5B'19` = Combined 5 Banks AME 2019 · `(১০৯)` = ঐ সাবটপিকে মোট প্রশ্ন

---

## Important topic

| Topic | ★ | Subtopic | ★ | প্রমাণ |
|---|---|---|---|---|
| **Computer Networks** | ★★★★★ | Multiplexing & Bandwidth — **বিভিন্ন প্রকার multiplexing; TDM/FDM/WDM** | ★★★★★ | **AHE'23** · **AME'24** · ×৩ · (১৮) |
| | | Error Detection & Data Communication — **তুলনামূলক টেবিল আকারে পরিভাষা; CRC; throughput** | ★★★★★ | **AME'24** · **BB AME'23** · ×২ · (১৪) |
| | | OSI & TCP/IP Reference Model — **TCP/IP layer, প্রতিটির কাজ, protocol, device ও software — টেবিল আকারে** | ★★★★★ | **AME'24** · ×২ · (৫২) |
| | | Data Rate & Channel Capacity — Nyquist ও Shannon সূত্র, SNR | ★★★★★ | **BB AME'23-এ ২টি** · ×২ · (১৬) |
| | | Subnetting & IP Addressing — network/broadcast/mask/usable range | ★★★★★ | **BB AME'17** · ×২ · **(১০৯) ভাণ্ডারের সর্ববৃহৎ** |
| | | Networking Fundamentals & Terminology — bandwidth, latency, MAC বনাম IP | ★★★★ | **BB AME'19** · ×২ · (৩২) |
| | | Email Architecture & Protocols (SMTP, POP3, IMAP) | ★★★★ | **BB AME'17** · (১০) |
| | | Application Layer (DNS, DHCP, HTTPS) — troubleshooting | ★★★★ | **BB AME'17** · (২২) |
| | | Physical Layer & Transmission Media · Networking Devices · Topologies · Flow Control | ★★★ | (১৫)+(১৯)+(১৪)+(১২) |
| | | Transport Layer · Routing Protocols · IPv6 · NAT · Optical Fiber · Wireless & IoT | ★★★ | (১৭)+(১৮)+(১৩)+(১৩)+(১৩)+(১৯) |
| **Microprocessor & Architecture** | ★★★★★ | Microprocessor Architecture & Functions — **8086 বনাম 8088, flag register, bus, ALU/CU; ৩২ bit বনাম ৬৪ bit** | ★★★★★ | **BB AME'11** · ×৪ · **(৩৫) সর্ববৃহৎ** |
| | | Instruction Pipelining & Hazards — **multiprocessor বনাম multicomputer; shared memory; pipeline কেন ভালো** | ★★★★★ | **AME'24** · **BB SO'24** · **BB AME'19** · **BB AME'11** · ×৩ · (৯) |
| | | Memory Hierarchy & Storage — **memory organization; SRAM বনাম DRAM** | ★★★★★ | **AHE'23** · (২৬) |
| | | RAID Architecture & Storage — **RAID কী, ডেটা সেন্টারের সার্ভারে কেন জরুরি** | ★★★★★ | **AHE'23** · ×২ · (১৫) |
| | | Cache Memory — miss-এর ধরন, direct-mapped field, average access time | ★★★★★ | **BB ৩ পরীক্ষায়: SO'24, AME'23, AME'17** · ×২ · (১৪) |
| | | Assembly Language & Addressing Modes — 8086-এর addressing mode | ★★★★★ | **BB AME'17** · **BB AME'11** · (৮) |
| | | Secondary Storage (HDD বনাম SSD) · CPU Performance · RISC বনাম CISC · Multi-core | ★★★ | (১০)+(৬)+(৪)+(৫) |
| **Computer Fundamental** | ★★★★★ | Data Center Infrastructure & Power Management — **কুলিং সিস্টেমে DC জেনারেটর; ব্যাংকের ডেটা সেন্টারের গুরুত্বপূর্ণ উপাদান; energy efficiency** | ★★★★★ | **AME'24** · **AHE'23** · **BB AME'23** · ×৩ · (১০) |
| | | Computer Fundamentals & Acronyms — পূর্ণরূপ | ★★★★★ | **BB AME'16-এ ২টি** · **BB AME'11** · ×৩ · **(৫৯) সর্ববৃহৎ** |
| | | ICT in Society & Governance — **অনলাইন ব্যাংকিংয়ে ICT-র ১০টি উদ্ভাবনী প্রয়োগ** | ★★★★★ | **AME'24** · ×২ · (২৪) |
| | | Hardware Components & BIOS — booting, CMOS, UEFI | ★★★★★ | **BB AME'16-এ ২টি** · ×২ · (২৪) |
| | | Digital Banking & Financial Inclusion — **ডিজিটাল ব্যাংকিং বনাম প্রচলিত ব্যাংকিং** | ★★★★★ | **AHE'23** · (২) |
| | | Software Types & Classification · Server Hardware · Blockchain · Quantum Computing | ★★★ | (১৭)+(৫)+(৮)+(৩) |
| **গণিত** | ★★★★★ | Geometry & Coordinate Geometry — **আয়তক্ষেত্রের ভেতরের চতুর্ভুজের ক্ষেত্রফল; সমকোণী প্লটের ক্ষেত্রফল** | ★★★★★ | **AME'24** · **AHE'23** · ×৩ · (১০) |
| | | Ratio, Proportion & Mixtures — **তিন পাত্রে দুধ-পানি (১:২, ২:৩, ৩:৪) মেশালে অনুপাত; ছেলে-মেয়ের অনুপাত** | ★★★★★ | **AME'24-এ ২টি** · ×২ · (৪) |
| | | Speed, Time, Distance & Boats — **স্রোতের গতিবেগ (১৫ কিমি উজান, ২২ কিমি ভাটি, ৫ ঘণ্টা); উড়োজাহাজের গতি** | ★★★★★ | **AME'24** · **AHE'23** · ×২ · (৪) |
| | | Arithmetic & Algebra Problems — **নোটবুকের দাম ৫ টাকা বাড়লে ১০টি কম** ধাঁচ | ★★★★★ | **AHE'23** · **BB AME'23** · ×২ · (১৬) |
| | | Percentage, Profit & Loss, সুদ | ★★★★★ | **BB AME'23-এ ২টি** · ×২ · (১২) |
| | | Set Theory · Probability · Permutation & Combination | ★★★ | (১৩)+(৪)+(৬) |
| **Computer / Network Security** | ★★★★★ | Web Security Vulnerabilities — **ব্যাংকের e-banking ওয়েব সার্ভার ডেটা সেন্টারে কনফিগার ও সুরক্ষিত করার ধাপ** | ★★★★★ | **AME'24** · **BB AME'17** · **×৫ — এই পদের সর্বোচ্চ security হিট** · (১৯) |
| | | Social Engineering & Cyber Attacks — **encryption/decryption; top 10 cyber attack** | ★★★★★ | **AHE'23** · **(৩২) সর্ববৃহৎ** |
| | | Firewalls & Network Defense — **ফায়ারওয়ালের প্রকার; NGFW বনাম প্রচলিত ফায়ারওয়াল** | ★★★★★ | **AME'24** · (২০) |
| | | Authentication & Access Control — **OTP ভিত্তিক অনলাইন ব্যাংকিং প্রক্রিয়া** | ★★★★★ | **AME'24** · (১৬) |
| | | Security Protocols (SSL/TLS, HTTPS) | ★★★★ | **BB AME'19** · (১২) |
| | | Malware · Cryptography · Cyber Crime · CIA Triad · VPN | ★★★ | (২০)+(৩১)+(১০)+(৮)+(৬) |
| **DLD** | ★★★★★ | Logic Gates & Universal Gates — **Boolean expression-এর লজিক সার্কিট আঁকা ও নির্দিষ্ট ইনপুটে আউটপুট নির্ণয়** | ★★★★★ | **AME'24** (Q = ĀB̄ + BC·(B+C)‾) · **BB AME'19** · **BB AME'11** · ×৪ · **(৩৩) সর্ববৃহৎ** |
| | | Logic Families (TTL বনাম CMOS) — **ডিজিটাল IC-র গুরুত্বপূর্ণ বৈশিষ্ট্য**, fan-in/fan-out | ★★★★★ | **AHE'23** · ×২ · (৬) |
| | | Sequential Circuits (Latches & Flip-Flops) — latch বনাম flip-flop | ★★★★★ | **BB AME'17** · ×২ · (১৭) |
| | | Number Systems & Base Conversions · Boolean Algebra · K-Map · Combinational Circuits | ★★★★ | (২৬)+(১৯)+(১৯)+(২৩) |
| **Operating System** | ★★★★ | OS Concepts & System Software — **socket, kernel, process, program, multiprogramming, context switching; preemptive priority scheduling** | ★★★★★ | **AME'24** · **BB AME'19** · ×৩ · (২৪) |
| | | Virtual Memory & Page Replacement — **physical বনাম virtual memory, সুবিধা-অসুবিধা** | ★★★★★ | **AHE'23** · (১৬) |
| | | CPU Scheduling Algorithms — Gantt, AWT, ATAT, turnaround time | ★★★★★ | **BB AME'11** · ×২ · (২৫) |
| | | File Systems & Disk Management — I/O utilization, inode | ★★★★ | **BB AME'11** · (৭) |
| | | Linux / Unix Commands · Deadlock · Memory Management · Concurrency | ★★★ | (৪৭)+(২৩)+(১৬)+(১১) |
| **Database** | ★★★★ | SQL Queries — **শীর্ষ ১০% GPA-ধারী বের করার query; ডেটাবেজ ডিজাইন** | ★★★★★ | **5B'19** · ×২ · **(৮৭) সর্ববৃহৎ** |
| | | Data Warehousing, Data Mining & BI — **data mining-এর ধাপগুলো** | ★★★★★ | **5B'19** · (৯) |
| | | Database Backup & Disaster Recovery · Normalization · Keys · Transaction & ACID | ★★★ | (৮)+(২১)+(৩৪)+(১৪) |
| **Software Engineering** | ★★★★ | Software Testing & Evaluation — **সর্টিং অ্যালগরিদম টেস্ট করার কোড; বিতরণকৃত সিস্টেমে ATM কীভাবে টেস্ট করবেন** | ★★★★★ | **5B'19-এ ২টি** · **BB AME'19** (ATM testing ১০ ধাপ) · **BB AME'23** · ×৪ · (৪০) |
| | | IT Governance, Audit & Risk Management — **policy/guideline/procedure-এর পার্থক্য; অডিটর কেন নিয়ন্ত্রণকে সিস্টেম হিসেবে দেখবে; পেমেন্ট গেটওয়ে অডিট** | ★★★★★ | **AME'24** · **BB AME'23** · ×২ · (৪) |
| | | SDLC Phases & Models · UML · Requirements Engineering · Cost Estimation | ★★★ | (৪৫)+(১৪)+(১০)+(৪) |
| **Electrical & Electronics** | ★★★★ | Electrical Circuits & Protection Devices — **ব্যাটারি বনাম ক্যাপাসিটর; fuse/MCB/relay** | ★★★★★ | **BB AME'17** · ×২ · (১৩) |
| | | Transistors (BJT & FET) — cut-off/saturation/active region | ★★★★★ | **BB AME'23** · (৯) |
| | | Electrical Machines — অল্টারনেটর, ইন্ডাকশন মোটর, slip | ★★★★★ | **BB AME'19** · (১) |
| | | Semiconductor & Diodes · DAC/ADC · Op-amp · AC Power | ★★★ | (৪)+(৩)+(২)+(২) |
| **Web Technology** | ★★★ | JavaScript & jQuery — **HTML DOM দিয়ে element-এর মান বদলানো; `$.ajax()` বনাম `$.get()` বনাম `$.load()`** | ★★★★★ | **5B'19-এ ২টি** · ×২ · (১৬) |
| | | HTML & Web Fundamentals — **HTML5-এর `<header>`, `<footer>`, `<section>`, `<article>`** | ★★★★★ | **5B'19** · (৩০) |
| | | Full Stack & Backend · HTTP Protocol · REST বনাম SOAP · CSS | ★★★ | (৭)+(১০)+(৮)+(৪) |
| **Cloud Computing** | ★★★ | Cloud Service Models — IaaS/PaaS/SaaS | ★★★★★ | **BB AME'23-এ ২টি** · (১৩) |
| | | Virtualization & Containers — VM বনাম container, hypervisor | ★★★★★ | **BB AME'23** · (৮) |
| | | Cloud Fundamentals · Edge Computing · Cloud Security | ★★★ | (৬)+ প্রত্যেকটি (১)–(৪) |
| **Programming Languages** | ★★★ | .NET Framework — **.NET Framework কী, এর বিভিন্ন component** | ★★★★★ | **5B'19** · (৬) |
| **C Programming** | ★★★ | Output Tracing & Control Flow — **প্রদত্ত কোডের ভুল খুঁজে বের করা** | ★★★★ | **5B'19** · (৫৭) |
| | | Basic Programs & Control Statements · Recursion & Functions · Flowcharts | ★★★ | (১১১)+(৩৮)+(১৬) |
| **Data Structure / Algorithm** | ★★ | Sorting Algorithms & Complexity · Tree · Stack · Linked List | ★★★ | (৩৬)+(২৭)+(২০)+(১৫) |
| **AI & ML** | ★★ | ML Paradigms · Generative AI | ★★★ | (৬)+(৪) |
| **OOP** | ★★ | OOP Concepts (Inheritance & Polymorphism) · Java Programming | ★★★ | (৫৪)+(১৮) |

### General section — বাংলা ও ইংরেজি

| Topic | ★ | Subtopic | ★ | প্রমাণ |
|---|---|---|---|---|
| **ইংরেজি** | ★★★★★ | Focus Writing — **পরিবেশ, প্রযুক্তি, জাতীয় প্রকল্প** ঘরানা | ★★★★★ | **AME'24** ("Impacts of air pollution on human health", ১৫০ শব্দ) · **AHE'23** ("Metro Rail Equal Opportunity") · ×৩ · **(৩৭) সর্ববৃহৎ** |
| | | Translation (বাংলা → ইংরেজি) | ★★★★★ | **AME'24** · **AHE'23** · ×৩ · (১৮) |
| | | English Grammar · Idioms · Comprehension | ★★★ | (২৯)+(৯)+(৫) |
| **বাংলা** | ★★★★ | Translation (ইংরেজি → বাংলা) | ★★★★★ | **AME'24** · **AHE'23** · ×৩ · (১৯) |
| | | Focus Writing (বাংলা রচনা) | ★★★★ | (২৫) |
| | | ব্যাকরণ ও সাহিত্য · সারমর্ম · পত্র লিখন | ★★ | (৬১)+(৬)+(৭) |
| **GK** | ★★★ | Bangladesh Affairs · International Affairs · Banking Abbreviations | ★★★ | (১১৪)+(৭০)+(৮) |

---

## Prediction

**কম্বাইন্ড ব্যাংক Assistant Maintenance Engineer ২০২৬-এর লিখিতে যেগুলো আসার সবচেয়ে বেশি সম্ভাবনা।** *(ভবিষ্যতের প্রশ্ন কেউ নিশ্চিত বলতে পারে না; স্টার আমার আত্মবিশ্বাসের মাত্রা, যা পুরোপুরি ঐতিহাসিক ডেটার ওপর দাঁড়ানো।)*

### ক. প্রায় নিশ্চিত — কম্বাইন্ড ব্যাংক AME-র পত্রেই এসেছে

| # | যা আসবে | কেন | ★ |
|---|---|---|---|
| ১ | **ডেটা সেন্টার — কুলিং সিস্টেমে DC জেনারেটর; ব্যাংকের ডেটা সেন্টারের গুরুত্বপূর্ণ উপাদান; energy efficiency** | **AME'24 · AHE'23 · BB AME'23 — পরপর তিনটি পত্রে**; মেইনটেন্যান্স পদের একদম কেন্দ্রীয় বিষয় | ★★★★★ |
| ২ | **Boolean expression-এর লজিক সার্কিট আঁকা + নির্দিষ্ট ইনপুটে আউটপুট নির্ণয়** | **AME'24**-এ হুবহু (Q = ĀB̄ + BC·(B+C)‾, ইনপুট দেওয়া ছিল); **BB AME'19** ও **BB AME'11**-এও লজিক গেট; ×৪; **(৩৩) সর্ববৃহৎ** | ★★★★★ |
| ৩ | **TCP/IP layer-এর টেবিল — কাজ, protocol, device ও software একসাথে** | **AME'24**-এ হুবহু; OSI ×২; (৫২) | ★★★★★ |
| ৪ | **টেবিল আকারে পরিভাষার পার্থক্য (নেটওয়ার্ক/ডেটা কমিউনিকেশন)** | **AME'24**-এ হুবহু; **BB AME'23**-এ parity ও ASCII | ★★★★★ |
| ৫ | **ব্যাংকের e-banking ওয়েব সার্ভার ডেটা সেন্টারে কনফিগার ও সুরক্ষিত করার ধাপ** | **AME'24**; **BB AME'17**-এ ওয়েব সার্ভার সুরক্ষার ধাপ — **×৫, এই পদের সর্বোচ্চ security হিট** | ★★★★★ |
| ৬ | **ফায়ারওয়ালের প্রকার; NGFW বনাম প্রচলিত ফায়ারওয়াল** | **AME'24**; BB AD(ICT)'25 ও BB AP'19-এও ফায়ারওয়াল ডায়াগ্রাম | ★★★★★ |
| ৭ | **OTP-ভিত্তিক অনলাইন ব্যাংকিং প্রমাণীকরণ প্রক্রিয়া** | **AME'24**-এ হুবহু | ★★★★★ |
| ৮ | **Multiplexing-এর প্রকারভেদ (TDM/FDM/WDM)** | **AHE'23** · **AME'24**; ×৩; SO'23-এও TDM/FDM/WDM | ★★★★★ |
| ৯ | **Multiprocessor বনাম multicomputer; shared memory; pipelining কেন ভালো** | **AME'24**; **BB SO'24 · BB AME'19 · BB AME'11 — বাংলাদেশ ব্যাংক তিনবার** | ★★★★★ |
| ১০ | **OS-র পরিভাষা এক প্রশ্নে — socket, kernel, process, program, multiprogramming, context switching + preemptive priority scheduling** | **AME'24**-এ হুবহু; **BB AME'19**-এও OS concepts | ★★★★★ |
| ১১ | **Policy, guideline ও procedure-এর পার্থক্য; অডিটর কেন নিয়ন্ত্রণকে সিস্টেম হিসেবে দেখবে** | **AME'24**; **BB AME'23**-এ পেমেন্ট গেটওয়ে ঝুঁকি অডিট — ×২ | ★★★★★ |
| ১২ | **অনলাইন ব্যাংকিংয়ে ICT-র ১০টি উদ্ভাবনী প্রয়োগ** | **AME'24**-এ হুবহু; ×২ | ★★★★★ |
| ১৩ | **RAID কী, ডেটা সেন্টারের সার্ভারে কেন জরুরি, কোন level** | **AHE'23**; ×২; Sonali PLC DBA'24-এও RAID | ★★★★★ |
| ১৪ | **Memory organization; SRAM বনাম DRAM** | **AHE'23**; (২৬) | ★★★★★ |
| ১৫ | **Physical memory বনাম virtual memory — সুবিধা-অসুবিধাসহ** | **AHE'23**; (১৬) | ★★★★★ |
| ১৬ | **ডিজিটাল IC-র গুরুত্বপূর্ণ বৈশিষ্ট্য (TTL বনাম CMOS, fan-in/fan-out)** | **AHE'23**; ×২; (৬) | ★★★★★ |
| ১৭ | **ডিজিটাল ব্যাংকিং বনাম প্রচলিত ব্যাংকিং; আর্থিক অন্তর্ভুক্তিতে ভূমিকা** | **AHE'23**-এ হুবহু | ★★★★★ |
| ১৮ | **Encryption ও decryption কী; সাইবার নিরাপত্তা; শীর্ষ ১০ সাইবার আক্রমণ** | **AHE'23**; SO'23 ও SO'26-এও একই প্রশ্ন | ★★★★★ |
| ১৯ | **গণিত — মিশ্রণের অনুপাত, নৌকা-স্রোত, আয়তক্ষেত্র/সমকোণী প্লটের ক্ষেত্রফল, দাম বাড়লে সংখ্যা কমা** | **AME'24-এ ৪টি · AHE'23-এ ৩টি · BB AME'23-এ ৩টি** — এই পদের লিখিতে গণিত বাদ দেওয়া মানে ১০+ নম্বর ছেড়ে দেওয়া | ★★★★★ |
| ২০ | **ইংরেজি রচনা — পরিবেশ/প্রযুক্তি/জাতীয় প্রকল্প (১৫০ শব্দ)** | **AME'24** (বায়ুদূষণের স্বাস্থ্যপ্রভাব) · **AHE'23** (মেট্রোরেল ও সমান সুযোগ); ×৩ | ★★★★★ |
| ২১ | **দুই দিকের অনুবাদ** | **AME'24-এ দুটোই** · **AHE'23-এ দুটোই**; ×৬ | ★★★★★ |

### খ. খুব বেশি সম্ভাবনা — বাংলাদেশ ব্যাংক AME বা Combined 5 Banks-এ এসেছে

| # | যা আসবে | কেন | ★ |
|---|---|---|---|
| ২২ | **Cache memory — miss-এর ধরন, direct-mapped field, average access time** | **বাংলাদেশ ব্যাংক ৩ পরীক্ষায়: SO'24, AME'23, AME'17** | ★★★★★ |
| ২৩ | **Nyquist ও Shannon দিয়ে সর্বোচ্চ ডেটা রেট** | **BB AME'23-এ ২টি**; (১৬) | ★★★★★ |
| ২৪ | **Subnetting — network/broadcast/mask/usable range** | **BB AME'17**; ×২; **(১০৯) ভাণ্ডারের সর্ববৃহৎ** | ★★★★★ |
| ২৫ | **8086 বনাম 8088, flag register; ৩২ bit বনাম ৬৪ bit; addressing mode** | **BB AME'11** · **BB AME'17**; ×৪; **(৩৫) সর্ববৃহৎ** | ★★★★★ |
| ২৬ | **Latch বনাম Flip-flop** | **BB AME'17**; SPCBL'21-এ হুবহু | ★★★★ |
| ২৭ | **ATM কীভাবে টেস্ট করবেন (বিতরণকৃত সিস্টেমে) + সর্টিং অ্যালগরিদম টেস্টের কোড** | **5B'19-এ দুটোই** · **BB AME'19** (ATM testing ১০ ধাপ); ×৪ | ★★★★★ |
| ২৮ | **Data mining-এর ধাপ; শীর্ষ ১০% GPA বের করার SQL** | **5B'19-এ দুটোই** | ★★★★ |
| ২৯ | **HTML5-এর `<header>`, `<footer>`, `<section>`, `<article>`; DOM দিয়ে মান বদলানো; `$.ajax()` বনাম `$.get()` বনাম `$.load()`** | **5B'19-এ ৩টি** — মেইনটেন্যান্স পদেও ওয়েব আসে | ★★★★ |
| ৩০ | **.NET Framework কী ও এর component** | **5B'19**; (৬) | ★★★★ |
| ৩১ | **প্রদত্ত কোডের ভুল বের করা** | **5B'19**; (৫৭) | ★★★★ |
| ৩২ | **Cloud service model (IaaS/PaaS/SaaS) ও VM বনাম container** | **BB AME'23-এ ৩টি** (service model দুইবার + virtualization) | ★★★★★ |
| ৩৩ | **ব্যাটারি বনাম ক্যাপাসিটর; fuse/MCB/relay; ট্রানজিস্টরের অঞ্চল; অল্টারনেটর ও ইন্ডাকশন মোটর** | **BB AME'17** · **BB AME'23** · **BB AME'19** — ইলেকট্রনিক্স এই পদে সত্যিই আসে | ★★★★★ |
| ৩৪ | **SMTP/DHCP-র short note; ইমেইলের পথ** | **BB AME'17**; (১০)+(২২) | ★★★★ |
| ৩৫ | **CPU scheduling — turnaround time; I/O utilization** | **BB AME'11-এ দুটোই**; ×২ | ★★★★ |
| ৩৬ | **কম্পিউটার ও নেটওয়ার্ক সংক্রান্ত পূর্ণরূপ; BIOS ও booting** | **BB AME'16-এ ৪টি** (২টি acronym + ২টি hardware/BIOS); **(৫৯) সর্ববৃহৎ** | ★★★★ |

---

## যাচাইকরণ নোট

সব স্টার, সংখ্যা আর পরীক্ষার নাম `all-questions/`-এর ভেতরের আসল exam tag থেকে গোনা — কোনোটাই অনুমান করা নয়। Prediction অংশটা ঐতিহাসিক প্যাটার্ন থেকে করা পূর্বাভাস, নিশ্চয়তা নয়।
