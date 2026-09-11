<!-- TOC START -->
**Table of Contents** — 9 subtopics · 29 theories

1. **[Computer Fundamentals & Acronyms](#computer-fundamentals--acronyms)**
   - [Computer and Computer System — Characteristics and Elements](#computer-and-computer-system--characteristics-and-elements)
   - [Generations of Computers](#generations-of-computers)
   - [Classification of Computers](#classification-of-computers)
   - [Data, Information and Units of Storage](#data-information-and-units-of-storage)
   - [Character Encoding — ASCII, Unicode and EBCDIC](#character-encoding--ascii-unicode-and-ebcdic)
   - [Registers in a Computer](#registers-in-a-computer)
   - [Master Glossary of IT Acronyms](#master-glossary-of-it-acronyms)
   - [Milestones, Firsts and Famous Names in Computing](#milestones-firsts-and-famous-names-in-computing)

2. **[ICT in Society & Governance](#ict-in-society--governance)**
   - [The Fourth Industrial Revolution (IR 4.0)](#the-fourth-industrial-revolution-ir-40)
   - [E-Governance and Digital Bangladesh](#e-governance-and-digital-bangladesh)
   - [E-Commerce and E-Business](#e-commerce-and-e-business)
   - [Information Systems — TPS, MIS and DSS](#information-systems--tps-mis-and-dss)
   - [Other ICT Topics — Copyright, RFID, Viral Video and Banking Software](#other-ict-topics--copyright-rfid-viral-video-and-banking-software)
   - [Digital Banking and Electronic Payment Systems](#digital-banking-and-electronic-payment-systems)

3. **[Quantum Computing & Emerging Technologies](#quantum-computing--emerging-technologies)**
   - [Quantum Computing](#quantum-computing)
   - [Virtual Reality, Augmented Reality and Nanotechnology](#virtual-reality-augmented-reality-and-nanotechnology)

4. **[Hardware Components & BIOS (CMOS Battery)](#hardware-components--bios-cmos-battery)**
   - [BIOS, CMOS, UEFI and the Boot Process](#bios-cmos-uefi-and-the-boot-process)
   - [Input and Output Devices](#input-and-output-devices)
   - [Factors Affecting Computer Performance](#factors-affecting-computer-performance)

5. **[Software Types & Classification](#software-types--classification)**
   - [Software — Types and Classification](#software--types-and-classification)
   - [Programming Languages and Their Levels](#programming-languages-and-their-levels)
   - [Common Application Software and Office Tools](#common-application-software-and-office-tools)

6. **[Data Center Infrastructure & Power Management](#data-center-infrastructure--power-management)**
   - [Data Centre — Components and Design Factors](#data-centre--components-and-design-factors)
   - [Data Centre Tier Standards](#data-centre-tier-standards)
   - [Data Centre Power — UPS, Generators and DCIM](#data-centre-power--ups-generators-and-dcim)

7. **[Server Hardware & Enterprise Systems](#server-hardware--enterprise-systems)**
   - [Server Hardware — Components and Selection](#server-hardware--components-and-selection)

8. **[User Interfaces (CLI vs GUI)](#user-interfaces-cli-vs-gui)**
   - [Command Line Interface and Graphical User Interface](#command-line-interface-and-graphical-user-interface)

9. **[Blockchain & Emerging Technologies](#blockchain--emerging-technologies)**
   - [Blockchain — Concept and How It Works](#blockchain--concept-and-how-it-works)
   - [Other Emerging Technology Short Notes](#other-emerging-technology-short-notes)

<!-- TOC END -->

---

## Computer Fundamentals & Acronyms

### Computer and Computer System — Characteristics and Elements

#### What is a computer?

A **computer** is an **electronic device** that accepts **data** as input, **processes** it according to a set of stored instructions (a **program**), produces **information** as output, and can **store** both data and results for later use.

The word comes from the Latin *computare*, "to calculate" — but a modern computer does far more than arithmetic.

#### Computer vs Computer System

| Point | **Computer** | **Computer System** |
|---|---|---|
| **Meaning** | The **physical machine** that processes data | The **complete working arrangement** of hardware + software + data + people + procedures |
| **Scope** | **Narrow** — just the device | **Wide** — everything needed to get useful work done |
| **Components** | CPU, memory, input/output devices | **Hardware, Software, Data, People (liveware), Procedures**, and often Connectivity |
| **Can it work alone?** | A computer without software is useless metal | The system is what actually **delivers the result** |
| **Example** | A desktop PC box | The PC + Windows + MS Office + the user + the office's working procedures |

#### The five elements of a computer system

```mermaid
flowchart TD
    CS["COMPUTER SYSTEM"]
    CS --> H["1 . HARDWARE<br/>the physical parts you can touch"]
    CS --> S["2 . SOFTWARE<br/>the programs that tell it what to do"]
    CS --> D["3 . DATA<br/>the raw facts to be processed"]
    CS --> P["4 . PEOPLE / Liveware<br/>users, operators, programmers"]
    CS --> PR["5 . PROCEDURES<br/>the rules and documentation for using it"]
```

#### The characteristics of a computer

| # | Characteristic | Meaning |
|---|---|---|
| 1 | **Speed** | Executes millions/billions of instructions per second; measured in MIPS, FLOPS, GHz |
| 2 | **Accuracy** | Results are exact — errors are almost always **human** errors of input or programming (**GIGO — Garbage In, Garbage Out**) |
| 3 | **Diligence** | Never gets tired, bored or distracted; the millionth calculation is as accurate as the first |
| 4 | **Versatility** | The same machine plays music, prints bills and predicts the weather |
| 5 | **Storage capacity** | Stores enormous volumes of data and retrieves it instantly |
| 6 | **Automation** | Once started, it completes a job without human intervention |
| 7 | **Reliability** | Consistent output over long periods |
| 8 | **No IQ / No intelligence** | A computer **has no intelligence of its own** — it only follows instructions. *(The standard exam answer to "What is the IQ of a computer?" is **ZERO**.)* |
| 9 | **No feelings** | It cannot make judgements based on emotion or experience |

#### The basic block diagram of a computer

```mermaid
flowchart LR
    I["INPUT UNIT<br/>keyboard, mouse, scanner"] --> CPU
    subgraph CPU["CENTRAL PROCESSING UNIT (CPU)"]
        CU["Control Unit (CU)<br/>directs all operations"]
        ALU["Arithmetic Logic Unit (ALU)<br/>calculations & comparisons"]
        REG["Registers<br/>ultra-fast temporary storage"]
    end
    CPU --> O["OUTPUT UNIT<br/>monitor, printer, speaker"]
    CPU <--> M["MEMORY UNIT<br/>Primary: RAM, ROM<br/>Secondary: HDD, SSD"]
```

| Unit | Function |
|---|---|
| **Input unit** | Accepts data and instructions and converts them to machine form |
| **CPU — Control Unit** | The "brain's manager": fetches, decodes and directs the execution of instructions |
| **CPU — ALU** | Performs all **arithmetic** (+, −, ×, ÷) and **logical** (AND, OR, NOT, comparison) operations |
| **CPU — Registers** | Tiny, extremely fast storage inside the CPU for the data being worked on right now |
| **Memory unit** | Holds the program and data — **primary** (RAM/ROM) and **secondary** (disk) |
| **Output unit** | Converts the result to human-readable form |

*(The CPU is often called the **brain** of the computer; the **Motherboard** is the main circuit board connecting everything.)*

**Previous Year Question List from this Topic:**

- [Here some idea in computer architecture. You fill the idea part of the table which describe the best? GUI, RAID, API, LRU](../written-answers/computer-fundamental.md?plain=1#L329)
- [(ক) “Computer” এবং “Computer System' এই দুটি term এর মধ্যে পার্থক্য কি?](../written-answers/computer-fundamental.md?plain=1#L437)
- [What are the characteristics and elements of a computer system?](../written-answers/computer-fundamental.md?plain=1#L1042)
- [Name and define the components of a computer system. Mention two optical input devices.](../written-answers/computer-fundamental.md?plain=1#L2303)
- [What are the components of a Micro computer system?](../written-answers/computer-fundamental.md?plain=1#L2329)
- [(খ) Computer System এর Components গুলির সংক্ষিপ্ত বর্ণনাসহ লিখুন।](../written-answers/computer-fundamental.md?plain=1#L2401)


---

### Generations of Computers

A **computer generation** is a stage in the development of computer technology, defined mainly by the **electronic component** used to build the processor. Each generation brought a large jump in speed, size, cost and reliability.

| Generation | Period | Main component | Language | Characteristics | Examples |
|---|---|---|---|---|---|
| **1st** | **1940–1956** | **Vacuum tubes** | Machine language (binary) | Huge, consumed enormous power, generated great heat, very unreliable, used punch cards | **ENIAC, EDVAC, EDSAC, UNIVAC-1, IBM-701** |
| **2nd** | **1956–1963** | **Transistors** | **Assembly language**, early FORTRAN/COBOL | Smaller, faster, cheaper, more reliable, less heat; magnetic core memory | IBM 1401, IBM 7094, CDC 1604, UNIVAC 1108 |
| **3rd** | **1964–1971** | **IC — Integrated Circuits (SSI, MSI)** | **High-level languages** (FORTRAN, COBOL, PASCAL, BASIC) | Much smaller and faster; keyboard and monitor introduced; **operating systems** and multiprogramming appear | IBM 360, IBM 370, PDP-8, PDP-11, ICL 2900 |
| **4th** | **1971–present** | **VLSI — Very Large Scale Integration / MICROPROCESSOR** | C, C++, Java, Python; GUI | Personal computers, GUI, networks, **the Internet**, portable devices; cheap and everywhere | IBM PC, Apple II, Macintosh, Pentium, modern laptops |
| **5th** | **Present & beyond** | **ULSI + Artificial Intelligence**, parallel processing, **quantum** | Natural language, AI languages (LISP, Prolog, Python) | **AI-based**, voice and image recognition, robotics, expert systems, quantum and bio computing | IBM Watson, self-driving cars, AI assistants, quantum computers |

```mermaid
flowchart LR
    A["1st Gen<br/>Vacuum Tube<br/>1940-56"] --> B["2nd Gen<br/>Transistor<br/>1956-63"]
    B --> C["3rd Gen<br/>Integrated Circuit<br/>1964-71"]
    C --> D["4th Gen<br/>Microprocessor / VLSI<br/>1971-present"]
    D --> E["5th Gen<br/>AI / ULSI / Quantum<br/>present onward"]
```

> **Key one-line answers:**
> - **"The base of the 5th generation computer" → Artificial Intelligence** (built on ULSI technology and parallel processing).
> - **"Which generation used VLSI?" → the FOURTH generation.**
> - **"Which generation introduced the microprocessor?" → the FOURTH.**
> - **"Which generation first used high-level languages?" → the THIRD.**
> - **"Which generation used transistors?" → the SECOND.**

#### The IC scales (useful for the VLSI question)

| Abbreviation | Full form | Transistors per chip | Generation |
|---|---|---|---|
| **SSI** | Small Scale Integration | 1 – 100 | 3rd |
| **MSI** | Medium Scale Integration | 100 – 1,000 | 3rd |
| **LSI** | Large Scale Integration | 1,000 – 10,000 | 3rd/4th |
| **VLSI** | **Very Large Scale Integration** | 10,000 – 1,000,000 | **4th** |
| **ULSI** | **Ultra Large Scale Integration** | over 1,000,000 | **5th** |

**Previous Year Question List from this Topic:**

- [What is the base of 5th generation Computer?](../written-answers/computer-fundamental.md?plain=1#L279)
- [কম্পিউটার প্রজন্ম বলতে কী বোঝায়? কম্পিউটারের বিভিন্ন প্রজন্মের বৈশিষ্ট্য বর্ণনা করুন।](../written-answers/computer-fundamental.md?plain=1#L288)
- [১৭. কোন প্রজন্মের কম্পিউটারে VLSI (Very Large Scale Integration) চিপ ব্যবহার শুরু হয়?](../written-answers/computer-fundamental.md?plain=1#L706)


---

### Classification of Computers

#### By size, capacity and cost

| Type | Description | Users at once | Examples / Use |
|---|---|---|---|
| **Supercomputer** | The **fastest and most expensive**; used for the heaviest scientific computation | Thousands | Weather forecasting, nuclear simulation, genome research, space research. **Frontier, Fugaku**; Bangladesh's **BCSIR supercomputer** |
| **Mainframe computer** | Very large, high **throughput**, extremely reliable, runs continuously for years | Hundreds to thousands | Banks, railways, insurance, census. **IBM z-series** |
| **Mini computer** (midrange) | Medium size and power, between mainframe and micro | Tens to hundreds | Departmental servers, industrial control. PDP-11, AS/400 |
| **Micro computer** (Personal Computer) | Built around a **single microprocessor**; small and cheap | **One** | Desktop, laptop, tablet, smartphone, workstation |

> **The difference between a supercomputer and a mainframe** is the key comparison: a **supercomputer** maximises **speed on one huge calculation** (measured in FLOPS), while a **mainframe** maximises **throughput — the number of transactions handled reliably** (measured in transactions per second).

#### Components of a micro-computer system

A **micro computer** = a **microprocessor (CPU)** + **memory (RAM/ROM)** + **input/output devices** + **storage** + a **motherboard/bus** joining them, plus a **power supply** and system software.

#### By the type of data handled

| Type | Works with | Example |
|---|---|---|
| **Analog computer** | **Continuous** physical quantities (voltage, pressure, temperature) | Speedometer, thermometer, old flight simulators |
| **Digital computer** | **Discrete** values — binary 0 and 1 | All modern computers |
| **Hybrid computer** | **Both** — measures analog signals and processes them digitally | ICU patient monitors, petrol pumps, ECG machines |

#### By purpose

| Type | Description |
|---|---|
| **General purpose** | Can run any program — a PC or laptop |
| **Special purpose** | Built for one job — an ATM, a washing-machine controller, a traffic signal |

**Previous Year Question List from this Topic:**

- [বিশ্বের সবচেয়ে শক্তিশালী সুপার কম্পিউটারের নাম কী?](../written-answers/computer-fundamental.md?plain=1#L480)
- [(ক) আকার আকৃতি ও ক্ষমতার ভিত্তিতে Digital Computer-এর প্রকারভেদ আলোচনা করুন।](../written-answers/computer-fundamental.md?plain=1#L759)
- [What are the components of a Micro computer system?](../written-answers/computer-fundamental.md?plain=1#L2329)


---

### Data, Information and Units of Storage

#### Data vs Information — a very frequently asked comparison

| Point | **Data** | **Information** |
|---|---|---|
| **Meaning** | **Raw, unorganised facts** and figures | **Processed, organised data** that has meaning |
| **Processing** | **Input** to processing | **Output** of processing |
| **Usefulness alone** | Not meaningful by itself | **Meaningful and useful** for decisions |
| **Depends on** | Nothing — it just exists | **Depends on data** |
| **Form** | Numbers, characters, symbols, images | Reports, charts, summaries, conclusions |
| **Decision making** | Cannot be used directly | **Used directly** |
| **Example** | `85, 90, 78, 92` | *"The class average is 86.25, which is a B+"* |
| **Example 2** | A list of every ATM transaction | *"Withdrawals peak on the 1st of each month"* |

```mermaid
flowchart LR
    D["DATA<br/>raw facts<br/>85, 90, 78, 92"] --> P["PROCESSING<br/>sort, calculate,<br/>summarise, analyse"]
    P --> I["INFORMATION<br/>Average = 86.25<br/>Grade = B+"]
    I --> K["KNOWLEDGE<br/>'This batch performs<br/>above the standard'"]
    K --> W["WISDOM<br/>'Keep the current<br/>teaching method'"]
```

#### Units of data storage

| Unit | Equal to | Note |
|---|---|---|
| **Bit** | 0 or 1 | **Bi**nary Digi**t** — the smallest unit |
| **Nibble** | **4 bits** | Half a byte; one hexadecimal digit |
| **Byte** | **8 bits** | The storage of **one character** in ASCII |
| **Kilobyte (KB)** | **1,024 bytes** = 2¹⁰ | |
| **Megabyte (MB)** | 1,024 KB = 2²⁰ bytes | |
| **Gigabyte (GB)** | 1,024 MB = 2³⁰ bytes | |
| **Terabyte (TB)** | **1,024 GB** = 2⁴⁰ bytes = **1,099,511,627,776 bytes** | |
| **Petabyte (PB)** | 1,024 TB | |
| **Exabyte (EB)** | 1,024 PB | |
| **Zettabyte (ZB)** | 1,024 EB | |
| **Yottabyte (YB)** | 1,024 ZB | The largest standard unit |

> ### **1 TB = how many bytes?**
> **1 TB = 1024 GB = 1024 × 1024 MB = 1024 × 1024 × 1024 KB = 1024⁴ bytes = 2⁴⁰ = 1,099,511,627,776 bytes** ≈ **1.1 × 10¹²** bytes.
>
> *(Disk manufacturers use the decimal definition **1 TB = 10¹² = 1,000,000,000,000 bytes**, which is why a "1 TB" drive shows as about **931 GB** in Windows. The binary units are strictly called **KiB, MiB, GiB, TiB**.)*

#### A worked storage calculation

> **A file contains 1 million characters. How much space does it need?**

| Encoding | Bytes per character | Total |
|---|---|---|
| **ASCII / ANSI** | **1 byte** | 1,000,000 bytes ≈ **977 KB ≈ 0.95 MB** |
| **UTF-8** (English text) | 1 byte | ≈ 0.95 MB |
| **UTF-8** (Bangla text) | **3 bytes** | 3,000,000 bytes ≈ **2.86 MB** |
| **UTF-16 / Unicode** | **2 bytes** | 2,000,000 bytes ≈ **1.91 MB** |

**Previous Year Question List from this Topic:**

- [1TB = কত বাইট?](../written-answers/computer-fundamental.md?plain=1#L263)
- [Write short notes on: (i) RAM (ii) ROM (iii) Primary key (iv) Foreign key (v) Data](../written-answers/computer-fundamental.md?plain=1#L393)
- [Difference between Data and Information.](../written-answers/computer-fundamental.md?plain=1#L507)
- [You have created a file containing 1 million characters. Suppose you want to save the file in ASCII format. How much memory space in MB in needed to store the f…](../written-answers/computer-fundamental.md?plain=1#L953)


---

### Character Encoding — ASCII, Unicode and EBCDIC

A computer stores **only numbers**. A **character encoding** is the agreed table that maps each character to a number.

| Scheme | Full form | Bits | Characters | Coverage |
|---|---|---|---|---|
| **BCD** | Binary Coded Decimal | 4 (per digit) | 10 digits | Digits only |
| **ASCII** | **American Standard Code for Information Interchange** | **7 bits** (8 with the parity/extended bit) | **128** (extended: 256) | English letters, digits, punctuation, control codes |
| **EBCDIC** | Extended Binary Coded Decimal Interchange Code | **8 bits** | 256 | Used on **IBM mainframes** |
| **Unicode** | — | **16 bits** (UTF-16) / variable (UTF-8) | **Over 1.1 million code points** (65,536 in the Basic Multilingual Plane) | **Every writing system in the world**, including **Bangla**, plus emoji |

#### Key ASCII values to memorise

| Character | Decimal |
|---|---|
| `'0'` to `'9'` | **48 – 57** |
| `'A'` to `'Z'` | **65 – 90** |
| `'a'` to `'z'` | **97 – 122** |
| Space | 32 |
| `'\0'` (null) | 0 |
| Enter (LF) | 10 |

**The two useful facts:** `'a' − 'A' = 32`, and `'5' − '0' = 5`.

#### Unicode

> ### "How many bits does a Unicode character use, and how many symbols are possible?"
>
> The classic exam answer is **16 bits**, giving **2¹⁶ = 65,536** possible characters. This refers to **UTF-16 / the Basic Multilingual Plane**, which is what most textbooks mean.
>
> **The fuller modern answer:** Unicode is a **character set**, not a fixed-width encoding. It currently defines **1,114,112 code points (17 planes × 65,536)**, of which about 150,000 are assigned. It is stored using one of three encodings:
>
> | Encoding | Bytes per character |
> |---|---|
> | **UTF-8** | **1 to 4** (variable) — 1 byte for English, **3 bytes for Bangla**; dominant on the web |
> | **UTF-16** | 2 or 4 bytes |
> | **UTF-32** | Always 4 bytes |
>
> **Why Unicode matters to Bangladesh:** ASCII has no place for Bangla. Unicode assigns the Bangla block **U+0980 – U+09FF**, which is what makes Bangla email, websites, SMS and databases possible. Before Unicode, every Bangla font (Bijoy, etc.) used its own incompatible mapping, so text copied between systems turned to garbage.

#### Image and file extensions

| Category | Extensions |
|---|---|
| **Image** | **.jpg / .jpeg, .png, .gif, .bmp, .tiff, .svg, .webp** |
| **Document** | .doc, .docx, .pdf, .txt, .rtf, .odt |
| **Spreadsheet** | .xls, .xlsx, .csv |
| **Audio** | .mp3, .wav, .aac, .flac, .ogg |
| **Video** | .mp4, .avi, .mkv, .mov, .wmv, .flv |
| **Compressed** | .zip, .rar, .7z, .tar, .gz |
| **Executable** | .exe, .com, .bat, .msi (Windows); no extension needed on Linux |
| **Web** | .html, .htm, .css, .js, .php, .jsp, .asp |

**Raster (bitmap) vs Vector images:** **.jpg, .png, .gif, .bmp** are **raster** — a grid of pixels that becomes blocky when enlarged. **.svg, .ai, .eps** are **vector** — mathematical paths that scale to any size with no loss of quality.

**Previous Year Question List from this Topic:**

- [Image file এর extension নিচের কোনটি?](../written-answers/computer-fundamental.md?plain=1#L357)
- [Unicode এর মাধ্যমে সম্ভাব্য কতগুলো চিহ্নকে নির্দিষ্ট করা যায়?](../written-answers/computer-fundamental.md?plain=1#L554)
- [How many bit is use of Unicode digit? (a) 8 (b) 16 (c) 20 (d) 24](../written-answers/computer-fundamental.md?plain=1#L585)
- [You have created a file containing 1 million characters. Suppose you want to save the file in ASCII format. How much memory space in MB in needed to store the f…](../written-answers/computer-fundamental.md?plain=1#L953)


---

### Registers in a Computer

A **register** is a **small, extremely fast storage location inside the CPU** used to hold the data, addresses and instructions the processor is working on **right now**.

Registers sit at the **very top of the memory hierarchy** — faster than cache, faster than RAM — because they are built directly into the CPU circuitry. Their capacity is measured in **bits** (a "64-bit processor" has 64-bit registers), and a CPU has only a few dozen of them.

#### The common registers of a basic computer

| Register | Full name | Function |
|---|---|---|
| **PC** | **Program Counter** (Instruction Pointer) | Holds the **address of the NEXT instruction** to be executed |
| **IR** | **Instruction Register** | Holds the **instruction currently being executed / decoded** |
| **MAR** | **Memory Address Register** | Holds the **address** of the memory location to be read from or written to |
| **MBR / MDR** | **Memory Buffer / Data Register** | Holds the **data** just read from, or about to be written to, memory |
| **AC** | **Accumulator** | Holds the **intermediate results** of ALU operations |
| **AR** | Address Register | Holds an operand's memory address |
| **DR** | Data Register | Holds an operand fetched from memory |
| **TR** | Temporary Register | Scratch space during instruction execution |
| **INPR / OUTR** | Input / Output Register | Buffers data to and from I/O devices |
| **SP** | **Stack Pointer** | Points to the **top of the stack** in memory |
| **PSW / Flag register** | Program Status Word | Holds **status flags** — Zero, Carry, Sign, Overflow, Parity, Interrupt enable |
| **General-purpose registers** | AX, BX, CX, DX (x86) / R0–R31 (RISC) | Hold any operand or result the program needs |

#### How registers are used in the instruction cycle

```mermaid
flowchart LR
    A["1 . FETCH<br/>PC → MAR<br/>memory → MBR → IR<br/>PC = PC + 1"] --> B["2 . DECODE<br/>the Control Unit<br/>interprets IR"]
    B --> C["3 . EXECUTE<br/>the ALU operates,<br/>result → Accumulator"]
    C --> D["4 . STORE<br/>result → memory<br/>via MAR and MBR"]
    D --> A
```

#### Why registers exist

1. **Speed** — accessing a register takes **less than one clock cycle**; RAM takes hundreds.
2. The **ALU can only operate on data held in registers**, not directly on memory.
3. They hold the **state** of execution (PC, flags) that makes sequencing possible.
4. **More registers = fewer memory accesses = faster programs**, which is why RISC architectures provide 32 or more.

**Previous Year Question List from this Topic:**

- [(b) What is register? What are the common register found in a basic computer?](../written-answers/computer-fundamental.md?plain=1#L243)


---

### Master Glossary of IT Acronyms

A large share of the marks in this subject comes from **full forms**. Learn them grouped by subject, not as a random list.

#### Networking and Internet

| Acronym | Full form |
|---|---|
| **HTTP** | **HyperText Transfer Protocol** |
| **HTTPS** | **HyperText Transfer Protocol Secure** |
| **FTP** | File Transfer Protocol |
| **SMTP** | **Simple Mail Transfer Protocol** (sending mail) |
| **POP / POP3** | **Post Office Protocol version 3** (downloading mail) |
| **IMAP** | Internet Message Access Protocol |
| **MIME** | **Multipurpose Internet Mail Extensions** |
| **TCP** | **Transmission Control Protocol** |
| **IP** | Internet Protocol |
| **TCP/IP** | Transmission Control Protocol / Internet Protocol |
| **UDP** | **User Datagram Protocol** |
| **ICMP** | **Internet Control Message Protocol** |
| **ARP** | **Address Resolution Protocol** |
| **RARP** | Reverse Address Resolution Protocol |
| **GARP** | Gratuitous ARP |
| **DNS** | **Domain Name System** |
| **DHCP** | **Dynamic Host Configuration Protocol** |
| **NAT** | **Network Address Translation** |
| **MAC** | **Media Access Control** |
| **URL** | **Uniform Resource Locator** |
| **URI** | Uniform Resource Identifier |
| **RIP** | **Routing Information Protocol** |
| **OSPF** | **Open Shortest Path First** |
| **BGP** | Border Gateway Protocol |
| **CSMA** | **Carrier Sense Multiple Access** |
| **CSMA/CD** | CSMA with Collision Detection |
| **CSMA/CA** | CSMA with Collision Avoidance |
| **VPN** | Virtual Private Network |
| **VLAN** | Virtual Local Area Network |
| **LAN / MAN / WAN** | Local / Metropolitan / Wide Area Network |
| **VSAT** | **Very Small Aperture Terminal** |
| **WiMAX** | **Worldwide Interoperability for Microwave Access** |
| **Wi-Fi** | **Wireless Fidelity** |
| **LTE** | **Long Term Evolution** |
| **VoIP** | **Voice over Internet Protocol** |
| **ISP** | Internet Service Provider |
| **SSL / TLS** | Secure Sockets Layer / Transport Layer Security |
| **SNMP** | Simple Network Management Protocol |
| **Telnet** | Telecommunication Network |
| **PPP** | Point-to-Point Protocol |

#### Hardware and architecture

| Acronym | Full form |
|---|---|
| **CPU** | **Central Processing Unit** |
| **ALU** | Arithmetic Logic Unit |
| **CU** | Control Unit |
| **RAM** | **Random Access Memory** |
| **ROM** | **Read Only Memory** |
| **PROM** | **Programmable Read Only Memory** |
| **EPROM** | Erasable Programmable ROM |
| **EEPROM** | Electrically Erasable Programmable ROM |
| **BIOS** | **Basic Input Output System** |
| **UEFI** | **Unified Extensible Firmware Interface** |
| **CMOS** | **Complementary Metal Oxide Semiconductor** |
| **VLSI / ULSI** | Very / Ultra Large Scale Integration |
| **TTL** | Transistor-Transistor Logic |
| **HDD / SSD** | Hard Disk Drive / Solid State Drive |
| **RAID** | **Redundant Array of Independent (Inexpensive) Disks** |
| **SATA** | Serial Advanced Technology Attachment |
| **SAS** | Serial Attached SCSI |
| **SCSI** | Small Computer System Interface |
| **USB** | Universal Serial Bus |
| **VGA** | **Video Graphics Array** |
| **EGA** | **Enhanced Graphics Adapter** |
| **CGA** | Colour Graphics Adapter |
| **HDMI** | High-Definition Multimedia Interface |
| **LCD / LED** | **Liquid Crystal Display** / Light Emitting Diode |
| **CRT** | Cathode Ray Tube |
| **GPU** | Graphics Processing Unit |
| **UPS** | Uninterruptible Power Supply |
| **OMR** | **Optical Mark Reader / Recognition** |
| **OCR** | **Optical Character Recognition** |
| **MICR** | **Magnetic Ink Character Recognition** |
| **RFID** | Radio Frequency Identification |
| **GPS** | **Global Positioning System** |
| **DVD** | **Digital Versatile Disc** (originally Digital Video Disc) |
| **CD-ROM** | Compact Disc Read Only Memory |
| **SMPS** | Switched Mode Power Supply |

#### Software, data and programming

| Acronym | Full form |
|---|---|
| **OS** | Operating System |
| **GUI / CLI** | Graphical User Interface / Command Line Interface |
| **API** | Application Programming Interface |
| **IDE** | Integrated Development Environment |
| **SDK** | Software Development Kit |
| **JVM / JDK / JRE** | Java Virtual Machine / Development Kit / Runtime Environment |
| **ASCII** | **American Standard Code for Information Interchange** |
| **EBCDIC** | Extended Binary Coded Decimal Interchange Code |
| **XML** | **eXtensible Markup Language** |
| **HTML** | HyperText Markup Language |
| **JSON** | JavaScript Object Notation |
| **SQL** | **Structured Query Language** |
| **PL/SQL** | Procedural Language extensions to SQL |
| **PostgreSQL** | "Post-Ingres" Structured Query Language |
| **DBMS / RDBMS** | (Relational) **DataBase Management System** |
| **ACID** | Atomicity, Consistency, Isolation, Durability |
| **JPEG** | **Joint Photographic Experts Group** |
| **PNG** | **Portable Network Graphics** |
| **GIF** | Graphics Interchange Format |
| **MPEG** | Moving Picture Experts Group |
| **PDF** | Portable Document Format |
| **COBOL** | **COmmon Business Oriented Language** |
| **FORTRAN** | **FORmula TRANslation** |
| **BASIC** | Beginner's All-purpose Symbolic Instruction Code |
| **ALGOL** | ALGOrithmic Language |
| **LISP** | LISt Processing |
| **PHP** | PHP: Hypertext Preprocessor (originally Personal Home Page) |
| **ASP** | Active Server Pages |
| **COCOMO** | **COnstructive COst MOdel** |
| **UML** | Unified Modeling Language |
| **SDLC** | Software Development Life Cycle |
| **MOOC** | **Massive Open Online Course** |

#### Security

| Acronym | Full form |
|---|---|
| **VIRUS** | **Vital Information Resources Under Siege** |
| **DoS / DDoS** | **Denial of Service** / Distributed Denial of Service |
| **CIA (triad)** | Confidentiality, Integrity, Availability |
| **AES / DES** | Advanced / Data Encryption Standard |
| **RSA** | Rivest–Shamir–Adleman |
| **PKI** | Public Key Infrastructure |
| **IDS / IPS** | Intrusion Detection / Prevention System |
| **MFA / 2FA** | Multi-Factor / Two-Factor Authentication |
| **OTP** | One Time Password |
| **SSO** | Single Sign-On |
| **CAPTCHA** | Completely Automated Public Turing test to tell Computers and Humans Apart |

#### Business, banking and governance

| Acronym | Full form |
|---|---|
| **ICT** | Information and Communication Technology |
| **IT** | Information Technology |
| **MIS** | **Management Information System** |
| **DSS** | **Decision Support System** |
| **TPS** | Transaction Processing System |
| **EIS** | Executive Information System |
| **ERP** | **Enterprise Resource Planning** |
| **CRM** | Customer Relationship Management |
| **SCM** | Supply Chain Management |
| **ATM** | **Automated Teller Machine** |
| **POS** | Point of Sale |
| **EFT** | Electronic Funds Transfer |
| **EPS** | Electronic Payment System |
| **KYC / eKYC** | (electronic) Know Your Customer |
| **BEFTN** | Bangladesh Electronic Funds Transfer Network |
| **RTGS** | Real Time Gross Settlement |
| **NPSB** | National Payment Switch Bangladesh |
| **BACH** | Bangladesh Automated Clearing House |
| **SWIFT** | Society for Worldwide Interbank Financial Telecommunication |
| **BTRC** | **Bangladesh Telecommunication Regulatory Commission** |
| **BCC** | Bangladesh Computer Council |
| **BTCL** | Bangladesh Telecommunications Company Limited |
| **IoT** | **Internet of Things** |
| **AI / ML** | Artificial Intelligence / Machine Learning |
| **IR 4.0** | Fourth Industrial Revolution |
| **B2B / B2C / C2C / B2G** | Business to Business / Consumer / Consumer to Consumer / Government |

**Previous Year Question List from this Topic:**

- [Write the full meaning: HTTP, DVD, and SMTP?](../written-answers/computer-fundamental.md?plain=1#L214)
- [Provide the full form of the following terms: HTTP, SMTP, ASCII, DHCP, ICMP.](../written-answers/computer-fundamental.md?plain=1#L221)
- [MOOC stands for __________.](../written-answers/computer-fundamental.md?plain=1#L233)
- [Write down the full form of VIRUS?](../written-answers/computer-fundamental.md?plain=1#L238)
- [Write full form of NAT, DHCP, MAC and TCP-IP](../written-answers/computer-fundamental.md?plain=1#L271)
- [Write short note : SMTP, RIP, RDBMS, ITSQN](../written-answers/computer-fundamental.md?plain=1#L307)
- [Write down the Meaning: MIME, PNG, JPGE, OSPF](../written-answers/computer-fundamental.md?plain=1#L315)
- [Full meaning of : HTTPs](../written-answers/computer-fundamental.md?plain=1#L323)
- [১৬. পূর্ণরূপ লিখুন: HTTP, POP, ATM, PROM](../written-answers/computer-fundamental.md?plain=1#L385)
- [Write down the full meaning of SMTP?](../written-answers/computer-fundamental.md?plain=1#L421)
- [Write short answer on the following: (a) Plaintext (b) HTTP (c) Gateway used in \underline{\phantom{\text{Network}}} layer. (d) VIRUS full form (e) Who is the f…](../written-answers/computer-fundamental.md?plain=1#L458)
- [Write full form: DHCP, POP3, VSAT and LCD.](../written-answers/computer-fundamental.md?plain=1#L472)
- [পূর্ণরূপ লিখুন: BTRC, MICR, SMTP, Virus, Wimax.](../written-answers/computer-fundamental.md?plain=1#L525)
- [Write the full form of: VIRUS, BIOS, DoS attack, OSPF, DVD, WiFi.](../written-answers/computer-fundamental.md?plain=1#L657)
- [Write down the full meaning: DHCP, ICMP, ACNS, GARP.](../written-answers/computer-fundamental.md?plain=1#L667)
- [Write the full form: TCP/IP, DHCP, XML, PoSQL, CSMA](../written-answers/computer-fundamental.md?plain=1#L675)
- [What does COBOL stand for?](../written-answers/computer-fundamental.md?plain=1#L698)
- [JPEG and RAID full form কি?](../written-answers/computer-fundamental.md?plain=1#L721)
- [VGA, EGA এর পূর্ণ নাম লিখ।](../written-answers/computer-fundamental.md?plain=1#L728)
- [পূর্ণরূপ লিখ: (a) LTE (b) IOT (c) RDBMS (d) FORTRAN](../written-answers/computer-fundamental.md?plain=1#L736)
- [Write down the full meaning: (i) DNS (ii) TCP (iii) FTP (iv) ARP (v) UDP](../written-answers/computer-fundamental.md?plain=1#L744)
- [Write the full form of following topics:](../written-answers/computer-fundamental.md?plain=1#L878)
- [Explain URL, FTP, ASCII and BIOS](../written-answers/computer-fundamental.md?plain=1#L892)
- [Describe about Firewalls, Microcontroller, COCOMO, Query Optimization, Genetic algorithm and UML.](../written-answers/computer-fundamental.md?plain=1#L919)
- [Explain URL, VOIP and Broadband.](../written-answers/computer-fundamental.md?plain=1#L973)


---

### Milestones, Firsts and Famous Names in Computing

These short factual questions appear in almost every paper.

#### Famous people

| Title | Person |
|---|---|
| **Father of the Computer** | **Charles Babbage** (designed the Analytical Engine, 1837) |
| **Father of the MODERN Computer / Computer Science** | **Alan Turing** |
| **Father of Artificial Intelligence** | **John McCarthy** |
| **Father of the Internet** | **Vinton Cerf** and **Robert Kahn** (TCP/IP) |
| **Inventor of the World Wide Web** | **Tim Berners-Lee** (1989, at CERN) |
| **Father of the Personal Computer** | Henry Edward Roberts |
| **First computer programmer** | **Ada Lovelace** |
| **Inventor of Copy and Paste** | **Larry Tesler** |
| **Founder of Microsoft** | Bill Gates and Paul Allen |
| **Founder of Apple** | Steve Jobs, Steve Wozniak, Ronald Wayne |
| **Founder of Facebook** | **Mark Zuckerberg** (with Eduardo Saverin, Dustin Moskovitz, Chris Hughes, Andrew McCollum) |
| **Founders of Google** | Larry Page and Sergey Brin |
| **Creator of Linux** | Linus Torvalds |
| **Creator of C** | Dennis Ritchie |
| **Creator of C++** | Bjarne Stroustrup |
| **Creator of Java** | James Gosling |
| **Creator of Python** | Guido van Rossum |
| **Inventor of email** | Ray Tomlinson |
| **Bangla font / Bijoy keyboard** | **Mostafa Jabbar** |
| **First Bangla Unicode-based work / Bangla computing pioneer** | Mostafa Jabbar (Bijoy, 1988) |

#### Dates and firsts

| Event | Year |
|---|---|
| First programming language (**FORTRAN**) | **1957** *(the very first was Plankalkül, 1945; the first assembly-level "Short Code" was 1949)* |
| ARPANET (the **Internet begins**) | **1969** |
| **TCP/IP** adopted — the modern Internet | **1 January 1983** |
| World Wide Web invented | 1989 (public in 1991) |
| **Internet comes to Bangladesh** | **1996** (VSAT); submarine cable **SEA-ME-WE-4** in **2006** |
| **Gmail** launched | **2004** |
| Facebook launched | 2004 |
| YouTube launched | 2005 |
| **First video/live sharing site of Bangladesh** | **Bongo / Bioscope** *(early Bangladeshi video platforms)* |
| ChatGPT launched | November 2022 |

#### Nicknames and codenames

| Nickname / Codename | Refers to |
|---|---|
| **"The Big Blue"** | **IBM** |
| **"Longhorn"** | **Windows Vista** (its development codename) |
| "Chicago" | Windows 95 |
| "Whistler" | Windows XP |
| "Blackcomb" / "Vienna" | Windows 7 |
| "Threshold" | Windows 10 |

#### Miscellaneous quick facts

| Question | Answer |
|---|---|
| **The IQ of a computer** | **Zero** — it has no intelligence of its own |
| Most powerful supercomputer (recent) | **Frontier** (USA) — the top of the TOP500 list |
| Molecular-scale / **nano computer** | A **molecular computer** (also called a **DNA computer** or nanocomputer) — built from molecules instead of silicon |
| Full form of **VIRUS** | **Vital Information Resources Under Siege** |
| What is a **plotter**? | An **output device** that draws high-quality line graphics — used for maps, engineering and architectural drawings |
| What is a **touch screen**? | **Both an input AND an output device** |
| Main component of a **dot-matrix printer** | The **print head with a matrix of pins/needles** that strike an inked ribbon (it is an **impact** printer) |
| What is a **graphics card**? | An expansion card (**GPU**) that renders images and sends them to the display; it has its own processor and **VRAM** |
| Two **optical input** devices | **OMR** (Optical Mark Reader) and **OCR / barcode scanner / optical scanner** |

#### OCR vs OMR vs MICR

| Point | **OCR** | **OMR** | **MICR** |
|---|---|---|---|
| **Full form** | Optical **Character** Recognition | Optical **Mark** Reader | **Magnetic Ink** Character Recognition |
| **Reads** | **Printed or handwritten CHARACTERS** and converts them to editable text | **Marks/shading** in predefined positions | Characters printed in **magnetic ink** |
| **Technology** | Light + pattern-recognition software | Light reflectance | **Magnetic** field sensing |
| **Output** | Editable text | Which box was ticked | Account and cheque numbers |
| **Accuracy** | Good but not perfect; depends on font and quality | **Very high** | **Extremely high** — unaffected by stamps, signatures or dirt |
| **Cost** | Low | Low | **High** — special ink and readers |
| **Used for** | Scanning documents/books, number plates, passports, digitising records | **MCQ answer sheets**, surveys, ballot papers, lottery tickets | **Bank CHEQUE processing** — the numbers at the bottom of a cheque |

#### Serial vs Parallel port

| Point | **Serial Port** | **Parallel Port** |
|---|---|---|
| **Data transmission** | **One bit at a time**, over a single wire | **Multiple bits (8 or more) simultaneously**, over parallel wires |
| **Number of wires** | Few (2–9) | Many (25+) |
| **Cable cost and size** | **Cheap, thin, flexible** | Expensive, thick, bulky |
| **Distance** | **Long** — up to 50 ft or much more | **Short** — about 10–15 ft (crosstalk and skew limit it) |
| **Speed (in theory)** | Slower per clock | Faster per clock |
| **Speed (in practice, modern)** | **Much FASTER** — can be clocked far higher | Limited by **clock skew** between the wires |
| **Connector** | DB-9, DB-25, RS-232 | DB-25, Centronics 36-pin |
| **Typical device** | Mouse, modem, console, industrial sensors | Old printers, scanners |
| **Modern successors** | **USB, SATA, PCIe, Ethernet — all SERIAL** | Effectively obsolete |

> **The important insight:** parallel *sounds* faster, but at high frequencies the bits on different wires arrive at slightly different times (**clock skew**) and interfere with each other (**crosstalk**). That is why **every modern high-speed interface — USB, SATA, PCI Express, HDMI, Ethernet — is serial.**

**Previous Year Question List from this Topic:**

- [What is OCR? Write down the difference between OCR and OMR.](../written-answers/computer-fundamental.md?plain=1#L368)
- [What is first programming language?](../written-answers/computer-fundamental.md?plain=1#L428)
- [“Copy and Paste” এর উদ্ভাবক কে?](../written-answers/computer-fundamental.md?plain=1#L499)
- [Internet চালু হয় কত সালে?](../written-answers/computer-fundamental.md?plain=1#L534)
- [আধুনিক Computer এর জনক কাকে বলা হয়?](../written-answers/computer-fundamental.md?plain=1#L544)
- [Computer এর IQ কত?](../written-answers/computer-fundamental.md?plain=1#L568)
- [Bangla font এর উদ্ভাবক কে?](../written-answers/computer-fundamental.md?plain=1#L577)
- [Which year gmail is started? (a) 1998 (b) 1988 (c) 2004 (d) 2021](../written-answers/computer-fundamental.md?plain=1#L593)
- [Meaning of the GPS system? (a) Global Pointing System (b) Global Positioning System (c) Global Partion System (d) None](../written-answers/computer-fundamental.md?plain=1#L602)
- [Facebook এর জনক কে?](../written-answers/computer-fundamental.md?plain=1#L649)
- [Which It company nickname is “The Big Blue”?](../written-answers/computer-fundamental.md?plain=1#L684)
- [Whose codename was Longhorn?](../written-answers/computer-fundamental.md?plain=1#L691)
- [Answer the following question](../written-answers/computer-fundamental.md?plain=1#L790)
- [Short question:](../written-answers/computer-fundamental.md?plain=1#L816)
- [c) Enter annotation (any 5)](../written-answers/computer-fundamental.md?plain=1#L994)
- [Plotter কোন ধরনের Device?](../written-answers/computer-fundamental.md?plain=1#L2480)
- [গ্রাফিক্স কার্ড কি?](../written-answers/computer-fundamental.md?plain=1#L2549)
- [ডট মেট্রিক্স প্রিন্টারের মূল উপাদান কি?](../written-answers/computer-fundamental.md?plain=1#L2568)
- [Touch Screen কি জাতীয় ডিভাইস?](../written-answers/computer-fundamental.md?plain=1#L2590)
- [Distinguish between OMR and MICR.](../written-answers/computer-fundamental.md?plain=1#L2720)
- [Write down the difference between Serial Port and Parallel Port.](../written-answers/computer-fundamental.md?plain=1#L2285)

## ICT in Society & Governance

### The Fourth Industrial Revolution (IR 4.0)

The **Fourth Industrial Revolution (IR 4.0)**, a term popularised by **Klaus Schwab** of the World Economic Forum in 2016, is the current era in which **digital, physical and biological technologies fuse together**, driven by **cyber-physical systems**, the **Internet of Things**, **Artificial Intelligence** and **big data**.

#### The four industrial revolutions

| Revolution | Period | Driving technology | Key change |
|---|---|---|---|
| **IR 1.0** | ~1760–1840 | **Steam engine**, water power | Mechanisation; factories replace handicraft |
| **IR 2.0** | ~1870–1914 | **Electricity**, the assembly line | **Mass production** |
| **IR 3.0** | ~1960–2000 | **Computers, electronics, the Internet** | **Automation and digitisation** |
| **IR 4.0** | **2011 – present** | **AI, IoT, Big Data, Robotics, Cloud, Cyber-physical systems** | **Intelligent, connected, self-optimising systems** |

```mermaid
flowchart LR
    A["IR 1.0<br/>Steam<br/>Mechanisation"] --> B["IR 2.0<br/>Electricity<br/>Mass production"]
    B --> C["IR 3.0<br/>Computers<br/>Automation"]
    C --> D["IR 4.0<br/>AI + IoT + Data<br/>Intelligent systems"]
```

#### The key elements / technologies of IR 4.0

| # | Technology | What it contributes |
|---|---|---|
| 1 | **Artificial Intelligence & Machine Learning** | Machines that learn, predict and decide |
| 2 | **Internet of Things (IoT)** | Billions of sensors and devices connected and sharing data |
| 3 | **Big Data & Analytics** | Extracting value from enormous data volumes |
| 4 | **Cloud Computing** | On-demand, elastic computing power and storage |
| 5 | **Robotics & Automation** | Industrial robots, cobots, drones, RPA |
| 6 | **Cyber-Physical Systems** | Software controlling physical machines in real time |
| 7 | **3D Printing / Additive Manufacturing** | Made-to-order production, no moulds |
| 8 | **Blockchain** | Trust without a central authority |
| 9 | **Augmented / Virtual Reality (AR/VR)** | Immersive training, design and maintenance |
| 10 | **5G and advanced connectivity** | Ultra-low latency for real-time control |
| 11 | **Digital Twin** | A live virtual replica of a physical asset |
| 12 | **Quantum computing, Biotechnology, Nanotechnology** | The emerging frontier |
| 13 | **Cybersecurity** | The enabler without which none of the above is safe |

#### Characteristics of IR 4.0

1. **Interoperability** — machines, devices, sensors and people connect and communicate.
2. **Information transparency** — a virtual copy of the physical world built from sensor data.
3. **Technical assistance** — systems support humans in decisions and in physically difficult tasks.
4. **Decentralised decisions** — cyber-physical systems decide autonomously wherever possible.

#### Impact on Bangladesh — opportunities and challenges

**Opportunities**
- **Smart manufacturing** in the **RMG (garment) sector** — automated cutting, quality inspection by computer vision, predictive maintenance.
- **Precision agriculture** — soil sensors, drone spraying, crop-disease detection from leaf photos.
- **Digital financial services** — bKash, Nagad, agent banking, and the push for **financial inclusion**.
- **IT/ITES export and freelancing** — Bangladesh is among the world's largest suppliers of online freelancers.
- **Smart cities and e-governance** — traffic management, land records, citizen services.
- **Healthcare** — telemedicine, AI-assisted diagnosis in underserved districts.

**Challenges**
- **Job displacement**, especially in the labour-intensive RMG sector, which employs about 4 million people.
- **Skills gap** — the workforce needs reskilling in data, AI and automation.
- **Digital divide** between urban and rural, and between genders.
- **Weak infrastructure** — electricity reliability, rural broadband.
- **Cybersecurity and data-protection** readiness.
- **Investment cost** of automation for small and medium enterprises.

**Strategies:** invest in **STEM and vocational education**, build **industry-academia partnerships**, expand **broadband and reliable power**, enact strong **data-protection and cyber law**, provide **incentives for local innovation and start-ups**, and plan a **just transition** with reskilling for displaced workers.

**Previous Year Question List from this Topic:**

- [(ক) IR 4.0 বলতে কি বুঝায়? IR 4.0 এর গুরুত্বপূর্ণ উপাদানগুলো লিখুন।](../written-answers/computer-fundamental.md?plain=1#L1680)
- [৯. চতুর্থ শিল্প বিপ্লব কি? ইহার সম্পর্কে ৪ লাইন লিখুন।](../written-answers/computer-fundamental.md?plain=1#L1844)
- [বর্তমান যুগ চতুর্থ শিল্প বিপ্লবের যুগ। BREB ও সেই যুগের সাথে তালমিলিয়ে চলছে, মানুষের দ্বারপ্রান্তে বিদ্যুৎ সেবা পৌছে দেওয়ার জন্য। BREB এর এমন ৫টি পরিকল্পনা বা…](../written-answers/computer-fundamental.md?plain=1#L1877)
- [Discuss the impact of Artificial Intelligence and Automation on the banking sector of Bangladesh. What strategies should financial institutions adopt to balance…](../written-answers/computer-fundamental.md?plain=1#L1611)


---

### E-Governance and Digital Bangladesh

#### What is E-Government?

**E-Government (Electronic Government)** is the **use of ICT — especially the Internet — by government agencies to deliver services, information and transactions to citizens, businesses and other government bodies more efficiently, transparently and conveniently.**

> The goal is **SMART government**: **S**imple, **M**oral, **A**ccountable, **R**esponsive and **T**ransparent.

#### The four models of e-government

| Model | Meaning | Example |
|---|---|---|
| **G2C** — Government to Citizen | Services delivered to the public | Online birth registration, NID, passport application, e-Porcha (land records), result publication |
| **G2B** — Government to Business | Services to companies | Online tax and VAT filing, trade licence, e-tender (e-GP), company registration |
| **G2G** — Government to Government | Between agencies/departments | Inter-ministry file sharing, the **e-Nothi (e-file)** system |
| **G2E** — Government to Employee | Services to civil servants | Online payroll, pension, training, transfer and posting |

#### Benefits of e-government

1. **Transparency** — decisions and records are visible, which reduces the scope for corruption.
2. **Efficiency and speed** — a service that took weeks now takes minutes.
3. **Cost reduction** — less paper, less travel, fewer offices.
4. **24×7 accessibility** from anywhere, including from rural areas.
5. **Accountability** — every action is logged and auditable.
6. **Reduced harassment** — no middlemen, no repeated visits.
7. **Better decision making** through data.
8. **Citizen participation** — feedback, complaints, e-consultation.
9. **Environmental benefit** — a paperless office.

#### Digital Bangladesh

**Digital Bangladesh** was declared in **2008** as a core element of **Vision 2021**, aiming to use ICT to achieve middle-income status by the 50th anniversary of independence. It has since evolved into **"Smart Bangladesh" (Vision 2041)**, built on four pillars: **Smart Citizen, Smart Government, Smart Society and Smart Economy**.

**The four pillars of Digital Bangladesh:**

```mermaid
flowchart TD
    DB["DIGITAL BANGLADESH"]
    DB --> A["1 . Human Resource Development<br/>ICT-skilled citizens"]
    DB --> B["2 . Connecting Citizens<br/>affordable internet everywhere"]
    DB --> C["3 . Digital Government<br/>e-services & e-administration"]
    DB --> D["4 . ICT in Business<br/>e-commerce, IT industry, export"]
```

#### Factors needed to implement Digital Bangladesh

| Factor | Requirement |
|---|---|
| **Infrastructure** | Nationwide **broadband and mobile network**, submarine cable capacity, **reliable electricity**, data centres |
| **Human resources** | ICT-literate citizens, trained officials, skilled IT professionals |
| **Affordable devices and internet** | Low-cost smartphones and data so that the poor are not excluded |
| **Legal framework** | ICT Act, **Digital/Cyber Security Act**, Right to Information Act, data-protection law, e-signature law |
| **Government commitment & funding** | Sustained political will, budget allocation, a dedicated ICT Division |
| **Interoperability & standards** | Shared national databases, a single-sign-on identity, open standards |
| **Cybersecurity** | A national CERT, secure data centres, audit and compliance |
| **Digital literacy & awareness** | Citizens must know the services exist and how to use them |
| **Local content in Bangla** | Services and interfaces in the national language |
| **Public-private partnership** | Private sector innovation alongside government platforms |
| **Change management** | Officials must be willing to move from paper to digital processes |

#### Major e-government initiatives in Bangladesh

| Sector | Initiative |
|---|---|
| **General / citizen services** | **a2i (Aspire to Innovate)** programme, **Union Digital Centres (UDC)** in every union, the **National Portal**, **333 call centre**, **MyGov** app |
| **Identity & civil registration** | **Smart NID**, online **birth and death registration (BDRIS)**, e-passport, MRP |
| **Finance & revenue** | Online **VAT and income-tax return**, **e-GP (electronic government procurement)**, **iBAS++** budget system, challan (a-challan) |
| **Banking** | **BEFTN, RTGS, NPSB, BACH**, MFS (bKash, Nagad, Rocket), agent banking |
| **Land** | **e-Porcha**, e-Mutation, online land-development-tax payment |
| **Education** | Online **SSC/HSC results**, e-Book (all textbooks online), **Teachers' Portal**, **Muktopaath** e-learning, online university admission |
| **Health** | **Shastho Batayon 16263**, telemedicine, DGHS **Surokkha** vaccination portal, hospital MIS |
| **Agriculture** | **Krishi Call Centre 16123**, Agriculture Information Service, e-Krishi |
| **Judiciary** | e-Judiciary, online cause list, virtual courts |
| **Police / safety** | **Online GD**, National Emergency Service **999**, traffic e-challan |

#### E-government in health and education — specifics

**Health:** the **Shastho Batayon (16263)** 24-hour health call centre; **telemedicine** links in upazila health complexes; the **Surokkha** portal that managed nationwide COVID-19 vaccine registration and certificates; DHIS2-based health MIS; online doctor appointment and hospital automation.

**Education:** all national textbooks freely downloadable (**e-Book**); online publication of **public exam results**; the **Teachers' Portal** with 500,000+ members sharing digital content; **Muktopaath** free e-learning platform; **multimedia classrooms** in tens of thousands of schools; online university admission and BdREN (the research and education network).

**Previous Year Question List from this Topic:**

- [a) What is E-Government? How can E-Government be implemented through the vision of Digital Bangladesh?](../written-answers/computer-fundamental.md?plain=1#L1986)
- [b) List some factors that are needed to implement Digital Bangladesh.](../written-answers/computer-fundamental.md?plain=1#L2012)
- [c) Mention some government entities that have taken E-Government initiatives. What initiatives are taken by the Bangladesh Public Service Commission?](../written-answers/computer-fundamental.md?plain=1#L2030)
- [d) State the E-Government initiatives taken in health and education sectors of Bangladesh?](../written-answers/computer-fundamental.md?plain=1#L2055)
- [Describe in Bangali or English on the post COVID-19 social challenge that Bangladesh may can front end the way ICT can support to overcome them.](../written-answers/computer-fundamental.md?plain=1#L1724)


---

### E-Commerce and E-Business

#### What is E-Commerce?

**E-Commerce (Electronic Commerce)** is the **buying and selling of goods and services, and the transfer of funds or data, over an electronic network — primarily the Internet.**

#### Types of E-Commerce

| Type | Full form | Meaning | Example |
|---|---|---|---|
| **B2B** | Business to Business | One business sells to another | Alibaba; a garment factory buying fabric online |
| **B2C** | Business to Consumer | A business sells directly to the end consumer | **Daraz, Chaldal, Amazon, Rokomari** |
| **C2C** | Consumer to Consumer | Individuals sell to each other via a platform | **Bikroy.com**, eBay, OLX, Facebook Marketplace |
| **C2B** | Consumer to Business | An individual offers products/services to businesses | **Freelancer, Upwork, Fiverr**, stock-photo sellers |
| **B2G / B2A** | Business to Government | A business sells to government | **e-GP tenders** |
| **G2C** | Government to Consumer | Government charges/services online | Online tax and utility bill payment |
| **C2G** | Consumer to Government | Citizens pay government | e-challan, licence fees |

**Newer sub-types:** **F-commerce** (Facebook commerce), **M-commerce** (mobile commerce), **S-commerce** (social commerce), **D2C** (direct to consumer).

**E-commerce sites of Bangladesh:** **Daraz, Chaldal, Rokomari, Pickaboo, AjkerDeal, Bikroy, Evaly, Othoba, Foodpanda, Shohoz, Pathao**.

#### E-Commerce vs F-Commerce

| Point | **E-Commerce** | **F-Commerce (Facebook Commerce)** |
|---|---|---|
| **Platform** | A **dedicated website or app** | A **Facebook page / group / Instagram** |
| **Setup cost** | High — domain, hosting, development | **Almost zero** |
| **Technical skill needed** | Considerable | **Minimal** |
| **Payment** | Integrated gateway, cards, MFS | Usually **cash on delivery** or manual bKash |
| **Order management** | Automated cart, inventory, invoicing | **Manual** — via Messenger comments and chat |
| **Product catalogue** | Structured, searchable, filterable | Unstructured posts and albums |
| **Trust & regulation** | Registered business, trade licence, return policy | **Often unregistered**, weak buyer protection |
| **Customer reach** | Search engines + ads | **Social sharing and the Facebook algorithm** |
| **Scalability** | High | Limited — manual processes break down at volume |
| **Data & analytics** | Full control of customer data | Limited to what Facebook provides |
| **Best for** | Established businesses, large catalogues | **Micro-entrepreneurs, home-based and women entrepreneurs**, testing an idea |

> **Why F-commerce matters in Bangladesh:** it has become the entry point for **hundreds of thousands of micro-entrepreneurs, especially women**, who can start a business from home with a phone and no capital. Groups such as **"Women and e-Commerce Forum (WE)"** have enabled large numbers of women to earn independently. The weaknesses — no formal registration, no buyer protection, cash-on-delivery losses and no data ownership — are exactly why the government has pushed for **digital business identity (DBID)** registration.

#### E-Commerce vs E-Business

| Point | **E-Commerce** | **E-Business** |
|---|---|---|
| **Scope** | **Narrow** — commercial **transactions** only | **Wide** — **all** business processes done electronically |
| **Relationship** | **A SUBSET of e-business** | The superset |
| **Focus** | Buying, selling, payment | Buying/selling **plus** procurement, CRM, SCM, HR, production, accounting, internal collaboration |
| **Requires the Internet?** | ✅ Yes, essentially | Uses Internet, **intranet and extranet** |
| **Money involved?** | **Always** — it is about transactions | Not necessarily — much of it is internal process |
| **Example** | Buying a book on Rokomari | The **whole operation** of Rokomari: inventory, supplier ERP, staff portal, analytics, delivery routing |

#### Self-service strategy in e-commerce

E-commerce increases profit by shifting work **from the company's staff to the customer** — and the customer usually *prefers* it:

| Self-service element | Benefit to the company | Benefit to the customer |
|---|---|---|
| The customer **browses and searches** the catalogue | No salesperson cost | Browse at 2 a.m., compare freely |
| The customer **enters their own order and address** | No data-entry staff, **fewer errors** | Faster, in their own words |
| **Online payment** | No cashier, instant settlement | No cash handling |
| **Self-service order tracking** | Massive reduction in support calls | Instant answer, no waiting |
| **FAQ, knowledge base, chatbot** | One answer serves millions | Immediate help |
| **Customer reviews** | Free, credible content | Better buying decisions |
| **Automated recommendations** | **Increases basket size** — cross-selling with no salesperson | Discovers relevant products |

The net effect: **the marginal cost of serving one more customer falls towards zero**, which is why e-commerce can scale to millions of customers with a small team.

#### Traditional planning vs "sense and respond"

| Point | **Traditional business planning** | **Sense and Respond strategy** |
|---|---|---|
| **Assumption** | The future is **predictable**; the environment is stable | The future is **uncertain** and changes fast |
| **Planning horizon** | Long — 3 to 5 year plans | **Short cycles**, continuously revised |
| **Approach** | **Make and sell** — forecast demand, produce, then push to market | **Sense and respond** — detect what customers actually do, then adapt |
| **Data used** | Historical data, annual surveys | **Real-time data** — clicks, sales, sensors, social signals |
| **Structure** | Hierarchical, centralised | Networked, **decentralised**, empowered teams |
| **Inventory** | Large buffer stock (just in case) | **Just-in-time**, demand-driven |
| **Change** | Resisted; plans are executed as written | **Expected and embraced** |
| **Customer role** | Passive recipient | **Active participant** — reviews, customisation, co-creation |
| **Measure of success** | Meeting the plan | **Speed of adaptation** |
| **Enabled by** | — | ICT: real-time analytics, cloud, IoT, e-commerce platforms |

#### Advantages of using the Internet in a business organisation

1. **Global market reach** at low cost.
2. **24×7 operation** with no additional staff.
3. **Lower operating cost** — no shop rent, less paperwork, fewer intermediaries.
4. **Faster communication** — email, video conference, instant messaging.
5. **Direct marketing** and precise targeting; measurable advertising.
6. **Better customer service** — online support, self-service, feedback.
7. **Efficient supply chain** — online procurement, real-time tracking.
8. **Access to information** — market research, competitor analysis.
9. **Remote and flexible working.**
10. **Data-driven decisions** through web analytics.

#### Intranet, Extranet and legacy systems

| Term | Definition | Users |
|---|---|---|
| **Internet** | The global public network | Everyone |
| **Intranet** | A **private network inside one organisation**, using Internet technology (TCP/IP, web browsers) | **Employees only** |
| **Extranet** | An intranet **extended to selected outsiders** | Employees **+ suppliers, partners, key customers** |

> **How a legacy system is included in an intranet:** older systems (a COBOL mainframe, an old banking core) cannot simply be thrown away — they hold critical data and encode decades of business rules. They are integrated by placing a **middleware / wrapper layer** in front of them:
> 1. **Screen scraping / terminal emulation** — a web front end drives the legacy green-screen.
> 2. **API wrapper** — a modern **REST/SOAP web service** is written that calls the legacy program and returns JSON/XML.
> 3. **Middleware / Enterprise Service Bus (ESB)** — a message broker translates between systems.
> 4. **Database gateway** — the intranet application reads the legacy database directly through an ODBC/JDBC bridge.
> 5. **Batch synchronisation / ETL** — data is exported nightly into a modern database that the intranet uses.
>
> This gives employees a **single modern browser interface** while the proven legacy system keeps running underneath — the standard approach in banks and government.

**Previous Year Question List from this Topic:**

- [E-commerce ভিত্তিক ৪টি সাইটের নাম লিখুন?](../written-answers/computer-fundamental.md?plain=1#L1708)
- [E-commerce and F-commerce -এর মধ্যে পার্থক্য লিখুন। নারী গোষ্ঠী দ্বারা পরিচালিত F-Commerce -এর সামাজিক প্রভাব সম্বন্ধে লিখুন।](../written-answers/computer-fundamental.md?plain=1#L1801)
- [(ii) E-Commerce কী? E-Commerce-এর প্রকারভেদ উল্লেখ করুন। Search engine কী? এর কয়েকটি উদাহরণ দিন।](../written-answers/computer-fundamental.md?plain=1#L1895)
- [(a) Differentiate between e-commerce and e-business. How does e-commerce exploit self-serviced strategy to increase the market share?](../written-answers/computer-fundamental.md?plain=1#L2081)
- [(b) Distinguish between traditional business planning assumption and today’s sense and response strategy.](../written-answers/computer-fundamental.md?plain=1#L2110)
- [(c) Write down the advantages of using internet in business organization. How is legacy system included in intranet of an organization?](../written-answers/computer-fundamental.md?plain=1#L2132)
- [What is E-Commerce? What are the types of E-commerce?](../written-answers/computer-fundamental.md?plain=1#L2161)
- [Describe the transformative power of ICT with ten innovative applications for the online banking system.](../written-answers/computer-fundamental.md?plain=1#L1643)


---

### Information Systems — TPS, MIS and DSS

Organisations run a **hierarchy of information systems**, each serving a different management level.

```mermaid
flowchart TD
    A["EIS / ESS — Executive Support System<br/>Top management · strategic · external data"] --> B
    B["DSS — Decision Support System<br/>Middle/senior management · semi-structured · analytical"] --> C
    C["MIS — Management Information System<br/>Middle management · structured reports"] --> D
    D["TPS — Transaction Processing System<br/>Operational staff · day-to-day transactions"]
```

#### TPS — Transaction Processing System

Records and processes the **routine, day-to-day transactions** of the business. It is the **source of the raw data** that every higher system depends on.
*Examples:* ATM withdrawals, cheque clearing, sales at a POS terminal, payroll, order entry, ticket booking.

#### MIS — Management Information System

Converts TPS data into **summarised, structured, routine reports** that help **middle managers monitor and control** operations.
*Examples:* monthly branch-wise deposit report, weekly sales summary, inventory status report, quarterly profit statement.

#### DSS — Decision Support System

An **interactive, analytical** system that helps managers take **semi-structured or unstructured decisions** by running models, **what-if analyses** and simulations. It uses **both internal and external data**.
*Examples:* a loan-risk model, a "what if interest rates rise 2 %" simulation, branch-location analysis, portfolio optimisation, credit scoring.

#### MIS vs DSS — the key comparison

| Point | **MIS** | **DSS** |
|---|---|---|
| **Purpose** | **Monitoring and control** — "what happened?" | **Decision support** — "what should we do?" / "what if?" |
| **Decision type** | **Structured, routine** | **Semi-structured and unstructured** |
| **Users** | **Middle** management | **Middle and top** management, analysts |
| **Output** | **Fixed, periodic reports** (daily/weekly/monthly) | **Interactive, ad-hoc** analyses, models, simulations |
| **Data source** | Mainly **internal** (from TPS) | **Internal + EXTERNAL** (market, competitor, economic data) |
| **Flexibility** | **Low** — predefined formats | **High** — the user builds the query and the model |
| **Analytical capability** | Basic summarising, totalling | **Strong** — statistical models, optimisation, forecasting, what-if |
| **Orientation** | **Past** and present | **Present and FUTURE** |
| **User interaction** | Passive — read the report | **Active** — the manager drives the analysis |
| **Example** | "Branch-wise deposit report for March" | "If we open a branch in Sylhet, what is the projected 3-year return?" |

#### TPS vs DSS

| Point | **TPS** | **DSS** |
|---|---|---|
| **Level** | **Operational** | Management / strategic |
| **Purpose** | **Record** transactions accurately | **Support decisions** |
| **Data** | Detailed, current, internal | Summarised + external, historical and projected |
| **Volume** | **Very high** — thousands per second | Low — a few analyses per day |
| **Processing** | Repetitive, routine, high-speed | Analytical, model-based, ad-hoc |
| **Users** | Clerks, tellers, operators | Managers, analysts |
| **Requirement** | **Accuracy, reliability, speed, availability** | **Flexibility, modelling power** |
| **Example** | Recording a cash deposit at the counter | Deciding which customer segment to target for a new product |

#### The role of MIS in the banking sector

1. **Regulatory reporting** to Bangladesh Bank — CRR/SLR, CAMELS, capital adequacy, statutory returns.
2. **Branch performance monitoring** — deposits, advances, profitability by branch and product.
3. **Credit monitoring** — classified loans, NPL tracking, sector-wise exposure.
4. **Liquidity and treasury management** — daily cash position and fund flow.
5. **Customer analytics** — segmentation, product holding, churn risk, cross-sell targets.
6. **Fraud and AML monitoring** — flagging unusual transaction patterns.
7. **HR and payroll management** — staff productivity, training, transfers.
8. **Budgeting and cost control** — actual vs budget variance analysis.
9. **Audit trail and compliance** — every transaction traceable.
10. **Strategic planning support** — branch expansion, new product launch, ATM placement.

#### ERP — Enterprise Resource Planning

**ERP** is an **integrated software suite that manages all core business processes — finance, HR, manufacturing, supply chain, sales, procurement and inventory — through a SINGLE shared database**, so every department sees the same real-time data.

*Examples:* **SAP, Oracle ERP Cloud, Microsoft Dynamics 365, Odoo, Tally ERP.*

**Benefits:** one source of truth (no duplicate or conflicting data) · real-time visibility across departments · automated workflows · standardised processes · better reporting and compliance · lower long-run operating cost.

**Implementation challenges of ERP** *(a directly asked question)*

| # | Challenge | Explanation |
|---|---|---|
| 1 | **Very high cost** | Licences, hardware, consultants, training — often crores of taka, with cost overruns common |
| 2 | **Long implementation time** | 6 months to several years; business cannot wait |
| 3 | **Resistance to change** | Staff are comfortable with old methods and fear job loss or loss of control — **the single biggest cause of ERP failure** |
| 4 | **Business process re-engineering** | The organisation must often **change its processes to fit the ERP**, which is painful and political |
| 5 | **Data migration** | Cleaning, mapping and transferring decades of legacy data is error-prone and hugely underestimated |
| 6 | **Customisation trap** | Heavy customisation raises cost, delays the project and makes future upgrades very difficult |
| 7 | **Integration with existing systems** | Legacy and third-party systems must be interfaced |
| 8 | **Inadequate training** | Users who do not understand the system enter wrong data, destroying its value |
| 9 | **Lack of top-management commitment** | Without visible executive sponsorship the project loses priority and funding |
| 10 | **Choosing the wrong vendor or module set** | A poor fit with the industry's real needs |
| 11 | **Unclear requirements and scope creep** | Requirements keep expanding during the project |
| 12 | **Downtime risk during go-live** | Switching over is risky for a running business |

**Critical success factors:** strong **top-management sponsorship**, a **clear scope**, **phased rollout** rather than big-bang, thorough **change management and training**, **data cleansing before migration**, minimal customisation, and an experienced implementation partner.

**Previous Year Question List from this Topic:**

- [Comparison between MIS and DSS. What is the roles of MIS in Banking sector?](../written-answers/computer-fundamental.md?plain=1#L1772)
- [What is ERP? Write down the Implementation Challenges of ERP?](../written-answers/computer-fundamental.md?plain=1#L1856)
- [What is DSS? Write the difference between MIS and DSS.](../written-answers/computer-fundamental.md?plain=1#L2970)
- [Compare between TPS and DSS.](../written-answers/computer-fundamental.md?plain=1#L2995)


---

### Other ICT Topics — Copyright, RFID, Viral Video and Banking Software

#### Copyright law

**Copyright** is a legal right that gives the **creator of an original work exclusive control over its reproduction, distribution, adaptation and public display** for a limited period.

**What it protects:** literary works, music, films, photographs, paintings, **computer software and source code**, databases, architectural designs, website content.
**What it does NOT protect:** ideas, facts, methods, procedures and concepts — only their **particular expression**.

**In Bangladesh:** the **Copyright Act 2000** (amended 2005, and updated by the **Copyright Act 2023**), administered by the **Copyright Office** under the Ministry of Cultural Affairs. Protection generally lasts the **author's lifetime plus 60 years**. Registration is **not mandatory** — copyright exists automatically on creation — but registration provides strong legal evidence.

**Why copyright is necessary**

1. **Protects the creator's moral and economic rights** — the right to be credited and to be paid.
2. **Provides financial incentive** to create, invest and innovate.
3. **Prevents piracy and plagiarism**, which destroy the market for genuine work.
4. **Supports the software and creative industries** — without it, no one would invest in developing software locally.
5. **Encourages the growth of culture, literature, music and film.**
6. **Enables licensing** — a legal framework for selling and sharing work (including **open-source licences**, which are built on copyright).
7. **Attracts foreign investment** — companies will not bring technology to a country that cannot protect it.
8. **Balances public interest** through **fair use/fair dealing** for education, research, criticism and news reporting.

*(Related rights: **patent** protects inventions; **trademark** protects brand names and logos; **trade secret** protects confidential business information.)*

#### RFID — Radio Frequency Identification

**RFID** uses **radio waves** to automatically identify and track objects carrying a **tag**, without needing line of sight or physical contact.

**Components:** a **tag** (a microchip + antenna, attached to the object), a **reader** (transmits a radio signal and receives the tag's reply), an **antenna**, and **middleware/software** that interprets the data.

```mermaid
flowchart LR
    T["RFID TAG<br/>chip + antenna<br/>on the product"] -->|"radio signal<br/>with the unique ID"| R["RFID READER<br/>+ antenna"]
    R -->|"ID + timestamp + location"| M["Middleware / Software"]
    M --> D[("Database<br/>ERP / WMS")]
    R -.->|"energising signal"| T
```

| Type | Power | Range |
|---|---|---|
| **Passive tag** | No battery — powered by the reader's signal | Up to ~10 m |
| **Active tag** | Has its own battery | Up to ~100 m |
| **Semi-passive** | Battery for the chip, reader powers the transmission | Medium |

**RFID in supply chain management**

1. **Automatic goods receipt** — a whole pallet is read in one pass, no unpacking, no barcode scanning of each item.
2. **Real-time inventory visibility** — instantly know what is on which shelf in which warehouse.
3. **Track and trace** from factory → warehouse → truck → shop → customer.
4. **Anti-counterfeiting** — each unique tag proves authenticity.
5. **Automatic reordering** when stock falls below a threshold.
6. **Reduced shrinkage and theft**; **loss prevention** at exits.
7. **Cold-chain monitoring** — sensor tags record temperature for pharmaceuticals and food.
8. **Faster checkout** — an entire basket is read at once.

**RFID in toll collection (ETC — Electronic Toll Collection)**

```mermaid
flowchart LR
    V["Vehicle with an<br/>RFID tag on the windscreen"] --> G["Toll gantry antenna<br/>reads the tag at speed"]
    G --> S["Central system<br/>identifies the account"]
    S --> B["Toll amount DEDUCTED<br/>from the prepaid account"]
    B --> O["Barrier opens / no barrier at all<br/>the vehicle does not stop"]
    S --> N["SMS / app notification<br/>to the vehicle owner"]
```

**Benefits:** no stopping, so **no queues and no congestion** · lower fuel consumption and emissions · no cash handling, so **no leakage or corruption** · complete audit trail of every transaction · lower manpower cost · reliable traffic data for planning.
*(Examples: the Padma Bridge and Dhaka Elevated Expressway ETC systems, India's FASTag, and E-ZPass in the USA.)*

**RFID vs Barcode**

| Point | **RFID** | **Barcode** |
|---|---|---|
| **Line of sight** | ❌ **Not needed** | ✅ **Required** |
| **Read at once** | **Hundreds** of tags simultaneously | **One** at a time |
| **Range** | Up to 100 m | A few centimetres |
| **Data storage** | Read/write, kilobytes | Read-only, a few characters |
| **Durability** | Works through dirt, paint, packaging | Fails if smudged or torn |
| **Unique per item?** | ✅ Yes — each tag has a unique ID | ❌ No — identifies the *product type* only |
| **Cost** | **Higher** | **Very low** |

#### Viral video

A **viral video** is a video that **spreads extremely rapidly and widely across the internet**, mainly through **social media sharing** rather than through paid advertising, reaching a very large audience in a short time.

**Characteristics:** short and instantly understandable; strong **emotional trigger** (humour, surprise, inspiration, outrage); highly **relatable** or topical; easy to share; and often boosted by an algorithm once early engagement is strong.

**Three advantages of a viral video:**
1. **Enormous reach at almost zero cost** — organic sharing replaces an advertising budget.
2. **Rapid brand awareness and credibility** — a recommendation from a friend carries far more trust than an advertisement.
3. **High engagement and conversion** — viewers watch, comment and act; for a business this drives sales, and for a cause it drives awareness and donations.

*(Other benefits: SEO value, media coverage, and an audience the creator keeps afterwards. The risks: it is **unpredictable**, the attention is **short-lived**, and content can go viral for the **wrong** reasons, damaging reputation.)*

#### Banking software used in Bangladesh

| Type | Examples |
|---|---|
| **Core banking solutions (CBS)** | **Temenos T24, Flexcube (Oracle FLEXCUBE), Finacle (Infosys), BankUltimus (Leads), Ababil (Millennium — Islamic banking), Stelar, Kastle, Bexibank** |
| **Payment / settlement** | **BACH, BEFTN, RTGS, NPSB**, SWIFT |
| **Mobile financial services** | **bKash, Nagad, Rocket, Upay, SureCash** |
| **Card management** | Cardpro, Way4, Euronet |
| **AML / compliance** | goAML, Oracle Mantas, in-house AML engines |
| **ERP / HR** | SAP, Oracle, in-house HRMS |

**Essential features of good banking software**

1. **Core banking (CBS)** — accounts, deposits, loans, GL, with **any-branch banking**.
2. **Real-time processing** and **24×7 availability**.
3. **Multi-channel access** — branch, ATM, POS, internet banking, mobile app, agent banking.
4. **Robust security** — encryption, **MFA**, role-based access, audit trail, fraud detection.
5. **Regulatory compliance and reporting** — Bangladesh Bank returns, **AML/CFT, KYC/eKYC**, Basel III.
6. **Scalability and high availability** — clustering, **disaster recovery site**, 99.99 % uptime.
7. **Integration/API layer** — connects to BACH, BEFTN, NPSB, MFS, SWIFT, credit bureau.
8. **MIS and analytics dashboards** for management.
9. **Parameterisation** — new products configurable without code changes.
10. **Bangla language support** and localisation.
11. **Complete audit trail** — every transaction traceable to a user and terminal.
12. **Backup, recovery and business continuity**.

**Previous Year Question List from this Topic:**

- [What do you mean by viral video? List three advantages of viral vedio.](../written-answers/computer-fundamental.md?plain=1#L1663)
- [Copyright আইন কি? এর প্রয়োজনীয়তা ব্যাখ্যা করুন।](../written-answers/computer-fundamental.md?plain=1#L1748)
- [১৪. বাংলাদেশের প্রথম ভিডিও লাইভ শেয়ারিং অ্যাপস কোনটি?](../written-answers/computer-fundamental.md?plain=1#L1836)
- [Make a list of banking software used in Bangladesh. List the essential features for successful Banking Software and Apps.](../written-answers/computer-fundamental.md?plain=1#L1920)
- [RFID has huge applications in business, especially in supply chain management and toll collection system. Show the basic working principle of RFID in brief.](../written-answers/computer-fundamental.md?plain=1#L1951)


---

### Digital Banking and Electronic Payment Systems

#### What is digital banking?

**Digital banking** is the **delivery of banking products and services through digital channels — internet, mobile app, ATM, POS and agent points — with end-to-end digitisation of processes**, so that a customer can complete almost any banking task **without visiting a branch**.

#### Digital banking vs traditional banking

| Point | **Traditional Banking** | **Digital Banking** |
|---|---|---|
| **Service point** | A **physical branch** | **Anywhere** — phone, computer, agent point |
| **Timing** | **Banking hours** (10 a.m.–4 p.m., weekdays) | **24 × 7 × 365** |
| **Process** | **Paper forms**, manual signature, physical verification | Digital forms, **e-KYC**, OTP, biometric |
| **Speed** | Slow — queues, multiple visits | **Instant** |
| **Account opening** | Visit the branch with documents | **e-KYC** in minutes from home |
| **Fund transfer** | Cheque, pay order, counter | **Instant** — BEFTN, RTGS, NPSB, MFS |
| **Operating cost per transaction** | **Very high** — staff, rent, paper | **A fraction** of it |
| **Geographic reach** | Limited by branch network | **Nationwide**, including remote areas |
| **Staff needed** | Large | Small, focused on complex cases |
| **Record keeping** | Physical ledgers and files | **Digital, searchable, auditable** |
| **Customer relationship** | **Face to face**, personal | Digital, data-driven, less personal |
| **Risk** | Physical theft, forgery, human error | **Cyber fraud, phishing**, system failure |
| **Accessibility for the unbanked** | Poor — a branch is far away | **Excellent** — an agent or a mobile phone is nearby |

#### How digital banking promotes financial inclusion

**Financial inclusion** means ensuring that **everyone, especially the poor and rural population, has access to affordable, useful financial services** — an account, payments, savings, credit and insurance.

| # | Mechanism | Explanation |
|---|---|---|
| 1 | **Reach without branches** | **Agent banking** and **MFS** put a financial access point in every village; building a branch there would never be viable |
| 2 | **Drastically lower cost** | A digital transaction costs a small fraction of a branch transaction, so **small-value accounts become profitable** to serve |
| 3 | **Simplified onboarding** | **e-KYC with the NID and a photo** lets someone with no documents beyond an NID open an account in minutes |
| 4 | **Low minimum balance** | Digital accounts (e.g. the 10-taka farmer's account) remove the entry barrier |
| 5 | **Remittance delivery** | Migrant workers' remittances reach families directly and instantly, with government incentives applied automatically |
| 6 | **Government-to-Person (G2P) payments** | Social safety-net allowances, stipends, pensions and relief go **directly into the beneficiary's account**, removing leakage and middlemen |
| 7 | **Alternative credit scoring** | Mobile wallet and transaction history creates a **digital footprint** that lets the previously "invisible" borrow — **nano-loans** |
| 8 | **Women's empowerment** | A woman can hold and control her own account on her own phone, without a male escort to the branch |
| 9 | **Merchant payments** | Small shops accept digital payment, join the formal economy and become creditworthy |
| 10 | **Savings and insurance products** | Micro-savings and micro-insurance become deliverable at scale |
| 11 | **Transparency** | Every transaction is recorded, reducing corruption and building trust |

**The Bangladesh evidence:** **bKash, Nagad and Rocket** together serve well over 100 million registered accounts; **agent banking** operates tens of thousands of outlets, a majority in rural areas; and government stipends and COVID-19 relief were disbursed digitally to millions of households.

**The remaining barriers:** digital and financial **literacy**, smartphone and internet **affordability**, **network coverage** gaps, **trust and fraud** concerns, **cash-out costs**, and the **gender gap** in phone ownership.

#### Electronic Payment System (EPS)

An **Electronic Payment System** is a system that allows **payment for goods and services to be made electronically — without physical cash or cheques — by transferring value between accounts over a network.**

```mermaid
flowchart LR
    C["CUSTOMER<br/>(Payer)"] -->|"1 . initiates payment"| PG["PAYMENT GATEWAY<br/>encrypts & forwards"]
    PG -->|"2 . authorisation request"| PS["PAYMENT PROCESSOR /<br/>Card network (VISA, Mastercard)"]
    PS -->|"3 . verify funds"| IB["ISSUING BANK<br/>(customer's bank)"]
    IB -->|"4 . approve / decline"| PS
    PS -->|"5 . response"| PG
    PG -->|"6 . confirmation"| M["MERCHANT<br/>(Payee)"]
    IB -->|"7 . SETTLEMENT of funds"| AB["ACQUIRING BANK<br/>(merchant's bank)"]
    AB -->|"8 . credit"| M
```

**The five main types of EPS:**

| # | Type | Description | Example |
|---|---|---|---|
| 1 | **Card-based payment** | Debit, credit and prepaid cards used at **POS, ATM or online** | VISA, Mastercard, AMEX; a local debit card |
| 2 | **Mobile Financial Services / e-Wallet** | Value held in a mobile account, used by phone | **bKash, Nagad, Rocket, Upay**; PayPal, Apple Pay |
| 3 | **Internet / Online banking transfer** | Direct account-to-account transfer through a bank's portal | **BEFTN, RTGS, NPSB**, NEFT |
| 4 | **Electronic cheque / Electronic Funds Transfer (EFT)** | The cheque or instruction is cleared electronically | **BACH** cheque truncation, direct debit, standing order |
| 5 | **Digital / Crypto currency** | Value transferred on a distributed ledger or as central-bank digital currency | Bitcoin, stablecoins, **CBDC** |

*(Others worth naming: **QR-code payment**, **contactless/NFC**, **biometric payment**, and **BNPL — Buy Now Pay Later**.)*

**Advantages of EPS:** speed (instant settlement) · convenience and 24×7 availability · **lower transaction cost** · **complete transaction record** for accounting and tax · reduced cash-handling risk · enables e-commerce · supports financial inclusion · reduces the cost of printing and moving currency notes.

**Challenges:** **cyber fraud and phishing** · dependence on internet and power · **digital literacy** · transaction and interchange fees · **privacy concerns** over transaction data · system downtime · the **unbanked** without any account · and regulatory/AML compliance burden.

**Previous Year Question List from this Topic:**

- [Discuss the impact of Artificial Intelligence and Automation on the banking sector of Bangladesh. What strategies should financial institutions adopt to balance…](../written-answers/computer-fundamental.md?plain=1#L1611)
- [Describe the transformative power of ICT with ten innovative applications for the online banking system.](../written-answers/computer-fundamental.md?plain=1#L1643)
- [What is digital banking and how does it differ from traditional banking? How can digital banking promote financial inclusion?](../written-answers/computer-fundamental.md?plain=1#L3823)
- [(a) Define Electronic Payment System (EPS) with necessary diagram. Name 5 types of EPS.](../written-answers/computer-fundamental.md?plain=1#L3859)


---

## Quantum Computing & Emerging Technologies

### Quantum Computing

**Quantum computing** uses the principles of **quantum mechanics** — superposition, entanglement and interference — to process information in a fundamentally different way from classical computers.

#### The qubit

A classical computer stores a **bit**, which is **either 0 or 1**. A quantum computer stores a **qubit**, which can be **0, 1, or BOTH AT THE SAME TIME** (a *superposition*).

| Concept | Meaning | Consequence |
|---|---|---|
| **Superposition** | A qubit holds 0 and 1 simultaneously, with probabilities | **n qubits represent 2ⁿ states at once** — 300 qubits exceed the number of atoms in the observable universe |
| **Entanglement** | Two qubits become correlated so that measuring one instantly determines the other, however far apart | Enables massively parallel correlated computation |
| **Interference** | Probability amplitudes add and cancel | Algorithms are designed so that **wrong answers cancel out** and the right answer is amplified |
| **Measurement** | Observing a qubit **collapses** it to a definite 0 or 1 | You get one answer, so algorithms must be designed around probability |

#### Classical vs Quantum computing

| Point | **Classical Computer** | **Quantum Computer** |
|---|---|---|
| **Basic unit** | **Bit** (0 **or** 1) | **Qubit** (0 **and** 1 simultaneously) |
| **States of n units** | **One** of 2ⁿ | **All 2ⁿ** at once |
| **Operations** | Boolean logic gates (AND, OR, NOT) | **Quantum gates** (Hadamard, CNOT, Pauli-X) — reversible |
| **Processing** | Sequential / limited parallelism | **Massively parallel** by nature |
| **Error rate** | Very low | **Very high** — needs constant error correction |
| **Operating conditions** | Room temperature | **Near absolute zero (−273 °C)**, shielded from all vibration and radiation |
| **Best at** | Everyday tasks, arithmetic, databases, graphics | **Specific hard problems** — factoring, simulation, optimisation, search |
| **Maturity** | Fully mature | **Experimental / early commercial** |

#### Importance and applications

1. **Drug discovery and chemistry** — simulating molecules exactly, which is intractable classically. The most promising application.
2. **Materials science** — designing superconductors, better batteries, catalysts.
3. **Cryptography** — **Shor's algorithm** can factor large numbers efficiently, which would **break RSA and ECC encryption**. This is why the world is moving to **post-quantum cryptography**.
4. **Optimisation** — logistics, routing, portfolio optimisation, scheduling, supply chains.
5. **Search** — **Grover's algorithm** searches an unsorted database in **O(√N)** instead of O(N).
6. **Machine learning** — quantum ML may speed up training on certain problems.
7. **Weather and climate modelling**; **financial risk simulation**.

#### Disadvantages and limitations

| # | Limitation | Explanation |
|---|---|---|
| 1 | **Decoherence** | Qubits lose their quantum state in **microseconds** from the slightest heat, vibration or electromagnetic noise |
| 2 | **High error rates** | Quantum gates are far less reliable than classical ones; **error correction** may need 1,000 physical qubits per useful logical qubit |
| 3 | **Extreme operating conditions** | Dilution refrigerators near **absolute zero**; enormous cost and power |
| 4 | **Very expensive** | Tens of millions of dollars per machine; only large labs and cloud providers have them |
| 5 | **Not general purpose** | **Slower than a laptop** for ordinary tasks — it only wins on specific problem classes |
| 6 | **Few algorithms** | Only a handful of quantum algorithms with proven advantage exist |
| 7 | **Scalability** | Current machines have hundreds to a few thousand noisy qubits; millions are needed for most useful work |
| 8 | **Security threat** | It threatens to break the encryption that currently protects banking, government and the internet |
| 9 | **Shortage of expertise** | Requires deep knowledge of quantum physics *and* computer science |
| 10 | **Probabilistic output** | Results are statistical; the computation must be repeated many times |

*(Leading players: **IBM Quantum, Google (Sycamore/Willow), Microsoft Azure Quantum, D-Wave, IonQ, Rigetti**.)*

**Previous Year Question List from this Topic:**

- [কোয়ান্টাম কম্পিউটিং কি? এর গুরুত্ব এবং অসুবিধাগুলো কি কি? সংক্ষেপে আলোচনা করুন।](../written-answers/computer-fundamental.md?plain=1#L3750)


---

### Virtual Reality, Augmented Reality and Nanotechnology

#### Virtual Reality (VR)

**Virtual Reality** is a computer-generated **simulation of a three-dimensional environment** that **completely replaces** the user's view of the real world, and with which the user can **interact** in a seemingly real way using special equipment.

**How it works:** a **head-mounted display (HMD)** shows a slightly different image to each eye to create **stereoscopic depth**; **motion sensors and head tracking** update the view as the user moves; **hand controllers, gloves or haptic suits** allow interaction; and **3-D spatial audio** completes the illusion. The key requirements are a **wide field of view**, **high frame rate** and **very low latency** — otherwise the user experiences motion sickness.

**Devices:** Meta Quest, HTC Vive, PlayStation VR, Valve Index, Apple Vision Pro.

**Applications**

| Sector | Use |
|---|---|
| **Education & training** | Virtual laboratories, historical site tours, virtual field trips |
| **Medicine** | **Surgical training and rehearsal**, phobia and PTSD therapy, physiotherapy |
| **Military & aviation** | **Flight simulators**, combat and equipment training — safe and cheap |
| **Engineering & architecture** | Walking through a building before it is built; design review |
| **Gaming & entertainment** | Immersive games, virtual concerts, 360° film |
| **Real estate & tourism** | Virtual property tours and destination previews |
| **Industry** | Assembly training, remote maintenance guidance, **digital twins** |
| **Retail** | Virtual showrooms and try-before-you-buy |

**Advantages:** safe practice of dangerous tasks · huge cost saving on physical prototypes and travel · far better retention than passive learning · access to places and situations otherwise impossible.
**Disadvantages:** expensive hardware · **motion sickness and eye strain** · social isolation and addiction risk · content is costly to produce · requires powerful computing.

#### VR vs AR vs MR

| Point | **Virtual Reality (VR)** | **Augmented Reality (AR)** | **Mixed Reality (MR)** |
|---|---|---|---|
| **Environment** | **Fully virtual** — the real world is replaced | **Real world + digital overlay** | Real and virtual objects **interact** |
| **Immersion** | **Complete** | Partial | High |
| **Device** | Headset (HMD) | **Smartphone, tablet, smart glasses** | HoloLens, Magic Leap, Vision Pro |
| **User awareness of reality** | ❌ Blocked out | ✅ Fully aware | ✅ Aware |
| **Example** | A VR flight simulator | **Pokémon GO**, Google Lens, an IKEA app placing furniture in your room, Snapchat filters | A holographic engine you can walk around and take apart |

#### Nanotechnology and molecular computing

**Nanotechnology** is the manipulation of matter at the scale of **1 to 100 nanometres** (a nanometre is one billionth of a metre — roughly 1/80,000 of the width of a human hair). At that scale, materials show entirely different physical, chemical and electrical properties.

> ### "What is the name of a molecular-scale computer?"
> A **MOLECULAR COMPUTER** — also called a **nanocomputer**, and in its best-known biological form a **DNA computer**.
>
> Instead of silicon transistors, it uses **individual molecules** (or strands of DNA) as the switching and storage elements. **Leonard Adleman** demonstrated the first DNA computer in 1994 by solving a small Hamiltonian-path problem with DNA strands in a test tube.
>
> **Why it is interesting:** molecules are **astronomically dense** (a gram of DNA could in principle store more data than every hard disk ever made) and **massively parallel** (trillions of molecules react at once), while consuming very little energy. **Why it is not practical yet:** it is extremely **slow to read results**, error-prone, and difficult to program or reuse.

**Applications of nanotechnology in computing:** ever-smaller transistors (modern chips are built at the **3–5 nanometre** node); **carbon nanotube** and **graphene** transistors as a successor to silicon; **nano-memory** with far higher density; **quantum dots** for displays and qubits; and better heat dissipation.

**Other applications:** targeted **drug delivery**, cancer treatment, water purification, stronger and lighter materials, self-cleaning and stain-resistant fabrics, more efficient solar cells and batteries.

**Previous Year Question List from this Topic:**

- [What is the name of molecular scale computer?](../written-answers/computer-fundamental.md?plain=1#L3778)
- [Virtual Reality বলতে কি বুঝায় ব্যাখ্যা করুন।](../written-answers/computer-fundamental.md?plain=1#L3792)

## Hardware Components & BIOS (CMOS Battery)

### BIOS, CMOS, UEFI and the Boot Process

#### What is BIOS?

**BIOS (Basic Input Output System)** is **firmware** — permanent low-level software stored on a **chip on the motherboard** — that is the **very first program a computer runs when it is switched on**. It initialises and tests the hardware, then loads the operating system.

> **BIOS is the bridge between the hardware and the operating system.** Without it, the CPU would power on with no idea what hardware exists or where to find the OS.

#### The four functions of BIOS

| # | Function | Description |
|---|---|---|
| 1 | **POST — Power On Self Test** | Checks that the CPU, RAM, keyboard, graphics and storage are present and working. Failures are reported by **beep codes** |
| 2 | **Bootstrap loader** | Finds the **boot device**, loads the **boot loader** from it, and hands over control |
| 3 | **BIOS drivers / firmware** | Provides basic low-level control of the hardware before the OS drivers load |
| 4 | **BIOS Setup (CMOS Setup)** | The configuration utility (entered with Del/F2) for boot order, date/time, passwords, overclocking |

#### The boot process of a PC — step by step

```mermaid
flowchart TD
    A["1 . POWER ON<br/>the PSU sends the 'Power Good' signal"] --> B["2 . CPU jumps to the RESET VECTOR<br/>(a fixed address in the BIOS ROM)"]
    B --> C["3 . POST — Power On Self Test<br/>checks CPU, RAM, graphics, keyboard, storage"]
    C --> D{"Hardware<br/>OK ?"}
    D -->|No| E["❌ Error beep codes<br/>or an error message; boot halts"]
    D -->|Yes| F["4 . BIOS reads its settings from CMOS<br/>(date, time, boot order, hardware config)"]
    F --> G["5 . BIOS initialises hardware<br/>and displays the system summary"]
    G --> H["6 . BIOS searches the BOOT ORDER<br/>for a bootable device"]
    H --> I["7 . Reads the MBR / GPT — the first sector —<br/>and loads the BOOT LOADER into RAM"]
    I --> J["8 . The boot loader (GRUB / Windows Boot Manager)<br/>loads the OS KERNEL"]
    J --> K["9 . The kernel initialises drivers,<br/>services and the file system"]
    K --> L["10 . Login screen / desktop — the OS is in control"]
```

**The stages in words**

1. **Power on.** The power supply stabilises and sends a **"Power Good"** signal; the CPU comes out of reset.
2. **The CPU executes the first instruction from the BIOS ROM** at the reset vector.
3. **POST** runs, verifying essential hardware. A **single short beep** usually means success; a pattern of beeps identifies the fault (e.g. repeated beeps = RAM failure).
4. **BIOS reads its saved configuration from CMOS memory** — date, time, boot sequence, enabled devices.
5. **Hardware initialisation** — the video card first (so messages can be displayed), then drives and peripherals.
6. **The boot device is selected** by following the configured **boot order** (SSD → USB → network).
7. **The Master Boot Record (MBR, sector 0)** or the **GPT/EFI System Partition** is read and the **boot loader** is loaded into RAM.
8. **The boot loader** (GRUB on Linux, Windows Boot Manager on Windows) loads the **OS kernel**.
9. **The kernel** takes control, initialises memory management, drivers, and mounts the file system.
10. **Services and the user interface** start; the login screen appears.

#### What is CMOS, and the CMOS battery

**CMOS (Complementary Metal Oxide Semiconductor)** is a small amount of **volatile RAM on the motherboard** that stores the **BIOS settings and the real-time clock**. Because it is volatile, it needs constant power — supplied by the **CMOS battery**, a coin cell, usually a **CR2032 (3 V lithium)**.

**Performance and lifetime of the CMOS battery**

| Aspect | Detail |
|---|---|
| **Type** | Coin-cell lithium, usually **CR2032, 3 volts** |
| **Typical life** | **3 to 10 years** (commonly 5) |
| **Power drawn** | Only a few microamps — it only runs the clock and holds the settings when the machine is off |
| **Drains faster if** | The computer is **left unplugged for long periods** (when mains power is present, the board powers the CMOS instead), or in high-temperature environments |

**Symptoms of a failing/dead CMOS battery:**
1. **The date and time reset** to a default (e.g. 01/01/2000) on every boot — *the classic symptom*.
2. **"CMOS checksum error"** or **"CMOS battery failure"** message at startup.
3. BIOS settings (boot order, RAID mode) **revert to default** each time.
4. **Boot failure or a slow boot** because the boot order changed.
5. Hardware such as a drive appearing "missing".
6. **SSL/HTTPS certificate errors and failed software licence checks**, because the system clock is wrong.
7. On a **server**, log timestamps become wrong, breaking scheduled jobs, backups and forensic analysis.

**The fix:** replace the CR2032 (a few taka, two minutes' work), then re-enter the BIOS and set the date, time and boot order.

#### BIOS vs CMOS — the comparison

| Point | **BIOS** | **CMOS** |
|---|---|---|
| **What it is** | **Firmware — a PROGRAM** | **Memory — a CHIP that stores data** |
| **Function** | **Runs** the POST and boots the machine | **Stores** the BIOS settings and the clock |
| **Storage type** | **Non-volatile** — ROM / Flash EEPROM | **Volatile** — needs the battery |
| **Retains data without power?** | ✅ **Yes** | ❌ **No** — only while the battery lasts |
| **Size** | A few MB | A few hundred **bytes** |
| **Battery needed?** | ❌ No | ✅ **Yes — the CMOS battery** |
| **If it fails** | The machine cannot boot at all (requires reflashing) | Settings and time are lost, but the machine still boots |

> **The relationship in one line:** **BIOS is the program; CMOS is the notebook where that program keeps its settings; the CMOS battery is what keeps the notebook readable when the power is off.**

#### BIOS vs UEFI

**UEFI (Unified Extensible Firmware Interface)** is the **modern replacement for the legacy BIOS**, standard on all machines since roughly 2012.

| Point | **Legacy BIOS** | **UEFI** |
|---|---|---|
| **Introduced** | 1975 (IBM PC era) | 2005 onward; standard since ~2012 |
| **Operating mode** | **16-bit real mode** | **32-bit or 64-bit** |
| **Addressable memory during boot** | **1 MB** | Effectively unlimited |
| **Partition scheme** | **MBR** | **GPT** (and MBR for compatibility) |
| **Maximum disk size** | **2 TB** | **9.4 ZB** (zettabytes) |
| **Maximum primary partitions** | **4** | **128** |
| **Interface** | Text-only, keyboard only | **Graphical, mouse support, multi-language** |
| **Boot speed** | Slower | **Faster** — parallel initialisation, **Fast Boot** |
| **Security** | ❌ None | ✅ **Secure Boot** — only signed boot loaders may run, blocking bootkits/rootkits |
| **Network capability** | Very limited | Built-in networking, **remote diagnostics and update** |
| **Drivers** | Firmware-only | Modular, extensible **UEFI drivers and applications** |
| **Extensibility** | Fixed | **Extensible** — a shell and applications can run pre-OS |

#### BIOS/UEFI in servers, and firmware vs boot loader

On a **server**, the firmware layer matters far more than on a desktop, because it controls **RAID configuration, boot order across many drives, virtualisation extensions (VT-x/AMD-V), memory mirroring, power profiles and remote management**. Server boards add an out-of-band management controller — **iDRAC (Dell), iLO (HP), IMM (IBM/Lenovo)** — which lets an administrator power-cycle, reconfigure the BIOS and mount installation media **remotely, even when the OS is dead**. Firmware settings therefore directly affect **boot reliability, virtualisation support, performance and maintenance windows**.

| Term | Meaning |
|---|---|
| **Firmware** | Permanent low-level software stored in a hardware device's own ROM/flash, controlling that device. **BIOS/UEFI is firmware**; so is the firmware in a router, SSD, printer or smartphone |
| **Boot loader** | A small **program stored on the DISK** whose only job is to **load the operating system kernel** into memory and start it. Examples: **GRUB, LILO, Windows Boot Manager, U-Boot** |

| Point | **Firmware (BIOS/UEFI)** | **Boot loader (GRUB etc.)** |
|---|---|---|
| **Stored in** | A **chip on the motherboard** | **The disk** (MBR / EFI System Partition) |
| **Runs** | **First**, at power-on | **Second**, after the firmware hands over |
| **Job** | Initialise and test **hardware**, find a boot device | Find and load the **OS kernel**; offer a boot menu |
| **Hardware/OS specific** | Hardware specific | OS specific |
| **Updated by** | Flashing the chip | Reinstalling/reconfiguring the OS |

**Previous Year Question List from this Topic:**

- [Performance of CMOS battery?](../written-answers/computer-fundamental.md?plain=1#L2190)
- [(c) Explain the rule of BIOS (Basic Input Output System) in the boot process of a PC. Describe the steps involved in booting a computer from power on to loading…](../written-answers/computer-fundamental.md?plain=1#L2212)
- [Explain BIOS in Server. How does affect booting configuration in Hardware maintenance.](../written-answers/computer-fundamental.md?plain=1#L2249)
- [What is BIOS?](../written-answers/computer-fundamental.md?plain=1#L2272)
- [What is BIOS?](../written-answers/computer-fundamental.md?plain=1#L2372)
- [What is the difference between UEFI and BIOS?](../written-answers/computer-fundamental.md?plain=1#L2456)
- [Write the difference between BIOS and CMOS?](../written-answers/computer-fundamental.md?plain=1#L2529)
- [Difference between BIOS and EFI also BOOT loader and firmware.](../written-answers/computer-fundamental.md?plain=1#L2660)


---

### Input and Output Devices

#### Classification

| Category | Devices |
|---|---|
| **Input** | Keyboard, mouse, scanner, microphone, webcam, joystick, light pen, **barcode reader, OMR, OCR, MICR**, biometric/fingerprint reader, digitiser/graphics tablet, sensors |
| **Output** | **Monitor**, printer, **plotter**, speaker, projector, headphone |
| **Both (I/O)** | **Touch screen**, modem, network card, hard disk, USB drive, headset (mic + speaker), multifunction printer |

> ### "Is a touch screen an input or an output device?"
> **BOTH.** It **displays** information (output, as a monitor) and **accepts** the user's finger or stylus input (input). It is therefore classified as an **input-output (I/O) device**, and is the standard example of one.

> ### "What kind of device is a plotter?"
> An **OUTPUT device** — specifically a **hard-copy graphics output device** that draws continuous **lines** by moving a pen (or an ink head) across the paper, rather than printing dots. It is used for **large, precise line drawings**: engineering and architectural blueprints, maps, circuit diagrams and CAD output. Types: **drum plotter, flatbed plotter, inkjet plotter, electrostatic plotter**.

#### Printers

| Category | Type | How it works | Quality / Speed |
|---|---|---|---|
| **Impact** | **Dot matrix** | A **print head carrying a matrix of pins/needles** strikes an **inked ribbon** against the paper | Low quality, noisy, **cheap running cost**; the only type that can print **multi-part carbon copies** (bank vouchers, invoices) |
| **Impact** | Daisy wheel, Line printer | A moulded character strikes the ribbon | Letter quality but no graphics |
| **Non-impact** | **Inkjet** | Sprays tiny droplets of liquid ink | Good quality, good colour, cheap printer but expensive ink |
| **Non-impact** | **Laser** | A laser draws the image on a drum; **toner** sticks to it and is **fused by heat** | **Best quality and speed**, low cost per page, ideal for offices |
| **Non-impact** | Thermal | Heat darkens special paper | Receipts, POS, ATM slips |
| **Non-impact** | **3-D printer** | Builds an object layer by layer | Prototyping, manufacturing |

> **The main component of a dot-matrix printer is the PRINT HEAD** — a column of small pins (typically 9 or 24) driven by electromagnets. The more pins, the better the quality (a 24-pin head produces near-letter-quality output).

#### Display: pixel and resolution

| Term | Meaning |
|---|---|
| **Pixel** | **PICture ELement** — the **smallest addressable dot** of a display or image. Each pixel has a colour, formed from **red, green and blue** sub-pixels |
| **Resolution** | The **number of pixels** a display or image contains, written as **width × height** (e.g. 1920 × 1080) |
| **PPI / DPI** | **Pixels (or dots) per inch** — the *density* of pixels, which determines sharpness at a given physical size |
| **Aspect ratio** | The ratio of width to height — 4:3, **16:9**, 21:9 |
| **Colour depth** | Bits per pixel — 8-bit (256 colours), 16-bit, **24-bit true colour (16.7 million)**, 32-bit (with alpha) |

**Standard resolutions:**

| Name | Resolution | Total pixels |
|---|---|---|
| VGA | 640 × 480 | 307,200 |
| **HD** | **1280 × 720** | 921,600 |
| **Full HD (1080p)** | **1920 × 1080** | **2,073,600** |
| 2K / QHD | 2560 × 1440 | 3,686,400 |
| **4K / UHD** | **3840 × 2160** | **8,294,400** |
| 8K | 7680 × 4320 | 33,177,600 |

> **Higher resolution = more pixels = sharper image and more detail**, but it also needs **more memory, more GPU power and more bandwidth**.
>
> **Worked calculation:** the video memory needed for one screen of 1920 × 1080 at 24-bit colour = 1920 × 1080 × 3 bytes = **6,220,800 bytes ≈ 5.93 MB** per frame. For a "pixel number of 130", the intended reading is usually **130 PPI** — pixel *density* — or a small 130 × 130 image, which contains 130 × 130 = **16,900 pixels**. Always state which interpretation you are using.

#### What is a graphics card?

A **graphics card (video card / display adapter)** is an expansion card containing a **GPU (Graphics Processing Unit)** and its own **video memory (VRAM)**, which **renders images, video and animation and sends the signal to the monitor**.

| Component | Function |
|---|---|
| **GPU** | Massively parallel processor specialised for graphics and matrix maths |
| **VRAM** | Dedicated high-speed memory (GDDR6) holding textures and frame buffers |
| **Cooling** | Heat sink and fans — GPUs generate a great deal of heat |
| **Output ports** | HDMI, DisplayPort, DVI, VGA |
| **Power connectors** | High-end cards need direct PSU power |

**Integrated vs dedicated:** an **integrated** GPU is built into the CPU and shares system RAM — cheap, low power, fine for office work. A **dedicated** card has its own GPU and VRAM — essential for **gaming, video editing, CAD, 3-D rendering, and AI/deep learning training**.

**Previous Year Question List from this Topic:**

- [Name and define the components of a computer system. Mention two optical input devices.](../written-answers/computer-fundamental.md?plain=1#L2303)
- [Plotter কোন ধরনের Device?](../written-answers/computer-fundamental.md?plain=1#L2480)
- [গ্রাফিক্স কার্ড কি?](../written-answers/computer-fundamental.md?plain=1#L2549)
- [ডট মেট্রিক্স প্রিন্টারের মূল উপাদান কি?](../written-answers/computer-fundamental.md?plain=1#L2568)
- [Touch Screen কি জাতীয় ডিভাইস?](../written-answers/computer-fundamental.md?plain=1#L2590)
- [Distinguish between OMR and MICR.](../written-answers/computer-fundamental.md?plain=1#L2720)


---

### Factors Affecting Computer Performance

> *(A directly asked question: "Discuss the factors that affect the processing speed of a computer.")*

| # | Factor | How it affects speed |
|---|---|---|
| 1 | **CPU clock speed (GHz)** | Cycles per second — more cycles, more instructions per second |
| 2 | **Number of cores and threads** | **Multi-core** CPUs execute several tasks genuinely in parallel |
| 3 | **CPU architecture / IPC** | Instructions executed per clock cycle; a modern 3 GHz CPU is far faster than an old 3 GHz one |
| 4 | **Cache memory (L1, L2, L3)** | Larger, faster cache means fewer slow trips to RAM — often more important than raw GHz |
| 5 | **RAM size** | Too little RAM forces **swapping/paging to disk**, which is catastrophic for speed |
| 6 | **RAM speed and channels** | DDR generation, MHz, and dual/quad-channel bandwidth |
| 7 | **Storage type** | **SSD vs HDD is the single biggest practical difference** — an SSD is 10–100× faster to access |
| 8 | **Bus width and speed** | The data highway between CPU, memory and devices (FSB, PCIe generation) |
| 9 | **Word size** | 32-bit vs **64-bit** — how much data is handled per operation |
| 10 | **GPU** | Offloads graphics and parallel computation from the CPU |
| 11 | **Operating system and background processes** | Bloatware, startup programs and malware steal CPU and RAM |
| 12 | **Disk fragmentation and free space** | A nearly full or fragmented drive slows dramatically (matters for HDD) |
| 13 | **Malware / viruses** | Consume resources silently |
| 14 | **Heat and thermal throttling** | An overheating CPU **deliberately slows itself down** to avoid damage |
| 15 | **Power settings** | "Power saver" mode caps the CPU frequency |
| 16 | **Software efficiency** | A badly written O(n²) program beats no hardware |
| 17 | **Network speed** | For cloud and networked applications, the bottleneck is often the link, not the machine |

#### Laptop overheating — causes and solutions

**Causes:** dust clogging the vents and heat sink · **dried-out thermal paste** between CPU and heat sink · a failing or blocked **fan** · use on a **bed, pillow or lap** blocking the intake · heavy sustained load (gaming, rendering, many browser tabs) · high ambient temperature · malware consuming 100 % CPU · a swollen or faulty battery · an old, degraded cooling system.

**Solutions:**
1. **Clean the vents and internal heat sink** with compressed air — the most common and most effective fix.
2. **Replace the thermal paste** (recommended every 2–3 years).
3. Use it on a **hard, flat surface**; add a **cooling pad** with fans.
4. **Check fan operation**; replace a failing fan.
5. **Close unnecessary programs**; check the task manager for a runaway process; **scan for malware**.
6. **Update BIOS and drivers** — fan curves are often improved in updates.
7. Reduce load: lower game settings, limit background sync, use a **balanced/power-saver** profile.
8. **Undervolt** the CPU (advanced) to cut heat with minimal performance loss.
9. Keep the ambient temperature reasonable and avoid direct sunlight.
10. If it persists, have the **heat pipes and heat sink assembly** inspected or replaced.

#### Choosing a monitor

When replacing a monitor, evaluate: **panel technology** (IPS for colour accuracy and viewing angles, VA for contrast, TN for cheap high refresh rates) · **size and resolution** (and therefore PPI) · **refresh rate** (60 Hz for office, 120 Hz+ for gaming) · **response time** · **brightness and contrast ratio** · **colour gamut** (sRGB coverage, important for design work) · **ports** (HDMI/DisplayPort/USB-C, and whether they match the computer) · **ergonomics** (height/tilt/pivot adjustment, VESA mount) · **eye comfort** (flicker-free, blue-light filter) · **power consumption** and **warranty/dead-pixel policy**.

**Previous Year Question List from this Topic:**

- [(ক) কম্পিউটার সিস্টেমের কর্মক্ষমতার উপর প্রভাব রাখতে সক্ষম এরূপ ৩টি Component এর সংক্ষিপ্ত বর্ণনা দিন।](../written-answers/computer-fundamental.md?plain=1#L2434)
- [(d) Mention and discuss some fectors that affect the processing speed a computer.](../written-answers/computer-fundamental.md?plain=1#L2605)
- [How to solve laptop overheating problem?](../written-answers/computer-fundamental.md?plain=1#L2638)
- [Suppose you are entering data into computer but facing some problem with your monitor. You need to buy a new monitor. What factor should you consider in case of…](../written-answers/computer-fundamental.md?plain=1#L2691)
- [What do understand by the resolution of computer screen?](../written-answers/computer-fundamental.md?plain=1#L2351)
- [Pixel number 130 হলে রেজুলেশন কত হবে?](../written-answers/computer-fundamental.md?plain=1#L2385)
- [পিক্সেল ও রেজ্যুলেশন কি ব্যাখ্যা করুন।](../written-answers/computer-fundamental.md?plain=1#L2500)


---

## Software Types & Classification

### Software — Types and Classification

**Software** is the **set of programs, procedures and associated documentation** that tells the hardware what to do. It is the **logical, intangible** part of a computer system.

```mermaid
flowchart TD
    S["SOFTWARE"] --> A["1 . SYSTEM SOFTWARE<br/>runs and manages the computer itself"]
    S --> B["2 . APPLICATION SOFTWARE<br/>does work for the USER"]
    S --> C["3 . UTILITY / SUPPORT SOFTWARE"]
    A --> A1["Operating System<br/>Windows, Linux, macOS, Android"]
    A --> A2["Device Drivers"]
    A --> A3["Language Translators<br/>Compiler, Interpreter, Assembler"]
    A --> A4["Firmware / BIOS"]
    B --> B1["General purpose<br/>MS Word, Excel, browsers"]
    B --> B2["Custom / Bespoke<br/>a bank's core banking system"]
    C --> C1["Antivirus, disk cleanup,<br/>backup, compression"]
```

#### System software vs Application software

| Point | **System Software** | **Application Software** |
|---|---|---|
| **Purpose** | **Manages and controls the computer hardware** and provides a platform | **Performs a specific task for the USER** |
| **Works for** | **The computer itself** | **The user** |
| **When it runs** | **Starts with the system** and runs continuously in the background | **Started by the user** when needed |
| **Essential?** | ✅ **Yes — the computer cannot work without it** | ❌ No — the computer runs fine without it |
| **Written in** | Usually **low-level languages** (C, assembly) for speed and hardware access | Usually **high-level languages** (Java, Python, C#) |
| **Interaction** | Interacts **directly with hardware** | Interacts with the **user**, and reaches hardware **through the system software** |
| **Independence** | Can run **independently** | **Depends on** system software |
| **Size / complexity** | Generally large and complex, but general-purpose | Varies; task-specific |
| **User awareness** | Mostly invisible to the user | The user works with it directly |
| **Installation** | Usually pre-installed | Installed by the user as needed |
| **Examples** | **Operating systems** (Windows, Linux, macOS, Android), **device drivers**, **compilers/assemblers/interpreters**, BIOS/firmware, utility programs | **MS Word, Excel, PowerPoint**, Chrome, Photoshop, VLC, WhatsApp, games, **banking software, Tally, AutoCAD** |

#### Software vs Hardware

| Point | **Hardware** | **Software** |
|---|---|---|
| **Nature** | **Physical, tangible** — you can touch it | **Logical, intangible** — a set of instructions |
| **Made of** | Electronic and mechanical components | Code written by programmers |
| **Wear and tear** | ✅ **Degrades physically** over time | ❌ **Does not wear out**, but it does become **obsolete** and accumulate bugs |
| **If it fails** | **Repair or REPLACE** the part | **Reinstall, patch or update** |
| **Virus affected?** | ❌ Not directly | ✅ **Yes** |
| **Transfer** | Must be physically moved | **Copied instantly** over a network |
| **Manufacturing cost** | High per unit — raw materials, factory | **Nearly zero per extra copy** after development |
| **Development cost** | Design + manufacture | **Almost all the cost is development** |
| **Dependency** | Useless without software | Cannot run without hardware |
| **Examples** | CPU, RAM, monitor, keyboard, hard disk, printer | Windows, MS Office, Chrome, a compiler, a mobile app |

> **They are inseparable:** *hardware without software is a lifeless box; software without hardware is an idea that cannot execute.*

#### Platform-independent software

**Platform-independent (cross-platform) software** runs on **multiple operating systems and hardware architectures without being rewritten**.

**How it is achieved**

| Method | How it works | Example |
|---|---|---|
| **Virtual machine / bytecode** | The source is compiled once to an **intermediate bytecode**, which a platform-specific **virtual machine** executes | **Java → bytecode → JVM** — "write once, run anywhere" |
| **Interpreted languages** | The source is shipped as-is and interpreted by a platform-specific interpreter | **Python, JavaScript, Ruby, PHP** |
| **Web applications** | The application runs inside the **browser**, which is the universal platform | Gmail, Google Docs, any web app |
| **Cross-platform frameworks** | One code base compiled or rendered for each target | Flutter, React Native, Electron, Qt, .NET MAUI |
| **Containers** | The app plus its dependencies ship together | **Docker** (across Linux hosts) |

**Example explained — Java.** A Java program `Hello.java` is compiled by `javac` into **`Hello.class`, which contains bytecode, not machine code**. That same `.class` file runs unchanged on Windows, Linux, macOS or Android, because each platform has its **own JVM** that translates the bytecode into that machine's native instructions. **The bytecode is portable; the JVM is not.**

**Advantages:** one code base to write and maintain; a much larger market; lower development cost; users are not locked to one OS.
**Disadvantages:** usually **slower** than native code; cannot easily use platform-specific features; a larger download (the runtime must be present); and the look-and-feel may not match the host OS perfectly.

**Previous Year Question List from this Topic:**

- [What is the difference between System Software and Application Software?](../written-answers/computer-fundamental.md?plain=1#L2745)
- [What is platform independent software discuss with example?](../written-answers/computer-fundamental.md?plain=1#L2764)
- [Software বলতে কী বোঝেন? উদাহরণসহ System Software and Application Software -এর সংক্ষিপ্ত বর্ণনা দিন?](../written-answers/computer-fundamental.md?plain=1#L2901)
- [Differentiate between system software and application software.](../written-answers/computer-fundamental.md?plain=1#L3017)
- [Define system software and application software with three examples of each.](../written-answers/computer-fundamental.md?plain=1#L3035)
- [b) What are the main differences between software and hardware? Discuss with examples.](../written-answers/computer-fundamental.md?plain=1#L3057)


---

### Programming Languages and Their Levels

| Level | Description | Machine dependence | Translator needed | Speed | Ease |
|---|---|---|---|---|---|
| **Machine language (1GL)** | Pure **binary** — 0s and 1s, the only language the CPU truly understands | **Fully machine dependent** | **None** | **Fastest** | Extremely hard |
| **Assembly language (2GL)** | **Mnemonics** — MOV, ADD, SUB — one statement per machine instruction | Machine dependent | **Assembler** | Very fast | Hard |
| **High-level language (3GL)** | English-like statements, hardware details hidden | **Machine INDEPENDENT** | **Compiler or Interpreter** | Slower | **Easy** |
| **Very high level (4GL)** | Declarative — say *what*, not *how* | Independent | Interpreter/engine | Slower | Very easy |
| **Natural / AI (5GL)** | Constraints and natural language | Independent | AI engine | — | Easiest |

#### High-level vs Low-level languages

| Point | **Low-Level Language** | **High-Level Language** |
|---|---|---|
| **Closeness to hardware** | **Very close** — direct register and memory access | **Far** — hardware details are abstracted away |
| **Human readability** | **Difficult** — binary or cryptic mnemonics | **Easy** — English-like |
| **Machine dependence** | **Machine DEPENDENT** — code written for one CPU will not run on another | **Machine INDEPENDENT / portable** |
| **Translator** | Assembler (or none for machine code) | **Compiler or interpreter** |
| **Execution speed** | **Fastest** | Slower |
| **Memory efficiency** | **Highly efficient** — the programmer controls every byte | Less efficient |
| **Development speed** | **Very slow**; many lines for a simple task | **Fast** — one line replaces many |
| **Debugging & maintenance** | **Very difficult** | **Easy** |
| **Error probability** | High | Lower |
| **Used for** | **Device drivers, embedded systems, OS kernels, BIOS, real-time control**, performance-critical routines | **Applications, web, business software, games, data science** — almost everything |
| **Examples** | **Machine code, Assembly (8085/8086, ARM, MIPS)** | **C, C++, Java, Python, C#, PHP, JavaScript, COBOL, FORTRAN** |

*(**C is often called a "middle-level" language**, because it has high-level structure and readability but also allows low-level pointer and bit manipulation.)*

#### Which language for which job

| Task | Language |
|---|---|
| **Android application development** | **Java** (and **Kotlin**, now Google's preferred language) |
| iOS application development | **Swift** (formerly Objective-C) |
| Web front end | **JavaScript** (with HTML and CSS) |
| Web back end | PHP, Python, Java, Node.js, C#, Go |
| System / OS programming | **C, C++, Rust** |
| Embedded systems | **C, Assembly** |
| Data science and AI | **Python**, R |
| Enterprise / banking back office | **Java, COBOL, C#** |
| Databases | **SQL** |
| Scientific computing | FORTRAN, Python, MATLAB |
| **Teaching children / turtle graphics** | **LOGO** — an educational language famous for its "turtle" that draws shapes as it moves |

**Previous Year Question List from this Topic:**

- [Difference between High level languages and low level language with some example?](../written-answers/computer-fundamental.md?plain=1#L2788)
- [Which language help you to learn android programming? (a) C (b) C++ (c) Java (d) IOS](../written-answers/computer-fundamental.md?plain=1#L2841)
- [LOGO কি ধরনের প্রোগ্রাম?](../written-answers/computer-fundamental.md?plain=1#L2850)


---

### Common Application Software and Office Tools

| Category | Software |
|---|---|
| **Word processing** | **MS Word**, Google Docs, LibreOffice Writer, WPS Writer |
| **Spreadsheet / calculation** | **MS Excel**, Google Sheets, LibreOffice Calc |
| **Presentation** | **MS PowerPoint**, Google Slides, Prezi |
| **Database** | MS Access, MySQL, Oracle, SQL Server, PostgreSQL |
| **Accounting** | **Tally**, QuickBooks, Zoho Books, SAP FI |
| **Graphics design** | **Adobe Photoshop, Adobe Illustrator, CorelDRAW, Canva**, GIMP, Inkscape, Figma |
| **Video editing** | Adobe Premiere Pro, Final Cut Pro, DaVinci Resolve, Filmora |
| **Web browsing** | Chrome, Firefox, Edge, Safari |
| **Email client** | Outlook, Thunderbird, Gmail |
| **Bangla writing** | **Avro Keyboard, Bijoy Bayanno**, Ridmik |

> **Which software is used for calculation work on a computer?** → a **SPREADSHEET** program, principally **Microsoft Excel**.
>
> **What is the grid of cells in a spreadsheet called?** → the **WORKSHEET** (or **spreadsheet**). Each individual box is a **CELL**, identified by its **column letter + row number** (A1, B5). A collection of worksheets in one file is a **WORKBOOK**.
>
> **LOGO** is an **educational programming language** designed to teach programming concepts to children through **turtle graphics**.
>
> **Bangla email software:** any standard email client can send Bangla once a **Unicode Bangla keyboard** such as **Avro** or **Bijoy** is installed — Avro is the most widely used free Bangla typing software in Bangladesh.

#### MS Excel — the IF function

The **IF** function returns one value when a condition is true and another when it is false:

```
=IF(logical_test, value_if_true, value_if_false)
```

**Examples using cells A1, B1, C1:**

```excel
=IF(A1>50, "Pass", "Fail")                     ' simple two-way test
=IF(A1>B1, A1, B1)                             ' the larger of A1 and B1
=IF(A1>=B1, IF(A1>=C1, A1, C1), IF(B1>=C1, B1, C1))   ' the largest of THREE — nested IF
=IF(AND(A1>40, B1>40, C1>40), "All Passed", "Not all passed")
=IF(OR(A1>90, B1>90), "Excellent", "Normal")
=IF(A1="", "Empty", "Has data")                ' blank check
=IFERROR(A1/B1, "Division error")              ' safe division
```

**A grade calculation with a nested IF:**
```excel
=IF(A1>=80,"A+", IF(A1>=70,"A", IF(A1>=60,"A-", IF(A1>=50,"B", IF(A1>=40,"C","F")))))
```

**Running MS Office from the Run dialog** (Windows + R): **`winword`** opens MS Word · **`excel`** opens Excel · **`powerpnt`** opens PowerPoint · **`msaccess`** opens Access · **`outlook`** opens Outlook · **`notepad`**, **`calc`**, **`mspaint`**, **`cmd`**, **`control`** for the Control Panel.

**MS Word, Excel and PowerPoint together are classified as APPLICATION software** — specifically **general-purpose packaged application software**, sold as the **Microsoft Office suite**.

**Previous Year Question List from this Topic:**

- [Computer এ হিসাব কার্যক্রম করার জন্য কোন Software টি ব্যবহৃত হয়?](../written-answers/computer-fundamental.md?plain=1#L2812)
- [Spreed sheet program এ অসংখ্য ঘর বিশিষ্ট ছককে কি বলে?](../written-answers/computer-fundamental.md?plain=1#L2826)
- [MS-Excell এর IF Function ব্যবহার করে A1, B1, C1 থেকে ডাটা বের করে D1 এর মধ্যে রাখার ফাংশন লিখ।](../written-answers/computer-fundamental.md?plain=1#L2870)
- [১৫. বাংলায় ই-মেইল করার সফটওয়্যারের নাম কি?](../written-answers/computer-fundamental.md?plain=1#L2929)
- [Graphics Design এর চারটি Software এর নাম লিখ।](../written-answers/computer-fundamental.md?plain=1#L2937)
- [Fill in the blank: (i) Run command to MS word open করবেন কিভাবে _____? (ii) MS Word, Excel, Spreadsheet Macro ব্যবহার করা হয় _____ সুবিধার জন্য। (iii) Spreadshe…](../written-answers/computer-fundamental.md?plain=1#L2951)


---

## Data Center Infrastructure & Power Management

### Data Centre — Components and Design Factors

A **data centre** is a **dedicated facility that houses an organisation's IT infrastructure** — servers, storage, networking equipment — together with the **power, cooling, security and connectivity** needed to keep it running continuously.

#### The elements/components of a data centre

```mermaid
flowchart TD
    DC["DATA CENTRE"]
    DC --> IT["1 . IT INFRASTRUCTURE"]
    DC --> PW["2 . POWER SYSTEM"]
    DC --> CL["3 . COOLING SYSTEM"]
    DC --> NW["4 . NETWORK & CONNECTIVITY"]
    DC --> SEC["5 . PHYSICAL SECURITY"]
    DC --> FIRE["6 . FIRE DETECTION & SUPPRESSION"]
    DC --> MON["7 . MONITORING & MANAGEMENT (DCIM)"]
    IT --> IT1["Servers · Storage (SAN/NAS) · Racks · Cabling"]
    PW --> PW1["Utility feed · UPS · Generators · PDU · ATS · Batteries"]
    CL --> CL1["CRAC/CRAH units · Chillers · Hot/cold aisles · Raised floor"]
    NW --> NW1["Core & ToR switches · Routers · Firewalls · Load balancers · Redundant ISP links"]
    SEC --> SEC1["Access control · Biometrics · CCTV · Mantrap · Guards"]
    FIRE --> FIRE1["VESDA smoke detection · Clean-agent (FM-200/Novec) suppression"]
    MON --> MON1["DCIM · BMS · NOC · Sensors · Alerting"]
```

| Component | Detail |
|---|---|
| **Servers & compute** | Rack-mounted or blade servers, virtualisation hosts |
| **Storage** | SAN, NAS, disk arrays, tape/backup libraries |
| **Racks & cabinets** | Standard **42U, 19-inch** racks with cable management |
| **Network** | Core, aggregation and top-of-rack switches, routers, firewalls, structured cabling, **redundant ISP links** |
| **Power** | Utility feed, **UPS** for instant backup, **diesel generators** for long outages, **PDUs**, **ATS (Automatic Transfer Switch)**, battery banks |
| **Cooling / HVAC** | **CRAC/CRAH** units, chillers, cooling towers, **hot aisle / cold aisle containment**, raised floor, humidity control |
| **Physical security** | Multi-layer access control, biometrics, **mantrap**, CCTV, 24×7 guards |
| **Fire safety** | Very-early smoke detection (**VESDA**), **clean-agent** suppression (FM-200, Novec 1230 — water would destroy the equipment) |
| **Environmental monitoring** | Temperature, humidity, water-leak and airflow sensors |
| **Management** | **DCIM** software, a **BMS**, a **NOC**, ticketing and change management |
| **Disaster recovery** | A **geographically separate DR site** with replication |

#### The most important factors for a banking data centre

| # | Factor | Why it matters in banking |
|---|---|---|
| 1 | **Availability / uptime** | Banking is 24×7; a **Tier III or Tier IV** design with N+1 or 2N redundancy is expected. Every minute of downtime is lost transactions and reputational damage |
| 2 | **Security — physical and cyber** | Customer financial data is the highest-value target: multi-layer access, encryption, IDS/IPS, **SOC** monitoring |
| 3 | **Regulatory compliance** | **Bangladesh Bank ICT Security Guideline**, **PCI-DSS** for cards, ISO 27001, data-localisation rules |
| 4 | **Disaster Recovery / Business Continuity** | A **DR site in a different seismic and flood zone**, with defined **RPO and RTO**, and regular DR drills |
| 5 | **Power reliability** | **Redundant utility feeds + UPS + N+1 generators**; a bank cannot tolerate a power gap |
| 6 | **Cooling reliability** | Redundant CRAC units; overheating shuts down servers as surely as a power cut |
| 7 | **Network redundancy** | Multiple ISPs over **diverse physical paths**, redundant core switches, no single point of failure |
| 8 | **Data integrity and backup** | **Real-time replication**, tested restores, immutable/offline backups against ransomware |
| 9 | **Scalability** | Room to grow as customers, branches and digital channels expand |
| 10 | **Monitoring and 24×7 NOC/SOC** | Detect and respond before customers notice |
| 11 | **Location** | Away from flood plains, industrial hazards and political risk; good connectivity and skilled staff nearby |
| 12 | **Audit trail** | Every physical and logical access logged for regulators |

#### National data centre

A **national data centre** is a **government-owned, centralised data centre facility that hosts the IT systems, databases and e-services of the state**, providing shared, secure and sovereign infrastructure to all ministries and agencies instead of each building its own.

**Purpose and benefits:** **data sovereignty** (citizen data stays inside the country) · **cost saving** through shared infrastructure · **uniform security and compliance** standards · **interoperability** between agencies · **disaster recovery** for critical national systems · foundation for e-government and **Digital Bangladesh**.

**In Bangladesh:** the **National Data Center (NDC)** at the **Bangladesh Computer Council (BCC)**, and the **Tier IV National Data Center at Kaliakoir (Bangabandhu Hi-Tech City)** — one of the largest Tier IV facilities in the region — plus a **Disaster Recovery site in Jessore**.

**Previous Year Question List from this Topic:**

- [Describe the most important factors of data center for banking organization.](../written-answers/computer-fundamental.md?plain=1#L3112)
- [What do you mean by national data center?](../written-answers/computer-fundamental.md?plain=1#L3168)
- [Write down the element of data center.](../written-answers/computer-fundamental.md?plain=1#L3282)
- [Explain the component of Data Center.](../written-answers/computer-fundamental.md?plain=1#L3336)


---

### Data Centre Tier Standards

The **Uptime Institute Tier classification** rates a data centre's infrastructure **redundancy and availability** on a four-level scale.

| | **Tier I** | **Tier II** | **Tier III** | **Tier IV** |
|---|---|---|---|---|
| **Name** | Basic capacity | Redundant components | **Concurrently maintainable** | **Fault tolerant** |
| **Redundancy** | **N** (none) | **N + 1** (partial) | **N + 1** (full, with dual paths) | **2N or 2(N+1)** (fully duplicated) |
| **Distribution paths** | **1** | **1** | **2** (one active, one alternate) | **2 ACTIVE** simultaneously |
| **Uptime guarantee** | **99.671 %** | **99.741 %** | **99.982 %** | **99.995 %** |
| **Downtime per year** | **28.8 hours** | **22 hours** | **1.6 hours** | **26.3 minutes** |
| **Maintenance without shutdown?** | ❌ **No** — must shut down | ❌ Partly | ✅ **YES** — any component can be serviced with no downtime | ✅ Yes |
| **Survives an unplanned failure?** | ❌ No | ❌ Limited | ⚠️ Mostly — but a single fault can still cause an outage | ✅ **YES — any single fault is absorbed automatically** |
| **Cost** | Lowest | Low | High | **Highest** |
| **Typical user** | Small business, startup | SME | **Most enterprises, banks** | **National infrastructure, stock exchanges, top-tier banks** |

```mermaid
flowchart TD
    subgraph T1["TIER I — N, single path"]
        U1["Utility"] --> UP1["UPS"] --> R1["Racks"]
    end
    subgraph T3["TIER III — N+1, dual path, one active"]
        U3["Utility A"] --> UP3A["UPS A"] --> R3["Racks"]
        U3B["Generator"] --> UP3B["UPS B (standby)"] -.->|"alternate path"| R3
    end
    subgraph T4["TIER IV — 2N, dual path, BOTH active"]
        U4A["Utility A"] --> UP4A["UPS A"] --> R4["Racks"]
        U4B["Utility B"] --> UP4B["UPS B"] --> R4
        G4A["Generator A"] --> UP4A
        G4B["Generator B"] --> UP4B
    end
```

> **The essential distinction between Tier III and Tier IV:** Tier III is **concurrently maintainable** — you can service *any* component **on a planned basis** without downtime, because there is an alternate path. Tier IV is **fault tolerant** — it also survives an **unplanned, unexpected failure of any single component** with **no** interruption, because both paths are **simultaneously active**.

**Previous Year Question List from this Topic:**

- [What do you mean by TIERing data center? Difference between data center TIER standards with illustrative figures.](../written-answers/computer-fundamental.md?plain=1#L3210)


---

### Data Centre Power — UPS, Generators and DCIM

#### Online vs Offline UPS

An **Uninterruptible Power Supply (UPS)** provides **instant battery backup** when mains power fails, and conditions the power while mains is present.

| Point | **Offline / Standby UPS** | **Online / Double-Conversion UPS** |
|---|---|---|
| **Normal operation** | The load runs **directly on raw mains**; the inverter is idle | Mains → **rectifier → DC → inverter → AC** — the load **always** runs from the inverter |
| **Transfer time** | **2–10 milliseconds** (there IS a brief gap) | **ZERO — no transfer at all**, because the inverter never stops |
| **Power conditioning** | **Minimal** — spikes, sags and frequency variation pass through | **Complete** — the output is a clean, regulated, constant-voltage, constant-frequency sine wave, fully isolated from mains disturbance |
| **Protection level** | Basic | **Highest** |
| **Efficiency** | **Higher (95–98 %)** — no conversion loss in normal mode | Lower (85–95 %) — double conversion always costs energy |
| **Heat generated** | Low | **High** |
| **Cost** | **Low** | **High** |
| **Size** | Small | Large |
| **Used for** | **Home PCs, small offices**, non-critical loads | **Data centres, servers, medical equipment, telecom, banking systems** |
| **Also called** | Standby UPS | True UPS / double-conversion UPS |

*(A third type, the **Line-Interactive UPS**, sits between them: it adds **AVR (Automatic Voltage Regulation)** to correct voltage fluctuation without switching to battery, and is the usual choice for small servers and network equipment.)*

> **For a data centre, an ONLINE UPS is mandatory**, because even a 5-millisecond gap can reboot a server, and because the double conversion completely isolates sensitive equipment from the poor mains quality common in Bangladesh.

#### Generators for a data centre

**UPS** covers **seconds to minutes** (batteries); a **diesel generator** covers **hours to days**. The **ATS (Automatic Transfer Switch)** starts the generator and transfers the load automatically when mains fails, while the UPS bridges the 10–60 second gap until the generator stabilises.

> ### "For a data centre cooling system, which type of generator would you prefer — AC or DC?"
>
> **An AC generator (alternator) — a standard diesel-driven synchronous AC generator — is the correct choice.**
>
> **Reasons:**
> 1. **Cooling equipment is AC.** CRAC units, chillers, compressors, pumps and blowers are driven by **three-phase AC induction motors**, which require an AC supply. A DC generator would need a large inverter to drive them, adding cost, loss and another failure point.
> 2. **AC is the standard for power distribution** — it can be **transformed** to different voltages efficiently and distributed over the facility with low loss; DC cannot be transformed simply.
> 3. **AC generators (alternators) are simpler and more reliable** — they have **no commutator or brushes** (in a brushless design), so there is far less wear, sparking and maintenance than a DC generator with its commutator.
> 4. **Higher capacity and efficiency** at the megawatt scale required.
> 5. **Easy synchronisation and paralleling** — several AC generators can be run in parallel to share load and provide N+1 redundancy.
> 6. **Compatibility with the grid and the ATS**, and with the UPS input.
> 7. **Availability, cost and serviceability** — AC diesel gensets are the industry standard and spares and technicians are readily available.
>
> **Specification points to add:** size the generator for the full cooling load **plus** the IT load with margin (cooling is often 30–40 % of total); prefer **three-phase, 400 V, 50 Hz**; provide **N+1 redundancy**; ensure **automatic start and transfer (ATS)** within 10 seconds; and keep **adequate fuel storage** with an automatic refill contract for extended outages.
>
> *(DC power **is** used inside data centres — telecom-style **48 V DC** distribution and DC-powered racks improve efficiency by removing conversion stages — but that DC is produced by **rectifiers from an AC source**, not by a DC generator, and it is not used for driving cooling machinery.)*

#### DCIM — Data Center Infrastructure Management

**DCIM** is **software that monitors, measures and manages a data centre's IT equipment together with its physical infrastructure** (power, cooling, space), bringing both worlds into a single view.

**What DCIM does**

| Function | Detail |
|---|---|
| **Asset management** | A complete inventory of every server, switch and rack, with location and lifecycle |
| **Real-time monitoring** | Power draw, temperature, humidity, airflow, UPS and generator status |
| **Capacity planning** | How much **space, power and cooling** remains; where the next server can safely go |
| **Power management** | Per-rack and per-outlet power measurement, **PUE** calculation, cost allocation |
| **Cooling optimisation** | Identifies hot spots and over-cooled zones; supports containment planning |
| **Change management** | Plan and record every move, add and change |
| **Alerting** | Threshold alarms before something fails |
| **Reporting and compliance** | Energy, uptime and audit reports |

**Benefits:** prevents outages by catching problems early · **reduces energy cost** · defers capital expenditure by using existing capacity fully · shortens fault diagnosis · supports audits and sustainability reporting.

#### Energy efficiency and PUE

> **PUE (Power Usage Effectiveness) = Total facility power ÷ IT equipment power**

| PUE | Meaning |
|---|---|
| **1.0** | Perfect — every watt goes to IT (theoretically impossible) |
| **1.1 – 1.2** | **Excellent** — modern hyperscale data centres (Google averages ~1.1) |
| **1.5 – 1.8** | Typical modern enterprise data centre |
| **2.0 – 3.0** | Poor / older facility — for every watt of computing, another one or two is spent on cooling and losses |

#### Challenges in optimising data centre energy efficiency

| # | Challenge | Explanation |
|---|---|---|
| 1 | **Cooling dominates consumption** | Cooling can be **30–50 %** of total power; every watt of IT power becomes a watt of heat that must be removed |
| 2 | **Over-provisioning** | Infrastructure is sized for peak load and redundancy, so it runs far below capacity most of the time — and equipment is **least efficient at low load** |
| 3 | **Idle and "zombie" servers** | Studies find **20–30 %** of servers doing no useful work, yet drawing 50–60 % of their peak power |
| 4 | **Hot spots and air mixing** | Hot exhaust mixing with cold supply air forces over-cooling of the whole room to protect a few racks |
| 5 | **Legacy equipment** | Older servers and CRAC units are far less efficient but expensive to replace |
| 6 | **The redundancy vs efficiency conflict** | 2N redundancy means every component runs at **≤50 % load**, which is inefficient — but reliability cannot be sacrificed |
| 7 | **Lack of measurement** | You cannot optimise what you do not measure; many facilities lack per-rack metering |
| 8 | **Climate** | In a hot, humid country like Bangladesh, free-air cooling is rarely possible and dehumidification adds load |
| 9 | **Rising power density** | AI and GPU racks now draw **30–100 kW per rack** versus 3–5 kW a decade ago, outrunning air cooling entirely |
| 10 | **Uninterruptible power losses** | Double-conversion UPS and transformers each waste several percent |
| 11 | **Split incentives / organisational silos** | The IT team buys the servers; the facilities team pays the electricity bill |
| 12 | **Uptime risk aversion** | Nobody wants to be blamed for an outage caused by an efficiency experiment |

**Solutions:** **hot-aisle/cold-aisle containment** · raise the supply air temperature (ASHRAE now allows up to 27 °C) · **virtualisation and consolidation** to raise server utilisation · decommission zombie servers · variable-speed fans and pumps · **free cooling / economisers** where climate allows · **liquid and immersion cooling** for high-density racks · high-efficiency **modular UPS** · DCIM monitoring with **per-rack metering** · renewable energy and heat reuse.

#### Dynamic capacity provisioning

**Dynamic capacity provisioning** is the practice of **automatically allocating and releasing computing resources in real time to match the actual workload**, instead of keeping a fixed amount of capacity permanently powered on.

**How it works:** the system continuously monitors demand (CPU, memory, request rate); when load rises it **starts more virtual machines or containers and powers on more physical servers**; when load falls it **consolidates workloads onto fewer hosts and powers the rest down or puts them to sleep**.

**Why it is essential for a data centre**

1. **Energy saving** — idle servers still draw 50–60 % of peak power; turning them off is the single largest saving available.
2. **Cost reduction** — less electricity, less cooling, deferred hardware purchases.
3. **Handles demand spikes** — sale days, salary day, exam-result day.
4. **Higher utilisation** — typical static data centres run at 10–20 % utilisation; dynamic provisioning can double or triple that.
5. **Sustainability** — a direct reduction in carbon footprint.
6. **Better SLA compliance** — capacity is added *before* performance degrades.
7. **It is the foundation of cloud elasticity** — pay-per-use billing only works if capacity can actually be released.

**Challenges:** the **provisioning delay** (a server takes minutes to boot), the risk of **thrashing** (constantly powering on and off), accurate **workload prediction**, **stateful applications** that cannot be moved easily, and the wear of frequent power cycling.

**Previous Year Question List from this Topic:**

- [To maintain a data center cooling system sometimes where you need a DC generator. Which type of generator do you prefer based on fuel type generator type, cost,…](../written-answers/computer-fundamental.md?plain=1#L3084)
- [What are the challenges in optimizing energy efficiency of data centers? Explain!](../written-answers/computer-fundamental.md?plain=1#L3149)
- [What is DCIM in a data center?](../written-answers/computer-fundamental.md?plain=1#L3187)
- [What do you mean by dynamic capacity provisioning? Why it is essential for data center?](../written-answers/computer-fundamental.md?plain=1#L3258)
- [Write down difference between Online UPS and Offline UPS.](../written-answers/computer-fundamental.md?plain=1#L3315)


---

## Server Hardware & Enterprise Systems

### Server Hardware — Components and Selection

A **server** is a computer built for **continuous, reliable, multi-user operation**, providing services (files, applications, databases, web pages) to **client** machines over a network.

#### Server vs desktop computer

| Point | **Server** | **Desktop PC** |
|---|---|---|
| **Purpose** | Serve **many users/clients** simultaneously | One user |
| **Uptime** | **24 × 7 × 365** | A few hours a day |
| **CPU** | **Multiple sockets**, many cores (Xeon, EPYC) | One socket, fewer cores |
| **RAM** | **ECC (Error-Correcting Code)** memory, hundreds of GB to TB | Non-ECC, 8–64 GB |
| **Storage** | **RAID arrays**, hot-swappable, SAS/NVMe | A single SSD/HDD |
| **Power supply** | **Redundant, hot-swappable** | Single |
| **Cooling** | Heavy-duty, redundant fans | Basic |
| **Form factor** | **Rack (1U/2U), blade, tower** | Tower or all-in-one |
| **Management** | **Out-of-band (iDRAC/iLO/IPMI)** — full remote control even when powered off | None |
| **OS** | Windows Server, Linux (RHEL, Ubuntu Server), VMware ESXi | Windows/macOS desktop |
| **Cost** | Very high | Moderate |

#### Key hardware components of a server and their contribution

| Component | Contribution to performance and reliability |
|---|---|
| **CPU (processor)** | **Multi-socket, many-core** (Xeon/EPYC) — determines how many concurrent workloads and VMs it can run. More cores and larger cache directly raise throughput |
| **RAM — ECC memory** | Capacity determines how many VMs/databases fit in memory; **ECC automatically detects and corrects single-bit errors**, preventing silent data corruption and crashes — the single most important server-specific feature |
| **Storage (HDD/SSD/NVMe)** | **The commonest bottleneck.** NVMe SSDs give the highest IOPS for databases; capacity HDDs for archives. Hot-swap bays allow replacement without downtime |
| **RAID controller** | Combines drives for **redundancy (survives a disk failure) and performance (striping)**; a battery/flash-backed write cache accelerates writes safely |
| **Network Interface Cards** | **Multiple 1/10/25/100 GbE ports**, teamed/bonded for **bandwidth and failover**; determines how fast clients are served |
| **Motherboard / chipset** | Determines socket count, memory channels, PCIe lanes — the ceiling on everything else |
| **Power Supply Units (PSU)** | **Redundant (1+1) and hot-swappable**, ideally fed from two separate circuits — removes a single point of failure |
| **Cooling — fans and heat sinks** | Redundant, variable-speed fans prevent **thermal throttling** and hardware failure; a server runs hot 24×7 |
| **Out-of-band management (iDRAC/iLO/IPMI)** | Remote power control, console, BIOS access, firmware update and hardware alerts **even when the OS is dead** — saves site visits and cuts MTTR |
| **Expansion (PCIe slots)** | GPUs for AI, HBAs for SAN, additional NICs |
| **Chassis / form factor** | Rack density, airflow, cable management, serviceability |
| **TPM (Trusted Platform Module)** | Hardware root of trust for secure boot and disk encryption |

#### What to check before buying a server

| # | Consideration | Questions to ask |
|---|---|---|
| 1 | **Workload and purpose** | Web, database, file, virtualisation host, AI training? Each has a different bottleneck |
| 2 | **Performance sizing** | Required cores, RAM, IOPS, network throughput — with headroom for **3–5 years** of growth |
| 3 | **Scalability** | Can RAM, CPU, disks and NICs be added later? How many free slots and bays? |
| 4 | **Reliability / redundancy** | Redundant PSU, ECC RAM, RAID, hot-swap drives and fans |
| 5 | **Form factor and rack space** | Tower vs **rack (how many U?)** vs blade; does it fit the existing rack and airflow? |
| 6 | **Power and cooling budget** | Watts drawn, heat produced, and whether the UPS, PDU and CRAC can support it |
| 7 | **Storage strategy** | Internal disks, SAN/NAS attachment, RAID level, capacity and IOPS |
| 8 | **Network requirement** | Port count and speed, redundancy, compatibility with existing switches |
| 9 | **Operating system and software compatibility** | Is the OS and the application certified on this hardware? Are drivers available? |
| 10 | **Virtualisation support** | VT-x/AMD-V, enough RAM and cores for the planned VM density |
| 11 | **Management features** | iDRAC/iLO licence level, monitoring integration |
| 12 | **Vendor, warranty and support** | **On-site SLA (e.g. 4-hour response)**, local spare-parts availability in Bangladesh, warranty length |
| 13 | **Total Cost of Ownership (TCO)** | Purchase + power + cooling + licences + support over 5 years — **not just the sticker price** |
| 14 | **Security features** | TPM, secure boot, firmware signing, physical locks |
| 15 | **Compliance** | Meets Bangladesh Bank ICT guidelines / organisational standards |
| 16 | **Future-proofing** | Latest CPU generation and PCIe/DDR standard, so upgrades remain possible |

#### Server maintenance best practices

**Routine physical maintenance**
1. **Clean dust** from fans, filters, heat sinks and vents on a schedule — dust is the leading cause of overheating.
2. Check and **test cooling and airflow**; keep blanking panels in empty rack slots.
3. Inspect **cabling** and connectors; keep cable management tidy for airflow.
4. **Test the UPS batteries and generator** under load regularly.
5. Verify **environmental conditions** — temperature and humidity within ASHRAE limits.

**Monitoring**
6. Monitor **CPU, memory, disk, network and temperature** continuously with alerting thresholds.
7. Review **hardware health logs** (predictive disk failure, ECC error counts, PSU status).
8. Track **capacity trends** so upgrades happen before exhaustion.
9. Keep a **24×7 NOC** or at least automated alerts to on-call staff.

**Security and updates**
10. Apply **security patches and firmware/BIOS updates** promptly, **after testing in a staging environment**.
11. Review **user accounts and privileges** regularly; remove dormant accounts; enforce least privilege and MFA.
12. Keep **antivirus/EDR** and firewall rules current; scan for vulnerabilities.
13. Review **logs** for anomalies; retain them for audit.

**Data protection**
14. Follow the **3-2-1 backup rule**: **3** copies, on **2** different media, with **1** off-site.
15. **Test restores regularly** — an untested backup is not a backup.
16. Maintain and **rehearse the disaster recovery plan**.

**Process discipline**
17. Use **change management** — document every change, with a rollback plan.
18. Maintain **up-to-date documentation and asset inventory**.
19. Schedule maintenance in **agreed windows** with user notification.
20. Track **hardware lifecycle** and plan replacement before end-of-support.

#### SAS vs SATA

| Point | **SAS (Serial Attached SCSI)** | **SATA (Serial ATA)** |
|---|---|---|
| **Designed for** | **Enterprise servers and storage arrays** | **Desktops and consumer devices** |
| **Speed** | **12 Gb/s / 24 Gb/s** | 6 Gb/s |
| **Rotational speed (HDD)** | **10,000 / 15,000 RPM** | 5,400 / 7,200 RPM |
| **Reliability (MTBF)** | **~1.6 million hours** | ~700,000 hours |
| **Duty cycle** | Designed for **24 × 7 at 100 % load** | Designed for ~8 hours a day |
| **Error rate (UBER)** | **1 in 10¹⁶** — ten times better | 1 in 10¹⁵ |
| **Full duplex** | ✅ **Yes** — read and write simultaneously | ❌ No — half duplex |
| **Dual porting** | ✅ **Yes** — two independent paths to the drive, so a controller failure does not lose access | ❌ No |
| **Command queueing** | **TCQ — up to 256 commands** | NCQ — 32 commands |
| **Cable length** | Up to **10 m** | Up to 1 m |
| **Devices per controller** | **Up to 65,535** (with expanders) | Typically 4–8 |
| **Cost per GB** | **High** | **Low** |
| **Capacity available** | Lower per drive | **Higher** per drive |
| **Can mix?** | A SAS controller **can** run SATA drives; a SATA controller **cannot** run SAS drives | |

> ### Which is best for a server?
> **SAS is the better choice for a server**, and for the same reason in every case: it is **engineered for continuous, mission-critical, multi-user operation**. Its **dual porting** removes a single point of failure, its **full duplex** operation and deeper command queue handle the **random, concurrent I/O** that a database or virtualisation host generates, and its far **lower error rate and higher MTBF** mean less risk of data loss.
>
> **But the honest, complete answer is that it depends on the workload:**
>
> | Use case | Best choice |
> |---|---|
> | **Database, OLTP, virtualisation host, email server** — random I/O, high concurrency | **SAS** (or **NVMe SSD**, which is now better still) |
> | **Backup, archive, file server, video surveillance storage, cold data** — sequential, capacity-driven | **SATA** — far cheaper per terabyte, and the performance is adequate |
> | **Highest performance regardless of cost** | **NVMe SSD** — it bypasses the SAS/SATA controller entirely and connects over **PCIe**, giving an order of magnitude more IOPS |
>
> Most real servers use a **tiered mix**: NVMe/SAS SSD for hot data, SAS HDD for warm, and large SATA drives for cold data and backups.

**Previous Year Question List from this Topic:**

- [What should be checked before buying servers?](../written-answers/computer-fundamental.md?plain=1#L3584)
- [Scenario based descriptive question for server related problem ( How do you handle those problem for your company )](../written-answers/computer-fundamental.md?plain=1#L3626)
- [What are the key hardware components that make up a typical server, and how do they contribute to its overall performance and functionality?](../written-answers/computer-fundamental.md?plain=1#L3662)
- [Discuss server maintenance best practices, including routine tasks like cleaning, monitoring, and applying security patches. How do these practices contribute t…](../written-answers/computer-fundamental.md?plain=1#L3682)
- [Difference between SAS and SATA. Which one is best server?](../written-answers/computer-fundamental.md?plain=1#L3721)


---

## User Interfaces (CLI vs GUI)

### Command Line Interface and Graphical User Interface

#### What is a CLI?

A **Command Line Interface (CLI)** is a **text-based user interface** in which the user interacts with the computer by **typing commands** at a prompt, and the system responds with text output.

**Examples:** **Command Prompt (cmd.exe)** and **PowerShell** on Windows · **Bash, Zsh, sh** on Linux and macOS · the **Cisco IOS CLI** on routers and switches · **MySQL** and **psql** database shells · **git**, **docker** and **kubectl**.

```
$ ls -l                      # list files in long format
$ cd /var/log                # change directory
$ grep "error" system.log    # search for text
$ ps aux | grep nginx        # find a running process
$ mkdir backup && cp *.conf backup/
```

#### Characteristics of a CLI

| Aspect | Detail |
|---|---|
| **Input** | Typed **commands** with options/flags and arguments |
| **Output** | **Plain text** |
| **Structure** | `command [options] [arguments]` — e.g. `cp -r source/ dest/` |
| **Needs** | The user must **know the command names and syntax** |
| **Power** | Commands can be **combined (pipes), scripted and automated** |

#### CLI vs GUI — the comparison

| Point | **CLI (Command Line Interface)** | **GUI (Graphical User Interface)** |
|---|---|---|
| **Interaction** | **Typing text commands** | **Clicking icons, menus, buttons, windows** |
| **Learning curve** | **Steep** — commands must be memorised | **Gentle** — visual, discoverable, intuitive |
| **Ease for a beginner** | Difficult | **Easy** |
| **Speed for an expert** | **Much faster** — one line does what takes many clicks | Slower for repetitive work |
| **Resource usage** | **Very low** — a few KB of memory, no graphics hardware | **High** — needs a graphics subsystem, more RAM and CPU |
| **Precision and control** | **Maximum** — every option is exposed | Limited to what the designer exposed in the interface |
| **Automation / scripting** | ✅ **Excellent** — the core strength; scripts, cron jobs, pipelines | ❌ **Poor** — clicking cannot easily be automated |
| **Remote administration** | ✅ **Ideal** — works over a slow SSH link with almost no bandwidth | Needs remote desktop and far more bandwidth |
| **Repeatability & documentation** | ✅ A command can be **copied, pasted, logged and audited** exactly | Hard to document "click here, then here" |
| **Multitasking** | Multiple sessions, background jobs (`&`), `screen`/`tmux` | Multiple windows |
| **Error messages** | Terse, sometimes cryptic | Usually friendly dialogs |
| **Risk** | **Higher** — a mistyped `rm -rf /` executes instantly with no confirmation | Lower — confirmation dialogs and undo |
| **Visual/graphical work** | ❌ Impossible — no images, drag and drop, or design work | ✅ **Essential** for design, video, browsing |
| **Memory/disk footprint** | Tiny | Large |
| **Used by** | System administrators, developers, network engineers, DevOps | **General users**, office workers |
| **Examples** | Bash, PowerShell, cmd, Cisco IOS | Windows Explorer, macOS Finder, GNOME/KDE, any app window |

#### When each is preferred

**Use the CLI when:** administering a **server** (most servers run with no GUI at all, to save resources); **automating** anything repetitive; working **remotely over SSH**; you need exact, auditable, repeatable operations; working with **version control, containers and cloud tooling**; or troubleshooting a system whose GUI has failed.

**Use the GUI when:** the user is a **non-technical end user**; the work is inherently **visual** (design, video, presentations, browsing); you are **exploring** an unfamiliar system and need discoverability; or you need to see **many things at once** in different windows.

> **In practice, professionals use both.** A Linux administrator may run a graphical desktop for the browser and documentation, while doing every administrative task in a terminal. Most modern tools (Git, Docker, cloud consoles) deliberately provide **both** a GUI for learning and a CLI for automation.

**Previous Year Question List from this Topic:**

- [What is CLI?](../written-answers/computer-fundamental.md?plain=1#L3896)

## Blockchain & Emerging Technologies

### Blockchain — Concept and How It Works

**Blockchain** is a **distributed, decentralised, immutable digital ledger** that records transactions across a **peer-to-peer network of computers**, in such a way that a recorded transaction **cannot be altered retroactively** without altering every block after it and gaining the agreement of the network majority.

> **A distributed ledger maintained on a peer-to-peer network is called a BLOCKCHAIN** (more generally, **Distributed Ledger Technology — DLT**).

**In plain words:** imagine a shared notebook that **thousands of people each hold an identical copy of**. Every new entry is announced to everyone, checked by everyone, and then written into **all** copies simultaneously. To forge an entry you would have to change **every copy at once** — which is practically impossible. There is **no bank, no government and no single company** in the middle; **trust comes from mathematics and from the majority of the network**, not from an authority.

#### The structure of a block

```mermaid
flowchart LR
    B1["BLOCK 1 (Genesis)<br/>─────────────<br/>Prev Hash: 0000<br/>Data: transactions<br/>Timestamp · Nonce<br/>Hash: 00a3f…"]
    B2["BLOCK 2<br/>─────────────<br/>Prev Hash: 00a3f…<br/>Data: transactions<br/>Timestamp · Nonce<br/>Hash: 00b7c…"]
    B3["BLOCK 3<br/>─────────────<br/>Prev Hash: 00b7c…<br/>Data: transactions<br/>Timestamp · Nonce<br/>Hash: 00d9e…"]
    B1 --> B2 --> B3
```

| Field | Purpose |
|---|---|
| **Block number / index** | Its position in the chain |
| **Timestamp** | When the block was created |
| **Data / Transactions** | The actual records (usually organised as a **Merkle tree**, whose root hash summarises them all) |
| **Previous block's hash** | **The link that forms the chain** — this is what makes tampering detectable |
| **Nonce** | A number miners vary to find a valid hash (Proof of Work) |
| **Own hash** | A **SHA-256** fingerprint of everything above |

#### How blockchain works — step by step

```mermaid
flowchart TD
    A["1 . A user REQUESTS a transaction<br/>(send 5 BTC to X)"] --> B["2 . The transaction is BROADCAST<br/>to the peer-to-peer network"]
    B --> C["3 . Nodes VALIDATE it<br/>— signature, balance, rules"]
    C --> D["4 . Valid transactions are grouped<br/>into a new BLOCK"]
    D --> E["5 . CONSENSUS — miners/validators compete<br/>(Proof of Work / Proof of Stake)"]
    E --> F["6 . The winning block is BROADCAST<br/>and verified by every node"]
    F --> G["7 . The block is APPENDED to the chain<br/>and linked by the previous hash"]
    G --> H["8 . Every node UPDATES its copy<br/>— the transaction is now permanent"]
```

#### The core concepts

| Concept | Meaning |
|---|---|
| **Distributed ledger** | Every node holds a **full copy**; there is no master copy |
| **Decentralisation** | **No single controlling authority** or point of failure |
| **Cryptographic hashing (SHA-256)** | Any change to a block changes its hash completely — the **avalanche effect** |
| **Immutability** | Because each block stores the previous block's hash, changing block 50 invalidates 51, 52, 53 … |
| **Consensus mechanism** | The rule by which the network agrees on the next block — **PoW, PoS, PBFT, PoA** |
| **Digital signature** | Each transaction is signed with the sender's **private key** and verified with their **public key** |
| **Smart contract** | Self-executing code stored on the chain that runs automatically when conditions are met (Ethereum) |
| **Merkle tree** | A hash tree summarising all transactions in a block into a single root hash |
| **Mining** | Solving the computational puzzle to earn the right to add the next block |

#### Consensus mechanisms

| Mechanism | How it works | Used by | Trade-off |
|---|---|---|---|
| **Proof of Work (PoW)** | Miners race to find a nonce that makes the block hash start with enough zeros | **Bitcoin** | Extremely **secure** but consumes enormous **energy** |
| **Proof of Stake (PoS)** | Validators are chosen in proportion to the coins they "stake" as collateral | **Ethereum (since 2022)**, Cardano | ~99.9 % less energy; risk of favouring the wealthy |
| **Delegated PoS** | Token holders elect a small set of validators | EOS, TRON | Fast but more centralised |
| **PBFT / Raft** | Voting among a known set of nodes | **Hyperledger Fabric** (private chains) | Very fast; requires known participants |
| **Proof of Authority** | Pre-approved, identified validators | Private/consortium chains | Fast, but trust is placed in the authorities |

#### Why blockchain is secure

1. **Cryptographic chaining.** Each block contains the hash of the previous one, so altering any past block **breaks every subsequent link**, and the tampering is instantly visible.
2. **Distributed copies.** Thousands of nodes hold identical copies; an attacker must change them **all simultaneously**.
3. **Consensus requirement.** To rewrite history an attacker needs control of **more than 50 % of the network's hash power or stake** — the **"51 % attack"** — which for Bitcoin would cost billions of dollars and be economically irrational.
4. **Proof of Work cost.** Re-mining a changed block **and every block after it**, faster than the honest network extends the chain, is computationally infeasible.
5. **Digital signatures.** Only the holder of the **private key** can authorise a transfer; forging a signature is cryptographically impossible.
6. **Transparency and auditability.** Every participant can verify the whole history independently, so fraud is detected immediately.
7. **No single point of failure.** There is no central server to hack, bribe or shut down.
8. **Immutability by design.** Records are **append-only** — data can be added but never silently edited or deleted.

#### Types of blockchain

| Type | Access | Example | Use |
|---|---|---|---|
| **Public (permissionless)** | Anyone can join, read and validate | **Bitcoin, Ethereum** | Cryptocurrency, DeFi, NFTs |
| **Private (permissioned)** | Only invited members of one organisation | Hyperledger Fabric | Internal enterprise records |
| **Consortium / Federated** | A group of organisations jointly control it | Trade-finance networks, **R3 Corda** | Inter-bank settlement, supply chains |
| **Hybrid** | Some data public, some private | — | Regulated industries |

#### Top benefits of blockchain

1. **Security** — cryptographically protected and tamper-evident.
2. **Transparency** — all participants see the same verified record.
3. **Immutability** — a permanent, auditable history.
4. **Decentralisation** — no single point of failure or control.
5. **No intermediaries** — removes brokers, clearing houses and correspondent banks, cutting **cost and time**.
6. **Faster settlement** — cross-border payments in minutes instead of 3–5 days.
7. **Traceability** — full provenance of every asset from origin to destination.
8. **Automation through smart contracts** — payment releases automatically when a shipment is delivered.
9. **Reduced fraud** — records cannot be quietly altered.
10. **Availability** — 24×7, with no downtime from a central server.

#### Limitations

**Scalability** — Bitcoin handles about 7 transactions per second and Ethereum about 15–30, against Visa's ~24,000. **Energy consumption** of Proof of Work is enormous. **Storage growth** — every node stores the entire history. **Irreversibility** — a mistaken or fraudulent transfer cannot be undone. **Regulatory uncertainty** and legal status. **Privacy** — a public ledger exposes transaction patterns. **Key management** — lose your private key and the assets are gone forever. **Complexity and skills shortage**. **The 51 % risk** on small networks.

#### Traditional database vs Blockchain

| Point | **Traditional Database** | **Blockchain** |
|---|---|---|
| **Control** | **Centralised** — one administrator/organisation | **Decentralised** — shared across all participants |
| **Architecture** | Client–server | **Peer-to-peer** |
| **Operations** | **CRUD** — Create, Read, **Update, Delete** | **Only INSERT and READ** — append-only |
| **Data modification** | Records can be **edited or deleted** by an admin | **Immutable** — nothing can be altered or removed |
| **Trust model** | You must **trust the administrator** | **Trustless** — trust the protocol and the majority |
| **Transparency** | Restricted; visible to authorised users only | **Full transparency** to all participants (in a public chain) |
| **Performance** | **Very high** — thousands to millions of TPS | **Low** — 7 to a few thousand TPS |
| **Storage cost** | One copy | **Replicated on every node** — far more expensive |
| **Data integrity** | Depends on the admin's controls | **Cryptographically guaranteed** |
| **Single point of failure** | ✅ Yes | ❌ No |
| **History / audit** | Can be overwritten; audit logs can be tampered with by an admin | **Complete, permanent, verifiable history** |
| **Best for** | High-volume business applications, where one trusted owner exists | Multi-party situations where **participants do not fully trust each other** |

> **When should you NOT use blockchain?** If there is a single trusted owner of the data, if the data must be edited or deleted (GDPR "right to be forgotten"), if you need high throughput, or if no multiple parties are involved — **a normal database is better, cheaper and faster.** Blockchain earns its cost only when **mutual distrust between parties** is the core problem.

#### Applications of blockchain

| Sector | Application |
|---|---|
| **Finance** | Cryptocurrency, **cross-border remittance**, trade finance and letters of credit, settlement, DeFi |
| **Banking** | KYC sharing between banks, syndicated loans, bond issuance, audit trails |
| **Supply chain** | Provenance and traceability — food safety, pharmaceuticals, **garment supply chain (highly relevant to Bangladesh's RMG exports)** |
| **Government** | **Land registry**, birth/death records, digital identity, **tamper-proof voting** |
| **Healthcare** | Secure, patient-controlled medical records; drug authenticity |
| **Education** | Verifiable digital certificates and degrees — instantly checkable, impossible to forge |
| **Energy** | Peer-to-peer solar energy trading |
| **Legal** | Smart contracts, notarisation, intellectual-property registration |
| **Insurance** | Automatic parametric claim settlement |
| **Charity/aid** | Transparent tracking of donations and relief funds |

**Previous Year Question List from this Topic:**

- [What is Blockchain technology? How it works?](../written-answers/computer-fundamental.md?plain=1#L3376)
- [What is blockchain technology? Why it is more secure( Such type)](../written-answers/computer-fundamental.md?plain=1#L3409)
- [Write about Blockchain.](../written-answers/computer-fundamental.md?plain=1#L3428)
- [What is Blockchain? How does work it? Mention 5 top benefits of blockchain. Write down the difference between Traditional banking and Digital banking.](../written-answers/computer-fundamental.md?plain=1#L3457)
- [A distributive ledger in a peer-to-peer network is called?](../written-answers/computer-fundamental.md?plain=1#L3489)
- [(a) Write short note on (i) Blockchain technology (ii) Cloud Computing](../written-answers/computer-fundamental.md?plain=1#L3497)
- [Write short notes on the following: (a) Digital Signature (b) Cloud Computing (c) Block Chain (d) TOT](../written-answers/computer-fundamental.md?plain=1#L3517)
- [Write short note on the folloing topics](../written-answers/computer-fundamental.md?plain=1#L3544)


---

### Other Emerging Technology Short Notes

#### Digital signature

A **digital signature** is a **cryptographic mechanism that verifies the authenticity and integrity of a digital message or document**, and proves who created it.

```mermaid
flowchart LR
    subgraph SIGN["SIGNING — by the sender"]
        D["Document"] --> H1["Hash function<br/>SHA-256"]
        H1 --> HD["Message digest"]
        HD --> E["Encrypt with the<br/>SENDER'S PRIVATE KEY"]
        E --> S["DIGITAL SIGNATURE"]
    end
    subgraph VERIFY["VERIFICATION — by the receiver"]
        S2["Signature"] --> DE["Decrypt with the<br/>SENDER'S PUBLIC KEY"]
        DE --> HD2["Digest A"]
        D2["Received document"] --> H2["Hash function"]
        H2 --> HD3["Digest B"]
        HD2 --> C{"A = B ?"}
        HD3 --> C
        C -->|Yes| OK["✅ Authentic and unaltered"]
        C -->|No| BAD["❌ Forged or tampered"]
    end
```

**What it guarantees:**

| Property | Meaning |
|---|---|
| **Authentication** | Proves **who** signed it — only the holder of the private key could have |
| **Integrity** | Proves the document **has not been changed** — any change alters the hash |
| **Non-repudiation** | The signer **cannot later deny** having signed it |

**Note:** a digital signature does **not** provide **confidentiality** — the document itself is still readable unless it is separately encrypted.

**Handwritten vs digital signature:** a handwritten signature is the same on every document and can be copied; a **digital signature is different for every document** (because it depends on the document's hash) and cannot be transferred to another document.

**Uses:** e-tender and e-GP submissions, e-banking instructions, software code signing, SSL/TLS certificates, legally valid e-documents (recognised in Bangladesh under the **ICT Act 2006**), email signing (S/MIME, PGP).

#### Internet of Things (IoT)

**IoT** is a network of **physical objects embedded with sensors, software and connectivity** that collect and exchange data over the Internet, with little or no human intervention.

**Architecture:** **Perception layer** (sensors and actuators) → **Network layer** (Wi-Fi, 4G/5G, LoRaWAN, Zigbee, Bluetooth) → **Edge/Fog layer** (local gateways) → **Cloud/Application layer** (storage, analytics, dashboards).

**Applications:** smart home (lights, AC, locks), **smart agriculture** (soil moisture, automated irrigation), **smart metering** for electricity and gas, healthcare wearables, industrial predictive maintenance, smart city traffic and waste management, vehicle and fleet tracking, **cold-chain monitoring**.

**Challenges:** **security** (billions of weakly protected devices — the Mirai botnet built from IoT cameras), **privacy**, lack of **standards and interoperability**, **power** for remote sensors, network coverage, and the sheer **volume of data** generated.

#### Microcontroller

A **microcontroller** is a **complete small computer on a single chip** — CPU + memory (RAM and flash) + input/output ports — designed to control one specific embedded task.

| Point | **Microprocessor** | **Microcontroller** |
|---|---|---|
| **Contains** | Only the **CPU** | **CPU + RAM + ROM/Flash + I/O ports + timers + ADC** |
| **External components** | Needs external memory and I/O chips | **Self-contained** — a "computer on a chip" |
| **Cost** | Higher | **Very low** |
| **Power consumption** | High | **Very low** |
| **Clock speed** | GHz | MHz |
| **Purpose** | **General purpose** computing | **Dedicated, embedded control** |
| **Examples** | Intel Core i7, AMD Ryzen, ARM Cortex-A | **8051, AVR (Arduino), PIC, ESP32, ARM Cortex-M** |
| **Used in** | PCs, laptops, servers, smartphones | Washing machines, microwave ovens, cars, **IoT devices**, remote controls, medical devices |

#### Genetic algorithm

A **genetic algorithm (GA)** is an **optimisation and search technique inspired by natural evolution and Darwin's "survival of the fittest"**.

```mermaid
flowchart LR
    A["1 . Initial POPULATION<br/>random candidate solutions"] --> B["2 . FITNESS evaluation<br/>score each solution"]
    B --> C["3 . SELECTION<br/>pick the fittest as parents"]
    C --> D["4 . CROSSOVER<br/>combine two parents"]
    D --> E["5 . MUTATION<br/>random small changes"]
    E --> F{"Good enough<br/>or max generations?"}
    F -->|No| B
    F -->|Yes| G["Best solution found"]
```

**Terminology:** a **chromosome** is one candidate solution (often encoded as a bit string); a **gene** is one element of it; the **fitness function** measures how good a solution is; **crossover** mixes two parents; **mutation** introduces random variation to avoid getting stuck in a local optimum.

**Used for:** the Travelling Salesman Problem, timetable and exam scheduling, neural-network architecture search, engineering design optimisation, route and network planning, feature selection in machine learning, and portfolio optimisation.

**Advantages:** works on problems with **no known mathematical formula**; escapes **local optima** better than hill climbing; naturally parallel. **Disadvantages:** gives a **good** answer, not a **provably optimal** one; computationally expensive; needs careful tuning of population size, crossover and mutation rates.

#### COCOMO

**COCOMO (COnstructive COst MOdel)**, developed by **Barry Boehm (1981)**, is an **algorithmic model for estimating the effort, time and cost of a software project** from its estimated size in **KLOC (thousands of lines of code)**.

> **Effort (person-months) E = a × (KLOC)^b**
> **Development time (months) D = c × E^d**

| Project type | Description | a | b | c | d |
|---|---|---|---|---|---|
| **Organic** | Small team, familiar problem, flexible requirements | **2.4** | **1.05** | 2.5 | 0.38 |
| **Semi-detached** | Medium size, mixed experience, moderate constraints | **3.0** | **1.12** | 2.5 | 0.35 |
| **Embedded** | Large, complex, tight hardware/regulatory constraints | **3.6** | **1.20** | 2.5 | 0.32 |

**Worked example:** an **organic** project estimated at **40 KLOC**:
- Effort E = 2.4 × 40^1.05 = 2.4 × 47.9 ≈ **115 person-months**
- Time D = 2.5 × 115^0.38 ≈ 2.5 × 6.06 ≈ **15 months**
- Average staff = E ÷ D = 115 ÷ 15 ≈ **8 people**

**The three levels:** **Basic** (size only), **Intermediate** (adds 15 cost drivers such as product complexity, team capability and tool support), and **Detailed** (applies the drivers phase by phase). **COCOMO II** (1995) updates it for modern reuse-based and object-oriented development.

**Limitation:** it depends entirely on an accurate **estimate of KLOC**, which is notoriously hard to make early in a project — the core weakness of all size-based estimation.

#### Query optimisation

**Query optimisation** is the process by which a **DBMS finds the most efficient way to execute a given SQL query** — the **execution plan** that returns the correct result with the least cost in disk I/O, CPU and memory.

**Why it is needed:** SQL is **declarative** — you state *what* data you want, not *how* to get it. For a join of three tables there may be **dozens of possible execution plans** whose running times differ by a factor of thousands. The optimiser's job is to pick a good one.

**The process:** **Parsing** → **Translation** into relational algebra → **Optimisation** (generate candidate plans and estimate their cost using table statistics) → **Execution**.

**Common techniques:** push **selections and projections down** the tree so that less data flows upward · choose the best **join order** (join the most selective tables first) · choose the best **join algorithm** (nested loop, hash join, sort-merge) · use available **indexes** instead of full table scans · eliminate redundant sub-queries · use **materialised views** and cached plans.

**What a developer can do:** create appropriate **indexes**; avoid `SELECT *`; avoid functions on indexed columns in the `WHERE` clause (they prevent index use); filter **before** joining; keep **statistics up to date**; and read the **`EXPLAIN` / execution plan** to see what the optimiser actually chose.

**Previous Year Question List from this Topic:**

- [(a) Write short note on (i) Blockchain technology (ii) Cloud Computing](../written-answers/computer-fundamental.md?plain=1#L3497)
- [Write short notes on the following: (a) Digital Signature (b) Cloud Computing (c) Block Chain (d) TOT](../written-answers/computer-fundamental.md?plain=1#L3517)
- [Write short note on the folloing topics](../written-answers/computer-fundamental.md?plain=1#L3544)
- [Write short answer on the following: (a) Plaintext (b) HTTP (c) Gateway used in \underline{\phantom{\text{Network}}} layer. (d) VIRUS full form (e) Who is the f…](../written-answers/computer-fundamental.md?plain=1#L458)
- [Describe about Firewalls, Microcontroller, COCOMO, Query Optimization, Genetic algorithm and UML.](../written-answers/computer-fundamental.md?plain=1#L919)
