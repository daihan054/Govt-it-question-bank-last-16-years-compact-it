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

## Web Security Vulnerabilities (15)

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

## Malware & Security Threats (15)

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

## Security Protocols (SSL/TLS, HTTPS) (11)

1. **What is SSL?** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*

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

## Email & Messaging Security (Spam, Phishing) (2)

1. **Unsoliciated email is called?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

2. **If you downloaded the email, you will be able to face the problem. Which attack do you face?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*

## Buffer Overflow & Software Vulnerabilities (1)

1. **Explain buffer overflow attack with an example.** *[BTCL Assistant Manager (Technical) 2023 compact it 592 (ET: BUET)]*
