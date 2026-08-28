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
