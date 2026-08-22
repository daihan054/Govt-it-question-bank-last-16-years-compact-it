## Cryptography

1. Explain the operational difference between Hashing and Encryption. [SO IT 25-07-2026]

2. Explain the concepts of encryption and decryption with an example. (Combined Bank Officer (IT) Exam: 09.05.2026) [debug it]

3. What is social engineering? What is hashing? How is it different from encryption? (Combined Bank Officer (IT) Exam: 03.01.2026) [debug it]

## Security Principles (CIA Triad)

1. What does CIA stand for in information security? Explain each component briefly. (Combined Bank Officer (IT) Exam: 09.05.2026) [debug it]

2. What is authentication and authorization? What is the CIA triad in cyber security? How does it work? (Combined Bank Officer (IT) Exam: 03.01.2026) [debug it]

## Critical Information Infrastructure (CII) & Cyber Governance

1. What is CII? How many CII organizations? Name 10 CII organization name. (BEPRC Assistant Programmer Exam: 08.08.2026)

## Malware & Security Threats

1. Differentiate between a Computer Virus and a Computer Worm based on how they spread and replicate across host networks. (Officer (IT) Exam: 31 Jul 2026) [bscs 02]

## Social Engineering & Cyber Attacks

1. What is a phishing attack? Explain its types and discuss methods to prevent it. (Combined Bank Officer (IT) Exam: 09.05.2026) [debug it]

## Authentication & Access Control

1. Multi-Factor Authentication (MFA) is mandatory in modern banking infrastructure. (a) Define the concept of MFA and explicitly list the three globally recognized categories of authentication factors. (Combined Bank Officer (IT) Exam: 09.05.2026) [debug it]

## Web Security Vulnerabilities

1. Describe the SQL Injection and Cross-Site Scripting (XSS) web security threats and suggest preventive measures for each. (Officer (IT) Exam: 31 Jul 2026) [bscs 02]

## Cryptography & Network Security Scenarios

1. Cryptography and Network Security Scenario: [BSCCPL AME 21-08-2026 (BUET)] Cox's Bazar wants to send confidential information to Kuakata through an insecure network. Cox's Bazar first generates a hash value using a Hash Function (H). The message, hash value, and routing data are combined and encrypted using Kuakata's Public Key (Ku). The encrypted ciphertext is transmitted through the network. During transmission, an attacker positioned between Cox's Bazar and Kuakata intercepts the encrypted data. The attacker captures the ciphertext and deliberately blocks it so that Kuakata never receives the message. However, the attacker is unable to read or decrypt the original message because Kuakata's Private Key (\text{Ku}^{-1}) is not available to the attacker. Kuakata is expected to decrypt the received ciphertext using its Private Key (\text{Ku}^{-1}) and verify the integrity of the message using the hash value whenever the message is successfully delivered. Questions: (a) Is there any digital signature? (b) Identify attack. (c) How to identify origin of the? (d) How to manage the attack. (e) Does the described communication provide a Digital Signature? Give reasons. If not, explain how Cox's Bazar can add a Digital Signature using Cox's Bazar's Private Key (\text{Kc}^{-1}) and verification using Cox's Bazar's Public Key (\text{Kc}). (f) Which security services are provided by the system among Confidentiality, Integrity, Authentication, Non-repudiation, and Availability? (g) Suggest suitable techniques or mechanisms to protect the communication against the attack identified in question (b). (h) Draw a complete communication diagram showing \text{Message} \to \text{Hash} \to \text{Routing Data} \to \text{Encryption with Ku} \to \text{Attacker} \to \text{Kuakata} \to \text{Decryption with } \text{Ku}^{-1}, and indicate the keys used in each stage.
