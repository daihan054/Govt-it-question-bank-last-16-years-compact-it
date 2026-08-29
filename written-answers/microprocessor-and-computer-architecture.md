<!-- TOC START -->
**Table of Contents** — 11 subtopics · 107 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Microprocessor Architecture & Functions](#microprocessor-architecture--functions-27) | 27 |
| 2 | [Memory Hierarchy & Storage](#memory-hierarchy--storage-21) | 21 |
| 3 | [RAID Architecture & Storage](#raid-architecture--storage-13) | 13 |
| 4 | [Cache Memory](#cache-memory-12) | 12 |
| 5 | [Secondary Storage (HDD vs SSD)](#secondary-storage-hdd-vs-ssd-10) | 10 |
| 6 | [Multi-Core & Multi-Threading](#multi-core--multi-threading-5) | 5 |
| 7 | [Assembly Language & Addressing Modes](#assembly-language--addressing-modes-5) | 5 |
| 8 | [Instruction Pipelining & Hazards](#instruction-pipelining--hazards-5) | 5 |
| 9 | [CPU Performance & Instruction Cycle](#cpu-performance--instruction-cycle-4) | 4 |
| 10 | [8085 Microprocessor & Edge Computing](#8085-microprocessor--edge-computing-3) | 3 |
| 11 | [RISC vs CISC Architecture](#risc-vs-cisc-architecture-2) | 2 |

<!-- TOC END -->

---

## Microprocessor Architecture & Functions (27)

1. **ছোট প্রসেসরের (Microprocessor) কাজ এক নজরে এবং কী কী?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*


   Answer: মাইক্রোপ্রসেসর হলো একটি সিলিকন চিপে তৈরি সম্পূর্ণ কেন্দ্রীয় প্রক্রিয়াকরণ একক (CPU), যা কম্পিউটারের সব হিসাব ও নিয়ন্ত্রণের কাজ সম্পাদন করে।

   এক নজরে প্রধান কাজসমূহ:
   - নির্দেশ আনয়ন (Fetch): প্রোগ্রাম কাউন্টারে থাকা ঠিকানা অনুযায়ী মেমোরি থেকে পরবর্তী নির্দেশটি নিয়ে আসে।
   - নির্দেশ বিশ্লেষণ (Decode): কন্ট্রোল ইউনিট নির্দেশটি বিশ্লেষণ করে বুঝে নেয় কোন কাজ করতে হবে এবং কোন অপারেন্ড লাগবে।
   - নির্দেশ সম্পাদন (Execute): ALU এর মাধ্যমে গাণিতিক ও যৌক্তিক কাজ সম্পন্ন করে।
   - ফলাফল সংরক্ষণ (Store): ফলাফল রেজিস্টার বা মেমোরিতে লিখে রাখে।
   - গাণিতিক কাজ: যোগ, বিয়োগ, গুণ, ভাগ ও তুলনা।
   - যৌক্তিক কাজ: AND, OR, NOT, XOR এবং শিফট ও রোটেট।
   - ডেটা স্থানান্তর: রেজিস্টার, মেমোরি ও ইনপুট-আউটপুট যন্ত্রের মধ্যে তথ্য আদান-প্রদান।
   - সময় ও নিয়ন্ত্রণ সংকেত তৈরি: ঘড়ির স্পন্দনের সঙ্গে সমন্বয় রেখে READ, WRITE ও অন্যান্য নিয়ন্ত্রণ সংকেত পাঠানো।
   - ইন্টারাপ্ট ব্যবস্থাপনা: বাইরের যন্ত্র থেকে আসা জরুরি অনুরোধে সাড়া দিয়ে চলমান কাজ স্থগিত রেখে সেবা প্রদান।
   - প্রোগ্রাম প্রবাহ নিয়ন্ত্রণ: শর্তসাপেক্ষ ও নিঃশর্ত জাম্প, কল ও রিটার্ন সম্পাদন করে।
   - স্ট্যাক ব্যবস্থাপনা: সাবরুটিন কল ও ইন্টারাপ্টের সময় প্রসঙ্গ (context) সংরক্ষণ ও পুনরুদ্ধার।

   গঠনগত অংশ তিনটি:
   - ALU (Arithmetic Logic Unit): হিসাব ও যুক্তির কাজ করে।
   - Control Unit (CU): সব অংশের কাজ পরিচালনা ও সমন্বয় করে।
   - Register set: অতি দ্রুত অস্থায়ী তথ্য সংরক্ষণ করে।

   ইতিহাস: বিশ্বের প্রথম মাইক্রোপ্রসেসর ইন্টেল ৪০০৪, যা ১৯৭১ সালে বাজারে আসে। এটি ছিল ৪ বিটের এবং এতে প্রায় ২,৩০০টি ট্রানজিস্টর ছিল।
2. **b) Compare and contrast between CPU and GPU.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1342 (ET: N/A)]*


   Answer:

   | Point | CPU (Central Processing Unit) | GPU (Graphics Processing Unit) |
   |---|---|---|
   | Design goal | Low latency on a single task | High throughput on many identical tasks |
   | Number of cores | Few, typically 4 to 64, but each is powerful | Thousands of small, simple cores |
   | Core complexity | Complex, with branch prediction, out-of-order execution and large caches | Simple, optimised for arithmetic |
   | Type of parallelism | Task parallelism, running different tasks at once | Data parallelism, running the same operation on many data items at once (SIMD) |
   | Cache | Large, several levels, tens of megabytes | Small per core, but very high memory bandwidth |
   | Clock speed | Higher, 3 to 5 GHz | Lower, 1 to 2 GHz |
   | Control logic | A large part of the chip | A small part of the chip; most of it is arithmetic units |
   | Branch handling | Very good | Poor; divergent branches slow it down badly |
   | Memory bandwidth | Moderate, tens of GB per second | Very high, hundreds of GB to several TB per second |
   | Best at | Operating systems, databases, compilers, sequential and branch-heavy code | Graphics rendering, matrix and vector operations, image processing, deep learning, cryptocurrency mining, scientific simulation |
   | Programming | C, Java, Python and ordinary compilers | CUDA, OpenCL, and frameworks such as TensorFlow and PyTorch |

   Similarity: both are processors built from transistors, both execute instructions, both have cores, registers, caches and arithmetic units, and both are fabricated with the same semiconductor technology.

   How they work together: the CPU acts as the manager. It runs the operating system, prepares the data, and hands large parallel workloads to the GPU, which returns the results. This division is called heterogeneous computing.

   Simple analogy: a CPU is a few university professors who can solve any hard problem but only a few at a time; a GPU is a thousand school students who can each do simple arithmetic, so together they finish a thousand simple sums far faster than the professors could.
3. **What exactly is a microcontroller? What distinguishes a microprocessor from a microcontroller? Mention the differences between RISC and CISC microprocessors.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 323 (ET: BIBM)]*


   Answer: A microcontroller is a complete small computer built on a single integrated circuit. It contains a CPU core, program memory (ROM or Flash), data memory (RAM), and input-output peripherals such as timers, counters, serial ports and analogue-to-digital converters, all on the same chip. It is designed to control one dedicated task in an embedded system rather than to run general-purpose software.

   Difference between a microprocessor and a microcontroller:

   | Point | Microprocessor | Microcontroller |
   |---|---|---|
   | Definition | A single-chip CPU only | A single chip containing CPU, memory and I/O ports |
   | Memory | RAM and ROM must be connected externally | RAM, ROM/Flash and EEPROM are built in |
   | Peripherals | Timers, serial ports, ADC must be added externally | Timers, counters, UART, SPI, I2C, ADC and PWM are on chip |
   | Bus structure | Address, data and control buses are brought out to pins | Buses are internal, so fewer external pins are needed |
   | Cost of a complete system | High, because many support chips are required | Low, because one chip does the whole job |
   | Power consumption | High, generally watts | Very low, milliwatts, with sleep modes |
   | Clock speed | High, GHz range | Low, typically 8 MHz to 200 MHz |
   | Architecture | Usually von Neumann | Usually Harvard, with separate program and data memory |
   | Design purpose | General purpose computing, runs an operating system | Dedicated control of one embedded task |
   | Real-time response | Not deterministic | Deterministic, suited to real-time control |
   | Board size | Large, needs a motherboard | Small, often a single small board |
   | Examples | Intel Core i7, AMD Ryzen, Intel 8086 | Intel 8051, ATmega328 (Arduino), PIC16F877A, ESP32, ARM Cortex-M |
   | Applications | Desktop and laptop computers, servers, smartphones | Washing machines, microwave ovens, digital cameras, ATMs, cars, robots, IoT devices |

   In one sentence: a microprocessor is the brain alone and needs a body of support chips, while a microcontroller is a complete small computer on one chip.

   Difference between RISC and CISC microprocessors:

   | Point | RISC (Reduced Instruction Set Computer) | CISC (Complex Instruction Set Computer) |
   |---|---|---|
   | Instruction set | Small, simple, about 100 instructions | Large, complex, several hundred instructions |
   | Instruction length | Fixed length, typically 32 bits | Variable length, 1 to 15 bytes |
   | Execution time | Mostly one clock cycle per instruction | Several clock cycles per instruction |
   | Addressing modes | Few, typically 3 to 5 | Many, 12 to 20 or more |
   | Memory access | Only by dedicated load and store instructions | Almost any instruction can access memory |
   | Registers | Many, typically 32 or more | Few, typically 8 to 16 |
   | Pipelining | Easy and highly efficient | Difficult because of variable instruction length |
   | Control unit | Hardwired, so it is fast | Microprogrammed, so it is flexible but slower |
   | Code size | Larger, more instructions per program | Smaller, one instruction does more work |
   | Compiler | Complex, must do more optimisation | Simpler, hardware does more of the work |
   | Power consumption | Low, so it suits battery-powered devices | Higher |
   | Chip complexity | Simpler, leaves room for cache and more registers | Complex control logic uses much of the chip |
   | Examples | ARM, MIPS, SPARC, PowerPC, RISC-V, Apple M series | Intel x86, AMD x86-64, Intel 8086, Motorola 68000 |

   Note: modern x86 processors are CISC on the outside but internally translate each complex instruction into simple RISC-like micro-operations, so the two philosophies have converged in practice.
4. **GPU stands for __________?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*


   Answer: GPU stands for Graphics Processing Unit.

   - It is a specialised electronic circuit designed to accelerate the creation and manipulation of images, and more generally to perform a large number of identical arithmetic operations in parallel.
   - It was originally built for rendering three-dimensional graphics in games and design software, where the same lighting and transformation calculation must be applied to millions of pixels and vertices.
   - Because that workload is highly parallel, GPUs proved equally suited to scientific computing, video encoding, image processing, cryptocurrency mining and, above all, training and running deep neural networks. This wider use is called GPGPU, General Purpose computing on Graphics Processing Units.
   - Types: an integrated GPU shares memory with the CPU and is built into the same chip, while a discrete GPU is a separate card with its own high-bandwidth memory.
   - Major manufacturers: NVIDIA (GeForce, Tesla, RTX), AMD (Radeon) and Intel (Arc, and integrated graphics).
5. **Maximum three word complete this below section:** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 431 (ET: BUET)]*

| Question | Answer |
|---|---|
| (a) Which bus transfers data between data and I/O Data Bus devices? | Data Bus |
| (b) Which register contains the address of next instructions? | Program counter |
| (c) Which register does the arithmetic and logical operation? | Arithmetic Logic Unit (ALU) |
| (d) Which system connects the hardware and software? | Operating System(OS) |
| (e) Microprocessor and other peripherals are interfaced Microcontroller, with which board? | Microcontrollers, Motherboard |

6. **ALU কী? এর কার্যপদ্ধতি চিত্রসহ বর্ণনা করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 405 (ET: N/A)]*


   Answer: ALU এর পূর্ণরূপ Arithmetic Logic Unit বা গাণিতিক ও যুক্তি একক। এটি সিপিইউ-এর সেই অংশ যেখানে প্রকৃত হিসাব ও যৌক্তিক সিদ্ধান্ত নেওয়ার কাজ সম্পন্ন হয়। একে সিপিইউ-এর "কর্মশালা" বলা যায়।

   কাজসমূহ:
   - গাণিতিক কাজ: যোগ, বিয়োগ, গুণ, ভাগ, বৃদ্ধি (increment) ও হ্রাস (decrement)।
   - যৌক্তিক কাজ: AND, OR, NOT, XOR।
   - তুলনামূলক কাজ: দুইটি সংখ্যা সমান কিনা, বড় না ছোট তা নির্ণয়।
   - বিট ম্যানিপুলেশন: শিফট লেফট, শিফট রাইট, রোটেট।

   গঠন ও কার্যপদ্ধতির চিত্র:

   ```mermaid
   flowchart LR
     A[Register A - Operand 1] --> ALU[Arithmetic Logic Unit]
     B[Register B - Operand 2] --> ALU
     CU[Control Unit - Opcode / Function Select] --> ALU
     ALU --> ACC[Accumulator - Result]
     ALU --> FLAG[Flag Register - Carry, Zero, Sign, Overflow, Parity]
   ```

   কার্যপদ্ধতি ধাপে ধাপে:
   - ধাপ ১: কন্ট্রোল ইউনিট নির্দেশ বিশ্লেষণ করে ঠিক করে কোন কাজটি করতে হবে এবং ফাংশন সিলেক্ট লাইনে সংশ্লিষ্ট সংকেত পাঠায়।
   - ধাপ ২: প্রয়োজনীয় দুইটি অপারেন্ড রেজিস্টার বা মেমোরি থেকে ALU-এর দুই ইনপুট লাইনে আসে।
   - ধাপ ৩: ফাংশন সিলেক্ট সংকেত অনুযায়ী ALU-এর ভেতরের নির্দিষ্ট সার্কিট (যেমন অ্যাডার, তুলনাকারী বা লজিক গেট গুচ্ছ) সক্রিয় হয়।
   - ধাপ ৪: ফলাফল আউটপুট লাইনে আসে এবং সাধারণত অ্যাকিউমুলেটরে সংরক্ষিত হয়।
   - ধাপ ৫: একই সঙ্গে ফলাফলের বৈশিষ্ট্য অনুযায়ী ফ্ল্যাগ রেজিস্টারের বিটগুলো সেট বা রিসেট হয়।

   প্রধান ফ্ল্যাগসমূহ:
   - Carry Flag: যোগে হাতে থাকলে বা বিয়োগে ধার নিলে সেট হয়।
   - Zero Flag: ফলাফল শূন্য হলে সেট হয়।
   - Sign Flag: ফলাফল ঋণাত্মক হলে (MSB = 1) সেট হয়।
   - Overflow Flag: চিহ্নযুক্ত সংখ্যার ফলাফল ধারণক্ষমতা ছাড়িয়ে গেলে সেট হয়।
   - Parity Flag: ফলাফলে ১ এর সংখ্যা জোড় হলে সেট হয়।

   ভেতরের গঠন: ALU মূলত অ্যাডার-সাবট্রাক্টর, লজিক গেট গুচ্ছ, শিফটার এবং একটি মাল্টিপ্লেক্সার দিয়ে গঠিত। মাল্টিপ্লেক্সারটি ফাংশন সিলেক্ট সংকেত অনুযায়ী কোন সার্কিটের ফলাফল আউটপুটে যাবে তা নির্বাচন করে। বিয়োগের কাজ আলাদা সার্কিট দিয়ে নয়, বরং ২ এর পরিপূরক নিয়ে যোগ করেই সম্পন্ন হয়, যা হার্ডওয়্যার সাশ্রয় করে।
7. **(ক) Microprocessor এবং Microcontroller এর মাঝে দুইটি পার্থক্য লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*


   Answer: Microprocessor ও Microcontroller এর মধ্যে দুইটি প্রধান পার্থক্য:

   - মেমোরি ও পেরিফেরালের অবস্থান: মাইক্রোপ্রসেসরে কেবল সিপিইউ থাকে; RAM, ROM, টাইমার ও ইনপুট-আউটপুট পোর্ট বাইরে থেকে যুক্ত করতে হয়। পক্ষান্তরে মাইক্রোকন্ট্রোলারে সিপিইউ, RAM, ROM/Flash, টাইমার, সিরিয়াল পোর্ট ও ADC সবই একই চিপের ভেতরে থাকে, তাই একটি চিপেই সম্পূর্ণ ব্যবস্থা তৈরি করা যায়।

   - ব্যবহারের উদ্দেশ্য ও ক্ষমতা: মাইক্রোপ্রসেসর সাধারণ উদ্দেশ্যে ব্যবহৃত হয়, অপারেটিং সিস্টেম চালায়, গতি গিগাহার্জ পর্যায়ে এবং বিদ্যুৎ খরচ বেশি। মাইক্রোকন্ট্রোলার একটি নির্দিষ্ট নিয়ন্ত্রণকাজের জন্য তৈরি, গতি মেগাহার্জ পর্যায়ে, বিদ্যুৎ খরচ অত্যন্ত কম এবং রিয়েল-টাইম সাড়াদানে নির্ভরযোগ্য।

   অতিরিক্ত পার্থক্য:
   - খরচ: সম্পূর্ণ ব্যবস্থার খরচ মাইক্রোকন্ট্রোলারে অনেক কম।
   - স্থাপত্য: মাইক্রোপ্রসেসর সাধারণত ভন নিউম্যান, আর মাইক্রোকন্ট্রোলার সাধারণত হার্ভার্ড স্থাপত্য অনুসরণ করে।
   - উদাহরণ: মাইক্রোপ্রসেসর — Intel Core i7, Intel 8086; মাইক্রোকন্ট্রোলার — Intel 8051, ATmega328, ESP32।
   - প্রয়োগ: মাইক্রোপ্রসেসর ডেস্কটপ, ল্যাপটপ ও সার্ভারে; মাইক্রোকন্ট্রোলার ওয়াশিং মেশিন, মাইক্রোওয়েভ ওভেন, এটিএম, গাড়ি ও আইওটি যন্ত্রে।
8. **Discuss the factors that affect the Speed of a CPU.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 541 (ET: MIST)]*


   Answer: The speed of a CPU is not decided by the clock frequency alone. The following factors together determine how fast a processor actually finishes work.

   - Clock speed (clock rate): the number of cycles per second, measured in GHz. A higher clock means more cycles per second, but it also means more heat and more power consumption, which limits how far it can be raised.
   - Number of cores: more cores allow more threads to run truly in parallel. This helps only when the software is written to use multiple threads.
   - Instructions per cycle (IPC): how much work the processor completes in each cycle. Superscalar design, out-of-order execution and better branch prediction all raise IPC. Real performance is roughly clock speed multiplied by IPC.
   - Word size: a 64-bit processor handles 64 bits per operation and can address far more memory than a 32-bit one.
   - Cache memory: the size, number of levels and hit rate of L1, L2 and L3 cache. A cache miss forces the CPU to wait for main memory, which is roughly a hundred times slower, so cache is often the single biggest practical factor.
   - Pipelining and its depth: pipelining allows several instructions to be in different stages at the same time. A deeper pipeline allows a higher clock but suffers more from branch mispredictions.
   - Bus width and speed: the width of the data and address buses and the speed of the front-side bus or interconnect limit how quickly data reaches the CPU.
   - Main memory speed and bandwidth: DDR generation, frequency and channel count. A fast CPU starved of data cannot perform.
   - Instruction set architecture: RISC or CISC, and the availability of vector instructions such as SSE and AVX that process many data items in one instruction.
   - Fabrication technology: a smaller process node, for example 5 nm instead of 14 nm, packs more transistors, switches faster and uses less power.
   - Thermal design and cooling: if the chip overheats it reduces its own clock speed, which is called thermal throttling. Good cooling therefore directly affects sustained speed.
   - Power supply and management: a stable supply and features such as turbo boost, which raises the clock temporarily when thermal headroom allows.
   - Software factors: the efficiency of the compiler, the algorithm used, the operating system scheduler, and how well the workload matches the hardware.

   Performance equation that ties several of these together:

   CPU time = (Instruction count) x (Cycles per instruction) x (Clock cycle time)

   To make a program run faster, any of the three terms can be reduced: fewer instructions through a better algorithm or compiler, fewer cycles per instruction through better architecture, or a shorter cycle time through a higher clock.
9. **Difference between 32 bit Microprocessor and 64 bit Microprocessor with example. What is the meaning of 2.40GHz Microprocessor? Differentiate among Core Intel i3, i5 and i7 processor. Why do you prefer SSD instead of HD?** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 508 (ET: MIST)]*


   Answer:

   Difference between a 32-bit and a 64-bit microprocessor:

   | Point | 32-bit Microprocessor | 64-bit Microprocessor |
   |---|---|---|
   | Word size | Processes 32 bits at a time | Processes 64 bits at a time |
   | Register width | 32 bits | 64 bits |
   | Addressable memory | 2^32 = 4 GB | 2^64 = 16 exabytes in theory; current chips support 256 TB or more |
   | Number of registers | Fewer general-purpose registers | More registers, which reduces memory traffic |
   | Performance | Adequate for ordinary work | Better for large data sets, scientific work, video editing and databases |
   | Operating system | Runs 32-bit operating systems only | Runs both 64-bit and, with compatibility support, 32-bit operating systems |
   | Software compatibility | Cannot run 64-bit software | Runs both 32-bit and 64-bit software |
   | Examples | Intel 80386, Intel 80486, Pentium 4 (early versions) | Intel Core i3, i5, i7, i9, AMD Ryzen, Apple M series, ARM64 |

   Meaning of a 2.40 GHz microprocessor:
   - GHz stands for gigahertz, that is one thousand million cycles per second.
   - 2.40 GHz means the processor's internal clock completes 2,400,000,000 cycles every second, and every internal operation is synchronised to that clock.
   - It does not mean the processor executes 2.4 billion instructions per second. A modern superscalar processor may finish several instructions in one cycle, while a memory access may stall it for hundreds of cycles.
   - Real performance is roughly the clock speed multiplied by the instructions completed per cycle, so a 2.4 GHz processor of a newer generation can easily outperform a 3.0 GHz processor of an older one.

   Difference among Intel Core i3, i5 and i7:

   | Point | Core i3 | Core i5 | Core i7 |
   |---|---|---|---|
   | Target user | Entry level, everyday use | Mainstream, general and light professional use | High performance, professional and gaming |
   | Cores and threads | Fewest cores | More cores than i3 | Most cores of the three |
   | Cache | Smallest L3 cache | Medium L3 cache | Largest L3 cache |
   | Turbo Boost | Usually absent or limited | Present | Present, with higher boost clocks |
   | Hyper-Threading | Present on many models | Varies by generation | Generally present |
   | Base clock | Lower | Medium | Higher |
   | Price and power | Lowest | Medium | Highest |
   | Suitable for | Browsing, office work, streaming | Office work, moderate gaming, photo editing | Video editing, 3D rendering, heavy gaming, software development |

   Note: the exact core counts and cache sizes change with every generation, so the comparison should always be made within the same generation. An older i7 may well be slower than a newer i5.

   Why SSD is preferred over HDD:
   - Speed: an SSD reads and writes at 500 MB/s for SATA and 3,000 to 7,000 MB/s for NVMe, whereas a hard disk manages 80 to 160 MB/s. Boot time and application loading are several times faster.
   - Access time: about 0.1 millisecond for an SSD against 5 to 10 milliseconds for an HDD, because there is no seek or rotational delay.
   - No moving parts: an SSD has no spinning platter or moving head, so it is far more resistant to shock, vibration and being dropped.
   - Reliability and noise: no mechanical wear, silent operation, and no risk of a head crash.
   - Power consumption: lower, which gives longer battery life in laptops.
   - Heat and weight: less heat generated, and lighter and thinner packaging.
   - Random access: the decisive advantage. An SSD handles random reads and writes at nearly the same speed as sequential ones, whereas an HDD slows down dramatically, which is exactly the pattern of operating system and database workloads.

   Where HDD is still preferred: bulk storage, archives and backups, because the cost per gigabyte is much lower and very large capacities are available.
10. **8086 microprocessor সম্বলিত একটি ডায়াগ্রাম বা ফিগার হতে ২টি পার্ট এর নাম উল্লেখ কর?** *[BTCL Junior Assistant Manager 2022 compact it 640 (ET: BUET)]*


    Answer: ৮০৮৬ মাইক্রোপ্রসেসরের অভ্যন্তরীণ স্থাপত্য দুইটি প্রধান অংশে বিভক্ত।

    - বাস ইন্টারফেস ইউনিট (Bus Interface Unit, BIU):
      - বাইরের জগতের সঙ্গে যোগাযোগের দায়িত্ব পালন করে, অর্থাৎ মেমোরি ও ইনপুট-আউটপুট যন্ত্র থেকে তথ্য আনা-নেওয়া করে।
      - ভৌত ঠিকানা (physical address) তৈরি করে: সেগমেন্ট রেজিস্টারের মান ১৬ দিয়ে গুণ করে অফসেটের সঙ্গে যোগ করে।
      - এতে থাকে চারটি সেগমেন্ট রেজিস্টার (CS, DS, SS, ES), ইনস্ট্রাকশন পয়েন্টার (IP) এবং ৬ বাইটের ইনস্ট্রাকশন কিউ।
      - ইনস্ট্রাকশন কিউ আগেভাগেই পরবর্তী নির্দেশগুলো এনে রাখে, একে বলে prefetching।

    - এক্সিকিউশন ইউনিট (Execution Unit, EU):
      - কিউ থেকে নির্দেশ নিয়ে বিশ্লেষণ ও সম্পাদন করে।
      - এতে থাকে ALU, কন্ট্রোল ইউনিট, ফ্ল্যাগ রেজিস্টার এবং সাধারণ উদ্দেশ্যের রেজিস্টারসমূহ (AX, BX, CX, DX) ও পয়েন্টার-সূচক রেজিস্টার (SP, BP, SI, DI)।
      - এটি সরাসরি বাসের সঙ্গে যুক্ত নয়; প্রয়োজনীয় তথ্যের জন্য BIU-কে অনুরোধ করে।

    এই বিভাজনের সুবিধা: BIU যখন পরবর্তী নির্দেশ এনে কিউতে রাখছে, EU তখন আগের নির্দেশটি সম্পাদন করতে পারে। এই সমান্তরাল কাজকে বলা হয় পাইপলাইনিং, যা ৮০৮৫ এর তুলনায় ৮০৮৬ এর গতি উল্লেখযোগ্যভাবে বাড়িয়ে দেয়। ৮০৮৫ তে এই বিভাজন ছিল না, ফলে নির্দেশ আনা ও সম্পাদন পর্যায়ক্রমে হতো।
11. **Explain the necessary steps to communicate through a programmable peripheral interfacing device (8255 Microprocessor).** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 672 (ET: N/A)]*


    Answer: The 8255 is a Programmable Peripheral Interface (PPI), a general-purpose input-output chip used with the 8085 and 8086 microprocessors. It provides 24 input-output lines arranged in three 8-bit ports.

    Structure:
    - Port A: 8 lines, can be programmed for input or output in all three modes.
    - Port B: 8 lines, can be programmed for input or output in modes 0 and 1.
    - Port C: 8 lines, divided into an upper half (PC7 to PC4) and a lower half (PC3 to PC0). It can be used for data, or as handshake and status lines for ports A and B.
    - Control register: an 8-bit write-only register that stores the configuration.
    - The chip is selected by CS, and the two lines A1 and A0 choose among Port A, Port B, Port C and the control register.

    Operating modes:
    - Mode 0, simple input-output: ports simply latch output or read input, with no handshaking.
    - Mode 1, strobed input-output: ports A and B transfer data with handshake signals taken from Port C.
    - Mode 2, bidirectional bus: only Port A, which both sends and receives using five lines of Port C for handshaking.
    - BSR mode (Bit Set/Reset): individual bits of Port C are set or reset without disturbing the others.

    Steps to communicate through the 8255:

    Step 1 - Address decoding and connection:
    - Connect the 8255 data lines D0 to D7 to the system data bus.
    - Connect A0 and A1 of the 8255 to the corresponding low address lines, so that the four internal addresses can be distinguished.
    - Generate the CS signal from the higher address lines using a decoder, which fixes the port addresses. For example, with a base address of 80H the addresses become 80H for Port A, 81H for Port B, 82H for Port C and 83H for the control register.
    - Connect RD and WR from the control bus, and RESET.

    Step 2 - Prepare the control word:
    - Bit D7 = 1 selects the input-output mode; D7 = 0 selects the BSR mode.
    - D6 and D5 select the mode for group A (00 = mode 0, 01 = mode 1, 1X = mode 2).
    - D4 sets Port A direction (1 = input, 0 = output).
    - D3 sets the direction of the upper half of Port C.
    - D2 selects the mode for group B (0 = mode 0, 1 = mode 1).
    - D1 sets Port B direction.
    - D0 sets the direction of the lower half of Port C.

    Example: to make Port A output, Port B input and Port C output, all in mode 0, the control word is 1000 0010 in binary, which is 82H.

    Step 3 - Write the control word to the control register:

    ```
    MVI A, 82H      ; control word: Mode 0, Port A out, Port B in, Port C out
    OUT 83H         ; write to the control register address
    ```

    Step 4 - Perform the data transfer:

    ```
    IN  81H         ; read a byte from Port B into the accumulator
    OUT 80H         ; write the accumulator to Port A
    ```

    Step 5 - Use handshaking if mode 1 or 2 is selected:
    - For output, wait for the OBF (output buffer full) and ACK signals.
    - For input, wait for STB (strobe) and IBF (input buffer full).
    - The INTR line of Port C can be used to interrupt the processor when the peripheral is ready, which avoids wasteful polling.

    Step 6 - Use the BSR mode when a single control line must be toggled:

    ```
    MVI A, 0DH      ; D7 = 0 selects BSR, bits select PC6, set to 1
    OUT 83H
    ```

    Typical applications: interfacing a keyboard matrix, a seven-segment display, a printer, stepper motors, relays and analogue-to-digital converters.
12. **What is the function of GPU?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*


    Answer: The function of a GPU (Graphics Processing Unit) is to perform a very large number of identical arithmetic operations in parallel, which makes it the specialised engine for graphics and for any other massively parallel workload.

    Graphics functions:
    - Rendering: converting three-dimensional models into the two-dimensional image shown on the screen.
    - Geometry processing: transforming vertices, applying rotation, scaling and projection.
    - Rasterisation: converting geometric shapes into pixels.
    - Shading and lighting: computing the colour of every pixel from light sources, materials and shadows.
    - Texture mapping: wrapping images onto surfaces.
    - Anti-aliasing: smoothing the jagged edges of diagonal lines.
    - Video decoding and encoding: hardware acceleration of formats such as H.264, HEVC and AV1.
    - Driving multiple displays and managing the frame buffer.

    General-purpose (GPGPU) functions:
    - Deep learning: training and inference of neural networks, which are built almost entirely from matrix multiplications.
    - Scientific computing: weather modelling, molecular dynamics, fluid simulation and finite element analysis.
    - Image and signal processing: filtering, convolution, medical image reconstruction.
    - Cryptography and cryptocurrency mining.
    - Big data analytics and database acceleration.

    Why it is suited to this work: the GPU dedicates most of its chip area to arithmetic units rather than to control logic and cache. It contains thousands of simple cores that all execute the same instruction on different data, which is the SIMD (Single Instruction, Multiple Data) model. It also has very high memory bandwidth, which keeps those cores fed.

    Relationship with the CPU: the CPU runs the operating system and the sequential parts of the program, prepares the data and issues the work; the GPU performs the parallel computation and returns the result. Programming is done with CUDA, OpenCL or higher-level frameworks such as TensorFlow and PyTorch.
13. **Flag Register কী? Intel 8086 Microprocessor-এর Control Flag গুলোর কাজ লিখুন।** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 697 (ET: DPI)]*


    Answer: ফ্ল্যাগ রেজিস্টার (Flag Register) হলো একটি বিশেষ রেজিস্টার, যার প্রতিটি বিট প্রসেসরের সর্বশেষ সম্পাদিত কাজের ফলাফল সম্পর্কে একটি নির্দিষ্ট তথ্য ধারণ করে অথবা প্রসেসরের আচরণ নিয়ন্ত্রণ করে। একে Program Status Word (PSW) ও বলা হয়। এর বিটগুলো দেখেই শর্তসাপেক্ষ জাম্প নির্দেশগুলো সিদ্ধান্ত নেয়।

    Intel 8086 এর ফ্ল্যাগ রেজিস্টার ১৬ বিটের, যার মধ্যে ৯টি বিট ব্যবহৃত হয়: ৬টি স্ট্যাটাস ফ্ল্যাগ এবং ৩টি কন্ট্রোল ফ্ল্যাগ।

    কন্ট্রোল ফ্ল্যাগ তিনটি এবং তাদের কাজ:

    - Trap Flag (TF) — বিট ৮:
      - TF = 1 হলে প্রসেসর একক ধাপ (single step) মোডে চলে, অর্থাৎ প্রতিটি নির্দেশ সম্পাদনের পর টাইপ-১ ইন্টারাপ্ট তৈরি হয়।
      - এর ফলে প্রোগ্রামার প্রতিটি নির্দেশের পর রেজিস্টার ও মেমোরির অবস্থা পরীক্ষা করতে পারেন।
      - প্রধান ব্যবহার: প্রোগ্রাম ডিবাগিং। ডিবাগার এই ফ্ল্যাগ ব্যবহার করেই স্টেপ-বাই-স্টেপ এক্সিকিউশন করায়।
      - TF = 0 হলে প্রসেসর স্বাভাবিক গতিতে চলে।

    - Interrupt Enable Flag (IF) — বিট ৯:
      - এটি মাস্কযোগ্য (maskable) হার্ডওয়্যার ইন্টারাপ্ট, অর্থাৎ INTR পিনের অনুরোধ গ্রহণ করা হবে কিনা তা নিয়ন্ত্রণ করে।
      - IF = 1 হলে প্রসেসর INTR পিনের ইন্টারাপ্ট গ্রহণ করে; IF = 0 হলে উপেক্ষা করে।
      - STI নির্দেশ দিয়ে IF সেট করা হয় এবং CLI নির্দেশ দিয়ে ক্লিয়ার করা হয়।
      - সংকটপূর্ণ কোড অংশ (critical section) চলার সময় CLI দিয়ে ইন্টারাপ্ট বন্ধ রাখা হয়, যাতে কাজটি ব্যাহত না হয়।
      - উল্লেখ্য, NMI (Non-Maskable Interrupt) এই ফ্ল্যাগ দ্বারা নিয়ন্ত্রিত হয় না।

    - Direction Flag (DF) — বিট ১০:
      - স্ট্রিং সংক্রান্ত নির্দেশে (MOVS, CMPS, SCAS, LODS, STOS) সূচক রেজিস্টার SI ও DI কোন দিকে পরিবর্তিত হবে তা নির্ধারণ করে।
      - DF = 0 হলে অটো-ইনক্রিমেন্ট, অর্থাৎ নিম্ন ঠিকানা থেকে উচ্চ ঠিকানার দিকে প্রক্রিয়াকরণ হয় (সামনের দিকে)।
      - DF = 1 হলে অটো-ডিক্রিমেন্ট, অর্থাৎ উচ্চ ঠিকানা থেকে নিম্ন ঠিকানার দিকে (পেছনের দিকে)।
      - CLD নির্দেশ দিয়ে DF ক্লিয়ার এবং STD নির্দেশ দিয়ে সেট করা হয়।
      - ওভারল্যাপিং মেমোরি ব্লক কপি করার সময় সঠিক দিক নির্বাচন জরুরি, নইলে তথ্য নষ্ট হয়।

    তুলনার জন্য ছয়টি স্ট্যাটাস ফ্ল্যাগ: Carry (CF), Parity (PF), Auxiliary Carry (AF), Zero (ZF), Sign (SF) এবং Overflow (OF)। মূল পার্থক্য হলো স্ট্যাটাস ফ্ল্যাগ ফলাফলের বৈশিষ্ট্য জানায়, আর কন্ট্রোল ফ্ল্যাগ প্রসেসরের আচরণ নির্ধারণ করে এবং প্রোগ্রামার সরাসরি সেট বা ক্লিয়ার করতে পারেন।
14. **What is Microprocessor?** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*


    Answer: A microprocessor is a single integrated circuit that contains the entire central processing unit (CPU) of a computer. It fetches instructions from memory, decodes them, executes them and stores the results, and in doing so it controls every other part of the system.

    Key characteristics:
    - It is programmable: the same hardware performs different tasks depending on the program loaded.
    - It is clock-driven: all internal operations are synchronised to a clock signal.
    - It is register-based: it holds working data in a small set of very fast registers.
    - It is digital: it works entirely with binary data.

    Basic components:
    - Arithmetic Logic Unit (ALU): performs arithmetic operations (add, subtract, multiply, divide, increment, decrement) and logic operations (AND, OR, NOT, XOR, shift, rotate, compare).
    - Control Unit (CU): decodes each instruction and generates the timing and control signals that direct every other unit. It manages the fetch-decode-execute cycle and handles interrupts.
    - Register array: small, extremely fast storage inside the CPU, including the accumulator, general-purpose registers, program counter, instruction register, stack pointer, memory address register, memory data register and the flag register.
    - Internal buses: the address bus (unidirectional, carries the memory address), the data bus (bidirectional, carries the data) and the control bus (carries signals such as READ, WRITE, INTERRUPT and CLOCK).
    - Instruction decoder and timing-and-control circuitry.
    - In modern processors, also the cache memory, the memory controller, the branch predictor and often an integrated graphics unit.
15. **Explain four type of register.** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 719 (ET: N/A)]*


    Answer: A register is a small, very fast storage location inside the CPU used to hold data, addresses or control information during processing. Four important types are described below.

    - Accumulator (AC): holds one operand before an arithmetic or logic operation and stores the result afterwards. It is the busiest register in a simple CPU.
     - Program Counter (PC): holds the address of the next instruction to be fetched. It is incremented automatically after each fetch, and it is loaded with a new value on a jump or a call.
     - Instruction Register (IR): holds the instruction that has just been fetched, while the control unit decodes it.
     - Memory Address Register (MAR): holds the address of the memory location that is to be read or written. It is connected to the address bus.
     - Memory Buffer Register (MBR) or Memory Data Register (MDR): holds the data being transferred to or from memory. It is connected to the data bus.
     - General Purpose Registers: used by the programmer to hold intermediate data, for example AX, BX, CX and DX in the 8086.
     - Index and Pointer registers: SI, DI, BP and SP, used in address calculation. SP in particular holds the top of the stack.
     - Status Register or Flag Register (PSW): holds condition flags such as carry, zero, sign, parity and overflow, which record the outcome of the last operation.

     Grouped into four categories:
     - Data registers: hold the operands and results, for example the accumulator and the general-purpose registers.
     - Address registers: hold memory addresses, for example the program counter, the memory address register, the stack pointer and the index registers.
     - Control registers: govern the operation of the processor, for example the instruction register and the control register.
     - Status registers: record the outcome of operations, for example the flag register with its carry, zero, sign, parity and overflow bits.

     Why registers are needed: main memory access takes tens to hundreds of clock cycles, whereas a register is read or written within a single cycle. Keeping the working data in registers is therefore the single most important reason a CPU can run at full speed.
16. **(খ) Typical মাইক্রোকম্পিউটারে কী কী বাস থাকে। একটি মাইক্রোপ্রসেসর এর সাথে RAM, ROM এবং I/O এর কানেকশন বাস এর মাধ্যমে দেখাও।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 777 (ET: N/A)]*


    Answer: একটি সাধারণ মাইক্রোকম্পিউটারে তিন ধরনের বাস থাকে। বাস হলো সমান্তরাল তারের একটি গুচ্ছ, যার মাধ্যমে বিভিন্ন অংশের মধ্যে সংকেত আদান-প্রদান হয়।

    - অ্যাড্রেস বাস (Address Bus): মাইক্রোপ্রসেসর কোন মেমোরি ঘর বা কোন ইনপুট-আউটপুট পোর্টে কাজ করতে চায় তার ঠিকানা বহন করে। এটি একমুখী (unidirectional), কেবল প্রসেসর থেকে বাইরের দিকে যায়। এর প্রস্থই ঠিক করে দেয় সর্বোচ্চ কত মেমোরি সম্বোধন করা যাবে: n বিট প্রস্থে 2^n ঘর। যেমন ৮০৮৬ এর ২০ বিট অ্যাড্রেস বাস দিয়ে 2^20 = ১ মেগাবাইট মেমোরি সম্বোধন করা যায়।

    - ডেটা বাস (Data Bus): প্রকৃত তথ্য বা নির্দেশ বহন করে। এটি দ্বিমুখী (bidirectional), কারণ তথ্য প্রসেসরে আসতেও পারে, প্রসেসর থেকে বেরোতেও পারে। এর প্রস্থ প্রসেসরের শব্দদৈর্ঘ্য নির্দেশ করে; ৮০৮৬ এর ডেটা বাস ১৬ বিট।

    - কন্ট্রোল বাস (Control Bus): নিয়ন্ত্রণ ও সময় সংকেত বহন করে, যেমন MEMR (মেমোরি রিড), MEMW (মেমোরি রাইট), IOR, IOW, ALE, READY, RESET, INTR, INTA ও CLOCK। এটি এককভাবে দ্বিমুখী নয়; কিছু লাইন প্রসেসর থেকে বের হয়, কিছু ভেতরে আসে।

    বাসের মাধ্যমে সংযোগের চিত্র:

    ```mermaid
    flowchart LR
      MP[Microprocessor] --- AB[Address Bus - unidirectional]
      MP --- DB[Data Bus - bidirectional]
      MP --- CB[Control Bus]
      AB --- RAM[RAM]
      AB --- ROM[ROM]
      AB --- IO[I/O Ports]
      DB --- RAM
      DB --- ROM
      DB --- IO
      CB --- RAM
      CB --- ROM
      CB --- IO
    ```

    সংযোগের ব্যাখ্যা:
    - RAM: অ্যাড্রেস বাস থেকে ঠিকানা পায়, ডেটা বাস দিয়ে তথ্য আদান-প্রদান করে এবং কন্ট্রোল বাসের MEMR ও MEMW সংকেত অনুযায়ী পড়া বা লেখার কাজ করে। এটি পঠন ও লিখন উভয়ই সমর্থন করে, তাই ডেটা বাসের সংযোগ দ্বিমুখী।
    - ROM: অ্যাড্রেস ও ডেটা বাসে যুক্ত হলেও কেবল MEMR সংকেতে সাড়া দেয়, কারণ এতে কেবল পড়া যায়। তাই ডেটা বাসের সংযোগ একমুখী, ROM থেকে প্রসেসরের দিকে।
    - I/O পোর্ট: অ্যাড্রেস বাসের নিম্ন কয়েকটি লাইন দিয়ে পোর্ট নম্বর পায় এবং IOR ও IOW সংকেত অনুযায়ী তথ্য আদান-প্রদান করে।
    - অ্যাড্রেস ডিকোডার: অ্যাড্রেস বাসের উচ্চ বিটগুলো বিশ্লেষণ করে ঠিক করে দেয় কোন মুহূর্তে RAM, ROM নাকি I/O চিপটি সক্রিয় (chip select) হবে, যাতে একই সময়ে একাধিক যন্ত্র ডেটা বাস দখল না করে।

    গুরুত্বপূর্ণ নীতি: যেহেতু ডেটা বাস সবার মধ্যে ভাগাভাগি করা, তাই একটি নির্দিষ্ট সময়ে কেবল একটি যন্ত্রই বাসে তথ্য দিতে পারে। বাকিগুলো ত্রি-অবস্থা (tri-state) বাফারের মাধ্যমে উচ্চ ইম্পিড্যান্স অবস্থায় থাকে।
17. **CPU এর অর্থ কি? এর কয়টি অংশ ও কি কি?** *[BPSC Computer Operator 2021 compact it 780 (ET: N/A)]*


    Answer: CPU এর পূর্ণরূপ Central Processing Unit বা কেন্দ্রীয় প্রক্রিয়াকরণ একক। এটি কম্পিউটারের প্রধান অংশ, যেখানে সব হিসাব-নিকাশ ও নিয়ন্ত্রণের কাজ সম্পাদিত হয়। একে কম্পিউটারের মস্তিষ্ক বলা হয়।

    CPU এর অংশ তিনটি:

    - গাণিতিক ও যুক্তি একক (Arithmetic Logic Unit, ALU):
      - যোগ, বিয়োগ, গুণ, ভাগসহ সব গাণিতিক কাজ সম্পন্ন করে।
      - AND, OR, NOT, XOR সহ যৌক্তিক কাজ এবং তুলনার কাজ করে।
      - ফলাফল অনুযায়ী ফ্ল্যাগ বিট সেট করে।

    - নিয়ন্ত্রণ একক (Control Unit, CU):
      - মেমোরি থেকে নির্দেশ আনে এবং তা বিশ্লেষণ (decode) করে।
      - প্রয়োজনীয় নিয়ন্ত্রণ ও সময় সংকেত তৈরি করে কম্পিউটারের সব অংশকে পরিচালনা করে।
      - ইনপুট, আউটপুট, মেমোরি ও ALU এর মধ্যে সমন্বয় সাধন করে।
      - এটি নিজে কোনো হিসাব করে না, কেবল নির্দেশনা দেয়।

    - রেজিস্টার বা স্মৃতি একক (Register set / Memory Unit):
      - অতি দ্রুতগতির অস্থায়ী সংরক্ষণাগার, যেখানে প্রক্রিয়াধীন তথ্য ও ঠিকানা রাখা হয়।
      - প্রধান রেজিস্টারগুলো: অ্যাকিউমুলেটর, প্রোগ্রাম কাউন্টার, ইনস্ট্রাকশন রেজিস্টার, মেমোরি অ্যাড্রেস রেজিস্টার, স্ট্যাক পয়েন্টার ও ফ্ল্যাগ রেজিস্টার।

    চিত্র:

    ```mermaid
    flowchart LR
      IN[Input Unit] --> CPU
      subgraph CPU[Central Processing Unit]
        CU[Control Unit]
        ALU[Arithmetic Logic Unit]
        REG[Registers]
      end
      CPU --> OUT[Output Unit]
      MEM[Main Memory] <--> CPU
    ```

    কার্যচক্র: CPU একটি পুনরাবৃত্ত চক্রে কাজ করে, যাকে বলে fetch-decode-execute-store চক্র। প্রথমে নির্দেশ আনা হয়, তারপর বিশ্লেষণ, তারপর সম্পাদন এবং শেষে ফলাফল সংরক্ষণ। এই চক্র সেকেন্ডে কোটি কোটি বার ঘটে।

    উল্লেখ্য, কিছু বইয়ে স্মৃতি একককে CPU-এর বাইরে ধরে CPU-এর অংশ দুইটি (ALU ও CU) বলা হয়; আবার কিছু বইয়ে রেজিস্টারসহ তিনটি ধরা হয়। উভয় উত্তরই গ্রহণযোগ্য, তবে ব্যাখ্যা দিতে হবে।
18. **Microprocessor কি? এর আবিষ্কারে তথ্য ও যোগাযোগ প্রযুক্তিতে কি ধরনের অগ্রগতি সাধিত হয়েছে ব্যাখ্যা করুন।** *[DMLC Assistant Teacher (ICT) 2021 compact it 827 (ET: N/A)]*


    Answer: মাইক্রোপ্রসেসর হলো একটি সিলিকন চিপে তৈরি সম্পূর্ণ কেন্দ্রীয় প্রক্রিয়াকরণ একক, যা প্রোগ্রামের নির্দেশ অনুযায়ী তথ্য গ্রহণ, প্রক্রিয়াকরণ ও ফলাফল প্রদান করে এবং কম্পিউটারের সব অংশ নিয়ন্ত্রণ করে। এর তিনটি মৌলিক অংশ হলো ALU, কন্ট্রোল ইউনিট ও রেজিস্টার।

    ইতিহাস: বিশ্বের প্রথম মাইক্রোপ্রসেসর ইন্টেল ৪০০৪ বাজারে আসে ১৯৭১ সালে। এটি ছিল ৪ বিটের এবং এতে ছিল প্রায় ২,৩০০টি ট্রানজিস্টর। আজকের একটি প্রসেসরে ট্রানজিস্টর সংখ্যা কয়েক হাজার কোটি।

    তথ্য ও যোগাযোগ প্রযুক্তিতে অগ্রগতি:

    - কম্পিউটারের আকার ও দামের বিপ্লব: মাইক্রোপ্রসেসরের আগে কম্পিউটার ছিল ঘরজোড়া মেইনফ্রেম, যার দাম ছিল লক্ষ লক্ষ ডলার। এক চিপে সম্পূর্ণ সিপিইউ আসায় ব্যক্তিগত কম্পিউটার সম্ভব হলো এবং কম্পিউটার সাধারণ মানুষের নাগালে এলো।
    - ব্যক্তিগত কম্পিউটার বিপ্লব: ১৯৮১ সালে ইন্টেল ৮০৮৮ ভিত্তিক আইবিএম পিসি বাজারে আসার পর অফিস, শিক্ষা ও গৃহে কম্পিউটার ব্যবহারের যুগ শুরু হয়।
    - ইন্টারনেট ও নেটওয়ার্ক: রাউটার, সুইচ, মডেম, সার্ভার ও ডেটা সেন্টার — সবকিছুই মাইক্রোপ্রসেসরনির্ভর। এটি ছাড়া ইন্টারনেটের অস্তিত্বই সম্ভব হতো না।
    - মোবাইল যোগাযোগ: স্মার্টফোনে থাকা ARM ভিত্তিক প্রসেসর আজকের ব্যক্তিগত কম্পিউটারের চেয়েও শক্তিশালী। ফলে ইন্টারনেট, ব্যাংকিং, শিক্ষা ও স্বাস্থ্যসেবা সবার পকেটে পৌঁছে গেছে।
    - এমবেডেড সিস্টেম ও স্বয়ংক্রিয়তা: টেলিভিশন, ওয়াশিং মেশিন, গাড়ি, চিকিৎসা যন্ত্র, শিল্প রোবট ও কৃষি যন্ত্রে মাইক্রোপ্রসেসর ও মাইক্রোকন্ট্রোলার বসেছে।
    - ডিজিটাল যোগাযোগ ব্যবস্থা: ডিজিটাল সিগন্যাল প্রসেসিং, মড্যুলেশন, ত্রুটি সংশোধন ও এনক্রিপশন সবই প্রসেসরের গতি ও সক্ষমতার ওপর নির্ভরশীল।
    - তথ্য সংরক্ষণ ও প্রক্রিয়াকরণ: বড় ডেটাবেজ, ক্লাউড কম্পিউটিং, বিগ ডেটা বিশ্লেষণ ও কৃত্রিম বুদ্ধিমত্তা সম্ভব হয়েছে প্রসেসরের ক্রমবর্ধমান ক্ষমতার কারণে।
    - মুরের সূত্র: প্রতি দুই বছরে চিপে ট্রানজিস্টর সংখ্যা দ্বিগুণ হওয়ার এই প্রবণতা পাঁচ দশক ধরে দাম কমিয়ে এবং ক্ষমতা বাড়িয়ে সমগ্র ডিজিটাল অর্থনীতির ভিত্তি তৈরি করেছে।
    - বাংলাদেশের প্রেক্ষাপট: ডিজিটাল বাংলাদেশ কর্মসূচি, ইউনিয়ন ডিজিটাল সেন্টার, মোবাইল ফিনান্সিয়াল সার্ভিস, ই-জিপি ও অনলাইন সেবা — সবই মাইক্রোপ্রসেসরভিত্তিক অবকাঠামোর ওপর দাঁড়িয়ে আছে।

    সারকথা: মাইক্রোপ্রসেসরের আবিষ্কার কেবল একটি যন্ত্রের উন্নতি নয়, বরং এটি তথ্যপ্রযুক্তি বিপ্লবের সূচনাবিন্দু, যা যোগাযোগ, শিক্ষা, চিকিৎসা, ব্যবসা ও শাসনব্যবস্থার প্রতিটি ক্ষেত্রকে বদলে দিয়েছে।
19. **8-bit microprocessor and 16-bit microprocessor write the data and address widths?** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 864 (ET: BUET)]*


    Answer:

    | Feature | 8-bit Microprocessor | 16-bit Microprocessor |
    |---|---|---|
    | Data bus width | 8 bits, so it transfers one byte at a time | 16 bits, so it transfers two bytes at a time |
    | Address bus width | 16 bits | 20 bits (in the Intel 8086) |
    | Directly addressable memory | 2^16 = 65,536 bytes = 64 KB | 2^20 = 1,048,576 bytes = 1 MB |
    | Word size | 8 bits | 16 bits |
    | Register size | 8 bits (pairs can be combined to make 16 bits) | 16 bits |
    | Typical example | Intel 8085, Zilog Z80, Motorola 6800 | Intel 8086 and 8088, Motorola 68000 |

    Explanation of the two widths:
    - The data bus width tells how many bits the processor can move in a single memory read or write, and therefore how much work one operation accomplishes. An 8-bit processor adding two 16-bit numbers needs two operations; a 16-bit processor needs one.
    - The address bus width determines the size of the memory that can be addressed, since n address lines give 2^n distinct locations.

    Notes on specific chips:
    - The Intel 8085 has an 8-bit data bus and a 16-bit address bus, giving 64 KB of addressable memory. Its address and the lower half of its data bus are multiplexed on the pins AD0 to AD7, and the ALE signal separates them.
    - The Intel 8086 has a 16-bit data bus and a 20-bit address bus, giving 1 MB. It uses segmentation, where a 16-bit segment register is shifted left by four bits and added to a 16-bit offset to form the 20-bit physical address: physical address = (segment x 16) + offset.
    - The Intel 8088 is internally identical to the 8086 but has only an 8-bit external data bus, which made it cheaper; it was used in the original IBM PC.
20. **What is Microprocessor? Explain basic component of Microprocessor.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 868-869 (ET: N/A)]*


    Answer: A microprocessor is a single integrated circuit that contains the entire central processing unit (CPU) of a computer. It fetches instructions from memory, decodes them, executes them and stores the results, and in doing so it controls every other part of the system.

    Key characteristics:
    - It is programmable: the same hardware performs different tasks depending on the program loaded.
    - It is clock-driven: all internal operations are synchronised to a clock signal.
    - It is register-based: it holds working data in a small set of very fast registers.
    - It is digital: it works entirely with binary data.

    Basic components:
    - Arithmetic Logic Unit (ALU): performs arithmetic operations (add, subtract, multiply, divide, increment, decrement) and logic operations (AND, OR, NOT, XOR, shift, rotate, compare).
    - Control Unit (CU): decodes each instruction and generates the timing and control signals that direct every other unit. It manages the fetch-decode-execute cycle and handles interrupts.
    - Register array: small, extremely fast storage inside the CPU, including the accumulator, general-purpose registers, program counter, instruction register, stack pointer, memory address register, memory data register and the flag register.
    - Internal buses: the address bus (unidirectional, carries the memory address), the data bus (bidirectional, carries the data) and the control bus (carries signals such as READ, WRITE, INTERRUPT and CLOCK).
    - Instruction decoder and timing-and-control circuitry.
    - In modern processors, also the cache memory, the memory controller, the branch predictor and often an integrated graphics unit.
21. **Difference between Microprocessor and Microcontroller.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 870 (ET: N/A)]*


    Answer:

    | Point | Microprocessor | Microcontroller |
    |---|---|---|
    | Definition | A single-chip CPU only | A single chip containing CPU, memory and I/O ports |
    | Memory | RAM and ROM must be connected externally | RAM, ROM/Flash and EEPROM are built in |
    | Peripherals | Timers, serial ports, ADC must be added externally | Timers, counters, UART, SPI, I2C, ADC and PWM are on chip |
    | Bus structure | Address, data and control buses are brought out to pins | Buses are internal, so fewer external pins are needed |
    | Cost of a complete system | High, because many support chips are required | Low, because one chip does the whole job |
    | Power consumption | High, generally watts | Very low, milliwatts, with sleep modes |
    | Clock speed | High, GHz range | Low, typically 8 MHz to 200 MHz |
    | Architecture | Usually von Neumann | Usually Harvard, with separate program and data memory |
    | Design purpose | General purpose computing, runs an operating system | Dedicated control of one embedded task |
    | Real-time response | Not deterministic | Deterministic, suited to real-time control |
    | Board size | Large, needs a motherboard | Small, often a single small board |
    | Examples | Intel Core i7, AMD Ryzen, Intel 8086 | Intel 8051, ATmega328 (Arduino), PIC16F877A, ESP32, ARM Cortex-M |
    | Applications | Desktop and laptop computers, servers, smartphones | Washing machines, microwave ovens, digital cameras, ATMs, cars, robots, IoT devices |

    In one sentence: a microprocessor is the brain alone and needs a body of support chips, while a microcontroller is a complete small computer on one chip.
22. **Central Processing Unit (CPU) -এর প্রধান কাজ কী? একটি চিত্রের সাহায্যে CPU-এর বিভিন্ন অংশ বর্ণনা করুন?** *[41th BCS 2021 compact it 884 (ET: N/A)]*


    Answer: কেন্দ্রীয় প্রক্রিয়াকরণ একক বা CPU হলো কম্পিউটারের প্রধান অংশ, যাকে কম্পিউটারের মস্তিষ্ক বলা হয়।

    CPU এর প্রধান কাজ:
    - মেমোরি থেকে নির্দেশ আনা (Fetch)
    - নির্দেশ বিশ্লেষণ করা (Decode)
    - নির্দেশ সম্পাদন করা (Execute)
    - ফলাফল সংরক্ষণ করা (Store)
    - সব গাণিতিক ও যৌক্তিক কাজ সম্পাদন করা
    - কম্পিউটারের সব অংশের কাজ নিয়ন্ত্রণ ও সমন্বয় করা
    - ইনপুট, আউটপুট ও মেমোরির মধ্যে তথ্যপ্রবাহ পরিচালনা করা
    - ইন্টারাপ্ট গ্রহণ ও পরিচালনা করা

    চিত্র:

    ```mermaid
    flowchart LR
      IN[Input Devices] --> CU
      subgraph CPU[Central Processing Unit]
        CU[Control Unit] --> ALU[Arithmetic Logic Unit]
        CU --> REG[Register Set]
        ALU <--> REG
      end
      REG <--> MEM[Main Memory - RAM]
      CU --> OUT[Output Devices]
    ```

    বিভিন্ন অংশের বর্ণনা:

    - নিয়ন্ত্রণ একক (Control Unit):
      - মেমোরি থেকে নির্দেশ আনে এবং ডিকোড করে।
      - সময় ও নিয়ন্ত্রণ সংকেত (READ, WRITE, CLOCK) তৈরি করে সব অংশকে নির্দেশ দেয়।
      - এটি নিজে হিসাব করে না, ট্রাফিক পুলিশের মতো কাজ করে।

    - গাণিতিক ও যুক্তি একক (ALU):
      - যোগ, বিয়োগ, গুণ, ভাগ ইত্যাদি গাণিতিক কাজ করে।
      - AND, OR, NOT, XOR ও তুলনার কাজ করে।
      - শিফট ও রোটেট অপারেশন করে এবং ফ্ল্যাগ সেট করে।

    - রেজিস্টার সেট:
      - অ্যাকিউমুলেটর: হিসাবের অপারেন্ড ও ফলাফল রাখে।
      - প্রোগ্রাম কাউন্টার: পরবর্তী নির্দেশের ঠিকানা রাখে।
      - ইনস্ট্রাকশন রেজিস্টার: বর্তমান নির্দেশ ধরে রাখে।
      - মেমোরি অ্যাড্রেস ও ডেটা রেজিস্টার: মেমোরির সঙ্গে আদান-প্রদানে ব্যবহৃত হয়।
      - স্ট্যাক পয়েন্টার ও ফ্ল্যাগ রেজিস্টার।

    - অভ্যন্তরীণ বাস: তিন ধরনের — অ্যাড্রেস বাস, ডেটা বাস ও কন্ট্রোল বাস, যা CPU এর অংশগুলোর মধ্যে এবং বাইরের যন্ত্রের সঙ্গে সংকেত পরিবহন করে।

    - ক্যাশ মেমোরি: আধুনিক CPU-তে অন্তর্ভুক্ত অতি দ্রুত ছোট স্মৃতি, যা প্রায়শ ব্যবহৃত তথ্য ধরে রেখে প্রধান মেমোরিতে যাওয়ার প্রয়োজন কমায়।

    কার্যচক্র: Fetch → Decode → Execute → Store। এই চক্র সেকেন্ডে কোটি কোটি বার পুনরাবৃত্ত হয়, যা ঘড়ির কম্পাঙ্ক (GHz) দ্বারা নিয়ন্ত্রিত।
23. **When does the parity bit occur in the microprocessors? What does it do?** *[SGFL Assistant General Engineer 2021 compact it 937 (ET: BUET)]*


    Answer: The parity bit in a microprocessor is one of the status flags in the flag register. It is set or cleared automatically by the processor after certain instructions, based on the result produced.

    When it occurs:
    - It is updated after an arithmetic or logical instruction, for example ADD, SUB, AND, OR, XOR, CMP, INC and DEC.
    - It is not updated by instructions that merely move data, such as MOV.
    - It reflects the number of 1 bits in the low-order 8 bits of the result only, even on a 16-bit or 32-bit processor.

    What it does:
    - In the Intel 8085 and 8086 the parity flag follows even parity: PF is set to 1 if the number of 1 bits in the low byte of the result is even, and cleared to 0 if that number is odd.
    - Examples:
      - Result = 0000 0111 (three 1 bits, odd) so PF = 0
      - Result = 0000 0011 (two 1 bits, even) so PF = 1
      - Result = 0000 0000 (zero 1 bits, which is even) so PF = 1
    - The flag can then be tested by conditional jump instructions, JP (jump if parity even) and JPO or JNP (jump if parity odd) in the 8086, or JPE and JPO in the 8085.

    Uses:
    - Error detection in data communication: when a byte is sent over a serial link, a parity bit is appended so that a single-bit error changes the parity and is detected at the receiver. The processor's parity flag makes computing this bit fast.
    - Simple data integrity checks in memory and storage.
    - Testing individual results in low-level arithmetic routines.

    Limitations of parity checking:
    - It detects any odd number of bit errors, but not an even number, since two flipped bits restore the original parity.
    - It can detect an error but cannot correct it. For correction, stronger schemes such as Hamming code, ECC memory, checksums or CRC are used.

    Two conventions:
    - Even parity: the parity bit is chosen so that the total number of 1 bits, including the parity bit, is even.
    - Odd parity: it is chosen so that the total is odd.
24. **১২. 8086 মাইক্রোপ্রসেসর এর Flag Register কত বিটের?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 942 (ET: N/A)]*


    Answer: ৮০৮৬ মাইক্রোপ্রসেসরের ফ্ল্যাগ রেজিস্টার ১৬ বিটের।

    - এই ১৬ বিটের মধ্যে কেবল ৯টি বিট ব্যবহৃত হয়; বাকি ৭টি বিট সংরক্ষিত বা অব্যবহৃত থাকে।
    - ব্যবহৃত ৯টি বিটের মধ্যে ৬টি স্ট্যাটাস ফ্ল্যাগ এবং ৩টি কন্ট্রোল ফ্ল্যাগ।

    স্ট্যাটাস ফ্ল্যাগ (৬টি) — এগুলো সর্বশেষ কাজের ফলাফল নির্দেশ করে:
    - Carry Flag (CF) — বিট ০
    - Parity Flag (PF) — বিট ২
    - Auxiliary Carry Flag (AF) — বিট ৪
    - Zero Flag (ZF) — বিট ৬
    - Sign Flag (SF) — বিট ৭
    - Overflow Flag (OF) — বিট ১১

    কন্ট্রোল ফ্ল্যাগ (৩টি) — এগুলো প্রসেসরের আচরণ নিয়ন্ত্রণ করে:
    - Trap Flag (TF) — বিট ৮, একক ধাপে চালানোর জন্য, ডিবাগিংয়ে ব্যবহৃত
    - Interrupt Enable Flag (IF) — বিট ৯, মাস্কযোগ্য ইন্টারাপ্ট গ্রহণ করা হবে কিনা নিয়ন্ত্রণ করে
    - Direction Flag (DF) — বিট ১০, স্ট্রিং অপারেশনে SI ও DI বাড়বে না কমবে তা নির্ধারণ করে

    তুলনা: ৮০৮৫ মাইক্রোপ্রসেসরের ফ্ল্যাগ রেজিস্টার ৮ বিটের, যার মধ্যে ৫টি ফ্ল্যাগ ব্যবহৃত হয় — Carry, Parity, Auxiliary Carry, Zero ও Sign।
25. **What is Register? Write down the name of 5 CPU Register.** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1018 (ET: N/A)]*


    Answer: A register is a small, high-speed storage location built inside the CPU that temporarily holds data, an address or control information while an instruction is being executed. Registers are the fastest storage in the whole memory hierarchy, faster even than cache, because they sit directly inside the processing unit and are accessed in a single clock cycle.

    Names of five CPU registers and their functions:

    - Accumulator (AC): holds one operand before an arithmetic or logical operation and stores the result afterwards. It is the register most frequently used by the ALU.
    - Program Counter (PC), also called the Instruction Pointer: holds the memory address of the next instruction to be fetched. It is incremented automatically after each fetch, and loaded with a new value on a jump, call or interrupt.
    - Instruction Register (IR): holds the instruction currently being decoded and executed, after it has been fetched from memory.
    - Memory Address Register (MAR): holds the address of the memory location to be read from or written to. It drives the address bus.
    - Memory Buffer Register (MBR), also called the Memory Data Register: holds the data being transferred to or from memory. It connects to the data bus.

    Other important registers:
    - Stack Pointer (SP): points to the top of the stack, used for subroutine calls and interrupts.
    - Flag Register or Program Status Word (PSW): holds the carry, zero, sign, parity and overflow flags.
    - General-purpose registers: for example AX, BX, CX and DX in the 8086.
    - Index registers: SI and DI, used in address calculation and string operations.

    Why registers matter: access to main memory takes tens to hundreds of clock cycles, whereas a register access takes one. Keeping the active working set in registers is therefore essential to CPU performance, and one of the main tasks of a compiler is register allocation, that is deciding which variables live in registers.
26. **(b) What is DMA? Why it is used for high-speed I/O devices?** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1025-1026 (ET: N/A)]*


    Answer: DMA stands for Direct Memory Access. It is a technique by which an input-output device transfers data directly to or from main memory without the data passing through the CPU.

    How it works:
    - A separate hardware unit called the DMA controller (for example the Intel 8237) manages the transfer.
    - Step 1: the CPU programs the DMA controller with the source address, the destination address, the number of bytes and the direction of transfer, and then continues with other work.
    - Step 2: when the peripheral is ready, it asserts a DMA request (DRQ) to the controller.
    - Step 3: the controller asserts HOLD (or BUS REQUEST) to the CPU, asking for control of the buses.
    - Step 4: the CPU finishes its current bus cycle, places its address, data and control lines in the high-impedance state, and replies with HLDA (hold acknowledge).
    - Step 5: the DMA controller now becomes bus master. It places addresses on the bus and generates the read and write signals, moving data directly between the device and memory.
    - Step 6: when the byte count reaches zero the controller releases HOLD, sends an end-of-process signal or an interrupt to the CPU, and the CPU resumes control of the buses.

    Modes of transfer:
    - Burst or block mode: the whole block is transferred in one go, which is fastest but keeps the CPU off the bus the longest.
    - Cycle stealing: one byte is transferred at a time, with the bus returned to the CPU in between, so the CPU is only slightly slowed.
    - Transparent mode: transfers happen only in cycles when the CPU does not need the bus, so the CPU is not slowed at all, but the transfer is slow.

    Why DMA is used for high-speed I/O devices:

    - Speed of transfer: with programmed I/O, every byte must be read into a CPU register and then written out again, which takes several instructions per byte. DMA moves a byte in a single bus cycle, so the transfer rate is limited only by the memory and the device, not by the processor.
    - Frees the CPU: the CPU only sets up the transfer and is then free to execute other programs, which raises overall system throughput. Without DMA, transferring a large file would consume almost all CPU time.
    - Avoids data loss: a fast device such as a disk, a network card or an audio codec produces data continuously. If the CPU is busy servicing another interrupt, bytes would be lost. DMA guarantees that the data is taken as soon as it is ready.
    - Reduces interrupt overhead: instead of one interrupt per byte or per word, there is a single interrupt at the end of the whole block, which saves thousands of context switches.
    - Efficient for large blocks: disk sectors, network packets, video frames and sound buffers are all transferred in blocks, which is exactly what DMA is designed for.

    Typical users of DMA: hard disks and SSDs, network interface cards, sound cards, graphics cards, USB controllers and scanners.
27. **Microcontroller এবং Microprocessor এর মধ্যে Hardware Related পার্থক্য গুলো লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1041 (ET: DPI)]*


    Answer: Microcontroller ও Microprocessor এর মধ্যে হার্ডওয়্যার সংক্রান্ত পার্থক্যসমূহ নিচে দেওয়া হলো।

    | হার্ডওয়্যার বিষয় | Microprocessor | Microcontroller |
    |---|---|---|
    | চিপে অন্তর্ভুক্ত অংশ | কেবল CPU (ALU, কন্ট্রোল ইউনিট, রেজিস্টার) | CPU, RAM, ROM/Flash, EEPROM, টাইমার, I/O পোর্ট সবই একই চিপে |
    | RAM ও ROM | বাইরে থেকে আলাদা চিপ যুক্ত করতে হয় | চিপের ভেতরেই থাকে |
    | মেমোরির পরিমাণ | বাইরে যুক্ত করে গিগাবাইট পর্যন্ত বাড়ানো যায় | সীমিত, সাধারণত কয়েক কিলোবাইট থেকে কয়েকশ কিলোবাইট |
    | পিন সংখ্যা | বেশি, কারণ অ্যাড্রেস ও ডেটা বাস বাইরে আনতে হয় | তুলনামূলক কম, কারণ বাস অভ্যন্তরীণ |
    | বাস | অ্যাড্রেস, ডেটা ও কন্ট্রোল বাস পিনে উন্মুক্ত | বাস চিপের ভেতরেই সীমাবদ্ধ |
    | পেরিফেরাল | টাইমার, সিরিয়াল পোর্ট, ADC, PWM বাইরে যুক্ত করতে হয় | সবই অন-চিপ |
    | সার্কিট বোর্ড | বড়, বহু সাপোর্ট চিপ প্রয়োজন | ছোট, প্রায় একক চিপেই সম্পূর্ণ |
    | স্থাপত্য | সাধারণত ভন নিউম্যান, প্রোগ্রাম ও ডেটা একই মেমোরিতে | সাধারণত হার্ভার্ড, প্রোগ্রাম ও ডেটা মেমোরি আলাদা |
    | ক্লক গতি | উচ্চ, গিগাহার্জ পর্যায়ে | কম, সাধারণত ৮ থেকে ২০০ মেগাহার্জ |
    | বিদ্যুৎ খরচ | বেশি, ওয়াট পর্যায়ে | অত্যন্ত কম, মিলিওয়াট পর্যায়ে; স্লিপ মোড আছে |
    | তাপ ও কুলিং | হিট সিংক ও ফ্যান প্রয়োজন | সাধারণত কিছুই লাগে না |
    | বিট প্রশস্ততা | ৩২ বা ৬৪ বিট | ৮, ১৬ বা ৩২ বিট |
    | খরচ | চিপ ও সম্পূর্ণ ব্যবস্থা উভয়ই ব্যয়বহুল | সস্তা |
    | উদাহরণ | Intel Core i7, Intel 8086, AMD Ryzen | Intel 8051, ATmega328, PIC16F877A, ESP32 |

    সারকথা: হার্ডওয়্যার দৃষ্টিকোণ থেকে মাইক্রোপ্রসেসর একটি অসম্পূর্ণ ব্যবস্থা, যাকে কাজ করাতে হলে আরও বহু চিপ যোগ করতে হয়; আর মাইক্রোকন্ট্রোলার একটি একক চিপেই সম্পূর্ণ কম্পিউটার।

## Memory Hierarchy & Storage (21)

1. Compare RAM, ROM, cache memory, and secondary storage in terms of speed and usage. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*


   Answer: The four form a memory hierarchy, in which speed falls and capacity rises as one moves away from the CPU.

   | Level | Type | Typical size | Access time | Cost per bit | Volatile | Managed by |
   |---|---|---|---|---|---|---|
   | 1 | CPU registers | Bytes to a few hundred bytes | Less than 1 ns | Highest | Yes | Compiler and hardware |
   | 2 | Cache memory (L1, L2, L3) | 32 KB to 64 MB | 1 to 20 ns | Very high | Yes | Hardware |
   | 3 | Main memory (RAM) | 4 GB to 64 GB | 50 to 100 ns | Moderate | Yes | Operating system |
   | 4 | Secondary storage (SSD, HDD) | 256 GB to several TB | 0.1 ms (SSD) to 10 ms (HDD) | Low | No | Operating system and user |
   | 5 | Tertiary or offline storage (tape, optical, cloud) | Very large | Seconds to minutes | Lowest | No | User |

   Governing principle: as one moves down the hierarchy the capacity and the cost advantage increase, while the speed decreases. The design works because of the principle of locality: a program tends to use a small part of its data repeatedly (temporal locality) and to use data stored close together (spatial locality). Keeping that small active part in the fast levels gives almost the speed of the fastest level at almost the cost of the slowest.

   Comparison of the four named types:

   | Point | Cache memory | RAM | ROM | Secondary storage |
   |---|---|---|---|---|
   | Speed | Fastest of the four, 1 to 20 ns | Fast, 50 to 100 ns | Slower than RAM | Slowest, 0.1 ms to 10 ms |
   | Capacity | Smallest, KB to a few MB | GB | KB to a few MB | Largest, GB to TB |
   | Volatility | Volatile | Volatile | Non-volatile | Non-volatile |
   | Cost per bit | Very high | Moderate | Low | Lowest |
   | Technology | SRAM | DRAM | Flash or mask ROM | Magnetic platters or NAND flash |
   | Read and write | Both | Both | Read only in normal use | Both |
   | Usage | Holds the instructions and data the CPU is using right now, to avoid waiting for RAM | Holds the operating system and the programs and data currently running | Holds the BIOS and firmware that start the machine | Permanent storage of all files, programs and the operating system itself |
   | Direct CPU access | Yes | Yes | Yes | No; data must first be copied into RAM |

   How they work together when a program runs: the program file is stored on secondary storage; when it is launched, the operating system loads it into RAM; the CPU then fetches instructions from RAM, and the cache automatically keeps copies of the most recently and most frequently used of those instructions and data so that the CPU rarely has to wait. ROM meanwhile holds the code that made this whole sequence possible by starting the machine.
2. **Difference between SRAM & DRAM also write Differences Cache Memory vs Flash Memory.** *[BUET Assistant Programmer 21.06.2025 compact it 1434 (ET: BUET)]*


   Answer:

   Difference between SRAM and DRAM:

   | Point | SRAM (Static RAM) | DRAM (Dynamic RAM) |
   |---|---|---|
   | Storage element | A flip-flop made of 6 transistors per bit | One transistor and one capacitor per bit |
   | Refreshing | Not required; data holds as long as power is on | Required every few milliseconds, because the capacitor leaks |
   | Speed | Very fast, access time 1 to 10 ns | Slower, access time 50 to 70 ns |
   | Density | Low, fewer bits per unit area | High, many more bits per unit area |
   | Cost per bit | High | Low |
   | Power consumption | Higher in the idle state, lower when active | Lower in the idle state, but refresh circuitry consumes power |
   | Complexity of circuit | Complex | Simple |
   | Capacity | Small, kilobytes to a few megabytes | Large, gigabytes |
   | Typical use | Cache memory (L1, L2, L3), registers, buffers | Main memory of computers, graphics memory |
   | Volatility | Volatile | Volatile |

   Summary: SRAM is fast but expensive, so it is used in small quantities close to the CPU; DRAM is cheap and dense, so it is used for the large main memory.

   Difference between cache memory and flash memory:

   | Point | Cache Memory | Flash Memory |
   |---|---|---|
   | Technology | SRAM, built from flip-flops | Floating-gate transistors (NAND or NOR) |
   | Volatility | Volatile; contents are lost when power goes off | Non-volatile; contents survive without power |
   | Location | Inside or very close to the CPU | On a storage device such as an SSD, pen drive or memory card |
   | Speed | Extremely fast, 1 to 20 ns | Much slower, tens of microseconds |
   | Capacity | Very small, KB to a few MB | Large, GB to TB |
   | Cost per bit | Very high | Low |
   | Purpose | To hold data the CPU is about to reuse, bridging the speed gap between CPU and RAM | To store files and programs permanently |
   | Write endurance | Effectively unlimited | Limited; each cell tolerates a few thousand to a hundred thousand write cycles, so wear levelling is needed |
   | Erase before write | Not needed | Needed; flash must be erased in whole blocks before rewriting |
   | Managed by | Hardware, automatically and invisibly | The operating system through a file system and a flash controller |
   | Examples | L1, L2 and L3 cache in a processor | SSD, USB pen drive, SD card, BIOS chip |

   In short: cache is small, volatile and extremely fast, and exists to make the CPU wait less; flash is large, non-volatile and comparatively slow, and exists to keep data permanently.
3. **DRAM stands for __________?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*


   Answer: DRAM stands for Dynamic Random Access Memory.

   - Each bit is stored as a charge on a tiny capacitor, with one transistor acting as a switch, so only two components are needed per bit.
   - The capacitor leaks its charge within a few milliseconds, so the contents must be read and rewritten periodically. This is called refreshing, and it is why the memory is called "dynamic".
   - Because it uses so few components per bit, DRAM is dense and cheap, which makes it the standard technology for the main memory of a computer.
   - It is volatile: all contents are lost when the power is switched off.
   - Common forms: SDRAM, DDR, DDR2, DDR3, DDR4 and DDR5, where DDR stands for Double Data Rate, meaning data is transferred on both the rising and the falling edge of the clock.
   - It is contrasted with SRAM (Static Random Access Memory), which needs no refreshing but uses six transistors per bit and is therefore fast, expensive and used only for cache.
4. **What is stand for EEPROM?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*


   Answer: EEPROM stands for Electrically Erasable Programmable Read Only Memory.

   - It is a type of non-volatile memory that can be erased and reprogrammed electrically, byte by byte, while it remains in the circuit.
   - It retains its contents without power, typically for 10 to 100 years.
   - Endurance is limited, usually 10,000 to 1,000,000 erase and write cycles per cell.
   - It is slow to write compared with RAM, but reading is fast.

   The ROM family, in order of development:
   - ROM (Mask ROM): programmed during manufacture and can never be changed.
   - PROM (Programmable ROM): can be written once by the user with a special programmer, then never changed.
   - EPROM (Erasable PROM): erased by exposing the chip through a quartz window to ultraviolet light for about 20 minutes, and erasure affects the whole chip. It must be removed from the circuit to be erased.
   - EEPROM: erased and rewritten electrically, one byte at a time, without removing it from the circuit.
   - Flash memory: a form of EEPROM that erases in blocks rather than bytes, which makes it much faster and cheaper for large capacities. It is the technology of SSDs, pen drives and memory cards.

   Typical uses of EEPROM: storing the BIOS settings, calibration constants in instruments, configuration data in microcontrollers, and the data in smart cards.
5. **কম্পিউটার স্মৃতি বলতে কী বোঝায়? কম্পিউটারের স্মৃতির শ্রেণিবিভাগ আলোচনা করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 405 (ET: N/A)]*


   Answer: কম্পিউটার স্মৃতি বা মেমোরি বলতে সেই সব যন্ত্রাংশকে বোঝায়, যেখানে কম্পিউটার তথ্য, নির্দেশ ও ফলাফল সাময়িক বা স্থায়ীভাবে সংরক্ষণ করে রাখে এবং প্রয়োজনে পুনরুদ্ধার করে। প্রক্রিয়াকরণের আগে ও পরে সব তথ্যই মেমোরিতে থাকতে হয়, তাই মেমোরি ছাড়া কম্পিউটার কাজ করতে পারে না।

   পরিমাপের একক: বিট, বাইট (৮ বিট), কিলোবাইট, মেগাবাইট, গিগাবাইট, টেরাবাইট, পেটাবাইট।

   কম্পিউটার স্মৃতির শ্রেণিবিভাগ:

   ক. প্রধান বা প্রাথমিক স্মৃতি (Primary / Main Memory):
   - সিপিইউ সরাসরি এই স্মৃতিতে প্রবেশ করতে পারে।
   - RAM (Random Access Memory): অস্থায়ী ও অস্থিতিশীল (volatile)। চলমান প্রোগ্রাম ও তথ্য এখানে থাকে। দুই প্রকার:
     - SRAM: ফ্লিপ-ফ্লপ দিয়ে তৈরি, দ্রুত, ব্যয়বহুল, রিফ্রেশ লাগে না, ক্যাশে ব্যবহৃত।
     - DRAM: ক্যাপাসিটর দিয়ে তৈরি, সস্তা, ঘন, রিফ্রেশ প্রয়োজন, প্রধান মেমোরিতে ব্যবহৃত।
   - ROM (Read Only Memory): স্থায়ী ও স্থিতিশীল (non-volatile)। BIOS ও ফার্মওয়্যার এখানে থাকে। প্রকারভেদ: PROM, EPROM, EEPROM, Flash।

   খ. ক্যাশে স্মৃতি (Cache Memory):
   - সিপিইউ ও প্রধান স্মৃতির মধ্যবর্তী অতি দ্রুতগতির ছোট স্মৃতি।
   - স্তরভেদ: L1 (সবচেয়ে ছোট ও দ্রুত, প্রতিটি কোরে আলাদা), L2, L3 (সবচেয়ে বড়, সব কোরের মধ্যে ভাগাভাগি)।
   - উদ্দেশ্য: সিপিইউ ও RAM এর গতির ব্যবধান কমানো।

   গ. রেজিস্টার:
   - সিপিইউ-এর ভেতরের সবচেয়ে দ্রুত ও ক্ষুদ্রতম স্মৃতি। প্রক্রিয়াধীন তথ্য ও ঠিকানা রাখে।

   ঘ. সহায়ক বা মাধ্যমিক স্মৃতি (Secondary Storage):
   - স্থায়ী সংরক্ষণের জন্য ব্যবহৃত, সিপিইউ সরাসরি প্রবেশ করতে পারে না; আগে RAM এ আনতে হয়।
   - চৌম্বকীয়: হার্ড ডিস্ক, ম্যাগনেটিক টেপ, ফ্লপি ডিস্ক।
   - অপটিক্যাল: সিডি, ডিভিডি, ব্লু-রে।
   - সেমিকন্ডাক্টর ভিত্তিক: SSD, পেন ড্রাইভ, মেমোরি কার্ড।

   ঙ. তৃতীয় পর্যায়ের ও অফলাইন স্মৃতি (Tertiary / Offline):
   - ম্যাগনেটিক টেপ লাইব্রেরি ও ক্লাউড স্টোরেজ, যা মূলত সংরক্ষণাগার (archive) ও ব্যাকআপের জন্য।

   স্মৃতির স্তরবিন্যাস (Memory Hierarchy):

   রেজিস্টার → ক্যাশে → RAM → SSD/HDD → টেপ ও ক্লাউড

   উপরের দিকে গতি বেশি, ধারণক্ষমতা কম ও দাম বেশি; নিচের দিকে ঠিক উল্টো।

   অন্য দৃষ্টিকোণ থেকে শ্রেণিবিভাগ:
   - অস্থিতিশীলতা অনুযায়ী: Volatile (RAM, ক্যাশে, রেজিস্টার) ও Non-volatile (ROM, HDD, SSD)।
   - প্রবেশ পদ্ধতি অনুযায়ী: Random access (RAM, SSD), Sequential access (ম্যাগনেটিক টেপ), Direct access (হার্ড ডিস্ক)।
   - প্রযুক্তি অনুযায়ী: সেমিকন্ডাক্টর, চৌম্বকীয় ও অপটিক্যাল।
6. **Write down the difference between RAM and ROM.** *[DESCO Sub-Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)], [DMLC Assistant Teacher (ICT) 2021 compact it 826 (ET: N/A)]*


   Answer:

   | Point | RAM (Random Access Memory) | ROM (Read Only Memory) |
   |---|---|---|
   | Full form | Random Access Memory | Read Only Memory |
   | Volatility | Volatile; contents are lost when power is switched off | Non-volatile; contents are retained without power |
   | Read and write | Both reading and writing are possible | Normally only reading; writing needs a special process |
   | Purpose | Working memory that holds the operating system, running programs and their data | Permanent storage of firmware such as BIOS and the bootstrap loader |
   | Speed | Fast | Slower than RAM |
   | Capacity | Large, gigabytes | Small, kilobytes to a few megabytes |
   | Cost per bit | Higher | Lower |
   | Modification by user | Contents change constantly during use | Contents are fixed by the manufacturer or programmed once |
   | Types | SRAM, DRAM (SDRAM, DDR, DDR2, DDR3, DDR4, DDR5) | PROM, EPROM, EEPROM, Flash, Mask ROM |
   | Physical form | Removable modules such as DIMM and SO-DIMM | Soldered chip on the motherboard |
   | Example of use | Running a browser or a word processor | Holding the BIOS that starts the computer |

   Key idea: RAM is the desk on which you work, cleared at the end of the day; ROM is the printed instruction manual that stays on the shelf permanently.
7. **Differentiate among CPU register, Cache memory, Main memory and Secondary memory.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 510 (ET: MIST)]*


   Answer:

   | Level | Type | Typical size | Access time | Cost per bit | Volatile | Managed by |
   |---|---|---|---|---|---|---|
   | 1 | CPU registers | Bytes to a few hundred bytes | Less than 1 ns | Highest | Yes | Compiler and hardware |
   | 2 | Cache memory (L1, L2, L3) | 32 KB to 64 MB | 1 to 20 ns | Very high | Yes | Hardware |
   | 3 | Main memory (RAM) | 4 GB to 64 GB | 50 to 100 ns | Moderate | Yes | Operating system |
   | 4 | Secondary storage (SSD, HDD) | 256 GB to several TB | 0.1 ms (SSD) to 10 ms (HDD) | Low | No | Operating system and user |
   | 5 | Tertiary or offline storage (tape, optical, cloud) | Very large | Seconds to minutes | Lowest | No | User |

   Governing principle: as one moves down the hierarchy the capacity and the cost advantage increase, while the speed decreases. The design works because of the principle of locality: a program tends to use a small part of its data repeatedly (temporal locality) and to use data stored close together (spatial locality). Keeping that small active part in the fast levels gives almost the speed of the fastest level at almost the cost of the slowest.

   Detailed comparison of the four:

   | Point | CPU Register | Cache Memory | Main Memory (RAM) | Secondary Memory |
   |---|---|---|---|---|
   | Location | Inside the CPU, part of the ALU and control path | Inside or beside the CPU chip | On the motherboard as removable modules | External device connected by SATA, NVMe or USB |
   | Technology | Flip-flops | SRAM | DRAM | Magnetic platters or NAND flash |
   | Size | A few bytes to a few hundred bytes | 32 KB to 64 MB | 4 GB to 64 GB | 256 GB to several TB |
   | Access time | Under 1 ns | 1 to 20 ns | 50 to 100 ns | 0.1 ms for SSD, 5 to 10 ms for HDD |
   | Cost per bit | Highest | Very high | Moderate | Lowest |
   | Volatility | Volatile | Volatile | Volatile | Non-volatile |
   | Accessed by CPU | Directly, in the same cycle | Directly | Directly | Not directly; contents must be copied into RAM first |
   | Managed by | The compiler and the instruction set | Hardware, automatically | The operating system's memory manager | The operating system's file system |
   | Purpose | Hold the operands and results of the instruction being executed | Hold recently and frequently used data to avoid waiting for RAM | Hold the running programs and their data | Store all files and programs permanently |

   Note on speed ratios: if a register access is taken as one second on a human scale, a cache access is about ten seconds, a RAM access about two minutes, an SSD access about two days and a hard disk access about three months. This is why the hierarchy exists at all.
8. **What do you mean by memory organization? Write the different between SRAM and DRAM.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 558 (ET: BIBM)]*


   Answer: Memory organization means the way in which the different types of memory in a computer are arranged, connected and managed so that the processor gets the data it needs as quickly and as cheaply as possible.

   What it covers:
   - The memory hierarchy: registers, cache, main memory and secondary storage arranged by speed and cost.
   - Address space: how physical addresses are assigned to memory locations, and how the address bus width limits the total addressable memory (n address lines give 2^n locations).
   - Memory interleaving: dividing memory into banks that can be accessed in parallel, so that consecutive addresses lie in different banks and several reads can overlap.
   - Memory mapping: how logical addresses used by a program are translated into physical addresses, using paging or segmentation.
   - Virtual memory: using part of the disk as an extension of RAM, so a program larger than physical memory can run.
   - Cache organization: direct-mapped, fully associative or set-associative placement, and the replacement and write policies used.
   - Memory management by the operating system: allocation, deallocation, protection between processes and swapping.
   - Physical arrangement: modules such as SIMM and DIMM, channels (single, dual, quad) and error correction (ECC).

   Aim of memory organization: to obtain the speed of the fastest memory at close to the cost of the cheapest. This is possible because of the principle of locality, both temporal (recently used data is likely to be used again) and spatial (data near recently used data is likely to be needed next).

   Difference between SRAM and DRAM:

   | Point | SRAM (Static RAM) | DRAM (Dynamic RAM) |
   |---|---|---|
   | Storage element | A flip-flop made of 6 transistors per bit | One transistor and one capacitor per bit |
   | Refreshing | Not required; data holds as long as power is on | Required every few milliseconds, because the capacitor leaks |
   | Speed | Very fast, access time 1 to 10 ns | Slower, access time 50 to 70 ns |
   | Density | Low, fewer bits per unit area | High, many more bits per unit area |
   | Cost per bit | High | Low |
   | Power consumption | Higher in the idle state, lower when active | Lower in the idle state, but refresh circuitry consumes power |
   | Complexity of circuit | Complex | Simple |
   | Capacity | Small, kilobytes to a few megabytes | Large, gigabytes |
   | Typical use | Cache memory (L1, L2, L3), registers, buffers | Main memory of computers, graphics memory |
   | Volatility | Volatile | Volatile |

   Summary: SRAM is fast but expensive, so it is used in small quantities close to the CPU; DRAM is cheap and dense, so it is used for the large main memory.
9. **What is dual channel RAM? Difference between single In-Line and Dual In-Line Memory Module.** *[BITAC Assistant Programmer 27.10.2023 compact it 559 (ET: BUTEX)]*


   Answer: Dual channel RAM is a memory architecture in which the memory controller uses two independent 64-bit channels to communicate with the memory modules at the same time, giving an effective 128-bit path instead of 64 bits.

   How it works:
   - Memory modules are installed in matched pairs, in the correctly coloured slots specified by the motherboard manual, for example slots 1 and 3 or 2 and 4.
   - The controller splits the data across the two channels, so while one module is being accessed the other can also be accessed.
   - The theoretical bandwidth is therefore doubled, though the practical gain is usually 5 to 30 per cent depending on the workload. Integrated graphics, which share system memory, benefit the most.
   - The modules should be identical in capacity, speed and timings for the mode to work properly.
   - Single channel uses one 64-bit path; triple and quad channel extend the same idea to three and four paths.

   Difference between SIMM and DIMM:

   | Point | SIMM (Single In-line Memory Module) | DIMM (Dual In-line Memory Module) |
   |---|---|---|
   | Contacts | The pins on the two sides of the board are electrically connected, so both sides carry the same signal | The pins on the two sides are independent, so each side carries different signals |
   | Data path width | 32 bits (later 72-pin versions) | 64 bits |
   | Pin count | 30 pins or 72 pins | 168, 184, 240, 288 pins depending on generation |
   | Installation | Had to be installed in matched pairs on 64-bit processors, since two 32-bit modules were needed to fill the bus | Can be installed singly, since one module already provides 64 bits |
   | Voltage | 5 volts | 3.3 volts and lower in later generations |
   | Memory type | FPM and EDO DRAM | SDRAM, DDR, DDR2, DDR3, DDR4, DDR5 |
   | Era | 1980s and early 1990s | Mid 1990s to the present |
   | Notch | One notch | Different notch positions, which prevent a module being fitted into the wrong generation of slot |

   Variants of DIMM: SO-DIMM for laptops, which is physically shorter; RDIMM (registered) and LRDIMM (load reduced) for servers, which add a buffer to support very large capacities; and ECC DIMM, which adds parity chips for error correction.
10. **What is the difference between Dynamic RAM and Static RAM?** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 642 (ET: BUET)]*


    Answer:

    | Point | SRAM (Static RAM) | DRAM (Dynamic RAM) |
    |---|---|---|
    | Storage element | A flip-flop made of 6 transistors per bit | One transistor and one capacitor per bit |
    | Refreshing | Not required; data holds as long as power is on | Required every few milliseconds, because the capacitor leaks |
    | Speed | Very fast, access time 1 to 10 ns | Slower, access time 50 to 70 ns |
    | Density | Low, fewer bits per unit area | High, many more bits per unit area |
    | Cost per bit | High | Low |
    | Power consumption | Higher in the idle state, lower when active | Lower in the idle state, but refresh circuitry consumes power |
    | Complexity of circuit | Complex | Simple |
    | Capacity | Small, kilobytes to a few megabytes | Large, gigabytes |
    | Typical use | Cache memory (L1, L2, L3), registers, buffers | Main memory of computers, graphics memory |
    | Volatility | Volatile | Volatile |

    Summary: SRAM is fast but expensive, so it is used in small quantities close to the CPU; DRAM is cheap and dense, so it is used for the large main memory.
11. **Give classification of memory. Differentiate between RAM and ROM.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 664 (ET: N/A)]*


    Answer: Classification of memory:

    By position in the hierarchy:
    - CPU registers: inside the processor, fastest and smallest.
    - Cache memory: L1, L2 and L3, made of SRAM, sits between the CPU and main memory.
    - Primary or main memory: RAM and ROM, directly accessible by the CPU.
    - Secondary storage: hard disk, SSD, optical disc, pen drive; not directly accessible by the CPU.
    - Tertiary and offline storage: magnetic tape, cloud storage, used for archives and backup.

    By volatility:
    - Volatile: contents lost when power is removed. Registers, cache, RAM.
    - Non-volatile: contents retained without power. ROM, flash, HDD, SSD, optical media.

    By technology:
    - Semiconductor: RAM, ROM, cache, SSD, pen drive.
    - Magnetic: hard disk, floppy disk, magnetic tape.
    - Optical: CD, DVD, Blu-ray.

    By access method:
    - Random access: any location reachable in the same time, as in RAM and SSD.
    - Sequential access: data must be read in order, as on magnetic tape.
    - Direct or semi-random access: a track is located directly, then read sequentially, as on a hard disk.

    By read and write capability:
    - Read-write memory: RAM, hard disk, SSD.
    - Read-only memory: ROM, CD-ROM.
    - Write once, read many: PROM, CD-R.

    Difference between RAM and ROM:

    | Point | RAM (Random Access Memory) | ROM (Read Only Memory) |
    |---|---|---|
    | Full form | Random Access Memory | Read Only Memory |
    | Volatility | Volatile; contents are lost when power is switched off | Non-volatile; contents are retained without power |
    | Read and write | Both reading and writing are possible | Normally only reading; writing needs a special process |
    | Purpose | Working memory that holds the operating system, running programs and their data | Permanent storage of firmware such as BIOS and the bootstrap loader |
    | Speed | Fast | Slower than RAM |
    | Capacity | Large, gigabytes | Small, kilobytes to a few megabytes |
    | Cost per bit | Higher | Lower |
    | Modification by user | Contents change constantly during use | Contents are fixed by the manufacturer or programmed once |
    | Types | SRAM, DRAM (SDRAM, DDR, DDR2, DDR3, DDR4, DDR5) | PROM, EPROM, EEPROM, Flash, Mask ROM |
    | Physical form | Removable modules such as DIMM and SO-DIMM | Soldered chip on the motherboard |
    | Example of use | Running a browser or a word processor | Holding the BIOS that starts the computer |

    Key idea: RAM is the desk on which you work, cleared at the end of the day; ROM is the printed instruction manual that stays on the shelf permanently.
12. **(গ) Primary Memory and Secondary Memory এর উদাহরণসহ তুলনামূলক আলোচনা করুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 705 (ET: N/A)]*


    Answer:

    | বিষয় | প্রাথমিক স্মৃতি (Primary Memory) | সহায়ক স্মৃতি (Secondary Memory) |
    |---|---|---|
    | সংজ্ঞা | সিপিইউ সরাসরি যে স্মৃতিতে প্রবেশ করতে পারে | স্থায়ী সংরক্ষণের জন্য ব্যবহৃত স্মৃতি, যাতে সিপিইউ সরাসরি প্রবেশ করতে পারে না |
    | অবস্থান | মাদারবোর্ডে সিপিইউ-এর কাছাকাছি | আলাদা যন্ত্র হিসেবে, তার বা পোর্টের মাধ্যমে যুক্ত |
    | গতি | দ্রুত (৫০-১০০ ন্যানোসেকেন্ড) | ধীর (SSD-তে ০.১ মিলিসেকেন্ড, HDD-তে ৫-১০ মিলিসেকেন্ড) |
    | ধারণক্ষমতা | কম, সাধারণত ৪ থেকে ৬৪ গিগাবাইট | অনেক বেশি, শত গিগাবাইট থেকে টেরাবাইট |
    | অস্থিতিশীলতা | RAM অস্থিতিশীল (volatile), বিদ্যুৎ গেলে তথ্য মুছে যায়; ROM স্থিতিশীল | স্থিতিশীল (non-volatile), বিদ্যুৎ ছাড়াও তথ্য থাকে |
    | দাম (প্রতি বাইট) | বেশি | কম |
    | প্রকৃতি | সেমিকন্ডাক্টর ভিত্তিক | চৌম্বকীয়, অপটিক্যাল বা ফ্ল্যাশ ভিত্তিক |
    | কাজ | চলমান প্রোগ্রাম ও তথ্য ধারণ করা | ফাইল, প্রোগ্রাম ও অপারেটিং সিস্টেম স্থায়ীভাবে সংরক্ষণ করা |
    | বহনযোগ্যতা | সাধারণত বহনযোগ্য নয় | পেন ড্রাইভ ও এক্সটার্নাল ড্রাইভ সহজে বহনযোগ্য |
    | উদাহরণ | RAM, ROM, ক্যাশে মেমোরি, রেজিস্টার | হার্ড ডিস্ক, SSD, পেন ড্রাইভ, সিডি, ডিভিডি, মেমোরি কার্ড, ম্যাগনেটিক টেপ |

    সম্পর্ক: হার্ড ডিস্কে সংরক্ষিত একটি প্রোগ্রাম চালু করলে অপারেটিং সিস্টেম সেটিকে প্রথমে RAM এ নিয়ে আসে; তারপরই সিপিইউ তার নির্দেশ পড়তে পারে। কাজ শেষে ফলাফল আবার সহায়ক স্মৃতিতে সংরক্ষণ করা হয়। অর্থাৎ দুই ধরনের স্মৃতিই পরস্পরের পরিপূরক।
13. **Write down the difference between SRAM and DRAM.** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 718 (ET: N/A)]*


    Answer:

    | Point | SRAM (Static RAM) | DRAM (Dynamic RAM) |
    |---|---|---|
    | Storage element | A flip-flop made of 6 transistors per bit | One transistor and one capacitor per bit |
    | Refreshing | Not required; data holds as long as power is on | Required every few milliseconds, because the capacitor leaks |
    | Speed | Very fast, access time 1 to 10 ns | Slower, access time 50 to 70 ns |
    | Density | Low, fewer bits per unit area | High, many more bits per unit area |
    | Cost per bit | High | Low |
    | Power consumption | Higher in the idle state, lower when active | Lower in the idle state, but refresh circuitry consumes power |
    | Complexity of circuit | Complex | Simple |
    | Capacity | Small, kilobytes to a few megabytes | Large, gigabytes |
    | Typical use | Cache memory (L1, L2, L3), registers, buffers | Main memory of computers, graphics memory |
    | Volatility | Volatile | Volatile |

    Summary: SRAM is fast but expensive, so it is used in small quantities close to the CPU; DRAM is cheap and dense, so it is used for the large main memory.
14. **(ক) Data transfer rate এর ভিত্তিতে নিম্নোক্ত memory/storage device গুলোকে বেশী থেকে কম ক্রমানুসারে সাজান। (i) Flash drive (ii) SSD (iii) Cache memory (iv) DVD (v) RAM (vi) Magnetic HD** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 767 (ET: N/A)]*


    Answer: Data transfer rate অনুযায়ী বেশি থেকে কম ক্রমানুসারে সাজানো হলো:

    - ১. Cache memory — সবচেয়ে দ্রুত। SRAM প্রযুক্তিতে তৈরি এবং সিপিইউ-এর ভেতরেই থাকে; স্থানান্তর হার সেকেন্ডে কয়েকশ গিগাবাইট থেকে টেরাবাইট পর্যায়ে।
    - ২. RAM — প্রধান স্মৃতি, DDR4 বা DDR5 প্রযুক্তিতে সেকেন্ডে প্রায় ২৫ থেকে ৬০ গিগাবাইট।
    - ৩. SSD — NVMe হলে সেকেন্ডে ৩,০০০ থেকে ৭,০০০ মেগাবাইট, SATA হলে প্রায় ৫৫০ মেগাবাইট।
    - ৪. Magnetic Hard Disk — সেকেন্ডে প্রায় ৮০ থেকে ১৬০ মেগাবাইট।
    - ৫. Flash drive (পেন ড্রাইভ) — USB 3.0 হলে সেকেন্ডে ৩০ থেকে ১০০ মেগাবাইট, USB 2.0 হলে আরও কম।
    - ৬. DVD — সবচেয়ে ধীর, ১x গতিতে সেকেন্ডে প্রায় ১.৩৫ মেগাবাইট এবং ১৬x গতিতেও প্রায় ২১ মেগাবাইট।

    চূড়ান্ত ক্রম: Cache memory > RAM > SSD > Magnetic Hard Disk > Flash drive > DVD

    কারণ ব্যাখ্যা: ক্যাশে ও RAM সেমিকন্ডাক্টর ভিত্তিক এবং সিপিইউ-এর সঙ্গে সরাসরি উচ্চগতির বাসে যুক্ত। SSD ও ফ্ল্যাশ ড্রাইভও সেমিকন্ডাক্টর ভিত্তিক, তবে বাইরের ইন্টারফেসের (NVMe, SATA, USB) সীমাবদ্ধতায় ধীর। হার্ড ডিস্ক ও ডিভিডিতে যান্ত্রিক ঘূর্ণন ও মাথা সরানোর প্রয়োজন হয়, তাই এগুলো সবচেয়ে ধীর।
15. **Which of the following is non volatile memory? (a) SRAM (b) DRAM (c) ROM (d) HDD** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*


    Answer: (c) ROM এবং (d) HDD — উভয়ই অস্থায়ীহীন বা non-volatile memory।

    ব্যাখ্যা:
    - Non-volatile memory হলো সেই স্মৃতি, যা বিদ্যুৎ সরবরাহ বন্ধ হয়ে গেলেও তথ্য ধরে রাখে।
    - (a) SRAM: volatile। ফ্লিপ-ফ্লপ দিয়ে তৈরি; বিদ্যুৎ গেলে তথ্য মুছে যায়। ক্যাশে মেমোরিতে ব্যবহৃত।
    - (b) DRAM: volatile। ক্যাপাসিটরে চার্জ আকারে তথ্য রাখে, যা প্রতি কয়েক মিলিসেকেন্ডে রিফ্রেশ করতে হয়; বিদ্যুৎ গেলে সব মুছে যায়। প্রধান মেমোরিতে ব্যবহৃত।
    - (c) ROM: non-volatile। BIOS ও ফার্মওয়্যার স্থায়ীভাবে ধরে রাখে।
    - (d) HDD: non-volatile। চৌম্বকীয় প্লেটে তথ্য সংরক্ষিত থাকে, যা বিদ্যুৎ ছাড়াও বহু বছর টিকে থাকে।

    যদি প্রশ্নে একটিমাত্র উত্তর চাওয়া হয়, তবে স্মৃতি (memory) শব্দটির প্রচলিত অর্থে সঠিক উত্তর (c) ROM, কারণ HDD-কে সাধারণত মেমোরি নয়, স্টোরেজ ডিভাইস হিসেবে শ্রেণিবদ্ধ করা হয়।

    অন্যান্য non-volatile উদাহরণ: PROM, EPROM, EEPROM, ফ্ল্যাশ মেমোরি, SSD, পেন ড্রাইভ, মেমোরি কার্ড, সিডি ও ডিভিডি।
16. **(b) Here are given 4 types of different memory. Which memory is the faster? Write in sequence order in the following figure: Register, Hard disk, Cache, RAM.** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 821 (ET: BUET)]*


    Answer: Speed order, from fastest to slowest:

    Register > Cache > RAM > Hard disk

    | Position | Memory | Typical access time | Typical size | Volatile |
    |---|---|---|---|---|
    | 1 (fastest) | Register | Less than 1 ns | Bytes | Yes |
    | 2 | Cache | 1 to 20 ns | KB to MB | Yes |
    | 3 | RAM | 50 to 100 ns | GB | Yes |
    | 4 (slowest) | Hard disk | 5 to 10 ms | GB to TB | No |

    The fastest is the register.

    Reason for the order:
    - A register is inside the CPU itself, in the same silicon as the ALU, so it is read in the same clock cycle as the operation that uses it.
    - Cache is SRAM placed on or beside the CPU die, very fast but limited in size by cost.
    - RAM is DRAM on the motherboard, reached over an external bus, which adds latency, and it needs periodic refreshing.
    - A hard disk is a mechanical device; the head must move to the right track and the platter must rotate to the right sector, which takes milliseconds, roughly a hundred thousand times longer than a RAM access.

    General rule of the hierarchy: as speed increases, capacity decreases and cost per bit increases.
17. **RAM and ROM difference লিখ?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 944 (ET: N/A)]*


    Answer:

    | Point | RAM (Random Access Memory) | ROM (Read Only Memory) |
    |---|---|---|
    | Full form | Random Access Memory | Read Only Memory |
    | Volatility | Volatile; contents are lost when power is switched off | Non-volatile; contents are retained without power |
    | Read and write | Both reading and writing are possible | Normally only reading; writing needs a special process |
    | Purpose | Working memory that holds the operating system, running programs and their data | Permanent storage of firmware such as BIOS and the bootstrap loader |
    | Speed | Fast | Slower than RAM |
    | Capacity | Large, gigabytes | Small, kilobytes to a few megabytes |
    | Cost per bit | Higher | Lower |
    | Modification by user | Contents change constantly during use | Contents are fixed by the manufacturer or programmed once |
    | Types | SRAM, DRAM (SDRAM, DDR, DDR2, DDR3, DDR4, DDR5) | PROM, EPROM, EEPROM, Flash, Mask ROM |
    | Physical form | Removable modules such as DIMM and SO-DIMM | Soldered chip on the motherboard |
    | Example of use | Running a browser or a word processor | Holding the BIOS that starts the computer |

    Key idea: RAM is the desk on which you work, cleared at the end of the day; ROM is the printed instruction manual that stays on the shelf permanently.
18. **(a) Write the difference between: (i) RAM and ROM (ii) Open source software and Proproetary software.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1023-1024 (ET: N/A)]*


    Answer:

    (i) Difference between RAM and ROM:

    | Point | RAM (Random Access Memory) | ROM (Read Only Memory) |
    |---|---|---|
    | Full form | Random Access Memory | Read Only Memory |
    | Volatility | Volatile; contents are lost when power is switched off | Non-volatile; contents are retained without power |
    | Read and write | Both reading and writing are possible | Normally only reading; writing needs a special process |
    | Purpose | Working memory that holds the operating system, running programs and their data | Permanent storage of firmware such as BIOS and the bootstrap loader |
    | Speed | Fast | Slower than RAM |
    | Capacity | Large, gigabytes | Small, kilobytes to a few megabytes |
    | Cost per bit | Higher | Lower |
    | Modification by user | Contents change constantly during use | Contents are fixed by the manufacturer or programmed once |
    | Types | SRAM, DRAM (SDRAM, DDR, DDR2, DDR3, DDR4, DDR5) | PROM, EPROM, EEPROM, Flash, Mask ROM |
    | Physical form | Removable modules such as DIMM and SO-DIMM | Soldered chip on the motherboard |
    | Example of use | Running a browser or a word processor | Holding the BIOS that starts the computer |

    Key idea: RAM is the desk on which you work, cleared at the end of the day; ROM is the printed instruction manual that stays on the shelf permanently.

    (ii) Difference between open source software and proprietary software:

    | Point | Open Source Software | Proprietary Software |
    |---|---|---|
    | Source code | Publicly available; anyone may read, modify and redistribute it | Kept secret by the owner; only the compiled binary is supplied |
    | Licence | GPL, MIT, Apache, BSD and similar permissive or copyleft licences | End User Licence Agreement that restricts copying and modification |
    | Cost | Usually free of charge, though support may be paid for | Purchased, or licensed by subscription |
    | Modification | Permitted and encouraged | Prohibited; reverse engineering is usually forbidden |
    | Redistribution | Permitted under the licence terms | Prohibited without permission |
    | Development | By a community of contributors worldwide | By a single company's in-house team |
    | Support | Community forums, documentation, and optional commercial support | Official vendor support with service level agreements |
    | Security | Many independent reviewers can find flaws, but fixes depend on community activity | Fewer reviewers, but a dedicated team and a formal patch schedule |
    | Update and bug fixing | Often rapid, but not guaranteed | On the vendor's release schedule |
    | Vendor lock-in | Low; the code and data formats remain accessible | High; migration can be difficult and costly |
    | Customisation | Full, down to the source level | Limited to the options the vendor provides |
    | Accountability | No single party is legally responsible | The vendor is contractually responsible |
    | Examples | Linux, Apache, MySQL, PHP, Python, LibreOffice, Firefox, Android Open Source Project | Microsoft Windows, Microsoft Office, Adobe Photoshop, Oracle Database, macOS |

    Relevance for government offices: open source lowers licence cost, avoids vendor lock-in and allows local customisation and audit, which is why many public ICT policies, including in Bangladesh, encourage its use. Proprietary software is chosen where guaranteed vendor support, certified compliance and legal accountability are essential.
19. **(b) Outline the functions performed by memory. List some factors upon which memory can be classified.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1024 (ET: N/A)]*


    Answer:

    Functions performed by memory:
    - Storage: it holds the program instructions, the input data, the intermediate results and the final output.
    - Supplying the CPU: it delivers instructions and data to the processor whenever they are requested, and accepts results back.
    - Holding the operating system: the kernel and its data structures reside in memory while the machine is running.
    - Buffering: it holds data temporarily while it moves between devices that work at different speeds, for example between the CPU and a printer or a disk.
    - Caching: faster levels keep copies of frequently used items from slower levels, so that repeated access is quick.
    - Address mapping and protection: it provides the address space in which programs run, and, with hardware support, keeps one process from reading or writing another's memory.
    - Supporting virtual memory: part of secondary storage is used as an extension of main memory, so a program larger than physical RAM can run.
    - Stack management: it holds the call stack for subroutine calls, local variables and interrupt handling.
    - Permanent retention: non-volatile memory preserves files, programs and firmware when power is off.

    Factors on which memory is classified:
    - Volatility: volatile (RAM, cache, registers) or non-volatile (ROM, flash, HDD, SSD).
    - Accessibility by the CPU: primary memory, which the CPU addresses directly, and secondary memory, which it does not.
    - Access method: random access (RAM, SSD), sequential access (magnetic tape) or direct access (hard disk).
    - Technology: semiconductor, magnetic or optical.
    - Read and write capability: read-write (RAM, disk), read-only (ROM, CD-ROM), or write-once read-many (PROM, CD-R).
    - Speed or access time: from under a nanosecond for registers to milliseconds for disks.
    - Storage capacity: from bytes in registers to terabytes in secondary storage.
    - Cost per bit: highest for registers, lowest for tape and optical media.
    - Physical location: internal (on the motherboard) or external (removable devices).
    - Position in the memory hierarchy: registers, cache, main memory, secondary storage, tertiary storage.

    The design goal that ties these factors together is to combine the speed of the fastest technology with the capacity and cost of the cheapest, which is achieved through the memory hierarchy and the principle of locality.
20. **(c) Given below the list of some memory devices. Identify which are semi-conductor, optical and magnetic memory. CD, RAM, Floppy Disk, Hard Disk, ROM, DVD.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1024 (ET: N/A)]*


    Answer: Classification of the given devices by the technology on which they are based:

    | Technology | Devices | How data is stored |
    |---|---|---|
    | Semiconductor memory | RAM, ROM | As electrical charge or as the state of transistors in an integrated circuit |
    | Magnetic memory | Floppy disk, Hard disk | As the direction of magnetisation of tiny regions on a coated surface |
    | Optical memory | CD, DVD | As pits and lands on a reflective surface, read by a laser beam |

    Details:

    Semiconductor:
    - RAM: volatile, made of SRAM or DRAM cells, used as main memory.
    - ROM: non-volatile, holds the BIOS and firmware.
    - Other examples not listed in the question: cache, SSD, pen drive, memory card.

    Magnetic:
    - Floppy disk: a flexible magnetic disk, capacity 1.44 MB, now obsolete.
    - Hard disk: rigid magnetic platters spinning at 5,400 to 15,000 revolutions per minute, with a read-write head on an actuator arm; capacity in terabytes.
    - Other examples: magnetic tape, used for backup and archives.

    Optical:
    - CD: 700 MB, read by an infrared laser of 780 nm wavelength.
    - DVD: 4.7 GB single layer, red laser of 650 nm.
    - Other example: Blu-ray, 25 GB per layer, blue-violet laser of 405 nm. A shorter wavelength focuses to a smaller spot, which is why capacity rises from CD to DVD to Blu-ray.
21. **How Maximum size of memory (RAM) is needed that can be addressed by 32-bit system.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1031 (ET: BUET)]*


    Answer: The maximum memory that can be addressed depends on the width of the address bus, because each address line can be either 0 or 1.

    Step 1 - number of distinct addresses with 32 address lines:
    - Number of addresses = 2^32

    Step 2 - compute 2^32:
    - 2^10 = 1,024 = 1 K
    - 2^20 = 1,048,576 = 1 M
    - 2^30 = 1,073,741,824 = 1 G
    - 2^32 = 2^30 x 2^2 = 1 G x 4 = 4 G

    Step 3 - since memory is byte addressable, each address holds one byte:
    - Maximum addressable memory = 4 x 2^30 bytes = 4,294,967,296 bytes

    Final answer: 4 GB (4 gigabytes).

    General formula: with n address lines, the addressable memory is 2^n bytes.

    Related values:
    - 16-bit address bus: 2^16 = 64 KB (as in the Intel 8085)
    - 20-bit address bus: 2^20 = 1 MB (as in the Intel 8086)
    - 24-bit address bus: 2^24 = 16 MB
    - 32-bit address bus: 2^32 = 4 GB
    - 64-bit address bus: 2^64 = 16 exabytes in theory, though current processors implement only 48 or 52 bits

    Practical note: a 32-bit operating system cannot use the full 4 GB for applications, because part of the address space is reserved for the BIOS, the graphics card aperture and other memory-mapped devices. Usable RAM is therefore typically about 3.2 to 3.5 GB. The Physical Address Extension (PAE) feature allows a 32-bit processor to address up to 64 GB by widening the physical address to 36 bits, but any single process is still limited to 4 GB of virtual address space.

## RAID Architecture & Storage (13)

1. **Which RAID level is best and why?** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 319 (ET: N/A)], [BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*


   Answer: There is no single RAID level that is best in every situation, because each level trades performance, capacity and fault tolerance differently. The correct answer is to name the best level for a given purpose and to justify it.

   | Level | Technique | Minimum disks | Usable capacity | Fault tolerance | Read speed | Write speed | Typical use |
   |---|---|---|---|---|---|---|---|
   | RAID 0 | Striping only | 2 | 100 per cent | None; one failure loses everything | Very high | Very high | Video editing scratch space, temporary data |
   | RAID 1 | Mirroring | 2 | 50 per cent | Survives 1 disk failure | High | Same as a single disk | Operating system and boot volumes, small servers |
   | RAID 5 | Striping with distributed parity | 3 | (n-1)/n | Survives 1 disk failure | High | Moderate; a write costs read-modify-write | File servers, general purpose storage |
   | RAID 6 | Striping with double distributed parity | 4 | (n-2)/n | Survives 2 disk failures | High | Lower than RAID 5 | Large arrays with high-capacity drives |
   | RAID 10 (1+0) | Mirrored pairs, then striped | 4 | 50 per cent | Survives at least 1, often more, failures | Very high | Very high | Databases, high-transaction OLTP systems |
   | RAID 50 (5+0) | Striped RAID 5 groups | 6 | Varies | 1 failure per group | Very high | High | Large file and application servers |

   Parity calculation: parity is the bitwise XOR of the data blocks in a stripe. For example, with data blocks A = 1011 and B = 0110, parity P = A XOR B = 1101. If the disk holding A fails, A is recovered as B XOR P = 0110 XOR 1101 = 1011, the original value.

   The usual answers, with justification:

   - Best overall for a database or any transaction-heavy server: RAID 10.
     - It combines mirroring and striping, so it gives both high read speed and high write speed.
     - It has no parity to compute, so there is no write penalty, which matters greatly for the small random writes that databases produce.
     - Rebuilding after a failure is fast and low-risk, because it is a simple block-for-block copy from the surviving mirror rather than a computation across every other disk.
     - Its drawback is cost: only 50 per cent of the raw capacity is usable.

   - Best balance of capacity, protection and cost for general file storage: RAID 5.
     - It gives fault tolerance for one disk failure while sacrificing the capacity of only a single disk, so usable capacity is (n-1)/n.
     - It gives excellent read performance, because reads are striped across all disks.
     - Its drawback is the write penalty: every small write requires reading the old data and parity, computing the new parity, and writing both back. Rebuilding is also slow and stresses every remaining disk, which raises the risk of a second failure during rebuild.

   - Best for very large arrays of high-capacity drives: RAID 6, because with modern multi-terabyte disks a rebuild takes many hours or days, during which a second failure is a real possibility. RAID 6 survives two simultaneous failures.

   - Best for pure speed with no need for protection: RAID 0, for scratch and temporary data only.

   Conclusion: for a bank or an organisation running transactional databases, RAID 10 is preferred despite its cost, because performance and rebuild safety matter more than capacity. For a departmental file server where capacity matters most, RAID 5 or RAID 6 is chosen.
2. **Striping with parity is done in which level of RAID.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*


   Answer: Striping with parity is done in RAID 5, and striping with double parity in RAID 6.

   RAID 5 - striping with distributed parity:
   - Data is striped in blocks across all disks, and for each stripe one parity block is computed as the XOR of the data blocks in that stripe.
   - The parity block is not kept on one dedicated disk; it rotates across all disks, which is why it is called distributed parity. This avoids the bottleneck that a single dedicated parity disk would create.
   - Minimum disks: 3. Usable capacity: (n-1)/n of the total. Fault tolerance: one disk failure.

   RAID 6 - striping with double distributed parity:
   - Two independent parity blocks are computed per stripe, so the array survives two simultaneous disk failures.
   - Minimum disks: 4. Usable capacity: (n-2)/n.

   For completeness:
   - RAID 3 and RAID 4 also use parity, but on a single dedicated parity disk. RAID 3 stripes at byte level and RAID 4 at block level. Both are rarely used today, because the dedicated parity disk becomes a write bottleneck.
   - RAID 0 uses striping without parity, so it has no fault tolerance.
   - RAID 1 uses mirroring, not parity.

   How parity works: parity is the bitwise XOR of the data blocks in a stripe. With A = 1011 and B = 0110, parity P = A XOR B = 1101. If the disk holding A fails, A is recovered as B XOR P = 0110 XOR 1101 = 1011. The same single parity therefore protects against the loss of any one block in the stripe, but only one.
3. **Concept of RAID, Relevance in Database, Uses in Database, is it possible?** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 319 (ET: N/A)]*


   Answer:

   Concept of RAID:
   RAID stands for Redundant Array of Independent Disks (originally Redundant Array of Inexpensive Disks). It is a technology that combines several physical disk drives into a single logical unit in order to improve performance, provide fault tolerance, or both.

   Three basic techniques are used, alone or in combination:
   - Striping: data is split into blocks and written across several disks in turn, so several disks work in parallel and the transfer rate multiplies. Striping alone gives speed but no protection.
   - Mirroring: the same data is written identically to two or more disks, so if one fails the other still holds a complete copy. Mirroring gives protection but costs capacity.
   - Parity: an extra block is computed by an XOR of the data blocks and stored on another disk. If any one disk fails, its contents can be reconstructed from the remaining data and the parity. Parity gives protection at a much lower capacity cost than mirroring.

   Relevance to a database:
   - A database is the workload for which storage performance and reliability matter most, because every transaction involves disk input and output, and the loss of a single data file can destroy the whole system.
   - Databases generate a great deal of small random reads and writes, which is precisely the pattern that a single disk handles worst and that striping across several disks improves.
   - The transaction log must be written before a commit can be acknowledged, so log write latency directly limits transaction throughput.
   - Continuous availability is usually required, and RAID allows the system to keep running while a failed disk is replaced.

   Uses in a database:
   - Data files: RAID 10 for heavy transactional systems, or RAID 5 or RAID 6 for read-heavy data warehouses where capacity matters more.
   - Transaction log: usually placed on its own RAID 1 or RAID 10 volume, because the log is written sequentially and its latency is critical.
   - Temporary and scratch space: sometimes RAID 0, since it can be rebuilt if lost.
   - Backups: on a separate array, never on the same physical disks as the live data.
   - Separating the data files, log files and temporary space onto different physical arrays prevents them from competing for the same spindles.

   Is it possible? Yes, and it is standard practice. Every serious database deployment, including those of banks and government systems in Bangladesh, runs on RAID storage or on a SAN that itself uses RAID internally. The database software is unaware of RAID; it sees a single logical volume, and the RAID controller or the operating system handles the distribution and redundancy.

   Important warning: RAID is not a backup. It protects against the mechanical failure of a disk, but it does not protect against accidental deletion, a corrupt transaction, ransomware, fire, theft or a controller failure, because every such event is faithfully written to all the disks at once. A separate backup regime, preferably off-site, is always required.
4. **How to solve drive failure in RAID?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1454 (ET: BUET)]*


   Answer: Solving a drive failure in a RAID array follows a defined procedure. What is possible depends on the RAID level.

   Step 1 - detect the failure:
   - The RAID controller marks the array as degraded and raises an alert through the management software, an audible alarm, an indicator light on the drive bay, or an entry in the system log.
   - In a degraded state the array continues to serve data, but with no remaining protection (in RAID 1, 5 and 10) and with reduced performance.

   Step 2 - identify the failed drive:
   - Use the controller utility to find the exact slot. Most enclosures allow the light on the failed bay to be flashed, which prevents the fatal mistake of pulling a healthy drive.

   Step 3 - take a backup before doing anything else:
   - The array is unprotected while degraded, so if the data is critical and a current backup does not exist, copy it off first.

   Step 4 - replace the drive:
   - Hot swap: in enterprise systems with hot-swappable bays, simply remove the failed drive and insert a new one while the system runs.
   - Cold swap: in systems without hot-swap support, shut down, replace and restart.
   - The replacement must be of the same or greater capacity, and preferably the same model and firmware.

   Step 5 - rebuild the array:
   - RAID 1: the surviving mirror is copied block for block onto the new disk. This is fast and low risk.
   - RAID 5: every remaining disk is read in full and the missing data is recomputed by XOR. This is slow and stresses all drives.
   - RAID 6: the same, using one or both parity sets.
   - RAID 10: only the partner of the failed disk in that mirrored pair is read, so the rebuild is fast.
   - RAID 0: no rebuild is possible. All data is lost and must be restored from backup.
   - Rebuild may take from a few hours to more than a day for large drives, and performance is reduced throughout.

   Step 6 - verify and restore protection:
   - Confirm from the controller that the array status has returned to optimal, run a consistency check, and verify that the data is intact.

   If a hot spare is configured, steps 4 and 5 begin automatically the moment the failure is detected, which greatly shortens the window of exposure.

   Preventive measures:
   - Keep hot spares in the array.
   - Enable monitoring and email alerts, and check SMART attributes regularly.
   - Prefer RAID 6 or RAID 10 over RAID 5 when using large drives, because of the long rebuild time.
   - Do not build an array entirely from drives of the same batch, since they tend to fail at similar times.
   - Maintain independent backups, because RAID is redundancy, not backup.
5. **Explain the purpose of RAID.** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 564 (ET: N/A)]*


   Answer: The purpose of RAID (Redundant Array of Independent Disks) is to combine several physical disks into one logical unit in order to achieve one or more of the following objectives.

   - Fault tolerance and data protection: by keeping a mirror copy or a parity block, the array continues to work when a disk fails, and the lost data can be reconstructed. This is the primary purpose of RAID 1, 5, 6 and 10.
   - Improved performance: by striping data across several disks, several read or write operations proceed in parallel, so the transfer rate and the number of operations per second multiply. This is the purpose of RAID 0, and it is also present in RAID 5, 6 and 10.
   - High availability and continuous service: a business system need not be shut down when a disk fails, because a degraded array keeps serving data and a hot-swappable drive can be replaced while the system runs.
   - Larger logical volumes: several smaller disks are combined into one large volume, so a file system can exceed the size of any single physical disk.
   - Better use of inexpensive hardware: the original idea was that many cheap drives with redundancy could match the reliability of one very expensive drive at a lower total cost.
   - Reduced downtime and recovery time: rebuilding onto a replacement disk is far faster than restoring an entire system from tape or from an off-site backup.
   - Simplified management: the operating system sees a single logical drive instead of many separate ones.

   What RAID does not do: it is not a backup. It protects against the mechanical failure of a disk only. Accidental deletion, file corruption, ransomware, a database error, fire, theft or a controller failure will affect every disk in the array simultaneously. A separate, preferably off-site, backup is therefore always required in addition to RAID.
6. **What do you mean by RAID? Write the difference types of RAID level.** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 595 (ET: N/A)]*


   Answer: RAID stands for Redundant Array of Independent Disks (originally Redundant Array of Inexpensive Disks). It is a technology that combines several physical disk drives into a single logical unit in order to improve performance, provide fault tolerance, or both.

   Three basic techniques are used, alone or in combination:
   - Striping: data is split into blocks and written across several disks in turn, so several disks work in parallel and the transfer rate multiplies. Striping alone gives speed but no protection.
   - Mirroring: the same data is written identically to two or more disks, so if one fails the other still holds a complete copy. Mirroring gives protection but costs capacity.
   - Parity: an extra block is computed by an XOR of the data blocks and stored on another disk. If any one disk fails, its contents can be reconstructed from the remaining data and the parity. Parity gives protection at a much lower capacity cost than mirroring.

   The different RAID levels:

   | Level | Technique | Minimum disks | Usable capacity | Fault tolerance | Read speed | Write speed | Typical use |
   |---|---|---|---|---|---|---|---|
   | RAID 0 | Striping only | 2 | 100 per cent | None; one failure loses everything | Very high | Very high | Video editing scratch space, temporary data |
   | RAID 1 | Mirroring | 2 | 50 per cent | Survives 1 disk failure | High | Same as a single disk | Operating system and boot volumes, small servers |
   | RAID 5 | Striping with distributed parity | 3 | (n-1)/n | Survives 1 disk failure | High | Moderate; a write costs read-modify-write | File servers, general purpose storage |
   | RAID 6 | Striping with double distributed parity | 4 | (n-2)/n | Survives 2 disk failures | High | Lower than RAID 5 | Large arrays with high-capacity drives |
   | RAID 10 (1+0) | Mirrored pairs, then striped | 4 | 50 per cent | Survives at least 1, often more, failures | Very high | Very high | Databases, high-transaction OLTP systems |
   | RAID 50 (5+0) | Striped RAID 5 groups | 6 | Varies | 1 failure per group | Very high | High | Large file and application servers |

   Parity calculation: parity is the bitwise XOR of the data blocks in a stripe. For example, with data blocks A = 1011 and B = 0110, parity P = A XOR B = 1101. If the disk holding A fails, A is recovered as B XOR P = 0110 XOR 1101 = 1011, the original value.

   Descriptions of the main levels:

   - RAID 0 (striping): data is divided into blocks and written across all disks in turn. It gives the highest performance and uses 100 per cent of the capacity, but it has no redundancy at all. The failure of any one disk destroys the entire array, and the risk actually increases with the number of disks. Used only for temporary or reproducible data.

   - RAID 1 (mirroring): every block is written identically to two disks. Reads can be served from either disk, so read performance improves, while write performance is about that of a single disk. Only 50 per cent of the capacity is usable, but rebuilding is a simple copy and is therefore fast and safe. Used for boot volumes and small critical systems.

   - RAID 5 (striping with distributed parity): needs at least three disks. Each stripe has one parity block, computed by XOR, and the parity rotates across the disks. It survives one disk failure and gives (n-1)/n usable capacity, which makes it the most capacity-efficient protected level. Its weakness is the write penalty and the long, risky rebuild.

   - RAID 6 (striping with double parity): needs at least four disks and survives two simultaneous failures, at the cost of (n-2)/n usable capacity and a heavier write penalty. It is the preferred choice for arrays built from large modern drives, because rebuilds take so long that a second failure during rebuild is a genuine risk.

   - RAID 10 (mirroring then striping): needs at least four disks. Disks are first paired as mirrors, and the mirrored pairs are then striped. It gives the performance of RAID 0 and the safety and fast rebuild of RAID 1, at the cost of 50 per cent of the capacity. It is the standard choice for databases.

   Note on RAID 2, 3 and 4: RAID 2 used Hamming code error correction and is obsolete. RAID 3 stripes at byte level and RAID 4 at block level, both with a single dedicated parity disk, which becomes a bottleneck. All three are rare in practice.
7. **What is RAID technology? Why it's important Server in data center?** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 555 (ET: BIBM)]*


   Answer: RAID technology combines several physical disk drives into a single logical storage unit using striping, mirroring and parity, so as to improve performance, provide fault tolerance, or both.

   Why it is important for a server in a data centre:

   - Continuous availability: a data centre serves users around the clock, and a disk is the component most likely to fail because it is the only major part with moving mechanics. RAID allows the server to keep running in a degraded state when a disk fails, so there is no service interruption and no missed service level agreement.
   - Protection against data loss: banking transactions, national identity records, medical records and government files cannot be lost. Mirroring or parity guarantees that the failure of a drive does not destroy the data.
   - Hot swapping: enterprise arrays allow a failed disk to be pulled and replaced while the system is powered and serving requests, so maintenance requires no downtime window.
   - Performance under heavy load: a data centre server handles thousands of concurrent requests. Striping distributes those requests across many spindles, so throughput and input-output operations per second scale with the number of disks.
   - Large capacity as one volume: databases and virtual machine stores routinely exceed the capacity of a single drive, so many drives must be presented as one logical volume.
   - Faster recovery: rebuilding onto a replacement disk restores protection in hours, whereas restoring a multi-terabyte system from backup tape could take days.
   - Hot spares and automatic rebuild: a spare disk sitting idle in the enclosure is brought into the array automatically the moment a failure is detected, which shortens the unprotected window to minutes.
   - Cost efficiency: many standard drives with redundancy are far cheaper than a single ultra-reliable drive of the same total capacity.
   - Foundation for virtualisation and cloud: hypervisors, container platforms and storage area networks all assume a reliable, fast, large shared volume underneath, which RAID provides.

   Typical choices in a data centre: RAID 10 for database and transaction servers where speed and rebuild safety dominate, RAID 6 for bulk file and archive storage where capacity dominates, and RAID 1 for operating system and boot volumes.

   Essential caution: RAID protects against hardware failure only. Data centres therefore combine RAID with regular backups, off-site replication and a disaster recovery site, which in Bangladesh is the model used for the National Data Center at Kaliakair with its disaster recovery site at Jashore.
8. **(a) Compare RAID 1 and RAID 5 levels. Which one you prefer? Why?** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 691 (ET: N/A)]*


   Answer: Comparison of RAID 1 and RAID 5:

   | Point | RAID 1 (Mirroring) | RAID 5 (Striping with distributed parity) |
   |---|---|---|
   | Technique | Identical copy of all data on two or more disks | Data striped across disks with one rotating parity block per stripe |
   | Minimum disks | 2 | 3 |
   | Usable capacity | 50 per cent | (n-1)/n, for example 75 per cent with 4 disks |
   | Fault tolerance | Survives 1 disk failure (more with additional mirrors) | Survives 1 disk failure |
   | Read performance | High; either copy can serve a read | High; reads are spread across all disks |
   | Write performance | About that of a single disk; each write goes to both disks | Lower; each small write needs a read-modify-write cycle for the parity, known as the write penalty |
   | Rebuild method | Direct block-for-block copy from the surviving mirror | Read every surviving disk in full and recompute by XOR |
   | Rebuild speed and risk | Fast and low risk | Slow, and it stresses every remaining disk, raising the chance of a second failure during rebuild |
   | Controller overhead | Very low, no calculation required | Higher; parity must be computed on every write |
   | Cost per usable gigabyte | High | Lower |
   | Suitable for | Boot volumes, transaction logs, small critical systems | File servers, archives, read-heavy general storage |

   Which one I prefer, and why:

   The choice depends on the workload, so a good answer states the condition:

   - For a database server, a transaction log, or any write-intensive and latency-sensitive system, I prefer RAID 1 (or RAID 10, which extends it with striping). The reasons are that there is no parity calculation and therefore no write penalty, the read performance is high, and above all the rebuild is a simple copy, which is fast and does not endanger the remaining disks. In a bank or a government transaction system, the extra cost of the lost 50 per cent of capacity is small compared with the cost of slow writes or a failed rebuild.

   - For a departmental file server, a document archive or a backup target, where the data is read far more often than it is written and where capacity per taka matters, I prefer RAID 5. With five disks it gives 80 per cent usable capacity instead of 50 per cent, which is a large saving on a big array.

   - Caveat for modern large drives: as drive capacity has grown into the multi-terabyte range, a RAID 5 rebuild can take a day or more, during which a second failure destroys everything. For such arrays RAID 6 should be used instead of RAID 5.

   Overall preference for a critical production system: RAID 10, because it gives the performance of striping together with the fast, safe rebuild of mirroring.
9. **What is RAID?** *[BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*


   Answer: RAID stands for Redundant Array of Independent Disks (originally Redundant Array of Inexpensive Disks). It is a technology that combines several physical disk drives into a single logical unit in order to improve performance, provide fault tolerance, or both.

   Three basic techniques are used, alone or in combination:
   - Striping: data is split into blocks and written across several disks in turn, so several disks work in parallel and the transfer rate multiplies. Striping alone gives speed but no protection.
   - Mirroring: the same data is written identically to two or more disks, so if one fails the other still holds a complete copy. Mirroring gives protection but costs capacity.
   - Parity: an extra block is computed by an XOR of the data blocks and stored on another disk. If any one disk fails, its contents can be reconstructed from the remaining data and the parity. Parity gives protection at a much lower capacity cost than mirroring.

   In short: RAID makes many disks behave as one, so that the system is faster, safer, or both.

   The common levels in one line each:
   - RAID 0: striping only. Fastest, no protection.
   - RAID 1: mirroring. Full copy, survives one failure, half the capacity usable.
   - RAID 5: striping with distributed parity. Survives one failure, (n-1)/n capacity usable.
   - RAID 6: double parity. Survives two failures.
   - RAID 10: mirrored pairs then striped. Best performance with protection, half the capacity usable.

   Implementation: RAID can be hardware based, using a dedicated controller card with its own processor and battery-backed cache, or software based, implemented by the operating system (for example mdadm on Linux, Storage Spaces on Windows, or ZFS). Hardware RAID is faster and independent of the operating system; software RAID is cheaper and more flexible.

   Important caution: RAID is redundancy, not backup. It protects against the mechanical failure of a disk but not against deletion, corruption, ransomware, fire or theft, because those affect all disks at once.
10. **What is RAID? What is the classification of RAIDs? Difference between RAID 1 and RAID 5 using illustration.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 755 (ET: N/A)]*


    Answer: RAID stands for Redundant Array of Independent Disks (originally Redundant Array of Inexpensive Disks). It is a technology that combines several physical disk drives into a single logical unit in order to improve performance, provide fault tolerance, or both.

     Three basic techniques are used, alone or in combination:
     - Striping: data is split into blocks and written across several disks in turn, so several disks work in parallel and the transfer rate multiplies. Striping alone gives speed but no protection.
     - Mirroring: the same data is written identically to two or more disks, so if one fails the other still holds a complete copy. Mirroring gives protection but costs capacity.
     - Parity: an extra block is computed by an XOR of the data blocks and stored on another disk. If any one disk fails, its contents can be reconstructed from the remaining data and the parity. Parity gives protection at a much lower capacity cost than mirroring.

     Classification of RAID levels:

    | Level | Technique | Minimum disks | Usable capacity | Fault tolerance | Read speed | Write speed | Typical use |
    |---|---|---|---|---|---|---|---|
    | RAID 0 | Striping only | 2 | 100 per cent | None; one failure loses everything | Very high | Very high | Video editing scratch space, temporary data |
    | RAID 1 | Mirroring | 2 | 50 per cent | Survives 1 disk failure | High | Same as a single disk | Operating system and boot volumes, small servers |
    | RAID 5 | Striping with distributed parity | 3 | (n-1)/n | Survives 1 disk failure | High | Moderate; a write costs read-modify-write | File servers, general purpose storage |
    | RAID 6 | Striping with double distributed parity | 4 | (n-2)/n | Survives 2 disk failures | High | Lower than RAID 5 | Large arrays with high-capacity drives |
    | RAID 10 (1+0) | Mirrored pairs, then striped | 4 | 50 per cent | Survives at least 1, often more, failures | Very high | Very high | Databases, high-transaction OLTP systems |
    | RAID 50 (5+0) | Striped RAID 5 groups | 6 | Varies | 1 failure per group | Very high | High | Large file and application servers |

    Parity calculation: parity is the bitwise XOR of the data blocks in a stripe. For example, with data blocks A = 1011 and B = 0110, parity P = A XOR B = 1101. If the disk holding A fails, A is recovered as B XOR P = 0110 XOR 1101 = 1011, the original value.

     Difference between RAID 1 and RAID 5, with illustration:

     RAID 1 with 2 disks. Every block is written twice, once to each disk.

     ```
       Disk 1        Disk 2
       ------        ------
         A             A
         B             B
         C             C
         D             D

       Usable capacity: 50 per cent
       If Disk 1 fails, Disk 2 already holds a complete copy.
       Rebuild = straight copy from Disk 2 to the replacement.
     ```

     RAID 5 with 4 disks. Each stripe has three data blocks and one parity block, and the parity rotates.

     ```
       Disk 1     Disk 2     Disk 3     Disk 4
       ------     ------     ------     ------
         A1         A2         A3         Ap
         B1         B2         Bp         B3
         C1         Cp         C2         C3
         Dp         D1         D2         D3

       Ap = A1 XOR A2 XOR A3, and so on for each stripe.
       Usable capacity: 3 of 4 disks = 75 per cent
       If Disk 2 fails, A2 is recovered as A1 XOR A3 XOR Ap,
       and the same computation restores B2, C2 (parity) and D2.
     ```

     | Point | RAID 1 | RAID 5 |
     |---|---|---|
     | Minimum disks | 2 | 3 |
     | Usable capacity | 50 per cent | (n-1)/n |
     | Write performance | Same as a single disk | Reduced by the parity write penalty |
     | Rebuild | Fast, a simple copy | Slow, must read every surviving disk |
     | Controller work | Minimal | Parity computation on every write |
     | Cost per usable gigabyte | High | Lower |
     | Best for | Boot volumes, transaction logs, small critical systems | File servers, archives, read-heavy storage |
11. **What is RAID technology? Describe about the advantages of RAID technology.** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 820 (ET: BUET)]*


    Answer: RAID technology, which stands for Redundant Array of Independent Disks, is a method of combining several physical disk drives into a single logical unit through striping, mirroring and parity, in order to improve performance, provide fault tolerance, or both.

    Advantages of RAID technology:

    - Fault tolerance: the array continues to operate when a disk fails. RAID 1, 5 and 10 survive one failure, and RAID 6 survives two. Without RAID, a single disk failure means immediate loss of service and of data.
    - Data reconstruction: the contents of a failed disk can be rebuilt automatically onto a replacement, using the mirror copy or the parity blocks, so no data is lost.
    - Improved read performance: because data is striped across several disks, several reads proceed in parallel, which multiplies the transfer rate and the number of operations per second.
    - Improved write performance in the striping levels: RAID 0 and RAID 10 write in parallel across disks, giving a large gain over a single drive.
    - High availability and reduced downtime: with hot-swappable bays a failed disk is replaced while the system runs, so critical services need not be stopped.
    - Automatic recovery with hot spares: a spare disk kept idle in the enclosure is brought into service automatically the moment a failure is detected, so the unprotected window is minutes rather than hours.
    - Large logical volumes: many smaller drives are presented as one large volume, so a file system or database can exceed the capacity of any single physical disk.
    - Cost effectiveness: several ordinary drives with redundancy give the reliability that would otherwise require a single very expensive drive, at a lower total cost.
    - Transparency to software: the operating system and the applications see one ordinary drive, so no application needs to be modified.
    - Scalability: capacity is increased by adding drives to the array rather than by rebuilding the system.
    - Choice of trade-off: different levels allow the administrator to choose between speed, capacity and protection according to the workload.
    - Faster recovery than backup restoration: rebuilding a disk takes hours, whereas restoring a large system from backup media can take days.

    Limitations that must be stated alongside the advantages:
    - RAID is not a backup. It gives no protection against accidental deletion, file corruption, ransomware, fire or theft, because every such event is written to all disks at once.
    - The controller itself is a single point of failure unless it is duplicated.
    - Levels with parity impose a write penalty.
    - Rebuild times on large modern drives are long, and performance is degraded throughout.
    - Redundancy costs capacity: 50 per cent in RAID 1 and 10, and one or two disks in RAID 5 and 6.
12. **Why necessary to use RAID? If you choose a RAID level for an organization with huge data process. Justify your answer?** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 854 (ET: N/A)]*


    Answer: Why RAID is necessary:

    - A disk drive is the component of a server most likely to fail, because it is the only major part with moving mechanics. Without redundancy, one failure stops the service and destroys the data.
    - Modern systems need more capacity and more input-output operations per second than a single drive can provide, so several drives must work together.
    - Business systems must remain available continuously; RAID allows a failed drive to be replaced while the system runs.
    - Restoring a large system from backup can take days, whereas a RAID rebuild takes hours and requires no service interruption.
    - Striping across several spindles multiplies throughput, which matters for databases, virtualisation and file services.

    Choice of RAID level for an organisation with a huge data processing load, with justification:

    Recommended level: RAID 10 for the transactional data and RAID 6 for bulk and archival storage.

    Justification for RAID 10 on the transaction and database tier:
    - Heavy data processing means a very large number of small random reads and writes. RAID 10 has no parity, so there is no read-modify-write penalty on every small write, whereas RAID 5 would suffer badly under exactly this pattern.
    - It gives the read and write performance of striping combined with the safety of mirroring, which is the best performance available with protection.
    - Rebuilding is a straight copy from the surviving member of the mirrored pair. It is fast and it does not stress the whole array, so the risk of a second failure during rebuild is low. In RAID 5 a rebuild must read every remaining disk in full, which both takes far longer and raises the chance of a second failure.
    - It can survive more than one failure, provided the failures are not both members of the same mirrored pair.
    - The cost is that only 50 per cent of the raw capacity is usable. For an organisation whose business depends on transaction throughput and data integrity, this cost is justified.

    Justification for RAID 6 on the bulk and archive tier:
    - Archival data is written once and read many times, so the write penalty matters little.
    - Capacity efficiency of (n-2)/n is far better than the 50 per cent of RAID 10.
    - With multi-terabyte drives a rebuild takes a day or more, during which RAID 5 would be completely unprotected. RAID 6 survives a second failure during that window, which is why RAID 5 is no longer recommended for large arrays.

    Supporting measures that must accompany the choice:
    - Configure hot spares so that rebuilding begins automatically.
    - Use a hardware controller with battery-backed or flash-backed write cache.
    - Separate the database data files, the transaction log and the temporary space onto different arrays.
    - Monitor SMART data and set up alerts.
    - Maintain independent backups and an off-site disaster recovery site, because RAID is redundancy and not backup.
13. **Your office need some storage device. Highest capacity 500GB. Two system backup of 30GB. Using RAID 1, Explain how many storage devices will need?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*


    Answer: Given:
    - The largest single storage requirement is 500 GB.
    - Two system backups of 30 GB each are also to be kept.
    - RAID 1 (mirroring) is to be used.

    Step 1 - find the total usable capacity required:
    - Main storage = 500 GB
    - Backups = 2 x 30 GB = 60 GB
    - Total usable capacity required = 500 + 60 = 560 GB

    Step 2 - apply the RAID 1 rule:
    - In RAID 1 every block is written to two disks, so only 50 per cent of the raw capacity is usable.
    - Raw capacity required = 2 x usable capacity
    - = 2 x 560 GB
    - = 1120 GB

    Step 3 - decide the number of drives, taking a practical drive size:
    - If 500 GB drives are used, the pair gives 500 GB usable, which is not enough for 560 GB. Two mirrored pairs would be needed, that is 4 drives, giving 1000 GB usable.
    - If 1 TB (1000 GB) drives are used, one mirrored pair gives 1000 GB usable, which comfortably covers the 560 GB requirement with room to grow.

    Final answer:
    - The minimum is 2 drives of at least 560 GB each, in one mirrored pair. In practice, using standard 1 TB drives, 2 drives are sufficient.
    - If only 500 GB drives are available, 4 drives are needed, arranged as two mirrored pairs, because a single 500 GB pair cannot hold 560 GB.

    Recommended configuration:
    - 2 drives of 1 TB in RAID 1, giving 1 TB usable, which holds the 500 GB of data and the 60 GB of backups with about 440 GB spare for growth.
    - Add one hot spare drive, making 3 drives in total, so that rebuilding starts automatically if one fails.

    Important note to add in the answer: keeping the backups on the same RAID array as the live data is poor practice. A RAID array protects only against the mechanical failure of a disk; accidental deletion, corruption, ransomware, fire or theft would destroy the live data and the backups together. The backups should be kept on a separate device, and preferably off site.

## Cache Memory (12)

1. Explain the difference between a "Compulsory Miss" (Cold Miss) and a "Capacity Miss" in cache memory. [SO IT 25-07-2026]


   Answer: Cache misses are classified into three kinds, known as the three Cs: compulsory, capacity and conflict.

   Compulsory miss (also called a cold miss or a first-reference miss):
   - It occurs the very first time a block of data is referenced, because that block has never been in the cache before.
   - It is unavoidable regardless of how large the cache is made, since the data must be brought in from main memory at least once.
   - It dominates at the start of a program, when the cache is empty, which is why it is called a cold start.
   - Remedies: increase the block size, so that one miss brings in more useful neighbouring data (spatial locality), or use hardware or software prefetching to fetch a block before it is actually needed.

   Capacity miss:
   - It occurs when the working set of the program is larger than the cache, so a block that was previously loaded had to be evicted to make room, and is then referenced again.
   - It would not happen in a cache of unlimited size, which is exactly what distinguishes it from a compulsory miss.
   - It becomes worse as the program's active data set grows relative to the cache.
   - Remedies: increase the cache size, add another level of cache, or restructure the program so that its working set is smaller, for example by blocking or tiling a matrix computation.

   Conflict miss (mentioned for completeness):
   - It occurs in a direct-mapped or set-associative cache when several blocks map to the same set and evict one another, even though the cache as a whole still has free space elsewhere.
   - Remedy: raise the associativity, or use a victim cache.

   | Point | Compulsory miss | Capacity miss |
   |---|---|---|
   | Cause | The block has never been referenced before | The block was evicted because the cache was too small |
   | Occurs when | The first access to any block | On re-access after eviction |
   | Would a larger cache help? | No | Yes |
   | Would an infinite cache help? | No | Yes, it would eliminate them entirely |
   | Typical timing | At program start-up, or on first touch of new data | During steady-state execution of a large working set |
   | Main remedy | Larger blocks, prefetching | Larger cache, more cache levels, better data locality in the program |
2. **(d) What is cache memory? Explain the concepts of (i) Cache hit and (ii) Cache miss.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1352 (ET: N/A)]*


   Answer: Cache memory is a small, very fast memory placed between the CPU and the main memory. It is built from SRAM and it holds copies of the instructions and data that the processor has used most recently or is most likely to use next. Its purpose is to bridge the large speed gap between the processor, which works in fractions of a nanosecond, and DRAM main memory, which takes 50 to 100 nanoseconds.

   Levels: L1 is the smallest and fastest and is private to each core, often split into separate instruction and data caches; L2 is larger and slower and is usually per core; L3 is the largest and is shared by all cores.

   Why it works: the principle of locality of reference.
   - Temporal locality: a location that has just been accessed is very likely to be accessed again soon, for example a loop counter.
   - Spatial locality: locations near a recently accessed one are likely to be accessed soon, for example successive elements of an array. This is why data is brought in as a whole block rather than a single byte.

   (i) Cache hit:
   - A cache hit occurs when the data the CPU requests is already present in the cache, so it can be supplied within a few nanoseconds without going to main memory.
   - The proportion of accesses that are hits is called the hit ratio: hit ratio = number of hits / total number of accesses.
   - A well-designed cache achieves a hit ratio of 90 to 99 per cent.
   - Effect: the CPU is not stalled, so the program runs at full speed.

   (ii) Cache miss:
   - A cache miss occurs when the requested data is not in the cache, so the CPU must wait while the whole block containing it is fetched from main memory and placed in the cache.
   - Miss ratio = 1 - hit ratio.
   - A miss costs the miss penalty, which is the time to fetch the block, typically 50 to 200 clock cycles.
   - Types of miss: compulsory (first ever reference), capacity (the working set exceeds the cache) and conflict (several blocks map to the same set).

   Average memory access time:
   AMAT = hit time + (miss ratio x miss penalty)

   Worked example: if the hit time is 2 ns, the miss penalty is 100 ns and the hit ratio is 95 per cent, then
   AMAT = 2 + (0.05 x 100) = 2 + 5 = 7 ns.
   Without a cache every access would take about 100 ns, so the cache has made memory access roughly fourteen times faster.
3. **Write advantage and disadvantage of direct mapping and associative mapping between cache memory and main memory.** *[BCIC Assistant Programmer 14.02.2025 compact it 1330 (ET: BUET)]*


   Answer: Direct mapping and associative mapping are two ways of deciding where a block of main memory may be placed in the cache.

   Direct mapping:
   - Each main memory block can go into exactly one cache line, determined by cache line number = (block number) modulo (number of cache lines).
   - The address is divided into three fields: tag, index (line number) and block offset.

   Advantages of direct mapping:
   - Simplest and cheapest to implement, because only one line has to be checked on every access.
   - Fastest lookup, since a single tag comparison is required; no search is needed.
   - No replacement algorithm is needed, because there is only one possible place for a block, so no decision has to be made about which block to evict.
   - Requires the least hardware, so it is well suited to a large L2 or L3 cache where cost matters.

   Disadvantages of direct mapping:
   - Suffers heavily from conflict misses. If a program repeatedly uses two blocks that happen to map to the same line, they evict each other on every access even though the rest of the cache is empty. This is called thrashing.
   - Cache utilisation can be poor, since some lines are heavily contended while others sit unused.
   - The hit ratio is the lowest of the three schemes.
   - Performance is sensitive to the exact addresses a program uses, so it can be unpredictable.

   Associative mapping (fully associative):
   - Any main memory block may be placed in any cache line.
   - The address is divided into only two fields: tag and block offset.

   Advantages of associative mapping:
   - Complete flexibility of placement, so conflict misses are eliminated entirely; a miss occurs only if the cache is genuinely full or the block has never been seen.
   - Highest hit ratio and the best possible utilisation of the cache.
   - Performance is not sensitive to the particular addresses used by the program.

   Disadvantages of associative mapping:
   - Very expensive, because every line's tag must be compared with the requested tag simultaneously, which requires an array of comparators or a content-addressable memory.
   - The tag field is long, since it must hold the whole block number, so more storage is wasted on tags.
   - Slower access or higher power consumption, because of the parallel comparison of all tags.
   - A replacement algorithm such as LRU, FIFO or random is required, and implementing true LRU across many lines is itself costly.
   - Impractical for a large cache; it is used only for small structures such as the TLB.

   Set-associative mapping, the practical compromise:
   - The cache is divided into sets of k lines each, and a block maps to one set but may occupy any line within it.
   - Only k comparators are needed, so it is far cheaper than fully associative, and conflict misses are greatly reduced compared with direct mapping.
   - Typical modern designs use 4-way or 8-way set-associative caches, which give almost the hit ratio of a fully associative cache at a small fraction of the cost. This is why nearly every real processor uses it.
4. **How many total bits are required for a direct mapped cache with 16KB of data and 4-word blocks? Assuming a 32 bit address?** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 421 (ET: BIBM)]*


   Answer: Given:
   - Cache data size = 16 KB
   - Block size = 4 words
   - Address size = 32 bits
   - Word size = 4 bytes (32 bits), which follows from the 32-bit architecture
   - Mapping = direct mapped

   Step 1 - find the block size in bytes:
   - Block size = 4 words x 4 bytes per word = 16 bytes

   Step 2 - find the number of blocks (cache lines):
   - Number of blocks = cache size / block size
   - = 16 KB / 16 bytes
   - = 16,384 / 16
   - = 1,024 blocks = 2^10

   Step 3 - find the index field:
   - In a direct mapped cache the index selects one of the 1,024 lines
   - Index bits = log2(1,024) = 10 bits

   Step 4 - find the offset field:
   - The offset selects a byte within the 16-byte block
   - Offset bits = log2(16) = 4 bits
   - These 4 bits are often described as 2 bits to select the word within the block and 2 bits to select the byte within the word

   Step 5 - find the tag field:
   - Tag bits = address bits - index bits - offset bits
   - = 32 - 10 - 4
   - = 18 bits

   Address division:

   | Field | Tag | Index | Block offset |
   |---|---|---|---|
   | Bits | 18 | 10 | 4 |
   | Purpose | Identifies which memory block is stored in the line | Selects the cache line | Selects the byte within the block |

   Step 6 - find the total number of bits in the cache:
   - Each line stores: the data block, the tag, and one valid bit
   - Data per line = 4 words x 32 bits = 128 bits
   - Tag per line = 18 bits
   - Valid bit = 1 bit
   - Total per line = 128 + 18 + 1 = 147 bits
   - Total for the cache = 1,024 x 147 = 150,528 bits

   Final answers:
   - Tag = 18 bits, Index = 10 bits, Offset = 4 bits
   - Total cache size including overhead = 150,528 bits = 147 Kbits = 18,816 bytes = 18.375 KB

   Observation: the cache holds 16 KB of useful data but occupies 18.375 KB of storage, so the overhead of tags and valid bits is about 15 per cent. Using a larger block size would reduce this overhead, because fewer lines would be needed and therefore fewer tags.
5. **6.3 Explain the difference between a "Compulsory Miss" (Cold Miss) and a "Capacity Miss" in cache memory.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*


   Answer: Cache misses are classified into three kinds, known as the three Cs: compulsory, capacity and conflict.

   Compulsory miss (also called a cold miss or a first-reference miss):
   - It occurs the very first time a block of data is referenced, because that block has never been in the cache before.
   - It is unavoidable regardless of how large the cache is made, since the data must be brought in from main memory at least once.
   - It dominates at the start of a program, when the cache is empty, which is why it is called a cold start.
   - Remedies: increase the block size, so that one miss brings in more useful neighbouring data (spatial locality), or use hardware or software prefetching to fetch a block before it is actually needed.

   Capacity miss:
   - It occurs when the working set of the program is larger than the cache, so a block that was previously loaded had to be evicted to make room, and is then referenced again.
   - It would not happen in a cache of unlimited size, which is exactly what distinguishes it from a compulsory miss.
   - It becomes worse as the program's active data set grows relative to the cache.
   - Remedies: increase the cache size, add another level of cache, or restructure the program so that its working set is smaller, for example by blocking or tiling a matrix computation.

   Conflict miss (mentioned for completeness):
   - It occurs in a direct-mapped or set-associative cache when several blocks map to the same set and evict one another, even though the cache as a whole still has free space elsewhere.
   - Remedy: raise the associativity, or use a victim cache.

   | Point | Compulsory miss | Capacity miss |
   |---|---|---|
   | Cause | The block has never been referenced before | The block was evicted because the cache was too small |
   | Occurs when | The first access to any block | On re-access after eviction |
   | Would a larger cache help? | No | Yes |
   | Would an infinite cache help? | No | Yes, it would eliminate them entirely |
   | Typical timing | At program start-up, or on first touch of new data | During steady-state execution of a large working set |
   | Main remedy | Larger blocks, prefetching | Larger cache, more cache levels, better data locality in the program |
6. **Write Concept of cache memory in computer. How its change performance of computer?** *[BITAC Assistant Programmer 27.10.2023 compact it 559 (ET: BUTEX)]*


   Answer: Concept of cache memory:

   Cache memory is a small, extremely fast memory placed between the CPU and the main memory. It is built from SRAM and holds copies of the instructions and data that the processor has used most recently or is most likely to need next.

   The problem it solves: the processor works in fractions of a nanosecond while DRAM main memory needs 50 to 100 nanoseconds. Without a cache the CPU would spend most of its time idle, waiting for memory. This gap is called the memory wall, and it has widened steadily because processor speed has improved much faster than memory latency.

   The principle that makes it work is locality of reference:
   - Temporal locality: an item just used is likely to be used again very soon, for example a loop variable.
   - Spatial locality: items stored near a recently used item are likely to be needed next, for example successive elements of an array. This is why a whole block is fetched rather than a single byte.

   Levels: L1 is small (32 to 64 KB), fastest, and private to each core, usually split into instruction and data caches. L2 is larger (256 KB to 2 MB) and usually per core. L3 is the largest (8 to 64 MB) and shared by all cores.

   Operation: when the CPU requests an address, the cache is searched first. If the data is present it is a cache hit and the data is delivered in a few nanoseconds. If not it is a cache miss, and the whole block containing the address is fetched from main memory, placed in the cache, and then delivered.

   How it changes the performance of a computer:

   - It reduces the average memory access time, which is the direct measure of its effect:
     AMAT = hit time + (miss ratio x miss penalty)
   - Worked example: with a hit time of 2 ns, a miss penalty of 100 ns and a hit ratio of 95 per cent,
     AMAT = 2 + (0.05 x 100) = 7 ns, against 100 ns with no cache. Memory access becomes roughly fourteen times faster.
   - It keeps the CPU busy: fewer stall cycles mean more instructions completed per second, so the effective instructions per cycle rises.
   - It reduces traffic on the memory bus, which matters greatly in a multi-core system where several cores share one memory controller.
   - It saves energy, because reading from a small on-chip SRAM consumes far less power than driving the external bus and activating a DRAM row.
   - It benefits programs with good locality most: loops, array processing and repeated function calls run dramatically faster, while random access over a very large data set benefits little.
   - Larger and better-organised caches are one of the main reasons a newer processor outperforms an older one at the same clock speed.

   Limits: a cache cannot help with compulsory misses, its benefit falls off as the cache grows (diminishing returns), it occupies expensive die area, and in multi-core systems it requires cache coherence protocols such as MESI to keep the copies in different cores consistent.
7. **Suppose we have a 16 KB of data in a direct mapped cache with 4 word blocks. Determine the size of the tag, index and offset fields if we are using a 32-bit architecture.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 439 (ET: BIBM)]*


   Answer: Given:
   - Cache data size = 16 KB
   - Block size = 4 words
   - Address size = 32 bits
   - Word size = 4 bytes (32 bits), which follows from the 32-bit architecture
   - Mapping = direct mapped

   Step 1 - find the block size in bytes:
   - Block size = 4 words x 4 bytes per word = 16 bytes

   Step 2 - find the number of blocks (cache lines):
   - Number of blocks = cache size / block size
   - = 16 KB / 16 bytes
   - = 16,384 / 16
   - = 1,024 blocks = 2^10

   Step 3 - find the index field:
   - In a direct mapped cache the index selects one of the 1,024 lines
   - Index bits = log2(1,024) = 10 bits

   Step 4 - find the offset field:
   - The offset selects a byte within the 16-byte block
   - Offset bits = log2(16) = 4 bits
   - These 4 bits are often described as 2 bits to select the word within the block and 2 bits to select the byte within the word

   Step 5 - find the tag field:
   - Tag bits = address bits - index bits - offset bits
   - = 32 - 10 - 4
   - = 18 bits

   Address division:

   | Field | Tag | Index | Block offset |
   |---|---|---|---|
   | Bits | 18 | 10 | 4 |
   | Purpose | Identifies which memory block is stored in the line | Selects the cache line | Selects the byte within the block |

   Step 6 - find the total number of bits in the cache:
   - Each line stores: the data block, the tag, and one valid bit
   - Data per line = 4 words x 32 bits = 128 bits
   - Tag per line = 18 bits
   - Valid bit = 1 bit
   - Total per line = 128 + 18 + 1 = 147 bits
   - Total for the cache = 1,024 x 147 = 150,528 bits

   Final answers:
   - Tag = 18 bits, Index = 10 bits, Offset = 4 bits
   - Total cache size including overhead = 150,528 bits = 147 Kbits = 18,816 bytes = 18.375 KB

   Observation: the cache holds 16 KB of useful data but occupies 18.375 KB of storage, so the overhead of tags and valid bits is about 15 per cent. Using a larger block size would reduce this overhead, because fewer lines would be needed and therefore fewer tags.
8. **What is the use of cache memory?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*


   Answer: The use of cache memory is to bridge the speed gap between the very fast CPU and the comparatively slow main memory, so that the processor spends less time waiting for data.

   Specific uses:
   - Storing frequently used data and instructions: the items a program uses repeatedly, such as loop bodies and loop counters, are kept where they can be reached in a few nanoseconds.
   - Storing recently used data: by temporal locality, whatever has just been used is likely to be used again shortly, so it is retained.
   - Prefetching neighbouring data: because a whole block is fetched on a miss, the neighbouring items are already present when they are needed, which exploits spatial locality.
   - Reducing average memory access time, which is the direct performance benefit.
   - Reducing traffic on the system bus, which matters especially when several cores share one memory controller.
   - Reducing power consumption, since an on-chip SRAM access uses far less energy than an external DRAM access.
   - Holding the results of address translation in the TLB, which is itself a specialised cache.
   - Buffering writes, so the CPU need not wait for a slow memory write to complete.

   Where caches appear beyond the CPU: disk caches inside a drive or in the operating system, web browser caches, DNS caches, database buffer pools and content delivery networks all apply the same idea at different scales.

   Effect in numbers: with a hit time of 2 ns, a miss penalty of 100 ns and a hit ratio of 95 per cent, the average access time is 2 + (0.05 x 100) = 7 ns instead of 100 ns, so memory appears roughly fourteen times faster than it really is.
9. **Some of the factors determine the performance of a computer system. Cache memory is one of them. Why cache memory is one of the factors to determine the performance of a computer system?** *[BTRC Assistant Director (Technical) 2021 compact it 807 (ET: IBA)]*


   Answer: Cache memory determines the performance of a computer system because the processor can only run as fast as the data reaches it, and the cache is what decides how often the processor has to wait.

   Reasons:

   - It closes the memory wall. A modern CPU executes an instruction in a fraction of a nanosecond, while DRAM main memory needs 50 to 100 nanoseconds, which is one to two hundred processor cycles. Without a cache the processor would be idle for the great majority of its cycles regardless of how high its clock speed was.
   - It determines the average memory access time directly:
     AMAT = hit time + (miss ratio x miss penalty)
     A change in the hit ratio therefore changes the effective speed of the whole machine. Improving the hit ratio from 90 to 98 per cent, with a hit time of 2 ns and a miss penalty of 100 ns, reduces AMAT from 12 ns to 4 ns, that is a threefold improvement, with no change in clock speed at all.
   - It governs how many stall cycles the pipeline suffers. A cache miss empties the pipeline of useful work for a hundred cycles or more, so miss rate translates almost directly into lost instructions per cycle.
   - Its size and organisation set the working set that can be held. A program whose active data fits in the cache runs several times faster than the same program on a slightly larger data set that does not fit. This is why the same benchmark shows a sharp performance cliff as the data size crosses the cache size.
   - It reduces contention on the shared memory bus, which is a limiting factor in multi-core processors where several cores compete for one memory controller.
   - The number of levels matters: L1 for speed, L2 for capacity per core, L3 shared to avoid duplicate fetches and to allow cores to share data cheaply.
   - Its associativity and replacement policy determine the number of conflict misses.
   - It saves energy, and since modern processors are limited by thermal budget, energy saved is performance gained through higher sustained clocks.

   Practical evidence: two processors of the same generation and the same clock speed but with different cache sizes show clearly different performance, and server processors are given very large L3 caches for exactly this reason. Cache is therefore listed alongside clock speed, core count, instructions per cycle and memory bandwidth as one of the principal determinants of computer performance.
10. **Assume that for a certain processor, a read request takes 50 nanoseconds on a cache miss and 5 nanoseconds on a cache hit. Suppose while running a program, it was observed that 80% of the processor's read requests result in a cache hit. The average read access time in nanoseconds is ______.** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 864 (ET: BUET)]*


    Answer: Given:
    - Time on a cache hit = 5 nanoseconds
    - Time on a cache miss = 50 nanoseconds
    - Hit ratio = 80 per cent = 0.8
    - Miss ratio = 1 - 0.8 = 0.2

    Step 1 - write the formula for the average access time as a weighted average:
    - Average access time = (hit ratio x hit time) + (miss ratio x miss time)

    Step 2 - substitute the values:
    - = (0.8 x 5) + (0.2 x 50)

    Step 3 - compute each term:
    - 0.8 x 5 = 4
    - 0.2 x 50 = 10

    Step 4 - add:
    - Average access time = 4 + 10 = 14 nanoseconds

    Final answer: 14 nanoseconds.

    Note on the two common formulations: the question states that a miss takes 50 ns in total, so the simple weighted average above is correct. If instead the problem had said that a miss costs a penalty of 50 ns in addition to the hit time, the formula would be
    AMAT = hit time + (miss ratio x miss penalty) = 5 + (0.2 x 50) = 15 ns.
    The wording "takes 50 nanoseconds on a cache miss" means the total, so 14 ns is the answer here.

    Observation: raising the hit ratio from 80 to 95 per cent would give (0.95 x 5) + (0.05 x 50) = 4.75 + 2.5 = 7.25 ns, almost halving the access time. This shows how strongly the hit ratio governs system performance.
11. **Cache memory কী কাজে ব্যবহৃত হয়? Compiler and Interpreater -এর মধ্যে পার্থক্য লিখুন।** *[41th BCS 2021 compact it 880-881 (ET: N/A)]*


    Answer:

    ক্যাশে মেমোরির ব্যবহার:

    ক্যাশে মেমোরি হলো সিপিইউ ও প্রধান মেমোরির (RAM) মধ্যবর্তী একটি ছোট কিন্তু অত্যন্ত দ্রুতগতির স্মৃতি, যা SRAM প্রযুক্তিতে তৈরি। এর কাজ নিচে দেওয়া হলো।

    - সিপিইউ ও RAM এর গতির বিশাল ব্যবধান কমানো। সিপিইউ ন্যানোসেকেন্ডের ভগ্নাংশে কাজ করে, আর RAM এর অ্যাক্সেস সময় ৫০ থেকে ১০০ ন্যানোসেকেন্ড। ক্যাশে না থাকলে সিপিইউ-কে বেশির ভাগ সময় বসে থাকতে হতো।
    - সাম্প্রতিক ও ঘন ঘন ব্যবহৃত নির্দেশ ও তথ্যের অনুলিপি ধরে রাখা, যাতে পরের বার তা কয়েক ন্যানোসেকেন্ডেই পাওয়া যায়।
    - একটি ব্লক আনার সময় পার্শ্ববর্তী তথ্যও চলে আসায় ভবিষ্যতের অনুরোধ আগেই পূরণ হয়ে যায়।
    - মেমোরি বাসের ট্রাফিক কমানো, যা মাল্টি-কোর প্রসেসরে বিশেষভাবে গুরুত্বপূর্ণ।
    - বিদ্যুৎ খরচ কমানো, কারণ চিপের ভেতরের ছোট SRAM পড়তে বাইরের DRAM পড়ার চেয়ে অনেক কম শক্তি লাগে।
    - গড় মেমোরি অ্যাক্সেস সময় (AMAT) কমিয়ে সামগ্রিক কর্মদক্ষতা বাড়ানো।

    স্তরভেদ: L1 (ছোট ও দ্রুততম, প্রতিটি কোরে আলাদা), L2 (মাঝারি), L3 (সবচেয়ে বড়, সব কোরের মধ্যে ভাগাভাগি)।

    Compiler ও Interpreter এর মধ্যে পার্থক্য:

    | বিষয় | Compiler | Interpreter |
    |---|---|---|
    | অনুবাদ পদ্ধতি | সম্পূর্ণ সোর্স কোড একবারে অনুবাদ করে | এক লাইন করে অনুবাদ ও সম্পাদন করে |
    | আউটপুট | একটি স্বতন্ত্র অবজেক্ট বা এক্সিকিউটেবল ফাইল তৈরি করে | কোনো আলাদা ফাইল তৈরি করে না |
    | সম্পাদনের গতি | দ্রুত, কারণ অনুবাদ আগেই শেষ হয়ে যায় | ধীর, কারণ প্রতিবার চালানোর সময় অনুবাদ করতে হয় |
    | ত্রুটি নির্ণয় | সম্পূর্ণ প্রোগ্রাম স্ক্যান করে সব ত্রুটি একসঙ্গে দেখায় | প্রথম ত্রুটি পেলেই থেমে যায় ও সেটি দেখায় |
    | ডিবাগিং | তুলনামূলক কঠিন, কারণ ত্রুটির তালিকা দীর্ঘ হয় | সহজ, কারণ ত্রুটির অবস্থান তাৎক্ষণিকভাবে জানা যায় |
    | মেমোরি ব্যবহার | বেশি, কারণ অবজেক্ট কোড সংরক্ষণ করতে হয় | কম |
    | পুনরায় চালানো | একবার কম্পাইল করে বারবার চালানো যায় | প্রতিবারই নতুন করে অনুবাদ করতে হয় |
    | সোর্স কোডের প্রয়োজন | চালানোর সময় প্রয়োজন হয় না | প্রতিবার চালানোর সময় প্রয়োজন হয় |
    | প্ল্যাটফর্ম নির্ভরতা | অবজেক্ট কোড নির্দিষ্ট প্ল্যাটফর্মের জন্য | সোর্স কোড যেকোনো প্ল্যাটফর্মে চলে, যদি ইন্টারপ্রেটার থাকে |
    | উদাহরণ ভাষা | C, C++, Java (বাইটকোডে), Go, Rust | Python, JavaScript, PHP, Ruby, BASIC |

    উল্লেখযোগ্য: জাভা দুটোই ব্যবহার করে। জাভা কম্পাইলার সোর্স কোডকে বাইটকোডে অনুবাদ করে, আর জাভা ভার্চুয়াল মেশিন সেই বাইটকোড ইন্টারপ্রেট করে অথবা JIT (Just-In-Time) কম্পাইলারের মাধ্যমে মেশিন কোডে রূপান্তর করে চালায়।
12. **(ii) Cache Memory কী? Computer এর main memory-এর সাথে এর পার্থক্য কী?** *[BPSC Assistant Network Engineer 2020 compact it 951-952 (ET: N/A)], [BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019 (ET: N/A)]*


    Answer: ক্যাশে মেমোরি (Cache Memory) হলো সিপিইউ ও প্রধান মেমোরির মধ্যবর্তী একটি ছোট আকারের অত্যন্ত দ্রুতগতির স্মৃতি, যা SRAM প্রযুক্তিতে তৈরি। এতে সিপিইউ-এর সদ্য ব্যবহৃত ও ঘন ঘন ব্যবহৃত নির্দেশ ও তথ্যের অনুলিপি রাখা হয়, যাতে সিপিইউ-কে ধীরগতির RAM পর্যন্ত যেতে না হয়।

    কেন প্রয়োজন: সিপিইউ ন্যানোসেকেন্ডের ভগ্নাংশে কাজ করে, কিন্তু DRAM এর অ্যাক্সেস সময় ৫০ থেকে ১০০ ন্যানোসেকেন্ড। এই ব্যবধানকে বলা হয় "মেমোরি ওয়াল"। ক্যাশে এই ব্যবধান পূরণ করে।

    কাজের ভিত্তি — স্থানিকতার নীতি (locality of reference):
    - কালিক স্থানিকতা (temporal locality): যে তথ্য এইমাত্র ব্যবহৃত হয়েছে, তা শীঘ্রই আবার লাগার সম্ভাবনা বেশি।
    - স্থানিক স্থানিকতা (spatial locality): ব্যবহৃত তথ্যের পাশের তথ্যও শীঘ্রই লাগার সম্ভাবনা বেশি। তাই একটি বাইট নয়, পুরো ব্লক আনা হয়।

    স্তরভেদ: L1 (৩২-৬৪ কিলোবাইট, প্রতিটি কোরে আলাদা), L2 (২৫৬ কিলোবাইট থেকে ২ মেগাবাইট), L3 (৮ থেকে ৬৪ মেগাবাইট, সব কোরের মধ্যে ভাগাভাগি)।

    প্রধান মেমোরির সঙ্গে ক্যাশে মেমোরির পার্থক্য:

    | বিষয় | ক্যাশে মেমোরি | প্রধান মেমোরি (RAM) |
    |---|---|---|
    | প্রযুক্তি | SRAM, ফ্লিপ-ফ্লপ ভিত্তিক | DRAM, ক্যাপাসিটর ভিত্তিক |
    | গতি | অত্যন্ত দ্রুত, ১ থেকে ২০ ন্যানোসেকেন্ড | ধীর, ৫০ থেকে ১০০ ন্যানোসেকেন্ড |
    | ধারণক্ষমতা | খুব কম, কিলোবাইট থেকে কয়েক মেগাবাইট | অনেক বেশি, গিগাবাইট |
    | দাম (প্রতি বাইট) | অত্যন্ত বেশি | তুলনামূলক কম |
    | অবস্থান | সিপিইউ চিপের ভেতরে বা খুব কাছে | মাদারবোর্ডে আলাদা মডিউল হিসেবে |
    | রিফ্রেশ | প্রয়োজন হয় না | প্রতি কয়েক মিলিসেকেন্ডে প্রয়োজন |
    | পরিচালনা | হার্ডওয়্যার স্বয়ংক্রিয়ভাবে করে, প্রোগ্রামার জানেন না | অপারেটিং সিস্টেমের মেমোরি ম্যানেজার করে |
    | বিষয়বস্তু | প্রধান মেমোরির একটি অংশের অনুলিপি | চলমান প্রোগ্রাম ও তথ্যের মূল কপি |
    | ঠিকানাযোগ্যতা | প্রোগ্রাম সরাসরি ঠিকানা দিয়ে ডাকতে পারে না | প্রোগ্রাম সরাসরি ঠিকানা দিয়ে ডাকতে পারে |
    | বিদ্যুৎ খরচ | প্রতি বাইটে বেশি, কিন্তু অ্যাক্সেসে কম | প্রতি বাইটে কম |
    | অস্থিতিশীলতা | অস্থিতিশীল (volatile) | অস্থিতিশীল (volatile) |

    গড় অ্যাক্সেস সময়ের সূত্র: AMAT = হিট টাইম + (মিস রেশিও x মিস পেনাল্টি)। উদাহরণস্বরূপ হিট টাইম ২ ন্যানোসেকেন্ড, মিস পেনাল্টি ১০০ ন্যানোসেকেন্ড এবং হিট রেশিও ৯৫ শতাংশ হলে AMAT = ২ + (০.০৫ x ১০০) = ৭ ন্যানোসেকেন্ড, যেখানে ক্যাশে ছাড়া লাগত ১০০ ন্যানোসেকেন্ড।

## Secondary Storage (HDD vs SSD) (10)

1. Storage technology selection directly impacts banking operations. Server A will host the Core Banking Database. Server B will host 10 years of immutable archive data. Compare Hard Disk Drives (HDD) and Solid State Drives (SSD). *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*


   Answer: Comparison of HDD and SSD:

   | Point | HDD (Hard Disk Drive) | SSD (Solid State Drive) |
   |---|---|---|
   | Technology | Magnetic platters spinning at 5,400 to 15,000 rpm, with a read-write head on an actuator arm | NAND flash memory chips, no moving parts |
   | Sequential read and write | 80 to 160 MB/s | 550 MB/s for SATA, 3,000 to 7,000 MB/s for NVMe |
   | Random access (IOPS) | 100 to 200 IOPS | 50,000 to over 1,000,000 IOPS |
   | Access latency | 5 to 10 ms, because of seek time and rotational delay | About 0.1 ms, with no mechanical delay |
   | Cost per gigabyte | Low; the cheapest bulk storage | Several times higher |
   | Maximum capacity per drive | Very large, 20 TB and above | Large, but more expensive at the top end |
   | Durability and shock resistance | Poor; vibration or a drop can crash the head | Excellent; no moving parts |
   | Power consumption | Higher, 6 to 10 watts | Lower, 2 to 5 watts |
   | Heat and noise | Generates heat, audible | Silent, cooler |
   | Wear mechanism | Mechanical wear of bearings and head | Limited program-erase cycles per flash cell |
   | Data retention when unpowered | Many years | Good, but charge slowly leaks over years at high temperature |
   | Recovery after failure | Often partially recoverable by specialists | Usually unrecoverable once the controller or cells fail |

   Server A, hosting the Core Banking Database: SSD, specifically enterprise NVMe SSDs in RAID 10.

   Justification:
   - A core banking database is dominated by small random reads and writes: index lookups, row updates and transaction log writes. Random IOPS is therefore the decisive metric, and here an SSD is several thousand times faster than an HDD.
   - Transaction latency directly determines how many transactions per second the branch counters and the ATM network can sustain. Sub-millisecond latency is essential.
   - The transaction log must be written before a commit is acknowledged, so write latency is on the critical path of every single transaction.
   - Consistent performance under concurrent load matters, and an HDD degrades sharply when many users issue random requests at once, because the head must seek continuously.
   - Enterprise SSDs offer power-loss protection capacitors, which guarantee that data in the drive's write cache reaches the flash if power fails, a requirement for financial data integrity.
   - The higher cost per gigabyte is acceptable, because the active database is comparatively small and the cost of slow transactions is far greater.

   Server B, hosting ten years of immutable archive data: HDD, in RAID 6, with tape or object storage for the deepest tier.

   Justification:
   - Archive data is written once and read rarely, so high IOPS is not needed; the workload is sequential and latency-tolerant.
   - The volume is very large, so cost per gigabyte is the dominant factor, and HDDs are several times cheaper.
   - Very high capacities per drive are available, which keeps the number of drives, the rack space and the power bill down.
   - Long-term data retention on unpowered flash is a genuine concern, since charge leaks over years, whereas magnetic storage is stable.
   - Regulatory retention rules in banking require the data to be kept and to be provably intact, so RAID 6 plus an off-site copy and periodic integrity verification is the right design, and the drives need not be fast.

   Summary recommendation: use SSD where latency and IOPS determine business throughput, and HDD where capacity per taka determines cost. In practice a bank tiers its storage: NVMe SSD for the live database, SATA SSD or fast HDD for recent backups and reporting, and high-capacity HDD or tape for the long-term archive.
2. **a) Define the term "SSD". Briefly describe the working principle of "SSD".** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1342 (ET: N/A)]*


   Answer: An SSD (Solid State Drive) is a non-volatile storage device that stores data in NAND flash memory chips and has no moving parts, unlike a hard disk drive with its spinning platters and moving read-write head.

   Working principle:
   - The storage element is a floating-gate transistor. It is an ordinary MOSFET with a second, electrically isolated gate, the floating gate, placed between the control gate and the channel and surrounded by an insulating oxide layer.
   - Writing (programming): a high voltage is applied to the control gate, and electrons tunnel through the thin oxide onto the floating gate by Fowler-Nordheim tunnelling. Because the floating gate is completely insulated, the trapped charge remains there for years without power, which is what makes the memory non-volatile.
   - Reading: the trapped electrons alter the threshold voltage needed to turn the transistor on. The controller applies a reference voltage to the control gate and observes whether the transistor conducts, and from that it deduces the stored value.
   - Erasing: a high voltage is applied to the substrate, which pulls the electrons off the floating gate by the reverse tunnelling process. Erasing can only be done for a whole block at a time, not for individual cells, which is the fundamental constraint of flash memory.

   Organisation:
   - Cells are grouped into pages, typically 4 to 16 KB, which is the smallest unit that can be written.
   - Pages are grouped into blocks, typically 128 to 256 pages, which is the smallest unit that can be erased.
   - A page cannot be overwritten in place; the block must first be erased. This is why a controller is essential.

   The SSD controller performs several critical functions:
   - Wear levelling: each cell tolerates only a limited number of erase cycles, so the controller spreads writes evenly across all blocks instead of repeatedly using the same ones.
   - Garbage collection: it consolidates valid pages from partly used blocks so that whole blocks can be erased and reused.
   - The TRIM command: the operating system tells the drive which blocks the file system no longer needs, so they can be erased in advance rather than at the moment of the next write.
   - Error correction: ECC codes such as BCH or LDPC detect and correct bit errors, which become more frequent as the drive ages.
   - Over-provisioning: some capacity is reserved and hidden from the user, to keep spare blocks available.
   - Mapping: it maintains the flash translation layer, which maps logical block addresses used by the operating system to the physical pages that actually hold the data.

   Cell types, in order of density and against endurance:
   - SLC (Single Level Cell): 1 bit per cell, fastest and most durable, about 100,000 write cycles, most expensive.
   - MLC (Multi Level Cell): 2 bits per cell, about 10,000 cycles.
   - TLC (Triple Level Cell): 3 bits per cell, about 3,000 cycles, the common consumer type.
   - QLC (Quad Level Cell): 4 bits per cell, about 1,000 cycles, cheapest per gigabyte.
   - 3D NAND stacks cell layers vertically, which raises capacity without shrinking the cells further.

   Interfaces: SATA gives about 550 MB/s, while NVMe over PCIe gives 3,000 to 7,000 MB/s and much lower latency, because it removes the protocol overhead designed for rotating disks.
3. **Write two SSD characteristics?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*


   Answer: Two characteristics of an SSD:

   - No moving parts: an SSD stores data entirely in NAND flash memory chips, so there is no spinning platter and no moving read-write head. This makes it silent, shock resistant, cooler and far more reliable in portable and mobile use than a hard disk.
   - Very high speed and low latency: because there is no seek time or rotational delay, access latency is about 0.1 millisecond against 5 to 10 milliseconds for a hard disk, and the sequential transfer rate is 550 MB/s on SATA and 3,000 to 7,000 MB/s on NVMe. Random access performance, measured in IOPS, is several thousand times better than a hard disk.

   Other important characteristics:
   - Non-volatile: data is retained without power, because the electrons on the floating gate are trapped by an insulating oxide layer.
   - Limited write endurance: each flash cell tolerates only a limited number of program-erase cycles, from about 100,000 for SLC down to about 1,000 for QLC. The controller uses wear levelling to spread writes evenly and prolong life.
   - Erase-before-write constraint: a page cannot be overwritten in place; the whole block must be erased first, which is why the controller performs garbage collection and why the TRIM command exists.
   - Lower power consumption: 2 to 5 watts against 6 to 10 watts for a hard disk, which extends laptop battery life.
   - Higher cost per gigabyte than a hard disk, which is why hard disks remain the choice for bulk archival storage.
4. **How can you define SSD?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*


   Answer: An SSD, or Solid State Drive, is a non-volatile secondary storage device that stores data in NAND flash memory integrated circuits and contains no moving mechanical parts.

   Definition in detail:
   - "Solid state" means that the whole device is made of semiconductor components, with nothing that spins or moves, in contrast to a hard disk drive with its rotating platters and moving actuator arm.
   - Data is stored as electrical charge trapped on the floating gate of a transistor, and it remains there without power, which makes the storage non-volatile.
   - The drive presents itself to the operating system exactly as a hard disk does, through a SATA, NVMe, M.2 or USB interface, so no change to the file system or the software is needed.

   Key attributes:
   - Access latency of about 0.1 millisecond, against 5 to 10 milliseconds for a hard disk.
   - Sequential transfer of 550 MB/s on SATA and 3,000 to 7,000 MB/s on NVMe.
   - Silent, shock resistant, cool and low in power consumption.
   - Limited program-erase endurance per cell, managed by the controller through wear levelling.
   - Higher cost per gigabyte than a hard disk.

   Form factors: 2.5 inch SATA, M.2 (NVMe or SATA), U.2, and add-in PCIe cards for servers.
5. **(খ) Solid State Drives (SSD) এর কার্যপ্রণালী ও ব্যবহার লিখুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 704 (ET: N/A)]*


   Answer: SSD (Solid State Drive) হলো এমন একটি স্থায়ী সংরক্ষণ যন্ত্র, যা NAND ফ্ল্যাশ মেমোরি চিপে তথ্য সংরক্ষণ করে এবং যাতে কোনো ঘূর্ণায়মান বা চলমান যান্ত্রিক অংশ নেই।

   কার্যপ্রণালী:

   - মূল সংরক্ষণ একক ফ্লোটিং গেট ট্রানজিস্টর। এটি একটি সাধারণ MOSFET, যার কন্ট্রোল গেট ও চ্যানেলের মাঝে একটি অতিরিক্ত বিচ্ছিন্ন গেট থাকে, যা চারদিক থেকে অক্সাইড অন্তরক দিয়ে ঘেরা।
   - লেখা (Programming): কন্ট্রোল গেটে উচ্চ ভোল্টেজ প্রয়োগ করলে ইলেকট্রন সূক্ষ্ম অক্সাইড স্তর ভেদ করে ফ্লোটিং গেটে জমা হয় (Fowler-Nordheim টানেলিং)। গেটটি সম্পূর্ণ বিচ্ছিন্ন হওয়ায় বিদ্যুৎ বন্ধ হলেও ইলেকট্রন সেখানেই আটকে থাকে, তাই তথ্য স্থায়ী হয়।
   - পড়া (Reading): জমা ইলেকট্রন ট্রানজিস্টরের থ্রেশহোল্ড ভোল্টেজ পরিবর্তন করে। কন্ট্রোলার একটি নির্দিষ্ট রেফারেন্স ভোল্টেজ প্রয়োগ করে দেখে ট্রানজিস্টর পরিবাহী হলো কি না, তা থেকেই সংরক্ষিত মান নির্ণয় করে।
   - মোছা (Erasing): সাবস্ট্রেটে উচ্চ ভোল্টেজ দিয়ে ইলেকট্রনগুলোকে ফ্লোটিং গেট থেকে টেনে বের করা হয়। উল্লেখযোগ্য, মোছার কাজ একক কোষে নয়, পুরো ব্লকে করতে হয়।

   সাংগঠনিক কাঠামো:
   - কোষগুলো মিলে পেজ (সাধারণত ৪ থেকে ১৬ কিলোবাইট) তৈরি করে, যা লেখার ক্ষুদ্রতম একক।
   - পেজগুলো মিলে ব্লক (১২৮ থেকে ২৫৬ পেজ) তৈরি করে, যা মোছার ক্ষুদ্রতম একক।
   - কোনো পেজ সরাসরি ওভাররাইট করা যায় না; আগে পুরো ব্লক মুছতে হয়।

   কন্ট্রোলারের কাজ:
   - Wear levelling: প্রতিটি কোষের লেখার সীমা থাকায় কন্ট্রোলার সব ব্লকে সমানভাবে লেখা ছড়িয়ে দেয়, যাতে নির্দিষ্ট কিছু ব্লক আগে নষ্ট না হয়।
   - Garbage collection: আংশিক ব্যবহৃত ব্লক থেকে বৈধ পেজগুলো একত্র করে পুরো ব্লক মুছে ফেলার উপযোগী করে।
   - TRIM কমান্ড: অপারেটিং সিস্টেম জানায় কোন ব্লকগুলো আর প্রয়োজন নেই, যাতে সেগুলো আগেভাগেই মুছে রাখা যায়।
   - ত্রুটি সংশোধন (ECC) এবং লজিক্যাল থেকে ফিজিক্যাল ঠিকানা রূপান্তর (Flash Translation Layer)।

   কোষের প্রকারভেদ: SLC (প্রতি কোষে ১ বিট, দ্রুততম ও টেকসই), MLC (২ বিট), TLC (৩ বিট, সাধারণ ভোক্তা পর্যায়ে), QLC (৪ বিট, সবচেয়ে সস্তা কিন্তু কম টেকসই)। 3D NAND প্রযুক্তিতে কোষের স্তর উল্লম্বভাবে সাজিয়ে ধারণক্ষমতা বাড়ানো হয়।

   ব্যবহার:
   - অপারেটিং সিস্টেম ইনস্টল করা, যাতে বুট সময় ও অ্যাপ্লিকেশন চালু হওয়ার সময় কয়েক গুণ কমে যায়।
   - ডেটাবেজ সার্ভার ও লেনদেন প্রক্রিয়াকরণ, যেখানে র‍্যান্ডম অ্যাক্সেসের গতি নির্ণায়ক।
   - ল্যাপটপ ও আল্ট্রাবুক, কারণ এটি হালকা, কম বিদ্যুৎ খরচ করে ও ঝাঁকুনিতে নষ্ট হয় না।
   - ভিডিও সম্পাদনা, 3D রেন্ডারিং ও গেমিং, যেখানে বড় ফাইল দ্রুত পড়তে হয়।
   - সার্ভার ভার্চুয়ালাইজেশন ও ক্লাউড অবকাঠামো।
   - এমবেডেড ও শিল্প যন্ত্র, যেখানে কম্পন ও তাপমাত্রার সমস্যা থাকে।
   - ক্যাশে বা টায়ার্ড স্টোরেজে দ্রুত স্তর হিসেবে, যেখানে বাকি তথ্য হার্ড ডিস্কে থাকে।

   সীমাবদ্ধতা: প্রতি গিগাবাইটে দাম বেশি, লেখার চক্র সীমিত, এবং একবার নষ্ট হলে তথ্য উদ্ধার করা প্রায় অসম্ভব।
6. **In a solid state drive data is sarved to a pool of NAND flash. NAND itself is made up of what are called floating gate transmission. How does floating gate transmission store 0 and 1?** *[BTRC Assistant Director (Technical) 2021 compact it 808-809 (ET: IBA)]*


   Answer: A floating-gate transistor stores a 0 or a 1 as the presence or absence of trapped electrons on an electrically isolated gate.

   Structure:
   - It is an ordinary MOSFET with an extra gate added. From top to bottom the layers are: the control gate, an oxide insulating layer, the floating gate, a very thin tunnel oxide layer, and then the silicon channel between the source and the drain.
   - The floating gate is completely surrounded by insulating oxide, so any charge placed on it has nowhere to go. This is why the memory is non-volatile and holds data for years without power.

   Storing a 0 (programming):
   - A high positive voltage, about 12 to 20 volts, is applied to the control gate while the source and drain are held at a low voltage.
   - The strong electric field causes electrons from the channel to tunnel through the thin oxide onto the floating gate. This is Fowler-Nordheim tunnelling, and in some designs hot-carrier injection is used instead.
   - The trapped negative charge partly screens the control gate from the channel, so a higher voltage than normal is now needed to turn the transistor on. In other words the threshold voltage has been raised.
   - By convention a programmed cell, with electrons trapped, represents a logic 0.

   Storing a 1 (erased state):
   - A high positive voltage is applied to the substrate while the control gate is grounded, which pulls the electrons off the floating gate back into the channel.
   - With no trapped charge the threshold voltage is low, and the transistor turns on at the normal voltage.
   - An erased cell represents a logic 1. Note that erasing can only be done for a whole block at a time.

   Reading:
   - A reference voltage between the two threshold levels is applied to the control gate, and the sense amplifier checks whether current flows from source to drain.
   - Current flows: the threshold is low, so the cell is erased, and the value read is 1.
   - No current flows: the threshold is high, so electrons are trapped, and the value read is 0.
   - Reading uses a low voltage and does not disturb the stored charge.

   Summary table:

   | State | Electrons on floating gate | Threshold voltage | Conducts at read voltage | Logic value |
   |---|---|---|---|---|
   | Programmed | Present | High | No | 0 |
   | Erased | Absent | Low | Yes | 1 |

   Storing more than one bit per cell:
   - Instead of only two levels of trapped charge, several distinct levels are used, and each level is assigned a different bit pattern.
   - SLC uses 2 levels for 1 bit, MLC uses 4 levels for 2 bits, TLC uses 8 levels for 3 bits and QLC uses 16 levels for 4 bits.
   - Packing more levels into the same voltage window narrows the margin between them, which is why higher-density cells are slower, less durable and need stronger error correction.

   Wear mechanism: each program-erase cycle drives electrons through the thin tunnel oxide, which gradually damages it and traps charge in the oxide itself. After enough cycles the cell can no longer hold its charge reliably. This is why endurance is limited, from about 100,000 cycles for SLC down to about 1,000 for QLC, and why the controller performs wear levelling.
7. **Which of the following is the unit of Hard Disk Drive? (a) Megaharz (b) Kiloharz (c) Gigabyte (d) None** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*


   Answer: (c) Gigabyte

   Explanation:
   - The capacity of a hard disk drive is measured in units of digital storage: bytes, kilobytes, megabytes, gigabytes and terabytes. A modern drive is typically stated in gigabytes or terabytes.
   - The other options are units of frequency, not storage:
     - (a) Megahertz and (b) Kilohertz measure frequency, that is cycles per second. They are used for clock speed, radio frequency and signal bandwidth, not for storage capacity.
   - Storage units in order: 1 byte = 8 bits, 1 KB = 1,024 bytes, 1 MB = 1,024 KB, 1 GB = 1,024 MB, 1 TB = 1,024 GB, 1 PB = 1,024 TB.

   Point worth noting in an answer: drive manufacturers use decimal units, in which 1 GB means 1,000,000,000 bytes, while operating systems display binary units, in which 1 GiB means 1,073,741,824 bytes. This is why a drive sold as 500 GB appears in Windows as about 465 GB. No storage is actually missing; only the unit differs.

   Other quantities associated with a hard disk and their units:
   - Rotational speed: revolutions per minute (rpm), for example 5,400 or 7,200 rpm.
   - Data transfer rate: megabytes per second (MB/s).
   - Average seek time and latency: milliseconds (ms).
   - Cache or buffer size: megabytes (MB).
8. **Consider a magnetic disk consisting of 16 heads and 400 cylinders. This disk has four 100-cylinder zones with the cylinders in different zones containing 160, 200, 240. and 280 sectors, respectively. Assume that each sector contains 512 bytes, average seek time between adjacent cylinders is 1 msec, and the disk rotates at 7200 RPM. Calculate the (a) disk capacity (b) maximum data transfer rate.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*


   Answer: Given:
   - Number of heads (that is, recording surfaces) = 16
   - Number of cylinders = 400, divided into four zones of 100 cylinders each
   - Sectors per track: 160, 200, 240 and 280 in the four zones
   - Bytes per sector = 512
   - Rotational speed = 7,200 rpm
   - Average seek time between adjacent cylinders = 1 ms

   (a) Disk capacity

   Step 1 - find the total number of sectors on one surface, summing over the four zones:
   - Zone 1: 100 cylinders x 160 sectors = 16,000 sectors
   - Zone 2: 100 cylinders x 200 sectors = 20,000 sectors
   - Zone 3: 100 cylinders x 240 sectors = 24,000 sectors
   - Zone 4: 100 cylinders x 280 sectors = 28,000 sectors
   - Total per surface = 16,000 + 20,000 + 24,000 + 28,000 = 88,000 sectors

   Step 2 - multiply by the number of surfaces:
   - Total sectors on the disk = 88,000 x 16 = 1,408,000 sectors

   Step 3 - multiply by the bytes per sector:
   - Capacity = 1,408,000 x 512 bytes
   - = 720,896,000 bytes

   Step 4 - express in convenient units:
   - = 720.896 x 10^6 bytes, that is about 720.9 MB in decimal units
   - = 720,896,000 / 1,048,576 = 687.5 MiB in binary units

   Answer (a): the disk capacity is 720,896,000 bytes, that is about 720.9 MB (687.5 MiB).

   (b) Maximum data transfer rate

   The maximum rate is obtained from the zone with the most sectors per track, which is the outermost zone with 280 sectors, since one full rotation there passes the largest amount of data under the head.

   Step 1 - find the time for one rotation:
   - 7,200 revolutions per minute = 7,200 / 60 = 120 revolutions per second
   - Time for one rotation = 1 / 120 second = 8.33 milliseconds

   Step 2 - find the data on one track in the outermost zone:
   - 280 sectors x 512 bytes = 143,360 bytes per track

   Step 3 - compute the transfer rate:
   - Rate = data per track / time per rotation
   - = 143,360 bytes x 120 rotations per second
   - = 17,203,200 bytes per second

   Step 4 - express in convenient units:
   - = 17.2 MB per second in decimal units
   - = 16.4 MiB per second in binary units

   Answer (b): the maximum data transfer rate is 17,203,200 bytes per second, that is about 17.2 MB/s.

   Note: the minimum transfer rate, from the innermost zone with 160 sectors, would be 160 x 512 x 120 = 9,830,400 bytes per second, about 9.8 MB/s. This variation between the outer and inner tracks is exactly why zone bit recording is used: it packs more sectors on the physically longer outer tracks instead of wasting that space.
9. **Consider a disk pack with the following specifications- 16 surfaces, 128 tracks per surface, 256 sectors per track and 512 bytes per sector. Answer the following questions: (a) What is the capacity of disk pack? (b) If the format overhead is 32 bytes per sector, what is the formatted disk space? (c) If the disk is rotating at 3600 rpm, what is the data transfer rate?** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 924-925 (ET: CTI)]*


   Answer: Given:
   - Number of surfaces = 16
   - Tracks per surface = 128
   - Sectors per track = 256
   - Bytes per sector = 512
   - Rotational speed = 3,600 rpm

   (a) Capacity of the disk pack

   Step 1 - multiply the four quantities:
   - Capacity = surfaces x tracks per surface x sectors per track x bytes per sector
   - = 16 x 128 x 256 x 512

   Step 2 - compute step by step:
   - 16 x 128 = 2,048
   - 2,048 x 256 = 524,288
   - 524,288 x 512 = 268,435,456 bytes

   Step 3 - express in convenient units:
   - 268,435,456 / 1,048,576 = 256 MiB

   Answer (a): the capacity of the disk pack is 268,435,456 bytes, that is 256 MB.

   (b) Formatted disk space with 32 bytes of overhead per sector

   Step 1 - find the usable data per sector:
   - Usable bytes per sector = 512 - 32 = 480 bytes

   Step 2 - find the total number of sectors:
   - Total sectors = 16 x 128 x 256 = 524,288 sectors

   Step 3 - multiply:
   - Formatted capacity = 524,288 x 480
   - = 251,658,240 bytes

   Step 4 - express in convenient units:
   - 251,658,240 / 1,048,576 = 240 MiB

   Answer (b): the formatted disk space is 251,658,240 bytes, that is 240 MB. The overhead consumes 16 MB, which is 6.25 per cent of the raw capacity, and it is used for the sector header, the synchronisation field, the address mark and the error correcting code.

   (c) Data transfer rate at 3,600 rpm

   Step 1 - find the number of rotations per second:
   - 3,600 / 60 = 60 rotations per second
   - Time for one rotation = 1 / 60 second = 16.67 milliseconds

   Step 2 - find the data held on one track:
   - 256 sectors x 512 bytes = 131,072 bytes per track

   Step 3 - compute the transfer rate. In one rotation the head passes over one complete track:
   - Rate = 131,072 bytes x 60 rotations per second
   - = 7,864,320 bytes per second

   Step 4 - express in convenient units:
   - = 7.86 MB/s in decimal units
   - = 7.5 MiB/s in binary units

   Answer (c): the data transfer rate is 7,864,320 bytes per second, that is about 7.5 MB/s.

   Note: if the formatted capacity is used instead of the raw capacity, the useful data rate becomes 256 x 480 x 60 = 7,372,800 bytes per second, about 7.03 MB/s.
10. **(i) Optical disk কীভাবে data Read/Write করে বর্ণনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 951 (ET: N/A)], [BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019 (ET: N/A)]*


    Answer: অপটিক্যাল ডিস্ক (সিডি, ডিভিডি, ব্লু-রে) লেজার রশ্মির প্রতিফলনের সাহায্যে তথ্য পড়ে ও লেখে। ডিস্কের পৃষ্ঠে সর্পিলাকার একটি ট্র্যাক বরাবর অতি ক্ষুদ্র গর্ত ও সমতল অংশ তৈরি করে তথ্য সংরক্ষণ করা হয়।

    গঠন:
    - সবচেয়ে নিচে স্বচ্ছ পলিকার্বোনেট স্তর।
    - তার ওপরে প্রতিফলক অ্যালুমিনিয়াম বা রূপার স্তর।
    - তার ওপরে সুরক্ষামূলক ল্যাকার ও লেবেল।
    - তথ্য কেন্দ্র থেকে বাইরের দিকে একটি একক সর্পিল ট্র্যাকে সাজানো থাকে, হার্ড ডিস্কের মতো আলাদা আলাদা বৃত্তাকার ট্র্যাকে নয়।

    তথ্য পড়ার পদ্ধতি (Read):
    - ডিস্কের পৃষ্ঠে দুই ধরনের এলাকা থাকে: গর্ত (pit) এবং সমতল অংশ (land)।
    - লেজার ডায়োড থেকে নির্গত রশ্মি লেন্সের মাধ্যমে ডিস্কের পৃষ্ঠে ফোকাস করা হয়।
    - সমতল অংশ (land) থেকে রশ্মি প্রায় সম্পূর্ণ প্রতিফলিত হয়ে ফটোডিটেক্টরে পৌঁছায়, ফলে সবল সংকেত পাওয়া যায়।
    - গর্ত (pit) এর গভীরতা তরঙ্গদৈর্ঘ্যের প্রায় এক-চতুর্থাংশ রাখা হয়। ফলে গর্ত থেকে প্রতিফলিত রশ্মি ও পাশের সমতল থেকে প্রতিফলিত রশ্মির মধ্যে অর্ধ-তরঙ্গের পথপার্থক্য তৈরি হয় এবং ধ্বংসাত্মক ব্যতিচারের (destructive interference) কারণে প্রতিফলিত আলো দুর্বল হয়ে যায়।
    - ফটোডিটেক্টর এই আলোর তীব্রতার পরিবর্তনকে বৈদ্যুতিক সংকেতে রূপান্তর করে।
    - গুরুত্বপূর্ণ নিয়ম: গর্ত ও সমতলের সীমানায় যে পরিবর্তন ঘটে সেটিকে ১ ধরা হয়, আর পরিবর্তন না ঘটলে ০ ধরা হয়। অর্থাৎ গর্ত মানেই ০ এবং সমতল মানেই ১ নয়।

    তথ্য লেখার পদ্ধতি (Write):
    - উৎপাদিত (pressed) সিডি: ধাতব স্ট্যাম্পার দিয়ে পলিকার্বোনেটে গর্তগুলো ছাপ দিয়ে তৈরি করা হয়। এতে আর পরিবর্তন করা যায় না।
    - রেকর্ডেবল ডিস্ক (CD-R, DVD-R): প্রতিফলক স্তরের নিচে একটি জৈব রঞ্জক (organic dye) স্তর থাকে। উচ্চ ক্ষমতার লেজার নির্দিষ্ট বিন্দুতে রঞ্জককে পুড়িয়ে দেয়, ফলে সেখানে স্বচ্ছতা কমে যায় এবং কার্যত গর্তের মতো আচরণ করে। এই পরিবর্তন স্থায়ী, তাই একবারই লেখা যায়।
    - রি-রাইটেবল ডিস্ক (CD-RW, DVD-RW): রঞ্জকের বদলে একটি ফেজ-চেঞ্জ সংকর ধাতুর স্তর থাকে। উচ্চ তাপে গলিয়ে দ্রুত ঠান্ডা করলে স্তরটি অনিয়তাকার (amorphous) হয়ে যায় এবং কম প্রতিফলন করে; মাঝারি তাপে ধীরে ঠান্ডা করলে তা কেলাসিত (crystalline) হয় এবং বেশি প্রতিফলন করে। এই দুই অবস্থার পার্থক্যই ০ ও ১ নির্দেশ করে, এবং এটি প্রায় এক হাজার বার পর্যন্ত পরিবর্তন করা যায়।

    ধারণক্ষমতা ও লেজারের তরঙ্গদৈর্ঘ্য:

    | ডিস্ক | লেজারের তরঙ্গদৈর্ঘ্য | রং | ধারণক্ষমতা |
    |---|---|---|---|
    | CD | ৭৮০ ন্যানোমিটার | ইনফ্রারেড | ৭০০ মেগাবাইট |
    | DVD | ৬৫০ ন্যানোমিটার | লাল | ৪.৭ গিগাবাইট (এক স্তরে) |
    | Blu-ray | ৪০৫ ন্যানোমিটার | নীল-বেগুনি | ২৫ গিগাবাইট (এক স্তরে) |

    কারণ: তরঙ্গদৈর্ঘ্য যত কম, লেজার তত ছোট বিন্দুতে ফোকাস করা যায়, ফলে গর্তগুলো ছোট ও ঘন করে বসানো যায় এবং ধারণক্ষমতা বাড়ে।

    অন্যান্য বৈশিষ্ট্য:
    - ঘূর্ণন পদ্ধতি: সিডিতে সাধারণত ধ্রুব রৈখিক বেগ (CLV) ব্যবহৃত হয়, অর্থাৎ ভেতরের দিকে পড়ার সময় ডিস্ক দ্রুত ঘোরে এবং বাইরের দিকে ধীরে ঘোরে, যাতে ট্র্যাক বরাবর গতি সমান থাকে।
    - ত্রুটি সংশোধন: আঁচড় ও ধুলার প্রভাব সামলাতে Reed-Solomon কোড এবং ইন্টারলিভিং ব্যবহার করা হয়, যাতে একটি ছোট আঁচড়ে হারানো বিটগুলো পুনরুদ্ধার করা যায়।

## Multi-Core & Multi-Threading (5)

1. **Core vs thread in networking?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*


   Answer: The question uses the word "networking", but core and thread are terms of processor architecture, so the comparison is given in that sense.

   Core:
   - A core is a complete physical processing unit inside the CPU chip, with its own ALU, control unit, registers and usually its own L1 and L2 cache.
   - It is real hardware, so a quad-core processor genuinely contains four processing units and can execute four instruction streams in parallel.
   - Adding cores increases the true parallel processing capacity of the chip.

   Thread:
   - A thread is the smallest sequence of instructions that the operating system can schedule; it is a software concept.
   - A logical thread, in the hardware sense, is a virtual processing path presented by a core. With simultaneous multithreading (Intel calls it Hyper-Threading), one physical core presents itself as two logical processors.
   - Threads on the same core share that core's execution units and caches; only the register state and program counter are duplicated.

   | Point | Core | Thread |
   |---|---|---|
   | Nature | Physical hardware unit | Logical or virtual execution path, and in software a scheduled sequence of instructions |
   | Own execution units | Yes, its own ALU and registers | No; shares the core's ALU and caches |
   | True parallelism | Yes | Only apparent; two threads on one core interleave on shared units |
   | Performance gain | Large, close to linear with core count for parallel work | Modest, typically 15 to 30 per cent |
   | Cost in silicon | High | Very low, about 5 per cent extra die area |
   | Example | A 4-core processor has 4 physical cores | A 4-core processor with Hyper-Threading presents 8 logical threads |

   Meaning of a specification such as "4 cores, 8 threads": there are four physical cores, and each supports two hardware threads, so the operating system sees eight logical processors and can schedule eight tasks concurrently.

   Where networking touches this: a network server benefits from many cores and threads because each connection or request is usually handled by its own thread, so a server processor is designed with a high core and thread count to handle many simultaneous clients.
2. **Core i5 and i7 Microprocessor এর মধ্যে হার্ডওয়্যারগত মূল পার্থক্য কী?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 698 (ET: DPI)]*


   Answer: Core i5 ও Core i7 প্রসেসরের মধ্যে প্রধান হার্ডওয়্যারগত পার্থক্যসমূহ:

   | বিষয় | Core i5 | Core i7 |
   |---|---|---|
   | কোর সংখ্যা | কম | বেশি |
   | থ্রেড সংখ্যা | কম; হাইপার-থ্রেডিং সব মডেলে থাকে না | বেশি; সাধারণত হাইপার-থ্রেডিং থাকে |
   | L3 ক্যাশে | ছোট | বড়, ফলে মেমোরিতে যাওয়ার প্রয়োজন কম হয় |
   | বেস ক্লক ও টার্বো ক্লক | তুলনামূলক কম | বেশি |
   | টার্বো বুস্ট | আছে, তবে সীমিত | আছে, উচ্চতর ফ্রিকোয়েন্সি পর্যন্ত |
   | তাপ ও বিদ্যুৎ খরচ (TDP) | কম | বেশি |
   | সমন্বিত গ্রাফিক্স | মৌলিক পর্যায়ের | তুলনামূলক শক্তিশালী |
   | দাম | কম | বেশি |
   | উপযুক্ত ব্যবহার | সাধারণ অফিসের কাজ, মাঝারি গেমিং, ছবি সম্পাদনা | ভিডিও সম্পাদনা, 3D রেন্ডারিং, ভারী গেমিং, সফটওয়্যার ডেভেলপমেন্ট |

   সবচেয়ে গুরুত্বপূর্ণ তিনটি পার্থক্য:
   - কোর ও থ্রেডের সংখ্যা: এটিই সমান্তরাল কাজের ক্ষমতা নির্ধারণ করে। বেশি কোর মানে একসঙ্গে বেশি কাজ প্রকৃত অর্থে সমান্তরালে চলতে পারে।
   - ক্যাশে মেমোরির আকার: বড় L3 ক্যাশে থাকলে সিপিইউ-কে কম বার ধীরগতির RAM পর্যন্ত যেতে হয়, ফলে বড় ডেটাসেটে কর্মদক্ষতা অনেক বাড়ে।
   - ক্লক গতি ও টার্বো বুস্ট: একক থ্রেডের কাজে i7 এর উচ্চতর টার্বো ফ্রিকোয়েন্সি সরাসরি সুবিধা দেয়।

   গুরুত্বপূর্ণ সতর্কতা: i3, i5, i7 ও i9 কেবল একটি শ্রেণিবিন্যাস, নির্দিষ্ট কোনো স্পেসিফিকেশন নয়। প্রতিটি প্রজন্মে কোর সংখ্যা ও ক্যাশের আকার বদলায়, তাই তুলনা সবসময় একই প্রজন্মের মধ্যে করতে হয়। একটি নতুন প্রজন্মের i5 প্রায়ই পুরোনো প্রজন্মের i7 এর চেয়ে দ্রুত হয়। মডেল নম্বরের প্রথম সংখ্যাগুলো প্রজন্ম নির্দেশ করে; যেমন i5-13600K এর "13" মানে ত্রয়োদশ প্রজন্ম।
3. **What is Hyper threading? What is the use of it?** *[BOF Assistant Programmer 2022 compact it 733 (ET: MIST)]*


   Answer: Hyper-Threading is Intel's implementation of simultaneous multithreading (SMT). It makes a single physical core appear to the operating system as two logical processors, so that two threads can be scheduled on the same core at the same time.

   How it works:
   - The core duplicates only the small architectural state needed to hold a thread: the register set, the program counter, the instruction pointer and the interrupt controller state.
   - It does not duplicate the expensive execution resources: the ALUs, the floating-point units, the caches and the buses remain shared.
   - A modern core has many execution units, and a single thread rarely keeps all of them busy, because it stalls on cache misses, branch mispredictions and dependencies between instructions.
   - When one thread stalls, the core immediately issues instructions from the other thread instead of standing idle, so the unused execution slots are filled.

   Uses and benefits:
   - Better utilisation of the execution units, which raises throughput by roughly 15 to 30 per cent on multithreaded workloads.
   - More responsive multitasking, because more threads can be in flight at once.
   - Useful for servers, virtualisation, database engines, web servers, video encoding and compilation, all of which run many threads.
   - It costs only about 5 per cent extra die area, which is far cheaper than adding a whole physical core.

   Limitations:
   - It is not the same as doubling the cores. Two logical processors share one set of execution units, so the gain is well short of 100 per cent.
   - A single-threaded program gains nothing.
   - Two threads competing for the same cache can evict each other's data and actually slow things down.
   - It has been implicated in side-channel security vulnerabilities, which is why some secure environments disable it.
4. **Now a day, core i3, i5, i7 and i9 CPUs are aavailable. The higher the number is that means powerful processor. What is hyper threading? What does 2 core and 4 thread means?** *[BTRC Assistant Director (Technical) 2021 compact it 808 (ET: IBA)]*


   Answer: The naming i3, i5, i7 and i9 is a tier classification, and within one generation a higher number does indicate a more capable processor, generally with more cores, more threads, more cache and a higher turbo frequency. The comparison is only valid within the same generation, since a newer i5 often outperforms an older i7.

   Hyper-Threading is Intel's implementation of simultaneous multithreading (SMT). It makes a single physical core appear to the operating system as two logical processors, so that two threads can be scheduled on the same core at the same time.

   How it works:
   - The core duplicates only the small architectural state needed to hold a thread: the register set, the program counter, the instruction pointer and the interrupt controller state.
   - It does not duplicate the expensive execution resources: the ALUs, the floating-point units, the caches and the buses remain shared.
   - A modern core has many execution units, and a single thread rarely keeps all of them busy, because it stalls on cache misses, branch mispredictions and dependencies between instructions.
   - When one thread stalls, the core immediately issues instructions from the other thread instead of standing idle, so the unused execution slots are filled.

   Uses and benefits:
   - Better utilisation of the execution units, which raises throughput by roughly 15 to 30 per cent on multithreaded workloads.
   - More responsive multitasking, because more threads can be in flight at once.
   - Useful for servers, virtualisation, database engines, web servers, video encoding and compilation, all of which run many threads.
   - It costs only about 5 per cent extra die area, which is far cheaper than adding a whole physical core.

   Limitations:
   - It is not the same as doubling the cores. Two logical processors share one set of execution units, so the gain is well short of 100 per cent.
   - A single-threaded program gains nothing.
   - Two threads competing for the same cache can evict each other's data and actually slow things down.
   - It has been implicated in side-channel security vulnerabilities, which is why some secure environments disable it.

   Meaning of "2 cores and 4 threads":
   - There are 2 physical cores, that is two complete processing units, each with its own ALU, registers and L1 and L2 cache.
   - Each core supports two hardware threads through Hyper-Threading, so 2 x 2 = 4 logical processors.
   - The operating system's task manager therefore shows 4 CPUs and can schedule 4 tasks at once.
   - The performance is not that of 4 physical cores. Each pair of threads shares one core's execution units, so the realistic gain over 2 cores without Hyper-Threading is about 15 to 30 per cent on multithreaded work, not 100 per cent.

   Related configurations:
   - 4 cores, 4 threads: no Hyper-Threading.
   - 4 cores, 8 threads: Hyper-Threading enabled.
   - 8 cores, 16 threads: a typical mid-range modern desktop processor.
   - Recent Intel designs also mix performance cores and efficiency cores, where only the performance cores support two threads, which is why a chip may show, for example, 14 cores and 20 threads.
5. **১৩. Core i7 জেনারেশন এর প্রসেসর এর উদাহরণ লিখ?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 942 (ET: N/A)]*


   Answer: Core i7 প্রজন্ম অনুযায়ী প্রসেসরের কয়েকটি উদাহরণ:

   | প্রজন্ম | কোড নাম | উদাহরণ মডেল |
   |---|---|---|
   | ১ম | Nehalem / Lynnfield | Core i7-920, i7-870 |
   | ২য় | Sandy Bridge | Core i7-2600K, i7-2670QM |
   | ৩য় | Ivy Bridge | Core i7-3770K |
   | ৪র্থ | Haswell | Core i7-4790K |
   | ৫ম | Broadwell | Core i7-5775C |
   | ৬ষ্ঠ | Skylake | Core i7-6700K |
   | ৭ম | Kaby Lake | Core i7-7700K |
   | ৮ম | Coffee Lake | Core i7-8700K |
   | ৯ম | Coffee Lake Refresh | Core i7-9700K |
   | ১০ম | Comet Lake | Core i7-10700K |
   | ১১তম | Rocket Lake | Core i7-11700K |
   | ১২তম | Alder Lake | Core i7-12700K |
   | ১৩তম | Raptor Lake | Core i7-13700K |
   | ১৪তম | Raptor Lake Refresh | Core i7-14700K |

   মডেল নম্বর পড়ার নিয়ম, উদাহরণ Core i7-12700K:
   - i7 — প্রসেসরের শ্রেণি বা টিয়ার
   - 12 — প্রজন্ম (দ্বাদশ প্রজন্ম)
   - 700 — ওই প্রজন্মের মধ্যে মডেলের অবস্থান; সংখ্যা যত বড়, মডেল তত উচ্চতর
   - K — প্রত্যয়, যার অর্থ আনলকড, অর্থাৎ ওভারক্লক করা যায়

   প্রচলিত প্রত্যয়সমূহ:
   - K — আনলকড, ওভারক্লক করা যায়
   - F — সমন্বিত গ্রাফিক্স নেই, আলাদা গ্রাফিক্স কার্ড লাগবে
   - U — অতি কম বিদ্যুৎ খরচ, পাতলা ল্যাপটপের জন্য
   - H — উচ্চ কর্মক্ষমতার ল্যাপটপ প্রসেসর
   - T — কম বিদ্যুৎ খরচের ডেস্কটপ সংস্করণ
   - X — এক্সট্রিম সংস্করণ

   উল্লেখযোগ্য: প্রজন্ম বদলালে কোর সংখ্যা, ক্যাশের আকার ও স্থাপত্য বদলে যায়। যেমন চতুর্থ প্রজন্মের i7-4790K ছিল ৪ কোর ও ৮ থ্রেডের, আর দ্বাদশ প্রজন্মের i7-12700K এ রয়েছে ১২ কোর (৮টি পারফরম্যান্স ও ৪টি এফিসিয়েন্সি কোর) ও ২০ থ্রেড। তাই কেবল i7 নাম দেখে তুলনা করা ভুল; প্রজন্মও দেখতে হবে।

## Assembly Language & Addressing Modes (5)

1. (a) চয়ন করুন: (i) Propagation delay; (ii) Transmission delay;
   (b) SIMD instruction এর সংক্ষিপ্ত বর্ণনা লিখুন: MOV AX, A334H এবং MOV AX, [A334H] *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*


   Answer:

   (a) Propagation delay ও Transmission delay এর পার্থক্য:

   | বিষয় | Propagation Delay | Transmission Delay |
   |---|---|---|
   | সংজ্ঞা | একটি বিট উৎস থেকে গন্তব্যে পৌঁছাতে যে সময় লাগে | সম্পূর্ণ প্যাকেটের সব বিট লিংকে ঠেলে দিতে যে সময় লাগে |
   | সূত্র | দূরত্ব / সঞ্চালন গতি (d / s) | প্যাকেটের আকার / ব্যান্ডউইথ (L / R) |
   | কীসের উপর নির্ভর করে | লিংকের দৈর্ঘ্য ও মাধ্যমের প্রকৃতি | প্যাকেটের আকার ও লিংকের ব্যান্ডউইথ |
   | প্যাকেটের আকারের প্রভাব | নেই | সরাসরি সমানুপাতিক |
   | দূরত্বের প্রভাব | সরাসরি সমানুপাতিক | নেই |
   | কোথায় প্রধান | দূরপাল্লার লিংক, যেমন স্যাটেলাইট বা আন্তমহাদেশীয় ফাইবার | উচ্চগতির স্বল্প দূরত্বের লিংক, যেমন ল্যান |

   উদাহরণ: ১,০০০ কিলোমিটার ফাইবারে সঞ্চালন গতি ২ x ১০^৮ মিটার/সেকেন্ড হলে propagation delay = ১০^৬ / (২ x ১০^৮) = ৫ মিলিসেকেন্ড। ওই লিংকে ১০ Mbps হারে ১,০০০ বাইটের প্যাকেট পাঠাতে transmission delay = (১০০০ x ৮) / (১০ x ১০^৬) = ০.৮ মিলিসেকেন্ড।

   (b) MOV AX, A334H এবং MOV AX, [A334H] এর পার্থক্য:

   | বিষয় | MOV AX, A334H | MOV AX, [A334H] |
   |---|---|---|
   | অ্যাড্রেসিং মোড | Immediate addressing | Direct (memory) addressing |
   | অর্থ | A334H সংখ্যাটিকেই AX রেজিস্টারে বসাও | মেমোরির A334H ঠিকানায় যে মান আছে, তা AX রেজিস্টারে আনো |
   | বর্গাকার বন্ধনী | নেই, তাই মানটি ধ্রুবক | আছে, তাই মানটি ঠিকানা |
   | AX এর চূড়ান্ত মান | A334H | ওই ঠিকানার বিষয়বস্তু, যা যেকোনো মান হতে পারে |
   | মেমোরি অ্যাক্সেস | প্রয়োজন হয় না; মানটি নির্দেশের সঙ্গেই আসে | প্রয়োজন হয়; ডেটা সেগমেন্ট থেকে দুই বাইট পড়তে হয় |
   | সম্পাদনের গতি | দ্রুত | ধীর, কারণ অতিরিক্ত মেমোরি চক্র লাগে |
   | ডিফল্ট সেগমেন্ট | প্রযোজ্য নয় | DS (ডেটা সেগমেন্ট) |

   উদাহরণ দিয়ে ব্যাখ্যা: ধরা যাক মেমোরির A334H ঠিকানায় 1234H সংরক্ষিত আছে।
   - MOV AX, A334H সম্পাদনের পর AX = A334H
   - MOV AX, [A334H] সম্পাদনের পর AX = 1234H

   অর্থাৎ বর্গাকার বন্ধনী থাকলে সেটি ঠিকানা বোঝায়, না থাকলে সরাসরি মান বোঝায়। এটিই immediate ও direct অ্যাড্রেসিং মোডের মৌলিক পার্থক্য।

   SIMD সম্পর্কে সংক্ষিপ্ত টীকা: SIMD এর পূর্ণরূপ Single Instruction, Multiple Data। এতে একটি নির্দেশ একসঙ্গে একাধিক ডেটা উপাদানের ওপর একই কাজ সম্পাদন করে। যেমন একটি SIMD যোগ নির্দেশ চার জোড়া সংখ্যাকে একই সঙ্গে যোগ করতে পারে। ইন্টেলের MMX, SSE ও AVX এবং ARM এর NEON হলো SIMD নির্দেশ সেট। এগুলো মাল্টিমিডিয়া, ছবি প্রক্রিয়াকরণ, বৈজ্ঞানিক গণনা ও যন্ত্র শিখনে গতি বহুগুণ বাড়ায়। উল্লেখ্য, প্রশ্নে দেওয়া MOV নির্দেশ দুটি SIMD নয়, বরং সাধারণ অ্যাড্রেসিং মোডের উদাহরণ।
2. **Explain the difference between direct, immediate, and register addressing modes in the 8086 microprocessor.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1424 (ET: E-Zone)]*


   Answer: An addressing mode specifies how the operand of an instruction is to be located. Three of the modes of the 8086 are compared below.

   Immediate addressing mode:
   - The operand is a constant supplied as part of the instruction itself, so it is stored in the code segment along with the opcode.
   - No memory access and no register read is needed to obtain it.
   - Example: MOV AX, 1234H places the constant 1234H into AX.
   - It is the fastest mode, since the value travels with the instruction.
   - It can only be a source operand, never a destination, and its size must match the destination register.

   Register addressing mode:
   - The operand is held in one of the processor's own registers.
   - No memory access is required at all, so it is very fast, second only to immediate.
   - Example: MOV AX, BX copies the contents of BX into AX.
   - The instruction is short, because only a few bits are needed to name the register.
   - It is the mode used most heavily in optimised code, which is why compilers work hard to keep values in registers.

   Direct addressing mode:
   - The instruction contains the 16-bit offset of the memory location that holds the operand, written in square brackets.
   - The physical address is formed as (DS x 16) + offset, using the data segment register by default.
   - Example: MOV AX, [1234H] fetches the two bytes stored at offset 1234H in the data segment and loads them into AX.
   - It is slower than the other two, because an extra memory read cycle is needed.

   | Point | Immediate | Register | Direct |
   |---|---|---|---|
   | Where the operand is | Inside the instruction | In a CPU register | In main memory |
   | Memory access needed | No | No | Yes, one extra cycle |
   | Speed | Fastest | Very fast | Slowest of the three |
   | Instruction length | Longer, carries the constant | Shortest | Longer, carries the address |
   | Syntax example | MOV AX, 1234H | MOV AX, BX | MOV AX, [1234H] |
   | Flexibility | Value fixed at assembly time | Limited by the number of registers | Any memory location, fixed at assembly time |
   | Can be a destination | No | Yes | Yes |

   The critical distinction to remember: the square brackets. MOV AX, 1234H loads the number 1234H, while MOV AX, [1234H] loads whatever value is stored at address 1234H. Omitting or adding brackets by mistake is one of the most common errors in assembly programming.

   Other addressing modes of the 8086, for completeness: register indirect (MOV AX, [BX]), based (MOV AX, [BX+4]), indexed (MOV AX, [SI+4]), based-indexed (MOV AX, [BX+SI]), based-indexed with displacement (MOV AX, [BX+SI+4]), and the implied and relative modes used by string and jump instructions.
3. **(খ) নিচের instruction দুটির মাঝে পার্থক্য লিখুন:** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*
MOV AX, A534H এবং MOV AX, [A534H]


   Answer: MOV AX, A534H এবং MOV AX, [A534H] নির্দেশ দুটির পার্থক্য:

   | বিষয় | MOV AX, A534H | MOV AX, [A534H] |
   |---|---|---|
   | অ্যাড্রেসিং মোড | Immediate addressing (তাৎক্ষণিক) | Direct addressing (প্রত্যক্ষ বা মেমোরি) |
   | অর্থ | A534H সংখ্যাটিকে সরাসরি AX রেজিস্টারে বসানো হয় | মেমোরির A534H অফসেটে সংরক্ষিত মানটি AX রেজিস্টারে আনা হয় |
   | বর্গাকার বন্ধনী | নেই, তাই এটি একটি ধ্রুব মান | আছে, তাই এটি একটি ঠিকানা |
   | অপারেন্ড কোথায় থাকে | নির্দেশের ভেতরেই, কোড সেগমেন্টে | মেমোরিতে, ডেটা সেগমেন্টে |
   | মেমোরি অ্যাক্সেস | প্রয়োজন নেই | প্রয়োজন; দুই বাইট পড়তে হয় |
   | সম্পাদনের গতি | দ্রুত | ধীর, অতিরিক্ত মেমোরি চক্রের কারণে |
   | ভৌত ঠিকানা গণনা | প্রযোজ্য নয় | (DS x 16) + A534H |
   | AX এর ফলাফল | সর্বদা A534H | ওই ঠিকানার বিষয়বস্তু, যা যেকোনো মান হতে পারে |

   উদাহরণ দিয়ে ব্যাখ্যা:
   - ধরা যাক DS = 2000H এবং মেমোরির ভৌত ঠিকানা (2000H x 16) + A534H = 2A534H এ 7BC9H মানটি সংরক্ষিত আছে।
   - MOV AX, A534H সম্পাদনের পর AX = A534H
   - MOV AX, [A534H] সম্পাদনের পর AX = 7BC9H

   মূল কথা: বর্গাকার বন্ধনী থাকলে ভেতরের সংখ্যাটি ঠিকানা হিসেবে গণ্য হয় এবং ওই ঠিকানার বিষয়বস্তু আনা হয়; বন্ধনী না থাকলে সংখ্যাটি নিজেই অপারেন্ড। অ্যাসেম্বলি ভাষায় এই পার্থক্য ভুল করা সবচেয়ে সাধারণ ভুলগুলোর একটি।

   বাইট বনাম শব্দ: AX ১৬ বিটের রেজিস্টার, তাই [A534H] থেকে পরপর দুই বাইট আনা হয়। নিম্ন বাইট যায় AL এ এবং উচ্চ বাইট যায় AH এ, কারণ ইন্টেল প্রসেসর লিটল-এন্ডিয়ান পদ্ধতি অনুসরণ করে।
4. **(b) Explain the operations of the following instructions: (i) ADC (ii) CMP (iii) JBE** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 691 (ET: N/A)]*


   Answer:

   (i) ADC — Add with Carry:
   - Syntax: ADC destination, source
   - Operation: destination = destination + source + CF, where CF is the current value of the carry flag.
   - It differs from ADD in that it also adds in the carry produced by the previous addition.
   - Purpose: it makes multi-byte or multi-word addition possible. A 16-bit processor can add two 32-bit numbers by adding the low words with ADD and the high words with ADC, so that the carry out of the low half is carried into the high half.
   - Example:
     - ADD AX, BX    ; add the low words; a carry out sets CF
     - ADC DX, CX    ; add the high words together with that carry
   - Flags affected: CF, PF, AF, ZF, SF and OF are all updated by the result.

   (ii) CMP — Compare:
   - Syntax: CMP destination, source
   - Operation: it performs destination minus source, exactly as SUB does, but it discards the result and keeps only the flags. The destination operand is therefore unchanged.
   - Purpose: it sets the flags so that a conditional jump can test the relationship between the two operands. It is almost always followed immediately by a conditional jump.
   - Interpretation of the flags after CMP A, B:
     - ZF = 1 means A equals B
     - ZF = 0 and CF = 0 means A is greater than B (for unsigned numbers)
     - CF = 1 means A is less than B (for unsigned numbers)
     - For signed numbers the comparison uses SF and OF instead of CF
   - Example:
     - CMP AX, BX
     - JE  EQUAL      ; jump if AX equals BX
     - JA  GREATER    ; jump if AX is above BX, unsigned
   - Flags affected: CF, PF, AF, ZF, SF and OF.

   (iii) JBE — Jump if Below or Equal:
   - Syntax: JBE label
   - Operation: the jump is taken if CF = 1 or ZF = 1.
   - Meaning: it is used after a comparison of unsigned numbers, and it transfers control when the first operand is less than or equal to the second.
   - Its synonym is JNA (Jump if Not Above); both assemble to the same opcode.
   - Example:
     - CMP AX, 100
     - JBE SMALL      ; jump to SMALL if AX is less than or equal to 100, unsigned
   - Flags affected: none. A conditional jump reads the flags but does not change them.
   - Important distinction: JBE is for unsigned comparison. The signed equivalent is JLE (Jump if Less or Equal), which tests ZF = 1 or SF is not equal to OF. Using the wrong one is a common source of bugs when negative numbers are involved.
5. **Assembly Language Instructions এর ক্ষেত্রে নিম্মোক্ত Instructions গুলোর কাজ লিখুন। ADC, XCHG, POP ও JNZ.** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1041 (ET: DPI)]*


   Answer:

   ADC — Add with Carry:
   - গঠন: ADC গন্তব্য, উৎস
   - কাজ: গন্তব্য = গন্তব্য + উৎস + CF, অর্থাৎ দুইটি অপারেন্ডের সঙ্গে ক্যারি ফ্ল্যাগের মানও যোগ করা হয়।
   - ADD থেকে পার্থক্য: ADD ক্যারি যোগ করে না, ADC করে।
   - প্রয়োজনীয়তা: প্রসেসরের শব্দদৈর্ঘ্যের চেয়ে বড় সংখ্যা যোগ করতে। যেমন ১৬ বিট প্রসেসরে দুইটি ৩২ বিট সংখ্যা যোগ করতে নিম্ন অংশ ADD দিয়ে এবং উচ্চ অংশ ADC দিয়ে যোগ করতে হয়।
   - উদাহরণ: ADD AX, BX এরপর ADC DX, CX
   - প্রভাবিত ফ্ল্যাগ: CF, PF, AF, ZF, SF, OF

   XCHG — Exchange:
   - গঠন: XCHG অপারেন্ড১, অপারেন্ড২
   - কাজ: দুইটি অপারেন্ডের বিষয়বস্তু পরস্পর বিনিময় করে।
   - বিশেষত্ব: কোনো অস্থায়ী রেজিস্টার বা ভেরিয়েবল ছাড়াই একটি নির্দেশে বিনিময় সম্পন্ন হয়, যা সাজানো (sorting) অ্যালগরিদমে অত্যন্ত কার্যকর।
   - উদাহরণ: XCHG AX, BX সম্পাদনের পর AX এ আগের BX এর মান এবং BX এ আগের AX এর মান থাকে।
   - সীমাবদ্ধতা: দুইটি মেমোরি অবস্থানের মধ্যে সরাসরি XCHG করা যায় না; অন্তত একটি অপারেন্ড রেজিস্টার হতে হবে।
   - প্রভাবিত ফ্ল্যাগ: কোনোটিই নয়।

   POP — Pop from Stack:
   - গঠন: POP গন্তব্য
   - কাজ: স্ট্যাকের শীর্ষ থেকে দুই বাইট (একটি শব্দ) নিয়ে গন্তব্যে বসায় এবং স্ট্যাক পয়েন্টার SP এর মান ২ বাড়িয়ে দেয়।
   - কার্যধারা: গন্তব্য = [SS:SP], তারপর SP = SP + 2
   - PUSH এর বিপরীত কাজ। PUSH আগে SP কমিয়ে তারপর লেখে, POP আগে পড়ে তারপর SP বাড়ায়।
   - ব্যবহার: সাবরুটিন থেকে ফেরার সময় সংরক্ষিত রেজিস্টার পুনরুদ্ধার করা, প্যারামিটার গ্রহণ করা এবং ইন্টারাপ্টের পর প্রসঙ্গ ফিরিয়ে আনা।
   - উল্লেখ্য: ৮০৮৬ এর স্ট্যাক নিচের দিকে বাড়ে, অর্থাৎ PUSH করলে SP কমে।
   - প্রভাবিত ফ্ল্যাগ: কোনোটিই নয়, তবে POPF নির্দেশ ফ্ল্যাগ রেজিস্টার পুনরুদ্ধার করে।

   JNZ — Jump if Not Zero:
   - গঠন: JNZ লেবেল
   - কাজ: জিরো ফ্ল্যাগ ZF = 0 হলে নির্দিষ্ট লেবেলে লাফ দেয়; ZF = 1 হলে পরবর্তী নির্দেশে যায়।
   - সমার্থক নির্দেশ: JNE (Jump if Not Equal); দুটির অপকোড একই।
   - ব্যবহার: লুপ তৈরি করা এবং তুলনার পর শর্তসাপেক্ষ শাখা তৈরি করা।
   - উদাহরণ:
     - MOV CX, 5
     - LOOP1: DEC CX
     - JNZ LOOP1      ; CX শূন্য না হওয়া পর্যন্ত পুনরাবৃত্তি
   - প্রভাবিত ফ্ল্যাগ: কোনোটিই নয়; এটি কেবল ফ্ল্যাগ পড়ে।

## Instruction Pipelining & Hazards (5)

1. Why do modern processor designs favor a multi-stage pipelined approach over a single-cycle implementation? [SO IT 25-07-2026]

2. **Write down the names of different stages of instruction pipelining in a multi-cycle datapath architecture. What is a data-hazard in a pipelined datapath?** *[BPSC (Ministry) Network/Website Manager (CSE) 21.05.2025 compact it 1340 (ET: N/A)]*

3. **(c) Fill in the gaps RISC or CISC:** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 416 (ET: BUET)]*
   * (i) Pipelining is less efficient due to instruction complexity and variability ______
   * (ii) Emphasis on hardware simplicity and efficiency ______
   * (iii) Complex decoding due to variable instruction length ______
   * (iv) Each instruction typically executes in a single clock cycle ______

4. **Difference between mutliprocessor system and multi computer system, Explain Shared memory; discuss the two schemes to maintain cache coherence. What is pipelining? Explain the 4 stages of the pipeline.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 299 (ET: BIBM)]*

5. **6.1 Why do modern processor designs favor a multi-stage pipelined approach over a single-cycle implementation?** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

## CPU Performance & Instruction Cycle (4)

1. **There was a CPU cycle math** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 400 (ET: BUET)]*

2. **(খ) Clock cycle কী? একটি মাইক্রো-প্রসেসরের speed 3.5 GHz বলতে কী বোঝায়?** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

3. **A program (or a program task) takes 1 billion instructions to execute on a processor running at 2 GHz. Suppose also that 50% of the instructions execute in 3 clock cycles, 30% execute in 4 clock cycles, and 20% execute in 5 clock cycles. What is the execution time for the program or task?** *[RAKUB Programmer (PO) 12.10.2021 compact it 847 (ET: N/A)]*

4. **Operating system math: clock frequency 700MHz.** *[RAKUB Programmer (PO) 12.10.2021 compact it 852 (ET: N/A)]*

## 8085 Microprocessor & Edge Computing (3)

1. (a) Edge Computing এর ধারণা সংক্ষেপে ব্যাখ্যা করুন।
   (b) 8085 মাইক্রোপ্রসেসর কী? রেজিস্টারের ইফেক্টিভ মেমোরি অ্যাড্রেসিং কার্যকারিতা ব্যাখ্যা করুন। *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

2. **Intel 8085 ও Intel 8086 Microprocessor-এর সর্বোচ্চ ফিজিক্যাল মেমোরি ক্যাপাসিটি কত এবং কেন?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 697 (ET: DPI)]*

3. **What is the difference between 8-bit (8085) and 16-bit (8086) microprocessor?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 865-866 (ET: BUET)]*

## RISC vs CISC Architecture (2)

1. **RISC stand for __________? Write two characteristics of it's?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

2. **Difference between RISC and CISC.** *[NPCBL Executive Trainee (IT) 2022 compact it 644 (ET: BUET)]*
