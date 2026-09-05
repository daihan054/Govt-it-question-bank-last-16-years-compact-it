# Nipu Bhai Coaching Class Report - Computer Networks & Security

**ক্লাসের তারিখ:** ০৩-সেপ্টেম্বর-২০২৬ (Network-1) ও ০৫-সেপ্টেম্বর-২০২৬ (Network-2)  
**লেকচার নোট সোর্স:** `E:\Govt job\Networking class` (Page 1 থেকে Page 12)  
**প্রজেক্ট ম্যাপিং:** `all-questions/written/` এবং `written-answers/`

---

## ১. Sir যা যা পড়িয়েছেন: Topic এবং Subtopic

লেকচারের ১২টি পৃষ্ঠার ইমেজ (Page 1 থেকে 12) পুঙ্খানুপুঙ্খভাবে বিশ্লেষণ করে স্যার যা যা পড়িয়েছেন তা নিচে Topic এবং Subtopic আকারে সাজানো হলো:

---

### পর্ব ১: Network Architecture & Enterprise Security (Page 1 – 8)
*(Lecture-1: তারিখ ০৩-সেপ্টেম্বর-২০২৬)*

#### ১. Topic: Networking Fundamentals & Devices (Page 1)
* **Subtopics:**
  * **Intranet vs. Internet** এর মৌলিক ধারণা।
  * **End-User Devices:** PC, Printer, Server, Smartphone।
  * **Intermediary Devices:** Router, Wireless Router, Cell Tower, Modem, Internet Cloud।
  * **ছোট নেটওয়ার্কের কাঠামো (Small Network):** Hub বনাম Switch (Hub হলো Insecure/Broadcast ডিভাইস; Switch হলো Secure যা MAC Address দেখে নির্দিষ্ট পোর্টে ফ্রেম পাঠায়)।
  * **বড় প্রতিষ্ঠানের নেটওয়ার্ক কাঠামো (Enterprise Network):** Access Switch (Switch-1, Switch-2: ৪৮ পোর্ট) $\rightarrow$ Core Switch $\rightarrow$ Perimeter Router $\rightarrow$ Internet।

#### ২. Topic: Enterprise Security Devices & Architecture (Page 2)
* **Subtopics:**
  * কোনো বড় সংস্থায় (যেমন: World Bank) ব্যবহৃত **১১টি কোর ডিভাইস:**
    1. PCs
    2. Firewall
    3. Switch
    4. IPS (Intrusion Prevention System)
    5. IDS (Intrusion Detection System)
    6. Anti-DDoS
    7. WAF (Web Application Firewall)
    8. Web Server
    9. Database Server
    10. Storage (SAN)
    11. SIEM / Monitoring
  * **Zero Trust Architecture:** সম্পূর্ণ সুরক্ষিত নেটওয়ার্ক ডিজাইনে Zero Trust মডেল অনুসরণ ("Never trust, always verify")।

#### ৩. Topic: Network Architecture Evolution & DMZ (Page 3)
* **Subtopics:**
  * **Old Approach (Flat Network):** ইন্টারনেট $\rightarrow$ ফায়ারওয়াল $\rightarrow$ একই নেটওয়ার্কে ইউজার + সার্ভার + ডেটাবেজ (অত্যন্ত ঝুঁকিপূর্ণ, কারণ একটি পিসি আক্রান্ত হলে সম্পূর্ণ নেটওয়ার্ক কম্প্রোমাইজড হয়)।
  * **Hardware Firewall Placement:** ইউজার সুইচ $\rightarrow$ ডেডিকেটেড হার্ডওয়্যার ফায়ারওয়াল $\rightarrow$ রাউটার $\rightarrow$ আউটার নেটওয়ার্ক।
  * **Modern 3-Tier Approach:** ইন্টারনেট $\rightarrow$ ফায়ারওয়াল $\rightarrow$ ৩টি পৃথক জোন:
    * **DMZ (Demilitarized Zone)**
    * **User Network**
    * **Server Network (Apps $\rightarrow$ DB)**

#### ৪. Topic: Hacker-Resilient Multi-tier DMZ Architecture (Page 4)
* **Subtopics:**
  * **DMZ (Demilitarized Zone):** ইন্টারনেটমুখী পাবলিক-ফেসিং জোন যেখানে WAF এবং Web Server (Web, Email, Mobile) অবস্থান করে।
  * **Internal Firewall:** DMZ এবং ডেটাবেজের মাঝে অবস্থান করে। নির্দিষ্ট পলিসি অনুযায়ী শুধু অনুমোদিত রিকোয়েস্ট (যেমন: MySQL পোর্ট 3306) ফিল্টার করে।
  * **Database Server:** সিকিউর জোনে থাকে, ইন্টারনেটের সাথে সরাসরি কোনো সংযোগ থাকে না।

#### ৫. Topic: Defense in Depth & Firewall Technologies (Page 5)
* **Subtopics:**
  * **Defense in Depth (স্তরভিত্তিক নিরাপত্তা):** DMZ-এর ওয়েব সার্ভার হ্যাক হলেও ইন্টারনাল ফায়ারওয়ালের কঠোর পলিসির (Allow 3306, ALL DENY) কারণে ডেটাবেজ সুরক্ষিত থাকে।
  * **Firewall প্রকারভেদ ও কাজের তুলনা:**
    * **Traditional/Old Firewall:** শুধু প্যাকেট হেডার ও ফুটার (IP, Port, Protocol) চেক করে (Packet Filtering)।
    * **Next-Generation Firewall (NGFW):** ডিপ প্যাকেট ইন্সপেকশন (DPI), অ্যাপ্লিকেশন অ্যাওয়ারনেস, পেলোড (Payload) এবং এনক্রিপশন/ডিক্রিপশন চেক করে।
  * **WAF (Web Application Firewall)-এর ৪টি প্রধান কাজ:**
    1. ব্যাকএন্ড সার্ভারের পাবলিক আইপি হাইড করে (Reverse Proxy হিসেবে কাজ করে)।
    2. ম্যালিশাস ট্রাফিক আটকায়।
    3. ম্যালিশাস স্ক্রিপ্ট ও ওয়েব অ্যাপ্লিকেশন অ্যাটাক (SQL Injection, XSS ইত্যাদি) প্রতিহত করে।
    4. লোড ব্যালান্সিং করে।

#### ৬. Topic: Anti-DDoS Protection & Multi-layer Filtering (Page 6)
* **Subtopics:**
  * **DDoS ট্রাফিকের বৈশিষ্ট্য:** সফটওয়্যার জেনারেটেড আবর্জনা/ফ্লাড ট্রাফিক যা সার্ভার ডাউন করতে আসে।
  * **Anti-DDoS ডিভাইসের ভূমিকা:** মূল ফায়ারওয়ালে পৌঁছানোর আগেই বট/গারবেজ ট্রাফিক ফিল্টার করা।
  * **মাল্টি-লেয়ার ফিল্টারিং পাইপলাইন:**
    * Filter 1: Anti-DDoS Device $\rightarrow$ Filter 2: Perimeter Firewall $\rightarrow$ Filter 3: WAF $\rightarrow$ Web Server $\rightarrow$ Filter 4: Internal Firewall $\rightarrow$ Database Server।

#### ৭. Topic: End-to-End Enterprise Flow & Asset Valuation (Page 7)
* **Subtopics:**
  * **Internet to Database Server Architecture:** Internet $\rightarrow$ Anti-DDoS $\rightarrow$ Firewall $\rightarrow$ WAF $\rightarrow$ Load Balancer $\rightarrow$ Web Server 1 & 2 $\rightarrow$ App Server $\rightarrow$ Internal Firewall $\rightarrow$ Database Server।
  * **Viva / Exam Question:** *"Database কি High-value asset নাকি Low-value asset?"* (Answer: High-value asset বা Crown jewel)।

#### ৮. Topic: SOC, SIEM & Security Architecture (Page 8)
* **Subtopics:**
  * Internet $\rightarrow$ Anti-DDoS $\rightarrow$ Perimeter Router $\rightarrow$ NGFW (High Availability - HA মোডে)।
  * ৩টি প্রধান জোন সেগমেন্টেশন:
    1. **DMZ:** WAF $\rightarrow$ Load Balancer $\rightarrow$ Web Server $\rightarrow$ Log Analysis (IDS/IPS) $\rightarrow$ SIEM $\rightarrow$ SOC (Security Operations Center)।
    2. **VPN Gateway:** দূরবর্তী কর্মীদের নিরাপদ রিমোট অ্যাক্সেসের জন্য।
    3. **Internal Network:** Core Switch $\rightarrow$ User PC, Database Server, Management Network।
  * **IDS/IPS vs SIEM:** সফটওয়্যার হিসেবে লগ অ্যানালাইসিস করে SIEM ও SOC টিমের কাছে অ্যালার্ট পাঠানো।

---

### পর্ব ২: OSI Reference Model & Protocols (Page 9 – 12)
*(Lecture-2: তারিখ ০৫-সেপ্টেম্বর-২০২৬)*

#### ৯. Topic: OSI Overview, Application & Presentation Layer (Page 9)
* **Subtopics:**
  * **OSI 7 Layers (Mnemonic - PDNTSPA):** Physical, Data Link, Network, Transport, Session, Presentation, Application।
  * **Layer 7 - Application Layer:**
    * নেটওয়ার্ক অ্যাপ্লিকেশনের (Chrome, Firefox ইত্যাদি) সাথে সরাসরি ইন্টারঅ্যাক্ট করে।
    * প্রোটোকলসমূহ: HTTP, HTTPS (Web Surfing), FTP (File Transfer), SMTP, POP3 (Email), DHCP, Telnet (Virtual Terminal)।
  * **Layer 6 - Presentation Layer:**
    * (i) **Translation:** ক্যারেক্টারকে মেশিনের বাইনারি ফরম্যাটে রূপান্তর (ASCII $\rightarrow$ EBCDIC ইত্যাদি)।
    * (ii) **Data Compression:** ডেটা কম্প্রেস করা (যেমন: Huffman Coding অ্যালগরিদম)।

#### ১০. Topic: Presentation (cont.), Session & Transport Layer (Page 10)
* **Subtopics:**
  * **Presentation Layer (cont.):** (iii) **Encryption / Decryption:** SSL (Secure Sockets Layer) প্রোটোকলের মাধ্যমে।
  * **Layer 5 - Session Layer:**
    * (i) **Authentication:** "Who are you?" (ব্যবহারকারীর পরিচয় নিশ্চিতকরণ)।
    * (ii) **Authorization:** "What permissions do you have?" (Admin vs. Guest অ্যাক্সেস কন্ট্রোল)।
    * (iii) **Session Management:** ইমেজ, টেক্সট, ডেটার সেশন ট্র্যাকিং।
    * *নোট:* ব্রাউজার মূলত উপরের ৩টি স্তরই (Application, Presentation, Session) হ্যান্ডেল করে।
  * **Layer 4 - Transport Layer (Segmentation):**
    * (i) **Segmentation:** ডেটাকে সেগমেন্টে ভাগ করা।
    * **Port Addressing:** অ্যাপ্লিকেশন লেভেলের অ্যাড্রেসিং (যেমন: IP + Port; MySQL-এর পোর্ট 3306)।

#### ১১. Topic: Transport Layer Flow/Error Control & TCP vs. UDP (Page 11)
* **Subtopics:**
  * (ii) **Flow Control:** সেন্ডার ও রিসিভারের গতির সমন্বয় (যেমন: সার্ভার 100 Mbps পাঠালে ফোন 20 Mbps-এ গ্রহণ করার রেট নিয়ন্ত্রণ)।
  * (iii) **Error Control:** ARQ (Automatic Repeat reQuest) মেকানিজম—ডেটা হারিয়ে গেলে পুনরায় পাঠানোর অনুরোধ।
  * **TCP বনাম UDP তুলনা:**
    * **TCP:** Connection-oriented, নির্ভরযোগ্য/Reliable (যেমন: Bank Transactions)।
    * **UDP:** Connectionless, দ্রুতগতির, প্যাকেট লস হলেও সমস্যা নেই (যেমন: Live Cricket Streaming)।

#### ১২. Topic: Network Layer, Data Link Layer & PDU Comparison (Page 12)
* **Subtopics:**
  * **Layer 3 - Network Layer:**
    * (i) **Logical Addressing:** IPv4 এবং IPv6 (Source IP + Destination IP + Segment = Packet)।
    * (ii) **Routing:** প্যাকেট পাঠানোর উপযুক্ত পথ নির্ধারণ।
    * (iii) **Shortest Path Algorithm:** Dijkstra's Algorithm ব্যবহার করে রাউটিং।
  * **Layer 2 - Data Link Layer:**
    * **Physical Addressing:** MAC Address (MAC1 + Packet + MAC2 = Frame)।
  * **ক্লাসের গুরুত্বপূর্ণ প্রশ্নসমূহ (Exam/Viva):**
    * *Q1:* Frame, Packet ও Segment-এর মধ্যে পার্থক্য কী?
    * *Q2:* ফায়ারওয়াল কী চেক করে? Frame নাকি Packet? (Answer: মূলত Packet; NGFW পেলোড পর্যন্ত দেখে)।

---

## ২. এই প্রজেক্টের মধ্যে যা যা আসছে Previous Year Question থেকে (স্যারের পড়ানোর মধ্য থেকে)

প্রজেক্টের `all-questions/written/` ফোল্ডারের ফাইলগুলো থেকে স্যারের পড়ানো টপিক ও সাবটপিকগুলোর সাথে সরাসরি মিলে যাওয়া প্রশ্নগুলোর বিস্তারিত রেফারেন্স নিচে দেওয়া হলো:

---

### ফাইল ১: `all-questions/written/computer-network-security.md`
*(পূর্ণ সমাধান: `written-answers/computer-network-security.md`)*

#### ১. সাবটপিক: `## Firewalls & Network Defense (20)` (লাইন ১৫৬ – ২০৪)
> **স্যারের পড়ানোর সাথে মিল:** ফায়ারওয়াল, NGFW বনাম Traditional ফায়ারওয়াল, WAF, DMZ নেটওয়ার্ক ডায়াগ্রাম, IDS/IPS, Defense in Depth।

* **সরাসরি বিগত সালের লিখিত প্রশ্নসমূহ:**
  1. **Write down the difference between Next-Generation Firewall (NGFW) and Web Application Firewall (WAF)?**  
     *[Islami Bank PLC Senior Officer (Network/System) 14.03.2025]*  
     *(স্যারের লেকচার নোট: Page 5-এ ঠিক এই প্রশ্নটি SO (IT)-এর জন্য বিশেষভাবে মার্ক করা আছে)*
  2. **Bangladesh Bank have client server and the communication with Mail Server, DNS server, Web server. Bangladesh Bank want to ensure the security using firewall on those server. Draw a diagram with the scenario.**  
     *[Bangladesh Bank Assistant Director (ICT) 07.02.2025]*  
     *(স্যারের লেকচার নোট: Page 3, 4, 7-এর DMZ, Web Server, Firewall ডায়াগ্রামের হুবহু সিনারিও)*
  3. **What is Demilitarized Zone (DMZ) and sandbox for security test?**  
     *[PGCB Assistant Engineer (CSE) 17.05.2024]*
  4. **Different types of network firewalls. Explain NGFW compared to traditional firewall.**  
     *[Combined Bank Assistant Maintenance Engineer / Assistant Engineer (IT) 24.02.2024]*
  5. **Draw a diagram of LAN including network Firewall. Why is firewall important in network security? List 5 major types of network firewalls. Differentiate between Traditional Firewall and Next Generation Firewall.**  
     *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023]*
  6. **What is DMZ in data center? Describe using diagram? Write the network devices in this system?**  
     *[BDCCL Assistant Manager (Cyber Security) 14.10.2022]*
  7. **DMZ and firewall placement in a diagram.**  
     *[MGMCL Assistant Manager (ICT) 20.05.2022]*
  8. **What is DMZ? Explain with appropriate figure.**  
     *[NESCO Manager (Software) 2018]*
  9. **What is Stateful and Stateless Firewall?**  
     *[Dutch Bangla Bank Assistant Network/Hardware Engineer 2019]*
  10. **As a cybersecurity analyst at a nuclear power plant, what IDS strategies and steps are required to prevent cyberattacks?**  
      *[NPCBL Sub Assistant Engineer: Cyber Security Analyst 11.07.2026]*
  11. **What is Packet Filter of Firewall?**  
      *[National Legal Aid Services Organization AME 18.10.2025]*

#### ২. সাবটপিক: `## Social Engineering & Cyber Attacks (32)` (লাইন ২৬ – ৯১)
> **স্যারের পড়ানোর সাথে মিল:** Anti-DDoS ডিভাইস, DoS/DDoS আক্রমণ ও মাল্টি-লেয়ার ট্রাফিক ফিল্টারিং (Page 6, 7, 8)।

* **সরাসরি বিগত সালের লিখিত প্রশ্নসমূহ:**
  1. **What is a Denial of Service (DoS) attack? Explain Distributed Denial of Service (DDoS) and how to mitigate it.**  
     *[Multiple Bank & Ministry Exams]*

#### ৩. সাবটপিক: `## Security Protocols (SSL/TLS, HTTPS)` (লাইন ৩৫০ – ৩৮২)
> **স্যারের পড়ানোর সাথে মিল:** Presentation Layer-এ SSL প্রোটোকল ও Encryption/Decryption (Page 10)।

* **সরাসরি বিগত সালের লিখিত প্রশ্নসমূহ:**
  1. **What is SSL/TLS? How does HTTPS secure communication?**  
     *[Combined Bank Officer (IT) 2024 / BPSC]*

#### ৪. সাবটপিক: `## Authentication & Access Control` (লাইন ২৮৭ – ৩২০)
> **স্যারের পড়ানোর সাথে মিল:** Session Layer-এর Authentication ("Who are you?") ও Authorization (Admin vs Guest) (Page 10)।

* **সরাসরি বিগত সালের লিখিত প্রশ্নসমূহ:**
  1. **Difference between Authentication and Authorization with examples.**  
     *[Multiple IT Exams]*

---

### ফাইল ২: `all-questions/written/computer-networks.md`
*(পূর্ণ সমাধান: `written-answers/computer-networks.md`)*

#### ১. সাবটপিক: `## OSI & TCP/IP Reference Model (57)` (লাইন ৩৩২ – ৪৬১)
> **স্যারের পড়ানোর সাথে মিল:** OSI 7 Layers (PDNTSPA), প্রতিটি স্তরের কাজ, প্রোটোকল, ডিভাইস এবং Data $\rightarrow$ Segment $\rightarrow$ Packet $\rightarrow$ Frame $\rightarrow$ Bit (PDU) রূপান্তর।

* **সরাসরি বিগত সালের লিখিত প্রশ্নসমূহ:**
  1. **Mention the layers of the OSI Model and the function of each layer.**  
     *[Combined Bank Officer (IT) 03.01.2026]*
  2. **OSI মডেলের ৭টি স্তরের কাজ কি? এই সমগ্র স্তরগুলোর ভূমিকা কি?**  
     *[Department of Immigration & Passports Assistant Programmer 15.07.2026]*
  3. **What is the OSI model? Explain the functions of each layer with examples.**  
     *[Senior Officer IT (Job ID: 10225) 22.05.2026]*
  4. **In the TCP/IP model, how is data known in the different layers? (PDU)**  
     *[DPDC Assistant Engineer (CSE) 17.10.2025]*
  5. **Write bottom to top OSI reference Model.**  
     *[National Legal Aid Services Organization AME 18.10.2025]*
  6. **Tabular representation of TCP/IP layer, functions of each layer, Associate protocols, device, and software in each layer. Different types of network firewalls. Explain NGFW compared to traditional firewall.**  
     *[Combined Bank AME / AE (IT) 24.02.2024]*
  7. **Difference between OSI model and TCP/IP model. Relation between Data, Segment, Packet and Bit in OSI model.**  
     *[Combined Bank Senior Officer (IT) 13.10.2023]*  
     *(স্যারের লেকচার নোট: Page 12-এর হুবহু প্রশ্ন: Frame, Packet, Segment-এর সম্পর্ক)*
  8. **What is PDU?**  
     *[BARC Data Entry Officer 10.09.2022]*
  9. **In order to prevent that the company decided to add end to end encryption techniques which layer of the OSI model is suitable to work in...**  
     *[Bangladesh Bank Assistant Programmer 03.02.2023]*  
     *(স্যারের লেকচার নোট: Page 10-এ Presentation Layer-এ SSL Encryption)*
  10. **Describe the OSI layers. Draw a diagram to show the hierarchy when the data is transmitted or received.**  
      *[Combined Bank Senior Officer (IT/ICT) 2019]*

#### ২. সাবটপিক: `## Networking Devices (24)` (লাইন ৫৩১ – ৫৯৮)
> **স্যারের পড়ানোর সাথে মিল:** Hub, Switch, Router, Core Switch, Gateway, Access Point, Broadcast/Collision Domain (Page 1, 2, 8)।

* **সরাসরি বিগত সালের লিখিত প্রশ্নসমূহ:**
  1. **Describe the functions of a Switch and a Router and explain two key differences between these networking devices.**  
     *[Officer (IT) 31.07.2026]*
  2. **Briefly describe the following network devices: Repeater, Hub, Bridge, Switch and Router.**  
     *[Combined Bank Senior Officer (IT) 17.05.2024]*
  3. **Write the Difference among Network Switch, Hub and Router.**  
     *[BPSC AME 2020, DESCO SAE 2023, BMA SAE 2021]*
  4. **Write down the difference between Hub and Switch.**  
     *[DMLC Assistant Teacher (ICT) 2021]*  
     *(স্যারের লেকচার নোট: Page 1-এ Hub Insecure বনাম Switch Secure / MAC based)*
  5. **Write down the difference between gateway and firewall.**  
     *[DMTCL Assistant Engineer (ICT) 27.01.2023]*
  6. **What is gateway? Is router and gateway have any difference?**  
     *[BEPZA Programmer 03.11.2023]*
  7. **How many collision domains are created when you segment a network with a 12-port switch?**  
     *[BARI Assistant Maintenance Engineer 10.05.2024]*

#### ৩. সাবটপিক: `## Transport Layer (TCP & UDP) (22)` (লাইন ৬৪৮ – ৭১০)
> **স্যারের পড়ানোর সাথে মিল:** TCP বনাম UDP, Flow Control, Error Control (ARQ), Segmentation, 3-Way Handshake (Page 10, 11)।

* **সরাসরি বিগত সালের লিখিত প্রশ্নসমূহ:**
  1. **Distinguish between TCP and UDP protocols.**  
     *[Combined Bank Officer (IT) 03.01.2026, BCC ANE 18.10.2025, BPSC 2021]*
  2. **A live video stream will be transmitted. Which Transport layer protocol will you use and why?**  
     *[Microcredit Regulatory Authority AME 2020]*  
     *(স্যারের লেকচার নোট: Page 11-এ হুবহু একই উদাহরণ: Live cricket $\rightarrow$ UDP, Bank transaction $\rightarrow$ TCP)*
  3. **Show the pictorial representation of TCP 3-way handshaking protocol for establishing a connection between a server and a client.**  
     *[BPSC Network/Website Manager 21.05.2025, BRiCM AME 2024/2025, BICIC 2022]*
  4. **The primary function of the Transmission Control Protocol (TCP) is to turn an unreliable network into a reliable network... What are the basic functions performing by TCP?**  
     *[BTRC Assistant Director 2021, Sonali & Janata Bank Officer (IT) 2020]*
  5. **A client needs to send 4000 bytes of data to a database server. The client divides the data into packets of 500 bytes each... TCP cumulative ACK table.**  
     *[BSCCPL AME 21.08.2026]*

#### ৪. সাবটপিক: `## Flow Control & Data Link Layer (Stop-and-Wait) (12)` (লাইন ১১৮৯ – ১২১৪)
> **স্যারের পড়ানোর সাথে মিল:** Flow Control, Data Link Layer, MAC Address, Frame (Page 11, 12)।

* **সরাসরি বিগত সালের লিখিত প্রশ্নসমূহ:**
  1. **Two OSI layers which known as "flow Control" which are those? Write them and explain.**  
     *[Bangladesh Bank Assistant Programmer 2019]*  
     *(উত্তর: Data Link Layer এবং Transport Layer)*
  2. **Unit of data link layer?**  
     *[BCC Assistant Programmer 11.11.2023]*  
     *(উত্তর: Frame — স্যারের Page 12-এর নোট)*
  3. **Using an explanation of the difference between flow-control and congestion control...**  
     *[Combined 2 Bank Officer IT 04.10.2024]*
  4. **What is the piggybacking and MAC Address?**  
     *[BOF Assistant Engineer 2021]*

#### ৫. সাবটপিক: `## Routing Protocols & Route Configuration (19)` (লাইন ৮৮৯ – ৯৫৬)
> **স্যারের পড়ানোর সাথে মিল:** Network Layer-এ Routing ও Shortest Path (Dijkstra's Algorithm) (Page 12)।

* **সরাসরি বিগত সালের লিখিত প্রশ্নসমূহ:**
  1. **Which routing protocol use Dijkstra Algorithm?**  
     *[BARI Assistant Maintenance Engineer 10.05.2024]*  
     *(স্যারের লেকচার নোট: Page 12-এ Dijkstra অ্যালগরিদমের কথা সরাসরি উল্লেখিত)*
  2. **What is Routing? Explain different types of Routing? Which routing algorithm is used in shortest path algorithm?**  
     *[Sonali & Janata Bank Officer (IT) 14.10.2023]*
  3. **What is OSPF? Briefly Explain.**  
     *[DESCO Sub-Assistant Engineer 20.06.2025]*

#### ৬. সাবটপিক: `## Application Layer Protocols & Troubleshooting` (লাইন ৫৯৯ – ৬৪৭)
> **স্যারের পড়ানোর সাথে মিল:** Application Layer Protocols: HTTP, HTTPS, DNS, DHCP, Telnet (Page 9)।

* **সরাসরি বিগত সালের লিখিত প্রশ্নসমূহ:**
  1. **Identify the roles of DNS, DHCP, and HTTPS in communication... troubleshooting steps.**  
     *[BSCCPL AME 21.08.2026]*
  2. **দূরবর্তী কম্পিউটার সংযোগ এর জন্য কোন প্রোটোকল ব্যবহার করা হয়?**  
     *[BPSC Computer Trainer 2021]*  
     *(উত্তর: Virtual Terminal / Telnet — স্যারের Page 9-এর নোট)*
  3. **SMTP, DNS, DHCP, NAT এর কাজ কি লিখ?**  
     *[BTCL Junior Assistant Manager 2022]*

#### ৭. সাবটপিক: `## Email Architecture & Protocols (SMTP, POP3, IMAP) (10)` (লাইন ১২৬১ – ১২৮৪)
> **স্যারের পড়ানোর সাথে মিল:** Application Layer Email Protocols: SMTP, POP3 (Page 9)।

* **সরাসরি বিগত সালের লিখিত প্রশ্নসমূহ:**
  1. **Sinthia wants to send an email to her friend... Mention the protocol of application layer and transport layer.**  
     *[Bangladesh Bank Assistant Director (ICT) 07.02.2025]*
  2. **Distinguish the purpose of SMTP and IMAP in email communication.**  
     *[BPSC Senior Computer Operator 2022]*
  3. **E-mail পাঠানো এবং রিসিভ করার জন্য একটি করে প্রোটোকলের নাম লিখ?**  
     *[PGCB Sub-Assistant Engineer 2021]*

#### ৮. সাবটপিক: `## Application Layer & Well-Known Port Numbers (6)` (লাইন ১২৮৫ – ১২৯৮)
> **স্যারের পড়ানোর সাথে মিল:** Well-known Ports এবং Application Addressing (যেমন: MySQL 3306, HTTP/HTTPS, FTP, SMTP, DNS) (Page 4, 5, 9, 10)।

* **সরাসরি বিগত সালের লিখিত প্রশ্নসমূহ:**
  1. **Full Form and Port Number – SSH, FTP, SMTP, DNS, IMAP.**  
     *[BEPRC Assistant Programmer 08.08.2026]*
  2. **Write the port address of the following applications: (i) HTTP, (ii) HTTPS, (iii) FTP, (iv) SMTP, (v) POP.**  
     *[BPSC Assistant Database Administrator 2022]*
  3. **What is the port number used by DNS? / HTTPS এর পোর্ট নাম্বার কত?**  
     *[BARI AME 2025, BCC AP 2025, BBA AP 2025]*

#### ৯. সাবটপিক: `## Subnetting & IP Addressing` এবং `## IPv6 Addressing (13)`
> **স্যারের পড়ানোর সাথে মিল:** Network Layer Logical Addressing: IPv4 & IPv6 (Page 12)।
