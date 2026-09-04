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

2. **OSI মডেলের ৭টি স্তরের কাজ কি? এই সমগ্র স্তরগুলোর ভূমিকা কি?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

3. **What is the OSI model? Explain the functions of each layer with examples.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

4. **(b) Name the OSI layers and give one example of a cyber threat at any tree of those layers.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

5. **Write bottom to top OSI reference Model.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1449 (ET: N/A)]*

6. **In the TCP/IP model, how is data known in the different layers?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

7. **(b) Explain the TCP/IP protocol switch layers.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1444 (ET: N/A)]*

8. **(b) Draw the diagram of TCP/IP protocol suite and mention the name of protocols used in different layers of TCP/IP.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1352 (ET: N/A)]*

9. **How many Layers of OSI?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1450 (ET: N/A)]*

10. **রাউটার OSI এর কোন লেয়ারে থাকে?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1450 (ET: N/A)]*

11. **Write the name of OSI layers.** *[NSDA Assistant Maintenance Engineer 11.05.2024 compact it 384 (ET: N/A)]*

12. **Write the name of OSI layers protocol for every layers.** *[NSDA Assistant Maintenance Engineer 11.05.2024 compact it 384 (ET: N/A)]*

13. **Tabular representation of TCP/IP layer, functions of each layer, Associate protocols, device, and software in each layer. Different types of network firewalls. Explain NGFW compared to traditional firewall.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 301 (ET: BIBM)]*

14. **Explain TCP/IP model and its protocol and device.** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 404 (ET: N/A)]*

15. **Write down the OSI model.** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 404 (ET: N/A)]*

16. **How many TCP/IP layer? Write its Layer name?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

17. **Differentiate between OSI Model and TCP/IP Model. Draw the diagram of 4 Layers of TCP/IP Model including the main function of each layer and related protocols. List some basic functions performed at MAC layer.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 530 (ET: MIST)]*

18. **What is OSI Model? Write all layer name sequence should be top to bottom or bottom to top.** *[DESCO Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)]*

19. **Difference between OSI model and TCP/IP model. Relation between Data, Segment, Packet and Bit in OSI model.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 510 (ET: MIST)]*

20. **(a) List down the layers of OSI model in top-down manner.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 480 (ET: N/A)]*

21. **Fill up the following protocol table by work at which layer?** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 452 (ET: BUET)]*
| Protocol Name | Layer |
|---|---|
| Carrier-Sense Multiple Access (CSMA) |  |
| Open Shortest Path First (OSPF) |  |
| Transmission Control Protocol (TCP) |  |
| Routing Information Protocol (RIP) |  |
| User datagram protocol (UDP) |  |

22. **Which layer is used to link the network support layers and user support layers?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

23. **What is the number for the Network layer and the support layer?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

24. **(c) Write the all layers of OSI model.** *[BARC Programmer 04.08.2023 compact it 598 (ET: N/A)]*

25. **In order to prevent that the company decided to add end to end encryption techniques which layer of the OSI model is suitable to work in considering parameters like development time, software maintainability and development cost, Give reasons for your concepts.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 438 (ET: BIBM)]*

26. **What is TCP/IP model? Briefly explain TCP/IP model.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 837 (ET: N/A)], [EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)]*

27. **(a) What is OSI model? Explain how two computers can exchange information using the OSI model.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 694 (ET: N/A)]*

28. **TCP/IP model এর Layer গুলোর কাজ লিখুন।** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 698 (ET: DPI)]*

29. **What is OSI model? Write different layers of OSI model.** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 699 (ET: BUET)]*

30. **What is the difference between DOD and OSI model?** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 700 (ET: BUET)]*

31. **What is PDU?** *[BARC Data Entry Officer 10.09.2022 compact it 702 (ET: N/A)]*

32. **(খ) Computer network এর OSI 7-Layer গুলো উদাহরণসহ লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 767 (ET: N/A)]*

33. **Computer Network এ OSI Model এর Layer কয়টি?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

34. **OSI Model এর কাজ কী? এর লেয়ারসমূহ কী কী?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 811 (ET: IBA)]*

35. **Which layer data packet receive port from sender to destination? (a) Data link layer (b) Network layer (c) Transport layer (d) None** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

36. **What is OSI model? Write down the name of OSI model layer.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 837 (ET: N/A)]*

37. **What is OSI and TCP/IP model and briefly explain?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 870-872 (ET: N/A)]*

38. **TCP/IP protocol suite -এর বিভিন্ন স্তরের নাম লিখুন? HTTPs কী? এর ব্যবহারের প্রয়োজনীয়তা সংক্ষেপে বর্ণনা করুন?** *[41th BCS 2021 compact it 882 (ET: N/A)]*

39. **বর্তমানে Hybrid network model জনপ্রিয় একটি মডেল। এই মডেলের পাঁচটি Layer হচ্ছে, Application, Transport, Physical, Data link and Network Layer। এদের কাজ দেওয়া আছে বামপাশের কলামে, ডানপাশের কলামে কাজ অনুসারে Layer গুলোর নাম লিখুন।** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 975-976 (ET: BUET)]*

40. **Write down the functionality of OSI model.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1007-1008 (ET: DU)]*

41. **OSI Model এর Layer গুলো বর্ণনা করুন।** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019 (ET: N/A)]*

42. **(d) What do you mean by network protocol? Compare TCP/IP protocol suite and OSI reference model.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1028 (ET: N/A)]*

43. **TCP/IP মডেলের Layers সমূহের কাজ সংক্ষেপে লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1042-1043 (ET: DPI)]*

44. **(ক) OSI Model (Layer) এর সাতটি Layer কী কী? প্রথম দুটি সংক্ষেপে বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1097-1098 (ET: N/A)]*

45. **(খ) TCP/IP প্রোটোকল কী কাজ করে তা বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1098 (ET: N/A)]*

46. **Describe the OSI layers. Draw a diagram to show the hierarchy when the data is transmitted or received.** *[Combined Bank Senior Officer (IT/ICT) 2019 compact it 1114 (ET: DU)]*

47. **OSI model এর layer গুলোর নাম লিখ।** *[NPCBL Junior Technical Engineer 2019 compact it 1148 (ET: BUET)]*

48. **How many layers are used in OSI and TCP/IP model? Draw the layer.** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1152 (ET: KUET)]*

49. **Give answer of the following question:** *[Dutch Bangla Bank Assistant Network/Hardware Engineer 2019 compact it 1161 (ET: BUET)]*
   a) IP address converted into physical address \_\_\_\_\_\_\_\_?
   b) Name are converted into domain name \_\_\_\_\_\_\_\_?
   c) Mail is transferred between various devices using \_\_\_\_\_\_\_\_ protocol.
   d) Data link layer responsible for convert IP address into \_\_\_\_\_\_\_\_?
   e) HTTP service provides using which protocol \_\_\_\_\_\_\_\_?

50. **What is OSI model? Which layers are important for data transfer and user interaction?** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1189 (ET: N/A)]*

51. **Name OSI layer that transmitted bit stream to frames.** *[NWPGCL Assistant Engineer (CSE) 2018 compact it 1213-1214 (ET: N/A)]*

52. **Explain: ISO, OSI and TCP/IP model with figure.** *[ICT Ministry Assistant Programmer 2017 compact it 1241-1242 (ET: N/A)]*

## Networking Fundamentals & Terminology (32)

1. **Define Computer Network. Describe different types of Computer Networks.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

2. **(ক) IP address এবং MAC Address- এর মাঝে তুলনা করুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

3. **(ক) সংজ্ঞা লিখুন: (i) Propagation delay, (ii) Transmission delay.** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

4. **Write short note: Network, Protocol, link, gateway, Node.** *[BREB Assistant Programmer 18.02.2023 compact it 470 (ET: N/A)]*

5. **(b) Define following terms: (i) Bandwidth (ii) Latency (iii) MAC Address (iv) IP address** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 491 (ET: N/A)]*

6. **Define networking and Internetworking. What are the different types of network? Explain in details.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 672 (ET: N/A)]*

7. **Write short note: (i) web server (ii) ISP (iii) Router (iv) Search Engine** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 680 (ET: N/A)]*

8. **What is Interface protocol?** *[BARC Data Entry Officer 10.09.2022 compact it 703 (ET: N/A)]*

9. **(ক) সংজ্ঞা লিখুন: WWW, URL, HTTP, IP Address, Router.** *[Software Assistant Programmer 13.10.2022 compact it 708 (ET: N/A)]*

10. **What is computer network?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

11. **What is SDN?** *[IDRA Assistant Network Administrator 2022 compact it 727 (ET: N/A)]*

12. **How to works networks?** *[IDRA Assistant Network Administrator 2022 compact it 727 (ET: N/A)]*

13. **(খ) Address গুলির সংক্ষিপ্ত বর্ণনা দিন। (i) Port Number (ii) IP অ্যাড্রেস (iii) MAC অ্যাড্রেস।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 775 (ET: N/A)]*

14. **(i) নিচের MAC Address গুলো কোন ধরনের বের করুন। (a) 4C:23:10:4A:1A:2A (b) 45:24:56:2B:24:12 (c) FF:FF:FF:FF:FF:FF** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 788 (ET: N/A)]*

15. **If you have a company of two branch in the same city and they are connected. Which connection is used between then? (a) LAN (b) MAN (c) WAN (d) NONE** *[BCC Assistant Programmer 12.02.2021 compact it 811 (ET: BUET)]*

16. **Short Question: a) What are the protocol for connectionless and connection oriented? b) Why UTP cable are twisted? c) What are the main requirement of optical fiber splicing? d) Why use subnet mask? e) What the major difference between multicast and broadcast?** *[BPDB Assistant Engineer (CSE) 2021 compact it 816 (ET: BUET)]*

17. **Name of the Following figure:** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 880 (ET: BUET)]*
   Broadcast
   Unicast
   Multicast

18. **(i) Computer network কী? বিভিন্ন প্রকার Computer network সম্পর্কে আলোচনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 955-956 (ET: N/A)]*

19. **What is difference between MAC Address and IP Address?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1018-1019 (ET: N/A)]*

20. **(b) List the factors that affect the performance of a network.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1027 (ET: N/A)]*

21. **(a) Write a brief history of the internet. How to access to the internet?** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1028-1029 (ET: N/A)]*

22. **(b) Define computer network. Sate some merits and demerits of a computer network.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1029 (ET: N/A)]*

23. **b) Two IP address map to same Ethernet address. Will both of them receive packets?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033 (ET: BUET)]*

24. **Write short note: Node, Backbone, Router and Gateway.** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1049 (ET: BUET)]*

25. **(খ) Public and Private Network-এর মধ্যে পার্থক্য লিখুন? IP address কী?** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1073 (ET: N/A)]*

26. **What is MAC address?** *[BREB Assistant Hardware & Network Engineer 2019 compact it 1124 (ET: BREB)]*

27. **(a) To setup a network among the computers of your office which type of network and network features will you prefer? Justify your choice?** *[BPSC Assistant Programmer (ICT) 2019 compact it 1140-1141 (ET: N/A)]*

28. **(b) Suppose, your office needs to setup a network which can uses for internet purpose only? What will be your steps to setup that network in terms of:** *[BPSC Assistant Programmer (ICT) 2019 compact it 1144 (ET: N/A)]*

29. **What is an access network? Briefly describe the available access network.** *[BTRC Assistant Director (Technical) 2019 compact it 1147 (ET: N/A)]*

30. **Explain the terms Domains, Bandwidth, Broadcast and Multicast.** *[Multiple Ministry Assistant Programmer 2017 compact it 1232 (ET: N/A)]*

31. **Differentiate between Intranet and Extranet.** *[Bangladesh Bank Assistant Maintenance Engineer 2016 compact it 1264 (ET: N/A)]*

32. **a) Briefly discuss what a computer network means.** *[Ministry of Finance Programmer 2013 compact it 1272 (ET: N/A)]*

## Application Layer Protocols & Troubleshooting (DNS, DHCP, HTTPS) (22)

1. [http://BSCPL.bd.gov](http://BSCPL.bd.gov) is connected to multiple international ISPs, and users can successfully access other websites, but they are unable to access the [http://BSCPL.bd.gov](http://BSCPL.bd.gov) website. The network uses essential services such as DNS, DHCP, and HTTPS, each performing different functions in the communication process. Identify the roles of DNS, DHCP, and HTTPS, determine which component or configuration could be responsible for this site-specific failure, and explain the possible causes and troubleshooting steps. [BSCCPL AME 21-08-2026 (BUET)]

2. **Write down the DNS function.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1449 (ET: N/A)]*

3. **Why does the Domain Name System (DNS) primarily use UDP as its transport layer protocol instead of TCP? Describe the sequence of events that take place during the DNS name resolution process when a user enters www.companybd.com into a web browser and presses Enter.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1421 (ET: E-Zone)]*

4. **What is DHCP?** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*

5. **Which protocol is used by the ping tools?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

6. **Which server can be used to dinamically assign IP address to the PCs is a LAN?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*

7. **Explain how do DHCP work?** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 565 (ET: N/A)], [BREB Assistant Programmer (AP) 21.02.2025 compact it 1335 (ET: N/A)]*

8. **SMTP, DNS, DHCP, NAT এর কাজ কি লিখ?** *[BTCL Junior Assistant Manager 2022 compact it 639 (ET: BUET)]*

9. **What is DNS? What is forward and reverse lookup DNS?** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 658 (ET: N/A)]*

10. **What is ICMP, SMTP, POP server, Boot loader and Clustering?** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 659 (ET: N/A)]*

11. **Write a command how to find DNS www.egcb.gov.bd and which protocol uses?** *[EGCB Assistant Engineer (CSE) 2022 compact it 716 (ET: BUET)]*

12. **For the following description of various IP networking protocols write down the protocol name and its full form in the following table:** *[BTCL Assistant Manager (Technical) 2021 compact it 764 (ET: BUET)]*

13. **(a) How does a browser retrieve IP address from URL?** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 794 (ET: N/A)]*

14. **(d) What is DNS? “TCP/IP is used in DNS”- justify the statement.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 795 (ET: N/A)]*

15. **(b) How is Hierarchical DNS resolution done in Domain Naming System? Give an example resolution for xyz.uv.gov.bd domain name.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 802 (ET: N/A)]*

16. **What is Web cashing? Why we use web cashing?** *[Sonali Bank Ltd. Officer IT 2021 compact it 908 (ET: N/A)]*

17. **What is DNS Resolver?** *[Sonali Bank Ltd. Officer IT 2021 compact it 908-909 (ET: N/A)]*

18. **DNS server এবং DHCP server এর কাজ কী?** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 911 (ET: BUET)]*

19. **দূরবর্তী কম্পিউটার সংযোগ এর জন্য কোন প্রোটোকল ব্যবহার করা হয়?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 944 (ET: N/A)]*

20. **(a) Differentiate between DNS server and caches.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1142 (ET: N/A)]*

21. **What is the difference between DNS server and caches? What is the importance of DNS cache in World Wide Web?** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1189 (ET: N/A)]*

22. **Write short notes on DHCP and SMTP.** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1227 (ET: N/A)]*

## Wireless Networks & IoT (mmWave) (19)

1. **Describe Wi-Fi, Bluetooth, and WiMAX.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

2. **What is the use of mmWave in IoT?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1454 (ET: BUET)]*

3. **What is IoT? Brefly explain.** *[Mongla Port Authority Assistant Programmer 2023 compact it 571 (ET: N/A)]*

4. **How to work WiMax technology?** *[Mongla Port Authority Assistant Programmer 2023 compact it 571 (ET: N/A)]*

5. **Briefly describe the basis structure at a mobile cellular system with a proper figure.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 676 (ET: N/A)]*

6. **How can you define IoT? What are the basic components of IoT?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 680 (ET: N/A)]*

7. **(a) Write down the features of 4G wireless networks.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 695 (ET: N/A)]*

8. **5G প্রথম কত সালে ও কোথায় চালু হয়?** *[BWMRI Assistant Maintenance Engineer 2022 compact it 736 (ET: N/A)]*

9. **(ক) Wi-Fi Network সম্পর্কে সংক্ষিপ্ত বিবরণ দিন। Wi-Fi Sensor Network এবং Ad Hoc Network এর মধ্যে পার্থক্য লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 769 (ET: N/A)]*

10. **Call Drop কী? এর কারণ গুলো উল্লেখ করুন।** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 810 (ET: IBA)]*

11. **LTE কী? এর এডভান্সড প্রযুক্তির নাম লিখুন।** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 811 (ET: IBA)]*

12. **Wi-Fi, Bluetooth, Wi-Max, Cellure network এইগুলোকে দূরত্বের ক্রমানুসারে ছোট থেকে বড় এর দিক অনুসারে লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 867 (ET: BUET)]*

13. **(c) Difference between broadband Wi-Fi and Wi-Max communication technology.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 896 (ET: N/A)]*

14. **What is wireless network system? Why CSMA/CA used instead of CSMA/CD?** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922-923 (ET: N/A)]*

15. **Write about 5G disadvantages: (a) Increased High Costs (b) Draining Battery of devices. (c) Increased infrastructure development cost** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 928 (ET: CTI)]*

16. **Make a list of LTE Network elements.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 988 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

17. **Explain Bluetooth, Wi-Fi and Cellular Network.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1023 (ET: N/A)]*

18. **(b) How cellular networks handoff works?** *[BPSC Assistant Programmer (ICT) 2019 compact it 1142 (ET: N/A)]*

19. **Write the basic function of GGSN and SGSN. Describe LTE radio technology.** *[BTRC Assistant Director (Technical) 2019 compact it 1145 (ET: N/A)]*

## Networking Devices (19)

1. Describe the functions of a Switch and a Router and explain two key differences between these networking devices. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

2. **Briefly describe the following network devices: Repeater, Hub, Bridge, Switch and Router.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 325 (ET: BIBM)]*

3. **How many collision domians are created when you segment a network with a 12-port switch?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

4. **Difference among Switch, Bridge and Router.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 524 (ET: MIST)]*

5. **Differentiate between Collision Domain and Broadcast Domain in computer network. What is the function of DNS and DHCP?** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 535 (ET: MIST)]*

6. **Write down the difference between gateway and firewall.** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 476 (ET: N/A)]*

7. **What is gateway? Is router and gateway have any difference?** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*

8. **অথবা, (ক) ডেটা ট্রান্সমিশনে Router ও Gateway এর মধ্যে কোনটি অধিকতর সুবিধাজনক-মতামত ব্যক্ত করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 615 (ET: N/A)]*

9. **Write the Difference among Network Switch, Hub and Router.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1023 (ET: N/A)], [DESCO Sub-Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)], [BMA Signal Assistant Engineer (Computer) 2021 compact it 933 (ET: BUET)]*

10. **(iii) Router and Gateway এর ফাংশন লিখুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 789 (ET: N/A)]*

11. **Write down the difference between Hub and Switch.** *[DMLC Assistant Teacher (ICT) 2021 compact it 825 (ET: N/A)]*

12. **Wi-Fi access point বলতে কী বুঝানো হয়? Router and Switch -এর মধ্যে পার্থক্য লিখুন।** *[41th BCS 2021 compact it 883 (ET: N/A)]*

13. **হাব, সুইচ ও রাউটার এর মধ্যে পার্থক্য লিখ।** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 947 (ET: BUET)]*

14. **(c) Briefly describe three devices using which different LANs can be connected.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1030 (ET: N/A)]*

15. **(ক) Hub এবং Switch কী? কোনটির ব্যবহার সুবিধাজনক সপক্ষে যুক্তি দিন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1098 (ET: N/A)]*

16. **Difference among HUB, Switch and Router.** *[DESCO Assistant Engineer (CSE) 2019 compact it 1119 (ET: BUET)]*

17. **(a) What are the difference among Hub, Switch and Routers?** *[BPSC Assistant Programmer (ICT) 2019 compact it 1144 (ET: N/A)]*

18. **Difference between Router and Switch.** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1151 (ET: KUET)]*

19. **Describe about Hub, Switch and Router.** *[BPDB Assistant Engineer (CSE) 2018 compact it 1214 (ET: N/A)]*

## Multiplexing & Bandwidth (18)

1. Five channels, each with a 100-kHz bandwidth, are to be multiplexed together. What is the minimum bandwidth of the link if there is a need for a guard band of 10 kHz between the channels to prevent interference? [SO IT 25-07-2026]

2. **ব্যান্ডউইথ (Bandwidth) বলতে কী বুঝায়?** *[সাধারণ জ্ঞান: বিজ্ঞান ও প্রযুক্তি, বিষয় কোড: ১০৪, মান: ৪০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

3. **6.9 Five channels, each with a 100-kHz bandwidth, are to be multiplexed together. What is the minimum bandwidth of the link if there is a need for a guard band of 10 kHz between the channels to prevent interference?** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

4. **Differentiate among TDM, FDM and WDM. How does working process in TDM?** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 511 (ET: MIST)]*

5. **Describe the different types of Multiplexing.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 554 (ET: BIBM)]*

6. **What technique allows simultaneous transmission of multiple signals across a single data link?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

7. **(খ) FDM এবং TDM এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 615 (ET: N/A)]*

8. **Show that the data rate of T-1 carrier is 1.544 Mbps.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

9. **Suppose you are appointed as an Assistant Engineer in a Government organization. The number of telephone connections required for the organization is 1000. The per year increment of telephone connection is 100. Considering the life time of telephone equipment is to be 15 years, design a T-carrier based TDM system for the organization.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

10. **Compare between TDM and TDMA techniques.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 676 (ET: N/A)]*

11. **Assume a TDMA based communication system having 8 transmission receiver pairs. Each source is sampled at 8KHz. That generates 16bits per sample if two synchronization bits are added to each frame calculate the data rate of TDMA line.** *[BDCCL Assistant Engineer (Network) 2022 compact it 742 (ET: N/A)], [Water Supply and Sewerage Authority (WASA); Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)], [BTCL Assistant Manager (Technical) 2021 compact it 765 (ET: BUET)]*

12. **Two channels, one with a bit rate of 190kbps and another with a bit rate 180 kbps are to be multiplexed using pulse stuffing TDM with no synchronization bits. Answer the following questions: (a) What is the size of a frame in bits? (b) What is the frame rate? (c) What is the duration of a frame? (d) What is the date rate?** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)]*

13. **What is Multiplexing? Write about Time division Multiplexing.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 870 (ET: N/A)]*

14. **(a) Distinguish between Frequency Division Multiplexing (FDM) and Time Division Multiplexing (TDM).** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 888 (ET: N/A)]*

15. **TDM math: rate= 1.536 Mbps, message size= 960000, Slot=32, end to end circuit Switch time=800ms, calculate transfer time.** *[Sonali Bank Ltd. Officer IT 2021 compact it 910 (ET: N/A)]*

16. **A want to send 2 files the size of each file is 500000 bit's data to B through TDM channel which has slot 16 channel bit rate 1.5 Mbps and 30 millisecond delay time, if no propagation delay; find out time to send the data.** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 925 (ET: CTI)]*

17. **We have four sources, each creating 250 characters per second. If the interleaved unit is a character and 1 synchronizing bit is added to each frame. Now find- (a) the data rate of each source. (b) the duration of each character in each source.** *[BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)]*

18. **Figure shows synchronous TOM with a data stream for each input and one data stream for the output. The unit of data is 1bit. Find (a) the input bit duration (b) the output bit duration (c) the output bit rate and (d) the output frame rate.** *[Janata Bank Ltd SO ( Assistant Network Engineer) 2020 compact it 1009 (ET: N/A)]*

## Routing Protocols & Route Configuration (18)

1. A BGP router receives multiple routes to the same destination network from different neighboring autonomous systems. The available routes are given in the following table, containing Path, LOCAL_PREF, AS_PATH, ORIGIN, and MED values. Using the standard BGP best-path selection rules, analyze the attributes in the given order and determine which path will be selected as the best route, showing the comparison and justification for each step. [BSCCPL AME 21-08-2026 (BUET)]

| Path | LOCAL_PREF | AS_PATH | ORIGIN | MED |
|---|---|---|---|---|
| Path 1 | 200 | 65001 65010 | IGP | 50 |
| Path 2 | 150 | 65020 | IGP | 5 |
| Path 3 | 200 | 65030 65040 | IGP | 10 |
| Path 4 | 200 | 65050 65060 | IGP | 20 |

2. **Static route Configuration: Configure R0 to reach PC1 you can assume any Vendor, Cisco, Huawei, juniper** *[Islami Bank PLC Senior Officer (Network/System) 14.03.2025 compact it 1331 (ET: BUET)]*

3. **What is OSPF? Briefly Explain.** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1358 (ET: BUET)]*

4. **Which of the following is a pair of routing protocol?** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*
   * **(A) TCP and IP**
   * **(B) HTTP and FTP**
   * **(C) RIP and OSPF**
   * **(D) ARP and RARP**

5. **BGP is __________ protocol.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

6. **BGP stands for __________?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

7. **Which routing protocol use Dijkstra Algorithm?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

8. **What is Routing? Explain different types of Routing? Why using benefit of an Adhoce routing? Which routing algorithm is used in shortest path algorithm?** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 525 (ET: MIST)]*

9. **(b) Distinguish between routing and forwarding. What are the advantages of net specific routing over host specific routing?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 490 (ET: N/A)]*

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

11. **Define distance Vector and Link state routing protocols.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 635 (ET: N/A)]*

12. **What are static and dynamic routing? Given their relative advantages.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 635 (ET: N/A)]*

13. **What is Routing? Write down the difference between static routing and dynamic routing.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 837-838 (ET: N/A)]*

14. **Name of the Algorithm RIP, OSPF and EIGRP routing protocol.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 838 (ET: N/A)]*

15. **What is Autonomous system? What is the difference between Link state routing protocol and Distance vector routing protocol?** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 838-839 (ET: N/A)]*

16. **Cost calculation of EIGRP formula.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 839 (ET: N/A)]*

17. **Given a totology of distance vector routing. Find the table of each node for the 1^{\text{st}} route.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 859-860 (ET: N/A)]*

18. **What is difference between link state routing and distance vector routing?** *[Sonali Bank Ltd. Officer IT 2021 compact it 909 (ET: N/A)]*

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

2. **(b) Distinguish between TCP and UDP protocols.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 886 (ET: N/A)], [Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)], [BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 694 (ET: N/A)]*

3. **Show the pictorial representation of TCP 3-way handshaking protocol for establishing a connection between a server and a client.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1339 (ET: N/A)]*

4. **What is the deference between TCP and UDP?** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*

5. **3-way handshake protocol for TCP connection using diagram.** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 403 (ET: N/A)], [BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 876-877 (ET: BUET)]*

6. **Write a TCP/UDP used service name?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

7. **Difference between TCP and UDP. Distinguish between Cat5 and Cat6. Difference among exFAT, FAT32 and NTFS.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 523 (ET: MIST)]*

8. **Show a 3-way handshake protocol in TCP connection established using a diagram.** *[BICIC Assistant Programmer 2022 compact it 630 (ET: BUET)]*

9. **Differecne between TCP and UDP.** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 658 (ET: N/A)]*

10. **What is UDP protocol? UDP is reliable or not? Explain why or why not?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 754 (ET: N/A)]*

11. **The primary function of the Transmission Control Protocol (TCP). TCP performs six basic functions. What are the basic function performing by TCP?** *[BTRC Assistant Director (Technical) 2021 compact it 807-808 (ET: IBA)]*

12. **(c) What is purpose of routers? How congestion control works in the TCP?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 886-887 (ET: N/A)]*

13. **What is a TCP Three-way handshaking step?** *[Sonali Bank Ltd. Officer IT 2021 compact it 909 (ET: N/A)]*

14. **The primary function of the Transmission Control Protocol (TCP) is to turn an unreliable network into a reliable network that is free from lost and duplicate packets. What are the functions performed by TCP to make a network more reliable?** *[Sonali & Janata Bank Officer (IT) 2020 compact it 990 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

15. **a) A live video stream will be transmitted. Which Transport layer protocol will you use and why?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033 (ET: BUET)]*

16. **(c) What is TCP protocol? How does it work?** *[BPSC Assistant Programmer (CSE) 2019 compact it 1125-1127 (ET: N/A)]*

17. **Write down difference between TCP and UDP with write down some TCP and UDP protocols.** *[Dutch Bangla Bank Assistant Network/Hardware Engineer 2019 compact it 1160 (ET: BUET)]*

## Communication System & Transmission Modes (17)

1. What is a communication system? Describe the different types of transmission modes with examples. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

2. **How many types of modes are used in data transferring through networks? Briefly explain those modes. Differentiate between TCP vs UDP.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 338 (ET: BIBM)]*

3. **(b) Name and define five components of Data communication system with necessary diagram.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 487 (ET: N/A)]*

4. **(a) Differentiate between half-duplex and full duplex transmission.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 489 (ET: N/A)]*

5. **(গ) উদাহরণসহ Simplex, half-duplex এবং duplex কমিউনিকেশন সিস্টেমের পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 628 (ET: N/A)]*

6. **What is the difference between Synchronous and Asynchronous transmission?** *[CAAB Assistant Maintenance Engineer (AME) 2022 compact it 723 (ET: N/A)], [RAKUB Assistant Network System Engineer 03.11.2023 compact it 550 (ET: BIBM)]*

7. **Briefly mention the main रणनीति impairments in telecommunication channel. Considering these impairments explain which communication is better between analog and digital communication systems?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*

8. **Describe the data communication system with necessary diagram.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 679 (ET: N/A)]*

9. **Write down the Data Communication elements.** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*

10. **(ক) Data Communication System এর পাঁচটি প্রধান Component এর চিত্রসহকারে বর্ণনা দিন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 704 (ET: N/A)]*

11. **(খ) Data Communication কত প্রকার? উদাহরণসহ সংক্ষিপ্ত বর্ণনা দিন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 704 (ET: N/A)]*

12. **Define full duplex with an example.** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

13. **Which communication mode use serial communication? (a) Duplex (b) Half Duplex (c) Simplex (d) All** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

14. **(c) Illustrate a communication model in simplified form.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1027-1028 (ET: N/A)]*

15. **(a) Draw a general model of communication system. Discuss different modes of communications.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1141-1142 (ET: N/A)]*

16. **Write down the problem of asynchronous data transmission? How to solve this Problem using synchronous data transmission?** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1152 (ET: KUET)]*

17. **What is data communication? Define Simplex, half duplex and full duplex.** *[ICT Ministry Assistant Programmer 2017 compact it 1239 (ET: N/A)]*

## Data Rate & Channel Capacity (Nyquist, Shannon) (16)

1. **Nyquist math: See in Data Communication & Networking Chapter** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 499 (ET: N/A)]*

2. **Suppose that a digitized TV picture is to be transmitted from a source that uses a matrix of 480 × 500 picture elements (pixels), where each pixel can take on one of 32 intensity values. Assume that 30 pictures are sent per second. (This digital source is roughly equivalent to broadcast TV standards that have been adopted). Find the source rate R (bps).** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 (ET: BIBM)]*

3. **One of the drawbacks of a small packet size is that a large function of link bandwidth is consumed by overhead bytes. To this end, supposed that the packet consists of P bytes and 5 bytes of header. Consider sending a digitally encoded voice source directly. Suppose the source is encoded a constant rate of 128 kbps. Assume each packet is entirely filled before the source sends the packet into the network. The time required to fill a packet is the packetization delay. Determine the packetization delay for length L-1500 bytes (roughly corresponding to maximum-sized Ethernet packet).** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 (ET: BIBM)]*

4. **(ক) Bandwidth এবং Through put এর মধ্যে পার্থক্য কী?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 628 (ET: N/A)]*

5. **The power of signal is 10\text{mW} and the power of the noise is 1\mu\text{W}; What are the values of \text{SNR} and \text{SNR}_{\text{dB}}?** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 651 (ET: BUET)]*

6. **We need to send 265\text{ kbps} over a noiseless channel with a bandwidth of 20\text{kHz}. How many signal levels do we need?** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 652 (ET: BUET)]*

7. **A telephone line normally has a bandwidth of 3000\text{ Hz} (300\text{ to } 3300\text{ Hz}) assigned foe data communications. The signal-to-noise ratio is usually 3162. Calculate the capacity for this channel?** *[RPGCL Assistant Manager (ICT) 2022 compact it 656 (ET: BUET)]*

8. **Consider that a signal is transmitted over a channel of bandwidth 200kHz and the total path loss in the channel is found to be 60dB. The noise power per hertz at the receiver is- 100 dBm. Determine the required transmit power to achieve data rate of 40kb/s.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

9. **(গ) নিম্নে উল্লিখিত ডাটা ট্রান্সফার রেট গুলিকে bit/sec এর পরিণত করুন 50Mb/S; 10KB/S; 20MB/S; 10Kb/S.** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 704 (ET: N/A)]*

10. **What is the channel capacity for a teleprinter channel with a 300 Hz bandwidth and a signal-to-noise ratio of 3 dB?** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 719 (ET: N/A)]*

11. **Using the Nyquist theorem, we can sample 12 million times/sec. Four–level signals provide 2 bits per sample, for a total data rate of 24 Mbps.** *[NESCO Assistant Manager (ICT) 2021 compact it 908 (ET: BUET)]*

12. **In serial communication employing 8 data bits, a parity bit and 2 stop bits. What is the minimum band rate requested to sustain a transfer rate of 300 characters per second?** *[BAUST Assistant Programmer 2021 compact it 918 (ET: N/A)]*

13. **Find signal bit per second bound rate 1000 and 16-QAM signal.** *[BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)]*

14. **Channel capacity related math. (প্রশ্ন সংগ্রহ করা সম্ভব হয়নি)** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1038 (ET: BUET)]*

15. **a) Determine the Nyquist sampling rate and the Nyquist sampling interval for the signal $X(t) = \sin(2100\pi t)$** *[38th BCS 2018 compact it 1177 (ET: N/A)]*

16. **Consider a noiseless channel with a bandwidth of 3 KHz transmitting a signal with two signal levels. What is the maximum bit rate?** *[Multiple Ministry Assistant Programmer 2017 compact it 1232 (ET: N/A)]*

## Physical Layer & Transmission Media (Cables & Wiring) (15)

1. **Straight through connection vs Crossover connection.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1448 (ET: N/A)]*

2. **Which transmission medium is used in LAN? Write their maximum length and capacity (bps).** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1452 (ET: N/A)]*

3. **IEEE __________ Standard used Ethernet LAN?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

4. **What is the connector name copper cable in LAN?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*

5. **What are the different types of transmission media used for data communication? Explain their advantages and disadvantages.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 326 (ET: BIBM)]*

6. **Difference between Guided and Unguided media. Difference between STP and UTP. Why using benefit UTP instead of STP?** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 523 (ET: MIST)]*

7. **What is the main benefit of broadband transmission system compared to baseband? What is the attenuation of transmission media? Distinguish between twisted pair, co-axial cable and fiber optics in tabular form.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 530 (ET: MIST)]*

8. **Why we used straight-through and cross cable with example?** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 595 (ET: N/A)]*

9. **(খ) Fiber optic cable, Twisted pair cable এবং Co-axial cable এর সুবিধাগুলো বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 629 (ET: N/A)]*

10. **What happens when you use cables longer than the prescribed length in a network?** *[BOF Assistant Programmer 2022 compact it 732 (ET: MIST)]*

11. **(ii) ব্যাখ্যা করুন: (a) 10Base5 (b) 10BaseF** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 789 (ET: N/A)]*

12. **Explain 10baseT.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 839 (ET: N/A)]*

13. **Which media transfer data with higher bandwidth? Advantages of this media.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 843 (ET: N/A)]*

14. **(a) What are the problems that transmission lines suffer from? Briefly describe any one of them.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1026-1027 (ET: N/A)]*

15. **Explain 10Base2, 10Base5, 10BaseT and Ethernet.** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 1276-1277 (ET: N/A)]*

## Error Detection & Data Communication (CRC, Throughput) (14)

1. (a) CMY color model এর উপাদানগুলো লিখুন (CMY color model এর কাজ কী?)
   (b) CRC এর কাজ কী? (IIB CRC-16 এর ক্ষেত্র এবং প্রশ্নগুলো আলোচনা করুন)
   (c) Data communication এর ক্ষেত্রে bandwidth এবং throughput এর মধ্যে পার্থক্য লিখুন। *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

2. **Data communication mathematical problems.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1368 (ET: BUET)]*

3. **Question on data communication transmission and signal related math.** *[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1441 (ET: BUET)]*

4. **10Mbps bandwidth, average packet length 1500 bytes what is maximum packet arrival rate support without causing congestion.** *[Bangladesh Satellite Company Limited Assistant Engineer (CSE) 23.08.2025 compact it 1430 (ET: BUET)]*

5. **What is Total Latency for a 3-kbyte message (an e-mail) if the bandwidth of the network is 1Gbps? Assume that the distance between the sender and the receiver is 300\text{ km} and that light travels at 2 \times 10^8\text{ m/s}. Round Trip Time 50ms Queuing Time 5ms?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1320 (ET: DU)]*

6. **Differentiate the following terms in tabular form:** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 300 (ET: BIBM)]*
   * **A. CSMA/CD and CSMA/CA.**
   * **B. Optical Communication and Satellite Communication.**
   * **C. Parity bit check, CRC and Checksum.**

7. **Two math from data communication.** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 405 (ET: N/A)]*

8. **(গ) Data communication-এর সাপেক্ষে bandwidth এবং troughput এর সংজ্ঞা লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

9. **CRC is a redundancy error technique used to determine the error. Suppose the original data is 11100 and divisor is 1001.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 493 (ET: N/A)]*

10. **A telephone line normally has a bandwidth of 3000 Hz (300 to 3300 Hz) assigned for data communication. The SNR is usually 3162. What will be the capacity for this channel?** *[Combined Bank Assistant Programmer 09.06.2023 compact it 497 (ET: N/A)]*

11. **Which technique is used for binary division check in network?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

12. **Explain parity method for error detection. Write down the bit strings of “Delta” using ASCII.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 (ET: BIBM)]*

13. **An end system sends 50 packets per second using the User Datagram Protocol (UDP) over a full duplex 100 Mbps ethernet LAN connection. Each packet consists 1500B of ethernet frame payload data. What is the throughput, when measured at the UDP layer?** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 718 (ET: N/A)]*

14. **The message 11001001 is to be transmitted using the CRC polynomial x^3+1 to protect it from the errors. Now find out the message that should be transmitted.** *[BAUST Assistant Programmer 2021 compact it 917-918 (ET: N/A)]*

## Network Topologies (14)

1. **What is Star vs Mesh Topology?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1449 (ET: N/A)]*

2. **(b) Define network topology and classify it.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1446 (ET: N/A)]*

3. **Write 4 topology name?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

4. **What is Network Topology? Distinguish between Bus, Ring, Tree and Star topology. Discuss how the Bus topology works.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 530 (ET: MIST)]*

5. **What is Personal Area Network? What is needed component and explain?** *[Mongla Port Authority Assistant Programmer 2023 compact it 572 (ET: N/A)]*

6. **What is Topology in data communication? What are differences between Bus, Ring, Tree and Star topology? Purpose of IEEE 802.11 committee.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 512 (ET: MIST)]*

7. **(খ) একটি নেটওয়ার্কে n সংখ্যক ডিভাইসের জন্যে Bus, Mesh এবং Star টপোলজিতে তারের লিংকগুলোর সংখ্যা কত?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 628 (ET: N/A)]*

8. **What is network topology? Write the name all different topology used in computer networking with example, diagram and their activities.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 673 (ET: N/A)]*

9. **Write down the types of topology.** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*

10. **Write down the Disadvantages of Bus topology.** *[DMLC Assistant Teacher (ICT) 2021 compact it 825 (ET: N/A)]*

11. **(b) Define network topologies with features.** *[National University Assistant Programmer 2020 compact it 977 (ET: DU)]*

12. **(d) List some various types of Topologies. What are the factors to choose a topology?** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1030 (ET: N/A)]*

13. **(খ) Bus and Ring টপোলজির মধ্যে কোনটি ভালো এবং কেন?** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1067 (ET: N/A)]*

14. **Draw Different type of Network topologies and mention their features.** *[Sonali & Janata Bank Senior Officer (IT/ICT) 2018 compact it 1166 (ET: N/A)]*

## IPv6 Addressing (13)

1. 4B:30:10:21:2A:1B, 4C:20:1B:2E:08:E7 Identify which of the given IPv6 addresses represent Unicast and Multicast communication, and determine whether any of them represents a Broadcast address. Explain your answer based on the IPv6 addressing rules. [BSCCPL AME 21-08-2026 (BUET)]

2. A host is connected to an IPv6 network and needs to configure its own IPv6 address automatically using Stateless Address Autoconfiguration (SLAAC). Arrange the steps in the correct order and explain the purpose of each step. [BSCCPL AME 21-08-2026 (BUET)]

3. **(a) What are the differences between IPv4 and IPv6, and why is IPv6 considered more secure?** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

4. **How many bits in IPv4 and IPv6 address? Why NAT is not required in IPv6?** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 398 (ET: BUET)]*

5. **(ক) IP Address কী? IPv4 এবং IPv6 এর মধ্যে চারটি প্রধান পার্থক্য লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 415 (ET: N/A)]*

6. **(a) Differentiate between IPV4 and IPV6.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 896 (ET: N/A)], [BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)], [WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 501 (ET: N/A)], [BMA Signal Assistant Engineer (Computer) 2021 compact it 932 (ET: BUET)]*

7. **IPv4 and IPv6 how many bits and Why is NAT not needed in IPv6?** *[RPGCL Assistant Manager (ICT) 2022 compact it 652 (ET: BUET)]*

8. **IPv6 address কত বিটের?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

9. **What is the difference between stateful DHCPv6 and stateless DHCPv6?** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 840-841 (ET: N/A)]*

10. **What is DHCPv6?** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 841 (ET: N/A)]*

11. **Explain IPv6 link local address and multicast address.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 843 (ET: N/A)]*

12. **Write down the difference between IPv4 and IPv6.** *[BREB Assistant Junior Engineer (IT) 2019 compact it 1122-1123 (ET: BREB)]*

13. **How many bits for IPv6? Write an example IPv6?** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1150 (ET: KUET)]*

## Physical Layer & Optical Fiber (Attenuation & Power Budget) (13)

1. **A fiber optic network is designed using single-mode fiber with an attenuation of 0.35 dB/km. The network includes a splitter with a 14 dB loss as specified in the datasheet. Additionally, there are two mechanical splices (each with 0.1 dB loss) and two connectors (each with 0.75 dB loss). Given the following parameters:**
   * **Transmitter Power: 5 dBm**
   * **Receiver Sensitivity: -14 dBm**
   * **Fiber Attenuation: 0.35 dB/km**
   **Calculate the maximum fiber length (D) that can be used between the OLT (Optical Line Terminal) and ONU (Optical Network Unit) while maintaining an acceptable signal level.** *[Islami Bank PLC Senior Officer (Network/System) 14.03.2025 compact it 1332 (ET: BUET)]*

2. **(a) Why fiber optic cable is used in submarine instead of satellite?** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 431 (ET: BUET)]*

3. **(b) Why the submarine cable is damaged under water?** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 432 (ET: BUET)]*

4. **(ক) ফাইবার অপটিক ক্যাবলের গঠন ও বৈশিষ্ট্য ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 614 (ET: N/A)]*

5. **Write down the Working principle of Optical Fibre.** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 649 (ET: BUET)]*

6. **Define the attenuation and dispersion in an optical fiber. Draw the block diagram of a long-haul optical fiber communication system.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

7. **Define the principle of data transmission through the fiber optic cable.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*

8. **How can you do fix the signal attenuation problems?** *[BOF Assistant Programmer 2022 compact it 734 (ET: MIST)]*

9. **Where are the low loss transmission windows of silicon based optical fiber and Which window is the most popular in communication and wave. Draw diagram of a long haul WDM Transmission system.** *[BTCL Assistant Manager (Technical) 2021 compact it 765 (ET: BUET)]*

10. **A 1550nm fiber optic transmission Link if of 50km length without repeating with a signal mode fiber having loss of 0.2dB/km. The fiber is joined ever 2km with conductor each with 0.5dB loss. Determine the minimum average power which should be lunched in to the fiver in order to Tarantion an average optical power level of 10 micro-watts at the receiver.** *[BTCL Assistant Manager (Technical) 2021 compact it 766 (ET: BUET)]*

11. **কোন মাধ্যমে আলোর Pulse ব্যবহৃত হয়?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

12. **What is 3dB?** *[BTRC Assistant Director (Technical) 2019 compact it 1145-1146 (ET: N/A)]*

13. **From single mode fiber and multimode fiber which one is suitable for LAN?** *[NWPGCL Assistant Engineer (CSE) 2019 compact it 1153 (ET: RUET)]*

## Network Address Translation (NAT) (13)

1. Network Address Translation (NAT) maps internal networks to the public internet.
   * (a) Explain the historical IP addressing limitation that made NAT a necessity globally.
   * (b) Explain the step-by-step logical translation process that occurs at a branch router when an internal employee (IP 192.168.1.5) sends a web request to an external server, and how the router correctly handles the returning response packet. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

2. **Connection between Public IP to Private IP is called __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

3. **What is NAT? Explain with topological diagram.** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 589 (ET: BUET)]*

4. **Explain NAT? Differenc between IPv4 and IPv6.** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 549 (ET: BIBM)]*

5. **What is NAT? Write down the list of private IP address.** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 717 (ET: N/A)]*

6. **Briefly explain Network Address Translation (NAT).** *[IDRA Assistant Network Administrator 2022 compact it 727 (ET: N/A)]*

7. **(i) Network Address Translation (NAT) ছবি সহ ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 787 (ET: N/A)]*

8. **(b) What is NAT? Mention its advantages.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 794 (ET: N/A)]*

9. **(a) Why do we need NAT? What are its advantages? Draw a topology diagram to explain NAT.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 799 (ET: N/A)]*

10. **Why do we need NAT? Draw a topology diagram to explain NAT.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 841 (ET: N/A)]*

11. **What is PAT? How does a network PAT work?** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 841 (ET: N/A)]*

12. **What is NAT?** *[BREB Assistant Hardware & Network Engineer 2019 compact it 1124 (ET: BREB)]*

13. **Show the translation process of a NAT Box.** *[Agrani Bank Ltd. Officer (ICT) 2017 compact it 1224 (ET: N/A)]*

## Flow Control & Data Link Layer (Stop-and-Wait) (12)

1. A single-mode optical fiber communication link connects two locations 250\text{ km} apart using WDM technology with 50 channels, where each channel provides a bit rate of 10\text{ Gbps}. The refractive index of the fiber is 1.5, and data is transmitted using the Stop-and-Wait protocol. A 1\text{ GB} file is divided into suitable data frames, and after successfully receiving each frame, the receiver sends a 54-byte acknowledgment (ACK) back to the sender. Assuming no processing or queuing delay, determine the total time required to completely transfer the 1\text{ GB} file, including data transmission time, propagation delay, ACK transmission time, and the Stop-and-Wait waiting time. [BSCCPL AME 21-08-2026 (BUET)]

2. **Using an explanation of the difference between flow-control and congestion control, discuss the impact of a stable end-to-end latency.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 424 (ET: BIBM)]*

3. **(খ) Congestion কী? Network-এ কীভাবে Congestion নিয়ন্ত্রণ করা যায়? আলোচনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 415 (ET: N/A)]*

4. **Unit of data link layer?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

5. **(ক) নেটওয়ার্কে ডাটা প্যাকেটে trailer কোথায় এবং কেন ব্যবহার করা হয়? উদাহরণ দিন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 775 (ET: N/A)]*

6. **How STP works? Explain congestion control algorithm.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 842-843 (ET: N/A)]*

7. **Host A is sending data to Host B over a full duplex link. A and B are using the sliding window protocol for flow control. The send and receive window size are 5 packets each. Data packets (sent only from A to B) are all 1000 bytes long and transmission time for such a packet is 50\mu\text{s}. Acknowledgement packets (sent only from B to A) are very small and require negligible transmission time. The propagation delay over the link is 200\mu\text{s}. What is the maximum achievable throughput in this communication?** *[BAUST Assistant Programmer 2021 compact it 918 (ET: N/A)]*

8. **What is the piggybacking and MAC Address?** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 921 (ET: N/A)]*

9. **(i) Congestion Control কী? কী কী ভাবে Congestion Control করা যায়?** *[BPSC Assistant Network Engineer 2020 compact it 950 (ET: N/A)]*

10. **Two OSI layers which known as “flow Control” which are those? Write them and explain.** *[Bangladesh Bank Assistant Programmer 2019 compact it 1156 (ET: DU)]*

11. **What is piggybacking in Networking? Difference among Hub, Switch and Router.** *[BCC-4TDC Assistant Programmer 2019 compact it 1161 (ET: BCC)]*

12. **Explain IEEE 802.3 frame format.** *[Multiple Ministry Assistant Programmer 2017 compact it 1233 (ET: N/A)]*

## Network Services (DHCP, NAT) (11)

1. **What is the DHCP in computer networking?** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 405 (ET: N/A)]*

2. **What is the NAT in Computer networking?** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 405 (ET: N/A)]*

3. **NAT Stands for __________?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

4. **Which two services are required to enable a computer to receive dynamic IP address and access internet using domain names?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 634 (ET: N/A)]*

5. **What is DHCP Server and why it is needed in a computer network.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 670 (ET: N/A)]*

6. **(b) Explain the message flow between a DHCP server and client. Show necessary timing diagram.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 799 (ET: N/A)]*

7. **What is APIPA?** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 840 (ET: N/A)]*

8. **What do you mean by DHCP server? Explain the benefits of using dedicated DHCP server. Briefly describe the main benefits of using IPv6 protocol.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 914 (ET: N/A)]*

9. **১৬. DHCP uses UDP port _____ for sending data to the server.** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 942 (ET: N/A)]*

10. **DHCP কি? DHCP কিভাবে কাজ করে লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1043 (ET: DPI)]*

11. **Write the disadvantage of manual IP. Name the protocol of dynamic IP assigning. DHCP how works?** *[BTCL Assistant Manager (Technical) 2017 compact it 1255 (ET: N/A)]*

## Digital Modulation & Signal Processing (BPSK, QPSK) (10)

1. **Draw Bit Error Rate vs Signal to Noise Ratio curve of QPSK and BPSK.** *[NWPGCL Assistant Manager (ICT) 12.01.2024 compact it 293 (ET: BUET)]*

2. **What is baseband and passband frequency?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 499 (ET: N/A)]*

3. **অথবা, (ক) Low-pass Channel এবং Band-pass Channel এর মধ্যে উদাহরণসহ পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 628 (ET: N/A)]*

4. **What is modulation? Why is it necessary?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 637 (ET: N/A)]*

5. **Amplitude Modulation related problem. (Approximate)** *[NPCBL Executive Trainee (IT) 2022 compact it 644 (ET: BUET)]*

6. **Compare between (i) AM and ASK and (ii) FM and FSK considering modulation scheme, bandwith requirement, noise tolerance and circuit complexity.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

7. **What are the advantages of PSK and explain why coherent detection is necessary for demodulating the PSK signal?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

8. **Draw the constellation diagram of QPSK, 8-PSK and 32-QAM. Why these multilevel signals prefereed and what are the challenges for multilevel modulation?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

9. **a) What is QAM? Explain it.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1030 (ET: N/A)]*

10. **b) Draw diagram for 16 QAM having? (i) 3 amplitudes, 12 phases (ii) 4 amplitudes, 8 phases** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1030-1031 (ET: N/A)]*

## Email Architecture & Protocols (SMTP, POP3, IMAP) (10)

1. **Sinthia wants to send an email to her friend (Afsana). He sends the email through application and transport layer.** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1323 (ET: DU)]*
   * (a) Mention the protocol of application layer and transport layer.
   * (b) Write down the steps of Mail transfer from Afsana to Sinthia.

2. **Difference between: (i) SMTP and SNMP (ii) HTTP and HTTPs** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 550 (ET: BIBM)]*

3. **Which protocol is used for email received?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

4. **(a) Distinguish the purpose of SMTP and IMAP in email communication.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 688 (ET: N/A)]*

5. **Email এর ক্ষেত্রে CC এবং BCC এর অর্থ কি বুঝায়?** *[BPSC Computer Operator 2021 compact it 780 (ET: N/A)]*

6. **Which of the following is correct email formate? (a) compact@webmail.com (b) compact@webmail@com (c) compact.webmail.com (d) None** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

7. **E-mail পাঠানো এবং রিসিভ করার জন্য একটি করে প্রোটোকলের নাম লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 866 (ET: BUET)]*

8. **Which protocol provides e-mail facility amount different hosts?** *[BSEC Assistant Director (MIS) 2021 compact it 937 (ET: IBA)]*

9. **ই-মেইল করার ক্ষেত্রে TO, CC ও BCC কোন ব্যবহার করা হয়?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 945 (ET: N/A)]*

10. **(a) What is SMTP? How SMTP works?** *[BPSC Assistant Programmer (ICT) 2019 compact it 1143 (ET: N/A)]*

## Application Layer & Well-Known Port Numbers (6)

1. Full Form and Port Number – SSH, FTP, SMTP, DNS, IMAP. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

2. **What is the port number used by DNS?** *[BBA Assistant Programmer 12.07.2025 compact it 1432 (ET: BUET)], [BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)], [BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

3. **HTTPS এর পোর্ট নাম্বার কত?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

4. **Write the port address of the following applications of data communications. (i) HTTP; (ii) HTTPS; (iii) FTP; (iv) SMTP; (v) POP** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 671 (ET: N/A)]*

5. **Describe TCP/IP protocols and its ports.** *[BDCCL Assistant Engineer (Network) 2022 compact it 742 (ET: N/A)]*

6. **A server has port number 1223. A user is requesting the server (www.example.com) but it is showing server is not reached. How can you solve this?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*

## Pulse Code Modulation (PCM) & Signal Processing (6)

1. **A PCM system have step resolution of 2V. Sinusoidal signal amplitude 10V. SNR=? And total number of bits=?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)], [BTCL Assistant Manager (Technical) 2021 compact it 765 (ET: BUET)]*

2. **Draw Delta modulation figure and math. (Approximate)** *[NPCBL Executive Trainee (IT) 2022 compact it 648 (ET: BUET)]*

3. **A singla-tone message signal of bandwidth 4KHZ and amplitude 10V is transmitted by \Delta-modulation with step size 2V. Determine the data rate so that slope overloading noise is the minimum.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

4. **A single-tone message signal of bandwidth 4 KHZ is sampled by using a pulse train of frequency 200% higher than the Nyquist rate of the message signal to obtain PAM signal. The duty cycle of the pulse train is 20%. By drawing the amplitude spectrum of the PAM signal, determine its bandwidth.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 676 (ET: N/A)]*

5. **Define pulse amplitude modulation. Explaine the different type of computer network.** *[Sonali & Janata Bank Officer (IT/ICT) 2019 compact it 1107 (ET: AUST)]*

6. **Consider an audio signal with spectral component limited to the frequency band to 3300Hz. Assume that a sampling rate of 8000s/s with be used to generate a signal power to average needs to be 30dB.** *[NWPGCL Assistant Engineer (CSE) 2019 compact it 1154 (ET: RUET)]*
   a) What the minimum number of bit per sample?
   b) Calculate the minimum channel bandwidth required for transmission of such a PCM signal.

## Switching Techniques (Circuit vs Packet Switching) (5)

1. **Why is packet switching more suitable for internet communication?** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

2. **Difference between circuit switching and packet switching. Identify which of the two is predominantly used in Internet communication and justify why?** *[BUET Assistant Programmer 21.06.2025 compact it 1435 (ET: BUET)]*

3. **(c) Compare circuit switching and packet switching.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1353 (ET: N/A)]*

4. **Do you prefer packet switching compared to circuit switching in communication network? If Yes, why? How does packet switching work step by step? What applications use packet switching?** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 536 (ET: MIST)]*

5. **Why is packet suiting suitable for digital data transmission?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 681 (ET: N/A)]*

## WAN Technologies (SONET/SDH, ATM, WDM) (5)

1. **White short notes on: (i) SONET/SDH; (ii) IP telephony; (iii) WDM technology; (iv) ATM network** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*

2. **(c) Explain IPTV and VOIP.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 794 (ET: N/A)]*

3. **Write the full form of the given technologies CX, IGW and IIG. Write feature of there technologies.** *[BTRC Assistant Director (Technical) 2021 compact it 806 (ET: IBA)]*

4. **TSCM এর কাজ কী? VoIP পরিচালনায় কী কী সরঞ্জামের প্রয়োজন হয়?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 810 (ET: IBA)]*

5. **Write down the difference between IPoE and PPPoE.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 839-840 (ET: N/A)]*

## Network Layer (Packet Fragmentation & Tunneling) (4)

1. **(a) How do you define packet fragmentation? Explain briefly the transparent and non-transparent fragmentation with necessary diagram.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 481 (ET: N/A)]*

2. **(b) Describe briefly the TCP/IP tunneling using appropriate diagram.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 482 (ET: N/A)]*

3. **Why network need packet fragmentation? Define different types of packet fragmentation with necessary diagram.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 666 (ET: N/A)]*

4. **Suppose a 22-byte packet is to be transmitted through a network of \text{MTU} = 3\text{ byte}. The elementary fragment size is 1\text{ byte}. Show the segment numbering of the above packet. Packet number is 217.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*

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
