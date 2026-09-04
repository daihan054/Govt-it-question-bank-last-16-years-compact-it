# কম্বাইন্ড ব্যাংক অ্যাসিস্ট্যান্ট সিস্টেম ইঞ্জিনিয়ার ২০২৬ — লিখিত সাজেশন

**ভিত্তি:** [`all-questions/`](../../all-questions/)-এর ৫০টি `.md` ফাইল সম্পূর্ণ পড়া হয়েছে — ৫,৯১০টি প্রশ্ন, ৩৫০টি আলাদা পরীক্ষা, ২০১১–২০২৬। লিখিত অংশে ৩,১৬৮টি প্রশ্ন।

## ⚠️ এই পদটি নিয়ে একটি সৎ কথা

**`all-questions/`-এ "Combined Bank Assistant System Engineer" নামের কোনো প্রশ্নপত্র নেই।** এই নামে কোনো exam tag ভাণ্ডারে পাওয়া যায়নি, তাই এই পদের নিজস্ব ঐতিহাসিক প্রশ্ন দেখানো সম্ভব নয় — এবং বানিয়ে দেখানো হবেও না।

তার বদলে এই সাজেশন দাঁড়িয়েছে **একই কাজের অন্য নামে হওয়া পদগুলোর ১৫১টি যাচাই করা লিখিত রেকর্ডের** ওপর:

| পরীক্ষা | লিখিত প্রশ্ন |
|---|---|
| `RAKUB Network System Engineer (PO) 10.10.2021` | ২৫ |
| `Rupali Bank Ltd. Assistant Network Engineer 04.11.2023` | ২৪ |
| `Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024` | ১৮ |
| `RAKUB Assistant Network System Engineer 03.11.2023` | ৯ |
| `Dhaka Mass Transit (DMTCL) Assistant Engineer (ICT) 27.01.2023` | ৯ |
| `BPSC Assistant Network Engineer 2020` · `Sylhet Gas Field (SGFL) Assistant Engineer (IT) 2023` | ৮ + ৮ |
| `Rupali Bank Limited Assistant Network Engineer (ANE) 2021` | ৭ |
| `BCC Assistant Network Engineer 18.10.2025` — **সবচেয়ে সাম্প্রতিক** | ৬ |
| `BREB Assistant Hardware & Network Engineer 2019` | ৬ |
| `APSCL Assistant Engineer (ICT/MIS) 12.11.2021` · `NWPGCL Assistant Engineer (IT) 03.12.2021` | ৫ + ৪ |

## এই ঘরানার চরিত্র — সরাসরি গোনা

১৫১টি লিখিত হিটের **৪৯টিই computer-networks** — অর্থাৎ **প্রতি ৩টির ১টি**। কোনো পদেই নেটওয়ার্কের ঘনত্ব এত বেশি নয়। এরপর security ১৩ · database ১১ · c-programming ১০ · computer-fundamental ৮ · dld ৭ · microprocessor ৭।

**এই পদে পাশ-ফেল ঠিক হবে নেটওয়ার্কিং দিয়ে।** subnetting, routing, NAT, OSI ও ফায়ারওয়াল — এই পাঁচটা জায়গা শক্ত হলে অর্ধেকের বেশি নম্বর নিশ্চিত।

### স্টারের অর্থ

| স্টার | মানে |
|---|---|
| ★★★★★ | এই ঘরানার একাধিক লিখিত পত্রে এসেছে (×৩ বা তার বেশি), বা সবচেয়ে সাম্প্রতিক পত্রে |
| ★★★★ | এই ঘরানার কোনো পত্রে এসেছে, অথবা সাবটপিকটা খুব বড় |
| ★★★ | ব্যাংক সেক্টরে নিয়মিত আসে |
| ★★ | আছে, কিন্তু ঘনত্ব কম |
| ★ | বিরল — সময় থাকলে দেখবেন |

`RAKUB'21` = RAKUB Network System Engineer (PO) 10.10.2021 · `Rupali'23` = Rupali Bank ANE 04.11.2023 · `AE(IT)'24` = Combined Bank AME/Assistant Engineer (IT) 24.02.2024 · `BCC'25` = BCC Assistant Network Engineer 18.10.2025 · `(১০৯)` = ঐ সাবটপিকে মোট প্রশ্ন

---

## Important topic

| Topic | ★ | Subtopic | ★ | প্রমাণ |
|---|---|---|---|---|
| **Computer Networks** | ★★★★★ | Subnetting & IP Addressing — **/19, /23, /28 ব্লক ভাগ করে network/broadcast/first-last usable**; public বনাম private IP; decimal→binary IP | ★★★★★ | **BCC'25-এ ২টি · Rupali'23-এ ৩টি · RAKUB'21** (172.18.10.0/23 → ৪ সাবনেট) · **×৮** · **(১০৯) ভাণ্ডারের সর্ববৃহৎ** |
| | | Routing Protocols & Route Configuration — **static বনাম dynamic; distance vector বনাম link state; RIP/OSPF/EIGRP; EIGRP cost; autonomous system** | ★★★★★ | **RAKUB'21-এ ৪টি আলাদা প্রশ্ন** · **BCC'25** · ×৫ · (১৮) |
| | | Network Address Translation (NAT) — **কেন দরকার, টপোলজি ডায়াগ্রাম এঁকে; PAT কীভাবে কাজ করে** | ★★★★★ | **RAKUB'21-এ ২টি** · **RAKUB'23** · ×৫ · (১৩) |
| | | OSI & TCP/IP Reference Model — **OSI বনাম TCP/IP; ৪ layer-এর ডায়াগ্রাম; layer-ভিত্তিক protocol/device/software টেবিল** | ★★★★★ | **Rupali'23** · **RAKUB'21-এ ২টি** · **AE(IT)'24** · ×৪ · (৫২) |
| | | IPv6 Addressing — **DHCPv6 (stateful বনাম stateless); link-local ও multicast address; IPv4 বনাম IPv6** | ★★★★★ | **RAKUB'21-এ ৩টি** · **RAKUB'23** · ×৩ · (১৩) |
| | | Physical Layer & Transmission Media — **10BaseT; কোন media-য় সর্বোচ্চ bandwidth; broadband বনাম baseband** | ★★★★★ | **RAKUB'21-এ ২টি** · **Rupali'23** · ×৩ · (১৫) |
| | | Networking Fundamentals & Terminology — নেটওয়ার্কের সংজ্ঞা ও প্রকার | ★★★★ | ×৩ · (৩২) |
| | | Networking Devices — **collision domain বনাম broadcast domain** | ★★★★ | **Rupali'23** · ×২ · (১৯) |
| | | Network Topologies — Bus/Ring/Tree/Star, bus থেকে star-এ রূপান্তর | ★★★★ | **Rupali'23** · (১৪) |
| | | Multiplexing & Bandwidth · Flow Control (STP, congestion control) | ★★★★ | **RAKUB'21** (STP ও congestion control) · ×২ · (১৮)+(১২) |
| | | Network Services (DHCP, APIPA) · Address Resolution (ARP) · VLAN (static বনাম dynamic) | ★★★★ | **RAKUB'21-এ তিনটিই** · (১১)+(২)+(২) |
| | | Email Architecture (SMTP বনাম SNMP; HTTP বনাম HTTPS) · Switching (packet বনাম circuit) | ★★★★ | **RAKUB'23** · **Rupali'23** · (১০)+(৫) |
| | | WAN Technologies — IPoE বনাম PPPoE | ★★★★ | **RAKUB'21** · (৫) |
| | | Application Layer (DNS, DHCP) · Transport Layer (TCP বনাম UDP) · Data Rate · Error Detection | ★★★★ | **BCC'25-এ দুটোই** · (২২)+(১৭)+(১৬)+(১৪) |
| | | Optical Fiber · Wireless & IoT · Digital Modulation · PCM · Satellite | ★★★ | (১৩)+(১৯)+(১০)+(৬)+(৪) |
| **Computer / Network Security** | ★★★★★ | Firewalls & Network Defense — **ফায়ারওয়ালসহ LAN-এর ডায়াগ্রাম আঁকা; NGFW বনাম প্রচলিত ফায়ারওয়াল** | ★★★★★ | **Rupali'23** · **AE(IT)'24** · ×৩ · (২০) |
| | | Security Protocols (SSL/TLS, HTTPS) — **SSL কী; TLS 1.2 বনাম 1.3** | ★★★★★ | **BCC'25** · **Rupali'23** · ×৩ · (১২) |
| | | Cryptography — symmetric বনাম asymmetric encryption উদাহরণসহ | ★★★★★ | **Rupali'23** · ×২ · (৩১) |
| | | VPN & Tunneling — **site-to-site বনাম remote access VPN**, IPsec | ★★★★★ | **RAKUB'21** · ×২ · (৬) |
| | | Web Security Vulnerabilities — ওয়েব সার্ভার সুরক্ষিত করার ধাপ | ★★★★★ | **AE(IT)'24** · ×২ · (১৯) |
| | | Authentication & Access Control — OTP ভিত্তিক অনলাইন ব্যাংকিং | ★★★★ | **AE(IT)'24** · (১৬) |
| | | Social Engineering & Cyber Attacks · Malware · Cyber Crime · CIA Triad | ★★★ | (৩২)+(২০)+(১০)+(৮) |
| **Computer Fundamental** | ★★★★★ | Server Hardware & Enterprise Systems — **সার্ভারের মূল হার্ডওয়্যার উপাদান; সার্ভার রক্ষণাবেক্ষণের best practice** | ★★★★★ | **Rupali'23-এ ২টি** · ×২ · (৫) |
| | | Data Center Infrastructure & Power Management — **ডেটা সেন্টারের কুলিংয়ে DC জেনারেটর; ব্যাংকের ডেটা সেন্টারের গুরুত্বপূর্ণ উপাদান** | ★★★★★ | **AE(IT)'24** · ×২ · (১০) |
| | | Hardware Components & BIOS — **সার্ভারে BIOS, booting configuration** | ★★★★★ | **RAKUB'23** · (২৪) |
| | | Computer Fundamentals & Acronyms — **DHCP, ICMP, ACNS, GARP-এর পূর্ণরূপ** | ★★★★★ | **RAKUB'21** · **(৫৯) সর্ববৃহৎ** |
| | | ICT in Society & Governance — অনলাইন ব্যাংকিংয়ে ICT-র ১০টি প্রয়োগ | ★★★★ | **AE(IT)'24** · ×২ · (২৪) |
| | | Blockchain · Digital Banking · Quantum Computing | ★★★ | (৮)+(২)+(৩) |
| **Database** | ★★★★ | SQL Queries — query থেকে আউটপুট বিশ্লেষণ, join | ★★★★★ | **Rupali'23** · **RAKUB'23** · ×৬ · **(৮৭) সর্ববৃহৎ** |
| | | ER Diagram & Database Design | ★★★★ | ×৩ · (২৫) |
| | | Database Backup & Disaster Recovery — **data recovery বনাম disaster recovery** | ★★★★★ | **Rupali'23** · (৮) |
| | | Keys in DBMS · Normalization · Transaction & ACID · DBMS Architecture | ★★★ | (৩৪)+(২১)+(১৪)+(২৬) |
| **Microprocessor & Architecture** | ★★★★ | Microprocessor Architecture & Functions — **CPU-র গতিকে প্রভাবিত করা উপাদানগুলো** | ★★★★★ | **Rupali'23** · **(৩৫) সর্ববৃহৎ** |
| | | Instruction Pipelining & Hazards — multiprocessor বনাম multicomputer, shared memory | ★★★★★ | **AE(IT)'24** · (৯) |
| | | Secondary Storage (HDD বনাম SSD) | ★★★★ | ×২ · (১০) |
| | | Memory Hierarchy & Storage · RAID Architecture · Cache Memory | ★★★★ | (২৬)+(১৫)+(১৪) |
| **C Programming / প্রোগ্রাম লেখা** | ★★★★ | Basic Programs & Control Statements | ★★★★★ | ×৪ · **(১১১) ভাণ্ডারের সর্ববৃহৎ** |
| | | Output Tracing & Control Flow — **আউটপুটসহ time ও space complexity** | ★★★★★ | **Rupali'23** · ×২ · (৫৭) |
| | | String Manipulation & Algorithms | ★★★★ | ×২ · (১৪) |
| | | Recursion & Functions · Flowcharts · Pointers | ★★★ | (৩৮)+(১৬)+(৪) |
| **DLD** | ★★★★ | Logic Gates & Universal Gates — **Boolean expression-এর লজিক সার্কিট আঁকা ও নির্দিষ্ট ইনপুটে আউটপুট** | ★★★★★ | **AE(IT)'24** (Q = ĀB̄ + BC·(B+C)‾) · ×২ · **(৩৩) সর্ববৃহৎ** |
| | | Karnaugh Map (K-Map) — minimal SOP | ★★★★★ | ×২ · (১৯) |
| | | Logic Families (TTL বনাম CMOS) — ডিজিটাল IC-র বৈশিষ্ট্য | ★★★★ | (৬) |
| | | Number Systems · Boolean Algebra · Combinational · Sequential Circuits | ★★★ | (২৬)+(১৯)+(২৩)+(১৭) |
| **Operating System** | ★★★★ | OS Concepts & System Software — **socket, kernel, process, program, multiprogramming, context switching; preemptive priority scheduling** | ★★★★★ | **AE(IT)'24** · ×৩ · (২৪) |
| | | Virtual Memory & Page Replacement — physical বনাম virtual memory | ★★★★ | (১৬) |
| | | Linux / Unix Commands & Administration | ★★★★ | **(৪৭) OS-র সর্ববৃহৎ** |
| | | CPU Scheduling · Deadlock · Memory Management · Concurrency | ★★★ | (২৫)+(২৩)+(১৬)+(১১) |
| **Data Structure** | ★★★ | Binary Search Tree (BST) | ★★★★ | ×২ · (৯) |
| | | Tree · Stack · Linked List · Queue · Hashing | ★★★ | (২৭)+(২০)+(১৫)+(৬)+(৬) |
| **Algorithm** | ★★★ | Algorithm Analysis & Asymptotic Complexity — time ও space complexity | ★★★★ | **RAKUB'23** · (১৪) |
| | | Sorting · Graph Traversal · Graph Algorithms · Searching | ★★★ | (৩৬)+(১৭)+(১৫)+(১৪) |
| **Cloud Computing** | ★★★ | Virtualization & Containers — **সার্ভার ভার্চুয়ালাইজেশন উদাহরণসহ** | ★★★★★ | **RAKUB'23** · (৮) |
| | | Cloud Service Models · Cloud Fundamentals | ★★★ | (১৩)+(৬) |
| **Software Engineering** | ★★★ | Open Source Software & Licensing — সুবিধা-অসুবিধা উদাহরণসহ | ★★★★★ | **RAKUB'23** · (২) |
| | | Software Testing · SDLC · IT Governance & Audit · UML | ★★★ | (৪০)+(৪৫)+(৪)+(১৪) |
| **AI & ML** | ★★ | ML Paradigms · Generative AI | ★★★ | (৬)+(৪) |
| **Web Technology** | ★★ | JavaScript & jQuery · HTML · HTTP Protocol | ★★★ | (১৬)+(৩০)+(১০) |

### General section — বাংলা, ইংরেজি, গণিত, GK

| Topic | ★ | Subtopic | ★ | প্রমাণ |
|---|---|---|---|---|
| **ইংরেজি** | ★★★★★ | Focus Writing — **নারীর ক্ষমতায়ন, বায়ুদূষণ, জাতীয় উন্নয়ন** ঘরানা | ★★★★★ | **Rupali'23** ("Women's Empowerment and Gender Equality in Bangladesh", ২০০ শব্দ) · **AE(IT)'24** ("Impacts of air pollution on human health") · ×৪ · **(৩৭) সর্ববৃহৎ** |
| | | Translation (বাংলা → ইংরেজি) | ★★★★★ | **AE(IT)'24** · **RAKUB'21** · ×২ · (১৮) |
| | | English Grammar · Idioms · Comprehension | ★★★ | (২৯)+(৯)+(৫) |
| **বাংলা** | ★★★★ | Focus Writing — **"সমৃদ্ধির অগ্রযাত্রায় বাংলাদেশ"** ঘরানার রচনা | ★★★★★ | **Rupali'23** · **RAKUB'21** · ×৩ · (২৫) |
| | | Translation (ইংরেজি → বাংলা) | ★★★★★ | **AE(IT)'24** · ×২ · (১৯) |
| | | ব্যাকরণ ও সাহিত্য · সারমর্ম · পত্র লিখন | ★★ | (৬১)+(৬)+(৭) |
| **গণিত** | ★★★★ | Ratio, Proportion & Mixtures — **দুধ-পানির মিশ্রণ (১:২, ২:৩, ৩:৪); ছেলে-মেয়ের অনুপাত** | ★★★★★ | **AE(IT)'24-এ ২টি** · ×২ · (৪) |
| | | Geometry & Coordinate Geometry — আয়তক্ষেত্রের ভেতরের চতুর্ভুজের ক্ষেত্রফল | ★★★★★ | **AE(IT)'24** · (১০) |
| | | Speed, Time, Distance & Boats — স্রোতের গতিবেগ (নৌকা ভাটি-উজান) | ★★★★★ | **AE(IT)'24** · (৪) |
| | | Arithmetic & Algebra · Percentage & সুদ · Set Theory | ★★★ | (১৬)+(১২)+(১৩) |
| **GK** | ★★★★ | Bangladesh Affairs — গ্রন্থের লেখক, পুরস্কার, অর্থনীতি | ★★★★★ | **Rupali'23-এ ২টি** · ×৩ · **(১১৪) সর্ববৃহৎ** |
| | | Everyday Science & Environment — দীর্ঘতম-ক্ষুদ্রতম দিন, বৃহত্তম-ভারী গ্রহ | ★★★★★ | **Rupali'23-এ ২টি** · ×২ · (২২) |
| | | International Affairs · Banking & ICT Abbreviations | ★★★★ | (৭০)+(৮) |

---

## Prediction

**কম্বাইন্ড ব্যাংক Assistant System Engineer ২০২৬-এর লিখিতে যেগুলো আসার সবচেয়ে বেশি সম্ভাবনা।** *(এই পদের নিজস্ব ঐতিহাসিক পত্র ভাণ্ডারে নেই — নিচের প্রতিটি লাইন নেটওয়ার্ক/সিস্টেম ইঞ্জিনিয়ার ঘরানার আসল পত্র থেকে গোনা প্যাটার্নের ভিত্তিতে করা পূর্বাভাস, নিশ্চয়তা নয়।)*

### ক. প্রায় নিশ্চিত — এই ঘরানার একাধিক পত্রে এসেছে

| # | যা আসবে | কেন | ★ |
|---|---|---|---|
| ১ | **Subnetting — একটা ব্লক ভাগ করে network, broadcast, প্রথম ও শেষ usable IP** | **BCC'25** (192.168.0.0/28) · **Rupali'23** (172.16.0.0/19-এ কত সাবনেট) · **RAKUB'21** (172.18.10.0/23 → ৪ সাবনেট) — **তিনটি আলাদা পত্রে**; **(১০৯) ভাণ্ডারের সর্ববৃহৎ** | ★★★★★ |
| ২ | **Class A/B/C-র private IP range; public বনাম private IP** | **BCC'25** · **Rupali'23** — পরপর দুই পত্রে | ★★★★★ |
| ৩ | **Routing — static বনাম dynamic; distance vector বনাম link state; RIP/OSPF/EIGRP; autonomous system** | **RAKUB'21-এ ৪টি আলাদা প্রশ্ন** — এক পত্রে চারবার মানে এটাই পদের মূল এলাকা; **BCC'25**-এও routing protocol জোড়া | ★★★★★ |
| ৪ | **NAT কেন দরকার + টপোলজি ডায়াগ্রাম এঁকে ব্যাখ্যা; PAT কীভাবে কাজ করে** | **RAKUB'21-এ ২টি** · **RAKUB'23** · ×৫; Officer(IT) '২৬ মে-তেও NAT | ★★★★★ |
| ৫ | **OSI বনাম TCP/IP মডেল; ৪ layer-এর ডায়াগ্রাম; layer-ভিত্তিক protocol-device-software টেবিল** | **Rupali'23** · **RAKUB'21-এ ২টি** · **AE(IT)'24** — ×৪ | ★★★★★ |
| ৬ | **IPv6 — DHCPv6 (stateful বনাম stateless), link-local ও multicast address, IPv4 বনাম IPv6** | **RAKUB'21-এ ৩টি** · **RAKUB'23** | ★★★★★ |
| ৭ | **ফায়ারওয়ালসহ LAN-এর ডায়াগ্রাম আঁকা; NGFW বনাম প্রচলিত ফায়ারওয়াল; ফায়ারওয়াল কেন জরুরি** | **Rupali'23** · **AE(IT)'24** — পরপর দুই পত্রে; BB AD(ICT)'25 ও BB AP'19-এও ফায়ারওয়াল ডায়াগ্রাম | ★★★★★ |
| ৮ | **SSL কী; TLS 1.2 বনাম TLS 1.3** | **BCC'25** (সবচেয়ে সাম্প্রতিক) · **Rupali'23** | ★★★★★ |
| ৯ | **VPN — site-to-site বনাম remote access, IPsec** | **RAKUB'21**; ×২ | ★★★★★ |
| ১০ | **সার্ভারের মূল হার্ডওয়্যার উপাদান ও রক্ষণাবেক্ষণের best practice** | **Rupali'23-এ ২টি আলাদা প্রশ্ন** — এটা এই পদের একদম নিজস্ব প্রশ্ন | ★★★★★ |
| ১১ | **ডেটা সেন্টার — কুলিং, জেনারেটর, ব্যাংকের ডেটা সেন্টারের গুরুত্বপূর্ণ উপাদান** | **AE(IT)'24** · ×২; **BB AME'23**-এও data center energy efficiency | ★★★★★ |
| ১২ | **সার্ভারে BIOS ও booting configuration** | **RAKUB'23**; হার্ডওয়্যার রক্ষণাবেক্ষণের সাথে সরাসরি জড়িত | ★★★★★ |
| ১৩ | **পূর্ণরূপ — DHCP, ICMP, ARP, GARP, APIPA, STP** | **RAKUB'21** (DHCP, ICMP, ACNS, GARP) · **RAKUB'21**-এ APIPA ও ARP আলাদা প্রশ্ন · **BCC'25** (DHCP) | ★★★★★ |
| ১৪ | **TCP বনাম UDP** | **BCC'25** — সবচেয়ে সাম্প্রতিক পত্র; ৩ পরীক্ষায় হুবহু | ★★★★★ |
| ১৫ | **Collision domain বনাম broadcast domain; switch ও router-এর কাজ** | **Rupali'23**; Officer(IT) '২৬ জুলাই-তেও switch বনাম router | ★★★★★ |
| ১৬ | **Network topology — Bus/Ring/Tree/Star, bus থেকে star-এ রূপান্তর** | **Rupali'23**; SO'23-এও topology | ★★★★★ |
| ১৭ | **Transmission media — 10BaseT, কোন media-য় সর্বোচ্চ bandwidth, broadband বনাম baseband** | **RAKUB'21-এ ২টি** · **Rupali'23** | ★★★★★ |
| ১৮ | **VLAN — static বনাম dynamic VLAN** | **RAKUB'23** | ★★★★★ |
| ১৯ | **STP কীভাবে কাজ করে; congestion control অ্যালগরিদম** | **RAKUB'21** | ★★★★★ |
| ২০ | **IPoE বনাম PPPoE** | **RAKUB'21** — এই ঘরানা ছাড়া আর কোথাও নেই | ★★★★ |
| ২১ | **Packet switching বনাম circuit switching — কোনটা কেন পছন্দ করবেন** | **Rupali'23** | ★★★★ |
| ২২ | **SMTP বনাম SNMP; HTTP বনাম HTTPS** | **RAKUB'23** | ★★★★ |
| ২৩ | **সার্ভার ভার্চুয়ালাইজেশন উদাহরণসহ** | **RAKUB'23**; Officer(IT) '২৬ জুলাই-তেও VM ক্যাপাসিটি গণনা | ★★★★ |
| ২৪ | **Symmetric বনাম asymmetric encryption উদাহরণসহ** | **Rupali'23**; ×২; **BB SO'24 → '২৬**-এ hashing বনাম encryption | ★★★★ |
| ২৫ | **Data recovery বনাম disaster recovery** | **Rupali'23**; SO'23/'24-এও DR plan ও ০-bit data loss | ★★★★ |
| ২৬ | **Boolean expression-এর লজিক সার্কিট আঁকা ও নির্দিষ্ট ইনপুটে আউটপুট** | **AE(IT)'24** (Q = ĀB̄ + BC·(B+C)‾); **(৩৩) dld-র সর্ববৃহৎ** | ★★★★ |
| ২৭ | **OS-র পরিভাষা — socket, kernel, process, program, multiprogramming, context switching + preemptive priority scheduling** | **AE(IT)'24**-এ একটি প্রশ্নেই সবগুলো | ★★★★ |
| ২৮ | **Multiprocessor বনাম multicomputer; shared memory** | **AE(IT)'24** | ★★★★ |
| ২৯ | **CPU-র গতিকে প্রভাবিত করা উপাদানগুলো** | **Rupali'23**; **(৩৫) সর্ববৃহৎ** | ★★★★ |
| ৩০ | **কোডের আউটপুট + time ও space complexity** | **Rupali'23**; **RAKUB'23**-এ complexity আলাদা প্রশ্ন | ★★★★ |
| ৩১ | **Open source software-এর সুবিধা-অসুবিধা উদাহরণসহ** | **RAKUB'23**; SO'26-এও একই প্রশ্ন compiler-এর সাথে | ★★★★ |
| ৩২ | **অনলাইন ব্যাংকিংয়ে OTP ভিত্তিক প্রমাণীকরণ; ওয়েব সার্ভার সুরক্ষার ধাপ** | **AE(IT)'24-এ দুটোই** | ★★★★ |
| ৩৩ | **ইংরেজি রচনা (নারীর ক্ষমতায়ন / বায়ুদূষণ / উন্নয়ন) + বাংলা রচনা ("সমৃদ্ধির অগ্রযাত্রায় বাংলাদেশ" ঘরানা)** | **Rupali'23-এ দুটোই** · **AE(IT)'24** · **RAKUB'21** — প্রতিটি পত্রেই | ★★★★★ |
| ৩৪ | **দুই দিকের অনুবাদ** | **AE(IT)'24-এ দুটোই**; ×৪ | ★★★★★ |
| ৩৫ | **গণিত — মিশ্রণের অনুপাত, নৌকা-স্রোত, আয়তক্ষেত্রের ক্ষেত্রফল** | **AE(IT)'24-এ ৪টি গাণিতিক প্রশ্ন** — এই ঘরানার লিখিতে গণিত বাদ দেওয়া যাবে না | ★★★★★ |
| ৩৬ | **সংক্ষিপ্ত GK — গ্রন্থের লেখক, পুরস্কার, গ্রহ-নক্ষত্র, দীর্ঘতম দিন** | **Rupali'23-এ ৫টি**; ×৬ | ★★★★ |

---

## যাচাইকরণ নোট

`all-questions/`-এ "Combined Bank Assistant System Engineer" নামে কোনো প্রশ্নপত্র নেই — সেটা উপরে স্পষ্ট করে বলা হয়েছে, বানিয়ে দেখানো হয়নি। সব স্টার, সংখ্যা আর পরীক্ষার নাম ভাণ্ডারের আসল exam tag থেকে গোনা। Prediction অংশটা নিকটতম পদগুলোর প্যাটার্ন থেকে করা পূর্বাভাস, নিশ্চয়তা নয়।
