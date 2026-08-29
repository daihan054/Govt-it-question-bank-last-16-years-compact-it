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

2. An organization has been assigned the IPv4 network address 192.168.1.0/24. As part of the network deployment, the network administrator is required to divide the address space into four equal-sized subnets to support different departments. Determine the Network Address, Subnet Mask (both CIDR and dotted-decimal notation). *[Officer (IT) 31 Jul 2026 bscs 01 (ET: N/A)]*

3. Subnetting logic requires precise binary calculation. A network engineer is tasked with dividing the internal network 192.168.10.0/24 into exactly 4 equal subnets for four different bank branches. Show the mathematical calculation to determine how many bits must be borrowed to create 4 subnets, and state the new Subnet Mask in both CIDR notation and decimal format. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

4. Network Address, Broadcast Address, Subnet Mask and Usable Host IP Range of: 10.0.0.0/30, 192.168.0.0/23, 172.16.1.0/24. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

5. (a) IP address এবং MAC/MU এর পার্থক্য লেখ।
   (b) Classfull এবং Classless IP address এর মধ্যে পার্থক্য লেখ।
   (c) 11000001 00001001 00001010 00010101 এই IP এর Class লিখ। *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

6. **A bank has the network block 192.168.10.0/24. The IT manager wants to divide this into 4 equal subnets.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*
(a) How many bits do you need to borrow to make 4 subnets?
(b) What is the new Subnet Mask in dotted-decimal format?
(c) Write down the Network Address, the First Usable IP, and the Broadcast Address for the second subnet created. Show your calculation.

7. **What is subnetting? For the network 192.168.1.0/22, how many usable host addresses does it have?** *[NPCBL Sub Assistant Engineer: Cyber Security Analyst Date: 11 July 2026 (ET: N/A)]*

8. **Given IP address 10.0.0.100 and Subnet mask 255.255.240.0 which is network address?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1449 (ET: N/A)]*

9. **Given IP address 10.10.0.0/16, you have divide the network into eight equal subnets. Find the subnet mask in dotted decimal and CIDR notation. Also find the first and last usable IP addresses of third subnet.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1362 (ET: BUET)], [DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*

10. **Subnet mask & Total host calculation.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

11. **Given the network 245.248.128.0/20, divide the address space among three departments as follows:**
   **(a) Manager: half of the address space.**
   **(b) HR: one-quarter of the address space.**
   **(c) Admin: the remaining one-quarter.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1437 (ET: BUET)]*

   **For each department, determine:**
   **(i) The network block (in CIDR notation).**
   **(ii) The IP address valid range.**
   **(iii) The number of valid hosts.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1438 (ET: BUET)]*

12. **Find out the network address and Broadcast address of the address: 192.168.0.0/28** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1360 (ET: BUET)]*

13. **(a) An organization wants to divide its LAN IP address 192.168.0.0/24 into 4 subnets according to buildings. The buildings IP address creiteria are given below.**

| Building block | Hosts need |
|---|---|
| A | 110 |
| B | 50 |
| C | 20 |
| D | 8 |

**Calculate the network and broadcast address of this network for each building block.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1443 (ET: N/A)]*

14. **Check the valid IP address from the following table.** *[BREB Assistant Programmer (AP) 21.02.2025 compact it 1335 (ET: N/A)]*

15. **(a) A network has been assigned the IP address 200.1.2.0/24. It has 3 subnets. Determine the following for each subnet:** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1352 (ET: N/A)]*
 * **(i) Total number of IP addresses**
 * **(ii) Range of usable IP addresses**
 * **(iii) Network address**
 * **(iv) Direct broadcast address**
 * **(v) Limited broadcast address.**

16. **The IP address of a device in a network is 172.16.128.123/22. Answer the following questions:** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1343 (ET: N/A)]*
   * **i) What is the network address?**
   * **ii) What is the subnet mask for the given network?**
   * **iii) What is the broadcast address?**
   * **iv) What is the maximum number of devices this network can connect?**
   * **v) What is the IP address of the first host device in the network?**

17. **Find the network address, subnet mask, broadcast address, and usable host IP range for the following IP address: 192.9.205.31/16.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1339 (ET: N/A)]*

18. **What is the CIDR Prefixes exactly represents the range of IP addresses 10.12.2.0 to 10.12.3.255?** *[BCIC Assistant Programmer 14.02.2025 compact it 1328 (ET: BUET)]*

19. **Write down the private IP address rang for class B?** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*

20. **Given IP address 192.168.0.0/28, determine Network address, Broadcast address, First usable IP, Last usable IP.** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*

21. **Write range of private IP address Class A, B and C.** *[BCC Assistant Network Engineer 18.10.2025 compact it 1441 (ET: BCC)]*

22. **Given an IP address 192.168.111.169/28. Then Determine the (i) Network address (ii) Broadcast address (iii) First usable Host (iv) Last usable Host.** *[BBA Assistant Maintenance Engineer 12.07.2025 compact it 1431 (ET: BUET)]*

23. **What are the private IP Ranges for the following IP classes? Class A, Class B and Class C** *[BBA Assistant Maintenance Engineer 12.07.2025 compact it 1431 (ET: BUET)]*

24. **Which is Class C Default Subnet Mask?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

25. **What is the maximum number of valid hosts in a network?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

26. **Given IP address 10.2.3.20/22 find the Total valid Host address in this IP?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

27. **Mapping between MAC to IP address?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

28. **How many bits are in a MAC address?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

29. **What is the primary motivation for classful IP address to classless IP addressing?** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 316 (ET: N/A)]*

30. **Given IP address 192.168.1.50, Subnet Mask: 255.255.255.240. Find the valid IP range. Also find Network address and Broadcast address.** *[NWPGCL Assistant Manager (ICT) 12.01.2024 compact it 292 (ET: BUET)], [BTCL Assistant Manager (Technical) 2023 compact it 594 (ET: BUET)], [BPDB Assistant Engineer (CSE) 10.05.2024 compact it 389 (ET: BUET)], [BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 456 (ET: BUET)]*

31. **Given IP Address: 192.168.5.154/27, Calculate a) Network Address b) First valid host c) Last valid host d) Broadcast address e) Subnet mask** *[NSDA Assistant Maintenance Engineer 11.05.2024 compact it 383 (ET: N/A)]*

32. **Write down the Public and Private IPv4 address for Class A, Class B and Class C.** *[NSDA Assistant Maintenance Engineer 11.05.2024 compact it 384 (ET: N/A)]*

33. **(b) What is a subnet? What benefits will you get using subnets for this office?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 324 (ET: BIBM)]*

34. **Local loopback address কি? কোন কমান্ড ব্যবহার করে কানেক্টিভিটি টেস্ট করা হয়?** *[BTCL - JAM ( Technical) 05.04.2024 compact it 383 (ET: BUET)]*

35. **Given IP address 192.168. 2.0/ 24; Determine to network address and broadcast address.** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 405 (ET: N/A)]*

36. **Given a (slash) /26 based network address. Find Subnet mask, broadcast address, number of host, Number of valid host and number of subnet.** *[BKSP Assistant Programmer 13.07.2024 compact it 1459 (ET: N/A)]*

37. **Write Class A private IP range.** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

38. **Write Command for check LAN connecte?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

39. **(a) Given 4 Network interface in a table and find which of the following network is on which network.** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 433 (ET: BUET)]*

40. **(খ) Classful এবং Classless IP address এর পার্থক্য কী? নিচের IP গুলোর Class নির্ণয় করুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*
i) 00000001 00001011 00001011 11101111
ii) 211.10.15.4

41. **6.10 An organization is granted the IPv4 network block 14.24.74.0/24 and needs to segment it into two subnets: Subnet A (requires 120 addresses) and Subnet B (requires 60 addresses). Allocating sequentially from the requirement first to maximize remaining address space, state only the Network Address (with its CIDR mask) and the Broadcast Address for both subnets.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

42. **An IP address subnet mask is 255.255.255.224 which is the subnet address in this block?** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*

43. **Write down the basic differences of the following:**
   **(i) Public vs Private IP address** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 534 (ET: MIST)]*

44. **What do you mean by Subnet and Subnet Mask? The network address of 172.16.0.0/19 provides how many subnets and hosts? What is the function of OSPF?** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 536 (ET: MIST)]*

45. **Convert the decimal IP address 192.168.101.5 into binary IP address. Fill-up the following in tabular form:** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 539 (ET: MIST)]*
| Address Class | First Octet Decimal Range | Example of IP Address (IPA) | Network ID of IPA | Host ID of IPA |
|---|---|---|---|---|
| Class A |  |  |  |  |
| Class B |  |  |  |  |
| Class C |  |  |  |  |

46. **What is IP address? Explain the necessity of IP address in network?** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 564 (ET: N/A)]*

47. **What is subnet mask? Why it is used?** *[Mongla Port Authority Assistant Programmer 2023 compact it 573 (ET: N/A)]*

48. **In HR department have 12 IP enable devices are available in our office and have a big IP block 172.16.5.0/24. To consider your HR department find a suitable IP block than also answer the following question.**
   **i. Subnet mask; ii. Number of usable IP address; iii. First and last IP Address of that block iv. Broadcast IP address** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 596 (ET: N/A)]*

49. **What is private IP range class A, B and C with maximum host of each class?** *[BREB Assistant Programmer 18.02.2023 compact it 470 (ET: N/A)]*

50. **(b) Find out the default mask, network address and broadcast address of the classful IPv4 address: 172.16.99.45** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 480 (ET: N/A)]*

51. **Identify the class, network IP address, direct broadcast address and limited broadcast address of the following IP address: (i) 1.2.3.4 (ii) 130.1.2.3 (iii) 220.15.1.10 (iv) 200.1.10.100** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 637 (ET: N/A)]*

52. **What is the subnet mask in 10.2.1.3/22 network?** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 637 (ET: N/A)]*

53. **In IPv4 show the network address and host address range of class A, B and C.** *[NSDA Assistant Programmer Date: 04-03-2022 compact it 656 (ET: N/A)]*

54. **Given IP Address: 192.168.5.154/26, Calculate network address and subnet mask.** *[NSDA Assistant Programmer Date: 04-03-2022 compact it 657 (ET: N/A)]*

55. **Mention the maximum number of networks and hosts used in Class A, B and C networks.** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 659 (ET: N/A)]*

56. **Which subnet mask would be appropriate for address range to submit for up to LANs, with each LAN contains 5 to 26 hosts?** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 659 (ET: N/A)]*

57. **Given IP Address: 192.168.19.24/29, find out the following IP Class & type, Number of Host, Network address, Broadcast address, Wildcard, and Subnet mask.** *[NSDA Assistant Maintenance Engineer Date: 04-03-2022 compact it 659 (ET: N/A)]*

58. **Find network address, subnet mask, broadcast address and IP host range of 192.168.100.128/26** *[GTCL Assistant Engineer (CSE) 2022 compact it 685 (ET: BUET)]*

59. **What is the range of IPv4 address class A, B and C?** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 699 (ET: BUET)]*

60. **What is subnet mask? Given IP address 192.168.0.0/29 find 10^{\text{th}} and 22^{\text{th}} subnet first host address and last host address.** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 701 (ET: BUET)]*

61. **How many bits need to identify an IP address in IPv4?** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*

62. **What is default subnet mask?** *[BARC Data Entry Officer 10.09.2022 compact it 702 (ET: N/A)]*

63. **Given IP: 168.20.96.63, Subnet mask: 255.255.192.0 Find network address, broadcast address and number of host.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 712 (ET: BUET)]*

64. **An IP address is: 172.162.100.25/27, Find out the following: (a) Network Address (b) IP class (c) Subnet mask (d) Broadcast address (e) Hosts per subnet** *[IDRA Assistant Network Administrator 2022 compact it 727 (ET: N/A)]*

65. **What is Public and Private IP?** *[IDRA Assistant Network Administrator 2022 compact it 728 (ET: N/A)]*

66. **A network IP address is 172.16.236.92/27. Find out the: (a) Subnet mask (b) Network Address (c) Broadcast Address** *[NWPGCL Junior Assistant Manager (IT) 2022 compact it 731 (ET: N/A)]*

67. **Given IP address 172.3.16.156/23 and find out the following answer: (i) Network address (ii) Subnet mask (iii) Number of host** *[BOF Assistant Programmer 2022 compact it 733 (ET: MIST)]*

68. **Answer the following: (i) 192.168.10.0/23, How many usable address? (ii) 192.168.10.0/23, Find subnet mask. (iii) 192.168.10.0/23, Find Broadcast Address. (iv) 192.168.10.0/23, What is last usable host?** *[BTCL Assistant Manager (Technical) 2021 compact it 764 (ET: BUET)]*

69. **(ii) CIDR কী? 192.168.100.9/26 IP address থেকে (a) Total subnets (b) Block size (c) Valid Hosts (d) Total hosts বের করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 788 (ET: N/A)]*

70. **(a) What is the usable number of host IP addresses available on a network that has a /26 mask? Write down the subset mask of this network. Write down the first and the last IP address that can be assigned to host PCs if the network address is 192.168.30.128/26. What address should be used for broadcast purpose in this Network?** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 801-802 (ET: N/A)]*

71. **Answer the following: (i) 192.168.10.2/28, Find subnet mask. (ii) 192.168.10.2/28, Find Network Address. (iii) 192.168.10.2/28, Find IP Address of the first host? (iv) 192.168.10.2/28, Find IP Address of the last host? (v) 192.168.10.2/28, Find Broadcast Address.** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

72. **Select the correct answer: (i) Which cannot IP address 172.16.28.0/16- (a) .0 (b) .1 (c) .255 (d) All (ii) Which at the follow Dynamically Assign Protocol? (a) DHCP (b) ARP (c) ICMP (d) TCP (iii) Which one is Private IP address? (a) 10.10.10.10 (b) 172.172.172.172 (c) 192.192.192.192 (d) All (iv) SSH Protocol port number is _____. (v) Which is the name of Symmetric key encryption algorithm? (a) AES (b) 3DES (c) Re4 (d) None** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 824 (ET: BUET)]*

73. **A network address is given 172.18.10.0/23, divide this network address into 4 subnets and find every subnet address, start address, subnet mask, broadcast address etc.** *[RAKUB Network System Engineer (PO) 10.10.2021 compact it 843-844 (ET: N/A)]*

74. **A network address is given 172.168.0.0/28, divide this network address into 4 subnets and find every subnet address, start address, subnet mask, broadcast address etc.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 856 (ET: N/A)]*

75. **In a “Class A” network total 20 subnets are needed with maximum 260 hosts per subnets. Can 255.255.255.0 subnet mask be used in this?** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 862 (ET: BUET)]*

76. **Find Network address, Valid Host, Subnet mask and Broadcast address from 172.16.128.120/25.** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 867 (ET: BUET)]*

77. **What is the range of class C IPv4 address? Suppose, Class C network has four subnets. How many usable PC needed each subnet?** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 875-876 (ET: BUET)]*

78. **(a) What is the subnet mask of 10.2.1.3/26 and What is the usable number of IP address on network that has a 26 mask?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 886 (ET: N/A)]*

79. **172.168.128.0/20 এর Broadcast Address বের কর এবং কতগুলো Computer (Host) Connect করা যাবে?** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 913 (ET: BUET)]*

80. **Suppose a network with IP address 192.16.0.0 is divided into 2 subnets, find number of hosts per subnet. Also for the first subnet, find- (i) First Subnet address (ii) First host address (iii) Last host address (iv) Broadcast address** *[BAUST Assistant Programmer 2021 compact it 919 (ET: N/A)]*

81. **Find the Subnet mask from the following IP: 192.168.3.0/22** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922 (ET: N/A)]*

82. **VLSM Subnetting. Given an IP address, 192.168.0.0/20 For creating 4 subnets department of A, B, C, D with 2000, 1000, 6000 and 8000 hosts, find out every department first and last IP address. Also write the subnet mask of q.x.y.z/notation.** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 927 (ET: CTI)]*

83. **You are given a IP address 172.16.20.0/25 have four subnets. For each department find the following information. (CSE, EEE, IPE, PME)** *[NRCC Assistant Programmer 2021 compact it 931 (ET: N/A)]*

84. **Define IP 127.0.0.1, what is localhost?** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 932 (ET: BUET)]*

85. **What is static IP Address and dynamic IP Address?** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 932 (ET: BUET)]*

86. **Using the IP address 192.168.10.0/23 find out- (i) Subnet/First address (ii) Last Address (iii) Subnet mask** *[SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)]*

87. **Consider the IP address 10.20.30.0/25 now answer the below question: (i) What is the subnet mask of the above IP address? (ii) How many host per subnet have? (iii) What is the Broadcast address of this 10.20.30.0/3 IP address?** *[Janata Bank Assistant System Administrator 2021 compact it 938 (ET: N/A)]*

88. **২. 192.168.10.0/28 এর জন্য সাবনেট মাস্ক হবে কোনটি?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

89. **৯. ক্লাস C এর ডিফল্ট সাবনেট মাস্ক কত?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

90. **১১. নিচের কোনটি লুপ ব্যাক আইপি এড্রেস?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

91. **A IP Address is: 172.16.128.120/25 now answers the following questions: (i) What is the network address of this IP? (ii) What is the subnet mask? (iii) What is the broadcast address? (iv) How many connection is possible in this network?** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 975 (ET: BUET)]*

92. **(a) A IP address is 172.20.0.0/27. How many subnets and hosts per subnet?** *[National University Assistant Programmer 2020 compact it 977 (ET: DU)]*

93. **Given IP address 172.16.128.120/25 what is the subnet mask, network address, broadcast address and total usable host in this network?** *[NACTAR Assistant Instructor (ICT) 2020 compact it 991 (ET: N/A)]*

94. **Given IP address is 172.168.10.0/24, administrator wants to create 32 subnets, then find out sub netmask, number of address of each subnet, first and last address of subnet 1, first and last address of subnet 32.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1012 (ET: DU)]*

95. **Given IP Address 180.79.35.5/24, Find the (i) Network address (ii) Broadcast address (iii) Subnet mask (iv) Total valid host (v) IP address class** *[PGCB Sub-Assistant Engineer (CSE) 2020 compact it 1043 (ET: BUET)]*

## OSI & TCP/IP Reference Model (43)

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

## Networking Fundamentals & Terminology (23)

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

## Application Layer Protocols & Troubleshooting (DNS, DHCP, HTTPS) (19)

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

## Wireless Networks & IoT (mmWave) (17)

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
   - Router: a layer 3 device that connects different networks. It reads the destination IP address, looks it up in the routing table, and forwards the packet to the best next hop. It blocks broadcasts, so each interface is a separate broadcast domain, and it also provides NAT, DHCP, ACLs and WAN connectivity.
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


   Answer: Data transmission-e Router ebong Gateway duitar bhumika alada, tai kon ta beshi shubidhajonok seta nirbhor kore ki dhoroner network jog kora hocche tar upor.

   | Bishoy | Router | Gateway |
   |---|---|---|
   | Kaj | Ek IP network theke aar ek IP network-e packet forward kora | Bhinno protocol ba format-er duti network-er modhye translate kora |
   | Layer | Network layer, layer 3 | Je kono layer, prayoshoi application layer |
   | Speed | Onek druto, hardware forwarding | Dheere, karon puro message rupantor korte hoy |
   | Cost | Kom | Beshi |
   | Example | LAN theke Internet-e traffic pathano | VoIP theke PSTN, IoT Zigbee theke TCP/IP |

   Motamot:
   - Jodi duti network-i same protocol, mane TCP/IP byabohar kore, tahole Router-i beshi shubidhajonok: eta druto, shosta, scalable, ar routing protocol diye best path nijei ber kore.
   - Jodi duti network-er protocol ba data format alada hoy, tahole Router kichui korte parbe na, tokhon Gateway-i ekmatro somadhan.
   - Ajker Internet praytoi puropuri TCP/IP bhittik, tai bastobe beshirbhag khetre Router-i beshi byabohar hoy, ar Gateway lage bishesh khetre.
   - Practical bhabe duitai ek device-e thake: ekti home router-i default gateway, NAT ar firewall-er kaj kore.
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

   Router-er function:
   - Layer 3, mane network layer-e kaj kore ebong duti ba tar beshi bhinno network-ke jukto kore.
   - Packet-er destination IP address dekhe routing table-e longest prefix match kore best next hop nirbachon kore.
   - Static route ba RIP, OSPF, BGP-er moto routing protocol diye routing table toiri ar update kore.
   - Protita hop-e TTL komay, dorkar hole packet fragment kore, ar layer 2 header notun kore lekhe.
   - Broadcast block kore, tai protita interface ekti alada broadcast domain toiri kore.
   - Ei sathe NAT, DHCP server, ACL diye filtering, QoS ar WAN connectivity dey.

   Gateway-er function:
   - Bhinno protocol, architecture ba data format-er duti network-ke jukto kore ebong tader modhye translate kore.
   - OSI-r je kono layer-e, emonki application layer porjonto kaj korte pare, karon puro message-er format bodlate hote pare.
   - Network-er entry ba exit point hisebe kaj kore; LAN-er host-ra nijer subnet-er baire jete default gateway byabohar kore.
   - Example: VoIP gateway IP call-ke PSTN call-e rupantor kore, email gateway duti mail system-er modhye onubad kore, IoT gateway Zigbee sensor data-ke TCP/IP-te ane.
   - Prayoshoi security ar protocol conversion ekshathe kore, jemon ekti API gateway.
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
   - Wi-Fi Access Point holo emon ekti networking device ja wireless client-der, jemon laptop ba mobile, wired LAN-er sathe jukto kore. Eta radio signal ke Ethernet frame-e ebong ulto dike rupantor kore.
   - Eta layer 2-e kaj kore ar mulot ekti wireless bridge; IEEE 802.11 standard mene CSMA/CA diye medium access niyontron kore.
   - Protita AP ekti SSID broadcast kore, client authenticate ar associate hoy, ebong WPA2 ba WPA3 diye encryption hoy.
   - Ekti AP-r coverage area ke bola hoy BSS; ekadhik AP mile ekti ESS toiri kore, jekhane client ek AP theke onno AP-te roam korte pare.
   - Home router-e AP, switch ar router — tinti kaj ek boxe thake, kintu enterprise-e AP alada device ebong ekti WLAN controller diye niyontrito hoy.

   Router ar Switch-er parthokko:

   | Bishoy | Router | Switch |
   |---|---|---|
   | Layer | Network layer, layer 3 | Data link layer, layer 2 |
   | Address | IP address | MAC address |
   | Kaj | Bhinno network-er modhye packet forward kora | Ek LAN-er bhitor frame forward kora |
   | Table | Routing table | MAC address table |
   | Broadcast | Block kore, protita interface alada broadcast domain | Forward kore, shob port ek broadcast domain |
   | Port songkha | Kom, 2 theke 8 | Beshi, 8 theke 48 ba tar beshi |
   | Baroti feature | NAT, DHCP, ACL, firewall, WAN link | VLAN, STP, port security, link aggregation |
   | Speed ar dam | Tulonamulok dheere ar dami | Druto ar kom dami |
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

   - Sonkhipto kotha: Hub kichu bujhe na, shudhu signal repeat kore; Switch MAC address dekhe thik port-e frame pathay; ar Router IP address dekhe ek network theke onno network-e packet pathay.
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

   | Bishoy | Simplex | Half duplex | Full duplex |
   |---|---|---|---|
   | Direction | Ek dike matro | Duidike, kintu ekbare ek dike | Duidike ekshathe |
   | Channel capacity | Purota ek dike | Purota, kintu palakrome | Duidike bhag kore, ba duti alada channel |
   | Turnaround delay | Prayojon nei | Ache | Nei |
   | Performance | Shob theke kom nomonio | Moddhom | Shob theke bhalo |
   | Cost | Shob theke kom | Moddhom | Shob theke beshi |
   | Udahoron | Keyboard theke computer, monitor, radio o TV broadcast | Walkie-talkie, CB radio, hub bhittik Ethernet | Telephone, mobile call, switched Ethernet |

   - Simplex-e receiver kokhono uttor dite pare na, tai eta shudhu one-way broadcast-er jonno.
   - Half duplex-e ek pokkho sesh na kora porjonto onno pokkho opekkha kore, tai shared medium-e CSMA/CD lage.
   - Full duplex-e duti alada path ba echo cancellation byabohar kore ekshathe pathano o grohon kora jay, tai throughput dwigun hote pare.
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


   Answer: Data Communication System-er panchti prodhan component:

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

   - Ei panchti-r modhye ekti-o na thakle jogajog somvob noy: message na thakle pathanor kichu nei, sender ba receiver na thakle prante keu nei, medium na thakle path nei, ar protocol na thakle duti device eke oporer bhasha bujhbe na.
11. **(খ) Data Communication কত প্রকার? উদাহরণসহ সংক্ষিপ্ত বর্ণনা দিন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 704 (ET: N/A)]*


   Answer: Data communication ke sadharonoto duti drishtikon theke bhag kora hoy.

   Data flow-er dik onujayi tin prokar:
   - Simplex: shudhu ek dike data jay. Udahoron: keyboard theke computer, computer theke monitor, radio o TV broadcast.
   - Half duplex: duidike jay kintu ekbare ek dike. Udahoron: walkie-talkie, CB radio, hub bhittik Ethernet.
   - Full duplex: duidike ekshathe jay. Udahoron: telephone, mobile call, switched Ethernet.

   Signal-er dhoron onujayi dui prokar:
   - Analog data communication: signal ekaditkrome poriborton hoy, jemon purono telephone line ba AM/FM radio.
   - Digital data communication: signal discrete 0 ar 1 hisebe jay, jemon computer network. Eta noise-er birudhdhe onek beshi shokto, karon repeater signal ke notun kore toiri korte pare.

   Synchronization-er dhoron onujayi dui prokar:
   - Asynchronous: ek ekti character alada kore, start ar stop bit shoho pathano hoy. Udahoron: RS-232 serial port.
   - Synchronous: ekti boro block ekshathe, common clock diye pathano hoy. Udahoron: Ethernet, SONET.
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

## Data Rate & Channel Capacity (Nyquist, Shannon) (14)

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
   - Bus: all nodes share one backbone cable with terminators at both ends.
   - Ring: nodes form a closed loop, data travels in one direction, often with token passing.
   - Star: every node connects to a central hub or switch.
   - Mesh: every node connects to every other node, needing n(n − 1)/2 links.
   - Tree or hierarchical: several star networks joined to a common backbone.
   - Hybrid: any combination of the above, for example a star-bus or star-ring, which is what most real campus networks are.
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


   Answer: n-ti device-er jonno link songkha:

   | Topology | Number of links | Reason |
   |---|---|---|
   | Bus | n links to the backbone, plus 1 backbone cable | Each device needs one drop cable onto the shared backbone |
   | Mesh | n(n − 1)/2 for duplex links, or n(n − 1) for simplex | Every device connects to every other device, and each pair is counted once |
   | Star | n | Each device has exactly one cable to the central hub |

   - Mesh-e protita device-er port lage n − 1 ti, Star-e lage 1 ti, ar Bus-e 1 ti.
   - Example, n = 5: Bus needs 5 drops, Mesh needs 5 × 4 / 2 = 10 links, Star needs 5 links.
   - Ei karone Mesh-e cabling cost n²-er sathe bare, jar jonno full mesh shudhu choto ba khub critical network-e byabohar kora hoy.
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


   Answer: IP address holo ekti network layer identifier, jeta Internet ba kono network-e juktho protita device-ke unique bhabe chinte ebong tar kache packet pathate byabohar kora hoy. Eta duti ongsho niye toiri: network part ar host part.

   Four main differences between IPv4 and IPv6:

   | Point | IPv4 | IPv6 |
   |---|---|---|
   | Address length | 32 bits, dotted decimal, 192.168.10.1 | 128 bits, hexadecimal with colons, 2001:0db8::1 |
   | Header | Variable 20 to 60 bytes with a checksum | Fixed 40 bytes, no checksum, extension headers |
   | Configuration and NAT | Manual or DHCP, NAT needed because addresses are scarce | SLAAC or DHCPv6, no NAT needed |
   | Broadcast and security | Broadcast exists, IPsec optional | No broadcast, multicast instead, IPsec built in |
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


   Answer: IPv6 address 128 bit-er. Eta 8-ti group-e bhag kora, protita group 4-ti hexadecimal digit, colon diye alada kora, jemon 2001:0db8:85a3:0000:0000:8a2e:0370:7334.

   - Prothom 64 bit sadharonoto network prefix ar shesh 64 bit interface identifier.
   - IPv4 chilo 32 bit, tai IPv6-e address songkha 2⁹⁶ gun beshi.
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


   Answer: Optical Fibre cable-e aalor pulse byabohar kora hoy.

   - Ekhane data 0 ar 1 hisebe LED ba laser diode theke aalor pulse akare pathano hoy.
   - Aalo core-er bhitor Total Internal Reflection-er madhome cholte thake ebong opor prante photodiode take abar electrical signal-e rupantorito kore.

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


   Answer: DHCP is the Dynamic Host Configuration Protocol, which automatically supplies the IP address, subnet mask, default gateway and DNS server address to a host, so that no manual configuration is needed. It runs over UDP, port 67 on the server and 68 on the client.

   How it works, the DORA process:
   - DHCPDISCOVER: the new client has no address, so it broadcasts a discover message from 0.0.0.0 to 255.255.255.255 to find any DHCP server on the link.
   - DHCPOFFER: every server that receives it reserves a free address from its pool and offers it back, together with the mask, the gateway, the DNS servers and the lease time.
   - DHCPREQUEST: the client accepts one offer and broadcasts its choice, so the remaining servers release the addresses they had reserved.
   - DHCPACK: the chosen server confirms the assignment and the lease period begins. If the address has meanwhile been taken, the server replies DHCPNAK and the client restarts.

   Lease management:
   - At 50 percent of the lease, called T1, the client unicasts a renewal request to the same server.
   - At 87.5 percent, called T2, if there was no reply, it broadcasts a rebind request to any server.
   - If the lease expires the client gives up the address and starts from DHCPDISCOVER again.
   - DHCPRELEASE is sent when the client shuts down, returning the address to the pool.
   - If the server is on another subnet, a DHCP relay agent configured on the router forwards the broadcast to the server as a unicast.

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
