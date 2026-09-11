<!-- TOC START -->
**Table of Contents** — 2 subtopics · 13 theories

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
> Using modular exponentiation (26² = 676 mod 77 = 60; 26⁴ = 60² = 3600 mod 77 = 55; 26⁸ = 55² = 3025 mod 77 = 44; 26¹⁶ = 44² = 1936 mod 77 = 12; 26³² = 12² = 144 mod 77 = 67)
> 26³⁷ = 26³² × 26⁴ × 26¹ = 67 × 55 × 26 mod 77
> 67 × 55 = 3685 mod 77 = 3685 − 3619 = 66 · 66 × 26 = 1716 mod 77 = 1716 − 1694 = **22**

*(Note: with these particular small numbers the arithmetic must be done very carefully; the standard textbook set p = 3, q = 11, n = 33, φ = 20, e = 7, d = 3 gives a cleaner check: encrypting P = 2 gives C = 2⁷ mod 33 = 128 mod 33 = **29**, and decrypting gives 29³ mod 33 = 24389 mod 33 = **2** ✅ — use that set if you must show the full arithmetic under time pressure.)*

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
