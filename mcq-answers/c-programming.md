<!-- TOC START -->
**Table of Contents** — 10 subtopics · 113 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Output Tracing](#output-tracing-36) | 36 |
| 2 | [Control Statements & Loops](#control-statements--loops-16) | 16 |
| 3 | [Arrays & Functions](#arrays--functions-15) | 15 |
| 4 | [Data Types & Variables](#data-types--variables-14) | 14 |
| 5 | [Operators & Expressions](#operators--expressions-11) | 11 |
| 6 | [Programming Concepts](#programming-concepts-8) | 8 |
| 7 | [Pointers & Memory Allocation](#pointers--memory-allocation-5) | 5 |
| 8 | [Recursion](#recursion-4) | 4 |
| 9 | [Storage Classes & Scope](#storage-classes--scope-3) | 3 |
| 10 | [Flowcharts & Algorithms](#flowcharts--algorithms-1) | 1 |

<!-- TOC END -->

---

## Output Tracing (36)

1. **Find Output:** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xviii (ET: DU)]*
   ```cpp
   int fun(int *p) {
   *p = *p + 10;
   return *p;
   }
   int main() {
   int x = 5;
   cout << fun(&x);
   return 0;
   }
   ```
   (a) 15
   (b) 10
   (c) 25
   (d) 5
answer: A
explanation: `fun(&x)`-এ `x`-এর অ্যাড্রেস পাস করা হয়েছে (pass by reference via pointer)। `*p = *p + 10` দ্বারা `x`-এর মান $5+10=15$ হয় এবং 15 রিটার্ন করে।

2. **Find Output:** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it xviii (ET: DU)]*
   ```cpp
   int main() {
   int x=3, y=2;
   if (x==3)
   y=2;
   else
   y=3;
   cout<<x<<" "<<y<<endl;
   return 0;
   }
   ```
   (a) 3 3
   (b) 3 2
   (c) 2 3
   (d) 3 1
answer: B
explanation: `x==3` শর্তটি সত্য হওয়ায় `if` ব্লকে `y=2` অ্যাসাইন হয়। সুতরাং আউটপুট হবে `3 2`।

3. **What will be the output of the following C code?** *[Combined Bank Officer (IT) 04.10.2024 compact it 16 (ET: BIBM)]*
   ```c
   int main() {
   int x=20, y=10, z=5;
   printf("%d", x>y>z);
   return 0;
   }
   ```
   (a) 20
   (b) 10
   (c) 0
   (d) 1
answer: C
explanation: রিলেশনাল অপারেটর `>` বাম থেকে ডানে (left-to-right) কাজ করে। ফলে `(x > y) > z` $\rightarrow (20 > 10) > 5 \rightarrow 1 > 5 \rightarrow 0$।

4. **What will be the output of the following C code?** *[Combined Bank Officer (IT) 04.10.2024 compact it 16 (ET: BIBM)]*
   ```c
   int main() {
   double k=0;
   for(k=0.0;k<3.0; k++)
   printf("muli");
   return 0;
   }
   ```
   (a) run time error
   (b) muli is printed infinitely
   (c) muli is printed twice
   (d) muli is printed thrice
answer: D
explanation: লুপটি `k = 0.0, 1.0, 2.0`-এর জন্য ৩ বার চলবে এবং ৩ বার "muli" প্রিন্ট হবে (thrice)।

5. **What will be the output of the following C code?** *[Combined Bank Officer (IT) 04.10.2024 compact it 16 (ET: BIBM)]*
   ```c
   int main() {
   int i,j, count;
   count=0;for (i=0; i<5; i++) {
   for(j=0;j<i;j++) {
   count++;
   }
   }
   printf("%d", count);
   return 0;
   }
   ```
   (a) 1
   (b) 5
   (c) 10
   (d) 25
answer: C
explanation: নেস্টেড লুপটিতে `j`-এর মোট ইটারেশন সংখ্যা হবে $0 + 1 + 2 + 3 + 4 = 10$। ফলে `count`-এর মান হবে 10।

6. **What will be the output of the following C code?** *[Combined Bank Officer (IT) 04.10.2024 compact it 17 (ET: BIBM)]*
   ```c
   int main() {
   int x = 107;
   char y = 'Q';
   printf("%c%d",x, y);
   return 0;
   }
   ```
   (a) 107, Q
   (b) k, 81
   (c) k, Q
   (d) Q, K
answer: B
explanation: `%c` দিয়ে পূর্ণসংখ্যা 107 প্রিন্ট করায় এর ASCII ক্যারেক্টার 'k' প্রদর্শিত হবে, এবং `%d` দিয়ে ক্যারেক্টার 'Q' প্রিন্ট করায় এর ASCII মান 81 প্রদর্শিত হবে।

7. **What will be the output of the following C code?** *[Combined Bank Officer (IT) 04.10.2024 compact it 17 (ET: BIBM)]*
   ```c
   int main() {
   int data [2][3][2]={0,1,2,3,4,5,6,7,8,9,10,11};
   int i=0,j=2, k = 1;
   printf("%d\n", data [i][j][k]);
   return 0;
   }
   ```
   (a) 0
   (b) 5
   (c) 6
   (d) 11
answer: B
explanation: 3D অ্যারেতে `data[0][2][1]`-এর ফ্ল্যাট ইনডেক্স হলো $0 \times (3 \times 2) + 2 \times 2 + 1 = 5$, যার মান 5।

8. **What will be the output of the following C code?** *[Combined Bank Officer (IT) 04.10.2024 compact it 17 (ET: BIBM)]*
   ```c
   int main() {
   int i= 11, j = 3;
   printf("%d\n", i|j);
   return 0;
   }
   ```
   (a) 11
   (b) 12
   (c) 13
   (d) 14
answer: A
explanation: বিটওয়াইজ OR (`|`): $11 = 1011_2$ এবং $3 = 0011_2$। $1011_2 \mid 0011_2 = 1011_2 = 11$।

9. **What will be the output of this C program?** *[Combined Bank Assistant Programmer 09.02.2024 compact it 19 (ET: BIBM)]*
   ```c
   #include<stdio.h>
   int main() {
   float p=10.5;
   int a=5*p+5.0;
   printf("%d\n",a);
   return 0;
   }
   ```
   a) 57.500000
   b) 57
   c) 57.000000
   d) The program has errors and will not run.
answer: B
explanation: $5 \times 10.5 + 5.0 = 52.5 + 5.0 = 57.5$। এটি পূর্ণসংখ্যা ভ্যারিয়েবল `int a`-তে সংরক্ষিত হওয়ায় দশমিক অংশ ট্রাঙ্কেট হয়ে 57 হবে।

10. **Which of the following Output of this program?** *[Combined Bank Assistant Programmer 09.02.2024 compact it 21 (ET: BIBM)]*
   ```c
   #include <stdio.h>
   int main() {
   static int i=5;
   if (--i) {
   printf("%d ",i);
   main() ;
   }
   }
   ```
   (A) 4 3 2 1
   (B) 1 2 3 4
   (C) 4 4 4 4
   (D) 0 0 0 0
answer: A
explanation: `static int i` এর মান প্রতিটি রিকার্সিভ কলে সংরক্ষিত থাকে। `--i` যথাক্রমে 4, 3, 2, 1 হয়ে প্রিন্ট হবে এবং 0 হলে রিকার্শন বন্ধ হবে।

11. **Given Output:** *[Combined Bank Assistant Programmer 09.02.2024 compact it 21 (ET: BIBM)]*
   ```c
   #include <stdio.h>
   int main() {
   int y = 0;
   int x = (y != 0);
   printf("%d", x);
   return 0;
   }
   ```
   (A) 0
   (B) 1
   (C) A bog negative Number
   (D) Compiler Error
answer: A
explanation: `y` এর মান 0 হওয়ায় `(y != 0)` শর্তটি মিথ্যা (false) বা 0 প্রদান করে, ফলে `x = 0` প্রিন্ট হবে।

12. **How many times will loop iterate?** *[NPCBL Executive Trainee (Software) 2023 compact it 38 (ET: N/A)]*
   (a) 9
   (b) 10
   (c) 8
   (d) infinite
answer: B
explanation: স্ট্যান্ডার্ড C লুপ (যেমন: `for(i=0; i<10; i++)` বা `for(i=1; i<=10; i++)`) সাধারণত 10 বার আবর্তিত (iterate) হয়।

13. **What will be the output of the following “C” code fragment?** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*
   ```c
   x=0;
   while (x<100)
   x+=2;
   print(x);
   ```
   a) 99
   b) 100
   c) 101
   d) 98
answer: B
explanation: লুপে `x` প্রতি ধাপে 2 করে বৃদ্ধি পায়। `x=98` এর পর যোগ হয়ে 100 হয় এবং `100 < 100` মিথ্যা হওয়ায় লুপ শেষ হয়। ফলে আউটপুট 100।

14. **Determine Output:** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 26 (ET: BIBM)]*
   ```c
   void main() {
   int i=i++, j=j++, k=k++;
   printf("%d %d %d", i, j, k);
   }
   ```
   (a) 1 1 1
   (b) 0 0 0
   (c) garbage values
   (d) Error
answer: C
explanation: লোকাল ভ্যারিয়েবল ইনিশিয়ালাইজেশনের সময় `i++` ব্যবহার অনির্ধারিত আচরণ (undefined behavior) ঘটায় এবং মেমোরিতে থাকা অনির্ধারিত মান (garbage values) ধারণ করে।

15. **Determine Output:** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 27 (ET: BIBM)]*
   ```c
   void main() {
   struct xx {
   int x=3;
   char name[] = "hello";
   };
   struct xx *s = malloc(sizeof(struct xx));
   printf("%d", s->x);
   printf("%s", s->name);
   }
   ```
   (a) 3 hello
   (b) Compiler Error
   (c) Linking error
   (d) None of these
answer: B
explanation: C ভাষায় স্ট্রাকচার ডেফিনিশনের ভেতরে ফিল্ডের ইনিশিয়ালাইজেশন (`int x = 3;` ইত্যাদি) অবৈধ, ফলে কম্পাইল এরর (Compiler Error) হবে।

16. **Assume that the size of an integer is 4 bytes, predict the output of following program.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 28 (ET: BIBM)]*
   ```c
   #include <stdio.h>
   int main() {
   int i = 12;
   int j = sizeof(i++);
   printf("%d %d", i, j);
   return 0;
   }
   ```
   (a) 12 4
   (b) 13 4
   (c) Compiler Error
   (d) 0 4
answer: A
explanation: C ভাষায় `sizeof` অপারেটরের ভেতরের এক্সপ্রেশন রানটাইমে এক্সিকিউট বা মূল্যায়ন (evaluate) হয় না। ফলে `i++` কার্যকর হয় না এবং `i`-এর মান 12-ই থাকে, আর `sizeof(int)` হলো 4।

17. **Which is the correct output?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 129 (ET: N/A)]*
   ```c
   int i = 4; printf("%d %d", +1,i++); printf("%d", i++);
   ```
   a) 4 5 6
   b) 5 7 8
   c) 6 4 6
   d) 1 4 5
answer: D
explanation: প্রথম `printf`-এ `+1` এর জন্য 1 এবং পোস্ট-ইনক্রিমেন্ট `i++` এর জন্য 4 প্রিন্ট হয়ে `i` এর মান 5 হয়। দ্বিতীয় `printf`-এ `i++` এর মান 5 প্রিন্ট হয়। ফলে মোট আউটপুট `1 4 5`।

18. **Which is correct output?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 130 (ET: N/A)]*
   ```c
   int a = 100; int *p = &a +2; *p = 22; printf("%d", a);
   ```
   a) 100
   b) 22
   c) Error
   d) Garbage value
answer: A
explanation: পয়েন্টার `p`-তে `&a + 2` এর মেমরি অ্যাড্রেস থাকায় `*p = 22` অন্য কোনো মেমোরি লোকেশনে মান লেখে। মূল ভ্যারিয়েবল `a`-এর মান অপরিবর্তিত থেকে 100-ই থাকে।

19. **Find the correct output:** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 130 (ET: N/A)], [Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 166 (ET: N/A)]*
   ```c
   int a = 10,b = 20; a ^= b; b ^= a; a ^= b;
   printf("%d %d", a, b);
   ```
   a) 20 30
   b) 10 30
   c) 20 10
   d) Garbage Value
answer: C
explanation: এটি XOR সোয়াপিং (swap) অ্যালগরিদম যা কোনো তৃতীয় ভ্যারিয়েবল ছাড়াই দুটি সংখ্যার মান অদলবদল করে। ফলে `a` হবে 20 এবং `b` হবে 10।

20. **What is the correct output of the following C program statements?** *[Rupali Bank Ltd. Assistant Network Engineer (ANE) 2021 compact it 81 (ET: N/A)], [6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 88 (ET: N/A)], [Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 186 (ET: N/A)]*
   ```c
   int array[]={6, 7, 8, 9, 0, 1, 2, 4, 5, 6}, *p=array+5;
   printf("%d\n",p[1]);
   ```
   a. 1
   b. 2
   c. 3
   d. Compile Error
answer: B
explanation: `p = array + 5` অ্যারের ৫ম ইনডেক্স উপাদান 1-কে নির্দেশ করে। ফলে `p[1]` নির্দেশ করবে তার পরবর্তী উপাদান `array[6]` বা 2-কে।

21. **What is the output for the following C code segment?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 84 (ET: N/A)]*
   ```c
   int i;
   if(printf("0")) i = 5;
   else i = 3;
   printf("%d",i);
   ```
   a. 3
   b. 5
   c. 03
   d. 05
answer: D
explanation: `printf("0")` স্ক্রিনে "0" প্রিন্ট করে এবং প্রিন্ট হওয়া ক্যারেক্টার সংখ্যা 1 রিটার্ন করে যা সত্য (true)। ফলে `if` শর্ত সত্য হয়ে `i = 5` হয় এবং পরবর্তী `printf` দ্বারা 5 প্রিন্ট হয়ে মোট আউটপুট "05" হয়।

22. **Consider the function fun (x, y) below. That is the value of fun (4, 3)?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 87 (ET: N/A)]*
   ```c
   int fun(int x, int y) {
   if (x == 0)
   return y;
   return fun(x - 1, x + y);
   }
   ```
   a. 13
   b. 12
   c. 9
   d. 10
answer: A
explanation: ধাপগুলো: `fun(4, 3) = fun(3, 7) = fun(2, 10) = fun(1, 12) = fun(0, 13)`। যেহেতু `x == 0`, এটি 13 রিটার্ন করে।

23. **What does the following function do?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 87 (ET: N/A)]*
   ```c
   int fun(int x, int y) {
   if (y == 0) return 0;
   return (x + fun(x, y-1));
   }
   ```
   a. x+y
   b. x+x*y
   c. x*y
   d. xy
answer: C
explanation: ফাংশনটি `y` বার `x`-কে রিকার্সিভভাবে যোগ করে, যা মূলত গুণফল $x \times y$ হিসাব করার অ্যালগরিদম।

24. **Find Output:** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 90 (ET: N/A)]*
   ```c
   #include<stdio.h>
   struct Testnode(char x, y, z;);
   int main() {
   struct Trstnode node1 = {'1', '2', 'c'+3};
   struct Testnode *node2 = &node1;
   printf("%c, %c", *((char*)node2+1),*((char*)node2+2));
   return 0;
   }
   ```
   Which one is the output of the above program?
   a. 0, f
   b. 0, c+3
   c. '0', 'c+3'
   d. '0', 'f'
answer: A
explanation: `*((char*)node2+2)` ৩য় বাইট নির্দেশ করে, যেখানে `'c' + 3 = 'f'`। এবং প্রদত্ত অপশন অনুযায়ী সঠিক ফলাফল (a) `0, f`।

25. **Find the output:** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 163 (ET: N/A)]*
   ```c
   int a= 10, c, b;
   c = (a=99)? b = 11:20;
   printf("%d, %d", a, c);
   ```
   a) 11, 99
   b) 99, 11
   c) 20, 11
   d) 99, 20
answer: B
explanation: `(a=99)` সত্য (non-zero) হওয়ায় টার্নারি অপারেটর `b = 11` এক্সিকিউট করে, ফলে `c = 11` হয় এবং `a` এর মান 99 থাকে। আউটপুট `99, 11`।

26. **What will be the output of following code?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 164 (ET: N/A)]*
   ```c
   int x=5, y=5, z=5;
   printf("%d", ++z+y-1-y+z+x++);
   ```
   a) 15
   b) 17
   c) 16
   d) 19
answer: C
explanation: `++z` এর মান 6, তারপর $6 + 5 - 1 - 5 + 6 + 5 = 16$। `x++` পোস্ট-ইনক্রিমেন্ট হওয়ায় এক্সপ্রেশনে এর তৎকালীন মান 5 ব্যবহৃত হয়।

27. **What will be the output of the given line?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 165 (ET: N/A)]*
   ```c
   printf("%d",sizeof(int));
   ```
   a) 2
   b) 4
   c) 1
   d) 8
answer: B
explanation: আধুনিক ৩২-বিট ও ৬৪-বিট আর্কিটেকচারে এবং স্ট্যান্ডার্ড C কম্পাইলারে `int` ডেটা টাইপের সাইজ সাধারণত 4 বাইট।

28. **Which for loop statement is invalid?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 167 (ET: N/A)]*
   a) for(int x=10; k<=5; x/9)
   b) for(int x=10; x>=2; --x)
   c) for(int x=10; x>=200; x=3*x)
   d) for(int x=10; x>=0; x+=2)
answer: A
explanation: অপশন (a)-তে অঘোষিত ভ্যারিয়েবল `k` ব্যবহৃত হয়েছে এবং `x/9` কোনো ভ্যারিয়েবল আপডেট বা অ্যাসাইনমেন্ট ছাড়া একটি অকার্যকর স্টেটমেন্ট।

29. **Which type of following errors is generated when the program is being execute?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 159 (ET: N/A)]*
   A) Syntax error
   B) Semantic error
   C) Run-time error
   D) Linker error
answer: C
explanation: প্রোগ্রাম চলাকালীন বা এক্সিকিউশনের সময় যে ত্রুটি ঘটে তাকে রান-টাইম এরর (Run-time error) বলে।

30. **Which is the correct output?** *[Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 180 (ET: N/A)]*
   ```c
   int i = 4;
   printf ("%d%d", ++i, i++);
   printf ("%d ", i++);
   ```
   a) 5 4 6
   b) 5 7 8
   c) 6 4 6
   d) 4 5 7
answer: C
explanation: C কম্পাইলারে সাধারণত ফাংশন আর্গুমেন্ট ডান থেকে বামে ইভালুয়েট হয়। ফলে প্রথমে `i++` এর জন্য 4, তারপর `++i` এর জন্য 6 প্রিন্ট হয় এবং পরের স্টেটমেন্টে বর্তমান মান 6 প্রিন্ট হয়ে আউটপুট `6 4 6` দেয়।

31. **What will happen if this C program is compiled and executed?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 152 (ET: DU)]*
   ```c
   #include<stdio.h>
   int main() {
   return 0;
   }
   ```
   a) The program will show some garbage output
   b) There will be a compile error and the program will not execute
   c) No output (Output screen will be empty)
   d) There will be a run-time error
answer: C
explanation: প্রোগ্রামটিতে কোনো আউটপুট স্টেটমেন্ট (`printf`) না থাকায় এটি সফলভাবে সমাপ্ত হবে এবং আউটপুট স্ক্রিন সম্পূর্ণ খালি (empty) থাকবে।

32. **What will be the output of this C program?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 153 (ET: DU)]*
   ```c
   #include<stdio.h>
   int main() {
   float p=10.5;
   int a=5*p+5.0;
   printf("%d\n",a);
   return 0;
   }
   ```
   a) 57.500000
   b) 57
   c) 57.000000
   d) The program has errors and will not run.
answer: B
explanation: $5 \times 10.5 + 5.0 = 57.5$। `int a`-তে সংরক্ষণের কারণে দশমিক মান বাদ গিয়ে পূর্ণসংখ্যা 57 প্রিন্ট হবে।

33. **What will be the output of this C program?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 153 (ET: DU)]*
   ```c
   #include<stdio.h>
   int main() {
   int i=1;
   do{
   printf("%d-",i++);
   }while(i<=0);
   return 0;
   }
   ```
   a) 1-2-
   b) 1-
   c) No output (Output screen will be empty
   d) The program will cause an infinite loop and has to be stopped manually
answer: B
explanation: `do...while` লুপের বডি অন্তত একবার চলে। ফলে `i=1` থাকা অবস্থায় "1-" প্রিন্ট হয়ে `i` এর মান 2 হয় এবং শর্ত `2 <= 0` মিথ্যা হওয়ায় লুপ শেষ হয়।

34. **If any error occurs due to violation of programming rule is ________.** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 173 (ET: N/A)]*
   a) Syntax error
   b) Run-time Errors
   c) Linker Errors
   d) Logical Errors
answer: A
explanation: প্রোগ্রামিং ভাষার ব্যাকরণগত বা সিনট্যাক্স সংক্রান্ত নিয়ম ভঙ্গ করার কারণে যে এরর হয় তাকে সিনট্যাক্স এরর (Syntax error) বলে।

35. **Find output in C- Program:** *[BPSC Assistant Network Engineer 2019 compact it 198 (ET: N/A)]*
   ```c
   #include<stdio.h>
   int main() {
   printf("%c", 100);
   return 0;
   }
   ```
   A) 100
   B) one hundred
   C) d
   D) 0
answer: C
explanation: ASCII টেবিলে ডেসিমাল সংখ্যা 100 এর সমতুল্য ক্যারেক্টার হলো ছোট হাতের 'd' ('a'=97, 'b'=98, 'c'=99, 'd'=100)।

36. **What will be output if you compile & and execute following C code?** *[Bangladesh Bank Assistant Programmer 2011 compact it 272 (ET: N/A)]*
   ```c
   void main() {
   const int i=5;
   i++;
   printf("%d", i);
   }
   ```
   a. 5
   b. 6
   c. 0
   d. Compiler Error
answer: D
explanation: `const` হিসেবে ঘোষিত ভ্যারিয়েবল রিড-অনলি (read-only) হয়। একে পরিবর্তনের চেষ্টা (`i++`) করলে কম্পাইলার এরর (Compiler Error) দেয়।

## Control Statements & Loops (16)

1. **Which of the following statements about the "do while" loop is correct?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 6 (ET: BIBM)]*
   a) The condition is checked before the loop body is executed for the first time.
   b) The loop body is guaranteed to execute at least once.
   c) The loop condition must always be false for the loop to execute.
   d) The "do while" loop and "while" loop have identical behavior in all cases.
answer: B
explanation: `do...while` একটি exit-controlled loop, যার শর্তটি বডি এক্সিকিউশনের পর যাচাই করা হয়। ফলে শর্ত যাই হোক না কেন, লুপের বডি অন্তত একবার নিশ্চিতভাবে এক্সিকিউট হয়।

2. **Which for loop has range of similar indexes of 'i' used in for (i = 0; i < n; i++)?** *[Combined Bank Officer (IT) 04.10.2024 compact it 16 (ET: BIBM)]*
   (a) for (i= n; i>0; i--)
   (b) for (i=n-1; i>0; i--)
   (c) for (i = 0; i = 0; i--)
   (d) for (i=n-1; i>-1; i--)
answer: D
explanation: `for (i = 0; i < n; i++)` লুপে `i`-এর মান $0$ থেকে $n-1$ পর্যন্ত $n$ টি মানে চলে। বিপরীতক্রমে একই রেঞ্জ ($n-1$ থেকে $0$) পেতে `for (i=n-1; i>-1; i--)` ব্যবহৃত হয়।

3. **Consider int i=0; Then which of the following is not an infinite loop?** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*
   a) for(;;){}
   b) while ( ){}
   c) while ( ++i<0) { --i;}
   d) do {++i; while(--i<=0);
answer: C
explanation: `i=0` হলে `++i < 0` (অর্থাৎ $1 < 0$) শর্তটি প্রথমবারেই মিথ্যা (false) হয়ে যায়। ফলে লুপটি সাথে সাথে বন্ধ হয়ে যায় এবং এটি ইনফিনিট লুপ নয়।

4. **Which keyword is used to skip the rest of a loop and carry on from the top of the loop again?** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*
   a) Break
   b) resume
   c) continue
   d) skip
answer: C
explanation: লুপের বর্তমান ইটারেশনের বাকি অংশ বাদ দিয়ে (skip করে) পরবর্তী ইটারেশনে যাওয়ার জন্য `continue` কিওয়ার্ড ব্যবহৃত হয়।

5. **What can be used to terminate for(;;)?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*
   **Ans:** break statement
answer: A
explanation: `for(;;)` একটি ইনফিনিট লুপ। একে শর্তসাপেক্ষে বন্ধ বা টার্মিনেট করতে লুপের ভেতরে `break` স্টেটমেন্ট (অথবা `return`/`goto`) ব্যবহার করা হয়।

6. **The ________ loop is especially useful when you process a menu selection?** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 170 (ET: N/A)]*
   a) while
   b) do-while
   c) for
   d) switch
answer: B
explanation: মেনু চালিত প্রোগ্রামে (menu-driven programs) ব্যবহারকারীকে অপশন অন্তত একবার দেখাতে হয় এবং ইনপুট নিয়ে শর্ত পরীক্ষা করতে হয়, তাই `do-while` লুপ বিশেষভাবে উপযোগী।

7. **C programming Language এ কোনো loop থেকে তৎক্ষণাৎ বের করার জন্য উল্লেখিত কোনটি ব্যবহৃত হয়?** *[BPSC Assistant Network Engineer 2019 compact it 196 (ET: N/A)]*
   A) break
   B) switch
   C) continue
   D) if
answer: A
explanation: C ভাষায় চলমান লুপ বা সুইচ ব্লক থেকে সাথে সাথে বের হয়ে আসার জন্য `break` স্টেটমেন্ট ব্যবহৃত হয়।

8. **Which Control statement can be executed at least once?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 235 (ET: N/A)]*
   A) While
   B) For
   C) do-while
   D) None of the above
answer: C
explanation: `do-while` লুপের শর্তটি বডি এক্সিকিউশনের পর শেষে চেক করা হয়, তাই এর বডি কমপক্ষে একবার এক্সিকিউট হয়।

9. **Which of the following cannot be checked in a switch-case statement?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 238 (ET: N/A)]*
   A) Character
   B) Integer
   C) Float
   D) None of above
answer: C
explanation: C ভাষায় `switch-case`-এ শুধুমাত্র পূর্ণসংখ্যা বা সমতুল্য টাইপ (`int`, `char`, `enum`) ব্যবহার করা যায়; ফ্লোটিং পয়েন্ট টাইপ (`float` বা `double`) ব্যবহার করা যায় না।

10. **Which control statement can be executed at least once?** *[Combined Bank Maintenance Engineer 2018 compact it 226 (ET: N/A)]*
   A) While
   B) for
   C) do-while
   D) All of the above
answer: C
explanation: `do-while` লুপে শর্ত যাচাই করার আগেই স্টেটমেন্ট ব্লক একবার রান করে, ফলে এটি অন্তত একবার কার্যকর হয়।

11. **Which of the following correctly shows the hierarchy of algorithm operation in C?** *[Combined Bank Maintenance Engineer 2018 compact it 227 (ET: N/A)]*
   A) /*+-
   B) *-/+
   C) +-/*
   D) /*+-
   25. Consider the following code
   ```c
   #include<stdio.h>
   int main (int argc, char *argv[]){
   return 0;}
   ```
   What is the maximum length of character array argv in the above code? *[Combined Bank Maintenance Engineer 2018 compact it 227 (ET: N/A)]*
   A) 0
   B) 1
   C) Undefined
   D) -1
   26. Which is the value of “d” after this line of code has been executed?
   double d = Math.round(2.5+math.random()); *[Combined Bank Maintenance Engineer 2018 compact it 227 (ET: N/A)]*
   A) 2
   B) 2.5
   C) 3
   D) 4
answer: B
explanation: C ভাষায় অ্যারিথমেটিক অপারেটরের অগ্রাধিকার (precedence) ক্রমানুসারে গুণ (`*`) ও ভাগ (`/`) এর অগ্রাধিকার যোগ (`+`) ও বিয়োগ (`-`) এর চেয়ে বেশি।

12. **What is an example of iteration in C?** *[Combined 3 Bank Assistant Programmer 2018 compact it 231 (ET: N/A)]*
   A) for
   B) while
   C) do-while
   D) all of the above
answer: D
explanation: C প্রোগ্রামিংয়ে `for`, `while`, এবং `do-while` তিনটিই ইটারেশন বা লুপ স্টেটমেন্ট।

13. **Which of the following format is a correct format for declaration of function?** *[Combined 3 Bank Assistant Programmer 2018 compact it 232 (ET: N/A)]*
   A) return-type function-name (argument type);
   B) return-type function-name (argument type) {}
   C) return-type (argument type) function-name;
   D) return-type {} function-name
answer: A
explanation: ফাংশন ডিক্লেয়ারেশন বা প্রোটোটাইপের সঠিক সিনট্যাক্স হলো `return-type function-name (argument-types);`।

14. **What are the final values of a and c in the following C statement? (initialize value a=2, c=1) c=c? c=2:a=0;** *[Combined 3 Bank Assistant Programmer 2018 compact it 233 (ET: N/A)]*
   A) a=0, c=0
   B) a=2, c=2
   C) a=2, c=2
   D) a=1, c=2
answer: B
explanation: যেহেতু শুরুতে `c=1` (true), তাই টার্নারি অপারেটরের প্রথম অংশ `c=2` কার্যকর হয়ে `c`-এর মান 2 হয় এবং `a` এর মান অপরিবর্তিত থেকে 2 থাকে।

15. **Which of the following doesn’t require an ‘&’ for the input in scanf ( ) ?** *[Combined 3 Bank Assistant Programmer 2018 compact it 233 (ET: N/A)]*
   A) char name [10];
   B) int name [10];
   C) float name[10];
   D) double name [10];
answer: A
explanation: স্ট্রিং বা ক্যারেক্টার অ্যারে (`char name[10]`) এর নাম নিজেই তার প্রথম উপাদানের মেমোরি অ্যাড্রেস (বেস অ্যাড্রেস) নির্দেশ করে, তাই `scanf("%s", name)`-এ `&` চিহ্নের প্রয়োজন হয় না।

16. **Which are the keywords of structured programming?** *[Bangladesh Bank Assistant Programmer 2016 compact it 245 (ET: N/A)]*
   A) Keywords
   B) Constant
   C) volatile
   D) Above all
answer: D
explanation: স্ট্রাকচার্ড প্রোগ্রামিং ভাষায় নির্দিষ্ট কীওয়ার্ড, ধ্রুবক (constant) এবং টাইপ কোয়ালিফায়ার (যেমন: volatile) সবগুলোই ভাষার মৌলিক উপাদান।

## Arrays & Functions (15)

1. **The number of values a function can return at a time?** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*
   a) 1
   b) 2
   c) 0
   d) more than 2
answer: A
explanation: C ভাষায় একটি ফাংশন `return` স্টেটমেন্টের মাধ্যমে একবারে কেবল একটিমাত্র (1টি) মান রিটার্ন করতে পারে।

2. **Which of the following correctly accesses the seventh element stored in arr, an array with 100 elements?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 27 (ET: BIBM)]*
   a) arr[6]
   b) arr[7]
   c) arr{6}
   d) arr{7}
answer: A
explanation: C ভাষায় অ্যারে 0-ইনডেক্সড (zero-indexed)। ফলে ৭ম উপাদানটি অ্যাক্সেস করতে `arr[6]` ব্যবহার করতে হয়।

3. **Which of the following do not return any value?** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 53 (ET: N/A)]*
   (ক) Constructor function
   (খ) Friend function
   (গ) In line Function
   (ঘ) Member Functions
answer: A
explanation: কনস্ট্রাক্টর ফাংশনের কোনো রিটার্ন টাইপ থাকে না (এমনকি `void`-ও নয়) এবং এটি কোনো মান রিটার্ন করে না।

4. **Assuming an int is of 4 bytes, What is the size of “int array[15]”?** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 55 (ET: N/A)]*
   (ক) 15
   (খ) 19
   (গ) 11
   (ঘ) 60
answer: D
explanation: প্রতিটি `int` 4 বাইট হলে 15টি উপাদানের জন্য মোট সাইজ হবে $15 \times 4 = 60$ বাইট।

5. **In C++, The library function exit() causes an exit from-** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 57 (ET: N/A)]*
   (ক) a block of statements
   (খ) a loop in which it occurs
   (গ) a function in which it occurs
   (ঘ) a program in which it occurs
answer: D
explanation: `exit()` স্ট্যান্ডার্ড লাইব্রেরি ফাংশনটি কল করলে সম্পূর্ণ প্রোগ্রামটির এক্সিকিউশন তৎক্ষণাৎ বন্ধ (terminate) হয়ে যায়।

6. **Which of the following is correct to initialize arrays in C?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 83 (ET: N/A)]*
   a. int array = (1, 2, 3, 4, 5)
   b. int array = {1, 2, 3, 4, 5}
   c. int array() = (1, 2, 3, 4, 5)
   d. int array[5] = {1, 2, 3, 4, 5}
answer: D
explanation: C ভাষায় অ্যারে ডিক্লেয়ার ও ইনিশিয়ালাইজ করার সঠিক সিনট্যাক্স হলো `int array[5] = {1, 2, 3, 4, 5};`।

7. **What is the access methodology in array?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 83 (ET: N/A)]*
   a. Sequential
   b. Random
   c. Rational
   d. Stochastic
answer: B
explanation: অ্যারের যেকোনো উপাদান ইনডেক্সের মাধ্যমে সরাসরি সমসময়ে ($O(1)$) অ্যাক্সেস করা যায়, তাই এটি র‍্যান্ডম অ্যাক্সেস (Random access) পদ্ধতি।

8. **Which of the following is correct?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 84 (ET: N/A)]*
   a. “X extends Y” is correct if and only if X is a class and Y is an interface
   b. “X extends Y” is correct if and only if X is an interface and Y is a class
   c. “X extends Y” is correct if X and Y are either both classes or both interfaces
   d. “X extends Y” is correct for all combinations of X and Y being classes and/or interfaces
answer: C
explanation: অবজেক্ট-ওরিয়েন্টেড প্রোগ্রামিংয়ে (যেমন জাভায়) `extends` কিওয়ার্ড তখনই সঠিক যখন `X` ও `Y` উভয়ই ক্লাস অথবা উভয়ই ইন্টারফেস।

9. **An n*n array v is defined as follows: v[i, j]=i-j for all i, j; 1<=i<=n, 1<=j<=n, the sum of the element of array v is** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 207 (ET: AUST)]*
   A) 0
   B) n-1
   C) n^2-3n+2
   D) n^2(n+1)/2
answer: A
explanation: যেহেতু $v[i, j] = i - j$ এবং $v[j, i] = j - i = -(i - j)$, তাই প্রতিটি উপাদানের বিপরীত উপাদান ম্যাট্রিক্সে বিদ্যমান ($v[i, i]=0$ সহ)। ফলে সকল উপাদানের যোগফল 0।

10. **When you pass array as an argument to a function, which actually gets passed?** *[BPSC Assistant Maintenance Engineer 2019 compact it 191 (ET: N/A)]*
   (a) Base address of the array
   (b) The first element of the array
   (c) Address of the first element of the array
   (d) Address of the last element of the array
answer: A
explanation: C ভাষায় ফাংশনে অ্যারে পাস করলে প্রকৃতপক্ষে অ্যারেটির বেস অ্যাড্রেস (Base address) বা প্রথম উপাদানের মেমরি অ্যাড্রেস পাস হয় (pass by pointer/decay)।

11. **int number [] = {10,20,30,40,50}; number[3] =?** *[Sonali & Janata Bank Assistant Programmer 2018 compact it 240 (ET: N/A)]*
   A) 10
   B) 20
   C) 30
   D) 40
answer: D
explanation: 0-ইনডেক্সিং অনুযায়ী `number[0]=10, number[1]=20, number[2]=30, number[3]=40`। ফলে মান হবে 40।

12. **Two dimensional arrays are also called?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 234 (ET: N/A)]*
   A) table array
   B) matrix array
   C) both A and B
   D) none of the above
answer: C
explanation: দ্বিমাত্রিক (2D) অ্যারেকে রো ও কলামের বিন্যাস থাকায় টেবিল অ্যারে বা ম্যাট্রিক্স অ্যারে উভয়ই বলা হয়।

13. **The smallest element of array index is called it-** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 235 (ET: N/A)]*
   A) Lower Bound
   B) Upper Bound
   C) Range
   D) Extraction
answer: A
explanation: অ্যারের সর্বনিম্ন ইনডেক্সকে লোয়ার বাউন্ড (Lower Bound) এবং সর্বোচ্চ ইনডেক্সকে আপার বাউন্ড (Upper Bound) বলা হয়।

14. **What type of reference should be used in vector arithmetic in C++?** *[Combined Bank Senior Officer (IT) 2018 compact it 220 (ET: DU)]*
   A) Dynamic
   B) const
   C) a and b
   D) none of the mentioned
answer: B
explanation: C++ এ ভেক্টর বা অবজেক্ট অপারেশনে অপ্রয়োজনীয় অবজেক্ট কপি এড়াতে এবং ডেটা সুরক্ষিত রাখতে `const` রেফারেন্স (`const &`) ব্যবহার করা সর্বোত্তম রীতি।

15. **In C, if you pass an array as an argument to a function, what actually gets passed?** *[Bangladesh Bank Assistant Programmer 2011 compact it 271 (ET: N/A)]*
   a. Value of elements in array
   b. First element of the array
   c. Base address of the array
   d. Address of the last element of the array
answer: C
explanation: ফাংশনে অ্যারে পাস করলে অ্যারের প্রথম উপাদানের মেমোরি অ্যাড্রেস বা বেস অ্যাড্রেস (Base address) পাস হয়।

## Data Types & Variables (14)

1. **What is the minimum value that can be stored accurately in a 32-bit signed integer of C programming language?** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 179 (ET: N/A)]*
   a) 0
   b) -2^{31}
   c) -2^{31}-1
   d) -2^{32}
answer: B
explanation: ৩২-বিট সাইন্ড ইন্টিজারে (2's complement) মানের সীমা $-2^{31}$ থেকে $2^{31}-1$ পর্যন্ত। ফলে সর্বনিম্ন মান $-2^{31}$।

2. **What is the maximum value that can be stored in a 32-bit signed integer of C language?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 155 (ET: DU)]*
   a) 10^{32}
   b) 2^{32}
   c) 2^{32}-1
   d) 2^{31}-1
answer: D
explanation: ৩২-বিট সাইন্ড ইন্টিজারের ক্ষেত্রে সর্বোচ্চ ধনাত্মক মান হলো $2^{31}-1$ (২,১৪৭,৪৮৩,৬৪৭)।

3. **C programming এ নিচের কোনটি Invalid variable name?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 187 (ET: N/A)], [BPSC Assistant Network Engineer 2019 compact it 197 (ET: N/A)]*
   A) Average
   B) No#of-students
   C) Xyz
   D) y23z
answer: B
explanation: C ভাষায় ভ্যারিয়েবলের নামে `#` বা `-` (হাইফেন) এর মতো বিশেষ ক্যারেক্টার ব্যবহার করা যায় না। ফলে `No#of-students` একটি অবৈধ (invalid) নাম।

4. **C কী ধরনের programming language?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 187 (ET: N/A)]*
   A) Low level language
   B) Mid-level language
   C) High level language
   D) None of these
answer: B
explanation: C ভাষাকে প্রায়ই মিড-লেভেল ল্যাঙ্গুয়েজ (Mid-level language) বলা হয়, কারণ এতে হাই-লেভেল ভাষার বৈশিষ্ট্যের পাশাপাশি মেমরি অ্যাড্রেস সরাসরি নিয়ন্ত্রণ করার মতো লো-লেভেল ক্ষমতাও বিদ্যমান।

5. **নিচের কোনটি C ভাষার Keyword নয়?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)]*
   A) struct
   B) int
   C) star
   D) float
answer: C
explanation: `struct`, `int`, এবং `float` C ভাষার সংরক্ষিত কীওয়ার্ড (keyword), কিন্তু `star` কোনো কীওয়ার্ড নয়।

6. **C programming language এ নিচের কোনটিকে "if" দিয়ে Replace করা যায়?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)], [BPSC Assistant Network Engineer 2019 compact it 198 (ET: N/A)]*
   A) switch
   B) structure
   C) return
   D) for
answer: A
explanation: সিলেকশন বা ডিসিশন মেকিং স্টেটমেন্ট `switch`-কে সমতুল্য `if-else` কাঠামো দ্বারা প্রতিস্থাপন (replace) করা যায়।

7. **Suppose a C program has floating constant 1.414, what's the best way to convert it as a float data type?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 203 (ET: AUST)]*
   A) (float)1.414
   B) float (1.414)
   C) 1.414f or 1.414F
   D) None of these
   3. Consider the following variable declarations and definitions in C:
   (i) int var_9=1
   (ii) int 9_var=2
   (iii) int _=3
   Choose the correct statement w.r.t above variables. *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 203 (ET: AUST)]*
   A) Both (i) and (ii) are valid
   B) Only (i) is valid
   C) Both (i) and (iii) are valid
   D) All of these
answer: C
explanation: C ভাষায় ডিফল্টভাবে দশমিক ভগ্নাংশকে `double` ধরা হয়; একে `float` লিটারেল হিসেবে প্রকাশ করার আদর্শ উপায় হলো শেষে `f` বা `F` যুক্ত করা (যেমন: `1.414f`)।

8. **Variable which use same name in whole program and in its all routines thus best classified as-** *[Probashi Kallyan Bank Programmer: 2019 compact it 213 (ET: AUST)]*
   A) middle variable
   B) default variable
   C) local variable
   D) global variable
answer: D
explanation: যে ভ্যারিয়েবল সম্পূর্ণ প্রোগ্রাম এবং এর সকল ফাংশন বা রুটিনে একই নামে কার্যকর থাকে তাকে গ্লোবাল ভ্যারিয়েবল (global variable) বলে।

9. **Which format specifier is used for typing double data?** *[BREB Assistant Junior Engineer (IT) 2019 compact it 218 (ET: N/A)]*
   A) %f
   B) %lf
   C) %d
   D) %s
answer: B
explanation: C ভাষায় `double` ডেটা টাইপ পড়ার (ইনপুট নেওয়ার) জন্য ফরম্যাট স্পেসিফায়ার হিসেবে `%lf` (long float) ব্যবহৃত হয়।

10. **Which one of the following is not a valid identifier?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 235 (ET: N/A)]*
   A) _compact
   B) compact
   C) com-pact
   D) com_pact
   17. Consider the following code
   ```c
   #include<stdio.h>
   int main (int argc, char *argv[]){
   return 0;
   }
   ```
   What is the maximum length of character array argv in the above code? *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 236 (ET: N/A)]*
   A) 0
   B) 1
   C) Undefined
   D) -1
   18. Which is the value of “d” after this line of code has been executed?
   double d=Math.round(2.5+Math.random()); *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 236 (ET: N/A)]*
   A) 2
   B) 2.5
   C) 3
   D) 4
answer: C
explanation: ভ্যারিয়েবল বা আইডেন্টিফায়ারে হাইফেন (`-`) ব্যবহার করা যায় না (এটি বিয়োগ অপারেটর হিসেবে গণ্য হয়)। তাই `com-pact` একটি অবৈধ আইডেন্টিফায়ার।

11. **Which of the following correctly shows the hierarchy of algorithm operation in C?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 236 (ET: N/A)]*
   A) /*+-
   B) *-/+
   C) +-/*
   D) /*+-
answer: B
explanation: অ্যারিথমেটিক অপারেশনে গুণ (`*`) ও ভাগ (`/`)-এর প্রাধান্য যোগ (`+`) ও বিয়োগ (`-`)-এর চেয়ে বেশি।

12. **The value 9.87 to 10 when use?** *[Bangladesh Bank Assistant Programmer 2016 compact it 246 (ET: N/A)]*
   A) floor ()
   B) ceil ()
   C) both A & B
   D) None
answer: B
explanation: `ceil()` ফাংশন কোনো ফ্লোটিং সংখ্যার পরবর্তী নিকটতম বৃহত্তর পূর্ণসংখ্যা রিটার্ন করে, ফলে `ceil(9.87)` এর মান হয় 10।

13. **Hungarian notation is used to ________.** *[BREB Assistant General Manager (IT) 2016 compact it 254 (ET: N/A)]*
   A) Design system manual
   B) Design user manual
   C) Define name of the variable
   D) All
answer: C
explanation: হাঙ্গেরিয়ান নোটেশন (Hungarian notation) হলো ভ্যারিয়েবল নামকরণের একটি বিশেষ পদ্ধতি (naming convention), যেখানে ভ্যারিয়েবলের নামের শুরুতে তার ডেটা টাইপ বা উদ্দেশ্য নির্দেশক প্রিফিক্স যুক্ত করা হয় (যেমন: `iCount`, `strName`)।

14. **Which of the following is not derived data type in C?** *[Bangladesh Bank Assistant Programmer 2011 compact it 272 (ET: N/A)]*
   a. Function
   b. Pointer
   c. Enumeration
   d. Array
answer: C
explanation: C ভাষায় অ্যারে, পয়েন্টার এবং ফাংশন হলো ড্রাইভড (derived) ডেটা টাইপ; আর `enum` (ইনিউমারেশন), `struct`, `union` হলো ইউজার-ডিফাইন্ড (user-defined) ডেটা টাইপ।

## Operators & Expressions (11)

1. **Let x be an integer which can take a value of 0 or 1. The statement if (x==0) x=1; else x=0; is equivalent to which of the following?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 203 (ET: AUST)]*
   A) x=1+x
   B) x=1-x
   C) x=x-1
   D) x=1%x
answer: B
explanation: যদি $x = 0$ হয়, তবে $1 - 0 = 1$; আর $x = 1$ হলে $1 - 1 = 0$। ফলে `x = 1 - x` স্টেটমেন্টটি $0$ ও $1$-এর মধ্যে টগল করার জন্য `if-else` এর সমতুল্য।

2. **For a given integer, which of the following operators can be used to set and reset a particular bit respectively?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 203 (ET: AUST)]*
   A) | and &
   B) && and ||
   C) & and |
   D) || and &&
answer: A
explanation: কোনো বিটকে সেট (1) করতে বিটওয়াইজ OR (`|`) এবং রিসেট (0) করতে বিটওয়াইজ AND (`&`) অপারেটর ব্যবহৃত হয়।

3. **Which of the declaration is correct?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 206 (ET: AUST)], [Probashi Kallyan Bank Assistant Programmer 2018 compact it 237 (ET: N/A)]*
   A) int length;
   B) char int
   C) int long;
   D) float double;
answer: A
explanation: `int length;` একটি সঠিক ভ্যারিয়েবল ডিক্লেয়ারেশন। অন্যগুলোতে রিজার্ভড কীওয়ার্ডকে নাম হিসেবে ব্যবহার করা হয়েছে যা অবৈধ।

4. **What is the precedence of arithmetic operators (from highest to lowest)?** *[Probashi Kallyan Bank Programmer: 2019 compact it 210 (ET: AUST)]*
   A) %, +, /, *, -
   B) +, -, %, *, /
   C) %, +, -, *, /
   D) %, *, /, +, -
answer: D
explanation: অ্যারিথমেটিক অপারেটরের অগ্রাধিকার (precedence) ক্রমানুসারে মডুলাস (`%`), গুণ (`*`), এবং ভাগ (`/`) সবার উপরে থাকে; এরপর যোগ (`+`) এবং বিয়োগ (`-`) কাজ করে।

5. **Which is logical operator?** *[BREB Assistant General Manager (IT) 2016 compact it 253 (ET: N/A)]*
   A) +
   B) >=
   C) AND
   D) <<
answer: C
explanation: `AND` (C ভাষায় `&&`) হলো একটি লজিক্যাল অপারেটর (Logical operator)।

6. **Which of the following will not increase the value of variable c by 1?** *[BREB Assistant General Manager (IT) 2016 compact it 253 (ET: N/A)]*
   A) c++
   B) c = c + 1
   C) c + 1 >= c
   D) c += 1
answer: C
explanation: `c + 1 >= c` একটি তুলনামূলক বা রিলেশনাল এক্সপ্রেশন যা কোনো অ্যাসাইনমেন্ট করে না। বাকি সবগুলো `c`-এর মান 1 বৃদ্ধি করে।

7. **The escape sequence “\b” in C programming is -----** *[BREB Assistant General Manager (IT) 2016 compact it 254 (ET: N/A)]*
   A) Backspace
   B) Next Line
   C) Tab
   D) None of these
answer: A
explanation: C ভাষায় এস্কেপ সিকোয়েন্স `\b` কার্সারকে এক ঘর পেছনে নেওয়ার জন্য বা ব্যাকস্পেস (Backspace) হিসেবে ব্যবহৃত হয়।

8. **What is not the kind of data type?** *[BREB Assistant General Manager (IT) 2016 compact it 254 (ET: N/A)]*
   A) Logical
   B) Text
   C) Number
   D) Currency
answer: D
explanation: সাধারণ প্রোগ্রামিং ভাষা এবং C-তে কারেন্সি (Currency) কোনো স্ট্যান্ডার্ড প্রিমিটিভ ডেটা টাইপ নয়।

9. **Which keyword is used in C language?** *[BREB Assistant General Manager (IT) 2016 compact it 255 (ET: N/A)]*
   A) ing
   B) for
   C) select
   D) href
answer: B
explanation: `for` হলো C প্রোগ্রামিং ভাষার ৩২টি সংরক্ষিত কীওয়ার্ডের অন্যতম, যা লুপ চালনার জন্য ব্যবহৃত হয়।

10. **Find out the error in following block of code: if (x=100) cout<<"x is 100";** *[Bangladesh Bank Assistant Programmer 2011 compact it 271 (ET: N/A)]*
   a. 100 should be enclosed in quotations
   b. There is no semicolon at the end of first line
   c. Equals to operator mistake
   d. Variable x should not be inside quotation
answer: C
explanation: শর্ত পরীক্ষা করার জন্য সমতা বা ইকুয়ালিটি অপারেটর `==` ব্যবহারের জায়গায় অ্যাসাইনমেন্ট অপারেটর `=` ব্যবহার করা হয়েছে, যা লজিক্যাল ভুল (Equals to operator mistake)।

11. **Which of the following is not a logical operator?** *[Bangladesh Bank Assistant Programmer 2011 compact it 271 (ET: N/A)]*
   a. &
   b. &&
   c. ||
   d. |
answer: A
explanation: `&&` এবং `||` হলো লজিক্যাল অপারেটর (logical operators), আর `&` এবং `|` হলো বিটওয়াইজ অপারেটর (bitwise operators)।

## Programming Concepts (8)
1. **Which of the following is used to restrict access to certain details of an object in OOP? [ OOP-এ কোনটি object-এর কিছু বিস্তারিত তথ্য অ্যাক্সেস সীমিত করতে ব্যবহৃত হয়?]** *[Combined Bank Senior Officer (IT) Date: 17.10.2025 [bitbox it book 218]]*
   (a) Polymorphism
   (b) Inheritance
   (c) Abstraction
   (d) Encapsulation
answer: D
explanation: এনক্যাপসুলেশন (Encapsulation) অবজেক্টের অভ্যন্তরীণ ডেটা ও মেথডকে একসাথে আবদ্ধ করে এবং অ্যাক্সেস রেস্ট্রিক্ট বা সীমিত করার মাধ্যমে ডেটা হাইডিং নিশ্চিত করে।

2. **(a) Write a JavaScript function to validate an email.** *[Dhaka Power Distribution Company Limited Assistant Engineer (ICT) Exam Date: 17.10.2025 Time: 1 Hour, Total Marks: 100 (MCQ: 20, Written: 8×10 = 80) [bitbox it book 236]]*
answer: A
explanation: ইমেইল ভ্যালিডেশনের জন্য জাভাস্ক্রিপ্ট রেগুলার এক্সপ্রেশন ফাংশন: `function validateEmail(email) { return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email); }`।

3. **In a doubly linked list, the number of pointers affected in insertion operation will be— [ ডাবলি লিঙ্কড লিস্টে ইনসারশন অপারেশনে কতটি পয়েন্টার প্রভাবিত হয়? ]** *[Bankers' Selection Committee Secretariat Post: Assistant Programmer; Date: 15 Feb, 2024 Exam Taker: ANZA; Post: 35 [bitbox it book 347]]*
   (A) 5
   (B) 0
   (C) 1
   (D) None of these
answer: D
explanation: ডাবলি লিঙ্কড লিস্টের মাঝে কোনো নতুন নোড ইনসার্ট করতে সাধারণত ৪টি পয়েন্টার পরিবর্তন করতে হয় (`next` ও `prev` পয়েন্টারসমূহ)। ৪ অপশনে না থাকায় উত্তর (D) None of these।

4. **What is the class and subnet mask if the subnet mask is 255.224.0.0? [ সাবনেট মাস্ক 255.224.0.0 হলে এর ক্লাস এবং মাস্ক বিট কত? ]** *[Bankers' Selection Committee Secretariat Post: Assistant Programmer; Date: 15 Feb, 2024 Exam Taker: ANZA; Post: 35 [bitbox it book 348]]*
   (A) Class A, 8
   (B) Class A, 3
   (C) Class B, 3
   (D) Class B, 32
answer: B
explanation: প্রথম অকটেট 255 নির্দেশ করে ক্লাস A নেটওয়ার্ক। দ্বিতীয় অকটেটে 224 ($11100000_2$) থাকায় সাবনেট বিটের সংখ্যা ৩টি। সুতরাং এটি Class A, 3 সাবনেট বিট।

5. **Martin Cooper is known for his invention of— [ Martin Cooper কোন উদ্ভাবনের জন্য পরিচিত? ]** *[Bankers' Selection Committee Secretariat Post: Senior Office (IT); Date: 04 October, 2024 Exam Taker: ANZA; Post: 222 [bitbox it book 499]]*
   (a) Digital Camera
   (b) X-ray
   (c) Mobile Phone
   (d) Telephone
answer: C
explanation: মার্টিন কুপার (Martin Cooper) ১৯৭৩ সালে মটোরোলা কোম্পানিতে প্রথম হ্যান্ডহেল্ড মোবাইল ফোন (Mobile Phone) আবিষ্কার করেন।

6. **What is the main goal of reinforcement learning?[ রিইনফোর্সমেন্ট লার্নিং (Reinforcement learning) এর প্রধান লক্ষ্য কী? ]** *[Bankers' Selection Committee Secretariat Post: Senior Office (IT); Date: 04 October, 2024 Exam Taker: ANZA; Post: 222 [bitbox it book 502]]*
   (a) To classify data into categories
   (b) To optimize a system for maximum efficiency
   (c) To make predinction based on historical data
   (d) To learn optima actions through trail and error
answer: D
explanation: রিইনফোর্সমেন্ট লার্নিং (Reinforcement Learning)-এর মূল লক্ষ্য হলো পরিবেশের সাথে মিথস্ক্রিয়া এবং ট্রায়াল অ্যান্ড এরর (trial and error) ও রিওয়ার্ড-পেনাল্টির মাধ্যমে সর্বোত্তম কর্মপদ্ধতি (optimal actions) শেখা।

7. **Which for loop has range of similar indexes of ‘i’ used in for(i=0; i<n; i++)?[ for(i=0; i<n; i++) লুপের সমান ইনডেক্স রেঞ্জ নিচের কোন লুপটিতে ব্যবহৃত হয়েছে? ]** *[Bankers' Selection Committee Secretariat Post: Senior Office (IT); Date: 04 October, 2024 Exam Taker: ANZA; Post: 222 [bitbox it book 508]]*
   (a) for (i=n; i>0; i--)
   (b) for (i=n-1; i>0; i--)
   (c) for (i=0; i=0; i--)
   (d) for (i=n-1; i>=0; i--)
answer: D
explanation: `for(i=0; i<n; i++)` লুপে $0$ থেকে $n-1$ পর্যন্ত ইনডেক্স পাওয়া যায়। একইভাবে বিপরীত দিক থেকে পেতে `for (i=n-1; i>=0; i--)` ব্যবহৃত হয়।

8. **A collection of objects that use common structure and a common behavior is known as—[ একই কাঠামো এবং একই আচরণ ব্যবহার করে এমন অবজেক্টের সংগ্রহকে কী বলা হয়? ]** *[Bankers' Selection Committee Secretariat Post: Senior Office (IT); Date: 04 October, 2024 Exam Taker: ANZA; Post: 222 [bitbox it book 509]]*
   (a) Object
   (b) Entity
   (c) Instance
   (d) Class
answer: D
explanation: একই ধরনের বৈশিষ্ট্য (গঠন) এবং আচরণসম্পন্ন অবজেক্টের ব্লুপ্রিন্ট বা সংগ্রহকে ক্লাস (Class) বলা হয়।

## Pointers & Memory Allocation (5)

1. **Address stored in the pointer variable is of type ______** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*
   a) Integer
   b) Float
   c) Character
   d) Double
answer: A
explanation: মেমোরি অ্যাড্রেস হলো মূলত ধনাত্মক পূর্ণসংখ্যা (unsigned integer), যা পয়েন্টার ভ্যারিয়েবলে সংরক্ষিত হয়।

2. **Address variable রাখা যায় কোনটিতে?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)]*
   A) Break
   B) Int
   C) Pointer
   D) Float
answer: C
explanation: মেমোরি অ্যাড্রেস ধারণ করার জন্য ব্যবহৃত বিশেষ ভ্যারিয়েবলকে পয়েন্টার (Pointer) বলে।

3. **C-programming এ address রাখার জন্য কোনটি সাধারণত ব্যবহৃত হয়?** *[BPSC Assistant Network Engineer 2019 compact it 196 (ET: N/A)]*
   A) break
   B) pointer
   C) char
   D) float
answer: B
explanation: C প্রোগ্রামিংয়ে অন্য কোনো ভ্যারিয়েবলের মেমোরি অ্যাড্রেস সংরক্ষণ করার জন্য পয়েন্টার (pointer) ব্যবহৃত হয়।

4. **What is the following declaration for? int (*a)[10];** *[BPSC Assistant Maintenance Engineer 2019 compact it 192 (ET: N/A)]*
   (a) Pointer to an array of 10 integers
   (b) Array of 10 function Pointers returning integer
   (c) A pointer of to function returning an array to 10 integers
   (d) Array of 10 integers pointers
answer: A
explanation: বন্ধনী থাকার কারণে `(*a)` নির্দেশ করে `a` হলো একটি পয়েন্টার, যা ১০টি পূর্ণসংখ্যার সমন্বয়ে গঠিত একটি অ্যারেকে পয়েন্ট করে (Pointer to an array of 10 integers)।

5. **Which header file should be included to use functions like malloc() and calloc()?** *[Bangladesh Bank Assistant Programmer 2011 compact it 271 (ET: N/A)]*
   a. memory.h
   b. stdlib.h
   c. string.h
   d. dos.h
answer: B
explanation: C ভাষায় ডাইনামিক মেমোরি অ্যালোকোশন ফাংশন `malloc()`, `calloc()`, `free()` ইত্যাদি `<stdlib.h>` (Standard Library) হেডার ফাইলে সংজ্ঞায়িত থাকে।

## Recursion (4)

1. **When a function is called more than one time that is called?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*
   **Ans:** This is known as function reusability or recursion or Idempotence

2. **How many function calls will be performed to execute the following recursive function?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 156 (ET: DU)]*
   ```c
   void function(int N) {
   if (N==0)
   return;
   function(N+1);
   }
   ```
   a) N
   b) 2*N
   c) Infinite
   d) The answer can vary depending on the initial value of N

3. **Consider the following recursive function fun (x,y) . What is the value of fun (4,3) ?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 204 (ET: AUST)]*
   ```c
   int fun (int x, int y) {
   if(x==0)
   return y;
   return fun (x-1, x+y)
   }
   ```
   A) 9
   B) 10
   C) 12
   D) 13

4. **An algorithm that calls itself directly or indirectly is known as?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 234 (ET: N/A)], [Sonali Bank Limited Assistant Programmer 2016 compact it 252 (ET: N/A)]*
   A) Sub Algorithm
   B) Recursion
   C) Polish Notation
   D) Traversal algorithm

## Storage Classes & Scope (3)

1. **Which of the following is not a storage class specifier in C?** *[Combined Bank Assistant Programmer 09.02.2024 compact it 21 (ET: BIBM)]*
   (A) auto
   (B) register
   (C) static
   (D) extern
   (E) volatile

2. **In C, static storage class cannot be used with:** *[Combined Bank Assistant Programmer 09.02.2024 compact it 21 (ET: BIBM)]*
   (A) Global variabl
   (B) Function parameter
   (C) Function name
   (D) Local variable

3. **Which of the following storage classes have global visibility in C/C++?** *[Combined Bank Assistant Programmer 09.02.2024 compact it 21 (ET: BIBM)]*
   (A) Auto
   (B) Extern
   (C) Static
   (D) Register

## Flowcharts & Algorithms (1)

1. **In flowchart what does below represent?** *[Bangladesh Bank Data Entry Operator (IT) 2020 compact it 189 (ET: N/A)]*
   ```
   +-------+
   |       |
   (       )
   |       |
   +-------+
   ```
   a. Document
   b. Database
   c. Terminal
   d. Process
