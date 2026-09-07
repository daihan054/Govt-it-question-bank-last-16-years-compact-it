<!-- TOC START -->
**Table of Contents** — 6 subtopics · 79 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Number Systems & Binary Arithmetic](#number-systems--binary-arithmetic-45) | 45 |
| 2 | [Logic Gates & Universal Gates](#logic-gates--universal-gates-16) | 16 |
| 3 | [Sequential Circuits (Flip-Flops)](#sequential-circuits-flip-flops-6) | 6 |
| 4 | [Digital Logic & Number Systems](#digital-logic--number-systems-6) | 6 |
| 5 | [Boolean Algebra & Simplification](#boolean-algebra--simplification-4) | 4 |
| 6 | [Combinational Circuits (MUX, Decoder)](#combinational-circuits-mux-decoder-2) | 2 |

<!-- TOC END -->

---

## Number Systems & Binary Arithmetic (45)

1. **What is the 2's complement of (65)_{16} number?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xix (ET: DU)]*
   (a) 10011011
   (b) 10011010
   (c) 00011011
   (d) 10011100
answer: A
explanation: হেক্সাডেসিমেল $(65)_{16}$-এর ৮-বিট বাইনারি হলো $01100101$। এর ১-এর পরিপূরক $10011010$ এবং এর সাথে ১ যোগ করলে ২-এর পরিপূরক পাওয়া যায় $10011011$।

2. **What is the result of the binary sum 10101+1011?** *[Combined Bank Officer (IT) 04.10.2024 compact it 15 (ET: BIBM)]*
   (a) 10000
   (b) 101010
   (c) 100000
   (d) 111100
answer: C
explanation: বাইনারি যোগ: $10101_2 (২১) + 1011_2 (১১) = 100000_2 (৩২)$।

3. **A computer system needs to store 100 different symbols. In this case, how many bits of data is required for each symbol?** *[NPCBL Executive Trainee (Software) 2023 compact it 38 (ET: N/A)]*
   a) 4
   b) 5
   c) 6
   d) 7
answer: D
explanation: ১০০টি ভিন্ন প্রতীক এনকোড করতে $\lceil \log_2(100) \rceil = 7$ টি বিট প্রয়োজন ($2^6 = 64$ যথেষ্ট নয়, $2^7 = 128$ প্রতীক ধারণ করতে পারে)।

4. **The greatest negative number which can be stored in computer that has 8-bits work length and use 2's complement arithmetic is ______.** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 23 (ET: BIBM)]*
   (a) -256
   (b) -127
   (c) -255
   (d) -128
answer: D
explanation: ৮-বিট ২-এর পরিপূরক (2's complement) পদ্ধতিতে ঋণাত্মক সংখ্যার সর্বনিম্ন বা পরম মানের বিচারে সর্ববৃহৎ সীমা হলো $-2^7 = -128$ (রেঞ্জ: $-128$ থেকে $+127$)।

5. **(1111111101)_2 = (?)_{10}** *[BREB Assistant Programmer 2023 compact it 32 (ET: N/A)]*
   (a) 1511
   (b) 1510
   (c) 1500
   (d) 1537
answer: A
explanation: গাণিতিকভাবে $(1111111101)_2 = 2^{10} - 1 - 2 = 1021_{10}$। প্রশ্ন বা অপশনের মুদ্রণজনিত বিভ্রান্তি থাকলেও নিকটবর্তী/প্রশ্নব্যাংক উত্তর হিসেবে (a) নির্দেশ করা হয়, তবে প্রকৃত মান ১০২১।

6. **Find out 2's complement value of 11100101.** *[BREB Assistant Programmer 2023 compact it 32 (ET: N/A)]*
   (a) 00011011
   (b) 00011111
   (c) 0011001
   (d) 00011010
answer: A
explanation: $11100101$-এর ১-এর পরিপূরক $00011010$; এর সাথে ১ যোগ করলে ২-এর পরিপূরক মান পাওয়া যায় $00011011$।

7. **(2023)_{10} = (?)_{16}** *[BREB Assistant Programmer 2023 compact it 33 (ET: N/A)]*
   (a) 7E0
   (b) 7D0
   (c) 8E0
   (d) 7E7
answer: D
explanation: $2023$-কে ১৬ দ্বারা ক্রমাগত ভাগ করলে ভাগশেষগুলো নিচ থেকে উপরে পাওয়া যায় ৭, ১৪ (E) এবং ৭; অর্থাৎ $(2023)_{10} = (7E7)_{16}$।

8. **A computer has main memory of 960 Kb. What is the exact number of bytes contained in this memory?** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 56 (ET: N/A)]*
   (ক) 960x8
   (খ) 960x1000
   (গ) 960x1024
   (ঘ) 960x1024x1024
answer: C
explanation: ১ কিলোবাইট (KB) = ১০২৪ বাইট; সুতরাং ৯৬০ KB মেমোরিতে মোট বাইটের সঠিক সংখ্যা হলো $960 \times 1024$ বাইট।

9. **Which of the following numbers is the next sequence number of 77_8 in Octal number system?** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 44 (ET: N/A)]*
   (ক) 88
   (খ) 80
   (গ) 100
   (ঘ) 99
answer: C
explanation: অক্টাল সংখ্যা পদ্ধতিতে সর্বোচ্চ অঙ্ক ৭; তাই $77_8$-এর সাথে ১ যোগ করলে পরবর্তী সংখ্যাটি হবে $100_8$ ($7+1 = 10_8$, কেরি ১ যোগ হয়ে পুনরায় $7+1 = 10_8 \implies 100_8$)।

10. **If a processor has 8-bit register, what is the value of (11111111)_2 represented in 2's complement form-** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 47 (ET: N/A)]*
    (ক) 255
    (খ) -1
    (গ) 256
    (ঘ) 0
answer: B
explanation: ৮-বিট ২-এর পরিপূরক পদ্ধতিতে সাইন বিট ১ (ঋণাত্মক); এর মান বের করতে ১-এর পরিপূরক ($00000000$) করে ১ যোগ করলে পাই ১, ফলে চূড়ান্ত মান $-1$।

11. **নিম্নের কোন লজিক অপারেশনটি সঠিক?** *[BDCCL Assistant Manager (Transmission) 2022 compact it 70 (ET: N/A)], [BDCCL Assistant Manager (Transmission) 2022 compact it 34 (ET: BUET)]*
    (ক) A+A = 1
    (খ) AA = 0
    (গ) A+1 = 1
    (ঘ) A+1 = 0
    **Ans: গ**
answer: C
explanation: বুলিয়ান অ্যালজেব্রার মৌলিক সূত্রানুসারে যেকোনো ইনপুটের সাথে ১-এর লজিক্যাল OR করলে আউটপুট সর্বদা ১ হয় ($A + 1 = 1$)।

12. **বিসিডি কোডে বিট সংখ্যা কত?** *[BDCCL Assistant Manager (Transmission) 2022 compact it 70 (ET: N/A)], [BDCCL Assistant Manager (Transmission) 2022 compact it 34 (ET: BUET)]*
    (ক) 1
    (খ) 2
    (গ) 8
    (ঘ) 4
    **Ans: ঘ**
answer: D
explanation: বিসিডি (Binary Coded Decimal বা BCD 8421) কোডে প্রতিটি দশমিক অঙ্ককে প্রকাশ করতে ৪টি করে বাইনারি বিট ব্যবহৃত হয়।

13. **বাইনারি পদ্ধতির যোগে 1+1+1 = কত?** *[BDCCL Assistant Manager (Transmission) 2022 compact it 70 (ET: N/A)], [BDCCL Assistant Manager (Transmission) 2022 compact it 34 (ET: BUET)]*
    (ক) 10
    (খ) 11
    (গ) 101
    (ঘ) 111
    **Ans: খ**
answer: B
explanation: বাইনারি যোগে $1 + 1 + 1 = 3_{10} = 11_2$ (অর্থাৎ যোগফল ১ এবং কেরি ১)।

14. **bit এর সংখ্যার বিচারে নিচের কোন ক্রমটি সঠিক?** *[BDCCL Assistant Manager (Transmission) 2022 compact it 71 (ET: N/A)], [BDCCL Assistant Manager (Transmission) 2022 compact it 35 (ET: BUET)]*
    (ক) \text{byte} > \text{GB} > \text{KB} > \text{TB}
    (খ) \text{byte} > \text{KB} > \text{GB} > \text{TB}
    (গ) \text{byte} > \text{KB} > \text{TB} > \text{GB}
    (ঘ) \text{byte} > \text{TB} > \text{GB} > \text{KB}
    **Ans: খ**
answer: B
explanation: মেমোরি পরিমাপের স্বাভাবিক ক্রম হলো Byte < KB < MB < GB < TB; প্রশ্নে প্রতীকচিহ্ন ছাপার বিচ্যুতি থাকলেও ধারাবাহিকতার বিচারে (খ) সঠিক।

15. **Suppose you have an 8-bit binary number N. Which of the following operations does not change its lower 4 bits?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 131 (ET: N/A)]*
    a) An exclusive logical sum of N with 0Fh
    b) A negative logical product of N with 0Fh
    c) A logical product of N with 0Fh
    d) A logical sum of N with 0Fh
answer: C
explanation: `0Fh` এর বাইনারি হলো `00001111`। $N$-এর সাথে এর লজিক্যাল প্রোডাক্ট বা AND অপারেশন ($N \text{ AND } 0Fh$) করলে লোয়ার ৪ বিটের ক্ষেত্রে $x \text{ AND } 1 = x$ থাকে, অর্থাৎ লোয়ার ৪ বিটের কোনো পরিবর্তন হয় না।

    **Consider the following relational database–**
    *Order (OrderNumber, OrderDate, Promised Date)*
    *Orderline (OrderNumber, ProductID, QuantityOrdered)*
    *Product (Product ID Description, Price)*
    What types of relationship exists in the following Order line table? *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 132 (ET: N/A)]*
    a) One to One
    b) One to Many
    c) Many to Many
    d) Many to One
answer: C
explanation: একটি অর্ডারে একাধিক প্রোডাক্ট থাকতে পারে এবং একটি প্রোডাক্ট একাধিক অর্ডারে অন্তর্ভুক্ত হতে পারে; Order ও Product-এর মধ্যকার এই Many-to-Many সম্পর্ককে বাস্তবায়ন করতে Orderline টেবিলটি তৈরি করা হয়েছে।

16. **Which of the following values is the correct value of this hexadecimal code 1F.01B?** *[BREB Assistant General Manager (O&M/E&C) 2021 compact it 137 (ET: N/A)]*
    a. 35.0065918
    b. 32.0065918
    c. 31.0065918
    d. 30.0065918
answer: C
explanation: হেক্সাডেসিমেল পূর্ণসংখ্যা $1F_{16} = (1 \times 16 + 15) = 31$; এবং ভগ্নাংশ $.01B_{16} = 0/16 + 1/256 + 11/4096 \approx 0.0065918$; সুতরাং মোট মান ৩১.০০৬৫৯১৮।

17. **Suppose you have an 8-bit binary number N. Which of the following operations does not change its lower 4 bits?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 89 (ET: N/A)]*
    a. An exclusive logical sum of N with 0Fh
    b. A logical product of N with 0Fn
    c. A negative logical product of N with 0Fn
    d. A logical sum of N with 0Fh
answer: B
explanation: `0Fh` (`00001111`) এর সাথে $N$-এর লজিক্যাল প্রোডাক্ট বা AND অপারেশন ($N \text{ AND } 0Fh$) করলে লোয়ার ৪ বিটের মান অপরিবর্তিত থাকে ($x \text{ AND } 1 = x$)।

18. **Suppose, Y is an integer variable whose value is either 0 or 1. Which of the following is the equivalent of the statement. if(Y==0) Y=1; else Y=0;?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 90 (ET: N/A)], [Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 167 (ET: N/A)]*
    a. Y = 1+Y
    b. Y = 1-Y
    c. Y = Y-1
    d. Y = 1%Y
answer: B
explanation: $Y = 0$ হলে $1 - 0 = 1$, এবং $Y = 1$ হলে $1 - 1 = 0$; অর্থাৎ $Y = 1 - Y$ স্টেটমেন্টটি প্রদত্ত শর্তের সমতুল্য টগল অপারেশন সম্পন্ন করে।

19. **Among the following which is not a divisor of - (1001011011110000000)_2?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 166 (ET: N/A)]*
    a) (2)_{10}
    b) (64)_{10}
    c) (128)_{10}
    d) (256)_{10}
answer: D
explanation: প্রদত্ত বাইনারি সংখ্যাটির শেষে ৭টি শূন্য (trailing zeros) রয়েছে, যার অর্থ সংখ্যাটি সর্বোচ্চ $2^7 = 128$ দ্বারা বিভাজ্য; এটি $2^8 = 256$ দ্বারা বিভাজ্য নয়।

20. **Suppose you have an 8-bit binary number N. Which of the following operations does not change its lower 4 bits?** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 183 (ET: N/A)]*
    a) An exclusive logical sum of N with 0Fh
    b) A logical sum of N with 0Fh
    c) A negative logical product of N with 0Fh
    d) A logical product of N with 0Fh
answer: D
explanation: $N$ এর সাথে `0Fh` (`00001111`)-এর লজিক্যাল প্রোডাক্ট (AND) অপারেশনে লোয়ার ৪ বিটের মান অবিকৃত থাকে ($x \text{ AND } 1 = x$)।

21. **Which one is the binary representation of (1234567)_{10}?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 152 (ET: DU)]*
    a) 100101101011010000000
    b) 1101011011111010001010
    c) 1001011010110100000111
    d) 111111111011010000110
answer: C
explanation: ১২৩৪৫৬৭ একটি বিজোড় সংখ্যা, তাই এর বাইনারি মানের সর্বশেষ বিট অবশ্যই ১ হতে হবে (একমাত্র অপশন 'c'-এর শেষ বিট ১)। গাণিতিকভাবে $(1234567)_{10} = 1001011010110100000111_2$।

22. **Convert the binary number (1011010)_2 into hexadecimal?** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 172 (ET: N/A)]*
    a) 5B
    b) 5F
    c) 5A
    d) 5C
answer: C
explanation: বাইনারি সংখ্যাটিকে ৪-বিট করে গ্রুপ করলে পাই: $0101_2 = 5$ এবং $1010_2 = A$; অর্থাৎ হেক্সাডেসিমেল মান $5A_{16}$।

23. **‘b’ এর ASCII value কত?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 186 (ET: N/A)]*
    A) 66
    B) 98
    C) 3000
    D) 1
answer: B
explanation: স্ট্যান্ডার্ড আসকি (ASCII) টেবিলে ছোট হাতের 'a'-এর মান ৯৭ এবং ছোট হাতের 'b'-এর মান ৯৮ (বড় হাতের 'B' হলো ৬৬)।

24. **10000000 এর বাইনারী নম্বরটির 2's complement ফরম্যাটের মান কত (৮ বিট)?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)]*
    A) 0
    B) 128
    C) -128
    D) 256
answer: C
explanation: ৮-বিট সাইনড ২-এর পরিপূরক পদ্ধতিতে $10000000_2$ সংখ্যাটির মান হলো $-2^7 = -128$।

25. **Number of bits in 'BCD' code used in computing are-** *[Probashi Kallyan Bank Programmer: 2019 compact it 209 (ET: AUST)]*
    A) seven bits
    B) twelve bits
    C) eighteen bits
    D) six bits
answer: D
explanation: কম্পিউটিংয়ের প্রারম্ভিক আলফানিউমেরিক বিসিডি কোডিং সিস্টেমে (IBM BCDIC) অক্ষর ও সংখ্যা উপস্থাপনের জন্য ৬টি বিট (২টি জোন বিট ও ৪টি নিউমেরিক বিট) ব্যবহৃত হতো।

26. **Number systems used in the computer is known as:** *[BTRC Sub-Assistant Director (Technical) 2019 compact it 199 (ET: IBA)]*
    A. Octal System
    B. Decimal System
    C. Binary System
    D. Real System
answer: C
explanation: কম্পিউটারের ডিজিটাল ইলেকট্রনিক্স মূলত ০ ও ১ ভিত্তিক বাইনারি সংখ্যা পদ্ধতিতে (Binary System) কাজ করে।

27. **________ are the two symbols present in the binary number system.** *[BTRC Sub-Assistant Director (Technical) 2019 compact it 200 (ET: IBA)]*
    A. 1 and 2
    B. 0 and 1
    C. 8 and 9
    D. 5 and 6
answer: B
explanation: বাইনারি সংখ্যা পদ্ধতির ভিত্তি হলো ২ এবং এতে কেবল দুটি প্রতীক '0' এবং '1' উপস্থিত থাকে।

28. **How many unique signs could be specified by using ASCII-8?** *[BTRC Sub-Assistant Director (Technical) 2019 compact it 201 (ET: IBA)]*
    A. 128
    B. 256
    C. 512
    D. 65536
answer: B
explanation: আসকি-৮ (ASCII-8) কোডে ৮টি বিট ব্যবহৃত হয়, যার মাধ্যমে সর্বোচ্চ $2^8 = 256$ টি অনন্য অক্ষর বা চিহ্ন নির্দিষ্ট করা যায়।

29. **Which one of the following is equivalent hexadecimal number of (734)_8?** *[BTRC Sub-Assistant Director (Technical) 2019 compact it 202 (ET: IBA)]*
    A. C1D
    B. D1C
    C. 1CD
    D. 1DC
answer: D
explanation: $(734)_8$-কে প্রথমে ৩-বিট বাইনারিতে রূপান্তর করলে $111011100_2$ পাওয়া যায়; এরপর ডানদিক থেকে ৪-বিট করে সাজালে $0001\ 1101\ 1100_2 = (1DC)_{16}$।

30. **A nibble is equal to:** *[BREB Assistant Junior Engineer (IT) 2019 compact it 219 (ET: N/A)]*
    A) 4-bits
    B) 6-bits
    C) 8-bits
    D) 16-bits
answer: A
explanation: ডিজিটাল কম্পিউটিংয়ে ৪টি বিটের সমষ্টিকে একত্রে ১ নিবল (1 Nibble = 4 bits বা আধা বাইট) বলা হয়।

31. **দশমিক পদ্ধতির সংখ্যা 300_{(10)} কে Hexadecimal এ রূপান্তর করলে কত হবে?** *[BPSC Assistant Network Engineer 2019 compact it 195 (ET: N/A)]*
    A) \text{C}3_{(16)}
    B) 12\text{C}_{(16)}
    C) \text{C}2_{(16)}
    D) \text{A}2\text{C}_{(16)}
answer: B
explanation: ৩০০-কে ১৬ দ্বারা ভাগ করলে ভাগফল ১৮ এবং ভাগশেষ ১২ (C); পুনরায় ১৬ দ্বারা ভাগ করলে ভাগফল ১ এবং ভাগশেষ ২; সুতরাং হেক্সাডেসিমেল মান $12C_{16}$।

32. **10101111 ও 00110011 এর Bitwise OR এর ফলাফল কত?** *[BPSC Assistant Network Engineer 2019 compact it 197 (ET: N/A)]*
    A) 10111111
    B) 00100011
    C) 01010101
    D) 11111111
answer: A
explanation: বিটওয়াইজ OR অপারেশনে যেকোনো একটি বিট ১ হলেই ফলাফল ১ হয়: $10101111 \text{ OR } 00110011 = 10111111$।

33. **(\text{B12})_{16} + (\text{5CA})_{16} = ?** *[BPSC Assistant Maintenance Engineer 2019 compact it 192 (ET: N/A)]*
    (a) (10\text{DC})_{16}
    (b) (\text{AFDC})_{16}
    (c) (1\text{FDC})_{16}
    (d) (\text{E1DC})_{16}
answer: A
explanation: হেক্সাডেসিমেল যোগ: $2 + A(10) = 12(C)$; $1 + C(12) = 13(D)$; $B(11) + 5 = 16 (0$ এবং কেরি $1)$; ফলে মোট যোগফল $(10DC)_{16}$।

34. **What is the largest decimal value that can be represented by 12 bits?** *[BPSC Assistant Maintenance Engineer 2019 compact it 194 (ET: N/A)]*
    (a) 1024
    (b) 2048
    (c) 2095
    (d) 4095
answer: D
explanation: ১২টি বিট দ্বারা আনসাইন্ড বাইনারিতে ০ থেকে শুরু করে সর্বোচ্চ $2^{12} - 1 = 4096 - 1 = 4095$ পর্যন্ত দশমিক মান প্রকাশ করা যায়।

35. **What is the binary of (68)_{10}?** *[Sonali & Janata Bank Assistant Programmer 2018 compact it 239 (ET: N/A)]*
    A) 01000100
    B) 10000100
    C) 00100100
    D) 00010100
answer: A
explanation: $68 = 64 + 4$; অর্থাৎ ৬৪-এর পজিশনে ১ এবং ৪-এর পজিশনে ১ বসালে এর ৮-বিট বাইনারি রূপ দাঁড়ায় $01000100$।

36. **1(one) nibble equal to—** *[Sonali & Janata Bank Assistant Programmer 2018 compact it 240 (ET: N/A)]*
    A) 1 but
    B) 2-bit
    C) 4-bit
    D) 8-bit
answer: C
explanation: ১ নিবল (1 Nibble) সর্বদা ৪ বিট (4-bit)-এর সমান।

37. **(2019)_{10} in Binary is ________.** *[Combined Bank Senior Officer (IT) 2018 compact it 221 (ET: DU)]*
    A) 0000011111100010
    B) 0000001111110011
    C) 0000001111110010
    D) 0000011111100011
answer: D
explanation: $2019 = 1024 + 512 + 256 + 128 + 64 + 32 + 2 + 1$; ১৬-বিট ফরম্যাটে সাজালে এর মান দাঁড়ায় $0000011111100011$।

38. **(11100010)_2 has a decimal value of ________.** *[Combined Bank Senior Officer (IT) 2018 compact it 222 (ET: DU)]*
    A) 252
    B) 225
    C) 226
    D) 220
answer: C
explanation: $(11100010)_2 = 2^7(128) + 2^6(64) + 2^5(32) + 2^1(2) = 226$।

39. **For some base r, the digits which are allowed in its representation are?** *[Combined 3 Bank Assistant Programmer 2018 compact it 229 (ET: N/A)]*
    A) Digit from 1 to r
    B) Digit from 0 to r-1
    C) Digit from 1 to r-1
    D) Digit form 0 to r
answer: B
explanation: যেকোনো বেস বা ভিত্তি $r$-এর সংখ্যা পদ্ধতিতে ব্যবহারযোগ্য অঙ্কগুলো সর্বদা $0$ থেকে $r-1$ পর্যন্ত বিস্তৃত থাকে (যেমন ডেসিমেলে ০ থেকে ৯, বাইনারিতে ০ থেকে ১)।

40. **The Ex-OR of this string 01010101 with 11111111 is ________.** *[Combined 3 Bank Assistant Programmer 2018 compact it 230 (ET: N/A)]*
    A) 10101010
    B) 00110100
    C) 01010101
    D) 10101001
answer: A
explanation: ১-এর সাথে যেকোনো বিটের এক্স-অর (XOR) করলে বিটটি ইনভার্ট বা উল্টে যায় ($0 \oplus 1 = 1, 1 \oplus 1 = 0$); ফলে $01010101 \oplus 11111111 = 10101010$।

41. **How many numerical bits of ASCII -8 codes?** *[BREB Assistant General Manager (IT) 2016 compact it 255 (ET: N/A)]*
    A) 2
    B) 4
    C) 8
    D) 16
answer: B
explanation: আসকি-৮ (ASCII-8) কোডের ৮টি বিটের মধ্যে ডানদিকের ৪টি বিটকে 'নিউমেরিক বিট' (Numeric bits) এবং বামদিকের ৪টি বিটকে 'জোন বিট' (Zone bits) বলা হয়।

42. **How many bits in Unicode?** *[BREB Assistant General Manager (IT) 2016 compact it 255 (ET: N/A)]*
    A) 4
    B) 8
    C) 16
    D) 32
answer: C
explanation: প্রথাগত পাঠ্যক্রম ও পরীক্ষায় ইউনিকোড (Unicode)-কে প্রমিতভাবে ১৬-বিট (16 bits) কোড হিসেবে বিবেচনা করা হয়, যা $2^{16} = 65,536$ টি ভিন্ন অক্ষর বা চিহ্ন ধারণ করতে পারে।

43. **On which number system computer does not work?** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 259 (ET: N/A)]*
    A) Binary
    B) Decimal
    C) Octal
    D) Hexadecimal
answer: B
explanation: কম্পিউটার হার্ডওয়্যার অভ্যন্তরীণভাবে কেবলমাত্র বাইনারি পদ্ধতিতে (০ ও ১ ভোল্টেজ স্তর) কাজ করে; এটি প্রত্যক্ষভাবে সরাসরি দশমিক সংখ্যা পদ্ধতিতে (Decimal) কাজ করে না।

44. **What is the Hexadecimal form of (2016)_{10}?** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 260 (ET: N/A)]*
    A) 5A0
    B) 7A0
    C) 5E0
    D) 7E0
answer: D
explanation: ২০১৬-কে ১৬ দ্বারা ক্রমাগত ভাগ করলে ভাগশেষগুলো নিচ থেকে উপরে সাজিয়ে পাই ৭, ১৪ (E) এবং ০; সুতরাং হেক্সাডেসিমেল রূপ $(7E0)_{16}$।

45. **When we subtract 3 from 2, the answer is-** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 261 (ET: N/A)]*
    A) 0001
    B) 1101
    C) 0101
    D) 1001
answer: D
explanation: $২ - ৩ = -১$; সাইন-ম্যাগনিটিউড (Sign-magnitude) পদ্ধতিতে ৪-বিট ফরম্যাটে ঋণাত্মক চিহ্নের জন্য MSB ১ এবং মানের (১) জন্য ০০১ ব্যবহার করলে ফলাফল দাঁড়ায় $1001$।

## Logic Gates & Universal Gates (16)

1. **Which one is a Universal logic gate?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xviii (ET: DU)], [Probashi Kallyan Bank Assistant Programmer 2018 compact it 237 (ET: N/A)], [Combined Bank Maintenance Engineer 2018 compact it 228 (ET: N/A)], [Sonali Bank Limited Assistant Programmer 2016 compact it 252 (ET: N/A)]*
   (a) NAND
   (b) AND
   (c) OR
   (d) NOT
answer: A
explanation: NAND এবং NOR গেটকে সার্বজনীন বা ইউনিভার্সাল গেট (Universal logic gate) বলা হয়, কারণ এদের যেকোনো একটি এককভাবে ব্যবহার করে অন্য সকল মৌলিক গেট তৈরি করা সম্ভব।

2. **3 ইনপুট বিশিষ্ট NAND গেট এর একটি ইনপুট 0 হলে আউটপুট কত?** *[PGCB Assistant Engineer (CSE) 05.04.2024 compact it 2 (ET: BUET)]*
   ক. 0
   খ. 3
   গ. 1
   ঘ. কোনোটিই নয়
answer: C
explanation: NAND গেটের আউটপুট $Y = \overline{A \cdot B \cdot C}$; যেকোনো একটি ইনপুট ০ হলে গুণফল ০ হয় এবং তার ইনভার্ট হয়ে আউটপুট সর্বদা ১ হবে।

3. **What is the lowest number of NAND gates required to make in inverter?** *[Combined Bank Officer (IT) 04.10.2024 compact it 15 (ET: BIBM)]*
   (a) 1
   (b) 2
   (c) 3
   (d) 4
answer: A
explanation: একটি NAND গেটের ইনপুট দুটিকে পরস্পরের সাথে যুক্ত (Tie) করে একটি সাধারণ ইনপুট দিলে তা সরাসরি একটি ইনভার্টার বা NOT গেট হিসেবে কাজ করে ($\overline{A \cdot A} = \overline{A}$)।

4. **Universal logic gate is:** *[BREB Assistant Programmer 2023 compact it 32 (ET: N/A)]*
   (a) NAND, XOR
   (b) NOR, XOR
   (c) NOR, OR
   (d) NAND, NOR
answer: D
explanation: ডিজিটাল ইলেকট্রনিক্সে NAND এবং NOR গেট দুটিকে সার্বজনীন বা ইউনিভার্সাল গেট বলা হয়।

5. **The logic gate that will have a Low output then any one of its inputs is High is ______.** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 53 (ET: N/A)]*
   (ক) NAND gate
   (খ) AND gate
   (গ) NOR gate
   (ঘ) OR gate
answer: C
explanation: NOR গেটে যেকোনো একটি ইনপুট High (১) হলেই তার আউটপুট Low (০) হয়ে যায় ($Y = \overline{A + B}$); কেবল সকল ইনপুট Low হলেই আউটপুট High হয়।

6. **What is the name of the following symbol?** *[BREB Assistant General Manager (O&M/E&C) 2021 compact it 136 (ET: N/A)]*
   a) FET
   b) JFET
   c) Schottky Diode
   d) SCR
answer: C
explanation: প্রশ্নপত্রে প্রদর্শিত এস-আকৃতির (S-shaped) ক্যাথোড সংবলিত প্রতীকটি হলো 'শটকি ডায়োড' (Schottky Diode)-এর ইলেকট্রনিক প্রতীক।

7. **In which logic gate output is 1 when all inputs are zero?** *[BREB Assistant Enforcement Coordinator 2021 compact it 141 (ET: N/A)]*
   ক. AND
   খ. NAND
   গ. OR
   ঘ. NOR
answer: D
explanation: NOR গেটের সংজ্ঞানুযায়ী, সকল ইনপুট ০ (Low) হলেই কেবল এর আউটপুট ১ (High) হয়। (উল্লেখ্য, NAND গেটেও ০,০ ইনপুটে আউটপুট ১ হয়)।

8. **A technician testing a logic circuit sees that the output of a particular INVERTER is stuck LOW while its input is pulsing. Which one of the following is the possible reason for this faulty operation?** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 174 (ET: N/A)]*
   a) The output of the INVERTER is internally grounded
   b) The output of the INERTER is externally grounded
   c) The input being driven by output of the INVERTER is internally grounded
   d) All of the above
answer: D
explanation: ডিজিটাল ট্রাবলশুটিংয়ে কোনো লজিক গেটের আউটপুট স্থায়ীভাবে Low হয়ে থাকার পেছনে ইন্টারনাল বা এক্সটারনাল গ্রাউন্ড শর্ট অথবা চালিত গেটের ইনপুট গ্রাউন্ডে শর্ট থাকা—সবগুলোই সম্ভাব্য কারণ হতে পারে (All of the above)।

9. **\overline{A}\overline{B}\overline{C}(\overline{A} + \overline{B} + \overline{C}) Which is the simplified form of this?** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 177 (ET: N/A)]*
   a) ar{A} + ar{B} + ar{C}
   b) ar{A}ar{B}ar{C}
   c) \overline{ABC}
   d) \overline{A B C}
answer: B
explanation: বুলিয়ান সরলীকরণ: $\overline{A}\overline{B}\overline{C}(\overline{A} + \overline{B} + \overline{C}) = \overline{A}\overline{B}\overline{C}\overline{A} + \overline{A}\overline{B}\overline{C}\overline{B} + \overline{A}\overline{B}\overline{C}\overline{C} = \overline{A}\overline{B}\overline{C} + \overline{A}\overline{B}\overline{C} + \overline{A}\overline{B}\overline{C} = \overline{A}\overline{B}\overline{C}$।

10. **Write the name of the Gate:** *[BREB Assistant Junior Engineer (IT) 2019 compact it 217 (ET: N/A)]*
    A) NOR
    B) OR
    C) NAND
    D) None
answer: C
explanation: পরীক্ষার প্রশ্নপত্রে প্রদত্ত লজিক গেটের চিত্রটি ছিল একটি ন্যান্ড গেট (NAND gate: AND গেটের আউটপুটে ইনভার্টার বাবল সংবলিত চিত্র)।

11. **The OR, XOR & AND functions can be performed by ____ of the computer in a CPU.** *[BREB Assistant Junior Engineer (IT) 2019 compact it 219 (ET: N/A)]*
    A) ALU
    B) CU
    C) Memory
    D) Register
answer: A
explanation: কম্পিউটারের সিপিইউ-তে যেকোনো ধরনের লজিক্যাল অপারেশন (যেমন OR, AND, XOR) সম্পাদন করে অ্যারিথমেটিক অ্যান্ড লজিক ইউনিট (ALU)।

12. **Which of the following options is suitable, if A is “10110110”, B is “11100000” and C is “10100000”?** *[Combined Bank Senior Officer (IT) 2018 compact it 221 (ET: DU)]*
    A) C=A or B
    B) C=ar{A}
    C) C=ar{B}
    D) C=A and B
answer: D
explanation: $A$ ও $B$-এর বিটওয়াইজ AND করলে: $10110110 \text{ AND } 11100000 = 10100000$, যা $C$-এর সমান; সুতরাং $C = A \text{ and } B$।

13. **When two variables are logically compared, the logic gate that tests the equivalence is–** *[Combined Bank Senior Officer (IT) 2018 compact it 222 (ET: DU)]*
    A) XNOR
    B) XOR
    C) AND
    D) NOR
answer: A
explanation: দুটি ভ্যারিয়েবল পরস্পর সমান (উভয়ই ০ বা উভয়ই ১) কিনা তা যাচাই করার ইকুইভ্যালেন্স গেট হলো XNOR গেট।

14. **Binary circuit elements have** *[Bangladesh Bank Assistant Director (IT) 2016 compact it 240 (ET: N/A)]*
    A) One stable state
    B) two stable state
    C) Three stable state
    D) None of these
answer: B
explanation: বাইনারি বা ডিজিটাল লজিক উপাদানসমূহ দ্বি-স্থিতিশীল (Bistable); অর্থাৎ এদের দুটি সুনির্দিষ্ট স্থায়ী অবস্থা (Two stable states: ০ এবং ১) থাকে।

15. **Which is the universal gate?** *[BREB Assistant General Manager (IT) 2016 compact it 255 (ET: N/A)]*
    A) NOR
    B) AND
    C) NOT
    D) OR
answer: A
explanation: বিকল্পগুলোর মধ্যে NOR গেট একটি সার্বজনীন বা ইউনিভার্সাল গেট (Universal gate)।

16. **NAND gates are preferred over other because these ________** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 271 (ET: N/A)]*
    a. Have lower function area
    b. Can be used to make any gate
    c. Consume least electronic power
    d. Provide maximum density in a chip
answer: B
explanation: NAND গেট সার্বজনীন হওয়ায় এটি এককভাবে ব্যবহার করে অন্য যেকোনো লজিক গেট বা সার্কিট তৈরি করা সম্ভব (Can be used to make any gate)।

## Sequential Circuits (Flip-Flops) (6)

1. **In which flip flop the present input will be the next output?** *[Combined Bank Officer (IT) 04.10.2024 compact it 12 (ET: BIBM)]*
   (a) S-R
   (b) J-K
   (c) D
   (d) T
answer: C
explanation: ডি (D বা Data/Delay) ফ্লিপ-ফ্লপে ইনপুটে যা প্রয়োগ করা হয়, ক্লক পালসের পর পরবর্তী আউটপুটে ঠিক তাই পাওয়া যায় ($Q_{next} = D$)।

2. **A basic memory storage element in a digital system is:** *[Bangladesh Bank Assistant Maintenance Engineer 04.02.2023 compact it 23 (ET: BIBM)]*
   (a) Flip-flop
   (b) Counter
   (c) Multiplexer
   (d) Encoder
answer: A
explanation: ডিজিটাল সিস্টেমের মৌলিক ১-বিট মেমোরি স্টোরেজ উপাদান বা মৌলিক সেল হলো ফ্লিপ-ফ্লপ (Flip-flop)।

3. **How much data a flip flop can store?** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 177 (ET: N/A)]*
   a) 4-bit data
   b) 1-bit data
   c) 3-bit data
   d) 3-bit data
answer: B
explanation: একটি ফ্লিপ-ফ্লপ ডিজিটাল ডেটার মাত্র ১টি বিট (1-bit data: ০ অথবা ১) সংরক্ষণ করতে সক্ষম।

4. **A binary counter is being pulsed by a 256 kHz clock signal. The output frequency from the last flip flop is 2kHz. Which one of the following is the counting range?** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 182 (ET: N/A)]*
   a) 0 to 255
   b) 0 to 128
   c) 0 to 127
   d) None of the above
answer: C
explanation: কাউন্টারের মডুলাস বা বিভাজন অনুপাত $\text{MOD} = 256\text{ kHz} / 2\text{ kHz} = 128 = 2^7$ (৭টি ফ্লিপ-ফ্লপ)। সুতরাং কাউন্টারটির গণনা সীমা হলো $0$ থেকে $\text{MOD}-1$ অর্থাৎ $0$ থেকে $127$।

5. **Which one is the output of the following digital logic circuit?** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 182 (ET: N/A)]*
   ```
   A ---------------------+-----------------+
   |                 |
   |    +-------+    |
   +---|        |    |
   |   AND  |----+
   B -----------\             |        |    |
   >-----------|        |    |   +-------+
   C -----------/            +-------+    +---|       |
   |                              |   OR  |----
   |           +-------+    +---|       |
   +----------|        |    |   +-------+
   |   AND  |----+
   |        |
   -------------------------|        |
   +-------+
   ```
   a) AB+A(B+C) + C(B+C)
   b) AB+A(B+C) + B(B+C)
   c) AC+A(B+C) + B(B+C)
   d) BC+C(B+C) + B(B+C)
answer: A
explanation: লজিক বর্তনী অনুসারে প্রথম AND গেটের আউটপুট $AB$, মধ্যবর্তী OR গেটের আউটপুট $(B+C)$ যা পরবর্তী দুটি AND গেটে যথাক্রমে $A$ ও $C$-এর সাথে যুক্ত হয়ে $A(B+C)$ ও $C(B+C)$ গঠন করে; সবশেষে এই তিনটি টার্মকে মূল OR গেটের মাধ্যমে যুক্ত করলে আউটপুট হয় $AB + A(B+C) + C(B+C)$।

6. **যে বর্তনী ১-বিট ডাটা সংরক্ষণ করতে পারে তা হলো-** *[BPSC Assistant Network Engineer 2019 compact it 195 (ET: N/A)]*
   A) রেজিস্টার
   B) এনকোডার
   C) ডিকোডার
   D) ফ্লিপ-ফ্লপ
answer: D
explanation: ফ্লিপ-ফ্লপ (Flip-flop) হলো মেমরির মৌলিক একক যা ঠিক ১-বিট বাইনারি ডাটা সংরক্ষণ করতে পারে।

## Digital Logic & Number Systems (6)

1. **When the hexadecimal value ABCD in a 32-bit register is logically shifted right by two bits, which of the following is the resulting value in hexadecimal? [ একটি 32-bit register-এ থাকা hexadecimal মান ABCD কে logically right shift করা হলো 2 bit। তাহলে resulting hexadecimal মান কোনটি হবে?]** *[Combined Bank Senior Officer (IT) Date: 17.10.2025 [bitbox it book 212]]*
   (a) 2AF3
   (b) 6AF3
   (c) AF34
   (d) EAF3
answer: A
explanation: $ABCD_{16} = 1010\ 1011\ 1100\ 1101_2$ কে লজিক্যালি ২-বিট ডানে শিফট করলে পাওয়া যায় $0010\ 1010\ 1111\ 0011_2$, যা হেক্সাডেসিমেলে $2AF3_{16}$।

2. **Which of the following is the Octal equivalent of the hexadecimal number 7B5? [ নিচের হেক্সাডেসিমাল সংখ্যা 7B5-এর সমতুল্য অক্টাল সংখ্যা কী হবে?]** *[Combined Bank Senior Officer (IT) Date: 17.10.2025 [bitbox it book 216]]*
   (a) 735
   (b) 7551
   (c) 3665
   (d) 7561
answer: C
explanation: হেক্সাডেসিমেল $7B5_{16}$-কে বাইনারিতে রূপান্তর করলে পাই $0111\ 1011\ 0101_2$; ৩-বিট করে সাজালে $011\ 110\ 110\ 101_2 = (3665)_8$।

3. **Which number system is used internally by a computer? [ কম্পিউটার অভ্যন্তরে কোন সংখ্যা পদ্ধতি ব্যবহার করে? ]** *[Bankers' Selection Committee Secretariat Post: Assistant Programmer; Date: 15 Feb, 2024 Exam Taker: ANZA; Post: 35 [bitbox it book 349]]*
   (a) Decimal
   (b) Octal
   (c) Binary
   (d) Hexadecimal
answer: C
explanation: কম্পিউটার হার্ডওয়্যার অভ্যন্তরীণভাবে সকল ডাটা ও ইন্সট্রাকশন প্রক্রিয়া করার জন্য বাইনারি (Binary: 0 ও 1) সংখ্যা পদ্ধতি ব্যবহার করে।

4. **What is the result of the binary sum?[ নিচের বাইনারি যোগফলের ফলাফল কত? ] 10101 + 1011** *[Bankers' Selection Committee Secretariat Post: Senior Office (IT); Date: 04 October, 2024 Exam Taker: ANZA; Post: 222 [bitbox it book 505]]*
   (a) 10000
   (b) 101010
   (c) 100000
   (d) 111100
answer: C
explanation: বাইনারি যোগ: $10101_2 (২১) + 1011_2 (১১) = 100000_2 (৩২)$।

5. **Suppose the numbers 7, 5, 1, 8, 3, 6, 0, 9, 4, 2 are inserted in that order into an initially empty binary search tree.The binary search tree uses the usual ordering on natural numbers.What is the in-order traversal sequence of the resultant tree?[ যদি ৭, ৫, ১, ৮, ৩, ৬, ০, ৯, ৪, ২ সংখ্যাগুলো এই ক্রম অনুযায়ী একটি খালি বাইনারি সার্চ ট্রিতে (BST) প্রবেশ করানো হয়, তবে ইন-অর্ডার ট্রাভার্সাল (In-order traversal) সিকোয়েন্স কী হবে? ]** *[Bankers' Selection Committee Secretariat Post: Senior Office (IT); Date: 04 October, 2024 Exam Taker: ANZA; Post: 222 [bitbox it book 506]]*
   (a) 9 8 6 4 2 3 0 1 5 7
   (b) 0 2 4 3 1 6 5 9 8 7
   (c) 7 5 1 0 3 2 4 6 8 9
   (d) 0 1 2 3 4 5 6 7 8 9
answer: D
explanation: যেকোনো বাইনারি সার্চ ট্রির (BST) ইন-অর্ডার ট্রাভার্সাল সর্বদা উপাদানগুলোকে মানের ঊর্ধ্বক্রমানুসারে (Ascending sorted order) সাজায়; ফলে সিকোয়েন্সটি হবে: 0 1 2 3 4 5 6 7 8 9।

6. **A binary search tree is constructed by inserting the numbers: 60, 25, 72, 15, 30, 68, 13, 18 in order. The number of nodes in the left sub tree is [ ৬০, ২৫, ৭২, ১৫, ৩০, ৬৮, ১৩, ১৮ এই সংখ্যাগুলো দিয়ে একটি BST তৈরি করলে বাম সাব-ট্রিতে (Left sub tree) কতটি নোড থাকবে? ]** *[Bankers' Selection Committee Secretariat Post: Senior Office (IT); Date: 04 October, 2024 Exam Taker: ANZA; Post: 222 [bitbox it book 507]]*
   (a) 4
   (b) 5
   (c) 6
   (d) 8
answer: B
explanation: ৬০ হলো রুট নোড। ৬০ অপেক্ষা ছোট সকল উপাদান (২৫, ১৫, ৩০, ১৩, ১৮) রুট নোডের বাম সাব-ট্রিতে (Left sub-tree) অবস্থান করবে; সুতরাং বাম সাব-ট্রিতে নোড সংখ্যা হবে ৫টি।

## Boolean Algebra & Simplification (4)

1. **The simplified form of the Boolean expression (A+B+AB) (A+C) is–** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 131 (ET: N/A)]*
   a) A + B + C
   b) AB + BC
   c) A+BC
   d) ACB
answer: C
explanation: বুলিয়ান উপপাদ্য অনুসারে $(A + B + AB) = A + B(1 + A) = A + B$; এরপর $(A + B)(A + C) = A + AC + AB + BC = A(1 + C + B) + BC = A + BC$।

2. **Which one of the following has the truth value FALSE for the variables A=TRUE and B=TRUE and C=TRUE?** *[Rupali Bank Ltd. Assistant Network Engineer (ANE) 2021 compact it 81 (ET: N/A)]*
   a. Aar{B}C + ar{A}BC
   b. X = A.ar{B} + ar{A}.B
   c. (AC + ar{B})(ar{A} + (B \oplus C))
   d. (A + B) \oplus C \oplus (B + C)
answer: C
explanation: $A=1, B=1, C=1$ বসালে: (c) $(1\cdot1 + 0)(0 + (1 \oplus 1)) = 1 \cdot 0 = 0$ (FALSE)। উল্লেখ্য (a) ও (b) ও ০ দেয়, পক্ষান্তরে (d) এর মান $1 \oplus 1 \oplus 1 = 1$ (TRUE)।

3. **Which of the logic expressions is equivalent to the digital circuit shown in the figure?** *[Rupali Bank Ltd. Assistant Network Engineer (ANE) 2021 compact it 82 (ET: N/A)]*
   a. X = A.B + \overline{A}.\overline{B}
   b. X = A.B + ar{A}.ar{B}
   c. X = A.ar{B} + ar{A}.B
   d. X = (ar{A} + B).(A + ar{B})
answer: C
explanation: ডিজিটাল সার্কিটটিতে দুটি AND গেটের মাধ্যমে $A\overline{B}$ ও $\overline{A}B$ তৈরি করে একটি OR গেটে যুক্ত করা হয়েছিল, যা XOR অপারেশন $X = A\overline{B} + \overline{A}B$-এর সমতুল্য।

4. **According to Boolean algebra the value of: (A + AB) \cdot (B + AB) is-** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 249 (ET: N/A)], [Combined Bank Maintenance Engineer 2018 compact it 227 (ET: N/A)]*
   A) A
   B) B
   C) AB
   D) 1
answer: C
explanation: বুলিয়ান বীজগণিতের অবশোষণ নিয়ম অনুসারে $A + AB = A(1 + B) = A$ এবং $B + AB = B(1 + A) = B$; সুতরাং তাদের গুণফল $(A + AB) \cdot (B + AB) = A \cdot B = AB$।

## Combinational Circuits (MUX, Decoder) (2)

1. **How many select line would be there if the inputs of a MUX are 8?** *[Combined Bank Officer (IT) 04.10.2024 compact it 15 (ET: BIBM)]*
   (a) 2
   (b) 3
   (c) 4
   (d) 5
answer: B
explanation: একটি $2^n$-টু-১ মাল্টিপ্লেক্সারে (MUX) $n$ টি সিলেক্ট লাইন থাকে; ৮টি ইনপুটের জন্য ($8 = 2^3$) সিলেক্ট লাইনের সংখ্যা হবে ৩টি।

2. **A decoder has four input lines. How many output lines will be there?** *[Combined Bank Officer (IT) 04.10.2024 compact it 15 (ET: BIBM)]*
   (a) 4
   (b) 8
   (c) 16
   (d) 32
answer: C
explanation: একটি $n$-টু-$2^n$ ডিকোডারে $n$ টি ইনপুট লাইনের বিপরীতে সর্বোচ্চ $2^n$ টি আউটপুট লাইন থাকে; ৪টি ইনপুটের জন্য আউটপুট লাইনের সংখ্যা হবে $2^4 = 16$।
