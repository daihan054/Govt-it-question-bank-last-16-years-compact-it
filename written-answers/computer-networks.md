<!-- TOC START -->
**Table of Contents** — 33 subtopics · 440 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Subnetting & IP Addressing](#subnetting--ip-addressing-95) | 95 |
| 2 | [OSI & TCP/IP Reference Model](#osi--tcpip-reference-model-43) | 43 |
| 3 | [Networking Fundamentals & Terminology](#networking-fundamentals--terminology-23) | 23 |
| 4 | [Application Layer Protocols & Troubleshooting (DNS, DHCP, HTTPS)](#application-layer-protocols--troubleshooting-dns-dhcp-https-19) | 19 |
| 5 | [Multiplexing & Bandwidth](#multiplexing--bandwidth-18) | 18 |
| 6 | [Routing Protocols & Route Configuration](#routing-protocols--route-configuration-18) | 18 |
| 7 | [Wireless Networks & IoT (mmWave)](#wireless-networks--iot-mmwave-17) | 17 |
| 8 | [Transport Layer (TCP & UDP)](#transport-layer-tcp--udp-15) | 15 |
| 9 | [Networking Devices](#networking-devices-14) | 14 |
| 10 | [Communication System & Transmission Modes](#communication-system--transmission-modes-14) | 14 |
| 11 | [Physical Layer & Transmission Media (Cables & Wiring)](#physical-layer--transmission-media-cables--wiring-14) | 14 |
| 12 | [Error Detection & Data Communication (CRC, Throughput)](#error-detection--data-communication-crc-throughput-14) | 14 |
| 13 | [Data Rate & Channel Capacity (Nyquist, Shannon)](#data-rate--channel-capacity-nyquist-shannon-14) | 14 |
| 14 | [Network Topologies](#network-topologies-12) | 12 |
| 15 | [IPv6 Addressing](#ipv6-addressing-11) | 11 |
| 16 | [Physical Layer & Optical Fiber (Attenuation & Power Budget)](#physical-layer--optical-fiber-attenuation--power-budget-11) | 11 |
| 17 | [Network Address Translation (NAT)](#network-address-translation-nat-11) | 11 |
| 18 | [Network Services (DHCP, NAT)](#network-services-dhcp-nat-10) | 10 |
| 19 | [Digital Modulation & Signal Processing (BPSK, QPSK)](#digital-modulation--signal-processing-bpsk-qpsk-10) | 10 |
| 20 | [Flow Control & Data Link Layer (Stop-and-Wait)](#flow-control--data-link-layer-stop-and-wait-9) | 9 |
| 21 | [Email Architecture & Protocols (SMTP, POP3, IMAP)](#email-architecture--protocols-smtp-pop3-imap-9) | 9 |
| 22 | [Application Layer & Well-Known Port Numbers](#application-layer--well-known-port-numbers-6) | 6 |
| 23 | [Switching Techniques (Circuit vs Packet Switching)](#switching-techniques-circuit-vs-packet-switching-5) | 5 |
| 24 | [WAN Technologies (SONET/SDH, ATM, WDM)](#wan-technologies-sonetsdh-atm-wdm-5) | 5 |
| 25 | [Pulse Code Modulation (PCM) & Signal Processing](#pulse-code-modulation-pcm--signal-processing-4) | 4 |
| 26 | [Network Layer (Packet Fragmentation & Tunneling)](#network-layer-packet-fragmentation--tunneling-4) | 4 |
| 27 | [Analog Modulation & Radio Receivers](#analog-modulation--radio-receivers-3) | 3 |
| 28 | [Satellite Communication](#satellite-communication-3) | 3 |
| 29 | [Line Coding & Digital Encoding](#line-coding--digital-encoding-2) | 2 |
| 30 | [Address Resolution (ARP & RARP)](#address-resolution-arp--rarp-2) | 2 |
| 31 | [VLANs & Subnetting Comparison](#vlans--subnetting-comparison-2) | 2 |
| 32 | [Spread Spectrum & Multiple Access (CDMA, FHSS, DSSS)](#spread-spectrum--multiple-access-cdma-fhss-dsss-2) | 2 |
| 33 | [High Availability & Redundancy Protocols (VRRP, HSRP)](#high-availability--redundancy-protocols-vrrp-hsrp-1) | 1 |

<!-- TOC END -->

---

## Subnetting & IP Addressing (95)

1. An organization is granted the IPv4 network block 14.24.74.0/24 and needs to segment it into two subnets: Subnet A (requires 120 addresses) and Subnet B (requires 60 addresses). Allocating sequentially from the requirement first to maximize remaining address space, state only the Network Address (with its CIDR mask) and the Broadcast Address for both subnets. [SO IT 25-07-2026]


   Answer:

   Step 1, size each subnet:
   - Subnet A needs 120 addresses. 2⁷ = 128 ≥ 120 + 2, so 7 host bits are needed, giving a /25.
   - Subnet B needs 60 addresses. 2⁶ = 64 ≥ 60 + 2, so 6 host bits are needed, giving a /26.

   Step 2, allocate sequentially, largest first:

   Subnet A, /25:
   - Network address: 14.24.74.0/25
   - Broadcast address: 14.24.74.127

   Subnet B, /26, starting from the next free address 14.24.74.128:
   - Network address: 14.24.74.128/26
   - Broadcast address: 14.24.74.191

   Final answer:
   - Subnet A: 14.24.74.0/25, broadcast 14.24.74.127
   - Subnet B: 14.24.74.128/26, broadcast 14.24.74.191
   - Remaining free space: 14.24.74.192/26, that is 64 addresses left for future use.
2. An organization has been assigned the IPv4 network address 192.168.1.0/24. As part of the network deployment, the network administrator is required to divide the address space into four equal-sized subnets to support different departments. Determine the Network Address, Subnet Mask (both CIDR and dotted-decimal notation). *[Officer (IT) 31 Jul 2026 bscs 01 (ET: N/A)]*


   Answer:

   Step 1, bits to borrow:
   - Number of subnets required = 4, and 2ⁿ ≥ 4 gives n = 2, so 2 bits are borrowed from the host part.

   Step 2, new prefix and mask:
   - New prefix = /24 + 2 = /26
   - Subnet mask in dotted decimal = 255.255.255.192
   - Binary of the last octet: 11000000

   Step 3, block size and the four subnets:
   - Block size = 256 − 192 = 64 addresses per subnet, of which 62 are usable.

   | Subnet | Network address | Mask | Usable range | Broadcast |
   |---|---|---|---|---|
   | 1 | 192.168.1.0/26 | 255.255.255.192 | 192.168.1.1 to 192.168.1.62 | 192.168.1.63 |
   | 2 | 192.168.1.64/26 | 255.255.255.192 | 192.168.1.65 to 192.168.1.126 | 192.168.1.127 |
   | 3 | 192.168.1.128/26 | 255.255.255.192 | 192.168.1.129 to 192.168.1.190 | 192.168.1.191 |
   | 4 | 192.168.1.192/26 | 255.255.255.192 | 192.168.1.193 to 192.168.1.254 | 192.168.1.255 |

   Final answer: subnet mask /26, that is 255.255.255.192, with the four network addresses 192.168.1.0, 192.168.1.64, 192.168.1.128 and 192.168.1.192.
3. Subnetting logic requires precise binary calculation. A network engineer is tasked with dividing the internal network 192.168.10.0/24 into exactly 4 equal subnets for four different bank branches. Show the mathematical calculation to determine how many bits must be borrowed to create 4 subnets, and state the new Subnet Mask in both CIDR notation and decimal format. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*


   Answer:

   Step 1, how many bits must be borrowed:
   - The rule is 2ⁿ ≥ number of subnets required, where n is the number of borrowed bits.
   - 2¹ = 2, which is less than 4.
   - 2² = 4, which equals 4. So n = 2 bits must be borrowed.

   Step 2, the new prefix:
   - Original prefix /24, so 24 + 2 = /26.

   Step 3, the mask in binary and decimal:
   - /26 means the first 26 bits are 1: 11111111.11111111.11111111.11000000
   - The last octet 11000000 = 128 + 64 = 192
   - Subnet mask = 255.255.255.192

   Step 4, verification:
   - Host bits left = 32 − 26 = 6, so each subnet has 2⁶ = 64 addresses and 2⁶ − 2 = 62 usable hosts.
   - 4 subnets × 64 = 256 addresses, which is exactly the original /24, so nothing is wasted.

   The four branch subnets:

   | Branch | Network | Usable range | Broadcast |
   |---|---|---|---|
   | 1 | 192.168.10.0/26 | 192.168.10.1 to 192.168.10.62 | 192.168.10.63 |
   | 2 | 192.168.10.64/26 | 192.168.10.65 to 192.168.10.126 | 192.168.10.127 |
   | 3 | 192.168.10.128/26 | 192.168.10.129 to 192.168.10.190 | 192.168.10.191 |
   | 4 | 192.168.10.192/26 | 192.168.10.193 to 192.168.10.254 | 192.168.10.255 |

   Final answer: 2 bits must be borrowed, and the new subnet mask is /26, that is 255.255.255.192.
4. Network Address, Broadcast Address, Subnet Mask and Usable Host IP Range of: 10.0.0.0/30, 192.168.0.0/23, 172.16.1.0/24. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*


   Answer:

   | Item | 10.0.0.0/30 | 192.168.0.0/23 | 172.16.1.0/24 |
   |---|---|---|---|
   | Network address | 10.0.0.0 | 192.168.0.0 | 172.16.1.0 |
   | Subnet mask | 255.255.255.252 | 255.255.254.0 | 255.255.255.0 |
   | Broadcast address | 10.0.0.3 | 192.168.1.255 | 172.16.1.255 |
   | Usable host range | 10.0.0.1 to 10.0.0.2 | 192.168.0.1 to 192.168.1.254 | 172.16.1.1 to 172.16.1.254 |
   | Usable hosts | 2 | 510 | 254 |

   Working:
   - /30: host bits = 2, so 2² = 4 addresses and 4 − 2 = 2 usable. This is the standard mask for a point to point router link.
   - /23: host bits = 9, so 2⁹ = 512 addresses and 510 usable. The block spans two whole third octets, 192.168.0.x and 192.168.1.x.
   - /24: host bits = 8, so 256 addresses and 254 usable.
5. (a) IP address এবং MAC/MU এর পার্থক্য লেখ।

   Answer:

   (a) Difference between IP address and MAC address:

   | Point | IP address | MAC address |
   |---|---|---|
   | Layer | Network layer, layer 3 | Data link layer, layer 2 |
   | Length | 32 bits for IPv4, 128 bits for IPv6 | 48 bits |
   | Format | 192.168.1.10 | 00:1A:2B:3C:4D:5E |
   | Assigned by | The administrator or DHCP | The manufacturer, burned into the NIC |
   | Nature | Logical and changeable | Physical and permanent |
   | Structure | Hierarchical, network part plus host part | Flat, the first 24 bits are the vendor OUI |
   | Scope | End to end across the whole Internet | Within one local network only |
   | Forwarded by a router | Yes | No |
   | Changes in transit | No, except under NAT | Yes, rewritten at every hop |
   | Resolved by | DNS, from a name to an address | ARP, from an IP address to a MAC address |

   (b) Difference between classful and classless IP addressing:

   | Point | Classful | Classless, that is CIDR |
   |---|---|---|
   | Division | Fixed Class A, B, C, D and E | No classes at all |
   | Mask | A fixed default mask, /8, /16 or /24 | Any prefix from /1 to /32 |
   | Notation | The IP address alone | The IP address written with a /n prefix |
   | Address waste | Very high, since only three sizes exist | Very low, since a block of the required size is given |
   | VLSM | Not supported | Supported, so different subnet sizes may be used in one network |
   | Route summarisation | Not possible | Possible, so routing tables stay small |
   | Routing protocols | RIPv1, IGRP | RIPv2, OSPF, EIGRP, BGP |
   | Status | Obsolete, replaced in 1993 | The system in use today |

   (c) Class of the given IP address:
   - Binary: 11000001 00001001 00001010 00010101
   - First octet 11000001 = 128 + 64 + 1 = 193
   - In dotted decimal the address is 193.9.10.21
   - The first octet 193 lies between 192 and 223, and in binary it begins with 110.
   - Answer: this is a Class C IP address.
6. **A bank has the network block 192.168.10.0/24. The IT manager wants to divide this into 4 equal subnets.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*
(a) How many bits do you need to borrow to make 4 subnets?
(b) What is the new Subnet Mask in dotted-decimal format?
(c) Write down the Network Address, the First Usable IP, and the Broadcast Address for the second subnet created. Show your calculation.


   Answer:

   (a) Bits to borrow:
   - Rule: 2ⁿ ≥ number of subnets. 2¹ = 2 < 4, and 2² = 4 = 4, so n = 2 bits must be borrowed.

   (b) New subnet mask:
   - New prefix = /24 + 2 = /26
   - Binary: 11111111.11111111.11111111.11000000
   - Dotted decimal: 255.255.255.192

   (c) Second subnet:
   - Block size = 256 − 192 = 64, so the subnets start at 0, 64, 128 and 192.
   - The second subnet therefore begins at 192.168.10.64.
   - Network address: 192.168.10.64
   - First usable IP: 192.168.10.65
   - Last usable IP: 192.168.10.126
   - Broadcast address: 192.168.10.127

   Calculation shown:
   - Host bits left = 32 − 26 = 6, so each subnet holds 2⁶ = 64 addresses and 2⁶ − 2 = 62 usable hosts.
   - Second subnet range = 192.168.10.64 to 192.168.10.64 + 63 = 192.168.10.127; the first of these is the network address and the last is the broadcast address.

   All four subnets for reference:

   | Subnet | Network | Usable range | Broadcast |
   |---|---|---|---|
   | 1 | 192.168.10.0 | .1 to .62 | 192.168.10.63 |
   | 2 | 192.168.10.64 | .65 to .126 | 192.168.10.127 |
   | 3 | 192.168.10.128 | .129 to .190 | 192.168.10.191 |
   | 4 | 192.168.10.192 | .193 to .254 | 192.168.10.255 |
7. **What is subnetting? For the network 192.168.1.0/22, how many usable host addresses does it have?** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*


   Answer:

   What subnetting is:
   - Subnetting is the process of dividing one large IP network into several smaller logical networks called subnets, by borrowing bits from the host part of the address and adding them to the network part.
   - Purpose: to reduce the size of broadcast domains, improve performance and security, use address space efficiently, and make administration and troubleshooting easier.

   Usable hosts in 192.168.1.0/22:
   - Prefix /22, so host bits = 32 − 22 = 10.
   - Total addresses = 2¹⁰ = 1024.
   - Usable hosts = 1024 − 2 = 1022, since the first is the network address and the last is the broadcast address.

   Final answer: 1022 usable host addresses.

   - Note: with a /22 mask the address 192.168.1.0 is not itself a network address. The block boundary falls on a multiple of 4 in the third octet, so the actual network is 192.168.0.0/22, running from 192.168.0.0 to 192.168.3.255, with the usable range 192.168.0.1 to 192.168.3.254.
8. **Given IP address 10.0.0.100 and Subnet mask 255.255.240.0 which is network address?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1449 (ET: N/A)]*


   Answer:

   Given: IP 10.0.0.100, subnet mask 255.255.240.0, which is a /20.

   Step 1, AND the address with the mask, octet by octet:
   - 10 AND 255 = 10
   - 0 AND 255 = 0
   - 0 AND 240 = 0
   - 100 AND 0 = 0

   Step 2, read the result:
   - Network address = 10.0.0.0

   Final answer: the network address is 10.0.0.0/20.

   - Supporting values: block size in the third octet = 256 − 240 = 16, so the block runs from 10.0.0.0 to 10.0.15.255. The broadcast address is 10.0.15.255, the usable range is 10.0.0.1 to 10.0.15.254, and there are 2¹² − 2 = 4094 usable hosts.
9. **Given IP address 10.10.0.0/16, you have divide the network into eight equal subnets. Find the subnet mask in dotted decimal and CIDR notation. Also find the first and last usable IP addresses of third subnet.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1362 (ET: BUET)], [DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*


   Answer:

   Step 1, bits to borrow for 8 subnets:
   - 2ⁿ ≥ 8 gives n = 3, so 3 bits are borrowed from the host part.

   Step 2, new prefix and mask:
   - New prefix = /16 + 3 = /19
   - Binary: 11111111.11111111.11100000.00000000
   - Dotted decimal: 255.255.224.0
   - CIDR notation: /19

   Step 3, block size:
   - Block size in the third octet = 256 − 224 = 32, so each subnet holds 32 × 256 = 8192 addresses, of which 8190 are usable.

   Step 4, the eight subnets:

   | Subnet | Network | Usable range | Broadcast |
   |---|---|---|---|
   | 1 | 10.10.0.0/19 | 10.10.0.1 to 10.10.31.254 | 10.10.31.255 |
   | 2 | 10.10.32.0/19 | 10.10.32.1 to 10.10.63.254 | 10.10.63.255 |
   | 3 | 10.10.64.0/19 | 10.10.64.1 to 10.10.95.254 | 10.10.95.255 |
   | 4 | 10.10.96.0/19 | 10.10.96.1 to 10.10.127.254 | 10.10.127.255 |
   | 5 | 10.10.128.0/19 | 10.10.128.1 to 10.10.159.254 | 10.10.159.255 |
   | 6 | 10.10.160.0/19 | 10.10.160.1 to 10.10.191.254 | 10.10.191.255 |
   | 7 | 10.10.192.0/19 | 10.10.192.1 to 10.10.223.254 | 10.10.223.255 |
   | 8 | 10.10.224.0/19 | 10.10.224.1 to 10.10.255.254 | 10.10.255.255 |

   Final answer:
   - Subnet mask = 255.255.224.0, that is /19.
   - Third subnet: first usable IP 10.10.64.1 and last usable IP 10.10.95.254.
10. **Subnet mask & Total host calculation.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*


    Answer: Method for finding the subnet mask and the total number of hosts.

    Formulas:
    - Host bits h = 32 − prefix length.
    - Total addresses per subnet = 2ʰ.
    - Usable hosts = 2ʰ − 2, because the all zeros address is the network address and the all ones address is the broadcast address.
    - Borrowed bits n = prefix length − default prefix of the class; number of subnets = 2ⁿ.
    - Block size = 256 − the value of the interesting octet of the mask, that is the last non-255 octet.

    Reference table:

    | Prefix | Subnet mask | Block size | Total addresses | Usable hosts |
    |---|---|---|---|---|
    | /24 | 255.255.255.0 | 256 | 256 | 254 |
    | /25 | 255.255.255.128 | 128 | 128 | 126 |
    | /26 | 255.255.255.192 | 64 | 64 | 62 |
    | /27 | 255.255.255.224 | 32 | 32 | 30 |
    | /28 | 255.255.255.240 | 16 | 16 | 14 |
    | /29 | 255.255.255.248 | 8 | 8 | 6 |
    | /30 | 255.255.255.252 | 4 | 4 | 2 |

    Worked example: 192.168.20.0/27
    - Host bits = 32 − 27 = 5, so 2⁵ = 32 addresses and 30 usable hosts.
    - Mask = 255.255.255.224, block size = 256 − 224 = 32.
    - Subnets start at .0, .32, .64, .96, .128, .160, .192 and .224, giving 8 subnets from the /24.
    - The exception to remember: a /31 is used for point to point links under RFC 3021 and gives 2 usable addresses, and a /32 is a single host route.
11. **Given the network 245.248.128.0/20, divide the address space among three departments as follows:**
   **(a) Manager: half of the address space.**
   **(b) HR: one-quarter of the address space.**
   **(c) Admin: the remaining one-quarter.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1437 (ET: BUET)]*

   **For each department, determine:**
   **(i) The network block (in CIDR notation).**
   **(ii) The IP address valid range.**
   **(iii) The number of valid hosts.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1438 (ET: BUET)]*


    Answer:

    Given: 245.248.128.0/20, which holds 2¹² = 4096 addresses, from 245.248.128.0 to 245.248.143.255.

    Step 1, translate the shares into prefixes:
    - Manager needs half, that is 2048 addresses, so the prefix is /21.
    - HR needs one quarter, that is 1024 addresses, so the prefix is /22.
    - Admin needs the remaining quarter, 1024 addresses, so the prefix is /22.

    Step 2, allocate sequentially, largest first:

    | Department | (i) Network block | (ii) Valid IP range | (iii) Valid hosts |
    |---|---|---|---|
    | Manager | 245.248.128.0/21 | 245.248.128.1 to 245.248.135.254 | 2046 |
    | HR | 245.248.136.0/22 | 245.248.136.1 to 245.248.139.254 | 1022 |
    | Admin | 245.248.140.0/22 | 245.248.140.1 to 245.248.143.254 | 1022 |

    Broadcast addresses: Manager 245.248.135.255, HR 245.248.139.255, Admin 245.248.143.255.

    Check: 2048 + 1024 + 1024 = 4096, which is exactly the /20, so the whole block is used with nothing left over.
12. **Find out the network address and Broadcast address of the address: 192.168.0.0/28** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1360 (ET: BUET)]*


    Answer:

    Given: 192.168.0.0/28.

    Step 1, host bits and block size:
    - Host bits = 32 − 28 = 4, so 2⁴ = 16 addresses per block.
    - Subnet mask = 255.255.255.240, and the block size is 256 − 240 = 16.

    Step 2, network and broadcast:
    - Network address = 192.168.0.0
    - Broadcast address = network address + block size − 1 = 192.168.0.0 + 15 = 192.168.0.15

    Final answer:
    - Network address: 192.168.0.0
    - Broadcast address: 192.168.0.15
    - Usable host range: 192.168.0.1 to 192.168.0.14, that is 14 hosts.
13. **(a) An organization wants to divide its LAN IP address 192.168.0.0/24 into 4 subnets according to buildings. The buildings IP address creiteria are given below.**

| Building block | Hosts need |
|---|---|
| A | 110 |
| B | 50 |
| C | 20 |
| D | 8 |

**Calculate the network and broadcast address of this network for each building block.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1443 (ET: N/A)]*


    Answer: This requires VLSM, that is Variable Length Subnet Masking, allocating the largest requirement first.

    Step 1, choose a prefix for each building:

    | Building | Hosts needed | Host bits, 2ʰ − 2 ≥ need | Prefix | Block size | Usable |
    |---|---|---|---|---|---|
    | A | 110 | 7, since 2⁷ − 2 = 126 | /25 | 128 | 126 |
    | B | 50 | 6, since 2⁶ − 2 = 62 | /26 | 64 | 62 |
    | C | 20 | 5, since 2⁵ − 2 = 30 | /27 | 32 | 30 |
    | D | 8 | 4, since 2⁴ − 2 = 14 | /28 | 16 | 14 |

    Step 2, allocate sequentially from 192.168.0.0, largest block first:

    | Building | Network address | Subnet mask | Usable range | Broadcast address |
    |---|---|---|---|---|
    | A | 192.168.0.0/25 | 255.255.255.128 | 192.168.0.1 to 192.168.0.126 | 192.168.0.127 |
    | B | 192.168.0.128/26 | 255.255.255.192 | 192.168.0.129 to 192.168.0.190 | 192.168.0.191 |
    | C | 192.168.0.192/27 | 255.255.255.224 | 192.168.0.193 to 192.168.0.222 | 192.168.0.223 |
    | D | 192.168.0.224/28 | 255.255.255.240 | 192.168.0.225 to 192.168.0.238 | 192.168.0.239 |

    Check: 128 + 64 + 32 + 16 = 240 addresses used out of 256, so 192.168.0.240/28, that is 16 addresses, is left free for future growth.

    - The reason for allocating largest first is that it keeps every block correctly aligned on its own boundary; allocating smallest first would leave gaps that no larger block could fit into.
14. **Check the valid IP address from the following table.** *[BREB Assistant Programmer (AP) 21.02.2025 compact it 1335 (ET: N/A)]*


    Answer: Rules for deciding whether an IPv4 address is valid, with the usual test cases.

    Validity rules:
    - The address must have exactly four octets separated by dots.
    - Each octet must be a decimal number from 0 to 255; anything above 255 is invalid.
    - No octet may be empty, and no letters or special characters are allowed.
    - Leading zeros should not be used, since they may be read as octal.
    - The first octet 127 is reserved for loopback, and 0 and 255 as a whole first octet are reserved.
    - An address ending in the all zeros host part is a network address and one ending in the all ones host part is a broadcast address; neither may be assigned to a host.

    | Example | Valid? | Reason |
    |---|---|---|
    | 192.168.1.10 | Valid | All four octets are in range, and it is a usable private host address |
    | 256.100.50.25 | Invalid | 256 exceeds the maximum of 255 |
    | 192.168.1 | Invalid | Only three octets |
    | 172.16.0.0/16 | Valid block, but not a host address | It is the network address of the block |
    | 10.0.0.255/24 | Not assignable | It is the broadcast address of 10.0.0.0/24 |
    | 127.0.0.1 | Valid but special | Loopback, refers to the machine itself |
    | 192.168.01.1 | Invalid in practice | Leading zero may be interpreted as octal |
    | 300.1.1.1 | Invalid | 300 exceeds 255 |
15. **(a) A network has been assigned the IP address 200.1.2.0/24. It has 3 subnets. Determine the following for each subnet:** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1352 (ET: N/A)]*
 * **(i) Total number of IP addresses**
 * **(ii) Range of usable IP addresses**
 * **(iii) Network address**
 * **(iv) Direct broadcast address**
 * **(v) Limited broadcast address.**


    Answer:

    Given: 200.1.2.0/24, to be divided into 3 subnets.

    Step 1, bits to borrow:
    - 2ⁿ ≥ 3 gives n = 2, so 2 bits are borrowed and the prefix becomes /26. This creates 4 equal subnets, of which 3 are used and 1 is kept spare.
    - Subnet mask = 255.255.255.192, block size = 64.

    Step 2, the results for each subnet:

    | Item | Subnet 1 | Subnet 2 | Subnet 3 |
    |---|---|---|---|
    | (i) Total number of IP addresses | 64 | 64 | 64 |
    | (ii) Range of usable IP addresses | 200.1.2.1 to 200.1.2.62 | 200.1.2.65 to 200.1.2.126 | 200.1.2.129 to 200.1.2.190 |
    | (iii) Network address | 200.1.2.0/26 | 200.1.2.64/26 | 200.1.2.128/26 |
    | (iv) Direct broadcast address | 200.1.2.63 | 200.1.2.127 | 200.1.2.191 |
    | (v) Limited broadcast address | 255.255.255.255 | 255.255.255.255 | 255.255.255.255 |

    - Usable hosts per subnet = 64 − 2 = 62.
    - The direct broadcast address is the last address of the subnet and it is routable, so a host outside can in principle send to it. The limited broadcast address 255.255.255.255 is the same for every network and is never forwarded by a router; it is used, for example, by DHCPDISCOVER.
    - The fourth subnet, 200.1.2.192/26, is left unused and available for future expansion.
16. **The IP address of a device in a network is 172.16.128.123/22. Answer the following questions:** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1343 (ET: N/A)]*
   * **i) What is the network address?**
   * **ii) What is the subnet mask for the given network?**
   * **iii) What is the broadcast address?**
   * **iv) What is the maximum number of devices this network can connect?**
   * **v) What is the IP address of the first host device in the network?**


    Answer:

    Given: 172.16.128.123/22.

    Step 1, mask and block size:
    - /22 means 22 network bits, so the mask is 11111111.11111111.11111100.00000000 = 255.255.252.0.
    - Block size in the third octet = 256 − 252 = 4, so blocks begin at third octet values 0, 4, 8, ... 128, 132, and so on.

    Step 2, find the block containing 128:
    - 128 is a multiple of 4, so the block starts at 172.16.128.0 and ends at 172.16.131.255.

    Answers:
    - i) Network address: 172.16.128.0
    - ii) Subnet mask: 255.255.252.0, that is /22
    - iii) Broadcast address: 172.16.131.255
    - iv) Maximum number of devices: host bits = 32 − 22 = 10, so 2¹⁰ − 2 = 1022 devices
    - v) First host address: 172.16.128.1

    - The last usable host is 172.16.131.254.
17. **Find the network address, subnet mask, broadcast address, and usable host IP range for the following IP address: 192.9.205.31/16.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1339 (ET: N/A)]*


    Answer:

    Given: 192.9.205.31/16.

    Step 1, mask:
    - /16 means the first 16 bits are the network part, so the subnet mask is 255.255.0.0.

    Step 2, network address, by ANDing the address with the mask:
    - 192 AND 255 = 192, 9 AND 255 = 9, 205 AND 0 = 0, 31 AND 0 = 0
    - Network address = 192.9.0.0

    Step 3, broadcast address, that is all host bits set to 1:
    - Broadcast address = 192.9.255.255

    Step 4, usable host range and count:
    - Host bits = 32 − 16 = 16, so 2¹⁶ = 65,536 addresses and 65,534 usable.
    - Usable range = 192.9.0.1 to 192.9.255.254

    Final answer:
    - Network address: 192.9.0.0
    - Subnet mask: 255.255.0.0
    - Broadcast address: 192.9.255.255
    - Usable host range: 192.9.0.1 to 192.9.255.254, that is 65,534 hosts

    - Note: by the old classful rules 192 is a Class C first octet with a default /24, but the given /16 overrides that, which is exactly what classless addressing allows.
18. **What is the CIDR Prefixes exactly represents the range of IP addresses 10.12.2.0 to 10.12.3.255?** *[BCIC Assistant Programmer 14.02.2025 compact it 1328 (ET: BUET)]*


    Answer:

    Step 1, count the addresses in the range:
    - From 10.12.2.0 to 10.12.3.255 the third octet takes the values 2 and 3, that is 2 blocks of 256 addresses.
    - Total = 2 × 256 = 512 addresses.

    Step 2, find the prefix:
    - 2ʰ = 512 gives h = 9 host bits.
    - Prefix = 32 − 9 = /23.

    Step 3, check the alignment:
    - A /23 block must start on an even third octet, and 2 is even, so 10.12.2.0 is a valid network address.
    - Mask = 255.255.254.0, block size in the third octet = 256 − 254 = 2, so the block covers third octets 2 and 3.

    Final answer: the CIDR prefix is 10.12.2.0/23.

    - Verification: network 10.12.2.0, broadcast 10.12.3.255, usable range 10.12.2.1 to 10.12.3.254, and 510 usable hosts.
19. **Write down the private IP address rang for class B?** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*


    Answer: The private IP address range for Class B is 172.16.0.0 to 172.31.255.255.

    - In CIDR notation this is 172.16.0.0/12, which covers 16 contiguous Class B networks, from 172.16 through 172.31.
    - It contains 2²⁰ = 1,048,576 addresses.
    - Private addresses are defined by RFC 1918 and are not routable on the public Internet, so a host using one needs NAT to reach the outside.
20. **Given IP address 192.168.0.0/28, determine Network address, Broadcast address, First usable IP, Last usable IP.** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*


    Answer:

    Given: 192.168.0.0/28.

    Step 1, mask and block size:
    - Host bits = 32 − 28 = 4, so 2⁴ = 16 addresses per block.
    - Subnet mask = 255.255.255.240, block size = 256 − 240 = 16.

    Step 2, the four values:
    - Network address: 192.168.0.0
    - Broadcast address: 192.168.0.15
    - First usable IP: 192.168.0.1
    - Last usable IP: 192.168.0.14

    Final answer: 14 usable host addresses, from 192.168.0.1 to 192.168.0.14, with 192.168.0.0 as the network address and 192.168.0.15 as the broadcast address.
21. **Write range of private IP address Class A, B and C.** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*


    Answer: The private IP address ranges defined by RFC 1918:

    | Class | Private range | CIDR | Number of addresses |
    |---|---|---|---|
    | A | 10.0.0.0 to 10.255.255.255 | 10.0.0.0/8 | 16,777,216 |
    | B | 172.16.0.0 to 172.31.255.255 | 172.16.0.0/12 | 1,048,576 |
    | C | 192.168.0.0 to 192.168.255.255 | 192.168.0.0/16 | 65,536 |

    - These addresses are not routable on the public Internet, so a device using one must go through NAT to reach the outside world.
    - Two related special ranges worth naming: 127.0.0.0/8 for loopback, and 169.254.0.0/16 for APIPA link local addressing when DHCP fails.
22. **Given an IP address 192.168.111.169/28. Then Determine the (i) Network address (ii) Broadcast address (iii) First usable Host (iv) Last usable Host.** *[BBA Assistant Maintenance Engineer 12.07.2025 compact it 1431 (ET: BUET)]*


    Answer:

    Given: 192.168.111.169/28.

    Step 1, mask and block size:
    - Host bits = 32 − 28 = 4, so 16 addresses per block.
    - Subnet mask = 255.255.255.240, block size = 256 − 240 = 16.

    Step 2, find the block containing 169:
    - Blocks in the last octet start at 0, 16, 32, ... 160, 176.
    - 169 lies between 160 and 175, so the block is 192.168.111.160 to 192.168.111.175.

    Answers:
    - (i) Network address: 192.168.111.160
    - (ii) Broadcast address: 192.168.111.175
    - (iii) First usable host: 192.168.111.161
    - (iv) Last usable host: 192.168.111.174

    - Usable hosts = 16 − 2 = 14.
23. **What are the private IP Ranges for the following IP classes? Class A, Class B and Class C** *[BBA Assistant Maintenance Engineer 12.07.2025 compact it 1431 (ET: BUET)]*


    Answer: The private IP ranges for the three classes:

    | Class | Private range | CIDR | Number of addresses |
    |---|---|---|---|
    | A | 10.0.0.0 to 10.255.255.255 | 10.0.0.0/8 | 16,777,216 |
    | B | 172.16.0.0 to 172.31.255.255 | 172.16.0.0/12 | 1,048,576 |
    | C | 192.168.0.0 to 192.168.255.255 | 192.168.0.0/16 | 65,536 |

    - Defined by RFC 1918. They are reserved for internal use and are never routed on the public Internet, so NAT is required for Internet access.
    - Class A private space is used by very large organisations, Class B by medium ones, and Class C, especially 192.168.0.0/24 and 192.168.1.0/24, in almost every home and small office router.
24. **Which is Class C Default Subnet Mask?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


    Answer: The default subnet mask for Class C is 255.255.255.0, that is /24.

    - In binary: 11111111.11111111.11111111.00000000.
    - It gives 24 network bits and 8 host bits, so each Class C network has 2⁸ = 256 addresses and 254 usable hosts.
    - For comparison, Class A default is 255.0.0.0 (/8) and Class B default is 255.255.0.0 (/16).
25. **What is the maximum number of valid hosts in a network?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


    Answer: The maximum number of valid, that is usable, hosts in a network is 2ʰ − 2, where h is the number of host bits.

    - Two addresses are always subtracted: the all zeros host address, which is the network address, and the all ones host address, which is the directed broadcast address. Neither can be given to a host.
    - Class A, /8: 2²⁴ − 2 = 16,777,214 hosts.
    - Class B, /16: 2¹⁶ − 2 = 65,534 hosts.
    - Class C, /24: 2⁸ − 2 = 254 hosts.
    - The exception is a /31, which under RFC 3021 gives 2 usable addresses on a point to point link because no broadcast is needed there, and a /32, which identifies a single host.
26. **Given IP address 10.2.3.20/22 find the Total valid Host address in this IP?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


    Answer:

    Given: 10.2.3.20/22.

    Step 1, host bits:
    - Host bits = 32 − 22 = 10.

    Step 2, total and usable addresses:
    - Total addresses = 2¹⁰ = 1024.
    - Valid hosts = 1024 − 2 = 1022.

    Final answer: 1022 valid host addresses.

    - Supporting values: mask 255.255.252.0, block size in the third octet = 256 − 252 = 4, so the block starts at 10.2.0.0 and ends at 10.2.3.255. Network address 10.2.0.0, broadcast 10.2.3.255, usable range 10.2.0.1 to 10.2.3.254.
27. **Mapping between MAC to IP address?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


    Answer: The mapping between an IP address and a MAC address is done by ARP and RARP.

    - ARP, the Address Resolution Protocol, maps a known IP address to the unknown MAC address. The host broadcasts an ARP request asking who has that IP, and the owner replies with its MAC address, which is then cached in the ARP table for a few minutes.
    - RARP, the Reverse Address Resolution Protocol, does the opposite, mapping a known MAC address to an IP address. It was used by diskless workstations and has been replaced by BOOTP and DHCP.
    - In IPv6 the same job is done by the Neighbor Discovery Protocol using ICMPv6 Neighbor Solicitation and Neighbor Advertisement messages, which use multicast rather than broadcast.
    - The command to view the cached mappings is `arp -a` on Windows and `arp -n` or `ip neigh` on Linux.
    - Security note: ARP has no authentication, so a false reply can redirect traffic through an attacker. This is ARP spoofing, and it is countered by dynamic ARP inspection and static entries.
28. **How many bits are in a MAC address?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


    Answer: A MAC address is 48 bits, that is 6 bytes, long.

    - It is written as six pairs of hexadecimal digits, for example `00:1A:2B:3C:4D:5E`, since each pair represents 8 bits.
    - The first 24 bits are the Organisationally Unique Identifier assigned to the manufacturer, and the last 24 bits identify the individual card.
    - The total address space is 2⁴⁸, about 281 trillion addresses.
    - The newer EUI-64 format is 64 bits and is used when forming an IPv6 interface identifier from a MAC address.
29. **What is the primary motivation for classful IP address to classless IP addressing?** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 316 (ET: N/A)]*


    Answer: The primary motivation for moving from classful to classless addressing was the rapid exhaustion of the IPv4 address space caused by the enormous waste inherent in fixed classes.

    The problem with classful addressing:
    - Only three usable sizes existed: Class A with 16.7 million hosts, Class B with 65,534 and Class C with 254. Nothing in between was available.
    - An organisation needing 300 hosts was too big for a Class C and had to be given a whole Class B, wasting more than 65,000 addresses. An organisation needing 2000 hosts wasted 63,000.
    - The Class B space ran out fastest, because it was the size almost everyone asked for.
    - The routing tables of the Internet backbone grew explosively, since every allocated network needed its own entry and no summarisation was possible.

    What classless addressing, that is CIDR, solved:
    - The prefix length is written explicitly, so a block of any power of two size can be allocated, exactly matching the requirement. An organisation needing 300 hosts gets a /23 with 510 addresses instead of a whole Class B.
    - VLSM allows different subnet sizes inside one organisation, so a point to point link uses a /30 with two addresses instead of a whole /24.
    - Route summarisation, or supernetting, lets many contiguous networks be advertised as a single prefix, which drastically slowed the growth of the global routing table.
    - Address allocation became hierarchical, following the topology of the Internet, which made aggregation effective.

    - CIDR was introduced in 1993 by RFC 1519. Together with NAT and private addressing it postponed IPv4 exhaustion by about two decades, which is why IPv6 deployment took so long to become urgent.
30. **Given IP address 192.168.1.50, Subnet Mask: 255.255.255.240. Find the valid IP range. Also find Network address and Broadcast address.** *[NWPGCL Assistant Manager (ICT) 12.01.2024 compact it 292 (ET: BUET)], [BTCL Assistant Manager (Technical) 2023 compact it 594 (ET: BUET)], [BPDB Assistant Engineer (CSE) 10.05.2024 compact it 389 (ET: BUET)], [BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 456 (ET: BUET)]*


    Answer:

    Given: IP 192.168.1.50, subnet mask 255.255.255.240, which is a /28.

    Step 1, block size:
    - Block size = 256 − 240 = 16, so blocks in the last octet start at 0, 16, 32, 48, 64 and so on.

    Step 2, find the block containing 50:
    - 50 lies between 48 and 63, so the block is 192.168.1.48 to 192.168.1.63.

    Answers:
    - Network address: 192.168.1.48
    - Broadcast address: 192.168.1.63
    - Valid, that is usable, IP range: 192.168.1.49 to 192.168.1.62
    - Number of usable hosts: 16 − 2 = 14

    - Check by ANDing: 50 in binary is 00110010, and the mask's last octet 240 is 11110000; the AND gives 00110000 = 48, which confirms the network address.
31. **Given IP Address: 192.168.5.154/27, Calculate a) Network Address b) First valid host c) Last valid host d) Broadcast address e) Subnet mask** *[NSDA Assistant Maintenance Engineer 11.05.2024 compact it 383 (ET: N/A)]*


    Answer:

    Given: 192.168.5.154/27.

    Step 1, mask and block size:
    - /27 gives the mask 11111111.11111111.11111111.11100000 = 255.255.255.224.
    - Block size = 256 − 224 = 32, so blocks start at 0, 32, 64, 96, 128, 160, 192 and 224.

    Step 2, find the block containing 154:
    - 154 lies between 128 and 159, so the block is 192.168.5.128 to 192.168.5.159.

    Answers:
    - a) Network address: 192.168.5.128
    - b) First valid host: 192.168.5.129
    - c) Last valid host: 192.168.5.158
    - d) Broadcast address: 192.168.5.159
    - e) Subnet mask: 255.255.255.224, that is /27

    - Usable hosts = 32 − 2 = 30.
32. **Write down the Public and Private IPv4 address for Class A, Class B and Class C.** *[NSDA Assistant Maintenance Engineer 11.05.2024 compact it 384 (ET: N/A)]*


    Answer:

    Private IPv4 addresses, defined by RFC 1918:

    | Class | Private range | CIDR | Number of addresses |
    |---|---|---|---|
    | A | 10.0.0.0 to 10.255.255.255 | 10.0.0.0/8 | 16,777,216 |
    | B | 172.16.0.0 to 172.31.255.255 | 172.16.0.0/12 | 1,048,576 |
    | C | 192.168.0.0 to 192.168.255.255 | 192.168.0.0/16 | 65,536 |

    Public IPv4 address ranges, that is everything else in the class that is not private or reserved:

    | Class | Full range | Public portion |
    |---|---|---|
    | A | 1.0.0.0 to 126.255.255.255 | All of it except 10.0.0.0/8, and 127.0.0.0/8 which is loopback |
    | B | 128.0.0.0 to 191.255.255.255 | All of it except 172.16.0.0/12, and 169.254.0.0/16 which is APIPA |
    | C | 192.0.0.0 to 223.255.255.255 | All of it except 192.168.0.0/16 |

    Difference in short:
    - A public address is globally unique, allocated by IANA through the regional registries and the ISP, and is directly reachable from the Internet.
    - A private address may be reused inside any number of separate organisations, is never routed on the public Internet, and needs NAT to reach the outside.
33. **(b) What is a subnet? What benefits will you get using subnets for this office?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 324 (ET: BIBM)]*


    Answer:

    What a subnet is:
    - A subnet is a logical subdivision of a larger IP network, created by borrowing bits from the host part of the address and adding them to the network part. Each subnet behaves as an independent network with its own network address, broadcast address and range of hosts.

    Benefits of using subnets in an office:
    - Smaller broadcast domains: a broadcast from one department no longer reaches every machine in the building, so bandwidth and CPU are not wasted and broadcast storms are contained.
    - Better performance: less unnecessary traffic on each segment, and congestion in one department does not slow another.
    - Improved security and isolation: departments such as Finance and HR can be separated, and access between subnets can be controlled by ACLs on the router, because all inter-subnet traffic must pass through it.
    - Efficient use of address space: with VLSM each department receives only as many addresses as it needs, so a point to point link takes a /30 instead of a whole /24.
    - Easier management and troubleshooting: an IP address immediately tells you which department and which floor a machine belongs to, so a fault can be localised quickly.
    - Fault containment: a problem such as a loop or a rogue DHCP server affects only its own subnet.
    - Simpler policy: QoS, monitoring and firewall rules can be written per subnet rather than per host.
    - Scalability: new departments or floors are added as new subnets without redesigning the whole address plan.
    - Smaller routing tables, because contiguous subnets can be summarised into a single advertised prefix.
34. **Local loopback address কি? কোন কমান্ড ব্যবহার করে কানেক্টিভিটি টেস্ট করা হয়?** *[BTCL - JAM ( Technical) 05.04.2024 compact it 383 (ET: BUET)]*

    Answer:

    Local loopback address:
    - The loopback address is 127.0.0.1, and the whole block 127.0.0.0/8 is reserved for this purpose.
    - A packet sent to it never reaches the network card or the cable; the TCP/IP stack loops it straight back. It therefore tests the machine's own protocol stack rather than any external connectivity.
    - Its hostname is `localhost`, and the IPv6 equivalent is `::1`.
    - Uses: connecting to a server running on the same machine, for example `http://127.0.0.1:8080`, and connecting to a local database during development.

    Command used to test connectivity:
    - `ping 127.0.0.1` checks that the local TCP/IP stack is working.
    - `ping <gateway IP>` checks that the router is reachable.
    - `ping 8.8.8.8` checks that the Internet is reachable.
    - `ping www.google.com` checks that DNS resolution is working.
    - Related tools: `tracert` or `traceroute` shows the path, `ipconfig` or `ifconfig` shows the local address, `nslookup` tests DNS, and `netstat` lists active connections.
35. **Given IP address 192.168. 2.0/ 24; Determine to network address and broadcast address.** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 405 (ET: N/A)]*


    Answer:

    Given: 192.168.2.0/24.

    Step 1, mask and host bits:
    - /24 gives the mask 255.255.255.0, so the host bits are the whole last octet, 8 bits.

    Step 2, network and broadcast:
    - Network address, all host bits 0: 192.168.2.0
    - Broadcast address, all host bits 1: 192.168.2.255

    Final answer:
    - Network address: 192.168.2.0
    - Broadcast address: 192.168.2.255
    - Usable host range: 192.168.2.1 to 192.168.2.254, that is 2⁸ − 2 = 254 hosts.
36. **Given a (slash) /26 based network address. Find Subnet mask, broadcast address, number of host, Number of valid host and number of subnet.** *[BKSP Assistant Programmer 13.07.2024 compact it 1459 (ET: N/A)]*


    Answer: For a /26 network, taking a Class C block such as 192.168.1.0/24 as the parent.

    - Subnet mask: /26 = 11111111.11111111.11111111.11000000 = 255.255.255.192
    - Number of hosts, that is total addresses per subnet: host bits = 32 − 26 = 6, so 2⁶ = 64
    - Number of valid, that is usable, hosts: 64 − 2 = 62
    - Number of subnets: bits borrowed from the /24 default = 26 − 24 = 2, so 2² = 4 subnets
    - Block size = 256 − 192 = 64

    Broadcast address of each subnet:

    | Subnet | Network address | Usable range | Broadcast address |
    |---|---|---|---|
    | 1 | 192.168.1.0 | .1 to .62 | 192.168.1.63 |
    | 2 | 192.168.1.64 | .65 to .126 | 192.168.1.127 |
    | 3 | 192.168.1.128 | .129 to .190 | 192.168.1.191 |
    | 4 | 192.168.1.192 | .193 to .254 | 192.168.1.255 |

    - General rule: the broadcast address of any subnet is one less than the next subnet's network address, and the last address of the block.
37. **Write Class A private IP range.** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*


    Answer: The Class A private IP range is 10.0.0.0 to 10.255.255.255.

    - In CIDR notation: 10.0.0.0/8.
    - It contains 2²⁴ = 16,777,216 addresses, of which 16,777,214 are usable.
    - It is defined by RFC 1918 and is not routable on the public Internet, so NAT is needed for Internet access. Large organisations and cloud providers use it because it offers the biggest private address space.
38. **Write Command for check LAN connecte?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*


    Answer: Commands to check LAN connectivity:

    - `ping <IP address>` — the basic reachability test using ICMP Echo. For example `ping 192.168.1.1` to test the gateway, or `ping 127.0.0.1` to test the local TCP/IP stack.
    - `ipconfig` on Windows, or `ifconfig` and `ip addr` on Linux — shows the interface's IP address, mask and gateway. `ipconfig /all` also shows the MAC address, DHCP server and DNS servers.
    - `tracert` on Windows or `traceroute` on Linux — shows every hop along the path and where it stops.
    - `arp -a` — lists the IP to MAC mappings learned on the local segment, which confirms that layer 2 is working.
    - `netstat -an` — lists the active connections and listening ports.
    - `nslookup` or `dig` — confirms that name resolution is working, which separates a DNS fault from a connectivity fault.
    - `getmac` on Windows, and `ethtool eth0` on Linux — shows the physical address and the link status, that is whether the cable is actually connected.

    - Practical order of testing: first `ping 127.0.0.1` for the stack, then the own IP, then the default gateway, then a public IP such as 8.8.8.8, and finally a domain name. The step at which it fails tells you where the fault lies.
39. **(a) Given 4 Network interface in a table and find which of the following network is on which network.** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 433 (ET: BUET)]*


    Answer: Method for deciding which network a given interface belongs to.

    Procedure:
    - Take the interface's IP address and its subnet mask.
    - Convert both to binary, or use the block size shortcut: block size = 256 − the value of the interesting octet of the mask, that is the last octet that is not 255.
    - Perform a bitwise AND of the address with the mask; the result is the network address of that interface.
    - Two interfaces are on the same network if and only if they produce the same network address with the same mask.

    Worked example:

    | Interface | IP address | Mask | Network address | Broadcast |
    |---|---|---|---|---|
    | 1 | 192.168.1.10 | 255.255.255.0, /24 | 192.168.1.0 | 192.168.1.255 |
    | 2 | 192.168.1.130 | 255.255.255.128, /25 | 192.168.1.128 | 192.168.1.255 |
    | 3 | 172.16.5.30 | 255.255.0.0, /16 | 172.16.0.0 | 172.16.255.255 |
    | 4 | 10.1.2.3 | 255.255.255.252, /30 | 10.1.2.0 | 10.1.2.3 |

    - The point the examiner is checking: the same IP address can belong to different networks depending on the mask, so the mask must always be applied before any conclusion is drawn. Interfaces 1 and 2 look alike but are on different networks, because the /25 mask splits the block at .128. <!-- verify -->
40. **(খ) Classful এবং Classless IP address এর পার্থক্য কী? নিচের IP গুলোর Class নির্ণয় করুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

    Answer:

    Difference between classful and classless IP addressing:

    | Point | Classful | Classless, that is CIDR |
    |---|---|---|
    | Division | Fixed Class A, B, C, D and E | No classes at all |
    | Mask | A fixed default mask, /8, /16 or /24 | Any prefix from /1 to /32 |
    | Notation | The IP address alone | The IP address written with a /n prefix |
    | Address waste | Very high, since only three sizes exist | Very low, since a block of the required size is given |
    | VLSM | Not supported | Supported, so different subnet sizes may be used in one network |
    | Route summarisation | Not possible | Possible, so routing tables stay small |
    | Routing protocols | RIPv1, IGRP | RIPv2, OSPF, EIGRP, BGP |
    | Status | Obsolete, replaced in 1993 | The system in use today |

    Class of the given IP addresses:

    (i) 00000001 00001011 00001011 11101111
    - First octet 00000001 = 1
    - Second octet 00001011 = 11, third octet 00001011 = 11, fourth octet 11101111 = 239
    - In dotted decimal the address is 1.11.11.239
    - The first octet 1 lies between 1 and 126, and in binary it begins with 0.
    - Answer: Class A

    (ii) 211.10.15.4
    - The first octet 211 lies between 192 and 223.
    - Answer: Class C
41. **6.10 An organization is granted the IPv4 network block 14.24.74.0/24 and needs to segment it into two subnets: Subnet A (requires 120 addresses) and Subnet B (requires 60 addresses). Allocating sequentially from the requirement first to maximize remaining address space, state only the Network Address (with its CIDR mask) and the Broadcast Address for both subnets.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*


    Answer:

    Step 1, size each subnet:
    - Subnet A needs 120 addresses. 2⁷ = 128, and 128 − 2 = 126 ≥ 120, so 7 host bits are needed, giving a /25.
    - Subnet B needs 60 addresses. 2⁶ = 64, and 64 − 2 = 62 ≥ 60, so 6 host bits are needed, giving a /26.

    Step 2, allocate sequentially from 14.24.74.0, largest first:

    | Subnet | Network address with mask | Broadcast address |
    |---|---|---|
    | A | 14.24.74.0/25 | 14.24.74.127 |
    | B | 14.24.74.128/26 | 14.24.74.191 |

    Final answer:
    - Subnet A: network 14.24.74.0/25, broadcast 14.24.74.127
    - Subnet B: network 14.24.74.128/26, broadcast 14.24.74.191

    - Address space remaining: 14.24.74.192/26, that is 64 addresses, kept free for future growth, which is why the larger block is allocated first.
42. **An IP address subnet mask is 255.255.255.224 which is the subnet address in this block?** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*


    Answer:

    Given: subnet mask 255.255.255.224, which is a /27.

    Step 1, block size:
    - Block size = 256 − 224 = 32.

    Step 2, the possible subnet addresses in the last octet:
    - They are the multiples of 32: 0, 32, 64, 96, 128, 160, 192 and 224.
    - So for a network such as 192.168.1.0/24 the subnet addresses are 192.168.1.0, .32, .64, .96, .128, .160, .192 and .224.

    How to decide for any given host address:
    - Divide the last octet by 32 and take the whole number part, then multiply by 32. For example 192.168.1.100: 100 ÷ 32 = 3 remainder 4, and 3 × 32 = 96, so the subnet address is 192.168.1.96 and the broadcast address is 192.168.1.127.

    Final answer: the subnet address is always the largest multiple of 32 that is less than or equal to the host's last octet, and there are 8 such subnets, each with 32 addresses and 30 usable hosts.
43. **Write down the basic differences of the following:**
   **(i) Public vs Private IP address** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 534 (ET: MIST)]*


    Answer:

    Public vs Private IP address:

    | Point | Public IP address | Private IP address |
    |---|---|---|
    | Uniqueness | Globally unique on the whole Internet | Unique only within its own private network |
    | Assigned by | IANA through the regional registries and the ISP | The local network administrator or the local DHCP server |
    | Routable on the Internet | Yes, directly reachable | No, routers on the Internet discard it |
    | Ranges | Everything not reserved | 10.0.0.0/8, 172.16.0.0/12 and 192.168.0.0/16 |
    | Cost | Has to be bought or rented from the ISP | Free, and reusable by anyone |
    | Security | Directly exposed, so it needs a firewall | Hidden behind NAT, which gives some protection |
    | Reuse | Cannot be reused anywhere else | The same range is used in millions of homes and offices |
    | Needs NAT | No | Yes, to reach the Internet |
    | Typical use | Web servers, mail servers, the WAN interface of a router | PCs, printers and phones inside a LAN |
44. **What do you mean by Subnet and Subnet Mask? The network address of 172.16.0.0/19 provides how many subnets and hosts? What is the function of OSPF?** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 536 (ET: MIST)]*


    Answer:

    Subnet and subnet mask:
    - A subnet is a logical subdivision of a larger IP network, created by borrowing bits from the host part and adding them to the network part, so that one network becomes several smaller independent networks.
    - A subnet mask is a 32 bit value in which the network bits are 1 and the host bits are 0. A host ANDs an address with the mask to find its network address, and that is how it decides whether a destination is local or must go through the gateway.

    172.16.0.0/19, subnets and hosts:
    - 172.16.x.x has the first octet 172, so it is a Class B address with a default prefix of /16.
    - Bits borrowed = 19 − 16 = 3, so the number of subnets = 2³ = 8.
    - Host bits = 32 − 19 = 13, so addresses per subnet = 2¹³ = 8192 and usable hosts = 8192 − 2 = 8190.
    - Mask = 255.255.224.0, block size in the third octet = 256 − 224 = 32, so the subnets are 172.16.0.0, 172.16.32.0, 172.16.64.0, 172.16.96.0, 172.16.128.0, 172.16.160.0, 172.16.192.0 and 172.16.224.0.

    Final answer: 8 subnets, each with 8190 usable hosts.

    Function of OSPF:
    - OSPF, Open Shortest Path First, is a link state interior gateway protocol that determines the best routes within an autonomous system.
    - Every router floods its link state information to all routers in the area, so all of them build an identical topology database, and each then runs Dijkstra's shortest path first algorithm with itself as the root.
    - Its metric is cost, derived from bandwidth. It converges fast, is loop free, supports VLSM and CIDR, has no hop count limit, allows equal cost load balancing and authentication, and divides large networks into areas around a backbone Area 0 to limit flooding. Its administrative distance is 110.
45. **Convert the decimal IP address 192.168.101.5 into binary IP address. Fill-up the following in tabular form:** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 539 (ET: MIST)]*
| Address Class | First Octet Decimal Range | Example of IP Address (IPA) | Network ID of IPA | Host ID of IPA |
|---|---|---|---|---|
| Class A |  |  |  |  |
| Class B |  |  |  |  |
| Class C |  |  |  |  |


    Answer:

    Conversion of 192.168.101.5 to binary:
    - 192 = 11000000
    - 168 = 10101000
    - 101 = 01100101
    - 5 = 00000101
    - Full binary: 11000000.10101000.01100101.00000101

    Address class table:

    | Address Class | First Octet Decimal Range | Example of IP Address | Network ID of the example | Host ID of the example |
    |---|---|---|---|---|
    | Class A | 1 to 126 | 10.25.30.40 | 10 | 25.30.40 |
    | Class B | 128 to 191 | 172.16.50.60 | 172.16 | 50.60 |
    | Class C | 192 to 223 | 192.168.101.5 | 192.168.101 | 5 |

    - Class A uses the first octet as the network ID and the remaining three as the host ID, with a default mask of 255.0.0.0.
    - Class B uses the first two octets as the network ID, with a default mask of 255.255.0.0.
    - Class C uses the first three octets as the network ID, with a default mask of 255.255.255.0.
    - The first octet 127 is skipped because it is reserved for loopback, Class D from 224 to 239 is multicast, and Class E from 240 to 255 is reserved.
46. **What is IP address? Explain the necessity of IP address in network?** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 564 (ET: N/A)]*


    Answer:

    What an IP address is:
    - An IP address is a logical network layer address that uniquely identifies a device on a network and allows data to be routed to it across the Internet.
    - IPv4 is 32 bits, written as four decimal octets such as 192.168.1.10; IPv6 is 128 bits, written in hexadecimal such as 2001:db8::1.
    - It is divided by the subnet mask into a network part, which says which network the device is on, and a host part, which says which device it is on that network.
    - It may be public or private, and static or dynamically assigned by DHCP.

    Necessity of an IP address in a network:
    - Identification: every device needs a unique identifier, otherwise the network cannot tell one machine from another.
    - Location and routing: because the address is hierarchical, a router can tell from the network part which direction to send the packet, without knowing anything about the individual host. A flat address such as a MAC address could never be routed globally, since the routing table would need an entry for every device on earth.
    - End to end delivery: the source and destination IP addresses stay unchanged for the whole journey, so the packet can be delivered and the reply returned across any number of intermediate networks and technologies.
    - Technology independence: Ethernet, Wi-Fi, fibre and satellite all use different framing, but IP provides one common addressing scheme above them, which is what makes internetworking possible.
    - Network management: subnetting, access control lists, firewall rules, QoS and monitoring are all written in terms of IP addresses and ranges.
    - Service association: together with the port number the IP address forms a socket, which identifies not just the machine but the exact process the data is for.
    - Practical services depend on it: DNS exists to translate names into IP addresses, DHCP exists to hand them out, and NAT exists to share them.
47. **What is subnet mask? Why it is used?** *[Mongla Port Authority Assistant Programmer 2023 compact it 573 (ET: N/A)]*


    Answer:

    What a subnet mask is:
    - A subnet mask is a 32 bit number used with an IP address to separate the network part from the host part. In the mask every network bit is 1 and every host bit is 0, and the 1s must run together from the left with no gap.
    - CIDR notation is the short way of writing it. /24 means the first 24 bits are the network part.

    The two formulas we always use:
    - Number of subnets = 2^(number of borrowed bits)
    - Usable hosts per subnet = 2^(remaining host bits) − 2

    We subtract 2 because the first address of a subnet is the network ID and the last one is the broadcast address. Neither can be given to a device.

    Why we subnet at all:
    - Efficient use of IP addresses. Each department gets only as many addresses as it needs.
    - Better performance. Broadcast traffic stays inside one department instead of flooding the whole network.
    - Better security. Each department is logically separated from the others.
    - Easier management. Small networks are easier to run than one huge one.
    - It is written in dotted decimal, such as 255.255.255.0, or as a CIDR prefix, such as /24.

    Why it is used:
    - To identify the network address: the host performs a bitwise AND of the IP address and the mask, and the result is the network address.
    - To make the local or remote decision: for every outgoing packet, the host ANDs its own address and the destination address with the mask. If the two results are the same the destination is on the same network and the frame is sent directly using ARP; if they differ, the packet is sent to the default gateway. This single decision is made for every packet a host sends.
    - To perform subnetting: by lengthening the mask, bits are borrowed from the host part, dividing one network into several smaller ones, which reduces broadcast domains and improves security and performance.
    - To determine the number of hosts: host bits h = 32 − prefix, so each subnet has 2ʰ addresses and 2ʰ − 2 usable hosts.
    - To find the broadcast address, which is the address with all host bits set to 1.
    - For routing: routers use the mask in the longest prefix match to choose the most specific route to a destination.
    - For efficient allocation: with VLSM, different masks can be used in different parts of one network, so a point to point link takes a /30 rather than a whole /24.

    Example: 192.168.1.10 with mask 255.255.255.0 gives the network 192.168.1.0, the broadcast 192.168.1.255 and 254 usable hosts.
48. **In HR department have 12 IP enable devices are available in our office and have a big IP block 172.16.5.0/24. To consider your HR department find a suitable IP block than also answer the following question.**
   **i. Subnet mask; ii. Number of usable IP address; iii. First and last IP Address of that block iv. Broadcast IP address** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 596 (ET: N/A)]*


    Answer:

    Step 1, choose a suitable block for 12 devices:
    - Requirement is 12 hosts, and a gateway address is also needed, so at least 13 usable addresses.
    - 2⁴ − 2 = 14 ≥ 13, so 4 host bits are enough and the prefix is /28.
    - Taking the first block of 172.16.5.0/24, the suitable IP block is 172.16.5.0/28.

    Answers:
    - i. Subnet mask: 255.255.255.240, that is /28
    - ii. Number of usable IP addresses: 2⁴ − 2 = 14
    - iii. First IP address: 172.16.5.1, and last IP address: 172.16.5.14
    - iv. Broadcast IP address: 172.16.5.15

    - Block size = 256 − 240 = 16, so the block runs from 172.16.5.0 to 172.16.5.15.
    - Choosing a /28 rather than the whole /24 leaves 172.16.5.16 to 172.16.5.255, that is 240 addresses, free for the other departments, which is exactly the point of subnetting.
    - A /29 with only 6 usable addresses would be too small, and a /27 with 30 would waste more than half.
49. **What is private IP range class A, B and C with maximum host of each class?** *[BREB Assistant Programmer 18.02.2023 compact it 470 (ET: N/A)]*


    Answer:

    Private IP ranges with the maximum hosts of each class:

    | Class | Private range | CIDR | Addresses | Maximum hosts in one default network of that class |
    |---|---|---|---|---|
    | A | 10.0.0.0 to 10.255.255.255 | 10.0.0.0/8 | 16,777,216 | 16,777,214, that is 2²⁴ − 2 |
    | B | 172.16.0.0 to 172.31.255.255 | 172.16.0.0/12 | 1,048,576 | 65,534, that is 2¹⁶ − 2 |
    | C | 192.168.0.0 to 192.168.255.255 | 192.168.0.0/16 | 65,536 | 254, that is 2⁸ − 2 |

    - The Class A private space is a single network of 16.7 million addresses.
    - The Class B private space is 16 contiguous Class B networks, 172.16 through 172.31, each holding 65,534 hosts.
    - The Class C private space is 256 contiguous Class C networks, 192.168.0 through 192.168.255, each holding 254 hosts.
    - Two addresses are always subtracted from each network: the network address and the broadcast address.
50. **(b) Find out the default mask, network address and broadcast address of the classful IPv4 address: 172.16.99.45** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 480 (ET: N/A)]*


    Answer:

    Given: 172.16.99.45, treated as a classful address.

    Step 1, identify the class:
    - The first octet is 172, which lies between 128 and 191, so this is a Class B address.

    Step 2, default mask:
    - Class B default mask = 255.255.0.0, that is /16.

    Step 3, network address, by ANDing with the mask:
    - 172 AND 255 = 172, 16 AND 255 = 16, 99 AND 0 = 0, 45 AND 0 = 0
    - Network address = 172.16.0.0

    Step 4, broadcast address, that is all host bits set to 1:
    - Broadcast address = 172.16.255.255

    Final answer:
    - Default mask: 255.255.0.0
    - Network address: 172.16.0.0
    - Broadcast address: 172.16.255.255
    - Usable host range: 172.16.0.1 to 172.16.255.254, that is 65,534 hosts.

    - Note: 172.16.0.0/12 is a private range, so this address is not routable on the public Internet.
51. **Identify the class, network IP address, direct broadcast address and limited broadcast address of the following IP address: (i) 1.2.3.4 (ii) 130.1.2.3 (iii) 220.15.1.10 (iv) 200.1.10.100** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 637 (ET: N/A)]*


    Answer:

    | IP address | Class | Network address | Direct broadcast address | Limited broadcast address |
    |---|---|---|---|---|
    | 1.2.3.4 | A, first octet 1 is in 1 to 126 | 1.0.0.0 | 1.255.255.255 | 255.255.255.255 |
    | 130.1.2.3 | B, first octet 130 is in 128 to 191 | 130.1.0.0 | 130.1.255.255 | 255.255.255.255 |
    | 220.15.1.10 | C, first octet 220 is in 192 to 223 | 220.15.1.0 | 220.15.1.255 | 255.255.255.255 |
    | 200.1.10.100 | C, first octet 200 is in 192 to 223 | 200.1.10.0 | 200.1.10.255 | 255.255.255.255 |

    Method:
    - The class is read from the first octet, which fixes the default mask: /8 for A, /16 for B and /24 for C.
    - The network address is found by setting all the host bits to 0.
    - The direct broadcast address is found by setting all the host bits to 1. It is routable, so a host on another network can address it, and it reaches every host on the target network.
    - The limited broadcast address is always 255.255.255.255. It is never forwarded by a router, so it stays within the local segment; DHCPDISCOVER uses it because the sender has no address or network information yet.
52. **What is the subnet mask in 10.2.1.3/22 network?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 637 (ET: N/A)]*


    Answer:

    Given: 10.2.1.3/22.

    Step 1, write the mask in binary:
    - /22 means the first 22 bits are 1: 11111111.11111111.11111100.00000000

    Step 2, convert each octet to decimal:
    - 11111111 = 255
    - 11111111 = 255
    - 11111100 = 128 + 64 + 32 + 16 + 8 + 4 = 252
    - 00000000 = 0

    Final answer: the subnet mask is 255.255.252.0.

    - Supporting values: block size in the third octet = 256 − 252 = 4, so the network is 10.2.0.0/22, the broadcast is 10.2.3.255, the usable range is 10.2.0.1 to 10.2.3.254, and there are 2¹⁰ − 2 = 1022 usable hosts.
53. **In IPv4 show the network address and host address range of class A, B and C.** *[NSDA Assistant Programmer Date: 04-03-2022 compact it 656 (ET: N/A)]*


    Answer: Network address and host address ranges of the IPv4 classes:

    | Class | First octet range | Address range | Default mask | Network / Host bits | Networks | Hosts per network |
    |---|---|---|---|---|---|---|
    | A | 1 to 126 | 1.0.0.0 to 126.255.255.255 | 255.0.0.0, /8 | 8 / 24 | 126 | 16,777,214 |
    | B | 128 to 191 | 128.0.0.0 to 191.255.255.255 | 255.255.0.0, /16 | 16 / 16 | 16,384 | 65,534 |
    | C | 192 to 223 | 192.0.0.0 to 223.255.255.255 | 255.255.255.0, /24 | 24 / 8 | 2,097,152 | 254 |

    - 127.0.0.0/8 is reserved for loopback, Class D from 224 to 239 is multicast, and Class E from 240 to 255 is reserved.

    Structure of each class:
    - Class A: the first octet is the network ID and the last three octets are the host ID. Example, 10.0.0.0 is the network and 10.0.0.1 to 10.255.255.254 are the hosts.
    - Class B: the first two octets are the network ID and the last two are the host ID. Example, 172.16.0.0 is the network and 172.16.0.1 to 172.16.255.254 are the hosts.
    - Class C: the first three octets are the network ID and the last octet is the host ID. Example, 192.168.1.0 is the network and 192.168.1.1 to 192.168.1.254 are the hosts.
    - In each case the all zeros host address is the network address and the all ones host address is the broadcast address, which is why 2 is subtracted from the host count.
54. **Given IP Address: 192.168.5.154/26, Calculate network address and subnet mask.** *[NSDA Assistant Programmer Date: 04-03-2022 compact it 657 (ET: N/A)]*


    Answer:

    Given: 192.168.5.154/26.

    Step 1, subnet mask:
    - /26 in binary is 11111111.11111111.11111111.11000000
    - The last octet 11000000 = 128 + 64 = 192
    - Subnet mask = 255.255.255.192

    Step 2, block size:
    - Block size = 256 − 192 = 64, so blocks in the last octet begin at 0, 64, 128 and 192.

    Step 3, network address:
    - 154 lies between 128 and 191, so the network address is 192.168.5.128.
    - Check by ANDing: 154 = 10011010, mask 192 = 11000000, AND = 10000000 = 128.

    Final answer:
    - Network address: 192.168.5.128
    - Subnet mask: 255.255.255.192, that is /26

    - Supporting values: broadcast 192.168.5.191, usable range 192.168.5.129 to 192.168.5.190, and 62 usable hosts.
55. **Mention the maximum number of networks and hosts used in Class A, B and C networks.** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 659 (ET: N/A)]*


    Answer: Maximum number of networks and hosts in each class:

    | Class | Network bits | Host bits | Maximum networks | Maximum hosts per network |
    |---|---|---|---|---|
    | A | 8, of which 7 are usable | 24 | 2⁷ − 2 = 126 | 2²⁴ − 2 = 16,777,214 |
    | B | 16, of which 14 are usable | 16 | 2¹⁴ = 16,384 | 2¹⁶ − 2 = 65,534 |
    | C | 24, of which 21 are usable | 8 | 2²¹ = 2,097,152 | 2⁸ − 2 = 254 |

    Explanation of the arithmetic:
    - Class A begins with the bit 0, so only 7 of the 8 network bits are free. Networks 0 and 127 are excluded, giving 126.
    - Class B begins with 10, so 14 of the 16 network bits are free, giving 16,384 networks.
    - Class C begins with 110, so 21 of the 24 network bits are free, giving 2,097,152 networks.
    - In every class 2 is subtracted from the host count, for the network address and the broadcast address.
56. **Which subnet mask would be appropriate for address range to submit for up to LANs, with each LAN contains 5 to 26 hosts?** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 659 (ET: N/A)]*


    Answer:

    Given: each LAN must support 5 to 26 hosts, so the largest requirement is 26 hosts.

    Step 1, find the host bits needed:
    - 2ʰ − 2 ≥ 26
    - h = 4 gives 2⁴ − 2 = 14, which is not enough.
    - h = 5 gives 2⁵ − 2 = 30, which is enough.

    Step 2, find the prefix and mask:
    - Prefix = 32 − 5 = /27
    - Mask in binary: 11111111.11111111.11111111.11100000
    - Mask in decimal: 255.255.255.224

    Final answer: the appropriate subnet mask is 255.255.255.224, that is /27, giving 30 usable hosts per LAN.

    - From a Class C /24 this gives 2³ = 8 such LANs, with block size 32, starting at .0, .32, .64, .96, .128, .160, .192 and .224.
    - A /28 with only 14 hosts would be too small for a LAN of 26, and a /26 with 62 hosts would waste more than half of every block.
57. **Given IP Address: 192.168.19.24/29, find out the following IP Class & type, Number of Host, Network address, Broadcast address, Wildcard, and Subnet mask.** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 659 (ET: N/A)]*


    Answer:

    Given: 192.168.19.24/29.

    IP class and type:
    - The first octet is 192, which lies between 192 and 223, so it is a Class C address.
    - It falls in 192.168.0.0/16, so it is a private address, and it is a unicast address.

    Number of hosts:
    - Host bits = 32 − 29 = 3, so 2³ = 8 total addresses and 8 − 2 = 6 usable hosts.

    Network address:
    - Block size = 256 − 248 = 8, so blocks start at 0, 8, 16, 24, 32 and so on.
    - 24 is itself a block boundary, so the network address is 192.168.19.24.

    Broadcast address:
    - Last address of the block = 192.168.19.24 + 7 = 192.168.19.31.

    Wildcard mask:
    - The wildcard is the inverse of the subnet mask: 255.255.255.255 − 255.255.255.248 = 0.0.0.7.

    Subnet mask:
    - /29 = 11111111.11111111.11111111.11111000 = 255.255.255.248.

    Summary:

    | Item | Value |
    |---|---|
    | Class and type | Class C, private, unicast |
    | Number of usable hosts | 6 |
    | Network address | 192.168.19.24 |
    | Broadcast address | 192.168.19.31 |
    | Usable range | 192.168.19.25 to 192.168.19.30 |
    | Wildcard mask | 0.0.0.7 |
    | Subnet mask | 255.255.255.248 |
58. **Find network address, subnet mask, broadcast address and IP host range of 192.168.100.128/26** *[GTCL Assistant Engineer (CSE) 2022 compact it 685 (ET: BUET)]*


    Answer:

    Given: 192.168.100.128/26.

    Step 1, subnet mask:
    - /26 = 11111111.11111111.11111111.11000000 = 255.255.255.192

    Step 2, block size and boundaries:
    - Block size = 256 − 192 = 64, so blocks start at 0, 64, 128 and 192.
    - 128 is a block boundary, so this is already a network address.

    Answers:
    - Network address: 192.168.100.128
    - Subnet mask: 255.255.255.192, that is /26
    - Broadcast address: 192.168.100.128 + 63 = 192.168.100.191
    - IP host range: 192.168.100.129 to 192.168.100.190
    - Usable hosts: 2⁶ − 2 = 62
59. **What is the range of IPv4 address class A, B and C?** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 699 (ET: BUET)]*


    Answer: The ranges of the IPv4 address classes:

    | Class | First octet range | Address range | Default mask | Network / Host bits | Networks | Hosts per network |
    |---|---|---|---|---|---|---|
    | A | 1 to 126 | 1.0.0.0 to 126.255.255.255 | 255.0.0.0, /8 | 8 / 24 | 126 | 16,777,214 |
    | B | 128 to 191 | 128.0.0.0 to 191.255.255.255 | 255.255.0.0, /16 | 16 / 16 | 16,384 | 65,534 |
    | C | 192 to 223 | 192.0.0.0 to 223.255.255.255 | 255.255.255.0, /24 | 24 / 8 | 2,097,152 | 254 |

    - 127.0.0.0/8 is reserved for loopback, Class D from 224 to 239 is multicast, and Class E from 240 to 255 is reserved.

    - How the class is recognised from the leading bits: Class A begins with 0, Class B with 10, Class C with 110, Class D with 1110 and Class E with 1111.
    - Class D, 224.0.0.0 to 239.255.255.255, is used for multicast, and Class E, 240.0.0.0 to 255.255.255.255, is reserved for research.
60. **What is subnet mask? Given IP address 192.168.0.0/29 find 10^{\text{th}} and 22^{\text{th}} subnet first host address and last host address.** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 701 (ET: BUET)]*


    Answer:

    What a subnet mask is:
    - A subnet mask is a 32 bit value in which the network bits are 1 and the host bits are 0. A host ANDs an IP address with the mask to obtain the network address, which is how it decides whether a destination is on its own network or must be sent to the default gateway. It also determines how many hosts a subnet can hold and where the broadcast address lies.

    Given: 192.168.0.0/29, taking the parent block as 192.168.0.0/24.

    Step 1, block size and mask:
    - /29 gives host bits = 3, so 2³ = 8 addresses per subnet and 6 usable hosts.
    - Mask = 255.255.255.248, block size = 256 − 248 = 8.
    - Number of subnets from a /24 = 2^(29 − 24) = 2⁵ = 32.

    Step 2, find the nth subnet:
    - The nth subnet starts at (n − 1) × 8 in the last octet.

    10th subnet:
    - Start = (10 − 1) × 8 = 72, so the network address is 192.168.0.72.
    - First host address: 192.168.0.73
    - Last host address: 192.168.0.78
    - Broadcast address: 192.168.0.79

    22nd subnet:
    - Start = (22 − 1) × 8 = 168, so the network address is 192.168.0.168.
    - First host address: 192.168.0.169
    - Last host address: 192.168.0.174
    - Broadcast address: 192.168.0.175

    Final answer: the 10th subnet has hosts 192.168.0.73 to 192.168.0.78, and the 22nd subnet has hosts 192.168.0.169 to 192.168.0.174.
61. **How many bits need to identify an IP address in IPv4?** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*


    Answer: An IPv4 address needs 32 bits.

    - It is written as four octets of 8 bits each, separated by dots, for example 192.168.1.10, where each octet ranges from 0 to 255.
    - The total address space is 2³² = 4,294,967,296 addresses, about 4.3 billion, which is why IPv4 exhaustion became a problem.
    - IPv6 by comparison uses 128 bits, giving about 3.4 × 10³⁸ addresses.
62. **What is default subnet mask?** *[BARC Data Entry Officer 10.09.2022 compact it 702 (ET: N/A)]*


    Answer: A default subnet mask is the standard mask that belongs to an address class before any subnetting is done. It marks exactly the bits that the class definition treats as the network part.

    | Class | Default subnet mask | CIDR | Network bits |
    |---|---|---|---|
    | A | 255.0.0.0 | /8 | 8 |
    | B | 255.255.0.0 | /16 | 16 |
    | C | 255.255.255.0 | /24 | 24 |

    - Class D and E have no default mask, since they are used for multicast and for reserved purposes.
    - When bits are borrowed from the host part to create subnets, the resulting mask is called a custom or subnet mask and it is always longer than the default. For example, subnetting a Class C with 2 borrowed bits gives 255.255.255.192, that is /26.
63. **Given IP: 168.20.96.63, Subnet mask: 255.255.192.0 Find network address, broadcast address and number of host.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 712 (ET: BUET)]*


    Answer:

    Given: IP 168.20.96.63, subnet mask 255.255.192.0, which is a /18.

    Step 1, block size:
    - The interesting octet is the third, so block size = 256 − 192 = 64.
    - Blocks in the third octet begin at 0, 64, 128 and 192.

    Step 2, find the block containing 96:
    - 96 lies between 64 and 127, so the block is 168.20.64.0 to 168.20.127.255.

    Answers:
    - Network address: 168.20.64.0
    - Broadcast address: 168.20.127.255
    - Number of usable hosts: host bits = 32 − 18 = 14, so 2¹⁴ − 2 = 16,382
    - Usable host range: 168.20.64.1 to 168.20.127.254

    - Check by ANDing the third octet: 96 = 01100000, mask 192 = 11000000, AND = 01000000 = 64, which confirms the network address.
64. **An IP address is: 172.162.100.25/27, Find out the following: (a) Network Address (b) IP class (c) Subnet mask (d) Broadcast address (e) Hosts per subnet** *[IDRA Assistant Network Administrator 2022 compact it 727 (ET: N/A)]*


    Answer:

    Given: 172.162.100.25/27.

    (a) Network address:
    - Block size = 256 − 224 = 32, so blocks in the last octet start at 0, 32, 64, 96 and so on.
    - 25 lies between 0 and 31, so the network address is 172.162.100.0.

    (b) IP class:
    - The first octet is 172, which lies between 128 and 191, so it is a Class B address. Note that only 172.16 to 172.31 is private, so 172.162 is a public Class B address.

    (c) Subnet mask:
    - /27 = 11111111.11111111.11111111.11100000 = 255.255.255.224.

    (d) Broadcast address:
    - Last address of the block = 172.162.100.0 + 31 = 172.162.100.31.

    (e) Hosts per subnet:
    - Host bits = 32 − 27 = 5, so 2⁵ − 2 = 30 usable hosts.
    - Usable range: 172.162.100.1 to 172.162.100.30.
65. **What is Public and Private IP?** *[IDRA Assistant Network Administrator 2022 compact it 728 (ET: N/A)]*


    Answer:

    Public IP address:
    - A globally unique address allocated by IANA through the regional registries and the ISP, which is directly routable and reachable on the Internet.
    - It cannot be reused anywhere else in the world, it has to be bought or rented, and it is directly exposed, so it needs firewall protection.
    - Used by web servers, mail servers and the WAN interface of a router.

    Private IP address:
    - An address from the ranges reserved by RFC 1918, used inside a private network. It is unique only within that network, and the same range may be reused in millions of other networks.
    - Ranges: 10.0.0.0/8, 172.16.0.0/12 and 192.168.0.0/16.
    - Routers on the Internet discard packets carrying a private source or destination address, so NAT is required at the network edge to reach the outside.
    - It is free, conserves the scarce public address space, and gives some security because internal hosts are not directly reachable from outside.
    - Used by PCs, printers and phones inside a home or office LAN.

    - Practical picture: a home has one public address on its router's WAN side, and every device inside uses a private 192.168.x.x address; NAT translates between the two.
66. **A network IP address is 172.16.236.92/27. Find out the: (a) Subnet mask (b) Network Address (c) Broadcast Address** *[NWPGCL Junior Assistant Manager (IT) 2022 compact it 731 (ET: N/A)]*


    Answer:

    Given: 172.16.236.92/27.

    (a) Subnet mask:
    - /27 = 11111111.11111111.11111111.11100000 = 255.255.255.224.

    (b) Network address:
    - Block size = 256 − 224 = 32, so blocks start at 0, 32, 64, 96, 128 and so on.
    - 92 lies between 64 and 95, so the network address is 172.16.236.64.
    - Check: 92 = 01011100, mask 224 = 11100000, AND = 01000000 = 64.

    (c) Broadcast address:
    - Last address of the block = 172.16.236.64 + 31 = 172.16.236.95.

    - Usable range: 172.16.236.65 to 172.16.236.94, that is 2⁵ − 2 = 30 hosts.
67. **Given IP address 172.3.16.156/23 and find out the following answer: (i) Network address (ii) Subnet mask (iii) Number of host** *[BOF Assistant Programmer 2022 compact it 733 (ET: MIST)]*


    Answer:

    Given: 172.3.16.156/23.

    (i) Network address:
    - The interesting octet is the third, and block size = 256 − 254 = 2, so blocks begin at even third octets: 0, 2, 4, ... 16, 18.
    - 16 is even, so the block starts at 172.3.16.0 and the network address is 172.3.16.0.

    (ii) Subnet mask:
    - /23 = 11111111.11111111.11111110.00000000 = 255.255.254.0.

    (iii) Number of hosts:
    - Host bits = 32 − 23 = 9, so 2⁹ = 512 addresses and 512 − 2 = 510 usable hosts.

    - Supporting values: broadcast address 172.3.17.255, and usable range 172.3.16.1 to 172.3.17.254.
68. **Answer the following: (i) 192.168.10.0/23, How many usable address? (ii) 192.168.10.0/23, Find subnet mask. (iii) 192.168.10.0/23, Find Broadcast Address. (iv) 192.168.10.0/23, What is last usable host?** *[BTCL Assistant Manager (Technical) 2021 compact it 764 (ET: BUET)]*


    Answer: Given 192.168.10.0/23. Block size in the third octet = 256 − 254 = 2, so the block covers 192.168.10.x and 192.168.11.x.

    (i) How many usable addresses:
    - Host bits = 32 − 23 = 9, so 2⁹ = 512 total and 512 − 2 = 510 usable.

    (ii) Subnet mask:
    - /23 = 255.255.254.0.

    (iii) Broadcast address:
    - The last address of the block = 192.168.11.255.

    (iv) Last usable host:
    - One below the broadcast address = 192.168.11.254.

    - The first usable host is 192.168.10.1, and the network address is 192.168.10.0.
69. **(ii) CIDR কী? 192.168.100.9/26 IP address থেকে (a) Total subnets (b) Block size (c) Valid Hosts (d) Total hosts বের করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 788 (ET: N/A)]*

    Answer:

    What CIDR is:
    - CIDR stands for Classless Inter-Domain Routing, introduced in 1993 by RFC 1519. Instead of the fixed Classes A, B and C, the prefix length is written explicitly with the address, for example 192.168.100.9/26.
    - Its benefits: a block of exactly the required size can be allocated, so waste falls sharply; VLSM allows subnets of different sizes inside one network; and contiguous networks can be summarised into a single prefix, which keeps the global routing table manageable.

    From the address 192.168.100.9/26:

    (a) Total subnets:
    - The default prefix of a Class C address is /24, so the bits borrowed are 26 − 24 = 2, and the number of subnets is 2² = 4.

    (b) Block size:
    - The mask is 255.255.255.192, so the block size is 256 − 192 = 64.

    (c) Valid hosts:
    - Host bits = 32 − 26 = 6, so valid hosts = 2⁶ − 2 = 62.

    (d) Total hosts:
    - Total addresses per subnet = 2⁶ = 64.

    The subnet this address belongs to:
    - 9 lies between 0 and 63, so the network address is 192.168.100.0, the broadcast address is 192.168.100.63, and the host range is 192.168.100.1 to 192.168.100.62.
70. **(a) What is the usable number of host IP addresses available on a network that has a /26 mask? Write down the subset mask of this network. Write down the first and the last IP address that can be assigned to host PCs if the network address is 192.168.30.128/26. What address should be used for broadcast purpose in this Network?** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 801-802 (ET: N/A)]*


    Answer:

    Usable host addresses on a /26 network:
    - Host bits = 32 − 26 = 6, so 2⁶ = 64 total addresses and 64 − 2 = 62 usable hosts.

    Subnet mask of this network:
    - /26 = 11111111.11111111.11111111.11000000 = 255.255.255.192.

    For the network 192.168.30.128/26:
    - Block size = 256 − 192 = 64, so the block runs from 192.168.30.128 to 192.168.30.191.
    - First IP address that can be assigned to a host: 192.168.30.129
    - Last IP address that can be assigned to a host: 192.168.30.190

    Broadcast address for this network:
    - 192.168.30.191, which is the last address of the block.

    - In practice one of the usable addresses, usually the first or the last, is given to the router interface as the default gateway, so 61 remain for PCs.
71. **Answer the following: (i) 192.168.10.2/28, Find subnet mask. (ii) 192.168.10.2/28, Find Network Address. (iii) 192.168.10.2/28, Find IP Address of the first host? (iv) 192.168.10.2/28, Find IP Address of the last host? (v) 192.168.10.2/28, Find Broadcast Address.** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*


    Answer: Given 192.168.10.2/28. Block size = 256 − 240 = 16, so blocks in the last octet start at 0, 16, 32, 48 and so on, and 2 lies in the first block.

    - (i) Subnet mask: /28 = 11111111.11111111.11111111.11110000 = 255.255.255.240
    - (ii) Network address: 192.168.10.0
    - (iii) IP address of the first host: 192.168.10.1
    - (iv) IP address of the last host: 192.168.10.14
    - (v) Broadcast address: 192.168.10.15

    - Usable hosts = 2⁴ − 2 = 14.
72. **Select the correct answer: (i) Which cannot IP address 172.16.28.0/16- (a) .0 (b) .1 (c) .255 (d) All (ii) Which at the follow Dynamically Assign Protocol? (a) DHCP (b) ARP (c) ICMP (d) TCP (iii) Which one is Private IP address? (a) 10.10.10.10 (b) 172.172.172.172 (c) 192.192.192.192 (d) All (iv) SSH Protocol port number is _____. (v) Which is the name of Symmetric key encryption algorithm? (a) AES (b) 3DES (c) Re4 (d) None** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 824 (ET: BUET)]*


    Answer:

    (i) Which cannot be an IP address in 172.16.28.0/16 — the answer is (a) .0
    - With a /16 mask the network is 172.16.0.0 and the broadcast is 172.16.255.255. The address 172.16.28.0 is a perfectly valid host address, because the host part is the whole last two octets, so only 172.16.0.0 and 172.16.255.255 are excluded. The address that truly cannot be assigned is the all zeros host address, that is 172.16.0.0, which the option lists as .0.

    (ii) Which is a dynamic address assignment protocol — the answer is (a) DHCP
    - DHCP, the Dynamic Host Configuration Protocol, leases IP addresses automatically over UDP ports 67 and 68 using the DORA exchange. ARP maps IP to MAC, ICMP reports errors and carries ping, and TCP is a transport protocol.

    (iii) Which one is a private IP address — the answer is (a) 10.10.10.10
    - The private ranges are 10.0.0.0/8, 172.16.0.0/12 and 192.168.0.0/16. 172.172.172.172 is outside 172.16 to 172.31, and 192.192.192.192 is outside 192.168, so both are public.

    (iv) SSH protocol port number — the answer is 22
    - SSH runs on TCP port 22. For comparison, Telnet is 23, FTP is 20 and 21, HTTP is 80 and HTTPS is 443.

    (v) Which is a symmetric key encryption algorithm — the answer is all of (a) AES, (b) 3DES and (c) RC4
    - AES, 3DES and RC4 are all symmetric algorithms, which use the same key to encrypt and decrypt. If only one answer is allowed, AES is the strongest and the current standard. RSA, Diffie-Hellman and ECC are the asymmetric algorithms.
73. **A network address is given 172.18.10.0/23, divide this network address into 4 subnets and find every subnet address, start address, subnet mask, broadcast address etc.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 843-844 (ET: N/A)]*


    Answer:

    Given: 172.18.10.0/23, to be divided into 4 subnets.

    Step 1, bits to borrow:
    - 2ⁿ ≥ 4 gives n = 2, so the new prefix is /23 + 2 = /25.

    Step 2, mask and block size:
    - /25 = 255.255.255.128, block size in the last octet = 256 − 128 = 128.
    - Host bits = 32 − 25 = 7, so 2⁷ = 128 addresses and 126 usable hosts per subnet.

    Step 3, the four subnets:

    | Subnet | Network address | Subnet mask | First host | Last host | Broadcast |
    |---|---|---|---|---|---|
    | 1 | 172.18.10.0/25 | 255.255.255.128 | 172.18.10.1 | 172.18.10.126 | 172.18.10.127 |
    | 2 | 172.18.10.128/25 | 255.255.255.128 | 172.18.10.129 | 172.18.10.254 | 172.18.10.255 |
    | 3 | 172.18.11.0/25 | 255.255.255.128 | 172.18.11.1 | 172.18.11.126 | 172.18.11.127 |
    | 4 | 172.18.11.128/25 | 255.255.255.128 | 172.18.11.129 | 172.18.11.254 | 172.18.11.255 |

    - Check: 4 × 128 = 512 addresses, which is exactly the 2⁹ of the original /23, so nothing is wasted.
74. **A network address is given 172.168.0.0/28, divide this network address into 4 subnets and find every subnet address, start address, subnet mask, broadcast address etc.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 856 (ET: N/A)]*


    Answer:

    Given: 172.168.0.0/28, to be divided into 4 subnets.

    Step 1, bits to borrow:
    - 2ⁿ ≥ 4 gives n = 2, so the new prefix is /28 + 2 = /30.

    Step 2, mask and block size:
    - /30 = 255.255.255.252, block size = 256 − 252 = 4.
    - Host bits = 32 − 30 = 2, so 2² = 4 addresses and only 4 − 2 = 2 usable hosts per subnet.

    Step 3, the four subnets:

    | Subnet | Network address | Subnet mask | First host | Last host | Broadcast |
    |---|---|---|---|---|---|
    | 1 | 172.168.0.0/30 | 255.255.255.252 | 172.168.0.1 | 172.168.0.2 | 172.168.0.3 |
    | 2 | 172.168.0.4/30 | 255.255.255.252 | 172.168.0.5 | 172.168.0.6 | 172.168.0.7 |
    | 3 | 172.168.0.8/30 | 255.255.255.252 | 172.168.0.9 | 172.168.0.10 | 172.168.0.11 |
    | 4 | 172.168.0.12/30 | 255.255.255.252 | 172.168.0.13 | 172.168.0.14 | 172.168.0.15 |

    - Check: 4 × 4 = 16 addresses, which is exactly the 2⁴ of the original /28.
    - With only 2 usable addresses each, these subnets are suitable only for point to point router links, which is in fact the standard use of a /30.
75. **In a “Class A” network total 20 subnets are needed with maximum 260 hosts per subnets. Can 255.255.255.0 subnet mask be used in this?** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 862 (ET: BUET)]*


    Answer: No, the mask 255.255.255.0 cannot be used, because it does not provide enough hosts per subnet.

    Step 1, check the host requirement:
    - 255.255.255.0 is a /24, so host bits = 32 − 24 = 8.
    - Usable hosts = 2⁸ − 2 = 254.
    - The requirement is 260 hosts per subnet, and 254 < 260, so the mask fails.

    Step 2, find a mask that does work:
    - 2ʰ − 2 ≥ 260 requires h = 9, since 2⁹ − 2 = 510 ≥ 260, while 2⁸ − 2 = 254 is not enough.
    - Prefix = 32 − 9 = /23, so the mask is 255.255.254.0.

    Step 3, check the subnet requirement with /23:
    - The network is Class A with a default /8, so borrowed bits = 23 − 8 = 15, giving 2¹⁵ = 32,768 subnets, which is far more than the 20 required.

    Final answer: 255.255.255.0 cannot be used because it gives only 254 usable hosts against the requirement of 260. The correct mask is 255.255.254.0, that is /23, which gives 510 usable hosts per subnet and 32,768 subnets, easily satisfying both requirements.
76. **Find Network address, Valid Host, Subnet mask and Broadcast address from 172.16.128.120/25.** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 867 (ET: BUET)]*


    Answer:

    Given: 172.16.128.120/25.

    Step 1, subnet mask:
    - /25 = 11111111.11111111.11111111.10000000 = 255.255.255.128

    Step 2, block size and boundary:
    - Block size = 256 − 128 = 128, so blocks in the last octet start at 0 and 128.
    - 120 lies between 0 and 127, so the block is 172.16.128.0 to 172.16.128.127.

    Answers:
    - Network address: 172.16.128.0
    - Subnet mask: 255.255.255.128, that is /25
    - Broadcast address: 172.16.128.127
    - Valid host range: 172.16.128.1 to 172.16.128.126, that is 2⁷ − 2 = 126 hosts
77. **What is the range of class C IPv4 address? Suppose, Class C network has four subnets. How many usable PC needed each subnet?** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 875-876 (ET: BUET)]*


    Answer:

    Range of Class C IPv4 addresses:
    - First octet from 192 to 223, that is 192.0.0.0 to 223.255.255.255.
    - The default mask is 255.255.255.0, that is /24, giving 254 usable hosts per network.
    - The private portion is 192.168.0.0 to 192.168.255.255.

    Class C network divided into four subnets:
    - Bits to borrow: 2ⁿ ≥ 4 gives n = 2, so the prefix becomes /24 + 2 = /26 and the mask is 255.255.255.192.
    - Host bits = 32 − 26 = 6, so each subnet has 2⁶ = 64 addresses and 2⁶ − 2 = 62 usable addresses.
    - One of those 62 is normally taken by the router interface as the default gateway, so about 61 PCs can be connected per subnet.

    Final answer: 62 usable PCs per subnet, that is 248 in total across the four subnets, against 254 before subnetting. The 6 lost addresses are the extra network and broadcast addresses created by the division.

    | Subnet | Network | Usable range | Broadcast |
    |---|---|---|---|
    | 1 | x.y.z.0/26 | .1 to .62 | .63 |
    | 2 | x.y.z.64/26 | .65 to .126 | .127 |
    | 3 | x.y.z.128/26 | .129 to .190 | .191 |
    | 4 | x.y.z.192/26 | .193 to .254 | .255 |
78. **(a) What is the subnet mask of 10.2.1.3/26 and What is the usable number of IP address on network that has a 26 mask?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 886 (ET: N/A)]*


    Answer:

    Subnet mask of 10.2.1.3/26:
    - /26 in binary is 11111111.11111111.11111111.11000000
    - The last octet 11000000 = 128 + 64 = 192
    - Subnet mask = 255.255.255.192

    Usable number of IP addresses on a /26 network:
    - Host bits = 32 − 26 = 6
    - Total addresses = 2⁶ = 64
    - Usable = 64 − 2 = 62, since the first is the network address and the last is the broadcast address

    Final answer: the subnet mask is 255.255.255.192 and there are 62 usable IP addresses.

    - For this particular address: block size = 256 − 192 = 64, and 3 lies in the first block, so the network address is 10.2.1.0, the broadcast is 10.2.1.63 and the usable range is 10.2.1.1 to 10.2.1.62.
79. **172.168.128.0/20 এর Broadcast Address বের কর এবং কতগুলো Computer (Host) Connect করা যাবে?** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 913 (ET: BUET)]*

    Answer:

    Given: 172.168.128.0/20.

    Step 1, subnet mask and block size:
    - /20 gives the mask 11111111.11111111.11110000.00000000 = 255.255.240.0
    - The interesting octet is the third, so the block size is 256 − 240 = 16, and blocks begin at third octet values 0, 16, 32, ... 128, 144.

    Step 2, boundaries of the block:
    - 128 is itself a block boundary, so the block runs from 172.168.128.0 to 172.168.143.255.

    Step 3, broadcast address:
    - The last address of the block = 172.168.143.255

    Step 4, how many computers can be connected:
    - Host bits = 32 − 20 = 12
    - Total addresses = 2¹² = 4096
    - Usable hosts = 4096 − 2 = 4094

    Final answer:
    - Broadcast address: 172.168.143.255
    - Number of computers that can be connected: 4094, with the usable range 172.168.128.1 to 172.168.143.254.
80. **Suppose a network with IP address 192.16.0.0 is divided into 2 subnets, find number of hosts per subnet. Also for the first subnet, find- (i) First Subnet address (ii) First host address (iii) Last host address (iv) Broadcast address** *[BAUST Assistant Programmer 2021 compact it 919 (ET: N/A)]*


    Answer:

    Given: network 192.16.0.0, divided into 2 subnets.

    Step 1, identify the class and default mask:
    - The first octet is 192, which lies between 192 and 223, so it is a Class C address with a default mask of 255.255.255.0, that is /24. The network is therefore 192.16.0.0/24.

    Step 2, bits to borrow for 2 subnets:
    - 2ⁿ ≥ 2 gives n = 1, so the new prefix is /25 and the mask is 255.255.255.128.

    Step 3, hosts per subnet:
    - Host bits = 32 − 25 = 7, so 2⁷ = 128 addresses and 128 − 2 = 126 usable hosts per subnet.

    Step 4, the first subnet:
    - (i) First subnet address: 192.16.0.0/25
    - (ii) First host address: 192.16.0.1
    - (iii) Last host address: 192.16.0.126
    - (iv) Broadcast address: 192.16.0.127

    - The second subnet is 192.16.0.128/25, with hosts 192.16.0.129 to 192.16.0.254 and broadcast 192.16.0.255.
81. **Find the Subnet mask from the following IP: 192.168.3.0/22** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922 (ET: N/A)]*


    Answer:

    Given: 192.168.3.0/22.

    Step 1, write the mask in binary:
    - /22 means the first 22 bits are 1: 11111111.11111111.11111100.00000000

    Step 2, convert to decimal:
    - 255.255.252.0

    Final answer: the subnet mask is 255.255.252.0.

    - Supporting values: block size in the third octet = 256 − 252 = 4, so the blocks start at third octets 0, 4, 8 and so on. The address 192.168.3.0 falls in the block beginning at 192.168.0.0, so the actual network is 192.168.0.0/22, the broadcast is 192.168.3.255, the usable range is 192.168.0.1 to 192.168.3.254, and there are 2¹⁰ − 2 = 1022 usable hosts.
82. **VLSM Subnetting. Given an IP address, 192.168.0.0/20 For creating 4 subnets department of A, B, C, D with 2000, 1000, 6000 and 8000 hosts, find out every department first and last IP address. Also write the subnet mask of q.x.y.z/notation.** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 927 (ET: CTI)]*


    Answer: This requires VLSM, allocating the largest requirement first.

    Step 1, check whether the given block is large enough:
    - Total requirement = 2000 + 1000 + 6000 + 8000 = 17,000 hosts.
    - A /20 block holds only 2¹² = 4096 addresses, which is far short of 17,000. The given block is therefore too small, and the smallest block that can hold the allocation is a /17 with 32,768 addresses.
    - The solution below is worked on 192.168.0.0/17, since the method is what is being examined; with a /20 the requirement simply cannot be met.

    Step 2, size each department:

    | Dept | Hosts | Host bits, 2ʰ − 2 ≥ need | Prefix | Block size |
    |---|---|---|---|---|
    | D | 8000 | 13, since 2¹³ − 2 = 8190 | /19 | 8192 |
    | C | 6000 | 13, since 2¹³ − 2 = 8190 | /19 | 8192 |
    | A | 2000 | 11, since 2¹¹ − 2 = 2046 | /21 | 2048 |
    | B | 1000 | 10, since 2¹⁰ − 2 = 1022 | /22 | 1024 |

    Step 3, allocate sequentially, largest first:

    | Dept | Network block | Subnet mask | First IP | Last IP | Broadcast |
    |---|---|---|---|---|---|
    | D, 8000 | 192.168.0.0/19 | 255.255.224.0 | 192.168.0.1 | 192.168.31.254 | 192.168.31.255 |
    | C, 6000 | 192.168.32.0/19 | 255.255.224.0 | 192.168.32.1 | 192.168.63.254 | 192.168.63.255 |
    | A, 2000 | 192.168.64.0/21 | 255.255.248.0 | 192.168.64.1 | 192.168.71.254 | 192.168.71.255 |
    | B, 1000 | 192.168.72.0/22 | 255.255.252.0 | 192.168.72.1 | 192.168.75.254 | 192.168.75.255 |

    - Total used = 8192 + 8192 + 2048 + 1024 = 19,456 addresses out of 32,768, so 192.168.76.0 onwards remains free.
    - The reason for allocating largest first is alignment: every block must start on a boundary that is a multiple of its own size, and taking the big blocks first guarantees this without leaving unusable gaps. <!-- verify -->
83. **You are given a IP address 172.16.20.0/25 have four subnets. For each department find the following information. (CSE, EEE, IPE, PME)** *[NRCC Assistant Programmer 2021 compact it 931 (ET: N/A)]*


    Answer:

    Given: 172.16.20.0/25, to be divided into 4 subnets for CSE, EEE, IPE and PME.

    Step 1, bits to borrow:
    - 2ⁿ ≥ 4 gives n = 2, so the new prefix is /25 + 2 = /27.

    Step 2, mask and block size:
    - /27 = 255.255.255.224, block size = 256 − 224 = 32.
    - Host bits = 32 − 27 = 5, so 2⁵ = 32 addresses and 30 usable hosts per department.

    Step 3, the four departments:

    | Department | Network address | Subnet mask | First host | Last host | Broadcast | Usable hosts |
    |---|---|---|---|---|---|---|
    | CSE | 172.16.20.0/27 | 255.255.255.224 | 172.16.20.1 | 172.16.20.30 | 172.16.20.31 | 30 |
    | EEE | 172.16.20.32/27 | 255.255.255.224 | 172.16.20.33 | 172.16.20.62 | 172.16.20.63 | 30 |
    | IPE | 172.16.20.64/27 | 255.255.255.224 | 172.16.20.65 | 172.16.20.94 | 172.16.20.95 | 30 |
    | PME | 172.16.20.96/27 | 255.255.255.224 | 172.16.20.97 | 172.16.20.126 | 172.16.20.127 | 30 |

    - Check: 4 × 32 = 128 addresses, which is exactly the 2⁷ of the original /25, so the block is used completely.
84. **Define IP 127.0.0.1, what is localhost?** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 932 (ET: BUET)]*


    Answer:

    IP 127.0.0.1:
    - It is the IPv4 loopback address, and the whole block 127.0.0.0/8 is reserved for this purpose.
    - A packet sent to it never reaches the network card or the cable; the TCP/IP stack of the machine loops it straight back. So it tests the machine's own protocol stack rather than any external connectivity.
    - `ping 127.0.0.1` is therefore the first diagnostic step: if it fails, the TCP/IP stack or the driver is broken, and no cable or switch check will help.
    - The IPv6 equivalent is `::1`.
    - Any address in 127.0.0.0/8, such as 127.0.0.53, behaves the same way, which is why some system resolvers listen on such addresses.

    What localhost is:
    - `localhost` is the standard hostname that refers to the machine itself. It resolves to 127.0.0.1 for IPv4 and to `::1` for IPv6.
    - The mapping is defined in the `hosts` file, `C:\Windows\System32\drivers\etc\hosts` on Windows and `/etc/hosts` on Linux, so it works even when DNS is unavailable.
    - Uses: connecting to a server running on the same machine, for example `http://localhost:8080` for a local web application or `localhost:3306` for a local MySQL database; and testing an application during development before it is deployed.
    - A service bound to 127.0.0.1 is reachable only from that machine and not from the network, which is a common and deliberate security measure for databases and admin interfaces.
85. **What is static IP Address and dynamic IP Address?** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 932 (ET: BUET)]*


    Answer:

    Static IP address:
    - An address configured manually on the device and kept permanently, so it does not change when the machine restarts.
    - Advantages: the address is always known, which is essential for servers, printers, routers, cameras and any device that must be reached by name or by port forwarding; DNS records and firewall rules stay valid; remote access is reliable; and there is no dependence on a DHCP server.
    - Disadvantages: manual configuration on every device is slow and error prone; a mistake causes an IP conflict; it does not scale to hundreds of machines; and moving a device to another subnet requires reconfiguration.

    Dynamic IP address:
    - An address leased automatically by a DHCP server for a limited period, which may change on renewal or when the device reconnects.
    - Advantages: no manual work, no duplicate address conflicts, efficient reuse of a limited address pool, easy support for laptops, phones and guests, and central change of gateway or DNS settings for the whole network at once.
    - Disadvantages: the address is not predictable, so the device cannot easily be reached from outside; the network depends on the DHCP server, which becomes a single point of failure; and troubleshooting is harder because the address in yesterday's log may belong to another machine today.

    | Point | Static | Dynamic |
    |---|---|---|
    | Assigned by | Administrator, manually | DHCP server, automatically |
    | Changes | Never | On lease expiry or reconnection |
    | Suitable for | Servers, printers, routers, cameras | PCs, laptops, phones, guest devices |
    | Cost and effort | Higher administrative effort | Very low |
    | Reliability of reachability | High | Low unless a reservation is used |

    - Middle ground: a DHCP reservation binds a fixed address to a device's MAC, giving the predictability of a static address with the central management of DHCP.
86. **Using the IP address 192.168.10.0/23 find out- (i) Subnet/First address (ii) Last Address (iii) Subnet mask** *[SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)]*


    Answer:

    Given: 192.168.10.0/23.

    Step 1, subnet mask:
    - /23 = 11111111.11111111.11111110.00000000 = 255.255.254.0

    Step 2, block size and boundary:
    - Block size in the third octet = 256 − 254 = 2, so blocks begin at even third octets.
    - 10 is even, so the block runs from 192.168.10.0 to 192.168.11.255.

    Answers:
    - (i) Subnet, that is the first address: 192.168.10.0, which is the network address; the first usable host address is 192.168.10.1
    - (ii) Last address: 192.168.11.255, which is the broadcast address; the last usable host address is 192.168.11.254
    - (iii) Subnet mask: 255.255.254.0, that is /23

    - Total addresses = 2⁹ = 512, of which 510 are usable.
87. **Consider the IP address 10.20.30.0/25 now answer the below question: (i) What is the subnet mask of the above IP address? (ii) How many host per subnet have? (iii) What is the Broadcast address of this 10.20.30.0/3 IP address?** *[Janata Bank Assistant System Administrator 2021 compact it 938 (ET: N/A)]*


    Answer:

    Given: 10.20.30.0/25.

    (i) Subnet mask:
    - /25 = 11111111.11111111.11111111.10000000 = 255.255.255.128

    (ii) Hosts per subnet:
    - Host bits = 32 − 25 = 7, so 2⁷ = 128 addresses and 128 − 2 = 126 usable hosts.

    (iii) Broadcast address:
    - Block size = 256 − 128 = 128, so the block runs from 10.20.30.0 to 10.20.30.127.
    - Broadcast address = 10.20.30.127

    - Usable host range: 10.20.30.1 to 10.20.30.126.
88. **২. 192.168.10.0/28 এর জন্য সাবনেট মাস্ক হবে কোনটি?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

    Answer: The subnet mask for 192.168.10.0/28 is 255.255.255.240.

    - /28 means the first 28 bits are 1: 11111111.11111111.11111111.11110000
    - The last octet 11110000 = 128 + 64 + 32 + 16 = 240
    - Therefore the mask is 255.255.255.240.

    - In this block the host bits are 32 − 28 = 4, so there are 2⁴ = 16 addresses and 14 usable hosts. The network address is 192.168.10.0, the broadcast address is 192.168.10.15, and the host range is 192.168.10.1 to 192.168.10.14.
89. **৯. ক্লাস C এর ডিফল্ট সাবনেট মাস্ক কত?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

    Answer: The default subnet mask of Class C is 255.255.255.0, that is /24.

    - In binary: 11111111.11111111.11111111.00000000
    - It has 24 network bits and 8 host bits, so every Class C network holds 2⁸ = 256 addresses and 254 usable hosts.
    - For comparison, the Class A default mask is 255.0.0.0, that is /8, and the Class B default mask is 255.255.0.0, that is /16.
90. **১১. নিচের কোনটি লুপ ব্যাক আইপি এড্রেস?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

    Answer: The loopback IP address is 127.0.0.1.

    - The whole block 127.0.0.0/8 is reserved for loopback, that is 127.0.0.0 to 127.255.255.255.
    - A packet sent to this address never reaches the network card or the cable; the TCP/IP stack returns it directly. This is why `ping 127.0.0.1` is used to test whether the machine's own TCP/IP stack is working.
    - Its hostname is `localhost`, and the IPv6 loopback address is `::1`.
91. **A IP Address is: 172.16.128.120/25 now answers the following questions: (i) What is the network address of this IP? (ii) What is the subnet mask? (iii) What is the broadcast address? (iv) How many connection is possible in this network?** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 975 (ET: BUET)]*


    Answer:

    Given: 172.16.128.120/25.

    Step 1, mask and block size:
    - /25 = 255.255.255.128, block size = 256 − 128 = 128, so blocks in the last octet begin at 0 and 128.
    - 120 lies between 0 and 127, so the block is 172.16.128.0 to 172.16.128.127.

    Answers:
    - (i) Network address: 172.16.128.0
    - (ii) Subnet mask: 255.255.255.128, that is /25
    - (iii) Broadcast address: 172.16.128.127
    - (iv) Number of connections possible: host bits = 32 − 25 = 7, so 2⁷ − 2 = 126 usable host addresses, of which one is normally the router interface, leaving 125 for hosts.

    - Usable range: 172.16.128.1 to 172.16.128.126.
92. **(a) A IP address is 172.20.0.0/27. How many subnets and hosts per subnet?** *[National University Assistant Programmer 2020 compact it 977 (ET: DU)]*


    Answer:

    Given: 172.20.0.0/27.

    Step 1, identify the class and default prefix:
    - The first octet is 172, which lies between 128 and 191, so it is a Class B address with a default prefix of /16.

    Step 2, number of subnets:
    - Bits borrowed = 27 − 16 = 11
    - Number of subnets = 2¹¹ = 2048

    Step 3, hosts per subnet:
    - Host bits = 32 − 27 = 5
    - Total addresses = 2⁵ = 32, and usable hosts = 32 − 2 = 30

    Final answer: 2048 subnets, each with 30 usable hosts.

    - Check: 2048 × 32 = 65,536 addresses, which is exactly the 2¹⁶ of the original Class B block.
    - The first subnet is 172.20.0.0/27 with hosts 172.20.0.1 to 172.20.0.30 and broadcast 172.20.0.31; the mask is 255.255.255.224 and the block size is 32.
93. **Given IP address 172.16.128.120/25 what is the subnet mask, network address, broadcast address and total usable host in this network?** *[NACTAR Assistant Instructor (ICT) 2020 compact it 991 (ET: N/A)]*


    Answer:

    Given: 172.16.128.120/25.

    Step 1, subnet mask:
    - /25 = 11111111.11111111.11111111.10000000 = 255.255.255.128

    Step 2, block size and boundary:
    - Block size = 256 − 128 = 128, so blocks in the last octet start at 0 and 128.
    - 120 lies between 0 and 127, so the block is 172.16.128.0 to 172.16.128.127.

    Answers:
    - Subnet mask: 255.255.255.128
    - Network address: 172.16.128.0
    - Broadcast address: 172.16.128.127
    - Total usable hosts: 2⁷ − 2 = 126, with the range 172.16.128.1 to 172.16.128.126
94. **Given IP address is 172.168.10.0/24, administrator wants to create 32 subnets, then find out sub netmask, number of address of each subnet, first and last address of subnet 1, first and last address of subnet 32.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1012 (ET: DU)]*


    Answer:

    Given: 172.168.10.0/24, to be divided into 32 subnets.

    Step 1, bits to borrow:
    - 2ⁿ ≥ 32 gives n = 5, so the new prefix is /24 + 5 = /29.

    Step 2, subnet mask:
    - /29 = 11111111.11111111.11111111.11111000 = 255.255.255.248

    Step 3, addresses per subnet:
    - Host bits = 32 − 29 = 3, so 2³ = 8 addresses per subnet, of which 6 are usable.
    - Block size = 256 − 248 = 8, so the subnets start at 0, 8, 16, 24, ... 248.

    Step 4, first and last subnets:

    | Subnet | Network address | First host | Last host | Broadcast |
    |---|---|---|---|---|
    | 1 | 172.168.10.0/29 | 172.168.10.1 | 172.168.10.6 | 172.168.10.7 |
    | 32 | 172.168.10.248/29 | 172.168.10.249 | 172.168.10.254 | 172.168.10.255 |

    - The 32nd subnet begins at (32 − 1) × 8 = 248.

    Final answer:
    - Subnet mask: 255.255.255.248, that is /29
    - Number of addresses per subnet: 8, of which 6 are usable
    - Subnet 1: first address 172.168.10.0 and last address 172.168.10.7, with hosts 172.168.10.1 to 172.168.10.6
    - Subnet 32: first address 172.168.10.248 and last address 172.168.10.255, with hosts 172.168.10.249 to 172.168.10.254
    - Check: 32 × 8 = 256, which is exactly the original /24.
95. **Given IP Address 180.79.35.5/24, Find the (i) Network address (ii) Broadcast address (iii) Subnet mask (iv) Total valid host (v) IP address class** *[PGCB Sub-Assistant Engineer (CSE) 2020 compact it 1043 (ET: BUET)]*


    Answer:

    Given: 180.79.35.5/24.

    (i) Network address:
    - /24 means the first three octets are the network part, so the network address is 180.79.35.0.

    (ii) Broadcast address:
    - All host bits set to 1 gives 180.79.35.255.

    (iii) Subnet mask:
    - /24 = 11111111.11111111.11111111.00000000 = 255.255.255.0.

    (iv) Total valid hosts:
    - Host bits = 32 − 24 = 8, so 2⁸ = 256 addresses and 256 − 2 = 254 valid hosts, with the range 180.79.35.1 to 180.79.35.254.

    (v) IP address class:
    - The first octet is 180, which lies between 128 and 191, so it is a Class B address.
    - Note that the given /24 mask overrides the Class B default of /16, which is what classless addressing permits; the address is therefore a Class B address being used with a /24 subnet mask.

## OSI & TCP/IP Reference Model (43)

1. Mention the layers of the OSI Model and the function of each layer. *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*


   Answer: The OSI model, Open Systems Interconnection, developed by ISO in 1984, divides network communication into seven layers, each providing a defined service to the layer above it.

   | # | Layer | Function | PDU | Protocols and devices |
   |---|---|---|---|---|
   | 7 | Application | Provides the interface to the user's application: file transfer, mail, web, name lookup | Data | HTTP, HTTPS, FTP, SMTP, DNS, SNMP, Telnet |
   | 6 | Presentation | Translation of data format, encryption and decryption, compression | Data | SSL/TLS, JPEG, MPEG, ASCII, EBCDIC |
   | 5 | Session | Establishes, manages and terminates sessions, dialogue control and synchronisation checkpoints | Data | NetBIOS, RPC, PPTP, SQL sessions |
   | 4 | Transport | End to end delivery between processes, segmentation and reassembly, port addressing, flow and error control | Segment for TCP, Datagram for UDP | TCP, UDP, SCTP; gateway |
   | 3 | Network | Logical addressing, routing between different networks, path selection, fragmentation | Packet | IP, ICMP, IGMP, OSPF, RIP, BGP; router, layer 3 switch |
   | 2 | Data link | Gives reliable node to node delivery. It breaks data into frames with start and stop bits, uses MAC addresses for physical addressing, detects errors and asks for retransmission, and controls access to the medium so frames do not collide. It has two sublayers: LLC, which handles flow and error control, and MAC, which handles hardware addressing | Frame | Ethernet, PPP, PPTP, HDLC, ARP; switch, bridge, NIC |
   | 1 | Physical | Sends raw bits as electrical, optical or radio signals. It gives bit synchronisation through a clock, sets the bit rate, and defines the topology (bus, star, mesh) and the transmission mode (simplex, half-duplex, full-duplex) | Bit | USB, SONET/SDH, RS-232, DSL; hub, repeater, modem, cable |

   From top to bottom:
   - 7. Application
   - 6. Presentation
   - 5. Session
   - 4. Transport
   - 3. Network
   - 2. Data Link
   - 1. Physical

   - Mnemonic, top down: All People Seem To Need Data Processing. Bottom up: Please Do Not Throw Sausage Pizza Away.
2. **OSI মডেলের ৭টি স্তরের কাজ কি? এই সমগ্র স্তরগুলোর ভূমিকা কি?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

   Answer: The seven layers of the OSI model and their functions:

   | # | Layer | Function | PDU | Protocols and devices |
   |---|---|---|---|---|
   | 7 | Application | Provides the interface to the user's application: file transfer, mail, web, name lookup | Data | HTTP, HTTPS, FTP, SMTP, DNS, SNMP, Telnet |
   | 6 | Presentation | Translation of data format, encryption and decryption, compression | Data | SSL/TLS, JPEG, MPEG, ASCII, EBCDIC |
   | 5 | Session | Establishes, manages and terminates sessions, dialogue control and synchronisation checkpoints | Data | NetBIOS, RPC, PPTP, SQL sessions |
   | 4 | Transport | End to end delivery between processes, segmentation and reassembly, port addressing, flow and error control | Segment for TCP, Datagram for UDP | TCP, UDP, SCTP; gateway |
   | 3 | Network | Logical addressing, routing between different networks, path selection, fragmentation | Packet | IP, ICMP, IGMP, OSPF, RIP, BGP; router, layer 3 switch |
   | 2 | Data link | Gives reliable node to node delivery. It breaks data into frames with start and stop bits, uses MAC addresses for physical addressing, detects errors and asks for retransmission, and controls access to the medium so frames do not collide. It has two sublayers: LLC, which handles flow and error control, and MAC, which handles hardware addressing | Frame | Ethernet, PPP, PPTP, HDLC, ARP; switch, bridge, NIC |
   | 1 | Physical | Sends raw bits as electrical, optical or radio signals. It gives bit synchronisation through a clock, sets the bit rate, and defines the topology (bus, star, mesh) and the transmission mode (simplex, half-duplex, full-duplex) | Bit | USB, SONET/SDH, RS-232, DSL; hub, repeater, modem, cable |

   Overall role of the seven layers:
   - They break a complex communication problem into small independent parts, so each part can be designed, understood and debugged separately.
   - Each layer uses the service of the layer below and provides a service to the layer above, while hiding its own internal working. Because of this abstraction, a technology can be changed in one layer without disturbing the others; moving from copper to fibre changes nothing above the physical layer.
   - Equipment from different manufacturers can interoperate, because the interface and the protocol of every layer are standardised.
   - Troubleshooting becomes systematic: start at layer 1 and work upward, and the layer at which the failure appears identifies the problem.
   - When data is sent, each layer adds its own header, which is called encapsulation, and at the receiving end each layer removes its own header in the reverse order.
3. **What is the OSI model? Explain the functions of each layer with examples.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*


   Answer: The OSI, Open Systems Interconnection, model is a seven layer reference model developed by ISO in 1984 that describes how data moves from an application on one computer to an application on another, dividing the whole task into seven independent layers.

   | # | Layer | Function | PDU | Protocols and devices |
   |---|---|---|---|---|
   | 7 | Application | Provides the interface to the user's application: file transfer, mail, web, name lookup | Data | HTTP, HTTPS, FTP, SMTP, DNS, SNMP, Telnet |
   | 6 | Presentation | Translation of data format, encryption and decryption, compression | Data | SSL/TLS, JPEG, MPEG, ASCII, EBCDIC |
   | 5 | Session | Establishes, manages and terminates sessions, dialogue control and synchronisation checkpoints | Data | NetBIOS, RPC, PPTP, SQL sessions |
   | 4 | Transport | End to end delivery between processes, segmentation and reassembly, port addressing, flow and error control | Segment for TCP, Datagram for UDP | TCP, UDP, SCTP; gateway |
   | 3 | Network | Logical addressing, routing between different networks, path selection, fragmentation | Packet | IP, ICMP, IGMP, OSPF, RIP, BGP; router, layer 3 switch |
   | 2 | Data link | Gives reliable node to node delivery. It breaks data into frames with start and stop bits, uses MAC addresses for physical addressing, detects errors and asks for retransmission, and controls access to the medium so frames do not collide. It has two sublayers: LLC, which handles flow and error control, and MAC, which handles hardware addressing | Frame | Ethernet, PPP, PPTP, HDLC, ARP; switch, bridge, NIC |
   | 1 | Physical | Sends raw bits as electrical, optical or radio signals. It gives bit synchronisation through a clock, sets the bit rate, and defines the topology (bus, star, mesh) and the transmission mode (simplex, half-duplex, full-duplex) | Bit | USB, SONET/SDH, RS-232, DSL; hub, repeater, modem, cable |

   Function of each layer with an example:
   - Physical: sends raw bits as signals. Example, the electrical voltage on a UTP cable or the light pulse in a fibre; a hub works here.
   - Data link: builds frames and delivers them between two directly connected devices using MAC addresses. Example, an Ethernet switch forwarding a frame to the port where 00:1A:2B:3C:4D:5E lives.
   - Network: gives logical addresses and routes packets between different networks. Example, a router sending a packet destined for 8.8.8.8 out of its Internet interface.
   - Transport: delivers data between processes, with ports, segmentation and reliability. Example, TCP port 443 carrying a web session and retransmitting a lost segment.
   - Session: opens, manages and closes the conversation. Example, a remote procedure call or a database session that must be reopened after a disconnection.
   - Presentation: translates, encrypts and compresses. Example, TLS encrypting the data, or a JPEG image being decoded into pixels.
   - Application: gives the user's program access to the network. Example, a browser issuing an HTTP GET, or a mail client using SMTP.

   - Encapsulation: as data goes down the stack each layer adds its header, Data becomes Segment, then Packet, then Frame, then Bits; at the receiver the process is reversed, which is called decapsulation.
4. **(b) Name the OSI layers and give one example of a cyber threat at any tree of those layers.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*


   Answer: The seven OSI layers, from the top: Application, Presentation, Session, Transport, Network, Data Link and Physical.

   Cyber threats at three of those layers:
   - Application layer: SQL injection, cross site scripting and an HTTP flood DDoS attack. A crafted input string reaches the database and lets the attacker read or delete data. Defence: input validation, prepared statements and a web application firewall.
   - Transport layer: a TCP SYN flood. The attacker sends thousands of SYN packets with spoofed sources and never completes the handshake, so the server's connection table fills up and legitimate users are refused. Defence: SYN cookies, rate limiting and a firewall.
   - Network layer: IP spoofing and ICMP based attacks such as smurf or ping of death, and route hijacking through forged BGP announcements. Defence: ingress and egress filtering, RPKI, and blocking directed broadcasts.
   - Data link layer, if a fourth is wanted: ARP spoofing, which lets an attacker place himself in the middle of a conversation, and MAC flooding, which turns a switch into a hub. Defence: dynamic ARP inspection and port security.
   - Physical layer: cable tapping, jamming and simple theft or destruction of equipment. Defence: locked rooms, conduit, CCTV and fibre, which shows a detectable disturbance when tapped.
5. **Write bottom to top OSI reference Model.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1449 (ET: N/A)]*


   Answer: OSI reference model from bottom to top:

   - 1. Physical
   - 2. Data Link
   - 3. Network
   - 4. Transport
   - 5. Session
   - 6. Presentation
   - 7. Application

   - Mnemonic: Please Do Not Throw Sausage Pizza Away.
6. **In the TCP/IP model, how is data known in the different layers?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*


   Answer: In the TCP/IP model the unit of data, that is the Protocol Data Unit, has a different name at each layer.

   | TCP/IP layer | Name of the data unit |
   |---|---|
   | Application | Data, or message |
   | Transport | Segment for TCP, Datagram for UDP |
   | Internet | Packet, also called an IP datagram |
   | Network Access | Frame at the data link sublayer, and Bits at the physical sublayer |

   - As the data goes down the stack, each layer adds its own header to the unit it received; this is encapsulation. At the receiving end each layer removes its header, which is decapsulation.
   - Example: an HTTP request is Data, TCP adds a header with the ports and it becomes a Segment, IP adds a header with the addresses and it becomes a Packet, Ethernet adds a header and a CRC trailer and it becomes a Frame, and finally the NIC transmits it as Bits.
7. **(b) Explain the TCP/IP protocol switch layers.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1444 (ET: N/A)]*


   Answer: The TCP/IP protocol suite is organised into four layers, each with its own protocols.

   | Layer | Corresponding OSI layers | Function | Protocols | Devices |
   |---|---|---|---|---|
   | Application | Application, Presentation, Session | Provides network services directly to the user's programs: web, mail, file transfer, name resolution | HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH | Proxy server, application firewall, gateway |
   | Transport | Transport | End to end delivery between processes, port addressing, segmentation, reliability, flow and congestion control | TCP, UDP, SCTP | Gateway, layer 4 load balancer |
   | Internet | Network | Logical addressing, routing between networks, packet forwarding, fragmentation | IP, ICMP, IGMP, ARP, RARP, OSPF, BGP | Router, layer 3 switch |
   | Network Access, that is Link | Data link, Physical | Framing, MAC addressing, medium access, and physical transmission of bits over the medium | Ethernet, Wi-Fi 802.11, PPP, HDLC, Frame Relay | Switch, bridge, hub, NIC, cable, repeater |

   ```mermaid
   graph TD
       A["Application layer: HTTP, HTTPS, FTP, SMTP, DNS, DHCP, SNMP, Telnet, SSH"] --> B["Transport layer: TCP, UDP"]
       B --> C["Internet layer: IP, ICMP, IGMP, ARP, OSPF, BGP"]
       C --> D["Network Access layer: Ethernet, Wi-Fi 802.11, PPP, HDLC"]
       D --> E["Physical medium: copper, fibre, radio"]
   ```

   - The Application layer of TCP/IP absorbs the Application, Presentation and Session layers of OSI, and the Network Access layer absorbs the Data Link and Physical layers.
   - Data is encapsulated on the way down, Data to Segment to Packet to Frame to Bits, and decapsulated on the way up.
8. **(b) Draw the diagram of TCP/IP protocol suite and mention the name of protocols used in different layers of TCP/IP.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1352 (ET: N/A)]*


   Answer:

   ```mermaid
   graph TD
       A["Application layer: HTTP, HTTPS, FTP, SMTP, DNS, DHCP, SNMP, Telnet, SSH"] --> B["Transport layer: TCP, UDP"]
       B --> C["Internet layer: IP, ICMP, IGMP, ARP, OSPF, BGP"]
       C --> D["Network Access layer: Ethernet, Wi-Fi 802.11, PPP, HDLC"]
       D --> E["Physical medium: copper, fibre, radio"]
   ```

   Protocols used in each layer:

   | Layer | Corresponding OSI layers | Function | Protocols | Devices |
   |---|---|---|---|---|
   | Application | Application, Presentation, Session | Provides network services directly to the user's programs: web, mail, file transfer, name resolution | HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH | Proxy server, application firewall, gateway |
   | Transport | Transport | End to end delivery between processes, port addressing, segmentation, reliability, flow and congestion control | TCP, UDP, SCTP | Gateway, layer 4 load balancer |
   | Internet | Network | Logical addressing, routing between networks, packet forwarding, fragmentation | IP, ICMP, IGMP, ARP, RARP, OSPF, BGP | Router, layer 3 switch |
   | Network Access, that is Link | Data link, Physical | Framing, MAC addressing, medium access, and physical transmission of bits over the medium | Ethernet, Wi-Fi 802.11, PPP, HDLC, Frame Relay | Switch, bridge, hub, NIC, cable, repeater |

   - Note on ARP: it sits between the Internet and Network Access layers, since it maps an IP address to a MAC address, and it is usually shown at the Network Access layer in the TCP/IP model.
9. **How many Layers of OSI?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1450 (ET: N/A)]*


   Answer: The OSI model has 7 layers.

   - From bottom to top: Physical, Data Link, Network, Transport, Session, Presentation and Application.
10. **রাউটার OSI এর কোন লেয়ারে থাকে?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1450 (ET: N/A)]*

    Answer: A router works at the Network layer, that is Layer 3, of the OSI model.

    - It reads the destination IP address of a packet, performs a longest prefix match in its routing table and selects the best next hop.
    - It also decrements the TTL, performs fragmentation where the next link has a smaller MTU, and blocks broadcasts, so every interface becomes a separate broadcast domain.
    - For comparison: a hub and a repeater work at Layer 1, a switch and a bridge at Layer 2, a Layer 3 switch and a router at Layer 3, and a gateway or a firewall may work anywhere from Layer 4 up to Layer 7.
11. **Write the name of OSI layers.** *[NSDA Assistant Maintenance Engineer 11.05.2024 compact it 384 (ET: N/A)]*


    Answer: The names of the OSI layers:

    From top to bottom:
    - 7. Application
    - 6. Presentation
    - 5. Session
    - 4. Transport
    - 3. Network
    - 2. Data Link
    - 1. Physical

    - Mnemonic, top down: All People Seem To Need Data Processing. Bottom up: Please Do Not Throw Sausage Pizza Away.
12. **Write the name of OSI layers protocol for every layers.** *[NSDA Assistant Maintenance Engineer 11.05.2024 compact it 384 (ET: N/A)]*


    Answer: Protocols used at each layer of the OSI model:

    | Layer | Protocols |
    |---|---|
    | 7. Application | HTTP, HTTPS, FTP, TFTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH, NFS |
    | 6. Presentation | SSL, TLS, JPEG, GIF, MPEG, MIME, ASCII, EBCDIC, and compression formats |
    | 5. Session | NetBIOS, RPC, PPTP, SIP, SQL sessions, NFS session control |
    | 4. Transport | TCP, UDP, SCTP, DCCP |
    | 3. Network | IP, IPv6, ICMP, IGMP, IPsec, OSPF, RIP, EIGRP, BGP |
    | 2. Data Link | Ethernet 802.3, Wi-Fi 802.11, PPP, HDLC, Frame Relay, ATM, ARP, RARP, STP, VLAN 802.1Q |
    | 1. Physical | Ethernet physical specifications, RS-232, DSL, ISDN, USB, Bluetooth radio, SONET, and the cable and connector standards |
13. **Tabular representation of TCP/IP layer, functions of each layer, Associate protocols, device, and software in each layer. Different types of network firewalls. Explain NGFW compared to traditional firewall.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 301 (ET: BIBM)]*


    Answer:

    TCP/IP layers, functions, protocols, devices and software:

    | Layer | Corresponding OSI layers | Function | Protocols | Devices |
    |---|---|---|---|---|
    | Application | Application, Presentation, Session | Provides network services directly to the user's programs: web, mail, file transfer, name resolution | HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH | Proxy server, application firewall, gateway |
    | Transport | Transport | End to end delivery between processes, port addressing, segmentation, reliability, flow and congestion control | TCP, UDP, SCTP | Gateway, layer 4 load balancer |
    | Internet | Network | Logical addressing, routing between networks, packet forwarding, fragmentation | IP, ICMP, IGMP, ARP, RARP, OSPF, BGP | Router, layer 3 switch |
    | Network Access, that is Link | Data link, Physical | Framing, MAC addressing, medium access, and physical transmission of bits over the medium | Ethernet, Wi-Fi 802.11, PPP, HDLC, Frame Relay | Switch, bridge, hub, NIC, cable, repeater |

    Software at each layer, to complete the table: browsers, mail clients and web servers at the Application layer; the operating system's TCP/IP socket stack at the Transport and Internet layers; and the NIC driver and firmware at the Network Access layer.

    Types of network firewall:
    - Packet filtering firewall: examines each packet's source and destination IP, port and protocol against an ACL. Stateless, very fast and cheap, but it cannot see the context and is easily fooled by a fragmented or spoofed packet.
    - Stateful inspection firewall: keeps a connection table and allows a packet only if it belongs to a legitimate existing session. Far more secure than packet filtering, and it is the standard type today.
    - Circuit level gateway: works at the session layer, verifying the TCP handshake before allowing the session, but it does not inspect the content.
    - Application level gateway, that is a proxy firewall: terminates the connection and rebuilds it, inspecting the full application content such as the HTTP request. Very secure but slower, and one proxy is needed per protocol.
    - Next Generation Firewall, NGFW: combines all of the above with deep packet inspection and additional security services.
    - Others worth naming: a host based software firewall, a Web Application Firewall for HTTP only, and a cloud or firewall-as-a-service deployment.

    NGFW compared with a traditional firewall:

    | Point | Traditional firewall | NGFW |
    |---|---|---|
    | Inspection depth | Header only, that is IP, port and protocol | Deep packet inspection of the payload as well |
    | Layers covered | 3 and 4 | 3 to 7, including the application layer |
    | Application awareness | None; it sees only port 443 | Identifies the actual application, so Facebook and Dropbox on the same port 443 are distinguished |
    | User awareness | None; it sees only IP addresses | Integrates with Active Directory or LDAP, so policy can be written per user or group |
    | Threat prevention | None built in | Integrated IPS, antivirus, anti-bot and sandboxing |
    | Encrypted traffic | Cannot inspect it | TLS inspection, decrypt, inspect and re-encrypt |
    | Threat intelligence | None | Cloud feeds of known bad IPs, domains and file hashes, updated continuously |
    | Policy style | Allow port 443 from this subnet | Allow the Finance group to use Salesforce but not file sharing |
    | Performance cost | Very low | High, so it needs far more processing power |
    | Cost and complexity | Low | High, with subscription licences for the security services |

    - In short, a traditional firewall asks where the packet is going, while an NGFW asks who is sending it, what application it is, and whether it is carrying an attack.
14. **Explain TCP/IP model and its protocol and device.** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 404 (ET: N/A)]*


    Answer: The TCP/IP model is the four layer practical architecture on which the Internet actually runs, developed by DARPA in the 1970s and named after its two principal protocols.

    | Layer | Corresponding OSI layers | Function | Protocols | Devices |
    |---|---|---|---|---|
    | Application | Application, Presentation, Session | Provides network services directly to the user's programs: web, mail, file transfer, name resolution | HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH | Proxy server, application firewall, gateway |
    | Transport | Transport | End to end delivery between processes, port addressing, segmentation, reliability, flow and congestion control | TCP, UDP, SCTP | Gateway, layer 4 load balancer |
    | Internet | Network | Logical addressing, routing between networks, packet forwarding, fragmentation | IP, ICMP, IGMP, ARP, RARP, OSPF, BGP | Router, layer 3 switch |
    | Network Access, that is Link | Data link, Physical | Framing, MAC addressing, medium access, and physical transmission of bits over the medium | Ethernet, Wi-Fi 802.11, PPP, HDLC, Frame Relay | Switch, bridge, hub, NIC, cable, repeater |

    ```mermaid
    graph TD
        A["Application layer: HTTP, HTTPS, FTP, SMTP, DNS, DHCP, SNMP, Telnet, SSH"] --> B["Transport layer: TCP, UDP"]
        B --> C["Internet layer: IP, ICMP, IGMP, ARP, OSPF, BGP"]
        C --> D["Network Access layer: Ethernet, Wi-Fi 802.11, PPP, HDLC"]
        D --> E["Physical medium: copper, fibre, radio"]
    ```

    - Encapsulation: Data at the Application layer becomes a Segment at Transport, a Packet at Internet, a Frame at Network Access, and finally Bits on the wire.
    - Compared with OSI, TCP/IP merges Application, Presentation and Session into one Application layer, and Data Link and Physical into one Network Access layer.
15. **Write down the OSI model.** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 404 (ET: N/A)]*


    Answer: The OSI model has seven layers, each providing a defined service to the layer above.

    | # | Layer | Function | PDU | Protocols and devices |
    |---|---|---|---|---|
    | 7 | Application | Provides the interface to the user's application: file transfer, mail, web, name lookup | Data | HTTP, HTTPS, FTP, SMTP, DNS, SNMP, Telnet |
    | 6 | Presentation | Translation of data format, encryption and decryption, compression | Data | SSL/TLS, JPEG, MPEG, ASCII, EBCDIC |
    | 5 | Session | Establishes, manages and terminates sessions, dialogue control and synchronisation checkpoints | Data | NetBIOS, RPC, PPTP, SQL sessions |
    | 4 | Transport | End to end delivery between processes, segmentation and reassembly, port addressing, flow and error control | Segment for TCP, Datagram for UDP | TCP, UDP, SCTP; gateway |
    | 3 | Network | Logical addressing, routing between different networks, path selection, fragmentation | Packet | IP, ICMP, IGMP, OSPF, RIP, BGP; router, layer 3 switch |
    | 2 | Data link | Gives reliable node to node delivery. It breaks data into frames with start and stop bits, uses MAC addresses for physical addressing, detects errors and asks for retransmission, and controls access to the medium so frames do not collide. It has two sublayers: LLC, which handles flow and error control, and MAC, which handles hardware addressing | Frame | Ethernet, PPP, PPTP, HDLC, ARP; switch, bridge, NIC |
    | 1 | Physical | Sends raw bits as electrical, optical or radio signals. It gives bit synchronisation through a clock, sets the bit rate, and defines the topology (bus, star, mesh) and the transmission mode (simplex, half-duplex, full-duplex) | Bit | USB, SONET/SDH, RS-232, DSL; hub, repeater, modem, cable |

    From top to bottom:
    - 7. Application
    - 6. Presentation
    - 5. Session
    - 4. Transport
    - 3. Network
    - 2. Data Link
    - 1. Physical

    - Mnemonic, top down: All People Seem To Need Data Processing. Bottom up: Please Do Not Throw Sausage Pizza Away.
16. **How many TCP/IP layer? Write its Layer name?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*


    Answer: The TCP/IP model has 4 layers.

    From top to bottom:
    - 4. Application layer
    - 3. Transport layer
    - 2. Internet layer
    - 1. Network Access layer, also called the Link or Network Interface layer

    - A five layer hybrid version is also taught, in which the Network Access layer is split into a separate Data Link layer and Physical layer.
17. **Differentiate between OSI Model and TCP/IP Model. Draw the diagram of 4 Layers of TCP/IP Model including the main function of each layer and related protocols. List some basic functions performed at MAC layer.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 530 (ET: MIST)]*


    Answer:

    OSI model vs TCP/IP model:

    | Point | OSI model | TCP/IP model |
    |---|---|---|
    | Number of layers | 7 | 4, or 5 in the hybrid form |
    | Developed by | ISO, in 1984 | DARPA, in the 1970s |
    | Nature | A theoretical reference model | A practical model built from working protocols |
    | Order of creation | The model came first, the protocols afterwards | The protocols came first, the model was described afterwards |
    | Layer separation | Presentation and Session are separate layers | Both are merged into the Application layer |
    | Data link and Physical | Two separate layers | Merged into one Network Access layer |
    | Protocol dependence | Protocol independent, a generic standard | Protocol dependent, built around TCP and IP |
    | Transport layer service | Both connection oriented and connectionless | Both, TCP and UDP |
    | Network layer service | Both connection oriented and connectionless | Connectionless only |
    | Usage | Used for teaching, design and troubleshooting | Used in the real Internet |
    | Reliability of the model | More detailed and clearer, but never implemented as a whole | Less clear in its layering, but proven in practice |

    - The relationship in one line: OSI is the theory used to explain and troubleshoot networks, and TCP/IP is the practice actually running on them.

    Four layers of the TCP/IP model, with functions and protocols:

    ```mermaid
    graph TD
        A["Application layer: HTTP, HTTPS, FTP, SMTP, DNS, DHCP, SNMP, Telnet, SSH"] --> B["Transport layer: TCP, UDP"]
        B --> C["Internet layer: IP, ICMP, IGMP, ARP, OSPF, BGP"]
        C --> D["Network Access layer: Ethernet, Wi-Fi 802.11, PPP, HDLC"]
        D --> E["Physical medium: copper, fibre, radio"]
    ```

    | Layer | Corresponding OSI layers | Function | Protocols | Devices |
    |---|---|---|---|---|
    | Application | Application, Presentation, Session | Provides network services directly to the user's programs: web, mail, file transfer, name resolution | HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH | Proxy server, application firewall, gateway |
    | Transport | Transport | End to end delivery between processes, port addressing, segmentation, reliability, flow and congestion control | TCP, UDP, SCTP | Gateway, layer 4 load balancer |
    | Internet | Network | Logical addressing, routing between networks, packet forwarding, fragmentation | IP, ICMP, IGMP, ARP, RARP, OSPF, BGP | Router, layer 3 switch |
    | Network Access, that is Link | Data link, Physical | Framing, MAC addressing, medium access, and physical transmission of bits over the medium | Ethernet, Wi-Fi 802.11, PPP, HDLC, Frame Relay | Switch, bridge, hub, NIC, cable, repeater |

    Basic functions performed at the MAC layer:
    - Framing: adding the header and trailer to build a frame from the packet handed down by the network layer.
    - Physical addressing: inserting the source and destination MAC addresses so the frame reaches the right device on the local link.
    - Medium access control: deciding which station may transmit and when, using CSMA/CD on wired Ethernet and CSMA/CA on wireless.
    - Collision handling: detecting a collision, sending a jam signal and applying binary exponential backoff.
    - Error detection: computing and checking the CRC in the frame trailer, and discarding a corrupted frame.
    - Frame delimiting and synchronisation, using the preamble and the start frame delimiter.
    - Flow control between two directly connected devices, and Ethernet PAUSE frames.
    - Filtering and forwarding decisions in a switch, based on the learned MAC address table.
    - VLAN tagging with 802.1Q, and quality of service marking with 802.1p.
18. **What is OSI Model? Write all layer name sequence should be top to bottom or bottom to top.** *[DESCO Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)]*


    Answer: The OSI model, Open Systems Interconnection, is a seven layer reference model developed by ISO in 1984 that describes how data travels from an application on one machine to an application on another, dividing the task into seven independent layers, each serving the layer above it.

    Layer names from top to bottom:
    - 7. Application
    - 6. Presentation
    - 5. Session
    - 4. Transport
    - 3. Network
    - 2. Data Link
    - 1. Physical

    Layer names from bottom to top:
    - 1. Physical
    - 2. Data Link
    - 3. Network
    - 4. Transport
    - 5. Session
    - 6. Presentation
    - 7. Application

    - Which direction to write depends on the question: data being sent travels top to bottom, and data being received travels bottom to top. Both orders are correct as long as the numbering is kept consistent.
19. **Difference between OSI model and TCP/IP model. Relation between Data, Segment, Packet and Bit in OSI model.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 510 (ET: MIST)]*


    Answer:

    Difference between OSI and TCP/IP:

    | Point | OSI model | TCP/IP model |
    |---|---|---|
    | Number of layers | 7 | 4, or 5 in the hybrid form |
    | Developed by | ISO, in 1984 | DARPA, in the 1970s |
    | Nature | A theoretical reference model | A practical model built from working protocols |
    | Order of creation | The model came first, the protocols afterwards | The protocols came first, the model was described afterwards |
    | Layer separation | Presentation and Session are separate layers | Both are merged into the Application layer |
    | Data link and Physical | Two separate layers | Merged into one Network Access layer |
    | Protocol dependence | Protocol independent, a generic standard | Protocol dependent, built around TCP and IP |
    | Transport layer service | Both connection oriented and connectionless | Both, TCP and UDP |
    | Network layer service | Both connection oriented and connectionless | Connectionless only |
    | Usage | Used for teaching, design and troubleshooting | Used in the real Internet |
    | Reliability of the model | More detailed and clearer, but never implemented as a whole | Less clear in its layering, but proven in practice |

    - The relationship in one line: OSI is the theory used to explain and troubleshoot networks, and TCP/IP is the practice actually running on them.

    Relation between Data, Segment, Packet and Bit:
    - These are the Protocol Data Units of successive layers, and each is the previous one wrapped in a new header. This process is called encapsulation.

    | OSI layer | PDU name |
    |---|---|
    | Application, Presentation, Session | Data or message |
    | Transport | Segment for TCP, Datagram for UDP |
    | Network | Packet, also called a datagram |
    | Data link | Frame |
    | Physical | Bit |

    - The chain when sending: the application produces Data; the transport layer adds a TCP or UDP header with port numbers, making a Segment; the network layer adds an IP header with the addresses, making a Packet; the data link layer adds a MAC header and a CRC trailer, making a Frame; and the physical layer converts the frame into Bits, that is signals on the medium.
    - At the receiver the reverse happens, decapsulation, each layer stripping its own header and passing the remainder upwards.
    - So Data, Segment, Packet, Frame and Bit are not different things; they are the same user information seen at successive layers with progressively more headers attached.
20. **(a) List down the layers of OSI model in top-down manner.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 480 (ET: N/A)]*


    Answer: Layers of the OSI model in top-down order:

    From top to bottom:
    - 7. Application
    - 6. Presentation
    - 5. Session
    - 4. Transport
    - 3. Network
    - 2. Data Link
    - 1. Physical

    - Mnemonic, top down: All People Seem To Need Data Processing. Bottom up: Please Do Not Throw Sausage Pizza Away.
21. **Fill up the following protocol table by work at which layer?** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 452 (ET: BUET)]*
| Protocol Name | Layer |
|---|---|
| Carrier-Sense Multiple Access (CSMA) |  |
| Open Shortest Path First (OSPF) |  |
| Transmission Control Protocol (TCP) |  |
| Routing Information Protocol (RIP) |  |
| User datagram protocol (UDP) |  |


    Answer:

    | Protocol Name | Layer |
    |---|---|
    | Carrier-Sense Multiple Access (CSMA) | Data Link layer, layer 2, specifically the MAC sublayer |
    | Open Shortest Path First (OSPF) | Network layer, layer 3 |
    | Transmission Control Protocol (TCP) | Transport layer, layer 4 |
    | Routing Information Protocol (RIP) | Network layer, layer 3 |
    | User Datagram Protocol (UDP) | Transport layer, layer 4 |

    - CSMA is a medium access method, and medium access control is the lower sublayer of the data link layer.
    - OSPF and RIP are routing protocols, and routing is the defining function of the network layer. A fine point worth adding: OSPF is carried directly inside IP as protocol 89 while RIP is carried inside UDP on port 520, but both perform a network layer function, so layer 3 is the expected answer for both.
    - TCP and UDP provide end to end delivery between processes using port numbers, which is the transport layer.
22. **Which layer is used to link the network support layers and user support layers?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*


    Answer: The Transport layer, layer 4, links the network support layers to the user support layers.

    - The network support layers are Physical, Data Link and Network, layers 1 to 3, which are concerned with moving bits from one machine to another.
    - The user support layers are Session, Presentation and Application, layers 5 to 7, which are concerned with the interoperability of software.
    - The Transport layer sits between them and makes sure that the message delivered by the lower layers arrives complete, in order and at the correct process, so that the upper layers can work with it. This is why it is described as the bridge between the two groups.
23. **What is the number for the Network layer and the support layer?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*


    Answer:

    - The Network layer is layer 3 of the OSI model.
    - The network support layers are layers 1, 2 and 3, that is Physical, Data Link and Network.
    - The user support layers are layers 5, 6 and 7, that is Session, Presentation and Application.
    - Layer 4, the Transport layer, links the two groups together.
24. **(c) Write the all layers of OSI model.** *[BARC Programmer 04.08.2023 compact it 598 (ET: N/A)]*


    Answer: All the layers of the OSI model:

    | # | Layer | Function | PDU | Protocols and devices |
    |---|---|---|---|---|
    | 7 | Application | Provides the interface to the user's application: file transfer, mail, web, name lookup | Data | HTTP, HTTPS, FTP, SMTP, DNS, SNMP, Telnet |
    | 6 | Presentation | Translation of data format, encryption and decryption, compression | Data | SSL/TLS, JPEG, MPEG, ASCII, EBCDIC |
    | 5 | Session | Establishes, manages and terminates sessions, dialogue control and synchronisation checkpoints | Data | NetBIOS, RPC, PPTP, SQL sessions |
    | 4 | Transport | End to end delivery between processes, segmentation and reassembly, port addressing, flow and error control | Segment for TCP, Datagram for UDP | TCP, UDP, SCTP; gateway |
    | 3 | Network | Logical addressing, routing between different networks, path selection, fragmentation | Packet | IP, ICMP, IGMP, OSPF, RIP, BGP; router, layer 3 switch |
    | 2 | Data link | Gives reliable node to node delivery. It breaks data into frames with start and stop bits, uses MAC addresses for physical addressing, detects errors and asks for retransmission, and controls access to the medium so frames do not collide. It has two sublayers: LLC, which handles flow and error control, and MAC, which handles hardware addressing | Frame | Ethernet, PPP, PPTP, HDLC, ARP; switch, bridge, NIC |
    | 1 | Physical | Sends raw bits as electrical, optical or radio signals. It gives bit synchronisation through a clock, sets the bit rate, and defines the topology (bus, star, mesh) and the transmission mode (simplex, half-duplex, full-duplex) | Bit | USB, SONET/SDH, RS-232, DSL; hub, repeater, modem, cable |
25. **In order to prevent that the company decided to add end to end encryption techniques which layer of the OSI model is suitable to work in considering parameters like development time, software maintainability and development cost, Give reasons for your concepts.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 438 (ET: BIBM)]*


    Answer: The Presentation layer, layer 6, is the suitable place for end to end encryption.

    Reasons:
    - The Presentation layer exists precisely for data representation, that is translation, compression and encryption and decryption. Putting encryption there matches the model's own design intent, so the design is clean rather than a workaround.
    - True end to end protection: the data is encrypted before it leaves the sending host and decrypted only at the receiving host, so every intermediate router, switch and ISP sees only ciphertext. Encrypting at layer 2 or 3 would protect only one hop or one tunnel segment.
    - Development time: mature standard libraries already exist at this layer, notably SSL and TLS, so the team implements a well tested library rather than writing cryptography itself. This is the fastest route to a working, reviewed solution.
    - Software maintainability: encryption is written once at this layer and every application above it inherits the protection, so a change of algorithm or a key rotation is a single change in one place. If it were built into each application at layer 7, every application would have to be modified separately, and any application that was missed would leak plaintext.
    - Development cost: one shared implementation is far cheaper than either writing cryptography into every application or buying and operating dedicated hardware encryptors for the network layer.
    - Independence from the network: because it sits above the transport layer, it works unchanged over Ethernet, Wi-Fi, a leased line or the Internet, so no network equipment has to be replaced.
    - Comparison with the alternatives worth stating: IPsec at layer 3 is strong and transparent to applications but is a network wide project, needs router support and is harder to configure and troubleshoot; link encryption at layer 2 protects only a single link and leaves the data exposed at each intermediate node; and application layer encryption gives the finest control but multiplies development and maintenance cost across every application.
    - Practical note: in real systems TLS is described as sitting between the transport and application layers, and it is the concrete implementation of exactly this Presentation layer role, which is why HTTPS is the standard answer in practice.
26. **What is TCP/IP model? Briefly explain TCP/IP model.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 837 (ET: N/A)], [EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)]*


    Answer: The TCP/IP model, also called the Internet protocol suite or the DoD model, is the four layer architecture on which the Internet actually operates. It was developed by DARPA in the 1970s and named after its two core protocols, TCP and IP.

    | Layer | Corresponding OSI layers | Function | Protocols | Devices |
    |---|---|---|---|---|
    | Application | Application, Presentation, Session | Provides network services directly to the user's programs: web, mail, file transfer, name resolution | HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH | Proxy server, application firewall, gateway |
    | Transport | Transport | End to end delivery between processes, port addressing, segmentation, reliability, flow and congestion control | TCP, UDP, SCTP | Gateway, layer 4 load balancer |
    | Internet | Network | Logical addressing, routing between networks, packet forwarding, fragmentation | IP, ICMP, IGMP, ARP, RARP, OSPF, BGP | Router, layer 3 switch |
    | Network Access, that is Link | Data link, Physical | Framing, MAC addressing, medium access, and physical transmission of bits over the medium | Ethernet, Wi-Fi 802.11, PPP, HDLC, Frame Relay | Switch, bridge, hub, NIC, cable, repeater |

    ```mermaid
    graph TD
        A["Application layer: HTTP, HTTPS, FTP, SMTP, DNS, DHCP, SNMP, Telnet, SSH"] --> B["Transport layer: TCP, UDP"]
        B --> C["Internet layer: IP, ICMP, IGMP, ARP, OSPF, BGP"]
        C --> D["Network Access layer: Ethernet, Wi-Fi 802.11, PPP, HDLC"]
        D --> E["Physical medium: copper, fibre, radio"]
    ```

    Brief explanation of each layer:
    - Application layer: gives the user's programs direct access to network services. It combines the OSI Application, Presentation and Session layers, so formatting, encryption and session control are handled here too. Example: a browser issuing an HTTP GET.
    - Transport layer: delivers data from process to process using port numbers. TCP provides a reliable, ordered, connection oriented byte stream with flow and congestion control; UDP provides a fast connectionless datagram service with no guarantee.
    - Internet layer: gives every host a logical IP address and routes packets across different networks, choosing the path with the routing table and handling fragmentation and TTL.
    - Network Access layer: puts the packet into a frame with MAC addresses, controls access to the medium and finally transmits the bits as signals. It combines the OSI Data Link and Physical layers.
    - Encapsulation: Data becomes a Segment, then a Packet, then a Frame, then Bits, and the reverse at the receiver.
27. **(a) What is OSI model? Explain how two computers can exchange information using the OSI model.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 694 (ET: N/A)]*


    Answer: The OSI model, Open Systems Interconnection, is a seven layer reference model published by ISO in 1984 which describes how communication between two systems is divided into seven independent layers, each providing a defined service to the layer above and using the service of the layer below.

    | # | Layer | Function | PDU | Protocols and devices |
    |---|---|---|---|---|
    | 7 | Application | Provides the interface to the user's application: file transfer, mail, web, name lookup | Data | HTTP, HTTPS, FTP, SMTP, DNS, SNMP, Telnet |
    | 6 | Presentation | Translation of data format, encryption and decryption, compression | Data | SSL/TLS, JPEG, MPEG, ASCII, EBCDIC |
    | 5 | Session | Establishes, manages and terminates sessions, dialogue control and synchronisation checkpoints | Data | NetBIOS, RPC, PPTP, SQL sessions |
    | 4 | Transport | End to end delivery between processes, segmentation and reassembly, port addressing, flow and error control | Segment for TCP, Datagram for UDP | TCP, UDP, SCTP; gateway |
    | 3 | Network | Logical addressing, routing between different networks, path selection, fragmentation | Packet | IP, ICMP, IGMP, OSPF, RIP, BGP; router, layer 3 switch |
    | 2 | Data link | Gives reliable node to node delivery. It breaks data into frames with start and stop bits, uses MAC addresses for physical addressing, detects errors and asks for retransmission, and controls access to the medium so frames do not collide. It has two sublayers: LLC, which handles flow and error control, and MAC, which handles hardware addressing | Frame | Ethernet, PPP, PPTP, HDLC, ARP; switch, bridge, NIC |
    | 1 | Physical | Sends raw bits as electrical, optical or radio signals. It gives bit synchronisation through a clock, sets the bit rate, and defines the topology (bus, star, mesh) and the transmission mode (simplex, half-duplex, full-duplex) | Bit | USB, SONET/SDH, RS-232, DSL; hub, repeater, modem, cable |

    How two computers exchange information using the OSI model:
    - The process is called encapsulation on the way down and decapsulation on the way up. Each layer on the sending machine talks logically to the same layer on the receiving machine, which is called peer to peer communication, but physically the data travels down the stack, across the medium and back up.
    - At the sender, the application produces Data. The Presentation layer encrypts and formats it. The Session layer opens and marks the session.
    - The Transport layer breaks it into Segments, adds source and destination port numbers, sequence numbers and a checksum.
    - The Network layer adds the source and destination IP addresses, making a Packet, and decides the route.
    - The Data Link layer adds the source and destination MAC addresses of the next hop and a CRC trailer, making a Frame.
    - The Physical layer converts the frame into Bits and transmits them as electrical, optical or radio signals.
    - Along the way, a switch reads only the frame's MAC header, and a router strips the frame, reads the IP header, chooses the next hop, and builds a new frame. So intermediate devices work only up to their own layer.
    - At the receiver everything is reversed: the Physical layer recovers the bits, the Data Link layer checks the CRC and removes the frame header, the Network layer confirms the destination IP and removes the packet header, the Transport layer reorders the segments, acknowledges them and removes its header, and the Session, Presentation and Application layers restore the session, decrypt and finally hand the original Data to the receiving program.

    ```mermaid
    graph TD
        A["Sender: Application -> Presentation -> Session"] --> B["Transport: adds ports, makes Segment"]
        B --> C["Network: adds IP addresses, makes Packet"]
        C --> D["Data Link: adds MAC and CRC, makes Frame"]
        D --> E["Physical: transmits Bits over the medium"]
        E --> F["Receiver: Physical -> Data Link -> Network"]
        F --> G["Transport -> Session -> Presentation -> Application"]
    ```
28. **TCP/IP model এর Layer গুলোর কাজ লিখুন।** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 698 (ET: DPI)]*

    Answer: The four layers of the TCP/IP model and their functions:

    | Layer | Corresponding OSI layers | Function | Protocols | Devices |
    |---|---|---|---|---|
    | Application | Application, Presentation, Session | Provides network services directly to the user's programs: web, mail, file transfer, name resolution | HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH | Proxy server, application firewall, gateway |
    | Transport | Transport | End to end delivery between processes, port addressing, segmentation, reliability, flow and congestion control | TCP, UDP, SCTP | Gateway, layer 4 load balancer |
    | Internet | Network | Logical addressing, routing between networks, packet forwarding, fragmentation | IP, ICMP, IGMP, ARP, RARP, OSPF, BGP | Router, layer 3 switch |
    | Network Access, that is Link | Data link, Physical | Framing, MAC addressing, medium access, and physical transmission of bits over the medium | Ethernet, Wi-Fi 802.11, PPP, HDLC, Frame Relay | Switch, bridge, hub, NIC, cable, repeater |

    ```mermaid
    graph TD
        A["Application layer: HTTP, HTTPS, FTP, SMTP, DNS, DHCP, SNMP, Telnet, SSH"] --> B["Transport layer: TCP, UDP"]
        B --> C["Internet layer: IP, ICMP, IGMP, ARP, OSPF, BGP"]
        C --> D["Network Access layer: Ethernet, Wi-Fi 802.11, PPP, HDLC"]
        D --> E["Physical medium: copper, fibre, radio"]
    ```

    - Encapsulation: the unit is Data at the Application layer, a Segment at the Transport layer, a Packet at the Internet layer, a Frame at the Network Access layer, and finally Bits on the medium. At the receiving end the headers are removed in the reverse order.
29. **What is OSI model? Write different layers of OSI model.** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 699 (ET: BUET)]*


    Answer: The OSI model, Open Systems Interconnection, is a seven layer reference model developed by ISO in 1984. It divides the whole task of network communication into seven layers, each performing a specific function and serving the layer above it, so that systems from different vendors can interoperate.

    Different layers of the OSI model:

    | # | Layer | Function | PDU | Protocols and devices |
    |---|---|---|---|---|
    | 7 | Application | Provides the interface to the user's application: file transfer, mail, web, name lookup | Data | HTTP, HTTPS, FTP, SMTP, DNS, SNMP, Telnet |
    | 6 | Presentation | Translation of data format, encryption and decryption, compression | Data | SSL/TLS, JPEG, MPEG, ASCII, EBCDIC |
    | 5 | Session | Establishes, manages and terminates sessions, dialogue control and synchronisation checkpoints | Data | NetBIOS, RPC, PPTP, SQL sessions |
    | 4 | Transport | End to end delivery between processes, segmentation and reassembly, port addressing, flow and error control | Segment for TCP, Datagram for UDP | TCP, UDP, SCTP; gateway |
    | 3 | Network | Logical addressing, routing between different networks, path selection, fragmentation | Packet | IP, ICMP, IGMP, OSPF, RIP, BGP; router, layer 3 switch |
    | 2 | Data link | Gives reliable node to node delivery. It breaks data into frames with start and stop bits, uses MAC addresses for physical addressing, detects errors and asks for retransmission, and controls access to the medium so frames do not collide. It has two sublayers: LLC, which handles flow and error control, and MAC, which handles hardware addressing | Frame | Ethernet, PPP, PPTP, HDLC, ARP; switch, bridge, NIC |
    | 1 | Physical | Sends raw bits as electrical, optical or radio signals. It gives bit synchronisation through a clock, sets the bit rate, and defines the topology (bus, star, mesh) and the transmission mode (simplex, half-duplex, full-duplex) | Bit | USB, SONET/SDH, RS-232, DSL; hub, repeater, modem, cable |

    From top to bottom:
    - 7. Application
    - 6. Presentation
    - 5. Session
    - 4. Transport
    - 3. Network
    - 2. Data Link
    - 1. Physical

    - Mnemonic, top down: All People Seem To Need Data Processing. Bottom up: Please Do Not Throw Sausage Pizza Away.
30. **What is the difference between DOD and OSI model?** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 700 (ET: BUET)]*


    Answer: The DoD model is another name for the TCP/IP model, since it was developed by the United States Department of Defense through DARPA. So this question is the comparison between the TCP/IP and OSI models.

    | Point | OSI model | TCP/IP model |
    |---|---|---|
    | Number of layers | 7 | 4, or 5 in the hybrid form |
    | Developed by | ISO, in 1984 | DARPA, in the 1970s |
    | Nature | A theoretical reference model | A practical model built from working protocols |
    | Order of creation | The model came first, the protocols afterwards | The protocols came first, the model was described afterwards |
    | Layer separation | Presentation and Session are separate layers | Both are merged into the Application layer |
    | Data link and Physical | Two separate layers | Merged into one Network Access layer |
    | Protocol dependence | Protocol independent, a generic standard | Protocol dependent, built around TCP and IP |
    | Transport layer service | Both connection oriented and connectionless | Both, TCP and UDP |
    | Network layer service | Both connection oriented and connectionless | Connectionless only |
    | Usage | Used for teaching, design and troubleshooting | Used in the real Internet |
    | Reliability of the model | More detailed and clearer, but never implemented as a whole | Less clear in its layering, but proven in practice |

    - The relationship in one line: OSI is the theory used to explain and troubleshoot networks, and TCP/IP is the practice actually running on them.

    Layer mapping between the two:

    | OSI layers | DoD, that is TCP/IP layer |
    |---|---|
    | 7 Application, 6 Presentation, 5 Session | Application, sometimes called Process |
    | 4 Transport | Transport, sometimes called Host-to-Host |
    | 3 Network | Internet |
    | 2 Data Link, 1 Physical | Network Access, sometimes called Link |
31. **What is PDU?** *[BARC Data Entry Officer 10.09.2022 compact it 702 (ET: N/A)]*


    Answer: PDU stands for Protocol Data Unit. It is the name given to the unit of data handled at a particular layer of the protocol stack, that is the payload received from the layer above together with the header added by that layer.

    | OSI layer | PDU name |
    |---|---|
    | Application, Presentation, Session | Data or message |
    | Transport | Segment for TCP, Datagram for UDP |
    | Network | Packet, also called a datagram |
    | Data link | Frame |
    | Physical | Bit |

    - Each layer treats the whole PDU it receives from above as data and wraps it in its own header, which is called encapsulation. At the receiver each layer removes its own header, which is decapsulation.
    - A PDU generally has three parts: the header with control information, the payload or Service Data Unit received from above, and in some cases a trailer, as in the Ethernet CRC.
    - Knowing the PDU names matters in practice, because it tells you which device works where: a switch handles Frames, a router handles Packets, and a firewall may inspect Segments and Data.
32. **(খ) Computer network এর OSI 7-Layer গুলো উদাহরণসহ লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 767 (ET: N/A)]*

    Answer: The seven layers of the OSI model, with an example for each:

    | # | Layer | Function | PDU | Protocols and devices |
    |---|---|---|---|---|
    | 7 | Application | Provides the interface to the user's application: file transfer, mail, web, name lookup | Data | HTTP, HTTPS, FTP, SMTP, DNS, SNMP, Telnet |
    | 6 | Presentation | Translation of data format, encryption and decryption, compression | Data | SSL/TLS, JPEG, MPEG, ASCII, EBCDIC |
    | 5 | Session | Establishes, manages and terminates sessions, dialogue control and synchronisation checkpoints | Data | NetBIOS, RPC, PPTP, SQL sessions |
    | 4 | Transport | End to end delivery between processes, segmentation and reassembly, port addressing, flow and error control | Segment for TCP, Datagram for UDP | TCP, UDP, SCTP; gateway |
    | 3 | Network | Logical addressing, routing between different networks, path selection, fragmentation | Packet | IP, ICMP, IGMP, OSPF, RIP, BGP; router, layer 3 switch |
    | 2 | Data link | Gives reliable node to node delivery. It breaks data into frames with start and stop bits, uses MAC addresses for physical addressing, detects errors and asks for retransmission, and controls access to the medium so frames do not collide. It has two sublayers: LLC, which handles flow and error control, and MAC, which handles hardware addressing | Frame | Ethernet, PPP, PPTP, HDLC, ARP; switch, bridge, NIC |
    | 1 | Physical | Sends raw bits as electrical, optical or radio signals. It gives bit synchronisation through a clock, sets the bit rate, and defines the topology (bus, star, mesh) and the transmission mode (simplex, half-duplex, full-duplex) | Bit | USB, SONET/SDH, RS-232, DSL; hub, repeater, modem, cable |

    Example of each layer:
    - Physical: the voltage on a UTP cable, the light pulse in a fibre, or the radio signal of Wi-Fi. Devices: hub and repeater.
    - Data link: an Ethernet switch forwarding a frame to the port where 00:1A:2B:3C:4D:5E is located, and ARP finding a MAC address from an IP address.
    - Network: a router sending a packet destined for 8.8.8.8 out of its Internet interface, and the `ping` command, which uses ICMP.
    - Transport: a web session carried on TCP port 443, where a lost segment is retransmitted, and a DNS query carried on UDP port 53.
    - Session: a database session or a remote procedure call, which must be re-established after a disconnection.
    - Presentation: TLS encrypting the data, a JPEG image being decoded, or ZIP compression.
    - Application: a browser issuing an HTTP GET request, a mail client sending mail by SMTP, or a file transfer by FTP.
33. **Computer Network এ OSI Model এর Layer কয়টি?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

    Answer: The OSI model in computer networking has 7 layers.

    - From bottom to top: Physical, Data Link, Network, Transport, Session, Presentation and Application.
    - For comparison, the TCP/IP model has 4 layers: Network Access, Internet, Transport and Application.
34. **OSI Model এর কাজ কী? এর লেয়ারসমূহ কী কী?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 811 (ET: IBA)]*

    Answer:

    Function of the OSI model:
    - To give a standard reference framework for how two different systems should communicate, so that equipment from different manufacturers can interoperate.
    - To divide the complex process of communication into seven independent parts, so that each can be designed, built and upgraded separately.
    - To let each layer use the service of the layer below and offer a service to the layer above while hiding its internal working. Because of this abstraction, changing one layer does not force a change in the others.
    - To provide a systematic method of troubleshooting: start at layer 1 and work upward until the failing layer is identified.
    - To define the rules of encapsulation and decapsulation, so that each layer adds its header when sending and removes it when receiving.
    - To provide a common vocabulary, so that saying "this is a layer 3 problem" means the same thing to every engineer.

    Its layers:

    | # | Layer | Function | PDU | Protocols and devices |
    |---|---|---|---|---|
    | 7 | Application | Provides the interface to the user's application: file transfer, mail, web, name lookup | Data | HTTP, HTTPS, FTP, SMTP, DNS, SNMP, Telnet |
    | 6 | Presentation | Translation of data format, encryption and decryption, compression | Data | SSL/TLS, JPEG, MPEG, ASCII, EBCDIC |
    | 5 | Session | Establishes, manages and terminates sessions, dialogue control and synchronisation checkpoints | Data | NetBIOS, RPC, PPTP, SQL sessions |
    | 4 | Transport | End to end delivery between processes, segmentation and reassembly, port addressing, flow and error control | Segment for TCP, Datagram for UDP | TCP, UDP, SCTP; gateway |
    | 3 | Network | Logical addressing, routing between different networks, path selection, fragmentation | Packet | IP, ICMP, IGMP, OSPF, RIP, BGP; router, layer 3 switch |
    | 2 | Data link | Gives reliable node to node delivery. It breaks data into frames with start and stop bits, uses MAC addresses for physical addressing, detects errors and asks for retransmission, and controls access to the medium so frames do not collide. It has two sublayers: LLC, which handles flow and error control, and MAC, which handles hardware addressing | Frame | Ethernet, PPP, PPTP, HDLC, ARP; switch, bridge, NIC |
    | 1 | Physical | Sends raw bits as electrical, optical or radio signals. It gives bit synchronisation through a clock, sets the bit rate, and defines the topology (bus, star, mesh) and the transmission mode (simplex, half-duplex, full-duplex) | Bit | USB, SONET/SDH, RS-232, DSL; hub, repeater, modem, cable |
35. **Which layer data packet receive port from sender to destination? (a) Data link layer (b) Network layer (c) Transport layer (d) None** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*


    Answer: The correct option is (c) Transport layer.

    - The Transport layer, layer 4, adds the source and destination port numbers to the segment, and it is the port number that identifies which application or process the data belongs to at the destination.
    - TCP and UDP both carry a 16 bit source port and a 16 bit destination port in their headers, so a value from 0 to 65535 is possible.
    - The Network layer, layer 3, deals with IP addresses, which identify the host, not the process. The Data Link layer deals with MAC addresses, which identify the interface on the local link.
    - The combination of IP address and port number is called a socket, for example 192.168.1.10:443.
36. **What is OSI model? Write down the name of OSI model layer.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 837 (ET: N/A)]*


    Answer: The OSI model, Open Systems Interconnection, is a seven layer reference model published by ISO in 1984 which standardises how two different systems communicate, dividing the task into seven layers so that equipment from different vendors can interoperate.

    Names of the OSI model layers:

    From top to bottom:
    - 7. Application
    - 6. Presentation
    - 5. Session
    - 4. Transport
    - 3. Network
    - 2. Data Link
    - 1. Physical

    - Mnemonic, top down: All People Seem To Need Data Processing. Bottom up: Please Do Not Throw Sausage Pizza Away.

    | # | Layer | Function | PDU | Protocols and devices |
    |---|---|---|---|---|
    | 7 | Application | Provides the interface to the user's application: file transfer, mail, web, name lookup | Data | HTTP, HTTPS, FTP, SMTP, DNS, SNMP, Telnet |
    | 6 | Presentation | Translation of data format, encryption and decryption, compression | Data | SSL/TLS, JPEG, MPEG, ASCII, EBCDIC |
    | 5 | Session | Establishes, manages and terminates sessions, dialogue control and synchronisation checkpoints | Data | NetBIOS, RPC, PPTP, SQL sessions |
    | 4 | Transport | End to end delivery between processes, segmentation and reassembly, port addressing, flow and error control | Segment for TCP, Datagram for UDP | TCP, UDP, SCTP; gateway |
    | 3 | Network | Logical addressing, routing between different networks, path selection, fragmentation | Packet | IP, ICMP, IGMP, OSPF, RIP, BGP; router, layer 3 switch |
    | 2 | Data link | Gives reliable node to node delivery. It breaks data into frames with start and stop bits, uses MAC addresses for physical addressing, detects errors and asks for retransmission, and controls access to the medium so frames do not collide. It has two sublayers: LLC, which handles flow and error control, and MAC, which handles hardware addressing | Frame | Ethernet, PPP, PPTP, HDLC, ARP; switch, bridge, NIC |
    | 1 | Physical | Sends raw bits as electrical, optical or radio signals. It gives bit synchronisation through a clock, sets the bit rate, and defines the topology (bus, star, mesh) and the transmission mode (simplex, half-duplex, full-duplex) | Bit | USB, SONET/SDH, RS-232, DSL; hub, repeater, modem, cable |
37. **What is OSI and TCP/IP model and briefly explain?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 870-872 (ET: N/A)]*


    Answer:

    OSI model:
    - The Open Systems Interconnection model, published by ISO in 1984, is a seven layer theoretical reference model describing how communication should be divided between two systems. It was designed before its protocols, and it is used mainly for teaching, design and troubleshooting.

    | # | Layer | Function | PDU | Protocols and devices |
    |---|---|---|---|---|
    | 7 | Application | Provides the interface to the user's application: file transfer, mail, web, name lookup | Data | HTTP, HTTPS, FTP, SMTP, DNS, SNMP, Telnet |
    | 6 | Presentation | Translation of data format, encryption and decryption, compression | Data | SSL/TLS, JPEG, MPEG, ASCII, EBCDIC |
    | 5 | Session | Establishes, manages and terminates sessions, dialogue control and synchronisation checkpoints | Data | NetBIOS, RPC, PPTP, SQL sessions |
    | 4 | Transport | End to end delivery between processes, segmentation and reassembly, port addressing, flow and error control | Segment for TCP, Datagram for UDP | TCP, UDP, SCTP; gateway |
    | 3 | Network | Logical addressing, routing between different networks, path selection, fragmentation | Packet | IP, ICMP, IGMP, OSPF, RIP, BGP; router, layer 3 switch |
    | 2 | Data link | Gives reliable node to node delivery. It breaks data into frames with start and stop bits, uses MAC addresses for physical addressing, detects errors and asks for retransmission, and controls access to the medium so frames do not collide. It has two sublayers: LLC, which handles flow and error control, and MAC, which handles hardware addressing | Frame | Ethernet, PPP, PPTP, HDLC, ARP; switch, bridge, NIC |
    | 1 | Physical | Sends raw bits as electrical, optical or radio signals. It gives bit synchronisation through a clock, sets the bit rate, and defines the topology (bus, star, mesh) and the transmission mode (simplex, half-duplex, full-duplex) | Bit | USB, SONET/SDH, RS-232, DSL; hub, repeater, modem, cable |

    TCP/IP model:
    - The Internet protocol suite, developed by DARPA in the 1970s, is a four layer practical model built from protocols that already worked. It is what the Internet actually runs on.

    | Layer | Corresponding OSI layers | Function | Protocols | Devices |
    |---|---|---|---|---|
    | Application | Application, Presentation, Session | Provides network services directly to the user's programs: web, mail, file transfer, name resolution | HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH | Proxy server, application firewall, gateway |
    | Transport | Transport | End to end delivery between processes, port addressing, segmentation, reliability, flow and congestion control | TCP, UDP, SCTP | Gateway, layer 4 load balancer |
    | Internet | Network | Logical addressing, routing between networks, packet forwarding, fragmentation | IP, ICMP, IGMP, ARP, RARP, OSPF, BGP | Router, layer 3 switch |
    | Network Access, that is Link | Data link, Physical | Framing, MAC addressing, medium access, and physical transmission of bits over the medium | Ethernet, Wi-Fi 802.11, PPP, HDLC, Frame Relay | Switch, bridge, hub, NIC, cable, repeater |

    Comparison:

    | Point | OSI model | TCP/IP model |
    |---|---|---|
    | Number of layers | 7 | 4, or 5 in the hybrid form |
    | Developed by | ISO, in 1984 | DARPA, in the 1970s |
    | Nature | A theoretical reference model | A practical model built from working protocols |
    | Order of creation | The model came first, the protocols afterwards | The protocols came first, the model was described afterwards |
    | Layer separation | Presentation and Session are separate layers | Both are merged into the Application layer |
    | Data link and Physical | Two separate layers | Merged into one Network Access layer |
    | Protocol dependence | Protocol independent, a generic standard | Protocol dependent, built around TCP and IP |
    | Transport layer service | Both connection oriented and connectionless | Both, TCP and UDP |
    | Network layer service | Both connection oriented and connectionless | Connectionless only |
    | Usage | Used for teaching, design and troubleshooting | Used in the real Internet |
    | Reliability of the model | More detailed and clearer, but never implemented as a whole | Less clear in its layering, but proven in practice |

    - The relationship in one line: OSI is the theory used to explain and troubleshoot networks, and TCP/IP is the practice actually running on them.
38. **TCP/IP protocol suite -এর বিভিন্ন স্তরের নাম লিখুন? HTTPs কী? এর ব্যবহারের প্রয়োজনীয়তা সংক্ষেপে বর্ণনা করুন?** *[41th BCS 2021 compact it 882 (ET: N/A)]*

    Answer:

    Layers of the TCP/IP protocol suite:
    - Application layer
    - Transport layer
    - Internet layer
    - Network Access layer, also called the Link or Network Interface layer

    What HTTPS is:
    - HTTPS stands for HyperText Transfer Protocol Secure. It is ordinary HTTP carried inside an SSL/TLS encrypted channel. It runs on TCP port 443, whereas plain HTTP runs on port 80.
    - The browser first performs a TLS handshake with the server: it validates the server's digital certificate, the two sides agree a session key, and all subsequent data is encrypted with that key.

    Why HTTPS is necessary:
    - Confidentiality: passwords, card numbers, national identity numbers and other personal data are encrypted, so nobody in the middle can read them.
    - Integrity: if the data is altered in transit, TLS detects it, so pages and transactions cannot be tampered with.
    - Server authentication: the certificate proves that the site really is the bank's site and not an imitation, which makes phishing and man in the middle attacks far harder.
    - Safety on public Wi-Fi: on an open network everything sent over plain HTTP can be captured trivially, while HTTPS traffic cannot.
    - Legal and regulatory compliance: PCI DSS for online payments and data protection laws effectively make HTTPS mandatory.
    - User trust and search ranking: browsers mark HTTP sites as "Not Secure", and search engines rank HTTPS sites higher.
    - Modern protocols: HTTP/2 and HTTP/3, which are considerably faster, are in practice available only over HTTPS.
39. **বর্তমানে Hybrid network model জনপ্রিয় একটি মডেল। এই মডেলের পাঁচটি Layer হচ্ছে, Application, Transport, Physical, Data link and Network Layer। এদের কাজ দেওয়া আছে বামপাশের কলামে, ডানপাশের কলামে কাজ অনুসারে Layer গুলোর নাম লিখুন।** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 975-976 (ET: BUET)]*


    Answer: The five layers of the hybrid model, with the function that belongs to each.

    | Function described | Layer |
    |---|---|
    | Transmits raw bits as electrical, optical or radio signals; defines cable, connector, voltage and data rate | Physical |
    | Builds frames, adds MAC addresses, detects errors with CRC, controls access to the shared medium, hop to hop delivery | Data Link |
    | Assigns logical IP addresses, routes packets between different networks, selects the path, performs fragmentation | Network |
    | Process to process delivery using port numbers, segmentation and reassembly, reliability, flow and congestion control | Transport |
    | Provides network services directly to the user's programs, and handles formatting, encryption and session control | Application |

    Summary of the five layer hybrid model, from bottom to top:
    - Physical: bits on the medium. Devices: hub, repeater, cable.
    - Data Link: frames, MAC addressing, CRC. Protocols: Ethernet, PPP, ARP. Device: switch.
    - Network: packets, IP addressing, routing. Protocols: IP, ICMP, OSPF. Device: router.
    - Transport: segments, ports, reliability. Protocols: TCP, UDP.
    - Application: data, user services. Protocols: HTTP, FTP, SMTP, DNS.

    - This model is popular because it keeps the useful separation of Physical and Data Link from OSI while avoiding the Presentation and Session layers, which in practice are always implemented inside the application.
40. **Write down the functionality of OSI model.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1007-1008 (ET: DU)]*


    Answer: The functionality of the OSI model, layer by layer.

    | # | Layer | Function | PDU | Protocols and devices |
    |---|---|---|---|---|
    | 7 | Application | Provides the interface to the user's application: file transfer, mail, web, name lookup | Data | HTTP, HTTPS, FTP, SMTP, DNS, SNMP, Telnet |
    | 6 | Presentation | Translation of data format, encryption and decryption, compression | Data | SSL/TLS, JPEG, MPEG, ASCII, EBCDIC |
    | 5 | Session | Establishes, manages and terminates sessions, dialogue control and synchronisation checkpoints | Data | NetBIOS, RPC, PPTP, SQL sessions |
    | 4 | Transport | End to end delivery between processes, segmentation and reassembly, port addressing, flow and error control | Segment for TCP, Datagram for UDP | TCP, UDP, SCTP; gateway |
    | 3 | Network | Logical addressing, routing between different networks, path selection, fragmentation | Packet | IP, ICMP, IGMP, OSPF, RIP, BGP; router, layer 3 switch |
    | 2 | Data link | Gives reliable node to node delivery. It breaks data into frames with start and stop bits, uses MAC addresses for physical addressing, detects errors and asks for retransmission, and controls access to the medium so frames do not collide. It has two sublayers: LLC, which handles flow and error control, and MAC, which handles hardware addressing | Frame | Ethernet, PPP, PPTP, HDLC, ARP; switch, bridge, NIC |
    | 1 | Physical | Sends raw bits as electrical, optical or radio signals. It gives bit synchronisation through a clock, sets the bit rate, and defines the topology (bus, star, mesh) and the transmission mode (simplex, half-duplex, full-duplex) | Bit | USB, SONET/SDH, RS-232, DSL; hub, repeater, modem, cable |

    Overall functionality of the model itself:
    - It provides a standard framework so that equipment and software from different vendors can interoperate.
    - It breaks a complex problem into seven manageable parts, so each can be designed, built and upgraded independently.
    - Each layer hides its internal working from the others and offers only a defined service interface, so a change of technology in one layer, for example copper to fibre, does not disturb the rest.
    - It defines encapsulation and decapsulation: each layer adds its header when sending and removes it when receiving.
    - It gives a systematic method of troubleshooting, working upward from layer 1, and a common vocabulary for engineers.
41. **OSI Model এর Layer গুলো বর্ণনা করুন।** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019 (ET: N/A)]*

    Answer: The layers of the OSI model:

    | # | Layer | Function | PDU | Protocols and devices |
    |---|---|---|---|---|
    | 7 | Application | Provides the interface to the user's application: file transfer, mail, web, name lookup | Data | HTTP, HTTPS, FTP, SMTP, DNS, SNMP, Telnet |
    | 6 | Presentation | Translation of data format, encryption and decryption, compression | Data | SSL/TLS, JPEG, MPEG, ASCII, EBCDIC |
    | 5 | Session | Establishes, manages and terminates sessions, dialogue control and synchronisation checkpoints | Data | NetBIOS, RPC, PPTP, SQL sessions |
    | 4 | Transport | End to end delivery between processes, segmentation and reassembly, port addressing, flow and error control | Segment for TCP, Datagram for UDP | TCP, UDP, SCTP; gateway |
    | 3 | Network | Logical addressing, routing between different networks, path selection, fragmentation | Packet | IP, ICMP, IGMP, OSPF, RIP, BGP; router, layer 3 switch |
    | 2 | Data link | Gives reliable node to node delivery. It breaks data into frames with start and stop bits, uses MAC addresses for physical addressing, detects errors and asks for retransmission, and controls access to the medium so frames do not collide. It has two sublayers: LLC, which handles flow and error control, and MAC, which handles hardware addressing | Frame | Ethernet, PPP, PPTP, HDLC, ARP; switch, bridge, NIC |
    | 1 | Physical | Sends raw bits as electrical, optical or radio signals. It gives bit synchronisation through a clock, sets the bit rate, and defines the topology (bus, star, mesh) and the transmission mode (simplex, half-duplex, full-duplex) | Bit | USB, SONET/SDH, RS-232, DSL; hub, repeater, modem, cable |

    Description of each layer:
    - Physical layer: converts bits into electrical, optical or radio signals and puts them on the medium. It defines the cable type, the connector, the voltage levels, the data rate and the physical topology. Devices: hub, repeater, cable.
    - Data link layer: wraps the packet in a frame carrying the source and destination MAC addresses, detects errors with a CRC, and controls which station may use a shared medium. Devices: switch, bridge, network interface card.
    - Network layer: assigns logical IP addresses and routes packets between different networks, choosing the best path. Fragmentation and the TTL also belong here. Device: router.
    - Transport layer: delivers data from one process to another, adds port numbers, divides the data into segments, and in the case of TCP provides reliable delivery with flow and congestion control.
    - Session layer: establishes, maintains and terminates the session between two applications, and provides dialogue control and synchronisation checkpoints so that a broken transfer can be resumed.
    - Presentation layer: translates the data format, performs encryption and decryption, and compresses the data. SSL and TLS, JPEG and MPEG belong here.
    - Application layer: gives the user's programs access to network services such as the web, email, file transfer and name lookup.
42. **(d) What do you mean by network protocol? Compare TCP/IP protocol suite and OSI reference model.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1028 (ET: N/A)]*


    Answer:

    Network protocol:
    - A network protocol is an agreed set of rules that governs how two devices communicate over a network. Without a shared protocol two devices cannot understand each other even when they are physically connected.
    - It has three key elements: syntax, that is the format and structure of the data and the order of the fields; semantics, that is the meaning of each field and what action to take on it; and timing, that is when data may be sent and how fast.
    - Protocols are arranged in layers, each using the services of the one below, and the whole set is called a protocol suite, for example TCP/IP.
    - Examples: TCP, IP, HTTP, FTP, SMTP, DNS, ARP and OSPF.

    Comparison of the TCP/IP suite and the OSI reference model:

    | Point | OSI model | TCP/IP model |
    |---|---|---|
    | Number of layers | 7 | 4, or 5 in the hybrid form |
    | Developed by | ISO, in 1984 | DARPA, in the 1970s |
    | Nature | A theoretical reference model | A practical model built from working protocols |
    | Order of creation | The model came first, the protocols afterwards | The protocols came first, the model was described afterwards |
    | Layer separation | Presentation and Session are separate layers | Both are merged into the Application layer |
    | Data link and Physical | Two separate layers | Merged into one Network Access layer |
    | Protocol dependence | Protocol independent, a generic standard | Protocol dependent, built around TCP and IP |
    | Transport layer service | Both connection oriented and connectionless | Both, TCP and UDP |
    | Network layer service | Both connection oriented and connectionless | Connectionless only |
    | Usage | Used for teaching, design and troubleshooting | Used in the real Internet |
    | Reliability of the model | More detailed and clearer, but never implemented as a whole | Less clear in its layering, but proven in practice |

    - The relationship in one line: OSI is the theory used to explain and troubleshoot networks, and TCP/IP is the practice actually running on them.

    Layer mapping:

    | OSI layers | TCP/IP layer |
    |---|---|
    | 7 Application, 6 Presentation, 5 Session | Application |
    | 4 Transport | Transport |
    | 3 Network | Internet |
    | 2 Data Link, 1 Physical | Network Access |
43. **TCP/IP মডেলের Layers সমূহের কাজ সংক্ষেপে লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1042-1043 (ET: DPI)]*

    Answer: The four layers of the TCP/IP model and their functions, in brief:

    - Application layer: gives the user's programs direct access to network services such as web browsing, email, file transfer and name resolution. The work of the OSI Application, Presentation and Session layers is all done here, so data formatting, encryption and session control belong to this layer as well. Protocols: HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, DHCP, SNMP, Telnet, SSH.

    - Transport layer: delivers data from a process on one computer to a process on another. It uses port numbers to identify the application, divides large data into segments and reassembles them at the far end. TCP is reliable and connection oriented, providing sequence numbers, acknowledgements, retransmission, and flow and congestion control; UDP is fast and connectionless, offering no guarantee but with very little overhead.

    - Internet layer: gives every host a logical IP address and routes packets between different networks, selecting the best path. Longest prefix match in the routing table, decrementing the TTL and fragmentation are all done here. Protocols: IP, ICMP, IGMP, ARP, OSPF, RIP, BGP. Device: router.

    - Network Access layer: wraps the packet in a frame with source and destination MAC addresses, detects errors with a CRC, controls access to the shared medium, and finally converts the bits into electrical, optical or radio signals. The work of the OSI Data Link and Physical layers is combined here. Examples: Ethernet, Wi-Fi 802.11, PPP, HDLC. Devices: switch, network interface card, cable.

    - Encapsulation: Data at the Application layer, a Segment at the Transport layer, a Packet at the Internet layer, a Frame at the Network Access layer, and Bits on the medium.

## Networking Fundamentals & Terminology (23)

1. **Define Computer Network. Describe different types of Computer Networks.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*


   Answer: A computer network is a collection of two or more computing devices connected by a transmission medium so that they can exchange data and share resources such as files, printers and an Internet connection, following an agreed set of protocols.

   Types of computer network, classified by geographical area:

   - PAN, Personal Area Network: about 10 metres around one person, connecting that person's own devices. Uses Bluetooth, Zigbee, NFC or USB. Example: a phone paired with a headset and a smartwatch.
   - LAN, Local Area Network: one building or campus, up to a few kilometres. Privately owned, high speed of 1 to 10 Gbps, very low delay and low error rate. Uses Ethernet and Wi-Fi with switches and access points. Example: an office or a university network.
   - CAN, Campus Area Network: several nearby buildings under one organisation, larger than a LAN but smaller than a MAN.
   - MAN, Metropolitan Area Network: a whole city, roughly 5 to 50 km, often owned by an operator and shared by several organisations. Uses fibre, Metro Ethernet and formerly WiMAX. Example: a cable television network or a bank's branches across Dhaka.
   - WAN, Wide Area Network: a country or the whole world, with no distance limit. Usually leased from a carrier, lower speed per user, higher delay and higher error rate than a LAN. Uses leased lines, MPLS, SONET and satellite. Example: the Internet itself, or a bank's national network.
   - Additional types worth naming: SAN, a Storage Area Network for block level access to storage; VPN, a Virtual Private Network that tunnels a private network securely over the public Internet; WLAN for the wireless version of a LAN; and an intranet, which is an organisation's private internal network, with an extranet extending part of it to partners.

   Classification by architecture:
   - Client-server: dedicated servers provide services and clients consume them. Centralised control, better security and easier backup, but the server is a single point of failure and it costs more.
   - Peer to peer: every machine is both client and server. Cheap and simple, but hard to secure and to manage beyond about ten machines.
2. **(ক) IP address এবং MAC Address- এর মাঝে তুলনা করুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer:

   | Point | IP address | MAC address |
   |---|---|---|
   | Layer | Network layer, layer 3 | Data link layer, layer 2 |
   | Length | 32 bits for IPv4, 128 bits for IPv6 | 48 bits |
   | Format | 192.168.1.10 | 00:1A:2B:3C:4D:5E |
   | Assigned by | The administrator or DHCP | The manufacturer, burned into the NIC |
   | Nature | Logical and changeable | Physical and permanent |
   | Structure | Hierarchical, network part plus host part | Flat, the first 24 bits are the vendor OUI |
   | Scope | End to end across the whole Internet | Within one local network only |
   | Forwarded by a router | Yes | No |
   | Changes in transit | No, except under NAT | Yes, rewritten at every hop |
   | Resolved by | DNS, from a name to an address | ARP, from an IP address to a MAC address |
   | Command to view | `ipconfig` or `ip addr` | `ipconfig /all` or `ifconfig` |

   - How the two work together: the source and destination IP addresses stay the same for the whole journey, while the MAC addresses in the frame are rewritten at every hop. The IP address says where the packet must finally go, and the MAC address says which neighbouring device should receive it at this moment. ARP is the protocol that bridges the two.
3. **(ক) সংজ্ঞা লিখুন: (i) Propagation delay, (ii) Transmission delay.** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer:

   (i) Propagation delay:
   - Propagation delay is the time taken for a single bit of the signal to travel from the sender to the receiver across the medium.
   - Formula: Tp = distance / propagation speed. The speed is about 2 × 10⁸ m/s in cable and 3 × 10⁸ m/s in air or vacuum.
   - It depends only on the distance and the medium; it has nothing to do with the size of the data or the bandwidth.
   - Example: over a 2000 km cable, Tp = 2 × 10⁶ / 2 × 10⁸ = 10 ms.

   (ii) Transmission delay:
   - Transmission delay is the time taken to push the whole message onto the link, that is from the first bit to the last bit leaving the sender.
   - Formula: Tt = message size in bits / bandwidth in bps.
   - It depends on the size of the message and the bandwidth; it has nothing to do with the distance.
   - Example: a 1000 bit frame on a 1 Mbps link gives Tt = 1000 / 10⁶ = 1 ms.

   - Total delay = transmission + propagation + queuing + processing delay. On a LAN the transmission delay dominates, while on a satellite link or a long WAN the propagation delay dominates.
4. **Write short note: Network, Protocol, link, gateway, Node.** *[BREB Assistant Programmer 18.02.2023 compact it 470 (ET: N/A)]*


   Answer:

   Network:
   - A collection of two or more devices connected by a transmission medium so that they can exchange data and share resources such as files, printers and Internet access.
   - Classified by area as PAN, LAN, MAN and WAN, and by architecture as client-server or peer to peer.
   - Its purpose is resource sharing, communication, centralised data management and cost saving.

   Protocol:
   - A set of agreed rules that governs how two devices communicate, covering syntax, that is the format of the data; semantics, that is the meaning of each field and what action to take; and timing, that is when and how fast to send.
   - Without a common protocol two devices cannot understand each other even when physically connected.
   - Examples: TCP, IP, HTTP, FTP, SMTP, DNS and ARP. They are organised in layers, each layer using the services of the one below.

   Link:
   - The physical or logical connection between two directly connected nodes, that is the actual transmission path.
   - It may be guided, such as twisted pair, coaxial cable or fibre, or unguided, such as radio, microwave or satellite.
   - It may be point to point, joining exactly two devices, or multipoint, shared by several devices.

   Gateway:
   - A device or software that connects two networks using different protocols, architectures or data formats, and translates between them.
   - It can operate at any layer of the OSI model, up to the application layer, because translation may mean rebuilding the message entirely.
   - In everyday LAN usage the default gateway is the router interface a host uses to reach anything outside its own subnet.
   - Examples: a VoIP gateway between IP and the PSTN, an email gateway, an IoT gateway.

   Node:
   - Any device on a network that can send, receive or forward data and that has a network address.
   - End nodes are computers, phones, printers and servers; intermediate nodes are switches, routers and access points.
   - Every node needs a network interface, and in a mesh topology n nodes require n(n − 1)/2 links.
5. **(b) Define following terms: (i) Bandwidth (ii) Latency (iii) MAC Address (iv) IP address** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 491 (ET: N/A)]*


   Answer:

   (i) Bandwidth:
   - The maximum theoretical capacity of a link, that is the highest rate at which data can be carried. It is measured in bps, Mbps or Gbps for a digital link, and in Hz for an analog channel.
   - It is a fixed property of the medium and the technology, and it is always an upper limit; the throughput actually achieved is lower.

   (ii) Latency:
   - The total time taken for a message to travel from the source to the destination, also called delay.
   - Latency = transmission delay + propagation delay + queuing delay + processing delay.
   - Transmission delay is size divided by bandwidth, propagation delay is distance divided by signal speed, queuing delay is the waiting time in router buffers, and processing delay is the time each router spends examining the header.
   - Round trip time is the latency in both directions and is what `ping` reports. Jitter is the variation in latency, and it matters greatly for voice and video.

   (iii) MAC address:
   - The Media Access Control address, a 48 bit physical address permanently burned into the network interface card by its manufacturer, written as six hexadecimal pairs such as `00:1A:2B:3C:4D:5E`.
   - The first 24 bits are the vendor's Organisationally Unique Identifier and the last 24 bits identify the card.
   - It works at the data link layer, is flat and non-routable, and is used for delivery within a single local network.

   (iv) IP address:
   - A logical network layer address that identifies a device on a network and enables end to end routing across the Internet.
   - IPv4 is 32 bits in dotted decimal such as 192.168.1.10, and IPv6 is 128 bits in hexadecimal such as 2001:db8::1.
   - It is hierarchical, divided into a network part and a host part by the subnet mask, and it may be assigned statically or by DHCP.
   - It may be public, that is globally routable, or private, that is 10.x, 172.16 to 172.31 and 192.168.x, which need NAT to reach the Internet.
6. **Define networking and Internetworking. What are the different types of network? Explain in details.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 672 (ET: N/A)]*


   Answer:

   Networking:
   - Networking is the practice of connecting two or more computing devices through a transmission medium so that they can exchange data and share resources, using an agreed set of protocols. It covers the design, implementation and management of a single network.

   Internetworking:
   - Internetworking is the connecting of two or more distinct, and often dissimilar, networks so that they function as one larger network. It is done by routers and gateways operating at the network layer, using a common protocol, which in practice is IP.
   - The Internet itself is the largest example: millions of independent networks joined together, each keeping its own internal technology, whether Ethernet, Wi-Fi or a WAN link, while IP provides a common addressing and forwarding scheme above them.
   - Its purposes are to extend reach, to allow different technologies to interwork, and to divide a large network into manageable and separately administered parts.

   Types of network:

   - PAN, Personal Area Network: about 10 metres around one person, connecting that person's own devices. Uses Bluetooth, Zigbee, NFC or USB. Example: a phone paired with a headset and a smartwatch.
   - LAN, Local Area Network: one building or campus, up to a few kilometres. Privately owned, high speed of 1 to 10 Gbps, very low delay and low error rate. Uses Ethernet and Wi-Fi with switches and access points. Example: an office or a university network.
   - CAN, Campus Area Network: several nearby buildings under one organisation, larger than a LAN but smaller than a MAN.
   - MAN, Metropolitan Area Network: a whole city, roughly 5 to 50 km, often owned by an operator and shared by several organisations. Uses fibre, Metro Ethernet and formerly WiMAX. Example: a cable television network or a bank's branches across Dhaka.
   - WAN, Wide Area Network: a country or the whole world, with no distance limit. Usually leased from a carrier, lower speed per user, higher delay and higher error rate than a LAN. Uses leased lines, MPLS, SONET and satellite. Example: the Internet itself, or a bank's national network.
   - Additional types worth naming: SAN, a Storage Area Network for block level access to storage; VPN, a Virtual Private Network that tunnels a private network securely over the public Internet; WLAN for the wireless version of a LAN; and an intranet, which is an organisation's private internal network, with an extranet extending part of it to partners.
7. **Write short note: (i) web server (ii) ISP (iii) Router (iv) Search Engine** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 680 (ET: N/A)]*


   Answer:

   (i) Web server:
   - A server, that is both the hardware and the software, that stores website files and delivers them to browsers over HTTP and HTTPS, on ports 80 and 443.
   - It listens for requests, finds or generates the requested resource, and returns it with a status code such as 200 OK, 404 Not Found or 500 Internal Server Error.
   - It serves static content directly from disk and passes dynamic requests to an application layer such as PHP, Java or Node.js, which may in turn query a database.
   - It also handles TLS termination, virtual hosting of many sites on one machine, logging, compression and caching.
   - Examples: Apache, Nginx, Microsoft IIS and LiteSpeed.

   (ii) ISP:
   - An Internet Service Provider is an organisation that provides access to the Internet to homes and businesses, for a fee.
   - It is arranged in tiers: Tier 1 providers own global backbones and peer with each other without payment, Tier 2 providers buy transit and also peer, and Tier 3 providers are local access networks.
   - Services offered: broadband access over fibre, DSL or cable, leased lines, IP address allocation, DNS resolution, email and web hosting, and often domain registration and colocation.
   - In Bangladesh the chain runs from the submarine cable operator BSCPLC to the IIGs, then the NTTN operators, then the ISPs, and finally the subscriber.

   (iii) Router:
   - A network layer, layer 3, device that connects two or more different networks and forwards packets between them.
   - It reads the destination IP address, performs a longest prefix match in its routing table and sends the packet to the best next hop, decrementing the TTL at each hop.
   - It builds that table with static routes or dynamic protocols such as RIP, OSPF and BGP, and it blocks broadcasts, so each interface is a separate broadcast domain.
   - It usually also provides NAT, DHCP, ACL based filtering, QoS and WAN interfaces.

   (iv) Search engine:
   - A software system that searches the World Wide Web for information matching a user's query and returns a ranked list of results.
   - It works in three stages: crawling, where automated bots follow links and fetch pages; indexing, where the content is parsed and stored in an inverted index; and ranking, where an algorithm orders the matching pages by relevance and authority, using signals such as keywords, links, freshness and user location.
   - Examples: Google, Bing, DuckDuckGo and Yahoo.
8. **What is Interface protocol?** *[BARC Data Entry Officer 10.09.2022 compact it 703 (ET: N/A)]*


   Answer: An interface protocol is the agreed set of rules that governs how two adjacent components exchange information across the boundary between them.

   - In the OSI model each layer offers services to the layer above through a well defined service interface, and the rules of that exchange, that is what may be requested and what will be returned, form the interface protocol. The layer above does not need to know how the layer below does its work.
   - Between two networks or two systems, an interface protocol defines the format, timing and control signals used at the boundary, so that equipment from different vendors can interoperate.
   - Examples: RS-232 and USB define the interface between a computer and a peripheral; the UNI, User Network Interface, and NNI, Network Node Interface, in ATM and Frame Relay define the boundary between the customer and the carrier and between two carriers; and an API defines the interface between two software components.
   - The value of the idea is separation of concerns: as long as the interface stays fixed, either side may be redesigned independently, which is what makes layered network architecture work at all.
9. **(ক) সংজ্ঞা লিখুন: WWW, URL, HTTP, IP Address, Router.** *[Software Assistant Programmer 13.10.2022 compact it 708 (ET: N/A)]*

   Answer:

   WWW:
   - The World Wide Web is an information system of hypertext documents and resources, each identified by a URL and linked to others by hyperlinks. It runs over the Internet using HTTP or HTTPS. Tim Berners-Lee invented it at CERN in 1989. The Web and the Internet are not the same thing: the Internet is the underlying network infrastructure, and the Web is one service running on top of it.

   URL:
   - A Uniform Resource Locator is the complete address of a resource on the Internet. Its parts are the scheme (`https`), the host (`www.example.com`), the port (`:443`), the path (`/page/index.html`), the query string (`?id=10`) and the fragment (`#top`). Example: `https://www.example.com:443/page?id=10`.

   HTTP:
   - The HyperText Transfer Protocol is the application layer protocol that carries web pages and resources. It runs on TCP port 80, and HTTPS on port 443. It is a stateless request and response protocol, so cookies or sessions are needed to maintain state. Its main methods are GET, POST, PUT and DELETE, and its common status codes are 200 OK, 301 Moved Permanently, 404 Not Found and 500 Internal Server Error.

   IP address:
   - A logical network layer address that uniquely identifies a device on a network and makes end to end routing possible. IPv4 is 32 bits, for example 192.168.1.10, and IPv6 is 128 bits, for example 2001:db8::1. The subnet mask separates the network part from the host part. It may be public or private, and static or assigned by DHCP.

   Router:
   - A layer 3 device that connects two or more different networks and forwards packets between them. It reads the destination IP address, performs a longest prefix match in its routing table and selects the best next hop. It builds that table with RIP, OSPF or BGP. It blocks broadcasts, so each interface is a separate broadcast domain. It also provides NAT, DHCP, ACL filtering and WAN connectivity.
10. **What is computer network?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*


    Answer: A computer network is a collection of two or more computing devices connected together by a transmission medium so that they can exchange data and share resources, following an agreed set of protocols.

    - Its components are the devices themselves, the network interface cards, the transmission medium, the connecting devices such as switches and routers, and the protocols.
    - Purposes: sharing files, printers and an Internet connection; communication by email, chat and video; centralised data storage and backup; and reduced cost, since one resource serves many users.
    - Classified by area as PAN, LAN, MAN and WAN, and by architecture as client-server or peer to peer.
11. **What is SDN?** *[IDRA Assistant Network Administrator 2022 compact it 727 (ET: N/A)]*


    Answer: SDN, Software Defined Networking, is a network architecture in which the control plane is separated from the data plane and moved into a central software controller, so the whole network can be programmed and managed from one place.

    - In a traditional network every switch and router makes its own forwarding decisions, so a policy change means configuring each device individually. In SDN the devices become simple forwarding hardware and all the intelligence sits in the controller.
    - Three layers: the application layer holds the network applications and business logic; the control layer holds the SDN controller, such as OpenDaylight, ONOS or Ryu; and the infrastructure layer holds the switches and routers.
    - Two interfaces: the southbound API, usually OpenFlow, through which the controller programs the flow tables of the switches; and the northbound API, usually REST, through which applications tell the controller what they want.
    - Advantages: central control and a global view of the network, rapid provisioning, automation through software, vendor independence, easy implementation of complex policy and traffic engineering, and lower operating cost.
    - Disadvantages: the controller is a single point of failure and a high value target, so redundancy is essential; latency between the switch and the controller matters; and the skills required are different from traditional networking.
    - Uses: data centres, cloud providers, WAN traffic engineering such as Google's B4, and SD-WAN for enterprise branch connectivity. It is closely related to Network Function Virtualisation, NFV, which replaces dedicated appliances such as firewalls and load balancers with software.
12. **How to works networks?** *[IDRA Assistant Network Administrator 2022 compact it 727 (ET: N/A)]*


    Answer: A network works by breaking data into packets, addressing them, and passing them through a series of devices until they reach the destination, where they are reassembled.

    Step by step:
    - The application produces data, which the transport layer divides into segments and gives a port number so the right application receives it at the far end. TCP adds sequence numbers and acknowledgements for reliability; UDP does not.
    - The network layer wraps each segment in an IP packet carrying the source and destination IP addresses. This is the end to end address that stays the same all the way.
    - The data link layer wraps the packet in a frame carrying the source and destination MAC addresses of the next hop only, plus a CRC for error detection. ARP is used to find the MAC address that matches the next hop IP.
    - The physical layer converts the frame into signals, that is voltage on copper, light in fibre or radio waves, and puts it on the medium.
    - A switch reads the destination MAC and forwards the frame out of the correct port, using the table it built by learning source addresses.
    - If the destination is on another network, the frame goes to the default gateway. The router strips the frame, reads the destination IP, looks it up in its routing table using the longest prefix match, builds a new frame for the next hop and forwards it. This repeats at every router, and the TTL is decremented each time.
    - At the destination the process runs in reverse up the layers: the frame's CRC is checked, the packet is passed to the network layer, the segment to the transport layer, which reorders and acknowledges it, and the data is delivered to the application by port number.
    - Along the way DNS translates the name into an IP address, DHCP supplied the sender's address in the first place, and NAT may rewrite the address at the network edge.
13. **(খ) Address গুলির সংক্ষিপ্ত বর্ণনা দিন। (i) Port Number (ii) IP অ্যাড্রেস (iii) MAC অ্যাড্রেস।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 775 (ET: N/A)]*

    Answer:

    (i) Port Number:
    - A 16 bit number at the transport layer that identifies which application or service a packet belongs to. The range is 0 to 65535.
    - Three groups: well known ports from 0 to 1023 (HTTP 80, HTTPS 443, FTP 21, SSH 22, SMTP 25, DNS 53), registered ports from 1024 to 49151, and dynamic or ephemeral ports from 49152 to 65535, which a client chooses for itself at the moment of connection.
    - The IP address says which computer, and the port number says which program on that computer. The two together form a socket, for example 192.168.1.10:443.

    (ii) IP address:
    - A logical network layer address that uniquely identifies a device on a network and makes end to end routing possible.
    - IPv4 is 32 bits in dotted decimal, for example 192.168.1.10; IPv6 is 128 bits in hexadecimal, for example 2001:db8::1.
    - The subnet mask separates the network part from the host part, which is what makes the address hierarchical and routable.
    - It may be public or private, and it may be configured statically or leased by DHCP, so it is changeable.

    (iii) MAC address:
    - A 48 bit physical address at the data link layer, written permanently into the network interface card by its manufacturer and expressed as six hexadecimal pairs, for example 00:1A:2B:3C:4D:5E.
    - The first 24 bits are the manufacturer's Organisationally Unique Identifier and the last 24 bits identify the individual card.
    - It is flat and non-routable, used only for delivery within the local network, and it is replaced at every hop.
    - The ARP protocol finds the MAC address that corresponds to a given IP address.
14. **(i) নিচের MAC Address গুলো কোন ধরনের বের করুন। (a) 4C:23:10:4A:1A:2A (b) 45:24:56:2B:24:12 (c) FF:FF:FF:FF:FF:FF** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 788 (ET: N/A)]*

    Answer: The type of a MAC address is determined by the least significant bit of the first byte, called the I/G bit. If that bit is 0 the address is unicast, and if it is 1 the address is multicast or a group address. If all 48 bits are 1 the address is broadcast.

    (a) `4C:23:10:4A:1A:2A`
    - First byte 4C = 0100 1100 in binary. The least significant bit is 0, so this is a Unicast address.
    - The next bit, the U/L bit, is also 0, which means the address is universally administered, that is a globally unique address assigned by the manufacturer.
    - Answer: Unicast.

    (b) `45:24:56:2B:24:12`
    - First byte 45 = 0100 0101 in binary. The least significant bit is 1, so this is a Multicast or group address.
    - Answer: Multicast.

    (c) `FF:FF:FF:FF:FF:FF`
    - All 48 bits are 1, which is the Broadcast address. Every device on the local network accepts this frame.
    - Answer: Broadcast.

    | Address | First byte in binary | I/G bit | Type |
    |---|---|---|---|
    | 4C:23:10:4A:1A:2A | 0100 1100 | 0 | Unicast |
    | 45:24:56:2B:24:12 | 0100 0101 | 1 | Multicast |
    | FF:FF:FF:FF:FF:FF | 1111 1111 | 1, and all bits 1 | Broadcast |
15. **If you have a company of two branch in the same city and they are connected. Which connection is used between then? (a) LAN (b) MAN (c) WAN (d) NONE** *[BCC Assistant Programmer 12.02.2021 compact it 811 (ET: BUET)]*


    Answer: The correct option is (b) MAN, Metropolitan Area Network.

    - The two branches are in the same city, and a MAN is defined as a network covering a metropolitan area, roughly 5 to 50 km.
    - A LAN covers only one building or campus, so it is too small.
    - A WAN covers a country or the world, so it is larger than needed here, although in practice such a link is often bought as a WAN service from a carrier.
16. **Short Question: a) What are the protocol for connectionless and connection oriented? b) Why UTP cable are twisted? c) What are the main requirement of optical fiber splicing? d) Why use subnet mask? e) What the major difference between multicast and broadcast?** *[BPDB Assistant Engineer (CSE) 2021 compact it 816 (ET: BUET)]*


    Answer:

    (a) Protocols for connectionless and connection oriented:
    - Connectionless: UDP at the transport layer, and IP at the network layer. Also ICMP, ARP, DHCP, DNS and TFTP. Data is sent immediately with no setup and no guarantee.
    - Connection oriented: TCP at the transport layer, and SCTP. At the network level, virtual circuit technologies such as X.25, Frame Relay and ATM. A connection is established first, data flows in order, and the connection is then closed.

    (b) Why UTP cables are twisted:
    - To cancel electromagnetic interference. The two wires of a pair carry equal and opposite currents, so their magnetic fields cancel, and any external noise that reaches both wires equally is rejected as common mode noise at the differential receiver.
    - To reduce crosstalk between adjacent pairs. Each pair in the cable has a different twist rate, so no two pairs stay parallel for long and the coupling between them is minimised.
    - Without the twist the pair would act as an antenna, both radiating and receiving interference, and the usable distance and speed would collapse.

    (c) Main requirements of optical fibre splicing:
    - Clean and precise preparation: strip the coating, clean the fibre with alcohol, and cleave the end so the face is flat and exactly perpendicular, within about 1 degree.
    - Accurate core alignment, since the single mode core is only about 9 micron across; the fusion splicer aligns the cores automatically.
    - Matching fibre types, that is the same core diameter, refractive index profile and mode, on both sides.
    - Low splice loss and low back reflection: a good fusion splice loses about 0.02 to 0.1 dB, a mechanical splice about 0.2 to 0.5 dB.
    - Correct fusion arc current and time, so the glass melts and fuses without bubbles or bending.
    - Mechanical protection afterwards: a heat shrink splice protector, and secure mounting in a splice tray and closure.
    - Testing with an OTDR or a power meter to confirm the loss, and a clean and dust free working environment throughout.

    (d) Why a subnet mask is used:
    - To separate the network part of an IP address from the host part, which the address alone does not reveal in a classless network.
    - A host ANDs its own address with the mask to find its network address, and does the same with the destination address; if the two results match, the destination is local and the frame is sent directly, otherwise it is sent to the default gateway. This is the single most important decision a host makes for every packet.
    - It allows a large network to be divided into smaller subnets, which reduces broadcast domains, improves performance and security, and lets addresses be allocated efficiently with VLSM.
    - Routers use it in the longest prefix match to select the best route.

    (e) Major difference between multicast and broadcast:
    - Broadcast sends the packet to every device on the network segment, whether or not it wants the data. The destination is 255.255.255.255 or the subnet broadcast address, and the MAC address is FF:FF:FF:FF:FF:FF. Every host must process the frame, so bandwidth and CPU are wasted, and routers do not forward it.
    - Multicast sends the packet only to the devices that have joined a particular group. The destination is a class D address, 224.0.0.0 to 239.255.255.255, and membership is managed by IGMP. Only interested hosts process it, routers can forward it across networks, and one copy of a stream can serve thousands of receivers.
    - In short: broadcast is one to all and wasteful, multicast is one to many who asked and efficient. IPv6 has removed broadcast altogether and uses multicast in its place.
17. **Name of the Following figure:** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 880 (ET: BUET)]*
   Broadcast
   Unicast
   Multicast


    Answer: The three figures represent the three basic modes of data delivery.

    - Broadcast: one sender transmits to every device on the network segment. The destination address is 255.255.255.255 or the subnet broadcast address, and at layer 2 it is FF:FF:FF:FF:FF:FF. Every host must receive and process the frame. Routers do not forward broadcasts, so it is limited to one broadcast domain. Used by ARP and by DHCPDISCOVER.
    - Unicast: one sender transmits to exactly one receiver, using that receiver's own address. This is the normal one to one communication and it accounts for almost all Internet traffic, for example a web request or a file transfer.
    - Multicast: one sender transmits to a selected group of receivers who have joined that group. The address is a class D address in the range 224.0.0.0 to 239.255.255.255, and membership is managed by IGMP. Only the interested hosts process the packet, and the routers replicate the stream only where it is needed, so it is far more efficient than sending a separate unicast to each receiver. Used for IPTV, video conferencing, stock feeds and routing protocol updates.

    ```
    Unicast              Broadcast              Multicast
    S --> R1             S --> R1               S --> R1 (joined)
          R2                   R2                     R2 (joined)
          R3                   R3                     R3 (not joined, ignored)
    one to one           one to all             one to a group
    ```

    - The fourth mode, anycast, delivers the packet to the nearest member of a group of identically addressed servers, and is used by DNS root servers and CDNs.
18. **(i) Computer network কী? বিভিন্ন প্রকার Computer network সম্পর্কে আলোচনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 955-956 (ET: N/A)]*

    Answer: A computer network is a collection of two or more computing devices connected by a transmission medium so that they can exchange data and share resources, following an agreed set of protocols.

    - Purpose: sharing files, printers and an Internet connection; communication by email, chat and video; centralised data storage and backup; and reduced cost, since one resource serves many users.
    - Components: the devices themselves, network interface cards, the transmission medium, connecting devices such as switches and routers, and the protocols.

    Types of computer network, by geographical area:
    - PAN, Personal Area Network: about 10 metres around one person, connecting that person's own devices, using Bluetooth, Zigbee, NFC or USB. Example: a phone paired with a headset and a smartwatch.
    - LAN, Local Area Network: one building or campus, up to a few kilometres. Privately owned, high speed of 1 to 10 Gbps, very low delay and low error rate, using Ethernet and Wi-Fi with switches and access points. Example: an office or university network.
    - CAN, Campus Area Network: several nearby buildings belonging to one organisation, larger than a LAN and smaller than a MAN.
    - MAN, Metropolitan Area Network: a whole city, roughly 5 to 50 km, often owned by an operator and shared by several organisations, using fibre and Metro Ethernet. Example: a cable television network, or a bank's branches across Dhaka.
    - WAN, Wide Area Network: a country or the whole world, with no distance limit, usually leased from a carrier, with lower speed per user and higher delay than a LAN. Example: the Internet itself, or a bank's national network.
    - Other types: SAN for storage, VPN for a secure tunnel over the public Internet, WLAN for a wireless LAN, and an intranet for an organisation's private internal network.

    Types by architecture:
    - Client-server: dedicated servers provide services and clients consume them. Centralised control, better security and easier backup, but the server is a single point of failure and the cost is higher.
    - Peer to peer: every machine is both client and server. Cheap and simple, but hard to secure and to manage beyond about ten machines.
19. **What is difference between MAC Address and IP Address?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1018-1019 (ET: N/A)]*


    Answer:

    | Point | MAC address | IP address |
    |---|---|---|
    | Layer | Data link layer, layer 2 | Network layer, layer 3 |
    | Length | 48 bits, six hexadecimal pairs | 32 bits for IPv4, 128 bits for IPv6 |
    | Format | 00:1A:2B:3C:4D:5E | 192.168.1.10 |
    | Assigned by | The manufacturer, burned into the NIC | The network administrator or DHCP |
    | Nature | Physical and permanent | Logical and changeable |
    | Structure | Flat, the first 24 bits are the vendor OUI | Hierarchical, network part plus host part |
    | Scope | Within one local network only | End to end across the whole Internet |
    | Routable | No, a router does not forward it | Yes, this is what routers forward on |
    | Changes in transit | Rewritten at every hop | Stays the same from source to destination, except under NAT |
    | Resolved by | ARP, from an IP address to a MAC address | DNS, from a name to an IP address |
    | Command to view | `ipconfig /all` or `ifconfig` | `ipconfig` or `ip addr` |

    - How they work together: the source and destination IP addresses stay the same for the whole journey, while the MAC addresses in the frame are rewritten at every hop. So the IP address says where the packet is finally going, and the MAC address says which neighbouring device should receive it right now. ARP is the protocol that bridges the two.
20. **(b) List the factors that affect the performance of a network.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1027 (ET: N/A)]*


    Answer: Factors that affect the performance of a network:

    - Bandwidth: the capacity of the link. A link that is too narrow for the offered traffic becomes the bottleneck for everything behind it.
    - Latency or delay: made up of transmission delay, which is size divided by bandwidth; propagation delay, which is distance divided by signal speed; queuing delay in router buffers; and processing delay at each node.
    - Number of users and the traffic load. As utilisation rises above about 70 percent, queuing delay grows very sharply.
    - Congestion: when the offered load exceeds capacity, queues overflow, packets are dropped, retransmissions increase and throughput can collapse.
    - Transmission medium: fibre gives far better bandwidth, attenuation and noise immunity than copper or wireless.
    - Errors and packet loss: a high bit error rate forces retransmission, which consumes capacity twice over.
    - Network devices: the speed, memory and forwarding capacity of the switches and routers, and whether a hub is used instead of a switch.
    - Topology and design: a poor design creates unnecessary hops, single points of failure and traffic concentration.
    - Protocol overhead: header size, acknowledgements, window size and the bandwidth delay product. A small TCP window on a long fat link wastes most of the capacity.
    - Jitter: variation in delay, which is critical for voice and video even when the average delay is acceptable.
    - Distance and the number of hops between source and destination.
    - Interference and noise, especially on wireless links, and physical problems such as damaged cable or a bad connector.
    - Server and end device performance: a slow disk, a loaded CPU or a weak NIC limits throughput regardless of the network.
    - Security processing: encryption, firewall inspection and deep packet inspection all add delay.
    - Configuration errors: a duplex mismatch, a wrong MTU or a routing loop can destroy performance on an otherwise healthy network.
21. **(a) Write a brief history of the internet. How to access to the internet?** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1028-1029 (ET: N/A)]*


    Answer:

    Brief history of the Internet:
    - 1957: after the launch of Sputnik, the United States set up ARPA to advance defence research.
    - 1969: ARPANET became operational, connecting four universities, UCLA, Stanford Research Institute, UC Santa Barbara and the University of Utah. It used packet switching, the idea developed by Paul Baran and Donald Davies.
    - 1972: Ray Tomlinson invented email and chose the `@` symbol.
    - 1974: Vint Cerf and Bob Kahn designed TCP/IP, which is why they are called the fathers of the Internet.
    - 1983: ARPANET formally adopted TCP/IP on 1 January, the date usually taken as the birth of the Internet. DNS was introduced in 1984.
    - 1986: NSFNET was created as a high speed backbone linking supercomputer centres, and it gradually replaced ARPANET, which was retired in 1990.
    - 1989 to 1991: Tim Berners-Lee at CERN invented the World Wide Web, with HTML, HTTP and the first browser and web server.
    - 1993: the Mosaic graphical browser made the Web accessible to ordinary users, and commercial use grew rapidly.
    - 1995 onwards: full commercialisation, the growth of ISPs, search engines, e-commerce, broadband, mobile Internet, social media and cloud computing.
    - In Bangladesh, dial-up Internet arrived in 1996, and the country joined the SEA-ME-WE 4 submarine cable in 2006 and SEA-ME-WE 5 in 2017.

    How to access the Internet:
    - Dial-up over a telephone line with a modem, up to 56 kbps; obsolete now.
    - DSL and ADSL over the existing telephone line, a few Mbps, without blocking voice calls.
    - Cable Internet over the cable television coaxial network.
    - Fibre to the home, FTTH or GPON, which is the normal broadband service today, offering tens to hundreds of Mbps.
    - Leased line, a dedicated symmetric link with a guaranteed service level, used by banks and large offices.
    - Wireless: Wi-Fi from a local access point, and mobile data over 3G, 4G LTE or 5G.
    - Satellite, including modern low earth orbit services, for remote areas where no cable reaches.
    - WiMAX and other fixed wireless access in areas without cabling.
    - In every case the user needs a device, a modem or router, an account with an ISP, and the TCP/IP protocol stack with an IP address supplied by DHCP.
22. **(b) Define computer network. Sate some merits and demerits of a computer network.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1029 (ET: N/A)]*


    Answer: A computer network is a collection of two or more computing devices connected by a transmission medium so that they can exchange data and share resources, following an agreed set of protocols.

    Merits:
    - Resource sharing: one printer, scanner, storage array or Internet connection serves many users, which saves a great deal of money.
    - File sharing and central data storage, so everyone works on the same current version.
    - Communication: email, chat, voice and video conferencing, both inside and outside the organisation.
    - Centralised administration: software can be installed, updated and licensed centrally, and policy applied to everyone at once.
    - Centralised backup and easier disaster recovery.
    - Better security control through user accounts, permissions and auditing, which is impossible with isolated machines.
    - Reliability through redundancy: if one server or one path fails, another can take over.
    - Scalability: new users and new services can be added without redesigning everything.
    - Remote access, so staff can work from home or from a branch office.
    - Distributed processing, so a heavy computation can be shared across several machines.

    Demerits:
    - Initial cost of cabling, switches, routers, servers and software licences.
    - Skilled staff are needed to design, run and troubleshoot the network, and their salaries are a continuing cost.
    - Security risks: a network exposes every machine to viruses, worms, ransomware, unauthorised access and eavesdropping, and one infected machine can spread the problem to all.
    - Dependency: if the server or a key link fails, work stops for everyone, so a single point of failure becomes very costly.
    - Congestion and performance degradation as the number of users grows.
    - Privacy concerns, since an administrator can in principle see users' files and traffic.
    - Maintenance overhead: patching, monitoring, backup verification and hardware replacement never stop.
    - Distraction and misuse of the Internet connection during working hours.
23. **b) Two IP address map to same Ethernet address. Will both of them receive packets?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033 (ET: BUET)]*


    Answer: Yes, both will receive the packets, and this is not an error; it is a normal and deliberate configuration.

    - The mapping is one way. ARP maps an IP address to a MAC address, and many IP addresses may map to the same MAC address, but one MAC address cannot map to two different interfaces.
    - When a frame arrives, the NIC accepts it because the destination MAC matches, and passes it up to the IP layer. The IP layer then looks at the destination IP address in the packet header and decides which logical interface or service it belongs to. So both packets are received by the same machine, and the machine separates them by IP address.
    - Common situations where this happens deliberately:
    - IP aliasing, where one physical interface is given several IP addresses, for example `eth0` and `eth0:1`, so that one server can host several websites on different addresses.
    - A router or firewall interface holding a primary and a secondary address for two subnets on the same physical segment.
    - A virtualisation host or a load balancer presenting several service addresses on one NIC.
    - A machine that has both a static address and a DHCP address on the same card.
    - The reverse case is the problem: two different machines sharing the same MAC address would cause the switch's MAC table to flap between two ports and traffic would be delivered erratically. That is a genuine fault, and it is also how a MAC spoofing attack works.
    - So the answer is yes, both IP addresses receive their packets, because the delivery decision is made by MAC at layer 2 and then by IP at layer 3.

## Application Layer Protocols & Troubleshooting (DNS, DHCP, HTTPS) (19)

1. [http://BSCPL.bd.gov](http://BSCPL.bd.gov) is connected to multiple international ISPs, and users can successfully access other websites, but they are unable to access the [http://BSCPL.bd.gov](http://BSCPL.bd.gov) website. The network uses essential services such as DNS, DHCP, and HTTPS, each performing different functions in the communication process. Identify the roles of DNS, DHCP, and HTTPS, determine which component or configuration could be responsible for this site-specific failure, and explain the possible causes and troubleshooting steps. [BSCCPL AME 21-08-2026 (BUET)]


   Answer:

   Roles of the three services:
   - DNS, Domain Name System: translates the name in the URL into an IP address, over UDP port 53. Without it the browser has no address to connect to.
   - DHCP, Dynamic Host Configuration Protocol: gives each client its IP address, subnet mask, default gateway and DNS server addresses, over UDP ports 67 and 68. It affects whether a client can reach the network at all, not which particular site works.
   - HTTPS: carries the web page itself over TCP port 443, encrypted and authenticated by TLS using the server's certificate.

   Which component is responsible:
   - Since other websites work normally, DHCP is ruled out: the clients clearly have a valid address, gateway and DNS server, otherwise nothing at all would work.
   - The failure is specific to one site, so the fault lies in the DNS record for that domain, in the web server or its HTTPS configuration, or in a firewall or routing entry that concerns only that destination.

   Possible causes:
   - DNS: the A record for the domain is missing, wrong or expired; the zone was not updated after a server migration; the authoritative name server is down; the domain registration or its DNSSEC signature has expired; or a stale cached record is being served locally.
   - HTTPS and the web server: an expired or mismatched TLS certificate, a wrong certificate chain, TLS version mismatch, the web service stopped, or the server listening on port 80 but not 443.
   - Network: a firewall or ACL blocking port 443 to that specific server, an asymmetric routing problem, or the server's public IP not being advertised correctly by BGP to one of the ISPs while the users' traffic prefers that ISP.
   - Server side: the host is down, overloaded, or blocking the source IP range.

   Troubleshooting steps, in order:
   - `ping bscpl.bd.gov` and `ping 8.8.8.8` to separate a name problem from a reachability problem.
   - `nslookup bscpl.bd.gov` and `nslookup bscpl.bd.gov 8.8.8.8`, then `dig bscpl.bd.gov +trace`. If the public resolver answers but the local one does not, the fault is a stale local cache; flush it with `ipconfig /flushdns`.
   - Compare the returned IP with the address the server should actually have.
   - `tracert` to the returned IP to see where the path stops, which shows whether the problem is routing or the server itself.
   - `telnet <ip> 443` and `telnet <ip> 80` to test whether the ports are open, which separates a firewall block from a TLS problem.
   - `curl -Iv https://bscpl.bd.gov` to read the certificate and the HTTP status, and check the certificate expiry date in the browser.
   - Try the site over a second ISP or a mobile connection; if it works there, the problem is the route or the DNS of the first ISP.
   - Check the web server logs, the service status and the firewall and ACL rules on the server side.
   - Verify the domain registration and DNSSEC status with the registrar, since an expired domain or a broken DNSSEC chain gives exactly this symptom.
2. **Write down the DNS function.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1449 (ET: N/A)]*


   Answer: Functions of DNS, the Domain Name System:

   - Name to address resolution: it translates a human readable domain name such as `www.example.com` into the IP address that the network actually needs. This is the forward lookup and it uses A records for IPv4 and AAAA for IPv6.
   - Reverse resolution: it maps an IP address back to a name using PTR records in the `in-addr.arpa` zone, which is used for logging, verification and anti-spam checks.
   - Mail routing: MX records tell a sending mail server which host accepts mail for a domain.
   - Aliasing: CNAME records let one name point to another, so several services can share one host.
   - Name server delegation: NS records delegate a subdomain to another set of name servers, which is what makes the system hierarchical and distributed.
   - Load distribution and failover: several A records for one name, or weighted and geographic answers, spread users across several servers.
   - Service discovery: SRV records advertise which host and port provide a particular service, and TXT records carry SPF, DKIM and verification data.
   - Caching: every resolver caches answers for the TTL period, which is what makes the whole system fast and keeps the load on the root and TLD servers low.
   - It runs over UDP port 53 for ordinary queries, and TCP port 53 for zone transfers and large responses.

   The domain name space is a hierarchy with four levels:
   - Root level: the top of the whole DNS hierarchy. It is written as a dot at the end of a name, and it is where every lookup starts.
   - Top Level Domain (TLD): the level just below the root. It defines the extension, such as .com, .org, .net, .edu, or a country code such as .bd.
   - Second level domain: the registered name that comes before the TLD, such as `example` in example.com. It identifies one organisation inside that TLD.
   - Subdomain and hostname: names such as `www`, `mail` or `blog`, which organise the different parts of a site and point to particular servers.

   Three kinds of DNS server:
   - Root servers: they send the resolver on to the right TLD server.
   - TLD servers: they send the resolver on to the authoritative server of that domain.
   - Authoritative servers: they return the actual IP address.

   Recursive and iterative queries:
   - In a recursive query, the resolver fetches the complete answer on behalf of the client. The client asks once and waits for the final answer.
   - In an iterative query, each server gives the best information it has, or a referral to another server. The resolver then walks step by step towards the answer.

   Caching: a resolver stores DNS records for a while, so the same question does not have to be asked again. The TTL, Time To Live, says how many seconds a record may stay in the cache. After that, a fresh lookup is needed.
3. **Why does the Domain Name System (DNS) primarily use UDP as its transport layer protocol instead of TCP? Describe the sequence of events that take place during the DNS name resolution process when a user enters www.companybd.com into a web browser and presses Enter.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1421 (ET: E-Zone)]*


   Answer:

   Why DNS primarily uses UDP:
   - Speed and low overhead: a DNS query and its reply are a single small exchange. TCP would need a three way handshake before the query and a four way close after it, so the delay would be several times greater for the same data.
   - Header size: UDP's header is 8 bytes against TCP's 20, and there is no connection state to keep.
   - Server scalability: a busy resolver handles thousands of queries per second. With UDP the server keeps no per-connection state, so its memory and CPU cost stay low; with TCP each query would tie up a socket.
   - Retransmission is cheap at the application layer: if no reply arrives within a couple of seconds the resolver simply asks again, or asks the next server in its list. Rebuilding the whole query costs less than TCP's reliability machinery.
   - Message size: a normal DNS response fits inside 512 bytes, which UDP carries comfortably.
   - TCP is still used where UDP is unsuitable: for zone transfers, AXFR and IXFR, which are large and must be reliable, and for any response larger than 512 bytes when EDNS0 is not available, in which case the server sets the truncated bit and the resolver retries over TCP. DNS over TLS and DNS over HTTPS also use TCP.

   Sequence of events when a user types `www.companybd.com`:
   - The browser checks its own DNS cache, then the operating system cache and the hosts file. If the name is found, resolution stops here.
   - Otherwise the operating system's stub resolver sends a recursive query to the configured local DNS server, usually the ISP's resolver, over UDP port 53.
   - The local resolver checks its own cache. If it has the record and the TTL has not expired, it answers immediately.
   - If not, it queries a root server, which does not know the answer but returns a referral to the `.com` TLD name servers.
   - It queries a `.com` TLD server, which returns a referral to the authoritative name servers for `companybd.com`.
   - It queries the authoritative server, which returns the A record, that is the IP address of `www.companybd.com`.
   - The local resolver caches the answer for its TTL and returns it to the client, which also caches it.
   - The browser now opens a TCP connection to that IP address on port 443, completes the TLS handshake, sends an HTTP GET request and receives the page.

   ```mermaid
   sequenceDiagram
       participant B as Browser
       participant R as Local DNS Resolver / ISP
       participant Ro as Root Server
       participant T as TLD Server
       participant A as Authoritative Server
       B->>R: Query the domain name
       R->>Ro: Where is this TLD?
       Ro->>R: Referral to the TLD server
       R->>T: Where is this domain?
       T->>R: Referral to the authoritative server
       R->>A: What is the A record?
       A->>R: The IP address
       R->>B: The IP address, plus it caches for the TTL
   ```

   - Note the division of labour: the client makes one recursive query, and the resolver makes several iterative queries on its behalf.
4. **What is DHCP?** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*


   Answer: DHCP, the Dynamic Host Configuration Protocol, is an application layer protocol that automatically assigns IP configuration to hosts on a network.

   - It supplies the IP address, subnet mask, default gateway and DNS server addresses, and optionally the NTP server and domain name.
   - It runs over UDP, port 67 on the server and port 68 on the client, and uses the DORA exchange: DHCPDISCOVER, DHCPOFFER, DHCPREQUEST and DHCPACK.
   - Addresses are given on lease for a fixed period; the client renews at 50 percent of the lease and rebinds at 87.5 percent.
   - It removes the need for manual configuration and prevents duplicate address conflicts, which is essential for laptops, phones and guest devices.
5. **Which protocol is used by the ping tools?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: The `ping` tool uses ICMP, the Internet Control Message Protocol.

   - It sends an ICMP Echo Request, type 8, and waits for an ICMP Echo Reply, type 0, measuring the round trip time.
   - ICMP is a network layer protocol carried directly inside IP as protocol number 1; it does not use TCP or UDP and has no port number.
   - `traceroute` on Linux uses UDP with an increasing TTL, while `tracert` on Windows uses ICMP Echo with an increasing TTL, and both rely on the ICMP Time Exceeded message coming back from each hop.
6. **Which server can be used to dinamically assign IP address to the PCs is a LAN?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*


   Answer: A DHCP server is used to assign IP addresses dynamically to the PCs in a LAN.

   - It holds a pool, called a scope, of available addresses and leases one to each client along with the subnet mask, default gateway and DNS server addresses.
   - It works over UDP ports 67 and 68 using the DORA exchange, and it keeps a lease table so that no two hosts receive the same address.
   - If the server is on another subnet, a DHCP relay agent on the router forwards the client's broadcast to it as a unicast.
7. **Explain how do DHCP work?** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 565 (ET: N/A)], [BREB Assistant Programmer (AP) 21.02.2025 compact it 1335 (ET: N/A)]*


   Answer: DHCP works through a four message exchange known as DORA.

   ```mermaid
   sequenceDiagram
       participant C as Client (UDP 68)
       participant S as DHCP Server (UDP 67)
       C->>S: DHCPDISCOVER, broadcast from 0.0.0.0 to 255.255.255.255
       S->>C: DHCPOFFER, an address plus mask, gateway, DNS and lease time
       C->>S: DHCPREQUEST, broadcast, accepting one offer
       S->>C: DHCPACK, confirmed, the lease begins
   ```

   - DHCPDISCOVER: the client has no address yet, so it broadcasts a discover message to find any DHCP server on the link. The message carries its MAC address as the identifier.
   - DHCPOFFER: every server that hears the discover reserves a free address from its scope and offers it, together with the subnet mask, default gateway, DNS servers and lease duration.
   - DHCPREQUEST: the client selects one offer, normally the first to arrive, and broadcasts its choice so that the other servers know to release the addresses they had reserved.
   - DHCPACK: the chosen server confirms the assignment and the lease clock starts. If the address has meanwhile been taken, it replies DHCPNAK instead and the client begins again.

   Lease management:
   - At 50 percent of the lease, T1, the client unicasts a DHCPREQUEST to the same server to renew.
   - At 87.5 percent, T2, if there was no reply, it broadcasts a rebind request to any server.
   - When the lease expires the client must stop using the address and restart with DHCPDISCOVER.
   - DHCPRELEASE returns the address to the pool when the client shuts down cleanly.
   - If the server is on a different subnet, a DHCP relay agent, configured with `ip helper-address`, converts the client's broadcast into a unicast towards the server.
8. **SMTP, DNS, DHCP, NAT এর কাজ কি লিখ?** *[BTCL Junior Assistant Manager 2022 compact it 639 (ET: BUET)]*

   Answer:

   Function of SMTP:
   - SMTP stands for Simple Mail Transfer Protocol, and it is used to send email. It runs on TCP port 25, and on port 587 for client submission.
   - It is a push protocol: it carries the message from the sender's mail client to the sender's mail server, and then from one mail server to the next.
   - It uses simple text commands: HELO, MAIL FROM, RCPT TO, DATA and QUIT.
   - It is not used to receive mail; POP3 or IMAP is used for that.

   Function of DNS:
   - DNS stands for Domain Name System, and it translates a domain name into an IP address. It uses UDP port 53 for queries and TCP port 53 for zone transfers.
   - A forward lookup gives the IP address from the name, using A and AAAA records; a reverse lookup gives the name from the IP address, using PTR records.
   - MX records are used for mail routing, CNAME records for aliases, and NS records for delegation.
   - It is a hierarchical distributed database of root, TLD and authoritative servers, and caching is what makes the whole system fast.

   Function of DHCP:
   - DHCP stands for Dynamic Host Configuration Protocol, and it automatically gives a client its IP address, subnet mask, default gateway and DNS server addresses. It uses UDP ports 67 and 68.
   - It works through the DORA exchange: DHCPDISCOVER, DHCPOFFER, DHCPREQUEST and DHCPACK.
   - Addresses are given on lease, so an address can be reused when it is released and duplicate address conflicts are prevented.
   - It removes the need to configure every machine by hand, which is indispensable in a large network.

   Function of NAT:
   - NAT stands for Network Address Translation, and it converts a private IP address into a public IP address, and back again on the return path.
   - It lets thousands of private hosts share one public address, which conserves the scarce IPv4 space. In PAT, also called NAT overload, the hosts are distinguished by port number.
   - Internal addresses are not visible from outside, which gives a degree of security.
   - Its drawback is that it breaks true end to end connectivity and causes problems for protocols such as FTP and SIP that carry addresses in their payload.
9. **What is DNS? What is forward and reverse lookup DNS?** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 658 (ET: N/A)]*


   Answer:

   DNS:
   - The Domain Name System is a hierarchical, distributed database that translates human readable domain names into IP addresses and back.
   - It runs over UDP port 53 for queries and TCP port 53 for zone transfers, and its structure is root, then top level domains, then second level domains, then hosts.
   - It also provides MX records for mail, CNAME aliases, NS delegation, SRV service records and TXT records, and every answer is cached for its TTL.

   Forward lookup:
   - Converts a domain name into an IP address, which is the normal direction of use.
   - It uses the A record for IPv4 and the AAAA record for IPv6.
   - Example: a query for `www.example.com` returns 93.184.216.34.
   - Every web request, email delivery and application connection begins with a forward lookup.

   Reverse lookup:
   - Converts an IP address back into a domain name.
   - It uses the PTR record, held in the special `in-addr.arpa` zone for IPv4 and `ip6.arpa` for IPv6, with the octets written in reverse order.
   - Example: to look up 93.184.216.34 the resolver queries `34.216.184.93.in-addr.arpa`.
   - Uses: mail servers check that a sending IP has a matching PTR record as an anti-spam measure, server logs are made readable, and network troubleshooting and auditing rely on it.
   - The forward and reverse zones are maintained separately, so a name can resolve forward without a matching reverse record, which is a common cause of mail being rejected.
10. **What is ICMP, SMTP, POP server, Boot loader and Clustering?** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 659 (ET: N/A)]*


    Answer:

    ICMP:
    - Internet Control Message Protocol, a network layer protocol carried directly inside IP as protocol number 1, with no ports.
    - It reports errors and carries diagnostic messages rather than user data: Destination Unreachable, Time Exceeded, Redirect, Source Quench and Echo Request and Reply.
    - `ping` uses Echo Request and Echo Reply; `traceroute` relies on the Time Exceeded message returned when the TTL reaches zero.

    SMTP:
    - Simple Mail Transfer Protocol, TCP port 25, the protocol that sends and relays email.
    - It is a push protocol, moving the message from the client to its mail server and from one mail server to the next, using the commands HELO, MAIL FROM, RCPT TO, DATA and QUIT.
    - It does not retrieve mail; that is done by POP3 or IMAP.

    POP server:
    - A Post Office Protocol server, TCP port 110 or 995 with TLS, which stores incoming mail until the user collects it.
    - The client connects, authenticates, downloads the messages and, by default, the server then deletes them, so the mail lives on one device.
    - It is simple and needs little server storage, but it suits only single device use; IMAP is preferred when the same mailbox is read from a phone and a laptop.

    Boot loader:
    - A small program that runs after the BIOS or UEFI power on self test and loads the operating system kernel into memory, then transfers control to it.
    - It sits in the master boot record or the EFI system partition, may present a menu when several operating systems are installed, and passes parameters to the kernel.
    - Examples: GRUB and LILO on Linux, the Windows Boot Manager, and U-Boot on embedded systems.

    Clustering:
    - Connecting several independent servers so that they work together and appear to users as a single system.
    - High availability clustering: if one node fails, another takes over its work automatically, so service continues. This is what a bank's core system uses.
    - Load balancing clustering: incoming requests are spread across the nodes, so capacity grows with the number of nodes.
    - High performance computing clustering: many nodes work in parallel on one large computation.
    - Benefits are availability, scalability and better use of hardware; the costs are complexity, the need for shared storage or replication, and licensing.
11. **Write a command how to find DNS www.egcb.gov.bd and which protocol uses?** *[EGCB Assistant Engineer (CSE) 2022 compact it 716 (ET: BUET)]*


    Answer:

    Commands to find the DNS record of `www.egcb.gov.bd`:

    ```
    nslookup www.egcb.gov.bd
    nslookup -type=A www.egcb.gov.bd
    nslookup -type=MX egcb.gov.bd
    nslookup -type=NS egcb.gov.bd
    ```

    On Linux, the more detailed tools are:

    ```
    dig www.egcb.gov.bd
    dig www.egcb.gov.bd +short
    dig www.egcb.gov.bd +trace
    host www.egcb.gov.bd
    ```

    - `nslookup` works on both Windows and Linux; `dig` and `host` are the standard Linux tools, and `dig +trace` shows the whole resolution path from the root downwards.
    - To query a specific server instead of the configured one: `nslookup www.egcb.gov.bd 8.8.8.8`.

    Protocol used:
    - DNS uses UDP on port 53 for ordinary queries, because a query and its reply are one small exchange and the overhead of a TCP handshake would not be worth paying.
    - TCP on port 53 is used for zone transfers, AXFR and IXFR, and for any response larger than 512 bytes, where the server sets the truncated flag and the resolver retries over TCP.
    - At the network layer everything is carried over IP, and the browser's later connection to the web server uses TCP on port 80 or 443.
12. **For the following description of various IP networking protocols write down the protocol name and its full form in the following table:** *[BTCL Assistant Manager (Technical) 2021 compact it 764 (ET: BUET)]*


    Answer: The common IP networking protocols, their full forms and the description each matches.

    | Description | Protocol | Full form |
    |---|---|---|
    | Translates a domain name into an IP address | DNS | Domain Name System |
    | Automatically assigns IP configuration to hosts | DHCP | Dynamic Host Configuration Protocol |
    | Resolves an IP address to a MAC address on a LAN | ARP | Address Resolution Protocol |
    | Resolves a MAC address to an IP address, used by diskless machines | RARP | Reverse Address Resolution Protocol |
    | Reports errors and carries diagnostics, used by ping | ICMP | Internet Control Message Protocol |
    | Reliable connection oriented transport | TCP | Transmission Control Protocol |
    | Fast connectionless transport with no guarantee | UDP | User Datagram Protocol |
    | Transfers web pages, and its secure version | HTTP and HTTPS | HyperText Transfer Protocol, and Secure |
    | Transfers files between hosts | FTP | File Transfer Protocol |
    | Sends and relays email | SMTP | Simple Mail Transfer Protocol |
    | Downloads email to one device | POP3 | Post Office Protocol version 3 |
    | Reads and synchronises email across devices | IMAP | Internet Message Access Protocol |
    | Secure encrypted remote login | SSH | Secure Shell |
    | Manages and monitors network devices | SNMP | Simple Network Management Protocol |
    | Translates private addresses to public addresses | NAT | Network Address Translation |
    | Distance vector interior routing protocol | RIP | Routing Information Protocol |
    | Link state interior routing protocol | OSPF | Open Shortest Path First |
    | Path vector routing between autonomous systems | BGP | Border Gateway Protocol |
    | Manages multicast group membership | IGMP | Internet Group Management Protocol |
    | Synchronises clocks across a network | NTP | Network Time Protocol |
13. **(a) How does a browser retrieve IP address from URL?** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 794 (ET: N/A)]*


    Answer: The browser obtains the IP address from a URL through DNS resolution, in the following order.

    - Step 1, parse the URL. The browser splits `https://www.example.com/page` into the scheme `https`, the host `www.example.com`, and the path. Only the host part needs resolving.
    - Step 2, browser cache. The browser first checks its own internal DNS cache. If a valid entry exists, it is used immediately.
    - Step 3, operating system cache and hosts file. Next the OS resolver cache is checked, and the `hosts` file, which overrides DNS entirely.
    - Step 4, query the local resolver. If the name is still unknown, the stub resolver sends a recursive query over UDP port 53 to the DNS server that DHCP supplied, usually the ISP's resolver.
    - Step 5, the resolver's cache. If it holds the record within its TTL, it answers at once.
    - Step 6, root server. Otherwise the resolver asks a root server, which returns a referral to the servers for the top level domain, for example `.com`.
    - Step 7, TLD server. The resolver asks a `.com` server, which returns a referral to the authoritative name servers of `example.com`.
    - Step 8, authoritative server. The resolver asks one of them and receives the A record, the IPv4 address, or the AAAA record for IPv6.
    - Step 9, caching and return. The resolver caches the answer for its TTL and sends it to the client, which caches it too.
    - Step 10, connect. The browser opens a TCP connection to that IP address on port 443, performs the TLS handshake, and sends the HTTP request.

    ```mermaid
    sequenceDiagram
        participant B as Browser
        participant R as Local DNS Resolver / ISP
        participant Ro as Root Server
        participant T as TLD Server
        participant A as Authoritative Server
        B->>R: Query the domain name
        R->>Ro: Where is this TLD?
        Ro->>R: Referral to the TLD server
        R->>T: Where is this domain?
        T->>R: Referral to the authoritative server
        R->>A: What is the A record?
        A->>R: The IP address
        R->>B: The IP address, plus it caches for the TTL
    ```
14. **(d) What is DNS? “TCP/IP is used in DNS”- justify the statement.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 795 (ET: N/A)]*


    Answer:

    What DNS is:
    - The Domain Name System is a hierarchical, distributed database that translates human readable domain names into IP addresses, and back again through reverse lookup.
    - Its hierarchy is root, then top level domains such as `.com` and `.bd`, then second level domains, then subdomains and hosts.
    - It also carries MX records for mail, CNAME aliases, NS delegation records, SRV and TXT records, and every answer is cached for its TTL, which is what keeps the system fast.

    Justification that TCP/IP is used in DNS:
    - DNS is an application layer protocol of the TCP/IP suite, so by definition it runs on top of the TCP/IP stack and cannot work without it.
    - It uses UDP on port 53 for ordinary queries, and UDP is part of the TCP/IP transport layer. A query and its reply are small and self contained, so the low overhead of UDP is exactly what is wanted.
    - It uses TCP on port 53 where reliability or size demands it: for zone transfers between a primary and a secondary name server, AXFR and IXFR, and for any response larger than 512 bytes, where the server sets the truncated bit and the resolver retries over TCP.
    - Both UDP and TCP segments are carried inside IP datagrams, and the DNS servers themselves are identified by IP addresses, which the client learns from DHCP.
    - Finally, DNS exists to serve TCP/IP: the address it returns is used to open a TCP connection to the destination.
    - Therefore the statement is correct on both counts. DNS is a member of the TCP/IP protocol suite, and it uses both TCP and UDP over IP for its own operation.
15. **(b) How is Hierarchical DNS resolution done in Domain Naming System? Give an example resolution for xyz.uv.gov.bd domain name.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 802 (ET: N/A)]*


    Answer: DNS resolution is hierarchical because the name space itself is a tree, read from right to left, and each level delegates the level below it to another set of name servers.

    The hierarchy:
    - Root, written as the invisible trailing dot. There are 13 logical root server clusters worldwide.
    - Top level domain, here `.bd`, operated by the country's registry.
    - Second level, `gov.bd`, delegated to the government's name servers.
    - Third level, `uv.gov.bd`, delegated to that organisation's name servers.
    - Host, `xyz.uv.gov.bd`, the actual record.

    Resolution of `xyz.uv.gov.bd`:
    - The client's stub resolver sends one recursive query to the local DNS server and then waits.
    - The local resolver checks its cache. If any part of the chain is cached, it starts from there instead of the root.
    - It asks a root server for `xyz.uv.gov.bd`. The root does not know, but it returns a referral to the `.bd` TLD name servers.
    - It asks a `.bd` server, which returns a referral to the name servers for `gov.bd`.
    - It asks a `gov.bd` server, which returns a referral to the name servers for `uv.gov.bd`.
    - It asks a `uv.gov.bd` server, which is authoritative for the zone and returns the A record for `xyz`, that is the IP address.
    - The resolver caches every referral and the final answer for their TTLs, and returns the address to the client.

    ```mermaid
    graph TD
        R["Root servers"] -->|referral| B[".bd TLD servers"]
        B -->|referral| G["gov.bd name servers"]
        G -->|referral| U["uv.gov.bd name servers"]
        U -->|A record, the IP address| C["Local resolver, then the client"]
    ```

    - Note the division of labour: the client makes one recursive query, and the local resolver makes four iterative queries on its behalf. Caching means that the next user asking for anything under `uv.gov.bd` skips the root and TLD steps entirely.
16. **What is Web cashing? Why we use web cashing?** *[Sonali Bank Ltd. Officer IT 2021 compact it 908 (ET: N/A)]*


    Answer: Web caching is the storing of copies of web content closer to the user, so that later requests for the same content are served from the copy instead of from the origin server.

    Types:
    - Browser cache, on the user's own machine.
    - Proxy or forward cache, shared by all the users of an organisation or an ISP.
    - Reverse proxy cache, placed in front of the web server itself, for example Varnish or Nginx.
    - CDN, a content delivery network with edge servers distributed around the world.

    How it works:
    - The first request goes to the origin server, and the response is stored along with its expiry information, controlled by the `Cache-Control`, `Expires`, `ETag` and `Last-Modified` headers.
    - Later requests are answered from the cache if the copy is still fresh, which is a cache hit. If it has expired, the cache sends a conditional request, and the server may reply 304 Not Modified, so only the headers travel and not the whole object.

    Why web caching is used:
    - Faster page loading, because the content comes from a nearby cache instead of a distant server, so latency falls sharply.
    - Lower bandwidth consumption on the expensive upstream or international link, which matters greatly for an organisation in Bangladesh paying for IIG bandwidth.
    - Reduced load on the origin server, so it serves more users with the same hardware.
    - Better availability: a cached copy may still be served when the origin server or the link to it is temporarily down.
    - Lower cost, both in bandwidth charges and in server capacity.
    - Better scalability during traffic spikes, since the cache absorbs most of the repeated requests.
    - Limitations to mention: stale content if the expiry policy is wrong, difficulty with personalised or dynamic pages, and privacy concerns when a shared cache holds user specific content, which is why such responses are marked private or no-store.
17. **What is DNS Resolver?** *[Sonali Bank Ltd. Officer IT 2021 compact it 908-909 (ET: N/A)]*


    Answer: A DNS resolver is the client side component that takes a domain name and obtains its IP address by querying the DNS servers.

    - Stub resolver: the small library inside the operating system that applications call. It does not do the work itself; it sends one recursive query to the configured DNS server and waits for the final answer. Its server address comes from DHCP or is configured manually.
    - Recursive resolver, also called a caching resolver: the server that actually does the work, usually run by the ISP or a public provider such as 8.8.8.8 or 1.1.1.1. It queries the root, then the TLD, then the authoritative server, following referrals until it has the answer.
    - Caching: the resolver stores every answer for the duration of its TTL, so most queries are answered from cache without touching the root servers at all. This is what makes DNS fast and what keeps the global infrastructure viable.
    - It also handles negative caching for names that do not exist, retries and timeouts when a server does not answer, and DNSSEC validation where it is enabled.
    - In short: the stub resolver asks, the recursive resolver finds out, and the authoritative server knows.
18. **DNS server এবং DHCP server এর কাজ কী?** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 911 (ET: BUET)]*

    Answer:

    Function of a DNS server:
    - To translate a domain name into an IP address, for example `www.example.com` into 93.184.216.34. This is the forward lookup, using A records for IPv4 and AAAA for IPv6.
    - To perform reverse lookup, giving a name from an IP address using PTR records, which is used for mail server verification and for readable logs.
    - To provide MX records that say which server accepts mail for a domain, CNAME records for aliases, and NS records that delegate a subdomain to other name servers.
    - To maintain a hierarchical distributed database of root servers, TLD servers and authoritative servers.
    - To cache answers for their TTL, so that a later query does not have to travel the whole path again. This is what makes DNS fast and keeps the global infrastructure viable.
    - To distribute load and provide failover by returning several A records, or weighted and geographic answers.
    - It answers queries on UDP port 53 and performs zone transfers on TCP port 53.

    Function of a DHCP server:
    - To lease an IP address to a client automatically from a pool, called a scope.
    - To supply the subnet mask, the default gateway and the DNS server addresses along with it, and where required the NTP server and the domain name.
    - To run the DORA exchange: DHCPDISCOVER, DHCPOFFER, DHCPREQUEST and DHCPACK, over UDP ports 67 and 68.
    - To keep a lease table so that no two hosts receive the same address.
    - To return an address to the pool when its lease expires, so that a small pool can serve a far larger number of occasional users.
    - To hold reservations by MAC address, so that a printer or a server always receives the same address.
    - To let the gateway or DNS settings of the whole network be changed from one place instead of on every machine.

    - The difference in one line: DHCP gives the address, and DNS finds the address.
19. **দূরবর্তী কম্পিউটার সংযোগ এর জন্য কোন প্রোটোকল ব্যবহার করা হয়?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 944 (ET: N/A)]*

    Answer: Telnet and SSH are the protocols mainly used to connect to a remote computer.

    - SSH, Secure Shell, TCP port 22: encrypted remote login, so the username, the password and every command are protected. This is the standard today.
    - Telnet, TCP port 23: the older remote login protocol, but everything travels in plain text, so it is insecure and is now rarely used.
    - RDP, Remote Desktop Protocol, TCP port 3389: for graphical remote desktop access to Windows.
    - VNC, port 5900: platform independent graphical remote access.
    - FTP on port 21 and SFTP on port 22 are used to transfer files to and from a remote computer.

## Multiplexing & Bandwidth (18)

1. Five channels, each with a 100-kHz bandwidth, are to be multiplexed together. What is the minimum bandwidth of the link if there is a need for a guard band of 10 kHz between the channels to prevent interference? [SO IT 25-07-2026]


   Answer:

   Given:
   - 5 channels, each of 100 kHz bandwidth.
   - A guard band of 10 kHz is needed between adjacent channels.

   Step 1, total channel bandwidth:
   - 5 × 100 = 500 kHz

   Step 2, number of guard bands:
   - Guard bands are placed only between channels, so for 5 channels there are 5 − 1 = 4 guard bands.
   - 4 × 10 = 40 kHz

   Step 3, minimum link bandwidth:
   - Total = 500 + 40 = 540 kHz

   Final answer: the minimum bandwidth of the link is 540 kHz.

   ```
   |<-100->|10|<-100->|10|<-100->|10|<-100->|10|<-100->|
      Ch1   G    Ch2   G    Ch3   G    Ch4   G    Ch5
   Total = 500 kHz of channels + 40 kHz of guard bands = 540 kHz
   ```

   - The guard band is unused spectrum kept between adjacent channels so that a small drift or the skirt of one filter does not spill into the neighbouring channel and cause interference. This is a feature of FDM only; TDM needs no guard band because the channels are separated in time.
2. **ব্যান্ডউইথ (Bandwidth) বলতে কী বুঝায়?** *[সাধারণ জ্ঞান: বিজ্ঞান ও প্রযুক্তি, বিষয় কোড: ১০৪, মান: ৪০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer: Bandwidth means the data carrying capacity of a transmission channel, that is the maximum amount of data that can be sent in one second.

   - For an analog signal, bandwidth means the difference between the highest and the lowest frequency the channel can carry, and it is measured in Hertz. For example, a telephone line has a bandwidth of 3000 Hz, from 300 Hz to 3300 Hz.
   - For a digital signal, bandwidth means the maximum number of bits that can be sent in one second, and it is measured in bps, Kbps, Mbps or Gbps.
   - The greater the bandwidth, the more data can be sent at once, so video streaming or a large file transfer completes more quickly.
   - Bandwidth and throughput are not the same. Bandwidth is the maximum theoretical capacity, while throughput is the data rate actually achieved, which is always lower because of congestion, errors and protocol overhead.
   - An analogy: bandwidth is the width of a road, and throughput is the number of vehicles that actually pass along it in an hour.
3. **6.9 Five channels, each with a 100-kHz bandwidth, are to be multiplexed together. What is the minimum bandwidth of the link if there is a need for a guard band of 10 kHz between the channels to prevent interference?** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*


   Answer:

   Given:
   - 5 channels, each of 100 kHz bandwidth.
   - A guard band of 10 kHz is needed between adjacent channels.

   Step 1, total channel bandwidth:
   - 5 × 100 = 500 kHz

   Step 2, number of guard bands:
   - Guard bands are placed only between channels, so for 5 channels there are 5 − 1 = 4 guard bands.
   - 4 × 10 = 40 kHz

   Step 3, minimum link bandwidth:
   - Total = 500 + 40 = 540 kHz

   Final answer: the minimum bandwidth of the link is 540 kHz.

   ```
   |<-100->|10|<-100->|10|<-100->|10|<-100->|10|<-100->|
      Ch1   G    Ch2   G    Ch3   G    Ch4   G    Ch5
   Total = 500 kHz of channels + 40 kHz of guard bands = 540 kHz
   ```

   - The guard band is unused spectrum kept between adjacent channels so that a small drift or the skirt of one filter does not spill into the neighbouring channel and cause interference. This is a feature of FDM only; TDM needs no guard band because the channels are separated in time.
4. **Differentiate among TDM, FDM and WDM. How does working process in TDM?** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 511 (ET: MIST)]*


   Answer:

   | Point | FDM | TDM | WDM |
   |---|---|---|---|
   | Full form | Frequency Division Multiplexing | Time Division Multiplexing | Wavelength Division Multiplexing |
   | Divides | The bandwidth into frequency bands | The time into slots | The light spectrum into wavelengths |
   | Signal | Analog | Digital | Optical |
   | Medium | Copper, coaxial, radio | Copper, wireless, any digital link | Optical fibre only |
   | Concurrency | All channels transmit simultaneously on different frequencies | One channel at a time, in rotation | All wavelengths travel simultaneously in one fibre |
   | Separation | Guard band | Guard bit or framing bit | Wavelength spacing, 0.8 nm for DWDM |
   | Equipment | Modulator, filter, carrier oscillator | Multiplexer with precise clock synchronisation | Prism or diffraction grating, or an AWG |
   | Capacity | Limited by the total bandwidth | Limited by the link bit rate | Very high, terabits per second |
   | Examples | Radio, TV, cable TV, ADSL | T-1, E-1, SONET, GSM, ISDN | Submarine cable, long haul backbone, PON |

   - WDM is really FDM applied to light: the difference is only that the carriers are wavelengths of light rather than radio frequencies.

   Working process of TDM:
   - The link's total time is divided into repeating frames, and each frame is divided into fixed time slots, one slot per input channel.
   - The multiplexer rotates through the input channels like a rotating switch, taking one unit of data, that is one bit or one byte, from each channel in turn and placing it in that channel's slot.
   - The slots are then sent one after another down the shared link, so at any instant the whole link bandwidth belongs to one channel.
   - At the far end the demultiplexer rotates in exact synchronism, taking the data out of each slot and delivering it to the correct output line. A framing bit added to each frame keeps the two ends in step.
   - Example, the T-1 carrier: 24 voice channels, each contributing 8 bits per frame, gives 192 bits, plus 1 framing bit makes 193 bits per frame; at 8000 frames per second this is 1.544 Mbps.
   - Two kinds: synchronous TDM, where every channel gets its slot whether or not it has data, so idle slots are wasted; and statistical or asynchronous TDM, where slots are allocated only to channels that actually have data, which is far more efficient but requires an address in each slot.
5. **Describe the different types of Multiplexing.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 554 (ET: BIBM)]*


   Answer: Multiplexing is the technique of combining several signals so that they can share one transmission link, with a multiplexer at the sending end and a demultiplexer at the receiving end.

   Types of multiplexing:

   - Frequency Division Multiplexing, FDM: the bandwidth of the link is divided into frequency bands and each signal is modulated onto its own carrier. All signals travel at the same time on different frequencies, separated by guard bands. It is analog in nature. Examples: radio and TV broadcast, cable TV, ADSL.
   - Wavelength Division Multiplexing, WDM: the optical version of FDM, where several wavelengths of light travel through one fibre at the same time and are combined and separated by prisms, gratings or arrayed waveguides. CWDM uses a few widely spaced wavelengths and DWDM uses dozens spaced only 0.8 nm apart. It gives terabits per second on one fibre and is used in submarine and backbone links.
   - Time Division Multiplexing, TDM: the time is divided into frames and slots, and each channel is given a slot in rotation, so at any instant the whole bandwidth belongs to one channel. It is digital in nature. It has two forms:
   - Synchronous TDM, where each channel gets its own fixed slot whether or not it has data, so idle slots are wasted. Examples: T-1, E-1, SONET, ISDN.
   - Statistical or asynchronous TDM, where slots are given only to channels that actually have data at that moment, so the link is used far more efficiently, at the cost of carrying an address in each slot.
   - Code Division Multiplexing, CDM or CDMA: every channel uses the whole bandwidth all the time, but each is multiplied by a unique orthogonal chip code. The receiver recovers its own channel by correlating with the same code. It resists jamming and interference well and is used in 3G mobile and in GPS.
   - Orthogonal Frequency Division Multiplexing, OFDM: a refined FDM in which the subcarriers are orthogonal and may therefore overlap, so no guard band is wasted. It resists multipath fading very well and is used in Wi-Fi, LTE, 5G, DSL and digital TV.
   - Space Division Multiplexing, SDM: separate physical paths are used, for example several fibres in one cable or several antennas in MIMO.
   - Polarisation Division Multiplexing: two signals share one wavelength using perpendicular polarisations of light, used in modern coherent optical systems.
6. **What technique allows simultaneous transmission of multiple signals across a single data link?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*


   Answer: The technique is called multiplexing.

   - Multiplexing allows several signals to be combined and carried simultaneously over a single data link, using a multiplexer at the sending end and a demultiplexer at the receiving end.
   - Its main forms are FDM, which divides the frequency; TDM, which divides the time; WDM, which divides the light spectrum in a fibre; and CDM, which separates the signals by orthogonal codes.
   - The purpose is efficiency: one expensive high capacity link is shared by many low rate users instead of laying a separate link for each.
7. **(খ) FDM এবং TDM এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 615 (ET: N/A)]*


   Answer:

   | Point | FDM | TDM |
   |---|---|---|
   | Sharing | The bandwidth is divided, each channel gets its own frequency band | The time is divided, each channel gets its own time slot |
   | Signal type | Suits analog signals | Suits digital signals |
   | Transmission | All channels transmit at the same time on different frequencies | Only one channel transmits at any instant, in turn |
   | Separation | Guard bands in frequency | Guard bits or a framing bit in time |
   | Equipment | Needs modulators, filters and carriers | Needs precise synchronisation between sender and receiver |
   | Interference | Crosstalk between adjacent bands is possible | No crosstalk, but a timing error corrupts everything |
   | Bandwidth use | The full bandwidth is needed all the time | The full bandwidth is given to one user at a time |
   | Efficiency | Wasted if a channel is idle | Synchronous TDM also wastes an idle slot, but statistical TDM does not |
   | Examples | Radio and TV broadcast, cable TV, ADSL, first generation mobile | T-1 and E-1 carriers, SONET, GSM, ISDN |

   - In short: in FDM every channel receives its own separate frequency band and all of them transmit at the same time, whereas in TDM every channel receives the whole bandwidth but only in turn, during its own time slot.
8. **Show that the data rate of T-1 carrier is 1.544 Mbps.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*


   Answer:

   Given: the T-1 carrier multiplexes 24 voice channels using synchronous TDM.

   Step 1, sampling rate of each voice channel:
   - A voice channel is limited to 4 kHz, so by the Nyquist theorem the sampling rate is 2 × 4000 = 8000 samples per second.

   Step 2, bits per sample:
   - Each sample is quantised into 8 bits by PCM.

   Step 3, bits per frame:
   - One frame carries one 8 bit sample from each of the 24 channels: 24 × 8 = 192 bits.
   - One extra framing bit is added for synchronisation: 192 + 1 = 193 bits per frame.

   Step 4, frame rate:
   - Since each channel is sampled 8000 times per second, 8000 frames must be sent per second.

   Step 5, data rate:
   - Data rate = 193 bits per frame × 8000 frames per second = 1,544,000 bps

   Final answer: the data rate of the T-1 carrier is 1,544,000 bps, that is 1.544 Mbps, which is what was to be shown.

   - Note: each channel therefore carries 8 × 8000 = 64 kbps, which is the standard DS-0 rate, and 24 × 64 kbps = 1.536 Mbps of payload plus 8 kbps of framing gives the 1.544 Mbps total. The European E-1 uses 32 slots instead and gives 2.048 Mbps.
9. **Suppose you are appointed as an Assistant Engineer in a Government organization. The number of telephone connections required for the organization is 1000. The per year increment of telephone connection is 100. Considering the life time of telephone equipment is to be 15 years, design a T-carrier based TDM system for the organization.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*


   Answer:

   Step 1, find the total number of connections over the equipment lifetime:
   - Present requirement = 1000 connections.
   - Growth = 100 connections per year.
   - Lifetime = 15 years, so growth over the lifetime = 100 × 15 = 1500.
   - Total capacity to be designed for = 1000 + 1500 = 2500 connections.

   Step 2, recall the T-carrier hierarchy:

   | Level | Voice channels | Data rate |
   |---|---|---|
   | DS-0 | 1 | 64 kbps |
   | T-1, DS-1 | 24 | 1.544 Mbps |
   | T-2, DS-2 | 96, that is 4 T-1 | 6.312 Mbps |
   | T-3, DS-3 | 672, that is 28 T-1 | 44.736 Mbps |
   | T-4, DS-4 | 4032, that is 6 T-3 | 274.176 Mbps |

   Step 3, number of T-1 lines required:
   - 2500 / 24 = 104.17, so 105 T-1 lines would be needed. This is far too many to manage individually.

   Step 4, choose a higher level of the hierarchy:
   - Using T-3, each carrying 672 channels: 2500 / 672 = 3.72, so 4 T-3 lines are required.
   - 4 T-3 gives 4 × 672 = 2688 channels, which covers the 2500 requirement with 188 spare channels, that is nearly two more years of growth beyond the fifteenth.
   - A single T-4, with 4032 channels, would also work but leaves 1532 channels idle, which is wasteful and costlier.

   Final design:
   - Provide 4 T-3 links, each of 44.736 Mbps, giving 2688 voice channels in all.
   - Each T-3 is formed by multiplexing 28 T-1 links, and each T-1 by multiplexing 24 DS-0 channels of 64 kbps.
   - Total capacity = 4 × 44.736 = 178.944 Mbps.

   ```mermaid
   graph LR
       A["2500 telephone lines, 64 kbps each DS-0"] --> B["T-1 multiplexers: 24 channels each, 1.544 Mbps"]
       B --> C["T-3 multiplexers: 28 T-1 each, 44.736 Mbps"]
       C --> D["4 x T-3 trunk to the exchange, 178.944 Mbps"]
   ```

   - Practical recommendation to add: since 4 T-3 links are needed anyway, a modern design would use a single SONET OC-3 at 155.52 Mbps or an OC-12 at 622 Mbps over fibre instead, which is cheaper per channel, easier to expand and gives built in protection switching.
10. **Compare between TDM and TDMA techniques.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 676 (ET: N/A)]*


    Answer:

    | Point | TDM | TDMA |
    |---|---|---|
    | Full form | Time Division Multiplexing | Time Division Multiple Access |
    | Nature | A multiplexing technique | A channel access, that is a MAC, method |
    | Where used | At one point, a multiplexer combining several inputs onto one link | Among many separate users sharing one medium |
    | Sources | All the inputs arrive at the same physical multiplexer | The users are physically separate and far apart |
    | Synchronisation | Simple, one local clock at the multiplexer | Difficult, every user must be synchronised to the base station, and guard time is needed for the different propagation delays |
    | Guard time | Not needed, only a framing bit | Essential, so that bursts from different distances do not overlap |
    | Slot assignment | Fixed at the time of configuration | Assigned dynamically by the base station on request |
    | Layer | Physical layer | Data link layer, MAC sublayer |
    | Example | T-1 and E-1 carriers, SONET | GSM, DECT, satellite uplink access |

    - The relationship in one sentence: TDMA is TDM applied to a shared radio or satellite medium where the users are geographically separated, so it has to add synchronisation, guard time and a request-and-grant mechanism that ordinary TDM does not need.
11. **Assume a TDMA based communication system having 8 transmission receiver pairs. Each source is sampled at 8KHz. That generates 16bits per sample if two synchronization bits are added to each frame calculate the data rate of TDMA line.** *[BDCCL Assistant Engineer (Network) 2022 compact it 742 (ET: N/A)], [Water Supply and Sewerage Authority (WASA); Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)], [BTCL Assistant Manager (Technical) 2021 compact it 765 (ET: BUET)]*


    Answer:

    Given:
    - 8 transmitter and receiver pairs, so 8 sources.
    - Each source is sampled at 8 kHz, that is 8000 samples per second.
    - Each sample produces 16 bits.
    - 2 synchronisation bits are added to each frame.

    Step 1, data rate of each source:
    - 8000 samples per second × 16 bits = 128,000 bps = 128 kbps

    Step 2, size of one frame:
    - Each frame carries one sample from each of the 8 sources: 8 × 16 = 128 bits
    - Plus 2 synchronisation bits: 128 + 2 = 130 bits per frame

    Step 3, frame rate:
    - Since each source is sampled 8000 times per second, 8000 frames must be sent per second.

    Step 4, data rate of the TDMA line:
    - 130 bits per frame × 8000 frames per second = 1,040,000 bps

    Final answer: the data rate of the TDMA line is 1,040,000 bps, that is 1.04 Mbps.

    - Check: the useful payload is 8 × 128 kbps = 1.024 Mbps and the overhead is 2 × 8000 = 16 kbps, and 1.024 + 0.016 = 1.04 Mbps, which agrees. The efficiency is 1.024 / 1.04 = 98.5 percent.
12. **Two channels, one with a bit rate of 190kbps and another with a bit rate 180 kbps are to be multiplexed using pulse stuffing TDM with no synchronization bits. Answer the following questions: (a) What is the size of a frame in bits? (b) What is the frame rate? (c) What is the duration of a frame? (d) What is the date rate?** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)]*


    Answer:

    Given: two channels of 190 kbps and 180 kbps, multiplexed by pulse stuffing TDM, no synchronisation bits.

    Principle: in pulse stuffing the slower channel has dummy bits inserted so that its rate is raised to match the fastest channel. So both channels are treated as 190 kbps.

    (a) Size of a frame in bits:
    - The interleaving unit is 1 bit, and there are 2 channels, so each frame takes 1 bit from each.
    - Frame size = 2 × 1 = 2 bits.

    (b) Frame rate:
    - Each channel must contribute 190,000 bits per second, and it contributes 1 bit per frame.
    - Frame rate = 190,000 frames per second.

    (c) Duration of a frame:
    - Duration = 1 / frame rate = 1 / 190,000 = 5.26 × 10⁻⁶ s = 5.26 microseconds.

    (d) Data rate of the link:
    - Data rate = frame size × frame rate = 2 × 190,000 = 380,000 bps = 380 kbps.

    Final answer: frame size 2 bits, frame rate 190,000 frames per second, frame duration 5.26 microseconds, and link data rate 380 kbps.

    - Note: the second channel really supplies only 180 kbps, so 10 kbps of the link is stuffed dummy bits. This waste is the price of using synchronous TDM with sources of unequal rate.
13. **What is Multiplexing? Write about Time division Multiplexing.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 870 (ET: N/A)]*


    Answer: Multiplexing is the technique of combining several separate signals so that they share a single transmission link, using a multiplexer at the sending end to combine them and a demultiplexer at the receiving end to separate them again.

    - Purpose: one high capacity link is expensive, so it is far cheaper to share it among many low rate users than to lay a separate link for each. It also reduces the number of cables, connectors and amplifiers.
    - Main types: FDM which divides the frequency, TDM which divides the time, WDM which divides the light spectrum in a fibre, CDM which separates signals by orthogonal codes, and OFDM which uses overlapping orthogonal subcarriers.

    Time Division Multiplexing:
    - TDM divides the transmission time into repeating frames, and each frame into fixed time slots, one per input channel.
    - The multiplexer acts like a rotating switch: it takes one unit of data, a bit or a byte, from each input in turn and places it in that channel's slot.
    - At any instant the entire link bandwidth belongs to one channel, so TDM suits digital signals which can be buffered and sent in bursts.
    - The demultiplexer at the far end rotates in exact synchronism and delivers each slot to the correct output. A framing bit in every frame keeps the two ends aligned.
    - Synchronous TDM: every channel gets its slot in every frame whether it has data or not, so an idle channel wastes its slot. Used in T-1, E-1, SONET and ISDN.
    - Statistical or asynchronous TDM: slots are given only to channels that actually have data, so the link is used much more efficiently, but each slot must then carry an address to say which channel it belongs to.
    - Example, T-1: 24 channels × 8 bits = 192 bits, plus 1 framing bit = 193 bits per frame, at 8000 frames per second = 1.544 Mbps.
    - Advantages: no crosstalk, simple digital circuitry, and full bandwidth for each user in its slot. Disadvantage: it needs precise synchronisation, and synchronous TDM wastes idle slots.
14. **(a) Distinguish between Frequency Division Multiplexing (FDM) and Time Division Multiplexing (TDM).** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 888 (ET: N/A)]*


    Answer:

    | Point | FDM | TDM |
    |---|---|---|
    | Sharing | The bandwidth is divided, each channel gets its own frequency band | The time is divided, each channel gets its own time slot |
    | Signal type | Suits analog signals | Suits digital signals |
    | Transmission | All channels transmit at the same time on different frequencies | Only one channel transmits at any instant, in turn |
    | Separation | Guard bands in frequency | Guard bits or a framing bit in time |
    | Equipment | Needs modulators, filters and carriers | Needs precise synchronisation between sender and receiver |
    | Interference | Crosstalk between adjacent bands is possible | No crosstalk, but a timing error corrupts everything |
    | Bandwidth use | The full bandwidth is needed all the time | The full bandwidth is given to one user at a time |
    | Efficiency | Wasted if a channel is idle | Synchronous TDM also wastes an idle slot, but statistical TDM does not |
    | Examples | Radio and TV broadcast, cable TV, ADSL, first generation mobile | T-1 and E-1 carriers, SONET, GSM, ISDN |
15. **TDM math: rate= 1.536 Mbps, message size= 960000, Slot=32, end to end circuit Switch time=800ms, calculate transfer time.** *[Sonali Bank Ltd. Officer IT 2021 compact it 910 (ET: N/A)]*


    Answer:

    Given:
    - Link rate = 1.536 Mbps.
    - The link is time division multiplexed into 32 slots, so each circuit gets one slot.
    - Message size = 960,000 bits.
    - End to end circuit establishment time = 800 ms = 0.8 s.

    Step 1, bandwidth available to one circuit:
    - Each circuit gets 1 / 32 of the link.
    - Rate per circuit = 1,536,000 / 32 = 48,000 bps = 48 kbps.

    Step 2, time to transmit the message:
    - Transmission time = message size / rate per circuit = 960,000 / 48,000 = 20 s.

    Step 3, total transfer time:
    - Total = circuit establishment time + transmission time = 0.8 + 20 = 20.8 s.

    Final answer: the total transfer time is 20.8 seconds.

    - Note: propagation delay is ignored here, as the question gives none. The important observation is that in a circuit switched network the user does not get the full 1.536 Mbps; the dedicated slot gives only 48 kbps, and the circuit setup time must be paid before any data can flow.
16. **A want to send 2 files the size of each file is 500000 bit's data to B through TDM channel which has slot 16 channel bit rate 1.5 Mbps and 30 millisecond delay time, if no propagation delay; find out time to send the data.** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 925 (ET: CTI)]*


    Answer:

    Given:
    - Two files of 500,000 bits each, so total data = 1,000,000 bits.
    - The TDM channel has 16 slots.
    - Channel bit rate = 1.5 Mbps = 1,500,000 bps.
    - Circuit establishment delay = 30 ms = 0.03 s, and there is no propagation delay.

    Step 1, bandwidth available to one circuit:
    - Rate per slot = 1,500,000 / 16 = 93,750 bps.

    Step 2, total data to be sent:
    - 2 × 500,000 = 1,000,000 bits.

    Step 3, transmission time:
    - Time = 1,000,000 / 93,750 = 10.67 s.

    Step 4, total time:
    - Total = setup delay + transmission time = 0.03 + 10.67 = 10.70 s.

    Final answer: the time required to send the data is about 10.70 seconds.

    - Note: if the two files were sent as two separate circuits, each with its own 30 ms setup, the total would be 0.03 + 0.03 + 10.67 = 10.73 s, which is practically the same, since the setup delay is negligible against the transmission time here.
17. **We have four sources, each creating 250 characters per second. If the interleaved unit is a character and 1 synchronizing bit is added to each frame. Now find- (a) the data rate of each source. (b) the duration of each character in each source.** *[BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)]*


    Answer:

    Given:
    - 4 sources, each producing 250 characters per second.
    - The interleaved unit is one character, that is 8 bits.
    - 1 synchronising bit is added to each frame.

    (a) Data rate of each source:
    - Each character is 8 bits, and there are 250 characters per second.
    - Data rate = 250 × 8 = 2000 bps = 2 kbps.

    (b) Duration of each character in each source:
    - Duration = 1 / character rate = 1 / 250 = 0.004 s = 4 ms.

    Additional results the examiner usually expects:
    - Frame size: each frame carries one character from each source, so 4 × 8 = 32 bits, plus 1 synchronising bit = 33 bits per frame.
    - Frame rate: 250 frames per second, since each source contributes one character per frame.
    - Frame duration: 1 / 250 = 4 ms, the same as the character duration.
    - Link data rate: 33 × 250 = 8250 bps.
    - Efficiency: useful data is 4 × 2000 = 8000 bps out of 8250 bps, that is 97 percent.
18. **Figure shows synchronous TOM with a data stream for each input and one data stream for the output. The unit of data is 1bit. Find (a) the input bit duration (b) the output bit duration (c) the output bit rate and (d) the output frame rate.** *[Janata Bank Ltd SO ( Assistant Network Engineer) 2020 compact it 1009 (ET: N/A)]*


    Answer: The relationships used for synchronous TDM, and the standard case shown in this figure, three inputs of 1 kbps each with 1 bit as the unit of data.

    Formulas:
    - Input bit duration = 1 / input bit rate.
    - Output bit rate = n × input bit rate, where n is the number of inputs.
    - Output bit duration = input bit duration / n.
    - Output frame rate = input bit rate, since each frame carries exactly one bit from each input.

    Applying them to three inputs of 1 kbps:

    (a) Input bit duration:
    - 1 / 1000 = 1 ms.

    (b) Output bit duration:
    - Each input bit must be squeezed into one third of the time, so 1 ms / 3 = 333 microseconds.

    (c) Output bit rate:
    - 3 × 1000 = 3000 bps = 3 kbps. Equivalently, 1 / 333 microseconds = 3 kbps.

    (d) Output frame rate:
    - Each frame carries 3 bits, one from each input, and each input supplies 1000 bits per second, so 1000 frames per second.

    - The general rule to remember: the frame rate always equals the bit rate of a single input, and the output bit rate is n times an input bit rate, so the multiplexer neither creates nor destroys data. <!-- verify -->

## Routing Protocols & Route Configuration (18)

1. A BGP router receives multiple routes to the same destination network from different neighboring autonomous systems. The available routes are given in the following table, containing Path, LOCAL_PREF, AS_PATH, ORIGIN, and MED values. Using the standard BGP best-path selection rules, analyze the attributes in the given order and determine which path will be selected as the best route, showing the comparison and justification for each step. [BSCCPL AME 21-08-2026 (BUET)]

| Path | LOCAL_PREF | AS_PATH | ORIGIN | MED |
|---|---|---|---|---|
| Path 1 | 200 | 65001 65010 | IGP | 50 |
| Path 2 | 150 | 65020 | IGP | 5 |
| Path 3 | 200 | 65030 65040 | IGP | 10 |
| Path 4 | 200 | 65050 65060 | IGP | 20 |


   Answer: BGP compares the attributes in a fixed order and stops at the first attribute that produces a single winner.

   Step 1, highest LOCAL_PREF wins:
   - Path 1 = 200, Path 2 = 150, Path 3 = 200, Path 4 = 200.
   - Path 2 is eliminated. Paths 1, 3 and 4 continue.

   Step 2, shortest AS_PATH wins:
   - Path 1 = 65001 65010, length 2. Path 3 = 65030 65040, length 2. Path 4 = 65050 65060, length 2.
   - All three are equal, so no decision. All continue.

   Step 3, lowest ORIGIN wins, where IGP is better than EGP which is better than Incomplete:
   - All three are IGP, so no decision. All continue.

   Step 4, lowest MED wins:
   - Path 1 = 50, Path 3 = 10, Path 4 = 20.
   - Path 3 has the lowest MED, so Path 3 is selected.

   Final answer: Path 3 is chosen as the best route, on the basis of the lowest MED of 10 among the paths that tied on LOCAL_PREF, AS_PATH length and ORIGIN.

   Full BGP best path order, for reference:
   - Highest weight, which is Cisco specific and local to the router.
   - Highest LOCAL_PREF.
   - Locally originated route, that is one injected by this router.
   - Shortest AS_PATH.
   - Lowest ORIGIN code: IGP, then EGP, then Incomplete.
   - Lowest MED.
   - eBGP preferred over iBGP.
   - Lowest IGP metric to the next hop.
   - Oldest route, for eBGP stability.
   - Lowest router ID, and finally the lowest neighbour IP address.

   - One caution worth writing: by the strict rule MED is compared only between paths received from the same neighbouring AS. Here the three paths come from different ASes, so a real router with the default configuration would skip MED and move on to the eBGP versus iBGP and IGP metric tie-breakers. The question asks for the attributes to be applied in the given order, so Path 3 is the intended answer, and `bgp always-compare-med` would make a real router behave that way too.
2. **Static route Configuration: Configure R0 to reach PC1 you can assume any Vendor, Cisco, Huawei, juniper** *[Islami Bank PLC Senior Officer (Network/System) 14.03.2025 compact it 1331 (ET: BUET)]*


   Answer: Static route configuration on a Cisco router, so that R0 can reach PC1.

   Assumed topology: PC1 sits on the LAN 192.168.2.0/24 behind R1; R0 and R1 are joined by the link 10.0.0.0/30, with R0 at 10.0.0.1 and R1 at 10.0.0.2. R0's own LAN is 192.168.1.0/24.

   ```
   PC0 --- [R0] ---10.0.0.0/30--- [R1] --- PC1
   192.168.1.0/24  .1        .2   192.168.2.0/24
   ```

   Configuration on R0:

   ```
   Router> enable
   Router# configure terminal
   Router(config)# hostname R0
   R0(config)# interface gigabitEthernet 0/0
   R0(config-if)# ip address 192.168.1.1 255.255.255.0
   R0(config-if)# no shutdown
   R0(config-if)# exit
   R0(config)# interface serial 0/0/0
   R0(config-if)# ip address 10.0.0.1 255.255.255.252
   R0(config-if)# clock rate 64000
   R0(config-if)# no shutdown
   R0(config-if)# exit
   R0(config)# ip route 192.168.2.0 255.255.255.0 10.0.0.2
   R0(config)# exit
   R0# write memory
   ```

   - Syntax of the static route: `ip route <destination network> <subnet mask> <next hop IP or exit interface>`.
   - Here it says: to reach 192.168.2.0/24, send the packet to the next hop 10.0.0.2, which is R1.

   The return route must also be configured on R1, otherwise the reply cannot come back:

   ```
   R1(config)# ip route 192.168.1.0 255.255.255.0 10.0.0.1
   ```

   Verification commands:
   - `show ip route` to confirm the route appears with an S, meaning static.
   - `show ip interface brief` to check that the interfaces are up.
   - `ping 192.168.2.10` from R0, and `tracert` from PC0 to PC1.

   - A default route `ip route 0.0.0.0 0.0.0.0 10.0.0.2` could be used instead if R0 has only one way out. Static routes have an administrative distance of 1, so they are preferred over any dynamically learned route.
3. **What is OSPF? Briefly Explain.** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1358 (ET: BUET)]*


   Answer: OSPF, Open Shortest Path First, is a link state interior gateway protocol used to route within a single autonomous system.

   - It is an open standard, defined in RFC 2328 for OSPFv2 with IPv4 and RFC 5340 for OSPFv3 with IPv6, so it works between equipment from different vendors.
   - Algorithm: Dijkstra's shortest path first. Every router builds a complete map of the area and computes the shortest path tree with itself as the root.
   - Metric: cost, calculated as reference bandwidth divided by interface bandwidth, with a default reference of 100 Mbps.
   - It runs directly over IP as protocol number 89, and uses multicast 224.0.0.5 for all OSPF routers and 224.0.0.6 for the designated routers.
   - Operation: routers discover each other with Hello packets every 10 seconds on a broadcast link, form adjacencies, exchange Link State Advertisements, build an identical link state database for the area, and then each runs Dijkstra independently.
   - On a multi-access segment a Designated Router and a Backup Designated Router are elected, so that adjacencies are n instead of n(n − 1)/2.
   - Hierarchy: the network is divided into areas, all connected to the backbone Area 0. This limits flooding, reduces the size of the database and speeds up convergence.
   - Advantages: fast convergence, no routing loops, classless with VLSM and CIDR support, no hop count limit, supports equal cost load balancing and authentication, and sends updates only when something changes.
   - Disadvantages: it needs more CPU and memory than a distance vector protocol, and its design and troubleshooting are more complex.
   - Administrative distance is 110.
4. **Which of the following is a pair of routing protocol?** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*
   * **(A) TCP and IP**
   * **(B) HTTP and FTP**
   * **(C) RIP and OSPF**
   * **(D) ARP and RARP**


   Answer: The correct option is (C) RIP and OSPF.

   - RIP, the Routing Information Protocol, is a distance vector routing protocol using hop count as its metric, and OSPF, Open Shortest Path First, is a link state routing protocol using cost. Both are interior gateway routing protocols.
   - (A) TCP and IP are transport and network layer protocols, not routing protocols.
   - (B) HTTP and FTP are application layer protocols.
   - (D) ARP and RARP are address resolution protocols, which map between IP and MAC addresses.
5. **BGP is __________ protocol.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: BGP is a path vector routing protocol.

   - It is also called an exterior gateway protocol, EGP, because it routes between autonomous systems rather than inside one, and it is the routing protocol of the Internet itself.
   - It is called path vector because each advertisement carries the full list of autonomous systems the route has traversed, the AS_PATH, which is how loops are detected and how policy is applied.
   - It runs over TCP port 179, uses BGP-4 today, and its administrative distance is 20 for eBGP and 200 for iBGP.
6. **BGP stands for __________?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*


   Answer: BGP stands for Border Gateway Protocol.

   - It is the exterior gateway protocol that exchanges routing information between autonomous systems, and it is what holds the global Internet routing table together.
   - It is a path vector protocol running over TCP port 179, and the current version is BGP-4.
7. **Which routing protocol use Dijkstra Algorithm?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*


   Answer: OSPF, Open Shortest Path First, uses Dijkstra's algorithm.

   - IS-IS, Intermediate System to Intermediate System, is the other link state protocol that also uses Dijkstra.
   - Every OSPF router builds an identical link state database for its area and then runs Dijkstra's shortest path first algorithm with itself as the root, producing a shortest path tree from which the routing table is derived.
   - For contrast, RIP and IGRP use the Bellman-Ford distance vector algorithm, EIGRP uses DUAL, and BGP uses a path vector best path selection process.
8. **What is Routing? Explain different types of Routing? Why using benefit of an Adhoce routing? Which routing algorithm is used in shortest path algorithm?** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 525 (ET: MIST)]*


   Answer:

   Routing:
   - Routing is the process of selecting a path along which a packet travels from a source network to a destination network, and of building and maintaining the routing table that records those paths.

   Types of routing:
   - Static routing: paths are entered manually by the administrator. No overhead, complete control, but no automatic adaptation and no scalability. Suits small or stub networks and default routes.
   - Default routing: a single route, 0.0.0.0/0, that catches everything not matched by a more specific entry. Used on a stub router with only one exit.
   - Dynamic routing: routers learn paths automatically by exchanging information with a routing protocol, and adapt when a link fails. It is subdivided as follows.
   - Interior Gateway Protocols, used inside one autonomous system: RIP and IGRP as distance vector, OSPF and IS-IS as link state, and EIGRP as a hybrid.
   - Exterior Gateway Protocol, used between autonomous systems: BGP, a path vector protocol.
   - Distance vector routing: uses Bellman-Ford; each router tells its neighbours its whole table periodically.
   - Link state routing: uses Dijkstra; each router floods the state of its own links to everyone, so all routers hold the same map.

   Benefits of ad hoc routing:
   - No fixed infrastructure is needed: no router, no access point and no cabling, so a network can be formed anywhere immediately.
   - Rapid deployment, which is exactly what is needed in a disaster area, a battlefield or a temporary site where the fixed network has been destroyed or never existed.
   - Self configuring and self healing: every node also acts as a router, so if one node moves away or fails, the routes are recomputed automatically around it.
   - Multi-hop reach: two nodes far apart can still communicate by relaying through intermediate nodes, so the coverage is greater than any single radio range.
   - Low cost, and full mobility, since the topology is expected to change continuously.
   - Robustness, since there is no single point of failure such as a central base station.
   - Common protocols are AODV and DSR, which are reactive, and OLSR and DSDV, which are proactive.

   Shortest path algorithm:
   - Dijkstra's algorithm is used for shortest path routing, and OSPF and IS-IS are the protocols built on it.
   - Bellman-Ford is the shortest path algorithm used by distance vector protocols such as RIP.
9. **(b) Distinguish between routing and forwarding. What are the advantages of net specific routing over host specific routing?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 490 (ET: N/A)]*


   Answer:

   Routing vs forwarding:

   | Point | Routing | Forwarding |
   |---|---|---|
   | Meaning | Deciding which paths exist and which is best | Moving one arriving packet to the correct outgoing interface |
   | Scope | Network wide, involves many routers | Local to one router, one packet at a time |
   | Plane | Control plane | Data plane |
   | Timescale | Slow, seconds to minutes, runs in the background | Very fast, nanoseconds, for every packet |
   | Produces or uses | Builds the routing table, the RIB | Uses the forwarding table, the FIB |
   | Implementation | Software, running routing protocols such as OSPF and BGP | Hardware, using an ASIC or TCAM lookup |
   | Trigger | A topology change or a periodic update | The arrival of a packet |

   - In one sentence: routing decides the map, forwarding drives on it.

   Advantages of net specific routing over host specific routing:
   - Far smaller routing tables. One entry covers a whole network of thousands of hosts, instead of one entry per host, so a router that would otherwise need millions of entries needs only a few hundred thousand.
   - Faster lookup, because the table is smaller and can fit into fast hardware memory.
   - Less memory and less CPU needed on every router.
   - Much less routing update traffic, since a change affecting one host does not have to be advertised across the network.
   - Better scalability: adding or removing a host inside a network requires no routing change at all anywhere.
   - Simpler administration and far fewer opportunities for error.
   - It supports aggregation and CIDR, so many adjacent networks can be summarised into a single supernet entry, which is what keeps the global Internet routing table manageable.
   - Host specific routing still has its place, for a special path for one particular server or for troubleshooting, and being more specific it takes precedence under the longest prefix match rule.
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


    Answer: The router uses the longest prefix match. The mask 255.255.254.0 is a /23, so each entry covers a block of two consecutive third octets.

    Ranges covered by the table:
    - 172.168.164.0/23 covers 172.168.164.0 to 172.168.165.255, Interface 0.
    - 172.168.166.0/23 covers 172.168.166.0 to 172.168.167.255, Interface 1.
    - 172.168.168.0/23 covers 172.168.168.0 to 172.168.169.255, Interface 2.
    - 172.168.170.0/23 covers 172.168.170.0 to 172.168.171.255, Interface 3.
    - Everything else falls to the default route, Interface 4.

    Matching each address:

    | IP address | Falls in | Outgoing interface |
    |---|---|---|
    | 172.168.165.121 | 164.0 to 165.255 | Interface 0 |
    | 172.168.167.151 | 166.0 to 167.255 | Interface 1 |
    | 172.168.163.151 | no entry matches | Interface 4, the default |
    | 172.168.171.92 | 170.0 to 171.255 | Interface 3 |
    | 0.0.0.0 | no entry matches | Interface 4, the default |

    - Note that 172.168.163.151 lies just below the first block, since 163 is odd and the /23 blocks start at even third octets, so it does not match any specific entry and takes the default route.
    - Interface 2 is not used by any of the given addresses, because none of them lies in 172.168.168.0 to 172.168.169.255.
11. **Define distance Vector and Link state routing protocols.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 635 (ET: N/A)]*


    Answer:

    Distance vector routing protocol:
    - Each router knows only the distance, that is the metric, and the direction, that is the next hop, to each destination; it has no picture of the whole network.
    - It periodically sends its entire routing table to its directly connected neighbours only, and updates its own table from what they send back, using the Bellman-Ford algorithm.
    - Convergence is slow because information spreads one hop per update cycle, and it is vulnerable to routing loops and the count to infinity problem, which is why split horizon, route poisoning and hold-down timers are needed.
    - It uses little CPU and memory. Examples: RIP with a hop count metric and a limit of 15 hops, and IGRP. EIGRP is a hybrid that adds link state ideas.

    Link state routing protocol:
    - Every router discovers the state of its own directly connected links and floods that information, as a Link State Advertisement, to every router in the area.
    - All routers thus hold an identical link state database, that is a complete map of the topology, and each independently runs Dijkstra's shortest path first algorithm with itself as the root to build its routing table.
    - Updates are sent only when something changes, plus a periodic refresh, so the steady state overhead is low, but a change causes a burst of flooding.
    - Convergence is fast and routing loops are essentially impossible, at the cost of much higher CPU and memory use. Examples: OSPF and IS-IS.
12. **What are static and dynamic routing? Given their relative advantages.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 635 (ET: N/A)]*


    Answer:

    Static routing: routes are configured manually by the administrator with a command such as `ip route <network> <mask> <next hop>`. The router never changes them by itself.

    Dynamic routing: routes are learned automatically by running a routing protocol such as RIP, OSPF, EIGRP or BGP, which exchanges information with neighbouring routers and rebuilds the table when the topology changes.

    | Point | Static routing | Dynamic routing |
    |---|---|---|
    | Configuration | Entered manually by the administrator | Learned automatically by a routing protocol |
    | Adaptation | None; a failed link must be fixed by hand | Automatic; an alternative path is found in seconds |
    | CPU, memory and bandwidth | Almost none | Consumes CPU, memory and link bandwidth for updates |
    | Security | Higher, no routing information is advertised | Lower, updates can be spoofed unless authenticated |
    | Scalability | Poor, unusable beyond a few routers | Excellent, designed for large networks |
    | Predictability | Complete, the path is always known | The path may change with conditions |
    | Administrative distance | 1, so it is preferred over dynamic routes | 90 for EIGRP, 110 for OSPF, 120 for RIP |
    | Best use | Small or stub networks, a default route, a backup path | Medium and large networks with redundant links |

    Relative advantages of static routing:
    - No protocol overhead at all, so it suits low bandwidth links.
    - Total administrative control and complete predictability of the path.
    - More secure, since nothing is advertised that an attacker could read or inject.
    - Simple to understand and easy to troubleshoot in a small network.

    Relative advantages of dynamic routing:
    - Adapts automatically to a link or router failure, giving real fault tolerance.
    - Scales to hundreds of routers without manual work.
    - Chooses the best path by a metric, and can load balance across equal cost paths.
    - Far less administrative effort and far less risk of a typing mistake.
13. **What is Routing? Write down the difference between static routing and dynamic routing.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 837-838 (ET: N/A)]*


    Answer: Routing is the process of selecting the path along which a packet is sent from a source network to a destination network, and of building and maintaining the routing table that records those paths. The router reads the destination IP address, looks it up in the routing table using the longest prefix match, and forwards the packet towards the chosen next hop.

    | Point | Static routing | Dynamic routing |
    |---|---|---|
    | Configuration | Entered manually by the administrator | Learned automatically by a routing protocol |
    | Adaptation | None; a failed link must be fixed by hand | Automatic; an alternative path is found in seconds |
    | CPU, memory and bandwidth | Almost none | Consumes CPU, memory and link bandwidth for updates |
    | Security | Higher, no routing information is advertised | Lower, updates can be spoofed unless authenticated |
    | Scalability | Poor, unusable beyond a few routers | Excellent, designed for large networks |
    | Predictability | Complete, the path is always known | The path may change with conditions |
    | Administrative distance | 1, so it is preferred over dynamic routes | 90 for EIGRP, 110 for OSPF, 120 for RIP |
    | Best use | Small or stub networks, a default route, a backup path | Medium and large networks with redundant links |

    Relative advantages of static routing:
    - No protocol overhead at all, so it suits low bandwidth links.
    - Total administrative control and complete predictability of the path.
    - More secure, since nothing is advertised that an attacker could read or inject.
    - Simple to understand and easy to troubleshoot in a small network.

    Relative advantages of dynamic routing:
    - Adapts automatically to a link or router failure, giving real fault tolerance.
    - Scales to hundreds of routers without manual work.
    - Chooses the best path by a metric, and can load balance across equal cost paths.
    - Far less administrative effort and far less risk of a typing mistake.
14. **Name of the Algorithm RIP, OSPF and EIGRP routing protocol.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 838 (ET: N/A)]*


    Answer:

    - RIP, the Routing Information Protocol, uses the Bellman-Ford algorithm, which is the distance vector algorithm. Its metric is hop count, with a maximum of 15, and it updates every 30 seconds. Administrative distance 120.
    - OSPF, Open Shortest Path First, uses Dijkstra's algorithm, which is the shortest path first or link state algorithm. Its metric is cost, derived from bandwidth. Administrative distance 110.
    - EIGRP, the Enhanced Interior Gateway Routing Protocol, uses DUAL, the Diffusing Update Algorithm. It is a hybrid or advanced distance vector protocol whose composite metric is based on bandwidth and delay, and DUAL keeps a loop free feasible successor ready so that convergence is almost instant. Administrative distance 90 for internal routes.
15. **What is Autonomous system? What is the difference between Link state routing protocol and Distance vector routing protocol?** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 838-839 (ET: N/A)]*


    Answer:

    Autonomous System:
    - An Autonomous System is a collection of networks and routers under a single administrative authority that presents a common and clearly defined routing policy to the outside world.
    - It is identified by a globally unique Autonomous System Number, ASN, 16 bit originally and 32 bit now, allocated by IANA through the regional registries. Every ISP, and any large organisation that connects to more than one ISP, holds one.
    - Inside the AS an interior gateway protocol such as OSPF, EIGRP or IS-IS is used; between autonomous systems the exterior protocol BGP is used.
    - The purpose is scalability: the Internet is treated as a network of autonomous systems rather than a network of individual routers, so the global routing table stays manageable, and each operator keeps full control of its own internal design.
    - Types: a stub AS with a single connection, a multihomed AS with several connections but carrying no transit traffic, and a transit AS such as an ISP that carries traffic for others.

    Link state vs distance vector:

    | Point | Distance Vector | Link State |
    |---|---|---|
    | Algorithm | Bellman-Ford | Dijkstra's shortest path first |
    | What is known | Only the distance and direction to each destination | The complete topology of the whole area |
    | What is shared | The entire routing table | Only the state of its own directly connected links, the LSA |
    | Shared with | Directly connected neighbours only | Flooded to every router in the area |
    | Frequency | Periodically, RIP every 30 seconds | Only when a change occurs, plus a refresh every 30 minutes |
    | Convergence | Slow, information travels hop by hop | Fast, every router recomputes at once |
    | Routing loops | Possible, needs split horizon, poison reverse and hold-down timers | Very unlikely, since each router has the full map |
    | Count to infinity | Yes, this is its classic weakness | No |
    | CPU and memory | Low | High, it must store the whole topology database |
    | Bandwidth use | Steady periodic overhead | A burst on change, quiet otherwise |
    | Hierarchy | None | Supports areas, which limits flooding |
    | Metric | Hop count in RIP | Cost derived from bandwidth |
    | Examples | RIP, IGRP, and EIGRP as a hybrid | OSPF, IS-IS |

    - The saying that captures the difference: distance vector routers tell their neighbours about the whole world, while link state routers tell the whole world about their neighbours.
16. **Cost calculation of EIGRP formula.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 839 (ET: N/A)]*


    Answer: The EIGRP composite metric is calculated from the K values.

    Full formula:
    - Metric = 256 × [ (K1 × Bandwidth + (K2 × Bandwidth) / (256 − Load) + K3 × Delay) × K5 / (Reliability + K4) ]
    - Where the K value defaults are K1 = 1, K2 = 0, K3 = 1, K4 = 0 and K5 = 0.
    - When K5 = 0 the whole trailing term is omitted rather than multiplied by zero.

    Default simplified formula:
    - Metric = 256 × (Bandwidth + Delay)
    - Bandwidth = 10⁷ / (the lowest bandwidth in kbps along the whole path)
    - Delay = (the sum of all the interface delays along the path, in microseconds) / 10

    Worked example: a path across a 64 kbps serial link with a total delay of 42,000 microseconds.
    - Bandwidth term = 10⁷ / 64 = 156,250
    - Delay term = 42,000 / 10 = 4,200
    - Metric = 256 × (156,250 + 4,200) = 256 × 160,450 = 41,075,200

    - Note: bandwidth uses the minimum, that is the slowest link on the path, because that is what limits the throughput, whereas delay is cumulative because every hop adds to it. Load and reliability are excluded by default because they change constantly and would make the routing table unstable.
17. **Given a totology of distance vector routing. Find the table of each node for the 1^{\text{st}} route.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 859-860 (ET: N/A)]*


    Answer: Method for building the first round of distance vector tables, applied to a standard four node topology.

    Assumed topology, since the figure is not reproduced here: nodes A, B, C and D with links A-B cost 2, B-C cost 3, C-D cost 1 and A-C cost 5.

    Step 1, initialisation. Every node knows only its own directly connected neighbours; everything else is infinity.

    | From | To A | To B | To C | To D |
    |---|---|---|---|---|
    | A | 0 | 2 | 5 | infinity |
    | B | 2 | 0 | 3 | infinity |
    | C | 5 | 3 | 0 | 1 |
    | D | infinity | infinity | 1 | 0 |

    Step 2, first exchange. Each node sends its vector to its neighbours and applies the Bellman-Ford rule, Dx(y) = min over all neighbours v of [ cost(x,v) + Dv(y) ].

    Table of A after the first round:
    - To B: direct 2, or via C = 5 + 3 = 8. Keep 2, next hop B.
    - To C: direct 5, or via B = 2 + 3 = 5. Both are 5, keep 5, next hop C.
    - To D: via C = 5 + 1 = 6, or via B = 2 + infinity. So 6, next hop C.

    Table of B after the first round:
    - To A: 2, next hop A. To C: 3, next hop C. To D: via C = 3 + 1 = 4, next hop C.

    Table of C after the first round:
    - To A: direct 5, or via B = 3 + 2 = 5. Keep 5. To B: 3, next hop B. To D: 1, next hop D.

    Table of D after the first round:
    - To C: 1, next hop C. To B: via C = 1 + 3 = 4, next hop C. To A: via C = 1 + 5 = 6, next hop C.

    Consolidated result after the first exchange:

    | From | To A | To B | To C | To D |
    |---|---|---|---|---|
    | A | 0 | 2 via B | 5 via C | 6 via C |
    | B | 2 via A | 0 | 3 via C | 4 via C |
    | C | 5 via A | 3 via B | 0 | 1 via D |
    | D | 6 via C | 4 via C | 1 via C | 0 |

    - Method to repeat for any given figure: start with the direct costs and infinity elsewhere, then for every destination take the minimum over each neighbour of the cost to that neighbour plus the neighbour's advertised distance, and record the neighbour that gave the minimum as the next hop. Repeat until no table changes; the count of rounds needed is at most n − 1 for n nodes. <!-- verify -->
18. **What is difference between link state routing and distance vector routing?** *[Sonali Bank Ltd. Officer IT 2021 compact it 909 (ET: N/A)]*


    Answer:

    | Point | Distance Vector | Link State |
    |---|---|---|
    | Algorithm | Bellman-Ford | Dijkstra's shortest path first |
    | What is known | Only the distance and direction to each destination | The complete topology of the whole area |
    | What is shared | The entire routing table | Only the state of its own directly connected links, the LSA |
    | Shared with | Directly connected neighbours only | Flooded to every router in the area |
    | Frequency | Periodically, RIP every 30 seconds | Only when a change occurs, plus a refresh every 30 minutes |
    | Convergence | Slow, information travels hop by hop | Fast, every router recomputes at once |
    | Routing loops | Possible, needs split horizon, poison reverse and hold-down timers | Very unlikely, since each router has the full map |
    | Count to infinity | Yes, this is its classic weakness | No |
    | CPU and memory | Low | High, it must store the whole topology database |
    | Bandwidth use | Steady periodic overhead | A burst on change, quiet otherwise |
    | Hierarchy | None | Supports areas, which limits flooding |
    | Metric | Hop count in RIP | Cost derived from bandwidth |
    | Examples | RIP, IGRP, and EIGRP as a hybrid | OSPF, IS-IS |

    - The saying that captures the difference: distance vector routers tell their neighbours about the whole world, while link state routers tell the whole world about their neighbours.

## Wireless Networks & IoT (mmWave) (17)

1. **Describe Wi-Fi, Bluetooth, and WiMAX.** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*


   Answer:

   Wi-Fi:
   - Wireless LAN technology defined by IEEE 802.11, used to connect devices to a local network and the Internet without cable.
   - Operates in the unlicensed 2.4 GHz, 5 GHz and now 6 GHz bands, with a range of about 30 to 100 metres indoors.
   - Uses CSMA/CA for medium access, since a radio cannot detect a collision while transmitting.
   - Data rates from 11 Mbps in 802.11b to about 9.6 Gbps theoretical in 802.11ax, that is Wi-Fi 6.
   - Security is provided by WPA2 and WPA3. Devices connect through an access point that bridges the wireless side to the wired LAN.

   Bluetooth:
   - Short range WPAN technology defined by IEEE 802.15.1, designed to replace cables between personal devices.
   - Operates in the 2.4 GHz ISM band using frequency hopping spread spectrum, 1600 hops per second, which gives good resistance to interference.
   - Range is about 10 metres for class 2 devices and up to 100 metres for class 1. Data rate is 1 to 3 Mbps for classic Bluetooth and about 2 Mbps for Bluetooth Low Energy.
   - Topology is a piconet with one master and up to seven active slaves; several piconets form a scatternet.
   - Very low power consumption, which is why BLE dominates wearables and IoT sensors. Devices are paired with a PIN and the link is encrypted.

   WiMAX:
   - Worldwide Interoperability for Microwave Access, defined by IEEE 802.16, a wireless metropolitan area network technology, that is broadband wireless access over a whole city.
   - Range up to about 50 km for fixed line of sight links and 5 to 15 km for mobile use, with data rates up to about 70 Mbps.
   - Operates in licensed and unlicensed bands from 2 to 66 GHz, using OFDM and OFDMA with adaptive modulation.
   - Architecture is a base station serving many subscriber stations, both line of sight and non line of sight.
   - Unlike Wi-Fi it is connection oriented and scheduled by the base station, so it has built in QoS. It was designed as a last mile alternative to DSL and cable, but LTE largely displaced it commercially.
2. **What is the use of mmWave in IoT?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1454 (ET: BUET)]*


   Answer: mmWave, millimetre wave, is the radio spectrum from 24 GHz to 100 GHz, where the wavelength is 1 to 10 mm. It is used in IoT for the following purposes.

   - Very high data rate: the enormous available bandwidth, hundreds of MHz to several GHz per channel, allows multi-gigabit links, which suits IoT applications that carry video, such as smart surveillance, industrial machine vision and augmented reality headsets.
   - Massive device density: 5G mmWave supports up to a million connected devices per square kilometre, which is what a dense sensor deployment in a smart city or a factory needs.
   - Ultra low latency: about 1 ms, which makes real time control possible for industrial robots, autonomous vehicle to everything communication and remote surgery.
   - Precise sensing and radar: because the wavelength is a few millimetres, mmWave radar can measure distance, speed and even small movements very accurately. It is used for gesture recognition, occupancy and people counting, fall detection for elderly care, vehicle collision avoidance and level measurement in tanks.
   - Privacy friendly sensing: a mmWave radar sensor can detect presence, posture and breathing without any camera image, so it suits homes and hospitals where a camera would be intrusive.
   - Small antennas and beamforming: the tiny wavelength lets many antenna elements fit into a small array, so massive MIMO and narrow steerable beams become practical, which increases capacity and reduces interference.
   - Short range by design: mmWave is heavily attenuated by walls, rain and foliage and needs near line of sight, so cells are small, typically 100 to 200 metres. This is a limitation for coverage but an advantage for spatial reuse and security, since the signal does not leak far.
   - Typical deployments: smart factories, smart cities, stadiums and airports, fixed wireless access to homes, and in vehicle radar.
3. **What is IoT? Brefly explain.** *[Mongla Port Authority Assistant Programmer 2023 compact it 571 (ET: N/A)]*


   Answer: IoT, the Internet of Things, is a network of physical objects embedded with sensors, software and network connectivity, which collect data and exchange it over the Internet with little or no human involvement.

   - The idea is to give ordinary objects, such as a light, a meter, a pump or a wristband, the ability to sense their environment, report it and be controlled remotely.
   - A typical flow is: sensor collects data, a gateway forwards it over the network, a cloud platform stores and analyses it, and an application presents it or triggers an action back on the device.
   - Communication uses Wi-Fi, Bluetooth Low Energy, Zigbee, LoRaWAN, NB-IoT or 5G, and the application layer usually uses MQTT or CoAP because they are lightweight.
   - Examples: smart electricity meters, smart agriculture with soil moisture sensors, wearable health monitors, smart traffic lights, industrial predictive maintenance and home automation.
   - Benefits: automation, real time monitoring, better efficiency, cost saving and data driven decisions.
   - Challenges: security and privacy, since many devices are weakly protected; power consumption; the sheer volume of data; and the lack of a single common standard.
4. **How to work WiMax technology?** *[Mongla Port Authority Assistant Programmer 2023 compact it 571 (ET: N/A)]*


   Answer: WiMAX, IEEE 802.16, provides broadband wireless access over a metropolitan area, working as a wireless replacement for DSL or cable in the last mile.

   How it works:
   - The network has two main parts, a base station mounted on a tower and subscriber stations, that is customer premises equipment, at homes and offices. The base station connects back to the Internet through a wired or microwave backhaul.
   - The base station covers up to about 50 km for a fixed line of sight link and 5 to 15 km for non line of sight and mobile use, serving thousands of subscribers.
   - The air interface uses OFDM and OFDMA, which splits the channel into many orthogonal subcarriers. This resists multipath fading well and lets subcarriers be allocated to different users at the same time.
   - Adaptive modulation is used: a subscriber close to the tower with a strong signal gets 64-QAM and a high rate, while a distant one falls back to QPSK, so the link stays alive rather than dropping.
   - Access is connection oriented and scheduled. Unlike Wi-Fi, a subscriber does not contend randomly; it requests bandwidth and the base station grants it a time slot. This is what gives WiMAX real QoS, with separate service classes for voice, video and best effort data.
   - Duplexing may be TDD, where uplink and downlink share one frequency in different time slots, or FDD with separate frequencies.
   - Mobile WiMAX, 802.16e, adds handover between base stations, so a moving user stays connected.
   - Security uses EAP based authentication and AES encryption of the traffic.
   - Typical performance is up to about 70 Mbps shared, and it operates in bands from 2 to 66 GHz. Commercially it has largely been replaced by LTE.
5. **Briefly describe the basis structure at a mobile cellular system with a proper figure.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 676 (ET: N/A)]*


   Answer: A mobile cellular system divides the service area into small regions called cells, each served by its own base station, so that the same frequencies can be reused in cells that are far enough apart.

   ```mermaid
   graph TD
       M1["Mobile Station MS"] --> B1["Base Transceiver Station BTS, Cell 1"]
       M2["Mobile Station MS"] --> B2["Base Transceiver Station BTS, Cell 2"]
       B1 --> C["Base Station Controller BSC"]
       B2 --> C
       C --> S["Mobile Switching Centre MSC"]
       S --> H["HLR: Home Location Register"]
       S --> V["VLR: Visitor Location Register"]
       S --> A["AUC and EIR: authentication and equipment check"]
       S --> P["PSTN / Internet"]
   ```

   Basic structure:
   - Cell: the basic geographic unit, drawn as a hexagon for convenience, from a few hundred metres in a city to tens of kilometres in a rural area. Each cell uses a set of frequencies that is reused in distant cells, which is the whole reason a cellular system can serve millions of users with limited spectrum.
   - Mobile Station: the handset with its SIM, which identifies the subscriber.
   - Base Transceiver Station: the antennas and radios at the tower, handling the air interface for one cell or sector.
   - Base Station Controller: controls a group of BTSs, allocates radio channels, manages power control and takes handover decisions.
   - Mobile Switching Centre: the telephone exchange of the mobile network. It sets up and routes calls, handles handover between BSCs, and connects to the PSTN and to other networks.
   - HLR: the permanent database of all subscribers of this network, holding the subscription details and the current location area.
   - VLR: a temporary database of the subscribers currently roaming in this MSC area.
   - AUC and EIR: the authentication centre holds the keys used to verify the SIM, and the equipment identity register checks the handset IMEI against a blacklist.
   - Handover: as a user moves out of one cell, the network transfers the call to the neighbouring cell without dropping it. Frequency reuse and handover together are the two central ideas of the cellular concept.
6. **How can you define IoT? What are the basic components of IoT?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 680 (ET: N/A)]*


   Answer: IoT, the Internet of Things, is a network of physical objects fitted with sensors, processors and communication modules that collect data and exchange it over the Internet, so that they can be monitored and controlled remotely with little human involvement.

   Basic components of IoT:
   - Sensors and actuators: the sensor measures a physical quantity such as temperature, humidity, motion, light or current, and the actuator performs an action such as switching a relay, opening a valve or running a motor. Together they form the perception layer.
   - Embedded device and processor: a microcontroller or SoC, for example ESP32, Arduino or Raspberry Pi, which reads the sensor, does basic processing and drives the actuator. This is where edge computing is done to reduce the data sent upward.
   - Connectivity: the communication technology carrying the data, that is Wi-Fi, Bluetooth Low Energy, Zigbee, LoRaWAN, NB-IoT, 5G or Ethernet, chosen according to range, data rate and battery life.
   - Gateway: aggregates data from many local devices, translates between the local protocol such as Zigbee and IP, and often provides local storage, filtering and security.
   - Cloud platform and data storage: receives, stores and processes the data at scale, using MQTT or CoAP as the messaging protocol because they are lightweight.
   - Data analytics and intelligence: analytics and machine learning turn raw readings into useful information, for example predicting when a machine will fail.
   - User interface and application: the mobile app or dashboard through which the user sees the data and issues commands.
   - Security layer: device authentication, encryption of data in transit and at rest, secure firmware update, and access control, which runs across every other component.
   - Power supply: usually a battery, which is why low power design dominates IoT hardware.
7. **(a) Write down the features of 4G wireless networks.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 695 (ET: N/A)]*


   Answer: Features of 4G wireless networks:

   - All IP packet switched network. There is no separate circuit switched voice path; voice is carried as VoLTE over the same IP core.
   - High data rate: about 100 Mbps for a user in a fast moving vehicle and up to 1 Gbps for a stationary or slow moving user, as set by the IMT-Advanced requirement.
   - Low latency, about 30 to 50 ms, which makes video calling, online gaming and cloud applications usable.
   - OFDMA on the downlink and SC-FDMA on the uplink, which resists multipath fading well and uses spectrum efficiently.
   - MIMO with multiple transmit and receive antennas, which multiplies throughput without extra bandwidth.
   - Scalable channel bandwidth from 1.4 MHz to 20 MHz, and carrier aggregation in LTE-Advanced to combine several carriers.
   - High spectral efficiency, about 15 bits per second per hertz on the downlink.
   - Seamless handover and global roaming, with smooth handover between LTE, 3G and Wi-Fi.
   - Better QoS support, so voice, video and data can be given different treatment.
   - Improved security with stronger mutual authentication and encryption than 3G.
   - Support for high mobility, working at speeds up to 350 km per hour.
   - A flat, simplified network architecture, eNodeB and the Evolved Packet Core, with fewer nodes than 3G, which lowers cost and delay.
8. **5G প্রথম কত সালে ও কোথায় চালু হয়?** *[BWMRI Assistant Maintenance Engineer 2022 compact it 736 (ET: N/A)]*

   Answer: 5G was launched commercially for the first time in 2019.

   - In April 2019 South Korea launched the world's first nationwide commercial 5G network, and at almost the same time Verizon launched 5G in Chicago and Minneapolis in the United States.
   - South Korea is generally credited as the first, because it was the first to offer a full nationwide commercial 5G service.
   - In Bangladesh, Teletalk launched 5G on a limited scale on 12 December 2021.
9. **(ক) Wi-Fi Network সম্পর্কে সংক্ষিপ্ত বিবরণ দিন। Wi-Fi Sensor Network এবং Ad Hoc Network এর মধ্যে পার্থক্য লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 769 (ET: N/A)]*

   Answer:

   Wi-Fi network:
   - Wi-Fi is a wireless LAN technology built on the IEEE 802.11 standard, which connects devices to a local network and to the Internet without cable.
   - It works in the unlicensed 2.4 GHz, 5 GHz and now 6 GHz bands, with an indoor range of about 30 to 100 metres.
   - An access point bridges the wireless clients to the wired LAN. The coverage area of one access point is called a BSS, and several access points form an ESS within which a client can roam.
   - Medium access uses CSMA/CA, because a radio cannot detect a collision while it is transmitting.
   - Data rates run from 11 Mbps in 802.11b up to a theoretical 9.6 Gbps in 802.11ax, that is Wi-Fi 6.
   - Security is provided by WPA2 and WPA3. Its advantages are easy installation, mobility and low cost; its disadvantages are interference, limited range and the security risk of an open medium.

   Difference between a Wireless Sensor Network and an Ad Hoc Network:

   | Point | Wireless Sensor Network | Ad Hoc Network |
   |---|---|---|
   | Purpose | Sensing and collecting data from the environment | General communication between two or more devices |
   | Nodes | Small, cheap, low powered sensor nodes, often thousands of them | Capable devices such as laptops and phones, and far fewer of them |
   | Traffic direction | Usually many to one, from every node towards a single sink | Peer to peer, from any node to any node |
   | Power | Battery powered and often not replaceable, so energy is the main design constraint | Rechargeable, so power is a much smaller problem |
   | Mobility | Nodes are normally stationary | Nodes are often moving |
   | Data rate | Very low, a few bytes at intervals | Much higher, files or video |
   | Addressing | Data centric, by attribute, and possibly without an identifier | Node centric, each node has its own address |
   | Redundancy | Many nodes observe the same event, so the data is redundant | Each node's data is distinct |
   | Examples | Soil moisture sensors in a field, forest fire detection | Direct file sharing between two laptops, MANET, VANET |

   - In essence a wireless sensor network is a special kind of ad hoc network whose purpose is sensing and whose overriding concern is saving energy.
10. **Call Drop কী? এর কারণ গুলো উল্লেখ করুন।** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 810 (ET: IBA)]*

    Answer:

    What a call drop is:
    - A call drop is the sudden termination of an ongoing telephone call by the network, without either party wishing to end it.
    - Regulators such as the BTRC treat the call drop rate as a key measure of service quality, and it is normally expected to remain below 2 percent.

    Causes of call drops:
    - Weak signal or lack of coverage: when a user moves to the edge of a cell or into a coverage hole, the signal strength falls below the usable threshold.
    - Handover failure: when a user moves from one cell to another, the call is lost if the target cell has no free capacity or if the handover is not completed in time.
    - Network congestion: when the channels or the capacity of a cell are exhausted, not only are new calls blocked but ongoing calls may also be dropped.
    - Interference: co-channel and adjacent channel interference from neighbouring cells, or noise from other sources.
    - Indoor penetration loss: thick walls, lifts, basements and shopping malls block the signal.
    - Equipment faults at the tower or base station: power failure, a failed transmission link, antenna misalignment or hardware failure.
    - Geographical obstacles: hills, tall buildings and dense trees, particularly at higher frequencies.
    - Weather: heavy rain or storms weaken microwave backhaul links.
    - Handset problems: a weak battery, a poor antenna, outdated firmware or a faulty SIM.
    - High speed movement: on a train or in a fast car there is too little time for handover, and the Doppler effect degrades the signal.
    - Lack of optimisation: when new buildings appear, the old cell plan no longer fits, and the network must be re-optimised through drive testing.
11. **LTE কী? এর এডভান্সড প্রযুক্তির নাম লিখুন।** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 811 (ET: IBA)]*

    Answer:

    What LTE is:
    - LTE stands for Long Term Evolution, a wireless broadband standard developed by 3GPP and generally known as 4G.
    - It is a fully IP based packet switched network; there is no separate circuit switched voice path, and voice is carried over the same IP core as VoLTE.
    - It uses OFDMA on the downlink and SC-FDMA on the uplink, together with MIMO antennas.
    - Downlink data rates are 100 to 300 Mbps and latency is about 30 to 50 ms. The channel bandwidth is scalable from 1.4 MHz to 20 MHz.
    - Its architecture is flat, consisting of the eNodeB and the Evolved Packet Core, so there are fewer nodes and lower delay.

    Names of its advanced technologies:
    - LTE-Advanced, 3GPP Release 10, which meets the ITU requirements for true 4G. Its main technologies are:
    - Carrier Aggregation: combining up to five carriers for a total of 100 MHz of bandwidth, giving much higher speed.
    - Enhanced MIMO: up to 8 × 8 on the downlink and 4 × 4 on the uplink.
    - Coordinated Multi-Point, CoMP: several neighbouring cells serve one user together, so speed remains good even at the cell edge.
    - Relay Nodes and Heterogeneous Networks, HetNet: small pico and femto cells placed inside the large macro cell.
    - Enhanced Inter-Cell Interference Coordination, eICIC, which reduces interference between cells.
    - LTE-Advanced Pro, Release 13 and later, which adds License Assisted Access, Massive MIMO, NB-IoT and Gigabit LTE. 5G NR follows after this.
12. **Wi-Fi, Bluetooth, Wi-Max, Cellure network এইগুলোকে দূরত্বের ক্রমানুসারে ছোট থেকে বড় এর দিক অনুসারে লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 867 (ET: BUET)]*

    Answer: In order of range, from smallest to largest:

    | Order | Technology | Typical range | Network type |
    |---|---|---|---|
    | 1 | Bluetooth | 10 m, up to 100 m for class 1 | WPAN, Personal Area Network |
    | 2 | Wi-Fi | 30 to 100 m indoors | WLAN, Local Area Network |
    | 3 | WiMAX | 5 to 50 km | WMAN, Metropolitan Area Network |
    | 4 | Cellular network | 1 to 35 km per cell, but nationwide coverage overall | WWAN, Wide Area Network |

    - The order is therefore: Bluetooth < Wi-Fi < WiMAX < Cellular network.
    - Measured from a single tower, WiMAX can reach further than one cellular cell, but a cellular network uses thousands of towers to cover a whole country, so its overall coverage is the greatest.
13. **(c) Difference between broadband Wi-Fi and Wi-Max communication technology.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 896 (ET: N/A)]*


    Answer:

    | Point | Broadband Wi-Fi | WiMAX |
    |---|---|---|
    | Standard | IEEE 802.11 | IEEE 802.16 |
    | Network type | WLAN, local area | WMAN, metropolitan area |
    | Range | 30 to 100 m indoors | 5 to 15 km non line of sight, up to 50 km line of sight |
    | Frequency band | Unlicensed 2.4, 5 and 6 GHz | Licensed and unlicensed, 2 to 66 GHz |
    | Access method | CSMA/CA, random contention | Scheduled by the base station, connection oriented |
    | QoS | Weak, added later by 802.11e | Built in, with defined service classes for voice, video and data |
    | Data rate | Up to about 9.6 Gbps theoretical in Wi-Fi 6, shared | Up to about 70 Mbps shared per channel |
    | Users supported | Tens per access point | Thousands per base station |
    | Channel bandwidth | 20, 40, 80 or 160 MHz | Scalable, 1.25 to 20 MHz |
    | Modulation | OFDM and OFDMA | OFDM and OFDMA with adaptive modulation by distance |
    | Mobility | Limited, roaming within an ESS | Supported, 802.16e allows handover at vehicular speed |
    | Security | WPA2, WPA3 | EAP authentication with AES encryption |
    | Cost and deployment | Very cheap, anyone can install | Expensive, needs licensed spectrum and towers |
    | Purpose | Last few metres, home and office access | Last mile, replacing DSL and cable across a city |
14. **What is wireless network system? Why CSMA/CA used instead of CSMA/CD?** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922-923 (ET: N/A)]*


    Answer:

    Wireless network system:
    - A wireless network is a network in which devices are connected by radio, microwave or infrared waves instead of physical cable, so the transmission medium is unguided.
    - Categories by range: WPAN such as Bluetooth and Zigbee, WLAN such as Wi-Fi, WMAN such as WiMAX, and WWAN such as cellular 4G and 5G.
    - Components: wireless NIC in each device, an access point or base station, an antenna, and the radio spectrum itself.
    - Advantages: mobility, easy and cheap installation with no cabling, easy expansion, and access in places where cable cannot go.
    - Disadvantages: lower bandwidth than cable, interference, limited range, higher security risk because the medium is open, and variable performance.

    Why CSMA/CA is used instead of CSMA/CD:
    - Collision detection is physically impossible on a radio interface. A station transmits at a much higher power than the signal it would receive from a distant station, so its own transmission drowns out everything else and it simply cannot hear a collision while sending.
    - Building a radio that could transmit and listen on the same channel at the same time would need full duplex radio with echo cancellation, which was not practical or affordable in ordinary Wi-Fi hardware.
    - The hidden terminal problem: two stations A and C may both be in range of the access point B but not of each other. Neither hears the other's carrier, so both sense the channel as free and transmit together, colliding at B. Carrier sensing alone therefore cannot prevent collisions, and CSMA/CA adds the RTS and CTS exchange to solve exactly this.
    - The exposed terminal problem similarly makes a station defer unnecessarily when it could safely transmit.
    - Wireless collisions are expensive. The channel is scarce and the error rate is already high, so it is far better to avoid a collision beforehand than to detect one and retransmit.
    - How CSMA/CA works instead: sense the channel; if it is busy, wait; if it is free, wait a DIFS interval and then a random backoff before transmitting; optionally exchange RTS and CTS so that all neighbours set their network allocation vector and stay silent; and require an ACK for every unicast frame, since the absence of an ACK is the only way the sender can learn that a collision occurred.
15. **Write about 5G disadvantages: (a) Increased High Costs (b) Draining Battery of devices. (c) Increased infrastructure development cost** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 928 (ET: CTI)]*


    Answer: Disadvantages of 5G.

    (a) Increased high costs
    - 5G devices and subscription plans are considerably more expensive than 4G, so ordinary users bear a higher monthly cost.
    - Handsets need new mmWave and massive MIMO capable chipsets and antennas, which raises the price of the phone itself.
    - Older 4G handsets cannot use 5G at all, so the whole user base has to replace its equipment, which is a large national expense.
    - Licensed 5G spectrum is auctioned at very high prices, and the operator recovers this from the tariff.

    (b) Draining battery of devices
    - The 5G modem consumes far more power than a 4G modem, so a phone on 5G typically loses 20 percent or more battery life for the same use.
    - mmWave has a short range, so the handset frequently switches between 5G and 4G and constantly searches for a signal, and searching consumes more energy than a stable connection.
    - Beamforming and massive MIMO need multiple antennas and continuous channel measurement and reporting, which keeps the radio busy.
    - The very high data rates make the application processor work harder as well, and the whole device heats up, which further degrades battery health over time.
    - IoT sensors that must run for years on one battery cannot use ordinary 5G, which is why low power variants such as NB-IoT and RedCap exist.

    (c) Increased infrastructure development cost
    - mmWave cells cover only 100 to 300 metres, so many times more base stations are needed than for 4G, each with site rental, power and maintenance.
    - Every small cell needs a fibre backhaul link, so a vast amount of new fibre must be laid, which is usually the largest single item of expenditure.
    - Existing towers must be upgraded with new massive MIMO antennas and radios, and the power supply at each site must be strengthened.
    - Coverage in rural areas becomes commercially unattractive because the same dense infrastructure serves far fewer subscribers, which widens the digital divide.
    - Signals are blocked by walls, glass, rain and even foliage, so indoor coverage needs additional repeaters and distributed antenna systems.
    - The result is that operators recover the cost slowly, and full national coverage takes many years, which is exactly the position in Bangladesh today.
16. **Make a list of LTE Network elements.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 988 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*


    Answer: LTE network elements, grouped into the radio access network and the core network.

    Radio access network, E-UTRAN:
    - UE, User Equipment: the handset or data device together with its USIM.
    - eNodeB, Evolved Node B: the base station. It handles the radio interface, scheduling, radio resource management, handover decisions and header compression. Unlike 3G there is no separate controller; the eNodeBs talk to each other directly over the X2 interface.

    Core network, Evolved Packet Core:
    - MME, Mobility Management Entity: the control plane node. It handles attach and detach, authentication, bearer setup, tracking area updates, paging and handover signalling. It carries no user data.
    - S-GW, Serving Gateway: routes and forwards user data packets, and acts as the mobility anchor during handover between eNodeBs.
    - P-GW, PDN Gateway: the gateway to the external packet data network, that is the Internet. It allocates the IP address to the UE, enforces policy and does charging and packet filtering.
    - HSS, Home Subscriber Server: the master database of subscriber profiles and authentication keys, the LTE equivalent of the HLR and AUC.
    - PCRF, Policy and Charging Rules Function: decides QoS policy and charging rules for each service flow.

    Supporting elements:
    - IMS, IP Multimedia Subsystem, which delivers VoLTE voice and video calling.
    - ANDSF for access network discovery and selection, and the ePDG for secure access over untrusted Wi-Fi.
    - Key interfaces: Uu between the UE and the eNodeB, S1-MME and S1-U between the eNodeB and the core, X2 between eNodeBs, and SGi from the P-GW to the Internet.
17. **Explain Bluetooth, Wi-Fi and Cellular Network.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1023 (ET: N/A)]*


    Answer:

    Bluetooth:
    - A short range wireless personal area network technology, IEEE 802.15.1, designed to replace cables between personal devices.
    - Works in the 2.4 GHz ISM band using frequency hopping spread spectrum at 1600 hops per second, which gives strong resistance to interference.
    - Range about 10 metres for class 2 and up to 100 metres for class 1; data rate 1 to 3 Mbps for classic Bluetooth and about 2 Mbps for Bluetooth Low Energy.
    - Topology is a piconet with one master and up to seven active slaves; interconnected piconets form a scatternet.
    - Very low power consumption, so it dominates headsets, wearables, keyboards and IoT sensors. Devices pair with a PIN and the link is encrypted.

    Wi-Fi:
    - A wireless local area network technology, IEEE 802.11, connecting devices to a LAN and the Internet without cable.
    - Works in the unlicensed 2.4 GHz, 5 GHz and 6 GHz bands, with an indoor range of 30 to 100 metres.
    - Uses CSMA/CA with RTS and CTS, since a radio cannot detect a collision while it is transmitting.
    - Data rates from 11 Mbps in 802.11b to about 9.6 Gbps theoretical in Wi-Fi 6, shared among all users of the access point.
    - An access point bridges the wireless clients to the wired network; several access points form an ESS allowing roaming. Security uses WPA2 and WPA3.

    Cellular network:
    - A wide area wireless network in which the coverage area is divided into cells, each served by a base station, so that the same frequencies can be reused in cells that are sufficiently far apart.
    - Uses licensed spectrum, with cells from a few hundred metres in a city to about 35 km in a rural area, and coverage extending nationwide and, through roaming, worldwide.
    - Core elements are the mobile station, the base station, the base station controller and the mobile switching centre, together with the HLR and VLR databases.
    - Handover transfers a call to the next cell as the user moves, so the connection is not lost.
    - Generations: 2G GSM for voice and SMS, 3G UMTS for data, 4G LTE as an all IP network at up to 1 Gbps, and 5G NR with about 1 ms latency and support for a million devices per square kilometre.
    - Comparison in one line: Bluetooth covers metres, Wi-Fi covers a building, and a cellular network covers a country.

## Transport Layer (TCP & UDP) (15)

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

   Given: 4000 bytes divided into 8 packets of 500 bytes, first sequence number 3001. Packets 1 to 5 arrive, packets 6 and 7 are lost, packet 8 arrives. The server carries no data of its own, so its sequence number stays fixed; it is taken as 8001 here.

   Sequence number of packet n = 3001 + (n − 1) × 500. The cumulative ACK is the number of the next byte the server expects.

   | SL | Client Packet Sequence No. | DB Server Sequence No. | ACK Sequence No. |
   |---|---|---|---|
   | 1 | 3001, bytes 3001 to 3500 | 8001 | 3501 |
   | 2 | 3501, bytes 3501 to 4000 | 8001 | 4001 |
   | 3 | 4001, bytes 4001 to 4500 | 8001 | 4501 |
   | 4 | 4501, bytes 4501 to 5000 | 8001 | 5001 |
   | 5 | 5001, bytes 5001 to 5500 | 8001 | 5501 |
   | 6 | 5501, bytes 5501 to 6000 | lost, no ACK | none |
   | 7 | 6001, bytes 6001 to 6500 | lost, no ACK | none |
   | 8 | 6501, bytes 6501 to 7000 | 8001 | 5501, a duplicate ACK |

   Explanation:
   - After the first five packets the server has received bytes 3001 to 5500 continuously, so it acknowledges 5501, meaning it now expects byte 5501.
   - Packets 6 and 7 never arrive, so no acknowledgement is generated for them.
   - Packet 8 arrives out of order. TCP cumulative acknowledgement can only acknowledge a continuous run of bytes, so the server cannot acknowledge 7001. It repeats ACK 5501, which is a duplicate ACK, and holds packet 8 in its out of order buffer.
   - When three duplicate ACKs of 5501 arrive, the client's fast retransmit triggers and it resends packet 6 without waiting for the timeout. After packet 6 arrives the server still holds a gap at packet 7, so it sends ACK 6001; once packet 7 also arrives the server can acknowledge everything including the buffered packet 8, and it sends ACK 7001.
   - With SACK enabled, the server would also report the block it already holds, 6501 to 7000, so the client would retransmit only packets 6 and 7 and nothing more.
2. **(b) Distinguish between TCP and UDP protocols.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 886 (ET: N/A)], [Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)], [BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 694 (ET: N/A)]*


   Answer:

   | Point | TCP | UDP |
   |---|---|---|
   | Full form | Transmission Control Protocol | User Datagram Protocol |
   | Definition | A reliable, connection oriented transport protocol. It makes sure the data arrives correctly and in the right order | A fast, connectionless transport protocol. It sends data with no guarantee of delivery |
   | Connection | Connection oriented, three way handshake before data | Connectionless, sends immediately |
   | Reliability | Reliable, acknowledgement and retransmission | Unreliable, fire and forget |
   | Ordering | In order delivery using sequence numbers | No ordering guarantee |
   | Header size | Variable, 20 to 60 bytes | Fixed, 8 bytes |
   | Flow control | Yes, sliding window | No |
   | Congestion control | Yes, slow start and AIMD | No |
   | Error control | Checksum plus retransmission | Checksum only, bad datagrams are dropped |
   | Speed and overhead | Slower, high overhead | Faster, minimal overhead |
   | Data boundary | Byte stream, no message boundary | Message oriented, boundaries preserved |
   | Broadcast and multicast | Not supported | Supported |
   | Handshake and teardown | SYN, SYN-ACK, ACK, then FIN exchange | None |
   | Typical use | HTTP, HTTPS, FTP, SMTP, SSH, Telnet, file transfer | DNS, DHCP, TFTP, SNMP, RIP, VoIP, video streaming, gaming |

   - Rule of thumb: use TCP when every byte must arrive correctly and in order, and UDP when speed and low delay matter more than perfection, such as live voice and video where a retransmitted packet would arrive too late to be of any use.
3. **Show the pictorial representation of TCP 3-way handshaking protocol for establishing a connection between a server and a client.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1339 (ET: N/A)]*


   Answer: TCP establishes a connection using a three way handshake.

   ```mermaid
   sequenceDiagram
       participant C as Client
       participant S as Server
       Note over C: CLOSED -> SYN-SENT
       C->>S: SYN, seq = x
       Note over S: LISTEN -> SYN-RECEIVED
       S->>C: SYN + ACK, seq = y, ack = x + 1
       Note over C: ESTABLISHED
       C->>S: ACK, seq = x + 1, ack = y + 1
       Note over S: ESTABLISHED
       C->>S: Data transfer begins
   ```

   Steps:
   - Step 1, SYN: the client sends a segment with the SYN flag set and its own initial sequence number x. It moves to the SYN-SENT state. No data is carried, but the SYN consumes one sequence number.
   - Step 2, SYN + ACK: the server replies with both SYN and ACK flags set. It sends its own initial sequence number y and acknowledges the client with ack = x + 1. It also advertises its receive window and MSS. The server moves to SYN-RECEIVED.
   - Step 3, ACK: the client acknowledges the server's SYN with ack = y + 1 and seq = x + 1. Both sides are now ESTABLISHED and data transfer can begin.

   Why three ways are needed:
   - The connection is full duplex, so both directions must be opened and both initial sequence numbers must be agreed and acknowledged.
   - It also synchronises the window sizes and the MSS, and it prevents an old delayed duplicate SYN from opening a spurious connection.
   - A connection is closed by a separate four way exchange of FIN and ACK in each direction.
4. **What is the deference between TCP and UDP?** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*


   Answer:

   | Point | TCP | UDP |
   |---|---|---|
   | Full form | Transmission Control Protocol | User Datagram Protocol |
   | Definition | A reliable, connection oriented transport protocol. It makes sure the data arrives correctly and in the right order | A fast, connectionless transport protocol. It sends data with no guarantee of delivery |
   | Connection | Connection oriented, three way handshake before data | Connectionless, sends immediately |
   | Reliability | Reliable, acknowledgement and retransmission | Unreliable, fire and forget |
   | Ordering | In order delivery using sequence numbers | No ordering guarantee |
   | Header size | Variable, 20 to 60 bytes | Fixed, 8 bytes |
   | Flow control | Yes, sliding window | No |
   | Congestion control | Yes, slow start and AIMD | No |
   | Error control | Checksum plus retransmission | Checksum only, bad datagrams are dropped |
   | Speed and overhead | Slower, high overhead | Faster, minimal overhead |
   | Data boundary | Byte stream, no message boundary | Message oriented, boundaries preserved |
   | Broadcast and multicast | Not supported | Supported |
   | Handshake and teardown | SYN, SYN-ACK, ACK, then FIN exchange | None |
   | Typical use | HTTP, HTTPS, FTP, SMTP, SSH, Telnet, file transfer | DNS, DHCP, TFTP, SNMP, RIP, VoIP, video streaming, gaming |
5. **3-way handshake protocol for TCP connection using diagram.** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 403 (ET: N/A)], [BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 876-877 (ET: BUET)]*


   Answer:

   ```mermaid
   sequenceDiagram
       participant C as Client
       participant S as Server
       Note over C: CLOSED -> SYN-SENT
       C->>S: SYN, seq = x
       Note over S: LISTEN -> SYN-RECEIVED
       S->>C: SYN + ACK, seq = y, ack = x + 1
       Note over C: ESTABLISHED
       C->>S: ACK, seq = x + 1, ack = y + 1
       Note over S: ESTABLISHED
       C->>S: Data transfer begins
   ```

   Steps:
   - Step 1, SYN: the client sends a segment with the SYN flag set and its own initial sequence number x. It moves to the SYN-SENT state. No data is carried, but the SYN consumes one sequence number.
   - Step 2, SYN + ACK: the server replies with both SYN and ACK flags set. It sends its own initial sequence number y and acknowledges the client with ack = x + 1. It also advertises its receive window and MSS. The server moves to SYN-RECEIVED.
   - Step 3, ACK: the client acknowledges the server's SYN with ack = y + 1 and seq = x + 1. Both sides are now ESTABLISHED and data transfer can begin.

   Why three ways are needed:
   - The connection is full duplex, so both directions must be opened and both initial sequence numbers must be agreed and acknowledged.
   - It also synchronises the window sizes and the MSS, and it prevents an old delayed duplicate SYN from opening a spurious connection.
   - A connection is closed by a separate four way exchange of FIN and ACK in each direction.
6. **Write a TCP/UDP used service name?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*


   Answer:

   Services that use TCP:
   - HTTP on port 80 and HTTPS on 443, web browsing.
   - FTP on ports 20 and 21, file transfer.
   - SMTP on 25, POP3 on 110 and IMAP on 143, email.
   - SSH on 22 and Telnet on 23, remote login.
   - Because these need every byte to arrive correctly and in order.

   Services that use UDP:
   - DNS on port 53 for queries.
   - DHCP on ports 67 and 68.
   - TFTP on 69.
   - SNMP on 161 and 162.
   - RIP on 520, VoIP, video streaming and online gaming.
   - Because these need speed and low delay, or are short single request and reply exchanges where retransmission by the application is cheaper than a connection setup.
7. **Difference between TCP and UDP. Distinguish between Cat5 and Cat6. Difference among exFAT, FAT32 and NTFS.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 523 (ET: MIST)]*


   Answer:

   TCP vs UDP:

   | Point | TCP | UDP |
   |---|---|---|
   | Full form | Transmission Control Protocol | User Datagram Protocol |
   | Definition | A reliable, connection oriented transport protocol. It makes sure the data arrives correctly and in the right order | A fast, connectionless transport protocol. It sends data with no guarantee of delivery |
   | Connection | Connection oriented, three way handshake before data | Connectionless, sends immediately |
   | Reliability | Reliable, acknowledgement and retransmission | Unreliable, fire and forget |
   | Ordering | In order delivery using sequence numbers | No ordering guarantee |
   | Header size | Variable, 20 to 60 bytes | Fixed, 8 bytes |
   | Flow control | Yes, sliding window | No |
   | Congestion control | Yes, slow start and AIMD | No |
   | Error control | Checksum plus retransmission | Checksum only, bad datagrams are dropped |
   | Speed and overhead | Slower, high overhead | Faster, minimal overhead |
   | Data boundary | Byte stream, no message boundary | Message oriented, boundaries preserved |
   | Broadcast and multicast | Not supported | Supported |
   | Handshake and teardown | SYN, SYN-ACK, ACK, then FIN exchange | None |
   | Typical use | HTTP, HTTPS, FTP, SMTP, SSH, Telnet, file transfer | DNS, DHCP, TFTP, SNMP, RIP, VoIP, video streaming, gaming |

   Cat5 vs Cat6:

   | Point | Cat5 and Cat5e | Cat6 |
   |---|---|---|
   | Bandwidth | 100 MHz for Cat5e | 250 MHz |
   | Data rate | 100 Mbps for Cat5, 1 Gbps for Cat5e | 1 Gbps at 100 m, 10 Gbps up to 55 m |
   | Construction | Fewer twists per inch, no separator | More twists, and a plastic spline separating the pairs |
   | Crosstalk and noise | Higher | Much lower, better NEXT and return loss |
   | Cable thickness and cost | Thinner, cheaper, more flexible | Thicker, costlier, stiffer |
   | Use | Legacy installations | Current standard for new structured cabling |

   exFAT vs FAT32 vs NTFS:

   | Point | FAT32 | exFAT | NTFS |
   |---|---|---|---|
   | Maximum file size | 4 GB | Practically unlimited, 16 EB | 16 TB and above |
   | Maximum volume size | 2 TB, 32 GB when formatted by Windows | 128 PB | 256 TB |
   | Journaling | No | No | Yes, so it recovers well from a crash |
   | Permissions and encryption | None | None | ACL permissions, EFS encryption, compression, quotas |
   | Compatibility | Highest, works on almost every device | Good, Windows, macOS, modern Linux and cameras | Full on Windows, read only by default on macOS |
   | Best use | Small USB drives and devices needing wide compatibility | Large USB drives, SD cards, external drives shared between systems | Windows system and data drives |
8. **Show a 3-way handshake protocol in TCP connection established using a diagram.** *[BICIC Assistant Programmer 2022 compact it 630 (ET: BUET)]*


   Answer: TCP uses a three way handshake to establish a connection.

   ```mermaid
   sequenceDiagram
       participant C as Client
       participant S as Server
       Note over C: CLOSED -> SYN-SENT
       C->>S: SYN, seq = x
       Note over S: LISTEN -> SYN-RECEIVED
       S->>C: SYN + ACK, seq = y, ack = x + 1
       Note over C: ESTABLISHED
       C->>S: ACK, seq = x + 1, ack = y + 1
       Note over S: ESTABLISHED
       C->>S: Data transfer begins
   ```

   Steps:
   - Step 1, SYN: the client sends a segment with the SYN flag set and its own initial sequence number x. It moves to the SYN-SENT state. No data is carried, but the SYN consumes one sequence number.
   - Step 2, SYN + ACK: the server replies with both SYN and ACK flags set. It sends its own initial sequence number y and acknowledges the client with ack = x + 1. It also advertises its receive window and MSS. The server moves to SYN-RECEIVED.
   - Step 3, ACK: the client acknowledges the server's SYN with ack = y + 1 and seq = x + 1. Both sides are now ESTABLISHED and data transfer can begin.

   Why three ways are needed:
   - The connection is full duplex, so both directions must be opened and both initial sequence numbers must be agreed and acknowledged.
   - It also synchronises the window sizes and the MSS, and it prevents an old delayed duplicate SYN from opening a spurious connection.
   - A connection is closed by a separate four way exchange of FIN and ACK in each direction.
9. **Differecne between TCP and UDP.** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 658 (ET: N/A)]*


   Answer:

   | Point | TCP | UDP |
   |---|---|---|
   | Full form | Transmission Control Protocol | User Datagram Protocol |
   | Definition | A reliable, connection oriented transport protocol. It makes sure the data arrives correctly and in the right order | A fast, connectionless transport protocol. It sends data with no guarantee of delivery |
   | Connection | Connection oriented, three way handshake before data | Connectionless, sends immediately |
   | Reliability | Reliable, acknowledgement and retransmission | Unreliable, fire and forget |
   | Ordering | In order delivery using sequence numbers | No ordering guarantee |
   | Header size | Variable, 20 to 60 bytes | Fixed, 8 bytes |
   | Flow control | Yes, sliding window | No |
   | Congestion control | Yes, slow start and AIMD | No |
   | Error control | Checksum plus retransmission | Checksum only, bad datagrams are dropped |
   | Speed and overhead | Slower, high overhead | Faster, minimal overhead |
   | Data boundary | Byte stream, no message boundary | Message oriented, boundaries preserved |
   | Broadcast and multicast | Not supported | Supported |
   | Handshake and teardown | SYN, SYN-ACK, ACK, then FIN exchange | None |
   | Typical use | HTTP, HTTPS, FTP, SMTP, SSH, Telnet, file transfer | DNS, DHCP, TFTP, SNMP, RIP, VoIP, video streaming, gaming |
10. **What is UDP protocol? UDP is reliable or not? Explain why or why not?** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 754 (ET: N/A)]*


    Answer: UDP, the User Datagram Protocol, is a connectionless transport layer protocol that sends independent datagrams without establishing a connection first.

    - Its header is only 8 bytes, containing the source port, destination port, length and checksum.
    - It performs no handshake, no acknowledgement, no sequencing, no flow control and no congestion control.
    - It preserves message boundaries and supports broadcast and multicast.

    Is UDP reliable? No, UDP is not reliable.

    Why it is not reliable:
    - There is no acknowledgement, so the sender never learns whether the datagram arrived.
    - There is no retransmission, so a lost datagram is lost for good.
    - There is no sequence number, so datagrams may arrive out of order and the receiver cannot reorder them.
    - There is no duplicate detection, so a duplicated datagram is delivered twice.
    - There is no flow control, so a fast sender can overwhelm a slow receiver and the excess is simply dropped.
    - The checksum only detects corruption; a corrupt datagram is discarded silently, not repaired.

    Why it is still used despite being unreliable:
    - It is fast, with an 8 byte header against TCP's 20, and no connection setup delay of one round trip.
    - For real time voice and video, a retransmitted packet would arrive too late to be played, so dropping it is better than delaying everything behind it.
    - For a short single request and reply such as DNS, retrying at the application layer is cheaper than a full TCP connection.
    - It supports broadcast and multicast, which TCP cannot.
    - Where reliability is needed over UDP, the application adds it itself, which is what QUIC and RTP with RTCP do.
11. **The primary function of the Transmission Control Protocol (TCP). TCP performs six basic functions. What are the basic function performing by TCP?** *[BTRC Assistant Director (Technical) 2021 compact it 807-808 (ET: IBA)]*


    Answer: The primary function of TCP is to provide a reliable, connection oriented, in-order byte stream service between two application processes over an unreliable IP network.

    The six basic functions performed by TCP:
    - Connection management: it establishes a connection with the three way handshake of SYN, SYN-ACK and ACK, maintains it, and closes it with the four way FIN and ACK exchange.
    - Reliable data transfer: every byte is numbered and acknowledged; unacknowledged data is retransmitted after a timeout, or immediately on three duplicate ACKs through fast retransmit.
    - Sequencing and in-order delivery: sequence numbers let the receiver reassemble segments in the correct order and discard duplicates, so the application sees a clean byte stream.
    - Flow control: the receiver advertises a window size in every acknowledgement, and the sender never transmits more than that, so a fast sender cannot overwhelm a slow receiver.
    - Congestion control: slow start, congestion avoidance, fast retransmit and fast recovery adjust the congestion window so the network itself is not overloaded.
    - Error detection and multiplexing: a checksum covering the header, data and pseudo header detects corruption, and port numbers multiplex many application conversations over one IP address.

    - Additional services worth mentioning: full duplex operation, segmentation of the byte stream into segments sized by the MSS, urgent data through the URG pointer, and buffering at both ends.
12. **(c) What is purpose of routers? How congestion control works in the TCP?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 886-887 (ET: N/A)]*


    Answer:

    Purpose of routers:
    - To connect two or more different networks and forward packets between them, which is what makes an internetwork possible.
    - To choose the best path by reading the destination IP address and consulting the routing table with a longest prefix match.
    - To build and maintain that routing table using static routes or dynamic protocols such as RIP, OSPF and BGP, and to adapt automatically when a link fails.
    - To separate broadcast domains, since a router does not forward broadcasts, which stops broadcast storms from spreading.
    - To perform fragmentation where the next link has a smaller MTU, and to decrement the TTL so that looping packets are eventually destroyed.
    - To provide additional services: NAT, DHCP, access control lists for filtering, QoS and WAN connectivity.

    How congestion control works in TCP:
    - TCP keeps a congestion window, cwnd, in addition to the receiver's advertised window, and the amount it may send is the smaller of the two.
    - Slow start: cwnd begins at one MSS and doubles every round trip time, that is exponential growth, until it reaches the slow start threshold ssthresh.
    - Congestion avoidance: beyond ssthresh, cwnd grows by only one MSS per round trip time, that is linear additive increase, so the network is probed gently.
    - Loss detected by timeout: this is taken as severe congestion. ssthresh is set to half the current window and cwnd drops back to one MSS, so slow start begins again.
    - Fast retransmit: three duplicate acknowledgements indicate a single lost segment while later ones are still arriving, so TCP retransmits it immediately without waiting for the timeout.
    - Fast recovery: after a fast retransmit, ssthresh and cwnd are halved rather than dropped to one, so the connection continues from half its previous rate. This whole pattern is called AIMD, additive increase multiplicative decrease.
    - Modern additions: ECN lets routers mark packets instead of dropping them, and algorithms such as CUBIC and BBR replace the classical growth rule on high speed links.
13. **What is a TCP Three-way handshaking step?** *[Sonali Bank Ltd. Officer IT 2021 compact it 909 (ET: N/A)]*


    Answer: The TCP three way handshake has three steps.

    - Step 1, SYN: the client sends a segment with the SYN flag set and its initial sequence number x, and moves to the SYN-SENT state.
    - Step 2, SYN + ACK: the server replies with both SYN and ACK set, its own initial sequence number y, and ack = x + 1. It also advertises its window size and MSS, and moves to SYN-RECEIVED.
    - Step 3, ACK: the client sends ACK with seq = x + 1 and ack = y + 1. Both sides are now ESTABLISHED and data can flow.

    ```mermaid
    sequenceDiagram
        participant C as Client
        participant S as Server
        Note over C: CLOSED -> SYN-SENT
        C->>S: SYN, seq = x
        Note over S: LISTEN -> SYN-RECEIVED
        S->>C: SYN + ACK, seq = y, ack = x + 1
        Note over C: ESTABLISHED
        C->>S: ACK, seq = x + 1, ack = y + 1
        Note over S: ESTABLISHED
        C->>S: Data transfer begins
    ```

    Steps:
    - Step 1, SYN: the client sends a segment with the SYN flag set and its own initial sequence number x. It moves to the SYN-SENT state. No data is carried, but the SYN consumes one sequence number.
    - Step 2, SYN + ACK: the server replies with both SYN and ACK flags set. It sends its own initial sequence number y and acknowledges the client with ack = x + 1. It also advertises its receive window and MSS. The server moves to SYN-RECEIVED.
    - Step 3, ACK: the client acknowledges the server's SYN with ack = y + 1 and seq = x + 1. Both sides are now ESTABLISHED and data transfer can begin.

    Why three ways are needed:
    - The connection is full duplex, so both directions must be opened and both initial sequence numbers must be agreed and acknowledged.
    - It also synchronises the window sizes and the MSS, and it prevents an old delayed duplicate SYN from opening a spurious connection.
    - A connection is closed by a separate four way exchange of FIN and ACK in each direction.
14. **The primary function of the Transmission Control Protocol (TCP) is to turn an unreliable network into a reliable network that is free from lost and duplicate packets. What are the functions performed by TCP to make a network more reliable?** *[Sonali & Janata Bank Officer (IT) 2020 compact it 990 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*


    Answer: TCP performs the following functions to turn an unreliable IP network into a reliable service.

    - Sequence numbering: every byte in the stream is numbered, so the receiver can place segments in the correct order however they arrive, and can detect a gap.
    - Acknowledgement: the receiver returns a cumulative acknowledgement giving the next byte it expects, so the sender knows exactly what has arrived safely.
    - Retransmission on timeout: the sender keeps a retransmission timer, calculated from the measured round trip time, and resends any segment that is not acknowledged in time.
    - Fast retransmit: three duplicate acknowledgements are taken as a sign that one segment was lost while later ones arrived, so it is resent at once instead of waiting for the timer.
    - Duplicate detection: because every byte is numbered, a duplicate segment is recognised and discarded, so the application never sees the same data twice.
    - Checksum: a 16 bit checksum over the header, the data and a pseudo header detects corruption; a corrupt segment is discarded and will be retransmitted.
    - Flow control: the receiver advertises its free buffer space as a window in every acknowledgement, and the sender never exceeds it, so no data is lost through receiver overflow.
    - Congestion control: slow start, congestion avoidance, fast retransmit and fast recovery keep the sending rate within what the network can carry, so loss caused by router queue overflow is minimised.
    - Connection management: the three way handshake agrees the initial sequence numbers and window sizes before any data flows, and the four way close ensures no data is lost at the end.
    - Buffering and reordering: segments arriving out of order are held in a receive buffer until the gap is filled, so the application always receives a continuous byte stream.

    - The result is that although IP may lose, duplicate, corrupt or reorder packets, the application above TCP sees an exact, ordered copy of what was sent.
15. **a) A live video stream will be transmitted. Which Transport layer protocol will you use and why?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1033 (ET: BUET)]*


    Answer: For a live video stream, UDP is the correct transport layer protocol, normally with RTP running on top of it.

    Reasons:
    - Real time delay matters more than perfection. A retransmitted packet would arrive after the moment it was needed and would have to be discarded anyway, so TCP's retransmission is wasted effort.
    - TCP's head of line blocking is fatal for live media: while one lost segment is being retransmitted, all the later data waits in the buffer, so the picture freezes. UDP simply carries on with the next frame.
    - TCP's congestion control halves the sending rate on any loss, which causes visible quality collapse and rebuffering. Live streaming prefers to control its own rate through adaptive bit rate logic.
    - Video codecs tolerate loss. A few missing packets cause a brief artefact that the decoder conceals, and the next key frame corrects it entirely.
    - The 8 byte UDP header against TCP's 20 saves bandwidth on a high volume continuous stream, and there is no connection setup delay.
    - UDP supports multicast, so one stream can serve thousands of viewers, which TCP cannot do at all.
    - RTP over UDP adds the sequence numbers and timestamps needed for playback ordering and synchronisation, and RTCP reports quality back, so the application gets exactly the features it needs and nothing more.

    - Caution worth stating: for stored, non-live video such as YouTube on demand, TCP based HTTP streaming, that is DASH or HLS, is used instead, because a few seconds of buffering is acceptable there and TCP passes through firewalls more easily.

## Networking Devices (14)

1. Describe the functions of a Switch and a Router and explain two key differences between these networking devices. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*


   Answer:

   Functions of a switch:
   - Works at the data link layer, layer 2, and connects devices inside one LAN.
   - Learns the source MAC address of every incoming frame and builds a MAC address table against the port.
   - Forwards a frame only out of the port where the destination MAC lives, floods it if the address is unknown, and filters it if source and destination are on the same port.
   - Gives each port its own collision domain and full duplex operation, so there are no collisions.
   - Supports VLANs, port security, STP for loop prevention and link aggregation.

   Functions of a router:
   - Works at the network layer, layer 3, and connects two or more different networks.
   - Examines the destination IP address and consults the routing table to choose the best next hop.
   - Builds and maintains that table using static routes or routing protocols such as RIP, OSPF and BGP.
   - Decrements the TTL, performs fragmentation where needed, and rewrites the layer 2 header at each hop.
   - Provides NAT, DHCP service, ACL filtering and WAN interfaces.

   Two key differences:
   - Layer and addressing: a switch works at layer 2 using MAC addresses within one network, while a router works at layer 3 using IP addresses to move traffic between different networks.
   - Broadcast domain: a switch forwards broadcasts, so all its ports remain one broadcast domain, whereas a router blocks broadcasts and creates a separate broadcast domain on each interface.
2. **Briefly describe the following network devices: Repeater, Hub, Bridge, Switch and Router.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 325 (ET: BIBM)]*


   Answer:

   - Repeater: a physical layer, layer 1, device with two ports that receives a weak signal, regenerates and retimes it, and sends it on. It extends the maximum cable length of a segment. It has no addressing and no filtering; whatever arrives is repeated, including noise-free but unwanted traffic.
   - Hub: a multiport repeater, also layer 1. Any frame arriving on one port is broadcast out of every other port. The whole hub is one collision domain and works half duplex with CSMA/CD, so performance falls badly with load. It is obsolete today.
   - Bridge: a layer 2 device with a small number of ports that joins two LAN segments. It learns MAC addresses and forwards a frame to the other segment only when the destination is there, so it divides collision domains and reduces unnecessary traffic. It does not divide broadcast domains.
   - Switch: a multiport bridge, layer 2, implemented in hardware with an ASIC. It keeps a MAC address table, forwards each frame only to the correct port, gives every port its own collision domain and supports full duplex. It also supports VLANs, STP and port security. This is the standard LAN device today.
   - Router: a layer 3 device that connects several networks and directs packets between them using IP addresses. It reads the destination IP, looks it up in the routing table, and sends the packet to the best next hop. It blocks broadcasts, so each interface is its own broadcast domain. It also provides NAT, DHCP, ACLs and WAN connectivity.
   - Gateway: a hardware device or a software node that works as the entry and exit point between two different networks that use different protocols. It translates the data so the two sides can understand each other. It works at layers 4 to 7.
   - Modem: it bridges the gap between digital computer data and analog signals, so a device can reach the internet over a telephone, cable or fibre line. It converts digital to analog, called modulation, and analog back to digital, called demodulation. Layer 1.
   - Access Point (AP): networking hardware that lets Wi-Fi devices such as laptops and phones join a wired network. It acts as a bridge between wired Ethernet and wireless devices. It does not route and does not hand out IP addresses. Layer 2.
   - NIC, Network Interface Card: the card inside the computer that physically connects it to the network. It carries the burned-in MAC address. It works at layers 1 and 2.

   Summary:

   | Device | OSI layer | Function |
   |---|---|---|
   | Repeater | 1, Physical | Amplifies and regenerates a weak signal |
   | Hub | 1, Physical | Broadcasts to all ports blindly |
   | Modem | 1, Physical | Converts digital to analog and back |
   | NIC | 1 and 2 | Connects the computer to the network, holds the MAC address |
   | Bridge | 2, Data link | Joins two LAN segments into one |
   | Switch | 2, Data link | Sends the frame only to the correct port, using the MAC table |
   | Access Point | 2, Data link | Bridges wireless devices to a wired network |
   | Router | 3, Network | Connects different networks, routes by IP address |
   | Gateway | 4 to 7 | Translates between two networks using different protocols |
3. **How many collision domians are created when you segment a network with a 12-port switch?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*


   Answer: A 12-port switch creates 12 collision domains, one per port, because every switch port is a separate collision domain.

   - It creates only 1 broadcast domain, since a switch forwards broadcasts out of all ports unless VLANs are configured.
   - By contrast a 12-port hub would give only 1 collision domain and 1 broadcast domain.
4. **Difference among Switch, Bridge and Router.** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 524 (ET: MIST)]*


   Answer:

   | Point | Bridge | Switch | Router |
   |---|---|---|---|
   | OSI layer | Data link, layer 2 | Data link, layer 2 | Network, layer 3 |
   | Address used | MAC | MAC | IP |
   | Ports | Few, typically 2 to 4 | Many, 8 to 48 or more | Few, usually 2 to 8, LAN and WAN |
   | Implementation | Software based | Hardware ASIC, so much faster | Software plus hardware, slowest per packet |
   | Collision domain | One per port, divides the segment | One per port | One per port |
   | Broadcast domain | Does not divide | Does not divide, unless VLANs | Divides, one per interface |
   | Forwarding table | MAC table, small | MAC table, large, learned dynamically | Routing table, built by static routes or RIP, OSPF, BGP |
   | Connects | Two segments of the same network | Devices within one network | Two or more different networks |
   | Extra features | Minimal | VLAN, STP, port security, link aggregation | NAT, DHCP, ACL, firewall, QoS, WAN protocols |

   - In short, a bridge is the ancestor of the switch, a switch is a fast multiport bridge, and a router is the device that actually joins different networks together.
5. **Differentiate between Collision Domain and Broadcast Domain in computer network. What is the function of DNS and DHCP?** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 535 (ET: MIST)]*


   Answer:

   Collision domain vs broadcast domain:

   | Point | Collision domain | Broadcast domain |
   |---|---|---|
   | Definition | The set of devices whose frames can collide with one another on a shared medium | The set of devices that receive a broadcast frame sent by any one of them |
   | Layer concerned | Physical and MAC | Data link and network |
   | Divided by | Bridge, switch, router | Router, or a VLAN on a switch |
   | Not divided by | Hub, repeater | Hub, repeater, bridge, plain switch |
   | Effect of growth | More collisions, more retransmission, less throughput | More broadcast traffic, wasted CPU on every host, risk of a broadcast storm |
   | Example count | A 24-port switch gives 24 collision domains | The same switch gives 1 broadcast domain |

   Function of DNS:
   - The Domain Name System translates a human readable domain name such as `www.example.com` into the IP address needed to reach it, and also does the reverse lookup.
   - It is a distributed hierarchical database of root servers, TLD servers and authoritative servers, and it uses UDP port 53 for queries and TCP 53 for zone transfers.
   - It also provides MX records for mail routing, CNAME aliases and load distribution across several servers.

   Function of DHCP:
   - The Dynamic Host Configuration Protocol automatically leases an IP address, subnet mask, default gateway and DNS server address to a client.
   - It uses UDP ports 67 and 68 and the DORA exchange, and it prevents duplicate addresses and removes the need for manual configuration.
6. **Write down the difference between gateway and firewall.** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 476 (ET: N/A)]*


   Answer:

   | Point | Gateway | Firewall |
   |---|---|---|
   | Purpose | Joins two networks that use different protocols or architectures and translates between them | Controls which traffic is allowed to pass, based on a security policy |
   | Main job | Protocol conversion and connectivity | Filtering, inspection and blocking |
   | OSI layer | Can work at any layer, up to and including the application layer | Layer 3 and 4 for a packet filter, up to layer 7 for an application firewall |
   | Focus | Communication and interoperability | Security |
   | Decision made | How to translate and where to forward | Permit or deny |
   | Example | An email gateway converting between two mail formats, a VoIP gateway between IP and PSTN, the default gateway of a LAN | An ACL on a router, iptables, a Cisco ASA, a web application firewall |
   | If removed | The two networks cannot talk at all | The networks still talk, but with no protection |

   - The two roles are often combined in one box, for example a home router acts as the default gateway, performs NAT and also runs a basic firewall, but the functions themselves are distinct.
7. **What is gateway? Is router and gateway have any difference?** *[BEPZA Programmer 03.11.2023 compact it 562 (ET: N/A)]*


   Answer: A gateway is a device or software that connects two networks using different protocols, architectures or data formats, and translates between them so that the two can communicate.

   - It can operate at any layer of the OSI model, right up to the application layer, since translation may involve changing the data format itself.
   - Examples: a VoIP gateway between an IP network and the PSTN, an email gateway between two mail systems, an IoT gateway between Zigbee sensors and TCP/IP, and a payment gateway.
   - In everyday LAN usage, the phrase default gateway simply means the router interface that a host uses to reach anything outside its own subnet.

   Difference between router and gateway:

   | Point | Router | Gateway |
   |---|---|---|
   | Function | Forwards packets between networks that use the same protocol, normally IP | Translates between networks that use different protocols or formats |
   | Layer | Network layer, layer 3 | Any layer, often the application layer |
   | Complexity | Reads the IP header and consults the routing table | May rebuild the whole message in another format |
   | Relationship | A router is one kind of gateway | A gateway is the broader term |

   - So yes, there is a difference: every router acting as an exit point is a gateway, but not every gateway is a router. A router routes; a gateway translates.
8. **অথবা, (ক) ডেটা ট্রান্সমিশনে Router ও Gateway এর মধ্যে কোনটি অধিকতর সুবিধাজনক-মতামত ব্যক্ত করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 615 (ET: N/A)]*

   Answer: A router and a gateway perform different roles, so which is more advantageous depends on what kind of networks are being joined.

   | Point | Router | Gateway |
   |---|---|---|
   | Function | Forwards packets from one IP network to another | Translates between two networks using different protocols or data formats |
   | Layer | Network layer, layer 3 | Any layer, most often the application layer |
   | Speed | Much faster, forwarding is done in hardware | Slower, because the whole message may have to be converted |
   | Cost | Lower | Higher |
   | Example | Sending traffic from a LAN to the Internet | VoIP to PSTN, or an IoT Zigbee network to TCP/IP |

   Opinion:
   - If both networks use the same protocol, that is TCP/IP, the router is clearly the more advantageous choice. It is faster, cheaper and scalable, and with a routing protocol it finds the best path by itself.
   - If the two networks use different protocols or data formats, a router can do nothing at all, and a gateway is the only possible solution.
   - Today's Internet is almost entirely TCP/IP based, so in practice the router is used in the great majority of cases and the gateway is needed only in special situations.
   - In practical equipment the two are combined: a home router is simultaneously the default gateway, the NAT device and the firewall.
9. **Write the Difference among Network Switch, Hub and Router.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1023 (ET: N/A)], [DESCO Sub-Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)], [BMA Signal Assistant Engineer (Computer) 2021 compact it 933 (ET: BUET)]*


   Answer:

   | Point | Hub | Switch | Router |
   |---|---|---|---|
   | OSI layer | Physical, layer 1 | Data link, layer 2 | Network, layer 3 |
   | Addressing used | None, it is a dumb repeater | MAC address | IP address |
   | Forwarding | Broadcasts the frame out of every port | Forwards only to the correct port using the MAC table | Forwards between networks using the routing table |
   | Collision domain | One for the whole hub | One per port | One per port |
   | Broadcast domain | One | One, unless VLANs are used | One per interface, it breaks broadcasts |
   | Duplex | Half duplex, uses CSMA/CD | Full duplex | Full duplex |
   | Connects | Devices in one LAN segment | Devices in one LAN | Two or more different networks |
   | Intelligence and cost | None, cheapest, now obsolete | Learns addresses, moderate cost | Runs routing protocols, most expensive |
   | NAT, DHCP, firewall | No | No, except on layer 3 switches | Yes |

   - Summary: a hub simply repeats the electrical signal, a switch makes an intelligent forwarding decision inside one network, and a router makes a routing decision between different networks.
10. **(iii) Router and Gateway এর ফাংশন লিখুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 789 (ET: N/A)]*

    Answer:

    Functions of a router:
    - It works at layer 3, the network layer, and connects two or more different networks.
    - It reads the destination IP address of a packet, performs a longest prefix match in the routing table and selects the best next hop.
    - It builds and updates that routing table with static routes or with routing protocols such as RIP, OSPF and BGP.
    - It decrements the TTL at every hop, fragments the packet where the next link has a smaller MTU, and rewrites the layer 2 header.
    - It blocks broadcasts, so every interface forms a separate broadcast domain.
    - It also provides NAT, a DHCP service, filtering with access control lists, QoS and WAN connectivity.

    Functions of a gateway:
    - It connects two networks that use different protocols, architectures or data formats and translates between them.
    - It can operate at any layer of the OSI model, up to and including the application layer, because the whole format of the message may have to be changed.
    - It acts as the entry and exit point of a network; hosts on a LAN use the default gateway to reach anything outside their own subnet.
    - Examples: a VoIP gateway converting an IP call into a PSTN call, an email gateway translating between two mail systems, and an IoT gateway bringing Zigbee sensor data onto TCP/IP.
    - It often performs protocol conversion and security functions together, as an API gateway does.
11. **Write down the difference between Hub and Switch.** *[DMLC Assistant Teacher (ICT) 2021 compact it 825 (ET: N/A)]*


    Answer:

    | Point | Hub | Switch |
    |---|---|---|
    | OSI layer | Physical, layer 1 | Data link, layer 2 |
    | Intelligence | None, a multiport repeater | Learns MAC addresses and keeps a table |
    | Forwarding | Broadcasts the frame out of every port | Sends the frame only to the destination port |
    | Collision domain | One for the whole device | One per port, so effectively none |
    | Duplex | Half duplex, CSMA/CD is needed | Full duplex |
    | Bandwidth | Shared among all ports | Dedicated per port |
    | Security | Poor, every device sees every frame | Better, frames go only where they are needed |
    | Performance under load | Falls sharply as nodes increase | Stays high |
    | Cost and status | Cheap but obsolete | Slightly costlier, the standard device today |
12. **Wi-Fi access point বলতে কী বুঝানো হয়? Router and Switch -এর মধ্যে পার্থক্য লিখুন।** *[41th BCS 2021 compact it 883 (ET: N/A)]*

    Answer:

    Wi-Fi access point:
    - A Wi-Fi access point is a networking device that connects wireless clients, such as laptops and mobile phones, to a wired LAN. It converts radio signals into Ethernet frames and Ethernet frames back into radio signals.
    - It works at layer 2 and is essentially a wireless bridge. It follows the IEEE 802.11 standard and controls access to the medium with CSMA/CA.
    - Each access point broadcasts an SSID; the client authenticates and associates with it, and the traffic is encrypted with WPA2 or WPA3.
    - The coverage area of one access point is called a BSS, and several access points together form an ESS, within which a client can roam from one access point to another.
    - In a home router the access point, the switch and the router are combined in a single box, but in an enterprise the access point is a separate device managed by a WLAN controller.

    Difference between a router and a switch:

    | Point | Router | Switch |
    |---|---|---|
    | Layer | Network layer, layer 3 | Data link layer, layer 2 |
    | Address used | IP address | MAC address |
    | Function | Forwards packets between different networks | Forwards frames within one LAN |
    | Table | Routing table | MAC address table |
    | Broadcast | Blocks it, so each interface is a separate broadcast domain | Forwards it, so all ports form one broadcast domain |
    | Number of ports | Few, typically 2 to 8 | Many, 8 to 48 or more |
    | Extra features | NAT, DHCP, ACL, firewall, WAN links | VLAN, STP, port security, link aggregation |
    | Speed and cost | Comparatively slower and more expensive | Faster and cheaper |
13. **হাব, সুইচ ও রাউটার এর মধ্যে পার্থক্য লিখ।** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 947 (ET: BUET)]*

    Answer:

    | Point | Hub | Switch | Router |
    |---|---|---|---|
    | OSI layer | Physical, layer 1 | Data link, layer 2 | Network, layer 3 |
    | Addressing used | None, it is a dumb repeater | MAC address | IP address |
    | Forwarding | Broadcasts the frame out of every port | Forwards only to the correct port using the MAC table | Forwards between networks using the routing table |
    | Collision domain | One for the whole hub | One per port | One per port |
    | Broadcast domain | One | One, unless VLANs are used | One per interface, it breaks broadcasts |
    | Duplex | Half duplex, uses CSMA/CD | Full duplex | Full duplex |
    | Connects | Devices in one LAN segment | Devices in one LAN | Two or more different networks |
    | Intelligence and cost | None, cheapest, now obsolete | Learns addresses, moderate cost | Runs routing protocols, most expensive |
    | NAT, DHCP, firewall | No | No, except on layer 3 switches | Yes |

    - In short: a hub understands nothing and simply repeats the signal; a switch reads the MAC address and sends the frame to the correct port; and a router reads the IP address and sends the packet from one network to another.
14. **(c) Briefly describe three devices using which different LANs can be connected.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1030 (ET: N/A)]*


    Answer: Three devices used to connect different LANs are the bridge, the switch and the router.

    - Bridge: a data link layer, layer 2, device that joins two LAN segments using the same protocol. It learns MAC addresses and forwards a frame across only when the destination lies on the other side, so it separates collision domains and reduces unnecessary traffic. It keeps both segments in one broadcast domain and one IP network.
    - Switch: a multiport bridge implemented in hardware, also layer 2. It joins many LAN segments, keeps a MAC address table, gives each port its own collision domain and full duplex operation, and can separate LANs logically using VLANs. A layer 3 switch can also route between those VLANs at wire speed.
    - Router: a network layer, layer 3, device that connects LANs belonging to different IP networks, which is the usual case for two separate LANs. It reads the destination IP address, consults the routing table and forwards the packet to the best next hop. It blocks broadcasts, so each connected LAN becomes its own broadcast domain, and it also provides NAT, ACL filtering and WAN links.

    - A gateway is mentioned as a fourth option when the two LANs use entirely different protocols or data formats, since it performs the necessary translation.

## Communication System & Transmission Modes (14)

1. What is a communication system? Describe the different types of transmission modes with examples. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*


   Answer: A communication system is the complete set of hardware, software and rules that carries information from a source to a destination over a medium.

   Its five components are the message, the sender, the receiver, the transmission medium and the protocol. Noise is always present on the medium and the system must be designed to resist it.

   Types of transmission mode, that is the direction of data flow:

   - Simplex: data flows in one direction only. The sender can only send and the receiver can only receive, so the whole channel capacity is used in that one direction. Examples: keyboard to computer, computer to monitor, radio and TV broadcast, a public address system.
   - Half duplex: data flows in both directions but only one direction at a time. The devices take turns, so there is a turnaround delay. Examples: walkie-talkie, CB radio, a hub based Ethernet segment using CSMA/CD.
   - Full duplex: data flows in both directions simultaneously, so the capacity is shared between the two directions or two separate channels are used. Examples: telephone, mobile phone conversation, modern switched Ethernet, most Internet connections.

   - A useful comparison: simplex uses the full capacity in one direction, half duplex uses the full capacity but alternately, and full duplex divides the capacity or the medium between two simultaneous directions.
2. **How many types of modes are used in data transferring through networks? Briefly explain those modes. Differentiate between TCP vs UDP.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 338 (ET: BIBM)]*


   Answer: Three modes of data transfer are used, based on the direction of flow.

   - Simplex: data flows in one direction only. The sender can only send and the receiver can only receive, so the whole channel capacity is used in that one direction. Examples: keyboard to computer, computer to monitor, radio and TV broadcast, a public address system.
   - Half duplex: data flows in both directions but only one direction at a time. The devices take turns, so there is a turnaround delay. Examples: walkie-talkie, CB radio, a hub based Ethernet segment using CSMA/CD.
   - Full duplex: data flows in both directions simultaneously, so the capacity is shared between the two directions or two separate channels are used. Examples: telephone, mobile phone conversation, modern switched Ethernet, most Internet connections.

   TCP vs UDP:

   | Point | TCP | UDP |
   |---|---|---|
   | Connection | Connection oriented, three way handshake first | Connectionless, sends immediately |
   | Reliability | Reliable, acknowledgements and retransmission | Unreliable, no acknowledgement |
   | Ordering | Delivers in order using sequence numbers | No ordering, packets may arrive out of order |
   | Header size | 20 to 60 bytes | 8 bytes |
   | Flow and congestion control | Both present, sliding window and AIMD | Neither |
   | Speed | Slower, more overhead | Faster, minimal overhead |
   | Error handling | Checksum plus retransmission | Checksum only, corrupt packets are discarded |
   | Broadcast and multicast | Not supported | Supported |
   | Typical use | HTTP, HTTPS, FTP, SMTP, SSH, email, file transfer | DNS, DHCP, TFTP, SNMP, VoIP, video streaming, online gaming |
3. **(b) Name and define five components of Data communication system with necessary diagram.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 487 (ET: N/A)]*


   Answer: A data communication system has five components.

   - Message: the actual information to be communicated, that is text, number, image, audio or video.
   - Sender: the device that originates and transmits the message, for example a computer, a phone or a camera.
   - Receiver: the device that receives the message, for example a computer, a phone or a television.
   - Transmission medium: the physical path over which the message travels, either guided such as twisted pair, coaxial or fibre, or unguided such as radio, microwave or infrared.
   - Protocol: the set of rules that governs the communication, covering syntax, semantics and timing. Without a shared protocol the two devices cannot understand each other even if they are physically connected.

   ```mermaid
   graph LR
       A["Sender / Source"] --> B["Transmitter / Encoder"]
       B --> C["Transmission medium: guided or unguided"]
       C --> D["Receiver / Decoder"]
       D --> E["Destination"]
       F["Protocol: rules of syntax, semantics and timing"] -.-> C
       G["Noise"] -.-> C
   ```
4. **(a) Differentiate between half-duplex and full duplex transmission.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 489 (ET: N/A)]*


   Answer:

   | Point | Half duplex | Full duplex |
   |---|---|---|
   | Direction | Both directions, but only one at a time | Both directions at the same time |
   | Channel use | The whole capacity is used by whichever side is sending | The capacity is shared, or two separate channels are used |
   | Turnaround delay | Present, the line must be reversed before the other side can send | None |
   | Efficiency and throughput | Lower | Higher, up to double |
   | Collision | Possible, so CSMA/CD is needed on shared media | Not possible on a dedicated link |
   | Cost and complexity | Simpler and cheaper | More complex, needs two paths or echo cancellation |
   | Examples | Walkie-talkie, CB radio, hub based Ethernet | Telephone, mobile call, switched Ethernet |
5. **(গ) উদাহরণসহ Simplex, half-duplex এবং duplex কমিউনিকেশন সিস্টেমের পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 628 (ET: N/A)]*

   Answer:

   | Point | Simplex | Half duplex | Full duplex |
   |---|---|---|---|
   | Direction | One direction only | Both directions, but only one at a time | Both directions at the same time |
   | Channel capacity | The whole capacity is used in one direction | The whole capacity, but used alternately | Divided between the two directions, or two separate channels |
   | Turnaround delay | Not applicable | Present | None |
   | Performance | Least flexible | Moderate | Best |
   | Cost | Lowest | Moderate | Highest |
   | Examples | Keyboard to computer, monitor, radio and television broadcast | Walkie-talkie, CB radio, hub based Ethernet | Telephone, mobile call, switched Ethernet |

   - In simplex the receiver can never reply, so it suits one way broadcasting only.
   - In half duplex one side must finish before the other can begin, which is why CSMA/CD is needed on a shared medium.
   - In full duplex two separate paths or echo cancellation allow sending and receiving at the same instant, so the throughput can be double that of half duplex.
6. **What is the difference between Synchronous and Asynchronous transmission?** *[CAAB Assistant Maintenance Engineer (AME) 2022 compact it 723 (ET: N/A)], [RAKUB Assistant Network System Engineer 03.11.2023 compact it 550 (ET: BIBM)]*


   Answer:

   | Point | Synchronous transmission | Asynchronous transmission |
   |---|---|---|
   | Unit sent | A continuous block or frame of many characters | One character at a time, typically 8 bits |
   | Start and stop bits | Not used | Each character is framed by a start bit and one or two stop bits |
   | Timing | The sender and receiver clocks are synchronised, using a common clock or an embedded clock in the line coding | No common clock; the receiver resynchronises on every start bit |
   | Gaps | No gap between characters; the block is sent as one stream | Variable gaps allowed between characters |
   | Overhead | Low, only the frame header and trailer | High, about 20 to 25 percent extra for start and stop bits |
   | Speed | Fast, suitable for high data rates | Slower |
   | Cost and complexity | Costlier, needs clock recovery circuitry | Cheap and simple |
   | Error handling | CRC over the whole frame | Parity bit per character |
   | Examples | Ethernet, SONET, ATM, USB bulk transfer, ISDN | RS-232 serial port, keyboard to computer, old modems, UART |

   - In short, asynchronous transmission suits slow and bursty traffic where simplicity matters, while synchronous transmission suits large continuous volumes of data where efficiency matters.
7. **Briefly mention the main रणनीति impairments in telecommunication channel. Considering these impairments explain which communication is better between analog and digital communication systems?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*


   Answer: The main impairments in a telecommunication channel are the following.

   - Attenuation: the signal loses strength with distance, since energy is absorbed by the medium. It is measured in dB, and it is also frequency dependent, so different components of the signal fade unequally. Amplifiers and repeaters correct it.
   - Distortion: different frequency components travel at different speeds, so the shape of the signal changes and pulses spread out, causing intersymbol interference. Equalisers correct it.
   - Noise: unwanted energy added to the signal. Thermal noise from random electron motion, intermodulation noise from non-linearity, crosstalk from a neighbouring pair, and impulse noise from lightning or switching spikes.
   - Delay distortion and jitter: variation in propagation delay across frequencies and in time.
   - Fading and multipath, particularly on wireless links, and echo on long copper circuits.

   Which is better, analog or digital, considering these impairments:
   - Digital communication is clearly better.
   - In an analog system every amplifier boosts the noise together with the signal, so noise accumulates over every hop and the quality falls steadily along the route; it can never be recovered.
   - In a digital system a regenerative repeater only has to decide whether the received symbol is a 0 or a 1. As long as the noise is below the decision threshold, a clean new pulse is produced and the noise is removed completely, so quality does not degrade with distance.
   - Digital transmission can add error detection and correction such as CRC and Hamming or Reed-Solomon codes, which analog cannot.
   - Digital signals can be encrypted, compressed, multiplexed by TDM and processed by cheap integrated circuits, and different kinds of traffic, voice, video and data, can share the same channel.
   - The cost is a wider bandwidth requirement and the need for analog to digital conversion, but the benefits far outweigh this, which is why all modern networks are digital.
8. **Describe the data communication system with necessary diagram.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 679 (ET: N/A)]*


   Answer: A data communication system is an arrangement of hardware and software that exchanges data between two devices through a transmission medium according to an agreed protocol.

   Its five components:

   - Message: the actual information to be communicated, that is text, number, image, audio or video.
   - Sender: the device that originates and transmits the message, for example a computer, a phone or a camera.
   - Receiver: the device that receives the message, for example a computer, a phone or a television.
   - Transmission medium: the physical path over which the message travels, either guided such as twisted pair, coaxial or fibre, or unguided such as radio, microwave or infrared.
   - Protocol: the set of rules that governs the communication, covering syntax, semantics and timing. Without a shared protocol the two devices cannot understand each other even if they are physically connected.

   ```mermaid
   graph LR
       A["Sender / Source"] --> B["Transmitter / Encoder"]
       B --> C["Transmission medium: guided or unguided"]
       C --> D["Receiver / Decoder"]
       D --> E["Destination"]
       F["Protocol: rules of syntax, semantics and timing"] -.-> C
       G["Noise"] -.-> C
   ```

   Characteristics that decide how effective the system is:
   - Delivery: the data must reach the correct destination and only that destination.
   - Accuracy: the data must arrive without alteration; errors must be detected and corrected.
   - Timeliness: data must arrive in time, which is critical for real time traffic such as voice and video.
   - Jitter: the variation in packet arrival time must be small, otherwise playback is uneven.
9. **Write down the Data Communication elements.** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*


   Answer: The elements of data communication are:

   - Message: the actual information to be communicated, that is text, number, image, audio or video.
   - Sender: the device that originates and transmits the message, for example a computer, a phone or a camera.
   - Receiver: the device that receives the message, for example a computer, a phone or a television.
   - Transmission medium: the physical path over which the message travels, either guided such as twisted pair, coaxial or fibre, or unguided such as radio, microwave or infrared.
   - Protocol: the set of rules that governs the communication, covering syntax, semantics and timing. Without a shared protocol the two devices cannot understand each other even if they are physically connected.
10. **(ক) Data Communication System এর পাঁচটি প্রধান Component এর চিত্রসহকারে বর্ণনা দিন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 704 (ET: N/A)]*

    Answer: A data communication system has five components.

    - Message: the actual information to be communicated, that is text, numbers, images, audio or video.
    - Sender: the device that originates and transmits the message, for example a computer, a phone or a camera.
    - Receiver: the device that receives the message, for example a computer, a phone or a television.
    - Transmission medium: the physical path along which the message travels, either guided such as twisted pair, coaxial cable or fibre, or unguided such as radio, microwave or infrared.
    - Protocol: the set of rules governing the communication, covering syntax, semantics and timing. Without a shared protocol two devices cannot understand each other even when they are physically connected.

    ```mermaid
    graph LR
        A["Sender / Source"] --> B["Transmitter / Encoder"]
        B --> C["Transmission medium: guided or unguided"]
        C --> D["Receiver / Decoder"]
        D --> E["Destination"]
        F["Protocol: rules of syntax, semantics and timing"] -.-> C
        G["Noise"] -.-> C
    ```

    - If any one of these five is missing, communication is impossible: without a message there is nothing to send, without a sender or receiver there is nobody at the ends, without a medium there is no path, and without a protocol the two devices cannot understand each other's language.
11. **(খ) Data Communication কত প্রকার? উদাহরণসহ সংক্ষিপ্ত বর্ণনা দিন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 704 (ET: N/A)]*

    Answer: Data communication is classified from three points of view.

    By the direction of data flow, three types:
    - Simplex: data travels in one direction only. Examples: keyboard to computer, computer to monitor, radio and television broadcast.
    - Half duplex: data travels in both directions but only one at a time. Examples: walkie-talkie, CB radio, hub based Ethernet.
    - Full duplex: data travels in both directions at the same time. Examples: telephone, mobile call, switched Ethernet.

    By the nature of the signal, two types:
    - Analog data communication: the signal varies continuously, as on an old telephone line or in AM and FM radio.
    - Digital data communication: the signal is carried as discrete 0s and 1s, as in a computer network. It is far more resistant to noise, because a repeater can regenerate the signal completely.

    By the method of synchronisation, two types:
    - Asynchronous: each character is sent separately, framed by a start bit and one or two stop bits. Example: an RS-232 serial port.
    - Synchronous: a large block is sent as one stream with a common clock. Examples: Ethernet, SONET.
12. **Define full duplex with an example.** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*


    Answer: Full duplex is a transmission mode in which data flows in both directions at the same time, so each device can send and receive simultaneously.

    - This is achieved either by using two separate physical channels, one for each direction, or by dividing the capacity of a single channel between the two directions, or by echo cancellation.
    - Example: a telephone conversation, where both people can speak and hear at the same instant. Another example is modern switched Ethernet, where a device uses one pair of wires to transmit and another pair to receive, so there are no collisions and CSMA/CD is unnecessary.
13. **Which communication mode use serial communication? (a) Duplex (b) Half Duplex (c) Simplex (d) All** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*


    Answer: The correct option is (d) All.

    - Serial communication means the bits are sent one after another over a single line, and this is independent of the direction of flow.
    - Simplex, half duplex and full duplex all describe the direction of the data, not the way the bits are placed on the wire, so all three modes can and do use serial communication.
    - Almost all long distance and network communication is serial, because parallel transmission suffers from crosstalk, clock skew and high cable cost over distance.
14. **(c) Illustrate a communication model in simplified form.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1027-1028 (ET: N/A)]*


    Answer: A simplified communication model has five parts: the source, the transmitter, the transmission system, the receiver and the destination.

    ```mermaid
    graph LR
        A["Source: e.g. computer"] --> B["Transmitter: e.g. modem"]
        B --> C["Transmission System: e.g. public telephone network"]
        C --> D["Receiver: e.g. modem"]
        D --> E["Destination: e.g. server"]
        N["Noise"] -.-> C
    ```

    - Source: generates the data to be transmitted, for example a computer producing a bit stream.
    - Transmitter: converts and encodes that data into a signal suitable for the medium, for example a modem turning a digital bit stream into an analog signal.
    - Transmission system: the path carrying the signal, from a single link to a complex network, and this is where attenuation, distortion and noise act on the signal.
    - Receiver: converts the received signal back into a form the destination can handle, for example a modem recovering the bit stream.
    - Destination: takes the incoming data from the receiver and uses it.

    - Example flow: a workstation sends a file, its modem modulates the bits onto the telephone line, the network carries the signal, the modem at the far end demodulates it, and the server stores the file.

## Physical Layer & Transmission Media (Cables & Wiring) (14)

1. **Straight through connection vs Crossover connection.** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1448 (ET: N/A)]*


   Answer:

   | Point | Straight through cable | Crossover cable |
   |---|---|---|
   | Wiring | Both ends use the same standard, T568A-T568A or T568B-T568B | One end T568A and the other end T568B |
   | Pin mapping | Pin 1 to pin 1, pin 2 to pin 2, and so on | Pins 1 and 2 swap with pins 3 and 6 |
   | Connects | Unlike devices | Like devices |
   | Examples | PC to switch, PC to hub, router to switch, switch to router | PC to PC, switch to switch, hub to hub, router to router, PC to router |
   | Reason | The two devices already transmit and receive on opposite pairs | Both devices transmit on the same pair, so the pairs must be crossed |

   - Modern equipment supports Auto-MDIX, which detects the situation and crosses the pairs internally, so in practice a straight through cable now works in almost every case.
2. **Which transmission medium is used in LAN? Write their maximum length and capacity (bps).** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1452 (ET: N/A)]*


   Answer: The transmission media used in a LAN are twisted pair copper cable, coaxial cable, optical fibre and wireless radio.

   | Medium | Standard | Maximum length | Capacity |
   |---|---|---|---|
   | UTP Cat 5e | 1000BASE-T | 100 m | 1 Gbps |
   | UTP Cat 6 | 1000BASE-T, 10GBASE-T | 100 m at 1 Gbps, 55 m at 10 Gbps | 1 to 10 Gbps |
   | UTP Cat 6A | 10GBASE-T | 100 m | 10 Gbps |
   | Thin coaxial | 10BASE2 | 185 m | 10 Mbps |
   | Thick coaxial | 10BASE5 | 500 m | 10 Mbps |
   | Multimode fibre | 1000BASE-SX | 220 to 550 m | 1 Gbps and above |
   | Single mode fibre | 1000BASE-LX | 5 to 40 km, up to 100 km | 1 Gbps to terabits with WDM |
   | Wireless, Wi-Fi 6 | IEEE 802.11ax | 30 to 50 m indoors | up to 9.6 Gbps theoretical |

   - Twisted pair Cat 5e or Cat 6 is the usual choice for desk connections, and fibre is used for the backbone between floors and buildings.
3. **IEEE __________ Standard used Ethernet LAN?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: IEEE 802.3 is the standard used for Ethernet LAN.

   - It defines the physical layer and the MAC sublayer of wired Ethernet, including the CSMA/CD access method and the frame format.
   - For reference, IEEE 802.11 is Wireless LAN, 802.15 is Bluetooth and WPAN, 802.16 is WiMAX and 802.5 was Token Ring.
4. **What is the connector name copper cable in LAN?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*


   Answer: The connector used with copper cable in a LAN is the RJ-45 connector.

   - It is an eight pin modular connector, 8P8C, crimped onto UTP or STP cable following the T568A or T568B wiring standard.
   - For reference, RJ-11 with four or six pins is used for telephone lines, BNC for thin coaxial Ethernet, AUI for thick coaxial, and SC, LC or ST connectors for optical fibre.
5. **What are the different types of transmission media used for data communication? Explain their advantages and disadvantages.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 326 (ET: BIBM)]*


   Answer: Transmission media fall into two categories, guided and unguided.

   Guided media:
   - Twisted pair, UTP and STP. Advantages: cheapest, light, easy to install and terminate with RJ-45, adequate for 1 to 10 Gbps LANs. Disadvantages: high attenuation, limited to 100 m, poor immunity to EMI and crosstalk in UTP, easy to tap.
   - Coaxial cable. Advantages: better bandwidth and much better EMI immunity than twisted pair because of the shield, longer segments, cheap for cable TV distribution. Disadvantages: bulky and stiff, harder to install, a single break can affect a whole bus segment, largely obsolete for LANs.
   - Optical fibre. Advantages: enormous bandwidth, very low attenuation of 0.2 dB/km, complete immunity to EMI and crosstalk, high security since a tap is detectable, light and thin, no electrical hazard. Disadvantages: expensive cable and equipment, brittle, needs skilled fusion splicing, cannot carry power, and unidirectional so two fibres are needed.

   Unguided media:
   - Radio waves. Advantages: omnidirectional, penetrate walls, no line of sight needed, cheap mobility, good for Wi-Fi and broadcast. Disadvantages: low bandwidth, interference from other users, insecure without encryption, regulated spectrum.
   - Microwave. Advantages: high bandwidth, no cabling needed across rivers and difficult terrain, cheaper than laying cable over long spans. Disadvantages: strict line of sight needed, towers required, rain fade, and it can be intercepted.
   - Infrared. Advantages: high bandwidth, no licence needed, secure because it cannot pass through walls. Disadvantages: very short range, blocked by any obstacle, useless in direct sunlight.
   - Satellite. Advantages: covers a huge area, reaches remote regions, ships and aircraft. Disadvantages: about 250 ms one way delay for geostationary orbit, very expensive, rain fade, limited bandwidth per transponder.
6. **Difference between Guided and Unguided media. Difference between STP and UTP. Why using benefit UTP instead of STP?** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 523 (ET: MIST)]*


   Answer:

   Guided vs unguided media:

   | Point | Guided media | Unguided media |
   |---|---|---|
   | Path | A physical cable directs the signal | The signal travels freely through air or space |
   | Also called | Wired or bounded media | Wireless or unbounded media |
   | Direction | Point to point along the cable | Broadcast in all directions, or a beam |
   | Bandwidth | Higher, especially fibre | Generally lower |
   | Interference | Less, and controllable | High, from other transmitters and weather |
   | Security | Better, physical access is needed to tap | Poorer, anyone in range can receive it |
   | Installation and cost | Cabling cost and labour, hard over difficult terrain | No cabling, cheaper to cover large or difficult areas |
   | Mobility | None | Full mobility |
   | Examples | Twisted pair, coaxial, optical fibre | Radio, microwave, infrared, satellite |

   STP vs UTP:

   | Point | STP | UTP |
   |---|---|---|
   | Shielding | A metallic foil or braid around the pairs, or around each pair | No shield, only the twist and the outer jacket |
   | EMI and crosstalk | Much better protection | Weaker protection, relies on the twisting |
   | Diameter and weight | Thicker, heavier, less flexible | Thin, light, flexible |
   | Grounding | Must be properly earthed, otherwise the shield acts as an antenna and makes things worse | No earthing needed |
   | Installation | Difficult, needs special connectors and care | Very easy, standard RJ-45 crimping |
   | Cost | Higher | Lowest |
   | Use | Factories, near heavy machinery, data centre high speed runs | General office and home LAN cabling |

   Why UTP is used instead of STP:
   - It is considerably cheaper, both the cable and the connectors, which matters when hundreds of runs are needed.
   - It is thinner, lighter and far more flexible, so it fits easily in conduits and cable trays and turns tight corners.
   - Installation and termination are simple, and no earthing is required, so labour cost and error rate are lower.
   - The twisting itself already cancels most interference, and in an ordinary office environment that is enough.
   - A wrongly earthed STP shield performs worse than plain UTP, so UTP avoids a common installation mistake.
   - It is the standard used by structured cabling systems worldwide, so equipment and spares are readily available.
7. **What is the main benefit of broadband transmission system compared to baseband? What is the attenuation of transmission media? Distinguish between twisted pair, co-axial cable and fiber optics in tabular form.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 530 (ET: MIST)]*


   Answer:

   Main benefit of broadband over baseband:
   - Broadband uses frequency division multiplexing, so many independent signals can travel over the same medium at the same time, each on its own carrier frequency. Baseband gives the whole medium to a single signal at a time.
   - The consequence is far better use of the available capacity, longer distance because the modulated high frequency signal attenuates less over coax and can be amplified, and the ability to carry different services such as voice, video and data on one cable, as cable TV does.

   Attenuation of a transmission medium:
   - Attenuation is the loss of signal strength as it travels through the medium, caused by the resistance of the conductor, absorption and scattering.
   - It is measured in decibels: attenuation (dB) = 10 log10(Pout / Pin), and per unit length it is quoted as dB/km or dB per 100 m.
   - Typical values: UTP loses roughly 20 dB per 100 m at 100 MHz, coaxial cable much less, and single mode fibre only 0.2 dB/km at 1550 nm.
   - It is the reason segment lengths are limited and repeaters or amplifiers are needed.

   Twisted pair vs coaxial vs fibre optic:

   | Point | Twisted pair | Coaxial cable | Optical fibre |
   |---|---|---|---|
   | Conductor | Two insulated copper wires twisted together | Central copper core, insulator, braided shield, jacket | Glass or plastic core with cladding, carries light |
   | Signal carried | Electrical | Electrical | Light pulses |
   | Bandwidth | Up to about 10 Gbps on Cat 6A over short runs | Up to about 1 Gbps typically | Terabits per second with WDM |
   | Maximum segment | 100 m | 185 m for thin, 500 m for thick coax | 2 km multimode, 40 to 100 km single mode |
   | Attenuation | High | Moderate | Very low, 0.2 dB/km at 1550 nm |
   | EMI immunity | Poor for UTP, better for STP | Good, because of the shield | Complete immunity, it is not electrical |
   | Security | Easy to tap | Easy to tap | Very hard to tap without detection |
   | Cost | Cheapest | Moderate | Highest for cable and for installation |
   | Installation | Very easy, RJ-45 crimping | Moderate | Difficult, needs fusion splicing |
   | Typical use | LAN cabling, telephone | Cable TV, old Ethernet, CCTV | Backbone, submarine, long haul, FTTH |
8. **Why we used straight-through and cross cable with example?** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 595 (ET: N/A)]*


   Answer: Straight through and crossover cables exist because a network interface transmits on one pair of wires and receives on another, so the two ends must be matched correctly.

   Straight through cable:
   - Both ends are wired to the same standard, T568B at both ends or T568A at both ends, so pin 1 goes to pin 1 and pin 2 to pin 2.
   - It is used between unlike devices, where one device transmits on pins 1 and 2 and the other receives on those same pins.
   - Examples: PC to switch, PC to hub, router to switch, switch to a wall outlet, access point to switch.

   Crossover cable:
   - One end is T568A and the other is T568B, which swaps the transmit pair, pins 1 and 2, with the receive pair, pins 3 and 6.
   - It is used between like devices, which would otherwise both transmit on the same pins and both listen on the same pins, so nothing would be received.
   - Examples: PC to PC directly, switch to switch, hub to hub, router to router, and PC directly to a router interface.

   - In modern equipment Auto-MDIX detects the mismatch and swaps the pairs electronically, so a straight through cable now works in nearly every situation, but the distinction is still asked in examinations and still matters with older gear.
9. **(খ) Fiber optic cable, Twisted pair cable এবং Co-axial cable এর সুবিধাগুলো বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 629 (ET: N/A)]*

   Answer:

   Advantages of fibre optic cable:
   - Very high bandwidth, up to terabits per second using WDM.
   - Very low attenuation, only about 0.2 dB/km at 1550 nm, so the signal can travel 80 to 100 km without a repeater.
   - Complete immunity to electromagnetic and radio frequency interference, and no crosstalk, because the signal is light and not electricity.
   - High security: tapping a fibre disturbs the light and is immediately detectable.
   - Light and thin, so it occupies far less duct space than copper of the same capacity.
   - It carries no electricity, so it is safe in explosive environments and needs no earthing.
   - It does not corrode and has a long service life.

   Advantages of twisted pair cable:
   - The cheapest medium and available everywhere.
   - Light, flexible and easily pulled through conduit and around corners.
   - Very easy to terminate by crimping an RJ-45 connector, so less skilled labour is required.
   - Power over Ethernet can supply electricity to a device over the same cable.
   - Cat 6A supports up to 10 Gbps over 100 metres, which is more than adequate for an ordinary office.
   - It is the worldwide standard for structured cabling, so equipment and spares are readily available.

   Advantages of coaxial cable:
   - The shield gives far better protection against electromagnetic interference and much less crosstalk than twisted pair.
   - Greater bandwidth and longer segments than twisted pair, 185 to 500 metres.
   - It supports broadband FDM, so voice, video and data can all travel on the same cable at once, as in cable television.
   - Strong and durable, so it works well outdoors and in CCTV installations.
   - Cheaper than fibre and easier to terminate.
10. **What happens when you use cables longer than the prescribed length in a network?** *[BOF Assistant Programmer 2022 compact it 732 (ET: MIST)]*


    Answer: If a cable longer than the prescribed limit is used, the following problems occur.

    - Attenuation: the signal becomes too weak by the time it reaches the far end, so the receiver cannot distinguish it reliably from noise. The result is a high bit error rate, CRC errors and constant retransmission.
    - Late collisions: in a CSMA/CD segment the round trip propagation time exceeds the time taken to send the minimum 64 byte frame, so a collision is detected after the frame has already been sent. The sending station never retransmits it, so the frame is silently lost and only the upper layer notices, which is very hard to diagnose.
    - Intermittent connectivity: the link comes up and goes down, or negotiates a lower speed, for example 100 Mbps instead of 1 Gbps.
    - Increased delay and jitter, which hurts voice and video badly.
    - Distortion and crosstalk increase with length, so the eye pattern closes and the error rate rises further.
    - Throughput collapses, because most of the capacity is consumed by retransmission.

    - The limits exist for exactly these reasons: 100 m for UTP Ethernet, 185 m for 10BASE2 and 500 m for 10BASE5. The correct fix is to insert a switch or a repeater within the limit, or to change to fibre.
11. **(ii) ব্যাখ্যা করুন: (a) 10Base5 (b) 10BaseF** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 789 (ET: N/A)]*

    Answer:

    (a) 10Base5
    - 10 means a data rate of 10 Mbps, Base means baseband transmission, and 5 means a maximum segment length of 500 metres.
    - It uses thick coaxial cable, known as Thicknet, about 10 mm in diameter and yellow in colour.
    - Computers are attached to the cable through a vampire tap and an AUI connector, and consecutive taps must be at least 2.5 metres apart.
    - A single segment supports up to 100 nodes, and under the 5-4-3 rule up to 5 segments and 4 repeaters give a total span of 2500 metres.
    - The topology is a bus and the access method is CSMA/CD. It is now completely obsolete.

    (b) 10BaseF
    - 10 means 10 Mbps, Base means baseband, and F means fibre optic cable.
    - Two fibres are used, one for transmitting and one for receiving, so it can work in full duplex.
    - The maximum segment length is about 2000 metres, far more than copper allows, because attenuation in fibre is very low.
    - It is immune to electromagnetic interference, so it was used as a backbone link between buildings and inside factories.
    - It has three variants: 10BASE-FL for links, 10BASE-FB for backbones and 10BASE-FP for a passive star.
12. **Explain 10baseT.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 839 (ET: N/A)]*


    Answer: 10BASE-T is the IEEE 802.3i Ethernet standard that runs at 10 Mbps over twisted pair copper cable.

    - 10 means 10 Mbps, BASE means baseband signalling, so the whole cable carries one signal, and T means twisted pair.
    - It uses Category 3 or better UTP with RJ-45 connectors, and only two of the four pairs, pins 1 and 2 to transmit and pins 3 and 6 to receive.
    - Maximum segment length is 100 metres between the station and the hub or switch.
    - Physically it is a star topology centred on a hub or switch, although with a hub it behaves logically as a bus using CSMA/CD.
    - Encoding is Manchester, which embeds the clock in the data, so the signalling rate on the wire is 20 Mbaud.
    - Its importance is historical: by replacing coaxial bus wiring with cheap structured star cabling, it made Ethernet easy to install and troubleshoot, and it led directly to 100BASE-TX and 1000BASE-T which use the same cable and connector.
13. **Which media transfer data with higher bandwidth? Advantages of this media.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 843 (ET: N/A)]*


    Answer: Optical fibre transfers data with the highest bandwidth.

    - A single fibre carries terabits per second using Dense Wavelength Division Multiplexing, far beyond any copper medium or wireless link.

    Advantages of optical fibre:
    - Enormous bandwidth and very high data rate, and the capacity of an installed cable can be raised later just by upgrading the terminal equipment.
    - Very low attenuation, about 0.2 dB/km at 1550 nm, so repeaters can be 80 to 100 km apart against 100 m for UTP.
    - Complete immunity to electromagnetic and radio frequency interference and to crosstalk, since the signal is light and not electricity.
    - High security: tapping the fibre disturbs the light and is easily detected, so it suits banking and defence links.
    - Light and thin compared with copper of equivalent capacity, so it saves duct space.
    - No electrical conductivity, therefore safe in explosive or high voltage environments, immune to lightning and needing no earthing.
    - No corrosion and a long service life, which lowers maintenance cost.
    - Limitations to mention for balance: high installation cost, brittleness, and the need for skilled fusion splicing.
14. **(a) What are the problems that transmission lines suffer from? Briefly describe any one of them.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1026-1027 (ET: N/A)]*


    Answer: Transmission lines suffer from the following problems.

    - Attenuation: the signal loses power with distance.
    - Distortion, including delay distortion, where different frequency components travel at different speeds.
    - Noise: thermal, intermodulation, crosstalk and impulse noise.
    - Interference from external electromagnetic sources.
    - Echo and reflection from impedance mismatch at the ends.
    - Jitter, that is variation in the arrival timing of pulses.
    - Fading on wireless lines, and skin effect in copper at high frequency.

    Description of one of them, attenuation:
    - Attenuation is the loss of signal strength as the signal travels along the line, caused by the resistance of the conductor converting part of the electrical energy into heat, and by absorption and scattering in the medium.
    - It is measured in decibels: attenuation (dB) = 10 log10(Pin / Pout), and it is expressed per unit length as dB/km.
    - It is frequency dependent, higher frequencies attenuate faster, so a complex signal is not merely weakened but also changed in shape, which is why equalisers are used together with amplifiers.
    - If it is not corrected, the received signal falls towards the noise level, the signal to noise ratio drops, and the bit error rate rises until communication fails.
    - The remedies are amplifiers for analog systems and regenerative repeaters for digital systems, placed at intervals calculated from the power budget, together with a lower loss medium such as fibre where the distance is long.

## Error Detection & Data Communication (CRC, Throughput) (14)

1. (a) CMY color model এর উপাদানগুলো লিখুন (CMY color model এর কাজ কী?)
   (b) CRC এর কাজ কী? (IIB CRC-16 এর ক্ষেত্র এবং প্রশ্নগুলো আলোচনা করুন)
   (c) Data communication এর ক্ষেত্রে bandwidth এবং throughput এর মধ্যে পার্থক্য লিখুন। *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*


   Answer:

   (a) CMY color model
   - Components: Cyan, Magenta and Yellow. In the practical printing version, CMYK, a fourth component Key, that is black, is added.
   - It is a subtractive colour model: it starts from white paper and each ink subtracts, that is absorbs, one primary colour of light. Cyan absorbs red, magenta absorbs green and yellow absorbs blue.
   - Relation to RGB: C = 1 − R, M = 1 − G, Y = 1 − B, when the values are normalised to the range 0 to 1.
   - Work of the model: it is used for hard copy output, that is printers, plotters and all colour printing, because ink on paper works by subtracting reflected light, unlike a monitor which emits light and therefore uses the additive RGB model.
   - K is added because mixing full C, M and Y gives a muddy dark brown rather than true black, and black ink alone is cheaper and sharper for text.

   (b) Work of CRC
   - CRC, Cyclic Redundancy Check, is an error detection method that treats the data as a binary polynomial and divides it by a fixed generator polynomial. The remainder becomes the check bits appended to the data.
   - Sender: append n zeros to the data, where n is the degree of the generator, divide by the generator using modulo-2 division, and put the n bit remainder in place of the zeros.
   - Receiver: divide the whole received frame by the same generator. A remainder of zero means the frame is accepted, any non-zero remainder means it is discarded.
   - Detection power: it catches all single bit errors, all double bit errors for a suitable generator, all odd numbers of bit errors if the generator has the factor x + 1, and all burst errors shorter than or equal to the degree of the generator.
   - CRC-16 uses the generator x¹⁶ + x¹⁵ + x² + 1, giving a 16 bit remainder that detects every burst error up to 16 bits and 99.997 percent of longer bursts. It is used in HDLC, USB and Modbus, while CRC-32 is used in Ethernet.
   - It only detects errors, it does not correct them; correction is left to retransmission.

   (c) Bandwidth vs throughput

   | Point | Bandwidth | Throughput |
   |---|---|---|
   | Meaning | The maximum theoretical capacity of a link | The actual amount of data delivered successfully per unit time |
   | Nature | A fixed property of the medium and the technology | A measured value that varies moment to moment |
   | Unit | bps, Mbps, Gbps, or Hz for an analog channel | bps, Mbps, Gbps |
   | Affected by | Medium, encoding, channel width | Congestion, errors, retransmission, protocol overhead, latency, device speed |
   | Relation | Always the upper limit | Always less than or equal to the bandwidth |
   | Analogy | The width of a road | The number of vehicles that actually pass per hour |
   | Example | A 100 Mbps link | The same link may deliver only 60 Mbps of useful data |
2. **Data communication mathematical problems.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1368 (ET: BUET)]*


   Answer: The standard formulas used for data communication numerical problems, with the method to apply them.

   Delay and latency:
   - Transmission time Tt = message size / bandwidth.
   - Propagation time Tp = distance / propagation speed, where the speed is 2 × 10⁸ m/s in cable and 3 × 10⁸ m/s in air.
   - Total latency = propagation + transmission + queuing + processing delay.

   Capacity:
   - Nyquist, for a noiseless channel: C = 2 B log2 L bps.
   - Shannon, for a noisy channel: C = B log2(1 + SNR) bps.
   - SNR in dB = 10 log10(Psignal / Pnoise).

   Efficiency:
   - Bandwidth delay product = bandwidth × round trip time, which is the number of bits that can be in flight.
   - a = Tp / Tt, and link utilisation = W / (1 + 2a) for a window of W frames; for stop and wait W = 1.
   - Throughput = useful data delivered per second, always less than the bandwidth after overhead is removed.

   Method to follow in the examination:
   - Write the formula first, then convert all units to bits and seconds, then substitute the numbers, then give the final answer with its unit on a separate line.
   - Watch the units carefully: 1 byte is 8 bits, 1 kbps is 10³ bps in communication but 1 KB is 1024 bytes in storage.

   Worked example: a 1 Mbps link of 5000 km with a 1000 bit frame.
   - Tt = 1000 / 10⁶ = 1 ms.
   - Tp = 5 × 10⁶ / (2 × 10⁸) = 25 ms.
   - a = 25, so stop and wait efficiency = 1 / (1 + 50) = 1.96 percent, and effective throughput = 19.6 kbps out of 1 Mbps.
3. **Question on data communication transmission and signal related math.** *[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1441 (ET: BUET)]*


   Answer: Signal and transmission numerical problems are solved with the following formulas.

   Signal and bit rate:
   - Bit rate = baud rate × log2 L, where L is the number of signal levels.
   - Baud rate = bit rate / log2 L, that is the number of signal elements per second.

   Bandwidth requirement:
   - Nyquist noiseless capacity: C = 2 B log2 L, so the required bandwidth B = C / (2 log2 L).
   - Shannon noisy capacity: C = B log2(1 + SNR).
   - The practical capacity is the smaller of the two, and the number of levels needed follows from equating them.

   Signal power:
   - SNR = Psignal / Pnoise, and SNR in dB = 10 log10(SNR).
   - Power in dBm = 10 log10(P in mW).
   - Attenuation in dB = 10 log10(Pin / Pout); a gain is a positive dB and a loss is negative.

   Time components:
   - Transmission time = size / bandwidth, propagation time = distance / speed, and total latency is the sum of transmission, propagation, queuing and processing delays.

   Worked example: a channel of 4 kHz bandwidth with SNR of 1000.
   - Shannon: C = 4000 × log2(1001) = 4000 × 9.967 = 39,868 bps, about 39.9 kbps.
   - Nyquist, to reach this rate: 39,868 = 2 × 4000 × log2 L, so log2 L = 4.98 and L = 31.6, so 32 levels are needed.
   - Final answer: maximum capacity about 39.9 kbps, requiring 32 signal levels.
4. **10Mbps bandwidth, average packet length 1500 bytes what is maximum packet arrival rate support without causing congestion.** *[Bangladesh Satellite Company Limited Assistant Engineer (CSE) 23.08.2025 compact it 1430 (ET: BUET)]*


   Answer:

   Given:
   - Bandwidth = 10 Mbps = 10 × 10⁶ bits per second.
   - Average packet length = 1500 bytes.

   Step 1, convert the packet length to bits:
   - 1500 bytes × 8 = 12,000 bits per packet.

   Step 2, maximum packet arrival rate:
   - Rate = bandwidth / packet size in bits = 10 × 10⁶ / 12,000 = 833.33 packets per second.

   Final answer: the link can support about 833 packets per second before congestion occurs.

   - Note: at exactly this rate the link is 100 percent utilised, so the queue grows without limit. In practice the design target is about 70 to 80 percent, that is roughly 580 to 660 packets per second, to keep the queuing delay acceptable.
5. **What is Total Latency for a 3-kbyte message (an e-mail) if the bandwidth of the network is 1Gbps? Assume that the distance between the sender and the receiver is 300\text{ km} and that light travels at 2 \times 10^8\text{ m/s}. Round Trip Time 50ms Queuing Time 5ms?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1320 (ET: DU)]*


   Answer:

   Given:
   - Message size = 3 kbyte = 3 × 1024 × 8 = 24,576 bits.
   - Bandwidth = 1 Gbps = 10⁹ bps.
   - Distance = 300 km = 3 × 10⁵ m, speed of light in the medium = 2 × 10⁸ m/s.
   - Round trip time = 50 ms, queuing time = 5 ms.

   Step 1, transmission time:
   - Tt = 24,576 / 10⁹ = 24.576 × 10⁻⁶ s = 0.0246 ms.

   Step 2, propagation time:
   - Tp = 3 × 10⁵ / 2 × 10⁸ = 1.5 × 10⁻³ s = 1.5 ms.

   Step 3, total latency:
   - Latency = RTT + queuing time + transmission time = 50 + 5 + 0.0246 = 55.02 ms.

   Final answer: total latency is about 55.02 ms.

   - Observation worth writing: the transmission time is only 0.0246 ms out of 55 ms, so the delay is dominated by the round trip and queuing time, not by the bandwidth. For a small message, increasing the bandwidth further would hardly help at all.
   - If the RTT is not to be counted separately and only the one way path is asked, the latency would be Tp + Tt + queuing = 1.5 + 0.0246 + 5 = 6.52 ms.
6. **Differentiate the following terms in tabular form:** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 300 (ET: BIBM)]*
   * **A. CSMA/CD and CSMA/CA.**
   * **B. Optical Communication and Satellite Communication.**
   * **C. Parity bit check, CRC and Checksum.**


   Answer:

   A. CSMA/CD vs CSMA/CA

   | Point | CSMA/CD | CSMA/CA |
   |---|---|---|
   | Full form | Carrier Sense Multiple Access with Collision Detection | Carrier Sense Multiple Access with Collision Avoidance |
   | Approach | Detects a collision after it happens and recovers | Tries to prevent a collision from happening |
   | Medium | Wired, IEEE 802.3 Ethernet | Wireless, IEEE 802.11 Wi-Fi |
   | Why | A wired node can transmit and listen at the same time | A radio node cannot hear a collision while transmitting, since its own signal is far stronger |
   | On collision | Sends a jam signal, then binary exponential backoff | Waits a random backoff before transmitting at all, then uses RTS/CTS and ACK |
   | Efficiency | Higher, the medium is used until a collision occurs | Lower, time is spent on backoff and control frames |
   | Acknowledgement | Not used at the MAC layer | Every unicast frame is acknowledged |

   B. Optical vs satellite communication

   | Point | Optical communication | Satellite communication |
   |---|---|---|
   | Medium | Optical fibre cable | Free space radio, microwave |
   | Bandwidth | Terabits per second with WDM | A few Gbps per satellite |
   | Latency | Very low, a few ms over regional distances | About 250 ms one way for geostationary orbit |
   | Coverage | Only where cable is laid, point to point | Very wide, whole continents, ships, aircraft, remote areas |
   | Weather | Unaffected | Rain fade, atmospheric and solar interference |
   | Cost | High to lay, very low per bit afterwards | High launch cost, expensive rented bandwidth |
   | Security | High, a tap is detectable | Lower, the beam covers a huge area |
   | Best use | Backbone, submarine, long haul bulk traffic | Broadcast, remote regions, disaster recovery, mobile platforms |

   C. Parity bit check vs CRC vs Checksum

   | Point | Parity bit | Checksum | CRC |
   |---|---|---|---|
   | Redundant bits | 1 bit | 8, 16 or 32 bits | 8, 16 or 32 bits |
   | Method | Count the 1s and set the bit for even or odd parity | Add all the words, take the one's complement of the sum | Modulo-2 polynomial division, keep the remainder |
   | Detects | Only an odd number of bit errors | Most errors, but not a reordering or a compensating pair of changes | All single and double errors, all odd errors, all bursts up to the generator degree |
   | Strength | Weakest | Moderate | Strongest |
   | Cost | Almost nothing | Cheap, simple addition | Higher, but implemented in hardware so it is fast |
   | Layer used | Character transmission, memory | Transport layer, TCP, UDP, IP header | Data link layer, Ethernet, HDLC, USB |
7. **Two math from data communication.** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 405 (ET: N/A)]*


   Answer: Two typical data communication problems and their solutions.

   Problem 1, channel capacity:
   - A channel has a bandwidth of 4 kHz and a signal to noise ratio of 30 dB. Find the maximum data rate.
   - SNR in linear form = 10^(30/10) = 1000.
   - Shannon: C = B log2(1 + SNR) = 4000 × log2(1001) = 4000 × 9.967 = 39,868 bps.
   - Final answer: about 39.9 kbps.

   Problem 2, transmission and propagation delay:
   - A 1000 bit frame is sent over a 1 Mbps link of length 2000 km, with a propagation speed of 2 × 10⁸ m/s. Find the total delay and the stop-and-wait efficiency.
   - Transmission time Tt = 1000 / 10⁶ = 1 ms.
   - Propagation time Tp = 2 × 10⁶ / 2 × 10⁸ = 10 ms.
   - One way delay = Tt + Tp = 11 ms; the acknowledgement adds another 10 ms, so a full cycle is 21 ms.
   - a = Tp / Tt = 10, so efficiency = 1 / (1 + 2a) = 1 / 21 = 4.76 percent.
   - Effective throughput = 0.0476 × 1 Mbps = 47.6 kbps.
   - Final answer: total delay 11 ms one way, efficiency 4.76 percent, throughput 47.6 kbps.
8. **(গ) Data communication-এর সাপেক্ষে bandwidth এবং troughput এর সংজ্ঞা লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer:

   Bandwidth: the maximum theoretical capacity of a link, that is the greatest number of bits that can be sent in one second. It is measured in bps, Mbps or Gbps for a digital channel and in Hertz for an analog channel. It is a fixed property of the medium and the technology.

   Throughput: the number of bits that actually reach the destination successfully in one second, as measured. It is always less than the bandwidth.

   | Point | Bandwidth | Throughput |
   |---|---|---|
   | Meaning | The maximum theoretical capacity of a link | The data actually delivered successfully per unit time |
   | Nature | A fixed property of the medium and the technology | A measured value that changes from moment to moment |
   | Unit | bps, Mbps, Gbps, or Hz for an analog channel | bps, Mbps, Gbps |
   | Affected by | Medium, encoding, channel width | Congestion, errors, retransmission, protocol overhead, latency |
   | Relation | Always the upper limit | Always less than or equal to the bandwidth |
   | Analogy | The width of a road | The number of vehicles that actually pass per hour |

   - Example: on a 100 Mbps LAN, after congestion, errors, retransmission and protocol overhead, perhaps 60 Mbps of useful data is actually delivered. Here the bandwidth is 100 Mbps and the throughput is 60 Mbps.
9. **CRC is a redundancy error technique used to determine the error. Suppose the original data is 11100 and divisor is 1001.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 493 (ET: N/A)]*


   Answer:

   Given: data = 11100, divisor or generator = 1001.

   Step 1, number of check bits:
   - The divisor has 4 bits, so its degree is 3, and 3 zeros are appended to the data.
   - Dividend = 11100 000 = 11100000.

   Step 2, modulo-2 division of 11100000 by 1001:

   ```
        11100000 ÷ 1001
        1001
        ----
        1010 000
        1001
        ----
          11 000
          1001
          ----
           101 0
           0000
           ----
            1010
            1001
            ----
             011  -> bring down, remainder = 111
   ```

   - Working it through step by step, the remainder is 111.

   Step 3, transmitted codeword:
   - Codeword = data + CRC = 11100 + 111 = 11100111.

   Final answer: the CRC is 111 and the transmitted frame is 11100111.

   Step 4, verification at the receiver:
   - Dividing 11100111 by 1001 gives a remainder of 000, so the frame is accepted. Any non-zero remainder would mean an error and the frame would be discarded.
10. **A telephone line normally has a bandwidth of 3000 Hz (300 to 3300 Hz) assigned for data communication. The SNR is usually 3162. What will be the capacity for this channel?** *[Combined Bank Assistant Programmer 09.06.2023 compact it 497 (ET: N/A)]*


    Answer:

    Given:
    - Bandwidth B = 3000 Hz, from 300 Hz to 3300 Hz.
    - SNR = 3162.

    Step 1, Shannon capacity formula:
    - C = B log2(1 + SNR)

    Step 2, substitute:
    - C = 3000 × log2(1 + 3162) = 3000 × log2(3163)

    Step 3, evaluate the logarithm:
    - log2(3163) = ln(3163) / ln(2) = 8.0593 / 0.6931 = 11.627

    Step 4, capacity:
    - C = 3000 × 11.627 = 34,881 bps

    Final answer: the channel capacity is about 34,881 bps, that is roughly 34.9 kbps.

    - Note: SNR = 3162 corresponds to 10 log10(3162) = 35 dB, and a useful shortcut is C ≈ B × SNR(dB) / 3, which gives 3000 × 35 / 3 = 35,000 bps, very close to the exact value. This is exactly why old telephone line modems topped out at about 33.6 kbps.
11. **Which technique is used for binary division check in network?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*


    Answer: The technique used for binary division based checking in a network is CRC, the Cyclic Redundancy Check.

    - The data is treated as a binary polynomial and divided by a fixed generator polynomial using modulo-2 division; the remainder is appended as the check bits.
    - The receiver divides the received frame by the same generator, and a zero remainder means the frame is error free.
    - It is used in Ethernet with CRC-32, and in HDLC and USB with CRC-16.
12. **Explain parity method for error detection. Write down the bit strings of “Delta” using ASCII.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 (ET: BIBM)]*


    Answer:

    Parity method for error detection:
    - One extra bit, the parity bit, is added to each group of data bits so that the total number of 1s becomes even or odd according to the agreed scheme.
    - Even parity: the parity bit is set so that the count of 1s including the parity bit is even. Odd parity: the count is made odd.
    - Sender: count the 1s in the data and set the parity bit accordingly. Receiver: count the 1s in the received unit including the parity bit; if the parity is wrong, an error has occurred and the unit is discarded.
    - Example, data 1000100 with even parity: it has two 1s, already even, so the parity bit is 0 and the transmitted unit is 10001000.
    - Strengths: extremely simple and cheap, needs only one bit.
    - Weakness: it detects only an odd number of bit errors. If two bits flip, the parity is unchanged and the error passes undetected. It cannot correct anything.
    - Two dimensional parity, that is a parity bit per row and per column, improves this and can even correct a single bit error, but CRC is used instead wherever the error rate matters.

    Bit strings of "Delta" in 7 bit ASCII:

    | Character | Decimal | 7 bit ASCII | With even parity as the 8th bit |
    |---|---|---|---|
    | D | 68 | 1000100 | 10001000 |
    | e | 101 | 1100101 | 11001010 |
    | l | 108 | 1101100 | 11011001 |
    | t | 116 | 1110100 | 11101001 |
    | a | 97 | 1100001 | 11000011 |

    - Full bit string of "Delta" in 7 bit ASCII: 1000100 1100101 1101100 1110100 1100001, that is 35 bits in all.
13. **An end system sends 50 packets per second using the User Datagram Protocol (UDP) over a full duplex 100 Mbps ethernet LAN connection. Each packet consists 1500B of ethernet frame payload data. What is the throughput, when measured at the UDP layer?** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 718 (ET: N/A)]*


    Answer:

    Given:
    - 50 packets per second, over a full duplex 100 Mbps Ethernet link.
    - Each packet contains 1500 bytes of Ethernet frame payload data.

    Step 1, find how much of the 1500 bytes is actual UDP application data:
    - The Ethernet payload carries the IP packet.
    - IP header = 20 bytes, UDP header = 8 bytes, total overhead = 28 bytes.
    - UDP application data = 1500 − 28 = 1472 bytes.

    Step 2, convert to bits:
    - 1472 × 8 = 11,776 bits per packet.

    Step 3, throughput at the UDP layer:
    - Throughput = 50 × 11,776 = 588,800 bps.

    Final answer: the throughput measured at the UDP layer is 588,800 bps, that is about 588.8 kbps or 0.589 Mbps.

    - Note: measured at the Ethernet payload level it would be 50 × 1500 × 8 = 600 kbps, and the 100 Mbps link is therefore only about 0.6 percent utilised.
14. **The message 11001001 is to be transmitted using the CRC polynomial x^3+1 to protect it from the errors. Now find out the message that should be transmitted.** *[BAUST Assistant Programmer 2021 compact it 917-918 (ET: N/A)]*


    Answer:

    Given:
    - Message M = 11001001.
    - Generator polynomial G(x) = x³ + 1, which in binary is 1001 since the x² term is absent.

    Step 1, number of check bits:
    - The degree of the generator is 3, so 3 zeros are appended.
    - Dividend = 11001001 000 = 11001001000.

    Step 2, modulo-2 division of 11001001000 by 1001:

    ```
    11001001000 ÷ 1001
    1001
    ----
    1010 01000
    1001
    ----
      11 01000
      1001
      ----
       1 11000
         1001
         ----
          1110 0
          1001
          ----
           1110
           1001
           ----
            011   remainder = 011
    ```

    - The remainder, that is the CRC, is 011.

    Step 3, transmitted message:
    - Transmitted frame = original message with the zeros replaced by the remainder = 11001001 011 = 11001001011.

    Final answer: the message to be transmitted is 11001001011.

    Step 4, check:
    - Dividing 11001001011 by 1001 gives a remainder of 000, which confirms the codeword is correct.

## Data Rate & Channel Capacity (Nyquist, Shannon) (14)

1. **Nyquist math: See in Data Communication & Networking Chapter** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 499 (ET: N/A)]*


   Answer: Nyquist's theorem gives the maximum data rate of a noiseless channel.

   Formulas:
   - Maximum bit rate: C = 2 B log2 L bps, where B is the bandwidth in Hz and L is the number of discrete signal levels.
   - Number of levels needed: L = 2^(C / 2B).
   - Nyquist sampling theorem: fs ≥ 2 fmax, that is the sampling rate must be at least twice the highest frequency, otherwise aliasing occurs.
   - Maximum signalling rate, that is baud rate, = 2 B symbols per second.
   - Bit rate = baud rate × log2 L.

   Worked example: a noiseless 3 kHz channel using 4 signal levels.
   - C = 2 × 3000 × log2 4 = 2 × 3000 × 2 = 12,000 bps.
   - If 16 levels were used instead, C = 2 × 3000 × 4 = 24,000 bps.

   Points the examiner looks for:
   - Nyquist applies only to a noiseless channel, so it gives an upper bound that cannot be reached in practice.
   - Raising L raises the bit rate without extra bandwidth, but the levels come closer together, so noise causes more errors. Shannon's law sets the real limit.
   - The practical capacity is the smaller of the Nyquist and the Shannon values.
2. **Suppose that a digitized TV picture is to be transmitted from a source that uses a matrix of 480 × 500 picture elements (pixels), where each pixel can take on one of 32 intensity values. Assume that 30 pictures are sent per second. (This digital source is roughly equivalent to broadcast TV standards that have been adopted). Find the source rate R (bps).** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 (ET: BIBM)]*


   Answer:

   Given:
   - Picture matrix = 480 × 500 pixels.
   - Each pixel can take 32 intensity values.
   - 30 pictures are sent per second.

   Step 1, bits needed per pixel:
   - 32 levels need log2 32 = 5 bits per pixel.

   Step 2, pixels per picture:
   - 480 × 500 = 240,000 pixels.

   Step 3, bits per picture:
   - 240,000 × 5 = 1,200,000 bits per picture.

   Step 4, source rate:
   - R = 1,200,000 × 30 = 36,000,000 bps.

   Final answer: the source rate R is 36 Mbps, that is 36 × 10⁶ bits per second.

   - Note: this is the raw uncompressed rate. Broadcast television uses compression such as MPEG-2 or H.264 to bring it down to a few Mbps, which is why compression is essential for video transmission.
3. **One of the drawbacks of a small packet size is that a large function of link bandwidth is consumed by overhead bytes. To this end, supposed that the packet consists of P bytes and 5 bytes of header. Consider sending a digitally encoded voice source directly. Suppose the source is encoded a constant rate of 128 kbps. Assume each packet is entirely filled before the source sends the packet into the network. The time required to fill a packet is the packetization delay. Determine the packetization delay for length L-1500 bytes (roughly corresponding to maximum-sized Ethernet packet).** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 (ET: BIBM)]*


   Answer:

   Given:
   - Voice source encoded at a constant rate of 128 kbps = 128,000 bps.
   - Packet length L = 1500 bytes of data, plus a 5 byte header.
   - The packet must be completely filled before it is sent.

   Step 1, convert the packet payload to bits:
   - 1500 bytes × 8 = 12,000 bits.

   Step 2, packetization delay, that is the time to fill the packet:
   - Delay = payload bits / source rate = 12,000 / 128,000 = 0.09375 s.

   Final answer: the packetization delay is 0.09375 s, that is 93.75 ms.

   - Comment the examiner wants: 93.75 ms of delay is far too high for interactive voice, where the total one way budget is about 150 ms. This is why VoIP uses very small packets, typically 20 ms of speech, even though the 5 byte header then becomes a much larger fraction of the packet.
   - Trade-off: a large packet gives low header overhead but high packetization delay; a small packet gives low delay but wastes bandwidth on headers. If instead the 1500 bytes includes the 5 byte header, the payload is 1495 bytes and the delay is 93.44 ms, which changes nothing in the conclusion.
4. **(ক) Bandwidth এবং Through put এর মধ্যে পার্থক্য কী?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 628 (ET: N/A)]*

   Answer:

   Bandwidth: the maximum theoretical capacity of a link, that is the greatest number of bits that can be sent in one second. It is measured in bps or Mbps for a digital channel and in Hertz for an analog one.

   Throughput: the number of bits that actually reach the destination successfully in one second. It is always less than the bandwidth.

   | Point | Bandwidth | Throughput |
   |---|---|---|
   | Meaning | The maximum possible capacity | The data rate actually achieved |
   | Nature | A fixed property of the medium, unchanging | Varies with conditions |
   | Unit | bps, Mbps, Gbps, or Hz | bps, Mbps, Gbps |
   | Affected by | Medium, encoding, channel width | Congestion, errors, retransmission, protocol overhead, latency |
   | Relation | Always the upper limit | Always equal to or less than the bandwidth |
   | Analogy | The width of a road | The number of vehicles that actually pass per hour |

   - Example: on a 100 Mbps link, after overhead and congestion, perhaps 60 Mbps of useful data is delivered.
5. **The power of signal is 10\text{mW} and the power of the noise is 1\mu\text{W}; What are the values of \text{SNR} and \text{SNR}_{\text{dB}}?** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 651 (ET: BUET)]*


   Answer:

   Given:
   - Signal power = 10 mW = 10 × 10⁻³ W.
   - Noise power = 1 µW = 1 × 10⁻⁶ W.

   Step 1, SNR:
   - SNR = Psignal / Pnoise = (10 × 10⁻³) / (1 × 10⁻⁶) = 10,000

   Step 2, SNR in decibels:
   - SNR(dB) = 10 log10(SNR) = 10 log10(10,000) = 10 × 4 = 40 dB

   Final answer: SNR = 10,000 and SNR in dB = 40 dB.

   - Note: SNR is a ratio, so it has no unit. A higher SNR means a cleaner channel and, by Shannon's law, a higher achievable capacity.
6. **We need to send 265\text{ kbps} over a noiseless channel with a bandwidth of 20\text{kHz}. How many signal levels do we need?** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 652 (ET: BUET)]*


   Answer:

   Given:
   - Required bit rate C = 265 kbps = 265,000 bps.
   - Bandwidth B = 20 kHz = 20,000 Hz, noiseless channel.

   Step 1, Nyquist formula for a noiseless channel:
   - C = 2 B log2 L

   Step 2, substitute:
   - 265,000 = 2 × 20,000 × log2 L
   - 265,000 = 40,000 × log2 L
   - log2 L = 265,000 / 40,000 = 6.625

   Step 3, find L:
   - L = 2^6.625 = 98.7

   Final answer: the calculation gives L = 98.7 levels.

   - Since the number of signal levels must be a power of 2, 98.7 is not usable. Rounding down to 64 levels gives C = 40,000 × 6 = 240 kbps, which is below the requirement. Rounding up to 128 levels gives C = 40,000 × 7 = 280 kbps, which meets it.
   - Therefore 128 signal levels are needed. The practical caution is that more levels means the levels are closer together, so the system becomes far more sensitive to noise, and Shannon's law must also be checked.
7. **A telephone line normally has a bandwidth of 3000\text{ Hz} (300\text{ to } 3300\text{ Hz}) assigned foe data communications. The signal-to-noise ratio is usually 3162. Calculate the capacity for this channel?** *[RPGCL Assistant Manager (ICT) 2022 compact it 656 (ET: BUET)]*


   Answer:

   Given:
   - Bandwidth B = 3000 Hz, from 300 Hz to 3300 Hz.
   - SNR = 3162.

   Step 1, Shannon capacity formula:
   - C = B log2(1 + SNR)

   Step 2, substitute:
   - C = 3000 × log2(1 + 3162) = 3000 × log2(3163)

   Step 3, evaluate:
   - log2(3163) = 11.627
   - C = 3000 × 11.627 = 34,881 bps

   Final answer: the channel capacity is about 34,881 bps, that is roughly 34.9 kbps.

   - Cross check: SNR = 3162 is 35 dB, and the shortcut C ≈ B × SNR(dB)/3 gives 3000 × 35/3 = 35,000 bps, which agrees. This is why telephone line modems could not exceed about 33.6 kbps.
8. **Consider that a signal is transmitted over a channel of bandwidth 200kHz and the total path loss in the channel is found to be 60dB. The noise power per hertz at the receiver is- 100 dBm. Determine the required transmit power to achieve data rate of 40kb/s.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*


   Answer:

   Given:
   - Channel bandwidth B = 200 kHz = 2 × 10⁵ Hz.
   - Total path loss = 60 dB.
   - Noise power spectral density N0 = −100 dBm/Hz.
   - Required data rate C = 40 kbps.

   Step 1, find the required SNR from Shannon's law:
   - C = B log2(1 + SNR)
   - 40,000 = 200,000 × log2(1 + SNR)
   - log2(1 + SNR) = 0.2
   - 1 + SNR = 2^0.2 = 1.1487, so SNR = 0.1487
   - SNR in dB = 10 log10(0.1487) = −8.28 dB

   Step 2, find the total noise power at the receiver:
   - N = N0 × B, so in dB: N = −100 + 10 log10(200,000) = −100 + 53.01 = −46.99 dBm

   Step 3, find the required received signal power:
   - S(dBm) = N(dBm) + SNR(dB) = −46.99 + (−8.28) = −55.27 dBm

   Step 4, add the path loss to get the transmit power:
   - Pt = S + path loss = −55.27 + 60 = 4.73 dBm
   - In linear form, Pt = 10^(4.73/10) = 2.97 mW

   Final answer: the required transmit power is about 4.73 dBm, that is roughly 2.97 mW.

   - Note that the required SNR is less than 1, which is possible because the bandwidth of 200 kHz is five times the data rate, so the system is bandwidth rich and power poor. Spread spectrum systems work in exactly this region.
9. **(গ) নিম্নে উল্লিখিত ডাটা ট্রান্সফার রেট গুলিকে bit/sec এর পরিণত করুন 50Mb/S; 10KB/S; 20MB/S; 10Kb/S.** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 704 (ET: N/A)]*

   Answer: Converting each rate into bits per second:

   | Given | Working | Answer |
   |---|---|---|
   | 50 Mb/s | 50 × 10⁶ | 50,000,000 bps |
   | 10 KB/s | 10 × 10³ × 8 | 80,000 bps |
   | 20 MB/s | 20 × 10⁶ × 8 | 160,000,000 bps |
   | 10 Kb/s | 10 × 10³ | 10,000 bps |

   - Rule to remember: a small b means bit and a capital B means Byte, and 1 Byte = 8 bits.
   - In data communication k, M and G mean 10³, 10⁶ and 10⁹ respectively, not the 1024 based values used in storage.
10. **What is the channel capacity for a teleprinter channel with a 300 Hz bandwidth and a signal-to-noise ratio of 3 dB?** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 719 (ET: N/A)]*


    Answer:

    Given:
    - Bandwidth B = 300 Hz.
    - SNR = 3 dB.

    Step 1, convert the SNR from dB to a linear ratio:
    - SNR(dB) = 10 log10(SNR)
    - 3 = 10 log10(SNR), so log10(SNR) = 0.3
    - SNR = 10^0.3 = 1.995, which is approximately 2

    Step 2, apply Shannon's law:
    - C = B log2(1 + SNR) = 300 × log2(1 + 2) = 300 × log2 3

    Step 3, evaluate:
    - log2 3 = 1.585
    - C = 300 × 1.585 = 475.5 bps

    Final answer: the channel capacity is about 475 bps.

    - Using the exact SNR of 1.995 instead of 2 gives 474.8 bps, so 475 bps is the correct answer to state.
    - Useful rule to remember: an SNR of 3 dB means the signal power is twice the noise power.
11. **Using the Nyquist theorem, we can sample 12 million times/sec. Four–level signals provide 2 bits per sample, for a total data rate of 24 Mbps.** *[NESCO Assistant Manager (ICT) 2021 compact it 908 (ET: BUET)]*


    Answer: The statement is correct, and it is verified as follows.

    Given:
    - Sampling rate = 12 million samples per second.
    - Four level signalling, so L = 4.

    Step 1, bits per sample:
    - log2 L = log2 4 = 2 bits per sample.

    Step 2, data rate:
    - Data rate = samples per second × bits per sample = 12 × 10⁶ × 2 = 24 × 10⁶ bps = 24 Mbps.

    Final answer: the total data rate is 24 Mbps, which confirms the statement.

    Relation to the Nyquist formula:
    - Nyquist's theorem says the maximum signalling rate is 2 B symbols per second, so 12 million samples per second corresponds to a channel bandwidth of B = 6 MHz.
    - Applying C = 2 B log2 L directly: C = 2 × 6 × 10⁶ × log2 4 = 12 × 10⁶ × 2 = 24 Mbps, the same result.
    - Raising the number of levels to 16 would double this to 48 Mbps in the same 6 MHz, but the levels would be four times closer together and the system far more vulnerable to noise.
12. **In serial communication employing 8 data bits, a parity bit and 2 stop bits. What is the minimum band rate requested to sustain a transfer rate of 300 characters per second?** *[BAUST Assistant Programmer 2021 compact it 918 (ET: N/A)]*


    Answer:

    Given:
    - 8 data bits, 1 parity bit, 2 stop bits, and asynchronous serial framing always adds 1 start bit.
    - Transfer rate required = 300 characters per second.

    Step 1, total bits per character:
    - 1 start + 8 data + 1 parity + 2 stop = 12 bits per character.

    Step 2, minimum baud rate:
    - Baud rate = characters per second × bits per character = 300 × 12 = 3600 bits per second.

    Final answer: the minimum baud rate required is 3600 baud, that is 3600 bps.

    - Note on efficiency: only 8 of the 12 bits carry data, so the useful data rate is 300 × 8 = 2400 bps out of 3600 bps, that is 66.7 percent. The remaining 33.3 percent is framing overhead, which is the price of asynchronous transmission.
    - In this case the baud rate equals the bit rate, because each signal element carries one bit; they differ only when multilevel signalling is used.
13. **Find signal bit per second bound rate 1000 and 16-QAM signal.** *[BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)]*


    Answer:

    Given:
    - Baud rate, that is the signalling rate = 1000 symbols per second.
    - Modulation = 16-QAM.

    Step 1, bits per symbol:
    - 16-QAM has 16 constellation points, so each symbol carries log2 16 = 4 bits.

    Step 2, bit rate:
    - Bit rate = baud rate × bits per symbol = 1000 × 4 = 4000 bps.

    Final answer: the signal rate is 4000 bits per second, that is 4 kbps.

    - General relation: bit rate = baud rate × log2 L. For the same baud rate, 4-QAM would give 2000 bps, 64-QAM would give 6000 bps and 256-QAM would give 8000 bps, but each step needs a higher signal to noise ratio.
14. **Channel capacity related math. (প্রশ্ন সংগ্রহ করা সম্ভব হয়নি)** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1038 (ET: BUET)]*


    Answer: The two formulas required for any channel capacity problem, with the method.

    Nyquist, for a noiseless channel:
    - C = 2 B log2 L bps, where B is the bandwidth in Hz and L is the number of signal levels.
    - Rearranged: L = 2^(C / 2B), which gives the number of levels needed for a target rate.

    Shannon, for a noisy channel:
    - C = B log2(1 + SNR) bps, where SNR is the linear power ratio.
    - SNR(dB) = 10 log10(SNR), so SNR = 10^(SNR(dB)/10).
    - Shortcut: C ≈ B × SNR(dB) / 3, which is accurate for a high SNR.

    Method:
    - Convert the SNR from dB to linear form first, apply Shannon to find the real upper limit, then apply Nyquist to find how many signal levels are needed to reach that limit.
    - The practical capacity is the smaller of the two values, since Shannon sets the limit imposed by noise and Nyquist the limit imposed by bandwidth.

    Worked example: B = 1 MHz with an SNR of 63.
    - Shannon: C = 10⁶ × log2(64) = 10⁶ × 6 = 6 Mbps.
    - Nyquist, to reach 6 Mbps: 6 × 10⁶ = 2 × 10⁶ × log2 L, so log2 L = 3 and L = 8 levels.
    - Final answer: capacity 6 Mbps, requiring 8 signal levels.

## Network Topologies (12)

1. **What is Star vs Mesh Topology?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1449 (ET: N/A)]*


   Answer:

   | Point | Star topology | Mesh topology |
   |---|---|---|
   | Structure | Every node connects to one central hub or switch | Every node connects directly to every other node |
   | Number of links for n nodes | n | n(n − 1)/2 for full duplex |
   | Ports per node | 1 | n − 1 |
   | Reliability | The central device is a single point of failure | Very high, many alternative paths |
   | Cost and cabling | Low, easy to install | Very high, cabling grows quadratically |
   | Fault isolation | Easy, a faulty link affects one node only | Easy, but tracing a fault in many links is laborious |
   | Expansion | Easy, add a cable to a free port | Hard, a new node needs a link to every existing node |
   | Typical use | Office and campus LANs, the usual Ethernet layout | Backbone links, WAN cores, military and mission critical networks |
2. **(b) Define network topology and classify it.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1446 (ET: N/A)]*


   Answer: Network topology is the physical or logical arrangement of the nodes and the links that connect them in a network, that is how the devices are laid out and how data flows between them.

   - Physical topology is the actual cabling layout; logical topology is the path the data actually follows, and the two need not be the same. Ethernet on a switch is physically a star but logically a bus in the old hub days.

   Classification:
   - Bus: every computer and device connects to one single backbone cable, through short drop lines.
     - Advantages: it needs the least cable, one backbone plus N drop lines. It is cheap, the installation method is well known, and it suits a small network.
     - Disadvantages: if the backbone cable fails, the whole network dies. Heavy traffic causes many collisions. Adding devices slows the network. Security is low.
   - Ring: the devices form a ring. Each node connects to exactly two neighbours, and the data flows in one direction, or both ways in a dual ring.
     - Advantages: high speed transmission, very little chance of collision, and it is cheap to install and to extend.
     - Disadvantages: one failed node can bring down the whole ring. Faults are hard to trace. Security is low.
   - Star: every device connects to one central hub, like spokes on a wheel.
     - Advantages: it needs only N cables for N devices, and each device needs just one port. It is robust, because one broken link does not affect the others. Faults are easy to find, and the cabling is cheap.
     - Disadvantages: if the hub fails, the whole network fails. Installation cost is high. The performance depends completely on the hub.
   - Mesh: every device connects to every other device through its own dedicated channel.
     - Number of links for N devices = N × (N − 1) / 2
     - Advantages: very fast communication, a robust design, easy fault diagnosis, and dedicated channels that make the transfer reliable and secure.
     - Disadvantages: installation and configuration are complex. The cable cost is very high, because of the bulk wiring. Maintenance is expensive. It suits only small networks.
   - Tree: a hierarchy. A central hub connects to secondary hubs, and those connect to the devices, making a parent-child structure.
     - Advantages: more devices can hang off the central hub. The signal travels a shorter distance. We can isolate and prioritise parts of the network. Adding a device is easy.
     - Disadvantages: if the central hub fails, the whole system fails. Cabling cost is high. Reconfiguring it when adding devices is difficult.
   - Hybrid: a mix of several topologies together, for example star-bus or star-ring. Most real campus networks are like this.
     - Advantages: very flexible in design, and easy to scale by adding new devices.
     - Disadvantages: the architecture is complex to design. It needs expensive hubs. The infrastructure and cabling cost is high.
3. **Write 4 topology name?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*


   Answer: Four topology names are Bus, Star, Ring and Mesh. Tree and Hybrid are the other two commonly listed.
4. **What is Network Topology? Distinguish between Bus, Ring, Tree and Star topology. Discuss how the Bus topology works.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 530 (ET: MIST)]*


   Answer: Network topology is the arrangement of nodes and the links connecting them, describing how devices are physically cabled and how data logically flows.

   Distinction between Bus, Ring, Tree and Star:

   | Point | Bus | Ring | Star | Tree |
   |---|---|---|---|---|
   | Layout | All nodes tap onto one common backbone cable | Each node connects to two neighbours forming a closed loop | All nodes connect to one central hub or switch | Groups of star networks connected to a common backbone in a hierarchy |
   | Cable needed | Least, one backbone plus n drops | n links | n links | n − 1 links |
   | Central device | None, terminators at both ends | None | Hub or switch, mandatory | Root switch plus secondary switches |
   | Single point of failure | The backbone cable | Any node or link breaks the ring, unless it is dual ring | The central hub | The root node and the backbone |
   | Fault isolation | Very hard | Hard | Easy, only one node is affected | Easy within a branch |
   | Expansion | Difficult, the backbone must be cut | Difficult, the ring must be broken | Easy, plug into a free port | Easiest, add a new branch |
   | Data flow | Broadcast in both directions, CSMA/CD | Unidirectional, token passing | Through the central device | Down the hierarchy |
   | Performance under load | Poor, collisions rise sharply | Predictable, no collision | Good with a switch | Good |
   | Cost | Lowest | Moderate | Higher, hub plus more cable | Highest |

   How Bus topology works:
   - A single backbone cable, normally coaxial, runs through the whole network and every computer taps onto it through a T connector or a vampire tap.
   - Both ends of the backbone carry a terminator, a resistor matching the cable impedance, which absorbs the signal and prevents reflection.
   - When a node transmits, the signal travels in both directions along the backbone and reaches every node, so the bus is a broadcast medium.
   - Every node reads the destination MAC address in the frame. The node whose address matches accepts the frame and all the others discard it.
   - Because the medium is shared, access is controlled by CSMA/CD. A node listens first, and if the line is free it transmits. If two nodes transmit together a collision occurs, a jam signal is sent, and both back off for a random time before retrying.
   - Performance therefore falls sharply as the number of nodes grows, and a single break in the backbone brings down the whole network. This is why bus topology, 10BASE2 and 10BASE5, has been replaced by switched star Ethernet.
5. **What is Personal Area Network? What is needed component and explain?** *[Mongla Port Authority Assistant Programmer 2023 compact it 572 (ET: N/A)]*


   Answer: A Personal Area Network is the smallest category of network, covering roughly 10 metres around a single person, and used to connect that person's own devices to each other.

   - Examples: a phone paired with a headset and a smartwatch, a laptop with a wireless mouse and keyboard, a fitness band syncing to a phone.
   - It may be wired, using USB or FireWire, or wireless, called WPAN, using Bluetooth, Zigbee, infrared or NFC.

   Components needed:
   - End devices: the phone, laptop, tablet, printer, headset or sensor that take part in the network.
   - A short range transceiver in each device, that is a Bluetooth, Zigbee, NFC or infrared radio module, which does the actual sending and receiving.
   - A master or coordinator device, usually the phone or laptop, which forms the piconet and controls the clock; in Bluetooth one master serves up to seven active slaves.
   - The wireless medium or cable: the 2.4 GHz ISM band for Bluetooth and Zigbee, or a USB cable for a wired PAN.
   - Protocol stack and profiles, for example the Bluetooth stack with A2DP for audio and HID for keyboards, which let two different manufacturers' devices understand one another.
   - Security elements: pairing, a PIN or passkey, and link encryption, so that a nearby stranger cannot join.
   - Power source, usually a small battery, which is why these standards are designed for very low power consumption.
6. **What is Topology in data communication? What are differences between Bus, Ring, Tree and Star topology? Purpose of IEEE 802.11 committee.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 512 (ET: MIST)]*


   Answer: Topology in data communication means the physical or logical layout of the devices and the links joining them, that is how the nodes are connected and how the data moves between them.

   Differences between Bus, Ring, Tree and Star:

   | Point | Bus | Ring | Star | Tree |
   |---|---|---|---|---|
   | Layout | All nodes tap onto one common backbone cable | Each node connects to two neighbours forming a closed loop | All nodes connect to one central hub or switch | Groups of star networks connected to a common backbone in a hierarchy |
   | Cable needed | Least, one backbone plus n drops | n links | n links | n − 1 links |
   | Central device | None, terminators at both ends | None | Hub or switch, mandatory | Root switch plus secondary switches |
   | Single point of failure | The backbone cable | Any node or link breaks the ring, unless it is dual ring | The central hub | The root node and the backbone |
   | Fault isolation | Very hard | Hard | Easy, only one node is affected | Easy within a branch |
   | Expansion | Difficult, the backbone must be cut | Difficult, the ring must be broken | Easy, plug into a free port | Easiest, add a new branch |
   | Data flow | Broadcast in both directions, CSMA/CD | Unidirectional, token passing | Through the central device | Down the hierarchy |
   | Performance under load | Poor, collisions rise sharply | Predictable, no collision | Good with a switch | Good |
   | Cost | Lowest | Moderate | Higher, hub plus more cable | Highest |

   Purpose of the IEEE 802.11 committee:
   - IEEE 802.11 is the working group that develops the standards for Wireless LAN, that is Wi-Fi.
   - It defines the physical layer and the MAC sublayer for wireless communication in the 2.4 GHz, 5 GHz and 6 GHz bands.
   - It specifies the CSMA/CA access method with RTS and CTS, since collision detection is not possible on a radio medium.
   - It standardises the security framework, WEP first, then WPA, WPA2 with 802.11i and now WPA3.
   - It ensures interoperability, so that equipment from different vendors works together, which is what the Wi-Fi Alliance certifies.
   - Well known amendments: 802.11a, b, g, n which is Wi-Fi 4, ac which is Wi-Fi 5, ax which is Wi-Fi 6, and be which is Wi-Fi 7.
7. **(খ) একটি নেটওয়ার্কে n সংখ্যক ডিভাইসের জন্যে Bus, Mesh এবং Star টপোলজিতে তারের লিংকগুলোর সংখ্যা কত?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 628 (ET: N/A)]*

   Answer: Number of links required for n devices:

   | Topology | Number of links | Reason |
   |---|---|---|
   | Bus | n links to the backbone, plus 1 backbone cable | Each device needs one drop cable onto the shared backbone |
   | Mesh | n(n − 1)/2 for duplex links, or n(n − 1) for simplex | Every device connects to every other, and each pair is counted once |
   | Star | n | Each device has exactly one cable to the central hub |

   - Ports required per device: n − 1 in a mesh, and 1 in both a star and a bus.
   - Example with n = 5: a bus needs 5 drops, a mesh needs 5 × 4 / 2 = 10 links, and a star needs 5 links.
   - This is why the cabling cost of a mesh grows with the square of n, so a full mesh is used only in small networks or in networks where reliability is critical.
8. **What is network topology? Write the name all different topology used in computer networking with example, diagram and their activities.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 673 (ET: N/A)]*


   Answer: Network topology is the physical or logical arrangement of nodes and links in a network.

   ```
   BUS                          STAR                    RING
   |--+----+----+----+--|          A                     A---B
      |    |    |    |             |                     |   |
      A    B    C    D          B--HUB--C                 D---C
   Terminators at both ends        |
                                   D

   MESH                         TREE
   A-----B                          ROOT
   |\   /|                        /      \
   | \ / |                     SW1        SW2
   |  X  |                    /   \      /   \
   | / \ |                   A     B    C     D
   D-----C
   ```

   Types, examples and activity:

   - Bus: one backbone cable with terminators, all nodes tap on. Example, old 10BASE2 coaxial Ethernet. Activity: a node broadcasts, every node hears it, only the addressed node keeps it, and CSMA/CD resolves collisions. Cheap but a single break kills the network.
   - Star: all nodes cable to a central hub or switch. Example, modern office LAN with a switch and UTP cable. Activity: every frame goes to the central device, which forwards it to the correct port. Easy to install and troubleshoot, but the hub is a single point of failure.
   - Ring: a closed loop, data travels in one direction. Example, Token Ring and FDDI. Activity: a token circulates and only the node holding it may transmit, so there are no collisions and delay is predictable. A single break stops the ring unless a dual counter-rotating ring is used.
   - Mesh: every node linked to every other, n(n − 1)/2 links. Example, WAN backbone and Internet core routers. Activity: traffic takes a direct path, and if one link fails another is used. Highest reliability, highest cost.
   - Tree: a hierarchy of stars on a common backbone. Example, a campus network with a core switch, distribution switches and access switches. Activity: traffic flows up and down the hierarchy; the root is critical.
   - Hybrid: any mixture, for example star-bus or star-ring. Example, a large corporate network. Activity: takes the strong points of each, at the cost of complex design and management.
9. **Write down the types of topology.** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*


   Answer: The types of topology are:

   - Bus
   - Star
   - Ring
   - Mesh
   - Tree, also called hierarchical
   - Hybrid, any combination of the above such as star-bus or star-ring
10. **Write down the Disadvantages of Bus topology.** *[DMLC Assistant Teacher (ICT) 2021 compact it 825 (ET: N/A)]*


    Answer: Disadvantages of bus topology:

    - The entire network fails if the single backbone cable breaks anywhere, so it has no fault tolerance.
    - Fault isolation is very difficult; the whole cable has to be checked to find the break.
    - Only one node can transmit at a time, so collisions increase sharply as nodes are added and performance falls with load.
    - Limited cable length and limited number of nodes; the signal weakens with distance and needs repeaters.
    - Terminators are essential at both ends, and a missing or wrong terminator causes reflections that corrupt all traffic.
    - Adding or removing a node normally disturbs the running network.
    - Security is poor because every node receives every frame, so traffic is easy to sniff.
    - It cannot support high speed, which is why it has been replaced by switched star Ethernet.
11. **(b) Define network topologies with features.** *[National University Assistant Programmer 2020 compact it 977 (ET: DU)]*


    Answer: Network topology is the physical or logical arrangement of nodes and links in a network. Physical topology is the cable layout, and logical topology is the actual path the data takes.

    Topologies with their features:

    - Bus: single backbone with terminators. Features are lowest cable cost, easy for a small network, broadcast medium with CSMA/CD, no central device, but a single cable fault brings down everything and performance falls with load.
    - Star: all nodes to a central hub or switch. Features are easy installation and expansion, easy fault isolation, one faulty cable affects one node only, good performance with a switch, but the central device is a single point of failure and more cable is needed.
    - Ring: nodes in a closed loop with unidirectional flow. Features are collision free token passing, predictable and fair delay under heavy load, equal access for all, but one break stops the ring and adding a node interrupts service.
    - Mesh: every node linked to every other. Features are the highest reliability with many redundant paths, dedicated links so no congestion, privacy and easy fault identification, but n(n − 1)/2 links make it very costly and hard to install.
    - Tree: hierarchy of stars on a backbone. Features are good scalability, easy segmentation and management, suits large campus networks, but the root and backbone are critical and the design is more complex.
    - Hybrid: a mixture such as star-bus. Features are flexibility, scalability and the ability to use the best topology in each part, at the cost of complex design and higher management effort.
12. **(d) List some various types of Topologies. What are the factors to choose a topology?** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1030 (ET: N/A)]*


    Answer:

    Types of topology: Bus, Star, Ring, Mesh, Tree and Hybrid.

    Factors to consider when choosing a topology:
    - Cost: the amount of cable and the number of ports and switches needed. Bus is cheapest, full mesh is the most expensive.
    - Reliability and fault tolerance: how much of the network stops if one link or one device fails. Mesh is best, bus is worst.
    - Scalability: how easy it is to add nodes later. Star and tree expand easily, ring and bus do not.
    - Number of nodes and the physical distance between them, and the geography of the site, that is one floor, several floors or several buildings.
    - Required bandwidth and traffic pattern: heavy or real time traffic rules out shared media such as bus.
    - Ease of installation and maintenance, and how quickly a fault can be located and repaired.
    - Availability of skilled staff and of spare equipment.
    - Security requirements: a shared medium exposes every frame to every node.
    - Future growth and the budget available, including cabling that will still be usable in five years.

## IPv6 Addressing (11)

1. 4B:30:10:21:2A:1B, 4C:20:1B:2E:08:E7 Identify which of the given IPv6 addresses represent Unicast and Multicast communication, and determine whether any of them represents a Broadcast address. Explain your answer based on the IPv6 addressing rules. [BSCCPL AME 21-08-2026 (BUET)]


   Answer: Neither of the two given values is a valid IPv6 address. Both are 48 bit MAC addresses, written as six hexadecimal pairs separated by colons, whereas an IPv6 address is 128 bits written as eight groups of four hex digits.

   Judged by IPv6 addressing rules:
   - Unicast: identifies a single interface. Global unicast begins with 2000::/3, link local with FE80::/10, and unique local with FC00::/7.
   - Multicast: identifies a group of interfaces. An IPv6 multicast address always begins with FF, that is FF00::/8, and the packet is delivered to every member of the group.
   - Anycast: syntactically identical to unicast, delivered to the nearest member of the group.
   - Broadcast: IPv6 has no broadcast address at all. Its function is replaced by the all-nodes multicast address FF02::1, which reaches every node on the link.

   Conclusion:
   - Since neither `4B:30:10:21:2A:1B` nor `4C:20:1B:2E:08:E7` begins with FF, neither would be multicast; and since neither is 128 bits long, neither is a valid IPv6 address of any kind.
   - No IPv6 address can represent broadcast, because the concept does not exist in IPv6. <!-- verify -->
2. A host is connected to an IPv6 network and needs to configure its own IPv6 address automatically using Stateless Address Autoconfiguration (SLAAC). Arrange the steps in the correct order and explain the purpose of each step. [BSCCPL AME 21-08-2026 (BUET)]


   Answer: SLAAC lets a host build its own IPv6 address without any DHCP server.

   Correct order of steps:
   - Step 1, link local address generation. The host forms `FE80::` plus a 64 bit interface identifier, made either from the MAC address by the modified EUI-64 method or randomly for privacy. Purpose: to have a usable address for local communication before anything else.
   - Step 2, Duplicate Address Detection. The host sends a Neighbor Solicitation for its own tentative address. If nobody replies, the address is unique and becomes valid. Purpose: to guarantee no two hosts on the link use the same address.
   - Step 3, Router Solicitation. The host sends an RS message to the all-routers multicast address FF02::2. Purpose: to ask the routers on the link to advertise immediately instead of waiting for the periodic advertisement.
   - Step 4, Router Advertisement. The router replies with an RA to FF02::1 carrying the /64 prefix, the default gateway, the MTU and the A, M and O flags. Purpose: to give the host the network part of its address and the route out.
   - Step 5, global address formation. The host concatenates the advertised 64 bit prefix with its own 64 bit interface identifier to make a full 128 bit global unicast address. Purpose: to obtain a routable Internet address.
   - Step 6, Duplicate Address Detection on the new global address, exactly as in step 2. Purpose: to confirm the global address is unique before use.
   - Step 7, optional stateless DHCPv6. If the O flag is set in the RA, the host asks a DHCPv6 server only for extra information such as DNS and NTP servers, not for an address. Purpose: SLAAC itself does not supply DNS.

   ```mermaid
   graph TD
       A["Link-local FE80:: + Interface ID"] --> B["DAD on link-local"]
       B --> C["Router Solicitation to FF02::2"]
       C --> D["Router Advertisement: prefix + gateway"]
       D --> E["Global address = Prefix + Interface ID"]
       E --> F["DAD on global address"]
       F --> G["Optional stateless DHCPv6 for DNS"]
   ```
3. **(a) What are the differences between IPv4 and IPv6, and why is IPv6 considered more secure?** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*


   Answer:

   Differences between IPv4 and IPv6:

   | Point | IPv4 | IPv6 |
   |---|---|---|
   | Address size | 32 bits, about 4.3 billion addresses | 128 bits, about 3.4 × 10³⁸ addresses |
   | Notation | Dotted decimal, 192.168.1.1 | Hexadecimal with colons, 2001:0db8::1 |
   | Header | Variable, 20 to 60 bytes, 13 fields | Fixed 40 bytes, 8 fields, extension headers |
   | Checksum | Present in the header | Removed, left to the link and transport layers |
   | Fragmentation | Done by the sender and by routers | Only by the sender, using Path MTU Discovery |
   | Configuration | Manual or DHCP | SLAAC as well as DHCPv6 |
   | Broadcast | Present | Removed, replaced by multicast |
   | Address resolution | ARP | Neighbor Discovery Protocol using ICMPv6 |
   | Security | IPsec optional | IPsec designed in as part of the suite |
   | NAT | Needed because of address shortage | Not needed |
   | QoS | Type of Service field | Traffic Class and a 20 bit Flow Label |

   Why IPv6 is considered more secure:
   - IPsec support, that is authentication header and encapsulating security payload, is a mandatory part of the IPv6 specification, so end to end authentication, integrity and encryption are always available.
   - The huge address space makes address scanning impractical. Scanning one /64 subnet at a million probes per second would take hundreds of thousands of years, so automated worms and reconnaissance scans become useless.
   - No broadcast address means broadcast amplification attacks such as smurf are not possible.
   - End to end connectivity without NAT removes the protocol breakage that NAT causes, so security mechanisms that need the real address, such as IPsec, work properly.
   - Secure Neighbor Discovery, SEND, with cryptographically generated addresses, protects against the spoofing that plagues ARP in IPv4.
   - A caution worth stating: IPv6 is not automatically secure. IPsec is available but often not enabled, and new attack surfaces exist in Neighbor Discovery, rogue router advertisements and tunnelling. A firewall is still needed. <!-- verify -->
4. **How many bits in IPv4 and IPv6 address? Why NAT is not required in IPv6?** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 398 (ET: BUET)]*


   Answer:

   - IPv4 is 32 bits, written as four decimal octets, giving about 4.3 × 10⁹ addresses.
   - IPv6 is 128 bits, written as eight groups of four hexadecimal digits, giving about 3.4 × 10³⁸ addresses.

   Why NAT is not required in IPv6:
   - NAT exists only to work around the shortage of IPv4 addresses by letting many private hosts share one public address.
   - IPv6 has so many addresses that every device, including every sensor and every phone, can be given its own globally unique address, so there is nothing to conserve.
   - Removing NAT restores true end to end connectivity, which simplifies peer to peer applications, VoIP, online gaming and IPsec, all of which NAT breaks.
   - Routers no longer have to keep translation state, so forwarding is simpler and faster and there is no bottleneck.
   - Security is provided by firewalls and IPsec rather than by the accidental hiding that NAT gives.
5. **(ক) IP Address কী? IPv4 এবং IPv6 এর মধ্যে চারটি প্রধান পার্থক্য লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 415 (ET: N/A)]*

   Answer: An IP address is a network layer identifier used to identify uniquely every device connected to the Internet or to a network, and to deliver packets to it. It consists of two parts, the network part and the host part.

   Four main differences between IPv4 and IPv6:

   | Point | IPv4 | IPv6 |
   |---|---|---|
   | Address length | 32 bits, dotted decimal, 192.168.10.1 | 128 bits, hexadecimal with colons, 2001:0db8::1 |
   | Header | Variable, 20 to 60 bytes, with a checksum | Fixed 40 bytes, no checksum, with extension headers |
   | Configuration and NAT | Manual or DHCP, and NAT is needed because addresses are scarce | SLAAC or DHCPv6, and NAT is not needed |
   | Broadcast and security | Broadcast exists, IPsec is optional | No broadcast, multicast instead, IPsec is built in |
6. **(a) Differentiate between IPV4 and IPV6.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 896 (ET: N/A)], [BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)], [WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 501 (ET: N/A)], [BMA Signal Assistant Engineer (Computer) 2021 compact it 932 (ET: BUET)]*


   Answer:

   | Point | IPv4 | IPv6 |
   |---|---|---|
   | Address size | 32 bits, about 4.3 billion addresses | 128 bits, about 3.4 × 10³⁸ addresses |
   | Notation | Dotted decimal, 172.16.0.1 | Hexadecimal, colon separated, 2001:db8::1 |
   | Header size | 20 to 60 bytes, variable, 13 fields | Fixed 40 bytes, 8 fields |
   | Header checksum | Present | Removed |
   | Fragmentation | By sender and by intermediate routers | By the sender only, with Path MTU Discovery |
   | Address configuration | Manual or DHCP | SLAAC, and DHCPv6 when needed |
   | Address types | Unicast, multicast, broadcast | Unicast, multicast, anycast; no broadcast |
   | Address resolution | ARP, a broadcast protocol | Neighbor Discovery over ICMPv6, multicast based |
   | Security | IPsec optional | IPsec part of the specification |
   | NAT | Required | Not required |
   | QoS | Type of Service byte | Traffic Class plus a 20 bit Flow Label |
   | Minimum MTU | 576 bytes | 1280 bytes |
7. **IPv4 and IPv6 how many bits and Why is NAT not needed in IPv6?** *[RPGCL Assistant Manager (ICT) 2022 compact it 652 (ET: BUET)]*


   Answer:

   - IPv4 uses 32 bits, IPv6 uses 128 bits.
   - IPv4 therefore has about 4.3 billion addresses, IPv6 about 3.4 × 10³⁸.

   Why NAT is not needed in IPv6:
   - NAT was invented purely to stretch the exhausted IPv4 address space by sharing one public address among many private hosts.
   - IPv6 gives every device a globally unique address, even a /64 subnet alone holds 1.8 × 10¹⁹ addresses, so there is no shortage to work around.
   - Without NAT, end to end connectivity is restored, so peer to peer applications, VoIP, gaming and IPsec work without special handling or port forwarding.
   - Routers keep no translation table, so there is less state, less delay and no single point of failure.
   - Protection comes from stateful firewalls and IPsec instead, which is proper security rather than the accidental obscurity NAT provides.
8. **IPv6 address কত বিটের?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

   Answer: An IPv6 address is 128 bits long.

   - It is divided into 8 groups of 4 hexadecimal digits, separated by colons, for example 2001:0db8:85a3:0000:0000:8a2e:0370:7334.
   - The first 64 bits are normally the network prefix and the last 64 bits the interface identifier.
   - IPv4 was 32 bits, so IPv6 provides 2⁹⁶ times as many addresses, about 3.4 × 10³⁸ in all.
9. **What is the difference between stateful DHCPv6 and stateless DHCPv6?** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 840-841 (ET: N/A)]*


   Answer:

   | Point | Stateful DHCPv6 | Stateless DHCPv6 |
   |---|---|---|
   | Who gives the address | The DHCPv6 server assigns the IPv6 address from a pool | The host builds its own address by SLAAC from the router advertisement prefix |
   | What the server supplies | Address, plus DNS, domain and other options | Only extra options such as DNS server, domain name, NTP, SIP server |
   | State kept on the server | Yes, a binding table of which address went to which client | No address binding is kept |
   | Router Advertisement flags | M flag = 1, managed | M flag = 0, O flag = 1, other configuration |
   | Comparable to | IPv4 DHCP | SLAAC plus a small DHCP lookup for DNS |
   | When used | When the administrator must control and log exactly which host has which address, for example in a bank or a server VLAN | When simple automatic addressing is enough but DNS still has to be handed out |

   - The reason stateless DHCPv6 exists at all is that plain SLAAC gives the address and gateway but has no way to supply DNS server information in its original form, so a lightweight DHCPv6 exchange fills that gap.
10. **What is DHCPv6?** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 841 (ET: N/A)]*


    Answer: DHCPv6 is the Dynamic Host Configuration Protocol for IPv6, defined in RFC 8415, used to give IPv6 hosts their configuration automatically.

    - It runs over UDP, port 546 on the client and port 547 on the server.
    - It uses multicast rather than broadcast: the client sends to All_DHCP_Relay_Agents_and_Servers at FF02::1:2.
    - The message exchange is SOLICIT, ADVERTISE, REQUEST, REPLY, which parallels DORA in IPv4. A fast two message exchange, SOLICIT with rapid commit and REPLY, is also possible.
    - Clients are identified by a DUID, a DHCP Unique Identifier, instead of by the MAC address as in IPv4.
    - Two modes: stateful, where the server assigns the address itself, and stateless, where SLAAC gives the address and DHCPv6 supplies only DNS and similar options.
    - It also supports prefix delegation, DHCPv6-PD, where an ISP hands a whole /56 or /48 prefix to a customer router, which then subnets it internally.
11. **Explain IPv6 link local address and multicast address.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 843 (ET: N/A)]*


    Answer:

    Link local address:
    - Range FE80::/10, in practice every link local address begins with FE80.
    - It is created automatically on every IPv6 interface as soon as the interface comes up, by combining the FE80::/64 prefix with a 64 bit interface identifier derived from the MAC by modified EUI-64, or generated randomly.
    - Its scope is only the local link. Routers never forward a packet whose source or destination is link local, so the same address may be reused on every link, which is why an interface must be specified, for example `ping6 fe80::1%eth0`.
    - Uses: Neighbor Discovery, Duplicate Address Detection, router advertisements, and as the next-hop address in routing protocols such as OSPFv3, and for communication before any global address exists.

    Multicast address:
    - Range FF00::/8, so every multicast address starts with FF.
    - Format: `FF` then 4 flag bits, then 4 scope bits, then the 112 bit group ID. Scope 1 is interface local, 2 is link local, 5 is site local and E is global.
    - IPv6 has no broadcast at all; multicast performs that role, which is more efficient because only interested nodes process the packet.
    - Well known groups: FF02::1 all nodes on the link, FF02::2 all routers on the link, FF02::5 all OSPF routers, FF02::9 all RIP routers, and FF02::1:FFXX:XXXX the solicited node multicast address used by Neighbor Discovery in place of ARP.
    - The solicited node address is formed from the last 24 bits of the unicast address, so a Neighbor Solicitation disturbs only the very few hosts that share those bits, instead of every host as ARP broadcast does.

## Physical Layer & Optical Fiber (Attenuation & Power Budget) (11)

1. **A fiber optic network is designed using single-mode fiber with an attenuation of 0.35 dB/km. The network includes a splitter with a 14 dB loss as specified in the datasheet. Additionally, there are two mechanical splices (each with 0.1 dB loss) and two connectors (each with 0.75 dB loss). Given the following parameters:**
   * **Transmitter Power: 5 dBm**
   * **Receiver Sensitivity: -14 dBm**
   * **Fiber Attenuation: 0.35 dB/km**
   **Calculate the maximum fiber length (D) that can be used between the OLT (Optical Line Terminal) and ONU (Optical Network Unit) while maintaining an acceptable signal level.** *[Islami Bank PLC Senior Officer (Network/System) 14.03.2025 compact it 1332 (ET: BUET)]*


   Answer:

   Step 1, power budget available:
   - Power budget = Transmitter power − Receiver sensitivity = 5 dBm − (−14 dBm) = 19 dB.

   Step 2, fixed losses in the link:
   - Splitter loss = 14 dB
   - Splices = 2 × 0.1 = 0.2 dB
   - Connectors = 2 × 0.75 = 1.5 dB
   - Total fixed loss = 14 + 0.2 + 1.5 = 15.7 dB

   Step 3, loss left for the fibre:
   - Fibre loss allowed = 19 − 15.7 = 3.3 dB

   Step 4, maximum length:
   - D = fibre loss allowed / attenuation per km = 3.3 / 0.35 = 9.43 km

   Final answer: the maximum fibre length between the OLT and the ONU is about 9.43 km.

   - Note: if a system margin of 3 dB is reserved for ageing, repairs and temperature, only 0.3 dB is left for the fibre, which gives about 0.86 km, so in a real design a splitter of 14 dB and this transmitter would be used only over a very short span.
2. **(a) Why fiber optic cable is used in submarine instead of satellite?** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 431 (ET: BUET)]*


   Answer: Submarine communication uses fibre optic cable rather than satellite for the following reasons.

   - Capacity: a single modern submarine cable carries hundreds of terabits per second using WDM, while a communication satellite transponder set carries only a few gigabits. Bulk Internet traffic simply cannot fit on satellites.
   - Latency: a geostationary satellite is 35,786 km away, so one hop costs about 250 ms and a round trip about 500 ms. Light in fibre from Bangladesh to Singapore costs only a few tens of milliseconds. Interactive traffic, VoIP, trading and gaming need low delay.
   - Cost per bit: once laid, a cable carries enormous traffic for 25 years, so the cost per gigabit is a small fraction of satellite cost. Satellite bandwidth is rented and expensive.
   - Reliability and weather: fibre is unaffected by rain fade, solar interference, atmospheric absorption and sunspot outages, all of which degrade satellite links, particularly in the tropics during the monsoon.
   - Signal quality: fibre gives a very low bit error rate and no attenuation from weather, so error correction overhead is small.
   - Security: light in a fibre laid on the seabed is far harder to intercept than a radio beam that covers a whole continent.
   - Scalability: the capacity of an existing cable can be raised by upgrading only the terminal equipment, without touching the cable itself.
   - Satellite still has its place for remote islands, ships, aircraft, disaster recovery and broadcast, where laying cable is impossible.
3. **(b) Why the submarine cable is damaged under water?** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 432 (ET: BUET)]*


   Answer: Submarine cables are damaged under water mainly by human activity in shallow water and by natural events in deep water.

   Human causes, which account for most faults:
   - Fishing trawlers dragging bottom nets and beam trawls across the cable.
   - Ships' anchors dropped or dragged over a cable route, especially near ports and anchorages.
   - Dredging and sand mining, and construction of other cables or pipelines nearby.
   - Deliberate cutting, theft of cable for the copper and the steel armour, and sabotage.

   Natural causes:
   - Undersea earthquakes and the turbidity currents and submarine landslides they trigger, which can cut several cables at once, as happened off Taiwan in 2006.
   - Volcanic activity and seabed movement.
   - Strong currents and tides causing abrasion where the cable rubs against rock.
   - Marine life, notably shark bites on the shallow sections, which is why some cables carry an extra protective layer.
   - Corrosion of the armour and water ingress through a damaged sheath over time.

   Mitigation:
   - Heavier armouring and burial one to three metres under the seabed in shallow water, cable protection zones, route surveys, awareness campaigns for fishermen, and diverse routing so that one cut does not isolate a country. Bangladesh keeps both SEA-ME-WE 4 and SEA-ME-WE 5 for exactly this reason.
4. **(ক) ফাইবার অপটিক ক্যাবলের গঠন ও বৈশিষ্ট্য ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 614 (ET: N/A)]*


   Answer: Optical fibre cable-er gathan (structure):

   ```
   +---------------------------------------------+
   |  Outer Jacket (PVC, protects from moisture)  |
   |  +---------------------------------------+  |
   |  |  Strength member (Kevlar / aramid)     |  |
   |  |  +---------------------------------+   |  |
   |  |  |  Buffer coating (plastic)        |  |  |
   |  |  |  +---------------------------+   |  |  |
   |  |  |  |  Cladding (n2, lower RI)   |  |  |  |
   |  |  |  |  +-------------------+     |  |  |  |
   |  |  |  |  |  Core (n1, higher) |     |  |  |  |
   |  |  |  |  +-------------------+     |  |  |  |
   |  |  |  +---------------------------+   |  |  |
   |  |  +---------------------------------+   |  |
   |  +---------------------------------------+  |
   +---------------------------------------------+
   ```

   - Core: the central glass or silica strand that actually carries the light. Diameter is 8 to 10 micron in single mode and 50 or 62.5 micron in multimode. It has the higher refractive index, n1.
   - Cladding: a glass layer around the core with a slightly lower refractive index, n2. The difference between n1 and n2 is what causes total internal reflection and keeps the light inside the core.
   - Buffer coating: a plastic layer that protects the glass from moisture and physical damage.
   - Strength member: Kevlar or aramid yarn that takes the pulling force during installation so the glass is not stretched.
   - Outer jacket: the PVC or LSZH sheath that gives mechanical and environmental protection.

   Boishishtho (characteristics):
   - Very high bandwidth, terabits per second with WDM, far beyond copper.
   - Very low attenuation, about 0.2 dB/km at 1550 nm, so repeaters can be 80 to 100 km apart.
   - Complete immunity to electromagnetic and radio frequency interference, and no crosstalk.
   - Light in weight and small in diameter compared with copper of the same capacity.
   - No electrical conductivity, so it is safe in explosive environments and needs no earthing.
   - High security, because tapping the fibre disturbs the light and is easily detected.
   - Long life and no corrosion.
   - Limitations: brittle, needs skilled splicing with expensive fusion equipment, higher installation cost, and it cannot carry power to a remote device.
5. **Write down the Working principle of Optical Fibre.** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 649 (ET: BUET)]*


   Answer: An optical fibre works on the principle of Total Internal Reflection.

   Working principle:
   - The core has refractive index n1 and the cladding has a slightly lower refractive index n2, so n1 is greater than n2.
   - When light travels from the denser core towards the rarer cladding and strikes the boundary at an angle greater than the critical angle θc, where sin θc = n2 / n1, none of it escapes; it is entirely reflected back into the core.
   - The ray therefore bounces along the core from one boundary to the other, and in this way it is guided along the fibre even when the cable is bent.
   - Only rays entering within the acceptance cone are guided. The acceptance angle is given by the numerical aperture, NA = √(n1² − n2²) = sin θmax.

   ```mermaid
   graph LR
       A["Electrical signal"] --> B["Transmitter: LED or Laser diode"]
       B --> C["Optical pulse launched into core"]
       C --> D["Total internal reflection along the fibre"]
       D --> E["Receiver: PIN or APD photodetector"]
       E --> F["Electrical signal restored"]
   ```

   - The transmitter, an LED for short distance or a laser diode for long distance, converts the electrical bits into light pulses; light on means 1 and light off means 0.
   - The pulses travel through the core by total internal reflection with very little loss, about 0.2 dB/km at 1550 nm.
   - At the far end a photodiode, PIN or avalanche, converts the light back into an electrical current, which is amplified and regenerated.
   - Over long routes optical amplifiers such as EDFA boost the signal without converting it back to electrical form.
6. **Define the attenuation and dispersion in an optical fiber. Draw the block diagram of a long-haul optical fiber communication system.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*


   Answer:

   Attenuation:
   - Attenuation is the loss of optical power as the signal travels along the fibre, measured in dB/km.
   - Formula: α (dB/km) = (10 / L) × log10(Pin / Pout).
   - Causes are absorption by impurities such as OH ions and by the silica itself, Rayleigh scattering from microscopic density variations which dominates at short wavelengths, and bending losses, both macrobend and microbend.
   - It limits how far the signal can go before a repeater or amplifier is needed. Typical values are 0.35 dB/km at 1310 nm and 0.2 dB/km at 1550 nm.

   Dispersion:
   - Dispersion is the spreading of a light pulse in time as it travels, so that adjacent pulses overlap and cause intersymbol interference.
   - Types: modal dispersion, where different modes take different paths and so arrive at different times, which affects multimode fibre only; chromatic dispersion, where different wavelengths travel at slightly different speeds, made up of material and waveguide dispersion; and polarisation mode dispersion, which matters at very high bit rates.
   - It limits the maximum bit rate and hence the bandwidth-distance product, expressed in MHz·km. It is corrected by using single mode fibre, narrow linewidth lasers, dispersion shifted fibre and dispersion compensating modules.
   - In short, attenuation limits distance by weakening the signal, dispersion limits speed by blurring the pulse.

   Block diagram of a long-haul optical fibre communication system:

   ```mermaid
   graph LR
       A["Information source"] --> B["Electrical transmitter / Encoder"]
       B --> C["Optical source: Laser diode + Modulator"]
       C --> D["Source-to-fibre coupler"]
       D --> E["Optical fibre cable span"]
       E --> F["Optical amplifier EDFA / Repeater"]
       F --> G["Optical fibre cable span"]
       G --> H["Fibre-to-detector coupler"]
       H --> I["Photodetector: PIN or APD"]
       I --> J["Amplifier + Equalizer + Decoder"]
       J --> K["Destination"]
   ```
7. **Define the principle of data transmission through the fiber optic cable.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*


   Answer: Data transmission through fibre optic cable works on the principle of Total Internal Reflection, with the data carried as pulses of light.

   - The core has a higher refractive index n1 than the cladding n2.
   - Light striking the core-cladding boundary at an angle greater than the critical angle, sin θc = n2 / n1, is reflected completely back into the core with no energy escaping.
   - The pulse therefore zigzags along the core and is guided from one end to the other, even round bends.
   - Only light entering within the acceptance cone is guided; this is defined by the numerical aperture NA = √(n1² − n2²).

   Transmission steps:
   - The electrical bit stream drives an LED or a laser diode, which converts it into light pulses; light present is 1, absent is 0. This is intensity modulation.
   - The pulses travel through the core by total internal reflection with very low attenuation.
   - A photodiode at the far end converts the light back into an electrical current, which is amplified, reshaped and retimed.
   - For very long links, EDFA optical amplifiers boost the signal directly in the optical domain, and WDM lets many wavelengths share one fibre simultaneously.
8. **How can you do fix the signal attenuation problems?** *[BOF Assistant Programmer 2022 compact it 734 (ET: MIST)]*


   Answer: Signal attenuation is the weakening of the signal with distance. It is fixed by the following measures.

   General measures:
   - Use repeaters and regenerators at calculated intervals to reshape, retime and reamplify the signal.
   - Use amplifiers, an EDFA for optical links and a line amplifier for copper, at points where the level is still above the noise floor.
   - Shorten the cable run, or add an intermediate switch, so that no segment exceeds the standard limit, for example 100 metres for UTP Ethernet.
   - Choose a better medium: Cat 6 or Cat 6A instead of Cat 5, or fibre instead of copper where the distance is long.
   - Increase the transmitter power, within regulatory and eye safety limits.

   For copper cabling:
   - Use a thicker gauge conductor, which has lower resistance.
   - Keep the cable away from motors, fluorescent lamps and power cables, and use shielded cable where interference is unavoidable.
   - Avoid sharp bends, kinks and over-tightened cable ties, and keep the untwisted length at the connector under 13 mm.
   - Make proper terminations, test every link with a certified cable tester, and replace any run that fails.

   For fibre:
   - Clean and inspect connectors, since dirt is the commonest cause of unexpected loss.
   - Use fusion splices, about 0.1 dB, rather than mechanical splices or extra connectors.
   - Respect the minimum bend radius to avoid macrobend loss.
   - Work at 1550 nm rather than 1310 nm where the fibre loss is lower, and keep a proper power budget with a 3 dB margin.

   For wireless:
   - Use a higher gain antenna, raise the antenna height, keep the Fresnel zone clear, and add a repeater or a directional antenna.
9. **Where are the low loss transmission windows of silicon based optical fiber and Which window is the most popular in communication and wave. Draw diagram of a long haul WDM Transmission system.** *[BTCL Assistant Manager (Technical) 2021 compact it 765 (ET: BUET)]*


   Answer:

   Low loss transmission windows of silica fibre:
   - First window, around 850 nm, attenuation about 2 to 3 dB/km. Used with LED sources for short multimode links.
   - Second window, around 1310 nm, attenuation about 0.35 dB/km. This is the zero dispersion wavelength of standard single mode fibre.
   - Third window, around 1550 nm, attenuation about 0.2 dB/km, the minimum loss of silica. This is the C band, 1530 to 1565 nm.
   - A fourth and fifth window, the L band around 1625 nm and the E band around 1400 nm, became usable after the water peak caused by OH ions was removed in low water peak fibre.

   Most popular window:
   - The 1550 nm window, the C band, is the most popular for long haul communication.
   - Reasons: it has the lowest attenuation of any window, about 0.2 dB/km, so repeater spacing can be 80 to 100 km; the erbium doped fibre amplifier works exactly in this band; and it has the room for dense WDM with dozens of channels. Its higher chromatic dispersion is dealt with by dispersion shifted fibre or dispersion compensating modules.

   Long haul WDM transmission system:

   ```mermaid
   graph LR
       A["Tx1 lambda1"] --> M["WDM Multiplexer"]
       B["Tx2 lambda2"] --> M
       C["TxN lambdaN"] --> M
       M --> P["Post amplifier / Booster EDFA"]
       P --> F1["Fibre span 80 to 100 km"]
       F1 --> L["In-line EDFA + Dispersion compensator"]
       L --> F2["Fibre span 80 to 100 km"]
       F2 --> R["Pre amplifier EDFA"]
       R --> D["WDM Demultiplexer"]
       D --> X["Rx1 lambda1"]
       D --> Y["Rx2 lambda2"]
       D --> Z["RxN lambdaN"]
   ```
10. **A 1550nm fiber optic transmission Link if of 50km length without repeating with a signal mode fiber having loss of 0.2dB/km. The fiber is joined ever 2km with conductor each with 0.5dB loss. Determine the minimum average power which should be lunched in to the fiver in order to Tarantion an average optical power level of 10 micro-watts at the receiver.** *[BTCL Assistant Manager (Technical) 2021 compact it 766 (ET: BUET)]*


    Answer:

    Given:
    - Link length L = 50 km, fibre loss = 0.2 dB/km, wavelength 1550 nm, no repeater.
    - A connector every 2 km, each with 0.5 dB loss.
    - Required average received optical power = 10 microwatt.

    Step 1, fibre loss:
    - Fibre loss = 50 × 0.2 = 10 dB

    Step 2, number of joints and joint loss:
    - The fibre is joined every 2 km, so 50 / 2 = 25 sections and therefore 25 − 1 = 24 joints inside the link.
    - Joint loss = 24 × 0.5 = 12 dB

    Step 3, total link loss:
    - Total loss = 10 + 12 = 22 dB

    Step 4, required received power in dBm:
    - Pr = 10 log10(10 microwatt / 1 milliwatt) = 10 log10(0.01) = −20 dBm

    Step 5, launched power:
    - Pt (dBm) = Pr (dBm) + total loss = −20 + 22 = 2 dBm
    - In linear form, Pt = 10^(2/10) = 1.585 milliwatt

    Final answer: the minimum average power that must be launched into the fibre is 2 dBm, that is about 1.59 mW.

    - If a 3 dB system margin is also required, the launch power becomes 5 dBm, about 3.16 mW.
11. **কোন মাধ্যমে আলোর Pulse ব্যবহৃত হয়?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

    Answer: Pulses of light are used in optical fibre cable.

    - Data is sent as pulses of light produced by an LED or a laser diode, where light present represents 1 and light absent represents 0.
    - The light travels inside the core by total internal reflection, and at the far end a photodiode converts it back into an electrical signal.

## Network Address Translation (NAT) (11)

1. Network Address Translation (NAT) maps internal networks to the public internet.
   * (a) Explain the historical IP addressing limitation that made NAT a necessity globally.
   * (b) Explain the step-by-step logical translation process that occurs at a branch router when an internal employee (IP 192.168.1.5) sends a web request to an external server, and how the router correctly handles the returning response packet. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer:

   (a) The addressing limitation
   - IPv4 uses a 32-bit address, so only about 4.3 billion (2^32) addresses exist in total.
   - Internet growth from the 1990s (PCs, then mobiles and IoT) pushed demand far beyond this pool, and IANA gave out its last free blocks in 2011.
   - Early class-based allocation wasted addresses badly, because a single Class A block handed about 16 million addresses to one organisation.
   - RFC 1918 reserved private ranges (`10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`) that every organisation may reuse internally, but these are not routable on the public Internet.
   - NAT became the bridge: many private hosts share a few public addresses, which allowed IPv4 to survive until IPv6 is fully deployed.

   (b) Translation of the web request

   Outgoing packet:
   - The PC sends a packet with source `192.168.1.5:50000` and destination `203.0.113.10:80`.
   - It reaches the inside interface of the branch router, and the routing table sends it out through the outside interface.
   - The router replaces the source IP with its own public address `198.51.100.7` and replaces the source port with a free unique port, say `6001`.
   - The router creates a NAT table entry mapping `192.168.1.5:50000` to `198.51.100.7:6001`.
   - IP and TCP checksums are recalculated because the header changed, and the packet is forwarded to the Internet.

   Returning packet:
   - The server replies with source `203.0.113.10:80` and destination `198.51.100.7:6001`.
   - The router searches the NAT table using this destination IP and port.
   - The stored entry matches, so the destination is rewritten back to `192.168.1.5:50000`.
   - Checksums are recalculated again and the packet is delivered to the PC on the LAN.
   - Without that NAT table entry the router would have no way to know which internal host the reply belongs to.

2. **Connection between Public IP to Private IP is called __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: NAT (Network Address Translation), performed by the router or firewall placed at the boundary between the private network and the Internet.

3. **What is NAT? Explain with topological diagram.** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 589 (ET: BUET)]*

   Answer: NAT (Network Address Translation) is a router function that rewrites the IP address in a packet header, so that hosts using private IP addresses can communicate over the public Internet through one or a few public IP addresses.

   ```mermaid
   graph LR
       PC1["PC-1<br/>192.168.1.5"] --> SW[LAN Switch]
       PC2["PC-2<br/>192.168.1.6"] --> SW
       PC3["PC-3<br/>192.168.1.7"] --> SW
       SW --> R["NAT Router<br/>Inside: 192.168.1.1<br/>Outside: 198.51.100.7"]
       R --> NET((Internet))
       NET --> SRV["Web Server<br/>203.0.113.10"]
   ```

   - Left of the router is the inside local network, which uses private addresses that are not routable on the Internet.
   - Right of the router is the outside network, holding one registered public address.
   - The router keeps a NAT table and swaps private and public addresses in both directions.
   - The web server sees only `198.51.100.7`, so the internal structure stays hidden.

4. **Explain NAT? Differenc between IPv4 and IPv6.** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 549 (ET: BIBM)]*

   Answer: NAT translates private IP addresses into public IP addresses at the network boundary, allowing many internal hosts to reach the Internet through a small number of registered addresses. It also hides the internal topology, which adds a layer of security.

   Difference between IPv4 and IPv6:

   | Point | IPv4 | IPv6 |
   |---|---|---|
   | Address size | 32-bit | 128-bit |
   | Total addresses | about 4.3 × 10^9 | about 3.4 × 10^38 |
   | Notation | Dotted decimal (192.168.1.1) | Hexadecimal with colons (2001:db8::1) |
   | Header | 20–60 bytes, variable | 40 bytes, fixed |
   | Header checksum | Present | Removed |
   | Broadcast | Supported | Not used, multicast and anycast instead |
   | Configuration | Manual or DHCP | SLAAC (auto) or DHCPv6 |
   | IPsec | Optional | Designed in from the start |
   | Fragmentation | Sender and routers | Sender only |
   | NAT | Usually required | Generally not required |

5. **What is NAT? Write down the list of private IP address.** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 717 (ET: N/A)]*

   Answer: NAT (Network Address Translation) is the process of changing the source or destination IP address of a packet as it passes through a router, so that privately addressed hosts can communicate with the public Internet.

   Private IP address ranges defined in RFC 1918:
   - Class A: `10.0.0.0` to `10.255.255.255`, that is `10.0.0.0/8`, giving 16,777,216 addresses.
   - Class B: `172.16.0.0` to `172.31.255.255`, that is `172.16.0.0/12`, giving 1,048,576 addresses.
   - Class C: `192.168.0.0` to `192.168.255.255`, that is `192.168.0.0/16`, giving 65,536 addresses.
   - Any organisation may reuse these ranges internally, and Internet routers drop packets carrying them, so NAT is required before such traffic leaves the network.
   - `127.0.0.0/8` is loopback and `169.254.0.0/16` is APIPA link-local; these are reserved but are not usable private ranges.

6. **Briefly explain Network Address Translation (NAT).** *[IDRA Assistant Network Administrator 2022 compact it 727 (ET: N/A)]*

   Answer: NAT is a router service that replaces the private IP address of an outgoing packet with a public IP address, and reverses the change for the returning packet by using entries stored in a NAT table.

   - Purpose: save scarce public IPv4 addresses and hide the internal network from outside.
   - Types: Static NAT (fixed one-to-one), Dynamic NAT (one-to-one from a pool), and PAT or NAT Overload (many-to-one using port numbers).
   - Where: implemented on the border router or firewall.
   - Cost: it breaks true end-to-end addressing and complicates protocols such as IPsec, VoIP and peer-to-peer applications.

7. **(i) Network Address Translation (NAT) ছবি সহ ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 787 (ET: N/A)]*

   Answer: NAT (Network Address Translation) is a process running on a router that changes the private IP address of a packet into a public IP address. Because of this, many computers using private addresses can communicate with the Internet through only a few public addresses.

   ```mermaid
   graph LR
       A["PC-1<br/>192.168.10.2"] --> SW[LAN Switch]
       B["PC-2<br/>192.168.10.3"] --> SW
       SW --> R["NAT Router<br/>Private: 192.168.10.1<br/>Public: 103.15.20.5"]
       R --> NET((Internet))
   ```

   - The left side of the router is the private network, and those addresses are not routable on the Internet.
   - The right side is the public network, where one registered IP address is assigned.
   - While going out, the router replaces the source address with the public address and stores an entry in the NAT table.
   - When the reply returns, the router reads that NAT table and delivers the packet to the correct PC.
   - Benefit: public IP addresses are saved, and the internal network structure cannot be seen from outside.

8. **(b) What is NAT? Mention its advantages.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 794 (ET: N/A)]*

   Answer: NAT (Network Address Translation) is a technique in which a router rewrites the IP address of a packet, so that hosts holding private addresses can access the public Internet through a registered public address.

   Advantages:
   - Saves public IPv4 addresses, because hundreds of internal hosts can share a single public address, which slowed down IPv4 exhaustion.
   - Gives security by hiding topology, since external hosts see only the public address and unsolicited inbound connections are blocked by default.
   - Gives addressing flexibility, because the internal network can use any private range without permission from any authority.
   - Makes ISP change easy, as only the router configuration changes while internal hosts are never renumbered.
   - Allows load sharing, because static NAT can map incoming requests to different internal servers.

9. **(a) Why do we need NAT? What are its advantages? Draw a topology diagram to explain NAT.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 799 (ET: N/A)]*

   Answer:

   Why NAT is needed:
   - IPv4 has only about 4.3 billion addresses and the free pool is already finished, so every host cannot be given a public address.
   - Private ranges defined in RFC 1918 are not routable on the Internet, so traffic from them must be translated before it leaves the network.
   - Organisations want to keep their internal addressing hidden from the outside world.

   Advantages:
   - Conserves public IPv4 addresses.
   - Hides internal hosts and blocks unsolicited inbound traffic.
   - Internal addressing can be chosen freely and changed without informing any authority.
   - Changing the ISP needs a change only on the router, not on every host.

   ```mermaid
   graph LR
       H1["Host 192.168.1.10"] --> SW[Switch]
       H2["Host 192.168.1.11"] --> SW
       SW --> FW["NAT Router / Firewall<br/>Inside 192.168.1.1<br/>Outside 203.0.113.5"]
       FW --> NET((Internet))
       NET --> WS["Remote Server"]
   ```

   The router is the only device holding a public address, and every internal host reaches the Internet through it.

10. **Why do we need NAT? Draw a topology diagram to explain NAT.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 841 (ET: N/A)]*

    Answer: NAT is needed because IPv4 addresses are limited to about 4.3 billion and have already run out, while the private addresses defined in RFC 1918 cannot be routed on the Internet. NAT lets many private hosts reach the Internet through one public address and at the same time keeps the internal network hidden.

    ```mermaid
    graph LR
        P1["PC 192.168.0.2"] --> L[LAN Switch]
        P2["PC 192.168.0.3"] --> L
        L --> RT["NAT Router<br/>Inside 192.168.0.1<br/>Outside 198.51.100.20"]
        RT --> INT((Internet))
    ```

    - Inside the LAN every host uses a private address.
    - The router swaps that private address for `198.51.100.20` on the way out.
    - The reply is matched through the NAT table and sent back to the correct host.

11. **What is PAT? How does a network PAT work?** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 841 (ET: N/A)]*

    Answer: PAT (Port Address Translation), also called NAT Overload, is a form of NAT in which many private IP addresses share a single public IP address, and the individual sessions are separated by port numbers instead of by address.

    How it works:
    - An internal host sends a packet carrying its private IP and a source port, for example `192.168.1.5:1050`.
    - The router replaces the source IP with the single public IP and replaces the source port with a unique port that is not currently in use, for example `198.51.100.7:6001`.
    - It records this mapping in the PAT table, so private IP with private port is tied to public IP with the new port.
    - The reply arrives addressed to the public IP and that unique port, the router looks the port up in the table, and forwards the packet to the correct internal host and port.
    - If a second host also used port `1050`, PAT simply gives it a different public port such as `6002`, so the two replies never get mixed up.
    - Because the port field is 16-bit, one public address can theoretically track around 65,000 simultaneous sessions.

## Network Services (DHCP, NAT) (10)

1. **What is the DHCP in computer networking?** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 405 (ET: N/A)]*


   Answer: DHCP, Dynamic Host Configuration Protocol, is an application layer protocol that automatically assigns IP configuration to hosts on a network.

   - It supplies the IP address, subnet mask, default gateway and DNS server address, and it works over UDP, port 67 on the server and port 68 on the client.
   - Without it every machine would have to be configured by hand, which is slow and causes duplicate address conflicts.
   - The address is given on lease for a fixed time, and the client renews it at half the lease period.
2. **What is the NAT in Computer networking?** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 405 (ET: N/A)]*


   Answer: NAT, Network Address Translation, is the process by which a router rewrites the private IP address in a packet header into a public IP address, and the reverse on the way back.

   - It lets many hosts on a private network, for example 192.168.0.0/16, share one or a few public addresses, which conserves the limited IPv4 space.
   - Types are static NAT, one to one, dynamic NAT, from a pool, and PAT or NAT overload, where many hosts share one public IP and are separated by port number.
   - It also hides the internal addressing, which gives a degree of security.
   - Drawback: it breaks true end to end connectivity, complicates protocols that carry IP addresses in the payload such as FTP and SIP, and makes incoming connections need port forwarding.
3. **NAT Stands for __________?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*


   Answer: NAT stands for Network Address Translation.
4. **Which two services are required to enable a computer to receive dynamic IP address and access internet using domain names?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 634 (ET: N/A)]*


   Answer: The two services are DHCP and DNS.

   - DHCP, Dynamic Host Configuration Protocol, gives the computer a dynamic IP address along with the subnet mask, default gateway and DNS server address.
   - DNS, Domain Name System, resolves a domain name such as `www.example.com` into the IP address needed to reach it, so the user can browse using names instead of numbers.
5. **What is DHCP Server and why it is needed in a computer network.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 670 (ET: N/A)]*


   Answer: A DHCP server is a server that holds a pool of IP addresses and hands out complete IP configuration to clients automatically when they join the network.

   What it supplies:
   - IP address and subnet mask.
   - Default gateway.
   - DNS server addresses, and optionally NTP server, domain name, TFTP or boot server for PXE.

   Why it is needed:
   - Manual configuration of hundreds of machines is slow, error prone and impossible for guests and mobile devices.
   - It prevents duplicate IP address conflicts, because the server tracks which addresses are already leased.
   - Addresses are reused: when a lease expires the address returns to the pool, so a small pool serves a much larger number of occasional users.
   - Changing the DNS server or gateway for the whole network becomes a single change on the server instead of a visit to every desk.
   - Devices can move between subnets and get a correct address automatically, which is essential for laptops and phones.
   - Reserved or static bindings can still be made by MAC address for printers and servers, so control is not lost.
6. **(b) Explain the message flow between a DHCP server and client. Show necessary timing diagram.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 799 (ET: N/A)]*


   Answer: The client and server exchange four messages, remembered as DORA.

   ```mermaid
   sequenceDiagram
       participant C as DHCP Client (port 68)
       participant S as DHCP Server (port 67)
       C->>S: DHCPDISCOVER (broadcast 255.255.255.255)
       S->>C: DHCPOFFER (offers an IP, mask, gateway, DNS, lease)
       C->>S: DHCPREQUEST (broadcast, accepts one offer)
       S->>C: DHCPACK (confirms, lease starts)
       Note over C,S: T1 = 50% of lease -> DHCPREQUEST to renew
       Note over C,S: T2 = 87.5% of lease -> broadcast rebind
       C->>S: DHCPRELEASE (when the client shuts down)
   ```

   Timing diagram of the lease:

   ```
   0%            50% (T1)        87.5% (T2)        100%
   |---------------|-----------------|---------------|
   ACK          RENEW to          REBIND to      lease expires,
   lease start  the same server   any server     address released,
                                                 client restarts DISCOVER
   ```

   - DHCPDISCOVER: the client has no address, so it broadcasts from 0.0.0.0 to 255.255.255.255 looking for any server.
   - DHCPOFFER: each server that hears it reserves an address and offers it with the lease time and options.
   - DHCPREQUEST: the client picks one offer and broadcasts its choice, so the other servers know to withdraw their offers.
   - DHCPACK: the chosen server confirms and the lease clock starts. If the address is no longer available it sends DHCPNAK instead and the client starts again.
   - If the DHCP server is on another subnet, a DHCP relay agent on the router forwards the broadcast as a unicast to the server.
7. **What is APIPA?** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 840 (ET: N/A)]*


   Answer: APIPA is Automatic Private IP Addressing.

   - When a Windows client cannot reach a DHCP server, it assigns itself an address from the range 169.254.0.1 to 169.254.255.254 with mask 255.255.0.0.
   - Before using it, the host performs an ARP check to make sure no other machine on the link already has that address.
   - It allows communication only within the same local link. There is no default gateway and no DNS, so the Internet is not reachable.
   - Seeing a 169.254.x.x address on a PC is therefore a clear diagnostic sign that DHCP has failed, that the cable or switch port is faulty, or that the relay agent is misconfigured.
   - The client keeps retrying for a DHCP server in the background, and switches to the real address as soon as one answers.
8. **What do you mean by DHCP server? Explain the benefits of using dedicated DHCP server. Briefly describe the main benefits of using IPv6 protocol.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 914 (ET: N/A)]*


   Answer:

   DHCP server:
   - A server that automatically leases IP addresses and related configuration, that is subnet mask, default gateway and DNS servers, to clients using the DORA exchange over UDP ports 67 and 68.

   Benefits of a dedicated DHCP server:
   - Central control: the whole address plan, the gateway and the DNS settings are managed from one place, so a change is made once instead of on every host.
   - No duplicate addresses, because the server keeps a lease database.
   - Efficient reuse of a limited address pool through leases, which suits guest and mobile devices.
   - Scales to thousands of clients, which a router based DHCP service cannot do reliably.
   - Supports reservations by MAC, multiple scopes for many VLANs, and advanced options such as PXE boot, NTP and vendor options.
   - Better logging and auditing, since every lease is recorded with the MAC and the time.
   - Redundancy is possible with a failover pair or split scopes, so the network keeps working if one server fails.

   Main benefits of IPv6:
   - A 128 bit address space, about 3.4 × 10³⁸ addresses, so address exhaustion and the need for NAT disappear.
   - A simplified fixed 40 byte header with extension headers, so routers process packets faster and do not fragment in transit.
   - Stateless Address Autoconfiguration, so a host can build its own address without a DHCP server.
   - IPsec support is built into the design, which improves security.
   - Better support for multicast and anycast, and broadcast is removed altogether, which reduces unnecessary traffic.
   - Built in mobility support through Mobile IPv6, and a flow label field that makes QoS handling easier.
   - Hierarchical addressing gives smaller and more efficient routing tables on the Internet backbone.
9. **১৬. DHCP uses UDP port _____ for sending data to the server.** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 942 (ET: N/A)]*


   Answer: DHCP uses UDP port 67 for sending data to the server, and port 68 for the reply to the client.
10. **DHCP কি? DHCP কিভাবে কাজ করে লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1043 (ET: DPI)]*

    Answer: DHCP is the Dynamic Host Configuration Protocol, which automatically supplies a host with its IP address, subnet mask, default gateway and DNS server addresses, so that no manual configuration is needed. It runs over UDP, on port 67 at the server and port 68 at the client.

    How it works, the DORA process:
    - DHCPDISCOVER: the new client has no address, so it broadcasts a discover message from 0.0.0.0 to 255.255.255.255 to find any DHCP server on the link.
    - DHCPOFFER: every server that receives it reserves a free address from its pool and offers it back, together with the mask, the gateway, the DNS servers and the lease time.
    - DHCPREQUEST: the client accepts one offer and broadcasts its choice, so the remaining servers release the addresses they had reserved.
    - DHCPACK: the chosen server confirms the assignment and the lease period begins. If the address has meanwhile been taken, the server replies DHCPNAK and the client starts again.

    Lease management:
    - At 50 percent of the lease, called T1, the client unicasts a renewal request to the same server.
    - At 87.5 percent, called T2, if there was no reply, it broadcasts a rebind request to any server.
    - If the lease expires, the client gives up the address and starts again from DHCPDISCOVER.
    - DHCPRELEASE is sent when the client shuts down, returning the address to the pool.
    - If the server is on another subnet, a DHCP relay agent configured on the router forwards the client's broadcast to the server as a unicast.

## Digital Modulation & Signal Processing (BPSK, QPSK) (10)

1. **Draw Bit Error Rate vs Signal to Noise Ratio curve of QPSK and BPSK.** *[NWPGCL Assistant Manager (ICT) 12.01.2024 compact it 293 (ET: BUET)]*


   Answer: BER falls as SNR rises, and for the same Eb/N0 BPSK and QPSK give the same BER, but QPSK carries twice the bit rate in the same bandwidth.

   ```
   BER (log scale)
   1e-1 |*
        | \*
   1e-2 |  \ \
        |   \ \
   1e-3 |    \  \
        |     \   \
   1e-4 |      \    \
        |       \     \
   1e-5 |________\______\________
        0    4    8   12   16   20   Eb/N0 (dB)
              BPSK = solid, QPSK = dashed (overlapping)
   ```

   - For BPSK, BER = Q(√(2Eb/N0)); for QPSK, BER = Q(√(2Eb/N0)) as well, so the two curves lie on top of each other when plotted against Eb/N0.
   - If the curve is plotted against SNR per symbol instead of per bit, QPSK sits about 3 dB to the right of BPSK, because each QPSK symbol carries two bits.
   - The curve is a waterfall shape: almost flat at low SNR, then falling very steeply once the SNR crosses about 8 to 10 dB.
   - Practical reading: at Eb/N0 = 9.6 dB both schemes give a BER of about 10⁻⁵.
   - Higher order schemes such as 8-PSK and 16-QAM shift the curve to the right, that is they need more SNR for the same BER, but give higher spectral efficiency.
2. **What is baseband and passband frequency?** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 499 (ET: N/A)]*


   Answer:

   Baseband:
   - The original signal in its own frequency range, starting from or near 0 Hz, without any modulation. Human voice at 300 to 3400 Hz and the digital output of a computer are baseband signals.
   - Baseband transmission puts these frequencies directly onto the medium, so only one signal can occupy the medium at a time and the medium must support very low frequencies. Ethernet on a LAN cable is a baseband system.

   Passband:
   - The band of frequencies around a high carrier frequency into which the baseband signal is shifted by modulation.
   - If the carrier is fc and the baseband bandwidth is B, the passband occupies fc − B to fc + B.
   - Passband transmission is needed for wireless and for any medium that cannot pass low frequencies, and it allows many signals to share the medium by giving each one a different carrier, which is frequency division multiplexing.
   - Example: an FM radio station modulates a 15 kHz audio baseband onto an 88 to 108 MHz carrier.
3. **অথবা, (ক) Low-pass Channel এবং Band-pass Channel এর মধ্যে উদাহরণসহ পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 628 (ET: N/A)]*


   Answer:

   | Point | Low-pass channel | Band-pass channel |
   |---|---|---|
   | Frequency range | 0 to some upper limit f, includes DC | f1 to f2, where f1 is greater than 0 |
   | Signal it can carry | Baseband signal directly | Only a modulated signal around a carrier |
   | Modulation | Not required | Required, the baseband must be shifted up |
   | Bandwidth | Equal to the upper cut-off frequency | f2 − f1 |
   | Example | Ethernet on twisted pair or coaxial LAN cable, a dedicated link | Telephone line 300 to 3400 Hz, radio, TV, mobile network |

   - A low-pass channel is used when the whole medium belongs to one signal, which is why LAN cabling uses baseband.
   - A band-pass channel is used when the medium must be shared, so each user is given a different band, and the data must first be modulated onto a carrier inside that band. A dial-up modem exists precisely because the telephone line is a band-pass channel.
4. **What is modulation? Why is it necessary?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 637 (ET: N/A)]*


   Answer: Modulation is the process of changing a property of a high frequency carrier signal, that is its amplitude, frequency or phase, in step with the message signal that has to be transmitted.

   Types:
   - Analog: AM, FM, PM.
   - Digital: ASK, FSK, PSK, QAM.

   Why it is necessary:
   - Antenna size: the antenna must be about one tenth to one half of the wavelength. A 3 kHz voice signal would need an antenna of tens of kilometres, but on a 100 MHz carrier the antenna is about a metre.
   - Multiplexing: many signals can share one medium if each is placed on a different carrier frequency, so stations do not interfere with one another.
   - Long distance transmission: high frequency signals travel further and can be reflected or refracted, so coverage improves.
   - Noise immunity: FM and digital modulation schemes resist noise far better than a raw baseband signal.
   - Matching the channel: a band-pass medium such as a telephone line or the air cannot carry low baseband frequencies at all, so shifting the signal up is the only way to use it.
   - Reduced interference and better use of the available spectrum.
5. **Amplitude Modulation related problem. (Approximate)** *[NPCBL Executive Trainee (IT) 2022 compact it 644 (ET: BUET)]*


   Answer: Standard AM problem method, shown with a typical worked case.

   Formulas:
   - Modulation index, m = Am / Ac, or m = (Vmax − Vmin) / (Vmax + Vmin).
   - Bandwidth, BW = 2 × fm.
   - Total power, Pt = Pc (1 + m²/2).
   - Power in each sideband = Pc m² / 4, and total sideband power = Pc m² / 2.
   - Efficiency, η = m² / (2 + m²).

   Worked example: a carrier of 10 kW is amplitude modulated to a depth of 60 percent by a 5 kHz tone.
   - m = 0.6, Pc = 10 kW, fm = 5 kHz.
   - Bandwidth = 2 × 5 = 10 kHz.
   - Pt = 10 × (1 + 0.36/2) = 10 × 1.18 = 11.8 kW.
   - Total sideband power = 11.8 − 10 = 1.8 kW, so each sideband carries 0.9 kW.
   - Efficiency = 0.36 / 2.36 = 0.1525, that is 15.25 percent.

   Final answer: BW = 10 kHz, total transmitted power = 11.8 kW, sideband power = 1.8 kW, efficiency = 15.25 percent.

   - Note the key weakness of AM that the examiner looks for: more than 84 percent of the power sits in the carrier, which carries no information, which is why SSB and DSB-SC are used where power matters.
6. **Compare between (i) AM and ASK and (ii) FM and FSK considering modulation scheme, bandwith requirement, noise tolerance and circuit complexity.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*


   Answer:

   (i) AM vs ASK

   | Point | AM | ASK |
   |---|---|---|
   | Modulating signal | Analog | Digital, a bit stream |
   | Scheme | Carrier amplitude varies continuously with the message | Carrier amplitude switches between discrete levels, typically on and off |
   | Bandwidth | 2 fm | About (1 + d) × Nbaud, roughly equal to the bit rate |
   | Noise tolerance | Poor, noise directly affects amplitude | Poor as well, but the receiver only has to decide between levels, so it is a little better |
   | Circuit complexity | Simple | Simple, the simplest digital scheme |

   (ii) FM vs FSK

   | Point | FM | FSK |
   |---|---|---|
   | Modulating signal | Analog | Digital |
   | Scheme | Carrier frequency varies continuously with the message amplitude | Carrier switches between two or more fixed frequencies, f1 for 0 and f2 for 1 |
   | Bandwidth | Carson's rule, BW = 2(Δf + fm), much wider than AM | BW = Nbaud + Δf, wider than ASK |
   | Noise tolerance | Very good, amplitude noise is removed by the limiter | Very good, far better than ASK |
   | Circuit complexity | Complex, needs a VCO and a discriminator or PLL | Moderate, more complex than ASK but simpler than PSK |

   - Common thread: the analog scheme and its digital counterpart use the same carrier property, so they share the same noise behaviour, but the digital version needs only a finite set of decisions at the receiver, which makes regeneration possible.
7. **What are the advantages of PSK and explain why coherent detection is necessary for demodulating the PSK signal?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*


   Answer:

   Advantages of PSK:
   - Better noise immunity than ASK, because the information is in the phase and amplitude noise does not directly corrupt it.
   - Constant envelope, so the transmitter power amplifier can be run in saturation, which is efficient, and there is no amplitude distortion problem.
   - Better bandwidth efficiency than FSK, since it does not need separate frequency slots.
   - For the same bit error rate, BPSK needs about 3 dB less power than coherent FSK and much less than ASK.
   - It extends easily to multilevel schemes, QPSK, 8-PSK and QAM, which raise the data rate without extra bandwidth.
   - It suits regeneration in digital repeaters, so errors do not accumulate over long links.

   Why coherent detection is necessary:
   - In PSK the transmitted symbols differ only in phase, and phase is a relative quantity. The receiver has no absolute reference of its own.
   - A simple envelope detector cannot be used, because the envelope is constant for every symbol, so it carries no information.
   - Therefore the receiver must regenerate a local carrier that has exactly the same frequency and phase as the transmitted carrier, using a Costas loop or a squaring loop, and multiply the incoming signal by it. Only then does the phase difference appear as a positive or negative voltage at the integrator output.
   - If the local carrier is offset in phase by θ, the output is reduced by cos θ, and at θ = 90 degrees the output is zero, so detection fails completely.
   - The practical way out of the phase ambiguity is DPSK, differential PSK, where the information is put in the phase change between successive symbols, so no absolute reference is needed. The cost is about 1 dB extra power and a doubling of errors, because one wrong symbol corrupts the next.
8. **Draw the constellation diagram of QPSK, 8-PSK and 32-QAM. Why these multilevel signals prefereed and what are the challenges for multilevel modulation?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*


   Answer:

   Constellation diagrams, plotted on the in-phase and quadrature axes:

   ```
   QPSK, 4 points          8-PSK, 8 points on a circle       32-QAM, cross shape
        Q                            Q                              Q
        |                            |                       . . . . . .
    *   |   *                    *   *   *                  . . . . . . . .
        |                          \ | /                    . . . . . . . .
   -----+----- I               *----+----* I                . . . . . . . .
        |                          / | \                    . . . . . . . .
    *   |   *                    *   *   *                    . . . . . .
        |                            |                    (32 points, 4 corners removed)
   2 bits/symbol            3 bits/symbol                  5 bits/symbol
   ```

   - QPSK: four points at 45, 135, 225 and 315 degrees, all on one circle, one amplitude and four phases, 2 bits per symbol.
   - 8-PSK: eight points equally spaced by 45 degrees on a single circle, one amplitude and eight phases, 3 bits per symbol.
   - 32-QAM: a cross shaped grid of 32 points using several amplitudes and several phases, 5 bits per symbol.

   Why multilevel signals are preferred:
   - Bit rate = symbol rate × log2 M, so raising M raises the bit rate without raising the bandwidth.
   - Spectral efficiency in bits per second per hertz increases, which matters because spectrum is scarce and licensed.
   - The same physical channel can carry more users or a higher throughput, which is why LTE and Wi-Fi use 16-QAM, 64-QAM and 256-QAM.

   Challenges:
   - The points sit closer together, so the minimum distance shrinks and the same noise causes far more errors. Each step up needs several dB more SNR.
   - QAM and higher order PSK need very accurate carrier phase and timing recovery.
   - QAM has a varying envelope, so it needs a linear amplifier, which is less power efficient and needs back-off.
   - Higher sensitivity to phase noise, I-Q imbalance, non-linear distortion and multipath fading, so equalisation is required.
   - The receiver is more complex and more expensive.
9. **a) What is QAM? Explain it.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1030 (ET: N/A)]*


   Answer: QAM, Quadrature Amplitude Modulation, is a modulation scheme that varies both the amplitude and the phase of the carrier at the same time, so it combines ASK and PSK.

   - Two carriers of the same frequency but 90 degrees apart, cos(2πfct) and sin(2πfct), are used. These are called the in-phase (I) and quadrature (Q) carriers.
   - The bit stream is split into two streams; one modulates the amplitude of the I carrier and the other the amplitude of the Q carrier, and the two are added.
   - Transmitted signal: s(t) = I·cos(2πfct) − Q·sin(2πfct). Because the two carriers are orthogonal, the receiver can separate them again without interference.
   - Each combination of I and Q values gives one point on the constellation, so M-QAM carries log2 M bits per symbol. 16-QAM carries 4 bits, 64-QAM carries 6 bits and 256-QAM carries 8 bits per symbol.
   - Advantage: very high spectral efficiency in bits per second per hertz.
   - Disadvantage: the envelope is not constant, so a linear amplifier is needed, and the closely spaced points demand a high SNR.
   - Uses: cable modems, DSL, Wi-Fi, LTE and 5G, and digital TV.
10. **b) Draw diagram for 16 QAM having? (i) 3 amplitudes, 12 phases (ii) 4 amplitudes, 8 phases** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1030-1031 (ET: N/A)]*


    Answer: Both are 16-QAM, so both carry 4 bits per symbol and have 16 constellation points, but the points are distributed differently.

    (i) 3 amplitudes and 12 phases

    ```
    Ring 1 (small radius)  : 4 points at 45, 135, 225, 315 degrees
    Ring 2 (medium radius) : 8 points at 0, 45, 90, 135, 180, 225, 270, 315 degrees
    Ring 3 (large radius)  : 4 points at 0, 90, 180, 270 degrees
    Total = 4 + 8 + 4 = 16 points, 3 distinct amplitudes, 12 distinct phase angles
    ```

    (ii) 4 amplitudes and 8 phases

    ```
    Ring 1 : 2 points   at 0, 180 degrees
    Ring 2 : 6 points   at 45, 90, 135, 225, 270, 315 degrees
    Ring 3 : 6 points   at 0, 45, 135, 180, 225, 315 degrees
    Ring 4 : 2 points   at 90, 270 degrees
    Total = 2 + 6 + 6 + 2 = 16 points, 4 distinct amplitudes, 8 distinct phase angles
    ```

    - In both cases each point is one symbol representing a unique 4 bit pattern, since 2⁴ = 16.
    - The number of amplitudes is the number of distinct rings, that is distinct distances from the origin, and the number of phases is the number of distinct angles used across all rings.
    - Design rule: for good noise performance the points should be spread as evenly as possible, which is why practical systems use the square 4 × 4 grid rather than these ring arrangements.

## Flow Control & Data Link Layer (Stop-and-Wait) (9)

1. A single-mode optical fiber communication link connects two locations 250\text{ km} apart using WDM technology with 50 channels, where each channel provides a bit rate of 10\text{ Gbps}. The refractive index of the fiber is 1.5, and data is transmitted using the Stop-and-Wait protocol. A 1\text{ GB} file is divided into suitable data frames, and after successfully receiving each frame, the receiver sends a 54-byte acknowledgment (ACK) back to the sender. Assuming no processing or queuing delay, determine the total time required to completely transfer the 1\text{ GB} file, including data transmission time, propagation delay, ACK transmission time, and the Stop-and-Wait waiting time. [BSCCPL AME 21-08-2026 (BUET)]


   Answer:

   Given:
   - Distance d = 250 km = 250 × 10³ m
   - Refractive index of the fibre n = 1.5
   - WDM: 50 channels × 10 Gbps each
   - Protocol: Stop-and-Wait
   - File size = 1 GB
   - ACK size = 54 bytes
   - No processing or queuing delay

   Step 1 — Propagation speed in the fibre

   v = c / n

   where c = 3 × 10⁸ m/s is the speed of light in vacuum.

   v = (3 × 10⁸) / 1.5
   v = 2 × 10⁸ m/s

   Step 2 — Propagation delay (one way)

   Tp = d / v

   Tp = (250 × 10³) / (2 × 10⁸)
   Tp = 1.25 × 10⁻³ s

   Tp = 1.25 ms

   Step 3 — Total link capacity from WDM

   R = number of channels × bit rate per channel

   R = 50 × 10 Gbps
   R = 500 Gbps = 500 × 10⁹ bps

   Step 4 — Frame size

   The frame size is not stated, so the standard Ethernet payload of 1500 bytes is taken as the "suitable" frame size.

   L = 1500 bytes = 1500 × 8 = 12,000 bits
   ACK = 54 bytes = 54 × 8 = 432 bits

   Step 5 — Number of frames

   N = file size / frame size

   N = (1 × 10⁹ bytes) / (1500 bytes)
   N = 666,666.67 → 666,667 frames

   Step 6 — Transmission time of one data frame

   Tt = L / R

   Tt = 12,000 / (500 × 10⁹)
   Tt = 2.4 × 10⁻⁸ s = 0.024 µs = 24 ns

   Step 7 — Transmission time of one ACK

   Tack = 432 / (500 × 10⁹)
   Tack = 8.64 × 10⁻¹⁰ s = 0.000864 µs = 0.864 ns

   Step 8 — Time for one Stop-and-Wait cycle

   In Stop-and-Wait the sender transmits one frame and then waits idle until the ACK arrives.

   Tcycle = Tt + Tp + Tack + Tp = Tt + Tack + 2Tp

   Tcycle = 24 ns + 0.864 ns + 2 × 1,250,000 ns
   Tcycle = 24.864 ns + 2,500,000 ns
   Tcycle = 2,500,024.864 ns

   Tcycle = 2.500025 ms

   Step 9 — Total transfer time

   Ttotal = N × Tcycle

   Ttotal = 666,667 × 2.500025 × 10⁻³ s
   Ttotal = 1666.68 s

   Final answer: total time ≈ 1666.7 seconds ≈ 27.8 minutes ≈ 27 minutes 47 seconds.

   Step 10 — Link utilisation, which shows why the figure is so large

   η = Tt / Tcycle = useful transmission time / total cycle time

   η = 24 / 2,500,024.864
   η = 9.6 × 10⁻⁶ = 0.00096 %

   Interpretation, which is the point of the problem: the link can carry 500 Gbps, so a 1 GB file should take

   Tideal = (8 × 10⁹ bits) / (500 × 10⁹ bps) = 0.016 s = 16 ms

   but Stop-and-Wait takes 1666.7 s, which is more than 100,000 times longer. The reason is that the sender waits 2.5 ms of propagation for every 24 ns of transmission, so the line sits idle 99.999 % of the time. Stop-and-Wait is unusable on a long fat pipe, that is a link with a large bandwidth-delay product.

   Bandwidth-delay product of this link:

   BDP = R × 2Tp = 500 × 10⁹ × 2.5 × 10⁻³ = 1.25 × 10⁹ bits = 156.25 MB

   To keep such a link busy the window must hold about 156 MB of unacknowledged data, so a sliding-window protocol with a very large window, such as Go-Back-N or Selective Repeat with window scaling, is required. With a window of W frames the time becomes

   Ttotal = (N / W) × Tcycle,  for W ≤ 1 + 2Tp/Tt

   Note on the alternative reading: if the Stop-and-Wait session is taken to run over one WDM channel only, then R = 10 Gbps, Tt = 1.2 µs, Tack = 0.0432 µs, Tcycle = 2.501243 ms and Ttotal = 1667.5 s. The answer barely changes, because propagation delay, not bandwidth, dominates completely. This is itself worth stating: on this link, adding bandwidth does nothing at all for a Stop-and-Wait transfer.

   Note on the unit of 1 GB: if 1 GB is taken as 2³⁰ = 1,073,741,824 bytes, then N = 715,828 frames and Ttotal = 1789.6 s ≈ 29.8 minutes.
2. **Using an explanation of the difference between flow-control and congestion control, discuss the impact of a stable end-to-end latency.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 424 (ET: BIBM)]*


   Answer:

   | Point | Flow control | Congestion control |
   |---|---|---|
   | Problem addressed | A fast sender overwhelming a slow receiver | Too much traffic overwhelming the network itself |
   | Scope | End to end, between two hosts | Global, involves routers and the whole network |
   | Layer | Data link layer and transport layer | Mainly transport and network layer |
   | Mechanism | Sliding window, receiver advertised window | Slow start, congestion window, AIMD, ECN |
   | Who signals | The receiver, through the window size in the acknowledgement | The network, through packet loss, delay or ECN marks |

   Impact of a stable end to end connection:
   - When the path is stable, the round trip time stays predictable, so TCP's retransmission timer is accurate and unnecessary retransmissions are avoided.
   - The congestion window can grow to the full bandwidth delay product and stay there, so throughput reaches its maximum.
   - Buffer occupancy at the receiver stays steady, so the advertised window does not oscillate and the sender transmits smoothly.
   - On an unstable path, variable delay causes spurious timeouts, the congestion window repeatedly collapses to one, and throughput drops sharply even when no real congestion exists.
3. **(খ) Congestion কী? Network-এ কীভাবে Congestion নিয়ন্ত্রণ করা যায়? আলোচনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 415 (ET: N/A)]*


   Answer: Congestion occurs when the number of packets arriving at a part of the network exceeds what that part can handle, so router queues overflow and packets are dropped.

   Symptoms: rising queue length, growing delay, packet loss, many retransmissions and falling throughput. If it is not controlled it leads to congestion collapse, where the network is busy but almost no useful data gets through.

   Congestion control methods:
   - Open loop, that is prevention: admission control, traffic shaping with leaky bucket or token bucket, and proper resource allocation before congestion occurs.
   - Closed loop, that is reaction: the network detects congestion and feeds the information back, then the sender slows down.
   - TCP congestion control: slow start increases the window exponentially, congestion avoidance increases it linearly after a threshold, fast retransmit resends a lost segment after three duplicate acknowledgements, and fast recovery halves the window instead of dropping to one.
   - Choke packet: the router sends an explicit message to the source telling it to reduce its rate.
   - Explicit Congestion Notification marks packets instead of dropping them, so the sender is warned earlier.
   - Random Early Detection drops packets at random before the queue is completely full, which prevents global synchronisation.
   - Load shedding: when nothing else works, the router simply discards packets, preferring to drop lower priority ones.
4. **Unit of data link layer?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*


   Answer: The unit of data at the data link layer is called a frame.

   - A frame consists of a header, the payload received from the network layer, and a trailer.
   - The header carries the source and destination MAC address, and the trailer carries the error checking field, normally a CRC.
   - For reference, the unit is a bit at the physical layer, a packet or datagram at the network layer, a segment for TCP and a datagram for UDP at the transport layer, and data or a message at the application layer.
5. **(ক) নেটওয়ার্কে ডাটা প্যাকেটে trailer কোথায় এবং কেন ব্যবহার করা হয়? উদাহরণ দিন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 775 (ET: N/A)]*


   Answer: The trailer is placed at the end of the data link layer frame, after the payload.

   Why it is used:
   - It carries the error detection field, normally a Cyclic Redundancy Check, computed over the header and the data.
   - The receiver recomputes the CRC and compares it with the received value; if they differ the frame is discarded, so corrupted data never reaches the upper layer.
   - It may also carry a frame delimiter that marks the end of the frame.

   Why at the end rather than in the header:
   - The CRC can only be computed after the whole frame content is known, so placing it at the end lets the sender calculate and transmit it on the fly without buffering the entire frame first.

   Example, Ethernet frame:
   - Header: destination MAC 6 bytes, source MAC 6 bytes, type or length 2 bytes.
   - Payload: 46 to 1500 bytes.
   - Trailer: Frame Check Sequence of 4 bytes, which is the CRC-32 value.
6. **How STP works? Explain congestion control algorithm.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 842-843 (ET: N/A)]*


   Answer:

   How STP works:
   - STP is the Spanning Tree Protocol, defined in IEEE 802.1D, and its job is to prevent switching loops in a network that has redundant links.
   - Without it, a loop causes broadcast storms, multiple frame copies and MAC table instability, because Ethernet frames have no TTL field.
   - Step 1: all switches exchange BPDU messages and elect a Root Bridge, which is the switch with the lowest bridge ID, that is priority followed by MAC address.
   - Step 2: every other switch selects one Root Port, the port with the lowest path cost towards the root.
   - Step 3: on each network segment one Designated Port is chosen, again by lowest path cost.
   - Step 4: every remaining port is put into Blocking state, so the physical loop becomes a loop free logical tree.
   - Port states are Blocking, Listening, Learning, Forwarding and Disabled. Convergence takes about 30 to 50 seconds, which is why Rapid STP (802.1w) is normally used today.
   - If an active link fails, a blocked port is brought back into forwarding, so redundancy is preserved without a loop.

   Congestion control methods:
   - Open loop, that is prevention: admission control, traffic shaping with leaky bucket or token bucket, and proper resource allocation before congestion occurs.
   - Closed loop, that is reaction: the network detects congestion and feeds the information back, then the sender slows down.
   - TCP congestion control: slow start increases the window exponentially, congestion avoidance increases it linearly after a threshold, fast retransmit resends a lost segment after three duplicate acknowledgements, and fast recovery halves the window instead of dropping to one.
   - Choke packet: the router sends an explicit message to the source telling it to reduce its rate.
   - Explicit Congestion Notification marks packets instead of dropping them, so the sender is warned earlier.
   - Random Early Detection drops packets at random before the queue is completely full, which prevents global synchronisation.
   - Load shedding: when nothing else works, the router simply discards packets, preferring to drop lower priority ones.
7. **Host A is sending data to Host B over a full duplex link. A and B are using the sliding window protocol for flow control. The send and receive window size are 5 packets each. Data packets (sent only from A to B) are all 1000 bytes long and transmission time for such a packet is 50\mu\text{s}. Acknowledgement packets (sent only from B to A) are very small and require negligible transmission time. The propagation delay over the link is 200\mu\text{s}. What is the maximum achievable throughput in this communication?** *[BAUST Assistant Programmer 2021 compact it 918 (ET: N/A)]*


   Answer: In the sliding window protocol the sender may transmit a window of frames before waiting for an acknowledgement, which keeps the link busy instead of idle.

   Key relations:
   - Link utilisation = W / (1 + 2a), where W is the window size in frames and a is the ratio of propagation time to transmission time.
   - Transmission time Tt = frame size / bandwidth.
   - The optimum window size is W = 1 + 2a, because at that value the first acknowledgement returns exactly when the last frame of the window has been sent, so the link never goes idle.
   - Sequence number bits needed: for Go-Back-N the window must satisfy W ≤ 2ⁿ − 1, and for Selective Repeat W ≤ 2ⁿ⁻¹.

   Worked method:
   - Compute Tt = L / B and Tp = distance / propagation speed.
   - Compute a = Tp / Tt.
   - Efficiency = W / (1 + 2a), and effective throughput = efficiency × bandwidth.
   - Example: with L = 1000 bits, B = 1 Mbps and Tp = 10 ms, Tt = 1 ms so a = 10. Utilisation with W = 4 is 4/21 = 19 percent, while the optimum window 21 gives full utilisation.

   - Stop and wait is the special case W = 1, which is why it performs very poorly on long or fast links.
8. **What is the piggybacking and MAC Address?** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 921 (ET: N/A)]*


   Answer:

   Piggybacking:
   - It is the technique of carrying an acknowledgement inside an outgoing data frame instead of sending a separate acknowledgement frame.
   - When both sides are sending data, the receiver delays its acknowledgement for a short time and attaches it to the next data frame going in the reverse direction.
   - Advantage: fewer frames on the link, so bandwidth and processing are saved.
   - Disadvantage: if no reverse data appears within the timer, the acknowledgement is delayed, which may cause an unnecessary retransmission at the sender.

   MAC address:
   - A Media Access Control address is the 48 bit physical address permanently burned into a network interface card, written as six hexadecimal pairs such as `00:1A:2B:3C:4D:5E`.
   - The first 24 bits are the Organisationally Unique Identifier assigned to the manufacturer, and the last 24 bits identify the specific card.
   - It works at the data link layer and is used for delivery within a local network, whereas the IP address works at the network layer and is used for end to end routing.
   - A MAC address is flat and non-routable, while an IP address is hierarchical and routable.
9. **(i) Congestion Control কী? কী কী ভাবে Congestion Control করা যায়?** *[BPSC Assistant Network Engineer 2020 compact it 950 (ET: N/A)]*


   Answer: Congestion control means keeping the total traffic offered to the network within the capacity that the network can actually carry, so that queues do not overflow.

   Why it is needed:
   - Without it, routers drop packets, senders retransmit, the load rises further and throughput collapses. This is called congestion collapse.

   Congestion control methods:
   - Open loop, that is prevention: admission control, traffic shaping with leaky bucket or token bucket, and proper resource allocation before congestion occurs.
   - Closed loop, that is reaction: the network detects congestion and feeds the information back, then the sender slows down.
   - TCP congestion control: slow start increases the window exponentially, congestion avoidance increases it linearly after a threshold, fast retransmit resends a lost segment after three duplicate acknowledgements, and fast recovery halves the window instead of dropping to one.
   - Choke packet: the router sends an explicit message to the source telling it to reduce its rate.
   - Explicit Congestion Notification marks packets instead of dropping them, so the sender is warned earlier.
   - Random Early Detection drops packets at random before the queue is completely full, which prevents global synchronisation.
   - Load shedding: when nothing else works, the router simply discards packets, preferring to drop lower priority ones.

## Email Architecture & Protocols (SMTP, POP3, IMAP) (9)

1. **Sinthia wants to send an email to her friend (Afsana). He sends the email through application and transport layer.** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1323 (ET: DU)]*
   * (a) Mention the protocol of application layer and transport layer.
   * (b) Write down the steps of Mail transfer from Afsana to Sinthia.


   Answer:

   (a) Protocols used
   - Application layer: SMTP is used to push the mail from Sinthia's client to her mail server and onward to Afsana's mail server. Afsana retrieves it using POP3 or IMAP.
   - Transport layer: TCP is used, because mail delivery must be reliable and in order. SMTP uses port 25, POP3 uses 110 and IMAP uses 143.

   (b) Steps of mail transfer

   ```mermaid
   sequenceDiagram
       participant S as Sinthia (MUA)
       participant SS as Sender Mail Server (MTA)
       participant RS as Receiver Mail Server (MTA)
       participant A as Afsana (MUA)
       S->>SS: SMTP submit (port 587/25)
       SS->>SS: DNS MX lookup for recipient domain
       SS->>RS: SMTP transfer (port 25)
       RS->>RS: Store in Afsana's mailbox
       A->>RS: POP3 (110) or IMAP (143) request
       RS->>A: Deliver the message
   ```

   - Sinthia composes the mail in her Mail User Agent and clicks send.
   - The MUA opens a TCP connection to her own mail server and uses SMTP commands HELO, MAIL FROM, RCPT TO, DATA and QUIT.
   - Her mail server performs a DNS MX record lookup to find the mail server of Afsana's domain.
   - The two mail servers talk to each other over SMTP and the message is transferred and stored in Afsana's mailbox.
   - When Afsana opens her mail client, it fetches the message using POP3, which normally downloads and deletes, or IMAP, which keeps the mail on the server and synchronises across devices.
2. **Difference between: (i) SMTP and SNMP (ii) HTTP and HTTPs** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 550 (ET: BIBM)]*


   Answer:

   (i) SMTP vs SNMP

   | Point | SMTP | SNMP |
   |---|---|---|
   | Full form | Simple Mail Transfer Protocol | Simple Network Management Protocol |
   | Purpose | Sending and relaying email | Monitoring and managing network devices |
   | Transport and port | TCP 25 | UDP 161, and 162 for traps |
   | Components | MUA, MTA, MDA | Manager, Agent, MIB |
   | Example use | Delivering a mail from one server to another | Reading the CPU load or interface status of a router |

   (ii) HTTP vs HTTPS

   | Point | HTTP | HTTPS |
   |---|---|---|
   | Security | Data travels in plain text | Data is encrypted with TLS |
   | Port | 80 | 443 |
   | Certificate | Not required | An SSL/TLS certificate is required |
   | Protection | None against eavesdropping or tampering | Confidentiality, integrity and server authentication |
   | Speed | Marginally faster | Slightly slower due to the handshake, but negligible today |
   | Use | Non-sensitive public content | Login, banking, any page handling personal data |
3. **Which protocol is used for email received?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*


   Answer: POP3 and IMAP are the protocols used to receive or retrieve email.

   - POP3, Post Office Protocol version 3, port 110, normally downloads the mail to one device and deletes it from the server.
   - IMAP, Internet Message Access Protocol, port 143, keeps the mail on the server and synchronises it across many devices, so it suits modern usage.
   - SMTP, port 25, is used only for sending, not receiving.
4. **(a) Distinguish the purpose of SMTP and IMAP in email communication.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 688 (ET: N/A)]*


   Answer:

   | Point | SMTP | IMAP |
   |---|---|---|
   | Purpose | Sending and relaying mail | Retrieving and managing mail |
   | Direction | Client to server, and server to server | Server to client |
   | Port | 25, and 587 for client submission | 143, and 993 with TLS |
   | Storage | Does not store, it only pushes the message forward | Mail stays on the server and is synchronised |
   | Folder support | None | Full folder, flag and search support on the server |
   | Multi-device | Not applicable | Excellent, all devices see the same state |

   - In short, SMTP is the push protocol that gets the mail out, while IMAP is the pull protocol that lets the user read and organise it.
   - The two together, plus POP3 as an alternative to IMAP, make up the complete email architecture.
5. **Email এর ক্ষেত্রে CC এবং BCC এর অর্থ কি বুঝায়?** *[BPSC Computer Operator 2021 compact it 780 (ET: N/A)]*


   Answer:

   - CC stands for Carbon Copy. The addresses written in CC receive a copy of the mail, and every recipient can see who was placed in the To and CC fields. It is used to keep someone informed without making them the primary recipient.
   - BCC stands for Blind Carbon Copy. The addresses written in BCC also receive a copy, but they are hidden from all other recipients, and BCC recipients cannot see each other either.
   - BCC is used when a mail must go to many people without exposing their addresses to one another, for example a circular, and it also protects privacy.
6. **Which of the following is correct email formate? (a) compact@webmail.com (b) compact@webmail@com (c) compact.webmail.com (d) None** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*


   Answer: The correct format is (a) `compact@webmail.com`.

   - A valid email address has exactly one `@` symbol, separating the local part from the domain part.
   - Option (b) `compact@webmail@com` has two `@` symbols, which is invalid.
   - Option (c) `compact.webmail.com` has no `@` at all, so it is a domain name, not an email address.
   - The domain part must also contain at least one dot, for example `webmail.com`.
7. **E-mail পাঠানো এবং রিসিভ করার জন্য একটি করে প্রোটোকলের নাম লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 866 (ET: BUET)]*


   Answer:

   - Protocol for sending email: SMTP, the Simple Mail Transfer Protocol, which uses TCP port 25.
   - Protocol for receiving email: POP3, the Post Office Protocol version 3, on TCP port 110, or IMAP, the Internet Message Access Protocol, on TCP port 143.
8. **Which protocol provides e-mail facility amount different hosts?** *[BSEC Assistant Director (MIS) 2021 compact it 937 (ET: IBA)]*


   Answer: SMTP, the Simple Mail Transfer Protocol, provides the email facility between different hosts.

   - It is an application layer protocol that runs over TCP port 25.
   - It is a push protocol, used to transfer mail from the sender's client to the sender's mail server and then from one mail server to another.
   - It uses simple text commands such as HELO, MAIL FROM, RCPT TO, DATA and QUIT.
   - For retrieving mail from the server, POP3 or IMAP is used instead.
9. **ই-মেইল করার ক্ষেত্রে TO, CC ও BCC কোন ব্যবহার করা হয়?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 945 (ET: N/A)]*


   Answer:

   - TO: the primary recipient of the mail, that is the person the message is actually addressed to and who is expected to act on it. More than one address may be written here.
   - CC, Carbon Copy: people who should be kept informed but are not required to act. All recipients can see the CC list.
   - BCC, Blind Carbon Copy: people who receive a copy without any other recipient knowing. The BCC list is hidden from everyone, including the other BCC recipients.

   - Practical rule: use TO for the person responsible, CC for those who need visibility, and BCC when sending to a large group so that private addresses are not exposed.

## Application Layer & Well-Known Port Numbers (6)

1. Full Form and Port Number – SSH, FTP, SMTP, DNS, IMAP. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*


   Answer:

   | Protocol | Full form | Port |
   |---|---|---|
   | SSH | Secure Shell | 22 (TCP) |
   | FTP | File Transfer Protocol | 21 control, 20 data (TCP) |
   | SMTP | Simple Mail Transfer Protocol | 25 (TCP) |
   | DNS | Domain Name System | 53 (both TCP and UDP) |
   | IMAP | Internet Message Access Protocol | 143 (TCP), 993 for IMAPS |
2. **What is the port number used by DNS?** *[BBA Assistant Programmer 12.07.2025 compact it 1432 (ET: BUET)], [BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)], [BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: DNS uses port number 53.

   - It uses UDP port 53 for ordinary queries and responses, because UDP is fast and the messages are small.
   - It uses TCP port 53 when the response is larger than 512 bytes and for zone transfers between DNS servers.
   - This is why DNS is the standard example of a protocol that uses both TCP and UDP on the same port number.
3. **HTTPS এর পোর্ট নাম্বার কত?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: HTTPS uses port number 443.

   - HTTP uses port 80 and HTTPS uses port 443 over TCP.
   - HTTPS is HTTP running inside a TLS encrypted session, which provides confidentiality, integrity and server authentication.
4. **Write the port address of the following applications of data communications. (i) HTTP; (ii) HTTPS; (iii) FTP; (iv) SMTP; (v) POP** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 671 (ET: N/A)]*


   Answer:

   | Application | Port |
   |---|---|
   | HTTP | 80 (TCP) |
   | HTTPS | 443 (TCP) |
   | FTP | 21 control, 20 data (TCP) |
   | SMTP | 25 (TCP), also 587 for submission |
   | Telnet | 23 (TCP) |
   | DNS | 53 (TCP and UDP) |
   | POP3 | 110 (TCP) |
   | IMAP | 143 (TCP) |
   | DHCP | 67 server, 68 client (UDP) |
   | SNMP | 161, and 162 for traps (UDP) |
5. **Describe TCP/IP protocols and its ports.** *[BDCCL Assistant Engineer (Network) 2022 compact it 742 (ET: N/A)]*


   Answer: The TCP/IP protocol suite is the four layer model on which the Internet runs.

   Application layer:
   - Provides services directly to the user and includes HTTP (80), HTTPS (443), FTP (21 and 20), SMTP (25), POP3 (110), IMAP (143), DNS (53), DHCP (67 and 68), SNMP (161), Telnet (23) and SSH (22).

   Transport layer:
   - TCP is connection oriented, reliable and ordered, using a three way handshake, sequence numbers, acknowledgements and flow control. It suits file transfer, email and web browsing.
   - UDP is connectionless and unreliable but has very low overhead, so it suits DNS queries, video streaming, VoIP and online gaming.
   - Both identify the application using a 16 bit port number, so 65,536 ports exist per protocol.

   Internet layer:
   - IP provides logical addressing and routing. Supporting protocols are ICMP for error reporting and ping, ARP for address resolution, and IGMP for multicast group management.

   Network access layer:
   - Handles the physical transmission and framing, for example Ethernet, Wi-Fi and PPP.

   - Port ranges: 0 to 1023 are well known, 1024 to 49151 are registered, and 49152 to 65535 are dynamic or private ports.
6. **A server has port number 1223. A user is requesting the server (www.example.com) but it is showing server is not reached. How can you solve this?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*


   Answer: The problem is that port 1223 is not the port a web browser uses by default.

   Reason:
   - A browser requesting `www.example.com` automatically connects to port 80 for HTTP or port 443 for HTTPS.
   - If the web service is actually listening on port 1223, the browser's request to port 80 finds nothing, so the connection is refused and the page does not load.

   Solutions:
   - Access the server by writing the port explicitly in the URL, for example `http://www.example.com:1223`.
   - Or configure the web server to listen on the standard port 80 or 443 instead.
   - Or put a reverse proxy in front, which listens on port 80 and forwards to 1223 internally.
   - Or configure port forwarding on the router so that traffic arriving on port 80 is redirected to 1223.

   Other points to check:
   - The firewall must allow inbound traffic on port 1223.
   - The DNS record for the domain must resolve to the correct IP address, which can be checked with `nslookup` or `ping`.
   - `telnet www.example.com 1223` confirms whether the port is actually reachable and open.

## Switching Techniques (Circuit vs Packet Switching) (5)

1. **Why is packet switching more suitable for internet communication?** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*


   Answer: Packet switching suits Internet communication because Internet traffic is bursty and the network must serve a very large number of users on shared links.

   - Efficient use of bandwidth: a link is occupied only when a packet is actually being sent, so many users share the same line through statistical multiplexing. Circuit switching would hold a line idle during the pauses in a web session.
   - No setup delay: a packet can be sent immediately, whereas circuit switching must first establish a path end to end.
   - Fault tolerance: if a router or link fails, later packets are simply routed along another path, so the session survives. In circuit switching the whole connection breaks.
   - Scalability: millions of simultaneous flows can share the backbone, since no resources are reserved per flow.
   - Cost: fewer physical resources are needed for the same number of users.
   - It also fits the store and forward model, allowing error checking at each hop.

   - The cost of this flexibility is variable delay and possible out of order arrival, which TCP handles at the transport layer.
2. **Difference between circuit switching and packet switching. Identify which of the two is predominantly used in Internet communication and justify why?** *[BUET Assistant Programmer 21.06.2025 compact it 1435 (ET: BUET)]*


   Answer:

   | Point | Circuit Switching | Packet Switching |
   |---|---|---|
   | Path | A dedicated physical path is set up before data flows | No dedicated path, each packet is routed independently |
   | Setup | Connection setup phase is required | No setup needed |
   | Bandwidth | Reserved for the whole session, wasted when idle | Shared, used only when data is actually sent |
   | Efficiency | Low for bursty data | High, links are statistically multiplexed |
   | Delay | Fixed after setup, so no jitter | Variable, packets may face queuing delay |
   | Reliability on failure | The whole call drops if a link fails | Packets simply take another route |
   | Order of arrival | Always in order | May arrive out of order and need reordering |
   | Example | Traditional telephone network | The Internet |

   - Packet switching is predominantly used in Internet communication, because Internet traffic is bursty and packet switching uses the shared bandwidth far more efficiently.
3. **(c) Compare circuit switching and packet switching.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1353 (ET: N/A)]*


   Answer:

   | Point | Circuit Switching | Packet Switching |
   |---|---|---|
   | Path | A dedicated physical path is set up before data flows | No dedicated path, each packet is routed independently |
   | Setup | Connection setup phase is required | No setup needed |
   | Bandwidth | Reserved for the whole session, wasted when idle | Shared, used only when data is actually sent |
   | Efficiency | Low for bursty data | High, links are statistically multiplexed |
   | Delay | Fixed after setup, so no jitter | Variable, packets may face queuing delay |
   | Reliability on failure | The whole call drops if a link fails | Packets simply take another route |
   | Order of arrival | Always in order | May arrive out of order and need reordering |
   | Example | Traditional telephone network | The Internet |
4. **Do you prefer packet switching compared to circuit switching in communication network? If Yes, why? How does packet switching work step by step? What applications use packet switching?** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 536 (ET: MIST)]*


   Answer: Yes, packet switching is preferred for a data communication network.

   Reasons:
   - Data traffic is bursty, so a reserved circuit would stay idle most of the time and waste bandwidth.
   - Many users can share the same link through statistical multiplexing, which lowers cost.
   - There is no connection setup delay before sending.
   - If a link fails, packets are rerouted automatically, so the network is resilient.

   How packet switching works:
   - The message is divided into small units called packets, each carrying a header with the source and destination address and a sequence number.
   - Each packet is forwarded independently, hop by hop, using the routing table at every router. This is the store and forward principle.
   - Because packets may take different routes, they can arrive out of order or with different delays.
   - The destination uses the sequence numbers to reorder the packets and reassemble the original message, and requests retransmission of anything missing.

   - Two modes exist: datagram, where every packet is routed independently as in IP, and virtual circuit, where a logical path is fixed first as in Frame Relay and ATM.
5. **Why is packet suiting suitable for digital data transmission?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 681 (ET: N/A)]*


   Answer: Packet switching suits digital data transmission for the following reasons.

   - Digital data is bursty rather than continuous, so reserving a fixed circuit would leave the line idle for long periods.
   - Bandwidth is shared dynamically, so the same physical link serves many users, which raises utilisation and lowers cost.
   - Store and forward at each node allows error checking on every hop, and a corrupted packet can be retransmitted alone instead of the whole message.
   - Different packets can take different routes, so congestion and link failure are handled automatically.
   - Speed and code conversion is possible, since sender and receiver need not operate at the same data rate.
   - Priority can be given to important packets, which is the basis of quality of service.

## WAN Technologies (SONET/SDH, ATM, WDM) (5)

1. **White short notes on: (i) SONET/SDH; (ii) IP telephony; (iii) WDM technology; (iv) ATM network** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*


   Answer:

   (i) SONET/SDH
   - SONET is the Synchronous Optical Network standard used in North America and SDH is the equivalent Synchronous Digital Hierarchy used elsewhere.
   - They carry multiple digital streams over optical fibre using synchronous time division multiplexing.
   - The base rate is STS-1 at 51.84 Mbps, and higher rates are exact multiples, for example OC-3 at 155.52 Mbps and OC-48 at 2.5 Gbps.
   - Ring topology with automatic protection switching gives recovery within 50 ms.

   (ii) IP telephony
   - Also called VoIP, it carries voice as IP packets over a data network instead of over a dedicated telephone circuit.
   - The voice is digitised, compressed by a codec such as G.729, packetised and sent using RTP over UDP.
   - Signalling is handled by SIP or H.323.
   - Advantages are much lower call cost and integration with data services; the challenge is maintaining quality of service.

   (iii) WDM technology
   - Wavelength Division Multiplexing sends several optical signals on one fibre by giving each a different wavelength, that is a different colour of light.
   - CWDM uses a few widely spaced channels, while DWDM packs 40 to 160 channels closely and is used in long haul backbones.
   - It multiplies the capacity of an existing fibre without laying new cable.

   (iv) ATM network
   - Asynchronous Transfer Mode is a connection oriented, cell based switching technology.
   - It uses a fixed cell of 53 bytes, made of a 5 byte header and 48 byte payload, which makes hardware switching fast and predictable.
   - It supports guaranteed quality of service classes such as CBR, VBR and ABR, so voice, video and data can share one network.
   - It has largely been replaced by IP over Ethernet and MPLS.
2. **(c) Explain IPTV and VOIP.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 794 (ET: N/A)]*


   Answer:

   IPTV, Internet Protocol Television:
   - Television content delivered over an IP network instead of by terrestrial, satellite or cable broadcast.
   - The video is encoded, compressed and streamed as IP packets, usually over a managed network rather than the open Internet.
   - Three main services: live television using multicast, video on demand using unicast, and time shifted television such as catch up TV.
   - Advantages: interactivity, personalised content, and use of the same infrastructure as Internet and telephone in a triple play package.

   VoIP, Voice over Internet Protocol:
   - Voice conversation carried as IP packets over a data network.
   - Steps: the analogue voice is sampled and digitised, compressed by a codec, packetised, and carried by RTP over UDP; SIP handles call setup and teardown.
   - Advantages: very low call cost especially for international calls, and easy integration with video and messaging.
   - Challenges: it needs quality of service control, because delay above 150 ms, jitter and packet loss noticeably degrade the call.
3. **Write the full form of the given technologies CX, IGW and IIG. Write feature of there technologies.** *[BTRC Assistant Director (Technical) 2021 compact it 806 (ET: IBA)]*


   Answer:

   Full forms:
   - CX — Carrier Exchange
   - IGW — International Gateway
   - IIG — International Internet Gateway

   Features:
   - IGW, International Gateway: it is the licensed gateway through which all international voice calls enter and leave the country. It handles call routing, billing and lawful interception, and connects national operators to foreign carriers.
   - IIG, International Internet Gateway: it is the gateway that carries international Internet data traffic. It connects the country's ISPs to the global Internet through submarine cable or terrestrial links, and provides bandwidth to ISPs.
   - CX, Carrier Exchange: it sits between the IGW operators and the mobile or fixed line operators, switching and routing calls between them so that every operator does not need a direct link with every IGW.

   - Together these form the licensed layered structure of international telecommunication in Bangladesh, regulated by BTRC. <!-- verify -->
4. **TSCM এর কাজ কী? VoIP পরিচালনায় কী কী সরঞ্জামের প্রয়োজন হয়?** *[BTRC Sub-Assistant Director (Technical) 2021 compact it 810 (ET: IBA)]*


   Answer:

   Work of TSCM:
   - TSCM stands for Technical Surveillance Counter Measures.
   - It is the process of detecting and neutralising hidden eavesdropping devices such as bugs, hidden microphones, hidden cameras and unauthorised wiretaps.
   - The work includes physical inspection of the premises, radio frequency spectrum analysis to find hidden transmitters, checking telephone and network lines for taps, and thermal or non-linear junction detection to find hidden electronics.
   - It is used to protect sensitive meeting rooms in government offices, banks and corporate houses. <!-- verify -->

   Equipment needed to run VoIP:
   - Broadband Internet connection with sufficient and stable bandwidth.
   - IP phone, or an ordinary analogue phone with an ATA (Analogue Telephone Adapter), or a softphone application on a computer or mobile.
   - Router and switch with quality of service support so that voice packets get priority.
   - VoIP gateway to connect the IP network with the traditional PSTN.
   - IP PBX or a SIP server to handle call setup, routing and extensions.
   - Headset or microphone, and an uninterrupted power supply since IP phones do not draw power from the telephone line.
5. **Write down the difference between IPoE and PPPoE.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 839-840 (ET: N/A)]*


   Answer:

   | Point | IPoE | PPPoE |
   |---|---|---|
   | Full form | Internet Protocol over Ethernet | Point to Point Protocol over Ethernet |
   | Authentication | No username or password; the device is identified by MAC address or option 82 | Username and password required at every connection |
   | IP assignment | Through DHCP | Negotiated during the PPP session |
   | Overhead | Lower, no extra PPP header | Higher, 8 bytes of PPP overhead so the usable MTU falls to 1492 |
   | Session concept | Sessionless, always on | Session based, established and torn down |
   | Configuration effort | Simpler for the user, plug and play | The user or router must store credentials |
   | Accounting | Harder, based on IP or MAC | Easy, per session accounting per subscriber |
   | Typical use | Modern fibre and IPTV deployments | Traditional DSL broadband |

   - PPPoE is preferred where per subscriber authentication and billing matter, while IPoE is simpler and more efficient for managed fibre networks.

## Pulse Code Modulation (PCM) & Signal Processing (4)

1. **A PCM system have step resolution of 2V. Sinusoidal signal amplitude 10V. SNR=? And total number of bits=?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)], [BTCL Assistant Manager (Technical) 2021 compact it 765 (ET: BUET)]*


   Answer:

   Given: step size Δ = 2 V, sinusoidal signal peak amplitude A = 10 V.

   Step 1: signal power
   - For a sinusoid, P_signal = A² / 2
   - P_signal = 10² / 2 = 50 W

   Step 2: quantization noise power
   - Formula: P_noise = Δ² / 12
   - P_noise = 2² / 12 = 4 / 12 = 0.3333 W

   Step 3: signal to noise ratio
   - SNR = P_signal / P_noise = 50 / 0.3333 = 150
   - In decibels: SNR(dB) = 10 log₁₀(150) = 21.76 dB

   Step 4: number of bits
   - Total signal swing is from −10 V to +10 V, that is 20 V.
   - Number of quantization levels L = 20 / 2 = 10
   - Bits required n = ⌈log₂ 10⌉ = ⌈3.32⌉ = 4 bits

   Final answer: SNR = 150, that is 21.76 dB, and 4 bits per sample are required.
2. **Draw Delta modulation figure and math. (Approximate)** *[NPCBL Executive Trainee (IT) 2022 compact it 648 (ET: BUET)]*


   Answer: Delta modulation encodes the difference between the current sample and the previous approximation using a single bit per sample.

   Working:
   - If the input signal is larger than the staircase approximation, a 1 is transmitted and the approximation is raised by one step size Δ.
   - If the input is smaller, a 0 is transmitted and the approximation is lowered by Δ.
   - So the output is a staircase that tries to follow the input waveform.

   ```text
   Amplitude
      ^            ____
      |        ___/    \___        <- input signal
      |    ___|            |___
      |   |  staircase approximation
      +---------------------------> time
   Bits: 1 1 1 1 0 0 1 0 0 0 1 1
   ```

   Two types of noise:
   - Slope overload distortion: when the input changes faster than the staircase can follow. The condition to avoid it is Δ · fs ≥ 2π · fm · Am.
   - Granular noise: when the input is almost constant, the staircase keeps oscillating up and down by one step, producing a small hunting noise. A smaller Δ reduces this but worsens slope overload.

   - Adaptive Delta Modulation solves the conflict by changing the step size according to the slope of the signal.
3. **A singla-tone message signal of bandwidth 4KHZ and amplitude 10V is transmitted by \Delta-modulation with step size 2V. Determine the data rate so that slope overloading noise is the minimum.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*


   Answer:

   Given: message bandwidth fm = 4 kHz, amplitude Am = 10 V, step size Δ = 2 V.

   Condition to avoid slope overload:
   - The staircase must be able to rise at least as fast as the steepest part of the signal.
   - Maximum slope of the message signal = 2π · fm · Am
   - Maximum slope of the staircase = Δ · fs
   - So the condition is Δ · fs ≥ 2π · fm · Am

   Step 1: maximum slope of the signal
   - 2π × 4000 × 10 = 251,327.4 volts per second

   Step 2: minimum sampling frequency
   - fs ≥ 251,327.4 / Δ = 251,327.4 / 2
   - fs ≥ 125,663.7 Hz

   Step 3: data rate
   - Delta modulation sends 1 bit per sample, so the data rate equals fs.
   - Data rate = 125,663.7 bits per second ≈ 125.66 kbps

   Final answer: the minimum data rate required so that slope overload noise is minimum is about 125.66 kbps.
4. **A single-tone message signal of bandwidth 4 KHZ is sampled by using a pulse train of frequency 200% higher than the Nyquist rate of the message signal to obtain PAM signal. The duty cycle of the pulse train is 20%. By drawing the amplitude spectrum of the PAM signal, determine its bandwidth.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 676 (ET: N/A)]*


   Answer:

   Given: message bandwidth fm = 4 kHz, sampling frequency 200 percent higher than the Nyquist rate, duty cycle 20 percent.

   Step 1: Nyquist rate
   - Nyquist rate = 2 × fm = 2 × 4 kHz = 8 kHz

   Step 2: actual sampling frequency
   - 200 percent higher means the Nyquist rate plus 200 percent of it.
   - fs = 8 + (2 × 8) = 24 kHz

   Step 3: pulse duration
   - Sampling period Ts = 1 / fs = 1 / 24,000 = 41.67 µs
   - Duty cycle is 20 percent, so pulse width τ = 0.2 × Ts = 8.33 µs

   Step 4: bandwidth of the PAM signal
   - The spectrum of a rectangular pulse train is a sinc envelope whose first null occurs at 1/τ.
   - BW = 1 / τ = 1 / 8.33 µs = 120,000 Hz

   Final answer: the bandwidth of the PAM signal is 120 kHz.

   - The amplitude spectrum consists of the message spectrum repeated at multiples of 24 kHz, with the amplitudes shaped by the sinc envelope that first crosses zero at 120 kHz.
   - Note that the narrower the pulse, the wider the required bandwidth.

## Network Layer (Packet Fragmentation & Tunneling) (4)

1. **(a) How do you define packet fragmentation? Explain briefly the transparent and non-transparent fragmentation with necessary diagram.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 481 (ET: N/A)]*


   Answer: Packet fragmentation is the process of dividing a datagram into smaller pieces when it is larger than the Maximum Transmission Unit (MTU) of the network it must cross.

   Why it is needed:
   - Different networks have different MTUs, for example Ethernet allows 1500 bytes while some WAN links allow far less.
   - A datagram larger than the MTU cannot be carried, so the router must either fragment it or discard it.

   Transparent fragmentation:
   - The router at the entry of the small MTU network fragments the packet, and the router at the exit reassembles it before passing it on.
   - So the fragmentation is invisible to the rest of the path, hence the name.
   - Advantage: subsequent networks see a normal sized packet.
   - Disadvantage: the exit router must buffer all fragments and wait for them, and every fragment must follow the same route.

   Non-transparent fragmentation:
   - The router fragments the packet but no intermediate router reassembles it. The fragments travel independently and only the final destination host reassembles them.
   - This is the method used by IPv4.
   - Advantage: routers stay simple and stateless, and fragments may follow different routes.
   - Disadvantage: header overhead is repeated for every fragment, and losing a single fragment forces the whole datagram to be discarded.

   - IPv4 uses the Identification, Flags and Fragment Offset fields for this. IPv6 does not allow routers to fragment; the source performs Path MTU Discovery instead.
2. **(b) Describe briefly the TCP/IP tunneling using appropriate diagram.** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 482 (ET: N/A)]*


   Answer: Tunneling is the technique of carrying a packet of one protocol inside the payload of another protocol, so that it can cross a network that would not otherwise support it.

   How it works:
   - The entry router encapsulates the original packet by adding a new outer header. This is the tunnel entry point.
   - The intermediate network forwards the packet based only on the outer header and does not examine the inner one.
   - The exit router removes the outer header and delivers the original packet. This is the tunnel exit point.

   ```mermaid
   flowchart LR
       A[Host A<br/>IPv6 network] --> B[Tunnel entry router<br/>encapsulate]
       B --> C[IPv4 Internet]
       C --> D[Tunnel exit router<br/>decapsulate]
       D --> E[Host B<br/>IPv6 network]
   ```

   Uses:
   - Connecting two IPv6 islands across an IPv4 Internet, which is the classic example.
   - Building a VPN, where an IP packet is encapsulated and encrypted inside another IP packet using IPsec or GRE.
   - Joining two branches of a private network over the public Internet.

   - The cost is extra header overhead and a reduced effective MTU, which can itself cause fragmentation.
3. **Why network need packet fragmentation? Define different types of packet fragmentation with necessary diagram.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 666 (ET: N/A)]*


   Answer: Fragmentation is needed because every physical network has its own Maximum Transmission Unit, and a datagram larger than that MTU cannot be carried in a single frame.

   Reasons in detail:
   - Ethernet has an MTU of 1500 bytes, but other links such as PPP or older WAN technologies allow much less.
   - A path may cross several networks with different MTUs, and the sender usually does not know the smallest one.
   - Without fragmentation the router would have to discard the packet, which would break end to end delivery.

   Types:
   - Transparent fragmentation, where the exit router of the small MTU network reassembles the fragments before forwarding them onward.
   - Non-transparent fragmentation, where reassembly is done only by the destination host. IPv4 uses this method.

   ```mermaid
   flowchart LR
       A[Original datagram<br/>4000 bytes] --> B[Router<br/>MTU = 1500]
       B --> C[Fragment 1<br/>offset 0]
       B --> D[Fragment 2<br/>offset 185]
       B --> E[Fragment 3<br/>offset 370]
       C --> F[Destination<br/>reassembles]
       D --> F
       E --> F
   ```

   - The Fragment Offset field is counted in units of 8 bytes, which is why every fragment except the last must carry a multiple of 8 bytes of data.
   - The More Fragments flag is 1 in every fragment except the last one.
4. **Suppose a 22-byte packet is to be transmitted through a network of \text{MTU} = 3\text{ byte}. The elementary fragment size is 1\text{ byte}. Show the segment numbering of the above packet. Packet number is 217.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*


   Answer:

   Given: packet size 22 bytes, MTU 3 bytes, elementary fragment size 1 byte, packet number 217.

   Step 1: number of fragments
   - Each fragment can carry at most 3 bytes of data.
   - Number of fragments = ceiling(22 / 3) = 8
   - Seven fragments carry 3 bytes each, that is 21 bytes, and the eighth carries the remaining 1 byte.

   Step 2: numbering of the fragments
   - Each fragment carries three fields: the packet number, the offset of its first byte measured in elementary units, and the End of Packet bit which is 0 for all but the last fragment.

   | Fragment | Bytes carried | Packet number | Offset | End bit |
   |---|---|---|---|---|
   | 1 | 1 to 3 | 217 | 0 | 0 |
   | 2 | 4 to 6 | 217 | 3 | 0 |
   | 3 | 7 to 9 | 217 | 6 | 0 |
   | 4 | 10 to 12 | 217 | 9 | 0 |
   | 5 | 13 to 15 | 217 | 12 | 0 |
   | 6 | 16 to 18 | 217 | 15 | 0 |
   | 7 | 19 to 21 | 217 | 18 | 0 |
   | 8 | 22 | 217 | 21 | 1 |

   Final answer: the packet is split into 8 fragments, numbered (217, 0, 0), (217, 3, 0), (217, 6, 0), (217, 9, 0), (217, 12, 0), (217, 15, 0), (217, 18, 0) and (217, 21, 1).

   - The destination uses the packet number 217 to group the fragments, the offset to place them in order, and the end bit to know that all fragments have arrived.

## Analog Modulation & Radio Receivers (3)

1. **With appropriate figures, distinguish between homodyne and heterodyne detection processes. Draw the block diagram of a super heterodyne AM receiver.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*


   Answer:

   Homodyne detection:
   - The incoming RF signal is mixed with a local oscillator running at exactly the same frequency as the carrier, so the signal is converted directly to baseband in one step.
   - It is also called direct conversion or zero IF.
   - Advantage: no intermediate frequency stage is needed, so the circuit is simple and cheap.
   - Disadvantage: it needs the local oscillator to be locked in both frequency and phase, and it suffers from DC offset and local oscillator leakage.

   Heterodyne detection:
   - The incoming RF signal is mixed with a local oscillator running at a different frequency, producing a fixed intermediate frequency, for example 455 kHz for AM radio and 10.7 MHz for FM.
   - Most of the amplification and filtering is done at this fixed IF, and only then is the signal demodulated.
   - Advantage: the IF filter can be sharp and fixed, so selectivity and sensitivity are much better across the whole tuning range.
   - Disadvantage: image frequency interference must be suppressed by an RF stage before the mixer.

   Block diagram of a superheterodyne receiver:

   ```mermaid
   flowchart LR
       A[Antenna] --> B[RF Amplifier and Tuner]
       B --> C[Mixer]
       D[Local Oscillator] --> C
       C --> E[IF Amplifier at fixed IF]
       E --> F[Detector / Demodulator]
       F --> G[Audio Amplifier]
       G --> H[Speaker]
   ```

   - The local oscillator and the RF tuner are ganged together so that the difference always stays equal to the IF.
2. **Difference between AM and FM. (a) Which is prefer for long distance communication? (b) Which has low distortion? (c) Which has low interference?** *[EGCB Assistant Engineer (CSE) 2022 compact it 716 (ET: BUET)]*


   Answer:

   | Point | AM | FM |
   |---|---|---|
   | What varies | Amplitude of the carrier | Frequency of the carrier |
   | Bandwidth | Narrow, about 10 kHz | Wide, about 200 kHz for broadcast |
   | Noise immunity | Poor, since noise adds to amplitude | Good, since amplitude changes are removed by a limiter |
   | Sound quality | Lower | Higher |
   | Frequency range | 535 to 1605 kHz | 88 to 108 MHz |
   | Coverage | Long distance via sky wave | Line of sight, shorter range |
   | Circuit complexity | Simple | More complex |

   - (a) Long distance communication: AM is preferred, because its lower frequency waves are reflected by the ionosphere and can travel far beyond the horizon.
   - (b) Low distortion: FM has lower distortion, giving it much better audio fidelity.
   - (c) Low interference: FM again, because the receiver uses a limiter that strips away amplitude variations caused by noise, and the capture effect suppresses the weaker of two signals.
3. **A sinusoidal modulating waveform of amplitude 5V and frequency of 2 kHz is applied to FM generator, which has a frequency sensitivity of 40Hz/volt. Calculate the frequency deviation, modulation index and bandwidth.** *[BOF Assistant Programmer 2022 compact it 734 (ET: MIST)]*


   Answer:

   Given: modulating amplitude Am = 5 V, modulating frequency fm = 2 kHz, frequency sensitivity kf = 40 Hz per volt.

   Step 1: frequency deviation
   - Formula: Δf = kf × Am
   - Δf = 40 × 5 = 200 Hz

   Step 2: modulation index
   - Formula: β = Δf / fm
   - β = 200 / 2000 = 0.1

   Step 3: bandwidth by Carson's rule
   - Formula: BW = 2(Δf + fm)
   - BW = 2(200 + 2000) = 2 × 2200 = 4400 Hz

   Final answer: frequency deviation = 200 Hz, modulation index = 0.1 and bandwidth = 4400 Hz, that is 4.4 kHz.

   - Since β is much less than 1, this is narrowband FM, and for narrowband FM the bandwidth is approximately 2fm, which is 4 kHz, close to the Carson value.

## Satellite Communication (3)

1. **(b) Difference between active and passive satellites.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 695 (ET: N/A)]*


   Answer:

   | Point | Passive satellite | Active satellite |
   |---|---|---|
   | Function | Only reflects the signal back to earth | Receives, amplifies, changes frequency and retransmits |
   | Onboard equipment | No transmitter or amplifier | Has a transponder with receiver, amplifier and transmitter |
   | Power source | None needed | Solar panels and batteries required |
   | Signal strength at receiver | Very weak, so huge earth stations are needed | Strong and usable |
   | Cost and complexity | Low | High |
   | Example | Echo 1, and the moon used as a reflector | Intelsat, Bangabandhu-1, all modern communication satellites |

   - Passive satellites are now obsolete because the reflected signal loses far too much power.
2. **(c) Briefly describe different types of earth orbital satellite.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (ICT) 13.09.2022 compact it 695 (ET: N/A)]*


   Answer: Satellites are classified by the height of their orbit above the earth.

   GEO, Geostationary Earth Orbit:
   - Altitude about 35,786 km above the equator, orbital period exactly 24 hours, so the satellite appears fixed in the sky.
   - Only three satellites can cover almost the whole earth.
   - Round trip delay is about 500 ms, which is noticeable in voice calls.
   - Used for television broadcast, weather monitoring and VSAT. Bangabandhu-1 is a GEO satellite.

   MEO, Medium Earth Orbit:
   - Altitude roughly 2,000 to 35,000 km, period 6 to 12 hours.
   - Fewer satellites are needed than LEO and the delay is moderate.
   - Used mainly for navigation, for example GPS at about 20,200 km.

   LEO, Low Earth Orbit:
   - Altitude roughly 160 to 2,000 km, period about 90 to 120 minutes.
   - Very low delay, so it suits real time communication, but a large constellation is required for continuous coverage.
   - Used by Iridium, Starlink and earth observation satellites.

   - HEO, Highly Elliptical Orbit, is used to give long coverage over high latitude regions that GEO cannot serve well.
3. **Satellite ভিত্তিক যোগাযোগের একটি অসুবিধা লিখুন।** *[DMLC Assistant Teacher (ICT) 2021 compact it 825 (ET: N/A)]*


   Answer: One major disadvantage of satellite based communication is the high propagation delay.

   - A geostationary satellite is about 35,786 km above the earth, so a signal takes roughly 250 ms to go up and come down, giving a round trip of about 500 ms.
   - This delay makes interactive applications such as voice calls, video conferencing and online gaming noticeably uncomfortable.
   - It also reduces the efficiency of TCP, because the protocol waits for acknowledgements.

   - Other disadvantages worth noting: very high launch and maintenance cost, signal attenuation during heavy rain which is called rain fade, limited bandwidth per transponder, and the fact that a satellite cannot be repaired once it is in orbit.

## Line Coding & Digital Encoding (2)

1. **Assume we want to transmit the following binary string: 01001110. Show the resulting signal on the one using the following line coding techniques: (i) NRZ-L (ii) Manchester NRZ (iii) Unipolar RZ (binary string: 11011000100)** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 638 (ET: N/A)]*


   Answer: Line coding converts a binary sequence into a digital signal. The three schemes are shown below for the given strings.

   (i) NRZ-L for 01001110
   - Rule: bit 0 is one voltage level and bit 1 is the opposite level, and the level is held for the whole bit period with no return to zero.
   - Taking 0 as positive and 1 as negative:

   ```text
   Bit    :  0    1    0    0    1    1    1    0
   Level  : +V   -V   +V   +V   -V   -V   -V   +V
            ▔▔▔┐    ┌▔▔▔▔▔▔▔┐            ┌▔▔▔
               └────┘       └────────────┘
   ```

   (ii) Manchester for 01001110
   - Rule: every bit period has a transition in the middle. A 0 is high to low and a 1 is low to high.
   - The mid-bit transition provides self synchronisation, which is the main advantage.

   ```text
   Bit    :  0     1     0     0     1     1     1     0
   Signal : ▔╲_   _╱▔   ▔╲_   ▔╲_   _╱▔   _╱▔   _╱▔   ▔╲_
   ```

   (iii) Unipolar RZ for 11011000100
   - Rule: bit 1 is a positive pulse for the first half of the bit period and returns to zero for the second half. Bit 0 stays at zero for the whole period.

   ```text
   Bit    : 1   1   0   1   1   0   0   0   1   0   0
   Signal : ▄   ▄   _   ▄   ▄   _   _   _   ▄   _   _
   ```

   - NRZ-L is simple but has a DC component and no self clocking.
   - Manchester has no DC component and is self clocking, but needs twice the bandwidth.
   - Unipolar RZ is easy to build but wastes power and still carries a DC component.
2. **What is Line coding? What is the different line coding techniques?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 869-870 (ET: N/A)]*


   Answer: Line coding is the process of converting binary data into a digital signal suitable for transmission over a physical medium.

   Purpose:
   - To match the signal to the characteristics of the channel.
   - To provide clock synchronisation between sender and receiver.
   - To remove or reduce the DC component, since transformers and capacitors in the path cannot pass DC.
   - To allow error detection in some schemes.

   Main categories and techniques:
   - Unipolar: only one polarity is used, for example Unipolar NRZ and Unipolar RZ. Simple but has a strong DC component.
   - Polar: two polarities are used, for example NRZ-L, NRZ-I, RZ, Manchester and Differential Manchester.
   - Bipolar: three levels are used, for example AMI (Alternate Mark Inversion) and Pseudoternary, which remove the DC component.
   - Multilevel: more than one bit is carried per signal element, for example 2B1Q and 8B6T, which increases the data rate.
   - Multitransition: for example MLT-3, used in 100BASE-TX Ethernet to reduce the required bandwidth.

   - NRZ-I encodes a 1 as a transition and a 0 as no transition.
   - AMI represents 0 as zero voltage and alternates the polarity for successive 1s, which keeps the average voltage at zero.

## Address Resolution (ARP & RARP) (2)

1. **(a) Discuss the main role of Address Resolution Protocol (ARP) in the network layer of TCP/IP protocol suite.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 490 (ET: N/A)]*


   Answer: ARP (Address Resolution Protocol) maps a known logical IP address to the corresponding physical MAC address on a local network. It works between the network layer and the data link layer of the TCP/IP suite.

   Why it is needed:
   - Data is routed using IP addresses, but the actual frame delivery on a LAN happens using MAC addresses.
   - So before sending a frame, a host must learn the MAC address that belongs to the destination IP.

   How it works:
   - The sender first checks its ARP cache. If the mapping is present, it is used directly.
   - If not, the sender broadcasts an ARP Request frame to the address FF:FF:FF:FF:FF:FF asking "who has this IP address".
   - Every host on the LAN receives it, but only the host owning that IP replies.
   - The owner sends a unicast ARP Reply containing its MAC address.
   - The sender stores the mapping in its ARP cache for a few minutes, so the process is not repeated for every packet.

   Related points:
   - If the destination is on another network, ARP resolves the MAC address of the default gateway instead.
   - RARP does the reverse, finding an IP address from a known MAC address, and has largely been replaced by BOOTP and DHCP.
   - ARP has no authentication, which makes ARP spoofing possible, so dynamic ARP inspection is used as a defence.
2. **What is ARP? Briefly explain ARP.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 841-842 (ET: N/A)]*


   Answer: ARP (Address Resolution Protocol) is the protocol that finds the MAC address corresponding to a known IP address within a local network.

   - Need: a router or host knows the destination IP address, but the Ethernet frame must carry a MAC address, so the two must be linked.
   - Request: the sender broadcasts an ARP Request asking which machine owns the given IP address.
   - Reply: only the machine that owns that IP responds with a unicast ARP Reply containing its MAC address.
   - Cache: the result is stored in the ARP table for a short time so that repeated broadcasts are avoided. The table can be viewed with the command `arp -a`.
   - If the destination lies outside the local network, ARP is used to obtain the MAC address of the default gateway instead.

## VLANs & Subnetting Comparison (2)

1. A large organization wants to isolate different departments and user groups within the same physical network to improve security, reduce broadcast traffic, and manage network resources efficiently. The network administrator is considering either subnetting or VLANs to achieve this isolation. Compare subnetting and VLANs in this scenario and determine which technique is more appropriate for logical network isolation, explaining how the selected technique improves security and traffic management. [BSCCPL AME 21-08-2026 (BUET)]


   Answer: VLAN (Virtual LAN) is the correct solution for this requirement.

   Why VLAN:
   - A VLAN divides one physical switch or network into several logical broadcast domains, so departments are isolated even though they share the same cabling and switches.
   - Traffic of one VLAN cannot reach another VLAN unless it passes through a router or a Layer 3 switch, where access control rules can be applied.
   - Users can be grouped by function rather than by physical location, so a user who moves desks stays in the same VLAN.

   Benefits:
   - Security: sensitive departments such as Accounts can be isolated from general staff.
   - Performance: broadcast traffic stays inside its own VLAN, which reduces unnecessary load.
   - Flexibility: adding or moving a user is a configuration change, not a re-cabling job.
   - Cost: one physical switch serves several logical networks, so fewer devices are needed.

   Implementation outline:
   - Create VLANs on the switch, for example VLAN 10 for Accounts, VLAN 20 for HR and VLAN 30 for IT.
   - Assign access ports to the correct VLAN and configure trunk ports carrying 802.1Q tags between switches.
   - Give each VLAN its own subnet and configure inter-VLAN routing on a router or Layer 3 switch, applying ACLs where isolation must be enforced.
2. **What is VLAN? Difference between static and dynamic VLAN.** *[RAKUB Assistant Network System Engineer 03.11.2023 compact it 550 (ET: BIBM)]*


   Answer: A VLAN (Virtual Local Area Network) is a logical grouping of devices into a single broadcast domain, independent of their physical location, created by configuration on a switch.

   | Point | Static VLAN | Dynamic VLAN |
   |---|---|---|
   | Assignment basis | Switch port number | Device MAC address, or user credentials |
   | Configuration | Manual, done by the administrator per port | Automatic, from a policy server such as VMPS or through 802.1X |
   | When a user moves | The new port must be reconfigured | The user keeps the same VLAN automatically |
   | Complexity | Simple to set up | Needs a central server and more setup effort |
   | Common name | Port based VLAN | MAC based or policy based VLAN |
   | Use | Small and medium fixed networks | Large networks with mobile users |

   - Static VLAN is the most widely used because of its simplicity and predictability.

## Spread Spectrum & Multiple Access (CDMA, FHSS, DSSS) (2)

1. **What are the limitaions of CDMA?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*


   Answer: Limitations of CDMA are the following.

   - Near-far problem: a user close to the base station drowns out a distant user, so strict and fast power control is essential.
   - Self jamming: since all users transmit on the same frequency at the same time, the signals of other users appear as background noise.
   - Capacity is soft limited: there is no hard channel count, but as more users join, the noise floor rises and the quality of every call degrades.
   - Complexity: the receiver needs a rake receiver and precise code synchronisation, which makes the hardware costlier.
   - Code management: a large set of orthogonal codes must be generated and distributed, and code planning is difficult.
   - Handset power consumption is higher because of continuous power control signalling.
2. **Mention the basic differences between frequency-hopped spread spectrum (FHSS) and direct sequence spread spectrum (DSSS) techniques.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 675 (ET: N/A)]*


   Answer:

   | Point | FHSS | DSSS |
   |---|---|---|
   | Technique | The carrier hops from one frequency to another following a pseudo-random pattern | The data bit is multiplied by a high rate pseudo-random chip sequence |
   | Bandwidth spreading | Achieved by using many narrow channels in turn | Achieved by widening each bit into many chips |
   | Resistance to narrowband interference | Very good, the signal simply hops away from the jammed band | Good, the interference is spread out during despreading |
   | Processing gain | Number of hopping channels | Chip rate divided by bit rate |
   | Power spectral density | Concentrated in one channel at a time | Very low and spread over the whole band |
   | Synchronisation | Hop timing must be synchronised | Chip sequence must be synchronised |
   | Data rate | Comparatively lower | Higher |
   | Example | Bluetooth | Wi-Fi 802.11b, GPS, CDMA |

## High Availability & Redundancy Protocols (VRRP, HSRP) (1)

1. **State the network protocol of VRRP?** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1359 (ET: BUET)]*


   Answer: VRRP stands for Virtual Router Redundancy Protocol. It is an open standard first-hop redundancy protocol defined in RFC 5798.

   - Purpose: it removes the single point of failure at the default gateway by letting several physical routers share one virtual IP address.
   - Working: one router is elected Master based on the highest priority and it forwards traffic for the virtual IP. The others stay as Backup.
   - The Master sends advertisement messages every second by default. If the Backup routers stop receiving them, the one with the highest priority takes over the virtual IP.
   - Hosts on the LAN keep pointing to the same virtual gateway address, so the failover is invisible to them.
   - It uses IP protocol number 112 and multicast address 224.0.0.18.
   - HSRP is the equivalent Cisco proprietary protocol, and GLBP additionally provides load balancing.
