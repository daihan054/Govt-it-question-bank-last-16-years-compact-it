<!-- TOC START -->
**Table of Contents** — 14 subtopics · 184 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Social Engineering & Cyber Attacks](#social-engineering--cyber-attacks-32) | 32 |
| 2 | [Cryptography](#cryptography-31) | 31 |
| 3 | [Firewalls & Network Defense](#firewalls--network-defense-20) | 20 |
| 4 | [Malware & Security Threats](#malware--security-threats-20) | 20 |
| 5 | [Web Security Vulnerabilities](#web-security-vulnerabilities-19) | 19 |
| 6 | [Authentication & Access Control](#authentication--access-control-16) | 16 |
| 7 | [Security Protocols (SSL/TLS, HTTPS)](#security-protocols-ssltls-https-12) | 12 |
| 8 | [Cyber Crime & Security](#cyber-crime--security-10) | 10 |
| 9 | [Security Principles (CIA Triad)](#security-principles-cia-triad-8) | 8 |
| 10 | [VPN & Tunneling Protocols (IPsec, SSL VPN)](#vpn--tunneling-protocols-ipsec-ssl-vpn-6) | 6 |
| 11 | [Critical Information Infrastructure (CII) & Cyber Governance](#critical-information-infrastructure-cii--cyber-governance-3) | 3 |
| 12 | [Cryptography & Network Security Scenarios](#cryptography--network-security-scenarios-3) | 3 |
| 13 | [Email & Messaging Security (Spam, Phishing)](#email--messaging-security-spam-phishing-3) | 3 |
| 14 | [Buffer Overflow & Software Vulnerabilities](#buffer-overflow--software-vulnerabilities-1) | 1 |

<!-- TOC END -->

---

## Social Engineering & Cyber Attacks (32)

1. What is a phishing attack? Explain its types and discuss methods to prevent it. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

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

1. Explain the operational difference between Hashing and Encryption. [SO IT 25-07-2026] *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 701 (ET: BUET)], [BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*

2. Explain the concepts of encryption and decryption with an example. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

3. What is social engineering? What is hashing? How is it different from encryption? *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*

4. **What is Encryption? What are the types? Explain the role of Encryption in security.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

5. **Write the differences among encryption, hashing, and digital signatures. Mention their uses in cybersecurity.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

6. **How many bits MD5 encryption?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

7. **What type of key used for decrypt message of PKI?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

8. **6.2 Explain the operational difference between Hashing and Encryption.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

9. **Breifly Explain Asymmetric encryption.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 501 (ET: N/A)]*

10. **Distinguish between Symmetric Encryption and Asymmetric Encryption. Give some examples of encryption algorithm. What are the different types of ciphers in cryptography? What are the factors to be considered for cryptographic strength?** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 533 (ET: MIST)]*

11. **What is Symmetric and Asymmetric Encryption? Explain with example.** *[NPCBL Executive Trainee (Software) 26.05.2023 compact it 499 (ET: IBA)]*

12. **What is symmetric and Asymmetric key explain with example?** *[Mongla Port Authority Assistant Programmer 2023 compact it 573 (ET: N/A)]*

13. **What is Cryptography? Difference between Symmetric and Asymmetric encryption with example. Draw and design public key encryption using Hash function. Draw a diagram for e-commerce online transactions.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 512 (ET: MIST)]*

14. **The high level method of DES...** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 450 (ET: BUET)]*

15. **Difference between symmetric and asymetric key encryption.** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*

16. **Identify the type of algorithm? (i) MD5 (ii) AES (iii) RSA (iv) Diffie-Hellman** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 461 (ET: BUET)]*

17. **Describe RSA Algorithm and how it works?** *[Teletalk Assistant Manager (IT) 2023 compact it 467 (ET: N/A)]*

18. **অথবা, (ক) Private key এবং Public key উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 614 (ET: N/A)]*

19. **(খ) Plaintext ও Cipher text এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 614 (ET: N/A)]*

20. **What is SHA-256 and SHA-512 in network security, what is avalanche effect, is it desirable or undesirable.** *[RPGCL Assistant Manager (ICT) 2022 compact it 655 (ET: BUET)]*

21. **(ii) Symmetric Key Encryption and Asymmetric Key Encryption ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 790 (ET: N/A)]*

22. **(a) What is meant by Encryption and Decryption?** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 796 (ET: N/A)]*

23. **Difference between private key and public key.** *[BCC CA Monitoring System Project 2021 compact it 829 (ET: N/A)]*

24. **Write two symmetric key algorithm name.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 859 (ET: N/A)]*

25. **(b) Describe secret key and public key encryption.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 896 (ET: N/A)]*

26. **The Caesar Cipher is a type of shift cipher. Shift Ciphers work by using the modulo operator to encrypt and decrypt messages. The Shift Cipher has a key K, which is an integer from 0 to 25. How to Encrypt, How to decrypt.** *[Janata Bank Ltd SO ( Assistant Network Engineer) 2020 compact it 1009-1010 (ET: N/A)]*

27. **Public key cryptography কীভাবে কাজ করে?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1020 (ET: N/A)]*

28. **(গ) Plain Text and Cipher Text-এর মধ্যে মূল পার্থক্য কী? লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1069 (ET: N/A)]*

29. **(ক) Data encryption বলতে কী বোঝায়? বহুল ব্যবহৃত কয়েকটি encryption পদ্ধতির নাম লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1095 (ET: N/A)]*

30. **What is public key encryption? Explain digital signature with example.** *[ICT Ministry Assistant Programmer 2017 compact it 1238-1239 (ET: N/A)]*

31. **b) What is a digital signature? And why is that important?** *[Ministry of Finance Programmer 2013 compact it 1272 (ET: N/A)]*

## Firewalls & Network Defense (20)

1. **As a cybersecurity analyst at a nuclear power plant, what IDS strategies and steps are required to prevent cyberattacks?** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

2. **What is Packet Filter of Firewall?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

3. **Write down the difference between Next-Generation Firewall (NGFW) and Web Application Firewall (WAF)?** *[Islami Bank PLC Senior Officer (Network/System) 14.03.2025 compact it 1331 (ET: BUET)]*

| NGFW | WAF |
|---|---|
| নেটওয়ার্ক-ভিত্তিক সুরক্ষা | ওয়েব অ্যাপ্লিকেশন সুরক্ষা |
| Layer 3, 4, 7 | Layer 7 |
| Network-based Attacks (DDoS, Malware, IPS) | Web-based Attacks (SQL Injection, XSS, CSRF) |
| Palo Alto, Fortinet, Cisco Firepower | Cloudflare WAF, AWS WAF, Imperva WAF |

4. **Bangladesh Bank have client server and the communication with Mail Server, DNS server, Web server. Bangladesh Bank want to ensure the security using firewall on those server. Draw a diagram with the scenario.** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1323 (ET: DU)]*

5. **What is Demilitarized Zone (DMZ) and sandbox for security test?** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 398 (ET: BUET)]*

6. **Different types of network firewalls. Explain NGFW compared to traditional firewall.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 301 (ET: BIBM)]*

7. **What is Firewall? Discuss about different types of Firewall.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 528 (ET: MIST)]*

8. **Draw a diagram of LAN including network Firewall. Why is firewall important in network security? List 5 major types of network firewalls. Differentiate between Traditional Firewall and Next Generation Firewall.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 532 (ET: MIST)]*

9. **What is firewall and why it is used?** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 475 (ET: N/A)]*

10. **What is the function of a firewall?** *[BCC Assistant Programmer 11.11.2023 compact it 545 (ET: N/A)]*

11. **DMZ and firewall placement in a diagram. (Approximate)** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 651 (ET: BUET)]*

12. **What is Blacklist and Whitelist? Write down the difference between Black list and White list.** *[SPCB Sub-Assistant Programmer 2022 compact it 737 (ET: N/A)]*

13. **What is DMZ in data center? Describe using diagram? Write the network devices in this system?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 756 (ET: N/A)]*

14. **Difference between blacklisting and whitelisting. Which is more secure and why?** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 864 (ET: BUET)]*

15. **Write difference between Antivirus and Firewall.** *[BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)]*

16. **What is firewell? Draw a LAN network to showing firewall.** *[BREB Junior Assistant Manager (ICT) 2021 compact it 949 (ET: N/A)]*

17. **What is proxy server? Explain it.** *[BREB Assistant Junior Engineer (IT) 2019 compact it 1123 (ET: BREB)]*

18. **What is firewall? explain its work. Draw a LAN network and a firewall where firewall will be situated.** *[Bangladesh Bank Assistant Programmer 2019 compact it 1156 (ET: DU)]*

19. **What is Stateful and Stateless Firewall?** *[Dutch Bangla Bank Assistant Network/Hardware Engineer 2019 compact it 1159 (ET: BUET)]*

20. **What is DMZ? Explain with appropriate figure.** *[NESCO Manager (Software) 2018 compact it 1207 (ET: N/A)]*

## Malware & Security Threats (20)

1. Differentiate between a Computer Virus and a Computer Worm based on how they spread and replicate across host networks. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

2. **What is exfiltration?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1449 (ET: N/A)]*

3. **Software downloaded from internet and installed that is not malicious is called?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

4. **একটি Virus ও Ransomware এর নাম লিখ?** *[BTCL Junior Assistant Manager 2022 compact it 640 (ET: BUET)]*

5. **What is Trojan horse virus?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

6. **Computer এর Virus কি?** *[BPSC Computer Operator 2021 compact it 780 (ET: N/A)]*

7. **Trojan Horse কি?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

8. **What is QR code? What is Rootkit and bootkit?** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 820-821 (ET: BUET)]*

9. **Suppose your computer system is attack by a VIRUS and it's also copy into the six neighbor computer. Then it encrypts your all data in your all data in your system so that you can’t detect your data. What is the name of the VIRUS, how can you detect it?** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 821 (ET: BUET)]*

10. **‘Trojan Horse’ এর একটি বৈশিষ্ট্য লিখুন।** *[DMLC Assistant Teacher (ICT) 2021 compact it 825 (ET: N/A)]*

11. **Explain: Worm, Botnet, Ransomware and Trojan horse.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*

12. **Malware বলতে কী বুঝানো হয়? উদাহরণসহ সংক্ষেপে বর্ণনা করুন।** *[41th BCS 2021 compact it 883 (ET: N/A)]*

13. **Define component of computer virus.** *[BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)]*

14. **দুটি এন্টিভাইরাস সফটওয়্যার এর নাম লিখ।** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 945 (ET: N/A)]*

15. **কম্পিউটার ভাইরাস, ওয়ার্ম এবং ট্রোজান হর্স এর মধ্যে পার্থক্য লিখ।** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 947 (ET: BUET)]*

16. **Write down possible threats to a computer systems and how to provide security?** *[BTRC Assistant Director (Technical) 2019 compact it 1146 (ET: N/A)]*

17. **What protection do you provide for your computer from malware?** *[Bangladesh Bank Assistant Programmer 2019 compact it 1155 (ET: DU)]*

18. **Describe five types of malware threats and mention five known countermeasures.** *[Combined 3 Banks Assistant Programmer 2018 compact it 1197-1198 (ET: N/A)]*

19. **Define ransomware attack.** *[NESCO Manager (Software) 2018 compact it 1209 (ET: N/A)]*

20. **c) What is a computer virus? Name of the two software that are used to prevent the virus.** *[Ministry of Finance Programmer 2013 compact it 1272 (ET: N/A)]*

## Web Security Vulnerabilities (19)

1. Describe the SQL Injection and Cross-Site Scripting (XSS) web security threats and suggest preventive measures for each. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

2. Explain the vulnerability of SQL Injection. How can it be prevented? *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

3. **What is Cross site script and SQL injection?** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1333 (ET: BUET)]*

4. **What is CSRF attack?** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1333 (ET: BUET)]*

5. **What is CSRF and XSS?** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1361 (ET: BUET)]*

6. **What is SQL Injection? How to Prevent against SQL Injection Attacks?** *[RAKUB Programmer (PO) 12.10.2021 compact it 853-854 (ET: N/A)], [RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)], [Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*

7. **(b) Explain XSS and CSRF (how do you prevent these attacks).** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 415 (ET: BUET)]*

8. **Your bank wants to secure an e-banking online system and wants to configure a web server in your data center. What kind of tools and technology do you use for this?** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 309 (ET: BIBM)]*

9. **What is SQL Injection attack? How it launched?** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 588 (ET: BUET)]*

10. **Write the difference types of Web application attacks?** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 595 (ET: N/A)]*

11. **Write two differences between SQL Injection and cross site scripting (XSS).** *[BICIC Assistant Programmer 2022 compact it 630 (ET: BUET)]*

12. **What is SQL injection? How to prevent it?** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*

13. **What is Cross site script XSS and how can fix it?** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*

14. **Write down the counter measure of SQL injection attack.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 753 (ET: N/A)]*

15. **What is SQL Injection? How can we protect web Application from SQL Injection attack?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*

16. **What is SQL injection? How many ways to prevent it?** *[Bangladesh Television Assistant Programmer 2019 compact it 1064 (ET: N/A)]*

17. **(খ) Cross Site Scripting (XSS) বলতে কী বোঝায়? এর হাত থেকে রক্ষা পাওয়ার পদ্ধতিগুলো লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1090 (ET: N/A)]*

18. **What is session hijacking and how to encrypt username and password in PHP?** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1227-1228 (ET: N/A)]*

19. **What are the important steps to secure a web server?** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1228 (ET: N/A)]*

## Authentication & Access Control (16)

1. Multi-Factor Authentication (MFA) is mandatory in modern banking infrastructure. (a) Define the concept of MFA and explicitly list the three globally recognized categories of authentication factors. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

2. **টু-ফ্যাক্টর অথেনটিকেশন এবং ডিজিটাল সিগনেচার দিয়ে ডেটার সুরক্ষা কীভাবে করা হয়?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

3. **ডিজিটাল সিগনেচার (Digital Signature) কী? এর কার্যকারিতা ব্যাখ্যা করুন।** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

4. **(a) What is 2-factor authentication? Describe it with an example.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1356 (ET: N/A)], [BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 796 (ET: N/A)]*

5. **Write down the full form of LDAP?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

6. **Your bank has an online banking system and this process is performed by sending OTP in mobile or OTP in mail when a customer transfers money from a mobile banking app or online. This is a secured policy. Without this biometric policy, how can you more secure your online banking? Explain your strategy.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 306 (ET: BIBM)]*

7. **Difference between Digital signature and Digital certificate.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 527 (ET: MIST)]*

8. **How to work two factor authentication?** *[Mongla Port Authority Assistant Programmer 2023 compact it 574 (ET: N/A)]*

9. **(b) How do you define 2 factor authentication? Give example.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 486 (ET: N/A)]*

10. **What is digital signature? Where is it used?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 635 (ET: N/A)]*

11. **What is a digital signature? Describe its role in digital security?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 679 (ET: N/A)]*

12. **What is Digital signature? Explain shortly.** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 718 (ET: N/A)]*

13. **(খ) Authentication বলতে কি বুঝায়? Two Factor Authenticating কি? উদাহরণসহ ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 769 (ET: N/A)]*

14. **(b) Write down the purpose of Certification Authority (CA) in Digital Signature.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 797 (ET: N/A)]*

15. **১৮. পাসওয়ার্ড সুরক্ষা জন্য যে পদ্ধতি ব্যবহার করা হয় তার নাম কী?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 942 (ET: N/A)]*

16. **What do you mean by two factor authentication? Explain with example.** *[BTRC Assistant Director (Technical) 2019 compact it 1147-1148 (ET: N/A)]*

## Security Protocols (SSL/TLS, HTTPS) (12)

1. **What is SSL?** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*, *[BREB Assistant Hardware & Network Engineer 2019 compact it 1124 (ET: BREB)]*

2. **Which client is used to security cannot to a remote server?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*

3. **Ensure secure communication between a client application and the database server.** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 314 (ET: N/A)]*

4. **Difference between HTTP and HTTPs.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 398 (ET: BUET)]*

5. **(গ) HTTP ও HTTPS প্রোটোকলের মধ্যে সুরক্ষার দিক থেকে কোনটি কার্যকর?** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

6. **Write down the basic differences of the following:**
   **(ii) TLS 1.2 vs. 1.3** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 535 (ET: MIST)]*

7. **What is SSL, TLS, and HTTPs?** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 594 (ET: N/A)]*

8. **Attacker steals private key of website that uses transport layer security and remains undetected what can be done with private key?** *[Combined Bank Assistant Programmer 09.06.2023 compact it 493 (ET: N/A)]*

9. **(a) Write the full form of those: (i) SSL (ii) TSL** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 819 (ET: BUET)]*

10. **(b) Which IP address may have secured via SSL and publicly by the Certificate Authority(CA). If secured Write Yes or otherwise No.** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 819 (ET: BUET)]*
   1.1.1.1
   8.8.4.1
   192.168.10.2
   8.8.8.8
   172.16.8.1
   10.0.0.1

11. **HTTPs কীভাবে একটি Website-এর সুরক্ষা দেয়? ব্লক ডায়াফ্রামের মাধ্যমে উত্তর দিন।** *[40th BCS 2020 compact it 971 (ET: BPSC)]*

12. **What is the difference among threat, vulnerability and risk? Explain SSL and TLS.** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1050 (ET: BUET)]*

## Cyber Crime & Security (10)

1. **সাইবার অপরাধের প্রকারভেদ পরিবেশের স্থায়িত্ব বর্ণনা করুন।** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

2. **Why is cyber security important? What are the common types of cyber threats? Explain cyber security measures.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

3. **Hacking a system without cracking the system, only for finding bugs and vulgarities is called?** *[BCC Assistant Programmer 11.11.2023 compact it 545 (ET: N/A)]*

4. **What is Cybercrime? Cybercrime রোধে প্রয়োজনীয় পদক্ষেপ গুলো লিখ।** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 642 (ET: BUET)]*

5. **What is Cyber space? Write some threats of cyber space.** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 699 (ET: BUET)]*

6. **Write the cyber security threats.** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*

7. **What is Vulnerability?** *[BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*

8. **What is cyber threat intelligence database? What is the use of this in corporate office network?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 752 (ET: N/A)]*

9. **সাইবার অপরাধ কি? ৮টি সাইবার অপরাধ এর নাম লিখুন। সাইবার অপরাধ দূর করার জন্য ৬টি পন্থার নাম লিখুন।** *[BREB Junior Assistant Manager (ICT) 2021 compact it 948-949 (ET: N/A)]*

10. **Employee causes the most risk of fraud and computer compromises- do you agree with the statement. Justify your answer.** *[Combined Bank Senior Officer (IT/ICT) 2019 compact it 1113 (ET: DU)]*

## Security Principles (CIA Triad) (8)

1. What does CIA stand for in information security? Explain each component briefly. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

2. What is authentication and authorization? What is the CIA triad in cyber security? How does it work? *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*

3. **(a) What is the CIA triad of information system? Briefly describe its each component.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

4. **Describe how the principles of Confidentiality, Integrity, and Availability work together to protect organizational data, and provide one real-world example of a security breach where one or more of these principles were compromised.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1428 (ET: E-Zone)]*

5. **What is CIA Triad?** *[EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)], [Teletalk Assistant Manager (IT) 2023 compact it 465 (ET: N/A)]*

6. **Preserving confidentiality integrity and availability of data is a restatement of the concern over falsification, interception, masquerade and denial of service. Explain how the first three concepts relate to the last four.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 435 (ET: BIBM)]*

7. **Information System কী? Information Syetem -এর সুরক্ষায় প্রয়োজনীয় পদক্ষেপ সংক্ষেপে বর্ণনা করুন?** *[41th BCS 2021 compact it 883-884 (ET: N/A)]*

8. **What is non-repudiation in network security? Give a proper example.** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1189 (ET: N/A)]*

## VPN & Tunneling Protocols (IPsec, SSL VPN) (6)

1. **What is the purpose of VPN used in computer security?** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 476 (ET: N/A)]*

2. **In which layer IPsec works?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

3. **What is VPN? How it is working.** *[BOF Assistant Programmer 2022 compact it 732 (ET: MIST)]*

4. **(a) How can VPN provide secure communication platform? Explain site-to-site VPN and remote-access VPN using necessary figures.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 800 (ET: N/A)]*

5. **What is VPN? Difference between site to site VPN and Remote access VPN.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 840 (ET: N/A)]*

6. **What is VPN? Why we use it?** *[Sonali Bank Ltd. Officer IT 2021 compact it 909 (ET: N/A)]*

## Critical Information Infrastructure (CII) & Cyber Governance (3)

1. What is CII? How many CII organizations? Name 10 CII organization name. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

2. **CTC কী? কী কাজে ব্যবহার হয়?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

3. **(c) Briefly write about the cybersecurity laws of Bangladesh.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

## Cryptography & Network Security Scenarios (3)

1. Cryptography and Network Security Scenario: [BSCCPL AME 21-08-2026 (BUET)] Cox's Bazar wants to send confidential information to Kuakata through an insecure network. Cox's Bazar first generates a hash value using a Hash Function (H). The message, hash value, and routing data are combined and encrypted using Kuakata's Public Key (Ku). The encrypted ciphertext is transmitted through the network. During transmission, an attacker positioned between Cox's Bazar and Kuakata intercepts the encrypted data. The attacker captures the ciphertext and deliberately blocks it so that Kuakata never receives the message. However, the attacker is unable to read or decrypt the original message because Kuakata's Private Key (\text{Ku}^{-1}) is not available to the attacker. Kuakata is expected to decrypt the received ciphertext using its Private Key (\text{Ku}^{-1}) and verify the integrity of the message using the hash value whenever the message is successfully delivered. Questions: (a) Is there any digital signature? (b) Identify attack. (c) How to identify origin of the? (d) How to manage the attack. (e) Does the described communication provide a Digital Signature? Give reasons. If not, explain how Cox's Bazar can add a Digital Signature using Cox's Bazar's Private Key (\text{Kc}^{-1}) and verification using Cox's Bazar's Public Key (\text{Kc}). (f) Which security services are provided by the system among Confidentiality, Integrity, Authentication, Non-repudiation, and Availability? (g) Suggest suitable techniques or mechanisms to protect the communication against the attack identified in question (b). (h) Draw a complete communication diagram showing \text{Message} \to \text{Hash} \to \text{Routing Data} \to \text{Encryption with Ku} \to \text{Attacker} \to \text{Kuakata} \to \text{Decryption with } \text{Ku}^{-1}, and indicate the keys used in each stage.

2. **Explain Cyber Attack Scenario-** *[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1441 (ET: BUET)]*

3. **Imagine yu should design a secure transmission protocol for sending data from one node to another node. You should divide the message in the multiple packets and this packets will be using different path so that any one cannot decrypt the message.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 756 (ET: N/A)]*

## Email & Messaging Security (Spam, Phishing) (3)

1. **Unsoliciated email is called?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

2. **If you downloaded the email, you will be able to face the problem. Which attack do you face?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*

3. **e) What is email? What precautions can be taken to prevent unnecessary and unwanted e-mails?** *[Ministry of Finance Programmer 2013 compact it 1272 (ET: N/A)]*

## Buffer Overflow & Software Vulnerabilities (1)

1. **Explain buffer overflow attack with an example.** *[BTCL Assistant Manager (Technical) 2023 compact it 592 (ET: BUET)]*
