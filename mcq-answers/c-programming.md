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

   answer: a — 15  
   explanation: fun receives the address of x, so *p = *p + 10 changes x to 15 and returns 15.

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

   answer: b — 3 2  
   explanation: x is 3 so the if branch runs and keeps y = 2; the program prints "3 2".

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

   answer: c — 0  
   explanation: > is left-associative, so x>y>z becomes (20>10)>5 = 1>5 = 0.

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

   answer: d — muli is printed thrice  
   explanation: k takes the values 0.0, 1.0 and 2.0 before 3.0 fails the test, so the loop body runs three times.

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

   answer: c — 10  
   explanation: The inner loop runs i times for each i, giving 0+1+2+3+4 = 10.

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

   answer: b — k, 81  
   explanation: %c prints int 107 as the character 'k', and %d prints char 'Q' as its ASCII code 81.

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

   answer: b — 5  
   explanation: The flat index is i*3*2 + j*2 + k = 0 + 4 + 1 = 5, and the initialiser puts 5 at that position.

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

   answer: a — 11  
   explanation: 11 is 1011 and 3 is 0011, so bitwise OR gives 1011 = 11.

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

   answer: b — 57  
   explanation: 5*10.5 + 5.0 = 57.5, and assigning to int truncates the fraction to 57.

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

   answer: A — 4 3 2 1  
   explanation: i is static so it keeps its value across the recursive main() calls, printing 4, 3, 2, 1 before --i makes it 0 and the if fails.

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

   answer: A — 0  
   explanation: y is 0, so the comparison y != 0 is false and x gets the value 0.

12. **How many times will loop iterate?** *[NPCBL Executive Trainee (Software) 2023 compact it 38 (ET: N/A)]*  
   (a) 9  
   (b) 10  
   (c) 8  
   (d) infinite

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

   answer: b — 100  
   explanation: x increases by 2 from 0 and the loop stops as soon as x reaches 100, which fails x<100.

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

   answer: c — garbage values  
   explanation: i, j and k are used in their own initialisers before they hold any value, so the variables are uninitialised and print garbage.

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

   answer: b — Compiler Error  
   explanation: C does not allow a member to be initialised inside a struct declaration, so int x=3 and char name[]="hello" are rejected.

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

   answer: a — 12 4  
   explanation: sizeof is a compile-time operator and does not evaluate its operand, so i++ never runs; i stays 12 and j is 4.

17. **Which is the correct output?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 129 (ET: N/A)]*
   ```c
   int i = 4; printf("%d %d", +1,i++); printf("%d", i++);
   ```
   a) 4 5 6  
   b) 5 7 8  
   c) 6 4 6  
   d) 1 4 5

   answer: d — 1 4 5  
   explanation: +1 is unary plus giving 1, and i++ yields 4 while making i 5; the second printf then yields 5.

18. **Which is correct output?** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 130 (ET: N/A)]*
   ```c
   int a = 100; int *p = &a +2; *p = 22; printf("%d", a);
   ```
   a) 100  
   b) 22  
   c) Error  
   d) Garbage value

   answer: a — 100  
   explanation: &a + 2 points past the variable, so writing 22 there does not touch a, which still prints 100 (this is undefined behaviour).

19. **Find the correct output:** *[Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021 compact it 130 (ET: N/A)], [Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 166 (ET: N/A)]*
   ```c
   int a = 10,b = 20; a ^= b; b ^= a; a ^= b;
   printf("%d %d", a, b);
   ```
   a) 20 30  
   b) 10 30  
   c) 20 10  
   d) Garbage Value

   answer: c — 20 10  
   explanation: The three XOR steps are the classic swap without a temporary, so a becomes 20 and b becomes 10.

20. **What is the correct output of the following C program statements?** *[Rupali Bank Ltd. Assistant Network Engineer (ANE) 2021 compact it 81 (ET: N/A)], [6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 88 (ET: N/A)], [Janata Bank Ltd. Assistant Network Engineer (SO) 2020 compact it 186 (ET: N/A)]*
   ```c
   int array[]={6, 7, 8, 9, 0, 1, 2, 4, 5, 6}, *p=array+5;
   printf("%d\n",p[1]);
   ```
   a. 1  
   b. 2  
   c. 3  
   d. Compile Error

   answer: b — 2  
   explanation: p points at array[5], so p[1] is array[6], which is 2.

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

   answer: d — 05  
   explanation: printf("0") prints 0 and returns 1 (characters written), which is true, so i becomes 5 and is printed after the 0.

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

   answer: a — 13  
   explanation: The calls run fun(4,3) → fun(3,7) → fun(2,10) → fun(1,12) → fun(0,13), and the last one returns y = 13.

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

   answer: c — x*y  
   explanation: The function adds x to itself y times before hitting the base case, which is repeated addition, i.e. x*y.

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

   answer: a — 0, f  
   explanation: The bytes are read through a char pointer, and the third member 'c'+3 is 99+3 = 102, which %c prints as f without quotes.

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

   answer: b — 99, 11  
   explanation: (a=99) is an assignment whose value 99 is non-zero, so the true branch runs and c gets b = 11, while a is now 99.

26. **What will be the output of following code?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 164 (ET: N/A)]*
   ```c
   int x=5, y=5, z=5;
   printf("%d", ++z+y-1-y+z+x++);
   ```
   a) 15  
   b) 17  
   c) 16  
   d) 19

   answer: c — 16  
   explanation: ++z makes z 6, then 6+5-1-5+6 = 11, and x++ adds its old value 5, giving 16.

27. **What will be the output of the given line?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 165 (ET: N/A)]*
   ```c
   printf("%d",sizeof(int));
   ```
   a) 2  
   b) 4  
   c) 1  
   d) 8

   answer: b — 4  
   explanation: On a normal 32-bit or 64-bit compiler an int is 4 bytes.

28. **Which for loop statement is invalid?** *[Sonali Bank Ltd. Assistant Database Administrator 2020 compact it 167 (ET: N/A)]*  
   a) for(int x=10; k<=5; x/9)  
   b) for(int x=10; x>=2; --x)  
   c) for(int x=10; x>=200; x=3*x)  
   d) for(int x=10; x>=0; x+=2)

   answer: a — for(int x=10; k<=5; x/9)  
   explanation: k is never declared, so the condition does not compile; the other three are syntactically valid even though (d) loops forever.

29. **Which type of following errors is generated when the program is being execute?** *[Sonali & Janata Bank Ltd. Officer (IT) 2020 compact it 159 (ET: N/A)]*  
   A) Syntax error  
   B) Semantic error  
   C) Run-time error  
   D) Linker error

   answer: C — Run-time error  
   explanation: Run-time errors, such as divide by zero or an invalid memory access, appear only while the program is executing.

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

   answer: c — 6 4 6  
   explanation: GCC evaluates printf arguments right to left, so i++ gives 4 (i becomes 5) and ++i then gives 6; the next printf yields 6.

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

   answer: c — No output (Output screen will be empty)  
   explanation: main only returns 0 — there is no printf — so the program compiles, runs and prints nothing.

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

   answer: b — 57  
   explanation: 5*10.5 + 5.0 = 57.5, and storing it in an int drops the fractional part.

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

   answer: b — 1-  
   explanation: A do-while always runs the body once, printing "1-" and making i 2; the test i<=0 then fails immediately.

34. **If any error occurs due to violation of programming rule is ________.** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 173 (ET: N/A)]*  
   a) Syntax error  
   b) Run-time Errors  
   c) Linker Errors  
   d) Logical Errors

   answer: a — Syntax error  
   explanation: Breaking the grammar rules of the language, such as a missing semicolon, is a syntax error caught by the compiler.

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

   answer: C — d  
   explanation: %c prints the character whose ASCII code is 100, which is 'd'.

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

   answer: d — Compiler Error  
   explanation: i is declared const, so the assignment in i++ is rejected at compile time.

## Control Statements & Loops (16)

1. **Which of the following statements about the "do while" loop is correct?** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 6 (ET: BIBM)]*  
   a) The condition is checked before the loop body is executed for the first time.  
   b) The loop body is guaranteed to execute at least once.  
   c) The loop condition must always be false for the loop to execute.  
   d) The "do while" loop and "while" loop have identical behavior in all cases.

   answer: b — The loop body is guaranteed to execute at least once  
   explanation: A do-while tests its condition after the body, so the body always runs once even if the condition is false.

2. **Which for loop has range of similar indexes of 'i' used in for (i = 0; i < n; i++)?** *[Combined Bank Officer (IT) 04.10.2024 compact it 16 (ET: BIBM)]*  
   (a) for (i= n; i>0; i--)  
   (b) for (i=n-1; i>0; i--)  
   (c) for (i = 0; i = 0; i--)  
   (d) for (i=n-1; i>-1; i--)

   answer: d — for (i=n-1; i>-1; i--)  
   explanation: The original loop covers i = 0 to n-1; this one runs i from n-1 down to 0, so it touches exactly the same index values.

3. **Consider int i=0; Then which of the following is not an infinite loop?** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*  
   a) for(;;){}  
   b) while ( ){}  
   c) while ( ++i<0) { --i;}  
   d) do {++i; while(--i<=0);

   answer: c — while ( ++i<0) { --i;}  
   explanation: With i starting at 0, ++i makes it 1 and 1<0 is false, so the loop body never runs at all.

4. **Which keyword is used to skip the rest of a loop and carry on from the top of the loop again?** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*  
   a) Break  
   b) resume  
   c) continue  
   d) skip

   answer: c — continue  
   explanation: continue abandons the rest of the current iteration and jumps to the next one; break leaves the loop entirely.

5. **What can be used to terminate for(;;)?** *[BCC Assistant Programmer 11.11.2023 compact it 36 (ET: N/A)]*  
   **Ans:** break statement

   answer: break statement  
   explanation: for(;;) has no exit condition, so a break inside the body (or a return/goto) is what ends it.

6. **The ________ loop is especially useful when you process a menu selection?** *[Combined 2 Banks Senior Officer (IT) 2020 compact it 170 (ET: N/A)]*  
   a) while  
   b) do-while  
   c) for  
   d) switch

   answer: b — do-while  
   explanation: A menu must be displayed once before the user can choose, and do-while runs the body before testing, so it fits naturally.

7. **C programming Language এ কোনো loop থেকে তৎক্ষণাৎ বের করার জন্য উল্লেখিত কোনটি ব্যবহৃত হয়?** *[BPSC Assistant Network Engineer 2019 compact it 196 (ET: N/A)]*  
   A) break  
   B) switch  
   C) continue  
   D) if

   answer: A — break  
   explanation: break immediately exits the innermost loop or switch and continues after it.

8. **Which Control statement can be executed at least once?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 235 (ET: N/A)]*  
   A) While  
   B) For  
   C) do-while  
   D) None of the above

   answer: C — do-while  
   explanation: Only do-while checks its condition after the body, so it always executes at least one time.

9. **Which of the following cannot be checked in a switch-case statement?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 238 (ET: N/A)]*  
   A) Character  
   B) Integer  
   C) Float  
   D) None of above

   answer: C — Float  
   explanation: switch needs an integral or enum expression; float and double are not allowed as case selectors.

10. **Which control statement can be executed at least once?** *[Combined Bank Maintenance Engineer 2018 compact it 226 (ET: N/A)]*  
   A) While  
   B) for  
   C) do-while  
   D) All of the above

   answer: C — do-while  
   explanation: The do-while body runs before the condition is tested, guaranteeing one execution.

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

   answer: A — /*+-  
   explanation: In C, * and / share the highest precedence here, then + and -, so the order is / * + - (option D is the same text). The two stray items pasted into this entry answer as: argv length — C (Undefined), and Math.round(2.5+Math.random()) — C (3).

12. **What is an example of iteration in C?** *[Combined 3 Bank Assistant Programmer 2018 compact it 231 (ET: N/A)]*  
   A) for  
   B) while  
   C) do-while  
   D) all of the above

   answer: D — all of the above  
   explanation: for, while and do-while are all iteration (looping) constructs in C.

13. **Which of the following format is a correct format for declaration of function?** *[Combined 3 Bank Assistant Programmer 2018 compact it 232 (ET: N/A)]*  
   A) return-type function-name (argument type);  
   B) return-type function-name (argument type) {}  
   C) return-type (argument type) function-name;  
   D) return-type {} function-name

   answer: A — return-type function-name (argument type);  
   explanation: A function declaration (prototype) states the return type, name and parameter types and ends with a semicolon; the version with {} is a definition.

14. **What are the final values of a and c in the following C statement? (initialize value a=2, c=1) c=c? c=2:a=0;** *[Combined 3 Bank Assistant Programmer 2018 compact it 233 (ET: N/A)]*  
   A) a=0, c=0  
   B) a=2, c=2  
   C) a=2, c=2  
   D) a=1, c=2

   answer: B — a=2, c=2  
   explanation: c is 1, which is true, so the conditional takes the first branch and sets c = 2; a is never touched and stays 2.

15. **Which of the following doesn’t require an ‘&’ for the input in scanf ( ) ?** *[Combined 3 Bank Assistant Programmer 2018 compact it 233 (ET: N/A)]*  
   A) char name [10];  
   B) int name [10];  
   C) float name[10];  
   D) double name [10];

   answer: A — char name [10];  
   explanation: For %s the array name already decays to the address of its first element, so scanf("%s", name) needs no &.

16. **Which are the keywords of structured programming?** *[Bangladesh Bank Assistant Programmer 2016 compact it 245 (ET: N/A)]*  
   A) Keywords  
   B) Constant  
   C) volatile  
   D) Above all

   answer: D — Above all  
   explanation: The exam key treats keywords, constants and storage qualifiers such as volatile as all belonging to structured C programming.

## Arrays & Functions (15)

1. **The number of values a function can return at a time?** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*  
   a) 1  
   b) 2  
   c) 0  
   d) more than 2

   answer: a — 1  
   explanation: A C function returns a single value; multiple results need pointers, a struct or global variables.

2. **Which of the following correctly accesses the seventh element stored in arr, an array with 100 elements?** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 27 (ET: BIBM)]*  
   a) arr[6]  
   b) arr[7]  
   c) arr{6}  
   d) arr{7}

   answer: a — arr[6]  
   explanation: Array indexing starts at 0, so the seventh element sits at index 6; braces are not valid subscript syntax.

3. **Which of the following do not return any value?** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 53 (ET: N/A)]*  
   (ক) Constructor function  
   (খ) Friend function  
   (গ) In line Function  
   (ঘ) Member Functions

   answer: ক — Constructor function  
   explanation: A constructor has no return type at all — not even void — because its job is to initialise the object.

4. **Assuming an int is of 4 bytes, What is the size of “int array[15]”?** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 55 (ET: N/A)]*  
   (ক) 15  
   (খ) 19  
   (গ) 11  
   (ঘ) 60

   answer: ঘ — 60  
   explanation: 15 elements × 4 bytes each = 60 bytes.

5. **In C++, The library function exit() causes an exit from-** *[BPSC (Ministry) Assistant Programmer 21.09.2022 compact it 57 (ET: N/A)]*  
   (ক) a block of statements  
   (খ) a loop in which it occurs  
   (গ) a function in which it occurs  
   (ঘ) a program in which it occurs

   answer: ঘ — a program in which it occurs  
   explanation: exit() terminates the whole program immediately and returns the status code to the operating system.

6. **Which of the following is correct to initialize arrays in C?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 83 (ET: N/A)]*  
   a. int array = (1, 2, 3, 4, 5)  
   b. int array = {1, 2, 3, 4, 5}  
   c. int array() = (1, 2, 3, 4, 5)  
   d. int array[5] = {1, 2, 3, 4, 5}

   answer: d — int array[5] = {1, 2, 3, 4, 5}  
   explanation: An array needs square brackets for its size and braces for the initialiser list; parentheses are not valid.

7. **What is the access methodology in array?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 83 (ET: N/A)]*  
   a. Sequential  
   b. Random  
   c. Rational  
   d. Stochastic

   answer: b — Random  
   explanation: Element i is reached by computing base + i×size, so any element takes the same constant time — random access.

8. **Which of the following is correct?** *[6 Banks & Financial Institutions Assistant Programmer 18.03.2021 compact it 84 (ET: N/A)]*  
   a. “X extends Y” is correct if and only if X is a class and Y is an interface  
   b. “X extends Y” is correct if and only if X is an interface and Y is a class  
   c. “X extends Y” is correct if X and Y are either both classes or both interfaces  
   d. “X extends Y” is correct for all combinations of X and Y being classes and/or interfaces

   answer: c — "X extends Y" is correct if X and Y are either both classes or both interfaces  
   explanation: A class extends a class and an interface extends an interface; a class uses implements, not extends, for an interface.

9. **An n*n array v is defined as follows: v[i, j]=i-j for all i, j; 1<=i<=n, 1<=j<=n, the sum of the element of array v is** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 207 (ET: AUST)]*  
   A) 0  
   B) n-1  
   C) n^2-3n+2  
   D) n^2(n+1)/2

   answer: A — 0  
   explanation: The terms pair up as (i-j) and (j-i), which cancel, and the diagonal terms are 0, so the whole sum is 0.

10. **When you pass array as an argument to a function, which actually gets passed?** *[BPSC Assistant Maintenance Engineer 2019 compact it 191 (ET: N/A)]*  
   (a) Base address of the array  
   (b) The first element of the array  
   (c) Address of the first element of the array  
   (d) Address of the last element of the array

   answer: a — Base address of the array  
   explanation: An array name decays to a pointer to its first element, so only that address is passed, not a copy of the data (option c says the same thing).

11. **int number [] = {10,20,30,40,50}; number[3] =?** *[Sonali & Janata Bank Assistant Programmer 2018 compact it 240 (ET: N/A)]*  
   A) 10  
   B) 20  
   C) 30  
   D) 40

   answer: D — 40  
   explanation: Indexing is zero-based, so number[3] is the fourth element, 40.

12. **Two dimensional arrays are also called?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 234 (ET: N/A)]*  
   A) table array  
   B) matrix array  
   C) both A and B  
   D) none of the above

   answer: C — both A and B  
   explanation: A 2-D array is arranged in rows and columns, so it is called both a table array and a matrix array.

13. **The smallest element of array index is called it-** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 235 (ET: N/A)]*  
   A) Lower Bound  
   B) Upper Bound  
   C) Range  
   D) Extraction

   answer: A — Lower Bound  
   explanation: The smallest valid index is the lower bound and the largest is the upper bound.

14. **What type of reference should be used in vector arithmetic in C++?** *[Combined Bank Senior Officer (IT) 2018 compact it 220 (ET: DU)]*  
   A) Dynamic  
   B) const  
   C) a and b  
   D) none of the mentioned

   answer: B — const  
   explanation: Vector arithmetic passes operands by const reference, which avoids copying large objects while guaranteeing they are not modified.

15. **In C, if you pass an array as an argument to a function, what actually gets passed?** *[Bangladesh Bank Assistant Programmer 2011 compact it 271 (ET: N/A)]*  
   a. Value of elements in array  
   b. First element of the array  
   c. Base address of the array  
   d. Address of the last element of the array

   answer: c — Base address of the array  
   explanation: The array name decays to a pointer to element 0, so the function receives that base address and works on the original array.

## Data Types & Variables (14)

1. **What is the minimum value that can be stored accurately in a 32-bit signed integer of C programming language?** *[Sonali, Janata and RAKUB AE (IT)/ AHME/ AME 2020 compact it 179 (ET: N/A)]*  
   a) 0  
   b) -2^{31}  
   c) -2^{31}-1  
   d) -2^{32}

   answer: b — -2^31  
   explanation: A 32-bit signed int in two's complement spans -2³¹ to 2³¹-1, so the minimum is -2147483648.

2. **What is the maximum value that can be stored in a 32-bit signed integer of C language?** *[Combined 4 Bank Assistant Programmer (AP) 2020 compact it 155 (ET: DU)]*  
   a) 10^{32}  
   b) 2^{32}  
   c) 2^{32}-1  
   d) 2^{31}-1

   answer: d — 2^31-1  
   explanation: One bit holds the sign, leaving 31 value bits, so the largest value is 2³¹-1 = 2147483647.

3. **C programming এ নিচের কোনটি Invalid variable name?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 187 (ET: N/A)], [BPSC Assistant Network Engineer 2019 compact it 197 (ET: N/A)]*  
   A) Average  
   B) No#of-students  
   C) Xyz  
   D) y23z

   answer: B — No#of-students  
   explanation: Identifiers may use only letters, digits and underscore and cannot start with a digit; # and - are not allowed.

4. **C কী ধরনের programming language?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 187 (ET: N/A)]*  
   A) Low level language  
   B) Mid-level language  
   C) High level language  
   D) None of these

   answer: B — Mid-level language  
   explanation: C is conventionally classed as a middle-level language because it has high-level structure yet also allows low-level work with pointers and bit operations.

5. **নিচের কোনটি C ভাষার Keyword নয়?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)]*  
   A) struct  
   B) int  
   C) star  
   D) float

   answer: C — star  
   explanation: struct, int and float are reserved C keywords; star is not, so it can be used as an identifier.

6. **C programming language এ নিচের কোনটিকে "if" দিয়ে Replace করা যায়?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)], [BPSC Assistant Network Engineer 2019 compact it 198 (ET: N/A)]*  
   A) switch  
   B) structure  
   C) return  
   D) for

   answer: A — switch  
   explanation: Any switch can be rewritten as a chain of if-else statements testing the same expression against each case value.

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

   answer: C — 1.414f or 1.414F  
   explanation: An unsuffixed floating constant is a double; the f or F suffix makes it a float without a cast. For the stray item pasted here: C — both (i) and (iii) are valid, since an identifier cannot begin with a digit but _ alone is legal.

8. **Variable which use same name in whole program and in its all routines thus best classified as-** *[Probashi Kallyan Bank Programmer: 2019 compact it 213 (ET: AUST)]*  
   A) middle variable  
   B) default variable  
   C) local variable  
   D) global variable

   answer: D — global variable  
   explanation: A global variable is declared outside every function, so the same name is visible to the whole program and all its routines.

9. **Which format specifier is used for typing double data?** *[BREB Assistant Junior Engineer (IT) 2019 compact it 218 (ET: N/A)]*  
   A) %f  
   B) %lf  
   C) %d  
   D) %s

   answer: B — %lf  
   explanation: scanf needs %lf for a double; %f reads a float.

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

   answer: C — com-pact  
   explanation: A hyphen is not allowed in an identifier — only letters, digits and underscore, and it may not start with a digit. The two stray items pasted here answer as: argv length — C (Undefined), and Math.round(2.5+Math.random()) — C (3).

11. **Which of the following correctly shows the hierarchy of algorithm operation in C?** *[Probashi Kallyan Bank Assistant Programmer 2018 compact it 236 (ET: N/A)]*  
   A) /*+-  
   B) *-/+  
   C) +-/*  
   D) /*+-

   answer: A — /*+-  
   explanation: / and * bind tightest and share a level, then + and -, so the order is / * + - (option D repeats the same text).

12. **The value 9.87 to 10 when use?** *[Bangladesh Bank Assistant Programmer 2016 compact it 246 (ET: N/A)]*  
   A) floor ()  
   B) ceil ()  
   C) both A & B  
   D) None

   answer: B — ceil ()  
   explanation: ceil() rounds up to the next whole number, turning 9.87 into 10; floor() would give 9.

13. **Hungarian notation is used to ________.** *[BREB Assistant General Manager (IT) 2016 compact it 254 (ET: N/A)]*  
   A) Design system manual  
   B) Design user manual  
   C) Define name of the variable  
   D) All

   answer: C — Define name of the variable  
   explanation: Hungarian notation prefixes a variable's name with a short tag for its type or purpose, such as iCount or szName.

14. **Which of the following is not derived data type in C?** *[Bangladesh Bank Assistant Programmer 2011 compact it 272 (ET: N/A)]*  
   a. Function  
   b. Pointer  
   c. Enumeration  
   d. Array

   answer: c — Enumeration  
   explanation: Arrays, pointers and functions are derived types built from basic types, while enum is a user-defined type.

## Operators & Expressions (11)

1. **Let x be an integer which can take a value of 0 or 1. The statement if (x==0) x=1; else x=0; is equivalent to which of the following?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 203 (ET: AUST)]*  
   A) x=1+x  
   B) x=1-x  
   C) x=x-1  
   D) x=1%x

   answer: B — x=1-x  
   explanation: With x limited to 0 or 1, 1-x flips 0 to 1 and 1 to 0, exactly what the if-else does.

2. **For a given integer, which of the following operators can be used to set and reset a particular bit respectively?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 203 (ET: AUST)]*  
   A) | and &  
   B) && and ||  
   C) & and |  
   D) || and &&

   answer: A — | and &  
   explanation: OR with a mask (x | 1<<n) turns a bit on, and AND with the inverted mask (x & ~(1<<n)) turns it off.

3. **Which of the declaration is correct?** *[Sonali & Janata Bank Officer (IT/ICT)- 2019 compact it 206 (ET: AUST)], [Probashi Kallyan Bank Assistant Programmer 2018 compact it 237 (ET: N/A)]*  
   A) int length;  
   B) char int  
   C) int long;  
   D) float double;

   answer: A — int length;  
   explanation: A declaration needs a type followed by an identifier; char int, int long; and float double; are not valid declarations.

4. **What is the precedence of arithmetic operators (from highest to lowest)?** *[Probashi Kallyan Bank Programmer: 2019 compact it 210 (ET: AUST)]*  
   A) %, +, /, *, -  
   B) +, -, %, *, /  
   C) %, +, -, *, /  
   D) %, *, /, +, -

   answer: D — %, *, /, +, -  
   explanation: %, * and / share the highest precedence level, and + and - come below them.

5. **Which is logical operator?** *[BREB Assistant General Manager (IT) 2016 compact it 253 (ET: N/A)]*  
   A) +  
   B) >=  
   C) AND  
   D) <<

   answer: C — AND  
   explanation: AND is a logical operator; + is arithmetic, >= is relational and << is a bitwise shift.

6. **Which of the following will not increase the value of variable c by 1?** *[BREB Assistant General Manager (IT) 2016 compact it 253 (ET: N/A)]*  
   A) c++  
   B) c = c + 1  
   C) c + 1 >= c  
   D) c += 1

   answer: C — c + 1 >= c  
   explanation: That line only evaluates a comparison and throws the result away — c is never assigned, so its value does not change.

7. **The escape sequence “\b” in C programming is -----** *[BREB Assistant General Manager (IT) 2016 compact it 254 (ET: N/A)]*  
   A) Backspace  
   B) Next Line  
   C) Tab  
   D) None of these

   answer: A — Backspace  
   explanation: \b moves the cursor one position back; \n is newline and \t is tab.

8. **What is not the kind of data type?** *[BREB Assistant General Manager (IT) 2016 compact it 254 (ET: N/A)]*  
   A) Logical  
   B) Text  
   C) Number  
   D) Currency

   answer: D — Currency  
   explanation: Logical, text and number are the basic categories of data, while currency is a formatted number rather than a distinct kind of data type. <!-- verify -->

9. **Which keyword is used in C language?** *[BREB Assistant General Manager (IT) 2016 compact it 255 (ET: N/A)]*  
   A) ing  
   B) for  
   C) select  
   D) href

   answer: B — for  
   explanation: for is a C keyword; ing, select and href are not part of the C language.

10. **Find out the error in following block of code: if (x=100) cout<<"x is 100";** *[Bangladesh Bank Assistant Programmer 2011 compact it 271 (ET: N/A)]*  
   a. 100 should be enclosed in quotations  
   b. There is no semicolon at the end of first line  
   c. Equals to operator mistake  
   d. Variable x should not be inside quotation

   answer: c — Equals to operator mistake  
   explanation: x=100 is an assignment that is always true; comparison needs the == operator.

11. **Which of the following is not a logical operator?** *[Bangladesh Bank Assistant Programmer 2011 compact it 271 (ET: N/A)]*  
   a. &  
   b. &&  
   c. ||  
   d. |

   answer: a — &  
   explanation: & is bitwise AND, not a logical operator — the logical ones are && and ||. Note | is also bitwise, so the option set is loose.

## Programming Concepts (8)
1. **Which of the following is used to restrict access to certain details of an object in OOP? [ OOP-এ কোনটি object-এর কিছু বিস্তারিত তথ্য অ্যাক্সেস সীমিত করতে ব্যবহৃত হয়?]** *[Combined Bank Senior Officer (IT) Date: 17.10.2025 [bitbox it book 218]]*  
   (a) Polymorphism  
   (b) Inheritance  
   (c) Abstraction  
   (d) Encapsulation

   answer: d — Encapsulation  
   explanation: Encapsulation bundles data with its methods and hides internal fields behind private access, so outside code cannot reach those details directly.

2. **(a) Write a JavaScript function to validate an email.** *[Dhaka Power Distribution Company Limited Assistant Engineer (ICT) Exam Date: 17.10.2025 Time: 1 Hour, Total Marks: 100 (MCQ: 20, Written: 8×10 = 80) [bitbox it book 236]]*

   answer: Use a regular expression test inside a function, e.g. function validateEmail(e) { return /^[^\s@]+@[^\s@]+\.[^\s@]{2,}$/.test(e); }  
   explanation: The pattern requires a non-empty local part, one @, a domain, and a dot followed by a top-level domain of at least two characters; it returns true or false.

3. **In a doubly linked list, the number of pointers affected in insertion operation will be— [ ডাবলি লিঙ্কড লিস্টে ইনসারশন অপারেশনে কতটি পয়েন্টার প্রভাবিত হয়? ]** *[Bankers' Selection Committee Secretariat Post: Assistant Programmer; Date: 15 Feb, 2024 Exam Taker: ANZA; Post: 35 [bitbox it book 347]]*  
   (A) 5  
   (B) 0  
   (C) 1  
   (D) None of these

   answer: D — None of these  
   explanation: Inserting a node in the middle of a doubly linked list changes 4 pointers (the new node's prev and next, plus the neighbours' links), and 4 is not offered.

4. **What is the class and subnet mask if the subnet mask is 255.224.0.0? [ সাবনেট মাস্ক 255.224.0.0 হলে এর ক্লাস এবং মাস্ক বিট কত? ]** *[Bankers' Selection Committee Secretariat Post: Assistant Programmer; Date: 15 Feb, 2024 Exam Taker: ANZA; Post: 35 [bitbox it book 348]]*  
   (A) Class A, 8  
   (B) Class A, 3  
   (C) Class B, 3  
   (D) Class B, 32

   answer: B — Class A, 3  
   explanation: The first octet 255 makes it Class A whose default mask is /8, and 224 = 11100000 adds 3 subnet bits, giving 255.224.0.0 = /11.

5. **Martin Cooper is known for his invention of— [ Martin Cooper কোন উদ্ভাবনের জন্য পরিচিত? ]** *[Bankers' Selection Committee Secretariat Post: Senior Office (IT); Date: 04 October, 2024 Exam Taker: ANZA; Post: 222 [bitbox it book 499]]*  
   (a) Digital Camera  
   (b) X-ray  
   (c) Mobile Phone  
   (d) Telephone

   answer: c — Mobile Phone  
   explanation: Martin Cooper of Motorola made the first handheld mobile phone call in 1973.

6. **What is the main goal of reinforcement learning?[ রিইনফোর্সমেন্ট লার্নিং (Reinforcement learning) এর প্রধান লক্ষ্য কী? ]** *[Bankers' Selection Committee Secretariat Post: Senior Office (IT); Date: 04 October, 2024 Exam Taker: ANZA; Post: 222 [bitbox it book 502]]*  
   (a) To classify data into categories  
   (b) To optimize a system for maximum efficiency  
   (c) To make predinction based on historical data  
   (d) To learn optima actions through trail and error

   answer: d — To learn optima actions through trail and error  
   explanation: A reinforcement learning agent explores an environment and uses reward and penalty signals to discover the actions that maximise long-term reward.

7. **Which for loop has range of similar indexes of ‘i’ used in for(i=0; i<n; i++)?[ for(i=0; i<n; i++) লুপের সমান ইনডেক্স রেঞ্জ নিচের কোন লুপটিতে ব্যবহৃত হয়েছে? ]** *[Bankers' Selection Committee Secretariat Post: Senior Office (IT); Date: 04 October, 2024 Exam Taker: ANZA; Post: 222 [bitbox it book 508]]*  
   (a) for (i=n; i>0; i--)  
   (b) for (i=n-1; i>0; i--)  
   (c) for (i=0; i=0; i--)  
   (d) for (i=n-1; i>=0; i--)

   answer: d — for (i=n-1; i>=0; i--)  
   explanation: The original loop covers indexes 0 to n-1; this one counts down from n-1 to 0, so it visits the same set of values.

8. **A collection of objects that use common structure and a common behavior is known as—[ একই কাঠামো এবং একই আচরণ ব্যবহার করে এমন অবজেক্টের সংগ্রহকে কী বলা হয়? ]** *[Bankers' Selection Committee Secretariat Post: Senior Office (IT); Date: 04 October, 2024 Exam Taker: ANZA; Post: 222 [bitbox it book 509]]*  
   (a) Object  
   (b) Entity  
   (c) Instance  
   (d) Class

   answer: d — Class  
   explanation: A class is the blueprint that defines the common attributes and behaviour shared by all its objects.

## Pointers & Memory Allocation (5)

1. **Address stored in the pointer variable is of type ______** *[NPCBL Executive Trainee (Software) 2023 compact it 40 (ET: N/A)]*  
   a) Integer  
   b) Float  
   c) Character  
   d) Double

2. **Address variable রাখা যায় কোনটিতে?** *[BPSC Assistant Programmer (Dept. of ICT) 2020 compact it 188 (ET: N/A)]*  
   A) Break  
   B) Int  
   C) Pointer  
   D) Float

3. **C-programming এ address রাখার জন্য কোনটি সাধারণত ব্যবহৃত হয়?** *[BPSC Assistant Network Engineer 2019 compact it 196 (ET: N/A)]*  
   A) break  
   B) pointer  
   C) char  
   D) float

4. **What is the following declaration for? int (*a)[10];** *[BPSC Assistant Maintenance Engineer 2019 compact it 192 (ET: N/A)]*  
   (a) Pointer to an array of 10 integers  
   (b) Array of 10 function Pointers returning integer  
   (c) A pointer of to function returning an array to 10 integers  
   (d) Array of 10 integers pointers

5. **Which header file should be included to use functions like malloc() and calloc()?** *[Bangladesh Bank Assistant Programmer 2011 compact it 271 (ET: N/A)]*  
   a. memory.h  
   b. stdlib.h  
   c. string.h  
   d. dos.h

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
