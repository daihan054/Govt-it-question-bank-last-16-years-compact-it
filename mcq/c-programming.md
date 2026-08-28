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

## Pointers & Memory Allocation

1. **Address stored in the pointer variable is of type ______** **(NPCBL Executive Trainee (Software) Exam: 2023) [compact it 40]**
   a) Integer
   b) Float
   c) Character
   d) Double

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
