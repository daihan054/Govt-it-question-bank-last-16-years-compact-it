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

   Answer: The question is `incomplete` — the paper printed a code snippet that was not captured, so the specific program cannot be traced. The traps that C output questions test are set out below, with worked examples, so the method is available whatever the missing code was.

   1. Integer division truncates
   ```c
      printf("%d", 5/2);        // 2   , not 2.5
      printf("%f", 5/2.0);      // 2.500000  - one operand is a double
      printf("%d", -5/2);       // -2  , C truncates TOWARDS ZERO
      printf("%d", -5%2);       // -1  , the remainder takes the sign of the left
   ```

   2. Pre-increment and post-increment
   ```c
      int i = 5;
      printf("%d", i++);        // prints 5 , then i becomes 6
      printf("%d", ++i);        // i becomes 7 first , then prints 7
   ```

   3. Type promotion and format specifiers
   ```c
      char c = 'A';
      printf("%d", c);          // 65  - the ASCII value
      printf("%c", 66);         // B

      float f = 3.7;
      printf("%d", (int)f);     // 3   - the fraction is discarded
   ```

   4. sizeof
   ```c
      printf("%lu", sizeof(int));      // 4 on a typical machine
      printf("%lu", sizeof(char));     // 1, ALWAYS
      printf("%lu", sizeof("hello"));  // 6 - five characters plus '\0'

      int a[10];
      printf("%lu", sizeof(a));        // 40
      void f(int a[]) { sizeof(a); }   // 8 - an array DECAYS to a pointer
   ```

   5. The `=` versus `==` trap
   ```c
      int x = 5;
      if (x = 0)  printf("A");     // ASSIGNS 0, which is false -> nothing
      if (x == 0) printf("B");     // compares
   ```

   6. Missing `break` in a switch — fall-through
   ```c
      int x = 2;
      switch (x) {
          case 1: printf("1");
          case 2: printf("2");     // no break
          case 3: printf("3");     // falls through
          default: printf("D");
      }
      // Output : 23D
   ```

   7. Loop with a misplaced semicolon
   ```c
      for (i = 0; i < 5; i++);     // the semicolon ENDS the loop
          printf("%d", i);         // runs ONCE, printing 5
   ```

   8. Array index out of range
   ```c
      int a[5] = {1,2,3,4,5};
      printf("%d", a[5]);          // UNDEFINED - a[5] does not exist
   ```

   9. String and pointer basics
   ```c
      char s[] = "hello";
      printf("%d", strlen(s));     // 5
      printf("%lu", sizeof(s));    // 6 - includes '\0'
      printf("%c", *(s+1));        // e
      printf("%s", s+1);           // ello
   ```

   10. Static and scope
   ```c
      void f() {
          static int c = 0;        // initialised ONCE, keeps its value
          int d = 0;               // reset on every call
          printf("%d %d", ++c, ++d);
      }
      f(); f(); f();               // 1 1  2 1  3 1
   ```

   - The general method for any such question: `evaluate the expression exactly as C does` — apply the precedence table, note every side effect and its sequence point, watch for implicit type conversion, and check whether the format specifier matches the argument's type. Most output questions are built on one of the ten traps above.

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

   Answer: Output is `0 0 1 3 1`.

   Step-by-step evaluation of `m = i++ && j++ && k++ || l++`
   - `&&` binds tighter than `||`, so the expression is `(i++ && j++ && k++) || l++`.
   - `i++` returns the old value `−1`, which is non-zero (true), and `i` becomes `0`.
   - `j++` returns `−1`, true, and `j` becomes `0`.
   - `k++` returns `0`, which is false, and `k` becomes `1`.
   - So the whole `&&` chain is false. Because `false || X` still needs `X`, the right operand runs.
   - `l++` returns `2`, which is true, and `l` becomes `3`.
   - `false || true` is true, so `m = 1`.

   Final values

   | Variable | Value |
   |---|---|
   | i | 0 |
   | j | 0 |
   | k | 1 |
   | l | 3 |
   | m | 1 |

   - Key point: in C, `−1` is true because only `0` is false. And short-circuiting did not stop the `&&` chain early here, since the first two operands were both true.

3. **(b) Find out the output of this program.**
```c
for (int i= 5; i>=1; i--) {
    for (int j=1; j<=i; j++) {
        printf("%3d", j);
    }
}

```
*[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1444 (ET: N/A)]*

   Answer: Output is everything on a single line, because there is no `printf("\n")` anywhere:

   ```
     1  2  3  4  5  1  2  3  4  1  2  3  1  2  1
   ```

   Trace
   - `i = 5` → inner loop prints `1 2 3 4 5`
   - `i = 4` → prints `1 2 3 4`
   - `i = 3` → prints `1 2 3`
   - `i = 2` → prints `1 2`
   - `i = 1` → prints `1`

   - `%3d` right-aligns each number in a field 3 characters wide, so each value is preceded by two spaces.
   - Total numbers printed = `5 + 4 + 3 + 2 + 1 = 15`.
   - Adding `printf("\n")` after the inner loop would turn this into the familiar inverted triangle.

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

   (A) Output is `Devel`, and `len` becomes `5`.
   - `"Development"` occupies indices 0 to 10. Writing `'\0'` at index 5 replaces `'o'` with the string terminator.
   - `printf("%s", ...)` stops at the first `'\0'`, so only `D e v e l` is printed.
   - `strlen` counts characters before the first `'\0'`, giving 5 instead of the original 11.
   - The remaining characters `pment` are still in memory but are now unreachable through normal string functions.

   (B) Output is `1`.
   - Iteration 1: `i` is 2, which is true, so `--i` runs → `i` becomes 1, and 1 is true → body runs and prints `i`, which is now `1`.
   - Iteration 2: `i` is 1, true, so `--i` → `i` becomes 0, and 0 is false → the loop ends without printing.
   - `j` is never touched, because the false branch of the conditional is never taken while `i` is non-zero.

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

   Answer: The program does not compile. It contains several errors.

   Errors present
   - `cout` is used but only `<stdio.h>` is included. `cout` belongs to C++ and needs `<iostream>` plus `using namespace std;`.
   - The text `km 101` is not valid C or C++ — it appears to be a transcription error in the question paper.
   - Both `cout` statements are missing their terminating semicolons.

   What the intended expression would produce
   - Taking the intended line as `cout << (++i || ++j && ++k);` with `i = j = k = 1`:
   - `&&` binds tighter than `||`, so it is `++i || (++j && ++k)`.
   - `++i` makes `i = 2`, which is true. Because `||` short-circuits, the right side is never evaluated.
   - So `j` and `k` stay at `1`, the expression prints `1`, and the next line prints `211`.
   - Full intended output: `1211`.

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

   Answer: Output is `57`.

   Step-by-step
   - `5 * p` promotes the integer 5 to float, giving `5 × 10.5 = 52.5`.
   - `52.5 + 5.0 = 57.5`.
   - Assigning a float to an `int` truncates toward zero — the fractional part is discarded, not rounded.
   - So `a = 57`, and `printf("%d", a)` prints `57`.

   - Note the difference: truncation gives 57, whereas rounding would have given 58. C assignment always truncates.

7. **Explain following program while part in step for the input 1221 and 3456 and also write the output of the program. (সম্পূর্ণ প্রশ্ন সংগ্রহ করা সম্ভব হয় নি!!)** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 463 (ET: BUET)]*

   Answer: The question is `incomplete` — the paper itself records that the full program could not be collected. Without the loop body the exact output cannot be produced. The standard program that this question describes is the `digit-processing while loop`, traced below for the two given inputs, `1221` and `3456`.

   The usual program — reverse a number, or test it for a palindrome
   ```c
   #include <stdio.h>

   int main() {
       int n, rev = 0, digit, original;

       printf("Enter a number: ");
       scanf("%d", &n);
       original = n;

       while (n > 0) {              // the 'while part' the question refers to
           digit = n % 10;          // take the LAST digit
           rev = rev * 10 + digit;  // append it to the reversed number
           n = n / 10;              // remove the last digit
       }

       printf("Reversed: %d\n", rev);
       if (rev == original)
           printf("It is a PALINDROME\n");
       else
           printf("It is NOT a palindrome\n");

       return 0;
   }
   ```

   Step-by-step trace for input `1221`
   ```
      n = 1221 , rev = 0 , original = 1221

      Iteration 1 : digit = 1221 % 10 = 1
                    rev   = 0*10 + 1   = 1
                    n     = 1221 / 10  = 122

      Iteration 2 : digit = 122 % 10  = 2
                    rev   = 1*10 + 2   = 12
                    n     = 122 / 10   = 12

      Iteration 3 : digit = 12 % 10   = 2
                    rev   = 12*10 + 2  = 122
                    n     = 12 / 10    = 1

      Iteration 4 : digit = 1 % 10    = 1
                    rev   = 122*10 + 1 = 1221
                    n     = 1 / 10     = 0     -> loop ends

      Output : Reversed: 1221
               It is a PALINDROME
   ```

   Step-by-step trace for input `3456`
   ```
      n = 3456 , rev = 0 , original = 3456

      Iteration 1 : digit = 6 , rev = 6    , n = 345
      Iteration 2 : digit = 5 , rev = 65   , n = 34
      Iteration 3 : digit = 4 , rev = 654  , n = 3
      Iteration 4 : digit = 3 , rev = 6543 , n = 0   -> loop ends

      Output : Reversed: 6543
               It is NOT a palindrome
   ```

   Summary table
   ```
      Input   Reversed   Palindrome?
      1221      1221        YES
      3456      6543        NO
   ```

   The three lines that do all the work
   ```
      digit = n % 10        extract the LAST digit
      rev   = rev*10 + digit  shift the result left and append the digit
      n     = n / 10        remove the last digit (integer division)

      The loop runs once per digit, so it is O(number of digits) = O(log n).
   ```

   - If the intended program was instead `digit sum` or `counting digits`, the same trace applies with `sum = sum + digit` or `count++` in place of the middle line:
   ```
      1221 -> digit sum 6 , 4 digits
      3456 -> digit sum 18 , 4 digits
   ```

8. **Write the function for which the output is 1 for that input.** *[BAPEX Assistant General Manager (ICT) 20.01.2023 compact it 463 (ET: BUET)]*

   Answer: The question is `incomplete` — the input for which the function must return 1 was printed with the previous question and is not present here. The answer below covers the functions that this question normally asks for, all of which return `1` (true) for a matching input and `0` otherwise.

   If the required test is `palindrome number` — which follows from the 1221 and 3456 inputs of the previous question
   ```c
   int isPalindrome(int n) {
       int rev = 0, original = n;

       while (n > 0) {
           rev = rev * 10 + (n % 10);
           n = n / 10;
       }
       return (rev == original) ? 1 : 0;
   }
   ```
   ```
      isPalindrome(1221)  ->  1        1221 reversed is 1221
      isPalindrome(3456)  ->  0        3456 reversed is 6543
   ```

   If the test is `prime number`
   ```c
   int isPrime(int n) {
       if (n <= 1) return 0;
       for (int i = 2; i * i <= n; i++)
           if (n % i == 0) return 0;
       return 1;
   }
   ```
   ```
      isPrime(17) -> 1 ,  isPrime(18) -> 0
      The loop stops at sqrt(n), so it is O(sqrt n).
   ```

   If the test is `even number`
   ```c
   int isEven(int n) {
       return (n % 2 == 0) ? 1 : 0;
   }
   ```

   If the test is `Armstrong number`
   ```c
   int isArmstrong(int n) {
       int sum = 0, temp = n, digits = 0, t = n;
       while (t > 0) { digits++; t /= 10; }
       t = n;
       while (t > 0) {
           int d = t % 10, p = 1;
           for (int i = 0; i < digits; i++) p *= d;
           sum += p;
           t /= 10;
       }
       return (sum == n) ? 1 : 0;
   }
   ```
   ```
      isArmstrong(153) -> 1     1^3 + 5^3 + 3^3 = 1 + 125 + 27 = 153
      isArmstrong(154) -> 0
   ```

   If the test is `string palindrome`
   ```c
   int isStringPalindrome(char s[]) {
       int i = 0, j = strlen(s) - 1;
       while (i < j) {
           if (s[i] != s[j]) return 0;
           i++; j--;
       }
       return 1;
   }
   ```
   ```
      isStringPalindrome("madam") -> 1
      isStringPalindrome("hello") -> 0
   ```

   - The pattern every such function follows: `return 1 when the property holds and 0 otherwise`, exiting early the moment a counter-example is found. C has no built-in boolean type in C89, so `int` with 0 and 1 is the convention; `<stdbool.h>` in C99 adds `bool`, `true` and `false`, which compile to the same values.

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

   Answer: The program reverses the digits of the input and checks whether the reversed value equals the original — that is, it tests for a palindrome number.

   Explanation of lines 7 to 11 (the while block)
   - Line 7 `while (n != 0)` — keep looping as long as digits remain in `n`.
   - Line 8 `remainder = n % 10` — take the last digit of `n`.
   - Line 9 `reversed = reversed * 10 + remainder` — shift the digits already collected one place to the left, then append the new digit at the units place.
   - Line 10 `n /= 10` — integer division removes the last digit, shrinking `n` by one digit per pass.
   - Line 11 closes the loop; the loop ends when `n` becomes 0.

   Trace for input `1221`

   | Pass | n | remainder | reversed |
   |---|---|---|---|
   | 1 | 1221 | 1 | 0×10 + 1 = 1 |
   | 2 | 122 | 2 | 1×10 + 2 = 12 |
   | 3 | 12 | 2 | 12×10 + 2 = 122 |
   | 4 | 1 | 1 | 122×10 + 1 = 1221 |
   | end | 0 | — | 1221 |

   - `original = 1221` and `reversed = 1221`, so the output is `1221 is a palindrome.`

   Trace for input `3456`
   - `reversed` becomes 6, 65, 654, then 6543.
   - `3456 != 6543`, so the `if` fails. The code as printed has no `else`, so nothing is printed at all.

   - The program also has no closing brace or `return 0;` in the excerpt, so it would not compile as shown.

10. **C programming output problem.** *[Teletalk Assistant Manager (IT) 2023 compact it 468 (ET: N/A)]*

    Answer: The question is `incomplete` — the paper printed a code snippet that was not captured, so the specific output cannot be produced. The traps that C output questions are built on are set out below with worked examples.

    1. Operator precedence and associativity
    ```c
       printf("%d", 2 + 3 * 4);         // 14 , not 20 - * binds tighter than +
       printf("%d", (2 + 3) * 4);       // 20
       printf("%d", 10 > 5 == 1);       // 1  - > binds tighter than ==
    ```

    2. Increment operators and their side effects
    ```c
       int i = 5, j;
       j = i++ + ++i;         // UNDEFINED BEHAVIOUR - i is modified twice
                              // between sequence points. Never write this.

       int a = 5;
       printf("%d %d", a++, a);   // the ORDER of evaluation of arguments is
                                  // not specified - also undefined
    ```

    3. Integer division and the modulus sign
    ```c
       printf("%d", 7/2);       // 3
       printf("%d", 7%2);       // 1
       printf("%d", -7/2);      // -3  (truncated towards zero)
       printf("%d", -7%2);      // -1  (sign follows the left operand)
       printf("%f", 7/2);       // GARBAGE - %f with an int argument
    ```

    4. Pointer arithmetic
    ```c
       int a[5] = {10,20,30,40,50};
       int *p = a;

       printf("%d", *p);        // 10
       printf("%d", *(p+2));    // 30
       printf("%d", *p++);      // 10 , then p moves on
       printf("%d", ++*p);      // 11 - increments the VALUE, not the pointer
       printf("%d", p[3]);      // 40 - identical to *(p+3)
    ```

    5. Character and ASCII
    ```c
       char c = 'A';
       printf("%c %d", c, c);       // A 65
       printf("%c", c + 1);         // B
       printf("%d", 'z' - 'a');     // 25
    ```

    6. Strings and the terminating null
    ```c
       char s[] = "hello";
       printf("%lu %d", sizeof(s), (int)strlen(s));   // 6 5
       printf("%s", s + 2);                            // llo
       printf("%c", s[strlen(s)]);                     // '\0' - prints nothing
    ```

    7. Loops with tricky conditions
    ```c
       for (i = 0; i < 5; i++);         // semicolon ends the loop body
           printf("%d", i);             // prints 5, once

       i = 0;
       while (i++ < 3) printf("%d", i); // 123
       // i is compared, THEN incremented
    ```

    8. switch fall-through
    ```c
       switch (2) {
           case 1: printf("A");
           case 2: printf("B");     // no break
           case 3: printf("C");
       }
       // Output : BC
    ```

    9. Static variables
    ```c
       void f() { static int c = 0; printf("%d", ++c); }
       f(); f(); f();               // 123
    ```

    10. Pass by value versus pass by reference
    ```c
       void swap(int a, int b)   { int t=a; a=b; b=t; }      // does NOTHING
       void swap(int *a, int *b) { int t=*a; *a=*b; *b=t; }  // works
    ```

    - The method for any output question: work through the code `line by line, keeping a table of every variable`, and apply C's rules exactly — precedence, integer truncation, implicit conversion, and the match between the format specifier and the argument type. Most such questions are one of the ten traps above.

11. **What is the output of code snippet?** *[BICIC Assistant Programmer 2022 compact it 631 (ET: BUET)]*

    Answer: The question is `incomplete` — the code snippet it refers to was not captured. The commonest snippets used in such questions are traced below, so the method is available whichever one was intended.

    Snippet type 1 — pointer and array
    ```c
       int a[5] = {1, 2, 3, 4, 5};
       int *p = a;
       printf("%d %d %d", *p, *(p+2), p[4]);
    ```
    ```
       Output : 1 3 5

       *p       = a[0] = 1
       *(p+2)   = a[2] = 3          pointer arithmetic scales by sizeof(int)
       p[4]     = *(p+4) = a[4] = 5
    ```

    Snippet type 2 — increment operators
    ```c
       int i = 5;
       printf("%d ", i++);      // 5 , then i = 6
       printf("%d ", ++i);      // i = 7 , prints 7
       printf("%d ", i--);      // 7 , then i = 6
       printf("%d", --i);       // i = 5 , prints 5
    ```
    ```
       Output : 5 7 7 5
    ```

    Snippet type 3 — string handling
    ```c
       char s[] = "Bangladesh";
       printf("%lu ", sizeof(s));     // 11 - ten characters plus '\0'
       printf("%lu ", strlen(s));     // 10
       printf("%s ", s + 5);          // adesh
       printf("%c", s[2]);            // n
    ```
    ```
       Output : 11 10 adesh n
    ```

    Snippet type 4 — switch fall-through
    ```c
       int x = 2;
       switch (x) {
           case 1: printf("One");
           case 2: printf("Two");
           case 3: printf("Three");
                   break;
           default: printf("Other");
       }
    ```
    ```
       Output : TwoThree

       Without a break, execution FALLS THROUGH into the following cases
       until a break or the end of the switch is reached.
    ```

    Snippet type 5 — static variable
    ```c
       void count() {
           static int c = 0;
           int d = 0;
           c++; d++;
           printf("%d %d | ", c, d);
       }
       int main() { count(); count(); count(); }
    ```
    ```
       Output : 1 1 | 2 1 | 3 1 |

       'static' is initialised ONCE and keeps its value between calls;
       the ordinary local d is created and destroyed every call.
    ```

    Snippet type 6 — integer division and type
    ```c
       printf("%d ", 5/2);         // 2
       printf("%.2f ", 5/2.0);     // 2.50
       printf("%d ", (int)2.9);    // 2   - truncates, does not round
       printf("%d", 'A' + 1);      // 66
    ```
    ```
       Output : 2 2.50 2 66
    ```

    Snippet type 7 — the semicolon trap
    ```c
       int i;
       for (i = 0; i < 5; i++);
           printf("%d", i);
    ```
    ```
       Output : 5

       The semicolon after the for statement makes the loop body EMPTY.
       The printf is not part of the loop and runs once, after i has
       reached 5.
    ```

    - The method for any snippet: `keep a table of every variable and update it line by line`, watching for integer truncation, the difference between prefix and postfix increment, missing `break` statements, and whether the `printf` format specifier matches the argument's actual type.

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

    Answer: Output is

    ```
    x is greater than y
    ```

    Step-by-step
    - `x, y = 8, 4` is tuple unpacking, so `x = 8` and `y = 4`.
    - The condition `x < y` tests `8 < 4`, which is False.
    - Control moves to the `else` branch, so `st = "x is greater than y"`.
    - `print(st)` writes that string.
    - `if __name__ == "__main__":` is true when the file is run directly, so `main()` is called.

    - The `__name__` guard exists so that the code does not run automatically when this file is imported as a module by another program.

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

    (A) Output is `Devel`, with `len = 5`.
    - Placing `'\0'` at index 5 makes it the new end of the string, so `printf("%s")` and `strlen()` both stop there.

    (B) Output is
    ```
    0
    1
    2
    3
    4
    6
    7
    8
    ```
    - `continue` skips the rest of the loop body for that iteration and jumps straight to `i++`.
    - So when `i` equals 5 the `printf` is skipped, but the loop itself keeps running.
    - This differs from `break`, which would have ended the loop entirely and printed only 0 to 4.

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

    Answer: On a typical GCC compiler the output is `36 63`.

    Step-by-step (as GCC evaluates it)
    - Start: `a = 10`, `b = 25`.
    - `a = b++ + a++` → uses the old values `25 + 10 = 35`, and both are incremented as side effects. After the assignment `a = 35` and `b = 26`. Note the `a++` side effect is overwritten by the assignment to `a`.
    - `b = ++b + ++a` → `++b` makes `b = 27` and yields 27; `++a` makes `a = 36` and yields 36. So `b = 27 + 36 = 63`.
    - Output: `36 63`.

    Important caveat
    - The statement `a = b++ + a++` modifies `a` twice between two sequence points — once by `a++` and once by the assignment. In C this is undefined behaviour, so a different compiler may legitimately print a different result.
    - Exam papers expect the GCC answer, but the correct engineering comment is that such code should never be written.

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

    Answer: Output is `3 5 7`.

    Step-by-step
    - `a++` is post-increment, so it yields the current value `2` for the expression and only afterwards makes `a` become `3`.
    - `c = 2 + 5 = 7`.
    - `b` is never modified, so it stays `5`.
    - Final values: `a = 3`, `b = 5`, `c = 7`.

    - Contrast with pre-increment: had the code been `c = ++a + b`, then `a` would become 3 first and `c` would be `8`.
    - Unlike question 14, this statement is well defined, because `a` is modified only once.

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

    Answer: Output is `3, 2, 15`.

    Step-by-step
    - Initial array: `a = {5, 1, 15, 20, 25}`.
    - `i = ++a[1]` — pre-increment makes `a[1]` become `2`, and that new value is assigned, so `i = 2`. Array is now `{5, 2, 15, 20, 25}`.
    - `j = a[1]++` — post-increment yields the current value `2`, so `j = 2`, and afterwards `a[1]` becomes `3`. Array is `{5, 3, 15, 20, 25}`.
    - `m = a[i++]` — post-increment yields `i = 2` for the subscript, so `m = a[2] = 15`, and afterwards `i` becomes `3`.
    - Final: `i = 3`, `j = 2`, `m = 15`.

    - Note also that `void main()` is non-standard; the correct signature is `int main(void)`.

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

    Answer: On GCC the output is `2 2 2`, but the code is undefined behaviour and the answer is compiler dependent.

    Why the result is not reliable
    - The C standard does not fix the order in which function arguments are evaluated. A compiler may evaluate them left to right, right to left, or in any order.
    - Worse, `a` is modified twice (by `++a` and `a++`) within one expression with no sequence point in between. The standard explicitly calls this undefined behaviour.
    - GCC typically evaluates the arguments right to left: `a++` yields 1 and makes `a = 2`; then `a` reads as 2; then `++a` makes `a = 3` and yields... yet the printed values come out as `2 2 2` on common builds.

    The correct answer in an exam
    - State that the output is undefined behaviour, mention that GCC prints `2 2 2`, and note that the expression should be split into separate statements to be well defined.
    - The declared function `isLeapYear` is never defined or called, which is harmless but pointless here.

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

    Answer: Output is `16`.

    Recursion trace
    - `fun(2)` → `n != 4`, so it returns `2 * fun(3)`
    - `fun(3)` → `n != 4`, so it returns `2 * fun(4)`
    - `fun(4)` → base case reached, returns `4`

    Unwinding the calls
    - `fun(4) = 4`
    - `fun(3) = 2 × 4 = 8`
    - `fun(2) = 2 × 8 = 16`

    - The recursion depth is 3, and the base case `n == 4` is what stops it. If `fun(5)` were called instead, `n` would never equal 4 and the recursion would run until the stack overflowed.

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

    Answer: Output is `30`.

    Step 1 - compute y
    - `y = 6 + 3*3/5`. Multiplication and division bind tighter than addition, and both are left-associative.
    - `3*3 = 9`, then `9/5 = 1` by integer division.
    - `y = 6 + 1 = 7`.

    Step 2 - understand what x*x expands to
    - `#define` is a plain textual macro with no parentheses, so `x*x` expands literally to:
    - `9+2/4*3-2*4+(5-4)*3 * 9+2/4*3-2*4+(5-4)*3`
    - This is NOT the square of the macro's value. Only the last term of the first copy and the first term of the second copy get multiplied together.

    Step 3 - evaluate the expanded expression
    - `2/4 = 0` (integer division), so `2/4*3 = 0`.
    - First part: `9 + 0 − 8 + (1)*3*9` — here `(5-4)*3 * 9 = 1×3×9 = 27`.
    - Running total: `9 + 0 − 8 + 27 = 28`.
    - Second part: `+ 0 − 8 + 3` → `28 + 0 − 8 + 3 = 23`.
    - So `x*x = 23`.

    Step 4 - final answer
    - `i = 23 + 7 = 30`.

    - Moral of the question: always wrap a macro body in parentheses — `#define x (9+2/4*3-2*4+(5-4)*3)` — otherwise textual substitution produces surprises like this one.

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

    Errors found

    | Line | Error | Correction |
    |---|---|---|
    | 1 | Missing `#` before `include` | `#include<stdio.h>` |
    | 2 | Missing `()` after `main` | `int main()` |
    | 3 | Missing semicolon | `int i, sum = 0;` |
    | 4 | Commas used instead of semicolons in the `for` header; stray `{` after `;` | `for(i=1; i<=10; i++) {` |
    | 5 | Missing semicolon | `sum = sum + i;` |
    | 7 | Format string not quoted, `%` missing before `d`, no semicolon | `printf("Sum of number = %d", sum);` |
    | 8 | Missing semicolon | `return 0;` |

    Corrected program
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

    Output
    ```
    Sum of number = 55
    ```
    - The loop adds 1 through 10, and `10 × 11 / 2 = 55`.

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

    Answer: Output is `146`.

    The function returns the sum of `x[0]` through `x[i]`, and prints each partial sum on the way back up the recursion.

    Call trace with `y = {1, 3, 2, 8}` and `i = 2`
    - `function(y, 2)` → `s = y[2] = 2`, and since `i > 0` it calls `function(y, 1)` first.
    - `function(y, 1)` → `s = y[1] = 3`, calls `function(y, 0)`.
    - `function(y, 0)` → `s = y[0] = 1`, `i` is not greater than 0, so it prints `1` and returns 1.
    - Back in `function(y, 1)`: `s = 3 + 1 = 4`, prints `4`, returns 4.
    - Back in `function(y, 2)`: `s = 2 + 4 = 6`, prints `6`, returns 6.

    - The prints happen while unwinding, so the order is `1`, then `4`, then `6` — giving `146` with no separators.
    - `y[3] = 8` is never touched, because the call started at index 2.

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

    ```
    Bangladesh
     nutiladTc
    ```

    First loop
    - Prints `s[0]` to `s[9]`, which is `Bangladesh`.
    - `++s1` runs 10 times, so afterwards `s1` points to `s + 10`, the space after "Bangladesh".

    Second loop — the tricky part
    - Both `i` and `s1` advance on every pass, so the effective index into the original string increases by 2 each time.
    - Pass `i`: it prints `s1[i]`, where `s1` currently equals `s + 10 + i`. So the character printed is `s[10 + 2i]`.

    | i | index into s | character |
    |---|---|---|
    | 0 | 10 | (space) |
    | 1 | 12 | n |
    | 2 | 14 | u |
    | 3 | 16 | t |
    | 4 | 18 | i |
    | 5 | 20 | l |
    | 6 | 22 | a |
    | 7 | 24 | d |
    | 8 | 26 | T |
    | 9 | 28 | c |

    - Result: `" nutiladTc"` — every second character, skipping one each time.

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

    Answer: The program computes `n` raised to the power `r`, that is `nʳ`.

    How it works
    - `sum` starts at 1, which is the correct value for `r = 0`.
    - The loop multiplies `sum` by `n` exactly `r` times, so `sum` ends up as `n × n × ... × n` (`r` factors).

    Sample outputs

    | Input (n r) | Calculation | Output |
    |---|---|---|
    | 2 3 | 2 × 2 × 2 | 8 |
    | 5 2 | 5 × 5 | 25 |
    | 3 4 | 3 × 3 × 3 × 3 | 81 |
    | 7 0 | loop never runs | 1 |

    - Time complexity `O(r)`. Fast exponentiation by squaring would reduce it to `O(log r)`.
    - Limitation: `int` overflows quickly — `2³¹` already exceeds the range, so `long long` would be safer.

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

    Answer: The function returns the XOR of the first `arrSize` elements. With only 0s and 1s in the array, that equals 1 when the count of 1s is odd and 0 when it is even — this is the parity bit.

    | Call | Elements XORed | Count of 1s | Output |
    |---|---|---|---|
    | f(arr, 2) | 0 ^ 1 | 1 (odd) | 1 |
    | f(arr, 3) | 0 ^ 1 ^ 1 | 2 (even) | 0 |
    | f(arr, 5) | 0 ^ 1 ^ 1 ^ 0 ^ 1 | 3 (odd) | 1 |
    | f(arr, 8) | 0 ^ 1 ^ 1 ^ 0 ^ 1 ^ 1 ^ 0 ^ 1 | 5 (odd) | 1 |

    - XOR properties used: `x ^ 0 = x` and `x ^ x = 0`, so pairs of equal bits cancel out.
    - `*(arr + i)` is pointer arithmetic and is exactly equivalent to `arr[i]`.
    - Time complexity `O(n)`, space `O(1)`.

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

    ```
    5
    8
    9
    11
    5
    ```

    Why `y` accumulates across calls
    - `y` is declared `static`, so it is created once and keeps its value between calls. Every call adds its own `x` to the same shared `y`.

    Call trace
    - `recursion(5)` → `y = 0 + 5 = 5`, prints `5`, then calls `recursion(3)` and `recursion(2)`.
    - `recursion(3)` → `y = 5 + 3 = 8`, prints `8`, calls `recursion(1)` and `recursion(0)`.
    - `recursion(1)` → `y = 8 + 1 = 9`, prints `9`, calls `recursion(-1)` and `recursion(-2)`, both of which return 1 immediately. So it returns `2`.
    - `recursion(0)` → `x <= 0`, returns `1` with no printing.
    - So `recursion(3) = 2 + 1 = 3`.
    - `recursion(2)` → `y = 9 + 2 = 11`, prints `11`, calls `recursion(0)` and `recursion(-1)`, both returning 1. So it returns `2`.
    - Final: `recursion(5) = 3 + 2 = 5`, printed last.

    - Key learning point: a `static` local variable is not reset on each call, which is what produces the running total 5, 8, 9, 11.

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

    ```
    i=-1, p=1, sum=0
    i=1, p=1, sum=2
    i=3, p=9, sum=14
    i=5, p=25, sum=44

     Outsite Loop, i=7, p=49, sum=44
    ```

    Trace

    | i | p = i×i | i > 5 ? | sum = sum + (i + p) | Printed? |
    |---|---|---|---|---|
    | −1 | 1 | No | 0 + (−1 + 1) = 0 | Yes |
    | 1 | 1 | No | 0 + (1 + 1) = 2 | Yes |
    | 3 | 9 | No | 2 + (3 + 9) = 14 | Yes |
    | 5 | 25 | No | 14 + (5 + 25) = 44 | Yes |
    | 7 | 49 | Yes → break | not updated | No |

    - The critical detail is that `p = i*i` executes before the `break` check, so `p` becomes 49 even though the loop exits on that pass.
    - `sum` stays at 44 because `break` fires before the sum line.
    - After `break`, `i` retains the value 7 outside the loop.

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

    Answer: Output is `11 22 34 39`.

    What the function does
    - `func` is bubble sort in ascending order — it repeatedly compares adjacent pairs and swaps them when they are out of order.
    - `n = sizeof(arr)/sizeof(arr[0]) = 16/4 = 4`.

    Pass-by-pass trace starting from `{39, 22, 11, 34}`
    - Pass 1: (39,22) swap → `22,39,11,34`; (39,11) swap → `22,11,39,34`; (39,34) swap → `22,11,34,39`
    - Pass 2: (22,11) swap → `11,22,34,39`; (22,34) no swap
    - Pass 3: (11,22) no swap
    - Final array: `11 22 34 39`

    - The array is modified in place, because in C an array parameter decays to a pointer and the function works on the caller's memory directly.
    - Time complexity `O(n²)`.

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

    ```
    i=0 x=3 sum=3
    i=4 x=7 sum=14
    i=6 x=9 sum=29
    Out site loop:
     i=8 x=11 sum=29
    ```

    Trace

    | i | x = i+3 | i == 2 ? | i >= 8 ? | sum | Printed? |
    |---|---|---|---|---|---|
    | 0 | 3 | No | No | 0 + 3 = 3 | Yes |
    | 2 | 5 | Yes → continue | — | unchanged | No |
    | 4 | 7 | No | No | 3 + 11 = 14 | Yes |
    | 6 | 9 | No | No | 14 + 15 = 29 | Yes |
    | 8 | 11 | No | Yes → break | unchanged | No |

    - Two important details: `x = i + 3` runs before both checks, so `x` becomes 11 on the final pass even though `break` fires.
    - `continue` at `i = 2` skips the printing but the loop keeps running; `break` at `i = 8` ends it entirely.
    - After the loop `i` remains 8, `x` remains 11, and `sum` stays at 29.

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

    Answer: Output is `i=5, count=10j=5, x=30`.

    Step-by-step trace

    | Iteration | i | count | x = x + i + count | i after ++ | count after |
    |---|---|---|---|---|---|
    | 1 | 0 | 0 | 0 + 0 + 0 = 0 | 1 | 2 |
    | 2 | 1 | 2 | 0 + 1 + 2 = 3 | 2 | 4 |
    | 3 | 2 | 4 | 3 + 2 + 4 = 9 | 3 | 6 |
    | 4 | 3 | 6 | 9 + 3 + 6 = 18 | 4 | 8 |
    | 5 | 4 | 8 | 18 + 4 + 8 = 30 | 5 | 10 |

    - The loop ends when `i` reaches 5, because `j > i` becomes `5 > 5`, which is false.
    - The `if (i == 7) break;` never fires, since the loop already stops at `i = 5`.
    - Final values: `i = 5`, `count = 10`, `x = 30`, and `j` is still 5.

    - Note a bug in the code: the second `printf` prints `i` where it says `j=%d`. That is why the output shows `j=5` — which coincidentally matches the real `j`, since `i` also ended at 5.
    - Also, neither `printf` has a newline, so the two lines run together as one.

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

    Answer: Output is `ello` followed by one invisible null character.

    Step-by-step
    - `"Hello\0 World!!"` contains an explicit `\0` after "Hello". The array still holds all 14 characters plus the final terminator, but `strlen` stops at the first `\0`.
    - So `length = 5`.
    - `s` starts pointing at `string[0]`.
    - `*++s` is pre-increment, so `s` moves first and then the character is read. That means the loop never prints `string[0]`.

    | i | s points to | Character printed |
    |---|---|---|
    | 0 | string[1] | e |
    | 1 | string[2] | l |
    | 2 | string[3] | l |
    | 3 | string[4] | o |
    | 4 | string[5] | `\0` (nothing visible) |

    - Visible output: `ello`.
    - Two traps in one question — the embedded `\0` shortening `strlen`, and `*++s` skipping the first character.
    - The program also omits `<stdio.h>` while calling `printf`, which a strict compiler would flag.

31. **After compilation and execution, what will be output in the following code:** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 972 (ET: BUET)]*

    Answer: The question is `incomplete` — the code that was to be compiled and executed is not present. The classes of behaviour that "after compilation and execution" questions test are set out below with worked examples.

    Case 1 — the program does not compile
    ```c
       int main() {
           int x = 10;
           x = "hello";        // ERROR: assigning char* to int
           return 0;
       }
    ```
    ```
       Output : COMPILATION ERROR. No output is produced at all.

       Common compile errors : missing semicolon , undeclared variable ,
       type mismatch , missing header , wrong number of arguments.
    ```

    Case 2 — it compiles but the behaviour is undefined
    ```c
       int main() {
           int a[5];
           printf("%d", a[10]);      // out of bounds
           int *p;
           printf("%d", *p);         // uninitialised pointer
           return 0;
       }
    ```
    ```
       Output : UNDEFINED. It may print garbage, or crash with a
       segmentation fault, or appear to work. The standard imposes no
       requirement, so "undefined behaviour" is the correct answer.
    ```

    Case 3 — it compiles with a warning and prints something surprising
    ```c
       int main() {
           float f = 3.14;
           printf("%d", f);          // WRONG specifier for a float
           return 0;
       }
    ```
    ```
       Output : garbage. %d reads four bytes as an int, but a float is
       passed as a double and laid out differently.
    ```

    Case 4 — it works, and the trick is in the logic
    ```c
       int main() {
           int i = 0;
           while (i++ < 3)
               printf("%d ", i);
           return 0;
       }
    ```
    ```
       Output : 1 2 3

       i++ < 3 : the CURRENT value is compared, then i is incremented.
       i = 0 -> 0<3 true , i becomes 1 , print 1
       i = 1 -> 1<3 true , i becomes 2 , print 2
       i = 2 -> 2<3 true , i becomes 3 , print 3
       i = 3 -> 3<3 false , loop ends
    ```

    Case 5 — a runtime error
    ```c
       int main() {
           int a = 10, b = 0;
           printf("%d", a / b);      // division by zero
           return 0;
       }
    ```
    ```
       Output : the program compiles, then crashes.
       On Linux : "Floating point exception (core dumped)"
    ```

    The stages a C program passes through
    ```
       source.c
          |  PREPROCESSOR   - expands #include and #define
          v
       source.i
          |  COMPILER       - checks syntax and types, produces assembly
          v
       source.s
          |  ASSEMBLER      - produces machine code
          v
       source.o
          |  LINKER         - joins the object files and libraries
          v
       a.out                - the executable
    ```
    ```
       A syntax or type fault is caught by the COMPILER  -> no executable
       A missing function body is caught by the LINKER   -> no executable
       A bad pointer is caught at RUN TIME, or not at all
    ```

    - The habit that answers such questions correctly: first ask `does it compile`, then `is any behaviour undefined`, and only then trace the logic. Many exam snippets are designed so that the answer is "compilation error" rather than a value.

32. **Write down the output of following program:** *[NACTAR Assistant Instructor (ICT) 2020 compact it 991 (ET: N/A)]*

    Answer: The question is `incomplete` — the program whose output was to be written is not present. The programs that appear most often in this position are traced below.

    Program type 1 — nested loop pattern
    ```c
    #include <stdio.h>
    int main() {
        int i, j;
        for (i = 1; i <= 4; i++) {
            for (j = 1; j <= i; j++)
                printf("%d ", j);
            printf("\n");
        }
        return 0;
    }
    ```
    ```
       Output :
       1
       1 2
       1 2 3
       1 2 3 4
    ```

    Program type 2 — recursion
    ```c
    #include <stdio.h>
    int fact(int n) {
        if (n <= 1) return 1;
        return n * fact(n - 1);
    }
    int main() {
        printf("%d", fact(5));
        return 0;
    }
    ```
    ```
       Output : 120

       fact(5) = 5 * fact(4)
               = 5 * 4 * fact(3)
               = 5 * 4 * 3 * fact(2)
               = 5 * 4 * 3 * 2 * fact(1)
               = 5 * 4 * 3 * 2 * 1 = 120
    ```

    Program type 3 — array and pointer
    ```c
    #include <stdio.h>
    int main() {
        int a[] = {10, 20, 30, 40, 50};
        int *p = a;
        printf("%d %d %d %d", *p, *(p+1), *(p+4), p[2]);
        return 0;
    }
    ```
    ```
       Output : 10 20 50 30
    ```

    Program type 4 — string reversal
    ```c
    #include <stdio.h>
    #include <string.h>
    int main() {
        char s[] = "BANGLADESH";
        int i, n = strlen(s);
        for (i = n - 1; i >= 0; i--)
            printf("%c", s[i]);
        return 0;
    }
    ```
    ```
       Output : HSEDALGNAB
    ```

    Program type 5 — swap by pointer, versus swap by value
    ```c
    #include <stdio.h>
    void swapVal(int a, int b)   { int t = a; a = b; b = t; }
    void swapRef(int *a, int *b) { int t = *a; *a = *b; *b = t; }

    int main() {
        int x = 10, y = 20;
        swapVal(x, y);
        printf("%d %d | ", x, y);      // 10 20 - UNCHANGED
        swapRef(&x, &y);
        printf("%d %d", x, y);         // 20 10 - swapped
        return 0;
    }
    ```
    ```
       Output : 10 20 | 20 10

       C passes arguments BY VALUE. swapVal receives copies and changes
       only those copies. Only passing the ADDRESS lets a function alter
       the caller's variables.
    ```

    Program type 6 — Fibonacci
    ```c
    #include <stdio.h>
    int main() {
        int a = 0, b = 1, c, i;
        printf("%d %d ", a, b);
        for (i = 3; i <= 8; i++) {
            c = a + b;
            printf("%d ", c);
            a = b; b = c;
        }
        return 0;
    }
    ```
    ```
       Output : 0 1 1 2 3 5 8 13
    ```

    - The method for any such question: `keep a running table of every variable`, update it line by line, and write down exactly what each `printf` emits, including whether it ends with a newline. Most marks are lost by forgetting integer truncation or by mis-tracing a prefix versus postfix increment.

33. **What will be the output in C and java code? (i) C program:** *[Combined 4 Banks Assistant Programmer 2020 compact it 1003 (ET: DU)]*

    Answer: The question is `incomplete` — the C program and the Java program it refers to were not captured. The comparison the question is built on is set out below, with the snippets that appear most often in this position.

    Case 1 — integer division
    ```c
       /* C */
       printf("%d", 5/2);          // 2
       printf("%f", 5/2.0);        // 2.500000
    ```
    ```java
       // Java
       System.out.println(5/2);    // 2
       System.out.println(5/2.0);  // 2.5
    ```
    - Both truncate integer division. Java prints `2.5`, C prints `2.500000`, because `%f` defaults to six decimal places.

    Case 2 — array size
    ```c
       /* C */
       int a[5] = {1,2,3,4,5};
       printf("%lu", sizeof(a)/sizeof(a[0]));   // 5
    ```
    ```java
       // Java
       int[] a = {1,2,3,4,5};
       System.out.println(a.length);            // 5
    ```
    - C has no length field, so the size must be computed. Java stores the length with the array, and checks every index at run time.

    Case 3 — out-of-bounds access
    ```c
       /* C */
       int a[5];
       printf("%d", a[10]);        // UNDEFINED - garbage or a crash
    ```
    ```java
       // Java
       int[] a = new int[5];
       System.out.println(a[10]);  // ArrayIndexOutOfBoundsException
    ```
    - This is the sharpest difference: C does not check, Java always does.

    Case 4 — string comparison
    ```c
       /* C */
       char s1[] = "test", s2[] = "test";
       printf("%d", s1 == s2);          // 0 - two different addresses
       printf("%d", strcmp(s1,s2));     // 0 - contents are equal
    ```
    ```java
       // Java
       String s1 = "test", s2 = "test";
       System.out.println(s1 == s2);        // true  - both from the string pool
       String s3 = new String("test");
       System.out.println(s1 == s3);        // false - a new heap object
       System.out.println(s1.equals(s3));   // true
    ```

    Case 5 — uninitialised variables
    ```c
       /* C */
       int x;
       printf("%d", x);            // GARBAGE - undefined
    ```
    ```java
       // Java
       int x;
       System.out.println(x);      // COMPILE ERROR: variable x might not
                                   // have been initialized
    ```
    - A `field` in Java is zero-initialised; a `local variable` must be assigned before use, and the compiler enforces it.

    Case 6 — integer overflow
    ```c
       /* C */
       int x = 2147483647;
       printf("%d", x + 1);        // -2147483648 (implementation defined
                                   // for signed overflow - undefined by the standard)
    ```
    ```java
       // Java
       int x = 2147483647;
       System.out.println(x + 1);  // -2147483648 - DEFINED to wrap around
    ```

    Summary of the differences these questions test

    | Point | C | Java |
    |---|---|---|
    | Array bounds checked | `No` | `Yes` — throws an exception |
    | Pointers | Yes | No — references only |
    | Memory management | Manual `malloc` / `free` | Garbage collector |
    | Uninitialised local | Garbage value | Compile error |
    | String comparison | `strcmp` | `.equals()`, not `==` |
    | Integer overflow | Undefined for signed | Defined to wrap |
    | `sizeof` | Yes | No — use `.length` |
    | Output | `printf` with format specifiers | `System.out.println` |
    | Platform | Compiled to machine code | Compiled to bytecode, runs on the JVM |

    - The general rule that answers most of these: `C trusts the programmer and checks nothing at run time; Java checks everything and throws an exception instead of corrupting memory`. Where a C snippet prints garbage or crashes, the Java equivalent usually refuses to compile or throws.

34. **a) Using Pseudocode give an example of run time error.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1035-1036 (ET: BUET)]*

    Answer: A run-time error is an error that the compiler cannot detect. The program compiles successfully but fails or crashes while it is running.

    Example 1 — division by zero
    ```
    BEGIN
        READ a
        READ b
        result = a / b        // crashes when b = 0
        PRINT result
    END
    ```
    - The syntax is perfectly valid, so compilation succeeds. But if the user enters `b = 0`, the program crashes with a divide-by-zero error at run time.

    Example 2 — array index out of bounds
    ```
    BEGIN
        DECLARE arr[5]
        FOR i = 0 TO 5 DO      // should be 0 TO 4
            arr[i] = i
        END FOR
    END
    ```
    - Writing to `arr[5]` touches memory outside the array and causes a segmentation fault or silent corruption.

    Example 3 — null pointer dereference
    ```
    BEGIN
        SET ptr = NULL
        PRINT value at ptr     // crashes here
    END
    ```

    Types of errors compared

    | Error type | When detected | Example |
    |---|---|---|
    | Syntax error | Compile time | Missing semicolon |
    | Semantic error | Compile time | Assigning a string to an int |
    | Run-time error | While running | Division by zero, array overflow |
    | Logical error | Never — the result is just wrong | Using `+` instead of `-` |

    - Run-time errors are handled with input validation, bounds checking, and exception handling (`try...catch` in languages that support it).

35. **Find the Output:** *[Sundharban Gas Assistant Programmer 2020 compact it 1047 (ET: N/A)]*

    Answer: The question is `incomplete` — the code whose output was to be found is not present. The snippets that appear most often in this position are traced below.

    Snippet 1 — prefix and postfix in one expression
    ```c
       int i = 10;
       printf("%d %d %d", i++, ++i, i);
    ```
    ```
       Output : UNDEFINED BEHAVIOUR.

       'i' is modified more than once between sequence points, and the
       order in which printf's arguments are evaluated is unspecified.
       Different compilers print different results. The correct exam
       answer is "undefined", not a number.
    ```

    Snippet 2 — the comma operator
    ```c
       int x = (1, 2, 3);
       printf("%d", x);            // 3 - the comma operator yields the LAST value

       int a = 5, b;
       b = (a++, a+10);
       printf("%d %d", a, b);      // 6 16
    ```

    Snippet 3 — pointer to a string literal
    ```c
       char *s = "hello";
       printf("%c ", *s);          // h
       printf("%c ", *(s+4));      // o
       printf("%s ", s+2);         // llo
       printf("%lu", strlen(s));   // 5
    ```
    ```
       Output : h o llo 5
    ```

    Snippet 4 — the dangling else
    ```c
       int a = 5, b = 10;
       if (a > 3)
           if (b > 20)
               printf("A");
       else
           printf("B");
    ```
    ```
       Output : nothing.

       The 'else' binds to the NEAREST unmatched 'if', which is the inner
       one, not the outer one as the indentation suggests. Since a > 3 is
       true and b > 20 is false, control reaches the else - but the else
       belongs to the inner if, so "B" is printed.

       Corrected reading : the output is B.
       The lesson : indentation means nothing to the compiler. Use braces.
    ```

    Snippet 5 — the size of things
    ```c
       printf("%lu ", sizeof(int));        // 4
       printf("%lu ", sizeof(char));       // 1 , always
       printf("%lu ", sizeof(double));     // 8
       printf("%lu ", sizeof("abc"));      // 4 - three characters plus '\0'
       printf("%lu", sizeof('a'));         // 4 in C - a character constant
                                           //   has type int
    ```
    ```
       Output : 4 1 8 4 4
    ```

    Snippet 6 — a do-while loop
    ```c
       int i = 10;
       do {
           printf("%d ", i);
           i++;
       } while (i < 5);
    ```
    ```
       Output : 10

       A do-while ALWAYS executes its body at least once, because the
       condition is tested at the END. This is the whole point of the
       construct, and the usual trick in such questions.
    ```

    Snippet 7 — bitwise operators
    ```c
       int a = 12, b = 10;              // 1100 and 1010 in binary
       printf("%d ", a & b);            // 8   -> 1000
       printf("%d ", a | b);            // 14  -> 1110
       printf("%d ", a ^ b);            // 6   -> 0110
       printf("%d ", a << 1);           // 24  - shift left = multiply by 2
       printf("%d", a >> 1);            // 6   - shift right = divide by 2
    ```
    ```
       Output : 8 14 6 24 6
    ```

    - The method for any "find the output" question: `keep a table of every variable and update it after each statement`, and before writing the answer ask three checks — is any behaviour undefined, does any integer division truncate, and does every format specifier match its argument's type.

36. **Find the error of given code** *[Combined 5 Banks Assistant Maintenance Engineer 2019 compact it 1055 (ET: AUST)]*
```c
Unsigned inti
For(i=100; i<=0; --i)
    Printf("%d",i);
```

    Answer: The code has both syntax errors and a logic error.

    Syntax errors
    - `Unsigned` should be lowercase `unsigned` — C keywords are case sensitive.
    - `inti` is missing a space; it should be `int i`.
    - The declaration has no terminating semicolon.
    - `For` should be lowercase `for`.
    - `Printf` should be lowercase `printf`.

    Logic error
    - The condition is `i <= 0` while `i` starts at 100, so the condition is false immediately and the loop body never runs. It should be `i >= 0` or `i > 0`.

    A second, subtler trap
    - If the condition were corrected to `i >= 0` with an `unsigned int`, the loop would become infinite. An unsigned value can never be negative, so after `i = 0` the decrement wraps around to a huge positive number and `i >= 0` stays true forever.
    - Either use a signed `int` with `i >= 0`, or keep `unsigned` and write `i > 0`.

    Corrected version
    ```c
    #include <stdio.h>
    int main(void) {
        unsigned int i;
        for (i = 100; i > 0; --i)
            printf("%d ", i);
        return 0;
    }
    ```
    - This prints 100 down to 1.

37. **What is the output of following code?** *[Bangladesh Competition Commission Programmer 2019 compact it 1062 (ET: DU)]*
```c
#include<stdio.h>
void main () {
    char *f [] = {"Ronaldo", "Messi", "Zidan", "Maradona"}, str[20];
    printf("%s\n", f[1]+2);
    printf("%s", f[2]+1);
}
```

    Answer: Output is

    ```
    ssi
    idan
    ```

    Explanation
    - `f` is an array of four pointers, each pointing to the first character of a string literal.
    - `f[1]` points to `"Messi"`. Adding 2 moves the pointer forward by two characters, so it now points at the first `'s'`. `printf("%s")` prints from there to the terminator, giving `ssi`.
    - `f[2]` points to `"Zidan"`. Adding 1 skips the `'Z'`, so printing from there gives `idan`.

    | Expression | Points to | Printed |
    |---|---|---|
    | f[1] | M-e-s-s-i | Messi |
    | f[1]+2 | s-s-i | ssi |
    | f[2] | Z-i-d-a-n | Zidan |
    | f[2]+1 | i-d-a-n | idan |

    - The variable `str[20]` is declared but never used.
    - `void main()` is non-standard; `int main(void)` is correct.

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

    Answer: The program is broken. It does not produce a meaningful output and, as written, runs until it crashes.

    Errors in the code
    - `if (s == "\0")` compares a pointer with the address of a string literal, not the character it points to. It is essentially never true. The correct test is `if (*s == '\0')`.
    - `else if (s == sup)` compares two pointers, not the characters they point to. Since `s` and `sup` are different arrays, this is never true either. The correct test is `else if (*s == *sup)`.
    - `fun` is declared to return `int` but the first branch does a bare `return;` with no value.
    - `fun` is called in `main` before it is declared, so there is no prototype in scope.
    - `gets()` is dangerous and was removed from the C standard in C11; `fgets()` should be used.

    What actually happens
    - Both comparisons are always false, so control always falls into the `else` branch.
    - It prints the string from the current position, then recurses with `s+1` and never stops at the terminator — it keeps walking past the end of the array until the program segfaults.

    Corrected version — prints each suffix of `s` that does not match `sup` character by character
    ```c
    void fun(char *s, char *sup) {
        if (*s == '\0')
            return;
        else if (*s == *sup)
            fun(s + 1, sup + 1);
        else {
            printf("%s\n", s);
            fun(s + 1, sup);
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

    Answer: Output is `30`.

    Step 1 - value of y
    - `y = 6 + 3*3/5` → `3*3 = 9`, then `9/5 = 1` (integer division), so `y = 6 + 1 = 7`.

    Step 2 - macro substitution
    - `#define` performs plain text replacement with no parentheses added, so `x*x` becomes:
    - `9+2/4*3-2*4+(5-4)*3 * 9+2/4*3-2*4+(5-4)*3`
    - Only the trailing `(5-4)*3` of the first copy and the leading `9` of the second copy actually multiply together.

    Step 3 - evaluate
    - `2/4 = 0`, so `2/4*3 = 0` in both copies.
    - `(5-4)*3*9 = 1 × 3 × 9 = 27`
    - Expression: `9 + 0 − 8 + 27 + 0 − 8 + 3 = 23`
    - So `x*x = 23`.

    Step 4 - final
    - `i = 23 + 7 = 30`.

    - The lesson: a macro must be written as `#define x (9+2/4*3-2*4+(5-4)*3)`. With the parentheses, `x*x` would correctly be `(-2)*(-2) = 4` and `i` would be `11` instead.

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

    Answer: Output is `30`. This is the same problem as the previous question.

    Summary of the working
    - `y = 6 + 3*3/5 = 6 + 9/5 = 6 + 1 = 7` (integer division truncates 1.8 to 1).
    - `x*x` expands textually, not as a squared value:
      `9+2/4*3-2*4+(5-4)*3 * 9+2/4*3-2*4+(5-4)*3`
    - With `2/4 = 0` and `(5-4)*3*9 = 27`, the expression evaluates to `9 + 0 − 8 + 27 + 0 − 8 + 3 = 23`.
    - `i = 23 + 7 = 30`.

    - This question is a standard test of two things at once — macro substitution being textual, and integer division truncating.
    - `printf` is used without including `<stdio.h>`, which a strict compiler would reject.

41. **Find the output of the following code:** *[Dutch Bangla Bank Assistant Network/Hardware Engineer 2019 compact it 1160 (ET: BUET)]*
```c
int a=3; int b=10;
if(a>b)
    printf("A");
else
    printf("B");
```

    Answer: Output is `B`.

    Reason
    - The condition `a > b` tests `3 > 10`, which is false.
    - So the `if` branch is skipped and the `else` branch runs, printing `B`.
    - Only one of the two branches ever executes.

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

    Answer: Output is `012`.

    Trace

    | i | i != n ? | i == 3 ? | Printed | i after |
    |---|---|---|---|---|
    | 0 | 0 != 3, true | No | 0 | 1 |
    | 1 | 1 != 3, true | No | 1 | 2 |
    | 2 | 2 != 3, true | No | 2 | 3 |
    | 3 | 3 != 3, false | — | — | loop ends |

    - The `if (i == 3) continue;` line is dead code — the loop condition already stops the loop the moment `i` reaches 3, so `continue` is never reached.
    - Had the condition been `i != 5`, the `continue` at `i == 3` would have skipped the `i++` as well and caused an infinite loop. That is the classic danger of `continue` inside a `while` loop.

43. **What is the output of following program?** *[Sonali & Janata Bank Senior Officer (IT/ICT) 2018 compact it 1166 (ET: N/A)]*

    Answer: The question is `incomplete` — the program is not present. The snippets that appear most often in this position are traced below.

    Snippet 1 — recursion with a printed trace
    ```c
    #include <stdio.h>
    void fun(int n) {
        if (n > 0) {
            printf("%d ", n);
            fun(n - 1);
            printf("%d ", n);       // printed on the way BACK UP
        }
    }
    int main() { fun(3); return 0; }
    ```
    ```
       Output : 3 2 1 1 2 3

       Going down : 3 , 2 , 1
       Base case  : n = 0 , returns
       Coming up  : 1 , 2 , 3

       The second printf runs AFTER the recursive call returns, which is
       why the sequence is symmetrical.
    ```

    Snippet 2 — a function that cannot swap
    ```c
    #include <stdio.h>
    void swap(int a, int b) { int t = a; a = b; b = t; }
    int main() {
        int x = 5, y = 10;
        swap(x, y);
        printf("%d %d", x, y);
        return 0;
    }
    ```
    ```
       Output : 5 10

       C passes arguments BY VALUE. swap works on copies, so the caller's
       variables are untouched. Passing &x and &y and taking int* fixes it.
    ```

    Snippet 3 — array decay in a function
    ```c
    #include <stdio.h>
    void f(int a[]) { printf("%lu ", sizeof(a)); }
    int main() {
        int a[10];
        printf("%lu ", sizeof(a));      // 40
        f(a);                            // 8 - a POINTER, not an array
        return 0;
    }
    ```
    ```
       Output : 40 8

       An array passed to a function DECAYS to a pointer, so its size
       information is lost. This is why array functions in C always take
       an extra length parameter.
    ```

    Snippet 4 — static versus automatic storage
    ```c
    #include <stdio.h>
    int counter() {
        static int c = 0;
        return ++c;
    }
    int main() {
        printf("%d %d %d", counter(), counter(), counter());
        return 0;
    }
    ```
    ```
       The three values are 1, 2 and 3 - but the ORDER in which printf's
       arguments are evaluated is UNSPECIFIED in C. Many compilers evaluate
       right to left and print "3 2 1".

       The safe answer : the counter returns 1, 2, 3 in call order, but the
       printed order depends on the compiler. Written as three separate
       printf statements it is unambiguously 1 2 3.
    ```

    Snippet 5 — the goto and label pattern
    ```c
    #include <stdio.h>
    int main() {
        int i = 0;
        loop:
            printf("%d ", i);
            i++;
            if (i < 5) goto loop;
        return 0;
    }
    ```
    ```
       Output : 0 1 2 3 4
    ```

    Snippet 6 — the ternary operator chained
    ```c
    #include <stdio.h>
    int main() {
        int marks = 75;
        char grade = marks >= 80 ? 'A' :
                     marks >= 70 ? 'B' :
                     marks >= 60 ? 'C' : 'F';
        printf("%c", grade);
        return 0;
    }
    ```
    ```
       Output : B

       The ternary operator is RIGHT associative, so the chain reads as a
       nested if-else and stops at the first true condition.
    ```

    - The general method: `trace the program line by line with a variable table`, and check three things before answering — whether anything is undefined (multiple modification between sequence points, unspecified argument order), whether any integer division truncates, and whether each format specifier matches its argument.

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

   Answer:

   (i) Infinite loop — the program prints `10` forever.
   - `for(;;)` has an empty condition. In C an omitted condition is treated as permanently true, so the loop never ends.
   - `n` is never changed inside the loop, so the same value is printed endlessly: `10101010...`
   - The `return 0;` is unreachable. The program must be stopped externally with Ctrl+C.
   - `for(;;)` and `while(1)` are equivalent ways of writing an infinite loop.

   (ii) Output is `1`.
   - Iteration 1: `i` is 2, non-zero, so the conditional picks `--i`. That makes `i = 1` and yields 1, which is true, so the body prints `i` — now `1`.
   - Iteration 2: `i` is 1, non-zero, so `--i` runs again. `i` becomes 0 and the expression yields 0, which is false, so the loop ends before printing.
   - `j++` never executes, because `i` never reaches 0 while the condition is being tested with `i` non-zero.

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

    Answer: The program does not compile. There is no output.

    Error
    - `break` can only appear inside a loop (`for`, `while`, `do-while`) or inside a `switch` statement. Here it sits in the `else` branch of a plain `if`, with no enclosing loop.
    - GCC reports: `error: break statement not within loop or switch`.

    What the condition would have evaluated to
    - `a && b > c` is parsed as `a && (b > c)`, because relational operators bind tighter than `&&`.
    - `b > c` is `2 > 1`, which is true (1).
    - `a` is 5, which is non-zero, so also true.
    - `true && true` is true, so the `if` branch would have run and printed `Bangladesh`.

    Corrected version
    ```c
    #include <stdio.h>
    int main(void) {
        int a = 5, b = 2, c = 1;
        if (a && b > c)
            printf("Bangladesh");
        else
            printf("Not Bangladesh");
        return 0;
    }
    ```
    - Output: `Bangladesh`.

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

   Answer:

   (i) Output is `Digi`, and `n` holds `18`.
   - `strlen` is called BEFORE the `'\0'` is inserted, so `n = 18`, the full length of `"Digital Bangladesh"`.
   - Writing `'\0'` at index 4 replaces `'t'` and becomes the new string terminator.
   - `printf("%s")` therefore stops after `D i g i`, printing `Digi`.
   - The order of the two statements is the whole point of the question — swapping them would give `n = 4`.

   (ii) Output is
   ```
   0
   1
   2
   4
   ```
   - `continue` skips the `printf` when `i` equals 3, then jumps to `i++` and carries on.
   - The loop still completes all five iterations; only the printing for `i = 3` is skipped.
   - With `break` instead, the output would have been just `0 1 2`.

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

    Answer: Output is `0 0 1 3 1`.

    Evaluation of `m = (i++ && j++ && k++) || l++`
    - `i++` yields the old value `−1`. In C anything non-zero is true, so this is true, and `i` becomes `0`.
    - `j++` yields `−1`, true, and `j` becomes `0`.
    - `k++` yields `0`, which is false, and `k` becomes `1`. The `&&` chain is therefore false.
    - `false || l++` still evaluates the right side. `l++` yields `2`, true, and `l` becomes `3`.
    - `m = 1`.

    | Variable | Final value |
    |---|---|
    | i | 0 |
    | j | 0 |
    | k | 1 |
    | l | 3 |
    | m | 1 |

    - The two traps here: `−1` is true in C (only `0` is false), and post-increment yields the old value while still performing the increment.

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

    Answer: Output is `Bang`.

    Explanation
    - `"Bangladesh"` fills indices 0 to 9. Writing `'\0'` at index 4 replaces `'l'` with the terminator.
    - `strlen(str1)` is now 4, and that value is stored in `str2`. Note `str2` is declared as a single `char`, not a string — storing 4 in it is legal but unusual, and it is never printed anyway.
    - `printf("%s", str1)` stops at the first `'\0'`, so it prints `B a n g`.
    - The remaining characters `ladesh` are still in memory but unreachable through string functions.

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

    Answer: Output is `0 1 2 4 `.

    Trace

    | i | i == 3 ? | Action |
    |---|---|---|
    | 0 | No | prints `0 ` |
    | 1 | No | prints `1 ` |
    | 2 | No | prints `2 ` |
    | 3 | Yes | `continue` — printing skipped |
    | 4 | No | prints `4 ` |

    - `continue` jumps straight to the increment step, so only the printing for `i = 3` is missed. The loop still runs to completion.
    - In a `for` loop `continue` is safe, because the increment `++i` is part of the loop header and still executes. In a `while` loop the same code would skip the increment and hang.

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

    Answer: The program does not compile as written.

    Compilation error
    - `cout` is a C++ stream object declared in `<iostream>`, but only `<stdio.h>` is included and there is no `using namespace std;`.
    - The compiler reports `'cout' was not declared in this scope`.

    Output if the headers are fixed
    - Correcting the includes and adding parentheses, the intended code is `cout << (++i || ++j && ++k);` followed by `cout << i << j << k;`.
    - Precedence: `&&` binds tighter than `||`, so the expression is `++i || (++j && ++k)`.
    - `++i` makes `i = 2`, which is true. Because `||` short-circuits, the right-hand side is never evaluated at all.
    - So `j` and `k` remain `1`.
    - First `cout` prints `1` (the boolean result), then the second prints `211`.
    - Full output: `1211`.

    - A second subtlety: without parentheses, `cout << ++i || ...` would actually parse as `(cout << ++i) || ...` because `<<` binds tighter than `||`. That is why the parentheses matter.

51. **Find the mistake in the following program and write it correct form.** *[Investment Corporation Bangladesh Assistant Programmer 2017 compact it 1216 (ET: N/A)]*
```c
unsigned int i;
for(i=100; i<=0; --i)
printf("%d",i);
return 0;
```

    Answer:

    Mistakes found
    - Logic error — the condition `i <= 0` is false at the very start, since `i` begins at 100. The loop body never executes, so nothing is printed. It should be `i > 0`.
    - The unsigned trap — if the condition were written as `i >= 0`, the loop would run forever. An `unsigned int` can never be negative, so after `i` reaches 0 the `--i` wraps around to 4,294,967,295 and the condition stays true.
    - Format specifier mismatch — `%d` prints a signed int. For an `unsigned int` the correct specifier is `%u`.
    - The code has no `#include <stdio.h>` and no `main()` function, so `printf` is undeclared and `return 0;` sits outside any function.

    Corrected form
    ```c
    #include <stdio.h>

    int main(void) {
        unsigned int i;
        for (i = 100; i > 0; --i)
            printf("%u ", i);
        return 0;
    }
    ```

    - This prints `100 99 98 ... 2 1` and stops cleanly at zero.
    - If counting down to 0 inclusive is required, use a signed `int` with the condition `i >= 0`.

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

    Answer: Output is `97 98 112 113 120 `.

    Explanation
    - `N - 2 = 5`, so the loop runs for `i = 0` to `4` — exactly the five characters of `"abpqx"`.
    - `%d` prints the ASCII code of the character, not the character itself.
    - Both `str[i]++` and `str[i]--` are post-operators, so the ORIGINAL value is printed and the change happens afterwards. That means the increment or decrement has no effect on what is displayed.

    | i | i % 2 | Operation | Character | ASCII printed | Value after |
    |---|---|---|---|---|---|
    | 0 | 0 (false) | `str[0]--` | 'a' | 97 | 96 |
    | 1 | 1 (true) | `str[1]++` | 'b' | 98 | 99 |
    | 2 | 0 | `str[2]--` | 'p' | 112 | 111 |
    | 3 | 1 | `str[3]++` | 'q' | 113 | 114 |
    | 4 | 0 | `str[4]--` | 'x' | 120 | 119 |

    - Key ASCII values: `'a' = 97`, `'b' = 98`, `'p' = 112`, `'q' = 113`, `'x' = 120`.
    - Had pre-operators been used (`++str[i]`), the modified values 98, 99, 111, 114, 119 would have been printed instead.

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

    Answer: Output is `-19, 0, 2, 0`.

    Step-by-step evaluation of `m = ++i && ++j && ++k`
    - `++i` — pre-increment makes `i = −19` and yields `−19`. Non-zero, so true. Continue.
    - `++j` — pre-increment makes `j = 0` and yields `0`. Zero is false.
    - `&&` short-circuits here: once an operand is false, the remaining operands are not evaluated at all.
    - Therefore `++k` never runs, and `k` stays at its original value `2`.
    - `m` receives the result of the whole expression, which is `0`.

    | Variable | Final value | Why |
    |---|---|---|
    | i | −19 | incremented from −20 |
    | j | 0 | incremented from −1 |
    | k | 2 | unchanged, short-circuited |
    | m | 0 | expression is false |

    - Note that `−20` and `−19` are both true in C. Only exactly `0` is false, which is why the chain stopped at `j` and not at `i`.

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

    Answer: Output is `2, 1, 2`.

    Breaking the statement into two halves

    Left side: `*((a) ? &b : &a)`
    - The condition `a` is `0`, which is false.
    - So the conditional selects `&a` — the address of `a`.
    - Dereferencing it gives `a` itself, so the left side is simply `a`.

    Right side: `a ? b : c`
    - Again `a` is `0`, false.
    - So the conditional selects `c`, whose value is `2`.

    Result
    - The statement becomes `a = 2`.
    - `b` and `c` are untouched, so they remain `1` and `2`.
    - Output: `2, 1, 2`.

    - The trick in this question is that the same condition `a` controls both sides, and the left side uses the conditional operator to choose which variable gets assigned — a legal but very unusual C idiom.

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

    Answer: The program does not compile. There is no output.

    Error
    - The controlling expression of a `switch` statement must have an integer type — `int`, `char`, `short`, `long` or an enum.
    - Here `n` is declared `float`, which is not allowed.
    - GCC reports: `error: switch quantity not an integer`. Clang says: `statement requires expression of integer type ('float' invalid)`.

    Why floats are forbidden in a switch
    - `switch` works by comparing the value against case labels for exact equality, and floating-point values cannot be compared reliably for exact equality because of rounding error. The standard therefore rules them out entirely.

    Corrected version
    ```c
    #include <stdio.h>
    int main(void) {
        int n = 2;                  // changed from float to int
        switch (n) {
            case 2:  printf("Hi");    break;
            default: printf("Hello");
        }
        return 0;
    }
    ```
    - This compiles and prints `Hi`.
    - Alternatively, keep the float and use an `if...else` chain instead of a `switch`.

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

    Answer: Output is `4`.

    Why — the macro expands textually
    - `max(i++, ++j)` becomes `(i++ > ++j ? i++ : ++j)`.
    - Note that the arguments appear TWICE in the expansion, so their side effects can happen twice.

    Step-by-step with `i = 1`, `j = 2`
    - Evaluate the condition `i++ > ++j`:
      - `i++` yields `1`, and `i` becomes `2`.
      - `++j` makes `j` become `3` and yields `3`.
      - `1 > 3` is false.
    - The false branch `++j` is taken: `j` becomes `4` and yields `4`.
    - So `k = 4`. Final state: `i = 2`, `j = 4`, `k = 4`.

    - This is the classic argument against function-like macros with side effects — `j` was incremented twice from a single call.
    - A real function `int max(int a, int b) { return a > b ? a : b; }` would evaluate each argument exactly once and return `2` here instead.

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

    Answer: Output is `1 3 6 10 15 21 28 36 45 `.

    Why the values accumulate
    - `total` is declared `static`, so it is initialised to 0 only once and keeps its value between calls. It is not recreated on each call the way an ordinary local variable would be.
    - Each call therefore adds the new `i` to the running total from all previous calls.

    | Call | i | total before | total after | Printed |
    |---|---|---|---|---|
    | 1 | 1 | 0 | 1 | 1 |
    | 2 | 2 | 1 | 3 | 3 |
    | 3 | 3 | 3 | 6 | 6 |
    | 4 | 4 | 6 | 10 | 10 |
    | 5 | 5 | 10 | 15 | 15 |
    | 6 | 6 | 15 | 21 | 21 |
    | 7 | 7 | 21 | 28 | 28 |
    | 8 | 8 | 28 | 36 | 36 |
    | 9 | 9 | 36 | 45 | 45 |

    - These are the triangular numbers — the running sum `1+2+...+n`, which equals `n(n+1)/2`.
    - Had `total` been a plain `int total = 0;`, it would have been reset on every call and the output would simply have been `1 2 3 4 5 6 7 8 9`.

## Recursion & Functions (38)

1. (a) Microprocessor এবং Microcontroller এর মধ্যে পার্থক্য লিখুন।
   (b) কোন প্রোগ্রামিং ভাষাকে 'C' programming language বলা হয়? একটি ছোট প্রোগ্রাম লিখুন, যা recursive function ব্যবহার করে ডিসপ্লেতে ৫ এর ফ্যাক্টোরিয়াল গণনা করবে। *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

   Answer:

   (a) Microprocessor vs Microcontroller

   | Point | Microprocessor | Microcontroller |
   |---|---|---|
   | Definition | Only the CPU on a single chip | CPU, RAM, ROM, I/O ports and timers on one chip |
   | Memory | RAM and ROM are external | RAM and ROM are built in |
   | Cost | Higher, because external chips are needed | Lower, a complete system on one chip |
   | Power use | High | Very low |
   | Purpose | General purpose computing | Dedicated, embedded control task |
   | Speed | Very high (GHz range) | Comparatively low (MHz range) |
   | Example | Intel Core i7, AMD Ryzen | 8051, Atmel AVR, PIC, Arduino |
   | Used in | Computers, laptops, servers | Washing machines, microwave ovens, cars, IoT devices |

   (b) Why the language is called 'C'
   - C was developed by Dennis Ritchie at Bell Labs in 1972. It was derived from an earlier language named B (written by Ken Thompson), which itself came from BCPL. Being the successor of B, the next letter of the alphabet was chosen — hence the name 'C'.

   Program — factorial of 5 using recursion
   ```c
   #include <stdio.h>

   int factorial(int n) {
       if (n == 0 || n == 1)
           return 1;                    // base case
       return n * factorial(n - 1);     // recursive case
   }

   int main(void) {
       printf("Factorial of 5 = %d\n", factorial(5));
       return 0;
   }
   ```

   - Call chain: `5 × factorial(4)` → `4 × factorial(3)` → `3 × factorial(2)` → `2 × factorial(1)` → `1`.
   - Unwinding gives `1 × 2 × 3 × 4 × 5 = 120`.
   - Output: `Factorial of 5 = 120`.

2. **Write a C program to find the sum of digits of an integer number using "recursion".** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1338 (ET: N/A)]*

   Answer:

   ```c
   #include <stdio.h>

   int sumOfDigits(int n) {
       if (n == 0)
           return 0;                        // base case
       return (n % 10) + sumOfDigits(n / 10);  // last digit + rest
   }

   int main(void) {
       int n;
       printf("Enter a number: ");
       scanf("%d", &n);
       if (n < 0) n = -n;
       printf("Sum of digits = %d\n", sumOfDigits(n));
       return 0;
   }
   ```

   Trace for `n = 1234`
   - `sumOfDigits(1234) = 4 + sumOfDigits(123)`
   - `sumOfDigits(123) = 3 + sumOfDigits(12)`
   - `sumOfDigits(12) = 2 + sumOfDigits(1)`
   - `sumOfDigits(1) = 1 + sumOfDigits(0)`
   - `sumOfDigits(0) = 0` — base case reached
   - Unwinding: `1 + 0 = 1`, `2 + 1 = 3`, `3 + 3 = 6`, `4 + 6 = 10`

   - Answer: `10`. Time complexity `O(d)` and space `O(d)` for the call stack, where `d` is the digit count.

3. **What is recursion?** *[BBA Assistant Programmer 12.07.2025 compact it 1432 (ET: BUET)]*

   Answer: Recursion is the process in which a function calls itself, directly or indirectly, to solve a smaller instance of the same problem. Such a function is called a recursive function.

   Two parts every recursive function must have
   - Base case — the condition that stops the recursion and returns a value directly. Without it the function calls itself forever and the program crashes with a stack overflow.
   - Recursive case — the function calls itself with a smaller input, moving closer to the base case each time.

   Example
   ```c
   int factorial(int n) {
       if (n == 0) return 1;            // base case
       return n * factorial(n - 1);     // recursive case
   }
   ```

   Advantages
   - Gives clean, short code for problems that are naturally recursive — tree traversal, Tower of Hanoi, backtracking, divide and conquer.

   Disadvantages
   - Slower, because every call carries function-call overhead.
   - Uses extra memory, since each call keeps its own stack frame on the call stack.
   - Deep recursion can overflow the stack.

   - Every recursive solution can be rewritten iteratively, usually with better speed and memory but longer code.

4. **Write recursive way below this program:** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 417 (ET: BUET)]*
```c
for(int i=1, i<n; i++)
    for(int j=0 ; j<i ; j ++)
        For( int k =0; k<i ; k++)
            X=X+1
```

   Answer: The three nested loops increment `X` once for every combination, so `X` grows by `i × i` for each value of `i`. The recursive version replaces each loop with a function that calls itself.

   ```c
   #include <stdio.h>

   int X = 0;

   void loopK(int k, int i) {               // innermost loop
       if (k >= i) return;
       X = X + 1;
       loopK(k + 1, i);
   }

   void loopJ(int j, int i) {               // middle loop
       if (j >= i) return;
       loopK(0, i);
       loopJ(j + 1, i);
   }

   void loopI(int i, int n) {               // outer loop
       if (i >= n) return;
       loopJ(0, i);
       loopI(i + 1, n);
   }

   int main(void) {
       int n = 4;
       loopI(1, n);
       printf("X = %d\n", X);
       return 0;
   }
   ```

   - Each loop becomes a function whose base case is the loop's exit condition and whose recursive call plays the role of the increment.
   - For `n = 4` the total is `1² + 2² + 3² = 1 + 4 + 9 = 14`.
   - Total work is `Σ i²` for `i = 1` to `n−1`, which is `O(n³)` — the same complexity as the loop version, but now with `O(n)` extra stack space.

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

   Answer: Output is

   ```
   5
   3
   1
   -1
   1
   3
   ```

   Trace — note `x` is a local copy in each call, and it is decremented twice per call
   - `fun(5)`: prints `5` (post-decrement leaves `x = 4`), then `--x` makes `x = 3` and calls `fun(3)`.
   - `fun(3)`: prints `3`, `x` becomes 2, then `--x` makes `x = 1` and calls `fun(1)`.
   - `fun(1)`: prints `1`, `x` becomes 0, then `--x` makes `x = -1` and calls `fun(-1)`.
   - `fun(-1)`: `x < 0`, so it returns immediately with no printing.
   - Unwinding — the second `printf` in each frame now runs, showing that frame's own `x`:
   - Back in `fun(1)`: prints `-1`
   - Back in `fun(3)`: prints `1`
   - Back in `fun(5)`: prints `3`

   - The two key points: `printf("%d", x--)` prints the value BEFORE decrementing, and each recursive call has its own separate copy of `x`.

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

   Answer: This is the Fibonacci function, and `F(5) = 5`. As written the code does not compile — the `if` conditions are missing parentheses, the parameter has no type, and the call `result F(5);` is not a valid statement.

   Corrected code
   ```c
   #include <stdio.h>

   int F(int n) {
       if (n == 0) return 0;
       if (n == 1) return 1;
       return F(n - 2) + F(n - 1);
   }

   int main(void) {
       printf("%d\n", F(5));
       return 0;
   }
   ```

   Recursion trace
   - `F(5) = F(3) + F(4)`
   - `F(4) = F(2) + F(3)`
   - `F(3) = F(1) + F(2) = 1 + 1 = 2`
   - `F(2) = F(0) + F(1) = 0 + 1 = 1`
   - So `F(4) = 1 + 2 = 3` and `F(5) = 2 + 3 = 5`.

   - Sequence: `F(0)=0, F(1)=1, F(2)=1, F(3)=2, F(4)=3, F(5)=5`.
   - Time complexity `O(2ⁿ)` because `F(3)` and lower are recomputed many times. Memoization brings this down to `O(n)`.

7. **What is function?** *[Sheikh Hasina National Institute of Youth Development Instructor ICT 20.05.2023 compact it 507 (ET: N/A)]*

   Answer: A function is a named block of code that performs one specific task. It is written once and can be called any number of times from anywhere in the program.

   Parts of a function
   - Declaration (prototype) — tells the compiler the return type, name and parameter types: `int add(int, int);`
   - Definition — the actual body containing the statements.
   - Call — the statement that invokes it: `result = add(5, 3);`

   General syntax
   ```c
   return_type function_name(parameter_list) {
       // body
       return value;
   }
   ```

   Types of function
   - Library (built-in) functions — already provided, such as `printf()`, `scanf()`, `sqrt()`, `strlen()`.
   - User-defined functions — written by the programmer for a specific need.

   Advantages
   - Reusability — write once, call many times.
   - Modularity — a large program is broken into small, manageable units.
   - Easier debugging and testing, since each function can be checked separately.
   - Less code duplication, so maintenance is simpler.

8. **Write a C/C++ program to calculte factorial of N using recursive function.** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 472 (ET: N/A)]*

   Answer:

   ```c
   #include <stdio.h>

   unsigned long long factorial(int n) {
       if (n <= 1)
           return 1;                    // base case: 0! = 1! = 1
       return n * factorial(n - 1);     // recursive case
   }

   int main(void) {
       int n;
       printf("Enter N: ");
       scanf("%d", &n);

       if (n < 0)
           printf("Factorial is not defined for negative numbers\n");
       else
           printf("Factorial of %d = %llu\n", n, factorial(n));
       return 0;
   }
   ```

   - For `n = 5`: `5 × 4 × 3 × 2 × 1 = 120`.
   - The base case `n <= 1` covers both `0!` and `1!`, which both equal 1.
   - Time complexity `O(n)`, space `O(n)` for the recursion stack. The iterative version needs only `O(1)` space.

9. **Write the recursive function of the below problem and find the recurrence relation of the function. F(n) = 1+2+3+..........+(n-1)+n** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 472 (ET: N/A)]*

   Answer:

   Recursive function
   ```c
   int F(int n) {
       if (n == 0)
           return 0;                    // base case
       return n + F(n - 1);             // recursive case
   }
   ```

   Recurrence relation for the VALUE
   - `F(n) = n + F(n − 1)`, with `F(0) = 0`
   - Expanding: `F(n) = n + (n−1) + (n−2) + ... + 1 = n(n+1)/2`

   Recurrence relation for the RUNNING TIME
   - Each call does one addition and makes one recursive call on a problem one step smaller.
   - `T(n) = T(n − 1) + c`, with `T(0) = c`

   Solving the time recurrence
   - `T(n) = T(n−1) + c`
   - `= T(n−2) + 2c`
   - `= T(n−k) + kc`
   - At `k = n`: `T(n) = T(0) + nc = c + nc`
   - Therefore `T(n) = O(n)`.

   - Space complexity is also `O(n)`, because `n` stack frames are open at the deepest point.
   - The closed formula `n(n+1)/2` gives the same answer in `O(1)` time.

10. **(a) Mention two basic differences between ‘Call by Value’ and ‘Call by Reference’. Write a simple program in C to swap two integer values using ‘Call by value’.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 487 (ET: N/A)]*

    Answer:

    Two basic differences
    - What is passed — call by value passes a copy of the variable, while call by reference passes its address.
    - Effect on the original — call by value cannot change the caller's variable, because the function works on a duplicate. Call by reference can change it, because both names refer to the same memory location.

    Program using call by value
    ```c
    #include <stdio.h>

    void swap(int a, int b) {            // receives copies
        int temp = a;
        a = b;
        b = temp;
        printf("Inside function: a = %d, b = %d\n", a, b);
    }

    int main(void) {
        int x = 10, y = 20;

        printf("Before swap: x = %d, y = %d\n", x, y);
        swap(x, y);
        printf("After swap:  x = %d, y = %d\n", x, y);
        return 0;
    }
    ```

    Output
    ```
    Before swap: x = 10, y = 20
    Inside function: a = 20, b = 10
    After swap:  x = 10, y = 20
    ```

    - The swap works inside the function but the caller's `x` and `y` are unchanged — this is exactly what "call by value" means.
    - To make the swap stick, pointers are needed: `void swap(int *a, int *b)` called as `swap(&x, &y)`.
    - Strictly, C only supports call by value; the call-by-reference effect is achieved by passing pointers, which are themselves passed by value.

11. **(b) Write a program in C using recursion to find the factorial of an integer.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 492 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    long long factorial(int n) {
        if (n == 0 || n == 1)
            return 1;                    // base case
        return n * factorial(n - 1);     // recursive case
    }

    int main(void) {
        int n;
        printf("Enter an integer: ");
        scanf("%d", &n);
        printf("Factorial of %d = %lld\n", n, factorial(n));
        return 0;
    }
    ```

    - For `n = 6` the calls unwind as `6 × 5 × 4 × 3 × 2 × 1 = 720`.
    - The base case is what prevents infinite recursion; removing it would crash the program with a stack overflow.
    - Time `O(n)`, space `O(n)` for the call stack.

12. **When a function is called more than one time that is called?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

    Answer: When a function calls itself repeatedly, it is called **recursion**, and such a function is a recursive function.

    - If the question means a function invoked several times from different places in a program, that is simply reusability — the main reason functions exist.
    - Two forms of recursion: direct recursion, where a function calls itself; and indirect recursion, where function A calls B and B calls A back.
    - Every recursive function needs a base case, otherwise it repeats forever and overflows the stack.

13. **(e) Write about the syntax of function.** *[BARC Programmer 04.08.2023 compact it 598 (ET: N/A)]*

    Answer: A function in C has three parts — declaration, definition and call.

    (a) Function declaration (prototype)
    ```c
    return_type function_name(parameter_type_list);
    ```
    - Example: `int add(int, int);`
    - Written before `main()` so the compiler knows the function exists and how it is used.

    (b) Function definition
    ```c
    return_type function_name(parameter_list) {
        // body — statements
        return value;
    }
    ```
    - Example:
    ```c
    int add(int a, int b) {
        return a + b;
    }
    ```

    (c) Function call
    ```c
    variable = function_name(arguments);
    ```
    - Example: `sum = add(5, 3);`

    Parts explained
    - `return_type` — the data type of the value sent back; `void` if nothing is returned.
    - `function_name` — a valid identifier, following the rules for variable names.
    - `parameter_list` — the inputs with their types; empty or `void` when there are none.
    - `return` — sends a value back and ends the function immediately.

14. **(ক) C প্রোগ্রামিং ল্যাঙ্গুয়েজে user defined function এবং library function এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 600 (ET: N/A)]*

    Answer:

    | Point | Library function | User-defined function |
    |---|---|---|
    | Who wrote it | Supplied with the compiler | Written by the programmer |
    | Definition location | Already compiled inside a library file | Written inside the programmer's own source file |
    | Header needed | Yes, the matching header must be included | Only a prototype, in the same file |
    | Name | Fixed and cannot be changed | Chosen freely by the programmer |
    | Purpose | Common, general tasks | Specific to the current problem |
    | Examples | `printf()`, `scanf()`, `sqrt()`, `strlen()`, `malloc()` | `add()`, `factorial()`, `isPrime()` |
    | Source code | Not available to the programmer | Fully visible and editable |

    - Both are called in exactly the same way; the difference lies only in who wrote and compiled them.
    - Library functions save time and are already tested, while user-defined functions handle logic that no library can know about.

15. **(ক) Call by Value এবং Call by Reference এর মধ্যে পার্থক্য কী?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 617 (ET: N/A)]*

    Answer:

    | Point | Call by Value | Call by Reference |
    |---|---|---|
    | What is passed | A copy of the variable | The address of the variable |
    | Parameter type | Ordinary variable — `void f(int x)` | Pointer — `void f(int *x)` |
    | Original variable | Cannot be changed | Can be changed |
    | Memory | Two separate locations, original plus copy | One shared location |
    | Memory cost | Higher for large data, since it is duplicated | Lower, only an address is passed |
    | Safety | Safer — the original is protected | Riskier — the original can be modified accidentally |
    | Use when | The original must not be altered | The function must alter the original, or return several values |

    Example
    ```c
    void byValue(int x)  { x = 100; }        // caller unaffected
    void byRef(int *x)   { *x = 100; }       // caller's variable changes

    int a = 5, b = 5;
    byValue(a);        // a is still 5
    byRef(&b);         // b becomes 100
    ```

    - Strictly, C supports only call by value. Passing a pointer gives the effect of call by reference, but the pointer itself is still passed by value.
    - Arrays are an exception — an array name decays to a pointer, so array arguments always behave like call by reference.

16. **(ঘ) উদাহরণসহ Parameter Passing ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 617 (ET: N/A)]*

    Answer: Parameter passing is the mechanism by which data is sent from a calling function to a called function.

    Two kinds of parameter
    - Formal parameter — the variable listed in the function definition. It exists only inside the function.
    - Actual parameter (argument) — the value or variable supplied at the call site.

    ```c
    int add(int a, int b) { ... }    // a, b are formal parameters
    sum = add(5, 3);                 // 5, 3 are actual parameters
    ```

    Method 1 — Call by value
    ```c
    #include <stdio.h>

    void increase(int x) {
        x = x + 10;
        printf("Inside: %d\n", x);   // 20
    }

    int main(void) {
        int a = 10;
        increase(a);
        printf("Outside: %d\n", a);  // 10, unchanged
        return 0;
    }
    ```
    - A copy of `a` is sent, so changes inside the function do not reach `main`.

    Method 2 — Call by reference (using pointers)
    ```c
    #include <stdio.h>

    void increase(int *x) {
        *x = *x + 10;
    }

    int main(void) {
        int a = 10;
        increase(&a);
        printf("Outside: %d\n", a);  // 20, changed
        return 0;
    }
    ```
    - The address of `a` is sent, so `*x` and `a` refer to the same memory and the change persists.

    - Arrays are always passed as pointers, so modifying an array inside a function changes the caller's array too.

17. **(খ) উদাহরণসহ recursion ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*

    Answer: Recursion is the technique in which a function solves a problem by calling itself on a smaller version of the same problem.

    Two required parts
    - Base case — stops the recursion by returning a value directly.
    - Recursive case — the function calls itself with an input closer to the base case.

    Example — factorial
    ```c
    int factorial(int n) {
        if (n == 0)                  // base case
            return 1;
        return n * factorial(n - 1); // recursive case
    }
    ```

    How `factorial(4)` works

    | Stage | Call | Waiting for | Returns |
    |---|---|---|---|
    | Going down | factorial(4) | factorial(3) | — |
    |  | factorial(3) | factorial(2) | — |
    |  | factorial(2) | factorial(1) | — |
    |  | factorial(1) | factorial(0) | — |
    | Base reached | factorial(0) | — | 1 |
    | Coming back up | factorial(1) | — | 1 × 1 = 1 |
    |  | factorial(2) | — | 2 × 1 = 2 |
    |  | factorial(3) | — | 3 × 2 = 6 |
    |  | factorial(4) | — | 4 × 6 = 24 |

    - Each call keeps its own copy of `n` in a separate stack frame, which is why the values are remembered while going down and used while coming back up.
    - Other natural uses: Fibonacci, Tower of Hanoi, tree traversal, binary search, merge sort.

18. **(ক) Tower of Hanoi সমস্যাটি সমাধানের জন্যে একটি recursive অ্যালগরিদম লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 622 (ET: N/A)]*

    Answer: Tower of Hanoi has three rods and `n` disks of different sizes, all stacked on the source rod in decreasing size. The whole stack must be moved to the destination rod under three rules — move one disk at a time, only the top disk of a rod may be moved, and a larger disk may never sit on a smaller one.

    Recursive idea
    - Move the top `n − 1` disks from source to auxiliary, using destination as the temporary rod.
    - Move the largest disk directly from source to destination.
    - Move those `n − 1` disks from auxiliary to destination, using source as the temporary rod.

    ```c
    #include <stdio.h>

    void towerOfHanoi(int n, char source, char auxiliary, char destination) {
        if (n == 1) {                                   // base case
            printf("Move disk 1 from %c to %c\n", source, destination);
            return;
        }
        towerOfHanoi(n - 1, source, destination, auxiliary);
        printf("Move disk %d from %c to %c\n", n, source, destination);
        towerOfHanoi(n - 1, auxiliary, source, destination);
    }

    int main(void) {
        int n = 3;
        towerOfHanoi(n, 'A', 'B', 'C');
        return 0;
    }
    ```

    Output for n = 3
    ```
    Move disk 1 from A to C
    Move disk 2 from A to B
    Move disk 1 from C to B
    Move disk 3 from A to C
    Move disk 1 from B to A
    Move disk 2 from B to C
    Move disk 1 from A to C
    ```

    - Number of moves = `2ⁿ − 1`. For `n = 3` that is 7 moves, and this is proven to be the minimum.
    - Recurrence: `T(n) = 2T(n−1) + 1`, giving `O(2ⁿ)` time and `O(n)` stack space.

19. **What are the differences between call by value and call by Reference?** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (CSE) 2022 compact it 667 (ET: N/A)], [BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 677 (ET: N/A)]*

    Answer:

    | Point | Call by Value | Call by Reference |
    |---|---|---|
    | Data passed | A copy of the actual value | The address of the variable |
    | Formal parameter | Ordinary variable | Pointer variable |
    | Change reflected in caller | No | Yes |
    | Memory locations used | Two — original and copy | One, shared |
    | Efficiency for large data | Poor, the whole object is copied | Good, only an address is copied |
    | Risk | None, the original is protected | Accidental modification is possible |
    | Returning multiple values | Not possible | Possible, through several pointers |
    | Syntax | `void f(int x)` … `f(a);` | `void f(int *x)` … `f(&a);` |

    - Classic demonstration: a swap function written with call by value appears to work inside the function but leaves the caller's variables unchanged; the pointer version actually swaps them.
    - In C, arrays are always effectively passed by reference, because an array name decays into a pointer to its first element.

20. **Distinguish between Call by value and Call by referee in C/C++.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 670 (ET: N/A)]*

    Answer:

    | Point | Call by Value | Call by Reference |
    |---|---|---|
    | What is sent | Copy of the value | Address (C) or alias (C++ reference) |
    | Original variable | Unchanged | Can be modified |
    | Memory | Extra copy created | No copy, same location used |
    | Speed for large structures | Slow | Fast |
    | C support | Native and default | Simulated using pointers |
    | C++ support | Native and default | Native, using the `&` reference syntax |

    C++ reference syntax, which C does not have
    ```cpp
    void swap(int &a, int &b) {      // & makes these references
        int temp = a;
        a = b;
        b = temp;
    }
    // called simply as swap(x, y);  — no & needed at the call site
    ```

    C pointer equivalent
    ```c
    void swap(int *a, int *b) {
        int temp = *a;
        *a = *b;
        *b = temp;
    }
    // called as swap(&x, &y);
    ```

    - The C++ reference version is safer and easier to read, since it cannot be NULL and needs no dereferencing.

21. **Write a recursive algorithm to find the factorial of a positive integer from 1 to N.** *[BPSC (Ministry of Home Affairs) Assistant Database Administrator (ICT) 2022 compact it 674 (ET: N/A)]*

    Answer:

    Algorithm
    ```
    FACTORIAL(n)
      Step 1: if n = 0 or n = 1
                  return 1                  // base case
      Step 2: else
                  return n × FACTORIAL(n − 1)   // recursive case
    ```

    Program printing the factorial of every number from 1 to N
    ```c
    #include <stdio.h>

    unsigned long long factorial(int n) {
        if (n <= 1) return 1;
        return n * factorial(n - 1);
    }

    int main(void) {
        int n, i;
        printf("Enter N: ");
        scanf("%d", &n);

        for (i = 1; i <= n; i++)
            printf("Factorial of %d = %llu\n", i, factorial(i));
        return 0;
    }
    ```

    - For `N = 5` the output lists `1, 2, 6, 24, 120`.
    - Time complexity `O(n)` for a single factorial, and `O(n²)` for the loop that recomputes each one. Building them up iteratively would make the whole listing `O(n)`.
    - Space `O(n)` for the recursion stack.

22. **What do you mean by recursion? Calculate factorial function using recursion with C programming code.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 679 (ET: N/A)]*

    Answer: Recursion means a function calling itself, directly or indirectly, to solve a smaller instance of the same problem. It needs a base case to stop and a recursive case that shrinks the input each time.

    ```c
    #include <stdio.h>

    unsigned long long factorial(int n) {
        if (n == 0 || n == 1)
            return 1;                    // base case stops the recursion
        return n * factorial(n - 1);     // recursive case
    }

    int main(void) {
        int n;
        printf("Enter a number: ");
        scanf("%d", &n);
        printf("Factorial of %d = %llu\n", n, factorial(n));
        return 0;
    }
    ```

    How factorial(5) is computed
    - Going down: `5 × f(4)` → `4 × f(3)` → `3 × f(2)` → `2 × f(1)`
    - Base case: `f(1) = 1`
    - Coming back: `2 × 1 = 2`, `3 × 2 = 6`, `4 × 6 = 24`, `5 × 24 = 120`
    - Output: `120`

    - Why it works here: `n! = n × (n−1)!`, so the problem naturally reduces to a smaller version of itself — the definition of optimal recursive structure.

23. **Write a program with a recursive function that shows the sum of its digits. For example, input =3426, output will be 3+4+2+6=15.** *[GTCL Assistant Engineer (CSE) 2022 compact it 684 (ET: BUET)]*

    Answer:

    ```c
    #include <stdio.h>

    int sumDigits(int n) {
        if (n == 0)
            return 0;
        return (n % 10) + sumDigits(n / 10);
    }

    void showExpression(int n) {         // prints 3+4+2+6 style output
        if (n < 10) { printf("%d", n); return; }
        showExpression(n / 10);
        printf("+%d", n % 10);
    }

    int main(void) {
        int n = 3426;
        showExpression(n);
        printf(" = %d\n", sumDigits(n));
        return 0;
    }
    ```

    Output
    ```
    3+4+2+6 = 15
    ```

    - `sumDigits` peels off the last digit with `n % 10` and recurses on the rest with `n / 10`.
    - `showExpression` recurses FIRST and prints afterwards, which is what puts the digits in their original left-to-right order.
    - Time `O(d)` and space `O(d)`, where `d` is the number of digits.

24. **(a) Write down a recursive function to find out number of digits is an integer number (n). Draw the recursion tree when n= 5396.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 690 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    int countDigits(int n) {
        if (n == 0)
            return 0;                    // base case
        return 1 + countDigits(n / 10);  // one digit + digits of the rest
    }

    int main(void) {
        printf("%d\n", countDigits(5396));   // 4
        return 0;
    }
    ```

    Recursion tree for n = 5396 — this recursion is a straight chain, not a branching tree

    ```mermaid
    flowchart TD
        A["countDigits(5396)<br/>= 1 + countDigits(539)"] --> B["countDigits(539)<br/>= 1 + countDigits(53)"]
        B --> C["countDigits(53)<br/>= 1 + countDigits(5)"]
        C --> D["countDigits(5)<br/>= 1 + countDigits(0)"]
        D --> E["countDigits(0)<br/>= 0 (base case)"]
    ```

    Unwinding the calls

    | Call | Returns |
    |---|---|
    | countDigits(0) | 0 |
    | countDigits(5) | 1 + 0 = 1 |
    | countDigits(53) | 1 + 1 = 2 |
    | countDigits(539) | 1 + 2 = 3 |
    | countDigits(5396) | 1 + 3 = 4 |

    - Answer: 5396 has `4` digits.
    - Depth of recursion equals the number of digits, so time is `O(d)` and stack space is `O(d)`.
    - Note the base case must be `n == 0` returning 0; if the input itself is 0, this function returns 0 rather than 1, which should be handled separately if 0 must count as one digit.

25. **(খ) Recursion কি? Recursion পদ্ধতিতে একটি Integer সংখ্যার Factorial নির্ণয়ের জন্য C-Language এ একটি Program লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 767 (ET: N/A)]*

    Answer: Recursion is the process where a function calls itself to solve a smaller instance of the same problem. It must have a base case that ends the calls, and a recursive case that moves toward that base case.

    ```c
    #include <stdio.h>

    long long factorial(int n) {
        if (n == 0 || n == 1)
            return 1;                    // base case
        else
            return n * factorial(n - 1); // recursive case
    }

    int main(void) {
        int n;
        printf("Enter an integer: ");
        scanf("%d", &n);

        if (n < 0)
            printf("Factorial does not exist for negative numbers\n");
        else
            printf("Factorial of %d = %lld\n", n, factorial(n));
        return 0;
    }
    ```

    - For input 5 the output is `Factorial of 5 = 120`.
    - Advantage: the code mirrors the mathematical definition `n! = n × (n−1)!` exactly.
    - Disadvantage: each call consumes a stack frame, so very large `n` risks a stack overflow. An iterative loop avoids that.

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

    Answer: The logic is already correct; the bug is a name mismatch. The function is DEFINED as `someDigits` but is CALLED as `sumDigits`, both inside itself and in `main`. The compiler reports an undefined reference.

    Corrected program
    ```c
    #include <stdio.h>

    int sumDigits(int num) {             // renamed to match the calls
        if (num == 0)
            return 0;
        else
            return num % 10 + sumDigits(num / 10);
    }

    int main(void) {
        int n;
        scanf("%d", &n);
        printf("%d", sumDigits(n));
        return 0;
    }
    ```

    How the recursion works
    - `num % 10` extracts the last digit.
    - `num / 10` removes it, and the function recurses on what is left.
    - `num == 0` is the base case that stops the chain.

    Trace for input 1234
    - `4 + sumDigits(123)` → `3 + sumDigits(12)` → `2 + sumDigits(1)` → `1 + sumDigits(0)` → `0`
    - Unwinding: `1, 3, 6, 10`. Output: `10`.

27. **(b) Write down a pseudocode/program to generate all possible permutation for a given word.** *[BPSC Workshop Maintenance Engineer (CSE) 2021 compact it 793 (ET: N/A)]*

    Answer: The standard method is backtracking — fix one character at each position by swapping, recurse on the rest, then swap back to restore the original order.

    Pseudocode
    ```
    PERMUTE(str, left, right)
        if left = right
            print str
        else
            for i = left to right
                swap str[left] and str[i]
                PERMUTE(str, left + 1, right)
                swap str[left] and str[i]        // backtrack
    ```

    C program
    ```c
    #include <stdio.h>
    #include <string.h>

    void swap(char *a, char *b) { char t = *a; *a = *b; *b = t; }

    void permute(char *str, int left, int right) {
        int i;
        if (left == right) {
            printf("%s\n", str);
            return;
        }
        for (i = left; i <= right; i++) {
            swap(&str[left], &str[i]);
            permute(str, left + 1, right);
            swap(&str[left], &str[i]);       // undo the swap
        }
    }

    int main(void) {
        char str[] = "ABC";
        permute(str, 0, strlen(str) - 1);
        return 0;
    }
    ```

    Output for "ABC"
    ```
    ABC
    ACB
    BAC
    BCA
    CBA
    CAB
    ```

    - Number of permutations = `n!`. For 3 characters that is 6.
    - The backtracking swap is essential — without it the string would be left scrambled and later branches would produce wrong results.
    - Time complexity `O(n × n!)`, space `O(n)` for the recursion stack.

28. **Paython এ Recursive function ব্যবহার করে একটি ধনাত্মক সংখ্যার factorial মান বের করার function লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 866 (ET: BUET)]*

    Answer:

    ```python
    def factorial(n):
        if n < 0:
            return "Factorial is not defined for negative numbers"
        if n == 0 or n == 1:
            return 1                     # base case
        return n * factorial(n - 1)      # recursive case


    # driver code
    num = int(input("Enter a positive number: "))
    print("Factorial of", num, "is", factorial(num))
    ```

    - For `num = 5` the output is `Factorial of 5 is 120`.
    - Python has no fixed integer size, so factorials of very large numbers are computed exactly without overflow — unlike C.
    - Default recursion limit in Python is 1000, so `factorial(2000)` raises `RecursionError` unless the limit is raised or an iterative version is used.
    - Time `O(n)`, space `O(n)`.

29. **Write a program in C/Java to find out the factorial of a number using recursion also write its iterative program.** *[BPSC Assistant Programmer (Ministry of Health) 2021 compact it 915 (ET: N/A)]*

    Answer:

    Recursive version
    ```c
    long long factorialRecursive(int n) {
        if (n <= 1) return 1;
        return n * factorialRecursive(n - 1);
    }
    ```

    Iterative version
    ```c
    long long factorialIterative(int n) {
        long long fact = 1;
        int i;
        for (i = 2; i <= n; i++)
            fact *= i;
        return fact;
    }
    ```

    Complete program
    ```c
    #include <stdio.h>

    long long factorialRecursive(int n) {
        if (n <= 1) return 1;
        return n * factorialRecursive(n - 1);
    }

    long long factorialIterative(int n) {
        long long fact = 1;
        for (int i = 2; i <= n; i++) fact *= i;
        return fact;
    }

    int main(void) {
        int n;
        printf("Enter a number: ");
        scanf("%d", &n);
        printf("Recursive: %lld\n", factorialRecursive(n));
        printf("Iterative: %lld\n", factorialIterative(n));
        return 0;
    }
    ```

    Comparison

    | Point | Recursive | Iterative |
    |---|---|---|
    | Time complexity | O(n) | O(n) |
    | Space complexity | O(n) — call stack | O(1) |
    | Code length | Shorter, closer to the maths | Slightly longer |
    | Speed | Slower, function-call overhead | Faster |
    | Risk | Stack overflow for large n | None |

30. **১. পাইথন প্রোগ্রামিং এর রিকার্সিভ ফাংশন ব্যবহার করে ১০টি সংখ্যার যোগফল বের করার প্রোগ্রাম লিখ।** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 946 (ET: BUET)]*

    Answer:

    ```python
    def recursive_sum(numbers, index=0):
        if index == len(numbers):        # base case: past the last element
            return 0
        return numbers[index] + recursive_sum(numbers, index + 1)


    # driver code
    numbers = []
    for i in range(10):
        numbers.append(int(input(f"Enter number {i+1}: ")))

    print("Sum of the 10 numbers =", recursive_sum(numbers))
    ```

    How it works
    - The base case returns 0 when the index moves past the end of the list.
    - Each call adds the current element to the sum of everything after it.
    - For `[1,2,3,4,5,6,7,8,9,10]` the result is `55`.

    Shorter alternative using slicing
    ```python
    def recursive_sum(numbers):
        if not numbers:
            return 0
        return numbers[0] + recursive_sum(numbers[1:])
    ```
    - This version is neater but slower, because each slice creates a new list — making it `O(n²)` in total.
    - The index version is `O(n)` time and `O(n)` stack space.

31. **(ii) Recursion কী? Recursion পদ্ধতির একটি Simple C-programming এর Code লিখুন।** *[BPSC Assistant Network Engineer 2020 compact it 954 (ET: N/A)]*

    Answer: Recursion is a technique in which a function calls itself to solve a smaller version of the same problem, until a base case is reached that can be answered directly.

    Two mandatory parts
    - Base case — the stopping condition.
    - Recursive case — the self-call on a smaller input.

    Simple example — sum of the first n natural numbers
    ```c
    #include <stdio.h>

    int sum(int n) {
        if (n == 0)
            return 0;                    // base case
        return n + sum(n - 1);           // recursive case
    }

    int main(void) {
        int n;
        printf("Enter n: ");
        scanf("%d", &n);
        printf("Sum of 1 to %d = %d\n", n, sum(n));
        return 0;
    }
    ```

    Trace for n = 4
    - `sum(4) = 4 + sum(3) = 4 + 3 + sum(2) = 4 + 3 + 2 + sum(1) = 4 + 3 + 2 + 1 + sum(0)`
    - `sum(0) = 0`, so the total unwinds to `10`.

    - Every recursive call keeps its own stack frame, which is why the intermediate values are remembered.
    - Recursion gives shorter, clearer code for naturally recursive problems, at the cost of extra memory and slower execution.

32. **Usually, recursion involves a function calling itself until specified condition is met and it is very useful to find out the factorial. Write a recursive algorithm to find the factorial of a number.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 985 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

    Answer:

    Algorithm
    ```
    Algorithm FACTORIAL(n)
    Input : a non-negative integer n
    Output: the value of n!

    Step 1: Start
    Step 2: if n < 0 then
                print "Not defined" and stop
    Step 3: if n = 0 or n = 1 then
                return 1                       // base case
    Step 4: else
                return n × FACTORIAL(n − 1)    // recursive case
    Step 5: Stop
    ```

    Implementation
    ```c
    unsigned long long factorial(int n) {
        if (n == 0 || n == 1) return 1;
        return n * factorial(n - 1);
    }
    ```

    Why recursion suits factorial
    - The mathematical definition is itself recursive: `n! = n × (n−1)!` with `0! = 1`.
    - The code therefore reads exactly like the definition, which makes it easy to verify as correct.

    - Time complexity `O(n)` — one multiplication per level.
    - Space complexity `O(n)` — `n` stack frames stay open until the base case is reached.
    - For large `n` the value overflows quickly: `21!` already exceeds a 64-bit integer.

33. **(a) Write down a function to compute the sum of the row an $n \times m$ matrix of integer.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1130-1131 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>
    #define MAXM 20

    // stores the sum of each row into rowSum[]
    void rowSums(int matrix[][MAXM], int n, int m, int rowSum[]) {
        int i, j;
        for (i = 0; i < n; i++) {
            rowSum[i] = 0;
            for (j = 0; j < m; j++)
                rowSum[i] += matrix[i][j];
        }
    }

    int main(void) {
        int matrix[20][MAXM], rowSum[20];
        int n, m, i, j;

        printf("Enter n and m: ");
        scanf("%d %d", &n, &m);

        printf("Enter matrix elements:\n");
        for (i = 0; i < n; i++)
            for (j = 0; j < m; j++)
                scanf("%d", &matrix[i][j]);

        rowSums(matrix, n, m, rowSum);

        for (i = 0; i < n; i++)
            printf("Sum of row %d = %d\n", i + 1, rowSum[i]);
        return 0;
    }
    ```

    Example
    - For the matrix `{{1,2,3},{4,5,6}}` the row sums are `6` and `15`.

    - In C the second dimension of a 2-D array parameter must be a compile-time constant, which is why `MAXM` is used in the signature.
    - Passing `rowSum[]` lets the function return `n` values at once, since a C function can return only one value directly.
    - Time complexity `O(n × m)`, space `O(n)` for the result array.

34. **What is recursive function? Give an example of recursive function.** *[WZPDCL Assistant Engineer (CSE) 2019 compact it 1152 (ET: KUET)]*

    Answer: A recursive function is a function that calls itself, either directly or indirectly, in order to solve a smaller instance of the same problem.

    Requirements
    - A base case, which returns a value without calling the function again. This is what terminates the recursion.
    - A recursive case, which calls the function with an argument that is closer to the base case.

    Example — Fibonacci numbers
    ```c
    #include <stdio.h>

    int fibonacci(int n) {
        if (n == 0) return 0;            // base case 1
        if (n == 1) return 1;            // base case 2
        return fibonacci(n - 1) + fibonacci(n - 2);
    }

    int main(void) {
        int i;
        for (i = 0; i < 10; i++)
            printf("%d ", fibonacci(i));
        return 0;
    }
    ```

    Output
    ```
    0 1 1 2 3 5 8 13 21 34
    ```

    Types of recursion
    - Direct — the function calls itself, as above.
    - Indirect — function A calls B, and B calls A back.
    - Tail recursion — the recursive call is the very last operation, which some compilers optimise into a loop.

    - Note this Fibonacci version is `O(2ⁿ)` because it recomputes the same values repeatedly. Adding memoization reduces it to `O(n)`.

35. **Difference between call by value and call by reference with example.** *[Palli Sanchay Bank Assistant Programmer 2018 compact it 1166-1167 (ET: N/A)]*

    Answer:

    | Point | Call by Value | Call by Reference |
    |---|---|---|
    | What is passed | A copy of the value | The address of the variable |
    | Original variable | Cannot be changed | Can be changed |
    | Parameter declared as | `int x` | `int *x` |
    | Call written as | `f(a)` | `f(&a)` |
    | Memory | Two copies exist | One shared location |
    | Efficiency for large data | Poor | Good |

    Example showing both
    ```c
    #include <stdio.h>

    void swapByValue(int a, int b) {
        int t = a; a = b; b = t;
    }

    void swapByReference(int *a, int *b) {
        int t = *a; *a = *b; *b = t;
    }

    int main(void) {
        int x = 10, y = 20;

        swapByValue(x, y);
        printf("After call by value:     x = %d, y = %d\n", x, y);

        swapByReference(&x, &y);
        printf("After call by reference: x = %d, y = %d\n", x, y);
        return 0;
    }
    ```

    Output
    ```
    After call by value:     x = 10, y = 20
    After call by reference: x = 20, y = 10
    ```

    - The value version swaps only its own local copies, which vanish when the function returns.
    - The reference version works through addresses, so it modifies the caller's actual variables.

36. **Write Algorithm of Fibonacci series.** *[Palli Sanchay Bank Programmer 2018 compact it 1171-1172 (ET: N/A)]*

    Answer: The Fibonacci series starts with 0 and 1, and every later term is the sum of the two before it: `F(n) = F(n−1) + F(n−2)`.

    Iterative algorithm — the efficient one
    ```
    Algorithm FIBONACCI(n)
    Step 1: Start
    Step 2: set a = 0, b = 1
    Step 3: if n >= 1, print a
    Step 4: if n >= 2, print b
    Step 5: for i = 3 to n
                next = a + b
                print next
                a = b
                b = next
            end for
    Step 6: Stop
    ```

    Recursive algorithm
    ```
    Algorithm FIB(n)
    Step 1: if n = 0 then return 0
    Step 2: if n = 1 then return 1
    Step 3: return FIB(n − 1) + FIB(n − 2)
    ```

    - Series: `0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, ...`
    - The iterative version runs in `O(n)` time and `O(1)` space.
    - The recursive version is `O(2ⁿ)` in time because branches recompute the same values; memoization or a DP table reduces it to `O(n)`.

37. **Write the performance of a non-recursive function which is written in recursive way.** *[Agrani Bank Ltd. Officer (ICT) 2017 compact it 1224 (ET: N/A)]*

    Answer: When an iterative (non-recursive) task is rewritten recursively, correctness stays the same but performance normally gets worse.

    Comparison for the same problem

    | Aspect | Iterative version | Recursive version |
    |---|---|---|
    | Time complexity | Same order, e.g. O(n) | Same order, but a larger constant |
    | Actual speed | Faster | Slower — every call has overhead |
    | Space complexity | O(1) | O(n) for the call stack |
    | Overhead per step | Loop counter update | Push arguments, return address and locals; then pop |
    | Risk | None | Stack overflow when the depth is large |
    | Code readability | Longer but explicit | Shorter and closer to the definition |

    Example — sum of 1 to n
    ```c
    int sumIterative(int n) { int s = 0; for (int i = 1; i <= n; i++) s += i; return s; }
    int sumRecursive(int n) { return (n == 0) ? 0 : n + sumRecursive(n - 1); }
    ```
    - Both are `O(n)` in time, but the recursive one uses `O(n)` stack space and will crash for `n` around a million, whereas the iterative one handles it easily.

    Where recursion is still worth it
    - Problems that are naturally recursive — tree traversal, Tower of Hanoi, backtracking, divide and conquer. There the clarity gained outweighs the overhead.
    - Tail-recursive functions can be optimised by the compiler into a loop, removing the stack cost entirely.

38. **Write a program in C with recursive function to compute the value $X^n$ where n is a positive integer and x has real value.** *[Multiple Ministry Assistant Programmer 2017 compact it 1235-1236 (ET: N/A)]*

    Answer:

    ```c
    #include <stdio.h>

    double power(double x, int n) {
        if (n == 0)
            return 1.0;                  // base case: x^0 = 1
        return x * power(x, n - 1);      // recursive case
    }

    int main(void) {
        double x;
        int n;

        printf("Enter x (real) and n (positive integer): ");
        scanf("%lf %d", &x, &n);

        printf("%.2lf ^ %d = %.4lf\n", x, n, power(x, n));
        return 0;
    }
    ```

    Trace for `x = 2.5`, `n = 3`
    - `power(2.5, 3) = 2.5 × power(2.5, 2)`
    - `power(2.5, 2) = 2.5 × power(2.5, 1)`
    - `power(2.5, 1) = 2.5 × power(2.5, 0)`
    - `power(2.5, 0) = 1.0` — base case
    - Unwinding: `2.5`, `6.25`, `15.625`

    Faster version — exponentiation by squaring
    ```c
    double fastPower(double x, int n) {
        if (n == 0) return 1.0;
        double half = fastPower(x, n / 2);
        if (n % 2 == 0) return half * half;
        return x * half * half;
    }
    ```

    - The simple version is `O(n)`; the squaring version is `O(log n)`, since it halves the exponent at every step.
    - `double` is used because `x` may be a real number and the result grows fast.

## Operators, Data Types & Language Concepts (25)

1. **(b) What is the difference between sizeof c+1 and sizeof (c+1)?** *[BPSC (Multiple Ministry) Assistant Programmer (CSE) 19.07.2023 compact it 483 (ET: N/A)]*

   Answer: The difference is operator precedence and integer promotion. Assume `char c;` on a machine where `char` is 1 byte and `int` is 4 bytes.

   `sizeof c + 1`
   - `sizeof` applied to a variable does not need parentheses, and it binds tighter than `+`.
   - So this parses as `(sizeof c) + 1` = `1 + 1` = `2`.
   - The `+ 1` is ordinary arithmetic done AFTER the size is found.

   `sizeof (c + 1)`
   - Here the parentheses make `c + 1` the operand of `sizeof`.
   - In C, a `char` in an arithmetic expression is promoted to `int` — this is called integer promotion.
   - So the type of `c + 1` is `int`, and the result is `4`.

   | Expression | Parsed as | Result |
   |---|---|---|
   | `sizeof c + 1` | `(sizeof c) + 1` | 2 |
   | `sizeof (c + 1)` | size of an `int` expression | 4 |

   - Extra point: `sizeof` never evaluates its operand at run time, so `sizeof(c++)` does not actually increment `c`. The size is decided entirely at compile time.

2. **What is the difference between Null and Void?** *[BCC Assistant Programmer 11.11.2023 compact it 546 (ET: N/A)]*

   Answer:

   | Point | NULL | void |
   |---|---|---|
   | What it is | A macro constant, defined as `((void*)0)` | A data type keyword |
   | Represents | A pointer that points to nothing | The absence of any type or value |
   | Where used | Assigned to a pointer variable | Function return type, parameter list, generic pointer |
   | Value | A pointer value, numerically 0 | Not a value at all |
   | Defined in | `<stddef.h>`, `<stdio.h>` and others | Built into the language |
   | Example | `int *p = NULL;` | `void display(void) { ... }` |

   - `NULL` is used to mark a pointer as "not pointing anywhere yet". Dereferencing it causes a run-time crash, so it should always be checked: `if (p != NULL)`.
   - `void` has three uses: a function that returns nothing (`void f()`), a function that takes no parameters (`f(void)`), and a generic pointer (`void *p`) that can hold the address of any type but must be cast before dereferencing.
   - `'\0'` is a third, different thing — the null character that terminates a C string.

3. **What can be used to terminate for(;;)?** *[BCC Assistant Programmer 11.11.2023 compact it 547 (ET: N/A)]*

   Answer: `for(;;)` has no condition, so it is an infinite loop. It can be terminated in these ways.

   - `break` — the normal way. It exits the loop immediately and control moves to the statement after the loop.
   ```c
   for (;;) {
       if (condition) break;
   }
   ```
   - `return` — ends the whole function, so the loop stops with it.
   - `goto label;` — jumps to a label outside the loop. It works but is discouraged.
   - `exit(0)` — from `<stdlib.h>`, terminates the entire program.

   - `continue` does NOT terminate the loop; it only skips the rest of the current iteration and starts the next one.
   - `for(;;)` and `while(1)` are exactly equivalent. An omitted condition in a `for` header is treated as permanently true.

4. **What will occur when an array is declared without size?** *[BCC Assistant Programmer 11.11.2023 compact it 548 (ET: N/A)]*

   Answer: It depends on whether an initializer is given.

   Case 1 — declared without size but WITH an initializer: this is legal.
   ```c
   int a[] = {10, 20, 30, 40};      // size becomes 4 automatically
   char s[] = "Hello";              // size becomes 6, including '\0'
   ```
   - The compiler counts the initializers and fixes the size at compile time.

   Case 2 — declared without size and WITHOUT an initializer: this is a compile error.
   ```c
   int a[];                         // error: array size missing
   ```
   - The compiler cannot decide how much memory to reserve, so it rejects the declaration.

   Case 3 — as a function parameter: this is legal and the size is simply ignored.
   ```c
   void f(int a[], int n) { ... }   // a decays to int *a
   ```
   - Which is exactly why the length must be passed separately as `n`.

   - Note that `sizeof(a)/sizeof(a[0])` correctly gives the element count in case 1, but not inside a function, where `a` is only a pointer.

5. **(ক) Local variable এবং Global variable এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 601 (ET: N/A)]*

   Answer:

   | Point | Local variable | Global variable |
   |---|---|---|
   | Declared | Inside a function or block | Outside all functions |
   | Scope | Visible only inside that function or block | Visible throughout the whole program |
   | Lifetime | Created on entry, destroyed on exit | Exists for the entire program run |
   | Storage | Stack | Data segment |
   | Default value | Garbage, if not initialised | Automatically 0 |
   | Access from other functions | Not possible | Possible |
   | Name reuse | The same name may be reused in different functions | One name for the whole program |
   | Memory use | Freed as soon as the function ends | Occupied for the full run |

   Example
   ```c
   #include <stdio.h>
   int g = 10;                      // global

   void show(void) {
       int l = 20;                  // local to show()
       printf("%d %d\n", g, l);     // both visible here
   }

   int main(void) {
       show();
       printf("%d\n", g);           // g visible, l is not
       return 0;
   }
   ```

   - If a local variable has the same name as a global one, the local shadows the global inside that block.
   - Global variables should be used sparingly, because any function can change them, which makes bugs hard to trace.

6. **(খ) আমি কী ৩২৬৭৮ মান সংরক্ষণ করতে ‘int’ ডাটা টাইপ ব্যবহার করতে পারি? না পারলে কেন?** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 617 (ET: N/A)]*

   Answer: Yes, 32678 can be stored in an `int`, but the margin depends on the machine.

   On a modern 32-bit `int` (the usual case today)
   - Range is `−2,147,483,648` to `2,147,483,647`.
   - 32678 is far inside that range, so there is no problem at all.

   On an older 16-bit `int`
   - Range is `−32,768` to `32,767`.
   - 32678 is still less than 32767, so it fits — but only by 89. Any value from 32768 upward would overflow and wrap round to a negative number.

   | Type | Size | Range | Can hold 32678? |
   |---|---|---|---|
   | short int | 2 bytes | −32,768 to 32,767 | Yes, barely |
   | int (32-bit) | 4 bytes | −2.1 billion to 2.1 billion | Yes, easily |
   | unsigned short | 2 bytes | 0 to 65,535 | Yes |

   - Practical advice: since the C standard only guarantees `int` to be at least 16 bits, a value this close to the 16-bit limit is safer stored in a `long int`, or checked with `sizeof(int)` and `<limits.h>` first.

7. **(গ) ‘++i’ এবং ‘i++’ অভিব্যক্তি দুটির মধ্যে পার্থক্য কী? উদাহরণসহ ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 617 (ET: N/A)]*

   Answer: Both add 1 to `i`. The difference is WHEN the new value becomes visible to the surrounding expression.

   | Point | ++i (pre-increment) | i++ (post-increment) |
   |---|---|---|
   | Order | Increment first, then use the value | Use the old value first, then increment |
   | Value of the expression | The NEW value | The OLD value |
   | Effect on i | Same — i increases by 1 either way | Same |
   | Speed | Marginally faster, no temporary copy needed | Needs to keep the old value |

   Example
   ```c
   int i = 5, a, b;

   a = ++i;     // i becomes 6, then a = 6   → i = 6, a = 6
   
   int j = 5;
   b = j++;     // b = 5 (old value), then j becomes 6 → j = 6, b = 5
   ```

   Another common case
   ```c
   int i = 5;
   printf("%d", ++i);   // prints 6
   
   int k = 5;
   printf("%d", k++);   // prints 5, but k is 6 afterwards
   ```

   - When used alone as a whole statement (`i++;` or `++i;`) the two are identical, because the expression value is discarded.
   - The difference only matters when the value is used — in an assignment, a condition, a function argument or an array subscript.

8. **What is the main difference between structure and array in C programming? Explain with examples.** *[BPSC (Ministry of Home Affairs) Assistant Engineer 17.05.2022 compact it 635 (ET: N/A)]*

   Answer: The main difference is the data type of the members — an array holds elements of the SAME type, while a structure holds members of DIFFERENT types.

   | Point | Array | Structure |
   |---|---|---|
   | Data type of members | All the same | May be different |
   | Memory | Always contiguous | Contiguous, but padding may be inserted |
   | Access | By index, `a[0]` | By member name, `s.name` |
   | Declaration keyword | None needed | `struct` |
   | Size | `elements × size of one element` | Sum of member sizes plus padding |
   | Pointer arithmetic | Supported | Not meaningful across members |
   | Assignment as a whole | Not allowed (`a = b` fails) | Allowed (`s1 = s2` works) |

   Array example
   ```c
   int marks[5] = {85, 90, 78, 92, 88};
   printf("%d", marks[2]);              // 78
   ```

   Structure example
   ```c
   struct Student {
       int roll;                        // int member
       char name[30];                   // char array member
       float cgpa;                      // float member
   };

   struct Student s1 = {101, "Rahim", 3.75};
   printf("%d %s %.2f", s1.roll, s1.name, s1.cgpa);
   ```

   - Use an array when many items of one kind must be stored; use a structure when one entity has several different attributes.
   - The two combine naturally: `struct Student class[50];` is an array of structures.

9. **Difference between array and structure data type.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 679 (ET: N/A)]*

   Answer:

   | Point | Array | Structure |
   |---|---|---|
   | Definition | A collection of elements of the same data type stored contiguously | A single variable grouping members that may be of different data types |
   | Members | Homogeneous | Heterogeneous |
   | Accessing | Index based, `arr[i]` | Name based, using the dot operator `s.member` |
   | Keyword | None | `struct` |
   | Whole-object assignment | Not allowed | Allowed |
   | Passing to a function | Passed as a pointer, so it behaves like call by reference | Passed by value by default, so a copy is made |
   | Memory | Exactly `n × sizeof(element)` | Sum of members plus padding for alignment |
   | Example | `int a[5];` | `struct Book { char title[50]; float price; };` |

   - Padding is worth noting: `struct { char c; int i; };` often occupies 8 bytes rather than 5, because the `int` must start on a 4-byte boundary.
   - Arrays give fast index arithmetic; structures give meaningful field names for related but differently typed data.

10. **Write down the types of errors which can occur the execution of a program.** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*

    Answer: Programming errors fall into four types.

    (a) Syntax errors
    - Violations of the language's grammar rules, caught by the compiler.
    - Examples: missing semicolon, unbalanced brace, misspelled keyword.
    - The program does not compile at all.

    (b) Semantic errors
    - The statement is grammatically valid but meaningless to the compiler.
    - Examples: using an undeclared variable, assigning a string to an `int`, calling a function with the wrong argument types.

    (c) Run-time errors
    - The program compiles and starts, then fails while executing.
    - Examples: division by zero, array index out of bounds, null pointer dereference, opening a file that does not exist, memory exhaustion.
    - Prevented by input validation and bounds checking.

    (d) Logical errors
    - The program runs to completion but produces the wrong answer. The compiler cannot detect these at all.
    - Examples: using `+` where `-` was meant, a loop that runs one time too many (off-by-one), wrong operator precedence.
    - Found only by testing and careful dry runs, and fixed by debugging.

    | Error type | Detected by | Program runs? | Result |
    |---|---|---|---|
    | Syntax | Compiler | No | Compilation fails |
    | Semantic | Compiler | No | Compilation fails |
    | Run-time | While executing | Starts, then crashes | Abnormal termination |
    | Logical | Nothing automatic | Yes, fully | Wrong output |

    - Logical errors are the hardest to find, because nothing warns you — only comparing the output with the expected result reveals them.

11. **Write the syntax of while and do while loop.** *[CAAB Assistant Programmer (AP) 2022 compact it 726 (ET: N/A)]*

    Answer:

    while loop — entry controlled
    ```c
    while (condition) {
        // statements
    }
    ```
    - The condition is tested BEFORE the body runs.
    - If the condition is false at the start, the body never executes — minimum 0 iterations.
    - No semicolon after `while (condition)`.

    do-while loop — exit controlled
    ```c
    do {
        // statements
    } while (condition);
    ```
    - The body runs FIRST, then the condition is tested.
    - The body always executes at least once — minimum 1 iteration.
    - A semicolon after `while (condition)` is mandatory.

    Example showing the difference with `int i = 10;`
    ```c
    while (i < 5) { printf("A"); i++; }      // prints nothing
    do    { printf("B"); i++; } while (i < 5);  // prints B once
    ```

    - Use `while` when the loop may not need to run at all; use `do-while` for things like a menu that must be displayed at least once.

12. **What is nested structure in C programming? Explain with example.** *[SPCB Sub-Assistant Programmer 2022 compact it 741 (ET: N/A)]*

    Answer: A nested structure is a structure that contains another structure as one of its members. It is used when one entity naturally contains another.

    Example
    ```c
    #include <stdio.h>

    struct Date {
        int day;
        int month;
        int year;
    };

    struct Employee {
        int id;
        char name[30];
        float salary;
        struct Date joinDate;        // nested structure member
    };

    int main(void) {
        struct Employee e = {101, "Karim", 45000.0, {15, 3, 2020}};

        printf("ID: %d\n", e.id);
        printf("Name: %s\n", e.name);
        printf("Joined: %d/%d/%d\n",
               e.joinDate.day, e.joinDate.month, e.joinDate.year);
        return 0;
    }
    ```

    Output
    ```
    ID: 101
    Name: Karim
    Joined: 15/3/2020
    ```

    - Access uses the dot operator twice: `outer.inner.member`, as in `e.joinDate.day`.
    - The inner structure must be declared before the outer one, or defined inside it.
    - Advantage: related fields stay grouped, so `Date` can be reused inside `Employee`, `Order`, `Invoice` and so on without repeating three fields each time.

13. **(ii) C Programming Language এ Array and Structure এর মধ্যে পার্থক্য লিখুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 784 (ET: N/A)]*

    Answer:

    | Point | Array | Structure |
    |---|---|---|
    | Member data types | All identical (homogeneous) | May differ (heterogeneous) |
    | Keyword required | None | `struct` |
    | Element access | By index — `a[0]`, `a[1]` | By member name — `s.roll`, `s.name` |
    | Memory layout | Strictly contiguous, no gaps | Contiguous but padding may be added for alignment |
    | Whole assignment | `a = b;` is illegal | `s1 = s2;` is legal |
    | Function argument | Decays to a pointer, behaves like call by reference | Copied by value unless a pointer is passed |
    | Size | `n × sizeof(element)` | Sum of members plus padding |
    | Purpose | Many values of one kind | Several attributes of one entity |

    Example
    ```c
    int marks[3] = {80, 75, 90};              // array

    struct Book {                              // structure
        char title[50];
        char author[30];
        float price;
        int pages;
    };
    struct Book b = {"C Programming", "Ritchie", 550.0, 272};
    ```

    - The two are often combined — `struct Book library[100];` is an array of structures, which is how records are usually stored.

14. **Write some default data type in C.** *[BCC CA Monitoring System Project 2021 compact it 830 (ET: N/A)]*

    Answer: The built-in (primary) data types of C are:

    | Data type | Size | Range | Format specifier |
    |---|---|---|---|
    | `char` | 1 byte | −128 to 127 | %c |
    | `int` | 4 bytes | −2,147,483,648 to 2,147,483,647 | %d |
    | `float` | 4 bytes | 1.2e−38 to 3.4e+38, 6 decimal digits | %f |
    | `double` | 8 bytes | 2.3e−308 to 1.7e+308, 15 decimal digits | %lf |
    | `void` | 0 byte | no value | — |

    With modifiers
    - `short int` (2 bytes), `long int` (8 bytes on 64-bit Linux), `long long int` (8 bytes)
    - `unsigned int` (0 to 4,294,967,295), `signed char`, `unsigned char` (0 to 255)
    - `long double` (usually 12 or 16 bytes)

    - These sizes are typical but not guaranteed by the standard; they depend on the compiler and architecture. Use `sizeof()` and `<limits.h>` to check.
    - Beyond these, C provides derived types (array, pointer, function) and user-defined types (`struct`, `union`, `enum`, `typedef`).

15. **Write the difference between Structure and Array.** *[BOF Assistant Engineer (EEE/ME/CSE) 2021 compact it 922 (ET: N/A)]*

    Answer:

    | Point | Structure | Array |
    |---|---|---|
    | Members | Different data types allowed | All the same data type |
    | Declared with | `struct` keyword | Just the type and `[]` |
    | Accessed by | Member name and the `.` operator | Numeric index |
    | Assignment of whole object | Allowed | Not allowed |
    | Default passing to function | By value (a full copy) | By reference (pointer decay) |
    | Memory | Members laid out in order, with padding | Elements packed with no gaps |
    | Typical use | One record with several fields | A list of similar values |

    Quick example
    ```c
    struct Student { int roll; char name[20]; float gpa; };  // structure
    int rolls[50];                                            // array
    ```

    - A structure describes ONE thing with many properties; an array describes MANY things of one property.
    - Note that `sizeof` on a structure can exceed the sum of its members because of alignment padding, whereas an array's size is always exact.

16. **Short question: (i) Difference between ++i and i++ (ii) Difference between Overloading and Overriding (iii) Polymorphism in Java (iv) String variable (v) Control structure in C programming (vi) Stack (vii) Debugging (viii) Increment and Decrement process in C programming (ix) Object in C++ (x) Data encapsulation** *[National University Assistant Programmer 2020 compact it 978-980 (ET: DU)]*

    Answer:

    (i) ++i vs i++
    - `++i` increments first and gives the new value; `i++` gives the old value and increments afterwards. Both change `i` by 1.

    (ii) Overloading vs Overriding

    | Point | Overloading | Overriding |
    |---|---|---|
    | Where | Same class | Base class and derived class |
    | Signature | Must differ | Must be identical |
    | Binding | Compile time (static) | Run time (dynamic) |
    | Also called | Compile-time polymorphism | Run-time polymorphism |

    (iii) Polymorphism in Java
    - "One name, many forms." A method call takes different behaviour depending on the object.
    - Compile-time polymorphism through method overloading; run-time polymorphism through method overriding with a base-class reference pointing to a derived object.

    (iv) String variable
    - In C, a string is a `char` array ending with the null character `'\0'`, for example `char name[20] = "Rahim";`. There is no separate string type.
    - In Java and C++ there is a proper `String` / `std::string` class with built-in operations.

    (v) Control structures in C
    - Sequential — statements run one after another.
    - Selection — `if`, `if-else`, nested `if`, `switch`.
    - Iteration — `for`, `while`, `do-while`.
    - Jump — `break`, `continue`, `goto`, `return`.

    (vi) Stack
    - A linear data structure following LIFO (Last In, First Out). Insertion and deletion both happen at one end called the top.
    - Operations: `push`, `pop`, `peek`, `isEmpty`, each `O(1)`.
    - Uses: function call management, expression evaluation, undo operations, backtracking.

    (vii) Debugging
    - The process of finding and removing errors from a program.
    - Techniques: print statements, a debugger with breakpoints and step execution, code review, unit tests, dry runs.

    (viii) Increment and decrement in C
    - `++` adds 1 and `--` subtracts 1. Each has a prefix and a postfix form, which differ in the value returned to the expression.

    (ix) Object in C++
    - An instance of a class. The class is the blueprint; the object is the actual variable that occupies memory and holds real data.
    - `Student s1;` creates an object `s1` of class `Student`.

    (x) Data encapsulation
    - Binding data and the functions that operate on it into a single unit (the class), and hiding the internal data from outside access.
    - Achieved with `private` members and `public` getter and setter methods. It protects data integrity and is one of the four pillars of OOP.

17. **নিচের if-else কে switch case এ পরিনত করুন। if(ch== 'A':: ch== 'E' :: ch== 'I' :: ch == 'O':: ch== 'U')** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1021 (ET: N/A)]*

    Answer: The condition checks whether `ch` is a vowel. The `::` in the printed question is a transcription of `||` (logical OR).

    Original if-else form
    ```c
    if (ch == 'A' || ch == 'E' || ch == 'I' || ch == 'O' || ch == 'U')
        printf("%c is a vowel\n", ch);
    else
        printf("%c is a consonant\n", ch);
    ```

    Converted to switch-case
    ```c
    switch (ch) {
        case 'A':
        case 'E':
        case 'I':
        case 'O':
        case 'U':
            printf("%c is a vowel\n", ch);
            break;
        default:
            printf("%c is a consonant\n", ch);
    }
    ```

    How the conversion works
    - Each value joined by `||` becomes its own `case` label.
    - The first four cases have no statements and no `break`, so control falls through to the fifth. This deliberate fall-through is exactly how OR conditions are expressed in a `switch`.
    - The `else` branch becomes `default`.

    - To handle lowercase too, add `case 'a': case 'e': case 'i': case 'o': case 'u':` alongside them.

18. **Answer the following question:** *[Bangladesh Competition Commission Programmer 2019 compact it 1063 (ET: DU)]*
   a. Polymorphism refers to \_\_\_\_\_\_\_?
   b. What is the simplest method to prove that a graph is bipartite?
   c. In C what is the correct syntax to a send a 3- dimension array as a parameter?
   d. The Size of the character variable in C is \_\_\_\_\_?
   e. In Java what is true about private constructor?

   Answer:

   (a) Polymorphism refers to the ability of one interface or name to take many forms — a single function name or operator behaving differently depending on the object or the arguments. In Greek it literally means "many forms".

   (b) The simplest method is 2-colouring using BFS. Colour the starting vertex, then colour every neighbour with the opposite colour as BFS proceeds. If an edge is ever found joining two vertices of the same colour, the graph is not bipartite. Equivalently, a graph is bipartite if and only if it contains no odd-length cycle. The check runs in `O(V + E)`.

   (c) All dimensions except the first must be specified:
   ```c
   void func(int arr[][10][20], int x);
   // or equivalently
   void func(int (*arr)[10][20], int x);
   ```
   - The first dimension may be left empty because the array decays into a pointer; the remaining dimensions are needed so the compiler can compute the address arithmetic.

   (d) The size of a `char` variable in C is **1 byte** (8 bits). This is fixed by the standard — `sizeof(char)` is always exactly 1. Its range is −128 to 127 for `signed char` and 0 to 255 for `unsigned char`.

   (e) A private constructor in Java means the class cannot be instantiated from outside itself. Consequences:
   - `new ClassName()` from another class causes a compile error.
   - The class cannot be subclassed, because a subclass constructor cannot call the private parent constructor.
   - It is used to implement the Singleton pattern, utility classes with only static methods, and factory-method-only creation.

19. **Coding এর সময় সংঘটিত ভুলসমূহ উদাহরণসহ ব্যাখ্যা করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1080 (ET: N/A)]*

    Answer: Errors made while coding fall into four categories.

    (a) Syntax error — breaking the grammar of the language, caught by the compiler.
    ```c
    int a = 10        // missing semicolon
    printf("%d", a)   // missing semicolon
    ```
    - The program will not compile until fixed.

    (b) Semantic error — grammatically valid but meaningless.
    ```c
    int a;
    a = "Hello";      // assigning a string to an int
    printf("%d", b);  // b was never declared
    ```

    (c) Run-time error — appears only while the program is executing.
    ```c
    int a = 10, b = 0;
    printf("%d", a / b);        // division by zero, crashes

    int arr[5];
    arr[10] = 100;              // index out of bounds
    ```

    (d) Logical error — the program runs perfectly but gives a wrong result.
    ```c
    // intended: average of two numbers
    average = a + b / 2;        // wrong, should be (a + b) / 2
    
    for (i = 1; i <= 10; i++)   // off-by-one if 1 to 9 was intended
    ```
    - Nothing warns the programmer; only testing against expected output reveals it.

    - Prevention: compile with warnings enabled (`gcc -Wall`), validate all input, use a debugger, and dry-run the logic on paper before coding.

20. **উদাহরণসহ i++ and ++i এর মধ্যে পার্থক্য লিখুন। Nested if কী?** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1082 (ET: N/A)]*

    Answer:

    Part 1 — i++ vs ++i
    - `i++` (post-increment): the expression yields the OLD value, then `i` is incremented.
    - `++i` (pre-increment): `i` is incremented first, and the expression yields the NEW value.

    ```c
    int i = 5, a;
    a = i++;        // a = 5, i = 6
    
    int j = 5, b;
    b = ++j;        // b = 6, j = 6
    ```
    - In both cases the variable ends up at 6. Only the value handed to the expression differs.
    - As a standalone statement (`i++;`) the two are identical.

    Part 2 — Nested if
    - A nested `if` is an `if` statement written inside the body of another `if` or `else`. The inner condition is tested only when the outer one is true.

    ```c
    if (marks >= 40) {
        if (marks >= 80)
            printf("Grade A+");
        else if (marks >= 60)
            printf("Grade A");
        else
            printf("Grade B");
    }
    else {
        printf("Fail");
    }
    ```

    - Use it when a decision depends on a previous decision — here the grade is only worked out for a student who has already passed.
    - Caution: an `else` always binds to the nearest unmatched `if`, so braces should be used to make the intent explicit.

21. **(খ) C প্রোগ্রামিং ল্যাঙ্গুয়েজে Structure ও Union এর মধ্যে পার্থক্য কী? উদাহরণসহ লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1083 (ET: N/A)]*

    Answer: The key difference is memory. A structure gives every member its own space, while a union makes all members share one space.

    | Point | Structure | Union |
    |---|---|---|
    | Keyword | `struct` | `union` |
    | Memory allocated | Sum of all members, plus padding | Size of the LARGEST member only |
    | Members holding a value | All at the same time | Only one at a time |
    | Writing to one member | Others are unaffected | Others are overwritten |
    | Initialisation | All members may be initialised | Only the first member can be initialised |
    | Use case | A record with several independent fields | Saving memory when only one field is needed at a time |

    Example
    ```c
    #include <stdio.h>

    struct S { int i; char c; float f; };
    union  U { int i; char c; float f; };

    int main(void) {
        printf("sizeof(struct S) = %zu\n", sizeof(struct S));  // 12 (4+1+3 padding+4)
        printf("sizeof(union U)  = %zu\n", sizeof(union U));   // 4  (largest member)

        union U u;
        u.i = 65;
        printf("u.i = %d\n", u.i);        // 65
        u.c = 'A';
        printf("u.i = %d\n", u.i);        // changed — same memory was overwritten
        return 0;
    }
    ```

    - In the union, writing `u.c` corrupts `u.i`, because both occupy the same bytes.
    - Unions are used in embedded systems and protocol parsing, where a field may hold one of several types depending on a separate tag.

22. **Which of the following is the correct order of evaluation?** *[BREB Assistant Hardware & Network Engineer 2019 compact it 1124 (ET: BREB)]*

    Answer: The options were not printed with the question, so the standard C operator precedence order is given, from highest to lowest.

    | Level | Operators | Associativity |
    |---|---|---|
    | 1 | `()` `[]` `->` `.` | Left to right |
    | 2 | `!` `~` `++` `--` unary `+` `-` `*` `&` `sizeof` | Right to left |
    | 3 | `*` `/` `%` | Left to right |
    | 4 | `+` `-` | Left to right |
    | 5 | `<<` `>>` | Left to right |
    | 6 | `<` `<=` `>` `>=` | Left to right |
    | 7 | `==` `!=` | Left to right |
    | 8 | `&` then `^` then `\|` | Left to right |
    | 9 | `&&` | Left to right |
    | 10 | `\|\|` | Left to right |
    | 11 | `?:` | Right to left |
    | 12 | `=` `+=` `-=` and other assignments | Right to left |
    | 13 | `,` | Left to right |

    Common memory aid: **BODMAS extended** — brackets, unary, multiplicative, additive, shift, relational, equality, bitwise, logical, conditional, assignment, comma.

    - Example: `a = 2 + 3 * 4` gives 14, not 20, because `*` outranks `+`.
    - Example: `a && b || c` is `(a && b) || c`, because `&&` outranks `||`.
    - Important caution: precedence decides how an expression is GROUPED, not the ORDER in which operands are evaluated. The evaluation order of function arguments and of most operands is unspecified in C.

23. **(c) Is it possible to convert all if-else code into switch code block? Give an example.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1130-1131 (ET: N/A)]*

    Answer: No. Not every `if-else` can be converted into a `switch`.

    Why not — the restrictions of switch
    - The controlling expression must be of integer or character type. Floating-point values and strings are not allowed.
    - Each `case` label must be a compile-time CONSTANT. Variables and expressions cannot be used.
    - Only equality is tested. Ranges and relational comparisons cannot be expressed directly.

    Example that CAN be converted — testing equality against constants
    ```c
    // if-else version
    if (day == 1) printf("Sunday");
    else if (day == 2) printf("Monday");
    else if (day == 3) printf("Tuesday");
    else printf("Invalid");

    // switch version
    switch (day) {
        case 1: printf("Sunday");  break;
        case 2: printf("Monday");  break;
        case 3: printf("Tuesday"); break;
        default: printf("Invalid");
    }
    ```

    Example that CANNOT be converted — a range test
    ```c
    if (marks >= 80)      printf("A+");
    else if (marks >= 70) printf("A");
    else if (marks >= 60) printf("A-");
    else                  printf("F");
    ```
    - A `switch` cannot express `marks >= 80`. A workaround is `switch (marks / 10)` with cases 10, 9, 8 and so on, but that only works because the ranges happen to be uniform.

    Other cases that cannot be converted
    - Conditions on `float` or `double` values.
    - Conditions comparing two variables, such as `if (a > b)`.
    - Conditions using `&&` or `||` between different variables.

    - Rule of thumb: `switch` suits a single variable compared against a fixed set of constants; `if-else` handles everything else.

24. **Using examples explain data types used in C language.** *[Multiple Ministry Assistant Programmer 2017 compact it 1231 (ET: N/A)]*

    Answer: A data type tells the compiler what kind of value a variable holds and how much memory to reserve for it. C data types fall into three groups.

    (a) Primary (basic) data types
    ```c
    char grade = 'A';           // 1 byte,  −128 to 127
    int age = 25;               // 4 bytes, about ±2.1 billion
    float price = 99.50;        // 4 bytes, 6 decimal digits
    double pi = 3.14159265358;  // 8 bytes, 15 decimal digits
    void display(void);         // no value
    ```

    (b) Derived data types
    ```c
    int marks[5] = {80, 75, 90, 65, 88};   // array
    int *ptr = &age;                        // pointer
    int add(int a, int b);                  // function
    ```

    (c) User-defined data types
    ```c
    struct Student { int roll; char name[30]; };   // structure
    union Data { int i; float f; };                // union
    enum Day { SUN, MON, TUE };                    // enumeration
    typedef unsigned int uint;                     // type alias
    ```

    Modifiers that change size or range
    ```c
    short int s;        // 2 bytes
    long int l;         // 8 bytes on 64-bit Linux
    unsigned int u;     // 0 to 4,294,967,295
    ```

    - Actual sizes depend on the compiler and machine, so `sizeof()` should be used rather than assuming them.
    - Choosing the right type matters: using `int` where `char` suffices wastes memory, and using `float` where `double` is needed loses precision.

25. **Explain in details the different forms of looping statement in C language.** *[Multiple Ministry Assistant Programmer 2017 compact it 1233-1235 (ET: N/A)]*

    Answer: A loop repeats a block of statements while a condition holds. C provides three loop statements.

    (a) for loop — used when the number of repetitions is known
    ```c
    for (initialization; condition; increment) {
        // statements
    }
    ```
    ```c
    for (i = 1; i <= 5; i++)
        printf("%d ", i);        // 1 2 3 4 5
    ```
    - All three parts sit in one line, which keeps counter-driven loops compact and readable.
    - Any part may be omitted; `for(;;)` is an infinite loop.

    (b) while loop — entry controlled, used when the count is not known in advance
    ```c
    while (condition) {
        // statements
    }
    ```
    ```c
    i = 1;
    while (i <= 5) { printf("%d ", i); i++; }
    ```
    - The condition is checked first, so the body may run zero times.
    - The programmer must remember to update the control variable inside the body, otherwise the loop never ends.

    (c) do-while loop — exit controlled, body always runs at least once
    ```c
    do {
        // statements
    } while (condition);
    ```
    ```c
    i = 1;
    do { printf("%d ", i); i++; } while (i <= 5);
    ```
    - Used for menus and input validation, where the prompt must appear at least once.
    - The semicolon after the closing `while` is mandatory.

    Comparison

    | Point | for | while | do-while |
    |---|---|---|---|
    | Control | Entry | Entry | Exit |
    | Minimum iterations | 0 | 0 | 1 |
    | Best when | Count is known | Count is unknown | Body must run once |
    | Init and update | In the header | Written separately | Written separately |

    Loop control statements
    - `break` — leaves the loop immediately.
    - `continue` — skips the rest of the current iteration and starts the next.
    - `goto` — jumps to a label; works but is discouraged.

    - Nested loops are loops inside loops, used for matrices and pattern printing. The inner loop completes fully for each single pass of the outer loop.

## Flowcharts & Algorithms (16)

1. **Draw and clearly describe a step-by-step flowchart for a User Login system. Your login must include: Taking a Username and Password as input. Checking the database. If correct: Granting access. If wrong: Adding 1 to a failed attempt counter. Access denied and block the account if the counter reaches 3.** *[Senior Officer IT (Job ID: 10225) Date: 22-05-2026 (ET: N/A)]*

   Answer:

   ```mermaid
   flowchart TD
       A([Start]) --> B[count = 0]
       B --> C[/Read Username and Password/]
       C --> D{Match found in database?}
       D -->|Yes| E[Grant access]
       E --> F[Reset count = 0]
       F --> Z([Stop])
       D -->|No| G[count = count + 1]
       G --> H{count >= 3 ?}
       H -->|Yes| I[Block the account]
       I --> Z
       H -->|No| J[/Show 'Invalid credentials'/]
       J --> C
   ```

   Step-by-step description
   - Step 1 — Start, and set the failed-attempt counter `count = 0`.
   - Step 2 — Read the username and password from the user.
   - Step 3 — Query the database for that username and compare the stored password.
   - Step 4 — If they match, grant access, reset the counter to 0 and stop.
   - Step 5 — If they do not match, increase `count` by 1.
   - Step 6 — If `count` has reached 3, block the account and stop.
   - Step 7 — Otherwise show an error message and go back to Step 2 for another attempt.

   - In a real system the password would never be compared in plain text; a salted hash of the entered password is compared with the stored hash.
   - The counter should be stored against the account in the database, not in memory, otherwise restarting the client resets it.

2. **Draw a Flow chart for print odd number for 1 to N.** *[BCC Assistant Programmer 18.10.2025 compact it 1442 (ET: BCC)]*

   Answer:

   ```mermaid
   flowchart TD
       A([Start]) --> B[/Read N/]
       B --> C[i = 1]
       C --> D{i <= N ?}
       D -->|No| G([Stop])
       D -->|Yes| E[/Print i/]
       E --> F[i = i + 2]
       F --> D
   ```

   Explanation
   - `i` starts at 1, the first odd number.
   - Each pass prints `i` and then adds 2, so only odd values are ever reached — no divisibility test is needed.
   - The loop ends as soon as `i` exceeds `N`.

   - For `N = 10` the output is `1 3 5 7 9`.
   - An alternative is `i = i + 1` with a check `if (i % 2 != 0)`, but stepping by 2 is half the work.

3. **১ থেকে ১০০ পর্যন্ত নাম্বার প্রদর্শনের ফ্লোচার্ট আক।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 381 (ET: BUET)]*

   Answer:

   ```mermaid
   flowchart TD
       A([Start]) --> B[i = 1]
       B --> C{i <= 100 ?}
       C -->|No| F([Stop])
       C -->|Yes| D[/Print i/]
       D --> E[i = i + 1]
       E --> C
   ```

   Explanation
   - Initialise the counter `i` to 1.
   - Check whether `i` is still within 100. If not, stop.
   - Print `i`, increase it by 1, and go back to the check.
   - The loop body runs exactly 100 times.

   Equivalent C code
   ```c
   for (i = 1; i <= 100; i++)
       printf("%d ", i);
   ```

4. **দুইটি সংখ্যার গ.সা.গু নির্ণয়ের জন্য ফ্লোচার্ট অঙ্কন করুন ও অ্যালগরিদম লিখুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 406 (ET: N/A)]*

   Answer: GCD (HCF) is found by Euclid's algorithm, which repeatedly replaces the pair `(a, b)` with `(b, a mod b)`.

   Algorithm
   ```
   Step 1: Start
   Step 2: Read a and b
   Step 3: while b != 0 do
               r = a mod b
               a = b
               b = r
           end while
   Step 4: Print a as the GCD
   Step 5: Stop
   ```

   Flowchart
   ```mermaid
   flowchart TD
       A([Start]) --> B[/Read a and b/]
       B --> C{b != 0 ?}
       C -->|No| G[/Print a as GCD/]
       G --> H([Stop])
       C -->|Yes| D[r = a mod b]
       D --> E[a = b]
       E --> F[b = r]
       F --> C
   ```

   Dry run with a = 48, b = 18
   - `r = 48 mod 18 = 12` → a = 18, b = 12
   - `r = 18 mod 12 = 6` → a = 12, b = 6
   - `r = 12 mod 6 = 0` → a = 6, b = 0
   - Loop ends, GCD = `6`.

   - Euclid's rule works because `gcd(a, b) = gcd(b, a mod b)`, and the numbers shrink fast, giving `O(log(min(a,b)))`.

5. **Write Algorithm and flowchart to find odd numbers between 1 to n where n is a positive integer.** *[Ministry of Land Assistant Maintenance Engineer 2023 compact it 596 (ET: N/A)]*

   Answer:

   Algorithm
   ```
   Step 1: Start
   Step 2: Read n
   Step 3: set i = 1
   Step 4: while i <= n do
               print i
               i = i + 2
           end while
   Step 5: Stop
   ```

   Flowchart
   ```mermaid
   flowchart TD
       A([Start]) --> B[/Read n/]
       B --> C[i = 1]
       C --> D{i <= n ?}
       D -->|No| G([Stop])
       D -->|Yes| E[/Print i/]
       E --> F[i = i + 2]
       F --> D
   ```

   - Starting at 1 and stepping by 2 guarantees every value visited is odd.
   - For `n = 9` the output is `1 3 5 7 9`.
   - Time complexity `O(n/2)`, which simplifies to `O(n)`.

6. **Write Algorithm and flowchart for printing 1+3+5+ \dots + N.** *[NPCBL Junior Assistant Manager (ICT) 2022 compact it 643 (ET: BUET)]*

   Answer:

   Algorithm
   ```
   Step 1: Start
   Step 2: Read N
   Step 3: set i = 1, sum = 0
   Step 4: while i <= N do
               sum = sum + i
               i = i + 2
           end while
   Step 5: Print sum
   Step 6: Stop
   ```

   Flowchart
   ```mermaid
   flowchart TD
       A([Start]) --> B[/Read N/]
       B --> C[i = 1, sum = 0]
       C --> D{i <= N ?}
       D -->|No| G[/Print sum/]
       G --> H([Stop])
       D -->|Yes| E[sum = sum + i]
       E --> F[i = i + 2]
       F --> D
   ```

   - For `N = 9`: `1 + 3 + 5 + 7 + 9 = 25`.
   - Useful property: the sum of the first `k` odd numbers is exactly `k²`. Here `k = 5`, so the sum is `5² = 25`.

7. **Write an Algorithm to check a number is Prime or not Prime.** *[NSDA Assistant Programmer Date: 04-03-2022 compact it 656 (ET: N/A)]*

   Answer:

   Algorithm
   ```
   Step 1: Start
   Step 2: Read n
   Step 3: if n < 2 then
               print "Not Prime" and go to Step 8
   Step 4: set i = 2, flag = 1
   Step 5: while i × i <= n do
               if n mod i = 0 then
                   set flag = 0
                   break
               i = i + 1
           end while
   Step 6: if flag = 1 then print "Prime"
   Step 7: else print "Not Prime"
   Step 8: Stop
   ```

   Flowchart
   ```mermaid
   flowchart TD
       A([Start]) --> B[/Read n/]
       B --> C{n < 2 ?}
       C -->|Yes| K[/Print Not Prime/]
       C -->|No| D[i = 2, flag = 1]
       D --> E{i*i <= n ?}
       E -->|No| I{flag = 1 ?}
       E -->|Yes| F{n mod i = 0 ?}
       F -->|Yes| G[flag = 0]
       G --> I
       F -->|No| H[i = i + 1]
       H --> E
       I -->|Yes| J[/Print Prime/]
       I -->|No| K
       J --> L([Stop])
       K --> L
   ```

   - Testing divisors only up to `√n` is enough, because any factor larger than `√n` must pair with a smaller one already checked.
   - Time complexity `O(√n)`.

8. **Write down the algorithm and draw the flowchart of Quadratic equation.** *[CAAB Programmer 2022 compact it 722 (ET: N/A)]*

   Answer: The roots of `ax² + bx + c = 0` come from `x = (−b ± √D) / 2a` where the discriminant `D = b² − 4ac`.

   Algorithm
   ```
   Step 1: Start
   Step 2: Read a, b, c
   Step 3: if a = 0 then print "Not a quadratic equation" and stop
   Step 4: D = b² − 4ac
   Step 5: if D > 0 then
               x1 = (−b + √D) / (2a)
               x2 = (−b − √D) / (2a)
               print "Real and distinct roots", x1, x2
   Step 6: else if D = 0 then
               x1 = −b / (2a)
               print "Real and equal roots", x1
   Step 7: else
               real = −b / (2a),  imag = √(−D) / (2a)
               print "Complex roots", real ± imag i
   Step 8: Stop
   ```

   Flowchart
   ```mermaid
   flowchart TD
       A([Start]) --> B[/Read a, b, c/]
       B --> C{a = 0 ?}
       C -->|Yes| M[/Print Not quadratic/]
       C -->|No| D[D = b*b - 4*a*c]
       D --> E{D > 0 ?}
       E -->|Yes| F[/Print two real distinct roots/]
       E -->|No| G{D = 0 ?}
       G -->|Yes| H[/Print two real equal roots/]
       G -->|No| I[/Print complex conjugate roots/]
       F --> N([Stop])
       H --> N
       I --> N
       M --> N
   ```

   - Example: `a=1, b=-5, c=6` gives `D = 25 − 24 = 1 > 0`, so the roots are 3 and 2.

9. **Draw a flowchart and write algorithm for finding Factorial value of an integer number.** *[CAAB Assistant Maintenance Engineer (AME) 2022 compact it 723 (ET: N/A)]*

   Answer:

   Algorithm
   ```
   Step 1: Start
   Step 2: Read n
   Step 3: if n < 0 then print "Not defined" and stop
   Step 4: set fact = 1, i = 1
   Step 5: while i <= n do
               fact = fact × i
               i = i + 1
           end while
   Step 6: Print fact
   Step 7: Stop
   ```

   Flowchart
   ```mermaid
   flowchart TD
       A([Start]) --> B[/Read n/]
       B --> C{n < 0 ?}
       C -->|Yes| I[/Print Not defined/]
       C -->|No| D[fact = 1, i = 1]
       D --> E{i <= n ?}
       E -->|No| H[/Print fact/]
       E -->|Yes| F[fact = fact * i]
       F --> G[i = i + 1]
       G --> E
       H --> J([Stop])
       I --> J
   ```

   - `fact` starts at 1 so that `0!` correctly returns 1 without a special case — the loop simply never runs.
   - For `n = 5` the value becomes `1 × 1 × 2 × 3 × 4 × 5 = 120`.
   - Time complexity `O(n)`.

10. **Draw a flowchart of the following series: 1+3+5+7+\dots+N** *[CAAB Assistant Programmer (AP) 2022 compact it 725 (ET: N/A)]*

    Answer:

    ```mermaid
    flowchart TD
        A([Start]) --> B[/Read N/]
        B --> C[i = 1, sum = 0]
        C --> D{i <= N ?}
        D -->|No| G[/Print sum/]
        G --> H([Stop])
        D -->|Yes| E[sum = sum + i]
        E --> F[i = i + 2]
        F --> D
    ```

    Trace for N = 7

    | i | sum before | sum after | next i |
    |---|---|---|---|
    | 1 | 0 | 1 | 3 |
    | 3 | 1 | 4 | 5 |
    | 5 | 4 | 9 | 7 |
    | 7 | 9 | 16 | 9 → loop ends |

    - Result: `16`, which matches `k² = 4² = 16` for the first 4 odd numbers.

11. **(খ) Algorithm কি? Algorithm প্রকাশের তিনটি পদ্ধতির নাম লিখুন।** *[BPSC Assistant Programmer (ICT Ministry) 2021 compact it 770 (ET: N/A)]*

    Answer: An algorithm is a finite, ordered sequence of unambiguous steps that takes some input and produces the required output in a finite amount of time.

    Properties every algorithm must have
    - Input — zero or more inputs.
    - Output — at least one output.
    - Definiteness — every step is clear and unambiguous.
    - Finiteness — it terminates after a finite number of steps.
    - Effectiveness — every step is simple enough to be carried out.

    Three methods of expressing an algorithm
    - Natural language (step-form) — the steps written in plain English or Bangla, numbered Step 1, Step 2 and so on. Easy to read but can be imprecise.
    - Flowchart — a diagram using standard symbols: oval for start/stop, parallelogram for input/output, rectangle for process, diamond for decision, arrows for flow. Very easy to follow visually.
    - Pseudocode — a mix of programming structure and plain language. It is precise like code but not tied to any particular language, so it converts directly into a program.

12. **Three types of control statements and their graphical presentation using flowchart or flow graph.** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1037-1038 (ET: BUET)]*

    Answer: Control statements decide the order in which statements execute. There are three basic types.

    (a) Sequence — statements execute one after another
    ```mermaid
    flowchart TD
        A[Statement 1] --> B[Statement 2]
        B --> C[Statement 3]
    ```

    (b) Selection (branching) — one path is chosen based on a condition. In C: `if`, `if-else`, `switch`.
    ```mermaid
    flowchart TD
        A{Condition} -->|True| B[Statement block 1]
        A -->|False| C[Statement block 2]
        B --> D[Continue]
        C --> D
    ```

    (c) Iteration (looping) — a block repeats while a condition holds. In C: `for`, `while`, `do-while`.
    ```mermaid
    flowchart TD
        A{Condition} -->|True| B[Loop body]
        B --> A
        A -->|False| C[Exit loop]
    ```

    - Jump statements — `break`, `continue`, `goto` and `return` — are a fourth group that transfer control unconditionally.
    - The structured programming theorem states that any program can be written using only these three constructs, which is why `goto` is discouraged.

13. **(ক) Loop কী? প্রবাহচিত্রসহ এর গঠন ব্যাখ্যা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1084 (ET: N/A)]*

    Answer: A loop is a control structure that repeats a block of statements as long as a given condition remains true. It removes the need to write the same statements many times.

    Four parts of every loop
    - Initialization — set the control variable to its starting value.
    - Condition — tested before or after each pass; the loop continues while it is true.
    - Body — the statements that are repeated.
    - Update — change the control variable so the condition eventually becomes false.

    Entry-controlled loop (for, while) — condition tested first
    ```mermaid
    flowchart TD
        A([Start]) --> B[Initialization]
        B --> C{Condition ?}
        C -->|False| F([Exit])
        C -->|True| D[Loop body]
        D --> E[Update]
        E --> C
    ```

    Exit-controlled loop (do-while) — body runs first
    ```mermaid
    flowchart TD
        A([Start]) --> B[Initialization]
        B --> C[Loop body]
        C --> D[Update]
        D --> E{Condition ?}
        E -->|True| C
        E -->|False| F([Exit])
    ```

    - An entry-controlled loop may run zero times; an exit-controlled loop always runs at least once.
    - If the update step is missing or the condition never becomes false, the result is an infinite loop.

14. **Write a pesudcode that takes in one positive number only and returns the factor for that number.** *[Combined Bank Senior Officer (IT/ICT) 2019 compact it 1113 (ET: DU)]*

    Answer:

    Pseudocode
    ```
    ALGORITHM FindFactors(n)
    Input : a positive integer n
    Output: all factors (divisors) of n

    Step 1: Start
    Step 2: Read n
    Step 3: if n <= 0 then
                print "Please enter a positive number"
                go to Step 7
    Step 4: set i = 1
    Step 5: while i <= n do
                if n mod i = 0 then
                    print i           // i divides n exactly
                i = i + 1
            end while
    Step 6: (all factors printed)
    Step 7: Stop
    ```

    C implementation
    ```c
    void printFactors(int n) {
        int i;
        if (n <= 0) { printf("Enter a positive number\n"); return; }
        printf("Factors of %d: ", n);
        for (i = 1; i <= n; i++)
            if (n % i == 0) printf("%d ", i);
    }
    ```

    - For `n = 12` the factors are `1 2 3 4 6 12`.
    - Time complexity `O(n)`. It can be reduced to `O(√n)` by looping to `√n` and printing both `i` and `n/i` for each divisor found.

15. **Write down the psudo-code that accepts i, n is integer and value as input, store all n integers in an array, called pairs and return all pairs where the summation of individual's pair=value.** *[Sonali & Janata Bank Senior Officer (IT/ICT) 2018 compact it 1165 (ET: N/A)]*

| Length: | Input | Output |
|---|---|---|
| Array | 5 | {1,5}, {7,-1} |
| Summation value: | 1 7 -1 5 -7 |  |
|  | 6 |  |

    Answer:

    Pseudocode — brute force, `O(n²)`
    ```
    ALGORITHM FindPairs(n, arr[], value)
    Input : n = number of elements, arr[] = the n integers, value = target sum
    Output: every pair of elements whose sum equals value

    Step 1: Start
    Step 2: Read n
    Step 3: for i = 0 to n-1
                read arr[i]
            end for
    Step 4: Read value
    Step 5: for i = 0 to n-2
                for j = i+1 to n-1
                    if arr[i] + arr[j] = value then
                        print "{", arr[i], ",", arr[j], "}"
                end for
            end for
    Step 6: Stop
    ```

    Verification with the sample data
    - Array = `1, 7, -1, 5, -7`, target value = `6`
    - `1 + 5 = 6` → pair `{1, 5}`
    - `7 + (-1) = 6` → pair `{7, -1}`
    - Output: `{1,5}, {7,-1}` — matching the expected output.

    Faster version using a hash set, `O(n)`
    ```
    create an empty set S
    for i = 0 to n-1
        complement = value - arr[i]
        if complement is in S then
            print "{", complement, ",", arr[i], "}"
        add arr[i] to S
    end for
    ```
    - Each element is checked against the set once, so the whole scan is linear at the cost of `O(n)` extra memory.

16. **Draw flowchart to input five positive numbers and sort them is ascending order.** *[Combined 3 Banks Assistant Programmer 2018 compact it 1199 (ET: N/A)]*

    Answer: Bubble sort is used, since it is the easiest to draw as a flowchart.

    ```mermaid
    flowchart TD
        A([Start]) --> B[/Read 5 numbers into arr[0..4]/]
        B --> C[i = 0]
        C --> D{i < 4 ?}
        D -->|No| K[/Print sorted array/]
        K --> L([Stop])
        D -->|Yes| E[j = 0]
        E --> F{j < 4 - i ?}
        F -->|No| I[i = i + 1]
        I --> D
        F -->|Yes| G{arr[j] > arr[j+1] ?}
        G -->|Yes| H[Swap arr[j] and arr[j+1]]
        H --> J[j = j + 1]
        G -->|No| J
        J --> F
    ```

    Explanation
    - The outer loop runs 4 times, since 5 elements need at most `n − 1` passes.
    - The inner loop compares each adjacent pair and swaps them when they are out of order.
    - The bound `4 - i` shrinks each pass, because after pass `i` the largest `i` elements are already in place at the end.

    - Example: `5 2 9 1 7` becomes `1 2 5 7 9`.
    - Time complexity `O(n²)`, space `O(1)`.

## String Manipulation & Algorithms (14)

1. **Write a C or Java program to convert string to integer without using any built-in function.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1362 (ET: BUET)]*

   Answer: Walk through the string one character at a time. Each digit's numeric value is `ch - '0'`, and the running result is shifted left by multiplying by 10.

   ```c
   #include <stdio.h>

   int stringToInt(char str[]) {
       int i = 0, result = 0, sign = 1;

       if (str[0] == '-') { sign = -1; i = 1; }   // handle a leading minus
       else if (str[0] == '+') { i = 1; }

       for (; str[i] != '\0'; i++) {
           if (str[i] < '0' || str[i] > '9')
               return 0;                          // not a valid digit
           result = result * 10 + (str[i] - '0');
       }
       return sign * result;
   }

   int main(void) {
       char s[] = "-1234";
       printf("%d\n", stringToInt(s));            // -1234
       return 0;
   }
   ```

   Trace for `"1234"`
   - `'1' - '0' = 1` → result = 1
   - `'2' - '0' = 2` → result = 1×10 + 2 = 12
   - `'3'` → 12×10 + 3 = 123
   - `'4'` → 123×10 + 4 = 1234

   - Why `ch - '0'` works: ASCII digits are consecutive, `'0'` is 48 and `'9'` is 57, so subtracting `'0'` gives the numeric value.
   - Time complexity `O(n)`, space `O(1)`. This is essentially what the library `atoi()` does.

2. **Write a C program to check whether a string is a Palindrome.** *[BUET Assistant Programmer 21.06.2025 compact it 1433 (ET: BUET)]*

   Answer: Compare characters from both ends moving inward. If every pair matches, the string is a palindrome.

   ```c
   #include <stdio.h>
   #include <string.h>

   int isPalindrome(char str[]) {
       int left = 0, right = strlen(str) - 1;
       while (left < right) {
           if (str[left] != str[right])
               return 0;                          // mismatch found
           left++;
           right--;
       }
       return 1;
   }

   int main(void) {
       char str[100];
       printf("Enter a string: ");
       scanf("%s", str);

       if (isPalindrome(str)) printf("%s is a Palindrome\n", str);
       else                   printf("%s is not a Palindrome\n", str);
       return 0;
   }
   ```

   - `"madam"` → m=m, a=a, pointers meet → palindrome.
   - `"hello"` → h ≠ o at the first comparison → not a palindrome.
   - Only `n/2` comparisons are needed, so the time complexity is `O(n)` with `O(1)` space.
   - For case-insensitive checking, convert both characters with `tolower()` before comparing.

3. **Write a C program upper case to lower case conversion.** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 475 (ET: N/A)]*

   Answer: In ASCII, a lowercase letter is exactly 32 more than its uppercase counterpart (`'A'` = 65, `'a'` = 97).

   ```c
   #include <stdio.h>

   int main(void) {
       char str[100];
       int i;

       printf("Enter a string: ");
       scanf("%s", str);

       for (i = 0; str[i] != '\0'; i++) {
           if (str[i] >= 'A' && str[i] <= 'Z')
               str[i] = str[i] + 32;              // convert to lowercase
       }

       printf("Lowercase: %s\n", str);
       return 0;
   }
   ```

   - For input `HELLO World` the output is `hello world` — non-letter characters are left untouched by the range check.
   - Equivalent forms: `str[i] = str[i] - 'A' + 'a';` or the library call `tolower(str[i])` from `<ctype.h>`.
   - Time complexity `O(n)`, space `O(1)`.

4. **String reverse program but without without using the library function.** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 660 (ET: N/A)], [BREB Assistant Programmer 18.02.2023 compact it 468 (ET: N/A)]*

   Answer: Find the length manually, then swap the outer characters inward.

   ```c
   #include <stdio.h>

   int main(void) {
       char str[100], temp;
       int len = 0, i;

       printf("Enter a string: ");
       scanf("%s", str);

       while (str[len] != '\0')          // find length without strlen()
           len++;

       for (i = 0; i < len / 2; i++) {   // swap from both ends
           temp = str[i];
           str[i] = str[len - 1 - i];
           str[len - 1 - i] = temp;
       }

       printf("Reversed string: %s\n", str);
       return 0;
   }
   ```

   - For input `Bangladesh` the output is `hsedalgnaB`.
   - The loop runs only `len/2` times; going all the way to `len` would swap everything back and undo the reversal.
   - Time complexity `O(n)`, space `O(1)` — the reversal happens in place.

5. **Write a C program to remove given character from string: Example input: programming and we want to remove: gram now output: proming without having the gram from string.** *[RPGCL Assistant Manager (ICT) 2022 compact it 652 (ET: BUET)]*

   Answer: The example removes the substring `"gram"` from `"programming"`, leaving `"proming"`. So the task is substring removal.

   ```c
   #include <stdio.h>
   #include <string.h>

   void removeSubstring(char str[], char sub[]) {
       char *pos;
       int len = strlen(sub);

       while ((pos = strstr(str, sub)) != NULL) {   // find the substring
           // shift the tail left over the matched part
           strcpy(pos, pos + len);
       }
   }

   int main(void) {
       char str[100] = "programming";
       char sub[20]  = "gram";

       removeSubstring(str, sub);
       printf("Result: %s\n", str);       // proming
       return 0;
   }
   ```

   Version without any library function
   ```c
   void removeChars(char str[], char remove[]) {
       int i, j, k = 0;
       char result[100];
       int subLen = 0;
       while (remove[subLen] != '\0') subLen++;

       for (i = 0; str[i] != '\0'; ) {
           for (j = 0; j < subLen && str[i + j] == remove[j]; j++) ;
           if (j == subLen) i += subLen;          // match found, skip it
           else result[k++] = str[i++];
       }
       result[k] = '\0';
       for (i = 0; i <= k; i++) str[i] = result[i];
   }
   ```

   - `"programming"` minus `"gram"` gives `pro` + `ming` = `proming`.
   - The `while` loop in the first version removes every occurrence, not just the first.
   - Time complexity `O(n × m)` where `m` is the substring length.

6. **Write a program IPv4 IP validation from given IP with valid and not valid.** *[RPGCL Assistant Manager (ICT) 2022 compact it 653 (ET: BUET)]*

   Answer: A valid IPv4 address has exactly four parts separated by dots, each part is a number from 0 to 255, and no part is empty or has extra leading zeros.

   ```c
   #include <stdio.h>
   #include <string.h>

   int isValidIPv4(char ip[]) {
       int i = 0, num = 0, dots = 0, digits = 0;

       if (ip[0] == '.' || ip[strlen(ip) - 1] == '.') return 0;

       for (i = 0; ip[i] != '\0'; i++) {
           if (ip[i] == '.') {
               if (digits == 0) return 0;         // empty part like "1..2.3"
               if (num > 255) return 0;
               dots++;
               num = 0;
               digits = 0;
           }
           else if (ip[i] >= '0' && ip[i] <= '9') {
               num = num * 10 + (ip[i] - '0');
               digits++;
               if (digits > 3) return 0;
           }
           else {
               return 0;                          // any other character
           }
       }
       if (dots != 3 || digits == 0 || num > 255) return 0;
       return 1;
   }

   int main(void) {
       char ip[50];
       printf("Enter an IP address: ");
       scanf("%s", ip);
       printf("%s is %s\n", ip, isValidIPv4(ip) ? "Valid" : "Not Valid");
       return 0;
   }
   ```

   Test cases

   | Input | Result | Reason |
   |---|---|---|
   | 192.168.1.1 | Valid | four parts, all 0-255 |
   | 255.255.255.255 | Valid | maximum allowed |
   | 256.1.1.1 | Not Valid | 256 exceeds 255 |
   | 192.168.1 | Not Valid | only 2 dots |
   | 192.168.1.1.1 | Not Valid | 4 dots |
   | 192.168.a.1 | Not Valid | non-digit character |

   - Time complexity `O(n)` where `n` is the length of the string.

7. **Find occurrence of a Character in a string. String: Bangladesh is a big country. Sample Input: b, Output: 2 times Sample Input p, Output: Not foud this letter** *[BKSP Assistant Programmer 03.12.2022 compact it 729 (ET: N/A)]*

   Answer: The sample shows the search is case-insensitive — `'b'` matches both the capital `B` of "Bangladesh" and the small `b` of "big", giving 2.

   ```c
   #include <stdio.h>
   #include <ctype.h>

   int main(void) {
       char str[] = "Bangladesh is a big country";
       char ch;
       int i, count = 0;

       printf("Enter a character to search: ");
       scanf(" %c", &ch);

       for (i = 0; str[i] != '\0'; i++)
           if (tolower(str[i]) == tolower(ch))
               count++;

       if (count == 0)
           printf("Not found this letter\n");
       else
           printf("%d times\n", count);
       return 0;
   }
   ```

   Verification with the sample
   - Input `b` → `B` in "Bangladesh" and `b` in "big" → `2 times`.
   - Input `p` → no `p` anywhere in the sentence → `Not found this letter`.

   - `scanf(" %c", &ch)` has a leading space, which skips any leftover newline in the input buffer.
   - Time complexity `O(n)`, space `O(1)`.

8. **What is the purpose of '\0' character in C?** *[BCC CA Monitoring System Project 2021 compact it 830 (ET: N/A)]*

   Answer: `'\0'` is the null character, and its purpose is to mark the END of a string in C.

   - C has no separate string type. A string is just a `char` array, and `'\0'` is what tells every string function where the data stops.
   - Its ASCII value is 0, and it is written as `'\0'` — a single character, not two.
   - Functions like `strlen()`, `printf("%s")`, `strcpy()` and `strcmp()` all keep reading until they hit `'\0'`.

   Consequence for array sizing
   - An `n`-character string needs an array of at least `n + 1` bytes.
   - `char s[] = "Hello";` occupies 6 bytes — `H e l l o \0` — even though `strlen(s)` returns 5.

   What happens without it
   - Reading past the end of the array continues into unrelated memory until a zero byte happens to appear, producing garbage output or a crash.

   Do not confuse three similar things

   | Symbol | Meaning | Value |
   |---|---|---|
   | `'\0'` | Null character, string terminator | 0 |
   | `'0'` | The digit character zero | 48 |
   | `NULL` | Null pointer constant | `((void*)0)` |

9. **(c) Write down a program to find length of a string without using any library function.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 892 (ET: N/A)]*

   Answer: Count characters until the null terminator is reached.

   ```c
   #include <stdio.h>

   int stringLength(char str[]) {
       int count = 0;
       while (str[count] != '\0')       // stop at the terminator
           count++;
       return count;
   }

   int main(void) {
       char str[100];
       printf("Enter a string: ");
       scanf("%s", str);
       printf("Length = %d\n", stringLength(str));
       return 0;
   }
   ```

   - For `"Bangladesh"` the result is `10`. The `'\0'` itself is not counted, which is exactly how `strlen()` behaves.
   - Pointer version: `int len(char *s){ char *p = s; while(*p) p++; return p - s; }`
   - Time complexity `O(n)`, space `O(1)`.

10. **Write a program to read a character “lower case ” and convert it into upper case.** *[BAUST Assistant Programmer 2021 compact it 918-919 (ET: N/A)]*

    Answer: An uppercase letter is 32 less than its lowercase counterpart in ASCII.

    ```c
    #include <stdio.h>

    int main(void) {
        char ch;

        printf("Enter a lowercase character: ");
        scanf(" %c", &ch);

        if (ch >= 'a' && ch <= 'z') {
            ch = ch - 32;                // convert to uppercase
            printf("Uppercase: %c\n", ch);
        }
        else {
            printf("Not a lowercase letter\n");
        }
        return 0;
    }
    ```

    - For input `d` the output is `D`, since `'d'` is 100 and `100 − 32 = 68`, which is `'D'`.
    - The range check prevents nonsense results for digits or symbols.
    - Equivalent library call: `toupper(ch)` from `<ctype.h>`, which is safer because it does not depend on the character set being ASCII.

11. **Given a IPv4 address string, write C/C++/JAVA code to show the class the IP address belongs to.** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 923-924 (ET: CTI)]*
   Sample Input: 192.168.0.0
   Sample Output: Class C

   Answer: The class is decided entirely by the FIRST octet.

   | Class | First octet range | Purpose |
   |---|---|---|
   | A | 1 – 126 | Very large networks |
   | B | 128 – 191 | Medium networks |
   | C | 192 – 223 | Small networks |
   | D | 224 – 239 | Multicast |
   | E | 240 – 255 | Reserved / experimental |

   ```c
   #include <stdio.h>

   int main(void) {
       char ip[20];
       int a, b, c, d;

       printf("Enter IPv4 address: ");
       scanf("%s", ip);
       sscanf(ip, "%d.%d.%d.%d", &a, &b, &c, &d);

       if      (a >= 1   && a <= 126) printf("Class A\n");
       else if (a == 127)             printf("Loopback address\n");
       else if (a >= 128 && a <= 191) printf("Class B\n");
       else if (a >= 192 && a <= 223) printf("Class C\n");
       else if (a >= 224 && a <= 239) printf("Class D (Multicast)\n");
       else if (a >= 240 && a <= 255) printf("Class E (Reserved)\n");
       else                           printf("Invalid IP address\n");
       return 0;
   }
   ```

   - For `192.168.0.0` the first octet is 192, which falls in 192–223, so the output is `Class C` — matching the sample.
   - 127.x.x.x is excluded from Class A because it is reserved for loopback (`127.0.0.1` is localhost).
   - `sscanf` parses the four octets out of the string in one call.

12. **(b) Write down a C function to sort a list of strings in alphabetic order.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1130-1131 (ET: N/A)]*

    Answer: Strings are compared with `strcmp()` and swapped with `strcpy()`, because `=` does not work on C strings.

    ```c
    #include <stdio.h>
    #include <string.h>

    void sortStrings(char list[][30], int n) {
        char temp[30];
        int i, j;

        for (i = 0; i < n - 1; i++)
            for (j = 0; j < n - 1 - i; j++)
                if (strcmp(list[j], list[j + 1]) > 0) {   // out of order
                    strcpy(temp, list[j]);
                    strcpy(list[j], list[j + 1]);
                    strcpy(list[j + 1], temp);
                }
    }

    int main(void) {
        char names[5][30] = {"Rahim", "Abul", "Karim", "Babu", "Salam"};
        int i;

        sortStrings(names, 5);

        for (i = 0; i < 5; i++)
            printf("%s\n", names[i]);
        return 0;
    }
    ```

    Output
    ```
    Abul
    Babu
    Karim
    Rahim
    Salam
    ```

    - `strcmp(a, b)` returns a positive value when `a` should come after `b`, which is exactly the swap condition.
    - Comparison is by ASCII value, so all uppercase letters sort before all lowercase ones. Use `strcasecmp()` for case-insensitive ordering.
    - Time complexity `O(n² × L)` where `L` is the average string length.

13. **(a) Write an algorithm to find Palindrome number.** *[BPSC Assistant Programmer (ICT) 2019 compact it 1140 (ET: N/A)]*

    Answer: A palindrome number reads the same forwards and backwards, such as 121, 1331 or 12321.

    Algorithm
    ```
    Step 1: Start
    Step 2: Read n
    Step 3: set original = n, reversed = 0
    Step 4: while n != 0 do
                remainder = n mod 10
                reversed  = reversed × 10 + remainder
                n = n / 10
            end while
    Step 5: if original = reversed then
                print "Palindrome"
            else
                print "Not Palindrome"
    Step 6: Stop
    ```

    Implementation
    ```c
    int isPalindrome(int n) {
        int original = n, reversed = 0;
        while (n != 0) {
            reversed = reversed * 10 + (n % 10);
            n /= 10;
        }
        return (original == reversed);
    }
    ```

    Trace for n = 121
    - `reversed`: 1 → 12 → 121
    - `original = 121` equals `reversed = 121`, so it is a palindrome.

    - Note the original must be saved before the loop, because `n` is destroyed by the repeated division.
    - Time complexity `O(d)` where `d` is the number of digits.

14. **Check string str2 is superscript of string str1.** *[NESCO Manager (Software) 2018 compact it 1209-1210 (ET: N/A)]*

| Input | Output |
|---|---|
| str1=x str2=x^x | Yes |
| str1=x str2=x^2 | No |

    Answer: From the sample data, `str2` is a "superscript" of `str1` only when `str2` has the exact form `str1 ^ str1` — that is, the base and the exponent are both `str1`.

    - `str1 = "x"`, `str2 = "x^x"` → base `x` and exponent `x` both equal `str1` → Yes.
    - `str1 = "x"`, `str2 = "x^2"` → exponent is `2`, not `x` → No.

    ```c
    #include <stdio.h>
    #include <string.h>

    int isSuperscript(char str1[], char str2[]) {
        char expected[200];

        // build the expected pattern:  str1 + "^" + str1
        strcpy(expected, str1);
        strcat(expected, "^");
        strcat(expected, str1);

        return (strcmp(str2, expected) == 0);
    }

    int main(void) {
        printf("%s\n", isSuperscript("x", "x^x") ? "Yes" : "No");   // Yes
        printf("%s\n", isSuperscript("x", "x^2") ? "Yes" : "No");   // No
        return 0;
    }
    ```

    Version that splits at the caret instead of building a pattern
    ```c
    int isSuperscript2(char str1[], char str2[]) {
        char *caret = strchr(str2, '^');
        if (caret == NULL) return 0;                 // no caret at all
        *caret = '\0';                               // split into base and exponent
        int ok = (strcmp(str2, str1) == 0) && (strcmp(caret + 1, str1) == 0);
        *caret = '^';                                // restore the string
        return ok;
    }
    ```

    - Time complexity `O(n)`, space `O(n)` for the pattern buffer.  <!-- verify -->
    - Note: the question wording is ambiguous and only two sample cases were given, so this reading is inferred from them.

## File Handling (4)

1. Name Top C 5 File Management Function Name. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

   Answer: The five most used file management functions in C are:

   | Function | Purpose | Syntax |
   |---|---|---|
   | `fopen()` | Opens a file and returns a `FILE *` | `fp = fopen("data.txt", "r");` |
   | `fclose()` | Closes an open file and flushes the buffer | `fclose(fp);` |
   | `fprintf()` | Writes formatted data to a file | `fprintf(fp, "%d %s", n, name);` |
   | `fscanf()` | Reads formatted data from a file | `fscanf(fp, "%d %s", &n, name);` |
   | `fgets()` | Reads one line from a file safely | `fgets(buf, 100, fp);` |

   File opening modes
   - `"r"` read, `"w"` write (erases existing content), `"a"` append
   - `"r+"` read and write, `"w+"` read and write with truncation, `"a+"` read and append
   - Adding `b` (as in `"rb"`) opens the file in binary mode.

   Other important file functions
   - `fputs()`, `fgetc()`, `fputc()` — line and character level input/output
   - `fread()`, `fwrite()` — binary block read and write
   - `fseek()`, `ftell()`, `rewind()` — move and report the file position
   - `feof()` — test for end of file; `remove()` and `rename()` — delete and rename

   - `fopen()` returns `NULL` when the file cannot be opened, so the return value must always be checked before use.

2. **Write a function in Python programming language which takes a filename as parameter, orders first 10 line in output.** *[BCC Assistant Programmer 12.02.2021 compact it 814 (ET: BUET)]*

   Answer: Read the file, take the first 10 lines, sort them and print the result.

   ```python
   def first_ten_sorted(filename):
       try:
           with open(filename, 'r') as f:
               lines = f.readlines()[:10]        # first 10 lines only
       except FileNotFoundError:
           print("File not found:", filename)
           return []

       lines = [line.rstrip('\n') for line in lines]
       lines.sort()                              # alphabetical order

       for line in lines:
           print(line)
       return lines


   # driver code
   first_ten_sorted("data.txt")
   ```

   Explanation
   - `with open(...)` closes the file automatically, even if an error occurs inside the block.
   - `readlines()[:10]` slices the first ten lines; if the file has fewer, Python simply returns what exists rather than raising an error.
   - `rstrip('\n')` removes the trailing newline so the sort compares only the text.
   - `sort()` orders them alphabetically. Use `sort(key=int)` for numeric lines, or `reverse=True` for descending order.

   - For a very large file, reading line by line with `itertools.islice(f, 10)` avoids loading the whole file into memory.

3. **You have a file name accounts.txt which contain the following information. Now write a C/C++/Java program to find the following: Total balance of saving account, Find the highest and second highest balance of saving account.** *[NRCC Assistant Programmer 2021 compact it 931-932 (ET: N/A)]*

   Answer: The file contents were not printed with the question, so the format `accountNo accountType balance` is assumed, one record per line.

   Sample `accounts.txt`
   ```
   1001 saving 25000
   1002 current 40000
   1003 saving 78000
   1004 saving 15000
   1005 current 32000
   1006 saving 92000
   ```

   ```c
   #include <stdio.h>

   int main(void) {
       FILE *fp;
       int accNo;
       char type[20];
       double balance, total = 0;
       double highest = -1, second = -1;

       fp = fopen("accounts.txt", "r");
       if (fp == NULL) {
           printf("Cannot open file\n");
           return 1;
       }

       while (fscanf(fp, "%d %s %lf", &accNo, type, &balance) == 3) {
           if (strcmp(type, "saving") == 0) {
               total += balance;

               if (balance > highest) {
                   second = highest;          // old highest drops to second
                   highest = balance;
               }
               else if (balance > second && balance != highest) {
                   second = balance;
               }
           }
       }
       fclose(fp);

       printf("Total saving balance   = %.2f\n", total);
       printf("Highest saving balance = %.2f\n", highest);
       printf("Second highest balance = %.2f\n", second);
       return 0;
   }
   ```

   Output for the sample file
   ```
   Total saving balance   = 210000.00
   Highest saving balance = 92000.00
   Second highest balance = 78000.00
   ```

   - The highest and second highest are tracked in a single pass, so no sorting is needed — `O(n)` time and `O(1)` space.
   - `fscanf` returning 3 confirms all three fields were read; the loop stops cleanly at end of file.
   - `<string.h>` must be included for `strcmp`.

4. **Folder থেকে একটি Image নিয়ে ঐ Image এর নামের .jpeg extention কে .png extention এ convert করার জন্য Python language এর Function লিখুন?** *[PGCB Sub-Assistant Engineer (CSE) 2020 compact it 1046 (ET: BUET)]*

   Answer: Two things could be meant — renaming the extension only, or actually converting the image format. Both are shown.

   Version 1 — rename the extension only
   ```python
   import os

   def rename_extension(folder, filename):
       old_path = os.path.join(folder, filename)

       name, ext = os.path.splitext(filename)
       if ext.lower() not in ['.jpeg', '.jpg']:
           print("Not a JPEG file")
           return None

       new_name = name + '.png'
       new_path = os.path.join(folder, new_name)

       os.rename(old_path, new_path)
       print("Renamed:", filename, "->", new_name)
       return new_path
   ```

   Version 2 — actually convert the image data (the correct approach)
   ```python
   from PIL import Image
   import os

   def convert_jpeg_to_png(folder, filename):
       old_path = os.path.join(folder, filename)

       name, ext = os.path.splitext(filename)
       if ext.lower() not in ['.jpeg', '.jpg']:
           print("Not a JPEG file")
           return None

       new_path = os.path.join(folder, name + '.png')

       img = Image.open(old_path)
       img.save(new_path, 'PNG')          # re-encodes the pixel data
       print("Converted:", filename, "->", name + '.png')
       return new_path


   # convert every JPEG in a folder
   def convert_all(folder):
       for f in os.listdir(folder):
           if f.lower().endswith(('.jpeg', '.jpg')):
               convert_jpeg_to_png(folder, f)
   ```

   - Important difference: `os.rename` only changes the filename. The bytes inside are still JPEG, so some programs will refuse to open it as a PNG.
   - `Image.save()` from the Pillow library actually re-encodes the pixels into PNG format, which is what "convert" really means.
   - Pillow is installed with `pip install Pillow`.

## Pointers (4)

1. **অথবা, (ক) Pointer কী? Pointer ব্যবহারের সুবিধাগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 600 (ET: N/A)]*

   Answer: A pointer is a variable that stores the memory address of another variable instead of storing a value directly.

   ```c
   int x = 10;
   int *p;          // p is a pointer to an int
   p = &x;          // p now holds the address of x
   printf("%d", *p) // prints 10 — the value AT that address
   ```
   - `&` is the address-of operator; `*` is the dereference operator that reads the value stored at an address.

   Advantages of using pointers
   - Direct memory access — memory can be read and written efficiently, which is essential for systems and embedded programming.
   - Dynamic memory allocation — `malloc()`, `calloc()` and `realloc()` return pointers, so arrays can grow at run time instead of being fixed at compile time.
   - Returning multiple values from a function — pass several pointers and the function writes results into all of them.
   - Efficient parameter passing — for a large structure, passing an 8-byte address is far cheaper than copying the whole object.
   - Building dynamic data structures — linked lists, trees, graphs, stacks and queues all depend on pointers to link nodes.
   - Array and string handling — an array name is itself a pointer to its first element, so pointer arithmetic walks through arrays quickly.
   - Function pointers — allow callbacks and jump tables, which makes flexible, table-driven code possible.

   - Risks to note: dereferencing a NULL or uninitialised pointer crashes the program, and forgetting to `free()` allocated memory causes a memory leak.

2. **(গ) পয়েন্টার কী? Malloc( ) এবং Calloc( ) এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*

   Answer: A pointer is a variable that holds the memory address of another variable. It is declared with `*` and is used with `&` to take an address and `*` to read the value at that address.

   malloc() vs calloc()

   | Point | malloc() | calloc() |
   |---|---|---|
   | Full form | memory allocation | contiguous allocation |
   | Number of arguments | 1 — total bytes | 2 — number of blocks and size of each |
   | Syntax | `p = (int*)malloc(n * sizeof(int));` | `p = (int*)calloc(n, sizeof(int));` |
   | Initialisation | Memory is left uninitialised (garbage) | Every byte is set to 0 |
   | Speed | Faster, no zero-filling step | Slower, because it clears the memory |
   | Returns | `void *` to the block, or `NULL` on failure | Same |
   | Use when | The data will be overwritten immediately | A clean, zeroed block is needed |

   Example
   ```c
   int *a = (int *) malloc(5 * sizeof(int));   // 5 ints, values are garbage
   int *b = (int *) calloc(5, sizeof(int));    // 5 ints, all set to 0

   if (a == NULL || b == NULL) { printf("Allocation failed\n"); return 1; }

   free(a);
   free(b);
   ```

   Related functions
   - `realloc(ptr, newSize)` — resizes an already allocated block, keeping the existing contents.
   - `free(ptr)` — releases the memory back to the system. Every successful `malloc` or `calloc` must be matched by exactly one `free`, otherwise memory leaks.

3. **Describe Dynamic memory allocation in programming in C?** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*

   Answer: Dynamic memory allocation means reserving memory while the program is RUNNING, rather than fixing the amount at compile time. The memory comes from the heap and is accessed through pointers.

   Why it is needed
   - A static array such as `int a[100];` fixes the size before the program starts. If only 5 elements are used, 95 slots are wasted; if 200 are needed, the program fails.
   - Dynamic allocation asks for exactly as much memory as the input requires, and releases it when it is no longer needed.

   The four functions, all declared in `<stdlib.h>`

   | Function | Purpose | Example |
   |---|---|---|
   | `malloc(size)` | Allocates `size` bytes, uninitialised | `p = (int*)malloc(n*sizeof(int));` |
   | `calloc(n, size)` | Allocates `n × size` bytes, all set to 0 | `p = (int*)calloc(n, sizeof(int));` |
   | `realloc(p, size)` | Resizes an existing block, keeping its contents | `p = (int*)realloc(p, 2*n*sizeof(int));` |
   | `free(p)` | Releases the block back to the heap | `free(p);` |

   Complete example
   ```c
   #include <stdio.h>
   #include <stdlib.h>

   int main(void) {
       int n, i, *arr;

       printf("How many elements? ");
       scanf("%d", &n);

       arr = (int *) malloc(n * sizeof(int));    // exactly n integers
       if (arr == NULL) {                        // always check
           printf("Memory allocation failed\n");
           return 1;
       }

       for (i = 0; i < n; i++) scanf("%d", &arr[i]);
       for (i = 0; i < n; i++) printf("%d ", arr[i]);

       free(arr);                                // release the memory
       arr = NULL;                               // avoid a dangling pointer
       return 0;
   }
   ```

   Common mistakes
   - Not checking for `NULL` — allocation can fail when memory is exhausted.
   - Memory leak — allocating without ever calling `free()`.
   - Dangling pointer — using a pointer after `free()`. Setting it to `NULL` afterwards prevents this.
   - Double free — calling `free()` twice on the same pointer, which corrupts the heap.

   - Static vs dynamic: static memory lives on the stack, is freed automatically and has a fixed size; dynamic memory lives on the heap, must be freed manually and can be sized at run time.

4. **(a) What is the difference between array and pointer?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 891-892 (ET: N/A)]*

   Answer:

   | Point | Array | Pointer |
   |---|---|---|
   | What it is | A block of contiguous memory holding several elements | A variable holding one memory address |
   | Memory allocated | At compile time (static), size fixed | Can point to static or dynamically allocated memory |
   | Reassignment | Not possible — `a = b;` is illegal | Possible — `p = q;` is fine |
   | `sizeof` | Gives the total size of the whole array | Gives the size of the pointer itself (8 bytes on 64-bit) |
   | Address arithmetic | The name is a constant address, cannot be incremented | Can be incremented and decremented freely |
   | Initialisation | `int a[3] = {1,2,3};` | `int *p = &x;` or `p = malloc(...)` |
   | Deallocation | Automatic when it goes out of scope | Must be freed manually if dynamically allocated |

   Example showing the sizeof difference
   ```c
   int a[10];
   int *p = a;

   printf("%zu\n", sizeof(a));    // 40 — ten ints
   printf("%zu\n", sizeof(p));    // 8  — just the pointer
   ```

   How they are related
   - An array name decays into a pointer to its first element in most expressions, so `a[i]` and `*(a + i)` mean exactly the same thing.
   - That is why an array passed to a function arrives as a pointer, and why `sizeof` inside the function no longer gives the array size — the length must be passed separately.

   - Key distinction to remember: an array name is a constant address that cannot be changed, while a pointer is a variable that can be pointed anywhere.

## Command Line Arguments & Basic Programs (1)

1. **Write a C program that takes inputs integer values from command line interface and print the summation of the integers.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1361 (ET: BUET)]*

   Answer: Command line arguments reach the program through `main(int argc, char *argv[])`. They arrive as strings, so each must be converted to an integer with `atoi()`.

   ```c
   #include <stdio.h>
   #include <stdlib.h>

   int main(int argc, char *argv[]) {
       int i, sum = 0;

       if (argc < 2) {
           printf("Usage: %s num1 num2 num3 ...\n", argv[0]);
           return 1;
       }

       for (i = 1; i < argc; i++) {       // start at 1, skip the program name
           sum += atoi(argv[i]);
       }

       printf("Sum of %d integers = %d\n", argc - 1, sum);
       return 0;
   }
   ```

   Understanding the parameters
   - `argc` — argument count, including the program name itself.
   - `argv[]` — argument vector, an array of strings. `argv[0]` is the program name, `argv[1]` onward are the actual arguments, and `argv[argc]` is `NULL`.

   Sample run
   ```
   $ gcc sum.c -o sum
   $ ./sum 10 20 30 40
   Sum of 4 integers = 100
   ```
   - Here `argc = 5` and `argv` holds `{"./sum", "10", "20", "30", "40", NULL}`.
   - The loop starts at `i = 1` because `argv[0]` is the program name, not a number.

   Safer version using `strtol` instead of `atoi`
   ```c
   char *end;
   long v = strtol(argv[i], &end, 10);
   if (*end != '\0') { printf("'%s' is not a valid integer\n", argv[i]); return 1; }
   sum += (int)v;
   ```
   - `atoi()` silently returns 0 for invalid input such as `"abc"`, whereas `strtol()` reports where parsing stopped, so bad input can be detected.
