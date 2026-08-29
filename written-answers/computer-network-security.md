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

2. **(b) What is an ARP poisoning attack, and how does it work?** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

3. **What is a Man-in-the-Middle (MITM) attack? Describe two countermeasures to prevent it.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

4. **What is a DoS attack? Explain the mechanism of a DDoS attack and how it differs from a simple DoS attack.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

5. **What is a Man-inThe Middle (MitM) attack? How can it be prevented?** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1337 (ET: N/A)]*

6. **Briefly explain phishing attack and denial-of-service (DoS) attack.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1341 (ET: N/A)]*

7. **How to attack DHCP server in MIMA?** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 416 (ET: BUET)]*

8. **Let you procure a microfinance application and host it in your office's data centre. What kind of cyber-security threats should you be aware of and what steps would you take to mitigate the threats?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 332 (ET: BIBM)]*

9. **Write down the 10 most Cyber attacks. Difference among Black Hat hacker, Grey hat hacker and white hat hacker.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 526 (ET: MIST)]*

10. **What is Cyber Security? Write down the top 10 cyber attack. Discuss about Ransomware and DDoS attack.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 512 (ET: MIST)]*

11. **What is meant by Encryption and Decryption? What is Cyber security? Write down the top 10 cyber attack.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 557 (ET: BIBM)]*

12. **Difference between active and passive atack.** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*

13. **Describe a man-in the middle attack on the Diffie-Hellman key exchange protocol in which the adversary generates two public key pairs for the attack.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 434 (ET: BIBM)]*

14. **What is MAC flooding? How to prevent MAC flooding?** *[Teletalk Assistant Manager (IT) 2023 compact it 466 (ET: N/A)], [Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 717 (ET: N/A)]*

15. **What is Denial of Service (DoS) is and NAT?** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 659 (ET: N/A)]*

16. **What do you understand by DOS attack and Man-in-the-middle attack? Please explain how it can be occurred?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*

17. **What do you mean by a DNS poisoning attack, and how does it work?** *[GTCL Assistant Engineer (CSE) 2022 compact it 685 (ET: BUET)]*

18. **Write down the difference between Active and Passive attack.** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 719 (ET: N/A)]*

19. **What is DHCP starvation and how DHCP starvation work with diagram? Write down the related attack introduced by DHCP starvation?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 753 (ET: N/A)]*

20. **What is MAC flooding attack? What is the impact of this switch?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 753 (ET: N/A)]*

21. **(b) Distinguish between phishing and pharming. Give examples to explain.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 801 (ET: N/A)]*

22. **What is DDoS and SQL Injection attack?** *[Sonali Bank Ltd. Officer IT 2021 compact it 909 (ET: N/A)]*

23. **Phishing attack এর মাধ্যমে কীভাবে attack করা হয়। উহার কারণে কি ক্ষতি হতে পারে?** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 913 (ET: BUET)]*

24. **Explain ARP Spoofing attack with diagram. Why ARP spoofing attacker used to launch Man-in-the-Middle attack.** *[SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)]*

25. **Difference between spoofing and sniffing** *[Combined 4 Banks Assistant Programmer 2020 compact it 1002 (ET: DU)]*

26. **Which security attacks (given) occur on client side or server side?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033 (ET: BUET)]*

## Firewalls & Network Defense (16)

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
