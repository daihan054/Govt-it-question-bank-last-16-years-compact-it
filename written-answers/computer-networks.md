<!-- TOC START -->
**Table of Contents** — 33 subtopics · 507 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Subnetting & IP Addressing](#subnetting--ip-addressing-109) | 109 |
| 2 | [OSI & TCP/IP Reference Model](#osi--tcpip-reference-model-52) | 52 |
| 3 | [Networking Fundamentals & Terminology](#networking-fundamentals--terminology-32) | 32 |
| 4 | [Application Layer Protocols & Troubleshooting (DNS, DHCP, HTTPS)](#application-layer-protocols--troubleshooting-dns-dhcp-https-22) | 22 |
| 5 | [Wireless Networks & IoT (mmWave)](#wireless-networks--iot-mmwave-19) | 19 |
| 6 | [Networking Devices](#networking-devices-19) | 19 |
| 7 | [Multiplexing & Bandwidth](#multiplexing--bandwidth-18) | 18 |
| 8 | [Routing Protocols & Route Configuration](#routing-protocols--route-configuration-18) | 18 |
| 9 | [Transport Layer (TCP & UDP)](#transport-layer-tcp--udp-17) | 17 |
| 10 | [Communication System & Transmission Modes](#communication-system--transmission-modes-17) | 17 |
| 11 | [Data Rate & Channel Capacity (Nyquist, Shannon)](#data-rate--channel-capacity-nyquist-shannon-16) | 16 |
| 12 | [Physical Layer & Transmission Media (Cables & Wiring)](#physical-layer--transmission-media-cables--wiring-15) | 15 |
| 13 | [Error Detection & Data Communication (CRC, Throughput)](#error-detection--data-communication-crc-throughput-14) | 14 |
| 14 | [Network Topologies](#network-topologies-14) | 14 |
| 15 | [IPv6 Addressing](#ipv6-addressing-13) | 13 |
| 16 | [Physical Layer & Optical Fiber (Attenuation & Power Budget)](#physical-layer--optical-fiber-attenuation--power-budget-13) | 13 |
| 17 | [Network Address Translation (NAT)](#network-address-translation-nat-13) | 13 |
| 18 | [Flow Control & Data Link Layer (Stop-and-Wait)](#flow-control--data-link-layer-stop-and-wait-12) | 12 |
| 19 | [Network Services (DHCP, NAT)](#network-services-dhcp-nat-11) | 11 |
| 20 | [Digital Modulation & Signal Processing (BPSK, QPSK)](#digital-modulation--signal-processing-bpsk-qpsk-10) | 10 |
| 21 | [Email Architecture & Protocols (SMTP, POP3, IMAP)](#email-architecture--protocols-smtp-pop3-imap-10) | 10 |
| 22 | [Application Layer & Well-Known Port Numbers](#application-layer--well-known-port-numbers-6) | 6 |
| 23 | [Pulse Code Modulation (PCM) & Signal Processing](#pulse-code-modulation-pcm--signal-processing-6) | 6 |
| 24 | [Switching Techniques (Circuit vs Packet Switching)](#switching-techniques-circuit-vs-packet-switching-5) | 5 |
| 25 | [WAN Technologies (SONET/SDH, ATM, WDM)](#wan-technologies-sonetsdh-atm-wdm-5) | 5 |
| 26 | [Network Layer (Packet Fragmentation & Tunneling)](#network-layer-packet-fragmentation--tunneling-4) | 4 |
| 27 | [Satellite Communication](#satellite-communication-4) | 4 |
| 28 | [Analog Modulation & Radio Receivers](#analog-modulation--radio-receivers-3) | 3 |
| 29 | [Spread Spectrum & Multiple Access (CDMA, FHSS, DSSS)](#spread-spectrum--multiple-access-cdma-fhss-dsss-3) | 3 |
| 30 | [Line Coding & Digital Encoding](#line-coding--digital-encoding-2) | 2 |
| 31 | [Address Resolution (ARP & RARP)](#address-resolution-arp--rarp-2) | 2 |
| 32 | [VLANs & Subnetting Comparison](#vlans--subnetting-comparison-2) | 2 |
| 33 | [High Availability & Redundancy Protocols (VRRP, HSRP)](#high-availability--redundancy-protocols-vrrp-hsrp-1) | 1 |

<!-- TOC END -->

---

## Subnetting & IP Addressing (109)

1. An organization is granted the IPv4 network block 14.24.74.0/24 and needs to segment it into two subnets: Subnet A (requires 120 addresses) and Subnet B (requires 60 addresses). Allocating sequentially from the requirement first to maximize remaining address space, state only the Network Address (with its CIDR mask) and the Broadcast Address for both subnets. [SO IT 25-07-2026]

   Answer: This is a VLSM problem. Allocate the larger subnet first, then take the smaller one from the space left over.

   Given block: 14.24.74.0/24 = 256 addresses (14.24.74.0 – 14.24.74.255)

   Step 1 – Subnet A (needs 120 addresses)
   - Host bits: 2^n >= 120 -> 2^7 = 128, so n = 7
   - Prefix = 32 − 7 = /25, block size 128
   - Range 14.24.74.0 – 14.24.74.127
   - Network address: `14.24.74.0/25`
   - Broadcast address: `14.24.74.127`

   Step 2 – Subnet B (needs 60 addresses)
   - Host bits: 2^n >= 60 -> 2^6 = 64, so n = 6
   - Prefix = 32 − 6 = /26, block size 64
   - Starts at the next free address after A: 14.24.74.128
   - Range 14.24.74.128 – 14.24.74.191
   - Network address: `14.24.74.128/26`
   - Broadcast address: `14.24.74.191`

   Final answer
   - Subnet A: network `14.24.74.0/25`, broadcast `14.24.74.127`
   - Subnet B: network `14.24.74.128/26`, broadcast `14.24.74.191`
   - Remaining free: `14.24.74.192/26` (64 addresses) for future growth

2. An organization has been assigned the IPv4 network address 192.168.1.0/24. As part of the network deployment, the network administrator is required to divide the address space into four equal-sized subnets to support different departments. Determine the Network Address, Subnet Mask (both CIDR and dotted-decimal notation). *[Officer (IT) 31 Jul 2026 bscs 01 (ET: N/A)]*

   Answer: Four equal subnets means borrowing host bits until 2^n reaches 4.

   Given: 192.168.1.0/24, default mask 255.255.255.0

   Step 1 – bits to borrow: 2^n >= 4 -> 2^2 = 4, so n = 2
   Step 2 – new prefix = 24 + 2 = /26
   Step 3 – mask: /26 = 11111111.11111111.11111111.11000000 = `255.255.255.192`
   Step 4 – block size = 256 − 192 = 64, so subnets start 64 apart

   Final answer – the mask is `/26` = `255.255.255.192` for all four:

   | # | Network address | Broadcast address | Usable host range |
   |---|---|---|---|
   | 1 | 192.168.1.0/26 | 192.168.1.63 | 192.168.1.1 – 192.168.1.62 |
   | 2 | 192.168.1.64/26 | 192.168.1.127 | 192.168.1.65 – 192.168.1.126 |
   | 3 | 192.168.1.128/26 | 192.168.1.191 | 192.168.1.129 – 192.168.1.190 |
   | 4 | 192.168.1.192/26 | 192.168.1.255 | 192.168.1.193 – 192.168.1.254 |

   - Each subnet holds 64 addresses = 62 usable hosts + 1 network + 1 broadcast.

3. Subnetting logic requires precise binary calculation. A network engineer is tasked with dividing the internal network 192.168.10.0/24 into exactly 4 equal subnets for four different bank branches. Show the mathematical calculation to determine how many bits must be borrowed to create 4 subnets, and state the new Subnet Mask in both CIDR notation and decimal format. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer: Given 192.168.10.0/24, default mask 255.255.255.0.

   Step 1 – bits to borrow
   - Number of subnets = 2^n, where n = borrowed bits
   - 2^n >= 4 -> 2^2 = 4, so n = 2 bits must be borrowed

   Step 2 – new prefix
   - New prefix = 24 + 2 = /26

   Step 3 – mask in binary and decimal
   ```
   Default /24 : 11111111.11111111.11111111.00000000 = 255.255.255.0
   Borrow 2    : 11111111.11111111.11111111.11000000 = 255.255.255.192
                                           ^^ these 2 bits are borrowed
   ```
   - Last octet 11000000 = 128 + 64 = 192

   Answer
   - Bits borrowed: 2
   - CIDR notation: `/26`
   - Decimal mask: `255.255.255.192`
   - Block size = 256 − 192 = 64, giving 4 subnets of 62 usable hosts each (192.168.10.0, .64, .128, .192)

4. Network Address, Broadcast Address, Subnet Mask and Usable Host IP Range of: 10.0.0.0/30, 192.168.0.0/23, 172.16.1.0/24. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

   Answer:

   (i) 10.0.0.0/30 – mask `255.255.255.252`, block size 4

   | Item | Value |
   |---|---|
   | Network address | 10.0.0.0 |
   | Broadcast address | 10.0.0.3 |
   | Usable range | 10.0.0.1 – 10.0.0.2 |
   | Usable hosts | 2 |

   - A /30 gives exactly 2 usable addresses, which is why it is the standard mask for a router-to-router point-to-point link.

   (ii) 192.168.0.0/23 – mask `255.255.254.0`, block size 2 in the third octet

   | Item | Value |
   |---|---|
   | Network address | 192.168.0.0 |
   | Broadcast address | 192.168.1.255 |
   | Usable range | 192.168.0.1 – 192.168.1.254 |
   | Usable hosts | 510 |

   (iii) 172.16.1.0/24 – mask `255.255.255.0`

   | Item | Value |
   |---|---|
   | Network address | 172.16.1.0 |
   | Broadcast address | 172.16.1.255 |
   | Usable range | 172.16.1.1 – 172.16.1.254 |
   | Usable hosts | 254 |

5. (a) IP address এবং MAC/MU এর পার্থক্য লেখ।
   (b) Classfull এবং Classless IP address এর মধ্যে পার্থক্য লেখ।
   (c) 11000001 00001001 00001010 00010101 এই IP এর Class লিখ। *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

   Answer:

   (a) IP address vs MAC address

   | Point | IP address | MAC address |
   |---|---|---|
   | Layer | Network layer (Layer 3) | Data link layer (Layer 2) |
   | Size | 32 bits (IPv4) / 128 bits (IPv6) | 48 bits |
   | Format | Dotted decimal, e.g. 192.168.1.5 | Hexadecimal, e.g. 00:1A:2B:3C:4D:5E |
   | Assigned by | Network administrator or DHCP | Manufacturer, burned into the NIC |
   | Changes | Changes when the device moves to a new network | Fixed for the life of the card (logically) |
   | Scope | Works end to end across the whole internet | Works only inside one local network segment |
   | Purpose | Logical addressing and routing | Physical delivery inside a LAN |

   (b) Classful vs Classless addressing

   | Point | Classful | Classless (CIDR) |
   |---|---|---|
   | Basis | Fixed classes A, B, C, D, E | Variable-length prefix |
   | Mask | Fixed default mask per class | Any prefix from /0 to /32 |
   | Flexibility | Rigid, huge wastage | Blocks sized to actual need |
   | Subnetting | FLSM only | VLSM supported |
   | Route summary | Not possible | Route aggregation possible |
   | Standard | RFC 791 (1981) | RFC 1519 (1993) |

   - The switch happened because a company needing 500 hosts had to take a whole Class B of 65,534 addresses, wasting over 64,000.

   (c) Class of 11000001 00001001 00001010 00010101
   - Convert to decimal: 11000001 = 193, 00001001 = 9, 00001010 = 10, 00010101 = 21
   - The address is `193.9.10.21`
   - First octet 193 lies in 192–223, and the leading bits are `110`
   - Class: `Class C`

6. **A bank has the network block 192.168.10.0/24. The IT manager wants to divide this into 4 equal subnets.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*
(a) How many bits do you need to borrow to make 4 subnets?
(b) What is the new Subnet Mask in dotted-decimal format?
(c) Write down the Network Address, the First Usable IP, and the Broadcast Address for the second subnet created. Show your calculation.

   Answer: Given 192.168.10.0/24, four equal subnets required.

   (a) Bits to borrow
   - 2^n >= 4 -> 2^2 = 4, so 2 bits are borrowed
   - New prefix = 24 + 2 = /26

   (b) New subnet mask
   - /26 = 11111111.11111111.11111111.11000000
   - Dotted decimal: `255.255.255.192`

   (c) The second subnet
   - Block size = 256 − 192 = 64, so subnets begin at .0, .64, .128, .192
   - Second subnet therefore starts at 192.168.10.64

   | Item | Value | How it is found |
   |---|---|---|
   | Network address | 192.168.10.64 | Second multiple of the block size |
   | First usable IP | 192.168.10.65 | Network address + 1 |
   | Last usable IP | 192.168.10.126 | Broadcast − 1 |
   | Broadcast address | 192.168.10.127 | Next network (128) − 1 |

   - Each subnet gives 64 − 2 = 62 usable host addresses.

7. **What is subnetting? For the network 192.168.1.0/22, how many usable host addresses does it have?** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

   Answer:

   What is subnetting
   - Subnetting is the process of dividing one large IP network into several smaller logical networks called subnets, by borrowing bits from the host portion and adding them to the network portion.
   - Benefits: less broadcast traffic, better security through separation, easier management, and efficient use of address space.

   Usable hosts in 192.168.1.0/22
   - Prefix /22 means 22 network bits, so host bits = 32 − 22 = 10
   - Total addresses = 2^10 = 1024
   - Usable hosts = 1024 − 2 = `1022` (subtracting the network and broadcast addresses)
   - Mask = `255.255.252.0`

   - Note: with a /22 mask the true network address of this block is 192.168.0.0/22, covering 192.168.0.0 – 192.168.3.255. The address 192.168.1.0 is an ordinary host address inside it.

8. **Given IP address 10.0.0.100 and Subnet mask 255.255.240.0 which is network address?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1449 (ET: N/A)]*

   Answer: Mask 255.255.240.0 = /20.

   Step 1 – AND the IP with the mask, octet by octet
   ```
   IP    10 . 0 . 0        . 100   -> 00001010.00000000.00000000.01100100
   Mask 255 .255. 240      .   0   -> 11111111.11111111.11110000.00000000
   AND                             -> 00001010.00000000.00000000.00000000
   ```

   Step 2 – result
   - Network address: `10.0.0.0/20`
   - Block size in the third octet = 256 − 240 = 16, so subnets run 10.0.0.0, 10.0.16.0, 10.0.32.0 …
   - Since the third octet of the IP is 0, it falls in the first block.
   - Broadcast address: 10.0.15.255, usable range 10.0.0.1 – 10.0.15.254 (4094 hosts).

9. **Given IP address 10.10.0.0/16, you have divide the network into eight equal subnets. Find the subnet mask in dotted decimal and CIDR notation. Also find the first and last usable IP addresses of third subnet.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1362 (ET: BUET)], [DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*

   Answer: Given 10.10.0.0/16, eight equal subnets required.

   Step 1 – bits to borrow
   - 2^n >= 8 -> 2^3 = 8, so n = 3 bits

   Step 2 – new prefix and mask
   - New prefix = 16 + 3 = `/19`
   - /19 = 11111111.11111111.11100000.00000000 = `255.255.224.0`

   Step 3 – block size
   - Third octet: 256 − 224 = 32, so subnets step by 32 in the third octet

   | Subnet | Network | Broadcast |
   |---|---|---|
   | 1 | 10.10.0.0/19 | 10.10.31.255 |
   | 2 | 10.10.32.0/19 | 10.10.63.255 |
   | 3 | 10.10.64.0/19 | 10.10.95.255 |
   | 4 | 10.10.96.0/19 | 10.10.127.255 |

   Step 4 – third subnet
   - Network 10.10.64.0
   - First usable IP: `10.10.64.1`
   - Last usable IP: `10.10.95.254`
   - Usable hosts per subnet = 2^13 − 2 = 8190

10. **Subnet mask & Total host calculation.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

    Answer:

    Subnet mask
    - A 32-bit number that separates the network portion from the host portion of an IP address. Network bits are 1, host bits are 0.
    - Example: /26 = 255.255.255.192 = 11111111.11111111.11111111.11000000.

    Total host calculation
    - Total addresses = 2^h, where h = 32 − prefix length
    - Usable hosts = 2^h − 2 (one address is the network ID, one is the broadcast address)
    - Number of subnets created = 2^n, where n = number of borrowed bits
    - Block size = 256 − (value of the interesting octet in the mask)

    Quick reference table

    | CIDR | Mask | Block | Total | Usable |
    |---|---|---|---|---|
    | /24 | 255.255.255.0 | 256 | 256 | 254 |
    | /25 | 255.255.255.128 | 128 | 128 | 126 |
    | /26 | 255.255.255.192 | 64 | 64 | 62 |
    | /27 | 255.255.255.224 | 32 | 32 | 30 |
    | /28 | 255.255.255.240 | 16 | 16 | 14 |
    | /29 | 255.255.255.248 | 8 | 8 | 6 |
    | /30 | 255.255.255.252 | 4 | 4 | 2 |

    - Exception: /31 links (RFC 3021) use both addresses, and /32 is a single host route.

11. **Given the network 245.248.128.0/20, divide the address space among three departments as follows:**
   **(a) Manager: half of the address space.**
   **(b) HR: one-quarter of the address space.**
   **(c) Admin: the remaining one-quarter.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1437 (ET: BUET)]*

   **For each department, determine:**
   **(i) The network block (in CIDR notation).**
   **(ii) The IP address valid range.**
   **(iii) The number of valid hosts.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1438 (ET: BUET)]*

    Answer: Given 245.248.128.0/20 = 4096 addresses, range 245.248.128.0 – 245.248.143.255.

    Step 1 – size each share
    - Manager = half of 4096 = 2048 -> host bits 11 -> prefix /21
    - HR = one quarter = 1024 -> host bits 10 -> prefix /22
    - Admin = remaining quarter = 1024 -> prefix /22

    Step 2 – allocate sequentially

    | Dept | (i) Block (CIDR) | (ii) Valid IP range | (iii) Valid hosts |
    |---|---|---|---|
    | Manager | 245.248.128.0/21 | 245.248.128.1 – 245.248.135.254 | 2046 |
    | HR | 245.248.136.0/22 | 245.248.136.1 – 245.248.139.254 | 1022 |
    | Admin | 245.248.140.0/22 | 245.248.140.1 – 245.248.143.254 | 1022 |

    Broadcast addresses
    - Manager: 245.248.135.255, HR: 245.248.139.255, Admin: 245.248.143.255
    - Masks: /21 = 255.255.248.0, /22 = 255.255.252.0
    - Check: 2048 + 1024 + 1024 = 4096, so the whole block is used with nothing left over.

12. **Find out the network address and Broadcast address of the address: 192.168.0.0/28** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1360 (ET: BUET)]*

    Answer: /28 means host bits = 32 − 28 = 4, block size = 2^4 = 16, mask = 255.255.255.240.

    - Network address: `192.168.0.0`
    - Broadcast address: `192.168.0.15` (all 4 host bits set to 1)
    - Usable range: 192.168.0.1 – 192.168.0.14
    - Usable hosts: 16 − 2 = 14

    ```
    192.168.0.0000 0000  -> network   192.168.0.0
    192.168.0.0000 1111  -> broadcast 192.168.0.15
    ```

13. **(a) An organization wants to divide its LAN IP address 192.168.0.0/24 into 4 subnets according to buildings. The buildings IP address creiteria are given below.**

| Building block | Hosts need |
|---|---|
| A | 110 |
| B | 50 |
| C | 20 |
| D | 8 |

**Calculate the network and broadcast address of this network for each building block.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1443 (ET: N/A)]*

    Answer: This is VLSM. Sort the requirements largest first, then allocate sequentially.

    Given 192.168.0.0/24 = 256 addresses.

    Step 1 – block size for each building

    | Block | Hosts needed | Needs (hosts + 2) | Power of 2 | Prefix |
    |---|---|---|---|---|
    | A | 110 | 112 | 128 | /25 |
    | B | 50 | 52 | 64 | /26 |
    | C | 20 | 22 | 32 | /27 |
    | D | 8 | 10 | 16 | /28 |

    Step 2 – allocate in order, largest first

    | Block | Network address | Broadcast address | Usable range | Usable hosts |
    |---|---|---|---|---|
    | A | 192.168.0.0/25 | 192.168.0.127 | .1 – .126 | 126 |
    | B | 192.168.0.128/26 | 192.168.0.191 | .129 – .190 | 62 |
    | C | 192.168.0.192/27 | 192.168.0.223 | .193 – .222 | 30 |
    | D | 192.168.0.224/28 | 192.168.0.239 | .225 – .238 | 14 |

    - Total used = 128 + 64 + 32 + 16 = 240 addresses.
    - Left free: 192.168.0.240/28 (16 addresses) for future expansion.
    - Note: always add 2 to the host requirement before rounding up, because the network and broadcast addresses cannot be given to a host.

14. **Check the valid IP address from the following table.** *[BREB Assistant Programmer (AP) 21.02.2025 compact it 1335 (ET: N/A)]*

    Answer: The table was not printed with the question, so the rules for checking validity are given.

    An IPv4 address is valid when
    - It has exactly four octets separated by dots.
    - Every octet is a decimal number from 0 to 255. Anything above 255 is invalid.
    - No octet is left blank and there are no letters.

    Addresses that are numerically valid but cannot be assigned to a host
    - Network address – all host bits 0 (e.g. 192.168.1.0/24)
    - Broadcast address – all host bits 1 (e.g. 192.168.1.255/24)
    - 127.0.0.0/8 – loopback
    - 0.0.0.0 – "this network" / default route
    - 169.254.0.0/16 – APIPA, self-assigned when DHCP fails
    - 224.0.0.0 – 239.255.255.255 – Class D multicast
    - 240.0.0.0 – 255.255.255.255 – Class E, reserved

    Examples

    | Address | Valid? | Reason |
    |---|---|---|
    | 192.168.1.10 | Yes | All octets 0–255, host address |
    | 256.10.10.1 | No | 256 exceeds 255 |
    | 172.16.5.256 | No | Last octet out of range |
    | 10.0.0.0/8 | Valid address, not assignable | Network address |
    | 127.0.0.1 | Valid, but loopback only | Reserved range |
    | 192.168.1 | No | Only three octets |

15. **(a) A network has been assigned the IP address 200.1.2.0/24. It has 3 subnets. Determine the following for each subnet:** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1352 (ET: N/A)]*
 * **(i) Total number of IP addresses**
 * **(ii) Range of usable IP addresses**
 * **(iii) Network address**
 * **(iv) Direct broadcast address**
 * **(v) Limited broadcast address.**

    Answer: Given 200.1.2.0/24 (Class C), 3 subnets required.

    Step 1 – bits to borrow
    - 2^n >= 3 -> 2^2 = 4, so borrow 2 bits (4 subnets are created, 3 are used)
    - New prefix = /26, mask 255.255.255.192, block size 64

    Step 2 – details for each subnet

    | Subnet | (iii) Network address | (ii) Usable range | (iv) Directed broadcast | (i) Total addresses |
    |---|---|---|---|---|
    | 1 | 200.1.2.0/26 | 200.1.2.1 – 200.1.2.62 | 200.1.2.63 | 64 |
    | 2 | 200.1.2.64/26 | 200.1.2.65 – 200.1.2.126 | 200.1.2.127 | 64 |
    | 3 | 200.1.2.128/26 | 200.1.2.129 – 200.1.2.190 | 200.1.2.191 | 64 |

    - (i) Total IP addresses per subnet = 2^6 = 64; usable = 62.
    - (v) Limited broadcast address = `255.255.255.255` for every subnet. It is the same for all networks, it is never routed, and it reaches only the local segment.
    - Difference to remember: a directed broadcast (200.1.2.63) targets one specific subnet and can in principle be routed; a limited broadcast (255.255.255.255) never leaves the local link.

16. **The IP address of a device in a network is 172.16.128.123/22. Answer the following questions:** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1343 (ET: N/A)]*
   * **i) What is the network address?**
   * **ii) What is the subnet mask for the given network?**
   * **iii) What is the broadcast address?**
   * **iv) What is the maximum number of devices this network can connect?**
   * **v) What is the IP address of the first host device in the network?**

    Answer: Given 172.16.128.123/22, host bits = 10, block size in the third octet = 256 − 252 = 4.

    - Third octet 128 is a multiple of 4, so the block begins at 172.16.128.0.

    | # | Item | Value |
    |---|---|---|
    | i | Network address | `172.16.128.0` |
    | ii | Subnet mask | `255.255.252.0` (/22) |
    | iii | Broadcast address | `172.16.131.255` |
    | iv | Maximum devices | 2^10 − 2 = `1022` |
    | v | First host address | `172.16.128.1` |

    - Address range covered: 172.16.128.0 – 172.16.131.255, last usable host 172.16.131.254.

17. **Find the network address, subnet mask, broadcast address, and usable host IP range for the following IP address: 192.9.205.31/16.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1339 (ET: N/A)]*

    Answer: Given 192.9.205.31/16. The prefix /16 is applied as written, ignoring the Class C default.

    - Mask: /16 = `255.255.0.0`
    - AND operation: 192.9.205.31 AND 255.255.0.0 -> `192.9.0.0`

    | Item | Value |
    |---|---|
    | Network address | 192.9.0.0 |
    | Subnet mask | 255.255.0.0 |
    | Broadcast address | 192.9.255.255 |
    | Usable host range | 192.9.0.1 – 192.9.255.254 |
    | Usable hosts | 2^16 − 2 = 65,534 |

    - Note: 192.9.205.31 is by class a Class C address whose default mask is /24. Using /16 here is supernetting — combining 256 Class C networks into one larger block, which classless (CIDR) addressing permits.

18. **What is the CIDR Prefixes exactly represents the range of IP addresses 10.12.2.0 to 10.12.3.255?** *[BCIC Assistant Programmer 14.02.2025 compact it 1328 (ET: BUET)]*

    Answer: The range 10.12.2.0 – 10.12.3.255 must be expressed as a single CIDR block.

    Step 1 – count the addresses
    - From 10.12.2.0 to 10.12.3.255 = 2 full /24 blocks = 2 × 256 = 512 addresses

    Step 2 – find the prefix
    - 512 = 2^9, so host bits = 9
    - Prefix = 32 − 9 = `/23`

    Step 3 – verify the boundary
    ```
    10.12.2.0 -> 00001010.00001100.00000010.00000000
    10.12.3.255-> 00001010.00001100.00000011.11111111
                                     ^^^^^^^ first 23 bits identical
    ```
    - Third octet 2 is even, so it is a valid /23 boundary.

    Answer: `10.12.2.0/23`, mask 255.255.254.0, broadcast 10.12.3.255, 510 usable hosts.

19. **Write down the private IP address rang for class B?** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*

    Answer: The Class B private range is `172.16.0.0 – 172.31.255.255`.

    - CIDR notation: `172.16.0.0/12`
    - Mask: 255.240.0.0
    - Total addresses: 1,048,576 (16 consecutive Class B networks, 172.16 through 172.31)
    - Defined by RFC 1918, used for medium-sized organisations.

    - Common mistake: 172.32.x.x and 172.15.x.x are public, not private. Only the second octet 16–31 is private.

20. **Given IP address 192.168.0.0/28, determine Network address, Broadcast address, First usable IP, Last usable IP.** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*

    Answer: /28 -> host bits = 4, block size = 16, mask = 255.255.255.240.

    | Item | Value |
    |---|---|
    | Network address | 192.168.0.0 |
    | Broadcast address | 192.168.0.15 |
    | First usable IP | 192.168.0.1 |
    | Last usable IP | 192.168.0.14 |

    - Usable hosts = 2^4 − 2 = 14.

21. **Write range of private IP address Class A, B and C.** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*

    Answer: The private ranges are defined by RFC 1918. They are not routed on the public internet and must be translated by NAT.

    | Class | Private range | CIDR | Mask | Addresses |
    |---|---|---|---|---|
    | A | 10.0.0.0 – 10.255.255.255 | 10.0.0.0/8 | 255.0.0.0 | 16,777,216 |
    | B | 172.16.0.0 – 172.31.255.255 | 172.16.0.0/12 | 255.240.0.0 | 1,048,576 |
    | C | 192.168.0.0 – 192.168.255.255 | 192.168.0.0/16 | 255.255.0.0 | 65,536 |

    - Class A is used by large enterprises and cloud networks, Class B by medium organisations, Class C by home and small office routers.

22. **Given an IP address 192.168.111.169/28. Then Determine the (i) Network address (ii) Broadcast address (iii) First usable Host (iv) Last usable Host.** *[BBA Assistant Maintenance Engineer 12.07.2025 compact it 1431 (ET: BUET)]*

    Answer: /28 -> host bits 4, block size 16, mask 255.255.255.240.

    Step – find the block that contains .169
    - Blocks in the last octet: 0, 16, 32 … 144, 160, 176 …
    - 169 falls between 160 and 175, so the block starts at 160.

    | # | Item | Value |
    |---|---|---|
    | i | Network address | `192.168.111.160` |
    | ii | Broadcast address | `192.168.111.175` |
    | iii | First usable host | `192.168.111.161` |
    | iv | Last usable host | `192.168.111.174` |

    - Usable hosts = 14.
    - Shortcut: network address = floor(169 ÷ 16) × 16 = 10 × 16 = 160.

23. **What are the private IP Ranges for the following IP classes? Class A, Class B and Class C** *[BBA Assistant Maintenance Engineer 12.07.2025 compact it 1431 (ET: BUET)]*

    Answer: RFC 1918 private ranges.

    | Class | Private IP range | CIDR |
    |---|---|---|
    | Class A | 10.0.0.0 – 10.255.255.255 | 10.0.0.0/8 |
    | Class B | 172.16.0.0 – 172.31.255.255 | 172.16.0.0/12 |
    | Class C | 192.168.0.0 – 192.168.255.255 | 192.168.0.0/16 |

    - These addresses can be reused freely inside any organisation because routers on the internet drop them. A NAT device converts them to a public address for outside communication.

24. **Which is Class C Default Subnet Mask?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

    Answer: The Class C default subnet mask is `255.255.255.0`, that is `/24`.

    - Class C uses the first three octets for the network ID and the last octet for the host ID.
    - Binary: 11111111.11111111.11111111.00000000
    - Hosts per Class C network = 2^8 − 2 = 254.

    Default masks of all three usable classes

    | Class | First octet range | Default mask | CIDR |
    |---|---|---|---|
    | A | 1 – 126 | 255.0.0.0 | /8 |
    | B | 128 – 191 | 255.255.0.0 | /16 |
    | C | 192 – 223 | 255.255.255.0 | /24 |

25. **What is the maximum number of valid hosts in a network?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

    Answer: The maximum number of valid (usable) hosts in a network is

    ```
    Usable hosts = 2^h − 2
    ```
    where h = number of host bits = 32 − prefix length.

    - Two addresses are subtracted: the all-zeros address is the network ID, and the all-ones address is the broadcast address. Neither can be assigned to a device.

    Examples
    - /24 -> 2^8 − 2 = 254
    - /26 -> 2^6 − 2 = 62
    - /30 -> 2^2 − 2 = 2
    - Class A (/8) -> 2^24 − 2 = 16,777,214, which is the largest possible in classful IPv4.

    - Exception: RFC 3021 allows a /31 to use both addresses on a point-to-point link, giving 2 hosts.

26. **Given IP address 10.2.3.20/22 find the Total valid Host address in this IP?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

    Answer: Given 10.2.3.20/22.

    Step 1 – host bits
    - h = 32 − 22 = 10

    Step 2 – total and valid hosts
    - Total addresses = 2^10 = 1024
    - Valid (usable) hosts = 1024 − 2 = `1022`

    Supporting details
    - Mask = 255.255.252.0, block size in the third octet = 256 − 252 = 4
    - Third octet 3 falls in the block starting at 0, so the network is 10.2.0.0/22
    - Range 10.2.0.0 – 10.2.3.255, usable 10.2.0.1 – 10.2.3.254, broadcast 10.2.3.255

27. **Mapping between MAC to IP address?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

    Answer: Mapping an IP address to a MAC address is done by `ARP` (Address Resolution Protocol); mapping a MAC address to an IP address is done by `RARP` (Reverse ARP), now replaced in practice by BOOTP and DHCP.

    How ARP works
    - The sender needs the MAC address for a known IP on its own LAN.
    - It broadcasts an ARP Request: "Who has 192.168.1.10? Tell 192.168.1.5."
    - Only the owner replies with an ARP Reply (unicast) carrying its MAC address.
    - The pair is stored in the ARP cache for a few minutes, so the broadcast is not repeated for every packet.
    - Command to view the table: `arp -a`.

    ```
    PC-A                                    PC-B
     |-- ARP Request (broadcast FF:FF:FF:FF:FF:FF) -->|
     |     "Who has 192.168.1.10?"                    |
     |<-- ARP Reply (unicast) ------------------------|
     |     "192.168.1.10 is at 00:1A:2B:3C:4D:5E"     |
    ```

    - Related protocols: Proxy ARP (a router answers on behalf of another host), Gratuitous ARP (announces its own mapping), and NDP, which replaces ARP in IPv6.

28. **How many bits are in a MAC address?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

    Answer: A MAC address is `48 bits` long, that is 6 bytes.

    - It is written as 12 hexadecimal digits, for example `00:1A:2B:3C:4D:5E`.
    - The first 24 bits are the OUI (Organizationally Unique Identifier), which identifies the manufacturer.
    - The last 24 bits are the serial number assigned by that manufacturer to the individual card.
    - It is also called the physical address, hardware address or burned-in address (BIA).
    - The broadcast MAC address is FF:FF:FF:FF:FF:FF.
    - The newer EUI-64 format used in IPv6 is 64 bits.

29. **What is the primary motivation for classful IP address to classless IP addressing?** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 316 (ET: N/A)]*

    Answer: The primary motivation was the rapid `exhaustion of IPv4 address space caused by the wastage built into classful addressing`.

    The problem with classful addressing
    - Only three block sizes existed: /8 (16.7 million hosts), /16 (65,534) and /24 (254).
    - An organisation needing 500 hosts could not use a Class C, so it received a full Class B and wasted more than 64,000 addresses.
    - An organisation needing 300 hosts had the same problem.
    - Millions of addresses were allocated but never used.

    Secondary motivation – routing table explosion
    - Every allocated network needed its own routing table entry. Backbone routers were running out of memory and lookup time.

    How classless (CIDR) addressing solved it
    - Any prefix length from /0 to /32 is allowed, so a block can be sized to actual need — 500 hosts get a /23 (510 hosts) instead of a /16.
    - VLSM lets different subnets of the same network use different mask lengths.
    - Route aggregation (supernetting) merges many small blocks into one advertisement, shrinking global routing tables.
    - Standardised in RFC 1519 (1993), together with NAT and later IPv6 as the long-term fix.

30. **Given IP address 192.168.1.50, Subnet Mask: 255.255.255.240. Find the valid IP range. Also find Network address and Broadcast address.** *[NWPGCL Assistant Manager (ICT) 12.01.2024 compact it 292 (ET: BUET)], [BTCL Assistant Manager (Technical) 2023 compact it 594 (ET: BUET)], [BPDB Assistant Engineer (CSE) 10.05.2024 compact it 389 (ET: BUET)], [BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 456 (ET: BUET)]*

    Answer: Mask 255.255.255.240 = /28, host bits 4, block size = 256 − 240 = 16.

    Step 1 – find the block containing .50
    - Blocks in the last octet: 0, 16, 32, 48, 64 …
    - 50 falls between 48 and 63, so the block starts at 48.

    | Item | Value |
    |---|---|
    | Network address | `192.168.1.48` |
    | Valid host range | `192.168.1.49 – 192.168.1.62` |
    | Broadcast address | `192.168.1.63` |
    | Usable hosts | 14 |

    ```
    Network   192.168.1.0011 0000 = 192.168.1.48
    Broadcast 192.168.1.0011 1111 = 192.168.1.63
    ```

31. **Given IP Address: 192.168.5.154/27, Calculate a) Network Address b) First valid host c) Last valid host d) Broadcast address e) Subnet mask** *[NSDA Assistant Maintenance Engineer 11.05.2024 compact it 383 (ET: N/A)]*

    Answer: /27 -> host bits 5, block size = 32, mask = 255.255.255.224.

    Find the block containing .154
    - Blocks: 0, 32, 64, 96, 128, 160 …
    - 154 falls between 128 and 159, so the block starts at 128.

    | # | Item | Value |
    |---|---|---|
    | a | Network address | `192.168.5.128` |
    | b | First valid host | `192.168.5.129` |
    | c | Last valid host | `192.168.5.158` |
    | d | Broadcast address | `192.168.5.159` |
    | e | Subnet mask | `255.255.255.224` |

    - Usable hosts = 2^5 − 2 = 30.

32. **Write down the Public and Private IPv4 address for Class A, Class B and Class C.** *[NSDA Assistant Maintenance Engineer 11.05.2024 compact it 384 (ET: N/A)]*

    Answer:

    | Class | Public (assignable) range | Private range (RFC 1918) | Default mask |
    |---|---|---|---|
    | A | 1.0.0.0 – 126.255.255.255 (excluding 10.x) | 10.0.0.0 – 10.255.255.255 | 255.0.0.0 |
    | B | 128.0.0.0 – 191.255.255.255 (excluding 172.16–172.31) | 172.16.0.0 – 172.31.255.255 | 255.255.0.0 |
    | C | 192.0.0.0 – 223.255.255.255 (excluding 192.168.x) | 192.168.0.0 – 192.168.255.255 | 255.255.255.0 |

    Key points
    - Public addresses are globally unique, allocated by IANA through the regional registries, and routable on the internet.
    - Private addresses are free to reuse, are dropped by internet routers, and need NAT to reach the outside.
    - 127.0.0.0/8 is reserved for loopback and is not part of the usable Class A range.
    - 169.254.0.0/16 (APIPA) is link-local, assigned automatically when a DHCP server cannot be reached.

33. **(b) What is a subnet? What benefits will you get using subnets for this office?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 324 (ET: BIBM)]*

    Answer:

    What is a subnet
    - A subnet is a smaller logical network created by dividing a larger IP network. Bits are borrowed from the host portion and added to the network portion, so one address block serves several separate segments.
    - Example: 192.168.1.0/24 split into four /26 subnets, one per department.

    Benefits for an office network
    - Smaller broadcast domains – ARP and other broadcasts stay inside one department instead of flooding every PC, which reduces congestion.
    - Better performance – less unnecessary traffic on each segment.
    - Security and isolation – Accounts can be separated from Sales, and an ACL on the router controls what passes between them. A problem in one subnet does not spread.
    - Easier troubleshooting – an IP address immediately tells you which department and floor a machine belongs to.
    - Efficient address use – VLSM gives each department only as many addresses as it needs.
    - Simpler policy and management – QoS, firewall rules and DHCP scopes can be applied per subnet.
    - Scalability – a new department is added as a new subnet without renumbering the whole office.

34. **Local loopback address কি? কোন কমান্ড ব্যবহার করে কানেক্টিভিটি টেস্ট করা হয়?** *[BTCL - JAM ( Technical) 05.04.2024 compact it 383 (ET: BUET)]*

    Answer:

    Local loopback address
    - The loopback address is `127.0.0.1` (the whole block 127.0.0.0/8 is reserved). Its hostname is `localhost`.
    - Packets sent to it never leave the machine — they are looped back inside the TCP/IP stack by the software.
    - Uses: testing whether the TCP/IP stack and NIC driver are working, testing a locally running server (for example `http://127.0.0.1:8080`), and development work before deployment.
    - In IPv6 the loopback address is `::1`.

    Connectivity test command
    - `ping` is the command used, for example `ping 127.0.0.1` or `ping 8.8.8.8`.
    - ping uses ICMP Echo Request and Echo Reply messages, and reports round-trip time and packet loss.

    Other useful commands

    | Command | Purpose |
    |---|---|
    | `ping` | Basic reachability and round-trip time |
    | `tracert` (Windows) / `traceroute` (Linux) | Shows every router along the path |
    | `ipconfig` / `ifconfig` | Shows the local IP configuration |
    | `nslookup` / `dig` | DNS name resolution test |
    | `netstat` | Active connections and listening ports |

35. **Given IP address 192.168. 2.0/ 24; Determine to network address and broadcast address.** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 405 (ET: N/A)]*

    Answer: /24 -> host bits 8, mask 255.255.255.0.

    - Network address: `192.168.2.0`
    - Broadcast address: `192.168.2.255`
    - Usable host range: 192.168.2.1 – 192.168.2.254
    - Usable hosts: 254

    ```
    Network   192.168.2.00000000 = 192.168.2.0
    Broadcast 192.168.2.11111111 = 192.168.2.255
    ```

36. **Given a (slash) /26 based network address. Find Subnet mask, broadcast address, number of host, Number of valid host and number of subnet.** *[BKSP Assistant Programmer 13.07.2024 compact it 1459 (ET: N/A)]*

    Answer: A /26 network — assuming it is carved out of a Class C /24 block.

    | Item | Value | Working |
    |---|---|---|
    | Subnet mask | `255.255.255.192` | 11111111.11111111.11111111.11000000 |
    | Block size | 64 | 256 − 192 |
    | Number of hosts (total addresses) | 64 | 2^(32−26) = 2^6 |
    | Number of valid hosts | 62 | 64 − 2 |
    | Number of subnets | 4 | 2^2, borrowing 2 bits from /24 |
    | Broadcast address | last address of each block | e.g. for 192.168.1.0/26 it is 192.168.1.63 |

    The four subnets of 192.168.1.0/24

    | Subnet | Network | Broadcast | Usable range |
    |---|---|---|---|
    | 1 | 192.168.1.0 | 192.168.1.63 | .1 – .62 |
    | 2 | 192.168.1.64 | 192.168.1.127 | .65 – .126 |
    | 3 | 192.168.1.128 | 192.168.1.191 | .129 – .190 |
    | 4 | 192.168.1.192 | 192.168.1.255 | .193 – .254 |

    - Note: the number of subnets depends on the parent block. From a /16 parent, a /26 would give 2^10 = 1024 subnets.

37. **Write Class A private IP range.** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

    Answer: The Class A private range is `10.0.0.0 – 10.255.255.255`.

    - CIDR: `10.0.0.0/8`, mask 255.0.0.0
    - Total addresses: 2^24 = 16,777,216 (16,777,214 usable)
    - It is a single large block, defined by RFC 1918.
    - Because it is so large, it is the range used by big enterprises, data centres, cloud VPCs and mobile carriers.

38. **Write Command for check LAN connecte?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

    Answer: The command normally used to check LAN connectivity is `ping`.

    - `ping <IP address>` — for example `ping 192.168.1.1` to test the gateway.
    - It sends ICMP Echo Requests and waits for Echo Replies, showing reply time and packet loss.

    Standard troubleshooting order
    - `ping 127.0.0.1` — is the TCP/IP stack working?
    - `ping <own IP>` — is the NIC configured?
    - `ping <gateway>` — is the LAN path working?
    - `ping 8.8.8.8` — is the internet reachable?
    - `ping google.com` — is DNS working?

    Other commands

    | Command | Purpose |
    |---|---|
    | `ipconfig /all` (Windows) or `ifconfig` / `ip addr` (Linux) | View IP, mask, gateway, MAC |
    | `arp -a` | List devices seen on the LAN |
    | `tracert` / `traceroute` | Trace the path hop by hop |
    | `netstat -an` | Show connections and listening ports |
    | `nslookup` | Test DNS resolution |

39. **(a) Given 4 Network interface in a table and find which of the following network is on which network.** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 433 (ET: BUET)]*

    Answer: The interface table was not printed with the question, so the method for deciding which interface belongs to which network is given.

    Method – AND the IP address with its subnet mask
    - The result of the bitwise AND is the network address of that interface.
    - Two interfaces are on the same network only when their network addresses AND their masks are both identical.

    Worked example
    ```
    Interface 1 : 192.168.1.10 /26   -> block size 64, 10 lies in 0–63  -> network 192.168.1.0/26
    Interface 2 : 192.168.1.70 /26   -> 70 lies in 64–127               -> network 192.168.1.64/26
    Interface 3 : 192.168.1.100/26   -> 100 lies in 64–127              -> network 192.168.1.64/26
    Interface 4 : 192.168.2.10 /26   -> different third octet           -> network 192.168.2.0/26
    ```
    - Result: interfaces 2 and 3 are on the same network and can talk directly. Interfaces 1 and 4 each sit on their own network and need a router.

    Quick shortcut without binary
    - Block size = 256 − (mask value of the interesting octet).
    - Network address = the largest multiple of the block size that is not greater than the octet value.

40. **(খ) Classful এবং Classless IP address এর পার্থক্য কী? নিচের IP গুলোর Class নির্ণয় করুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*
i) 00000001 00001011 00001011 11101111
ii) 211.10.15.4

    Answer:

    (a) Classful vs Classless IP addressing

    | Point | Classful | Classless (CIDR) |
    |---|---|---|
    | Division | Fixed classes A, B, C, D, E | No classes, any prefix length |
    | Mask | Default mask fixed by the first octet | Mask written explicitly, /0 to /32 |
    | Efficiency | Very wasteful; a 500-host firm takes a Class B | Block sized to exact need |
    | Subnetting | FLSM — all subnets equal | VLSM — subnets of different sizes |
    | Aggregation | Not possible | Supernetting shrinks routing tables |
    | Routing protocol | RIPv1, IGRP (mask not carried) | RIPv2, OSPF, EIGRP, BGP (mask carried) |
    | Standard | RFC 791 (1981) | RFC 1519 (1993) |

    (b) Class of the given addresses

    (i) 00000001 00001011 00001011 11101111
    - Decimal: 00000001 = 1, 00001011 = 11, 00001011 = 11, 11101111 = 239
    - Address = `1.11.11.239`
    - First octet 1 lies in 1–126, leading bit is `0`
    - Class: `Class A`, default mask 255.0.0.0

    (ii) 211.10.15.4
    - First octet 211 lies in 192–223, leading bits `110`
    - Class: `Class C`, default mask 255.255.255.0

    Rule of thumb for the first octet
    ```
    0xxxxxxx  1 – 126    Class A
    10xxxxxx  128 – 191  Class B
    110xxxxx  192 – 223  Class C
    1110xxxx  224 – 239  Class D (multicast)
    1111xxxx  240 – 255  Class E (reserved)
    ```

41. **6.10 An organization is granted the IPv4 network block 14.24.74.0/24 and needs to segment it into two subnets: Subnet A (requires 120 addresses) and Subnet B (requires 60 addresses). Allocating sequentially from the requirement first to maximize remaining address space, state only the Network Address (with its CIDR mask) and the Broadcast Address for both subnets.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

    Answer: Same VLSM problem — largest subnet first.

    Given 14.24.74.0/24 = 256 addresses.

    Step 1 – Subnet A (120 addresses)
    - 2^7 = 128 >= 120, so 7 host bits -> `/25`, block size 128
    - Network `14.24.74.0/25`, broadcast `14.24.74.127`
    - Usable range 14.24.74.1 – 14.24.74.126 (126 hosts)

    Step 2 – Subnet B (60 addresses)
    - 2^6 = 64 >= 60, so 6 host bits -> `/26`, block size 64
    - Begins at the next free address, 14.24.74.128
    - Network `14.24.74.128/26`, broadcast `14.24.74.191`
    - Usable range 14.24.74.129 – 14.24.74.190 (62 hosts)

    | Subnet | Requirement | Network address | Broadcast address |
    |---|---|---|---|
    | A | 120 | 14.24.74.0/25 | 14.24.74.127 |
    | B | 60 | 14.24.74.128/26 | 14.24.74.191 |

    - Remaining free space: 14.24.74.192/26 (64 addresses).

42. **An IP address subnet mask is 255.255.255.224 which is the subnet address in this block?** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*

    Answer: Mask 255.255.255.224 = /27.

    Step 1 – block size
    - 256 − 224 = 32, so subnet addresses step by 32 in the last octet.

    Step 2 – the subnet (block) addresses are the multiples of 32
    ```
    x.x.x.0    broadcast .31
    x.x.x.32   broadcast .63
    x.x.x.64   broadcast .95
    x.x.x.96   broadcast .127
    x.x.x.128  broadcast .159
    x.x.x.160  broadcast .191
    x.x.x.192  broadcast .223
    x.x.x.224  broadcast .255
    ```

    - So a given host address belongs to the block whose start is the largest multiple of 32 not greater than its last octet.
    - Rule: network address = floor(last octet ÷ 32) × 32. For 192.168.1.100, floor(100 ÷ 32) = 3, so the subnet address is 192.168.1.96/27.
    - Each /27 gives 32 addresses, 30 usable, and 8 subnets fit in one /24.

43. **Write down the basic differences of the following:**
   **(i) Public vs Private IP address** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 534 (ET: MIST)]*

    Answer: Public vs Private IP address

    | Point | Public IP | Private IP |
    |---|---|---|
    | Uniqueness | Globally unique on the internet | Unique only inside one organisation |
    | Assigned by | IANA / regional registry, through the ISP | The local network administrator or DHCP |
    | Routable | Yes, routed across the internet | No, internet routers drop it |
    | Reuse | Cannot be reused anywhere else | The same range is reused by millions of networks |
    | Cost | Paid, limited supply | Free, unlimited |
    | Range | Everything except the reserved blocks | 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 |
    | Security | Directly reachable, so more exposed | Hidden behind NAT, less exposed |
    | Example | 8.8.8.8, 103.108.140.5 | 192.168.1.1, 10.0.0.5 |

    - How they work together: a home router holds one public IP on its WAN side and hands out private IPs on the LAN side. NAT translates between them, which is a major reason IPv4 has lasted so long.

44. **What do you mean by Subnet and Subnet Mask? The network address of 172.16.0.0/19 provides how many subnets and hosts? What is the function of OSPF?** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 536 (ET: MIST)]*

    Answer:

    Subnet and subnet mask
    - A subnet is a smaller network created by dividing a larger IP block, by borrowing bits from the host portion.
    - A subnet mask is the 32-bit number that shows which bits are network and which are host: network bits are 1, host bits are 0. Example: /26 = 255.255.255.192.

    Subnets and hosts in 172.16.0.0/19
    - 172.16.0.0 is a Class B address, so the default prefix is /16.
    - Borrowed bits = 19 − 16 = 3
    - Number of subnets = 2^3 = `8`
    - Host bits = 32 − 19 = 13
    - Hosts per subnet = 2^13 − 2 = `8190`
    - Mask = 255.255.224.0, block size in the third octet = 32
    - The eight subnets are 172.16.0.0, 172.16.32.0, 172.16.64.0, 172.16.96.0, 172.16.128.0, 172.16.160.0, 172.16.192.0, 172.16.224.0.

    Function of OSPF
    - OSPF (Open Shortest Path First) is a link-state, classless interior gateway protocol that finds the best path inside one autonomous system.
    - Each router builds a complete map of the area (the link-state database) and runs Dijkstra's shortest path first algorithm on it.
    - Metric is cost, based on bandwidth. It supports VLSM and CIDR, converges quickly, and sends only incremental updates rather than the whole table.
    - It uses areas (with Area 0 as the backbone) to keep large networks scalable, and authentication to secure routing updates.

45. **Convert the decimal IP address 192.168.101.5 into binary IP address. Fill-up the following in tabular form:** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 539 (ET: MIST)]*
| Address Class | First Octet Decimal Range | Example of IP Address (IPA) | Network ID of IPA | Host ID of IPA |
|---|---|---|---|---|
| Class A |  |  |  |  |
| Class B |  |  |  |  |
| Class C |  |  |  |  |

    Answer:

    Binary form of 192.168.101.5
    ```
    192 -> 11000000
    168 -> 10101000
    101 -> 01100101
      5 -> 00000101
    ```
    - Answer: `11000000.10101000.01100101.00000101`
    - Method: divide each octet by 2 repeatedly, or subtract place values 128, 64, 32, 16, 8, 4, 2, 1.

    Completed table

    | Address Class | First Octet Decimal Range | Example of IP Address (IPA) | Network ID of IPA | Host ID of IPA |
    |---|---|---|---|---|
    | Class A | 1 – 126 | 10.25.30.40 | 10.0.0.0 | 0.25.30.40 |
    | Class B | 128 – 191 | 172.16.50.60 | 172.16.0.0 | 0.0.50.60 |
    | Class C | 192 – 223 | 192.168.101.5 | 192.168.101.0 | 0.0.0.5 |

    - Class A uses 1 octet for the network and 3 for hosts, Class B uses 2 and 2, Class C uses 3 and 1.
    - 127 is skipped because 127.0.0.0/8 is reserved for loopback.

46. **What is IP address? Explain the necessity of IP address in network?** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 564 (ET: N/A)]*

    Answer:

    What is an IP address
    - An IP address is a unique logical address given to every device on a TCP/IP network, used to identify the device and to find its location in the network.
    - IPv4 is 32 bits, written as four decimal octets (192.168.1.10). IPv6 is 128 bits, written in hexadecimal.
    - It has two parts: the network ID, which says which network the device is on, and the host ID, which says which device it is inside that network. The subnet mask decides where the split falls.
    - It can be static (fixed manually) or dynamic (assigned by DHCP).

    Why an IP address is necessary
    - Identification – it names the device, in the same way a postal address names a house.
    - Routing – routers read the network portion to decide where to forward a packet. Without it there is no way to reach a device outside the LAN.
    - End-to-end delivery – MAC addresses only work inside one LAN segment; the IP address carries the packet across many networks.
    - Hierarchy and scalability – the network/host split lets routers keep summarised routes instead of an entry per device.
    - Access control – firewalls and ACLs permit or block traffic based on IP addresses.
    - Services – DNS maps a name to an IP, NAT translates private to public, and QoS policies are applied per address.

47. **What is subnet mask? Why it is used?** *[Mongla Port Authority Assistant Programmer 2023 compact it 573 (ET: N/A)]*

    Answer:

    What is a subnet mask
    - A 32-bit number used together with an IP address to separate the network portion from the host portion.
    - Continuous 1s mark the network bits, continuous 0s mark the host bits. Example: 255.255.255.0 = /24 = 11111111.11111111.11111111.00000000.
    - The device performs a bitwise AND of the IP address and the mask to get the network address.

    Why it is used
    - To find the network address – AND the IP with the mask. This is how a host knows which network it belongs to.
    - To decide local or remote delivery – the sender ANDs both its own IP and the destination IP with the mask. If the results match, it sends the frame directly; if not, it sends the packet to the default gateway.
    - To enable subnetting – borrowing host bits into the mask splits one network into many, cutting broadcast traffic and improving security.
    - To calculate capacity – the mask fixes the number of usable hosts, 2^h − 2.
    - To support VLSM and CIDR – different masks on different segments avoid address wastage.
    - To let routers work – routing table lookups use the longest matching prefix, which is a mask comparison.

    Example
    ```
    IP      192.168.1.10   -> 11000000.10101000.00000001.00001010
    Mask    255.255.255.0  -> 11111111.11111111.11111111.00000000
    AND     192.168.1.0    -> the network address
    ```

48. **In HR department have 12 IP enable devices are available in our office and have a big IP block 172.16.5.0/24. To consider your HR department find a suitable IP block than also answer the following question.**
   **i. Subnet mask; ii. Number of usable IP address; iii. First and last IP Address of that block iv. Broadcast IP address** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 596 (ET: N/A)]*

    Answer: Given the block 172.16.5.0/24 and a requirement of 12 IP-enabled devices in HR.

    Step 1 – choose the right block size
    - Needed = 12 hosts + 2 (network and broadcast) = 14 addresses
    - Next power of 2: 2^4 = 16, so host bits = 4
    - Prefix = 32 − 4 = `/28`
    - Suitable block: `172.16.5.0/28`

    Step 2 – the answers

    | # | Item | Value |
    |---|---|---|
    | i | Subnet mask | `255.255.255.240` (/28) |
    | ii | Usable IP addresses | 2^4 − 2 = `14` |
    | iii | First and last usable IP | `172.16.5.1` and `172.16.5.14` |
    | iv | Broadcast IP address | `172.16.5.15` |

    - 14 usable addresses cover the 12 devices with 2 spare for growth.
    - A /29 would give only 6 usable addresses, which is too few — that is why /28 is the smallest workable choice.
    - The rest of the /24 (172.16.5.16 onwards) stays free for the other departments.

49. **What is private IP range class A, B and C with maximum host of each class?** *[BREB Assistant Programmer 18.02.2023 compact it 470 (ET: N/A)]*

    Answer:

    | Class | Private range | CIDR | Default mask | Maximum hosts per network |
    |---|---|---|---|---|
    | A | 10.0.0.0 – 10.255.255.255 | 10.0.0.0/8 | 255.0.0.0 | 2^24 − 2 = 16,777,214 |
    | B | 172.16.0.0 – 172.31.255.255 | 172.16.0.0/12 | 255.255.0.0 | 2^16 − 2 = 65,534 per /16 |
    | C | 192.168.0.0 – 192.168.255.255 | 192.168.0.0/16 | 255.255.255.0 | 2^8 − 2 = 254 per /24 |

    - The Class B private space is 16 consecutive /16 networks (172.16 to 172.31), and the Class C private space is 256 consecutive /24 networks (192.168.0 to 192.168.255).
    - Defined in RFC 1918; these addresses are never routed on the internet and require NAT.

50. **(b) Find out the default mask, network address and broadcast address of the classful IPv4 address: 172.16.99.45** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 480 (ET: N/A)]*

    Answer: The address 172.16.99.45 must be read in the classful way.

    Step 1 – identify the class
    - First octet 172 lies in 128–191, so it is `Class B`.

    Step 2 – default mask
    - Class B default mask = `255.255.0.0` (/16)

    Step 3 – network address
    ```
    IP    172.16.99.45   -> 10101100.00010000.01100011.00101101
    Mask  255.255.0.0    -> 11111111.11111111.00000000.00000000
    AND   172.16.0.0
    ```
    - Network address: `172.16.0.0`

    Step 4 – broadcast address
    - Set all 16 host bits to 1: `172.16.255.255`

    | Item | Value |
    |---|---|
    | Class | B |
    | Default mask | 255.255.0.0 |
    | Network address | 172.16.0.0 |
    | Broadcast address | 172.16.255.255 |
    | Usable range | 172.16.0.1 – 172.16.255.254 |
    | Usable hosts | 65,534 |

51. **Identify the class, network IP address, direct broadcast address and limited broadcast address of the following IP address: (i) 1.2.3.4 (ii) 130.1.2.3 (iii) 220.15.1.10 (iv) 200.1.10.100** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 637 (ET: N/A)]*

    Answer: Each address is read with its classful default mask.

    | Address | Class | Network IP address | Directed broadcast | Limited broadcast |
    |---|---|---|---|---|
    | (i) 1.2.3.4 | A (1–126) | 1.0.0.0 | 1.255.255.255 | 255.255.255.255 |
    | (ii) 130.1.2.3 | B (128–191) | 130.1.0.0 | 130.1.255.255 | 255.255.255.255 |
    | (iii) 220.15.1.10 | C (192–223) | 220.15.1.0 | 220.15.1.255 | 255.255.255.255 |
    | (iv) 200.1.10.100 | C (192–223) | 200.1.10.0 | 200.1.10.255 | 255.255.255.255 |

    Method
    - Class from the first octet; default masks /8, /16, /24 for A, B, C.
    - Network address – set all host bits to 0.
    - Directed broadcast – set all host bits to 1. It targets one named network and can in principle be routed to it (most routers block it today, because it was used in Smurf attacks).
    - Limited broadcast – always 255.255.255.255, the same for every network, and never forwarded by a router. It reaches only the local segment, and is what DHCP Discover uses.

52. **What is the subnet mask in 10.2.1.3/22 network?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 637 (ET: N/A)]*

    Answer: /22 means the first 22 bits are network bits.

    ```
    /22 -> 11111111.11111111.11111100.00000000
    ```
    - Third octet 11111100 = 128 + 64 + 32 + 16 + 8 + 4 = 252
    - Subnet mask: `255.255.252.0`

    Supporting details
    - Host bits = 32 − 22 = 10, so 1024 addresses and 1022 usable hosts.
    - Block size in the third octet = 256 − 252 = 4.
    - Third octet of the IP is 1, which falls in the block starting at 0, so the network is 10.2.0.0/22 and the broadcast is 10.2.3.255.

53. **In IPv4 show the network address and host address range of class A, B and C.** *[NSDA Assistant Programmer Date: 04-03-2022 compact it 656 (ET: N/A)]*

    Answer:

    | Class | First octet | Network address range | Default mask | Host address range within a network | Networks | Hosts per network |
    |---|---|---|---|---|---|---|
    | A | 1 – 126 | 1.0.0.0 – 126.0.0.0 | 255.0.0.0 (/8) | x.0.0.1 – x.255.255.254 | 2^7 − 2 = 126 | 2^24 − 2 = 16,777,214 |
    | B | 128 – 191 | 128.0.0.0 – 191.255.0.0 | 255.255.0.0 (/16) | x.y.0.1 – x.y.255.254 | 2^14 = 16,384 | 2^16 − 2 = 65,534 |
    | C | 192 – 223 | 192.0.0.0 – 223.255.255.0 | 255.255.255.0 (/24) | x.y.z.1 – x.y.z.254 | 2^21 = 2,097,152 | 2^8 − 2 = 254 |

    Notes
    - 127.0.0.0/8 is missing from Class A because it is reserved for loopback.
    - Class A network count is 2^7 − 2 because network 0 and network 127 are not usable.
    - Class D (224–239) is multicast and Class E (240–255) is reserved, so neither has a host range.
    - In every class the all-zeros host part is the network address and the all-ones host part is the broadcast address, which is why 2 is subtracted.

54. **Given IP Address: 192.168.5.154/26, Calculate network address and subnet mask.** *[NSDA Assistant Programmer Date: 04-03-2022 compact it 657 (ET: N/A)]*

    Answer: /26 -> host bits 6, block size = 64, mask = 255.255.255.192.

    Step – find the block containing .154
    - Blocks in the last octet: 0, 64, 128, 192
    - 154 falls between 128 and 191, so the block starts at 128.

    | Item | Value |
    |---|---|
    | Network address | `192.168.5.128` |
    | Subnet mask | `255.255.255.192` (/26) |
    | Broadcast address | 192.168.5.191 |
    | Usable range | 192.168.5.129 – 192.168.5.190 |
    | Usable hosts | 62 |

    ```
    Mask /26  : 11111111.11111111.11111111.11000000 = 255.255.255.192
    IP  .154  : 10011010
    AND       : 10000000 = 128
    ```

55. **Mention the maximum number of networks and hosts used in Class A, B and C networks.** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 659 (ET: N/A)]*

    Answer:

    | Class | Network bits | Maximum networks | Host bits | Maximum hosts per network |
    |---|---|---|---|---|
    | A | 8 (7 usable) | 2^7 − 2 = `126` | 24 | 2^24 − 2 = `16,777,214` |
    | B | 16 (14 usable) | 2^14 = `16,384` | 16 | 2^16 − 2 = `65,534` |
    | C | 24 (21 usable) | 2^21 = `2,097,152` | 8 | 2^8 − 2 = `254` |

    Why the bits differ from the class size
    - Class A fixes the leading bit as 0, so only 7 of the 8 network bits vary; networks 0 and 127 are excluded, hence −2.
    - Class B fixes the leading bits as 10, leaving 14 variable bits.
    - Class C fixes the leading bits as 110, leaving 21 variable bits.
    - In every class, 2 host addresses are lost to the network address and the broadcast address.

56. **Which subnet mask would be appropriate for address range to submit for up to LANs, with each LAN contains 5 to 26 hosts?** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 659 (ET: N/A)]*

    Answer: Each LAN must hold up to 26 hosts.

    Step 1 – addresses required
    - 26 hosts + 2 (network and broadcast) = 28 addresses

    Step 2 – round up to a power of 2
    - 2^4 = 16, too small
    - 2^5 = 32 >= 28, so host bits = 5

    Step 3 – prefix and mask
    - Prefix = 32 − 5 = `/27`
    - Mask = 11111111.11111111.11111111.11100000 = `255.255.255.224`

    Check
    - Usable hosts = 2^5 − 2 = 30, which covers the 5-to-26 range with 4 spare.
    - Block size = 32, so eight such LANs fit in one /24, for example 192.168.1.0/27, .32/27, .64/27 … .224/27.
    - A /28 would give only 14 usable hosts, which is not enough for 26.

57. **Given IP Address: 192.168.19.24/29, find out the following IP Class & type, Number of Host, Network address, Broadcast address, Wildcard, and Subnet mask.** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 659 (ET: N/A)]*

    Answer: Given 192.168.19.24/29.

    | Item | Value | Working |
    |---|---|---|
    | IP class and type | Class C, private | First octet 192 is in 192–223; 192.168.x.x is RFC 1918 private |
    | Number of hosts | 6 usable (8 total) | 2^3 = 8, minus 2 |
    | Network address | `192.168.19.24` | Block size 8; 24 is a multiple of 8 |
    | Broadcast address | `192.168.19.31` | 24 + 8 − 1 |
    | Wildcard mask | `0.0.0.7` | 255.255.255.255 − 255.255.255.248 |
    | Subnet mask | `255.255.255.248` | /29 = 11111111.11111111.11111111.11111000 |

    - Usable range: 192.168.19.25 – 192.168.19.30.
    - The wildcard mask is the inverse of the subnet mask and is what Cisco ACLs and OSPF network statements use; a 0 bit means "must match", a 1 bit means "ignore".

58. **Find network address, subnet mask, broadcast address and IP host range of 192.168.100.128/26** *[GTCL Assistant Engineer (CSE) 2022 compact it 685 (ET: BUET)]*

    Answer: /26 -> host bits 6, block size 64, mask 255.255.255.192.

    - The last octet 128 is a multiple of 64, so it is itself a valid network address.

    | Item | Value |
    |---|---|
    | Network address | `192.168.100.128` |
    | Subnet mask | `255.255.255.192` |
    | Broadcast address | `192.168.100.191` |
    | IP host range | `192.168.100.129 – 192.168.100.190` |
    | Usable hosts | 62 |

    - This is the third of the four /26 subnets of 192.168.100.0/24 (.0, .64, .128, .192).

59. **What is the range of IPv4 address class A, B and C?** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 699 (ET: BUET)]*

    Answer:

    | Class | First octet range | Full address range | Default mask |
    |---|---|---|---|
    | A | 1 – 126 | 1.0.0.0 – 126.255.255.255 | 255.0.0.0 (/8) |
    | B | 128 – 191 | 128.0.0.0 – 191.255.255.255 | 255.255.0.0 (/16) |
    | C | 192 – 223 | 192.0.0.0 – 223.255.255.255 | 255.255.255.0 (/24) |

    Also defined
    - Class D: 224 – 239, used for multicast, no default mask.
    - Class E: 240 – 255, reserved for research and experiments.
    - 127.0.0.0 – 127.255.255.255 is excluded from Class A and reserved for loopback.
    - 0.0.0.0 means "this network" or the default route and is not assignable.

60. **What is subnet mask? Given IP address 192.168.0.0/29 find 10^{\text{th}} and 22^{\text{th}} subnet first host address and last host address.** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 701 (ET: BUET)]*

    Answer:

    What is a subnet mask
    - A 32-bit value that marks which bits of an IP address are the network part (1s) and which are the host part (0s). Combined with the IP address by a bitwise AND, it yields the network address, and it tells a host whether a destination is local or must go through the gateway.

    Given 192.168.0.0/29
    - Host bits = 3, block size = 2^3 = `8`, mask = `255.255.255.248`
    - Usable hosts per subnet = 8 − 2 = 6
    - Subnets step through the last octet in 8s: 0, 8, 16, 24 …

    Finding the nth subnet
    - Network address of subnet n = (n − 1) × 8

    10th subnet
    - (10 − 1) × 8 = 72 -> network `192.168.0.72/29`
    - First host: `192.168.0.73`
    - Last host: `192.168.0.78`
    - Broadcast: 192.168.0.79

    22nd subnet
    - (22 − 1) × 8 = 168 -> network `192.168.0.168/29`
    - First host: `192.168.0.169`
    - Last host: `192.168.0.174`
    - Broadcast: 192.168.0.175

    | Subnet | Network | First host | Last host | Broadcast |
    |---|---|---|---|---|
    | 10th | 192.168.0.72 | 192.168.0.73 | 192.168.0.78 | 192.168.0.79 |
    | 22nd | 192.168.0.168 | 192.168.0.169 | 192.168.0.174 | 192.168.0.175 |

    - A /24 divided into /29 gives 32 subnets, so both the 10th and the 22nd exist.

61. **How many bits need to identify an IP address in IPv4?** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*

    Answer: An IPv4 address needs `32 bits` (4 bytes).

    - It is written in dotted-decimal form as four octets of 8 bits each, for example 192.168.1.1.
    - Each octet holds a value from 0 to 255.
    - Total address space = 2^32 = 4,294,967,296 addresses, which is why IPv4 ran out.
    - IPv6 uses 128 bits, giving 2^128 addresses.
    - A MAC address, by contrast, is 48 bits.

62. **What is default subnet mask?** *[BARC Data Entry Officer 10.09.2022 compact it 702 (ET: N/A)]*

    Answer: A default subnet mask is the standard mask that belongs to an IP address class before any subnetting is done. It marks exactly the class boundary between the network part and the host part.

    | Class | Default mask | CIDR | Binary |
    |---|---|---|---|
    | A | 255.0.0.0 | /8 | 11111111.00000000.00000000.00000000 |
    | B | 255.255.0.0 | /16 | 11111111.11111111.00000000.00000000 |
    | C | 255.255.255.0 | /24 | 11111111.11111111.11111111.00000000 |

    - Class A uses 1 octet for the network, Class B uses 2, Class C uses 3.
    - Classes D and E have no default mask, because they are not divided into network and host parts.
    - A custom (subnetted) mask is always longer than the default, since subnetting borrows host bits — for example a Class C subnetted to /26 uses 255.255.255.192.

63. **Given IP: 168.20.96.63, Subnet mask: 255.255.192.0 Find network address, broadcast address and number of host.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 712 (ET: BUET)]*

    Answer: Mask 255.255.192.0 = /18 (11111111.11111111.11000000.00000000).

    Step 1 – block size
    - Third octet: 256 − 192 = 64, so networks step 168.20.0.0, 168.20.64.0, 168.20.128.0, 168.20.192.0

    Step 2 – find the block containing 168.20.96.63
    - Third octet 96 lies between 64 and 127, so the block starts at 64.

    | Item | Value |
    |---|---|
    | Network address | `168.20.64.0` |
    | Broadcast address | `168.20.127.255` |
    | Usable range | 168.20.64.1 – 168.20.127.254 |
    | Number of hosts | 2^14 = 16,384 total, `16,382` usable |

    - Host bits = 32 − 18 = 14.
    - Note that 168.20.96.63 is an ordinary host address here, not a broadcast address — the .63 only looks like one because of the /24 habit.

64. **An IP address is: 172.162.100.25/27, Find out the following: (a) Network Address (b) IP class (c) Subnet mask (d) Broadcast address (e) Hosts per subnet** *[IDRA Assistant Network Administrator 2022 compact it 727 (ET: N/A)]*

    Answer: Given 172.162.100.25/27 -> host bits 5, block size 32, mask 255.255.255.224.

    - Blocks in the last octet: 0, 32, 64, 96, 128 …
    - 25 lies between 0 and 31, so the block starts at 0.

    | # | Item | Value |
    |---|---|---|
    | a | Network address | `172.162.100.0` |
    | b | IP class | `Class B` (first octet 172 is in 128–191) |
    | c | Subnet mask | `255.255.255.224` |
    | d | Broadcast address | `172.162.100.31` |
    | e | Hosts per subnet | 2^5 − 2 = `30` |

    - Usable range: 172.162.100.1 – 172.162.100.30.
    - Note: 172.162.x.x is a public Class B address. The private Class B block is only 172.16 – 172.31.

65. **What is Public and Private IP?** *[IDRA Assistant Network Administrator 2022 compact it 728 (ET: N/A)]*

    Answer:

    Public IP
    - A globally unique address allocated by IANA through the regional registries and handed to a customer by an ISP.
    - It is routable on the internet, so any device holding one can be reached directly from outside.
    - Limited in supply and normally paid for. Examples: 8.8.8.8 (Google DNS), 1.1.1.1 (Cloudflare).
    - Used by web servers, mail servers and the WAN side of a router.

    Private IP
    - An address from a reserved range, unique only inside one organisation, defined by RFC 1918.
    - Internet routers drop these addresses, so a private host cannot be reached directly from outside.
    - Free, unlimited and reusable by every organisation.
    - Ranges: 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16.
    - Used by PCs, printers, IP cameras and phones inside a LAN.

    How they work together
    ```
      LAN (private)                Router / NAT              Internet (public)
    192.168.1.10  ----------->  103.108.140.5  ----------->  8.8.8.8
    192.168.1.11  ----------->  (single public IP)
    ```
    - NAT rewrites the private source address to the router's public address on the way out, and reverses it on the way back. This lets hundreds of private hosts share one public address, which slowed IPv4 exhaustion, and it also hides internal hosts, giving a basic layer of security.

66. **A network IP address is 172.16.236.92/27. Find out the: (a) Subnet mask (b) Network Address (c) Broadcast Address** *[NWPGCL Junior Assistant Manager (IT) 2022 compact it 731 (ET: N/A)]*

    Answer: /27 -> host bits 5, block size = 32, mask = 255.255.255.224.

    Find the block containing .92
    - Blocks: 0, 32, 64, 96, 128 …
    - 92 lies between 64 and 95, so the block starts at 64.

    | # | Item | Value |
    |---|---|---|
    | a | Subnet mask | `255.255.255.224` |
    | b | Network address | `172.16.236.64` |
    | c | Broadcast address | `172.16.236.95` |

    - Usable range: 172.16.236.65 – 172.16.236.94 (30 hosts).
    - Shortcut: floor(92 ÷ 32) = 2, and 2 × 32 = 64.

67. **Given IP address 172.3.16.156/23 and find out the following answer: (i) Network address (ii) Subnet mask (iii) Number of host** *[BOF Assistant Programmer 2022 compact it 733 (ET: MIST)]*

    Answer: /23 -> host bits 9, mask 255.255.254.0, block size in the third octet = 256 − 254 = 2.

    Find the block containing 172.3.16.156
    - Third octet 16 is even, so it is itself the start of a /23 block covering third octets 16 and 17.

    | # | Item | Value |
    |---|---|---|
    | i | Network address | `172.3.16.0` |
    | ii | Subnet mask | `255.255.254.0` |
    | iii | Number of hosts | 2^9 = 512 total, `510` usable |

    - Address range 172.3.16.0 – 172.3.17.255, usable 172.3.16.1 – 172.3.17.254, broadcast 172.3.17.255.
    - Rule for /23: the block always starts on an even third octet.

68. **Answer the following: (i) 192.168.10.0/23, How many usable address? (ii) 192.168.10.0/23, Find subnet mask. (iii) 192.168.10.0/23, Find Broadcast Address. (iv) 192.168.10.0/23, What is last usable host?** *[BTCL Assistant Manager (Technical) 2021 compact it 764 (ET: BUET)]*

    Answer: For 192.168.10.0/23 — host bits = 9, block size in the third octet = 2, and 10 is even, so this is a valid network address.

    | # | Question | Answer |
    |---|---|---|
    | i | Usable addresses | 2^9 − 2 = `510` |
    | ii | Subnet mask | `255.255.254.0` |
    | iii | Broadcast address | `192.168.11.255` |
    | iv | Last usable host | `192.168.11.254` |

    - Full range: 192.168.10.0 – 192.168.11.255, usable 192.168.10.1 – 192.168.11.254.
    - A /23 is simply two /24 blocks merged, which is why the range spans both 192.168.10.x and 192.168.11.x.

69. **(ii) CIDR কী? 192.168.100.9/26 IP address থেকে (a) Total subnets (b) Block size (c) Valid Hosts (d) Total hosts বের করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 788 (ET: N/A)]*

    Answer:

    What is CIDR
    - CIDR (Classless Inter-Domain Routing) removes the fixed A/B/C classes and lets any prefix length from /0 to /32 be used, written as address/prefix (192.168.100.9/26).
    - It was introduced in RFC 1519 (1993) to stop the address wastage of classful addressing and to shrink routing tables through route aggregation (supernetting).
    - It also makes VLSM possible, so different subnets of one network can have different sizes.

    Calculations for 192.168.100.9/26
    - Class C address, default prefix /24, so borrowed bits = 26 − 24 = 2
    - Host bits = 32 − 26 = 6

    | # | Item | Value | Working |
    |---|---|---|---|
    | a | Total subnets | `4` | 2^2 |
    | b | Block size | `64` | 256 − 192 |
    | c | Valid hosts | `62` | 2^6 − 2 |
    | d | Total hosts | `64` | 2^6 |

    - Mask = 255.255.255.192. The address .9 falls in the first block, so the network is 192.168.100.0/26, broadcast 192.168.100.63, usable 192.168.100.1 – 192.168.100.62.

70. **(a) What is the usable number of host IP addresses available on a network that has a /26 mask? Write down the subset mask of this network. Write down the first and the last IP address that can be assigned to host PCs if the network address is 192.168.30.128/26. What address should be used for broadcast purpose in this Network?** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 801-802 (ET: N/A)]*

    Answer: For a /26 mask — host bits = 32 − 26 = 6.

    Usable hosts and mask
    - Total addresses = 2^6 = 64
    - Usable hosts = 64 − 2 = `62`
    - Subnet mask = `255.255.255.192` (11111111.11111111.11111111.11000000)

    For the network 192.168.30.128/26
    - Block size = 64, and 128 is a multiple of 64, so this is a valid network address covering .128 – .191.

    | Item | Value |
    |---|---|
    | Network address | 192.168.30.128 |
    | First host IP | `192.168.30.129` |
    | Last host IP | `192.168.30.190` |
    | Broadcast address | `192.168.30.191` |

    - The address used for broadcast in this network is `192.168.30.191` (all 6 host bits set to 1).

71. **Answer the following: (i) 192.168.10.2/28, Find subnet mask. (ii) 192.168.10.2/28, Find Network Address. (iii) 192.168.10.2/28, Find IP Address of the first host? (iv) 192.168.10.2/28, Find IP Address of the last host? (v) 192.168.10.2/28, Find Broadcast Address.** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

    Answer: /28 -> host bits 4, block size 16, mask 255.255.255.240.

    - .2 lies between 0 and 15, so the block starts at 0.

    | # | Item | Value |
    |---|---|---|
    | i | Subnet mask | `255.255.255.240` |
    | ii | Network address | `192.168.10.0` |
    | iii | First host | `192.168.10.1` |
    | iv | Last host | `192.168.10.14` |
    | v | Broadcast address | `192.168.10.15` |

    - Usable hosts = 14.

72. **Select the correct answer: (i) Which cannot IP address 172.16.28.0/16- (a) .0 (b) .1 (c) .255 (d) All (ii) Which at the follow Dynamically Assign Protocol? (a) DHCP (b) ARP (c) ICMP (d) TCP (iii) Which one is Private IP address? (a) 10.10.10.10 (b) 172.172.172.172 (c) 192.192.192.192 (d) All (iv) SSH Protocol port number is _____. (v) Which is the name of Symmetric key encryption algorithm? (a) AES (b) 3DES (c) Re4 (d) None** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 824 (ET: BUET)]*

    Answer:

    (i) Which cannot be an IP address in 172.16.28.0/16 — answer `(d) All`
    - With a /16 mask the network is 172.16.0.0 and the broadcast is 172.16.255.255. Inside that range, 172.16.28.0, 172.16.28.1 and 172.16.28.255 are all ordinary host addresses, so none of them is barred.
    - Note: many exam keys mark (a) .0 here, on the assumption of a /24 mask. With the /16 stated in the question, all three are usable.

    (ii) Dynamic assignment protocol — answer `(a) DHCP`
    - DHCP (Dynamic Host Configuration Protocol) leases an IP address, mask, gateway and DNS server to a client automatically. It uses UDP ports 67 (server) and 68 (client), and the DORA exchange: Discover, Offer, Request, Acknowledge.
    - ARP maps IP to MAC, ICMP carries error and ping messages, TCP is a transport protocol — none of them assigns addresses.

    (iii) Private IP address — answer `(a) 10.10.10.10`
    - 10.0.0.0/8 is the RFC 1918 Class A private block.
    - 172.172.172.172 is public, because only 172.16 – 172.31 is private.
    - 192.192.192.192 is public, because only 192.168.x.x is private.

    (iv) SSH port number — `22` (TCP)
    - Other common ports: FTP 20/21, Telnet 23, SMTP 25, DNS 53, HTTP 80, HTTPS 443.

    (v) Symmetric key algorithm — answer `(a) AES` and `(b) 3DES`
    - AES, 3DES, DES, Blowfish and RC4 are all symmetric. The option written as "Re4" is RC4, which is also symmetric but is now deprecated as insecure.
    - Asymmetric algorithms are RSA, ECC, Diffie-Hellman and DSA.

73. **A network address is given 172.18.10.0/23, divide this network address into 4 subnets and find every subnet address, start address, subnet mask, broadcast address etc.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 843-844 (ET: N/A)]*

    Answer: Given 172.18.10.0/23, four equal subnets.

    Step 1 – bits to borrow
    - 2^n >= 4 -> n = 2 bits
    - New prefix = 23 + 2 = `/25`, mask `255.255.255.128`, block size 128

    Step 2 – the four subnets
    - The /23 covers 172.18.10.0 – 172.18.11.255, so the 128-address blocks are:

    | Subnet | Network (subnet address) | Start (first usable) | Last usable | Broadcast | Mask |
    |---|---|---|---|---|---|
    | 1 | 172.18.10.0/25 | 172.18.10.1 | 172.18.10.126 | 172.18.10.127 | 255.255.255.128 |
    | 2 | 172.18.10.128/25 | 172.18.10.129 | 172.18.10.254 | 172.18.10.255 | 255.255.255.128 |
    | 3 | 172.18.11.0/25 | 172.18.11.1 | 172.18.11.126 | 172.18.11.127 | 255.255.255.128 |
    | 4 | 172.18.11.128/25 | 172.18.11.129 | 172.18.11.254 | 172.18.11.255 | 255.255.255.128 |

    - Usable hosts per subnet = 2^7 − 2 = 126.
    - Check: 4 × 128 = 512 = the full size of a /23.

74. **A network address is given 172.168.0.0/28, divide this network address into 4 subnets and find every subnet address, start address, subnet mask, broadcast address etc.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 856 (ET: N/A)]*

    Answer: Given 172.168.0.0/28 = 16 addresses only, four equal subnets.

    Step 1 – bits to borrow
    - 2^n >= 4 -> n = 2
    - New prefix = 28 + 2 = `/30`, mask `255.255.255.252`, block size 4

    Step 2 – the four subnets

    | Subnet | Network | Start (first usable) | Last usable | Broadcast | Mask |
    |---|---|---|---|---|---|
    | 1 | 172.168.0.0/30 | 172.168.0.1 | 172.168.0.2 | 172.168.0.3 | 255.255.255.252 |
    | 2 | 172.168.0.4/30 | 172.168.0.5 | 172.168.0.6 | 172.168.0.7 | 255.255.255.252 |
    | 3 | 172.168.0.8/30 | 172.168.0.9 | 172.168.0.10 | 172.168.0.11 | 255.255.255.252 |
    | 4 | 172.168.0.12/30 | 172.168.0.13 | 172.168.0.14 | 172.168.0.15 | 255.255.255.252 |

    - Usable hosts per subnet = 2^2 − 2 = 2, which is exactly right for a router-to-router WAN link but useless for a LAN.
    - Check: 4 × 4 = 16 = the full size of a /28.

75. **In a “Class A” network total 20 subnets are needed with maximum 260 hosts per subnets. Can 255.255.255.0 subnet mask be used in this?** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 862 (ET: BUET)]*

    Answer: No — `255.255.255.0 cannot be used`.

    Step 1 – what the proposed mask gives
    - 255.255.255.0 = /24, host bits = 8
    - Usable hosts per subnet = 2^8 − 2 = `254`
    - Requirement is 260 hosts per subnet, and 254 < 260, so it fails.

    Step 2 – the mask that does work
    - Hosts needed = 260 + 2 = 262
    - 2^8 = 256, too small; 2^9 = 512 >= 262, so host bits = 9
    - Prefix = 32 − 9 = `/23`, mask = `255.255.254.0`, giving 510 usable hosts

    Step 3 – check the subnet requirement
    - Class A default is /8, so borrowed bits = 23 − 8 = 15
    - Subnets available = 2^15 = 32,768, far more than the 20 required

    Answer
    - 255.255.255.0 is rejected because it supports only 254 hosts.
    - Use `255.255.254.0` (/23): 510 usable hosts per subnet and 32,768 subnets, satisfying both conditions.
    - Rule to remember: always size the mask by the host requirement first, then verify that the subnet count is still enough.

76. **Find Network address, Valid Host, Subnet mask and Broadcast address from 172.16.128.120/25.** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 867 (ET: BUET)]*

    Answer: /25 -> host bits 7, block size = 128, mask = 255.255.255.128.

    - Blocks in the last octet: 0 and 128. The value 120 lies in 0–127, so the block starts at 0.

    | Item | Value |
    |---|---|
    | Network address | `172.16.128.0` |
    | Subnet mask | `255.255.255.128` |
    | Valid host range | `172.16.128.1 – 172.16.128.126` |
    | Broadcast address | `172.16.128.127` |
    | Valid hosts | 2^7 − 2 = 126 |

    - Careful: the third octet 128 is part of the address, not the subnet boundary. Only the last octet is split by a /25.

77. **What is the range of class C IPv4 address? Suppose, Class C network has four subnets. How many usable PC needed each subnet?** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 875-876 (ET: BUET)]*

    Answer:

    Range of Class C IPv4 addresses
    - First octet 192 – 223, so the full range is `192.0.0.0 – 223.255.255.255`.
    - Default mask 255.255.255.0 (/24); leading bits 110.
    - Each Class C network has 2^8 − 2 = 254 usable hosts.

    Class C network divided into four subnets
    - Bits to borrow: 2^n >= 4 -> n = 2
    - New prefix = 24 + 2 = /26, mask 255.255.255.192, block size 64
    - Usable PCs per subnet = 2^6 − 2 = `62`

    | Subnet | Network | Broadcast | Usable range | Usable PCs |
    |---|---|---|---|---|
    | 1 | 192.168.1.0/26 | 192.168.1.63 | .1 – .62 | 62 |
    | 2 | 192.168.1.64/26 | 192.168.1.127 | .65 – .126 | 62 |
    | 3 | 192.168.1.128/26 | 192.168.1.191 | .129 – .190 | 62 |
    | 4 | 192.168.1.192/26 | 192.168.1.255 | .193 – .254 | 62 |

    - Total usable = 4 × 62 = 248, against 254 in the unsubnetted /24. The 6 lost addresses are the extra network and broadcast addresses that subnetting creates.

78. **(a) What is the subnet mask of 10.2.1.3/26 and What is the usable number of IP address on network that has a 26 mask?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 886 (ET: N/A)]*

    Answer: Given 10.2.1.3/26.

    Subnet mask
    - /26 = 11111111.11111111.11111111.11000000
    - Last octet = 128 + 64 = 192
    - Mask: `255.255.255.192`

    Usable IP addresses on a /26 network
    - Host bits = 32 − 26 = 6
    - Total addresses = 2^6 = 64
    - Usable = 64 − 2 = `62`

    Supporting detail
    - Block size = 64, and .3 lies in 0–63, so the network is 10.2.1.0/26, broadcast 10.2.1.63, usable range 10.2.1.1 – 10.2.1.62.

79. **172.168.128.0/20 এর Broadcast Address বের কর এবং কতগুলো Computer (Host) Connect করা যাবে?** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 913 (ET: BUET)]*

    Answer: Given 172.168.128.0/20.

    Step 1 – mask and block size
    - /20 -> 11111111.11111111.11110000.00000000 = 255.255.240.0
    - Block size in the third octet = 256 − 240 = 16
    - 128 is a multiple of 16, so the block runs from third octet 128 to 143.

    Step 2 – broadcast address
    - Set all 12 host bits to 1
    - Broadcast address: `172.168.143.255`
    - Full range: 172.168.128.0 – 172.168.143.255

    Step 3 – number of hosts
    - Host bits = 32 − 20 = 12
    - Total = 2^12 = 4096
    - Connectable computers = 4096 − 2 = `4094`
    - Usable range: 172.168.128.1 – 172.168.143.254

80. **Suppose a network with IP address 192.16.0.0 is divided into 2 subnets, find number of hosts per subnet. Also for the first subnet, find- (i) First Subnet address (ii) First host address (iii) Last host address (iv) Broadcast address** *[BAUST Assistant Programmer 2021 compact it 919 (ET: N/A)]*

    Answer: 192.16.0.0 has first octet 192, so it is a Class C address with default mask /24 (256 addresses).

    Step 1 – divide into 2 subnets
    - 2^n >= 2 -> n = 1 bit borrowed
    - New prefix = 24 + 1 = /25, mask 255.255.255.128, block size 128
    - Hosts per subnet = 2^7 − 2 = `126`

    Step 2 – the first subnet

    | # | Item | Value |
    |---|---|---|
    | i | First subnet address | `192.16.0.0/25` |
    | ii | First host address | `192.16.0.1` |
    | iii | Last host address | `192.16.0.126` |
    | iv | Broadcast address | `192.16.0.127` |

    - The second subnet is 192.16.0.128/25, hosts 192.16.0.129 – 192.16.0.254, broadcast 192.16.0.255.

81. **Find the Subnet mask from the following IP: 192.168.3.0/22** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922 (ET: N/A)]*

    Answer: /22 means 22 network bits.

    ```
    /22 -> 11111111.11111111.11111100.00000000
    ```
    - Third octet 11111100 = 252
    - Subnet mask: `255.255.252.0`

    Supporting details
    - Host bits = 10, total addresses 1024, usable hosts 1022.
    - Block size in the third octet = 256 − 252 = 4, so blocks begin at third octet 0, 4, 8, 12 …
    - The given third octet 3 falls in the block starting at 0, so the actual network is 192.168.0.0/22, covering 192.168.0.0 – 192.168.3.255 with broadcast 192.168.3.255.

82. **VLSM Subnetting. Given an IP address, 192.168.0.0/20 For creating 4 subnets department of A, B, C, D with 2000, 1000, 6000 and 8000 hosts, find out every department first and last IP address. Also write the subnet mask of q.x.y.z/notation.** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 927 (ET: CTI)]*

    Answer: First check whether the given block is large enough.

    Step 1 – size each department (hosts + 2, rounded up to a power of 2)

    | Dept | Hosts | Needs | Block | Prefix |
    |---|---|---|---|---|
    | D | 8000 | 8002 | 8192 | /19 |
    | C | 6000 | 6002 | 8192 | /19 |
    | A | 2000 | 2002 | 2048 | /21 |
    | B | 1000 | 1002 | 1024 | /22 |

    - Total required = 8192 + 8192 + 2048 + 1024 = 19,456 addresses.
    - A /20 holds only 2^12 = 4096 addresses, so `192.168.0.0/20 is too small`. The smallest block that fits is a /17 (32,768 addresses).
    - The allocation below therefore uses `192.168.0.0/17`. The method is identical; only the parent prefix changes.

    Step 2 – VLSM allocation, largest first

    | Dept | Hosts | Block (CIDR) | Mask | First IP | Last IP | Broadcast | Usable |
    |---|---|---|---|---|---|---|---|
    | D | 8000 | 192.168.0.0/19 | 255.255.224.0 | 192.168.0.1 | 192.168.31.254 | 192.168.31.255 | 8190 |
    | C | 6000 | 192.168.32.0/19 | 255.255.224.0 | 192.168.32.1 | 192.168.63.254 | 192.168.63.255 | 8190 |
    | A | 2000 | 192.168.64.0/21 | 255.255.248.0 | 192.168.64.1 | 192.168.71.254 | 192.168.71.255 | 2046 |
    | B | 1000 | 192.168.72.0/22 | 255.255.252.0 | 192.168.72.1 | 192.168.75.254 | 192.168.75.255 | 1022 |

    - Free space left: 192.168.76.0 onwards, inside the /17.
    - The two rules of VLSM used here: always allocate the biggest requirement first, and always start each new block on a boundary that is a multiple of its own size. <!-- verify -->

83. **You are given a IP address 172.16.20.0/25 have four subnets. For each department find the following information. (CSE, EEE, IPE, PME)** *[NRCC Assistant Programmer 2021 compact it 931 (ET: N/A)]*

    Answer: Given 172.16.20.0/25 = 128 addresses, four subnets for CSE, EEE, IPE and PME.

    Step 1 – bits to borrow
    - 2^n >= 4 -> n = 2
    - New prefix = 25 + 2 = `/27`, mask `255.255.255.224`, block size 32

    Step 2 – allocation

    | Department | Network address | First usable | Last usable | Broadcast | Mask | Usable hosts |
    |---|---|---|---|---|---|---|
    | CSE | 172.16.20.0/27 | 172.16.20.1 | 172.16.20.30 | 172.16.20.31 | 255.255.255.224 | 30 |
    | EEE | 172.16.20.32/27 | 172.16.20.33 | 172.16.20.62 | 172.16.20.63 | 255.255.255.224 | 30 |
    | IPE | 172.16.20.64/27 | 172.16.20.65 | 172.16.20.94 | 172.16.20.95 | 255.255.255.224 | 30 |
    | PME | 172.16.20.96/27 | 172.16.20.97 | 172.16.20.126 | 172.16.20.127 | 255.255.255.224 | 30 |

    - Check: 4 × 32 = 128, which exactly fills the /25.

84. **Define IP 127.0.0.1, what is localhost?** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 932 (ET: BUET)]*

    Answer:

    IP 127.0.0.1
    - It is the loopback address, part of the reserved block 127.0.0.0/8.
    - A packet sent to it is turned back inside the machine's own TCP/IP stack and never reaches the network card or the cable.
    - It is used to test whether TCP/IP is installed and working, and to reach a server running on the same machine, for example `http://127.0.0.1:3000`.
    - In IPv6 the loopback address is `::1`.
    - The whole 127.x.x.x range is reserved — that is 16.7 million addresses lost from Class A for this one purpose.

    localhost
    - `localhost` is the hostname that maps to the loopback address. The mapping lives in the hosts file (`/etc/hosts` on Linux, `C:\Windows\System32\drivers\etc\hosts` on Windows) as:
    ```
    127.0.0.1   localhost
    ::1         localhost
    ```
    - Developers use it constantly: a web server, database or API running locally is reached as localhost, so the application can be tested before it is deployed.
    - Because loopback traffic never leaves the machine, a service bound only to 127.0.0.1 cannot be reached from outside, which is also a useful security property.

85. **What is static IP Address and dynamic IP Address?** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 932 (ET: BUET)]*

    Answer:

    Static IP address
    - An address configured manually on the device and fixed until someone changes it.
    - Advantages: always the same, so DNS records, port forwarding and firewall rules stay valid; needed by servers, printers, routers, CCTV cameras and remote-access hosts.
    - Disadvantages: manual work, risk of duplicate addresses, and difficult to manage in a large network.

    Dynamic IP address
    - An address leased automatically by a DHCP server for a limited time. When the lease expires the client renews it or receives a different address.
    - Advantages: no manual configuration, no address conflicts, efficient reuse of a limited pool, easy for laptops and phones that move between networks.
    - Disadvantages: the address can change, so it is unsuitable for a server; the network depends on the DHCP server being available.
    - It is assigned through the DORA exchange: Discover, Offer, Request, Acknowledge.

    Comparison

    | Point | Static | Dynamic |
    |---|---|---|
    | Assigned by | Administrator, manually | DHCP server |
    | Changes | Never, unless edited | On lease renewal |
    | Configuration effort | High | Very low |
    | Conflict risk | Present | Avoided by the server |
    | Typical use | Servers, routers, printers | PCs, laptops, phones |
    | Cost | Usually chargeable from an ISP | Included by default |

    - A common middle option is a DHCP reservation, which ties one MAC address to one fixed IP, giving the stability of static with the central management of DHCP.

86. **Using the IP address 192.168.10.0/23 find out- (i) Subnet/First address (ii) Last Address (iii) Subnet mask** *[SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)]*

    Answer: /23 -> host bits 9, mask 255.255.254.0, block size in the third octet = 2. The value 10 is even, so this is a valid network address.

    | # | Item | Value |
    |---|---|---|
    | i | Subnet / first address | `192.168.10.0` (first usable host 192.168.10.1) |
    | ii | Last address | `192.168.11.255` (last usable host 192.168.11.254) |
    | iii | Subnet mask | `255.255.254.0` |

    - Total addresses = 2^9 = 512, usable hosts = 510.
    - The block spans two /24 ranges, 192.168.10.x and 192.168.11.x, with the broadcast at 192.168.11.255.

87. **Consider the IP address 10.20.30.0/25 now answer the below question: (i) What is the subnet mask of the above IP address? (ii) How many host per subnet have? (iii) What is the Broadcast address of this 10.20.30.0/3 IP address?** *[Janata Bank Assistant System Administrator 2021 compact it 938 (ET: N/A)]*

    Answer: Given 10.20.30.0/25 -> host bits 7, block size 128, mask 255.255.255.128.

    | # | Item | Value |
    |---|---|---|
    | i | Subnet mask | `255.255.255.128` |
    | ii | Hosts per subnet | 2^7 − 2 = `126` |
    | iii | Broadcast address | `10.20.30.127` |

    - Network address 10.20.30.0, usable range 10.20.30.1 – 10.20.30.126.
    - The second /25 of the same /24 would be 10.20.30.128, with broadcast 10.20.30.255.

88. **২. 192.168.10.0/28 এর জন্য সাবনেট মাস্ক হবে কোনটি?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

    Answer: The subnet mask for /28 is `255.255.255.240`.

    ```
    /28 -> 11111111.11111111.11111111.11110000
    Last octet: 128 + 64 + 32 + 16 = 240
    ```
    - Host bits = 32 − 28 = 4, so 16 addresses per block and 14 usable hosts.
    - Block size = 256 − 240 = 16, so 192.168.10.0/28 covers 192.168.10.0 – 192.168.10.15, with broadcast 192.168.10.15.
    - Sixteen /28 subnets fit inside one /24.

89. **৯. ক্লাস C এর ডিফল্ট সাবনেট মাস্ক কত?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

    Answer: The Class C default subnet mask is `255.255.255.0`, that is `/24`.

    - Binary: 11111111.11111111.11111111.00000000
    - The first three octets are the network ID, the last octet is the host ID.
    - Usable hosts per Class C network = 2^8 − 2 = 254.
    - For comparison: Class A default 255.0.0.0 (/8), Class B default 255.255.0.0 (/16).

90. **১১. নিচের কোনটি লুপ ব্যাক আইপি এড্রেস?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

    Answer: The loopback IP address is `127.0.0.1`.

    - The entire block 127.0.0.0 – 127.255.255.255 (127.0.0.0/8) is reserved for loopback.
    - A packet addressed here is returned by the machine's own TCP/IP stack and never reaches the network card.
    - Its hostname is `localhost`; the IPv6 loopback address is `::1`.
    - It is used to test the TCP/IP stack (`ping 127.0.0.1`) and to reach services running on the same machine.
    - It is not 0.0.0.0 (default route), not 169.254.x.x (APIPA link-local), and not 255.255.255.255 (limited broadcast).

91. **A IP Address is: 172.16.128.120/25 now answers the following questions: (i) What is the network address of this IP? (ii) What is the subnet mask? (iii) What is the broadcast address? (iv) How many connection is possible in this network?** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 975 (ET: BUET)]*

    Answer: Given 172.16.128.120/25 -> host bits 7, block size 128, mask 255.255.255.128.

    - In the last octet the blocks are 0 and 128. The value 120 lies in 0–127, so the block starts at 0.

    | # | Item | Value |
    |---|---|---|
    | i | Network address | `172.16.128.0` |
    | ii | Subnet mask | `255.255.255.128` |
    | iii | Broadcast address | `172.16.128.127` |
    | iv | Possible connections | 2^7 − 2 = `126` |

    - Usable range: 172.16.128.1 – 172.16.128.126.
    - Watch out: the third octet 128 is not the subnet boundary here — a /25 only splits the last octet.

92. **(a) A IP address is 172.20.0.0/27. How many subnets and hosts per subnet?** *[National University Assistant Programmer 2020 compact it 977 (ET: DU)]*

    Answer: Given 172.20.0.0/27. First octet 172 means this is a Class B address, so the default prefix is /16.

    Step 1 – borrowed bits
    - Borrowed = 27 − 16 = 11
    - Number of subnets = 2^11 = `2048`

    Step 2 – hosts per subnet
    - Host bits = 32 − 27 = 5
    - Total addresses = 2^5 = 32
    - Usable hosts = 32 − 2 = `30`

    Check
    - 2048 × 32 = 65,536, which is exactly the size of a Class B network.
    - Mask = 255.255.255.224, block size 32, so subnets run 172.20.0.0, 172.20.0.32, 172.20.0.64 … 172.20.255.224.

93. **Given IP address 172.16.128.120/25 what is the subnet mask, network address, broadcast address and total usable host in this network?** *[NACTAR Assistant Instructor (ICT) 2020 compact it 991 (ET: N/A)]*

    Answer: /25 -> host bits 7, block size 128, mask 255.255.255.128. The value 120 lies in 0–127, so the block starts at 0.

    | Item | Value |
    |---|---|
    | Subnet mask | `255.255.255.128` |
    | Network address | `172.16.128.0` |
    | Broadcast address | `172.16.128.127` |
    | Total usable hosts | 2^7 − 2 = `126` |

    - Usable range: 172.16.128.1 – 172.16.128.126.

94. **Given IP address is 172.168.10.0/24, administrator wants to create 32 subnets, then find out sub netmask, number of address of each subnet, first and last address of subnet 1, first and last address of subnet 32.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1012 (ET: DU)]*

    Answer: Given 172.168.10.0/24, 32 subnets required.

    Step 1 – bits to borrow
    - 2^n >= 32 -> 2^5 = 32, so n = 5 bits
    - New prefix = 24 + 5 = `/29`

    Step 2 – subnet mask
    - /29 = 11111111.11111111.11111111.11111000 = `255.255.255.248`

    Step 3 – addresses per subnet
    - Host bits = 3, so `8` addresses per subnet (6 usable)
    - Block size = 256 − 248 = 8, so subnets step by 8

    Step 4 – first and last subnets

    | Subnet | Network | First address | Last address | Usable range |
    |---|---|---|---|---|
    | 1 | 172.168.10.0/29 | `172.168.10.0` | `172.168.10.7` | .1 – .6 |
    | 32 | 172.168.10.248/29 | `172.168.10.248` | `172.168.10.255` | .249 – .254 |

    - Formula: network address of subnet n = (n − 1) × 8. For n = 32, (32 − 1) × 8 = 248.
    - Check: 32 × 8 = 256, exactly one /24.

95. **Given IP Address 180.79.35.5/24, Find the (i) Network address (ii) Broadcast address (iii) Subnet mask (iv) Total valid host (v) IP address class** *[PGCB Sub-Assistant Engineer (CSE) 2020 compact it 1043 (ET: BUET)]*

    Answer: Given 180.79.35.5/24.

    | # | Item | Value |
    |---|---|---|
    | i | Network address | `180.79.35.0` |
    | ii | Broadcast address | `180.79.35.255` |
    | iii | Subnet mask | `255.255.255.0` |
    | iv | Total valid hosts | 2^8 − 2 = `254` |
    | v | IP address class | `Class B` (first octet 180 is in 128–191) |

    - Usable range: 180.79.35.1 – 180.79.35.254.
    - Note: although the address is Class B by its first octet, the /24 prefix here is a subnetted mask — 8 bits have been borrowed from the Class B default of /16, creating 256 subnets of 254 hosts each.

96. **What is private IP? List the class B private IP.** *[Bangladesh Television Assistant Programmer 2019 compact it 1066 (ET: N/A)]*

    Answer:

    What is a private IP
    - A private IP address comes from a range reserved by RFC 1918 for use inside an organisation. It is unique only within that network, is never routed on the public internet, and needs NAT to reach the outside.
    - It exists because IPv4 addresses are scarce: hundreds of internal hosts can share one public address.
    - The three blocks are 10.0.0.0/8, 172.16.0.0/12 and 192.168.0.0/16.

    Class B private IP range
    - `172.16.0.0 – 172.31.255.255`
    - CIDR: 172.16.0.0/12, mask 255.240.0.0
    - This is 16 consecutive Class B networks: 172.16.x.x, 172.17.x.x, … up to 172.31.x.x
    - Total addresses: 1,048,576
    - Each individual /16 inside it holds 65,534 usable hosts.
    - Common mistake: 172.15.x.x and 172.32.x.x are public. Only second octets 16 through 31 are private.

97. **Identify the IP address: (i) 192.168.1.1 (ii) 1.1.191.168** *[DESCO Sub-Assistant Engineer (CSE) 2019 compact it 1119 (ET: BUET)]*

    Answer:

    (i) 192.168.1.1
    - First octet 192 lies in 192–223, so it is `Class C`.
    - It falls in 192.168.0.0/16, so it is a `private` address (RFC 1918).
    - It is not routable on the internet and is the address most commonly used as a home router's default gateway.
    - Default mask 255.255.255.0.

    (ii) 1.1.191.168
    - First octet 1 lies in 1–126, so it is `Class A`.
    - It is outside 10.0.0.0/8, so it is a `public` address, routable on the internet.
    - Default mask 255.0.0.0, network 1.0.0.0.
    - The digits are the same as in (i) but reversed; the class and type are decided only by the first octet, so the two addresses are completely different in nature.

98. **(b) Find subnet of 172.16.2.1/22 which will be applicable for your office room having 50 and 23 PCs. Also find the first and last usable ip addresses along with board cast address.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1141 (ET: N/A)]*

    Answer: The block 172.16.2.1/22 belongs to the network 172.16.0.0/22, which covers 172.16.0.0 – 172.16.3.255 (1024 addresses).

    Step 1 – size each requirement (hosts + 2, rounded to a power of 2)

    | Room | PCs | Needs | Block | Prefix | Mask |
    |---|---|---|---|---|---|
    | First | 50 | 52 | 64 | /26 | 255.255.255.192 |
    | Second | 23 | 25 | 32 | /27 | 255.255.255.224 |

    Step 2 – allocate largest first (VLSM)

    | Room | Network | First usable | Last usable | Broadcast | Usable hosts |
    |---|---|---|---|---|---|
    | 50 PCs | `172.16.0.0/26` | `172.16.0.1` | `172.16.0.62` | `172.16.0.63` | 62 |
    | 23 PCs | `172.16.0.64/27` | `172.16.0.65` | `172.16.0.94` | `172.16.0.95` | 30 |

    - Free space left: 172.16.0.96 onwards, plenty for future rooms.
    - Reason for the sizes: a /27 gives only 30 usable hosts, too few for 50; a /28 gives 14, too few for 23.

99. **(c) What is loopback address of a computer?** *[BPSC Assistant Programmer (ICT) 2019 compact it 1143 (ET: N/A)]*

    Answer: The loopback address of a computer is `127.0.0.1`.

    - The whole range 127.0.0.0/8 (127.0.0.0 – 127.255.255.255) is reserved for this purpose.
    - A packet sent to it is looped back inside the machine's own TCP/IP stack, so it never reaches the network card or the cable.
    - Its hostname is `localhost`; the IPv6 equivalent is `::1`.
    - Uses: `ping 127.0.0.1` tests whether the TCP/IP stack is installed and working, and a locally running server is reached as http://127.0.0.1:port during development.
    - If a ping to 127.0.0.1 fails, the fault is in the TCP/IP software of that machine, not in the network.

100. **Write 3 private IP address range.** *[Dutch Bangla Bank Assistant Network/Hardware Engineer 2019 compact it 1160 (ET: BUET)]*

    Answer: The three private ranges defined by RFC 1918 are:

    | # | Range | CIDR | Mask | Class |
    |---|---|---|---|---|
    | 1 | 10.0.0.0 – 10.255.255.255 | 10.0.0.0/8 | 255.0.0.0 | A |
    | 2 | 172.16.0.0 – 172.31.255.255 | 172.16.0.0/12 | 255.240.0.0 | B |
    | 3 | 192.168.0.0 – 192.168.255.255 | 192.168.0.0/16 | 255.255.0.0 | C |

    - These addresses are dropped by internet routers, so they are reachable only inside an organisation and require NAT for outside access.
    - 169.254.0.0/16 (APIPA) is also non-routable but is link-local, not an RFC 1918 private range.

101. **Find the subnet and host number of 255.255.240.0** *[Dutch Bangla Bank Assistant Network/Hardware Engineer 2019 compact it 1160 (ET: BUET)]*

    Answer: Mask 255.255.240.0 = /20, since 240 = 11110000.

    ```
    255.255.240.0 -> 11111111.11111111.11110000.00000000
                                        ^^^^ 4 borrowed bits
    ```

    Assuming a Class B network (default /16)
    - Subnet bits borrowed = 20 − 16 = 4
    - Number of subnets = 2^4 = `16`
    - Host bits = 32 − 20 = 12
    - Hosts per subnet = 2^12 − 2 = `4094`

    Check
    - 16 × 4096 = 65,536, exactly the size of a Class B network.
    - Block size in the third octet = 256 − 240 = 16, so subnets run x.y.0.0, x.y.16.0, x.y.32.0 … x.y.240.0.
    - If the parent were a Class A /8 instead, the same mask would give 2^12 = 4096 subnets of 4094 hosts each — the host count never changes, only the subnet count depends on the parent.

102. **Find subnet mask and number of host on each subnet mask at a class B IP address is 172.16.2.1/23.** *[Palli Sanchay Bank Assistant Programmer 2018 compact it 1168 (ET: N/A)]*

    Answer: Given 172.16.2.1/23, a Class B address (default /16).

    Subnet mask
    - /23 = 11111111.11111111.11111110.00000000
    - Third octet 11111110 = 254
    - Mask: `255.255.254.0`

    Hosts per subnet
    - Host bits = 32 − 23 = 9
    - Total addresses = 2^9 = 512
    - Usable hosts = 512 − 2 = `510`

    Number of subnets
    - Borrowed bits = 23 − 16 = 7
    - Subnets = 2^7 = 128

    Supporting detail
    - Block size in the third octet = 256 − 254 = 2, and 2 is even, so the network is 172.16.2.0/23.
    - Range 172.16.2.0 – 172.16.3.255, usable 172.16.2.1 – 172.16.3.254, broadcast 172.16.3.255.

103. **Find Network Address, Broadcast Address, Net mask, valid host of the IP address is: 192.16.13.0/30** *[NESCO Assistant Manager (MIS & ICT) 2018 compact it 1176-1177 (ET: N/A)]*

    Answer: /30 -> host bits 2, block size 4, mask 255.255.255.252.

    | Item | Value |
    |---|---|
    | Network address | `192.16.13.0` |
    | Broadcast address | `192.16.13.3` |
    | Net mask | `255.255.255.252` |
    | Valid hosts | `192.16.13.1` and `192.16.13.2` (2 hosts) |

    ```
    Network   192.16.13.000000 00 = 192.16.13.0
    Host 1                        = 192.16.13.1
    Host 2                        = 192.16.13.2
    Broadcast 192.16.13.000000 11 = 192.16.13.3
    ```
    - A /30 wastes 50 percent of its addresses, but it is still the standard choice for a router-to-router serial link, where exactly two addresses are needed. RFC 3021 /31 links avoid even that waste.

104. **Given an IP address is 240.133.10.20/8 Find out network address, number of host and subnet mask.** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1192 (ET: N/A)]*

    Answer: Given 240.133.10.20/8.

    Step 1 – identify the class
    - First octet 240 lies in 240–255, so this is a `Class E` address, reserved for research and experimental use. It cannot be assigned to a normal host on the internet.

    Step 2 – apply the /8 mask as given
    - Mask: `255.0.0.0`
    - Network address: 240.133.10.20 AND 255.0.0.0 = `240.0.0.0`
    - Host bits = 32 − 8 = 24
    - Total addresses = 2^24 = 16,777,216
    - Number of hosts (usable) = 2^24 − 2 = `16,777,214`
    - Broadcast address: 240.255.255.255

    | Item | Value |
    |---|---|
    | Class | E (reserved) |
    | Network address | 240.0.0.0 |
    | Subnet mask | 255.0.0.0 |
    | Number of hosts | 16,777,214 |

    - The arithmetic is the same as for a Class A /8; only the reserved status of the address block differs.

105. **Calculate subnet mask and network address from the given IP address 192.168.5.44/26.** *[Jiban Bima Corporation Assistant Programmer 2018 compact it 1212 (ET: N/A)]*

    Answer: /26 -> host bits 6, block size = 64, mask = 255.255.255.192.

    - Blocks in the last octet: 0, 64, 128, 192. The value 44 lies in 0–63, so the block starts at 0.

    | Item | Value |
    |---|---|
    | Subnet mask | `255.255.255.192` |
    | Network address | `192.168.5.0` |
    | Broadcast address | 192.168.5.63 |
    | Usable range | 192.168.5.1 – 192.168.5.62 |
    | Usable hosts | 62 |

    ```
    IP   192.168.5.44  -> last octet 00101100
    Mask /26           -> last octet 11000000
    AND                -> last octet 00000000 = 0
    ```

106. **How many subnets and hosts per subnet can you get from the network 172.20.0.0/27?** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1226 (ET: N/A)]*

    Answer: Given 172.20.0.0/27, a Class B address whose default prefix is /16.

    Number of subnets
    - Borrowed bits = 27 − 16 = 11
    - Subnets = 2^11 = `2048`

    Hosts per subnet
    - Host bits = 32 − 27 = 5
    - Total addresses = 2^5 = 32
    - Usable hosts = 32 − 2 = `30`

    Check
    - 2048 × 32 = 65,536 = the full size of a Class B network.
    - Mask = 255.255.255.224, block size 32: 172.20.0.0, 172.20.0.32, 172.20.0.64 … through 172.20.255.224.

107. **A block address is granted to a small organization. If one of the addresses is 205.16.37.39/28, what is the first and last address of the block?** *[Multiple Ministry Assistant Programmer 2017 compact it 1230 (ET: N/A)]*

    Answer: /28 -> host bits 4, block size = 16, mask = 255.255.255.240.

    Step – find the block containing .39
    - Blocks in the last octet: 0, 16, 32, 48 …
    - 39 lies between 32 and 47, so the block starts at 32.
    - Shortcut: floor(39 ÷ 16) = 2, and 2 × 16 = 32.

    | Item | Value |
    |---|---|
    | First address of the block (network) | `205.16.37.32` |
    | Last address of the block (broadcast) | `205.16.37.47` |
    | Usable range | 205.16.37.33 – 205.16.37.46 |
    | Usable hosts | 14 |

    - So the organisation's block is 205.16.37.32/28, containing 16 addresses.

108. **Explain why subnet mask is used?** *[Multiple Ministry Assistant Programmer 2017 compact it 1232-1233 (ET: N/A)]*

    Answer: A subnet mask is used because an IP address alone does not say where the network part ends and the host part begins. The mask supplies that split, and everything below depends on it.

    Reasons

    - To identify the network address. The device ANDs the IP address with the mask; the result is the network the host belongs to.
    ```
    IP    192.168.1.10  -> 11000000.10101000.00000001.00001010
    Mask  255.255.255.0 -> 11111111.11111111.11111111.00000000
    AND   192.168.1.0   -> network address
    ```

    - To decide local versus remote delivery. The sender masks both its own address and the destination address. If the two network addresses match, the frame is sent directly on the LAN; if not, it is handed to the default gateway. Without a mask a host could not make this decision at all.

    - To make subnetting possible. Borrowing host bits into the mask splits one large network into several smaller ones, which shrinks broadcast domains, improves performance and separates departments for security.

    - To calculate capacity. The mask fixes the number of addresses in the block, 2^h, and the number of usable hosts, 2^h − 2.

    - To support VLSM and CIDR. Different masks on different segments let each subnet be sized to its actual need instead of wasting thousands of addresses.

    - To let routers forward correctly. A routing table stores network/mask pairs, and forwarding uses the longest prefix match, which is entirely a mask operation.

109. **Given an IP address 10.2.3.20/22, Find out the number of host and subnet mask.** *[BTCL Assistant Manager (Technical) 2017 compact it 1254 (ET: N/A)]*

    Answer: Given 10.2.3.20/22.

    Subnet mask
    - /22 = 11111111.11111111.11111100.00000000
    - Third octet = 252
    - Mask: `255.255.252.0`

    Number of hosts
    - Host bits = 32 − 22 = 10
    - Total addresses = 2^10 = 1024
    - Usable hosts = 1024 − 2 = `1022`

    Supporting detail
    - Block size in the third octet = 256 − 252 = 4, so blocks start at third octet 0, 4, 8, 12 …
    - The given third octet 3 falls in the block starting at 0, so the network is 10.2.0.0/22, covering 10.2.0.0 – 10.2.3.255 with broadcast 10.2.3.255 and usable range 10.2.0.1 – 10.2.3.254.

## OSI & TCP/IP Reference Model (52)

1. Mention the layers of the OSI Model and the function of each layer. *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*

   Answer: The OSI (Open Systems Interconnection) model, made by ISO in 1984, splits network communication into 7 layers. Each layer does one job and serves the layer above it.

   | # | Layer | Main function | PDU | Examples |
   |---|---|---|---|---|
   | 7 | Application | Provides network services directly to the user's program | Data | HTTP, FTP, SMTP, DNS |
   | 6 | Presentation | Translation, encryption/decryption, compression | Data | SSL/TLS, JPEG, ASCII |
   | 5 | Session | Sets up, manages and ends a session; synchronisation | Data | NetBIOS, RPC, SMB |
   | 4 | Transport | End-to-end delivery, segmentation, flow and error control | Segment (TCP) / Datagram (UDP) | TCP, UDP |
   | 3 | Network | Logical addressing and routing between networks | Packet | IP, ICMP, OSPF |
   | 2 | Data Link | Node-to-node delivery, framing, MAC addressing, error detection | Frame | Ethernet, PPP, ARP |
   | 1 | Physical | Sends raw bits as electrical, light or radio signals | Bit | Cables, hubs, RS-232 |

   Layer functions in short
   - Physical – defines voltage, pin layout, cable type, data rate and topology. Devices: hub, repeater, cable, NIC connector.
   - Data Link – builds frames, adds source and destination MAC addresses, detects errors with CRC, and controls access to the medium. Sub-layers: LLC and MAC. Devices: switch, bridge.
   - Network – gives every host a logical IP address and chooses the best path through routers. Also handles fragmentation.
   - Transport – breaks data into segments, numbers them, and rebuilds them in order. TCP gives reliability and flow control; UDP gives speed. Port numbers live here.
   - Session – opens, maintains and closes a conversation; adds checkpoints so a long transfer can resume.
   - Presentation – the "translator": character-set conversion, encryption and compression.
   - Application – the layer the user actually touches through a browser, mail client or file transfer program.

   Memory aid (Layer 7 down to 1): All People Seem To Need Data Processing.

2. **OSI মডেলের ৭টি স্তরের কাজ কি? এই সমগ্র স্তরগুলোর ভূমিকা কি?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   The OSI model has 7 layers. Their work and their overall role are as follows.

   | # | Layer | Work it does |
   |---|---|---|
   | 7 | Application | Gives the user's program access to the network — web, mail, file transfer |
   | 6 | Presentation | Data format translation, encryption/decryption, compression |
   | 5 | Session | Opens, controls and closes the dialogue between two machines |
   | 4 | Transport | Segmentation, reassembly, port addressing, flow and error control |
   | 3 | Network | Logical (IP) addressing, routing, fragmentation |
   | 2 | Data Link | Framing, MAC addressing, error detection, media access |
   | 1 | Physical | Transmits raw bits over cable, fibre or radio |

   Role of the layer structure as a whole
   - Standardisation – equipment from different vendors can work together because every layer has an agreed interface.
   - Modularity – each layer can be changed or upgraded without disturbing the others. Wi-Fi replaced Ethernet at Layer 1–2 without changing IP or HTTP.
   - Simplicity – a large, complex problem is broken into seven small, manageable problems.
   - Troubleshooting – a fault can be isolated to one layer. "No link light" is Layer 1, "wrong IP" is Layer 3, "DNS failure" is Layer 7.
   - Teaching and design – it is the common vocabulary engineers use to describe networks.
   - Encapsulation – as data goes down the stack each layer adds its own header; on the receiving side each layer removes its own header. Every layer talks logically to its peer layer on the other machine.

3. **What is the OSI model? Explain the functions of each layer with examples.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

   Answer:

   What is the OSI model
   - OSI (Open Systems Interconnection) is a 7-layer reference model published by ISO in 1984. It describes how data moves from an application on one computer to an application on another, dividing the work into layers so that different vendors' equipment can interoperate.
   - It is a reference model, not a protocol. The internet actually runs on TCP/IP, but OSI remains the standard language for design and troubleshooting.

   The seven layers with examples

   | # | Layer | Function | Example |
   |---|---|---|---|
   | 7 | Application | Network service to the user's program | Opening www.google.com in a browser uses HTTP |
   | 6 | Presentation | Translation, encryption, compression | TLS encrypts the page; a JPEG image is decoded |
   | 5 | Session | Start, manage and end the dialogue | A bank login session that stays open until logout |
   | 4 | Transport | Segmentation and reliable delivery | TCP port 443 numbers and re-sends lost segments |
   | 3 | Network | Logical addressing and path selection | IP header carries 103.108.140.5 to 142.250.x.x |
   | 2 | Data Link | Framing and MAC delivery on one hop | Ethernet frame from your PC to the router's MAC |
   | 1 | Physical | Raw bits on the medium | Voltage on UTP cable, light in fibre, Wi-Fi radio |

   Encapsulation — how the layers work together
   ```
   Sender                                 Receiver
   Application  Data                      Data        Application
   Presentation Data                      Data        Presentation
   Session      Data                      Data        Session
   Transport    [TCP hdr | Data]          Segment     Transport
   Network      [IP hdr | Segment]        Packet      Network
   Data Link    [MAC hdr | Packet | FCS]  Frame       Data Link
   Physical      101101010101  ------->   Bits        Physical
   ```
   - Going down, each layer adds a header (encapsulation). Going up, each layer removes its own header (decapsulation). Logically, each layer talks to the same layer on the other machine.

4. **(b) Name the OSI layers and give one example of a cyber threat at any tree of those layers.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

   Answer:

   The OSI layers (top to bottom)
   - 7 Application, 6 Presentation, 5 Session, 4 Transport, 3 Network, 2 Data Link, 1 Physical.

   Cyber threats at three of those layers

   | Layer | Threat | How it works |
   |---|---|---|
   | 7 Application | SQL injection / phishing | Malicious input is placed in a web form so the database executes attacker SQL; or a fake page steals credentials |
   | 4 Transport | TCP SYN flood | The attacker sends thousands of SYN packets and never completes the handshake, filling the server's connection table (DoS) |
   | 3 Network | IP spoofing / ICMP flood | The source IP in the packet header is forged to hide the attacker or to reflect traffic at a victim |
   | 2 Data Link | ARP spoofing / MAC flooding | Fake ARP replies redirect LAN traffic through the attacker (man-in-the-middle); a flooded CAM table turns a switch into a hub |
   | 1 Physical | Cable tapping / jamming | Fibre or copper is tapped to copy traffic, or a Wi-Fi jammer blocks the channel |

   Matching defence
   - Layer 7 – input validation, prepared statements, WAF, user awareness training.
   - Layer 4 – SYN cookies, rate limiting, stateful firewall.
   - Layer 3 – ingress and egress filtering, IPsec, anti-spoofing ACLs.
   - Layer 2 – Dynamic ARP Inspection, port security, DHCP snooping.
   - Layer 1 – locked cabinets, conduit, physical access control.

5. **Write bottom to top OSI reference Model.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1449 (ET: N/A)]*

   Answer: Bottom to top, the OSI reference model is:

   ```
   7. Application     <- top
   6. Presentation
   5. Session
   4. Transport
   3. Network
   2. Data Link
   1. Physical        <- bottom
   ```

   Bottom-to-top order in words
   - Physical -> Data Link -> Network -> Transport -> Session -> Presentation -> Application

   - Memory aid (bottom to top): Please Do Not Throw Sausage Pizza Away.
   - Memory aid (top to bottom): All People Seem To Need Data Processing.
   - Data travels down the stack at the sender and up the stack at the receiver.

6. **In the TCP/IP model, how is data known in the different layers?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

   Answer: The name given to the data changes at every layer. The unit is called the PDU (Protocol Data Unit).

   | TCP/IP layer | Name of the data (PDU) | Header added |
   |---|---|---|
   | Application | Data (or Message) | Application header |
   | Transport | `Segment` (TCP) or `Datagram` (UDP) | Port numbers, sequence numbers |
   | Internet / Network | `Packet` (or Datagram) | Source and destination IP addresses |
   | Network Access / Data Link | `Frame` | Source and destination MAC addresses, FCS |
   | Physical | `Bits` | None — raw signal |

   ```
   Application  |            Data            |
   Transport    | TCPhdr |   Data            |   -> Segment
   Internet     | IPhdr | TCPhdr | Data      |   -> Packet
   Net Access   | MAC | IPhdr | TCPhdr | Data | FCS |  -> Frame
   Physical     | 1011010010110101 ...       |   -> Bits
   ```

   - This wrapping process is called encapsulation at the sender and decapsulation at the receiver.
   - Memory aid: Data, Segment, Packet, Frame, Bits — "Do Some People Fear Birthdays".

7. **(b) Explain the TCP/IP protocol switch layers.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1444 (ET: N/A)]*

   Answer: The TCP/IP protocol suite has 4 layers. It was created by the US Department of Defense and is the model the internet actually runs on.

   | Layer | OSI equivalent | Function | Protocols |
   |---|---|---|---|
   | Application | 7, 6, 5 | User services, data formatting, session control — all in one layer | HTTP, HTTPS, FTP, SMTP, DNS, DHCP, SNMP, Telnet, SSH |
   | Transport | 4 | End-to-end delivery, segmentation, port addressing, reliability | TCP, UDP |
   | Internet | 3 | Logical (IP) addressing, routing, fragmentation | IP, ICMP, ARP, IGMP |
   | Network Access (Link) | 2, 1 | Framing, MAC addressing, physical transmission | Ethernet, Wi-Fi, PPP, Frame Relay |

   Layer details
   - Application – the interface for the user's program. A browser uses HTTP, mail uses SMTP/POP3/IMAP, name lookup uses DNS.
   - Transport – TCP gives connection-oriented, reliable, ordered delivery with the three-way handshake, acknowledgements, retransmission and flow control. UDP is connectionless and fast, used for DNS, DHCP, streaming and VoIP. Port numbers identify the application.
   - Internet – IP puts a source and destination address on every packet and routers forward it hop by hop. It is connectionless and best-effort. ICMP reports errors and carries ping; ARP resolves IP to MAC.
   - Network Access – puts the packet into a frame, adds MAC addresses and a CRC, and drives the actual medium.

   - The "switching" between layers is encapsulation: each layer adds its own header on the way down and strips it on the way up.

8. **(b) Draw the diagram of TCP/IP protocol suite and mention the name of protocols used in different layers of TCP/IP.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1352 (ET: N/A)]*

   Answer:

   Diagram of the TCP/IP protocol suite
   ```
   +---------------------------------------------------------------+
   | APPLICATION LAYER                                             |
   |  HTTP  HTTPS  FTP  TFTP  SMTP  POP3  IMAP  DNS  DHCP          |
   |  SNMP  Telnet  SSH  NTP                                       |
   +---------------------------------------------------------------+
   | TRANSPORT LAYER                                               |
   |            TCP                 |            UDP               |
   |  (reliable, connection-       |  (fast, connectionless)       |
   |   oriented, ordered)          |                               |
   +---------------------------------------------------------------+
   | INTERNET LAYER                                                |
   |      IPv4 / IPv6      ICMP      IGMP      ARP / RARP          |
   |      routing: OSPF, RIP, BGP, EIGRP                           |
   +---------------------------------------------------------------+
   | NETWORK ACCESS LAYER (Data Link + Physical)                   |
   |  Ethernet  Wi-Fi (802.11)  PPP  Frame Relay  ATM  DSL         |
   |  cables, fibre, connectors, NIC drivers                       |
   +---------------------------------------------------------------+
   ```

   Protocols by layer

   | Layer | Protocols |
   |---|---|
   | Application | HTTP (80), HTTPS (443), FTP (20/21), SMTP (25), POP3 (110), IMAP (143), DNS (53), DHCP (67/68), SNMP (161), Telnet (23), SSH (22) |
   | Transport | TCP, UDP (and SCTP) |
   | Internet | IPv4, IPv6, ICMP, IGMP, ARP, RARP, plus routing protocols OSPF, RIP, BGP, EIGRP |
   | Network Access | Ethernet, Wi-Fi 802.11, PPP, HDLC, Frame Relay, ATM |

   - ARP sits between the Internet and Network Access layers, because it maps an IP address to a MAC address.

9. **How many Layers of OSI?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1450 (ET: N/A)]*

   Answer: The OSI model has `7 layers`.

   ```
   7. Application
   6. Presentation
   5. Session
   4. Transport
   3. Network
   2. Data Link
   1. Physical
   ```
   - It was defined by ISO in 1984.
   - The TCP/IP model, by contrast, has 4 layers (some books show 5).
   - Memory aid, top to bottom: All People Seem To Need Data Processing.

10. **রাউটার OSI এর কোন লেয়ারে থাকে?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1450 (ET: N/A)]*

    Answer: A router works at the `Network layer, Layer 3` of the OSI model.

    - It reads the destination IP address in the packet header and uses its routing table to choose the best path to the destination network.
    - It joins different networks together, and it does not forward broadcasts, so each of its interfaces is a separate broadcast domain.
    - Other functions at Layer 3: fragmentation, TTL decrement, NAT and ACL filtering.

    Devices by layer

    | Layer | Devices |
    |---|---|
    | 1 Physical | Hub, repeater, cable, modem |
    | 2 Data Link | Switch, bridge, NIC, access point |
    | 3 Network | `Router`, Layer 3 switch |
    | 4 Transport | Firewall (stateful), load balancer |
    | 7 Application | Proxy server, gateway, WAF |

11. **Write the name of OSI layers.** *[NSDA Assistant Maintenance Engineer 11.05.2024 compact it 384 (ET: N/A)]*

    Answer: The seven layers of the OSI model are:

    ```
    Layer 7 - Application
    Layer 6 - Presentation
    Layer 5 - Session
    Layer 4 - Transport
    Layer 3 - Network
    Layer 2 - Data Link
    Layer 1 - Physical
    ```

    - Top to bottom memory aid: All People Seem To Need Data Processing.
    - Bottom to top memory aid: Please Do Not Throw Sausage Pizza Away.
    - Layers 1–3 are called the network support layers, layers 5–7 the user support layers, and layer 4 links the two groups.

12. **Write the name of OSI layers protocol for every layers.** *[NSDA Assistant Maintenance Engineer 11.05.2024 compact it 384 (ET: N/A)]*

    Answer: Protocols used at each OSI layer.

    | # | Layer | Protocols |
    |---|---|---|
    | 7 | Application | HTTP, HTTPS, FTP, TFTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH, NTP |
    | 6 | Presentation | SSL/TLS, JPEG, GIF, MPEG, ASCII, EBCDIC, MIME |
    | 5 | Session | NetBIOS, RPC, PPTP, SQL sessions, SMB, NFS |
    | 4 | Transport | TCP, UDP, SCTP |
    | 3 | Network | IPv4, IPv6, ICMP, IGMP, ARP, RARP, OSPF, RIP, BGP, EIGRP, IPsec |
    | 2 | Data Link | Ethernet (802.3), Wi-Fi (802.11), PPP, HDLC, Frame Relay, ATM, STP, VLAN (802.1Q) |
    | 1 | Physical | RS-232, DSL, ISDN, USB, Bluetooth physical, cable and fibre standards |

    - Note: ARP is often placed at Layer 2, since it deals with MAC addresses, and sometimes at Layer 3, since it is triggered by IP. Both placements appear in textbooks.

13. **Tabular representation of TCP/IP layer, functions of each layer, Associate protocols, device, and software in each layer. Different types of network firewalls. Explain NGFW compared to traditional firewall.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 301 (ET: BIBM)]*

    Answer:

    (a) TCP/IP layers, functions, protocols, devices and software

    | Layer | Function | Protocols | Devices | Software |
    |---|---|---|---|---|
    | Application | User services, data format, session control | HTTP, HTTPS, FTP, SMTP, DNS, DHCP, SNMP, SSH | Proxy server, WAF, application gateway | Browser, mail client, web server, DNS server |
    | Transport | End-to-end delivery, ports, flow and error control | TCP, UDP | Stateful firewall, load balancer | Socket library, TCP stack |
    | Internet | Logical addressing, routing, fragmentation | IP, ICMP, ARP, IGMP, OSPF, BGP | Router, Layer 3 switch | Routing daemon, IP stack |
    | Network Access | Framing, MAC addressing, physical signalling | Ethernet, Wi-Fi, PPP, ARP | Switch, bridge, hub, NIC, AP | NIC driver, firmware |

    (b) Types of network firewall

    | Type | How it works |
    |---|---|
    | Packet-filtering | Checks source/destination IP, port and protocol against ACLs. Fast but stateless |
    | Stateful inspection | Keeps a connection table and allows return traffic only for sessions it saw start |
    | Application-layer (proxy) | Terminates and re-originates the connection, inspecting the payload of HTTP, FTP, DNS |
    | Circuit-level gateway | Validates the TCP handshake at the session layer, does not inspect content |
    | NAT firewall | Hides internal addresses behind one public address |
    | NGFW | All of the above plus deep packet inspection, IPS, application awareness and threat intelligence |
    | Cloud / WAF | Delivered as a service; a WAF specifically protects web applications from SQLi and XSS |

    (c) NGFW compared with a traditional firewall

    | Point | Traditional firewall | Next Generation Firewall (NGFW) |
    |---|---|---|
    | Inspection depth | Header only (IP, port, protocol) | Deep packet inspection of the payload |
    | Application awareness | Sees only port 80 or 443 | Identifies the actual application — Facebook, Skype, BitTorrent — even on port 443 |
    | User awareness | IP based | Integrates with Active Directory, so rules follow the user |
    | Threat prevention | None | Built-in IPS, antivirus, sandboxing, anti-bot |
    | Encrypted traffic | Cannot inspect | SSL/TLS decryption and inspection |
    | Intelligence | Static rules | Live threat-intelligence feeds and reputation lists |
    | Cost and load | Cheap, fast | Expensive, needs more CPU |

    - In short: a traditional firewall asks "which port?", an NGFW asks "which application, which user, and is the content malicious?"

14. **Explain TCP/IP model and its protocol and device.** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 404 (ET: N/A)]*

    Answer:

    The TCP/IP model
    - A 4-layer practical model developed by the US DoD and used by the internet. Each layer has real, implemented protocols, unlike the theoretical OSI model.

    | Layer | Function | Protocols | Devices |
    |---|---|---|---|
    | Application | Services to the user program, formatting, sessions | HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH | Proxy, application gateway, WAF |
    | Transport | Segmentation, ports, reliability, flow control | TCP, UDP | Stateful firewall, load balancer |
    | Internet | IP addressing, routing, fragmentation | IP, ICMP, ARP, IGMP, OSPF, RIP, BGP | Router, Layer 3 switch |
    | Network Access | Framing, MAC addressing, media access, bit transmission | Ethernet, Wi-Fi, PPP, Frame Relay | Switch, bridge, hub, NIC, modem, cable |

    Short explanation of each layer
    - Application – what the user sees: the browser, the mail client, name lookup through DNS.
    - Transport – TCP for reliable, ordered delivery with the three-way handshake and acknowledgements; UDP for speed with no guarantee. Port numbers identify the process.
    - Internet – IP gives every host a logical address; routers forward packets hop by hop using the longest prefix match. Best-effort and connectionless.
    - Network Access – merges the OSI Data Link and Physical layers; builds frames, adds MAC addresses and a CRC, and puts the signal on the wire.

    - Data unit names: Data -> Segment -> Packet -> Frame -> Bits.

15. **Write down the OSI model.** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 404 (ET: N/A)]*

    Answer: The OSI model, published by ISO in 1984, has 7 layers.

    | # | Layer | Function | PDU |
    |---|---|---|---|
    | 7 | Application | Network services for the user's program | Data |
    | 6 | Presentation | Translation, encryption, compression | Data |
    | 5 | Session | Establish, manage and terminate sessions | Data |
    | 4 | Transport | End-to-end delivery, segmentation, flow control | Segment |
    | 3 | Network | Logical addressing and routing | Packet |
    | 2 | Data Link | Framing, MAC addressing, error detection | Frame |
    | 1 | Physical | Raw bit transmission over the medium | Bit |

    - Purpose: to standardise communication so equipment from different vendors can interoperate, to break a complex problem into manageable parts, and to give engineers a common vocabulary for design and troubleshooting.
    - The lower three layers handle network support; the upper three handle user support; Transport joins the two halves.

16. **How many TCP/IP layer? Write its Layer name?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

    Answer: The TCP/IP model has `4 layers`.

    ```
    4. Application Layer      (OSI 7 + 6 + 5)
    3. Transport Layer        (OSI 4)
    2. Internet Layer         (OSI 3)
    1. Network Access Layer   (OSI 2 + 1)
    ```

    | Layer | Also called | Protocols |
    |---|---|---|
    | Application | Process layer | HTTP, FTP, SMTP, DNS, DHCP, SSH |
    | Transport | Host-to-host | TCP, UDP |
    | Internet | Network layer | IP, ICMP, ARP, IGMP |
    | Network Access | Link / Network Interface | Ethernet, Wi-Fi, PPP |

    - Some textbooks show a 5-layer version by splitting Network Access into separate Data Link and Physical layers.
    - It is also called the DoD model, since it came from the US Department of Defense.

17. **Differentiate between OSI Model and TCP/IP Model. Draw the diagram of 4 Layers of TCP/IP Model including the main function of each layer and related protocols. List some basic functions performed at MAC layer.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 530 (ET: MIST)]*

    Answer:

    (a) OSI model vs TCP/IP model

    | Point | OSI model | TCP/IP model |
    |---|---|---|
    | Layers | 7 | 4 (sometimes shown as 5) |
    | Developed by | ISO, 1984 | US DoD / DARPA, 1970s |
    | Nature | Theoretical reference model | Practical, implemented model |
    | Protocols | Defines no protocols of its own | Built around real protocols (TCP, IP, HTTP) |
    | Approach | Model first, protocols later | Protocols first, model described later |
    | Session and Presentation | Separate layers 5 and 6 | Merged into the Application layer |
    | Physical and Data Link | Separate layers 1 and 2 | Merged into Network Access |
    | Transport | Connection-oriented only | Both connection-oriented (TCP) and connectionless (UDP) |
    | Usage | Teaching, design, troubleshooting | The actual internet |
    | Reliability | Layer dependent | Handled mainly at the Transport layer |

    (b) Four-layer TCP/IP diagram with functions and protocols
    ```
    +--------------------------------------------------------------+
    | APPLICATION  - user services, formatting, session control     |
    |   HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, SSH    |
    +--------------------------------------------------------------+
    | TRANSPORT    - segmentation, ports, reliability, flow control |
    |   TCP (reliable)            UDP (fast, connectionless)        |
    +--------------------------------------------------------------+
    | INTERNET     - logical IP addressing, routing, fragmentation  |
    |   IPv4, IPv6, ICMP, IGMP, ARP, OSPF, RIP, BGP                 |
    +--------------------------------------------------------------+
    | NETWORK ACCESS - framing, MAC addressing, bit transmission    |
    |   Ethernet 802.3, Wi-Fi 802.11, PPP, Frame Relay              |
    +--------------------------------------------------------------+
    ```

    (c) Basic functions of the MAC sub-layer
    - Physical addressing – adds the 48-bit source and destination MAC addresses to each frame.
    - Framing – marks where a frame starts and ends, and adds the FCS field.
    - Media access control – decides who may transmit, using CSMA/CD on classic Ethernet and CSMA/CA on Wi-Fi, so collisions are avoided or handled.
    - Error detection – computes and checks the CRC in the FCS; a corrupted frame is discarded.
    - Frame filtering and forwarding – a switch reads the destination MAC and sends the frame only out of the correct port.
    - Collision handling – on shared media, detects a collision, sends a jam signal and applies binary exponential backoff.

18. **What is OSI Model? Write all layer name sequence should be top to bottom or bottom to top.** *[DESCO Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)]*

    Answer:

    What is the OSI model
    - The Open Systems Interconnection model is a 7-layer reference framework published by ISO in 1984. It describes how data travels from an application on one machine to an application on another, and it lets equipment from different vendors interoperate.

    Layer names, both directions

    | Top to bottom | Bottom to top |
    |---|---|
    | 7 Application | 1 Physical |
    | 6 Presentation | 2 Data Link |
    | 5 Session | 3 Network |
    | 4 Transport | 4 Transport |
    | 3 Network | 5 Session |
    | 2 Data Link | 6 Presentation |
    | 1 Physical | 7 Application |

    Which direction is correct
    - Both are correct; the direction depends on what you are describing.
    - Data being sent travels top to bottom (encapsulation, at the sender).
    - Data being received travels bottom to top (decapsulation, at the receiver).
    - Memory aids: "All People Seem To Need Data Processing" (top down) and "Please Do Not Throw Sausage Pizza Away" (bottom up).

19. **Difference between OSI model and TCP/IP model. Relation between Data, Segment, Packet and Bit in OSI model.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 510 (ET: MIST)]*

    Answer:

    (a) OSI vs TCP/IP

    | Point | OSI | TCP/IP |
    |---|---|---|
    | Number of layers | 7 | 4 |
    | Developed by | ISO (1984) | US DoD / DARPA (1970s) |
    | Type | Theoretical reference | Practical, in use today |
    | Protocol dependence | Protocol independent | Protocol specific |
    | Design order | Model first, then protocols | Protocols first, then model |
    | Session and Presentation | Separate layers | Merged into Application |
    | Physical and Data Link | Separate layers | Merged into Network Access |
    | Transport service | Connection-oriented only | TCP and UDP both |
    | Use | Teaching and troubleshooting | The real internet |

    (b) Relation between Data, Segment, Packet and Frame/Bit
    - These are the PDU (Protocol Data Unit) names — the same information called by a different name at each layer as headers are added.

    | OSI layer | PDU name | Header added |
    |---|---|---|
    | 7, 6, 5 Application / Presentation / Session | `Data` | Application data |
    | 4 Transport | `Segment` (TCP) / Datagram (UDP) | Ports, sequence and ACK numbers |
    | 3 Network | `Packet` | Source and destination IP |
    | 2 Data Link | `Frame` | Source and destination MAC + FCS |
    | 1 Physical | `Bit` | None, raw signal |

    ```
    Data                                  (Application)
    [TCP hdr | Data]                      = Segment
    [IP hdr | TCP hdr | Data]             = Packet
    [MAC | IP hdr | TCP hdr | Data | FCS] = Frame
    1010110100101101 ...                  = Bits
    ```
    - Adding headers on the way down is encapsulation; removing them on the way up is decapsulation. The user's data is unchanged throughout — only the wrapping differs.

20. **(a) List down the layers of OSI model in top-down manner.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 480 (ET: N/A)]*

    Answer: The OSI layers in top-down order:

    ```
    7. Application   - services for the user's program (HTTP, FTP, SMTP)
    6. Presentation  - translation, encryption, compression (TLS, JPEG)
    5. Session       - establishes, manages and ends sessions (NetBIOS, RPC)
    4. Transport     - end-to-end delivery, ports, flow control (TCP, UDP)
    3. Network       - logical addressing and routing (IP, ICMP, OSPF)
    2. Data Link     - framing, MAC addressing, error detection (Ethernet, PPP)
    1. Physical      - raw bits on the medium (cables, hubs, connectors)
    ```

    - Memory aid: All People Seem To Need Data Processing.
    - This is the direction data takes at the sender, where each layer adds its own header (encapsulation).

21. **Fill up the following protocol table by work at which layer?** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 452 (ET: BUET)]*
| Protocol Name | Layer |
|---|---|
| Carrier-Sense Multiple Access (CSMA) |  |
| Open Shortest Path First (OSPF) |  |
| Transmission Control Protocol (TCP) |  |
| Routing Information Protocol (RIP) |  |
| User datagram protocol (UDP) |  |

    Answer: Completed protocol table.

    | Protocol Name | Layer |
    |---|---|
    | Carrier-Sense Multiple Access (CSMA) | Data Link layer (Layer 2), MAC sub-layer |
    | Open Shortest Path First (OSPF) | Network layer (Layer 3) |
    | Transmission Control Protocol (TCP) | Transport layer (Layer 4) |
    | Routing Information Protocol (RIP) | Network layer (Layer 3) |
    | User Datagram Protocol (UDP) | Transport layer (Layer 4) |

    Reasons
    - CSMA is a media-access method — it decides who may transmit on a shared medium — so it belongs to the MAC sub-layer of the Data Link layer. Variants: CSMA/CD on wired Ethernet, CSMA/CA on Wi-Fi.
    - OSPF is a link-state routing protocol that builds the IP routing table, so it is a Network layer function. It runs directly over IP as protocol number 89.
    - TCP provides end-to-end reliable delivery with ports, sequence numbers and acknowledgements — Transport layer.
    - RIP is a distance-vector routing protocol, also a Network layer function. Note that RIP messages are carried inside UDP port 520, but the job it performs is routing.
    - UDP provides connectionless transport with ports and a checksum — Transport layer.

22. **Which layer is used to link the network support layers and user support layers?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

    Answer: The `Transport layer (Layer 4)` links the network support layers and the user support layers.

    - Network support layers: Physical (1), Data Link (2) and Network (3). They deal with the physical movement of data — electrical signals, MAC addresses and routing.
    - User support layers: Session (5), Presentation (6) and Application (7). They deal with interoperability between software processes.
    - The Transport layer sits between the two groups and makes sure that whatever the lower layers deliver is in a form the upper layers can use: it reassembles segments in the right order, recovers lost data, and hands a clean, complete stream upward.

    ```
    7 Application  |
    6 Presentation |  User support layers
    5 Session      |
    --------------------------------
    4 Transport    <- the link between the two groups
    --------------------------------
    3 Network      |
    2 Data Link    |  Network support layers
    1 Physical     |
    ```

23. **What is the number for the Network layer and the support layer?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

    Answer:

    - The `Network layer is Layer 3` of the OSI model. Its job is logical (IP) addressing and routing packets from source to destination across different networks. Devices: router and Layer 3 switch. PDU: packet.
    - The support layers are of two kinds:
      - Network support layers – `Layers 1, 2 and 3` (Physical, Data Link, Network). They handle the physical movement of bits, frames and packets.
      - User support layers – `Layers 5, 6 and 7` (Session, Presentation, Application). They let software processes interoperate.
    - Layer 4, Transport, is neither; it is the link between the two groups.

24. **(c) Write the all layers of OSI model.** *[BARC Programmer 04.08.2023 compact it 598 (ET: N/A)]*

    Answer: The seven layers of the OSI model.

    | # | Layer | Function | PDU | Device |
    |---|---|---|---|---|
    | 7 | Application | Services for the user's program | Data | Proxy, gateway |
    | 6 | Presentation | Translation, encryption, compression | Data | — |
    | 5 | Session | Session setup, control and termination | Data | — |
    | 4 | Transport | End-to-end delivery, ports, flow control | Segment | Firewall |
    | 3 | Network | Logical addressing, routing | Packet | Router |
    | 2 | Data Link | Framing, MAC addressing, error detection | Frame | Switch, bridge |
    | 1 | Physical | Raw bit transmission | Bit | Hub, cable, repeater |

    - Memory aid: All People Seem To Need Data Processing.

25. **In order to prevent that the company decided to add end to end encryption techniques which layer of the OSI model is suitable to work in considering parameters like development time, software maintainability and development cost, Give reasons for your concepts.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 438 (ET: BIBM)]*

    Answer: For end-to-end encryption, the `Presentation layer (Layer 6)` is the classically correct answer, and in practice the work is done at the `Application layer (Layer 7)` using TLS.

    Why the upper layers are the right choice
    - End-to-end means the data must stay encrypted from the sender's application all the way to the receiver's application, passing through routers and switches untouched. Only an upper layer can do that; encryption placed lower down is decrypted at every hop.
    - The Presentation layer's defined job is exactly this — translation, compression and encryption of the data.

    Judged against the three parameters asked for

    | Parameter | Why the upper layer wins |
    |---|---|
    | Development time | TLS libraries (OpenSSL) are ready-made. Adding HTTPS to an application takes days, not months. Layer 2 or Layer 3 encryption needs new hardware and network redesign |
    | Software maintainability | The change is confined to one place in the application. Certificate renewal and cipher upgrades are configuration, not code. Lower-layer encryption spreads the change across every router and switch |
    | Development cost | No new hardware; certificates are cheap or free (Let's Encrypt). Layer 1 or 2 encryption needs specialised link encryptors on every link, which is far more expensive |

    Comparison of the alternatives

    | Layer | Technology | Scope | Verdict |
    |---|---|---|---|
    | 1 Physical | Link encryptor | One cable | Very costly, protects one hop only |
    | 2 Data Link | MACsec | One LAN hop | Decrypted at each switch — not end to end |
    | 3 Network | IPsec | Host to host or gateway to gateway | Genuinely secure, but complex to configure and manage |
    | 4 Transport | TLS | Process to process | The practical, cheap and widely used choice |
    | 6/7 Presentation / Application | TLS, PGP, S/MIME | Application to application | True end-to-end, lowest cost and effort |

    Conclusion
    - Implement encryption at the Presentation/Application layer using TLS (or PGP for mail). It gives true end-to-end protection, reuses proven libraries, keeps maintenance in one place, and needs no new hardware — the best result on all three parameters.

26. **What is TCP/IP model? Briefly explain TCP/IP model.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 837 (ET: N/A)], [EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)]*

    Answer:

    What is the TCP/IP model
    - TCP/IP (Transmission Control Protocol / Internet Protocol) is the 4-layer protocol suite that the internet actually runs on. It was developed by DARPA for the US Department of Defense in the 1970s and became the standard in 1983.
    - Unlike OSI, it was built protocol-first: the protocols existed and the model was written to describe them. That is why it is called a practical model.

    The four layers

    | Layer | Function | Main protocols |
    |---|---|---|
    | Application | Services for the user program, data formatting, session control | HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH |
    | Transport | End-to-end delivery, segmentation, port addressing, reliability | TCP, UDP |
    | Internet | Logical addressing, routing, fragmentation | IP, ICMP, ARP, IGMP |
    | Network Access | Framing, MAC addressing, physical signalling | Ethernet, Wi-Fi, PPP, Frame Relay |

    Brief explanation
    - Application – combines OSI layers 5, 6 and 7. It is what the user's software talks to.
    - Transport – TCP sets up a connection with a three-way handshake (SYN, SYN-ACK, ACK), numbers every byte, acknowledges what arrives and retransmits what is lost. UDP simply sends, with no handshake, which suits DNS, DHCP, VoIP and video.
    - Internet – IP is connectionless and best-effort. Every packet carries a source and destination IP address, and each router forwards it independently using the longest prefix match.
    - Network Access – combines OSI layers 1 and 2. It builds frames, adds MAC addresses and a CRC, and transmits the signal.

    Data unit names: Data -> Segment -> Packet -> Frame -> Bits.

27. **(a) What is OSI model? Explain how two computers can exchange information using the OSI model.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 694 (ET: N/A)]*

    Answer:

    What is the OSI model
    - A 7-layer reference model published by ISO in 1984 that describes how two computers exchange information. Each layer performs a defined function and offers a service to the layer above it.

    How two computers exchange information
    - Communication is logical between peer layers, but physical only at Layer 1. Data goes down the stack at the sender and up the stack at the receiver.

    ```
       COMPUTER A (sender)                      COMPUTER B (receiver)
    7  Application    <--- logical peer link --->  Application
    6  Presentation   <--- logical peer link --->  Presentation
    5  Session        <--- logical peer link --->  Session
    4  Transport      <--- logical peer link --->  Transport
    3  Network        <--- logical peer link --->  Network
    2  Data Link      <--- logical peer link --->  Data Link
    1  Physical  ======= actual cable / radio ===  Physical
    ```

    Step by step
    - At the sender, the Application layer produces the data (for example an HTTP GET).
    - Presentation encrypts and compresses it; Session marks the start of the dialogue.
    - Transport splits it into segments, numbers them and adds port numbers.
    - Network adds the source and destination IP addresses, making a packet.
    - Data Link wraps the packet in a frame with MAC addresses and a CRC.
    - Physical converts the frame into bits and puts them on the medium. This whole process is `encapsulation`.
    - At the receiver the reverse happens — `decapsulation`. Physical rebuilds the bits, Data Link checks the CRC and strips the MAC header, Network checks the IP address and strips the IP header, Transport reorders the segments and acknowledges them, and the upper layers decrypt and present the data to the application.
    - Each layer only reads the header its peer layer wrote, which is why the layers stay independent of each other.

28. **TCP/IP model এর Layer গুলোর কাজ লিখুন।** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 698 (ET: DPI)]*

    Answer: (Answered in English, as required for IT topics.) The TCP/IP model has 4 layers.

    | Layer | Work it does |
    |---|---|
    | Application | Provides services to the user's program — web pages, email, file transfer, name lookup. Combines OSI layers 5, 6 and 7, so formatting, encryption and session control also happen here. Protocols: HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH |
    | Transport | Breaks the message into segments, numbers them, adds port numbers so the right program receives them, and rebuilds them in order at the other end. TCP adds reliability — handshake, acknowledgement, retransmission, flow control and congestion control. UDP is fast and connectionless |
    | Internet | Adds the source and destination IP addresses, chooses the path, and forwards the packet router by router. Also handles fragmentation and TTL. Protocols: IP, ICMP, ARP, IGMP, and the routing protocols OSPF, RIP, BGP |
    | Network Access | Puts the packet into a frame with MAC addresses and a CRC, controls access to the medium, and converts the frame into electrical, optical or radio signals. Protocols: Ethernet, Wi-Fi, PPP |

    - Data unit at each layer: Data -> Segment -> Packet -> Frame -> Bits.
    - Adding a header at each layer going down is encapsulation; removing it going up is decapsulation.

29. **What is OSI model? Write different layers of OSI model.** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 699 (ET: BUET)]*

    Answer:

    What is the OSI model
    - The Open Systems Interconnection model is a 7-layer reference model created by ISO in 1984. It divides the job of network communication into seven independent layers so that products from different vendors can work together, and so that a fault can be isolated to one layer.

    The seven layers

    | # | Layer | Function | PDU | Example protocols |
    |---|---|---|---|---|
    | 7 | Application | Network services for user programs | Data | HTTP, FTP, SMTP, DNS |
    | 6 | Presentation | Translation, encryption, compression | Data | TLS, JPEG, ASCII |
    | 5 | Session | Establish, manage, terminate sessions | Data | NetBIOS, RPC |
    | 4 | Transport | End-to-end delivery, ports, flow control | Segment | TCP, UDP |
    | 3 | Network | Logical addressing, routing | Packet | IP, ICMP, OSPF |
    | 2 | Data Link | Framing, MAC addressing, error detection | Frame | Ethernet, PPP |
    | 1 | Physical | Raw bit transmission | Bit | Cables, hubs |

    - Layers 1–3 are the network support layers, 5–7 the user support layers, and 4 joins them.

30. **What is the difference between DOD and OSI model?** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 700 (ET: BUET)]*

    Answer: The DOD model is another name for the TCP/IP model, since it was created by the US Department of Defense. The question is therefore the OSI vs TCP/IP comparison.

    | Point | OSI model | DOD (TCP/IP) model |
    |---|---|---|
    | Layers | 7 | 4 |
    | Created by | ISO, 1984 | US DoD / DARPA, 1970s |
    | Nature | Theoretical reference model | Practical, working model |
    | Protocols | Defines none of its own | Built from real protocols — TCP, IP, HTTP |
    | Order of design | Model first, protocols later | Protocols first, model later |
    | Session and Presentation | Separate layers 5 and 6 | Merged into Application |
    | Physical and Data Link | Separate layers 1 and 2 | Merged into Network Access |
    | Transport | Connection-oriented only | TCP (connection-oriented) and UDP (connectionless) |
    | Flexibility | Strict layer boundaries | Layers are less rigidly separated |
    | Usage today | Teaching, design, troubleshooting | Runs the actual internet |

    Layer mapping
    ```
    OSI                      DOD / TCP-IP
    7 Application    |
    6 Presentation   |-----> Application
    5 Session        |
    4 Transport      ------> Transport (Host-to-Host)
    3 Network        ------> Internet
    2 Data Link      |-----> Network Access
    1 Physical       |
    ```

31. **What is PDU?** *[BARC Data Entry Officer 10.09.2022 compact it 702 (ET: N/A)]*

    Answer: PDU stands for `Protocol Data Unit` — the name given to a unit of data at a particular layer of the network model.

    - At each layer the data carries a different header, so it is given a different name.

    | OSI layer | PDU name | What is added |
    |---|---|---|
    | 7, 6, 5 | Data (or Message) | Application information |
    | 4 Transport | Segment (TCP) / Datagram (UDP) | Ports, sequence and acknowledgement numbers |
    | 3 Network | Packet | Source and destination IP addresses |
    | 2 Data Link | Frame | Source and destination MAC addresses + FCS |
    | 1 Physical | Bit | Nothing — raw electrical, optical or radio signal |

    Structure of a PDU
    - A PDU generally has three parts: the header (control information written by that layer), the payload (the PDU handed down from the layer above, called the SDU or Service Data Unit), and sometimes a trailer, such as the Ethernet FCS.
    - Memory aid: Data, Segment, Packet, Frame, Bits.

32. **(খ) Computer network এর OSI 7-Layer গুলো উদাহরণসহ লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 767 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The 7 layers of the OSI model with examples.

    | # | Layer | Function | Real-world example |
    |---|---|---|---|
    | 7 | Application | Network services for the user's software | Typing www.google.com in Chrome — HTTP request |
    | 6 | Presentation | Translation, encryption, compression | TLS encrypts the page; a JPEG photo is decoded; UTF-8 conversion |
    | 5 | Session | Opens, keeps and closes the dialogue | A bank internet-banking session that stays alive until logout |
    | 4 | Transport | Segmentation, ports, reliability | TCP port 443 splits the page into segments and re-sends any that are lost |
    | 3 | Network | Logical addressing, path selection | The IP header carries the packet from 103.108.140.5 to Google's server through many routers |
    | 2 | Data Link | Framing, MAC delivery on one hop | The Ethernet frame from your PC's NIC to the router's MAC address |
    | 1 | Physical | Raw bits on the medium | Voltage on the UTP cable, light pulses in fibre, Wi-Fi radio waves |

    - Devices: hub at Layer 1, switch at Layer 2, router at Layer 3, firewall at Layer 4, proxy at Layer 7.
    - Memory aid: All People Seem To Need Data Processing.

33. **Computer Network এ OSI Model এর Layer কয়টি?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

    Answer: The OSI model has `7 layers`.

    ```
    7. Application
    6. Presentation
    5. Session
    4. Transport
    3. Network
    2. Data Link
    1. Physical
    ```
    - Defined by ISO in 1984.
    - The TCP/IP model, used in practice, has 4 layers.
    - Layers 1–3 are network support layers, 5–7 are user support layers, and layer 4 (Transport) links the two.

34. **OSI Model এর কাজ কী? এর লেয়ারসমূহ কী কী?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 811 (ET: IBA)]*

    Answer: (Answered in English, as required for IT topics.)

    Work of the OSI model
    - It is a reference framework that standardises how network communication happens, so equipment and software from different vendors can interoperate.
    - It divides one very complex problem into seven smaller ones, each with a clear job and a clear interface to its neighbours.
    - It allows any layer to be changed or upgraded without disturbing the others — Wi-Fi replaced cable at Layers 1 and 2 without touching IP or HTTP.
    - It makes troubleshooting systematic: no link light is Layer 1, wrong IP is Layer 3, DNS failure is Layer 7.
    - It provides the common vocabulary engineers use to describe networks.

    Its layers

    | # | Layer | Function |
    |---|---|---|
    | 7 | Application | Services for the user's program (HTTP, FTP, SMTP, DNS) |
    | 6 | Presentation | Translation, encryption, compression (TLS, JPEG) |
    | 5 | Session | Establish, manage and end the session (NetBIOS, RPC) |
    | 4 | Transport | End-to-end delivery, ports, flow control (TCP, UDP) |
    | 3 | Network | Logical addressing and routing (IP, ICMP, OSPF) |
    | 2 | Data Link | Framing, MAC addressing, error detection (Ethernet, PPP) |
    | 1 | Physical | Raw bit transmission (cable, fibre, radio) |

35. **Which layer data packet receive port from sender to destination? (a) Data link layer (b) Network layer (c) Transport layer (d) None** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

    Answer: The correct option is `(c) Transport layer`.

    - Port numbers live in the TCP and UDP headers, which are added at the Transport layer. A port identifies which application process on the destination host should receive the data — HTTP 80, HTTPS 443, SSH 22, DNS 53.
    - Without a port, the receiving machine would know which host the data is for (from the IP address) but not which program.

    Why the others are wrong

    | Option | Uses which address |
    |---|---|
    | Data Link layer | MAC (physical) address — no ports |
    | Network layer | IP (logical) address — no ports |
    | Transport layer | `Port number` — correct |

    - Complete addressing chain: MAC address finds the machine on the local link, IP address finds the host across networks, port number finds the process inside that host, and the combination of IP and port is called a socket.

36. **What is OSI model? Write down the name of OSI model layer.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 837 (ET: N/A)]*

    Answer:

    What is the OSI model
    - The Open Systems Interconnection model is a 7-layer reference model created by ISO in 1984 that describes how data travels from an application on one computer to an application on another. It standardises communication so that different vendors' products interoperate, and it makes fault isolation systematic.

    Names of the layers

    ```
    7. Application   - user services (HTTP, FTP, SMTP)
    6. Presentation  - translation, encryption, compression
    5. Session       - session setup, control, teardown
    4. Transport     - segmentation, ports, reliability (TCP, UDP)
    3. Network       - logical addressing and routing (IP)
    2. Data Link     - framing, MAC addressing, error detection
    1. Physical      - raw bits on the medium
    ```
    - Memory aid: All People Seem To Need Data Processing.

37. **What is OSI and TCP/IP model and briefly explain?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 870-872 (ET: N/A)]*

    Answer:

    OSI model
    - A 7-layer theoretical reference model published by ISO in 1984: Application, Presentation, Session, Transport, Network, Data Link, Physical.
    - It defines what each layer must do, but not the protocols that do it. Its value is as a common language for design, teaching and troubleshooting.

    TCP/IP model
    - A 4-layer practical model built by the US DoD in the 1970s and running the internet today: Application, Transport, Internet, Network Access.
    - It was built around real protocols — TCP, UDP, IP — which existed before the model was written down.

    Layer mapping
    ```
    OSI                       TCP/IP
    7 Application    |
    6 Presentation   |------>  Application
    5 Session        |
    4 Transport      ------->  Transport
    3 Network        ------->  Internet
    2 Data Link      |------>  Network Access
    1 Physical       |
    ```

    Brief comparison

    | Point | OSI | TCP/IP |
    |---|---|---|
    | Layers | 7 | 4 |
    | Nature | Theoretical | Practical |
    | Protocols | None of its own | TCP, IP, HTTP, etc. |
    | Design order | Model then protocols | Protocols then model |
    | Transport service | Connection-oriented only | TCP and UDP |
    | Use today | Reference and teaching | The actual internet |

    - Both use encapsulation: Data -> Segment -> Packet -> Frame -> Bits.

38. **TCP/IP protocol suite -এর বিভিন্ন স্তরের নাম লিখুন? HTTPs কী? এর ব্যবহারের প্রয়োজনীয়তা সংক্ষেপে বর্ণনা করুন?** *[41th BCS 2021 compact it 882 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    Layers of the TCP/IP protocol suite

    | Layer | Function | Protocols |
    |---|---|---|
    | Application | Services to the user's program | HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, SSH |
    | Transport | Segmentation, ports, reliability | TCP, UDP |
    | Internet | IP addressing, routing | IP, ICMP, ARP, IGMP |
    | Network Access | Framing, MAC addressing, transmission | Ethernet, Wi-Fi, PPP |

    What is HTTPS
    - HTTPS (HyperText Transfer Protocol Secure) is HTTP running inside a TLS-encrypted channel. It uses TCP port 443, while plain HTTP uses port 80.
    - The browser and server first complete a TLS handshake: the server presents a certificate signed by a trusted CA, the two sides agree a symmetric session key, and all HTTP messages after that are encrypted with it.

    Why HTTPS is necessary
    - Confidentiality – passwords, card numbers and personal data cannot be read by anyone tapping the line. With plain HTTP everything travels in clear text.
    - Integrity – the TLS message authentication code detects any alteration, so an attacker cannot silently modify a page or inject content.
    - Authentication – the certificate proves the site really is the bank it claims to be, defeating fake sites and man-in-the-middle attacks.
    - Trust and compliance – browsers mark plain HTTP as "Not secure", and standards such as PCI-DSS require encryption for payment data.
    - SEO and modern features – search engines rank HTTPS sites higher, and features like HTTP/2 and service workers require it.

39. **বর্তমানে Hybrid network model জনপ্রিয় একটি মডেল। এই মডেলের পাঁচটি Layer হচ্ছে, Application, Transport, Physical, Data link and Network Layer। এদের কাজ দেওয়া আছে বামপাশের কলামে, ডানপাশের কলামে কাজ অনুসারে Layer গুলোর নাম লিখুন।** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 975-976 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) The five layers of the hybrid model, matched to the work described.

    | Work described | Layer |
    |---|---|
    | Transmits raw bits over the medium; defines cable, voltage, connector and data rate | `Physical` |
    | Turns bits into frames, adds MAC addresses, detects errors with CRC, controls access to the medium (hop-to-hop delivery) | `Data Link` |
    | Gives logical IP addresses and selects the best route from source network to destination network; fragmentation | `Network` |
    | Splits the message into segments, adds port numbers, provides end-to-end reliability, flow control and error recovery | `Transport` |
    | Provides services to the user's program — web, email, file transfer, name resolution; also formatting and session control | `Application` |

    The hybrid (five-layer) model
    ```
    5. Application   (OSI 7 + 6 + 5)   HTTP, FTP, SMTP, DNS
    4. Transport     (OSI 4)           TCP, UDP
    3. Network       (OSI 3)           IP, ICMP, ARP
    2. Data Link     (OSI 2)           Ethernet, Wi-Fi, PPP
    1. Physical      (OSI 1)           cable, fibre, radio
    ```
    - It is popular because it keeps the practical protocol stack of TCP/IP but separates Physical from Data Link, which matches how real equipment is built — a hub at Layer 1, a switch at Layer 2.

40. **Write down the functionality of OSI model.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1007-1008 (ET: DU)]*

    Answer: Functionality of the OSI model, layer by layer.

    | # | Layer | Functionality |
    |---|---|---|
    | 7 | Application | Gives the user's program access to the network: file transfer, email, web browsing, directory services, name resolution |
    | 6 | Presentation | Data translation between formats (ASCII, EBCDIC, UTF-8), encryption and decryption, compression |
    | 5 | Session | Establishes, maintains and terminates sessions; dialogue control (half or full duplex); synchronisation checkpoints so a long transfer can resume |
    | 4 | Transport | Segmentation and reassembly, port (service-point) addressing, connection control, end-to-end flow control, error control and retransmission |
    | 3 | Network | Logical (IP) addressing, routing between networks, path determination, fragmentation, congestion control |
    | 2 | Data Link | Framing, physical (MAC) addressing, error detection with CRC, flow control on the link, media access control |
    | 1 | Physical | Bit transmission, definition of voltage, data rate, cable and connector type, transmission mode and physical topology |

    Overall functionality of the model
    - Standardisation so multi-vendor equipment interoperates.
    - Modularity — one layer can change without affecting the rest.
    - Encapsulation and decapsulation as data moves down and up the stack.
    - Systematic troubleshooting, layer by layer.
    - A common vocabulary for network design and teaching.

41. **OSI Model এর Layer গুলো বর্ণনা করুন।** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Description of the OSI layers.

    - Layer 1 – Physical. Moves raw bits across the medium. It defines voltage levels, bit timing, data rate, cable and connector type, transmission mode (simplex, half duplex, full duplex) and physical topology. Devices: hub, repeater, cable, modem.
    - Layer 2 – Data Link. Delivers frames from one node to the next node on the same link. It performs framing, adds 48-bit MAC addresses, detects errors with a CRC in the FCS field, and controls access to a shared medium. It has two sub-layers, LLC and MAC. Devices: switch, bridge, NIC.
    - Layer 3 – Network. Moves packets from the source network to the destination network. It provides logical (IP) addressing, chooses the best path using a routing table, fragments packets that are too large, and decrements the TTL. Protocols: IP, ICMP, ARP, OSPF, BGP. Device: router.
    - Layer 4 – Transport. Provides end-to-end delivery between processes. It splits data into segments, numbers them, adds port numbers, reassembles them in order, and provides flow control and error recovery. TCP is reliable and connection-oriented; UDP is fast and connectionless.
    - Layer 5 – Session. Establishes, manages and terminates the dialogue between two applications. It controls whether the exchange is half or full duplex and inserts synchronisation checkpoints so a long transfer can restart from the last checkpoint instead of the beginning.
    - Layer 6 – Presentation. The translator of the network: converts character sets and data formats, compresses data to save bandwidth, and encrypts and decrypts for security. Examples: TLS, JPEG, MPEG, ASCII.
    - Layer 7 – Application. The layer the user actually touches, through a browser, mail client or file transfer program. Protocols: HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH.

    - Data flows down the stack at the sender (encapsulation) and up the stack at the receiver (decapsulation): Data -> Segment -> Packet -> Frame -> Bits.

42. **(d) What do you mean by network protocol? Compare TCP/IP protocol suite and OSI reference model.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1028 (ET: N/A)]*

    Answer:

    What is a network protocol
    - A protocol is an agreed set of rules that governs how two devices exchange data. Both sides must follow the same rules or communication fails.
    - Three key elements: syntax (the format and order of the fields), semantics (what each field means and what action to take) and timing (when to send and how fast).
    - Examples: HTTP for web pages, TCP for reliable transport, IP for addressing and routing, SMTP for mail, DNS for name resolution.
    - Protocols are stacked: each layer's protocol adds its own header and uses the service of the layer below.

    Comparison of the TCP/IP suite and the OSI reference model

    | Point | OSI reference model | TCP/IP protocol suite |
    |---|---|---|
    | Layers | 7 | 4 |
    | Developed by | ISO, 1984 | US DoD / DARPA, 1970s |
    | Nature | Theoretical reference model | Practical, implemented suite |
    | Protocols | Defines none of its own | Defines TCP, UDP, IP, ICMP, HTTP and others |
    | Design order | Model designed first, protocols later | Protocols existed first, model described later |
    | Session and Presentation | Separate layers 5 and 6 | Merged into the Application layer |
    | Physical and Data Link | Separate layers 1 and 2 | Merged into Network Access |
    | Transport service | Connection-oriented only | Connection-oriented (TCP) and connectionless (UDP) |
    | Layer independence | Strict, well-defined boundaries | Boundaries less rigid |
    | Adoption | Never fully implemented | Runs the whole internet |

    - Common ground: both are layered, both use encapsulation, and both provide end-to-end communication. The OSI model is used to explain, the TCP/IP suite to build.

43. **TCP/IP মডেলের Layers সমূহের কাজ সংক্ষেপে লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1042-1043 (ET: DPI)]*

    Answer: (Answered in English, as required for IT topics.) Work of the TCP/IP model layers, in short.

    | Layer | Work |
    |---|---|
    | Application | Provides network services to the user's program — browsing, email, file transfer, name lookup. It also does the formatting, encryption and session control that OSI splits into layers 6 and 5. Protocols: HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH |
    | Transport | Splits the message into segments, adds port numbers so the right program gets the data, and reassembles in order at the far end. TCP adds the three-way handshake, acknowledgements, retransmission, flow control and congestion control; UDP just sends, with no guarantee |
    | Internet | Adds the source and destination IP addresses, selects the route, forwards the packet router by router, handles fragmentation and TTL. Protocols: IP, ICMP, ARP, IGMP, plus routing protocols OSPF, RIP, BGP |
    | Network Access | Builds the frame with MAC addresses and a CRC, controls access to the medium, and converts the frame into electrical, optical or radio signals. Protocols: Ethernet, Wi-Fi, PPP |

    - Data unit at each stage: Data -> Segment -> Packet -> Frame -> Bits.

44. **(ক) OSI Model (Layer) এর সাতটি Layer কী কী? প্রথম দুটি সংক্ষেপে বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1097-1098 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    The seven layers of the OSI model
    ```
    7. Application
    6. Presentation
    5. Session
    4. Transport
    3. Network
    2. Data Link
    1. Physical
    ```

    The first two layers described

    Layer 1 – Physical layer
    - Transmits raw bits (0s and 1s) over the physical medium as electrical voltage, light pulses or radio waves.
    - It defines the mechanical and electrical characteristics: cable and connector type, pin assignment, voltage levels, bit duration and data rate.
    - It defines the transmission mode — simplex, half duplex or full duplex — and the physical topology, such as bus, star or ring.
    - It performs no error checking at all; it simply moves bits.
    - PDU: bit. Devices: hub, repeater, cable, connector, modem.

    Layer 2 – Data Link layer
    - Delivers a frame from one node to the next node on the same physical link (hop-to-hop delivery).
    - Framing – groups bits into frames with a clear start and end.
    - Physical addressing – adds the 48-bit source and destination MAC addresses.
    - Error detection – appends a CRC in the FCS field; a corrupted frame is discarded.
    - Flow control – stops a fast sender from swamping a slow receiver on the link.
    - Media access control – decides who may transmit, using CSMA/CD on Ethernet or CSMA/CA on Wi-Fi.
    - Sub-layers: LLC (interface to Layer 3) and MAC (addressing and media access).
    - PDU: frame. Devices: switch, bridge, NIC. Protocols: Ethernet, PPP, HDLC.

45. **(খ) TCP/IP প্রোটোকল কী কাজ করে তা বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1098 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The TCP/IP protocol suite is what makes internet communication possible. Its work, layer by layer.

    What TCP does
    - Establishes a connection with the three-way handshake (SYN, SYN-ACK, ACK) before any data moves.
    - Numbers every byte with a sequence number, so the receiver can reassemble the data in the right order.
    - Acknowledges what arrives and retransmits anything that is lost or corrupted, which makes delivery reliable.
    - Provides flow control through the sliding window, so a fast sender cannot swamp a slow receiver.
    - Provides congestion control (slow start, congestion avoidance) so the network is not overloaded.
    - Uses port numbers to deliver data to the correct application process.

    What IP does
    - Gives every host a unique logical address and puts a source and destination address on every packet.
    - Routes the packet hop by hop; each router makes an independent forwarding decision using the longest prefix match.
    - Fragments a packet that is larger than the link MTU and reassembles it at the destination.
    - It is connectionless and best-effort — it does not guarantee delivery, order or freedom from duplication. That is exactly why TCP exists on top of it.

    Supporting protocols
    - ICMP reports errors and carries ping and traceroute; ARP maps an IP address to a MAC address; DNS turns a name into an IP address; DHCP hands out addresses automatically; UDP offers fast, connectionless transport for DNS, VoIP and streaming.

    - Together: the application hands data to TCP, TCP makes it reliable and adds ports, IP adds addresses and finds the path, and the link layer physically moves it. The result is that any two hosts on earth can exchange data.

46. **Describe the OSI layers. Draw a diagram to show the hierarchy when the data is transmitted or received.** *[Combined Bank Senior Officer (IT/ICT) 2019 compact it 1114 (ET: DU)]*

    Answer:

    The OSI layers

    | # | Layer | Function | PDU |
    |---|---|---|---|
    | 7 | Application | Services for the user's program (HTTP, FTP, SMTP, DNS) | Data |
    | 6 | Presentation | Translation, encryption, compression (TLS, JPEG) | Data |
    | 5 | Session | Establish, manage and end the dialogue; checkpoints | Data |
    | 4 | Transport | Segmentation, ports, reliability, flow control (TCP, UDP) | Segment |
    | 3 | Network | Logical IP addressing and routing (IP, ICMP, OSPF) | Packet |
    | 2 | Data Link | Framing, MAC addressing, CRC, media access (Ethernet) | Frame |
    | 1 | Physical | Raw bits as voltage, light or radio | Bit |

    Hierarchy diagram — transmission and reception
    ```
       SENDER                                          RECEIVER
    7  Application     Data                    Data          Application  7
          |  add AH                             ^  strip AH      |
    6  Presentation   [PH | Data]              [PH | Data]   Presentation 6
          |  add PH                             ^  strip PH      |
    5  Session        [SH | Data]              [SH | Data]     Session    5
          |  add SH                             ^  strip SH      |
    4  Transport      [TCP | Data]  = SEGMENT   ^              Transport  4
          |  add TCP header                     ^  reorder + ACK
    3  Network        [IP | TCP | Data] = PACKET^                Network  3
          |  add IP header                      ^  check IP
    2  Data Link      [MAC | IP | TCP | Data | FCS] = FRAME    Data Link  2
          |  add MAC header + FCS               ^  check CRC
    1  Physical       1011010010110101 = BITS  --> BITS         Physical  1
                            |                        ^
                            +====== medium ==========+
    ```
    - Downward at the sender is `encapsulation`: every layer adds its own header.
    - Upward at the receiver is `decapsulation`: every layer removes only its own header and passes the rest up.
    - Each layer communicates logically with its peer layer on the other machine, but the only physical transfer happens at Layer 1.

47. **OSI model এর layer গুলোর নাম লিখ।** *[NPCBL Junior Technical Engineer 2019 compact it 1148 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) The names of the OSI model layers:

    ```
    7. Application
    6. Presentation
    5. Session
    4. Transport
    3. Network
    2. Data Link
    1. Physical
    ```

    - Memory aid, top to bottom: All People Seem To Need Data Processing.
    - Memory aid, bottom to top: Please Do Not Throw Sausage Pizza Away.

48. **How many layers are used in OSI and TCP/IP model? Draw the layer.** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1152 (ET: KUET)]*

    Answer: The OSI model has `7 layers` and the TCP/IP model has `4 layers`.

    Diagram with the mapping between them
    ```
    +-------------------+           +-------------------------+
    |  OSI MODEL (7)    |           |  TCP/IP MODEL (4)       |
    +-------------------+           +-------------------------+
    | 7  Application    |  \        |                         |
    +-------------------+   \       |                         |
    | 6  Presentation   |    +----->|  4  Application         |
    +-------------------+   /       |     HTTP, FTP, SMTP,    |
    | 5  Session        |  /        |     DNS, DHCP, SSH      |
    +-------------------+           +-------------------------+
    | 4  Transport      | -------->  |  3  Transport           |
    |                   |           |     TCP, UDP            |
    +-------------------+           +-------------------------+
    | 3  Network        | -------->  |  2  Internet            |
    |                   |           |     IP, ICMP, ARP       |
    +-------------------+           +-------------------------+
    | 2  Data Link      |  \        |  1  Network Access      |
    +-------------------+   +-----> |     Ethernet, Wi-Fi,    |
    | 1  Physical       |  /        |     PPP, cables         |
    +-------------------+           +-------------------------+
    ```

    - OSI layers 7, 6 and 5 become one Application layer in TCP/IP.
    - OSI layers 2 and 1 become one Network Access layer.
    - OSI Transport and Network map one-to-one onto TCP/IP Transport and Internet.
    - Some books show a 5-layer TCP/IP model by keeping Physical and Data Link separate.

49. **Give answer of the following question:** *[Dutch Bangla Bank Assistant Network/Hardware Engineer 2019 compact it 1161 (ET: BUET)]*
   a) IP address converted into physical address \_\_\_\_\_\_\_\_?
   b) Name are converted into domain name \_\_\_\_\_\_\_\_?
   c) Mail is transferred between various devices using \_\_\_\_\_\_\_\_ protocol.
   d) Data link layer responsible for convert IP address into \_\_\_\_\_\_\_\_?
   e) HTTP service provides using which protocol \_\_\_\_\_\_\_\_?

    Answer:

    | # | Blank | Answer |
    |---|---|---|
    | a | IP address converted into physical address | `ARP` (Address Resolution Protocol) |
    | b | Names are converted into domain name / IP address | `DNS` (Domain Name System) |
    | c | Mail is transferred between devices using | `SMTP` (Simple Mail Transfer Protocol) |
    | d | Data link layer converts IP address into | `MAC address` (physical address), through ARP |
    | e | HTTP service is provided using which protocol | `TCP` (port 80; HTTPS uses TCP port 443) |

    Short notes
    - ARP broadcasts "who has this IP?" on the LAN and caches the MAC address that replies. RARP does the reverse and is now replaced by DHCP.
    - DNS resolves a hostname such as www.google.com into an IP address, using UDP port 53 for queries and TCP port 53 for zone transfers.
    - SMTP (port 25, or 587 with TLS) pushes mail from client to server and between servers. POP3 (110) and IMAP (143) are used to retrieve mail.
    - The Data Link layer works with MAC addresses only; ARP supplies the mapping so the frame can be addressed.
    - HTTP is an application-layer protocol that runs over TCP, because a web page must arrive complete and in order.

50. **What is OSI model? Which layers are important for data transfer and user interaction?** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1189 (ET: N/A)]*

    Answer:

    What is the OSI model
    - A 7-layer reference model published by ISO in 1984 that describes how data moves from an application on one machine to an application on another, and lets multi-vendor equipment interoperate.

    Layers important for data transfer
    - `Physical (1)` – actually moves the bits over cable, fibre or radio. Without it nothing travels.
    - `Data Link (2)` – frames the data and delivers it hop by hop using MAC addresses, with CRC error detection.
    - `Network (3)` – gives logical IP addresses and routes the packet across networks. This is what makes end-to-end transfer between distant networks possible.
    - `Transport (4)` – the key layer for reliable transfer: segmentation, sequencing, acknowledgement, retransmission and flow control.

    Layers important for user interaction
    - `Session (5)` – opens, maintains and closes the user's dialogue, and adds checkpoints so a long transfer can resume.
    - `Presentation (6)` – makes data readable to the user: character-set translation, decompression and decryption.
    - `Application (7)` – the layer the user actually touches, through a browser, mail client or file transfer program.

    - In short: layers 1–4 are the network support (data transfer) layers, and layers 5–7 are the user support (interaction) layers, with Transport acting as the bridge between the two groups.

51. **Name OSI layer that transmitted bit stream to frames.** *[NWPGCL Assistant Engineer (CSE) 2018 compact it 1213-1214 (ET: N/A)]*

    Answer: The `Data Link layer (Layer 2)` converts a bit stream into frames.

    - The Physical layer delivers an unstructured stream of bits. The Data Link layer performs `framing`: it groups those bits into meaningful units with a defined beginning and end, so the receiver knows where one frame stops and the next starts.
    - Each frame carries a header with the source and destination MAC addresses, and a trailer with the FCS (CRC) for error detection.

    ```
    Physical layer  : 1010110100101101110010101101 ...  (raw bits)
                                |
                         framing (Layer 2)
                                v
    Data Link layer : | Preamble | Dest MAC | Src MAC | Type | Data | FCS |
    ```

    - Framing methods include character count, byte stuffing with flag bytes, and bit stuffing (inserting a 0 after five consecutive 1s, as HDLC does).
    - Other Data Link functions: physical addressing, error detection, flow control and media access control.

52. **Explain: ISO, OSI and TCP/IP model with figure.** *[ICT Ministry Assistant Programmer 2017 compact it 1241-1242 (ET: N/A)]*

    Answer:

    ISO
    - ISO (International Organization for Standardization) is the worldwide standards body founded in 1947 and based in Geneva. It publishes standards across every industry.
    - In networking, ISO is the organisation that created the OSI model in 1984. A common exam point: ISO is the body, OSI is the model — they are not the same thing.

    OSI model — 7 layers
    ```
    +---------------------------------------------------+
    | 7  Application   - HTTP, FTP, SMTP, DNS   | Data   |
    +---------------------------------------------------+
    | 6  Presentation  - TLS, JPEG, ASCII       | Data   |
    +---------------------------------------------------+
    | 5  Session       - NetBIOS, RPC           | Data   |
    +---------------------------------------------------+
    | 4  Transport     - TCP, UDP               | Segment|
    +---------------------------------------------------+
    | 3  Network       - IP, ICMP, OSPF         | Packet |
    +---------------------------------------------------+
    | 2  Data Link     - Ethernet, PPP, ARP     | Frame  |
    +---------------------------------------------------+
    | 1  Physical      - cable, fibre, radio    | Bits   |
    +---------------------------------------------------+
    ```
    - It is a theoretical reference model: it says what each layer must do, not which protocol does it.

    TCP/IP model — 4 layers
    ```
    +---------------------------------------------------+
    |  Application    HTTP HTTPS FTP SMTP DNS DHCP SSH  |
    +---------------------------------------------------+
    |  Transport      TCP        |        UDP           |
    +---------------------------------------------------+
    |  Internet       IP  ICMP  ARP  IGMP  OSPF  BGP    |
    +---------------------------------------------------+
    |  Network Access Ethernet  Wi-Fi  PPP  Frame Relay |
    +---------------------------------------------------+
    ```
    - It is the practical model the internet runs on, built by the US DoD.

    Mapping and comparison

    | OSI | TCP/IP |
    |---|---|
    | Application + Presentation + Session | Application |
    | Transport | Transport |
    | Network | Internet |
    | Data Link + Physical | Network Access |

    | Point | OSI | TCP/IP |
    |---|---|---|
    | Layers | 7 | 4 |
    | Made by | ISO | US DoD |
    | Nature | Theoretical | Practical |
    | Protocols | None defined | TCP, IP, HTTP defined |
    | Design order | Model first | Protocols first |
    | In use | Reference only | The whole internet |

## Networking Fundamentals & Terminology (32)

1. **Define Computer Network. Describe different types of Computer Networks.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

   Answer:

   Definition
   - A computer network is a collection of two or more computing devices connected by a communication medium so that they can share data, hardware and software resources.
   - Components: hosts (PC, server, phone), transmission media (cable, fibre, radio), devices (switch, router, access point), protocols (TCP/IP) and network software.

   Types by geographical area

   | Type | Coverage | Speed | Owned by | Example |
   |---|---|---|---|---|
   | PAN (Personal Area Network) | A few metres around one person | Low | Individual | Bluetooth headset, smartwatch |
   | LAN (Local Area Network) | One room, building or campus | Very high (1–100 Gbps) | Private | Office or school network |
   | CAN (Campus Area Network) | Several buildings in one campus | High | Private | A university network |
   | MAN (Metropolitan Area Network) | One city, up to about 50 km | Medium | Private or public | Cable TV network, city fibre ring |
   | WAN (Wide Area Network) | Country or continent | Lower | Usually leased from carriers | The internet, a bank's branch network |

   Types by other criteria
   - By architecture: client–server (a central server provides services, easy to manage and secure) and peer-to-peer (every machine is both client and server, cheap but hard to secure).
   - By access: intranet (private, internal only), extranet (partly opened to partners and suppliers) and internet (public and global).
   - By medium: wired (UTP, coaxial, fibre) and wireless (Wi-Fi, Bluetooth, cellular, satellite).
   - Specialised: SAN (Storage Area Network) for block storage, VPN (a secure tunnel across a public network), and WLAN (a wireless LAN).

2. **(ক) IP address এবং MAC Address- এর মাঝে তুলনা করুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer: (Answered in English, as required for IT topics.)

   | Point | IP address | MAC address |
   |---|---|---|
   | Full form | Internet Protocol address | Media Access Control address |
   | OSI layer | Network layer (Layer 3) | Data Link layer (Layer 2) |
   | Size | 32 bits (IPv4), 128 bits (IPv6) | 48 bits |
   | Notation | Dotted decimal — 192.168.1.10 | Hexadecimal — 00:1A:2B:3C:4D:5E |
   | Assigned by | Administrator or DHCP server | Manufacturer, burned into the NIC |
   | Changes | Changes when the device moves to another network | Fixed for the card (can be spoofed in software) |
   | Scope | End to end, across the whole internet | Only within one local network segment |
   | Type | Logical address | Physical address |
   | Structure | Network portion + host portion | OUI (24 bits) + serial (24 bits) |
   | Used by | Routers, for path selection | Switches, for frame forwarding |
   | Found by | DNS (name to IP) | ARP (IP to MAC) |
   | Uniqueness | Unique within its network; private ranges are reused | Globally unique when universally administered |

   - They work together: IP finds the destination network anywhere on earth, and inside each network the MAC address delivers the frame to the right machine. The IP header stays the same end to end, while the MAC header is rewritten at every hop.

3. **(ক) সংজ্ঞা লিখুন: (i) Propagation delay, (ii) Transmission delay.** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer: (Answered in English, as required for IT topics.)

   (i) Propagation delay
   - The time a single bit takes to travel from the sender to the receiver across the physical medium.
   ```
   Propagation delay = Distance / Propagation speed
   ```
   - Propagation speed is about 2 × 10^8 m/s in copper and fibre, and 3 × 10^8 m/s in free space.
   - It depends only on distance and medium — never on packet size or bandwidth.
   - Example: a 2000 km link at 2 × 10^8 m/s gives 2,000,000 / 200,000,000 = 10 ms.

   (ii) Transmission delay
   - The time needed to push all the bits of a packet onto the link.
   ```
   Transmission delay = Packet size (bits) / Bandwidth (bps)
   ```
   - It depends only on packet size and link bandwidth — never on distance.
   - Example: a 1000-byte (8000-bit) packet on a 1 Mbps link takes 8000 / 1,000,000 = 8 ms.

   Difference at a glance

   | Point | Propagation delay | Transmission delay |
   |---|---|---|
   | Depends on | Distance and medium | Packet size and bandwidth |
   | Formula | Distance / Speed | Size / Bandwidth |
   | Reduced by | Shorter path | Higher bandwidth or smaller packets |

   - The other two delays that make up total delay are queuing delay (waiting in the router buffer) and processing delay (header checking and route lookup).

4. **Write short note: Network, Protocol, link, gateway, Node.** *[BREB Assistant Programmer 18.02.2023 compact it 470 (ET: N/A)]*

   Answer:

   Network
   - Two or more devices connected by a communication medium so they can exchange data and share resources such as printers, files and internet access. Types by size: PAN, LAN, MAN, WAN.

   Protocol
   - An agreed set of rules for communication that both sides must follow. It defines syntax (field format and order), semantics (what each field means) and timing (when and how fast to send). Examples: TCP, IP, HTTP, SMTP.

   Link
   - The physical or logical path that directly connects two adjacent nodes. A physical link is the cable, fibre or radio channel; a logical link is the connection seen at Layer 2. Links can be point-to-point (two devices only) or multipoint (shared by many).

   Gateway
   - A device that joins two networks using different protocols or architectures, translating between them. It works at all seven layers when full protocol conversion is needed. The default gateway is the router a host sends traffic to when the destination is outside its own subnet. Every router is a kind of gateway, but a gateway may also translate protocols — for example an email gateway between SMTP and a proprietary mail system.

   Node
   - Any device attached to the network that can send, receive or forward data — a PC, server, printer, switch, router or IP camera. Each node needs a unique address to be identified. An endpoint node is a source or destination; an intermediate node forwards traffic.

5. **(b) Define following terms: (i) Bandwidth (ii) Latency (iii) MAC Address (iv) IP address** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 491 (ET: N/A)]*

   Answer:

   (i) Bandwidth
   - The maximum amount of data a link can carry per unit time, measured in bits per second (bps, Mbps, Gbps). It is the theoretical capacity, like the width of a pipe.
   - Throughput is the data rate actually achieved, which is always lower because of overheads, congestion and errors.

   (ii) Latency
   - The total time a packet takes to travel from source to destination, measured in milliseconds. It is the delay, not the capacity.
   - It has four components: propagation delay (distance ÷ speed), transmission delay (packet size ÷ bandwidth), queuing delay (waiting in router buffers) and processing delay (header checks and lookups).
   - RTT (Round Trip Time) is the time for a packet to go and its reply to come back — this is what ping reports.
   - High bandwidth does not mean low latency. A satellite link can offer 100 Mbps with 600 ms latency.

   (iii) MAC address
   - A 48-bit physical address burned into the network card by the manufacturer, written as 12 hexadecimal digits, for example 00:1A:2B:3C:4D:5E.
   - The first 24 bits are the OUI identifying the vendor; the last 24 bits are the card's serial number.
   - It works at Layer 2 and is used only inside one local network segment. The broadcast MAC is FF:FF:FF:FF:FF:FF.

   (iv) IP address
   - A 32-bit (IPv4) logical address assigned to a device so that it can be identified and located across networks, written in dotted decimal as 192.168.1.10. IPv6 uses 128 bits.
   - It has a network portion and a host portion, separated by the subnet mask.
   - It works at Layer 3 and is used by routers to choose a path. It may be static or DHCP-assigned, public or private.

6. **Define networking and Internetworking. What are the different types of network? Explain in details.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 672 (ET: N/A)]*

   Answer:

   Networking
   - Networking is the practice of connecting computing devices together so they can exchange data and share resources. It covers the media, devices, protocols and configuration needed to make that happen.

   Internetworking
   - Internetworking is connecting two or more separate, and possibly different, networks so they behave as one large network. It is done with routers and gateways, using a common protocol suite — TCP/IP.
   - The internet is the largest example: millions of independent networks joined together.
   - Three forms: extranet (limited external access), intranet (internal only) and internet (global and public).

   Types of network

   | Type | Range | Description |
   |---|---|---|
   | PAN | 1–10 m | Around a single person — Bluetooth earphones, smartwatch, personal hotspot |
   | LAN | Up to a few km | One building or campus. Privately owned, very high speed (1–100 Gbps), low delay, low error rate. Built with switches and Ethernet or Wi-Fi |
   | CAN | A campus | Several nearby buildings connected by fibre, owned by one organisation |
   | MAN | A city, up to ~50 km | Joins several LANs across a city. Medium speed, may be public or private. Examples: cable TV networks, city-wide fibre rings, WiMAX |
   | WAN | Country or continent | Connects LANs and MANs over long distances using leased lines, MPLS or satellite. Lower speed, higher delay, usually owned by carriers. The internet is the largest WAN |

   Other classifications
   - By architecture: client–server (central control, easier security and backup) and peer-to-peer (no central server, cheap, harder to manage).
   - By connection: wired (UTP, coaxial, fibre) and wireless (Wi-Fi, cellular, satellite).
   - Special purpose: SAN for storage, VPN for secure tunnels over public links, WLAN for wireless LANs.

7. **Write short note: (i) web server (ii) ISP (iii) Router (iv) Search Engine** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 680 (ET: N/A)]*

   Answer:

   (i) Web server
   - A computer, plus the software running on it, that stores website files and delivers them to browsers over HTTP or HTTPS. The browser sends a request; the server returns the HTML, CSS, images or JSON.
   - Popular software: Apache, Nginx, Microsoft IIS, LiteSpeed. Default ports: 80 for HTTP and 443 for HTTPS.
   - A static server returns stored files; a dynamic server runs PHP, Python or Node.js and queries a database to build the page.

   (ii) ISP (Internet Service Provider)
   - A company that sells internet access to homes and organisations, providing the connection, a public IP address and often email, hosting and DNS.
   - Tiers: Tier 1 providers own global backbones and peer with each other free of charge; Tier 2 buy transit and also peer; Tier 3 sell to end users.
   - Access technologies: fibre (FTTH), DSL, cable, mobile broadband and satellite. Bangladeshi examples include BTCL and the licensed private ISPs.

   (iii) Router
   - A Layer 3 device that connects different networks and forwards packets between them using the destination IP address and its routing table.
   - Functions: path selection (longest prefix match), NAT, DHCP service, firewall and ACL filtering, and separating broadcast domains.
   - Routes are learned statically or dynamically through RIP, OSPF, EIGRP or BGP.

   (iv) Search engine
   - A system that crawls web pages, indexes their content, and returns ranked results for a user's query. Examples: Google, Bing, DuckDuckGo.
   - Three stages: crawling (spiders follow links to fetch pages), indexing (words are stored in an inverted index), and ranking (algorithms such as PageRank plus hundreds of other signals order the results).

8. **What is Interface protocol?** *[BARC Data Entry Officer 10.09.2022 compact it 703 (ET: N/A)]*

   Answer: An interface protocol is the agreed set of rules that governs communication across the boundary between two entities — either between two adjacent layers of a protocol stack on the same machine, or between two different networks or systems.

   Two senses of the term
   - Between layers – each OSI layer offers a service to the layer above through a defined Service Access Point. The rules for that hand-over are the interface protocol. It is why a layer can be replaced without disturbing its neighbours.
   - Between networks or devices – a protocol that lets two dissimilar systems talk, for example the interface between a router and a modem, or between a LAN and a WAN.

   Examples

   | Interface protocol | Where it works |
   |---|---|
   | NDIS, ODI | Between the NIC driver and the protocol stack |
   | Socket API | Between an application and the transport layer |
   | BGP | Between two autonomous systems (an exterior gateway protocol) |
   | PPP | Between a customer device and an ISP over a serial link |
   | USB, RS-232, HDMI | Between hardware devices |

   - Key idea: the interface defines what service is offered and how to ask for it, while the protocol between peer entities defines the message format on the wire. Keeping the two separate is what makes layered design work.

9. **(ক) সংজ্ঞা লিখুন: WWW, URL, HTTP, IP Address, Router.** *[Software Assistant Programmer 13.10.2022 compact it 708 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   WWW (World Wide Web)
   - A global system of interlinked hypertext documents and resources, accessed over the internet using HTTP/HTTPS and identified by URLs. Invented by Tim Berners-Lee at CERN in 1989.
   - It is a service that runs on the internet, not the internet itself — the internet is the underlying network, the web is one application on it.

   URL (Uniform Resource Locator)
   - The address of a resource on the web. Structure:
   ```
   https://www.example.com:443/folder/page.html?id=5#top
     |         |            |        |            |    |
   scheme   host          port     path        query  fragment
   ```

   HTTP (HyperText Transfer Protocol)
   - The application-layer protocol used to request and deliver web pages, running over TCP port 80 (HTTPS uses TLS on port 443).
   - It is stateless — each request is independent, which is why cookies and sessions exist. Methods: GET, POST, PUT, DELETE. Status codes: 200 OK, 301 Moved, 404 Not Found, 500 Server Error.

   IP address
   - A unique 32-bit (IPv4) logical address identifying a device on a network and allowing routers to locate it, written as 192.168.1.10. It has a network part and a host part, split by the subnet mask. IPv6 uses 128 bits.

   Router
   - A Layer 3 device that connects different networks and forwards packets between them based on the destination IP address and its routing table. It also performs NAT, DHCP and firewall functions, and separates broadcast domains.

10. **What is computer network?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

    Answer: A computer network is a group of two or more computing devices connected by a communication medium so that they can exchange data and share resources.

    Main components
    - Hosts / nodes – PCs, servers, printers, phones, IP cameras.
    - Transmission medium – UTP or coaxial cable, optical fibre, or wireless radio.
    - Networking devices – switch, router, access point, modem, firewall.
    - Protocols – the rules for communication, mainly the TCP/IP suite.
    - Network operating system and software – to manage users, resources and security.

    Purpose
    - Resource sharing – one printer, one internet connection and shared storage serve many users.
    - Communication – email, messaging, voice and video calls.
    - Centralised data and backup – files kept on a server, backed up in one place.
    - Cost saving – shared hardware and software licences.
    - Reliability – if one machine fails, data on the server is still available.

    Types by size: PAN, LAN, MAN, WAN. By architecture: client–server and peer-to-peer.

11. **What is SDN?** *[IDRA Assistant Network Administrator 2022 compact it 727 (ET: N/A)]*

    Answer: SDN (Software Defined Networking) is a network architecture that separates the control plane from the data plane and moves the control logic into a central software controller, so the whole network can be programmed and managed from one place.

    Traditional network vs SDN
    - In a traditional network every router and switch has its own control plane and data plane inside the box. Each device decides its own routes, and configuration must be done device by device.
    - In SDN the devices keep only the data plane (fast forwarding hardware). The control plane is lifted out into a controller that has a global view of the network.

    Architecture
    ```
    +-------------------------------------------------+
    | APPLICATION LAYER                               |
    |  routing app, firewall app, load balancer app   |
    +-------------------------------------------------+
            ^ Northbound API (REST)
    +-------------------------------------------------+
    | CONTROL LAYER — SDN Controller                  |
    |  OpenDaylight, ONOS, Ryu — global network view  |
    +-------------------------------------------------+
            ^ Southbound API (OpenFlow)
    +-------------------------------------------------+
    | INFRASTRUCTURE LAYER — data plane               |
    |  simple switches with flow tables               |
    +-------------------------------------------------+
    ```

    Key points
    - Control plane – decides where traffic should go, builds the flow rules.
    - Data plane – simply forwards frames according to the flow table it was given.
    - Southbound API – OpenFlow is the usual protocol between controller and switch.
    - Northbound API – REST APIs let applications and orchestration tools program the network.

    Advantages
    - Central management and a single global view of the whole network.
    - Programmable — network behaviour is changed by software, not by touching every device.
    - Vendor independence, since the switches become simpler and more interchangeable.
    - Fast automation, which is why cloud data centres and network virtualisation rely on it.

    Disadvantages
    - The controller is a single point of failure and a high-value target for attack, so it must be clustered and secured.
    - Adds new complexity and requires new skills.

12. **How to works networks?** *[IDRA Assistant Network Administrator 2022 compact it 727 (ET: N/A)]*

    Answer: A network works by breaking data into packets, addressing them, and passing them hop by hop until they reach the destination, where they are reassembled.

    Step by step
    - Data creation – an application produces data, for example a browser requesting a web page.
    - Encapsulation – the data goes down the protocol stack. Transport adds port numbers and sequence numbers (segment), Network adds source and destination IP addresses (packet), Data Link adds MAC addresses and a CRC (frame), and Physical converts it into signals (bits).
    - Addressing – the IP address identifies the destination host anywhere on the internet; the MAC address identifies the next device on the local link. ARP supplies the MAC for a known IP.
    - Local or remote decision – the sender ANDs its own IP and the destination IP with the subnet mask. If the network parts match, it sends directly; otherwise it sends to the default gateway.
    - Switching and routing – a switch forwards the frame using its MAC address table. A router strips the frame, reads the destination IP, looks up its routing table, and builds a new frame for the next hop. The IP header stays the same end to end; the MAC header is rewritten at every hop.
    - Delivery and decapsulation – at the destination each layer removes its own header, TCP reorders the segments and acknowledges them, and the data reaches the correct application through its port number.
    - Reliability – TCP retransmits anything lost, applies flow control with the sliding window, and applies congestion control so the network is not overloaded.

    ```
    PC ---- Switch ---- Router ---- Internet ---- Router ---- Switch ---- Server
       frame        frame      packet        packet       frame       frame
       (MAC rewritten at every router hop; IP addresses unchanged)
    ```

13. **(খ) Address গুলির সংক্ষিপ্ত বর্ণনা দিন। (i) Port Number (ii) IP অ্যাড্রেস (iii) MAC অ্যাড্রেস।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 775 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Three kinds of address are used together to deliver data.

    (i) Port number
    - A 16-bit number (0–65535) at the Transport layer that identifies which application process on a host should receive the data.
    - Ranges: 0–1023 well known (HTTP 80, HTTPS 443, SSH 22, DNS 53, SMTP 25), 1024–49151 registered, 49152–65535 dynamic or ephemeral, used by clients.
    - IP address + port number together form a socket, for example 192.168.1.10:443.

    (ii) IP address
    - A 32-bit logical address (IPv4) that identifies a host and its network, written in dotted decimal as 192.168.1.10. IPv6 uses 128 bits.
    - It has a network part and a host part, separated by the subnet mask, and it is used by routers to choose a path.
    - It may be static or assigned by DHCP, public or private, and it changes when the device moves to a different network.

    (iii) MAC address
    - A 48-bit physical address burned into the NIC by the manufacturer, written as 12 hex digits, for example 00:1A:2B:3C:4D:5E.
    - First 24 bits are the vendor OUI, last 24 bits are the card serial number. Broadcast MAC is FF:FF:FF:FF:FF:FF.
    - It works only inside one local segment, and switches use it to forward frames.

    How they work together
    ```
    MAC address  -> finds the correct machine on this link
    IP address   -> finds the correct host anywhere on the internet
    Port number  -> finds the correct program inside that host
    ```

14. **(i) নিচের MAC Address গুলো কোন ধরনের বের করুন। (a) 4C:23:10:4A:1A:2A (b) 45:24:56:2B:24:12 (c) FF:FF:FF:FF:FF:FF** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 788 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The type of a MAC address is decided by the two lowest bits of the FIRST octet.

    - I/G bit (least significant bit of octet 1): 0 = unicast, 1 = multicast.
    - U/L bit (next bit): 0 = universally administered (vendor assigned), 1 = locally administered.

    | Address | First octet in binary | I/G bit | Type |
    |---|---|---|---|
    | (a) 4C:23:10:4A:1A:2A | 4C = 0100 1100 | 0 | `Unicast`, universally administered (vendor assigned) |
    | (b) 45:24:56:2B:24:12 | 45 = 0100 0101 | 1 | `Multicast` |
    | (c) FF:FF:FF:FF:FF:FF | FF = 1111 1111 | 1 | `Broadcast` — all 48 bits are 1 |

    Notes
    - Unicast — one specific network card. Only that card processes the frame.
    - Multicast — a group of interested devices. Example: 01:00:5E:xx:xx:xx is the range used for IPv4 multicast.
    - Broadcast — every device on the segment. It is the special case where all bits are 1, and it is what ARP requests and DHCP Discover use.

15. **If you have a company of two branch in the same city and they are connected. Which connection is used between then? (a) LAN (b) MAN (c) WAN (d) NONE** *[BCC Assistant Programmer 12.02.2021 compact it 811 (ET: BUET)]*

    Answer: The correct option is `(b) MAN`.

    - Two branches in the same city are separated by more than a single building but less than a city's boundary, which is exactly the range a Metropolitan Area Network covers — typically 5 to 50 km.

    Why the others are wrong

    | Option | Coverage | Fit |
    |---|---|---|
    | LAN | One building or campus, up to about 1 km | Too small for two branches across a city |
    | `MAN` | One city, 5–50 km | `Correct` |
    | WAN | Country or continent, above 50 km | Too large for one city |

    - Typical MAN technologies: metro Ethernet, a city fibre ring, SONET/SDH, WiMAX, or a leased line from a local carrier.
    - Note: if the two branches were in different cities or countries the answer would be WAN, and today many such links are actually built as a VPN over the internet.

16. **Short Question: a) What are the protocol for connectionless and connection oriented? b) Why UTP cable are twisted? c) What are the main requirement of optical fiber splicing? d) Why use subnet mask? e) What the major difference between multicast and broadcast?** *[BPDB Assistant Engineer (CSE) 2021 compact it 816 (ET: BUET)]*

    Answer:

    (a) Connection-oriented and connectionless protocols
    - Connection-oriented: `TCP`. A connection is set up with the three-way handshake before any data moves; delivery is reliable, ordered and acknowledged, with flow and congestion control. Also SCTP, and at Layer 2, Frame Relay and ATM.
    - Connectionless: `UDP`. Data is sent with no handshake, no acknowledgement and no ordering — fast but unreliable. Also IP itself, ICMP and IPX.

    (b) Why UTP cables are twisted
    - Each pair is twisted so that the two wires pick up almost exactly the same external noise. Because the signal is sent as a difference between the two wires, the common noise cancels out at the receiver.
    - Twisting also reduces crosstalk between neighbouring pairs, since each pair has a different twist rate.
    - It cuts electromagnetic radiation out of the cable as well, so the cable interferes less with other equipment.
    - More twists per inch means better noise rejection, which is why Cat6 is twisted more tightly than Cat5e.

    (c) Main requirements of optical fibre splicing
    - Correct alignment of the two fibre cores, to within a fraction of a micrometre — misalignment is the biggest source of loss.
    - Clean, perpendicular end faces produced by a good cleaver, with no cracks or angle error.
    - Cleanliness — the fibre must be stripped and cleaned with alcohol, since dust causes permanent loss.
    - Matched fibres — same core diameter and type (single-mode with single-mode).
    - Low insertion loss and low back reflection: a fusion splice typically gives under 0.1 dB, a mechanical splice about 0.2–0.5 dB.
    - Mechanical protection afterwards: a heat-shrink splice sleeve and a splice tray, so the joint is not stressed.

    (d) Why a subnet mask is used
    - To separate the network portion from the host portion of an IP address, so a host can compute its network address by ANDing the two.
    - To decide whether a destination is local (send directly) or remote (send to the default gateway).
    - To make subnetting possible, which reduces broadcast traffic and separates departments.
    - To determine how many hosts a block can hold, 2^h − 2.
    - To let routers do longest-prefix-match forwarding.

    (e) Major difference between multicast and broadcast

    | Point | Multicast | Broadcast |
    |---|---|---|
    | Recipients | Only hosts that joined the group | Every host on the segment |
    | Efficiency | High — uninterested hosts are not disturbed | Low — every host must process the frame |
    | Address | 224.0.0.0–239.255.255.255 (Class D) | 255.255.255.255 or the subnet broadcast |
    | Routing | Can cross routers with multicast routing (PIM, IGMP) | Not forwarded by routers |
    | IPv6 | Supported and heavily used | Does not exist; replaced entirely by multicast |
    | Example | IPTV, video conferencing, OSPF hellos | ARP request, DHCP Discover |

17. **Name of the Following figure:** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 880 (ET: BUET)]*
   Broadcast
   Unicast
   Multicast

    Answer: The three figures show the three basic transmission modes.

    | Figure | Name | Meaning |
    |---|---|---|
    | One sender, one receiver | `Unicast` | One-to-one delivery |
    | One sender, all hosts on the segment | `Broadcast` | One-to-all delivery |
    | One sender, a selected group | `Multicast` | One-to-many delivery |

    ```
    UNICAST                BROADCAST              MULTICAST
      S                       S                      S
      |                    / | | \                 /   \
      v                   v  v v  v               v     v
      R                  R1 R2 R3 R4            R1      R3     (R2, R4 not in group)
    one-to-one            one-to-all             one-to-many
    ```

    Comparison

    | Point | Unicast | Broadcast | Multicast |
    |---|---|---|---|
    | Receivers | Exactly one | All on the segment | Only group members |
    | Address | Normal host IP | 255.255.255.255 or subnet broadcast | 224.0.0.0 – 239.255.255.255 |
    | Bandwidth | One copy per receiver — wasteful for many | One copy, but disturbs everyone | One copy per link — most efficient |
    | Crosses routers | Yes | No | Yes, with PIM and IGMP |
    | Example | Web browsing, email | ARP, DHCP Discover | IPTV, video conference, OSPF |

    - A fourth mode, anycast, sends to the nearest member of a group and is used by root DNS servers and CDNs.

18. **(i) Computer network কী? বিভিন্ন প্রকার Computer network সম্পর্কে আলোচনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 955-956 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    What is a computer network
    - A computer network is two or more computing devices connected by a communication medium so they can exchange data and share resources such as printers, files, applications and internet access.
    - It is built from hosts, transmission media, networking devices (switch, router, access point), protocols such as TCP/IP, and network software.

    Types of computer network

    | Type | Range | Speed | Ownership | Example |
    |---|---|---|---|---|
    | PAN | 1–10 m | Low | Personal | Bluetooth headset, smartwatch |
    | LAN | Up to ~1 km | Very high | Private | Office, school, home network |
    | CAN | A campus | High | Private | University network |
    | MAN | 5–50 km, one city | Medium | Private or public | Cable TV network, city fibre ring |
    | WAN | Country or continent | Lower | Leased from carriers | The internet, a bank's branch network |

    Discussion
    - LAN – covers a small area, uses Ethernet switches or Wi-Fi, offers 1–100 Gbps with very low delay and very low error rate, and is entirely owned and maintained by the organisation.
    - MAN – joins several LANs across a city using metro Ethernet, fibre rings or WiMAX. Speed and delay sit between LAN and WAN, and it may be run by a service provider.
    - WAN – spans long distances using leased lines, MPLS, satellite or the public internet. Bandwidth is lower and delay higher, and it is normally rented rather than owned.
    - Other classifications: client–server versus peer-to-peer by architecture; wired versus wireless by medium; intranet, extranet and internet by access; and special types such as SAN, WLAN and VPN.

19. **What is difference between MAC Address and IP Address?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1018-1019 (ET: N/A)]*

    Answer:

    | Point | MAC address | IP address |
    |---|---|---|
    | Layer | Data Link (Layer 2) | Network (Layer 3) |
    | Type | Physical / hardware address | Logical address |
    | Size | 48 bits | 32 bits (IPv4), 128 bits (IPv6) |
    | Format | Hexadecimal, 00:1A:2B:3C:4D:5E | Dotted decimal, 192.168.1.10 |
    | Assigned by | Manufacturer, burned into the NIC | Administrator or DHCP |
    | Changes | Fixed for the card | Changes with the network |
    | Scope | One local segment only | End to end, worldwide |
    | Structure | OUI (24 bits) + serial (24 bits) | Network portion + host portion |
    | Used by | Switches, to forward frames | Routers, to choose a path |
    | Resolution | ARP maps IP to MAC | DNS maps a name to an IP |
    | Broadcast form | FF:FF:FF:FF:FF:FF | 255.255.255.255 |

    - Analogy: the IP address is the postal address that gets a letter to the right city and street; the MAC address is the name of the person in the house who finally receives it.
    - In a packet's journey the IP addresses never change, but the MAC addresses are rewritten at every router hop.

20. **(b) List the factors that affect the performance of a network.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1027 (ET: N/A)]*

    Answer: The main factors that affect network performance.

    Bandwidth and capacity
    - Link bandwidth sets the ceiling on throughput. A link running near capacity queues packets and adds delay.

    Latency (delay)
    - Made up of propagation delay (distance ÷ speed), transmission delay (packet size ÷ bandwidth), queuing delay (waiting in buffers) and processing delay (header checks and route lookup).

    Jitter
    - Variation in latency between packets. Voice and video are very sensitive to it, even when average latency is acceptable.

    Congestion and traffic load
    - Too many packets for the available capacity causes queuing, buffer overflow and packet loss, which triggers TCP retransmission and reduces throughput further.

    Packet loss and error rate
    - Caused by noise, faulty cables, collisions or full buffers. Every lost packet must be retransmitted, so a small loss rate can cut TCP throughput sharply.

    Number of users and devices
    - More hosts mean more traffic and more broadcast overhead in a single broadcast domain.

    Transmission medium
    - Fibre gives the highest bandwidth and lowest error rate; UTP is limited to 100 m; wireless suffers interference, distance loss and shared airtime.

    Hardware and topology
    - Router and switch CPU, memory and buffer size, the number of hops, and whether links are full duplex or half duplex all matter. A hub creates collisions; a switch does not.

    Protocol and configuration
    - TCP window size, MTU and fragmentation, routing protocol convergence time, and the choice of TCP or UDP.

    Security and other overheads
    - Encryption, deep packet inspection and firewall rules consume CPU and add delay. Malware and broadcast storms consume bandwidth.

    - Measures used: throughput (actual data rate), latency, jitter, packet loss and availability. QoS is the usual tool for protecting critical traffic when capacity is limited.

21. **(a) Write a brief history of the internet. How to access to the internet?** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1028-1029 (ET: N/A)]*

    Answer:

    Brief history of the internet
    - 1969 – ARPANET, funded by the US Department of Defense, connects four universities. The first packet-switched network.
    - 1971 – Ray Tomlinson sends the first email and chooses the @ symbol.
    - 1974 – Vint Cerf and Bob Kahn design TCP/IP, which lets different networks interconnect.
    - 1983 – ARPANET switches to TCP/IP. This date is usually called the birth of the internet.
    - 1984 – DNS is introduced, replacing a single hosts file with a distributed naming system.
    - 1989–91 – Tim Berners-Lee at CERN invents the World Wide Web: HTML, HTTP and the first browser.
    - 1993 – Mosaic, the first graphical browser, makes the web popular.
    - 1995 onward – commercial ISPs, search engines, e-commerce.
    - 2000s – broadband, Wi-Fi, social media, mobile internet.
    - 2010s–today – 4G and 5G, cloud computing, IoT, and the gradual move to IPv6.
    - In Bangladesh, full internet connectivity began in 1996, and submarine cable connectivity with SEA-ME-WE 4 in 2006.

    How to access the internet

    | Method | Description | Typical speed |
    |---|---|---|
    | Fibre (FTTH) | Optical fibre to the home; dedicated bandwidth | 100 Mbps – 1 Gbps |
    | DSL / ADSL | Data over the existing telephone line | 1 – 100 Mbps |
    | Cable (HFC) | Fibre to the neighbourhood, coaxial to the house; shared | 25 Mbps – 1 Gbps |
    | Mobile broadband | 3G, 4G, 5G through a SIM or dongle | 10 Mbps – 1 Gbps |
    | Wi-Fi | Wireless access to a local router, which has the real link | Depends on the uplink |
    | Satellite | For remote areas; high latency in geostationary systems | 10 – 200 Mbps |
    | Leased line | A dedicated symmetrical link for businesses, with an SLA | 2 Mbps – 10 Gbps |

    - Requirements in every case: a device, a NIC or modem, an ISP subscription, an IP address, and TCP/IP configured with a gateway and DNS server.

22. **(b) Define computer network. Sate some merits and demerits of a computer network.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1029 (ET: N/A)]*

    Answer:

    Definition
    - A computer network is a group of two or more computing devices connected by a communication medium so they can exchange data and share resources such as printers, storage, applications and internet access.

    Merits
    - Resource sharing – one printer, one internet link and shared storage serve many users, cutting cost.
    - Communication – email, messaging, voice and video calls, and collaborative work on shared documents.
    - Centralised data – files kept on a server are easier to back up, secure and keep consistent.
    - Cost saving – shared hardware and volume software licences are cheaper than per-machine copies.
    - Central administration – users, permissions, updates and antivirus are managed from one console.
    - Scalability – new users and devices are added without redesigning everything.
    - Reliability – if one workstation fails, the data on the server is still available; redundant links keep the network up.

    Demerits
    - Security risk – one compromised machine can expose the whole network to malware, ransomware or data theft.
    - Single point of failure – if the server, main switch or internet link fails, many users stop working at once.
    - Setup and maintenance cost – cabling, switches, routers, servers, software and skilled staff are expensive.
    - Needs skilled administrators – configuration, monitoring and troubleshooting require trained people.
    - Virus and malware spread quickly across connected machines.
    - Loss of privacy – administrators can monitor traffic and stored files.
    - Congestion – heavy use slows everyone down, and broadcast storms can bring a segment to a halt.
    - Distraction and misuse – uncontrolled internet access reduces productivity, which is why policy and filtering are needed.

23. **b) Two IP address map to same Ethernet address. Will both of them receive packets?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033 (ET: BUET)]*

    Answer: `Yes, both will receive packets.`

    Why
    - A network interface card accepts any frame whose destination MAC address matches its own (or is a broadcast or a joined multicast address). The card knows nothing about IP addresses.
    - So if two IP addresses are configured on the same interface — or resolve through ARP to the same MAC — every frame for either address arrives at that card.
    - The card passes the frame up to the IP layer, which reads the destination IP in the packet header and delivers it to the right socket or process. This is demultiplexing.

    Where this happens in practice
    - IP aliasing / multihoming – one server holds several IP addresses on one NIC, for example to host several websites with separate certificates.
    - Virtual machines and containers bridged to one physical NIC.
    - VRRP or HSRP – a virtual IP shared by routers maps to a virtual MAC.
    - Loopback or secondary addresses configured for testing.

    Caution
    - The same situation arises maliciously in ARP spoofing, where the attacker answers ARP requests for several IP addresses with its own MAC in order to intercept traffic. Dynamic ARP Inspection is the defence.
    - So the mapping is legitimate when configured deliberately, and a red flag when it appears unexpectedly in the ARP table.

24. **Write short note: Node, Backbone, Router and Gateway.** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1049 (ET: BUET)]*

    Answer:

    Node
    - Any device attached to a network that can send, receive or forward data — a PC, server, printer, switch, router, phone or IP camera.
    - Each node needs a unique address (MAC at Layer 2, IP at Layer 3) so it can be identified.
    - An end node is a source or destination; an intermediate node forwards traffic on behalf of others.

    Backbone
    - The high-capacity central part of a network that carries aggregated traffic between smaller segments or sites.
    - It uses the fastest links available — typically fibre at 10, 40 or 100 Gbps — and is built with redundancy, because a backbone failure affects everyone.
    - Examples: the fibre riser joining every floor switch in a building, a campus core, or the international submarine cables and Tier 1 carriers that form the internet backbone.

    Router
    - A Layer 3 device that connects different networks and forwards packets between them using the destination IP address and its routing table (longest prefix match).
    - It also performs NAT, DHCP, ACL filtering and fragmentation, decrements the TTL, and separates broadcast domains — a broadcast does not pass through a router.
    - Routes are learned statically or through RIP, OSPF, EIGRP or BGP.

    Gateway
    - A device that joins two networks that use different protocols or architectures, translating between them. It may operate right up to Layer 7 when full protocol conversion is required.
    - The default gateway is simply the router a host sends traffic to when the destination lies outside its own subnet.
    - Difference from a router: every router is a gateway, but a gateway may additionally translate protocols — for example a VoIP gateway between an IP network and the PSTN, or an email gateway between SMTP and a proprietary system.

25. **(খ) Public and Private Network-এর মধ্যে পার্থক্য লিখুন? IP address কী?** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1073 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    Public network vs private network

    | Point | Public network | Private network |
    |---|---|---|
    | Access | Open to anyone | Restricted to authorised users of one organisation |
    | IP addresses | Public, globally unique | RFC 1918 private addresses |
    | Ownership | Service providers, shared infrastructure | Owned and controlled by the organisation |
    | Security | Low — traffic passes through untrusted networks | High — controlled by internal policy and firewalls |
    | Cost | Cheap or free to use | Expensive to build and maintain |
    | Control | None over routing or quality | Full control over addressing, QoS and policy |
    | Performance | Variable, no guarantee | Predictable, can be engineered |
    | Examples | The internet, public Wi-Fi in a café or airport | Office LAN, bank branch network, VPN, intranet |

    - The two are usually combined: a private LAN reaches the public internet through a router doing NAT, and a VPN builds a private, encrypted tunnel across the public network.

    What is an IP address
    - A unique logical address assigned to each device on a TCP/IP network so it can be identified and located. IPv4 is 32 bits, written as four decimal octets (192.168.1.10); IPv6 is 128 bits, written in hexadecimal.
    - It has two parts, a network portion and a host portion, separated by the subnet mask. Routers use the network portion to select a path.
    - It can be static or DHCP-assigned, and public or private.

26. **What is MAC address?** *[BREB Assistant Hardware & Network Engineer 2019 compact it 1124 (ET: BREB)]*

    Answer: A MAC (Media Access Control) address is a 48-bit physical address permanently assigned to a network interface card by its manufacturer. It identifies the device uniquely inside a local network.

    Format
    - 12 hexadecimal digits, written as `00:1A:2B:3C:4D:5E` or 00-1A-2B-3C-4D-5E.
    - First 24 bits (00:1A:2B) — the OUI, which identifies the vendor and is allocated by the IEEE.
    - Last 24 bits (3C:4D:5E) — the serial number chosen by that vendor.

    Key properties
    - Works at the Data Link layer (Layer 2) and is used by switches to forward frames.
    - Valid only within one local segment; it is never carried across a router, and is rewritten at every hop.
    - Also called the physical address, hardware address or burned-in address (BIA). It can be changed in software (MAC spoofing), which is why it is not a security control on its own.
    - Types: unicast (I/G bit = 0), multicast (I/G bit = 1), and broadcast, which is FF:FF:FF:FF:FF:FF.
    - ARP is the protocol that finds the MAC address belonging to a known IP address. `ipconfig /all` or `ip link` displays it.

27. **(a) To setup a network among the computers of your office which type of network and network features will you prefer? Justify your choice?** *[BPSC Assistant Programmer (ICT) 2019 compact it 1140-1141 (ET: N/A)]*

    Answer: For a typical office, the right choice is a `wired LAN in a star topology, using a client–server architecture, with Wi-Fi added for mobile devices`.

    Recommended design

    | Item | Choice | Justification |
    |---|---|---|
    | Network type | LAN | The office is one building, which is exactly LAN range |
    | Topology | Star (switch at the centre) | One cable failure affects only one PC; easy to add users; easy to troubleshoot |
    | Architecture | Client–server | Central file storage, central backup, central user accounts and permissions |
    | Medium | Cat6 UTP for desks, fibre between floors | Cat6 supports 1 Gbps to 100 m at low cost; fibre for long or noisy runs |
    | Devices | Managed switch, router, firewall, access points | A managed switch gives VLANs, QoS and port security |
    | Addressing | Private IPv4 with DHCP, plus static IPs for servers and printers | No manual configuration, no address conflicts, servers stay reachable |
    | Segmentation | VLANs per department | Smaller broadcast domains, department-level security |
    | Wireless | WPA3 Wi-Fi with a separate guest SSID | Visitors never touch the internal network |

    Features to insist on
    - Security – firewall, antivirus, WPA3, strong passwords, role-based file permissions, and a separate guest network.
    - Reliability – UPS on the switch and server, redundant uplinks, and scheduled backups.
    - Scalability – spare switch ports and structured cabling so new staff can be added easily.
    - Manageability – a managed switch with monitoring and logs, and centralised user administration.
    - Performance – gigabit to the desk, fibre backbone, QoS for voice and video.

    Why not the alternatives
    - Peer-to-peer is cheaper but has no central security, no central backup and becomes unmanageable beyond about ten machines.
    - A Wi-Fi-only office is easy to install but has shared bandwidth, more interference and a wider attack surface, so it suits laptops and phones rather than fixed workstations.
    - A bus or ring topology is obsolete: one break in a bus takes down the whole network.

28. **(b) Suppose, your office needs to setup a network which can uses for internet purpose only? What will be your steps to setup that network in terms of:** *[BPSC Assistant Programmer (ICT) 2019 compact it 1144 (ET: N/A)]*

    Answer: Steps to set up an internet-only office network.

    Step 1 – Requirement analysis
    - Count the users and devices, estimate bandwidth per user, and identify where the desks and access points will be.

    Step 2 – Choose an ISP and connection
    - Compare fibre, broadband and leased line on speed, contention ratio, SLA and price. For an office, a fibre or leased line with a fixed public IP is preferable.

    Step 3 – Hardware
    - Router with firewall, managed switch (with enough ports plus spares), Wi-Fi access points, structured Cat6 cabling with patch panel and rack, and a UPS.

    Step 4 – IP addressing
    - Use a private range, for example 192.168.1.0/24, with DHCP for user PCs and static addresses for the router, printers and access points. Set the gateway and DNS servers.

    Step 5 – Physical installation
    - Run the cables in trunking, terminate at the patch panel, mount the rack, place the access points for good coverage, and label everything.

    Step 6 – Configuration
    - Configure the router's WAN side with the ISP details, enable NAT and DHCP, set up Wi-Fi with WPA3 and a separate guest SSID, and apply firewall rules that block unwanted inbound traffic.

    Step 7 – Security
    - Change all default passwords, enable the firewall, install antivirus, apply content filtering if required, keep firmware updated, and separate the guest network with a VLAN.

    Step 8 – Testing
    - Check connectivity with ping, verify DNS resolution, run a speed test from several desks, and confirm Wi-Fi coverage in every room.

    Step 9 – Documentation and handover
    - Record the IP plan, device passwords, cable labelling and ISP contacts; train the staff; and set a maintenance and monitoring routine.

    - Approximate cost heads: ISP monthly charge, router, switch, access points, cabling and installation labour, UPS, and ongoing maintenance.

29. **What is an access network? Briefly describe the available access network.** *[BTRC Assistant Director (Technical) 2019 compact it 1147 (ET: N/A)]*

    Answer:

    What is an access network
    - The access network is the part of the network that connects an end user to the first router of the service provider — the "last mile" between the subscriber and the ISP's edge.
    - It sits between the customer premises equipment and the provider's core network, and it is usually the slowest and most expensive part to build, because it must reach every individual home.

    Available access networks

    | Technology | Medium | Typical speed | Notes |
    |---|---|---|---|
    | Dial-up | Telephone line, modem | Up to 56 kbps | Obsolete; occupies the phone line |
    | DSL / ADSL / VDSL | Existing copper telephone pair | 1 – 100 Mbps | Dedicated bandwidth; speed falls with distance from the exchange |
    | Cable (HFC) | Fibre to the neighbourhood, coaxial to the home | 25 Mbps – 1 Gbps | Bandwidth is shared with neighbours, so evening speed drops |
    | FTTH / FTTx | Optical fibre to the building | 100 Mbps – 1 Gbps or more | Fastest and most reliable; dedicated bandwidth; higher installation cost |
    | Ethernet / leased line | Fibre or copper, dedicated | 10 Mbps – 10 Gbps | Symmetrical with an SLA; used by businesses |
    | Mobile broadband | 3G, 4G, 5G radio | 10 Mbps – 1 Gbps | Mobile; shared cell capacity; data caps common |
    | Fixed wireless / WiMAX | Point-to-multipoint radio | 10 – 100 Mbps | Useful where cable cannot reach; weather sensitive |
    | Satellite | Geostationary or LEO | 10 – 200 Mbps | Reaches remote areas; GEO has very high latency, LEO much less |

    - Classification: residential access (DSL, cable, FTTH, mobile), enterprise access (Ethernet and leased lines) and wireless access (Wi-Fi, cellular, satellite).
    - Wi-Fi is strictly a LAN technology, not an access network — it connects the user to a router that itself uses one of the technologies above.

30. **Explain the terms Domains, Bandwidth, Broadcast and Multicast.** *[Multiple Ministry Assistant Programmer 2017 compact it 1232 (ET: N/A)]*

    Answer:

    Domain
    - In DNS, a domain is a named branch of the internet naming hierarchy, such as `example.com`. It is read right to left: root, then top-level domain (.com, .org, .bd), then second-level domain, then sub-domain.
    - In Windows networking, a domain is a group of computers and users administered centrally by a domain controller with Active Directory.
    - Two related terms in switching: a collision domain is the set of devices that can collide with each other (each switch port is its own), and a broadcast domain is the set of devices reached by a broadcast (each router interface bounds one, and VLANs subdivide it).

    Bandwidth
    - The maximum data-carrying capacity of a link, measured in bits per second — bps, Mbps, Gbps. In analogue terms it is the range of frequencies a channel can carry, in hertz.
    - It is the theoretical ceiling; the rate actually achieved is called throughput, and it is always lower because of protocol overhead, congestion and errors.

    Broadcast
    - Sending one message to every device on a network segment, a one-to-all transmission.
    - Address: 255.255.255.255 (limited) or the subnet broadcast such as 192.168.1.255 (directed); at Layer 2 it is FF:FF:FF:FF:FF:FF.
    - Routers do not forward broadcasts. Every host must process the frame, so heavy broadcast traffic wastes CPU and bandwidth, and a broadcast storm can bring a segment down.
    - Examples: ARP requests, DHCP Discover. IPv6 has removed broadcast entirely in favour of multicast.

    Multicast
    - Sending one message to a selected group of interested hosts, a one-to-many transmission.
    - Address range: 224.0.0.0 – 239.255.255.255 (Class D). Hosts join a group using IGMP, and routers forward group traffic using PIM.
    - It is efficient: the sender transmits one copy, and the network duplicates it only where paths diverge. Uninterested hosts are never disturbed.
    - Examples: IPTV, video conferencing, stock tickers, and routing protocol hellos (OSPF uses 224.0.0.5).

31. **Differentiate between Intranet and Extranet.** *[Bangladesh Bank Assistant Maintenance Engineer 2016 compact it 1264 (ET: N/A)]*

    Answer:

    | Point | Intranet | Extranet |
    |---|---|---|
    | Users | Employees of one organisation only | Employees plus selected outsiders — partners, suppliers, customers |
    | Access | Strictly internal | Controlled external access over the internet or a VPN |
    | Scope | Inside the organisation's own network | Extends the intranet to trusted third parties |
    | Security need | High | Higher — an outside-facing boundary must be defended |
    | Authentication | Internal accounts, often single sign-on | Stronger: VPN, MFA, per-partner accounts and separate portals |
    | Purpose | Internal communication, HR portal, policies, internal apps | B2B collaboration, supply chain, order tracking, shared project data |
    | Cost | Lower | Higher, because of the additional security and management |
    | Example | A bank's internal HR and circular portal | A supplier portal where vendors submit invoices and track payments |

    Relationship between the three terms
    ```
    INTERNET   - public, open to everyone
       |
    EXTRANET   - private network partially opened to trusted outsiders
       |
    INTRANET   - fully private, internal users only
    ```
    - An extranet is essentially an intranet with a controlled door in the wall. It is typically built with a DMZ, a reverse proxy or a VPN, and access is limited to exactly the resources a given partner needs.

32. **a) Briefly discuss what a computer network means.** *[Ministry of Finance Programmer 2013 compact it 1272 (ET: N/A)]*

    Answer: A computer network means two or more computing devices linked by a communication medium so that they can exchange data and share resources.

    The essential idea
    - Devices are given unique addresses, data is broken into packets, and agreed rules (protocols) govern how those packets are addressed, sent, checked and reassembled.

    Components
    - Hosts – PCs, servers, printers, phones and other endpoints.
    - Medium – UTP or coaxial cable, optical fibre, or wireless radio.
    - Devices – switch, router, access point, modem, firewall.
    - Protocols – the TCP/IP suite, which defines format, meaning and timing.
    - Software – network operating system, drivers and management tools.

    Why organisations build them
    - Resource sharing – one printer, one internet link and shared storage serve everyone.
    - Communication – email, messaging, voice and video.
    - Centralised data and backup, which improves consistency and recovery.
    - Cost saving through shared hardware and licences.
    - Central administration of users, permissions and security.
    - Reliability and scalability as the organisation grows.

    Types by size: PAN, LAN, MAN and WAN. By architecture: client–server and peer-to-peer.

## Application Layer Protocols & Troubleshooting (DNS, DHCP, HTTPS) (22)

1. [http://BSCPL.bd.gov](http://BSCPL.bd.gov) is connected to multiple international ISPs, and users can successfully access other websites, but they are unable to access the [http://BSCPL.bd.gov](http://BSCPL.bd.gov) website. The network uses essential services such as DNS, DHCP, and HTTPS, each performing different functions in the communication process. Identify the roles of DNS, DHCP, and HTTPS, determine which component or configuration could be responsible for this site-specific failure, and explain the possible causes and troubleshooting steps. [BSCCPL AME 21-08-2026 (BUET)]

   Answer: Other sites work but only this one site fails. That single fact narrows the problem sharply: the internet connection, DHCP and the general routing are all fine, so the fault lies in something specific to BSCPL.bd.gov.

   Roles of the three services

   | Service | Role in the communication | Port |
   |---|---|---|
   | DNS | Translates the name BSCPL.bd.gov into an IP address. Without it the browser has no address to connect to | UDP/TCP 53 |
   | DHCP | Automatically gives each client an IP address, subnet mask, default gateway and DNS server address | UDP 67 (server), 68 (client) |
   | HTTPS | Carries the actual web request over TCP inside a TLS-encrypted channel, and authenticates the server through its certificate | TCP 443 |

   Which component is responsible
   - `DNS is the most likely cause`, because a failure limited to one domain while every other site works is the classic signature of a name-resolution or a certificate problem for that domain. DHCP can be ruled out immediately — if DHCP were broken, nothing at all would work.

   Possible causes, grouped

   DNS related
   - The authoritative DNS server for bd.gov is down or unreachable.
   - The A record for BSCPL.bd.gov is missing, wrong or was mistyped after a change.
   - The DNS zone or the domain registration has expired.
   - Stale or poisoned entries in the local resolver cache still point to an old, dead IP.
   - A split-horizon DNS view returns an internal address that outside users cannot reach.
   - The TTL was long, so an old record is still cached widely after a genuine IP change.

   HTTPS / certificate related
   - The TLS certificate has expired, has the wrong common name, or is missing its intermediate chain — the browser then blocks the site.
   - Only TLS 1.0/1.1 is supported, which modern browsers refuse.
   - Port 443 is closed on the server or blocked by a firewall.

   Server or network related
   - The web server process is down, or the server is overloaded.
   - A firewall or ACL is dropping traffic to that specific IP.
   - Asymmetric routing or a black-holed route to that prefix at one of the multiple ISPs.

   Troubleshooting steps, in order

   - Step 1 — confirm it is DNS
   ```
   nslookup BSCPL.bd.gov
   dig BSCPL.bd.gov +trace
   ```
   If no address is returned, the fault is DNS. If an address is returned, move to step 3.

   - Step 2 — test with a different resolver
   ```
   nslookup BSCPL.bd.gov 8.8.8.8
   ```
   If Google's resolver answers but the local one does not, the local DNS server or its cache is at fault. Flush it with `ipconfig /flushdns` (Windows) or `systemd-resolve --flush-caches` (Linux).

   - Step 3 — test reachability of the resolved IP
   ```
   ping <resolved IP>
   tracert <resolved IP>
   telnet <resolved IP> 443
   ```
   This separates "name resolves but host unreachable" from "host reachable but service refused".

   - Step 4 — bypass DNS entirely
   Add a temporary entry in the hosts file mapping the correct IP to the name. If the site then loads, DNS is definitively the problem.

   - Step 5 — check the certificate
   ```
   openssl s_client -connect BSCPL.bd.gov:443 -servername BSCPL.bd.gov
   ```
   Look at the expiry date, the common name and the chain.

   - Step 6 — check from outside
   Use an external checking service or a mobile connection. If it works from outside but not inside, the problem is local (firewall, internal DNS view, proxy).

   - Step 7 — check the server itself
   Confirm the web service is running, review its logs, and verify the firewall allows 443.

   Preventive measures
   - Two authoritative DNS servers on separate networks.
   - Monitoring and automatic alerts for certificate expiry and DNS record changes.
   - Sensible TTL values — lower them before a planned IP change.
   - DNSSEC to prevent cache poisoning, and regular external availability monitoring.

2. **Write down the DNS function.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1449 (ET: N/A)]*

   Answer: DNS (Domain Name System) is the internet's naming service. Its main function is to translate human-readable domain names into machine-readable IP addresses.

   Functions
   - Name to IP resolution (forward lookup) — www.google.com becomes 142.250.190.78. This is the primary job, and it is why people never have to remember numbers.
   - IP to name resolution (reverse lookup) — using PTR records in the in-addr.arpa zone. Mail servers rely on this to check that a sending IP matches its claimed name.
   - Mail routing — MX records tell a sending mail server which host accepts mail for a domain.
   - Load distribution — several A records for one name, or a short TTL, spread users across servers; this is how CDNs steer traffic.
   - Service discovery — SRV records advertise which host and port provide a service.
   - Aliasing — CNAME records point one name at another.
   - Caching — resolvers store answers for the TTL period, which cuts traffic and speeds up later lookups.
   - Hierarchy and delegation — the namespace is divided into zones, so no single server has to hold the whole internet.

   Common record types

   | Record | Purpose |
   |---|---|
   | A | Name to IPv4 address |
   | AAAA | Name to IPv6 address |
   | CNAME | Alias for another name |
   | MX | Mail exchanger |
   | NS | Name servers for the zone |
   | PTR | IP to name (reverse) |
   | SOA | Start of authority — zone parameters |
   | TXT | Free text; used for SPF, DKIM and domain verification |

   - DNS uses port 53: UDP for ordinary queries, TCP for zone transfers and for responses larger than 512 bytes.

3. **Why does the Domain Name System (DNS) primarily use UDP as its transport layer protocol instead of TCP? Describe the sequence of events that take place during the DNS name resolution process when a user enters www.companybd.com into a web browser and presses Enter.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1421 (ET: E-Zone)]*

   Answer:

   Why DNS uses UDP rather than TCP
   - Speed — a DNS query and its reply are a single small exchange. TCP would need a three-way handshake first, roughly tripling the delay before any answer arrives.
   - Low overhead — a UDP header is 8 bytes against TCP's 20, and there is no connection state to set up or tear down.
   - Small messages — a typical query and response fit inside 512 bytes, so the segmentation and reliability machinery of TCP is not needed.
   - Server scalability — a busy resolver handles millions of queries; keeping a TCP connection open for each would exhaust memory and file descriptors. UDP is stateless, so the server just answers and forgets.
   - Retry is cheap — if a UDP reply is lost, the resolver simply asks again, or asks a different server. That is simpler than TCP's retransmission logic for a one-shot request.

   When DNS does use TCP
   - Zone transfers (AXFR/IXFR) between primary and secondary servers, which are large and must be reliable.
   - Any response larger than 512 bytes: the server sets the TC (truncated) flag and the resolver retries over TCP. DNSSEC and IPv6 records often exceed this.
   - Modern encrypted variants: DoT (DNS over TLS, port 853) and DoH (DNS over HTTPS, port 443).

   Sequence of events for www.companybd.com

   - Step 1 — the browser checks its own cache, then the operating system cache, then the hosts file. If a valid entry exists, resolution stops here.
   - Step 2 — if not cached, the OS sends a recursive query to the configured resolver, usually the ISP's or 8.8.8.8, on UDP port 53.
   - Step 3 — the resolver checks its own cache. If it has the answer within its TTL, it returns it immediately.
   - Step 4 — otherwise the resolver queries a root server. The root does not know the address, but replies with the name servers for `.com`. This is an iterative referral.
   - Step 5 — the resolver queries the `.com` TLD server, which replies with the authoritative name servers for `companybd.com`.
   - Step 6 — the resolver queries the authoritative server for companybd.com, which returns the A record for www with its IP address.
   - Step 7 — the resolver caches the answer for the TTL period and returns it to the client, which also caches it.
   - Step 8 — the browser now opens a TCP connection to that IP on port 443, completes the TLS handshake, sends the HTTP GET, and renders the page.

   ```
   Client --recursive--> Resolver --iterative--> Root (.)        "ask .com"
                                 --iterative--> .com TLD         "ask ns1.companybd.com"
                                 --iterative--> Authoritative     "93.184.x.x"
   Client <---answer------ Resolver (caches it for the TTL)
   ```
   - Note the pattern: the client makes one recursive query; the resolver does the iterative work of walking down the hierarchy.

4. **What is DHCP?** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*

   Answer: DHCP (Dynamic Host Configuration Protocol) is an application-layer protocol that automatically assigns IP addresses and other network settings to devices when they join a network.

   What it supplies
   - IP address, subnet mask, default gateway, DNS server addresses, and often the domain name, NTP server and lease time.

   Key facts
   - Ports: UDP 67 for the server, UDP 68 for the client.
   - It works through the four-step `DORA` exchange: Discover, Offer, Request, Acknowledge.
   - Addresses are leased for a limited time and must be renewed, normally at 50 percent of the lease (T1) and again at 87.5 percent (T2).
   - A relay agent (IP helper) forwards DHCP broadcasts across a router, so one server can serve many subnets.

   Advantages
   - No manual configuration, so no typing errors and no duplicate addresses.
   - Central management; a change to the gateway or DNS server is made once, on the server.
   - Efficient reuse of a limited address pool as devices come and go.
   - Essential for mobile devices that move between networks.

   Disadvantages and risks
   - No built-in authentication, so a rogue DHCP server can hand out a false gateway and intercept traffic. DHCP snooping on the switch is the defence.
   - DHCP starvation, where an attacker requests every address in the pool. Port security limits it.
   - If the server fails, new clients cannot obtain an address.

   - Reservations tie one MAC address to one fixed IP, giving static-like stability with central management.

5. **Which protocol is used by the ping tools?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: The ping tool uses `ICMP` (Internet Control Message Protocol).

   - ping sends an ICMP Echo Request (Type 8) and waits for an ICMP Echo Reply (Type 0).
   - ICMP is a Network layer (Layer 3) protocol carried directly inside IP, with protocol number 1. It uses no port numbers, because it is not a transport protocol.
   - What ping reports: whether the host is reachable, the round-trip time in milliseconds, the TTL of the reply, and the percentage of packets lost.

   Other ICMP messages

   | Type | Message | Meaning |
   |---|---|---|
   | 0 | Echo Reply | Response to a ping |
   | 3 | Destination Unreachable | No route, or port closed |
   | 5 | Redirect | Use a better gateway |
   | 8 | Echo Request | The ping itself |
   | 11 | Time Exceeded | TTL reached zero — this is what traceroute exploits |

   - Note: traceroute on Linux uses UDP with increasing TTL by default, while Windows tracert uses ICMP. Many firewalls block ICMP, so a failed ping does not always mean the host is down.

6. **Which server can be used to dinamically assign IP address to the PCs is a LAN?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*

   Answer: A `DHCP server` (Dynamic Host Configuration Protocol server) dynamically assigns IP addresses to PCs on a LAN.

   - It hands out the IP address, subnet mask, default gateway and DNS server addresses automatically, so no machine has to be configured by hand.
   - It runs on UDP port 67, with clients on port 68, and uses the DORA exchange — Discover, Offer, Request, Acknowledge.
   - It can be a dedicated server (Windows Server, Linux ISC DHCP), or the service built into a router or Layer 3 switch. Home routers all run one.
   - Each address is given on a lease and returned to the pool when the lease expires, so a limited pool serves many devices over time.
   - Reservations bind a specific MAC address to a fixed IP for printers and servers.
   - If no DHCP server answers, a Windows client self-assigns an APIPA address from 169.254.0.0/16, which only allows local communication — that address is a clear sign the DHCP server is unreachable.

7. **Explain how do DHCP work?** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 565 (ET: N/A)], [BREB Assistant Programmer (AP) 21.02.2025 compact it 1335 (ET: N/A)]*

   Answer: DHCP works through a four-step exchange known as `DORA` — Discover, Offer, Request, Acknowledge. It uses UDP port 67 (server) and 68 (client).

   The four steps

   - 1. DHCP DISCOVER — the client has no address, so it broadcasts to 255.255.255.255 from source 0.0.0.0, asking whether any DHCP server is present. The broadcast carries the client's MAC address.
   - 2. DHCP OFFER — every DHCP server that hears the discover reserves a free address from its pool and replies with an offer containing that IP, the subnet mask, gateway, DNS servers and the lease time.
   - 3. DHCP REQUEST — the client accepts one offer (normally the first that arrives) and broadcasts a request naming that server. The broadcast tells the other servers to release the addresses they had reserved.
   - 4. DHCP ACK — the chosen server confirms the assignment, writes the binding into its database, and the client configures its interface. If the address has become unavailable it sends a DHCP NAK instead, and the client restarts from Discover.

   ```
   CLIENT                                  SERVER
     |------- DHCP DISCOVER (broadcast) ----->|
     |<------ DHCP OFFER  (IP proposed) ------|
     |------- DHCP REQUEST (broadcast) ------>|
     |<------ DHCP ACK   (confirmed) ---------|
           client now has IP, mask, gateway, DNS
   ```

   Lease renewal
   - T1, at 50 percent of the lease, the client unicasts a renewal request to the same server.
   - T2, at 87.5 percent, if there was no reply, the client broadcasts to any server.
   - If the lease expires with no reply, the client gives up the address and starts DORA again.
   - `ipconfig /release` and `ipconfig /renew` force these steps manually.

   Across subnets
   - Routers do not forward broadcasts, so a DHCP relay agent (the `ip helper-address` command) converts the broadcast into a unicast towards the central server. That is how one server can serve many VLANs.

   Security notes
   - DHCP has no authentication. A rogue server can hand out a false gateway and become a man in the middle; DHCP snooping on the switch blocks offers from untrusted ports.
   - DHCP starvation exhausts the pool with forged MAC addresses; port security limits the number of MACs per port.

8. **SMTP, DNS, DHCP, NAT এর কাজ কি লিখ?** *[BTCL Junior Assistant Manager 2022 compact it 639 (ET: BUET)]*

   Answer: (Answered in English, as required for IT topics.)

   SMTP (Simple Mail Transfer Protocol)
   - Sends and relays email. It pushes a message from the client to its mail server, and from one mail server to the next, until it reaches the recipient's server.
   - Ports: 25 for server-to-server relay, 587 for client submission with STARTTLS, 465 for implicit TLS.
   - It is a push protocol and handles sending only. Retrieval is done by POP3 (port 110) or IMAP (port 143).

   DNS (Domain Name System)
   - Translates domain names into IP addresses (forward lookup) and IP addresses back into names (reverse lookup, using PTR records).
   - Also directs mail with MX records, distributes load with multiple A records, and caches answers for the TTL period.
   - Port 53: UDP for queries, TCP for zone transfers and large responses.

   DHCP (Dynamic Host Configuration Protocol)
   - Automatically assigns an IP address, subnet mask, default gateway and DNS servers to a client joining the network.
   - Uses the DORA exchange over UDP ports 67 and 68; addresses are leased for a limited time and reused when returned.
   - Removes manual configuration errors and address conflicts.

   NAT (Network Address Translation)
   - Translates private IP addresses into a public one, so many internal hosts can share a single public address. This is a major reason IPv4 has lasted so long.
   - Types: static NAT (one-to-one), dynamic NAT (from a pool) and PAT or NAT overload (many-to-one, distinguished by port number — what home routers use).
   - It also hides internal addressing, which gives a basic layer of security, but it breaks end-to-end connectivity and complicates protocols such as VoIP and FTP.

9. **What is DNS? What is forward and reverse lookup DNS?** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 658 (ET: N/A)]*

   Answer:

   What is DNS
   - The Domain Name System is the internet's distributed naming service. It translates human-readable domain names into IP addresses, so users never have to remember numbers.
   - It is hierarchical: root servers (.) at the top, then TLD servers (.com, .org, .bd), then authoritative servers for each individual domain. Each level delegates to the level below, so no single server holds the whole internet.
   - It runs on port 53 — UDP for ordinary queries, TCP for zone transfers and large responses — and it caches answers for the TTL period.

   Forward lookup
   - Converts a `name into an IP address`, which is the normal direction. www.example.com -> 93.184.216.34.
   - Uses A records (IPv4) and AAAA records (IPv6).
   - It is what happens every time a browser opens a website.

   Reverse lookup
   - Converts an `IP address into a name`. 93.184.216.34 -> www.example.com.
   - Uses PTR records held in the special zone `in-addr.arpa` for IPv4 (or ip6.arpa for IPv6). The IP is written backwards: 34.216.184.93.in-addr.arpa.
   - Uses: email anti-spam checks (a mail server verifies that the sending IP has a matching PTR record), logging and diagnostics that show names instead of numbers, and troubleshooting with `nslookup <IP>` or `dig -x <IP>`.

   | Point | Forward lookup | Reverse lookup |
   |---|---|---|
   | Direction | Name -> IP | IP -> Name |
   | Record type | A / AAAA | PTR |
   | Zone | The normal domain zone | in-addr.arpa / ip6.arpa |
   | Main use | Browsing, any client connection | Mail validation, logging, diagnostics |

10. **What is ICMP, SMTP, POP server, Boot loader and Clustering?** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 659 (ET: N/A)]*

    Answer:

    ICMP (Internet Control Message Protocol)
    - A Network layer protocol carried inside IP (protocol number 1) that reports errors and carries diagnostic messages. It uses no port numbers.
    - Messages: Echo Request/Reply (ping), Destination Unreachable, Time Exceeded (used by traceroute), Redirect, Source Quench.
    - It does not carry user data; it exists so that hosts and routers can report problems.

    SMTP (Simple Mail Transfer Protocol)
    - The application-layer protocol that sends and relays email, from client to server and between servers. Ports 25 (relay), 587 (submission with TLS) and 465 (implicit TLS).
    - It is a push protocol; retrieval is handled by POP3 or IMAP. Related standards SPF, DKIM and DMARC verify the sender.

    POP server (Post Office Protocol)
    - A mail server that lets a client download messages from the mailbox, on port 110 (995 with SSL).
    - POP3 normally downloads and then deletes the message from the server, so mail lives on one device and offline access is easy.
    - IMAP (port 143, or 993 with SSL) is the alternative: it keeps mail on the server and synchronises folders and read status across many devices, which suits modern multi-device use.

    Boot loader
    - A small program that runs when a computer is switched on and loads the operating system kernel into memory.
    - Sequence: BIOS or UEFI performs POST, reads the MBR or the EFI system partition, and hands control to the boot loader, which then loads the kernel.
    - Examples: GRUB and LILO on Linux, Windows Boot Manager (bootmgr) on Windows, U-Boot on embedded systems. A multi-boot loader shows a menu of installed operating systems.

    Clustering
    - Joining several computers so they behave as one system, for higher availability and performance.
    - Types: high-availability clusters (a standby takes over if the active node fails), load-balancing clusters (work is shared among nodes), and high-performance computing clusters (many nodes compute in parallel).
    - Benefits: no single point of failure, scalability by adding nodes, and maintenance without downtime. Components include a heartbeat link, shared storage and a virtual IP that follows the active node.

11. **Write a command how to find DNS www.egcb.gov.bd and which protocol uses?** *[EGCB Assistant Engineer (CSE) 2022 compact it 716 (ET: BUET)]*

    Answer:

    Commands to find the DNS record
    ```
    nslookup www.egcb.gov.bd
    dig www.egcb.gov.bd
    dig www.egcb.gov.bd A +short
    host www.egcb.gov.bd
    ```
    - `nslookup` works on both Windows and Linux. `dig` and `host` are the standard Linux tools and give more detail.
    - To query a specific server: `nslookup www.egcb.gov.bd 8.8.8.8`
    - To follow the full delegation chain from the root: `dig www.egcb.gov.bd +trace`
    - For the reverse direction: `nslookup <IP>` or `dig -x <IP>`

    Protocol used
    - The query itself uses `DNS`, which runs on `UDP port 53`.
    - TCP port 53 is used instead when the response is larger than 512 bytes (the server sets the TC flag and the resolver retries over TCP) and for zone transfers between name servers.
    - Encrypted variants: DNS over TLS on port 853 and DNS over HTTPS on port 443.

    Sample output shape
    ```
    Server:   8.8.8.8
    Address:  8.8.8.8#53

    Non-authoritative answer:
    Name:     www.egcb.gov.bd
    Address:  103.x.x.x
    ```
    - "Non-authoritative" means the answer came from a resolver's cache rather than from the domain's own authoritative server.

12. **For the following description of various IP networking protocols write down the protocol name and its full form in the following table:** *[BTCL Assistant Manager (Technical) 2021 compact it 764 (ET: BUET)]*

    Answer: The description table was not printed with the question, so the standard IP networking protocols and their full forms are given.

    | Protocol | Full form | Layer | Function |
    |---|---|---|---|
    | IP | Internet Protocol | Network | Logical addressing and routing of packets |
    | TCP | Transmission Control Protocol | Transport | Reliable, connection-oriented, ordered delivery |
    | UDP | User Datagram Protocol | Transport | Fast, connectionless delivery with no guarantee |
    | ICMP | Internet Control Message Protocol | Network | Error reporting and diagnostics — ping, traceroute |
    | ARP | Address Resolution Protocol | Network / Data Link | Maps a known IP address to a MAC address |
    | RARP | Reverse Address Resolution Protocol | Network / Data Link | Maps a MAC address to an IP address (obsolete) |
    | DHCP | Dynamic Host Configuration Protocol | Application | Automatically assigns IP, mask, gateway and DNS |
    | DNS | Domain Name System | Application | Translates names to IP addresses and back |
    | HTTP | HyperText Transfer Protocol | Application | Transfers web pages, TCP port 80 |
    | HTTPS | HTTP Secure | Application | HTTP inside a TLS-encrypted channel, TCP port 443 |
    | FTP | File Transfer Protocol | Application | File transfer, TCP ports 20 and 21 |
    | SMTP | Simple Mail Transfer Protocol | Application | Sends and relays email, port 25/587 |
    | POP3 | Post Office Protocol version 3 | Application | Downloads mail from the server, port 110 |
    | IMAP | Internet Message Access Protocol | Application | Keeps and synchronises mail on the server, port 143 |
    | SNMP | Simple Network Management Protocol | Application | Monitors and manages network devices, port 161 |
    | Telnet | Telecommunication Network | Application | Remote login in plain text, port 23 |
    | SSH | Secure Shell | Application | Encrypted remote login, port 22 |
    | IGMP | Internet Group Management Protocol | Network | Multicast group membership |
    | OSPF | Open Shortest Path First | Network | Link-state interior routing protocol |
    | BGP | Border Gateway Protocol | Application over TCP 179 | Routing between autonomous systems |
    | NAT | Network Address Translation | Network | Translates private addresses to public |

13. **(a) How does a browser retrieve IP address from URL?** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 794 (ET: N/A)]*

    Answer: The browser turns a URL into an IP address through DNS resolution, checking a series of caches first and only then querying the DNS hierarchy.

    Step by step
    - Step 1 — the browser parses the URL and extracts the hostname. From `https://www.example.com/page.html` the hostname is www.example.com.
    - Step 2 — it checks its own DNS cache. Chrome keeps one; `chrome://net-internals/#dns` shows it.
    - Step 3 — it asks the operating system, which checks the OS resolver cache (`ipconfig /displaydns` on Windows).
    - Step 4 — the OS checks the hosts file, which overrides DNS entirely.
    - Step 5 — if still unresolved, the OS sends a recursive query to the configured DNS resolver on UDP port 53.
    - Step 6 — the resolver checks its own cache. If the record is present and within its TTL, it answers immediately.
    - Step 7 — otherwise the resolver walks the hierarchy iteratively: a root server refers it to the `.com` TLD servers, the TLD servers refer it to the authoritative servers for example.com, and the authoritative server returns the A record.
    - Step 8 — the resolver caches the answer for the TTL and returns it. The OS and the browser cache it too.
    - Step 9 — the browser opens a TCP connection to that IP on port 443, completes the TLS handshake, sends the HTTP request and renders the response.

    ```
    Browser cache -> OS cache -> hosts file -> Resolver cache
            -> Root (.) -> .com TLD -> Authoritative -> IP address
    ```
    - Caching at every level is what keeps this fast: most lookups never leave the machine, and few ever reach a root server.

14. **(d) What is DNS? “TCP/IP is used in DNS”- justify the statement.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 795 (ET: N/A)]*

    Answer:

    What is DNS
    - The Domain Name System is the internet's distributed, hierarchical naming service. It translates domain names into IP addresses and back, using port 53.
    - Structure: root servers, TLD servers (.com, .org, .bd), and authoritative servers for each domain, with resolvers doing the lookup work on behalf of clients and caching the results for the TTL.
    - Records include A, AAAA, CNAME, MX, NS, PTR, SOA and TXT.

    Justification — "TCP/IP is used in DNS"
    - DNS is an application-layer protocol of the TCP/IP suite. It cannot work on its own; it relies on the lower layers of TCP/IP for every message it sends. Concretely:

    - It uses `UDP` (a TCP/IP transport protocol) on port 53 for ordinary queries and responses. UDP is chosen for speed, because a query is a single small exchange and a handshake would be wasteful.
    - It uses `TCP` on port 53 when a response exceeds 512 bytes (the server sets the TC flag and the resolver retries over TCP) and for zone transfers between primary and secondary servers, which must be reliable and are large.
    - It uses `IP` for addressing and routing: every DNS query is carried inside an IP packet from the resolver to the name server, and it is IP addresses that DNS ultimately returns.
    - It is defined as part of the TCP/IP application layer in RFC 1034 and RFC 1035, alongside HTTP, SMTP and FTP.
    - The dependency is mutual in practice: DNS needs TCP/IP to carry its messages, and TCP/IP applications need DNS to turn names into the addresses they must connect to.

    - Conclusion: the statement is correct. DNS is a TCP/IP application-layer service that uses both UDP and TCP over IP, which is exactly why it is described as "using TCP/IP".

15. **(b) How is Hierarchical DNS resolution done in Domain Naming System? Give an example resolution for xyz.uv.gov.bd domain name.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 802 (ET: N/A)]*

    Answer:

    Hierarchical DNS resolution
    - The DNS namespace is a tree. No single server holds everything; each level knows only its children and delegates the rest.
    ```
                        . (root)
                        |
          +-------+-----+-----+-------+
         com     org    net    bd    edu        <- top-level domains
                                |
                              gov.bd            <- second level
                                |
                              uv.gov.bd         <- sub-domain
                                |
                            xyz.uv.gov.bd       <- host
    ```
    - The client sends one recursive query to its resolver; the resolver then performs iterative queries down the tree.

    Example — resolving xyz.uv.gov.bd

    - Step 1 — the client asks its local resolver for xyz.uv.gov.bd (recursive query).
    - Step 2 — the resolver checks its cache. If the answer is there and still within its TTL, it stops here.
    - Step 3 — otherwise it queries a `root server`. The root does not know the address, but it returns the name servers for `.bd`.
    - Step 4 — it queries the `.bd` TLD server, which returns the name servers for `gov.bd`.
    - Step 5 — it queries the `gov.bd` server, which returns the name servers for `uv.gov.bd`.
    - Step 6 — it queries the `uv.gov.bd` authoritative server, which finally returns the A record for `xyz.uv.gov.bd`, say 203.112.x.x.
    - Step 7 — the resolver caches every referral and the final answer for their TTLs, then returns the address to the client.

    ```
    Client --recursive--> Resolver
                            |--iterative--> Root        -> "ask .bd servers"
                            |--iterative--> .bd         -> "ask gov.bd servers"
                            |--iterative--> gov.bd      -> "ask uv.gov.bd servers"
                            |--iterative--> uv.gov.bd   -> "203.112.x.x"
    Client <--answer-------- Resolver
    ```
    - Why the hierarchy matters: it distributes both the data and the load, allows each organisation to manage its own zone, and makes the system scale to billions of names. Caching means a root server is rarely troubled — most queries are answered from a cache long before that.

16. **What is Web cashing? Why we use web cashing?** *[Sonali Bank Ltd. Officer IT 2021 compact it 908 (ET: N/A)]*

    Answer:

    What is web caching
    - Web caching is storing a copy of a web resource — an HTML page, image, script or video segment — closer to the user, so that later requests are served from the copy instead of fetching it again from the origin server.
    - A proxy server that does this is called a web cache or proxy cache.

    Where caches exist
    - Browser cache — on the user's own disk, private to that user.
    - Proxy or organisational cache — one cache serving a whole office or campus.
    - ISP cache — serving all of a provider's customers.
    - CDN edge server — a distributed cache placed near users worldwide; this is the dominant form today.
    - Reverse proxy — sitting in front of the origin server to protect it.

    How it works
    - The client requests a resource. If the cache holds a fresh copy (its expiry has not passed), it returns it immediately — a cache hit.
    - If not, it forwards the request to the origin, stores the response and returns it — a cache miss.
    - Freshness is controlled by HTTP headers: `Cache-Control: max-age`, `Expires`, `ETag` and `Last-Modified`. A conditional request (`If-None-Match`) lets the server reply `304 Not Modified` with no body, which is very cheap.

    Why we use it
    - Faster response — the content comes from nearby, so latency drops sharply. This is the single biggest reason.
    - Less bandwidth used on the expensive upstream link, which matters greatly for an ISP or a campus.
    - Reduced load on the origin server, so it can serve more users with the same hardware.
    - Better availability — cached content may still be served when the origin is briefly unreachable.
    - Lower cost, since bandwidth and server capacity are the two main expenses of a busy site.
    - Better user experience and, indirectly, better search ranking.

    Limitations
    - Stale content if TTLs are set too long; personalised or private pages must not be cached (`Cache-Control: private, no-store`).
    - Cache invalidation is genuinely hard — the usual solution is versioned file names such as `style.v3.css`.

17. **What is DNS Resolver?** *[Sonali Bank Ltd. Officer IT 2021 compact it 908-909 (ET: N/A)]*

    Answer: A DNS resolver (also called a recursive resolver or recursive name server) is the DNS server that does the actual work of looking up a name on behalf of a client.

    What it does
    - Receives a recursive query from the client — "give me the IP address for www.example.com".
    - Checks its own cache first. If a valid record is present, it answers straight away.
    - If not, it performs iterative queries down the hierarchy: root server -> TLD server -> authoritative server.
    - Caches the answer for its TTL, so later clients are served instantly.
    - Returns the final answer to the client, marked "non-authoritative" if it came from cache.

    Types of resolver
    - Stub resolver — the small piece of code inside the operating system or browser. It cannot walk the hierarchy; it just forwards the query to a recursive resolver.
    - Recursive resolver — the full resolver, run by an ISP or a public service, that does the hierarchy walk.
    - Forwarding resolver — passes queries to another resolver rather than resolving them itself, common on office routers.

    Common public resolvers
    - Google 8.8.8.8 and 8.8.4.4, Cloudflare 1.1.1.1, Quad9 9.9.9.9, OpenDNS 208.67.222.222.

    Why it matters
    - It is the component that makes caching effective, so most lookups never reach a root or TLD server.
    - Its choice affects speed, privacy and filtering — some resolvers block malicious domains, and DoH/DoT encrypt the query so it cannot be read or altered in transit.
    - A misconfigured or poisoned resolver is a serious security problem, since it can silently send users to attacker-controlled addresses. DNSSEC validation at the resolver is the defence.

18. **DNS server এবং DHCP server এর কাজ কী?** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 911 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.)

    DNS server
    - Translates domain names into IP addresses (forward lookup, A and AAAA records) and IP addresses back into names (reverse lookup, PTR records).
    - Directs email using MX records, and supports aliases (CNAME), name servers (NS) and verification data (TXT, for SPF and DKIM).
    - Works hierarchically — root, TLD, authoritative — and caches answers for the TTL period, which is what makes the whole system fast.
    - Port 53: UDP for queries, TCP for zone transfers and large responses.
    - Without DNS, users would have to type IP addresses for every site.

    DHCP server
    - Automatically assigns an IP address, subnet mask, default gateway and DNS server addresses to every device that joins the network.
    - Uses the DORA exchange — Discover, Offer, Request, Acknowledge — over UDP ports 67 and 68.
    - Addresses are leased for a limited time and returned to the pool when they expire, so a limited pool serves many devices.
    - Reservations tie a specific MAC address to a fixed IP for printers and servers.
    - Without DHCP, every device would need manual configuration, which is slow and causes duplicate-address errors.

    How they work together
    - DHCP tells a new client which DNS server to use. So DHCP configures the client, and DNS then lets that client find other hosts by name. A failure in DHCP stops a client getting on the network at all; a failure in DNS leaves it connected but unable to resolve names.

19. **দূরবর্তী কম্পিউটার সংযোগ এর জন্য কোন প্রোটোকল ব্যবহার করা হয়?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 944 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) For connecting to a remote computer, the protocols used are:

    - `SSH (Secure Shell)` — TCP port 22. The standard today. It provides an encrypted command-line session, plus secure file transfer through SCP and SFTP and port forwarding. It authenticates with a password or, better, a key pair.
    - `Telnet` — TCP port 23. The older protocol for the same purpose, but everything including the password travels in plain text, so it must not be used over an untrusted network. SSH replaced it.
    - `RDP (Remote Desktop Protocol)` — TCP port 3389. Microsoft's protocol for a full graphical Windows desktop, with encryption.
    - `VNC (Virtual Network Computing)` — port 5900. A cross-platform graphical remote desktop; it should be tunnelled through SSH or a VPN, since it is weakly encrypted on its own.

    | Protocol | Port | Interface | Encrypted |
    |---|---|---|---|
    | SSH | 22 | Command line | Yes |
    | Telnet | 23 | Command line | No |
    | RDP | 3389 | Graphical (Windows) | Yes |
    | VNC | 5900 | Graphical (cross-platform) | Weak, tunnel it |

    - Best practice for remote access: use SSH with key-based authentication, disable password login and root login, change the default port, and place the whole thing behind a VPN.

20. **(a) Differentiate between DNS server and caches.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1142 (ET: N/A)]*

    Answer: A DNS server is the machine that answers name queries; a DNS cache is the temporary store of answers it has already learned.

    | Point | DNS server | DNS cache |
    |---|---|---|
    | What it is | A service that resolves names to IP addresses | A temporary store of previous answers |
    | Where it lives | A dedicated server, ISP resolver or router | Inside the browser, the OS, the resolver or the router |
    | Data held | The authoritative zone file, or the full resolution capability | Only recently used records, and only while the TTL lasts |
    | Persistence | Permanent, administratively maintained | Temporary; entries expire with the TTL and are lost on flush |
    | Answer type | Authoritative if it owns the zone | Always non-authoritative |
    | Purpose | To provide resolution for the namespace it serves | To make repeated lookups fast and reduce query traffic |
    | Failure effect | Names cannot be resolved at all | Lookups become slower, and stale entries can point to a dead address |

    How they work together
    - A resolver is a DNS server that keeps a cache. On each query it looks in the cache first; only on a miss does it walk the hierarchy from root to TLD to authoritative server, and it then caches what it learns.
    - Caching exists at several levels — browser, operating system, router, ISP resolver — so most queries never leave the user's own machine.
    - Cache problems are flushed with `ipconfig /flushdns` on Windows or `systemd-resolve --flush-caches` on Linux; this is the standard fix after a site's IP address has changed.

21. **What is the difference between DNS server and caches? What is the importance of DNS cache in World Wide Web?** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1189 (ET: N/A)]*

    Answer:

    Difference between a DNS server and a cache

    | Point | DNS server | DNS cache |
    |---|---|---|
    | Nature | A service that resolves names | A temporary store of already-resolved answers |
    | Location | Dedicated server, ISP resolver, or router | Browser, OS, router, resolver |
    | Contents | Zone data, or full resolution capability | Only recent records, held for their TTL |
    | Lifetime | Permanent | Temporary, expires with the TTL |
    | Authority | Authoritative for the zones it owns | Always non-authoritative |
    | Purpose | To answer queries for the namespace | To answer repeat queries instantly |

    Importance of the DNS cache to the World Wide Web
    - Speed — a cached lookup takes microseconds; a full walk from root to TLD to authoritative server can take hundreds of milliseconds. Since a single modern web page may reference dozens of hostnames, caching removes a large part of page-load time.
    - Scale — there are billions of DNS queries per second worldwide. Without caching, the 13 root server clusters and the TLD servers would be overwhelmed instantly. Caching is what makes the hierarchy survivable.
    - Reduced bandwidth and cost, especially on expensive international links.
    - Resilience — if an authoritative server briefly fails, cached records keep the site reachable until they expire.
    - Better user experience, and indirectly better search ranking, because page load time is a ranking factor.

    The trade-off
    - Stale data. When a site changes its IP address, cached entries still point to the old one until the TTL expires. Administrators therefore lower the TTL before a planned migration.
    - Cache poisoning — an attacker injects a false record so users are silently sent to a malicious server. DNSSEC, source-port randomisation and query ID randomisation are the defences.
    - Fix for a client: `ipconfig /flushdns` on Windows, `systemd-resolve --flush-caches` on Linux.

22. **Write short notes on DHCP and SMTP.** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1227 (ET: N/A)]*

    Answer:

    DHCP (Dynamic Host Configuration Protocol)
    - An application-layer protocol that automatically gives a device joining a network its IP address, subnet mask, default gateway, DNS servers and lease time.
    - Ports: UDP 67 (server) and UDP 68 (client).
    - Works through the `DORA` exchange:
      - Discover — the client broadcasts, looking for a server.
      - Offer — servers reply with an available address and settings.
      - Request — the client broadcasts its acceptance of one offer.
      - Acknowledge — the chosen server confirms and records the binding.
    - Addresses are leased, renewed at T1 (50 percent) and T2 (87.5 percent) of the lease, and returned to the pool when they expire.
    - A relay agent (`ip helper-address`) forwards the broadcast across a router so one server can serve many subnets.
    - Benefits: no manual configuration, no duplicate addresses, central management, efficient reuse of a limited pool.
    - Risks: no authentication, so rogue servers and starvation attacks are possible. DHCP snooping and port security are the defences. If no server answers, a Windows client falls back to an APIPA address in 169.254.0.0/16.

    SMTP (Simple Mail Transfer Protocol)
    - The application-layer protocol used to send and relay email — from the client to its mail server, and from one mail server to the next.
    - Ports: 25 for server-to-server relay, 587 for client submission with STARTTLS, 465 for implicit TLS.
    - It is a push protocol and handles sending only; retrieval uses POP3 (110) or IMAP (143).
    - A session is a simple text dialogue: HELO/EHLO, MAIL FROM, RCPT TO, DATA, then the message ending with a single dot, then QUIT. The server replies with codes such as 250 OK and 550 Rejected.
    - Components: the Mail User Agent (the client program), the Mail Transfer Agent (Postfix, Sendmail, Exchange) and the Mail Delivery Agent that puts the message in the mailbox.
    - Weakness: SMTP by itself does not verify the sender, which is why spam and spoofing are possible. SPF, DKIM and DMARC were added to authenticate the sending domain.

## Wireless Networks & IoT (mmWave) (19)

1. **Describe Wi-Fi, Bluetooth, and WiMAX.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

   Answer:

   Wi-Fi (IEEE 802.11)
   - A wireless LAN technology that connects devices to a network within a building or campus, through an access point.
   - Frequency: 2.4 GHz, 5 GHz and, in Wi-Fi 6E and 7, 6 GHz. Range: roughly 30–100 m indoors.
   - Speed: 54 Mbps (802.11g) to several Gbps (Wi-Fi 6 and 7).
   - Access method: CSMA/CA, because a radio cannot detect collisions while transmitting.
   - Security: WEP (broken), WPA, WPA2 with AES, and WPA3 today.
   - Uses: home and office internet, hotspots, campus networks.

   Bluetooth (IEEE 802.15.1)
   - A short-range personal area network (PAN) technology for connecting devices to each other, not to a network.
   - Frequency: 2.4 GHz ISM band, using frequency hopping spread spectrum to resist interference.
   - Range: about 10 m for Class 2 devices, up to 100 m for Class 1.
   - Speed: 1–3 Mbps for classic Bluetooth, 2 Mbps for BLE.
   - Topology: a piconet of one master and up to seven active slaves; several piconets form a scatternet.
   - BLE (Bluetooth Low Energy) is the version used by IoT sensors and wearables, because a coin cell can last for years.
   - Uses: headsets, keyboards, file transfer, fitness bands, car audio.

   WiMAX (IEEE 802.16)
   - Worldwide Interoperability for Microwave Access — a wireless MAN technology, intended as "broadband without cables" over a whole city.
   - Frequency: 2–11 GHz for non-line-of-sight, 10–66 GHz for line-of-sight.
   - Range: up to 50 km from a base station; speed up to about 70 Mbps shared.
   - Topology: point-to-multipoint from a base station to subscriber stations, with QoS support built in.
   - Uses: last-mile broadband where cable is impractical, rural connectivity, backhaul.
   - Status: largely displaced by LTE and 5G, which offered better mobility and a far larger ecosystem.

   Comparison

   | Point | Bluetooth | Wi-Fi | WiMAX |
   |---|---|---|---|
   | Standard | 802.15.1 | 802.11 | 802.16 |
   | Network type | PAN | LAN | MAN |
   | Range | 10–100 m | 30–100 m | Up to 50 km |
   | Speed | 1–3 Mbps | 54 Mbps – several Gbps | Up to ~70 Mbps |
   | Power use | Very low | Moderate | High |
   | Purpose | Device to device | Device to network | City-wide broadband access |

2. **What is the use of mmWave in IoT?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1454 (ET: BUET)]*

   Answer: mmWave (millimetre wave) is the radio spectrum from `30 GHz to 300 GHz`, with wavelengths of 1–10 mm. In 5G the bands around 24–40 GHz are the ones commonly used.

   Why it matters for IoT
   - Very high bandwidth — the channels are hundreds of MHz to several GHz wide, giving multi-gigabit data rates. This supports IoT applications that move real video and sensor streams, not just small readings.
   - Massive device density — 5G targets about one million connected devices per square kilometre, which is exactly what a dense sensor deployment needs. Wide mmWave channels make that density practical.
   - Very low latency — under 1 ms in ideal conditions, which is what industrial control, autonomous vehicles and remote surgery require.
   - Precise sensing and positioning — the short wavelength gives fine range resolution, so mmWave radar is used for gesture recognition, occupancy and people counting, vital-sign monitoring, and automotive collision avoidance. This is a genuine IoT use of mmWave as a sensor rather than as a link.
   - Small antennas — because the wavelength is millimetres, dozens of antenna elements fit into a tiny module, enabling beamforming in a device the size of a coin.

   Typical IoT applications
   - Industrial IoT — wireless factory automation, machine vision, AGV control.
   - Smart city — high-density CCTV, traffic monitoring, connected intersections.
   - Automotive — V2X communication and in-cabin occupant sensing.
   - Healthcare — contactless monitoring of breathing and heart rate.
   - Smart home — presence detection and gesture control without a camera.
   - Fixed wireless access — replacing the last-mile fibre run to a building.

   Limitations
   - Very short range, typically a few hundred metres, so many small cells are needed.
   - Poor penetration — walls, glass, foliage, even a hand on the phone, block the signal. It is largely line-of-sight.
   - Rain and atmospheric absorption reduce range further; oxygen absorption peaks near 60 GHz.
   - Beamforming is mandatory to overcome path loss, which adds cost and complexity.
   - Higher power consumption, a real problem for battery-powered sensors — which is why low-rate IoT still uses sub-GHz LPWAN such as NB-IoT and LoRa, and mmWave is reserved for high-bandwidth or sensing roles.

3. **What is IoT? Brefly explain.** *[Mongla Port Authority Assistant Programmer 2023 compact it 571 (ET: N/A)]*

   Answer: IoT (Internet of Things) is a network of physical objects — sensors, appliances, vehicles, machines — that are embedded with electronics and connectivity so they can collect data, exchange it over the internet, and act on it, largely without human intervention.

   How it works
   ```
   Sensors -> Connectivity -> Data processing -> User interface / Action
   (collect)   (Wi-Fi, BLE,    (cloud or edge     (app, dashboard,
                NB-IoT, 5G)     analytics)         automatic control)
   ```
   - Step 1 — sensors measure something: temperature, motion, current, location, humidity.
   - Step 2 — a gateway or radio sends that data over the network.
   - Step 3 — cloud or edge software stores and analyses it, often with machine learning.
   - Step 4 — a result is shown to the user or fed back as an automatic action through an actuator.

   Key components
   - Things — the sensors and actuators.
   - Connectivity — Wi-Fi, Bluetooth/BLE, Zigbee, LoRaWAN, NB-IoT, 4G/5G.
   - Gateway — aggregates local devices and bridges them to the internet.
   - Cloud platform — storage, analytics, device management.
   - User interface — mobile app or web dashboard.

   Applications
   - Smart home — thermostats, lights, security cameras, door locks.
   - Healthcare — wearables, remote patient monitoring.
   - Agriculture — soil moisture sensors, automatic irrigation.
   - Industry (IIoT) — predictive maintenance from vibration data, asset tracking.
   - Smart city — traffic control, street lighting, waste management.
   - Retail and logistics — inventory tracking, cold-chain monitoring.

   Challenges
   - Security is the biggest issue: many devices ship with default passwords and are never patched, which is how the Mirai botnet was built.
   - Privacy, since IoT devices collect very personal data.
   - Interoperability between competing standards.
   - Power supply and battery life for remote sensors.
   - The sheer volume of data generated, which is why edge computing is used to filter it before it reaches the cloud.

4. **How to work WiMax technology?** *[Mongla Port Authority Assistant Programmer 2023 compact it 571 (ET: N/A)]*

   Answer: WiMAX (IEEE 802.16) delivers broadband wirelessly over a metropolitan area, using a point-to-multipoint radio link from a base station to subscriber equipment.

   How it works
   ```
      Internet
         |
      [ISP core]
         |
    [WiMAX Base Station]  <- tower, sectored antennas
        /    |    \
       /     |     \        radio link, up to 50 km
      /      |      \
    [CPE]  [CPE]   [CPE]    subscriber station at home or office
      |      |       |
     LAN    LAN     LAN
   ```
   - Step 1 — the base station connects to the ISP core by fibre or microwave backhaul.
   - Step 2 — it transmits over licensed or unlicensed spectrum. Two modes exist: line-of-sight at 10–66 GHz for long, fixed links, and non-line-of-sight at 2–11 GHz for ordinary subscribers.
   - Step 3 — the subscriber station (an outdoor antenna or an indoor modem) registers with the base station, is authenticated, and is allocated capacity.
   - Step 4 — the air interface uses OFDM (and OFDMA in 802.16e) to resist multipath, with adaptive modulation: 64-QAM close to the tower, dropping to QPSK at the edge where the signal is weak.
   - Step 5 — the MAC layer is connection-oriented and schedules transmissions, which is why WiMAX has real QoS classes for voice, video and best-effort data.
   - Step 6 — the subscriber station passes traffic to the customer's LAN over Ethernet or Wi-Fi.

   Key characteristics
   - Range up to 50 km, throughput up to about 70 Mbps shared per sector.
   - Fixed WiMAX is 802.16d; mobile WiMAX with handover is 802.16e.
   - Security: EAP authentication and AES encryption.

   Advantages and limitations
   - Advantages: covers a wide area without laying cable, quick to deploy, useful for rural and last-mile access, built-in QoS.
   - Limitations: bandwidth is shared, so per-user speed falls as subscribers increase; needs line of sight for the best rates; weather affects higher frequencies; and it was ultimately outcompeted by LTE and 5G, which had far greater carrier and handset support.

5. **Briefly describe the basis structure at a mobile cellular system with a proper figure.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 676 (ET: N/A)]*

   Answer: A mobile cellular system divides the coverage area into small regions called cells, each served by its own base station, so that the same frequencies can be reused in distant cells.

   Basic structure
   ```
           +----------------+        +-------------------+
           |  PSTN / Internet|<----->|   MSC             |
           +----------------+        |  Mobile Switching |
                                     |  Centre           |
                                     +---+-----+---------+
                                         |     |
                           +-------------+     +-------------+
                           |                                 |
                      +----v----+                       +----v----+
                      |  BSC    |                       |  BSC    |
                      | Base    |                       |         |
                      | Station |                       |         |
                      | Contrl. |                       |         |
                      +--+---+--+                       +----+----+
                         |   |                               |
                   +-----v+  +v-----+                   +----v----+
                   | BTS  |  | BTS  |                    |  BTS   |
                   +--+---+  +--+---+                   +----+----+
                      |         |                            |
                    (MS)      (MS)                          (MS)
                 mobile station (handset)

     Databases attached to the MSC:  HLR | VLR | AUC | EIR
   ```

   Cell layout — hexagons are used because they tile without gaps and approximate a circle
   ```
         / \ / \ / \
        | A | B | C |
         \ / \ / \ /
        | G | A | B |        same letter = same frequency group,
         / \ / \ / \         reused because the cells are far apart
        | F | E | D |
         \ / \ / \ /
   ```

   Components
   - MS (Mobile Station) — the handset with its SIM.
   - BTS (Base Transceiver Station) — the radio equipment and antennas at the tower; it defines one cell.
   - BSC (Base Station Controller) — controls several BTSs, manages radio channels, power control and handover between them.
   - MSC (Mobile Switching Centre) — the switching core; sets up calls, routes them, and connects to the PSTN and other networks.
   - HLR (Home Location Register) — permanent subscriber database.
   - VLR (Visitor Location Register) — temporary record of subscribers currently in this MSC's area.
   - AUC (Authentication Centre) — holds keys and authenticates the SIM.
   - EIR (Equipment Identity Register) — the IMEI list of allowed, blocked and stolen handsets.

   Key concepts
   - Frequency reuse — cells far enough apart use the same frequencies, which is what makes a limited spectrum serve millions of users.
   - Cell splitting — a busy cell is divided into smaller cells to add capacity.
   - Handover — an active call is transferred to a new cell as the user moves.
   - Roaming — service continues in another operator's network through HLR/VLR co-operation.

6. **How can you define IoT? What are the basic components of IoT?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 680 (ET: N/A)]*

   Answer:

   Definition of IoT
   - The Internet of Things is a network of physical objects embedded with sensors, software and connectivity, which collect and exchange data over the internet and act on it with little or no human involvement.
   - Its purpose is to make ordinary objects "smart": aware of their state and surroundings, and able to report or respond automatically.

   Basic components

   - Sensors and actuators (the "things")
     - Sensors measure the physical world: temperature, humidity, motion, light, current, GPS position, heart rate.
     - Actuators act on it: a relay switches a pump, a motor opens a valve, a lock engages.

   - Connectivity
     - Short range: Bluetooth/BLE, Zigbee, Z-Wave, Wi-Fi, NFC, RFID.
     - Long range and low power: LoRaWAN, Sigfox, NB-IoT, LTE-M.
     - High bandwidth: 4G, 5G, Ethernet, satellite for remote sites.

   - Gateway
     - Aggregates many local devices, converts protocols, and bridges them to the internet. It often performs edge processing so that only useful data is sent onward.

   - Data processing and cloud platform
     - Stores the data, runs analytics and machine learning, manages devices, applies rules and issues alerts. Examples: AWS IoT, Azure IoT Hub, Google Cloud IoT.
     - Edge computing does part of this near the device, to cut latency and bandwidth.

   - User interface
     - A mobile app or web dashboard for monitoring, visualisation and manual control.

   - Security layer
     - Device authentication, encrypted transport (TLS, DTLS), secure boot, firmware signing and over-the-air updates. This is the weakest area of most real deployments.

   Typical protocols: MQTT and CoAP for messaging, HTTP/REST for integration, and JSON for data format.

   ```
   [Sensors] -> [Gateway] -> [Network] -> [Cloud / Edge analytics] -> [App / Action]
       ^                                                                    |
       +--------------------- actuator command ----------------------------+
   ```

7. **(a) Write down the features of 4G wireless networks.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 695 (ET: N/A)]*

   Answer: 4G is the fourth generation of mobile networks, standardised as LTE and LTE-Advanced (3GPP Releases 8 and 10). It is the first generation to be entirely packet-switched.

   Features
   - All-IP network — voice, video and data all travel as IP packets. The old circuit-switched core disappears, and voice is carried as VoLTE.
   - High data rates — LTE offers up to about 100 Mbps while moving and 1 Gbps when stationary; LTE-Advanced raises this with carrier aggregation.
   - Low latency — around 30–50 ms, against 100–500 ms on 3G, which is what makes video calling and online gaming usable.
   - OFDMA on the downlink and SC-FDMA on the uplink, which resist multipath fading and use the spectrum efficiently.
   - MIMO — multiple antennas at both ends multiply capacity without extra spectrum.
   - Scalable bandwidth — channels from 1.4 MHz to 20 MHz, and carrier aggregation in LTE-A combines several carriers.
   - Flat network architecture — fewer nodes (eNodeB and the EPC) than 3G, which lowers latency and cost.
   - Seamless mobility — handover between cells and backward compatibility with 3G and 2G.
   - Better spectral efficiency and improved QoS classes for voice, video and best-effort data.
   - Security — mutual authentication and stronger encryption than 3G.

   Main network elements: UE (handset), eNodeB (base station), and the Evolved Packet Core made up of MME, S-GW, P-GW, HSS and PCRF.

   - Limitations that led to 5G: not enough capacity for the device density of IoT, latency still too high for industrial control, and limited spectrum below 6 GHz.

8. **5G প্রথম কত সালে ও কোথায় চালু হয়?** *[BWMRI Assistant Maintenance Engineer 2022 compact it 736 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   - The world's first commercial 5G service was launched on `3 April 2019` in `South Korea`. The three operators SK Telecom, KT and LG U+ switched on their networks simultaneously, making South Korea the first country with a nationwide 5G service.
   - Verizon in the United States launched in Chicago and Minneapolis on the same day, hours later, so South Korea is credited as first.
   - The first 5G handset was the Samsung Galaxy S10 5G, released at the same time.

   5G in Bangladesh
   - Teletalk launched 5G on `12 December 2021` at six sites, in partnership with Huawei — Tungipara in Gopalganj, the National Martyrs' Memorial at Savar, the Bangladesh Secretariat, the Prime Minister's Office, Dhanmondi 32 and Sher-e-Bangla Nagar.
   - The 5G spectrum auction for the private operators (Grameenphone, Robi, Banglalink) was held in March 2022.

   Background
   - 5G targets peak rates of up to 20 Gbps, latency under 1 ms, and about one million devices per square kilometre.
   - Its three service categories are eMBB (enhanced mobile broadband), URLLC (ultra-reliable low-latency communication) and mMTC (massive machine-type communication for IoT).

9. **(ক) Wi-Fi Network সম্পর্কে সংক্ষিপ্ত বিবরণ দিন। Wi-Fi Sensor Network এবং Ad Hoc Network এর মধ্যে পার্থক্য লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 769 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   Wi-Fi network
   - A wireless LAN based on the IEEE 802.11 family, connecting devices to a network through an access point without cables.
   - Frequency bands: 2.4 GHz (longer range, more interference), 5 GHz (faster, shorter range) and 6 GHz in Wi-Fi 6E and 7.
   - Range about 30–100 m indoors; speed from 54 Mbps (802.11g) to several Gbps (Wi-Fi 6/7).
   - Access method: CSMA/CA with RTS/CTS, since a radio cannot listen while it transmits.
   - Two modes: infrastructure mode, where everything goes through an access point, and ad hoc mode, where devices talk directly.
   - Security: WPA2 with AES, and WPA3 today. WEP is broken and must not be used.
   - Advantages: mobility, easy installation, no cabling cost. Disadvantages: shared bandwidth, interference, weaker security than wired, and range limits.

   Wireless Sensor Network vs Ad Hoc Network

   | Point | Wireless Sensor Network (WSN) | Ad Hoc Network (MANET) |
   |---|---|---|
   | Purpose | Sense the environment and report data | General-purpose communication between peers |
   | Nodes | Very many, small, cheap, often hundreds or thousands | Fewer, more capable devices — laptops, phones |
   | Traffic pattern | Many-to-one, all data flows to a sink or base station | Any-to-any, peer to peer |
   | Power | Battery, often not replaceable; energy efficiency dominates every design decision | Rechargeable; power matters less |
   | Mobility | Usually static once deployed | Usually mobile |
   | Data rate | Very low, a few kbps | Moderate to high |
   | Hardware | Limited CPU, tiny memory | Full computing devices |
   | Addressing | Often data-centric ("all temperature readings") rather than address-centric | Node addresses, like a normal network |
   | Redundancy | High — many nodes report overlapping data | Low, each node is distinct |
   | Example | Soil moisture monitoring in a field, structural health monitoring | Laptops sharing files with no router, military field network |

   - Common ground: both are wireless, both are infrastructure-less, and both use multi-hop routing. The essential difference is that a WSN exists to collect data under a severe energy budget, while a MANET exists to carry general traffic between mobile peers.

10. **Call Drop কী? এর কারণ গুলো উল্লেখ করুন।** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 810 (ET: IBA)]*

    Answer: (Answered in English, as required for IT topics.)

    What is call drop
    - A call drop is the unintentional termination of an ongoing mobile call by the network, before either party hangs up. It is a key quality indicator, measured as the Call Drop Rate — dropped calls divided by total successful calls, usually required to stay under about 2 percent.

    Causes

    Radio and coverage
    - Weak signal or a coverage hole — the user moves into a basement, lift or rural gap and the signal falls below the receiver's sensitivity.
    - Interference — co-channel and adjacent-channel interference from nearby cells, or external noise, corrupts the link.
    - Fading and multipath — reflections from buildings cause deep fades, particularly for a moving user.
    - Obstruction — thick walls, hills or dense foliage between handset and tower.

    Mobility
    - Handover failure — the call is not transferred in time as the user crosses a cell boundary, or the target cell has no free channel. Fast movement, as on a highway, makes this worse.
    - Ping-pong handover between two cells of similar strength.

    Capacity and network
    - Congestion — no free traffic channel in the target cell during peak hours.
    - Insufficient base station capacity or spectrum for the subscriber density.
    - Backhaul failure or congestion between the BTS and the core.
    - Equipment faults, power failure at the tower, or misconfigured parameters and antenna tilt.

    Handset side
    - Low battery, faulty antenna, an outdated or defective handset, or SIM problems.
    - The user's hand covering the antenna, especially at higher frequencies.

    Remedies
    - Add or split cells, deploy small cells, repeaters and in-building DAS.
    - Optimise antenna tilt, azimuth and power; retune neighbour lists and handover thresholds.
    - Add spectrum and capacity; upgrade backhaul.
    - Regular drive testing and network monitoring to find weak areas.

11. **LTE কী? এর এডভান্সড প্রযুক্তির নাম লিখুন।** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 811 (ET: IBA)]*

    Answer: (Answered in English, as required for IT topics.)

    What is LTE
    - LTE (Long Term Evolution) is the 3GPP standard for high-speed mobile broadband, introduced in Release 8 (2008) and commonly marketed as 4G.
    - It is an all-IP, packet-switched network — the circuit-switched core disappears, and voice is carried as VoLTE.
    - Peak rates: about 100 Mbps download and 50 Mbps upload in Release 8; latency around 30–50 ms.
    - Radio technology: OFDMA on the downlink, SC-FDMA on the uplink, MIMO antennas, and scalable channel bandwidth from 1.4 to 20 MHz.
    - Architecture: UE (handset) -> eNodeB (base station) -> EPC (Evolved Packet Core: MME, S-GW, P-GW, HSS, PCRF). It is a flat architecture with fewer nodes than 3G, which is why latency is low.

    Advanced LTE technologies
    - `LTE-Advanced` (3GPP Release 10) — the true IMT-Advanced 4G. It adds:
      - Carrier Aggregation — combines up to five 20 MHz carriers for 100 MHz total, giving up to 1 Gbps.
      - Higher-order MIMO — 8×8 downlink, 4×4 uplink.
      - Relay nodes and heterogeneous networks (macro cells plus small cells).
      - CoMP (Coordinated Multi-Point), where several base stations serve one user together.
      - eICIC, to control interference between macro and small cells.
    - `LTE-Advanced Pro` (Release 13 and later), marketed as 4.5G — adds License Assisted Access (using unlicensed 5 GHz spectrum), massive carrier aggregation of up to 32 carriers, NB-IoT and LTE-M for machine communication, and 256-QAM.
    - `VoLTE` — voice over the LTE packet network, giving HD voice and much faster call setup.
    - `LTE-U / LAA` — LTE operating in unlicensed spectrum alongside Wi-Fi.
    - These features are the bridge to 5G NR, which reuses many of the same ideas at a larger scale.

12. **Wi-Fi, Bluetooth, Wi-Max, Cellure network এইগুলোকে দূরত্বের ক্রমানুসারে ছোট থেকে বড় এর দিক অনুসারে লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 867 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) In order of coverage distance, smallest to largest:

    ```
    1. Bluetooth  ->  2. Wi-Fi  ->  3. WiMAX  ->  4. Cellular network
       (~10 m)         (~100 m)      (~50 km)       (nationwide)
    ```

    | Order | Technology | Standard | Typical range | Network type |
    |---|---|---|---|---|
    | 1 | Bluetooth | IEEE 802.15.1 | 10 m (Class 2), up to 100 m (Class 1) | PAN |
    | 2 | Wi-Fi | IEEE 802.11 | 30–100 m indoors, a few hundred metres outdoors | LAN |
    | 3 | WiMAX | IEEE 802.16 | Up to 50 km from the base station | MAN |
    | 4 | Cellular (3G/4G/5G) | 3GPP | Cells of 1–35 km, joined into nationwide coverage | WAN |

    - The pattern to remember: as range grows, per-user speed and power efficiency generally fall, and the cost of the infrastructure rises. Bluetooth is cheapest and shortest; a cellular network is the most expensive and reaches furthest.
    - Note that 5G mmWave is an exception to the range pattern — it is very fast but reaches only a few hundred metres, which is why it needs dense small cells.

13. **(c) Difference between broadband Wi-Fi and Wi-Max communication technology.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 896 (ET: N/A)]*

    Answer: Difference between broadband Wi-Fi and WiMAX.

    | Point | Wi-Fi | WiMAX |
    |---|---|---|
    | Standard | IEEE 802.11 | IEEE 802.16 |
    | Network type | WLAN — local area | WMAN — metropolitan area |
    | Range | 30–100 m indoors | Up to 50 km from the base station |
    | Speed | 54 Mbps to several Gbps, over a short distance | Up to about 70 Mbps, shared across a large area |
    | Frequency | 2.4, 5 and 6 GHz, mostly unlicensed | 2–11 GHz (non line of sight) and 10–66 GHz (line of sight), mostly licensed |
    | MAC method | CSMA/CA — contention based, so performance falls as users increase | Scheduled and connection-oriented — the base station allocates slots |
    | QoS | Best effort; QoS added later and weak | Built into the standard, with defined service classes |
    | Scalability | Tens of users per access point | Hundreds to thousands per base station |
    | Mobility | Limited; roaming between access points only | 802.16e supports mobility with handover |
    | Purpose | Connect devices to a local network | Last-mile broadband access across a city |
    | Cost | Very cheap equipment | Expensive base stations, licensed spectrum |
    | Security | WPA2 / WPA3 | EAP authentication with AES |

    Key distinction
    - Wi-Fi is a LAN technology: it gives you the last few metres inside a building, and it needs some other connection to reach the internet.
    - WiMAX is an access technology: it replaces the cable from the ISP to your building, covering kilometres.
    - In practice they are complementary — a WiMAX (or now LTE/5G) link brings broadband to the premises, and Wi-Fi distributes it inside.

14. **What is wireless network system? Why CSMA/CA used instead of CSMA/CD?** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922-923 (ET: N/A)]*

    Answer:

    What is a wireless network system
    - A network in which devices communicate over radio waves rather than physical cables. Data is modulated onto a carrier frequency, transmitted through the air, and demodulated by the receiver.
    - Types by range: PAN (Bluetooth), WLAN (Wi-Fi), WMAN (WiMAX) and WWAN (cellular 3G/4G/5G), plus satellite.
    - Components: wireless NICs, access points or base stations, antennas, and a wired backbone behind them.
    - Advantages: mobility, no cabling cost, quick deployment, easy to extend.
    - Disadvantages: shared bandwidth, interference, weaker security, range limited by obstacles, and higher error rates than cable.

    Why CSMA/CA is used instead of CSMA/CD
    - CSMA/CD (Collision Detection) works on wired Ethernet because a station can listen to the cable while it transmits and notice a collision. On radio this is impossible, for several reasons.

    - A radio cannot listen while transmitting. Its own transmitted signal is millions of times stronger than any incoming signal, so a collision at the receiver is simply not detectable at the sender. Without detection, CD has nothing to work with.

    - The hidden terminal problem. A and C can both reach the access point B, but they cannot hear each other. Each senses the medium as idle and transmits, so their signals collide at B, and neither sender ever knows.
    ```
       A  ---- B ---- C
       |               |
       +--- cannot hear each other ---+
    ```
    CSMA/CA solves this with the optional RTS/CTS exchange: A sends Request To Send, B replies Clear To Send, which C also hears, so C stays quiet.

    - Signal strength varies with distance and fading, so "the medium is busy" is not a reliable global judgement on radio the way it is on a shared cable.

    - Collisions on radio are more expensive. A frame lost in the air must be retransmitted end to end, so it is better to avoid collisions in advance than to detect them afterwards.

    How CSMA/CA avoids collisions
    - Sense the channel. If busy, wait.
    - If idle, wait a DIFS interval, then a random backoff time; whichever station's timer expires first transmits, so two waiting stations rarely start together.
    - Optionally exchange RTS/CTS, which also reserves the medium for a stated duration through the NAV (virtual carrier sense).
    - The receiver returns an ACK for every frame. No ACK means the frame was lost, so the sender doubles its contention window and retries.

15. **Write about 5G disadvantages: (a) Increased High Costs (b) Draining Battery of devices. (c) Increased infrastructure development cost** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 928 (ET: CTI)]*

    Answer: The three named disadvantages of 5G, explained.

    (a) Increased high costs
    - Spectrum is expensive: 5G licences have cost operators billions of dollars worldwide, and that cost is passed to subscribers.
    - 5G handsets cost more than 4G handsets, because they need extra radios, more antennas and more processing.
    - Data plans are typically priced higher, and per-user revenue does not rise as fast as the investment, which is why many operators have been slow to roll out.
    - Older equipment must be replaced rather than upgraded, so both the operator and the customer face a hardware refresh.

    (b) Draining the battery of devices
    - A 5G modem consumes more power than a 4G modem, particularly on mmWave, where the phone must drive a beamforming antenna array.
    - Higher data rates mean the screen and processor also work harder, since more content is downloaded and rendered.
    - Devices frequently switch between 5G and 4G at the edge of coverage, and that constant searching and re-registration is itself power-hungry.
    - Handsets running 5G are noticeably warmer, and heat further reduces battery life and can force the phone to throttle.
    - Mitigations: DRX (discontinuous reception), better modem process nodes, and dynamic switching to 4G when 5G brings no benefit.

    (c) Increased infrastructure development cost
    - mmWave has very short range, a few hundred metres, and does not pass through walls. Covering a city therefore needs a very dense grid of small cells rather than a few tall towers.
    - Every small cell needs a site, power and fibre backhaul. The fibre trenching alone is often the largest single cost.
    - Site acquisition, rent, permissions and municipal approvals multiply with the number of sites.
    - Rural coverage is economically difficult, because the same dense infrastructure cannot be justified for few subscribers, which widens the digital divide.
    - Operating cost rises too: more sites mean more electricity, more maintenance and more monitoring.

    Other commonly cited disadvantages
    - Limited coverage in the early years, poor building penetration, upload speeds lower than download, and public concern (not supported by evidence) about radiation.

16. **Make a list of LTE Network elements.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 988 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

    Answer: LTE network elements, grouped into the radio access network and the Evolved Packet Core.

    Radio side — E-UTRAN
    - `UE (User Equipment)` — the handset or modem, containing the USIM.
    - `eNodeB (Evolved Node B)` — the base station. Unlike 3G it has no separate controller: radio resource management, scheduling, handover decisions and header compression all happen in the eNodeB itself. eNodeBs talk to each other directly over the X2 interface.

    Core side — EPC (Evolved Packet Core)
    - `MME (Mobility Management Entity)` — the control-plane brain. It handles attach and detach, authentication (with the HSS), bearer setup, tracking area updates, paging and handover signalling. It carries no user data.
    - `S-GW (Serving Gateway)` — the user-plane anchor for handovers between eNodeBs. All user packets pass through it, and it buffers downlink data while a device is idle.
    - `P-GW (PDN Gateway)` — the gateway to external packet networks (the internet, an IMS network). It allocates the UE's IP address, enforces policy, performs charging, and does deep packet inspection and filtering.
    - `HSS (Home Subscriber Server)` — the central subscriber database: identities, keys, subscribed services and current location. It replaces the HLR/AUC of earlier generations.
    - `PCRF (Policy and Charging Rules Function)` — decides QoS and charging policy per flow, and instructs the P-GW to enforce it.

    Additional elements
    - `IMS` — the IP Multimedia Subsystem that provides VoLTE voice and messaging.
    - `ANDSF` — helps the UE choose between LTE and Wi-Fi.
    - `eMBMS` — multicast and broadcast over LTE.

    ```
    UE --- eNodeB --- S-GW --- P-GW --- Internet
              |         |        |
              +-- MME --+        |
                  |              |
                 HSS           PCRF
    ```
    - Interfaces to remember: Uu (UE to eNodeB), S1-MME (eNodeB to MME), S1-U (eNodeB to S-GW), X2 (eNodeB to eNodeB), S5/S8 (S-GW to P-GW), S6a (MME to HSS).

17. **Explain Bluetooth, Wi-Fi and Cellular Network.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1023 (ET: N/A)]*

    Answer:

    Bluetooth
    - A short-range wireless technology (IEEE 802.15.1) for connecting personal devices directly to each other — a PAN.
    - Operates in the 2.4 GHz ISM band using frequency hopping spread spectrum, changing channel 1600 times a second to resist interference.
    - Range: about 10 m (Class 2) or up to 100 m (Class 1). Speed: 1–3 Mbps classic, 2 Mbps for BLE.
    - Topology: a piconet of one master and up to seven active slaves; overlapping piconets form a scatternet.
    - BLE (Bluetooth Low Energy) is the low-power variant used by wearables and IoT sensors, where a coin cell lasts for years.
    - Uses: headsets, keyboards, car audio, fitness bands, file transfer.

    Wi-Fi
    - A wireless LAN technology (IEEE 802.11) that connects devices to a network through an access point.
    - Bands: 2.4 GHz, 5 GHz and 6 GHz (Wi-Fi 6E/7). Range 30–100 m indoors. Speed from 54 Mbps to several Gbps.
    - Access method: CSMA/CA, with optional RTS/CTS to handle hidden terminals.
    - Two modes: infrastructure (through an access point) and ad hoc (device to device).
    - Security: WPA2-AES and WPA3. Uses: home and office internet, hotspots, campus networks.

    Cellular network
    - A wide-area mobile network in which the coverage area is divided into cells, each with a base station, so that frequencies can be reused in distant cells.
    - Elements: mobile station, BTS/eNodeB, BSC, MSC, and databases HLR, VLR, AUC and EIR.
    - Generations: 1G analogue voice, 2G digital voice and SMS (GSM), 3G mobile data (UMTS), 4G all-IP broadband (LTE), 5G with very high speed, low latency and massive IoT density.
    - Key mechanisms: frequency reuse, cell splitting, handover as the user moves, and roaming between operators.
    - Uses: voice, SMS, mobile internet, IoT connectivity anywhere with coverage.

    Comparison

    | Point | Bluetooth | Wi-Fi | Cellular |
    |---|---|---|---|
    | Range | 10–100 m | 30–100 m | Kilometres, nationwide |
    | Network | PAN | LAN | WAN |
    | Power | Very low | Moderate | High |
    | Cost | Very low | Low | Subscription based |
    | Mobility | Minimal | Within one building | Full, with handover |

18. **(b) How cellular networks handoff works?** *[BPSC Assistant Programmer (ICT) 2019 compact it 1142 (ET: N/A)]*

    Answer: Handoff (handover) is the process of transferring an active call or data session from one cell to another as the subscriber moves, without interrupting the connection.

    How it works
    - Step 1 — Measurement. The handset continuously measures the signal strength and quality of its serving cell and of neighbouring cells, and reports these measurements to the network.
    - Step 2 — Decision. The network compares the readings against thresholds. When a neighbour is stronger than the serving cell by a defined margin, for a defined time (the hysteresis and time-to-trigger, which prevent ping-ponging), a handover is decided.
    - Step 3 — Preparation. The network asks the target cell to reserve a channel and resources. If the target has no capacity, the handover fails and the call may drop.
    - Step 4 — Execution. The network sends a handover command to the handset, telling it which cell and channel to move to. The handset retunes.
    - Step 5 — Completion. The handset registers with the target cell, the path is switched so that traffic now flows through the new cell, and the old cell releases its resources.

    ```
       Cell A                         Cell B
      (serving)                      (target)
         ((o))                         ((o))
           \                             /
            \      user moves -->       /
             \___________ MS __________/
       signal falling            signal rising
       -> measurement report -> decision -> resource reservation
       -> handover command -> retune -> path switch -> release
    ```

    Types of handoff
    - Hard handover (break-before-make) — the old link is released before the new one is made. Used in GSM and LTE; there is a very brief gap.
    - Soft handover (make-before-break) — the handset is connected to two cells at once and the network combines the signals. Used in CDMA and 3G; more robust but uses more resources.
    - Softer handover — between two sectors of the same base station.
    - Intra-cell, inter-cell, inter-BSC, inter-MSC and inter-system (LTE to 3G) handovers, depending on how far the boundary crossing reaches.

    Reasons for handover
    - Falling signal strength as the user moves away, interference, congestion in the current cell (load balancing), or the user crossing into a different technology's coverage.

    Why it can fail
    - The target cell is full, the measurement report is lost, the user moves too fast for the decision to complete, or neighbour lists and thresholds are misconfigured. A failed handover is one of the main causes of call drops.

19. **Write the basic function of GGSN and SGSN. Describe LTE radio technology.** *[BTRC Assistant Director (Technical) 2019 compact it 1145 (ET: N/A)]*

    Answer:

    Basic function of SGSN and GGSN
    These are the two packet-switched core nodes of GPRS, EDGE and UMTS. In LTE their roles were taken over by the S-GW and P-GW respectively.

    `SGSN (Serving GPRS Support Node)`
    - Serves the mobile in its current location, and is the packet equivalent of the MSC.
    - Delivers packets to and from the mobiles in its service area.
    - Performs mobility management: attach and detach, location tracking, routing area updates and handovers.
    - Authenticates the subscriber against the HLR and handles ciphering.
    - Performs session management and creates the PDP context.
    - Collects charging data for the traffic it carries.

    `GGSN (Gateway GPRS Support Node)`
    - The gateway between the mobile network and external packet networks such as the internet or a corporate intranet.
    - Allocates the IP address to the mobile.
    - Converts GPRS packets from the SGSN into the correct external format and routes them out; incoming packets are tunnelled back to the correct SGSN.
    - Enforces policy and filtering, and performs charging and billing for external data.
    - Hides mobility from the outside world: to the internet, the mobile appears at a fixed point.

    ```
    MS -- BTS -- BSC -- SGSN -- GGSN -- Internet
                         |         |
                        HLR      charging
    ```
    - Mapping to LTE: SGSN -> MME (control) plus S-GW (user plane); GGSN -> P-GW.

    LTE radio technology
    - `OFDMA on the downlink` — the channel is split into many narrow orthogonal subcarriers spaced 15 kHz apart. Different users are given different subcarrier groups and time slots. Narrow subcarriers make each one flat-fading, which defeats multipath and removes the need for a complex equaliser.
    - `SC-FDMA on the uplink` — a single-carrier variant chosen because it has a much lower peak-to-average power ratio than OFDMA, which lets the handset's power amplifier run efficiently and saves battery.
    - `MIMO` — multiple antennas at both ends. Spatial multiplexing sends several data streams at once to multiply throughput; transmit diversity improves reliability at the cell edge; beamforming focuses energy towards the user. LTE supports up to 4×4, LTE-Advanced up to 8×8.
    - `Scalable bandwidth` — 1.4, 3, 5, 10, 15 or 20 MHz, so LTE fits into whatever spectrum an operator holds. LTE-Advanced aggregates up to five carriers.
    - `Adaptive modulation and coding` — QPSK, 16-QAM and 64-QAM (256-QAM in later releases), chosen per user according to channel quality reported by the CQI.
    - `Fast scheduling` — the eNodeB schedules resource blocks every 1 ms, exploiting the fact that different users experience good channel conditions at different moments.
    - `HARQ` — hybrid ARQ combines retransmission with error-correction coding, so a retransmitted block is combined with the failed one rather than replacing it.
    - `Frame structure` — 10 ms radio frame, ten 1 ms subframes; the smallest allocation unit is a resource block of 12 subcarriers × 0.5 ms.
    - Duplexing: both FDD (separate uplink and downlink bands) and TDD (one band shared in time) are supported.

## Networking Devices (19)

1. Describe the functions of a Switch and a Router and explain two key differences between these networking devices. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

   Answer:

   Functions of a switch (Layer 2)
   - Learns the MAC address of every device by reading the source address of incoming frames, and stores it against a port in the MAC address table.
   - Forwards each frame only out of the port where the destination MAC lives, instead of flooding it everywhere.
   - Floods a frame out of all ports when the destination MAC is unknown, or when it is a broadcast or multicast.
   - Gives every port its own collision domain, so full-duplex operation is possible and collisions disappear.
   - Runs Spanning Tree Protocol to prevent loops, supports VLANs, port security and QoS on a managed switch.

   Functions of a router (Layer 3)
   - Connects different networks and forwards packets between them using the destination IP address.
   - Builds and maintains a routing table, learned statically or through RIP, OSPF, EIGRP or BGP, and chooses the best path by longest prefix match.
   - Blocks broadcasts, so each interface bounds its own broadcast domain.
   - Performs NAT, DHCP service, ACL filtering, fragmentation and TTL decrement.
   - Rewrites the Layer 2 header at every hop while leaving the IP addresses unchanged.

   Two key differences

   | Point | Switch | Router |
   |---|---|---|
   | Layer and address used | Layer 2, forwards on `MAC address` | Layer 3, forwards on `IP address` |
   | Domains | Separates collision domains but keeps one broadcast domain | Separates both collision and broadcast domains |

   - Third difference worth stating: a switch connects devices `within` one network, while a router connects `different` networks — which is why a LAN needs a switch and internet access needs a router.

2. **Briefly describe the following network devices: Repeater, Hub, Bridge, Switch and Router.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 325 (ET: BIBM)]*

   Answer:

   Repeater — Layer 1
   - Receives a weakened signal, regenerates and retimes it, and sends it on. It extends the distance a segment can cover, for example beyond the 100 m limit of UTP.
   - It has two ports, understands nothing about addresses, and simply amplifies everything — including noise and collisions.

   Hub — Layer 1
   - A multi-port repeater. A frame arriving on one port is sent out of every other port.
   - All ports share one collision domain and one broadcast domain, so it works in half duplex and uses CSMA/CD. Performance collapses as devices are added.
   - Obsolete today; switches replaced hubs entirely.

   Bridge — Layer 2
   - Connects two LAN segments and forwards frames between them based on MAC addresses.
   - It learns which addresses live on which side and filters traffic, so local traffic stays local. This splits the collision domain in two while keeping one broadcast domain.
   - Usually has two ports; a switch is the modern multi-port version.

   Switch — Layer 2
   - A multi-port bridge with hardware forwarding. It learns MAC addresses into a table and sends each frame only to the correct port.
   - Every port is its own collision domain, so full duplex is possible and there are no collisions. All ports remain in one broadcast domain unless VLANs are configured.
   - Managed switches add VLANs, STP, port security, QoS and link aggregation.

   Router — Layer 3
   - Connects different networks and forwards packets using the destination IP address and a routing table.
   - It does not forward broadcasts, so it separates broadcast domains as well as collision domains.
   - Also performs NAT, DHCP, ACL filtering and fragmentation, and runs routing protocols.

   Summary

   | Device | Layer | Address used | Collision domains | Broadcast domains |
   |---|---|---|---|---|
   | Repeater | 1 | None | 1 | 1 |
   | Hub | 1 | None | 1 | 1 |
   | Bridge | 2 | MAC | One per port | 1 |
   | Switch | 2 | MAC | One per port | 1 (or one per VLAN) |
   | Router | 3 | IP | One per port | One per interface |

3. **How many collision domians are created when you segment a network with a 12-port switch?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

   Answer: A 12-port switch creates `12 collision domains` — one per port.

   Reason
   - A switch gives each port its own dedicated bandwidth and its own collision domain. Two devices on different ports can transmit at the same instant without colliding, because the switch buffers and forwards each frame independently.
   - With full-duplex links there are effectively no collisions at all, but the count of collision domains is still one per port.

   Broadcast domains
   - The same switch creates only `1 broadcast domain`, because a switch forwards broadcasts out of every port. Only a router — or VLANs configured on the switch — can split the broadcast domain.
   - If the 12 ports were divided into 3 VLANs, there would be 12 collision domains and 3 broadcast domains.

   Comparison

   | Device | Collision domains | Broadcast domains |
   |---|---|---|
   | 12-port hub | 1 | 1 |
   | 12-port switch | `12` | `1` |
   | 12-port switch with 3 VLANs | 12 | 3 |
   | Router with 12 interfaces | 12 | 12 |

4. **Difference among Switch, Bridge and Router.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 524 (ET: MIST)]*

   Answer:

   | Point | Bridge | Switch | Router |
   |---|---|---|---|
   | OSI layer | 2 (Data Link) | 2 (Data Link) | 3 (Network) |
   | Address used | MAC | MAC | IP |
   | Ports | Usually 2 | Many — 8, 24, 48 | Few, typically 2–8 |
   | Forwarding | Software based | Hardware (ASIC), very fast | Software and hardware, slower per packet |
   | Purpose | Joins two LAN segments | Connects many devices in one LAN | Connects different networks |
   | Collision domain | One per port | One per port | One per interface |
   | Broadcast domain | One (shared) | One, or one per VLAN | One per interface — it blocks broadcasts |
   | Routing table | No | No (a Layer 3 switch does) | Yes, with RIP, OSPF, BGP |
   | NAT / DHCP / firewall | No | No | Yes |
   | Speed | Slow | Very fast | Slower, because it inspects Layer 3 |
   | Cost | Low | Moderate | High |

   Short summary
   - A bridge is the ancestor: two ports, learns MAC addresses, splits a collision domain.
   - A switch is a multi-port bridge in hardware — it is what every LAN uses today.
   - A router works one layer higher, joining separate networks and stopping broadcasts. It is what connects the LAN to the internet.

5. **Differentiate between Collision Domain and Broadcast Domain in computer network. What is the function of DNS and DHCP?** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 535 (ET: MIST)]*

   Answer:

   (a) Collision domain vs broadcast domain

   | Point | Collision domain | Broadcast domain |
   |---|---|---|
   | Definition | The set of devices whose frames can collide with each other | The set of devices that receive a broadcast sent by any one of them |
   | Layer | Physical / Data Link | Data Link / Network |
   | Caused by | Shared medium and half duplex | The nature of a broadcast address |
   | Broken by | Switch, bridge, router | Router, or VLANs on a switch |
   | Not broken by | Hub, repeater | Hub, switch, bridge |
   | Address | — | FF:FF:FF:FF:FF:FF or 255.255.255.255 |
   | Effect of being large | Many collisions, retransmissions, poor throughput | Broadcast storms, wasted CPU on every host |

   Device summary

   | Device | Collision domains | Broadcast domains |
   |---|---|---|
   | Hub (8 ports) | 1 | 1 |
   | Switch (8 ports) | 8 | 1 |
   | Switch with 3 VLANs | 8 | 3 |
   | Router (4 interfaces) | 4 | 4 |

   (b) Function of DNS
   - Translates domain names into IP addresses (A and AAAA records) and IP addresses back into names (PTR records).
   - Routes email using MX records, supports aliases with CNAME, and distributes load across servers.
   - Works hierarchically — root, TLD, authoritative — and caches answers for the TTL. Port 53, UDP for queries and TCP for zone transfers.

   (c) Function of DHCP
   - Automatically assigns an IP address, subnet mask, default gateway and DNS servers to a device joining the network.
   - Uses the DORA exchange — Discover, Offer, Request, Acknowledge — on UDP ports 67 and 68.
   - Leases addresses for a limited time and reuses them, removing manual configuration and duplicate-address errors.

6. **Write down the difference between gateway and firewall.** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 476 (ET: N/A)]*

   Answer:

   | Point | Gateway | Firewall |
   |---|---|---|
   | Purpose | Connects two networks that use different protocols or architectures, translating between them | Controls and filters traffic to protect a network from unauthorised access |
   | Main job | Connectivity and protocol conversion | Security enforcement |
   | OSI layer | Can operate at all seven layers | Layer 3 and 4 for a packet filter, up to Layer 7 for an NGFW or WAF |
   | Traffic handling | Passes traffic through, converting formats | Permits or denies traffic against a rule set |
   | Decision basis | Protocol and address translation rules | Source, destination, port, protocol, state, and content |
   | Direction | Usually bidirectional pass-through | Inspects both directions, blocking what is not allowed |
   | Examples | Default gateway (router), VoIP gateway (IP to PSTN), email gateway, API gateway | Packet filter, stateful firewall, proxy firewall, NGFW, WAF |
   | Without it | Two dissimilar networks cannot communicate | The network is exposed to attack |

   Relationship
   - They are complementary, not alternatives. A gateway makes communication possible; a firewall decides which of that communication is allowed.
   - In practice a single box often does both: a home router is a gateway (NAT to the ISP) and a firewall (blocking unsolicited inbound traffic) at the same time. In an enterprise a "security gateway" or UTM device combines routing, NAT, firewall, IPS and content filtering.

7. **What is gateway? Is router and gateway have any difference?** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*

   Answer:

   What is a gateway
   - A gateway is a device that joins two networks that use different protocols, architectures or data formats, and translates between them so they can communicate.
   - It can operate at any layer of the OSI model, up to Layer 7, because full protocol conversion may need the payload to be rewritten.
   - Examples: a VoIP gateway between an IP network and the PSTN, an email gateway between SMTP and a proprietary mail system, an IoT gateway between Zigbee sensors and the internet, and an API gateway in front of microservices.
   - The `default gateway` on a PC is a special, common case: it is simply the router the host sends traffic to when the destination is outside its own subnet.

   Is there a difference from a router?
   - Yes. Every router is a kind of gateway, but not every gateway is a router.

   | Point | Router | Gateway |
   |---|---|---|
   | Primary job | Forward packets between networks by IP address | Translate between different protocols or architectures |
   | Requirement | Both networks must use the same protocol suite (IP) | The networks may use entirely different protocols |
   | OSI layer | Layer 3 | Any layer, up to Layer 7 |
   | Complexity | Reads the IP header only | May rewrite the entire message |
   | Speed | Fast, hardware assisted | Slower, because of translation |
   | Example | Joining 192.168.1.0/24 to 10.0.0.0/8 | Joining an IP network to the PSTN |

   Why the terms are used interchangeably
   - In an IP-only world, the device you send off-network traffic to is a router, and it is conventionally called the "default gateway". So in everyday networking the two words describe the same box. The distinction only becomes real when actual protocol translation is involved.

8. **অথবা, (ক) ডেটা ট্রান্সমিশনে Router ও Gateway এর মধ্যে কোনটি অধিকতর সুবিধাজনক-মতামত ব্যক্ত করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 615 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Which is more advantageous for data transmission, a router or a gateway?

   The short answer
   - For ordinary data transmission on an IP network, a `router is more advantageous`. A gateway is only preferable when the two networks genuinely speak different protocols.

   Reasons a router is better for normal transmission

   | Point | Router | Gateway |
   |---|---|---|
   | Speed | Very fast — reads only the IP header, and forwarding is done in hardware | Slower — may have to parse and rewrite the whole message |
   | Complexity | Simple and well standardised | Complex, often application specific |
   | Cost | Lower | Higher |
   | Scalability | Handles millions of packets per second | Becomes a bottleneck under load |
   | Reliability | Mature protocols, well understood failure modes | More moving parts, more failure points |
   | Standardisation | Universal — IP, OSPF, BGP | Often proprietary to the pair of protocols involved |

   When a gateway is the better choice
   - The two networks use different protocol suites, for example an IP network and the PSTN, or a Zigbee sensor network and the internet. A router simply cannot do this.
   - Data format conversion is required, such as an email gateway or a protocol translator between an old mainframe system and a modern one.
   - Application-layer inspection or mediation is needed, as with an API gateway or a security gateway.

   Conclusion
   - If both networks speak IP — which is almost always the case today — use a router: it is faster, cheaper, simpler and more scalable.
   - Use a gateway only where translation is unavoidable, accepting the performance cost as the price of connectivity that would otherwise be impossible.
   - In practice modern devices blur the line: a single enterprise box routes, does NAT, filters and translates, so the real design question is which functions you enable rather than which device you buy.

9. **Write the Difference among Network Switch, Hub and Router.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1023 (ET: N/A)], [DESCO Sub-Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)], [BMA Signal Assistant Engineer (Computer) 2021 compact it 933 (ET: BUET)]*

   Answer:

   | Point | Hub | Switch | Router |
   |---|---|---|---|
   | OSI layer | 1 — Physical | 2 — Data Link | 3 — Network |
   | Address used | None | MAC address | IP address |
   | Forwarding | Broadcasts to all ports | Sends only to the correct port | Routes between networks by best path |
   | Intelligence | None | Learns a MAC address table | Maintains a routing table |
   | Collision domains | 1 for the whole device | One per port | One per interface |
   | Broadcast domains | 1 | 1 (or one per VLAN) | One per interface |
   | Duplex | Half only | Full duplex | Full duplex |
   | Bandwidth | Shared among all ports | Dedicated per port | Depends on the link |
   | Security | None — every device sees every frame | Better, frames go only where needed | Best — ACLs, NAT, firewall |
   | Speed | Slowest | Very fast (hardware ASIC) | Slower per packet, more processing |
   | Cost | Cheapest | Moderate | Highest |
   | Use | Obsolete | Connects devices within a LAN | Connects different networks, LAN to internet |

   In one line each
   - Hub — a dumb repeater that shouts everything to everyone.
   - Switch — learns who is where and speaks only to the right port.
   - Router — knows about whole networks and finds the path between them.

10. **(iii) Router and Gateway এর ফাংশন লিখুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 789 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    Functions of a router
    - Forwards packets between different networks using the destination IP address.
    - Maintains a routing table, learned statically or through RIP, OSPF, EIGRP or BGP, and selects the best path by longest prefix match.
    - Determines the path — choosing the best of several possible routes by metric.
    - Blocks broadcasts, so each interface is a separate broadcast domain.
    - Performs NAT, translating private addresses to a public one.
    - Acts as a DHCP server, handing out addresses on the LAN.
    - Filters traffic with access control lists, and often includes firewall functions.
    - Fragments packets that exceed the next link's MTU, and decrements the TTL to kill looping packets.
    - Rewrites the Layer 2 header at every hop while leaving the IP header addresses unchanged.

    Functions of a gateway
    - Connects two networks that use different protocols or architectures, and translates between them.
    - Converts data formats, character sets and message structures where required.
    - Can operate at every layer up to Layer 7, since full conversion may require rewriting the payload.
    - Acts as the entry and exit point for a network — the `default gateway` is the router a host uses for anything outside its own subnet.
    - Often adds security functions: filtering, authentication and logging at the network boundary.
    - Examples: VoIP gateway (IP to PSTN), email gateway, IoT gateway, API gateway, payment gateway.

    Relationship
    - Every router is a gateway, but a gateway may do far more than route: it may translate protocols entirely. On an all-IP network the two words are used for the same device.

11. **Write down the difference between Hub and Switch.** *[DMLC Assistant Teacher (ICT) 2021 compact it 825 (ET: N/A)]*

    Answer:

    | Point | Hub | Switch |
    |---|---|---|
    | OSI layer | 1 — Physical | 2 — Data Link |
    | Address used | None | MAC address |
    | Frame handling | Broadcasts to every port | Forwards only to the destination port |
    | Intelligence | None; it is a multi-port repeater | Learns and stores a MAC address table |
    | Collision domain | One for the whole device | One per port |
    | Duplex | Half duplex only, uses CSMA/CD | Full duplex, so no collisions |
    | Bandwidth | Shared — a 100 Mbps hub with 10 users gives about 10 Mbps each | Dedicated — every port gets the full 100 Mbps |
    | Security | Poor; any device can sniff all traffic | Better; frames go only where they are needed |
    | Performance | Falls sharply as devices are added | Stays high |
    | Cost | Cheaper | Slightly more expensive |
    | Status | Obsolete | Standard in every network today |

    Example
    - On a 100 Mbps hub with 10 active users, all 10 share one 100 Mbps collision domain, so each gets roughly 10 Mbps and collisions are constant.
    - On a 100 Mbps switch, each of the 10 users has a private 100 Mbps full-duplex link and there are no collisions at all.

12. **Wi-Fi access point বলতে কী বুঝানো হয়? Router and Switch -এর মধ্যে পার্থক্য লিখুন।** *[41th BCS 2021 compact it 883 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    What is a Wi-Fi access point
    - An access point (AP) is a device that creates a wireless LAN and lets Wi-Fi clients join a wired network. It is the bridge between the radio side (802.11) and the cable side (Ethernet).
    - It broadcasts an SSID, authenticates clients with WPA2 or WPA3, and converts wireless frames into Ethernet frames and back.
    - It works at Layer 2 and is effectively a wireless switch port; it does not route.
    - Types: standalone (configured individually), controller-based (managed centrally in an enterprise), and mesh (APs relay for each other). Most are powered over Ethernet (PoE).
    - Multiple APs on different channels give roaming coverage across a building, and clients hand over between them.
    - A home "Wi-Fi router" is really three devices in one box: a router, a switch and an access point.

    Router vs Switch

    | Point | Switch | Router |
    |---|---|---|
    | OSI layer | 2 — Data Link | 3 — Network |
    | Address used | MAC | IP |
    | Purpose | Connects devices within one network | Connects different networks |
    | Table kept | MAC address table | Routing table |
    | Broadcast domain | One (or one per VLAN) | One per interface — it blocks broadcasts |
    | Ports | Many (24, 48) | Few |
    | Speed | Very fast, hardware forwarding | Slower, more processing per packet |
    | Extra functions | VLANs, STP, port security | NAT, DHCP, ACL, firewall, routing protocols |
    | Placement | Inside the LAN | At the network boundary |
    | Cost | Lower | Higher |

13. **হাব, সুইচ ও রাউটার এর মধ্যে পার্থক্য লিখ।** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 947 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.)

    | Point | Hub | Switch | Router |
    |---|---|---|---|
    | OSI layer | 1 — Physical | 2 — Data Link | 3 — Network |
    | Address used | None | MAC address | IP address |
    | Forwarding | Sends to every port | Sends only to the destination port | Routes between networks |
    | Intelligence | None | Learns a MAC table | Maintains a routing table |
    | Collision domain | 1 total | One per port | One per interface |
    | Broadcast domain | 1 | 1 (or per VLAN) | One per interface |
    | Duplex | Half only | Full | Full |
    | Bandwidth | Shared | Dedicated per port | Depends on the link |
    | Security | None | Moderate | Highest — ACL, NAT, firewall |
    | Cost | Lowest | Moderate | Highest |
    | Use | Obsolete | Building a LAN | Joining LAN to internet, or LAN to LAN |

    Simple summary
    - Hub — repeats everything to everyone, wasting bandwidth.
    - Switch — learns which device is on which port and delivers precisely.
    - Router — connects entire networks and chooses the best path between them.

14. **(c) Briefly describe three devices using which different LANs can be connected.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1030 (ET: N/A)]*

    Answer: Three devices used to connect different LANs together.

    1. Bridge (Layer 2)
    - Connects two LAN segments that use the same protocol, and forwards frames between them based on MAC addresses.
    - It learns which addresses are on each side and filters local traffic, so only frames destined for the other side cross.
    - Effect: splits the collision domain in two but keeps a single broadcast domain.
    - Suitable when two segments of the same network need to be joined and local traffic kept local.

    2. Switch (Layer 2)
    - A multi-port bridge implemented in hardware. It connects many devices and many segments, forwarding each frame only to the correct port using its MAC address table.
    - Every port is its own collision domain, and full duplex removes collisions entirely.
    - With VLANs it can also create several logical LANs on one physical switch, which are then joined by a router.
    - Suitable for connecting LAN segments within one building at high speed.

    3. Router (Layer 3)
    - Connects LANs that are on different IP networks, forwarding packets by IP address using a routing table.
    - It blocks broadcasts, so each connected LAN keeps its own broadcast domain — this is what stops a broadcast storm in one LAN from affecting the others.
    - It can also join networks over a WAN link, and it adds NAT, DHCP and ACL filtering.
    - Suitable for connecting LANs in different buildings, cities, or with different addressing.

    Also worth mentioning
    - Gateway — needed when the two LANs use different protocol suites, since it translates between them.
    - Repeater or hub (Layer 1) — extends a segment but does not really "connect LANs"; it merely enlarges one.

    | Device | Layer | Joins | Separates broadcasts |
    |---|---|---|---|
    | Bridge | 2 | Two segments of one LAN | No |
    | Switch | 2 | Many segments and devices | No (yes with VLANs) |
    | Router | 3 | Different IP networks | Yes |

15. **(ক) Hub এবং Switch কী? কোনটির ব্যবহার সুবিধাজনক সপক্ষে যুক্তি দিন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1098 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    What is a hub
    - A Layer 1 device — a multi-port repeater. A frame arriving on one port is regenerated and sent out of every other port.
    - It has no intelligence, keeps no address table, and cannot tell one device from another.
    - All ports share one collision domain and one broadcast domain, so it must run half duplex with CSMA/CD.

    What is a switch
    - A Layer 2 device — a multi-port bridge implemented in hardware. It learns the MAC address behind each port and forwards a frame only to the port where its destination lives.
    - Every port is a separate collision domain, so full-duplex operation is possible and collisions disappear.
    - Managed switches add VLANs, STP, port security and QoS.

    Which is preferable, and why — the `switch`, decisively

    - Bandwidth. A 100 Mbps hub with 10 users shares one 100 Mbps pipe, so each user gets roughly 10 Mbps. On a switch each user has a private 100 Mbps full-duplex link.
    - Collisions. A hub's single collision domain means constant collisions and retransmissions as users increase; a switch has none.
    - Security. On a hub every device receives every frame, so any machine can sniff passwords. A switch sends frames only where they belong.
    - Scalability. Hub performance collapses beyond a handful of active users; a switch stays fast.
    - Features. VLANs, QoS, link aggregation and port security exist only on switches.
    - Cost. Switches are now so cheap that hubs have no price advantage at all, and hubs are effectively no longer manufactured.

    - The only argument ever made for a hub is that it repeats all traffic to all ports, which is occasionally convenient for packet capture — and even that is now done with a switch's port-mirroring (SPAN) feature.
    - Conclusion: use a switch in every practical situation.

16. **Difference among HUB, Switch and Router.** *[DESCO Assistant Engineer (CSE) 2019 compact it 1119 (ET: BUET)]*

    Answer:

    | Point | Hub | Switch | Router |
    |---|---|---|---|
    | OSI layer | 1 — Physical | 2 — Data Link | 3 — Network |
    | Address used | None | MAC | IP |
    | How it forwards | Floods every port | Consults a learned MAC table | Consults a routing table |
    | Collision domains | 1 | One per port | One per interface |
    | Broadcast domains | 1 | 1 (or one per VLAN) | One per interface |
    | Duplex | Half only | Full | Full |
    | Bandwidth per user | Shared | Dedicated | Depends on the link |
    | Filtering | None | By MAC | By IP, port, protocol (ACL) |
    | Extra features | None | VLAN, STP, port security, QoS | NAT, DHCP, firewall, routing protocols |
    | Connects | Devices in one segment | Devices in one LAN | Different networks |
    | Speed | Slowest | Fastest (ASIC) | Slower per packet |
    | Cost | Lowest | Moderate | Highest |
    | Status | Obsolete | Standard | Essential for internet access |

17. **(a) What are the difference among Hub, Switch and Routers?** *[BPSC Assistant Programmer (ICT) 2019 compact it 1144 (ET: N/A)]*

    Answer:

    | Point | Hub | Switch | Router |
    |---|---|---|---|
    | OSI layer | 1 — Physical | 2 — Data Link | 3 — Network |
    | Decision based on | Nothing; it just repeats | MAC address | IP address |
    | Table maintained | None | MAC address table | Routing table |
    | Traffic sent to | All ports | Only the destination port | The best next hop towards the destination network |
    | Collision domain | One for the device | One per port | One per interface |
    | Broadcast domain | One | One (VLANs can split it) | One per interface — blocks broadcasts |
    | Duplex | Half duplex, CSMA/CD | Full duplex, no collisions | Full duplex |
    | Security | None; everyone sees everything | Frames go only where needed | ACLs, NAT, firewall |
    | Typical use | Obsolete | Building the LAN | Connecting LAN to internet or LAN to LAN |
    | Cost | Lowest | Moderate | Highest |

    Practical illustration
    ```
    Internet
       |
    [ROUTER]        <- joins the LAN to the internet, blocks broadcasts, does NAT
       |
    [SWITCH]        <- connects all internal devices, one collision domain per port
     / | \
    PC PC PC
    ```
    - A hub would sit where the switch is, but would share bandwidth and let every PC see every frame — which is why it is no longer used.

18. **Difference between Router and Switch.** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1151 (ET: KUET)]*

    Answer:

    | Point | Switch | Router |
    |---|---|---|
    | OSI layer | 2 — Data Link | 3 — Network |
    | Address used | MAC address | IP address |
    | Table kept | MAC address table | Routing table |
    | Purpose | Connects devices within the same network | Connects different networks |
    | Broadcast handling | Forwards broadcasts to all ports | Blocks broadcasts |
    | Broadcast domain | One (or one per VLAN) | One per interface |
    | Ports | Many — 8, 24, 48 | Few — 2 to 8 |
    | Speed | Very fast, hardware ASIC forwarding | Slower, more processing per packet |
    | Protocols run | STP, VLAN (802.1Q), LACP | RIP, OSPF, EIGRP, BGP |
    | Extra functions | Port security, QoS, link aggregation | NAT, DHCP, ACL, firewall, VPN |
    | Placement | Inside the LAN | At the boundary of the network |
    | Cost | Lower | Higher |
    | WAN support | No | Yes |

    Key point
    - A switch works `inside` a network; a router works `between` networks. That single distinction explains almost every other difference in the table — the addresses used, the tables kept, the handling of broadcasts and the placement in the topology.
    - A Layer 3 switch blurs the line: it does hardware routing between VLANs, combining switch speed with basic router function, but it still lacks WAN interfaces and the full feature set of a router.

19. **Describe about Hub, Switch and Router.** *[BPDB Assistant Engineer (CSE) 2018 compact it 1214 (ET: N/A)]*

    Answer:

    Hub — Layer 1
    - A multi-port repeater. Any frame received on one port is regenerated and sent out of every other port, with no examination of addresses.
    - All ports share one collision domain and one broadcast domain, so it must work in half duplex using CSMA/CD, and bandwidth is shared among all users.
    - No intelligence, no filtering, no security — every device sees every frame.
    - Types were passive, active and intelligent. It is obsolete today, completely replaced by switches.

    Switch — Layer 2
    - A multi-port bridge built in hardware. It reads the source MAC address of every incoming frame and records which port it came from, building a MAC address table.
    - A frame is then forwarded only out of the port where its destination lives. Unknown, broadcast and multicast frames are flooded.
    - Each port is its own collision domain with dedicated bandwidth, and full duplex means no collisions at all.
    - Forwarding methods: store-and-forward (checks the CRC first, safest), cut-through (fastest) and fragment-free.
    - Managed switches add VLANs to split broadcast domains, Spanning Tree Protocol to prevent loops, port security, QoS and link aggregation.

    Router — Layer 3
    - Connects different networks and forwards packets between them using the destination IP address and a routing table, choosing the best path by longest prefix match.
    - Routes are learned statically or dynamically through RIP, OSPF, EIGRP or BGP.
    - It does not forward broadcasts, so every interface bounds a separate broadcast domain — this is what stops a broadcast storm spreading.
    - Additional functions: NAT, DHCP server, ACL filtering, VPN termination, fragmentation and TTL decrement.
    - It rewrites the Layer 2 frame at each hop while leaving the IP addresses untouched, which is why the IP header identifies the endpoints and the MAC header identifies only the current hop.

    ```
    Internet --- [ROUTER] --- [SWITCH] --- PC, PC, PC, Printer
                 Layer 3       Layer 2
                 IP, NAT       MAC, VLAN
    ```

## Multiplexing & Bandwidth (18)

1. Five channels, each with a 100-kHz bandwidth, are to be multiplexed together. What is the minimum bandwidth of the link if there is a need for a guard band of 10 kHz between the channels to prevent interference? [SO IT 25-07-2026]

   Answer: This is FDM, so the bandwidths and the guard bands simply add up.

   Given
   - Number of channels, n = 5
   - Bandwidth of each channel = 100 kHz
   - Guard band = 10 kHz

   Step 1 — total channel bandwidth
   - 5 × 100 = 500 kHz

   Step 2 — number of guard bands
   - Guard bands are needed only BETWEEN channels, not outside the first and last.
   - Number of guard bands = n − 1 = 5 − 1 = 4
   - Total guard bandwidth = 4 × 10 = 40 kHz

   Step 3 — minimum link bandwidth
   ```
   Total = 500 + 40 = 540 kHz
   ```

   ```
   |--100--|10|--100--|10|--100--|10|--100--|10|--100--|
      ch1   GB   ch2   GB   ch3   GB   ch4   GB   ch5
                    total = 540 kHz
   ```
   - Answer: `540 kHz`.
   - The common mistake is to use 5 guard bands instead of 4.

2. **ব্যান্ডউইথ (Bandwidth) বলতে কী বুঝায়?** *[সাধারণ জ্ঞান: বিজ্ঞান ও প্রযুক্তি, বিষয় কোড: ১০৪, মান: ৪০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer: (Answered in English, as required for IT topics.)

   - Bandwidth is the maximum amount of data a communication channel can carry per unit of time. It is the capacity of the link — how wide the pipe is, not how fast a single drop travels through it.

   Two meanings
   - Digital (network) bandwidth — measured in bits per second: bps, kbps, Mbps, Gbps. A 100 Mbps link can carry at most 100 million bits per second.
   - Analogue (signal) bandwidth — measured in hertz: the range of frequencies a channel can pass. A voice channel of 300–3400 Hz has a bandwidth of 3100 Hz.
   - The two are linked by the Nyquist and Shannon formulas, which give the maximum bit rate obtainable from a given frequency bandwidth.

   Related terms that are often confused
   - Throughput — the data rate actually achieved, always lower than bandwidth because of protocol overhead, congestion and errors.
   - Latency — the delay in milliseconds. High bandwidth does not mean low latency: a satellite link can offer 100 Mbps with 600 ms delay.
   - Bandwidth-delay product — bandwidth × round-trip time, the amount of data "in flight" on the link at any moment.

   - Analogy: bandwidth is the width of a road (how many cars can pass per minute); latency is how long one car takes to reach the other end.

3. **6.9 Five channels, each with a 100-kHz bandwidth, are to be multiplexed together. What is the minimum bandwidth of the link if there is a need for a guard band of 10 kHz between the channels to prevent interference?** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

   Answer: FDM problem — bandwidths and guard bands add up.

   Given
   - n = 5 channels, each 100 kHz; guard band 10 kHz

   Step 1 — channel bandwidth
   - 5 × 100 kHz = 500 kHz

   Step 2 — guard bands
   - Guard bands go only between adjacent channels: n − 1 = 4
   - 4 × 10 kHz = 40 kHz

   Step 3 — minimum link bandwidth
   ```
   500 kHz + 40 kHz = 540 kHz
   ```

   ```
   |-100-|GB|-100-|GB|-100-|GB|-100-|GB|-100-|
     ch1  10  ch2  10  ch3  10  ch4  10  ch5
                 total = 540 kHz
   ```
   - Answer: `540 kHz`.
   - Guard bands exist to stop adjacent channels interfering with each other, which is the price FDM pays for using frequency separation.

4. **Differentiate among TDM, FDM and WDM. How does working process in TDM?** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 511 (ET: MIST)]*

   Answer:

   Comparison of TDM, FDM and WDM

   | Point | FDM | TDM | WDM |
   |---|---|---|---|
   | Full form | Frequency Division Multiplexing | Time Division Multiplexing | Wavelength Division Multiplexing |
   | Divides | The frequency band | Time into slots | The optical spectrum into wavelengths |
   | Signal type | Analogue | Digital (mainly) | Optical |
   | Medium | Copper, radio | Copper, fibre, radio | Optical fibre only |
   | Sharing | All channels transmit at the same time on different frequencies | All channels use the whole bandwidth, but at different times | All channels transmit at the same time on different colours of light |
   | Guard needed | Guard band (frequency) | Guard time | Guard wavelength |
   | Efficiency | Lower; guard bands waste spectrum | Higher | Very high — terabits per fibre |
   | Interference | Crosstalk between adjacent bands | Slot synchronisation errors | Very low |
   | Example | Radio and TV broadcast, cable TV, ADSL | T1/E1 carriers, GSM, SONET | DWDM and CWDM on long-haul fibre |

   - WDM is conceptually FDM applied to light: different wavelengths are simply different frequencies. CWDM uses widely spaced channels; DWDM packs 40–160 channels into one fibre.

   How TDM works
   - Step 1 — each input source is sampled or buffered in turn.
   - Step 2 — the multiplexer allocates a fixed time slot to each source, in a repeating round-robin order.
   - Step 3 — one pass through all sources forms a `frame`. A framing bit is added so the receiver can find the slot boundaries.
   - Step 4 — the frames are sent one after another over the shared link at a rate equal to the sum of all the input rates.
   - Step 5 — the demultiplexer stays synchronised using the framing bits and delivers each slot's data to the correct output.

   ```
   Input A: a1 a2 a3
   Input B: b1 b2 b3        --> output: | a1 b1 c1 | a2 b2 c2 | a3 b3 c3 |
   Input C: c1 c2 c3                      frame 1     frame 2    frame 3
   ```

   Two kinds of TDM
   - Synchronous TDM — every source gets a slot in every frame, whether or not it has data. Simple, but empty slots waste bandwidth.
   - Statistical (asynchronous) TDM — slots are given only to sources that actually have data, so an address must be carried with each slot. Far more efficient with bursty traffic.

5. **Describe the different types of Multiplexing.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 554 (ET: BIBM)]*

   Answer: Multiplexing is the technique of sending several signals over one shared communication link, so that an expensive medium is used efficiently. The device at the sending end is the MUX and at the receiving end the DEMUX.

   ```
   A --\                                          /--> A
   B ----> [ MUX ] === one shared link === [ DEMUX ] --> B
   C --/                                          \--> C
   ```

   Types

   1. FDM — Frequency Division Multiplexing
   - The channel's frequency band is divided; each signal modulates a different carrier and occupies its own sub-band, all transmitting at the same time.
   - Guard bands separate adjacent channels to prevent interference.
   - Analogue technique. Used in radio and TV broadcasting, cable TV and ADSL.

   2. TDM — Time Division Multiplexing
   - Time is divided into slots; each source gets the whole bandwidth, but only during its own slot.
   - Digital technique. Used in T1/E1 carriers, SONET/SDH and GSM.
   - Sub-types:
     - Synchronous TDM — a fixed slot per source in every frame, even if it is empty. Simple, but wasteful.
     - Statistical TDM — slots are allocated on demand to sources that have data, with an address carried in each slot. Much more efficient for bursty traffic.

   3. WDM — Wavelength Division Multiplexing
   - Several optical signals of different wavelengths (colours) share one fibre. It is FDM applied to light.
   - CWDM uses a few widely spaced channels and is cheap; DWDM packs 40–160 closely spaced channels for terabit capacity on long-haul links.

   4. CDM / CDMA — Code Division Multiplexing
   - All users transmit at the same time on the same frequency, but each is given a unique orthogonal code (a chip sequence). The receiver recovers one user's data by correlating with that user's code.
   - Used in 3G mobile networks and GPS. Resistant to jamming and gives good security.

   5. OFDM — Orthogonal Frequency Division Multiplexing
   - A refinement of FDM using many narrow, mathematically orthogonal subcarriers that overlap without interfering, so no guard band is wasted.
   - Used in Wi-Fi, LTE, 5G, DVB and ADSL. It resists multipath fading very well.

   6. SDM — Space Division Multiplexing
   - Physically separate paths: multiple fibres in one cable, multiple pairs in one bundle, or MIMO antennas in space.

   Why multiplexing is used
   - The medium is expensive; one fibre or one radio channel can serve hundreds of users. It cuts cost, uses spectrum efficiently, and makes long-distance links economic.

6. **What technique allows simultaneous transmission of multiple signals across a single data link?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

   Answer: The technique is `multiplexing`.

   - Multiplexing allows several signals or data streams to share one physical link at the same time. A multiplexer (MUX) combines them at the sending end and a demultiplexer (DEMUX) separates them at the receiving end.

   Main types
   - FDM (Frequency Division Multiplexing) — each signal gets its own frequency band, and all transmit simultaneously. Used in radio, TV and cable.
   - TDM (Time Division Multiplexing) — each signal gets its own time slot and uses the full bandwidth during it. Used in T1/E1 and GSM.
   - WDM (Wavelength Division Multiplexing) — each signal gets its own wavelength of light on one fibre. Used in long-haul optical links.
   - CDM/CDMA — all signals share the same frequency and time, separated by unique orthogonal codes. Used in 3G and GPS.
   - OFDM — many overlapping orthogonal subcarriers; used in Wi-Fi, LTE and 5G.

   - Purpose: the transmission medium is expensive, so sharing one link among many users maximises its use and cuts cost per user.

7. **(খ) FDM এবং TDM এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 615 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   | Point | FDM | TDM |
   |---|---|---|
   | Full form | Frequency Division Multiplexing | Time Division Multiplexing |
   | Divides | The frequency band into sub-bands | Time into slots |
   | Signal type | Analogue | Digital (mainly) |
   | Transmission | All channels transmit simultaneously, on different frequencies | Only one channel transmits at a time, using the whole bandwidth |
   | Bandwidth per channel | A fixed portion of the total | The full bandwidth, for a fraction of the time |
   | Separator needed | Guard band, in hertz | Guard time, in seconds |
   | Synchronisation | Not critical | Critical — the receiver must know slot boundaries, hence framing bits |
   | Circuitry | Simpler, but needs many modulators and filters | More complex timing, but simpler in digital form |
   | Efficiency | Lower — guard bands waste spectrum | Higher, especially statistical TDM |
   | Interference issue | Crosstalk between adjacent bands | Slot misalignment |
   | Example | Radio, TV, cable TV, ADSL | T1/E1, SONET, GSM, ISDN |

   ```
   FDM                          TDM
   freq ^                       freq ^
     f3 |CCCCCCCCCCCC             |ABCABCABCABC
     f2 |BBBBBBBBBBBB             |
     f1 |AAAAAAAAAAAA             |
        +------------> time       +------------> time
    each user owns a band     each user owns a slot
   ```

8. **Show that the data rate of T-1 carrier is 1.544 Mbps.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

   Answer: The T-1 carrier multiplexes 24 voice channels using synchronous TDM.

   Step 1 — sampling rate for one voice channel
   - A voice signal is limited to 4 kHz. By the Nyquist theorem the sampling rate must be at least 2 × 4000 = `8000 samples per second`.

   Step 2 — bits per sample
   - PCM quantises each sample into `8 bits`.

   Step 3 — data rate of one channel
   ```
   8000 samples/s × 8 bits = 64,000 bps = 64 kbps  (this is the DS-0 rate)
   ```

   Step 4 — bits in one T-1 frame
   - 24 channels × 8 bits = 192 bits
   - Plus 1 framing bit for synchronisation
   ```
   Frame size = 192 + 1 = 193 bits
   ```

   Step 5 — frame rate
   - One frame carries one sample from every channel, and each channel is sampled 8000 times a second, so there are `8000 frames per second`.

   Step 6 — T-1 data rate
   ```
   193 bits/frame × 8000 frames/s = 1,544,000 bps = 1.544 Mbps
   ```

   - Hence the T-1 rate is `1.544 Mbps`, of which 1.536 Mbps (24 × 64 kbps) is payload and 8 kbps is framing overhead.
   - The European E-1 carrier uses 32 slots instead: 32 × 8 × 8000 = 2.048 Mbps.

9. **Suppose you are appointed as an Assistant Engineer in a Government organization. The number of telephone connections required for the organization is 1000. The per year increment of telephone connection is 100. Considering the life time of telephone equipment is to be 15 years, design a T-carrier based TDM system for the organization.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

   Answer:

   Step 1 — total connections needed over the equipment lifetime
   - Present requirement = 1000
   - Growth = 100 per year for 15 years = 1500
   ```
   Total = 1000 + 1500 = 2500 telephone connections
   ```

   Step 2 — capacity of the T-carrier hierarchy

   | Carrier | Voice channels | Data rate | Composition |
   |---|---|---|---|
   | DS-0 | 1 | 64 kbps | one voice channel |
   | T-1 (DS-1) | 24 | 1.544 Mbps | 24 × DS-0 |
   | T-2 (DS-2) | 96 | 6.312 Mbps | 4 × T-1 |
   | T-3 (DS-3) | 672 | 44.736 Mbps | 7 × T-2 = 28 × T-1 |
   | T-4 (DS-4) | 4032 | 274.176 Mbps | 6 × T-3 |

   Step 3 — choose the carrier

   - Using T-1 only: 2500 ÷ 24 = 104.17 -> `105 T-1 lines`. Too many links to manage.
   - Using T-2: 2500 ÷ 96 = 26.04 -> 27 T-2 lines. Still many.
   - Using T-3: 2500 ÷ 672 = 3.72 -> `4 T-3 lines`, giving 2688 channels.
   - Using T-4: one T-4 gives 4032 channels — far more than needed and unnecessarily costly.

   Step 4 — recommended design
   - Deploy `4 T-3 (DS-3) links`, total capacity 2688 voice channels and 178.944 Mbps.
   - Spare capacity = 2688 − 2500 = 188 channels, about 7 percent headroom for unexpected growth.

   ```
   2500 subscriber lines
           |
      [ PBX / Channel banks ]   -> groups of 24 into DS-1
           |
      [ M13 multiplexers ]      -> 28 DS-1 into each DS-3
           |
      4 × T-3 (44.736 Mbps each) --> to the public network
   ```

   Practical notes
   - Growth is not perfectly linear, so provisioning to the 15-year figure from day one is the safe engineering choice; alternatively add one T-3 roughly every four years.
   - A modern equivalent design would use SDH/SONET (STM-1 = 63 E-1 = 1890 channels) or, more likely today, VoIP over an IP network, where 2500 concurrent calls at about 100 kbps each need roughly 250 Mbps — comfortably within a 1 Gbps link.

10. **Compare between TDM and TDMA techniques.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 676 (ET: N/A)]*

    Answer:

    | Point | TDM | TDMA |
    |---|---|---|
    | Full form | Time Division Multiplexing | Time Division Multiple Access |
    | Nature | A multiplexing technique | A channel-access (multiple-access) method |
    | Where used | Wired links — T1/E1, SONET, PDH | Wireless systems — GSM, satellite, DECT |
    | Sources | Several inputs at one physical location, feeding one multiplexer | Many users at different physical locations, sharing one radio channel |
    | Slot assignment | Fixed and pre-assigned by the multiplexer | Assigned dynamically by the base station, and released when the call ends |
    | Synchronisation | Simple; all inputs share one clock at the MUX | Difficult; users are at different distances, so timing advance is needed to keep bursts from overlapping |
    | Guard interval | Small guard time | Larger guard time, because of propagation differences |
    | Control | No signalling needed | Requires control channels for allocation and handover |
    | Purpose | Combine several streams onto one link | Let many independent users share one channel |
    | Example | 24 voice channels on a T-1 | 8 GSM calls on one 200 kHz carrier |

    Key insight
    - TDM is a `multiplexing` technique: the inputs are already together in one box, so the multiplexer just interleaves them.
    - TDMA is a `multiple-access` technique: the users are physically separate and must be told when to transmit, which is why it needs signalling, power control and timing advance.
    - In GSM, both appear together: TDMA divides each 200 kHz carrier into 8 time slots, and FDMA divides the band into carriers.

11. **Assume a TDMA based communication system having 8 transmission receiver pairs. Each source is sampled at 8KHz. That generates 16bits per sample if two synchronization bits are added to each frame calculate the data rate of TDMA line.** *[BDCCL Assistant Engineer (Network) 2022 compact it 742 (ET: N/A)], [Water Supply and Sewerage Authority (WASA); Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)], [BTCL Assistant Manager (Technical) 2021 compact it 765 (ET: BUET)]*

    Answer:

    Given
    - Number of transmitter–receiver pairs (sources) = 8
    - Sampling rate of each source = 8 kHz = 8000 samples per second
    - Bits per sample = 16
    - Synchronisation bits per frame = 2

    Step 1 — bits contributed by the sources in one frame
    - Each source puts one sample (16 bits) into each frame.
    ```
    8 × 16 = 128 bits
    ```

    Step 2 — total frame size
    ```
    Frame = 128 + 2 sync bits = 130 bits
    ```

    Step 3 — frame rate
    - Every source must be sampled 8000 times per second, and each frame carries one sample from each source.
    ```
    Frame rate = 8000 frames per second
    ```

    Step 4 — data rate of the TDMA line
    ```
    Data rate = frame size × frame rate
              = 130 × 8000
              = 1,040,000 bps
              = 1.04 Mbps
    ```

    - Answer: `1.04 Mbps`.
    - Check: each source alone runs at 16 × 8000 = 128 kbps; eight sources give 1.024 Mbps, and the 2 sync bits add 16 kbps, totalling 1.04 Mbps.

12. **Two channels, one with a bit rate of 190kbps and another with a bit rate 180 kbps are to be multiplexed using pulse stuffing TDM with no synchronization bits. Answer the following questions: (a) What is the size of a frame in bits? (b) What is the frame rate? (c) What is the duration of a frame? (d) What is the date rate?** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)]*

    Answer: In pulse-stuffing TDM, extra dummy bits are added to the slower channel so that both channels run at the same rate as the fastest one.

    Given
    - Channel 1 = 190 kbps, Channel 2 = 180 kbps, no synchronisation bits, interleaved unit = 1 bit

    Step 0 — pulse stuffing
    - Channel 2 is stuffed from 180 kbps up to `190 kbps`, so both inputs are now equal.

    (a) Size of a frame
    - One frame carries one bit from each of the 2 channels.
    ```
    Frame size = 2 bits
    ```

    (b) Frame rate
    - Each channel supplies 190,000 bits per second, and each frame takes one bit from each.
    ```
    Frame rate = 190,000 frames per second
    ```

    (c) Duration of a frame
    ```
    Duration = 1 / 190,000 = 5.26 × 10^-6 s = 5.26 microseconds
    ```

    (d) Data rate of the link
    ```
    Data rate = frame size × frame rate = 2 × 190,000 = 380,000 bps = 380 kbps
    ```

    | Item | Value |
    |---|---|
    | Frame size | 2 bits |
    | Frame rate | 190 kfps |
    | Frame duration | 5.26 µs |
    | Link data rate | 380 kbps |

    - Of the 380 kbps, 10 kbps is stuffing overhead (the difference between 190 and 180 kbps on channel 2), which is the cost of making the rates match.

13. **What is Multiplexing? Write about Time division Multiplexing.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 870 (ET: N/A)]*

    Answer:

    What is multiplexing
    - Multiplexing is sending several independent signals over a single shared communication link, so that an expensive medium is used efficiently.
    - The device that combines the signals is the multiplexer (MUX); the one that separates them at the far end is the demultiplexer (DEMUX).
    - Main types: FDM (by frequency), TDM (by time), WDM (by wavelength on fibre), CDM (by code) and OFDM (orthogonal subcarriers).
    - Purpose: one costly link — a fibre, a leased line, a radio channel — serves many users, which cuts cost per user dramatically.

    Time Division Multiplexing
    - The link's time is divided into small slots. Each source is given a slot in a repeating cycle, and during its slot it has the entire bandwidth of the link.
    - One complete cycle through all the sources is a `frame`. A framing bit is added so the receiver can find the slot boundaries and stay synchronised.
    - The output rate equals the sum of all the input rates, plus overhead.

    ```
    Input A: a1 a2 a3
    Input B: b1 b2 b3   ---> | a1 b1 c1 | a2 b2 c2 | a3 b3 c3 |
    Input C: c1 c2 c3          frame 1     frame 2     frame 3
    ```

    Two forms
    - Synchronous TDM — every source has a reserved slot in every frame, whether or not it has data. Simple and predictable, but empty slots waste bandwidth.
    - Statistical (asynchronous) TDM — slots are given only to sources with data ready, so each slot must carry an address. Much more efficient with bursty traffic, at the cost of extra overhead and variable delay.

    Related concepts
    - Bit interleaving takes one bit per source per frame; character (byte) interleaving takes one byte.
    - Pulse stuffing equalises sources of slightly different rates by adding dummy bits.

    - Example: a T-1 line carries 24 voice channels of 64 kbps each. Frame = 24 × 8 + 1 = 193 bits, sent 8000 times a second, giving 1.544 Mbps.

14. **(a) Distinguish between Frequency Division Multiplexing (FDM) and Time Division Multiplexing (TDM).** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 888 (ET: N/A)]*

    Answer:

    | Point | Frequency Division Multiplexing (FDM) | Time Division Multiplexing (TDM) |
    |---|---|---|
    | Resource divided | The frequency band | Time |
    | How it shares | Each channel gets a permanent sub-band and transmits continuously | Each channel gets the whole bandwidth, but only in its own time slot |
    | Signal type | Analogue | Digital (mainly) |
    | Simultaneity | All channels transmit at the same time | Only one channel transmits at any instant |
    | Separator | Guard band, measured in hertz | Guard time, measured in seconds |
    | Synchronisation | Not critical | Critical — framing bits keep the receiver aligned |
    | Bandwidth use | Fixed share per user, wasted if the user is idle | Slot wasted if the source is idle (synchronous TDM); statistical TDM avoids this |
    | Efficiency | Lower, because guard bands consume spectrum | Higher |
    | Hardware | Needs modulators, filters and oscillators per channel | Needs accurate timing and buffering |
    | Interference | Crosstalk between adjacent bands | Slot overlap if timing drifts |
    | Example | Radio, TV, cable TV, ADSL | T1/E1, SONET, GSM, ISDN |

    ```
    FDM                              TDM
    f ^                              f ^
    f3| CCCCCCCCCCCCCC                 | A B C A B C A B C
    f2| BBBBBBBBBBBBBB                 |
    f1| AAAAAAAAAAAAAA                 |
      +--------------> t               +----------------> t
    each user owns a frequency      each user owns a time slot
    ```
    - One-line summary: FDM shares the spectrum permanently, TDM shares the clock in turns. WDM is FDM applied to light, and OFDM is FDM with orthogonal subcarriers that need no guard band.

15. **TDM math: rate= 1.536 Mbps, message size= 960000, Slot=32, end to end circuit Switch time=800ms, calculate transfer time.** *[Sonali Bank Ltd. Officer IT 2021 compact it 910 (ET: N/A)]*

    Answer: This is a circuit-switched TDM path. The message travels in one dedicated slot, so first find that slot's rate.

    Given
    - Total link rate = 1.536 Mbps
    - Number of slots per frame = 32
    - Message size = 960,000 bits
    - End-to-end circuit setup time = 800 ms = 0.8 s

    Step 1 — data rate of one slot
    ```
    Slot rate = 1,536,000 / 32 = 48,000 bps = 48 kbps
    ```

    Step 2 — time to transmit the message
    ```
    Transmission time = 960,000 / 48,000 = 20 seconds
    ```

    Step 3 — total transfer time
    ```
    Total = setup time + transmission time
          = 0.8 + 20
          = 20.8 seconds
    ```

    | Item | Value |
    |---|---|
    | Slot rate | 48 kbps |
    | Transmission time | 20 s |
    | Setup time | 0.8 s |
    | Total transfer time | `20.8 s` |

    - Note the characteristic of circuit switching: the full path is reserved before any data flows, so the setup delay is paid once, and after that the rate is guaranteed for the whole transfer.

16. **A want to send 2 files the size of each file is 500000 bit's data to B through TDM channel which has slot 16 channel bit rate 1.5 Mbps and 30 millisecond delay time, if no propagation delay; find out time to send the data.** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 925 (ET: CTI)]*

    Answer:

    Given
    - 2 files, each 500,000 bits -> total 1,000,000 bits
    - TDM channel with 16 slots, total channel bit rate = 1.5 Mbps
    - Delay (setup) time = 30 ms = 0.03 s, no propagation delay

    Step 1 — data rate available in one slot
    ```
    Slot rate = 1,500,000 / 16 = 93,750 bps
    ```

    Step 2 — transmission time for the data
    ```
    Total bits = 2 × 500,000 = 1,000,000 bits
    Time = 1,000,000 / 93,750 = 10.67 seconds
    ```

    Step 3 — total time
    ```
    Total = 10.67 + 0.03 = 10.70 seconds
    ```

    | Item | Value |
    |---|---|
    | Slot data rate | 93.75 kbps |
    | Data transmission time | 10.67 s |
    | Delay | 0.03 s |
    | Total time | `10.70 s` |

    - Alternative reading: if the two files are sent in parallel over two separate slots, each file takes 500,000 ÷ 93,750 = 5.33 s, so the total is 5.33 + 0.03 = `5.36 s`. The single-slot answer above is the standard interpretation, since a circuit is normally allocated one slot.

17. **We have four sources, each creating 250 characters per second. If the interleaved unit is a character and 1 synchronizing bit is added to each frame. Now find- (a) the data rate of each source. (b) the duration of each character in each source.** *[BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)]*

    Answer:

    Given
    - 4 sources, each producing 250 characters per second
    - Interleaved unit = 1 character = 8 bits
    - 1 synchronising bit added to each frame

    (a) Data rate of each source
    ```
    250 characters/s × 8 bits/character = 2000 bps = 2 kbps
    ```

    (b) Duration of each character in each source
    ```
    1 / 250 = 0.004 s = 4 milliseconds
    ```

    Supporting values often asked with this question
    - Frame rate = 250 frames per second (each frame carries one character from each source).
    - Frame size = (4 × 8) + 1 = 33 bits.
    - Output (link) data rate = 33 × 250 = 8250 bps.
    - Duration of a frame = 1 / 250 = 4 ms, the same as one input character, because one frame is produced per character period.
    - Output bit duration = 4 ms ÷ 33 = 121.2 µs.

    | Item | Value |
    |---|---|
    | Data rate per source | 2 kbps |
    | Character duration | 4 ms |
    | Frame rate | 250 fps |
    | Frame size | 33 bits |
    | Link rate | 8250 bps |

    - Note that 4 × 2000 = 8000 bps of payload plus 250 bps of framing overhead gives the 8250 bps link rate.

18. **Figure shows synchronous TOM with a data stream for each input and one data stream for the output. The unit of data is 1bit. Find (a) the input bit duration (b) the output bit duration (c) the output bit rate and (d) the output frame rate.** *[Janata Bank Ltd SO ( Assistant Network Engineer) 2020 compact it 1009 (ET: N/A)]*

    Answer: The figure was not printed with the question. The standard version of this problem uses three input sources of 1 kbps each with a 1-bit interleaving unit, and the general formulas are given so any figure can be solved.

    General formulas — synchronous TDM with n inputs, each at rate R bps, unit = 1 bit
    ```
    (a) Input bit duration   = 1 / R
    (b) Output bit duration  = (1 / R) / n  = input bit duration ÷ n
    (c) Output bit rate      = n × R
    (d) Output frame rate    = R          (one frame per input bit period)
    ```

    Worked with the standard values: 3 inputs, each 1 kbps

    (a) Input bit duration
    ```
    1 / 1000 = 0.001 s = 1 ms
    ```

    (b) Output bit duration
    - Three input bits must be squeezed into the time of one input bit.
    ```
    1 ms / 3 = 0.333 ms = 333.33 microseconds
    ```

    (c) Output bit rate
    ```
    3 × 1000 = 3000 bps = 3 kbps
    ```
    - Check: 1 / 333.33 µs = 3000 bps, which agrees.

    (d) Output frame rate
    - One frame carries one bit from each of the three inputs, and each input produces 1000 bits per second.
    ```
    Frame rate = 1000 frames per second
    ```

    | Item | Value |
    |---|---|
    | Input bit duration | 1 ms |
    | Output bit duration | 333.33 µs |
    | Output bit rate | 3 kbps |
    | Output frame rate | 1000 fps |

    - The pattern to remember: the frame rate always equals the input bit rate, and the output bit rate is always n times one input rate. <!-- verify -->

## Routing Protocols & Route Configuration (18)

1. A BGP router receives multiple routes to the same destination network from different neighboring autonomous systems. The available routes are given in the following table, containing Path, LOCAL_PREF, AS_PATH, ORIGIN, and MED values. Using the standard BGP best-path selection rules, analyze the attributes in the given order and determine which path will be selected as the best route, showing the comparison and justification for each step. [BSCCPL AME 21-08-2026 (BUET)]

| Path | LOCAL_PREF | AS_PATH | ORIGIN | MED |
|---|---|---|---|---|
| Path 1 | 200 | 65001 65010 | IGP | 50 |
| Path 2 | 150 | 65020 | IGP | 5 |
| Path 3 | 200 | 65030 65040 | IGP | 10 |
| Path 4 | 200 | 65050 65060 | IGP | 20 |

   Answer: BGP evaluates attributes in a fixed order and stops at the first attribute that produces a single winner.

   The BGP best-path selection order
   - 1. Highest WEIGHT (Cisco proprietary, local to the router)
   - 2. Highest LOCAL_PREF
   - 3. Locally originated route (network / redistribute / aggregate)
   - 4. Shortest AS_PATH
   - 5. Lowest ORIGIN type (IGP < EGP < Incomplete)
   - 6. Lowest MED
   - 7. eBGP over iBGP
   - 8. Lowest IGP metric to the next hop
   - 9. Oldest eBGP path, then lowest router ID, then lowest neighbour address

   Step-by-step comparison

   Step 1 — WEIGHT
   - Not given for any path, so all are equal at the default. No decision. Continue.

   Step 2 — LOCAL_PREF (highest wins)

   | Path | LOCAL_PREF | Result |
   |---|---|---|
   | Path 1 | 200 | survives |
   | Path 2 | 150 | `ELIMINATED` |
   | Path 3 | 200 | survives |
   | Path 4 | 200 | survives |

   - Path 2 is removed here even though it has the shortest AS_PATH and the lowest MED. This is the key trap in the question: LOCAL_PREF is checked long before AS_PATH, so a lower LOCAL_PREF loses regardless of how good its other attributes are.

   Step 3 — Locally originated
   - None of the paths is locally originated; all are learned from neighbours. No decision.

   Step 4 — Shortest AS_PATH

   | Path | AS_PATH | Length |
   |---|---|---|
   | Path 1 | 65001 65010 | 2 |
   | Path 3 | 65030 65040 | 2 |
   | Path 4 | 65050 65060 | 2 |

   - All remaining paths have length 2. Tie. Continue.

   Step 5 — Lowest ORIGIN
   - All three are `IGP`, which is the lowest (best) origin code. Tie. Continue.

   Step 6 — Lowest MED (lowest wins)

   | Path | MED | Result |
   |---|---|---|
   | Path 1 | 50 | eliminated |
   | Path 3 | `10` | `BEST` |
   | Path 4 | 20 | eliminated |

   Conclusion
   - The selected best path is `Path 3` (LOCAL_PREF 200, AS_PATH 65030 65040, ORIGIN IGP, MED 10).

   Justification summary

   | Step | Attribute | Outcome |
   |---|---|---|
   | 1 | Weight | All equal |
   | 2 | LOCAL_PREF | Path 2 eliminated (150 < 200) |
   | 3 | Local origin | None |
   | 4 | AS_PATH | All length 2, tie |
   | 5 | ORIGIN | All IGP, tie |
   | 6 | MED | Path 3 wins with 10 |

   Important practical caveat
   - By default BGP compares MED only between paths received from the `same` neighbouring AS. Here the three surviving paths come from AS 65001, AS 65030 and AS 65050 — three different neighbours — so on a real router the MED comparison would be skipped unless `bgp always-compare-med` is configured, and the decision would fall through to step 8 (lowest IGP metric to the next hop) or step 9 (lowest router ID).
   - The question asks for the standard rules applied in the given order, so `Path 3` is the intended answer.

2. **Static route Configuration: Configure R0 to reach PC1 you can assume any Vendor, Cisco, Huawei, juniper** *[Islami Bank PLC Senior Officer (Network/System) 14.03.2025 compact it 1331 (ET: BUET)]*

   Answer: A static route is configured manually and tells the router exactly which next hop to use for a given destination network.

   Assumed topology
   ```
   PC0            R0            R1            PC1
   192.168.1.10   Gi0/0         Gi0/0         192.168.2.10
                  192.168.1.1   192.168.2.1
                  Gi0/1 -------- Gi0/1
                  10.0.0.1      10.0.0.2
                       (WAN link 10.0.0.0/30)
   ```
   - R0 knows about 192.168.1.0/24 directly, but not about 192.168.2.0/24 where PC1 lives. A static route is needed.

   Cisco IOS
   ```
   R0> enable
   R0# configure terminal
   R0(config)# interface GigabitEthernet0/0
   R0(config-if)#  ip address 192.168.1.1 255.255.255.0
   R0(config-if)#  no shutdown
   R0(config-if)# exit
   R0(config)# interface GigabitEthernet0/1
   R0(config-if)#  ip address 10.0.0.1 255.255.255.252
   R0(config-if)#  no shutdown
   R0(config-if)# exit
   !
   ! static route to reach PC1's network through R1
   R0(config)# ip route 192.168.2.0 255.255.255.0 10.0.0.2
   R0(config)# end
   R0# write memory
   ```
   - Syntax: `ip route <destination network> <mask> <next-hop IP | exit interface>`
   - A default route would instead be `ip route 0.0.0.0 0.0.0.0 10.0.0.2`.

   Return route on R1 (needed, or the reply cannot come back)
   ```
   R1(config)# ip route 192.168.1.0 255.255.255.0 10.0.0.1
   ```

   Huawei VRP
   ```
   [R0] interface GigabitEthernet0/0/1
   [R0-GigabitEthernet0/0/1] ip address 10.0.0.1 255.255.255.252
   [R0-GigabitEthernet0/0/1] quit
   [R0] ip route-static 192.168.2.0 255.255.255.0 10.0.0.2
   ```

   Juniper Junos
   ```
   user@R0# set interfaces ge-0/0/1 unit 0 family inet address 10.0.0.1/30
   user@R0# set routing-options static route 192.168.2.0/24 next-hop 10.0.0.2
   user@R0# commit
   ```

   Verification
   ```
   R0# show ip route
   R0# show ip route static
   R0# ping 192.168.2.10
   R0# traceroute 192.168.2.10
   ```
   - Points to remember: a static route needs a matching return route on the far side; the administrative distance of a static route is 1, so it beats any dynamic protocol; and on a broadcast link a next-hop IP address is preferred to an exit interface, because an exit interface alone forces proxy ARP.

3. **What is OSPF? Briefly Explain.** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1358 (ET: BUET)]*

   Answer: OSPF (Open Shortest Path First) is a link-state, classless interior gateway protocol used to find the best path inside one autonomous system. It is an open standard (RFC 2328), so it works between vendors.

   How it works
   - Step 1 — Neighbour discovery. Each router sends Hello packets to multicast 224.0.0.5 every 10 seconds on a broadcast link, and forms adjacencies with routers that agree on area, timers and authentication.
   - Step 2 — Link-state advertisement. Each router describes its own links and their costs in an LSA and floods it to every router in the area.
   - Step 3 — Link-state database. Every router in an area ends up with an identical LSDB, which is a complete map of the area's topology.
   - Step 4 — SPF calculation. Each router runs `Dijkstra's shortest path first algorithm` on that map, placing itself at the root, and computes the lowest-cost path to every network.
   - Step 5 — Routing table. The best paths are installed. Only incremental updates are flooded afterwards, plus a full refresh every 30 minutes.

   Key characteristics
   - Metric: `cost`, calculated as reference bandwidth ÷ interface bandwidth (default reference 100 Mbps). Lower is better.
   - Runs directly over IP as protocol number 89 — it does not use TCP or UDP.
   - Administrative distance 110.
   - Classless, so it carries the subnet mask and supports VLSM and CIDR.
   - Converges fast, because changes are flooded immediately rather than waiting for a periodic timer.
   - Supports equal-cost multipath load balancing.
   - Authentication (plain text or MD5) protects routing updates.

   Areas
   - Large networks are divided into areas to limit LSA flooding and SPF computation. Area 0 is the backbone, and every other area must connect to it, through an Area Border Router (ABR). An ASBR connects OSPF to an external routing domain.

   Router types and tables
   - Three tables: neighbour table, topology table (the LSDB) and routing table.
   - Router IDs, DR and BDR election on broadcast networks (to avoid every router adjacent to every other), with the DR at multicast 224.0.0.6.

   Advantages and drawbacks
   - Advantages: fast convergence, no hop-count limit, efficient use of bandwidth, hierarchical and scalable, vendor neutral.
   - Drawbacks: more CPU and memory than RIP, more complex to design and configure, and requires careful area planning.

4. **Which of the following is a pair of routing protocol?** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*
   * **(A) TCP and IP**
   * **(B) HTTP and FTP**
   * **(C) RIP and OSPF**
   * **(D) ARP and RARP**

   Answer: The correct option is `(C) RIP and OSPF`.

   - RIP (Routing Information Protocol) — a distance-vector interior gateway protocol using hop count as its metric, with a maximum of 15 hops. Based on the Bellman-Ford algorithm.
   - OSPF (Open Shortest Path First) — a link-state interior gateway protocol using cost (based on bandwidth) as its metric. Based on Dijkstra's algorithm.
   - Both build and maintain the IP routing table, which is precisely what makes them routing protocols.

   Why the others are wrong

   | Option | What they actually are |
   |---|---|
   | (A) TCP and IP | TCP is a transport protocol, IP is a routed (not routing) protocol |
   | (B) HTTP and FTP | Application-layer protocols for web and file transfer |
   | (C) `RIP and OSPF` | `Both are routing protocols — correct` |
   | (D) ARP and RARP | Address resolution protocols, mapping between IP and MAC |

   - Other routing protocols worth knowing: EIGRP (Cisco advanced distance vector), IS-IS (link state) and BGP (path vector, used between autonomous systems).
   - Important distinction: a routed protocol (IP) carries user data; a routing protocol (RIP, OSPF, BGP) carries the information routers use to build their tables.

5. **BGP is __________ protocol.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: BGP is a `path vector` routing protocol, and it is the `exterior gateway protocol (EGP)` of the internet.

   Key facts
   - Full form: Border Gateway Protocol. Current version is BGP-4 (RFC 4271).
   - Type: path vector — it advertises the complete AS_PATH, the list of autonomous systems a route has traversed, rather than a simple distance.
   - Use: routing `between` autonomous systems. It is what ties the whole internet together.
   - Transport: runs over `TCP port 179`, which gives it reliable delivery, so it needs no flooding mechanism of its own.
   - Administrative distance: 20 for eBGP, 200 for iBGP.
   - Metric: none in the usual sense. BGP chooses paths by `policy`, using attributes such as WEIGHT, LOCAL_PREF, AS_PATH length, ORIGIN and MED.

   Two forms
   - eBGP — between routers in different autonomous systems.
   - iBGP — between routers inside the same autonomous system, to carry external routes across it.

   Why the AS_PATH matters
   - Besides choosing the shortest path in AS terms, the AS_PATH prevents loops: a router rejects any advertisement that already contains its own AS number.

   - BGP is described as slow to converge and complex, but that is the price of carrying more than a million internet routes and of allowing each operator to express its own commercial routing policy.

6. **BGP stands for __________?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

   Answer: BGP stands for `Border Gateway Protocol`.

   - It is the exterior gateway protocol that routes traffic between autonomous systems, and it is what makes the global internet a single reachable network.
   - Current version: BGP-4, defined in RFC 4271.
   - It is a `path vector` protocol: it advertises the full AS_PATH, the list of autonomous systems a route has crossed.
   - It runs over `TCP port 179`, so delivery is reliable and ordered.
   - Administrative distance: 20 for eBGP, 200 for iBGP.
   - It selects paths by policy — WEIGHT, LOCAL_PREF, AS_PATH length, ORIGIN, MED — not by a simple metric.
   - The AS_PATH also prevents loops, since a router discards any route that already contains its own AS number.
   - Scale: the global BGP table now carries well over a million IPv4 prefixes.

7. **Which routing protocol use Dijkstra Algorithm?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

   Answer: `OSPF` (Open Shortest Path First) uses Dijkstra's algorithm, and so does `IS-IS`. Both are link-state protocols.

   How Dijkstra is used in OSPF
   - Every router floods LSAs describing its own links and their costs, so all routers in an area build an identical link-state database — a complete map of the topology.
   - Each router then runs Dijkstra's Shortest Path First algorithm on that map, placing itself at the root of the tree.
   - The algorithm repeatedly picks the nearest unvisited node, adds it to the tree, and relaxes the cost of its neighbours, until every network has a known lowest-cost path.
   - Those results become the routing table.
   - Metric: cost = reference bandwidth ÷ interface bandwidth, so faster links have lower cost.

   Algorithms used by the other protocols

   | Protocol | Type | Algorithm | Metric |
   |---|---|---|---|
   | RIP | Distance vector | Bellman-Ford | Hop count (max 15) |
   | `OSPF` | Link state | `Dijkstra (SPF)` | Cost from bandwidth |
   | IS-IS | Link state | `Dijkstra (SPF)` | Cost |
   | EIGRP | Advanced distance vector | DUAL (Diffusing Update Algorithm) | Composite: bandwidth and delay |
   | BGP | Path vector | Best-path selection by policy | Attributes, not a metric |

   - Note the pattern: link-state protocols need the whole topology, which is exactly what Dijkstra requires. Distance-vector protocols know only what their neighbours tell them, which is why they use Bellman-Ford instead.

8. **What is Routing? Explain different types of Routing? Why using benefit of an Adhoce routing? Which routing algorithm is used in shortest path algorithm?** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 525 (ET: MIST)]*

   Answer:

   What is routing
   - Routing is the process of selecting a path for traffic to travel from a source network to a destination network, and forwarding packets along that path. Routers do this using the destination IP address and a routing table, choosing the entry with the longest matching prefix.

   Types of routing

   1. Static routing — routes entered manually by the administrator.
   - Advantages: no CPU or bandwidth overhead, complete control, secure, predictable.
   - Disadvantages: no automatic reaction to a link failure, and unmanageable in a large network.

   2. Default routing — a single route (0.0.0.0/0) used for everything not matched elsewhere. Typical on a stub network with one exit.

   3. Dynamic routing — routers learn routes from each other automatically.
   - Interior Gateway Protocols, used inside one autonomous system:
     - Distance vector — RIP, IGRP. Each router tells its neighbours its whole table; Bellman-Ford.
     - Link state — OSPF, IS-IS. Each router floods a description of its links; every router runs Dijkstra on a complete map.
     - Advanced distance vector — EIGRP, which uses the DUAL algorithm and keeps a topology table.
   - Exterior Gateway Protocol — BGP, a path vector protocol used between autonomous systems.

   Benefits of ad hoc routing
   - Ad hoc routing is used in MANETs and sensor networks, where there is no fixed infrastructure and nodes move.
   - No infrastructure needed — the network can be created anywhere, instantly, which is why it suits disaster relief, military operations and temporary field deployments.
   - Self-organising and self-healing — nodes discover neighbours and repair routes automatically when a node moves or fails.
   - Multi-hop reach — a node can reach a distant node through intermediate nodes, extending range far beyond one radio hop.
   - Low cost and rapid deployment, with no towers, cabling or central controller.
   - Fault tolerance, because there is no single point of failure.
   - Protocol families: reactive (AODV, DSR — routes found on demand, low overhead), proactive (DSDV, OLSR — tables kept current, low latency) and hybrid (ZRP).

   Shortest path algorithm
   - The classic shortest-path algorithm used in routing is `Dijkstra's algorithm`, employed by the link-state protocols OSPF and IS-IS.
   - Distance-vector protocols such as RIP use the `Bellman-Ford` algorithm instead, which also finds shortest paths but converges more slowly and can suffer from the count-to-infinity problem.

9. **(b) Distinguish between routing and forwarding. What are the advantages of net specific routing over host specific routing?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 490 (ET: N/A)]*

   Answer:

   (a) Routing vs forwarding

   | Point | Routing | Forwarding |
   |---|---|---|
   | What it is | Deciding the paths — building the routing table | Moving one packet from an input port to the correct output port |
   | Time scale | Slow, in the background; seconds to minutes | Fast, per packet; nanoseconds |
   | Plane | Control plane | Data plane |
   | Inputs | Routing protocol messages, administrative configuration | The destination IP address in the packet header |
   | Output | The routing table (RIB), and from it the forwarding table (FIB) | The packet, sent out of one interface |
   | Implementation | Software, running RIP, OSPF, BGP | Hardware, ASIC or TCAM lookup |
   | Frequency | Runs when the topology changes | Runs for every single packet |

   - Analogy: routing is drawing the road map; forwarding is a driver reading the signpost at one junction and turning.
   - This separation is precisely what SDN exploits: it lifts the control plane out of the box and leaves only the forwarding plane behind.

   (b) Advantages of network-specific routing over host-specific routing
   - Host-specific routing keeps one entry per individual host; network-specific routing keeps one entry per whole network.

   - Much smaller routing tables. One entry for 192.168.1.0/24 replaces up to 254 host entries. On the internet this is the difference between a workable table and an impossible one.
   - Faster lookup, because there are fewer entries to search, which directly improves forwarding speed.
   - Less memory and cheaper hardware, since TCAM is expensive.
   - Less update traffic, because a network entry changes far less often than the set of hosts inside it.
   - Easier administration — adding a new PC to an existing subnet needs no routing change anywhere.
   - Better scalability, and it enables route aggregation (supernetting), where many networks are advertised as one prefix.
   - Faster convergence, because fewer entries have to be recomputed and re-advertised.

   - Host-specific routing is still used, sparingly, for special cases: a /32 route for a critical server, policy routing for one host, or troubleshooting. It is checked first, because the longest prefix always wins.

10. **Consider the following routing table at an IP router:** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 461 (ET: BUET)]*
| Network | Subnet mask | Outgoing Interface |
|---|---|---|
| 172.168.164.0 | 255.255.254.0 | Interface 0 |
| 172.168.166.0 | 255.255.254.0 | Interface 1 |
| 172.168.168.0 | 255.255.254.0 | Interface 2 |
| 172.168.170.0 | 255.255.254.0 | Interface 3 |
| 0.0.0.0 | Default | Interface 4 |

   **For each IP address in Group: I indentify the correct choice of the outgoing from Group: II using the entries from the routing table above.**
| Group: I | Group: II |
|---|---|
| 172.168.165.121 | Interface 0 |
| 172.168.167.151 | Interface 1 |
| 172.168.163.151 | Interface 2 |
| 172.168.171.92 | Interface 3 |
| 0.0.0.0 | Interface 4 |
*[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 462 (ET: BUET)]*

    Answer: The router uses `longest prefix match`. Each mask is 255.255.254.0 (/23), so each entry covers 2 consecutive values in the third octet.

    Step 1 — work out the range of each entry

    | Network | Mask | Range covered | Interface |
    |---|---|---|---|
    | 172.168.164.0 | /23 | 172.168.164.0 – 172.168.165.255 | Interface 0 |
    | 172.168.166.0 | /23 | 172.168.166.0 – 172.168.167.255 | Interface 1 |
    | 172.168.168.0 | /23 | 172.168.168.0 – 172.168.169.255 | Interface 2 |
    | 172.168.170.0 | /23 | 172.168.170.0 – 172.168.171.255 | Interface 3 |
    | 0.0.0.0 | default | Everything else | Interface 4 |

    Step 2 — match each address

    | Group: I address | Falls in | Outgoing interface |
    |---|---|---|
    | 172.168.165.121 | 164.0 – 165.255 | `Interface 0` |
    | 172.168.167.151 | 166.0 – 167.255 | `Interface 1` |
    | 172.168.163.151 | No entry matches (163 < 164) | `Interface 4` (default) |
    | 172.168.171.92 | 170.0 – 171.255 | `Interface 3` |
    | 0.0.0.0 | Matches only the default route | `Interface 4` |

    Working shown for the tricky ones
    - 172.168.163.151 — the third octet 163 is below the lowest configured network, 164. No specific entry covers it, so the default route is used.
    - 172.168.171.92 — 171 is the odd half of the 170/171 pair, so it belongs to 172.168.170.0/23.
    - Note that Interface 2 (172.168.168.0/23, covering third octets 168 and 169) is not used by any address in this list.

    - Rule to remember for a /23: the block always starts on an even third octet and covers that octet and the next one.

11. **Define distance Vector and Link state routing protocols.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 635 (ET: N/A)]*

    Answer:

    Distance vector routing
    - Each router knows only the distance (metric) and direction (next hop) to every destination — hence "distance vector".
    - It periodically sends its `entire routing table` to its `directly connected neighbours` only.
    - On receiving a neighbour's table it applies the Bellman-Ford equation: cost to X through neighbour N = cost to N + N's cost to X, keeping the minimum.
    - It has no map of the network; it trusts what neighbours say. This is "routing by rumour".
    - Convergence is slow, and the count-to-infinity problem can occur; it is limited by split horizon, route poisoning, poison reverse and hold-down timers.
    - Metric: usually hop count. RIP allows at most 15 hops, so 16 means unreachable.
    - Examples: RIP, RIPv2, IGRP. EIGRP is an advanced form using the DUAL algorithm.
    - Low CPU and memory use, easy to configure — suited to small networks.

    Link state routing
    - Each router discovers its own directly connected links and their costs, and floods this information as an LSA to `every router in the area`, not just to neighbours.
    - Every router therefore builds an identical link-state database — a complete map of the topology.
    - Each router independently runs `Dijkstra's SPF algorithm` on that map to compute the shortest path to every destination.
    - Updates are sent only when something changes (plus a periodic refresh), and they are flooded immediately, so convergence is fast.
    - Metric: cost, normally derived from bandwidth.
    - Examples: OSPF, IS-IS.
    - Needs more CPU and memory, and careful hierarchical design with areas — suited to large networks.

    | Point | Distance vector | Link state |
    |---|---|---|
    | Knowledge | Only what neighbours report | Full topology map |
    | Sends | Whole table, to neighbours | Link information, to everyone in the area |
    | Frequency | Periodic (RIP every 30 s) | On change only |
    | Algorithm | Bellman-Ford | Dijkstra |
    | Convergence | Slow | Fast |
    | Loops | Possible; needs split horizon and hold-down | Rare, because every router sees the same map |
    | Resources | Low CPU and memory | High CPU and memory |
    | Scale | Small networks | Large networks |

12. **What are static and dynamic routing? Given their relative advantages.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 635 (ET: N/A)]*

    Answer:

    Static routing
    - Routes are entered manually by the administrator with a command such as `ip route 192.168.2.0 255.255.255.0 10.0.0.2`.
    - The router never changes them by itself; if the path fails, traffic simply stops until someone edits the configuration.
    - Administrative distance is 1, so a static route beats every dynamic protocol.

    Dynamic routing
    - Routers exchange information automatically using a routing protocol — RIP, OSPF, EIGRP, IS-IS or BGP — and build their tables themselves.
    - When a link fails, the protocol detects it and recomputes an alternative path without human intervention.

    Relative advantages

    Advantages of static routing
    - No CPU, memory or bandwidth overhead — nothing is exchanged between routers.
    - Complete administrative control over exactly which path is used.
    - More secure: no routing updates to intercept, spoof or poison.
    - Predictable and easy to troubleshoot; the path never changes unexpectedly.
    - Ideal for a small network, a stub site with one exit, or a backup route with a higher administrative distance (a floating static route).

    Advantages of dynamic routing
    - Automatic adaptation — a failed link is routed around within seconds, with no human action.
    - Scalable — a network of hundreds of routers is impossible to maintain by hand.
    - Less administrative work; adding a new network is advertised automatically.
    - Load balancing across equal-cost (and in EIGRP, unequal-cost) paths.
    - Chooses the best path by a real metric, and keeps choosing it as conditions change.
    - Fewer human errors than manual entry.

    Disadvantages of each
    - Static: no fault tolerance, unmanageable at scale, and every change is a manual change.
    - Dynamic: consumes CPU, memory and bandwidth; more complex to design and troubleshoot; and routing updates are a security surface, which is why authentication is used.

    When to use which
    - Static — small networks, stub sites, default routes to an ISP, backup routes, and specific policy exceptions.
    - Dynamic — medium and large networks, any network with redundant paths, and anywhere fast automatic recovery is needed.
    - Most real networks use both: dynamic routing internally, and a static default route pointing at the ISP.

13. **What is Routing? Write down the difference between static routing and dynamic routing.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 837-838 (ET: N/A)]*

    Answer:

    What is routing
    - Routing is the process of choosing a path for traffic from a source network to a destination network, and forwarding packets along it. A router looks at the destination IP address of each packet and consults its routing table, selecting the entry with the longest matching prefix.
    - The routing table can be filled in three ways: directly connected networks, static routes and dynamic routing protocols.

    Static routing vs dynamic routing

    | Point | Static routing | Dynamic routing |
    |---|---|---|
    | Configuration | Entered manually by the administrator | Learned automatically by a routing protocol |
    | Adaptation | None; a failed link stops traffic | Automatic reroute within seconds |
    | Protocols used | None | RIP, OSPF, EIGRP, IS-IS, BGP |
    | CPU and memory | Almost none | Significant |
    | Bandwidth | None used | Routing updates consume bandwidth |
    | Administrative distance | 1 | RIP 120, OSPF 110, EIGRP 90, eBGP 20 |
    | Security | High — nothing to intercept or spoof | Lower; updates need authentication |
    | Scalability | Poor beyond a few routers | Excellent |
    | Complexity | Simple to write, hard to maintain at scale | Complex to design, easy to maintain |
    | Predictability | Completely predictable | Path may change with conditions |
    | Best suited to | Small or stub networks, default routes, backup routes | Medium and large networks with redundant paths |

    - Most production networks combine the two: a dynamic protocol inside the organisation, and a static default route towards the ISP.
    - A floating static route (a static route with a deliberately high administrative distance) is a common way to provide a backup path that only activates when the dynamic route disappears.

14. **Name of the Algorithm RIP, OSPF and EIGRP routing protocol.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 838 (ET: N/A)]*

    Answer: The algorithm used by each protocol.

    | Protocol | Full form | Type | Algorithm | Metric |
    |---|---|---|---|---|
    | RIP | Routing Information Protocol | Distance vector | `Bellman-Ford` | Hop count, maximum 15 |
    | OSPF | Open Shortest Path First | Link state | `Dijkstra (Shortest Path First)` | Cost = reference bandwidth ÷ interface bandwidth |
    | EIGRP | Enhanced Interior Gateway Routing Protocol | Advanced distance vector (hybrid) | `DUAL — Diffusing Update Algorithm` | Composite: bandwidth and delay by default |

    Brief notes
    - RIP / Bellman-Ford — each router adds one hop to what its neighbours report and keeps the minimum. Simple, but slow to converge and vulnerable to count-to-infinity, which is why split horizon and hold-down timers are needed. Updates every 30 seconds. Administrative distance 120.
    - OSPF / Dijkstra — every router floods LSAs, builds an identical map of the area, and computes the shortest-path tree with itself at the root. Fast convergence, no hop limit, scales with areas. Runs on IP protocol 89. Administrative distance 110.
    - EIGRP / DUAL — keeps a topology table with a successor (best route) and a feasible successor (a pre-verified loop-free backup). If the successor fails, the feasible successor is installed immediately with no recomputation, which gives near-instant convergence. Administrative distance 90 (internal). It is Cisco-originated but was published as RFC 7868.

    - Also worth knowing: IS-IS uses Dijkstra like OSPF, and BGP uses no shortest-path algorithm at all — it selects by policy attributes.

15. **What is Autonomous system? What is the difference between Link state routing protocol and Distance vector routing protocol?** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 838-839 (ET: N/A)]*

    Answer:

    What is an autonomous system
    - An Autonomous System (AS) is a collection of IP networks and routers under a single administrative authority that presents a common, clearly defined routing policy to the internet.
    - Each AS is identified by a globally unique Autonomous System Number (ASN), assigned by IANA through the regional registries. ASNs were originally 16 bits (1–65535) and are now 32 bits; 64512–65534 is reserved for private use.
    - Examples: an ISP, a large university, a bank with its own internet presence, or a content provider such as Google (AS15169).
    - Routing inside an AS uses an Interior Gateway Protocol (RIP, OSPF, EIGRP, IS-IS); routing between autonomous systems uses the Exterior Gateway Protocol BGP.
    - The purpose of the concept is scalability: the internet is not treated as millions of individual routers but as tens of thousands of autonomous systems, each of which internally does what it likes.

    Link state vs distance vector

    | Point | Distance vector | Link state |
    |---|---|---|
    | What each router knows | Distance and next hop only, as reported by neighbours | The full topology of the area |
    | What it sends | Its entire routing table | Information about its own links (LSAs) |
    | Sends to | Directly connected neighbours only | Every router in the area, by flooding |
    | When it sends | Periodically (RIP every 30 s) plus on change | Only when something changes, plus periodic refresh |
    | Algorithm | Bellman-Ford | Dijkstra (SPF) |
    | Convergence | Slow | Fast |
    | Loop risk | Real; needs split horizon, poison reverse, hold-down | Very low, since all routers share one map |
    | Count to infinity | Possible | Not possible |
    | CPU and memory | Low | High |
    | Bandwidth used | Higher (whole table, repeatedly) | Lower after the initial flood |
    | Hierarchy | None | Areas, with a backbone area 0 |
    | Scale | Small networks | Large networks |
    | Examples | RIP, RIPv2, IGRP | OSPF, IS-IS |

    - EIGRP sits between the two: it is a distance-vector protocol at heart, but its DUAL algorithm and topology table give it link-state-like convergence speed.

16. **Cost calculation of EIGRP formula.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 839 (ET: N/A)]*

    Answer: EIGRP uses a composite metric built from up to five components, weighted by the K values.

    Full formula
    ```
    Metric = 256 × [ (K1 × Bandwidth) + (K2 × Bandwidth) / (256 − Load) + (K3 × Delay) ]
                  × [ K5 / (Reliability + K4) ]
    ```
    - The last bracket is applied only when K5 is not zero.

    Default K values
    ```
    K1 = 1, K2 = 0, K3 = 1, K4 = 0, K5 = 0
    ```

    Simplified default formula
    - With the defaults, the load, reliability and MTU terms drop out entirely:
    ```
    Metric = 256 × (Bandwidth + Delay)
    ```
    where
    ```
    Bandwidth = 10,000,000 / (minimum bandwidth in kbps along the path)
    Delay     = (sum of all interface delays in microseconds) / 10
    ```

    Worked example
    - Path: FastEthernet (100,000 kbps, delay 100 µs) then Serial (1544 kbps, delay 20,000 µs).
    - Minimum bandwidth along the path = 1544 kbps
    ```
    Bandwidth term = 10,000,000 / 1544        = 6476  (integer division)
    Delay term     = (100 + 20,000) / 10      = 2010
    Metric         = 256 × (6476 + 2010)      = 256 × 8486 = 2,172,416
    ```

    Points to remember
    - Only the `minimum` bandwidth on the whole path is used, but the `sum` of all delays.
    - Bandwidth is expressed in kbps and delay in tens of microseconds; both use integer arithmetic, so remainders are discarded.
    - Load and reliability are excluded by default because they change constantly, and a metric that keeps changing causes route flapping.
    - The K values must match on both routers or the neighbour adjacency will not form.
    - Administrative distance: 90 for internal EIGRP, 170 for external.

17. **Given a totology of distance vector routing. Find the table of each node for the 1^{\text{st}} route.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 859-860 (ET: N/A)]*

    Answer: The topology figure was not printed with the question, so the distance-vector procedure is given with a worked example that can be adapted to any topology.

    The algorithm (Bellman-Ford, as used by RIP)
    - Step 1 — Initialisation. Each node's table contains 0 to itself, the link cost to each direct neighbour, and infinity to every other node.
    - Step 2 — Exchange. Each node sends its whole distance vector to its direct neighbours only.
    - Step 3 — Update. On receiving neighbour N's vector, node X computes for every destination D:
    ```
    cost(X, D) = min over all neighbours N of [ cost(X, N) + cost(N, D) ]
    ```
    and records N as the next hop for the minimum.
    - Step 4 — Repeat until no table changes. That state is convergence.

    Worked example
    ```
            2          3
       A -------- B -------- C
        \                   /
         \_______ 7 _______/
    ```

    Initial tables (round 0 — direct links only)

    | From A | Cost | Next hop |
    |---|---|---|
    | A | 0 | — |
    | B | 2 | B |
    | C | 7 | C |

    | From B | Cost | Next hop |
    |---|---|---|
    | A | 2 | A |
    | B | 0 | — |
    | C | 3 | C |

    | From C | Cost | Next hop |
    |---|---|---|
    | A | 7 | A |
    | B | 3 | B |
    | C | 0 | — |

    After the first exchange (round 1)
    - A learns from B that B reaches C at cost 3. A's cost to C via B = 2 + 3 = `5`, which is better than the direct 7. A updates.
    - C learns from B that B reaches A at cost 2. C's cost to A via B = 3 + 2 = `5`, better than the direct 7. C updates.
    - B already has the best routes to both neighbours, so B does not change.

    | From A | Cost | Next hop |
    |---|---|---|
    | A | 0 | — |
    | B | 2 | B |
    | C | `5` | `B` |

    | From C | Cost | Next hop |
    |---|---|---|
    | A | `5` | `B` |
    | B | 3 | B |
    | C | 0 | — |

    - Round 2 produces no further change, so the network has converged.

    Key points for the exam
    - Each node knows only distances and next hops, never the full topology — "routing by rumour".
    - Convergence is slow, and the count-to-infinity problem can arise when a link fails; split horizon, route poisoning, poison reverse and hold-down timers are the standard countermeasures.
    - RIP uses hop count with a maximum of 15, so 16 means unreachable. <!-- verify -->

18. **What is difference between link state routing and distance vector routing?** *[Sonali Bank Ltd. Officer IT 2021 compact it 909 (ET: N/A)]*

    Answer:

    | Point | Distance vector routing | Link state routing |
    |---|---|---|
    | What each router knows | Only the distance and direction reported by its neighbours | A complete map of the whole area |
    | Information sent | The entire routing table | Only its own link information (LSA) |
    | Sent to | Directly connected neighbours | Every router in the area, by flooding |
    | When sent | Periodically (RIP every 30 s) and on change | Only when a change occurs, plus a periodic refresh |
    | Algorithm | Bellman-Ford | Dijkstra (Shortest Path First) |
    | Metric | Usually hop count | Cost, derived from bandwidth |
    | Convergence | Slow | Fast |
    | Routing loops | Possible; needs split horizon, poison reverse, hold-down | Very unlikely, since all routers share one map |
    | Count to infinity | Can occur | Cannot occur |
    | CPU and memory | Low | High |
    | Bandwidth used | Higher — the whole table, repeatedly | Lower after the initial flood |
    | Hierarchy | None | Areas, with backbone area 0 |
    | Scalability | Small networks | Large networks |
    | Configuration | Simple | Complex, needs area design |
    | Examples | RIP, RIPv2, IGRP | OSPF, IS-IS |

    Core distinction
    - Distance vector: "tell your neighbours everything you know."
    - Link state: "tell everyone what you know about yourself."
    - That single difference explains the rest of the table — the algorithm each can use, the convergence speed, the loop behaviour and the resource cost.
    - EIGRP is a hybrid: distance vector in principle, but its DUAL algorithm and pre-computed feasible successors give it link-state-like convergence.

## Transport Layer (TCP & UDP) (17)

1. A client needs to send 4000\text{ bytes} of data to a database server. The client divides the data into packets of 500\text{ bytes} each. The sequence number of the first packet is 3001. After 2500\text{ bytes} have been successfully sent, 2 packets are lost/failed. Assuming TCP cumulative ACK, complete the following table: [BSCCPL AME 21-08-2026 (BUET)]

| SL | Client Packet Sequence No. | DB Server Sequence No. | ACK Sequence No. |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |
| 4 | | | |
| 5 | | | |
| 6 | | | |
| 7 | | | |
| 8 | | | |

Assumption: The first 5 packets (2500\text{ bytes}) are sent successfully. Packets 6 and 7 are lost, while packet 8 arrives. The server sends a cumulative ACK for the next byte it is expecting. Find the missing values in the table.

   Answer:

   Setting up the numbering
   - Total data = 4000 bytes, packet size = 500 bytes, so there are 4000 ÷ 500 = `8 packets`.
   - The first packet's sequence number is 3001. In TCP the sequence number is the number of the FIRST byte in that segment, so each following packet's sequence number is 500 higher.
   - The ACK number is the number of the NEXT byte the server expects, so ACK = last byte received + 1. This is what "cumulative ACK" means.
   - The server sends only acknowledgements and no data of its own, so the server's own sequence number never advances. It is written as `y` below (the server's ISN + 1, fixed for the whole exchange).

   Completed table

   | SL | Client Packet Sequence No. | DB Server Sequence No. | ACK Sequence No. |
   |---|---|---|---|
   | 1 | 3001 (bytes 3001–3500) | y | 3501 |
   | 2 | 3501 (bytes 3501–4000) | y | 4001 |
   | 3 | 4001 (bytes 4001–4500) | y | 4501 |
   | 4 | 4501 (bytes 4501–5000) | y | 5001 |
   | 5 | 5001 (bytes 5001–5500) | y | 5501 |
   | 6 | 5501 (bytes 5501–6000) — `LOST` | — | no ACK sent |
   | 7 | 6001 (bytes 6001–6500) — `LOST` | — | no ACK sent |
   | 8 | 6501 (bytes 6501–7000) — arrives | y | `5501` (duplicate ACK) |

   Explanation of the key rows
   - Rows 1–5: 2500 bytes arrive in order. Each ACK simply advances by 500, ending at 5501, meaning "I have everything up to byte 5500, send me 5501 next."
   - Rows 6 and 7: these segments never arrive, so the server generates nothing for them.
   - Row 8: packet 8 arrives, but out of order. Because ACKs are cumulative, the server cannot acknowledge byte 6501 while 5501–6500 is missing. It repeats `ACK 5501`, which is a `duplicate ACK`. It stores packet 8 in its out-of-order buffer.

   What happens next
   - Three duplicate ACKs for 5501 trigger `fast retransmit` at the client, which resends packet 6 (seq 5501) without waiting for the retransmission timer.
   - Once 5501–6000 arrives, the server can acknowledge only up to 6001, because 6001–6500 is still missing, so it sends ACK 6001.
   - After packet 7 (seq 6001) is retransmitted and arrives, the server has bytes 3001–7000 complete, including the buffered packet 8, and sends `ACK 7001`.

   | Retransmission | Client sends | Server ACK |
   |---|---|---|
   | 1st | seq 5501 | 6001 |
   | 2nd | seq 6001 | `7001` (all 4000 bytes received) |

   - The final ACK of 7001 confirms 3001 + 4000 = 7001, so the whole 4000 bytes have been delivered.
   - With SACK (Selective Acknowledgement) enabled, the server could have told the sender in row 8 that it already had 6501–7000, so only the two genuinely missing segments would be resent. Plain cumulative ACK cannot express that.

2. **(b) Distinguish between TCP and UDP protocols.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 886 (ET: N/A)], [Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)], [BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 694 (ET: N/A)]*

   Answer:

   | Point | TCP | UDP |
   |---|---|---|
   | Full form | Transmission Control Protocol | User Datagram Protocol |
   | Connection | Connection-oriented — three-way handshake first | Connectionless — just send |
   | Reliability | Reliable; lost data is retransmitted | Unreliable; no retransmission |
   | Acknowledgement | Yes, every segment is acknowledged | No |
   | Ordering | Guaranteed, using sequence numbers | Not guaranteed; datagrams may arrive out of order |
   | Error control | Checksum plus retransmission | Checksum only; a bad datagram is discarded |
   | Flow control | Yes, sliding window | No |
   | Congestion control | Yes — slow start, congestion avoidance | No |
   | Header size | 20 bytes minimum (up to 60 with options) | 8 bytes, fixed |
   | Speed | Slower, because of the overhead | Faster |
   | Overhead | High | Very low |
   | Data unit | Segment | Datagram |
   | Broadcast / multicast | Not supported | Supported |
   | Use when | Data must arrive complete and in order | Speed matters more than perfection |
   | Examples | HTTP, HTTPS, FTP, SMTP, SSH, Telnet | DNS, DHCP, TFTP, SNMP, VoIP, streaming, online games |

   Summary
   - TCP is like registered post: slower, but you get a delivery confirmation and nothing is lost.
   - UDP is like an ordinary postcard: fast and cheap, but there is no guarantee it arrives.
   - A missing byte in a bank transfer is unacceptable, so TCP is used. A missing frame in a live video is barely noticed, and waiting for it would be worse than losing it, so UDP is used.

3. **Show the pictorial representation of TCP 3-way handshaking protocol for establishing a connection between a server and a client.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1339 (ET: N/A)]*

   Answer: TCP establishes a connection with a three-way handshake before any data is sent, so that both sides agree on initial sequence numbers and confirm the other side is ready.

   Pictorial representation
   ```
      CLIENT                                        SERVER
         |                                             |
         |   1. SYN                                    |
         |     seq = x   (client's ISN)                |
         |     SYN flag = 1                            |
         |-------------------------------------------->|
         |                                             |
         |   2. SYN + ACK                              |
         |     seq = y   (server's ISN)                |
         |     ack = x + 1                             |
         |     SYN = 1, ACK = 1                        |
         |<--------------------------------------------|
         |                                             |
         |   3. ACK                                    |
         |     seq = x + 1                             |
         |     ack = y + 1                             |
         |     ACK = 1                                 |
         |-------------------------------------------->|
         |                                             |
         |============ CONNECTION ESTABLISHED =========|
         |            data transfer begins             |
   ```

   The three steps
   - Step 1 — SYN. The client picks a random initial sequence number x and sends a segment with the SYN flag set. It also advertises its window size and MSS. The client moves to SYN-SENT.
   - Step 2 — SYN + ACK. The server picks its own random ISN y, acknowledges the client's SYN with ack = x + 1, and sets both SYN and ACK flags. The server moves to SYN-RECEIVED.
   - Step 3 — ACK. The client acknowledges the server's SYN with ack = y + 1. Both sides move to ESTABLISHED, and data can flow.

   Why three steps and not two
   - Both directions must be synchronised. Step 1 and step 2 open and confirm the client-to-server direction; step 2 and step 3 open and confirm the server-to-client direction. Two messages could only synchronise one direction.
   - Random ISNs prevent an old, delayed segment from a previous connection being mistaken for current data, and make blind spoofing much harder.

   Related points
   - Closing the connection takes four steps (FIN, ACK, FIN, ACK), because each direction is closed independently.
   - The SYN flood attack exploits this handshake: the attacker sends many SYNs and never sends the final ACK, filling the server's half-open connection table. SYN cookies are the standard defence.

4. **What is the deference between TCP and UDP?** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*

   Answer:

   | Point | TCP | UDP |
   |---|---|---|
   | Connection | Connection-oriented (three-way handshake) | Connectionless |
   | Reliability | Reliable — retransmits lost data | Unreliable — no retransmission |
   | Acknowledgement | Yes | No |
   | Ordering | Guaranteed by sequence numbers | Not guaranteed |
   | Flow control | Yes, sliding window | No |
   | Congestion control | Yes | No |
   | Header | 20 bytes minimum | 8 bytes fixed |
   | Speed | Slower | Faster |
   | Data unit | Segment | Datagram |
   | Broadcast | Not supported | Supported |
   | Examples | HTTP, HTTPS, FTP, SMTP, SSH | DNS, DHCP, TFTP, SNMP, VoIP, video streaming |

   - Core idea: TCP guarantees delivery and pays for it in speed and overhead; UDP gives up the guarantee to gain speed and simplicity.
   - Choose TCP when every byte matters (file transfer, web pages, email). Choose UDP when timeliness matters more than completeness (live voice, video, DNS queries, gaming).

5. **3-way handshake protocol for TCP connection using diagram.** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 403 (ET: N/A)], [BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 876-877 (ET: BUET)]*

   Answer: The three-way handshake is how TCP opens a connection and synchronises sequence numbers in both directions.

   Diagram
   ```
      CLIENT                                        SERVER
      (CLOSED)                                      (LISTEN)
         |                                             |
         |  SYN, seq = x                               |
         |-------------------------------------------->|
      (SYN-SENT)                                (SYN-RECEIVED)
         |                                             |
         |  SYN + ACK, seq = y, ack = x + 1            |
         |<--------------------------------------------|
         |                                             |
         |  ACK, seq = x + 1, ack = y + 1              |
         |-------------------------------------------->|
     (ESTABLISHED)                               (ESTABLISHED)
         |                                             |
         |============== data transfer ================|
   ```

   Steps
   - 1. SYN — the client chooses a random initial sequence number x, sets the SYN flag, and sends it along with its window size and MSS.
   - 2. SYN + ACK — the server chooses its own random ISN y, acknowledges with ack = x + 1, and sets SYN and ACK together in one segment.
   - 3. ACK — the client acknowledges the server's ISN with ack = y + 1. The connection is now open in both directions.

   Why three
   - Each direction needs its own sequence number synchronised and confirmed. Steps 1–2 handle client to server; steps 2–3 handle server to client. Merging the server's SYN and ACK into one segment is what reduces four messages to three.

   Connection termination — four-way
   ```
      Client  --- FIN ------------------->  Server
      Client  <-- ACK -------------------   Server
      Client  <-- FIN -------------------   Server
      Client  --- ACK ------------------->  Server   (then TIME-WAIT)
   ```
   - Closing takes four steps because TCP connections are full duplex, so each direction must be closed separately.

6. **Write a TCP/UDP used service name?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

   Answer: Services and their transport protocol.

   Services that use TCP

   | Service | Port | Why TCP |
   |---|---|---|
   | HTTP | 80 | A web page must arrive complete and in order |
   | HTTPS | 443 | Same, plus TLS needs a reliable stream |
   | FTP | 20 (data), 21 (control) | A file must be byte-perfect |
   | SMTP | 25, 587 | Email must not lose text |
   | POP3 / IMAP | 110 / 143 | Mail retrieval must be reliable |
   | SSH | 22 | An interactive shell must not lose characters |
   | Telnet | 23 | Same, without encryption |
   | BGP | 179 | Routing updates must be reliable |
   | LDAP | 389 | Directory queries |

   Services that use UDP

   | Service | Port | Why UDP |
   |---|---|---|
   | DNS | 53 | One small query and reply; speed matters, retry is cheap |
   | DHCP | 67, 68 | Broadcast is needed, which TCP cannot do |
   | TFTP | 69 | Deliberately simple, for booting devices |
   | SNMP | 161, 162 | Small, frequent monitoring messages |
   | NTP | 123 | Time sync; a late packet is useless anyway |
   | RIP | 520 | Periodic routing broadcasts |
   | VoIP (RTP) | dynamic | Retransmitting late audio is worse than dropping it |
   | Video streaming, online games | dynamic | Low latency matters more than perfection |

   Services that use both
   - DNS — UDP 53 for normal queries, TCP 53 for zone transfers and responses over 512 bytes.
   - HTTP/3 — runs over QUIC, which is built on UDP but adds its own reliability.

7. **Difference between TCP and UDP. Distinguish between Cat5 and Cat6. Difference among exFAT, FAT32 and NTFS.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 523 (ET: MIST)]*

   Answer:

   (a) TCP vs UDP

   | Point | TCP | UDP |
   |---|---|---|
   | Connection | Connection-oriented, three-way handshake | Connectionless |
   | Reliability | Reliable, retransmits losses | Unreliable |
   | Ordering | Guaranteed | Not guaranteed |
   | Flow / congestion control | Yes | No |
   | Header | 20 bytes minimum | 8 bytes |
   | Speed | Slower | Faster |
   | Broadcast | No | Yes |
   | Examples | HTTP, FTP, SMTP, SSH | DNS, DHCP, VoIP, streaming |

   (b) Cat5 vs Cat6

   | Point | Cat5e | Cat6 |
   |---|---|---|
   | Bandwidth | 100 MHz | 250 MHz |
   | Max speed | 1 Gbps up to 100 m | 10 Gbps up to 55 m, 1 Gbps to 100 m |
   | Crosstalk | Higher | Much lower, tighter twists |
   | Separator | None | A plastic spline separates the pairs |
   | Cable diameter | Thinner, easier to pull | Thicker, stiffer |
   | Cost | Lower | Higher |
   | Use | General office networking | Backbone runs, data centres, PoE++ |

   - Cat6a extends 10 Gbps to the full 100 m, at 500 MHz. Plain Cat5 (not 5e) is limited to 100 Mbps and is obsolete.

   (c) exFAT vs FAT32 vs NTFS

   | Point | FAT32 | exFAT | NTFS |
   |---|---|---|---|
   | Max file size | 4 GB | 16 EB (effectively unlimited) | 16 EB |
   | Max volume size | 2 TB (32 GB in the Windows formatter) | 128 PB | 256 TB |
   | Journaling | No | No | Yes — recovers after a crash |
   | Permissions and security | No | No | Yes — ACLs, encryption (EFS) |
   | Compression / quotas | No | No | Yes |
   | Compatibility | Almost every device ever made | Windows, macOS, modern Linux, most cameras | Windows fully; macOS read-only by default |
   | Best for | Small USB sticks, very old devices | Large USB drives and SD cards used across systems | Windows system and internal drives |

   - Rule of thumb: NTFS for the Windows system drive, exFAT for a large removable drive shared between operating systems, FAT32 only when maximum compatibility with old hardware is required.

8. **Show a 3-way handshake protocol in TCP connection established using a diagram.** *[BICIC Assistant Programmer 2022 compact it 630 (ET: BUET)]*

   Answer: The three-way handshake opens a TCP connection and synchronises sequence numbers in both directions before any data is sent.

   Diagram
   ```
      CLIENT                                        SERVER
      (CLOSED)                                      (LISTEN)
         |                                             |
         |  (1) SYN                                    |
         |      SYN = 1, seq = x                       |
         |-------------------------------------------->|
      (SYN-SENT)                                (SYN-RECEIVED)
         |                                             |
         |  (2) SYN + ACK                              |
         |      SYN = 1, ACK = 1                       |
         |      seq = y, ack = x + 1                   |
         |<--------------------------------------------|
         |                                             |
         |  (3) ACK                                    |
         |      ACK = 1                                |
         |      seq = x + 1, ack = y + 1               |
         |-------------------------------------------->|
      (ESTABLISHED)                              (ESTABLISHED)
         |                                             |
         |=========== data transfer begins ============|
   ```

   What each step does
   - (1) The client sends SYN with a random ISN x, plus its window size and MSS. This synchronises the client-to-server direction.
   - (2) The server replies with its own random ISN y and acknowledges x + 1. One segment carries both SYN and ACK, which is why the handshake is three steps and not four.
   - (3) The client acknowledges y + 1. Both directions are now synchronised and the connection is ESTABLISHED.

   Notes
   - Random ISNs stop an old delayed segment being accepted into a new connection, and make blind spoofing difficult.
   - Termination requires four steps (FIN, ACK, FIN, ACK) because each direction closes independently.
   - SYN flooding attacks this handshake by never sending step 3; SYN cookies defend against it.

9. **Differecne between TCP and UDP.** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 658 (ET: N/A)]*

   Answer:

   | Point | TCP | UDP |
   |---|---|---|
   | Full form | Transmission Control Protocol | User Datagram Protocol |
   | Connection | Connection-oriented | Connectionless |
   | Handshake | Three-way handshake before data | None |
   | Reliability | Reliable — lost segments are retransmitted | Unreliable — no retransmission |
   | Acknowledgement | Every segment acknowledged | None |
   | Sequencing | Guaranteed in-order delivery | No ordering |
   | Flow control | Sliding window | None |
   | Congestion control | Slow start, congestion avoidance, fast recovery | None |
   | Error checking | Checksum plus recovery | Checksum only, bad datagrams discarded |
   | Header size | 20–60 bytes | 8 bytes |
   | Data unit | Segment | Datagram |
   | Speed | Slower | Faster |
   | Overhead | High | Very low |
   | Broadcast / multicast | Not supported | Supported |
   | Weight | Heavyweight | Lightweight |
   | Examples | HTTP, HTTPS, FTP, SMTP, SSH, Telnet | DNS, DHCP, TFTP, SNMP, NTP, VoIP, streaming, gaming |

   - Choose TCP when correctness matters more than speed; choose UDP when timeliness matters more than completeness.

10. **What is UDP protocol? UDP is reliable or not? Explain why or why not?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 754 (ET: N/A)]*

    Answer:

    What is UDP
    - UDP (User Datagram Protocol) is a connectionless transport-layer protocol defined in RFC 768. It simply wraps the application's data in an 8-byte header and hands it to IP.
    - Header fields: source port, destination port, length and checksum — nothing else.
    - No handshake, no acknowledgements, no sequence numbers, no retransmission, no flow control, no congestion control.
    - Data unit: datagram. It supports broadcast and multicast, which TCP does not.

    Is UDP reliable? — `No, UDP is not reliable.`

    Why it is unreliable
    - No acknowledgement — the sender never learns whether the datagram arrived. It sends and forgets.
    - No retransmission — a datagram lost to congestion, a full buffer or a bit error is simply gone.
    - No sequencing — datagrams may take different paths and arrive out of order, and UDP will not reorder them.
    - No duplicate detection — the same datagram may be delivered twice with no complaint.
    - No flow control — a fast sender can overwhelm a slow receiver, and the excess is dropped.
    - No congestion control — UDP keeps sending at the same rate even when the network is saturated, which can make congestion worse.
    - Its only error check is the checksum, and a datagram that fails it is silently discarded rather than repaired.

    Why UDP is still used, and used heavily
    - Speed — no handshake means no setup delay, so a DNS query and its reply take one round trip instead of four.
    - Low overhead — 8 header bytes against TCP's 20, which matters greatly for small messages.
    - No head-of-line blocking — in live audio or video, waiting for a lost packet ruins the stream. Dropping it and moving on is the correct behaviour.
    - Broadcast and multicast are possible, which is why DHCP and IPTV need UDP.
    - Statelessness lets a server handle far more clients, since there is no per-connection state to keep.
    - Applications that need reliability can add it themselves at the application layer, tuned to their own needs — this is exactly what QUIC (and therefore HTTP/3) does on top of UDP.

    - Uses: DNS, DHCP, TFTP, SNMP, NTP, RTP for voice and video, online games, and QUIC.

11. **The primary function of the Transmission Control Protocol (TCP). TCP performs six basic functions. What are the basic function performing by TCP?** *[BTRC Assistant Director (Technical) 2021 compact it 807-808 (ET: IBA)]*

    Answer: The primary function of TCP is to provide reliable, ordered, error-checked delivery of a byte stream between two applications, turning the unreliable, best-effort service of IP into something an application can depend on.

    The six basic functions

    1. Connection establishment and termination
    - Sets up a connection with the three-way handshake (SYN, SYN-ACK, ACK) before any data flows, and closes it with a four-way exchange (FIN, ACK, FIN, ACK). Both sides agree on initial sequence numbers and options such as MSS and window scaling.

    2. Segmentation and reassembly
    - Breaks the application's byte stream into segments no larger than the MSS, numbers every byte, and reassembles them in the correct order at the receiver, regardless of the order in which they arrived.

    3. Reliable delivery — acknowledgement and retransmission
    - Every segment is acknowledged. If an ACK does not arrive before the retransmission timer expires, or three duplicate ACKs are seen, the segment is retransmitted. This is what makes an unreliable network reliable.

    4. Error control
    - A 16-bit checksum covers the header, the data and a pseudo-header containing the IP addresses. A corrupted segment is discarded and, because it is never acknowledged, it is retransmitted. Duplicates are detected and dropped using sequence numbers.

    5. Flow control
    - The receiver advertises a window size in every ACK, stating how many more bytes it can accept. The sender never has more than that amount unacknowledged, so a fast sender cannot overwhelm a slow receiver. This is the sliding window mechanism.

    6. Congestion control
    - TCP infers network congestion from packet loss and adjusts its sending rate: slow start, congestion avoidance, fast retransmit and fast recovery. This protects the network itself, not just the receiver.

    Also commonly listed
    - Multiplexing with port numbers, so many applications share one IP address; and full-duplex operation, with independent data flow and sequence numbering in each direction.

12. **(c) What is purpose of routers? How congestion control works in the TCP?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 886-887 (ET: N/A)]*

    Answer:

    (a) Purpose of routers
    - To connect different networks and forward packets between them, using the destination IP address and a routing table with longest prefix match.
    - To determine the best path among several possible routes, using static entries or dynamic protocols such as RIP, OSPF, EIGRP and BGP.
    - To separate broadcast domains — a router does not forward broadcasts, which stops a broadcast storm in one LAN affecting others.
    - To perform NAT, translating private addresses to a public one so many hosts share one public IP.
    - To act as the default gateway for hosts, and to provide DHCP service.
    - To filter traffic with access control lists, and often to provide firewall and VPN functions.
    - To fragment packets that exceed the next link's MTU and to decrement the TTL, which kills looping packets.
    - To interconnect different media and technologies — Ethernet on one side, a serial or fibre WAN link on the other.

    (b) How congestion control works in TCP
    - TCP has no direct signal from the network, so it infers congestion from `packet loss` and adjusts its sending rate. It keeps a congestion window (cwnd) alongside the receiver's advertised window, and sends the minimum of the two.

    The four phases

    - 1. Slow start
      - cwnd begins at 1 MSS and doubles every round-trip time (it increases by 1 MSS for every ACK received), so growth is exponential.
      - It continues until cwnd reaches the slow-start threshold (ssthresh) or a loss occurs.
      - Despite the name, this is the fastest-growing phase; it is "slow" only because it starts from 1.

    - 2. Congestion avoidance
      - Once cwnd exceeds ssthresh, growth becomes linear: cwnd increases by about 1 MSS per round-trip time.
      - This probes carefully for extra capacity instead of doubling into congestion.

    - 3. Fast retransmit
      - Three duplicate ACKs indicate one segment was lost while later segments arrived. TCP retransmits it immediately, without waiting for the timeout.

    - 4. Fast recovery
      - After a fast retransmit, ssthresh is halved and cwnd is set to the new ssthresh, so sending continues at a reduced rate rather than collapsing to 1 MSS.
      - A full timeout is treated as much more serious: ssthresh is halved, cwnd drops to 1 MSS, and slow start begins again.

    ```
    cwnd
      |            /\        /\
      |           /  \      /  \        <- fast recovery: halve and continue
      |          /    \    /
      |         /      \  /
      |    ____/        \/
      |   /   linear growth (congestion avoidance)
      |  / exponential (slow start)
      +---------------------------------> time
            ^ ssthresh      ^ loss detected
    ```

    - The overall behaviour is called AIMD — Additive Increase, Multiplicative Decrease — and it is what keeps the internet from congestion collapse while sharing capacity roughly fairly between flows.
    - Modern variants: Reno, NewReno, CUBIC (the Linux default, which grows by a cubic function of time) and BBR (which models bandwidth and RTT instead of relying on loss).

13. **What is a TCP Three-way handshaking step?** *[Sonali Bank Ltd. Officer IT 2021 compact it 909 (ET: N/A)]*

    Answer: The TCP three-way handshake has three steps and is used to open a connection before any data is transferred.

    Step 1 — SYN
    - The client sends a segment with the SYN flag set and a randomly chosen initial sequence number, seq = x.
    - It also advertises its receive window size and its MSS.
    - Client state: CLOSED -> SYN-SENT.

    Step 2 — SYN + ACK
    - The server replies with a single segment carrying both flags: SYN = 1 with its own random ISN, seq = y, and ACK = 1 with ack = x + 1.
    - The ack value x + 1 tells the client "I received your SYN, and I now expect byte x + 1".
    - Server state: LISTEN -> SYN-RECEIVED.

    Step 3 — ACK
    - The client acknowledges the server's SYN with seq = x + 1 and ack = y + 1.
    - Both sides move to ESTABLISHED and data transfer begins. This third segment may already carry data.

    ```
    CLIENT                                     SERVER
       |--- SYN, seq=x ------------------------->|
       |<-- SYN+ACK, seq=y, ack=x+1 -------------|
       |--- ACK, seq=x+1, ack=y+1 -------------->|
       |============ ESTABLISHED ===============|
    ```

    Why it takes exactly three steps
    - Both directions must be synchronised, which needs four logical events: client SYN, server ACK, server SYN, client ACK. The server combines its ACK and its SYN into one segment, reducing four to three.

    - Note: a connection is closed with four steps (FIN, ACK, FIN, ACK), because each direction of the full-duplex connection is closed independently.

14. **The primary function of the Transmission Control Protocol (TCP) is to turn an unreliable network into a reliable network that is free from lost and duplicate packets. What are the functions performed by TCP to make a network more reliable?** *[Sonali & Janata Bank Officer (IT) 2020 compact it 990 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

    Answer: TCP makes an unreliable IP network reliable through the following mechanisms.

    1. Sequence numbers
    - Every byte in the stream is numbered. The receiver can therefore place segments in the correct order no matter what order they arrive in, and can detect a gap immediately.

    2. Acknowledgements
    - The receiver returns an ACK carrying the number of the next byte it expects. ACKs are cumulative, so one ACK confirms everything up to that point. Delayed and duplicate ACKs give the sender extra information about what is missing.

    3. Retransmission
    - If an ACK does not arrive before the retransmission timer expires, the segment is sent again. The timer is derived from a smoothed estimate of the round-trip time, so it adapts to network conditions.
    - `Fast retransmit`: three duplicate ACKs are taken as evidence of a single lost segment, and it is resent at once without waiting for the timer.

    4. Checksum
    - A 16-bit checksum covers the header, the data and a pseudo-header containing the IP addresses. A corrupted segment is discarded and, being unacknowledged, is retransmitted. This also detects misdelivered segments.

    5. Duplicate detection
    - Sequence numbers let the receiver recognise and discard a segment it has already accepted, so a spurious retransmission causes no harm.

    6. Flow control — the sliding window
    - The receiver advertises how many bytes of free buffer it has. The sender keeps no more than that amount unacknowledged, so a fast sender never overruns a slow receiver and causes avoidable loss.

    7. Congestion control
    - Slow start, congestion avoidance, fast retransmit and fast recovery adjust the sending rate to the capacity of the network, which prevents the router-buffer overflow that would otherwise cause most losses in the first place.

    8. Connection management
    - The three-way handshake synchronises sequence numbers and confirms both ends are ready; the four-way close ensures no data is lost at teardown; and the TIME-WAIT state ensures old duplicates from a closed connection cannot contaminate a new one.

    9. Ordered delivery to the application
    - Out-of-order segments are buffered rather than delivered, so the application always sees the exact byte stream that was sent, in the right order and with nothing missing.

    - The combined result: the application sees a reliable, ordered, full-duplex byte stream, even though IP underneath offers no guarantee at all.

15. **a) A live video stream will be transmitted. Which Transport layer protocol will you use and why?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033 (ET: BUET)]*

    Answer: For a live video stream, use `UDP` (in practice RTP running over UDP).

    Reasons

    - Latency matters more than perfection. In a live stream, a frame that arrives late is useless — the moment it belongs to has already passed. TCP would stop and wait for a retransmission, delaying everything behind it.
    - No head-of-line blocking. TCP delivers bytes strictly in order, so one lost segment stalls the entire stream until it is recovered. UDP delivers what arrives, and the decoder simply conceals the gap.
    - Loss is tolerable. Video codecs handle a lost packet gracefully: a brief artefact or a repeated block, which the viewer barely notices. A frozen picture for two seconds is far worse.
    - No connection setup. UDP has no handshake, so a viewer joins the stream instantly.
    - Multicast is possible. One server can send a single stream to thousands of viewers using IP multicast, which TCP cannot do at all. For a live broadcast this is decisive.
    - Lower overhead. An 8-byte header instead of 20, and no ACK traffic flowing back, which matters when serving many viewers.
    - Constant rate. TCP's congestion control would repeatedly halve the sending rate, causing visible quality swings; UDP lets the application control its own rate and adapt the bitrate deliberately.

    What is used with it
    - `RTP` over UDP carries the media, adding sequence numbers and timestamps so the receiver can detect loss, reorder and synchronise audio with video.
    - `RTCP` reports quality statistics back so the sender can adapt.
    - WebRTC, used for video calls, is built on this stack.

    When TCP is used instead
    - Video on demand (YouTube, Netflix) uses HTTP over TCP with adaptive bitrate streaming (HLS, DASH), because it is not truly live: a buffer of several seconds hides the retransmissions, and TCP passes through firewalls easily.
    - Some live streaming also uses TCP-based protocols (RTMP, or HLS with low-latency extensions) for exactly that firewall-traversal reason, accepting the extra latency.
    - The rule: `interactive and live` -> UDP/RTP; `buffered playback` -> TCP/HTTP.

16. **(c) What is TCP protocol? How does it work?** *[BPSC Assistant Programmer (CSE) 2019 compact it 1125-1127 (ET: N/A)]*

    Answer:

    What is TCP
    - TCP (Transmission Control Protocol) is the connection-oriented transport-layer protocol of the TCP/IP suite, defined in RFC 793. It provides a reliable, ordered, error-checked, full-duplex byte stream between two application processes.
    - It turns the unreliable, best-effort service of IP into something an application can rely on.
    - Header: 20 bytes minimum, containing source and destination ports, sequence number, acknowledgement number, flags (SYN, ACK, FIN, RST, PSH, URG), window size, checksum and urgent pointer.

    How it works

    - 1. Connection establishment — the three-way handshake
    ```
    CLIENT                                  SERVER
       |--- SYN, seq=x -------------------->|
       |<-- SYN+ACK, seq=y, ack=x+1 --------|
       |--- ACK, seq=x+1, ack=y+1 --------->|
       |=========== ESTABLISHED ============|
    ```
    Both sides agree on initial sequence numbers, window sizes and the MSS.

    - 2. Data transfer
      - The byte stream is divided into segments no larger than the MSS, and every byte is numbered.
      - The receiver acknowledges cumulatively, sending the number of the next byte it expects.
      - Segments arriving out of order are buffered and reordered; duplicates are discarded.

    - 3. Reliability
      - An unacknowledged segment is retransmitted when the adaptive retransmission timer expires.
      - Three duplicate ACKs trigger fast retransmit, without waiting for the timer.
      - A checksum over the header, data and pseudo-header detects corruption.

    - 4. Flow control
      - The receiver advertises a window size in every ACK. The sender keeps no more than that many bytes unacknowledged, so it cannot overwhelm a slow receiver. This is the sliding window.

    - 5. Congestion control
      - Slow start grows the congestion window exponentially, congestion avoidance then grows it linearly, and a loss halves it. The overall behaviour is AIMD, which shares network capacity fairly and prevents congestion collapse.

    - 6. Connection termination — four-way
    ```
       Client --- FIN ---> Server
       Client <-- ACK ---- Server
       Client <-- FIN ---- Server
       Client --- ACK ---> Server   (then TIME-WAIT)
    ```
    Each direction is closed independently, since the connection is full duplex.

    - 7. Multiplexing
      - Port numbers let many applications share one IP address. The four-tuple (source IP, source port, destination IP, destination port) uniquely identifies a connection.

    - Applications that use TCP: HTTP, HTTPS, FTP, SMTP, POP3, IMAP, SSH, Telnet and BGP — everything where losing a byte is unacceptable.

17. **Write down difference between TCP and UDP with write down some TCP and UDP protocols.** *[Dutch Bangla Bank Assistant Network/Hardware Engineer 2019 compact it 1160 (ET: BUET)]*

    Answer:

    Difference between TCP and UDP

    | Point | TCP | UDP |
    |---|---|---|
    | Full form | Transmission Control Protocol | User Datagram Protocol |
    | Connection | Connection-oriented; three-way handshake | Connectionless |
    | Reliability | Reliable; retransmits what is lost | Unreliable; no retransmission |
    | Acknowledgement | Yes, every segment | None |
    | Ordering | Guaranteed by sequence numbers | Not guaranteed |
    | Flow control | Sliding window | None |
    | Congestion control | Slow start, congestion avoidance | None |
    | Error handling | Checksum plus recovery | Checksum only; bad datagrams dropped |
    | Header size | 20 bytes minimum, up to 60 | 8 bytes, fixed |
    | Data unit | Segment | Datagram |
    | Speed | Slower | Faster |
    | Broadcast / multicast | Not supported | Supported |
    | Weight | Heavyweight | Lightweight |

    Protocols that run over TCP

    | Protocol | Port | Purpose |
    |---|---|---|
    | HTTP | 80 | Web pages |
    | HTTPS | 443 | Encrypted web |
    | FTP | 20, 21 | File transfer |
    | SMTP | 25, 587 | Sending email |
    | POP3 | 110 | Downloading email |
    | IMAP | 143 | Synchronised email |
    | SSH | 22 | Encrypted remote login |
    | Telnet | 23 | Plain-text remote login |
    | BGP | 179 | Inter-AS routing |
    | LDAP | 389 | Directory service |

    Protocols that run over UDP

    | Protocol | Port | Purpose |
    |---|---|---|
    | DNS | 53 | Name resolution (TCP for zone transfers) |
    | DHCP | 67, 68 | Automatic IP configuration |
    | TFTP | 69 | Simple file transfer, device booting |
    | SNMP | 161, 162 | Network monitoring |
    | NTP | 123 | Time synchronisation |
    | RIP | 520 | Routing updates |
    | RTP | dynamic | Voice and video streams |
    | QUIC | 443 | The transport under HTTP/3 |

## Communication System & Transmission Modes (17)

1. What is a communication system? Describe the different types of transmission modes with examples. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer:

   What is a communication system
   - A communication system is the set of hardware, software and rules that carries information from a source to a destination over a transmission medium.
   - Five components: message (the data), sender, receiver, transmission medium and protocol.
   ```
   [SOURCE] -> [TRANSMITTER] -> [MEDIUM] -> [RECEIVER] -> [DESTINATION]
                                    ^
                                  noise
   ```
   - Its purpose is to deliver the message accurately, on time, in the right order and without loss.

   Types of transmission mode (by direction of flow)

   1. Simplex — one direction only
   - Data travels only from sender to receiver; the receiver can never reply.
   - The whole channel capacity is used in that one direction.
   - Examples: keyboard to computer, computer to monitor, radio and television broadcast, a loudspeaker announcement, a sensor sending readings.

   2. Half duplex — both directions, one at a time
   - Both devices can send and receive, but not simultaneously; they must take turns.
   - The whole channel capacity is used by whichever side is transmitting.
   - Examples: walkie-talkie, CB radio, a network hub using CSMA/CD, an old shared Ethernet segment.

   3. Full duplex — both directions at once
   - Both devices can send and receive simultaneously, either over two separate paths or by splitting the channel capacity.
   - Examples: telephone call, modern switched Ethernet, mobile phone conversation, video call.

   ```
   SIMPLEX          A -----------> B
   HALF DUPLEX      A <----------> B   (one direction at a time)
   FULL DUPLEX      A ===========> B
                    A <=========== B   (both at once)
   ```

   | Point | Simplex | Half duplex | Full duplex |
   |---|---|---|---|
   | Direction | One way | Two way, alternating | Two way, simultaneous |
   | Performance | Worst | Better | Best |
   | Channel use | Full, one direction | Full, one at a time | Shared or two channels |
   | Example | Radio broadcast | Walkie-talkie | Telephone |

   Also classified by
   - Number of wires: serial transmission (one bit at a time, over one wire — used for long distances) and parallel transmission (many bits at once over many wires — fast but limited to short distances by skew and crosstalk).
   - Synchronisation: asynchronous (start and stop bits per character, no shared clock) and synchronous (a continuous block with a shared clock, much more efficient).

2. **How many types of modes are used in data transferring through networks? Briefly explain those modes. Differentiate between TCP vs UDP.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 338 (ET: BIBM)]*

   Answer:

   (a) Modes of data transfer
   - There are `three` transmission modes, classified by the direction of data flow.

   1. Simplex
   - Data flows in one direction only. The receiver cannot reply.
   - The entire channel capacity is devoted to that one direction.
   - Examples: keyboard to CPU, CPU to monitor, radio and TV broadcast, a sensor reporting readings.

   2. Half duplex
   - Both devices can send and receive, but only one at a time; they take turns on the same channel.
   - Examples: walkie-talkie, hub-based Ethernet using CSMA/CD.

   3. Full duplex
   - Both devices send and receive simultaneously, using two paths or a divided channel.
   - Examples: telephone call, switched Ethernet, mobile call, video conference.

   ```
   SIMPLEX        A ------------> B
   HALF DUPLEX    A <-----------> B   (alternating)
   FULL DUPLEX    A ============> B
                  A <============ B   (simultaneous)
   ```

   (b) TCP vs UDP

   | Point | TCP | UDP |
   |---|---|---|
   | Connection | Connection-oriented, three-way handshake | Connectionless |
   | Reliability | Reliable, retransmits | Unreliable |
   | Ordering | Guaranteed | Not guaranteed |
   | Acknowledgement | Yes | No |
   | Flow / congestion control | Yes | No |
   | Header | 20 bytes minimum | 8 bytes |
   | Speed | Slower | Faster |
   | Broadcast | No | Yes |
   | Data unit | Segment | Datagram |
   | Examples | HTTP, HTTPS, FTP, SMTP, SSH | DNS, DHCP, TFTP, SNMP, VoIP, streaming |

3. **(b) Name and define five components of Data communication system with necessary diagram.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 487 (ET: N/A)]*

   Answer: A data communication system has five components.

   Diagram
   ```
                           PROTOCOL (rules agreed by both ends)
           +--------------------------------------------------+
           |                                                  |
      +---------+                                        +----------+
      | SENDER  |  ---------- MESSAGE ---------------->  | RECEIVER |
      | (source)|      over the TRANSMISSION MEDIUM      | (sink)   |
      +---------+                                        +----------+
           PC, phone,        cable / fibre / radio         PC, printer,
           server                                           server
   ```

   The five components

   1. Message
   - The information (data) to be communicated: text, numbers, pictures, audio, video, or any combination.
   - It is what the whole system exists to deliver.

   2. Sender
   - The device that generates and transmits the message — a computer, phone, camera, sensor or server.
   - It encodes the data into signals suitable for the medium.

   3. Receiver
   - The device that accepts the message — a computer, printer, television or phone.
   - It decodes the signal back into usable data.

   4. Transmission medium
   - The physical path the message travels along.
   - Guided media: twisted pair, coaxial cable, optical fibre.
   - Unguided media: radio waves, microwave, infrared, satellite.

   5. Protocol
   - The set of rules both sides must follow: syntax (format and order of fields), semantics (meaning of each field and the action to take) and timing (when and how fast to send).
   - Without a shared protocol the two devices cannot understand each other even though they are physically connected. Example: TCP/IP.

   Criteria for an effective system
   - Delivery to the correct destination, accuracy (no corruption), timeliness (especially for real-time data) and low jitter.

4. **(a) Differentiate between half-duplex and full duplex transmission.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 489 (ET: N/A)]*

   Answer:

   | Point | Half duplex | Full duplex |
   |---|---|---|
   | Direction | Both ways, but only one at a time | Both ways simultaneously |
   | Channel use | The whole capacity, by whichever side is sending | Capacity divided, or two separate paths |
   | Performance | Lower — the line is idle while turning around | Higher, roughly double the effective throughput |
   | Turnaround delay | Present; devices must switch between send and receive | None |
   | Collisions | Possible on shared media; needs CSMA/CD | Impossible |
   | Cost | Cheaper, simpler hardware | More expensive, needs separate paths or splitting |
   | Efficiency | Lower | Higher |
   | Example | Walkie-talkie, hub-based Ethernet, CB radio | Telephone, switched Ethernet, mobile call |

   Diagram
   ```
   HALF DUPLEX                     FULL DUPLEX
   A -----------> B                A ===========> B
      (then)                       A <=========== B
   A <----------- B                    (at the same time)
   ```

   Practical note
   - Modern Ethernet is full duplex: a switch gives each port a dedicated pair for transmit and another for receive, so collisions disappear entirely and CSMA/CD becomes unnecessary. That is one of the main reasons switches replaced hubs.
   - A duplex mismatch, where one end is set to full and the other to half, produces late collisions and severe performance loss, and is a classic troubleshooting case.

5. **(গ) উদাহরণসহ Simplex, half-duplex এবং duplex কমিউনিকেশন সিস্টেমের পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 628 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   Simplex
   - Communication in one direction only. The receiver has no way to send anything back.
   - The full channel capacity is used in the one direction.
   - Examples: keyboard to computer, computer to monitor, radio broadcast, television broadcast, a public address system.

   Half duplex
   - Communication in both directions, but only one direction at a time. The devices must take turns.
   - The full channel capacity is used by whichever side is transmitting, and there is a turnaround delay when the direction changes.
   - Examples: walkie-talkie, CB radio, hub-based Ethernet with CSMA/CD.

   Full duplex (duplex)
   - Communication in both directions at the same time.
   - Achieved either by two separate physical paths, or by dividing the channel capacity between the two directions.
   - Examples: telephone call, mobile phone conversation, switched Ethernet, video conference.

   ```
   SIMPLEX       A ------------> B      one way only
   HALF DUPLEX   A <-----------> B      one direction at a time
   FULL DUPLEX   A ============> B      both directions
                 A <============ B      simultaneously
   ```

   | Point | Simplex | Half duplex | Full duplex |
   |---|---|---|---|
   | Direction | One way | Two way, alternating | Two way, simultaneous |
   | Channel capacity | Full, one direction | Full, one at a time | Split or doubled |
   | Performance | Lowest | Medium | Highest |
   | Cost | Lowest | Medium | Highest |
   | Turnaround delay | Not applicable | Present | None |
   | Example | Radio broadcast | Walkie-talkie | Telephone |

6. **What is the difference between Synchronous and Asynchronous transmission?** *[CAAB Assistant Maintenance Engineer (AME) 2022 compact it 723 (ET: N/A)], [RAKUB Assistant Network System Engineer 03.11.2023 compact it 550 (ET: BIBM)]*

   Answer:

   | Point | Asynchronous transmission | Synchronous transmission |
   |---|---|---|
   | Unit sent | One character (byte) at a time | A continuous block of many characters |
   | Synchronisation | Start bit and stop bit around every character | A shared clock, or timing recovered from the data stream |
   | Gaps | Idle gaps of any length between characters | No gaps; the block flows continuously |
   | Overhead | High — typically 2–3 extra bits per 8 data bits, about 20–30 percent | Low — a few sync bytes per block of hundreds or thousands |
   | Speed | Slower | Faster |
   | Cost | Cheaper hardware | More expensive, needs precise timing |
   | Timing accuracy needed | Low; resynchronised at each character | High; the clock must stay locked for the whole block |
   | Error effect | An error affects one character | A timing slip can corrupt the whole block |
   | Buffering | Not needed | Needed at both ends |
   | Suitable for | Low-speed, bursty data — keyboard, serial terminals, RS-232 | High-speed, continuous data — Ethernet, SONET, USB, disk transfers |

   Diagrams
   ```
   ASYNCHRONOUS
     ...idle...  [S|d d d d d d d d|P|E]  ...idle...  [S|d d d d d d d d|P|E]
                 start   8 data bits  parity stop

   SYNCHRONOUS
     [SYN|SYN|  data data data data data data data data data  |CRC]
           one long frame, no per-character overhead
   ```

   Summary
   - Asynchronous synchronises the receiver at the start of every single character, which is simple and forgiving but wasteful.
   - Synchronous synchronises once per block and then relies on a locked clock, which is far more efficient but demands accurate timing and buffering.

7. **Briefly mention the main रणनीति impairments in telecommunication channel. Considering these impairments explain which communication is better between analog and digital communication systems?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*

   Answer:

   Main transmission impairments in a telecommunication channel

   1. Attenuation
   - The signal loses strength as it travels, because energy is absorbed by the medium. Measured in decibels.
   - It is frequency dependent, so different components of a signal weaken by different amounts, distorting the shape.
   - Remedy: amplifiers for analogue signals, repeaters for digital, and equalisers to flatten the frequency response.

   2. Distortion
   - The signal changes shape. Different frequency components travel at different speeds (delay distortion), so they arrive at different times, which spreads pulses into each other — intersymbol interference.
   - Remedy: equalisation, and limiting the data rate for a given bandwidth.

   3. Noise
   - Unwanted energy added to the signal. Types:
     - Thermal noise — random motion of electrons, present in every conductor, cannot be eliminated.
     - Intermodulation noise — different frequencies mixing to produce new ones.
     - Crosstalk — a signal from an adjacent pair leaking in.
     - Impulse noise — sudden spikes from lightning or switching, the main cause of digital errors.
   - Measured as the signal-to-noise ratio (SNR).

   4. Other impairments
   - Jitter — variation in the timing of pulses. Fading — signal strength varying over time, particularly on radio. Echo — reflections from impedance mismatches. Bandwidth limitation — the channel cannot pass all frequencies.

   Which is better in the face of these impairments — `digital communication`

   - Regeneration versus amplification. A digital repeater reads the bits, decides 0 or 1, and generates a completely clean new signal. Noise picked up on the previous span is discarded entirely. An analogue amplifier cannot tell signal from noise, so it amplifies both, and noise accumulates over every hop. This single point is the decisive one for long distances.
   - Error detection and correction. Digital data carries parity, checksums, CRC and forward error correction, so errors can be detected and often repaired. Analogue has no equivalent.
   - Noise immunity. A digital receiver only has to decide which side of a threshold the sample falls on, so small amounts of noise cause no error at all. In analogue, any noise is a permanent change to the information.
   - Encryption and security. Digital data can be encrypted with strong algorithms; analogue scrambling is weak.
   - Multiplexing. TDM allows many digital channels to share one link efficiently, and statistical multiplexing gains more still.
   - Integration. Voice, video and data become the same thing — bits — so one network carries all services.
   - Processing and storage. Digital signals can be compressed, filtered, buffered and stored perfectly; analogue copies always degrade.
   - Cost. Digital circuitry is made from cheap, dense integrated circuits.

   Where analogue still has an advantage
   - It needs less bandwidth for the same raw signal, since digitising adds overhead, and it needs no analogue-to-digital conversion. The physical world is analogue, so sensors and speakers remain analogue at the edges.

   - Conclusion: because impairments accumulate irreversibly in analogue systems but are removed at every regeneration in digital ones, digital communication is clearly superior, and it is why the entire telecommunications network has converted to digital.

8. **Describe the data communication system with necessary diagram.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 679 (ET: N/A)]*

   Answer:

   Definition
   - A data communication system is the collection of hardware, software and rules that transfers data from one device to another over a transmission medium.

   Diagram
   ```
                             PROTOCOL
           +-----------------------------------------------+
           |                                               |
      +---------+     +--------+                 +--------+     +----------+
      | SENDER  |---->|ENCODER |=== MEDIUM ====>| DECODER|---->| RECEIVER |
      | (source)|     |modulator|      ^        |demod.  |     |(destination)|
      +---------+     +--------+       |        +--------+     +----------+
                                     NOISE
      MESSAGE: text, number, image, audio, video
   ```

   The five components
   - Message — the information being sent: text, numbers, images, audio or video.
   - Sender — the device that creates and transmits it: computer, phone, camera, sensor.
   - Receiver — the device that accepts it: computer, printer, television.
   - Transmission medium — the physical path: twisted pair, coaxial cable or fibre (guided); radio, microwave, infrared or satellite (unguided).
   - Protocol — the agreed rules of communication, covering syntax, semantics and timing. Without it the two devices cannot understand each other.

   Direction modes
   - Simplex (one way), half duplex (both ways alternately) and full duplex (both ways simultaneously).

   Criteria for effectiveness
   - Delivery — to the correct destination and to no one else.
   - Accuracy — the data must arrive uncorrupted.
   - Timeliness — real-time data delivered late is useless.
   - Jitter — the variation in arrival time must be small, especially for audio and video.

   Types of signal
   - Analogue — continuous, like a voice waveform. Digital — discrete levels representing 0 and 1. Modern systems are digital because noise can be removed completely at each regeneration.

9. **Write down the Data Communication elements.** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*

   Answer: The elements (components) of a data communication system are five.

   1. Message
   - The information to be communicated: text, numbers, images, audio, video or any combination.

   2. Sender (source)
   - The device that generates and transmits the message — computer, phone, camera, sensor, server.

   3. Receiver (destination)
   - The device that receives the message — computer, printer, phone, television.

   4. Transmission medium
   - The physical path the signal travels along.
   - Guided: twisted pair, coaxial cable, optical fibre.
   - Unguided: radio waves, microwave, infrared, satellite.

   5. Protocol
   - The agreed rules that govern the exchange: syntax (format and field order), semantics (meaning and required action) and timing (when to send and how fast).
   - Two devices physically connected but using different protocols still cannot communicate.

   ```
   [SENDER] ---- message ----> [MEDIUM] ---- message ----> [RECEIVER]
                    governed throughout by the PROTOCOL
   ```

   - Some textbooks add the encoder/decoder (modem) and the noise source as separate elements of the general communication model.

10. **(ক) Data Communication System এর পাঁচটি প্রধান Component এর চিত্রসহকারে বর্ণনা দিন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 704 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.)

    Diagram
    ```
                              PROTOCOL
            +-----------------------------------------------+
            |                                               |
       +---------+                                    +----------+
       | SENDER  | ------- MESSAGE over MEDIUM -----> | RECEIVER |
       +---------+                                    +----------+
        computer,        twisted pair / fibre /        computer,
        phone, sensor    radio / satellite             printer, TV
    ```

    The five main components

    1. Message
    - The data being communicated — text, numbers, images, audio, video, or a combination of these. It is the reason the system exists.

    2. Sender
    - The device that creates the message and puts it onto the medium. It encodes the data into a signal the medium can carry.
    - Examples: computer, mobile phone, video camera, workstation, sensor.

    3. Receiver
    - The device that takes the signal from the medium and decodes it back into the original data.
    - Examples: computer, printer, television, mobile phone.

    4. Transmission medium
    - The physical path between sender and receiver.
    - Guided (wired): twisted-pair cable, coaxial cable, optical fibre.
    - Unguided (wireless): radio waves, microwave, infrared, satellite links.
    - The choice determines bandwidth, distance, cost and noise immunity.

    5. Protocol
    - The set of rules both parties must follow. It defines syntax (the format and order of the fields), semantics (what each field means and what action to take) and timing (when to send, and at what rate).
    - Example: TCP/IP. Two devices connected by a perfect cable still cannot communicate without a common protocol.

11. **(খ) Data Communication কত প্রকার? উদাহরণসহ সংক্ষিপ্ত বর্ণনা দিন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 704 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Data communication is classified in several ways.

    (a) By direction of flow — three types

    1. Simplex — one direction only, no reply possible.
    - Example: keyboard to computer, radio and television broadcast, a monitor display.

    2. Half duplex — both directions, but one at a time.
    - Example: walkie-talkie, CB radio, hub-based Ethernet.

    3. Full duplex — both directions at the same time.
    - Example: telephone call, switched Ethernet, video conference.

    (b) By number of wires — two types

    1. Serial transmission — bits are sent one after another over a single line.
    - Cheaper, reliable over long distances, no skew between wires. Used by USB, Ethernet, RS-232 and almost all networking.
    - Sub-types: asynchronous (start and stop bits per character) and synchronous (continuous blocks with a shared clock).

    2. Parallel transmission — several bits sent simultaneously over several lines.
    - Faster over very short distances, but suffers from skew and crosstalk as length increases, and needs many wires.
    - Example: the old printer port, internal computer buses.

    (c) By signal type — two types
    1. Analogue — a continuously varying signal, as in traditional telephone or AM/FM radio.
    2. Digital — discrete levels representing 0 and 1, as in computer networks. Digital dominates because noise can be removed at every regeneration.

    (d) By number of receivers
    - Unicast (one to one), broadcast (one to all), multicast (one to a group) and anycast (one to the nearest of a group).

    ```
    SIMPLEX      A -----> B
    HALF DUPLEX  A <----> B  (alternating)
    FULL DUPLEX  A <====> B  (simultaneous)

    SERIAL    ---- 1 0 1 1 0 0 1 0 ---->   one wire
    PARALLEL  ==== 1 0 1 1 0 0 1 0 ====>   eight wires at once
    ```

12. **Define full duplex with an example.** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

    Answer: Full duplex is a transmission mode in which both devices can send and receive data `at the same time`.

    How it is achieved
    - Two separate physical paths, one for each direction — for example the separate transmit and receive pairs in an Ethernet cable.
    - Or by splitting the channel capacity into two, so each direction gets half.

    Example — a telephone call
    - Both people can speak and hear simultaneously. Neither has to wait for the other to finish, unlike a walkie-talkie where only one can speak at a time.

    Other examples
    - Switched Ethernet — a PC transmits on one pair while receiving on another, which is why collisions disappear on a switched full-duplex link and CSMA/CD becomes unnecessary.
    - Mobile phone conversation, video conferencing, and instant messaging where both sides can type at once.

    ```
    FULL DUPLEX
       A ===============> B      both directions
       A <=============== B      at the same instant
    ```

    Advantages
    - Roughly double the effective throughput of half duplex, no turnaround delay, and no collisions.

    Disadvantages
    - More expensive: it needs two paths or more complex circuitry.

    - Note: a duplex mismatch, where one end is configured full duplex and the other half duplex, causes late collisions and severe performance degradation. It is a classic network fault.

13. **Which communication mode use serial communication? (a) Duplex (b) Half Duplex (c) Simplex (d) All** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

    Answer: The correct option is `(d) All`.

    - Serial communication means sending bits one after another over a single line. It says nothing about the direction of flow, so it can operate in any of the three modes.

    | Mode | Serial example |
    |---|---|
    | Simplex | A sensor sending readings over a one-way serial line; a serial printer feed |
    | Half duplex | RS-485 two-wire, where devices take turns on the same pair; a walkie-talkie data link |
    | Full duplex | RS-232 with separate TX and RX lines; USB; Ethernet |

    Why the confusion arises
    - Serial versus parallel is a question of `how many wires` carry the bits.
    - Simplex, half duplex and full duplex is a question of `which direction` data can flow.
    - These are independent classifications, so all combinations exist.

    - Note: modern high-speed links are almost all serial (USB, SATA, PCIe, Ethernet), because parallel buses suffer from skew and crosstalk as speed and distance increase.

14. **(c) Illustrate a communication model in simplified form.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1027-1028 (ET: N/A)]*

    Answer: A simplified communication model has five functional blocks.

    ```
    +---------+   +-------------+   +--------------+   +----------+   +-------------+
    | SOURCE  |-->| TRANSMITTER |-->| TRANSMISSION |-->| RECEIVER |-->| DESTINATION |
    |         |   |  (encoder,  |   |    SYSTEM    |   | (decoder,|   |             |
    |         |   |  modulator) |   |   (medium)   |   |  demod.) |   |             |
    +---------+   +-------------+   +------^-------+   +----------+   +-------------+
                                           |
                                        NOISE
       text/voice     signal          transmitted        received        text/voice
       data           g(t)            signal s(t)        signal r(t)     data
    ```

    The blocks
    - Source — generates the data to be transmitted: a computer, telephone or sensor.
    - Transmitter — converts that data into a signal suitable for the medium. This is encoding and modulation; a modem is the classic example.
    - Transmission system — the medium itself, from a single cable to a complex network of links and switches. This is where attenuation, distortion and noise act on the signal.
    - Receiver — converts the received signal back into data, by demodulation and decoding, correcting errors where it can.
    - Destination — the device that takes the delivered data and uses it.

    Key tasks the model must handle
    - Interfacing to the medium, signal generation, synchronisation between sender and receiver, error detection and correction, flow control, addressing and routing, recovery from failure, message formatting, security and network management.

    - Noise is shown deliberately as acting on the transmission system, because that is what makes error control necessary. Everything else in data communications exists to deliver the message correctly despite it.

15. **(a) Draw a general model of communication system. Discuss different modes of communications.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1141-1142 (ET: N/A)]*

    Answer:

    General model of a communication system
    ```
    +---------+   +-------------+   +--------------+   +----------+   +-------------+
    | SOURCE  |-->| TRANSMITTER |-->| TRANSMISSION |-->| RECEIVER |-->| DESTINATION |
    |         |   | encoder /   |   |    SYSTEM    |   | decoder /|   |             |
    |         |   | modulator   |   |   (medium)   |   | demod.   |   |             |
    +---------+   +-------------+   +------^-------+   +----------+   +-------------+
                                           |
                                      NOISE SOURCE
    ```
    - Source produces the data; the transmitter converts it into a signal the medium can carry; the transmission system carries it (and adds impairments); the receiver converts it back; the destination consumes it.
    - Attenuation, distortion and noise all act on the transmission system, which is why error control exists.

    Modes of communication

    By direction of flow
    - `Simplex` — one direction only. The receiver cannot reply. Example: radio broadcast, keyboard to computer.
    - `Half duplex` — both directions, but one at a time, taking turns. Example: walkie-talkie, hub-based Ethernet.
    - `Full duplex` — both directions simultaneously. Example: telephone call, switched Ethernet.

    By number of wires
    - `Serial` — one bit at a time on one line. Cheap and reliable over distance; used by USB, Ethernet, RS-232.
    - `Parallel` — several bits at once on several lines. Fast over very short distances, but limited by skew and crosstalk.

    By synchronisation
    - `Asynchronous` — each character framed by start and stop bits; simple, but 20–30 percent overhead.
    - `Synchronous` — continuous blocks with a shared clock; far more efficient, but needs accurate timing and buffering.

    By number of receivers
    - `Unicast` (one to one), `broadcast` (one to all), `multicast` (one to a selected group) and `anycast` (one to the nearest member of a group).

    ```
    SIMPLEX      A ------> B
    HALF DUPLEX  A <-----> B   (alternating)
    FULL DUPLEX  A <=====> B   (simultaneous)
    ```

16. **Write down the problem of asynchronous data transmission? How to solve this Problem using synchronous data transmission?** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1152 (ET: KUET)]*

    Answer:

    Problems with asynchronous data transmission

    - High overhead. Every single character is framed with a start bit and one or two stop bits, and often a parity bit. For 8 data bits that is 2–3 extra bits, an overhead of 20–30 percent. A quarter of the link's capacity is spent on framing rather than data.
    - Low speed. Because of that overhead, and because the receiver must resynchronise at the start of every character, asynchronous transmission cannot reach high data rates. It is practical only up to a few hundred kbps.
    - Idle gaps waste the channel. The line sits idle between characters, so the medium is poorly used.
    - Weak error detection. A single parity bit detects an odd number of bit errors only; it cannot detect two errors in one character and cannot correct anything.
    - Per-character timing risk. If the receiver's clock drifts even slightly within one character, the later bits are sampled at the wrong instants and the character is corrupted.
    - Not suitable for bulk transfer. Sending a large file character by character with this overhead is very inefficient.

    How synchronous transmission solves them

    - Blocks instead of characters. Data is sent as a continuous frame of hundreds or thousands of bits with no start or stop bits around each character, so the per-character overhead disappears entirely.
    - Very low overhead. A few SYN characters or a preamble at the start of the block, plus a CRC at the end, serve an entire frame. Overhead falls from 25 percent to a fraction of one percent.
    - Shared or recovered clock. Either a separate clock line, or self-clocking line coding such as Manchester or 8B/10B, keeps the receiver locked to the sender for the whole block. There is no need to resynchronise per character.
    - Much higher speed. With no gaps and almost no overhead, synchronous links run from megabits to hundreds of gigabits per second — this is what Ethernet, SONET and USB use.
    - Strong error detection. A CRC over the whole block detects burst errors far more reliably than parity, and forward error correction can repair some of them.
    - Efficient channel use. The line is kept busy continuously, and idle patterns keep the clock locked even when there is no data.

    | Problem in asynchronous | Solution in synchronous |
    |---|---|
    | 20–30 percent framing overhead | One header and one CRC per large block |
    | Resynchronisation per character | Continuous clock, locked for the whole block |
    | Idle gaps waste the medium | Continuous stream with idle fill patterns |
    | Weak parity checking | CRC over the entire block |
    | Low speed | Very high speed |

    - The cost of synchronous transmission is more complex hardware, buffering at both ends and accurate timing — which is why asynchronous survives for slow, bursty, cheap links such as a serial console.

17. **What is data communication? Define Simplex, half duplex and full duplex.** *[ICT Ministry Assistant Programmer 2017 compact it 1239 (ET: N/A)]*

    Answer:

    What is data communication
    - Data communication is the exchange of data between two devices through a transmission medium, governed by a protocol.
    - Its five components are: message, sender, receiver, transmission medium and protocol.
    - Four criteria decide whether it is effective: delivery to the correct destination, accuracy (no corruption), timeliness (real-time data must not arrive late) and low jitter.

    Simplex
    - Data travels in one direction only; the receiver can never send anything back.
    - The entire channel capacity is used for that one direction.
    - Examples: keyboard to computer, computer to monitor, radio and television broadcast.

    Half duplex
    - Data travels in both directions, but only one direction at a time. The devices take turns on the same channel, with a turnaround delay when the direction changes.
    - The full capacity is available to whichever side is transmitting.
    - Examples: walkie-talkie, CB radio, hub-based Ethernet with CSMA/CD.

    Full duplex
    - Data travels in both directions simultaneously, using two separate paths or a divided channel.
    - Highest performance and no turnaround delay, but the most expensive.
    - Examples: telephone call, mobile conversation, switched Ethernet, video conference.

    ```
    SIMPLEX       A ------------> B
    HALF DUPLEX   A <-----------> B   (one at a time)
    FULL DUPLEX   A ============> B
                  A <============ B   (both at once)
    ```

    | Point | Simplex | Half duplex | Full duplex |
    |---|---|---|---|
    | Direction | One way | Two way, alternating | Two way, simultaneous |
    | Performance | Lowest | Medium | Highest |
    | Cost | Lowest | Medium | Highest |
    | Example | TV broadcast | Walkie-talkie | Telephone |

## Data Rate & Channel Capacity (Nyquist, Shannon) (16)

1. **Nyquist math: See in Data Communication & Networking Chapter** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 499 (ET: N/A)]*

   Answer: The question points at the standard Nyquist material, so the theorem and the worked forms used in exams are given.

   Two Nyquist results — do not confuse them

   1. Nyquist bit rate (maximum data rate of a NOISELESS channel)
   ```
   C = 2 × B × log2(L)
   ```
   - C = capacity in bps, B = bandwidth in Hz, L = number of signal (voltage) levels.
   - Increasing L increases the bit rate, but the receiver must distinguish more levels, so noise sets a practical limit.

   2. Nyquist sampling theorem (for digitising an analogue signal)
   ```
   Sampling rate >= 2 × f_max
   ```
   - Sampling below this rate causes aliasing, which cannot be undone afterwards.
   - Nyquist interval = 1 ÷ (2 f_max).

   Shannon capacity (for a NOISY channel), always used alongside
   ```
   C = B × log2(1 + SNR)      where SNR = signal power / noise power
   SNR(dB) = 10 log10(SNR)    and   SNR = 10^(SNR_dB / 10)
   ```

   Worked examples

   - Noiseless, B = 3 kHz, 2 levels: C = 2 × 3000 × log2(2) = `6000 bps`.
   - Noiseless, B = 3 kHz, 4 levels: C = 2 × 3000 × log2(4) = `12,000 bps`.
   - Noisy telephone line, B = 3000 Hz, SNR = 3162: C = 3000 × log2(3163) ≈ `34,860 bps`.
   - Digitising voice limited to 4 kHz: sampling rate >= 8000 samples/s; with 8-bit PCM this gives 64 kbps, the DS-0 rate.

   How to use them together
   - Compute both. Shannon gives the theoretical ceiling set by noise; Nyquist tells you how many levels are needed to reach a chosen rate. The lower of the two is the practical limit, and the number of levels is then rounded to a power of 2.

2. **Suppose that a digitized TV picture is to be transmitted from a source that uses a matrix of 480 × 500 picture elements (pixels), where each pixel can take on one of 32 intensity values. Assume that 30 pictures are sent per second. (This digital source is roughly equivalent to broadcast TV standards that have been adopted). Find the source rate R (bps).** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 (ET: BIBM)]*

   Answer:

   Given
   - Picture matrix = 480 × 500 pixels
   - Each pixel has one of 32 intensity values
   - 30 pictures per second

   Step 1 — pixels per picture
   ```
   480 × 500 = 240,000 pixels
   ```

   Step 2 — bits per pixel
   - 32 possible values need log2(32) bits.
   ```
   log2(32) = 5 bits per pixel
   ```

   Step 3 — bits per picture
   ```
   240,000 × 5 = 1,200,000 bits per picture
   ```

   Step 4 — source rate
   ```
   R = 1,200,000 × 30 = 36,000,000 bps = 36 Mbps
   ```

   - Answer: `R = 36 Mbps`.
   - The general formula is R = (rows × columns) × log2(levels) × frames per second.
   - This is why raw video must be compressed: 36 Mbps is far more than a broadcast channel can carry, so MPEG and H.264/H.265 reduce it by an order of magnitude or more.

3. **One of the drawbacks of a small packet size is that a large function of link bandwidth is consumed by overhead bytes. To this end, supposed that the packet consists of P bytes and 5 bytes of header. Consider sending a digitally encoded voice source directly. Suppose the source is encoded a constant rate of 128 kbps. Assume each packet is entirely filled before the source sends the packet into the network. The time required to fill a packet is the packetization delay. Determine the packetization delay for length L-1500 bytes (roughly corresponding to maximum-sized Ethernet packet).** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 (ET: BIBM)]*

   Answer: Packetization delay is the time taken to fill one packet with data at the source's encoding rate.

   Given
   - Source encoding rate = 128 kbps = 128,000 bits per second
   - Packet payload L = 1500 bytes
   - Header = 5 bytes (this does not affect the filling time, only the overhead)

   Step 1 — convert the payload to bits
   ```
   1500 bytes × 8 = 12,000 bits
   ```

   Step 2 — time to fill the packet
   ```
   Packetization delay = payload bits / source rate
                       = 12,000 / 128,000
                       = 0.09375 s
                       = 93.75 milliseconds
   ```

   - Answer: `93.75 ms`.

   Overhead for comparison
   ```
   Overhead fraction = 5 / (1500 + 5) = 0.332 %
   ```

   The trade-off the question is illustrating

   | Payload L | Packetization delay | Header overhead |
   |---|---|---|
   | 50 bytes | 3.125 ms | 9.09 % |
   | 200 bytes | 12.5 ms | 2.44 % |
   | 1500 bytes | 93.75 ms | 0.33 % |

   - A large packet is very efficient in bandwidth but adds a long delay before transmission even begins.
   - For voice this matters enormously: total one-way delay should stay under about 150 ms for a natural conversation, and 93.75 ms of packetization alone would leave almost no budget for propagation, queuing and jitter buffering.
   - That is exactly why VoIP uses small packets — typically 20 ms of audio, about 160 bytes at 64 kbps — accepting the higher header overhead in exchange for low delay.
   - If the 1500 bytes is taken to include the 5-byte header, the payload is 1495 bytes and the delay is 93.4375 ms; the conclusion is unchanged.

4. **(ক) Bandwidth এবং Through put এর মধ্যে পার্থক্য কী?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 628 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   | Point | Bandwidth | Throughput |
   |---|---|---|
   | Meaning | The maximum capacity of the link — theoretical | The data rate actually achieved — practical |
   | Nature | A fixed property of the link | Varies moment to moment |
   | Value | Always the higher figure | Always lower than bandwidth |
   | Measured in | bps, Mbps, Gbps (or Hz for analogue) | bps, Mbps, Gbps |
   | Determined by | Medium, hardware and technology | Congestion, errors, protocol overhead, distance, device performance |
   | Example | A 100 Mbps Ethernet port | 85 Mbps measured by a file copy on that port |
   | Can it be changed | Only by upgrading the link | Improves by reducing congestion, errors and overhead |

   Why throughput is always lower
   - Protocol overhead — Ethernet, IP and TCP headers consume part of every frame.
   - Congestion and queuing when several users share the link.
   - Retransmissions caused by errors or loss.
   - The slowest link on the path (the bottleneck) caps the whole route.
   - Processing limits in the end devices themselves.
   - Half-duplex operation, collisions and, on wireless, interference and airtime sharing.

   Related term
   - `Goodput` is narrower still: it counts only the useful application data delivered, excluding headers and retransmissions.

   - Analogy: bandwidth is the number of lanes on a road; throughput is how many cars actually get through in an hour, given traffic lights, congestion and accidents.

5. **The power of signal is 10\text{mW} and the power of the noise is 1\mu\text{W}; What are the values of \text{SNR} and \text{SNR}_{\text{dB}}?** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 651 (ET: BUET)]*

   Answer:

   Given
   - Signal power = 10 mW = 10 × 10^-3 W = 0.01 W
   - Noise power = 1 µW = 1 × 10^-6 W

   Step 1 — SNR (a ratio, so it has no unit)
   ```
   SNR = signal power / noise power
       = (10 × 10^-3) / (1 × 10^-6)
       = 10 × 10^3
       = 10,000
   ```

   Step 2 — SNR in decibels
   ```
   SNR(dB) = 10 × log10(SNR)
           = 10 × log10(10,000)
           = 10 × 4
           = 40 dB
   ```

   | Quantity | Value |
   |---|---|
   | SNR | `10,000` |
   | SNR(dB) | `40 dB` |

   - Both powers must be in the same unit before dividing; that is the usual source of error.
   - Useful check: every factor of 10 in the power ratio adds 10 dB, so 10,000 = 10^4 gives exactly 40 dB.
   - A higher SNR means a cleaner channel and, by Shannon's formula C = B log2(1 + SNR), a higher possible data rate.

6. **We need to send 265\text{ kbps} over a noiseless channel with a bandwidth of 20\text{kHz}. How many signal levels do we need?** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 652 (ET: BUET)]*

   Answer: The channel is noiseless, so Nyquist's formula applies.

   Given
   - Bit rate C = 265 kbps = 265,000 bps
   - Bandwidth B = 20 kHz = 20,000 Hz

   Nyquist formula
   ```
   C = 2 × B × log2(L)
   ```

   Step 1 — solve for log2(L)
   ```
   265,000 = 2 × 20,000 × log2(L)
   265,000 = 40,000 × log2(L)
   log2(L) = 265,000 / 40,000 = 6.625
   ```

   Step 2 — solve for L
   ```
   L = 2^6.625 = 98.7
   ```

   Step 3 — interpret the result
   - `L = 98.7`, but the number of signal levels must be a whole number, and in practice a power of 2 so that each level carries a whole number of bits.
   - Rounding down to 64 levels gives 2 × 20,000 × 6 = 240 kbps, which is `not enough`.
   - Rounding up to `128 levels` gives 2 × 20,000 × 7 = `280 kbps`, which covers the requirement.

   Answer
   - Use `L = 128 signal levels` (7 bits per symbol), giving a capacity of 280 kbps against the 265 kbps required.
   - Alternatively, keep fewer levels and increase the bandwidth, or reduce the required bit rate to 240 kbps.
   - Practical caution: 128 levels means the receiver must distinguish 128 distinct voltages. No real channel is truly noiseless, so Shannon's limit would have to be checked as well — in practice such a high level count demands a very high SNR.

7. **A telephone line normally has a bandwidth of 3000\text{ Hz} (300\text{ to } 3300\text{ Hz}) assigned foe data communications. The signal-to-noise ratio is usually 3162. Calculate the capacity for this channel?** *[RPGCL Assistant Manager (ICT) 2022 compact it 656 (ET: BUET)]*

   Answer: The channel is noisy, so Shannon's formula applies.

   Given
   - Bandwidth B = 3000 Hz (3300 − 300)
   - SNR = 3162

   Shannon capacity formula
   ```
   C = B × log2(1 + SNR)
   ```

   Step 1 — substitute
   ```
   C = 3000 × log2(1 + 3162)
     = 3000 × log2(3163)
   ```

   Step 2 — evaluate the logarithm
   ```
   log2(3163) = ln(3163) / ln(2) = 8.0593 / 0.6931 = 11.627
   ```

   Step 3 — capacity
   ```
   C = 3000 × 11.627 = 34,881 bps ≈ 34.88 kbps
   ```

   - Answer: about `34,860 bps` (commonly quoted as ~34.86 kbps; the small difference comes from rounding the logarithm).

   Interpretation
   - This is the theoretical maximum for an ordinary telephone line, and it explains why dial-up modems stopped at 33.6 kbps for symmetric use.
   - SNR = 3162 corresponds to 10 log10(3162) ≈ 35 dB, a typical value for a good telephone circuit.
   - Shannon gives only the ceiling. It says nothing about how many signal levels to use — that comes from Nyquist. To reach 34.88 kbps over 3000 Hz, Nyquist requires 2 × 3000 × log2(L) = 34,881, so log2(L) ≈ 5.8, meaning about 64 levels.

8. **Consider that a signal is transmitted over a channel of bandwidth 200kHz and the total path loss in the channel is found to be 60dB. The noise power per hertz at the receiver is- 100 dBm. Determine the required transmit power to achieve data rate of 40kb/s.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

   Answer: Use Shannon's formula to find the required SNR, then work back through the noise power and the path loss.

   Given
   - Bandwidth B = 200 kHz = 200,000 Hz
   - Path loss = 60 dB
   - Noise power spectral density N0 = −100 dBm/Hz
   - Required data rate C = 40 kbps = 40,000 bps

   Step 1 — required SNR from Shannon
   ```
   C = B log2(1 + SNR)
   40,000 = 200,000 × log2(1 + SNR)
   log2(1 + SNR) = 0.2
   1 + SNR = 2^0.2 = 1.1487
   SNR = 0.1487
   ```

   Step 2 — SNR in dB
   ```
   SNR(dB) = 10 log10(0.1487) = −8.28 dB
   ```

   Step 3 — total noise power at the receiver
   ```
   N = N0 + 10 log10(B)
     = −100 + 10 log10(200,000)
     = −100 + 53.01
     = −46.99 dBm
   ```

   Step 4 — required received signal power
   ```
   S = N + SNR(dB)
     = −46.99 + (−8.28)
     = −55.27 dBm
   ```

   Step 5 — required transmit power
   ```
   Pt = S + path loss
      = −55.27 + 60
      = 4.73 dBm
   ```

   Step 6 — convert to watts
   ```
   Pt = 10^(4.73/10) mW = 2.97 mW ≈ 3 mW
   ```

   | Quantity | Value |
   |---|---|
   | Required SNR | 0.1487 (−8.28 dB) |
   | Noise power | −46.99 dBm |
   | Required received power | −55.27 dBm |
   | Required transmit power | `4.73 dBm ≈ 2.97 mW` |

   - Note the SNR is below 1, which is perfectly valid: Shannon shows that data can be sent reliably even when the signal is weaker than the noise, provided the bandwidth is generous relative to the data rate. Here 200 kHz carries only 40 kbps, so the system is heavily bandwidth-rich.
   - Working in dBm throughout is what makes the arithmetic simple: multiplication and division become addition and subtraction.

9. **(গ) নিম্নে উল্লিখিত ডাটা ট্রান্সফার রেট গুলিকে bit/sec এর পরিণত করুন 50Mb/S; 10KB/S; 20MB/S; 10Kb/S.** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 704 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Convert each to bits per second. Note the capital B means bytes, the small b means bits, so a factor of 8 is involved.

   (i) 50 Mb/s
   ```
   50 Mb/s = 50 × 10^6 bits/s = 50,000,000 bps
   ```

   (ii) 10 KB/s
   ```
   10 KB/s = 10 × 1000 bytes/s = 10,000 bytes/s
           = 10,000 × 8 = 80,000 bps
   ```

   (iii) 20 MB/s
   ```
   20 MB/s = 20 × 10^6 bytes/s
           = 20,000,000 × 8 = 160,000,000 bps = 160 Mbps
   ```

   (iv) 10 Kb/s
   ```
   10 Kb/s = 10 × 1000 = 10,000 bps
   ```

   Summary

   | Given | In bits per second |
   |---|---|
   | 50 Mb/s | 50,000,000 bps |
   | 10 KB/s | 80,000 bps |
   | 20 MB/s | 160,000,000 bps |
   | 10 Kb/s | 10,000 bps |

   - The two rules to remember: 1 byte = 8 bits, and in data-rate units the prefixes are decimal (k = 1000, M = 10^6). Binary prefixes (KiB = 1024) are used for memory and file sizes, not for link speeds. If 1 KB were taken as 1024 bytes, 10 KB/s would be 81,920 bps.
   - This is why a "20 MB/s" download needs a 160 Mbps link, and a 100 Mbps connection delivers at most about 12.5 MB/s.

10. **What is the channel capacity for a teleprinter channel with a 300 Hz bandwidth and a signal-to-noise ratio of 3 dB?** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 719 (ET: N/A)]*

    Answer: The channel is noisy, so Shannon's formula applies. The SNR is given in decibels, so it must be converted to a plain ratio first.

    Given
    - Bandwidth B = 300 Hz
    - SNR = 3 dB

    Step 1 — convert SNR from dB to a ratio
    ```
    SNR = 10^(SNR_dB / 10)
        = 10^(3/10)
        = 10^0.3
        = 1.995 ≈ 2
    ```
    - The useful shortcut: 3 dB means approximately a factor of 2.

    Step 2 — apply Shannon's formula
    ```
    C = B × log2(1 + SNR)
      = 300 × log2(1 + 2)
      = 300 × log2(3)
      = 300 × 1.585
      = 475.5 bps
    ```

    - Answer: about `475 bps` (474.8 bps using the exact ratio 1.995).

    Interpretation
    - A teleprinter channel is deliberately narrow, and with an SNR of only 3 dB the achievable rate is very low — well under 500 bps.
    - This is why old telex systems ran at 50 to 75 baud: they were designed to work within exactly this kind of limit.
    - The common mistake is to put 3 straight into the formula as the SNR. The dB value must always be converted first.

11. **Using the Nyquist theorem, we can sample 12 million times/sec. Four–level signals provide 2 bits per sample, for a total data rate of 24 Mbps.** *[NESCO Assistant Manager (ICT) 2021 compact it 908 (ET: BUET)]*

    Answer: The statement is `correct`. Here is the verification.

    Given
    - Sampling rate = 12 million samples per second
    - Four-level signalling

    Step 1 — bits per sample
    - With L signal levels, each sample carries log2(L) bits.
    ```
    log2(4) = 2 bits per sample
    ```

    Step 2 — data rate
    ```
    Data rate = samples per second × bits per sample
              = 12,000,000 × 2
              = 24,000,000 bps
              = 24 Mbps
    ```
    - This confirms the stated 24 Mbps.

    Step 3 — the implied bandwidth
    - Nyquist says the maximum useful sampling rate is twice the bandwidth:
    ```
    Sampling rate = 2B  ->  12,000,000 = 2B  ->  B = 6 MHz
    ```
    - Checking with the Nyquist bit-rate formula: C = 2 × B × log2(L) = 2 × 6,000,000 × 2 = 24 Mbps. The two routes agree.

    What changes with more levels

    | Levels L | Bits per sample | Data rate at 12 Msamples/s |
    |---|---|---|
    | 2 | 1 | 12 Mbps |
    | 4 | 2 | `24 Mbps` |
    | 8 | 3 | 36 Mbps |
    | 16 | 4 | 48 Mbps |

    - The catch: more levels means the voltages are closer together, so the receiver needs a much better signal-to-noise ratio. Nyquist sets no limit on L, but Shannon's formula does, through the noise.

12. **In serial communication employing 8 data bits, a parity bit and 2 stop bits. What is the minimum band rate requested to sustain a transfer rate of 300 characters per second?** *[BAUST Assistant Programmer 2021 compact it 918 (ET: N/A)]*

    Answer:

    Given
    - 8 data bits, 1 parity bit, 2 stop bits
    - Transfer rate = 300 characters per second

    Step 1 — total bits per character
    - Asynchronous serial transmission always adds `1 start bit` at the beginning of every character. This is the part most often forgotten.
    ```
    Start bit      = 1
    Data bits      = 8
    Parity bit     = 1
    Stop bits      = 2
    -------------------
    Total          = 12 bits per character
    ```

    Step 2 — required bit rate
    ```
    Bit rate = 300 characters/s × 12 bits/character
             = 3600 bits per second
    ```

    Step 3 — baud rate
    - In simple binary serial signalling one signal element carries one bit, so the baud rate equals the bit rate.
    ```
    Minimum baud rate = 3600 baud
    ```

    - Answer: `3600 baud` (3600 bps).

    ```
    | S | d d d d d d d d | P | E E |   = 12 bit times per character
      ^ start   8 data     parity  2 stop
    ```
    - Efficiency check: only 8 of the 12 bits carry data, so 33 percent of the capacity is framing overhead. This is the classic weakness of asynchronous transmission.
    - Note the distinction: bit rate is bits per second; baud rate is signal changes per second. They are equal only when each symbol carries exactly one bit.

13. **Find signal bit per second bound rate 1000 and 16-QAM signal.** *[BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)]*

    Answer:

    Given
    - Baud rate (symbol rate) = 1000 baud
    - Modulation = 16-QAM

    Step 1 — bits per symbol
    - QAM with M constellation points carries log2(M) bits per symbol.
    ```
    16-QAM -> log2(16) = 4 bits per symbol
    ```

    Step 2 — bit rate
    ```
    Bit rate = baud rate × bits per symbol
             = 1000 × 4
             = 4000 bits per second
    ```

    - Answer: `4000 bps` (4 kbps).

    Bits per symbol for common modulations

    | Modulation | Points | Bits per symbol | Bit rate at 1000 baud |
    |---|---|---|---|
    | ASK / FSK / BPSK | 2 | 1 | 1000 bps |
    | QPSK / 4-QAM | 4 | 2 | 2000 bps |
    | 8-PSK | 8 | 3 | 3000 bps |
    | `16-QAM` | 16 | `4` | `4000 bps` |
    | 64-QAM | 64 | 6 | 6000 bps |
    | 256-QAM | 256 | 8 | 8000 bps |

    - Key relationship: `bit rate = baud rate × log2(M)`. Baud rate is limited by bandwidth, so higher-order modulation is the way to raise the bit rate without more bandwidth — at the cost of needing a much higher SNR, because the constellation points sit closer together.

14. **Channel capacity related math. (প্রশ্ন সংগ্রহ করা সম্ভব হয়নি)** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1038 (ET: BUET)]*

    Answer: The exact question could not be collected, so the two channel-capacity formulas and the standard worked patterns are given.

    Nyquist — maximum data rate of a NOISELESS channel
    ```
    C = 2 × B × log2(L)
    ```
    - B = bandwidth in Hz, L = number of signal levels.
    - Also written as bit rate = baud rate × log2(L), where baud rate = 2B.

    Shannon — capacity of a NOISY channel
    ```
    C = B × log2(1 + SNR)
    SNR(dB) = 10 log10(SNR)        SNR = 10^(SNR_dB / 10)
    ```

    Worked patterns

    Type 1 — noiseless, find the bit rate
    - B = 3 kHz, 2 levels: C = 2 × 3000 × log2(2) = `6000 bps`.
    - B = 3 kHz, 4 levels: C = 2 × 3000 × 2 = `12,000 bps`.

    Type 2 — noiseless, find the number of levels
    - Need 265 kbps over 20 kHz: log2(L) = 265,000 / 40,000 = 6.625, so L = 98.7 -> use `128 levels`.

    Type 3 — noisy, find the capacity
    - B = 3000 Hz, SNR = 3162: C = 3000 × log2(3163) ≈ `34,880 bps`.
    - B = 300 Hz, SNR = 3 dB: convert first, SNR = 10^0.3 ≈ 2, so C = 300 × log2(3) ≈ `475 bps`.

    Type 4 — combine both
    - Shannon gives the ceiling; Nyquist then tells you the number of levels needed to reach a chosen rate below that ceiling. Always compute both and take the lower.
    - Example: B = 1 MHz, SNR = 63. Shannon: C = 10^6 × log2(64) = 6 Mbps. Choosing to run at 4 Mbps, Nyquist gives 4,000,000 = 2 × 10^6 × log2(L), so log2(L) = 2 and L = 4 levels.

    Type 5 — sampling
    - Nyquist sampling rate >= 2 × f_max; Nyquist interval = 1 ÷ (2 f_max).
    - Voice limited to 4 kHz: 8000 samples/s, 8 bits each, giving the 64 kbps DS-0 rate. <!-- verify -->

15. **a) Determine the Nyquist sampling rate and the Nyquist sampling interval for the signal $X(t) = \sin(2100\pi t)$** *[38th BCS 2018 compact it 1177 (ET: N/A)]*

    Answer:

    Given
    ```
    X(t) = sin(2100 π t)
    ```

    Step 1 — find the signal frequency
    - The general form is sin(2π f t), so compare the arguments:
    ```
    2π f t = 2100 π t
    2π f   = 2100 π
    f      = 2100 / 2 = 1050 Hz
    ```

    Step 2 — Nyquist sampling rate
    - The sampling rate must be at least twice the highest frequency present.
    ```
    fs = 2 × f_max = 2 × 1050 = 2100 samples per second (2100 Hz)
    ```

    Step 3 — Nyquist sampling interval
    ```
    Ts = 1 / fs = 1 / 2100 = 4.762 × 10^-4 s = 476.19 microseconds
    ```

    | Quantity | Value |
    |---|---|
    | Signal frequency | 1050 Hz |
    | Nyquist sampling rate | `2100 Hz` (2100 samples/s) |
    | Nyquist sampling interval | `476.19 µs` |

    - Why it matters: sampling any slower than 2100 Hz causes `aliasing`, where the 1050 Hz tone is reconstructed as a different, lower frequency. Aliasing cannot be removed afterwards, which is why an anti-aliasing low-pass filter is placed before every analogue-to-digital converter.
    - The common slip is to read 2100π as the frequency. It is the angular frequency ω; the frequency is ω ÷ 2π.

16. **Consider a noiseless channel with a bandwidth of 3 KHz transmitting a signal with two signal levels. What is the maximum bit rate?** *[Multiple Ministry Assistant Programmer 2017 compact it 1232 (ET: N/A)]*

    Answer: The channel is noiseless, so Nyquist's formula applies.

    Given
    - Bandwidth B = 3 kHz = 3000 Hz
    - Number of signal levels L = 2

    Nyquist formula
    ```
    C = 2 × B × log2(L)
    ```

    Calculation
    ```
    C = 2 × 3000 × log2(2)
      = 2 × 3000 × 1
      = 6000 bps
    ```

    - Answer: maximum bit rate = `6000 bps` (6 kbps).

    Effect of more levels on the same 3 kHz channel

    | Levels L | log2(L) | Maximum bit rate |
    |---|---|---|
    | 2 | 1 | `6000 bps` |
    | 4 | 2 | 12,000 bps |
    | 8 | 3 | 18,000 bps |
    | 16 | 4 | 24,000 bps |

    - The Nyquist formula puts no ceiling on L, so in theory the rate could be raised indefinitely by adding levels. In reality noise limits how finely the receiver can distinguish voltages, and that limit is given by Shannon's formula, C = B log2(1 + SNR).

## Physical Layer & Transmission Media (Cables & Wiring) (15)

1. **Straight through connection vs Crossover connection.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1448 (ET: N/A)]*

   Answer: The difference is in how the two ends of the cable are wired.

   | Point | Straight-through | Crossover |
   |---|---|---|
   | Wiring | Both ends use the same standard (T568A–T568A or T568B–T568B) | One end T568A, the other end T568B |
   | Effect | Pin 1 to pin 1, pin 2 to pin 2, and so on | Transmit and receive pairs are swapped |
   | Connects | Unlike devices | Like devices |
   | Examples | PC to switch, PC to hub, router to switch, switch to router | PC to PC, switch to switch, router to router, PC to router |
   | Pins swapped | None | 1↔3 and 2↔6 |
   | Common use | Almost all normal cabling | Rare today |

   T568B colour order (the common standard)
   ```
   Pin 1  White/Orange      Pin 5  White/Blue
   Pin 2  Orange            Pin 6  Green
   Pin 3  White/Green       Pin 7  White/Brown
   Pin 4  Blue              Pin 8  Brown
   ```
   - T568A swaps the orange and green pairs. Both are electrically identical; only the colour order differs.

   Why the crossover exists
   - On a PC, pins 1 and 2 transmit while 3 and 6 receive. A switch is wired the opposite way (MDI-X), so a straight cable already lines up transmit with receive.
   - Connect two PCs directly and both would transmit on 1 and 2, so nothing is received. The crossover swaps the pairs to fix this.

   ```
   STRAIGHT-THROUGH        CROSSOVER
   1 --------- 1           1 ----\ /---- 1
   2 --------- 2           2 ---\ X /--- 2
   3 --------- 3           3 ----/ \---- 3
   6 --------- 6           6 ---------- 6
   ```

   - Modern relevance: almost every device made since about 2005 supports `Auto-MDI/MDIX`, which detects the wiring and adjusts automatically. In practice a straight-through cable now works everywhere, and crossover cables survive mainly on legacy equipment and in exam questions.

2. **Which transmission medium is used in LAN? Write their maximum length and capacity (bps).** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1452 (ET: N/A)]*

   Answer: The transmission media used in a LAN, with their limits.

   | Medium | Standard | Maximum length | Maximum capacity |
   |---|---|---|---|
   | UTP Cat5e | 1000BASE-T | 100 m | 1 Gbps |
   | UTP Cat6 | 1000BASE-T / 10GBASE-T | 100 m at 1 Gbps, 55 m at 10 Gbps | 10 Gbps |
   | UTP Cat6a | 10GBASE-T | 100 m | 10 Gbps |
   | UTP Cat7 / Cat8 | 40GBASE-T | 100 m / 30 m | 10–40 Gbps |
   | Coaxial (10BASE2, thin) | 10BASE2 | 185 m | 10 Mbps |
   | Coaxial (10BASE5, thick) | 10BASE5 | 500 m | 10 Mbps |
   | Multimode fibre | 1000BASE-SX, 10GBASE-SR | 550 m (1 Gbps), 300 m (10 Gbps) | 10–100 Gbps |
   | Single-mode fibre | 1000BASE-LX, 10GBASE-LR | 10 km, up to 80 km with ZR optics | 100 Gbps and beyond |
   | Wireless (Wi-Fi 6) | IEEE 802.11ax | 30–100 m indoors | Up to about 9.6 Gbps shared |

   The most common LAN medium
   - `UTP Cat5e or Cat6 with RJ45 connectors` is the standard choice for the horizontal cabling that reaches each desk: cheap, easy to terminate, and adequate at 1 Gbps to 100 m.
   - Optical fibre is used for the backbone between floors and buildings, because it has no distance limit at LAN scale and is immune to electrical interference.

   Why 100 m is the limit for UTP
   - The standard allows 90 m of solid horizontal cable plus 5 m of stranded patch cable at each end. Beyond that, attenuation weakens the signal and propagation delay breaks the collision-detection timing of the original Ethernet design.
   - A repeater, switch or media converter is used to go further.

3. **IEEE __________ Standard used Ethernet LAN?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: Ethernet LAN uses the `IEEE 802.3` standard.

   - IEEE 802.3 defines both the physical layer and the MAC sub-layer of wired Ethernet, including frame format, addressing and the CSMA/CD access method used on shared media.

   The IEEE 802 family

   | Standard | Technology |
   |---|---|
   | 802.1 | Bridging, VLANs (802.1Q), Spanning Tree |
   | 802.2 | LLC (Logical Link Control) |
   | `802.3` | `Ethernet` (CSMA/CD) |
   | 802.4 | Token Bus (obsolete) |
   | 802.5 | Token Ring (obsolete) |
   | 802.11 | Wireless LAN (Wi-Fi) |
   | 802.15.1 | Bluetooth |
   | 802.15.4 | Zigbee, low-rate WPAN |
   | 802.16 | WiMAX |
   | 802.3af / 802.3at | Power over Ethernet |

   Common 802.3 variants
   - 10BASE-T (10 Mbps), 100BASE-TX (Fast Ethernet), 1000BASE-T (Gigabit), 10GBASE-T (10 Gigabit), and the fibre versions 1000BASE-SX and 1000BASE-LX.
   - The naming reads as: speed, BASE for baseband signalling, and then the medium or reach — T for twisted pair, F or S/L for fibre.

4. **What is the connector name copper cable in LAN?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*

   Answer: The connector used with copper cable in a LAN is the `RJ45` connector.

   - Full form: Registered Jack 45. It is an 8-position, 8-contact (8P8C) modular plug used to terminate UTP and STP twisted-pair cable.
   - It carries four pairs — eight wires — wired to either the T568A or the T568B colour standard.
   - It is used with Cat5e, Cat6, Cat6a and Cat7 cables for 10BASE-T through 10GBASE-T Ethernet.
   - Tools: a crimping tool to attach it, and a cable tester to verify continuity and pair order.

   Other connectors worth knowing

   | Connector | Used with |
   |---|---|
   | `RJ45` | UTP/STP Ethernet — 8 pins |
   | RJ11 | Telephone line and DSL — 4 or 6 pins, physically smaller |
   | BNC | Thin coaxial cable, 10BASE2 |
   | AUI / Vampire tap | Thick coaxial cable, 10BASE5 |
   | F-type | Cable TV and cable modem coaxial |
   | SC, LC, ST, MTRJ | Optical fibre |
   | GBIC / SFP / SFP+ | Transceiver modules in switches |

   - Note that RJ45 and RJ11 look similar but are not interchangeable — RJ11 is narrower and will damage an RJ45 port's contacts if forced in.

5. **What are the different types of transmission media used for data communication? Explain their advantages and disadvantages.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 326 (ET: BIBM)]*

   Answer: Transmission media are divided into guided (wired) and unguided (wireless).

   GUIDED MEDIA

   1. Twisted pair (UTP and STP)
   - Pairs of insulated copper wires twisted together; the twisting cancels external noise and reduces crosstalk.
   - Categories: Cat5e (1 Gbps), Cat6 (10 Gbps to 55 m), Cat6a (10 Gbps to 100 m). Maximum run 100 m, RJ45 connector.
   - Advantages: cheapest, easy to install and terminate, flexible, lightweight, universally supported, and adequate for almost all desk connections.
   - Disadvantages: limited to 100 m, susceptible to EMI and crosstalk (especially UTP), lower bandwidth than fibre, and can be tapped for eavesdropping.

   2. Coaxial cable
   - A central copper conductor, insulation, a braided metal shield and an outer jacket. The shield gives good noise immunity.
   - Types: thinnet 10BASE2 (185 m) and thicknet 10BASE5 (500 m); also used for cable TV and cable internet.
   - Advantages: better noise immunity and longer runs than twisted pair, higher bandwidth than early twisted pair, still widely used for CATV and HFC broadband.
   - Disadvantages: bulky and inflexible, more expensive than UTP, harder to install, and obsolete for LANs.

   3. Optical fibre
   - A glass or plastic core carrying light by total internal reflection, surrounded by cladding and a protective jacket.
   - Single-mode (small core, laser source, tens of kilometres) and multimode (larger core, LED or VCSEL source, hundreds of metres).
   - Advantages: by far the highest bandwidth (terabits per fibre with WDM), extremely low attenuation so runs of kilometres are routine, complete immunity to EMI and RFI, no crosstalk, very hard to tap undetected, light and thin, no electrical hazard.
   - Disadvantages: expensive cable and equipment, fragile — it breaks if bent too sharply, splicing and termination need skilled technicians and costly tools, and it cannot carry power.

   UNGUIDED MEDIA

   4. Radio waves (3 kHz – 1 GHz)
   - Omnidirectional, pass through walls, used for Wi-Fi, Bluetooth, AM/FM radio and mobile networks.
   - Advantages: mobility, no cabling cost, easy to deploy, covers difficult areas.
   - Disadvantages: shared bandwidth, interference, weaker security, and range limited by obstacles.

   5. Microwave (1–300 GHz)
   - Highly directional and line-of-sight, used for point-to-point links and satellite uplinks.
   - Advantages: high bandwidth over long distances without laying cable, useful across rivers and mountains.
   - Disadvantages: needs clear line of sight, affected by rain and atmospheric conditions, needs licences and tall towers.

   6. Infrared
   - Short range and line of sight, blocked by walls, used for remote controls and some device-to-device links.
   - Advantages: cheap, secure because it cannot leave the room, no licence needed. Disadvantages: very short range, no obstacle penetration, disturbed by sunlight.

   7. Satellite
   - Reaches anywhere on earth, including oceans and remote regions.
   - Advantages: enormous coverage, useful for broadcast and disaster recovery. Disadvantages: very high cost, and geostationary satellites add about 250 ms one-way latency (LEO constellations reduce this greatly).

   Choosing between them

   | Requirement | Best choice |
   |---|---|
   | Cheap desk connection | UTP Cat6 |
   | Long distance, high bandwidth | Single-mode fibre |
   | Immunity to interference | Fibre |
   | Mobility | Wi-Fi or cellular |
   | Remote area, no infrastructure | Satellite |

6. **Difference between Guided and Unguided media. Difference between STP and UTP. Why using benefit UTP instead of STP?** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 523 (ET: MIST)]*

   Answer:

   (a) Guided vs unguided media

   | Point | Guided (wired) | Unguided (wireless) |
   |---|---|---|
   | Path | A physical conductor confines the signal | The signal travels through free space |
   | Direction | Point to point along the cable | Broadcast in all directions (or a beam) |
   | Examples | Twisted pair, coaxial, optical fibre | Radio, microwave, infrared, satellite |
   | Bandwidth | Very high, especially fibre | Lower and shared |
   | Interference | Low, and shielded further in STP and fibre | High — other signals, weather, obstacles |
   | Security | Better; physical access is needed to tap | Weaker; anyone in range can capture the signal |
   | Installation | Cabling cost and effort | Quick, no cabling |
   | Mobility | None | Full |
   | Distance | Limited by attenuation, but fibre reaches far | Limited by power, obstacles and frequency |
   | Cost | Higher installation, lower running cost | Lower installation, licence fees possible |

   (b) STP vs UTP

   | Point | UTP (Unshielded Twisted Pair) | STP (Shielded Twisted Pair) |
   |---|---|---|
   | Shielding | None — twisting alone resists noise | Foil or braid around each pair and/or the whole bundle |
   | Noise immunity | Moderate | High |
   | Cost | Cheaper | More expensive |
   | Diameter and weight | Thin, light | Thick, heavy |
   | Flexibility | Easy to pull round corners | Stiff, larger bend radius |
   | Installation | Simple; no earthing needed | Must be properly grounded at one end, or the shield becomes an antenna |
   | Termination | Standard RJ45, quick | Needs shielded connectors and more care |
   | Speed and distance | 1–10 Gbps to 100 m | Same, but more reliable in noisy places |
   | Typical use | Offices, homes, most LANs | Factories, hospitals, near heavy machinery, data centres |

   (c) Why UTP is preferred over STP
   - `Lower cost` — both the cable and the connectors are significantly cheaper, and in a building with hundreds of runs this dominates the decision.
   - `Easier installation` — thinner, lighter and more flexible, so it pulls through conduit easily and needs no grounding scheme.
   - `No grounding risk` — an improperly earthed STP shield can pick up noise instead of blocking it, or create a ground loop, making the situation worse than plain UTP.
   - `Sufficient performance` — in a normal office the twisting alone gives enough noise rejection for 1 Gbps and even 10 Gbps over Cat6a.
   - `Standard connectors and tools` — ordinary RJ45 plugs and crimpers, which every technician already has.
   - `Smaller bend radius and less conduit space`, which matters in crowded cable trays.

   - STP is still the right choice where interference is genuinely severe: near motors, welding equipment, X-ray machines, or long parallel runs beside power cables.

7. **What is the main benefit of broadband transmission system compared to baseband? What is the attenuation of transmission media? Distinguish between twisted pair, co-axial cable and fiber optics in tabular form.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 530 (ET: MIST)]*

   Answer:

   (a) Main benefit of broadband over baseband

   | Point | Baseband | Broadband |
   |---|---|---|
   | Signal | The digital signal is placed directly on the medium | Signals are modulated onto different carrier frequencies |
   | Channels | One channel uses the whole medium | Many channels share the medium by FDM |
   | Direction | Usually bidirectional (half duplex) | Usually unidirectional per channel |
   | Distance | Shorter; needs repeaters | Longer; uses amplifiers |
   | Example | Ethernet (10BASE-T) | Cable TV, ADSL, cable internet |

   - The main benefit of broadband is that it can carry `multiple simultaneous signals over one medium` by dividing it into frequency channels. One coaxial cable can therefore carry dozens of TV channels plus internet data at the same time, and it can also reach much further because amplifiers handle analogue signals over long distances.

   (b) Attenuation of transmission media
   - Attenuation is the loss of signal strength as the signal travels through a medium, caused by absorption and resistance in the material.
   - It is measured in decibels: `Attenuation (dB) = 10 log10(P2 / P1)`, a negative value indicating loss.
   - It increases with distance and with frequency, so higher-speed signals fade faster — this is why cable length limits exist.
   - Remedies: amplifiers for analogue signals, and repeaters for digital signals, which regenerate a clean new signal instead of amplifying the noise as well.

   Typical attenuation
   - UTP Cat5e/Cat6: high, hence the 100 m limit.
   - Coaxial: lower than twisted pair, so 185 m and 500 m runs were possible.
   - Optical fibre: extremely low, about 0.2 dB per kilometre at 1550 nm, which is why fibre spans tens of kilometres without regeneration.

   (c) Twisted pair vs coaxial vs fibre optic

   | Point | Twisted pair | Coaxial cable | Optical fibre |
   |---|---|---|---|
   | Signal carried | Electrical | Electrical | Light |
   | Bandwidth | Up to about 10 Gbps | Up to about 1 Gbps typical | Terabits with WDM |
   | Distance | 100 m | 185 m (thin), 500 m (thick) | 300 m to 80 km and beyond |
   | Attenuation | High | Medium | Very low |
   | EMI immunity | Poor (UTP), better (STP) | Good, thanks to the shield | Complete immunity |
   | Crosstalk | Present | Very low | None |
   | Security | Easy to tap | Can be tapped | Very hard to tap undetected |
   | Cost | Lowest | Medium | Highest (cable and equipment) |
   | Installation | Easy | Moderate | Skilled work; splicing needs a fusion splicer |
   | Flexibility | Very flexible | Stiff | Fragile, minimum bend radius |
   | Weight | Light | Heavy | Very light |
   | Connector | RJ45 | BNC, F-type | SC, LC, ST |
   | Typical use | Desk connections in a LAN | Cable TV, HFC broadband | Backbone, WAN, submarine cables |

8. **Why we used straight-through and cross cable with example?** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 595 (ET: N/A)]*

   Answer:

   Why the two cable types exist
   - A network interface transmits on one pair and receives on another. On a PC or router (MDI), pins 1 and 2 transmit and pins 3 and 6 receive. On a switch or hub (MDI-X), the roles are reversed internally.
   - Connecting two devices therefore requires that one side's transmit reaches the other side's receive. Whether the crossing is needed in the cable depends on whether the two devices are of the same type or not.

   Straight-through cable
   - Both ends wired identically (T568A–T568A or T568B–T568B). Pin 1 to pin 1, and so on.
   - Used to connect `unlike` devices, where one is MDI and the other MDI-X, so the crossing already happens inside the switch.
   - Examples:
     - PC to switch
     - PC to hub
     - Router to switch
     - Switch to router
     - Wireless access point to switch

   Crossover cable
   - One end T568A, the other T568B, which swaps pins 1↔3 and 2↔6.
   - Used to connect `like` devices, where both would otherwise transmit on the same pins.
   - Examples:
     - PC to PC directly
     - Switch to switch
     - Router to router
     - Hub to hub
     - PC to router (both are MDI, so this needs a crossover)

   ```
   STRAIGHT-THROUGH                CROSSOVER
   PC  1 TX ------- 1 RX  Switch   PC-A 1 TX ---\ /--- 1 TX PC-B
   PC  2 TX ------- 2 RX  Switch   PC-A 2 TX --\ X /-- 2 TX PC-B
   PC  3 RX ------- 3 TX  Switch   PC-A 3 RX --/ \--- 3 RX PC-B
   PC  6 RX ------- 6 TX  Switch   PC-A 6 RX -------- 6 RX PC-B
      (switch crosses internally)     (cable does the crossing)
   ```

   Memory rule
   - Different devices -> straight-through. Same devices -> crossover.
   - The one exception people forget is PC to router: although they look different, both are MDI, so a crossover is required on old equipment.

   Modern practice
   - Almost all equipment made since around 2005 supports `Auto-MDI/MDIX`, which senses the wiring and switches internally. With such equipment either cable works, and crossover cables have largely disappeared from use.

9. **(খ) Fiber optic cable, Twisted pair cable এবং Co-axial cable এর সুবিধাগুলো বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 629 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   Optical fibre cable — advantages
   - Enormous bandwidth: terabits per second on a single fibre using WDM, far beyond any copper medium.
   - Very low attenuation, about 0.2 dB per kilometre, so signals travel tens of kilometres without regeneration.
   - Complete immunity to electromagnetic and radio interference, since it carries light, not electricity. It can run beside power cables safely.
   - No crosstalk between fibres.
   - Very high security: tapping a fibre without being detected is extremely difficult.
   - Light and thin, so a single duct carries far more capacity than with copper.
   - No electrical hazard, no spark risk, and no earthing problems — it is safe in explosive or high-voltage environments.
   - Not affected by corrosion or moisture in the way copper is.

   Twisted pair cable — advantages
   - Cheapest of all media, both cable and connectors.
   - Very easy to install, terminate and test; ordinary RJ45 plugs and a crimping tool are enough.
   - Thin, light and flexible, so it pulls easily through conduit and around corners.
   - Universally supported — every PC, switch and printer has an RJ45 port.
   - Adequate performance for almost all desk connections: 1 Gbps on Cat5e and 10 Gbps on Cat6a, both to 100 m.
   - Supports Power over Ethernet, so a single cable powers an IP phone, camera or access point.
   - Twisting itself cancels much of the external noise, and the shielded version (STP) handles noisy environments.

   Coaxial cable — advantages
   - Better noise immunity than unshielded twisted pair, because of the braided shield around the conductor.
   - Longer runs than twisted pair: 185 m for thinnet and 500 m for thicknet.
   - Higher bandwidth than early twisted pair, and a broadband coaxial system carries many frequency-division channels at once — this is how cable TV delivers dozens of channels plus internet on one cable.
   - Robust and durable; the construction resists physical damage.
   - Well suited to CATV and HFC broadband distribution, where it is still in wide use.

   - Summary of when each is chosen: fibre for backbone and long distance, twisted pair for the last hundred metres to the desk, coaxial for television and cable-broadband distribution.

10. **What happens when you use cables longer than the prescribed length in a network?** *[BOF Assistant Programmer 2022 compact it 732 (ET: MIST)]*

    Answer: Exceeding the specified cable length causes the signal to degrade beyond what the receiver can correctly interpret. Several distinct problems appear.

    1. Attenuation
    - The signal loses strength with distance. Past the limit it becomes too weak for the receiver to distinguish 1 from 0, so bits are misread.

    2. Increased errors and retransmissions
    - Frames fail their CRC and are discarded. TCP retransmits them, so throughput falls sharply even though the link appears to be up.

    3. Intermittent or no connectivity
    - The link may fail to come up at all, or come up and drop repeatedly — the hardest kind of fault to diagnose, because it works sometimes.

    4. Timing and collision-detection failure (on shared Ethernet)
    - Classic Ethernet requires that a station still be transmitting when a collision reaches it. Excess length increases propagation delay, so collisions are detected too late — `late collisions` — and the frame is lost without retransmission by the MAC layer.

    5. Distortion and jitter
    - Different frequency components attenuate differently and arrive at slightly different times, spreading pulses into one another (intersymbol interference) and making the receiver's clock recovery unreliable.

    6. Speed negotiation dropping
    - A gigabit link may negotiate down to 100 Mbps, or a 10 Gbps link to 1 Gbps, because the higher speed cannot be sustained over the distance.

    7. More noise pickup
    - A longer run acts as a longer antenna, collecting more EMI and crosstalk.

    Standard limits

    | Medium | Limit |
    |---|---|
    | UTP Cat5e/Cat6 | 100 m (90 m solid + 2 × 5 m patch) |
    | Coaxial 10BASE2 | 185 m |
    | Coaxial 10BASE5 | 500 m |
    | Multimode fibre | 550 m at 1 Gbps, 300 m at 10 Gbps |
    | Single-mode fibre | 10 km, more with specialised optics |

    Solutions
    - Insert a `repeater` or, better, a `switch` at the midpoint to regenerate the signal.
    - Use `optical fibre` for the long run and a media converter at each end.
    - Redesign the cabling so that each horizontal run stays within 100 m by placing an intermediate distribution frame.
    - For a link that must be long and cheap, consider a wireless bridge instead.

11. **(ii) ব্যাখ্যা করুন: (a) 10Base5 (b) 10BaseF** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 789 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The naming convention reads as `<speed> BASE <medium or segment length>`.

    (a) 10BASE5 — "Thick Ethernet" or Thicknet
    - `10` = 10 Mbps data rate.
    - `BASE` = baseband signalling, meaning the digital signal occupies the whole medium with no modulation.
    - `5` = maximum segment length of 500 metres.
    - Medium: thick coaxial cable, about 10 mm diameter, rigid and yellow, hence the nickname "frozen yellow garden hose".
    - Topology: bus. Stations attach with a `vampire tap` that pierces the jacket to reach the core, connected through an AUI cable to a transceiver.
    - Rules: maximum 100 stations per segment, taps at least 2.5 m apart, both ends terminated with 50-ohm terminators, and the 5-4-3 rule (up to 5 segments, 4 repeaters, 3 populated).
    - It was the original Ethernet (IEEE 802.3, 1983), and it is completely obsolete: expensive, hard to install, and a single break brought down the entire segment.

    (b) 10BASE-F — Fibre Ethernet
    - `10` = 10 Mbps.
    - `BASE` = baseband.
    - `F` = optical fibre as the medium.
    - Uses two multimode fibres, one for transmit and one for receive, so it is naturally full duplex capable.
    - Segment length up to 2000 m, far beyond copper, because fibre attenuation is very low.
    - Complete immunity to EMI, so it suits runs between buildings, through industrial areas, or anywhere lightning or ground-potential differences make copper dangerous.
    - Variants: 10BASE-FL (link, 2 km, the common one), 10BASE-FB (backbone, for repeater interconnection) and 10BASE-FP (passive star).

    Comparison

    | Point | 10BASE5 | 10BASE-F |
    |---|---|---|
    | Medium | Thick coaxial | Optical fibre |
    | Segment length | 500 m | 2000 m |
    | Topology | Bus | Point to point / star |
    | EMI immunity | Moderate | Complete |
    | Installation | Very difficult | Skilled, needs splicing |
    | Status | Obsolete | Superseded by 100BASE-FX and gigabit fibre |

12. **Explain 10baseT.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 839 (ET: N/A)]*

    Answer: 10BASE-T is the IEEE 802.3i Ethernet standard that runs at 10 Mbps over twisted-pair cable. It is the version that made Ethernet universal.

    Reading the name
    - `10` = 10 Mbps data rate.
    - `BASE` = baseband signalling; the digital signal uses the entire medium with no carrier modulation.
    - `T` = twisted pair as the medium.

    Specifications
    - Medium: Category 3 or better UTP, using two of the four pairs — one for transmit (pins 1 and 2) and one for receive (pins 3 and 6).
    - Connector: RJ45.
    - Maximum segment length: `100 m` from the station to the hub or switch.
    - Topology: physical `star` — every station has its own cable to a central hub or switch. Logically it behaved as a bus when hubs were used.
    - Encoding: Manchester, which is self-clocking, so no separate clock line is needed. This costs bandwidth: 10 Mbps of data needs 20 Mbaud of signalling.
    - Access method: CSMA/CD on a hub; not needed on a full-duplex switched link.
    - Rules: the 5-4-3 rule for repeaters, and a minimum frame size of 64 bytes so that collisions are always detected in time.

    Why it replaced coaxial Ethernet
    - Star topology means one broken cable affects only one station, whereas a break in a 10BASE2 or 10BASE5 bus killed the whole segment.
    - Cheap, thin, flexible cable that is easy to install and terminate.
    - Easy to add or move a station — just patch a new port.
    - Central management and easy fault isolation; a link light shows immediately whether a station is connected.
    - It made structured cabling possible, which is why every modern building is wired this way.

    The family that followed
    - 100BASE-TX (Fast Ethernet, Cat5, 100 Mbps), 1000BASE-T (Gigabit, Cat5e, uses all four pairs), 10GBASE-T (Cat6a). All keep the 100 m limit and the RJ45 connector.

13. **Which media transfer data with higher bandwidth? Advantages of this media.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 843 (ET: N/A)]*

    Answer: `Optical fibre` transfers data with the highest bandwidth of any transmission medium.

    Capacity
    - A single fibre carries terabits per second when wavelength division multiplexing is used: DWDM puts 40 to 160 separate wavelengths on one strand, each carrying 100 Gbps or more.
    - Individual links: 10, 40, 100 and 400 Gbps Ethernet are all standard, and submarine cables carry hundreds of terabits per fibre pair.
    - Copper, by comparison, tops out at about 10–40 Gbps over 30–100 m.

    Advantages of optical fibre

    - Enormous bandwidth — the usable optical spectrum is vastly wider than anything copper can support, and WDM multiplies it further.
    - Very low attenuation, about 0.2 dB per kilometre at 1550 nm, so signals travel 80 km or more without regeneration. Copper needs a repeater every 100 m.
    - Complete immunity to electromagnetic and radio interference, because it carries light rather than current. It can be run beside power cables, motors and radio transmitters with no effect.
    - No crosstalk between fibres in the same cable.
    - High security: tapping a fibre requires physically bending or breaking it, which is detectable, so eavesdropping is very difficult.
    - Light and thin — a fibre cable of the same capacity weighs a fraction of copper, so ducts hold far more capacity.
    - No electrical hazard: no sparks, no short circuits, no ground loops and no lightning-induced surges. It is safe in explosive atmospheres and between buildings at different ground potentials.
    - Not corroded by moisture the way copper conductors are.
    - Long service life and excellent future-proofing — the same installed fibre supports higher speeds simply by changing the transceivers at each end.

    Disadvantages, for balance
    - Higher cost of cable, transceivers and test equipment; fragile with a minimum bend radius; splicing and termination need trained technicians and a fusion splicer; and it cannot deliver power the way PoE does over copper.

    - Uses: internet backbones, submarine cables, metro and campus backbones, data centre interconnects, FTTH broadband, and CCTV or industrial links in electrically noisy places.

14. **(a) What are the problems that transmission lines suffer from? Briefly describe any one of them.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1026-1027 (ET: N/A)]*

    Answer: Transmission lines suffer from three principal problems — `attenuation`, `distortion` and `noise`. Any of these can corrupt the signal enough to cause bit errors.

    The problems in brief
    - Attenuation — the signal weakens with distance as energy is absorbed by the medium.
    - Distortion — the signal changes shape, because different frequency components travel at different speeds and are attenuated by different amounts.
    - Noise — unwanted energy added to the signal: thermal, intermodulation, crosstalk and impulse noise.
    - Related effects: jitter (timing variation), echo (reflections from impedance mismatches), fading (varying strength on radio links) and limited bandwidth.

    Described in detail — Attenuation

    - Definition: attenuation is the loss of signal strength as the signal propagates. Electrical energy is converted to heat by the resistance of the conductor, and optical energy is absorbed and scattered in the fibre.

    - Measurement, in decibels:
    ```
    Attenuation (dB) = 10 × log10 (P2 / P1)
    ```
    where P1 is the transmitted power and P2 the received power. A negative result indicates loss; −3 dB means half the power has been lost.

    - Two properties that matter in practice
      - It grows with `distance`. Every metre of cable removes some energy, which is exactly why maximum cable lengths are specified: 100 m for UTP, 185 m for thin coaxial.
      - It grows with `frequency`. High-frequency components fade faster than low-frequency ones, so a square pulse arrives rounded and spread. This is why higher data rates are limited to shorter distances — Cat6 supports 10 Gbps at 55 m but only 1 Gbps at 100 m.

    - Consequence: once the received power falls near the noise level, the receiver can no longer decide reliably between 0 and 1. Errors rise, CRC checks fail, frames are retransmitted, and throughput collapses even though the link still appears connected.

    - Remedies
      - `Amplifier` for analogue signals — but it amplifies the accumulated noise as well, so noise builds up over every span.
      - `Repeater` for digital signals — it decides each bit and generates a completely clean new signal, discarding the noise entirely. This is the decisive advantage of digital transmission.
      - `Equaliser`, to boost high frequencies more than low ones and flatten the response.
      - Choosing a lower-loss medium: optical fibre loses only about 0.2 dB per kilometre, against tens of dB per hundred metres for copper.
      - Keeping runs within the specified length, and using thicker conductors where practical.

15. **Explain 10Base2, 10Base5, 10BaseT and Ethernet.** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 1276-1277 (ET: N/A)]*

    Answer: The naming convention is `<speed> BASE <medium or maximum segment length>`, where BASE means baseband signalling.

    Ethernet
    - The dominant LAN technology, standardised as `IEEE 802.3`. It defines the frame format, 48-bit MAC addressing and, on shared media, the CSMA/CD access method.
    - Frame: preamble, destination MAC, source MAC, type/length, data (46–1500 bytes) and FCS. Minimum frame 64 bytes, maximum 1518 bytes.
    - Invented by Robert Metcalfe at Xerox PARC in 1973 and standardised in 1983.
    - It has scaled from 10 Mbps to 400 Gbps while keeping the same frame format, which is the main reason it displaced every competing LAN technology.

    10BASE2 — Thin Ethernet, "Cheapernet"
    - 10 Mbps, baseband, `185 m` maximum segment (the 2 stands for approximately 200 m).
    - Medium: thin RG-58 coaxial cable, about 5 mm, flexible.
    - Connector: BNC, with T-connectors at each station and 50-ohm terminators at both ends.
    - Topology: bus. Maximum 30 stations per segment, minimum 0.5 m between taps.
    - Cheaper and easier than 10BASE5, but a single break or a missing terminator brought down the whole segment.

    10BASE5 — Thick Ethernet, "Thicknet"
    - 10 Mbps, baseband, `500 m` maximum segment.
    - Medium: thick, rigid yellow coaxial cable about 10 mm in diameter.
    - Stations attach with a `vampire tap` piercing the jacket, linked by an AUI drop cable to a transceiver.
    - Topology: bus. Maximum 100 stations per segment, taps at least 2.5 m apart, terminators at both ends.
    - The original Ethernet. Expensive and very hard to install, and equally vulnerable to a single cable break.

    10BASE-T — Twisted Pair Ethernet
    - 10 Mbps, baseband, twisted-pair medium, `100 m` maximum from station to hub or switch.
    - Medium: Cat3 or better UTP with RJ45 connectors, using two of the four pairs.
    - Topology: physical `star` around a hub or switch.
    - Encoding: Manchester, which is self-clocking.
    - This is the version that made Ethernet universal, because a broken cable affects only one station, cabling is cheap and flexible, moves and additions are trivial, and faults are easy to isolate.

    Comparison

    | Point | 10BASE5 | 10BASE2 | 10BASE-T |
    |---|---|---|---|
    | Medium | Thick coax | Thin coax | UTP |
    | Segment length | 500 m | 185 m | 100 m |
    | Topology | Bus | Bus | Star |
    | Connector | Vampire tap / AUI | BNC | RJ45 |
    | Stations per segment | 100 | 30 | 1 per port |
    | Effect of a break | Whole segment down | Whole segment down | One station only |
    | Cost | High | Medium | Low |
    | Status | Obsolete | Obsolete | Superseded by 100BASE-TX and gigabit |

## Error Detection & Data Communication (CRC, Throughput) (14)

1. (a) CMY color model এর উপাদানগুলো লিখুন (CMY color model এর কাজ কী?)
   (b) CRC এর কাজ কী? (IIB CRC-16 এর ক্ষেত্র এবং প্রশ্নগুলো আলোচনা করুন)
   (c) Data communication এর ক্ষেত্রে bandwidth এবং throughput এর মধ্যে পার্থক্য লিখুন। *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   (a) CMY colour model
   - CMY stands for `Cyan, Magenta, Yellow` — the three subtractive primary colours.
   - It is a `subtractive` model: each ink absorbs (subtracts) one additive primary from white light. Cyan absorbs red, magenta absorbs green, yellow absorbs blue.
   - Relationship with RGB:
   ```
   C = 1 − R
   M = 1 − G
   Y = 1 − B
   ```
   - Work it does: it is the model used for `printing` on paper, where the medium reflects light rather than emitting it. RGB is used for screens, which emit light and are therefore additive.
   - In practice printers use `CMYK`, adding a separate black (K) ink, because mixing equal C, M and Y gives a muddy dark brown rather than true black, and because black ink is far cheaper than using three coloured inks together.
   - Colour result: C + M = blue, M + Y = red, C + Y = green, C + M + Y = black (theoretically).

   (b) Work of CRC, and CRC-16
   - CRC (Cyclic Redundancy Check) is an `error-detection` method. The sender treats the data as a binary polynomial, divides it by an agreed generator polynomial using modulo-2 division, and appends the remainder as check bits. The receiver divides the whole received frame by the same generator; a remainder of zero means no error was detected.
   - What it detects: all single-bit errors, all double-bit errors (with a suitable generator), all odd numbers of errors, and all burst errors shorter than the CRC length. This last property is why it is used on real links, where errors arrive in bursts.
   - It only detects errors; it cannot correct them. A frame that fails is discarded and retransmitted.

   CRC-16
   - Generator polynomial: `x^16 + x^15 + x^2 + 1` (the CRC-16-IBM/ANSI form), giving a 16-bit remainder appended to the frame.
   - It detects all bursts of 16 bits or fewer, and 99.997 percent of longer bursts.
   - Uses: Modbus, USB, HDLC, Bisync and many industrial protocols.
   - Other common variants: CRC-32 (Ethernet FCS, ZIP, PNG) and CRC-CCITT, x^16 + x^12 + x^5 + 1.

   (c) Bandwidth vs throughput

   | Point | Bandwidth | Throughput |
   |---|---|---|
   | Meaning | Maximum theoretical capacity | Rate actually achieved |
   | Nature | Fixed by the link | Varies with conditions |
   | Value | Always the higher figure | Always lower |
   | Affected by | Medium and technology | Congestion, errors, overhead, distance |
   | Example | A 100 Mbps port | 85 Mbps measured in a real transfer |

   - Throughput is lower because of protocol headers, retransmissions, congestion, the bottleneck link on the path and device limits. `Goodput` is narrower still — only the useful application data.

2. **Data communication mathematical problems.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1368 (ET: BUET)]*

   Answer: The exact problems were not printed, so the standard data-communication formulas and worked patterns are given.

   Channel capacity
   ```
   Nyquist (noiseless):  C = 2 B log2(L)
   Shannon (noisy):      C = B log2(1 + SNR)
   SNR(dB) = 10 log10(SNR)          SNR = 10^(SNR_dB/10)
   ```
   - Example: B = 3000 Hz, SNR = 3162 -> C = 3000 × log2(3163) ≈ 34,880 bps.

   Delay and latency
   ```
   Transmission delay = message size (bits) / bandwidth (bps)
   Propagation delay  = distance / propagation speed  (2 × 10^8 m/s in cable)
   Queuing delay      = time waiting in router buffers
   Total latency      = transmission + propagation + queuing + processing
   ```
   - Example: a 3000-byte message on a 1 Gbps link over 300 km gives 0.024 ms transmission and 1.5 ms propagation.

   Bit rate, baud rate and modulation
   ```
   Bit rate = baud rate × log2(M)
   ```
   - 16-QAM at 1000 baud gives 4000 bps.

   Sampling and PCM
   ```
   Sampling rate >= 2 × f_max        (Nyquist)
   Bit rate = sampling rate × bits per sample
   ```
   - Voice limited to 4 kHz: 8000 samples/s × 8 bits = 64 kbps, the DS-0 rate.

   Multiplexing
   ```
   TDM output rate = sum of input rates + framing overhead
   Frame size = (number of sources × unit size) + framing bits
   FDM link bandwidth = n × channel bandwidth + (n − 1) × guard band
   ```
   - T-1: (24 × 8 + 1) × 8000 = 1.544 Mbps.

   Throughput and utilisation
   ```
   Throughput = data delivered / time taken
   Packets per second = bandwidth / (packet size in bits)
   Bandwidth-delay product = bandwidth × RTT
   ```
   - 10 Mbps with 1500-byte packets supports 833 packets per second.

   Error detection
   ```
   CRC: append (degree of generator) zeros, divide modulo 2, append the remainder.
   ```
   - Data 11100 with divisor 1001 gives remainder 111, so 11100111 is transmitted. <!-- verify -->

3. **Question on data communication transmission and signal related math.** *[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1441 (ET: BUET)]*

   Answer: The exact question was not printed, so the standard transmission and signal formulas with worked patterns are given.

   Signal fundamentals
   ```
   Period T and frequency f:   f = 1 / T
   Wavelength:                 λ = c / f      (c = 3 × 10^8 m/s in vacuum)
   Bandwidth of a composite signal = highest frequency − lowest frequency
   ```
   - A telephone channel from 300 Hz to 3300 Hz has a bandwidth of 3000 Hz.

   Signal power and decibels
   ```
   Attenuation / gain (dB) = 10 log10 (P2 / P1)
   SNR = signal power / noise power
   SNR(dB) = 10 log10(SNR)
   ```
   - Signal 10 mW, noise 1 µW: SNR = 10,000, which is 40 dB.

   Data rate
   ```
   Noiseless (Nyquist):  C = 2 B log2(L)
   Noisy (Shannon):      C = B log2(1 + SNR)
   Bit rate = baud rate × log2(M)
   ```
   - 265 kbps over a noiseless 20 kHz channel needs log2(L) = 6.625, so 128 levels.

   Digitisation (PCM)
   ```
   Sampling rate >= 2 f_max
   Bits per sample = log2(quantisation levels)
   Bit rate = sampling rate × bits per sample
   ```
   - A 4 kHz voice signal at 8 bits per sample gives 64 kbps.

   Delay
   ```
   Transmission delay = size / bandwidth
   Propagation delay  = distance / speed
   Latency = transmission + propagation + queuing + processing
   ```

   Transmission impairments to name in theory parts
   - Attenuation (loss of strength, cured by repeaters), distortion (shape change, cured by equalisers) and noise (thermal, intermodulation, crosstalk, impulse).

   Line coding and modulation
   - NRZ, RZ, Manchester and Differential Manchester for baseband; ASK, FSK, PSK, QPSK and QAM for passband. Manchester is self-clocking but needs twice the bandwidth. <!-- verify -->

4. **10Mbps bandwidth, average packet length 1500 bytes what is maximum packet arrival rate support without causing congestion.** *[Bangladesh Satellite Company Limited Assistant Engineer (CSE) 23.08.2025 compact it 1430 (ET: BUET)]*

   Answer:

   Given
   - Bandwidth = 10 Mbps = 10,000,000 bits per second
   - Average packet length = 1500 bytes

   Step 1 — convert the packet length to bits
   ```
   1500 bytes × 8 = 12,000 bits per packet
   ```

   Step 2 — maximum packet arrival rate
   ```
   Rate = bandwidth / packet size in bits
        = 10,000,000 / 12,000
        = 833.33 packets per second
   ```

   - Answer: about `833 packets per second`.

   Interpretation
   - At exactly this rate the link is 100 percent utilised, so any burst causes queuing and eventually loss. Real networks are engineered to stay well below full utilisation — typically 70 percent — so a practical working figure would be around 580 packets per second.
   - Note that this is the maximum the `link` can carry. Real Ethernet also adds framing overhead: the 1500-byte payload becomes a 1538-byte frame once the header, FCS, preamble and interframe gap are counted, which reduces the true maximum to about 812 packets per second.
   - If the packets were smaller the packet rate would rise but the useful data rate would fall, because header overhead would take a larger share.

5. **What is Total Latency for a 3-kbyte message (an e-mail) if the bandwidth of the network is 1Gbps? Assume that the distance between the sender and the receiver is 300\text{ km} and that light travels at 2 \times 10^8\text{ m/s}. Round Trip Time 50ms Queuing Time 5ms?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1320 (ET: DU)]*

   Answer: Total latency is the sum of the four delay components.

   ```
   Latency = transmission time + propagation time + queuing time + processing time
   ```

   Given
   - Message size = 3 kbyte = 3000 bytes = 24,000 bits
   - Bandwidth = 1 Gbps = 10^9 bps
   - Distance = 300 km = 300,000 m
   - Propagation speed = 2 × 10^8 m/s
   - Queuing time = 5 ms
   - Round trip time = 50 ms

   Step 1 — transmission time
   ```
   = message size / bandwidth
   = 24,000 / 1,000,000,000
   = 24 × 10^-6 s = 0.024 ms
   ```

   Step 2 — propagation time
   ```
   = distance / speed
   = 300,000 / (2 × 10^8)
   = 1.5 × 10^-3 s = 1.5 ms
   ```

   Step 3 — queuing time
   ```
   = 5 ms (given)
   ```

   Step 4 — one-way total latency
   ```
   Latency = 0.024 + 1.5 + 5
           = 6.524 ms
   ```

   | Component | Value | Share |
   |---|---|---|
   | Transmission time | 0.024 ms | 0.4 % |
   | Propagation time | 1.5 ms | 23 % |
   | Queuing time | 5 ms | 76.6 % |
   | `Total (one way)` | `6.524 ms` | |

   If the 50 ms round trip time is included
   - Where the transfer requires a handshake or an acknowledgement before it completes, the RTT is added:
   ```
   Total = 6.524 + 50 = 56.524 ms
   ```

   Point worth noting
   - The transmission time is negligible here — only 0.024 ms out of 6.5 ms. On a fast link, latency is dominated by propagation and queuing, not by bandwidth. Buying more bandwidth would barely change this figure; reducing queuing or shortening the path would.

6. **Differentiate the following terms in tabular form:** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 300 (ET: BIBM)]*
   * **A. CSMA/CD and CSMA/CA.**
   * **B. Optical Communication and Satellite Communication.**
   * **C. Parity bit check, CRC and Checksum.**

   Answer:

   A. CSMA/CD vs CSMA/CA

   | Point | CSMA/CD | CSMA/CA |
   |---|---|---|
   | Full form | Carrier Sense Multiple Access with Collision Detection | ... with Collision Avoidance |
   | Approach | Detects a collision after it happens | Tries to prevent a collision before it happens |
   | Medium | Wired Ethernet | Wireless (Wi-Fi) |
   | Standard | IEEE 802.3 | IEEE 802.11 |
   | Listens while sending | Yes — that is how it detects a collision | No; a radio cannot hear while transmitting |
   | On collision | Sends a jam signal, then binary exponential backoff | Collision is not detectable; loss is inferred from a missing ACK |
   | Extra mechanism | None needed | RTS/CTS, DIFS wait, random backoff before sending, NAV |
   | Acknowledgement | None at the MAC layer | Every frame is acknowledged |
   | Efficiency | Higher | Lower, because of the extra waiting and handshaking |
   | Hidden terminal | Not an issue on a cable | A real problem; solved by RTS/CTS |
   | Status | Obsolete on full-duplex switched links | In active use |

   B. Optical communication vs satellite communication

   | Point | Optical (fibre) | Satellite |
   |---|---|---|
   | Medium | Glass fibre, guided | Free space, unguided microwave |
   | Bandwidth | Terabits per fibre with WDM | Hundreds of Mbps to a few Gbps per transponder |
   | Latency | Very low, about 5 µs per km | Very high for GEO — about 250 ms one way; LEO much less |
   | Coverage | Point to point along the cable route | Vast area, including oceans and remote regions |
   | Installation | Trenching or submarine laying; slow and costly | Launch cost is enormous but coverage is instant once in orbit |
   | Weather | Unaffected | Rain fade, atmospheric absorption |
   | Security | Very hard to tap | Broadcast signal, easier to intercept; needs encryption |
   | Error rate | Extremely low | Higher |
   | Cost per bit | Very low once installed | High |
   | Best for | Backbones, submarine links, metro and campus networks | Remote areas, ships and aircraft, broadcasting, disaster recovery |

   C. Parity bit, CRC and checksum

   | Point | Parity bit | Checksum | CRC |
   |---|---|---|---|
   | Method | Add one bit so the total number of 1s is even or odd | Add the data words and send the complement of the sum | Divide the data by a generator polynomial, modulo 2, and send the remainder |
   | Bits added | 1 | 8, 16 or 32 | 8, 16 or 32 |
   | Detects | Any odd number of bit errors | Most single and multiple errors | All single and double errors, all odd numbers of errors, and all bursts shorter than the CRC |
   | Misses | Any even number of errors | Errors that cancel out, and reordered words | Only a tiny fraction of long bursts |
   | Complexity | Trivial | Simple addition | Polynomial division, but easy in hardware |
   | Speed | Fastest | Fast | Fast in hardware, slower in software |
   | Strength | Weakest | Medium | Strongest |
   | Used by | Memory, simple serial links | IP, TCP and UDP headers | Ethernet FCS, HDLC, USB, ZIP, PNG |

   - The pattern: parity is cheap but weak; checksum is a reasonable compromise done in software; CRC is the strong choice and is implemented in hardware, which is why every link layer uses it.

7. **Two math from data communication.** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 405 (ET: N/A)]*

   Answer: The two problems were not printed, so the two most frequently set data-communication problems are worked in full.

   Problem type 1 — channel capacity

   Noiseless channel (Nyquist)
   ```
   C = 2 B log2(L)
   ```
   - Example: B = 3 kHz with 4 signal levels.
   ```
   C = 2 × 3000 × log2(4) = 2 × 3000 × 2 = 12,000 bps
   ```
   - Reverse form, finding the number of levels: to send 265 kbps over 20 kHz,
   ```
   log2(L) = 265,000 / (2 × 20,000) = 6.625 -> L = 98.7 -> use 128 levels
   ```

   Noisy channel (Shannon)
   ```
   C = B log2(1 + SNR)
   ```
   - Example: B = 3000 Hz, SNR = 3162.
   ```
   C = 3000 × log2(3163) = 3000 × 11.63 = 34,881 bps
   ```
   - If the SNR is given in dB, convert first: SNR = 10^(dB/10).

   Problem type 2 — latency and throughput
   ```
   Transmission delay = size / bandwidth
   Propagation delay  = distance / speed (2 × 10^8 m/s)
   Latency = transmission + propagation + queuing + processing
   ```
   - Example: a 3000-byte message on a 1 Gbps link over 300 km with 5 ms queuing.
   ```
   Transmission = 24,000 / 10^9 = 0.024 ms
   Propagation  = 300,000 / (2 × 10^8) = 1.5 ms
   Total        = 0.024 + 1.5 + 5 = 6.524 ms
   ```

   Other common types
   - Packet rate: 10 Mbps with 1500-byte packets gives 10,000,000 ÷ 12,000 = 833 packets per second.
   - CRC: data 11100 with generator 1001 gives remainder 111, so 11100111 is sent.
   - Bit rate from modulation: 16-QAM at 1000 baud gives 1000 × 4 = 4000 bps.
   - PCM: a 4 kHz voice signal, 8000 samples/s at 8 bits gives 64 kbps. <!-- verify -->

8. **(গ) Data communication-এর সাপেক্ষে bandwidth এবং troughput এর সংজ্ঞা লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer: (Answered in English, as required for IT topics.)

   Bandwidth
   - The maximum data-carrying capacity of a communication channel — the theoretical ceiling.
   - Digital bandwidth is measured in bits per second (bps, Mbps, Gbps); analogue bandwidth is measured in hertz, as the range of frequencies the channel can pass.
   - It is a fixed property of the medium and the technology: a Gigabit Ethernet port has 1000 Mbps of bandwidth whether it is busy or idle.
   - It can be increased only by upgrading the link — better cable, faster hardware, more spectrum.

   Throughput
   - The data rate actually achieved on that channel, measured over a real transfer.
   - It is always lower than the bandwidth, and it varies from moment to moment.
   - Reduced by protocol overhead (Ethernet, IP and TCP headers), congestion and queuing, errors and retransmissions, the slowest link on the path, and the processing limits of the end devices.
   - Example: a 100 Mbps link may deliver 85 Mbps in practice.

   | Point | Bandwidth | Throughput |
   |---|---|---|
   | Nature | Theoretical maximum | Practical measured value |
   | Stability | Fixed | Varies continuously |
   | Relation | Always the higher | Always lower |
   | Improved by | Upgrading the link | Reducing congestion, errors and overhead |

   - A third term, `goodput`, is narrower still: only the useful application data delivered, excluding headers and retransmissions.
   - Analogy: bandwidth is the number of lanes on a road; throughput is how many vehicles actually complete the journey in an hour.

9. **CRC is a redundancy error technique used to determine the error. Suppose the original data is 11100 and divisor is 1001.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 493 (ET: N/A)]*

   Answer: CRC works by modulo-2 division. The divisor 1001 has 4 bits, so its degree is 3, and 3 zeros are appended to the data.

   Given
   - Data = 11100, Divisor (generator) = 1001

   Step 1 — append 3 zeros
   ```
   Dividend = 11100 000 = 11100000
   ```

   Step 2 — modulo-2 division (XOR at every step, no borrowing)
   ```
           1 1 1 1 1        <- quotient (discarded)
         -------------
   1001 ) 1 1 1 0 0 0 0 0
          1 0 0 1
          -------
          0 1 1 1 0 0 0 0
            1 0 0 1
            -------
          0 0 1 1 1 0 0 0
              1 0 0 1
              -------
          0 0 0 1 1 1 0 0
                1 0 0 1
                -------
          0 0 0 0 1 1 1 0
                  1 0 0 1
                  -------
          0 0 0 0 0 1 1 1
                    -----
                     1 1 1   <- REMAINDER (3 bits)
   ```

   Step 3 — form the codeword
   ```
   Transmitted frame = data + remainder = 11100 + 111 = 11100111
   ```

   Step 4 — verification at the receiver
   - The receiver divides the received 11100111 by 1001. If the remainder is `000`, no error is detected and the 3 CRC bits are stripped off. A non-zero remainder means the frame is corrupt, so it is discarded and retransmitted.

   Answer

   | Item | Value |
   |---|---|
   | Data | 11100 |
   | Divisor | 1001 |
   | Appended zeros | 000 |
   | Remainder (CRC) | `111` |
   | Transmitted codeword | `11100111` |

   - Points to remember: the number of appended zeros is always (length of divisor − 1); subtraction here is XOR, with no borrowing; the quotient is discarded, since only the remainder matters; and the remainder must be written with exactly that many bits, padding with leading zeros if necessary.

10. **A telephone line normally has a bandwidth of 3000 Hz (300 to 3300 Hz) assigned for data communication. The SNR is usually 3162. What will be the capacity for this channel?** *[Combined Bank Assistant Programmer 09.06.2023 compact it 497 (ET: N/A)]*

    Answer: The channel is noisy, so Shannon's capacity formula applies.

    Given
    - Bandwidth B = 3300 − 300 = 3000 Hz
    - SNR = 3162

    Formula
    ```
    C = B × log2(1 + SNR)
    ```

    Calculation
    ```
    C = 3000 × log2(1 + 3162)
      = 3000 × log2(3163)
      = 3000 × 11.627
      = 34,881 bps
    ```

    - Answer: approximately `34,880 bps`, usually quoted as about `34.86 kbps`.

    Notes
    - SNR = 3162 corresponds to 10 log10(3162) ≈ 35 dB, a typical figure for a good telephone circuit.
    - This is the theoretical ceiling, which is why dial-up modems plateaued around 33.6 kbps for symmetric transmission. The 56 kbps modems worked only in the downstream direction, where one end connected digitally to the telephone network and avoided one analogue-to-digital conversion.
    - Shannon gives only the capacity; it says nothing about how to achieve it. Nyquist supplies the number of levels: 2 × 3000 × log2(L) = 34,881 gives log2(L) ≈ 5.8, so roughly 64 signal levels would be needed.

11. **Which technique is used for binary division check in network?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

    Answer: The technique that uses binary division to check for errors is `CRC — Cyclic Redundancy Check`.

    How it works
    - The sender appends (n − 1) zeros to the data, where n is the length of the agreed generator polynomial (divisor).
    - It divides the result by the generator using `modulo-2 division`, in which subtraction is a simple XOR with no borrowing.
    - The remainder — the CRC or FCS — is appended to the data and transmitted.
    - The receiver divides the whole received frame by the same generator. A remainder of `zero` means no error was detected; anything else means the frame is corrupt and it is discarded.

    Example
    ```
    Data 11100, generator 1001
    Append 3 zeros -> 11100000
    Divide by 1001 modulo 2 -> remainder 111
    Transmit 11100111
    ```

    Why CRC is used everywhere
    - It detects all single-bit errors, all double-bit errors with a suitable generator, all odd numbers of errors, and all burst errors shorter than the CRC length. Real transmission errors arrive in bursts, so this last property is decisive.
    - It is extremely cheap to implement in hardware with a shift register and XOR gates, so it runs at line rate.

    Common generators

    | Name | Polynomial | Used by |
    |---|---|---|
    | CRC-8 | x^8 + x^2 + x + 1 | ATM header |
    | CRC-16 | x^16 + x^15 + x^2 + 1 | Modbus, USB, HDLC |
    | CRC-CCITT | x^16 + x^12 + x^5 + 1 | X.25, Bluetooth |
    | CRC-32 | x^32 + x^26 + … + 1 | Ethernet FCS, ZIP, PNG |

    - Note: CRC only `detects` errors, it cannot correct them. Correction requires Hamming code or another forward error correction scheme.

12. **Explain parity method for error detection. Write down the bit strings of “Delta” using ASCII.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 (ET: BIBM)]*

    Answer:

    Parity method for error detection
    - One extra bit, the parity bit, is added to each data unit so that the total number of 1s becomes even (even parity) or odd (odd parity), according to the scheme agreed by both ends.
    - The sender counts the 1s in the data and sets the parity bit accordingly. The receiver counts the 1s in the whole received unit including the parity bit; if the count does not match the agreed rule, an error is detected and the unit is discarded.

    Example with even parity
    ```
    Data 1000100 has two 1s -> already even -> parity bit 0 -> 01000100
    Data 1100001 has three 1s -> odd -> parity bit 1 -> 11100001
    ```

    Strengths and weaknesses
    - It detects any `odd` number of bit errors — one, three, five and so on.
    - It cannot detect an `even` number of errors, because two flipped bits leave the count's parity unchanged. This is its fundamental weakness.
    - It cannot locate or correct an error, only report that one exists.
    - Two-dimensional parity (a parity bit per row and per column) improves this: it detects most multiple errors and can correct a single-bit error by locating the intersection of the failing row and column.

    ASCII bit strings for "Delta" (7-bit ASCII, with an even parity bit added on the left)

    | Character | Decimal | 7-bit ASCII | Number of 1s | Even parity bit | 8-bit string |
    |---|---|---|---|---|---|
    | D | 68 | 1000100 | 2 (even) | 0 | `01000100` |
    | e | 101 | 1100101 | 4 (even) | 0 | `01100101` |
    | l | 108 | 1101100 | 4 (even) | 0 | `01101100` |
    | t | 116 | 1110100 | 4 (even) | 0 | `01110100` |
    | a | 97 | 1100001 | 3 (odd) | 1 | `11100001` |

    Complete transmitted bit stream
    ```
    01000100 01100101 01101100 01110100 11100001
    ```

    - Without the parity bit, the plain 7-bit ASCII for "Delta" is:
    ```
    1000100 1100101 1101100 1110100 1100001
    ```
    - Note the case sensitivity: uppercase D is 68 while lowercase d would be 100, a difference of exactly 32 in ASCII.

13. **An end system sends 50 packets per second using the User Datagram Protocol (UDP) over a full duplex 100 Mbps ethernet LAN connection. Each packet consists 1500B of ethernet frame payload data. What is the throughput, when measured at the UDP layer?** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 718 (ET: N/A)]*

    Answer:

    Given
    - 50 packets per second
    - Each packet carries 1500 bytes of `Ethernet frame payload`
    - Protocol: UDP over IPv4, on a 100 Mbps full-duplex link

    Step 1 — work out what the 1500 bytes contains
    - The Ethernet payload holds the complete IP packet.
    ```
    Ethernet payload   = 1500 bytes
    − IP header        =   20 bytes
    − UDP header       =    8 bytes
    -----------------------------------
    = UDP payload (application data) = 1472 bytes
    ```

    Step 2 — throughput at the UDP layer
    ```
    Throughput = 50 packets/s × 1472 bytes × 8 bits
               = 50 × 11,776 bits
               = 588,800 bits per second
               = 588.8 kbps
    ```

    - Answer: `588.8 kbps` (0.5888 Mbps).

    Comparison at each layer

    | Measured at | Bytes per packet | Throughput |
    |---|---|---|
    | Application / UDP payload | 1472 | 588.8 kbps |
    | UDP datagram (payload + 8) | 1480 | 592.0 kbps |
    | IP packet (Ethernet payload) | 1500 | 600.0 kbps |
    | Ethernet frame (+18 header and FCS) | 1518 | 607.2 kbps |
    | Wire, including preamble and IFG | 1538 | 615.2 kbps |

    - The point of the question is that "throughput" depends entirely on the layer at which it is measured; the useful application data rate is the lowest of these figures.
    - Note also that 588.8 kbps is less than 0.6 percent of the 100 Mbps link, so the link is nowhere near saturated.

14. **The message 11001001 is to be transmitted using the CRC polynomial x^3+1 to protect it from the errors. Now find out the message that should be transmitted.** *[BAUST Assistant Programmer 2021 compact it 917-918 (ET: N/A)]*

    Answer: The generator polynomial x^3 + 1 must first be written as a bit string.

    Step 1 — convert the polynomial to binary
    ```
    x^3 + 1  ->  1·x^3 + 0·x^2 + 0·x^1 + 1  ->  1001
    ```
    - The generator has 4 bits, so its degree is 3, and `3 zeros` are appended to the message.

    Given
    - Message = 11001001, Divisor = 1001

    Step 2 — append 3 zeros
    ```
    Dividend = 11001001 000 = 11001001000
    ```

    Step 3 — modulo-2 division (XOR, no borrowing)
    ```
    1001 ) 1 1 0 0 1 0 0 1 0 0 0
           1 0 0 1
           -------
           0 1 0 1 1 0 0 1 0 0 0
             1 0 0 1
             -------
           0 0 0 1 0 0 0 1 0 0 0
                 1 0 0 1
                 -------
           0 0 0 0 0 0 1 1 0 0 0
                       1 0 0 1
                       -------
           0 0 0 0 0 0 0 1 0 1 0
                         1 0 0 1
                         -------
           0 0 0 0 0 0 0 0 0 1 1
                           -----
                             0 1 1   <- REMAINDER (3 bits)
    ```
    - Note that a step is skipped wherever the leading bit is already 0 — the divisor is only XORed when the current leading bit is 1.

    Step 4 — form the transmitted frame
    ```
    Transmitted = message + remainder
                = 11001001 + 011
                = 11001001011
    ```

    Answer

    | Item | Value |
    |---|---|
    | Message | 11001001 |
    | Generator polynomial | x^3 + 1 |
    | Divisor in binary | 1001 |
    | Zeros appended | 3 |
    | CRC remainder | `011` |
    | Message to be transmitted | `11001001011` |

    Step 5 — check at the receiver
    - The receiver divides 11001001011 by 1001. The remainder is `000`, confirming no error is detected, and the last 3 bits are removed to recover the original message 11001001.

    - Rules to remember: the number of appended zeros equals the degree of the generator; subtraction is XOR; the quotient is discarded; and the remainder must be padded to exactly the degree of the generator — here 3 bits, so 11 is written as `011`.

## Network Topologies (14)

1. **What is Star vs Mesh Topology?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1449 (ET: N/A)]*

   Answer:

   Star topology
   - Every device connects by its own cable to a central device — a switch or hub. All traffic passes through that centre.
   ```
           PC
            |
     PC --[SWITCH]-- PC
            |
           PC
   ```
   - Links for n devices: `n`
   - Advantages: easy to install and extend; one cable failure affects only one device; faults are easy to isolate; central management; excellent performance with a switch.
   - Disadvantages: the central device is a single point of failure — if the switch dies, the whole network stops; more cable than a bus; the switch adds cost.

   Mesh topology
   - Every device has a direct dedicated link to every other device (full mesh).
   ```
        A -------- B
        | \      / |
        |   \  /   |
        |    \/    |
        |    /\    |
        |  /    \  |
        D -------- C
   ```
   - Links for n devices: `n(n − 1) / 2`; each device needs n − 1 ports.
   - Advantages: highest reliability, since traffic reroutes around any failed link; no traffic congestion, because every link is dedicated; excellent privacy and security; easy fault identification.
   - Disadvantages: enormous cabling and port cost, which grows quadratically; very difficult to install and maintain; impractical beyond a small number of nodes.

   Comparison

   | Point | Star | Mesh |
   |---|---|---|
   | Links for n devices | n | n(n − 1)/2 |
   | Ports per device | 1 | n − 1 |
   | Cost | Low | Very high |
   | Installation | Easy | Very difficult |
   | Fault tolerance | Poor — central device is critical | Excellent — many alternative paths |
   | Congestion | Possible at the centre | None; links are dedicated |
   | Scalability | Excellent | Poor |
   | Typical use | Every modern LAN | WAN backbones, critical links, wireless mesh |

   - Example for n = 6: star needs 6 links, mesh needs 15. For n = 20: star needs 20, mesh needs 190. That growth is why full mesh is reserved for a handful of critical nodes, usually as a `partial mesh`.

2. **(b) Define network topology and classify it.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1446 (ET: N/A)]*

   Answer:

   Definition
   - Network topology is the arrangement — the layout — of the nodes and links in a network. It describes how devices are physically connected and how data logically flows between them.
   - Two kinds are distinguished:
     - `Physical topology` — how the cables are actually laid out.
     - `Logical topology` — the path the data actually takes. These can differ: a 10BASE-T network is physically a star (all cables go to a hub) but logically a bus (every station hears every frame).

   Classification

   1. Bus
   - All devices attach to one shared backbone cable, terminated at both ends.
   - Links: n drop cables plus one backbone. Cheapest and simplest, but a break in the backbone brings down the whole network, and performance collapses as devices are added.

   2. Star
   - Every device has its own cable to a central switch or hub.
   - Links: n. Easy to install and troubleshoot; one cable failure affects one device only; but the central device is a single point of failure. This is the standard modern LAN topology.

   3. Ring
   - Each device connects to exactly two neighbours, forming a closed loop. Data travels in one direction, often controlled by a token.
   - Links: n. No collisions and predictable performance, but a single break stops everything unless a dual ring is used, as in FDDI.

   4. Mesh
   - Every device is directly connected to every other (full mesh).
   - Links: n(n − 1)/2. Highest reliability and no congestion, but the cost grows quadratically. A `partial mesh`, connecting only the important nodes, is the practical compromise.

   5. Tree (hierarchical)
   - A hierarchy of star networks connected to a common backbone. This is the standard structured-cabling model for a multi-floor building.
   - Scalable and easy to manage, but the root node is a critical point of failure.

   6. Hybrid
   - Any combination of the above — for example star-bus or star-ring. Most real networks are hybrids: star at each floor, joined by a fibre backbone.

   Summary table

   | Topology | Links for n devices | Cost | Reliability | Common use |
   |---|---|---|---|---|
   | Bus | 1 backbone + n taps | Lowest | Poor | Obsolete |
   | Star | n | Low | Medium | Every modern LAN |
   | Ring | n | Medium | Poor (single ring) | Legacy, metro fibre rings |
   | Mesh | n(n − 1)/2 | Highest | Excellent | WAN backbones, wireless mesh |
   | Tree | n − 1 | Medium | Medium | Campus and multi-storey buildings |
   | Hybrid | Varies | Varies | Good | Almost all real networks |

3. **Write 4 topology name?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

   Answer: Four network topologies are:

   1. `Bus topology` — all devices share one backbone cable, terminated at both ends.
   2. `Star topology` — every device connects to a central switch or hub.
   3. `Ring topology` — each device connects to two neighbours, forming a closed loop.
   4. `Mesh topology` — every device has a direct link to every other device.

   ```
   BUS                    STAR                RING              MESH
                                                                A----B
   --+----+----+--         PC                 A---B             |\  /|
     |    |    |            |                /     \            | \/ |
    PC   PC   PC      PC--[SW]--PC          D-------C           | /\ |
                             |                                  |/  \|
                            PC                                  D----C
   ```

   - Two more are commonly listed: `Tree` (a hierarchy of stars on a backbone) and `Hybrid` (any combination, which is what most real networks are).
   - Links needed for n devices: bus = 1 backbone, star = n, ring = n, mesh = n(n − 1)/2.

4. **What is Network Topology? Distinguish between Bus, Ring, Tree and Star topology. Discuss how the Bus topology works.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 530 (ET: MIST)]*

   Answer:

   What is network topology
   - The arrangement of nodes and links in a network — how devices are connected physically and how data flows logically between them. Physical and logical topology can differ: 10BASE-T is physically a star but logically a bus.

   Distinction between the four

   | Point | Bus | Ring | Star | Tree |
   |---|---|---|---|---|
   | Structure | One shared backbone cable | Closed loop of point-to-point links | All devices to one central device | Hierarchy of stars on a backbone |
   | Links for n devices | 1 backbone + n taps | n | n | n − 1 |
   | Central device | None | None | Switch or hub | Root switch plus branch switches |
   | Data flow | Broadcast along the bus in both directions | Unidirectional around the loop | Through the central device | Down and up the hierarchy |
   | Effect of one cable break | Whole network fails | Whole ring fails (single ring) | One device only | The branch below the break |
   | Effect of central failure | Not applicable | Not applicable | Whole network fails | That branch, or all of it at the root |
   | Collisions | Yes, uses CSMA/CD | None; token controlled | None on a switch | None on switches |
   | Adding a device | Easy but disruptive | Disrupts the ring | Very easy | Easy |
   | Cost | Lowest | Medium | Low | Medium |
   | Troubleshooting | Very difficult | Difficult | Easy | Moderate |
   | Performance under load | Degrades badly | Predictable | Excellent | Good |
   | Status | Obsolete | Legacy, metro fibre rings | Standard LAN | Standard for campuses |

   How bus topology works
   ```
      Terminator                                        Terminator
          |                                                  |
          +----+---------+---------+---------+---------+-----+
               |         |         |         |         |
              PC1       PC2       PC3       PC4       PC5
   ```
   - Step 1 — a station wanting to send first listens to the backbone (carrier sense). If it is busy, it waits.
   - Step 2 — when the line is idle, it transmits. The signal travels in `both directions` along the backbone and reaches every station.
   - Step 3 — every station reads the destination MAC address in the frame. Only the intended recipient copies it; all others discard it. This is why bus topology has no privacy.
   - Step 4 — if two stations transmit at once, the signals collide. Each detects the collision, sends a jam signal, waits a random backoff time, and retries. This is `CSMA/CD`.
   - Step 5 — terminators (50 ohm) at both ends absorb the signal so it does not reflect back and interfere. A missing terminator breaks the whole segment.

   - Weaknesses that killed it: one break disables everything, faults are very hard to locate, only one station can transmit at a time so bandwidth is shared, and performance collapses as stations are added.

5. **What is Personal Area Network? What is needed component and explain?** *[Mongla Port Authority Assistant Programmer 2023 compact it 572 (ET: N/A)]*

   Answer:

   What is a Personal Area Network
   - A PAN is the smallest category of network, covering the space immediately around one person — typically within about 10 metres.
   - It connects an individual's own devices to each other, or to a nearby network, for personal use.
   - It can be wired (USB, FireWire) or wireless (WPAN — Bluetooth, Zigbee, NFC, infrared).

   Components needed

   1. Devices (nodes)
   - The personal devices being connected: smartphone, laptop, tablet, smartwatch, wireless earphones, fitness band, wireless keyboard and mouse, printer, health sensors.

   2. Wireless adapter or transceiver
   - Each device needs a radio for the chosen technology — a Bluetooth chip, a Zigbee module or an NFC coil. Without a common radio standard the devices cannot connect.

   3. Communication technology (the protocol)
   - `Bluetooth` (IEEE 802.15.1) — the most common, 2.4 GHz, about 10 m, 1–3 Mbps; BLE for low-power sensors.
   - `Zigbee` (IEEE 802.15.4) — very low power, mesh capable, used in home automation.
   - `NFC` — a few centimetres, used for payments and pairing.
   - `Infrared (IrDA)` — line of sight, short range, used by remote controls.
   - `USB / FireWire` — the wired equivalents.

   4. Master or coordinator device
   - One device acts as the master. In Bluetooth a `piconet` has one master and up to seven active slaves; several piconets form a `scatternet`. A smartphone usually plays the master role.

   5. Pairing and security
   - Devices must be paired, which authenticates them and establishes an encryption key. Bluetooth uses PIN or Secure Simple Pairing, and encrypts the link afterwards. Without this, anyone in range could connect.

   6. Software and drivers
   - The protocol stack and profiles on each device — for example the Bluetooth A2DP profile for stereo audio, HID for keyboards, and companion apps for wearables.

   Characteristics
   - Range about 10 m, low data rate, very low power consumption, low cost, easy ad hoc setup, and no infrastructure required.
   - Uses: hands-free calling, wireless audio, file transfer between phones, wearable health monitoring, contactless payment, and connecting IoT sensors to a phone.

6. **What is Topology in data communication? What are differences between Bus, Ring, Tree and Star topology? Purpose of IEEE 802.11 committee.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 512 (ET: MIST)]*

   Answer:

   (a) What is topology in data communication
   - Topology is the arrangement of nodes and links in a network — how devices are connected and how data flows between them.
   - Physical topology describes the actual cable layout; logical topology describes the path the data takes. They can differ, as in 10BASE-T, which is physically a star and logically a bus.

   (b) Differences between Bus, Ring, Tree and Star

   | Point | Bus | Ring | Tree | Star |
   |---|---|---|---|---|
   | Structure | One shared backbone | Closed loop | Hierarchy of stars | All devices to one centre |
   | Links for n devices | 1 backbone + n taps | n | n − 1 | n |
   | Central device | None | None | Root switch | Switch or hub |
   | Data flow | Broadcast both ways | One direction round the loop | Down and up the hierarchy | Through the centre |
   | One cable break | Whole network down | Whole ring down | Branch below it down | One device only |
   | Central failure | N/A | N/A | That branch or all | Whole network down |
   | Collisions | Yes (CSMA/CD) | None, token based | None on switches | None on a switch |
   | Expansion | Limited | Disruptive | Very easy | Very easy |
   | Troubleshooting | Very hard | Hard | Moderate | Easy |
   | Cost | Lowest | Medium | Medium | Low |
   | Status | Obsolete | Legacy | Standard for campuses | Standard for LANs |

   (c) Purpose of the IEEE 802.11 committee
   - IEEE 802.11 is the working group responsible for standardising `Wireless LAN` — the family of technologies marketed as Wi-Fi.
   - Its purpose is to define the physical layer and the MAC sub-layer for wireless local area networks, so that equipment from different manufacturers interoperates.
   - Specifically it defines: the radio frequencies and channels used (2.4 GHz, 5 GHz, 6 GHz), the modulation schemes, the `CSMA/CA` access method with RTS/CTS, frame formats, association and roaming procedures, power-saving modes, and security (WEP, then WPA, WPA2 and WPA3 under 802.11i).

   Main amendments

   | Standard | Year | Band | Maximum rate |
   |---|---|---|---|
   | 802.11b | 1999 | 2.4 GHz | 11 Mbps |
   | 802.11a | 1999 | 5 GHz | 54 Mbps |
   | 802.11g | 2003 | 2.4 GHz | 54 Mbps |
   | 802.11n (Wi-Fi 4) | 2009 | 2.4/5 GHz | 600 Mbps |
   | 802.11ac (Wi-Fi 5) | 2013 | 5 GHz | 3.5 Gbps |
   | 802.11ax (Wi-Fi 6/6E) | 2019 | 2.4/5/6 GHz | 9.6 Gbps |
   | 802.11be (Wi-Fi 7) | 2024 | 2.4/5/6 GHz | 46 Gbps |

7. **(খ) একটি নেটওয়ার্কে n সংখ্যক ডিভাইসের জন্যে Bus, Mesh এবং Star টপোলজিতে তারের লিংকগুলোর সংখ্যা কত?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 628 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Number of cable links required for n devices.

   | Topology | Number of links | Ports per device |
   |---|---|---|
   | Bus | `1 backbone cable` plus n drop connections (often counted simply as `n` taps) | 1 |
   | Mesh (full) | `n(n − 1) / 2` | n − 1 |
   | Star | `n` | 1 |

   Derivation for mesh
   - Each device must connect to every other device, so each has n − 1 links.
   - Counting this way counts every link twice, once from each end.
   ```
   Number of links = n(n − 1) / 2
   ```

   Worked values

   | n | Bus | Star | Mesh |
   |---|---|---|---|
   | 4 | 1 backbone + 4 taps | 4 | 6 |
   | 5 | 1 backbone + 5 taps | 5 | 10 |
   | 6 | 1 backbone + 6 taps | 6 | 15 |
   | 10 | 1 backbone + 10 taps | 10 | 45 |
   | 20 | 1 backbone + 20 taps | 20 | 190 |
   | 100 | 1 backbone + 100 taps | 100 | 4950 |

   - The point the table makes: star and bus grow `linearly` with n, while mesh grows `quadratically`. That is exactly why full mesh is never used for a LAN and is reserved for a small number of critical WAN links, usually as a partial mesh.
   - Related figures: ring needs n links; tree needs n − 1 links.

8. **What is network topology? Write the name all different topology used in computer networking with example, diagram and their activities.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 673 (ET: N/A)]*

   Answer:

   What is network topology
   - The arrangement of nodes and links in a network — how devices are connected physically and how data flows logically between them.

   The topologies, with diagrams and how they work

   1. Bus topology
   ```
   Terminator --+----+----+----+----+-- Terminator
                |    |    |    |    |
               PC1  PC2  PC3  PC4  PC5
   ```
   - All devices share one backbone cable, terminated at both ends. A transmitted signal travels both ways and reaches every station; only the addressed one keeps it.
   - Access is controlled by CSMA/CD, so collisions occur and are resolved by backoff.
   - Example: 10BASE2 and 10BASE5 Ethernet.
   - Advantages: cheapest, least cable, easy to extend. Disadvantages: one break kills the whole network, faults are very hard to locate, and bandwidth is shared.

   2. Star topology
   ```
           PC
            |
     PC --[SWITCH]-- PC
            |
           PC
   ```
   - Every device has its own cable to a central switch or hub; all traffic passes through the centre.
   - With a switch, each port is its own collision domain and gets full bandwidth.
   - Example: every modern Ethernet LAN.
   - Advantages: easy to install, extend and troubleshoot; one cable fault affects only one device; central management. Disadvantage: the central device is a single point of failure.

   3. Ring topology
   ```
       A ----> B
       ^       |
       |       v
       D <---- C
   ```
   - Each device connects to exactly two neighbours in a closed loop. Data circulates in one direction, and a token grants the right to transmit, so there are no collisions.
   - Example: Token Ring (802.5), FDDI, SONET metro rings.
   - Advantages: no collisions, predictable performance under load, equal access for all. Disadvantages: a single break stops everything unless a dual counter-rotating ring is used, and adding a device disrupts the ring.

   4. Mesh topology
   ```
        A -------- B
        | \      / |
        |   \  /   |
        |    \/    |
        |    /\    |
        D -------- C
   ```
   - Every device links directly to every other. Links = n(n − 1)/2.
   - Example: internet backbone links, wireless mesh networks.
   - Advantages: highest reliability, no congestion, excellent security, easy fault isolation. Disadvantages: cost and cabling grow quadratically; impractical beyond a few nodes, so partial mesh is used instead.

   5. Tree (hierarchical) topology
   ```
               [ROOT SWITCH]
               /            \
        [SWITCH]            [SWITCH]
        /   |   \            /    \
      PC   PC   PC         PC     PC
   ```
   - A hierarchy of star networks joined to a common backbone. This is the structured-cabling model of a multi-floor building.
   - Advantages: highly scalable, easy to manage and expand, faults confined to a branch. Disadvantage: the root is critical, and heavy traffic concentrates on the backbone.

   6. Hybrid topology
   - Any combination of the above — star-bus, star-ring, and so on. Almost every real network is a hybrid: star at each floor, tree between floors, and mesh between sites.
   - Advantages: combines the strengths of each; flexible and scalable. Disadvantages: complex to design, and expensive.

   Summary

   | Topology | Links | Cost | Reliability | Scalability |
   |---|---|---|---|---|
   | Bus | n taps + backbone | Lowest | Poor | Poor |
   | Star | n | Low | Medium | Excellent |
   | Ring | n | Medium | Poor | Poor |
   | Mesh | n(n−1)/2 | Highest | Excellent | Poor |
   | Tree | n − 1 | Medium | Medium | Excellent |
   | Hybrid | Varies | Varies | Good | Excellent |

9. **Write down the types of topology.** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*

   Answer: The types of network topology are:

   1. `Bus` — all devices share one backbone cable, terminated at both ends. Links: 1 backbone plus n taps.
   2. `Star` — every device connects to a central switch or hub. Links: n.
   3. `Ring` — devices form a closed loop, each connected to two neighbours. Links: n.
   4. `Mesh` — every device links directly to every other. Links: n(n − 1)/2.
   5. `Tree (hierarchical)` — a hierarchy of stars joined to a backbone. Links: n − 1.
   6. `Hybrid` — any combination of the above; almost all real networks are hybrids.

   ```
   BUS              STAR              RING            MESH             TREE
   --+--+--+--       PC              A---B           A----B          [ROOT]
     |  |  |          |             /     \          |\  /|          /     \
    PC PC PC    PC--[SW]--PC       D-------C         | \/ |       [SW]    [SW]
                      |                              | /\ |        /|\     /\
                     PC                              D----C      PC PC PC PC PC
   ```

   - Two further distinctions: `physical` topology is how the cables are laid; `logical` topology is the path the data actually follows. A 10BASE-T network is physically a star but logically a bus.
   - The star is the standard for modern LANs, the tree for multi-storey buildings and campuses, and the mesh for critical WAN links.

10. **Write down the Disadvantages of Bus topology.** *[DMLC Assistant Teacher (ICT) 2021 compact it 825 (ET: N/A)]*

    Answer: Disadvantages of bus topology.

    - `Single point of total failure` — a break anywhere in the backbone cable splits the network and brings the entire segment down, not just one device. This is the most serious weakness.
    - `Very difficult to troubleshoot` — a fault could be anywhere along the cable, at any tap, or at either terminator. There is no link light to tell you which section is broken.
    - `Shared bandwidth` — only one station may transmit at a time, so the total capacity is divided among all devices. Adding devices slows everyone down.
    - `Collisions` — CSMA/CD means collisions increase sharply with the number of active stations, and performance collapses under load.
    - `Limited cable length and device count` — 185 m and 30 devices for 10BASE2; 500 m and 100 devices for 10BASE5. Signal attenuation sets these limits.
    - `Terminators are essential` — a missing or faulty 50-ohm terminator causes signal reflection that corrupts everything on the segment, and this is a common and confusing fault.
    - `No security or privacy` — every frame reaches every station, so any machine can capture all traffic simply by putting its NIC in promiscuous mode.
    - `Disruptive to extend` — adding a station usually means cutting into the backbone, which interrupts the whole network.
    - `No redundancy` — there is only one path, so there is no alternative route if the cable fails.
    - `Poor scalability` — the topology becomes unusable as the network grows.

    - These weaknesses, especially the whole-network failure and the impossibility of troubleshooting, are why bus topology is completely obsolete and has been replaced by the switched star.

11. **(b) Define network topologies with features.** *[National University Assistant Programmer 2020 compact it 977 (ET: DU)]*

    Answer:

    Definition
    - Network topology is the arrangement of nodes and links in a network — how devices are connected and how data flows between them.
    - `Physical topology` is the actual cable layout; `logical topology` is the route data takes. A 10BASE-T network is physically a star but logically a bus.

    The topologies with their features

    Bus
    - One shared backbone cable with terminators at both ends; every station taps into it.
    - Features: cheapest and least cabling; broadcast transmission reaching all stations; CSMA/CD access with collisions; a single break disables everything; very hard to troubleshoot; poor scalability; now obsolete.

    Star
    - Every device has its own cable to a central switch or hub.
    - Features: n links; easy installation and expansion; one cable fault affects only that device; excellent fault isolation and central management; dedicated bandwidth per port with a switch; but the central device is a single point of failure. This is the standard modern LAN.

    Ring
    - A closed loop in which each device connects to exactly two neighbours; data flows in one direction.
    - Features: n links; token-controlled access so there are no collisions; predictable, fair performance under heavy load; but one break stops the ring unless a dual counter-rotating ring is used; adding a device is disruptive.

    Mesh
    - Every device directly connected to every other.
    - Features: n(n − 1)/2 links and n − 1 ports per device; highest reliability with many alternative paths; dedicated links so no congestion; excellent privacy; easy fault identification; but the cost grows quadratically, so only partial mesh is practical at scale.

    Tree (hierarchical)
    - A hierarchy of star networks connected to a common backbone.
    - Features: n − 1 links; highly scalable; easy to manage and expand floor by floor; faults confined to a branch; but the root is critical and the backbone can become a bottleneck. This is the structured-cabling model.

    Hybrid
    - Any combination of the above.
    - Features: takes the strengths of each; very flexible and scalable; fault tolerant if designed with redundancy; but complex and expensive to design and maintain. Almost every real network is a hybrid.

    | Topology | Links | Cost | Reliability | Troubleshooting |
    |---|---|---|---|---|
    | Bus | backbone + n taps | Lowest | Poor | Very hard |
    | Star | n | Low | Medium | Easy |
    | Ring | n | Medium | Poor | Hard |
    | Mesh | n(n−1)/2 | Highest | Excellent | Easy |
    | Tree | n − 1 | Medium | Medium | Moderate |

12. **(d) List some various types of Topologies. What are the factors to choose a topology?** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1030 (ET: N/A)]*

    Answer:

    (a) Types of topology
    - `Bus` — one shared backbone cable with terminators at both ends.
    - `Star` — all devices connected to a central switch or hub.
    - `Ring` — a closed loop, each device connected to two neighbours.
    - `Mesh` — every device directly connected to every other; full or partial.
    - `Tree (hierarchical)` — a hierarchy of stars joined to a backbone.
    - `Hybrid` — any combination of the above.

    (b) Factors in choosing a topology

    - `Cost` — cabling, ports, switches and installation labour. Bus is cheapest, mesh by far the most expensive because links grow as n(n − 1)/2.
    - `Reliability and fault tolerance` — how much damage one failure causes. Mesh survives almost anything; a bus fails completely on one break.
    - `Scalability` — how easily devices and sites can be added. Star and tree scale well; bus and ring do not.
    - `Performance and traffic volume` — dedicated bandwidth per device (star with a switch, mesh) versus shared bandwidth (bus, ring).
    - `Number of devices and their distribution` — a handful of critical routers may justify a mesh; two hundred desks on four floors call for a tree of stars.
    - `Physical layout of the site` — building shape, distance between floors and buildings, existing ducts and cable trays. Cable length limits (100 m for UTP) often dictate where switches must sit.
    - `Ease of installation and maintenance` — how quickly it can be built, and how easily a fault can be located. Star is the clear winner here.
    - `Expandability and future growth` — spare ports and structured cabling so new users can be added without redesign.
    - `Security requirements` — a bus lets every station see all traffic; a switched star and VLANs confine it.
    - `Availability requirement` — if downtime is unacceptable, redundant links and a partial mesh core are needed, with protocols such as STP or VRRP.
    - `Type of cable and technology` — fibre for long backbone runs, UTP for the last 100 m, wireless where cabling is impossible.
    - `Skill and staffing` — a complex mesh or hybrid design needs trained administrators.

    - The usual outcome for an office: a `tree of switched stars` — a star at each floor, floors joined by a fibre backbone to a core switch, with a redundant second core link if availability matters.

13. **(খ) Bus and Ring টপোলজির মধ্যে কোনটি ভালো এবং কেন?** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1067 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Between bus and ring, `ring topology is better` overall, though each has its own strengths.

    Comparison

    | Point | Bus | Ring | Better |
    |---|---|---|---|
    | Collisions | Yes, CSMA/CD | None; token controlled | Ring |
    | Performance under heavy load | Collapses as collisions multiply | Stays predictable and fair | Ring |
    | Fair access | No; a busy station can dominate | Yes; the token circulates to everyone | Ring |
    | Signal strength | Attenuates along the shared cable | Each node regenerates the signal, so it can span longer distances | Ring |
    | Effect of one break | Entire network down | Entire ring down (single ring); a dual ring survives | Ring, if dual |
    | Cable required | Least | Slightly more | Bus |
    | Cost | Cheapest | Slightly higher | Bus |
    | Installation | Simplest | More complex | Bus |
    | Adding a device | Easy, but disrupts the segment | Must break the ring | Bus |
    | Troubleshooting | Very difficult | Difficult, but a station can report a fault | Ring |
    | Terminators | Required; a missing one breaks everything | Not needed | Ring |

    Why ring is generally judged better
    - `No collisions.` The token guarantees that only one station transmits at a time by design, rather than by detecting and recovering from collisions. This is decisive under heavy load, where a bus degrades badly but a ring keeps working predictably.
    - `Fair and deterministic access.` Every station gets the token in turn, so there is a guaranteed maximum waiting time — important for industrial and real-time applications.
    - `Signal regeneration at every node`, so the network can cover greater distances without a separate repeater.
    - `A dual counter-rotating ring`, as used by FDDI and SONET, survives a single cable break by wrapping the traffic back, which a bus can never do.

    Where bus wins
    - It is cheaper, uses less cable, is simpler to install, and adding a station does not require breaking a loop.

    Practical conclusion
    - Both are obsolete for LANs. The `switched star` replaced them, because it combines no collisions (like a ring) with easy installation and fault isolation (better than either), and one cable failure affects only one device. Ring topology survives today mainly in metro fibre networks, where the dual-ring resilience is the reason for choosing it.

14. **Draw Different type of Network topologies and mention their features.** *[Sonali & Janata Bank Senior Officer (IT/ICT) 2018 compact it 1166 (ET: N/A)]*

    Answer:

    1. Bus topology
    ```
    Terminator --+----+----+----+----+-- Terminator
                 |    |    |    |    |
                PC1  PC2  PC3  PC4  PC5
    ```
    - Features: one shared backbone with terminators at both ends; broadcast transmission that reaches every station; CSMA/CD access with collisions; least cabling and lowest cost; one break disables the entire network; very difficult to troubleshoot; poor scalability; no privacy. Obsolete.

    2. Star topology
    ```
             PC
              |
       PC --[SWITCH]-- PC
              |
             PC
    ```
    - Features: n links, one per device; easiest to install, extend and troubleshoot; a cable fault affects only one device; dedicated bandwidth and no collisions with a switch; central management and monitoring; but the central device is a single point of failure. The standard modern LAN.

    3. Ring topology
    ```
         A ----> B
         ^       |
         |       v
         D <---- C
    ```
    - Features: n links; unidirectional flow; token-controlled access so there are no collisions; fair and deterministic access with a bounded waiting time; every node regenerates the signal, allowing longer spans; but one break stops the ring unless a dual counter-rotating ring is used, and adding a device is disruptive. Used in FDDI and SONET metro rings.

    4. Mesh topology
    ```
          A -------- B
          | \      / |
          |   \  /   |
          |    \/    |
          |    /\    |
          D -------- C
    ```
    - Features: n(n − 1)/2 links and n − 1 ports per device; dedicated point-to-point links so there is no congestion; highest fault tolerance, since traffic reroutes around any failure; excellent privacy and easy fault isolation; but cost and cabling grow quadratically, so only a partial mesh is practical. Used for WAN backbones and wireless mesh.

    5. Tree (hierarchical) topology
    ```
                 [CORE SWITCH]
                 /           \
          [FLOOR SW]        [FLOOR SW]
           /  |  \            /    \
         PC  PC  PC         PC     PC
    ```
    - Features: n − 1 links; combines star groups on a common backbone; highly scalable and easy to expand floor by floor; faults confined to one branch; clear hierarchy simplifies management; but the root is critical and the backbone can become a bottleneck. The structured-cabling standard for buildings and campuses.

    6. Hybrid topology
    ```
        [ROUTER] ==== [ROUTER]      <- mesh between sites
           |               |
       [SWITCH]        [SWITCH]     <- star at each site
        / | \           /  |  \
      PC PC PC        PC  PC  PC
    ```
    - Features: any combination of the above; takes the strengths of each; flexible and highly scalable; fault tolerant when redundancy is designed in; but complex and expensive to plan and maintain. Almost every real network is a hybrid.

    Summary

    | Topology | Links | Cost | Reliability | Scalability | Troubleshooting |
    |---|---|---|---|---|---|
    | Bus | backbone + n taps | Lowest | Poor | Poor | Very hard |
    | Star | n | Low | Medium | Excellent | Easy |
    | Ring | n | Medium | Poor | Poor | Hard |
    | Mesh | n(n−1)/2 | Highest | Excellent | Poor | Easy |
    | Tree | n − 1 | Medium | Medium | Excellent | Moderate |
    | Hybrid | Varies | Varies | Good | Excellent | Moderate |

## IPv6 Addressing (13)

1. 4B:30:10:21:2A:1B, 4C:20:1B:2E:08:E7 Identify which of the given IPv6 addresses represent Unicast and Multicast communication, and determine whether any of them represents a Broadcast address. Explain your answer based on the IPv6 addressing rules. [BSCCPL AME 21-08-2026 (BUET)]

   Answer: The first point to make is that `neither of these is an IPv6 address`.

   Why they are not IPv6 addresses
   - An IPv6 address is `128 bits`, written as eight groups of four hexadecimal digits separated by colons, for example `2001:0db8:85a3:0000:0000:8a2e:0370:7334`.
   - The two given values have `six groups of two hexadecimal digits` = 48 bits, separated by colons. That is the format of a `MAC address`, not an IPv6 address.

   Answering them as MAC addresses
   - In a MAC address the type is decided by the least significant bit of the FIRST octet — the I/G (Individual/Group) bit: 0 means unicast, 1 means multicast.

   | Address | First octet | Binary | I/G bit | Type |
   |---|---|---|---|---|
   | 4B:30:10:21:2A:1B | 4B | 0100 1011 | `1` | `Multicast` |
   | 4C:20:1B:2E:08:E7 | 4C | 0100 1100 | `0` | `Unicast` |

   - Neither is a broadcast address. The broadcast MAC address is `FF:FF:FF:FF:FF:FF`, with all 48 bits set to 1.

   How IPv6 addressing rules would classify addresses

   | Type | IPv6 prefix | Meaning |
   |---|---|---|
   | Global unicast | 2000::/3 (starts with 2 or 3) | One interface, globally routable |
   | Link-local unicast | FE80::/10 | One interface, valid only on the local link |
   | Unique local unicast | FC00::/7 (in practice FD00::/8) | Private, like RFC 1918 |
   | Multicast | `FF00::/8` (starts with FF) | A group of interfaces |
   | Anycast | Taken from the unicast space | Delivered to the nearest member of a group |
   | Loopback | ::1 | The host itself |
   | Unspecified | :: | No address yet assigned |

   The key IPv6 rule the question is testing
   - `IPv6 has no broadcast address at all.` Broadcast was removed deliberately, because it forces every host on the link to process a packet it may not care about.
   - Its function is replaced by `multicast`, which reaches only interested hosts:
     - `FF02::1` — all nodes on the link (the nearest equivalent of broadcast)
     - `FF02::2` — all routers on the link
     - `FF02::1:FFxx:xxxx` — solicited-node multicast, used by Neighbour Discovery in place of ARP

   Conclusion
   - 4B:30:10:21:2A:1B is a `multicast` (group) address, 4C:20:1B:2E:08:E7 is a `unicast` address, and neither is a broadcast address.
   - More fundamentally, both are 48-bit MAC addresses rather than 128-bit IPv6 addresses, and IPv6 does not define a broadcast address in any case.

2. A host is connected to an IPv6 network and needs to configure its own IPv6 address automatically using Stateless Address Autoconfiguration (SLAAC). Arrange the steps in the correct order and explain the purpose of each step. [BSCCPL AME 21-08-2026 (BUET)]

   Answer: SLAAC lets a host configure its own IPv6 address with no DHCP server, using ICMPv6 Neighbour Discovery.

   The steps in the correct order

   Step 1 — Generate a tentative link-local address
   - The host forms `FE80::/64` plus a 64-bit interface identifier.
   - The interface ID comes either from the MAC address in EUI-64 form (split the 48-bit MAC, insert FFFE in the middle, and flip the 7th bit) or, for privacy, from a random value (RFC 4941 / 7217).
   - Purpose: every IPv6 interface needs a link-local address before it can send any Neighbour Discovery message at all. Nothing else can happen until this exists.

   Step 2 — Duplicate Address Detection (DAD) on the link-local address
   - The host sends a Neighbour Solicitation to the solicited-node multicast address of its own tentative address, with the source set to `::` (unspecified).
   - If no Neighbour Advertisement comes back, the address is unique and moves from `tentative` to `preferred`. If a reply arrives, the address is a duplicate and must not be used.
   - Purpose: guarantee uniqueness on the link before the address is used.

   Step 3 — Router Solicitation (RS)
   - The host multicasts an RS to `FF02::2`, the all-routers address.
   - Purpose: ask any router on the link to advertise immediately, rather than waiting for the next periodic advertisement (which may be up to several minutes away).

   Step 4 — Router Advertisement (RA)
   - The router replies with an RA to `FF02::1` (all nodes), carrying the on-link `/64 prefix`, the prefix lifetimes, the router's link-local address as the default gateway, the link MTU, and the `M` and `O` flags.
   - Purpose: tell the host which network it is on and which router to use.

   Step 5 — Generate the global unicast address
   - The host concatenates the advertised 64-bit prefix with its own 64-bit interface identifier.
   ```
   Prefix from RA        2001:db8:1:1::/64
   Interface identifier  ::a2b3:c4ff:fed5:e6f7
   Resulting address     2001:db8:1:1:a2b3:c4ff:fed5:e6f7/64
   ```
   - Purpose: obtain a globally routable address without any server.

   Step 6 — Duplicate Address Detection on the global address
   - The same NS/NA check is repeated for the new global address.
   - Purpose: confirm no other host on the link has generated the same address.

   Step 7 — Install the default gateway and obtain other settings
   - The router's link-local address from the RA becomes the default gateway.
   - The RA flags then decide what else is needed:
     - `M = 0, O = 0` — pure SLAAC; nothing more is required.
     - `M = 0, O = 1` — SLAAC for the address, plus `stateless DHCPv6` for DNS servers and the domain name.
     - `M = 1` — use `stateful DHCPv6` for the address itself instead.
   - RDNSS options inside the RA can also supply DNS servers without DHCPv6 at all.

   ```
   HOST                                              ROUTER
     |-- form FE80:: link-local                          |
     |-- NS (DAD) to solicited-node multicast --------->  |
     |   (no reply = address is unique)                   |
     |-- RS to FF02::2 ---------------------------------> |
     |<------------------- RA to FF02::1 (prefix, GW) ----|
     |-- build global = prefix + interface ID             |
     |-- NS (DAD) on the global address ---------------->  |
     |   address usable; default gateway = router's FE80  |
   ```

   - Advantages of SLAAC: no server, no state to maintain, and plug-and-play configuration.
   - Limitation: by itself it provides no DNS server or domain name, which is exactly why the O flag and stateless DHCPv6 exist.

3. **(a) What are the differences between IPv4 and IPv6, and why is IPv6 considered more secure?** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

   Answer:

   (a) Differences between IPv4 and IPv6

   | Point | IPv4 | IPv6 |
   |---|---|---|
   | Address size | 32 bits | 128 bits |
   | Address space | 4.3 × 10^9 | 3.4 × 10^38 |
   | Notation | Dotted decimal, 192.168.1.1 | Hexadecimal with colons, 2001:db8::1 |
   | Header size | 20–60 bytes, variable | 40 bytes, fixed |
   | Header fields | 13 | 8 — simpler and faster to process |
   | Checksum | Present in the header | Removed; left to the lower and upper layers |
   | Fragmentation | By the sender or any router | By the source only, using an extension header |
   | Configuration | Manual or DHCP | SLAAC, or DHCPv6 |
   | Broadcast | Yes | `None` — replaced entirely by multicast |
   | Address types | Unicast, multicast, broadcast | Unicast, multicast, anycast |
   | IPsec | Optional add-on | Designed in as part of the protocol |
   | NAT | Essential, because of address scarcity | Not needed |
   | ARP | Used to map IP to MAC | Replaced by Neighbour Discovery (NDP) using ICMPv6 |
   | QoS | ToS field | Traffic Class and a 20-bit Flow Label |
   | Mobility | Poor | Mobile IPv6 built in |
   | Loopback | 127.0.0.1 | ::1 |
   | Private range | 10/8, 172.16/12, 192.168/16 | FC00::/7 unique local |

   (b) Why IPv6 is considered more secure

   - `IPsec is built into the protocol.` In IPv4 IPsec was retrofitted and is optional; in IPv6 the Authentication Header and Encapsulating Security Payload are defined as standard extension headers, so authentication, integrity and encryption are native capabilities rather than add-ons.
   - `No NAT means true end-to-end security.` NAT rewrites addresses and therefore breaks end-to-end integrity checks and complicates IPsec. Without NAT, cryptographic protection can genuinely run host to host.
   - `Scanning a subnet is effectively impossible.` An IPv4 /24 has 254 hosts and can be swept in seconds. An IPv6 /64 has 1.8 × 10^19 addresses; at a million probes per second a full sweep would take over half a million years. This alone eliminates most automated reconnaissance and worm propagation.
   - `Secure Neighbour Discovery (SEND)` uses cryptographically generated addresses and RSA signatures to authenticate NDP messages, defeating the address-spoofing attacks that plague ARP.
   - `No broadcast` removes an entire family of amplification and reflection attacks, such as the IPv4 Smurf attack.
   - `Simpler, fixed-size header` gives attackers fewer malformed-packet and header-manipulation opportunities, and makes filtering more predictable.
   - `Mandatory 1280-byte minimum MTU and no router fragmentation` eliminates the fragmentation-based evasion techniques used to slip past IDS systems in IPv4.
   - `Privacy extensions` (RFC 4941) randomise and rotate the interface identifier, so a device cannot be tracked across networks by its MAC-derived address.

   Important caveat
   - IPv6 is not automatically more secure in practice. It introduces its own risks: rogue Router Advertisements (the IPv6 equivalent of a rogue DHCP server), extension-header abuse, and tunnels such as Teredo or 6to4 that can bypass IPv4 firewalls. Many organisations also run IPv6 unfiltered without realising it is enabled. Security still depends on configuration, not on the protocol version alone.

4. **How many bits in IPv4 and IPv6 address? Why NAT is not required in IPv6?** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 398 (ET: BUET)]*

   Answer:

   Address sizes
   - `IPv4 = 32 bits` (4 bytes), written in dotted decimal, giving 2^32 = about 4.3 billion addresses.
   - `IPv6 = 128 bits` (16 bytes), written as eight hexadecimal groups, giving 2^128 = about 3.4 × 10^38 addresses.

   Why NAT is not required in IPv6

   - `The address space is effectively unlimited.` NAT exists in IPv4 for exactly one reason: there are not enough public addresses, so many hosts must share one. With 3.4 × 10^38 addresses, every device on earth — including every sensor, appliance and vehicle — can have its own globally unique public address, many times over. A single /64 subnet alone holds 1.8 × 10^19 addresses.
   - `End-to-end connectivity is restored.` NAT breaks the original design of the internet, in which any host can address any other. Without NAT, peer-to-peer applications, VoIP, video calling, online gaming and IoT devices connect directly, with no port forwarding, no STUN or TURN servers and no ALGs.
   - `IPsec works properly.` NAT rewrites IP addresses, which invalidates the integrity checks IPsec performs over the header. Removing NAT allows genuine end-to-end authentication and encryption.
   - `Routers become simpler and faster.` No translation table to maintain, no per-flow state, no CPU spent rewriting headers and recalculating checksums, and no table-exhaustion failure mode under load.
   - `Troubleshooting and logging become accurate.` Every host has a unique address, so logs identify the real device rather than a shared public address, which matters for auditing and forensics.
   - `Applications become simpler.` Protocols such as FTP and SIP that embed IP addresses in their payload need special handling through NAT; without NAT they simply work.

   The security objection, and the answer to it
   - Some argue NAT provides security by hiding internal hosts. It does not: `a stateful firewall`, not NAT, is what blocks unsolicited inbound traffic, and IPv6 firewalls do exactly the same job while keeping addresses globally unique.
   - For those who still want address hiding, IPv6 offers `privacy extensions` (RFC 4941), which randomise and periodically change the interface identifier.

   - NAT66 does exist for IPv6, but it is discouraged and rarely used, precisely because it reintroduces all the problems listed above without solving any real shortage.

5. **(ক) IP Address কী? IPv4 এবং IPv6 এর মধ্যে চারটি প্রধান পার্থক্য লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 415 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   What is an IP address
   - A unique logical address assigned to every device on a TCP/IP network, so that it can be identified and located and packets can be routed to it.
   - It has two parts, a network portion and a host portion, separated by the subnet mask (or prefix length).
   - IPv4 uses 32 bits written in dotted decimal (192.168.1.10); IPv6 uses 128 bits written in hexadecimal (2001:db8::1).
   - It may be static or assigned by DHCP, and public or private.

   Four main differences between IPv4 and IPv6

   1. `Address size and space`
   - IPv4 is 32 bits, giving about 4.3 billion addresses — already exhausted.
   - IPv6 is 128 bits, giving 3.4 × 10^38 addresses, which is effectively unlimited.

   2. `Notation`
   - IPv4: four decimal octets separated by dots, 192.168.1.1.
   - IPv6: eight groups of four hexadecimal digits separated by colons, 2001:0db8:0000:0000:0000:8a2e:0370:7334, which may be shortened to 2001:db8::8a2e:370:7334.

   3. `Header and processing`
   - IPv4 has a variable 20–60 byte header with 13 fields, including a checksum, and any router may fragment a packet.
   - IPv6 has a fixed 40-byte header with 8 fields, no checksum, and only the source may fragment. This makes router processing significantly faster.

   4. `Configuration, NAT and security`
   - IPv4 needs manual configuration or DHCP, and relies on NAT because addresses are scarce.
   - IPv6 supports SLAAC, so a host configures itself; NAT is unnecessary; IPsec is part of the protocol rather than an add-on.

   Further differences worth naming
   - IPv6 has `no broadcast`; multicast replaces it entirely.
   - ARP is replaced by Neighbour Discovery over ICMPv6.
   - IPv6 adds a 20-bit Flow Label for QoS, and defines `anycast` as a standard address type.

6. **(a) Differentiate between IPV4 and IPV6.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 896 (ET: N/A)], [BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)], [WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 501 (ET: N/A)], [BMA Signal Assistant Engineer (Computer) 2021 compact it 932 (ET: BUET)]*

   Answer:

   | Point | IPv4 | IPv6 |
   |---|---|---|
   | Address size | 32 bits | 128 bits |
   | Total addresses | 2^32 ≈ 4.3 billion | 2^128 ≈ 3.4 × 10^38 |
   | Notation | Dotted decimal — 192.168.1.1 | Hexadecimal with colons — 2001:db8::1 |
   | Header length | 20–60 bytes, variable | 40 bytes, fixed |
   | Header fields | 13 | 8 |
   | Checksum | Present | Removed |
   | Fragmentation | By sender or any router | By the source only, via an extension header |
   | Options | In the header | In separate extension headers |
   | Configuration | Manual or DHCP | SLAAC or DHCPv6 |
   | Address types | Unicast, multicast, broadcast | Unicast, multicast, `anycast` — no broadcast |
   | Broadcast | Yes | None; replaced by multicast |
   | ARP | Used | Replaced by Neighbour Discovery (ICMPv6) |
   | IPsec | Optional | Built into the protocol |
   | NAT | Essential | Not needed |
   | QoS | ToS field | Traffic Class + 20-bit Flow Label |
   | Mobility | Poor | Mobile IPv6 built in |
   | Minimum MTU | 576 bytes | 1280 bytes |
   | Loopback | 127.0.0.1 | ::1 |
   | Private range | 10/8, 172.16/12, 192.168/16 | FC00::/7 (unique local) |
   | Link-local | 169.254.0.0/16 (APIPA) | FE80::/10, always present |
   | Subnet notation | Mask or prefix | Prefix only, normally /64 for a LAN |
   | Standard | RFC 791 (1981) | RFC 8200 (1998, revised 2017) |

   - The essential driver was IPv4 address exhaustion. Everything else — the simpler header, the removal of broadcast, the built-in autoconfiguration and IPsec — was an opportunity taken while redesigning the protocol.

7. **IPv4 and IPv6 how many bits and Why is NAT not needed in IPv6?** *[RPGCL Assistant Manager (ICT) 2022 compact it 652 (ET: BUET)]*

   Answer:

   Address sizes
   - `IPv4 = 32 bits`, giving 2^32 ≈ 4.3 billion addresses, written in dotted decimal (192.168.1.1).
   - `IPv6 = 128 bits`, giving 2^128 ≈ 3.4 × 10^38 addresses, written in hexadecimal (2001:db8::1).

   Why NAT is not needed in IPv6

   - `No address shortage.` NAT was invented for one purpose only — to let many private hosts share a scarce public IPv4 address. IPv6 has enough addresses for every device on earth many times over; a single /64 subnet contains 1.8 × 10^19 addresses, more than the whole IPv4 internet.
   - `End-to-end connectivity is restored.` Every host can have a globally unique, routable address, so peer-to-peer applications, VoIP, video calls, gaming and IoT devices connect directly without port forwarding, STUN, TURN or application-layer gateways.
   - `IPsec works correctly.` NAT rewrites the IP header, which breaks the integrity checks IPsec performs across it. Removing NAT allows true end-to-end authentication and encryption, which IPv6 supports natively.
   - `Simpler, faster routers.` No translation table, no per-flow state, no header rewriting or checksum recalculation, and no state-table exhaustion under heavy load.
   - `Accurate logging and troubleshooting.` Each device keeps its own unique address, so logs and audit trails identify the actual host rather than a shared public address.
   - `Applications that embed addresses simply work` — FTP, SIP and similar protocols need no special NAT handling.

   On the security argument for NAT
   - NAT is sometimes credited with providing security by hiding internal hosts. That protection actually comes from the `stateful firewall`, not from the translation. IPv6 firewalls block unsolicited inbound traffic just as effectively while keeping addresses globally unique.
   - Where address privacy is wanted, IPv6 provides `privacy extensions` (RFC 4941), which randomise and periodically change the interface identifier.

   - NAT66 exists but is discouraged; it reintroduces every drawback of NAT without solving any real shortage.

8. **IPv6 address কত বিটের?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) An IPv6 address is `128 bits` long — 16 bytes.

   Details
   - It is written as eight groups of four hexadecimal digits, separated by colons:
   ```
   2001:0db8:85a3:0000:0000:8a2e:0370:7334
   ```
   - Total address space = 2^128 ≈ 3.4 × 10^38 addresses, against IPv4's 2^32 ≈ 4.3 billion.

   Shortening rules
   - Leading zeros in any group may be dropped: `0db8` becomes `db8`.
   - One run of consecutive all-zero groups may be replaced by `::`, but only once in an address.
   ```
   2001:0db8:85a3:0000:0000:8a2e:0370:7334
   2001:db8:85a3::8a2e:370:7334        (shortened form)
   ```

   Structure of a typical global unicast address
   ```
   | 48 bits global routing prefix | 16 bits subnet | 64 bits interface ID |
   ```
   - A LAN is almost always given a `/64`, which leaves 64 bits for the interface identifier — enough for 1.8 × 10^19 hosts on one subnet.

   - For comparison: an IPv4 address is 32 bits, and a MAC address is 48 bits.

9. **What is the difference between stateful DHCPv6 and stateless DHCPv6?** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 840-841 (ET: N/A)]*

   Answer: Both are forms of DHCPv6; the difference is whether the server hands out the address itself and keeps a record of it.

   Stateful DHCPv6
   - The server assigns the `IPv6 address` to the client and keeps a binding — a record of which address went to which client, and for how long. This is the "state".
   - It also supplies the other settings: DNS servers, domain name, NTP servers.
   - It is the direct equivalent of IPv4 DHCP.
   - Triggered when the Router Advertisement has the `M flag (Managed) = 1`.
   - Use it when addresses must be controlled and logged centrally — enterprise networks, auditing, and reserving fixed addresses for servers.

   Stateless DHCPv6
   - The client obtains its `address by SLAAC` from the Router Advertisement, and asks DHCPv6 only for the extra information SLAAC cannot supply — DNS servers, domain name, NTP.
   - The server keeps `no record` of any client, because it never assigned an address. That is why it is stateless.
   - Triggered when the RA has `M = 0` and the `O flag (Other) = 1`.
   - Use it when SLAAC is adequate for addressing but DNS settings still have to be distributed.

   Comparison

   | Point | Stateful DHCPv6 | Stateless DHCPv6 |
   |---|---|---|
   | Who assigns the address | The DHCPv6 server | The host itself, by SLAAC |
   | Server keeps a binding | Yes | No |
   | RA flags | M = 1 | M = 0, O = 1 |
   | Information supplied | Address, DNS, domain, NTP | DNS, domain, NTP only |
   | Central control | Full | Limited |
   | Server load and state | Higher | Very low |
   | Audit trail of who had which address | Yes | No |
   | Equivalent to | IPv4 DHCP | SLAAC plus a small helper |

   - The third option is `pure SLAAC` (M = 0, O = 0), where no DHCPv6 is used at all. DNS can still be delivered through the RDNSS option inside the Router Advertisement.
   - DHCPv6 uses UDP ports 546 (client) and 547 (server), and clients reach servers at the multicast address FF02::1:2.

10. **What is DHCPv6?** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 841 (ET: N/A)]*

    Answer: DHCPv6 is the Dynamic Host Configuration Protocol for IPv6, defined in RFC 8415. It supplies IPv6 hosts with addresses and other configuration parameters.

    Key facts
    - Ports: `UDP 546` for the client and `UDP 547` for the server.
    - Clients reach servers on the multicast address `FF02::1:2` (all DHCPv6 servers and relay agents on the link).
    - Clients are identified by a `DUID` (DHCP Unique Identifier) rather than by MAC address, together with an IAID identifying the interface.

    Message exchange — four steps, like IPv4's DORA
    ```
    CLIENT                                  SERVER
      |------- SOLICIT (to FF02::1:2) ------->|
      |<------ ADVERTISE ---------------------|
      |------- REQUEST ---------------------->|
      |<------ REPLY -------------------------|
    ```
    - A two-message rapid-commit exchange (Solicit / Reply) is also possible.

    Two modes
    - `Stateful` — the server assigns the address and keeps a binding for it. Triggered by the M flag in the Router Advertisement.
    - `Stateless` — the host gets its address by SLAAC and asks DHCPv6 only for DNS, domain name and NTP. Triggered by the O flag. The server keeps no per-client state.

    Differences from IPv4 DHCP
    - No broadcast is used, because IPv6 has none; multicast is used instead.
    - No default gateway option — the gateway always comes from the Router Advertisement, never from DHCPv6. This is a common exam point.
    - Clients are keyed by DUID rather than MAC address.
    - It can delegate whole prefixes (`Prefix Delegation`, IA_PD), which is how an ISP hands a customer router a /56 or /48 to subdivide internally.
    - SLAAC exists as a complete alternative, so DHCPv6 is optional in a way IPv4 DHCP never was.

11. **Explain IPv6 link local address and multicast address.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 843 (ET: N/A)]*

    Answer:

    IPv6 link-local address
    - Prefix: `FE80::/10`; in practice every link-local address begins `FE80::` with the next 54 bits zero, followed by a 64-bit interface identifier.
    ```
    FE80::a2b3:c4ff:fed5:e6f7
    ```
    - Every IPv6 interface `automatically` configures one as soon as IPv6 is enabled — it is mandatory, not optional.
    - Scope: the local link only. Routers never forward a packet with a link-local source or destination, so the same address may be reused on every segment.
    - The interface ID comes from the MAC address in EUI-64 form, or from a random value for privacy.
    - Because the same address can appear on several interfaces, a zone index is required when using it: `ping6 fe80::1%eth0`.

    What link-local addresses are used for
    - Neighbour Discovery — the replacement for ARP.
    - Router Advertisement and Router Solicitation messages.
    - The `default gateway` on an IPv6 host is always the router's link-local address, never its global one.
    - Routing protocol adjacencies: OSPFv3 and EIGRPv6 form neighbours over link-local addresses.
    - Communication on a link before any global address exists — SLAAC itself depends on it.

    IPv6 multicast address
    - Prefix: `FF00::/8` — any address starting with FF is multicast.
    - Structure:
    ```
    | 8 bits | 4 bits | 4 bits |        112 bits          |
    |  FF    | flags  | scope  |        group ID          |
    ```
    - Flags: 0 means a permanently assigned (well-known) group; 1 means a temporary group.
    - Scope, which limits how far the packet travels:

    | Value | Scope |
    |---|---|
    | 1 | Interface-local |
    | 2 | Link-local |
    | 5 | Site-local |
    | 8 | Organisation-local |
    | E | Global |

    Well-known multicast addresses

    | Address | Meaning |
    |---|---|
    | `FF02::1` | All nodes on the link — the nearest thing to IPv4 broadcast |
    | `FF02::2` | All routers on the link |
    | `FF02::5`, `FF02::6` | OSPFv3 routers, OSPFv3 designated routers |
    | `FF02::9` | RIPng routers |
    | `FF02::1:2` | All DHCPv6 servers and relay agents |
    | `FF02::1:FFxx:xxxx` | Solicited-node multicast, used by Neighbour Discovery |

    Why multicast matters so much in IPv6
    - IPv6 has `no broadcast at all`. Every function that used broadcast in IPv4 uses multicast instead, which is more efficient because uninterested hosts are never disturbed.
    - The `solicited-node` address is the neatest example: instead of broadcasting an ARP request to every device, the host multicasts only to the small group whose addresses share the last 24 bits, so typically just one machine is interrupted.

12. **Write down the difference between IPv4 and IPv6.** *[BREB Assistant Junior Engineer (IT) 2019 compact it 1122-1123 (ET: BREB)]*

    Answer:

    | Point | IPv4 | IPv6 |
    |---|---|---|
    | Address length | 32 bits | 128 bits |
    | Address space | 2^32 ≈ 4.3 billion | 2^128 ≈ 3.4 × 10^38 |
    | Notation | Dotted decimal — 192.168.1.1 | Hexadecimal with colons — 2001:db8::1 |
    | Number of fields in header | 13 | 8 |
    | Header size | 20–60 bytes, variable | 40 bytes, fixed |
    | Header checksum | Yes | No — removed for speed |
    | Fragmentation | Sender or any router | Source only, via an extension header |
    | Options | Inside the header | Separate extension headers |
    | Address configuration | Manual or DHCP | SLAAC, DHCPv6, or both |
    | Address types | Unicast, multicast, broadcast | Unicast, multicast, anycast |
    | Broadcast | Supported | `Not supported` — multicast replaces it |
    | Address resolution | ARP | Neighbour Discovery (ICMPv6) |
    | Security | IPsec optional | IPsec built in |
    | NAT | Required | Not required |
    | QoS | ToS field | Traffic Class + 20-bit Flow Label |
    | Mobility support | Weak | Mobile IPv6 built in |
    | Minimum MTU | 576 bytes | 1280 bytes |
    | Loopback address | 127.0.0.1 | ::1 |
    | Private addressing | 10/8, 172.16/12, 192.168/16 | FC00::/7 unique local |
    | Link-local | 169.254.0.0/16 (only on DHCP failure) | FE80::/10, always configured |
    | Typical LAN subnet | /24 | /64 |
    | Defined in | RFC 791 (1981) | RFC 8200 (1998, revised 2017) |

    - Transition mechanisms used while both coexist: `dual stack` (run both protocols on every device — the preferred method), `tunnelling` (6to4, Teredo, ISATAP — carry IPv6 packets inside IPv4) and `translation` (NAT64 with DNS64).

13. **How many bits for IPv6? Write an example IPv6?** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1150 (ET: KUET)]*

    Answer: An IPv6 address is `128 bits` long — 16 bytes.

    Format
    - Eight groups of four hexadecimal digits, separated by colons.

    Example of a full IPv6 address
    ```
    2001:0db8:85a3:0000:0000:8a2e:0370:7334
    ```

    The same address in shortened form
    ```
    2001:db8:85a3::8a2e:370:7334
    ```
    - Two rules were applied: leading zeros in a group may be dropped (`0db8` → `db8`), and one run of consecutive all-zero groups may be replaced by `::`, which may appear only once in an address.

    Other example addresses

    | Address | Type |
    |---|---|
    | `2001:db8::1` | Global unicast (documentation prefix) |
    | `fe80::a2b3:c4ff:fed5:e6f7` | Link-local |
    | `fd00:1234::1` | Unique local (private) |
    | `ff02::1` | Multicast — all nodes on the link |
    | `::1` | Loopback |
    | `::` | Unspecified |

    Structure of a typical global unicast address
    ```
    | 48 bits routing prefix | 16 bits subnet ID | 64 bits interface ID |
    ```
    - A LAN is almost always assigned a `/64`, leaving 64 bits for the interface identifier.
    - Total space: 2^128 ≈ 3.4 × 10^38 addresses, against 2^32 ≈ 4.3 billion for IPv4's 32 bits.

## Physical Layer & Optical Fiber (Attenuation & Power Budget) (13)

1. **A fiber optic network is designed using single-mode fiber with an attenuation of 0.35 dB/km. The network includes a splitter with a 14 dB loss as specified in the datasheet. Additionally, there are two mechanical splices (each with 0.1 dB loss) and two connectors (each with 0.75 dB loss). Given the following parameters:**
   * **Transmitter Power: 5 dBm**
   * **Receiver Sensitivity: -14 dBm**
   * **Fiber Attenuation: 0.35 dB/km**
   **Calculate the maximum fiber length (D) that can be used between the OLT (Optical Line Terminal) and ONU (Optical Network Unit) while maintaining an acceptable signal level.** *[Islami Bank PLC Senior Officer (Network/System) 14.03.2025 compact it 1332 (ET: BUET)]*

   Answer: Find the total power budget, subtract every fixed loss, and divide what remains by the fibre attenuation per kilometre.

   Given
   - Transmitter power = +5 dBm
   - Receiver sensitivity = −14 dBm
   - Fibre attenuation = 0.35 dB/km
   - Splitter loss = 14 dB
   - 2 mechanical splices × 0.1 dB
   - 2 connectors × 0.75 dB

   Step 1 — total power budget
   ```
   Power budget = transmitter power − receiver sensitivity
                = 5 − (−14)
                = 19 dB
   ```

   Step 2 — total fixed (non-fibre) losses

   | Component | Quantity | Loss each | Total |
   |---|---|---|---|
   | Splitter | 1 | 14 dB | 14.0 dB |
   | Mechanical splices | 2 | 0.1 dB | 0.2 dB |
   | Connectors | 2 | 0.75 dB | 1.5 dB |
   | | | `Total` | `15.7 dB` |

   Step 3 — loss available for the fibre itself
   ```
   Available = 19 − 15.7 = 3.3 dB
   ```

   Step 4 — maximum fibre length
   ```
   D = available loss / attenuation per km
     = 3.3 / 0.35
     = 9.43 km
   ```

   - Answer: `D ≈ 9.43 km` (about 9.4 km).

   Check
   ```
   Total link loss = (9.43 × 0.35) + 15.7 = 3.3 + 15.7 = 19.0 dB
   Received power  = 5 − 19 = −14 dBm  = exactly the receiver sensitivity
   ```

   Practical note on safety margin
   - Working right at the sensitivity limit leaves nothing for ageing, temperature, future repair splices or connector contamination. A design margin of 3 dB is normal:
   ```
   Available for fibre = 19 − 15.7 − 3 = 0.3 dB  ->  D = 0.86 km
   ```
   - The 14 dB splitter is what dominates this budget. It corresponds to roughly a 1:16 PON split, and it is the reason the reach is short. Reducing the split ratio, or using a transmitter with higher output, is the only way to extend the distance meaningfully.

2. **(a) Why fiber optic cable is used in submarine instead of satellite?** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 431 (ET: BUET)]*

   Answer: Submarine fibre-optic cable carries well over 95 percent of all intercontinental traffic, and satellite carries very little. The reasons are decisive.

   Capacity
   - A single fibre pair carries tens of terabits per second, and a modern cable holds many pairs — hundreds of terabits in total. A satellite transponder offers hundreds of Mbps to a few Gbps. The difference is four to six orders of magnitude.

   Latency
   - This is the strongest argument. A geostationary satellite orbits at 35,786 km, so the signal must travel up and down: about `250 ms one way`, 500 ms round trip. Fibre from Bangladesh to Singapore takes roughly 20–30 ms.
   - Half a second of delay makes voice calls awkward, breaks interactive applications, and cripples TCP throughput, since TCP performance falls as the round-trip time rises.

   Cost per bit
   - A submarine cable is expensive to lay but, spread over its capacity and its 25-year life, the cost per gigabit is a tiny fraction of satellite capacity, which is limited and must be rented continuously.

   Reliability and quality
   - Fibre is unaffected by rain, cloud, solar activity or atmospheric conditions. Satellite links suffer rain fade, especially at Ku and Ka band, and solar interference twice a year when the sun passes behind the satellite.
   - Bit error rates on fibre are extremely low, so far less forward error correction is needed.

   Security
   - A satellite signal is a broadcast that anyone with a dish in the footprint can receive. Tapping a submarine cable requires physically reaching it on the sea floor, which is difficult and detectable.

   Scalability
   - Capacity on an existing cable can be increased simply by upgrading the terminal equipment at each end — new transponders and more WDM wavelengths on the same glass. Increasing satellite capacity requires launching another satellite.

   Power and lifetime
   - Repeaters on a cable are powered from shore and last decades. A satellite has finite fuel and a design life of roughly 15 years, after which it must be replaced.

   Where satellite is still the right choice
   - Reaching ships, aircraft, oil rigs and remote islands where no cable can land.
   - Broadcasting the same content to a very large area at once.
   - Disaster recovery, when cables are cut.
   - Rapid deployment where no infrastructure exists.
   - Low Earth Orbit constellations reduce latency to 20–40 ms and are changing this balance for consumer access, but they still cannot approach the capacity or cost per bit of a submarine cable for trunk traffic.

3. **(b) Why the submarine cable is damaged under water?** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 432 (ET: BUET)]*

   Answer: Submarine cables are damaged surprisingly often — roughly 150 to 200 faults occur worldwide every year. The causes fall into three groups.

   Human activity — about 70 to 80 percent of all faults
   - `Fishing gear` — trawlers dragging nets and beam trawls across the sea bed snag and cut cables. This is the single largest cause.
   - `Ship anchors` — vessels anchoring, or dragging anchor in bad weather, in or near cable corridors. Anchoring is prohibited in cable zones, but violations are common.
   - `Dredging and construction` — sand extraction, pipeline laying and port works.
   - `Deliberate damage` — sabotage, and theft of cable for its copper and steel, which has occurred in shallow water.
   - Most human damage happens in `shallow water`, within about 200 m depth, which is why cables are armoured and buried near shore and left unburied in the deep ocean.

   Natural causes
   - `Submarine landslides and turbidity currents` — an undersea avalanche of sediment can break several cables at once. The 2006 Hengchun earthquake off Taiwan cut eight cables this way.
   - `Earthquakes and seafloor movement`, which both break cables directly and trigger landslides.
   - `Volcanic activity` — the 2022 Tonga eruption severed the country's only cable.
   - `Abrasion` where a cable rests on rock and is moved by currents, gradually wearing through the sheath.
   - `Strong currents and tidal scour` that expose a buried cable.
   - `Marine life` — shark and fish bites have been recorded, though this is rare and mostly affects unarmoured cable.
   - `Corrosion` of the metallic sheath and water ingress over time.

   Technical and manufacturing causes
   - Component failure in a repeater or branching unit.
   - Insulation or joint failure allowing water into the cable.
   - Manufacturing defects or damage during laying.
   - Ageing, as cables are designed for about 25 years.

   Consequences and mitigation
   - A cut can reduce national bandwidth sharply. Bangladesh has experienced this with SEA-ME-WE 4 and SEA-ME-WE 5.
   - Repair requires a specialist cable ship to locate the fault, grapple the cable to the surface, splice in a new section and re-lay it — typically one to three weeks depending on weather and ship availability.
   - Mitigation: burying cable to 1–3 m in shallow water, double armouring near shore, marking cable corridors on charts, monitoring vessel traffic by AIS, and above all `route diversity` — connecting through several independent cables and landing stations so that one cut is not a national outage.

4. **(ক) ফাইবার অপটিক ক্যাবলের গঠন ও বৈশিষ্ট্য ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 614 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   Structure of a fibre optic cable
   ```
           +---------------------------------------+
           |          Outer jacket (PVC)           |
           |  +---------------------------------+  |
           |  |   Strength member (Kevlar)      |  |
           |  |  +---------------------------+  |  |
           |  |  |   Buffer coating          |  |  |
           |  |  |  +---------------------+  |  |  |
           |  |  |  |   Cladding (n2)     |  |  |  |
           |  |  |  |  +---------------+  |  |  |  |
           |  |  |  |  |   CORE (n1)   |  |  |  |  |    n1 > n2
           |  |  |  |  +---------------+  |  |  |  |
           |  |  |  +---------------------+  |  |  |
           |  |  +---------------------------+  |  |
           |  +---------------------------------+  |
           +---------------------------------------+
   ```

   - `Core` — the central glass (or plastic) strand that actually carries the light. Diameter 8–10 µm in single-mode fibre, 50 or 62.5 µm in multimode. It has the higher refractive index, n1.
   - `Cladding` — a glass layer surrounding the core with a slightly `lower` refractive index, n2. This difference is what causes total internal reflection and keeps the light inside the core. Outer diameter is 125 µm in both fibre types.
   - `Buffer coating` — a plastic layer that protects the glass from moisture and physical damage, and makes the fibre easier to handle.
   - `Strength member` — aramid yarn (Kevlar) that takes the pulling force during installation so the glass is not stressed.
   - `Outer jacket` — the PVC or LSZH sheath that protects everything and carries the identification markings.

   Working principle
   - Light enters the core at an angle greater than the critical angle and undergoes `total internal reflection` at the core–cladding boundary, so it bounces along the fibre rather than escaping. Digital data is sent as pulses of light: light on for 1, off for 0.

   Characteristics (features)
   - Enormous bandwidth — terabits per second with WDM.
   - Very low attenuation — about 0.2 dB/km at 1550 nm, so links of 80 km need no repeater.
   - Complete immunity to electromagnetic and radio interference, and no crosstalk between fibres.
   - High security: tapping requires physically bending or breaking the fibre, which is detectable.
   - Light, thin and space-efficient compared with copper of equivalent capacity.
   - Electrically safe — no sparks, no short circuits, no earthing problems, and immune to lightning surges.
   - Not corroded by moisture the way copper conductors are.
   - Long life and future-proof: capacity is increased by changing the transceivers, not the cable.

   Limitations
   - Higher cost of cable and equipment, fragile with a minimum bend radius, splicing needs skilled technicians and a fusion splicer, and it cannot deliver power the way PoE does over copper.

5. **Write down the Working principle of Optical Fibre.** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 649 (ET: BUET)]*

   Answer: An optical fibre carries information as pulses of light, guided along the core by `total internal reflection`.

   The physical principle
   - The core has a higher refractive index (n1) than the cladding (n2), so `n1 > n2`.
   - Snell's law gives the critical angle:
   ```
   θc = sin⁻¹ (n2 / n1)
   ```
   - When light strikes the core–cladding boundary at an angle of incidence `greater than θc`, none of it passes into the cladding — it is entirely reflected back into the core. That is total internal reflection, and it repeats thousands of times per metre, guiding the light along the fibre.

   ```
      cladding (n2)
     ────────────────────────────────────────
          \      /\      /\      /\
           \    /  \    /  \    /  \      core (n1), n1 > n2
            \  /    \  /    \  /    \
     ────────\/──────\/──────\/──────\/──────
      cladding (n2)      angle of incidence > critical angle
   ```

   How data is transmitted, step by step
   - Step 1 — the electrical data signal drives an optical source: an LED for multimode short links, or a laser diode for single-mode long-haul links.
   - Step 2 — the source converts it into light pulses. Light on represents 1, light off represents 0. This is intensity modulation.
   - Step 3 — the light enters the core within the `acceptance cone`, described by the numerical aperture:
   ```
   NA = sqrt(n1² − n2²)
   ```
   Light entering outside this cone escapes into the cladding and is lost.
   - Step 4 — the pulses travel the length of the fibre by repeated total internal reflection, losing very little energy: about 0.2 dB/km at 1550 nm.
   - Step 5 — at the far end a photodetector, a PIN photodiode or avalanche photodiode, converts the light back into an electrical signal.
   - Step 6 — the receiver amplifies, reshapes and retimes the signal, recovering the original data.
   - Step 7 — on long links, optical amplifiers (EDFAs) or regenerators are placed periodically to restore the signal level.

   Two fibre types
   - `Single-mode` — 8–10 µm core; only one path (mode) exists, so there is no modal dispersion. Used with lasers at 1310 or 1550 nm for long distances.
   - `Multimode` — 50 or 62.5 µm core; many paths exist, and because they have different lengths the pulse spreads (modal dispersion), limiting distance. Used with LEDs or VCSELs at 850 nm for short links.

   Limiting factors
   - `Attenuation` — absorption and scattering, which weaken the signal.
   - `Dispersion` — pulse spreading, which limits how close together pulses can be and therefore caps the bit rate over a given distance.

6. **Define the attenuation and dispersion in an optical fiber. Draw the block diagram of a long-haul optical fiber communication system.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

   Answer:

   Attenuation in an optical fibre
   - Attenuation is the loss of optical power as light travels along the fibre, measured in decibels per kilometre.
   ```
   Attenuation (dB/km) = (10 / L) × log10 (Pin / Pout)
   ```
   - Typical values for silica fibre: 3 dB/km at 850 nm, 0.4 dB/km at 1310 nm and `0.2 dB/km at 1550 nm`, which is why long-haul systems use 1550 nm.

   Causes of attenuation
   - `Absorption` — intrinsic absorption by the silica itself, and extrinsic absorption by impurities, especially the OH⁻ (water) ion, which produces the peak near 1385 nm.
   - `Scattering` — Rayleigh scattering from microscopic density variations frozen into the glass. It varies as 1/λ⁴, which is why longer wavelengths have lower loss.
   - `Bending losses` — macrobending when the cable is coiled too tightly, and microbending from small imperfections and pressure points.
   - `Coupling losses` — at connectors, splices and the source-to-fibre junction.

   Dispersion in an optical fibre
   - Dispersion is the `spreading of a light pulse` as it propagates, so that a sharp input pulse arrives broadened. Adjacent pulses eventually overlap — intersymbol interference — which sets the maximum bit rate for a given distance. It is measured in ps/(nm·km).

   Types of dispersion
   - `Modal dispersion` — different modes travel different path lengths in a multimode fibre and therefore arrive at different times. It is the dominant limit in multimode fibre and is eliminated entirely in single-mode fibre. Graded-index fibre reduces it.
   - `Chromatic dispersion` — different wavelengths travel at slightly different speeds. It has two parts, material dispersion and waveguide dispersion. It is the main limit in single-mode fibre, and it is compensated with dispersion-compensating fibre or Bragg gratings. It falls to zero near 1310 nm in standard fibre.
   - `Polarisation mode dispersion (PMD)` — the two polarisation states travel at slightly different speeds because the core is never perfectly circular. It matters only at very high bit rates.

   - Together the two set the link budget: attenuation limits how far the signal can go before it is too weak, dispersion limits how fast it can be sent before pulses merge.

   Block diagram of a long-haul optical fibre communication system
   ```
   +-----------+   +---------+   +--------+                +--------+
   |  Electrical|-->| Optical |-->|Fibre   |--- 80 km ---->|Optical |
   |  input     |   | Trans-  |   |coupler |                |Amplifier|
   |  (data)    |   | mitter  |   |        |                | (EDFA) |
   +-----------+   | laser + |   +--------+                +---+----+
                   | driver  |                                 |
                   +---------+                                 v
                                                        --- 80 km fibre ---
                                                               |
                                                               v
                                                       +---------------+
                                                       | Regenerator / |
                                                       | dispersion    |
                                                       | compensator   |
                                                       +-------+-------+
                                                               |
                                                               v
   +-----------+   +-----------+   +---------------+   +---------------+
   | Electrical|<--| Receiver  |<--| Photodetector |<--| Optical       |
   | output    |   | amp +     |   | PIN / APD     |   | pre-amplifier |
   | (data)    |   | decision  |   |               |   |               |
   +-----------+   +-----------+   +---------------+   +---------------+
   ```
   - Key elements: laser transmitter, single-mode fibre spans, EDFA optical amplifiers every 80–100 km, dispersion compensation, an optical pre-amplifier, photodetector and receiver electronics. With WDM, a multiplexer and demultiplexer are added at each end so that many wavelengths share the same fibre.

7. **Define the principle of data transmission through the fiber optic cable.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*

   Answer: Data is transmitted through fibre optic cable as `pulses of light guided by total internal reflection`.

   The principle
   - The fibre has a core of refractive index n1 surrounded by cladding of a lower index n2, so `n1 > n2`.
   - Light striking the core–cladding boundary at an angle greater than the critical angle
   ```
   θc = sin⁻¹ (n2 / n1)
   ```
   is `completely reflected` back into the core — none escapes. Repeating this thousands of times per metre guides the light along the fibre, even round gentle bends.

   The transmission process
   - Step 1 — the electrical data signal drives an optical source: a laser diode for long single-mode links, an LED or VCSEL for short multimode links.
   - Step 2 — the source performs `intensity modulation`: light on for binary 1, light off for binary 0. Modern systems also use phase and amplitude modulation for higher rates.
   - Step 3 — light must enter within the `acceptance cone`, defined by the numerical aperture NA = sqrt(n1² − n2²). Anything outside it leaks away.
   - Step 4 — the pulses travel down the core by total internal reflection, attenuating by only about 0.2 dB/km at 1550 nm.
   - Step 5 — a photodetector (PIN or avalanche photodiode) at the far end converts the light back into current.
   - Step 6 — the receiver amplifies, reshapes and retimes the signal to recover the original bit stream.
   - Step 7 — on long routes, optical amplifiers (EDFAs) boost the signal every 80–100 km without converting it back to electricity.

   ```
   Data --> [Laser/LED] --> ((( light pulses in the core ))) --> [Photodiode] --> Data
                 modulation        total internal reflection        detection
   ```

   Why light rather than electricity
   - Optical frequencies are around 10^14 Hz, so the available bandwidth is enormous — terabits per second with WDM.
   - Glass has far lower loss than copper at high frequencies.
   - Light is unaffected by electromagnetic interference, and produces none.

   Practical limits
   - `Attenuation` weakens the signal with distance; `dispersion` spreads the pulses so that they eventually overlap. These two together determine how far and how fast a link can run.

8. **How can you do fix the signal attenuation problems?** *[BOF Assistant Programmer 2022 compact it 734 (ET: MIST)]*

   Answer: Attenuation is the weakening of a signal with distance. It is fixed by the following measures.

   For any medium
   - `Insert repeaters or amplifiers` at the correct spacing. An amplifier boosts an analogue signal but amplifies the accumulated noise with it; a `repeater` regenerates a digital signal completely, discarding the noise. This is the single most important remedy, and it is why digital transmission is preferred.
   - `Keep within the specified cable length` — 100 m for UTP, 185 m for thin coax, 500 m for thick coax. Exceeding it is the most common self-inflicted cause.
   - `Use a lower-loss medium` — optical fibre loses about 0.2 dB/km against tens of dB per hundred metres for copper. Replacing a long copper run with fibre plus media converters solves the problem outright.
   - `Use higher-quality cable` — Cat6a instead of Cat5e, thicker conductors, better dielectric.
   - `Add an equaliser` to boost the high frequencies more than the low ones, since attenuation increases with frequency and would otherwise distort the pulse shape.
   - `Increase transmit power`, within regulatory and safety limits.
   - `Reduce the number of connectors, joints and patch panels`, since each adds insertion loss, and keep the ones that remain clean and correctly seated.
   - `Improve terminations` — a poor crimp or a dirty fibre connector can add more loss than a kilometre of cable.

   For optical fibre specifically
   - Use `1550 nm` rather than 1310 or 850 nm, since Rayleigh scattering falls as 1/λ⁴.
   - Use `fusion splices` (about 0.05 dB) rather than mechanical splices (0.2–0.5 dB).
   - Respect the `minimum bend radius`; macrobending and microbending losses are a frequent field problem.
   - Keep connector end faces spotless, and inspect them with a scope before mating.
   - Insert `EDFA optical amplifiers` every 80–100 km on long-haul routes.

   For wireless
   - Use higher-gain directional antennas, raise the antenna to clear obstructions, choose a lower frequency for better penetration, and add relay or repeater nodes.

   Design practice
   - Compute a `link budget`: transmit power minus receiver sensitivity gives the total loss the link can tolerate. Subtract every fixed loss, then check the remaining budget against the cable length, and always leave a `3 dB margin` for ageing, temperature and future repairs.

9. **Where are the low loss transmission windows of silicon based optical fiber and Which window is the most popular in communication and wave. Draw diagram of a long haul WDM Transmission system.** *[BTCL Assistant Manager (Technical) 2021 compact it 765 (ET: BUET)]*

   Answer:

   The low-loss transmission windows of silica fibre
   - Silica fibre has three historic windows where attenuation is low, separated by absorption peaks caused mainly by the OH⁻ (water) ion.

   | Window | Wavelength | Typical attenuation | Notes |
   |---|---|---|---|
   | 1st | 850 nm | ~3 dB/km | Cheap LEDs and VCSELs; short multimode links |
   | 2nd | 1310 nm | ~0.4 dB/km | Zero chromatic dispersion in standard fibre |
   | 3rd | `1550 nm` | `~0.2 dB/km` | Lowest loss of all; the EDFA amplification band |

   - Modern bands are labelled O (1260–1360), E (1360–1460), S (1460–1530), `C (1530–1565)`, L (1565–1625) and U (1625–1675). The C band sits inside the third window.

   The most popular window
   - `1550 nm — the third window, the C band` — is by far the most used in long-haul communication, for three reasons:
     - It has the `lowest attenuation` of any wavelength in silica, about 0.2 dB/km, which allows 80–100 km spans between amplifiers.
     - It is the band in which the `erbium-doped fibre amplifier (EDFA)` works. The EDFA amplifies the optical signal directly, without converting it to electricity, and amplifies all WDM channels at once. This single fact made DWDM economically possible.
     - It offers wide usable bandwidth, so 40 to 160 DWDM channels fit within it.
   - Its one drawback, higher chromatic dispersion than at 1310 nm, is handled by dispersion-compensating fibre or by dispersion-shifted fibre.

   Block diagram of a long-haul WDM transmission system
   ```
    Tx1 λ1 ---\                                                    /--- λ1 Rx1
    Tx2 λ2 ----\      +-----+      +------+      +------+     /----- λ2 Rx2
    Tx3 λ3 -----+---->| MUX |----->| Boost|--///-| EDFA |--///-+---->| DEMUX |----> λ3 Rx3
    Tx4 λ4 ----/      |(AWG)|      | ampl.|  80  | in-  |  80  |     | (AWG) |
    TxN λN ---/       +-----+      +------+  km  | line |  km  |     +-------+
                                                 +------+
                                                    |
                                           repeated every 80-100 km
                                                    |
                                                 +--v---+
                                                 | Pre- |
                                                 | ampl.|--> DEMUX --> receivers
                                                 +------+
   ```
   - `Transmitters` — one DFB laser per wavelength, each precisely on an ITU grid channel (100 GHz or 50 GHz spacing).
   - `MUX (AWG)` — an arrayed waveguide grating combines all wavelengths onto one fibre.
   - `Booster amplifier` — raises the combined power before launching into the line.
   - `In-line EDFAs` — every 80–100 km, amplifying all channels simultaneously.
   - `Dispersion compensation modules` — inserted with the amplifiers to undo pulse spreading.
   - `Pre-amplifier` — boosts the weak signal just before detection.
   - `DEMUX` — separates the wavelengths again, each to its own photodetector and receiver.
   - Optional `OADM` (optical add-drop multiplexers) drop and add individual wavelengths at intermediate sites without disturbing the rest.

10. **A 1550nm fiber optic transmission Link if of 50km length without repeating with a signal mode fiber having loss of 0.2dB/km. The fiber is joined ever 2km with conductor each with 0.5dB loss. Determine the minimum average power which should be lunched in to the fiver in order to Tarantion an average optical power level of 10 micro-watts at the receiver.** *[BTCL Assistant Manager (Technical) 2021 compact it 766 (ET: BUET)]*

    Answer:

    Given
    - Length L = 50 km, wavelength 1550 nm, single-mode fibre
    - Fibre loss = 0.2 dB/km
    - Connectors every 2 km, each 0.5 dB
    - Required received power = 10 µW

    Step 1 — total fibre attenuation
    ```
    = 50 km × 0.2 dB/km = 10 dB
    ```

    Step 2 — number of connectors and their loss
    - The fibre is joined every 2 km, so 50 km consists of 25 sections of 2 km, giving `24 internal joints`.
    ```
    Connector loss = 24 × 0.5 = 12 dB
    ```

    Step 3 — total link loss
    ```
    Total = fibre loss + connector loss
          = 10 + 12
          = 22 dB
    ```

    Step 4 — convert the required output power to dBm
    ```
    Pout = 10 µW = 10 × 10^-6 W = 10 × 10^-3 mW
    Pout(dBm) = 10 log10 (0.01) = −20 dBm
    ```

    Step 5 — required launch power
    ```
    Pin(dBm) = Pout(dBm) + total loss
             = −20 + 22
             = +2 dBm
    ```

    Step 6 — convert back to watts
    ```
    Pin = 10^(2/10) mW = 1.585 mW ≈ 1.59 mW
    ```

    | Quantity | Value |
    |---|---|
    | Fibre loss | 10 dB |
    | Connector loss (24 × 0.5) | 12 dB |
    | Total loss | 22 dB |
    | Required received power | 10 µW = −20 dBm |
    | `Minimum launch power` | `+2 dBm = 1.59 mW` |

    - Alternative count: if the joints are taken as 25 rather than 24, the connector loss becomes 12.5 dB, the total 22.5 dB, and the launch power +2.5 dBm = 1.78 mW.
    - Note what the numbers show: the 24 connectors contribute 12 dB while 50 km of fibre contributes only 10 dB. The joints dominate the budget. Using fusion splices at about 0.05 dB each would reduce that 12 dB to roughly 1.2 dB — which is exactly why real long-haul links are fusion spliced rather than connectorised.

11. **কোন মাধ্যমে আলোর Pulse ব্যবহৃত হয়?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Light pulses are used in `optical fibre` (fibre optic cable).

    How it works
    - Data is transmitted as pulses of light: light on represents binary 1, light off represents binary 0.
    - The light is guided along the glass core by `total internal reflection`, because the core has a higher refractive index than the surrounding cladding.
    - The source is a laser diode (for long single-mode links) or an LED/VCSEL (for short multimode links); the detector is a PIN or avalanche photodiode.
    - Wavelengths used: 850 nm, 1310 nm and 1550 nm, the three low-loss windows of silica.

    Why light rather than electricity
    - Enormous bandwidth — terabits per second on one fibre with WDM.
    - Very low attenuation, about 0.2 dB/km at 1550 nm, so links run 80 km without a repeater.
    - Complete immunity to electromagnetic interference, and no crosstalk.
    - Excellent security, since tapping requires physically bending or breaking the fibre.

    - Other media that use light: infrared (remote controls, IrDA) and free-space optical links, but for data networking the answer is optical fibre.

12. **What is 3dB?** *[BTRC Assistant Director (Technical) 2019 compact it 1145-1146 (ET: N/A)]*

    Answer: 3 dB is a power ratio of `2` — it means the power has been doubled (a 3 dB gain) or halved (a 3 dB loss).

    The arithmetic
    ```
    dB = 10 log10 (P2 / P1)
    3 = 10 log10 (P2 / P1)
    P2 / P1 = 10^0.3 = 1.995 ≈ 2
    ```
    - So +3 dB doubles the power and −3 dB halves it. The approximation to exactly 2 is close enough that engineers use it constantly for mental arithmetic.

    Where the 3 dB point matters
    - `Half-power point / cut-off frequency.` The bandwidth of a filter, amplifier or antenna is defined between the frequencies at which the output falls 3 dB below its maximum — that is, where half the power remains. This is the standard definition of bandwidth.
    - `Antenna beamwidth` is quoted as the 3 dB beamwidth: the angle between the two directions where radiated power is half the peak.
    - `Optical splitters.` A 1:2 splitter divides the light equally, so each output is 3 dB below the input. Every doubling of the split ratio costs another 3 dB — a 1:4 splitter costs 6 dB, 1:8 costs 9 dB, 1:16 costs about 12–14 dB with excess loss.
    - `Link budgets` in fibre and radio design use 3 dB as the standard safety margin for ageing and temperature.

    Useful dB values to remember

    | dB | Power ratio |
    |---|---|
    | 3 dB | 2× |
    | 6 dB | 4× |
    | 10 dB | 10× |
    | 20 dB | 100× |
    | 30 dB | 1000× |
    | −3 dB | ½ |
    | −10 dB | 1/10 |

    - Note the difference between dB and dBm: `dB` is a ratio between two powers, while `dBm` is an absolute power referred to 1 mW, so 0 dBm = 1 mW and −20 dBm = 10 µW.
    - Caution for voltage: because power is proportional to voltage squared, a voltage ratio uses 20 log10, so 3 dB in voltage terms is a factor of √2 ≈ 1.414.

13. **From single mode fiber and multimode fiber which one is suitable for LAN?** *[NWPGCL Assistant Engineer (CSE) 2019 compact it 1153 (ET: RUET)]*

    Answer: `Multimode fibre` is the suitable choice for a LAN.

    Why multimode suits a LAN

    | Reason | Explanation |
    |---|---|
    | Distance matches the need | Multimode covers 300–550 m at 1 Gbps and 10 Gbps — far more than any building or campus backbone requires. Single-mode's 10–80 km reach is wasted indoors |
    | Lower equipment cost | Multimode uses cheap 850 nm VCSELs and LEDs; single-mode needs precision DFB lasers at 1310 or 1550 nm, which cost several times more. Transceivers dominate the cost of a short link |
    | Easier to work with | The core is 50 or 62.5 µm against 9 µm for single-mode, so alignment tolerance is far greater. Termination, splicing and connector cleaning are quicker and less error-prone |
    | Cheaper connectors and tools | Larger core means lower-precision, lower-cost connectors and less demanding test equipment |
    | Adequate bandwidth | OM3 supports 10 Gbps to 300 m, OM4 to 400 m, OM5 supports 40 and 100 Gbps with SWDM |

    Where single-mode is the right choice
    - Runs longer than about 550 m, links between buildings, campus backbones over a kilometre, WAN and metro links, and any route where capacity must scale far into the future.

    Comparison

    | Point | Multimode | Single-mode |
    |---|---|---|
    | Core diameter | 50 or 62.5 µm | 8–10 µm |
    | Cladding | 125 µm | 125 µm |
    | Light source | LED / VCSEL | Laser (DFB, FP) |
    | Wavelength | 850, 1300 nm | 1310, 1550 nm |
    | Distance | Up to 550 m (1 Gbps), 300–400 m (10 Gbps) | 10–80 km and beyond |
    | Bandwidth | High | Effectively unlimited |
    | Dispersion | Modal dispersion limits distance | No modal dispersion |
    | Cost of cable | Slightly higher | Slightly lower |
    | Cost of equipment | `Much lower` | Much higher |
    | Jacket colour convention | Orange (OM1/OM2), aqua (OM3/OM4), lime (OM5) | Yellow |
    | Typical use | LAN, data centre, building backbone | WAN, metro, FTTH, submarine |

    - Practical recommendation: use `OM4 multimode` for backbone runs inside a building or campus, and `single-mode` for anything between buildings or beyond about 500 m. Many organisations now install single-mode even for short runs, because the cable itself is cheap and it removes any future distance or speed limit.

## Network Address Translation (NAT) (13)

1. Network Address Translation (NAT) maps internal networks to the public internet.
   * (a) Explain the historical IP addressing limitation that made NAT a necessity globally.
   * (b) Explain the step-by-step logical translation process that occurs at a branch router when an internal employee (IP 192.168.1.5) sends a web request to an external server, and how the router correctly handles the returning response packet. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer:

   (a) The historical IP addressing limitation that made NAT necessary

   - IPv4 uses a `32-bit` address, so the entire address space is 2^32 ≈ `4.3 billion` addresses. That seemed enormous in 1981, when the internet joined a few hundred research machines.
   - `Classful addressing wasted most of it.` Only three block sizes existed: Class A (/8, 16.7 million hosts), Class B (/16, 65,534) and Class C (/24, 254). An organisation needing 500 hosts could not use a Class C, so it received a whole Class B and wasted more than 64,000 addresses. Millions of addresses were allocated but never used.
   - Large blocks were also handed out generously in the early years to universities, corporations and government bodies, and were never reclaimed.
   - The internet then grew far faster than anyone predicted — commercial use from the early 1990s, then home broadband, then mobile phones, and now billions of IoT devices, several per person.
   - By the early 1990s projections showed the address space would be exhausted within a few years. IANA's central pool ran out in `February 2011`, and the regional registries followed.

   - Three responses were adopted: `CIDR` (1993) to stop the classful wastage, `NAT` (RFC 1631, 1994) to let many hosts share one public address, and `IPv6` as the permanent fix. NAT was the immediate, deployable answer, and it is the reason IPv4 has survived three decades past its predicted exhaustion.
   - Together with RFC 1918 private addressing (10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16), NAT allows an entire organisation to operate behind a single public address.

   (b) Step-by-step translation at the branch router

   Assume the employee's PC is 192.168.1.5, the router's public address is 203.0.113.10, and the web server is 93.184.216.34.

   Outbound — request leaving the branch

   - Step 1 — the PC creates the packet.
   ```
   Source      192.168.1.5 : 51000   (a random ephemeral port)
   Destination 93.184.216.34 : 80
   ```
   - Step 2 — the PC compares its own address and the destination with its subnet mask. They are on different networks, so the packet goes to the default gateway, the branch router.
   - Step 3 — the router receives the packet on its `inside` interface and sees that the source is a private RFC 1918 address, which the internet will not route.
   - Step 4 — the router `rewrites the source` to its own public address and allocates a unique source port:
   ```
   Source      203.0.113.10 : 62145
   Destination 93.184.216.34 : 80
   ```
   - Step 5 — it creates an entry in the `NAT translation table`:

   | Inside local | Inside global | Outside global | Protocol |
   |---|---|---|---|
   | 192.168.1.5:51000 | 203.0.113.10:62145 | 93.184.216.34:80 | TCP |

   - Step 6 — because the IP header changed, the router recalculates the IP header checksum and the TCP checksum (which covers the addresses through the pseudo-header), then forwards the packet.

   Inbound — response returning to the branch

   - Step 7 — the web server replies to what it believes is the client:
   ```
   Source      93.184.216.34 : 80
   Destination 203.0.113.10 : 62145
   ```
   - Step 8 — the packet arrives on the router's `outside` interface. The router looks up the destination port 62145 in its translation table and finds the matching entry.
   - Step 9 — it `rewrites the destination` back to the original private address and port:
   ```
   Source      93.184.216.34 : 80
   Destination 192.168.1.5 : 51000
   ```
   - Step 10 — checksums are recalculated again, and the packet is forwarded out of the inside interface to the PC, which receives a reply that appears to have come straight from the server.
   - Step 11 — the entry is removed when the TCP connection closes, or after an idle timeout (typically 24 hours for TCP, 5 minutes for UDP).

   ```
      PC                    ROUTER (NAT)                      SERVER
   192.168.1.5              203.0.113.10                  93.184.216.34
        |                        |                              |
        |--- src 192.168.1.5:51000 -->|                          |
        |                        |--- src 203.0.113.10:62145 --->|
        |                        |<-- dst 203.0.113.10:62145 ----|
        |<-- dst 192.168.1.5:51000 ---|                          |
   ```

   - The port number is the key. Hundreds of internal hosts can share one public address because each conversation is given a different source port, and that port is what identifies the return path. This form of NAT is called `PAT` or NAT overload.

2. **Connection between Public IP to Private IP is called __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: The mapping between a public IP address and a private IP address is called `NAT — Network Address Translation`.

   - NAT is performed by a router or firewall sitting at the boundary between the private network and the internet. It rewrites the source address of outgoing packets and the destination address of returning ones.
   - It exists because IPv4 addresses are scarce: RFC 1918 private addresses are not routable on the internet, so they must be translated to a public address before leaving the organisation.

   Types

   | Type | Mapping | Use |
   |---|---|---|
   | Static NAT | One private to one public, permanently | A server that must be reachable from outside |
   | Dynamic NAT | Private addresses to a pool of public ones, as available | A group of users sharing several public addresses |
   | `PAT` / NAT overload | Many private to one public, distinguished by port number | Home and office routers — the common case |

   - The specific variant that lets many hosts share a single public address is `PAT (Port Address Translation)`, also called NAT overload. It is what every home router does.
   - Related term: `port forwarding` is static NAT applied to a single port, used to expose an internal service to the internet.

3. **What is NAT? Explain with topological diagram.** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 589 (ET: BUET)]*

   Answer:

   What is NAT
   - Network Address Translation is the process of rewriting the IP addresses in a packet's header as it passes through a router, so that hosts using private addresses can communicate with the public internet.
   - It was defined in RFC 1631 (1994) as a short-term answer to IPv4 address exhaustion, and it became permanent because it worked so well.
   - The router keeps a `translation table` recording which internal conversation corresponds to which external one.

   Topological diagram
   ```
           PRIVATE NETWORK                        PUBLIC INTERNET
          (RFC 1918 addresses)                  (globally routable)

      +-------------+
      | PC1         |
      | 192.168.1.10|\
      +-------------+ \
                       \      +----------------------+
      +-------------+    \    |    NAT ROUTER        |
      | PC2         |-----+---| inside: 192.168.1.1  |
      | 192.168.1.11|    /    | outside: 203.0.113.5 |-----> INTERNET
      +-------------+   /     |                      |       (web server
                       /      |  translation table   |        93.184.216.34)
      +-------------+ /       +----------------------+
      | PC3         |/
      | 192.168.1.12|
      +-------------+
   ```

   Translation table (PAT example)

   | Inside local | Inside global | Outside global |
   |---|---|---|
   | 192.168.1.10:51000 | 203.0.113.5:62001 | 93.184.216.34:80 |
   | 192.168.1.11:49500 | 203.0.113.5:62002 | 93.184.216.34:80 |
   | 192.168.1.12:52310 | 203.0.113.5:62003 | 142.250.190.78:443 |

   How it works
   - Outbound: the router replaces the private source address (and port) with its own public address and a unique port, records the mapping, recalculates the checksums, and forwards.
   - Inbound: the router matches the destination port against the table, restores the original private address and port, and delivers the packet internally.

   Types of NAT

   | Type | Mapping | Typical use |
   |---|---|---|
   | Static NAT | 1 private ↔ 1 public, fixed | A web or mail server that must be reachable from outside |
   | Dynamic NAT | Many private ↔ a pool of public | Users sharing a small block of public addresses |
   | PAT (overload) | Many private ↔ 1 public, by port | Home and office routers |

   Advantages and drawbacks
   - Advantages: conserves public addresses, hides the internal topology, allows internal renumbering without changing anything external, and lets one public address serve hundreds of hosts.
   - Drawbacks: breaks end-to-end connectivity, complicates peer-to-peer applications, VoIP and IPsec, needs application-layer gateways for protocols that embed addresses (FTP, SIP), adds router CPU load and state, and obscures which internal host generated traffic in external logs.

4. **Explain NAT? Differenc between IPv4 and IPv6.** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 549 (ET: BIBM)]*

   Answer:

   (a) NAT
   - Network Address Translation rewrites the IP addresses in packet headers as they cross a router, so that hosts with private RFC 1918 addresses can reach the public internet.
   - Outbound, the router replaces the private source address (and, with PAT, the source port) with its own public address and records the mapping in a translation table. Inbound, it uses that table to restore the original private address.
   - It exists because IPv4 has only 4.3 billion addresses and they ran out; NAT lets hundreds of hosts share one.

   Types

   | Type | Mapping | Use |
   |---|---|---|
   | Static NAT | One to one, permanent | A server reachable from the internet |
   | Dynamic NAT | Many to a pool | Shared public address block |
   | PAT / overload | Many to one, by port number | Home and office routers |

   - Advantages: conserves addresses, hides internal topology, allows internal renumbering freely.
   - Drawbacks: breaks end-to-end connectivity, complicates VoIP, peer-to-peer and IPsec, needs ALGs for FTP and SIP, and adds state and CPU load to the router.

   (b) IPv4 vs IPv6

   | Point | IPv4 | IPv6 |
   |---|---|---|
   | Address size | 32 bits | 128 bits |
   | Address space | ≈ 4.3 billion | ≈ 3.4 × 10^38 |
   | Notation | 192.168.1.1 | 2001:db8::1 |
   | Header | 20–60 bytes, 13 fields | 40 bytes fixed, 8 fields |
   | Checksum | Present | Removed |
   | Fragmentation | Sender or any router | Source only |
   | Configuration | Manual or DHCP | SLAAC or DHCPv6 |
   | Broadcast | Yes | None — multicast replaces it |
   | Address types | Unicast, multicast, broadcast | Unicast, multicast, anycast |
   | Address resolution | ARP | Neighbour Discovery (ICMPv6) |
   | IPsec | Optional | Built in |
   | `NAT` | `Essential` | `Not needed` |
   | QoS | ToS field | Traffic Class + Flow Label |
   | Loopback | 127.0.0.1 | ::1 |
   | Typical LAN prefix | /24 | /64 |

   - The connection between the two answers: NAT exists only because IPv4 addresses are scarce. IPv6 removes the scarcity, so NAT becomes unnecessary and true end-to-end connectivity is restored.

5. **What is NAT? Write down the list of private IP address.** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 717 (ET: N/A)]*

   Answer:

   What is NAT
   - Network Address Translation is the process by which a router rewrites the IP addresses in packet headers so that hosts using private addresses can communicate over the public internet.
   - Outbound, the private source address (and with PAT, the source port) is replaced by the router's public address, and the mapping is stored in a translation table. Inbound, the table is used in reverse to restore the original private address.
   - It was created in RFC 1631 to slow IPv4 address exhaustion, and it is why one public address from an ISP can serve an entire office.
   - Types: static NAT (one to one), dynamic NAT (many to a pool) and PAT or NAT overload (many to one, distinguished by port number).

   List of private IP addresses (RFC 1918)

   | Class | Range | CIDR | Mask | Number of addresses |
   |---|---|---|---|---|
   | A | 10.0.0.0 – 10.255.255.255 | 10.0.0.0/8 | 255.0.0.0 | 16,777,216 |
   | B | 172.16.0.0 – 172.31.255.255 | 172.16.0.0/12 | 255.240.0.0 | 1,048,576 |
   | C | 192.168.0.0 – 192.168.255.255 | 192.168.0.0/16 | 255.255.0.0 | 65,536 |

   - These addresses are dropped by internet routers, so they can be reused freely by every organisation, and they must be translated by NAT to reach the outside.
   - Related reserved ranges that are also non-routable: `169.254.0.0/16` (APIPA link-local, self-assigned when DHCP fails), `127.0.0.0/8` (loopback) and `100.64.0.0/10` (carrier-grade NAT space).
   - Common mistake to avoid: only 172.16 through 172.31 is private. 172.15.x.x and 172.32.x.x are public.

6. **Briefly explain Network Address Translation (NAT).** *[IDRA Assistant Network Administrator 2022 compact it 727 (ET: N/A)]*

   Answer: Network Address Translation is the technique by which a router rewrites the IP addresses in a packet's header as it crosses the boundary between a private network and the internet.

   Why it exists
   - IPv4 provides only about 4.3 billion addresses, and they were exhausted. RFC 1918 defines private ranges (10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16) that any organisation may reuse, but internet routers drop them. NAT translates them into a public address so that private hosts can still reach the outside.

   How it works
   - Outbound: the router replaces the private source address — and, with PAT, the source port — with its own public address and a unique port, and records the mapping in a translation table. It then recalculates the IP and TCP/UDP checksums.
   - Inbound: the router matches the returning packet's destination port against the table, restores the original private address and port, and forwards it internally.
   - Entries are removed when the connection closes or after an idle timeout.

   Types

   | Type | Mapping | Typical use |
   |---|---|---|
   | Static NAT | One private ↔ one public, permanent | A server that must be reachable from the internet |
   | Dynamic NAT | Many private ↔ a pool of public, as available | Sharing a small block of public addresses |
   | PAT / NAT overload | Many private ↔ one public, by port number | Every home and small office router |

   Advantages
   - Conserves scarce public IPv4 addresses — hundreds of hosts behind one address.
   - Hides the internal topology and addressing from outside.
   - Allows internal renumbering without informing anyone externally.
   - Provides a basic barrier: unsolicited inbound connections have no translation entry, so they are dropped.
   - Makes changing ISP easy, since only the router's outside address changes.

   Disadvantages
   - Breaks true end-to-end connectivity, which complicates peer-to-peer, VoIP, video calling and online gaming; STUN, TURN and port forwarding exist to work around it.
   - Interferes with IPsec, because rewriting the header invalidates integrity checks; NAT-Traversal was created for this.
   - Protocols that embed addresses in their payload — FTP, SIP, H.323 — need application-layer gateways.
   - Adds CPU load and per-flow state to the router, which can be exhausted.
   - Obscures which internal host generated traffic, complicating logging and forensics.

   - IPv6 removes the need for NAT entirely, because addresses are no longer scarce.

7. **(i) Network Address Translation (NAT) ছবি সহ ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 787 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   What NAT does
   - A router at the network boundary rewrites the private source address of outgoing packets into its own public address, records the mapping, and reverses the process for the replies. This lets hosts with non-routable RFC 1918 addresses use the internet.

   Diagram
   ```
      PRIVATE SIDE (inside)                       PUBLIC SIDE (outside)

     +--------------+
     | PC1          |
     | 192.168.1.10 |\
     +--------------+ \
                       \    +------------------------------+
     +--------------+   \   |        NAT ROUTER            |
     | PC2          |----+--| inside  192.168.1.1          |
     | 192.168.1.11 |   /   | outside 203.0.113.5          |====> INTERNET
     +--------------+  /    |                              |
                      /     |  +------------------------+  |
     +--------------+/      |  |  Translation table     |  |
     | PC3          |       |  +------------------------+  |
     | 192.168.1.12 |       +------------------------------+
     +--------------+
   ```

   Translation table

   | Inside local (private) | Inside global (public) | Outside global (destination) |
   |---|---|---|
   | 192.168.1.10:51000 | 203.0.113.5:62001 | 93.184.216.34:80 |
   | 192.168.1.11:49500 | 203.0.113.5:62002 | 93.184.216.34:80 |
   | 192.168.1.12:52310 | 203.0.113.5:62003 | 142.250.190.78:443 |

   Packet flow
   ```
   Outbound:  [192.168.1.10:51000 -> 93.184.216.34:80]
                 becomes
              [203.0.113.5:62001  -> 93.184.216.34:80]

   Inbound:   [93.184.216.34:80 -> 203.0.113.5:62001]
                 becomes
              [93.184.216.34:80 -> 192.168.1.10:51000]
   ```

   Terminology used in the table
   - `Inside local` — the private address as the internal host sees it.
   - `Inside global` — the public address the outside world sees for that host.
   - `Outside global` — the real public address of the destination.
   - `Outside local` — how the destination appears to the inside, usually the same as outside global.

   Types
   - Static NAT (one to one, fixed), dynamic NAT (many to a pool) and PAT / NAT overload (many to one, distinguished by port). PAT is what home routers use.

8. **(b) What is NAT? Mention its advantages.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 794 (ET: N/A)]*

   Answer:

   What is NAT
   - Network Address Translation is the rewriting of IP addresses in packet headers by a router at the boundary of a private network, so that hosts with private RFC 1918 addresses can communicate with the public internet.
   - Outbound, the private source address and port are replaced with the router's public address and a unique port, and the mapping is stored in a translation table. Inbound, the table is used in reverse.
   - Defined in RFC 1631 (1994) as a response to IPv4 address exhaustion.
   - Types: static NAT (one to one), dynamic NAT (many to a pool) and PAT or NAT overload (many to one, by port).

   Advantages of NAT

   - `Conserves public IPv4 addresses.` This is the primary purpose. Hundreds or thousands of internal hosts share one public address, which is the single biggest reason IPv4 has survived three decades past its predicted exhaustion.
   - `Reduces cost`, since an organisation buys one or a few public addresses from its ISP instead of one per device.
   - `Hides the internal network.` Outsiders see only the public address, so internal addressing, host count and topology are not exposed. This makes reconnaissance harder.
   - `Provides a basic security barrier.` An unsolicited inbound packet has no matching translation entry, so it is discarded. This is not a substitute for a firewall, but it does stop casual scanning.
   - `Freedom to renumber internally.` The internal addressing plan can be redesigned without informing anyone outside, and without renegotiating addresses with the ISP.
   - `Simplifies changing ISP.` Only the router's outside address changes; not a single internal host needs reconfiguring.
   - `Allows merging of networks` that happen to use the same private ranges, by translating one side.
   - `Load distribution and redundancy`, since static NAT can map one public address to a pool of internal servers.
   - `Consistent internal addressing` for organisations with many branches, all of which can use the same private scheme.

   Disadvantages, for completeness
   - Breaks end-to-end connectivity, complicating peer-to-peer, VoIP and gaming; interferes with IPsec; needs ALGs for FTP and SIP; adds CPU load and state to the router; and makes it hard to attribute external traffic to a specific internal host.

9. **(a) Why do we need NAT? What are its advantages? Draw a topology diagram to explain NAT.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 799 (ET: N/A)]*

   Answer:

   Why we need NAT
   - `IPv4 address exhaustion.` The 32-bit address space provides only about 4.3 billion addresses, and classful allocation wasted most of them. IANA's central pool ran out in February 2011. There are far more devices than addresses.
   - `Private addresses are not routable.` RFC 1918 ranges (10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16) can be reused by every organisation, but internet routers drop them. Something must translate them into a public address, and that is NAT.
   - `Cost.` Public addresses must be leased from an ISP. NAT lets one address serve an entire office.
   - `Security and privacy.` Internal addressing and topology stay hidden, and unsolicited inbound traffic has no translation entry, so it is dropped.
   - `Flexibility.` Internal renumbering, changing ISP, or merging two networks that use the same private range all become manageable.

   Advantages
   - Conserves public addresses; reduces cost; hides internal topology; blocks unsolicited inbound connections by default; allows free internal renumbering; makes changing ISP trivial; and permits a common addressing scheme across all branches.

   Topology diagram
   ```
       PRIVATE NETWORK                                PUBLIC INTERNET
      (RFC 1918 addresses)

     +---------------+
     | PC1           |
     | 192.168.1.10  |\
     +---------------+ \
                        \    +-----------------------------+
     +---------------+    \   |       NAT ROUTER            |
     | PC2           |-----+--| inside  192.168.1.1         |
     | 192.168.1.11  |    /   | outside 203.0.113.5         |=====> INTERNET
     +---------------+   /    |                             |        |
                        /     |  NAT / PAT translation      |        v
     +---------------+ /      |  table                      |   Web server
     | Printer       |/       +-----------------------------+   93.184.216.34
     | 192.168.1.20  |
     +---------------+
   ```

   Translation table

   | Inside local | Inside global | Outside global |
   |---|---|---|
   | 192.168.1.10:51000 | 203.0.113.5:62001 | 93.184.216.34:80 |
   | 192.168.1.11:49500 | 203.0.113.5:62002 | 93.184.216.34:80 |

   - Outbound, the source 192.168.1.10:51000 becomes 203.0.113.5:62001. Inbound, the reply addressed to 203.0.113.5:62001 is rewritten back to 192.168.1.10:51000.
   - The port number is what allows many hosts to share one public address; this variant is called PAT or NAT overload.

   Disadvantages worth mentioning
   - Breaks end-to-end connectivity, complicates VoIP, peer-to-peer and IPsec, requires ALGs for FTP and SIP, and adds state and CPU load to the router. IPv6 removes the need for NAT entirely.

10. **Why do we need NAT? Draw a topology diagram to explain NAT.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 841 (ET: N/A)]*

    Answer:

    Why we need NAT
    - `IPv4 addresses ran out.` The 32-bit space gives about 4.3 billion addresses, and classful allocation wasted most of them. IANA exhausted its pool in February 2011, while the number of connected devices kept multiplying.
    - `Private addresses cannot be routed on the internet.` RFC 1918 ranges are reusable by everyone precisely because internet routers discard them, so they must be translated before leaving the organisation.
    - `Cost.` Public addresses are leased from an ISP; NAT lets one address serve hundreds of hosts.
    - `Security and privacy.` The internal addressing and topology are hidden, and unsolicited inbound packets have no translation entry, so they are dropped.
    - `Administrative flexibility.` Internal renumbering, changing ISP, or merging two networks using the same private range are all handled without touching internal hosts.

    Topology diagram
    ```
       INSIDE (private)                                OUTSIDE (public)

      +---------------+
      | PC1           |
      | 192.168.1.10  |\
      +---------------+ \
                         \   +------------------------------+
      +---------------+    \  |        NAT ROUTER            |
      | PC2           |-----+-| inside  192.168.1.1 (e0)     |
      | 192.168.1.11  |    /  | outside 203.0.113.5 (s0)     |======> INTERNET
      +---------------+   /   |                              |
                         /    |  translation table maps      |
      +---------------+  /    |  private:port <-> public:port |
      | PC3           | /     +------------------------------+
      | 192.168.1.12  |/
      +---------------+
    ```

    Packet flow
    ```
    Outbound
      PC1 sends   : src 192.168.1.10:51000  dst 93.184.216.34:80
      Router sends: src 203.0.113.5:62001   dst 93.184.216.34:80

    Inbound
      Server sends: src 93.184.216.34:80    dst 203.0.113.5:62001
      Router sends: src 93.184.216.34:80    dst 192.168.1.10:51000
    ```

    Translation table

    | Inside local | Inside global | Outside global |
    |---|---|---|
    | 192.168.1.10:51000 | 203.0.113.5:62001 | 93.184.216.34:80 |
    | 192.168.1.11:49500 | 203.0.113.5:62002 | 142.250.190.78:443 |
    | 192.168.1.12:52310 | 203.0.113.5:62003 | 8.8.8.8:53 |

    - The unique source port is what makes many-to-one sharing possible; the router uses it to identify which internal host a reply belongs to.

11. **What is PAT? How does a network PAT work?** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 841 (ET: N/A)]*

    Answer:

    What is PAT
    - PAT (Port Address Translation), also called `NAT overload`, is the form of NAT in which `many private IP addresses share a single public IP address`, distinguished by using a different source port number for each conversation.
    - It is the variant used by virtually every home and small office router, and it is the reason one public address from an ISP can serve an entire building.

    How PAT works, step by step

    - Step 1 — an internal host sends a packet:
    ```
    src 192.168.1.10 : 51000    dst 93.184.216.34 : 80
    ```
    - Step 2 — the router receives it on the inside interface and sees a private source address.
    - Step 3 — it replaces the source address with its own public address and allocates a `unique source port` from its pool (typically 1024–65535):
    ```
    src 203.0.113.5 : 62001     dst 93.184.216.34 : 80
    ```
    - Step 4 — it records the mapping in the translation table, keyed by that unique port.
    - Step 5 — it recalculates the IP header checksum and the TCP/UDP checksum, then forwards the packet.
    - Step 6 — the reply arrives addressed to 203.0.113.5:62001. The router looks up port 62001, finds the entry, and rewrites the destination back to 192.168.1.10:51000.
    - Step 7 — the entry is removed when the connection closes or after an idle timeout.

    Translation table

    | Inside local | Inside global | Outside global |
    |---|---|---|
    | 192.168.1.10:51000 | 203.0.113.5:`62001` | 93.184.216.34:80 |
    | 192.168.1.11:51000 | 203.0.113.5:`62002` | 93.184.216.34:80 |
    | 192.168.1.12:44120 | 203.0.113.5:`62003` | 142.250.190.78:443 |

    - Note rows 1 and 2: both hosts happened to choose the same source port 51000, but the router allocated different global ports, so the replies are never confused. This port allocation is the whole trick.

    NAT vs PAT

    | Point | NAT (static or dynamic) | PAT (overload) |
    |---|---|---|
    | Mapping | One to one, or many to a pool | Many to one |
    | Uses port numbers | No | Yes — this is the key difference |
    | Public addresses needed | One per concurrent host | Just one |
    | Address saving | Limited | Very large |
    | Cost | Higher | Lowest |
    | Typical use | Servers, address pools | Home and office internet access |

    - Capacity: roughly 64,000 ports are available, so in theory one public address supports tens of thousands of simultaneous connections; in practice a few thousand hosts share one address comfortably.
    - Limitation: an internal host cannot be reached from outside unless a `port forwarding` rule (static PAT) is configured, which is why hosting a server behind PAT requires explicit setup.

12. **What is NAT?** *[BREB Assistant Hardware & Network Engineer 2019 compact it 1124 (ET: BREB)]*

    Answer: NAT (Network Address Translation) is the process by which a router rewrites the IP addresses in a packet's header as it passes between a private network and the public internet.

    Purpose
    - IPv4 has only about 4.3 billion addresses, and they were exhausted. RFC 1918 defines private ranges — 10.0.0.0/8, 172.16.0.0/12 and 192.168.0.0/16 — that every organisation may reuse, but internet routers drop them. NAT translates them into a public address so private hosts can still reach the outside.

    How it works
    - Outbound: the private source address, and with PAT the source port, is replaced by the router's public address and a unique port. The mapping is recorded in the translation table and the checksums are recalculated.
    - Inbound: the router matches the returning packet against the table and restores the original private address and port.

    Types

    | Type | Mapping | Use |
    |---|---|---|
    | Static NAT | One to one, fixed | A server that must be reachable from outside |
    | Dynamic NAT | Many to a pool, as available | Sharing a block of public addresses |
    | PAT / overload | Many to one, by port | Home and office routers |

    Advantages
    - Conserves public addresses, reduces cost, hides internal topology, drops unsolicited inbound traffic by default, and allows internal renumbering or a change of ISP with no internal disruption.

    Disadvantages
    - Breaks end-to-end connectivity, complicates VoIP, peer-to-peer and online gaming, interferes with IPsec, requires application-layer gateways for FTP and SIP, adds CPU load and state to the router, and makes external logs point at a shared address rather than a specific host.

    - IPv6, with 3.4 × 10^38 addresses, removes the need for NAT altogether.

13. **Show the translation process of a NAT Box.** *[Agrani Bank Ltd. Officer (ICT) 2017 compact it 1224 (ET: N/A)]*

    Answer: The NAT box (router) sits between the private network and the internet and rewrites addresses in both directions, using a translation table to keep track.

    The translation process
    ```
       INSIDE                    NAT BOX                       OUTSIDE
      192.168.1.10           203.0.113.5                  93.184.216.34
           |                       |                             |
      (1)  |--- src 192.168.1.10:51000 ------->|                 |
           |    dst 93.184.216.34:80           |                 |
           |                       |                             |
      (2)  |            [creates table entry]                    |
           |                       |                             |
      (3)  |                       |--- src 203.0.113.5:62001 -->|
           |                       |    dst 93.184.216.34:80     |
           |                       |                             |
      (4)  |                       |<-- src 93.184.216.34:80 ----|
           |                       |    dst 203.0.113.5:62001    |
           |                       |                             |
      (5)  |            [looks up port 62001 in the table]       |
           |                       |                             |
      (6)  |<-- src 93.184.216.34:80 ----------|                 |
           |    dst 192.168.1.10:51000         |                 |
    ```

    Step by step
    - (1) The internal host sends a packet with its private source address and an ephemeral source port.
    - (2) The NAT box sees a private source address on the inside interface, allocates a free port on its public address, and creates an entry in the translation table.
    - (3) It rewrites the source to `public address : allocated port`, recalculates the IP header checksum and the TCP/UDP checksum (which covers the addresses through the pseudo-header), and forwards the packet.
    - (4) The external server replies to the public address and port, since that is all it ever saw.
    - (5) The NAT box matches the destination port against the table and finds the corresponding internal host.
    - (6) It rewrites the destination back to the original private address and port, recalculates the checksums again, and delivers the packet inside.
    - The entry is deleted when the TCP connection closes, or after an idle timeout — commonly 24 hours for TCP and about 5 minutes for UDP.

    Translation table structure

    | Inside local | Inside global | Outside global | Protocol |
    |---|---|---|---|
    | 192.168.1.10:51000 | 203.0.113.5:62001 | 93.184.216.34:80 | TCP |
    | 192.168.1.11:51000 | 203.0.113.5:62002 | 93.184.216.34:80 | TCP |
    | 192.168.1.12:44120 | 203.0.113.5:62003 | 8.8.8.8:53 | UDP |

    Terminology
    - `Inside local` — the private address as seen inside.
    - `Inside global` — the public address the outside world sees for that host.
    - `Outside global` — the real public address of the destination.
    - `Outside local` — how the destination appears from inside; usually identical to outside global.

    - Key point: the unique `source port` is what allows many internal hosts to share a single public address. Rows 1 and 2 above show two hosts that chose the same internal port, yet the router keeps them separate by allocating different global ports.

## Flow Control & Data Link Layer (Stop-and-Wait) (12)

1. A single-mode optical fiber communication link connects two locations 250\text{ km} apart using WDM technology with 50 channels, where each channel provides a bit rate of 10\text{ Gbps}. The refractive index of the fiber is 1.5, and data is transmitted using the Stop-and-Wait protocol. A 1\text{ GB} file is divided into suitable data frames, and after successfully receiving each frame, the receiver sends a 54-byte acknowledgment (ACK) back to the sender. Assuming no processing or queuing delay, determine the total time required to completely transfer the 1\text{ GB} file, including data transmission time, propagation delay, ACK transmission time, and the Stop-and-Wait waiting time. [BSCCPL AME 21-08-2026 (BUET)]

   Answer: Stop-and-Wait sends one frame, then waits idle for a full round trip before sending the next. The whole answer turns on that.

   Assumptions stated (the frame size is not given in the question)
   - Frame size = 1500 bytes, the standard Ethernet MTU. The 54-byte ACK is consistent with a minimum Ethernet + IP + TCP acknowledgement.
   - 1 GB = 10^9 bytes.
   - Speed of light in vacuum c = 3 × 10^8 m/s.

   Step 1 — total link bandwidth
   ```
   BW = 50 channels × 10 Gbps = 500 Gbps = 5 × 10^11 bps
   ```

   Step 2 — propagation speed and delay
   ```
   v  = c / n = (3 × 10^8) / 1.5 = 2 × 10^8 m/s
   Tp = distance / v = 250,000 / (2 × 10^8) = 1.25 × 10^-3 s = 1.25 ms
   ```

   Step 3 — transmission time of one data frame
   ```
   Tt(data) = 1500 × 8 / (5 × 10^11) = 12,000 / (5 × 10^11)
            = 2.4 × 10^-8 s = 24 nanoseconds
   ```

   Step 4 — transmission time of the ACK
   ```
   Tt(ack) = 54 × 8 / (5 × 10^11) = 432 / (5 × 10^11)
           = 8.64 × 10^-10 s = 0.864 nanoseconds
   ```

   Step 5 — time for one complete Stop-and-Wait cycle
   ```
   Tcycle = Tt(data) + Tp + Tt(ack) + Tp
          = 24 ns + 1.25 ms + 0.864 ns + 1.25 ms
          = 2.500024864 ms
   ```

   Step 6 — number of frames
   ```
   Number of frames = 10^9 / 1500 = 666,666.67  ->  666,667 frames
   ```

   Step 7 — total transfer time
   ```
   Total = 666,667 × 2.500024864 ms
         = 1,666,684 ms
         = 1666.68 seconds
         ≈ 27.8 minutes
   ```

   Summary

   | Quantity | Value |
   |---|---|
   | Total bandwidth | 500 Gbps |
   | Propagation speed | 2 × 10^8 m/s |
   | Propagation delay (one way) | 1.25 ms |
   | Data frame transmission time | 24 ns |
   | ACK transmission time | 0.864 ns |
   | One Stop-and-Wait cycle | 2.500025 ms |
   | Number of frames | 666,667 |
   | `Total transfer time` | `≈ 1666.7 s ≈ 27.8 minutes` |

   What the numbers show — the real point of the question

   - Protocol efficiency
   ```
   η = Tt(data) / Tcycle = 24 ns / 2.500025 ms = 0.00096 %
   ```
   - Effective throughput
   ```
   = (10^9 × 8 bits) / 1666.7 s ≈ 4.8 Mbps
   ```
   - So a 500 Gbps link delivers about `4.8 Mbps` — roughly `one hundred-thousandth` of its capacity. The link spends 99.999 percent of its time idle, waiting for acknowledgements.
   - The cause is the enormous bandwidth-delay product. `BDP = 500 Gbps × 2.5 ms = 1.25 Gbit = 156 MB` of data could be in flight, yet Stop-and-Wait allows only 1500 bytes at a time.

   The fix
   - Use a sliding window with a window large enough to fill the pipe:
   ```
   Window needed = BDP / frame size = 156 MB / 1500 B ≈ 104,000 frames
   ```
   - With such a window the transfer would take about `16 ms` instead of 27.8 minutes. This is exactly why real high-speed links use Go-Back-N or Selective Repeat with window scaling, never Stop-and-Wait.
   - Note also that a much larger frame size (jumbo frames, or aggregating the file into far fewer frames) would reduce the frame count proportionally, since the cost is per frame, not per byte.

2. **Using an explanation of the difference between flow-control and congestion control, discuss the impact of a stable end-to-end latency.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 424 (ET: BIBM)]*

   Answer:

   Flow control vs congestion control

   | Point | Flow control | Congestion control |
   |---|---|---|
   | Problem solved | A fast `sender` overwhelming a slow `receiver` | Too much traffic overwhelming the `network` |
   | Scope | End to end, between two hosts | Network wide, involving all flows |
   | Who is protected | The receiver's buffer | The routers and links in between |
   | Signal used | The receiver's advertised window in each ACK | Inferred from packet loss, delay or ECN marks |
   | Mechanism | Sliding window, receive window (rwnd) | Congestion window (cwnd), slow start, AIMD |
   | Layer | Transport (TCP), and Data Link on a single hop | Transport, with help from the Network layer |
   | Analogy | Do not pour faster than the glass can hold | Do not send more cars than the road can carry |

   - In TCP both act together: the sender may have in flight at most `min(rwnd, cwnd)` bytes. Flow control comes from the receiver, congestion control from the sender's own estimate of the network.

   Impact of stable end-to-end latency

   - `Accurate RTO estimation.` TCP computes its retransmission timeout from a smoothed RTT and its variance: `RTO = SRTT + 4 × RTTVAR`. When latency is stable, RTTVAR is small, so the timeout is tight and a genuine loss is detected quickly. When latency swings, RTTVAR grows and the timeout becomes conservative, so recovery from real loss is slow.

   - `Fewer spurious retransmissions.` A sudden latency spike can make an ACK arrive after the timer expires, so the sender retransmits a packet that was never lost. That wastes bandwidth and, worse, halves the congestion window unnecessarily. Stable latency avoids this entirely.

   - `Congestion control behaves correctly.` Loss-based algorithms interpret delay and loss as congestion signals. Stable latency means the signals are trustworthy, so the congestion window grows smoothly instead of oscillating. Delay-based algorithms such as BBR and Vegas depend on stable measurements even more directly.

   - `Higher and steadier throughput.` Throughput is roughly `window / RTT`. A stable RTT gives a stable, predictable rate; a fluctuating RTT makes throughput fluctuate even when no packets are lost.

   - `Flow control windows can be sized correctly.` The right receive window is the bandwidth-delay product. If the RTT is stable, one buffer size is correct all the time. If it varies, the window is either too small (wasting capacity) or too large (adding queuing delay and bufferbloat).

   - `Real-time applications work properly.` Voice and video care about `jitter`, which is precisely the variation in latency. Stable latency means a small jitter buffer, which means low end-to-end delay and natural conversation. Unstable latency forces a large jitter buffer, adding delay, or causes audible gaps.

   - `Predictable application behaviour.` Timeouts, retries and SLA guarantees can all be set tightly. Databases, financial trading and industrial control depend on this.

   - Conclusion: stable latency is worth more than merely low average latency. A link with 100 ms constant delay is easier to work with, and often performs better, than one averaging 50 ms but swinging between 10 and 300 ms.

3. **(খ) Congestion কী? Network-এ কীভাবে Congestion নিয়ন্ত্রণ করা যায়? আলোচনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 415 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   What is congestion
   - Congestion occurs when the amount of traffic offered to a network exceeds its capacity to carry it. Router buffers fill, queuing delay rises, and once the buffers overflow, packets are dropped.
   - The consequences: increased delay and jitter, packet loss, retransmissions that add still more traffic, and falling throughput. If unchecked this leads to `congestion collapse`, where the network is fully occupied yet almost no useful data is delivered.
   - Causes: too many sources sending at once, a bottleneck link, insufficient router buffer or CPU, a slow outgoing link fed by fast incoming ones, and broadcast storms.

   How congestion is controlled

   Open-loop methods — prevent it before it happens
   - `Admission control` — a new flow is admitted only if the network has spare capacity. Used in connection-oriented networks such as ATM and MPLS.
   - `Traffic shaping` — smooth bursty traffic to a steady rate before it enters the network.
     - `Leaky bucket` — output is at a constant rate regardless of how bursty the input is. Simple, but it cannot pass a legitimate burst.
     - `Token bucket` — tokens accumulate at a fixed rate up to a limit; a packet needs a token to be sent. This allows controlled bursts, which is why it is preferred in practice.
   - `Traffic policing` — measure and drop or mark traffic that exceeds an agreed rate at the network boundary.
   - `Resource reservation` — RSVP reserves bandwidth along the path before the flow starts.

   Closed-loop methods — react once it is detected
   - `TCP congestion control` — the main mechanism on the internet:
     - Slow start: the congestion window doubles each RTT until it reaches the threshold.
     - Congestion avoidance: growth becomes linear, about one MSS per RTT.
     - Fast retransmit and fast recovery: three duplicate ACKs cause immediate retransmission and the window is halved rather than reset.
     - The overall pattern is `AIMD` — additive increase, multiplicative decrease.
   - `Choke packets` — a congested router sends a message back telling the source to slow down.
   - `ECN (Explicit Congestion Notification)` — routers mark packets instead of dropping them, so the sender reduces its rate before any loss occurs.
   - `Backpressure` — congestion is signalled hop by hop back towards the source.
   - `Random Early Detection (RED)` — routers drop packets randomly as the queue grows, before it is full, so that TCP flows slow down at different moments instead of all together (avoiding global synchronisation).

   Supporting measures
   - `QoS and priority queuing` — protect voice and video with defined classes.
   - `Load balancing` across multiple paths, and `capacity upgrade` where the bottleneck is permanent.
   - `Network segmentation and VLANs` to limit broadcast traffic.
   - `Caching and CDNs` to keep traffic local instead of crossing congested links.

4. **Unit of data link layer?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

   Answer: The unit of data at the Data Link layer is the `frame`.

   - A frame is the PDU (Protocol Data Unit) of Layer 2. The Data Link layer takes a packet from the Network layer and wraps it with a header and a trailer.
   - Header: destination MAC address, source MAC address and a type/length field.
   - Trailer: the `FCS` (Frame Check Sequence), a CRC used for error detection.
   ```
   | Dest MAC | Src MAC | Type | Data (packet) | FCS |
   ```

   PDU names at every layer

   | Layer | PDU |
   |---|---|
   | Application / Presentation / Session | Data |
   | Transport | Segment (TCP) / Datagram (UDP) |
   | Network | Packet |
   | `Data Link` | `Frame` |
   | Physical | Bit |

   - Memory aid: Data, Segment, Packet, Frame, Bits.
   - Ethernet frame sizes: minimum 64 bytes, maximum 1518 bytes (1522 with a VLAN tag), of which the payload is 46 to 1500 bytes.

5. **(ক) নেটওয়ার্কে ডাটা প্যাকেটে trailer কোথায় এবং কেন ব্যবহার করা হয়? উদাহরণ দিন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 775 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   Where the trailer is used
   - The `trailer` is placed at the `end` of a frame, after the data, and it is added by the `Data Link layer` (Layer 2). Only Layer 2 adds a trailer; every other layer adds a header only.
   ```
   | Header (MAC addresses, type) | Data (payload) | TRAILER (FCS) |
   ```

   Why a trailer is used
   - `Error detection.` The trailer carries the FCS (Frame Check Sequence), a 32-bit CRC computed over the whole frame. The receiver recomputes the CRC and compares. If they differ, the frame was corrupted in transit and is discarded.
   - `It must come last.` The sender can only compute the CRC once every byte of the frame is known, so it is appended at the end rather than placed in the header. This also lets the receiver compute the CRC on the fly as the bits arrive, and check it the moment the frame ends — which is what makes hardware CRC checking possible at line rate.
   - `Frame delimiting.` In some protocols the trailer also marks where the frame ends, for example the closing flag `01111110` in HDLC and PPP.

   Examples

   | Protocol | Trailer contents |
   |---|---|
   | Ethernet (IEEE 802.3) | 4-byte FCS (CRC-32) |
   | HDLC | 2-byte FCS plus the closing flag 01111110 |
   | PPP | 2 or 4-byte FCS plus the flag |
   | Token Ring | FCS, end delimiter, frame status |

   Ethernet frame with the trailer shown
   ```
   | Preamble 7 | SFD 1 | Dest MAC 6 | Src MAC 6 | Type 2 | Data 46-1500 | FCS 4 |
                                                                           ^^^^^
                                                                          TRAILER
   ```

   - Note the contrast: TCP and IP put their checksums inside the header, because those checksums cover only the header (IP) or can be computed in advance. Layer 2 covers the entire frame, so its check value can only be a trailer.

6. **How STP works? Explain congestion control algorithm.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 842-843 (ET: N/A)]*

   Answer:

   (a) How STP works
   - STP (Spanning Tree Protocol, IEEE 802.1D) prevents `switching loops` in a network with redundant links. Without it, a loop causes a broadcast storm, MAC table instability and multiple frame copies — and because an Ethernet frame has no TTL, the storm never stops on its own.

   Steps
   - Step 1 — `Elect the root bridge.` Every switch sends BPDUs containing its Bridge ID (priority + MAC address). The switch with the `lowest Bridge ID` becomes the root. Default priority is 32768, so the lowest MAC wins unless priority is configured.
   - Step 2 — `Choose a root port on every non-root switch.` This is the port with the lowest cumulative path cost to the root. Cost is based on bandwidth: 10 Gbps = 2, 1 Gbps = 4, 100 Mbps = 19, 10 Mbps = 100.
   - Step 3 — `Choose a designated port on every segment.` The port on the switch with the lowest cost to the root forwards for that segment.
   - Step 4 — `Block every remaining port.` These become blocking ports; they receive BPDUs but forward no data. The result is a loop-free tree.
   - Step 5 — `Reconverge on failure.` If a link fails, BPDUs stop arriving, and a previously blocked port is brought into forwarding.

   Port states: Blocking (20 s) -> Listening (15 s) -> Learning (15 s) -> Forwarding, so classic STP takes about `50 seconds` to converge.

   Improvements
   - `RSTP` (802.1w) converges in a few seconds; `MSTP` (802.1s) runs one instance per group of VLANs; PortFast, UplinkFast and BackboneFast speed up specific cases.

   (b) Congestion control algorithm
   - TCP infers congestion from packet loss and adjusts its congestion window (cwnd). It sends the minimum of cwnd and the receiver's advertised window.

   - `1. Slow start` — cwnd starts at 1 MSS and doubles every RTT (it increases by 1 MSS per ACK). Growth is exponential and continues until cwnd reaches ssthresh or a loss occurs.
   - `2. Congestion avoidance` — beyond ssthresh, cwnd grows linearly, about 1 MSS per RTT, probing carefully for extra capacity.
   - `3. Fast retransmit` — three duplicate ACKs indicate a single lost segment; it is resent immediately without waiting for the timer.
   - `4. Fast recovery` — after a fast retransmit, ssthresh is halved and cwnd is set to it, so transmission continues at a reduced rate. A full timeout is treated as far more serious: cwnd drops to 1 MSS and slow start begins again.

   ```
   cwnd
     |          /\        /\
     |         /  \      /  \      <- halve on loss, continue (fast recovery)
     |    ____/    \    /
     |   /  linear  \  /
     |  / exponential\/
     +--------------------------> time
   ```
   - The overall behaviour is `AIMD` — additive increase, multiplicative decrease — which shares capacity roughly fairly and prevents congestion collapse.
   - Modern variants: Reno, NewReno, CUBIC (the Linux default) and BBR (which models bandwidth and RTT rather than relying on loss).
   - Network-side help: RED drops packets early to avoid global synchronisation, and ECN marks packets instead of dropping them.

7. **Host A is sending data to Host B over a full duplex link. A and B are using the sliding window protocol for flow control. The send and receive window size are 5 packets each. Data packets (sent only from A to B) are all 1000 bytes long and transmission time for such a packet is 50\mu\text{s}. Acknowledgement packets (sent only from B to A) are very small and require negligible transmission time. The propagation delay over the link is 200\mu\text{s}. What is the maximum achievable throughput in this communication?** *[BAUST Assistant Programmer 2021 compact it 918 (ET: N/A)]*

   Answer:

   Given
   - Window size N = 5 packets
   - Packet size = 1000 bytes = 8000 bits
   - Transmission time Tt = 50 µs
   - Propagation delay Tp = 200 µs
   - ACK transmission time = negligible

   Step 1 — time for one complete cycle
   - The sender transmits, the first packet propagates, and the ACK propagates back:
   ```
   Tcycle = Tt + 2 × Tp
          = 50 + 2(200)
          = 450 µs
   ```

   Step 2 — data sent in one cycle
   - The sliding window allows 5 packets before an acknowledgement is required:
   ```
   Data = 5 × 1000 bytes = 5000 bytes = 40,000 bits
   ```

   Step 3 — maximum achievable throughput
   ```
   Throughput = data per cycle / cycle time
              = 40,000 bits / 450 × 10^-6 s
              = 88.89 × 10^6 bps
              = 88.89 Mbps
   ```

   - Answer: `88.89 Mbps` (about 88.9 Mbps).

   Verification by the efficiency formula
   ```
   a  = Tp / Tt = 200 / 50 = 4
   η  = N / (1 + 2a) = 5 / (1 + 8) = 5/9 = 0.5556

   Link bandwidth = 8000 bits / 50 µs = 160 Mbps
   Throughput     = η × bandwidth = 0.5556 × 160 = 88.89 Mbps
   ```
   - The two methods agree.

   Interpretation
   - The link itself can carry 160 Mbps, but only 88.89 Mbps is achieved — an efficiency of 55.6 percent — because the window is too small to keep the pipe full.
   - To reach 100 percent efficiency the window must satisfy `N >= 1 + 2a = 9`, so a window of `9 packets` would fill the link completely and give the full 160 Mbps.
   - With N = 1 the protocol becomes Stop-and-Wait, giving 1/9 = 11.1 percent efficiency and only 17.8 Mbps.

8. **What is the piggybacking and MAC Address?** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 921 (ET: N/A)]*

   Answer:

   Piggybacking
   - Piggybacking is the technique of `carrying an acknowledgement inside an outgoing data frame` rather than sending a separate ACK frame.
   - It is possible because most communication is bidirectional. When B receives data from A and also has data of its own to send to A, B attaches the acknowledgement for A's frame to its own data frame, in the ACK field of the header.

   ```
   WITHOUT piggybacking          WITH piggybacking
   A --- data ------> B          A --- data --------> B
   A <-- ACK -------- B          A <-- data + ACK --- B
   A <-- data ------- B
   A --- ACK -------> B
   ```

   - Advantages: fewer frames on the medium, better bandwidth utilisation, and less processing overhead. The saving is significant, because an ACK frame carries almost no payload but still pays the full header cost.
   - Disadvantage: the receiver must wait a little for outgoing data to appear. If it waits too long, the sender's timer expires and the frame is retransmitted unnecessarily. The solution is a short timer — if no data is ready before it expires, a separate ACK is sent anyway.
   - Where it is used: TCP (the ACK field is part of every segment header), HDLC, and sliding window protocols generally.

   MAC address
   - A MAC (Media Access Control) address is the 48-bit physical address burned into a network interface card by its manufacturer, used to identify a device inside a local network.
   - Format: 12 hexadecimal digits, `00:1A:2B:3C:4D:5E`. The first 24 bits are the OUI identifying the vendor; the last 24 bits are the card's serial number.
   - It works at the Data Link layer (Layer 2), and switches use it to forward frames to the correct port.
   - It is valid only within one local segment — it is never carried across a router, and is rewritten at every hop.
   - Types: unicast (I/G bit = 0), multicast (I/G bit = 1) and broadcast (FF:FF:FF:FF:FF:FF).
   - ARP is the protocol that finds the MAC address belonging to a known IP address. `ipconfig /all` or `ip link` shows it.

9. **(i) Congestion Control কী? কী কী ভাবে Congestion Control করা যায়?** *[BPSC Assistant Network Engineer 2020 compact it 950 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   What is congestion control
   - Congestion occurs when the traffic offered to the network exceeds its capacity. Router queues fill, delay rises, and when the buffers overflow, packets are dropped.
   - Congestion control is the set of techniques that keep the total load within the network's capacity. It protects the `network`, which is what distinguishes it from flow control, which protects the `receiver`.
   - Without it, retransmissions add further traffic and the network can reach `congestion collapse`, in which the links are fully busy yet almost no useful data is delivered.

   Methods of congestion control

   Open-loop (prevention)
   - `Admission control` — accept a new flow only if capacity exists. Used in ATM and MPLS.
   - `Traffic shaping` — smooth bursts before they enter the network.
     - `Leaky bucket`: output flows at a constant rate whatever the input. Simple, but cannot pass a legitimate burst.
     - `Token bucket`: tokens accumulate at a fixed rate; a packet needs a token. Allows controlled bursts, so it is preferred.
   - `Traffic policing` — measure at the boundary and drop or mark traffic above the agreed rate.
   - `Resource reservation` — RSVP reserves bandwidth along the path in advance.

   Closed-loop (reaction)
   - `TCP congestion control`, the mechanism that actually keeps the internet stable:
     - Slow start — cwnd doubles every RTT.
     - Congestion avoidance — cwnd grows by about 1 MSS per RTT.
     - Fast retransmit — three duplicate ACKs trigger immediate retransmission.
     - Fast recovery — ssthresh is halved and sending continues, instead of restarting from 1.
     - The overall pattern is AIMD: additive increase, multiplicative decrease.
   - `Choke packets` — a congested router asks the source directly to slow down.
   - `ECN` — routers mark packets instead of dropping them, so senders react before any loss.
   - `Backpressure` — congestion is propagated hop by hop back towards the source.
   - `RED (Random Early Detection)` — routers drop packets randomly as the queue grows, before it is full, so flows back off at different times rather than all at once.

   Supporting measures
   - QoS classes and priority queuing to protect voice and video; load balancing across paths; upgrading a permanent bottleneck; segmentation and VLANs to limit broadcast traffic; and caching or CDNs to keep traffic local.

10. **Two OSI layers which known as “flow Control” which are those? Write them and explain.** *[Bangladesh Bank Assistant Programmer 2019 compact it 1156 (ET: DU)]*

    Answer: Flow control is performed at `two` OSI layers: the `Data Link layer (Layer 2)` and the `Transport layer (Layer 4)`.

    Data Link layer flow control (hop by hop)
    - Scope: between two directly connected nodes on a single link — for example a PC and the switch it is plugged into.
    - Purpose: stop a fast transmitter from overrunning the receiving node's frame buffer on that one link.
    - Mechanisms:
      - `Stop-and-Wait` — send one frame, wait for its acknowledgement, then send the next. Simple, but very inefficient on a long or fast link.
      - `Sliding window` — send up to N frames before an acknowledgement is required, which keeps the link busy. Go-Back-N and Selective Repeat are the two variants.
      - `Ethernet PAUSE frames` (IEEE 802.3x) — the receiver sends a PAUSE frame telling the sender to stop transmitting for a stated time.
    - Data unit: the frame. Failure mode if it is absent: buffer overflow and dropped frames at the next hop.

    Transport layer flow control (end to end)
    - Scope: between the two end hosts, across the whole path, regardless of how many routers lie in between.
    - Purpose: stop a fast sender from overrunning the receiving `application's` buffer.
    - Mechanism: TCP's `sliding window`. Every ACK carries a `receive window (rwnd)` field stating how much free buffer space the receiver has. The sender may have at most that many unacknowledged bytes outstanding.
      - If the application is slow to read, rwnd shrinks; if it reaches zero, the sender stops entirely and sends periodic window probes until the receiver advertises space again.
      - `Window scaling` (RFC 7323) extends the 16-bit field so that high bandwidth-delay-product links can be filled.
    - Data unit: the segment.

    | Point | Data Link layer | Transport layer |
    |---|---|---|
    | Scope | One hop | End to end |
    | Protects | The next node's buffer | The receiving application's buffer |
    | Mechanism | Stop-and-wait, sliding window, PAUSE frames | TCP sliding window with rwnd |
    | Data unit | Frame | Segment |
    | Addressing | MAC | Port |

    - Do not confuse flow control with `congestion control`. Flow control protects the receiver and is driven by the receiver's advertised window; congestion control protects the network and is driven by the sender's own estimate (cwnd). TCP obeys both, sending at most `min(rwnd, cwnd)`.

11. **What is piggybacking in Networking? Difference among Hub, Switch and Router.** *[BCC-4TDC Assistant Programmer 2019 compact it 1161 (ET: BCC)]*

    Answer:

    (a) Piggybacking in networking
    - Piggybacking is the technique of `attaching an acknowledgement to an outgoing data frame` instead of sending a separate ACK frame.
    - Because most communication is two-way, when B receives data from A and also has its own data to send back, B places the acknowledgement in the ACK field of its data frame. One frame then does two jobs.

    ```
    WITHOUT piggybacking             WITH piggybacking
    A --- data --------> B           A --- data ---------> B
    A <-- ACK ---------- B           A <-- data + ACK ---- B
    A <-- data --------- B
    A --- ACK ---------> B
    ```
    - Advantages: fewer frames on the wire, better bandwidth utilisation, and less per-frame processing. The saving is large because an ACK carries almost no payload yet pays the full header cost.
    - Disadvantage: the receiver must wait for outgoing data to appear. If it waits too long the sender's timer expires and retransmits unnecessarily, so a short timer forces a standalone ACK if nothing is ready.
    - Used by TCP (the ACK field is in every segment header), HDLC, and sliding-window protocols generally.

    (b) Hub vs Switch vs Router

    | Point | Hub | Switch | Router |
    |---|---|---|---|
    | OSI layer | 1 — Physical | 2 — Data Link | 3 — Network |
    | Address used | None | MAC | IP |
    | Forwarding | Floods every port | Only to the correct port, using a MAC table | Between networks, using a routing table |
    | Collision domains | 1 for the whole device | One per port | One per interface |
    | Broadcast domains | 1 | 1 (or one per VLAN) | One per interface |
    | Duplex | Half only | Full | Full |
    | Bandwidth | Shared | Dedicated per port | Depends on the link |
    | Security | None | Better | Best — ACLs, NAT, firewall |
    | Extra functions | None | VLAN, STP, port security, QoS | NAT, DHCP, routing protocols, VPN |
    | Cost | Lowest | Moderate | Highest |
    | Status | Obsolete | Standard in every LAN | Essential for internet access |

    - In one line each: a hub repeats blindly, a switch learns and delivers precisely, and a router connects whole networks and chooses the best path between them.

12. **Explain IEEE 802.3 frame format.** *[Multiple Ministry Assistant Programmer 2017 compact it 1233 (ET: N/A)]*

    Answer: IEEE 802.3 defines the Ethernet frame. Its total size is 64 to 1518 bytes, excluding the preamble.

    Frame format
    ```
    +----------+-----+----------+----------+--------+---------------+-----+
    | Preamble | SFD | Dest MAC | Src MAC  | Length | Data + Pad    | FCS |
    |  7 bytes | 1 B |  6 bytes |  6 bytes | /Type  |  46-1500 B    | 4 B |
    |          |     |          |          |  2 B   |               |     |
    +----------+-----+----------+----------+--------+---------------+-----+
     <-- not counted -->|<--------- 64 to 1518 bytes counted ------------->|
    ```

    Field by field

    | Field | Size | Purpose |
    |---|---|---|
    | Preamble | 7 bytes | Alternating 10101010, seven times. Lets the receiver's clock synchronise with the incoming bit stream |
    | SFD (Start Frame Delimiter) | 1 byte | 10101011. The final two 1s mark that the frame proper begins with the next bit |
    | Destination MAC | 6 bytes | Physical address of the receiving NIC; may be unicast, multicast or broadcast (FF:FF:FF:FF:FF:FF) |
    | Source MAC | 6 bytes | Physical address of the sending NIC; always unicast |
    | Length / Type | 2 bytes | Value 1500 or below = length of the data field (802.3); value 1536 (0x0600) or above = EtherType identifying the upper protocol — 0x0800 IPv4, 0x0806 ARP, 0x86DD IPv6 |
    | Data + Padding | 46–1500 bytes | The Network-layer packet. If it is shorter than 46 bytes, padding is added |
    | FCS (Frame Check Sequence) | 4 bytes | CRC-32 over all fields from the destination MAC onwards. The receiver recomputes it and discards the frame if it does not match |

    Key sizes and rules
    - `Minimum frame = 64 bytes` (6 + 6 + 2 + 46 + 4). This minimum exists so that a collision on a maximum-length CSMA/CD segment is detected while the sender is still transmitting. It is why padding is required.
    - `Maximum frame = 1518 bytes`, giving the familiar 1500-byte MTU. With an 802.1Q VLAN tag (4 extra bytes) the maximum becomes 1522.
    - `Interframe gap` — a mandatory idle period of 96 bit times between frames.
    - Jumbo frames of up to 9000 bytes are a non-standard extension used in data centres.

    802.3 vs Ethernet II
    - Ethernet II uses the 2-byte field as a `Type`; 802.3 uses it as a `Length` and expects an 802.2 LLC header inside the data field. In practice almost all traffic today uses Ethernet II framing, and the two are distinguished by whether the value is above or below 1536.

## Network Services (DHCP, NAT) (11)

1. **What is the DHCP in computer networking?** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 405 (ET: N/A)]*

   Answer: DHCP (Dynamic Host Configuration Protocol) is an application-layer protocol that automatically supplies a device with its IP configuration when it joins a network.

   What it provides
   - IP address, subnet mask, default gateway, DNS server addresses, and often the domain name, lease time and NTP server.

   Key facts
   - Ports: `UDP 67` (server) and `UDP 68` (client).
   - It works through the four-step `DORA` exchange: Discover, Offer, Request, Acknowledge.
   - Addresses are leased for a limited period and renewed at T1 (50 percent) and T2 (87.5 percent) of the lease.
   - A relay agent (`ip helper-address`) forwards DHCP broadcasts across a router, so one server can serve many subnets.
   - Reservations bind one MAC address to one fixed IP, for printers and servers.

   Why it is needed
   - Without DHCP every device would need manual configuration, which is slow, error-prone and impossible to manage at scale. It also eliminates duplicate-address conflicts and allows a limited pool of addresses to be reused as devices come and go.

   Risks
   - DHCP has no authentication, so a rogue server can hand out a false gateway and intercept traffic; DHCP snooping on the switch prevents this. DHCP starvation exhausts the pool with forged MAC addresses; port security limits it.
   - If no server replies, a Windows client self-assigns an `APIPA` address from 169.254.0.0/16, which allows only local communication and is a clear symptom of DHCP failure.

2. **What is the NAT in Computer networking?** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 405 (ET: N/A)]*

   Answer: NAT (Network Address Translation) is the process by which a router rewrites the IP addresses in a packet's header as it crosses the boundary between a private network and the public internet.

   Why it exists
   - IPv4 provides only about 4.3 billion addresses, and they were exhausted. RFC 1918 private ranges (10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16) can be reused by every organisation, but internet routers drop them. NAT translates them into a public address.

   How it works
   - Outbound: the private source address, and with PAT the source port, is replaced by the router's public address and a unique port; the mapping is stored in a translation table and the checksums are recalculated.
   - Inbound: the router matches the returning packet's destination port against the table and restores the original private address and port.

   Types

   | Type | Mapping | Use |
   |---|---|---|
   | Static NAT | One private ↔ one public, fixed | A server reachable from the internet |
   | Dynamic NAT | Many private ↔ a pool of public | Sharing a small public block |
   | PAT / NAT overload | Many private ↔ one public, by port | Home and office routers |

   Advantages and drawbacks
   - Advantages: conserves public addresses, lowers cost, hides internal topology, drops unsolicited inbound traffic by default, and allows internal renumbering or a change of ISP without touching internal hosts.
   - Drawbacks: breaks end-to-end connectivity, complicates VoIP, peer-to-peer and IPsec, needs application-layer gateways for FTP and SIP, adds CPU load and state to the router, and obscures which internal host generated external traffic.
   - IPv6 removes the need for NAT entirely.

3. **NAT Stands for __________?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

   Answer: NAT stands for `Network Address Translation`.

   - It is the technique by which a router rewrites the IP addresses in packet headers so that hosts using private RFC 1918 addresses can communicate over the public internet.
   - Defined in RFC 1631 (1994) as a response to IPv4 address exhaustion.
   - Ports and addresses are recorded in a `translation table` so that returning packets can be mapped back to the correct internal host.

   Types
   - `Static NAT` — one private address permanently mapped to one public address.
   - `Dynamic NAT` — private addresses mapped to a pool of public ones, as available.
   - `PAT` (Port Address Translation), also called NAT overload — many private addresses share one public address, distinguished by source port. This is what every home router uses.

   - Related abbreviations often asked with it: `PAT` — Port Address Translation; `DHCP` — Dynamic Host Configuration Protocol; `DNS` — Domain Name System.

4. **Which two services are required to enable a computer to receive dynamic IP address and access internet using domain names?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 634 (ET: N/A)]*

   Answer: The two services required are `DHCP` and `DNS`.

   DHCP (Dynamic Host Configuration Protocol)
   - Gives the computer a `dynamic IP address` automatically, together with the subnet mask, default gateway and the addresses of the DNS servers.
   - Uses the DORA exchange — Discover, Offer, Request, Acknowledge — over UDP ports 67 and 68.
   - Without it, every machine would have to be configured by hand.

   DNS (Domain Name System)
   - Translates `domain names into IP addresses`, so a user can type www.example.com instead of an address.
   - Runs on port 53: UDP for ordinary queries, TCP for zone transfers and large responses.
   - Without it the computer would have an internet connection but could not resolve any name.

   How they work together
   ```
   1. PC joins the network
   2. DHCP supplies: IP address, mask, gateway, and DNS server addresses
   3. User types www.example.com
   4. DNS resolves the name to an IP address
   5. The PC connects to that address through the gateway
   ```
   - The link between them is the key point: DHCP is what tells the client which DNS server to use. If DHCP fails, the client gets no address at all; if DNS fails, the client is connected but every name lookup fails.

5. **What is DHCP Server and why it is needed in a computer network.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 670 (ET: N/A)]*

   Answer:

   What is a DHCP server
   - A DHCP server is the machine or service that holds a pool of IP addresses and hands them out automatically to devices joining the network, along with the subnet mask, default gateway, DNS servers, domain name and lease time.
   - It listens on `UDP port 67` and replies to clients on `UDP port 68`.
   - It can be a dedicated server (Windows Server, Linux ISC DHCP or Kea), or the service built into a router or Layer 3 switch.
   - It maintains a database of `bindings`, recording which address was leased to which client (identified by MAC address or DUID) and until when.

   Why it is needed in a network

   - `Eliminates manual configuration.` Configuring an address, mask, gateway and DNS on every machine by hand is slow and impractical beyond a handful of devices. In an office with 500 PCs it is simply not viable.
   - `Prevents duplicate addresses.` Manual configuration inevitably produces conflicts, and an IP conflict knocks both machines off the network. The server tracks every allocation, so a conflict cannot occur.
   - `Uses a limited pool efficiently.` Addresses are leased, not owned. When a laptop leaves, its lease expires and the address returns to the pool for someone else. A pool of 100 addresses can serve several hundred occasional users.
   - `Supports mobility.` Laptops and phones move between networks constantly and receive correct settings automatically at each one.
   - `Centralises change.` If the DNS server or the gateway changes, it is edited once on the DHCP server rather than on every device.
   - `Reduces errors and support calls`, since users never type addresses.
   - `Scales`, whether the network has 10 devices or 10,000, and a relay agent lets one server serve many subnets.
   - `Reservations` give printers and servers a fixed address while still keeping the configuration central.

   Risks to be aware of
   - No authentication, so a rogue DHCP server can hand out a false gateway and become a man in the middle. `DHCP snooping` on the switch blocks offers from untrusted ports.
   - `DHCP starvation` exhausts the pool with forged MAC addresses; port security limits the number of MACs per port.
   - If the server fails, new clients cannot join, so redundancy (two servers splitting the scope, or a failover pair) is normal practice.

6. **(b) Explain the message flow between a DHCP server and client. Show necessary timing diagram.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 799 (ET: N/A)]*

   Answer: The exchange between a DHCP client and server is the four-step `DORA` process, carried over UDP ports 67 (server) and 68 (client).

   Timing diagram
   ```
      CLIENT                                            SERVER
    (no IP address)                                 (holds the pool)
         |                                                |
    t=0  |=== DHCP DISCOVER =============================>|
         |   src 0.0.0.0:68  dst 255.255.255.255:67       |
         |   broadcast, carries the client's MAC          |
         |                                                | [reserves a
         |                                                |  free address]
    t=1  |<================== DHCP OFFER =================|
         |   src server:67   dst 255.255.255.255:68       |
         |   offers IP, mask, gateway, DNS, lease time    |
         |                                                |
    t=2  |=== DHCP REQUEST ==============================>|
         |   broadcast, naming the chosen server          |
         |   (tells other servers to release their offers)|
         |                                                | [writes the
         |                                                |  binding]
    t=3  |<================== DHCP ACK ===================|
         |   confirms the lease and all parameters        |
         |                                                |
         |  === client configures its interface ===       |
         |                                                |
    T1   |=== DHCP REQUEST (renew, unicast) ============>|   at 50% of lease
    =0.5T|<== DHCP ACK ==================================|
         |                                                |
    T2   |=== DHCP REQUEST (rebind, broadcast) =========>|   at 87.5% of lease
   =0.875|<== DHCP ACK ==================================|
         |                                                |
         |=== DHCP RELEASE (on shutdown) ===============>|
   ```

   Message by message

   | Step | Message | Sent by | Type | Purpose |
   |---|---|---|---|---|
   | D | DISCOVER | Client | Broadcast | Is any DHCP server present? |
   | O | OFFER | Server | Broadcast | Here is an available address and its settings |
   | R | REQUEST | Client | Broadcast | I accept this server's offer |
   | A | ACK | Server | Broadcast | Confirmed; the lease is recorded |

   Why REQUEST is broadcast rather than unicast
   - Several servers may have made offers and each has reserved an address. Broadcasting the REQUEST tells the servers that were not chosen to release the addresses they set aside.

   Other messages
   - `NAK` — the server refuses, for example because the requested address is no longer valid on this subnet. The client restarts from DISCOVER.
   - `DECLINE` — the client found the offered address already in use (it ARPs to check) and rejects it.
   - `RELEASE` — the client gives the address back, typically on shutdown.
   - `INFORM` — the client already has an address but wants other parameters such as DNS.

   Lease renewal timers
   - `T1 = 50 %` of the lease: the client unicasts a REQUEST to the same server.
   - `T2 = 87.5 %`: if there was no reply, it broadcasts to any server.
   - If the lease expires with no reply, the address is given up and DORA starts again.
   - `ipconfig /release` and `ipconfig /renew` force these steps manually.

   Across subnets
   - Routers do not forward broadcasts, so a `DHCP relay agent` (the `ip helper-address` command) converts the broadcast into a unicast towards a central server.

7. **What is APIPA?** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 840 (ET: N/A)]*

   Answer: APIPA stands for `Automatic Private IP Addressing`. It is the mechanism by which a Windows (and most modern) host assigns itself an address when no DHCP server can be reached.

   How it works
   - The client boots and broadcasts DHCP DISCOVER messages.
   - If no DHCP server replies after several attempts (about a minute), the client picks a random address from `169.254.0.0/16` with mask `255.255.0.0`.
   - It then sends a gratuitous ARP to check that no other host already uses that address. If there is a conflict it picks another and repeats, up to ten times.
   - It keeps retrying DHCP in the background, typically every five minutes, and switches over the moment a server appears.

   Characteristics
   - Range: `169.254.0.0 – 169.254.255.255` (the usable part is 169.254.1.0 – 169.254.254.255).
   - It is a `link-local` address: routers never forward it, so communication is limited to the local segment.
   - No default gateway and no DNS server are configured, so `there is no internet access`. Name resolution falls back to NetBIOS or mDNS.
   - Devices with APIPA addresses can still talk to each other on the same segment, which is why an ad hoc file transfer between two PCs still works.

   Why it matters in practice
   - Seeing a 169.254.x.x address in `ipconfig` is a definitive diagnostic: it means the machine `could not reach a DHCP server`. The fault is therefore the cable, the switch port, the VLAN, the DHCP server itself, or a blocked relay — not the PC's IP configuration.

   Troubleshooting steps
   - Check the physical link and the switch port.
   - Verify the DHCP server is running and its scope is not exhausted.
   - Check the `ip helper-address` on the router if the server is on another subnet.
   - Run `ipconfig /release` then `ipconfig /renew`.
   - Confirm the port is in the correct VLAN.

   - The IPv6 equivalent is the `FE80::/10` link-local address, but with an important difference: in IPv6 a link-local address is always configured in addition to any global address, not only as a fallback.

8. **What do you mean by DHCP server? Explain the benefits of using dedicated DHCP server. Briefly describe the main benefits of using IPv6 protocol.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 914 (ET: N/A)]*

   Answer:

   (a) What is a DHCP server
   - A server that automatically issues IP addresses and related configuration — subnet mask, default gateway, DNS servers, domain name and lease time — to devices joining the network.
   - It listens on UDP port 67 and replies to clients on port 68, using the DORA exchange: Discover, Offer, Request, Acknowledge.
   - It keeps a binding database recording which address was leased to which client and until when.

   (b) Benefits of a dedicated DHCP server (as opposed to the service built into a router)

   - `Scalability` — a dedicated server handles thousands of clients and many subnets, where a router's built-in service typically manages one small pool.
   - `Multiple scopes and subnets` from one place, reached through relay agents, so the whole organisation is administered centrally.
   - `High availability` — two servers can split a scope 80/20, or run as a failover pair, so an outage does not stop new clients joining. A router's service is a single point of failure.
   - `Detailed control` — per-scope options, vendor and user class options, PXE boot parameters, and fine-grained lease times.
   - `Reservations at scale` — hundreds of MAC-to-IP bindings for printers, cameras and servers, managed in one console.
   - `Integration with DNS` — dynamic DNS updates so that a client's name resolves correctly as soon as it receives its address.
   - `Logging, auditing and reporting` — a record of which device held which address at which time, which is essential for security investigations.
   - `Better performance` — the router's CPU is left for routing rather than lease processing.
   - `Policy and filtering` — allow or deny by MAC address or vendor class.
   - `Backup and restore` of the lease database, and easier capacity planning from utilisation reports.

   (c) Main benefits of IPv6

   - `Vast address space` — 128 bits gives 3.4 × 10^38 addresses, permanently ending the shortage that shaped IPv4.
   - `No NAT required`, which restores true end-to-end connectivity and makes peer-to-peer, VoIP and IoT far simpler.
   - `Simpler, fixed 40-byte header` with 8 fields instead of 13, and no header checksum, so routers forward faster.
   - `Stateless autoconfiguration (SLAAC)` — a host configures itself from a Router Advertisement, with no DHCP server needed.
   - `Built-in IPsec` for authentication, integrity and encryption, rather than an optional add-on.
   - `Better QoS` through the Traffic Class field and a 20-bit Flow Label that identifies individual flows.
   - `No broadcast` — multicast replaces it, so uninterested hosts are never disturbed and broadcast-amplification attacks disappear.
   - `Efficient routing` through hierarchical allocation and route aggregation, which keeps global routing tables smaller.
   - `Built-in mobility` (Mobile IPv6), letting a device keep its address as it moves between networks.
   - `Harder to scan` — a /64 subnet holds 1.8 × 10^19 addresses, making automated reconnaissance and worm propagation impractical.
   - `Simpler network management`, since renumbering is supported by design and every device can have a unique, traceable address.

9. **১৬. DHCP uses UDP port _____ for sending data to the server.** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 942 (ET: N/A)]*

   Answer: DHCP uses `UDP port 67` for sending data to the server.

   - Client to server: destination port `67`.
   - Server to client: destination port `68`.
   - Both are well-known ports, and DHCP uses UDP rather than TCP because the client has no IP address yet and must broadcast, which TCP cannot do.

   Why these two ports
   - Using two fixed ports rather than an ephemeral client port allows the server's reply to be broadcast and still be recognised only by DHCP clients. A client with no address cannot receive a unicast reply, so the broadcast must be distinguishable.

   Message flow with ports
   ```
   DISCOVER  src 0.0.0.0:68        dst 255.255.255.255:67
   OFFER     src <server>:67       dst 255.255.255.255:68
   REQUEST   src 0.0.0.0:68        dst 255.255.255.255:67
   ACK       src <server>:67       dst 255.255.255.255:68
   ```

   Related port numbers

   | Service | Port |
   |---|---|
   | DHCP server / client | 67 / 68 (UDP) |
   | DHCPv6 server / client | 547 / 546 (UDP) |
   | DNS | 53 (UDP and TCP) |
   | TFTP | 69 (UDP) |
   | SNMP | 161, 162 (UDP) |
   | HTTP / HTTPS | 80 / 443 (TCP) |

10. **DHCP কি? DHCP কিভাবে কাজ করে লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1043 (ET: DPI)]*

    Answer: (Answered in English, as required for IT topics.)

    What is DHCP
    - DHCP (Dynamic Host Configuration Protocol) is an application-layer protocol that automatically assigns an IP address and the rest of the network configuration to a device when it joins a network.
    - It supplies: IP address, subnet mask, default gateway, DNS server addresses, domain name and lease time.
    - Ports: UDP 67 for the server, UDP 68 for the client.
    - It removes the need for manual configuration, prevents duplicate addresses, and lets a limited pool of addresses be reused as devices come and go.

    How DHCP works — the DORA exchange

    - `1. DHCP DISCOVER` — the client has no address, so it broadcasts to 255.255.255.255 from source 0.0.0.0, carrying its MAC address, asking whether any DHCP server is present.
    - `2. DHCP OFFER` — every server that hears it reserves a free address from its pool and replies with that address plus the mask, gateway, DNS servers and lease time.
    - `3. DHCP REQUEST` — the client accepts one offer (normally the first to arrive) and broadcasts a request naming that server. Broadcasting tells the other servers to release the addresses they had reserved.
    - `4. DHCP ACK` — the chosen server confirms, writes the binding into its database, and the client configures its interface. If the address has become unavailable it sends a NAK instead and the client restarts.

    ```
    CLIENT                                  SERVER
      |------- DISCOVER (broadcast) --------->|
      |<------ OFFER (IP proposed) -----------|
      |------- REQUEST (broadcast) ---------->|
      |<------ ACK (confirmed) ---------------|
         client now has IP, mask, gateway, DNS
    ```

    Lease renewal
    - At `T1` (50 percent of the lease) the client unicasts a renewal request to the same server.
    - At `T2` (87.5 percent), if there was no reply, it broadcasts to any server.
    - If the lease expires with no reply, the address is released and DORA begins again.

    Across subnets
    - Routers do not forward broadcasts, so a `DHCP relay agent` (`ip helper-address`) converts the broadcast into a unicast towards a central server, letting one server serve many VLANs.

    If DHCP fails
    - A Windows client assigns itself an APIPA address from 169.254.0.0/16, which allows only local communication. Seeing a 169.254.x.x address is a definite sign that the DHCP server was unreachable.

11. **Write the disadvantage of manual IP. Name the protocol of dynamic IP assigning. DHCP how works?** *[BTCL Assistant Manager (Technical) 2017 compact it 1255 (ET: N/A)]*

    Answer:

    (a) Disadvantages of manual (static) IP configuration

    - `Time consuming` — every device must be visited and configured individually. In an office of 500 machines this is days of work.
    - `Duplicate address conflicts` — the commonest and most damaging error. Two devices with the same address knock each other off the network, and the fault is hard to trace.
    - `Typing errors` — a wrong mask, gateway or DNS server silently breaks connectivity, and the symptom rarely points at the cause.
    - `No mobility` — a laptop moving between networks must be reconfigured by hand each time.
    - `Difficult to change` — if the DNS server or the gateway changes, every device must be edited again.
    - `Wasteful of addresses` — an address assigned to a machine stays assigned even when the machine is switched off or removed, so the pool is used inefficiently.
    - `Requires documentation` — a spreadsheet of every allocation must be maintained, and it goes stale immediately.
    - `Needs technical knowledge` — ordinary users cannot do it, so every new device becomes a support call.
    - `Does not scale`, and there is no central record of which device holds which address.

    (b) Protocol for dynamic IP assignment
    - `DHCP` — Dynamic Host Configuration Protocol, on UDP ports 67 (server) and 68 (client).
    - Its predecessors were BOOTP and RARP; the IPv6 version is DHCPv6 (ports 547 and 546), alongside SLAAC.

    (c) How DHCP works — the DORA exchange

    - `Discover` — the client broadcasts to 255.255.255.255 from 0.0.0.0, carrying its MAC address, looking for any DHCP server.
    - `Offer` — each server reserves a free address and replies with it plus the mask, gateway, DNS servers and lease time.
    - `Request` — the client broadcasts its acceptance of one offer, naming the chosen server so the others release their reservations.
    - `Acknowledge` — the chosen server confirms, records the binding, and the client configures its interface.

    ```
    CLIENT                                SERVER
      |----- DISCOVER (broadcast) --------->|
      |<---- OFFER ------------------------|
      |----- REQUEST (broadcast) --------->|
      |<---- ACK --------------------------|
    ```

    - Renewal happens at T1 (50 percent of the lease, unicast to the same server) and T2 (87.5 percent, broadcast to any server).
    - A relay agent forwards the broadcast across a router so one server can serve many subnets.
    - If no server answers, the client falls back to an APIPA address in 169.254.0.0/16, with local connectivity only.

## Digital Modulation & Signal Processing (BPSK, QPSK) (10)

1. **Draw Bit Error Rate vs Signal to Noise Ratio curve of QPSK and BPSK.** *[NWPGCL Assistant Manager (ICT) 12.01.2024 compact it 293 (ET: BUET)]*

   Answer: The important result is that `BPSK and QPSK have the same BER for a given Eb/N0` — their curves lie on top of each other.

   BER vs SNR curve
   ```
   BER
   1e-1 |*
        | *
        |  *
   1e-2 |   **
        |     *
        |      **        BPSK and QPSK
   1e-3 |        **   <-- both follow the SAME curve
        |          **
        |            **
   1e-4 |              **
        |                ***
   1e-5 |                   ***
        |                      ****
   1e-6 |                          ****
        +----+----+----+----+----+----+----> Eb/N0 (dB)
        0    2    4    6    8   10   12
   ```
   - Reference points on the curve: about 10^-3 at 7 dB, 10^-4 at 8.4 dB, 10^-5 at 9.6 dB, and 10^-6 at 10.5 dB.

   The formula
   ```
   BER (BPSK) = Q( sqrt(2 Eb/N0) )
   BER (QPSK) = Q( sqrt(2 Eb/N0) )       -- identical
   ```
   - The curves coincide because QPSK is simply two independent BPSK streams, one on the in-phase carrier and one on the quadrature carrier. Each stream carries half the total power but also half the total bits, so the energy per bit is unchanged.

   Why QPSK is therefore preferred
   - For the same BER and the same Eb/N0, QPSK sends `2 bits per symbol` against BPSK's 1, so it delivers `twice the data rate in the same bandwidth`. There is no penalty in error performance — this is why QPSK is used in satellite links, LTE, Wi-Fi and DVB.
   - The trade-off is complexity: QPSK needs a more elaborate modulator and demodulator, and it is more sensitive to phase noise and carrier recovery error.

   Where the curves do separate
   - Plotted against `SNR per symbol` rather than Eb/N0, QPSK is 3 dB worse than BPSK, because each QPSK symbol carries two bits. Examiners often expect the Eb/N0 version, in which the curves coincide.
   - Higher-order schemes are genuinely worse: 8-PSK needs roughly 3.5 dB more and 16-QAM about 4 dB more Eb/N0 than BPSK for the same BER, because the constellation points sit closer together.

   ```
   BER
        |  *  *   *
        |   *  *   *
        |    *  *   *
        |     *  *   *
        |      *  *   *   <- 16-QAM (rightmost, worst)
        |    BPSK/  8-PSK
        |    QPSK
        +--------------------> Eb/N0 (dB)
   ```

2. **What is baseband and passband frequency?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 499 (ET: N/A)]*

   Answer:

   Baseband
   - Baseband refers to the `original frequency band of the signal`, from (or near) zero hertz up to its highest frequency, with `no modulation onto a carrier`.
   - The digital signal is placed directly onto the medium as voltage levels.
   - Frequency range: `0 to f_max`. A voice signal is 0–4 kHz; a 10 Mbps Ethernet signal occupies from DC upwards.
   - Only one signal can occupy the medium at a time, so the whole bandwidth belongs to that one channel.
   - It uses digital line coding — NRZ, Manchester, RZ — rather than a modulator.
   - Examples: Ethernet (the `BASE` in 10BASE-T stands for baseband), RS-232, and any short digital cable link.
   - Repeaters, not amplifiers, are used to extend it.

   Passband (broadband)
   - Passband refers to a signal that has been `modulated onto a carrier frequency`, so it occupies a band of frequencies centred on that carrier rather than starting from zero.
   - Frequency range: `fc − B/2 to fc + B/2`, where fc is the carrier.
   - Because different signals can use different carriers, `many channels share the medium at once` through FDM. This is the essential advantage.
   - It uses ASK, FSK, PSK or QAM.
   - Examples: AM and FM radio, television broadcast, cable TV, ADSL, Wi-Fi, mobile networks.
   - Amplifiers are used to extend it, and the signal can travel much further.

   | Point | Baseband | Passband |
   |---|---|---|
   | Carrier | None | Yes |
   | Frequency range | 0 to f_max | Around fc |
   | Channels on the medium | One | Many, by FDM |
   | Signalling | Line coding | ASK, FSK, PSK, QAM |
   | Direction | Usually bidirectional | Usually one direction per channel |
   | Distance | Shorter, needs repeaters | Longer, uses amplifiers |
   | Example | Ethernet, RS-232 | Radio, TV, Wi-Fi, ADSL |

   - Why passband exists: a low-frequency baseband signal cannot be radiated efficiently (the antenna would have to be kilometres long), cannot share a medium with other signals, and cannot travel far. Modulating it onto a high carrier solves all three problems at once.

3. **অথবা, (ক) Low-pass Channel এবং Band-pass Channel এর মধ্যে উদাহরণসহ পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 628 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   Low-pass channel
   - A channel whose bandwidth starts at or near `zero hertz` and extends up to some maximum frequency: `0 to f_max`.
   - It can carry a baseband signal directly, with no modulation, because the DC and low-frequency components of a digital signal pass through unchanged.
   - Only one signal can use it at a time.
   - Examples: a twisted-pair cable in an Ethernet LAN, a coaxial cable carrying baseband data, an RS-232 serial link, the local loop of a telephone line used for a direct digital connection.

   Band-pass channel
   - A channel that passes only a `range of frequencies away from zero`, from f1 to f2, and blocks everything below f1 and above f2.
   - A baseband digital signal cannot pass through it, because its low-frequency components would be blocked. The signal must first be `modulated onto a carrier` inside the passband.
   - Because different carriers can be used, many signals can share the same medium at once by FDM.
   - Examples: a telephone voice channel (300–3300 Hz), an AM radio channel, a television channel, a Wi-Fi channel at 2.4 GHz, an ADSL sub-band.

   ```
   LOW-PASS CHANNEL                 BAND-PASS CHANNEL
   amplitude                        amplitude
      |______                          |     ______
      |      \                         |    /      \
      |       \                        |   /        \
      +--------\------> f              +--/----------\--> f
      0      f_max                     0  f1        f2
      passes from DC upward            passes only f1 to f2
   ```

   | Point | Low-pass channel | Band-pass channel |
   |---|---|---|
   | Frequency range | 0 to f_max | f1 to f2, with f1 > 0 |
   | Passes DC | Yes | No |
   | Signal used | Baseband, directly | Passband, modulated onto a carrier |
   | Modulation needed | No | Yes — ASK, FSK, PSK, QAM |
   | Channels at once | One | Many, by FDM |
   | Example | Ethernet cable, RS-232 | Telephone line for a modem, radio, Wi-Fi |

   - Practical consequence: this is exactly why a `modem` exists. A telephone line is a band-pass channel from 300 to 3300 Hz, so a computer's baseband digital signal must be modulated onto an audio carrier to pass through it, and demodulated at the far end.

4. **What is modulation? Why is it necessary?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 637 (ET: N/A)]*

   Answer:

   What is modulation
   - Modulation is the process of varying one or more properties of a high-frequency `carrier` signal — its amplitude, frequency or phase — in step with the information signal, so that the information can be carried over the medium.
   - The reverse process at the receiver is `demodulation`. A device that does both is a `modem`.

   Types
   - Analogue modulation: `AM` (amplitude), `FM` (frequency), `PM` (phase).
   - Digital modulation: `ASK`, `FSK`, `PSK`, `QAM`, and the multi-carrier scheme `OFDM`.
   - Pulse modulation: PAM, PWM, PPM, PCM.

   Why modulation is necessary

   - `Practical antenna size.` An antenna must be roughly a quarter of the wavelength to radiate efficiently. A 3 kHz audio signal has a wavelength of 100 km, needing a 25 km antenna — impossible. Shifting it onto a 100 MHz carrier gives a wavelength of 3 m and an antenna of about 75 cm. This is the single strongest reason.

   - `Multiplexing — sharing the medium.` Without modulation every transmitter would occupy the same low frequency band and interfere with every other. Modulating each onto a different carrier lets hundreds of radio stations, TV channels and Wi-Fi networks coexist. This is FDM.

   - `Long-distance transmission.` Higher frequencies propagate better through air and can be focused into a beam, so the signal travels much further with less power.

   - `Band-pass channels require it.` Many channels do not pass DC or low frequencies — a telephone line passes only 300–3300 Hz. A baseband digital signal simply cannot get through, so it must be modulated onto a carrier inside that band.

   - `Noise reduction.` FM and PSK are far more resistant to amplitude noise than a raw baseband signal, because the information is carried in frequency or phase rather than in amplitude.

   - `Higher data rate in the same bandwidth.` Multi-level schemes such as 16-QAM and 64-QAM carry 4 or 6 bits per symbol, multiplying throughput without extra spectrum.

   - `Regulatory allocation.` Spectrum is licensed in defined bands; modulation is what places a transmission into its assigned band.

   - Summary: modulation makes radiation practical, allows many users to share one medium, extends range, matches the signal to the channel's passband, improves noise immunity, and raises spectral efficiency.

5. **Amplitude Modulation related problem. (Approximate)** *[NPCBL Executive Trainee (IT) 2022 compact it 644 (ET: BUET)]*

   Answer: The exact problem was not printed, so the amplitude modulation formulas and the standard worked patterns are given.

   The AM signal
   ```
   s(t) = Ac [1 + m cos(2π fm t)] cos(2π fc t)
   ```
   - Ac = carrier amplitude, fc = carrier frequency, fm = modulating frequency, m = modulation index.

   Modulation index
   ```
   m = Am / Ac
   ```
   - From a trapezoidal or envelope display:
   ```
   m = (Vmax − Vmin) / (Vmax + Vmin)
   ```
   - `m < 1` — undermodulation, wasteful of power.
   - `m = 1` — 100 percent modulation, the ideal.
   - `m > 1` — overmodulation, which distorts the envelope and cannot be recovered by an envelope detector.

   Bandwidth
   ```
   BW = 2 fm          (for a single tone)
   BW = 2 fm(max)     (for a band of frequencies)
   ```
   - Example: a 5 kHz audio signal on a 1 MHz carrier occupies 990–1010 kHz... more precisely 995 to 1005 kHz, a bandwidth of 10 kHz.

   Power relations
   ```
   Pt = Pc (1 + m²/2)
   Psidebands = Pc · m²/2
   Efficiency η = (m²/2) / (1 + m²/2) = m² / (2 + m²)
   ```
   - At m = 1 the efficiency is only `33.3 percent` — two-thirds of the transmitted power is in the carrier, which carries no information. This is the fundamental weakness of AM and the reason DSB-SC and SSB exist.

   Worked example
   - Carrier power 1000 W, m = 0.8.
   ```
   Pt = 1000 (1 + 0.64/2) = 1000 × 1.32 = 1320 W
   Sideband power = 1000 × 0.32 = 320 W (160 W in each sideband)
   Efficiency = 0.32 / 1.32 = 24.2 %
   ```

   Multiple modulating signals
   ```
   m_total = sqrt(m1² + m2² + m3² + ...)
   ```

   Current relation
   ```
   It = Ic sqrt(1 + m²/2)
   ```
   - Example: Ic = 10 A, m = 0.6 gives It = 10 × sqrt(1.18) = 10.86 A. <!-- verify -->

6. **Compare between (i) AM and ASK and (ii) FM and FSK considering modulation scheme, bandwith requirement, noise tolerance and circuit complexity.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

   Answer:

   (i) AM vs ASK

   | Point | AM (Amplitude Modulation) | ASK (Amplitude Shift Keying) |
   |---|---|---|
   | Modulating signal | Analogue and continuous | Digital, discrete bits |
   | Modulation scheme | Carrier amplitude varies continuously with the message | Carrier amplitude switches between fixed levels: present for 1, absent (or lower) for 0 |
   | Output | A continuously varying envelope | A pulsed on/off carrier (OOK in the binary case) |
   | Bandwidth | `BW = 2 fm` | `BW = (1 + d) × Nbaud`, typically about 2 × bit rate |
   | Noise tolerance | Poor — noise directly alters amplitude, and it cannot be separated from the signal | Poor, but better than AM: the receiver only decides between two levels, so small noise causes no error |
   | Circuit complexity | Simple modulator, very simple envelope detector | Simple; a switch and an envelope detector suffice |
   | Error handling | None; noise is permanent | Digital regeneration removes noise completely at each repeater |
   | Application | Medium-wave broadcast radio, aircraft VHF | Optical fibre (on/off keying), low-cost RFID, infrared remote controls |

   (ii) FM vs FSK

   | Point | FM (Frequency Modulation) | FSK (Frequency Shift Keying) |
   |---|---|---|
   | Modulating signal | Analogue and continuous | Digital bits |
   | Modulation scheme | Carrier frequency varies continuously with the message amplitude | Carrier switches between two (or M) discrete frequencies: f1 for 0, f2 for 1 |
   | Bandwidth | `BW = 2(Δf + fm)` — Carson's rule; wide | `BW = (f2 − f1) + Nbaud`; wider than ASK or PSK |
   | Noise tolerance | Excellent — information is in frequency, so amplitude noise can be removed by a limiter | Excellent, for the same reason; far better than ASK |
   | Circuit complexity | More complex: VCO modulator, discriminator or PLL demodulator | Moderate; two oscillators or a VCO, and a filter-based or PLL detector |
   | Power efficiency | Constant envelope, so a non-linear class-C amplifier can be used efficiently | Same advantage — constant envelope |
   | Application | FM broadcast radio, TV sound, two-way radio | Low-speed modems, caller ID, Bluetooth (GFSK), LoRa, telemetry |

   The general pattern
   - The `SK` schemes are the digital counterparts of the analogue ones: continuous variation is replaced by switching between discrete states.
   - Amplitude-based schemes (AM, ASK) are simplest and cheapest but least noise-tolerant, because noise is itself an amplitude disturbance.
   - Frequency-based schemes (FM, FSK) buy much better noise immunity at the cost of more bandwidth and more complex circuitry.
   - Phase-based schemes (PSK, QAM), not asked here, give the best spectral efficiency of all and are what modern systems use.

7. **What are the advantages of PSK and explain why coherent detection is necessary for demodulating the PSK signal?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

   Answer:

   Advantages of PSK

   - `Better noise immunity than ASK.` The information is carried in the phase, so amplitude noise — which is the commonest kind — does not corrupt it. A limiter can strip amplitude variation away entirely before detection.
   - `Better bandwidth efficiency than FSK.` FSK needs enough spectrum to hold two or more separated frequencies; PSK keeps one carrier frequency and changes only its phase, so it occupies less bandwidth for the same bit rate.
   - `Constant envelope` (in BPSK and QPSK). The amplitude never changes, so the transmitter can use an efficient non-linear class-C power amplifier without distortion. This matters enormously for battery-powered and satellite transmitters.
   - `Lower BER for a given Eb/N0.` BPSK is the optimum binary scheme: it needs about 3 dB less Eb/N0 than coherent FSK and far less than ASK for the same error rate.
   - `Scales to higher orders.` QPSK carries 2 bits per symbol at the same BER as BPSK, 8-PSK carries 3, and the same idea extends to QAM. This doubles or triples throughput in the same bandwidth.
   - `Robust against fading` compared with amplitude schemes, since a fade changes amplitude, not phase.
   - Widely used: satellite links, LTE and 5G, Wi-Fi, DVB, cable modems and RFID.

   Why coherent detection is necessary for PSK

   - `The information is in the phase, and phase is only meaningful relative to a reference.` A receiver that does not know the carrier's phase has nothing to compare the incoming signal against. In BPSK the two symbols are `+A cos(2π fc t)` and `−A cos(2π fc t)`; they differ only in sign, so an envelope detector sees an identical amplitude for both and can distinguish nothing at all.

   - `Non-coherent detection cannot work for PSK.` ASK and FSK can be detected non-coherently, because they differ in amplitude or in frequency, both of which can be measured without a phase reference. PSK has no such handle — all symbols share the same amplitude and the same frequency.

   - `A locally generated carrier is therefore required`, exactly matched in frequency and phase to the transmitted carrier. It is recovered by a Costas loop, a squaring loop or a PLL, and the received signal is multiplied by it and integrated over each symbol period. The sign of the result gives the bit.

   - `Phase ambiguity is the practical problem.` A recovered carrier can lock 180° out of phase (or in 90° steps for QPSK), which inverts every bit. Two standard remedies exist:
     - `Differential encoding` (DPSK), in which the data is carried in the `change` of phase between consecutive symbols rather than in the absolute phase. This removes the need for an absolute reference, at the cost of about 1 dB in Eb/N0 and a tendency for errors to occur in pairs.
     - A known training or pilot sequence to resolve the ambiguity.

   - Summary: coherent detection is not an optional refinement for PSK — it is the only way to recover the data, because phase has no absolute meaning without a reference. That is the price paid for PSK's superior noise and bandwidth performance.

8. **Draw the constellation diagram of QPSK, 8-PSK and 32-QAM. Why these multilevel signals prefereed and what are the challenges for multilevel modulation?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

   Answer:

   Constellation diagrams

   QPSK — 4 points, 2 bits per symbol, all on one circle
   ```
                 Q
                 |
         01 *    |    * 00
                 |
      -----------+----------- I
                 |
         11 *    |    * 10
                 |
      4 phases: 45°, 135°, 225°, 315°
      constant amplitude
   ```

   8-PSK — 8 points, 3 bits per symbol, still one circle
   ```
                 Q
           *     |     *
                 |
      *          |          *
      -----------+----------- I
      *          |          *
                 |
           *     |     *

      8 phases spaced 45° apart, constant amplitude
   ```

   32-QAM — 32 points, 5 bits per symbol, a cross constellation
   ```
                 Q
            *  *  *  *
         *  *  *  *  *  *
         *  *  *  *  *  *
      ---*--*--*--+--*--*--*--- I
         *  *  *  *  *  *
         *  *  *  *  *  *
            *  *  *  *

      32 points; both amplitude and phase vary.
      The corners of the 6x6 grid are removed, giving
      the characteristic "cross" shape, which keeps the
      average power lower than a full square would.
   ```

   Why multilevel signals are preferred

   - `Higher bit rate in the same bandwidth.` The relationship is `bit rate = baud rate × log2(M)`. Bandwidth is set by the baud rate, so raising M raises throughput without needing more spectrum.

   | Scheme | Points M | Bits/symbol | Rate at 1000 baud |
   |---|---|---|---|
   | BPSK | 2 | 1 | 1 kbps |
   | QPSK | 4 | 2 | 2 kbps |
   | 8-PSK | 8 | 3 | 3 kbps |
   | 16-QAM | 16 | 4 | 4 kbps |
   | 32-QAM | 32 | 5 | 5 kbps |
   | 64-QAM | 64 | 6 | 6 kbps |

   - `Spectrum is scarce and expensive`, licensed in fixed blocks, so squeezing more bits into the same hertz has direct commercial value.
   - `Adaptive modulation` lets a system use a high order when the channel is good and drop to a lower order when it degrades, maximising throughput at every moment. LTE, Wi-Fi and DVB-S2 all do this.
   - `Lower symbol rate for a given bit rate` also means less intersymbol interference and simpler timing recovery.

   Challenges of multilevel modulation

   - `Higher SNR required.` The constellation points sit closer together, so less noise is needed to push a received point into the wrong decision region. Each step up in order costs roughly 3 to 6 dB in required Eb/N0.
   - `Higher bit error rate for a given SNR`, and one symbol error can corrupt several bits — Gray coding is used so that adjacent points differ by only one bit, limiting the damage.
   - `Linear amplifiers required.` QAM has a varying envelope, so the power amplifier must be linear, which is far less efficient than the class-C amplifier a constant-envelope scheme can use. Battery life and transmitter cost both suffer.
   - `High peak-to-average power ratio (PAPR)`, forcing the amplifier to be backed off from its peak, wasting further power.
   - `Precise carrier and timing recovery.` Phase noise, frequency offset and timing jitter rotate or smear the constellation, and the tolerance shrinks as M grows.
   - `Sensitivity to channel impairments` — fading, multipath and non-linearity all distort the constellation, so equalisation becomes essential.
   - `Greater receiver complexity and cost`, with more elaborate DSP for equalisation, carrier recovery and soft-decision decoding.

   - The design trade-off in one line: multilevel modulation buys spectral efficiency and pays for it in required SNR, amplifier linearity and receiver complexity.

9. **a) What is QAM? Explain it.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1030 (ET: N/A)]*

   Answer:

   What is QAM
   - QAM (Quadrature Amplitude Modulation) is a digital modulation scheme that varies `both the amplitude and the phase` of the carrier at the same time, so that each symbol represents several bits.
   - It combines ASK and PSK. Because it uses two dimensions rather than one, it packs far more points into the constellation for a given minimum spacing, which is why it is the most spectrally efficient scheme in common use.

   How it works
   - Two carriers of the same frequency, 90° apart in phase, are used: the `in-phase` carrier cos(2π fc t) and the `quadrature` carrier sin(2π fc t). Being orthogonal, they do not interfere with each other.
   - The incoming bit stream is split in two. One half amplitude-modulates the I carrier, the other half amplitude-modulates the Q carrier, and the two are added.
   ```
   s(t) = I(t) cos(2π fc t) − Q(t) sin(2π fc t)
   ```
   - The receiver multiplies the incoming signal separately by cos and by sin, low-pass filters both, and recovers I and Q. The pair (I, Q) identifies one point on the constellation, and that point maps to a group of bits.

   Bits per symbol
   ```
   Bits per symbol = log2(M)
   Bit rate = baud rate × log2(M)
   ```

   | Scheme | Points | Bits/symbol | Typical use |
   |---|---|---|---|
   | 4-QAM (= QPSK) | 4 | 2 | Satellite, LTE control channels |
   | 16-QAM | 16 | 4 | Wi-Fi, LTE, cable |
   | 64-QAM | 64 | 6 | Wi-Fi, DVB-C, LTE |
   | 256-QAM | 256 | 8 | Cable modems, Wi-Fi 5 |
   | 1024/4096-QAM | 1024/4096 | 10/12 | Wi-Fi 6/7, DOCSIS 3.1 |

   Constellation of 16-QAM
   ```
           Q
      *  *  |  *  *      4 amplitude levels on I
      *  *  |  *  *      4 amplitude levels on Q
    -------+-------- I   = 16 combinations
      *  *  |  *  *        4 bits per symbol
      *  *  |  *  *
   ```

   Advantages
   - The highest spectral efficiency of the common schemes — more bits per hertz than PSK of the same order.
   - Scales smoothly, and supports adaptive modulation: use 256-QAM when the channel is good, fall back to QPSK when it is poor.
   - Used everywhere: Wi-Fi, LTE and 5G, DVB, cable modems, ADSL and microwave links.

   Disadvantages
   - Requires a high SNR, because the points sit close together. Each doubling of the order costs roughly 3 dB.
   - The envelope varies, so a `linear` power amplifier is required, which is much less efficient than the class-C amplifier a constant-envelope scheme can use.
   - High peak-to-average power ratio, forcing amplifier back-off.
   - Sensitive to phase noise, frequency offset and non-linearity, so accurate carrier recovery and equalisation are essential.

10. **b) Draw diagram for 16 QAM having? (i) 3 amplitudes, 12 phases (ii) 4 amplitudes, 8 phases** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1030-1031 (ET: N/A)]*

    Answer: Both diagrams show 16 points, so both carry 4 bits per symbol, but they place those points differently.

    (i) 16-QAM with 3 amplitudes and 12 phases
    ```
                         Q
                         |
                  *      *      *
                     \   |   /
              *    *  \  |  /  *    *
                    \  \ | /  /
         *     *  *  \ \ | / /  *  *     *
       ------------------+------------------ I
         *     *  *  / / | \ \  *  *     *
                    /  / | \  \
              *    *  /  |  \  *    *
                     /   |   \
                  *      *      *
                         |

       3 concentric circles  = 3 amplitude levels
       12 distinct phase angles, 30 degrees apart
       Points: 4 on the inner ring, 8 on the middle, 4 on the outer
               = 16 points total
    ```
    - The points lie on three circles of different radius. Twelve phase positions are used, but not every phase appears on every ring — that is how 16 points are formed rather than 36.
    - Advantage: the constant-amplitude rings keep the peak-to-average power ratio lower than a square grid would.
    - Disadvantage: the minimum distance between points is smaller than in the square arrangement, so the error performance is worse for the same average power. It is the older, less efficient layout.

    (ii) 16-QAM with 4 amplitudes and 8 phases
    ```
                         Q
                         |
               *     *   |   *     *
                         |
           *      *      *      *      *
                         |
       ------*------*----+----*------*------ I
                         |
           *      *      *      *      *
                         |
               *     *   |   *     *
                         |

       4 concentric circles = 4 amplitude levels
       8 distinct phase angles, 45 degrees apart
       16 points distributed across the four rings
    ```
    - Four amplitude levels combined with eight phase positions, again selecting 16 of the possible combinations.

    For comparison — the standard square 16-QAM actually used in practice
    ```
            Q
       *  *  |  *  *      I takes 4 levels: -3, -1, +1, +3
       *  *  |  *  *      Q takes 4 levels: -3, -1, +1, +3
     -------+-------- I   4 x 4 = 16 points
       *  *  |  *  *      3 distinct amplitudes, 12 phases
       *  *  |  *  *      (corner, edge and inner points)
    ```
    - Interestingly, the square constellation is itself a "3 amplitude, 12 phase" arrangement: the four corner points share one amplitude, the eight edge points another, and the four inner points a third.
    - The square grid is preferred in real systems because it maximises the minimum distance between points for a given average power, which minimises the bit error rate, and because I and Q can be generated and detected independently, which greatly simplifies the hardware.

    Common properties of all three
    - 16 points, `log2(16) = 4 bits per symbol`.
    - Bit rate = baud rate × 4. At 1000 baud, that is 4000 bps.
    - Gray coding is applied so that adjacent points differ in only one bit, which limits the damage caused by a single symbol error.

## Email Architecture & Protocols (SMTP, POP3, IMAP) (10)

1. **Sinthia wants to send an email to her friend (Afsana). He sends the email through application and transport layer.** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1323 (ET: DU)]*
   * (a) Mention the protocol of application layer and transport layer.
   * (b) Write down the steps of Mail transfer from Afsana to Sinthia.

   Answer:

   (a) Protocols used

   | Layer | Protocol | Purpose |
   |---|---|---|
   | Application | `SMTP` (port 25 / 587) | Sending and relaying the mail |
   | Application | `POP3` (110) or `IMAP` (143) | Retrieving the mail at the receiving end |
   | Application | `DNS` (53) | Looking up the recipient domain's MX record |
   | Application | `MIME` | Encoding attachments and non-ASCII text |
   | Transport | `TCP` | Reliable, ordered delivery; email must arrive complete |

   - TCP is used rather than UDP because a lost or reordered byte would corrupt the message. SMTP, POP3 and IMAP all run over TCP.

   (b) Steps of mail transfer

   - Step 1 — Sinthia composes the message in her `MUA` (Mail User Agent — Outlook, Thunderbird, Gmail), addressing it to afsana@example.com. MIME encodes any attachment or Unicode text.
   - Step 2 — the MUA opens a `TCP` connection to Sinthia's outgoing mail server on port 587 (or 25) and authenticates.
   - Step 3 — it hands the message over using `SMTP`, in a simple text dialogue:
   ```
   EHLO client.example.net
   MAIL FROM: <sinthia@sender.com>
   RCPT TO:   <afsana@example.com>
   DATA
     ... headers and body ...
     .
   QUIT
   ```
   - Step 4 — Sinthia's server (the `MTA`, Mail Transfer Agent) queries `DNS` for the `MX record` of example.com, which names the host that accepts mail for that domain.
   - Step 5 — it opens a TCP connection to that host on port 25 and relays the message by SMTP. If the destination is busy, the message is queued and retried, typically for up to five days.
   - Step 6 — the receiving MTA accepts the message, runs spam and virus checks and `SPF`, `DKIM` and `DMARC` authentication, then passes it to the `MDA` (Mail Delivery Agent), which places it in Afsana's mailbox.
   - Step 7 — Afsana's MUA retrieves it, using `POP3` (download to one device) or `IMAP` (keep it on the server and synchronise across devices).
   - Step 8 — the MUA decodes the MIME parts and displays the message.

   ```
   Sinthia          Sender's MTA          Receiver's MTA        Afsana
     MUA  --SMTP-->    (queue)   --SMTP-->    MDA -> mailbox
                          |
                        DNS: MX lookup                    <--IMAP/POP3-- MUA
   ```
   - Note the asymmetry that examiners look for: SMTP is a `push` protocol used all the way to the recipient's server, while POP3 and IMAP are `pull` protocols used only for the last step, from the mailbox to the recipient's device.

2. **Difference between: (i) SMTP and SNMP (ii) HTTP and HTTPs** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 550 (ET: BIBM)]*

   Answer:

   (i) SMTP vs SNMP

   | Point | SMTP | SNMP |
   |---|---|---|
   | Full form | Simple Mail Transfer Protocol | Simple Network Management Protocol |
   | Purpose | Sending and relaying email | Monitoring and managing network devices |
   | Layer | Application | Application |
   | Transport | TCP | UDP |
   | Ports | 25 (relay), 587 (submission), 465 (implicit TLS) | 161 (agent), 162 (trap) |
   | Communicates between | Mail clients and mail servers, and between mail servers | A management station and device agents |
   | Data carried | Email messages | Device statistics, configuration, alerts |
   | Operations | HELO/EHLO, MAIL FROM, RCPT TO, DATA, QUIT | GET, GETNEXT, SET, TRAP, INFORM |
   | Data structure | RFC 5322 message headers and body | MIB (Management Information Base) with OIDs |
   | Versions | ESMTP with extensions | v1, v2c, v3 (v3 adds authentication and encryption) |
   | Example use | Sending an invoice by email | Monitoring router CPU, interface errors, link status |

   - They are easy to confuse only because of the similar abbreviation; their functions are entirely unrelated.

   (ii) HTTP vs HTTPS

   | Point | HTTP | HTTPS |
   |---|---|---|
   | Full form | HyperText Transfer Protocol | HTTP Secure |
   | Port | 80 | 443 |
   | Encryption | None — everything travels in plain text | TLS encrypts the whole session |
   | Certificate | Not required | Required, issued by a trusted CA |
   | Confidentiality | None; passwords and card numbers are readable | Protected |
   | Integrity | None; content can be altered in transit | TLS MAC detects any alteration |
   | Authentication | The site's identity is unverified | The certificate proves the server's identity |
   | Vulnerable to | Eavesdropping, man-in-the-middle, content injection | Greatly reduced |
   | Browser display | Marked "Not secure" | Padlock icon |
   | Speed | Marginally faster (no handshake) | Slightly slower to set up, negligible today |
   | SEO and features | Ranked lower; HTTP/2 and service workers unavailable | Ranked higher; required for modern browser features |

   - How HTTPS works: the browser and server complete a `TLS handshake` in which the server presents its certificate, the two agree a symmetric session key, and every HTTP message after that is encrypted with it.
   - There is no remaining reason to use plain HTTP; free certificates from Let's Encrypt removed the last cost argument.

3. **Which protocol is used for email received?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

   Answer: The protocols used to `receive` email are `POP3` and `IMAP`.

   POP3 (Post Office Protocol version 3)
   - Port `110`, or `995` with SSL/TLS.
   - Downloads messages from the server to the local device and, by default, `deletes them from the server`.
   - Mail therefore lives on one machine only. Offline access is easy, and server storage stays small.
   - Suits a single-device user with limited server space.

   IMAP (Internet Message Access Protocol)
   - Port `143`, or `993` with SSL/TLS.
   - Keeps messages `on the server` and synchronises them with the client, including folders, read status and flags.
   - Any change on one device appears on every other, which is why it suits phone, laptop and webmail used together.
   - Suits modern multi-device use; it needs more server storage and a connection to browse.

   | Point | POP3 | IMAP |
   |---|---|---|
   | Port | 110 / 995 | 143 / 993 |
   | Storage | On the client | On the server |
   | Multi-device sync | No | Yes |
   | Folders on server | No | Yes |
   | Offline access | Full | Partial, cached |
   | Server space used | Little | More |

   - For contrast, `SMTP` (ports 25, 587, 465) is the protocol used to `send` mail, not to receive it. A complete mail client uses SMTP for sending and POP3 or IMAP for receiving.

4. **(a) Distinguish the purpose of SMTP and IMAP in email communication.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 688 (ET: N/A)]*

   Answer:

   SMTP — Simple Mail Transfer Protocol
   - Purpose: to `send and relay` email. It pushes a message from the sender's client to the sender's mail server, and from one mail server to the next until it reaches the recipient's server.
   - Ports: 25 (server-to-server relay), 587 (client submission with STARTTLS), 465 (implicit TLS).
   - It is a `push` protocol, and it works with the message in transit — it never touches a stored mailbox.
   - A session is a plain text dialogue: EHLO, MAIL FROM, RCPT TO, DATA, then the message ending with a single dot, then QUIT.
   - It cannot retrieve mail at all. That is a deliberate design boundary.

   IMAP — Internet Message Access Protocol
   - Purpose: to `retrieve and manage` email that is already stored in the recipient's mailbox on the server.
   - Ports: 143, or 993 with SSL/TLS.
   - It is a `pull` protocol, and messages remain on the server. The client synchronises with it rather than downloading and deleting.
   - It supports server-side folders, search, flags (read, replied, flagged), and partial fetch — a client can download only the headers, or only one attachment.
   - Changes made on one device appear on every other device, which is why it suits phone, laptop and webmail used together.

   | Point | SMTP | IMAP |
   |---|---|---|
   | Function | Sending and relaying | Retrieving and managing |
   | Direction | Push | Pull |
   | Ports | 25, 587, 465 | 143, 993 |
   | Message location | In transit | Stored on the server |
   | Folder support | Not applicable | Yes, server-side |
   | Multi-device sync | Not applicable | Yes |
   | Can it send mail | Yes | No |
   | Can it read a mailbox | No | Yes |

   How they work together
   ```
   Sender's MUA --SMTP--> Sender's MTA --SMTP--> Recipient's MTA
                                                       |
                                                     mailbox
                                                       |
                                        Recipient's MUA <--IMAP--
   ```
   - The pair is complementary, not competing: SMTP carries the message all the way to the recipient's server, and IMAP (or POP3) covers the last step from the mailbox to the recipient's device.

5. **Email এর ক্ষেত্রে CC এবং BCC এর অর্থ কি বুঝায়?** *[BPSC Computer Operator 2021 compact it 780 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.)

   CC — Carbon Copy
   - A copy of the email is sent to these recipients.
   - Their addresses are `visible to everyone` — the To recipients and the other CC recipients all see them.
   - Meaning in practice: "this is for your information, but no action is expected from you." The people in To are the ones expected to act.
   - Typical use: copying a supervisor, or keeping a colleague informed of a decision.
   - The name comes from carbon paper, which was used to make a duplicate of a typed letter.

   BCC — Blind Carbon Copy
   - A copy is also sent, but the addresses are `hidden from everyone else`. Neither the To recipients, nor the CC recipients, nor the other BCC recipients can see them.
   - Uses:
     - `Protecting privacy` when mailing a large group — a newsletter or a notice to many customers. Putting them all in To or CC would expose every address to every recipient, which is both a privacy breach and a gift to spammers.
     - Discreetly informing a third party without the main recipients knowing.
     - Keeping a copy in one's own archive or ticketing system.
   - Caution: a BCC recipient who presses Reply All does not reach the hidden list, and using BCC to conceal a manager from colleagues can be seen as a breach of trust if discovered.

   Comparison

   | Field | Recipients get the mail | Addresses visible to others | Action expected |
   |---|---|---|---|
   | To | Yes | Yes | Yes — the primary recipients |
   | CC | Yes | Yes | No — for information only |
   | BCC | Yes | `No` — hidden from all | No |

   - Rule of thumb: use `To` for the people who must act, `CC` for those who should know, and `BCC` only for mass mailings where addresses must stay private.

6. **Which of the following is correct email formate? (a) compact@webmail.com (b) compact@webmail@com (c) compact.webmail.com (d) None** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

   Answer: The correct option is `(a) compact@webmail.com`.

   Why it is correct
   - A valid email address has the form `local-part@domain`:
   ```
   compact @ webmail.com
      |     |      |
    local  @   domain name
    part   separator
   ```
   - Exactly `one` @ symbol, a non-empty local part before it, and a valid domain name after it containing at least one dot.

   Why the others are wrong

   | Option | Problem |
   |---|---|
   | (a) `compact@webmail.com` | `Correct` — one @, valid local part, valid domain |
   | (b) compact@webmail@com | Two @ symbols. Only one is permitted |
   | (c) compact.webmail.com | No @ at all. This is a hostname, not an email address |
   | (d) None | Wrong, since (a) is valid |

   Rules for a valid email address
   - The local part may contain letters, digits and the characters `. _ % + -`, but a dot may not be first, last, or doubled.
   - No spaces are allowed (unless the local part is quoted, which is rare and rarely supported).
   - The domain must be a valid hostname with a top-level domain of at least two letters.
   - Maximum length: 64 characters for the local part, 254 for the whole address.
   - The local part is technically case sensitive but is treated as case insensitive by almost every provider; the domain is always case insensitive.

   Examples
   ```
   Valid:   user@example.com, first.last@sub.domain.co.uk, user+tag@gmail.com
   Invalid: user@@example.com, .user@example.com, user@example (no TLD), user name@example.com
   ```

7. **E-mail পাঠানো এবং রিসিভ করার জন্য একটি করে প্রোটোকলের নাম লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 866 (ET: BUET)]*

   Answer: (Answered in English, as required for IT topics.)

   For sending email — `SMTP`
   - Simple Mail Transfer Protocol.
   - Ports: 25 for server-to-server relay, 587 for client submission with STARTTLS, 465 for implicit TLS.
   - It is a push protocol: it carries the message from the client to the sender's mail server, and onward from server to server until it reaches the recipient's mail server.

   For receiving email — `POP3` or `IMAP`
   - `POP3` (Post Office Protocol version 3), port 110 or 995 with SSL. It downloads messages to the local device and by default deletes them from the server, so mail lives on one machine.
   - `IMAP` (Internet Message Access Protocol), port 143 or 993 with SSL. It keeps messages on the server and synchronises folders, read status and flags across every device.

   Summary

   | Function | Protocol | Port |
   |---|---|---|
   | Sending | `SMTP` | 25, 587, 465 |
   | Receiving (download) | `POP3` | 110, 995 |
   | Receiving (synchronise) | `IMAP` | 143, 993 |

   ```
   Sender --SMTP--> Mail Server --SMTP--> Mail Server --POP3/IMAP--> Receiver
   ```
   - Note that SMTP cannot retrieve mail and POP3/IMAP cannot send it. A complete mail client configures both.

8. **Which protocol provides e-mail facility amount different hosts?** *[BSEC Assistant Director (MIS) 2021 compact it 937 (ET: IBA)]*

   Answer: The protocol that provides email facilities between different hosts is `SMTP` — Simple Mail Transfer Protocol.

   - SMTP is the application-layer protocol that transfers mail from the sender's client to the sender's mail server, and from one mail server to another across the internet, until the message reaches the recipient's server.
   - It runs over TCP: port 25 for server-to-server relay, 587 for client submission with STARTTLS, and 465 for implicit TLS.
   - It is a `push` protocol — the sender initiates the transfer.

   A typical SMTP session
   ```
   S: 220 mail.example.com ESMTP ready
   C: EHLO client.sender.com
   S: 250-mail.example.com
   C: MAIL FROM: <sender@sender.com>
   S: 250 OK
   C: RCPT TO: <receiver@example.com>
   S: 250 OK
   C: DATA
   S: 354 Start mail input, end with <CRLF>.<CRLF>
   C: Subject: Test
   C: (message body)
   C: .
   S: 250 OK, queued
   C: QUIT
   S: 221 Bye
   ```
   - Reply codes: 220 ready, 250 OK, 354 start input, 550 rejected.

   Related protocols
   - `POP3` (110) and `IMAP` (143) retrieve mail from the recipient's mailbox — they cannot send.
   - `MIME` encodes attachments and non-ASCII text into the plain ASCII that SMTP carries.
   - `DNS` supplies the MX record that tells the sending server which host accepts mail for the destination domain.
   - `SPF`, `DKIM` and `DMARC` authenticate the sending domain, because SMTP by itself does not verify who the sender claims to be — which is why spoofing and spam are possible.

9. **ই-মেইল করার ক্ষেত্রে TO, CC ও BCC কোন ব্যবহার করা হয়?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 945 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) All three fields address recipients, but they differ in visibility and in what is expected of the recipient.

   TO
   - The `primary recipients` — the people the message is actually directed at, and from whom a response or an action is expected.
   - Their addresses are visible to everyone who receives the message.
   - Use it for the people who must read and act.

   CC — Carbon Copy
   - `Secondary recipients`, copied for information only. No action is expected from them.
   - Their addresses are also visible to everyone.
   - Use it to keep a supervisor or a colleague informed of a conversation that is not primarily theirs.
   - The name comes from carbon paper, which produced a duplicate of a typed letter.

   BCC — Blind Carbon Copy
   - Recipients who receive the message while their addresses stay `hidden from everyone else` — including from the other BCC recipients.
   - Two legitimate uses:
     - `Mass mailing` — a newsletter or notice to many people, where putting all the addresses in To or CC would expose every recipient's address to every other, which is both a privacy breach and a source of spam.
     - Quietly keeping a third party or an archive informed.
   - Caution: a BCC recipient pressing Reply All will not reach the hidden list, and covert copying can damage trust if it comes to light.

   | Field | Receives the mail | Address visible to others | Action expected |
   |---|---|---|---|
   | TO | Yes | Yes | Yes |
   | CC | Yes | Yes | No, for information |
   | BCC | Yes | `No` | No |

   - Practical rule: `To` for those who must act, `CC` for those who should know, and `BCC` only where addresses must be protected.

10. **(a) What is SMTP? How SMTP works?** *[BPSC Assistant Programmer (ICT) 2019 compact it 1143 (ET: N/A)]*

    Answer:

    What is SMTP
    - SMTP (Simple Mail Transfer Protocol) is the application-layer protocol used to `send and relay` email, defined in RFC 5321.
    - It runs over TCP — port 25 for server-to-server relay, 587 for client submission with STARTTLS, 465 for implicit TLS.
    - It is a text-based, `push` protocol: the sender initiates the transfer. It handles sending only; retrieval is done by POP3 or IMAP.
    - The extended version, ESMTP, adds capabilities negotiated with the EHLO command — authentication, TLS, size limits and 8-bit transfer.

    How SMTP works

    - Step 1 — the user composes the message in an MUA and presses send.
    - Step 2 — the MUA opens a TCP connection to the outgoing mail server (the MTA) on port 587 and authenticates.
    - Step 3 — the message is transferred through the SMTP command dialogue.
    - Step 4 — the sending MTA queries DNS for the `MX record` of the recipient's domain, which names the host that accepts mail for it.
    - Step 5 — it opens a TCP connection to that host on port 25 and relays the message. If the destination is unavailable, the message is queued and retried, typically for up to five days before a bounce.
    - Step 6 — the receiving MTA accepts it, runs spam and virus checks and SPF/DKIM/DMARC verification, and passes it to the MDA, which stores it in the mailbox.
    - Step 7 — the recipient collects it later using POP3 or IMAP.

    The SMTP dialogue
    ```
    S: 220 mail.example.com ESMTP Postfix
    C: EHLO client.sender.com
    S: 250-mail.example.com
    S: 250 STARTTLS
    C: STARTTLS
    S: 220 Ready to start TLS
    C: MAIL FROM: <sender@sender.com>
    S: 250 2.1.0 OK
    C: RCPT TO: <receiver@example.com>
    S: 250 2.1.5 OK
    C: DATA
    S: 354 End data with <CR><LF>.<CR><LF>
    C: From: sender@sender.com
    C: To: receiver@example.com
    C: Subject: Meeting
    C:
    C: Please confirm the meeting time.
    C: .
    S: 250 2.0.0 OK: queued as 4A2B1C
    C: QUIT
    S: 221 2.0.0 Bye
    ```

    Reply codes

    | Code | Meaning |
    |---|---|
    | 220 | Service ready |
    | 250 | Requested action completed |
    | 354 | Start mail input |
    | 421 | Service not available, closing |
    | 450 / 451 | Temporary failure, try again later |
    | 550 | Mailbox unavailable or rejected |

    Limitations
    - SMTP carries only 7-bit ASCII, so `MIME` is needed to encode attachments, images and non-English text.
    - It performs no sender authentication of its own, which is precisely why spam and spoofing are possible, and why `SPF`, `DKIM` and `DMARC` were added on top to verify the sending domain.

## Application Layer & Well-Known Port Numbers (6)

1. Full Form and Port Number – SSH, FTP, SMTP, DNS, IMAP. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

   Answer:

   | Protocol | Full form | Port | Transport | Purpose |
   |---|---|---|---|---|
   | SSH | Secure Shell | `22` | TCP | Encrypted remote login and secure file transfer (SCP, SFTP) |
   | FTP | File Transfer Protocol | `20` (data), `21` (control) | TCP | Transferring files between client and server |
   | SMTP | Simple Mail Transfer Protocol | `25` (relay), 587 (submission), 465 (implicit TLS) | TCP | Sending and relaying email |
   | DNS | Domain Name System | `53` | UDP (queries), TCP (zone transfers, large replies) | Translating names to IP addresses |
   | IMAP | Internet Message Access Protocol | `143`, 993 with SSL | TCP | Retrieving email while keeping it on the server |

   Points to note
   - FTP uses `two` ports: 21 carries the commands and 20 carries the data in active mode. In passive mode the data port is negotiated dynamically.
   - SSH replaced Telnet (port 23) because Telnet sends everything, including the password, in plain text.
   - DNS is the only one of these that normally uses UDP, chosen for speed on a single small query and reply.
   - IMAP keeps mail on the server and synchronises across devices; POP3 (port 110) downloads and deletes instead.
   - Secure variants: FTPS 990, SFTP over SSH 22, SMTPS 465, IMAPS 993, POP3S 995, DNS over TLS 853.

2. **What is the port number used by DNS?** *[BBA Assistant Programmer 12.07.2025 compact it 1432 (ET: BUET)], [BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)], [BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: DNS uses port `53`.

   - `UDP port 53` for ordinary queries and responses. UDP is chosen because a lookup is a single small exchange, and the three-way handshake of TCP would triple the delay for no benefit.
   - `TCP port 53` in two cases: zone transfers between primary and secondary name servers (AXFR/IXFR), and any response larger than 512 bytes. In the latter case the server sets the TC (truncated) flag and the resolver retries over TCP. DNSSEC and IPv6 records often exceed the limit.

   Encrypted variants
   - `DoT` — DNS over TLS, TCP port 853.
   - `DoH` — DNS over HTTPS, TCP port 443.
   - `DNSCrypt` — port 443 or 5353.

   Related port numbers

   | Service | Port |
   |---|---|
   | FTP | 20, 21 |
   | SSH | 22 |
   | Telnet | 23 |
   | SMTP | 25 |
   | `DNS` | `53` |
   | DHCP | 67, 68 |
   | HTTP | 80 |
   | POP3 | 110 |
   | IMAP | 143 |
   | HTTPS | 443 |

3. **HTTPS এর পোর্ট নাম্বার কত?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) The port number for HTTPS is `443`.

   - HTTPS (HyperText Transfer Protocol Secure) is HTTP carried inside a TLS-encrypted channel, and it runs over `TCP port 443`.
   - Plain HTTP uses TCP port 80.
   - The TLS handshake happens first: the server presents a certificate signed by a trusted CA, the two sides agree a symmetric session key, and every HTTP message after that is encrypted.
   - HTTP/3 also uses port 443, but over UDP rather than TCP, because it runs on QUIC.

   Common port numbers to remember

   | Service | Port |
   |---|---|
   | FTP | 20, 21 |
   | SSH | 22 |
   | Telnet | 23 |
   | SMTP | 25 |
   | DNS | 53 |
   | DHCP | 67, 68 |
   | HTTP | 80 |
   | POP3 | 110 |
   | IMAP | 143 |
   | SNMP | 161, 162 |
   | `HTTPS` | `443` |
   | RDP | 3389 |

4. **Write the port address of the following applications of data communications. (i) HTTP; (ii) HTTPS; (iii) FTP; (iv) SMTP; (v) POP** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 671 (ET: N/A)]*

   Answer:

   | # | Application | Port | Transport |
   |---|---|---|---|
   | i | HTTP | `80` | TCP |
   | ii | HTTPS | `443` | TCP |
   | iii | FTP | `20` (data) and `21` (control) | TCP |
   | iv | SMTP | `25` (relay); 587 submission, 465 implicit TLS | TCP |
   | v | POP (POP3) | `110`; 995 with SSL | TCP |

   Notes
   - HTTP transfers web pages in plain text; HTTPS is the same protocol inside a TLS-encrypted channel, which is why it needs a separate port.
   - FTP is unusual in using two ports: 21 carries the commands and 20 carries the data in active mode.
   - SMTP sends mail; POP3 and IMAP (143) retrieve it. All three run over TCP because a lost byte would corrupt the message.
   - Port ranges: 0–1023 are well known, 1024–49151 registered, 49152–65535 dynamic or ephemeral (used as the client's source port).

5. **Describe TCP/IP protocols and its ports.** *[BDCCL Assistant Engineer (Network) 2022 compact it 742 (ET: N/A)]*

   Answer:

   The TCP/IP protocol suite by layer

   Application layer

   | Protocol | Full form | Port | Transport | Function |
   |---|---|---|---|---|
   | HTTP | HyperText Transfer Protocol | 80 | TCP | Web pages |
   | HTTPS | HTTP Secure | 443 | TCP | Encrypted web |
   | FTP | File Transfer Protocol | 20, 21 | TCP | File transfer |
   | TFTP | Trivial FTP | 69 | UDP | Simple transfer, device booting |
   | SSH | Secure Shell | 22 | TCP | Encrypted remote login |
   | Telnet | — | 23 | TCP | Plain-text remote login |
   | SMTP | Simple Mail Transfer Protocol | 25, 587 | TCP | Sending email |
   | POP3 | Post Office Protocol 3 | 110 | TCP | Downloading email |
   | IMAP | Internet Message Access Protocol | 143 | TCP | Synchronised email |
   | DNS | Domain Name System | 53 | UDP/TCP | Name resolution |
   | DHCP | Dynamic Host Configuration Protocol | 67, 68 | UDP | Automatic IP configuration |
   | SNMP | Simple Network Management Protocol | 161, 162 | UDP | Device monitoring |
   | NTP | Network Time Protocol | 123 | UDP | Time synchronisation |
   | LDAP | Lightweight Directory Access Protocol | 389 | TCP | Directory services |
   | RDP | Remote Desktop Protocol | 3389 | TCP | Graphical remote access |

   Transport layer
   - `TCP` — connection-oriented, reliable, ordered; three-way handshake, acknowledgements, retransmission, flow control and congestion control. 20-byte header. Used where every byte matters.
   - `UDP` — connectionless, unreliable, fast; 8-byte header, no handshake. Used where timeliness beats completeness.
   - Port ranges: 0–1023 well known, 1024–49151 registered, 49152–65535 dynamic/ephemeral.

   Internet layer
   - `IP` — logical addressing and routing; connectionless and best effort.
   - `ICMP` — error reporting and diagnostics (ping, traceroute); protocol number 1, no ports.
   - `IGMP` — multicast group membership.
   - `ARP` — maps an IP address to a MAC address.
   - Routing protocols: OSPF (IP protocol 89), RIP (UDP 520), BGP (TCP 179), EIGRP (IP protocol 88).

   Network Access layer
   - Ethernet (802.3), Wi-Fi (802.11), PPP, Frame Relay — framing, MAC addressing and physical transmission. No port numbers exist at this layer.

   - A socket is the pair `IP address : port number`, and a TCP connection is uniquely identified by the four-tuple of source IP, source port, destination IP and destination port.

6. **A server has port number 1223. A user is requesting the server (www.example.com) but it is showing server is not reached. How can you solve this?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*

   Answer: The site is unreachable because the browser is not being told which port to use.

   The cause
   - A browser assumes the default ports: `80` for http:// and `443` for https://. When the user types `www.example.com`, the browser connects to port 80 (or 443), but the server is listening on `1223`. Nothing is listening on the default port, so the connection is refused and the browser reports that the server cannot be reached.

   Solutions, in order of preference

   - 1. `Specify the port in the URL` — the immediate fix:
   ```
   http://www.example.com:1223
   ```
   This works at once and proves the diagnosis.

   - 2. `Move the service to the standard port` — configure the web server to listen on 80 or 443. This is the right long-term answer for a public site, since users will not type a port number.

   - 3. `Use port forwarding on the router or firewall` — map incoming traffic on port 80 to internal port 1223:
   ```
   external 203.0.113.5:80  ->  internal 192.168.1.10:1223
   ```

   - 4. `Use a reverse proxy` — Nginx or Apache listens on 80/443 and forwards to 1223 internally. This is the standard production approach, and it also allows TLS termination and multiple sites on one address.

   Other checks if it still fails
   - Confirm the service is actually listening: `netstat -an | grep 1223` or `ss -tlnp`.
   - Confirm the firewall allows port 1223 inbound (`ufw allow 1223`, or the Windows Firewall rule).
   - Confirm DNS resolves the name to the right address: `nslookup www.example.com`.
   - Test connectivity to the port directly: `telnet www.example.com 1223` or `curl -v http://www.example.com:1223`.
   - Check that the server is bound to the correct interface — a service bound only to 127.0.0.1 is unreachable from outside even with the right port.
   - Verify that no other process already holds the port, and that SELinux or similar policy is not blocking it.

## Pulse Code Modulation (PCM) & Signal Processing (6)

1. **A PCM system have step resolution of 2V. Sinusoidal signal amplitude 10V. SNR=? And total number of bits=?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)], [BTCL Assistant Manager (Technical) 2021 compact it 765 (ET: BUET)]*

   Answer:

   Given
   - Step size (resolution) Δ = 2 V
   - Sinusoidal signal amplitude A = 10 V (peak)

   Step 1 — number of quantisation levels
   - The signal swings from −10 V to +10 V, a peak-to-peak range of 20 V.
   ```
   L = peak-to-peak range / step size = 20 / 2 = 10 levels
   ```

   Step 2 — number of bits per sample
   ```
   n = log2(L) = log2(10) = 3.32
   ```
   - A whole number of bits is required, so `n = 4 bits per sample` (giving 16 levels, which covers the 10 needed).

   Step 3 — signal power
   ```
   Ps = A² / 2 = 10² / 2 = 50 W (normalised)
   ```

   Step 4 — quantisation noise power
   ```
   Pq = Δ² / 12 = 2² / 12 = 4 / 12 = 0.3333 W
   ```
   - The Δ²/12 result comes from assuming the quantisation error is uniformly distributed between −Δ/2 and +Δ/2.

   Step 5 — signal-to-noise ratio
   ```
   SNR = Ps / Pq = 50 / 0.3333 = 150
   SNR(dB) = 10 log10(150) = 21.76 dB
   ```

   Check with the standard PCM formula
   ```
   SNR(dB) = 1.76 + 6.02 n
           = 1.76 + 6.02 × 3.32
           = 1.76 + 20.0
           = 21.76 dB     -- the two methods agree
   ```

   | Quantity | Value |
   |---|---|
   | Quantisation levels | 10 |
   | Bits per sample | 3.32, rounded up to `4` |
   | Signal power | 50 W |
   | Quantisation noise power | 0.333 W |
   | `SNR` | `150` |
   | `SNR in dB` | `21.76 dB` |

   - Rule to remember: `every extra bit adds about 6 dB` to the SNR, because it halves the step size and therefore quarters the noise power.

2. **Draw Delta modulation figure and math. (Approximate)** *[NPCBL Executive Trainee (IT) 2022 compact it 648 (ET: BUET)]*

   Answer: Delta modulation (DM) is the simplest form of differential PCM. It transmits only `one bit per sample`, indicating whether the signal has risen or fallen since the last sample.

   How it works
   - The encoder compares the input with a staircase approximation it maintains internally.
   - If the input is `higher`, it sends `1` and steps the staircase up by Δ.
   - If the input is `lower`, it sends `0` and steps the staircase down by Δ.
   - The decoder does the same thing in reverse, then smooths the staircase with a low-pass filter.

   Waveform diagram
   ```
    amplitude
       |            _____
       |         __/     \__            <- original analogue signal m(t)
       |      __/           \__
       |   __/                 \__
       |  /  ___                  \
       | /__|   |___                \
       |/|  |   |   |___             \
       +---------------------------------> time
         staircase approximation follows in steps of Delta

    output bits:  1 1 1 1 1 1 0 0 1 0 0 0 0 0 ...
                   ^rising          ^falling
   ```

   Block diagram
   ```
   TRANSMITTER                          RECEIVER
   m(t) --->(+)---> comparator ---> 1-bit ---> [Accumulator] ---> [LPF] ---> m'(t)
             ^      (1 if +, 0 if -)  output      (integrator)
             |                  |
             |     [Accumulator]<+
             +-----(staircase feedback)
   ```

   The two noise types — the key examination point

   - `Slope overload distortion` — occurs when the signal rises faster than the staircase can climb. The condition to avoid it is:
   ```
   Δ · fs  >=  max |dm/dt|
   ```
   For a sinusoid `Am sin(2π fm t)`, the maximum slope is `Am · 2π fm`, so
   ```
   Δ · fs >= 2π fm Am
   ```
   - `Granular (idle) noise` — occurs when the signal is nearly constant. The staircase hunts up and down by ±Δ around it, producing a small square-wave error. It is reduced by making Δ `smaller` — the opposite of what slope overload demands.

   Worked example
   - Am = 10 V, fm = 4 kHz, Δ = 2 V.
   ```
   Maximum slope = 10 × 2π × 4000 = 251,327 V/s
   fs >= 251,327 / 2 = 125,664 samples/s
   Data rate = 125.66 kbps (one bit per sample)
   ```

   Advantages and drawbacks
   - Advantages: extremely simple hardware, only 1 bit per sample, no need for a codeword framing structure.
   - Drawbacks: requires a very high sampling rate, and suffers from both slope overload and granular noise, which pull the choice of Δ in opposite directions.
   - `Adaptive Delta Modulation (ADM)` solves this by varying Δ automatically — large when the slope is steep, small when the signal is flat.

3. **A singla-tone message signal of bandwidth 4KHZ and amplitude 10V is transmitted by \Delta-modulation with step size 2V. Determine the data rate so that slope overloading noise is the minimum.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

   Answer: To minimise slope overload distortion, the staircase must be able to climb at least as fast as the signal itself.

   Given
   - Message bandwidth (single tone) fm = 4 kHz = 4000 Hz
   - Amplitude Am = 10 V
   - Step size Δ = 2 V

   Step 1 — the slope overload condition
   - For the staircase to keep up, the step size multiplied by the sampling rate must be at least the maximum slope of the signal:
   ```
   Δ · fs  >=  max | dm(t)/dt |
   ```

   Step 2 — maximum slope of the message signal
   - For `m(t) = Am sin(2π fm t)`:
   ```
   dm/dt = Am · 2π fm · cos(2π fm t)
   max |dm/dt| = Am · 2π fm
               = 10 × 2π × 4000
               = 251,327 V/s
   ```

   Step 3 — minimum sampling rate
   ```
   fs >= max slope / Δ
      = 251,327 / 2
      = 125,664 samples per second
   ```

   Step 4 — data rate
   - Delta modulation sends `one bit per sample`:
   ```
   Data rate = fs × 1 bit = 125,664 bps ≈ 125.7 kbps
   ```

   - Answer: the data rate must be at least `125.66 kbps` (about 125.7 kbps).

   Points worth noting
   - Compare this with the Nyquist rate for the same signal, only 8000 samples/s. Delta modulation needs `nearly 16 times` more samples, which is the price of using just one bit each.
   - The trade-off: raising Δ would reduce the required rate, but it would increase `granular noise` when the signal is flat. Lowering Δ reduces granular noise but demands an even higher sampling rate.
   - `Adaptive Delta Modulation` resolves the conflict by varying Δ with the signal slope, giving good performance at a far lower rate.

4. **A single-tone message signal of bandwidth 4 KHZ is sampled by using a pulse train of frequency 200% higher than the Nyquist rate of the message signal to obtain PAM signal. The duty cycle of the pulse train is 20%. By drawing the amplitude spectrum of the PAM signal, determine its bandwidth.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 676 (ET: N/A)]*

   Answer:

   Given
   - Message bandwidth fm = 4 kHz
   - Pulse train frequency = 200 % higher than the Nyquist rate
   - Duty cycle = 20 %

   Step 1 — Nyquist rate
   ```
   fN = 2 × fm = 2 × 4000 = 8000 Hz = 8 kHz
   ```

   Step 2 — actual sampling (pulse train) frequency
   - "200 % higher" means the Nyquist rate plus twice itself, so three times the value:
   ```
   fs = 8 kHz + (200 % of 8 kHz) = 8 + 16 = 24 kHz
   ```

   Step 3 — pulse period and pulse width
   ```
   Ts = 1 / fs = 1 / 24,000 = 41.67 µs
   τ  = duty cycle × Ts = 0.20 × 41.67 = 8.33 µs
   ```

   Step 4 — amplitude spectrum of the PAM signal
   - Natural or flat-top sampling multiplies the message by a rectangular pulse train. In the frequency domain this produces copies of the message spectrum at every multiple of fs, with their amplitudes shaped by a `sinc envelope` whose first null is at `1/τ`.
   ```
   amplitude
      |
      |####      sinc envelope, first null at 1/tau = 120 kHz
      | |  |###
      | |  | |  |##
      | |  | |  | |  |#
      +--+--+--+--+--+--+--+---------------------> f (kHz)
      0  24 48 72 96 120
         ^  ^  ^  ^  ^
         copies of the message spectrum at multiples of fs = 24 kHz,
         each 8 kHz wide, with amplitudes following the sinc envelope
   ```

   Step 5 — bandwidth of the PAM signal
   - The bandwidth is taken up to the first null of the sinc envelope:
   ```
   BW = 1 / τ = 1 / (8.33 × 10^-6) = 120,000 Hz = 120 kHz
   ```

   | Quantity | Value |
   |---|---|
   | Nyquist rate | 8 kHz |
   | Sampling frequency | 24 kHz |
   | Sampling period Ts | 41.67 µs |
   | Pulse width τ | 8.33 µs |
   | `Bandwidth of the PAM signal` | `120 kHz` |

   - The important observation: the PAM bandwidth depends on the `pulse width`, not on the message bandwidth. Narrower pulses (a smaller duty cycle) spread the spectrum further, which is why PAM is far less bandwidth-efficient than the 4 kHz of the original message.

5. **Define pulse amplitude modulation. Explaine the different type of computer network.** *[Sonali & Janata Bank Officer (IT/ICT) 2019 compact it 1107 (ET: AUST)]*

   Answer:

   (a) Pulse Amplitude Modulation
   - PAM is a pulse modulation technique in which the `amplitude` of each pulse in a regularly spaced pulse train is made proportional to the instantaneous amplitude of the analogue message signal at the sampling instant. The pulse width and the pulse position stay constant.
   - It is the first step in producing PCM: sample, then quantise, then encode.
   ```
   message   /\      /\
            /  \    /  \
    -------/----\--/----\-------
   PAM:    | |  |  | |  |     pulses of different heights,
           | |  |  | |  |     equally spaced in time
   ```
   - Two forms: `natural sampling`, where the pulse top follows the signal, and `flat-top sampling`, where the value is held constant for the pulse duration (which introduces the aperture effect).
   - Sampling must satisfy Nyquist: fs >= 2 fm, or aliasing occurs.
   - Bandwidth of the PAM signal is about 1/τ, where τ is the pulse width — much wider than the message bandwidth.
   - Drawbacks: the information is in the amplitude, so it is as vulnerable to noise as AM, and the varying amplitude requires a linear amplifier. This is why PAM is rarely transmitted directly and is instead converted to PCM. Related schemes PWM and PPM put the information in width or position and are far more noise-resistant.
   - Uses: an intermediate step in PCM, LED and motor control, Ethernet line coding (1000BASE-T uses PAM-5, and PAM-4 is used in 400G optics).

   (b) Types of computer network

   | Type | Range | Speed | Ownership | Example |
   |---|---|---|---|---|
   | PAN | 1–10 m | Low | Personal | Bluetooth headset, smartwatch |
   | LAN | Up to ~1 km | Very high, 1–100 Gbps | Private | Office or school network |
   | CAN | A campus | High | Private | University network |
   | MAN | 5–50 km, one city | Medium | Private or public | Cable TV network, city fibre ring |
   | WAN | Country or continent | Lower | Leased from carriers | The internet, a bank's branch network |

   Other classifications
   - By architecture: `client–server` (central control, easier security and backup) and `peer-to-peer` (no central server, cheap, hard to manage at scale).
   - By medium: wired (UTP, coaxial, fibre) and wireless (Wi-Fi, cellular, satellite).
   - By access: intranet (internal only), extranet (opened to selected partners) and internet (public).
   - Special purpose: SAN for storage, WLAN for wireless LAN, VPN for a secure tunnel across a public network.

6. **Consider an audio signal with spectral component limited to the frequency band to 3300Hz. Assume that a sampling rate of 8000s/s with be used to generate a signal power to average needs to be 30dB.** *[NWPGCL Assistant Engineer (CSE) 2019 compact it 1154 (ET: RUET)]*
   a) What the minimum number of bit per sample?
   b) Calculate the minimum channel bandwidth required for transmission of such a PCM signal.

   Answer:

   Given
   - Audio signal limited to 3300 Hz
   - Sampling rate = 8000 samples per second
   - Required signal-to-quantisation-noise ratio = 30 dB

   (a) Minimum number of bits per sample

   - The standard PCM relationship is:
   ```
   SNR(dB) = 1.76 + 6.02 n
   ```
   - Setting this at least equal to 30 dB:
   ```
   1.76 + 6.02 n >= 30
   6.02 n >= 28.24
   n >= 4.69
   ```
   - A whole number of bits is required, so
   ```
   n = 5 bits per sample
   ```
   - Check: with n = 5, SNR = 1.76 + 6.02 × 5 = `31.86 dB`, which satisfies the 30 dB requirement. With n = 4 it would be only 25.84 dB, which fails.

   (b) Minimum channel bandwidth

   Step 1 — bit rate
   ```
   Bit rate = sampling rate × bits per sample
            = 8000 × 5
            = 40,000 bps = 40 kbps
   ```

   Step 2 — minimum bandwidth from Nyquist
   - For binary signalling (2 levels), the Nyquist relation is `C = 2 B log2(L)` with L = 2, so `C = 2B`:
   ```
   B = bit rate / 2 = 40,000 / 2 = 20,000 Hz = 20 kHz
   ```

   | Quantity | Value |
   |---|---|
   | Message bandwidth | 3300 Hz |
   | Sampling rate | 8000 samples/s |
   | Quantisation levels | 2^5 = 32 |
   | `Bits per sample` | `5` |
   | Bit rate | 40 kbps |
   | `Minimum channel bandwidth` | `20 kHz` |

   Points worth noting
   - Sampling at 8000 samples/s satisfies Nyquist for 3300 Hz (which requires at least 6600), and the extra margin leaves room for the anti-aliasing filter to roll off.
   - The digitised signal needs 20 kHz of channel bandwidth against the original 3.3 kHz — roughly six times more. That is the cost of digitisation, paid for by noise immunity and perfect regeneration.
   - Using a multi-level line code (L = 4) would halve the required bandwidth to 10 kHz, at the price of needing a higher SNR.
   - Rule to remember: `each extra bit adds about 6 dB` of SNR and increases the bit rate by one sampling-rate's worth.

## Switching Techniques (Circuit vs Packet Switching) (5)

1. **Why is packet switching more suitable for internet communication?** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

   Answer: Packet switching suits internet communication because internet traffic is `bursty`, the network is `enormous and shared`, and reliability must survive partial failure. Circuit switching fails on all three counts.

   Reasons

   - `Efficient use of capacity.` A web session sends a burst of data then sits idle while the user reads. A circuit reserves bandwidth for the whole session, so it is idle most of the time and wasted. Packet switching gives the link to whoever has data at that instant, so one link serves many users through statistical multiplexing.

   - `No setup delay.` Circuit switching must establish an end-to-end path before any data moves. Packet switching sends immediately, which matters when a page load involves dozens of short connections to different servers.

   - `Robustness.` Each packet is routed independently, so if a link or router fails, later packets simply take another path. A circuit is destroyed by a single failure along its path and must be rebuilt. This survivability was the original design goal of ARPANET.

   - `Scalability.` The internet has billions of hosts. Reserving a dedicated circuit for every pair is impossible; packet switching requires no per-conversation state in the core routers.

   - `Supports variable rates.` Applications range from a 100-byte DNS query to a 4K video stream. Packets adapt automatically; a fixed circuit cannot.

   - `Cost.` Sharing links among many users lowers the cost per user dramatically, and no expensive per-circuit reservation machinery is needed.

   - `Natural fit for digital data.` Data is naturally chunked into messages, and errors can be detected and the individual packet retransmitted, rather than corrupting a continuous stream.

   - `Different services on one network.` Web, email, voice and video all travel as packets over the same infrastructure, which is why the telephone network itself has converged onto IP.

   The trade-off
   - Packet switching gives no bandwidth guarantee, and it introduces variable delay (jitter), out-of-order arrival and possible loss. These are handled above the network layer: TCP restores order and reliability, and QoS, buffering and jitter buffers handle real-time traffic. The internet accepted these costs because the gains in efficiency and robustness are overwhelming.

2. **Difference between circuit switching and packet switching. Identify which of the two is predominantly used in Internet communication and justify why?** *[BUET Assistant Programmer 21.06.2025 compact it 1435 (ET: BUET)]*

   Answer:

   Comparison

   | Point | Circuit switching | Packet switching |
   |---|---|---|
   | Path | A dedicated physical path reserved end to end for the whole session | No dedicated path; each packet is routed independently |
   | Setup | Connection must be established first | None; send immediately |
   | Bandwidth | Reserved and guaranteed, wasted when idle | Shared; allocated on demand |
   | Efficiency | Low for bursty traffic | High — statistical multiplexing |
   | Delay | Setup delay, then constant transmission delay | No setup delay, but variable queuing delay |
   | Jitter | None | Present |
   | Order of arrival | Always in order | May arrive out of order |
   | Reliability on failure | The whole call drops | Packets reroute around the failure |
   | Store and forward | No | Yes, at every router |
   | Charging | By time and distance | By volume of data |
   | Congestion effect | New calls are blocked; existing ones unaffected | Everyone slows down; packets may be dropped |
   | Overhead | Low per byte, no headers | Header on every packet |
   | Suited to | Continuous, constant-rate traffic | Bursty, variable-rate traffic |
   | Examples | Traditional telephone network, ISDN, leased line | The internet, Ethernet, X.25, Frame Relay |

   Which is used on the internet, and why
   - `Packet switching` is used predominantly on the internet.

   Justification
   - `Traffic is bursty.` A user loads a page, then reads it for a minute. A reserved circuit would sit idle for that minute. Packet switching gives the capacity to someone else in the meantime.
   - `Efficiency through statistical multiplexing.` Because not all users are active simultaneously, one link can serve far more subscribers than its raw capacity would suggest under circuit switching.
   - `Robustness.` Packets route around a failed link automatically. This survivability was the founding requirement of ARPANET, from which the internet grew.
   - `Scalability.` Billions of hosts cannot each hold a reserved circuit; the core routers keep no per-conversation state at all.
   - `No setup delay`, which matters greatly when a single web page opens dozens of short connections.
   - `One network for every service` — web, mail, voice and video all become packets, which is why even telephony has migrated to VoIP over IP.
   - `Lower cost`, since capacity is shared rather than reserved.

   - The costs — variable delay, possible loss and out-of-order arrival — are handled above the network layer by TCP, and by QoS and jitter buffers for real-time traffic. They are a small price for the efficiency and resilience gained.

3. **(c) Compare circuit switching and packet switching.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1353 (ET: N/A)]*

   Answer:

   | Point | Circuit switching | Packet switching |
   |---|---|---|
   | Resource allocation | Dedicated path reserved for the entire session | No reservation; resources shared on demand |
   | Connection setup | Required before any data flows | Not required (datagram); optional in virtual circuits |
   | Bandwidth | Fixed and guaranteed | Variable, shared |
   | Utilisation | Poor for bursty traffic — the circuit is idle much of the time | High, through statistical multiplexing |
   | Delay | Setup delay first, then constant | No setup delay, but variable queuing delay at each hop |
   | Jitter | None | Present |
   | Packet order | Always preserved | May arrive out of order (datagram) |
   | Store and forward | No | Yes, at every intermediate node |
   | Header overhead | None during the call | A header on every packet |
   | Effect of a link failure | The call is dropped | Packets reroute automatically |
   | Effect of congestion | New calls are blocked; existing calls unaffected | Everyone experiences delay; packets may be dropped |
   | Reliability of delivery | Guaranteed once connected | Best effort; TCP adds reliability above |
   | Billing | By duration and distance | By volume of data |
   | Complexity in the node | Simple switching once set up | Routing decision for every packet |
   | Best suited to | Continuous constant-rate traffic — voice | Bursty variable-rate traffic — data |
   | Examples | PSTN telephone, ISDN, leased line, SONET | Internet, Ethernet, X.25, Frame Relay, MPLS |

   Three phases of circuit switching
   - Setup, data transfer, teardown.

   Two kinds of packet switching
   - `Datagram` — every packet is routed independently and may take a different path (the internet, IP).
   - `Virtual circuit` — a path is agreed first and all packets follow it in order, but bandwidth is still shared (X.25, Frame Relay, ATM, MPLS). It combines the ordering of circuit switching with the efficiency of packet switching.

   - Summary: circuit switching guarantees quality by wasting capacity; packet switching maximises capacity by giving up guarantees. The internet chose the second and rebuilt the guarantees where needed, using TCP and QoS.

4. **Do you prefer packet switching compared to circuit switching in communication network? If Yes, why? How does packet switching work step by step? What applications use packet switching?** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 536 (ET: MIST)]*

   Answer:

   Do I prefer packet switching? — `Yes`, for a general communication network.

   Why

   - `Efficiency.` Traffic is bursty. A circuit reserves bandwidth for a whole session and wastes it whenever the user is idle. Packet switching gives the link to whoever has data at that moment, so one link serves many more users.
   - `No setup delay.` Data can be sent immediately, without first building an end-to-end path.
   - `Robustness.` Each packet is routed independently, so a failed link is simply avoided by subsequent packets. A circuit is destroyed by any single failure along it.
   - `Scalability.` No per-conversation state is held in core routers, so the network can grow to billions of hosts.
   - `Handles variable rates` — from a 100-byte DNS query to a 4K video stream, on the same infrastructure.
   - `Lower cost` per user, because capacity is shared rather than reserved.
   - `Error handling per packet` — only the damaged packet is retransmitted, not the whole transfer.

   The honest trade-off
   - Packet switching gives no bandwidth guarantee and introduces variable delay, jitter, reordering and possible loss. TCP restores order and reliability, and QoS, MPLS and jitter buffers manage real-time traffic. Circuit switching remains preferable only where a constant guaranteed rate is essential and traffic is continuous.

   How packet switching works, step by step

   - Step 1 — `Segmentation.` The message is divided into packets of a manageable size, typically up to 1500 bytes on Ethernet.
   - Step 2 — `Encapsulation.` Each packet receives a header containing the source and destination IP addresses, a sequence number, TTL and a checksum.
   - Step 3 — `Transmission.` The packet is sent to the first router; no path is reserved in advance.
   - Step 4 — `Store and forward.` Each router receives the whole packet, checks its integrity, consults its routing table, and queues it for the correct outgoing interface.
   - Step 5 — `Independent routing.` Each packet is forwarded by longest prefix match, and different packets of the same message may take different paths as conditions change.
   - Step 6 — `Queuing.` If the outgoing link is busy, the packet waits in a buffer. If the buffer is full it is dropped — this is where congestion becomes loss.
   - Step 7 — `Reassembly.` The destination uses the sequence numbers to put packets back in order and rebuild the original message.
   - Step 8 — `Error recovery.` Missing or corrupted packets are detected and retransmitted by TCP.

   ```
   Message -> [P1][P2][P3][P4] -> different paths -> reassembled at the destination

              /-- R1 -- R3 --\
   Sender ---+                +--- Receiver
              \-- R2 -- R4 --/
   ```

   Applications that use packet switching
   - The entire internet: web (HTTP/HTTPS), email (SMTP, IMAP), file transfer (FTP), DNS.
   - Ethernet and Wi-Fi LANs.
   - VoIP and video conferencing (Zoom, WhatsApp calls) — voice itself has migrated to packets.
   - Streaming video (YouTube, Netflix) and online gaming.
   - Mobile data networks: 4G LTE and 5G are entirely packet-switched, unlike 2G voice.
   - Cloud computing, IoT, and WAN technologies such as MPLS, Frame Relay and X.25.

5. **Why is packet suiting suitable for digital data transmission?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 681 (ET: N/A)]*

   Answer: Packet switching suits digital data transmission because digital data is naturally discrete and bursty, which is exactly what packet switching handles best.

   Reasons

   - `Data is naturally chunked.` A file, a web page or an email is already a discrete block of bits, so dividing it into packets is natural. Voice, by contrast, is a continuous stream, which is why the telephone network originally used circuits.

   - `Traffic is bursty.` A computer sends a burst then falls silent while the user reads or thinks. Reserving a circuit for the idle periods wastes almost all of the reserved capacity; packet switching gives that capacity to another user instantly.

   - `Statistical multiplexing.` Because not every user is active at once, one link can serve far more subscribers than its raw capacity would allow under reservation. This is the single largest efficiency gain.

   - `Error detection and selective retransmission.` Each packet carries its own checksum, so a corrupted packet is detected and only that packet is resent. In a continuous circuit an error corrupts the stream with no easy way to repair just the damaged part.

   - `Variable data rates are supported naturally.` The same network carries a 100-byte DNS query and a gigabit video stream without reconfiguration.

   - `No setup delay.` A short transaction — a DNS lookup, an API call — completes in milliseconds. Building and tearing down a circuit for it would cost far more time than the transfer itself.

   - `Robustness.` Packets route around failed links automatically, so a partial network failure degrades performance instead of dropping the connection.

   - `Sequence numbers restore order.` Digital data can be numbered, buffered and reassembled exactly, so out-of-order arrival is a solvable problem — which it is not for an analogue stream.

   - `Scalability and low cost.` No per-conversation state in the core, and shared links, so the cost per user falls as the network grows.

   - `Digital regeneration.` Each store-and-forward hop reads the bits and generates a clean new signal, so noise does not accumulate along the path.

   - Summary: packet switching matches the character of digital data — discrete, bursty, variable in rate, and repairable packet by packet — and it converts what would be wasted idle capacity into throughput for other users.

## WAN Technologies (SONET/SDH, ATM, WDM) (5)

1. **White short notes on: (i) SONET/SDH; (ii) IP telephony; (iii) WDM technology; (iv) ATM network** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

   Answer:

   (i) SONET / SDH
   - SONET (Synchronous Optical Network, the North American standard) and SDH (Synchronous Digital Hierarchy, the international standard) are TDM-based optical transport standards for carrying many digital streams synchronously over fibre.
   - Hierarchy: SONET OC-1 = 51.84 Mbps, OC-3 = 155.52, OC-12 = 622, OC-48 = 2.5 Gbps, OC-192 = 10 Gbps. The SDH equivalents are STM-1 = 155.52 Mbps, STM-4, STM-16, STM-64.
   - Frame: 810 bytes sent 8000 times a second, giving the 51.84 Mbps base rate. Rich overhead bytes carry management, performance monitoring and fault information.
   - Topology: usually a `dual counter-rotating ring`, which gives automatic protection switching in under `50 ms` after a fibre cut. This resilience is its main selling point.
   - Uses: carrier backbones, metro rings, leased-line delivery. It is now being displaced by packet-optical transport (OTN and carrier Ethernet), because rigid TDM channels suit voice better than bursty data.

   (ii) IP telephony
   - IP telephony (VoIP) carries voice as IP packets rather than over a dedicated circuit.
   - Process: the analogue voice is digitised and compressed by a codec (G.711, G.729, Opus), packetised into 20 ms chunks, carried by `RTP over UDP`, and reassembled and played out at the far end.
   - Signalling: `SIP` (most common), H.323, or Cisco's SCCP. RTCP reports quality back.
   - Advantages: far lower cost, especially for international calls; one network for voice and data; rich features (voicemail to email, presence, conferencing); easy scaling.
   - Challenges: it needs QoS, because voice tolerates only about 150 ms of one-way delay, 30 ms of jitter and 1 percent loss; it depends on power and on the data network; and emergency-call location is harder.
   - Equipment: IP phones or softphones, a VoIP gateway to the PSTN, an IP PBX, and a QoS-capable network.

   (iii) WDM technology
   - WDM (Wavelength Division Multiplexing) sends several optical signals of different wavelengths down one fibre at the same time. It is FDM applied to light.
   - `CWDM` — coarse WDM, up to 18 channels spaced 20 nm apart; cheap, uncooled lasers, short reach.
   - `DWDM` — dense WDM, 40 to 160 channels on a 100 or 50 GHz grid in the C band around 1550 nm; each channel carries 10, 100 or 400 Gbps, so one fibre carries tens of terabits.
   - Components: DFB lasers, arrayed waveguide grating multiplexers, EDFA amplifiers (which amplify every channel at once), dispersion compensators and optical add-drop multiplexers.
   - Advantages: multiplies the capacity of installed fibre without laying new cable, is protocol and bit-rate transparent, and one EDFA serves all channels.
   - It is what makes submarine cables and internet backbones economically possible.

   (iv) ATM network
   - ATM (Asynchronous Transfer Mode) is a `virtual-circuit`, cell-switched technology designed to carry voice, video and data on one network.
   - It uses a fixed `53-byte cell`: 5 bytes of header and 48 bytes of payload. The small fixed size makes switching simple and fast in hardware, and bounds the delay for voice.
   - Header fields: VPI and VCI identify the virtual path and channel; the switch swaps these labels at each hop.
   - Connection-oriented: a virtual circuit is set up before data flows, so cells always arrive in order.
   - Service classes give real QoS: CBR (constant bit rate, for voice), VBR, ABR and UBR.
   - Advantages: guaranteed QoS, high speed, and one network for all traffic types.
   - Disadvantages: the 5-byte header on a 48-byte payload is about 10 percent overhead — the so-called "cell tax" — and it is complex and expensive. It has been largely replaced by IP and MPLS, though it survives in some DSL and carrier networks.

2. **(c) Explain IPTV and VOIP.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 794 (ET: N/A)]*

   Answer:

   IPTV — Internet Protocol Television
   - IPTV delivers television content as IP packets over a managed network, instead of by terrestrial broadcast, satellite or cable RF.
   - It is normally carried on the operator's own network with QoS guarantees, which distinguishes it from ordinary internet video (OTT services such as YouTube or Netflix, which cross the public internet with no guarantee).

   How it works
   - Live channels are encoded (H.264 or H.265), then delivered by `IP multicast` — one stream serves every viewer of that channel, so bandwidth does not grow with the audience. `IGMP` is used by set-top boxes to join and leave channel groups, which is what channel changing actually does.
   - Video on demand uses unicast, since each viewer watches a different point in a different programme.
   - Equipment: an encoder and streaming server, a QoS-enabled multicast-capable network, and a set-top box or smart TV at the customer.

   Three service types
   - Live television, video on demand (VOD), and time-shifted TV such as catch-up and network PVR.

   Advantages
   - Two-way and interactive: pause, rewind, VOD, electronic programme guide, and personalisation.
   - Efficient use of bandwidth through multicast; unlimited channel capacity, unlike the fixed spectrum of RF broadcast.
   - Integrates with the operator's voice and internet services on one access line (triple play).

   Challenges
   - Needs sustained bandwidth (about 5 Mbps for HD, 25 Mbps for 4K) and strict QoS — packet loss produces visible blocking.
   - Requires multicast support throughout the network, and content protection (DRM).

   VoIP — Voice over Internet Protocol
   - VoIP carries telephone calls as IP packets rather than over a circuit-switched line.

   How it works
   - The analogue voice is sampled and compressed by a `codec` — G.711 (64 kbps, toll quality), G.729 (8 kbps), Opus (adaptive).
   - Samples are packetised into roughly 20 ms chunks and carried by `RTP over UDP`. UDP is chosen because a retransmitted late packet is useless; a lost one is concealed instead.
   - `SIP` handles signalling — registration, call setup, ringing, teardown. H.323 and SCCP are alternatives. `RTCP` reports quality statistics back.
   - A jitter buffer at the receiver absorbs variation in arrival time before playback.

   Equipment needed
   - IP phones or softphones, an IP PBX or SIP server, a VoIP gateway to reach the PSTN, an internet connection with adequate upstream bandwidth, and a QoS-capable router.

   Advantages
   - Much lower cost, especially internationally; one network for voice and data; features such as voicemail to email, presence, call recording and conferencing; easy to add extensions; and mobility, since a number follows the user anywhere.

   Challenges and quality targets
   - One-way delay should stay under `150 ms`, jitter under `30 ms`, and packet loss under `1 percent`. Beyond these, quality is noticeably poor.
   - It depends on power and on the data network, so a failure takes down the telephones too. Emergency-call location and lawful interception are harder than on the PSTN, and security requires SRTP and TLS to prevent eavesdropping and toll fraud.

3. **Write the full form of the given technologies CX, IGW and IIG. Write feature of there technologies.** *[BTRC Assistant Director (Technical) 2021 compact it 806 (ET: IBA)]*

   Answer:

   Full forms

   | Abbreviation | Full form |
   |---|---|
   | ICX | `Interconnection Exchange` (the question's "CX" is the ICX licence) |
   | IGW | `International Gateway` |
   | IIG | `International Internet Gateway` |

   - These are the three licence categories created by BTRC to structure Bangladesh's international and interconnection telecom traffic.

   ICX — Interconnection Exchange
   - Sits `inside` the country and interconnects domestic operators. Calls between two different mobile operators, or between a mobile network and a PSTN, are routed through an ICX rather than directly.
   - Features: switches domestic voice traffic between operators; records call detail for revenue sharing and settlement; enforces the regulator's tariff and revenue-sharing rules; provides a single controlled point where domestic interconnection can be monitored; and passes international calls from an IGW down to the terminating operator.
   - Benefit of the model: operators need one connection to an ICX instead of separate links to every other operator, which greatly reduces the number of interconnection links required.

   IGW — International Gateway
   - The gateway for `international voice` traffic entering and leaving Bangladesh.
   - Features: originates outgoing and terminates incoming international calls; interfaces with foreign carriers over both TDM and IP; handles settlement with those carriers; applies the regulator's approved termination rate; and provides the lawful-interception and monitoring point required for international voice.
   - Incoming international calls flow: foreign carrier -> IGW -> ICX -> the terminating mobile or PSTN operator.

   IIG — International Internet Gateway
   - The gateway for `international internet and data` traffic.
   - Features: connects the country's ISPs to the global internet through submarine cables (SEA-ME-WE 4, 5 and 6) and terrestrial cross-border links (ITC); provides bandwidth wholesale to ISPs; peers with international carriers and content providers; hosts caches and CDN nodes to keep popular content local; and provides the monitoring and filtering point for international data.
   - It is the data counterpart of the IGW, which handles only voice.

   Traffic flow through the three
   ```
   INTERNATIONAL VOICE
   foreign carrier --> IGW --> ICX --> mobile / PSTN operator --> subscriber

   INTERNATIONAL INTERNET
   global internet --> submarine cable / ITC --> IIG --> ISP --> subscriber
   ```

   - Note on current policy: BTRC has been consolidating these layers, and IGW, ICX and IIG licences are being phased out on expiry in favour of a broader international-connectivity licence, so the structure described here is the classical one that exam questions are set on. <!-- verify -->

4. **TSCM এর কাজ কী? VoIP পরিচালনায় কী কী সরঞ্জামের প্রয়োজন হয়?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 810 (ET: IBA)]*

   Answer: (Answered in English, as required for IT topics.)

   TSCM — Technical Surveillance Counter-Measures
   - TSCM is the practice of `detecting and neutralising illicit surveillance devices` — hidden microphones, cameras, GPS trackers, phone taps and other eavesdropping equipment. It is commonly called a "bug sweep".

   What TSCM work involves
   - `Radio frequency spectrum analysis` to detect transmitters hidden in a room.
   - `Physical inspection` of furniture, ceilings, power outlets, telephone instruments and cabling.
   - `Non-linear junction detection`, which finds electronic components even when they are switched off.
   - `Thermal imaging` to spot devices generating heat behind surfaces.
   - `Telephone and line analysis` to detect taps and unauthorised connections.
   - `Wi-Fi and network scanning` for unauthorised access points and covert devices.
   - Producing a report and recommending physical and procedural countermeasures.

   Where it is used: government offices, boardrooms, embassies, courts, and any place where confidential discussions take place. For a regulator such as BTRC it also covers verifying that telecom facilities are free of unauthorised interception equipment. <!-- verify -->

   Equipment needed to operate VoIP

   Terminal equipment
   - `IP phones` — handsets with a built-in Ethernet port and codec, usually powered over Ethernet (PoE).
   - `Softphones` — software on a PC or smartphone, with a headset or the device's own microphone.
   - `ATA (Analogue Telephone Adapter)` — lets an ordinary analogue telephone connect to a VoIP service.

   Call control
   - `IP PBX or SIP server` — Asterisk, FreePBX, 3CX or a hosted service. It handles registration, dial plans, extensions, voicemail, call routing and conferencing.
   - `SIP trunk` from a provider, replacing traditional telephone lines.

   Interconnection
   - `VoIP gateway` — converts between IP and the PSTN, so calls can reach ordinary telephone numbers. It houses FXS ports (to analogue phones) and FXO ports (to telephone lines), or E1/T1 interfaces.
   - `Session Border Controller (SBC)` — sits at the network edge for security, NAT traversal, topology hiding and codec conversion.

   Network infrastructure
   - `Internet connection` with adequate and stable upstream bandwidth — about 100 kbps per concurrent call with G.711, 30 kbps with G.729.
   - `Router and switch with QoS`, marking voice traffic with DSCP EF so it is queued ahead of data. This is essential, not optional.
   - `PoE switch` to power the phones over the same cable.
   - `UPS`, because unlike a traditional telephone, an IP phone stops working in a power cut.

   Software and protocols
   - `SIP` for signalling, `RTP` over UDP for the media, `RTCP` for quality reporting, and codecs G.711, G.729 or Opus.
   - `SRTP and TLS` for encryption, and a firewall configured for VoIP.

   Quality targets to design for
   - One-way delay under 150 ms, jitter under 30 ms, packet loss under 1 percent.

5. **Write down the difference between IPoE and PPPoE.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 839-840 (ET: N/A)]*

   Answer:

   | Point | PPPoE | IPoE |
   |---|---|---|
   | Full form | Point-to-Point Protocol over Ethernet | Internet Protocol over Ethernet |
   | Nature | Connection-oriented — a PPP session is established first | Connectionless — IP packets go straight into Ethernet frames |
   | Encapsulation | PPP frame inside an Ethernet frame | IP packet directly inside an Ethernet frame |
   | Address assignment | Through IPCP during PPP negotiation | Through `DHCP` |
   | Authentication | Built in — PAP or CHAP with username and password | None inherent; identity is derived from DHCP option 82, the MAC address, or the physical port |
   | Client software | Required (a PPPoE dialler on the router or PC) | Not required — the device just uses DHCP |
   | Overhead | 8 extra bytes, reducing the MTU from 1500 to `1492` | None; full 1500-byte MTU |
   | MTU problems | Common — fragmentation and "black hole" issues need MSS clamping | None |
   | Session state | The BRAS keeps per-subscriber session state | Stateless, or light DHCP lease state |
   | Accounting | Easy and precise, per session | Harder; relies on DHCP lease and port mapping |
   | Multicast / IPTV | Poorly suited; multicast must be replicated per session | Well suited — native multicast, which is why IPTV uses it |
   | Scalability | Session table limits the BRAS | Higher; less state per subscriber |
   | Setup speed | Slower — discovery, session and authentication stages | Faster; DHCP only |
   | Typical use | Traditional DSL broadband | Fibre (GPON), cable, and triple-play networks |

   PPPoE session stages
   - Discovery (PADI, PADO, PADR, PADS) to find the access concentrator and open a session, then the PPP session itself with LCP, authentication and IPCP.

   Which is better
   - `IPoE` is preferred for modern fibre and triple-play networks: no client software, full 1500-byte MTU, faster connection, and native multicast for IPTV. Subscriber identification is handled instead by DHCP option 82, which tells the server exactly which port and which device the request came from.
   - `PPPoE` remains valuable where per-subscriber authentication and accounting must be built into the access protocol itself, particularly on legacy DSL networks, and where the operator wants a username and password rather than trusting the physical port.

## Network Layer (Packet Fragmentation & Tunneling) (4)

1. **(a) How do you define packet fragmentation? Explain briefly the transparent and non-transparent fragmentation with necessary diagram.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 481 (ET: N/A)]*

   Answer:

   What is packet fragmentation
   - Fragmentation is the process of dividing a packet into smaller pieces so that it can pass through a network whose `MTU` (Maximum Transmission Unit) is smaller than the packet.
   - It is needed because different networks have different MTUs: Ethernet 1500 bytes, PPPoE 1492, FDDI 4352, and some WAN links far less. A packet crossing from one to another may simply be too large.
   - Each fragment becomes a packet in its own right, carrying the same identification number, its own fragment offset, and a More Fragments (MF) flag which is 1 on every fragment except the last.

   Transparent fragmentation
   - The network that fragments a packet also `reassembles it before the packet leaves`. The exit gateway of that network rebuilds the original packet, so the next network never knows fragmentation occurred.
   ```
           NETWORK 1 (MTU 1500)        NETWORK 2 (MTU 512)         NETWORK 3 (MTU 1500)
     Host --[G1]------------------->[G2]---F1--F2--F3--->[G3]------------------->Host
             full packet          fragments here      reassembles here
                                                      full packet again
   ```
   - Advantages: each network is independent; the destination host is not burdened with reassembly; and every fragment must follow the same path, so ordering is simple.
   - Disadvantages: every exit gateway needs buffers and timers for reassembly; all fragments are forced through one exit gateway, which prevents multipath routing; and if the packet must be fragmented again in the next network, the work is repeated. It is slower overall.
   - Used by: ATM and X.25.

   Non-transparent fragmentation
   - The fragments are `not reassembled` by the exit gateway. Each travels independently as a full datagram, and reassembly is done only at the `destination host`.
   ```
           NETWORK 1              NETWORK 2 (MTU 512)         NETWORK 3
     Host --[G1]------------->[G2] --F1--> ... --> [G3] --F1--> 
                                   --F2-->            --F2-->    Destination
                                   --F3-->            --F3-->    reassembles
   ```
   - Advantages: gateways stay simple and stateless; fragments may take different routes; and there is no need for all fragments to converge on one exit gateway. This suits a datagram network.
   - Disadvantages: every fragment carries a full header, so overhead is higher; the destination must buffer fragments and run a reassembly timer; and if any single fragment is lost, the whole original packet is discarded.
   - Used by: `IPv4`, which is the important case.

   | Point | Transparent | Non-transparent |
   |---|---|---|
   | Reassembled by | The exit gateway of each network | The destination host only |
   | Gateway complexity | High — buffers and timers | Low |
   | Routing | All fragments must use one exit gateway | Fragments may take different paths |
   | Overhead | Lower, repeated per network | Higher, header on every fragment |
   | Repeated fragmentation | Yes, in each network | No, fragments stay fragmented |
   | Used by | ATM, X.25 | IPv4 |

   - Note on IPv6: routers are `not allowed` to fragment at all. Only the source may fragment, using a Fragment extension header, and Path MTU Discovery is used to find the smallest MTU on the route in advance. This keeps routers simple and fast.

2. **(b) Describe briefly the TCP/IP tunneling using appropriate diagram.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 482 (ET: N/A)]*

   Answer: Tunnelling is the technique of `encapsulating one protocol's packet inside another protocol's packet`, so that it can travel across an intermediate network that does not support it.

   Why it is needed
   - Two networks running one protocol may be separated by a network that speaks a different one. Rather than translating, the original packet is wrapped up, carried across as ordinary payload, and unwrapped at the far end. The intermediate network never has to understand it.

   Diagram — two IPv6 islands joined across an IPv4 internet
   ```
      IPv6 NETWORK A                                     IPv6 NETWORK B
     +--------------+     +------------+   +------------+   +--------------+
     | Host A       |     | Router R1  |   | Router R2  |   | Host B       |
     | 2001:db8::1  |---->| entry point|   | exit point |-->| 2001:db8::2  |
     +--------------+     +------+-----+   +-----+------+   +--------------+
                                 |               |
                                 |   IPv4 INTERNET (the tunnel)
                                 +===============+
                           encapsulate      decapsulate
   ```

   The packet as it travels
   ```
   Inside network A:      | IPv6 hdr | payload |

   Inside the tunnel:     | IPv4 hdr | IPv6 hdr | payload |
                            ^ src = R1, dst = R2 (both IPv4 addresses)

   Inside network B:      | IPv6 hdr | payload |   (original packet restored)
   ```

   Step by step
   - Step 1 — Host A sends an ordinary IPv6 packet towards Host B.
   - Step 2 — Router R1, the tunnel entry point, sees that the next network cannot carry IPv6. It `encapsulates` the whole IPv6 packet as the payload of a new IPv4 packet addressed from R1 to R2.
   - Step 3 — the IPv4 internet forwards it like any other IPv4 packet. It has no idea what the payload is.
   - Step 4 — Router R2, the tunnel exit point, receives it, strips the IPv4 header, and recovers the original IPv6 packet unchanged.
   - Step 5 — R2 forwards the IPv6 packet natively to Host B.

   Common tunnelling protocols

   | Protocol | Carries | Typical use |
   |---|---|---|
   | 6to4, 6in4, Teredo, ISATAP | IPv6 over IPv4 | IPv6 transition |
   | GRE | Almost anything over IP | Site-to-site links, carrying routing protocols |
   | IPsec (tunnel mode) | IP over IP, encrypted | Secure site-to-site VPN |
   | L2TP, PPTP | Layer 2 frames over IP | Remote-access VPN |
   | VXLAN | Ethernet over UDP | Data centre network virtualisation |
   | MPLS | Labelled IP | Carrier backbones |
   | SSH tunnel | TCP over SSH | Secure port forwarding |

   Advantages and drawbacks
   - Advantages: allows incompatible networks to interconnect; supports gradual migration (IPv4 to IPv6); creates private virtual links across a public network; and, with IPsec, adds encryption and authentication.
   - Drawbacks: the extra header reduces the effective MTU and can cause fragmentation (MSS clamping is the usual remedy); it adds processing overhead at both endpoints; and it can bypass firewall inspection, which is a genuine security concern — an unmonitored Teredo or 6to4 tunnel can carry traffic straight past an IPv4-only firewall.

3. **Why network need packet fragmentation? Define different types of packet fragmentation with necessary diagram.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 666 (ET: N/A)]*

   Answer:

   Why a network needs packet fragmentation
   - Different networks have different `MTU` values — the largest packet they can carry. Ethernet allows 1500 bytes, PPPoE 1492, FDDI 4352, and some WAN and tunnel links considerably less.
   - When a packet has to cross from a network with a large MTU into one with a smaller MTU, it is simply too big to pass. The choice is to discard it or to divide it. Fragmentation divides it.
   - Without fragmentation, hosts would have to know the smallest MTU on every possible path in advance, and any change of route could break communication.
   - It also lets a single large transfer proceed across a heterogeneous internetwork without the application having to know anything about the underlying media.

   The IPv4 header fields used
   - `Identification` (16 bits) — the same value in every fragment of one original packet, so the destination knows which fragments belong together.
   - `Flags` — DF (Don't Fragment) and MF (More Fragments). MF is 1 in every fragment except the last.
   - `Fragment Offset` (13 bits) — the position of this fragment's data within the original packet, measured in units of `8 bytes`. This is why every fragment except the last must contain a multiple of 8 bytes of data.

   Types of fragmentation

   1. Transparent fragmentation
   - The network that fragments the packet also `reassembles it at its own exit gateway`, so the next network receives the original whole packet and never learns that fragmentation happened.
   ```
      NETWORK 1              NETWORK 2 (small MTU)          NETWORK 3
   Host--[G1]--full packet-->[G2]--F1-F2-F3-->[G3]--full packet-->Host
                           fragments        reassembles
   ```
   - Advantages: networks stay independent; the destination host does no reassembly work; only one fragmentation stage per network.
   - Disadvantages: every exit gateway needs reassembly buffers and timers; all fragments must pass through the same exit gateway, which forbids multipath routing; and repeated fragmentation and reassembly is slow.
   - Used by ATM and X.25.

   2. Non-transparent fragmentation
   - Fragments are `never reassembled in transit`. Each becomes an independent datagram and travels on its own, and only the `destination host` reassembles.
   ```
      NETWORK 1         NETWORK 2 (small MTU)      NETWORK 3
   Host--[G1]------->[G2]--F1-->  ...  -->[G3]--F1--> Destination
                         --F2-->              --F2--> reassembles
                         --F3-->              --F3-->
   ```
   - Advantages: gateways stay simple and stateless; fragments may take different routes; no convergence on a single exit gateway is required.
   - Disadvantages: every fragment carries a full header, so overhead is greater; the destination must buffer and run a reassembly timer; and losing one fragment destroys the entire original packet.
   - Used by `IPv4`.

   | Point | Transparent | Non-transparent |
   |---|---|---|
   | Reassembly point | Exit gateway of each network | Destination host |
   | Gateway state | Buffers and timers needed | Stateless |
   | Routing of fragments | All through one exit gateway | Independent paths allowed |
   | Header overhead | Lower | Higher |
   | Used by | ATM, X.25 | IPv4 |

   - IPv6 removed router fragmentation entirely: only the source may fragment, using a Fragment extension header, and hosts use `Path MTU Discovery` to learn the smallest MTU on the route beforehand. This keeps routers simple and fast, and it is one of the main reasons the IPv6 header dropped from 13 fields to 8.

4. **Suppose a 22-byte packet is to be transmitted through a network of \text{MTU} = 3\text{ byte}. The elementary fragment size is 1\text{ byte}. Show the segment numbering of the above packet. Packet number is 217.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*

   Answer:

   Given
   - Original packet size = 22 bytes of data
   - MTU = 3 bytes (data per fragment)
   - Elementary fragment size = 1 byte, so the offset is counted in units of 1 byte
   - Packet identification number = 217

   Step 1 — number of fragments
   ```
   22 ÷ 3 = 7 remainder 1
   So 7 full fragments of 3 bytes + 1 fragment of 1 byte = 8 fragments
   ```

   Step 2 — fragment numbering

   | Fragment | Bytes carried | Size | Offset | MF flag | Identification |
   |---|---|---|---|---|---|
   | 1 | 0 – 2 | 3 | `0` | 1 | 217 |
   | 2 | 3 – 5 | 3 | `3` | 1 | 217 |
   | 3 | 6 – 8 | 3 | `6` | 1 | 217 |
   | 4 | 9 – 11 | 3 | `9` | 1 | 217 |
   | 5 | 12 – 14 | 3 | `12` | 1 | 217 |
   | 6 | 15 – 17 | 3 | `15` | 1 | 217 |
   | 7 | 18 – 20 | 3 | `18` | 1 | 217 |
   | 8 | 21 | 1 | `21` | `0` | 217 |

   Step 3 — the three header fields explained
   - `Identification = 217` in every fragment, so the destination knows they all belong to the same original packet.
   - `Fragment offset` is the position of the fragment's first byte within the original packet, measured in elementary fragment units. Since the elementary fragment size is 1 byte here, the offset is simply the byte position: 0, 3, 6, 9, 12, 15, 18, 21.
   - `MF (More Fragments)` is 1 for fragments 1 to 7, telling the receiver that more are coming, and `0` for fragment 8, marking the end.

   Diagram
   ```
   Original packet 217, 22 bytes:
   | 0 1 2 | 3 4 5 | 6 7 8 | 9 10 11 | 12 13 14 | 15 16 17 | 18 19 20 | 21 |

   Fragment 1: ID=217 off=0  MF=1   data bytes 0-2
   Fragment 2: ID=217 off=3  MF=1   data bytes 3-5
   Fragment 3: ID=217 off=6  MF=1   data bytes 6-8
   Fragment 4: ID=217 off=9  MF=1   data bytes 9-11
   Fragment 5: ID=217 off=12 MF=1   data bytes 12-14
   Fragment 6: ID=217 off=15 MF=1   data bytes 15-17
   Fragment 7: ID=217 off=18 MF=1   data bytes 18-20
   Fragment 8: ID=217 off=21 MF=0   data byte  21      <- last
   ```

   Step 4 — reassembly at the destination
   - Fragments are collected by identification number, sorted by offset, and joined. The MF=0 fragment marks the end, and its offset plus its length gives the original size: 21 + 1 = 22 bytes. If any fragment fails to arrive before the reassembly timer expires, the whole packet is discarded.

   - Note on real IPv4: the offset field there counts in units of `8 bytes`, so every fragment except the last must carry a multiple of 8 bytes of data. This question deliberately sets the elementary fragment size to 1 byte to keep the arithmetic simple.

## Satellite Communication (4)

1. **(b) Difference between active and passive satellites.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 695 (ET: N/A)]*

2. **(c) Briefly describe different types of earth orbital satellite.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 695 (ET: N/A)]*

3. **Satellite ভিত্তিক যোগাযোগের একটি অসুবিধা লিখুন।** *[DMLC Assistant Teacher (ICT) 2021 compact it 825 (ET: N/A)]*

4. **How does mobile work? How many satellites are required to cover the earth?** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 1279-1280 (ET: N/A)]*

## Analog Modulation & Radio Receivers (3)

1. **With appropriate figures, distinguish between homodyne and heterodyne detection processes. Draw the block diagram of a super heterodyne AM receiver.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

2. **Difference between AM and FM. (a) Which is prefer for long distance communication? (b) Which has low distortion? (c) Which has low interference?** *[EGCB Assistant Engineer (CSE) 2022 compact it 716 (ET: BUET)]*

3. **A sinusoidal modulating waveform of amplitude 5V and frequency of 2 kHz is applied to FM generator, which has a frequency sensitivity of 40Hz/volt. Calculate the frequency deviation, modulation index and bandwidth.** *[BOF Assistant Programmer 2022 compact it 734 (ET: MIST)]*

## Spread Spectrum & Multiple Access (CDMA, FHSS, DSSS) (3)

1. **What are the limitaions of CDMA?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

2. **Mention the basic differences between frequency-hopped spread spectrum (FHSS) and direct sequence spread spectrum (DSSS) techniques.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

3. **What is CDMA? Briefly explain.** *[BREB Assistant Junior Engineer (IT) 2019 compact it 1122 (ET: BREB)]*

## Line Coding & Digital Encoding (2)

1. **Assume we want to transmit the following binary string: 01001110. Show the resulting signal on the one using the following line coding techniques: (i) NRZ-L (ii) Manchester NRZ (iii) Unipolar RZ (binary string: 11011000100)** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 638 (ET: N/A)]*

2. **What is Line coding? What is the different line coding techniques?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 869-870 (ET: N/A)]*

## Address Resolution (ARP & RARP) (2)

1. **(a) Discuss the main role of Address Resolution Protocol (ARP) in the network layer of TCP/IP protocol suite.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 490 (ET: N/A)]*

2. **What is ARP? Briefly explain ARP.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 841-842 (ET: N/A)]*

## VLANs & Subnetting Comparison (2)

1. A large organization wants to isolate different departments and user groups within the same physical network to improve security, reduce broadcast traffic, and manage network resources efficiently. The network administrator is considering either subnetting or VLANs to achieve this isolation. Compare subnetting and VLANs in this scenario and determine which technique is more appropriate for logical network isolation, explaining how the selected technique improves security and traffic management. [BSCCPL AME 21-08-2026 (BUET)]

2. **What is VLAN? Difference between static and dynamic VLAN.** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 550 (ET: BIBM)]*

## High Availability & Redundancy Protocols (VRRP, HSRP) (1)

1. **State the network protocol of VRRP?** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1359 (ET: BUET)]*
