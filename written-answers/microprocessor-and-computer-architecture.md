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

   Answer: There is `no single best RAID level` — the right choice depends on whether performance, capacity or safety matters most. But for general-purpose server use, `RAID 10` is usually called the best, and `RAID 5` the best value.

   RAID 10 (1 + 0) — the best overall
   ```
      Disk 1 --+-- mirror --+-- Disk 2
               |            |
            stripe       stripe
               |            |
      Disk 3 --+-- mirror --+-- Disk 4
   ```
   - `Fastest reads and writes.` It has no parity to compute, so there is no write penalty beyond the mirroring itself.
   - `Excellent fault tolerance.` One disk from each mirrored pair can fail, and the array survives.
   - `Fastest rebuild.` A replaced disk is simply copied from its mirror, so there is no parity to recalculate and little extra load on the array.
   - `No write hole` and no risk of a second failure during a long rebuild.
   - Cost: only `50 per cent` of the raw capacity is usable, and it needs a minimum of `4` disks.
   - Used for: database servers, transaction processing, virtualisation, and any write-heavy workload.

   RAID 5 — the best balance of capacity and safety
   - Striping with `distributed parity`. Usable capacity is `(n-1)/n`, so with 5 disks 80 per cent is available against RAID 10's 50 per cent.
   - Survives `one` disk failure, and read performance is excellent.
   - Weaknesses: the `write penalty` — every write needs read-old-data, read-old-parity, write-new-data, write-new-parity, so four operations for one logical write. Rebuilds are slow and stress every remaining disk, and a second failure during that window destroys the array.
   - Used for: file servers, web servers, archives — read-heavy work where capacity matters.

   Comparison

   | Level | Min disks | Usable capacity | Fault tolerance | Read | Write | Best for |
   |---|---|---|---|---|---|---|
   | RAID 0 | 2 | 100 % | `None` | Fastest | Fastest | Scratch data, video editing |
   | RAID 1 | 2 | 50 % | 1 disk | Fast | Normal | OS drives, small critical volumes |
   | RAID 5 | 3 | (n-1)/n | 1 disk | Fast | Slow (4 ops) | File servers, capacity with safety |
   | RAID 6 | 4 | (n-2)/n | `2 disks` | Fast | Slower (6 ops) | Large arrays, big slow drives |
   | RAID 10 | 4 | 50 % | 1 per mirror | Very fast | `Very fast` | Databases, virtualisation |

   Which to choose in practice
   ```
      Need maximum speed, data is disposable      -> RAID 0
      Two disks only, need safety                 -> RAID 1
      Need capacity and can tolerate slow writes  -> RAID 5
      Large disks (4 TB+), long rebuild worries   -> RAID 6
      Database or write-heavy server, budget ok   -> RAID 10   (the usual answer)
   ```

   - The point most examiners want stated: `RAID is not a backup`. It protects against `disk failure` only. It does nothing against accidental deletion, ransomware, file corruption, fire or theft, because every one of those is faithfully written to all the disks at once. A separate off-site backup is still required.

2. **Striping with parity is done in which level of RAID.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*

   Answer: Striping with parity is done in `RAID 5`.

   - `RAID 5` stripes the data across all the disks and also writes a `parity block` for each stripe. Crucially, the parity is `distributed` — it rotates from disk to disk, so no single drive becomes a bottleneck.
   ```
      Disk 1    Disk 2    Disk 3    Disk 4
      ------    ------    ------    ------
       A1        A2        A3        Ap      <- parity for stripe A on disk 4
       B1        B2        Bp        B4      <- parity for stripe B on disk 3
       C1        Cp        C3        C4      <- parity for stripe C on disk 2
       Dp        D2        D3        D4      <- parity for stripe D on disk 1
   ```
   - Parity is computed by `XOR`:
   ```
      Ap = A1 XOR A2 XOR A3
   ```
   - If one disk fails, the missing block is recovered by XOR-ing the survivors:
   ```
      A2 = A1 XOR A3 XOR Ap
   ```
   - Minimum `3` disks. Usable capacity is `(n-1)/n` — with 4 disks, 75 per cent. It survives `one` disk failure.

   Related levels, for completeness
   ```
      RAID 3 : byte-level striping with a DEDICATED parity disk
      RAID 4 : block-level striping with a DEDICATED parity disk
               (the parity disk becomes a bottleneck, so both are obsolete)
      RAID 5 : block-level striping with DISTRIBUTED parity   <- the answer
      RAID 6 : block-level striping with DOUBLE distributed parity,
               survives TWO disk failures, minimum 4 disks
   ```

   The write penalty of RAID 5
   ```
      One logical write requires FOUR physical operations :

         1. read the old data block
         2. read the old parity block
         3. write the new data block
         4. write the new parity block

      new parity = old parity XOR old data XOR new data
   ```
   - This is why RAID 5 is excellent for reads but poor for write-heavy work such as a busy database, where RAID 10 is preferred.

   - Short answer: `RAID 5` — block-level striping with distributed parity. If the question means `dedicated` parity, the answer is RAID 3 or RAID 4; if it means `double` parity, RAID 6.

3. **Concept of RAID, Relevance in Database, Uses in Database, is it possible?** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 319 (ET: N/A)]*

   Answer: Concept of RAID
   - `RAID` stands for `Redundant Array of Independent Disks`. It combines several physical disks into `one logical drive`, so that the operating system sees a single volume.
   - Its three purposes are `performance`, `fault tolerance` and `capacity`, achieved by three techniques:
   ```
      Striping  : data is split across several disks, so they are read
                  and written in parallel  -> speed
      Mirroring : the same data is written to two disks  -> redundancy
      Parity    : an XOR checksum lets a lost block be reconstructed
                  -> redundancy at lower cost than mirroring
   ```

   Common levels
   ```
      RAID 0  : striping only. Fastest, 100 % capacity, NO redundancy.
      RAID 1  : mirroring. 50 % capacity, survives one disk failure.
      RAID 5  : striping + distributed parity. (n-1)/n capacity,
                survives one failure, minimum 3 disks.
      RAID 6  : double parity. (n-2)/n capacity, survives TWO failures.
      RAID 10 : mirrored pairs, then striped. 50 % capacity, fastest
                redundant option, minimum 4 disks.
   ```

   Relevance to a database
   - A database is the workload that benefits from RAID most, because it is `I/O bound`. The CPU usually waits for the disk, so making the disk faster and safer directly improves the whole system.
   - `Availability.` A bank's core system cannot stop because one disk failed. RAID keeps the database running through a disk failure, and the drive is replaced by `hot swapping` without shutting down.
   - `Performance.` Striping spreads reads across several spindles, so many concurrent queries are served in parallel.
   - `Durability.` The `D` in ACID promises that a committed transaction survives. RAID is part of how that promise is kept at the hardware level.
   - `Separating the workload` matters more than the level chosen:
   ```
      Data files      : RAID 10 or RAID 5   (random reads and writes)
      Transaction log : RAID 1 or RAID 10   (sequential, write-heavy, latency
                                             critical - never RAID 5)
      tempdb / temp   : RAID 10 or even RAID 0 on separate spindles
      Backups         : RAID 5 or RAID 6    (capacity matters, speed does not)
   ```
   - The log deserves its own array because every commit must reach it before the transaction can return. Putting it on RAID 5, with a four-operation write penalty, slows every single transaction in the system.

   Is it possible to use RAID in a database — yes, and it is standard practice
   - Every production database server uses RAID. Oracle, SQL Server, MySQL and PostgreSQL all run on RAID volumes, and Oracle's `ASM` implements striping and mirroring in software at the database layer.
   - Cloud databases do the same thing invisibly: AWS RDS and Azure SQL replicate every block across multiple devices.

   Choosing the level
   ```
      OLTP, heavy writes, banking core   -> RAID 10
      Data warehouse, read-heavy         -> RAID 5 or RAID 6
      Very large disks, long rebuilds    -> RAID 6
      Transaction log                    -> RAID 1 or RAID 10, always
   ```

   - The essential caveat: `RAID is not a backup`. It protects only against `disk failure`. A dropped table, a ransomware attack, a corrupted page, a fire or a theft is written faithfully to every disk in the array at the same instant. A database still needs full backups, log backups and an off-site copy.

4. **How to solve drive failure in RAID?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1454 (ET: BUET)]*

   Answer: How a drive failure is handled depends on the RAID level and on whether the array is `degraded` or has already lost its data.

   Step 1 — detect the failure
   - The RAID controller raises an alert, an LED on the drive bay turns amber, and the management software (or a monitoring system such as Nagios or the vendor's tool) reports the array as `degraded`.
   - The array `keeps running` in degraded mode for RAID 1, 5, 6 and 10 — the data is still available, but with no protection left. RAID 0 has no redundancy, so a failure there means immediate total loss.

   Step 2 — act at once, and do not delay
   - A degraded array has `no fault tolerance`. A second failure in RAID 1 or 5 destroys everything. This is the most dangerous state a storage system can be in.

   Step 3 — verify the backup before touching anything
   - Confirm that a recent restorable backup exists. If the rebuild goes wrong — and it sometimes does — the backup is the only remaining copy.

   Step 4 — replace the failed drive
   ```
      Hot swap    : if the enclosure supports it, pull the failed drive and
                    insert the new one while the system keeps running.
                    This is the normal case in a server.
      Cold swap   : otherwise shut down, replace, and power up.
   ```
   - The replacement must be of the `same or larger capacity` and preferably the same model, and it must be `verified as the correct bay` — pulling the wrong drive from a degraded RAID 5 destroys the array instantly.

   Step 5 — rebuild
   ```
      RAID 1 / RAID 10 : the new disk is COPIED from its mirror.
                         Fast, and it stresses only one other drive.

      RAID 5           : every surviving disk is read in full and the missing
                         blocks are recomputed by XOR.
                         Slow, and it stresses ALL the remaining drives.

      RAID 6           : the same, but it can still survive one more failure
                         during the rebuild.
   ```
   - With a `hot spare` installed, the controller begins the rebuild `automatically` the moment the failure is detected, without waiting for a human. This is the single most valuable configuration choice.
   - Rebuild time for a modern large disk can be `several hours to more than a day`, and the array is vulnerable for that whole period.

   Step 6 — verify and restore protection
   - Check that the controller reports the array as `Optimal`, run a consistency check, verify the file system, and replace the hot spare that was consumed.

   What happens if the redundancy is already exhausted
   ```
      RAID 0, any failure                -> total loss, restore from backup
      RAID 1 or 5, second failure        -> total loss, restore from backup
      RAID 6, third failure              -> total loss, restore from backup
   ```
   - At that point the only options are the backup, or a specialist data-recovery service, which is expensive and never guaranteed.

   Preventing the problem in the first place
   - Configure a `hot spare`, so the rebuild starts immediately.
   - Monitor `SMART` attributes and replace a drive that is showing reallocated sectors `before` it fails.
   - Use `RAID 6` rather than RAID 5 for arrays of large drives, because a rebuild is long and the chance of a second failure during it is real.
   - Do not buy every disk from the same batch — drives from one production run tend to fail at similar times.
   - Keep `off-site backups`, because RAID protects against disk failure and nothing else.

5. **Explain the purpose of RAID.** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 564 (ET: N/A)]*

   Answer: `RAID` (Redundant Array of Independent Disks) combines several physical disks into one logical drive. Its purpose is to improve `performance`, `fault tolerance` and `capacity` beyond what a single disk can give.

   1. Fault tolerance and availability
   - The main purpose. A single disk `will` fail eventually; RAID makes that failure survivable.
   - `Mirroring` keeps a second copy; `parity` stores an XOR checksum from which a lost block can be recomputed.
   - The system keeps running in `degraded` mode while the failed drive is replaced, and with `hot swapping` there is no downtime at all.

   2. Improved performance
   - `Striping` splits data across several disks, so they are read and written in parallel. Four disks can, in principle, deliver four times the throughput of one.
   - Reads improve most, because a mirrored pair can serve two different requests at the same time.

   3. Larger logical capacity
   - Several physical drives appear as one large volume, so a file system can exceed the size of any single disk.

   4. Continuous operation
   - Combined with a `hot spare`, the array detects a failure and begins rebuilding on its own, with no human intervention and no service interruption. This is what a bank or a hospital needs.

   5. Data integrity
   - Parity and mirroring also allow the controller to detect and, in RAID 6 and modern implementations, correct silent data corruption.

   The three techniques it uses
   ```
      Striping  : split data across disks       -> speed
      Mirroring : duplicate data on two disks   -> redundancy
      Parity    : XOR checksum                   -> redundancy, cheaper than mirroring
   ```

   The main levels

   | Level | Technique | Min disks | Usable capacity | Survives | Purpose |
   |---|---|---|---|---|---|
   | RAID 0 | Striping | 2 | 100 % | `Nothing` | Pure speed and capacity |
   | RAID 1 | Mirroring | 2 | 50 % | 1 failure | Redundancy, simple |
   | RAID 5 | Striping + distributed parity | 3 | (n-1)/n | 1 failure | Balance of capacity and safety |
   | RAID 6 | Double parity | 4 | (n-2)/n | 2 failures | Large arrays |
   | RAID 10 | Mirroring + striping | 4 | 50 % | 1 per mirror | Speed with redundancy |

   Where it is used
   - Database servers, file servers, mail servers, virtualisation hosts, NAS and SAN systems, video editing workstations, and every data centre.

   - The essential caveat to state: `RAID is not a backup`. It protects only against `disk failure`. Accidental deletion, ransomware, file corruption, fire and theft are all written faithfully to every disk in the array at the same instant. A separate off-site backup is still required.

6. **What do you mean by RAID? Write the difference types of RAID level.** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 595 (ET: N/A)]*

   Answer: What RAID is
   - `RAID` stands for `Redundant Array of Independent Disks`. Several physical disks are combined into `one logical drive`, which the operating system sees as a single volume.
   - Purposes: `performance`, `fault tolerance` and larger `capacity`.
   - Three underlying techniques:
   ```
      Striping  : data split across disks, read and written in parallel -> speed
      Mirroring : the same data written to two disks -> redundancy
      Parity    : an XOR checksum that allows a lost block to be rebuilt
   ```

   RAID levels

   `RAID 0 — striping only`
   ```
      Disk 1   Disk 2
      ------   ------
        A1       A2
        A3       A4
   ```
   - Minimum 2 disks, `100 %` capacity usable, `no redundancy at all`.
   - Fastest reads and writes. One disk failure destroys everything.
   - Used for: scratch space, video editing, caches — data that can be lost.

   `RAID 1 — mirroring`
   ```
      Disk 1   Disk 2
      ------   ------
        A1       A1
        A2       A2
   ```
   - Minimum 2 disks, `50 %` usable, survives one failure.
   - Fast reads (either disk can serve), normal writes. Rebuild is a simple copy.
   - Used for: operating system drives, small critical volumes.

   `RAID 5 — striping with distributed parity`
   ```
      Disk 1   Disk 2   Disk 3   Disk 4
      ------   ------   ------   ------
        A1       A2       A3       Ap
        B1       B2       Bp       B4
        C1       Cp       C3       C4
   ```
   - Minimum 3 disks, `(n-1)/n` usable, survives one failure.
   - Excellent reads. Writes suffer a `four-operation penalty`: read old data, read old parity, write new data, write new parity.
   - Used for: file servers, web servers, archives.

   `RAID 6 — double distributed parity`
   - Minimum 4 disks, `(n-2)/n` usable, survives `two` failures.
   - Writes are slower still (six operations), but it is the safe choice for arrays of large drives, where a rebuild takes many hours and a second failure is a real risk.

   `RAID 10 (1 + 0) — mirrored pairs, then striped`
   ```
      Disk 1 -- mirror -- Disk 2      Disk 3 -- mirror -- Disk 4
           |                               |
           +---------- stripe -------------+
   ```
   - Minimum 4 disks, `50 %` usable, survives one failure per mirrored pair.
   - Fastest redundant option, with no parity computation and a fast rebuild.
   - Used for: databases, transaction processing, virtualisation.

   Obsolete levels
   ```
      RAID 2 : bit-level striping with Hamming code - never used commercially
      RAID 3 : byte-level striping, DEDICATED parity disk
      RAID 4 : block-level striping, DEDICATED parity disk
               (the single parity disk is a bottleneck, so RAID 5 replaced both)
   ```

   Comparison

   | Level | Min disks | Usable | Survives | Read | Write |
   |---|---|---|---|---|---|
   | 0 | 2 | 100 % | Nothing | Fastest | Fastest |
   | 1 | 2 | 50 % | 1 disk | Fast | Normal |
   | 5 | 3 | (n-1)/n | 1 disk | Fast | Slow |
   | 6 | 4 | (n-2)/n | 2 disks | Fast | Slower |
   | 10 | 4 | 50 % | 1 per pair | Very fast | Very fast |

   - Remember: `RAID is not a backup`. It survives disk failure only, not deletion, corruption, ransomware or fire.

7. **What is RAID technology? Why it's important Server in data center?** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 555 (ET: BIBM)]*

   Answer: What RAID technology is
   - `RAID` (Redundant Array of Independent Disks) combines several physical disks into `one logical drive`, using three techniques:
   ```
      Striping  : data split across disks and accessed in parallel -> speed
      Mirroring : the same data written to two disks -> redundancy
      Parity    : an XOR checksum from which a lost block is rebuilt
   ```
   - Common levels: `RAID 0` (striping, no redundancy), `RAID 1` (mirroring), `RAID 5` (striping with distributed parity), `RAID 6` (double parity), `RAID 10` (mirrored then striped).
   - It may be implemented in `hardware` (a dedicated controller card with its own processor and battery-backed cache) or in `software` (by the operating system, cheaper but using host CPU time).

   Why it is important for a server in a data centre

   1. `High availability` — this is the reason it exists
   - Disks are the most failure-prone component in a server, because they are mechanical. In a data centre with thousands of drives, several fail every week.
   - RAID lets the server keep running in `degraded` mode through a failure, so the service does not stop. With a `hot spare` the rebuild starts automatically and nobody has to be called out.

   2. `No downtime for replacement`
   - `Hot swapping` allows the failed drive to be pulled and replaced while the server is running. A data centre measures availability in "nines" — 99.999 per cent uptime allows only about five minutes of outage a year, which is impossible without redundancy at the disk level.

   3. `Performance under heavy load`
   - A data centre server handles thousands of concurrent requests. Striping spreads them across several spindles, and a mirrored pair can serve two different reads at once, so throughput scales with the number of disks.

   4. `Large logical volumes`
   - Databases, virtual machine images and video archives outgrow any single drive. RAID presents many drives as one volume.

   5. `Meeting SLA and regulatory requirements`
   - Banks and government systems are held to service-level agreements and to regulator rules — in Bangladesh, Bangladesh Bank's ICT Security Guideline. Redundant storage is a stated requirement, not an option.

   6. `Protecting the transaction log`
   - Every committed database transaction must reach stable storage. Losing the log disk means losing committed work, which breaks the `durability` guarantee of ACID.

   7. `Foundation for virtualisation and cloud`
   - One physical host runs dozens of virtual machines. A single disk failure without RAID would take all of them down at once.

   Which level a data centre uses
   ```
      Database and OLTP servers   -> RAID 10   (fast writes, fast rebuild)
      File and web servers        -> RAID 5    (capacity with safety)
      Large archives, big drives  -> RAID 6    (survives a second failure
                                                during a long rebuild)
      Boot volumes                -> RAID 1
      Scratch and cache           -> RAID 0    (data is disposable)
   ```

   Advantages summarised
   ```
      Fault tolerance, continuous operation, hot swapping
      Higher read and write throughput
      Larger single volumes
      Automatic recovery with a hot spare
      Lower cost than duplicating whole servers
   ```

   - The point that must accompany any RAID answer: `RAID is not a backup`. It protects against disk failure alone. Deletion, ransomware, corruption, fire and theft are written to every disk in the array simultaneously, so off-site backups remain essential.

8. **(a) Compare RAID 1 and RAID 5 levels. Which one you prefer? Why?** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 691 (ET: N/A)]*

   Answer: Comparison of RAID 1 and RAID 5

   `RAID 1 — mirroring`
   ```
      Disk 1   Disk 2
      ------   ------
        A        A
        B        B
        C        C
   ```
   - Every block is written identically to both disks. Minimum `2` disks.
   - Usable capacity is `50 per cent`. Survives one disk failure per mirror.
   - Rebuild is a straight copy from the surviving disk — fast and low risk.

   `RAID 5 — striping with distributed parity`
   ```
      Disk 1   Disk 2   Disk 3   Disk 4
      ------   ------   ------   ------
        A1       A2       A3       Ap
        B1       B2       Bp       B4
        C1       Cp       C3       C4
        Dp       D2       D3       D4
   ```
   - Data is striped and a parity block per stripe rotates across the disks. Minimum `3` disks.
   - Usable capacity is `(n-1)/n` — 75 per cent with 4 disks, 80 per cent with 5.
   - Parity is `Ap = A1 XOR A2 XOR A3`, and a lost block is recovered by XOR-ing the survivors.

   | Point | RAID 1 | RAID 5 |
   |---|---|---|
   | Technique | Mirroring | Striping + distributed parity |
   | Minimum disks | 2 | 3 |
   | Usable capacity | 50 % | (n-1)/n — 75 % or more |
   | Fault tolerance | 1 disk per mirror | 1 disk |
   | Read performance | Fast (both disks serve) | Fast (parallel stripes) |
   | Write performance | `Normal` — 2 operations | `Slow` — 4 operations |
   | Write penalty | 2x | 4x (read data, read parity, write both) |
   | Rebuild speed | Fast — a simple copy | Slow — read every disk, recompute |
   | Rebuild risk | Low | High — all disks stressed for hours |
   | CPU / controller load | Minimal | Parity calculation needed |
   | Cost per usable GB | High | Lower |
   | Expandable | Only in pairs | One disk at a time |
   | Best for | OS drives, transaction logs | File servers, archives, read-heavy work |

   Which is preferred, and why
   - For a `write-heavy` system — a database, a transaction log, a mail server — `RAID 1` (or better still RAID 10, which is RAID 1 striped) is preferred.
   ```
      Reason 1 : RAID 5's four-operation write penalty slows every single
                 write. A bank's core banking log cannot afford it.
      Reason 2 : RAID 5 rebuilds are slow and read every surviving disk in
                 full. With modern 4 TB or 8 TB drives that takes many hours,
                 and a second failure during the rebuild destroys the array.
      Reason 3 : RAID 5 has a "write hole" - a power failure between writing
                 the data and writing the parity leaves the stripe
                 inconsistent, unless the controller has a battery-backed cache.
   ```
   - For a `read-heavy` system where capacity per taka matters — a file server, a document archive, a media library — `RAID 5` is preferred, because it delivers 75-80 per cent usable capacity against RAID 1's 50 per cent, with equally good read performance.

   - Practical recommendation: use `RAID 1` for the operating system and the database log, and `RAID 5` (or RAID 6 on large drives) for bulk data. Where budget allows, `RAID 10` combines the strengths of both — mirroring's fast writes and fast rebuild with striping's throughput — and is the standard choice for production database servers.

9. **What is RAID?** *[BKSP Assistant Programmer 03.12.2022 compact it 730 (ET: N/A)]*

   Answer: `RAID` stands for `Redundant Array of Independent Disks` (originally "Inexpensive" Disks). It is a technique that combines several physical disks into `one logical drive`, which the operating system sees as a single volume.

   Purpose
   ```
      Performance     : several disks work in parallel
      Fault tolerance : the array survives a disk failure
      Capacity        : one logical volume larger than any single disk
   ```

   Three underlying techniques
   ```
      Striping  : data is split into blocks and spread across the disks,
                  so they are read and written at the same time -> SPEED

      Mirroring : the same data is written to two disks -> REDUNDANCY

      Parity    : an XOR checksum is stored, from which any single lost
                  block can be recomputed -> redundancy at lower cost
                  Ap = A1 XOR A2 XOR A3
   ```

   Main levels

   | Level | Technique | Min disks | Usable | Survives |
   |---|---|---|---|---|
   | RAID 0 | Striping | 2 | 100 % | Nothing |
   | RAID 1 | Mirroring | 2 | 50 % | 1 disk |
   | RAID 5 | Striping + distributed parity | 3 | (n-1)/n | 1 disk |
   | RAID 6 | Double parity | 4 | (n-2)/n | 2 disks |
   | RAID 10 | Mirroring + striping | 4 | 50 % | 1 per mirror |

   Implementation
   ```
      Hardware RAID : a dedicated controller card with its own processor and
                      battery-backed cache. Faster, and independent of the OS.
      Software RAID : implemented by the operating system (Linux mdadm,
                      Windows Storage Spaces). Cheaper, but uses host CPU.
   ```

   Where it is used
   - Database servers, file servers, virtualisation hosts, NAS and SAN systems, and every data centre.

   - The essential caveat: `RAID is not a backup`. It protects against `disk failure` only. Accidental deletion, ransomware, corruption, fire and theft are written faithfully to every disk in the array at once, so off-site backups are still required.

10. **What is RAID? What is the classification of RAIDs? Difference between RAID 1 and RAID 5 using illustration.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 755 (ET: N/A)]*

    Answer: What RAID is
    - `RAID` (Redundant Array of Independent Disks) combines several physical disks into one logical drive, to gain `performance`, `fault tolerance` and `capacity`.
    ```
       Striping  : data split across disks, accessed in parallel -> speed
       Mirroring : the same data on two disks -> redundancy
       Parity    : an XOR checksum from which a lost block is rebuilt
    ```

    Classification of RAID levels

    `Standard levels`
    ```
       RAID 0  : striping only, no redundancy
       RAID 1  : mirroring
       RAID 2  : bit-level striping with Hamming code   (obsolete)
       RAID 3  : byte-level striping, dedicated parity  (obsolete)
       RAID 4  : block-level striping, dedicated parity (obsolete)
       RAID 5  : block-level striping, distributed parity
       RAID 6  : block-level striping, double distributed parity
    ```
    `Nested (hybrid) levels`
    ```
       RAID 10 (1+0) : mirror first, then stripe   - the usual choice
       RAID 01 (0+1) : stripe first, then mirror   - less resilient
       RAID 50 (5+0) : RAID 5 sets, then striped
       RAID 60 (6+0) : RAID 6 sets, then striped
    ```
    `By implementation`
    ```
       Hardware RAID : a dedicated controller with its own CPU and cache
       Software RAID : implemented by the operating system
    ```

    Difference between RAID 1 and RAID 5, with illustration

    `RAID 1 — mirroring`
    ```
       Disk 1        Disk 2
       ------        ------
         A     ---->   A          every block written twice
         B     ---->   B
         C     ---->   C
         D     ---->   D

       2 disks of 500 GB  ->  500 GB usable  (50 %)
       Disk 2 fails : Disk 1 still holds everything.
       Rebuild : straight copy from Disk 1 to the replacement.
    ```

    `RAID 5 — striping with distributed parity`
    ```
       Disk 1   Disk 2   Disk 3   Disk 4
       ------   ------   ------   ------
         A1       A2       A3       Ap     <- parity of stripe A on disk 4
         B1       B2       Bp       B4     <- parity rotates
         C1       Cp       C3       C4
         Dp       D2       D3       D4

       Ap = A1 XOR A2 XOR A3

       4 disks of 500 GB  ->  1500 GB usable  (75 %)
       Disk 2 fails : A2 = A1 XOR A3 XOR Ap, recomputed on the fly.
       Rebuild : read EVERY surviving disk in full and recompute.
    ```

    | Point | RAID 1 | RAID 5 |
    |---|---|---|
    | Technique | Mirroring | Striping + distributed parity |
    | Minimum disks | 2 | 3 |
    | Usable capacity | 50 % | (n-1)/n, so 75 % with 4 disks |
    | Fault tolerance | 1 disk per mirror | 1 disk |
    | Read speed | Fast | Fast |
    | Write speed | Normal (2 operations) | Slow (4 operations) |
    | Rebuild | Fast, a simple copy | Slow, all disks read |
    | Rebuild risk | Low | High — hours of full load on every disk |
    | Controller load | Minimal | Parity calculation required |
    | Cost per usable GB | High | Lower |
    | Best for | OS drives, transaction logs, write-heavy work | File servers, archives, read-heavy work |

    - Practical choice: `RAID 1` (or RAID 10) where writes are frequent and rebuild speed matters; `RAID 5` where capacity per taka matters and the workload is mostly reads. On large modern drives many administrators now prefer `RAID 6` over RAID 5, because a rebuild lasts many hours and a second failure during it would be fatal.

11. **What is RAID technology? Describe about the advantages of RAID technology.** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 820 (ET: BUET)]*

    Answer: What RAID technology is
    - `RAID` (Redundant Array of Independent Disks) combines several physical disks into `one logical drive` seen by the operating system as a single volume.
    - It uses three techniques:
    ```
       Striping  : data split into blocks and spread across the disks,
                   so they are read and written in parallel  -> speed
       Mirroring : the same data written to two disks         -> redundancy
       Parity    : an XOR checksum from which a lost block is recomputed
    ```
    - Levels: `RAID 0` (striping), `RAID 1` (mirroring), `RAID 5` (striping with distributed parity), `RAID 6` (double parity), `RAID 10` (mirrored then striped).
    - Implemented either in `hardware`, on a dedicated controller card with its own processor and battery-backed cache, or in `software` by the operating system.

    Advantages of RAID technology

    1. `Fault tolerance` — the main advantage
    - The array survives a disk failure. RAID 1 and 10 keep a full second copy; RAID 5 recomputes the lost blocks from parity; RAID 6 survives two simultaneous failures.

    2. `High availability and continuous operation`
    - The system keeps running in `degraded` mode while the failed disk is replaced. With `hot swapping` the drive is changed without shutting down, and with a `hot spare` the rebuild starts automatically with no human action at all.

    3. `Improved read and write performance`
    - Striping lets several disks work in parallel, so throughput scales roughly with the number of drives. A mirrored pair can serve two different reads simultaneously.

    4. `Larger logical capacity`
    - Several drives become one volume, so a file system, a database or a virtual machine store can exceed the size of any single disk.

    5. `Reduced downtime cost`
    - For a bank, a hospital or an e-commerce site, an hour of downtime costs far more than the extra disks. RAID converts a service-stopping event into a maintenance task.

    6. `Data integrity`
    - Parity and mirroring let the controller detect, and in RAID 6 correct, silent corruption that would otherwise go unnoticed.

    7. `Scalability`
    - A RAID 5 array can be expanded one disk at a time; capacity grows without rebuilding the file system from scratch.

    8. `Flexibility of trade-off`
    - The administrator chooses the level to match the workload — speed, capacity or safety — rather than accepting a single fixed compromise.

    9. `Cost effective`
    - Several ordinary drives give the reliability that would otherwise require duplicating the entire server.

    10. `Transparent to software`
    - The operating system and applications see one ordinary volume; no program has to be modified.

    Disadvantages, for balance
    ```
       Extra disks cost money and capacity (50 % lost in RAID 1 and 10)
       RAID 5 and 6 impose a write penalty
       Rebuilds are slow and risky on large drives
       A hardware controller is itself a single point of failure
       Increased complexity in configuration and monitoring
    ```

    - The point that must accompany any RAID answer: `RAID is not a backup`. It protects only against `disk failure`. A deleted table, a ransomware attack, a corrupted file, a fire or a theft is written to every disk in the array at the same instant. Off-site backups remain essential.

12. **Why necessary to use RAID? If you choose a RAID level for an organization with huge data process. Justify your answer?** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 854 (ET: N/A)]*

    Answer: Why RAID is necessary
    - `Disks fail.` A hard disk is the only mechanical part left in a server, and it is by far the most failure-prone. In a large organisation several drives fail every month.
    - `Downtime is expensive.` For a bank, a hospital or an e-commerce site, an hour of outage costs far more than the extra disks would.
    - `A single disk is too slow.` One drive delivers 100-200 MB/s. A busy database or file server needs many times that, which only parallel disks can supply.
    - `A single disk is too small.` Databases, virtual machine images and video archives outgrow any one drive.
    - `Continuity is a legal requirement.` Bangladesh Bank's ICT Security Guideline, and the service-level agreements of government systems, require redundant storage.
    - `Durability of committed transactions.` The `D` in ACID promises that a committed transaction survives; RAID is part of how that is delivered at the hardware level.

    Choosing a level for an organisation with huge data processing

    For huge data volumes with heavy processing, the recommendation is `RAID 10` for the transactional workload and `RAID 6` for the bulk archive.

    `RAID 10 for the live database and transaction processing`
    ```
       Justification
       -------------
       1. Write performance. Huge data processing means constant writes.
          RAID 5 needs FOUR physical operations for one logical write
          (read old data, read old parity, write data, write parity).
          RAID 10 needs only two. Every transaction is faster.

       2. Fast rebuild. A replaced disk is copied from its mirror. There is
          no parity to recompute and only one other drive is stressed, so the
          window of vulnerability is short.

       3. No write hole. RAID 5 can leave a stripe inconsistent if power fails
          between the data write and the parity write. RAID 10 cannot.

       4. Predictable performance in degraded mode. A RAID 5 array with a
          failed disk must recompute every read from parity and slows
          dramatically; RAID 10 simply reads the surviving mirror.

       Cost : only 50 % of raw capacity is usable, and a minimum of 4 disks.
              For a large organisation this cost is small next to downtime.
    ```

    `RAID 6 for the archive, backup and data-warehouse volumes`
    ```
       Justification
       -------------
       1. Capacity. (n-2)/n usable - far better than RAID 10's 50 %,
          which matters when the volume is hundreds of terabytes.

       2. Survives TWO failures. With 8 TB or larger drives, a rebuild takes
          many hours or days. During that time a second failure is a real
          possibility, and RAID 5 would lose everything. RAID 6 survives it.

       3. The workload here is read-heavy and sequential, so the write
          penalty matters much less.
    ```

    `Never RAID 0` — it has no redundancy at all, and with many disks the chance that at least one fails becomes a near certainty.
    `Avoid plain RAID 5` on large modern drives, for the rebuild reason above.

    A practical layout for such an organisation
    ```
       Operating system volume  -> RAID 1     (2 disks)
       Database data files      -> RAID 10    (fast random read/write)
       Transaction log          -> RAID 1 or RAID 10, on SEPARATE spindles
                                   (sequential, latency-critical - never RAID 5)
       Data warehouse / reports -> RAID 5 or 6 (read-heavy, capacity matters)
       Backup and archive       -> RAID 6      (capacity and double safety)
       Plus at least one HOT SPARE per array
    ```

    Comparison of the candidates

    | Level | Usable | Survives | Write speed | Rebuild | Verdict for huge data |
    |---|---|---|---|---|---|
    | RAID 0 | 100 % | Nothing | Fastest | — | `Rejected` — no redundancy |
    | RAID 1 | 50 % | 1 disk | Normal | Fast | Good, but does not scale |
    | RAID 5 | (n-1)/n | 1 disk | Slow | Slow and risky | Acceptable for archives only |
    | RAID 6 | (n-2)/n | 2 disks | Slower | Slow but safe | `Chosen` for bulk storage |
    | RAID 10 | 50 % | 1 per pair | Very fast | Very fast | `Chosen` for the live database |

    - And the standing caveat: `RAID is not a backup`. It handles disk failure alone. Deletion, ransomware, corruption, fire and theft reach every disk at once, so off-site and immutable backups are still required.

13. **Your office need some storage device. Highest capacity 500GB. Two system backup of 30GB. Using RAID 1, Explain how many storage devices will need?** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1032 (ET: BUET)]*

    Answer: In `RAID 1` every block is written to two disks, so the `usable capacity is half` the raw capacity.
    ```
       Usable capacity = raw capacity / 2
       Raw capacity needed = usable capacity x 2
    ```

    Step 1 — total data to be stored
    ```
       Main storage requirement    = 500 GB
       Backup of system 1          =  30 GB
       Backup of system 2          =  30 GB
       -----------------------------------
       Total usable capacity needed = 560 GB
    ```

    Step 2 — raw capacity required for RAID 1
    ```
       Raw = 560 x 2 = 1120 GB
    ```

    Step 3 — number of 500 GB drives
    ```
       A single mirrored pair of 500 GB disks gives 500 GB usable
            -> not enough for 560 GB

       Two mirrored pairs (4 disks) give 1000 GB usable
            -> enough, with 440 GB to spare
    ```
    ```
       Answer : 4 storage devices of 500 GB each
                (two RAID 1 mirrored pairs, giving 1000 GB usable)
    ```

    Layout
    ```
       Set 1 (main data)      Set 2 (backups + spare capacity)
       Disk 1 --- mirror --- Disk 2       Disk 3 --- mirror --- Disk 4
         500 GB      500 GB                 500 GB      500 GB
         -> 500 GB usable                   -> 500 GB usable

       Total usable = 1000 GB  >=  560 GB required
    ```

    Alternative reading, if the two requirements are kept on separate arrays
    ```
       Main data 500 GB   -> one mirrored pair of 500 GB disks = 2 drives
       Backups    60 GB   -> one mirrored pair of small disks  = 2 drives
                                                         ------------------
                                                         Total   4 drives
    ```
    - Both readings give the same answer: `4 drives`.

    Cost of the alternatives, for comparison
    ```
       RAID 1  : 4 x 500 GB = 2000 GB raw -> 1000 GB usable (50 %)
       RAID 5  : 3 x 500 GB = 1500 GB raw -> 1000 GB usable (67 %)
                 cheaper, but slower writes and a risky rebuild
       RAID 10 : 4 x 500 GB = 2000 GB raw -> 1000 GB usable (50 %)
                 same cost as RAID 1 here, but faster
    ```

    Practical points to add
    - Buy `5` drives rather than 4, keeping one as a `hot spare` so that a rebuild begins automatically the moment a disk fails.
    - The drives should be of the same model and capacity, but ideally not all from the same production batch, since drives from one batch tend to fail at similar times.
    - And the standing caveat: `RAID 1 is not a backup`. It protects against disk failure only. The two system backups should also be copied to separate `off-site` media, because a fire, a theft or a ransomware attack would destroy both mirrored disks together.

14. **What is RAID level? Write down of RAID level 0, level 1 and level 5?** *[Dutch Bangla Bank Assistant Network/Hardware Engineer 2019 compact it 1159 (ET: BUET)]*

    Answer: What a RAID level is
    - A `RAID level` is a defined way of arranging data across the disks of an array. Each level is a different trade-off between `performance`, `capacity` and `fault tolerance`.
    - The three underlying techniques are `striping` (speed), `mirroring` (redundancy) and `parity` (redundancy at lower cost).

    RAID level 0 — striping
    ```
       Disk 1   Disk 2
       ------   ------
         A1       A2
         A3       A4
         A5       A6
    ```
    - Data is split into blocks and written alternately across the disks, so both work in parallel.
    - Minimum `2` disks. Usable capacity `100 per cent`.
    - `No redundancy whatsoever` — if one disk fails, the whole array is lost, because every file is split across all of them.
    - Fastest reads and writes of any level.
    - Used for: scratch space, video editing, caches — data that can be regenerated.
    ```
       Reliability is WORSE than a single disk: with 2 disks the chance of
       failure is roughly doubled, since either failure destroys everything.
    ```

    RAID level 1 — mirroring
    ```
       Disk 1        Disk 2
       ------        ------
         A     ---->   A
         B     ---->   B
         C     ---->   C
    ```
    - Every block is written identically to both disks.
    - Minimum `2` disks. Usable capacity `50 per cent`.
    - Survives `one` disk failure per mirrored pair.
    - Reads are fast, since either disk can serve a request. Writes are normal speed — two operations.
    - Rebuild is a straight copy from the survivor, so it is fast and low risk.
    - Used for: operating system drives, transaction logs, small critical volumes.

    RAID level 5 — striping with distributed parity
    ```
       Disk 1   Disk 2   Disk 3   Disk 4
       ------   ------   ------   ------
         A1       A2       A3       Ap     <- parity of stripe A
         B1       B2       Bp       B4     <- parity rotates to disk 3
         C1       Cp       C3       C4
         Dp       D2       D3       D4

       Ap = A1 XOR A2 XOR A3
    ```
    - Data is striped, and one parity block per stripe is stored, `distributed` across all the disks so that no single drive becomes a bottleneck.
    - Minimum `3` disks. Usable capacity `(n-1)/n` — 75 per cent with 4 disks.
    - Survives `one` disk failure. The missing block is recovered by XOR:
    ```
       A2 = A1 XOR A3 XOR Ap
    ```
    - Reads are fast. Writes suffer a `four-operation penalty`: read the old data, read the old parity, write the new data, write the new parity.
    - Rebuild is slow — every surviving disk must be read in full — and a second failure during it destroys the array.
    - Used for: file servers, web servers, archives.

    Comparison

    | Level | Technique | Min disks | Usable | Survives | Read | Write |
    |---|---|---|---|---|---|---|
    | RAID 0 | Striping | 2 | 100 % | `Nothing` | Fastest | Fastest |
    | RAID 1 | Mirroring | 2 | 50 % | 1 disk | Fast | Normal |
    | RAID 5 | Striping + distributed parity | 3 | (n-1)/n | 1 disk | Fast | Slow |

    - Related levels worth naming: `RAID 6` adds a second parity block and survives two failures; `RAID 10` mirrors first and then stripes, giving RAID 1's safety with RAID 0's speed, and is the usual choice for database servers.

15. **Describe RAID level.** *[Dutch Bangla Bank Ltd. Probationary Officer (Software) 2018 compact it 1199 (ET: N/A)]*

    Answer: A `RAID level` defines how data is arranged across the disks of an array. Each level is a different trade-off between `performance`, `capacity` and `fault tolerance`, built from three techniques: `striping`, `mirroring` and `parity`.

    RAID 0 — striping
    ```
       Disk 1   Disk 2
         A1       A2
         A3       A4
    ```
    - Minimum 2 disks, `100 %` usable, `no redundancy`.
    - Fastest reads and writes. One failure destroys the whole array.
    - Used for: scratch data, video editing, caches.

    RAID 1 — mirroring
    ```
       Disk 1        Disk 2
         A     ---->   A
         B     ---->   B
    ```
    - Minimum 2 disks, `50 %` usable, survives one failure per pair.
    - Fast reads, normal writes, fast and safe rebuild.
    - Used for: OS drives, transaction logs.

    RAID 2 — bit-level striping with Hamming code
    - Minimum 3 disks. Bits are striped and error-correcting Hamming codes are stored on dedicated disks.
    - `Obsolete` — modern drives already have internal ECC, so it is redundant.

    RAID 3 — byte-level striping with a dedicated parity disk
    ```
       Disk 1  Disk 2  Disk 3  Parity
         b1      b2      b3      P
    ```
    - Minimum 3 disks. Good for large sequential transfers, but every write touches the single parity disk, which becomes a bottleneck. `Rarely used`.

    RAID 4 — block-level striping with a dedicated parity disk
    - Like RAID 5 but the parity all sits on one disk, which is again a bottleneck. `Superseded by RAID 5`.

    RAID 5 — striping with distributed parity
    ```
       Disk 1   Disk 2   Disk 3   Disk 4
         A1       A2       A3       Ap
         B1       B2       Bp       B4
         C1       Cp       C3       C4

       Ap = A1 XOR A2 XOR A3
    ```
    - Minimum 3 disks, `(n-1)/n` usable, survives one failure.
    - Excellent reads; writes cost four operations. Rebuild is slow and stresses every disk.
    - Used for: file servers, archives, read-heavy work.

    RAID 6 — double distributed parity
    - Minimum 4 disks, `(n-2)/n` usable, survives `two` simultaneous failures.
    - Writes cost six operations, but it is the safe choice for arrays of large drives where a rebuild lasts many hours.

    RAID 10 (1 + 0) — mirror then stripe
    ```
       Disk 1 -- mirror -- Disk 2      Disk 3 -- mirror -- Disk 4
            |                               |
            +---------- stripe -------------+
    ```
    - Minimum 4 disks, `50 %` usable, survives one failure per mirrored pair.
    - Fastest redundant level, with no parity computation and a fast rebuild.
    - Used for: databases, transaction processing, virtualisation.

    Other nested levels
    ```
       RAID 01 (0+1) : stripe first, then mirror - less resilient than 10
       RAID 50, 60   : RAID 5 or 6 sets, then striped - very large arrays
    ```

    Summary

    | Level | Min disks | Usable | Survives | Read | Write | Typical use |
    |---|---|---|---|---|---|---|
    | 0 | 2 | 100 % | Nothing | Fastest | Fastest | Scratch, editing |
    | 1 | 2 | 50 % | 1 disk | Fast | Normal | OS, logs |
    | 5 | 3 | (n-1)/n | 1 disk | Fast | Slow | File servers |
    | 6 | 4 | (n-2)/n | 2 disks | Fast | Slower | Large archives |
    | 10 | 4 | 50 % | 1 per pair | Very fast | Very fast | Databases |

    - Remember the caveat: `RAID is not a backup`. It survives disk failure alone; deletion, corruption, ransomware and fire reach every disk at once.

## Cache Memory (14)

1. Explain the difference between a "Compulsory Miss" (Cold Miss) and a "Capacity Miss" in cache memory. [SO IT 25-07-2026]

   Answer: Cache misses are classified into three kinds, known as the `three C's`: compulsory, capacity and conflict.

   Compulsory miss (cold miss, first-reference miss)
   - Occurs when a block is accessed for the `very first time`. It cannot possibly be in the cache, because it has never been brought in.
   - It happens even in an `infinitely large` cache — no size or organisation can avoid it.
   - The number of compulsory misses equals the number of `distinct blocks` the program touches.
   ```
      for (i = 0; i < 1000; i++)
          sum += A[i];              // the FIRST access to each cache block
                                    // of A[] is a compulsory miss
   ```
   - Reduced by: `larger block size` (one miss brings in more useful data) and `prefetching` (fetch the block before it is asked for). It cannot be eliminated.

   Capacity miss
   - Occurs when the program's `working set is larger than the cache`. A block was in the cache, was evicted to make room for others, and is then needed again.
   - It would `not` happen in an infinitely large cache — that is exactly the test that distinguishes it from a compulsory miss.
   ```
      Cache = 1 MB , array = 10 MB , read the array twice :

      Pass 1 : compulsory misses for every block
      Pass 2 : the early blocks were evicted long ago -> CAPACITY misses
   ```
   - Reduced by: a `larger cache`, and by rewriting the program to improve locality — `loop blocking` (tiling) is the standard technique, which processes the data in chunks that fit the cache.

   Conflict miss, for completeness
   - Occurs in a direct-mapped or set-associative cache when several blocks map to the `same set` and evict one another, even though the cache as a whole is not full.
   - Eliminated by `full associativity` or reduced by raising the associativity.

   Difference

   | Point | Compulsory miss | Capacity miss |
   |---|---|---|
   | Cause | The block has never been accessed before | The cache is too small to hold the working set |
   | Happens in an infinite cache | `Yes` | `No` |
   | Depends on cache size | No | Yes |
   | Depends on associativity | No | No |
   | Number of them | One per distinct block touched | Depends on the working-set size |
   | Reduced by | Larger blocks, prefetching | Larger cache, better locality, loop blocking |
   | Can be eliminated | No | Yes, with a big enough cache |
   | Also called | Cold-start or first-reference miss | — |

   - The clean way to tell them apart in an exam: `simulate the program on an infinitely large fully associative cache`. Every miss that still occurs is compulsory. Then shrink the cache to its real size but keep full associativity — the extra misses are capacity misses. Finally apply the real associativity — the remaining extra misses are conflict misses.

2. **(d) What is cache memory? Explain the concepts of (i) Cache hit and (ii) Cache miss.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1352 (ET: N/A)]*

   Answer: What cache memory is
   - `Cache memory` is a small, very fast memory placed between the CPU and main memory. It holds copies of the instructions and data that have been used most recently, so the CPU usually finds what it needs without waiting for RAM.
   - It is built from `SRAM`, which is far faster than the DRAM used for main memory, and it is managed entirely by `hardware` — the programmer never addresses it directly.
   ```
      CPU  <->  L1 cache  <->  L2 cache  <->  L3 cache  <->  Main memory (DRAM)
      ~1cy       ~4cy          ~12cy          ~40cy           ~200cy
   ```
   - Why it works: the `principle of locality`.
   ```
      Temporal locality : a location just used is likely to be used again soon
      Spatial locality  : locations near one just used are likely to be needed
                          (so a whole BLOCK is fetched, not a single word)
   ```

   (i) Cache hit
   - A `cache hit` occurs when the data the CPU asks for is `found in the cache`. The request is served in a few cycles and main memory is never touched.
   ```
      Hit ratio = number of hits / total number of accesses
   ```
   - A well-designed cache achieves a hit ratio of `90 to 99 per cent`, which is why the arrangement works at all.

   (ii) Cache miss
   - A `cache miss` occurs when the requested data is `not in the cache`. The CPU must then wait while the whole block containing it is fetched from main memory and copied into the cache, after which the access is retried and hits.
   ```
      Miss penalty = the extra time cost of a miss
      Average access time = hit time + (miss rate x miss penalty)
   ```

   Worked example
   ```
      Hit time     = 5 ns
      Miss penalty = 100 ns
      Hit ratio    = 95 %

      Average access time = 5 + (0.05 x 100) = 5 + 5 = 10 ns

      Compared with 105 ns without a cache -> more than ten times faster.
   ```

   Types of miss — the three C's
   ```
      Compulsory : the block is being accessed for the first time
      Capacity   : the working set is larger than the cache
      Conflict   : several blocks map to the same set and evict each other
   ```

   What happens on a miss
   ```
      1. The block containing the requested word is fetched from main memory.
      2. If the cache set is full, a block is EVICTED using a replacement
         policy - LRU, FIFO or random.
      3. If the evicted block was modified, it must be written back
         (write-back policy) or it was already written (write-through).
      4. The new block is stored and the access is retried, this time hitting.
   ```

   - Point worth stating: the whole memory hierarchy rests on the hit ratio. A drop from 95 per cent to 90 per cent doubles the miss cost and roughly halves the benefit of the cache, which is why cache design receives so much attention in processor architecture.

3. **Write advantage and disadvantage of direct mapping and associative mapping between cache memory and main memory.** *[BCIC Assistant Programmer 14.02.2025 compact it 1330 (ET: BUET)]*

   Answer: The `mapping function` decides where a block of main memory may be placed in the cache. The three schemes are direct, associative and set-associative.

   Direct mapping
   - Each main-memory block can go in `exactly one` cache line, determined by
   ```
      cache line = (block number) MOD (number of lines)
   ```
   - The address is split as:
   ```
      +------------+---------+--------+
      |    TAG     |  INDEX  | OFFSET |
      +------------+---------+--------+
      The INDEX picks the line; the TAG confirms which block is in it.
   ```

   Advantages
   - `Simplest and cheapest` hardware — only one comparator is needed, so the chip area and cost are minimal.
   - `Fastest lookup`, because the line is found by simple indexing with no search at all. Ideal for L1 cache, where every cycle counts.
   - `No replacement policy needed` — there is only one possible place, so nothing has to be decided or tracked.
   - Low power consumption.

   Disadvantages
   - `Conflict misses.` Two frequently used blocks that map to the same line evict each other repeatedly, even when the rest of the cache is empty. This is called `thrashing`.
   - `Poor utilisation` — the cache can perform badly while most of it sits unused.
   - Performance is `unpredictable`; it depends heavily on the addresses a particular program happens to use.

   Associative mapping (fully associative)
   - A block may be placed in `any` cache line. The address is split as:
   ```
      +----------------------+--------+
      |         TAG          | OFFSET |
      +----------------------+--------+
      The tag must be compared against EVERY line, in parallel.
   ```

   Advantages
   - `No conflict misses at all.` A block is evicted only when the cache is genuinely full, so the only misses are compulsory and capacity misses.
   - `Best possible hit ratio` for a given cache size.
   - `Full utilisation` of every line.
   - `Flexible` — the replacement policy (LRU, FIFO, random) can be chosen to suit the workload.

   Disadvantages
   - `Expensive hardware.` One comparator per line is required, all operating simultaneously. For 1024 lines that is 1024 comparators.
   - `Slower` lookup, because of the wide parallel comparison, and `higher power` consumption.
   - `Replacement policy needed`, which costs extra logic and per-line state (LRU counters).
   - `Larger tag field`, since no bits are used as an index, so more storage is spent on tags.
   - Practical only for very small caches — the TLB is the classic example.

   Comparison

   | Point | Direct mapping | Associative mapping |
   |---|---|---|
   | Placement | One fixed line | Any line |
   | Comparators needed | 1 | One per line |
   | Hardware cost | Lowest | Highest |
   | Lookup speed | Fastest | Slowest |
   | Conflict misses | Many | `None` |
   | Hit ratio | Lower | Highest |
   | Replacement policy | Not needed | Required (LRU, FIFO) |
   | Tag size | Smaller | Larger |
   | Power | Low | High |
   | Cache utilisation | Poor | Full |
   | Used in | Large L2/L3 caches | Very small caches, TLB |

   - The practical compromise is `set-associative mapping`, used in almost every real processor. The cache is divided into sets of `k` lines; the index selects the set, and the block may go anywhere within it. `k = 4` or `8` captures nearly all the hit-ratio benefit of full associativity at a small fraction of the hardware cost.

4. **How many total bits are required for a direct mapped cache with 16KB of data and 4-word blocks? Assuming a 32 bit address?** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 421 (ET: BIBM)]*

   Answer: Given
   ```
      Cache data size = 16 KB
      Block size      = 4 words
      Word size       = 4 bytes (32-bit architecture)
      Address         = 32 bits
      Mapping         = direct mapped
   ```

   Step 1 — block size in bytes
   ```
      1 block = 4 words x 4 bytes = 16 bytes = 2^4 bytes
   ```

   Step 2 — number of blocks (cache lines)
   ```
      Number of blocks = cache data size / block size
                       = 16 KB / 16 bytes
                       = 16384 / 16
                       = 1024 blocks = 2^10
   ```

   Step 3 — split the 32-bit address
   ```
      Byte offset within a word : 2 bits   (4 bytes  = 2^2)
      Word offset within a block: 2 bits   (4 words  = 2^2)
      ------------------------------------------------------
      Block offset total        : 4 bits

      Index (which of 1024 lines): 10 bits (2^10 = 1024)

      Tag = 32 - 10 - 4 = 18 bits
   ```
   ```
      +-------------+----------+------------+-----------+
      |  TAG 18 bit | INDEX 10 | WORD off 2 | BYTE off 2|
      +-------------+----------+------------+-----------+
           31-14        13-4        3-2          1-0
   ```

   Step 4 — bits stored in each cache line
   ```
      Data      : 4 words x 32 bits = 128 bits
      Tag       :                      18 bits
      Valid bit :                       1 bit
      ---------------------------------------------
      Per line  :                     147 bits
   ```

   Step 5 — total bits in the cache
   ```
      Total = number of lines x bits per line
            = 1024 x 147
            = 150,528 bits
   ```

   Answer
   ```
      Total bits required = 150,528 bits
                          = 147 Kibits  (147 x 1024)
                          = 18,816 bytes
                          = 18.375 KB
   ```

   Verification of the overhead
   ```
      Useful data  = 1024 x 128 = 131,072 bits = 16 KB       (as required)
      Overhead     = 1024 x  19 =  19,456 bits =  2.375 KB   (tag + valid)

      Overhead ratio = 19 / 147 = 12.9 %
   ```
   - So a "16 KB cache" actually occupies about 18.4 KB of silicon. The extra is the tag and valid bits, which are never counted in the advertised size.

   - Points worth noting: a `larger block size` reduces the number of lines and therefore the tag overhead, but it also increases the miss penalty and can waste bandwidth on data that is never used. If the cache were `set associative`, the index would be narrower (it selects a set rather than a line) and the tag correspondingly wider.

5. **6.3 Explain the difference between a "Compulsory Miss" (Cold Miss) and a "Capacity Miss" in cache memory.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

   Answer: Cache misses are classified into the `three C's`: compulsory, capacity and conflict. The first two are asked here.

   Compulsory miss (cold miss, first-reference miss)
   - Occurs when a block is accessed for the `very first time`. It cannot be in the cache, because it has never been brought in.
   - It happens even in an `infinitely large` cache — no size or organisation can prevent it.
   - The count equals the number of `distinct blocks` the program touches.
   ```
      for (i = 0; i < 1000; i++)
          sum += A[i];         // the FIRST access to each block of A[]
                               // is a compulsory miss
   ```
   - Reduced by `larger block size`, since one miss then brings in more useful neighbouring data, and by `prefetching`, which fetches a block before it is requested. It can never be eliminated.

   Capacity miss
   - Occurs when the program's `working set is larger than the cache`. A block was present, was evicted to make room for others, and is then needed again.
   - It would `not` occur in an infinitely large cache — that is the test that separates it from a compulsory miss.
   ```
      Cache = 1 MB , array = 10 MB , the array is read twice :

      Pass 1 : every block is a compulsory miss
      Pass 2 : the early blocks were evicted long ago -> CAPACITY misses
   ```
   - Reduced by a `larger cache`, and by improving the program's locality. The standard technique is `loop blocking` (tiling), which processes the data in chunks small enough to fit the cache.

   Conflict miss, for completeness
   - Occurs in a direct-mapped or set-associative cache when several blocks map to the `same set` and evict one another, even though the cache as a whole is not full. Eliminated by full associativity.

   Difference

   | Point | Compulsory miss | Capacity miss |
   |---|---|---|
   | Cause | First-ever access to the block | Working set exceeds the cache size |
   | Occurs in an infinite cache | `Yes` | `No` |
   | Depends on cache size | No | Yes |
   | Depends on associativity | No | No |
   | Count | One per distinct block touched | Depends on working-set size |
   | Reduced by | Larger blocks, prefetching | Larger cache, better locality, loop blocking |
   | Can be eliminated | Never | Yes, with a large enough cache |

   - How to separate them experimentally: simulate the program on an `infinite fully associative` cache — every miss that still occurs is compulsory. Then shrink it to the real size, still fully associative — the extra misses are capacity misses. Finally apply the real associativity — the remaining extra misses are conflict misses.

6. **Write Concept of cache memory in computer. How its change performance of computer?** *[BITAC Assistant Programmer 27.10.2023 compact it 559 (ET: BUTEX)]*

   Answer: Concept of cache memory
   - `Cache memory` is a small, very fast memory placed between the CPU and main memory, holding copies of the instructions and data that have been used most recently.
   - It exists because there is a huge `speed gap`: a CPU cycle is under a nanosecond, while a DRAM access takes 50-100 ns. Without a cache the processor would spend most of its life waiting.
   - It is built from `SRAM` and managed entirely by `hardware`; the programmer never addresses it directly.

   The hierarchy
   ```
      CPU  <->  L1  <->  L2  <->  L3  <->  Main memory (DRAM)
      ~1cy     ~4cy    ~12cy    ~40cy       ~200cy

      L1 : 32-64 KB, split into instruction and data caches, private per core
      L2 : 256 KB - 1 MB, private per core
      L3 : 8-32 MB, shared by all cores
   ```

   Why it works — the principle of locality
   ```
      Temporal locality : a location just used is likely to be used again soon
                          (loop variables, counters, frequently called functions)

      Spatial locality  : locations near one just used are likely to be needed
                          (arrays, sequential instructions)
                          -> so a whole BLOCK is fetched, not one word
   ```
   - Because of locality, a small cache captures a very large share of all accesses. Real hit ratios are `90 to 99 per cent`.

   How it changes performance
   ```
      Average access time = hit time + (miss rate x miss penalty)
   ```
   Worked example
   ```
      Hit time     =   5 ns
      Miss penalty = 100 ns
      Hit ratio    =  95 %

      With cache    : 5 + (0.05 x 100) = 10 ns
      Without cache :                    105 ns

      -> more than 10 times faster
   ```
   - The improvement is dramatic because the hit ratio is so high. Note how sensitive it is:
   ```
      Hit ratio 99 % : 5 + 1  =  6 ns
      Hit ratio 95 % : 5 + 5  = 10 ns
      Hit ratio 90 % : 5 + 10 = 15 ns
   ```
   - A five-point drop in hit ratio costs more than doubling the cache's own speed would gain, which is why cache design concentrates on the hit ratio.

   Other ways it improves performance
   - `Reduces bus traffic`, freeing the memory bus for DMA and for other cores.
   - `Keeps the pipeline full` — a stalled instruction fetch empties the pipeline and wastes many cycles.
   - `Lowers power consumption`, since an SRAM access on the die costs far less energy than driving the external memory bus.
   - `Helps multicore systems`, because each core's private L1 and L2 absorb most of its traffic instead of contending for shared memory.

   What limits the benefit
   ```
      Cache size        : too small and capacity misses dominate
      Block size        : too small loses spatial locality, too large wastes
                          bandwidth and raises the miss penalty
      Associativity     : direct mapped is fast but suffers conflict misses
      Replacement policy: LRU is best in practice but costs hardware
      Write policy      : write-through is simple, write-back is faster
      Program behaviour : code with poor locality defeats any cache
   ```

   - Summary: cache memory does not make the CPU or the RAM faster. It makes the `average` memory access fast, by ensuring that the slow level is reached only a few times in a hundred.

7. **Suppose we have a 16 KB of data in a direct mapped cache with 4 word blocks. Determine the size of the tag, index and offset fields if we are using a 32-bit architecture.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 439 (ET: BIBM)]*

   Answer: Given
   ```
      Cache data size = 16 KB
      Block size      = 4 words
      Word size       = 4 bytes (32-bit architecture)
      Address         = 32 bits
      Mapping         = direct mapped
   ```

   Step 1 — block size in bytes
   ```
      1 block = 4 words x 4 bytes = 16 bytes = 2^4 bytes
   ```

   Step 2 — number of cache lines
   ```
      Number of lines = 16 KB / 16 bytes
                      = 16384 / 16
                      = 1024 = 2^10
   ```

   Step 3 — offset field
   ```
      The offset selects a byte inside the block.

      Block = 16 bytes = 2^4   ->   OFFSET = 4 bits

      Split further, as textbooks often do :
         byte offset within a word  = 2 bits   (4 bytes  = 2^2)
         word offset within a block = 2 bits   (4 words  = 2^2)
   ```

   Step 4 — index field
   ```
      The index selects one of the 1024 lines.

      1024 = 2^10   ->   INDEX = 10 bits
   ```

   Step 5 — tag field
   ```
      TAG = total address bits - index - offset
          = 32 - 10 - 4
          = 18 bits
   ```

   Answer
   ```
      TAG    = 18 bits
      INDEX  = 10 bits
      OFFSET =  4 bits   (2 bits word offset + 2 bits byte offset)
      ---------------------------------------------------------
      Total  = 32 bits        matches the address width
   ```

   Address layout
   ```
      +----------------+-----------+----------+----------+
      |   TAG 18 bits  | INDEX 10  | WORD 2   | BYTE 2   |
      +----------------+-----------+----------+----------+
         bits 31-14      bits 13-4   bits 3-2   bits 1-0
   ```

   How an access is resolved
   ```
      1. The INDEX (10 bits) selects one cache line directly - no searching.
      2. The stored TAG of that line is compared with the TAG of the address.
      3. If they match AND the valid bit is 1  ->  HIT.
         Otherwise                             ->  MISS: fetch the block from
                                                    main memory.
      4. The OFFSET selects the required word and byte inside the block.
   ```

   Bits actually stored, as a check
   ```
      Per line : data 128 + tag 18 + valid 1 = 147 bits
      Total    : 1024 x 147 = 150,528 bits = 18.375 KB
   ```

   - Points worth noting: only `one comparator` is needed in a direct-mapped cache, which is why it is the fastest and cheapest arrangement. If the cache were `4-way set associative`, the number of sets would be 1024/4 = 256, so the index would shrink to `8 bits` and the tag would grow to `20 bits`.

8. **What is the use of cache memory?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*

   Answer: `Cache memory` is a small, very fast memory between the CPU and main memory, holding copies of the instructions and data most recently used.

   Uses of cache memory

   1. `Bridging the speed gap` — the main purpose
   - A CPU cycle is under a nanosecond; a DRAM access takes 50-100 ns. The cache supplies most requests in a few cycles, so the processor is not left idle.
   ```
      Average access time = hit time + (miss rate x miss penalty)

      Hit time 5 ns, miss penalty 100 ns, hit ratio 95 % :
         5 + (0.05 x 100) = 10 ns , against 105 ns with no cache
   ```

   2. `Storing frequently used instructions and data`
   - The `principle of locality` means a program reuses the same small set of instructions and data repeatedly (temporal locality) and reads neighbouring addresses (spatial locality). A small cache therefore captures 90-99 per cent of all accesses.

   3. `Keeping the pipeline full`
   - A stalled instruction fetch empties the pipeline and wastes many cycles. The `instruction cache` keeps the fetch stage supplied.

   4. `Reducing memory bus traffic`
   - Requests served from the cache never reach the bus, leaving it free for DMA transfers and for the other cores. This matters more as core counts rise.

   5. `Lowering power consumption`
   - An SRAM access on the die uses far less energy than driving the external memory bus and activating a DRAM row.

   6. `Supporting multicore operation`
   - Each core has its own L1 and L2 to absorb its own traffic, and shares an L3, so the cores do not constantly contend for main memory.

   7. `Other caches in the system`, built on the same idea
   ```
      TLB          : caches virtual-to-physical address translations
      Disk cache   : caches recently read disk blocks in RAM
      Browser cache: caches web pages and images locally
      DNS cache    : caches name-to-IP lookups
   ```

   Levels
   ```
      L1 : 32-64 KB, ~4 cycles, split into instruction and data, private per core
      L2 : 256 KB - 1 MB, ~12 cycles, private per core
      L3 : 8-32 MB, ~40 cycles, shared by all cores
   ```

   - The essential point: cache memory does not make the CPU or the RAM faster. It makes the `average` access fast, by ensuring that the slow level is reached only a few times in every hundred requests.

9. **Some of the factors determine the performance of a computer system. Cache memory is one of them. Why cache memory is one of the factors to determine the performance of a computer system?** *[BTRC Assistant Director (Technical) 2021 compact it 807 (ET: IBA)]*

   Answer: Cache memory determines a large part of a computer's performance because the CPU spends most of its time `waiting for memory`, and the cache is what stops that wait.

   1. The memory wall — the reason the cache matters at all
   ```
      CPU cycle       :  ~0.3 ns   (3 GHz)
      L1 cache access :  ~1-2 ns
      Main memory     :  ~50-100 ns
   ```
   - A DRAM access costs roughly `200 CPU cycles`. Without a cache, a 3 GHz processor would run at the speed of its memory, wasting almost all of its capability. This gap is called the `memory wall`, and it has widened every year because CPU speed improved far faster than DRAM latency.

   2. Its effect is measured directly
   ```
      Average memory access time = hit time + (miss rate x miss penalty)
   ```
   ```
      Hit time 5 ns , miss penalty 100 ns

      Hit ratio 99 % : 5 + 1  =  6 ns
      Hit ratio 95 % : 5 + 5  = 10 ns
      Hit ratio 90 % : 5 + 10 = 15 ns
      No cache       :          105 ns
   ```
   - A five-point change in hit ratio changes performance by more than 50 per cent. No other single parameter has that leverage.

   3. It keeps the pipeline full
   - A modern CPU executes several instructions per cycle only while the pipeline is fed. A cache miss on an instruction fetch stalls the whole pipeline for hundreds of cycles, and out-of-order execution can hide only a fraction of that.

   4. It is why the CPI formula includes memory
   ```
      CPU time = Instructions x CPI x Clock cycle time

      Effective CPI = base CPI + (memory accesses per instruction
                                  x miss rate x miss penalty in cycles)
   ```
   - A base CPI of 1.0 becomes 3.0 if 30 per cent of instructions touch memory with a 5 per cent miss rate and a 130-cycle penalty. The processor's real speed has fallen to a third.

   5. It frees the memory bus
   - Hits never reach the bus. In a multicore system, where all cores share one memory controller, this is what prevents them from starving each other.

   6. It saves power
   - Driving the external bus and activating a DRAM row costs far more energy than an on-die SRAM read, so the cache improves performance per watt as well as raw speed.

   7. Its design parameters are all performance decisions
   ```
      Size          : bigger reduces capacity misses, but is slower and costlier
      Block size    : bigger exploits spatial locality, but raises the
                      miss penalty and can waste bandwidth
      Associativity : higher reduces conflict misses, but is slower per access
      Replacement   : LRU gives the best hit ratio; random is cheapest
      Write policy  : write-back reduces bus traffic; write-through is simpler
      Levels        : L1 for speed, L2 and L3 for capacity
   ```

   8. Practical evidence
   - Two processors with identical clock speed and core count can differ by 20-30 per cent in real work purely because of cache size and organisation. Server processors are sold largely on the size of their L3.
   - Programs written with `cache-aware` algorithms — loop blocking, row-major traversal, data structure padding — often run several times faster than the same algorithm written without regard to locality.

   - Summary: the cache does not make the CPU or the RAM faster. It decides how often the CPU has to touch the slow level at all, and since that gap is a factor of 200, the hit ratio effectively `sets` the machine's real speed.

10. **Assume that for a certain processor, a read request takes 50 nanoseconds on a cache miss and 5 nanoseconds on a cache hit. Suppose while running a program, it was observed that 80% of the processor's read requests result in a cache hit. The average read access time in nanoseconds is ______.** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 864 (ET: BUET)]*

    Answer: The average access time is the weighted mean of the hit time and the miss time.
    ```
       Average access time = (hit ratio x hit time) + (miss ratio x miss time)
    ```

    Given
    ```
       Time on a cache HIT   =  5 ns
       Time on a cache MISS  = 50 ns
       Hit ratio             = 80 % = 0.8
       Miss ratio            = 1 - 0.8 = 0.2
    ```

    Calculation
    ```
       Average = (0.8 x 5) + (0.2 x 50)

               = 4.0 + 10.0

       Average = 14 nanoseconds
    ```
    ```
       Answer : 14 ns
    ```

    Check by reasoning over 100 requests
    ```
       80 hits   x  5 ns =   400 ns
       20 misses x 50 ns = 1,000 ns
       -------------------------------
       Total for 100     = 1,400 ns

       Average = 1400 / 100 = 14 ns        correct
    ```

    Point to note about the wording
    - The question says a read `takes 50 ns on a miss`, so 50 ns is the `total` time for a miss, not an extra penalty added to the hit time. That is why the formula uses 50 directly.
    - If instead the problem said the miss `penalty` was 50 ns on top of the hit time, the working would be:
    ```
       Average = hit time + (miss rate x miss penalty)
               = 5 + (0.2 x 50) = 5 + 10 = 15 ns
    ```
    - Read the wording carefully; this single distinction is the usual reason for a wrong answer in such questions.

    How sensitive the result is to the hit ratio
    ```
       Hit ratio 80 % : (0.8 x 5) + (0.2 x 50) = 14 ns
       Hit ratio 90 % : (0.9 x 5) + (0.1 x 50) =  9.5 ns
       Hit ratio 95 % : (0.95 x 5) + (0.05 x 50) = 7.25 ns
       Hit ratio 99 % : (0.99 x 5) + (0.01 x 50) = 5.45 ns
    ```
    - An 80 per cent hit ratio is poor by modern standards; real caches reach 95-99 per cent, which is why the arrangement is so effective in practice.

11. **Cache memory কী কাজে ব্যবহৃত হয়? Compiler and Interpreater -এর মধ্যে পার্থক্য লিখুন।** *[41th BCS 2021 compact it 880-881 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Uses of cache memory
    - `Cache memory` is a small, very fast SRAM between the CPU and main memory, holding the instructions and data most recently used.
    - Its purpose is to `bridge the speed gap`: a CPU cycle is under a nanosecond, while a DRAM access takes 50-100 ns — about 200 cycles.
    ```
       Average access time = hit time + (miss rate x miss penalty)

       Hit time 5 ns, miss penalty 100 ns, hit ratio 95 % :
          5 + (0.05 x 100) = 10 ns , against 105 ns with no cache
    ```
    - It works because of the `principle of locality`: a program reuses the same instructions and data (temporal locality) and reads neighbouring addresses (spatial locality), so a small cache captures 90-99 per cent of all accesses.
    - Other uses: keeping the instruction pipeline full, reducing memory bus traffic so other cores and DMA can use it, and lowering power consumption.
    ```
       L1 : 32-64 KB, ~4 cycles, private per core
       L2 : 256 KB - 1 MB, ~12 cycles, private per core
       L3 : 8-32 MB, ~40 cycles, shared
    ```

    Compiler versus interpreter

    Both translate a high-level program into machine-executable form. The difference is `when` and `how much` they translate.

    `Compiler`
    - Translates the `entire` source program into machine code `once`, producing an executable file. The program then runs directly on the CPU with no translator present.
    - Errors are reported for the whole program at the end of compilation.
    - Examples: C, C++, Go, Rust.

    `Interpreter`
    - Translates and executes the program `line by line, at run time`. No separate executable is produced, and the interpreter must be present every time the program runs.
    - Execution stops at the first error, so a bug is reported immediately with its line number.
    - Examples: Python, Ruby, PHP, JavaScript, shell scripts.

    | Point | Compiler | Interpreter |
    |---|---|---|
    | Translation | Whole program at once | One statement at a time |
    | Output | A separate executable file | None — executes directly |
    | Execution speed | `Fast` — already machine code | `Slow` — translated every run |
    | Translation time | Slow, done once | Fast per line, repeated every run |
    | Memory use | Object code needs space | Lower, no object file |
    | Error reporting | All errors listed after compilation | Stops at the first error |
    | Debugging | Harder — errors reported together | `Easier` — immediate, line by line |
    | Translator needed at run time | No | `Yes` |
    | Portability of the output | Machine-specific binary | Source runs anywhere with the interpreter |
    | Source code needed by the user | No | Yes |
    | Examples | C, C++, Go, Rust | Python, PHP, Ruby, JavaScript |

    - Many modern languages use `both`. Java compiles to `bytecode`, which the JVM then interprets, and a `JIT (Just-In-Time)` compiler translates the hot parts to native machine code while the program runs — combining the interpreter's portability with the compiler's speed. Python does the same, compiling to `.pyc` bytecode before interpreting it.

12. **(ii) Cache Memory কী? Computer এর main memory-এর সাথে এর পার্থক্য কী?** *[BPSC Assistant Network Engineer 2020 compact it 951-952 (ET: N/A)], [BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What cache memory is
    - `Cache memory` is a small, very fast memory placed between the CPU and main memory, holding copies of the instructions and data that have been used most recently.
    - It exists because a CPU cycle is under a nanosecond while a DRAM access takes 50-100 ns — a gap of about 200 cycles. The cache stops the processor from waiting.
    - It is built from `SRAM` and managed entirely by `hardware`; the programmer never addresses it directly.
    ```
       CPU  <->  L1  <->  L2  <->  L3  <->  Main memory (DRAM)
       ~1cy     ~4cy    ~12cy    ~40cy       ~200cy
    ```
    - It works because of the `principle of locality`: a program keeps reusing the same instructions and data (temporal locality) and reads neighbouring addresses (spatial locality). Real hit ratios are 90-99 per cent.
    ```
       Average access time = hit time + (miss rate x miss penalty)
    ```

    Difference from main memory

    | Point | Cache memory | Main memory (RAM) |
    |---|---|---|
    | Technology | SRAM — 6-transistor flip-flop cell | DRAM — 1 transistor + 1 capacitor |
    | Refresh needed | No | Yes, every few milliseconds |
    | Access time | 1-15 ns (4-40 cycles) | 50-100 ns (~200 cycles) |
    | Capacity | KB to MB (32 KB to 32 MB) | GB (4 to 64 GB) |
    | Cost per byte | Very high | Moderate |
    | Location | On or beside the CPU die | On the motherboard in DIMM slots |
    | Managed by | Hardware, automatically | The operating system |
    | Addressed by the programmer | No | Yes |
    | Holds | Recently used blocks | All running programs and their data |
    | Levels | L1, L2, L3 | Single level |
    | Volatile | Yes | Yes |
    | Power per byte | Higher | Lower |

    How they work together
    ```
       1. The CPU requests an address.
       2. The cache is checked first.
            HIT  -> the data is returned in a few cycles.
            MISS -> the whole BLOCK containing it is fetched from main memory,
                    stored in the cache, and the access is retried.
       3. Because of locality, the next several requests are usually hits.
    ```

    Worked example
    ```
       Hit time 5 ns , miss penalty 100 ns , hit ratio 95 %

       With cache    : 5 + (0.05 x 100) = 10 ns
       Without cache :                    105 ns     -> 10 times faster
    ```

    - The essential point: cache and main memory are not alternatives but `two levels of one hierarchy`. Cache supplies speed, main memory supplies capacity, and the hierarchy works because locality lets a small fast level answer almost every request.

13. **If main memory access time is 100ns, cache access time is 50 ns, cache hit rate is 90% then what is the average time to read from memory?** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1228 (ET: N/A)]*

    Answer: The average access time is the weighted mean of the time taken on a hit and on a miss.

    Given
    ```
       Cache access time (hit)  Tc = 50 ns
       Main memory access time  Tm = 100 ns
       Hit ratio                h  = 90 % = 0.9
       Miss ratio               1-h = 0.1
    ```

    Method 1 — simultaneous (parallel) access, the standard textbook model
    ```
       Average access time = (h x Tc) + (1 - h) x Tm

                           = (0.9 x 50) + (0.1 x 100)

                           = 45 + 10

                           = 55 ns
    ```
    ```
       Answer : 55 nanoseconds
    ```
    - This assumes that on a miss the data is fetched from main memory in 100 ns, and that the failed cache lookup does not add to it, because the two are searched at the same time.

    Method 2 — hierarchical (sequential) access
    ```
       On a miss the CPU first looks in the cache (50 ns), fails, and then
       goes to main memory (100 ns), so a miss costs 50 + 100 = 150 ns.

       Average = (0.9 x 50) + (0.1 x 150)
               = 45 + 15
               = 60 ns
    ```
    ```
       Answer under this model : 60 nanoseconds
    ```

    - `Both answers are accepted`, provided the model is stated. Unless the question says the cache is searched first, the usual expected answer is `55 ns`.

    Check by reasoning over 100 accesses (Method 1)
    ```
       90 hits   x  50 ns = 4,500 ns
       10 misses x 100 ns = 1,000 ns
       ---------------------------------
       Total for 100      = 5,500 ns

       Average = 5500 / 100 = 55 ns        correct
    ```

    Improvement over having no cache
    ```
       Without a cache : every access costs 100 ns
       With the cache  : 55 ns

       Speed-up = 100 / 55 = 1.82 times faster
    ```
    - The gain here is modest because the cache is only twice as fast as main memory. In a real processor the cache is roughly `20 times` faster, which is where the large speed-up comes from.

    Sensitivity to the hit ratio
    ```
       h = 0.80 : (0.8 x 50) + (0.2 x 100) = 60 ns
       h = 0.90 : (0.9 x 50) + (0.1 x 100) = 55 ns
       h = 0.95 : (0.95 x 50) + (0.05 x 100) = 52.5 ns
       h = 0.99 : (0.99 x 50) + (0.01 x 100) = 50.5 ns
    ```
    - As the hit ratio approaches 1, the average approaches the cache's own access time. That is the whole aim of cache design.

14. **Explain how cache memory is used to increase the processing speed of computer.** *[Multiple Ministry Assistant Programmer 2017 compact it 1230-1231 (ET: N/A)]*

    Answer: The cache increases processing speed by making sure the CPU almost never has to wait for main memory.

    The problem it solves — the memory wall
    ```
       CPU cycle       : ~0.3 ns   (3 GHz)
       Main memory     : ~50-100 ns
    ```
    - A DRAM access costs about `200 CPU cycles`. Without a cache, a fast processor would run at the speed of its memory and waste almost all of its capability.

    How the cache is placed
    ```
       CPU  <->  L1  <->  L2  <->  L3  <->  Main memory (DRAM)
       ~1cy     ~4cy    ~12cy    ~40cy       ~200cy

       L1 : 32-64 KB, split into instruction and data caches, private per core
       L2 : 256 KB - 1 MB, private per core
       L3 : 8-32 MB, shared by all cores
    ```

    How an access works
    ```
       1. The CPU requests an address.
       2. The cache is checked first.

            HIT  -> the data is returned in a few cycles. Main memory is
                    never touched.

            MISS -> the whole BLOCK containing the word is fetched from main
                    memory, copied into the cache, and the access is retried.
       3. Because of locality, the following accesses to that block are hits.
    ```

    Why it works — the principle of locality
    ```
       Temporal locality : a location just used is likely to be used again soon
                           -> loop bodies, counters, frequently called functions

       Spatial locality  : locations near one just used are likely to be needed
                           -> arrays and sequential instructions, which is why a
                              whole BLOCK is fetched rather than a single word
    ```
    - Because of this, a cache of a few megabytes satisfies `90-99 per cent` of all accesses.

    The measured effect
    ```
       Average access time = hit time + (miss rate x miss penalty)
    ```
    ```
       Hit time 5 ns , miss penalty 100 ns

       Hit ratio 99 % : 5 + 1  =   6 ns
       Hit ratio 95 % : 5 + 5  =  10 ns
       Hit ratio 90 % : 5 + 10 =  15 ns
       No cache       :           105 ns
    ```
    - With a 95 per cent hit ratio the machine is `more than ten times` faster than it would be with no cache.

    Other ways it raises speed
    - `Keeps the pipeline full.` An instruction-fetch miss stalls the entire pipeline for hundreds of cycles; the instruction cache prevents that.
    - `Reduces bus traffic.` Hits never reach the memory bus, leaving it free for DMA and for the other cores.
    - `Helps multicore scaling`, because each core's private L1 and L2 absorb its own traffic instead of contending for shared memory.
    - `Prefetching` fetches blocks before they are requested, hiding the miss penalty entirely for predictable access patterns.

    Design choices that affect the gain
    ```
       Size          : larger reduces capacity misses, but is slower and costlier
       Block size    : larger exploits spatial locality, but raises the miss
                       penalty and can waste bandwidth
       Associativity : higher reduces conflict misses, but slows each access
       Write policy  : write-back reduces bus traffic; write-through is simpler
       Replacement   : LRU gives the best hit ratio in practice
    ```

    - The essential statement: cache memory does not make the CPU or the RAM any faster. It makes the `average` memory access fast, by ensuring that the slow level is reached only a few times in every hundred requests.

## Secondary Storage (HDD vs SSD) (10)

1. Storage technology selection directly impacts banking operations. Server A will host the Core Banking Database. Server B will host 10 years of immutable archive data. Compare Hard Disk Drives (HDD) and Solid State Drives (SSD). *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer: Server A — the Core Banking Database → use `SSD` (NVMe)
   Server B — 10 years of immutable archive → use `HDD`

   Comparison of the two technologies

   | Point | HDD (Hard Disk Drive) | SSD (Solid State Drive) |
   |---|---|---|
   | Technology | Spinning magnetic platters, moving head | NAND flash, no moving parts |
   | Sequential read | 100-200 MB/s | 500 MB/s (SATA) to 7,000 MB/s (NVMe) |
   | Random IOPS | 100-200 | 100,000 to 1,000,000 |
   | Access latency | 5-10 ms | 20-100 microseconds |
   | Cost per TB | Very low | 3 to 6 times higher |
   | Capacity per drive | Up to 24 TB | Up to 30 TB, but costlier |
   | Power | 6-10 W | 2-5 W |
   | Shock resistance | Poor — mechanical | Excellent |
   | Noise and heat | Yes | Minimal |
   | Endurance limit | None; mechanical wear | Limited program/erase cycles per cell |
   | Data retention unpowered | Decades | Falls after a few years without power |
   | Failure mode | Gradual, often warned by SMART | Sudden, once the controller or cells fail |

   Server A — Core Banking Database: `NVMe SSD`
   ```
      Workload  : small RANDOM reads and writes, thousands of concurrent
                  transactions, latency-critical
      Decisive  : random IOPS and latency, not capacity
   ```
   - A core banking system does mostly `random` 8 KB page reads and writes. An HDD delivers about 150 random IOPS; an NVMe SSD delivers hundreds of thousands. That is the difference between a transaction taking 10 ms and 0.1 ms.
   - Every `COMMIT` must reach stable storage before it returns, so write latency directly sets the transaction rate. This is where the mechanical seek and rotational delay of an HDD are fatal.
   - Concurrency: an HDD's single head serialises requests; an SSD serves many queues in parallel.
   - Capacity is not the constraint — a core banking database is usually a few terabytes, which is affordable in SSD.
   - Recommended configuration: `NVMe SSDs in RAID 10`, with the transaction log on its own array, and enterprise-grade drives with power-loss protection and high DWPD (drive writes per day) endurance.

   Server B — 10 years of immutable archive: `HDD`
   ```
      Workload  : write once, read rarely, sequential, enormous volume
      Decisive  : cost per terabyte and long-term retention, not speed
   ```
   - The data is written once and almost never read, so the SSD's random-access advantage is worth nothing here.
   - `Cost per terabyte` dominates. Ten years of banking archive runs to hundreds of terabytes; HDDs cost a third to a sixth as much, and that difference is the whole budget.
   - `Long-term retention`: an unpowered SSD gradually loses charge from its floating gates and can lose data after a few years. Magnetic media holds its state for decades, which suits an archive that may sit untouched.
   - `Endurance` is irrelevant, because the data is written once. The SSD's limited write cycles are not a factor either way.
   - Sequential throughput of 150-200 MB/s is perfectly adequate for the occasional bulk retrieval or audit.
   - Recommended configuration: high-capacity `nearline HDDs in RAID 6` (double parity, because rebuilds on large drives take many hours), with WORM or object-lock storage for immutability, plus tape or cloud cold storage as the off-site copy.

   Summary
   ```
      Server A : NVMe SSD  -> buy IOPS and latency
      Server B : HDD       -> buy capacity per taka and long-term retention
   ```
   - The reasoning to state clearly: `match the storage to the access pattern`. Random, latency-critical, high-value data justifies the SSD premium; sequential, cold, high-volume data does not. Using SSDs for the archive would waste money without improving anything, and using HDDs for the core database would throttle the whole bank.

2. **a) Define the term "SSD". Briefly describe the working principle of "SSD".** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1342 (ET: N/A)]*

   Answer: Definition
   - An `SSD (Solid State Drive)` is a storage device that keeps data in `NAND flash memory` instead of on spinning magnetic platters. It has `no moving parts` at all — hence "solid state".

   Main components
   ```
      NAND flash chips : where the data is actually stored
      Controller       : the processor that manages everything
      DRAM cache       : holds the mapping table and buffers writes
      Host interface   : SATA, or PCIe/NVMe for high performance
   ```

   Working principle

   1. The storage cell — a floating-gate transistor
   ```
           Control gate
         ================
         ~~~~~~~~~~~~~~~~   oxide insulator
         ################   FLOATING GATE  <- charge is trapped here
         ~~~~~~~~~~~~~~~~   oxide insulator
         +--------------+
         | N+ |      | N+|   channel
         +--------------+
   ```
   - The floating gate is completely surrounded by insulating oxide, so any charge placed on it `stays there without power`. That is what makes the drive non-volatile.
   ```
      Charge trapped on the floating gate  ->  raises the threshold voltage  ->  bit = 0
      No charge on the floating gate       ->  low threshold voltage         ->  bit = 1
   ```

   2. Writing (programming)
   - A high voltage on the control gate forces electrons through the oxide onto the floating gate by `Fowler-Nordheim tunnelling`. This is what sets the bit.

   3. Reading
   - A moderate voltage is applied to the control gate and the controller checks whether the channel conducts. A charged floating gate blocks conduction; an uncharged one allows it. The cell is not disturbed by reading.

   4. Erasing
   - Electrons are pulled off the floating gate by the reverse voltage. Erasing works only on a whole `block` (typically 128 KB to 4 MB), never on a single cell — this is the key limitation of flash.
   ```
      Read  and PROGRAM : per PAGE  (4-16 KB)
      ERASE             : per BLOCK (many pages)
   ```
   - Because a page cannot be overwritten in place, the controller writes the new data to a fresh page and marks the old one invalid. This is called `out-of-place writing`.

   5. What the controller does
   ```
      Flash Translation Layer (FTL) : maps logical block addresses used by the
           OS onto the constantly changing physical pages
      Wear levelling  : spreads writes evenly, since each cell survives only a
           limited number of program/erase cycles
      Garbage collection : consolidates valid pages and erases stale blocks
      TRIM support    : lets the OS tell the drive which blocks are deleted,
           so they can be erased in advance
      ECC             : corrects the bit errors that flash naturally produces
      Over-provisioning : hidden spare capacity used for the above
   ```

   Cell types
   ```
      SLC : 1 bit per cell  - fastest, ~100,000 cycles, most expensive
      MLC : 2 bits per cell
      TLC : 3 bits per cell - the common consumer choice
      QLC : 4 bits per cell - cheapest, slowest, lowest endurance
   ```
   - More bits per cell means more voltage levels to distinguish, so speed, endurance and reliability all fall as density rises.

   Why it is fast
   - No seek time and no rotational delay: any page is reached electrically in microseconds.
   - Many flash chips are accessed `in parallel` across several channels.
   - NVMe over PCIe replaces the old SATA/AHCI stack with deep parallel queues, raising throughput to several gigabytes per second.

   - Practical consequence: an SSD's advantage over an HDD is largest in `random` access — roughly a hundredfold — and smallest in long sequential transfers, where it is three or four times faster. Since operating systems and databases do mostly random access, the real-world difference is enormous.

3. **Write two SSD characteristics?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

   Answer: Two characteristics of an SSD
   ```
      1. It has NO MOVING PARTS.
         Data is stored in NAND flash memory rather than on spinning platters,
         so there is no seek time and no rotational delay. This is why an SSD
         is shock resistant, silent, cool and low in power.

      2. It is VERY FAST, especially for RANDOM access.
         Access latency is 20-100 microseconds against 5-10 milliseconds for a
         hard disk, and it delivers 100,000+ IOPS against about 150 for an HDD.
   ```

   Further characteristics, if more are wanted
   ```
      Non-volatile      : charge trapped on a floating gate keeps the data
                          without power
      Limited endurance : each cell survives a fixed number of program/erase
                          cycles, so the controller performs wear levelling
      Sequential speed  : 500 MB/s (SATA) to 7,000 MB/s (NVMe)
      Low power         : 2-5 W against 6-10 W for an HDD
      Silent and cool   : no motor, no head assembly
      Compact           : available in the small M.2 form factor
      Higher cost per TB: 3 to 6 times an HDD
      Sudden failure    : it usually fails without the gradual warning signs
                          an HDD gives
   ```

   - The one-line version for an exam: an SSD is `non-volatile flash storage with no moving parts, giving microsecond access times and very high random IOPS`.

4. **How can you define SSD?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 676 (ET: N/A)]*

   Answer: An `SSD (Solid State Drive)` is a storage device that stores data in `NAND flash memory` chips instead of on spinning magnetic platters. It has `no moving parts`, which is where the name "solid state" comes from.

   How it stores a bit
   - Each cell is a `floating-gate transistor`. The floating gate is surrounded by insulating oxide, so charge placed on it stays there with no power at all — that is what makes the drive non-volatile.
   ```
      Charge trapped on the floating gate  ->  bit = 0
      No charge                            ->  bit = 1
   ```
   - Writing forces electrons onto the gate by `tunnelling`; erasing pulls them off, and erasing works only on a whole `block`, never on a single cell.

   Main components
   ```
      NAND flash chips : the storage itself
      Controller       : runs the flash translation layer, wear levelling,
                         garbage collection and error correction
      DRAM cache       : holds the mapping table and buffers writes
      Interface        : SATA, or PCIe / NVMe for high performance
   ```

   Key characteristics
   ```
      No moving parts   : no seek time, no rotational delay
      Access latency    : 20-100 microseconds (HDD: 5-10 milliseconds)
      Random IOPS       : 100,000 to 1,000,000 (HDD: about 150)
      Sequential speed  : 500 MB/s SATA to 7,000 MB/s NVMe
      Power             : 2-5 W (HDD: 6-10 W)
      Shock resistance  : excellent
      Noise and heat    : minimal
      Cost per TB       : 3 to 6 times an HDD
      Endurance         : each cell survives a limited number of write cycles
   ```

   Cell types
   ```
      SLC : 1 bit per cell - fastest, longest life, most expensive
      MLC : 2 bits per cell
      TLC : 3 bits per cell - the common consumer choice
      QLC : 4 bits per cell - cheapest, slowest, lowest endurance
   ```

   - Where it is used: operating system and application drives, database servers, laptops, and anywhere random access dominates. `HDDs` remain the choice for bulk archives, where cost per terabyte matters more than speed.

5. **(খ) Solid State Drives (SSD) এর কার্যপ্রণালী ও ব্যবহার লিখুন।** *[BPSC Sub-Assistant Maintenance Engineer 13.10.2022 compact it 704 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Working principle of an SSD

   An `SSD (Solid State Drive)` stores data in `NAND flash` memory chips and has no moving parts.

   The storage cell — a floating-gate transistor
   ```
           Control gate
         ================
         ~~~~~~~~~~~~~~~~   oxide insulator
         ################   FLOATING GATE  <- charge is trapped here
         ~~~~~~~~~~~~~~~~   oxide insulator
         +--------------+
         | N+ |      | N+|
         +--------------+
   ```
   - The floating gate is completely enclosed by insulating oxide, so charge placed on it remains without power. That is what makes the drive `non-volatile`.
   ```
      Charge on the floating gate   ->  high threshold voltage  ->  bit = 0
      No charge                     ->  low threshold voltage   ->  bit = 1
   ```

   Operations
   ```
      PROGRAM (write) : a high voltage on the control gate forces electrons
           through the oxide onto the floating gate by Fowler-Nordheim
           tunnelling. Done a PAGE at a time (4-16 KB).

      READ : a moderate voltage is applied and the controller checks whether
           the channel conducts. A charged gate blocks conduction. Reading
           does not disturb the cell.

      ERASE : the reverse voltage pulls the electrons off. Erasing works only
           on a whole BLOCK (128 KB to 4 MB), never on one cell. This is
           flash's fundamental limitation.
   ```
   - Because a page cannot be overwritten in place, the controller writes new data to a fresh page and marks the old one invalid — `out-of-place writing`.

   What the controller does
   ```
      Flash Translation Layer : maps the OS's logical addresses onto the
           constantly changing physical pages
      Wear levelling          : spreads writes evenly, since each cell has a
           limited number of program/erase cycles
      Garbage collection      : consolidates valid pages and erases stale blocks
      TRIM                    : the OS tells the drive which blocks are deleted
      ECC                     : corrects the bit errors flash naturally produces
      Over-provisioning       : hidden spare capacity used for the above
   ```

   Components
   ```
      NAND flash chips + Controller + DRAM cache + Interface (SATA or NVMe)
   ```

   Cell types
   ```
      SLC 1 bit/cell , MLC 2 , TLC 3 , QLC 4
      More bits per cell -> cheaper and denser, but slower and less durable
   ```

   Uses of an SSD
   - `Operating system and application drives` — boot time falls from a minute to a few seconds, and applications launch almost instantly.
   - `Database and transaction servers` — random IOPS is the decisive factor, and an SSD gives hundreds of thousands against an HDD's 150.
   - `Laptops and portable devices` — light, shock resistant, silent, cool and low in power, which extends battery life.
   - `Virtualisation hosts`, where many virtual machines generate heavily random I/O.
   - `Video editing and content creation`, for high sequential throughput.
   - `Caching tier` in front of an HDD array — a hybrid or tiered storage design.
   - `Embedded and industrial systems`, where vibration would destroy a hard disk.
   - `Data centres and cloud storage` for hot data, with HDDs kept for cold archives.

   - Where an HDD is still preferred: `bulk archives and backups`, because cost per terabyte is three to six times lower and magnetic media retains data for decades without power, whereas an unpowered SSD gradually loses charge.

6. **In a solid state drive data is sarved to a pool of NAND flash. NAND itself is made up of what are called floating gate transmission. How does floating gate transmission store 0 and 1?** *[BTRC Assistant Director (Technical) 2021 compact it 808-809 (ET: IBA)]*

   Answer: A `floating-gate transistor` is the storage cell of NAND flash. It is an ordinary MOSFET with a second, completely insulated gate placed between the control gate and the channel.

   Structure
   ```
           Control gate      <- the gate the circuit drives
         ==================
         ~~~~~~~~~~~~~~~~~~   oxide insulator
         ##################   FLOATING GATE  <- charge is trapped here
         ~~~~~~~~~~~~~~~~~~   tunnel oxide
         +----------------+
         | N+ |        | N+|   source          drain
         +----------------+
                 channel
   ```
   - The floating gate is surrounded on all sides by insulating silicon dioxide. Once electrons are placed on it they have `nowhere to go`, so the charge stays for years `with no power at all`. That is exactly why flash is non-volatile.

   How a 0 and a 1 are stored
   ```
      Bit = 1  :  NO charge on the floating gate
                  The control gate's field reaches the channel normally, so the
                  transistor turns ON at a LOW threshold voltage.
                  This is the ERASED state - a fresh block is all 1s.

      Bit = 0  :  ELECTRONS TRAPPED on the floating gate
                  The trapped negative charge partly cancels the control gate's
                  field, so a HIGHER voltage is needed to turn the transistor on.
                  The threshold voltage has been RAISED.
   ```
   ```
      Threshold voltage
           |
           |        1 (erased)        0 (programmed)
           |          /\                    /\
           |         /  \                  /  \
           |________/____\________________/____\_______ Vt
                    low                  high
                           ^
                        read voltage applied here
   ```

   Writing a 0 — programming
   - A high positive voltage (about 20 V) is applied to the control gate. Electrons in the channel gain enough energy to cross the thin tunnel oxide onto the floating gate. This is `Fowler-Nordheim tunnelling`, or hot-electron injection in some designs.

   Writing a 1 — erasing
   - A high voltage is applied in the reverse direction, pulling the electrons back off the floating gate. Erasing works only on a `whole block`, never on one cell — which is why flash cannot overwrite in place.

   Reading
   - A fixed `read voltage` between the two thresholds is applied to the control gate.
   ```
      Transistor CONDUCTS      ->  low threshold  ->  no charge   ->  bit = 1
      Transistor does NOT conduct -> high threshold -> charge present -> bit = 0
   ```
   - Reading does not disturb the stored charge, so a cell can be read an unlimited number of times.

   Storing more than one bit per cell
   - The amount of charge can be controlled precisely, giving several distinguishable threshold levels.
   ```
      SLC : 2 levels  = 1 bit per cell   - fastest, ~100,000 cycles
      MLC : 4 levels  = 2 bits per cell
      TLC : 8 levels  = 3 bits per cell  - the common consumer choice
      QLC : 16 levels = 4 bits per cell  - cheapest, slowest, least durable
   ```
   - The more levels are packed into the same voltage range, the narrower the margin between them, so speed, endurance and reliability all fall as density rises.

   Why the cells wear out
   - Every program and erase cycle drives electrons through the `tunnel oxide` at high voltage, and each passage damages it slightly. After thousands of cycles the oxide leaks and the cell can no longer hold charge reliably.
   ```
      SLC : ~100,000 cycles     MLC : ~10,000
      TLC : ~3,000              QLC : ~1,000
   ```
   - This is why the SSD controller performs `wear levelling`, spreading writes evenly across all blocks so that no small area is exhausted while the rest of the drive is untouched.
   - It is also why an `unpowered` SSD gradually loses data: the trapped charge slowly leaks away over a few years, whereas magnetic media holds its state for decades.

7. **Which of the following is the unit of Hard Disk Drive? (a) Megaharz (b) Kiloharz (c) Gigabyte (d) None** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*

   Answer: The answer is `(c) Gigabyte`.

   - The `gigabyte (GB)` is a unit of `storage capacity`, which is what a hard disk drive is measured in. Capacity is the amount of data the disk can hold.
   ```
      1 KB = 1024 bytes
      1 MB = 1024 KB
      1 GB = 1024 MB
      1 TB = 1024 GB
   ```
   - Modern hard disks are sold in sizes from 500 GB up to 24 TB.

   Why the other options are wrong
   ```
      (a) Megahertz : a unit of FREQUENCY, one million cycles per second.
          It measures clock speed - the CPU, the bus, the RAM - not capacity.

      (b) Kilohertz  : also a unit of frequency, one thousand cycles per second.
          Used for audio and low-frequency signals.

      (d) None       : incorrect, since (c) is right.
   ```

   Units actually used to describe a hard disk
   ```
      Capacity        : gigabytes (GB), terabytes (TB)
      Rotational speed: revolutions per minute (RPM) - 5400, 7200, 10000, 15000
      Transfer rate   : megabytes per second (MB/s)
      Seek time       : milliseconds (ms)
      Cache buffer    : megabytes (MB)
      Interface speed : gigabits per second (Gbps) for SATA
   ```
   - Note that `RPM` and `Gbps` do appear in a disk's specification, but they describe its speed, not its size. The question asks for the unit of the drive itself, which is capacity.

   - One practical point worth knowing: manufacturers advertise capacity in `decimal` units where 1 GB = 1,000,000,000 bytes, while an operating system reports `binary` units where 1 GiB = 1,073,741,824 bytes. That is why a "1 TB" disk shows as about 931 GB in Windows — nothing is missing, the two are simply counting differently.

8. **Consider a magnetic disk consisting of 16 heads and 400 cylinders. This disk has four 100-cylinder zones with the cylinders in different zones containing 160, 200, 240. and 280 sectors, respectively. Assume that each sector contains 512 bytes, average seek time between adjacent cylinders is 1 msec, and the disk rotates at 7200 RPM. Calculate the (a) disk capacity (b) maximum data transfer rate.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*

   Answer: Given
   ```
      Heads (surfaces)      = 16
      Cylinders             = 400, divided into 4 zones of 100 cylinders
      Sectors per track     = 160, 200, 240, 280 in the four zones
      Bytes per sector      = 512
      Rotational speed      = 7200 RPM
      Seek time (adjacent)  = 1 ms
   ```
   - One `cylinder` is the set of tracks at the same radius on all 16 surfaces, so each cylinder holds 16 tracks.

   (a) Disk capacity

   Capacity of each zone
   ```
      Zone capacity = cylinders x heads x sectors/track x bytes/sector

      Zone 1 : 100 x 16 x 160 x 512 =  131,072,000 bytes
      Zone 2 : 100 x 16 x 200 x 512 =  163,840,000 bytes
      Zone 3 : 100 x 16 x 240 x 512 =  196,608,000 bytes
      Zone 4 : 100 x 16 x 280 x 512 =  229,376,000 bytes
   ```

   Total
   ```
      Total = 131,072,000 + 163,840,000 + 196,608,000 + 229,376,000

            = 720,896,000 bytes
   ```

   In convenient units
   ```
      720,896,000 / 1024          = 704,000 KB
                 / 1024           = 687.5  MB
                 / 1024           = 0.6714 GB   (binary, GiB)

      In decimal units : 0.72 GB
   ```
   ```
      Disk capacity = 720,896,000 bytes = 687.5 MB (binary) = 0.72 GB (decimal)
   ```

   Shortcut
   ```
      Total sectors per cylinder-set is the same in every zone structure, so

      Total = 100 x 16 x (160 + 200 + 240 + 280) x 512
            = 100 x 16 x 880 x 512
            = 720,896,000 bytes           same answer
   ```

   (b) Maximum data transfer rate

   - The maximum rate comes from the `outermost zone`, which has the most sectors per track — 280.
   ```
      Rotational speed = 7200 RPM
                       = 7200 / 60 = 120 revolutions per second

      Time for one revolution = 1 / 120 = 8.333 ms
   ```
   - In one revolution the head reads one entire track.
   ```
      Data per track (zone 4) = 280 sectors x 512 bytes = 143,360 bytes
   ```
   ```
      Maximum transfer rate = data per track x revolutions per second

                            = 143,360 x 120

                            = 17,203,200 bytes per second
   ```
   ```
      Maximum data transfer rate = 17,203,200 B/s
                                 = 17.2 MB/s  (decimal)
                                 = 16.4 MiB/s (binary)
                                 = 137.6 Mbps
   ```

   Minimum rate, for comparison
   ```
      Innermost zone : 160 x 512 x 120 = 9,830,400 B/s = 9.83 MB/s
   ```
   - The rate varies with the zone, which is exactly why `zone bit recording` is used: outer tracks are physically longer, so more sectors fit on them and they deliver more data per revolution.

   Other useful figures
   ```
      Average rotational latency = half a revolution = 8.333 / 2 = 4.17 ms
      Full-stroke seek (400 cylinders x 1 ms)        = 400 ms
      Sector transfer time (zone 4) = 8.333 ms / 280 = 0.0298 ms
   ```

9. **Consider a disk pack with the following specifications- 16 surfaces, 128 tracks per surface, 256 sectors per track and 512 bytes per sector. Answer the following questions: (a) What is the capacity of disk pack? (b) If the format overhead is 32 bytes per sector, what is the formatted disk space? (c) If the disk is rotating at 3600 rpm, what is the data transfer rate?** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 924-925 (ET: CTI)]*

   Answer: Given
   ```
      Surfaces           = 16
      Tracks per surface = 128
      Sectors per track  = 256
      Bytes per sector   = 512
      Rotational speed   = 3600 RPM
   ```

   (a) Capacity of the disk pack
   ```
      Capacity = surfaces x tracks/surface x sectors/track x bytes/sector

               = 16 x 128 x 256 x 512
   ```
   Step by step
   ```
      16 x 128        =     2,048 tracks in total
      2,048 x 256     =   524,288 sectors in total
      524,288 x 512   = 268,435,456 bytes
   ```
   ```
      Capacity = 268,435,456 bytes
               = 262,144 KB
               = 256 MB
   ```
   - Neatly, `16 x 128 x 256 x 512 = 2^4 x 2^7 x 2^8 x 2^9 = 2^28 = 256 MB`.

   (b) Formatted disk space, with 32 bytes of overhead per sector
   - The overhead is the sector header, the address mark and the ECC field. It occupies space on the disk but cannot hold user data.
   ```
      Usable bytes per sector = 512 - 32 = 480 bytes

      Formatted capacity = 524,288 sectors x 480 bytes

                         = 251,658,240 bytes
   ```
   ```
      Formatted disk space = 251,658,240 bytes
                           = 245,760 KB
                           = 240 MB
   ```
   Check
   ```
      Overhead lost = 524,288 x 32 = 16,777,216 bytes = 16 MB

      256 MB - 16 MB = 240 MB          correct

      Overhead percentage = 32 / 512 = 6.25 %
   ```

   (c) Data transfer rate at 3600 RPM
   ```
      Rotational speed = 3600 RPM
                       = 3600 / 60 = 60 revolutions per second

      Time for one revolution = 1 / 60 = 16.67 ms
   ```
   - In one revolution the head reads one complete track.
   ```
      Data per track = 256 sectors x 512 bytes = 131,072 bytes = 128 KB
   ```
   ```
      Transfer rate = data per track x revolutions per second

                    = 131,072 x 60

                    = 7,864,320 bytes per second
   ```
   ```
      Data transfer rate = 7,864,320 B/s
                         = 7,680 KB/s
                         = 7.5 MB/s (binary)
                         = 7.86 MB/s (decimal)
                         = 62.9 Mbps
   ```

   Formatted transfer rate, if the overhead is excluded
   ```
      Useful data per track = 256 x 480 = 122,880 bytes
      Rate = 122,880 x 60 = 7,372,800 B/s = 7.03 MB/s
   ```

   Other useful figures
   ```
      Average rotational latency = half a revolution = 16.67 / 2 = 8.33 ms
      One sector's transfer time = 16.67 ms / 256   = 0.065 ms
      Capacity of one surface    = 128 x 256 x 512  = 16 MB
      Capacity of one cylinder   = 16 x 256 x 512   = 2 MB
   ```
   - The formula to remember: `transfer rate = bytes per track x rotations per second`. It follows directly from the fact that one full revolution passes exactly one track under the head.

10. **(i) Optical disk কীভাবে data Read/Write করে বর্ণনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 951 (ET: N/A)], [BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) An `optical disc` — CD, DVD or Blu-ray — stores data as microscopic marks on a spiral track, and reads them with a `laser beam`. There are no magnetic fields and no contact with the surface.

    Physical structure
    ```
       +---------------------------+  protective lacquer / label
       +---------------------------+  reflective aluminium layer
       ~~~~~~ pits and lands ~~~~~~   the data layer
       +---------------------------+
       |    polycarbonate plastic  |  1.2 mm, the laser reads through this
       +---------------------------+
                    ^
                  LASER
    ```
    - The data sits on one continuous `spiral track` running from the centre outward — unlike a hard disk, which has concentric circular tracks.

    How data is represented
    ```
       PIT  : a microscopic depression burned or moulded into the surface
       LAND : the flat area between pits

       A TRANSITION from pit to land, or land to pit  ->  binary 1
       NO transition along a fixed length             ->  binary 0
    ```
    - Note that a pit is not "1" and a land "0". It is the `change` that encodes a 1. This scheme is `NRZI` encoding, and it is used because the laser detects edges far more reliably than absolute levels.
    - The actual bits are further encoded — `EFM` (eight-to-fourteen modulation) on a CD — so that runs of identical symbols never become too long for the timing circuit to track.

    Reading
    ```
       1. A low-power laser beam is focused through the plastic onto the
          reflective layer.
       2. A LAND reflects the beam strongly straight back.
       3. A PIT is about a quarter of a wavelength deep, so the light reflected
          from it interferes destructively with light from the surrounding land,
          and much less returns.
       4. A photodiode measures the reflected intensity.
       5. The changes in intensity are decoded into a bit stream, then
          error-corrected and passed to the computer.
    ```
    ```
       Strong reflection  ->  land
       Weak reflection    ->  pit
       Transition between them -> a 1 bit
    ```

    Writing
    ```
       Pressed discs (CD-ROM, DVD-ROM)
            Pits are physically STAMPED into the plastic during manufacture
            from a glass master. Cheap in volume, and unchangeable.

       Recordable (CD-R, DVD-R)
            A layer of ORGANIC DYE sits above the reflective layer. A
            high-power laser burns dark spots into it, which absorb light and
            so behave like pits. Permanent - write once.

       Rewritable (CD-RW, DVD-RW)
            A PHASE-CHANGE alloy is used. A high-power laser melts a spot and
            it cools into the AMORPHOUS state, which reflects poorly (a pit).
            A medium-power laser anneals it back into the CRYSTALLINE state,
            which reflects well (a land). This can be repeated about 1,000 times.
    ```

    Capacity depends on the laser's wavelength
    ```
       CD        : 780 nm infrared laser  -> 700 MB
       DVD       : 650 nm red laser       -> 4.7 GB (single layer)
       Blu-ray   : 405 nm blue-violet     -> 25 GB per layer
    ```
    - A shorter wavelength can be focused to a smaller spot, so the pits and the track spacing can be made smaller and more data fits on the same 12 cm disc.

    Rotation
    ```
       CLV (Constant Linear Velocity)  : the disc slows as the head moves
            outward, so the data passes the laser at a constant speed.
            Used for audio and video, where a steady data rate is needed.

       CAV (Constant Angular Velocity) : constant RPM, so the outer tracks
            deliver data faster. Used in data drives.
    ```

    - Advantages: cheap to duplicate, removable, immune to magnetic fields, and long-lived if stored properly. Disadvantages: slow (1-22 MB/s), small capacity by modern standards, and easily damaged by scratches — which is why optical media has largely been replaced by pen drives and cloud storage.

## Instruction Pipelining & Hazards (9)

1. Why do modern processor designs favor a multi-stage pipelined approach over a single-cycle implementation? [SO IT 25-07-2026]

   Answer: A `single-cycle` implementation completes one whole instruction per clock cycle. A `pipelined` implementation splits the instruction into stages and overlaps consecutive instructions, so one instruction `completes` every cycle even though each takes several cycles to pass through.

   The problem with a single-cycle design
   - The clock period must be long enough for the `slowest` instruction to finish completely.
   ```
      Instruction fetch      200 ps
      Register read          100 ps
      ALU operation          200 ps
      Data memory access     200 ps
      Register write         100 ps
      -----------------------------
      Load word (longest)    800 ps   ->  the clock period must be 800 ps
   ```
   - Every other instruction is padded out to the same 800 ps. An `ADD`, which needs only 600 ps, wastes 200 ps every time; a branch wastes even more.
   - Hardware is idle most of the time — the data memory sits unused during an ADD, and the ALU sits unused during a fetch.

   How pipelining fixes it
   ```
      Clock period = the slowest SINGLE STAGE, not the whole instruction
                   = 200 ps , not 800 ps
   ```
   ```
      Single cycle
      I1 |========800ps========|
      I2                        |========800ps========|
      I3                                               |=======...

      Pipelined (5 stages of 200 ps)
      I1 | IF | ID | EX |MEM | WB |
      I2      | IF | ID | EX |MEM | WB |
      I3           | IF | ID | EX |MEM | WB |
      I4                | IF | ID | EX |MEM | WB |
                             ^ from here, one instruction finishes every 200 ps
   ```

   Speed-up
   ```
      Ideal speed-up = number of pipeline stages = k

      Actual speed-up = (k x n) / (k + n - 1)
           where n is the number of instructions

      For large n, this approaches k.
   ```
   ```
      1000 instructions, 5 stages :

      Single cycle : 1000 x 800 ps = 800,000 ps
      Pipelined    : (5 + 999) x 200 ps = 200,800 ps

      Speed-up = 800,000 / 200,800 = 3.98 times
   ```

   Why designers favour it
   - `Much higher throughput.` One instruction completes per cycle instead of one per 800 ps — roughly a fivefold gain for a five-stage pipeline.
   - `Higher clock frequency.` The clock is set by the slowest stage, so it can be raised far above what a single-cycle design allows. Deeper pipelines allow even higher clocks, which is how GHz speeds were reached.
   - `Better hardware utilisation.` Every functional unit is busy on a different instruction at the same time, instead of one being used while the rest idle.
   - `No wasted time on short instructions.` Each instruction uses only the stages it needs, at full clock rate.
   - `Scalable.` More stages can be added, and the design extends naturally to superscalar issue.
   - `Cost effective` — it needs only pipeline registers between the stages, not duplicated functional units.

   The costs, which must also be stated
   ```
      Latency of a single instruction is UNCHANGED, or slightly worse, because
           of the pipeline register delays. Only throughput improves.

      HAZARDS :
         Structural : two stages want the same hardware unit
         Data       : an instruction needs a result not yet written back
                      -> solved by forwarding, or by stalling
         Control    : a branch is not resolved until later
                      -> solved by branch prediction; a misprediction flushes
                         the pipeline
      Deeper pipelines make the misprediction penalty larger, which is why
      the Pentium 4's 31-stage pipeline was abandoned.
   ```

   - Summary: a single-cycle design wastes time on every instruction because the clock must suit the worst one. Pipelining sets the clock by the `slowest stage` instead, and overlaps instructions so the hardware is never idle — buying a large gain in throughput at the cost of managing hazards.

2. **Write down the names of different stages of instruction pipelining in a multi-cycle datapath architecture. What is a data-hazard in a pipelined datapath?** *[BPSC (Ministry) Network/Website Manager (CSE) 21.05.2025 compact it 1340 (ET: N/A)]*

   Answer: Stages of instruction pipelining

   The classic `five-stage` pipeline, used in MIPS and DLX and taught as the standard model:
   ```
      1. IF  - Instruction Fetch
           Read the instruction from memory at the address in the PC,
           and increment the PC.

      2. ID  - Instruction Decode / Register Fetch
           Decode the opcode, and read the source operands from the
           register file. The branch target is also computed here.

      3. EX  - Execute / Address Calculation
           The ALU performs the arithmetic or logic operation, or computes
           the effective memory address for a load or store.

      4. MEM - Memory Access
           Read from or write to data memory. Only LOAD and STORE use this
           stage; other instructions pass through it doing nothing.

      5. WB  - Write Back
           Write the result into the destination register.
   ```
   ```
      I1 | IF | ID | EX |MEM | WB |
      I2      | IF | ID | EX |MEM | WB |
      I3           | IF | ID | EX |MEM | WB |
      I4                | IF | ID | EX |MEM | WB |
                             ^ from here one instruction completes per cycle
   ```
   - Between every pair of stages sits a `pipeline register` (IF/ID, ID/EX, EX/MEM, MEM/WB) which carries the instruction's data and control signals forward.

   The simpler four-stage model is also quoted
   ```
      Fetch -> Decode -> Execute -> Write back
   ```
   - Modern processors use far deeper pipelines: the Intel Core family uses 14-19 stages, splitting fetch, decode, rename, schedule, execute, memory and retire.

   Data hazard

   - A `data hazard` occurs when an instruction needs a value that an earlier instruction in the pipeline has computed but has `not yet written back`. The pipeline would read a stale value.

   Example
   ```asm
      ADD  R1, R2, R3      ; R1 = R2 + R3 , written back in WB (cycle 5)
      SUB  R4, R1, R5      ; needs R1 in EX (cycle 4) - too early!
   ```
   ```
      Cycle :     1    2    3    4    5    6
      ADD      | IF | ID | EX |MEM | WB |
      SUB           | IF | ID | EX |MEM | WB |
                               ^         ^
                               needs R1  R1 is only written here
   ```

   Three kinds of data hazard
   ```
      RAW (Read After Write)  : the true dependency shown above.
                                The only one that occurs in a simple in-order
                                pipeline.
      WAR (Write After Read)  : a later instruction writes a register an
                                earlier one has not yet read. Occurs only with
                                out-of-order execution.
      WAW (Write After Write) : two instructions write the same register out
                                of order.
   ```

   How data hazards are solved
   ```
      1. FORWARDING (bypassing) - the usual solution.
         The ALU result is routed directly from the EX/MEM pipeline register
         back to the ALU input of the next instruction, without waiting for WB.
         This removes most RAW hazards with no lost cycles.

      2. STALLING (pipeline bubble).
         When forwarding cannot help - a LOAD followed immediately by a use of
         the loaded value - the pipeline inserts one bubble, because the data
         is not available until the end of MEM.

            LW   R1, 0(R2)
            ADD  R3, R1, R4     ; must stall one cycle

      3. COMPILER SCHEDULING.
         The compiler reorders independent instructions into the gap, so the
         stall does no harm.

      4. OUT-OF-ORDER EXECUTION with register renaming, in modern processors,
         which removes WAR and WAW entirely and hides most RAW latency.
   ```

   The other two hazard types, for completeness
   ```
      Structural hazard : two stages need the same hardware in the same cycle,
           for example instruction fetch and data access competing for one
           memory. Solved by separate instruction and data caches.

      Control hazard    : a branch is not resolved until the EX stage, so the
           instructions fetched after it may be wrong. Solved by branch
           prediction; a misprediction flushes the pipeline.
   ```

3. **(c) Fill in the gaps RISC or CISC:** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 416 (ET: BUET)]*
   * (i) Pipelining is less efficient due to instruction complexity and variability ______
   * (ii) Emphasis on hardware simplicity and efficiency ______
   * (iii) Complex decoding due to variable instruction length ______
   * (iv) Each instruction typically executes in a single clock cycle ______

   Answer: (i) Pipelining is less efficient due to instruction complexity and variability — `CISC`
   - CISC instructions vary in length (1 to 15 bytes in x86) and in how many cycles they take. A pipeline works best when every instruction is the same size and takes the same time, so this variability causes stalls and makes the pipeline control logic complicated.

   (ii) Emphasis on hardware simplicity and efficiency — `RISC`
   - RISC deliberately keeps the instruction set small and regular so that the control unit can be `hardwired` rather than microprogrammed. The saved silicon is spent on more registers, larger caches and deeper pipelines.

   (iii) Complex decoding due to variable instruction length — `CISC`
   - Because a CISC instruction's length is not known until part of it has been decoded, the processor cannot simply fetch a fixed number of bytes per instruction. Modern x86 chips need several decoder units working in parallel just to keep up.

   (iv) Each instruction typically executes in a single clock cycle — `RISC`
   - Fixed-length, simple instructions each complete in about one cycle. This is what makes RISC pipelines efficient, since every stage takes the same time.

   Summary

   | Statement | Answer |
   |---|---|
   | (i) Pipelining is less efficient due to instruction complexity and variability | `CISC` |
   | (ii) Emphasis on hardware simplicity and efficiency | `RISC` |
   | (iii) Complex decoding due to variable instruction length | `CISC` |
   | (iv) Each instruction typically executes in a single clock cycle | `RISC` |

   Full comparison, for context

   | Point | RISC | CISC |
   |---|---|---|
   | Instruction set | Small and simple | Large and complex |
   | Instruction length | Fixed | Variable |
   | Cycles per instruction | Mostly 1 | Many |
   | Memory access | Only LOAD and STORE | Most instructions can |
   | Registers | Many (32 or more) | Few (8 to 16) |
   | Control unit | Hardwired | Microprogrammed |
   | Pipelining | Easy and efficient | Difficult |
   | Decoding | Simple | Complex |
   | Code size | Larger | Smaller |
   | Compiler effort | Higher | Lower |
   | Power consumption | Low | Higher |
   | Examples | ARM, RISC-V, MIPS, SPARC | Intel x86, AMD64, Motorola 68000 |

   - Practical note: the distinction has blurred. Modern x86 processors decode their CISC instructions into RISC-like `micro-operations` internally, so they are CISC at the interface and RISC in the execution core. RISC still wins decisively on power efficiency, which is why every mobile phone uses ARM.

4. **Difference between mutliprocessor system and multi computer system, Explain Shared memory; discuss the two schemes to maintain cache coherence. What is pipelining? Explain the 4 stages of the pipeline.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 299 (ET: BIBM)]*

   Answer: Multiprocessor versus multicomputer system

   `Multiprocessor` — several CPUs inside `one` computer, sharing the same main memory and one operating system. Communication is through `shared memory`. Also called a `tightly coupled` system.

   `Multicomputer` — several `complete, independent` computers, each with its own CPU, memory and operating system, joined by a network. Communication is by `message passing`. Also called a `loosely coupled` system, or a cluster.

   | Point | Multiprocessor | Multicomputer |
   |---|---|---|
   | Memory | Shared, single address space | Private to each node |
   | Communication | Through shared memory | Message passing over a network |
   | Coupling | Tight | Loose |
   | Operating system | One, for the whole machine | One per node |
   | Speed of communication | Very fast (nanoseconds) | Slower (microseconds) |
   | Scalability | Limited — memory bus contention | Very high — thousands of nodes |
   | Cost | Higher per processor | Lower, built from ordinary machines |
   | Fault tolerance | A failure can stop the system | A node can fail and the rest continue |
   | Programming | Threads, shared variables | MPI, sockets |
   | Examples | A multicore server, SMP machine | Beowulf cluster, Hadoop cluster, cloud |

   Shared memory
   - `Shared memory` means all processors see the `same physical address space`. If processor 1 writes to address X, processor 2 reading X sees the new value. This makes communication as cheap as an ordinary memory access.
   ```
      CPU1   CPU2   CPU3   CPU4
        |      |      |      |
        +------+---+--+------+
                   |
             SHARED MEMORY
   ```
   - Two organisations:
   ```
      UMA  (Uniform Memory Access) : every processor takes the same time to
           reach any location. Simple, but the bus becomes a bottleneck
           beyond a handful of processors. This is classic SMP.

      NUMA (Non-Uniform Memory Access) : each processor has local memory it
           reaches quickly and remote memory it reaches more slowly.
           Scales far better, and is what modern multi-socket servers use.
   ```
   - The difficulty it creates: each processor caches copies of shared data, so the copies can disagree. That is the `cache coherence problem`.

   Two schemes to maintain cache coherence

   `1. Snooping (bus-based)`
   - Every cache controller `watches` (snoops on) the shared bus and sees every transaction issued by every other cache.
   ```
      Write-invalidate  (the common scheme)
         When a processor writes to a block, it broadcasts an INVALIDATE.
         Every other cache holding that block marks its copy invalid.
         The next read by another processor misses and fetches the new value.

      Write-update (write-broadcast)
         The new value itself is broadcast, and every other cache updates its
         copy. Fewer misses, but far more bus traffic, so it is rarely used.
   ```
   - Usually implemented with the `MESI` protocol, in which each cache line is Modified, Exclusive, Shared or Invalid.
   - Simple and fast, but it needs a `broadcast medium`, so it does not scale beyond a few dozen processors.

   `2. Directory-based`
   - A central `directory` records, for every memory block, which caches hold a copy and in what state.
   ```
      Block address | State  | Sharers
      --------------+--------+-----------------
      0x1000        | Shared | CPU1, CPU3
      0x2000        | Modified| CPU2
   ```
   - On a write, the directory sends invalidation messages `only to the caches that actually hold the block` — a point-to-point message, not a broadcast.
   - Scales to hundreds or thousands of processors, which is why it is used in large NUMA machines. The cost is the directory storage and the extra latency of the lookup.

   | Point | Snooping | Directory-based |
   |---|---|---|
   | Needs a broadcast bus | Yes | No |
   | Messages | Broadcast to all | Point-to-point to sharers only |
   | Scalability | Poor, tens of CPUs | Good, hundreds or thousands |
   | Latency | Low | Higher, directory lookup first |
   | Storage overhead | None | Directory entry per block |
   | Used in | Small SMP systems | Large NUMA and distributed shared memory |

   Pipelining
   - `Pipelining` is a technique in which an instruction is divided into stages, and consecutive instructions are `overlapped` so that a different instruction occupies each stage at the same time. One instruction then `completes` every clock cycle, even though each takes several cycles to pass through.

   The four stages
   ```
      1. FETCH   : read the instruction from memory at the address in the PC,
                   and increment the PC.

      2. DECODE  : interpret the opcode, identify the operands, and read
                   them from the register file.

      3. EXECUTE : the ALU performs the arithmetic or logic operation, or
                   computes the effective memory address.

      4. WRITE BACK : store the result in the destination register or in
                   memory.
   ```
   ```
      I1 | F  | D  | E  | W  |
      I2      | F  | D  | E  | W  |
      I3           | F  | D  | E  | W  |
      I4                | F  | D  | E  | W  |
                          ^ from here, one instruction finishes every cycle
   ```
   ```
      Ideal speed-up = number of stages = 4
      Actual speed-up = (k x n) / (k + n - 1)   for n instructions, k stages
   ```
   - Hazards limit the gain: `structural` (two stages want the same unit), `data` (a result is not ready yet — fixed by forwarding or a stall) and `control` (a branch changes the flow — fixed by branch prediction).

5. **6.1 Why do modern processor designs favor a multi-stage pipelined approach over a single-cycle implementation?** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

   Answer: A `single-cycle` design completes one whole instruction per clock cycle, so the clock period must cover the `slowest` instruction. A `pipelined` design splits the instruction into stages and overlaps consecutive instructions, so the clock period need only cover the `slowest stage`.

   The problem with single-cycle
   ```
      Instruction fetch      200 ps
      Register read          100 ps
      ALU operation          200 ps
      Data memory access     200 ps
      Register write         100 ps
      -----------------------------
      Load word (longest)    800 ps  ->  clock period must be 800 ps
   ```
   - Every instruction is padded to 800 ps, even an `ADD` that needs only 600 ps and a branch that needs 500 ps.
   - Most of the hardware is idle at any moment: the data memory does nothing during an ADD, the ALU does nothing during a fetch.

   What pipelining changes
   ```
      Clock period = slowest STAGE = 200 ps , not 800 ps
   ```
   ```
      Single cycle
      I1 |=========800 ps=========|
      I2                           |=========800 ps=========|

      Pipelined, 5 stages of 200 ps
      I1 | IF | ID | EX |MEM | WB |
      I2      | IF | ID | EX |MEM | WB |
      I3           | IF | ID | EX |MEM | WB |
      I4                | IF | ID | EX |MEM | WB |
                             ^ one instruction completes every 200 ps
   ```

   Speed-up
   ```
      Actual speed-up = (k x n) / (k + n - 1)

      1000 instructions, 5 stages :
         Single cycle : 1000 x 800  = 800,000 ps
         Pipelined    : (5 + 999) x 200 = 200,800 ps
         Speed-up     = 3.98 times
   ```

   Reasons designers favour pipelining
   - `Higher throughput` — one instruction finishes per cycle rather than one per 800 ps.
   - `Higher clock frequency` — the clock is set by the slowest stage, not the whole instruction, which is how GHz speeds became possible.
   - `Better hardware utilisation` — every functional unit works on a different instruction simultaneously instead of sitting idle.
   - `No waste on short instructions` — each uses only the stages it needs, at the full clock rate.
   - `Low extra cost` — only pipeline registers are added, not duplicated functional units.
   - `Extensible` — the same idea scales to deeper pipelines and to superscalar issue of several instructions per cycle.

   Costs that must be mentioned
   ```
      Latency of a single instruction does NOT improve; only throughput does.

      Hazards :
         Structural : two stages want the same hardware unit
         Data       : a result is not written back before the next instruction
                      needs it  -> solved by forwarding, else a stall
         Control    : a branch is not resolved until later
                      -> solved by branch prediction; a wrong guess flushes
                         the pipeline

      Deeper pipelines suffer a larger misprediction penalty, which is why the
      Pentium 4's 31-stage design was abandoned in favour of shorter pipelines.
   ```

   - Summary: single-cycle wastes time on every instruction because the clock must suit the worst case. Pipelining sets the clock by the `slowest stage` and keeps every unit busy, buying a large throughput gain in exchange for hazard-handling logic.

6. **How computer Architecture is characterized. What are the 5 stages of the DLX pipeline?** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1049-1050 (ET: BUET)]*

   Answer: How computer architecture is characterized

   Computer architecture is described by the following attributes.

   1. `Instruction Set Architecture (ISA)`
   - The interface the machine presents to software: the instruction set, the data types, the registers, the addressing modes and the exception model.
   ```
      RISC : small, fixed-length, simple instructions (ARM, RISC-V, MIPS)
      CISC : large, variable-length, complex instructions (x86)
   ```

   2. `Word size and data path width` — 8, 16, 32 or 64 bits. It decides how much data is processed per operation and how much memory can be addressed.

   3. `Memory organisation`
   ```
      Von Neumann : one memory for both instructions and data
      Harvard     : separate instruction and data memories, with separate buses
      The memory hierarchy: registers, cache (L1/L2/L3), main memory, disk
      Virtual memory, paging and segmentation
   ```

   4. `Addressing modes` — immediate, direct, indirect, register, indexed, base-plus-offset, relative.

   5. `Instruction format` — the opcode field, the operand fields, and whether the length is fixed or variable.

   6. `Register organisation` — the number of general-purpose registers, and whether the machine is accumulator-based, stack-based or register-register.

   7. `Control unit design` — hardwired (fast, RISC) or microprogrammed (flexible, CISC).

   8. `Parallelism`
   ```
      Pipelining, superscalar issue, out-of-order execution
      SIMD vector instructions
      Multicore and multithreading
      Flynn's classification : SISD, SIMD, MISD, MIMD
   ```

   9. `I/O organisation` — programmed I/O, interrupt-driven I/O, DMA; memory-mapped or isolated I/O.

   10. `Performance metrics`
   ```
      CPU time = Instruction count x CPI x Clock cycle time
      MIPS, MFLOPS, SPEC benchmark scores
      Amdahl's law : the speed-up is limited by the serial fraction
   ```

   11. `Cost, power and reliability` — performance per watt matters as much as raw speed in mobile and data-centre design.

   The five stages of the DLX pipeline

   DLX is the teaching architecture of Hennessy and Patterson, and its five-stage pipeline is the classic model. MIPS uses the same arrangement.
   ```
      1. IF  - Instruction Fetch
           Fetch the instruction from memory using the PC, and increment the PC.

      2. ID  - Instruction Decode / Register Fetch
           Decode the opcode and read the source operands from the register
           file. The branch target address is also computed here.

      3. EX  - Execute / Effective Address Calculation
           The ALU performs the arithmetic or logic operation, or calculates
           the memory address for a load or store, or evaluates the branch
           condition.

      4. MEM - Memory Access
           Read from or write to data memory. Only LOAD and STORE use this
           stage; other instructions pass through it idle.

      5. WB  - Write Back
           Write the result into the destination register.
   ```
   ```
      I1 | IF | ID | EX |MEM | WB |
      I2      | IF | ID | EX |MEM | WB |
      I3           | IF | ID | EX |MEM | WB |
      I4                | IF | ID | EX |MEM | WB |
      I5                     | IF | ID | EX |MEM | WB |
                             ^ from here one instruction completes per cycle
   ```
   - Between the stages sit the `pipeline registers` IF/ID, ID/EX, EX/MEM and MEM/WB, which carry the instruction's data and control signals forward.
   - Ideal speed-up is 5; the hazards that reduce it are `structural`, `data` (solved by forwarding, or a stall after a load) and `control` (solved by branch prediction).

7. **“Pentium processor has a superscalar architecture.” Explain the meaning of statement.** *[Multiple Ministry Assistant Programmer 2017 compact it 1233 (ET: N/A)]*

   Answer: A `superscalar` processor can `issue and execute more than one instruction in the same clock cycle`, because it contains several parallel execution units. A plain pipelined processor completes at most one instruction per cycle; a superscalar one completes several.

   What the statement means for the Pentium
   - The original Pentium (1993) had `two integer pipelines`, called the `U pipe` and the `V pipe`, plus a separate floating-point unit.
   ```
      U pipe : the main pipeline - can execute any instruction
      V pipe : the secondary pipeline - can execute only simple instructions
   ```
   - When two consecutive instructions were compatible, the Pentium `paired` them and executed both in one cycle. This is why it was roughly twice as fast as the 486 at the same clock speed.
   ```
      Scalar pipeline (486)          Superscalar (Pentium)

      I1 | F | D | E | W |           I1 | F | D | E | W |     (U pipe)
      I2     | F | D | E | W |       I2 | F | D | E | W |     (V pipe)
      I3         | F | D | E | W |   I3     | F | D | E | W |
                                     I4     | F | D | E | W |

      1 instruction per cycle        2 instructions per cycle
   ```

   Conditions for pairing on the Pentium
   ```
      Both instructions must be SIMPLE (single-cycle, no microcode)
      Neither may be a jump, except as the second of the pair
      There must be NO DATA DEPENDENCY between them
      Neither may contain a prefix, except a few permitted cases
   ```
   - If the pair could not be issued together, the second instruction simply waited a cycle, so the processor never ran slower than a scalar one.

   Terms that go with it
   ```
      Scalar      : at most 1 instruction issued per cycle
      Superscalar : more than 1 instruction issued per cycle - SPATIAL parallelism
      Superpipelined : very deep pipeline, higher clock - TEMPORAL parallelism
      IPC (Instructions Per Cycle) : the measure of superscalar effectiveness
   ```
   ```
      Performance = clock frequency x IPC x number of cores
   ```
   - Superscalar design attacks the `IPC` term, while raising the clock attacks the frequency term. Since clock speeds stopped rising around 2005, IPC and core count are where all modern gains come from.

   What a superscalar processor needs
   - `Multiple execution units` — several ALUs, an FPU, load and store units.
   - `Wide instruction fetch and decode`, to supply several instructions per cycle.
   - `Dependency checking hardware`, to find which instructions may safely go together.
   - `Register renaming`, to remove false (WAR and WAW) dependencies.
   - `Out-of-order execution and a reorder buffer` in later designs, so an instruction waiting for data does not block the ones behind it.
   - `Branch prediction`, since a mispredicted branch now wastes several instructions per cycle rather than one.

   Limits
   - `Instruction-level parallelism` in ordinary code is limited — typically 4 to 8 independent instructions can be found, and beyond that the extra units sit idle.
   - The dependency-checking logic grows roughly as the square of the issue width, so it becomes expensive and power-hungry.
   - This diminishing return is precisely why the industry moved from ever-wider single cores to `multicore` processors.

   - Summary of the statement: saying the Pentium is superscalar means it has `more than one instruction pipeline` and can start two instructions in the same cycle, so its instructions-per-cycle can exceed 1 — the first x86 processor able to do so.

8. **Using pipeline calculate the value of fetch and execution cycle.** *[BTCL Assistant Manager (Technical) 2017 compact it 1255 (ET: N/A)]*

   Answer: The question gives no specific timings, so the standard pipeline formulas are derived and applied to a worked example. The method is what carries the marks.

   Non-pipelined (sequential) execution
   - Each instruction completes its fetch and execution before the next begins.
   ```
      Total time = n x (t(fetch) + t(execute))
   ```
   ```
      Example : n = 4 instructions , fetch = 1 cycle , execute = 1 cycle

      Total = 4 x (1 + 1) = 8 cycles

      I1 | F | E |
      I2         | F | E |
      I3                 | F | E |
      I4                         | F | E |
   ```

   Pipelined execution (2 stages: fetch and execute)
   - While one instruction is executing, the next is being fetched.
   ```
      Total time = (k + n - 1) x t(cycle)

      where k = number of stages , n = number of instructions
   ```
   ```
      Example : k = 2 , n = 4

      Total = (2 + 4 - 1) = 5 cycles

      I1 | F | E |
      I2     | F | E |
      I3         | F | E |
      I4             | F | E |
      cycle: 1   2   3   4   5
   ```

   Speed-up
   ```
      Speed-up = time without pipeline / time with pipeline

               = (n x k) / (k + n - 1)

      For this example = (4 x 2) / (2 + 4 - 1) = 8 / 5 = 1.6 times
   ```
   ```
      As n becomes large, speed-up -> k (the number of stages)
   ```

   The same with a five-stage pipeline
   ```
      Stages : IF , ID , EX , MEM , WB
      n = 1000 instructions

      Without pipeline : 1000 x 5 = 5,000 cycles
      With pipeline    : 5 + 1000 - 1 = 1,004 cycles

      Speed-up = 5000 / 1004 = 4.98 , close to the ideal 5
   ```

   Effect of unequal stage times
   ```
      Clock period = the SLOWEST stage + pipeline register delay

      IF 200 ps , ID 100 ps , EX 200 ps , MEM 200 ps , WB 100 ps
      -> clock period = 200 ps

      Non-pipelined instruction time = 800 ps
      Pipelined throughput           = one instruction per 200 ps
   ```

   Effect of stalls, which reduce the ideal figure
   ```
      Total cycles = k + n - 1 + (number of stall cycles)

      Effective CPI = 1 + stall cycles per instruction

      Speed-up = k / (1 + stalls per instruction)
   ```
   ```
      Example : 5 stages , 20 % of instructions cause a 1-cycle stall

      Effective CPI = 1 + 0.20 = 1.2
      Speed-up = 5 / 1.2 = 4.17  instead of the ideal 5
   ```

   Formulas to remember
   ```
      Non-pipelined time = n x k x t
      Pipelined time     = (k + n - 1) x t
      Speed-up           = (n x k) / (k + n - 1)
      Efficiency         = speed-up / k
      Throughput         = n / [(k + n - 1) x t]
   ```
   - Points worth stating: pipelining improves `throughput`, not the latency of any single instruction. The ideal speed-up equals the number of stages, and it is approached only when `n >> k` and there are no hazards. <!-- verify -->

9. **What is pipelining? What is opcode and operand in machine code? Explain snooping cache.** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 1277 (ET: N/A)]*

   Answer: What pipelining is
   - `Pipelining` divides the execution of an instruction into stages, and overlaps consecutive instructions so that a different instruction occupies each stage at the same time. One instruction then `completes` every clock cycle, even though each takes several cycles to pass through.
   ```
      Five-stage pipeline : IF -> ID -> EX -> MEM -> WB

      I1 | IF | ID | EX |MEM | WB |
      I2      | IF | ID | EX |MEM | WB |
      I3           | IF | ID | EX |MEM | WB |
                        ^ one instruction finishes every cycle from here
   ```
   ```
      Clock period    = the slowest STAGE, not the whole instruction
      Speed-up        = (n x k) / (k + n - 1)  ->  approaches k for large n
   ```
   - It improves `throughput`, not the latency of any single instruction. Its limits are the three hazards: `structural`, `data` (fixed by forwarding, else a stall) and `control` (fixed by branch prediction).

   Opcode and operand in machine code
   - A machine instruction is a binary pattern divided into fields. The two essential parts are the `opcode` and the `operand`.
   ```
      +----------------+---------------------------+
      |     OPCODE     |         OPERAND(S)        |
      +----------------+---------------------------+
         what to do            what to do it to
   ```

   `Opcode` (operation code)
   - The field that says `which operation` is to be performed — ADD, SUB, MOV, JMP, LOAD, STORE.
   - The control unit decodes it and generates the corresponding control signals.
   - Its width fixes how many distinct instructions exist: `n` bits allow 2^n opcodes.

   `Operand`
   - The field that says `what data` the operation works on. It may be:
   ```
      An immediate value  : the number itself is in the instruction
      A register name     : the data is in that register
      A memory address    : direct, indirect, indexed or base-plus-offset
   ```
   - An instruction may have zero, one, two or three operands.

   Example
   ```
      Assembly :  ADD  R1, R2

      Machine  :  0001 0001 0010
                  ^^^^ ^^^^ ^^^^
                  |    |    +-- operand 2 : register R2
                  |    +------- operand 1 : register R1
                  +------------ opcode    : ADD
   ```
   - The `addressing mode` field, where present, says how the operand field is to be interpreted.

   Snooping cache
   - `Cache snooping` is a hardware scheme that keeps the caches of several processors `coherent` — that is, it prevents two processors from holding different values for the same memory address.

   The problem it solves
   ```
      CPU1 and CPU2 both cache the block containing X = 5.
      CPU1 writes X = 10 into its own cache.
      CPU2 still reads 5 from its cache  ->  INCOHERENT.
   ```

   How snooping works
   - Every cache controller `watches` (snoops on) the shared bus and sees every transaction issued by every other cache. When a transaction affects a block it holds, it acts.
   ```
      WRITE-INVALIDATE  (the common scheme)
         When a processor writes a block, it broadcasts an INVALIDATE on the bus.
         Every other cache holding that block marks its copy INVALID.
         Their next read misses and fetches the new value.

      WRITE-UPDATE (write-broadcast)
         The new value itself is broadcast and every other cache updates its
         copy. Fewer misses, but far more bus traffic, so it is rarely used.
   ```
   - Implemented with the `MESI` protocol, in which each cache line carries one of four states:
   ```
      M (Modified)  : this cache has the only copy, and it has been changed
      E (Exclusive) : this cache has the only copy, unchanged
      S (Shared)    : several caches hold identical, unmodified copies
      I (Invalid)   : the copy is stale and must not be used
   ```

   Advantages and limits
   ```
      Advantages : simple, fast, no central directory needed
      Limits     : requires a BROADCAST medium, so it does not scale beyond
                   a few dozen processors
   ```
   - For larger systems, `directory-based` coherence is used instead: a directory records which caches hold each block, so invalidations are sent only to those caches as point-to-point messages rather than broadcast to all.

## Assembly Language & Addressing Modes (8)

1. (a) চয়ন করুন: (i) Propagation delay; (ii) Transmission delay;
   (b) SIMD instruction এর সংক্ষিপ্ত বর্ণনা লিখুন: MOV AX, A334H এবং MOV AX, [A334H] *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

   Answer: (a) Propagation delay and transmission delay

   `Propagation delay`
   - The time a bit takes to `travel` from the sender to the receiver along the medium. It depends on the `distance` and on the speed of the signal in that medium.
   ```
      Propagation delay = distance / propagation speed

      Speed : ~3 x 10^8 m/s in vacuum
              ~2 x 10^8 m/s in copper cable and optical fibre
   ```
   - Example: 2,000 km of fibre
   ```
      = 2,000,000 m / (2 x 10^8) = 0.01 s = 10 ms
   ```
   - It does `not` depend on how large the packet is.

   `Transmission delay`
   - The time the sender takes to `push all the bits` of the packet onto the link. It depends on the `packet size` and the `bandwidth`.
   ```
      Transmission delay = packet size / bandwidth
   ```
   - Example: a 1000-byte packet on a 1 Mbps link
   ```
      = 8000 bits / 1,000,000 bps = 0.008 s = 8 ms
   ```
   - It does `not` depend on the distance.

   | Point | Propagation delay | Transmission delay |
   |---|---|---|
   | Meaning | Time for a bit to travel the distance | Time to place all bits on the link |
   | Formula | distance / speed | packet size / bandwidth |
   | Depends on | Distance and medium | Packet size and bandwidth |
   | Independent of | Packet size and bandwidth | Distance |
   | Reduced by | A shorter path | A faster link or smaller packets |
   | Dominant in | Satellite and long-haul links | Low-bandwidth links |
   ```
      Total delay = transmission + propagation + queuing + processing
   ```

   (b) MOV AX, A534H versus MOV AX, [A534H]

   These two look almost identical but use `different addressing modes`, and the square brackets are the whole difference.

   `MOV AX, A534H` — immediate addressing
   ```
      The value A534H ITSELF is loaded into AX.

      AX  <-  A534H

      The operand is part of the instruction, so no memory access is needed
      beyond the instruction fetch. This is the FASTEST form.
   ```

   `MOV AX, [A534H]` — direct (memory) addressing
   ```
      A534H is an ADDRESS. The CONTENTS of that memory location are loaded.

      AX  <-  [DS:A534H]     the word stored at offset A534H in the data segment

      Two bytes are read, low byte first (little-endian) :
           AL <- byte at A534H
           AH <- byte at A535H
   ```

   Illustration
   ```
      Suppose the memory holds :

           Address   Content
           A534H      78H
           A535H      56H

      MOV AX, A534H     ->  AX = A534H     (the number itself)
      MOV AX, [A534H]   ->  AX = 5678H     (what is stored there)
   ```

   | Point | MOV AX, A534H | MOV AX, [A534H] |
   |---|---|---|
   | Addressing mode | Immediate | Direct |
   | A534H means | A constant value | A memory offset |
   | Loaded into AX | A534H | The contents of that location |
   | Memory access | None | One word read from the data segment |
   | Segment used | — | DS by default |
   | Speed | Fastest | Slower |
   | Written with brackets | No | `Yes` |

   - The `square brackets in 8086 assembly always mean "the contents of"`. Forgetting them is one of the most common beginner errors, because the instruction still assembles — it simply loads the wrong thing.

2. **Explain the difference between direct, immediate, and register addressing modes in the 8086 microprocessor.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1424 (ET: E-Zone)]*

   Answer: An `addressing mode` is the way an instruction specifies where its operand is. The 8086 has several; three of them are asked here.

   Immediate addressing
   - The operand is a `constant contained in the instruction itself`. No memory access is needed beyond fetching the instruction.
   ```asm
      MOV  AX, 1234H      ; AX <- 1234H  (the value itself)
      ADD  BL, 05H        ; BL <- BL + 5
      MOV  CX, 0FFH       ; CX <- 00FFH
   ```
   - Fastest of all modes, because the operand travels with the instruction. It can only be a source, never a destination — `MOV 1234H, AX` is meaningless.

   Register addressing
   - The operand is `in a CPU register`. Both source and destination may be registers.
   ```asm
      MOV  AX, BX         ; AX <- BX
      ADD  CL, DL         ; CL <- CL + DL
      MOV  DS, AX         ; segment register loaded from AX
   ```
   - The `fastest for repeated use`, because no memory access occurs at all. Both operands must be the same size — `MOV AX, BL` is illegal.

   Direct addressing
   - The instruction contains the `16-bit offset` of the memory location. The operand is the `contents` of that address, taken from the data segment by default.
   ```asm
      MOV  AX, [1234H]    ; AX <- the word stored at DS:1234H
      MOV  [5000H], BL    ; the byte at DS:5000H <- BL
      MOV  AX, TOTAL      ; TOTAL is a label, so this is direct addressing
   ```
   - The square brackets are what distinguish it from immediate addressing.
   ```
      Physical address = DS x 16 + offset
   ```
   - Slower, because it needs an extra memory cycle.

   Worked comparison
   ```
      Suppose memory holds :  address 1234H -> 78H , address 1235H -> 56H
                        and :  BX = 9999H

      MOV AX, 1234H      -> AX = 1234H      immediate : the number itself
      MOV AX, BX         -> AX = 9999H      register  : the register's contents
      MOV AX, [1234H]    -> AX = 5678H      direct    : the memory contents
   ```

   | Point | Immediate | Register | Direct |
   |---|---|---|---|
   | Operand is | A constant in the instruction | In a CPU register | In memory |
   | Memory access | None | None | One, in the data segment |
   | Speed | Fast | `Fastest` | Slowest of the three |
   | Instruction length | Longer (carries the constant) | Shortest | Longer (carries the address) |
   | Can be a destination | No | Yes | Yes |
   | Syntax | `MOV AX, 1234H` | `MOV AX, BX` | `MOV AX, [1234H]` |
   | Segment used | — | — | DS by default |

   The other 8086 addressing modes, for completeness
   ```
      Register indirect : MOV AX, [BX]            address held in BX, SI or DI
      Based             : MOV AX, [BX + 4]        base register plus displacement
      Indexed           : MOV AX, [SI + 4]        index register plus displacement
      Based indexed     : MOV AX, [BX + SI]       base plus index
      Based indexed with displacement : MOV AX, [BX + SI + 4]
      Implied           : CLC , STC               the operand is understood
      String            : MOVSB , LODSB           uses SI and DI automatically
   ```

3. **(খ) নিচের instruction দুটির মাঝে পার্থক্য লিখুন:** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*
MOV AX, A534H এবং MOV AX, [A534H]

   Answer: (Answered in English, as required for IT topics.) The two instructions differ only by the `square brackets`, and that changes the addressing mode completely.

   `MOV AX, A534H` — immediate addressing
   ```
      The value A534H ITSELF is loaded into AX.

      AX  <-  A534H

      The operand is part of the instruction, so no memory access is needed
      beyond the instruction fetch. This is the fastest form.
   ```

   `MOV AX, [A534H]` — direct (memory) addressing
   ```
      A534H is treated as an ADDRESS. The CONTENTS of that memory location
      are loaded into AX.

      AX  <-  [DS : A534H]

      Two bytes are read, low byte first (little-endian) :
           AL  <-  the byte at offset A534H
           AH  <-  the byte at offset A535H

      Physical address = DS x 16 + A534H
   ```

   Illustration
   ```
      Suppose the data segment contains :

           Offset    Content
           A534H       78H
           A535H       56H

      MOV AX, A534H     ->  AX = A534H     (the number itself)
      MOV AX, [A534H]   ->  AX = 5678H     (what is stored there)
   ```

   Difference

   | Point | MOV AX, A534H | MOV AX, [A534H] |
   |---|---|---|
   | Addressing mode | Immediate | Direct |
   | A534H means | A constant value | A memory offset |
   | Value placed in AX | A534H | The word stored at that address |
   | Memory accessed | No | Yes, one word read |
   | Segment register used | None | DS (by default) |
   | Machine cycles | Fewer | More |
   | Speed | Faster | Slower |
   | Square brackets | Absent | `Present` |
   | Result changes if memory changes | No | Yes |

   - The rule to remember: in 8086 assembly, `square brackets always mean "the contents of"`. Omitting them is a common and dangerous mistake, because the instruction still assembles correctly — it simply loads the wrong thing.
   - The default segment can be overridden if needed: `MOV AX, ES:[A534H]` reads from the extra segment instead of the data segment.

4. **(b) Explain the operations of the following instructions: (i) ADC (ii) CMP (iii) JBE** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 691 (ET: N/A)]*

   Answer: (i) ADC — Add with Carry
   ```
      Syntax  :  ADC destination, source

      Operation : destination <- destination + source + CF
   ```
   - It adds the source, the destination `and the carry flag`, then stores the result in the destination.
   - Purpose: adding numbers `larger than the register size`. A 32-bit addition on a 16-bit 8086 is done as a normal `ADD` on the low words followed by an `ADC` on the high words, so that the carry produced by the first addition is carried into the second.
   ```asm
      ; 32-bit addition : (DX:AX) = (DX:AX) + (CX:BX)
      ADD  AX, BX          ; add the LOW words, may generate a carry
      ADC  DX, CX          ; add the HIGH words PLUS that carry
   ```
   - Flags affected: `CF, PF, AF, ZF, SF, OF`.
   ```
      Example : AX = 0FFFFH , BX = 0001H , CF = 1
                ADC AX, BX  ->  AX = 0001H , CF = 1
   ```

   (ii) CMP — Compare
   ```
      Syntax  :  CMP destination, source

      Operation : destination - source     (the result is DISCARDED)
   ```
   - It performs a `subtraction purely to set the flags`. Neither operand is changed — this is what distinguishes it from `SUB`.
   - Purpose: to make a decision. `CMP` is almost always followed immediately by a conditional jump.
   ```
      After CMP A, B :

         ZF = 1                ->  A = B
         ZF = 0                ->  A is not equal to B
         CF = 1                ->  A < B   (unsigned)
         CF = 0 and ZF = 0     ->  A > B   (unsigned)
         SF <> OF              ->  A < B   (signed)
   ```
   ```asm
      CMP  AX, BX
      JE   equal_label        ; jump if AX = BX
      JA   above_label        ; jump if AX > BX (unsigned)
      JB   below_label        ; jump if AX < BX (unsigned)
   ```
   - Flags affected: `CF, PF, AF, ZF, SF, OF`. No register or memory location is modified.

   (iii) JBE — Jump if Below or Equal
   ```
      Syntax  :  JBE label          (same opcode as JNA - Jump if Not Above)

      Condition : jump if  CF = 1  OR  ZF = 1
   ```
   - It is an `unsigned` conditional jump, taken when the first operand of the preceding comparison was `less than or equal to` the second.
   ```
      CF = 1  ->  the destination was below the source
      ZF = 1  ->  they were equal
   ```
   ```asm
      CMP  AX, 10
      JBE  small_value        ; jump if AX <= 10  (unsigned)
   ```
   - It is a short jump, so the target must lie within -128 to +127 bytes of the next instruction.
   - Flags affected: `none`. A conditional jump reads the flags but does not change them.

   The signed and unsigned families, which are often confused
   ```
      UNSIGNED comparisons        SIGNED comparisons
      JA   / JNBE   above         JG   / JNLE   greater
      JAE  / JNB    above or equal JGE / JNL    greater or equal
      JB   / JNAE   below          JL  / JNGE   less
      JBE  / JNA    below or equal JLE / JNG    less or equal
   ```
   - Using `JBE` where `JLE` was needed, or the reverse, is a classic bug: with AX = -1 (FFFFH) and BX = 1, the unsigned comparison says AX is `above` BX, while the signed one says it is `below`.

   Summary

   | Instruction | Full name | Operation | Flags affected |
   |---|---|---|---|
   | `ADC` | Add with Carry | dest = dest + src + CF | All arithmetic flags |
   | `CMP` | Compare | dest - src, result discarded | All arithmetic flags |
   | `JBE` | Jump if Below or Equal | Jump if CF = 1 or ZF = 1 | None |

5. **Assembly Language Instructions এর ক্ষেত্রে নিম্মোক্ত Instructions গুলোর কাজ লিখুন। ADC, XCHG, POP ও JNZ.** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1041 (ET: DPI)]*

   Answer: (Answered in English, as required for IT topics.) ADC — Add with Carry
   ```
      Syntax    : ADC destination, source
      Operation : destination <- destination + source + CF
   ```
   - Adds the source, the destination `and the carry flag`, storing the result in the destination.
   - Purpose: adding numbers `wider than the register`. A 32-bit addition on the 16-bit 8086 uses `ADD` on the low words then `ADC` on the high words, so the carry from the first is included in the second.
   ```asm
      ; 32-bit addition : (DX:AX) = (DX:AX) + (CX:BX)
      ADD  AX, BX          ; low words, may generate a carry
      ADC  DX, CX          ; high words PLUS that carry
   ```
   - Flags affected: `CF, PF, AF, ZF, SF, OF`.

   XCHG — Exchange
   ```
      Syntax    : XCHG destination, source
      Operation : the two operands SWAP their contents
   ```
   - It exchanges the values without needing a temporary register, which would otherwise take three MOV instructions.
   ```asm
      XCHG  AX, BX         ; AX and BX swap contents
      XCHG  AL, AH         ; swap the two halves of AX
      XCHG  AX, [1234H]    ; swap AX with a memory word
   ```
   - Restrictions: both operands must be the same size, and both cannot be memory locations. Segment registers cannot be exchanged.
   - Flags affected: `none`.
   - Useful for byte-order reversal and for implementing a simple lock, since `XCHG` on the 8086 is atomic.

   POP — Pop from the stack
   ```
      Syntax    : POP destination
      Operation : destination <- [SS:SP]
                  SP <- SP + 2
   ```
   - Removes the word at the top of the stack and places it in the destination, then moves the stack pointer `up` by two bytes.
   ```asm
      POP  AX              ; AX <- top of stack, SP = SP + 2
      POP  DS              ; restore a segment register
      POPF                 ; restore the flag register
   ```
   - The 8086 stack grows `downward`: `PUSH` decrements SP, `POP` increments it. The stack is `LIFO`, so pops must mirror pushes in reverse order.
   ```asm
      PUSH AX
      PUSH BX
      ...
      POP  BX              ; note the REVERSE order
      POP  AX
   ```
   - Flags affected: `none`, except `POPF`, which restores all of them. `POP CS` is illegal, since it would break the instruction flow.

   JNZ — Jump if Not Zero
   ```
      Syntax    : JNZ label          (same opcode as JNE - Jump if Not Equal)
      Condition : jump if ZF = 0
   ```
   - Transfers control to the label when the previous operation produced a `non-zero` result, or when a comparison found the operands `unequal`.
   ```asm
      ; a countdown loop
      MOV  CX, 10
      again:
           ...              ; body of the loop
           DEC  CX          ; DEC sets ZF when CX reaches 0
           JNZ  again       ; repeat while CX is not zero

      ; a comparison
      CMP  AX, BX
      JNZ  not_equal        ; jump if AX <> BX
   ```
   - It is a short jump, so the target must lie within -128 to +127 bytes.
   - Flags affected: `none`. A conditional jump reads the flags but does not modify them.

   Summary

   | Instruction | Full name | Operation | Flags affected |
   |---|---|---|---|
   | `ADC` | Add with Carry | dest = dest + src + CF | All arithmetic flags |
   | `XCHG` | Exchange | The two operands swap | None |
   | `POP` | Pop from stack | dest = [SP], then SP = SP + 2 | None (except POPF) |
   | `JNZ` | Jump if Not Zero | Jump if ZF = 0 | None |

6. **Write down four common rules of Assembly language. Write different type of hazard.** *[Sonali & Janata Bank Officer (IT/ICT) 2019 compact it 1104 (ET: AUST)]*

   Answer: Four common rules of assembly language

   1. `One statement per line, in a fixed field format`
   ```
      [label:]   mnemonic   [operands]   [; comment]

      START:     MOV  AX, BX       ; copy BX into AX
   ```
   - The `label` is optional and marks the address; the `mnemonic` is the operation; the `operands` are what it acts on; anything after a `;` is a comment.

   2. `Operands must match in size and in type`
   ```
      MOV  AX, BX      ; legal   - both 16-bit
      MOV  AL, BL      ; legal   - both 8-bit
      MOV  AX, BL      ; ILLEGAL - size mismatch
   ```
   - Also, `both operands cannot be memory locations` — one must be a register. `MOV [1000H], [2000H]` is illegal, and must be done in two steps through a register.
   - An immediate value cannot be the destination: `MOV 1234H, AX` is meaningless.

   3. `Every program must define its segments and end properly`
   ```asm
      .MODEL SMALL
      .STACK 100H
      .DATA
           MSG  DB  'Hello$'
      .CODE
      MAIN PROC
           MOV  AX, @DATA
           MOV  DS, AX          ; DS must be initialised by the program
           ...
           MOV  AH, 4CH
           INT  21H             ; return to DOS
      MAIN ENDP
      END  MAIN                 ; END directive marks the entry point
   ```
   - Segment registers are not set automatically; the program must load `DS` itself.

   4. `Names, numbers and comments follow strict rules`
   ```
      Labels  : begin with a letter or _ ; letters, digits, _ , $ , ? allowed
                not a reserved word (AX, MOV, ADD are reserved)
                usually up to 31 characters, and case-insensitive

      Numbers : must BEGIN WITH A DIGIT
                1234H  legal        A534H  ILLEGAL -> write 0A534H
                suffix H = hex, B = binary, D or none = decimal, O/Q = octal

      Strings : enclosed in single or double quotes -> 'Hello'
      Comments: everything after a semicolon on the line
   ```

   Other rules worth knowing
   ```
      Square brackets mean "the contents of" : MOV AX,[BX] is not MOV AX,BX
      Directives (DB, DW, EQU, .DATA) are instructions to the ASSEMBLER,
          not to the CPU, and generate no machine code themselves
      Labels must be unique within a module
   ```

   Types of hazard in a pipeline

   A `hazard` is a situation in which the next instruction cannot execute in the following clock cycle. There are three kinds.

   1. `Structural hazard` (resource hazard)
   - Two instructions need the `same hardware unit` in the same cycle.
   ```
      I1 is in MEM, reading data from memory
      I4 is in IF, fetching an instruction from the same memory
      -> a single-ported memory cannot serve both
   ```
   - Solved by `duplicating the resource` — separate instruction and data caches (the Harvard arrangement), or a multi-ported register file.

   2. `Data hazard`
   - An instruction needs a value that an earlier instruction has computed but not yet written back.
   ```asm
      ADD  R1, R2, R3      ; R1 written back in cycle 5
      SUB  R4, R1, R5      ; needs R1 in cycle 4 - too early
   ```
   ```
      RAW (Read After Write)  : the true dependency, shown above
      WAR (Write After Read)  : only with out-of-order execution
      WAW (Write After Write) : only with out-of-order execution
   ```
   - Solved by `forwarding` (routing the ALU result straight to the next instruction's input), by `stalling` one cycle when a load is immediately used, and by compiler scheduling.

   3. `Control hazard` (branch hazard)
   - A branch is not resolved until the EX stage, so the instructions already fetched behind it may be the wrong ones.
   ```
      BEQ  R1, R2, TARGET
      ---- which instruction should be fetched next? Not known yet ----
   ```
   - Solved by `branch prediction` (static or dynamic, with a branch history table), `delayed branching` (the compiler fills the slot with a useful instruction), and `speculative execution`, with a pipeline flush when the prediction turns out wrong.

   | Hazard | Cause | Solution |
   |---|---|---|
   | Structural | Two stages want the same unit | Duplicate the resource, separate caches |
   | Data | A result is not ready yet | Forwarding, stalling, compiler scheduling |
   | Control | The branch outcome is unknown | Branch prediction, delayed branch, flush |

7. **Describe addressing mode of 8086 microprocessors.** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1225-1226 (ET: N/A)]*

   Answer: An `addressing mode` is the way an instruction specifies where its operand is. The 8086 supports the following modes.

   1. Immediate addressing
   - The operand is a `constant carried inside the instruction`.
   ```asm
      MOV  AX, 1234H       ; AX <- 1234H
      ADD  BL, 05H         ; BL <- BL + 5
   ```
   - Fastest, since no memory access is needed. It can only be a source, never a destination.

   2. Register addressing
   - The operand is `in a CPU register`.
   ```asm
      MOV  AX, BX          ; AX <- BX
      ADD  CL, DL
   ```
   - Fastest for repeated use — no memory cycle at all. Both operands must be the same size.

   3. Direct addressing
   - The instruction carries the `16-bit offset` of the memory location.
   ```asm
      MOV  AX, [1234H]     ; AX <- the word at DS:1234H
      MOV  TOTAL, BL       ; TOTAL is a label, so this is direct
   ```
   ```
      Physical address = DS x 16 + offset
   ```

   4. Register indirect addressing
   - The `offset is held in a register` — BX, SI, DI or BP.
   ```asm
      MOV  AX, [BX]        ; AX <- the word at DS:BX
      MOV  AX, [SI]
      MOV  AX, [BP]        ; NOTE: BP uses the STACK segment SS by default
   ```
   - Essential for arrays and pointers, since the register can be incremented in a loop.

   5. Based addressing
   - A `base register (BX or BP) plus a displacement`.
   ```asm
      MOV  AX, [BX + 4]
      MOV  AX, [BP + 6]    ; typical way to reach a parameter on the stack
   ```
   - Used for accessing fields of a record or structure.

   6. Indexed addressing
   - An `index register (SI or DI) plus a displacement`.
   ```asm
      MOV  AX, [SI + 4]
      MOV  AX, ARRAY[DI]
   ```
   - Used for stepping through an array: the displacement gives the array's start, the index gives the element.

   7. Based indexed addressing
   - A `base register plus an index register`.
   ```asm
      MOV  AX, [BX + SI]
      MOV  AX, [BP + DI]
   ```
   - Used for two-dimensional arrays: the base holds the row, the index the column.

   8. Based indexed with displacement
   - All three components together.
   ```asm
      MOV  AX, [BX + SI + 4]
      MOV  AX, ARRAY[BX][SI]
   ```
   - The most general form, used for arrays of records.

   9. Implied (implicit) addressing
   - The operand is `understood from the opcode` and is not written at all.
   ```asm
      CLC                  ; clear the carry flag
      STC , CLD , STD , NOP , CBW
   ```

   10. String addressing
   - The 8086 string instructions use `SI` and `DI` automatically, with `DS:SI` as the source and `ES:DI` as the destination, and increment or decrement them according to the direction flag.
   ```asm
      MOVSB , MOVSW        ; move a byte or word
      LODSB , STOSB , CMPSB , SCASB
   ```

   Default segment registers
   ```
      Offset in BX, SI, DI        ->  DS
      Offset in BP or SP          ->  SS
      Destination of a string op  ->  ES
      Instruction fetch           ->  CS

      Any of these may be overridden : MOV AX, ES:[BX]
   ```

   Summary

   | Mode | Example | Operand is |
   |---|---|---|
   | Immediate | `MOV AX, 1234H` | A constant in the instruction |
   | Register | `MOV AX, BX` | In a register |
   | Direct | `MOV AX, [1234H]` | In memory, address in the instruction |
   | Register indirect | `MOV AX, [BX]` | In memory, address in a register |
   | Based | `MOV AX, [BX+4]` | Base register + displacement |
   | Indexed | `MOV AX, [SI+4]` | Index register + displacement |
   | Based indexed | `MOV AX, [BX+SI]` | Base + index |
   | Based indexed + disp | `MOV AX, [BX+SI+4]` | Base + index + displacement |
   | Implied | `CLC` | Understood from the opcode |
   | String | `MOVSB` | DS:SI and ES:DI, automatically |

   - Why so many modes exist: each maps naturally onto a programming construct — immediate for constants, register indirect for pointers, indexed for arrays, based for record fields, based indexed for two-dimensional arrays. This richness is characteristic of a `CISC` design; RISC machines typically offer only two or three.

8. **Explain the instructions LDS, PUSHF, TEST and CLD.** *[Multiple Ministry Assistant Programmer 2017 compact it 1235 (ET: N/A)]*

   Answer: LDS — Load pointer using DS
   ```
      Syntax    : LDS destination, source

      Operation : destination <- [source]        the low word  (the offset)
                  DS          <- [source + 2]    the high word (the segment)
   ```
   - It loads a `32-bit far pointer` from memory in one instruction: the offset into the named register and the segment into `DS`.
   ```asm
      LDS  SI, POINTER     ; SI <- the word at POINTER
                           ; DS <- the word at POINTER+2
                           ; now DS:SI addresses the target data
   ```
   - Purpose: setting up access to data in another segment, typically when a far pointer has been passed to a procedure.
   - The companion instruction `LES` does the same but loads `ES` instead of DS, which is what string destinations need.
   - Flags affected: `none`.

   PUSHF — Push flags onto the stack
   ```
      Operation : SP <- SP - 2
                  [SS:SP] <- the 16-bit flag register
   ```
   - Saves the entire flag register — CF, PF, AF, ZF, SF, TF, IF, DF, OF — onto the stack.
   ```asm
      PUSHF                ; save the flags
      ...                  ; code that alters the flags
      POPF                 ; restore them exactly as they were
   ```
   - Purpose: preserving the processor state at the start of an interrupt service routine or a procedure, so the interrupted code resumes with its flags intact.
   - It is also the only way to `modify the trap flag`, since no instruction sets TF directly:
   ```asm
      PUSHF
      POP  AX
      OR   AX, 0100H       ; set bit 8 = TF, enabling single-step mode
      PUSH AX
      POPF
   ```
   - Flags affected: `none` by PUSHF itself; `POPF` restores all of them.

   TEST — Logical compare
   ```
      Syntax    : TEST destination, source

      Operation : destination AND source     (the result is DISCARDED)
   ```
   - Performs a bitwise AND `purely to set the flags`. Neither operand is changed — this is exactly what distinguishes it from `AND`.
   - Purpose: checking whether particular `bits` are set, without disturbing the data.
   ```asm
      TEST AL, 01H
      JNZ  odd_number      ; bit 0 set -> the value is odd

      TEST AL, 80H
      JNZ  negative        ; bit 7 set -> sign bit is 1

      TEST AX, AX
      JZ   is_zero         ; a fast way to test AX for zero
   ```
   - Flags affected: `SF, ZF, PF` are set from the result; `CF and OF are cleared`; AF is undefined.
   - `TEST` is to `AND` exactly what `CMP` is to `SUB`: the operation is performed only for its effect on the flags.

   CLD — Clear Direction flag
   ```
      Operation : DF <- 0
   ```
   - Sets the direction of the `string instructions` to `forward`: after each operation, `SI` and `DI` are `auto-incremented`.
   ```asm
      CLD                  ; forward direction
      MOV  CX, 100
      REP  MOVSB           ; copy 100 bytes from DS:SI to ES:DI, moving forward
   ```
   - Its counterpart `STD` sets DF = 1, making the string instructions move `backward` by auto-decrementing SI and DI.
   - Why the backward direction exists: when copying `overlapping` memory blocks, copying forward would overwrite bytes that have not yet been read, so the copy must be made from the end.
   - Flags affected: only `DF`.

   Summary

   | Instruction | Full name | Operation | Flags affected |
   |---|---|---|---|
   | `LDS` | Load pointer using DS | reg <- [src], DS <- [src+2] | None |
   | `PUSHF` | Push flags | Push the flag register onto the stack | None |
   | `TEST` | Logical compare | dest AND src, result discarded | SF, ZF, PF set; CF, OF cleared |
   | `CLD` | Clear direction flag | DF <- 0, string ops go forward | DF only |

## CPU Performance & Instruction Cycle (6)

1. **There was a CPU cycle math** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 400 (ET: BUET)]*

2. **(খ) Clock cycle কী? একটি মাইক্রো-প্রসেসরের speed 3.5 GHz বলতে কী বোঝায়?** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

   Answer: (Answered in English, as required for IT topics.) Clock cycle
   - A `clock cycle` is one complete oscillation of the processor's clock signal — one tick of the square wave that synchronises everything inside the CPU.
   ```
      CLK   __|‾‾|__|‾‾|__|‾‾|__
              |<-->|
              one clock cycle (one period, T)
   ```
   - Every action in the processor happens at a clock edge: a register latches, a pipeline stage advances, a flag is set. The clock is what keeps every part of the machine in step.
   ```
      Clock cycle time (period)  T = 1 / f
      Clock frequency            f = 1 / T
   ```
   - One instruction usually needs several cycles. `CPI` (cycles per instruction) measures how many.
   ```
      CPU time = Instruction count x CPI x Clock cycle time
   ```

   What "3.5 GHz" means
   ```
      1 Hz  = 1 cycle per second
      1 GHz = 1,000,000,000 cycles per second

      3.5 GHz = 3,500,000,000 clock cycles per second
   ```
   - The time for one cycle is therefore
   ```
      T = 1 / (3.5 x 10^9)
        = 0.2857 x 10^-9 s
        = 0.2857 nanoseconds
        = 285.7 picoseconds
   ```
   - So the processor advances one step every 0.286 nanoseconds — three and a half thousand million steps every second.

   What it does `not` mean
   - It does `not` mean 3.5 billion instructions per second. Some instructions need several cycles, while a superscalar processor completes several instructions per cycle. Real throughput is:
   ```
      Performance = clock frequency x IPC x number of cores
   ```
   - Comparing two processors by clock speed alone is only valid when they share the same architecture. A 2.5 GHz modern chip easily beats a 3.5 GHz chip of ten years ago, because it does far more work per cycle.
   - Modern processors quote a `base` clock and a higher `turbo` clock, reached only while thermal and power headroom allows. Under sustained load the chip may `throttle` back to protect itself.

   Worked example
   ```
      Program : 2 billion instructions , average CPI = 2 , clock 3.5 GHz

      Total cycles = 2 x 10^9 x 2 = 4 x 10^9
      Execution time = 4 x 10^9 / 3.5 x 10^9 = 1.14 seconds
   ```

   - Summary: `3.5 GHz` states how fast the processor's internal metronome ticks. It sets the upper limit on how quickly work can be done, but the actual speed also depends on `IPC`, the number of cores, the cache and the memory system.

3. **A program (or a program task) takes 1 billion instructions to execute on a processor running at 2 GHz. Suppose also that 50% of the instructions execute in 3 clock cycles, 30% execute in 4 clock cycles, and 20% execute in 5 clock cycles. What is the execution time for the program or task?** *[RAKUB Programmer (PO) 12.10.2021 compact it 847 (ET: N/A)]*

   Answer: The standard CPU performance equation is
   ```
      CPU time = Instruction count x CPI x Clock cycle time

               = (Instruction count x CPI) / Clock frequency
   ```

   Given
   ```
      Instruction count = 1 billion = 1 x 10^9
      Clock frequency   = 2 GHz     = 2 x 10^9 Hz

      50 % of instructions take 3 clock cycles
      30 % of instructions take 4 clock cycles
      20 % of instructions take 5 clock cycles
   ```

   Step 1 — average CPI (cycles per instruction)
   ```
      CPI = sum of (fraction x cycles)

          = (0.50 x 3) + (0.30 x 4) + (0.20 x 5)

          = 1.5 + 1.2 + 1.0

      CPI = 3.7 cycles per instruction
   ```

   Step 2 — total clock cycles needed
   ```
      Total cycles = Instruction count x CPI

                   = 1 x 10^9 x 3.7

                   = 3.7 x 10^9 cycles
   ```

   Step 3 — clock cycle time
   ```
      T = 1 / f = 1 / (2 x 10^9) = 0.5 x 10^-9 s = 0.5 nanoseconds
   ```

   Step 4 — execution time
   ```
      Execution time = total cycles x clock cycle time

                     = 3.7 x 10^9 x 0.5 x 10^-9

                     = 1.85 seconds
   ```
   ```
      Answer : 1.85 seconds
   ```

   Check by the direct formula
   ```
      Execution time = (Instruction count x CPI) / frequency

                     = (1 x 10^9 x 3.7) / (2 x 10^9)

                     = 3.7 / 2 = 1.85 s        correct
   ```

   Breakdown by instruction class, as a further check
   ```
      Class      Count            Cycles each   Total cycles
      ---------  ---------------  -----------   ---------------
      50 %       0.5 x 10^9            3        1.5 x 10^9
      30 %       0.3 x 10^9            4        1.2 x 10^9
      20 %       0.2 x 10^9            5        1.0 x 10^9
      ------------------------------------------------------
      Total      1.0 x 10^9                     3.7 x 10^9
   ```

   Related figures
   ```
      MIPS = Instruction count / (execution time x 10^6)
           = 1 x 10^9 / (1.85 x 10^6)
           = 540.5 MIPS

      Effective rate = frequency / CPI = 2 x 10^9 / 3.7 = 540.5 million
                       instructions per second        (the same figure)
   ```

   - Point worth stating: the three terms of the performance equation are influenced by different things. `Instruction count` depends on the compiler and the ISA, `CPI` on the microarchitecture and the memory system, and `clock cycle time` on the circuit technology. Improving any one of them improves performance, and a real design must attend to all three.

4. **Operating system math: clock frequency 700MHz.** *[RAKUB Programmer (PO) 12.10.2021 compact it 852 (ET: N/A)]*

5. **Computer A has 3.2GHz processing speed and it has 2.0 clock speeds in a program and at the same program Computer B has 2.4 GHz processing speed with 1.2 clock speed. Which computer will run faster and how much faster?** *[DESCO Assistant Engineer (CSE) 2019 compact it 1118-1119 (ET: BUET)]*

   Answer: Speed is judged by the `time taken per instruction`, not by clock frequency alone. The performance equation is
   ```
      CPU time per instruction = CPI / clock frequency
   ```
   - Here "clock speeds in a program" means the average `CPI` — cycles per instruction.

   Given
   ```
      Computer A : frequency = 3.2 GHz , CPI = 2.0
      Computer B : frequency = 2.4 GHz , CPI = 1.2
   ```

   Step 1 — clock cycle time of each machine
   ```
      Computer A : T = 1 / (3.2 x 10^9) = 0.3125 ns
      Computer B : T = 1 / (2.4 x 10^9) = 0.4167 ns
   ```

   Step 2 — time per instruction
   ```
      Computer A : 2.0 x 0.3125 ns = 0.625 ns per instruction

      Computer B : 1.2 x 0.4167 ns = 0.500 ns per instruction
   ```

   Step 3 — compare
   ```
      Computer B takes LESS time per instruction, so COMPUTER B IS FASTER.

      How much faster = time(A) / time(B)

                      = 0.625 / 0.500

                      = 1.25
   ```
   ```
      Answer : Computer B is faster, by a factor of 1.25 - that is, 25 % faster.
   ```

   Alternative working, for the same n instructions
   ```
      Let the program contain n instructions.

      Time on A = (n x CPI_A) / f_A = (n x 2.0) / 3.2 x 10^9 = n x 0.625 ns
      Time on B = (n x CPI_B) / f_B = (n x 1.2) / 2.4 x 10^9 = n x 0.500 ns

      Ratio = 0.625 n / 0.500 n = 1.25        same result
   ```

   Instruction throughput, another way to state it
   ```
      Computer A : 3.2 x 10^9 / 2.0 = 1,600 million instructions per second
      Computer B : 2.4 x 10^9 / 1.2 = 2,000 million instructions per second

      2000 / 1600 = 1.25        Computer B again 1.25 times faster
   ```

   - The lesson this question teaches: `clock speed alone does not decide performance`. Computer A has a 33 per cent higher clock but is 25 per cent slower, because its CPI is worse. Real speed is `frequency divided by CPI`, and modern architectures compete mainly on lowering CPI — better pipelines, branch prediction, superscalar issue and larger caches — rather than on raising the clock, which stopped improving significantly after about 2005.

6. **Write down factor of microprocessor speed?** *[BREB Assistant Hardware & Network Engineer 2019 compact it 1124-1125 (ET: BREB)]*

   Answer: The speed of a microprocessor is decided by several factors acting together, not by clock frequency alone.
   ```
      Performance = Clock frequency x IPC x Number of cores
   ```

   1. Clock speed (frequency)
   - The number of cycles per second, in GHz. A 3 GHz processor ticks three thousand million times a second, one tick every 0.33 ns.
   - It sets the upper limit, but is only meaningful when comparing processors of the `same architecture`.

   2. Instructions per cycle (IPC) and microarchitecture
   - How much work is completed per tick. Better pipelines, wider superscalar issue, out-of-order execution and good branch prediction all raise IPC. This is where nearly all modern gains come from.
   ```
      CPU time = Instruction count x CPI x Clock cycle time
   ```

   3. Number of cores and threads
   - More cores run more tasks genuinely simultaneously; hyper-threading lets one core run two threads and keeps its units busy.
   - Limited by `Amdahl's law` — the serial part of a program does not speed up however many cores are added.

   4. Cache memory
   - The most important single factor after the architecture itself.
   ```
      L1 : 32-64 KB   ~4 cycles
      L2 : 256KB-1MB  ~12 cycles
      L3 : 8-32 MB    ~40 cycles
      RAM: gigabytes  ~200 cycles
   ```
   - A larger, better-organised cache raises the hit ratio, and a five-point change in hit ratio can change real performance by 50 per cent.

   5. Word size (bus width)
   - A 64-bit processor moves 64 bits per operation and addresses far more memory than a 32-bit one.

   6. Pipelining and superscalar design
   - Pipelining overlaps stages so an instruction completes every cycle; superscalar issue completes several. `Hazards` — data dependencies and branch mispredictions — stall the pipeline and cost cycles.

   7. Memory and bus speed
   - The RAM type (DDR4 or DDR5), its latency, and the memory controller's bandwidth. A fast processor starved of data simply waits.

   8. Instruction set architecture
   - RISC instructions pipeline cleanly; CISC packs more work into each instruction. Special instruction sets — SSE, AVX, AES-NI — accelerate particular tasks enormously.

   9. Manufacturing process
   - A smaller process (7 nm, 5 nm, 3 nm) places transistors closer together, so they switch faster and use less power, allowing a higher clock at the same heat.

   10. Thermal design and power
   - If the chip overheats it `throttles`, dropping its clock to protect itself. Cooling therefore affects sustained speed directly, and `turbo boost` lasts only while thermal headroom remains.

   11. Software factors
   - A well-optimised, multi-threaded, compiler-optimised program uses the hardware far better than a poorly written one. Background processes steal cycles.

   - Summary: clock speed is only one term of three. `Speed = clock x IPC x cores`, and all of it is bounded by how quickly the cache and memory can feed the processor.

## Multi-Core & Multi-Threading (5)

1. **Core vs thread in networking?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

   Answer: `Core` and `thread` are processor terms rather than networking ones, though the same words appear in networking with different meanings. Both senses are given.

   In a processor

   `Core`
   - A `physical` independent processing unit inside the CPU chip. Each core has its own ALU, control unit, registers and L1 cache, and can execute a program entirely on its own.
   - A quad-core processor genuinely runs four programs at the same instant.

   `Thread`
   - A `logical` stream of instructions — the smallest unit the operating system schedules. With `hyper-threading` (SMT), one physical core presents itself as two logical processors and interleaves two threads, keeping its execution units busy while one thread waits for memory.
   ```
      4 cores , 8 threads

      Core 1 : Thread 1 , Thread 2
      Core 2 : Thread 3 , Thread 4
      Core 3 : Thread 5 , Thread 6
      Core 4 : Thread 7 , Thread 8
   ```
   - Hyper-threading adds roughly `20-30 per cent` performance, not 100 per cent, because the two threads share one core's actual hardware.

   | Point | Core | Thread |
   |---|---|---|
   | Nature | Physical hardware | Logical execution stream |
   | Own ALU and registers | Yes | No — shares the core's |
   | True parallelism | Yes | Interleaved on one core |
   | Set by | The chip design | The OS and the SMT feature |
   | Performance gain | Nearly linear with count | About 20-30 % per core |

   In networking, where the same words are used differently

   `Core` — the `core network` or `core layer`
   ```
      Access layer       : where users connect (switches, access points)
      Distribution layer : routing and policy between access and core
      Core layer         : the high-speed backbone that switches traffic
                           between distribution blocks as fast as possible
   ```
   - The core layer's job is `speed and reliability only`. No access lists, no filtering, no policy — anything that adds latency is pushed down to the distribution layer. It is built with redundant high-capacity links.
   - `Core router` and `core switch` mean the devices in that layer, and a `core network` is the operator's backbone that carries aggregated traffic between regions.

   `Thread` — two meanings in networking
   ```
      1. Thread (capital T) : an IEEE 802.15.4-based low-power mesh
         networking protocol for IoT devices, using IPv6 with 6LoWPAN.
         Self-healing, no single point of failure, used in smart homes.

      2. Threads in server software : a web server or a router's control
         plane creates one thread per connection or per queue, so that many
         sessions are handled concurrently.
   ```

   - Which meaning the question wants depends on context. In a hardware or CPU question, `core versus thread` means physical versus logical processors. In a network design question, `core` means the backbone layer.

2. **Core i5 and i7 Microprocessor এর মধ্যে হার্ডওয়্যারগত মূল পার্থক্য কী?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 698 (ET: DPI)]*

   Answer: (Answered in English, as required for IT topics.) The `i5` and `i7` labels denote performance tiers within one generation. The hardware differences are these.

   1. Number of cores and threads
   ```
      Core i5 : typically 6 cores , 12 threads
      Core i7 : typically 8 or more cores , 16 or more threads
   ```
   - More cores means more genuinely parallel work — the largest single difference in heavy multi-threaded tasks such as video encoding, compilation and virtualisation.

   2. Hyper-threading
   - On many generations the `i5 lacks hyper-threading` while the `i7 has it`, so an i7 presents twice as many logical processors as physical cores.
   - Hyper-threading adds roughly `20-30 per cent`, by keeping a core's execution units busy while one thread waits for memory.

   3. Cache size
   ```
      Core i5 : 9-12 MB of L3 cache
      Core i7 : 12-25 MB of L3 cache
   ```
   - A larger L3 raises the hit ratio, and since a main-memory access costs about 200 cycles against 40 for L3, this affects real performance considerably.

   4. Clock speed and Turbo Boost
   - The i7 usually has a higher base clock and a higher maximum turbo frequency, and it holds turbo for longer because of its larger power budget.

   5. Thermal design power and cooling
   ```
      Core i5 : 65 W typical
      Core i7 : 95-125 W typical
   ```
   - The higher TDP is what allows the extra cores and the higher sustained clocks, but it demands better cooling.

   6. Integrated graphics
   - Both usually have integrated graphics, but the i7's version often has more execution units and a higher graphics clock.

   7. Overclocking and platform features
   - The unlocked `K` variants are more common in the i7 line, and i7 chips more often support features such as more PCIe lanes.

   Summary

   | Point | Core i5 | Core i7 |
   |---|---|---|
   | Cores | 6 typically | 8 or more |
   | Threads | 6-12 | 16 or more |
   | Hyper-threading | Often absent | Usually present |
   | L3 cache | 9-12 MB | 12-25 MB |
   | Base clock | Lower | Higher |
   | Turbo Boost | Yes, lower ceiling | Yes, higher ceiling |
   | TDP | ~65 W | 95-125 W |
   | Price | Moderate | High |
   | Suited to | Everyday use, gaming | Video editing, CAD, development, virtualisation |

   - Two important warnings. First, the tier number is `not a generation`: a newer i5 usually beats an older i7, so the generation code — the leading digits of the model number, as in `i5-13600K` — matters more than the tier. Second, the exact figures above vary by generation; the `principle` is constant — i7 means more cores, more threads, more cache and a higher clock, at higher power and price.

3. **What is Hyper threading? What is the use of it?** *[BOF Assistant Programmer 2022 compact it 733 (ET: MIST)]*

   Answer: What hyper-threading is
   - `Hyper-Threading Technology (HTT)` is Intel's implementation of `Simultaneous Multithreading (SMT)`. One `physical` core presents itself to the operating system as `two logical processors`, so it can hold and interleave two threads at once.
   - It works by duplicating only the `architectural state` — the registers, the program counter and the control registers — while the two threads `share` the core's real execution hardware: the ALUs, the FPU, the caches and the branch predictor.
   ```
      +-------------------------------------------+
      |            One physical core              |
      |                                           |
      |  Thread 1 state      Thread 2 state       |  <- duplicated
      |  (registers, PC)     (registers, PC)      |
      |            \           /                  |
      |          Shared execution units           |  <- NOT duplicated
      |          (ALU, FPU, cache, scheduler)     |
      +-------------------------------------------+
   ```
   ```
      4 physical cores , hyper-threading enabled  ->  8 logical processors
      Windows Task Manager then shows "4 cores, 8 logical processors"
   ```

   Why it helps
   - A single thread frequently `stalls` — waiting for a cache miss, a branch misprediction or a long-latency instruction. During those cycles the core's execution units sit idle.
   - With two threads resident, the core simply issues instructions from the `other` thread while the first is stalled. The idle slots are filled.
   ```
      Without HT : | T1 | T1 | stall | stall | T1 |
      With HT    : | T1 | T1 |  T2   |  T2   | T1 |     -> units stay busy
   ```

   Uses and benefits
   - `Higher throughput` on multi-threaded work — typically `20-30 per cent`, not 100 per cent, because the two threads share one core's real hardware.
   - `Better responsiveness` when many programs run at once: browsing while a file compresses in the background.
   - `Server workloads` benefit most — web servers, database servers and virtualisation hosts, where many independent requests arrive and each stalls often on memory or I/O.
   - `Content creation` — video encoding, 3D rendering and compilation are all highly parallel.
   - `Cost efficiency`: extra performance from a modest amount of extra silicon, far cheaper than adding real cores.

   Limitations
   - It is `not` the same as doubling the cores. Two threads compete for one set of ALUs and one cache, so a single heavily compute-bound thread gains nothing.
   - `Cache contention` can make some workloads slightly `slower` with HT enabled.
   - Single-threaded programs see no benefit at all.
   - It raises power and heat.
   - `Security`: side-channel attacks such as `Spectre`, `Foreshadow` and `PortSmash` exploit the fact that two threads share a core. Some cloud providers and security-sensitive sites disable SMT for this reason.

   Comparison

   | Point | Physical core | Logical (hyper-)thread |
   |---|---|---|
   | Nature | Real hardware | Duplicated register state only |
   | Execution units | Its own | Shared with the sibling thread |
   | Performance gain | Nearly linear | About 20-30 % |
   | True parallelism | Yes | Interleaved on one core |
   | Cost in silicon | High | Small |

   - Terminology note: `Hyper-Threading` is Intel's brand name. AMD's equivalent is simply called `SMT`, and both implement the same idea. A processor described as "8 cores, 16 threads" has 8 physical cores each running 2 threads.

4. **Now a day, core i3, i5, i7 and i9 CPUs are aavailable. The higher the number is that means powerful processor. What is hyper threading? What does 2 core and 4 thread means?** *[BTRC Assistant Director (Technical) 2021 compact it 808 (ET: IBA)]*

   Answer: What hyper-threading is
   - `Hyper-Threading (HTT)` is Intel's implementation of `Simultaneous Multithreading (SMT)`. One `physical` core presents itself to the operating system as `two logical processors`, so it can hold and interleave two threads at once.
   - Only the `architectural state` is duplicated — the registers, the program counter and the control registers. The two threads `share` the real hardware: the ALUs, the FPU, the caches and the branch predictor.
   ```
      +-------------------------------------------+
      |            One physical core              |
      |   Thread 1 state       Thread 2 state     |  <- duplicated
      |            \             /                |
      |         Shared execution units            |  <- NOT duplicated
      |         (ALU, FPU, cache, scheduler)      |
      +-------------------------------------------+
   ```
   - Why it helps: a single thread frequently stalls waiting for a cache miss or a mispredicted branch, leaving the execution units idle. With two threads resident, the core issues instructions from the other thread and fills those idle slots.
   ```
      Without HT : | T1 | T1 | stall | stall | T1 |
      With HT    : | T1 | T1 |  T2   |  T2   | T1 |
   ```
   - Gain: typically `20-30 per cent` on multi-threaded work, `not` 100 per cent, because the two threads share one core's real hardware.

   What "2 cores and 4 threads" means
   ```
      2 CORES   : two PHYSICAL processing units on the chip. Each has its own
                  ALU, control unit, registers and L1 cache, and can execute a
                  program completely independently. These give TRUE parallelism.

      4 THREADS : four LOGICAL processors that the operating system can
                  schedule work onto. Since there are only 2 physical cores,
                  hyper-threading is enabled and each core carries 2 threads.
   ```
   ```
      Core 1 : Thread 1 , Thread 2
      Core 2 : Thread 3 , Thread 4

      The OS sees 4 processors and schedules 4 tasks.
      The chip really has 2 sets of execution hardware.
   ```
   - The relationship is simply `threads = cores x 2` when SMT is on, and `threads = cores` when it is off.
   - Practical effect: such a processor runs 4 tasks concurrently, but the throughput is roughly that of `2.5 cores`, not 4 — because two threads sharing a core cannot both use the ALUs at the same instant.

   Core i3, i5, i7 and i9

   | Point | i3 | i5 | i7 | i9 |
   |---|---|---|---|---|
   | Tier | Entry | Mid range | High end | Enthusiast |
   | Cores (typical) | 4 | 6 | 8 | 16-24 |
   | Threads | 8 | 12 | 16 | 24-32 |
   | L3 cache | Smallest | Medium | Large | Largest |
   | Turbo Boost | Usually absent | Yes | Yes | Yes, highest |
   | TDP | ~35-65 W | ~65 W | ~95-125 W | ~125-250 W |
   | Suited to | Browsing, office work | Everyday plus gaming | Editing, CAD, development | Workstation, rendering, servers |

   - The essential warning: the tier number is `not a generation`. A newer i5 usually beats an older i7, so the generation code — the leading digits of the model number, as in `i5-13600K` — matters more than the tier itself.
   - Note also that a higher number is not automatically better `for a given task`: a game that uses only four threads gains nothing from an i9's extra cores, and would run just as fast on an i5 with a higher clock.

5. **১৩. Core i7 জেনারেশন এর প্রসেসর এর উদাহরণ লিখ?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 942 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) An Intel `Core i7` processor's model number identifies its generation, so a full example names both.

   Examples by generation
   ```
      1st  gen (Nehalem, 2008)      : i7-920 , i7-960
      2nd  gen (Sandy Bridge, 2011) : i7-2600 , i7-2600K
      3rd  gen (Ivy Bridge, 2012)   : i7-3770 , i7-3770K
      4th  gen (Haswell, 2013)      : i7-4770 , i7-4790K
      6th  gen (Skylake, 2015)      : i7-6700 , i7-6700K
      8th  gen (Coffee Lake, 2017)  : i7-8700 , i7-8700K
      10th gen (Comet Lake, 2020)   : i7-10700 , i7-10700K
      11th gen (Rocket Lake, 2021)  : i7-11700K
      12th gen (Alder Lake, 2021)   : i7-12700K
      13th gen (Raptor Lake, 2022)  : i7-13700K
      14th gen (Raptor Lake R, 2023): i7-14700K
   ```

   How to read the model number
   ```
      i7 - 13 700 K
      ^    ^   ^  ^
      |    |   |  +-- suffix
      |    |   +----- SKU number : higher means a better chip in that generation
      |    +--------- GENERATION : 13 = 13th generation
      +-------------- tier : i3, i5, i7, i9
   ```

   Common suffixes
   ```
      K  : unlocked multiplier, can be overclocked
      F  : no integrated graphics
      KF : unlocked and no integrated graphics
      T  : low power desktop
      H  : high performance laptop
      U  : low power laptop
      HX : laptop, desktop-class performance
      X  : extreme edition (HEDT platform)
   ```

   A worked example — `i7-13700K`
   ```
      i7   : the high-end tier
      13   : 13th generation (Raptor Lake)
      700  : the SKU within that generation
      K    : unlocked, overclockable

      Specification : 16 cores (8 performance + 8 efficient), 24 threads,
                      30 MB L3 cache, up to 5.4 GHz turbo, 125 W base power
   ```

   - The point to state clearly: the `generation number matters more than the tier`. An `i7-4770` (4th generation, 2013) is comfortably beaten by an `i5-13600` (13th generation, 2022), because a decade of architectural improvement outweighs the tier difference. When comparing processors, always read the generation digits first.

## RISC vs CISC Architecture (4)

1. **RISC stand for __________? Write two characteristics of it's?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

   Answer: `RISC` stands for `Reduced Instruction Set Computer`.

   Two characteristics
   ```
      1. A SMALL SET OF SIMPLE, FIXED-LENGTH INSTRUCTIONS, each completing in
         about ONE clock cycle.
         Because every instruction is the same size and takes the same time,
         the pipeline never has to wait, and the control unit can be
         HARDWIRED rather than microprogrammed.

      2. A LOAD-STORE ARCHITECTURE with MANY REGISTERS.
         Only the LOAD and STORE instructions touch memory; every other
         instruction works on registers alone. With 32 or more general-purpose
         registers, most values stay in registers, so memory traffic is low.
   ```

   Other characteristics, if more are wanted
   ```
      Simple addressing modes    : usually only 3 or 4
      Efficient pipelining       : the direct result of uniform instructions
      Hardwired control unit     : fast, and small in silicon
      Larger code size           : more instructions are needed for the same job
      More work for the compiler : it must schedule instructions and allocate
                                   registers well
      Low power consumption      : which is why every mobile phone uses ARM
   ```

   Examples
   ```
      ARM, RISC-V, MIPS, SPARC, PowerPC, Apple M-series
   ```

   Compared with CISC

   | Point | RISC | CISC |
   |---|---|---|
   | Instruction set | Small and simple | Large and complex |
   | Instruction length | Fixed | Variable |
   | Cycles per instruction | About 1 | Many |
   | Memory access | Only LOAD and STORE | Most instructions |
   | Registers | Many (32+) | Few (8-16) |
   | Control unit | Hardwired | Microprogrammed |
   | Pipelining | Easy and efficient | Difficult |
   | Code size | Larger | Smaller |
   | Power | Low | Higher |
   | Examples | ARM, RISC-V, MIPS | Intel x86, AMD64 |

   - Practical note: modern x86 processors decode their CISC instructions internally into RISC-like `micro-operations`, so they are CISC at the interface and RISC in the execution core. RISC still wins decisively on `performance per watt`, which is why it dominates mobile and now, with Apple's M-series, the laptop market as well.

2. **Difference between RISC and CISC.** *[NPCBL Executive Trainee (IT) 2022 compact it 644 (ET: BUET)]*

   Answer: `RISC` (Reduced Instruction Set Computer) uses a small set of simple, uniform instructions. `CISC` (Complex Instruction Set Computer) uses a large set of powerful, varied instructions.

   RISC
   - Few instructions, all of `fixed length`, each completing in about `one clock cycle`.
   - A `load-store` architecture: only LOAD and STORE touch memory; everything else operates on registers.
   - Many general-purpose registers (32 or more), a `hardwired` control unit, and simple addressing modes.
   - Because every instruction has the same shape, `pipelining` works cleanly.
   - Examples: ARM, RISC-V, MIPS, SPARC, PowerPC, Apple M-series.

   CISC
   - Many instructions of `variable length`, some taking many cycles. One instruction can do a great deal of work — a single x86 instruction can load two operands from memory, multiply them and store the result.
   - Instructions may operate `directly on memory`.
   - Few registers (8 to 16), a `microprogrammed` control unit, and a rich set of addressing modes.
   - Designed when memory was expensive, so compact code mattered more than pipeline efficiency.
   - Examples: Intel x86, AMD64, Motorola 68000, IBM System/360.

   Difference

   | Point | RISC | CISC |
   |---|---|---|
   | Instruction set size | Small (about 100) | Large (several hundred) |
   | Instruction length | Fixed | Variable |
   | Cycles per instruction | Mostly 1 | 2 to 15 or more |
   | Memory access | Only LOAD and STORE | Most instructions can |
   | Registers | Many (32 or more) | Few (8 to 16) |
   | Addressing modes | Few (3-5) | Many (12 or more) |
   | Control unit | Hardwired | Microprogrammed |
   | Pipelining | Easy and efficient | Difficult |
   | Decoding | Simple | Complex |
   | Code size | Larger | Smaller |
   | Compiler complexity | Higher — it must schedule and allocate | Lower |
   | Transistor use | Spent on registers and cache | Spent on complex instruction logic |
   | Power consumption | Low | Higher |
   | Execution time | Depends on the number of instructions | Depends on instruction complexity |
   | Used in | Mobile, embedded, Apple M-series | Desktop and server x86 |

   The design philosophy behind each
   ```
      CISC : make each INSTRUCTION do more, so the program needs fewer of them.
             Sensible when memory was scarce and compilers were poor.

      RISC : make each instruction SIMPLE and FAST, and let the compiler
             assemble complex operations from them.
             Sensible when memory is cheap and compilers are good.
   ```

   - Practical note: the line has blurred. Modern x86 processors `decode` their CISC instructions into RISC-like `micro-operations` and execute those in a RISC-style pipeline, so they are CISC on the outside and RISC on the inside. RISC still wins clearly on `performance per watt`, which is why every mobile phone uses ARM, and why Apple moved its laptops to ARM as well.

3. **(ক) CISC and RISC processor বলতে কি বোঝেন?** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1072 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) CISC processor
   - `CISC` stands for `Complex Instruction Set Computer`. Its design philosophy is to make each `instruction do as much work as possible`, so that a program needs fewer of them.
   - Characteristics:
   ```
      A large instruction set, several hundred instructions
      VARIABLE-length instructions (1 to 15 bytes in x86)
      An instruction may take many clock cycles
      Instructions can operate DIRECTLY on memory
      Few general-purpose registers (8 to 16)
      Many addressing modes (12 or more)
      MICROPROGRAMMED control unit
      Smaller code size, but harder to pipeline
   ```
   - Why it was designed this way: in the 1970s memory was extremely expensive and compilers were poor, so packing more work into each instruction saved precious memory and made assembly programming easier.
   - Examples: `Intel x86`, `AMD64`, Motorola 68000, IBM System/360.

   RISC processor
   - `RISC` stands for `Reduced Instruction Set Computer`. Its philosophy is to make each instruction `simple and fast`, and let the compiler build complex operations out of them.
   - Characteristics:
   ```
      A small instruction set, about 100 instructions
      FIXED-length instructions
      Each instruction completes in about ONE clock cycle
      LOAD-STORE architecture : only LOAD and STORE touch memory
      Many general-purpose registers (32 or more)
      Few addressing modes (3 to 5)
      HARDWIRED control unit
      Larger code size, but very efficient pipelining
   ```
   - Why it works: memory became cheap and compilers became good, so the reasons for CISC disappeared. Studies also showed that compilers used only a small fraction of a CISC instruction set in practice.
   - Examples: `ARM`, `RISC-V`, MIPS, SPARC, PowerPC, Apple M-series.

   Comparison

   | Point | CISC | RISC |
   |---|---|---|
   | Instruction set | Large and complex | Small and simple |
   | Instruction length | Variable | Fixed |
   | Cycles per instruction | Many | About 1 |
   | Memory access | Most instructions | Only LOAD and STORE |
   | Registers | Few (8-16) | Many (32+) |
   | Addressing modes | Many | Few |
   | Control unit | Microprogrammed | Hardwired |
   | Pipelining | Difficult | Easy and efficient |
   | Code size | Smaller | Larger |
   | Compiler effort | Lower | Higher |
   | Power consumption | Higher | Low |
   | Transistors spent on | Instruction logic | Registers and cache |
   | Used in | Desktop and server | Mobile, embedded, Apple M-series |

   - The modern position: x86 processors now `decode` their CISC instructions into RISC-like `micro-operations` and execute those in a RISC-style pipeline — CISC at the interface, RISC in the core. RISC's advantage in `performance per watt` is decisive in battery-powered devices, which is why ARM dominates mobile and has now moved into laptops and servers.

4. **What is CISC and RISC?** *[BREB Assistant Hardware & Network Engineer 2019 compact it 1124 (ET: BREB)]*

   Answer: `CISC` and `RISC` are the two design philosophies for a processor's instruction set.

   CISC — Complex Instruction Set Computer
   - Makes each `instruction do as much work as possible`, so a program needs fewer instructions.
   ```
      Large instruction set (several hundred)
      VARIABLE-length instructions (1 to 15 bytes in x86)
      An instruction may take many clock cycles
      Instructions may operate DIRECTLY on memory
      Few registers (8 to 16), many addressing modes
      MICROPROGRAMMED control unit
      Compact code, but difficult to pipeline
   ```
   - Designed in the 1970s, when memory was very expensive and compilers were poor, so packing work into each instruction saved memory.
   - Examples: `Intel x86`, `AMD64`, Motorola 68000.

   RISC — Reduced Instruction Set Computer
   - Makes each instruction `simple and fast`, and lets the compiler assemble complex operations from them.
   ```
      Small instruction set (about 100)
      FIXED-length instructions
      Each completes in about ONE clock cycle
      LOAD-STORE architecture : only LOAD and STORE touch memory
      Many registers (32 or more), few addressing modes
      HARDWIRED control unit
      Larger code, but very efficient pipelining
   ```
   - Examples: `ARM`, `RISC-V`, MIPS, SPARC, PowerPC, Apple M-series.

   Comparison

   | Point | CISC | RISC |
   |---|---|---|
   | Instruction set | Large and complex | Small and simple |
   | Instruction length | Variable | Fixed |
   | Cycles per instruction | Many | About 1 |
   | Memory access | Most instructions | Only LOAD and STORE |
   | Registers | Few (8-16) | Many (32+) |
   | Addressing modes | Many (12+) | Few (3-5) |
   | Control unit | Microprogrammed | Hardwired |
   | Pipelining | Difficult | Easy and efficient |
   | Decoding | Complex | Simple |
   | Code size | Smaller | Larger |
   | Compiler effort | Lower | Higher |
   | Power consumption | Higher | Low |
   | Used in | Desktop, server | Mobile, embedded, laptops |

   An example of the difference
   ```
      Multiply two numbers held in memory :

      CISC : MULT [2:3], [5:2]        one instruction does load, multiply, store

      RISC : LOAD  R1, [2:3]
             LOAD  R2, [5:2]
             MUL   R1, R2
             STORE [2:3], R1          four simple instructions
   ```
   - The CISC version is shorter in code but takes many cycles and cannot be pipelined cleanly. The RISC version is longer but each instruction is one cycle and the pipeline stays full, so the total time is usually similar or better.

   - The modern reality: x86 processors `decode` CISC instructions into RISC-like `micro-operations` internally, so they are CISC at the interface and RISC in the execution core. RISC's decisive advantage is `performance per watt`, which is why ARM dominates mobile devices and now, with Apple's M-series, laptops as well.

## 8085 Microprocessor & Edge Computing (3)

1. (a) Edge Computing এর ধারণা সংক্ষেপে ব্যাখ্যা করুন।
   (b) 8085 মাইক্রোপ্রসেসর কী? রেজিস্টারের ইফেক্টিভ মেমোরি অ্যাড্রেসিং কার্যকারিতা ব্যাখ্যা করুন। *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

2. **Intel 8085 ও Intel 8086 Microprocessor-এর সর্বোচ্চ ফিজিক্যাল মেমোরি ক্যাপাসিটি কত এবং কেন?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 697 (ET: DPI)]*

3. **What is the difference between 8-bit (8085) and 16-bit (8086) microprocessor?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 865-866 (ET: BUET)]*
