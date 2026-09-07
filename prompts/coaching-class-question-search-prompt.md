# Coaching Class Lecture Analysis & Question Search Prompt

## মূল প্রম্পট (Original Prompt)
```text
Ami ekta coaching korchi, amar porar strategy hochche coaching e ja poray, oi topic ta dhore dekhbo oi topic theke last year e kuno question ashche kina, jodi ashe tobe oi subtopic er shob question pore felbo. Amar coaching sir networking class nise, ami image upload dibo, oi image theke text extract kore tumi prothome ber korbe sir kon kon topic er kon subtopic poraise. Then tumi ei project er "all questions/written" folder e search diba je ei topic, subtopic theke kuno question ase kina. Jodi thake tumi amake corresponding md file and subtopic er nam gula list kore diba. Here is the class lecture images are in this path "E:\Govt job\Networking class" page number 1 theke shuru korbe.
tumi output dibe evabe:
Sir ja ja poraise, topic and subtopic.

then ## ei project er modhdhe ja ja ashchce previous year question theke sir er poranor modhdhe.
```

---

## স্যারের পড়ানো টপিক ও সাবটপিক সারসংক্ষেপ (Lecture Summary: Page 1 - 17 / Class 1 - 3)
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

## ১. Written Questions Mapping (`all-questions/written/`)

### ফাইল ১: `computer-networks.md`
- Subtopic: `OSI & TCP/IP Reference Model (57)`
- Subtopic: `Networking Fundamentals & Terminology (32)`
- Subtopic: `Networking Devices (24)`
- Subtopic: `Application Layer Protocols & Troubleshooting (DNS, DHCP, HTTPS) (23)`
- Subtopic: `Transport Layer (TCP & UDP) (22)`
- Subtopic: `Routing Protocols & Route Configuration (19)`
- Subtopic: `Network Address Translation (NAT) (17)`
- Subtopic: `Flow Control & Data Link Layer (Stop-and-Wait) (12)`
- Subtopic: `Network Services (DHCP, NAT) (11)`
- Subtopic: `Email Architecture & Protocols (SMTP, POP3, IMAP) (10)`
- Subtopic: `Application Layer & Well-Known Port Numbers (6)`

### ফাইল ২: `computer-network-security.md`
- Subtopic: `Social Engineering & Cyber Attacks (32)`
- Subtopic: `Firewalls & Network Defense (20)`
- Subtopic: `Authentication & Access Control (16)`
- Subtopic: `Security Protocols (SSL/TLS, HTTPS) (12)`

---

## ২. MCQ Questions Mapping (`all-questions/mcq/`)

### ফাইল ১: `computer-networks.md`
- Subtopic: `Networking Fundamentals & Terminology (75)`
- Subtopic: `Application Layer Protocols (58)`
- Subtopic: `Network Devices & Configuration (38)`
- Subtopic: `OSI & TCP-IP Model (16)`
- Subtopic: `Routing Protocols (13)`

### ফাইল ২: `computer-network-security.md`
- Subtopic: `Cyber Attacks & Threats (20)`
- Subtopic: `Security Protocols (9)`
