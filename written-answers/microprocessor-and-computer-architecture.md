<!-- TOC START -->
**Table of Contents** — 11 subtopics · 135 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Microprocessor Architecture & Functions](#microprocessor-architecture--functions-35) | 35 |
| 2 | [Memory Hierarchy & Storage](#memory-hierarchy--storage-26) | 26 |
| 3 | [RAID Architecture & Storage](#raid-architecture--storage-15) | 15 |
| 4 | [Cache Memory](#cache-memory-14) | 14 |
| 5 | [Secondary Storage (HDD vs SSD)](#secondary-storage-hdd-vs-ssd-10) | 10 |
| 6 | [Instruction Pipelining & Hazards](#instruction-pipelining--hazards-9) | 9 |
| 7 | [Assembly Language & Addressing Modes](#assembly-language--addressing-modes-8) | 8 |
| 8 | [CPU Performance & Instruction Cycle](#cpu-performance--instruction-cycle-6) | 6 |
| 9 | [Multi-Core & Multi-Threading](#multi-core--multi-threading-5) | 5 |
| 10 | [RISC vs CISC Architecture](#risc-vs-cisc-architecture-4) | 4 |
| 11 | [8085 Microprocessor & Edge Computing](#8085-microprocessor--edge-computing-3) | 3 |

<!-- TOC END -->

---

## Microprocessor Architecture & Functions (35)

1. **ছোট প্রসেসরের (Microprocessor) কাজ এক নজরে এবং কী কী?** *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) A `microprocessor` is a single integrated circuit that contains the entire central processing unit of a computer — the ALU, the control unit and the registers. It fetches instructions from memory, decodes them and executes them.

   Main functions
   - `Fetch` — read the next instruction from memory, using the address held in the program counter.
   - `Decode` — work out what the instruction means and which units are needed.
   - `Execute` — perform the operation, then store the result.
   - `Write back / store` — put the result into a register or into memory.
   ```
      Fetch -> Decode -> Execute -> Store , repeated for every instruction.
      This is the INSTRUCTION CYCLE (also called the machine cycle).
   ```

   Detailed functions
   - `Arithmetic operations` — addition, subtraction, multiplication, division, increment, decrement, performed by the ALU.
   - `Logical operations` — AND, OR, NOT, XOR, and comparison, also in the ALU.
   - `Data transfer` — moving data between registers, memory and I/O devices.
   - `Control and timing` — the control unit generates the signals that tell every other part when to act, all synchronised to the clock.
   - `Program flow control` — jumps, branches, loops, procedure calls and returns, by changing the program counter.
   - `Interrupt handling` — suspending the current program to service an urgent event, then resuming it exactly where it left off.
   - `Bus control` — driving the address bus, data bus and control bus to reach memory and peripherals.
   - `Status reporting` — setting the flags (zero, carry, sign, overflow, parity) that later instructions test.
   - `I/O coordination` — reading from and writing to peripherals, and granting the bus to a DMA controller when a fast device needs it.

   Main parts
   ```
           +---------------------------------------+
           |            MICROPROCESSOR             |
           |                                       |
           |   +----------+     +-------------+    |
           |   |   ALU    |     |  Registers  |    |
           |   +----------+     +-------------+    |
           |            \        /                 |
           |          +--------------+             |
           |          | Control Unit |             |
           |          +--------------+             |
           +---------------|-----------------------+
                           |
           Address bus  ---+---  Data bus  ---  Control bus
                           |
                     Memory and I/O
   ```

   - `ALU` does the arithmetic and logic. `Registers` hold data and addresses temporarily — PC, IR, accumulator, MAR, MDR, flags. `Control unit` decodes instructions and issues timing signals.
   - Examples: Intel 8085, 8086, Pentium, Core i7; AMD Ryzen; ARM Cortex.

2. **b) Compare and contrast between CPU and GPU.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1342 (ET: N/A)]*

   Answer: A `CPU` is a general-purpose processor built to run a few complex tasks quickly, one after another. A `GPU` is built to run thousands of simple, identical tasks at the same time.

   CPU (Central Processing Unit)
   - A `few powerful cores` — typically 4 to 16 — each with a large instruction set, deep pipelines, branch prediction and out-of-order execution.
   - Large caches (L1, L2, L3) and a very high clock speed.
   - Optimised for `low latency`: finish one task as fast as possible.
   - Good at branching, decision-making and irregular code — anything with lots of `if` statements.

   GPU (Graphics Processing Unit)
   - `Thousands of simple cores` — an RTX-class chip has over 10,000. Each is weak on its own.
   - Small caches, lower clock speed, but very wide memory bandwidth.
   - Optimised for `high throughput`: run the same instruction on thousands of data items at once. This is the `SIMD` model.
   - Poor at branching, because the cores in a group must all execute the same instruction.

   ```
      CPU                            GPU
      +------+------+                +--+--+--+--+--+--+--+--+
      | Core | Core |                |c |c |c |c |c |c |c |c |
      +------+------+                +--+--+--+--+--+--+--+--+
      | Core | Core |                |c |c |c |c |c |c |c |c |
      +------+------+                +--+--+--+--+--+--+--+--+
      +-------------+                |c |c |c |c |c |c |c |c |
      |  large cache|                +--+--+--+--+--+--+--+--+
      +-------------+                    (many small cores)

      few strong cores               many weak cores
   ```

   Comparison

   | Point | CPU | GPU |
   |---|---|---|
   | Number of cores | Few (4 to 64) | Thousands |
   | Core strength | Very powerful | Simple and weak |
   | Optimised for | Low latency | High throughput |
   | Execution model | Sequential, task parallel | Massively parallel, SIMD |
   | Cache | Large | Small per core |
   | Memory bandwidth | Moderate (~50-100 GB/s) | Very high (~500-1000 GB/s) |
   | Branching | Handles it well | Handles it badly |
   | Clock speed | Higher (3-5 GHz) | Lower (1-2 GHz) |
   | Power per chip | 65-150 W | 200-450 W |
   | Best for | OS, applications, databases, logic | Graphics, matrix maths, AI training, video encoding |

   Why the GPU wins on parallel work
   ```
      Adding two arrays of one million elements :

      CPU : loop one million times on a few cores       -> slow
      GPU : launch one million threads, run thousands
            of them simultaneously                       -> far faster
   ```
   - This is exactly the shape of matrix multiplication, which is why the GPU became the standard hardware for `deep learning`. Training a neural network is billions of independent multiply-and-add operations.

   - They are used `together`, not as alternatives: the CPU runs the operating system and the program logic and decides what to do, then hands the heavy uniform number-crunching to the GPU. The CPU is the manager, the GPU is the workforce.

3. **What exactly is a microcontroller? What distinguishes a microprocessor from a microcontroller? Mention the differences between RISC and CISC microprocessors.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 323 (ET: BIBM)]*

   Answer: What a microcontroller is
   - A `microcontroller (MCU)` is a complete small computer on a single chip. It contains a CPU, `RAM`, `ROM/Flash`, `I/O ports`, `timers`, `ADC` and serial interfaces, all in one package.
   - It is designed for `embedded` control — running one fixed program that reads sensors and drives outputs — in washing machines, microwave ovens, cars, medical devices and IoT nodes.
   - Examples: Intel 8051, Atmel AVR (ATmega328 in Arduino), Microchip PIC, ARM Cortex-M, ESP32.

   Microprocessor versus microcontroller
   ```
      Microprocessor : CPU only. RAM, ROM and I/O must be added externally.
      Microcontroller: CPU + RAM + ROM + I/O + timers, all on one chip.
   ```

   | Point | Microprocessor | Microcontroller |
   |---|---|---|
   | Contains | CPU only | CPU + memory + I/O + timers |
   | External components | RAM, ROM, I/O chips all needed | Few or none |
   | Cost of a system | High | Low |
   | Board size | Large | Very small |
   | Power consumption | High (watts) | Very low (milliwatts) |
   | Clock speed | Very high (GHz) | Low (MHz) |
   | Memory capacity | Large — gigabytes | Small — kilobytes |
   | Architecture | Usually von Neumann | Usually Harvard |
   | Purpose | General purpose | One dedicated task |
   | Operating system | Runs Windows, Linux | Bare metal or an RTOS |
   | Real-time response | Not guaranteed | Precise and predictable |
   | Examples | Intel Core i7, AMD Ryzen | 8051, ATmega328, PIC, ARM Cortex-M |

   - Simple way to state it: a microprocessor is the `brain` and needs a body built around it; a microcontroller is `brain plus body` already on one chip.

   RISC versus CISC

   `RISC` (Reduced Instruction Set Computer)
   - A small set of simple, fixed-length instructions, each completing in about one clock cycle.
   - A `load-store` architecture: only LOAD and STORE touch memory, and everything else works on registers.
   - Many registers, simple hardwired control, and easy pipelining.
   - Examples: ARM, RISC-V, MIPS, SPARC, PowerPC.

   `CISC` (Complex Instruction Set Computer)
   - A large set of powerful, variable-length instructions, some taking many clock cycles. One instruction can do a lot of work.
   - Instructions can operate directly on memory.
   - Fewer registers, complex microcoded control.
   - Examples: Intel x86, AMD64, Motorola 68000.

   | Point | RISC | CISC |
   |---|---|---|
   | Instruction set | Small and simple | Large and complex |
   | Instruction length | Fixed | Variable |
   | Cycles per instruction | Mostly 1 | Many |
   | Memory access | Only LOAD and STORE | Most instructions can |
   | Registers | Many (32 or more) | Few (8 to 16) |
   | Control unit | Hardwired | Microprogrammed |
   | Pipelining | Easy and efficient | Difficult |
   | Code size | Larger | Smaller |
   | Compiler work | Higher | Lower |
   | Power consumption | Low | Higher |
   | Used in | Mobile, embedded, Apple M-series | Desktop and server x86 |

   - Practical note: the line has blurred. Modern x86 processors decode their CISC instructions internally into RISC-like `micro-operations`, so they are CISC on the outside and RISC on the inside. RISC still wins clearly on power efficiency, which is why every phone uses ARM.

4. **GPU stands for __________?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

   Answer: `GPU` stands for `Graphics Processing Unit`.

   - It is a specialised processor built to perform many simple calculations at the same time. It was originally designed to render images, video and 3D graphics for the display.
   - A GPU has `thousands of small cores`, against a CPU's handful of powerful ones, so it excels at doing the same operation on thousands of data items simultaneously — the `SIMD` model.
   ```
      CPU : few strong cores  -> low latency, good at logic and branching
      GPU : many weak cores   -> high throughput, good at uniform parallel maths
   ```

   Types
   ```
      Integrated GPU : built into the CPU chip, shares system RAM,
                       low power, adequate for office work
      Dedicated GPU  : a separate card with its own high-speed VRAM,
                       used for gaming, design and AI
   ```

   Modern uses beyond graphics
   - `Deep learning` — training a neural network is billions of independent multiply-and-add operations, exactly the shape a GPU is built for. This is why NVIDIA GPUs dominate AI.
   - `Scientific computing` — weather models, molecular dynamics, finite element analysis. Known as `GPGPU`, general-purpose computing on a GPU.
   - `Video encoding and decoding`, image processing, and cryptocurrency mining.

   - Manufacturers: `NVIDIA` (GeForce, RTX, Tesla), `AMD` (Radeon), `Intel` (Arc, and the integrated UHD graphics).

5. **Maximum three word complete this below section:** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 431 (ET: BUET)]*

| Question | Answer |
|---|---|
| (a) Which bus transfers data between data and I/O Data Bus devices? | Data Bus |
| (b) Which register contains the address of next instructions? | Program counter |
| (c) Which register does the arithmetic and logical operation? | Arithmetic Logic Unit (ALU) |
| (d) Which system connects the hardware and software? | Operating System(OS) |
| (e) Microprocessor and other peripherals are interfaced Microcontroller, with which board? | Microcontrollers, Motherboard |

   Answer: (a) Which bus transfers data between the CPU and I/O devices?
   ```
      Data Bus
   ```
   - It is `bidirectional` and carries the actual information. Its width — 8, 16, 32 or 64 lines — defines the word size of the processor.
   - The other two system buses are the `address bus` (unidirectional, carries the location) and the `control bus` (carries read, write, interrupt and clock signals).

   (b) Which register contains the address of the next instruction?
   ```
      Program Counter (PC)
   ```
   - Also called the `Instruction Pointer (IP)` in the Intel 8086 family.
   - It is incremented automatically after each fetch, and it is loaded with a new value by a jump, branch, call or interrupt.

   (c) Which unit does the arithmetic and logical operations?
   ```
      Arithmetic Logic Unit (ALU)
   ```
   - It performs `arithmetic` — add, subtract, multiply, divide, increment, decrement — and `logic` — AND, OR, NOT, XOR, compare and shift.
   - It also sets the `flags` (zero, carry, sign, overflow, parity) that later instructions test.

   (d) Which system connects the hardware and the software?
   ```
      Operating System (OS)
   ```
   - The OS is the layer between the user's programs and the machine. It manages the processor, memory, files, devices and security, and provides `system calls` and `device drivers` so that a program need not know anything about the hardware underneath.

   (e) Microprocessors and other peripherals are interfaced on which board?
   ```
      Motherboard (system board)
   ```
   - It carries the CPU socket, the chipset, RAM slots, expansion slots, the BIOS/UEFI chip and the connectors, and it holds the buses that join them all together.

   Summary

   | Question | Answer |
   |---|---|
   | (a) Bus that carries data | Data Bus |
   | (b) Register holding the next instruction address | Program Counter |
   | (c) Unit doing arithmetic and logic | ALU |
   | (d) System joining hardware and software | Operating System |
   | (e) Board that interfaces the processor and peripherals | Motherboard |

6. **ALU কী? এর কার্যপদ্ধতি চিত্রসহ বর্ণনা করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 405 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) The `Arithmetic Logic Unit (ALU)` is the part of the CPU that actually performs all the arithmetic and logical operations. Every calculation a computer makes happens here.

   Operations it performs
   ```
   Arithmetic : ADD, SUB, MUL, DIV, INC, DEC, negate
   Logical    : AND, OR, NOT, XOR
   Comparison : equal, greater than, less than
   Shift      : left shift, right shift, rotate
   ```

   Block diagram
   ```
                 Operand A            Operand B
                     |                    |
                     v                    v
             +---------------------------------+
             |                                 |
      Opcode |             A L U               |
      ------>|   (adder, logic unit, shifter)  |
      from   |                                 |
      control+---------------------------------+
      unit          |                  |
                    v                  v
                 Result            Status flags
                (to accumulator     Z  C  S  O  P
                 or register)
   ```

   ```mermaid
   flowchart LR
       A[Register A] --> ALU
       B[Register B] --> ALU
       C[Control Unit<br/>opcode] --> ALU
       ALU --> D[Result to accumulator]
       ALU --> E[Flag register<br/>Z C S O P]
   ```

   How it works, step by step
   ```
      1. The control unit decodes the instruction and sends an OPCODE
         (the function-select lines) to the ALU.

      2. The two operands are placed on the ALU's input lines, usually from
         the accumulator and a general-purpose register or from memory.

      3. Inside the ALU, every unit computes at once - the adder, the logic
         unit and the shifter. A multiplexer selects the one the opcode asks for.

      4. The result appears at the output and is written back to the
         accumulator or a destination register.

      5. The status FLAGS are set from the result :

            Z (Zero)     = 1 if the result is 0
            C (Carry)    = 1 if a carry came out of the MSB
            S (Sign)     = 1 if the result is negative (MSB = 1)
            O (Overflow) = 1 if the signed result is out of range
            P (Parity)   = 1 if the result has an even number of 1s

      6. The next instruction can test those flags to make a decision,
         which is how conditional jumps and loops work.
   ```

   Worked example — the instruction `ADD A, B` with A = 5 and B = 3
   ```
      Opcode  -> ALU is told to add
      Inputs  -> 0000 0101  and  0000 0011
      Adder   -> 0000 1000  = 8
      Result  -> written back into the accumulator
      Flags   -> Z = 0 , C = 0 , S = 0 , O = 0 , P = 0 (one 1 bit, odd)
   ```

   Internal structure
   - The ALU is built from `combinational logic`: an adder-subtractor made from full adders, a logic unit made from gate arrays, and a barrel shifter, with a multiplexer choosing the output.
   - Subtraction reuses the same adder: `A - B = A + (2's complement of B)`, which is why no separate subtractor circuit is needed.

   - Points to note: the ALU has no memory of its own — it is purely combinational, and all values come from and return to registers. Modern processors contain several ALUs plus a separate `Floating Point Unit (FPU)`, so more than one operation can be executed per clock cycle.

7. **(ক) Microprocessor এবং Microcontroller এর মাঝে দুইটি পার্থক্য লিখুন।** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer: (Answered in English, as required for IT topics.) A `microprocessor` contains only the CPU — the ALU, control unit and registers. A `microcontroller` contains the CPU `plus` memory, I/O ports and timers, all on one chip.

   Two main differences

   1. What is on the chip
   ```
      Microprocessor : CPU only.
                       RAM, ROM, I/O ports and timers must all be added
                       as separate chips on the board.

      Microcontroller: CPU + RAM + ROM/Flash + I/O ports + timers + ADC
                       + serial interfaces, all inside one package.
                       Very few external components are needed.
   ```

   2. Purpose and the resulting design
   ```
      Microprocessor : general purpose. It runs an operating system and any
                       program the user loads, so it needs large memory, a high
                       clock speed and a lot of power.

      Microcontroller: one dedicated embedded task, running a single fixed
                       program. It needs little memory, runs at a low clock speed
                       and consumes very little power, but must respond in
                       real time and predictably.
   ```

   Fuller comparison

   | Point | Microprocessor | Microcontroller |
   |---|---|---|
   | Contents | CPU only | CPU + RAM + ROM + I/O + timers |
   | External parts | Many required | Few or none |
   | System cost | High | Low |
   | Board size | Large | Very small |
   | Power | Watts | Milliwatts |
   | Clock speed | GHz | MHz |
   | Memory | Gigabytes | Kilobytes |
   | Architecture | Von Neumann | Harvard |
   | Real-time response | Not guaranteed | Precise |
   | Runs an OS | Yes — Windows, Linux | Bare metal or an RTOS |
   | Examples | Intel Core i7, AMD Ryzen | 8051, ATmega328, PIC, ARM Cortex-M |
   | Used in | PC, laptop, server | Washing machine, car ECU, IoT device |

   - The simplest way to say it in an exam: a `microprocessor is the brain and needs a body built around it`; a `microcontroller is brain plus body already on one chip`.

8. **Discuss the factors that affect the Speed of a CPU.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 541 (ET: MIST)]*

   Answer: The `speed` of a CPU is how much work it completes per second. Clock frequency alone does not decide it — several factors act together.

   1. Clock speed (frequency)
   - The number of cycles per second, measured in GHz. A 3.0 GHz processor performs three thousand million cycles a second.
   - Higher frequency means faster execution `only when comparing the same design`. A 2.5 GHz modern chip easily beats a 3.5 GHz ten-year-old one, because it does more work per cycle.

   2. Instructions per cycle (IPC) and architecture
   ```
      Real performance = clock speed x IPC x number of cores
   ```
   - A better pipeline, wider issue width, better branch prediction and out-of-order execution all raise IPC. This is where most modern gains come from.

   3. Number of cores and threads
   - More cores allow more tasks to run genuinely simultaneously. Hyper-threading lets one core run two threads and keeps its units busy.
   - The gain is limited by `Amdahl's law`: the serial part of a program does not get faster no matter how many cores are added.

   4. Cache memory
   - Cache is small, very fast memory close to the core. A `hit` takes a few cycles; a miss that reaches RAM takes hundreds.
   ```
      L1 : 32-64 KB    ~4 cycles
      L2 : 256KB-1 MB  ~12 cycles
      L3 : 8-32 MB     ~40 cycles
      RAM: gigabytes   ~200+ cycles
   ```
   - A larger, better-organised cache raises the hit rate and therefore the effective speed enormously.

   5. Word size (bus width)
   - A 64-bit CPU processes 64 bits per operation and can address far more memory than a 32-bit one, so it moves more data per cycle.

   6. Pipelining and superscalar design
   - Pipelining overlaps the fetch, decode and execute stages so an instruction completes every cycle. A superscalar CPU issues several instructions per cycle.
   - `Hazards` — data dependencies, branch mispredictions — stall the pipeline and cost cycles.

   7. Memory and bus speed
   - The `front-side bus` or memory controller bandwidth, the RAM type (DDR4 versus DDR5) and its latency all limit how fast data reaches the CPU. A fast CPU starved of data is idle.

   8. Instruction set
   - RISC instructions are simple and pipeline well; CISC packs more work into one instruction. Special instruction sets — SSE, AVX, AES — accelerate specific tasks dramatically.

   9. Thermal conditions and power
   - If the chip gets too hot it `throttles`, dropping its clock to protect itself. Good cooling therefore directly affects sustained speed, and `turbo boost` only lasts while thermal headroom exists.

   10. Manufacturing process
   - A smaller process (7 nm, 5 nm, 3 nm) puts transistors closer together, so they switch faster and use less power, allowing a higher clock at the same heat.

   11. Software factors
   - A well-optimised, multi-threaded, compiler-optimised program uses the hardware far better than a poorly written one. Background processes and an unsuitable OS also steal cycles.

   - Summary: clock speed is only one term. `Speed = clock x IPC x cores`, and all of it is limited by how fast the cache and memory can feed the processor.

9. **Difference between 32 bit Microprocessor and 64 bit Microprocessor with example. What is the meaning of 2.40GHz Microprocessor? Differentiate among Core Intel i3, i5 and i7 processor. Why do you prefer SSD instead of HD?** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 508 (ET: MIST)]*

   Answer: 32-bit versus 64-bit microprocessor
   - The number refers to the width of the `registers and the data path` — how many bits the CPU handles in one operation — and to the size of the address it can form.
   ```
      32-bit : addresses 2^32 bytes = 4 GB of RAM
      64-bit : addresses 2^64 bytes = 16 exabytes in theory
               (16 to 256 GB in practice, limited by the chipset)
   ```

   | Point | 32-bit | 64-bit |
   |---|---|---|
   | Register and data path width | 32 bits | 64 bits |
   | Maximum addressable RAM | 4 GB | Practically unlimited |
   | Data per operation | 4 bytes | 8 bytes |
   | Number of registers | Fewer | More (x86-64 doubles them) |
   | Speed on large data | Slower | Faster |
   | Software support | Runs only 32-bit software | Runs both 32-bit and 64-bit |
   | Examples | Intel 80386, 80486, Pentium 4 (early) | Intel Core i3/i5/i7/i9, AMD Ryzen, ARM64 |

   What "2.40 GHz microprocessor" means
   ```
      1 Hz  = 1 cycle per second
      1 GHz = 1,000,000,000 cycles per second

      2.40 GHz = 2,400,000,000 clock cycles per second
   ```
   - The `clock` is the metronome of the CPU. Each cycle the processor advances one step of the instruction pipeline, so at 2.4 GHz a step takes about `0.42 nanoseconds`.
   - It does `not` mean 2.4 billion instructions per second. Some instructions take several cycles, and a superscalar CPU completes several instructions per cycle. Real throughput is `clock x IPC x cores`.
   - Most modern CPUs quote a `base` clock and a higher `turbo` clock reached when thermal headroom allows.

   Core i3, i5 and i7

   | Point | Core i3 | Core i5 | Core i7 |
   |---|---|---|---|
   | Positioning | Entry level | Mid range | High end |
   | Cores (typical) | 4 | 6 | 8 or more |
   | Threads | 8 | 12 | 16 or more |
   | Cache | Smallest | Medium | Largest |
   | Turbo Boost | Usually absent | Yes | Yes, higher |
   | Clock speed | Lower | Medium | Highest |
   | Price and power | Lowest | Medium | Highest |
   | Suited to | Browsing, office work | Everyday plus gaming | Video editing, CAD, development |

   - Points to note: the number is a `tier`, not a generation. A newer i5 usually beats an older i7, so the generation code — the first digits of the model number, as in `i5-13600K` — matters more than the tier.

   Why SSD is preferred over HDD
   - `Speed.` An SSD has no moving parts and no seek time. Sequential read is 500 MB/s for SATA and 3,000-7,000 MB/s for NVMe, against 100-150 MB/s for a hard disk. Random access is where the gap is largest — microseconds against milliseconds — and random access is what an operating system does most.
   - `Boot and load times` fall from a minute to a few seconds.
   - `Durability` — no spinning platter or moving head, so it survives shock and vibration. This matters most in a laptop.
   - `Silent`, `cooler` and much lower power, which extends battery life.
   - `Lighter and smaller`, and available in the tiny M.2 form factor.

   - The case for keeping a hard disk: `cost per gigabyte` is still far lower, and capacities are larger, so the usual arrangement is an `SSD for the operating system and applications` and an `HDD for bulk storage and backups`.

10. **8086 microprocessor সম্বলিত একটি ডায়াগ্রাম বা ফিগার হতে ২টি পার্ট এর নাম উল্লেখ কর?** *[BTCL Junior Assistant Manager 2022 compact it 640 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) The 8086 architecture is divided into `two independent units`. Naming these two parts is what the question asks for.

    The two main parts
    ```
       1. BIU  -  Bus Interface Unit
       2. EU   -  Execution Unit
    ```

    ```
       +--------------------------------------------------+
       |                    8086 CPU                      |
       |                                                  |
       |   BUS INTERFACE UNIT (BIU)                       |
       |   +------------------------------------------+   |
       |   | Segment registers : CS  DS  SS  ES       |   |
       |   | Instruction Pointer (IP)                 |   |
       |   | Address adder (segment x 16 + offset)    |   |
       |   | 6-byte instruction QUEUE                 |   |
       |   +------------------------------------------+   |
       |                    |                             |
       |         instruction queue passes bytes down      |
       |                    v                             |
       |   EXECUTION UNIT (EU)                            |
       |   +------------------------------------------+   |
       |   | General registers : AX BX CX DX          |   |
       |   | Pointer / index   : SP BP SI DI          |   |
       |   | ALU (16-bit)                             |   |
       |   | Flag register                            |   |
       |   | Control unit / instruction decoder        |   |
       |   +------------------------------------------+   |
       +--------------------------------------------------+
    ```

    Bus Interface Unit (BIU)
    - Handles all communication with memory and I/O — it drives the address, data and control buses.
    - Contains the four `segment registers` (CS, DS, SS, ES) and the `instruction pointer (IP)`.
    - Calculates the 20-bit physical address:
    ```
       Physical address = segment register x 16 + offset
    ```
    - Holds a `6-byte instruction queue`. While the EU is busy executing, the BIU fetches the next instructions in advance and fills this queue. This is `pipelining`, and it is the main reason the 8086 was faster than the 8085.

    Execution Unit (EU)
    - Takes instructions from the queue, decodes them and executes them.
    - Contains the four general-purpose registers `AX, BX, CX, DX`, the pointer and index registers `SP, BP, SI, DI`, the `16-bit ALU`, the `flag register` and the control unit.
    - It has no connection to the outside buses at all; whenever it needs data it asks the BIU.

    Why the split matters
    ```
       Without the split : fetch, decode, execute, fetch, decode, execute ...
       With the split    : the BIU fetches the NEXT instruction while the EU
                           executes the CURRENT one -> the two overlap

       Result : the bus is kept busy, idle time falls, and throughput rises.
    ```
    - The queue is flushed whenever a jump, call or interrupt changes the flow, because the prefetched bytes are then no longer the right ones.

    - Short answer for the exam: the two parts are the `Bus Interface Unit (BIU)` and the `Execution Unit (EU)`.

11. **Explain the necessary steps to communicate through a programmable peripheral interfacing device (8255 Microprocessor).** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 672 (ET: N/A)]*

    Answer: The `8255 PPI` (Programmable Peripheral Interface) gives a microprocessor 24 programmable I/O lines, arranged as three 8-bit ports.
    ```
       Port A  : 8 lines  (PA0 - PA7)
       Port B  : 8 lines  (PB0 - PB7)
       Port C  : 8 lines  (PC0 - PC7), which can be split into two 4-bit halves
       Control word register : sets the direction and mode of each port
    ```

    Block diagram
    ```
                        +--------------------------+
       D0-D7  <-------->|  Data bus buffer         |
                        |                          |<-----> PA0-PA7  (Port A)
       RD'    --------->|  Read / Write            |
       WR'    --------->|  control logic           |<-----> PB0-PB7  (Port B)
       A0, A1 --------->|                          |
       CS'    --------->|  Group A and Group B     |<-----> PC0-PC7  (Port C)
       RESET  --------->|  control                 |
                        +--------------------------+
    ```

    Port selection by the address lines
    ```
       CS'  A1  A0 | Selected
       ------------+--------------------
        0    0   0 | Port A
        0    0   1 | Port B
        0    1   0 | Port C
        0    1   1 | Control word register
        1    x   x | Chip not selected
    ```

    Control word format (bit 7 = 1 selects I/O mode)
    ```
       D7  D6 D5   D4      D3      D2    D1      D0
       ------------------------------------------------
       1   Mode A  PortA  PortC    Mode  PortB  PortC
           (2 bits) I/O   upper    B     I/O    lower

       D7 = 1  : I/O mode         D7 = 0 : bit set/reset mode
       D6 D5   : 00 = Mode 0 , 01 = Mode 1 , 1x = Mode 2   (Group A)
       D4      : 1 = Port A input   , 0 = output
       D3      : 1 = Port C upper input , 0 = output
       D2      : 0 = Mode 0 , 1 = Mode 1                   (Group B)
       D1      : 1 = Port B input   , 0 = output
       D0      : 1 = Port C lower input , 0 = output
    ```

    Steps to communicate through the 8255
    ```
       1. Interface the chip.
          Connect D0-D7 to the data bus, A0 and A1 to the two lowest address
          lines, RD' and WR' to the control bus, and derive CS' from an address
          decoder. Assign the four port addresses, for example 80H, 81H, 82H, 83H.

       2. RESET.
          On reset all three ports default to INPUT mode. This is deliberate --
          it prevents the chip driving an output into a peripheral before the
          program has decided what the pin should be.

       3. Build the control word.
          Decide the mode and the direction of each port and write down the
          eight bits. Example : Mode 0, Port A output, Port B input,
          Port C output :

             D7 D6 D5 D4 D3 D2 D1 D0
              1  0  0  0  0  0  1  0   = 82H

       4. Write the control word to the control register (address 83H).
          This programs the chip.

       5. Transfer data.
          Read from or write to the port addresses like any I/O location.

       6. Use handshaking if Mode 1 or 2 is selected.
          Port C then supplies the STB', IBF, OBF' and ACK' signals and can
          raise an interrupt to the CPU when the peripheral is ready.
    ```

    Assembly example (8085 / 8086 style)
    ```asm
            MVI  A, 82H        ; control word: A out, B in, C out, Mode 0
            OUT  83H           ; write it to the control register

            MVI  A, 0FFH       ; data to send
            OUT  80H           ; write to Port A  (output)

            IN   81H           ; read from Port B (input)
            MOV  B, A          ; save the value
    ```

    Operating modes
    ```
       Mode 0 : simple I/O, no handshaking. Ports A, B and the two halves of C
                are each independently input or output. The usual choice.
       Mode 1 : handshake I/O. Ports A and B are data ports; Port C supplies
                the handshake and interrupt lines.
       Mode 2 : bidirectional handshake, available on Port A only.
       BSR mode : with D7 = 0, any single bit of Port C can be set or reset
                individually, without disturbing the others.
    ```

    - Practical point worth stating: the `bit set/reset (BSR) mode` writes to the same control register but with D7 = 0, so it does not change the port directions. It is used for toggling a single control line such as a relay or an LED.

12. **What is the function of GPU?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*

    Answer: A `GPU (Graphics Processing Unit)` is a specialised processor with thousands of small cores, built to perform many simple calculations at the same time.

    Original function — graphics rendering
    - `Geometry processing` — transforming 3D vertex coordinates, applying rotation, scaling and perspective projection.
    - `Rasterization` — converting the resulting triangles into pixels on the screen.
    - `Shading and texturing` — computing the colour of every pixel, applying textures, lighting, shadows and reflections. This is the heaviest work, and it is identical for millions of pixels, which is exactly what a GPU is built for.
    - `Frame buffer output` — assembling the finished image and sending it to the display, 60 or more times a second.
    - `Video decoding and encoding` — dedicated hardware blocks for H.264, H.265 and AV1, so video playback costs almost no CPU time.

    Modern function — general-purpose parallel computing (GPGPU)
    - `Deep learning` — training and running a neural network is billions of independent multiply-and-add operations on matrices, which maps perfectly onto a GPU. This is why GPUs became the standard hardware for AI.
    - `Scientific computing` — weather simulation, computational fluid dynamics, molecular dynamics, finite element analysis, genome sequencing.
    - `Image and signal processing` — filtering, convolution, medical image reconstruction.
    - `Cryptography and mining` — hashing is highly parallel.
    - `Physics simulation` in games — cloth, fluid, particle systems.
    - Programmed with `CUDA` (NVIDIA) or `OpenCL` (open standard).

    Why it is good at this
    ```
       CPU : a few powerful cores  -> optimised for LOW LATENCY, one task fast
       GPU : thousands of small cores -> optimised for HIGH THROUGHPUT,
                                         the same operation on many data items

       Adding two arrays of a million elements :
          CPU loops a million times on a few cores
          GPU launches a million threads and runs thousands at once
    ```
    - The model is `SIMD` — Single Instruction, Multiple Data. Its weakness is branching: cores in a group must all execute the same instruction, so heavy `if` logic wastes most of them.

    Types
    ```
       Integrated GPU : inside the CPU package, shares system RAM, low power
       Dedicated GPU  : a separate card with its own fast VRAM, far more powerful
    ```

    - The CPU and GPU work `together`: the CPU runs the operating system and decides what to do, then hands the large uniform number-crunching to the GPU.

13. **Flag Register কী? Intel 8086 Microprocessor-এর Control Flag গুলোর কাজ লিখুন।** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 697 (ET: DPI)]*

    Answer: (Answered in English, as required for IT topics.) A `flag register` is a special register in which each bit is a single-bit indicator that records something about the result of the last operation, or controls how the processor behaves. Later instructions test these bits to make decisions, which is how conditional jumps and loops work.

    The 8086 flag register is `16 bits` wide, of which `9 bits` are used — `6 status flags` and `3 control flags`. The rest are undefined.
    ```
       15 14 13 12 11 10  9  8  7  6  5  4  3  2  1  0
        -  -  -  -  OF DF IF TF SF ZF  - AF  - PF  - CF
                    |  |  |  |
                    |  +--+--+---- control flags
                    +------------- status (overflow)
    ```

    Status flags — set by the ALU after an operation
    ```
       CF (Carry)     : a carry out of, or borrow into, the most significant bit
       PF (Parity)    : 1 if the low byte of the result has an EVEN number of 1s
       AF (Auxiliary) : a carry from bit 3 to bit 4, used in BCD arithmetic
       ZF (Zero)      : 1 if the result is zero
       SF (Sign)      : copies the MSB; 1 means a negative result
       OF (Overflow)  : 1 if a signed result is out of range
    ```

    Control flags — set and cleared by the programmer to control the CPU
    - These three do not report a result; they change how the processor behaves.

    `TF — Trap Flag (bit 8)`
    ```
       TF = 1  ->  the CPU executes ONE instruction and then generates
                   an internal type-1 interrupt (single-step mode)
       TF = 0  ->  normal continuous execution
    ```
    - Purpose: `debugging`. With TF set, a debugger regains control after every single instruction, so the programmer can inspect the registers step by step. This is exactly how a single-step debugger works.
    - It cannot be set by a direct instruction; it is changed by pushing the flags, modifying the bit and popping them back.

    `IF — Interrupt Flag (bit 9)`
    ```
       IF = 1  ->  the CPU RECOGNISES maskable interrupts on the INTR pin
       IF = 0  ->  maskable interrupts are IGNORED

       Instructions :  STI  sets IF = 1     CLI  clears IF = 0
    ```
    - Purpose: to protect a `critical section` of code from being interrupted. A routine that is updating a shared data structure clears IF, finishes the update and sets it again.
    - It has no effect on the `NMI` (non-maskable interrupt) or on software interrupts — those always get through.

    `DF — Direction Flag (bit 10)`
    ```
       DF = 0  ->  string operations move FORWARD; SI and DI are AUTO-INCREMENTED
       DF = 1  ->  string operations move BACKWARD; SI and DI are AUTO-DECREMENTED

       Instructions :  CLD  clears DF = 0     STD  sets DF = 1
    ```
    - Purpose: it controls the direction of the string instructions `MOVS, LODS, STOS, CMPS, SCAS`.
    - It matters when copying `overlapping` memory blocks: copying forward would overwrite bytes that have not yet been read, so the copy is made backward instead.

    Summary of the three control flags

    | Flag | Bit | Set / clear by | Purpose |
    |---|---|---|---|
    | TF (Trap) | 8 | Via the stack | Single-step execution for debugging |
    | IF (Interrupt) | 9 | `STI` / `CLI` | Enable or disable maskable interrupts |
    | DF (Direction) | 10 | `STD` / `CLD` | Direction of string operations |

    - The essential distinction to state: `status flags are set BY the processor to report a result; control flags are set BY the programmer to control the processor.`

14. **What is Microprocessor?** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*

    Answer: A `microprocessor` is a single integrated circuit that contains the complete central processing unit of a computer — the arithmetic logic unit, the control unit and the registers. It fetches instructions from memory, decodes them and executes them, and it is often called the `brain` of the computer.

    - The first one was the `Intel 4004` (1971), a 4-bit chip. Modern examples are the Intel Core i7, AMD Ryzen and the ARM Cortex family.

    Main parts
    ```
            +---------------------------------------+
            |            MICROPROCESSOR             |
            |                                       |
            |   +----------+     +-------------+    |
            |   |   ALU    |     |  Registers  |    |
            |   +----------+     +-------------+    |
            |            \        /                 |
            |          +--------------+             |
            |          | Control Unit |             |
            |          +--------------+             |
            +---------------|-----------------------+
                            |
            Address bus  ---+---  Data bus  ---  Control bus
    ```
    - `ALU` — performs arithmetic (add, subtract, multiply, divide) and logic (AND, OR, NOT, XOR, compare).
    - `Control unit` — decodes each instruction and generates the timing and control signals that make every other part act at the right moment.
    - `Registers` — very fast internal storage: program counter, instruction register, accumulator, general-purpose registers and the flag register.

    How it works — the instruction cycle
    ```
       FETCH   : read the instruction at the address in the program counter
       DECODE  : work out what it means
       EXECUTE : perform the operation
       STORE   : write the result back

       ... and repeat, millions of times per second.
    ```

    Characteristics that describe a microprocessor
    ```
       Word size   : 8, 16, 32 or 64 bits - how much data it handles at once
       Clock speed : in MHz or GHz - how many cycles per second
       Address bus width : decides how much memory it can address
       Instruction set   : RISC or CISC
       Number of cores   : how many independent execution units
       Cache size        : the fast memory built into the chip
    ```

    - It is `general purpose`: it runs an operating system and any program loaded into it, which is why RAM, ROM and I/O chips must be added around it. A `microcontroller`, by contrast, has all of those already on the same chip and runs one fixed embedded program.

15. **Explain four type of register.** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 719 (ET: N/A)]*

    Answer: A `register` is a very small, very fast storage location inside the CPU, used to hold data, addresses and instructions while they are being processed. Registers are the fastest storage in the whole machine, faster even than cache.

    Four main types

    1. Data registers (general-purpose registers)
    - Hold the operands and the results of arithmetic and logical operations.
    - The `accumulator (AX)` is the principal one: the ALU takes one operand from it and usually places the result back in it.
    - In the 8086 these are `AX, BX, CX, DX`, each of which can be used as two 8-bit halves (AH/AL, BH/BL and so on).
    ```
       AX : accumulator, used in arithmetic and I/O
       BX : base register, holds a base address
       CX : counter, used automatically by loops and string instructions
       DX : data register, holds the high word in multiply and divide
    ```

    2. Address registers
    - Hold memory addresses rather than data.
    ```
       Program Counter (PC) / Instruction Pointer (IP)
            holds the address of the NEXT instruction to be fetched;
            incremented automatically, changed by a jump or a call

       Memory Address Register (MAR)
            holds the address currently placed on the address bus

       Stack Pointer (SP)
            points to the top of the stack, used by PUSH, POP, CALL and RET

       Base Pointer (BP), Source Index (SI), Destination Index (DI)
            used for indexed and based addressing, and by string instructions

       Segment registers (CS, DS, SS, ES in the 8086)
            hold the base of the code, data, stack and extra segments
    ```

    3. Instruction register (IR)
    - Holds the instruction that has just been fetched, while the control unit decodes it. The programmer cannot access it.
    - The `Memory Data Register (MDR)` or Memory Buffer Register works with it, holding the data being read from or written to memory.

    4. Status register (flag register / PSW)
    - Each bit records a fact about the last operation, or controls the processor.
    ```
       Status flags : Z (zero) , C (carry) , S (sign) , O (overflow) ,
                      P (parity) , A (auxiliary carry)

       Control flags: I (interrupt enable) , D (direction) , T (trap)
    ```
    - Conditional jumps test these bits, which is how `if` statements and loops are implemented in machine code.

    Summary

    | Type | Purpose | Examples |
    |---|---|---|
    | Data register | Hold operands and results | AX, BX, CX, DX, accumulator |
    | Address register | Hold memory addresses | PC/IP, MAR, SP, BP, SI, DI |
    | Instruction register | Hold the instruction being decoded | IR, MDR |
    | Status register | Record flags and control the CPU | Flag register, PSW |

    - Why registers matter to speed: a register access takes about `one clock cycle`, an L1 cache hit about 4, and a main-memory access more than 200. That is why compilers work so hard to keep the values a program uses most often in registers.

16. **(খ) Typical মাইক্রোকম্পিউটারে কী কী বাস থাকে। একটি মাইক্রোপ্রসেসর এর সাথে RAM, ROM এবং I/O এর কানেকশন বাস এর মাধ্যমে দেখাও।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 777 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) A `bus` is a set of parallel wires that carries signals between the parts of a computer. A typical microcomputer has `three` system buses.

    The three buses

    `Address bus`
    - Carries the `address` of the memory location or I/O port the CPU wants to reach.
    - It is `unidirectional` — only the CPU drives it.
    - Its width fixes how much memory can be addressed:
    ```
       16 lines -> 2^16 = 64 KB
       20 lines -> 2^20 = 1 MB      (8086)
       32 lines -> 2^32 = 4 GB
    ```

    `Data bus`
    - Carries the actual `data` being read or written.
    - It is `bidirectional` — data flows both ways.
    - Its width defines the word size: 8, 16, 32 or 64 bits.

    `Control bus`
    - Carries the `timing and command` signals that say what is to happen and when.
    ```
       RD'   (read)          WR'   (write)
       MEMR' , MEMW'         IOR'  , IOW'
       CLK   (clock)         RESET
       INTR  (interrupt request)   INTA' (interrupt acknowledge)
       HOLD / HLDA           (bus request and grant, for DMA)
       ALE   (address latch enable)
    ```
    - Individual lines are unidirectional, but the bus as a whole carries signals in both directions.

    Connection of a microprocessor to RAM, ROM and I/O
    ```
                        +------------------------+
                        |    MICROPROCESSOR      |
                        +------------------------+
                            |        |       |
         ADDRESS BUS  ======+========+=======+=========================
         (unidirectional)   |        |       |        |        |
                            |        |       |        |        |
         DATA BUS     <=====+========+=======+========+========+======>
         (bidirectional)    |        |       |        |        |
                            |        |       |        |        |
         CONTROL BUS  ------+--------+-------+--------+--------+------
                            |        |       |        |        |
                            v        v       v        v        v
                        +-------+ +-----+ +-----+ +-------+ +-------+
                        | ADDR  | | RAM | | ROM | | Input | |Output |
                        |DECODER| |     | |     | | port  | | port  |
                        +-------+ +-----+ +-----+ +-------+ +-------+
                            |        ^       ^        ^        ^
                            +--------+-------+--------+--------+
                              chip select (CS') lines
    ```

    How a memory read happens
    ```
       1. The CPU puts the address on the ADDRESS bus.
       2. The address decoder compares the high-order bits and asserts the
          CS' of exactly one chip - RAM, ROM or an I/O port.
       3. The CPU asserts MEMR' on the CONTROL bus.
       4. The selected chip places its contents on the DATA bus.
       5. The CPU reads the data bus into a register.
    ```

    Why an address decoder is needed
    - Every device must respond to its own range of addresses only. Without decoding, two chips would drive the data bus at once and the data would be corrupted. The decoder is usually a `3-to-8 decoder (74LS138)` or a small array of gates.

    Other buses in a real computer
    ```
       PCI Express : expansion cards - graphics, network, NVMe SSD
       SATA        : hard disks and optical drives
       USB         : external peripherals
       Memory bus  : between the CPU and RAM
    ```
    - Bus performance is measured by its `width` (bits) and its `clock speed`, whose product is the bandwidth. A wide, fast bus stops a fast CPU from being starved of data.

17. **CPU এর অর্থ কি? এর কয়টি অংশ ও কি কি?** *[BPSC Computer Operator 2021 compact it 780 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) `CPU` stands for `Central Processing Unit`. It is the part of the computer that carries out the instructions of a program — fetching them from memory, decoding them and executing them. It is called the `brain` of the computer.

    It has `three` main parts.

    1. Arithmetic Logic Unit (ALU)
    - Performs all the calculations and comparisons.
    ```
       Arithmetic : ADD, SUB, MUL, DIV, INC, DEC
       Logical    : AND, OR, NOT, XOR
       Comparison : equal, greater than, less than
       Shift      : left, right, rotate
    ```
    - It also sets the `flags` — zero, carry, sign, overflow, parity — which later instructions test.

    2. Control Unit (CU)
    - Directs everything else. It does no computing itself.
    ```
       Fetches the instruction from memory
       Decodes it to find out what is required
       Generates the timing and control signals for the ALU, registers,
           memory and I/O
       Controls the flow of data along the buses
       Handles interrupts
    ```
    - It is the `traffic controller` of the CPU, keeping every unit in step with the clock.

    3. Registers (memory unit of the CPU)
    - Very fast internal storage holding the data and addresses currently in use.
    ```
       Program Counter (PC)      : address of the next instruction
       Instruction Register (IR) : the instruction being decoded
       Accumulator (AC)          : holds ALU operands and results
       MAR / MDR                 : memory address and data buffers
       General-purpose registers : AX, BX, CX, DX
       Flag register             : status bits
    ```

    Block diagram
    ```
         +----------------------------------------------+
         |                    C P U                     |
         |                                              |
         |   +-----------+          +---------------+   |
         |   |    ALU    |<-------->|   Registers   |   |
         |   +-----------+          +---------------+   |
         |          ^                       ^           |
         |          |                       |           |
         |   +------+-----------------------+------+    |
         |   |         Control Unit                |    |
         |   +-------------------------------------+    |
         +--------------------|-------------------------+
                              |
           Address bus  ------+------  Data bus  ------  Control bus
                              |
                      Memory  and  I/O devices
    ```

    How they work together — the instruction cycle
    ```
       1. FETCH   : the CU uses the PC to read the next instruction into the IR
       2. DECODE  : the CU works out what the instruction means
       3. EXECUTE : the CU tells the ALU to operate on data held in registers
       4. STORE   : the result is written back to a register or to memory
       ... then the PC advances and the cycle repeats
    ```

    - Some textbooks count only `two` parts — the ALU and the control unit — treating the registers as belonging to the memory unit. Both answers are accepted; stating all three is safer, as long as the reason is given.

18. **Microprocessor কি? এর আবিষ্কারে তথ্য ও যোগাযোগ প্রযুক্তিতে কি ধরনের অগ্রগতি সাধিত হয়েছে ব্যাখ্যা করুন।** *[DMLC Assistant Teacher (ICT) 2021 compact it 827 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What a microprocessor is
    - A `microprocessor` is a single integrated circuit that contains the complete central processing unit — the ALU, the control unit and the registers. It fetches instructions from memory, decodes them and executes them.
    - The first was the `Intel 4004` in 1971: a 4-bit chip with 2,300 transistors running at 740 kHz. A modern processor has tens of billions of transistors running at several GHz.

    Its parts
    ```
       ALU           : arithmetic and logic operations
       Control unit  : decodes instructions, generates timing signals
       Registers     : PC, IR, accumulator, flags, general purpose
    ```

    Advances it brought to information and communication technology

    `Miniaturisation and the personal computer`
    - Before it, a computer filled a room and cost as much as a building. Putting the whole CPU on one chip made the `personal computer` possible, so computing moved from a few large institutions to every desk and every home.

    `Falling cost, rising power`
    - Moore's law — transistor count doubling roughly every two years — made computing power cheap enough for ordinary people and small businesses. This is the single largest reason ICT spread as fast as it did.

    `The Internet and telecommunications`
    - Routers, switches, modems and base stations are all built around microprocessors. Digital exchanges replaced mechanical ones, and packet switching became practical, which is what made the Internet possible at all.

    `Mobile communication`
    - A modern smartphone is a microprocessor with a radio attached. Mobile banking, mobile money (bKash, Nagad), video calling and messaging all rest on it.

    `Embedded systems everywhere`
    - Microcontrollers — microprocessors with memory and I/O on the same chip — now run washing machines, cars, medical equipment, industrial plants, traffic signals and smart meters. Most processors made today go into embedded systems, not computers.

    `Automation and industry`
    - Programmable logic controllers, CNC machines, robots and process control systems all became possible, raising productivity and consistency in manufacturing.

    `New services and industries`
    - E-governance, online banking, e-commerce, e-learning, telemedicine and digital media — none of them existed before cheap computing.
    - In Bangladesh this underpins the `Digital Bangladesh` programme: national ID, online passport and tax services, and the mobile financial services used by tens of millions.

    `Artificial intelligence and data processing`
    - Modern processors and GPUs made machine learning, big data analysis and cloud computing practical.

    Cost of the advance
    - New risks came with it: `cybercrime`, privacy loss, the `digital divide` between those with access and those without, `electronic waste`, and dependence on foreign chip supply chains.

    - Summary: the microprocessor turned computing from a rare, expensive institutional resource into a cheap component that could be put inside anything. Every later ICT development — the PC, the Internet, the mobile phone, embedded automation and AI — followed from that one change.

19. **8-bit microprocessor and 16-bit microprocessor write the data and address widths?** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 864 (ET: BUET)]*

    Answer: The `data bus width` is how many bits the processor transfers at once. The `address bus width` decides how much memory it can address.
    ```
       Addressable memory = 2^(number of address lines)
    ```

    8-bit microprocessor — for example the Intel 8085
    ```
       Data bus    : 8 bits    (D0 - D7)
       Address bus : 16 bits   (A0 - A15)

       Addressable memory = 2^16 = 65,536 bytes = 64 KB
    ```
    - Registers are 8 bits wide, though pairs can be combined to form 16-bit addresses.
    - The lower 8 address lines are `multiplexed` with the data lines (AD0-AD7) to save pins, and are separated by an external latch using the `ALE` signal.
    - Other 8-bit processors: Intel 8080, Zilog Z80, Motorola 6800.

    16-bit microprocessor — for example the Intel 8086
    ```
       Data bus    : 16 bits   (D0 - D15)
       Address bus : 20 bits   (A0 - A19)

       Addressable memory = 2^20 = 1,048,576 bytes = 1 MB
    ```
    - Registers are 16 bits wide. The 20-bit physical address is formed by the segment mechanism:
    ```
       Physical address = segment register x 16 + offset
    ```
    - Address and data lines are again multiplexed, as AD0-AD15.
    - The related `8088` is internally 16-bit but has only an `8-bit` external data bus, which is why the original IBM PC was cheaper to build.

    Comparison

    | Point | 8-bit (8085) | 16-bit (8086) |
    |---|---|---|
    | Data bus | 8 bits | 16 bits |
    | Address bus | 16 bits | 20 bits |
    | Memory addressable | 64 KB | 1 MB |
    | Register size | 8 bits | 16 bits |
    | Instruction queue | None | 6 bytes |
    | Speed | Slower | Faster |

    Wider processors, for completeness
    ```
       32-bit (80386) : data 32 bits , address 32 bits -> 2^32 = 4 GB
       64-bit (x86-64): data 64 bits , address 48 bits used -> 256 TB in practice
    ```

    - The point to state clearly: the `data bus` decides how much information moves per transfer, and therefore the speed; the `address bus` decides how much memory the processor can reach, and therefore the capacity. The two are independent — the 8085 has an 8-bit data bus but a 16-bit address bus.

20. **What is Microprocessor? Explain basic component of Microprocessor.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 868-869 (ET: N/A)]*

    Answer: A `microprocessor` is a single integrated circuit containing the complete central processing unit of a computer — the arithmetic logic unit, the control unit and the registers. It fetches instructions from memory, decodes them and executes them, and it is often called the brain of the computer.

    Basic components

    1. Arithmetic Logic Unit (ALU)
    - Performs every calculation and comparison.
    ```
       Arithmetic : ADD, SUB, MUL, DIV, INC, DEC
       Logical    : AND, OR, NOT, XOR
       Comparison and shift operations
    ```
    - It is purely combinational — it holds nothing itself; operands come from registers and results go back to them.
    - It also produces the `flags` (zero, carry, sign, overflow, parity) that later instructions test.

    2. Control Unit (CU)
    - Directs every other part but computes nothing itself.
    ```
       Fetches the instruction pointed to by the program counter
       Decodes it to determine the operation and the operands
       Generates the timing and control signals for the ALU, the registers,
           memory and I/O
       Manages the buses and handles interrupts
    ```
    - It may be `hardwired` (fast, used in RISC) or `microprogrammed` (flexible, used in CISC).

    3. Registers
    - Very fast internal storage — one clock cycle to access, against hundreds for main memory.
    ```
       Program Counter (PC)      : address of the next instruction
       Instruction Register (IR) : the instruction currently being decoded
       Accumulator (AC)          : main working register for the ALU
       MAR / MDR                 : memory address and data buffers
       General-purpose registers : AX, BX, CX, DX
       Stack Pointer (SP)        : top of the stack
       Flag register             : status and control bits
    ```

    4. Buses (the internal and external interconnect)
    ```
       Address bus : unidirectional, carries the location
       Data bus    : bidirectional, carries the information
       Control bus : carries read, write, clock, interrupt and reset signals
    ```

    5. Clock and timing circuit
    - Supplies the pulse that synchronises every operation. Its frequency, in GHz, is the clock speed.

    6. Instruction decoder
    - Part of the control unit; translates the opcode into the specific set of control signals needed.

    7. Cache memory (in modern processors)
    - Small, very fast memory built onto the chip, holding recently used instructions and data so the CPU is not forced to wait for main memory.

    Block diagram
    ```
         +-------------------------------------------------+
         |                 MICROPROCESSOR                  |
         |                                                 |
         |  +----------+   +-------------+   +----------+  |
         |  |   ALU    |<->|  Registers  |<->|  Cache   |  |
         |  +----------+   +-------------+   +----------+  |
         |        ^               ^                        |
         |        |               |                        |
         |  +-----+---------------+---------------------+  |
         |  |  Control Unit  +  Instruction Decoder     |  |
         |  +--------------------------------------------+ |
         |                     ^                           |
         |                  Clock                          |
         +---------------------|---------------------------+
                               |
         Address bus  ---------+------- Data bus ------- Control bus
                               |
                        Memory and I/O devices
    ```

    Working — the instruction cycle
    ```
       FETCH   : the CU uses the PC to read the next instruction into the IR
       DECODE  : the instruction decoder works out what is required
       EXECUTE : the ALU performs the operation on register data
       STORE   : the result is written back, and the PC advances
    ```

    - Characteristics used to describe a microprocessor: `word size` (8, 16, 32, 64 bits), `clock speed`, `address bus width`, `instruction set` (RISC or CISC), `number of cores` and `cache size`.

21. **Difference between Microprocessor and Microcontroller.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 870 (ET: N/A)]*

    Answer: A `microprocessor` contains only the CPU. A `microcontroller` contains the CPU together with memory, I/O ports and timers, all on one chip.

    Microprocessor
    - Holds the ALU, control unit and registers, and nothing else.
    - RAM, ROM, I/O ports and timers must all be added as separate chips on the board.
    - General purpose: it runs an operating system and any program loaded into it.
    - Examples: Intel Core i7, AMD Ryzen, Intel 8085, 8086.

    Microcontroller
    - A complete small computer on one chip — CPU, RAM, Flash/ROM, I/O ports, timers, ADC and serial interfaces.
    - Designed for a single embedded task, running one fixed program.
    - Examples: Intel 8051, ATmega328 (Arduino), PIC, ARM Cortex-M, ESP32.

    ```
       Microprocessor system              Microcontroller
       +-------+  +-----+  +-----+        +---------------------+
       |  CPU  |--| RAM |--| ROM |        |  CPU + RAM + ROM    |
       +-------+  +-----+  +-----+        |  + I/O + Timer +ADC |
           |         |        |           +---------------------+
       +-------+  +-------+               all on ONE chip
       |  I/O  |  | Timer |
       +-------+  +-------+
       several chips on a large board
    ```

    Difference

    | Point | Microprocessor | Microcontroller |
    |---|---|---|
    | Contents | CPU only | CPU + RAM + ROM + I/O + timers |
    | External components | Many required | Few or none |
    | System cost | High | Low |
    | Board size | Large | Very small |
    | Power consumption | Watts | Milliwatts |
    | Clock speed | GHz | MHz |
    | Memory capacity | Gigabytes | Kilobytes |
    | Architecture | Von Neumann | Harvard (separate code and data memory) |
    | Instruction set | Usually CISC | Usually RISC |
    | Purpose | General purpose | One dedicated task |
    | Operating system | Windows, Linux | Bare metal or an RTOS |
    | Real-time response | Not guaranteed | Precise and predictable |
    | Bit manipulation | Limited | Strong — individual pins addressable |
    | Used in | PC, laptop, server | Washing machine, car ECU, IoT device |

    - The clearest one-line statement: a `microprocessor is the brain alone and needs a body built around it`, while a `microcontroller is brain plus body on a single chip`.
    - Which to choose: a microcontroller when the job is fixed, small, low-power and must respond in real time; a microprocessor when the job needs large memory, an operating system and general-purpose flexibility.

22. **Central Processing Unit (CPU) -এর প্রধান কাজ কী? একটি চিত্রের সাহায্যে CPU-এর বিভিন্ন অংশ বর্ণনা করুন?** *[41th BCS 2021 compact it 884 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Main function of the CPU
    - The `Central Processing Unit` executes the instructions of a program. It repeatedly `fetches` an instruction from memory, `decodes` it, `executes` it and `stores` the result — the instruction cycle.
    ```
       FETCH  ->  DECODE  ->  EXECUTE  ->  STORE   , repeated continuously
    ```
    - In doing so it performs all the arithmetic and logic, controls the flow of data between memory and I/O, generates the timing signals for the whole machine, and handles interrupts.

    The parts of the CPU

    1. Arithmetic Logic Unit (ALU)
    ```
       Arithmetic : ADD, SUB, MUL, DIV, INC, DEC
       Logical    : AND, OR, NOT, XOR
       Comparison and shift operations
    ```
    - It also sets the `flags` — zero, carry, sign, overflow, parity — which later instructions test to make decisions.

    2. Control Unit (CU)
    - The director of the CPU. It performs no calculation itself.
    ```
       Fetches each instruction using the program counter
       Decodes it into the operation and the operands required
       Issues timing and control signals to the ALU, registers, memory and I/O
       Controls the address, data and control buses
       Handles interrupts
    ```

    3. Registers
    - The fastest storage in the machine, holding what is being worked on right now.
    ```
       Program Counter (PC)      : address of the next instruction
       Instruction Register (IR) : the instruction being decoded
       Accumulator (AC)          : working register for the ALU
       MAR / MDR                 : memory address and data buffers
       General-purpose registers : AX, BX, CX, DX
       Flag register             : status and control bits
    ```

    4. Cache (in modern CPUs)
    - Small very fast memory on the chip, holding recently used instructions and data so the CPU need not wait for main memory.

    Diagram
    ```
         +-------------------------------------------------+
         |                     C P U                       |
         |                                                 |
         |   +-----------+          +---------------+      |
         |   |    ALU    |<-------->|   Registers   |      |
         |   +-----------+          +---------------+      |
         |         ^                        ^              |
         |         |                        |              |
         |   +-----+------------------------+----------+   |
         |   |            Control Unit                 |   |
         |   +-----------------------------------------+   |
         +---------------------|---------------------------+
                               |
         Address bus  ---------+------- Data bus ------- Control bus
                               |
                  +------------+------------+
                  |                         |
              Main memory              I/O devices
    ```

    ```mermaid
    flowchart LR
        M[Main memory] -->|instruction| CU[Control Unit]
        CU -->|control signals| ALU
        R[Registers] <--> ALU
        CU --> R
        ALU -->|result| R
        R -->|data| M
    ```

    How the parts cooperate
    ```
       1. The CU reads the address in the PC and fetches the instruction into the IR.
       2. The CU decodes it and identifies the operands.
       3. The operands are loaded into registers, from memory if necessary.
       4. The CU signals the ALU, which performs the operation.
       5. The result goes back to a register or to memory, and the flags are set.
       6. The PC advances, and the cycle repeats.
    ```

    - Performance depends on `clock speed x instructions per cycle x number of cores`, and on how well the cache keeps the ALU supplied with data.

23. **When does the parity bit occur in the microprocessors? What does it do?** *[SGFL Assistant General Engineer 2021 compact it 937 (ET: BUET)]*

    Answer: The `parity bit` (PF) is one of the status flags in the flag register. It reports whether the result of the last operation contains an `even` or an `odd` number of 1 bits.

    When it is set
    - After every `arithmetic or logical` operation performed by the ALU — ADD, SUB, AND, OR, XOR, CMP, INC, DEC and so on. It is not set by data-move instructions such as `MOV`.
    ```
       PF = 1  ->  the result has an EVEN number of 1 bits    (even parity)
       PF = 0  ->  the result has an ODD  number of 1 bits    (odd parity)
    ```
    - In the Intel 8086 and 8085, the parity flag looks only at the `low-order 8 bits` of the result, even when the operation is 16-bit. This is a detail examiners like.

    Examples
    ```
       Result = 0000 0011   ->  two 1s   -> even -> PF = 1
       Result = 0000 0111   ->  three 1s -> odd  -> PF = 0
       Result = 1010 1010   ->  four 1s  -> even -> PF = 1
       Result = 0000 0000   ->  zero 1s  -> even -> PF = 1  (and ZF = 1 too)
    ```

    What it does
    - `Error detection in data communication.` The processor computes the parity of a byte and appends it as a ninth bit before transmitting. The receiver recomputes it; a mismatch means the byte was corrupted in transit. This is the classic use, in serial ports and modems.
    - `Memory error checking.` Parity RAM stores one extra bit per byte, and the memory controller checks it on every read. A parity error signals corrupted memory.
    - `Conditional branching.` The programmer can test it directly:
    ```
       JP  / JPE   jump if parity even  (PF = 1)
       JNP / JPO   jump if parity odd   (PF = 0)
    ```
    - `Counting bits` — used in some algorithms as a fast way to know the parity of a byte without counting manually.

    How it is generated in hardware
    - By XOR-ing all the bits of the result together. An even number of 1s gives 0 from the XOR chain, which is inverted to give PF = 1.
    ```
       D7 --|\
            | ))--+
       D6 --|/    |
                  +--|\
       D5 --|\    |  | ))o--- PF
            | ))--+  |/
       D4 --|/       (chain of XOR gates, then an inverter)
       ...
    ```

    Limitation
    - Parity detects `any odd number` of bit errors but misses an `even` number. If two bits flip, the parity is unchanged and the error goes unnoticed. It also cannot say `which` bit was wrong, so it cannot correct anything.
    - Stronger schemes are used where that matters: `CRC` for communication and `Hamming code` or `ECC` for memory, which can correct a single-bit error and detect a double-bit one.

    - The other status flags for comparison: `ZF` (result is zero), `CF` (carry out of the MSB), `SF` (sign, copies the MSB), `OF` (signed overflow) and `AF` (auxiliary carry, used in BCD arithmetic).

24. **১২. 8086 মাইক্রোপ্রসেসর এর Flag Register কত বিটের?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 942 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The flag register of the Intel 8086 is `16 bits` wide.

    - Of those 16 bits, only `9` are actually used — `6 status flags` and `3 control flags`. The remaining 7 bits are undefined and reserved.
    ```
       Bit  15 14 13 12 11 10  9  8  7  6  5  4  3  2  1  0
             -  -  -  -  OF DF IF TF SF ZF  - AF  - PF  - CF
    ```

    Status flags — set by the ALU to report the result
    ```
       CF (bit 0)  Carry     : a carry out of, or borrow into, the MSB
       PF (bit 2)  Parity    : 1 if the low byte has an EVEN number of 1s
       AF (bit 4)  Auxiliary : carry from bit 3 to bit 4, used in BCD arithmetic
       ZF (bit 6)  Zero      : 1 if the result is zero
       SF (bit 7)  Sign      : copies the MSB; 1 means negative
       OF (bit 11) Overflow  : 1 if a signed result is out of range
    ```

    Control flags — set by the programmer to control the CPU
    ```
       TF (bit 8)  Trap      : 1 puts the CPU in single-step mode, for debugging
       IF (bit 9)  Interrupt : 1 enables maskable interrupts (STI / CLI)
       DF (bit 10) Direction : 0 = forward, 1 = backward for string instructions
                               (CLD / STD)
    ```

    - The register is also called the `PSW` (Program Status Word). It is saved on the stack by `PUSHF` and restored by `POPF`, and it is pushed automatically whenever an interrupt occurs, so the flags survive the interrupt service routine.
    - For comparison, the `8085` has an 8-bit flag register with only 5 flags: S, Z, AC, P and CY.

25. **What is Register? Write down the name of 5 CPU Register.** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1018 (ET: N/A)]*

    Answer: A `register` is a very small, very fast storage location inside the CPU, used to hold data, addresses and instructions while they are being processed. A register access takes about one clock cycle, against hundreds for main memory, which is why registers exist at all.

    Names of five CPU registers

    1. Program Counter (PC), also called the Instruction Pointer (IP)
    - Holds the `address of the next instruction` to be fetched.
    - It is incremented automatically after each fetch, and loaded with a new value by a jump, branch, call or interrupt.

    2. Instruction Register (IR)
    - Holds the `instruction that has just been fetched`, while the control unit decodes it.
    - Not accessible to the programmer; it is used only inside the fetch-decode cycle.

    3. Accumulator (AC / AX)
    - The main `working register` for the ALU. One operand is usually taken from it and the result is usually placed back in it.
    - Used heavily in arithmetic, logic and I/O operations.

    4. Memory Address Register (MAR) and Memory Data Register (MDR)
    - `MAR` holds the address currently placed on the address bus.
    - `MDR` (also called the Memory Buffer Register) holds the data being read from or written to that address.
    - Together they are the CPU's interface to memory.

    5. Flag Register (Status register / PSW)
    - Each bit records a fact about the last operation, or controls the processor.
    ```
       Status : Z (zero) , C (carry) , S (sign) , O (overflow) ,
                P (parity) , A (auxiliary carry)
       Control: I (interrupt enable) , D (direction) , T (trap)
    ```
    - Conditional jumps test these bits, which is how `if` statements and loops are implemented in machine code.

    Others worth naming
    ```
       Stack Pointer (SP)     : points to the top of the stack, used by
                                PUSH, POP, CALL and RET
       Base Pointer (BP)      : points to the current stack frame
       General-purpose (BX, CX, DX) : hold operands, counters and addresses
       Index registers (SI, DI)     : used by string and array operations
       Segment registers (CS, DS, SS, ES) : segment base addresses in the 8086
    ```

    Classification

    | Type | Purpose | Examples |
    |---|---|---|
    | Data register | Hold operands and results | Accumulator, AX, BX, CX, DX |
    | Address register | Hold memory addresses | PC, MAR, SP, BP, SI, DI |
    | Instruction register | Hold the current instruction | IR |
    | Status register | Record flags | Flag register, PSW |

    - Why they matter to performance: register access is roughly `200 times` faster than a main-memory access, which is why a compiler's most important optimisation is keeping the values a program uses most often in registers rather than in memory.

26. **(b) What is DMA? Why it is used for high-speed I/O devices?** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1025-1026 (ET: N/A)]*

    Answer: What DMA is
    - `DMA (Direct Memory Access)` is a technique that lets an I/O device transfer data `directly to or from main memory` without the CPU handling each byte.
    - A separate chip called the `DMA controller (DMAC)` takes over the buses and performs the transfer while the CPU gets on with other work.

    How it works
    ```mermaid
    sequenceDiagram
        participant IO as I/O Device
        participant DMAC as DMA Controller
        participant CPU
        participant MEM as Memory
        CPU->>DMAC: 1. Initialise (source, destination, count, direction)
        IO->>DMAC: 2. DMA request (DREQ)
        DMAC->>CPU: 3. HOLD - request the bus
        CPU->>DMAC: 4. HLDA - bus granted, CPU floats its buses
        DMAC->>MEM: 5. Transfer data directly, word by word
        DMAC->>CPU: 6. Interrupt when the count reaches zero
    ```
    ```
       1. The CPU programs the DMAC with the memory address, the byte count
          and the direction of transfer.
       2. The device raises DREQ when it is ready.
       3. The DMAC asserts HOLD to ask the CPU for the buses.
       4. The CPU finishes its current cycle, tri-states the address, data
          and control buses, and replies with HLDA.
       5. The DMAC drives the buses itself and moves the data straight
          between the device and memory.
       6. When the count reaches zero the DMAC interrupts the CPU to say
          the transfer is complete, and releases the buses.
    ```

    Modes of transfer
    ```
       Burst (block) mode : the DMAC keeps the bus until the whole block is
                            moved. Fastest, but the CPU is stalled meanwhile.
       Cycle stealing     : one word per bus acquisition; the CPU runs between
                            transfers. Slower, but the CPU is not starved.
       Transparent mode   : the DMAC transfers only in cycles the CPU is not
                            using the bus. No CPU slowdown at all, but slowest.
    ```

    Why DMA is used for high-speed I/O devices
    - `It removes the per-byte CPU cost.` Under `programmed I/O` the CPU executes several instructions for every single byte — read the status, test it, read the data, store it, increment the pointer, loop. For a 100 MB file that is hundreds of millions of instructions spent purely on copying.
    - `Interrupt-driven I/O is not enough either.` It avoids busy-waiting, but the CPU still runs an interrupt service routine for every byte or word, and the context switch alone costs more time than the transfer.
    - `Speed.` The DMAC moves a word per bus cycle with no instruction fetch, decode or execute overhead. It is far faster than any software loop.
    - `The CPU is freed for real work.` During a disk transfer the CPU can run other processes, which is exactly what multiprogramming needs.
    - `It matches the device's data rate.` A hard disk, an SSD, a network card or a graphics card produces data continuously at tens or hundreds of megabytes per second. A software loop cannot keep up, and data would be lost.
    - `Block-oriented devices suit it.` Disks and network cards move data in blocks of hundreds or thousands of bytes to consecutive memory addresses — precisely the pattern DMA is built for.
    - `Lower power`, because dedicated hardware doing one job uses far less energy than a general-purpose CPU running a copy loop.

    Comparison of the three I/O methods

    | Point | Programmed I/O | Interrupt-driven I/O | DMA |
    |---|---|---|---|
    | CPU involvement | Continuous polling | Once per byte or word | Once per block |
    | Speed | Slowest | Medium | Fastest |
    | CPU free during transfer | No | Partly | Yes |
    | Extra hardware | None | Interrupt controller | DMA controller |
    | Suited to | Slow devices (keyboard) | Moderate devices | Disk, network, graphics |

    - One complication worth mentioning: because the DMAC writes to memory behind the CPU's back, the CPU's `cache` may hold stale copies of those locations. Systems solve this with cache-coherency hardware or by marking DMA buffers as non-cacheable.

27. **Microcontroller এবং Microprocessor এর মধ্যে Hardware Related পার্থক্য গুলো লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1041 (ET: DPI)]*

    Answer: (Answered in English, as required for IT topics.) The hardware differences all follow from one fact: a `microprocessor` is only a CPU, while a `microcontroller` has the CPU plus memory, I/O and timers on the same chip.

    1. What is inside the chip
    ```
       Microprocessor : ALU + control unit + registers only

       Microcontroller: ALU + control unit + registers
                        + RAM
                        + ROM / Flash program memory
                        + I/O ports
                        + timers and counters
                        + ADC / DAC
                        + serial interfaces (UART, SPI, I2C)
                        + interrupt controller and watchdog timer
    ```

    2. External components needed
    - A microprocessor system needs separate RAM chips, ROM chips, an I/O interface such as the 8255, a timer such as the 8253 and an address decoder. The board is large and has many chips.
    - A microcontroller usually needs nothing more than a crystal, a few capacitors and a power supply.

    3. Bus structure
    - A microprocessor brings its `address, data and control buses out to the pins`, because it must reach external memory. Many pins are therefore taken up by buses.
    - A microcontroller keeps its buses `inside the chip`, so almost all its pins are available as general-purpose I/O.

    4. Memory architecture
    ```
       Microprocessor : von Neumann - one memory holds both code and data
       Microcontroller: Harvard - separate program and data memory, with
                        separate buses, so an instruction and its data can be
                        fetched in the same cycle
    ```

    5. Memory size
    ```
       Microprocessor : gigabytes of external RAM
       Microcontroller: kilobytes of on-chip RAM (a few hundred bytes to 512 KB)
    ```

    6. Clock speed and power
    ```
       Microprocessor : GHz , watts , needs a heat sink and a fan
       Microcontroller: MHz , milliwatts , no cooling at all, and sleep modes
                        down to microamperes
    ```

    7. Pin count and package
    - A microprocessor has hundreds or thousands of pins in a large LGA or BGA package that must sit in a socket.
    - A microcontroller may have 8 to 100 pins in a small DIP or QFP package soldered straight to the board.

    8. Cost and board size
    ```
       Microprocessor system : expensive, large multi-chip board
       Microcontroller       : a few dollars or less, a board the size of a stamp
    ```

    Summary

    | Hardware point | Microprocessor | Microcontroller |
    |---|---|---|
    | On-chip memory | None | RAM + Flash/ROM |
    | On-chip I/O ports | None | Yes, several |
    | On-chip timers, ADC | None | Yes |
    | Buses | Brought out to pins | Internal |
    | Architecture | Von Neumann | Harvard |
    | External chips needed | Many | Few or none |
    | Pins usable as I/O | Very few | Almost all |
    | Clock | GHz | MHz |
    | Power | Watts | Milliwatts |
    | Cooling | Heat sink and fan | None |
    | Board size | Large | Very small |
    | Cost of the system | High | Low |
    | Examples | Intel Core i7, 8086 | 8051, ATmega328, PIC, ARM Cortex-M |

    - One line for the exam: the microprocessor is `a CPU that needs a system built around it`, and the microcontroller is `a whole system already on one chip`.

28. **(ক) System bus কী? বিভিন্ন প্রকার System bus সম্পর্কে সচিত্র আলোচনা করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1076 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) A `system bus` is the set of parallel conducting lines that carries information between the CPU, memory and I/O devices. It is the shared communication path of the whole computer.

    - Only one device may drive the bus at a time, so an `arbitration` mechanism decides who gets it. All other devices keep their outputs in the high-impedance (tri-state) condition.

    The three types of system bus

    1. Address bus
    - Carries the `address` of the memory location or I/O port the CPU wants to reach.
    - `Unidirectional` — only the CPU (or a DMA controller) drives it.
    - Its width fixes the addressable memory:
    ```
       16 lines -> 2^16 = 64 KB      (8085)
       20 lines -> 2^20 = 1 MB       (8086)
       32 lines -> 2^32 = 4 GB
    ```

    2. Data bus
    - Carries the `actual information` being read or written.
    - `Bidirectional` — data flows both to and from the CPU.
    - Its width is the word size: 8, 16, 32 or 64 bits. A wider data bus moves more per cycle, so the machine is faster.

    3. Control bus
    - Carries the `command and timing` signals that say what is to happen and when.
    ```
       RD'  , WR'          read and write
       MEMR', MEMW'        memory read and write
       IOR' , IOW'         I/O read and write
       CLK                 clock, synchronises everything
       RESET               initialise the system
       INTR , INTA'        interrupt request and acknowledge
       HOLD , HLDA         DMA bus request and grant
       ALE                 address latch enable
       READY               inserts wait states for slow devices
    ```
    - Individual lines are unidirectional, but the bus as a whole carries signals both ways.

    Diagram
    ```
                        +------------------------+
                        |          CPU           |
                        +------------------------+
                            |        |       |
         ADDRESS BUS  ======+========+=======+============================>
         (unidirectional)   |        |       |        |         |
                            |        |       |        |         |
         DATA BUS     <=====+========+=======+========+=========+========>
         (bidirectional)    |        |       |        |         |
                            |        |       |        |         |
         CONTROL BUS  ------+--------+-------+--------+---------+-------->
                            |        |       |        |         |
                            v        v       v        v         v
                         +-----+ +-----+ +-------+ +-------+ +-------+
                         | RAM | | ROM | | Input | |Output | |  DMA  |
                         +-----+ +-----+ +-------+ +-------+ +-------+
    ```

    ```mermaid
    flowchart LR
        CPU -->|address| MEM[Memory]
        CPU -->|address| IO[I/O devices]
        CPU <-->|data| MEM
        CPU <-->|data| IO
        CPU -->|control| MEM
        CPU -->|control| IO
    ```

    A memory read, step by step
    ```
       1. The CPU places the address on the ADDRESS bus.
       2. The address decoder asserts the chip-select of exactly one device.
       3. The CPU asserts MEMR' on the CONTROL bus.
       4. The selected chip drives the DATA bus with its contents.
       5. The CPU latches the data into a register.
    ```

    Other buses in a modern computer
    ```
       Internal (CPU) bus : between the ALU, registers and control unit
       Memory bus         : CPU to RAM
       PCI Express        : graphics cards, NVMe SSDs, network cards
       SATA               : hard disks and optical drives
       USB                : external peripherals
    ```

    - Bus performance is `width x clock speed = bandwidth`. A narrow or slow bus becomes the bottleneck of the whole machine, which is why the bus is often the limiting factor rather than the CPU itself.

29. **In an arithmetic operation the result has even number of 1s and for another operation the result is zero. Now write the the present status of the flag register.** *[DESCO Sub-Assistant Engineer (CSE) 2019 compact it 1120-1121 (ET: BUET)]*

    Answer: The question describes `two separate operations`, so the flags must be read for each. The flag register concerned is the 8085/8086 status set.
    ```
       Z  (Zero)     = 1 if the result is zero
       P  (Parity)   = 1 if the result has an EVEN number of 1 bits
       S  (Sign)     = 1 if the result is negative (MSB = 1)
       CY (Carry)    = 1 if a carry came out of the MSB
       AC (Auxiliary): carry from bit 3 to bit 4
       OV (Overflow) : signed overflow
    ```

    Operation 1 — the result has an even number of 1s
    ```
       Parity flag  P  = 1        even number of 1s -> parity EVEN -> PF = 1

       Zero flag    Z  = 0        the result is non-zero (it contains some 1s)
       Sign flag    S  = depends on the MSB of that result
       Carry flag   CY = depends on the operation
    ```
    - Example: result `0000 0011` has two 1s.
    ```
       P = 1  ,  Z = 0  ,  S = 0
    ```

    Operation 2 — the result is zero
    ```
       Result = 0000 0000

       Zero flag    Z  = 1        the result is zero
       Parity flag  P  = 1        zero has NO 1 bits, and 0 counts as EVEN
       Sign flag    S  = 0        MSB is 0, so the result is positive
       Carry flag   CY = 0        (unless the operation itself produced a carry,
                                   for example FFH + 01H = 00H with CY = 1)
       Auxiliary AC = 0
    ```

    Combined status

    | Flag | Operation 1 (even number of 1s) | Operation 2 (result is zero) |
    |---|---|---|
    | Z (Zero) | 0 | `1` |
    | P (Parity) | `1` | `1` |
    | S (Sign) | 0 (assuming a positive result) | 0 |
    | CY (Carry) | 0 | 0 |
    | AC (Auxiliary) | 0 | 0 |

    Flag register content for operation 2, in the 8085 layout
    ```
       Bit  7  6  5  4  3  2  1  0
            S  Z  -  AC -  P  -  CY
            0  1  0  0  0  1  0  0     = 44H
    ```

    Points worth stating
    - A zero result always sets `both Z and P`, because zero contains no 1 bits and zero is an even count. This is the key observation the question is testing.
    - The carry flag is the one exception that can still be 1 with a zero result: `FFH + 01H = 00H` sets `Z = 1` and `CY = 1` together.
    - These flags are what conditional jumps test — `JZ` (jump if zero), `JNZ`, `JPE` (jump if parity even), `JPO`, `JC`, `JNC` — which is how loops and `if` statements are built in machine code.

30. **Explain the functions of ALU and Control Unit of a Computer.** *[Multiple Ministry Assistant Programmer 2017 compact it 1229 (ET: N/A)]*

    Answer: The `ALU` and the `control unit` are the two working parts of the CPU. The ALU does the computing; the control unit decides what is computed and when.

    Functions of the Arithmetic Logic Unit (ALU)
    - `Arithmetic operations` — addition, subtraction, multiplication, division, increment and decrement. Subtraction reuses the adder, since `A - B = A + (2's complement of B)`.
    - `Logical operations` — AND, OR, NOT, XOR, used for masking, setting and testing individual bits.
    - `Comparison` — testing whether two values are equal, greater or less. This is done by subtracting and examining the flags.
    - `Shift and rotate` — moving bits left or right, which also multiplies or divides by powers of two.
    - `Setting the status flags` from the result:
    ```
       Z (zero) , C (carry) , S (sign) , O (overflow) , P (parity) , A (auxiliary)
    ```
    - It is purely `combinational` — it stores nothing. Operands come from registers and results go straight back to them.
    ```
          Operand A        Operand B
              |                |
              v                v
          +----------------------------+
          |            ALU             |<--- opcode from the control unit
          +----------------------------+
              |                |
              v                v
            Result          Flags
    ```

    Functions of the Control Unit (CU)
    - `Fetch` — read the next instruction from memory, using the address in the program counter, and place it in the instruction register.
    - `Decode` — interpret the opcode to determine the operation, the operands and the addressing mode.
    - `Generate control signals` — issue the exact sequence of enable, select and timing pulses that make the ALU, the registers, memory and the I/O units act in the right order.
    - `Sequence and timing` — keep every unit in step with the clock, and insert wait states for slow devices.
    - `Control the data flow` — decide what travels along the internal buses and when, and manage the address, data and control buses.
    - `Control program flow` — implement jumps, branches, loops, calls and returns by changing the program counter.
    - `Handle interrupts` — save the current state, transfer control to the service routine, and restore afterwards.
    - It performs `no calculation of its own`; it is the traffic controller of the CPU.

    Two ways a control unit is built
    ```
       Hardwired    : fixed logic gates and a sequencer.
                      Fast, but hard to modify. Used in RISC designs.

       Microprogrammed : each machine instruction is a small program of
                      microinstructions held in control memory.
                      Slower, but flexible. Used in CISC designs.
    ```

    How they work together
    ```
       1. CU fetches the instruction  ADD A, B
       2. CU decodes it and sees that an addition is required
       3. CU tells the registers to place A and B on the ALU inputs
       4. CU sends the ADD opcode to the ALU
       5. ALU computes the sum and sets the flags
       6. CU tells the accumulator to latch the result
       7. CU advances the program counter and repeats
    ```

    | Point | ALU | Control Unit |
    |---|---|---|
    | Role | Performs the operation | Directs the operation |
    | Type of circuit | Combinational | Sequential |
    | Input | Two operands and an opcode | The instruction from the IR |
    | Output | Result and flags | Control and timing signals |
    | Does calculation | Yes | No |

    - Together with the `registers`, these two make up the CPU. The ALU is the workshop, the control unit is the supervisor, and the registers are the workbench.

31. **Difference between microprocessor and micro-controller.** *[Multiple Ministry Assistant Programmer 2017 compact it 1233 (ET: N/A)]*

    Answer: A `microprocessor` contains only the CPU — the ALU, control unit and registers. A `microcontroller` contains the CPU together with memory, I/O ports and timers on the same chip.

    Microprocessor
    - RAM, ROM, I/O ports and timers must all be added as separate chips on the board.
    - General purpose: it runs an operating system and any program loaded into it, so it needs large memory and a high clock speed.
    - Examples: Intel 8085, 8086, Core i7, AMD Ryzen.

    Microcontroller
    - A complete small computer on one chip — CPU, RAM, Flash, I/O ports, timers, ADC and serial interfaces.
    - Built for one dedicated embedded task, running a single fixed program.
    - Examples: Intel 8051, ATmega328, PIC, ARM Cortex-M, ESP32.

    ```
       Microprocessor system              Microcontroller
       +-------+  +-----+  +-----+        +----------------------+
       |  CPU  |--| RAM |--| ROM |        | CPU + RAM + ROM      |
       +-------+  +-----+  +-----+        | + I/O + Timer + ADC  |
           |         |        |           +----------------------+
       +-------+  +-------+                  all on ONE chip
       |  I/O  |  | Timer |
       +-------+  +-------+
    ```

    Difference

    | Point | Microprocessor | Microcontroller |
    |---|---|---|
    | Contents | CPU only | CPU + RAM + ROM + I/O + timers |
    | External components | Many required | Few or none |
    | System cost | High | Low |
    | Board size | Large | Very small |
    | Power consumption | Watts | Milliwatts |
    | Clock speed | GHz | MHz |
    | Memory | Gigabytes | Kilobytes |
    | Architecture | Von Neumann | Harvard |
    | Instruction set | Usually CISC | Usually RISC |
    | Buses | Brought out to pins | Internal |
    | Real-time response | Not guaranteed | Precise and predictable |
    | Operating system | Windows, Linux | Bare metal or an RTOS |
    | Purpose | General purpose | One dedicated task |
    | Used in | PC, laptop, server | Washing machine, car ECU, IoT device |

    - The clearest one-line statement: a `microprocessor is the brain alone and needs a body built around it`; a `microcontroller is brain plus body already on a single chip`.

32. **Write down the necessary components of a USB bus with block diagram.** *[ICT Ministry Assistant Programmer 2017 compact it 1237 (ET: N/A)]*

    Answer: `USB` (Universal Serial Bus) is a serial interface standard for connecting peripherals to a computer. It provides both `data` and `power` over one cable and supports `hot plugging` and `plug and play`.

    Necessary components of a USB system

    1. USB Host
    - The computer, which controls the whole bus. There is exactly `one` host per USB system.
    - Contains the `host controller` hardware and the software stack. It is the only device that can initiate a transfer — devices never speak unless asked.
    - Its jobs: detect attachment and removal, assign each device a 7-bit address, enumerate and configure devices, schedule all traffic, and manage power.

    2. USB Hub
    - Expands one port into several. The `root hub` is inside the host controller; external hubs can be chained up to `5 tiers` deep, with a maximum of `127 devices` on one bus.
    - Detects attachment and removal on its downstream ports and reports it to the host, and distributes power.

    3. USB Device (function)
    - The peripheral: keyboard, mouse, printer, camera, pen drive, external disk.
    ```
       Bus powered  : takes power from the cable (up to 500 mA at USB 2.0,
                      900 mA at USB 3.0, far more with USB-C Power Delivery)
       Self powered : has its own supply
    ```
    - Each device contains `endpoints` — buffers that are the real source and destination of data — grouped into `pipes` between the host and the device.

    4. USB Cable and connectors
    ```
       USB 2.0 cable : 4 wires
            VBUS  (+5 V)     GND        D+  and  D-  (differential data pair)

       USB 3.x adds 5 more wires for two SuperSpeed differential pairs
       USB-C : 24 pins, reversible, supports up to 100 W and alternate modes
    ```
    - The differential pair gives good noise immunity; the maximum cable length is 5 m for USB 2.0 and 3 m for USB 3.0.

    5. USB Controller and software stack
    ```
       Host controller (xHCI / EHCI / OHCI) : the hardware that drives the bus
       Host controller driver               : lowest software layer
       USB core driver                      : enumeration, addressing, scheduling
       Class drivers (HID, mass storage, audio, CDC) : per device type
       Application
    ```

    Block diagram
    ```
       +--------------------------------------------+
       |                  HOST (PC)                 |
       |   +----------------+   +---------------+   |
       |   | Application    |   | Class drivers |   |
       |   +----------------+   +---------------+   |
       |   | USB core driver / host controller  |   |
       |   +------------------------------------+   |
       |   |     Host Controller + Root Hub     |   |
       +---+------------------------------------+---+
                        |            |
                  +-----+            +--------+
                  |                           |
            +-----------+              +-------------+
            | USB Hub   |              |  Device     |
            +-----------+              | (keyboard)  |
              |       |                +-------------+
         +--------+ +--------+
         | Device | | Device |
         | (mouse)| |(pendrive)
         +--------+ +--------+
    ```

    Four transfer types
    ```
       Control     : setup and configuration commands. Guaranteed, used at
                     enumeration.
       Bulk        : large, error-free but not time-critical data.
                     Printers, pen drives, external disks.
       Interrupt   : small, low-latency, polled at a guaranteed interval.
                     Keyboard, mouse.
       Isochronous : guaranteed bandwidth, no retransmission.
                     Audio and video, where being on time matters more
                     than being perfect.
    ```

    Speeds
    ```
       USB 1.1 : 1.5 Mbps (Low) , 12 Mbps (Full)
       USB 2.0 : 480 Mbps (High Speed)
       USB 3.0 : 5 Gbps        USB 3.1 : 10 Gbps
       USB 3.2 : 20 Gbps       USB4    : 40 Gbps
    ```

    - Why USB replaced the old serial and parallel ports: one standard connector for every device, hot pluggable, self-configuring, supplies power, and up to 127 devices on one bus instead of one device per dedicated port.

33. **a) Describe the central processing parts of a computer with a diagram.** *[Ministry of Finance Programmer 2013 compact it 1270 (ET: N/A)]*

    Answer: The `central processing unit (CPU)` executes the instructions of a program. It has three parts: the `arithmetic logic unit`, the `control unit` and the `registers`.

    Diagram
    ```
         +----------------------------------------------------+
         |                       C P U                        |
         |                                                    |
         |   +-------------+            +----------------+    |
         |   |     ALU     |<---------->|   Registers    |    |
         |   |             |            |  PC  IR  AC    |    |
         |   | + - x /     |            |  MAR MDR SP    |    |
         |   | AND OR NOT  |            |  Flags         |    |
         |   +-------------+            +----------------+    |
         |          ^                           ^             |
         |          |   control signals         |             |
         |   +------+---------------------------+---------+   |
         |   |            CONTROL UNIT                    |   |
         |   |   (fetch, decode, sequence, timing)        |   |
         |   +--------------------------------------------+   |
         |                        ^                           |
         |                     Clock                          |
         +------------------------|---------------------------+
                                  |
           Address bus  ----------+-------- Data bus -------- Control bus
                                  |
                  +---------------+---------------+
                  |                               |
            Main memory                      I/O devices
    ```

    ```mermaid
    flowchart LR
        MEM[Main memory] -->|instruction| CU[Control Unit]
        CU -->|control signals| ALU
        CU --> REG[Registers]
        REG <--> ALU
        ALU -->|result + flags| REG
        REG <-->|data| MEM
        CU --> IO[I/O devices]
    ```

    1. Arithmetic Logic Unit (ALU)
    - Performs every calculation and comparison in the machine.
    ```
       Arithmetic : ADD, SUB, MUL, DIV, INC, DEC
       Logical    : AND, OR, NOT, XOR
       Comparison and shift operations
    ```
    - It sets the `flags` — zero, carry, sign, overflow, parity — which later instructions test.
    - It is purely combinational; it stores nothing, so all operands come from and return to registers.

    2. Control Unit (CU)
    - Directs everything else but computes nothing itself.
    ```
       Fetches the instruction pointed to by the program counter
       Decodes it to find the operation and the operands
       Generates the timing and control signals for the ALU, registers,
           memory and I/O
       Controls the buses and handles interrupts
    ```

    3. Registers
    - The fastest storage in the machine, holding what is being worked on now.
    ```
       Program Counter (PC)      : address of the next instruction
       Instruction Register (IR) : the instruction being decoded
       Accumulator (AC)          : working register for the ALU
       MAR / MDR                 : memory address and data buffers
       Stack Pointer (SP)        : top of the stack
       Flag register             : status and control bits
    ```

    4. Cache (in a modern CPU)
    - Small very fast memory on the chip. An L1 hit takes about 4 cycles against more than 200 for main memory, so it keeps the ALU supplied with data.

    The instruction cycle — how the parts cooperate
    ```
       FETCH   : the CU reads the address in the PC and loads the instruction
                 at that address into the IR; the PC is incremented
       DECODE  : the CU interprets the opcode and identifies the operands
       EXECUTE : operands are loaded into registers and the ALU performs
                 the operation; the flags are set
       STORE   : the result is written back to a register or to memory
       ... and the cycle repeats, billions of times per second
    ```

    - CPU performance depends on `clock speed x instructions per cycle x number of cores`, and on how well the cache hides the latency of main memory.

34. **What are the difference between 8086 and 8088 microprocessors? Mention the flags of 8086 micriprocessor.** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 1273-1275 (ET: N/A)]*

    Answer: Differences between the 8086 and 8088

    Both were released by Intel in 1978-79 and are `software compatible` — the same machine code runs on either. The differences are all in the hardware interface.

    | Point | 8086 | 8088 |
    |---|---|---|
    | External data bus | 16 bits (D0-D15) | `8 bits` (D0-D7) |
    | Internal architecture | 16-bit | 16-bit (identical) |
    | Instruction queue | `6 bytes` | `4 bytes` |
    | Memory access | One 16-bit word per cycle | Two cycles needed for a 16-bit word |
    | Speed | Faster | Slower, because of the narrow bus |
    | Address bus | 20 bits, 1 MB | 20 bits, 1 MB (same) |
    | Address/data multiplexing | AD0-AD15 | AD0-AD7; A8-A15 are address only |
    | Memory organisation | Two banks, even and odd, selected by `BHE'` and A0 | A single bank; no BHE' pin |
    | Pin 28 | `M/IO'` (high for memory) | `IO/M'` (inverted sense) |
    | Pin 34 | `BHE'` (bank high enable) | `SSO` (status line) |
    | Hardware cost | Higher — needs a 16-bit board | Lower — 8-bit peripherals could be reused |
    | Used in | Later PCs and clones | The original IBM PC (1981) |

    - Why IBM chose the 8088 for the first PC: the 8-bit external bus let them use the cheap and widely available 8-bit support chips and memory boards of the time. The performance loss was accepted for the lower cost.
    - Why the queue is smaller: with an 8-bit bus the BIU cannot fill a 6-byte queue fast enough to be worth having, so 4 bytes was chosen.

    Flags of the 8086

    The flag register is `16 bits` wide, of which `9` are used — 6 status flags and 3 control flags.
    ```
       Bit  15 14 13 12 11 10  9  8  7  6  5  4  3  2  1  0
             -  -  -  -  OF DF IF TF SF ZF  - AF  - PF  - CF
    ```

    Status flags — set by the ALU to report the result
    ```
       CF (bit 0)  Carry     : carry out of, or borrow into, the MSB
       PF (bit 2)  Parity    : 1 if the low byte has an EVEN number of 1s
       AF (bit 4)  Auxiliary : carry from bit 3 to bit 4, used in BCD arithmetic
       ZF (bit 6)  Zero      : 1 if the result is zero
       SF (bit 7)  Sign      : copies the MSB; 1 means negative
       OF (bit 11) Overflow  : 1 if a signed result is out of range
    ```

    Control flags — set by the programmer to control the CPU
    ```
       TF (bit 8)  Trap      : 1 = single-step mode, used by debuggers
       IF (bit 9)  Interrupt : 1 enables maskable interrupts (STI / CLI)
       DF (bit 10) Direction : 0 = forward, 1 = backward for string
                               instructions (CLD / STD)
    ```

    - The register is saved and restored by `PUSHF` and `POPF`, and is pushed automatically when an interrupt occurs, so the flags survive an interrupt service routine.
    - The distinction to state clearly: `status flags are set BY the processor to report a result; control flags are set BY the programmer to control the processor`.

35. **What is SPI (Serial Peripheral Interface)? What are the advantages over parallel interface?** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 1276 (ET: N/A)]*

    Answer: What SPI is
    - `SPI (Serial Peripheral Interface)` is a synchronous, full-duplex serial communication protocol developed by Motorola. It connects a `master` — usually a microcontroller — to one or more `slave` devices over a short distance on the same board.
    - It uses `four` wires:
    ```
       SCLK : serial clock, generated by the master
       MOSI : Master Out, Slave In   - data from master to slave
       MISO : Master In, Slave Out   - data from slave to master
       SS'  : slave select, one line per slave, active LOW
    ```

    Connection
    ```
            MASTER                          SLAVE 1
       +--------------+                 +-------------+
       | SCLK  -------|---------------->| SCLK        |
       | MOSI  -------|---------------->| MOSI        |
       | MISO  <------|-----------------| MISO        |
       | SS1'  -------|---------------->| SS'         |
       | SS2'  -------|----+            +-------------+
       +--------------+    |
                           |            +-------------+
                           +----------->| SS'  SLAVE 2|
                                        +-------------+
       SCLK, MOSI and MISO are shared; each slave has its OWN SS' line.
    ```

    How it works
    ```
       1. The master pulls the chosen slave's SS' LOW to select it.
       2. The master generates clock pulses on SCLK.
       3. On each clock edge one bit goes out on MOSI and one bit comes in
          on MISO at the same time - it is FULL DUPLEX.
       4. Master and slave are effectively one circular shift register;
          after 8 clocks their bytes have been exchanged.
       5. The master raises SS' to end the transfer.
    ```
    - Four `modes` are defined by `CPOL` (clock idle level) and `CPHA` (which edge samples the data). Master and slave must be set to the same mode or the data is garbage.

    Advantages over a parallel interface
    - `Far fewer wires.` SPI needs 4 lines plus one per extra slave. An 8-bit parallel interface needs 8 data lines plus several control lines, and a 16-bit one needs 16. Fewer wires means a smaller connector, fewer PCB traces and a cheaper board.
    - `Fewer pins on the chip.` Pins are expensive; freeing 8 or 16 pins allows a smaller, cheaper package or more I/O for other purposes.
    - `No skew problem.` In a parallel bus all bits must arrive within a very narrow window. Small differences in trace length make them arrive at slightly different times — `clock skew` — which limits both the speed and the cable length. A serial link sends one bit at a time, so skew simply does not arise. This is why serial interfaces (SATA, PCIe, USB) replaced their parallel ancestors (PATA, PCI, parallel port).
    - `Higher usable clock rate.` Because skew and crosstalk are absent, SPI runs comfortably at 10-50 MHz, and often faster, while a parallel bus must slow down as it widens.
    - `Less crosstalk and EMI.` Fewer switching lines side by side means less interference and easier compliance with emission rules.
    - `Longer usable distance` on a board, and it works over a flat cable where parallel would fail.
    - `Simple hardware.` No addressing, no start/stop bits, no acknowledgement, no arbitration — just a shift register and a clock. It is easy to implement in software (`bit banging`) when no hardware peripheral is available.
    - `Full duplex.` Data flows both ways at once, which a simple parallel port cannot do without doubling the wires.
    - `Any word length.` SPI is not limited to 8 bits; 12-bit ADCs and 16-bit sensors work naturally.
    - `Lower power`, since fewer lines are switching.

    Limitations, for balance
    ```
       No acknowledgement or error checking built in
       One SS' line per slave, so many slaves need many pins
       Short distance only - within a board or a few tens of centimetres
       No formal standard, so implementations differ slightly
       Single master only
    ```

    - Compared with `I2C`: SPI is faster and full duplex but needs more pins; I2C needs only 2 wires and addresses up to 127 devices, but is slower and half duplex. SPI is used for SD cards, displays, ADCs and flash memory; I2C for slow sensors and EEPROMs.

## Memory Hierarchy & Storage (26)

1. Compare RAM, ROM, cache memory, and secondary storage in terms of speed and usage. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer: The four form a `memory hierarchy`: as you move away from the CPU, storage gets larger and cheaper but much slower.
   ```
           CPU
            |
         Registers      ~1 cycle        bytes          fastest, costliest
            |
         Cache (L1/L2/L3) 4-40 cycles   KB to MB
            |
         RAM (main)     ~200 cycles     GB
            |
         Secondary (SSD/HDD)  millions  TB             slowest, cheapest
   ```

   Cache memory
   - Very fast SRAM built on or beside the CPU chip, holding the instructions and data most recently used.
   - Access takes about `4 cycles (L1)` to `40 cycles (L3)`.
   - Size 32 KB to 32 MB. Volatile. Managed by hardware, not by the programmer.
   - Purpose: hide the slowness of RAM. Without it a fast CPU would spend most of its time waiting.

   RAM (Random Access Memory)
   - The computer's `main working memory`. Holds the operating system, the running programs and their data.
   - Access takes about `200 cycles` — roughly 50 to 100 ns. Size 4 GB to 64 GB.
   - `Volatile` — everything is lost when power goes off.
   - `Read and write` freely. Built as `DRAM`, which needs constant refreshing.

   ROM (Read Only Memory)
   - Holds the `firmware` that the machine needs at power-on: the BIOS/UEFI, the bootstrap loader, and the fixed program in an embedded device.
   - Speed is comparable to RAM but slightly slower; size is small, kilobytes to a few megabytes.
   - `Non-volatile` — the contents survive a power cut. Normally `read only`; modern EEPROM and Flash forms can be rewritten, but slowly.

   Secondary storage (HDD, SSD, optical, tape)
   - `Permanent` bulk storage for files, programs and the operating system itself.
   - Access takes `milliseconds` for a hard disk and `tens of microseconds` for an SSD — thousands to millions of times slower than RAM.
   - Size is terabytes; cost per gigabyte is by far the lowest. Non-volatile.
   - The CPU cannot execute directly from it; data must first be copied into RAM.

   Comparison

   | Point | Cache | RAM | ROM | Secondary storage |
   |---|---|---|---|---|
   | Speed | Fastest after registers | Fast | Moderate | Slowest |
   | Access time | 1-40 cycles | ~50-100 ns | ~100 ns | 0.1 ms (SSD) to 10 ms (HDD) |
   | Capacity | KB to MB | GB | KB to MB | GB to TB |
   | Volatile | Yes | Yes | No | No |
   | Read / write | Both | Both | Read mostly | Both |
   | Cost per byte | Highest | High | Low | Lowest |
   | Technology | SRAM | DRAM | Flash / EEPROM | Magnetic or NAND flash |
   | Managed by | Hardware | Operating system | Manufacturer | File system |
   | Holds | Recently used data | Running programs | Firmware, BIOS | All files, permanently |

   - Why the hierarchy works: the `principle of locality`. Programs reuse the same instructions and data repeatedly (temporal locality) and access neighbouring addresses (spatial locality), so a small fast cache satisfies most requests and the slow levels are reached rarely.

2. **Difference between SRAM & DRAM also write Differences Cache Memory vs Flash Memory.** *[BUET Assistant Programmer 21.06.2025 compact it 1434 (ET: BUET)]*

   Answer: SRAM versus DRAM

   `SRAM` (Static RAM)
   - Each cell is a `flip-flop` made of `6 transistors`. It holds its value as long as power is applied, with `no refreshing`.
   - Very fast, but large per bit and expensive.
   - Used for `cache memory` (L1, L2, L3) and CPU registers.

   `DRAM` (Dynamic RAM)
   - Each cell is `1 transistor + 1 capacitor`. The bit is the charge on the capacitor, which leaks away, so every cell must be `refreshed` thousands of times a second.
   - Slower, but very small and cheap per bit, so huge capacities are possible.
   - Used for `main memory` (the RAM sticks in a computer).

   | Point | SRAM | DRAM |
   |---|---|---|
   | Cell | 6 transistors (flip-flop) | 1 transistor + 1 capacitor |
   | Refresh needed | No | Yes, every few milliseconds |
   | Speed | Very fast (1-10 ns) | Slower (50-70 ns) |
   | Density | Low | Very high |
   | Cost per bit | High | Low |
   | Power (idle) | Low | Higher, refresh consumes power |
   | Capacity per chip | Small (KB to MB) | Large (GB) |
   | Used in | Cache, registers | Main memory |
   | Volatile | Yes | Yes |

   Cache memory versus Flash memory

   `Cache memory`
   - Small, very fast `SRAM` on or beside the CPU, holding recently used instructions and data. Managed automatically by hardware.
   - `Volatile` — contents vanish at power-off.
   - Purpose: hide the latency of main memory so the CPU is not left waiting.

   `Flash memory`
   - `Non-volatile` semiconductor storage using floating-gate transistors that trap charge. It keeps its contents with no power at all.
   - Slower than cache or RAM, and it wears out — each cell survives a limited number of write cycles (about 3,000 to 100,000).
   - Used in SSDs, pen drives, memory cards, and for BIOS/firmware storage.

   | Point | Cache memory | Flash memory |
   |---|---|---|
   | Technology | SRAM | Floating-gate NAND/NOR |
   | Volatile | Yes | No |
   | Speed | Extremely fast (ns) | Much slower (microseconds) |
   | Purpose | Speed up CPU access to RAM | Permanent storage of data |
   | Location | Inside or next to the CPU | On an SSD, pen drive or motherboard |
   | Capacity | KB to MB | GB to TB |
   | Cost per byte | Very high | Low |
   | Write endurance | Unlimited | Limited, cells wear out |
   | Erase before write | No | Yes, whole blocks at a time |
   | Managed by | Hardware | Controller and file system |

   - Where each sits in the hierarchy: `registers -> cache (SRAM) -> main memory (DRAM) -> SSD (flash) -> hard disk`. Speed falls and capacity rises at each step, which is exactly what the hierarchy is designed to do.

3. **DRAM stands for __________?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

   Answer: `DRAM` stands for `Dynamic Random Access Memory`.

   - "Dynamic" because each cell stores its bit as `charge on a tiny capacitor`, and that charge leaks away. The memory controller must therefore `refresh` every row thousands of times a second by reading it and writing it back. Without refreshing, the data is lost in a few milliseconds.
   - "Random Access" because any location can be reached directly in the same time, without reading through what comes before it.
   ```
      One DRAM cell = 1 transistor + 1 capacitor
   ```
   - Because a cell is so small, DRAM packs enormous capacity onto a chip at very low cost per bit. That is why it is used for `main memory` — the RAM sticks in a computer.
   - It is `volatile`: everything is lost when power is switched off.

   Types
   ```
      SDRAM  : synchronous, clocked with the system bus
      DDR    : Double Data Rate - transfers on both clock edges
      DDR2, DDR3, DDR4, DDR5 : successive generations, each faster and
                               lower in voltage
   ```

   Compared with SRAM
   ```
      SRAM : 6 transistors per cell, no refresh, very fast, expensive
             -> used for CACHE

      DRAM : 1 transistor + 1 capacitor, needs refresh, slower, cheap
             -> used for MAIN MEMORY
   ```

4. **What is stand for EEPROM?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

   Answer: `EEPROM` stands for `Electrically Erasable Programmable Read Only Memory`.

   - It is a `non-volatile` memory that keeps its contents with no power, but can be `erased and rewritten electrically`, byte by byte, while it stays in the circuit.
   - The bit is stored as charge trapped on a `floating gate` inside a transistor.

   How it improved on earlier ROMs
   ```
      ROM    : contents fixed by the manufacturer; can never be changed
      PROM   : Programmable ROM - the user can write it ONCE, then never again
      EPROM  : Erasable PROM - erased by ULTRAVIOLET light through a quartz
               window; the chip must be removed from the board, and the WHOLE
               chip is erased at once (about 20 minutes)
      EEPROM : erased ELECTRICALLY, BYTE by BYTE, without removing the chip
      Flash  : a fast EEPROM that erases in BLOCKS rather than bytes,
               which makes it much cheaper and denser
   ```

   Characteristics
   ```
      Non-volatile           : keeps data without power
      Byte-level erase       : any single byte can be rewritten
      In-circuit programmable: no need to remove the chip
      Endurance              : about 10,000 to 1,000,000 write cycles per cell
      Data retention         : 10 years or more
      Write speed            : slow (milliseconds) compared with reading
      Capacity               : small - bytes to a few hundred kilobytes
   ```

   Uses
   - Storing `configuration and calibration data` that must survive a power cut but may change occasionally — BIOS settings, a device's serial number, a meter's reading, a car ECU's tuning values.
   - Inside microcontrollers, as a small area for saving settings between power cycles.

   - `Flash memory` is the descendant that took over the bulk market: it gives up byte-level erasing in exchange for far higher density and lower cost, which is why SSDs, pen drives and memory cards all use flash rather than plain EEPROM.

5. **কম্পিউটার স্মৃতি বলতে কী বোঝায়? কম্পিউটারের স্মৃতির শ্রেণিবিভাগ আলোচনা করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 405 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Computer memory
   - `Memory` is the part of a computer that `stores` data, instructions and results so that they can be used by the processor. Without it a computer could hold nothing, not even the program it is running.
   - Memory is organised as a large number of `locations`, each with a unique `address`, and each holding a fixed number of bits — normally one byte.
   ```
      Address     Content
      ---------   -------
      0000        1010 1101
      0001        0011 0110
      0002        1111 0000
   ```

   Functions of memory
   - Hold the `program` currently being executed.
   - Hold the `data` it is working on, and the `results` produced.
   - Hold the `operating system` and the firmware needed to start the machine.
   - Store files `permanently` for future use.

   Classification of memory

   1. By position in the hierarchy
   ```
      Registers          : inside the CPU, fastest, a few bytes
      Cache memory       : L1, L2, L3 - SRAM, very fast, KB to MB
      Primary (main)     : RAM and ROM - directly accessible by the CPU, GB
      Secondary          : hard disk, SSD, optical disc - permanent, TB
      Tertiary / backup  : magnetic tape, cloud storage - archival
   ```
   - Moving down the list, speed and cost per byte fall while capacity rises.

   2. By volatility
   ```
      Volatile     : loses its contents when power is removed  -> RAM, cache
      Non-volatile : keeps its contents without power          -> ROM, HDD, SSD
   ```

   3. Primary memory, by type
   ```
      RAM (Random Access Memory) - volatile, read/write, main working memory
           SRAM : 6-transistor flip-flop cell, no refresh, fast, used for cache
           DRAM : 1 transistor + 1 capacitor, needs refresh, cheap, used for
                  main memory (SDRAM, DDR, DDR2, DDR3, DDR4, DDR5)

      ROM (Read Only Memory) - non-volatile, holds firmware
           MROM   : masked, written by the manufacturer, never changeable
           PROM   : user-programmable ONCE
           EPROM  : erased by ultraviolet light, whole chip at a time
           EEPROM : erased electrically, byte by byte, in circuit
           Flash  : block-erasable EEPROM, used in BIOS, SSDs, pen drives
   ```

   4. Secondary memory, by technology
   ```
      Magnetic      : hard disk, floppy disk, magnetic tape
      Optical       : CD, DVD, Blu-ray
      Semiconductor : SSD, pen drive, SD card (all flash based)
   ```

   5. By access method
   ```
      Random access     : any location reached directly, same time - RAM, SSD
      Sequential access : must pass through everything before it - magnetic tape
      Direct access     : a mixture of the two - hard disk
      Associative       : searched by content, not address - cache tag memory
   ```

   The hierarchy, drawn
   ```
                 /\
                /  \        Registers      - fastest, smallest, costliest
               /----\       Cache
              /------\      Main memory (RAM, ROM)
             /--------\     Secondary (SSD, HDD)
            /----------\    Tertiary (tape, cloud)
           /____________\   - slowest, largest, cheapest
   ```

   - Why the hierarchy exists: fast memory is expensive and slow memory is cheap, so a computer uses a little of the fast kind and a lot of the slow kind. It works because of the `principle of locality` — programs keep reusing the same small set of instructions and data, so the fast levels satisfy most requests.

6. **Write down the difference between RAM and ROM.** *[DESCO Sub-Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)], [DMLC Assistant Teacher (ICT) 2021 compact it 826 (ET: N/A)]*

   Answer: `RAM` is the computer's working memory — fast, read/write and volatile. `ROM` holds permanent firmware — non-volatile and normally read only.

   RAM (Random Access Memory)
   - Holds the operating system, the running programs and the data they are working on.
   - `Volatile`: everything is lost when the power goes off.
   - Both `read and write` at full speed.
   - Types: `SRAM` (flip-flop cell, no refresh, fast, used for cache) and `DRAM` (capacitor cell, needs refresh, cheap, used for main memory).

   ROM (Read Only Memory)
   - Holds the firmware the machine needs at power-on: the BIOS/UEFI, the bootstrap loader, and the fixed program of an embedded device.
   - `Non-volatile`: contents survive a power cut.
   - Written by the manufacturer, or rewritten only slowly and with a special procedure.
   - Types: `MROM`, `PROM`, `EPROM`, `EEPROM`, `Flash`.

   Difference

   | Point | RAM | ROM |
   |---|---|---|
   | Full form | Random Access Memory | Read Only Memory |
   | Volatility | Volatile — data lost at power-off | Non-volatile — data retained |
   | Read / write | Both, freely | Read normally; writing is slow or impossible |
   | Speed | Very fast | Slower to write, comparable to read |
   | Capacity | Large (4-64 GB) | Small (KB to a few MB) |
   | Cost per byte | Higher | Lower |
   | Contents | Programs and data currently in use | Firmware, BIOS, bootstrap loader |
   | Modified by the user | Yes, constantly | No, or rarely |
   | Types | SRAM, DRAM | MROM, PROM, EPROM, EEPROM, Flash |
   | Power consumption | Higher (DRAM needs refresh) | Lower |
   | Used for | Temporary working storage | Permanent instructions |

   - How they work together at start-up: the CPU can execute nothing without instructions, and RAM is empty at power-on. So the processor begins by fetching from `ROM`, which runs the BIOS, tests the hardware, and loads the operating system from disk into `RAM`. From that point the machine runs out of RAM.

7. **Differentiate among CPU register, Cache memory, Main memory and Secondary memory.** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 510 (ET: MIST)]*

   Answer: These four are successive levels of the `memory hierarchy`. Moving away from the CPU, storage becomes larger and cheaper but much slower.
   ```
      CPU Register  ->  Cache  ->  Main memory  ->  Secondary memory
      fastest                                         slowest
      smallest                                        largest
      costliest per byte                              cheapest per byte
   ```

   CPU register
   - Storage `inside` the CPU itself, used to hold the operands and addresses currently being processed.
   - Access takes about `one clock cycle` — the fastest storage that exists.
   - Capacity is tiny: a few dozen registers of 32 or 64 bits, so a few hundred bytes in total.
   - Managed by the `compiler and the instruction set`. Examples: PC, IR, accumulator, AX, flags.

   Cache memory
   - Small, very fast `SRAM` on or beside the CPU chip, holding recently used instructions and data.
   ```
      L1 : 32-64 KB   ~4 cycles
      L2 : 256KB-1MB  ~12 cycles
      L3 : 8-32 MB    ~40 cycles
   ```
   - Managed automatically by `hardware` — the programmer cannot address it directly.
   - Purpose: hide the latency of main memory so the CPU is not left waiting.

   Main memory (RAM)
   - The working memory of the computer, holding the operating system and every running program.
   - Access takes about `50-100 ns`, roughly 200 cycles. Capacity 4-64 GB.
   - Built as `DRAM`; volatile; managed by the operating system through virtual memory.
   - The CPU can address it directly, which is why a program must be loaded here before it can run.

   Secondary memory
   - Permanent bulk storage: hard disk, SSD, optical disc, pen drive.
   - Access takes `tens of microseconds (SSD)` to `milliseconds (HDD)` — thousands to millions of times slower than RAM.
   - Capacity is terabytes, and cost per byte is by far the lowest. `Non-volatile`.
   - The CPU `cannot` execute from it directly; data must be copied into RAM first. Managed by the `file system`.

   Comparison

   | Point | CPU register | Cache | Main memory | Secondary memory |
   |---|---|---|---|---|
   | Location | Inside the CPU | On or beside the CPU | On the motherboard | External drive |
   | Access time | ~1 cycle | 4-40 cycles | ~200 cycles | 10^4 to 10^7 cycles |
   | Capacity | Bytes | KB to MB | GB | TB |
   | Technology | Flip-flops | SRAM | DRAM | Magnetic or NAND flash |
   | Cost per byte | Highest | Very high | Moderate | Lowest |
   | Volatile | Yes | Yes | Yes | No |
   | Managed by | Compiler / ISA | Hardware | Operating system | File system |
   | CPU can execute from it | Yes | Yes | Yes | No |
   | Holds | Current operands | Recently used data | Running programs | All files, permanently |

   - Why the hierarchy works: the `principle of locality`. A program reuses the same instructions and data repeatedly (temporal locality) and accesses neighbouring addresses (spatial locality), so a small fast level satisfies most requests and the slow levels are reached only occasionally.

8. **What do you mean by memory organization? Write the different between SRAM and DRAM.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 558 (ET: BIBM)]*

   Answer: Memory organization
   - `Memory organization` is how the memory of a computer is `structured, addressed and connected` to the processor so that data can be stored and retrieved efficiently.

   It covers
   - `Addressing` — every location has a unique address; an n-bit address bus reaches 2^n locations.
   ```
      16 lines -> 64 KB      20 lines -> 1 MB      32 lines -> 4 GB
   ```
   - `Word size` — how many bits are read or written per access (8, 16, 32, 64).
   - `The memory hierarchy` — registers, cache, main memory and secondary storage arranged so that speed and cost are traded against capacity.
   - `Memory mapping and decoding` — an address decoder selects exactly one chip for each address range, so several chips share the same bus without conflict.
   - `Memory interleaving` — consecutive addresses are spread across several banks so that they can be accessed in parallel, raising bandwidth.
   - `Banking and organisation of a chip` — a chip described as `1K x 8` has 1024 locations of 8 bits each; several such chips are combined to widen the word or extend the address range.
   - `Virtual memory, paging and segmentation` — the operating system's way of giving each process its own address space larger than physical RAM.
   - `Cache organisation` — direct-mapped, set-associative or fully associative, with a replacement policy and a write policy.
   - `Memory-mapped I/O versus isolated I/O` — whether devices share the memory address space or have their own.

   Example of combining chips
   ```
      Required : 4K x 8 memory
      Available: 1K x 8 chips

      Number of chips = 4K / 1K = 4 chips in series (to extend the address range)

      Each chip needs 10 address lines (2^10 = 1K)
      2 more lines go to a 2-to-4 decoder to select which chip
      Total : 12 address lines -> 2^12 = 4K locations
   ```

   SRAM versus DRAM

   `SRAM` (Static RAM) — each cell is a `flip-flop` of `6 transistors`. It holds its value as long as power is on, with `no refreshing`. Fast but large and expensive per bit.

   `DRAM` (Dynamic RAM) — each cell is `1 transistor + 1 capacitor`. The charge leaks, so every row must be `refreshed` thousands of times a second. Slower, but tiny and cheap, so huge capacities are possible.

   | Point | SRAM | DRAM |
   |---|---|---|
   | Cell structure | 6 transistors (flip-flop) | 1 transistor + 1 capacitor |
   | Refresh required | No | Yes, every few milliseconds |
   | Access time | 1-10 ns | 50-70 ns |
   | Density | Low | Very high |
   | Cost per bit | High | Low |
   | Power (idle) | Low | Higher, refresh circuitry runs constantly |
   | Capacity per chip | KB to MB | GB |
   | Complexity | Simpler interface, no refresh logic | Needs a refresh controller |
   | Used in | Cache memory, registers | Main memory |
   | Volatile | Yes | Yes |

   - Both are volatile. The design trade is simple: `SRAM buys speed with area, DRAM buys capacity with refresh overhead`. That is why a computer uses a little SRAM as cache in front of a lot of DRAM.

9. **What is dual channel RAM? Difference between single In-Line and Dual In-Line Memory Module.** *[BITAC Assistant Programmer 27.10.2023 compact it 559 (ET: BUTEX)]*

   Answer: Dual channel RAM
   - `Dual channel` is a memory configuration in which the memory controller uses `two independent 64-bit data paths` to the RAM at the same time, instead of one.
   - This `doubles the theoretical bandwidth` between the CPU and memory — the width becomes 128 bits per transfer.
   ```
      Single channel : CPU <--- 64-bit path ---> RAM
      Dual channel   : CPU <--- 64-bit path ---> RAM stick A
                           <--- 64-bit path ---> RAM stick B    (in parallel)
   ```

   Requirements to enable it
   - `Two (or four) modules`, installed in the correct paired slots — usually the same colour, or slots 1 and 3, or 2 and 4. The motherboard manual states which.
   - The modules should `match` in capacity, speed, timings and preferably manufacturer. Mismatched sticks usually still run, but at the slower module's timings, or fall back to single channel.
   - The memory controller (now inside the CPU) must support it.

   What it gains
   - Higher memory bandwidth — in practice 10-30 per cent better in memory-bound work, and much more for `integrated graphics`, which shares system RAM and is starved by a single channel.
   - Little benefit for ordinary office work, which is not memory-bound.
   ```
      Practical rule : 2 x 8 GB is better than 1 x 16 GB, at the same price.
   ```
   - `Triple`, `quad` and `octa` channel exist on workstation and server platforms.

   SIMM versus DIMM

   `SIMM` (Single In-line Memory Module)
   - The contacts on the two sides of the edge connector are `electrically the same` — the two rows are joined, so there is effectively one row of contacts.
   - 30-pin (8-bit) or 72-pin (32-bit) data path.
   - Because a Pentium has a 64-bit bus, SIMMs had to be installed in `matched pairs`.
   - Older technology: FPM and EDO RAM, 5 V. Obsolete.

   `DIMM` (Dual In-line Memory Module)
   - The contacts on the two sides are `electrically independent`, so the module has twice as many usable connections in the same length.
   - 168-pin SDRAM, 184-pin DDR, 240-pin DDR2/DDR3, 288-pin DDR4/DDR5. Data path is `64 bits`.
   - Can be installed `singly`, because one module already matches the CPU's 64-bit bus.
   - Runs at lower voltage (3.3 V down to 1.1 V), so it uses less power.

   | Point | SIMM | DIMM |
   |---|---|---|
   | Contacts on the two sides | Connected — act as one row | Independent — two separate rows |
   | Data path width | 8 or 32 bits | 64 bits |
   | Pins | 30 or 72 | 168 to 288 |
   | Installed | In matched pairs | Singly |
   | Voltage | 5 V | 3.3 V down to 1.1 V |
   | Memory type | FPM, EDO | SDRAM, DDR to DDR5 |
   | Capacity | Small (up to 128 MB) | Large (up to 128 GB per module) |
   | Status | Obsolete | Current standard |

   - The laptop version of a DIMM is the `SO-DIMM` (Small Outline DIMM), which is shorter but works the same way.
   - Note the difference between `dual channel` and `dual in-line`: dual channel is a `motherboard and CPU feature` about how many paths exist to memory; dual in-line describes the `physical module` and how its edge contacts are wired. They are unrelated despite the similar names.

10. **What is the difference between Dynamic RAM and Static RAM?** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 642 (ET: BUET)]*

    Answer: Both are volatile read/write memories. The difference is the `cell design`, and everything else follows from it.

    `SRAM` (Static RAM)
    - Each cell is a `flip-flop` built from `6 transistors`. It holds its value as long as power is applied.
    - `Static` means no refreshing is needed — the cross-coupled inverters keep reinforcing the stored bit.
    - Fast, but a 6-transistor cell is large and expensive, so capacity is limited.

    `DRAM` (Dynamic RAM)
    - Each cell is `1 transistor + 1 capacitor`. The bit is the charge on that capacitor.
    - `Dynamic` means the charge leaks away, so every row must be `refreshed` — read and written back — every few milliseconds.
    - A one-transistor cell is tiny, so DRAM is cheap and very dense.

    ```
       SRAM cell (6T)                DRAM cell (1T1C)

          Vdd    Vdd                    word line
           |      |                         |
          |‾|    |‾|                      --|
          |_|    |_|                        |
           +--><--+   cross-coupled       -----  capacitor
           |      |   inverters            ---
          |‾|    |_|                        |
          |_|    | |                       GND
           |      |                    bit line
          GND    GND
    ```

    Difference

    | Point | SRAM | DRAM |
    |---|---|---|
    | Cell structure | 6 transistors (flip-flop) | 1 transistor + 1 capacitor |
    | Refresh required | No | Yes, every few milliseconds |
    | Access time | 1-10 ns | 50-70 ns |
    | Speed | Much faster | Slower |
    | Density | Low | Very high |
    | Capacity per chip | KB to MB | GB |
    | Cost per bit | High | Low |
    | Power when idle | Low | Higher — refresh runs constantly |
    | Power when active | Higher | Lower |
    | Extra circuitry | None | Refresh controller needed |
    | Heat | Lower | Higher |
    | Used in | Cache (L1, L2, L3), registers | Main memory (the RAM sticks) |
    | Volatile | Yes | Yes |
    | Types | Asynchronous, synchronous, pipeline burst | SDRAM, DDR, DDR2-DDR5 |

    - The trade-off in one line: `SRAM buys speed by spending area; DRAM buys capacity by accepting refresh overhead`.
    - That is exactly why a computer uses both — a few megabytes of SRAM as cache sitting in front of many gigabytes of DRAM. The cache hides the DRAM's latency, and the DRAM supplies the capacity the cache cannot.

11. **Give classification of memory. Differentiate between RAM and ROM.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 664 (ET: N/A)]*

    Answer: Classification of memory

    1. By position in the hierarchy
    ```
       Registers          : inside the CPU, ~1 cycle, a few hundred bytes
       Cache memory       : L1, L2, L3 - SRAM, 4-40 cycles, KB to MB
       Primary (main)     : RAM and ROM, ~200 cycles, GB
       Secondary          : hard disk, SSD, optical disc, TB
       Tertiary / backup  : magnetic tape, cloud - archival
    ```
    - Speed and cost per byte fall going down; capacity rises.

    2. By volatility
    ```
       Volatile     : contents lost at power-off   -> RAM, cache, registers
       Non-volatile : contents retained            -> ROM, HDD, SSD, flash
    ```

    3. Primary memory by type
    ```
       RAM - volatile, read/write
            SRAM : 6-transistor flip-flop cell, no refresh, fast, used for cache
            DRAM : 1 transistor + 1 capacitor, needs refresh, cheap,
                   used for main memory (SDRAM, DDR to DDR5)

       ROM - non-volatile, holds firmware
            MROM   : masked, fixed by the manufacturer
            PROM   : programmable once by the user
            EPROM  : erased by ultraviolet light, whole chip at a time
            EEPROM : erased electrically, byte by byte, in circuit
            Flash  : block-erasable EEPROM - BIOS, SSD, pen drive
    ```

    4. Secondary memory by technology
    ```
       Magnetic      : hard disk, floppy disk, magnetic tape
       Optical       : CD, DVD, Blu-ray
       Semiconductor : SSD, pen drive, SD card (all flash)
    ```

    5. By access method
    ```
       Random access     : any location reached directly - RAM, SSD
       Sequential access : must pass through everything before it - tape
       Direct access     : a mixture - hard disk
       Associative       : searched by content, not by address - cache tags
    ```

    Difference between RAM and ROM

    | Point | RAM | ROM |
    |---|---|---|
    | Full form | Random Access Memory | Read Only Memory |
    | Volatility | Volatile — lost at power-off | Non-volatile — retained |
    | Read / write | Both, at full speed | Read normally; writing slow or impossible |
    | Capacity | Large (4-64 GB) | Small (KB to a few MB) |
    | Cost per byte | Higher | Lower |
    | Speed | Very fast | Slower to write |
    | Contents | Programs and data in use now | Firmware, BIOS, bootstrap loader |
    | Changed by the user | Constantly | Rarely or never |
    | Types | SRAM, DRAM | MROM, PROM, EPROM, EEPROM, Flash |
    | Power use | Higher (DRAM refresh) | Lower |
    | Purpose | Temporary working storage | Permanent instructions |

    - How they cooperate at start-up: RAM is empty at power-on, so the CPU begins fetching from `ROM`. The BIOS there tests the hardware and loads the operating system from disk into `RAM`, and from that point the machine runs out of RAM.

12. **(গ) Primary Memory and Secondary Memory এর উদাহরণসহ তুলনামূলক আলোচনা করুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 705 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Primary memory
    - The memory the CPU can `address directly`. A program must be loaded here before it can run.
    - Fast, expensive per byte, and small in capacity.
    - Two kinds:
    ```
       RAM : volatile, read/write, holds the OS and running programs
             SRAM (cache) and DRAM (main memory)

       ROM : non-volatile, holds firmware - BIOS, bootstrap loader
             MROM, PROM, EPROM, EEPROM, Flash
    ```
    - Examples: DDR4 RAM modules, cache memory, the BIOS chip.

    Secondary memory
    - Permanent bulk storage that the CPU `cannot address directly`. Data must first be copied into primary memory.
    - Slow, cheap per byte, and very large in capacity. Non-volatile.
    ```
       Magnetic      : hard disk, magnetic tape, floppy disk
       Optical       : CD, DVD, Blu-ray
       Semiconductor : SSD, pen drive, SD card
    ```
    - Examples: a 1 TB hard disk, a 512 GB SSD, a 32 GB pen drive.

    Comparison

    | Point | Primary memory | Secondary memory |
    |---|---|---|
    | CPU access | Direct | Not direct — must go through primary |
    | Speed | Very fast (ns) | Slow (microseconds to milliseconds) |
    | Capacity | Small (GB) | Large (TB) |
    | Cost per byte | High | Very low |
    | Volatility | RAM volatile, ROM non-volatile | Always non-volatile |
    | Purpose | Hold programs and data in use now | Store everything permanently |
    | Data retention | Only while powered (RAM) | Retained for years |
    | Technology | Semiconductor | Magnetic, optical, flash |
    | Portability | Fixed inside the machine | Often removable |
    | Also called | Main memory, internal memory | Auxiliary memory, external storage |
    | Examples | RAM, ROM, cache | HDD, SSD, DVD, pen drive |

    How they work together
    ```
       1. A program file sits on the hard disk (secondary).
       2. The user runs it; the OS COPIES it into RAM (primary).
       3. The CPU executes it from RAM.
       4. Results are written back to the disk to be kept permanently.
    ```
    - The reason for the split is economic: fast memory is expensive, so a computer uses a small amount of it for the work in hand and a large amount of cheap slow storage for everything else.

13. **Write down the difference between SRAM and DRAM.** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 718 (ET: N/A)]*

    Answer: Both are volatile read/write memories, and every difference follows from the `cell design`.

    `SRAM` (Static RAM)
    - Each cell is a `flip-flop` of `6 transistors`, which holds its value as long as power is applied.
    - `No refresh` is needed — the cross-coupled inverters keep reinforcing the bit.
    - Fast, but the large cell makes it costly and limits capacity.

    `DRAM` (Dynamic RAM)
    - Each cell is `1 transistor + 1 capacitor`, storing the bit as charge.
    - The charge leaks away, so every row must be `refreshed` every few milliseconds.
    - The tiny cell makes it very dense and cheap.

    Difference

    | Point | SRAM | DRAM |
    |---|---|---|
    | Cell | 6 transistors (flip-flop) | 1 transistor + 1 capacitor |
    | Refresh needed | No | Yes, every few milliseconds |
    | Access time | 1-10 ns | 50-70 ns |
    | Speed | Much faster | Slower |
    | Density | Low | Very high |
    | Capacity per chip | KB to MB | GB |
    | Cost per bit | High | Low |
    | Idle power | Low | Higher — refresh runs constantly |
    | Extra circuitry | None | Refresh controller required |
    | Heat generated | Less | More |
    | Used in | Cache (L1, L2, L3), registers | Main memory (RAM sticks) |
    | Volatile | Yes | Yes |
    | Types | Asynchronous, synchronous, pipeline burst | SDRAM, DDR, DDR2 to DDR5 |

    - The trade-off in one line: `SRAM buys speed by spending silicon area; DRAM buys capacity by accepting the cost of refreshing`.
    - Both are used together in every computer — a few megabytes of SRAM cache in front of many gigabytes of DRAM. The cache hides the DRAM's latency; the DRAM supplies the capacity.

14. **(ক) Data transfer rate এর ভিত্তিতে নিম্নোক্ত memory/storage device গুলোকে বেশী থেকে কম ক্রমানুসারে সাজান। (i) Flash drive (ii) SSD (iii) Cache memory (iv) DVD (v) RAM (vi) Magnetic HD** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 767 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Arranged from the `highest` data transfer rate to the `lowest`:
    ```
       1. Cache memory      (iii)
       2. RAM               (v)
       3. SSD               (ii)
       4. Magnetic HD       (vi)
       5. Flash drive       (i)
       6. DVD               (iv)
    ```

    Typical transfer rates

    | Rank | Device | Typical transfer rate | Technology |
    |---|---|---|---|
    | 1 | Cache memory | 100 GB/s to 1 TB/s | SRAM, on the CPU die |
    | 2 | RAM | 20-50 GB/s (DDR4/DDR5) | DRAM, on the memory bus |
    | 3 | SSD | 500 MB/s (SATA) to 7 GB/s (NVMe) | NAND flash, PCIe or SATA |
    | 4 | Magnetic hard disk | 100-200 MB/s | Rotating magnetic platter |
    | 5 | Flash drive (pen drive) | 20-400 MB/s (USB 2.0 to 3.x) | NAND flash over USB |
    | 6 | DVD | 1.3-22 MB/s (1x to 16x) | Optical, laser reading a disc |

    Why the order comes out this way
    - `Cache` is SRAM built onto the processor die itself, only millimetres from the ALU, with an extremely wide internal bus. Nothing else is close.
    - `RAM` is DRAM on the motherboard, reached over a dedicated 64-bit (or 128-bit dual-channel) memory bus at gigahertz rates.
    - `SSD` has no moving parts, so there is no seek time, but it is reached over PCIe or SATA, which is far narrower and slower than the memory bus.
    - `Magnetic HD` must physically move a head and wait for the platter to rotate under it. Sequential transfer is respectable, but random access costs milliseconds.
    - `Flash drive` uses the same kind of NAND flash as an SSD, but with a cheap controller, fewer parallel chips and the USB bus as a bottleneck. A USB 2.0 drive is limited to about 40 MB/s.
    - `DVD` is slowest of all: a laser reads a spinning plastic disc, and even 16x speed is only about 22 MB/s.

    - Two related points worth stating. First, `random access` widens the gap far more than sequential transfer does — an SSD is roughly 100 times faster than a hard disk at random reads but only 3-5 times faster sequentially. Second, this order is exactly the `memory hierarchy`: speed falls and capacity rises as you move away from the CPU.

15. **Which of the following is non volatile memory? (a) SRAM (b) DRAM (c) ROM (d) HDD** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

    Answer: The non-volatile options are `(c) ROM` and `(d) HDD`.

    - `Non-volatile` memory keeps its contents when the power is switched off. `Volatile` memory loses everything.

    Option by option
    ```
       (a) SRAM : VOLATILE
           Each cell is a 6-transistor flip-flop. It holds its value only while
           power is applied. Used for cache memory.

       (b) DRAM : VOLATILE
           Each cell is 1 transistor + 1 capacitor. The charge leaks away, so
           it must be refreshed, and everything is lost at power-off.
           Used for main memory.

       (c) ROM  : NON-VOLATILE
           Holds firmware - the BIOS and bootstrap loader - which must survive
           a power cut, since the machine has to start from it.

       (d) HDD  : NON-VOLATILE
           Data is stored as magnetic polarity on a platter, which does not
           depend on power at all.
    ```

    - If the question expects a `single` answer from the memory devices proper, it is `(c) ROM`, because SRAM, DRAM and ROM are all semiconductor memories and only ROM among them is non-volatile. A hard disk is secondary storage rather than memory, though it is certainly non-volatile too.

    Volatile and non-volatile at a glance

    | Type | Volatile? | Used for |
    |---|---|---|
    | Registers | Yes | Current operands inside the CPU |
    | SRAM (cache) | Yes | Hiding main-memory latency |
    | DRAM (main memory) | Yes | Running programs and their data |
    | ROM / EEPROM / Flash | No | Firmware, BIOS, embedded programs |
    | HDD, SSD, optical, tape | No | Permanent file storage |

    - Why it matters at start-up: RAM is empty when the machine is switched on, so the CPU must begin executing from `non-volatile` ROM. The BIOS there tests the hardware and loads the operating system from the disk into RAM.

16. **(b) Here are given 4 types of different memory. Which memory is the faster? Write in sequence order in the following figure: Register, Hard disk, Cache, RAM.** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 821 (ET: BUET)]*

    Answer: In order from `fastest` to `slowest`:
    ```
       1. Register
       2. Cache
       3. RAM
       4. Hard disk
    ```

    The memory hierarchy
    ```
                  /\
                 /  \        1. REGISTER   ~1 cycle       bytes
                /----\       2. CACHE      4-40 cycles    KB-MB
               /------\      3. RAM        ~200 cycles    GB
              /--------\     4. HARD DISK  10^7 cycles    TB
             /__________\

       Going down : slower, larger, cheaper per byte
       Going up   : faster, smaller, costlier per byte
    ```

    Why the order is this way

    | Rank | Memory | Access time | Location | Technology |
    |---|---|---|---|---|
    | 1 | Register | ~1 clock cycle (0.3 ns) | Inside the CPU | Flip-flops |
    | 2 | Cache | 4-40 cycles (1-15 ns) | On or beside the CPU die | SRAM |
    | 3 | RAM | ~200 cycles (50-100 ns) | On the motherboard | DRAM |
    | 4 | Hard disk | 5-10 milliseconds | Separate drive | Magnetic platter |

    - `Register` is inside the ALU's own data path, so the value is already where it is needed. Nothing can be faster.
    - `Cache` is SRAM millimetres away on the same die, with a very wide internal bus.
    - `RAM` is DRAM on the motherboard, reached over the external memory bus, and its capacitor cells are inherently slower than flip-flops.
    - `Hard disk` has to move a mechanical head and wait for the platter to spin under it. It is roughly `a million times` slower than RAM — the largest single gap in the whole hierarchy, and the reason SSDs replaced hard disks for system drives.

    The size of the gap, put in human terms
    ```
       If a register access took 1 second, then

          cache  would take about 10 seconds
          RAM    would take about 3 minutes
          HDD    would take about 4 months
    ```

    - Why the hierarchy works at all: the `principle of locality`. A program reuses the same instructions and data repeatedly (`temporal locality`) and reads neighbouring addresses (`spatial locality`), so a small fast level satisfies most requests and the slow levels are reached only occasionally.

17. **RAM and ROM difference লিখ?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 944 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) `RAM` is the computer's working memory — fast, read/write and volatile. `ROM` holds permanent firmware — non-volatile and normally read only.

    RAM (Random Access Memory)
    - Holds the operating system, the running programs and the data being worked on.
    - `Volatile`: everything is lost when the power goes off.
    - Freely `read and written` at full speed.
    - Types: `SRAM` (flip-flop cell, no refresh, fast, used for cache) and `DRAM` (capacitor cell, needs refresh, cheap, used for main memory).

    ROM (Read Only Memory)
    - Holds the firmware needed at power-on: the BIOS/UEFI, the bootstrap loader, and the fixed program of an embedded device.
    - `Non-volatile`: the contents survive a power cut.
    - Written by the manufacturer, or rewritten only slowly with a special procedure.
    - Types: `MROM`, `PROM`, `EPROM`, `EEPROM`, `Flash`.

    Difference

    | Point | RAM | ROM |
    |---|---|---|
    | Full form | Random Access Memory | Read Only Memory |
    | Volatility | Volatile | Non-volatile |
    | Read / write | Both | Read normally; writing slow or impossible |
    | Speed | Very fast | Slower to write |
    | Capacity | Large (4-64 GB) | Small (KB to a few MB) |
    | Cost per byte | Higher | Lower |
    | Contents | Programs and data in use | Firmware, BIOS |
    | Changed by the user | Constantly | Rarely or never |
    | Types | SRAM, DRAM | MROM, PROM, EPROM, EEPROM, Flash |
    | Power consumption | Higher | Lower |
    | Purpose | Temporary working storage | Permanent instructions |

    - How they cooperate at start-up: RAM is empty at power-on, so the CPU begins fetching from `ROM`. The BIOS there tests the hardware and loads the operating system from disk into `RAM`, after which the machine runs out of RAM.

18. **(a) Write the difference between: (i) RAM and ROM (ii) Open source software and Proproetary software.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1023-1024 (ET: N/A)]*

    Answer: (i) RAM and ROM

    `RAM` is the working memory: fast, read/write, volatile, holding the operating system and the running programs. `ROM` holds permanent firmware: non-volatile and normally read only.

    | Point | RAM | ROM |
    |---|---|---|
    | Full form | Random Access Memory | Read Only Memory |
    | Volatility | Volatile — lost at power-off | Non-volatile — retained |
    | Read / write | Both, freely | Read normally; writing slow or impossible |
    | Speed | Very fast | Slower to write |
    | Capacity | Large (4-64 GB) | Small (KB to a few MB) |
    | Cost per byte | Higher | Lower |
    | Contents | Programs and data in use now | BIOS, bootstrap loader, firmware |
    | Types | SRAM, DRAM | MROM, PROM, EPROM, EEPROM, Flash |
    | Purpose | Temporary working storage | Permanent instructions |

    - At power-on, RAM is empty, so the CPU must start from `ROM`. The BIOS there tests the hardware and loads the operating system from disk into `RAM`.

    (ii) Open source software and proprietary software

    `Open source software` publishes its `source code` under a licence that allows anyone to read, modify and redistribute it. `Proprietary software` keeps the source code secret and is licensed only as a compiled binary, under conditions set by the owner.

    | Point | Open source software | Proprietary software |
    |---|---|---|
    | Source code | Public, freely available | Secret, kept by the vendor |
    | Cost | Usually free | Paid licence |
    | Modification | Allowed and encouraged | Prohibited by licence |
    | Redistribution | Allowed under the licence | Prohibited |
    | Licence | GPL, Apache, MIT, BSD | EULA, per-seat or subscription |
    | Developed by | A community of contributors | One company's employees |
    | Support | Community forums; paid support optional | Official vendor support included |
    | Security | Many eyes can find and fix bugs | Depends on the vendor; flaws stay hidden |
    | Updates | Frequent, community driven | On the vendor's schedule |
    | Vendor lock-in | Low — the code can be forked | High |
    | Customisation | Complete | None beyond what is offered |
    | Accountability | No single party responsible | The vendor is contractually responsible |
    | Examples | Linux, Apache, MySQL, LibreOffice, Firefox, Android | Windows, macOS, MS Office, Oracle, Photoshop |

    - Practical trade: open source gives `control and low cost` but requires in-house skill; proprietary gives `support and accountability` but costs money and creates dependence on the vendor. Many organisations, including government offices, mix the two — Linux servers running proprietary application software.

19. **(b) Outline the functions performed by memory. List some factors upon which memory can be classified.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1024 (ET: N/A)]*

    Answer: Functions performed by memory
    - `Store the program` currently being executed, so the CPU can fetch its instructions.
    - `Store the data` the program is working on, and the intermediate and final results.
    - `Hold the operating system` and the firmware needed to start the machine.
    - `Store files permanently` for future use — the job of secondary memory.
    - `Supply the CPU on demand`, delivering an instruction or an operand whenever it is requested.
    - `Act as a buffer` between devices working at different speeds — a print spooler, a disk cache, an I/O buffer.
    - `Provide addressability`: every location has a unique address, so any item can be found directly.
    - `Support multiprogramming`, by holding several processes at once with protection between them.
    - `Provide virtual memory`, so that a program larger than physical RAM can still run, with the operating system swapping pages to disk.
    - `Retain data without power`, in the non-volatile levels.

    Factors on which memory is classified

    1. `Volatility`
    ```
       Volatile     : contents lost at power-off  -> RAM, cache, registers
       Non-volatile : contents retained           -> ROM, HDD, SSD, flash
    ```

    2. `Position in the hierarchy and proximity to the CPU`
    ```
       Registers -> Cache -> Primary (RAM, ROM) -> Secondary -> Tertiary
    ```

    3. `Access method`
    ```
       Random access     : any location reached directly - RAM, SSD
       Sequential access : must pass through everything before it - magnetic tape
       Direct access     : a mixture of the two - hard disk
       Associative       : searched by content rather than address - cache tags
    ```

    4. `Read / write capability`
    ```
       Read-write   : RAM, hard disk
       Read-only    : ROM, CD-ROM
       Write-once   : PROM, CD-R
       Read-mostly  : EPROM, EEPROM, Flash
    ```

    5. `Technology used`
    ```
       Semiconductor : RAM, ROM, cache, SSD, pen drive
       Magnetic      : hard disk, floppy disk, magnetic tape
       Optical       : CD, DVD, Blu-ray
    ```

    6. `Speed / access time`
    ```
       Registers ~1 cycle , cache 4-40 , RAM ~200 , SSD 10^4 , HDD 10^7
    ```

    7. `Capacity` — bytes for registers, kilobytes to megabytes for cache, gigabytes for RAM, terabytes for disks.

    8. `Cost per bit` — highest for registers, lowest for tape and optical media.

    9. `Physical location` — internal (on the motherboard or the CPU) or external (removable drives, cloud).

    10. `Portability` — fixed (RAM, internal hard disk) or removable (pen drive, SD card, DVD).

    11. `Power consumption and volatility of the storage mechanism` — DRAM needs constant refreshing; SRAM and flash do not.

    - The classification matters because it explains the `hierarchy`: fast memory is expensive and small, slow memory is cheap and large, so a computer uses a little of each and relies on the `principle of locality` to make the arrangement work.

20. **(c) Given below the list of some memory devices. Identify which are semi-conductor, optical and magnetic memory. CD, RAM, Floppy Disk, Hard Disk, ROM, DVD.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1024 (ET: N/A)]*

    Answer: The six devices classified by the technology that stores the data.

    Semiconductor memory
    ```
       RAM
       ROM
    ```
    - Data is held in `transistors and capacitors` on a silicon chip. There are no moving parts, so access is very fast — nanoseconds.
    - `RAM` is volatile; `ROM` is non-volatile.
    - Other examples: cache, SSD, pen drive, SD card, EEPROM, flash.

    Magnetic memory
    ```
       Floppy Disk
       Hard Disk
    ```
    - Data is stored as the `direction of magnetisation` of tiny regions on a coated surface. A read/write head moves over a spinning platter.
    - Non-volatile, mechanical, and therefore slow — milliseconds — but very cheap per byte and large in capacity.
    - Other examples: magnetic tape, magnetic drum.

    Optical memory
    ```
       CD
       DVD
    ```
    - Data is stored as microscopic `pits and lands` burned into a reflective layer, and read by a `laser` that detects the change in reflection.
    - Non-volatile, removable, cheap to duplicate, but slow and limited in capacity.
    - Other examples: Blu-ray, CD-R, CD-RW, DVD-R.

    Summary

    | Device | Category | How data is stored | Volatile? |
    |---|---|---|---|
    | CD | Optical | Pits and lands read by a laser | No |
    | RAM | Semiconductor | Charge in transistors and capacitors | Yes |
    | Floppy Disk | Magnetic | Magnetised regions on a flexible disc | No |
    | Hard Disk | Magnetic | Magnetised regions on a rigid platter | No |
    | ROM | Semiconductor | Fixed transistor pattern or trapped charge | No |
    | DVD | Optical | Pits and lands, denser than CD | No |

    Capacity and speed, for comparison
    ```
       Floppy Disk : 1.44 MB     obsolete
       CD          : 700 MB      1.3-7.8 MB/s
       DVD         : 4.7-8.5 GB  1.3-22 MB/s
       Hard Disk   : 500 GB-20 TB  100-200 MB/s
       RAM         : 4-64 GB     20-50 GB/s
       ROM         : KB to MB    comparable to RAM for reading
    ```

    - The trend to note: semiconductor storage has been steadily replacing both of the others. `SSDs` (semiconductor) have displaced hard disks in laptops, and `pen drives` and cloud storage have displaced CDs and DVDs entirely.

21. **How Maximum size of memory (RAM) is needed that can be addressed by 32-bit system.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1031 (ET: BUET)]*

    Answer: The amount of memory a processor can address is set by the width of its `address bus`.
    ```
       Addressable memory = 2^(number of address lines) x (size of one location)
    ```
    - In almost every modern computer each location holds `one byte` — this is `byte addressing`.

    Calculation for a 32-bit system
    ```
       Number of address lines = 32

       Number of addressable locations = 2^32
                                       = 4,294,967,296 locations

       Each location = 1 byte

       Total = 4,294,967,296 bytes
    ```

    Convert to convenient units
    ```
       4,294,967,296 bytes
          / 1024 = 4,194,304 KB
          / 1024 = 4,096 MB
          / 1024 = 4 GB
    ```
    ```
       Maximum addressable RAM = 4 GB
    ```

    Shortcut worth memorising
    ```
       2^10 = 1 K        2^20 = 1 M        2^30 = 1 G

       2^32 = 2^2 x 2^30 = 4 x 1 G = 4 GB
    ```

    Why a 32-bit machine usually shows less than 4 GB
    - Part of that 4 GB address space is reserved for hardware, not for RAM: graphics card memory, BIOS ROM, PCI device windows and I/O mapping. This is `memory-mapped I/O`.
    - So a 32-bit Windows system with 4 GB installed typically reports only `3.2 to 3.5 GB` as usable. The rest is not missing, it is occupied by device addresses.
    - `PAE` (Physical Address Extension) works around this by widening the physical address to 36 bits, giving 64 GB, though any single process is still limited to 4 GB.

    Other bus widths, for comparison
    ```
       16-bit : 2^16 = 64 KB          (8085)
       20-bit : 2^20 = 1 MB           (8086)
       32-bit : 2^32 = 4 GB
       64-bit : 2^64 = 16 EB in theory
                in practice 48 address lines are implemented -> 256 TB
    ```

    - The distinction to state clearly: the `data bus` decides how many bits move per transfer and therefore the speed; the `address bus` decides how much memory can be reached and therefore the capacity. The two are independent.

22. **What is access time and transfer time?** *[Bangladesh Television Assistant Programmer 2019 compact it 1066 (ET: N/A)]*

    Answer: Both describe how long a memory or storage operation takes, but they measure different parts of it.

    Access time
    - The time from the moment a request is issued until the `first` item of data is available.
    - It is the `latency` — the waiting part of the operation, and it does not depend on how much data is being read.
    ```
       Access time = seek time + rotational latency + controller overhead
    ```
    - For a hard disk:
    ```
       Seek time          : moving the head to the right track   ~4-9 ms
       Rotational latency : waiting for the sector to arrive     ~2-4 ms
       Total access time  : ~5-12 ms
    ```
    - For semiconductor memory there is no mechanical part, so access time is the electrical delay only:
    ```
       Register :  ~0.3 ns        Cache : 1-15 ns
       RAM      :  50-100 ns      SSD   : 20-100 microseconds
    ```

    Transfer time
    - The time taken to actually `move the data` once it has been found. It depends directly on how much data there is.
    ```
       Transfer time = amount of data / transfer rate
    ```
    - Example: reading 10 MB from a disk whose transfer rate is 200 MB/s
    ```
       Transfer time = 10 / 200 = 0.05 s = 50 ms
    ```

    Total time for one operation
    ```
       Total time = access time + transfer time
    ```
    ```
       Reading one 512-byte sector from a hard disk :
          access time   = 10 ms          (dominates completely)
          transfer time = 512 B / 200 MB/s = 0.0026 ms
          total         ~ 10 ms

       Reading a 100 MB file from the same disk :
          access time   = 10 ms
          transfer time = 100 / 200 = 500 ms   (now dominates)
          total         ~ 510 ms
    ```

    Comparison

    | Point | Access time | Transfer time |
    |---|---|---|
    | Measures | Waiting to reach the data | Moving the data |
    | Also called | Latency | Data transfer / throughput time |
    | Depends on data size | No | Yes, directly proportional |
    | Depends on | Seek, rotation, electrical delay | Transfer rate and amount of data |
    | Units | Nanoseconds to milliseconds | Depends on the amount |
    | Improved by | Faster mechanics, no mechanics at all (SSD) | Wider or faster bus |

    - Why the distinction matters in practice: for `many small random reads` — which is what an operating system does most — `access time` decides performance, and this is exactly where an SSD beats a hard disk by a factor of about a hundred. For `one large sequential read` the transfer rate matters more, and there the gap narrows to three or four times.

23. **(ক) Memory address register and Memory buffer register কী? Primary memory and Secondary memory-এর মধ্যে পার্থক্য লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1069-1070 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Memory Address Register (MAR)
    - A CPU register that holds the `address` of the memory location the processor is about to read from or write to.
    - Its contents are placed directly on the `address bus`, so its width equals the number of address lines. A 32-bit MAR can address 2^32 = 4 GB.
    - It is `unidirectional` — the CPU only writes into it, and the address only travels outward to memory.

    Memory Buffer Register (MBR), also called the Memory Data Register (MDR)
    - A CPU register that holds the `data` just read from memory, or the data about to be written to it.
    - It is connected to the `data bus`, so its width equals the word size — 8, 16, 32 or 64 bits.
    - It is `bidirectional`, since data travels both to and from memory.

    How they work together
    ```
       MEMORY READ
          1. CPU loads the address into MAR
          2. MAR drives the address bus
          3. CPU asserts READ on the control bus
          4. Memory places the contents on the data bus
          5. MBR latches it
          6. The value is copied from MBR into a working register

       MEMORY WRITE
          1. CPU loads the address into MAR and the data into MBR
          2. MAR drives the address bus, MBR drives the data bus
          3. CPU asserts WRITE
          4. Memory stores the value
    ```
    ```
            CPU                                   MEMORY
       +-------------+                        +-------------+
       |    MAR      |=== address bus =======>|             |
       +-------------+                        |             |
       |    MBR      |<== data bus ==========>|             |
       +-------------+                        +-------------+
       |  control    |--- read / write ------>|             |
       +-------------+                        +-------------+
    ```

    | Point | MAR | MBR / MDR |
    |---|---|---|
    | Holds | The memory address | The data at that address |
    | Connected to | Address bus | Data bus |
    | Direction | Unidirectional (out) | Bidirectional |
    | Width equals | Number of address lines | Word size |
    | Set by | The CPU, before every access | The CPU or the memory |

    Primary versus secondary memory

    `Primary memory` is directly addressable by the CPU; a program must be loaded here before it can run. It is fast, expensive and small — RAM and ROM.

    `Secondary memory` is permanent bulk storage that the CPU cannot address directly; data must be copied into primary memory first. It is slow, cheap and very large — hard disk, SSD, optical disc, pen drive.

    | Point | Primary memory | Secondary memory |
    |---|---|---|
    | CPU access | Direct | Indirect, through primary |
    | Speed | Nanoseconds | Microseconds to milliseconds |
    | Capacity | Gigabytes | Terabytes |
    | Cost per byte | High | Very low |
    | Volatility | RAM volatile, ROM not | Always non-volatile |
    | Purpose | Hold what is running now | Store everything permanently |
    | Technology | Semiconductor | Magnetic, optical, flash |
    | Portability | Fixed | Often removable |
    | Examples | RAM, ROM, cache | HDD, SSD, DVD, pen drive |

24. **(b) Difference between SRAM and DRAM.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1134-1136 (ET: N/A)]*

    Answer: Both are volatile read/write memories; every difference follows from the `cell design`.

    `SRAM` (Static RAM)
    - Each cell is a `flip-flop` of `6 transistors`, holding its value as long as power is applied.
    - `No refresh` is needed, because the cross-coupled inverters keep reinforcing the bit.
    - Fast, but the large cell makes it costly and limits capacity.

    `DRAM` (Dynamic RAM)
    - Each cell is `1 transistor + 1 capacitor`, storing the bit as charge.
    - The charge leaks, so every row must be `refreshed` every few milliseconds.
    - The tiny cell makes it dense and cheap, so gigabyte capacities are practical.

    Difference

    | Point | SRAM | DRAM |
    |---|---|---|
    | Cell structure | 6 transistors (flip-flop) | 1 transistor + 1 capacitor |
    | Refresh required | No | Yes, every few milliseconds |
    | Access time | 1-10 ns | 50-70 ns |
    | Speed | Much faster | Slower |
    | Density | Low | Very high |
    | Capacity per chip | KB to MB | GB |
    | Cost per bit | High | Low |
    | Idle power | Low | Higher — refresh runs constantly |
    | Extra circuitry | None | Refresh controller required |
    | Heat | Less | More |
    | Used in | Cache (L1, L2, L3), registers | Main memory |
    | Volatile | Yes | Yes |
    | Types | Asynchronous, synchronous, pipeline burst | SDRAM, DDR to DDR5 |

    - The trade in one line: `SRAM buys speed by spending silicon area; DRAM buys capacity by accepting refresh overhead`.
    - Both appear in every computer — a few megabytes of SRAM cache in front of many gigabytes of DRAM. The cache hides the DRAM's latency while the DRAM supplies the capacity.

25. **Write the Memory faster access time memory in top and lowest access time memory is below from the following memory: [Cache Memory, Register Memory, Main Memory, Magnetic Tapes and Magnetic Disks.]** *[NWPGCL Assistant Engineer (CSE) 2019 compact it 1153 (ET: RUET)]*

    Answer: In order from `fastest access time` at the top to `slowest` at the bottom:
    ```
       1. Register Memory
       2. Cache Memory
       3. Main Memory
       4. Magnetic Disks
       5. Magnetic Tapes
    ```

    The hierarchy
    ```
                  /\
                 /  \        1. Register memory   ~0.3 ns      bytes
                /----\       2. Cache memory      1-15 ns      KB-MB
               /------\      3. Main memory       50-100 ns    GB
              /--------\     4. Magnetic disk     5-10 ms      TB
             /----------\    5. Magnetic tape     seconds      TB
            /____________\

       Going down : slower, larger, cheaper per byte
    ```

    | Rank | Memory | Access time | Capacity | Technology | Access method |
    |---|---|---|---|---|---|
    | 1 | Register | ~0.3 ns (1 cycle) | Bytes | Flip-flops in the CPU | Random |
    | 2 | Cache | 1-15 ns | KB to MB | SRAM | Random |
    | 3 | Main memory | 50-100 ns | GB | DRAM | Random |
    | 4 | Magnetic disk | 5-10 ms | GB to TB | Rotating magnetic platter | Direct |
    | 5 | Magnetic tape | Seconds to minutes | TB | Magnetic tape reel | `Sequential` |

    Why this order
    - `Register` sits inside the CPU's own data path, so the value is already where the ALU needs it.
    - `Cache` is SRAM on the same die, only millimetres away, with a very wide internal bus.
    - `Main memory` is DRAM on the motherboard, reached over the external memory bus, and its capacitor cells are inherently slower than flip-flops.
    - `Magnetic disk` must move a mechanical head and wait for the platter to rotate — milliseconds, about a million times slower than RAM.
    - `Magnetic tape` is worst of all because it is `sequential access`: to reach data in the middle, the whole tape before it must be wound past the head. That is why tape survives only for backup and archiving, where cost per terabyte matters and access speed does not.

    The size of the gaps, in human terms
    ```
       If a register access took 1 second, then

          cache        ~ 10 seconds
          main memory  ~ 3 minutes
          hard disk    ~ 4 months
          tape         ~ years
    ```

    - Why the hierarchy works: the `principle of locality`. A program reuses the same instructions and data (temporal locality) and reads neighbouring addresses (spatial locality), so a small fast level answers most requests and the slow levels are reached rarely.

26. **Difference between ROM and RAM.** *[ICT Ministry Assistant Programmer 2017 compact it 1240-1241 (ET: N/A)]*

    Answer: `ROM` holds permanent firmware — non-volatile and normally read only. `RAM` is the working memory — fast, read/write and volatile.

    ROM (Read Only Memory)
    - Holds what the machine needs at power-on: the BIOS/UEFI, the bootstrap loader, and the fixed program of an embedded device.
    - `Non-volatile`: the contents survive a power cut, which is essential, because the CPU has nothing else to execute when the machine is first switched on.
    - Written by the manufacturer, or rewritten only slowly with a special procedure.
    - Types: `MROM` (masked, fixed), `PROM` (write once), `EPROM` (erased by ultraviolet light), `EEPROM` (erased electrically, byte by byte), `Flash` (block erasable).

    RAM (Random Access Memory)
    - Holds the operating system, the running programs and their data.
    - `Volatile`: everything is lost when the power goes off.
    - Freely read and written at full speed.
    - Types: `SRAM` (flip-flop cell, no refresh, fast, used for cache) and `DRAM` (capacitor cell, needs refresh, cheap, used for main memory).

    Difference

    | Point | ROM | RAM |
    |---|---|---|
    | Full form | Read Only Memory | Random Access Memory |
    | Volatility | Non-volatile — retained | Volatile — lost at power-off |
    | Read / write | Read normally; writing slow or impossible | Both, freely |
    | Speed | Slower to write | Very fast |
    | Capacity | Small (KB to a few MB) | Large (4-64 GB) |
    | Cost per byte | Lower | Higher |
    | Contents | BIOS, firmware, bootstrap loader | Programs and data in use now |
    | Changed by the user | Rarely or never | Constantly |
    | Power consumption | Lower | Higher (DRAM refresh) |
    | Types | MROM, PROM, EPROM, EEPROM, Flash | SRAM, DRAM |
    | Purpose | Permanent instructions | Temporary working storage |

    - How they cooperate at start-up: RAM is empty when the power comes on, so the CPU begins fetching instructions from `ROM`. The BIOS there tests the hardware and loads the operating system from disk into `RAM`, and from that moment the machine runs out of RAM.

## RAID Architecture & Storage (15)

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

14. **What is RAID level? Write down of RAID level 0, level 1 and level 5?** *[Dutch Bangla Bank Assistant Network/Hardware Engineer 2019 compact it 1159 (ET: BUET)]*

15. **Describe RAID level.** *[Dutch Bangla Bank Ltd. Probationary Officer (Software) 2018 compact it 1199 (ET: N/A)]*

## Cache Memory (14)

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

13. **If main memory access time is 100ns, cache access time is 50 ns, cache hit rate is 90% then what is the average time to read from memory?** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1228 (ET: N/A)]*

14. **Explain how cache memory is used to increase the processing speed of computer.** *[Multiple Ministry Assistant Programmer 2017 compact it 1230-1231 (ET: N/A)]*

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

## Instruction Pipelining & Hazards (9)

1. Why do modern processor designs favor a multi-stage pipelined approach over a single-cycle implementation? [SO IT 25-07-2026]

2. **Write down the names of different stages of instruction pipelining in a multi-cycle datapath architecture. What is a data-hazard in a pipelined datapath?** *[BPSC (Ministry) Network/Website Manager (CSE) 21.05.2025 compact it 1340 (ET: N/A)]*

3. **(c) Fill in the gaps RISC or CISC:** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 416 (ET: BUET)]*
   * (i) Pipelining is less efficient due to instruction complexity and variability ______
   * (ii) Emphasis on hardware simplicity and efficiency ______
   * (iii) Complex decoding due to variable instruction length ______
   * (iv) Each instruction typically executes in a single clock cycle ______

4. **Difference between mutliprocessor system and multi computer system, Explain Shared memory; discuss the two schemes to maintain cache coherence. What is pipelining? Explain the 4 stages of the pipeline.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 299 (ET: BIBM)]*

5. **6.1 Why do modern processor designs favor a multi-stage pipelined approach over a single-cycle implementation?** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

6. **How computer Architecture is characterized. What are the 5 stages of the DLX pipeline?** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1049-1050 (ET: BUET)]*

7. **“Pentium processor has a superscalar architecture.” Explain the meaning of statement.** *[Multiple Ministry Assistant Programmer 2017 compact it 1233 (ET: N/A)]*

8. **Using pipeline calculate the value of fetch and execution cycle.** *[BTCL Assistant Manager (Technical) 2017 compact it 1255 (ET: N/A)]*

9. **What is pipelining? What is opcode and operand in machine code? Explain snooping cache.** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 1277 (ET: N/A)]*

## Assembly Language & Addressing Modes (8)

1. (a) চয়ন করুন: (i) Propagation delay; (ii) Transmission delay;
   (b) SIMD instruction এর সংক্ষিপ্ত বর্ণনা লিখুন: MOV AX, A334H এবং MOV AX, [A334H] *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

2. **Explain the difference between direct, immediate, and register addressing modes in the 8086 microprocessor.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1424 (ET: E-Zone)]*

3. **(খ) নিচের instruction দুটির মাঝে পার্থক্য লিখুন:** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*
MOV AX, A534H এবং MOV AX, [A534H]

4. **(b) Explain the operations of the following instructions: (i) ADC (ii) CMP (iii) JBE** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 691 (ET: N/A)]*

5. **Assembly Language Instructions এর ক্ষেত্রে নিম্মোক্ত Instructions গুলোর কাজ লিখুন। ADC, XCHG, POP ও JNZ.** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1041 (ET: DPI)]*

6. **Write down four common rules of Assembly language. Write different type of hazard.** *[Sonali & Janata Bank Officer (IT/ICT) 2019 compact it 1104 (ET: AUST)]*

7. **Describe addressing mode of 8086 microprocessors.** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1225-1226 (ET: N/A)]*

8. **Explain the instructions LDS, PUSHF, TEST and CLD.** *[Multiple Ministry Assistant Programmer 2017 compact it 1235 (ET: N/A)]*

## CPU Performance & Instruction Cycle (6)

1. **There was a CPU cycle math** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 400 (ET: BUET)]*

2. **(খ) Clock cycle কী? একটি মাইক্রো-প্রসেসরের speed 3.5 GHz বলতে কী বোঝায়?** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

3. **A program (or a program task) takes 1 billion instructions to execute on a processor running at 2 GHz. Suppose also that 50% of the instructions execute in 3 clock cycles, 30% execute in 4 clock cycles, and 20% execute in 5 clock cycles. What is the execution time for the program or task?** *[RAKUB Programmer (PO) 12.10.2021 compact it 847 (ET: N/A)]*

4. **Operating system math: clock frequency 700MHz.** *[RAKUB Programmer (PO) 12.10.2021 compact it 852 (ET: N/A)]*

5. **Computer A has 3.2GHz processing speed and it has 2.0 clock speeds in a program and at the same program Computer B has 2.4 GHz processing speed with 1.2 clock speed. Which computer will run faster and how much faster?** *[DESCO Assistant Engineer (CSE) 2019 compact it 1118-1119 (ET: BUET)]*

6. **Write down factor of microprocessor speed?** *[BREB Assistant Hardware & Network Engineer 2019 compact it 1124-1125 (ET: BREB)]*

## Multi-Core & Multi-Threading (5)

1. **Core vs thread in networking?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

2. **Core i5 and i7 Microprocessor এর মধ্যে হার্ডওয়্যারগত মূল পার্থক্য কী?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 698 (ET: DPI)]*

3. **What is Hyper threading? What is the use of it?** *[BOF Assistant Programmer 2022 compact it 733 (ET: MIST)]*

4. **Now a day, core i3, i5, i7 and i9 CPUs are aavailable. The higher the number is that means powerful processor. What is hyper threading? What does 2 core and 4 thread means?** *[BTRC Assistant Director (Technical) 2021 compact it 808 (ET: IBA)]*

5. **১৩. Core i7 জেনারেশন এর প্রসেসর এর উদাহরণ লিখ?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 942 (ET: N/A)]*

## RISC vs CISC Architecture (4)

1. **RISC stand for __________? Write two characteristics of it's?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

2. **Difference between RISC and CISC.** *[NPCBL Executive Trainee (IT) 2022 compact it 644 (ET: BUET)]*

3. **(ক) CISC and RISC processor বলতে কি বোঝেন?** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1072 (ET: N/A)]*

4. **What is CISC and RISC?** *[BREB Assistant Hardware & Network Engineer 2019 compact it 1124 (ET: BREB)]*

## 8085 Microprocessor & Edge Computing (3)

1. (a) Edge Computing এর ধারণা সংক্ষেপে ব্যাখ্যা করুন।
   (b) 8085 মাইক্রোপ্রসেসর কী? রেজিস্টারের ইফেক্টিভ মেমোরি অ্যাড্রেসিং কার্যকারিতা ব্যাখ্যা করুন। *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

2. **Intel 8085 ও Intel 8086 Microprocessor-এর সর্বোচ্চ ফিজিক্যাল মেমোরি ক্যাপাসিটি কত এবং কেন?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 697 (ET: DPI)]*

3. **What is the difference between 8-bit (8085) and 16-bit (8086) microprocessor?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 865-866 (ET: BUET)]*
