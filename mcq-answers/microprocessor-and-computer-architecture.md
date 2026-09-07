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
answer: C
explanation: Accumulator হলো CPU-র একটি বিশেষ রেজিস্টার যা গাণিতিক এবং যৌক্তিক অপারেশনের প্রাথমিক ডেটা, মধ্যবর্তী ফলাফল এবং চূড়ান্ত ফলাফল সাময়িকভাবে ধারণ করে।

2. **______ are used to quickly accept, store and transfer data and instructions that are being used immediately by the CPU.** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 53 (ET: N/A)]*
   (ক) Graphics
   (খ) RAMs
   (গ) Caches
   (ঘ) Registers
answer: ঘ
explanation: Registers হলো CPU-র অভ্যন্তরে অবস্থিত সবচেয়ে দ্রুতগতির স্টোরেজ উপাদান, যা CPU কর্তৃক তাৎক্ষণিকভাবে ব্যবহৃত ডেটা ও নির্দেশ দ্রুত গ্রহণ, সংরক্ষণ এবং স্থানান্তর করে।

3. **Which feature is not applicable for memory mapped I/O?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*
   a) Device registers can be accessed with any instructions
   b) System memory address space is used up for ports
   c) New instructions are required to access the device registers
   d) Arithmetic and logical operation can be performed directly on data
answer: c
explanation: Memory-mapped I/O-তে মেমরি এবং I/O ডিভাইসের জন্য একই অ্যাড্রেস স্পেস ব্যবহৃত হয়। ফলে স্বাভাবিক মেমরি ইন্সট্রাকশন (যেমন MOV, ADD) দিয়েই I/O রেজিস্টার অ্যাক্সেস করা যায়; কোনো নতুন নির্দেশ (যেমন IN বা OUT) প্রয়োজন হয় না।

4. **Which of the following registers is loaded with the contents of the memory location pointed by the PC?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 128 (ET: N/A)]*
   a) Memory address registers
   b) Instruction register
   c) Memory data stores
   d) Program counter
answer: b
explanation: Fetch সাইকেলে Program Counter (PC) নির্দেশিত মেমরি লোকেশন থেকে ইন্সট্রাকশনটি এনে Instruction Register (IR)-এ লোড করা হয় যাতে পরবর্তীতে তা ডিকোড ও এক্সিকিউট করা যায়।

5. **The address bus flow in——** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 128 (ET: N/A)]*
   a) Unidirectional
   b) Bidirectional
   c) Multidirectional
   d) Circular
answer: a
explanation: অ্যাড্রেস বাস একমুখী (Unidirectional), কারণ প্রসেসর মেমরি বা I/O ডিভাইসে অ্যাড্রেস পাঠায়; মেমরি বা পেরিফেরাল থেকে CPU-র দিকে অ্যাড্রেস আসে না।

6. **Which one is not the flag of the 8086 Microprocessor?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 129 (ET: N/A)]*
   a) Carry Flag
   b) Parity Flag
   c) Zero Flag
   d) State Plag
answer: d
explanation: Intel 8086 মাইক্রোপ্রসেসরে ৯টি সক্রিয় ফ্ল্যাগ রয়েছে (CF, PF, AF, ZF, SF, TF, IF, DF, OF)। State Flag নামে কোনো ফ্ল্যাগ নেই।

7. **In a memory-mapped I/O system, which one is not present?** *[BTRC Sub-Assistant Director (Tech.) 2021 compact it 148 (ET: IBA)]*
   A. LDA
   B. IN
   C. ADD
   D. OUT
answer: B
explanation: Memory-mapped I/O ব্যবস্থায় I/O পোর্টগুলো মেমরি লোকেশন হিসেবে গণ্য হওয়ায় মেমরি নির্দেশ (যেমন LDA, STA) ব্যবহার করা হয়; কোনো বিশেষ IN বা OUT নির্দেশের অস্তিত্ব থাকে না।

8. **Which one is the 7$^{th}$ Generation intel processor?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 158 (ET: N/A)]*
   A) Intel core i7-9850HL
   B) Intel core i5-7200U
   C) Intel core i5-9400H
   D) Intel core i9-10900K
answer: B
explanation: Intel Core প্রসেসরের মডেল নম্বরের ড্যাশের পরের প্রথম অঙ্কটি জেনারেশন নির্দেশ করে। Core i5-7200U হলো ৭ম প্রজন্মের (Kaby Lake) প্রসেসর।

9. **Suppose, the operating clock frequency of a typical CPU is 700 MHz and the number of clocks required for execution of three different instruction types are 4, 8, and 10. If the corresponding appearance rate of the instructions are 30%, 60% and 10%, respectively, how many MIPS does this CPU perform?** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 186 (ET: N/A)]*
   a) 10
   b) 50
   c) 70
   d) 100
answer: d
explanation: Average CPI = (0.30 × 4) + (0.60 × 8) + (0.10 × 10) = 1.2 + 4.8 + 1.0 = 7.0।\nMIPS = Clock Rate (MHz) / CPI = 700 / 7.0 = 100 MIPS।

10. **Communication path between a computer microprocessor and main memory is called:** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 172 (ET: N/A)]*
    a) System bus
    b) ISA bus
    c) PCI bus
    d) Local bus
answer: a
explanation: মাইক্রোপ্রসেসর এবং প্রধান মেমরির মধ্যকার প্রাথমিক ডেটা ও অ্যাড্রেস আদান-প্রদানের পথকে System Bus (বা Front Side Bus) বলা হয়।

11. **Ice Lake CPU is intel’s code name for the processor of:** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 172 (ET: N/A)]*
    a) 11^{\text{th}} generation
    b) 8^{\text{th}} generation
    c) 9^{\text{th}} generation
    d) 10^{\text{th}} generation
answer: d
explanation: Ice Lake হলো Intel-এর ১০ম প্রজন্মের (10th Generation) ১০ ন্যানোমিটার আর্কিটেকচারভিত্তিক প্রসেসরের কোডনেম।

12. **In core i7-8650U processor, here U means:** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 173 (ET: N/A)]*
    a) Ultra low power
    b) Ultra high power
    c) Upgrade version
    d) Upgrade processor
answer: a
explanation: Intel প্রসেসর নামকরণে সাফিক্স 'U' দিয়ে Ultra-low power নির্দেশ করা হয়, যা কম বিদ্যুৎ খরচে ল্যাপটপ ডিভাইসের ব্যাটারি দীর্ঘস্থায়ী করতে তৈরি।

13. **Which is not pipeline hazard?** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 173 (ET: N/A)]*
    a) Resource hazard
    b) Control hazard
    c) Address hazard
    d) Data hazard
answer: c
explanation: প্রসেসর পাইপলাইনিংয়ে ৩ ধরনের হ্যাজার্ড দেখা যায়: Structural (Resource) hazard, Data hazard এবং Control (Branch) hazard। Address hazard বলে কোনো পাইপলাইন হ্যাজার্ড নেই।

14. **The processor reads an instruction from memory is called:** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 173 (ET: N/A)]*
    a) Interpret instruction
    b) Fetch instruction
    c) Read instruction
    d) Fetch data
answer: b
explanation: মেমরি থেকে প্রসেসরে নির্দেশ লোড করে আনার প্রথম ধাপটিকে Fetch instruction (বা Instruction Fetch) বলা হয়।

15. **Microprocessor reference that are available in the cache are called ________:** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 173 (ET: N/A)]*
    a) Cache hits
    b) Cache line
    c) Cache memory
    d) All of these
answer: a
explanation: প্রসেসরের কাঙ্ক্ষিত মেমরি রেফারেন্স বা ডেটা যদি ক্যাশে মেমরিতে সরাসরি পাওয়া যায়, তবে তাকে Cache Hit বলা হয় (না পাওয়া গেলে Cache Miss)।

16. **Sequence Control Register আর কি নামে পরিচিত?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 187 (ET: N/A)]*
    A) Program Counter
    B) Instruction Counter
    C) Sequence Register
    D) Controlling Register
answer: A
explanation: Program Counter (PC)-কে Sequence Control Register (SCR) বলা হয়, কারণ এটি নির্দেশনাসমূহ ক্রমানুসারে এক্সিকিউট করার জন্য পরবর্তী নির্দেশের অ্যাড্রেস ধরে রাখে।

17. **Intel 8086 microprocessor এর বহিঃস্থ Address bus এর width কত bit হয়?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 187 (ET: N/A)]*
    A) 8-bit
    B) 16-bit
    C) 20-bit
    D) 32-bit
answer: C
explanation: Intel 8086 মাইক্রোপ্রসেসরে ২০-বিট বহিঃস্থ অ্যাড্রেস বাস থাকে, যা সর্বোচ্চ 2^20 = 1 MB ফিজিক্যাল মেমরি অ্যাড্রেস করতে পারে।

18. **Microprocessor এর কোন অংশে ALU থাকে?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)]*
    A) Fetch unit
    B) Control Unit
    C) Processing Unit
    D) Flags Unit
answer: C
explanation: মাইক্রোপ্রসেসরের এক্সিকিউশন বা প্রসেসিং ইউনিটের (Execution/Processing Unit) অন্তর্ভুক্ত থাকে ALU এবং ইন্টারনাল ডেটা রেজিস্টার।

19. **নিচের কোন Operation টি CPU তে দ্রুত কাজ করে?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)], [BPSC Assistant Network Engineer 2019 compact it 197 (ET: N/A)]*
    A) Multiplication
    B) Bitwise OR
    C) Addition
    D) Division
answer: B
explanation: Bitwise লজিক্যাল অপারেশনগুলো (যেমন OR, AND) কোনো ক্যারি প্রপাগেশন ছাড়াই একক ক্লক সাইকেলে সরাসরি প্রতিটি বিটে সম্পন্ন হয়, ফলে Multiplication বা Addition-এর চেয়ে অনেক দ্রুত কাজ করে।

20. **A hardware device that is capable of executing a sequence of instructions is known as:** *[BREB Assistant Junior Engineer (IT) 2019 compact it 217 (ET: N/A)]*
    A) CPU
    B) ALU
    C) CU
    D) Processor
answer: D
explanation: সংজ্ঞানুসারে, যে কোনো হার্ডওয়্যার ডিভাইস যা ধারাবাহিকভাবে নির্দেশাবলি (sequence of instructions) এক্সিকিউট করতে সক্ষম তাকে Processor বলা হয়।

21. **What is the Address bit for an 8-bit Microprocessor?** *[BREB Assistant Junior Engineer (IT) 2019 compact it 218 (ET: N/A)]*
    A) 4
    B) 8
    C) 16
    D) None
answer: C
explanation: প্রমিত ৮-বিট মাইক্রোপ্রসেসরে (যেমন Intel 8085) ১৬-বিট অ্যাড্রেস বাস থাকে, যার মাধ্যমে সর্বোচ্চ 2^16 = 64 KB মেমরি অ্যাড্রেস করা সম্ভব।

22. **Intel 8086 মাইক্রোপ্রসেসর কত বিট রেজিস্টার থাকে?** *[BPSC Assistant Network Engineer 2019 compact it 194 (ET: N/A)]*
    A) 4
    B) 8
    C) 14
    D) 16
answer: D
explanation: Intel 8086 একটি ১৬-বিট মাইক্রোপ্রসেসর এবং এর অভ্যন্তরীণ সকল জেনারেল ও স্পেশাল পারপাস রেজিস্টারসমূহ ১৬-বিটের (16-bit) হয়ে থাকে।

23. **START:MOV AX, BX একটি assembly language instruction এখানে MOV হলো-** *[BPSC Assistant Network Engineer 2019 compact it 195 (ET: N/A)]*
    A) লেবেল
    B) সোর্স
    C) Opcode
    D) ডেস্টিনেশন
answer: C
explanation: এই ইন্সট্রাকশনে START হলো লেবেল, MOV হলো অপারেশন কোড (Opcode), AX হলো গন্তব্য অপারেন্ড (Destination) এবং BX হলো উৎস অপারেন্ড (Source)।

24. **Physical connection between Microprocessor Memory and other parts is called-** *[Sonali & Janata Bank Assistant Programmer 2018 compact it 240 (ET: N/A)]*
    A) Address bus
    B) Data Bus
    C) path
    D) Hub
answer: A
explanation: মাইক্রোপ্রসেসর, মেমরি ও অন্যান্য অংশের মধ্যকার সরাসরি সংযোগ রক্ষাকারী বাসগুলোর মধ্যে মেমরি লোকেশন নির্দেশকারী ফিজিক্যাল চ্যানেলকে Address bus বলা হয়।

25. **Register circuit is not use in-** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 237 (ET: N/A)]*
    A) Digital clocks
    B) Components
    C) RAM
    D) Amplifier
answer: D
explanation: Amplifier একটি এনালগ বর্তনী (Analog circuit) যা সংকেতের বিস্তৃতি বাড়ায়; এতে ডিজিটাল বাইনারি ডেটা সংরক্ষণের জন্য কোনো রেজিস্টার সার্কিট ব্যবহৃত হয় না।

26. **A single communication system that transfers and connects the data between major components inside a computer is-** *[Combined Bank Senior Officer (IT) 2018 compact it 223 (ET: DU)]*
    A) Address Bus
    B) Data Bus
    C) System Bus
    D) Control Bus
answer: C
explanation: কম্পিউটারের প্রধান উপাদানসমূহের (CPU, Memory, I/O) মধ্যে সমন্বিতভাবে ডেটা ও সংকেত আদান-প্রদানকারী সামগ্রিক যোগাযোগ মাধ্যম হলো System Bus।

27. **USB stands for-** *[Combined Bank Senior Officer (IT) 2018 compact it 224 (ET: DU)]*
    A) Universal Serial Bus
    B) Universal Series Bus
    C) Universal Serial Bits
    D) Universal Series Bits
answer: A
explanation: USB-এর পূর্ণরূপ হলো Universal Serial Bus।

28. **Compared to CISC and RISC, processors (at the same clock) are -----** *[Combined Bank Maintenance Engineer 2018 compact it 227 (ET: N/A)], [Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 249 (ET: N/A)]*
    A) Faster
    B) slower
    C) similar
    D) undefined
answer: A
explanation: একই ক্লক গতিতে RISC প্রসেসর তুলনামূলক সরল আর্কিটেকচার এবং একক সাইকেল ইন্সট্রাকশন এক্সিকিউশনের কারণে CISC প্রসেসরের তুলনায় দ্রুতগতিতে (Faster) কাজ সম্পাদন করে।

29. **CPU fetches the instruction from memory according to value of-** *[Combined 3 Bank Assistant Programmer 2018 compact it 231 (ET: N/A)]*
    A) Program counter
    B) status register
    C) instruction register
    D) program status word
answer: A
explanation: Program Counter (PC) পরবর্তী নির্দেশের মেমরি ঠিকানা ধরে রাখে এবং CPU সেই ঠিকানা অনুসারে মেমরি থেকে নতুন ইন্সট্রাকশন ফেচ করে।

30. **ALU stores the computed result immediately in** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 246 (ET: N/A)]*
    A) Memory Address registers
    B) PC
    C) General registers
    D) Accumulator
answer: D
explanation: গাণিতিক ও যৌক্তিক ক্রিয়া সম্পাদনের পর ALU তার তাৎক্ষণিক ফলাফল সরাসরি Accumulator রেজিস্টারে জমা রাখে।

31. **The word length of a computer is measured in-** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 241 (ET: N/A)]*
    A) Bytes
    B) Millimeters
    C) Metes
    D) Bits
answer: D
explanation: কম্পিউটারের ওয়ার্ড লেন্থ (Word Length) অর্থাৎ একবারে CPU কত বিট ডেটা প্রসেস করতে পারে তা বিট (Bits)-এ পরিমাপ করা হয় (যেমন 32-bit বা 64-bit word)।

32. **Central Processing Unit is combination of-** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 242 (ET: N/A)]*
    A) Control Storage
    B) Control and output unit
    C) Arithmetic Logic and Input Unit
    D) Arithmetic logic and control unit
answer: D
explanation: CPU মূলত Arithmetic Logic Unit (ALU), Control Unit (CU) এবং ইন্টারনাল রেজিস্টারসমূহের সমন্বয়ে গঠিত।

33. **The control unit of a microprocessor-** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 243 (ET: N/A)]*
    A) Stores data in the memory
    B) accepts input data from keyboard
    C) Performs arithmetic/logic function
    D) None of the above
answer: D
explanation: Control Unit প্রসেসরের নির্দেশসমূহ ডিকোড করে বিভিন্ন অংশে নিয়ন্ত্রণ সংকেত প্রদান করে; এটি ডেটা সংরক্ষণ করে না, সরাসরি ইনপুট গ্রহণ করে না এবং পাটিগণিত/লজিক কাজও করে না।

34. **Which bus used to connect the monitor to the CPU?** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 261 (ET: N/A)]*
    A) PCI bus
    B) STE bus
    C) Memory bus
    D) SCSI bus
answer: A
explanation: কম্পিউটারের গ্রাফিক্স বা ভিডিও অ্যাডাপ্টার যার সাথে মনিটর যুক্ত থাকে, তা মাদারবোর্ডের PCI (বা PCIe) বাসের মাধ্যমে CPU-র সাথে সংযুক্ত হয়।

35. **At the same clock speed compared to CISC, RISC processor works ________.** *[Bangladesh Bank Assistant Maintenance Engineer 2013 compact it 261 (ET: N/A)]*
    a. faster
    b. Slower
    c. at same speed
    d. none
answer: a
explanation: ক্লক স্পিড এক হলে RISC প্রসেসর সরল ও কার্যকর পাইপলাইনিংয়ের মাধ্যমে প্রতি চক্রে একটি বা একাধিক নির্দেশ সম্পাদন করতে পারায় CISC-এর চেয়ে দ্রুততর (faster) কাজ করে।

## Memory Hierarchy (28)

1. **Considering computer memory speed, which one is correct order from highest to lowest?** *[Combined Bank Officer (IT) 04.10.2024 compact it 12 (ET: BIBM)]*
   (a) RAM>Cache>Register SSD HDD
   (b) Cache RAM>SSD>HDD>Register
   (c) RAM>SSD>Cache>HDD>Register
   (d) Register>Cache>RAM>SSD HDD
answer: d
explanation: মেমরি হায়ারার্কি অনুযায়ী অ্যাক্সেস গতির সঠিক অধঃক্রম (সর্বোচ্চ থেকে সর্বনিম্ন) হলো: Register > Cache > RAM > SSD > HDD।

2. **An increase in a computer's RAM leads to a typical improvement in performance because:** *[Combined Bank Officer (IT) 04.10.2024 compact it 13 (ET: BIBM)]*
   (a) Virtual memory increases
   (b) Fewer segmentation faults occur
   (c) A larger RAM is faster
   (d) Fewer page faults occur
answer: d
explanation: RAM বৃদ্ধি পেলে মেমরিতে একসাথে বেশি পেজ রাখা সম্ভব হয়, ফলে পেজ ফল্ট (Page fault) এবং ডিস্কে সোয়াপিংয়ের হার উল্লেখযোগ্যভাবে হ্রাস পায়, যা কম্পিউটারের পারফরম্যান্স বাড়ায়।

3. **Out of all the following, which one isn't a form of memory?** *[Combined Bank Officer (IT) 04.10.2024 compact it 13 (ET: BIBM)]*
   (a) translation lookaside buffer
   (b) instruction opcode
   (c) instruction register
   (d) instruction cachenss
answer: b
explanation: TLB, Instruction Register এবং Instruction Cache সবই মেমরি বা স্টোরেজের বিভিন্ন রূপ। কিন্তু Instruction Opcode হলো কোনো মেমরি নয়, বরং মেমরি নির্দেশিকার অপারেশনের ধরন নির্দেশক কোড।

4. **Which among the following is the fastest memory in a computer that holds information?** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 41 (ET: N/A)]*
   (a) Register
   (b) Cache
   (c) Main memory
   (d) RAM
answer: a
explanation: কম্পিউটারের মেমরি হায়ারার্কিতে CPU Register হলো সবচেয়ে দ্রুতগতির স্টোরেজ উপাদান, যা সরাসরি প্রসেসর কোরের ভেতর অবস্থিত।

5. **Which mode of memory access is the fastest?** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 47 (ET: N/A)]*
   (ক) Reference
   (খ) Pointer
   (গ) Double pointer
   (ঘ) DMA
answer: ঘ
explanation: Direct Memory Access (DMA) পদ্ধতিতে CPU-এর ক্রমাগত হস্তক্ষেপ ছাড়াই হার্ডওয়্যার ডিভাইস সরাসরি মেমরি থেকে বা মেমরিতে উচ্চগতিতে ডেটা আদান-প্রদান করতে পারে।

6. **Which of the following causes the average memory access time to increase in a memory system with cache memory?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*
   a) Reduction of access time to cache memory
   b) Decrease in hit ratio
   c) Reduction of miss penalty
   d) Decrease in miss ratio
answer: b
explanation: Average Memory Access Time (AMAT) = Hit Time + (Miss Rate × Miss Penalty)। Hit ratio হ্রাস পাওয়ার অর্থ Miss ratio বৃদ্ধি পাওয়া, যার ফলে গড় অ্যাক্সেস সময় বৃদ্ধি পায়।

7. **Which of the following is not a nonvolatile storage device?** *[Sonali and Janata Bank Assistant Database Administrator 25-09-2021 compact it 116 (ET: N/A)]*
   a) Memory Stick
   b) Hard Disk
   c) Random Access Memory
   d) NVRAM
answer: c
explanation: Random Access Memory (RAM) একটি ভোলাটাইল বা ক্ষণস্থায়ী মেমরি; বিদ্যুৎ সরবরাহ বন্ধ হলে এর অভ্যন্তরে সংরক্ষিত তথ্য মুছে যায়।

8. **What is the typical speed of USB version 3.0?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 102 (ET: N/A)]*
   (a) 4.8G bits per second
   (b) 610 Mbps
   (c) 6Gbps
   (d) Both a and b
answer: d
explanation: USB 3.0 (SuperSpeed)-এর স্ট্যান্ডার্ড তাত্ত্বিক সিগন্যালিং গতি হলো 5 Gbps বা প্রায় 4.8 Gbps (4.8G bits per second), যা প্রায় 600-610 MB/s (বাইট/সেকেন্ড) ট্রান্সফার রেটের সমতুল্য।

9. **SSDs are more durable than HDDs in extreme and harsh environments because** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 102 (ET: N/A)]*
   (a) They don't have actuator arms
   (b) They use fast electronics Memory
   (c) They do not use 0/1 as data storage unit which is prone to crash
   (d) All of the above statements are true
answer: a
explanation: SSD-তে কোনো ঘূর্ণায়মান ডিস্ক বা মুভিং মেকানিক্যাল অ্যাকচুয়েটর আর্ম (actuator arm) থাকে না; তাই ঝাঁকুনি বা কঠিন পরিবেশে হেড ক্র্যাশের কোনো ঝুঁকি থাকে না।

10. **The term LPDDR means-** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 105 (ET: N/A)]*
    (a) Low-Power Discrete Data Rate
    (b) Low-processing Double Data Rate
    (c) Low-Programmable Double Data Rate
    (d) None of the above
answer: d
explanation: LPDDR-এর পূর্ণরূপ হলো "Low-Power Double Data Rate" (SDRAM), যা মোবাইল ডিভাইস ও ল্যাপটপে কম বিদ্যুৎ খরচে ব্যবহৃত হয়।

11. **How many core/threads does the Intel Core i7-9700K processor have?** *[Sonali Bank and BDBL Senior Officer (IT) 25.09.2021 compact it 107 (ET: N/A)]*
    (a) 6/12
    (b) 4/8
    (c) 8/8
    (d) 8/16
answer: c
explanation: Intel Core i7-9700K (9th Gen) প্রসেসরে ৮টি ফিজিক্যাল কোর রয়েছে কিন্তু এতে Hyper-Threading প্রযুক্তি না থাকায় এর থ্রেড সংখ্যাও ৮টি (8 cores / 8 threads)।

12. **Which of the following uses the flip-flop circuit in a memory cell?** *[Rupali Bank Ltd. Assistant Network Engineer (ANE) 2021 compact it 82 (ET: N/A)]*
    a. DRAM
    b. EEPROM
    c. SDRAM
    d. SRAM
answer: d
explanation: Static RAM (SRAM)-এর প্রতিটি মেমরি সেল ফ্লিপ-ফ্লপ (ল্যাচ) সার্কিটের সমন্বয়ে গঠিত, তাই এতে ক্যাপাসিটরের মতো পর্যায়ক্রমিক রিফ্রেশিংয়ের প্রয়োজন হয় না।

13. **কোন বৈশিষ্ট্যের কারণে অজগ স্থায়ী স্মৃতি-স্টোরেজ হিসেবে ব্যবহার অনুপযোগী?** *[BTRC Sub-Assistant Director (Tech.) 2021 compact it 148 (ET: IBA)]*
    A. Too Slow
    B. Unreliable
    C. Volatility
    D. Too Bulky
answer: C
explanation: RAM একটি উদ্বায়ী (Volatile) মেমরি; বিদ্যুৎ প্রবাহ বন্ধ হওয়ার সাথে সাথে এতে সংরক্ষিত সকল ডেটা মুছে যায়, তাই এটি স্থায়ী স্টোরেজ হিসেবে অনুপযোগী।

14. **Which of the following memory devices is not reprogrammable?** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 174 (ET: N/A)]*
    a) Flash memory
    b) ROM
    c) EPROM
    d) EEPROM
answer: b
explanation: Mask ROM বা সাধারণ ROM কারখানায় তৈরির সময়ই স্থায়ীভাবে ডেটা লেখা হয়, যা পরবর্তীতে কোনোভাবেই পরিবর্তন বা রিপ্রোগ্রাম করা যায় না।

15. **There is a RAM issue on a PC/laptop. Which of the following symptom(s) might be an indication of RAM issue?** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 178 (ET: N/A)]*
    a) PC frequently freezes, reboots
    b) Wrong BIOS time
    c) Function keys are not working properly
    d) All of them
answer: a
explanation: RAM ত্রুটিপূর্ণ হলে মেমরি করাপশনের কারণে সিস্টেম ঘন ঘন ফ্রিজ (হ্যাং) করে, ব্লু স্ক্রিন অব ডেথ (BSOD) দেয় কিংবা কম্পিউটার হঠাৎ রিবুট নেয়।

16. **A solid-state drive (SSD) is a newer, faster type of device that stores data on instantly-accessible ________.** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 178 (ET: N/A)]*
    a) Ultra Magnetic Chip
    b) Integrated Circuit
    c) Random Access Memory
    d) High Bandwidth memory
answer: b
explanation: SSD সেমিকন্ডাক্টর ফ্ল্যাশ মেমরিভিত্তিক সমন্বিত বর্তনী বা ইন্টিগ্রেটেড সার্কিট (Integrated Circuit) চিপে স্থায়ীভাবে অতি দ্রুত অ্যাক্সেসযোগ্য ডেটা সংরক্ষণ করে।

17. **Which factor is not affecting the processing speed of a computer system?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 159 (ET: N/A)]*
    A) Cache memory
    B) Clock speed
    C) Monitor
    D) RAM
answer: C
explanation: মনিটর কেবল একটি ডিসপ্লে আউটপুট ডিভাইস; এটি CPU-র ডেটা প্রক্রিয়াকরণ বা প্রসেসিং স্পিডকে কোনোভাবে প্রভাবিত করে না।

18. **Main Memory কোনটি?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 186 (ET: N/A)]*
    A) RAM
    B) ROM
    C) HDD
    D) Floppy
answer: A
explanation: কম্পিউটারের প্রধান মেমরি বা মেইন মেমরি (Main Memory) বলতে মূলত RAM (Random Access Memory)-কে বোঝানো হয়।

19. **নিচের কোনটি সবচেয়ে দ্রুত Data transfer করতে পারে?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 187 (ET: N/A)], [BPSC Assistant Network Engineer 2019 compact it 197 (ET: N/A)]*
    A) RAM
    B) Hard disk
    C) CD ROM
    D) Cache Memory
answer: D
explanation: অপশনগুলোর মধ্যে ক্যাশে মেমরি (Cache Memory) CPU-র সবচেয়ে কাছাকাছি অতি উচ্চগতির SRAM দিয়ে গঠিত হওয়ায় এটি সবচেয়ে দ্রুত ডেটা স্থানান্তর করে।

20. **Arithmetic and Logical operation এর ডাটা কাজের সময় কোথায় রাখা হয়?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)]*
    A) Arithmetic Register
    B) Accumulator
    C) Logical Register
    D) Controller
answer: B
explanation: গাণিতিক ও যৌক্তিক অপারেশন সম্পাদনের সময় মধ্যবর্তী ডেটা ও ফলাফল তাৎক্ষণিকভাবে Accumulator রেজিস্টারে জমা রাখা হয়।

21. **Which one can be used for read only?** *[BREB Assistant Junior Engineer (IT) 2019 compact it 218 (ET: N/A)]*
    A) RAM
    B) ROM
    C) Both A & B
    D) None
answer: B
explanation: ROM (Read Only Memory)-এ সাধারণ কাজের সময় কোনো নতুন ডেটা রাইট করা যায় না, এটি থেকে কেবলমাত্র ডেটা পড়া (Read-only) সম্ভব।

22. **Which is the faster memory?** *[DESCO Assistant Engineer (CSE) 2016 compact it 257 (ET: N/A)], [BREB Assistant General Manager (IT) 2016 compact it 253 (ET: N/A)]*
    a. RAM
    b. Secondary memory
    c. DRAM
    d. Cache
answer: d
explanation: ক্যাশে মেমরি সরাসরি প্রসেসরে অন্তর্ভুক্ত থাকায় এর ল্যাটেন্সি সর্বনিম্ন এবং গতি সাধারণ RAM বা অন্যান্য মেমরির চেয়ে অনেক বেশি।

23. **Which of the following terms is the most closely related to main memory?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 240 (ET: N/A)]*
    A) Non-volatile
    B) Permanent
    C) Control unit
    D) Temporary
answer: D
explanation: প্রধান মেমরি বা RAM একটি ক্ষণস্থায়ী (Temporary / Volatile) স্টোরেজ, কারণ কম্পিউটার বন্ধ করলে এতে সংরক্ষিত ডেটা মুছে যায়।

24. **Which unit holds data permanently?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 241 (ET: N/A)]*
    A) Input unit
    B) Secondary storage unit
    C) Output unit
    D) Primary Memory unit
answer: B
explanation: সেকেন্ডারি স্টোরেজ ইউনিট (যেমন HDD, SSD, Magnetic Tape) বিদ্যুৎ সরবরাহ না থাকলেও ডেটা স্থায়ীভাবে (Permanently) ধারণ করে রাখে।

25. **Magnetic tape can serve as—** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 241 (ET: N/A)]*
    A) Secondary storage media
    B) Output media
    C) Input media
    D) All of them
answer: D
explanation: ম্যাগনেটিক টেপ সেকেন্ডারি ব্যাকআপ স্টোরেজ মিডিয়া হিসেবে কাজ করে এবং ডেটা রিড (ইনপুট) ও রাইট (আউটপুট) উভয় কাজেই ব্যবহৃত হতে পারে।

26. **Which of the following is internal memory?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 243 (ET: N/A)]*
    A) Disks
    B) Pen Drives
    C) RAM
    D) CDs
answer: C
explanation: RAM হলো কম্পিউটারের প্রাথমিক বা অভ্যন্তরীণ মেমরি (Internal Memory)। বাকিগুলো বাহ্যিক বা সেকেন্ডারি স্টোরেজ।

27. **Which of the following memories needs refreshing?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 243 (ET: N/A)]*
    A) SRAM
    B) DRAM
    C) ROM
    D) All of them
answer: B
explanation: DRAM-এর মেমরি সেল ক্যাপাসিটর দিয়ে তৈরি হওয়ায় এর চার্জ দ্রুত লিক হয়ে যায়; ডেটা ধরে রাখতে নিয়মিত বিরতিতে রিফ্রেশ (Periodic Refreshing) করতে হয়।

28. **Which memory is called as primary memory?** *[BREB Assistant General Manager (IT) 2016 compact it 254 (ET: N/A)]*
    A) Hard Disk
    B) Pen Drive
    C) Rom
    D) RAM
answer: D
explanation: কম্পিউটার সিস্টেমে সরাসরি প্রসেসর কর্তৃক ব্যবহৃত প্রধান কার্যকরী মেমরি বা প্রাইমারি মেমরি হলো RAM (Random Access Memory)।

## Secondary Storage (HDD & Disk Organization) (13)

1. **A hard disk is divided into tracks which are further subdivided into ______** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 41 (ET: N/A)]*
   (a) Vectors
   (b) Clusters
   (c) Sectors
   (d) None of the above
answer: c
explanation: হার্ড ডিস্কের প্রতিটি প্ল্যাটার কতগুলো এককেন্দ্রিক বৃত্তাকার ট্র্যাকে (Tracks) বিভক্ত থাকে এবং প্রতিটি ট্র্যাক আরও ছোট অংশে বিভক্ত থাকে যাকে সেক্টর (Sectors) বলা হয়।

2. **Consider a magnetic disk packed with 32 surfaces. Each surface is divided into 128 tracks while 256 sectors per track. If the size of a sector is 1024 bytes, then what is the total capacity of the disk?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 127 (ET: N/A)]*
   a) 2³⁰ bytes
   b) 2³³ bytes
   c) 2²⁷ bytes
   d) 2²⁰ bytes
answer: a
explanation: মোট ক্যাপাসিটি = Surfaces × Tracks × Sectors × Sector size = 32 × 128 × 256 × 1024 = 2^5 × 2^7 × 2^8 × 2^10 = 2^30 bytes (বা 1 GB)।

3. **DVD এর চেয়ে বেশী Data store করা যায় কোনটিতে?** *[BPSC Senior Instructor (MEW) 2021 compact it 145 (ET: N/A)]*
   (a) CD Rom
   (b) Floppy
   (c) Blue Ray disk
   (d) Red Ray disk
answer: c
explanation: Blu-ray ডিস্কের ধারণক্ষমতা একক লেয়ারে ২৫ জিবি এবং ডুয়াল লেয়ারে ৫০ জিবি পর্যন্ত হয়, যা ডিভিডির (৪.৭ জিবি - ৮.৫ জিবি) চেয়ে অনেক বেশি।

4. **Which of the following is major part of time taken when accessing data on the disk?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 205 (ET: AUST)]*
   A) Settle time
   B) Rotational delay
   C) Waiting time
   D) Seek time
answer: D
explanation: ডিস্কের রিড/রাইট হেডকে কাঙ্ক্ষিত সিলিন্ডার বা ট্র্যাকে মুভ করাতে যে সময় লাগে তাকে Seek time বলা হয়, এবং এটি ডিস্ক অ্যাক্সেস সময়ের সবচেয়ে বড় অংশ।

5. **Place where large amount of data is stored outside central processing unit is called** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 215 (ET: AUST)]*
   A) Peripherals
   B) Control unit
   C) AI unit
   D) Backing store
answer: D
explanation: CPU ও মূল মেমরির বাইরে বিপুল পরিমাণ ডেটা দীর্ঘমেয়াদে স্থায়ীভাবে সংরক্ষণ করার অক্সিলিয়ারি বা সেকেন্ডারি স্টোরেজকে Backing store বলা হয়।

6. **Which are not performance characteristics of hard disk?** *[Sonali & Janata Bank Assistant Programmer 2018 compact it 239 (ET: N/A)]*
   A) data transfer time
   B) response time
   C) power consumption
   D) shelf life
answer: D
explanation: Data transfer rate, response time এবং power consumption হলো হার্ড ডিস্কের কার্যক্ষমতা বা অপারেশনের বৈশিষ্ট্য। কিন্তু Shelf life হলো দীর্ঘমেয়াদে সংরক্ষণের স্থায়িত্বকাল, যা পারফরম্যান্স বৈশিষ্ট্য নয়।

7. **Which of the following is used for manufacturing chips?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 241 (ET: N/A)]*
   A) Control bus
   B) Control unit
   C) Parity unit
   D) Semiconductor
answer: D
explanation: কম্পিউটারের ইন্টিগ্রেটেড সার্কিট বা চিপ তৈরিতে অর্ধপরিবাহী বা সেমিকন্ডাক্টর (যেমন সিলিকন) উপাদান ব্যবহৃত হয়।

8. **Before a disk can be used to store data, it must be-** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 241 (ET: N/A)]*
   A) Formatted
   B) Reformatted
   C) Addressed
   D) None
answer: A
explanation: নতুন কোনো ডিস্কে ডেটা সংরক্ষণের পূর্বে অপারেটিং সিস্টেমের ব্যবহারোপযোগী ফাইল সিস্টেম এবং ট্র্যাক-সেক্টর কাঠামো তৈরির জন্য ডিস্ক ফরম্যাট (Formatted) করতে হয়।

9. **Which technology is used in Compact disks?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 241 (ET: N/A)]*
   A) Mechanical
   B) Electrical
   C) Electromagnetic
   D) Laser
answer: D
explanation: Compact Disc (CD) একটি অপটিক্যাল মিডিয়া, যাতে ডেটা রিড ও রাইট করতে লেজার রশ্মি (Laser technology) ব্যবহৃত হয়।

10. **Which of the following is a storage device?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 241 (ET: N/A)]*
    A) Tape
    B) Hard Disk
    C) Floppy Disk
    D) All of them
answer: D
explanation: ম্যাগনেটিক টেপ, হার্ড ডিস্ক এবং ফ্লপি ডিস্ক—সবগুলোই কম্পিউটার সিস্টেমে সেকেন্ডারি স্টোরেজ ডিভাইস হিসেবে ব্যবহৃত হয়।

11. **What does the disk drive of computer do?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 242 (ET: N/A)]*
    A) Rotate the Disk
    B) Read the disk
    C) Load a program form the disk into the memory
    D) Both B and C
answer: D
explanation: ডিস্ক ড্রাইভ ডিস্ক থেকে সংরক্ষিত ডেটা ও নির্দেশ রিড করে এবং প্রয়োজনীয় প্রোগ্রামকে মেমরিতে (RAM) লোড করতে সহায়তা করে।

12. **Which of the items below are considered removable storage media?** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 242 (ET: N/A)]*
    A) Removable hard disk cartridges
    B) (Magneto-optical) disk
    C) Flexible disks cartridges
    D) All of them
answer: D
explanation: Removable hard disk, Magneto-optical disk এবং Flexible disk (ফ্লপি কার্ট্রিজ)—সবগুলোই সিস্টেম থেকে সহজে আলাদা ও পরিবহনযোগ্য রিমুভেবল স্টোরেজ মিডিয়া।

13. **A hard disk is divided into tracks which are further subdivided into ________** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 270 (ET: N/A)]*
    a. Clusters
    b. Sectors
    c. Vectors
    d. Heads
answer: b
explanation: হার্ড ডিস্কের ট্র্যাকসমূহ ছোট ছোট নির্দিষ্ট আকারের ব্লকে বিভক্ত থাকে, যাদের সেক্টর (Sectors) বলা হয়।

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
