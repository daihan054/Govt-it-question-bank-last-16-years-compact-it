<!-- TOC START -->
**Table of Contents** — 9 subtopics · 270 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Basic Programs & Control Statements](#basic-programs--control-statements-111) | 111 |
| 2 | [Output Tracing & Control Flow](#output-tracing--control-flow-57) | 57 |
| 3 | [Recursion & Functions](#recursion--functions-38) | 38 |
| 4 | [Operators, Data Types & Language Concepts](#operators-data-types--language-concepts-25) | 25 |
| 5 | [Flowcharts & Algorithms](#flowcharts--algorithms-16) | 16 |
| 6 | [String Manipulation & Algorithms](#string-manipulation--algorithms-14) | 14 |
| 7 | [File Handling](#file-handling-4) | 4 |
| 8 | [Pointers](#pointers-4) | 4 |
| 9 | [Command Line Arguments & Basic Programs](#command-line-arguments--basic-programs-1) | 1 |

<!-- TOC END -->

---

## Basic Programs & Control Statements (111)

1. **Write a C program to check the number in EVEN or ODD.** *[BCC CA Monitoring System Project 2021 compact it 830 (ET: N/A)], [BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

   Answer:

   ```c
   #include <stdio.h>

   int main(void) {
       int n;
       printf("Enter a number: ");
       scanf("%d", &n);

       if (n % 2 == 0)
           printf("%d is EVEN\n", n);
       else
           printf("%d is ODD\n", n);
       return 0;
   }
   ```

   - Logic: a number is even when it leaves remainder 0 on division by 2.
   - The bitwise form `if (n & 1)` is faster and also works for negative numbers, where `n % 2` can return −1 in C.

2. **Write a C/Java program to determine if a given year is a leap year nor not.** *[DPDC Junior Assistant Manager (JAM) 27.06.2025 compact it 1440 (ET: BUET)]*

   Answer:

   ```c
   #include <stdio.h>

   int main(void) {
       int year;
       printf("Enter a year: ");
       scanf("%d", &year);

       if ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0))
           printf("%d is a Leap Year\n", year);
       else
           printf("%d is not a Leap Year\n", year);
       return 0;
   }
   ```

   Leap year rule
   - Divisible by 4 → leap year, except
   - Divisible by 100 → not a leap year, except
   - Divisible by 400 → leap year again.
   - So 2024 is leap, 1900 is not (divisible by 100 but not 400), and 2000 is leap (divisible by 400).

3. **Write a structured program (in C or Python) that takes an integer input n and prints the sum of all even numbers from 1 to n.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1423 (ET: E-Zone)]*

   Answer:

   ```c
   #include <stdio.h>

   int sumOfEven(int n) {
       int i, sum = 0;
       for (i = 2; i <= n; i += 2)      // step by 2, so only even numbers
           sum += i;
       return sum;
   }

   int main(void) {
       int n;
       printf("Enter n: ");
       scanf("%d", &n);
       printf("Sum of even numbers from 1 to %d = %d\n", n, sumOfEven(n));
       return 0;
   }
   ```

   - For `n = 10` the output is `2 + 4 + 6 + 8 + 10 = 30`.
   - Time complexity `O(n)`. The direct formula `k(k+1)` where `k = n/2` gives the same answer in `O(1)`.

4. **(a) Difference between a while loop and do-while loop.** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1446 (ET: N/A)]*

   Answer:

   | Point | while loop | do-while loop |
   |---|---|---|
   | Control type | Entry controlled | Exit controlled |
   | Condition check | Checked first, then the body runs | Body runs first, then the condition is checked |
   | Minimum iterations | Zero, if the condition is false at the start | At least one, always |
   | Syntax | `while (condition) { ... }` | `do { ... } while (condition);` |
   | Semicolon | Not needed after the condition | Required after the closing `while (condition)` |
   | Used when | The number of repetitions may be zero | The body must run at least once, e.g. a menu |

   Example showing the difference — `int i = 15;`
   ```c
   while (i < 10) { printf("Output"); i++; }     // prints nothing
   do    { printf("Output"); i++; } while (i < 10);  // prints "Output" once
   ```
   - The `while` loop tests `15 < 10` first, finds it false and never enters the body. The `do-while` executes the body once before testing.

5. **Write down a program is any high level language to read an integer and display a pattern like below. For example, if the given integer number is 1234, then the following pattern will be printed.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1354 (ET: N/A)]*
```
1 2 3 4
2 3 4
3 4
4
```

   Answer: The number is read as a string of digits. Row `i` prints digits from position `i` to the end, so each row drops one digit from the left.

   ```c
   #include <stdio.h>
   #include <string.h>

   int main(void) {
       char num[20];
       int i, j, len;

       printf("Enter an integer: ");
       scanf("%s", num);
       len = strlen(num);

       for (i = 0; i < len; i++) {          // row i starts at digit i
           for (j = i; j < len; j++)
               printf("%c ", num[j]);
           printf("\n");
       }
       return 0;
   }
   ```

   - For input `1234` the outer loop runs 4 times and the inner loop prints digits `i` to 3, giving exactly the required pattern.
   - Time complexity `O(d²)` where `d` is the number of digits.

6. **a) Suppose you are working with an array of size 10. It contains all the numbers from 1 to 10 exactly once in a random order. But accidentally, one of the numbers in the array got replaced by a zero (0). Write a C/C++ programme using functions, to restore the lost number.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1343 (ET: N/A)]*

   Answer: The sum of 1 to 10 is fixed at 55. Whatever is missing equals 55 minus the current sum of the array.

   ```c
   #include <stdio.h>

   int findMissing(int a[], int n) {
       int i, expected, actual = 0;
       expected = n * (n + 1) / 2;       // sum of 1..n
       for (i = 0; i < n; i++)
           actual += a[i];               // the 0 contributes nothing
       return expected - actual;
   }

   void restore(int a[], int n) {
       int missing = findMissing(a, n);
       int i;
       for (i = 0; i < n; i++)
           if (a[i] == 0) { a[i] = missing; break; }
   }

   int main(void) {
       int a[10] = {3, 7, 1, 0, 5, 9, 2, 10, 6, 4};
       int i;
       restore(a, 10);
       printf("Restored array: ");
       for (i = 0; i < 10; i++) printf("%d ", a[i]);
       return 0;
   }
   ```

   - Here `expected = 55` and `actual = 47`, so the lost number is `55 − 47 = 8`.
   - Time complexity `O(n)`, space `O(1)` — a single pass with no extra array.
   - The XOR method also works and avoids any risk of integer overflow on large `n`.

7. **Find biggest elements in an array of 10 components.** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*

   Answer:

   ```c
   #include <stdio.h>

   int main(void) {
       int a[10], i, max;

       printf("Enter 10 elements: ");
       for (i = 0; i < 10; i++) scanf("%d", &a[i]);

       max = a[0];                       // assume the first is largest
       for (i = 1; i < 10; i++)
           if (a[i] > max) max = a[i];

       printf("Largest element = %d\n", max);
       return 0;
   }
   ```

   - Start with `max = a[0]` rather than 0, otherwise an array of all negative numbers would give a wrong answer.
   - Time complexity `O(n)` with `n − 1` comparisons, space `O(1)`.

8. **Write a C program that accepts 10 elements in an array and finds the maximum elements from the array.** *[BBA Assistant Programmer 12.07.2025 compact it 1433 (ET: BUET)]*

   Answer:

   ```c
   #include <stdio.h>

   int findMax(int a[], int n) {
       int i, max = a[0];
       for (i = 1; i < n; i++)
           if (a[i] > max)
               max = a[i];
       return max;
   }

   int main(void) {
       int a[10], i;
       printf("Enter 10 elements: ");
       for (i = 0; i < 10; i++) scanf("%d", &a[i]);
       printf("Maximum element = %d\n", findMax(a, 10));
       return 0;
   }
   ```

   - The scan compares each element with the running maximum and updates it when a larger value appears.
   - Time `O(n)`, space `O(1)`.

9. **Write a function to find minimum number from an array, return minimum value as argument.** *[Bangladesh Satellite Company Limited Assistant Engineer (CSE) 23.08.2025 compact it 1430 (ET: BUET)]*

   Answer: To return the value "as an argument", the function writes the result into a pointer parameter instead of using a return value.

   ```c
   #include <stdio.h>

   void findMin(int a[], int n, int *min) {
       int i;
       *min = a[0];
       for (i = 1; i < n; i++)
           if (a[i] < *min)
               *min = a[i];              // written back through the pointer
   }

   int main(void) {
       int a[] = {45, 12, 78, 3, 56};
       int result;

       findMin(a, 5, &result);           // address of result is passed
       printf("Minimum element = %d\n", result);
       return 0;
   }
   ```

   - `&result` passes the address, so the function updates the caller's variable directly. This is call by reference.
   - Output for the sample array: `Minimum element = 3`.
   - Time `O(n)`, space `O(1)`.

10. **Write a C/Java program to check Armstrong number or not.** *[BREB Assistant General Manager (IT) 2021 compact it 934 (ET: N/A)], [BREB Assistant Programmer (AP) 21.02.2025 compact it 1334 (ET: N/A)]*

    Answer: A number is an Armstrong number when the sum of its digits, each raised to the power of the digit count, equals the number itself. For example `153 = 1³ + 5³ + 3³`.

    ```c
    #include <stdio.h>
    #include <math.h>

    int main(void) {
        int n, temp, digit, digits = 0, sum = 0;

        printf("Enter a number: ");
        scanf("%d", &n);

        temp = n;
        while (temp != 0) { digits++; temp /= 10; }   // count the digits

        temp = n;
        while (temp != 0) {
            digit = temp % 10;
            sum += (int)pow(digit, digits);
            temp /= 10;
        }

        if (sum == n) printf("%d is an Armstrong number\n", n);
        else          printf("%d is not an Armstrong number\n", n);
        return 0;
    }
    ```

    - For 153: digits = 3, sum = `1 + 125 + 27 = 153`, so it is an Armstrong number.
    - Other examples: 370, 371, 407, and 1634 (a 4-digit one).
    - Time complexity `O(d)` where `d` is the number of digits.

11. **Write a program from the following series: $e^x = 1 + \frac{x}{1} + \frac{x^2}{2!} + \frac{x^3}{3!} + \dots$** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 316 (ET: N/A)]*

    Answer: Each term is built from the previous one by multiplying with `x/i`, so no separate power or factorial calculation is needed.

    ```c
    #include <stdio.h>

    int main(void) {
        float x, term = 1.0, sum = 1.0;   // first term is 1
        int i, n;

        printf("Enter value of x and number of terms n: ");
        scanf("%f %d", &x, &n);

        for (i = 1; i < n; i++) {
            term = term * x / i;          // term(i) = term(i-1) * x / i
            sum += term;
        }

        printf("e^%.2f = %.4f\n", x, sum);
        return 0;
    }
    ```

    - Why the recurrence works: term `i` is `xⁱ/i!` and term `i−1` is `x^(i−1)/(i−1)!`, so their ratio is exactly `x/i`.
    - This avoids computing large factorials, which would overflow quickly.
    - Time complexity `O(n)`.

12. **Write a C program to find sum of: $X - \frac{X^3}{3!} + \frac{X^5}{5!} - \frac{X^7}{7!} \dots N$** *[PGCB Assistant Engineer (CSE) 17.05.2024 compact it 397 (ET: BUET)]*

    Answer: This is the Taylor series for `sin(x)`. Each term is obtained from the previous one by multiplying with `−x²/((2i)(2i+1))`.

    ```c
    #include <stdio.h>

    int main(void) {
        float x, term, sum;
        int i, n;

        printf("Enter value of x (radian) and number of terms n: ");
        scanf("%f %d", &x, &n);

        term = x;            // first term is x
        sum  = x;

        for (i = 1; i < n; i++) {
            term = -term * x * x / ((2 * i) * (2 * i + 1));
            sum += term;
        }

        printf("Sum of the series = %.5f\n", sum);
        return 0;
    }
    ```

    - The minus sign in the recurrence produces the alternating `+ − + −` pattern automatically.
    - Denominator step: from `3!` to `5!` the extra factors are `4 × 5`, which is `(2i)(2i+1)` for `i = 2`.
    - Time complexity `O(n)`.

13. **Salary Range and Tax Calculation are given:**

| Salary Range | Tax |
|---|---|
| 0-250000 | 0 |
| 250001-5000000 | 10% |
| 500001-100000 | 20% |
| >10,00000 | 30% |

   * **a. Write a program using any language to the calculate the total tax of employee.** *[NWPGCL Assistant Manager (ICT) 12.01.2024 compact it 290 (ET: BUET)]*
   * **b. From the three employee salary find the highest tax paying employee.** *[NWPGCL Assistant Manager (ICT) 12.01.2024 compact it 290 (ET: BUET)]*

   Answer: The slab boundaries in the printed table have typing errors, so the standard reading is used: 0–2,50,000 → 0%; 2,50,001–5,00,000 → 10%; 5,00,001–10,00,000 → 20%; above 10,00,000 → 30%. Tax is charged slab by slab, not on the whole salary at one rate.

   ```c
   #include <stdio.h>

   double calculateTax(double salary) {
       double tax = 0;

       if (salary > 1000000) {
           tax += (salary - 1000000) * 0.30;
           salary = 1000000;
       }
       if (salary > 500000) {
           tax += (salary - 500000) * 0.20;
           salary = 500000;
       }
       if (salary > 250000) {
           tax += (salary - 250000) * 0.10;
       }
       return tax;                      // first 250000 is tax free
   }

   int main(void) {
       double salary[3], tax[3];
       int i, highest = 0;

       printf("Enter salary of 3 employees: ");
       for (i = 0; i < 3; i++) {
           scanf("%lf", &salary[i]);
           tax[i] = calculateTax(salary[i]);
           printf("Employee %d: salary = %.2f, tax = %.2f\n", i + 1, salary[i], tax[i]);
           if (tax[i] > tax[highest]) highest = i;
       }

       printf("Highest tax paid by Employee %d = %.2f\n", highest + 1, tax[highest]);
       return 0;
   }
   ```

   - Example: a salary of 12,00,000 pays `0 + 25,000 + 1,00,000 + 60,000 = 1,85,000`.
   - Part (b) is handled inside the same loop by keeping the index of the largest tax so far.

14. **Write a C program find prime number 1 to n.** *[NSDA Assistant Maintenance Engineer 11.05.2024 compact it 384 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int isPrime(int num) {
        int i;
        if (num < 2) return 0;
        for (i = 2; i * i <= num; i++)    // check only up to sqrt(num)
            if (num % i == 0) return 0;
        return 1;
    }

    int main(void) {
        int n, i;
        printf("Enter n: ");
        scanf("%d", &n);

        printf("Prime numbers from 1 to %d: ", n);
        for (i = 2; i <= n; i++)
            if (isPrime(i)) printf("%d ", i);
        return 0;
    }
    ```

    - Why `i * i <= num` is enough: if `num` has a divisor larger than its square root, the matching co-divisor must be smaller than the square root and would already have been found.
    - Time complexity `O(n√n)`. The Sieve of Eratosthenes does the same job in `O(n log log n)`.

15. **Write a program in any language to find the sum of rows and columns of a m \times n matrix, where m and n is taken input from the user. Give the output in the following format:**
   **Sample Input matrix:**
   **Sample Output:**
   *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 331 (ET: BIBM)]*

   Answer:

   ```c
   #include <stdio.h>

   int main(void) {
       int a[20][20], m, n, i, j, rowSum, colSum;

       printf("Enter m and n: ");
       scanf("%d %d", &m, &n);

       printf("Enter matrix elements:\n");
       for (i = 0; i < m; i++)
           for (j = 0; j < n; j++)
               scanf("%d", &a[i][j]);

       for (i = 0; i < m; i++) {              // sum of each row
           rowSum = 0;
           for (j = 0; j < n; j++) rowSum += a[i][j];
           printf("Sum of row %d = %d\n", i + 1, rowSum);
       }

       for (j = 0; j < n; j++) {              // sum of each column
           colSum = 0;
           for (i = 0; i < m; i++) colSum += a[i][j];
           printf("Sum of column %d = %d\n", j + 1, colSum);
       }
       return 0;
   }
   ```

   - For the row sum the row index stays fixed while the column index moves; for the column sum the roles are swapped.
   - Time complexity `O(m × n)`, space `O(m × n)` for the matrix.

16. **Write a program in any language to find the prime numbers between 1.......n, where n is taken as user input.**
   **Sample input:**
   **Enter value of n: 20**
   **Sample Output:**
   **Prime Numbers: 2, 3, 5, 7, 11, 13, 17, 19** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 332 (ET: BIBM)]*

   Answer: The Sieve of Eratosthenes is used here, since it is far faster when all primes up to `n` are needed.

   ```c
   #include <stdio.h>

   int main(void) {
       int n, i, j, first = 1;
       int prime[1001];

       printf("Enter value of n: ");
       scanf("%d", &n);

       for (i = 0; i <= n; i++) prime[i] = 1;   // assume all are prime
       prime[0] = prime[1] = 0;

       for (i = 2; i * i <= n; i++)
           if (prime[i])
               for (j = i * i; j <= n; j += i)  // strike out the multiples
                   prime[j] = 0;

       printf("Prime Numbers: ");
       for (i = 2; i <= n; i++)
           if (prime[i]) {
               if (!first) printf(", ");
               printf("%d", i);
               first = 0;
           }
       return 0;
   }
   ```

   - For `n = 20` the output is `Prime Numbers: 2, 3, 5, 7, 11, 13, 17, 19`.
   - Marking starts at `i * i` because every smaller multiple of `i` already has a smaller prime factor.
   - Time complexity `O(n log log n)`, space `O(n)`.

17. **Write a Program Prime number print from 1 to n.** *[Combined Bank Assistant Programmer 09.02.2024 compact it 294 (ET: BIBM)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int n, i, j, isPrime;

        printf("Enter n: ");
        scanf("%d", &n);

        printf("Prime numbers from 1 to %d:\n", n);
        for (i = 2; i <= n; i++) {
            isPrime = 1;
            for (j = 2; j * j <= i; j++) {
                if (i % j == 0) { isPrime = 0; break; }
            }
            if (isPrime) printf("%d ", i);
        }
        return 0;
    }
    ```

    - The loop starts at 2 because 0 and 1 are not prime by definition.
    - `break` exits as soon as one divisor is found, so composite numbers are rejected quickly.
    - Time complexity `O(n√n)`.

18. **Write a Program Floyds triangle n=5**
```text
1
01
101
0101
10101
```
*[Combined Bank Assistant Programmer 09.02.2024 compact it 295 (ET: BIBM)]*

    Answer: Row `i` holds `i` characters, and the values alternate between 1 and 0. Looking at the pattern, the digit at row `i`, column `j` is 1 when `(i + j)` is even and 0 when it is odd.

    ```c
    #include <stdio.h>

    int main(void) {
        int n = 5, i, j;

        for (i = 1; i <= n; i++) {
            for (j = 1; j <= i; j++)
                printf("%d", (i + j) % 2 == 0 ? 1 : 0);
            printf("\n");
        }
        return 0;
    }
    ```

    Output
    ```
    1
    01
    101
    0101
    10101
    ```

    - Check row 3: `(3+1)=4` even → 1, `(3+2)=5` odd → 0, `(3+3)=6` even → 1, giving `101`.
    - Time complexity `O(n²)`, since the total characters printed are `1 + 2 + ... + n`.

19. **Write a C Program Find sum of the series: 1+2+4+7+11+..........+N** *[Combined Bank Assistant Programmer 09.02.2024 compact it 295 (ET: BIBM)]*

    Answer: The differences between consecutive terms are 1, 2, 3, 4, ... so each term is the previous term plus the term index.

    ```c
    #include <stdio.h>

    int main(void) {
        int n, i, term = 1, sum = 0;

        printf("Enter number of terms: ");
        scanf("%d", &n);

        printf("Series: ");
        for (i = 1; i <= n; i++) {
            printf("%d ", term);
            sum += term;
            term += i;                   // next term = current + i
        }

        printf("\nSum = %d\n", sum);
        return 0;
    }
    ```

    - For `n = 6` the terms are `1, 2, 4, 7, 11, 16` and the sum is `41`.
    - The general term is `1 + i(i−1)/2`, so a closed-form solution is also possible.
    - Time complexity `O(n)`.

20. **Write a function which receives an array of integers as parameter and print the numbers divisible by 3 in the array.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 428 (ET: BIBM)]*

    Answer:

    ```c
    #include <stdio.h>

    void printDivisibleByThree(int arr[], int n) {
        int i, found = 0;
        printf("Numbers divisible by 3: ");
        for (i = 0; i < n; i++) {
            if (arr[i] % 3 == 0) {
                printf("%d ", arr[i]);
                found = 1;
            }
        }
        if (!found) printf("None");
        printf("\n");
    }

    int main(void) {
        int arr[] = {12, 7, 9, 20, 33, 5, 18};
        printDivisibleByThree(arr, 7);
        return 0;
    }
    ```

    - Output for the sample array: `12 9 33 18`.
    - In C an array parameter decays into a pointer, so the size `n` must be passed separately.
    - Time complexity `O(n)`, space `O(1)`.

21. **Write a C program: ax^2+bx+c=0** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 390 (ET: BUET)]*

    Answer: The roots come from the quadratic formula `x = (−b ± √(b² − 4ac)) / 2a`. The discriminant `D = b² − 4ac` decides which of three cases applies.

    ```c
    #include <stdio.h>
    #include <math.h>

    int main(void) {
        float a, b, c, d, r1, r2, real, imag;

        printf("Enter a, b, c: ");
        scanf("%f %f %f", &a, &b, &c);

        if (a == 0) { printf("Not a quadratic equation\n"); return 0; }

        d = b * b - 4 * a * c;

        if (d > 0) {                               // two distinct real roots
            r1 = (-b + sqrt(d)) / (2 * a);
            r2 = (-b - sqrt(d)) / (2 * a);
            printf("Real and distinct roots: %.2f and %.2f\n", r1, r2);
        }
        else if (d == 0) {                         // two equal real roots
            r1 = -b / (2 * a);
            printf("Real and equal roots: %.2f and %.2f\n", r1, r1);
        }
        else {                                     // complex conjugate roots
            real = -b / (2 * a);
            imag = sqrt(-d) / (2 * a);
            printf("Complex roots: %.2f + %.2fi and %.2f - %.2fi\n",
                   real, imag, real, imag);
        }
        return 0;
    }
    ```

    - Example: `a=1, b=-5, c=6` gives `D = 25 − 24 = 1 > 0`, so the roots are 3 and 2.
    - The `a == 0` guard prevents division by zero, since the equation is then linear, not quadratic.

22. **Write a program that take a number as input and output should be sum of digits of that number using python/C also draw its flow chart.** *[BKSP Assistant Programmer 13.07.2024 compact it 1457 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int n, digit, sum = 0;

        printf("Enter a number: ");
        scanf("%d", &n);

        while (n != 0) {
            digit = n % 10;              // take the last digit
            sum += digit;
            n = n / 10;                  // remove the last digit
        }

        printf("Sum of digits = %d\n", sum);
        return 0;
    }
    ```

    Flowchart

    ```mermaid
    flowchart TD
        A([Start]) --> B[/Read n/]
        B --> C[sum = 0]
        C --> D{n != 0 ?}
        D -->|Yes| E[digit = n % 10]
        E --> F[sum = sum + digit]
        F --> G[n = n / 10]
        G --> D
        D -->|No| H[/Print sum/]
        H --> I([Stop])
    ```

    - For input `1234` the loop extracts 4, 3, 2, 1 and gives `sum = 10`.
    - Time complexity `O(d)` where `d` is the number of digits.

23. **Find the output from the following: take input and looks the output:**
   **Suppose Input: 6789; Output: 9876** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 379 (ET: BUET)]*

   Answer: The program reverses the digits of the number. Each digit is peeled off from the right and appended to the result from the left.

   ```c
   #include <stdio.h>

   int main(void) {
       int n, digit, rev = 0;

       printf("Enter a number: ");
       scanf("%d", &n);

       while (n != 0) {
           digit = n % 10;
           rev = rev * 10 + digit;      // shift left, then add the digit
           n = n / 10;
       }

       printf("Reversed number = %d\n", rev);
       return 0;
   }
   ```

   Dry run for input 6789

   | Step | n | digit | rev |
   |---|---|---|---|
   | 1 | 6789 | 9 | 0×10 + 9 = 9 |
   | 2 | 678 | 8 | 9×10 + 8 = 98 |
   | 3 | 67 | 7 | 98×10 + 7 = 987 |
   | 4 | 6 | 6 | 987×10 + 6 = 9876 |

   - Output: `9876`. Time complexity `O(d)`.

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

   Answer: Output is `30`.

   Step-by-step
   - `a[2]` is the element at index 2 of array `a`, which is `2`.
   - The expression becomes `b[2]`.
   - `b[2]` is the element at index 2 of array `b`, which is `30`.
   - `printf` prints `30` with no newline.

   - This is array indexing with a nested subscript — the inner subscript is evaluated first and its value is used as the index for the outer array.

25. **Given a code with a variable value "a=85" and finds its output a=85**
```c
if a>=90 point A;
if a>=80 point B;
if a>=70 point C;
if a>=60 point D;
else print F;
```
*[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1454 (ET: BUET)]*

   Answer: Output is `B C D`.

   Reason
   - These are four separate `if` statements, not an `if ... else if` chain. Each one is tested independently, so more than one can fire.
   - `a >= 90` → `85 >= 90` is false → nothing printed.
   - `a >= 80` → true → prints `B`.
   - `a >= 70` → true → prints `C`.
   - `a >= 60` → true → prints `D`. The `else` belongs only to this last `if`, so `F` is not printed.

   Correct version using else-if, which prints only one grade
   ```c
   if      (a >= 90) printf("A");
   else if (a >= 80) printf("B");
   else if (a >= 70) printf("C");
   else if (a >= 60) printf("D");
   else              printf("F");
   ```
   - With `a = 85` this prints only `B`, which is what a grading program actually needs.

26. **(ক) C ভাষায় ব্যবহৃত বিভিন্ন ধরনের Data Type বর্ণনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 407 (ET: N/A)]*

    Answer: A data type tells the compiler what kind of value a variable holds and how much memory to give it. C data types fall into three groups.

    (a) Primary (basic) data types

    | Type | Size | Range | Format specifier |
    |---|---|---|---|
    | char | 1 byte | −128 to 127 | %c |
    | int | 4 bytes | −2,147,483,648 to 2,147,483,647 | %d |
    | float | 4 bytes | 1.2e−38 to 3.4e+38 (6 digits) | %f |
    | double | 8 bytes | 2.3e−308 to 1.7e+308 (15 digits) | %lf |
    | void | 0 byte | no value | — |

    (b) Derived data types
    - Array — a collection of elements of the same type, e.g. `int a[10];`
    - Pointer — holds a memory address, e.g. `int *p;`
    - Function — a block of code that may return a value.

    (c) User-defined data types
    - `struct` — groups variables of different types under one name.
    - `union` — like a struct, but all members share the same memory.
    - `enum` — a set of named integer constants.
    - `typedef` — gives a new name to an existing type.

    - Modifiers `signed`, `unsigned`, `short` and `long` change the size or range, for example `unsigned int` (0 to 4,294,967,295).
    - Sizes depend on the machine architecture, so `sizeof()` should be used to check them rather than assuming fixed values.

27. **(খ) একটি ধনাত্মক পূর্ণ সংখ্যার Factorial নির্ণয়ের C program লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 408 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    unsigned long long factorial(int n) {
        int i;
        unsigned long long fact = 1;
        for (i = 2; i <= n; i++)
            fact *= i;
        return fact;
    }

    int main(void) {
        int n;
        printf("Enter a positive integer: ");
        scanf("%d", &n);

        if (n < 0) printf("Factorial is not defined for negative numbers\n");
        else       printf("Factorial of %d = %llu\n", n, factorial(n));
        return 0;
    }
    ```

    - `n! = n × (n−1) × ... × 2 × 1`, and by definition `0! = 1`, which the loop handles because it simply does not run.
    - `unsigned long long` is used because factorials grow very fast — `21!` already overflows a 64-bit integer.
    - Time complexity `O(n)`. The recursive form `n * factorial(n-1)` is shorter but uses `O(n)` stack space.

28. **Write a program swap two numbers without using 3rd variable.** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 501 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int a, b;
        printf("Enter two numbers: ");
        scanf("%d %d", &a, &b);
        printf("Before swap: a = %d, b = %d\n", a, b);

        a = a + b;        // a holds the sum
        b = a - b;        // b becomes the old a
        a = a - b;        // a becomes the old b

        printf("After swap:  a = %d, b = %d\n", a, b);
        return 0;
    }
    ```

    Dry run with `a = 5, b = 3`
    - `a = 5 + 3 = 8`
    - `b = 8 − 3 = 5` (old a)
    - `a = 8 − 5 = 3` (old b)

    - Alternative using XOR, which cannot overflow: `a = a ^ b; b = a ^ b; a = a ^ b;`
    - Caution: both methods fail if the same variable is passed twice (`swap(&x, &x)`), because the value becomes 0. The arithmetic version can also overflow for very large values.

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

    Answer: The first line printed is `112345`. After that the program has undefined behaviour and, when compiled and run, it hangs in an infinite loop.

    Why
    - `PrintArray(num, 5)` in `main` prints the array without separators, giving `112345`.
    - Inside `FunctionArray`, the variable `j` is declared but never assigned before `j--` is executed. Reading an uninitialised local variable is undefined behaviour in C — `j` holds whatever garbage was on the stack.
    - The condition `while (j >= 0 && j <= n)` is then tested against that garbage value. If it happens to be true, the loop body never modifies `j`, so the condition can never become false and the loop runs forever.
    - The body also does `num[j] = num[j+1]`, which can read and write outside the array bounds — another undefined behaviour.

    Corrected version — this is a broken insertion sort, and the intended code is:
    ```c
    void FunctionArray(int num[], int n) {
        int i, j, key;
        for (i = 1; i < n; i++) {
            key = num[i];
            j = i - 1;                       // j must be initialised here
            while (j >= 0 && num[j] > key) { // and moved inside the loop
                num[j + 1] = num[j];
                j--;
            }
            num[j + 1] = key;
            PrintArray(num, n);
        }
    }
    ```
    - With this fix the output would be the insertion sort passes ending at `12345`.

30. **Write a program for following sequence and analyze complexity of the program** *[Sonali & Janata Bank Officer (IT) 14.10.2023 compact it 522 (ET: MIST)]*

    Answer: The sequence was not printed with the question, so the Fibonacci sequence is used to show both the program and the complexity analysis.

    ```c
    #include <stdio.h>

    int main(void) {
        int n, i;
        long long a = 0, b = 1, next;

        printf("Enter number of terms: ");
        scanf("%d", &n);

        printf("Sequence: %lld %lld ", a, b);
        for (i = 3; i <= n; i++) {
            next = a + b;
            printf("%lld ", next);
            a = b;
            b = next;
        }
        return 0;
    }
    ```

    Complexity analysis
    - The loop runs `n − 2` times and each iteration does constant work, so time complexity is `O(n)`.
    - Only three variables are stored regardless of `n`, so space complexity is `O(1)`.
    - The naive recursive version `fib(n) = fib(n-1) + fib(n-2)` would cost `O(2ⁿ)` time and `O(n)` stack space, because it recomputes the same terms repeatedly.

31. **Write a C/C++ program to count the prime number up to N.** *[Sheikh Kamal IT Training & Incubation Center Assistant Programmer/Instructor 04.08.2023 compact it 599 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int n, i, j, count = 0, isPrime;

        printf("Enter N: ");
        scanf("%d", &n);

        for (i = 2; i <= n; i++) {
            isPrime = 1;
            for (j = 2; j * j <= i; j++)
                if (i % j == 0) { isPrime = 0; break; }
            if (isPrime) count++;
        }

        printf("Total prime numbers up to %d = %d\n", n, count);
        return 0;
    }
    ```

    - For `n = 20` the count is 8, namely 2, 3, 5, 7, 11, 13, 17, 19.
    - Time complexity `O(n√n)`. Using a sieve instead brings it down to `O(n log log n)`, which matters when `n` is large.

32. **Write a C/C++ program for check out a leap year program.** *[Sheikh Kamal IT Training & Incubation Center Assistant Programmer/Instructor 04.08.2023 compact it 599 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int isLeapYear(int year) {
        if (year % 400 == 0) return 1;      // divisible by 400 -> leap
        if (year % 100 == 0) return 0;      // divisible by 100 only -> not leap
        if (year % 4 == 0)   return 1;      // divisible by 4 -> leap
        return 0;
    }

    int main(void) {
        int year;
        printf("Enter a year: ");
        scanf("%d", &year);

        if (isLeapYear(year)) printf("%d is a Leap Year\n", year);
        else                  printf("%d is not a Leap Year\n", year);
        return 0;
    }
    ```

    - Checking 400 first, then 100, then 4 keeps the rules in the right priority order without needing compound conditions.
    - Test cases: 2024 leap, 2023 not leap, 1900 not leap, 2000 leap.

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

   (a) Number triangle — row `i` prints the numbers 1 to `i`.
   ```c
   #include <stdio.h>

   int main(void) {
       int n = 3, i, j;
       for (i = 1; i <= n; i++) {
           for (j = 1; j <= i; j++)
               printf("%d ", j);
           printf("\n");
       }
       return 0;
   }
   ```

   (b) Print a fixed string a fixed number of times.
   ```c
   #include <stdio.h>

   int main(void) {
       int i;
       for (i = 1; i <= 4; i++)
           printf("Start\n");
       return 0;
   }
   ```

   - In (a) the inner loop bound depends on the outer counter, which is what makes the triangle shape. Time complexity `O(n²)`.
   - In (b) the loop body is independent of the counter, so it is a simple `O(n)` repetition.

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

    Answer: The program prints the first `n` Fibonacci numbers.

    Output for input `n = 7`
    ```
    Enter the number of terms for the fibonacci series: 7
    Fibonacci Series:01,1,2,3,5,8
    ```

    Trace
    - `first = 0` and `second = 1` are printed first, with no comma between them — note the formatting quirk, `01` appears joined.
    - The loop then runs for `i = 2` to `6`, printing `,1 ,2 ,3 ,5 ,8`.
    - Other cases: `n = 0` prints only the prompt; `n = 1` prints `0`; `n = 2` prints `01`.

    Complexity
    - Time complexity `O(n)` — the loop runs `n − 2` times with constant work each pass.
    - Space complexity `O(1)` — only `first`, `second` and `next` are stored, regardless of `n`. Nothing is saved in an array.

35. **Write a program find prime number between 1 to 100?** *[NPCBL Executive Trainee (Software) 26.05.2023 compact it 499 (ET: IBA)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int i, j, isPrime;

        printf("Prime numbers between 1 and 100:\n");
        for (i = 2; i <= 100; i++) {
            isPrime = 1;
            for (j = 2; j * j <= i; j++)
                if (i % j == 0) { isPrime = 0; break; }
            if (isPrime) printf("%d ", i);
        }
        return 0;
    }
    ```

    Output
    ```
    2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97
    ```

    - There are 25 prime numbers between 1 and 100.
    - The loop starts at 2 because 1 is not prime — a prime must have exactly two distinct divisors.

36. **Write a C program sum of 1 to 100.** *[Mongla Port Authority Assistant Programmer 2023 compact it 571 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int i, sum = 0;

        for (i = 1; i <= 100; i++)
            sum += i;

        printf("Sum of 1 to 100 = %d\n", sum);
        return 0;
    }
    ```

    - Output: `Sum of 1 to 100 = 5050`.
    - The same result comes from the formula `n(n+1)/2 = 100 × 101 / 2 = 5050`, which runs in `O(1)` instead of `O(n)`.

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

   (a) Number triangle of 4 rows
   ```c
   #include <stdio.h>

   int main(void) {
       int n = 4, i, j;
       for (i = 1; i <= n; i++) {
           for (j = 1; j <= i; j++)
               printf("%d ", j);
           printf("\n");
       }
       return 0;
   }
   ```

   (b) Array of five fruit names — an array of string pointers
   ```c
   #include <stdio.h>

   int main(void) {
       char *fruits[5] = {"Mango", "Banana", "Jackfruit", "Litchi", "Guava"};
       int i;

       printf("List of fruits:\n");
       for (i = 0; i < 5; i++)
           printf("%d. %s\n", i + 1, fruits[i]);
       return 0;
   }
   ```

   - `char *fruits[5]` is an array of five pointers, each pointing to a string literal. A 2-D form `char fruits[5][20]` would also work and allows the strings to be modified.

38. **Write a program in any language that takes two matrices A and B as inputs ensure your code handles matrices of different dimensions—**
   **A) Find matrices C that is multiplication A and B.**
   **B) Find average in A and B.**
   **C) Max from matrices C** *[Combined Bank Senior Officer (IT) 13.10.2023 compact it 515 (ET: MIST)]*

   Answer: Matrix multiplication is possible only when the columns of A equal the rows of B, so that check comes first.

   ```c
   #include <stdio.h>

   int main(void) {
       int A[20][20], B[20][20], C[20][20];
       int m, n, p, q, i, j, k;
       int sumA = 0, sumB = 0, max;

       printf("Enter rows and columns of A: ");
       scanf("%d %d", &m, &n);
       printf("Enter rows and columns of B: ");
       scanf("%d %d", &p, &q);

       if (n != p) {                      // dimension check
           printf("Multiplication not possible: columns of A must equal rows of B\n");
           return 0;
       }

       printf("Enter elements of A:\n");
       for (i = 0; i < m; i++)
           for (j = 0; j < n; j++) { scanf("%d", &A[i][j]); sumA += A[i][j]; }

       printf("Enter elements of B:\n");
       for (i = 0; i < p; i++)
           for (j = 0; j < q; j++) { scanf("%d", &B[i][j]); sumB += B[i][j]; }

       // (A) multiplication
       for (i = 0; i < m; i++)
           for (j = 0; j < q; j++) {
               C[i][j] = 0;
               for (k = 0; k < n; k++)
                   C[i][j] += A[i][k] * B[k][j];
           }

       printf("Matrix C = A x B:\n");
       for (i = 0; i < m; i++) {
           for (j = 0; j < q; j++) printf("%d ", C[i][j]);
           printf("\n");
       }

       // (B) averages
       printf("Average of A = %.2f\n", (float)sumA / (m * n));
       printf("Average of B = %.2f\n", (float)sumB / (p * q));

       // (C) maximum of C
       max = C[0][0];
       for (i = 0; i < m; i++)
           for (j = 0; j < q; j++)
               if (C[i][j] > max) max = C[i][j];
       printf("Maximum element of C = %d\n", max);

       return 0;
   }
   ```

   - Matrix C has dimensions `m × q`.
   - Time complexity `O(m × n × q)` for the multiplication, which dominates the `O(m×n)` average and `O(m×q)` maximum scans.

39. **Write a function to find the smallest element from an array.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 492 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int findSmallest(int a[], int n) {
        int i, min = a[0];               // start with the first element
        for (i = 1; i < n; i++)
            if (a[i] < min)
                min = a[i];
        return min;
    }

    int main(void) {
        int a[] = {45, 12, 78, 3, 56, 91};
        printf("Smallest element = %d\n", findSmallest(a, 6));
        return 0;
    }
    ```

    - Output: `Smallest element = 3`.
    - Initialising `min` to `a[0]` rather than to a large constant keeps the function correct for any range of values.
    - Time `O(n)` with `n − 1` comparisons, space `O(1)`.

40. **Suppose you have an array. The array contains elements from 0 to 10. This array also contains 0. To replace these 0s, write a program in C/C++ language.** *[BTCL Assistant Manager (Technical) 2023 compact it 593 (ET: BUET)]*

    Answer: The array should hold 1 to 10 once each, but some entries were replaced by 0. The missing values are found by marking which numbers are present, then the zeros are filled with the missing ones.

    ```c
    #include <stdio.h>

    int main(void) {
        int a[10] = {3, 0, 1, 7, 5, 0, 2, 10, 6, 4};
        int present[11] = {0};
        int i, j = 1;

        for (i = 0; i < 10; i++)          // mark what is already present
            if (a[i] != 0) present[a[i]] = 1;

        for (i = 0; i < 10; i++) {        // fill each zero with a missing value
            if (a[i] == 0) {
                while (j <= 10 && present[j]) j++;
                a[i] = j;
                present[j] = 1;
            }
        }

        printf("Restored array: ");
        for (i = 0; i < 10; i++) printf("%d ", a[i]);
        return 0;
    }
    ```

    - Sample output: `3 8 1 7 5 9 2 10 6 4` — the missing values 8 and 9 fill the two zeros in order.
    - If exactly one zero exists, the simpler `sum` trick works: the missing number is `55 − (current sum)`.
    - Time complexity `O(n)`, space `O(n)` for the marker array.

41. **Write a function int equilibrium (int[] arr, int n); that given a sequence arr[] of size n, returns an equilibrium index (if any) or -1 if no equilibrium indexes exist. The equilibrium index of an array is an index such that the sum of elements at lower indexes is equal to the sum of elements at higher indexes. Foe example:** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 455 (ET: BUET)]*
   **Input: A[] = {-7, 1, 5, 2, -4, 3, 0}**
   **Output: 3**
   **3 is an equilibrium index, because: A[0] + A[1] + A[2] = A[4] + A[5] + A[6]**
   **Input: A[] = {1, 2, 3}**
   **Output: -1**

   Answer: Compute the total sum once, then sweep left to right keeping a running left sum. At each index the right sum is `total − leftSum − arr[i]`.

   ```c
   #include <stdio.h>

   int equilibrium(int arr[], int n) {
       int i, total = 0, leftSum = 0;

       for (i = 0; i < n; i++)
           total += arr[i];              // total sum, one pass

       for (i = 0; i < n; i++) {
           total -= arr[i];              // total now holds the right sum
           if (leftSum == total)
               return i;
           leftSum += arr[i];            // include arr[i] on the left for the next step
       }
       return -1;                        // no equilibrium index found
   }

   int main(void) {
       int a[] = {-7, 1, 5, 2, -4, 3, 0};
       int b[] = {1, 2, 3};
       printf("%d\n", equilibrium(a, 7));   // 3
       printf("%d\n", equilibrium(b, 3));   // -1
       return 0;
   }
   ```

   Verification for the first array
   - Total sum = `−7 + 1 + 5 + 2 − 4 + 3 + 0 = 0`
   - At `i = 3`: left sum = `−7 + 1 + 5 = −1`, right sum = `−4 + 3 + 0 = −1`. They match, so 3 is returned.

   - Time complexity `O(n)` — two single passes. Space `O(1)`.
   - The brute-force method of recomputing both sums for every index would cost `O(n²)`.

42. **Write a C program to print the following pattern:**
```text
0
010
01010

```
*[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 457 (ET: BUET)]*

    Answer: Row `i` has `2i − 1` characters, and the digits alternate starting from 0. So the character at column `j` is 0 when `j` is odd and 1 when `j` is even.

    ```c
    #include <stdio.h>

    int main(void) {
        int n = 3, i, j;

        for (i = 1; i <= n; i++) {
            for (j = 1; j <= 2 * i - 1; j++)
                printf("%d", j % 2 == 1 ? 0 : 1);
            printf("\n");
        }
        return 0;
    }
    ```

    Output
    ```
    0
    010
    01010
    ```

    - Row 1 has 1 character, row 2 has 3, row 3 has 5 — the odd numbers, which is `2i − 1`.
    - Time complexity `O(n²)`.

43. **Write a C code that show factorial of a number.** *[BITAC Assistant Programmer 27.10.2023 compact it 561 (ET: BUTEX)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int n, i;
        unsigned long long fact = 1;

        printf("Enter a number: ");
        scanf("%d", &n);

        if (n < 0) {
            printf("Factorial is not defined for negative numbers\n");
            return 0;
        }

        for (i = 1; i <= n; i++)
            fact *= i;

        printf("Factorial of %d = %llu\n", n, fact);
        return 0;
    }
    ```

    - For `n = 5` the output is `120`, since `5! = 5 × 4 × 3 × 2 × 1`.
    - `fact` starts at 1 so that `0!` correctly gives 1 without any special case.
    - Time `O(n)`, space `O(1)`.

44. **Write a C Program to delete duplicate element from array.** *[BEPZA Programmer 03.11.2023 compact it 561 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int removeDuplicates(int a[], int n) {
        int i, j, k;
        for (i = 0; i < n; i++) {
            for (j = i + 1; j < n; ) {
                if (a[j] == a[i]) {
                    for (k = j; k < n - 1; k++)   // shift the rest left
                        a[k] = a[k + 1];
                    n--;                          // array is now one shorter
                } else {
                    j++;
                }
            }
        }
        return n;                                 // new size
    }

    int main(void) {
        int a[] = {10, 20, 10, 30, 20, 40, 30};
        int n = 7, i;

        n = removeDuplicates(a, n);

        printf("Array after removing duplicates: ");
        for (i = 0; i < n; i++) printf("%d ", a[i]);
        return 0;
    }
    ```

    - Output: `10 20 30 40`, with the new size 4.
    - Note that `j` is not incremented after a deletion, because the shifted element now sits at index `j` and must also be checked.
    - Time complexity `O(n²)`. If the array is sorted first, a single pass removes duplicates and the total cost drops to `O(n log n)`.

45. **Given two integers A and B as input write a program to compute the least common multiple of A and B.** *[Bangladesh Bank Assistant Programmer 03.02.2023 compact it 436 (ET: BIBM)]*

    Answer: The relation `LCM(a,b) × GCD(a,b) = a × b` gives the fastest route — find the GCD by Euclid's algorithm, then divide.

    ```c
    #include <stdio.h>

    int gcd(int a, int b) {
        while (b != 0) {                 // Euclid's algorithm
            int temp = b;
            b = a % b;
            a = temp;
        }
        return a;
    }

    int main(void) {
        int a, b, result;

        printf("Enter two integers: ");
        scanf("%d %d", &a, &b);

        result = (a / gcd(a, b)) * b;    // divide first to avoid overflow

        printf("LCM of %d and %d = %d\n", a, b, result);
        return 0;
    }
    ```

    Example with `a = 12, b = 18`
    - `gcd(12,18)`: `18 % 12 = 6`, `12 % 6 = 0` → GCD = 6
    - `LCM = (12 / 6) × 18 = 2 × 18 = 36`

    - Dividing before multiplying (`a / gcd * b` rather than `a * b / gcd`) avoids overflow when `a` and `b` are large.
    - Time complexity `O(log(min(a,b)))` for the GCD.

46. **(খ) এমন একটি C program লিখুন যা একটি array তৈরি করে কতগুলো ডেটা রাখবে, তারপর ফলাফল হিসেবে ডেটাগুলোকে বিপরীত দিক থেকে print করবে।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 600 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int a[100], n, i;

        printf("How many elements? ");
        scanf("%d", &n);

        printf("Enter %d elements: ", n);
        for (i = 0; i < n; i++)
            scanf("%d", &a[i]);

        printf("Elements in reverse order: ");
        for (i = n - 1; i >= 0; i--)     // start at the last index
            printf("%d ", a[i]);

        return 0;
    }
    ```

    - For input `10 20 30 40 50` the output is `50 40 30 20 10`.
    - Only the printing order is reversed here; the array itself is unchanged. To actually reverse the stored array, swap `a[i]` with `a[n-1-i]` for `i` from 0 to `n/2`.
    - Time `O(n)`, space `O(1)` beyond the array.

47. **(খ) প্রথম দশটি Fibonacci number প্রদর্শনের জন্য একটি C program লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 601 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int i, first = 0, second = 1, next;

        printf("First 10 Fibonacci numbers:\n");
        printf("%d %d ", first, second);

        for (i = 3; i <= 10; i++) {
            next = first + second;
            printf("%d ", next);
            first = second;
            second = next;
        }
        return 0;
    }
    ```

    Output
    ```
    0 1 1 2 3 5 8 13 21 34
    ```

    - Each term after the first two is the sum of the previous two: `F(n) = F(n−1) + F(n−2)`.
    - Time `O(n)`, space `O(1)`. The recursive version would cost `O(2ⁿ)` because it recomputes the same terms.

48. **Write a C program: x - \frac{x^3}{3} + \frac{x^5}{5} - \dots** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 650 (ET: BUET)]*

    Answer: This is the arctan (Gregory-Leibniz) series. The denominators are odd numbers, not factorials, and the signs alternate.

    ```c
    #include <stdio.h>
    #include <math.h>

    int main(void) {
        float x, sum = 0;
        int i, n, sign = 1, power = 1;

        printf("Enter x and number of terms n: ");
        scanf("%f %d", &x, &n);

        for (i = 1; i <= n; i++) {
            sum += sign * pow(x, power) / power;
            sign = -sign;                // flip the sign each term
            power += 2;                  // 1, 3, 5, 7, ...
        }

        printf("Sum of the series = %.5f\n", sum);
        return 0;
    }
    ```

    - Term `i` is `± x^(2i−1) / (2i−1)`, so `power` advances by 2 and `sign` flips every pass.
    - For `x = 1` this series converges to `π/4`, though very slowly.
    - Time complexity `O(n)`.

49. **C program to find sum of odd numbers from 1 to n.** *[NSDA Assistant Programmer Date: 04-03-2022 compact it 656 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int n, i, sum = 0;

        printf("Enter n: ");
        scanf("%d", &n);

        for (i = 1; i <= n; i += 2)      // step by 2 to hit only odd numbers
            sum += i;

        printf("Sum of odd numbers from 1 to %d = %d\n", n, sum);
        return 0;
    }
    ```

    - For `n = 10` the sum is `1 + 3 + 5 + 7 + 9 = 25`.
    - Interesting property: the sum of the first `k` odd numbers is exactly `k²`, so for `n = 10` there are 5 odd numbers and the sum is `5² = 25`.
    - Time `O(n/2) = O(n)`, space `O(1)`.

50. **Determine whwther a given number is prime or not?** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 682 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int n, i, isPrime = 1;

        printf("Enter a number: ");
        scanf("%d", &n);

        if (n < 2) isPrime = 0;
        else
            for (i = 2; i * i <= n; i++)
                if (n % i == 0) { isPrime = 0; break; }

        if (isPrime) printf("%d is a prime number\n", n);
        else         printf("%d is not a prime number\n", n);
        return 0;
    }
    ```

    - A prime number is greater than 1 and divisible only by 1 and itself.
    - Checking divisors up to `√n` is enough, because a factor larger than `√n` must pair with one smaller than `√n`, which would already have been found.
    - Time complexity `O(√n)`, space `O(1)`.

51. **Find the most significant number in an array of N elements.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 683 (ET: N/A)]*

    Answer: "Most significant" here means the largest value in the array.

    ```c
    #include <stdio.h>

    int main(void) {
        int a[100], n, i, max;

        printf("Enter number of elements: ");
        scanf("%d", &n);
        printf("Enter %d elements: ", n);
        for (i = 0; i < n; i++) scanf("%d", &a[i]);

        max = a[0];
        for (i = 1; i < n; i++)
            if (a[i] > max) max = a[i];

        printf("Largest (most significant) element = %d\n", max);
        return 0;
    }
    ```

    - Time complexity `O(n)` with `n − 1` comparisons, which is the theoretical minimum for finding a maximum.
    - If "most significant digit" of a number is meant instead, repeatedly divide the number by 10 until it falls below 10; the remaining value is that digit.

52. **Determine even or odd numbers.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 684 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int n, i;

        printf("Enter n: ");
        scanf("%d", &n);

        printf("Even numbers: ");
        for (i = 1; i <= n; i++)
            if (i % 2 == 0) printf("%d ", i);

        printf("\nOdd numbers: ");
        for (i = 1; i <= n; i++)
            if (i % 2 != 0) printf("%d ", i);

        return 0;
    }
    ```

    - For a single number, `if (n % 2 == 0)` decides it directly.
    - The modulus operator `%` returns the remainder, so a remainder of 0 on division by 2 means even.
    - Time complexity `O(n)`.

53. **Print the following matrix using for loop.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 682 (ET: N/A)]*
```text
1
22
333
4444
55555
```

    Answer: Row `i` prints the digit `i` exactly `i` times.

    ```c
    #include <stdio.h>

    int main(void) {
        int n = 5, i, j;

        for (i = 1; i <= n; i++) {
            for (j = 1; j <= i; j++)
                printf("%d", i);         // print the row number, not j
            printf("\n");
        }
        return 0;
    }
    ```

    Output
    ```
    1
    22
    333
    4444
    55555
    ```

    - The key detail is that the inner loop prints `i` (the row number) and not `j` — printing `j` would give `1`, `12`, `123` instead.
    - Time complexity `O(n²)`.

54. **ইউজার হতে 10 টি integer data input করে যে data গুলো 5 দ্বারা বিভাজ্য তাদের গড় মান নির্ণয় এর একটি program লিখুন।** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 698 (ET: DPI)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int a[10], i, sum = 0, count = 0;

        printf("Enter 10 integers: ");
        for (i = 0; i < 10; i++)
            scanf("%d", &a[i]);

        for (i = 0; i < 10; i++) {
            if (a[i] % 5 == 0) {         // divisible by 5
                sum += a[i];
                count++;
            }
        }

        if (count == 0)
            printf("No number is divisible by 5\n");
        else
            printf("Count = %d, Sum = %d, Average = %.2f\n",
                   count, sum, (float)sum / count);
        return 0;
    }
    ```

    - The `count == 0` check prevents division by zero when no input is divisible by 5.
    - The cast `(float)sum` is needed, otherwise integer division would truncate the average.
    - Time `O(n)`, space `O(n)` for the array.

55. **Write a function in C/C++ that return kth largest number of an array. The function has three parameters array_name, size, k.** *[EGCB Assistant Engineer (CSE) 2022 compact it 714 (ET: BUET)]*

    Answer: Sort the array in descending order and return the element at index `k − 1`.

    ```c
    #include <stdio.h>

    int kthLargest(int arr[], int size, int k) {
        int i, j, temp;

        if (k < 1 || k > size) return -1;        // invalid k

        for (i = 0; i < size - 1; i++)           // selection sort, descending
            for (j = i + 1; j < size; j++)
                if (arr[j] > arr[i]) {
                    temp = arr[i]; arr[i] = arr[j]; arr[j] = temp;
                }

        return arr[k - 1];                       // kth largest
    }

    int main(void) {
        int a[] = {12, 45, 7, 89, 23, 56};
        printf("3rd largest = %d\n", kthLargest(a, 6, 3));
        return 0;
    }
    ```

    - Sorted descending the array becomes `89, 56, 45, 23, 12, 7`, so the 3rd largest is `45`.
    - Time complexity `O(n²)` with this simple sort. Using a min-heap of size `k` reduces it to `O(n log k)`, and Quickselect gives `O(n)` on average.
    - Note this version modifies the caller's array; copying it first would preserve the original.

56. **Write a C/C++ program to find out the prime from 1 to N.** *[Telephone Shilpa Sangstha Ltd. (TSS) Assistant Programmer 2022 compact it 718 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int n, i, j, isPrime;

        printf("Enter N: ");
        scanf("%d", &n);

        printf("Prime numbers from 1 to %d:\n", n);
        for (i = 2; i <= n; i++) {
            isPrime = 1;
            for (j = 2; j * j <= i; j++)
                if (i % j == 0) { isPrime = 0; break; }
            if (isPrime) printf("%d ", i);
        }
        return 0;
    }
    ```

    - For `N = 30` the output is `2 3 5 7 11 13 17 19 23 29`.
    - `break` stops the inner loop at the first divisor found, so composites are rejected quickly.
    - Time complexity `O(n√n)`, space `O(1)`.

57. **Write a C/C++ program to find the reverse number of a number.** *[CAAB Programmer 2022 compact it 721 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int n, digit, rev = 0;

        printf("Enter a number: ");
        scanf("%d", &n);

        while (n != 0) {
            digit = n % 10;              // last digit
            rev = rev * 10 + digit;      // shift rev left, append the digit
            n /= 10;                     // drop the last digit
        }

        printf("Reversed number = %d\n", rev);
        return 0;
    }
    ```

    - For input `12345` the output is `54321`.
    - `rev * 10` shifts the existing digits one place left, making room for the new digit at the units place.
    - Time complexity `O(d)` where `d` is the number of digits.

58. **Write a C/C++ program to find the HCF.** *[CAAB Programmer 2022 compact it 721 (ET: N/A)]*

    Answer: HCF (Highest Common Factor) is the same as GCD. Euclid's algorithm is the standard method.

    ```c
    #include <stdio.h>

    int hcf(int a, int b) {
        while (b != 0) {
            int remainder = a % b;
            a = b;
            b = remainder;
        }
        return a;                        // when b becomes 0, a is the HCF
    }

    int main(void) {
        int a, b;
        printf("Enter two numbers: ");
        scanf("%d %d", &a, &b);
        printf("HCF of %d and %d = %d\n", a, b, hcf(a, b));
        return 0;
    }
    ```

    Dry run with `a = 48, b = 18`
    - `48 % 18 = 12` → a = 18, b = 12
    - `18 % 12 = 6` → a = 12, b = 6
    - `12 % 6 = 0` → a = 6, b = 0 → stop
    - HCF = `6`

    - Euclid's rule works because `gcd(a, b) = gcd(b, a % b)`.
    - Time complexity `O(log(min(a,b)))`, far faster than testing every divisor.

59. **Write a C/C++ program to find the sum of digits.** *[CAAB Assistant Programmer (AP) 2022 compact it 725 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int n, sum = 0;

        printf("Enter a number: ");
        scanf("%d", &n);

        if (n < 0) n = -n;               // handle negative input

        while (n != 0) {
            sum += n % 10;               // add the last digit
            n /= 10;                     // remove it
        }

        printf("Sum of digits = %d\n", sum);
        return 0;
    }
    ```

    - For `n = 4567` the sum is `4 + 5 + 6 + 7 = 22`.
    - Time complexity `O(d)`, space `O(1)`.

60. **Write a program to find this is Leap year or not, using function.** *[BKSP Assistant Programmer 03.12.2022 compact it 729 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int isLeapYear(int year) {
        if ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0))
            return 1;                    // leap year
        return 0;
    }

    int main(void) {
        int year;

        printf("Enter a year: ");
        scanf("%d", &year);

        if (isLeapYear(year))
            printf("%d is a Leap Year\n", year);
        else
            printf("%d is not a Leap Year\n", year);
        return 0;
    }
    ```

    - The whole rule sits in one condition: divisible by 4 but not by 100, OR divisible by 400.
    - Putting it in a separate function makes it reusable — a date-validation routine can call `isLeapYear()` to decide whether February has 29 days.
    - Time complexity `O(1)`.

61. **Write a C program using array, here N is the number of total students. Take the input and find the average marks. Find out the students who got the above marks or low marks according to average marks.** *[BOF Assistant Programmer 2022 compact it 732 (ET: MIST)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int marks[100], n, i, sum = 0;
        float average;

        printf("Enter number of students: ");
        scanf("%d", &n);

        printf("Enter marks of %d students: ", n);
        for (i = 0; i < n; i++) {
            scanf("%d", &marks[i]);
            sum += marks[i];
        }

        average = (float)sum / n;
        printf("Average marks = %.2f\n", average);

        printf("\nStudents above average:\n");
        for (i = 0; i < n; i++)
            if (marks[i] > average)
                printf("Student %d: %d\n", i + 1, marks[i]);

        printf("\nStudents below average:\n");
        for (i = 0; i < n; i++)
            if (marks[i] < average)
                printf("Student %d: %d\n", i + 1, marks[i]);

        return 0;
    }
    ```

    - The average must be computed before the comparison loops, so two passes over the array are needed.
    - `(float)sum / n` prevents integer division from truncating the average.
    - Students exactly equal to the average appear in neither list, which is the correct reading of "above" and "below".
    - Time `O(n)`, space `O(n)`.

62. **Write down a function int reverse (int n) that takes a positive integer as input parameter and returns the reverse of the given integer. For example, if input integer N=2579, then reversed output is= 9752** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 748 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int reverse(int n) {
        int rev = 0;
        while (n != 0) {
            rev = rev * 10 + (n % 10);   // append the last digit of n to rev
            n /= 10;
        }
        return rev;
    }

    int main(void) {
        printf("%d\n", reverse(2579));   // 9752
        return 0;
    }
    ```

    Dry run for `n = 2579`

    | Step | n | n % 10 | rev |
    |---|---|---|---|
    | 1 | 2579 | 9 | 0×10 + 9 = 9 |
    | 2 | 257 | 7 | 9×10 + 7 = 97 |
    | 3 | 25 | 5 | 97×10 + 5 = 975 |
    | 4 | 2 | 2 | 975×10 + 2 = 9752 |

    - Returns `9752`. Time complexity `O(d)`, space `O(1)`.
    - For very large inputs the reversed value can overflow `int`; using `long long` avoids that.

63. **Consider int num[20][4] holds the marks of four class test(CT) of a class of 20 students. Write a program to find out the sum of best three CT marks for each student.** *[BDCCL Assistant Manager (Cloud) 14.10.2022 compact it 748 (ET: N/A)]*

    Answer: The best three out of four is simply the total of all four minus the lowest one.

    ```c
    #include <stdio.h>

    int main(void) {
        int num[20][4], i, j, total, min;

        printf("Enter marks of 20 students (4 CTs each):\n");
        for (i = 0; i < 20; i++)
            for (j = 0; j < 4; j++)
                scanf("%d", &num[i][j]);

        for (i = 0; i < 20; i++) {
            total = 0;
            min = num[i][0];
            for (j = 0; j < 4; j++) {
                total += num[i][j];
                if (num[i][j] < min) min = num[i][j];   // lowest CT of this student
            }
            printf("Student %d: best three total = %d\n", i + 1, total - min);
        }
        return 0;
    }
    ```

    - Example: marks 15, 18, 12, 20 give total 65 and minimum 12, so the best-three total is 53.
    - Sorting each row and adding the top three would also work, but dropping the minimum is `O(4)` per student instead of `O(4 log 4)`.
    - Time complexity `O(20 × 4)`, space `O(20 × 4)`.

64. **(ক) নিচের সিরিজ টি ক্যালকুলেটর এবং প্রিন্ট করার জন্য একটি C Program লিখুন। 1 + 2 + 3 + \dots + 100** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 776 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int i, sum = 0;

        for (i = 1; i <= 100; i++) {
            printf("%d", i);
            if (i < 100) printf(" + ");
            sum += i;
        }

        printf("\nSum = %d\n", sum);
        return 0;
    }
    ```

    - Output ends with `Sum = 5050`.
    - Cross-check with the formula `n(n+1)/2 = 100 × 101 / 2 = 5050`.
    - The `if (i < 100)` guard stops a trailing `+` from being printed after the last term.

65. **(খ) তোমার ক্লাসের ছাত্রদের তালিকা Sort করার জন্য একটি C Program লিখ।** *[BPSC Sub-Assistant Engineer (Ministry of Food) 2021 compact it 776 (ET: N/A)]*

    Answer: Student names are strings, so `strcmp` is used for comparison and `strcpy` for swapping.

    ```c
    #include <stdio.h>
    #include <string.h>

    int main(void) {
        char names[50][30], temp[30];
        int n, i, j;

        printf("How many students? ");
        scanf("%d", &n);

        printf("Enter %d names:\n", n);
        for (i = 0; i < n; i++)
            scanf("%s", names[i]);

        for (i = 0; i < n - 1; i++)               // bubble sort on strings
            for (j = 0; j < n - 1 - i; j++)
                if (strcmp(names[j], names[j + 1]) > 0) {
                    strcpy(temp, names[j]);
                    strcpy(names[j], names[j + 1]);
                    strcpy(names[j + 1], temp);
                }

        printf("\nSorted list:\n");
        for (i = 0; i < n; i++)
            printf("%d. %s\n", i + 1, names[i]);
        return 0;
    }
    ```

    - `strcmp(a, b)` returns a positive value when `a` comes after `b` alphabetically, which is exactly the swap condition.
    - Strings cannot be assigned with `=` in C, which is why `strcpy` is needed for the swap.
    - Time complexity `O(n² × L)` where `L` is the average name length.

66. **(b) Write a program in C/C++/Java to identify the largest number of given 3 numbers.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 791 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int a, b, c, max;

        printf("Enter three numbers: ");
        scanf("%d %d %d", &a, &b, &c);

        max = a;
        if (b > max) max = b;
        if (c > max) max = c;

        printf("Largest number = %d\n", max);
        return 0;
    }
    ```

    - The running-maximum approach scales to any count of numbers, unlike a nested `if (a > b && a > c)` chain which grows unwieldy.
    - Only 2 comparisons are needed for 3 numbers, which is the minimum possible.

67. **(b) Write down a program in C language that will find the maximum of four integer gives as inputs.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 804 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int a[4], i, max;

        printf("Enter four integers: ");
        for (i = 0; i < 4; i++)
            scanf("%d", &a[i]);

        max = a[0];
        for (i = 1; i < 4; i++)
            if (a[i] > max) max = a[i];

        printf("Maximum = %d\n", max);
        return 0;
    }
    ```

    - Using an array plus a loop keeps the code the same size whether there are 4 numbers or 400.
    - Time `O(n)` with `n − 1` comparisons.

68. **We are given an array of integers and a range, we need to find whether the subarray which falls in this range has values in the form of a mountain or not. All values of the subarray are said to be in the form of a mountain if either all values are increasing or decreasing or first increasing and then decreasing. Write a C/C++ Program that shows input is a Mountain sequence or Not Mountain sequence.** *[6 Banks & Financial Institutions Assistant Programmer 2021 compact it 833 (ET: N/A)]*

    Answer: Walk up while values increase, then walk down while they decrease. If the whole range is consumed, it is a mountain.

    ```c
    #include <stdio.h>

    int isMountain(int a[], int L, int R) {
        int i = L;

        while (i < R && a[i] < a[i + 1]) i++;      // climb up
        while (i < R && a[i] > a[i + 1]) i++;      // slide down

        return (i == R);                           // reached the end -> mountain
    }

    int main(void) {
        int a[] = {2, 3, 5, 8, 6, 4, 1};
        int b[] = {2, 3, 1, 4, 5};

        printf("%s\n", isMountain(a, 0, 6) ? "Mountain sequence" : "Not Mountain sequence");
        printf("%s\n", isMountain(b, 0, 4) ? "Mountain sequence" : "Not Mountain sequence");
        return 0;
    }
    ```

    - Array `a` climbs 2→3→5→8 and then falls 8→6→4→1, so `i` reaches the end and it is a mountain.
    - Array `b` climbs 2→3, falls 3→1, then rises again at 1→4, so the walk stops early and it is not a mountain.
    - A strictly increasing or strictly decreasing sequence also passes, because one of the two loops simply does not run.
    - Time complexity `O(R − L)`, space `O(1)`.

69. **Write a programme in C/C++/Java what finds sum of digits of a number until sum becomes single digit, simple input/output is: Input: 12345 Output: 6** *[RAKUB Programmer (PO) 12.10.2021 compact it 844 (ET: N/A)], [Sonali Bank Ltd. Officer IT 2021 compact it 908 (ET: N/A)]*

    Answer: This value is called the digital root. Keep summing the digits until a single digit remains.

    ```c
    #include <stdio.h>

    int digitalRoot(int n) {
        while (n > 9) {                  // repeat until one digit is left
            int sum = 0;
            while (n != 0) {
                sum += n % 10;
                n /= 10;
            }
            n = sum;
        }
        return n;
    }

    int main(void) {
        printf("%d\n", digitalRoot(12345));   // 6
        return 0;
    }
    ```

    Trace for 12345
    - Pass 1: `1 + 2 + 3 + 4 + 5 = 15`
    - Pass 2: `1 + 5 = 6` → single digit, stop.
    - Output: `6`

    - Shortcut formula: `digitalRoot(n) = 1 + (n − 1) % 9` for `n > 0`, which gives the answer in `O(1)`. For 12345: `1 + 12344 % 9 = 1 + 5 = 6`.

70. **Pattern this print using C++ program-** *[PGCB Assistant Engineer (CSE) 30.09.2021 compact it 862 (ET: BUET)]*
```text
1 2 3 4 5
1 2 3 4
1 2 3
1 2
1
```

    Answer: This is an inverted number triangle — row `i` prints 1 up to `n − i + 1`.

    ```cpp
    #include <iostream>
    using namespace std;

    int main() {
        int n = 5;
        for (int i = n; i >= 1; i--) {       // row length shrinks from n to 1
            for (int j = 1; j <= i; j++)
                cout << j << " ";
            cout << endl;
        }
        return 0;
    }
    ```

    - The outer loop counts down, so each row is one element shorter than the one above.
    - The inner loop always starts at 1, which is why every row begins with 1.
    - Time complexity `O(n²)`.

71. **(a) Write down a function in C Programming language, that will take an n\times n matrix as parameter and the dimension n as another parameter, then compute the sum of main diagonal elements of the matrix.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 884 (ET: N/A)]*

    Answer: On the main diagonal the row index equals the column index, so a single loop is enough.

    ```c
    #include <stdio.h>
    #define MAX 20

    int diagonalSum(int matrix[][MAX], int n) {
        int i, sum = 0;
        for (i = 0; i < n; i++)
            sum += matrix[i][i];         // row index == column index
        return sum;
    }

    int main(void) {
        int matrix[MAX][MAX], n, i, j;

        printf("Enter n: ");
        scanf("%d", &n);
        printf("Enter matrix elements:\n");
        for (i = 0; i < n; i++)
            for (j = 0; j < n; j++)
                scanf("%d", &matrix[i][j]);

        printf("Sum of main diagonal = %d\n", diagonalSum(matrix, n));
        return 0;
    }
    ```

    - Example: for `{{1,2,3},{4,5,6},{7,8,9}}` the diagonal is `1, 5, 9` and the sum is `15`.
    - In C the second dimension of a 2-D array parameter must be a fixed constant, which is why `MAX` is used.
    - Time complexity `O(n)` — only `n` cells are touched, not `n²`.

72. **(b) Write down a program to find sum of diagonal elements of a two dimensional matrix.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 895 (ET: N/A)]*

    Answer: A square matrix has two diagonals — the main diagonal `a[i][i]` and the secondary diagonal `a[i][n-1-i]`.

    ```c
    #include <stdio.h>

    int main(void) {
        int a[20][20], n, i, j;
        int mainSum = 0, secSum = 0;

        printf("Enter order of the square matrix: ");
        scanf("%d", &n);
        printf("Enter elements:\n");
        for (i = 0; i < n; i++)
            for (j = 0; j < n; j++)
                scanf("%d", &a[i][j]);

        for (i = 0; i < n; i++) {
            mainSum += a[i][i];             // main diagonal
            secSum  += a[i][n - 1 - i];     // secondary diagonal
        }

        printf("Main diagonal sum = %d\n", mainSum);
        printf("Secondary diagonal sum = %d\n", secSum);
        return 0;
    }
    ```

    - For `{{1,2,3},{4,5,6},{7,8,9}}`: main diagonal `1+5+9 = 15`, secondary diagonal `3+5+7 = 15`.
    - When `n` is odd the centre element belongs to both diagonals, so it is counted twice if the two sums are added together.
    - Time complexity `O(n)` for the diagonals themselves.

73. **(i) Write a C/C++ program up to series n: \frac{1}{2\times 3} + \frac{2}{3\times 4} + \frac{3}{4\times 5} \dots\dots\dots\dots\dots** *[NESCO Assistant Manager (ICT) 2021 compact it 907 (ET: BUET)]*

    Answer: The general term is `i / ((i+1) × (i+2))`.

    ```c
    #include <stdio.h>

    int main(void) {
        int i, n;
        float sum = 0;

        printf("Enter number of terms: ");
        scanf("%d", &n);

        for (i = 1; i <= n; i++)
            sum += (float)i / ((i + 1) * (i + 2));

        printf("Sum of the series = %.5f\n", sum);
        return 0;
    }
    ```

    - Check: `i = 1` gives `1/(2×3) = 1/6`, `i = 2` gives `2/(3×4) = 2/12`, matching the printed series.
    - The cast `(float)i` is essential — without it, integer division would make every term 0.
    - Time complexity `O(n)`.

74. **Write a C program to compute the perimeter and area of a circle with a given radius.** *[Sonali Bank Ltd. Officer IT 2021 compact it 909-910 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>
    #define PI 3.14159

    int main(void) {
        float radius, perimeter, area;

        printf("Enter the radius: ");
        scanf("%f", &radius);

        perimeter = 2 * PI * radius;     // circumference = 2πr
        area      = PI * radius * radius; // area = πr²

        printf("Perimeter (circumference) = %.2f\n", perimeter);
        printf("Area = %.2f\n", area);
        return 0;
    }
    ```

    - For `radius = 5`: perimeter = `31.42`, area = `78.54`.
    - `PI` is defined as a macro so the value appears once and cannot be mistyped. The `math.h` constant `M_PI` can also be used.

75. **A হলো মিটার নং, B হলো ব্যবহৃত ইউনিট। 300 ইউনিটের বেশী তাদের মিটার নং এবং ইউনিটের যোগফল বের কর।** *[NESCO Junior Assistant Manager (ICT) 2021 compact it 912 (ET: BUET)]*

    Answer: Read meter numbers and their units, then report every meter whose consumption exceeds 300 along with the total units of that group.

    ```c
    #include <stdio.h>

    int main(void) {
        int meter[100], unit[100], n, i, totalUnit = 0, count = 0;

        printf("How many meters? ");
        scanf("%d", &n);

        printf("Enter meter number and units used:\n");
        for (i = 0; i < n; i++)
            scanf("%d %d", &meter[i], &unit[i]);

        printf("\nMeters using more than 300 units:\n");
        for (i = 0; i < n; i++) {
            if (unit[i] > 300) {
                printf("Meter No: %d, Units: %d\n", meter[i], unit[i]);
                totalUnit += unit[i];
                count++;
            }
        }

        printf("\nTotal such meters = %d\n", count);
        printf("Total units consumed by them = %d\n", totalUnit);
        return 0;
    }
    ```

    - Two parallel arrays keep the meter number aligned with its unit reading; a `struct` would be a cleaner design for the same data.
    - Time complexity `O(n)`, space `O(n)`.

76. **Write the code for second highest maximum from given three number in c/c++.** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 920-921 (ET: N/A)]*

    Answer: The second highest of three numbers is the one that is neither the maximum nor the minimum.

    ```c
    #include <stdio.h>

    int main(void) {
        int a, b, c, max, min, second;

        printf("Enter three numbers: ");
        scanf("%d %d %d", &a, &b, &c);

        max = a;
        if (b > max) max = b;
        if (c > max) max = c;

        min = a;
        if (b < min) min = b;
        if (c < min) min = c;

        second = (a + b + c) - max - min;   // the remaining one

        printf("Second highest = %d\n", second);
        return 0;
    }
    ```

    - Example: for `10, 25, 15` the maximum is 25 and the minimum is 10, so the second highest is `50 − 25 − 10 = 15`.
    - The subtraction trick works because exactly three values are involved and each is counted once in the total.
    - For duplicates such as `10, 10, 5`, this returns 10, which is the correct second-largest value by position.

77. **Write a simple output C program to check odd-even number.** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 932 (ET: BUET)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int n;

        printf("Enter a number: ");
        scanf("%d", &n);

        if (n % 2 == 0)
            printf("%d is EVEN\n", n);
        else
            printf("%d is ODD\n", n);
        return 0;
    }
    ```

    - Sample run: input `7` gives `7 is ODD`; input `12` gives `12 is EVEN`.
    - Time complexity `O(1)`.

78. **Write a C program for prime numbers between 1 to N.** *[BMA Signal Assistant Engineer (Computer) 2021 compact it 932 (ET: BUET)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int n, i, j, isPrime;

        printf("Enter N: ");
        scanf("%d", &n);

        printf("Prime numbers between 1 and %d:\n", n);
        for (i = 2; i <= n; i++) {
            isPrime = 1;
            for (j = 2; j * j <= i; j++)
                if (i % j == 0) { isPrime = 0; break; }
            if (isPrime) printf("%d ", i);
        }
        printf("\n");
        return 0;
    }
    ```

    - Every number from 2 to `n` is tested for divisibility by any value up to its square root.
    - Time complexity `O(n√n)`, space `O(1)`.

79. **Write a program for the following series: 1^2+2^2+3^2+4^2+\dots\dots\dots\dots+N^2** *[BREB Junior Assistant Manager (ICT) 2021 compact it 948 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int n, i, sum = 0;

        printf("Enter N: ");
        scanf("%d", &n);

        for (i = 1; i <= n; i++)
            sum += i * i;

        printf("Sum of squares up to %d = %d\n", n, sum);
        return 0;
    }
    ```

    - For `n = 5`: `1 + 4 + 9 + 16 + 25 = 55`.
    - Cross-check with the formula `n(n+1)(2n+1)/6 = 5 × 6 × 11 / 6 = 55`. The formula runs in `O(1)` while the loop is `O(n)`.

80. **(i) Formatted Input/Output Statement কাকে বলে? Key-Board থেকে কিভাবে input নেয়া যায়? %d এর অর্থ কী?** *[BPSC Assistant Network Engineer 2020 compact it 954-955 (ET: N/A)]*

    Answer:

    Formatted input/output statement
    - A statement that reads or writes data in a specified format, controlled by format specifiers. In C these are `scanf()` for input and `printf()` for output.
    - "Formatted" means the programmer states the type and layout of each value, for example how many decimal places a float should show.

    Taking input from the keyboard
    - `scanf("%d", &n);` reads an integer from the keyboard into the variable `n`.
    - The `&` operator passes the address of the variable, which is how `scanf` writes the value back into it. Omitting `&` is the most common beginner error.
    - Several values can be read at once: `scanf("%d %f %c", &a, &b, &c);`
    - Other input functions: `getchar()` for a single character, `gets()` and `fgets()` for a full line.

    Meaning of %d
    - `%d` is the format specifier for a signed decimal integer.
    - In `printf("%d", n)` it prints `n` as a decimal number; in `scanf("%d", &n)` it reads a decimal number into `n`.

    Common format specifiers

    | Specifier | Data type |
    |---|---|
    | %d or %i | int |
    | %f | float |
    | %lf | double |
    | %c | char |
    | %s | string |
    | %u | unsigned int |
    | %x | hexadecimal |

81. **(ii) if......else statement এর format লিখ। 1+3+5+7+\dots+n সিরিজটির যোগফল নির্ণয়ের জন্য C-language এ একটি প্রোগ্রাম লিখ।** *[BPSC Assistant Network Engineer 2020 compact it 955 (ET: N/A)]*

    Answer:

    Format of the if-else statement
    ```c
    if (condition) {
        // runs when the condition is true
    }
    else {
        // runs when the condition is false
    }
    ```
    - The condition must evaluate to true (non-zero) or false (zero).
    - The `else` part is optional. For more than two paths, the `else if` ladder is used.

    Program for the series `1 + 3 + 5 + 7 + ... + n`
    ```c
    #include <stdio.h>

    int main(void) {
        int n, i, sum = 0;

        printf("Enter n: ");
        scanf("%d", &n);

        for (i = 1; i <= n; i += 2)      // odd numbers only
            sum += i;

        if (sum > 0)
            printf("Sum of the odd series = %d\n", sum);
        else
            printf("No terms to add\n");
        return 0;
    }
    ```

    - For `n = 9` the sum is `1 + 3 + 5 + 7 + 9 = 25`.
    - The sum of the first `k` odd numbers is always `k²`, so this result equals `5² = 25`.

82. **An employee’s total weekly pay is calculated by multiplying the hourly wage and number of regular hours plus any overtime pays which in turn is calculated as total overtime hours multiplied by 1.5 times the hourly wage. Write a program that takes as inputs the hourly wage, total regular hours, and total overtime hours and prints an employee’s total weekly pay.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 985 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        float wage, regularHours, overtimeHours;
        float regularPay, overtimePay, totalPay;

        printf("Enter hourly wage: ");
        scanf("%f", &wage);
        printf("Enter total regular hours: ");
        scanf("%f", &regularHours);
        printf("Enter total overtime hours: ");
        scanf("%f", &overtimeHours);

        regularPay  = wage * regularHours;
        overtimePay = overtimeHours * 1.5 * wage;    // overtime paid at 1.5x
        totalPay    = regularPay + overtimePay;

        printf("\nRegular pay  = %.2f\n", regularPay);
        printf("Overtime pay = %.2f\n", overtimePay);
        printf("Total weekly pay = %.2f\n", totalPay);
        return 0;
    }
    ```

    Example — wage 200, regular hours 40, overtime hours 5
    - Regular pay = `200 × 40 = 8000`
    - Overtime pay = `5 × 1.5 × 200 = 1500`
    - Total weekly pay = `9500`

83. **Write a C program: 1+2^n+3^n+4^n+\dots\dots\dots\dots+n^n (where n>0).** *[NACTAR Assistant Instructor (ICT) 2020 compact it 990-991 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>
    #include <math.h>

    int main(void) {
        int n, i;
        double sum = 0;

        printf("Enter n (n > 0): ");
        scanf("%d", &n);

        for (i = 1; i <= n; i++)
            sum += pow(i, n);            // i raised to the power n

        printf("Sum = %.0lf\n", sum);
        return 0;
    }
    ```

    - For `n = 3`: `1³ + 2³ + 3³ = 1 + 8 + 27 = 36`.
    - Note the exponent stays `n` for every term — it is not `i`. The first term `1` is consistent, since `1ⁿ = 1`.
    - `double` is used because the values grow extremely fast; `10¹⁰` already exceeds a 32-bit int.
    - Time complexity `O(n log n)` counting the cost of `pow`, or `O(n)` if a manual multiplication loop is used.

84. **X is an integer stream of N numbers. You have to select 2 data P and Q such that A <= (P+Q) <= B. Write an algorithm / pseudo code/ C program how many ways you can select P & Q. The time complexity must be n log n.** *[Combined 4 Banks Assistant Programmer 2020 compact it 1005-1006 (ET: DU)]*

    Answer: Sort the array first, then for each element use binary search to find the valid range of partners. Sorting costs `O(n log n)` and the `n` binary searches cost `O(n log n)` as well.

    ```c
    #include <stdio.h>
    #include <stdlib.h>

    int cmp(const void *x, const void *y) { return (*(int*)x - *(int*)y); }

    // first index > lo with value >= target
    int lowerBound(int a[], int lo, int hi, int target) {
        int mid, ans = hi + 1;
        while (lo <= hi) {
            mid = lo + (hi - lo) / 2;
            if (a[mid] >= target) { ans = mid; hi = mid - 1; }
            else lo = mid + 1;
        }
        return ans;
    }

    // first index > lo with value > target
    int upperBound(int a[], int lo, int hi, int target) {
        int mid, ans = hi + 1;
        while (lo <= hi) {
            mid = lo + (hi - lo) / 2;
            if (a[mid] > target) { ans = mid; hi = mid - 1; }
            else lo = mid + 1;
        }
        return ans;
    }

    int countPairs(int a[], int n, int A, int B) {
        int i, count = 0, left, right;

        qsort(a, n, sizeof(int), cmp);           // O(n log n)

        for (i = 0; i < n; i++) {
            // partner must lie in [A - a[i], B - a[i]], and sit after index i
            left  = lowerBound(a, i + 1, n - 1, A - a[i]);
            right = upperBound(a, i + 1, n - 1, B - a[i]) - 1;
            if (right >= left) count += (right - left + 1);
        }
        return count;
    }

    int main(void) {
        int a[] = {1, 3, 5, 7, 9};
        printf("Number of ways = %d\n", countPairs(a, 5, 8, 12));
        return 0;
    }
    ```

    - For `a = {1,3,5,7,9}` with `A = 8, B = 12`, the valid pairs are (1,7), (1,9), (3,5), (3,7), (3,9), (5,7) — that is 6 ways.
    - Searching only from `i + 1` onwards prevents counting the same pair twice.
    - Total time complexity `O(n log n)`, space `O(1)` beyond the input.

85. **Write a code in C/C++ that will output the 2nd largest number. (If N>=1)** *[Combined 4 Banks Assistant Programmer 2020 compact it 1008-1009 (ET: DU)]*

    Answer: One pass keeping two running values — the largest and the second largest.

    ```c
    #include <stdio.h>
    #include <limits.h>

    int main(void) {
        int a[100], n, i;
        int first = INT_MIN, second = INT_MIN;

        printf("Enter n: ");
        scanf("%d", &n);
        printf("Enter %d numbers: ", n);
        for (i = 0; i < n; i++) scanf("%d", &a[i]);

        for (i = 0; i < n; i++) {
            if (a[i] > first) {
                second = first;          // old maximum drops to second
                first = a[i];
            }
            else if (a[i] > second && a[i] != first) {
                second = a[i];
            }
        }

        if (second == INT_MIN)
            printf("No second largest element exists\n");
        else
            printf("Second largest = %d\n", second);
        return 0;
    }
    ```

    - For `12, 35, 1, 10, 34` the answer is `34`.
    - The `a[i] != first` guard stops a repeated maximum from being reported as the second largest.
    - Time complexity `O(n)` in a single pass, space `O(1)`. Sorting first would cost `O(n log n)`.

86. **0 থেকে n সংখ্যক পর্যন্ত Fibonacci Series লেখার জন্য প্রোগ্রাম লিখুন।** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1040-1041 (ET: DPI)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int n, i;
        long long first = 0, second = 1, next;

        printf("Enter number of terms: ");
        scanf("%d", &n);

        printf("Fibonacci Series: ");
        if (n >= 1) printf("%lld ", first);
        if (n >= 2) printf("%lld ", second);

        for (i = 3; i <= n; i++) {
            next = first + second;
            printf("%lld ", next);
            first = second;
            second = next;
        }
        return 0;
    }
    ```

    - For `n = 10` the output is `0 1 1 2 3 5 8 13 21 34`.
    - The two `if` guards handle the cases `n = 1` and `n = 2` correctly, so no extra term is printed.
    - Time `O(n)`, space `O(1)`.

87. **Write a program in C to find the sum of following series: $1^2+2^2+3^2+\dots\dots\dots\dots+n^2$** *[Bangladesh Competition Commission Programmer 2019 compact it 1061 (ET: DU)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int n, i;
        long long sum = 0;

        printf("Enter n: ");
        scanf("%d", &n);

        for (i = 1; i <= n; i++)
            sum += (long long)i * i;

        printf("Sum = %lld\n", sum);
        printf("Formula check n(n+1)(2n+1)/6 = %lld\n",
               (long long)n * (n + 1) * (2 * n + 1) / 6);
        return 0;
    }
    ```

    - For `n = 5`: `1 + 4 + 9 + 16 + 25 = 55`, and the formula gives `5 × 6 × 11 / 6 = 55`.
    - The cast to `long long` prevents overflow, since the sum grows roughly as `n³/3`.
    - Loop is `O(n)`; the closed formula is `O(1)`.

88. **A prim number is a number that is evenly divided by only 1 and itself. Write a program to your favorite language to print the first 100 prime numbers.** *[Bangladesh Competition Commission Programmer 2019 compact it 1062 (ET: DU)]*

    Answer: Note the difference from "primes up to 100" — here 100 primes are wanted, so the loop keeps going until the count reaches 100.

    ```c
    #include <stdio.h>

    int isPrime(int n) {
        int i;
        if (n < 2) return 0;
        for (i = 2; i * i <= n; i++)
            if (n % i == 0) return 0;
        return 1;
    }

    int main(void) {
        int count = 0, num = 2;

        printf("First 100 prime numbers:\n");
        while (count < 100) {            // stop on the count, not on the value
            if (isPrime(num)) {
                printf("%d ", num);
                count++;
            }
            num++;
        }
        return 0;
    }
    ```

    - The 100th prime number is `541`, so the loop runs until `num` reaches 541.
    - A `while` loop is the right choice here because the ending value is not known in advance.
    - Time complexity roughly `O(k √m)` where `k = 100` and `m` is the largest number tested.

89. **(গ) Array processor কী? $1+\frac{1}{2}+\frac{1}{3}+\dots\dots\dots\dots+\frac{1}{N}$ ধারাটির যোগফল নির্ণয়ের জন্য C ভাষায় একটি প্রোগ্রাম লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1072-1073 (ET: N/A)]*

    Answer:

    Array processor
    - A processor designed to perform the same operation on many data elements at the same time, using multiple processing elements that work in lock step under one control unit.
    - It belongs to the SIMD class (Single Instruction, Multiple Data) of Flynn's classification.
    - Instead of adding two arrays element by element in a loop, an array processor adds all elements in one instruction cycle.
    - Uses: weather forecasting, image and signal processing, matrix and vector computation, scientific simulation. Modern GPUs follow the same principle.

    Program for the harmonic series `1 + 1/2 + 1/3 + ... + 1/N`
    ```c
    #include <stdio.h>

    int main(void) {
        int n, i;
        float sum = 0;

        printf("Enter N: ");
        scanf("%d", &n);

        for (i = 1; i <= n; i++)
            sum += 1.0 / i;              // 1.0 forces floating point division

        printf("Sum of the series = %.5f\n", sum);
        return 0;
    }
    ```

    - Writing `1 / i` instead of `1.0 / i` would give integer division and a wrong answer of 1.
    - For `N = 5` the sum is about `2.28333`. This harmonic series grows very slowly and diverges as `N → ∞`.

90. **(ক) একটি Array তে পাঁচটি সংখ্যা Input হিসেবে নিয়ে তাদের গড় বের করার জন্য C প্রোগ্রামিং ল্যাঙ্গুয়েজে কোড লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1082-1083 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int a[5], i, sum = 0;
        float average;

        printf("Enter 5 numbers: ");
        for (i = 0; i < 5; i++) {
            scanf("%d", &a[i]);
            sum += a[i];
        }

        average = (float)sum / 5;

        printf("Sum = %d\n", sum);
        printf("Average = %.2f\n", average);
        return 0;
    }
    ```

    - For inputs `10, 20, 30, 40, 50`: sum = 150, average = `30.00`.
    - The cast `(float)sum` is required, otherwise `sum / 5` performs integer division and drops the fractional part.
    - Time `O(n)`, space `O(n)`.

91. **(খ) $ax^2+bx+c=0$ সমীকরণটির x চলকের মান নির্ণয়ের জন্য C প্রোগ্রামিং ল্যাঙ্গুয়েজে একটি কোড লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1084-1085 (ET: N/A)]*

    Answer: The roots come from `x = (−b ± √(b² − 4ac)) / 2a`, and the discriminant `D = b² − 4ac` selects one of three cases.

    ```c
    #include <stdio.h>
    #include <math.h>

    int main(void) {
        float a, b, c, d, x1, x2;

        printf("Enter a, b, c: ");
        scanf("%f %f %f", &a, &b, &c);

        if (a == 0) { printf("Not a quadratic equation\n"); return 0; }

        d = b * b - 4 * a * c;

        if (d > 0) {
            x1 = (-b + sqrt(d)) / (2 * a);
            x2 = (-b - sqrt(d)) / (2 * a);
            printf("Roots are real and different: x1 = %.2f, x2 = %.2f\n", x1, x2);
        }
        else if (d == 0) {
            x1 = -b / (2 * a);
            printf("Roots are real and equal: x1 = x2 = %.2f\n", x1);
        }
        else {
            printf("Roots are imaginary: %.2f + %.2fi and %.2f - %.2fi\n",
                   -b / (2 * a), sqrt(-d) / (2 * a),
                   -b / (2 * a), sqrt(-d) / (2 * a));
        }
        return 0;
    }
    ```

    - Example: `a=1, b=-7, c=12` gives `D = 49 − 48 = 1`, so the roots are 4 and 3.
    - `sqrt(-d)` is used in the imaginary branch because `d` itself is negative there.

92. **What is the equivalant code of the following statement in while loop format?** *[Sonali & Janata Bank Officer (IT/ICT) 2019 compact it 1107 (ET: AUST)]*
```c
for(a=1; a<=100; a++)
    printf("%d\n", a*a);
```

    Answer:

    ```c
    a = 1;                       // initialisation moves before the loop
    while (a <= 100) {           // condition stays in the while header
        printf("%d\n", a * a);
        a++;                     // increment moves to the end of the body
    }
    ```

    How the three parts map

    | for loop part | Position in the while version |
    |---|---|
    | Initialisation `a = 1` | Written just before `while` |
    | Condition `a <= 100` | Inside the `while (...)` |
    | Increment `a++` | Last statement inside the body |

    - Both versions print the squares 1, 4, 9, ... up to 10000.
    - The only real difference is scope: with `for (int a = 1; ...)` the counter is local to the loop, whereas in the while version `a` remains visible afterwards.
    - A `continue` statement behaves differently between the two — in a `for` loop the increment still runs, but in this `while` version it would be skipped, causing an infinite loop.

93. **(a) Write a Java/C program to find the sum of the following series? $\frac{1}{1!} + \frac{2}{2!} + \frac{3}{3!} + \dots\dots\dots\dots + \frac{N}{N!}$** *[BPSC Assistant Programmer (ICT) 2019 compact it 1139 (ET: N/A)]*

    Answer: The term `i/i!` simplifies to `1/(i−1)!`, but the direct approach is to build the factorial incrementally so it is never recomputed.

    ```c
    #include <stdio.h>

    int main(void) {
        int n, i;
        double fact = 1, sum = 0;

        printf("Enter N: ");
        scanf("%d", &n);

        for (i = 1; i <= n; i++) {
            fact *= i;                   // fact now holds i!
            sum += (double)i / fact;
        }

        printf("Sum of the series = %.6lf\n", sum);
        return 0;
    }
    ```

    - For `N = 4`: `1/1 + 2/2 + 3/6 + 4/24 = 1 + 1 + 0.5 + 0.1667 = 2.6667`.
    - Carrying `fact` forward keeps the loop `O(n)`; recomputing the factorial inside each pass would make it `O(n²)`.
    - `double` is used because factorials overflow an `int` beyond `12!`.
    - As `N → ∞` this series converges to `e ≈ 2.71828`.

94. **একটি ৯ ধার বিশিষ্ট বহুভুজের প্রতিটির ধার সমান। উক্ত বহুভুজের অভ্যন্তরীণ কোন ডিগ্রিতে প্রকাশের C Program লিখুন।** *[NPCBL Junior Technical Engineer 2019 compact it 1148 (ET: BUET)]*

    Answer: For a regular polygon with `n` sides, each interior angle is `(n − 2) × 180 / n` degrees.

    ```c
    #include <stdio.h>

    int main(void) {
        int n;
        float interiorAngle;

        printf("Enter number of sides: ");
        scanf("%d", &n);

        if (n < 3) {
            printf("A polygon must have at least 3 sides\n");
            return 0;
        }

        interiorAngle = (float)(n - 2) * 180 / n;

        printf("Each interior angle = %.2f degrees\n", interiorAngle);
        return 0;
    }
    ```

    Calculation for a 9-sided regular polygon (nonagon)
    - `Interior angle = (9 − 2) × 180 / 9`
    - `= 7 × 180 / 9`
    - `= 1260 / 9`
    - `= 140 degrees`

    - Cross-check: the exterior angle is `360 / 9 = 40°`, and `180 − 40 = 140°`. Both methods agree.

95. **Write a program to find the GCD using C/C++.** *[NWPGCL Assistant Engineer (CSE) 2019 compact it 1153 (ET: RUET)]*

    Answer:

    ```c
    #include <stdio.h>

    int gcd(int a, int b) {
        if (b == 0) return a;            // base case
        return gcd(b, a % b);            // Euclid: gcd(a,b) = gcd(b, a mod b)
    }

    int main(void) {
        int a, b;
        printf("Enter two numbers: ");
        scanf("%d %d", &a, &b);
        printf("GCD of %d and %d = %d\n", a, b, gcd(a, b));
        return 0;
    }
    ```

    Dry run with `a = 54, b = 24`
    - `gcd(54, 24)` → `gcd(24, 54 % 24 = 6)`
    - `gcd(24, 6)` → `gcd(6, 24 % 6 = 0)`
    - `gcd(6, 0)` → returns `6`

    - Euclid's rule holds because any common divisor of `a` and `b` also divides `a % b`.
    - Time complexity `O(log(min(a,b)))`. The iterative version avoids the recursion stack.

96. **Write a c program to find max price from 20 items.** *[Bangladesh Bank Assistant Programmer 2019 compact it 1155 (ET: DU)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        float price[20], max;
        int i, index = 0;

        printf("Enter prices of 20 items:\n");
        for (i = 0; i < 20; i++)
            scanf("%f", &price[i]);

        max = price[0];
        for (i = 1; i < 20; i++)
            if (price[i] > max) {
                max = price[i];
                index = i;               // remember which item it was
            }

        printf("Maximum price = %.2f (item number %d)\n", max, index + 1);
        return 0;
    }
    ```

    - `float` is used because prices usually carry decimal places.
    - Keeping `index` alongside `max` reports which item had the highest price, not just the value.
    - Time `O(n)` with 19 comparisons, space `O(n)`.

97. **Write a program to calculate GPA, Avg and total marks.** *[Probashi Kallyan Bank Programmer 2019 compact it 1158 (ET: AUST)]*

    Answer: Marks are converted to grade points using the standard Bangladeshi grading scale, and the GPA is the average of those points.

    ```c
    #include <stdio.h>

    float getGradePoint(int marks) {
        if (marks >= 80) return 5.0;
        if (marks >= 70) return 4.0;
        if (marks >= 60) return 3.5;
        if (marks >= 50) return 3.0;
        if (marks >= 40) return 2.0;
        if (marks >= 33) return 1.0;
        return 0.0;
    }

    int main(void) {
        int marks[10], n, i, total = 0;
        float gradePointSum = 0, average, gpa;

        printf("Enter number of subjects: ");
        scanf("%d", &n);

        printf("Enter marks of %d subjects: ", n);
        for (i = 0; i < n; i++) {
            scanf("%d", &marks[i]);
            total += marks[i];
            gradePointSum += getGradePoint(marks[i]);
        }

        average = (float)total / n;
        gpa     = gradePointSum / n;

        printf("\nTotal marks = %d\n", total);
        printf("Average = %.2f\n", average);
        printf("GPA = %.2f\n", gpa);
        return 0;
    }
    ```

    - Example: marks `85, 75, 62, 90, 55` give total 367, average 73.40 and GPA `(5+4+3.5+5+3)/5 = 4.10`.
    - A grade point of 0 in any subject normally means the student fails overall, which a real system would check separately.

98. **Write a program of find Prime number in 1 to 100 number. (Using any language)** *[BCC-4TDC Assistant Programmer 2019 compact it 1161 (ET: BCC)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        int i, j, isPrime, count = 0;

        printf("Prime numbers from 1 to 100:\n");
        for (i = 2; i <= 100; i++) {
            isPrime = 1;
            for (j = 2; j * j <= i; j++)
                if (i % j == 0) { isPrime = 0; break; }
            if (isPrime) { printf("%d ", i); count++; }
        }
        printf("\nTotal = %d prime numbers\n", count);
        return 0;
    }
    ```

    Output
    ```
    2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97
    Total = 25 prime numbers
    ```

    - 1 is excluded because a prime must have exactly two distinct positive divisors.
    - Time complexity `O(n√n)`.

99. **Write a program of find max from 20 item price. (Using any language)** *[BCC-4TDC Assistant Programmer 2019 compact it 1161 (ET: BCC)]*

    Answer:

    ```c
    #include <stdio.h>

    int main(void) {
        float price[20], max;
        int i;

        printf("Enter prices of 20 items:\n");
        for (i = 0; i < 20; i++)
            scanf("%f", &price[i]);

        max = price[0];                  // assume the first is the highest
        for (i = 1; i < 20; i++)
            if (price[i] > max)
                max = price[i];

        printf("Maximum price = %.2f\n", max);
        return 0;
    }
    ```

    - Initialising `max` from `price[0]` rather than 0 keeps the code correct even if all prices happen to be very small.
    - Time complexity `O(n)`, space `O(n)`.

100. **Write program for following pattern:** *[BCC-4TDC Assistant Programmer 2019 compact it 1161 (ET: BCC)]*
```text
12345
1234
123
12
1
```

     Answer: An inverted number triangle — row `i` prints 1 up to `n − i + 1`, with no spaces between digits.

     ```c
     #include <stdio.h>

     int main(void) {
         int n = 5, i, j;

         for (i = n; i >= 1; i--) {       // row length falls from n down to 1
             for (j = 1; j <= i; j++)
                 printf("%d", j);
             printf("\n");
         }
         return 0;
     }
     ```

     Output
     ```
     12345
     1234
     123
     12
     1
     ```

     - The outer loop counts downward, which is what shrinks each row by one digit.
     - The inner loop always restarts at 1, so every row begins with 1.
     - Time complexity `O(n²)`.

101. **Write a c program to verify a perfect number. Perfect number is a positive integer which is equal to the sum of its proper positive divisors.** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1190 (ET: N/A)]*

     Answer: A proper divisor of `n` is a divisor smaller than `n` itself. If those divisors add up to `n`, it is a perfect number.

     ```c
     #include <stdio.h>

     int main(void) {
         int n, i, sum = 0;

         printf("Enter a positive integer: ");
         scanf("%d", &n);

         for (i = 1; i <= n / 2; i++)     // proper divisors cannot exceed n/2
             if (n % i == 0)
                 sum += i;

         if (sum == n && n > 0)
             printf("%d is a Perfect number\n", n);
         else
             printf("%d is not a Perfect number\n", n);
         return 0;
     }
     ```

     Example — n = 28
     - Proper divisors: `1, 2, 4, 7, 14`
     - Sum = `1 + 2 + 4 + 7 + 14 = 28`, which equals `n`, so 28 is perfect.

     - The loop stops at `n/2` because no proper divisor can be larger than half of `n`.
     - The first few perfect numbers are 6, 28, 496 and 8128.
     - Time complexity `O(n)`; checking only up to `√n` and adding divisor pairs reduces it to `O(√n)`.

102. **Write a program check a number is prime or not prime.** *[Jiban Bima Corporation Assistant Programmer 2018 compact it 1211-1212 (ET: N/A)]*

     Answer:

     ```c
     #include <stdio.h>

     int main(void) {
         int n, i, isPrime = 1;

         printf("Enter a number: ");
         scanf("%d", &n);

         if (n <= 1)
             isPrime = 0;                // 0, 1 and negatives are not prime
         else
             for (i = 2; i * i <= n; i++)
                 if (n % i == 0) { isPrime = 0; break; }

         if (isPrime) printf("%d is a prime number\n", n);
         else         printf("%d is not a prime number\n", n);
         return 0;
     }
     ```

     - Test: 29 is prime (no divisor up to 5), 30 is not (divisible by 2).
     - Checking only up to `√n` is valid because any factor above `√n` pairs with one below it.
     - Time complexity `O(√n)`, space `O(1)`.

103. **Suppose an array is {4,5,6,7}. Write a C program that will output like {4,5}, {4,6}, {4,7}, {5,6}, {5,7}, {6,7}.** *[NWPGCL Assistant Engineer (CSE) 2018 compact it 1212-1213 (ET: N/A)]*

     Answer: This prints every unordered pair. The inner loop starts at `i + 1` so each pair appears once and no element is paired with itself.

     ```c
     #include <stdio.h>

     int main(void) {
         int a[] = {4, 5, 6, 7};
         int n = 4, i, j, first = 1;

         for (i = 0; i < n - 1; i++) {
             for (j = i + 1; j < n; j++) {
                 if (!first) printf(", ");
                 printf("{%d,%d}", a[i], a[j]);
                 first = 0;
             }
         }
         printf("\n");
         return 0;
     }
     ```

     Output
     ```
     {4,5}, {4,6}, {4,7}, {5,6}, {5,7}, {6,7}
     ```

     - Number of pairs = `nC2 = n(n−1)/2 = 4 × 3 / 2 = 6`, matching the output.
     - Starting the inner loop at `j = 0` instead would also print `{5,4}` and `{4,4}`, which is not wanted.
     - Time complexity `O(n²)`.

104. **Write a program using any programming language that reads five numbers from keyboard and display the smaller, larger and average of those numbers.** *[Bangladesh Development Bank Senior Officer (IT) 2017 compact it 1217-1218 (ET: N/A)]*

     Answer:

     ```c
     #include <stdio.h>

     int main(void) {
         int a[5], i, sum = 0, min, max;
         float average;

         printf("Enter five numbers: ");
         for (i = 0; i < 5; i++) {
             scanf("%d", &a[i]);
             sum += a[i];
         }

         min = max = a[0];
         for (i = 1; i < 5; i++) {
             if (a[i] < min) min = a[i];
             if (a[i] > max) max = a[i];
         }

         average = (float)sum / 5;

         printf("Smallest = %d\n", min);
         printf("Largest  = %d\n", max);
         printf("Average  = %.2f\n", average);
         return 0;
     }
     ```

     - For `25, 10, 48, 7, 30`: smallest 7, largest 48, average `24.00`.
     - Both minimum and maximum are found in the same loop, so only one extra pass is needed.
     - Time `O(n)`, space `O(n)`.

105. **Write a program to read the coordinates of the end points of a line and to find its length.** *[Multiple Ministry Assistant Programmer 2017 compact it 1231 (ET: N/A)]*

     Answer: The distance formula is `d = √[(x₂ − x₁)² + (y₂ − y₁)²]`.

     ```c
     #include <stdio.h>
     #include <math.h>

     int main(void) {
         float x1, y1, x2, y2, length;

         printf("Enter coordinates of first point (x1 y1): ");
         scanf("%f %f", &x1, &y1);
         printf("Enter coordinates of second point (x2 y2): ");
         scanf("%f %f", &x2, &y2);

         length = sqrt((x2 - x1) * (x2 - x1) + (y2 - y1) * (y2 - y1));

         printf("Length of the line = %.2f units\n", length);
         return 0;
     }
     ```

     Example — points (1, 2) and (4, 6)
     - `dx = 4 − 1 = 3`, `dy = 6 − 2 = 4`
     - `length = √(9 + 16) = √25 = 5.00`

     - The formula is simply the Pythagorean theorem applied to the horizontal and vertical gaps.
     - `math.h` must be included for `sqrt()`, and on Linux the program is compiled with `gcc file.c -lm`.

106. **Write a program in C++ to calculate the sum of the series: $1+(1+2)+(1+2+3)+\dots\dots+(1+2+\dots\dots+n)$.** *[Multiple Ministry Assistant Programmer 2017 compact it 1232 (ET: N/A)]*

     Answer: Each group is a triangular number `i(i+1)/2`, so the whole series is the sum of triangular numbers.

     ```cpp
     #include <iostream>
     using namespace std;

     int main() {
         int n, i, term = 0, sum = 0;

         cout << "Enter n: ";
         cin >> n;

         for (i = 1; i <= n; i++) {
             term += i;                   // term now holds 1+2+...+i
             sum  += term;
         }

         cout << "Sum of the series = " << sum << endl;
         cout << "Formula check n(n+1)(n+2)/6 = "
              << n * (n + 1) * (n + 2) / 6 << endl;
         return 0;
     }
     ```

     Verification for `n = 4`
     - Groups: `1`, `1+2 = 3`, `1+2+3 = 6`, `1+2+3+4 = 10`
     - Sum = `1 + 3 + 6 + 10 = 20`
     - Formula: `4 × 5 × 6 / 6 = 20`. Both agree.

     - Carrying `term` forward keeps the loop `O(n)`; a nested loop would make it `O(n²)`.

107. **Write a program to find out the minimum number from a series.** *[BTCL Assistant Manager (Technical) 2017 compact it 1254 (ET: N/A)]*

     Answer:

     ```c
     #include <stdio.h>

     int main(void) {
         int n, i, num, min;

         printf("How many numbers? ");
         scanf("%d", &n);

         printf("Enter number 1: ");
         scanf("%d", &min);               // first number is the initial minimum

         for (i = 2; i <= n; i++) {
             printf("Enter number %d: ", i);
             scanf("%d", &num);
             if (num < min) min = num;
         }

         printf("Minimum number = %d\n", min);
         return 0;
     }
     ```

     - The numbers are compared as they arrive, so no array is needed — space stays `O(1)`.
     - Taking the first value as the starting minimum is what makes the code correct for negative inputs too.
     - Time complexity `O(n)`.

108. **Write a C program to reverse an integer number.** *[BCC Assistant Programmer 2017 compact it 1256-1257 (ET: N/A)]*

     Answer:

     ```c
     #include <stdio.h>

     int main(void) {
         int n, digit, rev = 0, sign = 1;

         printf("Enter an integer: ");
         scanf("%d", &n);

         if (n < 0) { sign = -1; n = -n; }   // handle a negative input

         while (n != 0) {
             digit = n % 10;
             rev = rev * 10 + digit;
             n /= 10;
         }

         printf("Reversed number = %d\n", rev * sign);
         return 0;
     }
     ```

     - For `12345` the output is `54321`; for `-670` it is `-76`.
     - `rev * 10` shifts the digits already collected one place to the left, making room for the new one.
     - Time complexity `O(d)`, space `O(1)`.

109. **Write a C program to acending (A-Z) using selection sort.** *[BCC Assistant Programmer 2017 compact it 1257 (ET: N/A)]*

     Answer: Selection sort applied to characters — the same algorithm works, since characters compare by their ASCII values.

     ```c
     #include <stdio.h>
     #include <string.h>

     int main(void) {
         char str[100], temp;
         int i, j, min, len;

         printf("Enter a string: ");
         scanf("%s", str);
         len = strlen(str);

         for (i = 0; i < len - 1; i++) {
             min = i;
             for (j = i + 1; j < len; j++)
                 if (str[j] < str[min])
                     min = j;
             if (min != i) {                 // swap into place
                 temp = str[i];
                 str[i] = str[min];
                 str[min] = temp;
             }
         }

         printf("Sorted string (A-Z): %s\n", str);
         return 0;
     }
     ```

     - For input `DBCA` the output is `ABCD`.
     - Uppercase letters have ASCII values 65 to 90 and lowercase 97 to 122, so mixed-case input sorts all uppercase letters before lowercase ones.
     - Time complexity `O(n²)`, space `O(1)`.

110. **Write a structured program to display Fibonacci series up to 100 Numbers.** *[Bangladesh Bank Assistant Programmer 2016 compact it 1265 (ET: N/A)]*

     Answer: "Structured" means the logic is split into a separate function rather than sitting entirely inside `main`.

     ```c
     #include <stdio.h>

     void printFibonacci(int n) {
         int i;
         long long first = 0, second = 1, next;

         if (n >= 1) printf("%lld ", first);
         if (n >= 2) printf("%lld ", second);

         for (i = 3; i <= n; i++) {
             next = first + second;
             printf("%lld ", next);
             first = second;
             second = next;
         }
     }

     int main(void) {
         printf("Fibonacci series (100 terms):\n");
         printFibonacci(100);
         return 0;
     }
     ```

     - `long long` is essential here — the 93rd Fibonacci number already exceeds the range of a 32-bit `int`.
     - Even `long long` overflows around the 93rd term, so printing all 100 terms exactly would need an unsigned 128-bit type or big-integer arithmetic.
     - Time `O(n)`, space `O(1)`.

111. **Write a program in any language to find out maximum among three numbers.** *[DESCO Assistant Engineer (CSE) 2016 compact it 1267 (ET: N/A)]*

     Answer:

     ```c
     #include <stdio.h>

     int main(void) {
         int a, b, c, max;

         printf("Enter three numbers: ");
         scanf("%d %d %d", &a, &b, &c);

         max = a;                         // assume the first is largest
         if (b > max) max = b;
         if (c > max) max = c;

         printf("Maximum = %d\n", max);
         return 0;
     }
     ```

     - Alternative with nested conditions: `if (a >= b && a >= c) max = a; else if (b >= c) max = b; else max = c;`
     - The running-maximum form is preferred because it extends unchanged to any number of values.
     - Only 2 comparisons are needed, which is the minimum for three values. Time complexity `O(1)`.

## Output Tracing & Control Flow (57)

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

3. **(b) Find out the output of this program.**
```c
for (int i= 5; i>=1; i--) {
    for (int j=1; j<=i; j++) {
        printf("%3d", j);
    }
}

```
*[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1444 (ET: N/A)]*

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

31. **After compilation and execution, what will be output in the following code:** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 972 (ET: BUET)]*

32. **Write down the output of following program:** *[NACTAR Assistant Instructor (ICT) 2020 compact it 991 (ET: N/A)]*

33. **What will be the output in C and java code? (i) C program:** *[Combined 4 Banks Assistant Programmer 2020 compact it 1003 (ET: DU)]*

34. **a) Using Pseudocode give an example of run time error.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1035-1036 (ET: BUET)]*

35. **Find the Output:** *[Sundharban Gas Assistant Programmer 2020 compact it 1047 (ET: N/A)]*

36. **Find the error of given code** *[Combined 5 Banks Assistant Maintenance Engineer 2019 compact it 1055 (ET: AUST)]*
```c
Unsigned inti
For(i=100; i<=0; --i)
    Printf("%d",i);
```

37. **What is the output of following code?** *[Bangladesh Competition Commission Programmer 2019 compact it 1062 (ET: DU)]*
```c
#include<stdio.h>
void main () {
    char *f [] = {"Ronaldo", "Messi", "Zidan", "Maradona"}, str[20];
    printf("%s\n", f[1]+2);
    printf("%s", f[2]+1);
}
```

38. **Find the output of a program:** *[DESCO Assistant Engineer (CSE) 2019 compact it 1117 (ET: BUET)]*
```c
#include<stdio.h>
int main() {
    char s[200], s1[200];
    gets(s);
    gets(s1);
    fun(s, s1);
    return 0;
}
int fun(char *s, char *sup) {
    if(s=="\0")
        return;
    else if(s==sup)
        fun(s+1, sup+1);
    else {
        printf("%s\n", s);
        fun(s+1, sup);
    }
}
```

39. **Find the output of the code:** *[DESCO Sub-Assistant Engineer (CSE) 2019 compact it 1120 (ET: BUET)]*
```c
#include <stdio.h>
#define x 9+2/4*3-2*4+(5-4)*3
void main() {
    int i,y;
    y=6+3*3/5;
    i=x*x+y;
    printf("%d",i);
}
```

40. **What is the output of the following program?** *[NPCBL Junior Technical Engineer 2019 compact it 1148 (ET: BUET)]*
```c
#define x 9+2/4*3-2*4+(5-4)*3
int main() {
    int i;
    int y;
    y=6+3*3/5;
    i=x*x+y;
    printf("%d",i);
    return 0;
}
```

41. **Find the output of the following code:** *[Dutch Bangla Bank Assistant Network/Hardware Engineer 2019 compact it 1160 (ET: BUET)]*
```c
int a=3; int b=10;
if(a>b)
    printf("A");
else
    printf("B");
```

42. **Find the output of the following code:** *[Dutch Bangla Bank Assistant Network/Hardware Engineer 2019 compact it 1160-1161 (ET: BUET)]*
```c
int i=0; int n=3;
while(i!=n) {
    if(i==3)
        continue;
    printf("%d", i);
    i++;
}
```

43. **What is the output of following program?** *[Sonali & Janata Bank Senior Officer (IT/ICT) 2018 compact it 1166 (ET: N/A)]*

44. **Find the output of following program.** *[Palli Sanchay Bank Assistant Programmer 2018 compact it 1169 (ET: N/A)]*
   i)
```c
int main() {
    int n = 10;
    for(;;)
        printf("%d", n);
    return 0;
}
```
   ii)
```c
int main() {
    int i = 2, j = 2;
    while (i?--i:j++)
        printf("%d", i);
    return 0;
}
```

45. **Find the output following program:** *[Palli Sanchay Bank Assistant Database Administrator 2018 compact it 1170 (ET: N/A)]*
```c
int main() {
    int a=5, b=2, c=1;
    if (a&&b>c)
        printf("Bangladesh");
    else
        break;
}
```

46. **Find the output of following program.** *[Palli Sanchay Bank Programmer 2018 compact it 1171 (ET: N/A)]*
   i)
```c
int main() {
    char str[120]= "Digital Bangladesh";
    int n;
    n = strlen(str);
    str[4] = '\0';
    printf("%s", str);
    return 0;
}
```
   ii)
```c
int main() {
    int i;
    for (i=0; i<5; i++) {
        if(i==3)
            continue;
        printf("%d\n", i);
    }
    return 0;
}
```

47. **What will be the output of following program?** *[Bangladesh Water Development Board Assistant Programmer 2018 compact it 1190 (ET: N/A)]*
```c
#include <stdio.h>
int main() {
    int i=-1, j=-1, k=0, l=2, m;
    m= i++ && j++ && k++ || l++;
    printf("%d %d %d %d %d", i, j, k, l, m);
    return 0;
}
```

48. **Write output:** *[Jiban Bima Corporation Assistant Programmer 2018 compact it 1212 (ET: N/A)]*
```c
#include<stdio.h>
#include<string.h>
int main() {
    char str1[20]="Bangladesh";
    char str2;
    str1[4]='\0';
    str2=strlen(str1);
    printf("%s",str1);
    return 0;
}
```

49. **Write output:** *[Jiban Bima Corporation Assistant Programmer 2018 compact it 1212 (ET: N/A)]*
```c
#include<stdio.h>
int main() {
    int i;
    for(i=0;i<5;++i) {
        if(i==3)
            continue;
        printf("%d ",i);
    }
    return 0;
}
```

50. **Find output:** *[NWPGCL Assistant Engineer (CSE) 2018 compact it 1213 (ET: N/A)]*
```cpp
#include<stdio.h>
int main() {
    int i=1,j=1,k=1;
    cout<<++i || ++j && ++k;
    cout<<i<<j<<k;
    return 0;
}
```

51. **Find the mistake in the following program and write it correct form.** *[Investment Corporation Bangladesh Assistant Programmer 2017 compact it 1216 (ET: N/A)]*
```c
unsigned int i;
for(i=100; i<=0; --i)
printf("%d",i);
return 0;
```

52. **Find the output of a program.** *[BTCL Assistant Manager (Technical) 2017 compact it 1255 (ET: N/A)]*
```c
#include<stdio.h>
#define N 7
void main() {
    char str[] = "abpqx";
    for(int i=0; i<N-2; i++)
        if(i%2) printf("%d ", str[i]++);
        else printf("%d ", str[i]--);
}
```

53. **Write output:** *[BCC Assistant Programmer 2017 compact it 1257 (ET: N/A)]*
```c
#include <stdio.h>
int main() {
    int i=-20, j=-1, k=2,m;
    m=++i && ++j && ++k;
    printf("%d, %d, %d, %d\n", i,j,k,m);
    return 0;
}
```

54. **Write output:** *[BCC Assistant Programmer 2017 compact it 1257-1258 (ET: N/A)]*
```c
#include <stdio.h>
int main() {
    int a=0, b=1, c=2;
    *((a)?&b:&a)=a?b:c;
    printf("%d, %d, %d\n",a,b,c);
    return 0;
}
```

55. **Write output:** *[BCC Assistant Programmer 2017 compact it 1258 (ET: N/A)]*
```c
#include <stdio.h>
int main() {
    float n=2;
    switch(n) {
        case 2:
            printf("Hi");
            break;
        default:
            printf("Hello");
    }
    return 0;
}
```

56. **Write output:** *[DESCO Assistant Engineer (CSE) 2016 compact it 1268 (ET: N/A)]*
```c
#include<stdio.h>
#define max(a,b) (a>b?a:b)
int main() {
    int i=1,j=2,k=0;
    k=max(i++,++j);
    printf("%d",k);
    return 0;
}
```

57. **Write output:** *[DESCO Assistant Engineer (CSE) 2016 compact it 1268 (ET: N/A)]*
```c
#include <stdio.h>
int sum(int i) {
    static int total=0;
    total+=i;
    return total;
}
int main() {
    int i;
    for(i=1; i<10; i++) {
        printf("%d ", sum(i));
    }
}
```

## Recursion & Functions (38)

1. (a) Microprocessor এবং Microcontroller এর মধ্যে পার্থক্য লিখুন।
   (b) কোন প্রোগ্রামিং ভাষাকে 'C' programming language বলা হয়? একটি ছোট প্রোগ্রাম লিখুন, যা recursive function ব্যবহার করে ডিসপ্লেতে ৫ এর ফ্যাক্টোরিয়াল গণনা করবে। *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

2. **Write a C program to find the sum of digits of an integer number using "recursion".** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1338 (ET: N/A)]*

3. **What is recursion?** *[BBA Assistant Programmer 12.07.2025 compact it 1432 (ET: BUET)]*

4. **Write recursive way below this program:** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 417 (ET: BUET)]*
```c
for(int i=1, i<n; i++)
    for(int j=0 ; j<i ; j ++)
        For( int k =0; k<i ; k++)
            X=X+1
```

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

7. **What is function?** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*

8. **Write a C/C++ program to calculte factorial of N using recursive function.** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 472 (ET: N/A)]*

9. **Write the recursive function of the below problem and find the recurrence relation of the function. F(n) = 1+2+3+..........+(n-1)+n** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 472 (ET: N/A)]*

10. **(a) Mention two basic differences between ‘Call by Value’ and ‘Call by Reference’. Write a simple program in C to swap two integer values using ‘Call by value’.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 487 (ET: N/A)]*

11. **(b) Write a program in C using recursion to find the factorial of an integer.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 492 (ET: N/A)]*

12. **When a function is called more than one time that is called?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

13. **(e) Write about the syntax of function.** *[BARC Programmer 04.08.2023 compact it 598 (ET: N/A)]*

14. **(ক) C প্রোগ্রামিং ল্যাঙ্গুয়েজে user defined function এবং library function এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 600 (ET: N/A)]*

15. **(ক) Call by Value এবং Call by Reference এর মধ্যে পার্থক্য কী?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 617 (ET: N/A)]*

16. **(ঘ) উদাহরণসহ Parameter Passing ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 617 (ET: N/A)]*

17. **(খ) উদাহরণসহ recursion ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*

18. **(ক) Tower of Hanoi সমস্যাটি সমাধানের জন্যে একটি recursive অ্যালগরিদম লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*

19. **What are the differences between call by value and call by Reference?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)], [BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 677 (ET: N/A)]*

20. **Distinguish between Call by value and Call by referee in C/C++.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 670 (ET: N/A)]*

21. **Write a recursive algorithm to find the factorial of a positive integer from 1 to N.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*

22. **What do you mean by recursion? Calculate factorial function using recursion with C programming code.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 679 (ET: N/A)]*

23. **Write a program with a recursive function that shows the sum of its digits. For example, input =3426, output will be 3+4+2+6=15.** *[GTCL Assistant Engineer (CSE) 2022 compact it 684 (ET: BUET)]*

24. **(a) Write down a recursive function to find out number of digits is an integer number (n). Draw the recursion tree when n= 5396.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 690 (ET: N/A)]*

25. **(খ) Recursion কি? Recursion পদ্ধতিতে একটি Integer সংখ্যার Factorial নির্ণয়ের জন্য C-Language এ একটি Program লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 767 (ET: N/A)]*

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

27. **(b) Write down a pseudocode/program to generate all possible permutation for a given word.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 793 (ET: N/A)]*

28. **Paython এ Recursive function ব্যবহার করে একটি ধনাত্মক সংখ্যার factorial মান বের করার function লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 866 (ET: BUET)]*

29. **Write a program in C/Java to find out the factorial of a number using recursion also write its iterative program.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*

30. **১. পাইথন প্রোগ্রামিং এর রিকার্সিভ ফাংশন ব্যবহার করে ১০টি সংখ্যার যোগফল বের করার প্রোগ্রাম লিখ।** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 946 (ET: BUET)]*

31. **(ii) Recursion কী? Recursion পদ্ধতির একটি Simple C-programming এর Code লিখুন।** *[BPSC Assistant Network Engineer 2020 compact it 954 (ET: N/A)]*

32. **Usually, recursion involves a function calling itself until specified condition is met and it is very useful to find out the factorial. Write a recursive algorithm to find the factorial of a number.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 985 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

33. **(a) Write down a function to compute the sum of the row an $n \times m$ matrix of integer.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1130-1131 (ET: N/A)]*

34. **What is recursive function? Give an example of recursive function.** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1152 (ET: KUET)]*

35. **Difference between call by value and call by reference with example.** *[Palli Sanchay Bank Assistant Programmer 2018 compact it 1166-1167 (ET: N/A)]*

36. **Write Algorithm of Fibonacci series.** *[Palli Sanchay Bank Programmer 2018 compact it 1171-1172 (ET: N/A)]*

37. **Write the performance of a non-recursive function which is written in recursive way.** *[Agrani Bank Ltd. Officer (ICT) 2017 compact it 1224 (ET: N/A)]*

38. **Write a program in C with recursive function to compute the value $X^n$ where n is a positive integer and x has real value.** *[Multiple Ministry Assistant Programmer 2017 compact it 1235-1236 (ET: N/A)]*

## Operators, Data Types & Language Concepts (25)

1. **(b) What is the difference between sizeof c+1 and sizeof (c+1)?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 483 (ET: N/A)]*

2. **What is the difference between Null and Void?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*

3. **What can be used to terminate for(;;)?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

4. **What will occur when an array is declared without size?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

5. **(ক) Local variable এবং Global variable এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 601 (ET: N/A)]*

6. **(খ) আমি কী ৩২৬৭৮ মান সংরক্ষণ করতে ‘int’ ডাটা টাইপ ব্যবহার করতে পারি? না পারলে কেন?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 617 (ET: N/A)]*

7. **(গ) ‘++i’ এবং ‘i++’ অভিব্যক্তি দুটির মধ্যে পার্থক্য কী? উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 617 (ET: N/A)]*

8. **What is the main difference between structure and array in C programming? Explain with examples.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 635 (ET: N/A)]*

9. **Difference between array and structure data type.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 679 (ET: N/A)]*

10. **Write down the types of errors which can occur the execution of a program.** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*

11. **Write the syntax of while and do while loop.** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

12. **What is nested structure in C programming? Explain with example.** *[SPCB Sub-Assistant Programmer 2022 compact it 741 (ET: N/A)]*

13. **(ii) C Programming Language এ Array and Structure এর মধ্যে পার্থক্য লিখুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 784 (ET: N/A)]*

14. **Write some default data type in C.** *[BCC CA Monitoring System Project 2021 compact it 830 (ET: N/A)]*

15. **Write the difference between Structure and Array.** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922 (ET: N/A)]*

16. **Short question: (i) Difference between ++i and i++ (ii) Difference between Overloading and Overriding (iii) Polymorphism in Java (iv) String variable (v) Control structure in C programming (vi) Stack (vii) Debugging (viii) Increment and Decrement process in C programming (ix) Object in C++ (x) Data encapsulation** *[National University Assistant Programmer 2020 compact it 978-980 (ET: DU)]*

17. **নিচের if-else কে switch case এ পরিনত করুন। if(ch== 'A':: ch== 'E' :: ch== 'I' :: ch == 'O':: ch== 'U')** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1021 (ET: N/A)]*

18. **Answer the following question:** *[Bangladesh Competition Commission Programmer 2019 compact it 1063 (ET: DU)]*
   a. Polymorphism refers to \_\_\_\_\_\_\_?
   b. What is the simplest method to prove that a graph is bipartite?
   c. In C what is the correct syntax to a send a 3- dimension array as a parameter?
   d. The Size of the character variable in C is \_\_\_\_\_?
   e. In Java what is true about private constructor?

19. **Coding এর সময় সংঘটিত ভুলসমূহ উদাহরণসহ ব্যাখ্যা করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1080 (ET: N/A)]*

20. **উদাহরণসহ i++ and ++i এর মধ্যে পার্থক্য লিখুন। Nested if কী?** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1082 (ET: N/A)]*

21. **(খ) C প্রোগ্রামিং ল্যাঙ্গুয়েজে Structure ও Union এর মধ্যে পার্থক্য কী? উদাহরণসহ লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1083 (ET: N/A)]*

22. **Which of the following is the correct order of evaluation?** *[BREB Assistant Hardware & Network Engineer 2019 compact it 1124 (ET: BREB)]*

23. **(c) Is it possible to convert all if-else code into switch code block? Give an example.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1130-1131 (ET: N/A)]*

24. **Using examples explain data types used in C language.** *[Multiple Ministry Assistant Programmer 2017 compact it 1231 (ET: N/A)]*

25. **Explain in details the different forms of looping statement in C language.** *[Multiple Ministry Assistant Programmer 2017 compact it 1233-1235 (ET: N/A)]*

## Flowcharts & Algorithms (16)

1. **Draw and clearly describe a step-by-step flowchart for a User Login system. Your login must include: Taking a Username and Password as input. Checking the database. If correct: Granting access. If wrong: Adding 1 to a failed attempt counter. Access denied and block the account if the counter reaches 3.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

2. **Draw a Flow chart for print odd number for 1 to N.** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*

3. **১ থেকে ১০০ পর্যন্ত নাম্বার প্রদর্শনের ফ্লোচার্ট আক।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 381 (ET: BUET)]*

4. **দুইটি সংখ্যার গ.সা.গু নির্ণয়ের জন্য ফ্লোচার্ট অঙ্কন করুন ও অ্যালগরিদম লিখুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 406 (ET: N/A)]*

5. **Write Algorithm and flowchart to find odd numbers between 1 to n where n is a positive integer.** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 596 (ET: N/A)]*

6. **Write Algorithm and flowchart for printing 1+3+5+ \dots + N.** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 643 (ET: BUET)]*

7. **Write an Algorithm to check a number is Prime or not Prime.** *[NSDA Assistant Programmer Date: 04-03-2022 compact it 656 (ET: N/A)]*

8. **Write down the algorithm and draw the flowchart of Quadratic equation.** *[CAAB Programmer 2022 compact it 722 (ET: N/A)]*

9. **Draw a flowchart and write algorithm for finding Factorial value of an integer number.** *[CAAB Assistant Maintenance Engineer (AME) 2022 compact it 723 (ET: N/A)]*

10. **Draw a flowchart of the following series: 1+3+5+7+\dots+N** *[CAAB Assistant Programmer (AP) 2022 compact it 725 (ET: N/A)]*

11. **(খ) Algorithm কি? Algorithm প্রকাশের তিনটি পদ্ধতির নাম লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 770 (ET: N/A)]*

12. **Three types of control statements and their graphical presentation using flowchart or flow graph.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1037-1038 (ET: BUET)]*

13. **(ক) Loop কী? প্রবাহচিত্রসহ এর গঠন ব্যাখ্যা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1084 (ET: N/A)]*

14. **Write a pesudcode that takes in one positive number only and returns the factor for that number.** *[Combined Bank Senior Officer (IT/ICT) 2019 compact it 1113 (ET: DU)]*

15. **Write down the psudo-code that accepts i, n is integer and value as input, store all n integers in an array, called pairs and return all pairs where the summation of individual's pair=value.** *[Sonali & Janata Bank Senior Officer (IT/ICT) 2018 compact it 1165 (ET: N/A)]*

| Length: | Input | Output |
|---|---|---|
| Array | 5 | {1,5}, {7,-1} |
| Summation value: | 1 7 -1 5 -7 |  |
|  | 6 |  |

16. **Draw flowchart to input five positive numbers and sort them is ascending order.** *[Combined 3 Banks Assistant Programmer 2018 compact it 1199 (ET: N/A)]*

## String Manipulation & Algorithms (14)

1. **Write a C or Java program to convert string to integer without using any built-in function.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1362 (ET: BUET)]*

2. **Write a C program to check whether a string is a Palindrome.** *[BUET Assistant Programmer 21.06.2025 compact it 1433 (ET: BUET)]*

3. **Write a C program upper case to lower case conversion.** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 475 (ET: N/A)]*

4. **String reverse program but without without using the library function.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 660 (ET: N/A)], [BREB Assistant Programmer 18.02.2023 compact it 468 (ET: N/A)]*

5. **Write a C program to remove given character from string: Example input: programming and we want to remove: gram now output: proming without having the gram from string.** *[RPGCL Assistant Manager (ICT) 2022 compact it 652 (ET: BUET)]*

6. **Write a program IPv4 IP validation from given IP with valid and not valid.** *[RPGCL Assistant Manager (ICT) 2022 compact it 653 (ET: BUET)]*

7. **Find occurrence of a Character in a string. String: Bangladesh is a big country. Sample Input: b, Output: 2 times Sample Input p, Output: Not foud this letter** *[BKSP Assistant Programmer 03.12.2022 compact it 729 (ET: N/A)]*

8. **What is the purpose of '\0' character in C?** *[BCC CA Monitoring System Project 2021 compact it 830 (ET: N/A)]*

9. **(c) Write down a program to find length of a string without using any library function.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 892 (ET: N/A)]*

10. **Write a program to read a character “lower case ” and convert it into upper case.** *[BAUST Assistant Programmer 2021 compact it 918-919 (ET: N/A)]*

11. **Given a IPv4 address string, write C/C++/JAVA code to show the class the IP address belongs to.** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 923-924 (ET: CTI)]*
   Sample Input: 192.168.0.0
   Sample Output: Class C

12. **(b) Write down a C function to sort a list of strings in alphabetic order.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1130-1131 (ET: N/A)]*

13. **(a) Write an algorithm to find Palindrome number.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1140 (ET: N/A)]*

14. **Check string str2 is superscript of string str1.** *[NESCO Manager (Software) 2018 compact it 1209-1210 (ET: N/A)]*

| Input | Output |
|---|---|
| str1=x str2=x^x | Yes |
| str1=x str2=x^2 | No |

## File Handling (4)

1. Name Top C 5 File Management Function Name. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

2. **Write a function in Python programming language which takes a filename as parameter, orders first 10 line in output.** *[BCC Assistant Programmer 12.02.2021 compact it 814 (ET: BUET)]*

3. **You have a file name accounts.txt which contain the following information. Now write a C/C++/Java program to find the following: Total balance of saving account, Find the highest and second highest balance of saving account.** *[NRCC Assistant Programmer 2021 compact it 931-932 (ET: N/A)]*

4. **Folder থেকে একটি Image নিয়ে ঐ Image এর নামের .jpeg extention কে .png extention এ convert করার জন্য Python language এর Function লিখুন?** *[PGCB Sub-Assistant Engineer (CSE) 2020 compact it 1046 (ET: BUET)]*

## Pointers (4)

1. **অথবা, (ক) Pointer কী? Pointer ব্যবহারের সুবিধাগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 600 (ET: N/A)]*

2. **(গ) পয়েন্টার কী? Malloc( ) এবং Calloc( ) এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*

3. **Describe Dynamic memory allocation in programming in C?** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*

4. **(a) What is the difference between array and pointer?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 891-892 (ET: N/A)]*

## Command Line Arguments & Basic Programs (1)

1. **Write a C program that takes inputs integer values from command line interface and print the summation of the integers.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1361 (ET: BUET)]*
