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
