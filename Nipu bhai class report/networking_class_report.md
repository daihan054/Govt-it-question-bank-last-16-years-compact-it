## Sir ja poraise

1) Networking Fundamentals & Devices:<br>
   i) Intranet vs. Internet: ইন্ট্রানেট (প্রাইভেট লোকাল নেটওয়ার্ক) এবং ইন্টারনেটের (পাবলিক গ্লোবাল নেটওয়ার্ক) মধ্যকার মৌলিক পার্থক্য ও ব্যবহার।<br>
   ii) End-User Devices: ইউজার সরাসরি ব্যবহার করে এমন টার্মিনাল ডিভাইস যেমন PC, Printer, Server, Smartphone ইত্যাদি।<br>
   iii) Intermediary Devices: ডেটা আদান-প্রদানে মধ্যবর্তী সহায়ক ডিভাইস যেমন Router, Wireless Router, Cell Tower, Modem, Internet Cloud।<br>
   iv) Small Network Architecture (Hub vs. Switch): ছোট অফিসে হাব বনাম সুইচ—হাব হলো ইনসিকিউর/ব্রডকাস্ট ডিভাইস, পক্ষান্তরে সুইচ হলো সিকিউর যা নির্দিষ্ট MAC অ্যাড্রেস দেখে ইউনিটি বা ইউনিকাস্ট ফ্রেম পাঠায়।<br>
   v) Enterprise Network Architecture: বড় কোম্পানির ক্ষেত্রে একাধিক অ্যাক্সেস সুইচ (যেমন ৪৮-পোর্টের Switch-1, Switch-2) কোর সুইচের সাথে এবং কোর সুইচ পেরিমিটার রাউটার হয়ে ইন্টারনেটে যুক্ত থাকে।<br>

2) Enterprise Security Devices & Architecture:<br>
   i) 11 Core Enterprise Devices: ওয়ার্ল্ড ব্যাংকের মতো বড় সংস্থায় ব্যবহৃত ১১টি প্রধান ডিভাইস (PCs, Firewall, Switch, IPS, IDS, Anti-DDoS, WAF, Web Server, Database Server, Storage SAN, SIEM/Monitoring)।<br>
   ii) Zero Trust Architecture: আধুনিক সিকিউর নেটওয়ার্ক ডিজাইনের দর্শন যেখানে "কাউকেই ডিফল্টভাবে বিশ্বাস না করে সবসময় যাচাই" (Never trust, always verify) নীতি অনুসরণ করা হয়।<br>

3) Network Architecture Evolution & DMZ:<br>
   i) Old Flat Network: পুরনো আর্কিটেকচার যেখানে ফায়ারওয়ালের পেছনে একই নেটওয়ার্কে ইউজার, সার্ভার ও ডেটাবেজ থাকত, যা অত্যন্ত অনিরাপদ ও এক পিসি আক্রান্ত হলেই সব কম্প্রোমাইজড হতো।<br>
   ii) Perimeter Hardware Firewall: ইউজার সুইচের বাইরে নেটওয়ার্ক পেরিমিটারে ডেডিকেটেড হার্ডওয়্যার ফায়ারওয়াল স্থাপন।<br>
   iii) Modern 3-Tier Architecture: আধুনিক নেটওয়ার্কে ফায়ারওয়ালের পেছনে ট্রাফিক ৩টি পৃথক জোনে বিভক্ত (DMZ, User Network এবং Apps/DB সমন্বিত Server Network)।<br>

4) Hacker-Resilient Multi-tier DMZ Architecture:<br>
   i) Demilitarized Zone (DMZ): ইন্টারনেটমুখী পাবলিক-ফেসিং বাফার জোন যেখানে WAF এবং Web Server (Web, Email, Mobile ট্রাফিকের জন্য) অবস্থান করে।<br>
   ii) Internal Firewall: DMZ এবং মূল ডেটাবেজ জোনের মাঝে বসানো দ্বিতীয় ফায়ারওয়াল যা ভেতরের সিকিউর নেটওয়ার্ককে আলাদা রাখে।<br>
   iii) Database Server Isolation: ডেটাবেজকে ইন্টারনেটের সাথে কোনো সরাসরি সংযোগ না রেখে সর্বোচ্চ সুরক্ষিত অভ্যন্তরীণ জোনে রাখা।<br>
   iv) Port-based Access Filtering: ইন্টারনাল ফায়ারওয়ালে কঠোর রুল সেট করা (শুধুমাত্র অনুমোদিত MySQL Port 3306 অ্যালাউ, বাকি সব রিকোয়েস্ট ALL DENY)।<br>

5) Defense in Depth & Firewall Technologies:<br>
   i) Defense in Depth: স্তরভিত্তিক নিরাপত্তা নীতি—DMZ-এর ওয়েব সার্ভার হ্যাক হলেও ইন্টারনাল ফায়ারওয়ালের কঠোর পলিসির কারণে আক্রমণকারী যেন ডেটাবেজে পৌঁছাতে না পারে।<br>
   ii) Traditional Packet Filtering Firewall: পুরনো ফায়ারওয়াল যা শুধু প্যাকেটের হেডার ও ফুটার (IP, Port, Protocol) দেখে ট্রাফিক ফিল্টার করে।<br>
   iii) Next-Generation Firewall (NGFW): আধুনিক ফায়ারওয়াল যা ডিপ প্যাকেট ইন্সপেকশন (DPI), অ্যাপ্লিকেশন অ্যাওয়ারনেস, সম্পূর্ণ পেলোড (Payload) এবং এনক্রিপশন/ডিক্রিপশন চেক করতে পারে।<br>
   iv) Web Application Firewall (WAF) Functions: অ্যাপ্লিকেশন লেয়ারের সুরক্ষা—ব্যাকএন্ড পাবলিক আইপি গোপন রাখা (Reverse Proxy), ক্ষতিকর ওয়েব ট্রাফিক ব্লক, ওয়েব স্ক্রিপ্ট অ্যাটাক (SQL Injection, XSS) প্রতিহত করা এবং লোড ব্যালান্সিং।<br>

6) Anti-DDoS Protection & Multi-Layer Filtering:<br>
   i) DDoS Flood Traffic Characteristics: বট বা সফটওয়্যার জেনারেটেড ভুয়া ও অতিরিক্ত রিকোয়েস্টের বন্যা যার কোনো বৈধ হেডার/ফুটার উদ্দেশ্য থাকে না এবং লক্ষ্য থাকে সার্ভার ডাউন করা।<br>
   ii) Anti-DDoS Hardware Filtering: ট্রাফিক মূল ফায়ারওয়ালে পৌঁছানোর আগেই স্পেশালাইজড অ্যান্টি-ডিডস ডিভাইসের মাধ্যমে গারবেজ ট্রাফিক ছেঁকে ফেলা।<br>
   iii) Multi-Layer Security Pipeline: বহুস্তরী ফিল্টারিং পাইপলাইন (Filter 1: Anti-DDoS -> Filter 2: Perimeter Firewall -> Filter 3: WAF -> Web Server -> Filter 4: Internal Firewall -> Database Server)।<br>

7) End-to-End Enterprise Flow & Asset Valuation:<br>
   i) Internet to Database Architecture Flow: এন্ড-টু-এন্ড ট্রাফিক প্রবাহ (Internet -> Anti-DDoS -> Firewall -> WAF -> Load Balancer -> Web Servers -> App Server -> Internal Firewall -> Database Server)।<br>
   ii) Database Asset Classification: ডেটাবেজ কোনো সাধারণ এসেট নয়, এটি প্রতিষ্ঠানের সবচেয়ে মূল্যবান সম্পদ বা "High-Value Asset" (Crown Jewel)।<br>

8) SOC, SIEM & Security Architecture:<br>
   i) High Availability (HA) Firewall: সিঙ্গেল পয়েন্ট অফ ফেইলিউর রোধ করতে পেরিমিটার ফায়ারওয়াল হাই অ্যাভেইলেবিলিটি রিডানড্যান্ট মোডে কনফিগার করা।<br>
   ii) IDS/IPS Log Analysis: ইন্ট্রুশন ডিটেকশন ও প্রিভেনশন সিস্টেম সফটওয়্যার যা সন্দেহজনক কার্যকলাপ শনাক্তে নেটওয়ার্ক লগ বিশ্লেষণ করে।<br>
   iii) SIEM Log Monitoring: পুরো নেটওয়ার্কের বিভিন্ন ডিভাইসের ইভেন্ট লগ কেন্দ্রীয়ভাবে সংগ্রহ ও অ্যানালাইসিস করার সিস্টেম (Security Information and Event Management)।<br>
   iv) SOC Monitoring: সিকিউরিটি অপারেশন সেন্টারে (SOC) অ্যানালিস্টদের দ্বারা রিয়েল-টাইম থ্রেট মনিটরিং ও রেসপন্স।<br>
   v) VPN Gateway: রিমোট ইউজার ও শাখা অফিসগুলোর জন্য এনক্রিপ্টেড ও সুরক্ষিত ভার্চুয়াল প্রাইভেট নেটওয়ার্ক টানেল নিশ্চিত করা।<br>

9) OSI Application Layer (Layer 7):<br>
   i) OSI 7 Layers Model Overview: ওএসআই রেফারেন্স মডেলের ৭টি স্তরের ক্রম ও সংক্ষেপ রূপ (PDNTSPA: Physical, Data Link, Network, Transport, Session, Presentation, Application)।<br>
   ii) Interface with Network Applications: বিভিন্ন এন্ড-ইউজার সফটওয়্যার ও ওয়েব ব্রাউজার (Chrome, Firefox) নেটওয়ার্কে কমিউনিকেশন করার জন্য এই লেয়ার ব্যবহার করে।<br>
   iii) Application Layer Protocols: বিভিন্ন সেবার প্রোটোকল—ওয়েব ব্রাউজিংয়ের জন্য HTTP/HTTPS, ফাইল ট্রান্সফারের জন্য FTP, ইমেইলের জন্য SMTP/POP3 এবং অটো আইপি পাওয়ার জন্য DHCP।<br>
   iv) Virtual Terminal Protocol: দূরবর্তী সার্ভার বা নেটওয়ার্ক ডিভাইসে রিমোটলি কমান্ড-লাইন অ্যাক্সেসের জন্য Telnet প্রোটোকল।<br>

10) OSI Presentation Layer (Layer 6):<br>
    i) Character Translation & Binary Encoding: বিভিন্ন অপারেটিং সিস্টেমের ডেটা ফরম্যাট ও ক্যারেক্টার এনকোডিংকে মেশিনের বোধগম্য বাইনারিতে রূপান্তর (যেমন ASCII থেকে EBCDIC)।<br>
    ii) Data Compression Algorithms: ব্যান্ডউইথ সাশ্রয়ের জন্য ট্রান্সমিশনের আগে ডেটার সাইজ কমানো (যেমন Huffman Coding অ্যালগরিদম ব্যবহার)।<br>
    iii) Encryption & Decryption: ট্রানজিটে ডেটার গোপনীয়তা রক্ষায় প্রেজেন্টেশন লেয়ারে SSL (Secure Sockets Layer) প্রোটোকলের মাধ্যমে এনক্রিপশন ও ডিক্রিপশন সম্পাদন।<br>

11) OSI Session Layer (Layer 5):<br>
    i) Authentication: যোগাযোগ শুরুর আগে ব্যবহারকারী আসলেই কে তা নিশ্চিত করা ("Who are you?")।<br>
    ii) Authorization: ব্যবহারকারী শনাক্ত হওয়ার পর তার সিস্টেমে কী কী সুবিধা পাওয়ার অনুমতি রয়েছে তা নির্ধারণ ("Admin vs. Guest access permissions")।<br>
    iii) Session Management & State Tracking: একাধিক অ্যাপ্লিকেশন ও ডেটার সেশন স্থাপন, পরিচালনা ও সমাপ্তি ট্র্যাক রাখা।<br>
    iv) Browser-managed Upper Layers: ওয়েব ব্রাউজার মূলত উপরের ৩টি লেয়ারই (Application, Presentation, Session) সমন্বিতভাবে পরিচালনা করে।<br>

12) OSI Transport Layer (Layer 4):<br>
    i) Data Segmentation & Port Addressing: বড় ডেটাকে ছোট ছোট সেগমেন্টে বিভক্ত করা এবং আইপি ও পোর্ট নম্বরের সমন্বয়ে নির্দিষ্ট অ্যাপ্লিকেশন শনাক্তকরণ (যেমন MySQL এর জন্য localhost:3306)।<br>
    ii) Flow Control: প্রেরক ও প্রাপক ডিভাইসের গতির বৈষম্য দূর করতে ডেটা প্রেরণের হার নিয়ন্ত্রণ (যেমন সার্ভার 100 Mbps-এ পাঠালেও রিসিভিং ফোন যেন 20 Mbps-এ ড্রপ ছাড়া গ্রহণ করতে পারে)।<br>
    iii) Error Control: ডেটা লস হলে বা নষ্ট হলে ARQ (Automatic Repeat reQuest) প্রক্রিয়ার মাধ্যমে পুনরায় ডেটা চাওয়ার ব্যবস্থা।<br>
    iv) TCP vs. UDP Protocol Comparison: টিসিপি হলো কানেকশন-ওরিয়েন্টেড ও নির্ভরযোগ্য যা শতভাগ নির্ভুলতার ক্ষেত্রে প্রয়োজন (যেমন ব্যাংকিং লেনদেন), আর ইউডিপি হলো কানেকশনলেস ও দ্রুতগতির যা সাময়িক প্যাকেট লস হলেও চলে (যেমন লাইভ ক্রিকেট স্ট্রিমিং)।<br>

13) OSI Network Layer (Layer 3):<br>
    i) Logical Addressing: নেটওয়ার্কে হোস্ট শনাক্তকরণে লজিক্যাল আইপি অ্যাড্রেসিং (IPv4 ও IPv6) এবং সেগমেন্টের সাথে সোর্স ও ডেস্টিনেশন আইপি যোগ করে প্যাকেট তৈরি করা।<br>
    ii) Routing & Path Determination: এক নেটওয়ার্ক থেকে অন্য নেটওয়ার্কে প্যাকেট পৌঁছানোর সর্বোত্তম রুট নির্ধারণ।<br>
    iii) Shortest Path Routing Algorithm: রাউটিং প্রোটোকলে (যেমন OSPF) সবচেয়ে কম দূরত্বের পথ খুঁজে পেতে Dijkstra's Algorithm ব্যবহার।<br>

14) OSI Data Link Layer (Layer 2) & PDU Hierarchy:<br>
    i) Physical Addressing: লোকাল নেটওয়ার্কে নোড-টু-নোড ডেলিভারির জন্য হার্ডওয়্যার MAC Address যুক্ত করে প্যাকেটকে ফ্রেমে (Frame) রূপান্তর।<br>
    ii) PDU Hierarchy: লেয়ারভেদে ডেটার প্রোটোকল ডেটা ইউনিট বা পিডিইউ রূপান্তর ক্রম—Data -> Segment (Transport) -> Packet (Network) -> Frame (Data Link) -> Bit (Physical)।<br>
    iii) Firewall Inspection Level: ট্র্যাডিশনাল প্যাকেট ফিল্টারিং ফায়ারওয়াল সাধারণত ফ্রেম/প্যাকেট হেডার চেক করে, আর আধুনিক NGFW পুরো পেলোড পর্যন্ত ইনস্পেকশন করে।<br>

15) End-to-End Packet Traversal (PC to Singapore Server):<br>
    i) End-to-End Packet Flow: পিসি থেকে সিঙ্গাপুর সার্ভার পর্যন্ত সম্পূর্ণ ট্রাফিক রুট (PC -> Switch -> Firewall -> Internal Router -> BTCL ISP -> International Backbone -> Singapore ISP -> Datacenter Router -> Datacenter Firewall -> Server)।<br>
    ii) IP vs. MAC Address Behavior in Transmission: ডেটা ট্রান্সমিশনে পুরো জার্নিতে সোর্স ও ডেস্টিনেশন IP অ্যাড্রেস অপরিবর্তিত থাকে, কিন্তু প্রতি হপে (রাউটার/সুইচ পার হওয়ার সময়) MAC অ্যাড্রেস পরিবর্তিত হয়।<br>

16) Network Address Translation (NAT) / Netting:<br>
    i) NAT & Netting Concept: প্রাইভেট লোকাল আইপি দিয়ে ইন্টারনেট ব্রাউজ করতে রাউটারে পাবলিক আইপিতে রূপান্তর (Netting) এবং রেসপন্স প্যাকেট আসলে মূল অভ্যন্তরীণ প্রাইভেট আইপি শনাক্ত করে পাঠানো।<br>
    ii) Port Address Translation (PAT): একটি সিঙ্গেল পাবলিক আইপি ব্যবহার করে পোর্টের সাহায্যে একাধিক লোকাল পিসির ট্রাফিক ম্যাপ করা।<br>

17) Domain Name System (DNS) & Query Tools:<br>
    i) Browser & DNS Interaction: ব্যবহারকারী ব্রাউজারে ডোমেইন নাম লিখলে অ্যাপ্লিকেশন লেয়ারে DNS সার্ভার সেই ডোমেইনের বিপরীতে সংশ্লিষ্ট আইপি অ্যাড্রেস এনে দেয়।<br>
    ii) DNS Query CLI Commands: ডিএনএস কুয়েরি ও আইপি রিজলভিং চেক করার কমান্ড—উইন্ডোজে `nslookup` এবং লিনাক্সে `dig` (যেমন: `nslookup www.ittefaq.com.bd`, `dig www.ittefaq.com.bd`)।<br>

18) DNS Name Resolution Process (Recursive vs. Iterative):<br>
    i) Recursive DNS Resolution: ক্লায়েন্ট ব্রাউজার রিকোয়েস্ট পাঠায় Local/ISP DNS-এ -> Root DNS Server (বিশ্বব্যাপী ১৩টি) -> TLD DNS Server (.org/.com) -> Authoritative DNS Server -> আইপি নিয়ে ব্রাউজারে ফেরত আসে।<br>
    ii) Iterative DNS Resolution: লোকাল রিজলভার নিজেই প্রতিটি স্তরের ডিএনএস সার্ভারকে আলাদা আলাদা কুয়েরি করে রেফারাল অনুযায়ী ধাপে ধাপে আইপি সংগ্রহ করে।<br>
    iii) DNS Caching Mechanism: প্রথমবার রিকোয়েস্টে সম্পূর্ণ হায়ারার্কি ঘুরে আইপি বের করতে হলেও পরবর্তী রিকোয়েস্টে লোকাল ডিএনএস ক্যাশ (Cache) থেকে সাথে সাথে আইপি সরবরাহ করা হয়।<br>

19) Core Application Layer Protocols Focus:<br>
    i) Exam Focus Protocols: লিখিত ও এমসিকিউ পরীক্ষার জন্য অ্যাপ্লিকেশন লেয়ারের অতি গুরুত্বপূর্ণ প্রোটোকল—DHCP, DNS, RTP, HTTP, HTTPS।<br>

---

## all-questions/Written.md file e ja paoa gese

1) computer-networks.md (Computer Networks):<br>
   i) OSI & TCP/IP Reference Model (57)<br>
   ii) Networking Fundamentals & Terminology (32)<br>
   iii) Networking Devices (24)<br>
   iv) Application Layer Protocols & Troubleshooting (DNS, DHCP, HTTPS) (23)<br>
   v) Transport Layer (TCP & UDP) (22)<br>
   vi) Routing Protocols & Route Configuration (19)<br>
   vii) Network Address Translation (NAT) (17)<br>
   viii) Flow Control & Data Link Layer (Stop-and-Wait) (12)<br>
   ix) Network Services (DHCP, NAT) (11)<br>
   x) Email Architecture & Protocols (SMTP, POP3, IMAP) (10)<br>
   xi) Application Layer & Well-Known Port Numbers (6)<br>

2) computer-network-security.md (Computer Network Security):<br>
   i) Social Engineering & Cyber Attacks (32)<br>
   ii) Firewalls & Network Defense (20)<br>
   iii) Authentication & Access Control (16)<br>
   iv) Security Protocols (SSL/TLS, HTTPS) (12)<br>

---

## all-questions/mcq.md file e ja paoa gese:

1) computer-networks.md (Computer Networks):<br>
   i) Networking Fundamentals & Terminology (75)<br>
   ii) Application Layer Protocols (58)<br>
   iii) Network Devices & Configuration (38)<br>
   iv) OSI & TCP-IP Model (16)<br>
   v) Routing Protocols (13)<br>

2) computer-network-security.md (Computer Network Security):<br>
   i) Cyber Attacks & Threats (20)<br>
   ii) Security Protocols (9)<br>
