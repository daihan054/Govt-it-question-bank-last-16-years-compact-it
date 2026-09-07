<!-- TOC START -->
**Table of Contents** — 7 subtopics · 95 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Data Structure Basics](#data-structure-basics-25) | 25 |
| 2 | [Stack & Queue](#stack--queue-23) | 23 |
| 3 | [Tree & Binary Search Tree](#tree--binary-search-tree-20) | 20 |
| 4 | [Data Structures & Algorithms](#data-structures--algorithms-12) | 12 |
| 5 | [Linked List](#linked-list-10) | 10 |
| 6 | [Priority Queue & Heap](#priority-queue--heap-3) | 3 |
| 7 | [Hashing & Hash Tables](#hashing--hash-tables-2) | 2 |

<!-- TOC END -->

---

## Data Structure Basics (25)

1. **Which of the following is a non linear data structure?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 26 (ET: BIBM)]*
   (a) Array
   (b) Graph
   (c) Queue
   (d) Linked list
answer: b
explanation: Graph এবং Tree হলো নন-লিনিয়ার (Non-linear) ডেটা স্ট্রাকচার, কারণ এদের উপাদানগুলো অনুক্রমিক সরলরেখায় সাজানো থাকে না। Array, Queue এবং Linked list হলো লিনিয়ার।

2. **Which of the data structure is linear type?** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 172 (ET: N/A)]*
   a) Tree
   b) Binary Tree
   c) Queue
   d) Graph
answer: c
explanation: Queue হলো একটি লিনিয়ার ডেটা স্ট্রাকচার (FIFO)। অন্যদিকে Tree, Binary Tree এবং Graph হলো হায়ারার্কিকাল বা নন-লিনিয়ার ডেটা স্ট্রাকচার।

3. **Array data structure এ কোন ধরনের data রাখা যায়?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)], [BPSC Assistant Network Engineer 2019 compact it 198 (ET: N/A)]*
   A) various type data
   B) Only pointer type data
   C) Classes data
   D) Same type many data
answer: D
explanation: অ্যারে (Array) হলো একই ডেটা টাইপের (Homogeneous / Same type) একাধিক উপাদানের একটি সুনির্দিষ্ট এবং ধারাবাহিক মেমরি সংগ্রহ।

4. **LIFO data structure কোনটি?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)], [BPSC Assistant Network Engineer 2019 compact it 194 (ET: N/A)]*
   A) Queue
   B) Stack
   C) File
   D) কোনটি নয়
answer: B
explanation: Stack কাজ করে LIFO (Last In First Out) নীতিতে; অর্থাৎ যে উপাদান সবার শেষে যুক্ত (Push) হয়, অপসারণের (Pop) সময় সেটিই সবার আগে বের হয়।

5. **Linked list এ ন্যূনতম দুইটি field থাকে। একটি হচ্ছে data field, তবে অন্যটি কি?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)]*
   A) Pointer to char
   B) Node
   C) Pointer to node
   D) Null
answer: C
explanation: একটি লিঙ্কড লিস্টের প্রতিটি নোডে মূলত দুটি ফিল্ড থাকে: ডেটা ধারণের জন্য Data field এবং পরবর্তী নোডের অ্যাড্রেস ধারণের জন্য Pointer to node (বা Next pointer)।

6. **নিচের কোনটি একটি valid postfix expression?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 189 (ET: N/A)]*
   A) a*b(c+d)
   B) abc*+de-+
   C) +ab
   D) a+b-c
answer: B
explanation: Postfix (বা Reverse Polish) নোটেশনে অপারেটরসমূহ সংশ্লিষ্ট অপারেন্ডের পরে বসে। `abc*+de-+` একটি নিখুঁত ও বৈধ পোস্টফিক্স এক্সপ্রেশন (ইনফিক্স: a + b*c + d - e)।

7. **Which of the following data structure is non-linear type?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 206 (ET: AUST)]*
   A) Strings
   B) Lists
   C) Stacks
   D) None of these
answer: D
explanation: Strings, Lists এবং Stacks—সবগুলোই লিনিয়ার ডেটা স্ট্রাকচার। এদের কোনোটিই নন-লিনিয়ার নয়, তাই সঠিক উত্তর None of these।

8. **The maximum number of binary trees that can be formed with three unlabeled nodes is-** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 208 (ET: AUST)]*
   A) 1
   B) 3
   C) 5
   D) 4
answer: C
explanation: n সংখ্যক আনলেবেল্ড নোড দ্বারা গঠিত মোট বাইনারি ট্রির সংখ্যা হলো n-তম Catalan number: C_n = (2n)! / ((n+1)! * n!)। n=3 হলে C_3 = 6! / (4! * 3!) = 5।

9. **নিচের কোনটি দিয়ে Graph represent করা যায়?** *[BPSC Assistant Network Engineer 2019 compact it 195 (ET: N/A)]*
   A) Queue
   B) Stack
   C) Adjacency list
   D) Pointer
answer: C
explanation: গ্রাফ মেমরিতে উপস্থাপনের দুটি প্রমিত কৌশল হলো Adjacency Matrix এবং Adjacency List।

10. **Which one is less costly for insertion at a particular position?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 237 (ET: N/A)]*
    A) Array
    B) Queue
    C) Link List
    D) Stack
answer: C
explanation: লিঙ্কড লিস্টে কোনো নির্দিষ্ট অবস্থানে নোড ইনসার্ট করতে অন্যান্য উপাদান শিফট করতে হয় না, কেবল পয়েন্টার রি-অ্যাসাইন করলেই চলে (O(1) যদি পজিশন পয়েন্টার জানা থাকে); অন্যদিকে অ্যারেতে O(n) শিফটিং লাগে।

11. **Which data structure required evaluating a postfix expression is?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 237 (ET: N/A)]*
    A) Queue
    B) Stack
    C) Link List
    D) Array
answer: B
explanation: পোস্টফিক্স এক্সপ্রেশন মূল্যায়নের (Evaluation of Postfix Expression) জন্য স্ট্যাক (Stack) ডেটা স্ট্রাকচার ব্যবহৃত হয়।

12. **Link List can be implemented by using?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 238 (ET: N/A)]*
    A) Array
    B) Pointer
    C) Both A and B
    D) None of above
answer: C
explanation: লিঙ্কড লিস্ট ডায়নামিক মেমরি পয়েন্টার ব্যবহার করে স্বাভাবিকভাবে বাস্তবায়িত হয়, পাশাপাশি ফিক্সড সাইজ অ্যারে (Array of records / static allocation) ব্যবহার করেও বাস্তবায়ন করা যায়।

13. **Which following data structure is linear type?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 238 (ET: N/A)]*
    A) Strings
    B) Lists
    C) Queue
    D) All of above
answer: D
explanation: Strings, Lists এবং Queue—প্রত্যেকটিই লিনিয়ার ডেটা স্ট্রাকচার, কারণ এদের উপাদানগুলো মেমরিতে ক্রমানুসারে একটির পর একটি সাজানো থাকে।

14. **An array contains the following letters, Color = {E, L, E, C, T, I, O, N}. The value of the variable, E=3, Color[E] points to which value?** *[Combined Bank Senior Officer (IT) 2018 compact it 222 (ET: DU)]*
    A) E
    B) C
    C) T
    D) 1
answer: B
explanation: 0-ভিত্তিক ইনডেক্সিং অনুসারে: Color[0]='E', Color[1]='L', Color[2]='E', Color[3]='C'। যেহেতু E=3, তাই Color[E] বা Color[3] এর মান হবে 'C'।

15. **The operation of processing each element in the list is known as-----** *[Combined Bank Maintenance Engineer 2018 compact it 226 (ET: N/A)]*
    A) Sorting
    B) Merging
    C) Inserting
    D) Traversal
answer: D
explanation: কোনো ডেটা স্ট্রাকচারের প্রতিটি উপাদানকে ঠিক একবার পরিদর্শন বা প্রসেস করার প্রক্রিয়াকে ট্রাভার্সাল (Traversal) বলা হয়।

16. **Which of the following data structure are index structures?** *[Combined Bank Maintenance Engineer 2018 compact it 226 (ET: N/A)]*
    A) linear array
    B) link list
    C) both a and b
    D) none
answer: A
explanation: Linear array হলো একটি ইনডেক্সড ডেটা স্ট্রাকচার, যেখানে প্রতিটি উপাদানের একটি নির্দিষ্ট পূর্ণসংখ্যা ইনডেক্স থাকে যার মাধ্যমে O(1) সময়ে সরাসরি অ্যাক্সেস করা যায়।

17. **The term push and pop related to -** *[Combined Bank Maintenance Engineer 2018 compact it 226 (ET: N/A)]*
    A) Array
    B) list
    C) stack
    D) all of this
answer: C
explanation: Push (নতুন উপাদান যুক্ত করা) এবং Pop (শীর্ষ উপাদান মুছে ফেলা)—এ দুটি অপারেশন স্ট্যাক (Stack) ডেটা স্ট্রাকচারের সাথে সম্পর্কিত।

18. **Which data structure is used for indexing?** *[Combined Bank Maintenance Engineer 2018 compact it 226 (ET: N/A)]*
    A) Binary tree
    B) B+ tree
    C) Stack
    D) Link List
answer: B
explanation: ডাটাবেজ ম্যানেজমেন্ট সিস্টেম এবং ফাইল সিস্টেমে দ্রুত রেকর্ড খোঁজার ইনডেক্সিং কাঠামো হিসেবে B+ Tree সর্বাধিক ব্যবহৃত হয়।

19. **The Term push and Pop is related to the** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 247 (ET: N/A)]*
    A) Array
    B) Lists
    C) Stacks
    D) All of the above
answer: C
explanation: Push এবং Pop হলো স্ট্যাকের (Stacks) প্রধান দুটি মৌলিক অপারেশন।

20. **Which of the following data structure is non-linear type?** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 248 (ET: N/A)]*
    A) String
    B) Lists
    C) Stacks
    D) None
answer: D
explanation: String, Lists এবং Stacks প্রত্যেকেই লিনিয়ার ডেটা স্ট্রাকচার। এদের কোনটিই নন-লিনিয়ার নয়।

21. **The operation of processing each element in the list is known as-** *[Sonali Bank Limited Assistant Engineer (IT) 2016 compact it 248 (ET: N/A)]*
    A) Traversal
    B) Merging
    C) Inserting
    D) Sorting
answer: A
explanation: ডেটা তালিকার সকল উপাদান ক্রমানুসারে ভিজিট বা প্রসেস করার প্রক্রিয়াকে Traversal বলা হয়।

22. **Which is correct?** *[Bangladesh Bank Assistant Programmer 2016 compact it 243 (ET: N/A)]*
    A) <body color= 'yello'>
    B) <body bgcolor= 'yello'>
    C) <body background> yellow<body>
    D) <body background= 'yellow'>
answer: B
explanation: HTML-এ পৃষ্ঠার ব্যাকগ্রাউন্ড রঙ নির্ধারণের সঠিক সিনট্যাক্স হলো `<body bgcolor='yellow'>`।

23. **Which is not linear?** *[Bangladesh Bank Assistant Programmer 2016 compact it 246 (ET: N/A)]*
    A) Linked list
    B) array
    C) graph
    D) None
answer: C
explanation: Graph হলো একটি নন-লিনিয়ার ডেটা স্ট্রাকচার; Linked list এবং Array হলো লিনিয়ার ডেটা স্ট্রাকচার।

24. **When a new data is inserted into a data structure, but there is no available space; this situation is usually called ---** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 260 (ET: N/A)]*
    A) underflow
    B) overflow
    C) houseful
    D) saturated
answer: B
explanation: কোনো ডেটা স্ট্রাকচার (যেমন স্ট্যাক বা কিউ) পূর্ণ থাকা অবস্থায় আরও নতুন ডেটা প্রবেশ করানোর চেষ্টাকে Overflow বলা হয় (খালি অবস্থায় ডেটা মোছার চেষ্টাকে Underflow বলে)।

25. **To represent hierarchical relationship between element, which data Structure is suitable?** *[Janata Bank Limited Assistant Engineer (IT) 2015 compact it 260 (ET: N/A)]*
    A) Desuetude
    B) Priority
    C) Tree
    D) Graph
answer: C
explanation: উপাদানসমূহের মধ্যকার পদানুক্রমিক বা স্তরভিত্তিক সম্পর্ক (Hierarchical relationship) উপস্থাপনের জন্য Tree ডেটা স্ট্রাকচার সবচেয়ে উপযুক্ত।

## Stack & Queue (23)

1. **Which one of the following is an application of Stack Data Structure?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xx (ET: DU)]*
   (a) Managing function calls
   (b) The stock span problem
   (c) Arithmetic expression evaluation
   (d) All of the above
answer: d
explanation: ফাংশন কল ও রিকার্শন পরিচালনা (Call stack), স্টক স্প্যান প্রবলেম সমাধান এবং ইনফিক্স/পোস্টফিক্স গাণিতিক এক্সপ্রেশন রূপান্তর ও মূল্যায়ন—সবগুলোতেই স্ট্যাক ডেটা স্ট্রাকচার ব্যবহৃত হয়।

2. **The minimum number of stacks needed to implement a queue is** *[Combined Bank Officer (IT) 04.10.2024 compact it 15 (ET: BIBM)]*
   (a) 1
   (b) 2
   (c) 3
   (d) 4
answer: b
explanation: দুটি স্ট্যাক (একটি ইনসার্ট/ইনপুট ও অন্যটি রিভার্স/আউটপুটের জন্য) ব্যবহার করে সফলভাবে একটি FIFO কিউ বাস্তবায়ন করা যায়।

3. **Which Data structure is needed to convert infix notation to postfix notation?** *[NPCBL Executive Trainee (Software) 2023 compact it 38 (ET: N/A)]*
   a) Branch
   b) Tree
   c) Queue
   d) Stack
answer: d
explanation: Shunting-yard অ্যালগরিদমের মাধ্যমে ইনফিক্স এক্সপ্রেশনকে পোস্টফিক্স নোটেশনে রূপান্তর করতে অপারেটরদের অগ্রাধিকার নিয়ন্ত্রণে স্ট্যাক (Stack) ব্যবহৃত হয়।

4. **Find the output of the following prefix expression *+2-2 	ext{ } 1/4 	ext{ } 2+-531** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*
   a) 2
   b) 12
   c) 10
   d) 4
answer: b
explanation: প্রিফিক্স এক্সপ্রেশন ডান থেকে বামে স্ট্যাকের সাহায্যে মূল্যায়িত হয়। প্রথম উপ-অংশ `+ 2 (- 2 1)` এর মান হয় 3 এবং দ্বিতীয় উপ-অংশটির মান মূল্যায়িত হয়ে 4 আসে। উভয় অংশের গুণফল $3 	imes 4 = 12$।

5. **Which data structure allows insertion and deletion of elements from both ends?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 26 (ET: BIBM)]*
   (a) Deque
   (b) Queue
   (c) Stack
   (d) Linked list
answer: a
explanation: Deque বা Double-Ended Queue হলো এমন একটি ডেটা স্ট্রাকচার যার উভয় প্রান্ত (Front ও Rear) থেকেই ডেটা ইনসার্ট এবং ডিলিট করা যায়।

6. **In data structure use recursion?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*
   **Ans:** Stack
answer: Stack
explanation: প্রোগ্রামিংয়ে রিকার্সিভ ফাংশন কলের স্টেট, রিটার্ন অ্যাড্রেস ও লোকাল ভেরিয়েবল সংরক্ষণ করতে সিস্টেমের অভ্যন্তরীণ Call Stack ব্যবহৃত হয়।

7. **What is the prefix conversion of the expression 	ext{A}+(	ext{B}-	ext{C})*	ext{D}?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*
   **Ans:** +	ext{A}*-	ext{BCD}
answer: +	ext{A}*-	ext{BCD}
explanation: অগ্রাধিকারের ক্রমানুসারে: প্রথমে বন্ধনীর ভেতরের `(B - C)` $
ightarrow$ `-BC`; এরপর গুণ `-BC * D` $
ightarrow$ `*-BCD`; সর্বশেষে যোগ `A + (*-BCD)` $
ightarrow$ `+A*-BCD`।

8. **An example of a hierarchical data structure is ______** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 46 (ET: N/A)]*
   (ক) Array
   (খ) Link list
   (গ) Tree
   (ঘ) Ring
answer: গ
explanation: Tree হলো একটি নন-লিনিয়ার হায়ারার্কিকাল (স্তরভিত্তিক) ডেটা স্ট্রাকচার, যেখানে উপাদানগুলো প্যারেন্ট-চাইল্ড সম্পর্কের ভিত্তিতে বিন্যস্ত থাকে।

9. **Which of the following data structures follows the LIFO principle?** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 46 (ET: N/A)]*
   (ক) stack
   (খ) Linked list
   (গ) Queue
   (ঘ) Graph
answer: ক
explanation: স্ট্যাক (Stack) হলো LIFO (Last In First Out) ডেটা স্ট্রাকচার, যেখানে সর্বশেষ প্রবেশকৃত উপাদানটি সবার আগে বের হয়।

10. **A stack is also called-** *[BPSC (Ministry) Assistant Maintenance Engineer 2022 compact it 47 (ET: N/A)]*
    (ক) Last in First Out
    (খ) First in Last Out
    (গ) Last In Last Out
    (ঘ) First in Frist Out
answer: ক
explanation: স্ট্যাককে LIFO (Last In First Out) বা FILO (First In Last Out) তালিকা বলা হয়।

11. **What is postfix expression of the string, a+(b-c)*d?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 131 (ET: N/A)], [Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 166 (ET: N/A)]*
    a) abc-d*+
    b) abcd - *+
    c) ad* bc -
    d) abc – d+*
answer: a
explanation: অগ্রাধিকার অনুসারে: `(b-c)` $
ightarrow$ `bc-`; গুণের ফলে `bc-d*`; এবং সবশেষে যোগের ফলে `abc-d*+`।

12. **In a shop, customers are provided the service as a first come first serve policy. But some special customers can be served at any time based on their importance. Which data structure most fits this scenario?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 84 (ET: N/A)]*
    a. Stack
    b. Queue
    c. Priority Queue
    d. Dequeue
answer: c
explanation: আগমন ক্রমের পাশাপাশি উপাদানের অগ্রাধিকার বা গুরুত্বের ভিত্তিতে সেবা প্রদানের জন্য Priority Queue সবচেয়ে উপযুক্ত।

13. **Which of the following data structures can be used both as Stack and Queue?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 87 (ET: N/A)]*
    a. Vector
    b. Hash Table
    c. Deque
    d. Binary Search Tree
answer: c
explanation: Deque (Double Ended Queue)-এর উভয় প্রান্ত দিয়ে ইনসার্ট ও ডিলিট করা যায় বলে এটিকে Stack (LIFO) এবং Queue (FIFO) উভয় হিসেবেই ব্যবহার করা যায়।

14. **Suppose you are implementing a Queue of size N using a non-circular linked list having a front and a rare pointer as shown in the figure. The enqueue operation inserts a new node at the front and the dequeue operation deletes a node from the rare. Which one of the following is the time complexity of the most efficient implementation of the enqueue and dequeue operations, respectively on this data structure?** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 175 (ET: N/A)]*
    ```
    +---+---+    +---+---+               +---+---+
    -->|   | --+--->|   | --+----.........->|   | / |
    +---+---+    +---+---+               +---+---+
    ^                                    ^
    |                                    |
    head                                 tail
    ```
    a) \theta(1), \theta(1)
    b) \theta(1), \theta(n)
    c) \theta(n), \theta(1)
    d) \theta(n), \theta(n)
answer: b
explanation: Singly linked list-এর শুরুতে (front/head) নতুন নোড যুক্ত করার টাইম কমপ্লেক্সিটি \theta(1)। কিন্তু শেষ প্রান্ত (rear/tail) থেকে ডিলিট করার জন্য tail-এর পূর্ববর্তী নোড খুঁজে পেতে পুরো লিস্ট ট্রাভার্স করতে হয়, তাই এর কমপ্লেক্সিটি \theta(n)।

15. **Which one is the characteristics of Stack ADT?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 167 (ET: N/A)]*
    a) Sequential Index
    b) Last-In-First Out
    c) First-In-First Out
    d) Key indexing
answer: b
explanation: Stack Abstract Data Type (ADT)-এর প্রধান বৈশিষ্ট্য হলো Last-In-First Out (LIFO)।

16. **What will be the state of a queue after executing the following operation?** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 181 (ET: N/A)]*
    push(1), push(2), pop(), push(4), push(5), pop()
    a) 2, 5
    b) 2, 4
    c) 4, 5
    d) 1, 4
answer: c
explanation: FIFO নিয়মে: push(1), push(2) $
ightarrow$ [1, 2]; pop() $
ightarrow$ 1 বের হয়ে থাকে [2]; push(4), push(5) $
ightarrow$ [2, 4, 5]; pop() $
ightarrow$ 2 বের হয়ে অবশেষে কিউতে থাকে [4, 5]।

17. **Suppose you want to insert n elements into an empty linked list while maintaining the shorted order. What is the worst-case time complexity?** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 184 (ET: N/A)]*
    a) \theta(n)
    b) \theta(n \log n)
    c) \theta(1)
    d) \theta(n^2)
answer: d
explanation: প্রতিটি উপাদানকে ক্রমানুসারে ইনসার্ট করতে গড়ে ও ওর্স্ট কেসে O(i) ট্রাভার্সাল লাগে। n সংখ্যক উপাদান ইনসার্ট করতে মোট সময় লাগে 1 + 2 + ... + n = O(n^2)।

18. **The term push and pop are related to the-** *[Probashi Kallyan Bank Programmer: 2019 compact it 212 (ET: AUST)]*
    A) array
    B) stacks
    C) lists
    D) All of these
answer: B
explanation: Push এবং Pop হলো স্ট্যাক (Stacks) ডেটা স্ট্রাকচারের দুটি প্রধান মৌলিক অপারেশন।

19. **The data structure required to check whether an expression contains balanced parenthesis is-** *[Combined 3 Bank Assistant Programmer 2018 compact it 231 (ET: N/A)]*
    A) Stack
    B) Queue
    C) Array
    D) Tree
answer: A
explanation: বন্ধনীসমূহের ব্যালান্স (Balanced Parentheses) যাচাই করার জন্য স্ট্যাক ডেটা স্ট্রাকচার ব্যবহৃত হয়।

20. **Pushing an element into stack already having five elements and stack size of 5 then stack becomes-** *[Combined 3 Bank Assistant Programmer 2018 compact it 233 (ET: N/A)]*
    A) Overflow
    B) Crash
    C) Underflow
    D) User flow
answer: A
explanation: নির্দিষ্ট ধারণক্ষমতা পূর্ণ থাকা অবস্থায় নতুন উপাদান যোগ করতে গেলে স্ট্যাক ওভারফ্লো (Overflow) অবস্থা ঘটে।

21. **Which is correct for stack?** *[Bangladesh Bank Assistant Programmer 2016 compact it 243 (ET: N/A)]*
    A) FIFO
    B) LIFO
    C) Both A, B
    D) None
answer: B
explanation: স্ট্যাক LIFO (Last In First Out) নীতিতে কাজ করে।

22. **Find the correct arranged data after stack operation push (1), push (2), pop, push (1), push (2), pop, pop, pop, push (2), pop.** *[Bangladesh Bank Assistant Programmer 2016 compact it 244 (ET: N/A)]*
    A) 2 2 1 1 2
    B) 2 2 1 2 1
    C) 2 2 2 2 1
    D) 2 2 2 1 2
answer: A
explanation: ক্রমানুসারে পপ হওয়া উপাদানগুলো হলো: ১ম পপে 2, ২য় পপে 2, ৩য় পপে 1, ৪র্থ পপে 1 এবং ৫ম পপে 2। সুতরাং ফলাফল: 2 2 1 1 2।

23. **Stack operations are—** *[Bangladesh Bank Assistant Programmer 2016 compact it 245 (ET: N/A)]*
    A) delete, insertion
    B) insertion, delete
    C) push, pop
    D) pop, push
answer: C
explanation: স্ট্যাকে উপাদান সংযোজন ও বিয়োজনের আনুষ্ঠানিক নাম হলো যথাক্রমে Push এবং Pop।

## Tree & Binary Search Tree (20)

1. **Suppose the numbers 7, 5, 1, 8, 3, 6, 0, 9, 4, 2 are inserted in that order into an initially empty binary search tree. The binary search tree uses the usual ordering on natural numbers. What is the in-order traversal sequence of the resultant tree?** *[Combined Bank Officer (IT) 04.10.2024 compact it 15 (ET: BIBM)]*
   (a) 9 8 6 4 2 3 0 1 5 7
   (b) 0 2 4 3 1 6 5 9 8 7
   (c) 7 5 1 0 3 2 4 6 8 9
   (d) 0 1 2 3 4 5 6 7 8 9
answer: d
explanation: বাইনারি সার্চ ট্রির (BST) ইন-অর্ডার ট্রাভার্সাল (In-order traversal: Left-Root-Right) সবসময় উপাদানগুলোকে আরোহী বা ছোট থেকে বড় ক্রমানুসারে (Ascending sorted order) বিন্যস্ত করে।

2. **A binary search tree is constructed by inserting the numbers, 60 25 72 15 30 68 13 18 in order. The number of nodes in the left sub tree is-** *[Combined Bank Officer (IT) 04.10.2024 compact it 15 (ET: BIBM)]*
   (a) 4
   (b) 5
   (c) 6
   (d) 8
answer: b
explanation: প্রথম সংখ্যা 60 হলো ট্রির মূল বা রুট (Root)। BST-এর নিয়মানুযায়ী রুটের চেয়ে ছোট সকল উপাদান বাম সাব-ট্রিতে যাবে। এখানে 60-এর চেয়ে ছোট সংখ্যাগুলো হলো: 25, 15, 30, 13, 18 (মোট ৫টি)।

3. **Suppose you are given a binary tree with 11 nodes, such that each node has exactly either zero or two children. The maximum height of the tree will be-** *[Combined Bank Officer (IT) 04.10.2024 compact it 15 (ET: BIBM)]*
   (a) 2
   (b) 3
   (c) 4
   (d) 5
answer: d
explanation: প্রতিটি নোডের ০ অথবা ২টি চাইল্ড থাকলে তাকে Full Binary Tree বলে। উচ্চতা h হলে সর্বনিম্ন নোড সংখ্যা N = 2h + 1 (যেখানে রুটের উচ্চতা ০)। সুতরাং 2h + 1 = 11 => 2h = 10 => h = 5।

4. **Level order traversal of a rooted tree can be done by starting from root and performing-** *[Combined Bank Officer (IT) 04.10.2024 compact it 15 (ET: BIBM)]*
   (a) Deep search
   (b) Root search
   (c) Depth first search
   (d) Breadth first search
answer: d
explanation: লেভেল অর্ডার ট্রাভার্সাল কিউ (Queue) ডেটা স্ট্রাকচার ব্যবহারের মাধ্যমে Breadth First Search (BFS) পদ্ধতিতে স্তরে স্তরে সম্পন্ন করা হয়।

5. **Which data structure is suitable to represent hierarchical relationship between elements?** *[NPCBL Executive Trainee (Software) 2023 compact it 39 (ET: N/A)]*
   a) Stack
   b) Queue
   c) List
   d) Tree
answer: d
explanation: উপাদানসমূহের মধ্যকার পদানুক্রমিক বা স্তরভিত্তিক সম্পর্ক (Hierarchical relationship) উপস্থাপনের জন্য Tree ডেটা স্ট্রাকচার আদর্শ।

6. **How many children does a binary tree have?** *[NPCBL Executive Trainee (Software) 2023 compact it 39 (ET: N/A)]*
   a) 2
   b) 0
   c) 0 or 1 or 2
   d) Any number of children
answer: c
explanation: বাইনারি ট্রির সংজ্ঞানুসারে প্রতিটি নোডে সর্বোচ্চ ২টি চাইল্ড থাকতে পারে, অর্থাৎ চাইল্ড সংখ্যা ০, ১ বা ২ হতে পারে (at most 2)।

7. **A B* tree can contain a maximum of 7 pointers in a node. What is the minimum number keys in leaves?** *[NPCBL Executive Trainee (Software) 2023 compact it 39 (ET: N/A)]*
   a) 6
   b) 3
   c) 4
   d) 7
answer: c
explanation: m অর্ডারের B* Tree-তে প্রতিটি নন-রুট নোড কমপক্ষে 2/3 পূর্ণ থাকে। সর্বোচ্চ ৭টি পয়েন্টার থাকলে নোডের ন্যূনতম কী সংখ্যা হয় floor((2m - 1) / 3) = floor(13 / 3) = 4।

8. **In a completer k-array, every internal node has exactly k children. The number of leaves in such a tree with n internal nodes is-** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 26 (ET: BIBM)]*
   (a) (n-1)k+1
   (b) nk
   (c) n(k-1)
   (d) n(k-1)+1
answer: d
explanation: মোট নোড N = n + L। এজ সংখ্যা = N - 1 = n * k। ফলে n + L - 1 = n * k => L = n(k - 1) + 1।

9. **Access time of the symbolic table will be logarithmic if it is implemented by-** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 28 (ET: BIBM)]*
   (a) Linear list
   (b) Search tree
   (c) Hash table
   (d) Self organization list
answer: b
explanation: ব্যালান্সড সার্চ ট্রি (যেমন AVL বা Red-Black Tree) দিয়ে সিম্বল টেবিল বানালে এর সার্চিং সময় O(log n) বা লগারিদমিক হয়।

10. **What is the minimum node for binary tree?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*
    **Ans:** For a binary tree, max node = [2^{	ext{h}} + 1] and min node = [2	ext{h} + 1].
answer: 2h + 1 (or h + 1)
explanation: উচ্চতা h হলে একটি সাধারণ বাইনারি ট্রির সর্বনিম্ন নোড সংখ্যা h + 1 (বা ফুল বাইনারি ট্রির ক্ষেত্রে 2h + 1) এবং সর্বোচ্চ নোড সংখ্যা 2^(h+1) - 1।

11. **The Post-order traversal of a binary tree is 8, 9, 6, 7, 4, 5, 2, 3, 1, The In-order traversal of the same tree is 8, 6, 9, 4, 7, 2, 5, 1, 3. What is the height of the above binary tree?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 89 (ET: N/A)]*
    a. 2
    b. 3
    c. 4
    d. 1
answer: c
explanation: ট্রি পুনর্গঠন করলে দেখা যায়: রুট 1, এর বাম চাইল্ড 2, 2-এর বামে 4, 4-এর বামে 6, এবং 6-এর সন্তান 8 ও 9। রুট থেকে গভীরতম লিফ (8 বা 9) পর্যন্ত সর্বোচ্চ এজ দূরত্ব বা উচ্চতা হলো 4।

12. **The pre order traversal of binary tree is 40, 20, 10, 30, 60, 50, 70. Which one of the is the post-order traversal of the tree?** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 174 (ET: N/A)]*
    a) 10,20,30,40,50,60,70
    b) 10,30,20,50,70,60,40
    c) 40,20,60,10,30,50,70
    d) 70,50,60,30,10,20,40
answer: b
explanation: BST-এর নিয়মে রুট 40; বাম সাব-ট্রি {20, 10, 30}-এর পোস্ট-অর্ডার 10, 30, 20; ডান সাব-ট্রি {60, 50, 70}-এর পোস্ট-অর্ডার 50, 70, 60। সম্পূর্ণ পোস্ট-অর্ডার (Left-Right-Root): 10, 30, 20, 50, 70, 60, 40।

13. **Suppose we have a Binary Search Tree where each node has an integer value. Which of the following tree traversal techniques can give us a sorted list (in ascending order) of those integers?** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 180 (ET: N/A)]*
    a) Pre-order traversal
    b) In-order traversal
    c) Post-order traversal
    d) BFS traversal
answer: b
explanation: BST-তে ইন-অর্ডার ট্রাভার্সাল (In-order traversal) সর্বদা আরোহী বা ছোট থেকে বড় (Ascending) সাজানো তালিকা প্রদান করে।

14. **If we represent a binary tree using array, what will be the children of node “n”-** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 166 (ET: N/A)]*
    a) 2n & 2n+1
    b) 2n & 2-n
    c) (n+1)2
    d) 2n & 2n-1
answer: a
explanation: ১-ভিত্তিক অ্যারে উপস্থাপনায় n তম নোডের বাম চাইল্ড 2n এবং ডান চাইল্ড 2n+1 এ অবস্থান করে।

15. **In which tree structure left to right subtree height differs not more than 1?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 168 (ET: N/A)]*
    a) Binary tree
    b) BST
    c) AVL tree
    d) Binary Heap
answer: c
explanation: AVL Tree হলো একটি সেলফ-ব্যালান্সিং BST, যার প্রতিটি নোডের ব্যালান্স ফ্যাক্টর (বাম ও ডান সাব-ট্রির উচ্চতার পার্থক্য) -১, ০ বা +১ এর মধ্যে সীমাবদ্ধ থাকে।

16. **Maximum how many nodes can be placed in a binary Tree of N levels?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 155 (ET: DU)]*
    a) 2^N
    b) 2^N - 1
    c) 2^{N-1} - 1
    d) N^2
answer: b
explanation: N টি লেভেলবিশিষ্ট (Level 1 থেকে N) একটি বাইনারি ট্রিতে সর্বোচ্চ নোড সংখ্যা হতে পারে 2^N - 1।

17. **Max-Heap data structure এর সবচেয়ে বড় নম্বরটি কোথায় থাকে?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 186 (ET: N/A)], [BPSC Assistant Network Engineer 2019 compact it 197 (ET: N/A)]*
    A) Leaf
    B) Internal node
    C) Root
    D) Outside
answer: C
explanation: Max-Heap-এর বৈশিষ্ট্য অনুযায়ী প্যারেন্টের মান চাইল্ডের মানের চেয়ে বড় বা সমান হয়, তাই সমগ্র ট্রির বৃহত্তম মানটি সর্বদা রুট (Root) নোডে থাকে।

18. **Complete Binary tree যার height n, তার মধ্যে node কতটি?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 187 (ET: N/A)]*
    A) n
    B) 2^n
    C) 2^{n-1}
    D) 2^{n+1}-1
answer: D
explanation: উচ্চতা n বিশিষ্ট একটি পারফেক্ট/ফুল বাইনারি ট্রিতে (রুটের উচ্চতা ০ ধরে) সর্বোচ্চ 2^(n+1) - 1 টি নোড থাকতে পারে।

19. **Binary Search Tree-এর Time complexity কত?** *[BPSC Assistant Network Engineer 2019 compact it 196 (ET: N/A)]*
    A) O(n)
    B) O(n \log n)
    C) O(\log n)
    D) O(n^2)
answer: C
explanation: ব্যালান্সড বাইনারি সার্চ ট্রিতে অনুসন্ধান (Search), সংযোজন (Insert) এবং অপসারণ (Delete) অপারেশনের গড় সময় কমপ্লেক্সিটি হলো O(log n)।

20. **Which of the following is false about a binary search tree?** *[Combined 3 Bank Assistant Programmer 2018 compact it 232 (ET: N/A)]*
    A) The left child is always lesser than its parent
    B) The right child is always greater than its parent
    C) The left and right subtrees should also be binary search trees
    D) In order sequence gives decreasing order of elements
answer: D
explanation: BST-এর ইন-অর্ডার ট্রাভার্সাল উপাদানগুলোকে ঊর্ধ্বক্রমে বা ক্রমবর্ধমান (Increasing / Ascending order) আকারে দেয়, নিম্নক্রমে (Decreasing) নয়। সুতরাং D উক্তিটি মিথ্যা।

## Data Structures & Algorithms (12)
1. **When sorting an array using randomized quicksort (pivot chosen randomly), what are the average-case and worst-case time complexities? [ যখন একটি অ্যারে randomized quicksort ব্যবহার করে sort করা হয় (pivot র‍্যান্ডমভাবে নির্বাচন করা হয়), তখন এর average-case এবং worst-case time complexity কী হবে?]** *[Combined Bank Senior Officer (IT) Date: 17.10.2025 [bitbox it book 216]]*
   (a) O(n \log n), O(n)
   (b) O(n \log n), O(n^2)
   (c) O(n), O(n \log n)
   (d) O(n^2), O(n^2)
answer: b
explanation: Randomized quicksort-এ র্যান্ডম পিভট নির্বাচনের ফলে গড় সময় কমপ্লেক্সিটি হয় O(n log n), তবে চরম দুর্ভাগ্যজনক ক্ষেত্রে (যখন বারবার ক্ষুদ্রতম বা বৃহত্তম উপাদান পিভট হয়) ওর্স্ট-কেস কমপ্লেক্সিটি O(n^2) হতে পারে।

2. **Which of the following is not a linear data structure? [ নিচের কোনটি linear data structure নয়?]** *[Combined Bank Senior Officer (IT) Date: 17.10.2025 [bitbox it book 219]]*
   (a) Queue
   (b) Stack
   (c) Tree
   (d) Linked List
answer: c
explanation: Tree হলো একটি নন-লিনিয়ার (হায়ারার্কিকাল) ডেটা স্ট্রাকচার। Queue, Stack এবং Linked List লিনিয়ার ডেটা স্ট্রাকচার।

3. **Which OS concept allows multiple processes to run simultaneously? [ কোন OS concept একাধিক process একসাথে চলার অনুমতি দেয়?]** *[Combined Bank Senior Officer (IT) Date: 17.10.2025 [bitbox it book 219]]*
   (a) Multithreading
   (b) Multiprocessing
   (c) Multilevel Queue
   (d) Time slicing
answer: b
explanation: Multiprocessing সিস্টেমে একাধিক প্রসেসর বা কোর থাকায় একাধিক স্বতন্ত্র প্রসেস প্রকৃতপক্ষে একই সময়ে সমান্তরালভাবে (Simultaneously) চলতে পারে।

4. **Which data structure follows FIFO (First In First Out) principle? [ কোন ডেটা স্ট্রাকচার FIFO (First In First Out) নীতি মেনে চলে? ]** *[Bankers' Selection Committee Secretariat Post: Assistant Programmer; Date: 15 Feb, 2024 Exam Taker: ANZA; Post: 35 [bitbox it book 349]]*
   (A) Stack
   (B) Queue
   (C) Tree
   (D) Graph
answer: B
explanation: Queue ডেটা স্ট্রাকচার FIFO (First In First Out) মূলনীতি অনুযায়ী কাজ করে।

5. **How can you multiply two square 16\*16 matrices on a computer processor that can only handle 8\*8 matrix multiplications? Write an algorithm for this problem?** *[Bakhrabad Gas Distribution Company limited (BGDCL) Post: Assistant Engineer Date: 15 March, 2024 Exam Taker: BUET Marks: 20 MCQ; Written: 5\*8=40 [bitbox it book 380]]*
answer: Block Matrix Multiplication
explanation: ১৬×১৬ ম্যাট্রিক্স A ও B-কে চারটি করে ৮×৮ ব্লকে ভাগ করতে হবে: A = [[A11, A12], [A21, A22]] এবং B = [[B11, B12], [B21, B22]]। এরপর C11 = A11*B11 + A12*B21, C12 = A11*B12 + A12*B22, C21 = A21*B11 + A22*B21, C22 = A21*B12 + A22*B22 নিয়মে ৮টি ৮×৮ ম্যাট্রিক্স গুণ ও ৪টি যোগের মাধ্যমে গুণফল নির্ণয় করা যায়।

6. **How can a binary tree be represented using an array, and how are the positions of the left and right children determined based on the index of the parent node?** *[Bakhrabad Gas Distribution Company limited (BGDCL) Post: Assistant Engineer Date: 15 March, 2024 Exam Taker: BUET Marks: 20 MCQ; Written: 5\*8=40 [bitbox it book 381]]*
answer: Array Representation of Binary Tree
explanation: বাইনারি ট্রিকে অ্যারেতে লেভেল-অর্ডার অনুযায়ী রাখা হয়। ১-ভিত্তিক ইনডেক্সিংয়ে i তম প্যারেন্ট নোডের জন্য: বাম চাইল্ড = 2*i এবং ডান চাইল্ড = 2*i + 1। (০-ভিত্তিক ইনডেক্সিংয়ে বাম চাইল্ড = 2*i + 1 এবং ডান চাইল্ড = 2*i + 2)।

7. **a) একটি Stack এ 1, 2, 2, 3, 3, 3 push করা হলো। এরপর পর পর দুইবার pop করা হলো। এর পর আবারো pop করা হলে কোন সংখ্যা বের হবে।** *[Titas Gas Distribution Company Limited Post: Sub Assistant Enginner; Date: 24 May, 2024 Exam Taker: BUET; Total:MCQ:20, Written:40 [compact it 449]]*
answer: 3
explanation: পুশ করার পর স্ট্যাকের উপাদান নিচ থেকে উপরে থাকে: [1, 2, 2, 3, 3, 3]। পরপর দুটি pop-এ শীর্ষের দুটি 3 বের হয়। তৃতীয়বার pop করলেও স্ট্যাকের বর্তমান শীর্ষ উপাদান 3-ই বের হবে।

8. **b) মনে কর একটি Sorted array রয়েছে। সেখান থেকে একটি সংখ্যা খুঁজে বের করতে হবে যা minimum সময় নিবে তখন তুমি কোন সার্চিং Algorithm ব্যবহার করবে?** *[Titas Gas Distribution Company Limited Post: Sub Assistant Enginner; Date: 24 May, 2024 Exam Taker: BUET; Total:MCQ:20, Written:40 [compact it 449]]*
answer: Binary Search
explanation: সর্টেড অ্যারে থেকে সর্বনিম্ন সময়ে (মাত্র O(log n) কমপ্লেক্সিটিতে) উপাদান অনুসন্ধানের জন্য Binary Search অ্যালগরিদম ব্যবহার করতে হবে।

9. **BIDS published many Monographs every year. Now write an algorithm to sort them.** *[Bangladesh Institute of Development Studies Programmer; Date: 06 July, 2024 Exam Taker: BUET; Total:MCQ:20, Written:40 [bitbox it book 485]]*
answer: Merge Sort Algorithm
explanation: মনোগ্রাফের তালিকার জন্য Merge Sort উপযুক্ত: ১. মনোগ্রাফ তালিকাকে দুটি সমান ভাগে বিভক্ত করা হয় (Divide); ২. প্রতিটি অংশকে রিকার্সিভলি সর্ট করা হয়; ৩. পরিশেষে দুটি সাজানো অংশকে তুলনা করে মার্জ (Merge) করা হয়। এর সময় কমপ্লেক্সিটি নিশ্চিতভাবে O(n log n)।

10. **The minimum number of stacks needed to implement a queue is—[ একটি কিউ (Queue) ইমপ্লিমেন্ট করার জন্য সর্বনিম্ন কয়টি স্ট্যাক (Stack) প্রয়োজন? ]** *[Bankers' Selection Committee Secretariat Post: Senior Office (IT); Date: 04 October, 2024 Exam Taker: ANZA; Post: 222 [bitbox it book 506]]*
    (a) 1
    (b) 2
    (c) 3
    (d) 4
answer: b
explanation: একটি FIFO কিউ বাস্তবায়ন করতে সর্বনিম্ন ২টি স্ট্যাক প্রয়োজন হয়।

11. **Suppose you are given a binary tree with 11 nodes, such that each node has exactly either zero or two children. The maximum height of the tree will be—[ ১১টি নোড বিশিষ্ট একটি বাইনারি ট্রিতে প্রতিটি নোডের হয় ০ অথবা ২টি চাইল্ড আছে। এই ট্রির সর্বোচ্চ উচ্চতা (Height) কত হবে? ]** *[Bankers' Selection Committee Secretariat Post: Senior Office (IT); Date: 04 October, 2024 Exam Taker: ANZA; Post: 222 [bitbox it book 507]]*
    (a) 2
    (b) 3
    (c) 4
    (d) 5
answer: d
explanation: প্রতিটি নোডের ০ বা ২টি সন্তান থাকলে তাকে ফুল বাইনারি ট্রি বলে। উচ্চতা h হলে সর্বনিম্ন নোড সংখ্যা N = 2h + 1। ফলে 2h + 1 = 11 => 2h = 10 => h = 5।

12. **The following method, which is intended to find the maximum element of the integer array, is incorrect.[ অ্যারোর সর্বোচ্চ মান খুঁজে বের করার নিচের মেথডটি ভুল কেন? ] public int max(int[]** *[Bankers' Selection Committee Secretariat Post: Senior Office (IT); Date: 04 October, 2024 Exam Taker: ANZA; Post: 222 [bitbox it book 511-512]]*
    a) {

     int max = 0;

     for(int i = 0; i <
    a. length; i++) {

         if(a[i] > max)

             max = a[i];

     }

     return max;

 }
    (a) It fails whenever the array contains a 0
    (b) It fails whenever the array contains a negative number
    (c) It fails whenever the array contains only negative numbers
    (d) It fails whenever the first element of the array is the largest
answer: c
explanation: মেথডটিতে max-এর প্রারম্ভিক মান 0 ধরা হয়েছে। যদি অ্যারেতে কেবল ঋণাত্মক সংখ্যা থাকে (যেমন: [-3, -8, -5]), তবে কোনো উপাদানই 0-এর চেয়ে বড় হবে না এবং মেথডটি ভুলবশত 0 রিটার্ন করবে। তাই It fails whenever the array contains only negative numbers।

## Linked List (10)

1. **What is the worst case time complexity of inserting n elements into an empty linked list, if the linked list needs to be maintained in sorted order?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xx (ET: DU)]*
   (a) \Theta(n)
   (b) \Theta(n \log n)
   (c) \Theta(n^2)
   (d) \Theta(1)

2. **In the worst case, the number of comparisons needed to search a singly linked list oflength n for a given element is-** *[Combined Bank Officer (IT) 04.10.2024 compact it 15 (ET: BIBM)]*
   (a) \log(2*n)
   (b) \frac{n}{2}
   (c) n
   (d) \log(2*n)-1

3. **Let P be a singly linked list. Let Q be the pointer to an intermediate node x in the list. What is the worst-case time complexity of the best known algorithm to delete the node Q from the list?** *[Combined Bank Assistant Programmer 09.02.2024 compact it 20 (ET: BIBM)]*
   (A) O(n)
   (B) O(log2 n)
   (C) O(logn)
   (D) O(1)

4. **In a doubly linked list, the number of pointers affected for an insertion operation will be-** *[Combined Bank Assistant Programmer 09.02.2024 compact it 20 (ET: BIBM)]*
   (A) 5
   (B) 0
   (C) 1
   (D) None of these

5. **The time required to search an element in a linked list of length n is-** *[Combined Bank Assistant Programmer 09.02.2024 compact it 20 (ET: BIBM)]*
   (A) O (log n)
   (B) O (n)
   (C) O (1)
   (D) O (n^2)

6. **The minimum number of fields with each node of doubly linked list is** *[Combined Bank Assistant Programmer 09.02.2024 compact it 21 (ET: BIBM)]*
   (A) 1
   (B) 2
   (C) 3
   (D) 4

7. **What does following function do for a given Linked List with first node as head?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 88 (ET: N/A)]*
   ```c
   void fun1(struct node* head) {
   if (head == NULL)
   return;
   fun1(head->next);
   printf("%d",head->data);
   }
   ```
   a. Prints all nodes of linked lists
   b. Prints all nodes of linked list in reverse order
   c. Prints alternate nodes of Linked List
   d. Prints alternate nodes in reverse order

8. **Suppose you want to insert n elements into an empty linked list while maintaining the sorted order. What is the worst-case time complexity?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 88 (ET: N/A)]*
   a. \theta(n)
   b. \theta(n\log n)
   c. \theta(1)
   d. \theta(n^2)

9. **Link list can be implement using?** *[Probashi Kallyan Bank Assistant Programmer: 2019 compact it 215 (ET: AUST)]*
   A) Array
   B) Pointers
   C) Both A & B
   D) None of these

10. **What is the time complexity to count the number of elements in the linked list?** *[Combined 3 Bank Assistant Programmer 2018 compact it 231 (ET: N/A)]*
   A) O(1)
   B) O(n)
   C) O(\log n)
   D) O(n \log n)

## Priority Queue & Heap (3)

1. **Which data structure is preferred for Priority Queue?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xviii (ET: DU)]*
   (a) Heap Tree
   (b) Graph
   (c) Stack
   (d) Table

2. **What is the best way to implement priority queue?** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xx (ET: DU)]*
   (a) Array
   (b) Linked List
   (c) Heap
   (d) Stack

3. **In the priority queue, insertion and deletion take place at –** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 126 (ET: N/A)]*
   a) Front and rear end
   b) Only at the front end
   c) Only at the rear end
   d) Any position

## Hashing & Hash Tables (2)

1. **Given a hash table with 25 slots that stores 2000 elements, the load factor for the hash table is-** *[Combined Bank Officer (IT) 04.10.2024 compact it 15 (ET: BIBM)]*
   (a) 0.012506
   (b) 1.25
   (c) 80
   (d) 8000

2. **Which of the following symbol table implementation is best suited if access time is to be minimum?** *[Combined Bank Officer (IT) 04.10.2024 compact it 15 (ET: BIBM)]*
   (a) Linear list
   (b) Linked list
   (c) Hash table
   (d) Self-organizing list
