## Sir ja poraise

1. Networking Fundamentals & Devices:
   i) Intranet vs. Internet এর মৌলিক ধারণা
   ii) End-User Devices (PC, Printer, Server, Smartphone)
   iii) Intermediary Devices (Router, Wireless Router, Cell Tower, Modem, Internet Cloud)
   iv) Small Network Architecture (Hub vs. Switch: Hub insecure broadcast, Switch secure MAC-based unicast)
   v) Enterprise Network Architecture (Access switch -> Core switch -> Perimeter router -> Internet)

2. Enterprise Security Devices & Architecture:
   i) 11 Core Devices (PCs, Firewall, Switch, IPS, IDS, Anti-DDoS, WAF, Web Server, Database Server, Storage SAN, SIEM/Monitoring)
   ii) Zero Trust Architecture ("Never trust, always verify" মডেল)

3. Network Architecture Evolution & DMZ:
   i) Old Flat Network (User + Server + DB একই জোনে থাকার ঝুঁকি)
   ii) Perimeter Hardware Firewall Placement
   iii) Modern 3-Tier Architecture (DMZ, User Network, Server Network)

4. Hacker-Resilient Multi-tier DMZ Architecture:
   i) Demilitarized Zone (DMZ) - Public-facing Web, Email, Mobile servers
   ii) Internal Firewall Placement & Rule Configuration
   iii) Database Server Isolation in Secure Zone (No direct internet access)
   iv) Port-based Access Filtering (Allow only MySQL Port 3306, ALL DENY)

5. Defense in Depth & Firewall Technologies:
   i) Defense in Depth (স্তরভিত্তিক নিরাপত্তা কাঠামো)
   ii) Traditional Packet Filtering Firewall (Header & Footer check)
   iii) Next-Generation Firewall / NGFW (Deep packet inspection, Payload, SSL Decryption)
   iv) Web Application Firewall (WAF) Functions (Reverse proxy/Public IP hide, Malicious traffic blocking, Web attack mitigation like SQLi/XSS, Load balancing)

6. Anti-DDoS Protection & Multi-Layer Filtering:
   i) DDoS Flood Traffic Characteristics (Software-generated garbage packets)
   ii) Anti-DDoS Hardware Filtering before firewall
   iii) Multi-Layer Security Pipeline (Anti-DDoS -> Firewall -> WAF -> Web Server -> Internal Firewall -> Database Server)

7. End-to-End Enterprise Flow & Asset Valuation:
   i) Internet to Database Architecture Flow (Anti-DDoS -> Firewall -> WAF -> Load Balancer -> Web Servers -> App Server -> Internal Firewall -> Database Server)
   ii) Database Asset Classification (High-Value Asset / Crown Jewel)

8. SOC, SIEM & Security Architecture:
   i) High Availability (HA) Firewall Configuration
   ii) IDS/IPS Log Analysis Software
   iii) SIEM (Security Information and Event Management) Log Monitoring
   iv) SOC (Security Operations Center) Incident Response
   v) VPN Gateway for Secure Remote Access

9. OSI Application Layer (Layer 7):
   i) OSI 7 Layers Model Overview (PDNTSPA)
   ii) Interface with Network Applications (Chrome, Firefox, etc.)
   iii) Application Layer Protocols (HTTP, HTTPS, FTP, SMTP, POP3, DHCP)
   iv) Virtual Terminal Protocol (Telnet)

10. OSI Presentation Layer (Layer 6):
    i) Character Translation & Binary Encoding (ASCII to EBCDIC)
    ii) Data Compression Algorithms (Huffman Coding)
    iii) Encryption & Decryption (SSL - Secure Sockets Layer Protocol)

11. OSI Session Layer (Layer 5):
    i) Authentication ("Who are you?")
    ii) Authorization ("Access Permissions: Admin vs Guest")
    iii) Session Management & State Tracking
    iv) Browser-managed Upper Layers (Application, Presentation, Session)

12. OSI Transport Layer (Layer 4):
    i) Data Segmentation & Port Addressing (IP + Port combination)
    ii) Flow Control (Rate matching between sender and receiver)
    iii) Error Control (ARQ - Automatic Repeat reQuest)
    iv) TCP vs. UDP Protocol Comparison (Reliable/Bank Transaction vs. Fast/Live Streaming)

13. OSI Network Layer (Layer 3):
    i) Logical Addressing (IPv4, IPv6, Packet Encapsulation)
    ii) Routing & Path Determination
    iii) Shortest Path Algorithms (Dijkstra's Algorithm)

14. OSI Data Link Layer (Layer 2) & PDU Hierarchy:
    i) Physical Addressing (MAC Address & Frame Structure)
    ii) PDU Hierarchy (Segment -> Packet -> Frame -> Bit)
    iii) Firewall Inspection Level (Packet vs. Frame)

---

## all-questions/Written.md file e ja paoa gese

1) computer-networks.md (Computer Networks):
   i) OSI & TCP/IP Reference Model (57)
   ii) Networking Devices (24)
   iii) Transport Layer (TCP & UDP) (22)
   iv) Flow Control & Data Link Layer (Stop-and-Wait) (12)
   v) Routing Protocols & Route Configuration (19)
   vi) Application Layer Protocols & Troubleshooting (DNS, DHCP, HTTPS) (23)
   vii) Email Architecture & Protocols (SMTP, POP3, IMAP) (10)
   viii) Application Layer & Well-Known Port Numbers (6)
   ix) Networking Fundamentals & Terminology (32)
   x) Subnetting & IP Addressing (119)
   xi) IPv6 Addressing (13)
   xii) Switching Techniques (Circuit vs Packet Switching) (5)
   xiii) High Availability & Redundancy Protocols (VRRP, HSRP) (1)

2) computer-network-security.md (Computer Network Security):
   i) Firewalls & Network Defense (20)
   ii) Social Engineering & Cyber Attacks (32)
   iii) Security Protocols (SSL/TLS, HTTPS) (12)
   iv) Authentication & Access Control (16)
   v) Web Security Vulnerabilities (19)
   vi) VPN & Tunneling Protocols (IPsec, SSL VPN) (6)

---

## all-questions/mcq.md file e ja paoa gese:

1) computer-networks.md (Computer Networks):
   i) OSI & TCP-IP Model (16)
   ii) Network Devices & Configuration (38)
   iii) Application Layer Protocols (58)
   iv) Routing Protocols (13)
   v) Networking Fundamentals & Terminology (75)
   vi) Subnetting & IP Addressing (33)
   vii) IPv6 Addressing (13)
   viii) Switching Techniques (3)

2) computer-network-security.md (Computer Network Security):
   i) Cyber Attacks & Threats (20)
   ii) Security Protocols (9)
   iii) Web Security Vulnerabilities (4)
   iv) Email Security & Spam (2)
   v) Security Principles (CIA Triad) (5)
