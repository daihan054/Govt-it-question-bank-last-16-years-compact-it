<!-- TOC START -->
**Table of Contents** — 9 subtopics · 105 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Output Tracing](#output-tracing) | 36 |
| 2 | [Control Statements & Loops](#control-statements--loops) | 16 |
| 3 | [Arrays & Functions](#arrays--functions) | 15 |
| 4 | [Data Types & Variables](#data-types--variables) | 14 |
| 5 | [Operators & Expressions](#operators--expressions) | 11 |
| 6 | [Pointers & Memory Allocation](#pointers--memory-allocation) | 5 |
| 7 | [Recursion](#recursion) | 4 |
| 8 | [Storage Classes & Scope](#storage-classes--scope) | 3 |
| 9 | [Flowcharts & Algorithms](#flowcharts--algorithms) | 1 |

<!-- TOC END -->

---

## Control Statements & Loops

1. **Which of the following statements about the "do while" loop is correct?** **(Combined Bank Senior Officer (IT) Exam: 17.05.2024 (BIBM)) [compact it 6]**
   a) The condition is checked before the loop body is executed for the first time.
   b) The loop body is guaranteed to execute at least once.
   c) The loop condition must always be false for the loop to execute.
   d) The "do while" loop and "while" loop have identical behavior in all cases.

2. **Which for loop has range of similar indexes of 'i' used in for (i = 0; i < n; i++)?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
   (a) for (i= n; i>0; i--)
   (b) for (i=n-1; i>0; i--)
   (c) for (i = 0; i = 0; i--)
   (d) for (i=n-1; i>-1; i--)

3. **Consider int i=0; Then which of the following is not an infinite loop?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) for(;;){}
   b) while ( ){}
   c) while ( ++i<0) { --i;}
   d) do {++i; while(--i<=0);

4. **Which keyword is used to skip the rest of a loop and carry on from the top of the loop again?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) Break
   b) resume
   c) continue
   d) skip

5. **What can be used to terminate for(;;)?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** break statement

6. **The ________ loop is especially useful when you process a menu selection?** **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 170]**
   a) while
   b) do-while
   c) for
   d) switch

7. **C programming Language এ কোনো loop থেকে তৎক্ষণাৎ বের করার জন্য উল্লেখিত কোনটি ব্যবহৃত হয়?** **(BPSC Assistant Network Engineer Exam: 2019) [compact it 196]**
   A) break
   B) switch
   C) continue
   D) if

8. **Which Control statement can be executed at least once?** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 235]**
   A) While
   B) For
   C) do-while
   D) None of the above

9. **Which of the following cannot be checked in a switch-case statement?** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 238]**
   A) Character
   B) Integer
   C) Float
   D) None of above

10. **Which control statement can be executed at least once?** **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 226]**
   A) While
   B) for
   C) do-while
   D) All of the above

11. **Which of the following correctly shows the hierarchy of algorithm operation in C?** **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 227]**
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
   What is the maximum length of character array argv in the above code? **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 227]**
   A) 0
   B) 1
   C) Undefined
   D) -1
   26. Which is the value of “d” after this line of code has been executed?
   double d = Math.round(2.5+math.random()); **(Combined Bank Maintenance Engineer MCQ Test: 2018) [compact it 227]**
   A) 2
   B) 2.5
   C) 3
   D) 4

12. **What is an example of iteration in C?** **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 231]**
   A) for
   B) while
   C) do-while
   D) all of the above

13. **Which of the following format is a correct format for declaration of function?** **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 232]**
   A) return-type function-name (argument type);
   B) return-type function-name (argument type) {}
   C) return-type (argument type) function-name;
   D) return-type {} function-name

14. **What are the final values of a and c in the following C statement? (initialize value a=2, c=1) c=c? c=2:a=0;** **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 233]**
   A) a=0, c=0
   B) a=2, c=2
   C) a=2, c=2
   D) a=1, c=2

15. **Which of the following doesn’t require an ‘&’ for the input in scanf ( ) ?** **(Combined 3 Bank Assistant Programmer MCQ Test: 2018) [compact it 233]**
   A) char name [10];
   B) int name [10];
   C) float name[10];
   D) double name [10];

16. **Which are the keywords of structured programming?** **(Bangladesh Bank Assistant Programmer Preliminary Exam: 2016) [compact it 245]**
   A) Keywords
   B) Constant
   C) volatile
   D) Above all

## Output Tracing

1. **What will be the output of the following C code?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
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

2. **What will be the output of the following C code?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
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

3. **What will be the output of the following C code?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 16]**
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

4. **What will be the output of the following C code?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 17]**
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

5. **What will be the output of the following C code?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 17]**
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

6. **What will be the output of the following C code?** **(Combined Bank Officer (IT) Exam: 04.10.2024 (BIBM)) [compact it 17]**
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

7. **Find Output:** **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xviii]**
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

8. **Find Output:** **(Bangladesh Bank Assistant Director (ICT) Exam: 07.02.2025 (DU)) [compact it xviii]**
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

9. **What will be the output of this C program?** **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 19]**
   ```c
   #include<stdio.h>
   ```c
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

10. **Which of the following Output of this program?** **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 21]**
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

11. **Given Output:** **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 21]**
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

12. **How many times will loop iterate?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 38]**
   (a) 9
   (b) 10
   (c) 8
   (d) infinite

13. **What will be the output of the following “C” code fragment?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
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

14. **Determine Output:** **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 26]**
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

15. **Determine Output:** **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 27]**
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

16. **Assume that the size of an integer is 4 bytes, predict the output of following program.** **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 28]**
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

17. **Which is the correct output?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 129]**
   ```c
   int i = 4; printf("%d %d", +1,i++); printf("%d", i++);
   ```
   a) 4 5 6
   b) 5 7 8
   c) 6 4 6
   d) 1 4 5

18. **Which is correct output?** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]**
   ```c
   int a = 100; int *p = &a +2; *p = 22; printf("%d", a);
   ```
   a) 100
   b) 22
   c) Error
   d) Garbage value

19. **Find the correct output:** **(Sonali, Janata & Rupali Bank Ltd. Senior Officer (AHE) / AE (IT)/ AME 25.10.2021) [compact it 130]** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 166]**
   ```c
   int a = 10,b = 20; a ^= b; b ^= a; a ^= b;
   printf("%d %d", a, b);
   ```
   a) 20 30
   b) 10 30
   c) 20 10
   d) Garbage Value

20. **What is the correct output of the following C program statements?** **(Rupali Bank Ltd. Assistant Network Engineer (ANE) Exam: 2021) [compact it 81]** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 88]** **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 186]**
   ```c
   int array[]={6, 7, 8, 9, 0, 1, 2, 4, 5, 6}, *p=array+5;
   printf("%d\n",p[1]);
   ```
   a. 1
   b. 2
   c. 3
   d. Compile Error

21. **What is the output for the following C code segment?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 84]**
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

22. **Consider the function fun (x, y) below. That is the value of fun (4, 3)?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 87]**
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

23. **What does the following function do?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 87]**
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

24. **Find Output:** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 90]**
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

25. **Find the output:** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 163]**
   ```c
   int a= 10, c, b;
   c = (a=99)? b = 11:20;
   printf("%d, %d", a, c);
   ```
   a) 11, 99
   b) 99, 11
   c) 20, 11
   d) 99, 20

26. **What will be the output of following code?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 164]**
   ```c
   int x=5, y=5, z=5;
   printf("%d", ++z+y-1-y+z+x++);
   ```
   a) 15
   b) 17
   c) 16
   d) 19

27. **What will be the output of the given line?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 165]**
   ```c
   printf("%d",sizeof(int));
   ```
   a) 2
   b) 4
   c) 1
   d) 8

28. **Which for loop statement is invalid?** **(Sonali Bank Ltd. Assistant Database Administrator Exam: 2020) [compact it 167]**
   a) for(int x=10; k<=5; x/9)
   b) for(int x=10; x>=2; --x)
   c) for(int x=10; x>=200; x=3*x)
   d) for(int x=10; x>=0; x+=2)

29. **Which type of following errors is generated when the program is being execute?** **(Sonali & Janata Bank Ltd. Officer (IT) Exam: 2020) [compact it 159]**
   A) Syntax error
   B) Semantic error
   C) Run-time error
   D) Linker error

30. **Which is the correct output?** **(Janata Bank Ltd. Assistant Network Engineer (SO) Exam: 2020) [compact it 180]**
   ```c
   int i = 4;
   printf ("%d%d", ++i, i++);
   printf ("%d ", i++);
   ```
   a) 5 4 6
   b) 5 7 8
   c) 6 4 6
   d) 4 5 7

31. **What will happen if this C program is compiled and executed?** **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 152]**
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

32. **What will be the output of this C program?** **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 153]**
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

33. **What will be the output of this C program?** **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 153]**
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

34. **If any error occurs due to violation of programming rule is ________.** **(Combined 2 Banks Senior Officer (IT) Exam: 2020) [compact it 173]**
   a) Syntax error
   b) Run-time Errors
   c) Linker Errors
   d) Logical Errors

35. **Find output in C- Program:** **(BPSC Assistant Network Engineer Exam: 2019) [compact it 198]**
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

36. **What will be output if you compile & and execute following C code?** **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 272]**
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

## Storage Classes & Scope

1. **Which of the following is not a storage class specifier in C?** **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 21]**
   (A) auto
   (B) register
   (C) static
   (D) extern
   (E) volatile

2. **In C, static storage class cannot be used with:** **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 21]**
   (A) Global variabl
   (B) Function parameter
   (C) Function name
   (D) Local variable

3. **Which of the following storage classes have global visibility in C/C++?** **(Combined Bank Assistant Programmer Exam: 09.02.2024 (BIBM)) [compact it 21]**
   (A) Auto
   (B) Extern
   (C) Static
   (D) Register

## Arrays & Functions

1. **The number of values a function can return at a time?** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) 1
   b) 2
   c) 0
   d) more than 2

2. **Which of the following correctly accesses the seventh element stored in arr, an array with 100 elements?** **(Bangladesh Bank Assistant Programmer Exam: 03.02.2023 (BIBM)) [compact it 27]**
   a) arr[6]
   b) arr[7]
   c) arr{6}
   d) arr{7}

3. **Which of the following do not return any value?** **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 53]**
   (ক) Constructor function
   (খ) Friend function
   (গ) In line Function
   (ঘ) Member Functions

4. **Assuming an int is of 4 bytes, What is the size of “int array[15]”?** **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 55]**
   (ক) 15
   (খ) 19
   (গ) 11
   (ঘ) 60

5. **In C++, The library function exit() causes an exit from-** **(BPSC (Ministry) Assistant Programmer Exam: 21.09.2022) [compact it 57]**
   (ক) a block of statements
   (খ) a loop in which it occurs
   (গ) a function in which it occurs
   (ঘ) a program in which it occurs

6. **Which of the following is correct to initialize arrays in C?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 83]**
   a. int array = (1, 2, 3, 4, 5)
   b. int array = {1, 2, 3, 4, 5}
   c. int array() = (1, 2, 3, 4, 5)
   d. int array[5] = {1, 2, 3, 4, 5}

7. **What is the access methodology in array?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 83]**
   a. Sequential
   b. Random
   c. Rational
   d. Stochastic

8. **Which of the following is correct?** **(6 Banks & Financial Institutions Assistant Programmer Exam: 18.03.2021) [compact it 84]**
   a. “X extends Y” is correct if and only if X is a class and Y is an interface
   b. “X extends Y” is correct if and only if X is an interface and Y is a class
   c. “X extends Y” is correct if X and Y are either both classes or both interfaces
   d. “X extends Y” is correct for all combinations of X and Y being classes and/or interfaces

9. **An n*n array v is defined as follows: v[i, j]=i-j for all i, j; 1<=i<=n, 1<=j<=n, the sum of the element of array v is** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 207]**
   A) 0
   B) n-1
   C) n^2-3n+2
   D) n^2(n+1)/2

10. **When you pass array as an argument to a function, which actually gets passed?** **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 191]**
   (a) Base address of the array
   (b) The first element of the array
   (c) Address of the first element of the array
   (d) Address of the last element of the array

11. **int number [] = {10,20,30,40,50}; number[3] =?** **(Sonali & Janata Bank Assistant Programmer Preliminary Exam: 2018) [compact it 240]**
   A) 10
   B) 20
   C) 30
   D) 40

12. **Two dimensional arrays are also called?** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 234]**
   A) table array
   B) matrix array
   C) both A and B
   D) none of the above

13. **The smallest element of array index is called it-** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 235]**
   A) Lower Bound
   B) Upper Bound
   C) Range
   D) Extraction

14. **What type of reference should be used in vector arithmetic in C++?** **(Combined Bank Senior Officer (IT) Exam: 2018 Exam Taker: DU) [compact it 220]**
   A) Dynamic
   B) const
   C) a and b
   D) none of the mentioned

15. **In C, if you pass an array as an argument to a function, what actually gets passed?** **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 271]**
   a. Value of elements in array
   b. First element of the array
   c. Base address of the array
   d. Address of the last element of the array

## Pointers & Memory Allocation

1. **Address stored in the pointer variable is of type ______** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) Integer
   b) Float
   c) Character
   d) Double

2. **Address variable রাখা যায় কোনটিতে?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 188]**
   A) Break
   B) Int
   C) Pointer
   D) Float

3. **C-programming এ address রাখার জন্য কোনটি সাধারণত ব্যবহৃত হয়?** **(BPSC Assistant Network Engineer Exam: 2019) [compact it 196]**
   A) break
   B) pointer
   C) char
   D) float

4. **What is the following declaration for? int (*a)[10];** **(BPSC Assistant Maintenance Engineer Exam: 2019) [compact it 192]**
   (a) Pointer to an array of 10 integers
   (b) Array of 10 function Pointers returning integer
   (c) A pointer of to function returning an array to 10 integers
   (d) Array of 10 integers pointers

5. **Which header file should be included to use functions like malloc() and calloc()?** **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 271]**
   a. memory.h
   b. stdlib.h
   c. string.h
   d. dos.h

## Recursion

1. **When a function is called more than one time that is called?** **(BCC Assistant Programmer Exam: 11.11.2023) [compact it 36]**
   **Ans:** This is known as function reusability or recursion or Idempotence

2. **How many function calls will be performed to execute the following recursive function?** **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 156]**
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

3. **Consider the following recursive function fun (x,y) . What is the value of fun (4,3) ?** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 204]**
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

4. **An algorithm that calls itself directly or indirectly is known as?** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 234]** **(Sonali Bank Limited Assistant Programmer Preliminary Exam: 2016) [compact it 252]**
   A) Sub Algorithm
   B) Recursion
   C) Polish Notation
   D) Traversal algorithm

## Data Types & Variables

1. **What is the minimum value that can be stored accurately in a 32-bit signed integer of C programming language?** **(Sonali, Janata and RAKUB AE (IT)/ AHME/ AME Exam: 2020) [compact it 179]**
   a) 0
   b) -2^{31}
   c) -2^{31}-1
   d) -2^{32}

2. **What is the maximum value that can be stored in a 32-bit signed integer of C language?** **(Combined 4 Bank Assistant Programmer (AP) Exam: 2020 (DU)) [compact it 155]**
   a) 10^{32}
   b) 2^{32}
   c) 2^{32}-1
   d) 2^{31}-1

3. **C programming এ নিচের কোনটি Invalid variable name?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 187]** **(BPSC Assistant Network Engineer Exam: 2019) [compact it 197]**
   A) Average
   B) No#of-students
   C) Xyz
   D) y23z

4. **C কী ধরনের programming language?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 187]**
   A) Low level language
   B) Mid-level language
   C) High level language
   D) None of these

5. **নিচের কোনটি C ভাষার Keyword নয়?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 188]**
   A) struct
   B) int
   C) star
   D) float

6. **C programming language এ নিচের কোনটিকে "if" দিয়ে Replace করা যায়?** **(BPSC Assistant Programmer (Dept. of ICT) Exam: 2020) [compact it 188]** **(BPSC Assistant Network Engineer Exam: 2019) [compact it 198]**
   A) switch
   B) structure
   C) return
   D) for

7. **Suppose a C program has floating constant 1.414, what's the best way to convert it as a float data type?** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 203]**
   A) (float)1.414
   B) float (1.414)
   C) 1.414f or 1.414F
   D) None of these
   3. Consider the following variable declarations and definitions in C:
   (i) int var_9=1
   (ii) int 9_var=2
   (iii) int _=3
   Choose the correct statement w.r.t above variables. **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 203]**
   A) Both (i) and (ii) are valid
   B) Only (i) is valid
   C) Both (i) and (iii) are valid
   D) All of these

8. **Variable which use same name in whole program and in its all routines thus best classified as-** **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 213]**
   A) middle variable
   B) default variable
   C) local variable
   D) global variable

9. **Which format specifier is used for typing double data?** **(BREB Assistant Junior Engineer (IT) Exam: 2019) [compact it 218]**
   A) %f
   B) %lf
   C) %d
   D) %s

10. **Which one of the following is not a valid identifier?** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 235]**
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
   What is the maximum length of character array argv in the above code? **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 236]**
   A) 0
   B) 1
   C) Undefined
   D) -1
   18. Which is the value of “d” after this line of code has been executed?
   double d=Math.round(2.5+Math.random()); **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 236]**
   A) 2
   B) 2.5
   C) 3
   D) 4

11. **Which of the following correctly shows the hierarchy of algorithm operation in C?** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 236]**
   A) /*+-
   B) *-/+
   C) +-/*
   D) /*+-

12. **The value 9.87 to 10 when use?** **(Bangladesh Bank Assistant Programmer Preliminary Exam: 2016) [compact it 246]**
   A) floor ()
   B) ceil ()
   C) both A & B
   D) None

13. **Hungarian notation is used to ________.** **(BREB Assistant General Manager (IT) Preliminary Exam: 2016) [compact it 254]**
   A) Design system manual
   B) Design user manual
   C) Define name of the variable
   D) All

14. **Which of the following is not derived data type in C?** **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 272]**
   a. Function
   b. Pointer
   c. Enumeration
   d. Array

## Flowcharts & Algorithms

1. **In flowchart what does below represent?** **(Bangladesh Bank Data Entry Operator (IT) Exam: 2020) [compact it 189]**
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

## Operators & Expressions

1. **Let x be an integer which can take a value of 0 or 1. The statement if (x==0) x=1; else x=0; is equivalent to which of the following?** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 203]**
   A) x=1+x
   B) x=1-x
   C) x=x-1
   D) x=1%x

2. **For a given integer, which of the following operators can be used to set and reset a particular bit respectively?** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 203]**
   A) | and &
   B) && and ||
   C) & and |
   D) || and &&

3. **Which of the declaration is correct?** **(Sonali & Janata Bank Officer (IT/ICT)-2019 Exam Taker: AUST) [compact it 206]** **(Probashi Kallyan Bank Assistant Programmer Preliminary Exam: 2018) [compact it 237]**
   A) int length;
   B) char int
   C) int long;
   D) float double;

4. **What is the precedence of arithmetic operators (from highest to lowest)?** **(Probashi Kallyan Bank Programmer: 2019 Exam Taker: AUST) [compact it 210]**
   A) %, +, /, *, -
   B) +, -, %, *, /
   C) %, +, -, *, /
   D) %, *, /, +, -

5. **Which is logical operator?** **(BREB Assistant General Manager (IT) Preliminary Exam: 2016) [compact it 253]**
   A) +
   B) >=
   C) AND
   D) <<

6. **Which of the following will not increase the value of variable c by 1?** **(BREB Assistant General Manager (IT) Preliminary Exam: 2016) [compact it 253]**
   A) c++
   B) c = c + 1
   C) c + 1 >= c
   D) c += 1

7. **The escape sequence “\b” in C programming is -----** **(BREB Assistant General Manager (IT) Preliminary Exam: 2016) [compact it 254]**
   A) Backspace
   B) Next Line
   C) Tab
   D) None of these

8. **What is not the kind of data type?** **(BREB Assistant General Manager (IT) Preliminary Exam: 2016) [compact it 254]**
   A) Logical
   B) Text
   C) Number
   D) Currency

9. **Which keyword is used in C language?** **(BREB Assistant General Manager (IT) Preliminary Exam: 2016) [compact it 255]**
   A) ing
   B) for
   C) select
   D) href

10. **Find out the error in following block of code: if (x=100) cout<<"x is 100";** **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 271]**
   a. 100 should be enclosed in quotations
   b. There is no semicolon at the end of first line
   c. Equals to operator mistake
   d. Variable x should not be inside quotation

11. **Which of the following is not a logical operator?** **(Bangladesh Bank Assistant Programmer Exam: 2011) [compact it 271]**
   a. &
   b. &&
   c. ||
   d. |
