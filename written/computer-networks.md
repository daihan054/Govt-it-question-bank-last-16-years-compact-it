## Physical Layer & Transmission Media (Cables & Wiring)

1. **Straight through connection vs Crossover connection.** **(National Legal Aid Services Organization - Assistant Maintenance Engineer Exam: 18.10.2025) [compact it 1448]**

2. **Which transmission medium is used in LAN? Write their maximum length and capacity (bps).** **(DPDC - Assistant Engineer (CSE) Exam: 17.10.2025) [compact it 1452]**

## Physical Layer & Optical Fiber (Attenuation & Power Budget)

1. **A fiber optic network is designed using single-mode fiber with an attenuation of 0.35 dB/km. The network includes a splitter with a 14 dB loss as specified in the datasheet. Additionally, there are two mechanical splices (each with 0.1 dB loss) and two connectors (each with 0.75 dB loss). Given the following parameters:**
   * **Transmitter Power: 5 dBm**
   * **Receiver Sensitivity: -14 dBm**
   * **Fiber Attenuation: 0.35 dB/km**
   **Calculate the maximum fiber length (D) that can be used between the OLT (Optical Line Terminal) and ONU (Optical Network Unit) while maintaining an acceptable signal level.** **(Islami Bank PLC Senior Officer (Network/System) Exam: 14.03.2025 (BUET)) [compact it 1332]**

## Network Topologies

1. **What is Star vs Mesh Topology?** **(National Legal Aid Services Organization - Assistant Maintenance Engineer Exam: 18.10.2025) [compact it 1449]**

## OSI & TCP/IP Reference Model

1. Mention the layers of the OSI Model and the function of each layer. (Combined Bank Officer (IT) Exam: 03.01.2026) [debug it]

2. **OSI মডেলের ৭টি স্তরের কাজ কি? এই সমগ্র স্তরগুলোর ভূমিকা কি?** **(Assistant Programmer - Department of Immigration & Passports Exam: 15.07.2026) [compact it 1464]**

3. **Write bottom to top OSI reference Model.** **(National Legal Aid Services Organization - Assistant Maintenance Engineer Exam: 18.10.2025) [compact it 1449]**

4. **In the TCP/IP model, how is data known in the different layers?** **(DPDC - Assistant Engineer (CSE) Exam: 17.10.2025) [compact it 1453]**

## Application Layer & Well-Known Port Numbers

1. Full Form and Port Number – SSH, FTP, SMTP, DNS, IMAP. (BEPRC Assistant Programmer Exam: 08.08.2026)

## Transport Layer (TCP & UDP)

1. Compare TCP and UDP protocols with examples. (Combined Bank Officer (IT) Exam: 03.01.2026) [debug it]

2. A client needs to send 4000\text{ bytes} of data to a database server. The client divides the data into packets of 500\text{ bytes} each. The sequence number of the first packet is 3001. After 2500\text{ bytes} have been successfully sent, 2 packets are lost/failed. Assuming TCP cumulative ACK, complete the following table: [BSCCPL AME 21-08-2026 (BUET)]

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

## Communication System & Transmission Modes

1. What is a communication system? Describe the different types of transmission modes with examples. (Combined Bank Officer (IT) Exam: 09.05.2026) [debug it]

## Flow Control & Data Link Layer (Stop-and-Wait)

1. A single-mode optical fiber communication link connects two locations 250\text{ km} apart using WDM technology with 50 channels, where each channel provides a bit rate of 10\text{ Gbps}. The refractive index of the fiber is 1.5, and data is transmitted using the Stop-and-Wait protocol. A 1\text{ GB} file is divided into suitable data frames, and after successfully receiving each frame, the receiver sends a 54-byte acknowledgment (ACK) back to the sender. Assuming no processing or queuing delay, determine the total time required to completely transfer the 1\text{ GB} file, including data transmission time, propagation delay, ACK transmission time, and the Stop-and-Wait waiting time. [BSCCPL AME 21-08-2026 (BUET)]

## Pulse Code Modulation (PCM) & Signal Processing

1. **A PCM system have step resolution of 2V. Sinusoidal signal amplitude 10V. SNR=? And total number of bits=?** **(DPDC - Assistant Engineer (CSE) Exam: 17.10.2025) [compact it 1453]**

## Error Detection & Data Communication (CRC, Throughput)

1. (a) CMY color model এর উপাদানগুলো লিখুন (CMY color model এর কাজ কী?)
   (b) CRC এর কাজ কী? (IIB CRC-16 এর ক্ষেত্র এবং প্রশ্নগুলো আলোচনা করুন)
   (c) Data communication এর ক্ষেত্রে bandwidth এবং throughput এর মধ্যে পার্থক্য লিখুন। **(Assistant Programmer - Department of Immigration & Passports Exam: 15.07.2026) [compact it 1464]**

2. **Data communication mathematical problems.** **(DPDC Assistant Manager (ICT) Exam: 27.06.2025 (BUET)) [compact it 1368]**

3. **Question on data communication transmission and signal related math.** **(DPDC - Junior Assistant Manager (JAM) Exam: 27.06.2025 (BUET)) [compact it 1441]**

## Multiplexing & Bandwidth

1. Five channels, each with a 100-kHz bandwidth, are to be multiplexed together. What is the minimum bandwidth of the link if there is a need for a guard band of 10 kHz between the channels to prevent interference? [SO IT 25-07-2026]

## Subnetting & IP Addressing

1. An organization is granted the IPv4 network block 14.24.74.0/24 and needs to segment it into two subnets: Subnet A (requires 120 addresses) and Subnet B (requires 60 addresses). Allocating sequentially from the requirement first to maximize remaining address space, state only the Network Address (with its CIDR mask) and the Broadcast Address for both subnets. [SO IT 25-07-2026]

2. An organization has been assigned the IPv4 network address 192.168.1.0/24. As part of the network deployment, the network administrator is required to divide the address space into four equal-sized subnets to support different departments. Determine the Network Address, Subnet Mask (both CIDR and dotted-decimal notation). (Officer (IT) Exam: 31 Jul 2026) [bscs 01]

3. Subnetting logic requires precise binary calculation. A network engineer is tasked with dividing the internal network 192.168.10.0/24 into exactly 4 equal subnets for four different bank branches. Show the mathematical calculation to determine how many bits must be borrowed to create 4 subnets, and state the new Subnet Mask in both CIDR notation and decimal format. (Combined Bank Officer (IT) Exam: 09.05.2026) [debug it]

4. Network Address, Broadcast Address, Subnet Mask and Usable Host IP Range of: 10.0.0.0/30, 192.168.0.0/23, 172.16.1.0/24. (BEPRC Assistant Programmer Exam: 08.08.2026)

5. (a) IP address এবং MAC/MU এর পার্থক্য লেখ।
   (b) Classfull এবং Classless IP address এর মধ্যে পার্থক্য লেখ।
   (c) 11000001 00001001 00001010 00010101 এই IP এর Class লিখ। **(Assistant Programmer - Department of Immigration & Passports Exam: 15.07.2026) [compact it 1464]**

6. **Given IP address 10.0.0.100 and Subnet mask 255.255.240.0 which is network address?** **(National Legal Aid Services Organization - Assistant Maintenance Engineer Exam: 18.10.2025) [compact it 1449]**

7. **Given IP address 10.10.0.0/16, you have divide the network into eight equal subnets. Find the subnet mask in dotted decimal and CIDR notation. Also find the first and last usable IP addresses of third subnet.** **(DPDC Assistant Manager (ICT) Exam: 27.06.2025 (BUET)) [compact it 1362]**

8. **Given IP address 10.10.0.0/16, you have divide the network into eight equal subnets. Find the subnet mask in dotted decimal and CIDR notation. Also find the first and last usable IP addresses of third subnet.** **(DPDC - Junior Assistant Manager (JAM) Exam: 27.06.2025 (BUET)) [compact it 1440]**

9. **Subnet mask & Total host calculation.** **(DPDC - Assistant Engineer (CSE) Exam: 17.10.2025) [compact it 1453]**

10. **Given the network 245.248.128.0/20, divide the address space among three departments as follows:**
   **(a) Manager: half of the address space.**
   **(b) HR: one-quarter of the address space.**
   **(c) Admin: the remaining one-quarter.** **(Dhaka WASA - Assistant Maintenance Engineer (Network) Exam: 04.07.2025 (BUET)) [compact it 1437]**

   **For each department, determine:**
   **(i) The network block (in CIDR notation).**
   **(ii) The IP address valid range.**
   **(iii) The number of valid hosts.** **(Dhaka WASA - Assistant Maintenance Engineer (Network) Exam: 04.07.2025 (BUET)) [compact it 1438]**

11. **Find out the network address and Broadcast address of the address: 192.168.0.0/28** **(DESCO Sub-Assistant Engineer Exam: 20.06.2025 (BUET)) [compact it 1360]**

## IPv6 Addressing

1. 4B:30:10:21:2A:1B, 4C:20:1B:2E:08:E7 Identify which of the given IPv6 addresses represent Unicast and Multicast communication, and determine whether any of them represents a Broadcast address. Explain your answer based on the IPv6 addressing rules. [BSCCPL AME 21-08-2026 (BUET)]

2. A host is connected to an IPv6 network and needs to configure its own IPv6 address automatically using Stateless Address Autoconfiguration (SLAAC). Arrange the steps in the correct order and explain the purpose of each step. [BSCCPL AME 21-08-2026 (BUET)]

## Routing Protocols & Route Configuration

1. A BGP router receives multiple routes to the same destination network from different neighboring autonomous systems. The available routes are given in the following table, containing Path, LOCAL_PREF, AS_PATH, ORIGIN, and MED values. Using the standard BGP best-path selection rules, analyze the attributes in the given order and determine which path will be selected as the best route, showing the comparison and justification for each step. [BSCCPL AME 21-08-2026 (BUET)]

| Path | LOCAL_PREF | AS_PATH | ORIGIN | MED |
|---|---|---|---|---|
| Path 1 | 200 | 65001 65010 | IGP | 50 |
| Path 2 | 150 | 65020 | IGP | 5 |
| Path 3 | 200 | 65030 65040 | IGP | 10 |
| Path 4 | 200 | 65050 65060 | IGP | 20 |

2. **Static route Configuration: Configure R0 to reach PC1 you can assume any Vendor, Cisco, Huawei, juniper** **(Islami Bank PLC Senior Officer (Network/System) Exam: 14.03.2025 (BUET)) [compact it 1331]**

3. **What is OSPF? Briefly Explain.** **(DESCO Sub-Assistant Engineer Exam: 20.06.2025 (BUET)) [compact it 1358]**

## High Availability & Redundancy Protocols (VRRP, HSRP)

1. **State the network protocol of VRRP?** **(DESCO Sub-Assistant Engineer Exam: 20.06.2025 (BUET)) [compact it 1359]**

## Networking Devices

1. Describe the functions of a Switch and a Router and explain two key differences between these networking devices. (Officer (IT) Exam: 31 Jul 2026) [bscs 02]

## VLANs & Subnetting Comparison

1. A large organization wants to isolate different departments and user groups within the same physical network to improve security, reduce broadcast traffic, and manage network resources efficiently. The network administrator is considering either subnetting or VLANs to achieve this isolation. Compare subnetting and VLANs in this scenario and determine which technique is more appropriate for logical network isolation, explaining how the selected technique improves security and traffic management. [BSCCPL AME 21-08-2026 (BUET)]

## Network Address Translation (NAT)

1. Network Address Translation (NAT) maps internal networks to the public internet.
   * (a) Explain the historical IP addressing limitation that made NAT a necessity globally.
   * (b) Explain the step-by-step logical translation process that occurs at a branch router when an internal employee (IP 192.168.1.5) sends a web request to an external server, and how the router correctly handles the returning response packet. (Combined Bank Officer (IT) Exam: 09.05.2026) [debug it]

## Application Layer Protocols & Troubleshooting (DNS, DHCP, HTTPS)

1. [http://BSCPL.bd.gov](http://BSCPL.bd.gov) is connected to multiple international ISPs, and users can successfully access other websites, but they are unable to access the [http://BSCPL.bd.gov](http://BSCPL.bd.gov) website. The network uses essential services such as DNS, DHCP, and HTTPS, each performing different functions in the communication process. Identify the roles of DNS, DHCP, and HTTPS, determine which component or configuration could be responsible for this site-specific failure, and explain the possible causes and troubleshooting steps. [BSCCPL AME 21-08-2026 (BUET)]

2. **Write down the DNS function.** **(National Legal Aid Services Organization - Assistant Maintenance Engineer Exam: 18.10.2025) [compact it 1449]**

3. **Why does the Domain Name System (DNS) primarily use UDP as its transport layer protocol instead of TCP? Describe the sequence of events that take place during the DNS name resolution process when a user enters www.companybd.com into a web browser and presses Enter.** **(Combined Bank Senior Officer (IT) Exam: 17.10.2025 (E-Zone)) [compact it 1421]**
