<!-- TOC START -->
**Table of Contents** — 9 subtopics · 144 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Logic Gates & Universal Gates](#logic-gates--universal-gates-32) | 32 |
| 2 | [Number Systems & Base Conversions](#number-systems--base-conversions-24) | 24 |
| 3 | [Combinational Circuits (Adders, Encoders, MUX)](#combinational-circuits-adders-encoders-mux-23) | 23 |
| 4 | [Karnaugh Map (K-Map)](#karnaugh-map-k-map-19) | 19 |
| 5 | [Boolean Algebra & De Morgan’s Theorem](#boolean-algebra--de-morgans-theorem-18) | 18 |
| 6 | [Sequential Circuits (Latches & Flip-Flops)](#sequential-circuits-latches--flip-flops-17) | 17 |
| 7 | [Logic Families (TTL vs CMOS)](#logic-families-ttl-vs-cmos-6) | 6 |
| 8 | [2's Complement & Binary Arithmetic](#2s-complement--binary-arithmetic-4) | 4 |
| 9 | [Finite State Machines (FSM)](#finite-state-machines-fsm-1) | 1 |

<!-- TOC END -->

---

## Logic Gates & Universal Gates (32)

1. Draw the circuit schematic diagrams to build an Exclusive-OR (XOR) logic function using only universal NAND gates. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

2. Explain how any Boolean function can be implemented using only universal gates. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

3. **(b) Draw the X-OR and X-NOR gate truth table diagram.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1445 (ET: N/A)]*

4. **Why NAND is universal gate?** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*

5. **NOR গেইট এর দুটি ইনপুট a, b হলে আউটপুট x কত?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

6. **\bar{A}\bar{B}.(\overline{A+B}).C ; Write Truth Table.** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1320 (ET: DU)]*

7. **Logic Circuit of Boolean algebra: Q = \bar{C} + \bar{A}B + \overline{BC(B + C)}; Where output Q and input Q(A, B, C)=(0,0,1)?** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 315 (ET: N/A)]*

8. **Implement OR gate and AND gate using minimum number of NAND and NOR gate.** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 399 (ET: BUET)]*

9. **Draw the logic circuit of the Boolean Expression, Q = \bar{A}\bar{B} + BC\overline{(B+C)}; find Q as output where input (A, B, C) = (1, 0, 1).** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 307 (ET: BIBM)]*

10. **What is Universal gate and how is constructed it?** *[BRiCM Assistant Maintenance Engineer 24.02.2024 compact it 405 (ET: N/A)]*

11. **মৌলিক গেইট কী? NAND এবং NOR গেইটকে কেন সার্বজনীন গেইট বলা হয় ব্যাখ্যা করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 406 (ET: N/A)]*

12. **X = \bar{A}BC + A\bar{B}C + AB\bar{C} + ABC সমীকরণটির সরলীকৃত মান NAND এবং NOR গেইট দ্বারা বাস্তবায়ন করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 407 (ET: N/A)]*

13. **$Y = A \cdot B + \overline{(A \cdot B)}$** *[EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)]*

14. **Explain: NOR and NAND is a Universal gate.** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 643 (ET: BUET)]*

15. **Define basic logical operations with examples. (AND, OR, NOT)** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*

16. **(a) Implement the following expression using NAND gates only: F = AB\bar{C} + ABC + \bar{A}BC** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 687 (ET: N/A)]*

17. **NAND gate ব্যবহার করে OR gate তৈরি করার logic diagram অঙ্কন করুন?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 697 (ET: DPI)]*

18. **What is Logic gate? Prove that NAND and NOR gate is Universal gate.** *[CAAB Assistant Maintenance Engineer (AME) 2022 compact it 724 (ET: N/A)]*

19. **Implementation the following two Boolean functions using NAND gate only: (a) F = A + (B' + C)(D' + BE') (b) F = ((A + B) + CD)E** *[NWPGCL Junior Assistant Manager (IT) 2022 compact it 731 (ET: N/A)]*

20. **(গ) Universal logic gate কি? 3-input এর একটি Universal logic gate এর Logic symbol এবং Truth Table দেখান।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 770 (ET: N/A)]*

21. **What is Universal gate? NAND and NOR gate কে Universal gate বলা হয় কেন?** *[DMLC Assistant Teacher (ICT) 2021 compact it 827-828 (ET: N/A)]*

22. **Implement X-OR gate using NAND gate. Maximum 4 NAND gate are using.** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 862 (ET: BUET)]*

23. **What is basic Logic gate? Which gate are called Universal gate and write down advantages of Universal gate?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 873-874 (ET: N/A)]*

24. **How can you Implement AND, OR and NOT gates using only NAND and NOR gates? What is the main difference between Latch and Flip-flop?** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*

25. **Make NAND gate using NOR gate.** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 933 (ET: BUET)]*

26. **(i) Logic gate কী? মৌলিক Logic gate কয়টি ও কী কী? সত্যক সারণিসহ আলোচনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 958-959 (ET: N/A)]*

27. **Design 3 input NAND gate and 2 input XOR gate using 2 input NAND gate.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1034 (ET: BUET)]*

28. **How will realize a AND gate and OR gate using CMOS NAND and NOR gate?** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1051-1052 (ET: BUET)]*

29. **(খ) Universal Gate কাকে বলে? Universal Gate-এর সার্বজনীনতা প্রমাণ করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1074 (ET: N/A)]*

30. **Draw a circuit to relaise the following expression using AND, OR gates and inverter: $F = \bar{A}BC + A\bar{B}C + AB\bar{C}$** *[Sonali & Janata Bank Officer (IT/ICT) 2019 compact it 1104 (ET: AUST)]*

31. **Describe the seven basic logic gates and show their truth table.** *[Combined Bank Senior Officer (IT/ICT) 2019 compact it 1113 (ET: DU)]*

32. **Why binary logic is used for digital system?** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1188 (ET: N/A)]*

## Number Systems & Base Conversions (24)

1. **(a) Convert the following number:**
   **i. Decimal number 9 to binary number.**
   **ii. Octal number 2671 to decimal number.**
   **iii. Octal number 756 to hexadecimal number.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1447 (ET: N/A)]*

2. **(b) Represent - 25 in 8 bit binary using 2's complement.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1350 (ET: N/A)]*

3. **ডেসিমেল ৬১ এর বাইনারি মান কত?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1450 (ET: N/A)]*

4. **$(\text{CDAB})_{16}$ কে অক্টাল এ রূপান্তর কর।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 381 (ET: BUET)]*

5. **Convert Decimal to Octal (423)_{10} and Decimal to Hexadecimal (3000)_{10}.** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 392 (ET: BUET)]*

6. **কোড কী? BCD এবং Binary কোডের মধ্যে পার্থক্য লিখুন। তিনভিত্তিক সংখ্যা পদ্ধতি সম্পর্কে ব্যাখ্যা করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 407 (ET: N/A)]*

7. **(9\text{D.AB}6)_{16} ও (306.51)_{10} যোগ করুন এবং ফলাফল বাইনারীতে প্রকাশ করুন। (110101) কোন সংখ্যা পদ্ধতির সংখ্যা হতে পারে বলে মনে করেন?** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 407 (ET: N/A)]*

8. **Explain Binary digits, logical levels and digital waveforms using timing diagram.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 665 (ET: N/A)]*

9. **Convert: (1741)_{10} = (?)_{16}** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 701 (ET: BUET)]*

10. **Number Conversion: (i) (4673)_8 = (?)_{16} (ii) (7491)_{10} = (?)_{16}** *[CAAB Assistant Programmer (AP) 2022 compact it 725 (ET: N/A)]*

11. **Computer এর Binary পদ্ধতি কোন সংখ্যার উপর প্রতিষ্ঠিত?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

12. **BCD code – এ কতগুলি বিট থাকে?** *[DMLC Assistant Teacher (ICT) 2021 compact it 826 (ET: N/A)]*

13. **(b) Convert the following Octal number into Decimal and Hexadecimal: (651)_8** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 891 (ET: N/A)]*

14. **Binary Number system এর Base কত?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 943 (ET: N/A)]*

15. **(i) (1\text{AC})_{16} = (?)_{2}\text{ and }(?)_{10}** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 974 (ET: BUET)]*

16. **(ii) What is the Excess-3 code of 1010?** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 974 (ET: BUET)]*

17. **There are different number systems. i. Convert (10010.101)_2 = (?)_{10} ii. (543)_{10} = (?)_{16}** *[Sonali & Janata Bank Officer (IT) 2020 compact it 989 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

18. **Convert (343)_{10} to binary and Hexadecimal.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1034 (ET: BUET)]*

19. **(1111001101011)_2 কে অক্টাল ও হেক্সাডেসিম্যালে রূপান্তর করুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1038 (ET: DPI)]*

20. **(ক) Parity bit কী? $(17.625)_{10}$ কে বাইনারি এবং $(\text{AB.C})_{16}$ কে দশমিক সংখ্যায় প্রকাশ করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1071 (ET: N/A)]*

21. **(খ) $(3\text{D}.4\text{C})_{16}$ এবং $(514.6)_8$ কে বাইনারি সংখ্যায় পরিবর্তন করে যোগ এবং যোগফল হেক্সাডেসিমালে প্রকাশ করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1071-1072 (ET: N/A)]*

22. **(b) Solve the problem: $3.5_{10} + 2.4_8 + 1A.7_{16} = (?)_{16}$** *[BPSC Assistant Programmer (CSE) 2019 compact it 1132-1134 (ET: N/A)]*

23. **$(12345)_{10} = (?)_8$** *[Bangladesh Bank Assistant Programmer 2019 compact it 1156 (ET: DU)]*

24. **Convert $(2345)_{10}$ to Hexadecimal and $(\text{ABCD})_{16}$ to octal number.** *[ICT Ministry Assistant Programmer 2017 compact it 1240 (ET: N/A)]*

## Combinational Circuits (Adders, Encoders, MUX) (23)

1. What is the difference between a Multiplexer and a Demultiplexer? Explain one practical application of each in digital systems. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

2. **Design a Full Adder circuit using basic logic gates (AND, OR, NOT). Draw the truth table, derive the Boolean expressions for the Sum (S) and Carry (C_{out}), and draw the complete circuit diagram.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1423 (ET: E-Zone)]*

3. **What is half adder?** *[National Legal Aid Services Organization Assistant Maintenance Engineer 18.10.2025 compact it 1450 (ET: N/A)]*

4. **Design a full adder using NAND gates only.** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1439 (ET: BUET)]*

5. **Design a full adder using two half adders and an OR gate?** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1339 (ET: N/A)]*

6. **Multiplexing:** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 418 (ET: BUET)]*
```
          +-----------+
    A ---|>|---| I_3       |
          | I_2  4x1  |--- F(A, B, C)
    1 --------| I_1  MUX  |
    0 --------| I_0       |
          +-----------+
                 |  |
                 B  C
                 |  |
                S_1 S_0
```

7. **Truth Table from the following circuit (2-bit input A, B full adder with carry bit C_{in}).** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 314 (ET: N/A)]*

8. **একটি 2:4 ডিকোডার ও একটি OR গেট ব্যবহার করে একটি হাফ এডার ডিজাইন কর।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 382 (ET: BUET)]*

9. **Design 6 \times 1 MUX by using 2 \times 1 MUX** *[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 460 (ET: BUET)]*

10. **What is Half Adder circuit? Expalin with block diagram with logic circuit.** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 497 (ET: N/A)]*

11. **Desugn a logic circuit that counts the number of 1s in 3 inputs (A, B, C) and outputs a two-bit binary number representing that count of 1s?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 683 (ET: N/A)]*

12. **একটি 4:1 Multiplexer এর Logic Diagram অঙ্কন করে দেখান?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 697 (ET: DPI)]*

13. **How do you design a logic circuit that has three inputs A, B, C and whose output will be high only when majority of the inputs are high. (a) Find truth table and (b) Show SOP and POS equation.** *[EGCB Assistant Engineer (CSE) 2022 compact it 715 (ET: BUET)]*

14. **Design a 8\times 1 MUX and explain working procedure.** *[Microcredit Regulatory Authority (MRA) Assistant Maintenance Engineer 2022 compact it 720 (ET: N/A)]*

15. **(a) Draw the logic diagram of Half-Adder the truth table of Full-Adder and use half Adder (S) and basic gates to build a Full-Adder.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 797 (ET: N/A)]*

16. **Circuit of the following figure uses 4:1 Multiplexer, what is output of the function f?** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 857 (ET: N/A)]*

17. **For 7 segments display the input is abcdefg. When a decimal digit or value is display then its equivalent segment is high. (i) Draw logic circuit for 2-to-4 Line Decoder/De-Multiplexer** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 927-928 (ET: CTI)]*

18. **4:1 MUX এর লজিক ডায়াগ্রাম ডিজাইন করুন এবং Selection Line দুটির কাজ লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1041 (ET: DPI)]*

19. **Half adder এর সাহায্যে Full adder বাস্তবায়ন করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1080 (ET: N/A)]*

20. **(খ) Multiplexer কি? চিত্রসহ একটি Multiplexer এর গঠন ও কাজ বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1098 (ET: N/A)]*

21. **দুটি 1-bit full adder এর মাধ্যমে 2-bit full adder তৈরি করুন।** *[NPCBL Junior Technical Engineer 2019 compact it 1149 (ET: BUET)]*

22. **চিত্রে প্রদর্শিত 7 segment display দেওয়া আছে এখন 7 ও 2 display এর জন্য কোন LED High হবে?** *[NPCBL Junior Technical Engineer 2019 compact it 1149 (ET: BUET)]*

23. **Design $4\times1$ MUX with two selection line & 4 input (A,B,C,D) of the following sum of product (0,3,4,5,6,7) and CD as a selection line.** *[BTCL Assistant Manager (Technical) 2017 compact it 1253-1254 (ET: N/A)]*

## Karnaugh Map (K-Map) (19)

1. Simplify the following boolean expression using 4 variable K-map: F(A,B,C,D) = ∑ m(0,3,5,7,8,10,11,12,13,14,15). Draw the K-map grid, clearly show your groupings (loops), and write the final simplified Sum-of-Products (SOP) expression. [SO IT 25-07-2026]

2. **Simplification using K-map?** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

3. **(a) Consider the following logic circuit-** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1350 (ET: N/A)]*
 * **(i) Derive the Boolean expression algebraically for T1 through T4. Derive F1 and F2 as function of the three inputs A, B and C.**
 * **(ii) Use K-map to simplify these expressions F1 and F2, and show that they are equivalent to the ones obtained in (i).**

4. **b) Use the Karnaugh Map to simplify the following function. f(A,B,C) = A'B'C' + A'B'C + A'BC + A'BC' + ABC' + ABC** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1343 (ET: N/A)]*

5. **Show minimal function using K-Map: F(A, B, C, D) = \sum(2, 8, 9, 11, 13, 15).** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 391 (ET: BUET)], [BICIC Assistant Programmer 2022 compact it 632 (ET: BUET)]*

6. **6.8 Simplify the following boolean expression using 4 variable K-map: F(A,B,C,D)= \sum m(0,3,5,7,8,10,11,12,13,14,15). Draw the K-map grid, clearly show your groupings (loops), and write the final simplified Sum-of-Products (SOP) expression.** *[Bangladesh Bank Senior Officer (IT), Grade-9 (Job ID-25104) 2024 (ET: N/A)]*

7. **(b) Simplify the following Boolean function using K-map.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 489 (ET: N/A)]*

8. **Minimize the following function in SOP minimal form using K-map:** *[Teletalk Assistant Manager (IT) 2023 compact it 465 (ET: N/A)]*

9. **Simplify F(A, B, C, D) = ACD + AB + \overline{D} + AC\overline{D} using K-map and draw the logic circuits.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)]*

10. **Simplify using K-map with logic circuit.** *[Petrobangla Assistant Manager (IT) 16.09.2022 compact it 713 (ET: BUET)]*

11. **(a) A comparator has two inputs A = A_1 A_0 and B = B_1 B_0 and one output F. Output becomes one whenever the value of A > B (i) Show the truth table for F. (ii) Simplify the function using K-Map.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 798 (ET: N/A)]*

12. **Simplify \bar{A}\,\bar{B}\,\bar{C} + ABC + A\bar{B}\,\bar{C} using K-map.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 859 (ET: N/A)]*

13. **Simplify the following K-map: (i) K-map for function F (ii) K-map for function F** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 879 (ET: BUET)]*

14. **Draw the k-map for the equation:** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922 (ET: N/A)]*
   F = A'B'C'D' + A'B'CD' + A'BCD' + A'BCD + AB'C'D' + AB'CD' + ABCD' + ABCD

15. **F = \bar{A}\bar{B}\bar{C} + A\bar{B}\bar{C} + \bar{A}\bar{B}C + \bar{A}BC + ABC, Simplify using K-map with logic circuit.** *[Janata Bank Ltd SO ( Assistant Network Engineer) 2020 compact it 1010-1011 (ET: N/A)]*

16. **f(a, b, c, d) = \bar{a}b\bar{c}\bar{d} + \bar{a}\bar{b}\bar{c}d + \bar{a}b\bar{c}d + ab\bar{c}\bar{d} কে K-map এর সাহায্যে Simplify করুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1038-1039 (ET: DPI)]*

17. **(গ) Min term কী? K-map-এর সাহায্যে সরল করুন: $\bar{A}\bar{B}\bar{C} + \bar{A}B + AB\bar{C} + AC$** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1074 (ET: N/A)]*

18. **Simplify the expression: $F(A,B,C) = \bar{A}\bar{B}\bar{C} + \bar{A}B + AB\bar{C} + AC$, using k-map.** *[DESCO Sub-Assistant Engineer (CSE) 2019 compact it 1119 (ET: BUET)]*

19. **(a) Simplify $F(A,B,C,D) = ACD+AB+\bar{D}+A\bar{C}D$ using K-map and draw the simplified circuit diagram.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1132-1134 (ET: N/A)]*

## Boolean Algebra & De Morgan’s Theorem (18)

1. **(a) State De-Morgan’s law with an appropriate example.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 488 (ET: N/A)]*

2. **AB + (A(\overline{BC}))(AC + \overline{B}C)** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 643 (ET: BUET)]*

3. **Simplify Y = A\bar{B} + \overline{(\bar{A} + B)}C in digital logic design.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 671 (ET: N/A)]*

4. **X+\bar{X}Y = ?** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

5. **(ক) নিম্নলিখিত Boolean Function টি সংক্ষিপ্ত আকারে লিখুন: F(A, B, C, D) = \bar{A}\,\bar{B}\bar{C} + \bar{B}C\bar{D} + \bar{A}\bar{B}C\bar{D} + A\bar{B}\bar{C}** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 773 (ET: N/A)]*

6. **(b) Use Algebraic manipulation to convert the following equation to sum-of-product form: y(z + \bar{w}) + x(\bar{z} + \bar{y})\,\bar{w} + (zw)(\overline{xy})** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 797 (ET: N/A)]*

7. **Simplify the Boolean expression as possible: AB\bar{C}D + ABCD + \bar{A}BD** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 867 (ET: BUET)]*

8. **Simplify the Boolean expression: AB\bar{C}D + \bar{A}\bar{B}\bar{C}D + ABCD + \bar{A}\bar{B}CD + ABC\bar{D} + \bar{A}\bar{B}C\bar{D}** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 876 (ET: BUET)]*

9. **(b) Simplify the following expression using Boolean Algebra: \bar{x}\bar{y}z + \bar{x}yz + x\bar{y}** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 890 (ET: N/A)]*

10. **(a) Simplify the following Boolean expression: (x+y+xy)(x+z)** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 890-891 (ET: N/A)]*

11. **AB\bar{C}D + \bar{A}BD + ABCD convert it into minimum lateral.** *[SGFL Assistant General Engineer 2021 compact it 935 (ET: BUET)]*

12. **Simply the following function: ABCD + \bar{A}BD + AB\bar{C}D** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 972 (ET: BUET)]*

13. **De-Morgans Law গুলো বর্ণনা করুন।** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1022 (ET: N/A)]*

14. **(ক) বুলিয়ান অ্যালজেবরার সাহায্যে সরল করুন: $\overline{x+y(x+z)}$** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1073 (ET: N/A)]*

15. **(খ) প্রমাণ করুন: $A \oplus B = AB + \bar{A}\bar{B}$** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1073-1074 (ET: N/A)]*

16. **(ক) তিন চলকের De Morgan's উপপাদ্য দুইটি লিখুন এবং Truth table-এর সাহায্যে প্রমাণ করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1074 (ET: N/A)]*

17. **Simplify the following Boolean expression: $F = \bar{A}C + A\bar{B} + B\bar{C} + ABC$** *[DESCO Assistant Engineer (CSE) 2019 compact it 1118 (ET: BUET)]*

18. **Construct a truth table for the following function: $(r \lor (q \land \neg p)) \land \neg(r \land (q \land \neg p))$ is the same as $r \oplus (q \land \neg p)$ where $\lor = \text{OR}, \land = \text{AND}, \neg = \text{NOT}, \oplus = \text{XOR}$** *[Combined 3 Banks Assistant Programmer 2018 compact it 1198 (ET: N/A)]*

## Sequential Circuits (Latches & Flip-Flops) (17)

1. **What is Multiplexer? Difference between D latch and D flip-flop?** *[BCIC Assistant Programmer 14.02.2025 compact it 1328 (ET: BUET)]*

2. **Difference between combinational and sequential circuits.** *[Bangladesh Livestock Research Institute Assistant Maintenance Engineer 20.05.2023 compact it 498 (ET: N/A)]*

3. **(b) Design a 4-bit ring counter using flip-flops. Write down its working principle using.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 687 (ET: N/A)]*

4. **(খ) Combinational এবং Sequential circuit এর মধ্যে পার্থক্য ডায়াগ্রাম সহকারে লিখুন।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 773 (ET: N/A)]*

5. **Given a 100MHz clock signal derive a circuit using T-flip flops of generate 50MHz and 25MHz clock signals. Draw a timing diagram for all the three clock signal.** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823-824 (ET: BUET)]*

6. **What is the difference between latch and flip-flop?** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 874 (ET: N/A)]*

7. **There are different types of clocks available in the market. What type of clock will you use to reduce the cost of SGFL Company?** *[SGFL Assistant General Engineer 2021 compact it 937 (ET: BUET)]*

8. **(ii) R-S Flip-flop এর সত্যস্য সারণি ও বৈশিষ্ট আলোচনা করুন।** *[BPSC Assistant Network Engineer 2020 compact it 959-960 (ET: N/A)]*

9. **MOD-6 বাইনারি কাউন্টার এর Block Diagram অংকন করুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1039 (ET: DPI)]*

10. **(গ) Flip-Flop কী? একটি Multiplexer এর কার্যপদ্ধতি ব্যাখ্যা করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1075 (ET: N/A)]*

11. **Ripple counter কী? একটি তিন বিটের Asynchronous up ripple counter এর গঠন লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1077-1078 (ET: N/A)]*

12. **(c) Draw the circuit diagram of a mod-10 asynchronous ripple up counter and explain its operation.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1132-1134 (ET: N/A)]*

13. **Difference between Register and Latch.** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1151 (ET: KUET)]*

14. **Main difference between Combinational and Sequential circuits.** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1151 (ET: KUET)]*

15. **What is synchronous? Why sequential circuit use synchronization.** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1189 (ET: N/A)]*

16. **What is the difference between flip-flop and latch with figure?** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1190-1191 (ET: N/A)]*

17. **What is the difference between latch and flip-flop?** *[Bangladesh Bank Assistant Maintenance Engineer 2017 compact it 1227 (ET: N/A)]*

## Logic Families (TTL vs CMOS) (6)

1. **(c) Compare TTL and CMOS logic family in terms of-** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1351 (ET: N/A)]*
 * **(i) Speed**
 * **(ii) Noise**
 * **(iii) Power consumption.**

2. **Describe the important characteristics of digital IC's.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 556 (ET: BIBM)]*

3. **Difference between Analog and Digital Circuit.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 873 (ET: N/A)]*

4. **(c) What is fan-in and fan out?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 891 (ET: N/A)]*

5. **Sources of transient fault and permanent fault in a digital system consists of hardware and software? Example based on Hardware and software.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)]*

6. **What is IC? Advantages of IC over discrete component circuit. Why do IC's need small power for their operation?** *[BTRC Assistant Director (Technical) 2019 compact it 1147 (ET: N/A)]*

## 2's Complement & Binary Arithmetic (4)

1. **2-এর পরিপূরক পদ্ধতি কী? 2-এর পরিপূরক পদ্ধতি ব্যবহার করে (-15)_{10} থেকে (+11)_{10} বিয়োগ করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 406 (ET: N/A)]*

2. **BCD Addition: 00010011 + 00100110** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 644 (ET: BUET)]*

3. **(a) For two 8bit binary numbers. What will be output values in 2’s complement format: (i) (10000000+10000000) (ii) (11111111-01111111)** *[BPSC Assistant Programmer (CSE) 2019 compact it 1138 (ET: N/A)]*

4. **How many bits have to change to convert int A to int B. Sample A=31 and B=14.** *[Combined Bank (HBFC and BKB) Assistant Programmer 2018 compact it 1164 (ET: N/A)]*

## Finite State Machines (FSM) (1)

1. **A traffic signal cycles from RED to YELLOW, YELLOW to GREEN and GREEN to RED. In each cycle RED is turned for 100 seconds, YELLOW is turned for 40 seconds and GREEN is turned for 80 seconds. The traffic has to be implemented using FSM. The only input to this FSM is a clock of 10 second period. The minimum number of flip-flops require to implement this FSM is?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1455 (ET: BUET)]*
