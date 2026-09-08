<!-- TOC START -->
**Table of Contents** — 5 subtopics · 85 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [CPU & Registers](#cpu--registers-35) | 35 |
| 2 | [Memory Hierarchy](#memory-hierarchy-28) | 28 |
| 3 | [Secondary Storage (HDD & Disk Organization)](#secondary-storage-hdd--disk-organization-13) | 13 |
| 4 | [RAID & Storage Architecture](#raid--storage-architecture-5) | 5 |
| 5 | [Assembly Language & Machine Code](#assembly-language--machine-code-4) | 4 |

<!-- TOC END -->

---

## CPU & Registers (35)

1. **Which of the following is temporary storage used to hold data that is used for arithmetic and logical operations and storing its results?** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 41 (ET: N/A)]*  
   (a) ALU  
   (b) PC (Program counter)  
   (c) Accumulator  
   (d) IR (Instruction Register)

   answer: c — Accumulator  
   explanation: The accumulator holds one operand for the ALU and receives the result of the arithmetic or logic operation.

2. **______ are used to quickly accept, store and transfer data and instructions that are being used immediately by the CPU.** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 53 (ET: N/A)]*  
   (ক) Graphics  
   (খ) RAMs  
   (গ) Caches  
   (ঘ) Registers

   answer: ঘ — Registers  
   explanation: Registers are the fastest storage, sitting inside the CPU to hold the data and instructions in immediate use.

3. **Which feature is not applicable for memory mapped I/O?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*  
   a) Device registers can be accessed with any instructions  
   b) System memory address space is used up for ports  
   c) New instructions are required to access the device registers  
   d) Arithmetic and logical operation can be performed directly on data

   answer: c — New instructions are required to access the device registers  
   explanation: Memory-mapped I/O uses ordinary load and store instructions; needing special IN/OUT instructions is the mark of isolated (port-mapped) I/O.

4. **Which of the following registers is loaded with the contents of the memory location pointed by the PC?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 128 (ET: N/A)]*  
   a) Memory address registers  
   b) Instruction register  
   c) Memory data stores  
   d) Program counter

   answer: b — Instruction register  
   explanation: During fetch the word at the address in the PC is brought in and placed in the instruction register for decoding.

5. **The address bus flow in——** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 128 (ET: N/A)]*  
   a) Unidirectional  
   b) Bidirectional  
   c) Multidirectional  
   d) Circular

   answer: a — Unidirectional  
   explanation: Addresses only travel from the CPU out to memory and I/O, so the address bus carries traffic one way.

6. **Which one is not the flag of the 8086 Microprocessor?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 129 (ET: N/A)]*  
   a) Carry Flag  
   b) Parity Flag  
   c) Zero Flag  
   d) State Plag

   answer: d — State Plag  
   explanation: The 8086 has carry, parity, auxiliary carry, zero, sign, trap, interrupt, direction and overflow flags — there is no "state flag".

7. **In a memory-mapped I/O system, which one is not present?** *[BTRC Sub-Assistant Director (Tech.) 2021 compact it 148 (ET: IBA)]*  
   A. LDA  
   B. IN  
   C. ADD  
   D. OUT

   answer: B — IN  
   explanation: Memory-mapped I/O uses ordinary memory instructions, so the dedicated IN and OUT port instructions are not used (option D is equally absent).

8. **Which one is the 7$^{th}$ Generation intel processor?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 158 (ET: N/A)]*  
   A) Intel core i7-9850HL  
   B) Intel core i5-7200U  
   C) Intel core i5-9400H  
   D) Intel core i9-10900K

   answer: B — Intel core i5-7200U  
   explanation: The first digit after the dash gives the generation, so 7200U is 7th generation (Kaby Lake).

9. **Suppose, the operating clock frequency of a typical CPU is 700 MHz and the number of clocks required for execution of three different instruction types are 4, 8, and 10. If the corresponding appearance rate of the instructions are 30%, 60% and 10%, respectively, how many MIPS does this CPU perform?** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 186 (ET: N/A)]*  
   a) 10  
   b) 50  
   c) 70  
   d) 100

   answer: d — 100  
   explanation: Average CPI = 0.3×4 + 0.6×8 + 0.1×10 = 7, so MIPS = 700×10⁶ ÷ 7 ÷ 10⁶ = 100.

10. **Communication path between a computer microprocessor and main memory is called:** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 172 (ET: N/A)]*  
   a) System bus  
   b) ISA bus  
   c) PCI bus  
   d) Local bus

   answer: a — System bus  
   explanation: The system bus — address, data and control lines together — links the processor to main memory.

11. **Ice Lake CPU is intel’s code name for the processor of:** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 172 (ET: N/A)]*  
   a) 11^{\text{th}} generation  
   b) 8^{\text{th}} generation  
   c) 9^{\text{th}} generation  
   d) 10^{\text{th}} generation

   answer: d — 10th generation  
   explanation: Ice Lake is Intel's 10th generation Core microarchitecture, built on the 10 nm process.

12. **In core i7-8650U processor, here U means:** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 173 (ET: N/A)]*  
   a) Ultra low power  
   b) Ultra high power  
   c) Upgrade version  
   d) Upgrade processor

   answer: a — Ultra low power  
   explanation: The U suffix marks a mobile chip tuned for ultra-low power and long battery life.

13. **Which is not pipeline hazard?** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 173 (ET: N/A)]*  
   a) Resource hazard  
   b) Control hazard  
   c) Address hazard  
   d) Data hazard

   answer: c — Address hazard  
   explanation: The three pipeline hazards are structural (resource), data and control; there is no address hazard.

14. **The processor reads an instruction from memory is called:** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 173 (ET: N/A)]*  
   a) Interpret instruction  
   b) Fetch instruction  
   c) Read instruction  
   d) Fetch data

   answer: b — Fetch instruction  
   explanation: Fetch is the first step of the instruction cycle, bringing the instruction from memory into the CPU.

15. **Microprocessor reference that are available in the cache are called ________:** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 173 (ET: N/A)]*  
   a) Cache hits  
   b) Cache line  
   c) Cache memory  
   d) All of these

   answer: a — Cache hits  
   explanation: A cache hit is a reference that is found in the cache; a miss forces a slower fetch from main memory.

16. **Sequence Control Register আর কি নামে পরিচিত?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 187 (ET: N/A)]*  
   A) Program Counter  
   B) Instruction Counter  
   C) Sequence Register  
   D) Controlling Register

   answer: A — Program Counter  
   explanation: The program counter holds the address of the next instruction, so it is also called the sequence control register or instruction pointer.

17. **Intel 8086 microprocessor এর বহিঃস্থ Address bus এর width কত bit হয়?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 187 (ET: N/A)]*  
   A) 8-bit  
   B) 16-bit  
   C) 20-bit  
   D) 32-bit

   answer: C — 20-bit  
   explanation: The 8086 has a 20-bit address bus, giving 2²⁰ = 1 MB of addressable memory.

18. **Microprocessor এর কোন অংশে ALU থাকে?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)]*  
   A) Fetch unit  
   B) Control Unit  
   C) Processing Unit  
   D) Flags Unit

   answer: C — Processing Unit  
   explanation: The ALU sits in the execution or processing unit, where the actual arithmetic and logic work is done.

19. **নিচের কোন Operation টি CPU তে দ্রুত কাজ করে?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)], [BPSC Assistant Network Engineer 2019 compact it 197 (ET: N/A)]*  
   A) Multiplication  
   B) Bitwise OR  
   C) Addition  
   D) Division

   answer: B — Bitwise OR  
   explanation: A bitwise OR needs no carry propagation, so it completes in a single cycle faster than addition, multiplication or division.

20. **A hardware device that is capable of executing a sequence of instructions is known as:** *[BREB Assistant Junior Engineer (IT) 2019 compact it 217 (ET: N/A)]*  
   A) CPU  
   B) ALU  
   C) CU  
   D) Processor

   answer: D — Processor  
   explanation: A processor is any hardware unit that executes a stored sequence of instructions; the CPU is the main processor of a computer.

21. **What is the Address bit for an 8-bit Microprocessor?** *[BREB Assistant Junior Engineer (IT) 2019 compact it 218 (ET: N/A)]*  
   A) 4  
   B) 8  
   C) 16  
   D) None

   answer: C — 16  
   explanation: 8-bit microprocessors such as the 8085 carry a 16-bit address bus, addressing 64 KB.

22. **Intel 8086 মাইক্রোপ্রসেসর কত বিট রেজিস্টার থাকে?** *[BPSC Assistant Network Engineer 2019 compact it 194 (ET: N/A)]*  
   A) 4  
   B) 8  
   C) 14  
   D) 16

   answer: D — 16  
   explanation: The 8086 is a 16-bit processor with 16-bit general purpose registers.

23. **START:MOV AX, BX একটি assembly language instruction এখানে MOV হলো-** *[BPSC Assistant Network Engineer 2019 compact it 195 (ET: N/A)]*  
   A) লেবেল  
   B) সোর্স  
   C) Opcode  
   D) ডেস্টিনেশন

   answer: C — Opcode  
   explanation: MOV names the operation, so it is the opcode; AX is the destination operand and BX the source, with START as the label.

24. **Physical connection between Microprocessor Memory and other parts is called-** *[Sonali & Janata Bank Assistant Programmer 2018 compact it 240 (ET: N/A)]*  
   A) Address bus  
   B) Data Bus  
   C) path  
   D) Hub

   answer: B — Data Bus  
   explanation: The bus is the physical set of lines joining processor, memory and peripherals, and the data bus carries the actual information between them. <!-- verify -->

25. **Register circuit is not use in-** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 237 (ET: N/A)]*  
   A) Digital clocks  
   B) Components  
   C) RAM  
   D) Amplifier

   answer: D — Amplifier  
   explanation: An amplifier is an analog circuit; registers are digital storage used in clocks, counters and RAM.

26. **A single communication system that transfers and connects the data between major components inside a computer is-** *[Combined Bank Senior Officer (IT) 2018 compact it 223 (ET: DU)]*  
   A) Address Bus  
   B) Data Bus  
   C) System Bus  
   D) Control Bus

   answer: C — System Bus  
   explanation: The system bus bundles the address, data and control lines that connect all the major components.

27. **USB stands for-** *[Combined Bank Senior Officer (IT) 2018 compact it 224 (ET: DU)]*  
   A) Universal Serial Bus  
   B) Universal Series Bus  
   C) Universal Serial Bits  
   D) Universal Series Bits

   answer: A — Universal Serial Bus  
   explanation: USB is the Universal Serial Bus standard for connecting peripherals.

28. **Compared to CISC and RISC, processors (at the same clock) are -----** *[Combined Bank Maintenance Engineer 2018 compact it 227 (ET: N/A)], [Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 249 (ET: N/A)]*  
   A) Faster  
   B) slower  
   C) similar  
   D) undefined

   answer: A — Faster  
   explanation: RISC uses simple fixed-length instructions that mostly complete in one cycle, so at the same clock it outruns CISC.

29. **CPU fetches the instruction from memory according to value of-** *[Combined 3 Bank Assistant Programmer 2018 compact it 231 (ET: N/A)]*  
   A) Program counter  
   B) status register  
   C) instruction register  
   D) program status word

   answer: A — Program counter  
   explanation: The program counter holds the address of the next instruction, and the CPU fetches from that address.

30. **ALU stores the computed result immediately in** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 246 (ET: N/A)]*  
   A) Memory Address registers  
   B) PC  
   C) General registers  
   D) Accumulator

   answer: D — Accumulator  
   explanation: The ALU writes its result straight back into the accumulator register.

31. **The word length of a computer is measured in-** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 241 (ET: N/A)]*  
   A) Bytes  
   B) Millimeters  
   C) Metes  
   D) Bits

   answer: D — Bits  
   explanation: Word length is how many bits the CPU handles at once — 32-bit or 64-bit, for example.

32. **Central Processing Unit is combination of-** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 242 (ET: N/A)]*  
   A) Control Storage  
   B) Control and output unit  
   C) Arithmetic Logic and Input Unit  
   D) Arithmetic logic and control unit

   answer: D — Arithmetic logic and control unit  
   explanation: The CPU consists of the ALU, the control unit and its registers.

33. **The control unit of a microprocessor-** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 243 (ET: N/A)]*  
   A) Stores data in the memory  
   B) accepts input data from keyboard  
   C) Performs arithmetic/logic function  
   D) None of the above

   answer: D — None of the above  
   explanation: The control unit fetches, decodes and directs — it does not store data, take keyboard input or do the arithmetic, which is the ALU's job.

34. **Which bus used to connect the monitor to the CPU?** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 261 (ET: N/A)]*  
   A) PCI bus  
   B) STE bus  
   C) Memory bus  
   D) SCSI bus

   answer: A — PCI bus  
   explanation: The graphics card that drives the monitor plugs into the PCI (or PCIe) expansion bus.

35. **At the same clock speed compared to CISC, RISC processor works ________.** *[Bangladesh Bank Assistant Maintenance Engineer 2013 compact it 261 (ET: N/A)]*  
   a. faster  
   b. Slower  
   c. at same speed  
   d. none

   answer: a — faster  
   explanation: RISC instructions are simple and mostly single-cycle, and its pipeline is easier to keep full, so it is faster at equal clock speed.

## Memory Hierarchy (28)

1. **Considering computer memory speed, which one is correct order from highest to lowest?** *[Combined Bank Officer (IT) 04.10.2024 compact it 12 (ET: BIBM)]*  
   (a) RAM>Cache>Register SSD HDD  
   (b) Cache RAM>SSD>HDD>Register  
   (c) RAM>SSD>Cache>HDD>Register  
   (d) Register>Cache>RAM>SSD HDD

   answer: d — Register>Cache>RAM>SSD HDD  
   explanation: Speed falls as you move down the hierarchy — registers are fastest, then cache, main memory, SSD and finally the mechanical hard disk.

2. **An increase in a computer's RAM leads to a typical improvement in performance because:** *[Combined Bank Officer (IT) 04.10.2024 compact it 13 (ET: BIBM)]*  
   (a) Virtual memory increases  
   (b) Fewer segmentation faults occur  
   (c) A larger RAM is faster  
   (d) Fewer page faults occur

   answer: d — Fewer page faults occur  
   explanation: More RAM keeps more pages resident, so the system goes to disk less often and the costly page-fault handling drops.

3. **Out of all the following, which one isn't a form of memory?** *[Combined Bank Officer (IT) 04.10.2024 compact it 13 (ET: BIBM)]*  
   (a) translation lookaside buffer  
   (b) instruction opcode  
   (c) instruction register  
   (d) instruction cachenss

   answer: b — instruction opcode  
   explanation: The opcode is a field inside an instruction naming the operation; the TLB, instruction register and instruction cache are all storage.

4. **Which among the following is the fastest memory in a computer that holds information?** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 41 (ET: N/A)]*  
   (a) Register  
   (b) Cache  
   (c) Main memory  
   (d) RAM

   answer: a — Register  
   explanation: Registers sit inside the CPU itself and are accessed in a single clock cycle, faster than any cache or memory.

5. **Which mode of memory access is the fastest?** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 47 (ET: N/A)]*  
   (ক) Reference  
   (খ) Pointer  
   (গ) Double pointer  
   (ঘ) DMA

   answer: ঘ — DMA  
   explanation: Direct Memory Access lets a device move a block straight to or from memory without the CPU handling each word. <!-- verify -->

6. **Which of the following causes the average memory access time to increase in a memory system with cache memory?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*  
   a) Reduction of access time to cache memory  
   b) Decrease in hit ratio  
   c) Reduction of miss penalty  
   d) Decrease in miss ratio

   answer: b — Decrease in hit ratio  
   explanation: A lower hit ratio means more references miss the cache and must go to slow main memory, raising the average access time.

7. **Which of the following is not a nonvolatile storage device?** *[Sonali and Janata Bank Assistant Database Administrator 25-09-2021 compact it 116 (ET: N/A)]*  
   a) Memory Stick  
   b) Hard Disk  
   c) Random Access Memory  
   d) NVRAM

   answer: c — Random Access Memory  
   explanation: RAM loses its contents when power is removed, so it is volatile; memory sticks, hard disks and NVRAM all retain data.

8. **What is the typical speed of USB version 3.0?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 102 (ET: N/A)]*  
   (a) 4.8G bits per second  
   (b) 610 Mbps  
   (c) 6Gbps  
   (d) Both a and b

   answer: a — 4.8G bits per second  
   explanation: USB 3.0 (SuperSpeed) runs at 5 Gbps raw, which is about 4.8 Gbps of usable data rate.

9. **SSDs are more durable than HDDs in extreme and harsh environments because** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 102 (ET: N/A)]*  
   (a) They don't have actuator arms  
   (b) They use fast electronics Memory  
   (c) They do not use 0/1 as data storage unit which is prone to crash  
   (d) All of the above statements are true

   answer: a — They don't have actuator arms  
   explanation: An SSD has no moving heads or spinning platters, so shock and vibration cannot damage it the way they damage a hard disk.

10. **The term LPDDR means-** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 105 (ET: N/A)]*  
   (a) Low-Power Discrete Data Rate  
   (b) Low-processing Double Data Rate  
   (c) Low-Programmable Double Data Rate  
   (d) None of the above

   answer: d — None of the above  
   explanation: LPDDR stands for Low-Power Double Data Rate, and none of the three offered expansions matches that.

11. **How many core/threads does the Intel Core i7-9700K processor have?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 107 (ET: N/A)]*  
   (a) 6/12  
   (b) 4/8  
   (c) 8/8  
   (d) 8/16

   answer: c — 8/8  
   explanation: The i7-9700K has 8 cores but no hyper-threading, so it runs 8 threads.

12. **Which of the following uses the flip-flop circuit in a memory cell?** *[Rupali Bank Ltd. Assistant Network Engineer (ANE) 2021 compact it 82 (ET: N/A)]*  
   a. DRAM  
   b. EEPROM  
   c. SDRAM  
   d. SRAM

   answer: d — SRAM  
   explanation: Each SRAM cell is a latch built from cross-coupled transistors, so it holds its value without refreshing.

13. **কোন বৈশিষ্ট্যের কারণে অজগ স্থায়ী স্মৃতি-স্টোরেজ হিসেবে ব্যবহার অনুপযোগী?** *[BTRC Sub-Assistant Director (Tech.) 2021 compact it 148 (ET: IBA)]*  
   A. Too Slow  
   B. Unreliable  
   C. Volatility  
   D. Too Bulky

   answer: C — Volatility  
   explanation: RAM loses everything when power is cut, which is why it cannot serve as permanent storage.

14. **Which of the following memory devices is not reprogrammable?** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 174 (ET: N/A)]*  
   a) Flash memory  
   b) ROM  
   c) EPROM  
   d) EEPROM

   answer: b — ROM  
   explanation: Mask ROM is written once during manufacture and can never be reprogrammed; EPROM, EEPROM and flash can all be erased and rewritten.

15. **There is a RAM issue on a PC/laptop. Which of the following symptom(s) might be an indication of RAM issue?** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 178 (ET: N/A)]*  
   a) PC frequently freezes, reboots  
   b) Wrong BIOS time  
   c) Function keys are not working properly  
   d) All of them

   answer: a — PC frequently freezes, reboots  
   explanation: Faulty RAM corrupts data in memory, producing random freezes, reboots and blue screens; a wrong BIOS clock points to the CMOS battery instead.

16. **A solid-state drive (SSD) is a newer, faster type of device that stores data on instantly-accessible ________.** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 178 (ET: N/A)]*  
   a) Ultra Magnetic Chip  
   b) Integrated Circuit  
   c) Random Access Memory  
   d) High Bandwidth memory

   answer: b — Integrated Circuit  
   explanation: An SSD stores data in NAND flash integrated circuits, so there is nothing mechanical to wait for.

17. **Which factor is not affecting the processing speed of a computer system?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 159 (ET: N/A)]*  
   A) Cache memory  
   B) Clock speed  
   C) Monitor  
   D) RAM

   answer: C — Monitor  
   explanation: The monitor only displays output; processing speed depends on clock rate, cache and the amount of RAM.

18. **Main Memory কোনটি?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 186 (ET: N/A)]*  
   A) RAM  
   B) ROM  
   C) HDD  
   D) Floppy

   answer: A — RAM  
   explanation: RAM is the main memory the CPU reads and writes directly while programs run.

19. **নিচের কোনটি সবচেয়ে দ্রুত Data transfer করতে পারে?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 187 (ET: N/A)], [BPSC Assistant Network Engineer 2019 compact it 197 (ET: N/A)]*  
   A) RAM  
   B) Hard disk  
   C) CD ROM  
   D) Cache Memory

   answer: D — Cache Memory  
   explanation: Cache is the fastest of the four, sitting closest to the CPU and built from SRAM.

20. **Arithmetic and Logical operation এর ডাটা কাজের সময় কোথায় রাখা হয়?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)]*  
   A) Arithmetic Register  
   B) Accumulator  
   C) Logical Register  
   D) Controller

   answer: B — Accumulator  
   explanation: The accumulator holds the operand and receives the result of each arithmetic or logic operation.

21. **Which one can be used for read only?** *[BREB Assistant Junior Engineer (IT) 2019 compact it 218 (ET: N/A)]*  
   A) RAM  
   B) ROM  
   C) Both A & B  
   D) None

   answer: B — ROM  
   explanation: Read Only Memory is written once and afterwards can only be read.

22. **Which is the faster memory?** *[DESCO Assistant Engineer (CSE) 2016 compact it 257 (ET: N/A)], [BREB Assistant General Manager (IT) 2016 compact it 253 (ET: N/A)]*  
   a. RAM  
   b. Secondary memory  
   c. DRAM  
   d. Cache

   answer: d — Cache  
   explanation: Cache is built from fast SRAM and sits next to the CPU, so it is faster than RAM, DRAM or any secondary memory.

23. **Which of the following terms is the most closely related to main memory?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 240 (ET: N/A)]*  
   A) Non-volatile  
   B) Permanent  
   C) Control unit  
   D) Temporary

   answer: D — Temporary  
   explanation: Main memory is volatile working storage that holds data only while the program runs and the power is on.

24. **Which unit holds data permanently?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 241 (ET: N/A)]*  
   A) Input unit  
   B) Secondary storage unit  
   C) Output unit  
   D) Primary Memory unit

   answer: B — Secondary storage unit  
   explanation: Secondary storage such as a hard disk or SSD is non-volatile, so it keeps data after the power is switched off.

25. **Magnetic tape can serve as—** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 241 (ET: N/A)]*  
   A) Secondary storage media  
   B) Output media  
   C) Input media  
   D) All of them

   answer: D — All of them  
   explanation: Magnetic tape stores data offline as secondary storage and can also be used to feed data in or write results out.

26. **Which of the following is internal memory?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 243 (ET: N/A)]*  
   A) Disks  
   B) Pen Drives  
   C) RAM  
   D) CDs

   answer: C — RAM  
   explanation: RAM is internal (primary) memory on the motherboard; disks, pen drives and CDs are external secondary storage.

27. **Which of the following memories needs refreshing?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 243 (ET: N/A)]*  
   A) SRAM  
   B) DRAM  
   C) ROM  
   D) All of them

   answer: B — DRAM  
   explanation: A DRAM cell stores its bit as charge on a tiny capacitor that leaks away, so it must be refreshed thousands of times a second.

28. **Which memory is called as primary memory?** *[BREB Assistant General Manager (IT) 2016 compact it 254 (ET: N/A)]*  
   A) Hard Disk  
   B) Pen Drive  
   C) Rom  
   D) RAM

   answer: D — RAM  
   explanation: RAM is the primary memory the processor works from directly.

## Secondary Storage (HDD & Disk Organization) (13)

1. **A hard disk is divided into tracks which are further subdivided into ______** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 41 (ET: N/A)]*  
   (a) Vectors  
   (b) Clusters  
   (c) Sectors  
   (d) None of the above

2. **Consider a magnetic disk packed with 32 surfaces. Each surface is divided into 128 tracks while 256 sectors per track. If the size of a sector is 1024 bytes, then what is the total capacity of the disk?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*  
   a) 2³⁰ bytes  
   b) 2³³ bytes  
   c) 2²⁷ bytes  
   d) 2²⁰ bytes

3. **DVD এর চেয়ে বেশী Data store করা যায় কোনটিতে?** *[BPSC Senior Instructor (MEW) 2021 compact it 145 (ET: N/A)]*  
   (a) CD Rom  
   (b) Floppy  
   (c) Blue Ray disk  
   (d) Red Ray disk

4. **Which of the following is major part of time taken when accessing data on the disk?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 205 (ET: AUST)]*  
   A) Settle time  
   B) Rotational delay  
   C) Waiting time  
   D) Seek time

5. **Place where large amount of data is stored outside central processing unit is called** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 215 (ET: AUST)]*  
   A) Peripherals  
   B) Control unit  
   C) AI unit  
   D) Backing store

6. **Which are not performance characteristics of hard disk?** *[Sonali & Janata Bank Assistant Programmer 2018 compact it 239 (ET: N/A)]*  
   A) data transfer time  
   B) response time  
   C) power consumption  
   D) shelf life

7. **Which of the following is used for manufacturing chips?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 241 (ET: N/A)]*  
   A) Control bus  
   B) Control unit  
   C) Parity unit  
   D) Semiconductor

8. **Before a disk can be used to store data, it must be-** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 241 (ET: N/A)]*  
   A) Formatted  
   B) Reformatted  
   C) Addressed  
   D) None

9. **Which technology is used in Compact disks?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 241 (ET: N/A)]*  
   A) Mechanical  
   B) Electrical  
   C) Electromagnetic  
   D) Laser

10. **Which of the following is a storage device?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 241 (ET: N/A)]*  
   A) Tape  
   B) Hard Disk  
   C) Floppy Disk  
   D) All of them

11. **What does the disk drive of computer do?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 242 (ET: N/A)]*  
   A) Rotate the Disk  
   B) Read the disk  
   C) Load a program form the disk into the memory  
   D) Both B and C

12. **Which of the items below are considered removable storage media?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 242 (ET: N/A)]*  
   A) Removable hard disk cartridges  
   B) (Magneto-optical) disk  
   C) Flexible disks cartridges  
   D) All of them

13. **A hard disk is divided into tracks which are further subdivided into ________** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 270 (ET: N/A)]*  
   a. Clusters  
   b. Sectors  
   c. Vectors  
   d. Heads

## RAID & Storage Architecture (5)

1. **Which RAID level creates a mirror of all disks for storing data?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 126 (ET: N/A)]*  
   a) RAID Level 0  
   b) RAID Level 1  
   c) RAID Level 2  
   d) RAID Level 3

2. **The fastest read/write time and most efficient data storage of any disk array type is:** *[Sonali and Janata Bank Assistant Database Administrator 25-09-2021 compact it 114 (ET: N/A)]*  
   a) RAID-0  
   b) RAID-1  
   c) RAID-2  
   d) RAID-3

3. **How does RAID provide data protection?** *[Sonali and Janata Bank Assistant Database Administrator 25-09-2021 compact it 116 (ET: N/A)]*  
   a) Using either data mirroring or parity  
   b) Using either data mirroring or striping  
   c) Using high quality disk drives  
   d) Using dedicated data protection hardware

4. **Why RAID is used in database storage?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 168 (ET: N/A)]*  
   a) Improve performance  
   b) Reduce Cost  
   c) Both a & b  
   d) None

5. **What is the name of below RAID?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 150 (ET: DU)]*  
   a) RAID 0+1  
   b) RAID 1+0  
   c) RAID 01  
   d) RAID 10

## Assembly Language & Machine Code (4)

1. **In which addressing mode, the effective address of the operand is generated by adding a constant value to the contents of the register?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 131 (ET: N/A)]*  
   a) Absolute mode  
   b) Indirect mode  
   c) Immediate mode  
   d) Index mode

2. **Consider the following program fragment in assembly language:** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 107 (ET: N/A)]*
   ```assembly
   mov ax, 0h
   mov cx, 0A h
   doloop:
   dac ax
   loop doloop
   ```
   What is the value of ax and cx registers after the completion of the do loop?  
   (a) ax=FFF5 h and cx=0h  
   (b) ax=FFF6 h and cx=0h  
   (c) ax=FFF7 h and cx=A h  
   (d) ax=FFF5 h and cx=0A h

3. **Which is the immediate addressing mode in an 8086 microprocessor?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 164 (ET: N/A)]*  
   a) MOV, AX, BX  
   b) MOV, AX, [BX]  
   c) MOV AX, 1000  
   d) MOV Ax, [BX+1000]  
   7. Consider the following relation-  
   | employee |  
   |---|  
   | ID |  
   | name |  
   | \quad first_name |  
   | \quad last_name |  
   | address |  
   | \quad city |  
   | \quad zip |  
   | birth_date |  
   | age() |  
   Which is the composite attribute in the “employee” relation? *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 164 (ET: N/A)]*  
   a) age, ID  
   b) birth_date  
   c) name, address  
   d) name, age

4. **What is the difference between mnemonic codes & machine codes?** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 270 (ET: N/A)]*  
   a. Machine codes are in shorthand English & Mnemonic codes are high level language  
   b. Machine codes are in Binary & Mnemonic codes are in shorthand English  
   c. Mnemonic codes are in Binary & Machine codes are in shorthand English  
   d. There is no difference
