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

2. **Difference between SRAM & DRAM also write Differences Cache Memory vs Flash Memory.** *[BUET Assistant Programmer 21.06.2025 compact it 1434 (ET: BUET)]*

3. **DRAM stands for __________?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

4. **What is stand for EEPROM?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

5. **কম্পিউটার স্মৃতি বলতে কী বোঝায়? কম্পিউটারের স্মৃতির শ্রেণিবিভাগ আলোচনা করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 405 (ET: N/A)]*

6. **Write down the difference between RAM and ROM.** *[DESCO Sub-Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)], [DMLC Assistant Teacher (ICT) 2021 compact it 826 (ET: N/A)]*

7. **Differentiate among CPU register, Cache memory, Main memory and Secondary memory.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 510 (ET: MIST)]*

8. **What do you mean by memory organization? Write the different between SRAM and DRAM.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 558 (ET: BIBM)]*

9. **What is dual channel RAM? Difference between single In-Line and Dual In-Line Memory Module.** *[BITAC Assistant Programmer 27.10.2023 compact it 559 (ET: BUTEX)]*

10. **What is the difference between Dynamic RAM and Static RAM?** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 642 (ET: BUET)]*

11. **Give classification of memory. Differentiate between RAM and ROM.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 664 (ET: N/A)]*

12. **(গ) Primary Memory and Secondary Memory এর উদাহরণসহ তুলনামূলক আলোচনা করুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 705 (ET: N/A)]*

13. **Write down the difference between SRAM and DRAM.** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 718 (ET: N/A)]*

14. **(ক) Data transfer rate এর ভিত্তিতে নিম্নোক্ত memory/storage device গুলোকে বেশী থেকে কম ক্রমানুসারে সাজান। (i) Flash drive (ii) SSD (iii) Cache memory (iv) DVD (v) RAM (vi) Magnetic HD** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 767 (ET: N/A)]*

15. **Which of the following is non volatile memory? (a) SRAM (b) DRAM (c) ROM (d) HDD** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

16. **(b) Here are given 4 types of different memory. Which memory is the faster? Write in sequence order in the following figure: Register, Hard disk, Cache, RAM.** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 821 (ET: BUET)]*

17. **RAM and ROM difference লিখ?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 944 (ET: N/A)]*

18. **(a) Write the difference between: (i) RAM and ROM (ii) Open source software and Proproetary software.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1023-1024 (ET: N/A)]*

19. **(b) Outline the functions performed by memory. List some factors upon which memory can be classified.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1024 (ET: N/A)]*

20. **(c) Given below the list of some memory devices. Identify which are semi-conductor, optical and magnetic memory. CD, RAM, Floppy Disk, Hard Disk, ROM, DVD.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1024 (ET: N/A)]*

21. **How Maximum size of memory (RAM) is needed that can be addressed by 32-bit system.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1031 (ET: BUET)]*

## RAID Architecture & Storage (13)

1. **Which RAID level is best and why?** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 319 (ET: N/A)], [BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

2. **Striping with parity is done in which level of RAID.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*

3. **Concept of RAID, Relevance in Database, Uses in Database, is it possible?** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 319 (ET: N/A)]*

4. **How to solve drive failure in RAID?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1454 (ET: BUET)]*

5. **Explain the purpose of RAID.** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 564 (ET: N/A)]*

6. **What do you mean by RAID? Write the difference types of RAID level.** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 595 (ET: N/A)]*

7. **What is RAID technology? Why it's important Server in data center?** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 555 (ET: BIBM)]*

8. **(a) Compare RAID 1 and RAID 5 levels. Which one you prefer? Why?** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 691 (ET: N/A)]*

9. **What is RAID?** *[BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*

10. **What is RAID? What is the classification of RAIDs? Difference between RAID 1 and RAID 5 using illustration.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 755 (ET: N/A)]*

11. **What is RAID technology? Describe about the advantages of RAID technology.** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 820 (ET: BUET)]*

12. **Why necessary to use RAID? If you choose a RAID level for an organization with huge data process. Justify your answer?** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 854 (ET: N/A)]*

13. **Your office need some storage device. Highest capacity 500GB. Two system backup of 30GB. Using RAID 1, Explain how many storage devices will need?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*

## Cache Memory (12)

1. Explain the difference between a "Compulsory Miss" (Cold Miss) and a "Capacity Miss" in cache memory. [SO IT 25-07-2026]

2. **(d) What is cache memory? Explain the concepts of (i) Cache hit and (ii) Cache miss.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1352 (ET: N/A)]*

3. **Write advantage and disadvantage of direct mapping and associative mapping between cache memory and main memory.** *[BCIC Assistant Programmer 14.02.2025 compact it 1330 (ET: BUET)]*

4. **How many total bits are required for a direct mapped cache with 16KB of data and 4-word blocks? Assuming a 32 bit address?** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 421 (ET: BIBM)]*

5. **6.3 Explain the difference between a "Compulsory Miss" (Cold Miss) and a "Capacity Miss" in cache memory.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

6. **Write Concept of cache memory in computer. How its change performance of computer?** *[BITAC Assistant Programmer 27.10.2023 compact it 559 (ET: BUTEX)]*

7. **Suppose we have a 16 KB of data in a direct mapped cache with 4 word blocks. Determine the size of the tag, index and offset fields if we are using a 32-bit architecture.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 439 (ET: BIBM)]*

8. **What is the use of cache memory?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*

9. **Some of the factors determine the performance of a computer system. Cache memory is one of them. Why cache memory is one of the factors to determine the performance of a computer system?** *[BTRC Assistant Director (Technical) 2021 compact it 807 (ET: IBA)]*

10. **Assume that for a certain processor, a read request takes 50 nanoseconds on a cache miss and 5 nanoseconds on a cache hit. Suppose while running a program, it was observed that 80% of the processor's read requests result in a cache hit. The average read access time in nanoseconds is ______.** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 864 (ET: BUET)]*

11. **Cache memory কী কাজে ব্যবহৃত হয়? Compiler and Interpreater -এর মধ্যে পার্থক্য লিখুন।** *[41th BCS 2021 compact it 880-881 (ET: N/A)]*

12. **(ii) Cache Memory কী? Computer এর main memory-এর সাথে এর পার্থক্য কী?** *[BPSC Assistant Network Engineer 2020 compact it 951-952 (ET: N/A)], [BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019 (ET: N/A)]*

## Secondary Storage (HDD vs SSD) (10)

1. Storage technology selection directly impacts banking operations. Server A will host the Core Banking Database. Server B will host 10 years of immutable archive data. Compare Hard Disk Drives (HDD) and Solid State Drives (SSD). *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

2. **a) Define the term "SSD". Briefly describe the working principle of "SSD".** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1342 (ET: N/A)]*

3. **Write two SSD characteristics?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

4. **How can you define SSD?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*

5. **(খ) Solid State Drives (SSD) এর কার্যপ্রণালী ও ব্যবহার লিখুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 704 (ET: N/A)]*

6. **In a solid state drive data is sarved to a pool of NAND flash. NAND itself is made up of what are called floating gate transmission. How does floating gate transmission store 0 and 1?** *[BTRC Assistant Director (Technical) 2021 compact it 808-809 (ET: IBA)]*

7. **Which of the following is the unit of Hard Disk Drive? (a) Megaharz (b) Kiloharz (c) Gigabyte (d) None** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

8. **Consider a magnetic disk consisting of 16 heads and 400 cylinders. This disk has four 100-cylinder zones with the cylinders in different zones containing 160, 200, 240. and 280 sectors, respectively. Assume that each sector contains 512 bytes, average seek time between adjacent cylinders is 1 msec, and the disk rotates at 7200 RPM. Calculate the (a) disk capacity (b) maximum data transfer rate.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*

9. **Consider a disk pack with the following specifications- 16 surfaces, 128 tracks per surface, 256 sectors per track and 512 bytes per sector. Answer the following questions: (a) What is the capacity of disk pack? (b) If the format overhead is 32 bytes per sector, what is the formatted disk space? (c) If the disk is rotating at 3600 rpm, what is the data transfer rate?** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 924-925 (ET: CTI)]*

10. **(i) Optical disk কীভাবে data Read/Write করে বর্ণনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 951 (ET: N/A)], [BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019 (ET: N/A)]*

## Multi-Core & Multi-Threading (5)

1. **Core vs thread in networking?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

2. **Core i5 and i7 Microprocessor এর মধ্যে হার্ডওয়্যারগত মূল পার্থক্য কী?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 698 (ET: DPI)]*

3. **What is Hyper threading? What is the use of it?** *[BOF Assistant Programmer 2022 compact it 733 (ET: MIST)]*

4. **Now a day, core i3, i5, i7 and i9 CPUs are aavailable. The higher the number is that means powerful processor. What is hyper threading? What does 2 core and 4 thread means?** *[BTRC Assistant Director (Technical) 2021 compact it 808 (ET: IBA)]*

5. **১৩. Core i7 জেনারেশন এর প্রসেসর এর উদাহরণ লিখ?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 942 (ET: N/A)]*

## Assembly Language & Addressing Modes (5)

1. (a) চয়ন করুন: (i) Propagation delay; (ii) Transmission delay;
   (b) SIMD instruction এর সংক্ষিপ্ত বর্ণনা লিখুন: MOV AX, A334H এবং MOV AX, [A334H] *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

2. **Explain the difference between direct, immediate, and register addressing modes in the 8086 microprocessor.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1424 (ET: E-Zone)]*

3. **(খ) নিচের instruction দুটির মাঝে পার্থক্য লিখুন:** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*
MOV AX, A534H এবং MOV AX, [A534H]

4. **(b) Explain the operations of the following instructions: (i) ADC (ii) CMP (iii) JBE** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 691 (ET: N/A)]*

5. **Assembly Language Instructions এর ক্ষেত্রে নিম্মোক্ত Instructions গুলোর কাজ লিখুন। ADC, XCHG, POP ও JNZ.** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1041 (ET: DPI)]*

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
