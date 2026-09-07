# Coaching Class Lecture Analysis & Question Search Prompt

## ১. ব্যবহারকারীর রেডি প্রম্পট (User Copy-Paste Prompt)
নতুন কোনো ক্লাসের নোট বা ছবি দেওয়ার সময় নিচের প্রম্পটটি ব্যবহার করুন:

```text
Class notes / images pore prothome chat box-e details-e bolbe sir ki ki poraise (Topic and Subtopic breakdown).
Tarpor ei porar shathe "all-questions" folder-er written ebong mcq file-gular kon kon subtopic common sheta question count shoho chat box-ei list kore dekhabe.
Eigula chat box-e dekhanor por tumi amar permission / OK-er wait korbe.
Ami permission dile tumi "Nipu bhai important topics" folder-er written.md ebong mcq.md update korbe (ekhane 2-column table akare boshbe ebong subtopic question count descending order-e sort thakbe).
```

---

## ২. এআই অ্যাসিস্ট্যান্টের কার্যপ্রণালী (Step-by-Step AI Execution Workflow)

### ধাপ ১: লেকচার বিশ্লেষণ ও চ্যাটবক্সে বিস্তারিত উপস্থাপন
- ব্যবহারকারীর দেওয়া ইমেজ বা নোট থেকে টেক্সট ও কনসেপ্ট উদ্ধার করা।
- চ্যাটবক্সে প্রতিটি টপিক ও সাবটপিক পরিষ্কার ও বিস্তারিতভাবে তুলে ধরা:
  - `Topic: <টপিকের নাম>`
  - `Subtopic: <স্যার ক্লাসে কী পড়িয়েছেন এবং মূল টেকনিক্যাল পয়েন্টের সারসংক্ষেপ>`

### ধাপ ২: কমন সাবটপিক নির্ধারণ ও চ্যাটবক্সে প্রদর্শন
- `all-questions/written/` এবং `all-questions/mcq/` থেকে স্যারের পড়ানো বিষয়ের সাথে হুবহু মিল থাকা সাবটপিকগুলো খুঁজে বের করা।
- অপ্রাসঙ্গিক বা ক্লাসে না পড়ানো কোনো সাবটপিক (যেমন: জটিল ম্যাথ বা অপঠিত অংশ) বাদ রাখা।
- চ্যাটবক্সেই লিখিত ও এমসিকিউ সাবটপিকগুলোর তালিকা প্রশ্নসংখ্যার ভিত্তিতে বড় থেকে ছোট (Descending) সাজিয়ে উপস্থাপন করা:
  - **Written Subtopics (Count Descending)**
  - **MCQ Subtopics (Count Descending)**

### ধাপ ৩: ব্যবহারকারীর অনুমতির অপেক্ষা (Crucial Step)
- চ্যাটবক্সে সম্পূর্ণ বিশ্লেষণ দেওয়ার পর **ফাইলে কোনো কিছু না লিখে ব্যবহারকারীর মতামতের জন্য অপেক্ষা করা**।
- প্রম্পট: *"এই সাবটপিকগুলো কি চূড়ান্ত করবো? আপনার অনুমতি পেলে 'Nipu bhai important topics' ফোল্ডারের ফাইলগুলো আপডেট করবো।"*

### ধাপ ৪: অনুমতি পাওয়ার পর ফাইল আপডেট
- ব্যবহারকারী "OK", "হাঁ", "করো" বা অনুমতি দিলে তবেই ফাইল আপডেট করা:
  1. `Nipu bhai important topics/written.md`
  2. `Nipu bhai important topics/mcq.md`
- **টেবিল ফরম্যাট নিয়ম:**
  - ২ কলামের টেবিল হবে: `| File Name | Subtopic |`
  - কোনো ফাইলের প্রথম সারিতে ফাইলের নাম থাকবে, পরবর্তী সারিগুলোতে ফাইলের ঘরের অংশ ফাঁকা থাকবে।
  - সাবটপিকগুলো ব্র্যাকেটের ভেতরের প্রশ্নসংখ্যা অনুযায়ী বড় থেকে ছোট (Descending) ক্রমানুসারে সাজানো থাকতে হবে।

---

## ৩. এ যাবৎ সম্পন্ন হওয়া লেকচার রেফারেন্স (Lecture History: Class 1 - 3)

### স্যারের পড়ানো মূল বিষয়সমূহ (Topics 1 - 19):
1. **Networking Fundamentals & Devices:** Intranet vs Internet, End-user devices (PC, printer, server, smartphone), Intermediary devices (Router, Wireless router, Cell tower, Modem, Internet cloud), Hub (insecure broadcast) vs Switch (secure MAC unicast), Enterprise core switch hierarchy (Access switch $\rightarrow$ Core switch $\rightarrow$ Router $\rightarrow$ Internet).
2. **Enterprise Security & Zero Trust Architecture:** Zero Trust Architecture ("Never trust, always verify"), 11টি কোর ডিভাইস (Firewall, Switch, IPS, IDS, Anti-DDoS, WAF, Web Server, Database Server, Storage SAN, SIEM / Monitoring).
3. **Network Architecture Evolution & DMZ:** Old flat network vs Hardware firewall vs Modern 3-tier DMZ architecture (DMZ, User Network, Server Network).
4. **Hacker-Resilient DMZ Architecture:** Public DMZ zone (WAF, Web Server), Internal Firewall (Strict policy: Allow 3306, ALL DENY), Isolated secure database server zone.
5. **Defense in Depth & Firewalls:** Defense in depth layered security, Traditional packet filtering (Header & Footer) vs Next-Generation Firewall / NGFW (Deep packet inspection, Payload, SSL Decryption), WAF core functions (Reverse proxy/Public IP hide, malicious traffic blocking, web attack mitigation like SQLi/XSS, load balancing).
6. **Anti-DDoS & Multi-layer Filtering:** DDoS flood traffic characteristics, Multi-layer security pipeline (Anti-DDoS $\rightarrow$ Perimeter Firewall $\rightarrow$ WAF $\rightarrow$ Web Server $\rightarrow$ Internal Firewall $\rightarrow$ Database Server).
7. **End-to-End Enterprise Flow & Asset Valuation:** Internet to DB architecture, Database as a High-value asset (Crown jewel).
8. **Security Operations & Architecture:** High Availability (HA) NGFW, DMZ (WAF $\rightarrow$ Load Balancer $\rightarrow$ Web Server $\rightarrow$ IDS/IPS $\rightarrow$ SIEM $\rightarrow$ SOC), VPN Gateway, Internal Core Switch.
9. **OSI Layer 7 - Application Layer:** HTTP, HTTPS, FTP, SMTP, POP3, DHCP, Telnet (Virtual Terminal).
10. **OSI Layer 6 - Presentation Layer:** Character translation (ASCII $\rightarrow$ EBCDIC), Data compression (Huffman coding), Encryption & Decryption (SSL).
11. **OSI Layer 5 - Session Layer:** Authentication ("Who are you?"), Authorization ("Permissions: Admin vs Guest"), Session state management.
12. **OSI Layer 4 - Transport Layer:** Segmentation (IP + Port, e.g. 3306), Flow control (speed/rate matching), Error control (ARQ - Automatic Repeat reQuest), TCP vs UDP comparison (Reliable bank transactions vs Live video streaming).
13. **OSI Layer 3 - Network Layer:** Logical addressing (IPv4, IPv6), Routing protocols, Shortest path algorithms (Dijkstra algorithm).
14. **OSI Layer 2 - Data Link Layer:** Physical addressing (MAC address, Frame structure), PDU relationship (Segment $\rightarrow$ Packet $\rightarrow$ Frame $\rightarrow$ Bit).
15. **End-to-End Packet Traversal (PC to Singapore Server):** End-to-end packet route (PC $\rightarrow$ Switch $\rightarrow$ Firewall $\rightarrow$ Internal Router $\rightarrow$ ISP $\rightarrow$ Singapore Server), Key networking axiom: IP remains unchanged end-to-end; MAC address changes at every router/switch hop.
16. **Network Address Translation (NAT) / Netting:** Private to public IP conversion in router, Port Address Translation (PAT) for multiplexing connections.
17. **Domain Name System (DNS) & Query Tools:** Domain name to IP translation, CLI tools: `nslookup` (Windows) and `dig` (Linux).
18. **DNS Name Resolution Process (Recursive vs. Iterative):** Recursive query cycle (Browser $\rightarrow$ Local DNS $\rightarrow$ Root DNS $\rightarrow$ TLD DNS $\rightarrow$ Authoritative DNS $\rightarrow$ Local DNS $\rightarrow$ Browser), DNS caching mechanism for instant subsequent responses.
19. **Core Application Layer Protocols Focus:** High-priority exam protocols: DHCP, DNS, RTP, HTTP, HTTPS.

---

## ৪. বর্তমান অ্যাক্টিভ সাবটপিক ম্যাপিং (Current Active Subtopic Mapping)

### ১. Written (`all-questions/written/`)
- **`computer-networks.md`**:
  - OSI & TCP/IP Reference Model (57)
  - Networking Fundamentals & Terminology (32)
  - Networking Devices (24)
  - Application Layer Protocols & Troubleshooting (DNS, DHCP, HTTPS) (23)
  - Transport Layer (TCP & UDP) (22)
  - Routing Protocols & Route Configuration (19)
  - Network Address Translation (NAT) (17)
  - Flow Control & Data Link Layer (Stop-and-Wait) (12)
  - Network Services (DHCP, NAT) (11)
  - Email Architecture & Protocols (SMTP, POP3, IMAP) (10)
  - Application Layer & Well-Known Port Numbers (6)
- **`computer-network-security.md`**:
  - Social Engineering & Cyber Attacks (32)
  - Firewalls & Network Defense (20)
  - Authentication & Access Control (16)
  - Security Protocols (SSL/TLS, HTTPS) (12)

### ২. MCQ (`all-questions/mcq/`)
- **`computer-networks.md`**:
  - Networking Fundamentals & Terminology (75)
  - Application Layer Protocols (58)
  - Network Devices & Configuration (38)
  - OSI & TCP-IP Model (16)
  - Routing Protocols (13)
- **`computer-network-security.md`**:
  - Cyber Attacks & Threats (20)
  - Security Protocols (9)
