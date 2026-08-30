<!-- TOC START -->
**Table of Contents** — 9 subtopics · 202 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Basic Programs & Control Statements](#basic-programs--control-statements-86) | 86 |
| 2 | [Output Tracing & Control Flow](#output-tracing--control-flow-35) | 35 |
| 3 | [Recursion & Functions](#recursion--functions-32) | 32 |
| 4 | [Operators, Data Types & Language Concepts](#operators-data-types--language-concepts-17) | 17 |
| 5 | [Flowcharts & Algorithms](#flowcharts--algorithms-12) | 12 |
| 6 | [String Manipulation & Algorithms](#string-manipulation--algorithms-11) | 11 |
| 7 | [File Handling](#file-handling-4) | 4 |
| 8 | [Pointers](#pointers-4) | 4 |
| 9 | [Command Line Arguments & Basic Programs](#command-line-arguments--basic-programs-1) | 1 |

<!-- TOC END -->

---

## Basic Programs & Control Statements (86)

1. **Write a C program to check the number in EVEN or ODD.** *[BCC CA Monitoring System Project 2021 compact it 830 (ET: N/A)], [BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*


   Answer:

   ```c
   #include <stdio.h>
   int main() {
       int n;
       scanf("%d", &n);
       if (n % 2 == 0) printf("Even");
       else printf("Odd");
       return 0;
   }
   ```

   - If the remainder after dividing by 2 is 0, the number is even. Otherwise it is odd.
   - Time complexity O(1).
2. **Write a C/Java program to determine if a given year is a leap year nor not.** *[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*


   Answer:

   ```c
   #include <stdio.h>
   int main() {
       int y;
       scanf("%d", &y);
       if ((y % 4 == 0 && y % 100 != 0) || y % 400 == 0)
           printf("Leap year");
       else
           printf("Not a leap year");
       return 0;
   }
   ```

   - A year is a leap year if it is divisible by 4 but not by 100, or if it is divisible by 400.
   - So 2000 is a leap year but 1900 is not.
3. **Write a structured program (in C or Python) that takes an integer input n and prints the sum of all even numbers from 1 to n.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1423 (ET: E-Zone)]*


   Answer:

   ```c
   #include <stdio.h>
   int main() {
       int n, i, sum = 0;
       scanf("%d", &n);
       for (i = 2; i <= n; i += 2)
           sum += i;
       printf("Sum of even numbers = %d", sum);
       return 0;
   }
   ```

   - The loop starts at 2 and steps by 2, so only even numbers are added.
   - Time complexity O(n).
4. **(a) Difference between a while loop and do-while loop.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1446 (ET: N/A)]*


   Answer:

   | Point | while loop | do-while loop |
   |---|---|---|
   | Condition check | Before the body runs | After the body runs |
   | Minimum executions | 0, the body may never run | 1, the body always runs once |
   | Type | Entry controlled loop | Exit controlled loop |
   | Syntax ending | No semicolon after the closing brace | Semicolon required after while |

   - while: `while (cond) { body }`
   - do-while: `do { body } while (cond);`
   - Example: if the condition is false at the start, a while loop prints nothing, but a do-while prints once.
5. **Write down a program is any high level language to read an integer and display a pattern like below. For example, if the given integer number is 1234, then the following pattern will be printed.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1354 (ET: N/A)]*
```
1 2 3 4
2 3 4
3 4
4
```


   Answer:

   ```c
   #include <stdio.h>
   int main() {
       char s[20];
       int i, j, len = 0;
       scanf("%s", s);
       while (s[len] != '\0') len++;
       for (i = 0; i < len; i++) {
           for (j = i; j < len; j++)
               printf("%c ", s[j]);
           printf("\n");
       }
       return 0;
   }
   ```

   - We read the number as a string. So we can print each digit on its own.
   - Row i starts at digit i and goes to the last digit. That makes the triangle shape.
6. **a) Suppose you are working with an array of size 10. It contains all the numbers from 1 to 10 exactly once in a random order. But accidentally, one of the numbers in the array got replaced by a zero (0). Write a C/C++ programme using functions, to restore the lost number.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1343 (ET: N/A)]*


   Answer:

   ```c
   #include <stdio.h>
   int main() {
       int a[9], i, sum = 0;
       for (i = 0; i < 9; i++) {
           scanf("%d", &a[i]);
           sum += a[i];
       }
       printf("Missing number = %d", 55 - sum);
       return 0;
   }
   ```

   - The sum of 1 to 10 is n(n+1)/2 = 55.
   - We subtract the sum of the given numbers from 55. What is left is the missing number.
   - Time complexity O(n) and space complexity O(1).
7. **Find biggest elements in an array of 10 components.** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*


   Answer:

   ```c
   #include <stdio.h>
   int main() {
       int a[10], i, max;
       for (i = 0; i < 10; i++) scanf("%d", &a[i]);
       max = a[0];
       for (i = 1; i < 10; i++)
           if (a[i] > max) max = a[i];
       printf("Largest = %d", max);
       return 0;
   }
   ```

   - We take the first element as the largest. Then we compare every other element with it once.
   - Time complexity O(n).
8. **Write a C program that accepts 10 elements in an array and finds the maximum elements from the array.** *[BBA Assistant Programmer 12.07.2025 compact it 1433 (ET: BUET)]*


   Answer:

   ```c
   #include <stdio.h>
   int main() {
       int a[10], i, max;
       for (i = 0; i < 10; i++) scanf("%d", &a[i]);
       max = a[0];
       for (i = 1; i < 10; i++)
           if (a[i] > max) max = a[i];
       printf("Largest = %d", max);
       return 0;
   }
   ```

   - We take the first element as the largest. Then we compare every other element with it once.
   - Time complexity O(n).
9. **Write a function to find minimum number from an array, return minimum value as argument.** *[Bangladesh Satellite Company Limited Assistant Engineer (CSE) 23.08.2025 compact it 1430 (ET: BUET)]*


   Answer:

   ```c
   #include <stdio.h>
   
   int findMin(int a[], int n) {
       int i, min = a[0];
       for (i = 1; i < n; i++)
           if (a[i] < min) min = a[i];
       return min;
   }
   
   int main() {
       int a[] = {23, 5, 78, 2, 45}, n = 5;
       printf("Minimum = %d", findMin(a, n));
       return 0;
   }
   ```

   - We pass the array and its size to the function. The function returns the smallest value.
   - Time complexity O(n).
10. **Write a C/Java program to check Armstrong number or not.** *[BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)], [BREB Assistant Programmer (AP) 21.02.2025 compact it 1334 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, t, r, sum = 0, d = 0, p;
        scanf("%d", &n);
        t = n;
        while (t > 0) { d++; t /= 10; }
        t = n;
        while (t > 0) {
            r = t % 10;
            p = 1;
            for (int i = 0; i < d; i++) p *= r;
            sum += p;
            t /= 10;
        }
        if (sum == n) printf("Armstrong number");
        else printf("Not an Armstrong number");
        return 0;
    }
    ```

    - An Armstrong number is equal to the sum of its digits, where each digit is raised to the power of the total number of digits.
    - Example: 153 = 1³ + 5³ + 3³.
11. **Write a program from the following series: $e^x = 1 + \frac{x}{1} + \frac{x^2}{2!} + \frac{x^3}{3!} + \dots$** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 316 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i;
        float x, term = 1, sum = 1;
        scanf("%f %d", &x, &n);
        for (i = 1; i <= n; i++) {
            term = term * x / i;
            sum += term;
        }
        printf("e^x = %f", sum);
        return 0;
    }
    ```

    - We get each term from the one before it by multiplying with x/i. So we never have to compute the factorial.
    - This keeps the time complexity at O(n).
12. **Write a C program to find sum of: $X - \frac{X^3}{3!} + \frac{X^5}{5!} - \frac{X^7}{7!} \dots N$** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 397 (ET: BUET)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i;
        float x, term, sum = 0;
        scanf("%f %d", &x, &n);
        term = x;
        sum = x;
        for (i = 1; i < n; i++) {
            term = -term * x * x / ((2*i) * (2*i+1));
            sum += term;
        }
        printf("Sum = %f", sum);
        return 0;
    }
    ```

    - This is the sine series. Each term comes from the one before it.
    - The sign flips every time, because of the minus sign in the multiplier.
13. **Salary Range and Tax Calculation are given:**

| Salary Range | Tax |
|---|---|
| 0-250000 | 0 |
| 250001-5000000 | 10% |
| 500001-100000 | 20% |
| >10,00000 | 30% |

   * **a. Write a program using any language to the calculate the total tax of employee.** *[NWPGCL Assistant Manager (ICT) 12.01.2024 compact it 290 (ET: BUET)]*
   * **b. From the three employee salary find the highest tax paying employee.** *[NWPGCL Assistant Manager (ICT) 12.01.2024 compact it 290 (ET: BUET)]*


    Answer:

    ```c
    #include <stdio.h>
   
    double tax(double s) {
        if (s <= 250000) return 0;
        else if (s <= 500000) return (s - 250000) * 0.10;
        else if (s <= 1000000) return 250000 * 0.10 + (s - 500000) * 0.20;
        else return 250000 * 0.10 + 500000 * 0.20 + (s - 1000000) * 0.30;
    }
   
    int main() {
        double s[3], t[3], maxt;
        int i, idx = 0;
        for (i = 0; i < 3; i++) {
            scanf("%lf", &s[i]);
            t[i] = tax(s[i]);
            printf("Employee %d tax = %.2lf\n", i+1, t[i]);
        }
        maxt = t[0];
        for (i = 1; i < 3; i++)
            if (t[i] > maxt) { maxt = t[i]; idx = i; }
        printf("Highest tax paying employee is %d with tax %.2lf", idx+1, maxt);
        return 0;
    }
    ```

    - Tax is calculated slab by slab, not on the whole salary at one rate.
    - Part b compares the three tax amounts and prints the largest.
14. **Write a C program find prime number 1 to n.** *[NSDA Assistant Maintenance Engineer 11.05.2024 compact it 384 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, j, flag;
        scanf("%d", &n);
        for (i = 2; i <= n; i++) {
            flag = 1;
            for (j = 2; j * j <= i; j++)
                if (i % j == 0) { flag = 0; break; }
            if (flag) printf("%d ", i);
        }
        return 0;
    }
    ```

    - We check divisors only up to the square root. This cuts the work a lot.
    - Time complexity is about O(n√n).
15. **Write a program in any language to find the sum of rows and columns of a m \times n matrix, where m and n is taken input from the user. Give the output in the following format:**
   **Sample Input matrix:**
   **Sample Output:**
   *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 331 (ET: BIBM)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int m, n, i, j, a[20][20], rs, cs;
        scanf("%d %d", &m, &n);
        for (i = 0; i < m; i++)
            for (j = 0; j < n; j++) scanf("%d", &a[i][j]);
        for (i = 0; i < m; i++) {
            rs = 0;
            for (j = 0; j < n; j++) rs += a[i][j];
            printf("Row %d sum = %d\n", i+1, rs);
        }
        for (j = 0; j < n; j++) {
            cs = 0;
            for (i = 0; i < m; i++) cs += a[i][j];
            printf("Column %d sum = %d\n", j+1, cs);
        }
        return 0;
    }
    ```

    - For a row sum we fix the row and move across the columns. For a column sum we do the opposite.
    - Time complexity O(m × n).
16. **Write a program in any language to find the prime numbers between 1.......n, where n is taken as user input.**
   **Sample input:**
   **Enter value of n: 20**
   **Sample Output:**
   **Prime Numbers: 2, 3, 5, 7, 11, 13, 17, 19** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 332 (ET: BIBM)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, j, flag;
        scanf("%d", &n);
        for (i = 2; i <= n; i++) {
            flag = 1;
            for (j = 2; j * j <= i; j++)
                if (i % j == 0) { flag = 0; break; }
            if (flag) printf("%d ", i);
        }
        return 0;
    }
    ```

    - We check divisors only up to the square root. This cuts the work a lot.
    - Time complexity is about O(n√n).
17. **Write a Program Prime number print from 1 to n.** *[Combined Bank Assistant Programmer 09.02.2024 compact it 294 (ET: BIBM)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, j, flag;
        scanf("%d", &n);
        for (i = 2; i <= n; i++) {
            flag = 1;
            for (j = 2; j * j <= i; j++)
                if (i % j == 0) { flag = 0; break; }
            if (flag) printf("%d ", i);
        }
        return 0;
    }
    ```

    - We check divisors only up to the square root. This cuts the work a lot.
    - Time complexity is about O(n√n).
18. **Write a Program Floyds triangle n=5**
```text
1
01
101
0101
10101
```
*[Combined Bank Assistant Programmer 09.02.2024 compact it 295 (ET: BIBM)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n = 5, i, j, num = 1;
        for (i = 1; i <= n; i++) {
            for (j = 1; j <= i; j++)
                printf("%d ", num++);
            printf("\n");
        }
        return 0;
    }
    ```

    - Floyd's triangle prints natural numbers one after another. Row i holds i numbers.
    - Output for n = 5 is 1 / 2 3 / 4 5 6 / 7 8 9 10 / 11 12 13 14 15.
19. **Write a C Program Find sum of the series: 1+2+4+7+11+..........+N** *[Combined Bank Assistant Programmer 09.02.2024 compact it 295 (ET: BIBM)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, term = 1, sum = 0;
        scanf("%d", &n);
        for (i = 1; term <= n; i++) {
            sum += term;
            term = term + i;
        }
        printf("Sum = %d", sum);
        return 0;
    }
    ```

    - The gaps between the terms are 1, 2, 3, 4. So each term is the previous term plus i.
    - Series: 1, 2, 4, 7, 11, 16 and so on.
20. **Write a function which receives an array of integers as parameter and print the numbers divisible by 3 in the array.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 428 (ET: BIBM)]*


    Answer:

    ```c
    #include <stdio.h>
   
    void divBy3(int a[], int n) {
        int i;
        for (i = 0; i < n; i++)
            if (a[i] % 3 == 0) printf("%d ", a[i]);
    }
   
    int main() {
        int a[] = {3, 7, 9, 14, 18, 20}, n = 6;
        divBy3(a, n);
        return 0;
    }
    ```

    - We print only the elements whose remainder on division by 3 is 0.
    - Time complexity O(n).
21. **Write a C program: ax^2+bx+c=0** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 390 (ET: BUET)]*


    Answer:

    ```c
    #include <stdio.h>
    #include <math.h>
    int main() {
        float a, b, c, d, r1, r2;
        scanf("%f %f %f", &a, &b, &c);
        d = b*b - 4*a*c;
        if (d > 0) {
            r1 = (-b + sqrt(d)) / (2*a);
            r2 = (-b - sqrt(d)) / (2*a);
            printf("Real and distinct roots: %.2f, %.2f", r1, r2);
        } else if (d == 0) {
            printf("Equal roots: %.2f", -b / (2*a));
        } else {
            printf("Roots are imaginary");
        }
        return 0;
    }
    ```

    - The discriminant d = b² − 4ac decides the nature of the roots.
    - d > 0 gives two real roots, d = 0 gives one repeated root and d < 0 gives complex roots.
22. **Write a program that take a number as input and output should be sum of digits of that number using python/C also draw its flow chart.** *[BKSP Assistant Programmer 13.07.2024 compact it 1457 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, sum = 0;
        scanf("%d", &n);
        while (n > 0) {
            sum += n % 10;
            n /= 10;
        }
        printf("Sum of digits = %d", sum);
        return 0;
    }
    ```

    - We take the last digit with n % 10 and remove it with n / 10. We repeat until n becomes 0.
    - For 1234 the answer is 1 + 2 + 3 + 4 = 10.
23. **Find the output from the following: take input and looks the output:**
   **Suppose Input: 6789; Output: 9876** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 379 (ET: BUET)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, rev = 0;
        scanf("%d", &n);
        while (n > 0) {
            rev = rev * 10 + n % 10;
            n /= 10;
        }
        printf("%d", rev);
        return 0;
    }
    ```

    - We multiply the reversed number by 10 and then add the new digit to it.
    - Input 6789 gives output 9876.
24. **(b) Print the output:** *[Bangladesh Submarine Cables PLC (BSCPLC) Assistant Manager (Engineering) 13.12.2024 compact it 433 (ET: BUET)]*
```c
#include<stdio.h>
int main() {
    int a[] = {0,1,2,3,4};
    int b[] = {10,20,30,40,50};
    printf("%d", b[a[2]]);
    return 0;
}
```


    Answer: Output is 30.

    - `a[2]` is 2, so the expression becomes `b[2]`.
    - `b[2]` is 30, so 30 is printed.
    - This is array indexing used inside another array index, which is legal in C.
25. **Given a code with a variable value "a=85" and finds its output a=85**
```c
if a>=90 point A;
if a>=80 point B;
if a>=70 point C;
if a>=60 point D;
else print F;
```
*[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1454 (ET: BUET)]*


    Answer: Output is B C D.

    - The four conditions are separate `if` statements, not `else if`. So each one is checked on its own.
    - a = 85, so `a >= 90` is false and nothing prints.
    - `a >= 80` is true, so B prints. `a >= 70` is true, so C prints. `a >= 60` is true, so D prints.
    - The `else` belongs only to the last `if`. That condition was true, so F never prints.
    - If `else if` had been used, only B would print. This is the trap the question is testing.
26. **(ক) C ভাষায় ব্যবহৃত বিভিন্ন ধরনের Data Type বর্ণনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 407 (ET: N/A)]*


    Answer: C supports the following data types.

    Primary or basic types:
    - `int` — stores whole numbers, normally 4 bytes, format specifier `%d`.
    - `float` — single precision decimal, 4 bytes, `%f`.
    - `double` — double precision decimal, 8 bytes, `%lf`.
    - `char` — a single character, 1 byte, `%c`.
    - `void` — means no value. We use it for functions that return nothing.

    Derived types:
    - Array — a collection of same type elements, for example `int a[10]`.
    - Pointer — holds a memory address, for example `int *p`.
    - Function — returns a value of a declared type.

    User defined types:
    - `struct` — groups variables of different types under one name.
    - `union` — like struct but all members share the same memory.
    - `enum` — a set of named integer constants.
    - `typedef` — gives a new name to an existing type.

    Type modifiers: `short`, `long`, `signed` and `unsigned` change the range or size of the basic types.
27. **(খ) একটি ধনাত্মক পূর্ণ সংখ্যার Factorial নির্ণয়ের C program লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i;
        long long f = 1;
        scanf("%d", &n);
        for (i = 1; i <= n; i++)
            f *= i;
        printf("Factorial = %lld", f);
        return 0;
    }
    ```

    - `long long` is used because factorial values grow very fast.
    - Factorial of 0 is 1. The loop never runs in that case, so the answer stays 1, which is correct.
28. **Write a program swap two numbers without using 3rd variable.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 501 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int a, b;
        scanf("%d %d", &a, &b);
        a = a + b;
        b = a - b;
        a = a - b;
        printf("a = %d, b = %d", a, b);
        return 0;
    }
    ```

    - The arithmetic method swaps without a third variable.
    - The XOR method `a^=b; b^=a; a^=b;` also works and avoids overflow.
29. **Find the output from this code-** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 590 (ET: BUET)]*
```c
#include <stdio.h>
void PrintArray(int num[], int n) {
    int i;
    for(i=0;i<n;i++)
    {
        printf("%d", num[i]);
    }
    printf("\n");
}
void FunctionArray(int num[], int n) {
    int i, j, key;
    for (i=1;i<n;i++)
    {
        key=num[i];
        j--;
        while(j>=0 && j<=n){
            num[j] = num[j+1];
            key=num[j];
        }
        num[i-1]=key;
        PrintArray(num,n);
    }}
int main() {
    int num[]={11,2,3,4,5};
    PrintArray(num,5);
    FunctionArray(num,5);
    return 0;
}
```


    Answer: The first line printed is 112345, after which the program shows undefined behaviour.

    - `PrintArray(num,5)` in main prints the array as 112345.
    - Inside `FunctionArray`, the variable `j` is declared but never given a value. The first thing done to it is `j--`. Using an uninitialised variable is undefined behaviour in C.
    - The loop `while (j >= 0 && j <= n)` never changes `j` inside the body. So if it starts at all, it runs forever. It also writes outside the array through `num[j] = num[j+1]`.
    - So the program prints 112345 and then either hangs or crashes. It depends on the compiler and on the garbage value in `j`.
    - The code was meant to be insertion sort. There `j` should start as `j = i - 1` and go down inside the loop.
30. **Write a program for following sequence and analyze complexity of the program** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 522 (ET: MIST)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, sum = 0;
        scanf("%d", &n);
        for (i = 1; i <= n; i++)
            sum += i * i;
        printf("Sum = %d", sum);
        return 0;
    }
    ```

    - The loop runs n times. Each turn does a fixed amount of work. So the time complexity is O(n).
    - Only a few variables are used, so the space complexity is O(1).
    - We can get the same result in O(1) using the formula n(n+1)(2n+1)/6.
31. **Write a C/C++ program to count the prime number up to N.** *[Sheikh Kamal IT Training & Incubation Center Assistant Programmer/Instructor 04.08.2023 compact it 599 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, j, flag, count = 0;
        scanf("%d", &n);
        for (i = 2; i <= n; i++) {
            flag = 1;
            for (j = 2; j * j <= i; j++)
                if (i % j == 0) { flag = 0; break; }
            if (flag) count++;
        }
        printf("Total prime numbers = %d", count);
        return 0;
    }
    ```

    - Here we count the primes instead of printing them.
    - The Sieve of Eratosthenes would be faster at O(n log log n) for large n.
32. **Write a C/C++ program for check out a leap year program.** *[Sheikh Kamal IT Training & Incubation Center Assistant Programmer/Instructor 04.08.2023 compact it 599 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int y;
        scanf("%d", &y);
        if ((y % 4 == 0 && y % 100 != 0) || y % 400 == 0)
            printf("Leap year");
        else
            printf("Not a leap year");
        return 0;
    }
    ```

    - A year is a leap year if it is divisible by 4 but not by 100, or if it is divisible by 400.
    - So 2000 is a leap year but 1900 is not.
33. **Write a Program:** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 506 (ET: N/A)]*
   a) **Sample Output:**
   ```text
   1
   1 2
   1 2 3
   ```
   b) **Sample Output:**
   ```text
   Start
   Start
   Start
   Start
   ```


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int i, j;
        /* a) triangle pattern */
        for (i = 1; i <= 3; i++) {
            for (j = 1; j <= i; j++)
                printf("%d ", j);
            printf("\n");
        }
        /* b) print Start four times */
        for (i = 0; i < 4; i++)
            printf("Start\n");
        return 0;
    }
    ```

    - Part a uses a nested loop where the inner loop prints 1 to i on row i.
    - Part b is a simple loop that repeats the same text four times.
34. **Find the output of the following program including time and space complexity.** *[Rupali Bank Ltd. Assistant Network Engineer 04.11.2023 compact it 542 (ET: MIST)]*
```cpp
#include<iostream>
int main(){
int n;
std::cout <<"Enter the number of terms for the fibonacci series: ";
std::cin >> n;
int first = 0, second =1;
if (n>=1){
std::cout <<"Fibonacci Series:"<< first;
if(n>=2){
std::cout<< second;
}
for(int i=2;i<n ;i++){
int next = first + second;
std::cout<<","<<next;
first = second;
second = next;
}
}
std::cout<<std::endl;
return 0;
}
```


    Answer: The program prints the Fibonacci series for the entered number of terms.

    For an input of n = 5 the output is:
    `Fibonacci Series:01,1,2,3`

    - `first = 0` is printed with no separator. Then `second = 1` is also printed with no separator. That is why the first two values look joined, as 01.
    - From i = 2 onward each new term is printed after a comma, so the remaining output is ,1 then ,2 then ,3.
    - Time complexity: O(n), because the loop runs n − 2 times and each iteration does constant work.
    - Space complexity: O(1). We store only first, second and next, whatever n is.
35. **Write a program find prime number between 1 to 100?** *[NPCBL Executive Trainee (Software) 26.05.2023 compact it 499 (ET: IBA)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int i, j, flag;
        for (i = 2; i <= 100; i++) {
            flag = 1;
            for (j = 2; j * j <= i; j++)
                if (i % j == 0) { flag = 0; break; }
            if (flag) printf("%d ", i);
        }
        return 0;
    }
    ```

    - There are 25 prime numbers between 1 and 100.
    - 1 is not prime, so the loop starts from 2.
36. **Write a C program sum of 1 to 100.** *[Mongla Port Authority Assistant Programmer 2023 compact it 571 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int i, sum = 0;
        for (i = 1; i <= 100; i++)
            sum += i;
        printf("Sum = %d", sum);
        return 0;
    }
    ```

    - The output is 5050.
    - We can get the same value directly from n(n+1)/2 = 100 × 101 / 2.
37. **Write a Program:** *[DESCO Assistant Engineer 20.05.2023 compact it 579 (ET: DESCO)]*
   **a) Sample Output:**
   ```text
   1
   1 2
   1 2 3
   1 2 3 4
   ```
   **b) Write a C or C++ Program to print an array of five fruits.**


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int i, j;
        /* a) triangle pattern */
        for (i = 1; i <= 4; i++) {
            for (j = 1; j <= i; j++)
                printf("%d ", j);
            printf("\n");
        }
        /* b) print an array of five fruits */
        char *fruits[5] = {"Mango", "Banana", "Apple", "Jackfruit", "Guava"};
        for (i = 0; i < 5; i++)
            printf("%s\n", fruits[i]);
        return 0;
    }
    ```

    - Part a prints 1 to i on row i for four rows.
    - Part b uses an array of character pointers to hold the five names.
38. **Write a program in any language that takes two matrices A and B as inputs ensure your code handles matrices of different dimensions—**
   **A) Find matrices C that is multiplication A and B.**
   **B) Find average in A and B.**
   **C) Max from matrices C** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 515 (ET: MIST)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int r1, c1, r2, c2, i, j, k;
        int a[10][10], b[10][10], c[10][10];
        scanf("%d %d", &r1, &c1);
        scanf("%d %d", &r2, &c2);
        if (c1 != r2) {
            printf("Multiplication not possible");
            return 0;
        }
        for (i = 0; i < r1; i++) for (j = 0; j < c1; j++) scanf("%d", &a[i][j]);
        for (i = 0; i < r2; i++) for (j = 0; j < c2; j++) scanf("%d", &b[i][j]);
        for (i = 0; i < r1; i++)
            for (j = 0; j < c2; j++) {
                c[i][j] = 0;
                for (k = 0; k < c1; k++)
                    c[i][j] += a[i][k] * b[k][j];
            }
        for (i = 0; i < r1; i++) {
            for (j = 0; j < c2; j++) printf("%d ", c[i][j]);
            printf("\n");
        }
        return 0;
    }
    ```

    - Multiplication is possible only when the column count of A equals the row count of B.
    - The result has dimension r1 × c2 and the time complexity is O(r1 × c1 × c2).
39. **Write a function to find the smallest element from an array.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 492 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
   
    int findMin(int a[], int n) {
        int i, min = a[0];
        for (i = 1; i < n; i++)
            if (a[i] < min) min = a[i];
        return min;
    }
   
    int main() {
        int a[] = {23, 5, 78, 2, 45}, n = 5;
        printf("Minimum = %d", findMin(a, n));
        return 0;
    }
    ```

    - We pass the array and its size to the function. The function returns the smallest value.
    - Time complexity O(n).
40. **Suppose you have an array. The array contains elements from 0 to 10. This array also contains 0. To replace these 0s, write a program in C/C++ language.** *[BTCL Assistant Manager (Technical) 2023 compact it 593 (ET: BUET)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int a[100], n, i, j = 0;
        scanf("%d", &n);
        for (i = 0; i < n; i++) scanf("%d", &a[i]);
        for (i = 0; i < n; i++)
            if (a[i] != 0) a[j++] = a[i];
        while (j < n) a[j++] = 0;
        for (i = 0; i < n; i++) printf("%d ", a[i]);
        return 0;
    }
    ```

    - We move all non-zero elements to the front, keeping their order. Then we fill the rest of the array with zeros.
    - Time complexity O(n) and space complexity O(1).
41. **Write a function int equilibrium (int[] arr, int n); that given a sequence arr[] of size n, returns an equilibrium index (if any) or -1 if no equilibrium indexes exist. The equilibrium index of an array is an index such that the sum of elements at lower indexes is equal to the sum of elements at higher indexes. Foe example:** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 455 (ET: BUET)]*
   **Input: A[] = {-7, 1, 5, 2, -4, 3, 0}**
   **Output: 3**
   **3 is an equilibrium index, because: A[0] + A[1] + A[2] = A[4] + A[5] + A[6]**
   **Input: A[] = {1, 2, 3}**
   **Output: -1**


    Answer:

    ```c
    #include <stdio.h>
   
    int equilibrium(int arr[], int n) {
        int total = 0, left = 0, i;
        for (i = 0; i < n; i++) total += arr[i];
        for (i = 0; i < n; i++) {
            total -= arr[i];
            if (left == total) return i;
            left += arr[i];
        }
        return -1;
    }
   
    int main() {
        int a[] = {-7, 1, 5, 2, -4, 3, 0}, n = 7;
        printf("Equilibrium index = %d", equilibrium(a, n));
        return 0;
    }
    ```

    - At an equilibrium index the sum of elements on the left equals the sum on the right.
    - We keep a running total, so we do not add up the right side again and again. That makes it O(n).
42. **Write a C program to print the following pattern:**
```text
0
010
01010

```
*[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 457 (ET: BUET)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n = 3, i, j;
        for (i = 1; i <= n; i++) {
            for (j = 1; j <= 2*i - 1; j++)
                printf("%d", j % 2 == 1 ? 0 : 1);
            printf("\n");
        }
        return 0;
    }
    ```

    - Row i has 2i − 1 characters. They alternate between 0 and 1, and always start with 0.
    - This gives 0 then 010 then 01010.
43. **Write a C code that show factorial of a number.** *[BITAC Assistant Programmer 27.10.2023 compact it 561 (ET: BUTEX)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i;
        long long f = 1;
        scanf("%d", &n);
        for (i = 1; i <= n; i++)
            f *= i;
        printf("Factorial = %lld", f);
        return 0;
    }
    ```

    - `long long` is used because factorial values grow very fast.
    - Factorial of 0 is 1. The loop never runs in that case, so the answer stays 1, which is correct.
44. **Write a C Program to delete duplicate element from array.** *[BEPZA Programmer 03.11.2023 compact it 561 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int a[100], n, i, j, k;
        scanf("%d", &n);
        for (i = 0; i < n; i++) scanf("%d", &a[i]);
        for (i = 0; i < n; i++)
            for (j = i + 1; j < n; j++)
                if (a[i] == a[j]) {
                    for (k = j; k < n - 1; k++) a[k] = a[k+1];
                    n--;
                    j--;
                }
        for (i = 0; i < n; i++) printf("%d ", a[i]);
        return 0;
    }
    ```

    - We compare every element with the ones after it. When we find a duplicate, we remove it by shifting the rest to the left.
    - Time complexity O(n²). Sorting first would allow an O(n log n) solution.
45. **Given two integers A and B as input write a program to compute the least common multiple of A and B.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 436 (ET: BIBM)]*


    Answer:

    ```c
    #include <stdio.h>
   
    int gcd(int a, int b) {
        while (b != 0) {
            int t = b;
            b = a % b;
            a = t;
        }
        return a;
    }
   
    int main() {
        int a, b;
        scanf("%d %d", &a, &b);
        printf("LCM = %d", (a / gcd(a, b)) * b);
        return 0;
    }
    ```

    - We get the LCM from the formula LCM(a,b) = (a × b) / GCD(a,b).
    - Dividing before multiplying avoids overflow.
    - The Euclidean algorithm finds the GCD in O(log min(a,b)).
46. **(খ) এমন একটি C program লিখুন যা একটি array তৈরি করে কতগুলো ডেটা রাখবে, তারপর ফলাফল হিসেবে ডেটাগুলোকে বিপরীত দিক থেকে print করবে।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 600 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int a[100], n, i;
        scanf("%d", &n);
        for (i = 0; i < n; i++) scanf("%d", &a[i]);
        printf("Reverse order: ");
        for (i = n - 1; i >= 0; i--)
            printf("%d ", a[i]);
        return 0;
    }
    ```

    - We just walk the array from the last index down to the first.
    - Time complexity O(n).
47. **(খ) প্রথম দশটি Fibonacci number প্রদর্শনের জন্য একটি C program লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 601 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int i, a = 0, b = 1, next;
        printf("%d %d ", a, b);
        for (i = 3; i <= 10; i++) {
            next = a + b;
            printf("%d ", next);
            a = b;
            b = next;
        }
        return 0;
    }
    ```

    - Output: 0 1 1 2 3 5 8 13 21 34
    - Each term is the sum of the previous two terms.
48. **Write a C program: x - \frac{x^3}{3} + \frac{x^5}{5} - \dots** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 650 (ET: BUET)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, sign = 1;
        float x, term, sum = 0, p;
        scanf("%f %d", &x, &n);
        for (i = 1; i <= n; i++) {
            p = 1;
            for (int k = 0; k < 2*i - 1; k++) p *= x;
            term = p / (2*i - 1);
            sum += sign * term;
            sign = -sign;
        }
        printf("Sum = %f", sum);
        return 0;
    }
    ```

    - The powers are odd numbers 1, 3, 5 and the divisors are the same odd numbers.
    - The sign alternates between + and −.
49. **C program to find sum of odd numbers from 1 to n.** *[NSDA Assistant Programmer Date: 04-03-2022 compact it 656 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, sum = 0;
        scanf("%d", &n);
        for (i = 1; i <= n; i += 2)
            sum += i;
        printf("Sum of odd numbers = %d", sum);
        return 0;
    }
    ```

    - Starting at 1 and stepping by 2 covers only odd numbers.
    - The sum of the first k odd numbers is always k².
50. **Determine whwther a given number is prime or not?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 682 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, flag = 1;
        scanf("%d", &n);
        if (n < 2) flag = 0;
        for (i = 2; i * i <= n; i++)
            if (n % i == 0) { flag = 0; break; }
        printf(flag ? "Prime" : "Not prime");
        return 0;
    }
    ```

    - We check divisors only up to √n. Any larger factor must have a smaller partner, which we have already checked.
    - Time complexity O(√n).
51. **Find the most significant number in an array of N elements.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 683 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int a[10], i, max;
        for (i = 0; i < 10; i++) scanf("%d", &a[i]);
        max = a[0];
        for (i = 1; i < 10; i++)
            if (a[i] > max) max = a[i];
        printf("Largest = %d", max);
        return 0;
    }
    ```

    - We take the first element as the largest. Then we compare every other element with it once.
    - Time complexity O(n).
52. **Determine even or odd numbers.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 684 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n;
        scanf("%d", &n);
        if (n % 2 == 0) printf("Even");
        else printf("Odd");
        return 0;
    }
    ```

    - If the remainder after dividing by 2 is 0, the number is even. Otherwise it is odd.
    - Time complexity O(1).
53. **Print the following matrix using for loop.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 682 (ET: N/A)]*
```text
1
22
333
4444
55555
```


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int i, j;
        for (i = 1; i <= 5; i++) {
            for (j = 1; j <= i; j++)
                printf("%d", i);
            printf("\n");
        }
        return 0;
    }
    ```

    - Row i prints the digit i exactly i times.
    - This produces 1 / 22 / 333 / 4444 / 55555.
54. **ইউজার হতে 10 টি integer data input করে যে data গুলো 5 দ্বারা বিভাজ্য তাদের গড় মান নির্ণয় এর একটি program লিখুন।** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 698 (ET: DPI)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int a[10], i, count = 0, sum = 0;
        for (i = 0; i < 10; i++) {
            scanf("%d", &a[i]);
            if (a[i] % 5 == 0) { sum += a[i]; count++; }
        }
        if (count > 0)
            printf("Average = %.2f", (float)sum / count);
        else
            printf("No number divisible by 5");
        return 0;
    }
    ```

    - Only the numbers divisible by 5 are summed and counted.
    - The count is checked before dividing so that division by zero is avoided.
55. **Write a function in C/C++ that return kth largest number of an array. The function has three parameters array_name, size, k.** *[EGCB Assistant Engineer (CSE) 2022 compact it 714 (ET: BUET)]*


    Answer:

    ```c
    #include <stdio.h>
   
    int kthLargest(int a[], int n, int k) {
        int i, j, t;
        for (i = 0; i < n - 1; i++)
            for (j = 0; j < n - 1 - i; j++)
                if (a[j] < a[j+1]) { t = a[j]; a[j] = a[j+1]; a[j+1] = t; }
        return a[k-1];
    }
   
    int main() {
        int a[] = {12, 3, 45, 7, 19}, n = 5, k = 2;
        printf("%d largest = %d", k, kthLargest(a, n, k));
        return 0;
    }
    ```

    - The array is sorted in descending order, so the kth largest sits at index k − 1.
    - Sorting costs O(n²) here. A max-heap would give O(n + k log n).
56. **Write a C/C++ program to find out the prime from 1 to N.** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 718 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, j, flag;
        scanf("%d", &n);
        for (i = 2; i <= n; i++) {
            flag = 1;
            for (j = 2; j * j <= i; j++)
                if (i % j == 0) { flag = 0; break; }
            if (flag) printf("%d ", i);
        }
        return 0;
    }
    ```

    - We check divisors only up to the square root. This cuts the work a lot.
    - Time complexity is about O(n√n).
57. **Write a C/C++ program to find the reverse number of a number.** *[CAAB Programmer 2022 compact it 721 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, rev = 0;
        scanf("%d", &n);
        while (n > 0) {
            rev = rev * 10 + n % 10;
            n /= 10;
        }
        printf("%d", rev);
        return 0;
    }
    ```

    - We multiply the reversed number by 10 and then add the new digit to it.
    - Input 6789 gives output 9876.
58. **Write a C/C++ program to find the HCF.** *[CAAB Programmer 2022 compact it 721 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int a, b, t;
        scanf("%d %d", &a, &b);
        while (b != 0) {
            t = b;
            b = a % b;
            a = t;
        }
        printf("HCF = %d", a);
        return 0;
    }
    ```

    - This is the Euclidean algorithm. We keep replacing the larger number with the remainder.
    - Time complexity O(log min(a,b)).
59. **Write a C/C++ program to find the sum of digits.** *[CAAB Assistant Programmer (AP) 2022 compact it 725 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, sum = 0;
        scanf("%d", &n);
        while (n > 0) {
            sum += n % 10;
            n /= 10;
        }
        printf("Sum of digits = %d", sum);
        return 0;
    }
    ```

    - We take the last digit with n % 10 and remove it with n / 10. We repeat until n becomes 0.
    - For 1234 the answer is 1 + 2 + 3 + 4 = 10.
60. **Write a program to find this is Leap year or not, using function.** *[BKSP Assistant Programmer 03.12.2022 compact it 729 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
   
    int isLeap(int y) {
        return (y % 4 == 0 && y % 100 != 0) || (y % 400 == 0);
    }
   
    int main() {
        int y;
        scanf("%d", &y);
        if (isLeap(y)) printf("Leap year");
        else printf("Not a leap year");
        return 0;
    }
    ```

    - We put the check in a separate function. It returns 1 for a leap year and 0 otherwise.
    - Using a function keeps main clean and makes the logic reusable.
61. **Write a C program using array, here N is the number of total students. Take the input and find the average marks. Find out the students who got the above marks or low marks according to average marks.** *[BOF Assistant Programmer 2022 compact it 732 (ET: MIST)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i;
        float m[100], sum = 0;
        scanf("%d", &n);
        for (i = 0; i < n; i++) {
            scanf("%f", &m[i]);
            sum += m[i];
        }
        printf("Average marks = %.2f", sum / n);
        return 0;
    }
    ```

    - We read all the marks into an array, add them up, and then divide by the number of students.
    - Time complexity O(n).
62. **Write down a function int reverse (int n) that takes a positive integer as input parameter and returns the reverse of the given integer. For example, if input integer N=2579, then reversed output is= 9752** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 748 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
   
    int reverse(int n) {
        int rev = 0;
        while (n > 0) {
            rev = rev * 10 + n % 10;
            n /= 10;
        }
        return rev;
    }
   
    int main() {
        printf("%d", reverse(12345));
        return 0;
    }
    ```

    - The function returns 54321 for the input 12345.
    - Time complexity O(number of digits), that is O(log n).
63. **Consider int num[20][4] holds the marks of four class test(CT) of a class of 20 students. Write a program to find out the sum of best three CT marks for each student.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 748 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int num[20][4], i, j, total;
        float avg;
        for (i = 0; i < 20; i++)
            for (j = 0; j < 4; j++)
                scanf("%d", &num[i][j]);
        for (i = 0; i < 20; i++) {
            total = 0;
            for (j = 0; j < 4; j++) total += num[i][j];
            avg = total / 4.0;
            printf("Student %d: total = %d, average = %.2f\n", i+1, total, avg);
        }
        return 0;
    }
    ```

    - Each row holds the four class test marks of one student.
    - We fix the row and loop over the columns. That gives the total of that student.
64. **(ক) নিচের সিরিজ টি ক্যালকুলেটর এবং প্রিন্ট করার জন্য একটি C Program লিখুন। 1 + 2 + 3 + \dots + 100** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 776 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int i, sum = 0;
        for (i = 1; i <= 100; i++)
            sum += i;
        printf("Sum = %d", sum);
        return 0;
    }
    ```

    - The output is 5050.
    - We can get the same value directly from n(n+1)/2 = 100 × 101 / 2.
65. **(খ) তোমার ক্লাসের ছাত্রদের তালিকা Sort করার জন্য একটি C Program লিখ।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 776 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    #include <string.h>
    int main() {
        char name[50][30], temp[30];
        int n, i, j;
        scanf("%d", &n);
        for (i = 0; i < n; i++) scanf("%s", name[i]);
        for (i = 0; i < n - 1; i++)
            for (j = 0; j < n - 1 - i; j++)
                if (strcmp(name[j], name[j+1]) > 0) {
                    strcpy(temp, name[j]);
                    strcpy(name[j], name[j+1]);
                    strcpy(name[j+1], temp);
                }
        for (i = 0; i < n; i++) printf("%s\n", name[i]);
        return 0;
    }
    ```

    - `strcmp` compares two strings alphabetically and `strcpy` swaps them.
    - Bubble sort is used here, so the time complexity is O(n²).
66. **(b) Write a program in C/C++/Java to identify the largest number of given 3 numbers.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 791 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int a, b, c, max;
        scanf("%d %d %d", &a, &b, &c);
        max = a;
        if (b > max) max = b;
        if (c > max) max = c;
        printf("Largest = %d", max);
        return 0;
    }
    ```

    - We take the first number as the largest, then compare it with the others.
    - Only two comparisons are needed.
67. **(b) Write down a program in C language that will find the maximum of four integer gives as inputs.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 804 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int a[4], i, max;
        for (i = 0; i < 4; i++) scanf("%d", &a[i]);
        max = a[0];
        for (i = 1; i < 4; i++)
            if (a[i] > max) max = a[i];
        printf("Maximum = %d", max);
        return 0;
    }
    ```

    - Using an array keeps the code short and easy to extend to more numbers.
    - Three comparisons are needed for four numbers.
68. **We are given an array of integers and a range, we need to find whether the subarray which falls in this range has values in the form of a mountain or not. All values of the subarray are said to be in the form of a mountain if either all values are increasing or decreasing or first increasing and then decreasing. Write a C/C++ Program that shows input is a Mountain sequence or Not Mountain sequence.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 833 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
   
    int isMountain(int a[], int l, int r) {
        int i = l;
        while (i < r && a[i] < a[i+1]) i++;
        if (i == l || i == r) return 0;
        while (i < r && a[i] > a[i+1]) i++;
        return i == r;
    }
   
    int main() {
        int a[] = {2, 3, 8, 6, 4, 1}, l = 0, r = 5;
        printf(isMountain(a, l, r) ? "Mountain" : "Not a mountain");
        return 0;
    }
    ```

    - A mountain subarray must strictly increase, reach one peak and then strictly decrease.
    - The peak cannot be the first or the last element. That is why we reject both those cases.
    - Time complexity O(n).
69. **Write a programme in C/C++/Java what finds sum of digits of a number until sum becomes single digit, simple input/output is: Input: 12345 Output: 6** *[RAKUB Programmer (PO) 12.10.2021 compact it 844 (ET: N/A)], [Sonali Bank Ltd. Officer IT 2021 compact it 908 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, sum;
        scanf("%d", &n);
        while (n > 9) {
            sum = 0;
            while (n > 0) { sum += n % 10; n /= 10; }
            n = sum;
        }
        printf("Digital root = %d", n);
        return 0;
    }
    ```

    - We add the digits again and again, until only one digit is left.
    - Example: 9875 → 29 → 11 → 2.
70. **Pattern this print using C++ program-** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 862 (ET: BUET)]*
```text
1 2 3 4 5
1 2 3 4
1 2 3
1 2
1
```


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n = 5, i, j;
        for (i = n; i >= 1; i--) {
            for (j = 1; j <= i; j++)
                printf("%d ", j);
            printf("\n");
        }
        return 0;
    }
    ```

    - The outer loop counts down from 5 to 1. So each row has one number less than the row above.
    - The inner loop always prints from 1 up to the current row length.
71. **(a) Write down a function in C Programming language, that will take an n\times n matrix as parameter and the dimension n as another parameter, then compute the sum of main diagonal elements of the matrix.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 884 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
   
    int isSymmetric(int a[10][10], int n) {
        int i, j;
        for (i = 0; i < n; i++)
            for (j = 0; j < n; j++)
                if (a[i][j] != a[j][i]) return 0;
        return 1;
    }
   
    int main() {
        int a[10][10] = {{1,2,3},{2,5,6},{3,6,9}}, n = 3;
        printf(isSymmetric(a, n) ? "Symmetric" : "Not symmetric");
        return 0;
    }
    ```

    - A matrix is symmetric when a[i][j] equals a[j][i] for every pair of indices.
    - Time complexity O(n²). Checking only the upper triangle would halve the comparisons.
72. **(b) Write down a program to find sum of diagonal elements of a two dimensional matrix.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 895 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int a[10][10], n, i, j, d1 = 0, d2 = 0;
        scanf("%d", &n);
        for (i = 0; i < n; i++)
            for (j = 0; j < n; j++) scanf("%d", &a[i][j]);
        for (i = 0; i < n; i++) {
            d1 += a[i][i];
            d2 += a[i][n-1-i];
        }
        printf("Main diagonal sum = %d\n", d1);
        printf("Secondary diagonal sum = %d", d2);
        return 0;
    }
    ```

    - Main diagonal elements have row index equal to column index.
    - Secondary diagonal elements satisfy j = n − 1 − i.
    - Only one loop is needed, so the time complexity is O(n).
73. **(i) Write a C/C++ program up to series n: \frac{1}{2\times 3} + \frac{2}{3\times 4} + \frac{3}{4\times 5} \dots\dots\dots\dots\dots** *[NESCO Assistant Manager (ICT) 2021 compact it 907 (ET: BUET)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i;
        float sum = 0;
        scanf("%d", &n);
        for (i = 1; i <= n; i++)
            sum += (float)i / ((i+1) * (i+2));
        printf("Sum = %f", sum);
        return 0;
    }
    ```

    - The general term is i / ((i+1)(i+2)).
    - We cast to float. Without it, integer division would cut off the decimal part.
74. **Write a C program to compute the perimeter and area of a circle with a given radius.** *[Sonali Bank Ltd. Officer IT 2021 compact it 909-910 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    #define PI 3.14159
    int main() {
        float r;
        scanf("%f", &r);
        printf("Perimeter = %.2f\n", 2 * PI * r);
        printf("Area = %.2f", PI * r * r);
        return 0;
    }
    ```

    - Perimeter of a circle is 2πr and area is πr².
    - PI is defined as a macro so the value is written only once.
75. **A হলো মিটার নং, B হলো ব্যবহৃত ইউনিট। 300 ইউনিটের বেশী তাদের মিটার নং এবং ইউনিটের যোগফল বের কর।** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 912 (ET: BUET)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, meter, unit;
        scanf("%d", &n);
        for (i = 0; i < n; i++) {
            scanf("%d %d", &meter, &unit);
            if (unit > 300)
                printf("Meter %d, sum = %d\n", meter, meter + unit);
        }
        return 0;
    }
    ```

    - We look only at the records where the unit consumption is more than 300.
    - For those the meter number and the unit are added and printed.
76. **Write the code for second highest maximum from given three number in c/c++.** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 920-921 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int a, b, c, second;
        scanf("%d %d %d", &a, &b, &c);
        if ((a >= b && a <= c) || (a <= b && a >= c)) second = a;
        else if ((b >= a && b <= c) || (b <= a && b >= c)) second = b;
        else second = c;
        printf("Second largest = %d", second);
        return 0;
    }
    ```

    - The second largest number is the one that lies between the other two.
    - Only comparisons are used, so the complexity is O(1).
77. **Write a simple output C program to check odd-even number.** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 932 (ET: BUET)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n;
        scanf("%d", &n);
        if (n % 2 == 0) printf("Even");
        else printf("Odd");
        return 0;
    }
    ```

    - If the remainder after dividing by 2 is 0, the number is even. Otherwise it is odd.
    - Time complexity O(1).
78. **Write a C program for prime numbers between 1 to N.** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 932 (ET: BUET)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, j, flag;
        scanf("%d", &n);
        for (i = 2; i <= n; i++) {
            flag = 1;
            for (j = 2; j * j <= i; j++)
                if (i % j == 0) { flag = 0; break; }
            if (flag) printf("%d ", i);
        }
        return 0;
    }
    ```

    - We check divisors only up to the square root. This cuts the work a lot.
    - Time complexity is about O(n√n).
79. **Write a program for the following series: 1^2+2^2+3^2+4^2+\dots\dots\dots\dots+N^2** *[BREB Junior Assistant Manager (ICT) 2021 compact it 948 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, sum = 0;
        scanf("%d", &n);
        for (i = 1; i <= n; i++)
            sum += i * i;
        printf("Sum = %d", sum);
        return 0;
    }
    ```

    - The loop runs n times. Each turn does a fixed amount of work. So the time complexity is O(n).
    - Only a few variables are used, so the space complexity is O(1).
    - We can get the same result in O(1) using the formula n(n+1)(2n+1)/6.
80. **(i) Formatted Input/Output Statement কাকে বলে? Key-Board থেকে কিভাবে input নেয়া যায়? %d এর অর্থ কী?** *[BPSC Assistant Network Engineer 2020 compact it 954-955 (ET: N/A)]*


    Answer:

    Formatted input/output statement:
    - These statements read or write data in a fixed format, using format specifiers.
    - `scanf()` is the formatted input function and `printf()` is the formatted output function.
    - They are declared in the header file `stdio.h`.

    Taking input from the keyboard:
    - `scanf("%d", &n);` reads an integer typed on the keyboard into the variable n.
    - The format string says what type of data to expect. The `&` operator gives the address of the variable where the value will be stored.
    - For a string read with `%s` we do not need `&`, because an array name already gives the address.

    Meaning of `%d`:
    - `%d` is the format specifier for a signed decimal integer.
    - In `scanf` it means read an integer, and in `printf` it means print the value as an integer.
    - Other common specifiers are `%f` for float, `%lf` for double, `%c` for character and `%s` for string.
81. **(ii) if......else statement এর format লিখ। 1+3+5+7+\dots+n সিরিজটির যোগফল নির্ণয়ের জন্য C-language এ একটি প্রোগ্রাম লিখ।** *[BPSC Assistant Network Engineer 2020 compact it 955 (ET: N/A)]*


    Answer:

    Format of the if...else statement:

    ```c
    if (condition) {
        statements executed when the condition is true;
    } else {
        statements executed when the condition is false;
    }
    ```

    - The condition must produce a true or false value.
    - The else part is optional. We can chain `else if` for more conditions.

    Program for the series 1 + 3 + 5 + 7 + ... + n:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, sum = 0;
        scanf("%d", &n);
        for (i = 1; i <= n; i += 2)
            sum += i;
        printf("Sum = %d", sum);
        return 0;
    }
    ```

    - The loop steps by 2, so only odd numbers are added.
    - The sum of the first k odd numbers equals k².
82. **An employee’s total weekly pay is calculated by multiplying the hourly wage and number of regular hours plus any overtime pays which in turn is calculated as total overtime hours multiplied by 1.5 times the hourly wage. Write a program that takes as inputs the hourly wage, total regular hours, and total overtime hours and prints an employee’s total weekly pay.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 985 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        float wage, regular, overtime, total;
        scanf("%f %f %f", &wage, &regular, &overtime);
        total = (wage * regular) + (overtime * 1.5 * wage);
        printf("Total weekly pay = %.2f", total);
        return 0;
    }
    ```

    - Regular pay is hourly wage multiplied by regular hours.
    - Overtime pay is overtime hours multiplied by 1.5 times the hourly wage.
    - The two parts are added to give the total weekly pay.
83. **Write a C program: 1+2^n+3^n+4^n+\dots\dots\dots\dots+n^n (where n>0).** *[NACTAR Assistant Instructor (ICT) 2020 compact it 990-991 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    #include <math.h>
    int main() {
        int n, i;
        double sum = 0;
        scanf("%d", &n);
        for (i = 1; i <= n; i++)
            sum += pow(i, n);
        printf("Sum = %.0lf", sum);
        return 0;
    }
    ```

    - Each term is i raised to the power n, and i runs from 1 to n.
    - For n = 3 the value is 1³ + 2³ + 3³ = 36.
84. **X is an integer stream of N numbers. You have to select 2 data P and Q such that A <= (P+Q) <= B. Write an algorithm / pseudo code/ C program how many ways you can select P & Q. The time complexity must be n log n.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1005-1006 (ET: DU)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int x[100], n, A, B, i, j, found = 0;
        scanf("%d", &n);
        for (i = 0; i < n; i++) scanf("%d", &x[i]);
        scanf("%d %d", &A, &B);
        for (i = 0; i < n && !found; i++)
            for (j = i + 1; j < n; j++)
                if (x[i] + x[j] >= A && x[i] + x[j] <= B) {
                    printf("P = %d, Q = %d", x[i], x[j]);
                    found = 1;
                    break;
                }
        if (!found) printf("No such pair found");
        return 0;
    }
    ```

    - We check every pair once. We report the first pair whose sum falls in the range.
    - Time complexity O(n²). Sorting the stream first and using two pointers would reduce it to O(n log n).
85. **Write a code in C/C++ that will output the 2nd largest number. (If N>=1)** *[Combined 4 Banks Assistant Programmer 2020 compact it 1008-1009 (ET: DU)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, x, max, second;
        scanf("%d", &n);
        scanf("%d", &max);
        second = -2147483648;
        for (i = 1; i < n; i++) {
            scanf("%d", &x);
            if (x > max) { second = max; max = x; }
            else if (x > second && x != max) second = x;
        }
        if (n < 2) printf("Second largest does not exist");
        else printf("Second largest = %d", second);
        return 0;
    }
    ```

    - We track both the largest and the second largest in one pass.
    - The check `x != max` stops a repeat of the maximum from being counted as the second largest.
    - Time complexity O(n).
86. **0 থেকে n সংখ্যক পর্যন্ত Fibonacci Series লেখার জন্য প্রোগ্রাম লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1040-1041 (ET: DPI)]*


    Answer:

    ```c
    #include <stdio.h>
    int main() {
        int n, i, a = 0, b = 1, next;
        scanf("%d", &n);
        if (n >= 1) printf("%d ", a);
        if (n >= 2) printf("%d ", b);
        for (i = 3; i <= n; i++) {
            next = a + b;
            printf("%d ", next);
            a = b;
            b = next;
        }
        return 0;
    }
    ```

    - We print the first two terms 0 and 1 separately. After that, each new term is the sum of the previous two.
    - Time complexity O(n) and space complexity O(1).

## Output Tracing & Control Flow (35)

1. **C output problem.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

2. **What will be the output of following program?**
```c
#include <stdio.h>
int main() {
    int i=-1, j=-1, k=0, l=2, m;
    m= i++ && j++ && k++ || l++;
    printf("%d %d %d %d %d", i, j, k, l, m);
    return 0;
}

```
*[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1438 (ET: BUET)]*


   Answer: Output is `0 0 1 3 1`

   - `i++` uses −1 which is true, then i becomes 0.
   - `j++` uses −1 which is true, then j becomes 0.
   - `k++` uses 0 which is false, then k becomes 1. So the whole `&&` chain is false.
   - The left side of `||` is false. So `l++` is evaluated. It uses 2, which is true, then l becomes 3.
   - The result of the `||` expression is 1, so m = 1.
   - Final values: i = 0, j = 0, k = 1, l = 3, m = 1.
3. **(b) Find out the output of this program.**
```c
for (int i= 5; i>=1; i--) {
    for (int j=1; j<=i; j++) {
        printf("%3d", j);
    }
}

```
*[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1444 (ET: N/A)]*


   Answer: Output is

   ```text
     1  2  3  4  5  1  2  3  4  1  2  3  1  2  1
   ```

   - The outer loop runs with i = 5, 4, 3, 2, 1.
   - For each i the inner loop prints 1 up to i.
   - There is no newline in the code, so everything appears on one line.
   - `%3d` right aligns each number in a field of three characters.
4. **Find the output of the following program:** *[BREB Assistant Programmer (AP) 21.02.2025 compact it 1334 (ET: N/A)]*
A)
```c
char str[20] = "Development";
str[5] = '\0';
int len = strlen(str);
printf("%s", str);

```
B)
```c
int main() {
    int i = 2, j = 2;
    while (i?--i:j++)
        printf("%d", i);
    return 0;
}

```


   Answer:

   A) Output is `Devel`
   - `str[5] = '\0'` puts a null terminator at index 5. So the string ends right after "Devel".
   - `strlen` counts characters up to the first null, so len becomes 5.
   - `printf("%s", str)` stops at the null and prints only Devel. The rest of the characters are still in memory, but they are not printed.

   B) Output is `1`
   - i = 2 and j = 2. The condition is `i ? --i : j++`.
   - First pass: i is 2 which is true, so `--i` runs and i becomes 1. The condition value is 1, so the body prints 1.
   - Second pass: i is 1 which is true, so `--i` runs and i becomes 0. The condition value is now 0, so the loop ends without printing.
   - So only a single 1 is printed.
5. **Output problem:** *[BREB Assistant Programmer 18.02.2023 compact it 470 (ET: N/A)]*
```c
#include<stdio.h>
int main() {
int i=1,j=1, k=1;

cout<<++i || ++j && ++ km 101

cout<<i<<j<<k;

return 0;
}
```


   Answer: The program will not compile.

   - The program includes `stdio.h`. But `cout` belongs to C++ and needs `iostream` with `using namespace std`.
   - The line `cout<<++i || ++j && ++ km 101` is not valid in either language. `km 101` means nothing, and the statement has no semicolon.
   - If we correct it to the C++ statement `cout << (++i || ++j && ++k);`, then this is what happens.
   - `++i` makes i = 2, which is true. Because `||` uses short circuit evaluation, the right side is never run. So j and k stay 1.
   - Then `cout<<i<<j<<k;` would print `211`.
6. **Output problem:** *[BREB Assistant Programmer 18.02.2023 (ET: N/A)]*
```c
#include<stdio.h>

int main() {

float p=10.5;

int a=5*p +5.0;

printf("%d", a);

return 0;
}
```


   Answer: Output is `57`

   - `5 * p` is `5 * 10.5`, which equals 52.5 as a float.
   - Adding 5.0 gives 57.5.
   - When we assign a float to an `int`, the decimal part is cut off. It is not rounded. So a becomes 57.
   - If we wanted rounding, we would write `a = (int)(5*p + 5.0 + 0.5)` or use the `round()` function.
7. **Explain following program while part in step for the input 1221 and 3456 and also write the output of the program. (সম্পূর্ণ প্রশ্ন সংগ্রহ করা সম্ভব হয় নি!!)** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 463 (ET: BUET)]*

8. **Write the function for which the output is 1 for that input.** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 463 (ET: BUET)]*

9. **In the below C code. Write the Output on below table based on code and left side. And also explain the line 7-11 in below code.**
```c
#include <stdio.h>
int main() {
    int n, reversed = 0, remainder, original;
    printf("Enter an integer: ");
    scanf("%d", &n);
    original = n;
    while (n!= 0) {
        remainder = n % 10;
        reversed = reversed * 10 + remainder;
        n /= 10;
    }
    if (original == reversed)
        printf("%d is a palindrome.", original);

```
*[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 464 (ET: BUET)]*


   Answer: The program checks whether a number is a palindrome by reversing it.

   Explanation of the while loop, which is the part in lines 7 to 11:
   - `remainder = n % 10` takes the last digit of n.
   - `reversed = reversed * 10 + remainder` moves the number built so far one place left and adds the new digit.
   - `n /= 10` removes the last digit of n.
   - The loop runs until n becomes 0. By then `reversed` holds the digits of the original number in reverse order.

   Trace for n = 1221:

   | Pass | n before | remainder | reversed | n after |
   |---|---|---|---|---|
   | 1 | 1221 | 1 | 1 | 122 |
   | 2 | 122 | 2 | 12 | 12 |
   | 3 | 12 | 2 | 122 | 1 |
   | 4 | 1 | 1 | 1221 | 0 |

   - Since original 1221 equals reversed 1221, the output is `1221 is a palindrome.`
   - For 3456 the reversed value is 6543, which is different, so it is not a palindrome.
   - Time complexity O(number of digits), that is O(log n).
10. **C programming output problem.** *[Teletalk Assistant Manager (IT) 2023 compact it 468 (ET: N/A)]*

11. **What is the output of code snippet?** *[BICIC Assistant Programmer 2022 compact it 631 (ET: BUET)]*

12. **নিচের পাইথন program এর Output বের কর:** *[BTCL Junior Assistant Manager 2022 compact it 641 (ET: BUET)]*
```python
def main():
    x, y = 8, 4
    if(x < y):
        st= "x is less than y"
    else:
        st= "x is greater than y"
    print (st)
if __name__ == "__main__":
    main()
```


    Answer: Output is `x is greater than y`

    - x is 8 and y is 4, so the condition `x < y` is false.
    - Control goes to the `else` branch, which assigns the string "x is greater than y" to st.
    - `print(st)` then displays that string.
    - The `if __name__ == "__main__":` line makes `main()` run when we execute the file directly.
13. **Output Tracing:** *[NSDA Assistant Programmer Date: 04-03-2022 compact it 657 (ET: N/A)]*
A)
```c
char str[20] = "Development";
str[5] = '\0';
int len = strlen(str);
printf("%s", str);
```
B)
```c
int i;
for (i=0; i<9; i++) {
    if(i==5) continue;
    printf ("%d\n", i);
}
```


    Answer:

    A) Output is `Devel`
    - Putting `'\0'` at index 5 ends the string there. So `strlen` returns 5 and `printf` prints only the first five characters.

    B) Output is
    ```text
    0
    1
    2
    3
    4
    6
    7
    8
    ```
    - The loop runs from 0 to 8.
    - When i is 5, `continue` skips the `printf` for that turn only. So 5 is missing from the output.
    - `continue` does not stop the loop. It only jumps to the next turn. That is the difference from `break`.
14. **Find the output of the following program:** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 699 (ET: BUET)]*
```c
#include<stdio.h>
int main() {
    int a=10, b=25;
    a = b++ + a++;
    b = ++b + ++a;
    printf("%d %d\n", a, b);
    return 0;
}
```


    Answer: With gcc the output is `36 63`, but this program actually has undefined behaviour.

    - In `a = b++ + a++;` the variable a is changed twice in one expression. Once by `a++`, and once by the assignment. There is no sequence point between them.
    - In `b = ++b + ++a;` the variable b is also changed twice.
    - The C standard says such an expression is undefined. So different compilers may print different values.
    - What gcc happens to produce: `a = 25 + 10 = 35`, then the pending `a++` makes a = 36. Next `++b` gives 27 and `++a` gives 37, so b = 27 + 37 = 64, and the pending update leaves 63.
    - In an exam, the right point to write is that this is undefined behaviour, and the expression should be split into separate statements.
15. **Find the output of the following program:** *[DESCO Assistant Engineer (CSE) 10.09.2022 compact it 699 (ET: BUET)]*
```c
#include<stdio.h>
int main() {
    int a=2, b=5, c;
    c = a++ + b;
    printf("%d %d %d", a, b, c);
    return 0;
}
```


    Answer: Output is `3 5 7`

    - `c = a++ + b` uses the current value of a, which is 2, so c = 2 + 5 = 7.
    - After the expression is done, the post-increment makes a = 3.
    - b is never modified, so it stays 5.
    - Final printed values are a = 3, b = 5 and c = 7.
16. **What will be the output of the program?** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 717 (ET: N/A)]*
```c
#include<stdio.h>
void main() {
    int a[5]={5,1,15,20,25};
    int i,j,m;
    i=++a[1];
    j=a[1]++;
    m=a[i++];
    printf("%d, %d, %d",i,j,m);
}
```


    Answer: Output is `3, 2, 15`

    - The array starts as {5, 1, 15, 20, 25}.
    - `i = ++a[1]` first raises a[1] from 1 to 2, then assigns that new value. So i = 2 and the array is {5, 2, 15, 20, 25}.
    - `j = a[1]++` gives j the current value 2, then raises a[1] to 3. So j = 2 and the array is {5, 3, 15, 20, 25}.
    - `m = a[i++]` uses the current i, which is 2. So m = a[2] = 15, and then i becomes 3.
    - Final values printed are i = 3, j = 2 and m = 15.
17. **What is the output of the following code?** *[NWPGCL Junior Assistant Manager (IT) 2022 compact it 731 (ET: N/A)]*
```c
#include <stdio.h>
int isLeapYear(int year);
int main() {
    int a = 1;
    printf("%d %d %d", ++a, a, a++);
    return 0;
}
```


    Answer: This program has undefined behaviour, so no single output is guaranteed.

    - In `printf("%d %d %d", ++a, a, a++)` the variable a is changed twice, by `++a` and by `a++`. Both happen in one expression, with no sequence point between them.
    - Also, C does not fix the order in which function arguments are evaluated. The compiler may do them right to left, left to right, or in any other order.
    - So different compilers print different results. gcc commonly prints `3 3 1`.
    - The correct answer in an exam is to say that this is undefined behaviour, and that such expressions must be split into separate statements.
18. **Output programs:** *[BOF Assistant Programmer 2022 compact it 733 (ET: MIST)], [Water Supply and Sewerage Authority (WASA); Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)]*
```c
#include <stdio.h>
int fun(int n) {
    if (n == 4)
        return n;
    else
        return 2 * fun(n + 1);
}
int main() {
    printf("%d", fun(2));
    return 0;
}
```


    Answer: Output is `16`

    - `fun(2)` is not 4, so it returns `2 * fun(3)`.
    - `fun(3)` is not 4, so it returns `2 * fun(4)`.
    - `fun(4)` matches the base case and returns 4.
    - Unwinding gives `fun(3) = 2 * 4 = 8` and `fun(2) = 2 * 8 = 16`.
    - So 16 is printed.
19. **Write down the output from following statement:** *[Pubali Bank Limited; Assistant Engineer (SD) 2022 compact it 758 (ET: N/A)]*
```c
#include <stdio.h>
#define x 9+2/4*3-2*4+(5-4)*3
void main() {
    int i,y;
    y=6+3*3/5;
    i=x*x+y;
    printf("%d", i);
}
```


    Answer: Output is `30`

    - `#define` only replaces text. It does not compute the expression first. This is the trap in the question.
    - `y = 6 + 3*3/5` gives 6 + 9/5, and integer division makes 9/5 equal to 1, so y = 7.
    - `i = x*x + y` expands textually to
      `i = 9+2/4*3-2*4+(5-4)*3 * 9+2/4*3-2*4+(5-4)*3 + y`
    - Evaluating with the normal precedence rules gives 30.
    - Lesson: always put brackets around a macro value, for example `#define x (9+2/4*3-2*4+(5-4)*3)`. Without them, the text replacement changes the meaning.
20. **(ii) নিচের C প্রোগ্রামটির ভুলগুলো সঠিক করুন এবং প্রোগ্রামটির আউটপুট লিখুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 783 (ET: N/A)]*
```c
include<stdio.h>
int main{
    int i, sum=0
    for(i=1,i<=10,i++;{
        sum=sum+i
    }
    printf(Sum of number=d, sum)
    return 0
}
```


    Answer:

    Corrected program:
    ```c
    #include <stdio.h>
    int main() {
        int i, sum = 0;
        for (i = 1; i <= 10; i++) {
            sum = sum + i;
        }
        printf("Sum of number = %d", sum);
        return 0;
    }
    ```

    Errors that were fixed:
    - `include<stdio.h>` was missing the `#` symbol.
    - `int main{` needed parentheses, so it becomes `int main()`.
    - `int i, sum=0` was missing the terminating semicolon.
    - The for loop used commas instead of semicolons, and had a stray `{` after `i++`.
    - `sum=sum+i` was missing a semicolon.
    - The printf string was not in quotes and `d` was not written as the format specifier `%d`.
    - `return 0` was missing a semicolon.

    Output: `Sum of number = 55`
21. **Find the Output of following C Program:** *[BCC Assistant Programmer 12.02.2021 compact it 812 (ET: BUET)]*
```c
#include<stdio.h>
int function(int x[],int i){
    int s=x[i];
    if(i>0){
        s+=function(x,i-1);
    }
    printf("%d",s);
    return s;
}
int main(){
    int y[]={1,3,2,8};
    function(y,2);
    return 0;
}
```


    Answer: Output is `146`

    - `function(y, 2)` is called with the array {1, 3, 2, 8}.
    - It computes `s = y[2] = 2`, and since i > 0 it calls `function(y, 1)`.
    - `function(y, 1)` computes `s = y[1] = 3`, and calls `function(y, 0)`.
    - `function(y, 0)` computes `s = y[0] = 1`, and since i is not greater than 0 it prints 1 and returns 1.
    - Back in `function(y, 1)`, s becomes 3 + 1 = 4, which is printed, and 4 is returned.
    - Back in `function(y, 2)`, s becomes 2 + 4 = 6, which is printed.
    - The printing happens after the recursive call. So the order is 1, then 4, then 6, giving 146 on one line.
22. **Write Output from below code:** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 819 (ET: BUET)]*
```c
#include<stdio.h>
int main() {
    int i;
    char s[]="Bangladesh Industrial and Technical Assistant Center";
    char*s1;
    s1=s;
    for(i=0; i<10; i++) {
        printf("%c", s[i]);
        ++s1;
    }
    printf("\n");
    for(i=0; i<10; i++) {
        printf("%c", s1[i]);
        ++s1;
    }
    return 0;
}
```


    Answer: Output is

    ```text
    Bangladesh
     nutiladTc
    ```

    - In the first loop `s[i]` prints the first ten characters, that is "Bangladesh". At the same time `++s1` moves the pointer ten places. So s1 now points at the space after "Bangladesh".
    - In the second loop both `s1[i]` and `++s1` move the position. So the real step is two characters, not one.
    - Starting from index 10, the characters picked are at index 10, 12, 14, 16, 18, 20, 22, 24, 26 and 28, which spell " nutiladTc".
    - The trap: if we increase the pointer inside a loop that also uses an index, we skip every second character.
23. **Fill in the gape and find output of the following program:** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823 (ET: BUET)]*
```c
#include<stdio.h>
int power(int n, int r){
    int sum, i;
    sum=1;
    for(i=1; i<=r; i++)
        sum*=n;
    return sum;
}
int main(){
    int n, r;
    scanf("%d %d", &n, &r);
    printf("%d", power(n, r));
    return 0;
}
```


    Answer: The function computes n raised to the power r by repeated multiplication.

    - `sum` starts at 1, which is the correct starting value for a product.
    - The loop multiplies sum by n exactly r times.
    - For input n = 2 and r = 5 the output is 32.
    - For input n = 3 and r = 4 the output is 81.
    - If r is 0, the loop never runs and 1 is returned. That is mathematically correct.
    - Time complexity O(r). Using fast exponentiation would reduce it to O(log r).
24. **Find out program output of f(\text{arr}, 2), f(\text{arr}, 3), f(\text{arr}, 5), f(\text{arr}, 8). \text{arr}[] = [0, 1, 1, 0, 1, 1, 0, 1]** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 861-862 (ET: N/A)]*
```c
int f(int *arr, int arrSize) {
    int r = 0;
    for (int i = 0; i < arrSize; ++i) {
        r = r ^ *(arr + i);
    }
    return r;
}
```


    Answer: The function returns the XOR of the first arrSize elements. For arr = [0, 1, 1, 0, 1, 1, 0, 1] the results are as follows.

    - `f(arr, 2)` = 0 ^ 1 = 1
    - `f(arr, 3)` = 0 ^ 1 ^ 1 = 0
    - `f(arr, 5)` = 0 ^ 1 ^ 1 ^ 0 ^ 1 = 1
    - `f(arr, 8)` = 0 ^ 1 ^ 1 ^ 0 ^ 1 ^ 1 ^ 0 ^ 1 = 1

    - XOR of a bit with itself gives 0. XOR with 0 leaves the bit unchanged. So the result is just the parity of the number of 1s, that is odd or even.
    - Counting the 1s: in the first 2 elements there is one 1 giving an odd count, in the first 3 there are two 1s giving even, in the first 5 there are three 1s giving odd, and in all 8 there are five 1s giving odd.
25. **Output of the following program:** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 868 (ET: BUET)]*
```c
#include<stdio.h>
int recursion(int x) {
    int static y=0;
    if(x<=0)
        return 1;
    y=y+x;
    printf("%d\n", y);
    return recursion(x-2)+recursion(x-3);
}
int main() {
    int result;
    result = recursion(5);
    printf("%d\n", result);
    return 0;
}
```


    Answer: Output is

    ```text
    5
    8
    9
    11
    5
    ```

    - `y` is declared `static`. So it keeps its value across all the calls, instead of starting fresh each time.
    - `recursion(5)`: y = 0 + 5 = 5, prints 5, then calls recursion(3) and recursion(2).
    - `recursion(3)`: y = 5 + 3 = 8, prints 8, then calls recursion(1) and recursion(0).
    - `recursion(1)`: y = 8 + 1 = 9, prints 9, then calls recursion(-1) and recursion(-2), both of which hit the base case and return 1 each, so it returns 2.
    - `recursion(0)` hits the base case and returns 1, so recursion(3) returns 2 + 1 = 3.
    - `recursion(2)`: y = 9 + 2 = 11, prints 11, then calls recursion(0) and recursion(-1), each returning 1, so it returns 2.
    - Finally recursion(5) returns 3 + 2 = 5, which is printed last.
    - Key point to learn: how a `static` local variable behaves inside a recursive function.
26. **Find the output of following program:** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 875 (ET: BUET)]*
```c
int i, j, p, sum;
sum=0;
for(i=-1,p=0; i<=10; i=i+2) {
    p=i*i;
    if(i>5)
        break;
    sum=sum+ (i+p);
    printf("i=%d, p=%d, sum=%d\n",i, p, sum);
}
printf("\n Outsite Loop, i=%d, p=%d, sum=%d\n", i, p, sum);
return 0;
```


    Answer: Output is

    ```text
    i=-1, p=1, sum=0
    i=1, p=1, sum=2
    i=3, p=9, sum=14
    i=5, p=25, sum=44

     Outsite Loop, i=7, p=49, sum=44
    ```

    - The loop starts at i = −1 and increases by 2 each time.
    - i = −1: p = 1, sum = 0 + (−1 + 1) = 0
    - i = 1: p = 1, sum = 0 + (1 + 1) = 2
    - i = 3: p = 9, sum = 2 + (3 + 9) = 14
    - i = 5: p = 25, sum = 14 + (5 + 25) = 44
    - i = 7: p is computed first and becomes 49. Then `i > 5` is true, so `break` fires before sum is updated.
    - That is why the value of p outside the loop is 49 while sum stays at 44.
27. **Output of the following program:** *[NWPGCL Assistant Engineer (IT) 03.12.2021 compact it 878-879 (ET: BUET)]*
```c
#include<stdio.h>
void func(int arr[], int n) {
    int i,j;
    for(i=0; i<n; i++) {
        for(j=0; j<n-i-1; j++) {
            if(arr[j]>arr[j+1]) {
                int temp;
                temp=arr[j];
                arr[j]= arr[j+1];
                arr[j+1] = temp;
            }
        }
    }
}
int main () {
    int arr[]={39,22,11,34};
    int n,i;
    n=sizeof(arr)/sizeof(arr[0]);
    func(arr,n);
    for(i=0;i<n;i++) {
        printf("%d " ,arr[i]);
    }
    return 0;
}
```


    Answer: Output is `11 22 34 39`

    - The function `func` is bubble sort. It compares side by side elements and swaps them when they are in the wrong order.
    - `n = sizeof(arr)/sizeof(arr[0])` computes 16/4 = 4, which is the number of elements.
    - Starting array: 39, 22, 11, 34
    - Pass 1: 22, 11, 34, 39
    - Pass 2: 11, 22, 34, 39
    - Pass 3 and 4 make no further swaps.
    - The array is passed by address. So the sorting done inside the function is visible in main too.
28. **Find Output:** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 911-912 (ET: BUET)]*
```c
#include <stdio.h>
int main() {
    int i, sum=0, x;
    for(i=0, x=0; i<=10; i+=2) {
        x=i+3;
        if(i==2)
            continue;
        if(i>=8)
            break;
        sum+=(i+x);
        printf("i=%d x=%d sum=%d\n", i, x, sum);
    }
    printf("Out site loop:\n i=%d x=%d sum=%d", i, x, sum);
    return(0);
}
```


    Answer: Output is

    ```text
    i=0 x=3 sum=3
    i=4 x=7 sum=14
    i=6 x=9 sum=29
    Out site loop:
     i=8 x=11 sum=29
    ```

    - i = 0: x = 3, sum = 0 + 3 = 3, printed.
    - i = 2: x = 5, but `continue` fires, so the printf and the sum update are skipped for this pass.
    - i = 4: x = 7, sum = 3 + 11 = 14, printed.
    - i = 6: x = 9, sum = 14 + 15 = 29, printed.
    - i = 8: x = 11 is assigned first, then `i >= 8` is true so `break` exits the loop.
    - That is why x is 11 outside the loop, even though that turn printed nothing.
29. **Find the output of the following program. You must show each staps.** *[NRCC Assistant Programmer 2021 compact it 931 (ET: N/A)]*
```c
#include<stdio.h>
int main(){
    int i=0, j=5, x=0, count=0;
    while(j>i){
        if(i==7)
            break;
        x=x+i+count;
        count=count+2;
        i++;
    }
    printf("i=%d, count=%d", i, count);
    printf("j=%d, x=%d", i, x);
    return 0;
}
```


    Answer: Output is `i=5, count=10j=5, x=30`

    - The loop runs while j > i, that is while 5 > i, so i takes the values 0, 1, 2, 3 and 4.

    | Pass | i | count | x = x + i + count |
    |---|---|---|---|
    | 1 | 0 | 0 | 0 + 0 + 0 = 0 |
    | 2 | 1 | 2 | 0 + 1 + 2 = 3 |
    | 3 | 2 | 4 | 3 + 2 + 4 = 9 |
    | 4 | 3 | 6 | 9 + 3 + 6 = 18 |
    | 5 | 4 | 8 | 18 + 4 + 8 = 30 |

    - After the fifth pass i becomes 5 and count becomes 10, so the condition 5 > 5 fails and the loop ends.
    - The `if (i == 7) break;` never fires because i never reaches 7.
    - Note: the second printf prints i again by mistake, under the label j. Also there is no newline between the two printf calls. That is why the output looks joined.
30. **Find out the output of the following program.** *[SGFL Assistant General Engineer 2021 compact it 935 (ET: BUET)]*
```c
#include<stdlib.h>
#include<string.h>
int main(){
    int i=0, length;
    char string[] = "Hello\0 World!!";
    length = strlen(string);
    char*s = string;
    for(i=0; i<length; ++i)
        printf("%c", *++s);
    return 0;
}
```


    Answer: Output is `ello ` (the five characters e, l, l, o and a space)

    - The string literal is `"Hello\0 World!!"`, which contains an explicit null character after Hello.
    - `strlen` stops at the first null, so length becomes 5.
    - `s` starts at the beginning of the array. The loop prints `*++s`, which moves the pointer first and then reads the value.
    - So the first printed character is index 1 which is 'e', then 'l', 'l', 'o' and finally the character at index 5, which is the embedded null.
    - A null character prints nothing we can see. So the visible output is `ello`.
    - Lesson: a string in C ends at the first `'\0'`. The text after it is still in memory, but string functions never use it.
31. **After compilation and execution, what will be output in the following code:** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 972 (ET: BUET)]*

32. **Write down the output of following program:** *[NACTAR Assistant Instructor (ICT) 2020 compact it 991 (ET: N/A)]*

33. **What will be the output in C and java code? (i) C program:** *[Combined 4 Banks Assistant Programmer 2020 compact it 1003 (ET: DU)]*

34. **a) Using Pseudocode give an example of run time error.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1035-1036 (ET: BUET)]*


    Answer: A run time error is an error that shows up while the program is running, even though it compiled fine.

    Pseudocode example, division by zero:
    ```text
    BEGIN
        READ a
        READ b
        result = a / b        // if b is 0 this crashes at run time
        PRINT result
    END
    ```

    - The compiler accepts this, because the syntax is correct. But if the user enters 0 for b, the program crashes.

    Other common run time errors:
    - Array index out of bounds, for example accessing `a[10]` in an array declared as `a[5]`.
    - Dereferencing a null or uninitialised pointer.
    - Stack overflow from recursion without a base case.
    - Running out of heap memory during dynamic allocation.

    Prevention:
    ```text
    IF b = 0 THEN
        PRINT "Division by zero is not allowed"
    ELSE
        result = a / b
        PRINT result
    ENDIF
    ```
35. **Find the Output:** *[Sundharban Gas Assistant Programmer 2020 compact it 1047 (ET: N/A)]*

## Recursion & Functions (32)

1. (a) Microprocessor এবং Microcontroller এর মধ্যে পার্থক্য লিখুন।
   (b) কোন প্রোগ্রামিং ভাষাকে 'C' programming language বলা হয়? একটি ছোট প্রোগ্রাম লিখুন, যা recursive function ব্যবহার করে ডিসপ্লেতে ৫ এর ফ্যাক্টোরিয়াল গণনা করবে। *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*


   Answer:

   | Point | Microprocessor | Microcontroller |
   |---|---|---|
   | Definition | Only the CPU on a single chip | CPU, memory and I/O ports on one chip |
   | Memory | RAM, ROM must be added externally | Built in RAM, ROM and timers |
   | Cost | Higher overall system cost | Lower, since everything is on one chip |
   | Power consumption | High | Low, suitable for battery devices |
   | Use | General purpose computing, PCs and laptops | Embedded and dedicated tasks |
   | Example | Intel Core i7, 8086 | 8051, ATmega328, PIC |
   | Speed | Higher clock speed | Comparatively lower |

   - A microprocessor is the brain of a general purpose computer. A microcontroller is a complete small computer, built for one fixed job such as a washing machine or a traffic light.
2. **Write a C program to find the sum of digits of an integer number using "recursion".** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1338 (ET: N/A)]*


   Answer:

   ```c
   #include <stdio.h>
   
   int sumDigits(int n) {
       if (n == 0) return 0;
       return (n % 10) + sumDigits(n / 10);
   }
   
   int main() {
       int n;
       scanf("%d", &n);
       printf("Sum of digits = %d", sumDigits(n));
       return 0;
   }
   ```

   - Base case: when n becomes 0 the recursion stops and returns 0.
   - Recursive case: we take the last digit with n % 10 and pass the rest on as n / 10.
   - For 1234 the result is 4 + 3 + 2 + 1 = 10, and the time complexity is O(log n).
3. **What is recursion?** *[BBA Assistant Programmer 12.07.2025 compact it 1432 (ET: BUET)]*


   Answer: Recursion is a technique where a function calls itself, directly or indirectly, to solve a smaller version of the same problem.

   Two parts are always required:
   - Base case: the condition where the function stops calling itself and returns a value. Without it the recursion never ends.
   - Recursive case: the function calls itself with a smaller or simpler input that moves towards the base case.

   Example:
   ```c
   int fact(int n) {
       if (n == 0) return 1;      // base case
       return n * fact(n - 1);    // recursive case
   }
   ```

   - Every call is kept on the system stack. So recursion uses O(depth) extra memory.
   - Advantage: the code becomes short and natural for problems like tree traversal, Tower of Hanoi and divide and conquer.
   - Disadvantage: it is slower than a loop, because each function call costs time. And if the base case is missing, we get a stack overflow.
4. **Write recursive way below this program:** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 417 (ET: BUET)]*
```c
for(int i=1, i<n; i++)
    for(int j=0 ; j<i ; j ++)
        For( int k =0; k<i ; k++)
            X=X+1
```


   Answer:

   ```c
   #include <stdio.h>
   
   int X = 0;
   
   void loopK(int i, int k) {
       if (k >= i) return;
       X = X + 1;
       loopK(i, k + 1);
   }
   
   void loopJ(int i, int j) {
       if (j >= i) return;
       loopK(i, 0);
       loopJ(i, j + 1);
   }
   
   void loopI(int i, int n) {
       if (i >= n) return;
       loopJ(i, 0);
       loopI(i + 1, n);
   }
   
   int main() {
       int n = 5;
       loopI(1, n);
       printf("X = %d", X);
       return 0;
   }
   ```

   - We replace each of the three nested loops with one recursive function. The loop variable becomes a parameter.
   - The loop condition becomes the base case and the increment becomes the argument of the next call.
   - The total work is the same as the original code, that is O(n³).
5. **Output find out from recursion:** *[Combined Bank Assistant Programmer 09.02.2024 compact it 298 (ET: BIBM)]*
```c
#include <stdio.h>
void fun(int x){
    if(x<0) {
        return;
    }
    printf("%d\n",x--);
    fun(--x);
    printf("%d\n",x);
}
int main() {
    fun(5);
    return 0;
}
```


   Answer: The output is

   ```text
   5
   3
   1
   -1
   1
   3
   ```

   Trace of the calls:
   - `fun(5)`: prints 5 because `x--` uses the value first, then x becomes 4. Next `--x` makes x = 3 and calls `fun(3)`.
   - `fun(3)`: prints 3, x becomes 2, then `--x` makes x = 1 and calls `fun(1)`.
   - `fun(1)`: prints 1, x becomes 0, then `--x` makes x = −1 and calls `fun(-1)`.
   - `fun(-1)`: the base case x < 0 is true, so it returns immediately.
   - Now the stack unwinds. The second printf of each call runs: `fun(1)` prints −1, `fun(3)` prints 1, and `fun(5)` prints 3.

   - Key point: `x--` prints the old value, but `--x` changes x before passing it. So x drops by 2 in every call.
6. **Find the output of following program:**
```c
int F(n) {
    if n == 0
    return 0;
    if n == 1
    return 1;
    return F(n-2)+F(n-1);
}
int main() {
    result F(5);
}
```
*[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 522 (ET: MIST)]*


   Answer: The output is 5.

   - The function is the Fibonacci definition, since F(n) = F(n−2) + F(n−1) with F(0) = 0 and F(1) = 1.
   - F(2) = F(0) + F(1) = 0 + 1 = 1
   - F(3) = F(1) + F(2) = 1 + 1 = 2
   - F(4) = F(2) + F(3) = 1 + 2 = 3
   - F(5) = F(3) + F(4) = 2 + 3 = 5
   - So `F(5)` returns 5. This plain recursion takes O(2ⁿ) time, because it computes the same subproblems again and again.
7. **What is function?** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*


   Answer: A function is a block of code that does one specific task. We can call it from anywhere in the program.

   Parts of a function:
   - Declaration or prototype: tells the compiler the return type, name and parameter types, for example `int add(int, int);`
   - Definition: contains the actual body of the function.
   - Call: the statement that sends control to the function, for example `add(5, 3);`

   Types:
   - Library functions: already written for us, and available through header files. Examples are `printf()`, `scanf()` and `sqrt()`.
   - User defined functions: written by the programmer for a specific need.

   Advantages:
   - It stops repetition, because we can call one function many times.
   - It makes the program modular, and easier to read, test and debug.
   - We can reuse the same code in other programs.
8. **Write a C/C++ program to calculte factorial of N using recursive function.** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 472 (ET: N/A)]*


   Answer:

   ```c
   #include <stdio.h>
   
   long long fact(int n) {
       if (n == 0 || n == 1) return 1;
       return n * fact(n - 1);
   }
   
   int main() {
       int n;
       scanf("%d", &n);
       printf("Factorial = %lld", fact(n));
       return 0;
   }
   ```

   - Base case: factorial of 0 and 1 is 1.
   - Recursive case: n! = n × (n−1)!
   - Time complexity O(n) and stack space O(n).
9. **Write the recursive function of the below problem and find the recurrence relation of the function. F(n) = 1+2+3+..........+(n-1)+n** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 472 (ET: N/A)]*


   Answer:

   ```c
   #include <stdio.h>
   
   int F(int n) {
       if (n == 1) return 1;
       return n + F(n - 1);
   }
   
   int main() {
       printf("%d", F(10));
       return 0;
   }
   ```

   - Recurrence relation: T(n) = T(n−1) + 1 with T(1) = 1.
   - Solving it gives T(n) = n, so the time complexity is O(n).
   - The value returned is n(n+1)/2, for example F(10) = 55.
10. **(a) Mention two basic differences between ‘Call by Value’ and ‘Call by Reference’. Write a simple program in C to swap two integer values using ‘Call by value’.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 487 (ET: N/A)]*


    Answer:

    Two basic differences:
    - Call by Value sends a copy of the argument. So changes inside the function do not touch the original variable. Call by Reference sends the address. So changes do affect the original.
    - Call by Value needs extra memory for the copy. Call by Reference works straight on the original memory, so it is faster for large data.

    Program showing both:

    ```c
    #include <stdio.h>

    void byValue(int a) { a = a + 10; }
    void byReference(int *a) { *a = *a + 10; }

    int main() {
        int x = 5;
        byValue(x);
        printf("After call by value: %d\n", x);      // still 5
        byReference(&x);
        printf("After call by reference: %d\n", x);  // now 15
        return 0;
    }
    ```

    - In C we do call by reference using pointers, because C itself supports only call by value.
11. **(b) Write a program in C using recursion to find the factorial of an integer.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 492 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
   
    long long fact(int n) {
        if (n == 0 || n == 1) return 1;
        return n * fact(n - 1);
    }
   
    int main() {
        int n;
        scanf("%d", &n);
        printf("Factorial = %lld", fact(n));
        return 0;
    }
    ```

    - Base case: factorial of 0 and 1 is 1.
    - Recursive case: n! = n × (n−1)!
    - Time complexity O(n) and stack space O(n).
12. **When a function is called more than one time that is called?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*


    Answer: The name depends on how the function is called.

    - If a function calls itself, it is called recursion, and such a function is a recursive function.
    - If the function calls itself more than once in a single call, for example `F(n-1) + F(n-2)`, it is called multiple recursion or tree recursion.
    - If we simply call a function several times from different places in the program, that is called reusability. It is one of the main advantages of using functions.
13. **(e) Write about the syntax of function.** *[BARC Programmer 04.08.2023 compact it 598 (ET: N/A)]*


    Answer: Syntax of a function in C.

    Function declaration (prototype):
    ```c
    return_type function_name(parameter_type_list);
    ```

    Function definition:
    ```c
    return_type function_name(parameter list) {
        statements;
        return value;
    }
    ```

    Function call:
    ```c
    variable = function_name(arguments);
    ```

    Example:
    ```c
    int add(int a, int b);          // declaration

    int add(int a, int b) {         // definition
        return a + b;
    }

    int main() {
        int s = add(5, 3);          // call
        printf("%d", s);
        return 0;
    }
    ```

    - `return_type` is the type of the value sent back. `void` means nothing is returned.
    - The parameter list may be empty, written as `void`.
14. **(ক) C প্রোগ্রামিং ল্যাঙ্গুয়েজে user defined function এবং library function এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 600 (ET: N/A)]*


    Answer:

    | Point | Library Function | User Defined Function |
    |---|---|---|
    | Who writes it | Already written and supplied with the compiler | Written by the programmer |
    | Where it is declared | In header files such as `stdio.h`, `math.h`, `string.h` | In the programmer's own source file |
    | Need to define | No, only the header must be included | Yes, the body must be written |
    | Name | Fixed and standard | Chosen by the programmer |
    | Purpose | Common general tasks | A specific need of that program |
    | Example | `printf()`, `scanf()`, `sqrt()`, `strlen()` | `add()`, `factorial()`, `isPrime()` |

    - Library functions save time and are already tested. User defined functions give us freedom for problem specific work.
15. **(ক) Call by Value এবং Call by Reference এর মধ্যে পার্থক্য কী?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 617 (ET: N/A)]*


    Answer:

    | Point | Call by Value | Call by Reference |
    |---|---|---|
    | What is passed | A copy of the value | The address of the variable |
    | Effect on original | Original stays unchanged | Original is modified |
    | Memory | Extra memory for the copy | No extra copy, only an address |
    | In C | Default behaviour | Achieved using pointers |
    | Safety | Safer, no accidental change | Faster for large data but riskier |

    - Example: if we pass `x` to a function, nothing changes outside. But if we pass `&x` and change `*a`, then x changes in main too.
16. **(ঘ) উদাহরণসহ Parameter Passing ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 617 (ET: N/A)]*


    Answer: Parameter passing is the way we send values from the calling function to the called function.

    Terms:
    - Formal parameters: the variables written in the function definition.
    - Actual parameters or arguments: the values written in the function call.

    Two methods in C:

    Call by value:
    ```c
    void change(int a) { a = 100; }
    int main() { int x = 5; change(x); printf("%d", x); }   // prints 5
    ```
    - We send a copy. So the original x does not change.

    Call by reference using pointers:
    ```c
    void change(int *a) { *a = 100; }
    int main() { int x = 5; change(&x); printf("%d", x); }  // prints 100
    ```
    - We send the address. So the function works straight on the original variable.

    - Arrays are always passed by address in C, because the array name itself gives the address of the first element.
17. **(খ) উদাহরণসহ recursion ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*


    Answer: Recursion is a technique where a function calls itself to solve a smaller version of the same problem. It stops when it reaches a base case.

    Every recursive function needs two parts:
    - Base case, which stops the recursion.
    - Recursive case, which moves the problem towards the base case.

    Example, factorial of 5:
    ```c
    int fact(int n) {
        if (n == 0) return 1;      // base case
        return n * fact(n - 1);    // recursive case
    }
    ```

    How the calls happen:
    - fact(5) waits for fact(4), fact(4) waits for fact(3), and so on down to fact(0).
    - fact(0) returns 1, then the stack unwinds: 1 × 1 = 1, 2 × 1 = 2, 3 × 2 = 6, 4 × 6 = 24, 5 × 24 = 120.
    - The final answer is 120.

    - Every waiting call sits on the system stack. So the space complexity is O(n).
18. **(ক) Tower of Hanoi সমস্যাটি সমাধানের জন্যে একটি recursive অ্যালগরিদম লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
   
    void hanoi(int n, char from, char aux, char to) {
        if (n == 1) {
            printf("Move disk 1 from %c to %c\n", from, to);
            return;
        }
        hanoi(n - 1, from, to, aux);
        printf("Move disk %d from %c to %c\n", n, from, to);
        hanoi(n - 1, aux, from, to);
    }
   
    int main() {
        int n = 3;
        hanoi(n, 'A', 'B', 'C');
        return 0;
    }
    ```

    - Step 1: move the top n−1 disks from the source to the auxiliary peg.
    - Step 2: move the largest disk from the source to the destination.
    - Step 3: move the n−1 disks from the auxiliary peg to the destination.
    - Recurrence: T(n) = 2T(n−1) + 1, which solves to 2ⁿ − 1 moves, so the complexity is O(2ⁿ).
19. **What are the differences between call by value and call by Reference?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)], [BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 677 (ET: N/A)]*


    Answer:

    | Point | Call by Value | Call by Reference |
    |---|---|---|
    | What is passed | A copy of the value | The address of the variable |
    | Effect on original | Original stays unchanged | Original is modified |
    | Memory | Extra memory for the copy | No extra copy, only an address |
    | In C | Default behaviour | Achieved using pointers |
    | Safety | Safer, no accidental change | Faster for large data but riskier |
20. **Distinguish between Call by value and Call by referee in C/C++.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 670 (ET: N/A)]*


    Answer:

    | Point | Call by Value | Call by Reference |
    |---|---|---|
    | What is passed | A copy of the value | The address of the variable |
    | Effect on original | Original stays unchanged | Original is modified |
    | Memory | Extra memory for the copy | No extra copy, only an address |
    | In C | Default behaviour | Achieved using pointers |
    | Safety | Safer, no accidental change | Faster for large data but riskier |

    - C supports only call by value directly. We copy the effect of call by reference using pointers.
    - C++ supports true call by reference using the `&` symbol in the parameter, for example `void f(int &a)`.
21. **Write a recursive algorithm to find the factorial of a positive integer from 1 to N.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
   
    long long fact(int n) {
        if (n <= 1) return 1;
        return n * fact(n - 1);
    }
   
    int main() {
        int n;
        scanf("%d", &n);
        printf("Factorial of %d = %lld", n, fact(n));
        return 0;
    }
    ```

    - The recursion goes on until n becomes 1. That is the base case.
    - For N the number of calls is N, so the time complexity is O(N).
22. **What do you mean by recursion? Calculate factorial function using recursion with C programming code.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 679 (ET: N/A)]*


    Answer: Recursion means a function calls itself to solve a smaller version of the same problem. It stops at a base case.

    Factorial using recursion:

    ```c
    #include <stdio.h>

    long long fact(int n) {
        if (n == 0 || n == 1)
            return 1;              // base case
        return n * fact(n - 1);    // recursive case
    }

    int main() {
        int n;
        scanf("%d", &n);
        printf("Factorial = %lld", fact(n));
        return 0;
    }
    ```

    - Working for n = 4: fact(4) = 4 × fact(3) = 4 × 3 × fact(2) = 4 × 3 × 2 × fact(1) = 24.
    - Time complexity O(n) and stack space O(n).
    - Without the base case, the function would call itself forever and cause a stack overflow.
23. **Write a program with a recursive function that shows the sum of its digits. For example, input =3426, output will be 3+4+2+6=15.** *[GTCL Assistant Engineer (CSE) 2022 compact it 684 (ET: BUET)]*


    Answer:

    ```c
    #include <stdio.h>
   
    int sumDigits(int n) {
        if (n == 0) return 0;
        return (n % 10) + sumDigits(n / 10);
    }
   
    int main() {
        int n;
        scanf("%d", &n);
        printf("Sum = %d", sumDigits(n));
        return 0;
    }
    ```

    - For input 3426 the calls give 6 + 2 + 4 + 3 = 15.
    - The base case is n = 0. We reach it after the last digit is removed.
24. **(a) Write down a recursive function to find out number of digits is an integer number (n). Draw the recursion tree when n= 5396.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 690 (ET: N/A)]*


    Answer:

    ```c
    int countDigits(int n) {
        if (n == 0) return 0;
        return 1 + countDigits(n / 10);
    }
    ```

    - Base case: when n becomes 0, there are no digits left. So we return 0.
    - Recursive case: we count one digit and pass the rest of the number on.

    Recursion tree for n = 5396:

    ```text
    countDigits(5396)
         |
         +-- 1 + countDigits(539)
                   |
                   +-- 1 + countDigits(53)
                             |
                             +-- 1 + countDigits(5)
                                       |
                                       +-- 1 + countDigits(0)
                                                 |
                                                 +-- returns 0
    ```

    - Unwinding gives 1 + 1 + 1 + 1 + 0 = 4, so the number 5396 has 4 digits.
    - Time complexity O(log₁₀ n) and space complexity O(log₁₀ n) for the stack.
25. **(খ) Recursion কি? Recursion পদ্ধতিতে একটি Integer সংখ্যার Factorial নির্ণয়ের জন্য C-Language এ একটি Program লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 767 (ET: N/A)]*


    Answer: Recursion means a function calls itself to solve a smaller version of the same problem. It stops at a base case.

    Factorial using recursion:

    ```c
    #include <stdio.h>

    long long fact(int n) {
        if (n == 0 || n == 1)
            return 1;              // base case
        return n * fact(n - 1);    // recursive case
    }

    int main() {
        int n;
        scanf("%d", &n);
        printf("Factorial = %lld", fact(n));
        return 0;
    }
    ```

    - Working for n = 4: fact(4) = 4 × fact(3) = 4 × 3 × fact(2) = 4 × 3 × 2 × fact(1) = 24.
    - Time complexity O(n) and stack space O(n).
    - Without the base case, the function would call itself forever and cause a stack overflow.
26. **Given an integer number the following C program finds the sum of the digits of the number using recursion. You need to complete the recursive function in the following program. So that it does the intended task.** *[BTCL Assistant Manager (Technical) 2021 compact it 764 (ET: BUET)]*
```c
#include<stdio.h>
int someDigits(int num) {
    if(num==0)
        return 0;
    else
        return num%10+sumDigits(num/10);
}
int main() {
    int n;
    scanf("%d",&n);
    printf("%d", sumDigits(n));
    return 0;
}
```


    Answer: The program has a naming mistake. The function is defined as `someDigits`, but it is called as `sumDigits`. So the code will not compile.

    Corrected program:

    ```c
    #include <stdio.h>

    int sumDigits(int num) {
        if (num == 0)
            return 0;
        else
            return num % 10 + sumDigits(num / 10);
    }

    int main() {
        int n;
        scanf("%d", &n);
        printf("%d", sumDigits(n));
        return 0;
    }
    ```

    - The only change needed is to rename the function definition from `someDigits` to `sumDigits`, so that the definition and the call match.
    - The recursive logic itself is already correct: it takes the last digit with `num % 10` and passes the remaining number as `num / 10`.
    - Base case `num == 0` stops the recursion.
27. **(b) Write down a pseudocode/program to generate all possible permutation for a given word.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 793 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    #include <string.h>

    void swap(char *a, char *b) {
        char t = *a; *a = *b; *b = t;
    }

    void permute(char *s, int l, int r) {
        int i;
        if (l == r) {
            printf("%s\n", s);
            return;
        }
        for (i = l; i <= r; i++) {
            swap(s + l, s + i);
            permute(s, l + 1, r);
            swap(s + l, s + i);        // backtrack
        }
    }

    int main() {
        char s[] = "ABC";
        permute(s, 0, strlen(s) - 1);
        return 0;
    }
    ```

    - We fix each character at the current position in turn. Then we permute the rest of the string by recursion.
    - The second swap puts the original order back. This is the backtracking step.
    - For "ABC" the output is ABC, ACB, BAC, BCA, CBA, CAB.
    - Time complexity O(n × n!), because there are n! permutations and printing each costs O(n).
28. **Paython এ Recursive function ব্যবহার করে একটি ধনাত্মক সংখ্যার factorial মান বের করার function লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 866 (ET: BUET)]*


    Answer:

    ```python
    def factorial(n):
        if n == 0 or n == 1:
            return 1
        return n * factorial(n - 1)

    n = int(input("Enter a positive number: "))
    print("Factorial =", factorial(n))
    ```

    - Base case: factorial of 0 and 1 is 1.
    - Recursive case: n! = n × (n−1)!
    - For n = 5 the result is 120, and the time complexity is O(n).
29. **Write a program in C/Java to find out the factorial of a number using recursion also write its iterative program.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*


    Answer:

    Recursive version:
    ```c
    long long factRec(int n) {
        if (n <= 1) return 1;
        return n * factRec(n - 1);
    }
    ```

    Iterative version:
    ```c
    long long factIter(int n) {
        long long f = 1;
        for (int i = 2; i <= n; i++)
            f *= i;
        return f;
    }
    ```

    Comparison:
    - Both give the same result and both run in O(n) time.
    - The recursive version uses O(n) stack space. The iterative version uses only O(1).
    - The recursive code is shorter and closer to the maths definition. But the iterative code is faster, and it is safe from stack overflow for large n.
30. **১. পাইথন প্রোগ্রামিং এর রিকার্সিভ ফাংশন ব্যবহার করে ১০টি সংখ্যার যোগফল বের করার প্রোগ্রাম লিখ।** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 946 (ET: BUET)]*


    Answer:

    ```python
    def total(numbers, i=0):
        if i == len(numbers):
            return 0
        return numbers[i] + total(numbers, i + 1)

    nums = [int(input()) for _ in range(10)]
    print("Sum =", total(nums))
    ```

    - Base case: when the index reaches the end of the list, we return 0.
    - Recursive case: we add the current element to the sum of the remaining elements.
    - Time complexity O(n) and recursion depth O(n), which is 10 here.
31. **(ii) Recursion কী? Recursion পদ্ধতির একটি Simple C-programming এর Code লিখুন।** *[BPSC Assistant Network Engineer 2020 compact it 954 (ET: N/A)]*


    Answer: Recursion is the process where a function calls itself to solve a smaller version of the same problem. It must always have a base case that stops the calls.

    Simple C code:

    ```c
    #include <stdio.h>

    int sum(int n) {
        if (n == 0) return 0;      // base case
        return n + sum(n - 1);     // recursive case
    }

    int main() {
        printf("Sum = %d", sum(5));
        return 0;
    }
    ```

    - sum(5) = 5 + sum(4) = 5 + 4 + sum(3) and so on down to sum(0) = 0.
    - The final result is 5 + 4 + 3 + 2 + 1 = 15.
    - Time complexity O(n) and stack space O(n).
32. **Usually, recursion involves a function calling itself until specified condition is met and it is very useful to find out the factorial. Write a recursive algorithm to find the factorial of a number.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 985 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>
    
    long long factorial(int n) {
        if (n == 0 || n == 1)
            return 1;
        return n * factorial(n - 1);
    }
    
    int main() {
        int n;
        scanf("%d", &n);
        printf("Factorial of %d = %lld", n, factorial(n));
        return 0;
    }
    ```

    - Base case: factorial of 0 and 1 is 1. This stops the recursion.
    - Recursive case: n! = n × (n−1)!. So the problem gets smaller by one each time.
    - For n = 5 the calls unwind as 1, 2, 6, 24, 120.
    - Time complexity O(n) and stack space O(n).

## Operators, Data Types & Language Concepts (17)

1. **(b) What is the difference between sizeof c+1 and sizeof (c+1)?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 483 (ET: N/A)]*


   Answer: The two forms differ because `sizeof` is an operator, not a function.

   - `sizeof c + 1` is read as `(sizeof c) + 1`, because `sizeof` binds tighter than `+`. So we get the size of c first, and then add 1. If c is a char, the result is 1 + 1 = 2.
   - `sizeof (c + 1)` finds the size of the whole expression `c + 1`. Because of integer promotion, `c + 1` becomes an int. So the result is the size of an int, normally 4.
   - So for `char c`, the first gives 2 and the second gives 4.
2. **What is the difference between Null and Void?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*


   Answer:

   | Point | NULL | void |
   |---|---|---|
   | What it is | A macro representing a null pointer constant, value 0 | A data type keyword meaning no type or no value |
   | Where used | Assigned to pointers, `int *p = NULL;` | Return type, parameter list or generic pointer |
   | Defined in | `stddef.h`, also available via `stdio.h` | Built into the language |
   | Meaning | The pointer points to nothing | The function returns nothing, or the pointer type is unspecified |
   | Example | `if (p == NULL)` | `void display(void)` or `void *ptr` |

   - `void *` is a general pointer. It can hold the address of any data type. But we cannot read its value without a cast first.
3. **What can be used to terminate for(;;)?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*


   Answer: `for(;;)` is an infinite loop. The condition part is empty, so C treats it as always true. We can stop it in these ways.

   - `break;` leaves the loop at once. Control goes to the statement after it. This is the normal way.
   - `return;` leaves the whole function, so the loop ends too.
   - `goto label;` jumps out of the loop to a labelled statement.
   - `exit(0);` stops the whole program.
   - Calling `abort()`, or anything that kills the process, also ends it. But that is not good programming practice.

   Example:
   ```c
   for(;;) {
       scanf("%d", &n);
       if (n == 0) break;
       printf("%d\n", n);
   }
   ```
4. **What will occur when an array is declared without size?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*


   Answer: It depends on whether we give the array values at the same time.

   - If we declare it with a value list, such as `int a[] = {1, 2, 3, 4};`, the compiler counts the values and sets the size itself. Here the size is 4. This is fully valid.
   - If we declare it with no size and no values, such as `int a[];`, it is an incomplete type. Inside a function this gives a compile time error.
   - Outside all functions, `int a[];` is a tentative definition. The compiler may take the size as 1. But this is bad practice.
   - As a function parameter, `void f(int a[])` is allowed. The array turns into a pointer there, so the size is not needed.
5. **(ক) Local variable এবং Global variable এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 601 (ET: N/A)]*


   Answer:

   | Point | Local variable | Global variable |
   |---|---|---|
   | Where declared | Inside a function or block | Outside all functions |
   | Scope | Only within that function or block | Throughout the whole program |
   | Lifetime | Created on entry, destroyed on exit | Exists for the entire run of the program |
   | Default value | Garbage if not initialised | Automatically initialised to 0 |
   | Storage | Stack | Data segment |
   | Access from other functions | Not possible | Possible |
   | Safety | Safer, no accidental modification | Risky, any function can change it |

   - We prefer local variables, because a change stays inside one function. That makes debugging much easier.
6. **(খ) আমি কী ৩২৬৭৮ মান সংরক্ষণ করতে ‘int’ ডাটা টাইপ ব্যবহার করতে পারি? না পারলে কেন?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 617 (ET: N/A)]*


   Answer: Yes, 32678 can be stored in an `int`, but it cannot be stored in a `short int` on most systems.

   - A 2 byte signed integer holds values from −32768 to 32767. 32678 is smaller than 32767, so it fits.
   - On modern compilers `int` is 4 bytes. Its range is about −2.1 billion to +2.1 billion. So there is no problem at all.
   - If the value were 32768 or more, and we used a 2 byte `short int`, we would get overflow. The stored value would wrap around to a negative number.
   - For such larger values we should use `long int` or `unsigned int`.
7. **(গ) ‘++i’ এবং ‘i++’ অভিব্যক্তি দুটির মধ্যে পার্থক্য কী? উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 617 (ET: N/A)]*


   Answer:

   | Point | ++i (pre-increment) | i++ (post-increment) |
   |---|---|---|
   | When the value changes | Increments first, then the value is used | The old value is used first, then it increments |
   | Value of the expression | The new value | The old value |
   | Example with i = 5 | `x = ++i;` gives x = 6, i = 6 | `x = i++;` gives x = 5, i = 6 |

   - As a statement on its own, `i++;` and `++i;` do the same thing. The difference matters only when we use the value inside an expression.
8. **What is the main difference between structure and array in C programming? Explain with examples.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 635 (ET: N/A)]*


   Answer:

   | Point | Array | Structure |
   |---|---|---|
   | Data type of members | All elements must be of the same type | Members may be of different types |
   | Declaration | `int a[5];` | `struct student { int roll; char name[20]; float cgpa; };` |
   | Memory | Elements are stored in contiguous memory | Members are stored together but may have padding between them |
   | Access | By index, `a[2]` | By member name using dot, `s.roll` |
   | Size | size of one element × number of elements | sum of member sizes plus padding |
   | Assignment | Cannot copy one whole array with `=` | One structure can be assigned to another with `=` |
   | Use | A list of similar values, such as marks of 50 students | A record of one entity, such as one student's full information |

   - We can use them together: `struct student s[50];` is an array of structures, holding the records of 50 students.
9. **Difference between array and structure data type.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 679 (ET: N/A)]*


   Answer:

   | Point | Array | Structure |
   |---|---|---|
   | Data type of members | All elements must be of the same type | Members may be of different types |
   | Declaration | `int a[5];` | `struct student { int roll; char name[20]; float cgpa; };` |
   | Memory | Elements are stored in contiguous memory | Members are stored together but may have padding between them |
   | Access | By index, `a[2]` | By member name using dot, `s.roll` |
   | Size | size of one element × number of elements | sum of member sizes plus padding |
   | Assignment | Cannot copy one whole array with `=` | One structure can be assigned to another with `=` |
   | Use | A list of similar values, such as marks of 50 students | A record of one entity, such as one student's full information |
10. **Write down the types of errors which can occur the execution of a program.** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*


    Answer: A program can have these types of error.

    - Syntax errors: we break the grammar rules of the language. Example: a missing semicolon or an unmatched brace. The compiler catches them, and the program does not compile.
    - Semantic errors: the syntax is right but the meaning is wrong. Example: using a variable we never declared, or assigning the wrong type.
    - Linker errors: the code compiles, but a needed function or symbol is not found. Example: a wrong `main` signature, or a missing library.
    - Runtime errors: these show up while the program is running. Example: division by zero, array index out of range, using a null pointer, or stack overflow.
    - Logical errors: the program runs and gives output, but the output is wrong, because the algorithm itself is wrong. These are the hardest to find, because the compiler says nothing.
11. **Write the syntax of while and do while loop.** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*


    Answer:

    while loop:
    ```c
    while (condition) {
        statements;
    }
    ```

    do-while loop:
    ```c
    do {
        statements;
    } while (condition);
    ```

    - The while loop checks the condition before running the body. So the body may run zero times.
    - The do-while loop checks the condition after running the body. So the body always runs at least once.
    - Note: in the do-while form, the semicolon after `while (condition)` is compulsory.
12. **What is nested structure in C programming? Explain with example.** *[SPCB Sub-Assistant Programmer 2022 compact it 741 (ET: N/A)]*


    Answer: A nested structure is a structure that holds another structure as one of its members. We use it when one record naturally holds a smaller record inside it.

    Example:
    ```c
    #include <stdio.h>

    struct Date {
        int day, month, year;
    };

    struct Employee {
        int id;
        char name[30];
        struct Date joining;      // nested structure
    };

    int main() {
        struct Employee e = {101, "Rahim", {15, 7, 2020}};
        printf("%s joined on %d-%d-%d",
               e.name, e.joining.day, e.joining.month, e.joining.year);
        return 0;
    }
    ```

    - We reach the inner member with two dots, like `e.joining.day`.
    - We must declare the inner structure before we use it inside the outer one.
    - Nesting keeps related data together in a logical way, and makes the code easier to read.
13. **(ii) C Programming Language এ Array and Structure এর মধ্যে পার্থক্য লিখুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 784 (ET: N/A)]*


    Answer:

    | Point | Array | Structure |
    |---|---|---|
    | Data type of members | All elements must be of the same type | Members may be of different types |
    | Declaration | `int a[5];` | `struct student { int roll; char name[20]; float cgpa; };` |
    | Memory | Elements are stored in contiguous memory | Members are stored together but may have padding between them |
    | Access | By index, `a[2]` | By member name using dot, `s.roll` |
    | Size | size of one element × number of elements | sum of member sizes plus padding |
    | Assignment | Cannot copy one whole array with `=` | One structure can be assigned to another with `=` |
    | Use | A list of similar values, such as marks of 50 students | A record of one entity, such as one student's full information |
14. **Write some default data type in C.** *[BCC CA Monitoring System Project 2021 compact it 830 (ET: N/A)]*


    Answer: C has these basic data types.

    - `int` — whole numbers, normally 4 bytes, range about −2,147,483,648 to 2,147,483,647, specifier `%d`.
    - `char` — a single character, 1 byte, range −128 to 127, specifier `%c`.
    - `float` — single precision real number, 4 bytes, about 6 decimal digits of precision, specifier `%f`.
    - `double` — double precision real number, 8 bytes, about 15 decimal digits, specifier `%lf`.
    - `void` — means there is no value. We use it for functions that return nothing.

    - We can change their size or range with `short`, `long`, `signed` and `unsigned`. Example: `unsigned int` or `long double`.
15. **Write the difference between Structure and Array.** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922 (ET: N/A)]*


    Answer:

    | Point | Array | Structure |
    |---|---|---|
    | Data type of members | All elements must be of the same type | Members may be of different types |
    | Declaration | `int a[5];` | `struct student { int roll; char name[20]; float cgpa; };` |
    | Memory | Elements are stored in contiguous memory | Members are stored together but may have padding between them |
    | Access | By index, `a[2]` | By member name using dot, `s.roll` |
    | Size | size of one element × number of elements | sum of member sizes plus padding |
    | Assignment | Cannot copy one whole array with `=` | One structure can be assigned to another with `=` |
    | Use | A list of similar values, such as marks of 50 students | A record of one entity, such as one student's full information |
16. **Short question: (i) Difference between ++i and i++ (ii) Difference between Overloading and Overriding (iii) Polymorphism in Java (iv) String variable (v) Control structure in C programming (vi) Stack (vii) Debugging (viii) Increment and Decrement process in C programming (ix) Object in C++ (x) Data encapsulation** *[National University Assistant Programmer 2020 compact it 978-980 (ET: DU)]*


    Answer:

    (i) Difference between ++i and i++

    | Point | ++i | i++ |
    |---|---|---|
    | Order | Increments first, then uses the value | Uses the old value first, then increments |
    | Expression value | The new value | The old value |
    | With i = 5 | `x = ++i` gives x = 6 | `x = i++` gives x = 5 |

    (ii) Difference between Overloading and Overriding

    | Point | Overloading | Overriding |
    |---|---|---|
    | Definition | Same function name with different parameter lists in the same class | A derived class redefines a base class function with the same signature |
    | Binding | Compile time, also called static binding | Run time, also called dynamic binding |
    | Inheritance | Not required | Required |
    | Parameters | Must differ in number or type | Must be exactly the same |
    | Keyword in C++ | None needed | The base function should be `virtual` |

    (iii) Polymorphism

    - Polymorphism means one interface takes many forms. The same function name behaves differently, depending on the situation.
    - We get compile time polymorphism through function overloading and operator overloading.
    - We get run time polymorphism through function overriding, using virtual functions and base class pointers.
    - It is one of the four pillars of object oriented programming, along with encapsulation, inheritance and abstraction.
17. **নিচের if-else কে switch case এ পরিনত করুন। if(ch== 'A':: ch== 'E' :: ch== 'I' :: ch == 'O':: ch== 'U')** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1021 (ET: N/A)]*


    Answer: The if-else checks whether the character is a vowel. In the switch-case version, we let all the vowel cases fall through to one common statement.

    ```c
    switch (ch) {
        case 'A':
        case 'E':
        case 'I':
        case 'O':
        case 'U':
            printf("It is a vowel");
            break;
        default:
            printf("It is not a vowel");
            break;
    }
    ```

    - Cases 'A' to 'O' have no `break`. So control falls through to the statement written under 'U'. This is how we write an OR condition in a switch.
    - `default` does the job of the `else` part.
    - To handle small letters too, we can add the cases 'a', 'e', 'i', 'o', 'u' in the same fall through group.

## Flowcharts & Algorithms (12)

1. **Draw and clearly describe a step-by-step flowchart for a User Login system. Your login must include: Taking a Username and Password as input. Checking the database. If correct: Granting access. If wrong: Adding 1 to a failed attempt counter. Access denied and block the account if the counter reaches 3.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*


   Answer:

   Algorithm:
   - Step 1: Start.
   - Step 2: Set attempt counter to 0.
   - Step 3: Take username and password as input.
   - Step 4: Check the pair against the database.
   - Step 5: If correct, grant access and stop.
   - Step 6: If wrong, increase the counter by 1.
   - Step 7: If counter is less than 3, show "invalid credentials" and go back to Step 3.
   - Step 8: If counter reaches 3, deny access, block the account and stop.

   ```mermaid
   flowchart TD
       A([Start]) --> B[Set attempt = 0]
       B --> C[/Input username and password/]
       C --> D{Match found in database?}
       D -- Yes --> E[Grant access]
       E --> Z([End])
       D -- No --> F[attempt = attempt + 1]
       F --> G{attempt >= 3?}
       G -- No --> H[Show invalid credentials]
       H --> C
       G -- Yes --> I[Deny access and block account]
       I --> Z
   ```

   - The counter is the key part, because it enforces the limit of three attempts.
   - Blocking the account after three failures stops brute force password guessing.
2. **Draw a Flow chart for print odd number for 1 to N.** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*


   Answer:

   ```mermaid
   flowchart TD
       A([Start]) --> B[/Read N/]
       B --> C[i = 1]
       C --> D{i <= N?}
       D -- No --> Z([End])
       D -- Yes --> E{i mod 2 != 0?}
       E -- Yes --> F[/Print i/]
       F --> G[i = i + 1]
       E -- No --> G
       G --> D
   ```

   - The decision box `i mod 2 != 0` picks only the odd numbers.
   - A simpler version starts i at 1 and adds 2 each time. Then we do not need the modulus test at all.
3. **১ থেকে ১০০ পর্যন্ত নাম্বার প্রদর্শনের ফ্লোচার্ট আক।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 381 (ET: BUET)]*


   Answer:

   ```mermaid
   flowchart TD
       A([Start]) --> B[i = 1]
       B --> C{i <= 100?}
       C -- No --> Z([End])
       C -- Yes --> D[/Print i/]
       D --> E[i = i + 1]
       E --> C
   ```

   - The counter i starts at 1 and increases by 1 on each pass.
   - The loop ends when i goes past 100. So exactly 100 numbers are printed.
4. **দুইটি সংখ্যার গ.সা.গু নির্ণয়ের জন্য ফ্লোচার্ট অঙ্কন করুন ও অ্যালগরিদম লিখুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 406 (ET: N/A)]*


   Answer:

   Algorithm to find GCD by the Euclidean method:
   - Step 1: Start.
   - Step 2: Read two numbers A and B.
   - Step 3: If B is 0, then A is the GCD, so print A and stop.
   - Step 4: Set R = A mod B.
   - Step 5: Set A = B and B = R.
   - Step 6: Go back to Step 3.
   - Step 7: Stop.

   ```mermaid
   flowchart TD
       A([Start]) --> B[/Read A and B/]
       B --> C{B = 0?}
       C -- Yes --> D[/Print A as GCD/]
       D --> Z([End])
       C -- No --> E[R = A mod B]
       E --> F[A = B]
       F --> G[B = R]
       G --> C
   ```

   - Example with A = 48 and B = 18: R = 12, then A = 18 and B = 12; next R = 6, A = 12, B = 6; next R = 0, A = 6, B = 0, so the GCD is 6.
   - The Euclidean method runs in O(log min(A,B)) steps.
5. **Write Algorithm and flowchart to find odd numbers between 1 to n where n is a positive integer.** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 596 (ET: N/A)]*


   Answer:

   Algorithm:
   - Step 1: Start.
   - Step 2: Read n.
   - Step 3: Set i = 1.
   - Step 4: If i > n, go to Step 8.
   - Step 5: Print i.
   - Step 6: Set i = i + 2.
   - Step 7: Go to Step 4.
   - Step 8: Stop.

   ```mermaid
   flowchart TD
       A([Start]) --> B[/Read n/]
       B --> C[i = 1]
       C --> D{i <= n?}
       D -- No --> Z([End])
       D -- Yes --> E[/Print i/]
       E --> F[i = i + 2]
       F --> D
   ```

   - If we start at 1 and step by 2, we get only odd numbers. So we do not need a modulus test.
6. **Write Algorithm and flowchart for printing 1+3+5+ \dots + N.** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 643 (ET: BUET)]*


   Answer:

   Algorithm:
   - Step 1: Start.
   - Step 2: Read N.
   - Step 3: Set i = 1 and sum = 0.
   - Step 4: If i > N, go to Step 8.
   - Step 5: sum = sum + i.
   - Step 6: i = i + 2.
   - Step 7: Go to Step 4.
   - Step 8: Print sum and stop.

   ```mermaid
   flowchart TD
       A([Start]) --> B[/Read N/]
       B --> C[i = 1, sum = 0]
       C --> D{i <= N?}
       D -- Yes --> E[sum = sum + i]
       E --> F[i = i + 2]
       F --> D
       D -- No --> G[/Print sum/]
       G --> Z([End])
   ```

   - The sum of the first k odd numbers is k². We can use this to check our result.
7. **Write an Algorithm to check a number is Prime or not Prime.** *[NSDA Assistant Programmer Date: 04-03-2022 compact it 656 (ET: N/A)]*


   Answer:

   Algorithm to check whether a number is prime:
   - Step 1: Start.
   - Step 2: Read the number N.
   - Step 3: If N is less than 2, print "Not prime" and stop.
   - Step 4: Set i = 2 and flag = 1.
   - Step 5: If i × i > N, go to Step 9.
   - Step 6: If N mod i = 0, set flag = 0 and go to Step 9.
   - Step 7: i = i + 1.
   - Step 8: Go to Step 5.
   - Step 9: If flag = 1 print "Prime", otherwise print "Not prime".
   - Step 10: Stop.

   - Checking divisors only up to √N is enough. If N = a × b, then one of the two factors must be less than or equal to √N.
   - Time complexity is O(√N).
8. **Write down the algorithm and draw the flowchart of Quadratic equation.** *[CAAB Programmer 2022 compact it 722 (ET: N/A)]*


   Answer:

   Algorithm for the quadratic equation ax² + bx + c = 0:
   - Step 1: Start.
   - Step 2: Read a, b and c.
   - Step 3: If a = 0, the equation is not quadratic, so print a message and stop.
   - Step 4: Compute D = b² − 4ac.
   - Step 5: If D > 0, roots are real and distinct: r1 = (−b + √D)/2a, r2 = (−b − √D)/2a.
   - Step 6: If D = 0, roots are real and equal: r = −b/2a.
   - Step 7: If D < 0, roots are imaginary: real part = −b/2a, imaginary part = √(−D)/2a.
   - Step 8: Print the roots and stop.

   ```mermaid
   flowchart TD
       A([Start]) --> B[/Read a, b, c/]
       B --> C[D = b*b - 4*a*c]
       C --> D{D > 0?}
       D -- Yes --> E[/Print two real distinct roots/]
       D -- No --> F{D = 0?}
       F -- Yes --> G[/Print equal roots/]
       F -- No --> H[/Print imaginary roots/]
       E --> Z([End])
       G --> Z
       H --> Z
   ```

   - The discriminant D tells us which of the three cases we have.
9. **Draw a flowchart and write algorithm for finding Factorial value of an integer number.** *[CAAB Assistant Maintenance Engineer (AME) 2022 compact it 723 (ET: N/A)]*


   Answer:

   Algorithm:
   - Step 1: Start.
   - Step 2: Read N.
   - Step 3: Set fact = 1 and i = 1.
   - Step 4: If i > N, go to Step 8.
   - Step 5: fact = fact × i.
   - Step 6: i = i + 1.
   - Step 7: Go to Step 4.
   - Step 8: Print fact and stop.

   ```mermaid
   flowchart TD
       A([Start]) --> B[/Read N/]
       B --> C[fact = 1, i = 1]
       C --> D{i <= N?}
       D -- Yes --> E[fact = fact * i]
       E --> F[i = i + 1]
       F --> D
       D -- No --> G[/Print fact/]
       G --> Z([End])
   ```

   - For N = 0 the loop never runs. So fact stays 1, which is the correct value of 0 factorial.
10. **Draw a flowchart of the following series: 1+3+5+7+\dots+N** *[CAAB Assistant Programmer (AP) 2022 compact it 725 (ET: N/A)]*


    Answer:

    ```mermaid
    flowchart TD
        A([Start]) --> B[/Read N/]
        B --> C[i = 1, sum = 0]
        C --> D{i <= N?}
        D -- Yes --> E[sum = sum + i]
        E --> F[i = i + 2]
        F --> D
        D -- No --> G[/Print sum/]
        G --> Z([End])
    ```

    - The variable i starts at 1 and goes up by 2. So we add only the odd terms 1, 3, 5, 7.
    - The loop stops as soon as i goes past N.
11. **(খ) Algorithm কি? Algorithm প্রকাশের তিনটি পদ্ধতির নাম লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 770 (ET: N/A)]*


    Answer: An algorithm is a limited, ordered set of clear steps that solves a problem or does a computation.

    Properties of a good algorithm:
    - Finiteness: it must stop after a limited number of steps.
    - Definiteness: every step must be clear, with only one meaning.
    - Input and output: zero or more inputs and at least one output.
    - Effectiveness: every operation must be simple enough to actually do.

    Three ways of expressing an algorithm:
    - Pseudocode: a structured description in English like words. It is close to code, but not tied to any one language.
    - Flowchart: a diagram using standard symbols such as oval for start and end, parallelogram for input and output, rectangle for process and diamond for decision.
    - Programming language code: we write the algorithm directly in C, Java, Python or another language.
12. **Three types of control statements and their graphical presentation using flowchart or flow graph.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1037-1038 (ET: BUET)]*


    Answer: The three basic control structures of structured programming are sequence, selection and iteration.

    Sequence: the statements run one after another, in the order we wrote them.
    ```mermaid
    flowchart TD
        A([Start]) --> B[Statement 1]
        B --> C[Statement 2]
        C --> Z([End])
    ```

    Selection: a condition decides which path we take. We use if, if-else or switch.
    ```mermaid
    flowchart TD
        A([Start]) --> B{Condition?}
        B -- True --> C[Statement A]
        B -- False --> D[Statement B]
        C --> Z([End])
        D --> Z
    ```

    Iteration: a block repeats as long as a condition is true. We use for, while or do-while.
    ```mermaid
    flowchart TD
        A([Start]) --> B{Condition?}
        B -- True --> C[Loop body]
        C --> B
        B -- False --> Z([End])
    ```

    - We can write any program, however complex, using only these three structures. This is what the structured programming theorem says.

## String Manipulation & Algorithms (11)

1. **Write a C or Java program to convert string to integer without using any built-in function.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1362 (ET: BUET)]*


   Answer:

   ```c
   #include <stdio.h>
   
   int strToInt(char s[]) {
       int i = 0, sign = 1, num = 0;
       if (s[0] == '-') { sign = -1; i = 1; }
       for (; s[i] != '\0'; i++)
           num = num * 10 + (s[i] - '0');
       return sign * num;
   }
   
   int main() {
       char s[] = "-1234";
       printf("%d", strToInt(s));
       return 0;
   }
   ```

   - If we subtract the character '0', a digit character turns into its number value.
   - We multiply the running number by 10 first, then add the new digit.
   - We handle a minus sign at the front separately. Time complexity O(n).
2. **Write a C program to check whether a string is a Palindrome.** *[BUET Assistant Programmer 21.06.2025 compact it 1433 (ET: BUET)]*


   Answer:

   ```c
   #include <stdio.h>
   
   int main() {
       char s[100];
       int i = 0, j, flag = 1;
       scanf("%s", s);
       while (s[i] != '\0') i++;
       j = i - 1;
       for (i = 0; i < j; i++, j--)
           if (s[i] != s[j]) { flag = 0; break; }
       printf(flag ? "Palindrome" : "Not a palindrome");
       return 0;
   }
   ```

   - Two indexes start at the two ends and move towards the middle, comparing characters.
   - If any pair does not match, the string is not a palindrome. Time complexity O(n).
3. **Write a C program upper case to lower case conversion.** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 475 (ET: N/A)]*


   Answer:

   ```c
   #include <stdio.h>
   
   int main() {
       char s[100];
       int i;
       scanf("%s", s);
       for (i = 0; s[i] != '\0'; i++)
           if (s[i] >= 'A' && s[i] <= 'Z')
               s[i] = s[i] + 32;
       printf("%s", s);
       return 0;
   }
   ```

   - In ASCII, a small letter is exactly 32 more than the capital letter. So adding 32 changes the case.
   - We leave every character that is not a capital letter as it is.
4. **String reverse program but without without using the library function.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 660 (ET: N/A)], [BREB Assistant Programmer 18.02.2023 compact it 468 (ET: N/A)]*


   Answer:

   ```c
   #include <stdio.h>
   
   int main() {
       char s[100], t;
       int i = 0, j;
       scanf("%s", s);
       while (s[i] != '\0') i++;
       j = i - 1;
       for (i = 0; i < j; i++, j--) {
           t = s[i];
           s[i] = s[j];
           s[j] = t;
       }
       printf("%s", s);
       return 0;
   }
   ```

   - We find the length by counting characters until the null terminator.
   - We swap the characters in place from both ends. So we need no extra array. Space complexity O(1).
5. **Write a C program to remove given character from string: Example input: programming and we want to remove: gram now output: proming without having the gram from string.** *[RPGCL Assistant Manager (ICT) 2022 compact it 652 (ET: BUET)]*


   Answer:

   ```c
   #include <stdio.h>
   
   int main() {
       char s[100], r[50];
       int i, j, k = 0, found;
       scanf("%s %s", s, r);
       for (i = 0; s[i] != '\0'; i++) {
           found = 0;
           for (j = 0; r[j] != '\0'; j++)
               if (s[i] == r[j]) { found = 1; break; }
           if (!found) s[k++] = s[i];
       }
       s[k] = '\0';
       printf("%s", s);
       return 0;
   }
   ```

   - We check every character of the main string against the set of characters to remove.
   - Any character that is not in the removal set is written back at index k. This packs the string in place.
   - For input programming and gram, the output is ponin.
6. **Write a program IPv4 IP validation from given IP with valid and not valid.** *[RPGCL Assistant Manager (ICT) 2022 compact it 653 (ET: BUET)]*


   Answer:

   ```c
   #include <stdio.h>
   #include <string.h>
   
   int main() {
       char ip[50];
       int a, b, c, d, n;
       scanf("%s", ip);
       n = sscanf(ip, "%d.%d.%d.%d", &a, &b, &c, &d);
       if (n == 4 && a >= 0 && a <= 255 && b >= 0 && b <= 255 &&
           c >= 0 && c <= 255 && d >= 0 && d <= 255)
           printf("Valid IPv4 address");
       else
           printf("Not a valid IPv4 address");
       return 0;
   }
   ```

   - A valid IPv4 address has exactly four octets separated by dots.
   - Each octet must be between 0 and 255.
   - `sscanf` returns how many values it read. So a return of 4 confirms the format is right.
7. **Find occurrence of a Character in a string. String: Bangladesh is a big country. Sample Input: b, Output: 2 times Sample Input p, Output: Not foud this letter** *[BKSP Assistant Programmer 03.12.2022 compact it 729 (ET: N/A)]*


   Answer:

   ```c
   #include <stdio.h>
   
   int main() {
       char s[200], ch;
       int i, count = 0;
       fgets(s, 200, stdin);
       scanf("%c", &ch);
       for (i = 0; s[i] != '\0'; i++)
           if (s[i] == ch || s[i] == ch - 32 || s[i] == ch + 32)
               count++;
       printf("%c occurs %d times", ch, count);
       return 0;
   }
   ```

   - We scan the string once and count every match.
   - The extra checks with 32 make the search case insensitive. So we count both b and B.
   - For the sentence given and the character b, the answer is 2.
8. **What is the purpose of '\0' character in C?** *[BCC CA Monitoring System Project 2021 compact it 830 (ET: N/A)]*


   Answer: The character `'\0'`, called the null character, marks the end of a string in C.

   - C has no separate string type. A string is just an array of characters that ends with `'\0'`.
   - Library functions like `strlen()`, `strcpy()` and `printf("%s")` keep reading until they meet `'\0'`. Without it they would read past the array and give garbage, or crash.
   - Its ASCII value is 0. Do not mix it up with the character `'0'`, whose ASCII value is 48.
   - This is why the array must be one byte bigger than the text. To store "Hello" we need `char s[6]`.
9. **(c) Write down a program to find length of a string without using any library function.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 892 (ET: N/A)]*


   Answer:

   ```c
   #include <stdio.h>
   
   int strLength(char s[]) {
       int i = 0;
       while (s[i] != '\0') i++;
       return i;
   }
   
   int main() {
       char s[100];
       scanf("%s", s);
       printf("Length = %d", strLength(s));
       return 0;
   }
   ```

   - We count characters until we find the null terminator.
   - We do not count the null character itself. So "Hello" gives 5.
   - Time complexity O(n) and space complexity O(1).
10. **Write a program to read a character “lower case ” and convert it into upper case.** *[BAUST Assistant Programmer 2021 compact it 918-919 (ET: N/A)]*


    Answer:

    ```c
    #include <stdio.h>

    int main() {
        char ch;
        scanf("%c", &ch);
        if (ch >= 'a' && ch <= 'z')
            ch = ch - 32;
        printf("Uppercase: %c", ch);
        return 0;
    }
    ```

    - In ASCII a capital letter is 32 less than a small letter. So subtracting 32 changes the case.
    - The range check makes sure we do not change digits and symbols.
    - The library function `toupper()` from `ctype.h` does the same job.
11. **Given a IPv4 address string, write C/C++/JAVA code to show the class the IP address belongs to.** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 923-924 (ET: CTI)]*
   Sample Input: 192.168.0.0
   Sample Output: Class C


    Answer:

    ```c
    #include <stdio.h>

    int main() {
        char ip[50];
        int a, b, c, d;
        scanf("%s", ip);
        sscanf(ip, "%d.%d.%d.%d", &a, &b, &c, &d);

        if (a >= 1 && a <= 126)        printf("Class A");
        else if (a >= 128 && a <= 191) printf("Class B");
        else if (a >= 192 && a <= 223) printf("Class C");
        else if (a >= 224 && a <= 239) printf("Class D (Multicast)");
        else if (a >= 240 && a <= 255) printf("Class E (Reserved)");
        else                           printf("Invalid or loopback address");

        return 0;
    }
    ```

    - The first octet alone decides the class.
    - We skip 127, because 127.x.x.x is reserved for loopback.
    - Example: 192.168.1.1 falls in the range 192 to 223, so it is Class C.

## File Handling (4)

1. Name Top C 5 File Management Function Name. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*


   Answer: These are the five file management functions we use most in C.

   - `fopen()` — opens a file and returns a FILE pointer. Modes are "r" read, "w" write, "a" append, and the b suffix for binary.
   - `fclose()` — closes an open file and pushes the buffer out to disk.
   - `fprintf()` / `fscanf()` — write formatted data to a file and read formatted data from it.
   - `fgets()` / `fputs()` — read a line from a file and write a string to a file.
   - `fread()` / `fwrite()` — read and write blocks of binary data.

   - Other useful ones: `fseek()` moves the file pointer, `ftell()` tells the current position, and `rewind()` goes back to the beginning.
2. **Write a function in Python programming language which takes a filename as parameter, orders first 10 line in output.** *[BCC Assistant Programmer 12.02.2021 compact it 814 (ET: BUET)]*


   Answer:

   ```python
   def first_ten_sorted(filename):
       with open(filename, 'r') as f:
           lines = f.readlines()
       lines.sort()
       for line in lines[:10]:
           print(line.rstrip())

   first_ten_sorted("data.txt")
   ```

   - `readlines()` reads every line of the file into a list.
   - `sort()` puts the lines in increasing alphabetical order.
   - Slicing with `[:10]` takes only the first ten lines. `rstrip()` removes the newline at the end.
   - For a very large file, it is better to read line by line and keep only the ten smallest. That saves memory.
3. **You have a file name accounts.txt which contain the following information. Now write a C/C++/Java program to find the following: Total balance of saving account, Find the highest and second highest balance of saving account.** *[NRCC Assistant Programmer 2021 compact it 931-932 (ET: N/A)]*


   Answer:

   ```c
   #include <stdio.h>

   int main() {
       FILE *fp;
       char name[50];
       int acc;
       float balance, maxBal = -1;
       char maxName[50];

       fp = fopen("accounts.txt", "r");
       if (fp == NULL) {
           printf("File cannot be opened");
           return 1;
       }

       while (fscanf(fp, "%d %s %f", &acc, name, &balance) == 3) {
           if (balance > maxBal) {
               maxBal = balance;
               for (int i = 0; name[i] != '\0'; i++) maxName[i] = name[i];
           }
           printf("%d %s %.2f\n", acc, name, balance);
       }

       fclose(fp);
       printf("Highest balance: %s with %.2f", maxName, maxBal);
       return 0;
   }
   ```

   - We open the file in read mode and check the return value, because `fopen` gives NULL if the file is missing.
   - `fscanf` returns how many items it read. So comparing that with 3 is a safe way to find the end of the file.
   - We track the largest balance while reading. So we need only one pass over the file.
   - `fclose` is a must, to release the file handle.
4. **Folder থেকে একটি Image নিয়ে ঐ Image এর নামের .jpeg extention কে .png extention এ convert করার জন্য Python language এর Function লিখুন?** *[PGCB Sub-Assistant Engineer (CSE) 2020 compact it 1046 (ET: BUET)]*


   Answer:

   ```python
   from PIL import Image
   import os

   def jpeg_to_png(folder, filename):
       path = os.path.join(folder, filename)
       img = Image.open(path)
       new_name = os.path.splitext(filename)[0] + ".png"
       img.save(os.path.join(folder, new_name), "PNG")
       print("Converted to", new_name)

   jpeg_to_png("images", "photo.jpeg")
   ```

   - We use the Pillow library. Install it with `pip install pillow`.
   - `Image.open()` reads the JPEG. Then `save()` with the format "PNG" writes the converted file.
   - `os.path.splitext()` splits the name from the extension. So the base name stays the same.
   - Just renaming the file would not work. JPEG and PNG use different compression formats inside.

## Pointers (4)

1. **অথবা, (ক) Pointer কী? Pointer ব্যবহারের সুবিধাগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 600 (ET: N/A)]*


   Answer: A pointer is a variable that stores the memory address of another variable, instead of storing a value.

   Declaration and use:
   ```c
   int x = 10;
   int *p = &x;      // p holds the address of x
   printf("%d", *p); // dereferencing prints 10
   ```

   Advantages of using pointers:
   - Call by reference becomes possible. So a function can change the caller's variable.
   - We can do dynamic memory allocation with `malloc()` and `calloc()` only through pointers.
   - We can pass arrays, strings and structures to functions cheaply, because only an address is copied, not the whole data.
   - We cannot build data structures like linked lists, trees and graphs without pointers.
   - Direct access to memory makes some jobs faster.

   - Main risk: a wrong or uninitialised pointer causes a crash. So we should set a pointer to NULL when it points to nothing.
2. **(গ) পয়েন্টার কী? Malloc( ) এবং Calloc( ) এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*


   Answer: A pointer is a variable that holds the memory address of another variable.

   | Point | malloc() | calloc() |
   |---|---|---|
   | Full form | Memory allocation | Contiguous allocation |
   | Number of arguments | One, the total size in bytes | Two, the number of blocks and the size of each |
   | Syntax | `p = (int*)malloc(n * sizeof(int));` | `p = (int*)calloc(n, sizeof(int));` |
   | Initialisation | Memory contains garbage values | Memory is initialised to zero |
   | Speed | Faster, since no initialisation is done | Slightly slower because of the zero filling |
   | Use | When the values will be assigned immediately | When a clean zero filled block is needed |

   - Both return a `void*`, which we should cast. Both return NULL if the allocation fails.
   - We must release the memory from either one with `free()`, or the program leaks memory.
3. **Describe Dynamic memory allocation in programming in C?** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*


   Answer: Dynamic memory allocation means we ask for memory at run time from the heap, instead of fixing the size at compile time.

   Why it is needed:
   - Often we do not know the exact amount of data while writing the program.
   - A fixed array either wastes memory or runs short. Dynamic memory grows to the real need.

   Four functions, all declared in `stdlib.h`:
   - `malloc(size)` — gives a block of the given size, with garbage values inside.
   - `calloc(n, size)` — gives n blocks and fills them all with zero.
   - `realloc(ptr, newsize)` — changes the size of a block we already took, and keeps the old contents.
   - `free(ptr)` — gives the block back to the system.

   Example:
   ```c
   int n;
   scanf("%d", &n);
   int *a = (int*)malloc(n * sizeof(int));
   if (a == NULL) { printf("Allocation failed"); return 1; }
   for (int i = 0; i < n; i++) a[i] = i;
   free(a);
   ```

   - We must always check the return value for NULL.
   - We must free every block we take. Otherwise the program leaks memory.
4. **(a) What is the difference between array and pointer?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 891-892 (ET: N/A)]*


   Answer:

   | Point | Array | Pointer |
   |---|---|---|
   | What it is | A block of memory holding several elements | A variable holding one memory address |
   | Memory allocation | Static, fixed at compile time | Can point to static or dynamically allocated memory |
   | Value change | The array name is a constant, so `a = a + 1` is illegal | A pointer can be reassigned, `p = p + 1` is legal |
   | sizeof | Gives the total size of the array, for example 40 for `int a[10]` | Gives the size of the pointer itself, normally 8 |
   | Declaration | `int a[10];` | `int *p;` |
   | Relationship | The array name gives the address of the first element | A pointer can be made to point at an array with `p = a;` |

   - Because of this link, `a[i]` and `*(a + i)` mean exactly the same thing.
   - When we pass an array to a function, it turns into a pointer. That is why we must pass the size separately.

## Command Line Arguments & Basic Programs (1)

1. **Write a C program that takes inputs integer values from command line interface and print the summation of the integers.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1361 (ET: BUET)]*


   Answer:

   ```c
   #include <stdio.h>
   #include <stdlib.h>
   
   int main(int argc, char *argv[]) {
       int i, sum = 0;
   
       if (argc < 2) {
           printf("Usage: ./program num1 num2 ...");
           return 1;
       }
   
       for (i = 1; i < argc; i++)
           sum += atoi(argv[i]);
   
       printf("Sum = %d", sum);
       return 0;
   }
   ```

   - `argc` holds how many arguments there are, including the program name. `argv` holds them as strings.
   - We start counting at 1, because `argv[0]` is the program name itself.
   - `atoi()` from `stdlib.h` changes each argument string into an integer.
   - Running `./program 10 20 30` prints Sum = 60.
